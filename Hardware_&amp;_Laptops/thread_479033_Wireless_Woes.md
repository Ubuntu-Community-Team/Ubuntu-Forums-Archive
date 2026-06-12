---
title: "Wireless Woes"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by Jeff Mott on 2007-06-19
I just installed Ubuntu 7.04. Most everything seems to work fine, except my wireless. I've been referring to help.ubuntu.com. It said to go to System>Administration>Networking to see if my wireless card is listed. And it is. If I just let it roam, it doesn't find any wireless connections. I tried configuring the connection, entering the SSID, IP address and other information, and I checked the box to active the connection. The notification area will show that I'm then connected to that SSID, but there are no bars.

I ran "sudo lshw" and my wireless card showed up in the list.

What should I check next?

---

### Post by scrooge_74 on 2007-06-19
First Hi

second which version of Ubuntu are you using and which card.

Since the card is working (it seems), set it to roaming and try to connect using the network manager. On laters versions of  Ubuntu is on the panel by default, if it is not there open a terminal and click on nm-applet

If you can configure the router you could take out encryption and security so you can just conect and test things first. A few cards out there dont support WEP or WAP

---

### Post by Jeff Mott on 2007-06-20
I'm using Ubuntu 7.04. Is there another kind of version you need to know?

I've tried to let it roam, but it doesn't detect any networks. But those networks are definitely there.

The router is already not using any form of encryption.

---

### Post by scrooge_74 on 2007-06-20
Ok, let it in roaming 

just to be sure it is doing things kind of correct open a terminal and type iwlist eth1 (or what the system says is the wireless card) scanning

if the card is working you should see the details of your network

if it does then type nm-applet and click on the icon

---

### Post by Jeff Mott on 2007-06-23
It's saying my wireless is disabled now. ug!

Here's part of the results of sudo lshw```
           *-network:0 DISABLED
                description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@02:03.0
                logical name: eth0
                version: 02
                serial: 00:90:4b:ff:4b:03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:dfdfe000-dfdfffff irq:19
           *-network:1
                description: Ethernet interface
                product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@02:08.0
                logical name: eth1
                version: 03
                serial: 00:12:3f:0d:d0:b3
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
                resources: iomemory:dfdfd000-dfdfdfff ioport:df40-df7f irq:20
```...and the results of sudo lwlist scanning```
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning : No such device
```

---

### Post by scrooge_74 on 2007-06-23
check this thread

[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

---

