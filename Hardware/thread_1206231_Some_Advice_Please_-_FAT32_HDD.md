---
title: "Some Advice Please - FAT32 HDD"
date: 2009-07-06
forum: Hardware
---

### Post by opm595 on 2009-07-06
Hi Guys,

Just bought a new 640gb external HDD, hooked it up to my machine running 9.04 and it works fine however it's formatted in FAT32 and I'm only seeing a capacity of 596gb instead of the 640gb. 

As I understand it FAT32 is a big "no, no" under Linux, is it not?
Anyway, just wondering if anyone can give me a bit of advice on weather or not I should do anything like reformat it to something else, or anything think else you'd care to advise me on in regards to my new HDD. It's an external Western Digital 640gb, Plug and Play, USB 2.0 device.

Also there's 2 files already on the device: AUTORUN.INF and a folder (AUTORUN) containing WDLOGO.ICO  - Can I safely remove these?

Thanks in advance,
Rob

---

### Post by zepita on 2009-07-07
640GB are 640GiB really (1000MB = 1 GiB)

So, 640 GiB = 625,0 GB

The other GBs missing are part of the system volume information that takes a % of the drive total.

You may want to format the partition in EXT3 to get all the benefits from a more secure/fast filesystem. If you need to read the disk in windows, you may install in WinOS a driver to allow read of EXT3 partitions.

---

### Post by anystupidname on 2009-07-07
FAT32 is a poor choice for many reasons:
M$ patents
Fragmentation happy
Compression limitations
No file security
No fault tolerance
No crash recovery abilities
Slow
The list goes on...

---

