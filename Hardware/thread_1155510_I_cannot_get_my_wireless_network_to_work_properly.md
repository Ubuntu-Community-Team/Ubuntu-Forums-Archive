---
title: "I cannot get my wireless network to work properly"
date: 2009-05-10
forum: Hardware
---

### Post by hiddenintel0710 on 2009-05-10
Hello all, im new to Ubuntu, and have just installed Ubuntu 9.04 on my older laptop. The install went fine, but I am unable to scan for wireless networks. Auto eth0 ( wired connection ) works just fine. When I select network in the system tray, I dont even have an option to search for any connections. Any assistance on the issue would definately be welcome. 



I have a broadcom wireless network card
Any one trying to help me will likely need more info from me, so just let me kno what u need.

Thnx in advance.

---

### Post by hiddenintel0710 on 2009-05-10
This information should help


roy@Betsy:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: eth0
       version: 01
       serial: 00:03:25:21:96:be
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.2 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:cb:e6:d9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: ae:c0:80:72:c7:3f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

