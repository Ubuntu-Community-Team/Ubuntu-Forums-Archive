---
title: "Realtek RTL8139/810x issue, cannot enable wireless functions"
date: 2008-06-16
forum: Hardware
---

### Post by WhiteSlash on 2008-06-16
Read title...
It does not seem to be working at all, I run the test but it marks the wireless network as disabled... any advice on packages I could install?

---

### Post by stchman on 2008-06-16
> **WhiteSlash said:**
> Read title...
It does not seem to be working at all, I run the test but it marks the wireless network as disabled... any advice on packages I could install?

The RTL8139 is a 10/100 PCI wired ethernet card.  It is supported OOB with Ubuntu.  It is popular on laptops.  I have one on my Toshiba laptop and it and the wireless card work well.

---

### Post by losty on 2009-09-23
Hello i hope someone can please advice, i having issues with the same wireless adapter. it is not detecting any networks, even if i put in details manually

i am using 9.04


```

roibeard@roibeard-laptop:~$ lsmod | grep 8139
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
roibeard@roibeard-laptop:~$ sudo lshw -C network
[sudo] password for roibeard: 
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1b:9e:39:39:6d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: eth0
       version: 10
       serial: 00:1a:92:aa:d8:a8
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7a:26:56:0a:e5:d5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
roibeard@roibeard-laptop:~$ lsmod | grep 8139
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
roibeard@roibeard-laptop:~$ sudo lshw |grep -A 15 network
           *-network      
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 01
                serial: 00:1b:9e:39:39:6d
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
--
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:05:07.0
                logical name: eth0
                version: 10
                serial: 00:1a:92:aa:d8:a8
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
        *-isa
--
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7a:26:56:0a:e5:d5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

any advice would be much appreacited! :D

---

