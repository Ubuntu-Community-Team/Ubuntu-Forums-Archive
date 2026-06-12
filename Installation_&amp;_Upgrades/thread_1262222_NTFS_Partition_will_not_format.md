---
title: "NTFS Partition will not format"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by xi_Slick_ix on 2009-09-09
Had a Windows XP Partition Semi-frag.  I've tried formatting it / deleting it several times and I am coming up with an error every time.  The HD is a 320 GB Seagate, and the Windows NTFS Partition is 80GB

```
GParted 0.4.5

Libparted 1.8.8
Format /dev/sda1 as fat32  00:00:25    ( ERROR )
     	
calibrate /dev/sda1  00:00:08    ( SUCCESS )
     	
path: /dev/sda1
start: 63
end: 167943509
size: 167943447 (80.08 GiB)
set partition type on /dev/sda1  00:00:09    ( ERROR )
libparted messages    ( INFO )
     	
Input/output error during write on /dev/sda

========================================
```

I was having trouble formatting the drive prior to this so I flashed me BIOS for curiosity's sake.  I also have an Ubuntu partition on the Drive, which has also been acting a bit sketchy.  I'm seriously considering just trying to write 0's to the drive.  I know I used a slightly dated version of G-Parted live CD, but I assumed this was close enough.

Any Suggestions?

---

