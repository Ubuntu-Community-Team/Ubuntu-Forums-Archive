---
title: "Migrate ext3 to ext4"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by vange on 2009-11-04
I followed the guide "Converting an existing Ext3 file system to Ext4" ([https://help.ubuntu.com/community/ConvertFilesystemToExt4](https://help.ubuntu.com/community/ConvertFilesystemToExt4)).

But after I updated fstab and rebooted, the root partition still is mounted as ext3. I only have two partitions on my disk: root and swap.

I dare not continue with step 2 of the guide, as it looks like the partition is mounted with ext4 driver.

Do you know what to do next? Or troubleshoot in any way?

Output of "dmesg | grep EXT":
[    3.373020] EXT3-fs: mounted filesystem with writeback data mode.
[    7.593538] EXT3 FS on sda1, internal journal

Output of "mount":
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)

Contents of fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e3627f49-d0fb-4b10-aa28-8e628cb527f6 /               ext4    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4439a8b7-a3a3-428c-abec-f503bcdbc039 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by vange on 2010-01-20
The guide works!

I did a full backup of my partition and performed an upgrade, just in case. And it works fine.

Closing this thread.

---

