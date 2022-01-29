# spring-cloud-kubernetes-issue-963-demo

This repo is to replicate the issue [#963](https://github.com/spring-cloud/spring-cloud-kubernetes/issues/963) for
Spring Cloud Kubernetes.

## Running Locally

1. Set up Kubernetes cluster locally, e.g. using Minikube, Kind, or others.
2. Run Vault

    ```
    helm install vault hashicorp/vault --set server.dev.enabled=true,server.standalone.enabled=true
   ``` 

3. Run Consul

    ```
    helm install consul hashicorp/consul --set global.name=consul,server.replicas=1
    ``` 

4. Configure ConfigMap

    ```
    kubectl create configmap my-configmap --from-literal=hello=world
    ```

5. Build image
6. Deploy the image to the Kubernetes using Helm. Note: Need to change the `image.repository` and `image.tag` at
   the [values.yaml](helm/values.yaml) file.
