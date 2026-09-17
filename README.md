# nwlterry — repository catalog

All GitHub repositories for [nwlterry](https://github.com/nwlterry), grouped by **what is actually in the repo** (scripts, dashboards, plugins, runbooks). Empty placeholders are listed last.

**44 repositories** · **41 with content** · **3 empty**

Each content repo also has a [`GROUP.md`](groups.yml) that names its group and sibling repos.

| Group | Repos |
| --- | ---: |
| [Elastic Stack lab (Hyper-V)](#1-elastic-stack-lab-hyper-v) | 6 |
| [Elasticsearch ILM, indices, dashboards](#2-elasticsearch-ilm-indices-dashboards) | 8 |
| [Elastic plugins and upgrades](#3-elastic-plugins-and-upgrades) | 4 |
| [Elastic Agent, APM, ML, JVM](#4-elastic-agent-apm-ml-jvm) | 7 |
| [OpenShift logging](#5-openshift-logging) | 3 |
| [Kafka / Confluent](#6-kafka--confluent) | 5 |
| [Certificates / Windows PKI](#7-certificates--windows-pki) | 5 |
| [Ops tools](#8-ops-tools) | 3 |
| [Placeholder (empty)](#9-placeholder-empty) | 3 |

Machine-readable map: [`groups.yml`](groups.yml).

---

## 1. Elastic Stack lab (Hyper-V)

Hyper-V lab cluster (`ism-elk-cluster`), rolling restarts, NFS snapshots, disk tuning.

| Repository | Contents |
| --- | --- |
| [elastic_stack_on_hyper-v](https://github.com/nwlterry/elastic_stack_on_hyper-v) | Deploy/upgrade Elasticsearch, Kibana, Fleet, Agents on RHEL 8.10 Hyper-V (air-gap, NFS snaps, APM, 8.18 → 8.19 → 9.5.3) |
| [elk_cluster_post_os_patching_restart](https://github.com/nwlterry/elk_cluster_post_os_patching_restart) | Ansible rolling host reboot after OS patching (cold → hot → ML → masters → Kibana → Fleet → APM → Logstash) |
| [elk_cluster_health_check](https://github.com/nwlterry/elk_cluster_health_check) | Poll `_cluster/health` until green, then stop ES and reboot this node |
| [es_nfs_repo](https://github.com/nwlterry/es_nfs_repo) | NFS `fs` snapshot repository verification (mount + `path.repo` on every master and data node) |
| [es_node_disk_tuning](https://github.com/nwlterry/es_node_disk_tuning) | ES data-disk tuning for VMware/vSAN/RHEL (readahead, XFS, scheduler) |
| [elasticsearch_ldap_gmsa](https://github.com/nwlterry/elasticsearch_ldap_gmsa) | LDAP/AD bind on Linux: gMSA is not supported; use a regular service account + keystore |

---

## 2. Elasticsearch ILM, indices, dashboards

ILM reviews, index inventory, stack monitoring ingest, system-index size.

| Repository | Contents |
| --- | --- |
| [elasticsearch_cluster_ilm_review](https://github.com/nwlterry/elasticsearch_cluster_ilm_review) | ILM review pack: policies vs proposed changes, ingest notes, CSVs |
| [es-ilm-query](https://github.com/nwlterry/es-ilm-query) | Python ILM policy analyzer + index collector (JSON/CSV); Podman runner |
| [elasticsearch_query](https://github.com/nwlterry/elasticsearch_query) | Shell ILM/index TSV report and optional policy JSON+CSV export |
| [elk_index_monitoring](https://github.com/nwlterry/elk_index_monitoring) | Kibana 8.15 dashboard: system index (`.kibana`, `.security`, …) size and growth |
| [elk_stack_monitor](https://github.com/nwlterry/elk_stack_monitor) | Stack Monitoring cluster-status rules used to mute/unmute during rolling restart |
| [elasticsearch_stack_information_dashboard](https://github.com/nwlterry/elasticsearch_stack_information_dashboard) | Daily ingest from Stack Monitoring (`.monitoring-es-*`), air-gapped 8.14+ |
| [elastic-mapper-size](https://github.com/nwlterry/elastic-mapper-size) | Offline mapper-size plugin **8.18.4** |
| [elk_mapper-size](https://github.com/nwlterry/elk_mapper-size) | Offline mapper-size plugin **8.19.18** and **9.4.3** |

---

## 3. Elastic plugins and upgrades

Upgrade notes and older plugin zips.

| Repository | Contents |
| --- | --- |
| [elasticsearch_upgrade](https://github.com/nwlterry/elasticsearch_upgrade) | Agent `host.hostname` case change 8.14.3 → 8.18.4 (Linux raw hostname) |
| [elk_upgrade](https://github.com/nwlterry/elk_upgrade) | Offline mapper-size plugin **8.14.3** |

Related plugin zips also live in group 2 (`elastic-mapper-size`, `elk_mapper-size`).

---

## 4. Elastic Agent, APM, ML, JVM

Agents on OpenShift/Rancher, APM sample, ML planning, heap analysis, HTTP JSON poller.

| Repository | Contents |
| --- | --- |
| [elastic-agent-uptime-ocp](https://github.com/nwlterry/elastic-agent-uptime-ocp) | OpenShift manifests for Elastic Agent uptime/Heartbeat + Logstash |
| [rancher_elastic-agent](https://github.com/nwlterry/rancher_elastic-agent) | Elastic Agent DaemonSet + ConfigMap + RBAC for Rancher/K8s |
| [SampleDotNetApp_with_Elastic_APM_Agent](https://github.com/nwlterry/SampleDotNetApp_with_Elastic_APM_Agent) | Sample .NET app with Elastic APM agent |
| [elasticsearch_ml_job](https://github.com/nwlterry/elasticsearch_ml_job) | ML job planning (forecasting, log categorization, data frame analytics) |
| [elastic_brainstorm_ml_job](https://github.com/nwlterry/elastic_brainstorm_ml_job) | Discussion dump that led to the ML job notes |
| [elasticsearch-http-json](https://github.com/nwlterry/elasticsearch-http-json) | Elastic Agent `httpjson` poller for DolphinScheduler process instances |
| [java_heap_dump](https://github.com/nwlterry/java_heap_dump) | Split Eclipse Memory Analyzer 1.16.1 zip for heap dumps |

DolphinScheduler dashboards sit with the poller: [dolphinscheduler-dashboards](https://github.com/nwlterry/dolphinscheduler-dashboards) (Kibana NDJSON).

---

## 5. OpenShift logging

ClusterLogForwarder to external Elasticsearch, and stuck-project cleanup.

| Repository | Contents |
| --- | --- |
| [openshift-logging-external-elasticsearch](https://github.com/nwlterry/openshift-logging-external-elasticsearch) | OpenShift Logging 6.1 `ClusterLogForwarder` to external ES 8.x |
| [ocp-logforward-elk](https://github.com/nwlterry/ocp-logforward-elk) | OpenShift 4.18 log forwarding + filters (Vector / CLF) |
| [ocp_clean_empty_project](https://github.com/nwlterry/ocp_clean_empty_project) | Unstick Terminating projects blocked by OLM `PackageManifest` finalizers |

---

## 6. Kafka / Confluent

Broker mappings, Connect export, Redis connector, lag exporter, Grafana/Kibana formulas.

| Repository | Contents |
| --- | --- |
| [kafka_integration](https://github.com/nwlterry/kafka_integration) | Kafka broker Prometheus field list + Elasticsearch index mapping JSON |
| [kafka_dashboard_grafana_query](https://github.com/nwlterry/kafka_dashboard_grafana_query) | Kafka JVM heap Lens/Grafana formula notes |
| [kafka-connect_connector_config_bulk_export](https://github.com/nwlterry/kafka-connect_connector_config_bulk_export) | Export Connect connector configs to CSV (passwords stripped) |
| [confluent_redis_kafka_connector](https://github.com/nwlterry/confluent_redis_kafka_connector) | Offline Redis Kafka Connect plugin 0.9.1 |
| [kafa_lag_exporter_fix](https://github.com/nwlterry/kafa_lag_exporter_fix) | Confluent 7.7.2 Control Center lag + kafka-lag-exporter stale gauges |

---

## 7. Certificates / Windows PKI

IIS CCS, SSRS renewal, PFX/P12, ACME ADCS, architecture diagrams.

| Repository | Contents |
| --- | --- |
| [iis_cert_automation](https://github.com/nwlterry/iis_cert_automation) | Export IIS certs to Central Certificate Store + SYSTEM scheduled task |
| [ssrs_cert-automation](https://github.com/nwlterry/ssrs_cert-automation) | SSRS certificate auto-renewal via Certificate Services lifecycle notifications |
| [certificarte_management](https://github.com/nwlterry/certificarte_management) | OpenSSL/keytool: PFX → Java PKCS12 keystore + truststore |
| [acme-adcs_upgrade_planning](https://github.com/nwlterry/acme-adcs_upgrade_planning) | ACME ADCS v3.0.7 upgrade checklist and production settings |
| [eraser_project](https://github.com/nwlterry/eraser_project) | IIS certificate auto-renewal architecture (single and farm) diagrams |

---

## 8. Ops tools

Azure DevOps, HTTP timing, disk `dd` tests, small PowerShell helpers.

| Repository | Contents |
| --- | --- |
| [ado_rest_rools](https://github.com/nwlterry/ado_rest_rools) | WinForms PowerShell Azure DevOps Server REST tool (policies/repos) |
| [curl-time](https://github.com/nwlterry/curl-time) | `curl` timing table (connect / TTFB / total) |
| [dd-disk-test](https://github.com/nwlterry/dd-disk-test) | Interactive `dd` read/write speed test |
| [powershell](https://github.com/nwlterry/powershell) | JSON intersect + Kafka Prometheus mapping helpers |
| [dolphinscheduler-dashboards](https://github.com/nwlterry/dolphinscheduler-dashboards) | Whaleops / DolphinScheduler Kibana dashboard NDJSON |

---

## 9. Placeholder (empty)

No files to group yet. Left as created.

| Repository | Notes |
| --- | --- |
| [elastic_artifact_registry-alpine](https://github.com/nwlterry/elastic_artifact_registry-alpine) | Empty (intended local Elastic artifact registry on Alpine) |
| [elastic_java_oom](https://github.com/nwlterry/elastic_java_oom) | Empty (intended Java OOM notes; heap dumps live in `java_heap_dump`) |
| [katacoda-scenarios](https://github.com/nwlterry/katacoda-scenarios) | Empty Katacoda scenarios stub |

---

## How grouping works

1. **This README** is the profile catalog (shows on https://github.com/nwlterry).
2. **`groups.yml`** is the same map for scripts.
3. **`GROUP.md`** in each content repo names the group and lists siblings.

Repos were not moved into GitHub Organizations (that would change clone URLs). Grouping is by content, not by renaming.
