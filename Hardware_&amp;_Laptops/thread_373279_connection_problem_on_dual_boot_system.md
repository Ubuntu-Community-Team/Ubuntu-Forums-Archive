---
title: "connection problem on dual boot system"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by Buster95 on 2007-03-01
Loaded 6.10 from a downloaded boot disk, onto this laptop with XP on another partition. XP connects OK but not Ubuntu. Not sure where to start looking. Searched the threads but nothing seemed close to what I'm experiencing. 
Following suggestions on another thread, I interrogated for an IP address [sudo dhclient eth0] and got the message "No DHCPOFFERS received" Presumably that simply confirmed the bleeding obvious. Tried changing to a fixed IP - no result. This laptop came with a Via Ethernet adaptor card.
Would appreciate a starting tip.
Cheers

Curious - rebooted to Ubuntu, changed the IP address back to "automatically assigned by DHCP". Still no success, but when I rebooted in XP, the wireless icon activated. So now, I can connect by wireless router (it's a Realtek RTL 8187) on XP but still nothing on Ubuntu (neither the direct ethernet connection or the wireless).

More information:
Copied networking parameters from Windows to Edgy (Ethernet disconnected; Wireless DNS settings). Still no connection.
The wireless router is a Realtek RTL 8187
ifconfig returns the following:
laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:F5:57:BA:BB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:50 Base address:0x4800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7220 (7.0 KiB)  TX bytes:7220 (7.0 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:15:AF:12:7D:B7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:7 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1504 (1.4 KiB)  TX bytes:0 (0.0 b)

---

