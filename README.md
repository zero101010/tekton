# tekton

## Create your on cluster

- Install `ctlptl` and `kind`, after that run this command:
```
ctlptl create cluster kind --registry=ctlptl-registry
```

## Install Tekton pipelines
- Run this `kubectl apply --filename \
https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml`

## Install tekton CLI
- https://tekton.dev/docs/cli/

## Install Triggers
- Run this commands to install the triggers that will be used to call the pipelines

```
kubectl apply --filename \
https://storage.googleapis.com/tekton-releases/triggers/latest/release.yaml
kubectl apply --filename \
https://storage.googleapis.com/tekton-releases/triggers/latest/interceptors.yaml
```

## Run the First trigger
- To run your first trigger run all the yaml files that you have on this repos running:
```
kubectl apply -f Task
kubectl apply -f Pipeline
kubectl apply -f TriggerTemplate
kubectl apply -f TriggerBinding
kubectl apply  -f EventListener
```

- After this run this command to do a portFoward.
```
kubectl port-forward service/el-hello-listener 8080
```

- Then make a request 
```
curl -v \
   -H 'content-Type: application/json' \
   -d '{"username": "Tekton"}' \
   http://localhost:8080
   ```

## Install tekton Chain
- We need this to store data
```
kubectl apply --filename \
https://storage.googleapis.com/tekton-releases/chains/latest/release.yaml
```

## Install tekton UI

```
kubectl apply --filename https://storage.googleapis.com/tekton-releases/dashboard/latest/release.yaml
```
