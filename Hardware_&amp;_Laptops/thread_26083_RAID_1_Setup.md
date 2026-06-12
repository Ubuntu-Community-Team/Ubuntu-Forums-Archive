---
title: "RAID 1 Setup"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by teamchachi on 2005-04-11
I've got two 160GB SATA disks connected to an Abit nf7-s2g motherboard.  The motherboard has an integrate Sil 3112A SATA controller.

I tried setting up RAID 1 in the bios using the intregated controller and then installing Ubuntu.  No luck.  Ubuntu still saw two drives instead of one.

I've now resolved myself to using Linux Software Raid.

Here's my current setup which works (kind of)

md0  100mb  /boot partition
md1  159 GB  Using LVM

It installs and everything is happy.

Here's the problem:  It doesn't work if I turn off the power to one of the drives. It won't  boot.  Clearly mirroring the /boot partition is not working.

Am I going about this the wrong way?  Is it possible to mirror the /boot partition using software raid?

---

### Post by Gandalf on 2005-04-11
[QUOTE=teamchachi]I've got two 160GB SATA disks connected to an Abit nf7-s2g motherboard.  The motherboard has an integrate Sil 3112A SATA controller.

I tried setting up RAID 1 in the bios using the intregated controller and then installing Ubuntu.  No luck.  Ubuntu still saw two drives instead of one.

I've now resolved myself to using Linux Software Raid.

Here's my current setup which works (kind of)

md0  100mb  /boot partition
md1  159 GB  Using LVM

It installs and everything is happy.

Here's the problem:  It doesn't work if I turn off the power to one of the drives. It won't  boot.  Clearly mirroring the /boot partition is not working.

Am I going about this the wrong way?  Is it possible to mirror the /boot partition using software raid?[/QUOTE]
 well in setup use RAID1 instead of LVM

---

