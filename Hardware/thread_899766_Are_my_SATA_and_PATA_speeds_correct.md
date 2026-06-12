---
title: "Are my SATA and PATA speeds correct?"
date: 2008-08-24
forum: Hardware
---

### Post by Cubytus on 2008-08-24
Hi to all fellow ubunteros, 

since I read about the topics about slow SATA, I tested my setup, which is:

Asus A8N SLi DeLuxe
2x Western Digital hard drives WD2500KS-00MJB0, SATA 3.0Gb/s (supposedly)
(as /dev/sda and /dev/sdb)
1x DVD-ROM (as /dev/cdrom1)
1x DVD-RW NEC 3500A (as /dev/cdrom0), both on the same 40-pin IDE cable.

Command **sudo hdparm -tT /dev/sda** reads
```
/dev/sda:
 Timing cached reads:   1214 MB in  2.01 seconds = 604.20 MB/sec
 Timing buffered disk reads:  178 MB in  3.02 seconds =  59.02 MB/sec

```

for **/dev/sdb**:
```
/dev/sdb:
 Timing cached reads:   1298 MB in  2.00 seconds = 649.44 MB/sec
 Timing buffered disk reads:  186 MB in  3.01 seconds =  61.74 MB/sec

```

It's not exactly unbearable, but copying a large file to the same drive averages 8.5 to 10MiB/s. Approximately the same speed when copying the same file to the other drive, sometimes a tad higher (10 to 13MiB/s). On the wired 100Mbps network through Samba, the same file to another, older computer with ATA/133 hard drive is 7MiB/s.

As for the optical drives:
cdrom (burner) gives:
```
/dev/cdrom:
 Timing cached reads:   1004 MB in  2.00 seconds = 501.94 MB/sec
 Timing buffered disk reads:   26 MB in  3.06 seconds =   8.50 MB/sec

```

cdrom1
> /dev/cdrom1:
 Timing cached reads:   1250 MB in  2.00 seconds = 625.15 MB/sec
 Timing buffered disk reads:   20 MB in  3.13 seconds =   6.39 MB/sec


When I ran it right after the reboot, **dmesg | grep ata** gave:
```
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[   71.301111] Memory: 1027360k/1048512k available (2177k kernel code, 20460k reserved, 1006k data, 368k init, 131008k highmem)
[   71.301125]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   75.481984] libata version 3.00 loaded.
[   76.261838] pata_amd 0000:00:06.0: version 0.3.10
[   76.262715] scsi0 : pata_amd
[   76.262906] scsi1 : pata_amd
[   76.263445] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   76.263447] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   76.909093] ata2.00: ATAPI: _NEC DVD_RW ND-3500AG, 2.1B, max UDMA/33
[   76.909112] ata2.01: ATAPI: COMPAQ  DVD-ROM GD-8000, 0011, max UDMA/66
[   76.909123] ata2.01: limited to UDMA/33 due to 40-wire cable
[   77.072902] ata2.00: configured for UDMA/33
[   77.244770] ata2.01: configured for UDMA/33
[   77.251491] sata_nv 0000:00:07.0: version 3.5
[   77.251868] sata_nv 0000:00:07.0: Using ADMA mode
[   77.253359] scsi2 : sata_nv
[   77.253545] scsi3 : sata_nv
[   77.253695] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 19
[   77.253698] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 19
[   77.564337] ata3: SATA link down (SStatus 0 SControl 300)
[   77.876091] ata4: SATA link down (SStatus 0 SControl 300)
[   77.876499] sata_nv 0000:00:08.0: Using ADMA mode
[   77.876618] scsi5 : sata_nv
[   77.876842] scsi6 : sata_nv
[   77.876968] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 16
[   77.876970] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 16
[   78.343727] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   78.351865] ata5.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[   78.351868] ata5.00: 488397168 sectors, multi 1: LBA48 
[   78.359842] ata5.00: configured for UDMA/133
[   78.827344] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   78.835466] ata6.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[   78.835468] ata6.00: 488397168 sectors, multi 1: LBA48 
[   78.843471] ata6.00: configured for UDMA/133
[   78.843566] ata5: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   78.843911] ata6: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   78.844643] sata_sil 0000:05:0a.0: version 2.3
[   78.844876] sata_sil 0000:05:0a.0: Applying R_ERR on DMA activate FIS errata fix
[   78.845861] scsi7 : sata_sil
[   78.845997] scsi8 : sata_sil
[   78.846135] scsi9 : sata_sil
[   78.846269] scsi10 : sata_sil
[   78.846292] ata7: SATA max UDMA/100 mmio m1024@0xd400d000 tf 0xd400d080 irq 20
[   78.846295] ata8: SATA max UDMA/100 mmio m1024@0xd400d000 tf 0xd400d0c0 irq 20
[   78.846298] ata9: SATA max UDMA/100 mmio m1024@0xd400d000 tf 0xd400d280 irq 20
[   78.846300] ata10: SATA max UDMA/100 mmio m1024@0xd400d000 tf 0xd400d2c0 irq 20
[   79.155085] ata7: SATA link down (SStatus 0 SControl 310)
[   79.466839] ata8: SATA link down (SStatus 0 SControl 310)
[   79.778591] ata9: SATA link down (SStatus 0 SControl 310)
[   80.090347] ata10: SATA link down (SStatus 0 SControl 310)
[   82.040465] EXT3-fs: mounted filesystem with ordered data mode.
[   82.789945] scsi 4:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[  144.695715] EXT3-fs: mounted filesystem with ordered data mode.
```

I noticed one strange issue, that the burner (master on IDE1) has a slower maximum speed than the DVD-ROM, although it's more recent. However, **sudo hdparm -i /dev/cdrom** seems normal:

```
/dev/cdrom:

 Model=_NEC DVD_RW ND-3500AG                   , FwRev=2.1B    , SerialNo=                    
 Config={ Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no

 * signifies the current active mode

```

for **/dev/cdrom1**:
```
/dev/cdrom1:

 Model=COMPAQ  DVD-ROM GD-8000                 , FwRev=0011    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 
 AdvancedPM=no

 * signifies the current active mode
```

Copying a file from the DVD-ROM drive reads 1.3MiB/s to one hard drive, but 9MiB/s if it comes from the burner. Go figure.

So, the speeds I have don't seem so bad and the computer is never hung by a transfer, unlike other ubunteros her, but I *feel* they're a bit slow for a SATA-3 setup.

I read on a hard drive manufacturer site's (don't remember which one) that having two SATA hard drives bolted on the same chassis could lead to slower speeds because of the effects of inertial momentum due to the great mass rotating at high speed.

---

