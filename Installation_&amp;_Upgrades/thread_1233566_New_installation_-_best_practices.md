---
title: "New installation - best practices"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by ek1975 on 2009-08-06
Hello Guys, I bought a 300 GB HD and I am thinking about spliting it into 3 partitions. One for Windows XP, One for Ubuntu and one for my own data. I thought I should be able to share the data partition between Ubuntu and XP. Or should I have 4 partitions and put the Ubuntu data separate from Windows data. I read somewhere that putting Ubuntu and XP in separate partitions is an old stone age theory. Is that right?
 
I just want to start out right, so I could use some of your experience. Thanks for your time,
EK

---

### Post by Partyboi2 on 2009-08-06
> I read somewhere that putting Ubuntu and XP in separate partitions is an old stone age theory. Is that right? Ubuntu runs better installed to its own Partitions.
Ubuntu can read/write ntfs filesystem, so you could have a separate ntfs partition for sharing your data between Windows and Ubuntu.

---

### Post by merlinus on 2009-08-06
I also recommend creating a separate /home partition, which will make reinstalling and installing new versions easier.

---

### Post by ek1975 on 2009-08-06
Thanks Partyboi2.  I've got a couple of other questions.  The reason for me installing Ubuntu (Desktop version) is because I would like to install LAMP and play with it for my own personel use.
 
Secondly my old HD crashed and I can't seem get my data off it using XP.  I read that there is a way with Ubuntu where it's possible to read data off a crashed HD (not a mechanical failure).  I hope these two goals are possible.  Thanks again.

---

### Post by merlinus on 2009-08-06
Try testdisk and photorec for recovering data.

---

### Post by ek1975 on 2009-08-06
Thanks merlin,  I'll give that a shot.  Looks like I will have to install the Ubuntu server edition (instead of the desktop edition) for a LAMP setup...?

---

### Post by Partyboi2 on 2009-08-06
> **ek1975 said:**
> Thanks merlin,  I'll give that a shot.  Looks like I will have to install the Ubuntu server edition (instead of the desktop edition) for a LAMP setup...?
You can use the Desktop version.

---

### Post by ek1975 on 2009-08-06
Thanks Guys.  I wish I had this sort of support for software we really have to pay for!!!

---

### Post by chuckh1958 on 2009-09-01
> **merlinus said:**
> I also recommend creating a separate /home partition, which will make reinstalling and installing new versions easier.

I am curious as to how this makes installing new versions easier. TIA

---

### Post by Partyboi2 on 2009-09-01
> **chuckh1958 said:**
> I am curious as to how this makes installing new versions easier. TIA
The advantage of having a separate /home partition is that if  you need to reinstall or do a clean install is that all your data (music, videos, documents, settings etc...) that is on the /home partition will remain untouched.

---

### Post by raymondh on 2009-09-01
> **Partyboi2 said:**
> The advantage of having a separate /home partition is that if  you need to reinstall or do a clean install is that all your data (music, videos, documents, settings etc...) that is on the /home partition will remain untouched.

As I happen to be currently reading up on our linux filesystem hierarchy ...

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/home.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/home.html)

---

### Post by ronparent on 2009-09-01
Another advantage of a separate /home partition is that all your setting would be retained with a reinstall or major upgrade. Your customized desktop, for instance, would be the same as before.

---

