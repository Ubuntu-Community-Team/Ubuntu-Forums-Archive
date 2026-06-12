---
title: "help finding a busID please"
date: 2005-08-24
forum: Hardware &amp; Laptops
---

### Post by sal on 2005-08-24
im trying to find out the BusID's of my pci slots.
i know if i do a lspci i get the following:
=====================================
0000:00:00.0 Host bridge: Intel Corp. 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
0000:00:02.0 VGA compatible controller: Intel Corp. 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) LPC Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) UltraATA-100 IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:01:0b.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
0000:01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
==========================================

this one (0000:01:0b.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)) is listed in my xorg as 
BusID		"PCI:1:11:0"
and is on the lowest pci slot on my motherboard. i want to move it up a slot, and need to know what it would be listed as in the busid of xorg so when i change the slot i can reconfigure my xorg to the proper bus id.

thanks for the help in advance.

---

### Post by nad on 2005-08-24
The hex address of this device is presently 0000:01:0b.0 , converted to the decimal address format with bus type that xorg.conf requires is PCI:1:11:0 .

Moving it up one slot would logically make it 0000:01:0a.0 , or PCI:1:10:0 , however, this is no guarantee as the device addresses are enumerated by the bios at startup in an order determined by the engineers for your particular motherboard.

The surest way to determine the correct bus ID would be to move it, then start your computer to a command line (rescue mode?) and issue the lspci command again. At this point, you could edit xorg.conf and issue the command: init 2  to have your normal services load.

---

