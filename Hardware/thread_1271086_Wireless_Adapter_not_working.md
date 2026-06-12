---
title: "Wireless Adapter not working"
date: 2009-09-20
forum: Hardware
---

### Post by wildinco on 2009-09-20
I am new to Ubuntu. I just installed ubuntu on my dell inspiron 1501 and the wireless is not working i tried tons of things to get it to work and nothing seems to work. I have installed ndiswrapped and downloaded my drivers and it gice me the error unable to see if hardware is present but it says its present. My laptop has a wifi light and it is not on i tried the shortcut fn F2 and it does nothing. below is my network info. 

  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:ab:48:20
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.6 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1e:68:05:69:6d:9e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:1d:d9:3e:84:36
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by WatTwo on 2009-09-20
Hey, I am also new to Ubuntu, but i had a similar problem.

What i did was went to:

System > Administration > Hardware Drivers

And on that page, was my wireless card, i had to click on "activate"

Reboot, and wireless worked.

Hope this helps!

---

