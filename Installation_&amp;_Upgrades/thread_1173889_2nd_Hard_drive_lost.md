---
title: "2nd Hard drive lost"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by rickprice on 2009-05-30
I have a machine with two hard drives. Initially I had a dual boot system, and have recently upgraded to Ubuntu 9.04 with this setup. All was fine at this point but the system was a little slow and I was not using windows at all, so I decided to clean install Ubuntu from CD.

I therefore re-formatted the primary drive and installed Ubuntu without problems - except that it does not see my other drive at all.

Does anyone know how to tell it that it is there? Info as below:

richard@office-desktop:~$ sudo fdisk -l
[sudo] password for richard: 

[I]Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23947   192354246   83  Linux
/dev/sda2           23948       24321     3004155    5  Extended
/dev/sda5           23948       24321     3004123+  82  Linux swap / Solaris
richard@office-desktop:~$ 
richard@office-desktop:~$ 

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=01f97f46-04bb-47d1-b5db-d6a0c49c2414 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=238e422f-5aad-4298-b9fd-838f1c1f8401 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/I]
[I]
Many thanks for the advice,

Rick


[/I]

---

