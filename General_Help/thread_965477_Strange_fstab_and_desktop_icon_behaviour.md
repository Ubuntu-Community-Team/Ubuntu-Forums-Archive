---
title: "Strange fstab and desktop icon behaviour"
date: 2008-10-31
forum: General Help
---

### Post by El Jamo on 2008-10-31
Fresh install of Intrepid, IBM r51 laptop, dual-booting XP-Pro.
I'm sharing documents between XP and Ubuntu through an EXT3 partition (installed EXT3 capability in XP).  When I try to mount the EXT3 partition in /home/james/share it works, but I also get an icon on my desktop for that partition.  If I mount the same partition in /share instead, it also works,  but I don't get the icon on my desktop.

I don't want the icon on my desktop, so I mounted it at /share and created a symlink to /home/james/share as a workaround.  I can't figure out why it treats the two mount points differently, and would like to know if there's a way to mount it in my home folder without getting the icon on my desktop.

Here's my original /etc/fstab that was created at install (/dev/sda6 is the partition I'm concerned with).

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=1dee1181-f558-4bd4-ade4-f92956663921 /               jfs     relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=29acdf88-2e97-485b-9182-3f6de1f8d600 /home           jfs     relatime        0       2
# /dev/sda6
UUID=6368746f-2074-616b-6f65-207575696400 /home/james/share ext3    relatime        0       2
# /dev/sda1
UUID=E8B877BAB877863A /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda8
UUID=6368f884-5b4d-918b-3d08-3c8598c9c6ab none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

And here's my modified fstab, mounting it in /share and symlinking:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=1dee1181-f558-4bd4-ade4-f92956663921 /               jfs     relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=29acdf88-2e97-485b-9182-3f6de1f8d600 /home           jfs     relatime        0       2
# /dev/sda6
UUID=6368746f-2074-616b-6f65-207575696400 /share ext3    relatime,user       0       2
# /dev/sda1
UUID=E8B877BAB877863A /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda8
UUID=6368f884-5b4d-918b-3d08-3c8598c9c6ab none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Any help would be appreciated.

---

