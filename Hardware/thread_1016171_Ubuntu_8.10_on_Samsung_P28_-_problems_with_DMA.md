---
title: "Ubuntu 8.10 on Samsung P28 - problems with DMA"
date: 2008-12-19
forum: Hardware
---

### Post by vladimirkondratyev on 2008-12-19
Hallo All,

I've installed Ubuntu 8.10 on Samsung P28 (relatively old laptop). I/O operations such as file copying is _very_ slow: about 2-4 MB / sec and CPU load is 100%. File system is ext3 (everything is installed with default options). I have feeling that UDMA is not working.

sudo hdparm -i /dev/sda1

prints the following

/dev/sda1:

 Model=SAMSUNG MP0402H                         , FwRev=UC100-11, SerialNo=S077J10XB16581      
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=78242976
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

-----------------------------------------------------

The attempt to manually turn DMA on also prints errors:

sudo hdparm -d1 /dev/sda1

/dev/sda1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

Any help is _very_ appreciated. I do not want to return back to Windows XP :(

Best regards,
Vladimir

---

### Post by vladimirkondratyev on 2009-01-09
Ubuntu is successfully uninstalled and Windows XP now works just fine :)

---

### Post by RedRecidivist on 2010-05-20
Who knows whether you'll still get this so long later, but just an FYI that I use Ubuntu 10.04 32-bit on a Samsung P28 and it works very very nicely, just one or two tiny niggles.

Maybe it's time for you to ditch XP again? ;)

---

