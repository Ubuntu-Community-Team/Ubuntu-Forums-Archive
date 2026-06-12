---
title: "Problems installing or running from CD"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by JamesDC on 2009-11-04
Hello all,
 

 I am a fairly novice Linux user, and I am investigating using it for a small embedded project.  I am trying to install the latest version of xbuntu on a small barebones system using a mini-itx Via VX800 with a Nano Processor and 1gb of ram.
 

 I have tried just about every distribution I can find (Ubuntu 9.04, Kubuntu net book, Xbuntu 9.10) and all seem to lockup somewhere in the boot-up process.  Depending on if I disable HPET in the bios, I get a bit further, and the furthest I have gotten was disabling the Cache, but things go painfully slow at that point.   
 

 Trying to run Xbuntu 9.10 off of the distribution cd I use the following options (this seemed to be the least offensive)
 

 file=/cdrom/pressed/xbuntu.seed boot=casper initrd=/casper/initrd.lz acpi=off noapic nolapic ide=nodma splash --
 

 and I get a ton of stuff that I cant find a good way to capture, but this is the last couple of lines:
 

 [2.505608] io scheduler deadline registered
 [2.505719] io scheduler cfg registered (default)
 [2.505802] pci 0000:00:02.0: disabling DAC on VIA PCI bridge
 and I am frozen
 

 if I try the standard  
 file=/cdrom/pressed/xbuntu.seed boot=casper initrd=/casper/initrd.lz splash --
 I get:
 [0.219783] NetLabel: unlabeled traffic allowed by default
 [0.219870] hpet0: at MMIO 0xfe800000, IRQs 2, 8, 0
 [0.220089] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
 and I am frozen
 

 I am currently trying to transition this system off of windows NT, so I can run some utilitys on the box to check for things.
 

 Thanks,
 -James

---

