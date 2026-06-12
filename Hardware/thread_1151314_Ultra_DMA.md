---
title: "Ultra DMA?"
date: 2009-05-06
forum: Hardware
---

### Post by adamitj on 2009-05-06
I noticed my instalations of Ubuntu are consuming too much processor resources (peaks of 100%) when I am copying a big file (like 1 GB or more). The system just hangs up, and I can't work succesfully.

When I used Windows XP and Vista, this behavior only appeared when Ultra DMA where disabled (only annoying conditions).

Is there a way to bypass this processor usage and checkout if Ultra DMA is activated?

My notebook:
- Processor AMD Turion X2 TL-58 1.9;
- Disk 160 GB / 5400rpm;
- 2 GB of RAM.

Note: My workstation at work with a similar configuration does the same.

---

### Post by adamitj on 2009-05-13
I was very rookie regarding hard disk maintenance in Linux. So I found some resources to check out DMA settings:

```
hdparm -i /dev/sda
```

And the result was:

```
/dev/sda:

 Model=ST3250820AS                             , FwRev=3.AAE   , SerialNo=            5QE2VP7N
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=488397168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode
```

Now I noticed Ultra DMA is activated, but why in this world the file transfer is so sloooooow?

I observed another issue too: when navigating on the disk tree from Nautilus, every time I open a folder with approximately 200 itens, CPU usage jumps to 100%. And this behavior is reproduced into my notebook and my desktop machines.

Any ideas?

---

### Post by Arkold Thos on 2009-09-30
Same happens here, udma is enabled but transfer is VERY VERY slow, any clue?

> david@arkpc:~$ sudo hdparm -i /dev/sda
[sudo] password for david:

/dev/sda:

 Model=WDC WD5000AAKS-22YGA0                   , FwRev=12.01C02, SerialNo=     WD-WCAS84888424
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

david@arkpc:~$ sudo hdparm -i /dev/sda1

/dev/sda1:

 Model=WDC WD5000AAKS-22YGA0                   , FwRev=12.01C02, SerialNo=     WD-WCAS84888424
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

david@arkpc:~$ sudo hdparm -i /dev/sda2

/dev/sda2:

 Model=WDC WD5000AAKS-22YGA0                   , FwRev=12.01C02, SerialNo=     WD-WCAS84888424
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

---

### Post by Arkold Thos on 2009-09-30
Same happens here, udma is enabled but transfer is VERY VERY slow, any clue?

> david@arkpc:~$ sudo hdparm -i /dev/sda
[sudo] password for david:

/dev/sda:

 Model=WDC WD5000AAKS-22YGA0                   , FwRev=12.01C02, SerialNo=     WD-WCAS84888424
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

david@arkpc:~$ sudo hdparm -i /dev/sda1

/dev/sda1:

 Model=WDC WD5000AAKS-22YGA0                   , FwRev=12.01C02, SerialNo=     WD-WCAS84888424
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

david@arkpc:~$ sudo hdparm -i /dev/sda2

/dev/sda2:

 Model=WDC WD5000AAKS-22YGA0                   , FwRev=12.01C02, SerialNo=     WD-WCAS84888424
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

---

