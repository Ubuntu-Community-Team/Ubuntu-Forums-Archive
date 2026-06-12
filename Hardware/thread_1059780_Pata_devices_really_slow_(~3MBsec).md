---
title: "Pata devices really slow (~3MB/sec)"
date: 2009-02-04
forum: Hardware
---

### Post by Tuna-Fish on 2009-02-04
I'm having some weird trouble with my new intrepid installation. I have 4 ata devices, 2 of which are Sata hard disks, which work fine, and the rest being a pata dvd burner and an old pata hard disk.

As long as I only touch the Sata disks, everything works smooth, even when doing massive IO, but any io that is done to the pata devices instantly makes the machine very sluggish, as in mouse only moves every second or so. Also any such IO is very slow to complete - hdparm -t /dev/sda says "Timing buffered disk reads:   10 MB in  3.02 seconds =   3.31 MB/sec"

Can anyone help me?


```

hdparm /dev/sda
/dev/sda:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 24792/255/63, sectors = 398297088, start = 0

```

```

hdparm -i /dev/sda

/dev/sda:

 Model=Maxtor 6B200P0                          , FwRev=BAH41B10, SerialNo=B40625MH            
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=398297088
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

```

---

