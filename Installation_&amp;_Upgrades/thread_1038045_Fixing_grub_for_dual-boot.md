---
title: "Fixing grub for dual-boot"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by ejn114 on 2009-01-12
Hi,

I have a desktop that's been running only Ubuntu from the beginning.  I decided the other day to try out the Windows 7 beta, so I shrank my /home partition and installed Windows in the newly unallocated space.  So, my drive looks like this:

1. root Ubuntu partition (~15GB)
2. /home (~525GB)
3. Windows 7 (~100GB)

Upon installing Windows 7, as expected, the Windows bootloader replaced grub and Windows automatically started upon bootup.  I did a little research through these forums and the internet at large and found [SuperGrubDisk]("http://www.supergrubdisk.org").  Using it, I was able to restore grub as the bootloader, but now only Ubuntu will start (grub doesn't see Windows).  I can also boot Windows using an option from SuperGrubDisk, but I can't figure out how to get Windows to show up in grub as an option.

My question is this: how do I fix grub so that Windows is an option?  Alternately, is there some other bootloader I should use so that both operating systems will show up?

Thanks in advance,

EJN

---

### Post by damphoud on 2009-01-12
to better understand your setup, what are the outputs of:

sudo fdisk -l

cat /etc/fstab

---

### Post by ejn114 on 2009-01-12
Here's the result of fdisk -l, turns out there are five partitions:
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00045684

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       63598   510850903+  83  Linux
/dev/sda2   *       63599       63624      204800    7  HPFS/NTFS
/dev/sda3           63624       76346   102193152    7  HPFS/NTFS
/dev/sda4           76347       77825    11880067+   5  Extended
/dev/sda5           76347       77825    11880036   82  Linux swap / Solaris
```

---

### Post by ejn114 on 2009-01-12
Here's cat /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7271574f-2f04-4f0d-bf3e-a51f9fbca7ca /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=79bf679c-7dd5-4369-a6b6-943e83abe95b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by kranny on 2009-01-12
Why dont you edit your menu.lst manually to include windows 7 if there isnt one.


title Windows seven
root (hd0,1)
makeactive
chainloader +1

---

### Post by ejn114 on 2009-01-12
> **kranny said:**
> Why dont you edit your menu.lst manually to include windows 7 if there isnt one.


title Windows seven
root (hd0,1)
makeactive
chainloader +1

Thanks, that worked like a charm.  One other question, though: in order to access the grub menu, I have to press ESC within a three-second window.  On my laptop, which dual-boots XP and Ubuntu, the grub menu is always shown.  How do I set things up so that the grub menu is always shown?

---

### Post by kranny on 2009-01-12
By default GRUB Hides the menu .Open your menu.lst and search the section that looks like this

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
Put a # before hiddenmenu to comment that line out.Save the file, and you should see the menu the next time you reboot.

---

### Post by dstew on 2009-01-12
Find the line in /boot/grub/menu.lst that is **hiddenmenu** and comment it out (put a # in front of it).

---

