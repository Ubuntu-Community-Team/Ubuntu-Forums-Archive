---
title: "Problem with HP dc5750 and it's Broadcom 5755 and ATI Radeon XPress 1150 chipset"
date: 2008-04-15
forum: Hardware &amp; Laptops
---

### Post by Mark@MF on 2008-04-15
I am attempting to install Ubuntu 6.06 on my HP dc5750 at work.  As the supposed EOL of XP approaches, we are considering going to Ubuntu for certain machines as opposed to Vista (and thus being forced to buy new computers).

The specs of my dc5750 are:
AMD 64 X2 Dual Core Processor 4200+ 2.19GHz
896MB of RAM (512+256+128?????  seems wierd to me)
ATI Radeon XPress 1150 chipset
Broadcom 5755 Gigabit Ethernet

My supervisor uses a similar HP xw4300 PC and his works perfectly.  The main difference between his xw4300 and my dc5750 is that his has an Intel chipset and mine has an ATI chipset.  It even uses a similar Gigabit Ethernet adapter

The problem is that the network won't work, and the audio won't work.  We have never really cared about audio here at my workplace (obviously) but clearly the network is a critical feature.  Everything else works fine.

So I ran "sudo lshw -C network" and got this listing:

```
  *-network UNCLAIMED
       description: Ethernet controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@3f:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:d8400000-d840ffff irq:5
```

I repeated the same on my supervisor's machine and I got:

```
  *-network UNCLAIMED
       description: Ethernet controller
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@3f:00.0
       version: 01
       serial: 00:17:a4:17:56:47
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bs_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=tg3 driverversion=3.59.1 duplex=full firmware=5752-v3.10 ip=10.0.0.117 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:e8400000-e840ffff irq:82
```

I found from the Broadcom website that the network interface used the tg3 driver, as confirmed by the above information on the working machine.  So I downloaded the source code for the driver from Broadcom, but couldn't get it to build.  That's when I discovered that tg3.ko was indeed located in /lib/modules/2.6.15-26-386/kernel/drivers/net already.  Next I decided to try a more windows-like approach and look in the device manager to see if there was a way to force Ubuntu to recognize the driver.  I didn't notice such a function, but I did notice this that in the device list every device listed as 82801G is listed as "Unknown" on my computer(sorry, I have a screenshot, but don't have an account on a photosharing site and don't wish to open one).

This leads me to believe I should also look at drivers for the ATI Radeon XPress 1150 chipset.  Does anyone have thoughts on this mess?

---

### Post by cybil on 2008-04-15
I use the fglrx driver for the embedded dual head graphics card, on the dc5750, so that I can extend my desktop to two displays, and everything works well.

---

### Post by Mark@MF on 2008-04-17
I installed fglrx both the driver package and the kernel source package but still I have no network and everything in Device Manager is listed as "unknown device".

Also, I noticed when installing packages that it thinks my architecture is i386 when I know for certain that my processor is a dual core 64 bit AMD Athlon.  Was this some mistake made during installation?

---

