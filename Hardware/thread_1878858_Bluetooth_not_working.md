---
title: "Bluetooth not working"
date: 2011-11-10
forum: Hardware
---

### Post by FiveDiamonds on 2011-11-10
So my built in bluetooth adapter is not working in ubuntu 11.10.  The indicator icon says bluetooth is enabled, but under bluetooth preferences it says it's not.  Also hcitool says that there are no bluetooth devices.  bluetooth card is a broadcom something (don't know specifically because lspci doesn't show it)

please help

---

### Post by GugaBFigueiredo on 2011-12-03
Same problem here
Except mine is a USB Dongle Bluetooth adapter

---

### Post by bluexrider on 2011-12-03
would suspect NO or IMPROPER driver set

check your hardware configuration 

sudo lshw -c network

if under capabilities: the driver doesn't exisit or doesn't match. Reinstall driver set

---

### Post by FiveDiamonds on 2011-12-04
It doesn't show up there either.  Output to follow.

*************************************************************************

five@FiveDiamonds:~$ sudo lshw -c network
[sudo] password for five: 
PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f8000000-f8003fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: f0:4d:a2:44:39:d7
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 firmware=sb v2.17 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:fc500000-fc50ffff
  *-network
       description: Wireless interface
       physical id: 4
       logical name: wlan0
       serial: 78:e4:00:fa:46:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-13-generic firmware=478.104 ip=192.168.2.8 link=yes multicast=yes wireless=IEEE 802.11bg
five@FiveDiamonds:~$ 
five@FiveDiamonds:~$ sudo lshw -c network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f8000000-f8003fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: f0:4d:a2:44:39:d7
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 firmware=sb v2.17 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:fc500000-fc50ffff
  *-network
       description: Wireless interface
       physical id: 4
       logical name: wlan0
       serial: 78:e4:00:fa:46:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-13-generic firmware=478.104 ip=192.168.2.8 link=yes multicast=yes wireless=IEEE 802.11bg

*************************************************************************

---

