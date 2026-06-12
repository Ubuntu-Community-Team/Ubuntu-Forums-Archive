---
title: "m7440 hard disk wistle"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by aswhad on 2007-12-08
Hello i have a Fujitsu Amilo M7440g with Gutsy on it.
Problem is that when i halt the laptop the hard drive makes a wistle noise, it's louder than windows XP, so i'm a bit worried. (also Suse had the problem)
```
uname -a
Linux m-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

hdparm -i /dev/sda

/dev/sda:
Model=SAMSUNG HM080JI , FwRev=YC100-02, SerialNo=S082J10Y623696 
Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
PIO modes: pio0 pio1 pio2 pio3 pio4 
DMA modes: mdma0 mdma1 mdma2 
UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 
AdvancedPM=no WriteCache=enabled
Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0: ATA/ATAPI-1,2,3,4,5,6,7
* signifies the current active mode 
```
[here is a simular bug but it's with older kernels, so no solution i think]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810")
If changing the drive would be a solution that would be no problem but i have to be sure, money doesn't grow on trees in my garden.

---

### Post by aswhad on 2007-12-10
nobody?

---

