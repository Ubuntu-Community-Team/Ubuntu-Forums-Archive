---
title: "usb key on dell laptop"
date: 2006-09-19
forum: Hardware &amp; Laptops
---

### Post by erikringmar on 2006-09-19
Dear all,

I can't get my usb key to show up on the desktop when I plug it in.  I've tried rewriting fstab, but I'm not doing it right.  It looks like this:

proc /proc proc defaults 0 0
/dev/hdc1 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
/dev/hdc5 none swap sw 0 0
/dev/hdb /media/cdrom auto user,atime,auto,rw,dev,exec,suid 0 0
/dev/sdb1 /mnt/sdb1 vfat uid=0,gid=0,auto,rw,users 0 0
/dev/hda /media/cdrom0 ext2 nouser,noauto,atime,auto,ro,nodev,noexec,nosuid 0 0
/dev/sdc1 /mnt/sdb1 vfat uid=0,gid=0,auto,rw,users 0 0

Fdisk gives this output:

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...

I've installed usbmount but I don't know what to do with it.  Help!

Erik

---

### Post by jd65pl on 2006-09-19
Does the USB stick mount when you plug the stick in?

Is it listed in the folder /media


Thanks

J

---

