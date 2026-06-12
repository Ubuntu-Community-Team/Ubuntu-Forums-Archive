---
title: "DMA: Out of SW-IOMMU space"
date: 2009-07-14
forum: Hardware
---

### Post by mumutz on 2009-07-14
I have an Intel based system (Intel Xeon Dual Core E3110 proc, intel motherboard). The server has two network cards: onboard Intel network card plus an extra network card (Dlink DGE-528T). 

Via the Dlink network card a NAS storage is accessed (mounted as nfs). 

When I try to create a 50G file on the NAS I start getting the following message

"DMA: Out of SW-IOMMU space for 7022 bytes at device 0000:03:01.0" every second or so.


I have the following configuration: 
Kernel 2.6.24-24-server

lspci has the following output:

00:00.0 Host bridge: Intel Corporation 3200/3210 Chipset DRAM Controller
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
02:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G200e [Pilot] ServerEngines (SEP1) (rev 02)
03:01.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)
03:02.0 Ethernet controller: Intel Corporation 82541GI Gigabit Ethernet Controller (rev 05)


This gives me an idea that it might be something wrong with the driver for DGE-528T (it uses in fact the r8169 being based on the RTL8169 chipset).

Is this a bug or should I do additional configuration on the system?

If you need more info please let me know.

---

### Post by mumutz on 2009-07-20
Just found out that this actually a bug as described in 

[http://bugzilla.kernel.org/show_bug.cgi?id=9468](http://bugzilla.kernel.org/show_bug.cgi?id=9468)

---

