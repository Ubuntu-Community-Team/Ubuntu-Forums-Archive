---
title: "Help - Netbook Haier Olive X107B - RT2571 Ralink doesn't work"
date: 2010-04-16
forum: Hardware
---

### Post by Irwan on 2010-04-16
Please help me, I have netbook Haier Olive X107B, but wireless wifi not working. Does anyone can help me how to make it works.

Here is additional information

lsusb
Bus 001 Device 005: ID 148f:2070 Ralink Technology, Corp.

lshw -C network
*-network
description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:01:00.0
logical name: eth0
version: 02
serial: 00:eb:01:00:fb:bc
size: 10MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
resources: irq:25 ioport:ec00(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdfe0000-fdfeffff(prefetchable) memory:febe0000-febfffff(prefetchable)
*-network
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:1e:e3:de:1f:79
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

---

