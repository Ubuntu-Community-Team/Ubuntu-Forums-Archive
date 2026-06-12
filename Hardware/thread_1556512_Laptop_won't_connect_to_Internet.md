---
title: "Laptop won't connect to Internet"
date: 2010-08-19
forum: Hardware
---

### Post by blaporte on 2010-08-19
I have a Compaq Presario V3000 with a Broadcom Network card. I got the driver working and can connect to the wireless network but cannot get on the internet.  I have Ubuntu 10.04 installed. I can plug into the LAN and get onto the internet but the wireless will not work.

---

### Post by blaporte on 2010-08-19
I ran ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:16:d3:09:1a:61  
          inet6 addr: fe80::216:d3ff:fe09:1a61/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3095 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3606634 (3.6 MB)  TX bytes:368816 (368.8 KB)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr 00:14:a5:bc:34:d2  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:febc:34d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:52416
          TX packets:43 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:9590 (9.5 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:712 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55912 (55.9 KB)  TX bytes:55912 (55.9 KB)

My internet default gateway is 192.168.0.1 so I am not sure why it is not pulling a correct IP address. Because when I connect the LAN it pulls an IP address of 192.168.0.243

---

