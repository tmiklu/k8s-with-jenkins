# k8s-with-jenkins 

## Install kind 
[kind](https://kind.sigs.k8s.io/docs/user/quick-start/)

## Use kind to run kubernetes cluster in docker 
```bash
kind create cluster --name=k8s --config=config.yaml
``` 

## Run jenkins and install jenkins
```bash
docker run -d -v jenkins_home:/var/jenkins_home -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts
``` 
**Configuration Options**
---
1. Manage Jenkins
    + `Manage plugins`
    + `Install Kubernetes CLI` 

2. Manage Jenkins
    + `Add Credential`
    + `Secret File`
    + ` Use ${HOME}/.kube/config` 

3. New
    + `Add name`
    + `Chose freestyle pipeline`
    + `Build Environment`
    + `Check Configure Kubernetes CLI (kubectl) with multiple credentials`
    + `Cluster name`
    + `Context name`
    + `Apply`

4. Build
    + `Execute shell` 
    ```bash
    curl -LsO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl" 
    chmod u+x ./kubectl
    ./kubectl run nginx --image=nginx
    ./kubectl get pods
    ```
    + `Save`
    

