---
title: "upgrade to ubuntu 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by shaon3343 on 2009-10-30
[SIZE="3"]hi everyone , Is it possible to Upgrade my ubuntu 9.04 to ubuntu 9.10 with a ubuntu 9.10 live cd? ;) what will happen to my existing software? will they work as they are working now?? please help me[/SIZE].

---

### Post by dummy910 on 2009-10-30
> Is it possible to Upgrade my ubuntu 9.04 to ubuntu 9.10 with a ubuntu 9.10 live cd?
You can do an in place upgrade by using the Alternative version iso burned into either a cd-rom or usb-drive(for backup purposes). Mount the iso, load a terminal and navigate to the folder where you mounted it and:
```
gksudo ./cdromupgrade
```
and it will whir away and might also pipe out to download some more files-programs that you added above what were the standard progs in 9.04.
> what will happen to my existing software?
All existing software will be upgraded, thus the need for 'cdromupgrade' to pipe out and download those programs.
> will they work as they are working now?
They should. On all the machines I've upgraded to 9.10 over the last day, are all working fine, and most run a tad quicker too.

---

