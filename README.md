# EUTECH DASHBOARD-README

This README document will discuss how to import previously created kibana dashboard into new PC linux environment by installing ELK stack and manipulate servers.If you already installed ELK stack (Elasticsearch,Kibana,Logstash) then skip first 3 steps and follow from step 4 .Contact me if you want any clarification.

# Required software

Java(version according to your ELK stack version)

### 1.Clone the GIT repository
Clone the GIT repository 
```sh
https://github.com/rehanja/EUTECH-Dashboard
```

### 2.Download ELK stack Open source version 
Download main ELK stack components(Elasticsearch, kibana ,logstash) using below links into the previously cloned directory.

Elasticsearch-7.4.0 Open source version

https://www.elastic.co/downloads/elasticsearch or https://www.elastic.co/downloads/elasticsearch-oss

Kibana-7.4.1-linux-x86_64 Open source version

https://www.elastic.co/downloads/kibana-oss

Logstash-7.4.1 Open source version

https://www.elastic.co/downloads/logstash-oss

### 3.Extract above files into same directory
```sh
tar -zxvf [tar file name]
```

First Elasticsearch server should start then Logstash server and finally Kibana server.

### 4.Elasticsearch server manipulation

cd into elasticsearch bin folder
```sh
cd elasticsearch-7.4.0/bin/
```
Start the server by
```sh
elasticsearch
```
Then elasticsearch server will run in http://localhost:9200 

If you want to stop server 
```sh
sudo kill -9 `sudo lsof -t -i:9200`
```
Because it will not stop till process kill in relevant port

### 5.Manipulate logstash 
#### Configurations
Copy and paste the `eutech.conf` file in to your logstash directory.
`eutech.conf` file can be found in git repository.

**NOTE:** If you are feeding another type of logs you have to change the "filter" section according to your logs.

Run logstash server by
```sh
cd ./logstash-7.4.1/bin
./logstash -f ./../eutech.conf
```

### 6.kibana server manipulation

cd into elasticsearch bin folder
```sh
cd kibana-6.5.0-linux-x86_64/bin/
```
```sh
./kibana
```
Then kibana server will run in http://localhost:5601

### 7.Create a Index 
You have to create a index pattern to start Dashboard.For that go to

```sh
home page->Management->Index patterns->Create index pattern->[name of index pattern]
```

You have to give a name for index pattern that choose the index name in the logstash.conf file.
Eg: eutech

If it's happen correctly "Success! Your index pattern matches 1 index." message will apper.Then 

```sh
->Next Step ->Time Filter field name->[Choose @timestamp]->Create index pattern
```

### 8.Import Kibana visualization dashboard
Download exportDashboards.ndjson file from GIT repository 

Open http://localhost:5601 and go to kibana Home page 
```sh
Management->Saved Objects->Import->[exportDashboards.ndjson]->Import->Done
```
Go to home page
```sh 
Dashboard->EUTECH dashboard
```
The dashboard that previously created should appear there but will not run real time till API is connected via l logstash .conf file.


### 9.Special notice

Not important folder provide some irrelavent docs to dashboard process.





 
