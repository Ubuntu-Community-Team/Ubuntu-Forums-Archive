---
title: "intrepid completely unresponsive while  transfer or extract files"
date: 2009-01-30
forum: Hardware
---

### Post by ykpaiha on 2009-01-30
Hi!
As said in the title, my system hang completely unresponsive while  transfer or extract files on my internal sata disk or on a usb key board.
Booting in intrepid is good as long as i don't copy oy extract a file...
  Monitoring the system does not show a lot as memory or cpu uses they stay below 25 % ??
hdparm -tT gives me this result
 /dev/sda:
 Timing cached reads:   7046 MB in  2.00 seconds = 3526.36 MB/sec
 Timing buffered disk reads:  248 MB in  3.03 seconds =  81.87 MB/sec

/dev/sda:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 60801/255/63, sectors = 976773168, start = 0

And the iv=
/dev/sda:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 60801/255/63, sectors = 976773168, start = 0

 Model=MAXTOR STM3500320AS                     , FwRev=MX15    , SerialNo=            9QM18DEP
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

I changed as well the buffer size from 60 to 100 without any result.
if someone has a clue  thank you.

---

