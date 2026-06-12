---
title: "Wireless doesnt work, worked fine on 9.04"
date: 2009-11-16
forum: Hardware
---

### Post by nikolaig on 2009-11-16
wired INTERNET works fine, but wireless isn't seeing any networks, even though i know there are 10 here.

help

please

---

### Post by ajgreeny on 2009-11-16
What hardware?  It's impossible to answer without any more info from you.

---

### Post by nikolaig on 2009-11-16
> **ajgreeny said:**
> What hardware?  It's impossible to answer without any more info from you.

can you tell me what to put into the terminal so that it gives that info ?

---

### Post by ajgreeny on 2009-11-16
Try ```
sudo lshw -C network
```

---

### Post by nikolaig on 2009-11-16
> **ajgreeny said:**
> Try ```
sudo lshw -C network
```

 *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:f2:9f:bb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=188.74.86.59 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:18 memory:dfdfe000-dfdfffff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:64:d8:22
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: irq:17 memory:dfdfd000-dfdfdfff

---

### Post by bostonian95 on 2009-11-16
Hi, i am having the same problem. I am using a Dell inspiron 6000 with a BCM4318 wireless lan controller. (It says air force one 54g next to it?) and i know i have multiple  connections. A little bit of background, this laptop was working fine with XP, and then i reinstalled XP trying to get a fresh start, that is when the wireless stopped working. I then changed it over to ubuntu and it still does not work. I am desperate all help is greatly appreciated. If you guys care, my output was,
*-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:eb:a1:fd
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.113 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:18 memory:dfdfc000-dfdfdfff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfdfe000-dfdfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:39:63:07
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
Sorry for piggybacking on your post

---

### Post by bostonian95 on 2009-11-16
Thats intersting, now that i notice it, we are both using Broadcam wireless cards.

---

### Post by nikolaig on 2009-11-16
> **bostonian95 said:**
> Thats intersting, now that i notice it, we are both using Broadcam wireless cards.


Im on a dell inspiron 6000 as well, although , my situation is slightly different, wireless was working fine on ubuntu 9.04, but on 9.10 it doesnt work.

---

### Post by bostonian95 on 2009-11-16
yeah, i never tried 9.04 but i am assuming it wont work regardless of my OS.

---

### Post by nikolaig on 2009-11-16
> **bostonian95 said:**
> yeah, i never tried 9.04 but i am assuming it wont work regardless of my OS.

looking at your data read-out , it says wireless-DISABLED.

try right clicking on the little icon on the very top right of your screen and see if you have the option of "enable wireless" 

it should be the box to the left of the speaker/sound button

---

### Post by bostonian95 on 2009-11-16
Thanks, i tried it and enable wireless is checked, but no go. Im such a noob. I am still getting Disabled in my prompt.  any suggestions?

---

### Post by bostonian95 on 2009-11-16
i think sice i dont want to piggyback off of your post i will start a new one. thanks for helping!

---

### Post by nikolaig on 2009-11-17
*bump* still no solution guys...

---

### Post by moore.bryan on 2009-11-17
There are plenty of threads out there about the wireless issues in Karmic; AFAIK, there's no solution. There are a **ton** of Launchpad bugs, too...

---

### Post by nikolaig on 2009-11-17
> **moore.bryan said:**
> There are plenty of threads out there about the wireless issues in Karmic; AFAIK, there's no solution. There are a **ton** of Launchpad bugs, too...

ahh ok thanks :)

---

### Post by moore.bryan on 2009-11-18
Sure... let's hope this is fixed ASAP; I'm suffering from intermittent connections.

---

