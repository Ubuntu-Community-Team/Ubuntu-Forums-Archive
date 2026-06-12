---
title: "Hard drive speed"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by ctweb on 2007-10-22
I am having serious sp[LIST]
[*]eed issues with 7.10 on a Dell 600m.  As you can see I am hitting 3.84mb/sec.  I have rebooted into another distro I have multibooting and in that distro I am getting 35.6mb/sec.  Any help would be appreciated.  Also you can see I am unable to set dma.  


```


hdparm -t /dev/hda

/dev/hda:
 Timing buffered disk reads:   12 MB in  3.13 seconds =   3.84 MB/sec


hdparm -i /dev/hda

/dev/hda:

 Model=FUJITSU MHV2060AH, FwRev=00000096, SerialNo=NT25T592K7W4
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=117210240
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 3a:  ATA/ATAPI-2,3,4,5,6


hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma     =  0 (off)


```

---

### Post by ctweb on 2007-10-25
I really need some help with this, I have done two kernel compiles at 2.5mb/sec and getting nowhere fast.  I have turned on all DMA and IDE things I can find that might relate to my laptop.  It is a Dell 600m which is only a few years old and should be supported out of the box.

---

### Post by Daelyn on 2007-10-25
Sorry mate, but you are already on the highest DMA mode you could have.

DMA1-5 is slower than UDMA counterparts.


THere is something else stealing the performance of your filesystem/hdd.

---

### Post by ctweb on 2007-10-25
```

hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma     =  0 (off)

```

That is saying DMA is not enabled and cannot be turned on at least from the hours I've spent looking for a solution.

---

### Post by Daelyn on 2007-10-25
Difference in UDMA and DMA.
UDMA active does not neccesarily mean DMA active.

My Fujitsu HDD is set to UDMA5 (only active dma setting) and it gives me about 40mb/s

Boot into your other distro and compare the hdparm info. I suspect you will find it is the same.

---

### Post by ctweb on 2007-10-25
As I said in my first post my other distro works fine.  I have run hdparm on both distros to show the difference and the only difference is that DMA is not enabled, I know that I can turn on 32bit and so on but those I am able to turn on.  The problem is that DMA cannot be turned on.  I am now up to 3 kernel compiles and still performance is crap.  The board on this laptop uses ICH4.  I have looked through the kernel to find the chipset for this machine and I cant find a thing so I would really appreciate help because it isn't an uncommon chipset.

Ubuntu 7,10

```

sudo hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   1364 MB in  2.00 seconds = 682.27 MB/sec
 Timing buffered disk reads:    6 MB in  4.22 seconds =   1.42 MB/sec

```

BackTrack 2.0

```

hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   2744 MB in  2.00 seconds = 1371.71 MB/sec
 Timing buffered disk reads:  104 MB in  3.04 seconds =  34.16 MB/sec

```

Ubuntu 7,10

```

sudo hdparm /dev/hda

/dev/hda:
 multcount     =  0 (off)
 IO_support    =  0 (default 16-bit)
 unmaskirq     =  0 (off)
 using_dma     =  0 (off)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 65535/16/63, sectors = 117210240, start = 0

```

BackTrack 2.0

```

hdparm /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 117210240, start = 0

```

Ubuntu 7.1

```

sudo hdparm -i /dev/hda

/dev/hda:

 Model=FUJITSU MHV2060AH, FwRev=00000096, SerialNo=NT25T592K7W4
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=117210240
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 3a:  ATA/ATAPI-2,3,4,5,6

 * signifies the current active mode

```

BackTrack 2.0

```

hdparm -i /dev/hda

/dev/hda:

 Model=FUJITSU MHV2060AH, FwRev=00000096, SerialNo=NT25T592K7W4
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=117210240
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 3a:  ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode

```

---

### Post by ozorba on 2007-10-26
Has anybody managed to solve this problem? I have read this blog [http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear)
and want to adjust my HDD parmaneters accordingly.

Thanks,
OZ

---

### Post by samosamo on 2007-10-26
Did you read this guide?  I always found gentoo's wiki's very useful when compiling a kernel with hardware support

[http://gentoo-wiki.com/HARDWARE_Gentoo_on_Dell_Inspiron_600m](http://gentoo-wiki.com/HARDWARE_Gentoo_on_Dell_Inspiron_600m)

---

### Post by ctweb on 2007-10-26
I will give that a try, but I don't see anything new in there in relation to the hard drive.  Everything worked out of the box with no problem except for the hard drive.  I am up to 3 kernel compiles at 2.5mb/sec so it takes hours.  If I can't find a fix Ubuntu is gonna have to go because 9 other distros have been installed on this laptop without a problem.

---

### Post by Daelyn on 2007-10-28
> **ctweb said:**
> 
Ubuntu 7,10

```

sudo hdparm /dev/hda

/dev/hda:
 multcount     =  0 (off)
 IO_support    =  0 (default 16-bit)
 unmaskirq     =  0 (off)
 using_dma     =  0 (off)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 65535/16/63, sectors = 117210240, start = 0

```

Ubuntu 7.1

```

sudo hdparm -i /dev/hda

/dev/hda:

 Model=FUJITSU MHV2060AH, FwRev=00000096, SerialNo=NT25T592K7W4
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=117210240
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 3a:  ATA/ATAPI-2,3,4,5,6

 * signifies the current active mode

```



Copy of my stats (Ubuntu 7.10):

```
sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   6260 MB in  1.99 seconds = 3140.88 MB/sec
 Timing buffered disk reads:  120 MB in  3.01 seconds =  39.85 MB/sec
```

```
sudo hdparm /dev/sda

/dev/sda:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 14593/255/63, sectors = 234441648, start = 0
```

 ```
sudo hdparm -i /dev/sda

/dev/sda:

 Model=FUJITSU MHV2120BH PL                    , FwRev=00000029, SerialNo=        NW9BT6A2829T
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=234441648
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode

```

What I "thought" was, that there where no issue with your DMA, because, your 

```
sudo hdparm -i /dev/hda
```

showed

```
bla bla bla bla
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
bla bla bla bla

 * signifies the current active mode
```

By me reading that, I assumed (and still assume) that "Ultra DMA mode 5" is active.
My ubuntu does not specify "use_dma" when running hdparm.

Well, what do I know. I'm just a very fresh newbie anyways.

Hope someone else can shed some light on this issue. Sorry mate.

---

### Post by ctweb on 2007-10-31
Well I fixed it, but not the way I wanted to.

I ended up reinstalling Ubuntu and used Grub within Ubuntu to handle the booting.  I believe it is viewing the drive as a scsi, which might be the reason it works now.

I did not want to use grub as I am not familiar with it and I boot to BackTrack more often than Ubuntu.  Oh well maybe I will figure it out sometime.

Thanks for the help given



Daelyn,

I now have the same output you do, so something is being done to change the view of the hard drive in Ubuntu when using grub.

---

