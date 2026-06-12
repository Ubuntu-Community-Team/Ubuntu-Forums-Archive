---
title: "no DMA mode for my disk."
date: 2008-05-25
forum: Hardware
---

### Post by Andre-D on 2008-05-25
> andre@Ubuntu:/dev$ sudo hdparm  /dev/sda

/dev/sda:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 14593/255/63, sectors = 234441648, start = 0


I cannot enable DMA mode,:

> andre@Ubuntu:/dev$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device


Please help, this is a rather new laptop, Travelmte 4233, Centrino chipset.  - Ubuntu 8.04

---

### Post by Andre-D on 2008-05-26
It seems I am using DMA mode anyway:

> andre@Ubuntu:~$ sudo hdparm  -i /dev/sda

/dev/sda:

 Model=TOSHIBA MK1234GSX                       , FwRev=AH001J  , SerialNo=           X68PT0HPT
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=234441648
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode



and the speed is:

> andre@Ubuntu:~$ sudo hdparm  -tT /dev/sda

/dev/sda:
 Timing cached reads:   1620 MB in  2.00 seconds = 809.65 MB/sec
 Timing buffered disk reads:  104 MB in  3.05 seconds =  34.09 MB/sec


---

