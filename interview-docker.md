# Docker Image Commands – In-Depth with Use Cases

## 1. docker images
**Description:** Lists all local Docker images  
**Use Case:** To view all the images pulled or built on the current system  

**Example Output:**
```

REPOSITORY      TAG       IMAGE ID       CREATED         SIZE
nginx           latest    4bb46517cac3   4 days ago      142MB
myapp           v1        d9e9451a7c1b   2 weeks ago     235MB

```

---

## 2. docker pull `<image-name>`
**Description:** Downloads image from Docker Hub or other registry  
**Syntax:**
```

docker pull nginx\:latest

```
**Use Case:**  
When setting up a container environment, pull official base images like nginx, mysql, ubuntu.

---

## 3. docker build -t `<image-name>`:`<tag>` .
**Description:** Builds a custom image from a Dockerfile  
**Syntax:**
```

docker build -t myapp\:v1 .

```
**Use Case:**  
Create your own image with application code and environment.

**Example Dockerfile:**
```

FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD \["node", "index.js"]

```

---

## 4. docker tag `<image-id>` `<repository>`:`<tag>`
**Description:** Tags an existing image with a new name or destination  
**Syntax:**
```

docker tag d9e9451a7c1b myrepo/myapp\:v1

```
**Use Case:**  
Required before pushing to DockerHub or private registries.

---

## 5. docker push `<image-name>`:`<tag>`
**Description:** Pushes the image to a remote repository  
**Syntax:**
```

docker push myrepo/myapp\:v1

```
**Use Case:**  
Used during CI/CD pipelines or deployments to publish application image.  

> Note: Login first using `docker login`

---

## 6. docker rmi `<image-id or name>`
**Description:** Removes a specific Docker image from local system  
**Syntax:**
```

docker rmi nginx\:latest

```
**Use Case:**  
To clean up space or delete unwanted images.

To delete dangling images:
```

docker image prune -f

```

---

## 7. docker inspect `<image-id or image-name>`
**Description:** Displays detailed information about the image  
**Syntax:**
```

docker inspect nginx

```
**Use Case:**  
Debug issues or view configurations like env variables, volumes, etc.

---

## 8. docker history `<image-name>`
**Description:** Shows the layer history of an image  
**Syntax:**
```

docker history nginx

```
**Use Case:**  
Understand how an image was built layer-by-layer.

---

## 9. docker save -o `<filename.tar>` `<image-name>`
**Description:** Saves the Docker image to a tar file  
**Syntax:**
```

docker save -o nginx.tar nginx\:latest

```
**Use Case:**  
Transfer images offline or backup.

---

## 10. docker load -i `<filename.tar>`
**Description:** Loads an image from a tar archive  
**Syntax:**
```

docker load -i nginx.tar

```
**Use Case:**  
Restore image from shared or backed-up archive.

---

## 11. docker image ls
**Description:** Same as `docker images` – lists all images

---

## 12. docker image prune -a
**Description:** Removes all unused and dangling images  
**Syntax:**
```

docker image prune -a

```
**Use Case:**  
Free up disk space by removing all unused images.

---

## Summary Table

| Command                 | Description                        | Use Case                       |
|-------------------------|------------------------------------|-------------------------------|
| docker images           | List all local images              | View available images         |
| docker pull             | Download image from registry       | Setup environment             |
| docker build            | Build image from Dockerfile        | Create custom image           |
| docker tag              | Tag image for registry             | Prepare for push              |
| docker push             | Upload image to registry           | CI/CD deployment              |
| docker rmi              | Delete image from local            | Cleanup                       |
| docker inspect          | Show image details                 | Debug or analyze              |
| docker history          | Show build layers                  | Optimize builds               |
| docker save             | Save image to file                 | Transfer or backup            |
| docker load             | Load image from file               | Restore from tar              |
| docker image prune -a   | Cleanup unused images              | Save space                    |
```
