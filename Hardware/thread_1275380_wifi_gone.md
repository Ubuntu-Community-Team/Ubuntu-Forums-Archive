---
title: "wifi gone"
date: 2009-09-25
forum: Hardware
---

### Post by katoiam on 2009-09-25
I dont know what happened but I was trying to log into my wifi, but restarted then when i restarted there was no wifi! I did:
sudo lshw -C network
 it gave me:
*-network DISABLED      
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2b:85:95:0f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:5a:51:0a:f8
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.2.4 latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 56:b8:e6:56:3d:e9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
why  is my wifi disabled and how can I re-enable it?
thanx

---

### Post by swoody on 2009-09-25
Well, to start off, have you tried pressing the wireless button on your laptop to make sure it's on? Next, go into your BIOS, and if there's an option to disable/enable the wireless card, make sure it's set to 'Enabled'. Also, right-click on the network manager icon, and make sure "Enable Wireless" is checked.

---

