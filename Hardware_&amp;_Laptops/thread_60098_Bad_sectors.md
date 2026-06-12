---
title: "Bad sectors"
date: 2005-08-26
forum: Hardware &amp; Laptops
---

### Post by Hardi on 2005-08-26
Hy.
My hard drive makes wierd noises sometimes. It's almost impossible to boot without the noises. While the noise begins, the computer will stop working for ~5 secs. Sometimes it continues working but sometimes the computer freezes completely. I have 2 partitions.
1 partition has Linux Ubuntu on it.
the 2th partition has Windows XP on it.
The fault first appeared when I was working on windows for the last 2 months.
What I want, is to find out what really causes this problem.
And does anyone know a bad sector hunter for Ubuntu 5.04 Hoary hedehog(please give me the direct link to downloading). My system might crash at any time.

---

### Post by Scrambler on 2005-08-26
Well then your Hard Disk will probably be dead sometime in the future. Get a new one ;-) Finding bad sectors and reallocating them will most likely might destroy data because broken sectors will be remapped.

man e2fsck: "e2fsck -c [-c] /dev/hda1" or "badblocks" is what you'd need to use (should be base installed) 

Depending on the make of the hard disk, there are programs supplied by the vendors of the disk which will analyze the disk and perhaps tell you what is wrong with it.

Cheers, Uwe

---

