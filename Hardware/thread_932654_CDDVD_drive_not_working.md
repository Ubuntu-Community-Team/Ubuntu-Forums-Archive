---
title: "CD/DVD drive not working"
date: 2008-09-28
forum: Hardware
---

### Post by shan_2008 on 2008-09-28
Hey there,

I just replaced my SATA DVD burner with an old IDE one. (I need the SATA controller for a new hard disk). The IDE DVD drive is correctly detected, but isn't working (not mountable etc).

Relevant dmesg output:
```
[   20.256189] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-4120B A101 PQ: 0 ANSI: 5
[   21.101086] Uniform CD-ROM driver Revision: 3.20
[   21.101111] sr 0:0:1:0: Attached scsi CD-ROM sr0
```

The relevant symbolic links in /dev/
```
/dev/cdrom1 -> scd0
/dev/dvd1 -> scd0
/dev/dvdrw1 -> scd0
/dev/sr0 -> scd0
```

hdparm output
```
# hdparm -i /dev/scd0

/dev/scd0:

 Model=HL-DT-ST DVDRAM GSA-4120B               , FwRev=A101    , SerialNo=K3J45TJ3736         
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-2,3,4,5

 * signifies the current active mode
```

When I try to cat the drive, just to see if *anything* outputs, I get the following. When running the command the drive is seeking the CD-ROM.

```

# cat /dev/scd0 
cat: /dev/scd0: No medium found
```

I'm starting to think it's a hardware problem and the drive is physically broken. Any way to confirm this? (preferable without removing it and checking it in another machine)

PS in /etc/fstab I'm currently using the following line, but I doubt the problem is here
```
/dev/cdrom1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by shan_2008 on 2008-10-11
*bump*

---

