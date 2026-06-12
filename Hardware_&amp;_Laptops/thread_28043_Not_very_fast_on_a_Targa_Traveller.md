---
title: "Not very fast on a Targa Traveller"
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by Aurels on 2005-04-18
I've just installed ubuntu on my Targa Traveller laptop (AMD 64 3000+, 512Mo, ATI mobility radeon X700) and it's less fast than with my Athlon 2200+ 512Mo...
Is it just because the HDD is slow??

---

### Post by Aurels on 2005-04-18
PS: I installed hoary 5.04 i386

---

### Post by PinGzor on 2005-04-19
You can check if your hdd is slow with the command: sudo hdparm -tT /dev/hdX (X=your disk)

Then you can check if your processors speed, laptops can clock down their processors. Check if powernowd is running,

---

### Post by Aurels on 2005-04-19
OK thanks.
Result:

```

root@pingu:/home/aurels # hdparm -tT /dev/hda
/dev/hda:
 Timing cached reads:   2160 MB in  2.00 seconds = 1078.55 MB/sec
 Timing buffered disk reads:    4 MB in  3.93 seconds =   1.02 MB/sec
root@pingu:/home/aurels #

```

How to interpret this results?  :-? 

powernowd was running. Does it make CPU less performent?

---

### Post by StephenTidey on 2005-05-27
Hiya Aurels,

I too have installed Linux on my Targa (but I must confess it's not ubuntu) and I had the same problem of it going VERY slowly.

I found the problem was the kernel was using the default IDE driver and had not enabled DMA - so I upgraded to v2.6.10 and this one used the ATIIXP IDE driver which in turn enabled DMA and my throughput went from 1MB to 30MB transfer rate (hdparm -t /dev/hda).

Hope that helps, Stephen.

---

### Post by Data on 2005-07-16
[QUOTE=StephenTidey]Hiya Aurels,

I too have installed Linux on my Targa (but I must confess it's not ubuntu) and I had the same problem of it going VERY slowly.

I found the problem was the kernel was using the default IDE driver and had not enabled DMA - so I upgraded to v2.6.10 and this one used the ATIIXP IDE driver which in turn enabled DMA and my throughput went from 1MB to 30MB transfer rate (hdparm -t /dev/hda).
[/QUOTE]

Oook, my throughput is between 500-600KB... But, atiixp.ko is there. The question now is, how to load it as the right driver for the disk...

Data

PS: Using Hoary...

---

