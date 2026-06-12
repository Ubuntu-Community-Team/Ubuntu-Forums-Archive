---
title: "Trying to add Windows 7 RC to grub loader"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by low_mat on 2009-05-29
Here's what I have in my grub/menu.lst:

title Windows 7
root (hd1,0)
chainloader +1
makeactive

When I try it I get the BOOTMGR is missing and to do an CTRL+ALT+DEL and restart.

Here's my fdisk. What am I doing wrong? I'm trying to boot to my second hard drive which had windows 7 on it. Thanks fro the help.

matt@matts:~$ sudo fdisk -l
[sudo] password for matt: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc783c783

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe9c9e0d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS

---

### Post by low_mat on 2009-05-29
Can anyone help?

---

### Post by hyperdude111 on 2009-05-29
Read through this guide i made on how to dual boot win7 and ubuntu.
[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

I think some of the posters had the same problem as you but sorted it out, read through there.

---

### Post by coffeecat on 2009-05-29
I think you have to use the map commands for disk-swapping because Windows doesn't like to boot from anything but the first disc. See here:

[http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows)

Also, you may need to use the rootnoverify command rather than the root command, but I have no idea why. The Ubuntu installer sometimes uses root and sometimes rootnoverify on my systems where I always have Windows on the first disc. Pass. :?

**Edit:** after using the map commands, you *may* have to use (hd0,0) in the root/rootnoverify line because you've remapped the drives. But try both (hd0,0) and (hd1,0) - hopefully one will work.

---

