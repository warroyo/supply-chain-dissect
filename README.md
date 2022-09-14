# supply-chain-dissect

## source provider

```
kubectl get clustersourcetemplate source-template -o yaml

kubectl get gitrepo <workload-name> -n <namespace> -o yaml
```

## image builder

```
kubectl get clusterimagetemplate kpack-template -o yaml

kubectl get clusterimagetemplates kaniko-template -o yaml

#for tbs builds
kubectl get cnb-image <workload-name> -n <namespace> -o yaml


#for kaniko builds
kubectl get runnable <workload-name> -n <namespace> -o yaml

kubectl get clusterruntemplate kaniko-runtemplate -o yaml

kubectl get clustertask kaniko-build -o yaml

kubectl get taskrun -A -l carto.run/runnable-name=<workload-name> -l carto.run/run-template-name=kaniko-runtemplate -o yaml
```


## config provider
```
kubectl clusterconfigtemplates convention-template -o yaml

kubectl get podintent <workload-name> -n <namespace> -o yaml
```

## app config
```
kubectl get clusterconfigtemplates config-template -o yaml

kubectl get configmap <workload-name> -n <namespace> -o yaml
```

## config writer

```
kubectl get clusterTemplate config-writer-and-pull-requester-template -o yaml

kubectl get runnable <workload-name>-config-writer-pull-requester -n <namespace> -o yaml

kubectl get clusterruntemplate commit-and-pr-pipelinerun -o yaml

kubectl get clustertask commit-and-pr -o yaml

kubectl get taskrun -A -l carto.run/runnable-name=<workload-name> -l carto.run/run-template-name=commit-and-pr-pipelinerun -o yaml
```



## source tester

```
kubectl get clustersourcetemplate testing-pipeline -o yaml

kubectl get runnable <workload-name> -n <namespace> -o yaml

kubectl get clusterruntemplate tekton-source-pipelinerun -o yaml

kubectl get pipeline -A -l apps.tanzu.vmware.com/pipeline=test -o yaml

kubectl get pipelinerun -A -l carto.run/runnable-name=<workload-name> -o yaml

kubectl get taskrun -A -l carto.run/runnable-name=<workload-name> -l carto.run/run-template-name=tekton-source-pipelinerun -o yaml
```

## source scanner

```
kubectl get clustersourcetemplate source-scanner-template -o yaml

kubectl get sourcescan <workload-name> -n <namespace> -o yaml

kubectl get scantemplate blob-source-scan-template -n <namespace> -o yaml

kubectl get scanpolicy scanpolicy-sample -n <namespace> -o yaml

kubectl get jobs -A -l carto.run/workload-name=<workload-name> -l carto.run/resource-name=source-scanner -o yaml
```

## image scanner
```
kubectl get clusterimagetemplate  image-scanner-template -o yaml

kubectl get imagescan <workload-name> -n <namespace> -o yaml

kubectl  get scantemplate private-image-scan-template -n <namespace> -o yaml

kubectl get scanpolicy scanpolicy-sample -n <namespace> -o yaml

kubectl get jobs -A -l carto.run/workload-name=<workload-name> -l carto.run/resource-name=image-scanner -o yaml

```
