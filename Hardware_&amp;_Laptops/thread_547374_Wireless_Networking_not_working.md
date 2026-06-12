---
title: "Wireless Networking not working"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by maniac779 on 2007-09-09
I have just installed Ubuntu 7.04 on a Asus Aspire 5002WLCi Laptop. The installation has gone fine and I am able to connect to the internet via a wired connection without problems. However, I have been unable to find a list of available wireless connections and when I select "connect to other wireless network" and enter in the appropriate information, I am greeted by a wireless signal strength indication of 0% and a shield type icon with a red dot in the middle beside the name of the network.

I have run iwconfig and ifconfig and have the following results. Can anyone help??

From iwconfig:

eth1  IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

From ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:B8:18:32  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:feb8:1832/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3937 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2719209 (2.5 MiB)  TX bytes:308438 (301.2 KiB)
          Interrupt:16 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7468 (7.2 KiB)  TX bytes:7468 (7.2 KiB)


Thanks alot!

---

