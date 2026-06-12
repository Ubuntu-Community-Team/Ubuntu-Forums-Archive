---
title: "Sata hard drive slow"
date: 2008-06-04
forum: Hardware
---

### Post by caprilo on 2008-06-04
I use Hardy and recently bought a Sata ii Seagate Drive of 320GB. Having heard of the speed of these drives compared to the ones of IDE, I thought my system would be much more quick (I re-installed Hardy on the new drive). I found it was slower. I found something about the hdparm tool, and made the test, with the following results:

with my old IDE drive:
 Timing cached reads:   1568 MB in  2.00 seconds = 783.71 MB/sec
 Timing buffered disk reads:  166 MB in  3.03 seconds =  54.77 MB/sec

and the info:

 Model=ST380011A                               , FwRev=8.01    , SerialNo=5JVGMR6T            
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 2:  ATA/ATAPI-1,2,3,4,5,6

-----------------------------------------------------------

with my new SATA ii drive:
 Timing cached reads:   1220 MB in  2.00 seconds = 610.01 MB/sec
 Timing buffered disk reads:  200 MB in  3.02 seconds =  66.12 MB/sec

and the info:

 Model=ST3320620AS                             , FwRev=3.AAK   , SerialNo=            6QF3M4GD
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=625142448
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

-----------------------------------------------------------

Furthermore, the speed of the sata is very variable (I ran the tests about ten times). This was the highest I got for the SATA. The numbers for the IDE do not vary so much.

Should I contact the drive vendor, or is it an Ubuntu bug and I should change of distribution? I have read other threads about problems with this drives.

---

