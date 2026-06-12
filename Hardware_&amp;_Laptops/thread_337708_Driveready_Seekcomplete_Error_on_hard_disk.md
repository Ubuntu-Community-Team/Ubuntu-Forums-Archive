---
title: "Driveready Seekcomplete Error on hard disk"
date: 2007-01-13
forum: Hardware &amp; Laptops
---

### Post by kdub432 on 2007-01-13
I've been using a maxtor 300 gig sata hard drive for quite some time now under linux. However, yesterday, when I tried to boot up my computer, it wouldnt boot, and kept complaining about a "Driveready Seekcomplete Error" on my sata drive. At first i thought it might just be broken, but it works perfectly well under my windows partition. This is baffling me. I know from using the drive under windows that it works, but whenever i try to use it under linux, (even live cds) linux wont start. If i unplug my sata drive, and just use my other HDD(which has my OS-es on it) linux will boot fine. any help or suggestions would be appreciated.

---

### Post by kdub432 on 2007-01-14
I fixed this problem by running "spinrite" a hard disk repair utility. I had massive corruption of my data on track 0, which spinrite was able to correct, without any data loss

---

