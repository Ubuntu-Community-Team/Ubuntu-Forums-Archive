---
title: "Using a tape drive"
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by speedkreature on 2007-09-24
I have an old IDE tape drive (Seagate ST20000A) from which I'd like to read and copy the contents on to my hard drive.  I know the backup is good.

Firstly, I started my research with:
[This Thread]("http://ubuntuforums.org/showthread.php?t=391032")


I have read through dmesg output and found the drive to have a relationship between hdc and ht0...

```
[   15.977324]     ide1: BM-DMA at 0xe408-0xe40f, BIOS settings: hdc:DMA, hdd:pio
[    5.892000] hdc: Seagate STT20000A, ATAPI TAPE drive
[    6.564000] hdc: Disabling (U)DMA for Seagate STT20000A (blacklisted)
[    6.664000] ide-tape: hdc <-> ht0: Seagate STT20000A rev 8A51
[    6.672000] ide-tape: hdc <-> ht0: 1000KBps, 6*54kB buffer, 9720kB pipeline, 108ms tDSC

```

I then ran *mt -f /dev/ht0 status* and got...
```
drive type = 114
drive status = 512
sense key error = 0
residue count = 0
file number = 0
block number = 0

```
...I don't have the foggiest what that means but there weren't any erros so I assume all is well.
I've installed several backup suites (amanda--which I didn't know how to use, bacula, downloaded a trial version of Yosemite's--a previous version of which came with the tape drive) and haven't had any luck.

When I had this drive attached to my XP computer (RIP) about 5 years ago, I do recall it being very picky about how it was jumpered and what, if anything, was attached to the IDE channel it was on.

I don't need to write anything to the drive (thought that would be nice, I guess), I just need to know what to do so I can copy from it.  I don't even need to read indivitual files really; I just want the entire contents of the tape on my hard drive.

I've read through *man mt* and can control the device itself (i.e. seeking, retensioning, etc), but I haven't been able read anything yet.

I should probably also mention that I'm using 7.10 (Gutsy).

Please advise.

---

