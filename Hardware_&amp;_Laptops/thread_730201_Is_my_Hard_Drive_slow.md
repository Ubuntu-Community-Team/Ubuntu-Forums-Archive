---
title: "Is my Hard Drive slow?"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by tstack77 on 2008-03-20
I have 4 year old Dell Inspiron 600 with a 40gig 5400 IDE HD. I have noticed that programs seem to load slower and the overall snappyness of Gutsy has declined. What I can't figure out is why.

Here are the results of hdparm:

sudo hdparm -Tt /dev/sda1

/dev/sda1:
 Timing cached reads:   1366 MB in  2.00 seconds = 682.81 MB/sec
 Timing buffered disk reads:   36 MB in  3.50 seconds =  10.28 MB/sec

This seems incredibly slow but I have nothing to compare the results to. Is this normal?

Side: I have AWN and Compiz installed but at the time of the test nothing was writing to the disk.

---

### Post by jayson.rowe on 2008-03-20
That seems a little slow, depends on the rest of your system specs though.

Here's mine:
/dev/sda1:
 Timing cached reads:   2668 MB in  2.00 seconds = 1334.28 MB/sec
 Timing buffered disk reads:  214 MB in  3.00 seconds =  71.22 MB/sec

Your "Cached Reads" are going to be more dependent on your CPU/Chipset/RAM than your HDD.

I think there are better ways to benchmark a HDD though, I just don't know of them.

EDIT:
BTW, this is on an AMD Athlon64 X2 4600+ w/ 8GB DDR2-800 running Hardy 8.04 "Alpha 6'ish" AMD64, and the drive tested is an WD 320GB 7200RPM SATA w/ 16MB Cache.

---

