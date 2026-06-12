---
title: "Problem with cdrom after custom kernel installation"
date: 2006-08-29
forum: Hardware &amp; Laptops
---

### Post by raffytaffy on 2006-08-29
my dvd normally burns @ x8 max. with normal kernel ..however when i install custom one..i get terrible speed...now i made sure dma was on..and i sed hdparm to see its output..here are some tests i ran:
raf@vaio:~$ sudo hdparm -tT /dev/cdrom

/dev/cdrom:
read() failed: Input/output error
 Timing buffered disk reads:  read() failed: Input/output error
BLKFLSBUF failed: Function not implemented

raf@vaio:~$ hdparm -i /dev/cdrom

/dev/cdrom:

 Model=MATSHITAUJ-840D, FwRev=1.00, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode

can anyone see any problems in there that might make it run @ x1 even thou im seeting it to run @ x8 via nautilus and k3b settings?

---

### Post by raffytaffy on 2006-08-29
Update...i turned dma on ...it seems it was off in the nwe kernell..even thou i was sure it was on...and changed speed in nautilous...even thou i thought it was on 8x..and now it works ok

---

