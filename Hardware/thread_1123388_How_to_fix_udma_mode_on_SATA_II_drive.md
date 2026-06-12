---
title: "How to fix udma mode on SATA II drive?"
date: 2009-04-12
forum: Hardware
---

### Post by Cruz on 2009-04-12
Hello folks,

I have a 1TB Samsung HD103SI drive in my machine. The drive is very new, it's not even supported by HUTIL yet. :(

The thing is, when playing around with hdparm I seem to have screwed up the udma mode. 

# hdparm -i /dev/sdb

/dev/sdb:

 Model=SAMSUNG HD103SI                         , FwRev=1AG01113, SerialNo=S1Y5J1NS124455      
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=32767kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5 udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7


See how it's set to udma2?

The benchmarks show how sluggish it is:

# hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   618 MB in  2.00 seconds = 308.73 MB/sec
 Timing buffered disk reads:  114 MB in 32.19 seconds =   3.54 MB/sec



I'm absolutely sure that this was not the case from the beginning. After I chucked the drive into my machine the first thing I have done was testing it with hdparm -tT and the results were sweet. Then I played around with AAM, APM and spin down time. A day later, when I wanted to transfer some files via ftp I found that the drive is slow and the transfer is stalling like every minute. And now I can't set the udma mode back anymore!

hdparm -X udma6 /dev/sdb

/dev/sdb:
setting xfermode to 70 (UltraDMA mode6)
HDIO_DRIVE_CMD(setxfermode) failed: Input/output error


Now how do I get my drive back?

---

### Post by jesterthejedi on 2010-03-07
Mine is set to udma5, after reading the man hdparm, you add 64 to the mode #. My drive wouldn't take the change though.

Just reading about modes and the thought occured to me that udma6 is only possible with 80 wire cable, ie not the sata cable. So you could try 64+5, or -X 69 and see if that sticks.

---

