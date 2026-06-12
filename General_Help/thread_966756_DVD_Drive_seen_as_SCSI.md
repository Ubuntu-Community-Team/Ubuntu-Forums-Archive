---
title: "DVD Drive seen as SCSI"
date: 2008-11-01
forum: General Help
---

### Post by elricbillman on 2008-11-01
I have a Lite-on DVD drive (which has worked fine with Ubuntu previously) and is now really slow. It takes a few hours to burn a data disk. I have read other threads on this issue but have not found a solution. It would seem the drive, which is plugged into the secondary IDE channel on the motherboard, is being recognized as SCSI.

Below is the output from some commands I found online:
```
sudo lshw -C disk
 *-disk:0                
       description: ATA Disk
       product: SAMSUNG SP2504C
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: VT10
       serial: S09QJ1MA120277
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00000001
  *-disk:1
       description: ATA Disk
       product: SAMSUNG SP2504C
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: VT10
       serial: S09QJ1ML203705
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=8c10a4f4
  *-disk
       description: ATA Disk
       product: Maxtor 6Y160P0
       vendor: Maxtor
       physical id: 0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
       version: YAR4
       serial: Y48G1FME
       size: 152GiB (163GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00540054
  *-cdrom
       description: DVD writer
       product: DVDRW SHW-160P6S
       vendor: LITE-ON
       physical id: 1
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: PS08
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
  *-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdd
  *-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@6:0.0.1
       logical name: /dev/sde
  *-disk:2
       description: SCSI Disk
       physical id: 0.0.2
       bus info: scsi@6:0.0.2
       logical name: /dev/sdf
  *-disk:3
       description: SCSI Disk
       physical id: 0.0.3
       bus info: scsi@6:0.0.3
       logical name: /dev/sdg
```

```
sudo hdparm -i /dev/scd0
/dev/scd0:

 Model=LITE-ON DVDRW SHW-160P6S                , FwRev=PS08    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  *sdma0 *sdma1 *sdma2 sdma? mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode
```

---

