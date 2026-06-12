---
title: "Acer AspieOne WIFI issues (9.10)"
date: 2009-12-29
forum: Hardware
---

### Post by Monomer on 2009-12-29
Just switched from 9.04 to 9.10. Wifi worked for a bit, then completely stopped working.

I'm using wicd as a manager



ifconfig output:

[B]

eth0      Link encap:Ethernet  HWaddr 00:23:8b:3a:7d:10  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe3a:7d10/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:23848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21504 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22797161 (22.7 MB)  TX bytes:2825468 (2.8 MB)
          Interrupt:28 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)[/B]


Wireless does not show up at all. It does however, showup in network tools as wlan0, what gives?


(My apologies if this has been solved - I've been googling for hours, everone seems to have their own fix (none of which has seemed to work yet)

---

### Post by Monomer on 2009-12-29
Card info:

lspci | grep Network
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

---

### Post by Monomer on 2009-12-29
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"belkin54g"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


It shows up in iwconfig, odd. I'm still a rather new user here, be gentle :)

---

### Post by Monomer on 2009-12-29
kevin@ubuntu:~$ sudo ifconfig wlan0 up
[sudo] password for kevin: 
SIOCSIFFLAGS: Unknown error 132


posting any data I can here, sorry for the multiple posts.

---

### Post by margazhang on 2009-12-29
Hmmm... never had this problem. I usually had the problem the other way around - I clean installed or upgraded Ubuntu and then found the Gnome Network Manger (NM) not working for wireless connections. To solve the problem, I simply used Synaptic to install wicd to replace NM and then everything works fine.

Maybe you could install NM to replace wicd using Synaptic and see if it works for you. 

If that still does not work for you, you can try installing wicd again.

Make sure you have a wired internet connection when you do the above.

I suspect that your upgrade (not clean install) changed something that made wicd not work properly. Reinstall it should fix the problem.

---

### Post by Monomer on 2009-12-29
> **margazhang said:**
> Hmmm... never had this problem. I usually had the problem the other way around - I clean installed or upgraded Ubuntu and then found the Gnome Network Manger (NM) not working for wireless connections. To solve the problem, I simply used Synaptic to install wicd to replace NM and then everything works fine.
[B]
Maybe you could install NM to replace wicd using Synaptic and see if it works for you. [/B]

If that still does not work for you, you can try installing wicd again.

Make sure you have a wired internet connection when you do the above.

I suspect that your upgrade (not clean install) changed something that made wicd not work properly. Reinstall it should fix the problem.

That did it. 


Touchy, but stable.....

---

