---
title: "Unable to enable DMA on nForce based board"
date: 2008-12-13
forum: Hardware
---

### Post by speedsix on 2008-12-13
I'm not sure if this is the right board for nForce questions, mods please move if not.


Anyway, I've just replaced the motherboard on my Ubuntu box without reinstalling (nforce 250 based to nforce 630i) Everything seemed to just work, except DMA isn't enabled and I get the following error when trying to enable it for both the hard disk and the dvd drive;

```

dom@mythbox:~$ hdparm -d1 /dev/cdrom1

/dev/cdrom1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```

Drives are on the same IDE controller, HD as master, DVD as slave (not cable select)

Any ideas where to start?



Many thanks

---

### Post by speedsix on 2008-12-15
Hmm, while I get the error above, I think my drive is running DMA.

DMESG reports

```
[    4.277911] scsi 4:0:0:0: Direct-Access     ATA      Maxtor 6L300R0   BAJ4 PQ: 0 ANSI: 5

```

Also

```
dom@mythbox:~$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=Maxtor 6L300R0                          , FwRev=BAJ41G20, SerialNo=L61QTSFH            
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=586114704
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

```


Why is my PATA drive /dev/sda?

---

