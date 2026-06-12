---
title: "slow file transfer to sata hdd"
date: 2008-11-11
forum: General Help
---

### Post by angryhomer17 on 2008-11-11
I am encountering slow file transfers (3 MB/s) from sda to to sdb. I can transfer data from sdb1 to sda1 at a reasonable rate (30 -50 MB/s). 

```
hdparm -i /dev/sda
```

/dev/sda:

 Model=WDC WD3200JD-00KLB0, FwRev=08.05J08, SerialNo=     WD-WMAMR1394834
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?0?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=625142448
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode
------------------------
/dev/sdb:

 Model=SAMSUNG HD501LJ, FwRev=CR100-10, SerialNo=S0MUJ1KP602451      
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode

```
 sudo hdparm -Tt /dev/sda && sudo hdparm -Tt /dev/sdb
```

/dev/sda:
 Timing cached reads:   7134 MB in  2.00 seconds = 3571.05 MB/sec
 Timing buffered disk reads:  190 MB in  3.01 seconds =  63.13 MB/sec

/dev/sdb:
 Timing cached reads:   5862 MB in  2.00 seconds = 2933.40 MB/sec
 Timing buffered disk reads:  232 MB in  3.01 seconds =  77.03 MB/sec

These readings seem to be fine. Now the thing that may be causing issues is with sda, which is the western digital hdd. The drive is sata, but connects via some bs pci card. It is not a standard direct sata connection. (Yes, had I known this I never would have gotten it, but it was from eBay.)

Anyway, the pci card controls a Promise raid controller, which forces the drive to do something having to do with raid. The drive is not in a raid configuration though. It's completely separate from sdb.

Also, sda is reisferfs, while sdb is ext3. Before I upgraded to Ibex (and even for a short time after) I didn't have any issues with slow transfer speeds. I also tried installing:
dmraid (1.0.0.rc14-2ubuntu12)
libdmraid1.0.0.rc14 (1.0.0.rc14-2ubuntu12)

to see if that would help. It didnt. Any ideas of what is causing the problem or what I should do?

As a sidenote, I'm wondering if I should deal with this drive anymore; I'd like to reinstall and go 64-bit, but don't want to go through that trouble if I had a silly hdd.

---

### Post by cariboo on 2008-11-11
Have you gone into the raid controller and set it for jbod (just a bunch of disks), that way you shouldn't need any raid software.

Jim

---

### Post by angryhomer17 on 2008-11-11
How do I go into the raid controller?

I did access the "Easy Build Utility" at boot. I have 5 options:
1. Auto Setup
2. View Drive Assignments-- It is Array 1 Mode U5 and Stripe
3. Define Array
4. Delete Array
5. Rebuid Array

I didn't see any option for jbod.

---

### Post by angryhomer17 on 2008-11-15
I took another look at the drive (I don't know how I missed this), but it can be hooked up without the pci raid card. Unfortunately, right after I found that out, the drive crashed. 

So, after I get the drive cold, I'm going to see if I get any better transfer speeds when it's hooked up directly to the mobo.

---

