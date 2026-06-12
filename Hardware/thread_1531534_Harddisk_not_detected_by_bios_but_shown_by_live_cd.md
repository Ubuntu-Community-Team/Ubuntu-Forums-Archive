---
title: "Harddisk not detected by bios but shown by live cd"
date: 2010-07-15
forum: Hardware
---

### Post by jawadahmed on 2010-07-15
My live cd can detect hard disk and all data it contains is shown, but the bios does not show hard disk at all.  It happened just last night and i am unable to boot from hard disk.

---

### Post by dabl on 2010-07-15
That sounds backwards -- I would think if one of them could NOT detect the hard drive, it would be the Linux kernel, not the BIOS.

However, if that is literally true, then your computer is broken. 

You need to back up the data that is on that hard drive, then remove it and fix or replace the motherboard with the broken BIOS.

---

### Post by Alexis Phoenix on 2010-07-16
Try putting the disk on another ide channel - it may be a fault specific to the controller for that chaunnel.  Also, check your bios settings - some types let you manually set disk geometry.  You've said nothing about your hardware so it's difficult to make suggestions which are sane to you.

Another option, assuming there is nothing wrong with the disk itself, is to use a controller card instead of the onboard ide - you may need to give a boot parameter for this to work though.  Make sure it is possible to boot from the card if you take this route.  Cheaper than an new mobo anyways ;)

Alexis

---

### Post by jawadahmed on 2010-07-17
I tried to change cables and the ide channel but did not repair the problem. I reset the bios and no improvement. Then i took the cpu to repair shop and had the bios flashed. Now its working again on the same cables.

---

