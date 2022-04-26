**备忘录**
apt-get update	更新软件
apt-get upgrade	更新列表
apt-get install wget && apt-get update -y && apt-get install curl -y  	安装wget,curl
apt-get -y install sudo	


**防火墙**
systemctl stop firewalld.service 
systemctl disable firewalld.service 
service iptables stop 
chkconfig iptables off
或者开放所有端口!
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -F
/etc/init.d/ufw stop


rm -rf /etc/localtime	#**时间校准**
ln -s /usr/share/zoneinfo/Asia/Shanghai /etc/localtime	
	
  
curl -sSL https://get.daocloud.io/docker | sh	**安装docker**
curl -L https://get.daocloud.io/docker/compose/releases/download/v2.3.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose	安装 Docker Compose
chmod +x /usr/local/bin/docker-compose	
	
  
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf	**BBR加速**
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf	
sysctl -p	
lsmod | grep bbr	
	
  
curl -sSO https://raw.githubusercontent.com/zhucaidan/btpanel-v7.7.0/main/install/install_panel.sh && bash install_panel.sh	**宝塔7.7**
sed -i "s|if (bind_user == 'True') {|if (bind_user == 'REMOVED') {|g" /www/server/panel/BTPanel/static/js/index.js	
rm -rf /www/server/panel/data/bind.pl	
	
  
mkdir x-ui && cd x-ui	X-ui docker
docker run -itd --network=host -v $PWD/db/:/etc/x-ui/ -v $PWD/cert/:/root/cert/ --name x-ui --restart=unless-stopped enwaiax/x-ui:latest	
	
  
bash <(curl -s -L https://233blog.com/v2ray.sh) false	V2ray
bash <(curl -sL https://raw.githubusercontent.com/veip007/scripts/master/xray.sh)	
wget -P /root -N --no-check-certificate "https://raw.githubusercontent.com/mack-a/v2ray-agent/master/install.sh" && chmod 700 /root/install.sh && /root/install.sh	8合1
	
  
wget -q https://gitee.com/yanyuwangluo/onekey/raw/master/Onkey/xinql.sh -O xinql.sh && bash xinql.sh	**青龙面板**
docker exec -it qinglong bash -c  "$(curl -fsSL https://ghproxy.com/https://raw.githubusercontent.com/shidahuilang/QL-/main/npm.sh)" 	**安装青龙依赖命令**
docker exec -it qinglong bash 	
ql repo https://github.com/KingRan/KR.git "jd_|jx_|jdCookie" "activity|backUp" "^jd[^_]|USER|utils|function|sign|sendNotify|ql|JDJR"	
docker exec -it qinglong pnpm install moment	
ql repo https://github.com/Zy143L/wskey.git "wskey"	
33 */3 * * *
  
bash <(curl -sSL https://cdn.jsdelivr.net/gh/SuperManito/LinuxMirrors@main/ChangeMirrors.sh)	**Linux 一键更换国内软件源脚本**
wget -qO- 1keydd.com/inst.sh | bash -s - -t deb	**5K哥 DD脚本**
wget -O box.sh https://raw.githubusercontent.com/BlueSkyXN/SKY-BOX/main/box.sh && chmod +x box.sh && clear && ./box.sh	


bash <(wget -qO- https://git.io/mtg.sh)  
systemctl disable mtg #卸载
systemctl stop mtg 
rm -f /usr/local/bin/mtg /etc/systemd/system/mtg.service /etc/mtg.toml


https://github.com/Chasing66/beautiful_docker/tree/main/x-ui
mkdir x-ui && cd x-ui
docker run -itd --network=host -v $PWD/db/:/etc/x-ui/ -v $PWD/cert/:/root/cert/ --name x-ui --restart=unless-stopped enwaiax/x-ui:latest
https://github.com/stilleshan/dockerfiles/tree/main/x-ui/x-ui-ssl


https://hub.docker.com/r/ffdfgdfg/nps
docker pull ffdfgdfg/nps
docker run -d --name nps --net=host -v /root/conf:/conf ffdfgdfg/nps
注意事项:①NPS内网穿透占用服务端默认占用的端口:80 443 8080 8024（必要的端口一定要放行，不然无法启动服务，在使用其他端口的时候也需要放行或者关闭防火墙）




wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh"	
chmod +x tcp.sh	**重装系统**
./tcp.sh	
curl -fLO https://raw.githubusercontent.com/bohanyang/debi/master/debi.sh && chmod a+rx debi.sh	
./debi.sh --cdn --network-console --ethx --bbr --user root --password 密码
shutdown -r now	

