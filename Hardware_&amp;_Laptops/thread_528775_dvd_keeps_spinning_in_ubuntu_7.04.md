---
title: "dvd keeps spinning in ubuntu 7.04"
date: 2007-08-18
forum: Hardware &amp; Laptops
---

### Post by vtom80 on 2007-08-18
Hi,
I recently upgraded from ubuntu 6.04 to 7.04 on my acer TravelMate 4001 WLMi. Everything starts to work well, I even got my acer hot keys to work (after ~ 2 hours of work). 
But I have a problem with my dvd. When I insert a dvd, it keeps spinning without stopping, which was not the case with ubuntu 6.04. 
I suppose I can modify the spindown time of the device by doing (for setting the spindown time to 1 minute)
```
   sudo hdparm -S 12 /dev/dvd
```
but I get:
```
/dev/dvd:
 setting standby to 12 (1 minutes)
 HDIO_DRIVE_CMD(setidle1) failed: Input/output error
```
Requesting information by 
```
sudo hdparm -i /dev/dvd
```

results in:
```
/dev/dvd:

 Model=QSI     DVDRW SDW-042                   , FwRev=DX70    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no

 * signifies the current active mode

```

Does this means that the dvd lacks a proper driver?
Any suggestions/comments? Anyone had the same problem?

Thanks,
tom

---

### Post by vtom80 on 2007-08-20
Hi everybody.

I found out that probably some bug in the 2.6.20-16 kernel causes the dvd to keep spinning... When I start in the -15 kernel, I have no troubles...
It is not the only bug in -16. Also the battery monitor seems not to work in -16, but works in -15. Several people already complained about this on the forum. So have patients till -17 arrives ;-)

Bye

---

