---
title: "Filesystem Check Fails on Startup"
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by njkillian on 2007-08-27
The filesystem check fails on startup. Previous threads said to check that the UUIDS are correct in fstab. I have ubuntu 7.04 feisty fawn desktop and this is my error:

Log of fsck -C -R -A -a
Tue Aug 21 18:40:55 2007

fsck 1.40-WIP (14-Nov-2006)
/home: clean, 114025/5128192 files, 7008223/10239429 blocks
/dev/sda: clean, 10348/24428544 files, 41250079/48840246 blocks
/dev/sdb: clean, 3287/24428544 files, 37555924/48840246 blocks
fsck.ext3: Unable to resolve 'UUID=a9cdbf61-bc17-4997-9c62-a74fc91fd5c3'

fsck died with exit status 8

Tue Aug 21 18:40:55 2007
----------------
looking at this thread: [http://ubuntuforums.org/showthread.php?t=364216](http://ubuntuforums.org/showthread.php?t=364216)
 the UUIDs look the same to me...some other problem? Here is the output from what rsambuca said to do on that previous thread:

ls /dev/disk/by-uuid/ -alh
ls /dev/disk/by-uuid/ -alh
total 0
drwxr-xr-x 2 root root 160 2007-08-23 11:02 .
drwxr-xr-x 6 root root 120 2007-08-23 11:02 ..
lrwxrwxrwx 1 root root   9 2007-08-23 11:02 0c1734aa-b01c-4b8b-9bd4-77e48a60cf6c -> ../../sda
lrwxrwxrwx 1 root root  10 2007-08-23 11:02 440c88e4-4555-4380-91e3-6a0121042259 -> ../../hda3
lrwxrwxrwx 1 root root  10 2007-08-23 11:02 5a1e3c1a-dc3a-4a5a-9fc7-38ef8f926870 -> ../../hda1
lrwxrwxrwx 1 root root  10 2007-08-23 11:02 9a281aee-4b48-4eeb-881b-39c81a7f89d0 -> ../../hda2
lrwxrwxrwx 1 root root  10 2007-08-23 11:02 a9cdbf61-bc17-4997-9c62-a74fc91fd5c3 -> ../../hdb1
lrwxrwxrwx 1 root root   9 2007-08-23 11:02 c0575518-8674-4e2b-a9ec-df519a757703 -> ../../sdb

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=5a1e3c1a-dc3a-4a5a-9fc7-38ef8f926870 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=9a281aee-4b48-4eeb-881b-39c81a7f89d0 /media/hda2     ext3    defaults        0       2
# /dev/hdb1
UUID=a9cdbf61-bc17-4997-9c62-a74fc91fd5c3 /media/hdb1     ext3    defaults        0       2
# /dev/sda
UUID=0c1734aa-b01c-4b8b-9bd4-77e48a60cf6c /media/sda      ext3    defaults        0       2
# /dev/sdb
UUID=c0575518-8674-4e2b-a9ec-df519a757703 /media/sdb      ext3    defaults        0       2
# /dev/hda3
UUID=440c88e4-4555-4380-91e3-6a0121042259 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

