---
title: "New motherboard, now hard drive speed abysmal"
date: 2009-04-29
forum: Hardware
---

### Post by CPColin on 2009-04-29
I just swapped out the motherboard in my Mythbuntu box to an Asrock 945GCM-S. Now, the SATA drive (sdb) runs fine but the IDE drive (sda) runs horribly slow:

```

# dmesg |grep UDMA
[    3.457023] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    3.457031] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    3.628660] ata1.00: ATA-5: Maxtor 91826U4, FA550480, max UDMA/66
[    3.628710] ata1.01: ATAPI: TSSTcorpCD/DVDW TS-H652D, GA01, max UDMA/33
[    3.644598] ata1.00: configured for UDMA/66
[    3.660318] ata1.01: configured for UDMA/33
[    3.661979] ata3: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xc880 irq 19
[    3.661983] ata4: SATA max UDMA/133 cmd 0xd000 ctl 0xcc00 bmdma 0xc888 irq 19
[    3.843484] ata3.00: ATA-7: WDC WD1600AAJS-22PSA0, 05.06H05, max UDMA/133
[    3.856435] ata3.00: configured for UDMA/133

# hdparm -i /dev/sda

/dev/sda:

 Model=Maxtor 91826U4                          , FwRev=FA550480, SerialNo=E4059YVC
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=35673120
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 *udma4
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: ATA/ATAPI-4 T13 1153D revision 17:  ATA/ATAPI-1,2,3,4,5

# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:     2 MB in  7.77 seconds = 263.71 kB/sec
 Timing buffered disk reads:    2 MB in  3.11 seconds = 659.48 kB/sec

# hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   2050 MB in  2.00 seconds = 1024.54 MB/sec
 Timing buffered disk reads:  226 MB in  3.03 seconds =  74.70 MB/sec

```

It seems like nothing fishy is going on during boot and the right UDMA mode seems to be active. Anybody else seen speeds this low?

---

