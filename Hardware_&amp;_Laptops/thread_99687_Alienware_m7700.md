---
title: "Alienware m7700"
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by Finrod on 2005-12-06
Aright.  I am very new to linux and thought ubuntu would be a good place to get my feet wet.  On attempting the installation on my laptop, I am faced with quite a grievous issue.  My computer has a pair of hard disks in a RAID-0 array.  I would like to keep my installation of Windows xp pro at least while I get my computer running smoothly with ubuntu.  The installer doesn't like that.  No matter what I do, it sees 2 independent hard disks rather than the single array.  This strikes me as slightly odd, being as how my computer has a "fastbuild" utility that loads prior to the os.  If I create another partition in around the last 50 of my 75 free gigs, the first one fails to work as well until I restore to very close to its original size.  (yeah, it's all defragged and all and nothing should be in that area of the disk, but obviously I am fallible...)  I need to know what I can do to get this silly thing to read a single 120 gig hdd (instead of 2 60 gig ones) and what I can do to get it to install on a separate partition keeping windows alive.  Thanks!

---

### Post by ffadmraven on 2006-03-05
Hi, I have a M770 as well, but I only have one drive.  I do remember that if you choose the lvm option though, it should see it as one drive (maybe).  As for your windows, use your OEM CD to reinstall WindozeXP to adjust the partition size accordingly.  Windows will not let you change the partition size on a Raid array with out reinstalling (sorry).

---

