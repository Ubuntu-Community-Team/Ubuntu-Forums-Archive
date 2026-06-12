---
title: "How do you move an instalation to another HDD?"
date: 2006-05-28
forum: Hardware &amp; Laptops
---

### Post by Lucho on 2006-05-28
Not too long ago I posted a problem about the kernel I compiled
for my Breezy-64. Basically, I've got Debian (Etch and Sid) on hda, and
Ubuntu (Breezy and Dapper Beta) on hdb, as well as data partitions on both.
In the end, I'm going to move Breezy; I was going to remove the Sid partition
anyway, I'll replace it with Breezy-64.
        So here's my question: Is it possible to move a pre-existing installation
from one HD to another? I know about DD, but would it work? Or will I have
to re-install Breezy? I'll reinstall if necessary, but I'd like to keep my nicely-
tweaked installation.

---

### Post by aysiu on 2006-05-28
Try PartImage:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by Lucho on 2006-05-29
Sorry, too quick on the post button :roll:

---

### Post by Lucho on 2006-05-29
Interesting, but I have two doubts- all I have to do is create an image file
of my partition and copy it over to the new partition? Does it matter that it
will be going to a different HDD (from hdb1 to hda2)? Also, does it matter
that the partitions are different sizes (from 10GB to 25GB, but same reiserfs)?

      Sorry for the questions, but I want to get it right the first time.

---

### Post by aysiu on 2006-05-29
[QUOTE=Lucho]Interesting, but I have two doubts- all I have to do is create an image file
of my partition and copy it over to the new partition? Does it matter that it
will be going to a different HDD (from hdb1 to hda2)?[/quote] Yes, actually, it does. Thanks for asking. Your /boot/grub/menu.lst will refer to your partitions and also your /etc/fstab file will refer to your partitions, so you'll have to modify these in order to get them working.

> Also, does it matter
that the partitions are different sizes (from 10GB to 25GB, but same reiserfs)? The *used* space is what gets copied, not the entire partition. So if you have a 10 GB partition but only 6 GB of it is used, the partition image will be 6 GB.

I think what you should do is copy the image over, [restore Grub to the MBR](http://ubuntuforums.org/showthread.php?t=24113), adjust the aforementioned configuration files, and see if it works. Then you can erase the old partition if it does work and keep the old partition (and try to think of something else) if it doesn't work.

---

### Post by Lucho on 2006-05-29
Ok, sorry to seem dense, but just to make sure I understand- 
Grub is no problem. Yes, it´s in the MBR, but I boot out of Debian Etch-
my hda1. So in any case, editing Grub is a piece of cake. The same goes
for /etc/fstab; I´ve edited it before. 
  If those are the only two files to edit, I´ll set it up and post the results.
Thanks for the help 
         PAZ

---

