---
title: "Auto Mounting Issues"
date: 2008-09-28
forum: Hardware
---

### Post by Koloth on 2008-09-28
Hi All,

Distribution: Kubuntu
USB Hard Drives: Master and Rig 1 using NTFS-3G

I'm having some trouble mounting my two USB External hard drives automatically on boot.

They seem to mount fine manually:
```

sudo mount -t ntfs-3g /dev/sdf1 /mnt/master
sudo mount -t ntfs-3g /dev/sdg1 /mnt/rig1

```

My /etc/fstab file
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=94befc7c-31d1-4634-9e08-b1934bb5bce4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1a1efa39-6480-415f-8732-3fa08b9f5c38 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# Master 1000gb drive
UUID=7668419768415751 /mnt/master ntfs-3g noauto,user,exec,umask=007,gid=1000 0 0 

# Rig 1 500gb drive
UUID=D24C314E4C312F1B /mnt/rig1 ntfs-3g noauto,user,exec,umask=007,gid=1000 0 0

```

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9727    78132096    7  HPFS/NTFS
/dev/sda2           18648       19457     6506325    7  HPFS/NTFS
/dev/sda3            9728       18647    71649900    5  Extended
/dev/sda5           18399       18647     2000092+  82  Linux swap / Solaris
/dev/sda6            9728       18397    69641712   83  Linux

Partition table entries are not in disk order

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8726a0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       60801   488384001    7  HPFS/NTFS

```

I would appreciate any help. Thanks.

---

### Post by Koloth on 2008-09-29
Bump.

I'm really out of ideas on this one.  So it would be fantastic if someone could spare the time to help.  Thanks.

---

