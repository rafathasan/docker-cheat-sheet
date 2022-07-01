
  
# :bread:Docker Cheat Sheet
it contains my daily to daily essential commands that my brain isn't powerful enough to remember.

## :bulb:Appendix
- Deployment: commands for create, run & change the states of containers.
- Management: commands for listing & viewing of containers.
- Interaction: commands to interact with containers.
  
## :wrench:Deployment
### :apple:docker create
create container from image
```bash
docker container create <image_name>
```
or
```bash
docker create <image_name>
```
create container from image with fixed name
```bash
docker container create --name <container_name> <image_name>
```
```bash
docker create --name <container_name> <image_name>
```
create image from container
```bash
docker commit <container_id or container_name> <new_image_name>
```
### :watermelon:docker run
create and run containers (same as above but uses run instead)
```bash
docker run --name <container_name> <image_name>
```
run containers in foreground (by default)
```bash
docker run --name <container_name> <image_name>
```
delete containers on the exited state
```bash
docker run --rm --name <container_name> <image_name>
```
continue running containers after inner-process dies
```bash
docker run --name <container_name> -dt <image_name>
```
### :grapes:docker run -d (daemon)
run containers in daemon mode
```bash
docker run -d --name <container_name> <image_name>
```
run containers with mapped ports
```bash
docker run --name <container_name> -d -p <host_post>:<container_port> <image_name>
```
## :musical_keyboard: Interaction
list process running in containers
```bash
docker top <container_name or container_id>
```
### :strawberry:docker cp
copying files from containers to host
```bash
docker cp <container_id or container_name>:<source_file_path> <destination_path>
```
```bash
docker cp <location_of_file_on_host> <container_id or container_name>:<file_desinaion>
```
### :cherries:docker run -it (interactive)
run containers in interactive mode
```bash
docker container run --name <container_name> -it <image_name> /bin/bash
```
get running container in interactive mode
```bash
docker exec -it <contaner_id or container_name> /bin/bash
```
run command inside a container
```bash
docker exec -it <container_id or container_name> <command>
```
### :corn:docker run --env (set environment)
set environment variable in a container
```bash
docker run --env env_var1=value1 --env env_var1=value2 --name <container_name> <image_name>
```
set environment variable in a container from a file
```bash
docker run --env-file <path_to_the_file> --name <container_name> <image_name>
```

## :pushpin:Management
start/stop/restart/pause/un-pause containers
```bash
docker container <start,stop,restart,pause,unpause> <container_id or container_name>
```
```bash
docker <start,stop,restart,pause,unpause> <container_id or container_name>
```
delete containers
```bash
docker stop <container_name or container_id>
```
```bash
docker rm <container_name or container_id>
```
```bash
docker rm -f <container_name or container_id>
```
delete all stopped containers
```bash
docker container prune
```
delete all containers
```bash
docker rm -f $(docker ps -a -q)
```
rename containers
```bash
docker rename <old_name> <new_name>
```
### :sweet_potato:docker ps
list containers
```bash
docker ps -a
```
list containers with file size
```bash
docker ps -s
```
```bash
docker container ls -s
```
list ids of alive containers
```bash
docker ps -q
```
```bash
docker container ls -q
```
