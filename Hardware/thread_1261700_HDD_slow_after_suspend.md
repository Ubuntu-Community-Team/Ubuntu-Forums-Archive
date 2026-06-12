---
title: "HDD slow after suspend"
date: 2009-09-09
forum: Hardware
---

### Post by mehturt on 2009-09-09
The hdd is slow after laptop is resumed from pm-suspend.
I get this result from hdparm -tT /dev/sda:
[FONT="Courier New"]/dev/sda:
 Timing cached reads:     2 MB in  3.10 seconds = 660.59 kB/sec
  Timing buffered disk reads:    4 MB in  3.59 seconds =   1.11 MB/sec[/FONT]
Normally I'm getting:
[FONT="Courier New"]/dev/sda:
 Timing cached reads:   2118 MB in  2.00 seconds = 1059.13 MB/sec
 Timing buffered disk reads:  170 MB in  3.02 seconds =  56.31 MB/sec
[/FONT]
My hw is Dell D630, running Ubuntu 9.04 x86_64.

---

### Post by cristianrosa on 2009-09-18
I'm having exactly the same problem with a Dell Precision M90.
There is already a bug report in launchpad [Bug #371212]("https://bugs.launchpad.net/bugs/371212").
It seems related to the ahci driver for managing the disk.

---

### Post by mehturt on 2009-09-18
thanks for the bug report, I'll subscribe

---

