---
title: "Slow Hard disk"
date: 2009-10-01
forum: Hardware
---

### Post by ykpaiha on 2009-10-01
Hi

It's a bit odd and I get confused

I got 2 sata HDD connected to a ga-p35-ds3l

The first one with windows and Ubuntu installed
=Model=MAXTOR STM3500320AS   , FwRev=MX15    , SerialNo=         9QM18DEP

Second for datas and a smal partition for trials : Model=Maxtor 6V250F0  , FwRev=VA111900, SerialNo=V599SA7G 

So the #1  sudo hdparm -i /dev/sda*

Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=?16?
CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
PIO modes:  pio0 pio1 pio2 pio3 pio4
DMA modes:  mdma0 mdma1 mdma2
UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
AdvancedPM=no WriteCache=enabled
Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

But under windows with the maxtor tools Buffer=32 and active as well with a hackintosh (sdb2) and here BuffSize=0kB ??

The  #2 is activated  as well with linux 
sudo hdparm -i /dev/sdb

Config={ Fixed }
RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=?0?
CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=490234752
IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
PIO modes:  pio0 pio1 pio2 pio3 pio4
DMA modes:  mdma0 mdma1 mdma2
UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
AdvancedPM=yes: disabled (255) WriteCache=enabled
Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

And this one has the right amount of buffering
notice that one indicate FIXED and the other = HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5%
..

Access disk and copies or zip-unzip dezipe rise cpu activity to 100% and lag all other activities , than with windows all these jobs keep a reasonable amount of  ressources available with the same disk.

If someone has a clue .

NB it's a brand new disk (sda1) and no memtest error 
Bios disks are AHCI Smart off ( on doesn't change anything)

sudo dmesg | grep ata

[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  modified: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.004000] Memory: 2024696k/2096000k available (4749k kernel code, 500k absent, 70128k reserved, 2523k data, 532k init)
[    0.410544] libata version 3.00 loaded.
[    1.034244] ata1: SATA max UDMA/133 abar m2048@0xfb006000 port 0xfb006100 irq 2299
[    1.034246] ata2: SATA max UDMA/133 abar m2048@0xfb006000 port 0xfb006180 irq 2299
[    1.034248] ata3: DUMMY
[    1.034249] ata4: DUMMY
[    1.034250] ata5: SATA max UDMA/133 abar m2048@0xfb006000 port 0xfb006300 irq 2299
[    1.034252] ata6: SATA max UDMA/133 abar m2048@0xfb006000 port 0xfb006380 irq 2299
[    1.516018] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.518918] ata1.00: HPA unlocked: 976771055 -> 976773168, native 976773168
[    1.518922] ata1.00: ATA-8: MAXTOR STM3500320AS, MX15, max UDMA/133
[    1.518924] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.520725] ata1.00: configured for UDMA/133
[    2.020027] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.034063] ata2.00: HPA unlocked: 490232639 -> 490234752, native 490234752
[    2.034066] ata2.00: ATA-7: Maxtor 6V250F0, VA111900, max UDMA/133
[    2.034068] ata2.00: 490234752 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.037418] ata2.00: configured for UDMA/133
[    2.372019] ata5: SATA link down (SStatus 0 SControl 300)
[    2.872010] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.875037] ata6.00: ATAPI: TSSTcorpCD/DVDW SH-S183A, SB02, max UDMA/33, ATAPI AN
[    2.875046] ata6.00: applying bridge limits
[    2.878583] ata6.00: configured for UDMA/33
[    3.342012] Write protecting the kernel read-only data: 6688k
[    4.019596] ReiserFS: sda2: using ordered data mode
[   15.866814] EXT4-fs: mounted filesystem with ordered data mode.


Thanks

---

