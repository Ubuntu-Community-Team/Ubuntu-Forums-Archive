---
title: "Disk Speeds"
date: 2009-02-04
forum: Hardware
---

### Post by banana989 on 2009-02-04
```

desktop:~$ sudo hdparm -Tt /dev/sdb1

/dev/sdb1:
 Timing cached reads:   1416 MB in  2.00 seconds = 708.25 MB/sec
 Timing buffered disk reads:  316 MB in  3.00 seconds = 105.27 MB/sec
desktop:~$ sudo hdparm -Tt /dev/sdb1

/dev/sdb1:
 Timing cached reads:   1278 MB in  2.00 seconds = 638.70 MB/sec
 Timing buffered disk reads:  318 MB in  3.00 seconds = 105.90 MB/sec

```

This is a brand new Western Digital WD3200KSRTL Caviar 320 GB SATA; **are these normal numbers**?


Additionally when moving files from a disk that gets similar numbers, Gnome reports transfer rates as low as **3MB/s.** (Suck)

---

