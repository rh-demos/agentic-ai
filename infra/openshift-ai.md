# OpenShift AI installation

## Prerequisites

### Nvidia GPU

- Node Feature Discovery Operator
- NVIDIA GPU Operator

### OpenShift AI

- cert-manager Operator for Red Hat OpenShift
- Authorino Operator
- Red Hat OpenShift Service Mesh **3**
- Red Hat Connectivity Link
- Leader Worker Set Operator
- Red Hat OpenShift AI - **fast-3.x**

## DataScienceCluster

```
apiVersion: datasciencecluster.opendatahub.io/v2
kind: DataScienceCluster
metadata:
  name: default-dsc
  labels:
    app.kubernetes.io/name: datasciencecluster
spec:
  components:
    kserve:
      nim:
        managementState: Managed
      rawDeploymentServiceConfig: Headless
      managementState: Managed
    modelregistry:
      registriesNamespace: rhoai-model-registries
      managementState: Managed
    feastoperator:
      managementState: Managed
    trustyai:
      eval:
        lmeval:
          permitCodeExecution: deny
          permitOnline: deny
      managementState: Managed
    aipipelines:
      argoWorkflowsControllers:
        managementState: Managed
      managementState: Managed
    ray:
      managementState: Managed
    kueue:
      defaultClusterQueueName: default
      defaultLocalQueueName: default
      managementState: Removed
    workbenches:
      workbenchNamespace: rhods-notebooks
      managementState: Managed
    mlflowoperator:
      managementState: Removed
    dashboard:
      managementState: Managed
    llamastackoperator:
      managementState: Managed
    trainingoperator:
      managementState: Managed
```





