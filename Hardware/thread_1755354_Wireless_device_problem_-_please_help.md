---
title: "Wireless device problem - please help"
date: 2011-05-11
forum: Hardware
---

### Post by TMacca on 2011-05-11
ever since I upgraded to ubuntu 11.04, I have had trouble trying to get my wireless working.

in ifconfig it shows:
```
eth0      Link encap:Ethernet  HWaddr 00:18:8b:ab:25:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 droped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9180 (9.1 KB)  TX bytes:9180 (9.1 KB)
```In iwconfig it shows:```

lo        no wireless extensions.

eth0      no wireless extensions.
```but in lspci it shows (among others):
```
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```how do I fix this to get it working?

thanks in advance

---

### Post by grahammechanical on 2011-05-11
You may need to re-install the Broadcom driver. If you go to the Networking and Wireless part of the forum you will see a sticky thread with this title:

Solution to Broadcom 43xx Card Problem (11.04, Natty Narwhal)

			 			Regards.

---

