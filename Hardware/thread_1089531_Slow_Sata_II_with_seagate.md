---
title: "Slow Sata II with seagate"
date: 2009-03-07
forum: Hardware
---

### Post by mmark on 2009-03-07
HI!

My drive is slow. My motherboard is using AMD 690 chipset.

The hdparm  -tT results:

 Timing cached reads:   1046 MB in  2.00 seconds = 522.82 MB/sec
 Timing buffered disk reads:  180 MB in  3.01 seconds =  59.89 MB/sec

 the smartmontools results:

[http://pastebin.com/m4068063e](http://pastebin.com/m4068063e)

Also the seek noise is loud.

Can anybody help, why the timing cached read is so slow?

---

### Post by taurus on 2009-03-07
There is a jumper on the back of the drive and when you purchase it, it sets to 1.5Gb/s so you need to remove it if you want the max, 3Gb/s.

---

### Post by mmark on 2009-03-07
it's already removed.
but thx for the answer.

---

