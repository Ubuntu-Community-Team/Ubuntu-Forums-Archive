---
title: "IDE ATA-133 HD running at ATA-100"
date: 2009-01-02
forum: Hardware
---

### Post by pmerrill on 2009-01-02
Hi,

I've just installed 8.1 and while everything works, I seem to have a little issue with the hard drives not running at the best speed. I've got an older 40GB Maxtor IDE drive capable of ATA-133 but running at UDMA5 (ATA-100) and a CD running at UDMA2 (which is as fast as it will go).

My question is why is the drive running at UDMA5 and not UDMA6?

In addition, is there anyway that I can use hdparm to set it to UDMA6?

/dev/sdb:

 Model=Maxtor 2F040L0
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=80293248
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma6 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

---

### Post by logos34 on 2009-01-02
Maybe the board doesn't support that speed.  Or maybe an older (40-pin) cable?

Here's mine:

maxtor 120 gb ata133

> /dev/sda:

 Model=Maxtor 6L120P0                          , FwRev=BAJ41G20, SerialNo=L31TK1LG            
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=240121728
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode


dvd burner:

> user@ubuntu:~$ sudo hdparm -i /dev/scd0

/dev/scd0:

 Model=ASUS    DRW-1608P2                      , FwRev=1.41    , SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-2,3,4,5

 * signifies the current active mode

---

### Post by pmerrill on 2009-01-03
No, it's definitely a 80 wire cable and the motherboard and BIOS support ATA-133. In fact, it's a Vista/Ubuntu dual boot machine and under Windows the disk comes up as ATA-133. There is obviously some defect or hardware incompataibility here. What I don't understand is that with hdparm you could force the disk to ATA-133 but it no longer seems to work under Ubuntu because the IDE disk is being accessed by the serial ATA driver.

Ideas?

---

### Post by logos34 on 2009-01-03
Yeah, I wished they hadn't switched to the libata scsi driver, you could use hdparm to configure the drives before.  

you say it 'comes up' as 133, you mean it runs full speed in windows or just shows that in device manager?

---

### Post by pmerrill on 2009-01-07
> **logos34 said:**
> Yeah, I wished they hadn't switched to the libata scsi driver, you could use hdparm to configure the drives before.  

you say it 'comes up' as 133, you mean it runs full speed in windows or just shows that in device manager?

The driver indicates ATA-133 as does PC Wizard. The linux driver says ATA-100 but hdparm benchmarks the drive at

$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   1276 MB in  2.00 seconds = 637.97 MB/sec
 Timing buffered disk reads:  138 MB in  3.01 seconds =  45.83 MB/sec

$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   1350 MB in  2.00 seconds = 675.31 MB/sec
 Timing buffered disk reads:  138 MB in  3.01 seconds =  45.78 MB/sec

Since it's a 40GB ATA-133 drive it MAY be running at ATA-133 but the driver is indicating ATA-100. I can't bench it under windows because it's a pure linux drive and not recognised by Windows.

---

### Post by logos34 on 2009-01-07
Looks like you are running a tad slow, by maybe ~5 mb, but that's hardly noticeable. Try it several times in a row.  Take the average.  (of course, the point is you should be operating at 133)

I have to run hdparm command a few times to get an accurate reading because the first few readings are abnormally low:

> user@ubuntu:~$ sudo hdparm -tT /dev/sda
[sudo] password for user: 

/dev/sda:
 Timing cached reads:   998 MB in  2.00 seconds = 498.41 MB/sec
 Timing buffered disk reads:  104 MB in  3.06 seconds =  34.03 MB/sec
user@ubuntu:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   994 MB in  2.00 seconds = 496.62 MB/sec
 Timing buffered disk reads:  114 MB in  3.00 seconds =  37.99 MB/sec

user@ubuntu:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   890 MB in  2.00 seconds = 444.78 MB/sec
 Timing buffered disk reads:  122 MB in  3.03 seconds =  40.26 MB/sec
user@ubuntu:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   982 MB in  2.00 seconds = 490.65 MB/sec
 Timing buffered disk reads:  160 MB in  3.02 seconds =  52.97 MB/sec
user@ubuntu:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   980 MB in  2.00 seconds = 489.61 MB/sec
 Timing buffered disk reads:  164 MB in  3.02 seconds =  54.29 MB/sec
user@ubuntu:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   996 MB in  2.00 seconds = 497.29 MB/sec
 Timing buffered disk reads:  160 MB in  3.02 seconds =  53.01 MB/sec
user@ubuntu:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   992 MB in  2.00 seconds = 495.28 MB/sec
 Timing buffered disk reads:  148 MB in  3.00 seconds =  49.26 MB/sec
user@ubuntu:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   996 MB in  2.00 seconds = 497.49 MB/sec
 Timing buffered disk reads:  162 MB in  3.00 seconds =  53.92 MB/sec
user@ubuntu:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   868 MB in  2.00 seconds = 433.74 MB/sec
 Timing buffered disk reads:  164 MB in  3.03 seconds =  54.08 MB/sec
user@ubuntu:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   978 MB in  2.00 seconds = 488.83 MB/sec
 Timing buffered disk reads:  160 MB in  3.00 seconds =  53.33 MB/sec
user@ubuntu:~$ 


---

