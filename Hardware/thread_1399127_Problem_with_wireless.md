---
title: "Problem with wireless"
date: 2010-02-05
forum: Hardware
---

### Post by hart027 on 2010-02-05
I have been having problems recently with my laptop (hp zt3000) being able to see wireless networks. Often upon starting up it will just connect to the nearest known network, but recently it has not been dong that and will often not even see the network when I know it's on and working just fine. I'm wondering if this is a problem with Ubuntu (9.10) or it's possibly a problem with the laptop itself... If it's a problem with Ubuntu anyone have any ideas as to how I can go about fixing it.
Thanks, Alex

---

### Post by b00mzi11a on 2011-04-08
I'm searching to figure out that exact problem on the same laptop model.  did you ever resolve it?

edit:  oops, sorry for raising the dead.. anyways, anyone have any ideas?  I've been running 10.10 for a couple weeks now without any troubles until I brought it to school and it couldn't find any wireless network.  It finds everything at home just fine and nobody else was having any issues at school.  ..I'm a networking idiot but I did at least make sure the wireless physical button was on and the 'enable wireless' was on.

here's what's shown when I terminal "sudo lshw -C network"

 *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 20
       serial: 00:02:3f:67:05:ff
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139cp driverversion=1.3 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:10 ioport:2000(size=256) memory:90300000-903000ff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 04
       serial: 00:04:23:84:41:bc
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.0.15 latency=128 link=yes maxlatency=34 mingnt=2 multicast=yes wireless=IEEE 802.11b
       resources: irq:5 memory:90000000-90000fff

---

