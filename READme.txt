Steps to learn K8s 


Imperative/Declarative -> sample pod -> nginx 

kubectl run -> kubeapiserver (HTTP REST API) -> 

Apiserver -> etcd -> scheduler -> working node -> kubelet(container runtime (containerd)) -> kubeproxy -> pod is deployed -> Apiserver -> etcd

[User] 
   |
   | kubectl run nginx --image=nginx
   ↓
[kube-apiserver]
   ↓          ↘
[Validation]  [etcd ← stores spec]
   ↓
[kube-scheduler ← watches etcd]
   ↓
[Choose Node]
   ↓
[Update etcd with Node Info]
   ↓
[kubelet on Node] ← pulls pod spec
   ↓
[containerd → pulls nginx:latest image]
   ↓
[Pod Created and Running]
   ↓
[kubelet reports status → API server → etcd]

