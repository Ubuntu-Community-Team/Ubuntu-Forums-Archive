---
title: "hdparm settings to improve performance of notebook hard disk?"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by hardhu on 2006-10-23
Hello everybody,
I have recently installed a new 7200 rpm hard disk in my laptop, and I was asking myself if I should do some work with hdparm to improve its performances. 
Here's some informations:


user@eagle:/opt$ sudo hdparm -i /dev/hda

/dev/hda:

 Model=HTS721010G9AT00, FwRev=MCZOA51A, SerialNo=MPC0B2Y0GGVSME
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=7539kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=195371568
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 3a:  ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode

and here a test:

user@eagle:/opt$ sudo hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   1948 MB in  2.00 seconds = 972.73 MB/sec
 Timing buffered disk reads:  148 MB in  3.03 seconds =  48.83 MB/sec

I have noticed that:
1) IO_support   =  0 (default 16-bit); should I set it to 1 or 3?
2) it seems hdparm service is not started at boot by default at boot in (K)Ubuntu? is this correct? I think then I would have to do some modifications to /etc/hdparm.conf and to enable that service at startup to make configurations changes persistent, am I right?

---

### Post by lloyd_b on 2006-10-23
As I understand it, the "3" option is more likely to work on a given machine, but the "1" option has slightly faster performance.  The only way to determine what is best in your machine is to experiment (I STRONGLY recommend having a backup available before doing this).

Boot in recovery mode, login to the text console, set the value and run the tests from there.  Hopefully if you hit an incompatible mode, there won't be any filesystem corruption.

In addition to the IO_support, you may gain a performance boost by changing the "MultSect" (via the "-m" option).  Your drive supports a MultSect setting of 16, but it's currently set to 0.

I never even bother setting up the hdparm service - I just add the hdparm line(s) into "/etc/init.d/rc.local".

Lloyd B.

---

### Post by esaym on 2006-10-24
> **lloyd_b said:**
> As I understand it, the "3" option is more likely to work on a given machine, but the "1" option has slightly faster performance.  The only way to determine what is best in your machine is to experiment (I STRONGLY recommend having a backup available before doing this).

Boot in recovery mode, login to the text console, set the value and run the tests from there.  Hopefully if you hit an incompatible mode, there won't be any filesystem corruption.

In addition to the IO_support, you may gain a performance boost by changing the "MultSect" (via the "-m" option).  Your drive supports a MultSect setting of 16, but it's currently set to 0.

I never even bother setting up the hdparm service - I just add the hdparm line(s) into "/etc/init.d/rc.local".

Lloyd B.
"MultSect setting of 16,"

Any where we can look up the allowed parameters of our hard drives?  Or is it all just an experiment?

---

### Post by lloyd_b on 2006-10-25
> "MultSect setting of 16,"

Any where we can look up the allowed parameters of our hard drives? Or is it all just an experiment?

"hdparm" will tell you what the max is for this particular setting:

```
lloyd@laptop:~$ sudo hdparm -i /dev/hda
Password:

/dev/hda:

 Model=IBM-DARA-209000, FwRev=AR3OA51A, SerialNo=AG0AGL09647
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=418kB, MaxMultSect=16, MultSect=8
 CurCHS=17475/15/63, CurSects=16513875, LBA=yes, LBAsects=17660160
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-4 T13 1153D revision 17:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4

 * signifies the current active mode
```

If you look on the 4th line of the output (the one starting with "BuffType"), it shows this drive can support a MultSect ("MaxMultSect") setting of 16, but that's its currently set to 8 (Don't ask me why, but the drive runs faster with the setting at 8 than it does at 16).

Lloyd B.

---

### Post by esaym on 2006-10-25
Ohhh I missed that.  Is there a better way to benchmark the hard drive then just using the hdparm -Tt option?  Seems like what ever I change it doesn't really change the speed shown in the -Tt test.

Thanks!

---

### Post by lloyd_b on 2006-10-25
> Ohhh I missed that. Is there a better way to benchmark the hard drive then just using the hdparm -Tt option? Seems like what ever I change it doesn't really change the speed shown in the -Tt test.

Try installing the "bonnie++" package.  That program uses a MUCH more complex method of testing drive performance...

Also, be sure to do all testing when booted in recovery mode.  If there are other programs accessing the disk, any performance testing program is going to produce unreliable results...

Lloyd B.

---

### Post by esaym on 2006-10-26
It actually looks like most of the options are for legacy reasons.  The only thing that might make a difference in theory would be hdparm -u1 from what I read:

[http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance](http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance)

---

