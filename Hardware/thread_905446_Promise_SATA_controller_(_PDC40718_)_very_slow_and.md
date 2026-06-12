---
title: "Promise SATA controller ( PDC40718 ) very slow and maybe buggy"
date: 2008-08-30
forum: Hardware
---

### Post by frozenjim on 2008-08-30
I am running a PDC40718 Promise SATA controller on a fresh install of Hardy.  I replaced the IDE drive for SATA because I needed more storage.  What I lost was performance.  It's tough to be sure, but my nice Hardy seems to lock up more now as well.

From what I can tell though, hdparm seems to show a fairly fast drive but it does not seem to have access to things like DMA because of the "Inappropriate ioctl for device".

Device Info:```
lspci| grep -i 'promise'
02:0d.0 Mass storage controller: Promise Technology, Inc. PDC40718 (SATA 300 TX4) (rev 02)
```
hdparm has issues with setting or getting DMA:```
hdparm /dev/sda

/dev/sda:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 60801/255/63, sectors = 976773168, start = 0
```
hdparm seems to show decent performance:```
hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1044 MB in  2.00 seconds = 521.77 MB/sec
 Timing buffered disk reads:   82 MB in  3.09 seconds =  26.50 MB/sec
```
So far, I haven't found anything to indicate what else I can do to get this PROMISE SATA driver working right.  

Anybody have anything to add?

---

### Post by z35 on 2008-12-04
I have the same issue with the same card. Ridiculously slow. A while to formate (1T) and it is taking forever to sync software raid1. 
```

02:08.0 Mass storage controller: Promise Technology, Inc. PDC40718 (SATA 300 TX4) (rev 02)

```

```

Personalities : [raid1]
md0 : active raid1 sdc1[1] sdb1[0]
      976759936 blocks [2/2] [UU]
      [>....................]  resync =  0.1% (1239296/976759936) finish=536090.2min speed=12K/sec

```

Over a year to sync...

```

hdparm -i /dev/sdb

/dev/sdb:

 Model=ST31000340AS                            , FwRev=SD15    , SerialNo=            XXXXXXXX
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode

```

```

hdparm /dev/sdb

/dev/sdb:
 IO_support    =  0 (default)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 56065/255/63, sectors = 1953525168, start = 0

```

This is on intrepid 8.10...

These are attached to ata2 and ata3 (assuming ata0 is the first one) 

Any advise?

---

### Post by z35 on 2008-12-04
Must have been a fluke of some sort, now it seems to be going normal...

```

md0 : active raid1 sdc1[1] sdb1[0]
      976759936 blocks [2/2] [UU]
      [=>...................]  resync =  7.8% (76589056/976759936) finish=253.0min speed=59281K/sec

```

---

