---
title: "Extremely slow boot.  HDD problem?"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by sjo65 on 2007-02-07
I just recently installed Ubuntu (breezy) for the first time on my rig.

The computer consisted of P4 D CPU,  2x DVD-Rom drives,  and 1 SATA HDD.  Before installing Ubuntu I disconnected one of the DVD-Rom drives and inserted my old Deskstar 7200 IDE HDD as the master and the other DVD-Rom as the slave.  I had to unplug one of the DVD-ROM drives because there is only 1 IDE slot on the motherboard (Sony Vaio).

The installation went smoothly.  I partitioned 3 separated drives in the IDE drive: root, swap, and home.  Installed Ubuntu and then installed GRUB on the MBR.  

The problem is that everytime I boot my computer it takes forever to boot into Ubuntu and GRUB.  

It takes around 15-20 min to fully log into Ubuntu and about 2-5 minutes just to get to the menu selection for GRUB.  I ran the hdparam (sp?) commands in terminal once I logged in and the results were this:

```
 Model=IC35L060AVER07-0, FwRev=ER6OA46A, SerialNo=SZPTZTCV103
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=40
 BuffType=DualPortCache, BuffSize=1916kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=120103200
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-5 T13 1321D revision 1:

 * signifies the current active mode

 Timing cached reads:   3868 MB in  2.00 seconds = 1932.36 MB/sec
 Timing buffered disk reads:   12 MB in  3.57 seconds =   3.36 MB/sec
```

From what I've seen, the normal Timing buffered disk reads should be at least ~30MB/sec.  

Can anyone tell me why the HDD is running so slow???

PS.  The IDE drive is pretty old and beat up and has couple pins missing from the IDE connectors.  I don't know if this makes a huge difference, but just thought I should throw that out there.

---

### Post by sjo65 on 2007-02-08
*bump*

any help?:confused:

---

