---
title: "Ubuntu Server, Clutch, Port forwarding, Speed"
date: 2008-10-10
forum: General Help
---

### Post by spr- on 2008-10-10
Hi,

I just apt-got clutch (0.4-0ubuntu5) on Ubuntu (Server) 8.04.1 and it's working, but the download speed is abnormally low (2-10kB/s) and the torrent has enough downloaders/seeders (6000+). I've forwarded the port stated in the Preferences (51413). uTorrent on my Windows machine works fine. Is there anything else that could be influencing the download speed?

Cheers,

spr-

Edit: [http://www.utorrent.com/testport.php?port=51413](http://www.utorrent.com/testport.php?port=51413) shows the port is open.

---

### Post by spr- on 2008-10-10
Anything?

It seems that this is not a Clutch/Transmission-related problem. Other torrent application have the same problem. It feels like this is somehow an Ubuntu-related problem. I read there isn't any firewall installed by default, is there?

---

### Post by spr- on 2008-10-12
Clutch/Transmission listens on 51413.
Ports are forwarded (TCP&UDP 51413 to 51413).
Same problem with any torrent client on the machine. (Also tried bittornado and ctorrent.)
Torrents work fine on my Windows machine.
ISP doesn't throttle.
Upload speed is limited. (Not that that ever reaches it max as I don't download anything, so I don't have one byte to upload.)
netstat -a shows about 120 torrent-related ESTABLISHED tcp connections with 0 bytes received/sent.

iptables -L:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
netstat -a | grep LISTEN:
```
tcp        0      0 localhost:mysql         *:*                     LISTEN
tcp        0      0 *:www                   *:*                     LISTEN
tcp        0      0 *:munin                 *:*                     LISTEN
_**tcp        0      0 *:51413                 *:*                     LISTEN**_
tcp        0      0 *:https                 *:*                     LISTEN
```
ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:7d:12:82
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe7d:1282/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7041 errors:0 dropped:460076763 overruns:0 frame:0
          TX packets:7590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1895779 (1.8 MB)  TX bytes:906388 (885.1 KB)
          Interrupt:220 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:33674 (32.8 KB)  TX bytes:33674 (32.8 KB)
```

Is there **ANYTHING** I have overlooked? Is there anyone having the same problems?

---

