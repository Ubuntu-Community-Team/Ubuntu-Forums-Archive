---
title: "Help w/ getting Sis966/1184 SATA2 controller working"
date: 2006-10-01
forum: Hardware &amp; Laptops
---

### Post by rowol on 2006-10-01
Hi,

I have a Shuttle SS30G2 which has a Sis Southbridge 966L with a SATA-2 RAID disk controller on the motherboard.  I'm running the cotroller in AHCI mode via BIOS settings.   That controller is not supported by the 2.6.15 kernel in the 6.06.1 Ubuntu release.   ](*,)   I get "Unknown device 1184" from lspci with the kUbuntu live CD.

It looks like the 2.6.18 kernel supports it.   I have also found patches for the ahci.c driver code against the 2.6.17.11 kernel source so it might also be in the later 2.6.17 kernels, not sure.

What would be the easiest way to install Ubuntu onto my system?   If I need to patch drivers, modprobe them at some point during the installation, etc could you briefly explain how to do it?   i.e. do I need to get the whole kernel source or just the driver source? (and where might I find the driver source?)  Pointers to HowTo's, existing forums, etc would be appreciated if this info is already available.

Once I got Ubuntu onto the machine, I would probably just build a 2.6.18 custom kernel anyway as my onboard ethernet controller and pci wifi card are also not supported in the 2.6.15 kernel - the problem is the preliminary install as now I can't even partition the disk, etc.

Thanks!
Ross

---

### Post by rowol on 2006-10-23
I got this to work by remastering the Edgy EFT Beta install with a patched AHCI/SATA driver (and also a different Sis190 driver.)

See post [http://www.ubuntuforums.org/showthread.php?p=1651238](http://www.ubuntuforums.org/showthread.php?p=1651238)

---

### Post by joeytw on 2006-11-21
I am also similar ](*,) ](*,) ](*,)

---

### Post by peterbutler on 2007-02-07
I've put rowol's instructions for getting this working on the wiki here: [https://wiki.ubuntu.com/ShuttleSs30G2InstallEdgyHowTo](https://wiki.ubuntu.com/ShuttleSs30G2InstallEdgyHowTo)

Let me know if you can see anything that needs to be added/changed.

Cheers

Peter

---

### Post by donhamilton on 2007-04-18
Will these drivers be included in 7.04 ??

don

---

### Post by donhamilton on 2007-04-18
After rerding about compiler the SIS drivers and installing them into the the CD,

I am not interested it doing this.

Does any one have this already done so I can download a new ISO for my shuttle.

Thanks

don

rowol are you still here ??

---

