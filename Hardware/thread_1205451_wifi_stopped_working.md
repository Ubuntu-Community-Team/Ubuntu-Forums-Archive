---
title: "wifi stopped working"
date: 2009-07-06
forum: Hardware
---

### Post by wc77 on 2009-07-06
Hi there, I'm rather new to Linux Ubuntu, and new to this forum, so please help!!
I have a Compaq Presario CQ60 with Ubuntu 9.04 loaded, and for some reason the wifi just stopped working one day.
I've checked that the drivers are installed (Madwifi), etc.
I think it is de-activated, but I dont know how to put it back on through the terminal, as the button next to the ON/OFF switch doesn't work.

I'd like to ask for simple steps to follow pls, as I'm rather non-technical :-?

Thanks

---

### Post by wc77 on 2009-07-06
This is what I got, should it be of any help,

[COLOR=Blue]*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:46:55:c1
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: eth1
       serial: 00:30:0a:79:cb:7d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=10.0.0.10 link=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3a:8d:ae:f9:ef:59
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes[/COLOR]

---

