---
title: "Slow SATA"
date: 2005-01-07
forum: Hardware &amp; Laptops
---

### Post by negatron on 2005-01-07
First, forgive me about stupid questions but I've just started to use Linux.

The problem: Moving/copying files from PATA-disk to SATA-disk is extremely slow (2MB/s) and uses all processing power. My music stops and even the mouse doesn't move smoothly when moving files. But after the transfer is finished, music and mouse go back to normal.

I've installed the nForce drivers as instructed, but there might be something that I've done wrong. But I'd be more that happy to get the disks faster.

Here are hdparm results.

hdparm -tT

/dev/sda: (Seagate Barracuda 7200.7 SATA)
 Timing buffer-cache reads:   1856 MB in  2.00 seconds = 927.21 MB/sec
 Timing buffered disk reads:  182 MB in  3.00 seconds =  60.62 MB/sec

/dev/hda: (Maxtor Diamondmax+ 9)
 Timing buffer-cache reads:   1880 MB in  2.00 seconds = 940.14 MB/sec
 Timing buffered disk reads:   10 MB in  3.00 seconds =   3.33 MB/sec

/dev/hdd: (Samsung SpinPoint V80)
 Timing buffer-cache reads:   1900 MB in  2.00 seconds = 949.20 MB/sec
 Timing buffered disk reads:    8 MB in  3.80 seconds =   2.11 MB/sec

Ubuntu is installed on sda. I've also tried hdparm -d1 for /dev/hda and /dev/hdd but all I get is this:
HDIO_SET_DMA failed: Operation not permitted
using_dma = 0 (off)

My motherboard is Abit NF7-s rev2.0, if that helps.

---

### Post by Chareos on 2005-05-16
I don't have the HUGE drop you're having, but it's noticeable.

My Seagate Barracuda (8MB cache) SATA drive should really be faster than my Seagate Barracuda (2MB cache) IDE drive...

As of now, SATA drive is slower, according to hdparm -tT
Also, SATA drive don't accept DMA or access mode explicit adjustments.


Is there a way to solve ?
BTW, chipset is nForce4, Hoary amd64 (stock kernel).

---

### Post by robert114 on 2007-06-19
Having the same problem on feisty, using 32 bit at the moment

configuration: 
Motherboard: asus m2n
chipset: Nforce4 
CPU: AMD X2 4600

My hdparm:
Timing cached reads:   1578 MB in  2.00 seconds = 788.39 MB/sec
Timing buffered disk reads:  166 MB in  3.02 seconds =  54.89 MB/sec

Copying large files is a problem the CPU usage is very high!

---

