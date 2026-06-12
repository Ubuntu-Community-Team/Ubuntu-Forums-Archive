---
title: "can't see hard disks"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by vagamente on 2005-06-06
That's a question from a newbbie...
Hi all.. i've jst installd ubuntu on my pc.... i've got 4 hd on my pc and in 1 of them is installed win xp home ed sp2...  ubuntu is installed in one partiton of first hd... it works great but i can't see and access to other 3 hd... how can i?
thanx

---

### Post by codejunkie on 2005-06-06
[http://www.ubuntulinux.org/wiki/AutomaticallyMountMSWindowsPartitions/](http://www.ubuntulinux.org/wiki/AutomaticallyMountMSWindowsPartitions/)
also fair warning from someone that has went thrue this make sure and never write files to a ntfs partition only read from it, or it will damage the windows partition hope this helps.

---

### Post by vagamente on 2005-06-06
Can't understand very much from the link above.... (i'm newbbie and italian...)... anyone can help me?

---

### Post by Alexander Kirillov on 2005-06-06
[QUOTE=vagamente]Can't understand very much from the link above.... (i'm newbbie and italian...)... anyone can help me?[/QUOTE]
 First, here is how disks are called in Linux:
First hd: /dev/hda
second hd: /dev/hdb
third hd: /dev/hdc
(you get the pattern, right?)

Usually each physical disk is "partitioned", i.e. divided into several logical disks. Each of them also has a name in Linux as follows:
First partition of first hd: /dev/hda1
Second partition of first hd: /dev/hda2
First partition of second hd: /dev/hdb1
etc

Now: if you already know which partitions you have on which disks, and what filesystem type you have, do the following. For example, assuming that you have one partition with NTFS filesystem on it on hd2, you can do the following:

1. Create directory which will show the files from this partition. Traditionally, it should be under /mnt or /media. E.g.: 
sudo mkdir /media/disk2

You only need to make it once

2. "mount" the disk, i.e. make the contents of the disk available, by typing 
sudo mount -t ntfs /dev/hdb1 /media/disk2
(for other partitions or other disks, repalce /dev/hdb1 by appropriate device name)

3. Now try to open location /media/disk2 in Nautilus. Do you see your files? If so, you can now make it so that this "mounting" is done automatically each time you boot your computer. Instructions here: 
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

4. For other disks/partitions, repeat the above steps.  Note: you need a separate directory in /media for each of the partitions.

Warning: ntfs filesystems can be read but not written to in Linux. Fat32 can be read and written to.

---

