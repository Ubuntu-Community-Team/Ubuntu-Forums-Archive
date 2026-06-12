---
title: "SATA drive with Hardy and Intel DG43NB motherboard (ICH10)"
date: 2009-01-31
forum: Hardware
---

### Post by thorheimdall on 2009-01-31
Mother Board: Intel DG43NB
SATA controller: Intel Corporation 82801JI (ICH10 Family)

Here is my problem:

I can only boot in Kubuntu Hardy if I set SATA to the AHCI mode in the BIOS.  In the normal (IDE) native mode, it won't see any SATA drive (for the live CD), or it will stall forever during the boot process (once installed).  My computer has dual boot with Widows XP, which BSOD if in the AHCI mode.

So each time I want to boot on Linux or Windows, I have to go in the BIOS and set the SATA mode to native IDE for Windows, and AHCI for Linux, which is really annoying.

I installed the linux-backports-modules package in the hope that the driver for the SATA controller have been backported, but it seems it is not the case.  Using the live CD and the normal IDE mode, there is no reference of any SATA drive controller by looking at dmesg.

Updating to Intrepid is not an option for me (KDE 4.1 ...).

Any idea to get it work?

---

