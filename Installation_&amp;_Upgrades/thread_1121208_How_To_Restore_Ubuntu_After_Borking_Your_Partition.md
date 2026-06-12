---
title: "How To: Restore Ubuntu After Borking Your Partition Scheme"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by Peasantoid on 2009-04-09
We've all done it. Perhaps GParted froze up and you were forced to kill the process. Or maybe you installed another distro and accidentally fragged your Ubuntu partition (this happened to me when I installed Fedora). Whatever the cause, you're up a creek without a paddle. Here's how to fix your system.

**Prerequisites**
* You have a complete backup of your Ubuntu installation. **If you don't keep backups, start. Now.**
* You use GRUB as your bootloader.
* You have a second OS, preferably a Linux distro, that understands the filesystem your Ubuntu uses. It must not be on the borked drive. I recommend the Ubuntu live CD, if only because just about everyone has one.

**What To Do**
1. Boot into the other OS.
2. Fix your partition scheme. The Ubuntu live CD has GParted; I recommend this for non-CLI-savvy users. (System > Administration > Partition Editor)
3. Copy your backup onto the destination volume. Make sure to preserve metadata, or weird things are likely to happen later.
4. Reinstall GRUB using [this](http://ubuntuforums.org/showthread.php?t=224351) guide.
5. When you try to boot your restored system, it'll hang. This is because GRUB is trying to load Ubuntu from a nonexistent volume.
6. Boot the other OS again.
7. Mount the Ubuntu partition.
8. Open /etc/fstab and /boot/grub/menu.lst (on the Ubuntu partition) in your favorite text editor. You'll notice a bunch of "UUID=something-goes-here". This is what's causing the problem. (I'll explain what this means at the end of the guide.)
9. In a terminal, run "sudo blkid /dev/DRIVE", where "DRIVE" is the device node of your Ubuntu partition. (For example, I did "sudo blkid /dev/sda3".) You will see something like this:
```
/dev/sda3: UUID="cf1796e1-a1dc-403c-a4a4-e4a30777e687" TYPE="ext3" LABEL="MySuperUbuntu"
```
The UUID is what you want. In this case, it's "cf1796e1-a1dc-403c-a4a4-e4a30777e687" (without quotes).
10. Return to the text editor and replace the UUIDs that correspond to your Ubuntu partition. Here is my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=blah-blah-blah /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=blah-blah-blah-something-else   none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
Here, I'm fixing the UUID for /dev/sda3 (mount point: /). "blah-blah-blah" would become "cf1796e1-a1dc-403c-a4a4-e4a30777e687".
11. Repeat #10 on /boot/grub/menu.lst. It's probably safe to replace all the UUIDs there, unless you have GRUB set to boot other systems. Needless to say, you should exercise caution if this is the case &#8212; only modify the stanzas that correspond to Ubuntu.
12. For each UUID-based entry in /etc/fstab, repeat steps 9 and 10. I had to correct the UUID for my swap partition as well.
13. Save the two files and exit.
14. Boot into your Ubuntu partition. It should work now.

**What Are UUIDs, Anyway?**
UUIDs are used to identify drive partitions. They're a feature of the ext* filesystems (and probably others).

UUID stands for Universally Unique IDentifier. Instead of using device nodes or volume labels, which can change, UUIDs provide a means for the system to definitively identify volumes. The only downside to this system is that formatting a partition creates a new UUID, so if you try to boot an Ubuntu system with incorrect information, GRUB will just sit there until a volume with the [bad] UUID is found &#8212; i.e. forever, since one doesn't exist.

**Finally...**
Hopefully this guide will help someone. If I've been too vague, feel free to notify me.

---

