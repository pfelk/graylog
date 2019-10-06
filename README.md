## Added Java Repository 
```
sudo add-apt-repository ppa:webupd8team/java
```

## Added Elastic GPG Key
```
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
```

## Added Elastic Repository
```
echo "deb https://artifacts.elastic.co/packages/5.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-5.x.list
```

## Refresh
```
sudo apt-get update
```

## Install pwgen
```
sudo apt-get install pwgen
```

## Install Java
```
sudo apt-get install oracle-java8-installer
```

## Install MongoDB
```
sudo apt-get install mongodb-server
```

## Install Elasticsearch
```
sudo apt-get install elasticsearch
```

## Configure Elasticsearch
```
sudo nano /etc/elastisearch/elasticsearch.yml
```

## Amend Elasticsearch 
cluster.name: YOURNAME
node.name: ${HOSTNAME}
network.host: 10.0.0.16
http.port: 9200

## Start Elasticsearch
```
sudo systemctl daemon-reload
sudo systemctl enable elasticsearch.service
sudo systemctl restart elasticsearch.service
```

## Check Status
```
systemctl status elasticsearch.service
```

## Download Graylog (https://www.graylog.org/download) RPM
```
wget https://packages.graylog2.org/repo/packages/graylog-2.3-repository_latest.deb
```

## Install Graylog (Repository)
```
sudo dpkg -i graylog-2.3-repository_latest.deb
```

## Refresh
```
sudo apt-get update
```

## Install Graylog 
```
sudo apt-get install graylog-server
```
## Configure Graylog
```
sudo nano /etc/graylog/server/server.conf
```

## TimeZones
```
http://www.joda.org/joda-time/timezones.html
```

## Set rest_listen_uri
```
rest_listen_uri = http://10.0.0.16:129000/api/
```
## Set web_listen_uri
```
web_listen_uri = http://10.0.0.16:9000/
```

## Set Password
```
echo -n yourpassword | sha256sum
#Paste output to the two following within /etc/graylog/server/server.conf
password_secret = OUTPUTGOESHERE
pwgen -s 80 1
root_password_sha2 = OUTPUTGOESHERE
```

## Start Graylog
```
sudo systemctl daemon-reload
sudo systemctl enable graylog-server.service
sudo systemctl start graylog-server.service 
```
