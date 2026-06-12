---
title: "how to enable or install SATA AHCI driver in Ubuntu 10.04"
date: 2012-01-04
forum: Hardware
---

### Post by james2b on 2012-01-04
I need to find out how to enable or install the SATA AHCI driver in Ubuntu 10.04 when I have the BIOS serial ATA setting to the IDE compatibility mode ? This is a multi-boot system from 2009 with a few versions of Windows installed, (all were installed when in the IDE emulation compatibility mode, and now changing it to AHCI mode in the BIOS). It has a ASUS P5QL motherboard with the Intel P43 express IHC10 chip set.

---

### Post by james2b on 2012-01-05
Can I just search for the correct sata driver in the synaptic package manager and have it install, so that either the kernel or initial ram disk boot files can load that needed SATA hard drive AHCI device driver. ? Or is this a catch 22 issue like in the XP ?

---

### Post by Basher101 on 2012-01-05
just installing the driver won't resolve your issue.. the driver wont do any good installed when not enabled, did you try installing ubuntu with the AHCI mode enabled? you would then have the very unfortunate position of being forced to switch modes whenever you want to switch from windows to ubuntu..


regards

---

### Post by james2b on 2012-01-07
This issue is now all fixed which ended up really only a problem in the Windows XP, since after I changed the SATA mode in the BIOS from the IDE to the AHCI, which was after I completed the steps in my XP to have the sata driver, then when I booted the Ubuntu 10.04 it loaded up just fine with no issues, so it must have both PATA IDE and SATA drivers installed by default. Most newer Linux versions must now come with both hard drive controller drivers.

---

