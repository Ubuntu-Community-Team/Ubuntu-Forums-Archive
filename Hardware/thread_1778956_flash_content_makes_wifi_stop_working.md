---
title: "flash content makes wifi stop working"
date: 2011-06-09
forum: Hardware
---

### Post by uk80glue on 2011-06-09
Fresh install of 11.04 on a Lenovo L512 2598-42U. The wifi works fine for most pages however if I try to view flash based pages or anything that heavily uses it, stickam, youtube, ect my connection will just hang. It does not disconnect, but it never starts working again unless I restart my laptop. Flash content seems to be the only thing creating the issue but I have no idea how to fix it.

edit: It's doing it randomly now as well. Restarting is still the only fix I've found.

---

### Post by uk80glue on 2011-06-09
```
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: 1c:65:9d:cb:d7:e7
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 ip=192.168.0.111 latency=0 link=yes multicast=yes wireless=802.11bg
       resources: irq:17 ioport:2000(size=256) memory:f0600000-f0603fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 03
       serial: 60:eb:69:b0:0d:ff
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:3000(size=256) memory:f0a04000-f0a04fff memory:f0a00000-f0a03fff memory:f0a20000-f0a3ffff

```

---

### Post by uk80glue on 2011-06-09
In case someone comes across this thread while searching, [this seems to have fixed it]("https://answers.launchpad.net/ubuntu/+source/network-manager/+question/130154"), at least for now.

---

### Post by uk80glue on 2011-06-09
And oddly enough my connection screwed up for the first time in a few hours as soon as I posted that lol

---

### Post by uk80glue on 2011-06-10
bump

---

### Post by uk80glue on 2011-06-10
bump :|

---

