---
title: "weird slow read speeds on HD"
date: 2009-06-30
forum: Hardware
---

### Post by zackpete on 2009-06-30
I'm trying to copy files from one hard drive to another, and I'm getting really slow copy speeds (<10MB/s). The weird thing is when I copy a file a second time (like to the same place with a different filename) it copies at the rated speed of my hard drives (~110MB/s). I had a problem earlier this week with a DVD drive with the DMA mode randomly going off, but I doubt it's related as both drives appear to have DMA enabled.

```
$ sudo hdparm -itT /dev/sda

/dev/sda:

 Model=ST31000528AS                            , FwRev=CC34    , SerialNo=            6VP0AH23
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode

 Timing cached reads:   13356 MB in  2.00 seconds = 6684.78 MB/sec
 Timing buffered disk reads:  344 MB in  3.01 seconds = 114.12 MB/sec

```
```
$ sudo hdparm -itT /dev/sdb

/dev/sdb:

 Model=ST31000528AS                            , FwRev=CC34    , SerialNo=            6VP073YN
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode

 Timing cached reads:   14430 MB in  2.00 seconds = 7223.49 MB/sec
 Timing buffered disk reads:  362 MB in  3.01 seconds = 120.41 MB/sec

```

---

