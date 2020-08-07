# helm-db-replication

This project includes a helm chart with templates for Kubernetes yaml files. This chart can be packaged for usage with Kubernetes.
Kubernetes yaml files provide prove of concept for creation of Postgres Database Master-Slave-Replication inside different Kubernetes Deployments which orchestrate pods and containers on multiple Kubernetes Cluster nodes.<br>
It will create pods for one master and one slave database and respectively create containers with ready to use db replication based on Postgres 12.

## How to install

Copy the contents of this repo to your Kubernetes host<br>
Prerequisite: helm should be installed

## How to run
```hcl 
# create directory for persistent volume on each node
sudo mkdir /mnt/data

# go one level up from helm-db-replication directory to package it to an archive
helm package helm-db-replication

# to preview generated yaml files
helm template --debug helm-db-replication-0.1.0.tgz

# install chart to Kubernetes
helm install helm-db-replication helm-db-replication-0.1.0.tgz

# See which yaml files are deployed on the server
helm get manifest helm-db-replication
```


## Delete chart
```hcl
helm delete helm-db-replication
```

