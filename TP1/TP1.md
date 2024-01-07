TP1 B2 LINUX

***🌞 Ajouter votre utilisateur au groupe docker*** :

`[clone@dockertp1 ~]$ sudo usermod -aG docker $(whoami)`


***🌞 Lancer un conteneur NGINX*** :    
```
[clone@dockertp1 ~]$ docker run -d -p 9999:80 nginx
Unable to find image 'nginx:latest' locally
latest: Pulling from library/nginx
24e221e92a36: Pull complete 
58cc89079bd7: Pull complete 
3799b53049f3: Pull complete 
2a580edba2f4: Pull complete 
cfe7877ea167: Pull complete 
6f26751fc54b: Pull complete 
c98494bb3682: Pull complete 
Digest: sha256:2bdc49f2f8ae8d8dc50ed00f2ee56d00385c6f8bc8a8b320d0a294d9e3b49026
Status: Downloaded newer image for nginx:latest
1c4c49ecf48bd9fcd45c1425df4418abb17d411279abd7c3299a15e8cf56ce7e
```

***🌞 Visitons*** : 

***vérifier que le conteneur est actif avec une commande qui liste les conteneurs en cours de fonctionnement*** :   

```
[clone@dockertp1 ~]$ docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS                                   NAMES
1c4c49ecf48b   nginx     "/docker-entrypoint.…"   2 minutes ago   Up 2 minutes   0.0.0.0:9999->80/tcp, :::9999->80/tcp   gifted_almeida
```

***afficher les logs du conteneur*** :    

```
[clone@dockertp1 ~]$ docker logs gifted_almeida
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2024/01/07 19:06:19 [notice] 1#1: using the "epoll" event method
2024/01/07 19:06:19 [notice] 1#1: nginx/1.25.3
2024/01/07 19:06:19 [notice] 1#1: built by gcc 12.2.0 (Debian 12.2.0-14) 
2024/01/07 19:06:19 [notice] 1#1: OS: Linux 5.14.0-362.13.1.el9_3.aarch64
2024/01/07 19:06:19 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1073741816:1073741816
2024/01/07 19:06:19 [notice] 1#1: start worker processes
2024/01/07 19:06:19 [notice] 1#1: start worker process 29
2024/01/07 19:06:19 [notice] 1#1: start worker process 30
2024/01/07 19:06:19 [notice] 1#1: start worker process 31
2024/01/07 19:06:19 [notice] 1#1: start worker process 32
```

***afficher toutes les informations relatives au conteneur avec une commande docker inspect*** : 

