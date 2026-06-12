---
title: "My mdadm is smaller than expected :/"
date: 2010-05-02
forum: Hardware
---

### Post by ownaginatious on 2010-05-02
So recently I made a stripe array of two 1.5 TB drives. I copied over about 490 GB of stuff, and when I looked in df, it's already 24% full.

> 

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/md0p1           2113784984 479864568 1526546376  24% /media/test


I know that I don't actually get as much space as advertised on each disk (because of that 1000 for advertising 1024 actual thing), but this seems a bit low (looks like only ~2 TB).

Could there be something that I did wrong when making the RAID?

Thanks :p.

---

