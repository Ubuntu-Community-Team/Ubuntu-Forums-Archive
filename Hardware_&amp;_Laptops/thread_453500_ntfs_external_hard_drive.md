---
title: "ntfs external hard drive"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by gmcm1979 on 2007-05-24
i have recently bought an external enclosure and added a 250GB sata hard drive, i have formatted the drive in windows as ntfs. i then mounted it in linux with kdisk, i can now view the disk but i cant read or write to it. i have also downloaded ntfs-3g from the repositories.

---

### Post by IntuitiveNipple on 2007-05-24
If you check **/etc/fstab** you may find it is being mounted by the read-only file-system driver, ntfs.

If so, unmount the volume, then change "ntfs" to be "ntfs-3g" in /etc/fstab.

There's a safer way to this from a GUI - install **ntfs3g-config**. It is added to the Applications-> System Tools menu as **NTFS Configuration Tool**.

---

### Post by gmcm1979 on 2007-05-24
i have tried to edit fstab but cant identify which drive is my external hard drive, i have 2 internal hard drives already 1 has windows(80gb) and the other ubuntu (250gb sata)

Here is the output of my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=4c86e871-fc04-4997-bb67-2a345ebd26df / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=684802f9-f68f-45a3-96e3-e3b18ffd702d none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

# /dev/hda1 -- converted during upgrade to edgy
UUID=CE6C8A416C8A2475 /windows ntfs-3g nls=utf8,umask=000 0 0
/dev/fd0 /media/fd0 auto rw,user,noauto 0 0

---

### Post by gmcm1979 on 2007-05-24
here is output of fdisk

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30023   241159716   83  Linux
/dev/sda2           30024       30401     3036285    5  Extended
/dev/sda5           30024       30401     3036253+  82  Linux swap / Solaris

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           2       30401   244188000    5  Extended
/dev/sdb5               2       30401   244187968+   7  HPFS/NTFS

---

### Post by IntuitiveNipple on 2007-05-24
Based on the fact you say the drive is a 250GB SATA  NTFS it looks like it is /dev/sdb.

---

### Post by gmcm1979 on 2007-05-25
i think that might my internal hard drive as they are identical drives. i think it might be /dev/sdb5 although im not too sure if this it and what to do.

---

