---
title: "WD Passport 250GB - device busy or in use when mkfs.xfs"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by xover on 2008-01-04
fdisk -l
#
   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001   83  Linux
#
umount /dev/sdd1
umount: /dev/sdd1: not mounted
#
fuser -m /dev/sdd1
#
mkfs.xfs /dev/sdd1
mkfs.xfs: cannot open /dev/sdd1: Device or resource busy

Any help much appreciated, im on my fourth day of searching now. If you don't know can you tell me where to buy a shotgun as this is destroying my soul.

I had the same issue with a Seagate 500GB disc.

I'm considering upgrading to an A4 pad and a pencil.

Regards

Rich

---

### Post by njparton on 2008-01-04
Are you using windows too?

Unmount it from windows before you shutdown and reboot into ubuntu.

If not, post back.  I'm thinking NTFS has locked the drive?

---

### Post by xover on 2008-01-04
yoyo, 

thanks for the reply.

I deleted the partition, its running on linux partition as you can see from fdisk.

Seems to be related to the caddy, as the otehr caddies i have are very basic and all work. i cant remove the disc though as WD passports are sealed.

---

