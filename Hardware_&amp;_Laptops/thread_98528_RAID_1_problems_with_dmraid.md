---
title: "RAID 1 problems with dmraid"
date: 2005-12-03
forum: Hardware &amp; Laptops
---

### Post by homersbrain on 2005-12-03
I have a Gigabyte mboard with the promise fake hardware RAID device built in connected to two 120GB drives in a mirror raid configuration. I boot from a separate drive (dual boot Ubuntu Breezy (K7) and XP) and use the raid for data storage only (vfat so xp can access it - its already full of valuable data).
I have installed dmraid in ubuntu and typing dmraid -r into a terminal reports:

/dev/hde: pdc, "pdc_cgfajhehg", mirror, ok, 234375000 sectors, data@ 0
/dev/hdg: pdc, "pdc_cgfajhehg", mirror, ok, 234375000 sectors, data@ 0

and

sudo dmraid -ay

gives:

RAID set "pdc_cgfajhehg" already active
RAID set "pdc_cgfajhehg1" already active

and ls /dev/mapper gives:

control  pdc_cgfajhehg  pdc_cgfajhehg1

so I thought all is well.

But how so I mount the drive?
I tried:

 sudo mount -t vfat -o users,owner,ro,umask=000 /dev/mapper/pdc_cgfajhehg /media/drive_f

but it reports:

mount: mount point /media/drive_f does not exist

What am I doing wrong? I tried creating a drive_f folder in /media but then it reports:

mount: /dev/mapper/pdc_cgfajhehg already mounted or /media/drive_f busy

Please help!

---

### Post by notetoself.net on 2008-04-14
did you find the solution (after four years)?  i have the same issue mounting some raid1 discs using dmraid.

---

