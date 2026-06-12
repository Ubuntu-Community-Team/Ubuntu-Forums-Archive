---
title: "Restricted drivers in Gutsy not shown"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by SVWander on 2007-11-04
I figured out the problem. It was due to the early hour and time change LOL. I had reinstalled using the previous edition of Ubuntu which never supported the restricted drivers!  SORRY EVERYONE. Tim

I just reinstall 7.10 on my laptop. The reason I had to do so was extreme cpu usage . . . that problem is now corrected BUT now I Ubuntu cannot see that I need restricted drivers for my  BCM4306 802.11b/g Wireless LAN Controller    And by running:
 sudo lshw -C network
I find that it is disabled. How do I get Gutsy to SEE that it needs to install the restricted drivers for the BCM wireless card? Oh the print out for the command above is:
 *-network               
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 0
       resources: irq:16
  *-network
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:00:25:2a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.1.4 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:dfdff000-dfdfffff ioport:df40-df7f irq:20
  *-network DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@03:00.0
       logical name: eth1
       version: 03
       serial: 00:90:4b:d5:f1:f5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:44000000-44001fff irq:16

---

