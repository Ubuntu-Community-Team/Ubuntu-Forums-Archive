---
title: "Installing driver: dc.4freebsd.gz"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by ghed on 2009-06-29
I am new to xubuntu and need to install a driver for Ethernet Adapter Accton EN2242. Found the **dc.4freebsd.gz** on [http://manpages.ubuntu.com/manpages/intrepid/man4/dc.4freebsd.html](http://manpages.ubuntu.com/manpages/intrepid/man4/dc.4freebsd.html) which I hope will solve my problem. How do I install the driver. Is there a simple way.

---

### Post by atomizer on 2009-06-29
Before you grab a driver from the net: this is not windows, most of the time you can use software maintained by Canonical to solve your problem.

what is the output when you type in your terminal 

```
lshw -C network
```

(this means LiSt of HardWare -Class network)

then you can see what chipset your network has, probebly there is a post on this forum which guides you to install the right drivers for your network card.

---

### Post by ghed on 2009-06-29
the answer is
 
product: EN-1216 Eternet Adapter
vendor: Accton Technology Corporation
physical id : 10
bus info: [EMAIL="pci@0000:00.10.0"]pci@0000:00.10.0[/EMAIL]
logical name: eth0
version: 11
serial: 00:d0:59:54:20:48
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=64 maxlatency=255 mingnt=255 module=tulip multicast=yes
*-network DISABLED
description: Ethernet interface
phsical id: 1
logical name: pan0
serial:e6:0b:2c:5e:54:5a
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversio=2.3 firmware=N/A
multicast=yes

---

### Post by ghed on 2009-06-30
There is a driver istalled and the internet connections works. The problem was a faulty connection. Thanks for the help

---

