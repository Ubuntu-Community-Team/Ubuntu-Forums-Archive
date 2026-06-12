---
title: "can someone help with mounting 2nd HD"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by renihanc on 2009-07-16
this is my FSTAB can you tell me what i'm doing wrong. system loads ok, but won't allow me to mount when i go click on drive.




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





also heres my fdisk info


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


thanks alot,

Chris

---

### Post by merlinus on 2009-07-16
If the drive you are referring to is sdb1, then:

/dev/sdb1    /media/stgdrv ext3 relatime 0 1

may work.

---

### Post by renihanc on 2009-07-16
yes it's the 2nd HD..... what does relatime do ??? and why do i need the 1 for pass ?

thanks

---

### Post by merlinus on 2009-07-16
Does it work?  That's the important question, no?

---

### Post by renihanc on 2009-07-16
no , it say can not mount volume.

any other suggestions would be appreciated.

---

### Post by merlinus on 2009-07-16
Try this in a terminal:

```
sudo mount -t ext3 /dev/sdb1 /media/stgdrv
```If that works, then

```
gksu nautilus
```Navigate to the mountpoint, rightclick, properties, permissions.

And just to be sure, you already created the mountpoint?

---

