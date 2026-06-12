---
title: "How do I automount eSATA drive?"
date: 2009-07-15
forum: Hardware
---

### Post by eteq on 2009-07-15
I just got a PPA 1165 eSATA ExpressCard on my Asus F8SV laptop, and it appears to work great - if I plug my drive into the card, it immediately appears as /dev/sdb1 and I can manually mount it easily with mount /dev/sdb1 /my/mount/dir .

But, what I would like to do is have the drive automatically mount in a specific location whenever I plug it in (or just operate like USB hotplugging where it goes into /media/whatever).  How do I configure Ubuntu to do this?

I tried adding
UUID=9302505f-7ea3-4152-b4b1-8633e7fc5a62 /media/datadrive ext3 rw 0 0 
to /etc/fstab, and that lets me just "sudo mount datadrive", but it seems like I shouldn't have to do that...

(Oh, and  I'm running jaunty)

---

### Post by Kraut~salat on 2009-07-15
[http://ubuntuforums.org/showthread.php?t=262696](http://ubuntuforums.org/showthread.php?t=262696)

check posting #6, maybe that helps

---

### Post by eteq on 2009-07-15
Hmm... that may work... but I can't find where the rules are that deal with no USB hard drives... is that somewhere else?

---

### Post by cong06 on 2010-08-16
reasonable solution, but like the OP said, it only works with a specific hard drive.

I hotswap SATA hard drives... (over eSATA)

---

