---
title: "Internal Wi-FI Device Not Seen"
date: 2008-10-28
forum: Hardware
---

### Post by WarholsGhost on 2008-10-28
Hello
i have a compaq presario V4000 i just installed xubuntu and it seems like it is having problems seeing the internal wi-fi device. 

how can i troubleshoot?

---

### Post by nixscripter on 2008-10-28
Start off with running: ```
lshw -C network
``` in a terminal and see what devices show up.

---

### Post by WarholsGhost on 2008-10-28
it says the wi-fi device is disabled, how do i enable it?

---

### Post by nixscripter on 2008-10-29
It's probably a driver issue. Please post the output of that above command so I can look at it.

---

### Post by WarholsGhost on 2008-10-29
*-network:0 DISABLED    
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth0
       version: 05
       serial: 00:15:00:36:ee:38
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=128 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth1
       version: 10
       serial: 00:0a:e4:df:a4:e9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.108 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes

---

### Post by WarholsGhost on 2008-10-29
got it working, i had to install ndiswrapper

guess it didn't install with the system

---

### Post by bobromeo on 2008-10-31
> **WarholsGhost said:**
> got it working, i had to install ndiswrapper

guess it didn't install with the system

Your 'lshw' is exactly like mine !!
Only I have UNCLAIMED !

Did you have UNCLAIMED also. If Yes, what did you afterwards ?:confused:

---

### Post by nixscripter on 2008-11-01
Unclaimed usually means the driver is missing. I might be able to help you if you post your output from the same command. Also, please put it in [code] forum tags to make it easier to read.

---

