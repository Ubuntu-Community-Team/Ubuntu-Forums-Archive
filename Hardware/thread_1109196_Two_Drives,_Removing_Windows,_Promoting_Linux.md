---
title: "Two Drives, Removing Windows, Promoting Linux"
date: 2009-03-28
forum: Hardware
---

### Post by Tiler on 2009-03-28
I'll try to do the synopsis justice.
I have had two internal SATA drives for a while. Primary with XP and Secondary with Hardy.  Successful dual booting has existed harmoniously for over a year and it's time to finally demote the XP drive to USB to make room for a larger backup drive.  I can't get the second drive (My long time Hardy Drive) to boot when I remove the XP drive.  I've used SuperGrub to remove and reinstall grub on the second drive, tried it in bay 1 or bay 2 with no success.  Clearly I'm missing something.

Reinstalling isn't an option.  I intend to keep the XP drive bootable (probably with SGD) but for all intents and purposes, it need not show up in the grub menu from now on.

Here's sfdisk -l

> 
Disk /dev/sda: 9726 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+      6       7-     56196   de  Dell Utility
/dev/sda2   *      7    9273    9267   74437177+   7  HPFS/NTFS
/dev/sda3       9274    9724     451    3622657+  db  CP/M / CTOS / ...
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda4       9725    9725       1       8032+  83  Linux

Disk /dev/sdb: 48641 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+  47267   47268- 379680178+  83  Linux
/dev/sdb2      47268   48640    1373   11028622+   5  Extended
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
/dev/sdb5      47268+  48640    1373-  11028591   82  Linux swap / Solaris


Grub info:> 
grub> find /boot/grub/stage1
 (hd1,0)

FSTAB> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=d5fd3a1c-97f7-4e79-9fce-34f3f5256db5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=5717a912-f14e-4d91-b107-84b329c9d40c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Tiler on 2009-03-28
Do this:

Backup menu.lst
Use Super Grub to delete Grub.
Remove Windows Hard drive.
Boot Live CD and [reinstall Grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
Reboot
If fail, boot with Super Grub
Edit menu.lst to match your results from Grub> find /boot/grub/stage1 (See [link above]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"))

Enjoy

---

