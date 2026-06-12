---
title: "Mount External hard drives maxtor 3200"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by mysticfrost on 2007-08-01


If you have an external hard drive like maxtor and you cant mount it in Ubuntu do the following:

1)Use gparted 
2)select device as sdb1
3)choose make disklabel

and presto your external hard drive mounts!

Before that make sure you have installed ntfsconfig tool and enabled write for internal and external hard drives.

---

### Post by PONGsiFU on 2007-08-25
if you have a stuffed up hardrive already, using the "disklabel" option won't work because it requires reformatting unless you are willing to lose all your data.  
I solved this by using the app automatix instead, and installed the app within automatix  the "Automatix read/write NTFS FAT32 Mounter". Remember to follow the directions.  Pay close attention in removing all external hardrives* very important, restart, restart again, while in desktop, replug all usb drivers. BAM ALL DONE YO

---

