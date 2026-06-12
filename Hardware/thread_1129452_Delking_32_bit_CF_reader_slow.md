---
title: "Delking 32 bit CF reader slow"
date: 2009-04-18
forum: Hardware
---

### Post by maestrobwh1 on 2009-04-18
I am trying to figure out if I can speed up this situation.

I have a 266x CF card mounted in a Delkin 32 Bit CF reader.

[INDENT][root@chakra brian]# hdparm -t /dev/sdc

/dev/sdc:
 Timing buffered disk reads:    4 MB in  3.33 seconds =   1.20 MB/sec
[/INDENT] 

This is somewhat pathetic.

[INDENT]hdparm -i /dev/sdc

/dev/sdc:

 Model=Memory Card Adapter                     , FwRev=67281306, SerialNo=                  0
 Config={ HardSect NotMFM Removeable DTR>10Mbs nonMagnetic }
 RawCHS=16006/16/63, TrkSize=2048, SectSize=512, ECCbytes=4
 BuffType=1Sect, BuffSize=1kB, MaxMultSect=1, MultSect=?0?
 CurCHS=16006/16/63, CurSects=16134048, LBA=yes, LBAsects=16134144
 IORDY=no, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-1,2,3,4,5,6
[/INDENT]

So I thought I might be able to do this:
[INDENT]hdparm -c1 -d1 /dev/sdc

/dev/sdc:
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 IO_support    =  0 (default)
 HDIO_GET_DMA failed: Inappropriate ioctl for device
[/INDENT]

So is there a way to get something reasonable out of this card.  It runs at a significantly higher speed in XP with the proper driver.

---

