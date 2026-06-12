---
title: "wireless problem with atheros ar242x"
date: 2010-10-19
forum: Hardware
---

### Post by evgen_m on 2010-10-19
i have dell vostro a840 and one day i had some problems, so i reinstalled OS ubuntu 8.04 and after that i have internet with wire but i cannot use wireless, because is problems with drivers. i did read some topics here about this problem and tried to fix, but for now is not seccesful
for example what is right way for install madwifi?


e@e-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:26:b9:00:57:7c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.8 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
e@e-laptop:~$

---

