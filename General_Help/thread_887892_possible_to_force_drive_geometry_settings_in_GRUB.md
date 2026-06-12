---
title: "possible to force drive geometry settings in GRUB?"
date: 2008-08-12
forum: General Help
---

### Post by miatawnt2b on 2008-08-12
I am having a very bad day all of a sudden.  I installed a new hard disk, 250Gb, in my laptop (with new install of 8.04) last week and have things finally set up just how I need them.  Today, after playing around with a wireless adapter, I rebooted and received a grub error 16: inconsistent filesystem structure. I booted into the live CD, and ran a e2fsck -C0 -p -f -v /dev/sda1 and everything checked out OK.  The boot partition (sda1) was set up as most of the disk, around 247Gb.  Fdisk sees the partition, e2fsck sees it and checks it fine using the live CD.  I ran a grub-install and still get the error.

So I start to dig a bit into the hardware, and it seems my laptop, a DELL Inspiron 8600 only supports disks to 137Gb.  My guess is that I filled the 247Gb partition past 137Gb and now Grub is confused because it is trusting the drive geometry that the BIOS reports.

So I am wondering if I am completely hosed here or is there a way to pass the actual drive geometry to GRUB?

If Grub won't cut it, is there another bootloader I can use?

If I re-partition the drive so that the boot partition is less than the first 137Gb of the disk, will that work?

-J

---

