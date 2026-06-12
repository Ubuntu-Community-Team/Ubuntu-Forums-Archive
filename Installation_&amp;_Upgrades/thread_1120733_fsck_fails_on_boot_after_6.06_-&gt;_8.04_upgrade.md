---
title: "fsck fails on boot after 6.06 -&gt; 8.04 upgrade"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by niller23 on 2009-04-09
Hi

My upgrade to 8.04 failed, but I managed to get the system up and running after a lot of googling and playing around with dpkg and apt.

I have one problem left. fsck fails on boot with the following message:
```
Log of fsck -C -R -A -a 
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Device or resource busy while trying to open /dev/sdb6
Filesystem mounted or opened exclusively by another program?
fsck.ext3: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
fsck died with exit status 8

```

I am using LVM, but not for these two partitions. A manual check with fsck gives the same errors, but if /dev/sdXX is replaced with /dev/mapper/sdXX, everything works fine.

Are there any suggestions of what to do to make fsck happy?

I have attached the content of fstab and the output from blkid:

/etc/stab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/Ubuntu-root -- converted during upgrade to edgy
UUID=8732a334-620a-4f18-b3e0-622dd7c6d3af / ext3 defaults,errors=remount-ro 0 1
# /dev/hdc5 -- converted during upgrade to edgy
UUID=b1ed8b79-c5c5-4465-aca5-dc3d2fab49a1 /boot ext3 defaults 0 2
# /dev/mapper/Ubuntu-swap_1 -- converted during upgrade to edgy
UUID=bc73a585-5be2-481e-835d-557c6558bf7a none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# /dev/hde6 -- converted during upgrade to edgy
UUID=bcb00688-e349-4248-9895-448d14e0e5e6 /backup ext3 defaults 0 1

```

blkid
```
/dev/mapper/Ubuntu-swap_1: TYPE="swap" UUID="bc73a585-5be2-481e-835d-557c6558bf7a" 
/dev/mapper/Ubuntu-root: UUID="8732a334-620a-4f18-b3e0-622dd7c6d3af" TYPE="ext3" 
/dev/evms/lvm2/Ubuntu/swap_1: TYPE="swap" UUID="bc73a585-5be2-481e-835d-557c6558bf7a" 
/dev/evms/lvm2/Ubuntu/root: UUID="8732a334-620a-4f18-b3e0-622dd7c6d3af" TYPE="ext3" 
/dev/mapper/sdb1: UUID="6c987128-a629-4925-ab8f-3b1c5e03dfe8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/lvm2|Ubuntu|swap_1: TYPE="swap" UUID="bc73a585-5be2-481e-835d-557c6558bf7a" 
/dev/sda5: UUID="b1ed8b79-c5c5-4465-aca5-dc3d2fab49a1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="Z41ScP-ag2D-1Jln-NZun-PPqP-kDnv-PbM52t" TYPE="lvm2pv" 
/dev/sdb1: UUID="6c987128-a629-4925-ab8f-3b1c5e03dfe8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="bcb00688-e349-4248-9895-448d14e0e5e6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/sda6: UUID="Z41ScP-ag2D-1Jln-NZun-PPqP-kDnv-PbM52t" TYPE="lvm2pv" 
/dev/mapper/sda5: UUID="b1ed8b79-c5c5-4465-aca5-dc3d2fab49a1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/sdb6: UUID="bcb00688-e349-4248-9895-448d14e0e5e6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/lvm2|Ubuntu|root: UUID="8732a334-620a-4f18-b3e0-622dd7c6d3af" TYPE="ext3" 

```

---

