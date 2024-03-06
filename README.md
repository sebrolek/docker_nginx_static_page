# Static HTML page inside docker container using NGINX (LIVE)

## A fully functional docker project for webserving purposes
This project is using NGINX to serve sample HTML webpage about apes. Webserver is executed inside docker container. Everything is working on free VPS (https://frog.mikr.us/) with Alpine Linux distribution.

## Project diagram
![github](https://github.com/sebrolek/docker_nginx_static_page/assets/161625733/d5e73e24-5e97-455c-a4cf-68f4076f2cec)

## Prerequisites
Docker installed.

## System Setup during testing
- Alpine Linux 3.19.1
- Docker Desktop 4.27.1
  
## Setup
1. Clone this project
2. Transfer all files to your VPS (using i.e. SCP)
3. Use this command to build docker image: `docker build -t nginx_server:v1 .`  

To list all the created docker images use this command in terminal: `docker images`  
<img width="650" alt="images" src="https://github.com/sebrolek/docker_nginx_static_page/assets/161625733/3eb63b0c-09bd-4565-8ff1-1c39e8339d49">

4. Run the following command to spin up the container server:  
`docker run --rm -d --name nginx_container_1 -p 192.168.14.47:21447:80 nginx_server:v1`

If you want to deploy it locally set up port flag as `-p 3000:80`. In such case you can visit your page under: http://localhost:3000/

Note: Flag `-p` is set up with private IP, as I don't have public IPv4 on this VPS. Nevertheless, port 21447 is unique for me.  
Also, 192.168.14.47:21447 = frog01.mikr.us:21447 in my case.

To list all the containers running use this command in terminal: `docker ps -a`
<img width="850" alt="containers" src="https://github.com/sebrolek/docker_nginx_static_page/assets/161625733/e610e8e9-eade-454a-976c-2ffad2473d7c">

5. Visit webpage (http://frog01.mikr.us:21447) using browser or via `curl http://frog01.mikr.us:21447` in shell

6. Cleanup:
  - To stop the container that is running use this command: `docker stop {container_id}`
  - To delete the container that was created use this command: `docker rm {container_id}` (remember to stop it before)
  - To delete the docker image that was created: `docker rmi {image_id}`
