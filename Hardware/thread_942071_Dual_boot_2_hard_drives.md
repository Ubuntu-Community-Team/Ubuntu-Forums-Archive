---
title: "Dual boot 2 hard drives"
date: 2008-10-08
forum: Hardware
---

### Post by kortez on 2008-10-08
Hello all. I would like to know if it is possible and easy enough to dual boot with 2 operating systems on 2 different hard drives. I have windows xp on one hard drive and Ubuntu on the other one.

Thankyou in advance

---

### Post by Sef on 2008-10-08
Yes, read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

---

### Post by kortez on 2008-10-10
I followed the guide from [http://ubuntuforums.org/showthread.php?t=179902&highlight=dual+boot+hard+drives](http://ubuntuforums.org/showthread.php?t=179902&highlight=dual+boot+hard+drives) . It worked perfectly, except for one thing. Ubuntu sees the Windows hard drive and allows me to use it, but Windows sees the Ubuntu hard drive (it is in the device manager list) and I cannot access it, write to it/read it . Is there a way to "add" the Ubuntu hard drive (master) to Windows (slave drive) without formatting the master drive?

---

### Post by caljohnsmith on 2008-10-10
Windows doesn't know how to deal with any linux file systems, like Ubuntu's usual ext3 file system for example, so you have to use special software in Windows in order to access your linux partitions. One great free program that does that is ext2fsd, and you can download it from here:

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

Give that a shot and let me know how it goes. :)

---

### Post by kortez on 2008-10-11
Thankyou! It works perfectly.

---

