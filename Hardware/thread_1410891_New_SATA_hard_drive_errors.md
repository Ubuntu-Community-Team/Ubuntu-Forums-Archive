---
title: "New SATA hard drive errors"
date: 2010-02-19
forum: Hardware
---

### Post by davidshere on 2010-02-19
I am running a Western Digital TSD-1000EADS DH hard drive.  It is not my system drive.  My PCChipps M830LR motherboard (circa 2001) has no SATA controller, so I am using a StarTech PCIESATA2I PCI Card.  during periods of disk activity, I have been getting these errors in /var/log/syslog:

```

Feb 19 09:05:35 thebone kernel: [50918.164220] ata1.00: exception Emask 0x12 SAct 0x0 SErr 0x1000500 action 0x2
Feb 19 09:05:35 thebone kernel: [50918.164265] ata1.00: BMDMA stat 0x5
Feb 19 09:05:35 thebone kernel: [50918.164283] ata1: SError: { UnrecovData Proto TrStaTrns }
Feb 19 09:05:35 thebone kernel: [50918.164309] ata1.00: cmd 25/00:00:7f:71:9b/00:01:14:00:00/e0 tag 0 dma 131072 in
Feb 19 09:05:35 thebone kernel: [50918.164311]          res 51/84:af:7f:71:9b/84:00:14:00:00/e0 Emask 0x12 (ATA bus error)
Feb 19 09:05:35 thebone kernel: [50918.164342] ata1.00: status: { DRDY ERR }
Feb 19 09:05:35 thebone kernel: [50918.164358] ata1.00: error: { ICRC ABRT }
Feb 19 09:05:35 thebone kernel: [50918.487372] ata1: soft resetting link
Feb 19 09:05:35 thebone kernel: [50918.647235] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Feb 19 09:05:35 thebone kernel: [50918.707356] ata1.00: configured for UDMA/33
Feb 19 09:05:35 thebone kernel: [50918.707385] ata1: EH complete
Feb 19 09:05:35 thebone kernel: [50918.724057] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
Feb 19 09:05:35 thebone kernel: [50918.724082] sd 0:0:0:0: [sda] Write Protect is off
Feb 19 09:05:35 thebone kernel: [50918.724087] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 19 09:05:35 thebone kernel: [50918.724115] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

This problem does not seem to result in corrupt data on the drive; I have several ~12GB torrents that consistently pass their hash checks.  The only identifiable problem resulting from these errors (other than the console being unusable because the errors continuously scroll the screen) is that file reading/writing consumes large amounts of system resources.  Sometimes simply copying a file can result in load ratios of around 3.00.  

Things I have tried so far, and other observations:
1.  I have run a complete fsck, with the -f option.  It said "File System Modified", but did not indicate that there were any problems otherwise.
2.  I have looked at this page: [http://ata.wiki.kernel.org/index.php/Libata_error_messages](http://ata.wiki.kernel.org/index.php/Libata_error_messages) and I think what the error message are telling me is that there is a communications error between the PCI bus and the controller card, but getting down to that level is a little over my head.
3.  I jumpered this down to 1.5 from 3, its default, when I was trying to install it in a different machine.  I ultimately gave up on that because Ubuntu could not successfully start up with the drive and controller card in the computer.  It is still jumpered down.
4.  When if first got the drive, I put it in the same hardware and was using it under windows (again not the system drive) formatted as NTFS.  It did not appear to have any problems, however I did not look at the Windows logs.
5.  I have tried at least one other SATA cable.
6.  I have tried a different hard drive, and that one does not experience these problems.  It was ntfs, not ext3.
7.  I have tried installing this drive and card in another computer, a Dell Dimension 3000 (circa 2005).  In this new setup, this drive was still a data drive and another drive served as the system drive (similar to the previous machine).  OS was fresh install of Hardy.  Same problem.  I upgraded the machine to Lucid, same problem.
8.  My scenario for testing the drive involves copying a large file from one directory to another, or making a copy in the same directory.  The errors show up when the copy starts, and if I abort the copy, the errors stop.  If I repeat the same action, the errors do NOT show up right away.  Some sort of cache?

Right now there is no irreplacable data on the drive.  It's about half full.

---

### Post by europa on 2010-02-22
Interface CRC error during Ultra DMA transfer - often either a bad cable or power problem, though possibly an incorrect Ultra DMA mode setting by the driver

---

### Post by davidshere on 2010-03-01
How do I change the "Ultra DMA mode setting"?

---

### Post by davidshere on 2010-03-05
bump

because I added #6:

6. I have tried a different hard drive, and that one does not experience these problems. It was ntfs, not ext3.

---

### Post by davidshere on 2010-03-15
This is Western Digital's response:

[I]Western Digital technical support only provides jumper configuration and physical installation support for hard drives used in systems running the Linux/Unix operating systems. For setup questions beyond physical installation of your Western Digital hard drive, please contact the vendor of your Linux/Unix operating system. As a suggestion, please test the drive on a Windows environment with a built in SATA connection.
[/I]

---

### Post by davidshere on 2010-04-17
I hope y'all don't mind if I bump this one more time...

---

### Post by davidshere on 2010-05-12
bumped for adding #7 and #8.  I'm starting to wonder if I should file a bug...

---

### Post by hal8000 on 2010-05-12
Your last question was how do I change UDMA mode.
Normally the hdparm program sets these options on IDE/PATA drives.
there is a similar program sdparm for SATA drives.

However I would suggest using hapr, -i option to first see what settings your HD uses, example below:

[root@orac anc]# hdparm -i /dev/sda

/dev/sda:

 Model=Hitachi HDS721616PLA380, FwRev=P22OABEA, SerialNo=PVG904ZFTBZJDV
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=52
 BuffType=DualPortCache, BuffSize=7376kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=312581808
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 1:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode


My SATA  type 1 drive is automatically set to use udma6 mode and timing
can be found using the -tT  options, example below:

[root@orac anc]# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1982 MB in  2.00 seconds = 991.21 MB/sec
 Timing buffered disk reads:  226 MB in  3.02 seconds =  74.85 MB/sec


There is another thread on this:
[http://ubuntuforums.org/showthread.php?t=844717](http://ubuntuforums.org/showthread.php?t=844717)

It also states that hdparm is for IDE drives only and that SATA drives are already tuned for optimum performance. Try also searching google for SATA tuneup using sdparm

---

### Post by davidshere on 2010-05-12
Thanks!  I'll investigate that.  This is the current configuration:
```

