---
title: "oz711m3 smartcard / memory card reader"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by Jim Link on 2007-11-18
I performed the lspci command and it returned this:
```
06:09.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
06:09.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
06:09.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
06:09.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller

```

I searched the ubuntu forums and it seems as though at one time anyway it is possible to get this device to work using the drivers that Musclecard had available here:
[http://www.musclecard.com/sourcedrivers.html](http://www.musclecard.com/sourcedrivers.html)
[ftp://scrdriver:scrdriver@209.19.104.194/Linux/O2Micro_PCMCIA_SCR_203_Linux_Kernel26_OpenSource.tar.gz](ftp://scrdriver:scrdriver@209.19.104.194/Linux/O2Micro_PCMCIA_SCR_203_Linux_Kernel26_OpenSource.tar.gz)

but it seems to me that the site is down or out.  I tried to find them using multiple resources with no luck.  Anyone have this file or know where to get it?

---

### Post by Jim Link on 2007-11-18
gotta love the fact I misspelled the chipset name... damn.  Anyway its the 02711m3 not the oz711m3...sorry about that.

---

### Post by daengbo on 2007-11-18
I'm afraid getting this to work will probably have to wait. It's on the list of requested drivers for the Linux driver project, though.

---

### Post by Jim Link on 2007-11-18
If it weren't for the fact that people have stated that driver did work when it was available I would say cool and quit looking, but it seems to have worked but is nolonger available for download...

anyone else have any ideas or connetions?

---

### Post by Jim Link on 2007-11-24
Ok, I found a place the driver could be downloaded...  but have yet to get it to work.

Here is a link to the page its available on:
[http://saschashideout.de/wiki/OZ711M3/](http://saschashideout.de/wiki/OZ711M3/)

that page has a link to download the actual drivers and has several links to other references pertaining to the oz711m3.

Any help would be appreciated.

---

