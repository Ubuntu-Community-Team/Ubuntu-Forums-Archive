---
title: "Always Errno 30 when installation, help!"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by zxlstoner on 2009-10-13
I try to install ubuntu 9.04 on my external hard drive.
All is right except when copying files to hard drive around 23%-33%, it always pops the Errno 30 Read-only problem. I suggest that my hard drive or CD/DVD ROM is not correct or I need to burn the CD at low speed. But I indeed burned the installation CD at 4× speed. 
How should I do. I tried a lot of ways but it doesn't work. I even tried copying the iso file on the external hard drive first and then do the hard drive installation instead of CD install.
Is it possible that my external hard drive is too old. It is bought around 2003 which was taken out of my old laptop. But I am fairly sure that it is in a really good condition. 
Hope get the answer soon!
Thanks!

---

### Post by zvacet on 2009-10-13
Did you check [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")?

---

### Post by zxlstoner on 2009-10-13
yes, I checked it.
Actually, I also tried the CD mailed by Ubuntu. It did not work either.

---

### Post by AgentWD-40 on 2009-11-05
I was getting this error as well, but I was installing to two internal mirrored drives. I had to break the drive array, install to one of them, then re-create and rebuild the array. See [[COLOR="Blue"]this post[/COLOR]]("http://ubuntuforums.org/showthread.php?p=8246907#post8246907").

---

