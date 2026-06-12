---
title: "Editing fstab"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by MrDead on 2009-03-17
As of right now I have a slightly convoluted set up for my new (self-built) computer in addition to a host of problems. One of these problems is that I cannot get the computer to boot off of the correct partition. I have my hard drive (SATA) partitioned into two parts: (1) An NTFS partition that I cloned from my old computer (2) A primary partitioned split into two logcial drives: (a) A Linux swap partition and (b) A Ext3 partition on which I installed Ubuntu 8.10 64-bit. As of now I am having a lot of trouble just booting into the cloned partitioned, additionally the live-cd only works sporadically. It's possible that this is a hardware problem, but I doubt it. Anyhow, I accessed my Fstab file for my 2nd primary partitioned and this is what is contained in it:
#/etc/fstab: static file system information
#
#<filename> <mount point> <type> <options> <dump> <pass>
  proc       /proc        proc    defaults   0      0
#/dev/sdb6
UUID= (I don't think you need to know that actual UUID) /      ext3     relatime,errors=remount-ro 0   1
#/dev/sdb5
UUID=(You don't need to know this one either)  none    swap     sw    0     0
/dev/scd0      /media/cdrom0    udf,iso9660, user, noauto, exec, utf8   0    0

Essentially what I want to know is how to boot off this device instead of the old NTFS one.

Thank you

---

### Post by circa82 on 2009-03-18
I'm afraid /etc/fstab won't solve your booting problem. fstab is used to mount partitions under static mount points, it doesn't control boot. It would be more helpful to see the ouput of 'fdisk -l' and your current menu.lst file.

```
# [color=blue]sudo fdisk -l[/color] <-- lowercase L
# [color=blue]cat /boot/grub/menu.lst[/color]
```

---

