# TP1 : Premiers pas Docker

## I. Init
### 🌞 Ajouter votre utilisateur au groupe docker
```
[toto@docker1 ~]$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
### 🌞 Lancer un conteneur NGINX
```
[toto@docker1 ~]$ docker run -d -p 9999:80 nginx
Unable to find image 'nginx:latest' locally
latest: Pulling from library/nginx
bc0965b23a04: Pull complete
650ee30bbe5e: Pull complete
8cc1569e58f5: Pull complete
362f35df001b: Pull complete
13e320bf29cd: Pull complete
7b50399908e1: Pull complete
57b64962dd94: Pull complete
Digest: sha256:fb197595ebe76b9c0c14ab68159fd3c08bd067ec62300583543f0ebda353b5be
Status: Downloaded newer image for nginx:latest
9871fcfefb94bb6590771347555cef50bea77194f09bc2a2b492cf1d63cfd5e9
```
### 🌞 Visitons
```
[toto@docker1 ~]$ docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS                                     NAMES
9871fcfefb94   nginx     "/docker-entrypoint.…"   2 minutes ago   Up 2 minutes   0.0.0.0:9999->80/tcp, [::]:9999->80/tcp   hungry_wescoff
```
```
[toto@docker1 ~]$ docker logs 9871fcfefb94
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2024/12/12 08:35:21 [notice] 1#1: using the "epoll" event method
2024/12/12 08:35:21 [notice] 1#1: nginx/1.27.3
2024/12/12 08:35:21 [notice] 1#1: built by gcc 12.2.0 (Debian 12.2.0-14)
2024/12/12 08:35:21 [notice] 1#1: OS: Linux 5.14.0-503.15.1.el9_5.x86_64
2024/12/12 08:35:21 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1073741816:1073741816
2024/12/12 08:35:21 [notice] 1#1: start worker processes
2024/12/12 08:35:21 [notice] 1#1: start worker process 28
```
```
[toto@docker1 ~]$ docker inspect 9871fcfefb94
[
    {
        "Id": "9871fcfefb94bb6590771347555cef50bea77194f09bc2a2b492cf1d63cfd5e9",
        "Created": "2024-12-12T08:35:21.302842282Z",
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
            "Pid": 1891,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2024-12-12T08:35:21.484373992Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:66f8bdd3810c96dc5c28aec39583af731b34a2cd99471530f53c8794ed5b423e",
        "ResolvConfPath": "/var/lib/docker/containers/9871fcfefb94bb6590771347555cef50bea77194f09bc2a2b492cf1d63cfd5e9/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/9871fcfefb94bb6590771347555cef50bea77194f09bc2a2b492cf1d63cfd5e9/hostname",
        "HostsPath": "/var/lib/docker/containers/9871fcfefb94bb6590771347555cef50bea77194f09bc2a2b492cf1d63cfd5e9/hosts",
        "LogPath": "/var/lib/docker/containers/9871fcfefb94bb6590771347555cef50bea77194f09bc2a2b492cf1d63cfd5e9/9871fcfefb94bb6590771347555cef50bea77194f09bc2a2b492cf1d63cfd5e9-json.log",
        "Name": "/hungry_wescoff",
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
            "NetworkMode": "bridge",
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
                30,
                120
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
            "Ulimits": [],
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
                "LowerDir": "/var/lib/docker/overlay2/ac7498f31bd0e32e8322a4471370c1cd71ccab2d49e972e9e858c6d528f7c16a-init/diff:/var/lib/docker/overlay2/f139e01650dfb9d6ebb0d7fa2d4e31eaeac0f09a3bb0ff910484a6ecc3ca8274/diff:/var/lib/docker/overlay2/5a72674b896f942c269ff8c80022c63f380aea3cba6a322dba3b5877ab0d4d8a/diff:/var/lib/docker/overlay2/6dafe10c84fb159d44dc9ada3cdc6a119e20578d0f3f10b13c5fb1aad94b4dc1/diff:/var/lib/docker/overlay2/67ecbdb38ebd01e1dadf47478bd230adbe057924667ca201eb497d66ca1e726c/diff:/var/lib/docker/overlay2/fa9107322359062a548e21bb963ac1dd4e8c5a883ad6dbb6c5468fff3a878a14/diff:/var/lib/docker/overlay2/82f1fe59220df9e4c4557603ea1d067e28f61f4ff4f4f0f66e8b3fece7266900/diff:/var/lib/docker/overlay2/23a415f4b68aa61727ea097f543e1990eb59ca1fee199d4b6000eaa1ec0aaea5/diff",
                "MergedDir": "/var/lib/docker/overlay2/ac7498f31bd0e32e8322a4471370c1cd71ccab2d49e972e9e858c6d528f7c16a/merged",
                "UpperDir": "/var/lib/docker/overlay2/ac7498f31bd0e32e8322a4471370c1cd71ccab2d49e972e9e858c6d528f7c16a/diff",
                "WorkDir": "/var/lib/docker/overlay2/ac7498f31bd0e32e8322a4471370c1cd71ccab2d49e972e9e858c6d528f7c16a/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "9871fcfefb94",
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
                "NGINX_VERSION=1.27.3",
                "NJS_VERSION=0.8.7",
                "NJS_RELEASE=1~bookworm",
                "PKG_RELEASE=1~bookworm",
                "DYNPKG_RELEASE=1~bookworm"
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
            "SandboxID": "37d365902fc8e3bbe6eb5d8300ae9f92ddd08710d315e72c5a6c4ef7b1156a45",
            "SandboxKey": "/var/run/docker/netns/37d365902fc8",
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
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "6840e2e4fe9ae9f51fa2887a9842177ddc2b7cbb135f721992acaa6e0ef41e6e",
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
                    "MacAddress": "02:42:ac:11:00:02",
                    "DriverOpts": null,
                    "NetworkID": "cb90d4cf0867b7a9c6f7a0c55b1a092d77447168e24547a95e5d66c2a1aac51f",
                    "EndpointID": "6840e2e4fe9ae9f51fa2887a9842177ddc2b7cbb135f721992acaa6e0ef41e6e",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "DNSNames": null
                }
            }
        }
    }
]
```
```
[toto@docker1 ~]$ sudo ss -lnpt
State     Recv-Q    Send-Q       Local Address:Port       Peer Address:Port   Process
LISTEN    0         4096               0.0.0.0:9999            0.0.0.0:*       users:(("docker-proxy",pid=1840,fd=4))
LISTEN    0         128                0.0.0.0:22              0.0.0.0:*       users:(("sshd",pid=700,fd=3))
LISTEN    0         4096                  [::]:9999               [::]:*       users:(("docker-proxy",pid=1847,fd=4))
LISTEN    0         128                   [::]:22                 [::]:*       users:(("sshd",pid=700,fd=4))
```
```
[toto@docker1 ~]$ curl http://10.6.6.11:9999/
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

