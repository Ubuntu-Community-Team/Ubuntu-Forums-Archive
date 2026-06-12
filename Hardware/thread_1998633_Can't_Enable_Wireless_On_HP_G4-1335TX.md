---
title: "Can't Enable Wireless On HP G4-1335TX"
date: 2012-06-07
forum: Hardware
---

### Post by ysNoi on 2012-06-07
Hi...

I'm running on Precise 12.04 but I don't know to enable my Wireless.

I have an HP G4-1335TX laptop.

Here is my output for lshw -C network

  ```
*-network DISABLED      
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 7c:e9:d3:46:e8:70
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:c2500000-c2503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 80:c1:6e:3c:e1:af
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.179 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff

```

How do I enable my wireless to work?

Any help is highly appreciated in advanced...

TYIA...

---

### Post by ysNoi on 2012-06-08
Okey...

Just this morning after my software update...

```
*-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 7c:e9:d3:46:e8:70
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.0.2 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:c2500000-c2503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 80:c1:6e:3c:e1:af
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.179 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
```

And it works now...

Topic closed... :guitar:

---

