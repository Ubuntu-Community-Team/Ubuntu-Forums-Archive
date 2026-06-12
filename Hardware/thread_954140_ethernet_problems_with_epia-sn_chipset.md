---
title: "ethernet problems with epia-sn chipset"
date: 2008-10-20
forum: Hardware
---

### Post by esj on 2008-10-20
using a epia-sn mini-itx system and am having problems with ethernet.  whenever I try to transfer a few hundred GB of data via rsync, the ethernet driver drops off the network.  it seems that something looses it's mind and starts generating 10k+ interrupts per second.  the only way to recover is to reset the box.   it does not matter which ethernet controller I use, they both fail.

VIA VT6103L 10/100Mbps Ethernet PHY
VIA VT6130 PCI-E Gigabit Ethernet Controller 

using 8.04 server

any suggestions?  any way I can use a pio mode?

---

