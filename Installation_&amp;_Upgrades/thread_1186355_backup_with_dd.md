---
title: "backup with dd"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by frindly on 2009-06-13
hello,
i backup my root partition with dd to an image file. before i work with partimage, but with bigger partitions it give problems and so i u se dd to backup.
for backup i use:
dd if=/dev/sda1 of=/backup/filesystem.img
dd if=/dev/sda of=/backup/boot.img bs=512 count=63

fo restore:
dd if=/backup/filesystem.img of=/dev/sda1
dd if=/backup/boot.img of=/dev/sda bs=512 ount=63
(if necessary to restore the boot block with grub)

is this a good methode com backup the complete root partition to an image file and restore it exactly back?
with the boot.img i backup the boot sector and grub data before the partition 1 begins.

is this a good solution? ;)

---

