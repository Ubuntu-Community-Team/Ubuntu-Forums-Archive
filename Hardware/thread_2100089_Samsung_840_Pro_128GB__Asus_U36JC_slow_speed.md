---
title: "Samsung 840 Pro 128GB | Asus U36JC slow speed?"
date: 2012-12-31
forum: Hardware
---

### Post by foureight84 on 2012-12-31
I just installed Elementary OS (Ubuntu 12.04 based) on my Samsung 840 Pro (128GB) using GPT and aligned all the partitions. After installing Ubuntu, I modified the Fstab to add noatime and discard.

The strange thing that i'm noticing when I run hdparm -Tt is how slow the cached read and disk reads:

/dev/sda:
 Timing cached reads:   6290 MB in  2.00 seconds = 3145.90 MB/sec
 Timing buffered disk reads: 754 MB in  3.01 seconds = 250.81 MB/sec

Which is odd since I saw hdparm results for the Samsung 830 on archlinux:
[https://wiki.archlinux.org/index.php/SSD_Benchmarking#SAMSUNG_830_128GB](https://wiki.archlinux.org/index.php/SSD_Benchmarking#SAMSUNG_830_128GB)

# hdparm -Tt /dev/sda
Timing cached reads:   22130 MB in  2.00 seconds = 11080.54 MB/sec
Timing buffered disk reads: 1500 MB in  3.00 seconds = 499.38 MB/sec

Anyone know what could be causing this?

---

### Post by Dulleo on 2013-01-09
A) That's pretty fast still! Compared to a platter drive you're flying :D

B) My google search shows that your computer has SATA II, which is limiting the speeds to about 300 MB/s.  Only with a SATA III compatible machine will you hit the speeds close to 600 MB/s. 

See [http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)

---

