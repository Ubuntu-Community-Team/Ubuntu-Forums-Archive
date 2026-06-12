---
title: "Replacing HDD laptop - clone drive?"
date: 2010-11-29
forum: Hardware
---

### Post by polar11 on 2010-11-29
Hi All

A friends laptop (old samsung laptop 4 years old approx) hdd is dying - he has purchased a replacement samsung ide drive 160gb (original is 80gb).  Also got a usb enclosure with the intention being to clone the internal drive (windows xp) and then replace the drive. I assume the best way would be to boot ubuntu from the live cd and clone away? He wants to keep XP

can anybody provide a bit of advise as to whether this would be the best way and any recommendations for good easy to use cloning programs?

many thanks

---

### Post by polar11 on 2010-11-30
anyone?

---

### Post by Towers of Creation on 2010-11-30
A way to do it for about one dollar would be to use the Macrium Reflect Free software below to back up the hard drive onto DVD blanks. That’s assuming it be programmed to install Windows XP. Then use a program to make the boot disk. Then put the new hard drive in a laptop and use the boot disk to start the restore process. The firm also uses compression. I backed up an entire Vista Windows build onto three DVD blanks.

Macrium Reflect Free 4.2 build 2952 :p

[URL="http://download.cnet.com/Macrium-Reflect-Free/3000-2242_4-10845728.html?tag=mncol;1"]http://download.cnet.com/Macrium-Reflect-Free/3000-2242_4-10845728.html?tag=mncol;1
[/URL]
Other free cloning software can be found here.

Free Hard Disk and Partition Imaging and Backup Software

[URL="http://www.thefreecountry.com/utilities/backupandimage.shtml"]http://www.thefreecountry.com/utilities/backupandimage.shtml
[/URL]
[URL="http://www.thefreecountry.com/utilities/backupandimage.shtml#imaging"]http://www.thefreecountry.com/utilities/backupandimage.shtml#imaging
[/URL]

---

### Post by pricetech on 2010-11-30
You can also make a windows PE using your existing XP install.  PE will let you create an image of the drive and restore that image to the new drive.  Piece of cake to use.  Make it with a free download from Microsoft.

---

### Post by cristianfere on 2010-11-30
See: [http://redobackup.org/](http://redobackup.org/)

---

### Post by celsdogg on 2010-11-30
alternative methods:

boot from the Live CD and use dd to clone the original drive (in the usb enclosure) to the new drive (installed in the laptop)

You can also try PING to create images for backing up and restoring: [http://ping.windowsdream.com/](http://ping.windowsdream.com/)

---

