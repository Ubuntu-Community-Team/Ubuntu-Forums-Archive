---
title: "why cant i achieve udma5 in linux?... i can in windows?"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by hardyn on 2007-05-30
anybody? i found out the hard way that my machine will not support udma 5 under linux; however windows reports that it is using mode 5?

---

### Post by hardyn on 2007-05-30
bump

---

### Post by regor-paname on 2007-06-13
Same for me since feisty 7.04 (worked before), my HD is now in udma2 (or udma 33) :o

edit : but it's udma5 under recovery mode ...?

---

### Post by regor-paname on 2007-06-24
bump

---

### Post by logos34 on 2007-06-24
what does the command
> [B]
sudo hdparm -v -i /dev/hda[/B]

show? (replace 'hda' with your drive if diff)

---

### Post by regor-paname on 2007-06-26
>  sudo hdparm -v -i /dev/sda

/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 12161/255/63, sectors = 195371568, start = 0

 Model=FUJITSU MHV2100AT                       , FwRev=00000096, SerialNo=        NS84T58262A4
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=195371568
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma3 udma4 *udma5 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 3a:  ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode

thanks logos :D
Since i've download the last linux header, my HDA re-became SDA and everything go back to normal (udma5 is working)

---

