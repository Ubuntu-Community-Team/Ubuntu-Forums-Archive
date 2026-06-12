---
title: "No Wireless internet on Ubuntu 10.10"
date: 2011-02-19
forum: Hardware
---

### Post by salmankniazi on 2011-02-19
Hello, 

After spending hours on forums, I could not find a promising solution to wireless connection. I only have wireless Internet connection and can not seem to start learning power of Linux. I have put a temporary Ethernet connect. What is the problem? Missing hardware driver or hardware has been disabled by OS? 

Not an expert in Linux. Help will be appreciated. 
[B]
lshw -c net[/B] **OUTPUT**
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: f8:0f:41:01:8a:6c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=0.13-4 ip=192.168.2.20 latency=0 multicast=yes
       resources: irq:43 memory:fb200000-fb21ffff memory:fb228000-fb228fff ioport:f040(size=32)
  *-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 1c:65:9d:8e:27:25
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-25-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fb100000-fb10ffff

---

