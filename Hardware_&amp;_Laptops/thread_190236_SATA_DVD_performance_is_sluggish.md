---
title: "SATA DVD performance is sluggish"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by nudnikmeow on 2006-06-06
Hi,

I have a new Dell Inspiron E1705 (aka 9400) laptop.  It runs ubuntu well, except for one thing: the DVD performance is not very good.  The DVD+-RW drive is a SONY DVD+-RW DW-Q58A.  This drive is an SATA drive, so the interface should be plenty fast.

However, the DVD burn performance and read performance are somewhat slower than I expected (Seems to peak at 5 megs/s).  Here is output from hdparm:

sudo hdparm -Tt /dev/scd0

/dev/scd0:
 Timing cached reads:   3716 MB in  2.00 seconds = 1857.35 MB/sec
 Timing buffered disk reads:   14 MB in  3.07 seconds =   4.56 MB/sec

Note that sometimes the buffered disk reads are only 250 KB/s!

Is there any way to improve this performance?  When I play a video file off a data DVD (using mplayer), it seems like the drive cannot keep up, as playback will lag.  That same video file, when read off the 7200rpm harddisk of course runs fine.

Any ideas of how to improve performance?
-Zeke

---

### Post by nalmeth on 2006-06-07
Tryed enabling DMA hardware acceleration?
[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

---

