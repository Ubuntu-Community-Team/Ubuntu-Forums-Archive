---
title: "Installation takes forever, help or I´ll use M$WIn"
date: 2006-02-26
forum: Hardware &amp; Laptops
---

### Post by BigSwede on 2006-02-26
Hello! Im trying to install Xubuntu on my old 200MhZ 256Mb ram computer. The problem is the istallmenues takes forever to get trough and the partitioner is just silly slow. 18hrs for partitioning an empty 40Gb harddrive? Something is not right. 
Can anyone please help? I think maybe it´s a slow cd-drive that is causing the problem, should I try to copy the install cd to the empty HD?


/Newb

---

### Post by aysiu on 2006-02-26
200 MHz is a pretty slow processor, and you may have a slow CD-ROM drive as well, but 18 hours is insanely long.

Maybe your CD is corrupted somehow.

Do you know how to do checksums?
[http://www.linuxiso.org/viewdoc.php/verifyiso.html](http://www.linuxiso.org/viewdoc.php/verifyiso.html)

---

### Post by BigSwede on 2006-02-26
Yes I know It´s a slow system but still the install should work. I´ll maybe try do  a checksum test later.

I would use DSL, but I really want to have XFCE running.

(and Installing xfce is quite complicated on DSL i´ve heard)

---

### Post by aysiu on 2006-02-26
In DSL just do this: ```
su
``` enter your password then ```
vi /etc/apt/sources.list
``` (I think DSL uses vi... maybe it has nano...?) and add these two sources: ```
deb http://www.os-works.com/debian testing main
deb-src http://www.os-works.com/debian testing main
``` Then ```
apt-get update
apt-get install xfce4
```

---

### Post by BigSwede on 2006-02-26
Great, tanks! I´ll try that :)

---

### Post by SickTwist on 2006-02-26
If the CD and CD-ROM are OK then it's likely that you have a bad/dying HDD. There is no way a Linux install should take 18 hours-- or even half that! You most likely have a hardware problem.

---

