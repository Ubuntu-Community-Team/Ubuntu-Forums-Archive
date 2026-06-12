---
title: "Ubuntu driver for Token-Ring 16/4 PCI Adapter"
date: 2010-11-09
forum: Hardware
---

### Post by omidrayan68 on 2010-11-09
I have two network cards one is usable and the other no!! any help|!:

Here is "  lshw -c network  " the second one is UNCLAIMED.


  > *-network               
       description: Ethernet interface
       product: 82566DM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:21:86:12:51:1a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=1.3-1 ip=182.50.190.138 latency=0 multicast=yes
       resources: irq:40 memory:d0180000-d019ffff memory:d01a5000-d01a5fff ioport:1820(size=32)
  *-network UNCLAIMED
       description: Token ring network controller
       product: Token-Ring 16/4 PCI Adapter (3136/3137)
       vendor: Olicom
       physical id: a
       bus info: pci@0000:11:0a.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=228 maxlatency=64 mingnt=28
       resources: ioport:2000(size=64)

> sudo ifconfig eth1 up
Ignoring unknown interface eth1=eth1.

---

### Post by Fafler on 2010-11-09
Back in the day, i got a complete TokenRing network with MAU and PCI cards. The Olicom cards did not work under Linux and i don't think anyone has written a driven since then, because TokenRing is long since dead. Anyway, i found a IBM card that worked lout of the box.

find /lib/modules | grep token

for a list of TokenRing drivers.

---

### Post by omidrayan68 on 2010-11-09
> **Fafler said:**
> Back in the day, i got a complete TokenRing network with MAU and PCI cards. The Olicom cards did not work under Linux and i don't think anyone has written a driven since then, 

find /lib/modules | grep token

for a list of TokenRing drivers.

Thanks, this is the output of the command
> 
find /lib/modules | grep token
/lib/modules/2.6.35-22-generic/kernel/drivers/net/tokenring
/lib/modules/2.6.35-22-generic/kernel/drivers/net/tokenring/tms380tr.ko
/lib/modules/2.6.35-22-generic/kernel/drivers/net/tokenring/skisa.ko
/lib/modules/2.6.35-22-generic/kernel/drivers/net/tokenring/smctr.ko
/lib/modules/2.6.35-22-generic/kernel/drivers/net/tokenring/olympic.ko
/lib/modules/2.6.35-22-generic/kernel/drivers/net/tokenring/3c359.ko
/lib/modules/2.6.35-22-generic/kernel/drivers/net/tokenring/ibmtr.ko
/lib/modules/2.6.35-22-generic/kernel/drivers/net/tokenring/lanstreamer.ko
/lib/modules/2.6.35-22-generic/kernel/drivers/net/tokenring/tmspci.ko
/lib/modules/2.6.35-22-generic/kernel/drivers/net/tokenring/abyss.ko
/lib/modules/2.6.35-22-generic/kernel/drivers/net/tokenring/proteon.ko
/lib/modules/2.6.35-22-generic/kernel/drivers/net/tokenring/madgemc.ko




Is there any link for a compatible driver?

---

