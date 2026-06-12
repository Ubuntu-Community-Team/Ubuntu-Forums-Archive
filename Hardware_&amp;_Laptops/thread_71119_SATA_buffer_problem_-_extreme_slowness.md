---
title: "SATA buffer problem - extreme slowness"
date: 2005-10-02
forum: Hardware &amp; Laptops
---

### Post by fourthirtysix on 2005-10-02
all of a sudden my SATA drive has gone a bit crazy. i think there is a problem with the buffer cache causing it to work VERY slowly. it has worked fine for awhile until now.

the drive will actually mount and copy a few MB of data but then goes into VERY slow mode. here are some diagnostics:

hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1080 MB in  2.00 seconds = 538.74 MB/sec
 Timing buffered disk reads:    2 MB in 16.20 seconds = 126.41 kB/sec

hdparm -i /dev/sda

/dev/sda:

 Model=WDC WD2500JD-00G02.0, FwRev=02.0, SerialNo=
 Config={ }
 RawCHS=30401/255/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=30401/255/63, CurSects=0, LBA=no
 IORDY=no
 PIO modes:  pio0
 AdvancedPM=no

 * signifies the current active mode

hdparm /dev/sda

/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 30401/255/63, sectors = 250059350016, start = 0

i have tried to do "hdparm -d1 /dev/sda" to enable DMA but receive this message with the same slow throughput:

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

any help would be greatly appreciated!

thanks

---

### Post by telmo on 2005-10-22
I have exactly the same problem, and it sucks! Everything was looking so fine in my Thinkpad x41... and now i found the hd is just tooo slow.

Anyone?

thx

---

