---
title: "External Drive Mounts as Read Only"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by dannyb91979 on 2007-11-15
Hello,

I just bought a 1tb external WD drive.  When I plug it in, it mounts the drive as read only.  does anyone know how to switch this to allow read and write?

Thanks,
Dan

---

### Post by ddrichardson on 2007-11-15
Which version of Ubuntu are you running? Assuming its earlier than 7.10 then you need ntfs-3g installed other wise its a problem with permissions.

---

### Post by dannyb91979 on 2007-11-15
I am running 6.10.  I installed ntfs-3g.  It still comes up as read only.  It did this with my other external too, but my flash drive works just fine.  Please help!

---

### Post by ddrichardson on 2007-11-15
Try:```
sudo apt-get install ntfs-config
```There's also a guide [here]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html").

---

### Post by dannyb91979 on 2007-11-15
Sorry, I'm still new at this Linux stuff.

Here's what I got when I ran that command:

dan@Milton:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-config

---

### Post by ddrichardson on 2007-11-15
[This thread]("http://ubuntuforums.org/showthread.php?t=217009").

---

