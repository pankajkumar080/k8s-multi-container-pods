# k8s-multi-container-pods

1. Create a Kubernetes manifest file named "pod.yaml" in the path "-/Desktop/Project/k8s-multi-container-pods/" to create a Pod object named "multicontainer-nginx" with label "app: web" and configure it as follows: 

- Create a container named "nginx-container" with the image "nginx:latest" and expose it to the port 80.
- Create another container named "sidecar-container" with the image "curlimages/curl:latest" and add the following shell script that stores "nginx-container logs for every 3 mins in the path /var/log/nginx/http_responses.log.

  **"while true; do curls "your-nginx-service-ip" >> /"path-to-store"; "time-interval"; done"**

NOTE: 

 - Replace the <your-nginx-service-ip> with a nginx service ip, which is yet to be created in the following step. 

- Replace the <path-to-store> and <time interval> with the given argurments.

Create an "emptyDir" volume named "http-volume and mount it with both the containers using the path /var/log/nginx/.

2. Create a Kubernetes manifest file named "service.yaml" in the path *-/Desktop/Project/k8s-multi-container-pods//" to create a Service object named "nginx-service" of type "LoadBalancer" which uses the port "80".
