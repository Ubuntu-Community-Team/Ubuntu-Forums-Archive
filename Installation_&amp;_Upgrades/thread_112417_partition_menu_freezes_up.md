---
title: "partition menu freezes up"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by bastos.sergio on 2006-01-04
Hello,
I am unable to install ubuntu 5.10 on my home computer.  I have 2 hard disks.  On my master disk I have windows xp, and on the slave disk I want to install linux.
Problem is, when I run the install program the partition menu seems to freeze up and I can't proceed.  I have found a workaround to this.  If I remove the master disk the installation will occur normally, but after I reconnect the master disk the grub loader is gone, and I don't know how to force it to install again.
Could somebody help?
Thank you,

Sergio Santos Bastos

---

### Post by az on 2006-01-04
Easy.  Boot the installer and go to the console (CTRL-ALT-F2)  chroot into your install

mkdir /mnt
mount /dev/hdb1 /mnt
chroot /mnt
grub-install /dev/hda


You will probably have to change fstab and menu.list entries to adjust the fact that ubuntu thinks it is on hda instread of hdb (fstab hda-> hdb, grub hd(0,0)->hd(1,0) as well as the device.map)

---

