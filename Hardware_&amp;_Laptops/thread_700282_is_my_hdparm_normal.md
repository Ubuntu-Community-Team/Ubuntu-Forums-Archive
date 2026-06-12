---
title: "is my hdparm normal"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by afeasfaerw23231233 on 2008-02-18
here's my hdparm results on two boxes

box1 p4 1.8G 768MB RAM ATA-100 80G and ATA-100 160G harddisk
/dev/sda:
 Timing cached reads:   686 MB in  2.00 seconds = 342.27 MB/sec
 Timing buffered disk reads:  160 MB in  3.01 seconds =  53.18 MB/sec

/dev/sdb:
 Timing cached reads:   682 MB in  2.00 seconds = 340.26 MB/sec
 Timing buffered disk reads:  210 MB in  3.03 seconds =  69.33 MB/sec


box2 pIII 933Mhz 384MB RAM ATA-66 20G hardisk
/dev/sda:
 Timing cached reads:   204 MB in  2.00 seconds = 101.84 MB/sec
 Timing buffered disk reads:   68 MB in  3.06 seconds =  22.24 MB/sec

is it normal? i also want to know the results of the other boxes with similar spec

---

### Post by logos34 on 2008-02-18
your disk reads look fine, but the the cached reads are strangely low

---

### Post by Subliminal Aura on 2008-02-18
They are fine...

Cached read/writes are slow probably due to the slow bus on those machines.

Here's an old athlon machine...

root bart2:~> hdparm -tT /dev/hda

/dev/hda:
 Timing buffer-cache reads:   128 MB in  0.38 seconds =336.84 MB/sec
 Timing buffered disk reads:  64 MB in  2.39 seconds = 26.78 MB/sec
root bart2:~> hdparm -tT /dev/hdd

/dev/hdd:
 Timing buffer-cache reads:   128 MB in  0.37 seconds =345.95 MB/sec
 Timing buffered disk reads:  64 MB in  1.11 seconds = 57.66 MB/sec

---

### Post by afeasfaerw23231233 on 2008-02-20
yes, the cached read/writes are slow. any one know whats the bandwidth of north-south bridge link of i845G and ICH4?

---

