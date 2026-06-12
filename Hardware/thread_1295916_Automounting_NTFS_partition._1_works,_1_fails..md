---
title: "Automounting NTFS partition. 1 works, 1 fails."
date: 2009-10-20
forum: Hardware
---

### Post by Ubuntiac on 2009-10-20
Hi there,

I'm having a rather strange problem. I have an ntfs partition on a sata drive that:

1. Works fine if there's nothing in fstab and I click on it in the file manager, but
2. If I try to automount it with fstab the drive appears, still unmounted. Clicking on it returns: "mount:only root can mount /dev/sda1 on media/tb"

My other ntfs partition automounts fine on another (IDE) drive.

Fstab is:
```
proc                                       /proc          proc         defaults               0  0  
# / was on /dev/sdb5 during installation
UUID=12a7b580-f897-49d3-9de8-61c25050a86e  /              ext4         errors=remount-ro      0  1  
# swap was on /dev/sdb2 during installation
UUID=c2040270-0c2a-42b1-b268-2b10201269cb  none           swap         sw                     0  0  
/dev/scd1                                  /media/cdrom2  udf,iso9660  user,noauto,exec,utf8  0  0  
/dev/sdb1                                  /media/jaunty  ext3         errors=remount-ro      0  0  
/dev/sdb3                                  /media/xp      ntfs         defaults               0  0  
/dev/sda1                                  /media/tb      ntfs         defaults,auto          0  0  
```

[list]
[*]I get the same without "auto"
[*]With "defaults,user" I get "Unprivileged user can not mount NTFS block devices using the external FUSE library. Either mount the volume as root, or rebuild ntfs-3g with integrated fuse support and make it setuid root."
[/list]

sudo fdisk -l returns:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      182401  1465136001    7  HPFS/NTFS
/dev/sda4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdebf17c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9848    79104028+  83  Linux
/dev/sdb2           11474       12744    10209307+  82  Linux swap / Solaris
/dev/sdb3   *       12745       24321    92992252+   7  HPFS/NTFS
/dev/sdb4            9849       11473    13052812+   5  Extended
/dev/sdb5            9849       11473    13052781   83  Linux

Partition table entries are not in disk order

```

Any ideas anyone? Thanks!

---