david@thebone:~$ sudo hdparm -i /dev/sdd
[sudo] password for david:

/dev/sdd:

 Model=WDC WD10EADS-65M2B0                     , FwRev=01.00A01, SerialNo=     WD-WCAV53094176
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=32767kB, MaxMultSect=16, MultSect=?0?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5 udma6
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

david@thebone:~$ sudo hdparm -tT /dev/sdd

/dev/sdd:
 Timing cached reads:   344 MB in  2.01 seconds = 171.32 MB/sec
 Timing buffered disk reads:   16 MB in  3.00 seconds =   5.33 MB/sec

david@thebone:~$ sudo sdparm -i /dev/sdd
    /dev/sdd: ATA       WDC WD10EADS-65M  01.0
Device identification VPD page:
  Addressed logical unit:
    designator type: vendor specific [0x0],  code set: ASCII
 00     20 20 20 20 20 57 44 2d  57 43 41 56 35 33 30 39         WD-WCAV5309
 10     34 31 37 36                                         4176
    designator type: T10 vendor identification,  code set: ASCII
      vendor id: ATA
      vendor specific: WDC WD10EADS-65M2B0                          WD-WCAV53094176

```

---

### Post by davidshere on 2010-05-12
I just tried the drive in a Dell Dimension E521, and did not use the PCI controller card, because the motherboard has an onboard SATA controller.  I experienced no errors.  I then tried the drive in the same computer using the PCI controller card, and the errors came back.  

So it's either the card, or this particular card/drive combination.  I previously tried a Seagate ST380819AS SATA drive with this card, and did not experience the errors.  (As I mentioned in #6 of my original post).

The speeds are much better:

```
david@bone-test:~$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   1516 MB in  2.00 seconds = 757.52 MB/sec
 Timing buffered disk reads:  302 MB in  3.03 seconds =  99.81 MB/sec
david@bone-test:~$ sudo hdparm -i /dev/sdb

/dev/sdb:

 Model=WDC WD10EADS-65M2B0                     , FwRev=01.00A01, SerialNo=     W                                                    D-WCAV53094176
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=32767kB, MaxMultSect=16, MultSect=?0?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

david@bone-test:/etc/apt$ sudo sdparm -i /dev/sdb
    /dev/sdb: ATA       WDC WD10EADS-65M  01.0
Device identification VPD page:
  Addressed logical unit:
    designator type: vendor specific [0x0],  code set: ASCII
 00     20 20 20 20 20 57 44 2d  57 43 41 56 35 33 30 39         WD-WCAV5309
 10     34 31 37 36                                         4176
    designator type: T10 vendor identification,  code set: ASCII
      vendor id: ATA
      vendor specific: WDC WD10EADS-65M2B0                          WD-WCAV53094                                                    176

```

My eventual solution to this problem is going to be to buy a [new barebones system]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5750049&Sku=B69-0187"), since I think the problem here basically boils down to "new hard drive on old motherboard".  I did want to test the drive on a new(ish) motherboard first, because my big fear was that I would spend the money on a new machine and this problem wouldn't go away.  Right now I feel pretty confident that that won't happen.

---

