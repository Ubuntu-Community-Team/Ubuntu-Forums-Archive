---
title: "slow cd-rom problem"
date: 2005-03-02
forum: Hardware &amp; Laptops
---

### Post by cclay on 2005-03-02
Hi,

I'm having trouble with my IDE cdrom drives.  They both seem to copy audio discs to the hard drive very slowly.  One is a 16X Yamaha CDRW drive, and the other is a 50X CD-ROM drive.
```
cclay@ubuntu:/boot/grub $ sudo /sbin/hdparm -t /dev/hdc

/dev/hdc:
 Timing buffered disk reads:  read() failed: Input/output error
```

I get the same output for hdd.  

```
cclay@ubuntu:/boot/grub $ sudo /sbin/hdparm -i /dev/hdc

/dev/hdc:

 Model=CD-ROM 50X L, FwRev=15, SerialNo=
 Config={ SpinMotCtl Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:600,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  *mdma0 *mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no

 * signifies the current active mode
```

```
cclay@ubuntu:/boot/grub $ sudo /sbin/hdparm -i /dev/hdd

/dev/hdd:

 Model=YAMAHA CRW2100E, FwRev=1.0N, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 *udma1
 AdvancedPM=no

 * signifies the current active mode

```

I've used Sound Juicer, Grip, cdparanoia, and cdda2wav to copy data.  Each drive is really slow (<1X).

Any help is appreciated.

Thanks,

cclay

---

### Post by KLineD on 2005-03-02
Check [this](http://www.ubuntuforums.org/showthread.php?p=82602#post82602) post and see if that helps.

---

### Post by KLineD on 2005-03-02
Check [this](http://www.ubuntuforums.org/showthread.php?p=82602#post82602) post and see if that helps.

> cclay@ubuntu:/boot/grub $ sudo /sbin/hdparm -t /dev/hdc

/dev/hdc:
 Timing buffered disk reads:  read() failed: Input/output error 
BTW to do that, a CD must be in the drive.

---

### Post by cclay on 2005-03-02
Hi,

Thanks for the quick response.
```

cclay@ubuntu:/boot/grub $ sudo /sbin/hdparm -d1 /dev/hdc

/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

```

Also:
```
cclay@ubuntu:/boot/grub $ sudo /sbin/hdparm -t /dev/hdc

/dev/hdc:
 Timing buffered disk reads:    2 MB in  3.14 seconds = 651.29 kB/sec
```

Pretty slow, eh?

I don't know another way to turn DMA on.  Also, I can't append hdc=ide-scsi to /boot/grub/menu.lst on the kernel line.  Ubuntu won't boot if I do.

Thanks for any further support.

---

### Post by cclay on 2005-03-09
I still can't figure it out.  Anyone have any last ideas before I assume the drive is failing?

Thanks,

Clayton

---

