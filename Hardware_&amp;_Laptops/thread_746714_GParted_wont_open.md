---
title: "GParted wont open"
date: 2008-04-05
forum: Hardware &amp; Laptops
---

### Post by rectec794613 on 2008-04-05
Hi guys, I recently changed my iPod partition to Fat16 because I heard that Fat16 is better for 1GB hard-disks/iPods than Fat32 filesystems. I disconnected my iPod, (don't ask why)
And I later connected it back and it wouldn't show up in file browser *or* GtkPod.
I think this is because Ubuntu doesn't detect Fat16 filesystems. Now to the *real* problem. When I open GParted it closes as soon as it opens. When I open it through the terminal it shows this error: > robert@Ubuntu:~$ sudo gparted
[sudo] password for robert:
======================
libparted : 1.7.1
======================
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 - unrecognised disk label.
Segmentation fault (core dumped)
Can anyone help me out with this plz? Thanks in advance.:)

---

### Post by rectec794613 on 2008-04-08
Same thing with my CD drive now too!
PLEASE HELP!!!:(

---

### Post by Sef on 2008-04-08
> I think this is because Ubuntu doesn't detect Fat16 filesystems

Linux can [detect FAT 16]("http://en.wikipedia.org/wiki/Comparison_of_file_systems") file systems.  (See OS Support.)

From [Microsoft]("http://www.microsoft.com/technet/prodtechnol/windows2000serv/reskit/prork/prdf_fls_tllv.mspx?mfr=true"):

> FAT16 is not recommended for volumes larger than 511 MB; when relatively small files are placed on a FAT16 volume, FAT16 manages disk space inefficiently

---

### Post by rectec794613 on 2008-04-22
Well I solved it myself.
I had to disconnect the iPod to use GParted.
And i got the disk working to, I just booted off the live CD.

---

