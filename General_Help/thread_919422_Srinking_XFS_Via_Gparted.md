---
title: "Srinking XFS Via Gparted"
date: 2008-09-14
forum: General Help
---

### Post by Gannon8 on 2008-09-14
Hi. I have a SystemRescueCD ([http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)) with gparted on it. The gparted website claims you can shrink an XFS volume via it's copy function:> [3] Although it's not possible to shrink an xfs file system directly, you can shrink it using GParted's copy functionality. so I booted from that, and tried copying the partition to an external hard drive. I get an error saying the partition I am making is smaller than the partition I am copying. I have enough space for files. Any other way to shrink an XFS filesystem?

---

### Post by Pro-reason on 2008-09-14
XFS partitions [cannot be shrunk]("http://en.wikipedia.org/wiki/XFS#Disadvantages").

> **Gannon8 said:**
>  I get an error saying the partition I am making is smaller than the partition I am copying.

How much smaller?  If it is only a little smaller, then you could squeeze it in by using compression.

Use a command somewhat like the following:

```

sudo tar -cv /media/indrive | lzop > /media/outdrive/indrive-backup.tar.lzo

```

---

### Post by Gannon8 on 2008-09-14
I have enough space for the files, with some free space left over.

---

