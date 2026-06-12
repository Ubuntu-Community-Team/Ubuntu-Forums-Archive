---
title: "8GB usb stick, only 5.7GB free space"
date: 2009-04-05
forum: Hardware
---

### Post by Sealbhach on 2009-04-05
I have this puzzling thing with my 8GB memory stick. When I open it in Nautilus it says I have zero items in there (correct) but there is only 5.7GB free space.

Furthermore, when I look at /dev/sdb in Gparted,  it says I have 1.82GB used. Gparted won't let me re-format the USB stick either... I'm using Jaunty Beta.

---

### Post by vanadium on 2009-04-05
Check the file system. There are probably lost clusters, i.e. remainders of previous files that are not referred to from within the file directories.

```

sudo umount /dev/sdb1
sudo fsck -a /dev/sdb1

```

---

### Post by Sealbhach on 2009-04-05
Thanks. That reclaimed some files.

However, I still get this when I do that:

```
fsck 1.41.4 (27-Jan-2009)
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
 1:58/00, 90:fa/00, 91:fc/00, 92:31/00, 93:c0/00, 94:8e/00, 95:d0/00
  , 96:bc/00, 97:b4/00, 98:7b/00, 99:06/00, 100:57/00, 101:8e/00, 102:c0/00
  , 103:b9/00, 104:08/00, 106:bf/00, 107:b4/00, 108:7b/00, 109:f3/00
................................(many many of these)
504:d4/00, 505:5b/00, 506:e5/00, 508:7f/00
  Not automatically fixing this.
/dev/sdb1: 4 files, 6/244930 clusters

```

I've been using this USB as a bootup disk with Unetbootin. 

I'd really like to just reformat the whole thing with Gparted, but it won't allow me to.

.

---

### Post by vanadium on 2009-04-05
Once the drive is unmounted, you should be able to reformat it. From within gparted, you can unmount the partition by right-clicking on it. After that, other options in the right-click menu (among others "format") will become available.

---

### Post by Sealbhach on 2009-04-05
Thank you, yes. I hadn't unmounted it. 

Thanks for the help.

.

---

