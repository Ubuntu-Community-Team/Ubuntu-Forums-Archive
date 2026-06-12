---
title: "Problems Obtaining Broadcom STL in 8.10"
date: 2008-10-31
forum: General Help
---

### Post by Newtothegame on 2008-10-31
Hello everyone, 

Still a major linux noob here, so baby steps would be awesome. 

Here is my problem: I have been able to get my wireless card working however when I attempt to connect it asks for a CA certificate. After doing a bit of digging I found out there is a Broadcom driver that should be showing up in System>administration>Hardware drivers. While my Nvidia drivers are there, the Broadcom is not.(not sure if the problems are related, but I would prefer the Broadcom drivers) Could this be due to the drivers I have implemented for my wireless at the moment? Here is the info I have. 

  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:0e:ec:e9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:25:2f:80
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=130.253.57.234 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:30:c6:6d:61:3e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


-Newtothegame

---

### Post by Newtothegame on 2008-11-02
Bump :)

---

