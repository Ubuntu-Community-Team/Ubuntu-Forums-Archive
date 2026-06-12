---
title: "need help accessing extended drive"
date: 2009-02-24
forum: Hardware
---

### Post by Sgtblades275 on 2009-02-24
I just installed Ubuntu 8.10 Intrepid Ibex a few days ago and I pretty much ain't got much of an idea of what I'm doing. I've looked through the forums and googled a lot but I can't seem to find help for what I got.

When I installed Ubuntu I just hit the guided partition thing (installed from boot cd) and it partitioned the drive that has all my stuff on it and now all I can do is mount the 1st part which is the filesystem. It doesn't allow me to mount the extended.
Here's my drives:

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        9726    78083932+   7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2bb2d048

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       35726   286969063+  83  Linux
/dev/sdb2           35727       36481     6064537+   5  Extended
/dev/sdb5           35727       36481     6064506   82  Linux swap / Solaris

sdb1 is what I mount and when I explore it all there is is the Ubuntu files. When it was partitioned by the guided partition, Ubuntu was still able to get into My Documents from Windows and that is the only reason I can see why it uses sda as the drive to write on because I chose to copy My Doc stuff into /home/(name).
Also, when I mount the filesystem (sdb1) it says there is about 250gb of free space, but when I go into Windows I still see all the stuff there and which there is only about 60gb of free space.
I'm just trying to give enough information on my circumstance as I can so I can get into my freaking drive.

---

### Post by Sgtblades275 on 2009-02-25
a day... please. anyone. I could really use some help SOON. thanks...

---

