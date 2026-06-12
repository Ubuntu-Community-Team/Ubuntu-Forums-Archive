---
title: "ADSL+2 settings"
date: 2011-03-09
forum: Hardware
---

### Post by dargenov on 2011-03-09
Hi 
First:
```
Ubuntu 10.10 x64 
ADSL modem:
Buffalo AirStation WBMR-HP-GN ADSL2+ Wireless-N Router High Power
I use and still do the LAN cable to connect t he modem
```

I had the TD-8811 TP-link ADSL modem and I use (still use) Bridge mode and a ADSL connection via network manager to connect to INTERNET
OK!
when I had Tp link it was just an adsl 2+ modem but this new one is adsl and wireless router as well
for tp link I had to connect to wired connection (which is by default shown in network manager wired connections tab after fresh install ) to be able to go  to 192.168.1.1 (modem IP ) to set the settings and it worked fine.
but now with this modem I was able to go to 192.168.11.1 (IP for the new modem it is the factory manual) by creating a blank new wired connection and go to setup page for new one.

and the stange thing is that the privous wired connection (Auto eth0 ) which has the mac address setting in it does not show in the list of connection any more)

and if I put the mac address in the new connection this one will disappear too.
now look at my ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 00:25:64:4d:b2:be  
          inet6 addr: fe80::225:64ff:fe4d:b2be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1761 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1624 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1452127 (1.4 MB)  TX bytes:290293 (290.2 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:26:5e:45:93:23  
          inet6 addr: fe80::226:5eff:fe45:9323/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:642
          TX packets:24 errors:13 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2712 (2.7 KB)  TX bytes:3432 (3.4 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2880 (2.8 KB)  TX bytes:2880 (2.8 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:94.183.174.38  P-t-P:94.183.160.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1670 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1523 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1409738 (1.4 MB)  TX bytes:250763 (250.7 KB)
```


you see the first which is eth0 and its mac address if i put that in wired connection setting is shows in the list but not able to connect if I put the second mac address which is eth1 it does not show in the list

if my adsl connection is active it is not possible to connect to 192.168.11.1 and i could not have the eth connection so what should I do to conecct to 192.168.11.1 and change my setting?

help needed badly
PLZ:popcorn:

---

