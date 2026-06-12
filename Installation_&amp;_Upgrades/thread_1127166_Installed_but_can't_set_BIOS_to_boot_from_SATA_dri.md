---
title: "Installed but can't set BIOS to boot from SATA drive"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by mickwombat on 2009-04-16
I have an old(ish) Compaq Evo D510 and I put in a new SATA drive, which needed a PCI card adapter.

Installed Ubuntu fine with a seperate boot & home partition.
In the BIOS options, I can only set it to boot from IDE drive (or USB & CD).  The original IDE drive has been removed.

So, I need to put the boot partition onto a USB and set the BIOS to boot that.

Is it just a case of making a clone of this partition, using Clonezilla or do I need to do some tweaks to the menu.lst file so that it will just load up Ubuntu as normal?

Thanks

;)

---

### Post by khelben1979 on 2009-04-16
Have you tried to look for a BIOS upgrade?

---

### Post by mickwombat on 2009-04-17
Actually just reinstalled and chose to use the USB for the bootloader.  Working fine now.

---