```
[clone@dockertp1 ~]$ docker inspect --type=container gifted_almeida
[
    {
        "Id": "1c4c49ecf48bd9fcd45c1425df4418abb17d411279abd7c3299a15e8cf56ce7e",
        "Created": "2024-01-07T19:06:19.313385129Z",
        "Path": "/docker-entrypoint.sh",
        "Args": [
            "nginx",
            "-g",
            "daemon off;"
        ],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 1593,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2024-01-07T19:06:19.649567414Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:8aea65d81da202cf886d7766c7f2691bb9e363c6b5d9b1f5d9ddaaa4bc1e90c2",
        "ResolvConfPath": "/var/lib/docker/containers/1c4c49ecf48bd9fcd45c1425df4418abb17d411279abd7c3299a15e8cf56ce7e/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/1c4c49ecf48bd9fcd45c1425df4418abb17d411279abd7c3299a15e8cf56ce7e/hostname",
        "HostsPath": "/var/lib/docker/containers/1c4c49ecf48bd9fcd45c1425df4418abb17d411279abd7c3299a15e8cf56ce7e/hosts",
        "LogPath": "/var/lib/docker/containers/1c4c49ecf48bd9fcd45c1425df4418abb17d411279abd7c3299a15e8cf56ce7e/1c4c49ecf48bd9fcd45c1425df4418abb17d411279abd7c3299a15e8cf56ce7e-json.log",
        "Name": "/gifted_almeida",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {
                "80/tcp": [
                    {
                        "HostIp": "",
                        "HostPort": "9999"
                    }
                ]
            },
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "ConsoleSize": [
                24,
                80
            ],
            "CapAdd": null,
            "CapDrop": null,
            "CgroupnsMode": "private",
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": [],
            "BlkioDeviceWriteBps": [],
            "BlkioDeviceReadIOps": [],
            "BlkioDeviceWriteIOps": [],
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": null,
            "PidsLimit": null,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware",
                "/sys/devices/virtual/powercap"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/5dac0cdc31328b27f5f78bcf6f2bddb425931458513d7e7757182da989abf9f9-init/diff:/var/lib/docker/overlay2/75e05e8c61ae09a309ed8e1380636d5fe212aac6f5c39186c2cc1827dc21a9ba/diff:/var/lib/docker/overlay2/5fd85a77f6c7c3bd8c3aca6f1f590199ac93f961d7d2e56bc0ecd5cec3bb48ab/diff:/var/lib/docker/overlay2/d03388e4695a903ed1aeaf68539414ceab38a25995f9a09cf535a4a353fb4ede/diff:/var/lib/docker/overlay2/4025a91a8730d38d09b643138e461062cffe568c3d3e1505eb3169bf7f3a76ed/diff:/var/lib/docker/overlay2/8f1428431f3f187230dc2187c4f6b00321bf6a86585281a93ec63d88754b0e02/diff:/var/lib/docker/overlay2/48b2ba89979f72837ad8242dc6d868fa851c0ebd54ab932be9bd77202e941867/diff:/var/lib/docker/overlay2/236a460c353ace4bc3994394f858a239cafd413b53f6ed06192846246daae529/diff",
                "MergedDir": "/var/lib/docker/overlay2/5dac0cdc31328b27f5f78bcf6f2bddb425931458513d7e7757182da989abf9f9/merged",
                "UpperDir": "/var/lib/docker/overlay2/5dac0cdc31328b27f5f78bcf6f2bddb425931458513d7e7757182da989abf9f9/diff",
                "WorkDir": "/var/lib/docker/overlay2/5dac0cdc31328b27f5f78bcf6f2bddb425931458513d7e7757182da989abf9f9/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "1c4c49ecf48b",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "80/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "NGINX_VERSION=1.25.3",
                "NJS_VERSION=0.8.2",
                "PKG_RELEASE=1~bookworm"
            ],
            "Cmd": [
                "nginx",
                "-g",
                "daemon off;"
            ],
            "Image": "nginx",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": [
                "/docker-entrypoint.sh"
            ],
            "OnBuild": null,
            "Labels": {
                "maintainer": "NGINX Docker Maintainers <docker-maint@nginx.com>"
            },
            "StopSignal": "SIGQUIT"
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "1990bf7f9f15c70bdbddfdb3951aae906934867ec2d3a6b0d8e981e4f24607de",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {
                "80/tcp": [
                    {
                        "HostIp": "0.0.0.0",
                        "HostPort": "9999"
                    },
                    {
                        "HostIp": "::",
                        "HostPort": "9999"
                    }
                ]
            },
            "SandboxKey": "/var/run/docker/netns/1990bf7f9f15",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "b0cb135b92ff74d6d5ee53c10c0f5020f02729b43f28eee4a966e36d7ded8dc7",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.17.0.2",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:11:00:02",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "bce8b533b1c70c1fc1c906d0578f159df32eb34f5edd5c6a1b9427d2b593ee51",
                    "EndpointID": "b0cb135b92ff74d6d5ee53c10c0f5020f02729b43f28eee4a966e36d7ded8dc7",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:02",
                    "DriverOpts": null
                }
            }
        }
    }
]

```

***afficher le port en écoute sur la VM avec un sudo ss -lnpt*** : 

