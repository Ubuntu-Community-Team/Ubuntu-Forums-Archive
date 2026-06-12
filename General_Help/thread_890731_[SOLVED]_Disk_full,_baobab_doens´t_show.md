---
title: "[SOLVED] Disk full, baobab doens´t show"
date: 2008-08-15
forum: General Help
---

### Post by adieb on 2008-08-15
I am writing this thread, because I think that this could happen to anyone, and finding the solution is really difficult:


**DISK FULL:**
Yesterday i noticed, that my root-partition is full.
df -h showed 99% usage.

I wondered, because i use to store any data on /media/something, which is another disk. and /home is another partition too!

**SEARCHING FOR THE BIG FILES...**
So I started BAOBAB, the gnome disk-analyzer. I scanned my HDD and reported, that 18,9 GB of my 19GB Partition are used. But in the "usage-tree" it just counted 6 GB at all. ????


**SEARCHING THE NET:**
I really wondered, so I searched the internet, (i first thought it is a baobab bug.) And really, there were some posts that described similar problems. 
Some then said, it ist because of /root/.Thrash, other said it is because of a backup, that cannot be seen, or whatever.


**REALIZING SOMETHING STUPID ;-)**
In the end, I discovered, that it really was because of backup, that cannot be seen, but it really took me a while to discover.

/media/data is mount-point for another disk. But when I unmounted the disk, I discovered, that there was a 12GB big file.

**Baobab couldn´t see it, because it is normally covered by the mount.**



So i think that happened because of a automatic backup and a failure in mounting the disk. I don´t really know how that could happen...

Best regards and good luck

---

