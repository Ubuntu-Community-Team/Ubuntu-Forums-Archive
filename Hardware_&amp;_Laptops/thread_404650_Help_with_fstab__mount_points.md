---
title: "Help with fstab / mount points"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by Iceni on 2007-04-08
Hi. 

My mount settings are acting weird on me. I run Feisty beta, completely updated, with ntfs-3g and a few sata disks + 1 ide. The IDE disk won't even show up in file manager, and a random number of the sata disks will not mount untill I do it manually, but then I have only read access. I looked around in my fstab and compared it to the fdisk -l list, a lot of things looks plain wrong. 

My idea is to simple correct the fstab list according to the fdisk output, but after trying once and failing I'm afraid to break something. Could anyone be bothered to take a look or tell my why my idea is wrong? Thanks in advance!

*fdisk -l*
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21150   169887343+   7  HPFS/NTFS
/dev/sda2           21151       24321    25471057+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38536   309540388+  83  Linux
/dev/sdb2           38537       38913     3028252+   5  Extended
/dev/sdb5           38537       38913     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       17653   141797691    7  HPFS/NTFS
/dev/sdd2           17654       30401   102398310    7  HPFS/NTFS

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       30401   244196001    7  HPFS/NTFS

```

*Fstab*
```
proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=a0f7594d-502b-494e-b1b5-041cafd4c921 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=40c75d2d-713e-408c-8f77-85eea121f861 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sdc1 /media/River ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb2 /media/Ohabu ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb1 /media/Habu ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/Graendal ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sde1 /media/Serenity ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdd2 /media/NSGP ntfs-3g defaults, 0 0
```

---

### Post by kidders on 2007-04-09
Hi there,

There's no need to be *too* afraid of making mistakes with /etc/fstab. Granted, screwing up is irritating, but any Linux boot CD can rescue you, as long as you know how to find where your root filesystem lives.

The basic rules are ...
[LIST]
[*]_Make small changes._ Don't combine revisions to /etc/fstab with any other system modifications (in one go), unless you feel confident with what you're doing.
[*]If you mess up, and your system becomes unbootable, rescue yourself by booting with a CD, mounting your root filesystem, and tweaking (or maybe restoring) /etc/fstab. Keeping backups can be handy for this purpose.
[*]When booting from CDs, don't take it for granted that what the CD's environment calls /dev/sda will be the same thing your HDD install calls /dev/sda. Occasionally, device names can move around, so always check![/LIST]The one observation I would make about your system is that there are an awful lot of NTFS filesystems on it. Afaik the ntfs-3g driver is _not_ reliable ... making use of it more than once on the same system multiplies up the risk of a failure.

If you want, you could practice rescuing yourself, so you're sure you know how to do it, in the event something goes pear-shaped. Find a Linux CD, boot with it, identify & mount your root filesystem, open its /etc/fstab & take a look. If you can do that, you should feel free to make any changes you like, without fear of failing.

I hope that helps.

---

### Post by Iceni on 2007-04-10
Thanks a lot! I actually got things running pretty nicely after some reading and tweaking. 

Thanks for the tip about the ntfs disks, I really don't need them to be ntfs as I set up a dualboot when I installed ubuntu but never booted into windows again:)

---

