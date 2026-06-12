---
title: "HP Compaq 6730b Wireless &amp; LAN doesn't work"
date: 2010-06-30
forum: Hardware
---

### Post by kimibp on 2010-06-30
Power button for wireless is enabled, for lan cable on picture is not plugged, but if cable is plugged he trying to connect and say you are offline...

ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:d8700000-d8703fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:85:00.0
       logical name: eth0
       version: 02
       serial: 18:a9:05:97:f8:9d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=sb v2.13 latency=0 multicast=yes
       resources: irq:30 memory:d0600000-d060ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:26:82:3b:17:46
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

[IMG]http://a.yfrog.com/img251/2156/screenshotbx.jpg[/IMG]
[IMG]http://img31.imageshack.us/img31/7778/screenshot1pf.jpg[/IMG]

---

