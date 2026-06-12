---
title: "Hard disk stops responding"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by danbert on 2007-11-03
I installed Gusty Gibbon and am having a problem with my hard drive.  It takes forever to get anything done.  IO wait spikes and makes the system unusable for minutes at a time.  I have not been able to pin down the problem and have modified the power management for the drive, and it has not helped.  Is there a reason my hard drive stops responding when I try to access it?

Some info to track down the problem:
```
fleckdaj@fleckdaj-laptop:~$ sudo hdparm -tT /dev/sda

/dev/sda:

 Timing cached reads:   1362 MB in  2.00 seconds = 681.04 MB/sec
 Timing buffered disk reads:   80 MB in  3.01 seconds =  26.55 MB/sec
fleckdaj@fleckdaj-laptop:~$ sudo hdparm -i /dev/sda1

/dev/sda1:

 Model=TOSHIBA MK8025GAS                       , FwRev=KA023A  , SerialNo=           55HL8964T
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=48
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6

Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
fleckdaj-laptop  2G 14602  43 14931   5  6968   3 15385  37 16217   4  63.9   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
fleckdaj-laptop,2G,14602,43,14931,5,6968,3,15385,37,16217,4,63.9,0,16,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++

```

Concerns I saw: BuffSize was 0kB.  Does my drive not have a write/read buffer?  Could the lack of buffer detection be slowing the system?

---

### Post by john280z on 2007-11-03
danbert,

   I did some Googling on "TOSHIBA MK8025GAS hdparm" and noted that this hard disk seems to be a slow one, many hits.

Many hdparms show similar speeds to yours.

this forum shows the same sort of problems:
[http://www.webservertalk.com/archive242-2007-5-1902853.html](http://www.webservertalk.com/archive242-2007-5-1902853.html)

this site has some hdparm tuning suggestions ( at bottom) that might help.
[http://www.michaels-website.de/s270.html](http://www.michaels-website.de/s270.html)

Also most show BuffType=unknown, BuffSize=0kB as yours does.

johnm

---

### Post by danbert on 2007-11-03
Thanks, those links have some useful information.  I will try changing some fstab options, but I know it isn't the drive/CPU combination that's the problem because this wasn't an issue before Fiesty.  So maybe there was a new driver added that causes a conflict?

I have some additional info from the startup log
```
[    3.612000] scsi0 : ata_piix
[    3.612000] scsi1 : ata_piix
[    3.612000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011100 irq 14
[    3.612000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011108 irq 15
[    4.132000] ata1.00: ATA-6: TOSHIBA MK8025GAS, KA023A, max UDMA/100
[    4.132000] ata1.00: 156301488 sectors, multi 16: LBA 
[    4.576000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.576000] sd 0:0:0:0: [sda] Write Protect is off
[    4.576000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.576000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.576000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.576000] sd 0:0:0:0: [sda] Write Protect is off
[    4.576000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.576000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   45.012000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   45.012000] ata1.00: cmd c8/00:08:f0:a4:14/00:00:00:00:00/e7 tag 0 cdb 0x1e data 4096 in
[   45.012000]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)
[   45.012000] ata1: soft resetting port
[   45.540000] ata1.00: configured for UDMA/100
[   45.736000] ata1.01: configured for UDMA/33
[   45.736000] ata1: EH complete
```

The part that I think might be the problem is the:
[   45.012000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   45.012000] ata1.00: cmd c8/00:08:f0:a4:14/00:00:00:00:00/e7 tag 0 cdb 0x1e data 4096 in
[   45.012000]          res 40/00:03:00:00:20/00:00:00:00:00/b0 Emask 0x4 (timeout)

Any idea what that means?

---

### Post by danbert on 2007-11-06
I looked around some more on google for other similar problems.  Some people reported that their drives worked fine with 2.6.19 kernels.  I tried this, and it did not solve the problem.  Any ideas what other changes in fiesty and gutsy could have caused this to become an issue?

---

### Post by danbert on 2007-11-11
I have been trying out other distros to see if they have the problem.  It seems that any distro that comes with kernel 2.6.20 or later has the problem.  I have tried Fiesty, Gutsy, and Fedora 8.  Debian worked fine, but as it didn't support all the hardware and has ancient software repositories, it wasn't much use.  I am going to go back to Ubuntu and try to build my own kernel to fix the problem.

---

### Post by danbert on 2007-11-12
Another update:  I am thinking it's not the kernel itself, but rather a loaded module that is causing the problem.  I built a 2.6.19.7 kernel, and it still had the same problem.  I am going to build a few more kernels and see if I can't get it working again.

---

### Post by danbert on 2007-12-03
Long time since last update.  I have Mandriva 2008 working fine on the laptop.  I still have the IO wait, but the system doesn't hang during it.  It stops new programs from loading, but already open programs are still responsive.  However, on Mandriva, laptop mode is not working correctly.  Is there some new laptop feature added in fiesty that could cause the system to stop responding while waiting on hardware?

---

