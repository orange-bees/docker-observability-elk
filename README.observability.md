# Elasticsearch Observability

## Metricbeat

### Setup

```shell
docker container run \
--name=metricbeat \
--volume="$(pwd)/metricbeat.docker.yml:/usr/share/metricbeat/metricbeat.yml:ro" \
docker.elastic.co/beats/metricbeat:8.14.3 \
setup -E setup.kibana.host=host.docker.internal:5601 \
-E output.elasticsearch.hosts=["host.docker.internal:9200"] \
-E output.elasticsearch.username=elastic \
-E output.elasticsearch.password=changeme
```

```shell
docker container run \
--name=metricbeat \
--volume="$(pwd)/metricbeat.docker.yml:/usr/share/metricbeat/metricbeat.yml:ro" \
docker.elastic.co/beats/metricbeat:8.14.3 \
setup -E setup.kibana.host=host.docker.internal:5601 \
-E output.elasticsearch.hosts=["host.docker.internal:9200"]
```

```shell
docker container run \
-p 5066:5066 \
docker.elastic.co/beats/metricbeat:8.14.3 \
setup -E setup.kibana.host=host.docker.internal:5601 \
-E output.elasticsearch.hosts=["host.docker.internal:9200"] \
-E output.elasticsearch.username=elastic \
-E output.elasticsearch.password=changeme
```

```shell
docker container run \
-p 5066:5066 \
--volume="$(pwd)/metricbeat.docker.yml:/usr/share/metricbeat/metricbeat.yml:ro" \
docker.elastic.co/beats/metricbeat:8.14.3 \
setup -E setup.kibana.host=host.docker.internal:5601
```

### Deployment

```shell
docker container run \
-p 5066:5066 \
--volume="$(pwd)/metricbeat.docker.yml:/usr/share/metricbeat/metricbeat.yml:ro" \
docker.elastic.co/beats/metricbeat:8.14.3 \
metricbeat -e
```

## Filebeat
