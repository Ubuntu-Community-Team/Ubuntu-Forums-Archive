---
title: "ethernet not working"
date: 2010-03-01
forum: Hardware
---

### Post by desmane on 2010-03-01
Hi there, 

running thinkpad x200, docking station.. 

ethernet does work sometimes, but mostly its not available in gnome network manager (says: Wired Network: Disconnected) (forwarded through docking station or plugged in directly)

Any idea why it sometimes suddenly comes up but is mostly unavailable??

```
lspci
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300

```

```
eth0      Link encap:Ethernet  HWaddr 00:1f:16:0f:24:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:48045 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49911590 (49.9 MB)  TX bytes:7592402 (7.5 MB)
          Memory:f2600000-f2620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5832 (5.8 KB)  TX bytes:5832 (5.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6a:33:dc:68  
          inet addr:192.168.178.60  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6aff:fe33:dc68/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34759 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30956275 (30.9 MB)  TX bytes:6156277 (6.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-6A-33-DC-68-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

```
dmesg | grep eth
[    2.252581] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1f:16:0f:24:33
[    2.252584] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.252616] 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: 1008ff-0ff
[   21.381633] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.010173] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   23.010176] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   23.010414] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   33.930084] eth0: no IPv6 routers present
[ 7826.593359] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 9202.371994] ADDRCONF(NETDEV_UP): eth0: link is not ready
[11595.860471] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

---

