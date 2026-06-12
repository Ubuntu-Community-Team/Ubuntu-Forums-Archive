---
title: "Wireless Card Trouble, please help"
date: 2009-08-09
forum: Hardware
---

### Post by sideverteuil on 2009-08-09
Hello,
I have recently built my own desktop and I am having some trouble with connecting to the internet with my wireless network card. 

I have a  		[EDIMAX EW-7728In 32bit PCI Wireless 802.11n Draft 2.0 PCI Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833315078"), and I am running Ubuntu 8.10 on a 32 bit system.

So far, I have hooked my system up directly to my router, and I have updated and installed Windows Wireless Drivers program. I have located the .inf driver that the card uses and installed it. Unfortunately this does nothing to help my situation. Typing 

sudo lshw -C network 

in terminal, I get this message...

 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:d0:d7:ea:98
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.70 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=4 mingnt=2
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a6:68:48:5a:19:fc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

saying my network card is unclaimed and disabled still. The network card seems to be turned on as well. The lights for the card are on, but none of them are flashing like they should be.

Does anyone have any suggestions?

---

### Post by sideverteuil on 2009-08-10
If anyone needs additional information I would be happy to supply it. I am still new when it comes to using linux, so I am still learning the ropes. If anything I am using a RT2800 802.11n PCI card when it comes to using linux. I have done some additional research and apparently I have the linux driver on my driver cd. I just don't know which one to use, more or less how to install them.

---

