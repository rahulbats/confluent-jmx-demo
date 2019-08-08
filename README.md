## Steps to setup JMX monitoring with Prometheus and Grafana

* Download JMX prometheus agent from [maven central](https://mvnrepository.com/artifact/io.prometheus.jmx/jmx_prometheus_javaagent/0.3.0)
* Put the kafka-connect-jmx-exporter.yml in a location in your local machine.
* Edit the bin/connect-distributed in your machine and add this line before the last line `export EXTRA_ARGS=' -name connectDistributed -javaagent:<PATH_TO_JAR>/jmx_prometheus_javaagent-0.3.0.jar=7070:<PATH_TO_YML>/kafka-connect-jmx-exporter.yml'`
* Start Connector using `bin/connect-distributed etc/kafka/connect-distributed.properties`
* Open http://localhost:7070 in a browser and it should open a page with metrics 
* Download prometheus from [here](https://prometheus.io/download/)
* Unzip it and cd into it 
* Replace the prometheus yml with the one in this repo or add the scrape config.
* Start Prometheus with ./prometheus 
* Prometheus will be available on http://localhost:9090 and all the metrics for Connect will be available in its dropdown 
* Install [grafana](https://grafana.com/docs/installation/)
* Open grafana and add a datasource for prometheus at http://localhost:9090
* Create a dashboard by importing the grafana.json in this repo.
 


