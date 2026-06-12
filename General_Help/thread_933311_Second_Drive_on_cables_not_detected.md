---
title: "Second Drive on cables not detected"
date: 2008-09-29
forum: General Help
---

### Post by jecottrell on 2008-09-29
Been trying to build a NAS and have a bunch of drives in a xubuntu box.

Current hardware setup:

IDE0: two hardrives
IDE1: one DVD

Expansion IDE cards (2)
IDE0: one hard drive
IDE1: one hard drive

IDE0: one hard drive
IDE1: one hard drive

(All the expansion drives are on single connector cables jumpered to master.)

When I: ls /dev/hd*

It only shows:

hda hda1 hdc hdc1 hde hde1 hdg hdg1

Why can't I see the second drives on each cable/card?

Thanks.

John

---

### Post by jecottrell on 2008-09-29
Found part of the problem. My understanding of sd vs. hd


All disks appear when I fdisk -l

Main board drives are sd and expansion board drives are hd...

---

### Post by mindoms on 2008-09-29
You can use/mount sdX and hdX pretty much the same way. 

there is just a different driver in the back.
sdX was formerly used for SCSI, then for USB and SATA-drives, but now it also took over most of the IDE parts.

---

