---
title: "Ubuntu Breeze on Thinkpad 570"
date: 2006-03-11
forum: Hardware &amp; Laptops
---

### Post by Milambar on 2006-03-11
Got everything working, but, it seems to be in "hypersafe" mode. I mean...

hdparm -t /dev/hda

/dev/hda:
 Timing buffered disk reads:   34 MB in  3.13 seconds =  3.86 MB/sec

I repeated this 5 times, the average speed is 4.26MB/sec

This is hellishly slow.

I've tried tinkering with hdparm -d1 -X68, but it doesn't appear to make any improvements. Anyone able to help?

Additional information:
> 
 Model=IBM-DARA-212000, FwRev=AR4IA52A, SerialNo=AH0AHPZ4991
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=7944/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=418kB, MaxMultSect=16, MultSect=off
 CurCHS=7944/16/63, CurSects=8007552, LBA=yes, LBAsects=8007552
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2 udma3 udma4
 AdvancedPM=yes: mode=0x9F (159) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-4 T13 1153D revision 17:  1 2 3 4

0000:00:06.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)


Many thanks

Milambar

Many thanks.

---

