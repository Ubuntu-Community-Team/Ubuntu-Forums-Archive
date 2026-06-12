---
title: "Very slow HD transfer on main partition (was fine few days ago?!)"
date: 2009-09-06
forum: Hardware
---

### Post by Vric on 2009-09-06
Hi,

 I have build an HTPC/NAS computer 
Pentium Dual Core 6300 (2.8Ghz) 
Asus P5N7A-VM
2Gb DDR2
1x 160gb WD 2.5" drive
4x 1Tb WD Green on Areca 1220 Raid Card.
Ubuntu Jaunty

It's been working flawless for the last 2-3 weeks, but since yesterday, the speed of the file transfer have droper to 1.6Mb/sec 1.7Mb/sec max.

UBuntu is very slow (nearly impossible to work with) if I transfer a huge file.

Another thing that might be important: Since it was slow, I rebooted it this morning and NVidia driver were gone. I had to reinstall them.


IF I do benchmark test, everything looks fine:

```

vric@htpc:~$ sudo hdparm -t /dev/sda

/dev/sda:
 Timing buffered disk reads:  184 MB in  3.00 seconds =  61.31 MB/sec

vric@htpc:~$ sudo hdparm -t /dev/sdb

/dev/sdb:
 Timing buffered disk reads:  764 MB in  3.01 seconds = 254.19 MB/sec


```DMA seem active:

```
vric@htpc:~$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=WDC WD1600BEVT-75ZCT2                   , FwRev=11.01A11, SerialNo=     WD-WX*********
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=312581808
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

```But yet, if I transfer a file from sda1 to anywhere (same hard drive, sdb1 or even network) speed is maxed at 1.7Mb/sec.

If I copy a file from sdb1 (raid array) to sda1, speed is about 45Mb/sec. So problem is only reading on sda drive.

As I said, I'm new to Linux/Ubuntu, I tried my best to setup everything without asking help. but I'm stuck right now.

Thanks for help!

---

### Post by Vric on 2009-09-09
Help? :(

---

