---
title: "Ubuntu Wireless... Ugh (HP G56-128CA)"
date: 2011-05-08
forum: Hardware
---

### Post by el canadiano on 2011-05-08
Hey guys,

I was wondering if there was a more reliable driver for my computer which I struggle to find. I experience very frequent disconnections and it's so annoying I have to use ethernet where possible. This is also not a problem in my Windows partition (but to be fair, the laptop is very unreliable).

This is the result for doing sudo lshw -class network.
```
  *-network               
       description: Wireless interface
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 1c:65:9d:64:b4:b0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 ip=192.168.0.196 latency=0 link=yes multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:d3500000-d3503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 64:31:50:56:48:6d
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff

```

---

