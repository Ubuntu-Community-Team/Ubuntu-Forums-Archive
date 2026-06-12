---
title: "ext2 or fat32?"
date: 2005-10-26
forum: Hardware &amp; Laptops
---

### Post by Adrian on 2005-10-26
Hi!

I have a brand new 160gb drive, and I want to share it between a linux installation and a windows installation.

My first thought was to use the FAT32 file system, but then I discovered this:
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
It is an ext2 driver for Windows XP, and I think it looks very promising.

1. Has anyone tried it? Does it work? I will have a lot of important data on that drive, so I don't want to take any chances.

My main problem with FAT32 is its inefficiency due to heavy internal fragmentation. Everyone is telling me NOT to use FAT32 for large partitions (>32gb). This leads me to my second question:

2. Is it a good idea to force the cluster size to be smaller than recommended to avoid internal fragmentation? The problem with this is that some windows programs seem to have problems when the total amount of clusters exceeds 4.1 million. I will only use my windows install for music software, so I doubt this will be a problem in windows. However, I don't know about Linux...

---

### Post by sailor420 on 2005-10-26
I'm using that software on my dual-boot laptop.

It works OK. My problem with it is it's method of assigning drive letters. It comes with a little app that you run from the Windows control panel and tell it which drive (C:\, D:\, etc) is EXT2/3. That would work fine, except that my drive that I need both OSs to access is a USB drive, and everytime I remove it and plug it back in, it is no longer recognized at that particular drive letter, and I have to go in and add *another* drive letter for it. It's quite annoying, to the point that I just don't even use it anymore.

If your drive was internal, this probably wouldnt be a problem, and this would work fine :)

---

### Post by Kyral on 2005-10-26
I'm old-fashioned and I KNOW that FAT32 works. Defrag can take care of disk fragmentation :D

---

### Post by Adrian on 2005-10-28
Thanks both of you for your replies.

I agree that FAT32 seems to be a more secure choice. However, the internal fragmentation bothers me, and it's not something that a defrag tool can take care of (as opposed to external fragmentation). Basically it means that if every cluster has a size of 32k, files that just are a couple of bytes will use 32k on the disk. Consequently, a file that is 33k will in fact use 64k disk space and so on. For smaller disks, this is no problem because the cluster size depends on the size of the partition.

I installed the ext2 windows driver and it seems to work flawlessly so far. It's very fast too, so I can definitely recommend it.

---

### Post by CurlyChris on 2005-10-28
[QUOTE=Kyral]I'm old-fashioned and I KNOW that FAT32 works. Defrag can take care of disk fragmentation :D[/QUOTE]

Feel slightly silly asking this, but you never know.........

Given that I now spend 80-90% of my time in Ubuntu, is there a utility that will defrag my FAT32 (Windows) partition from Breezy?  (I'm never running Windows long enough to fully defrag it!)

Thanks

Chris

---

### Post by Kyral on 2005-10-28
Maybe the dosfsck tool.. I think you have to install the dosfstools package for it

---

### Post by CurlyChris on 2005-10-28
I'll check it out, thanks!

Chris

---

