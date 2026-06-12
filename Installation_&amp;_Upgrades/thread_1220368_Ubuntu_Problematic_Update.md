---
title: "Ubuntu Problematic Update"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by 23.12.2012 on 2009-07-22
Hi! I've installed Ubuntu 9.04 on a MacBook Pro. I've firstly created a new partition for Windows, using Boot Camp, and then installed Ubuntu on that one.

Although it might sound like an OS X problem, it's not. I've given 17GB to the partition, as all I need is a Ubuntu with Cross Over and two Windows applications. But when I go to the Update Manager, it does not allow me to install the updates because there isn't enough space. I can't really figure this out. I'm posting a screenshot for you to see.

Thanks in advance, and, again, don't move this to the Apple forum.

---

### Post by Partyboi2 on 2009-07-22
Hi, it looks like you don't have much room left on your / partition. Open a terminal (Applications>Accessories>Terminal) and type
```
sudo apt-get clean
``` this might make some extra space, also empty the trash can which also might yeild extra space.
If you are able too, you might want to look at increasing the size of your Ubuntu partition so you don't keep running into this problem.

---

### Post by 23.12.2012 on 2009-07-22
I've already done this, but it does not provide me enough space. How the hell don't I have enough space?!? I'd say 17GB is more than enough for an operating system.

Now the problem is so big I can't even open the Partition Editor...

---

### Post by Partyboi2 on 2009-07-23
> **23.12.2012 said:**
> I've already done this, but it does not provide me enough space. How the hell don't I have enough space?!? I'd say 17GB is more than enough for an operating system.

Now the problem is so big I can't even open the Partition Editor...
According to gparted its not Ubuntu taking the room up its bootcamp.

---

### Post by starcannon on 2009-07-23
The ext3 partition /dev/sda4 is only 2.33gb, thats the problem.
Bootcamp is holding the rest. Try again, perhaps use the manual partition manager during the Ubuntu installer, I've never tried to install Ubuntu using Bootcamp, so not sure. Be sure to check out the [Apple Subforums]("http://ubuntuforums.org/forumdisplay.php?f=328") for additional advice.
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

GL and HF

---

