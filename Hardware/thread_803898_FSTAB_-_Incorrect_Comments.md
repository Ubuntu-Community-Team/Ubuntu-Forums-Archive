---
title: "FSTAB - Incorrect Comments"
date: 2008-05-22
forum: Hardware
---

### Post by Haydn1 on 2008-05-22
Hey there everyone, 

I wanted to ask a quick question to the community. I have recently moved over to Ubuntu and am just loving my time with it. Learning the ins and outs has been a pleasure and I find myself addicted to exploring the system. So on to my question. 

I am in the process of automounting my hard drives. When I first opened FSTAB to edit I noticed something. I believe my file maybe incorrect here. Take a look at the comment headers for the drives and let me know what you think. 

As a note I did have to edit Grub to locate the correct partition on my first hard drive. But it was at least pionted to the right disk. The comment is FSTAB are pointed at the completely wrong drive. 

Your thoughts?

Is there a better way to list Terminal output? Thanks

fdisk -l  ------------------------------------------------------

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdaa7daa7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9561    76798701    7  HPFS/NTFS
/dev/sda2            9562       22309   102398310    7  HPFS/NTFS
/dev/sda3           22310       34467    97659135   83  Linux
/dev/sda4           34468       38913    35712495   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bec52

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36483   293049666    b  W95 FAT32
----------------------------------------------------------------------

FSTAB ----------------------------------------------------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=542d5551-dbf8-4848-92f1-0830093b3173 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb4
UUID=3446178e-0879-4b1a-9681-d290ba80346e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
-----------------------------------------------------------------------

---

### Post by ASULutzy on 2008-05-22
Yes, to list terminal output use code tags.
[ CODE ] [ /CODE ]

In order to get the uuid of any given partition you can use the blkid command.
```
sudo blkid /dev/sda1
```

The UUID's shouldn't change just because it went from /dev/sda4 to /dev/sdb4.

You could just edit the comment line that says # /dev/sda4 to # /dev/sdb4 and that will give you peace of mind.

Just to make sure everything is in working order, try ```
swapon -s
``` and it will tell you where your swap is located also, ```
df -h
``` should show you where / is mounted from.

Hope this helps, welcome to the forums, and enjoy Ubuntu

---

