---
title: "fstab what am I doing wrong"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by renihanc on 2009-07-16
can't access 2nd HD  heres what i got

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=1788b772-47b4-477c-aa1d-b4120c9d0d2e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=12866ed1-bfc2-4535-a14f-61b07a9db708 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1    /media/stgdrv    ext3,defaults        0    0


heres my fdisk if that helps

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x79627962

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sda2           16709       30401   109989022+   5  Extended
/dev/sda5           16709       29839   105474726   83  Linux
/dev/sda6           29840       30401     4514233+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux


thanks in advance

---

### Post by merlinus on 2009-07-16
Why are you double posting?  I responded to your initial one a few minutes ago.

---

### Post by renihanc on 2009-07-16
my mistake, didn't mean to,,,, sorry bout that

---

