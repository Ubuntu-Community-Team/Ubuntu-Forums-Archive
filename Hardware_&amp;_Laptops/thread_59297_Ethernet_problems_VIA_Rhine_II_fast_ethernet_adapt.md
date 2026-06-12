---
title: "Ethernet problems VIA Rhine II fast ethernet adaptar"
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by dsbeav on 2005-08-23
Hey!  I'm a linux newbie and I've been enjoying learning the OS and the additional challenges of using a AMD64 laptop.  (Gateway series 74xx)

Anyway, I've been having problems with my ethernet card.  I have a VIA RHINE II fast ethernet adapatar.  When I boot into windows I can access the interent through my Ethernet card.  When I boot linux nothing...  When i click on the network box in the system tray in Ubuntu I get the following error:

Please contact your system administrator to resolve the following problem:
SIOCGIFFAGS error: no such device

When I do an ifconfig I only get lo (loopback? I'm not sure really what this is)
and wlan0 (my broadcom wireless card that I have configured with ndiswrapper)

I'm pretty sure from the information gathered that Ubuntu is not finding my ethernet card.  Is there anything I need to do to configure it?  Are there any vital packages that I might need to install?

Any ideas?

Thanks!

---

### Post by nad on 2005-08-23
Search your boot messages for a reference to your ethernet devices: dmesg | grep eth 

Also, look at the output of: lspci  to see what devices are reported in your system and: lsmod  to see what modules are loaded in your running system.

You are looking for the via-rhine module here. This is a standard module. If you get a message about an unknown hardware ID, you may wish to report this to the author of the driver that he may add support in future versions.

---

### Post by dsbeav on 2005-08-23
Horray, I got it working :)

I'm not sure which thing I did, but I checked all the messages you said to check.  
In ifconfig eth0 was not showing up, but then I did a ifconfig eth0 and it found it.  

Now it works!

Thanks again!

---

### Post by senectus on 2006-02-22
I have the same issue but this time it's in Dapper...
If I do an ifconfig -a I have this show up:
```
eth0_clas Link encap:Ethernet  HWaddr 00:13:D4:C4:51:B4  

          BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

          Interrupt:217 Base address:0xd800 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:4818 errors:0 dropped:0 overruns:0 frame:0

          TX packets:4818 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:478160 (466.9 KiB)  TX bytes:478160 (466.9 KiB)



sit0      Link encap:IPv6-in-IPv4  

          NOARP  MTU:1480  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

Anyone got any idea's?

---

