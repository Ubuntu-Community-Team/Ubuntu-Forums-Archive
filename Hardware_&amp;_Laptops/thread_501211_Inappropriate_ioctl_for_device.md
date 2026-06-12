---
title: "Inappropriate ioctl for device"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by gerryscat on 2007-07-15
I have installed 7.04 but it seems slow. I used to have XP on this system (1 Ghz Celeron/256 meg) and with a little tweaking was able to watch HD downloads. With Ubuntu the video is unwatchable.

I read (at [http://opensource.apress.com/article...ne-gems-hdparm](http://opensource.apress.com/article...ne-gems-hdparm)) I need to change my harddrive settings to enable DMA, but it doesn't work. My HD is terrible, looks like it is running in 16 bit mode:

sudo hdparm -tT /dev/sda

/dev/sda:
Timing cached reads: 282 MB in 2.01 seconds = 140.24 MB/sec
Timing buffered disk reads: 24 MB in 3.03 seconds = 7.91 MB/sec

sudo hdparm /dev/sda

/dev/sda:
IO_support = 0 (default 16-bit)

sudo hdparm -m16 /dev/sda

/dev/sda:
setting multcount to 16
HDIO_SET_MULTCOUNT failed: Inappropriate ioctl for device
HDIO_GET_MULTCOUNT failed: Inappropriate ioctl for device

readonly = 0 (off)
readahead = 256 (on)
geometry = 3648/255/63, sectors = 58605120, start = 0

sudo hdparm -i /dev/sda

/dev/sda:

Model=FUJITSU MHR2030AT , FwRev=30B8 , SerialNo= NJ17T2212JMP
Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=?8?
CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=58605120
IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
PIO modes: pio0 pio1 pio2 pio3 pio4
DMA modes: mdma0 mdma1 mdma2
UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma3 udma4 *udma5
AdvancedPM=yes: mode=0x80 (12 WriteCache=enabled
Drive conforms to: ATA/ATAPI-6 T13 1410D revision 1: ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

* signifies the current active mode

So, anybody know why I'm getting inappropriate ioctl for device, and how I get the appropriate one? How can I speed up my HD?

Also, there is a command to set DMA, -c I think, but it just gives me invalid parameter. Odd.

thanks,
Gerry

---

### Post by Jamie Jackson on 2007-07-16
I might be in the same boat. I was following a howto for speeding up cd/dvdrom access, because I'm getting slow read speed during DVD ripping. However, I wasn't able to enable DMA either. I've read a bunch of threads on the subject, but I've had a hard time figuring out which issues apply to me and which don't.

```
jamie@mercury:~$ sudo hdparm /dev/scd0

/dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

jamie@mercury:~$ sudo hdparm -tT /dev/scd0

/dev/scd0:
 Timing cached reads:   2144 MB in  2.00 seconds = 1072.32 MB/sec
 Timing buffered disk reads:    8 MB in  3.16 seconds =   2.53 MB/sec

jamie@mercury:~$ sudo hdparm -d1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

```

...and same questions about my HD:
```
jamie@mercury:~$ sudo hdparm /dev/sda

/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 9729/255/63, sectors = 156301488, start = 0

jamie@mercury:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   2110 MB in  2.00 seconds = 1056.08 MB/sec
 Timing buffered disk reads:  110 MB in  3.04 seconds =  36.17 MB/sec


jamie@mercury:~$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

```



So, would DMA help me? If so, how do I set it?

Thanks,
Jamie

---

### Post by uopjohnson on 2007-08-16
any answers to this?

---

### Post by psypher on 2007-12-10
got the same issue, cannot set dma or IO. but I found this post:

[http://www.linuxquestions.org/questions/susenovell-60/copy-files-from-partition-to-partition-too-slow-sata-hard-disk.what-should-i-do-377370/](http://www.linuxquestions.org/questions/susenovell-60/copy-files-from-partition-to-partition-too-slow-sata-hard-disk.what-should-i-do-377370/)

they say dma is irrelevant on sata drives. but still drive seems slow

any answer on this? Please there has been no usefull posts from anyone in the know yet.

---

### Post by JoshuaJamZ on 2007-12-10
> **Jamie Jackson said:**
> I might be in the same boat. I was following a howto for speeding up cd/dvdrom access, because I'm getting slow read speed during DVD ripping. However, I wasn't able to enable DMA either. I've read a bunch of threads on the subject, but I've had a hard time figuring out which issues apply to me and which don't.

```
jamie@mercury:~$ sudo hdparm /dev/scd0

/dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

jamie@mercury:~$ sudo hdparm -tT /dev/scd0

/dev/scd0:
 Timing cached reads:   2144 MB in  2.00 seconds = 1072.32 MB/sec
 Timing buffered disk reads:    8 MB in  3.16 seconds =   2.53 MB/sec

jamie@mercury:~$ sudo hdparm -d1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

```


For your DVD, I would suggest:

```

sudo hdparm -d1 -X66 /dev/YOUR DEVICE

```

This will set UDMA mode to 2. This works for me, only problem is getting it to stay after a reboot, which is how I stumbled on this thread. 

> 
...and same questions about my HD:
```
jamie@mercury:~$ sudo hdparm /dev/sda

/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 9729/255/63, sectors = 156301488, start = 0

jamie@mercury:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   2110 MB in  2.00 seconds = 1056.08 MB/sec
 Timing buffered disk reads:  110 MB in  3.04 seconds =  36.17 MB/sec


jamie@mercury:~$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

```



So, would DMA help me? If so, how do I set it?

Thanks,
Jamie


As far as HD, just a guess, but maybe using hdparm to restore hardware defaults? :

```

sudo hdparm -X00 /dev/YOUR DEVICE

```

Anybody know how to get the UDMA mode setting to set upon boot?

---

### Post by JoshuaJamZ on 2007-12-10
Adding this line to /etc/hdparm.conf sets the DMA "on" and UDMA mode "2" at boot for my DVD burner:

```

command_line {
        hdparm -d1 -X66 /dev/dvdrw
}
```

Replace "dvdrw" with your device appropriately :)

I do still get the error:

```

HDIO_GETGEO failed: Inappropriate ioctl for device
```

But, the device works fine...

---

### Post by benash on 2008-02-27
I was having the same problem.  I'm running Ubuntu 7.10 on a Thinkpad - a T41p.  When I played DVDs, 100% of the CPU was taken up and playback was choppy.  Also, trying to enable DMA didn't do anything and gave an error:

```
benash@t41p:~$ sudo hdparm -d1 /dev/scd0 

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

```

I looked at the output of dmesg, though, and it looked like the DVD drive was using something called UDMA:

```
[    4.524000] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4242N, 0201, max UDMA/33
[    4.696000] ata2.00: configured for UDMA/33
[    4.696000] scsi 0:0:0:0: Direct-Access     ATA      HTS726060M9AT00  MH4O PQ: 0 ANSI: 5
[    4.700000] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4242N 0201 PQ: 0 ANSI: 5
```

It looked like that was running OK, so I thought the DMA/hdparm thing might not be the right route.  I went to System->Administration->"Restricted Drivers Manager" and disabled the ATI driver.  Then I rebooted, allowing the free ati driver to be used instead.

DVD playback was fine after this.

---

### Post by doxola on 2008-05-23
> **benash said:**
> I was having the same problem...

It looked like that was running OK, so I thought the DMA/hdparm thing might not be the right route.  I went to System->Administration->"Restricted Drivers Manager" and disabled the ATI driver.  Then I rebooted, allowing the free ati driver to be used instead.

DVD playback was fine after this.

I am on 8.04, and disabling that ATI driver did the trick.  Thanks for the tip.

:popcorn:

---

