---
title: "no internet on 9.04"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by Ziv Kohav on 2009-06-13
After a clean install of Ubuntu 9.04 on a new partition I configured pppoeconf and internet worked fine. Once I rebooted the internet was gone and running pppoeconf again did not help. On 8.10 and Windows XP, on other partitions it works fine. 
Here is the output of ifconfig on 9.04 following by ifconfig on 8.10 for comparison. I'd appreciate your help- I reinstalled so many times trying to understand why this happens without success.

**IFCONFIG on Ubuntu 9.04 (no internet)**

eth0      Link encap:Ethernet  HWaddr 00:e0:4d:2b:f9:ca  
          inet6 addr: fe80::2e0:4dff:fe2b:f9ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:600 (600.0 B)  TX bytes:1132 (1.1 KB)
          Interrupt:252 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:87.68.39.54  P-t-P:87.68.32.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:54 (54.0 B)  TX bytes:54 (54.0 B)
[B]
IFCONFIG on Ubuntu 8.10 (internet works fine)[/B]

eth0      Link encap:Ethernet  HWaddr 00:e0:4d:2b:f9:ca  
          inet6 addr: fe80::2e0:4dff:fe2b:f9ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:110225 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:155148204 (155.1 MB)  TX bytes:7159457 (7.1 MB)
          Interrupt:252 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:77.125.129.61  P-t-P:77.125.128.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:110175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85098 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:152721294 (152.7 MB)  TX bytes:4943093 (4.9 MB)

---

