---
title: "Openvpn server-bridge issues"
date: 2005-11-29
forum: General Help
---

### Post by Morphius on 2005-11-29
I am attempting to set up a VPN to bypass my schools firewall. I can ssh out to my box off-campus through the firewall but when I connect to my server using openvpn, I connect and am assigned an IP to the client computer, but it appears no data is traversing the tunnel. I cannot ping the server (69.44.242.142) or browse the internet. Here is the relevant information:

ifconfig server dump:

br0       Link encap:Ethernet  HWaddr 00:0D:87:49:57:BC
          inet addr:69.44.242.142  Bcast:69.44.255.255  Mask:255.255.240.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9733 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:473244 (462.1 KiB)  TX bytes:13181259 (12.5 MiB)

eth0      Link encap:Ethernet  HWaddr 00:0D:87:49:57:BC
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:236386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:185181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:4727 txqueuelen:1000
          RX bytes:184168635 (175.6 MiB)  TX bytes:32694878 (31.1 MiB)
          Interrupt:5 Base address:0xd400

eth1      Link encap:Ethernet  HWaddr 00:A0:CC:78:C1:7B
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:175451 errors:0 dropped:0 overruns:0 frame:0
          TX packets:234625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20291723 (19.3 MiB)  TX bytes:189107336 (180.3 MiB)
          Interrupt:11 Base address:0x8000

tap0      Link encap:Ethernet  HWaddr 00:FF:8E:29:99:96
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:15873 (15.5 KiB)  TX bytes:13658235 (13.0 MiB)

Server Config:

proto udp
dev tap
port 1195
ca /etc/openvpn/key.crt
cert /etc/openvpn/key.crt
server-bridge 69.44.242.142 255.255.255.0 69.44.242.200 69.44.242.201
key /etc/openvpn/key.key
dh /etc/openvpn/dh1024.pem
push "redirect-gateway def1"
push "route 69.44.242.0 255.255.255.0"
ifconfig-pool-persist ipp.txt
push "redirect-gateway"
client-to-client
duplicate-cn
keepalive 10 120
verb 5

Client Config:

proto udp
dev tap
remote 69.44.242.142 1195
mute-replay-warnings
client
ca key.crt
cert key.crt
key key.key
ping 10
verb 5

Yes I have properly bridged the connection. I am bridgeing eth0 eth1 an tap0 together. I know that this poses a security risk, however, the point of this little project is to be able to a) use samba and b) bypass the schools firewall so that I can browse as I see fit and c) allow for the use of bittorrent and other p2p.

PS
How do I put this stuff (the config info) in a scroll box to keep from cluttering up the screen?

---

