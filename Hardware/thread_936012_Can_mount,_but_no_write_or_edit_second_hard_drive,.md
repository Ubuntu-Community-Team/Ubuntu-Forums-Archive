---
title: "Can mount, but no write or edit second hard drive, Need help!"
date: 2008-10-02
forum: Hardware
---

### Post by Animal_Allen on 2008-10-02
I have a second hard drive in my computer, however I cannot create a new folder in it or write to it.  I can't basically just mount it.

Format: Ext3

Mount Point: /media/disk

Fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fa25f61e-2b44-46dc-b288-883c03f3c508 /               ext3    relatime,erro$
# /dev/sda5
UUID=634ff962-1ac5-4b68-b4d7-4606fbc830cd none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/scd1       /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0


Fdisk shows this:

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0150014f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9588    77015578+  83  Linux
/dev/sda2            9589        9964     3020220    5  Extended
/dev/sda5            9589        9964     3020188+  82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x84263459

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14946   120053713+  83  Linux

Any help to get my second hard drive read would be appreciated, thanks!

---

### Post by Animal_Allen on 2008-10-02
Anyone have any ideas at all?  I'm been spending all day searching the forums for something helpful, but nothing I try seems to have anny effect.

Basically, I can't write anything onto the disk, create a new folder, etc.

I just want to use this hard drive as a storage drive.

---

