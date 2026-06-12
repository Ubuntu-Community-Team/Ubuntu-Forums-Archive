---
title: "Please help!!!!!!!"
date: 2007-01-14
forum: Hardware &amp; Laptops
---

### Post by RaZoR-x11 on 2007-01-14
Hey there,

my samsung hd pata 250gd 7200rpm, 8mb has stoped booting, 
after i used partition magic 8.0 i resized the main home partition 
which was about 170gb tryed to rezise to 140gb and after a reboot
it did not wanna boot, so i loaded up partition magic again and there 
was a error.

```
partition tabe error #108
```


So atm im very confussed as i did back up my MBR to a 128, and track file
after i got the error in partition magic i restored my backup mbr the one before
i edited the hard drive partition's, is there anyway to render my harddisk working?

Ohh and im running ubuntu 6.10 Edgy, if that help's.

Meany thank's in advance!!

RaZoR.

---

### Post by logos34 on 2007-01-14
Boot from the Ubuntu install livecd, load the desktop, open a terminal and type
> sudo e2fsck /dev/hda1 
(or whatver your root partition is)

Or try [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by RaZoR-x11 on 2007-01-14
Hey thank for the quick reply, i have tryed the command you said on all hda1 to hda6 but i get error's on the last 3 hda4,hda5,hda6.

Honestly im all out off idea's 

Anyway thank you very much.

---

### Post by logos34 on 2007-01-14
then get TestDisk...hopefully that'll fix your partition table

---

### Post by RaZoR-x11 on 2007-01-14
It worked thank you very much! :D:D:D:D

---

