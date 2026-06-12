---
title: "Extra Drives Not Showing"
date: 2008-09-14
forum: Hardware
---

### Post by ibethebear on 2008-09-14
Hi All
I have recently converted my old computer to 100% Ubuntu 8.04 and it works great.

However, I have 3 80 gig hard drives in the system. The extra 2 drives do not show up and i cannot figure out how to access them.

When I installed Ubuntu, the installer saw all drives, but after installation, they are not there.

Any help would be greatly appreciated
Ibethebear

---

### Post by ibethebear on 2008-09-14
By the way al 3 drives are set up witht he ext3 Filesystem


Ibethebear

---

### Post by Casper Hansen on 2008-09-14
I'm not sure if this will help, but try to run a fdisk -l command in the terminal and paste the output.

---

### Post by ibethebear on 2008-09-14
here is the fdisk output
---------------------------------------

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68e74481

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161   83  Linux

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe87fe87

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         973     7815591   82  Linux swap / Solaris
/dev/sdb2             974        9964    72220207+  83  Linux

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1231

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         973     7815591   82  Linux swap / Solaris
/dev/sdc2             974        9729    70332570   83  Linux

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x385f8db3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               2       48641   390700800    f  W95 Ext'd (LBA)
/dev/sdd5               2       48641   390700768+   7  HPFS/NTFS

--------------------------------------------------
Thanks ahead for any help

by the way my external usb drive works fine.

ibethebear

---

### Post by Yellow Pasque on 2008-09-14
Please post output from:
```
cat /etc/fstab
blkid

```

---

### Post by markbuntu on 2008-09-14
You could be having a permissions issue with these drives. If you do not have any permission, they will not even show up. Though the default install should not have done this to you.

Look in System/Administration/Authorizations and see if the drives are there and what permissions they are under.

---

### Post by Casper Hansen on 2008-09-15
> **ibethebear said:**
> here is the fdisk output
---------------------------------------

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68e74481

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161   83  Linux

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe87fe87

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         973     7815591   82  Linux swap / Solaris
/dev/sdb2             974        9964    72220207+  83  Linux

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1231

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         973     7815591   82  Linux swap / Solaris
/dev/sdc2             974        9729    70332570   83  Linux

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x385f8db3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               2       48641   390700800    f  W95 Ext'd (LBA)
/dev/sdd5               2       48641   390700768+   7  HPFS/NTFS

--------------------------------------------------
Thanks ahead for any help

by the way my external usb drive works fine.

ibethebear

I also think it's a permission issue, because the computer detects the drives.

---

### Post by barrem01 on 2008-09-15
But what would the problem be if Ubuntu could not detect the drives (but they were recognized by bios)?

I lost a drive in an upgrade from a very old ubuntu (6.xx?)

[http://ubuntuforums.org/showthread.php?p=5790340](http://ubuntuforums.org/showthread.php?p=5790340)

Thanks,

 - Mike

---

### Post by ibethebear on 2008-09-21
here is the output from the earlier request

Thanks
Ibethebear

desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3f07fa91-438b-4f5e-bd32-cc5a20fa9cb4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8b1fb53a-576c-40fd-b2e7-cf5a20e40d7f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by ibethebear on 2008-09-21
i have checked "System/Administration/Authorizations".

The drives don't show specifically there, but under the "Storage"' subtitle, everything has access.

Ibethebear

---

### Post by Bucky Ball on 2008-09-21
They don't show in 'Places' drop down menu as simply '80Gb'? May need to mount them.

---

