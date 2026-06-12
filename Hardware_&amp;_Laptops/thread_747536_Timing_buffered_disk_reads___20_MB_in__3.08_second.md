---
title: "Timing buffered disk reads:   20 MB in  3.08 seconds =   6.49 MB/sec"
date: 2008-04-06
forum: Hardware &amp; Laptops
---

### Post by hokah on 2008-04-06
It is hard to belive, but it is true. I have found heaps of threads but no solution.



~$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   930 MB in  2.00 seconds = 463.92 MB/sec
 Timing buffered disk reads:   20 MB in  3.08 seconds =  ** 6.49 MB/sec**


$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=ST94011A                                , FwRev=5.11    , SerialNo=            3KW5FSP4
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=?16?
 CurCHS=17475/15/63, CurSects=16513875, LBA=yes, LBAsects=78140160
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 2:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode

---

### Post by stek79 on 2008-04-07
Hi, actually I've found the same problem on my PC!

With Hardy, I get a sequential throughput of about 25-30MB/s (hdparm -t). With the previous kernels (Gutsy), I was able to reach a value of 56MB/s!!!

With hdparm I noticed that my DMA is set to udma2, and not to udma5. Interestingly, I've found that during the boot the kernel logs:

[   36.294329] ata1.00: ATA-6: Maxtor 5T030H3, TAH71DP0, max UDMA/100
[   36.295740] ata1.01: ATA-6: WDC WD2500JB-00GVC0, 08.02D08, max UDMA/100
[   36.295770] ata1.00: limited to UDMA/33 due to 40-wire cable
[   36.295775] ata1.01: limited to UDMA/33 due to 40-wire cable

This is true, since I have old ATA disks, but with the previous kernel that undergrading was not occuring. 

Which kernel are you using? Do you get similar results? Ever tried with Gutsy kernel?

---

### Post by stek79 on 2008-04-07
Guys,
   it seems this is a common kernel issue (2.6.24).

The DMA type is set to a low performance value, AFAIK.

See for example [https://bugs.launchpad.net/ubuntu/+bug/195221](https://bugs.launchpad.net/ubuntu/+bug/195221)

---

### Post by hokah on 2008-04-07
Im using 7.10 fresh download from repository, I have no more power to fight with this, I just will try other distro. Maybe Mandriva will be working.

---

### Post by stek79 on 2008-04-08
> **hokah said:**
> Im using 7.10 fresh download from repository, I have no more power to fight with this, I just will try other distro. Maybe Mandriva will be working.

Can you post the output of dmesg?

The problem is probably in the libata (part of the kernel), which in my case I was not using with Gutsy (I have PATA drives). 

You may experiment the problem even with Gutsy since you are using a SATA drive.

If you find another distro which gives you good HD throughput, let us know, it may be important to discover the misconfiguration.

---

### Post by hokah on 2008-04-10
I have installed ELIVE under this particular distro my HD is appears as hda, I have about 30 MB/sec disk reads, which is better but I dont know if this is a maximum, I will try on Mandriva and on Windows this week and let you know.

---

