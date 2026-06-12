---
title: "xp ntfs 8.10 install partition problem"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by ubuntumaybe on 2009-05-14
Hi,

I have an old desktop that has xp with ntfs. I have tried to install 8.10 using the live cd but it will not let me resize the windows ntfs partition. I have a 40 gig hd with 16 free.

---

### Post by dstew on 2009-05-14
It is possible that the ntfs partition has bad sectors, or has files in the area you tried to shrink. Run the Windows chkdsk program from the Windows command line (the Run menu) with the /f /r switches:```
chkdsk c: /f /r
```See if it says you have bad sectors. Then, defragment the drive with the Windows Disk Defragmenter (I think it is in the Accessories --> System menu). If you see a green "immovable file" at the end of the partition on the defragmentation analysis display, this might be the Windows "Page File" (sort of like the swap partition in Linux). You can get rid of this from the Windows memory magagement menu, which I think might be in My Computer --> Advanced, or something like that.

If bad sectors are the problem, sometimes even if chkdsk runs OK gparted will not touch the partition. You can shrink the partition in two steps using command line tools ntfsresize and fdisk. If you have a [gparted live CD]("http://gparted.sourceforge.net/livecd.php"), these tools can be accessed via the command line on that disk.

---

### Post by ubuntumaybe on 2009-05-20
> **dstew said:**
> It is possible that the ntfs partition has bad sectors, or has files in the area you tried to shrink. Run the Windows chkdsk program from the Windows command line (the Run menu) with the /f /r switches:```
chkdsk c: /f /r
```See if it says you have bad sectors. Then, defragment the drive with the Windows Disk Defragmenter (I think it is in the Accessories --> System menu). If you see a green "immovable file" at the end of the partition on the defragmentation analysis display, this might be the Windows "Page File" (sort of like the swap partition in Linux). You can get rid of this from the Windows memory magagement menu, which I think might be in My Computer --> Advanced, or something like that.

If bad sectors are the problem, sometimes even if chkdsk runs OK gparted will not touch the partition. You can shrink the partition in two steps using command line tools ntfsresize and fdisk. If you have a [gparted live CD]("http://gparted.sourceforge.net/livecd.php"), these tools can be accessed via the command line on that disk.


I took your advice. First I defraged the harddrive then I loaded knoppix live and used ntfsresize with /b and/s to resize the harddrive. Windows now recognizes the new drive size but when I tried to install ubuntu 8.04 it will not recognize the smaller windows partition and tells me that there are 2 bad sectors on the harddrive. I have tried gparted and qtparted. Thanks.

---

### Post by dstew on 2009-05-20
If you use ntfsrezise, the *file system* is shrunken but not the *partition*. You now need to shrink the partition. The way I have done this is to use fdisk on a linux command line. Fdisk modifies partition tables but not file systems. Gparted will not touch a partition that has bad sectors, but fdisk will.

You would use fdisk to delete the partition, then create a new one that is just big enough to contain the now shrunken ntfs file system. It is important to create the new partition starting at the same sector as the old one. The command fdisk -l will show where the partition starts. You need to remember the sector number, or write it down, because when you create the new partition you need to tell it where to start.

It is important to be sure the new partition is big enough to contain the shrunken ntfs file system. If the new partition it too small, the system might not boot. See this [fdisk How-To]("http://tldp.org/HOWTO/Partition/fdisk_partitioning.html"). If you accidentally make it too small, you can just use fdisk and try again. As always, make sure you have backed up your vital data before using fdisk this way.

---

