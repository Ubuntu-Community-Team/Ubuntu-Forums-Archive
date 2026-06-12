---
title: "Re: Toshiba Portege R835, getting suspend working on Ubuntu 10.10."
date: 2011-11-05
forum: Hardware
---

### Post by craig100 on 2011-11-05
I have a new Toshiba R380-138 on which I'm running ubuntu 10.10. Everything seems to work except Wifi. Doesn't even appear on the network choices. Is this an issue with the Sandy Bridge architecture or is there a fix? I really, really, really don't want to upgrade to 11.10, Gnome Shell or Unity UI's.


craig@craig-TOSH:~$ sudo lshw -C network
[sudo] password for craig:
*-network
description: Ethernet interface
product: 82579LM Gigabit Network Connection
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
logical name: eth0
version: 04
serial: e8:9d:87:a1:23:22
capacity: 1GB/s
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
resources: irq:45 memory:c4800000-c481ffff memory:c482a000-c482afff ioport:3060(size=32)
*-network UNCLAIMED
description: Network controller
product: Intel Corporation
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:04:00.0
version: 34
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resources: memory:c2600000-c2601fff
craig@craig-TOSH:~$

---

