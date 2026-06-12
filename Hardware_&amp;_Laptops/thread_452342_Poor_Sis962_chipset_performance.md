---
title: "Poor Sis962 chipset performance"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by Dax0r on 2007-05-23
My motherboard has sis962 chipset.
The right module is sis5513 but it dont work 100% native mode (I think it's normal)

> [SIS5513: IDE controller at PCI slot 0000:00:02.5
[B]SIS5513: chipset revision 0
SIS5513: not 100% native mode: will probe irqs later
SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
    ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda: DMA, hdb: DMA
    ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc: DMA, hdd: DMA[/B]
Probing IDE interface ide0...
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000020ed00b31a7d]
hda: Maxtor 4D080K4, ATA DISK drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Probing IDE interface ide1...
hdc: SAMSUNG DVD-ROM SD-616T, ATAPI CD/DVD-ROM drive
hdd: _NEC CD-RW NR-9100A, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
hda: max request size: 128KiB
hda: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
hda: cache flushes not supported
 hda: hda1 hda2 < hda5 hda6 hda7 hda8 hda9 hda10 > hda3 hda4
hdc: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
Uniform CD-ROM driver Revision: 3.20


The problem is that I experienced poor performance

i just checked hdparm...
>  hdparm -tT /dev/hda 

/dev/hda:
 Timing cached reads:   466 MB in  2.00 seconds = 232.57 MB/sec
 Timing buffered disk reads:   74 MB in  3.03 seconds =  24.43 MB/sec

That seems slow.

This was my hdparm -i:

> # hdparm -i /dev/hda

/dev/hda:

 Model=Maxtor 4D080K4, FwRev=DAH017K0, SerialNo=D4H293FE
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=16
 CurCHS=4047/16/255, CurSects=16511760, LBA=yes, LBAsects=160086528
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 0:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode


>  hdparm /dev/hda 

/dev/hda:
 multcount     = 16 (on)
 IO_support    =  0 (default 16-bit)
 unmaskirq     =  0 (off)
 using_dma     =  1 (on)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 65535/16/63, sectors = 160086528, start = 0


How Can you see udma5 seems active...But why I have this poor performance??

---

### Post by size_XXM on 2007-05-23
Not that I'd know something about this, but did you run hdparm -t multiple times? The results vary quite a lot (even the man page says to repeat 2-3 times). I get 20 MB/s on the first run and 60 MB/s on the next run.
I have the same chipset and I didn't notice a great performance decrease (not that the performance in Windows was any great - using HDtach, the interface speed never reached 80 MB/s).

There IS a performance hit, however when i copy from the slave drive (ext2FS) to master (FAT32) - both on the primary channel - reaches merely 10MB/s. when copying the other way (incidentally from the newer, faster to the older, slower), the speed is ~25 MB/s, as in Windows.

PS: I'm pretty new to Linux, but if there are any settings/outputs I can provide from my machine, just say so :)

---

### Post by dlstyley on 2007-12-23
I have the exact same setup with similar benchmark results and the disk "seems" slow to me (compared to how XP "seemed").  I have no way to know so it's purely subjective.  I did put the 6.10 live CD in and the "Timed Cache Reads" was double what I am getting with Gutsy, however the "Buffered Reads" were slower.

---

### Post by Dax0r on 2008-03-16
> **dlstyley said:**
> I have the exact same setup with similar benchmark results and the disk "seems" slow to me (compared to how XP "seemed").  I have no way to know so it's purely subjective.  I did put the 6.10 live CD in and the "Timed Cache Reads" was double what I am getting with Gutsy, however the "Buffered Reads" were slower.

So do u experienced the same slowness?

---

