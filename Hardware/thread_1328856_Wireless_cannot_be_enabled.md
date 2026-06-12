---
title: "Wireless cannot be enabled"
date: 2009-11-16
forum: Hardware
---

### Post by bostonian95 on 2009-11-16
hi i am having a problem with my wireless. Although i know that i have multiple wireless connections available, my pc still says wireless networks are disconnected. this is what i get when i run ```
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


Notice that *-network says Disabled, i cannot seem to change this. i have a dell inspiron 6000. any and all help is greatly appreciated.

---

### Post by bostonian95 on 2009-11-17
bump

---

