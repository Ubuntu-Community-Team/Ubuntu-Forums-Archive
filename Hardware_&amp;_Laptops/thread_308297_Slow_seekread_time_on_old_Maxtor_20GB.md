---
title: "Slow seek/read time on old Maxtor 20GB"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by russianpirate on 2006-11-27
This is not exactly a linux question, but it applies to both windows and linux. I have 2 hard drives, a pretty new (2005 i think) Western Digital Caviar 80GB 8MB cache 7200rpm and an old (2000-2001 maybe) Maxtor 20GB (i think 5400rpm). The WD works great (read speeds like 30-40mb/s i think and write 20-25mb/s, seek time is great too). However, the Maxtor is probably just too old and now everything after the first few sectors (first 2-3gb), everything reads slow and seek time sucks. It takes more than a second to find the next song on my playlist, and it takes forever to get the ID3 info to the playlist. When copying those "slow" files to my mp3 player, the speeds are like <1 - 3 mb/s and the comp. lags a lot, unlike the other hard drive which goes like 10mb/s. Basically, is this the end of my hard drive, I mean I can barely take this because sometimes i need to copy the music quickly to the mp3 player in the morning.

Thanks a lot.. is there any performance enhancement (its not fragmented) i can do. The filesystem is NTFS, but i dont think it will slow it down THAT much.

Thanks again.

---

### Post by po0f on 2006-11-28
russianpirate,

The slow rotation (5400RPM compared to 7200RPM) will definitely affect performance, but I don't think by that much.  Run the following command (after booting into Linux) to see what mode it's running in:
```
[FONT="Courier New"]$ **hdparm -i /dev/hdX**[/FONT]
```
where X is the drive (a for master, b for slave).  There are three modes of operation (in order of their speed, least to greatest): PIO, DMA, and UDMA.  If it's an especially old drive (I have a WD 20GB model that won't operate higher than udma3), you might not get much more performance out of it.

Also another thing to consider is how much traffic is flowing through the IDE controller.  If both hard disks on an IDE channel are in use at the same time, it will bog down the speeds, as data can only be moved in one direction at a time.  (It really sucks when you're moving data from hda to hdb!)

---

### Post by russianpirate on 2006-11-28
Well it is on one IDE channel, but it's better than having the CDROM with the HD. It is running Ultra DMA 2 right now.

---

### Post by russianpirate on 2006-11-28
*Bump Please*

---