### 🌞 On va ajouter un site Web au conteneur NGINX
```
[toto@docker1 nginx]$ docker run -d -p 9999:8080 -v /home/toto/nginx/index.html:/var/www/html/index.html -v /home/toto/nginx/site_nul.conf:/etc/nginx/conf.d/site_nul.conf nginx
f7004d1896284aec0d34cb2dbd299d8c66d2171e7da9beca41adaf67449fa290
```
### 🌞 Visitons
```
[toto@docker1 nginx]$ curl http://10.6.6.11:9999/
MEOOOOOOOOOOOW
```

### 🌞 Lance un conteneur Python, avec un shell
```
[toto@docker1 nginx]$ docker run -it python bash
Unable to find image 'python:latest' locally
latest: Pulling from library/python
fdf894e782a2: Pull complete
5bd71677db44: Pull complete
551df7f94f9c: Pull complete
ce82e98d553d: Pull complete
5f0e19c475d6: Pull complete
abab87fa45d0: Pull complete
2ac2596c631f: Pull complete
Digest: sha256:9255d1993f6d28b8a1cd611b108adbdfa38cb7ccc46ddde8ea7d734b6c845e32
Status: Downloaded newer image for python:latest
root@8658e63dd005:/#
```
### 🌞 Installe des libs Python
```
root@8658e63dd005:/# pip install aiohttp
Collecting aiohttp
  Downloading aiohttp-3.11.10-cp313-cp313-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (7.7 kB)
Collecting aiohappyeyeballs>=2.3.0 (from aiohttp)
  Downloading aiohappyeyeballs-2.4.4-py3-none-any.whl.metadata (6.1 kB)
Collecting aiosignal>=1.1.2 (from aiohttp)
  Downloading aiosignal-1.3.1-py3-none-any.whl.metadata (4.0 kB)
Collecting attrs>=17.3.0 (from aiohttp)
  Downloading attrs-24.2.0-py3-none-any.whl.metadata (11 kB)
Collecting frozenlist>=1.1.1 (from aiohttp)
  Downloading frozenlist-1.5.0-cp313-cp313-manylinux_2_5_x86_64.manylinux1_x86_64.manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (13 kB)
Collecting multidict<7.0,>=4.5 (from aiohttp)
  Downloading multidict-6.1.0-cp313-cp313-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (5.0 kB)
Collecting propcache>=0.2.0 (from aiohttp)
  Downloading propcache-0.2.1-cp313-cp313-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (9.2 kB)
Collecting yarl<2.0,>=1.17.0 (from aiohttp)
  Downloading yarl-1.18.3-cp313-cp313-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (69 kB)
Collecting idna>=2.0 (from yarl<2.0,>=1.17.0->aiohttp)
  Downloading idna-3.10-py3-none-any.whl.metadata (10 kB)
Downloading aiohttp-3.11.10-cp313-cp313-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (1.7 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 1.7/1.7 MB 6.4 MB/s eta 0:00:00
Downloading aiohappyeyeballs-2.4.4-py3-none-any.whl (14 kB)
Downloading aiosignal-1.3.1-py3-none-any.whl (7.6 kB)
Downloading attrs-24.2.0-py3-none-any.whl (63 kB)
Downloading frozenlist-1.5.0-cp313-cp313-manylinux_2_5_x86_64.manylinux1_x86_64.manylinux_2_17_x86_64.manylinux2014_x86_64.whl (267 kB)
Downloading multidict-6.1.0-cp313-cp313-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (131 kB)
Downloading propcache-0.2.1-cp313-cp313-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (227 kB)
Downloading yarl-1.18.3-cp313-cp313-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (339 kB)
Downloading idna-3.10-py3-none-any.whl (70 kB)
Installing collected packages: propcache, multidict, idna, frozenlist, attrs, aiohappyeyeballs, yarl, aiosignal, aiohttp
Successfully installed aiohappyeyeballs-2.4.4 aiohttp-3.11.10 aiosignal-1.3.1 attrs-24.2.0 frozenlist-1.5.0 idna-3.10 multidict-6.1.0 propcache-0.2.1 yarl-1.18.3
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager, possibly rendering your system unusable.It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv. Use the --root-user-action option if you know what you are doing and want to suppress this warning.
root@8658e63dd005:/# pip install aioconsole
Collecting aioconsole
  Downloading aioconsole-0.8.1-py3-none-any.whl.metadata (46 kB)
Downloading aioconsole-0.8.1-py3-none-any.whl (43 kB)
Installing collected packages: aioconsole
Successfully installed aioconsole-0.8.1
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager, possibly rendering your system unusable.It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv. Use the --root-user-action option if you know what you are doing and want to suppress this warning.
root@8658e63dd005:/# python
Python 3.13.1 (main, Dec  4 2024, 20:40:27) [GCC 12.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import aiohttp
```
## II. Images
### 🌞 Récupérez des images
```
[toto@docker1 ~]$ docker images
REPOSITORY           TAG       IMAGE ID       CREATED         SIZE
linuxserver/wikijs   latest    863e49d2e56c   5 days ago      465MB
python               3.13      3ca4060004b1   8 days ago      1.02GB
python               latest    3ca4060004b1   8 days ago      1.02GB
nginx                latest    66f8bdd3810c   2 weeks ago     192MB
wordpress            latest    c89b40a25cd1   2 weeks ago     700MB
mysql                5.7       5107333e08a8   12 months ago   501MB
hello-world          latest    d2c94e258dcb   19 months ago   13.3kB
```
### 🌞 Lancez un conteneur à partir de l'image Python
```
[toto@docker1 ~]$ docker run -it python bash
root@d258ed5ffed7:/# python --version
Python 3.13.1
```
### 🌞 Ecrire un Dockerfile pour une image qui héberge une application Python
```
[toto@docker1 ~]$ sudo cat python_app_build/dockerfile
FROM debian

RUN apt update -y && apt install -y python3 python3 pip && apt install -y python3.11-venv

RUN python3 -m venv /venv && \
    /venv/bin/pip install --upgrade pip && \
    /venv/bin/pip install emoji

COPY app.py /

ENTRYPOINT ["/venv/bin/python", "app.py"]
```
### 🌞 Build l'image
```
[toto@docker1 python_app_build]$ docker build . -t python_app:version_de_ouf
[+] Building 454.0s (9/9) FINISHED                                                                       docker:default
 => [internal] load build definition from dockerfile                                                               0.1s
 => => transferring dockerfile: 356B                                                                               0.0s
 => [internal] load metadata for docker.io/library/debian:latest                                                   0.6s
 => [internal] load .dockerignore                                                                                  0.1s
 => => transferring context: 2B                                                                                    0.0s
 => CACHED [1/4] FROM docker.io/library/debian:latest@sha256:17122fe3d66916e55c0cbd5bbf54bb3f87b3582f4d86a755a0fd  0.0s
 => [internal] load build context                                                                                  0.2s
 => => transferring context: 86B                                                                                   0.1s
 => [2/4] RUN apt update -y && apt install -y python3 python3 pip && apt install -y python3.11-venv              290.8s
 => [3/4] RUN python3 -m venv /venv &&     /venv/bin/pip install --upgrade pip &&     /venv/bin/pip install emoj  50.2s
 => [4/4] COPY app.py /                                                                                            0.8s
 => exporting to image                                                                                           109.5s
 => => exporting layers                                                                                          109.2s
 => => writing image sha256:56bba04c80abad7c53f325d40ae820a16d46ab6506067d962d7328c1ff8fe862                       0.0s
 => => naming to docker.io/library/python_app:version_de_ouf
```
### 🌞 Lancer l'image
```
[toto@docker1 python_app_build]$ docker run python_app:version_de_ouf
Cet exemple d'application est vraiment naze 👎
```
## III. Docker compose
### 🌞 Créez un fichier docker-compose.yml
```
[toto@docker1 ~]$ sudo cat compose_test/docker-compose.yml
version: "3"

services:
  conteneur_nul:
    image: debian
    entrypoint: sleep 9999
  conteneur_flopesque:
    image: debian
    entrypoint: sleep 9999
```
### 🌞 Lancez les deux conteneurs avec docker compose
```
[toto@docker1 compose_test]$ docker compose up -d
WARN[0000] /home/toto/compose_test/docker-compose.yml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion
[+] Running 3/3
 ✔ conteneur_nul Pulled                                                                                            3.1s
 ✔ conteneur_flopesque Pulled                                                                                      2.8s
   ✔ fdf894e782a2 Already exists                                                                                   0.0s
[+] Running 3/3
 ✔ Network compose_test_default                  Created                                                           0.9s
 ✔ Container compose_test-conteneur_flopesque-1  Started                                                           0.8s
 ✔ Container compose_test-conteneur_nul-1        Started
```
### 🌞 Vérifier que les deux conteneurs tournent
```
[toto@docker1 compose_test]$ docker compose ps
WARN[0000] /home/toto/compose_test/docker-compose.yml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion
NAME                                 IMAGE     COMMAND        SERVICE               CREATED          STATUS          PORTS
compose_test-conteneur_flopesque-1   debian    "sleep 9999"   conteneur_flopesque   51 seconds ago   Up 50 seconds
compose_test-conteneur_nul-1         debian    "sleep 9999"   conteneur_nul         51 seconds ago   Up 50 seconds
```
### 🌞 Pop un shell dans le conteneur conteneur_nul
```
[toto@docker1 compose_test]$ docker exec -it compose_test-conteneur_nul-1 bash
root@461e79c0e6e0:/# apt update
root@461e79c0e6e0:/# apt install -y iputils-ping
root@461e79c0e6e0:/# ping conteneur_flopesque
PING conteneur_flopesque (172.18.0.3) 56(84) bytes of data.
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.3): icmp_seq=1 ttl=64 time=0.280 ms
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.3): icmp_seq=2 ttl=64 time=0.392 ms
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.3): icmp_seq=3 ttl=64 time=0.182 ms
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.3): icmp_seq=4 ttl=64 time=0.081 ms
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.3): icmp_seq=5 ttl=64 time=0.050 ms
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.3): icmp_seq=6 ttl=64 time=0.080 ms
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.3): icmp_seq=7 ttl=64 time=0.047 ms
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.3): icmp_seq=8 ttl=64 time=0.050 ms
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.3): icmp_seq=9 ttl=64 time=0.111 ms
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.3): icmp_seq=10 ttl=64 time=0.050 ms
64 bytes from compose_test-conteneur_flopesque-1.compose_test_default (172.18.0.3): icmp_seq=11 ttl=64 time=0.059 ms
^C
--- conteneur_flopesque ping statistics ---
11 packets transmitted, 11 received, 0% packet loss, time 10231ms
rtt min/avg/max/mdev = 0.047/0.125/0.392/0.108 ms
```