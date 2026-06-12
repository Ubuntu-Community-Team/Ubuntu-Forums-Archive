---
title: "slow hard disk, hdparm won't work (sata disk??)"
date: 2009-01-25
forum: Hardware
---

### Post by vajorie on 2009-01-25
First, here is my benchmarks and harddisk, because I am not quite sure if this slowness is an issue of hardware or software, but it became very pronounced after replacing Dapper (which labeled my disk as hda) with 8.04 (which labeled the disk as sda). the slowness slows down the system as it keeps waiting for io (iowait)... please let me know if you think these speeds are just normal: 

hardware:
```

$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=TOSHIBA MK1031GAS                       , FwRev=AA204A  , SerialNo=           35AW0324T
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=195371568
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode

```

The drive seems to be a "Toshiba MK1031GAS 100GB UDMA/100 4200RPM 8MB 2.5" IDE Hard Drive" ([source]("http://www.geeks.com/details.asp?InvtId=MK1031GAS-R&cpc=RECOM")) Filesystem is ext3. 

The benchmarks (?): 

```

$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   658 MB in  2.00 seconds = 329.02 MB/sec
 Timing buffered disk reads:   84 MB in  3.05 seconds =  27.54 MB/sec

```

I looked around and people seem to have 3 times the speeds above, but I'm not sure if I've got a problem or if this is just the limitations of the hard drive (cache? rpm? no idea)

I tried setting dma on, but it won't, and google says this is normal bc this is a sata drive. I have no idea if this is a sata drive or not. ay help appreciated a lot. thanks :)

---

### Post by logos34 on 2009-01-25
No, it's an IDE (PATA) drive--if it was Sata you'd see 'UDMA/150' or '3.0 GB/s', etc.

Run that benchmark a few times in a row, one after another--on mine the first couple of tests are abnormally slow for some reason.

---

### Post by electrogeist on 2009-01-27
[http://www.tomsguide.com/us/nine-notebook-hard-drives-make-their-debuts,review-358-9.html](http://www.tomsguide.com/us/nine-notebook-hard-drives-make-their-debuts,review-358-9.html)

[i]The ML1032GAS is Toshiba's first notebook drive with a total capacity of 100 GB. Unlike Seagate, Toshiba decided to stick to 4,200 RPM spindle speed. _Unfortunately, performance numbers were a bit below our expectations, despite the drive being equipped with the usual 8 MB cache. In some benchmarks, this new monster drive is the slowest._

Nevertheless, we were surprised to see that the Toshiba drive actually managed to score comparatively good results in the IOMeter suite, although other benchmarks did not fare as well. We would not want to recommend this drive as a notebook's system drive, because other models, including Toshiba's MK8026GAX, deliver better performance.

However, this drive looks very interesting when bundled with a mobile 2.5" hard drive enclosure with USB 2.0 and/or Firewire interfaces. Both interfaces usually do not provide more than 30 MB/s which is exactly where the performance range the MK1031GAS fits.[/i]

---

