---
title: "External hard drive slows down Ubuntu"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by Mantrasong on 2008-01-13
Hello, I just recently acquired a 250 GB (internal) hard drive, which I am keeping in an external USB enclosure. I formatted the drive to fat32, because I needed something that can be read on Windows, Linux, and Mac (especially the last two). It works fine on my Mac, however, when I mount it on Ubuntu and try to move data to and from it, Ubuntu slows way down. My mouse starts jumping, and it seems to have trouble opening new windows. The problem continues even after I've unmounted and disconnected the hard drive, and the only  way I've found to fix this is to reboot my computer. The slowdown doesn't actually start until after I start moving data to and from it, if I just mount it, it seems to be fine.

Needless to say, this is not my preferred way of handling this problem, and I wanted this to be a backup drive. Does anyone have any idea what could be wrong, and/or how to fix it?

---

### Post by twright on 2008-01-13
fat32 is a **very** bad file system, i would not recommend it on a drive that big as it was designed for drives no bigger than 10gb so it will quickly become corrupted

you could try creating a separate ext3 partition or using HFS+ and installing ubuntu support for that

---

### Post by Mantrasong on 2008-01-13
I was under the impression that Ubuntu only supports HFS+ read support, and (afaik) Mac does not support ext3. The reason I chose FAT32 was because it seems to be the only one supported with read/write between Linux and Mac, and the windows support was a nice addition. 

If there is an easy way to add support for HFS+ write support on ubuntu, or ext3 on mac, that would work, but until then I'm probably stuck with fat32. So is it the fact that ubuntu doesn't play nice with large fat32 partitions, or might there be something else wrong?

---

### Post by twright on 2008-01-13
you can make OSX support ntfs with ntfs-3g (the same thing that ubuntu uses) and i think you can get ubuntu to write HFS

or you can split it up into several smaller partitions

if you use fat32 it is very likely that the file system will get corrupted

---

### Post by sylv1 on 2008-04-04
I've got a similar problem:
I have a low quality external hard drive (160G), with 3 partitions on it: a 30G fat32, a 40G ext3 and the rest is an encrypted partition with LUKS (the filesystem is also ext3). When I transfer data to any partition, Ubuntu (Kubuntu, rather) becomes unusable (as if xorg was dying a painful death). CPU and  memory usage are both pretty low though (running "top" shows nothing wrong).
The data is read in big bursts (as seen from the disk access monitor of my gkrellms widget) and written continuously. A buffer gets filled in pretty quickly (presumably on the external drive). Could that be preventing some other processes from running properly?

I don't mind the data transfer being slow, as I know my drive is slow, but I don't want the whole system (in general nice and fast) to be slowed down. Any hint as to how to fix that?
Thanks

PS: I use Kubuntu 7.10

---

### Post by Mantrasong on 2008-04-05
The problem more or less resolved itself for me, and I'm not quite sure how it happened. As near as I can tell, its related to the other operating systems I used it on.  I found the problem tended to show up more when I didn't safely remove/eject the drive from somewhere else. I think when I went through all the OSes and made sure it had properly loaded and ejected from each of them, it started behaving better. I'm not entirely sure why this would make a difference, but it does seem to. 

I don't know if it needs to talk to other operating systems (though the fact that you have it formatted to FAT32 suggests to me that you do), but that might be a step to try if you can.

If that doesn't help, I can see if I can find the logs to look at to trace the problem but I'm mid-computer switch at the moment, and thus somewhat linux-less.

---

