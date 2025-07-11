# zivan的记事本
### 为了方便封个reality的镜像
```docker pull ghcr.io/zivan80/aquarzray:latest```
或者
```docker pull aquarz/aquarzray```
#### 命令行用:
```docker volume create xray_keys
docker run -d --name aquarzray --restart always \
-p 443:443 \
-v xray_keys:/app/keys \
-e SERVER_IP=YOUR_SERVER_IP \
-e UUID=YOUR_UUID \
-e REALITY_DEST=www.microsoft.com:443 \
-e REALITY_SERVER_NAMES=www.microsoft.com \
-e FINGERPRINT=firefox \
aquarzray:latest```

#### docker-compose.yaml
```services:
  xray:
    image: aquarzray:latest
    container_name: aquarzray
    restart: always
    ports:
      - "443:443"
    volumes:
      - ./config.env:/app/config.env
      - xray_keys:/app/keys

volumes:
  xray_keys:```
#### config.env 环境变量
```SERVER_IP=YOUR_SERVER_IP

UUID=87da4aff-03ad-40a9-86ae-ec6f6e2de620
#UUID command: cat /proc/sys/kernel/random/uuid
REALITY_DEST=www.microsoft.com:443
REALITY_SERVER_NAMES=www.microsoft.com
FINGERPRINT=firefox```
### 一个好用的API
```
curl 3.0.3.0/ip/8.8.8.8
```
### 自用iptv
- [订阅地址](iptv.m3u)

### 方便删减cloudflare上域名a记录
- [批量添加](https://github.com/zivan80/Scripts/blob/master/src/cloudflare/bulk_add.py)
- [列表/单个删除](https://github.com/zivan80/Scripts/blob/master/src/cloudflare/single_del.py)
  - 同目录下要放一个[proxyip.txt](https://github.com/zivan80/Scripts/blob/master/src/cloudflare/proxyip.txt)文件，写入优选后的IP

### 用GPT写了一个方便查IP的页面
- [GitHub上](https://zivan80.github.io/note/checkip)
- [Cloudflare上](https://ip.nnmm.fun)
- [serv00](https://zivan.pp.ua)
