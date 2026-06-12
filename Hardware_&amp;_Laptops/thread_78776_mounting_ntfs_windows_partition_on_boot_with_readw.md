---
title: "mounting ntfs windows partition on boot with read/write"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by eschickel on 2005-10-18
after searching i found this: [http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

the partition is ntfs.  those directions only tell me how to make it read only.  i would like it to be read/write.  can anyone help me out?

thanks,
evan

---

### Post by aysiu on 2005-10-18
NTFS is generally read-only in Linux. However, there are experimental programs like this that allow you to write to NTFS:

[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

---

### Post by eschickel on 2005-10-18
i'm a new user of linux, but definitely not new to computers.  is it pretty safe to use that program?  it doesn't list ubuntu as a supported version of linux. :confused:

---

### Post by aysiu on 2005-10-18
I don't know. As I said before, Linux write support for NTFS is experimental. If you must read/write, create a FAT32 partition to share files between the OSes. In all fairness, Windows doesn't write to EXT3, either.

---

### Post by eschickel on 2005-10-19
alright, i'll have to make do.  thanks for your help. :D

---

### Post by jtopping on 2005-10-21
in gentoo, the kernel had built-in write support for ntfs...i never used it too much but in what i did use it worked well...:KS

---

### Post by arcanistherogue on 2005-10-21
Wow, I must say that Fat32 partition is a good Idea.  I should add a 10 GB hard drive for that.

How do I partition it, using windows or the linux partitioner?   and If I use the linux partitioner, how will it come up when I boot windows?

---

### Post by Kyral on 2005-10-21
1) Get GParted or QtParted for the FAT32 issue

2) Writing to NTFS from Linux WILL corrupt the NTFS system. Don't try it yet

---

### Post by AlexandertheGreat on 2005-10-22
Please don't try to write to a ntfs partition. This is not safe. :oops:

I use a fat32 partition in order to exchange files in deferent operating systems. 

It works fine. Do the same and you won't have any problems with lost data.

---

### Post by eMCee on 2006-04-14
I created a FAT32 partition but i can't write  :???: 
"/media/hda7...esktop.ini" cannot be deleted because you do not have permissions to modify its parent folder.
How can i get permissions? :-|
Or what should i do ?

---

### Post by xenmax on 2006-04-14
eMCee: Try this thread: [http://www.ubuntuforums.org/showthread.php?t=144321](http://www.ubuntuforums.org/showthread.php?t=144321)

---