```
[clone@dockertp1 ~]$ sudo ss -lnpt | grep docker
[sudo] password for clone: 
LISTEN 0      4096         0.0.0.0:9999      0.0.0.0:*    users:(("docker-proxy",pid=1545,fd=4))
LISTEN 0      4096            [::]:9999         [::]:*    users:(("docker-proxy",pid=1553,fd=4))
```

***depuis le navigateur de votre PC, visiter le site web sur http://IP_VM:9999*** :   

```
[clone@dockertp1 ~]$ curl 192.168.128.5:9999
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```
***🌞 On va ajouter un site Web au conteneur NGINX*** :   

```
[clone@dockertp1 nginx]$ docker run -d -p 9999:8080 -v /home/clone/nginx/index.html:/var/www/html/index.html -v /home/clone/nginx/site_nul.conf:/etc/nginx/conf.d/site_nul.conf nginx
f62abdfb76a48ce9dc79cd7a4ca04f6d1065c986748498b8d33ed266b4091a6d
```

***🌞 Visitons*** :    

***vérifier que le conteneur est actif*** :    

```
[clone@dockertp1 nginx]$ docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS                                               NAMES
f62abdfb76a4   nginx     "/docker-entrypoint.…"   7 seconds ago   Up 6 seconds   80/tcp, 0.0.0.0:9999->8080/tcp, :::9999->8080/tcp   romantic_faraday
```
***🌞 Lance un conteneur Python, avec un shell***

```
[clone@dockertp1 ~]$ docker run -it python bash
Unable to find image 'python:latest' locally
latest: Pulling from library/python
b66b4ecd3ecf: Pull complete 
6c641d36985b: Pull complete 
ddd8544b6e15: Pull complete 
ae58c7c06d64: Pull complete 
f9f35f1c3178: Pull complete 
0d89c447e056: Pull complete 
9862771c91cc: Pull complete 
93aa698c30e4: Pull complete 
Digest: sha256:3733015cdd1bd7d9a0b9fe21a925b608de82131aa4f3d397e465a1fcb545d36f
Status: Downloaded newer image for python:latest
root@32ce98132385:/#
```

***🌞 Installe des libs Python*** 

`root@32ce98132385:/# pip install aiohttp aioconsole`

***🌞 Récupérez des images*** 

```
[clone@dockertp1 ~]$ docker pull python:3.11
[clone@dockertp1 ~]$ docker pull mysql:5.7
[clone@dockertp1 ~]$ docker pull wordpress:latest
[clone@dockertp1 ~]$ docker pull linuxserver/wikijs
```

```
[clone@dockertp1 ~]$ docker image ls
REPOSITORY           TAG       IMAGE ID       CREATED        SIZE
linuxserver/wikijs   latest    3e1a763e7f63   2 days ago     459MB
python               latest    b3148b8eb04d   4 weeks ago    1.02GB
wordpress            latest    430cba9ccb95   4 weeks ago    740MB
python               3.11      f983f601e9a2   4 weeks ago    1.01GB
nginx                latest    8aea65d81da2   2 months ago   192MB
hello-world          latest    ee301c921b8a   8 months ago   9.14kB
```

***🌞 Lancez un conteneur à partir de l'image Python*** 

```
[clone@dockertp1 ~]$ docker run -it python:3.11 bash
root@bba88733900e:/# python --version
Python 3.11.7
```

***🌞 Ecrire un Dockerfile pour une image qui héberge une application Python***

***🌞 Build l'image*** : 

