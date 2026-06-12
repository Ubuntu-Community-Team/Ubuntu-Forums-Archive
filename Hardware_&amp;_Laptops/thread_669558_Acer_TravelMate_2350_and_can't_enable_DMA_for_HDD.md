---
title: "Acer TravelMate 2350 and can't enable DMA for HDD"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by gacolek on 2008-01-16
Hi everybody,

I have laptop Acer TravelMate 2350 with 1,4GHz and 256MB Ram and I decided installing Xubuntu because I want to use a fast graphical environment. So after installing this I have disappointed because it isn't fast :/ When I look on my top command i have:
```
top - 21:37:31 up 16 min,  2 users,  load average: 0.23, 0.52, 0.53
Tasks:  86 total,   3 running,  82 sleeping,   0 stopped,   1 zombie
Cpu(s):  5.0%us,  0.7%sy,  0.0%ni, 90.7%id,  3.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    239688k total,   233752k used,     5936k free,     3156k buffers
Swap:   497972k total,    84596k used,   413376k free,    66576k cached

```

so my Xubuntu take me my all Ram memory and 84MB swap, but I open only Firefox now and Kadu. I try to disable some unnecessary process according to this post: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491) but it isn't change :/ I also try to speed up my disk to enable DMA mode and another option according to this post: [http://ubuntuforums.org/showthread.php?t=459101](http://ubuntuforums.org/showthread.php?t=459101) , but I have that like error:
```
/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

```

my IDE is:
```
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)

```

and my disk is:
```
ATA device, with non-removable media
        Model Number:       HTS424040M9AT00                         
        Serial Number:      MPA248Q2HYAD9E
        Firmware Revision:  MA2OA71A
Standards:
        Used: ATA/ATAPI-6 T13 1410D revision 3a 
        Supported: 6 5 4 
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:   78140160
        LBA48  user addressable sectors:   78140160
        device size with M = 1024*1024:       38154 MBytes
        device size with M = 1000*1000:       40007 MBytes (40 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Vendor, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Advanced power management level: 128 (0x80)
        Recommended acoustic management value: 128, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    NOP cmd
           *    Advanced Power Management feature set
                Power-Up In Standby feature set
           *    SET_FEATURES required to spinup after power up
                Address Offset Reserved Area Boot
                SET_MAX security extension
                Automatic Acoustic Management feature set
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
Security: 
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
        34min for SECURITY ERASE UNIT. 
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper
Checksum: correct

```

my present configuration of my disk is:
```
/dev/sda:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 4864/255/63, sectors = 78140160, start = 0

```

Anybody now how I solve problem with enabling DMA on my disk, and how to speed up Xubuntu because now it works worst than win xp on my laptop :/

Thanks for answer.

---

