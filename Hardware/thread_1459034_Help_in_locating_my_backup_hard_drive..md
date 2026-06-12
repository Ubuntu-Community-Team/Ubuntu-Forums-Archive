---
title: "Help in locating my backup hard drive."
date: 2010-04-20
forum: Hardware
---

### Post by Ulykan on 2010-04-20
Hi all.  I just moved in from PCLinuxOS and am having trouble finding(seeing) my second or backup hard drive.  When installing KUbuntu I identified that drive as /usr and under PCLinux it showed in Dolphin.  In KUbuntu I'm not able to locate it.  Using Krusader I can see it under "disks" but of course I can't access it.  Can someone guide me on locating this drive?  It is critical that I see this drive and am able to access it as all of my archived files are there.  Thanks in advance.

Bob

---

### Post by Fafler on 2010-04-21
Open a terminal and type
```
sudo fdisk -l
```
It will list all available drives and partitions on your system. Figure out which is the right one, eg. /dev/sdb2, and mount it with
```
sudo mount /dev/INSERTDEVICENAMEHERE /mnt
```

Your files are now available under /mnt

---

