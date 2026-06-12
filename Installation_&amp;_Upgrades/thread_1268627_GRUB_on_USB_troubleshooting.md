---
title: "GRUB on USB troubleshooting"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by janeks on 2009-09-17
Hi!

I installed GRUB on USB stick using this description:
[http://blog.torh.net/2007/08/19/creating-a-bootable-usb-flash-drive/](http://blog.torh.net/2007/08/19/creating-a-bootable-usb-flash-drive/)
And readed out some similar how tos and checked GRUB manual.

It seems that all should be fine, but upon start I get (depending on BIOS) blank screen or pause before MBR is loaded from HD.

So it seems, that BIOS supports USB booting, but it looks like on USB is something wrong?
Am I right in this conclusion?

What other could be wrong?
How to check?

File list on my USB:
/media/disk/boot/grub
/media/disk/boot/grub/default
/media/disk/boot/grub/device.map
/media/disk/boot/grub/e2fs_stage1_5
/media/disk/boot/grub/fat_stage1_5
/media/disk/boot/grub/installed-version
/media/disk/boot/grub/jfs_stage1_5
/media/disk/boot/grub/menu.lst
/media/disk/boot/grub/minix_stage1_5
/media/disk/boot/grub/reiserfs_stage1_5
/media/disk/boot/grub/stage1
/media/disk/boot/grub/stage2
/media/disk/boot/grub/xfs_stage1_5
/media/disk/boot/memtest86+.bin

brgds and thanks in advance,
Janeks

---

### Post by bumanie on 2009-09-17
Try searching [here]("http://www.pendrivelinux.com/category/flashdrive-installs-using-linux/") and doing a persistent installation, it should be more reliable. Also try the usb creator that is included in the later ubuntu versions (if you have one - can't quite remember when the usb creator was added). I have some mobo's bios boot well with usb media, some don't. Mine will boot a usb hard drive, but not a usb pendrive, whereas my work computer will do it the other way around.

---

### Post by mantelo on 2009-09-17
It's easier to use syslinux, which boots from a fat partition and it is installed by when you create your pen-drive using "usb-creator"

If you need to boot different installs on different partitions, you could chain syslinux to grub4dos. [This]("http://aronzak.wordpress.com/2008/09/16/howto-syslinux-and-grub-on-one-usb-drive/") is a good guide for doing it.


Good luck!

---

