---
title: "sata hard drive not recognized"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by Landoln on 2006-07-12
I have recently purchased a sil-3112 pci sata controller and a Seagate ST3320620AS SATA hard drive to put into an old pentium III box.  I see the cards bios after post and I can see that the card sees the hard drive and identifies it correctly.  Ubuntu recognizes the card, but I can't seem to get access to the hard drive when the system gets up and running.

Here's the lspci result: 
```

0000:00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 02)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 02)
0000:01:0a.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
**0000:01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 01)**
0000:02:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP
```

It currently has two PATA hard drives and a cdrom in it and working correctly.  The box is currently running Ubuntu 6.06 from the server install.  Any ideas?

---

### Post by Landoln on 2006-07-13
It appears that I just needed to add "irqpoll" to the boot options.  Now to find that thread I saw about the performance issues.

---

