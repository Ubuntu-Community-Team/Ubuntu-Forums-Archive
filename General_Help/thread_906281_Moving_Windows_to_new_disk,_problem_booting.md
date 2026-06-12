---
title: "Moving Windows to new disk, problem booting"
date: 2008-08-31
forum: General Help
---

### Post by fadenb on 2008-08-31
Hi.

First some information to describe the current situation:

Computer with 3 IDE disks and dvd-drive.

primary master: 80 gig samsung
primary slave: 30 gig wdc
secondary master: 30 gig wdc
secondary slave: dvd

pm: 1 partition with windows xp
ps and sm together in software raid: partition 1 (/boot, mirrored), partition 2 (/ , mirrored), partition 3 (swaps)

Grub is installed on the primary master and everything is just working fine (OS selection via grub menu) except that the old samsung disk is defect (read/write errors).

I got a new 80 gig SATA drive and wanted to move all the data from the old disk to the new one. I used "dd if=/dev/sda of=/dev/sdX....". I removed the old disk and configured the bios to boot from the new sata disk (should contain everything needed to boot because it is an exact copy of the old one).

The Problem: Only a single "GRUB" is being displayed and nothing else happens.

Any ideas what I did wrong?
Thx for any advice!

---

### Post by Sycron on 2008-08-31
Do you have the XP instalation CD ? If so then boot it into Recovery Console and type **fixboot** and **fixmbr**.

---

### Post by mrsteveman1 on 2008-08-31
hmm. If you did a block copy of the entire disk, including partition table and MBR code area, it should work the same.

I'm not as familiar with how Windows boots but i know you can't move an installed windows copy into another box sometimes (it refuses to boot and bluescreens because of hardware changes).

I'm not sure though about changing disks. Perhaps somewhere in the boot process it uses the disk serial number for something? But then again if the thing isn't even booting grub then this has little to do with Windows.

You should fix grub first because the VBR for windows is probably fine.

---

### Post by fadenb on 2008-08-31
> **mrsteveman1 said:**
> hmm. If you did a block copy of the entire disk, including partition table and MBR code area, it should work the same.

That is what i thought too :p
> **mrsteveman1 said:**
> 
...snip...

You should fix grub first because the VBR for windows is probably fine.

Thx! I used super grub disk to fix grub and now it is working :)

---

