---
title: "Netgear wg511 v2 (Made in China) IBM T20"
date: 2008-08-08
forum: Hardware
---

### Post by Twelveone on 2008-08-08
Hi,

I have an old IBM Thinkpad T20 with a Netgear WG511 v2 (made in China). I've had it running on Windows XP Pro and have decided to ditch Windows and install Ubuntu 8.04 (Hardy Heron). The problem is I can't get the wifi card to work. I've tried various threads on various forums but none seem to work. I've installed ndiswrapper and used it to install the 2802w driver (don't know if that's the right one). The ndiswrapper -l command returns "2802w : driver installed" but it doesn't see the hardware.

Can anyone tell me how I can get this wifi card to work?

Thanks

I've just run iwconfig and ifconfig and the results are as follows:

stewart@IBMT20:~$ iwconfig
lo          No wireless extensions

eth0        No wireless extensions

irda0       No wireless extensions

stewart@IBMT20:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:b3:05:86:45  
          inet addr:192.168.10.10  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::202:b3ff:fe05:8645/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1423 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2224713 (2.1 MB)  TX bytes:141594 (138.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20200 (19.7 KB)  TX bytes:20200 (19.7 KB)

Stewart

---

