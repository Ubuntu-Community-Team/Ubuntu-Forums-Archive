---
title: "How May I Check HD Info/Settings/Status?"
date: 2005-11-16
forum: Hardware &amp; Laptops
---

### Post by polo_step on 2005-11-16
I'm not sure my single hard drive is properly set up in terms of ATA speed, etc.

Is there a simple way to check this in Ubuntu and/or get comprehensive info on the drive as installed?

As always, thanks for any help.

---

### Post by bartc on 2005-11-16
I think what you are looking for is *hdparm.*

---

### Post by polo_step on 2005-11-16
[QUOTE=bartc]I think what you are looking for is *hdparm.*[/QUOTE]
Yes, that sounds about right, but what switches/options do you recommend?

Here's what I get with -i:

/dev/hda:

 Model=HDS722540VLAT20, FwRev=V31OA6MA, SerialNo=VN611ECADUDDLD
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=52
 BuffType=DualPortCache, BuffSize=1794kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=80418240
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 3a:

 * signifies the current active mode

I don't see all the active settings in there, assuming they are all applicable.

HDS722540VLAT20 = [http://www.hd4less.com/hide7k40uaha.html](http://www.hd4less.com/hide7k40uaha.html)

Thanks!

---

