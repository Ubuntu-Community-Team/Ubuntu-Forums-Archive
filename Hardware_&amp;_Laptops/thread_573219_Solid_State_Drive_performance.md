---
title: "Solid State Drive performance"
date: 2007-10-11
forum: Hardware &amp; Laptops
---

### Post by ehazlett on 2007-10-11
i have a dell latitude d430 with the SanDisk SSD UATA 500 32G  solid state drive.  ubuntu only shows the drive in udma2 with lackluster performance (boot times, etc. almost same as hard drives).  the drive supports udma6 which SanDisk recommends for highest performance...  

here are the hdparm -Tt stats from my d430 (ssd - Gutsy 64bit) and d630 (with a regular 7200 sata - Feisty 64bit)

d630:
/dev/sda:

 Timing cached reads:   8834 MB in  1.99 seconds = 4431.22 MB/sec

 Timing buffered disk reads:  170 MB in  3.02 seconds =  56.24 MB/sec


d430:
/dev/sda:
 Timing cached reads:   1546 MB in  2.00 seconds = 773.31 MB/sec
 Timing buffered disk reads:   84 MB in  3.07 seconds =  27.37 MB/sec


any ideas?


evan

---

### Post by cubeist on 2007-10-11
very interesting... I am behind the times, I didn't even know these were on the market for consumers...  It looks to me like it is treating it as a normal ide drive... but the speeds are slow even for ide... I really don't have a suggestion for you, but I found this link which may give you a place to start

[http://www.uwsg.iu.edu/hypermail/linux/kernel/0702.1/1486.html](http://www.uwsg.iu.edu/hypermail/linux/kernel/0702.1/1486.html)

keep us updated

---

