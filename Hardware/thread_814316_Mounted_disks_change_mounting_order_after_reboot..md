---
title: "Mounted disks change mounting order after reboot."
date: 2008-05-31
forum: Hardware
---

### Post by Brutalix on 2008-05-31
I have my server running on an old athlon with 2 old promise controllers. I am also using the onboard storage controllers. My problem is that even if i mount the disks in fstab, something weird happens everytime i reboot. It changes the order of the mount, so the disk that was previously mounted as /mnt/dill now becomes /mnt/audiobooks etc. 
How can I prevent that for happening. 

I included the fstab and the Fdisk -l output, hope someone can figure it out, its a bit anoying, but i havent found any other posts with the same problem, so it might be due to my hardware?

Thanxx in advance.

Brut.

fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=2d976464-67ee-4f48-adf4-f62a627fce14 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda5
UUID=c83aede6-2768-4ae8-9afa-456c9591ee78 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdd1 /mnt/S-linux ext3
/dev/sdj1 /mnt/scifi ext2 rw,rw,nosuid,nodec,uhelper=hal 0 0
/dev/sdh1 /mnt/dill ext2 rw,rw,nosuid,nodev,uhelper=hal 0 0
/dev/sdi1 /mnt/dill2 ext2 rw,nosuid,nodev,uhelper=hal 0 0
/dev/sde1 /mnt/shortmovies ext2 rw,nosuid,nodev,uhelper=hal 0 0
/dev/sda1 /mnt/shortmoviesself ext2 rw,nosuid,nodev,uhelper=hal 0 0
/dev/sdg1 /mnt/movies ext2 rw,nosuid,nodev,uhelper=hal 0 0
/dev/sdc1 /mnt/dill3 ext2 rw,nosuid,nodev,uhelper=hal 0 0
/dev/sdb1 /mnt/disk-s ext2 rw,nosuid,nodev,uhelper=hal 0 0
/dev/sdd1 /mnt/Audiobooks-Music ext2 rw,nosuid,nodev,uhelper=hal 0 0
/dev/sdf1 /mnt/action ext2 rw,nosuid,nodev,uhelper=hal 0 0

FDISK -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1730a858

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea73db98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea73db9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001   83  Linux

Disk /dev/sdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3c2cbe6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       24792   199141708+  83  Linux

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b7e41

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       30401   244196001   83  Linux

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc617aa6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001   83  Linux

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea73db99

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       60801   488384001   83  Linux

Disk /dev/sdh: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x857b857b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       60801   488384001   83  Linux

Disk /dev/sdi: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92bb92bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *           1       60800   488375968+  83  Linux

Disk /dev/sdj: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001ccb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1       91201   732572001   83  Linux

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ce4c388

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19082   153276133+  83  Linux
/dev/hda2           19083       19457     3012187+   5  Extended
/dev/hda5           19083       19457     3012156   82  Linux swap / Solaris

Disk /dev/hdd: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28a40ed7

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       19930   160083968   83  Linux

---

### Post by Brutalix on 2008-06-06
bump...

---

### Post by thideras on 2008-06-06
Sorry I can't give a direct answer, but I know there is a way to mount them by a unique ID.  This would solve your problem, let me see if I can get a link.


EDIT:

[https://help.ubuntu.com/community/Fstab#head-23e9727b63cb51002693e91815e2b3e0171a4837](https://help.ubuntu.com/community/Fstab#head-23e9727b63cb51002693e91815e2b3e0171a4837)

```
sudo blkid
ls -l /dev/disk/by-uuid
```That should give you the UUID's, you can then edit your fstab to use that instead of /mnt/dill.

---

### Post by Brutalix on 2008-06-07
Thanks what you suggested worked perfectly.

Brut.

---

### Post by thideras on 2008-06-07
> **Brutalix said:**
> Thanks what you suggested worked perfectly.

Brut.Awesome, glad to hear it worked for you! :D

---