```
[clone@dockertp1 python_app_build]$ docker build . -t python_app:version_de_ouf
[+] Building 71.3s (11/11) FINISHED                                                                                             docker:default
 => [internal] load build definition from Dockerfile                                                                                      0.0s
 => => transferring dockerfile: 252B                                                                                                      0.0s
 => [internal] load .dockerignore                                                                                                         0.0s
 => => transferring context: 2B                                                                                                           0.0s
 => [internal] load metadata for docker.io/library/debian:latest                                                                          1.2s
 => [1/6] FROM docker.io/library/debian@sha256:bac353db4cc04bc672b14029964e686cd7bad56fe34b51f432c1a1304b9928da                           0.0s
 => => resolve docker.io/library/debian@sha256:bac353db4cc04bc672b14029964e686cd7bad56fe34b51f432c1a1304b9928da                           0.0s
 => => sha256:80f7f4d265b23835f210c95cea5105ed01ea4d591c2bd58fc774f6e25ee16a39 1.48kB / 1.48kB                                            0.0s
 => => sha256:bac353db4cc04bc672b14029964e686cd7bad56fe34b51f432c1a1304b9928da 1.85kB / 1.85kB                                            0.0s
 => => sha256:104df696a52d049c4d210554795d6b3a03f5d0ffe9a11fdc89b9d4909ea019e2 529B / 529B                                                0.0s
 => [internal] load build context                                                                                                         0.0s
 => => transferring context: 188B                                                                                                         0.0s
 => [2/6] RUN apt update                                                                                                                  3.1s
 => [3/6] RUN apt install python3 -y                                                                                                      6.4s 
 => [4/6] RUN apt install pip -y                                                                                                         57.7s 
 => [5/6] RUN apt install python3-emoji                                                                                                   1.8s 
 => [6/6] COPY app.py .                                                                                                                   0.0s 
 => exporting to image                                                                                                                    1.0s 
 => => exporting layers                                                                                                                   1.0s 
 => => writing image sha256:01ac370d53ecef49e4724ba2a355188a132f8ba59d44552d8394314d46e9c734                                              0.0s 
 => => naming to docker.io/library/python_app:version_de_ouf   
```
***🌞 Lancer l'image***

```
[clone@dockertp1 python_app_build]$ docker run python_app:version_de_ouf                                                                       
Cet exemple d'application est vraiment naze 👎
```


***🌞 Créez un fichier docker-compose.yml***

***🌞 Lancez les deux conteneurs avec docker compose***

```
[clone@dockertp1 compose_test]$ docker compose up -d
[+] Running 3/3
 ✔ conteneur_flopesque Pulled                                                                                                             7.8s 
 ✔ conteneur_nul 1 layers [⣿]      0B/0B      Pulled                                                                                      6.9s 
   ✔ b66b4ecd3ecf Already exists                                                                                                          0.0s 
[+] Running 3/3
 ✔ Network compose_test_default                  Created                                                                                  0.2s 
 ✔ Container compose_test-conteneur_nul-1        Started                                                                                  0.0s 
 ✔ Container compose_test-conteneur_flopesque-1  Started                                                                                  0.0s 
```
***🌞 Vérifier que les deux conteneurs tournent*** 

```
[clone@dockertp1 compose_test]$ docker ps
CONTAINER ID   IMAGE     COMMAND        CREATED          STATUS          PORTS     NAMES
74b7fb85ac6b   debian    "sleep 9999"   47 seconds ago   Up 46 seconds             compose_test-conteneur_flopesque-1
e3b7ed2b83dd   debian    "sleep 9999"   47 seconds ago   Up 46 seconds             compose_test-conteneur_nul-1
```
***🌞 Pop un shell dans le conteneur conteneur_nul***

```
root@e3b7ed2b83dd:/# ping compose_test-conteneur_flopesque-1
PING compose_test-conteneur_flopesque-1 (172.18.0.3) 56(84) bytes of data.
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.3): icmp_seq=1 ttl=64 time=0.166 ms
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.3): icmp_seq=2 ttl=64 time=0.322 ms
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.3): icmp_seq=3 ttl=64 time=0.342 ms
^C
--- compose_test-conteneur_flopesque-1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2065ms
rtt min/avg/max/mdev = 0.166/0.276/0.342/0.078 ms
```










