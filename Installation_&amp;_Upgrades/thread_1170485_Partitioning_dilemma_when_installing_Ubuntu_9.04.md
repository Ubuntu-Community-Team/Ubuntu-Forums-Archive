---
title: "Partitioning dilemma when installing Ubuntu 9.04"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by simpeeg on 2009-05-26
Hi Ubuntu Geeks!

Upon installation of Ubuntu 9.04, i've been trying to partition my hard disk in such a fashion that it will be split into 4 primary partitions (one for Windows, one for Ubuntu, one for my personal files and a last one for the "swap"). Sadly, my hard disk already has 2 primary partitions (one for Windows and one created by my PC manufacturer, TOSHIBA). If you do the math, adding 3 primary partitions to my hard disk would make 5 total partitions, a feat which is sadly impossible to achieve :( . So i'm wondering if I could simply forget creating a primary partition for the "swap". My computer has 4GB of RAM, so i'm questioning the necessity of having an extra 1 or so GB of memory located on my hard disk. By leaving behind the "swap", I would be OK, my HDD would be split like this: 1 partition for Windows, 1 for Ubuntu, 1 for my files and 1 for the Toshiba files. Would this cause a problem? Is there any solution existing?

Thanks for your collaboration!

---

### Post by udippel on 2009-05-26
Yes. All is possible. What you need to do is creating an extended partition and then you can create up to 26 logical partitions in there. Not intending you should follow mine, I just show how easy it is, here on my box:

/dev/sda1               1          39      313236   83  Linux
/dev/sda2              40       20927   167782860   bf  Solaris
/dev/sda3           20928       26150    41953747+  83  Linux
/dev/sda4           26151       77825   415079437+   5  Extended
/dev/sda5           26151       26282     1060258+  83  Linux
/dev/sda6           26283       26818     4305388+  82  Linux swap / Solaris
/dev/sda7           26819       26950     1060258+  83  Linux
/dev/sda8           26951       27995     8393931   83  Linux
/dev/sda9           27996       28518     4200966   83  Linux
/dev/sda10          28519       31130    20980858+  83  Linux
/dev/sda11          31131       34264    25173823+   b  W95 FAT32
/dev/sda12          34265       38181    31463271   83  Linux
/dev/sda13          38182       77825   318440398+  83  Linux

Windows needs a primary partition, if I am not mistaken, and your Toshiba. The others can as well live on logical partitions.

Hope this helps,

Uwe

---

