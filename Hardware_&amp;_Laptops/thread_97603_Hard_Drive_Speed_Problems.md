---
title: "Hard Drive Speed Problems"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by Zlobadon on 2005-12-01
Hello,

I recently installed Ubuntu on a system that has 2 HDDs and immediately noticed something is fishy regarding the speed.  (8-10 minutes just for bootup).

I ran a hdparm -tT and discovered this:

/dev/hda:
 Timing cached reads:   1032 MB in  2.00 seconds = 515.82 MB/sec
 Timing buffered disk reads:    2 MB in  3.83 seconds = **[SIZE="4"]534.39 kB/sec[/SIZE]**

/dev/hdb:
 Timing cached reads:   1032 MB in  2.00 seconds = 515.31 MB/sec
 Timing buffered disk reads:  162 MB in  3.02 seconds =  53.62 MB/sec

I thought that perhaps it was not being recognized and access as the Ultra DMA 100 drive that it is, but hdparm -i tells me this:

/dev/hda:

 Model=IC35L060AVER07-0, FwRev=ER6OA46A, SerialNo=SZ0SZD00747
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=40
 BuffType=DualPortCache, BuffSize=1916kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=120103200
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-5 T13 1321D revision 1:

 * signifies the current active mode


/dev/hdb:

 Model=IC35L120AVV207-1, FwRev=V24OA66A, SerialNo=VNVD09G4GZALVT
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=52
 BuffType=DualPortCache, BuffSize=7965kB, MaxMultSect=16, MultSect=off
 CurCHS=65535/1/63, CurSects=4128705, LBA=yes, LBAsects=241254720
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 3a:

 * signifies the current active mode

I'm stumped at the moment.  The only thing that seemed even close at the moment was this post: [http://ubuntuforums.org/archive/index.php/t-23988.html](http://ubuntuforums.org/archive/index.php/t-23988.html) but there's no resolution.

Any insight is greatly appreciated!

---

