---
title: "burning and ripping of dvd is very slow:help"
date: 2006-03-09
forum: Hardware &amp; Laptops
---

### Post by ubunlilluz on 2006-03-09
hi,
i'm trying to do the backup of my dvd. I've used to do it k9copy and gnomebaker; then i tried dvddecrypter through
wine, but in every case a noted that the operations are very very low. Rippind speed of dvddecrypter is 1.4-1.7x, when in Windows is more then 4x. The dma is ok, is set to on. So
please help me, maybe my driver need to be set better.

---

### Post by frodon on 2006-03-09
You may have to enable DMA : [http://doc.gwos.org/index.php/DMA](http://doc.gwos.org/index.php/DMA)

---

### Post by ubunlilluz on 2006-03-09
the dma is ok:

lillux@lilluxsestum:~$ sudo hdparm /dev/hdd
Password:

/dev/hdd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
lillux@lilluxsestum:~$

---

