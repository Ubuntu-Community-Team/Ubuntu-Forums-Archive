---
title: "After 9.10 upgrade swap and usb fs don't work"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by AngusM on 2009-11-01
I'm at my sister's house, and I managed to fix the disaster involving menu.lst, but now when I start I get a very brief message telling something like "one or more filesystems in fstab cannot yet be mounted" then something about "swap" and "usbfs". The genius program that is giving the message does not repeat it in any file under /var/log. Indeed, the swap partition is not mounted, and if I manually swapon, it is. Here's the fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0189838d-7289-403e-a2cf-e00f67d436ec /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda6
UUID=5810a4ff-c5e9-4516-9330-6b051ef5eed0 /home           ext3    defaults,relatime        0       2
# /dev/sda5
UUID=17ea293c-0959-4341-ac52-dc2d82bab4c0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
#
# [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
/dev/sda2     /mnt/c ntfs locale=en_US.utf8 0 0

I've read about other problems people are having, and they are about a system that is totally broken and won't start up. I can start up, but these two filesystems just aren't mounting. I've tried
> sudo update-grub
and
> dpkg --configure -a
and none of these work. I'm scared to leave this computer w/out the swap automatically coming on, and I don't know what damage an absent usb fs does.

---

