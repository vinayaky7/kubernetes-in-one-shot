# Kubernetes in One Shot

This README serves as a comprehensive guide to all the commands used in the "Kubernetes in One Shot" tutorial. Commands are categorized by topic for better organization, with a brief description of each command to help you understand its purpose and usage.

---

## **Kind Cluster Setup**

1. `vim config.yml`  
   Create or edit the configuration file for the Kind cluster.

2. `kind create cluster --name=tws-cluster --config=config.yml`  
   Create a Kubernetes cluster using Kind with the specified configuration.

3. `kubectl cluster-info --context kind-tws-cluster`  
   Display cluster information for the Kind cluster context.

4. `kubectl config use-context kind-tws-cluster`  
   Switch the current context to the Kind cluster.

5. `kubectl get nodes`  
   List all nodes in the Kubernetes cluster.

---

## **Namespaces**

1. `kubectl apply -f namespace.yml`  
   Apply the namespace configuration from `namespace.yml`.

2. `kubectl delete -f namespace.yml`  
   Delete the namespace specified in `namespace.yml`.

3. `kubectl get namespaces`  
   List all namespaces in the cluster.

4. `kubectl create ns nginx`  
   Create a namespace named `nginx`.

5. `kubectl get ns`  
   List all namespaces in the cluster.

---

## **Deployments and ReplicaSets**

1. `vim deployment.yml`  
   Create or edit a deployment configuration file.

2. `kubectl apply -f deployment.yml`  
   Apply the deployment configuration from `deployment.yml`.

3. `kubectl delete -f deployment.yml`  
   Delete the deployment specified in `deployment.yml`.

4. `kubectl set image deployment/nginx-deployment -n nginx nginx=nginx:latest`  
   Update the `nginx` container image in the `nginx-deployment` deployment to the latest version.

5. `kubectl scale deployment/nginx-deployment -n nginx --replicas=5`  
   Scale the `nginx-deployment` to 5 replicas.

6. `kubectl get deployment -n nginx`  
   List all deployments in the `nginx` namespace.

7. `cp deployment.yml replicasets.yml`  
   Copy the `deployment.yml` file to create `replicasets.yml`.

8. `kubectl apply -f replicasets.yml`  
   Apply the ReplicaSet configuration from `replicasets.yml`.

9. `kubectl delete -f replicasets.yml`  
   Delete the ReplicaSet specified in `replicasets.yml`.

10. `kubectl get replicasets -n nginx`  
    List all ReplicaSets in the `nginx` namespace.

---

## **DaemonSets**

1. `vim daemonsets.yml`  
   Open `daemonsets.yml` in a text editor for modifications.

2. `kubectl apply -f daemonsets.yml`  
   Apply the DaemonSet configuration from `daemonsets.yml`.

3. `kubectl delete -f daemonsets.yml`  
   Delete the DaemonSet specified in `daemonsets.yml`.

4. `kubectl get pods -n nginx -o wide`  
   List all pods in the `nginx` namespace with detailed information, such as node assignment.

---

## **Jobs and CronJobs**

1. `vim job.yml`  
   Create or edit a Job configuration file.

2. `kubectl apply -f job.yml`  
   Apply the Job configuration from `job.yml`.

3. `kubectl get job -n nginx`  
   List all Jobs in the `nginx` namespace.

4. `kubectl logs pod/[pod_name] -n nginx`  
   View logs for a specific pod in the `nginx` namespace.

5. `kubectl delete -f job.yml`  
   Delete the Job specified in `job.yml`.

6. `vim cron-job.yml`  
   Create or edit a CronJob configuration file.

7. `kubectl apply -f cron-job.yml`  
   Apply the CronJob configuration from `cron-job.yml`.

8. `kubectl get cronjob -n nginx`  
   List all CronJobs in the `nginx` namespace.

---

## **Services and Networking**

1. `vim service.yml`  
   Create or edit a Service configuration file.

2. `kubectl apply -f service.yml`  
   Apply the Service configuration from `service.yml`.

3. `kubectl describe svc [service_name] -n [namespace]`  
   Display detailed information about a service in the specified namespace.

4. `kubectl get svc -n nginx`  
   List all services in the `nginx` namespace.

5. `kubectl port-forward service/nginx-service -n nginx [host_port]:[container_port] --address=0.0.0.0`  
   Forward a port from the service to the host.

6. `kubectl apply -f ingress.yml`  
   Apply an Ingress configuration.

7. `kubectl get ing -n nginx`  
   List all Ingress resources in the `nginx` namespace.

---

## **Persistent Storage**

1. `vim persistentVolume.yml`  
   Create or edit a PersistentVolume configuration file.

2. `kubectl apply -f persistentVolume.yml`  
   Apply the PersistentVolume configuration from `persistentVolume.yml`.

3. `vim persistentVolumeClaim.yml`  
   Create or edit a PersistentVolumeClaim configuration file.

4. `kubectl apply -f persistentVolumeClaim.yml`  
   Apply the PersistentVolumeClaim configuration from `persistentVolumeClaim.yml`.

5. `kubectl get pv`  
   List all PersistentVolumes in the cluster.

6. `kubectl get pvc`  
   List all PersistentVolumeClaims in the cluster.

7. `kubectl delete pvc/[pvc_name]`  
   Delete the specified PersistentVolumeClaim.

8. `kubectl delete pv/[pv_name]`  
   Delete the specified PersistentVolume.

---

## **Role-Based Access Control (RBAC)**

1. `vim role.yml`  
   Create or edit a Role configuration file.

2. `kubectl apply -f role.yml`  
   Apply the Role configuration from `role.yml`.

3. `vim role-binding.yml`  
   Create or edit a RoleBinding configuration file.

4. `kubectl apply -f role-binding.yml`  
   Apply the RoleBinding configuration from `role-binding.yml`.

5. `kubectl auth can-i [verb] [resource] --as [user] -n [namespace]`  
   Check if a user has permissions to perform a specific action on a resource.

6. `kubectl describe rolebinding [rolebinding_name] -n [namespace]`  
   Display detailed information about a RoleBinding in the specified namespace.

---

## **Kubernetes Dashboard**

1. `kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml`  
   Deploy the Kubernetes Dashboard.

2. `vim dashboard-admin-user.yml`  
   Create or edit a Dashboard admin user configuration file.

3. `kubectl apply -f dashboard-admin-user.yml`  
   Apply the admin user configuration for the Kubernetes Dashboard.

4. `kubectl proxy --port=8001 --address=0.0.0.0`  
   Start the Kubernetes API proxy accessible on port 8001.

5. `kubectl -n kubernetes-dashboard create token admin-user`  
   Generate a token for the admin user to access the dashboard.

---

## **Git Integration**

1. `git init`  
   Initialize a new Git repository.

2. `git remote add origin [repository_url]`  
   Add a remote Git repository.

3. `git add .`  
   Stage all changes for commit.

4. `git commit -m "Commit message"`  
   Commit the staged changes with a message.

5. `git push origin main`  
   Push changes to the `main` branch of the remote repository.

---

This README organizes all commands topic-wise to ensure clarity and proper sequencing. Let me know if additional updates are needed!

