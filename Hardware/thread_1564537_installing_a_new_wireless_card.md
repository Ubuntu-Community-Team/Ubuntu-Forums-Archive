---
title: "installing a new wireless card"
date: 2010-08-30
forum: Hardware
---

### Post by underworld288 on 2010-08-30
My old network card is dead so I needed to install a new one. I bought and installed the Linksys WMP54G card but ubuntu isn't auto detecting the change so I can't connected to the internet. It's weird because the new card doesn't show up on any output like *lspci* it still shows the old card.

_*lspci | grep Network* output_

```
03:06.0 Network controller: RaLink RT2561/RT61 802.11g PCI
```

_*lshw -C network* output_

```
 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:8e:69:01
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.42.43.10 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:de00(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdfe0000-fdfeffff(prefetchable) memory:fdf00000-fdf0ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:03:06.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: memory:fdef0000-fdef7fff
```

---

