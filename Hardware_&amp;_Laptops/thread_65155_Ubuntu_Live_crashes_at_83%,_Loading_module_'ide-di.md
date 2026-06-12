---
title: "Ubuntu Live crashes at: 83%, Loading module 'ide-disk' for 'Linux ATA Disk'..."
date: 2005-09-13
forum: Hardware &amp; Laptops
---

### Post by Kaaske on 2005-09-13
I have a serious problem with my pc:
Several operating systems do not work properly on it: they often crash  :mad: 
Installing new operating systems result in a crash during installation; always at a particular point during installation.

[B]When I try Ubuntu 5.04 Live, it always crashes / stops at:
83%
Loading module 'ide-disk' for 'Linux ATA Disk'...[/B]

I've tried almost everything in my power to overcome this problem:
* update the flash BIOS to newer versions
* format the harddrive
* scandisk the harddrive
* use antoher cd-rom drive

Nothing helps! ](*,) It always stops at 83% (the screen just freezes and I have to reboot).

[B]Having read Ubuntu 5.04 Live needs no harddrive, I disconnected the harddrive. The result was it now crashes / stops at:
86%
Loading module 'ide-cd' for 'Linux ATAPI CD-ROM'...[/B]

Is there anyone who has any clue as to what's going wrong?

I hope you can help me with this!

Kaaske

PS 
Some system info:
GIGABYTE Motherboard: GA 7VRX (Rev 1.1)
AMD Athlon XP 2000+
256 MB RAM
40 Gb Harddrive
cd-rom drives:
LG 	type: E-IDE CD-ROM 56X/AKH		40x 12x 40x
MTRP? 	type: HL-DT-ST CD-RW GCE-8400B	56x

---

### Post by Gezzer on 2005-09-13
try via the bios changing the drive access from AUTO to LBA for the HDD
this can also be done for the CD drives (if required)
save settings now try the install ...

this isn't a seagate HDD per chance ...

---

