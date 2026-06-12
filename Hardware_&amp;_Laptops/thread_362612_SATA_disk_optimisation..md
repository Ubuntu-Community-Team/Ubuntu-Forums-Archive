---
title: "SATA disk optimisation."
date: 2007-02-15
forum: Hardware &amp; Laptops
---

### Post by The Spacial Sprite on 2007-02-15
Hello everybody out there !

   Here are the important elements of my configuration for my present problem:

      -- Intel Core 2 Duo T7200 (2.0GHz 667MHz FSB);
      -- hard drive 100Go SATA 7200TPM;
      -- DVD reader and brurner 8x DVD+/- RW SATA;
      -- Ubuntu Edgy Eft 6.10 AMD64.

   Sometime, the harddrive access are slow. Moreover, DVD reading is jerky. None of the documentation I have found on the Internet helps me to solve the problem. Is there anyone who has any idea ?

   Best regards.

                                                                                                                                              The Spacial Sprite

---

### Post by dcstar on 2007-02-15
> **The Spacial Sprite said:**
> Hello everybody out there !

   Here are the important elements of my configuration for my present problem:

      -- Intel Core 2 Duo T7200 (2.0GHz 667MHz FSB);
      -- hard drive 100Go SATA 7200TPM;
      -- DVD reader and brurner 8x DVD+/- RW SATA;
      -- Ubuntu Edgy Eft 6.10 AMD64.

   Sometime, the harddrive access are slow. Moreover, DVD reading is jerky. None of the documentation I have found on the Internet helps me to solve the problem. Is there anyone who has any idea ?

   Best regards.

                                                                                                                                              The Spacial Sprite
To check DMA settings:

```
sudo hdparm /dev/whatever-you-disks-are
```

Also what kernel are you using?

---

### Post by The Spacial Sprite on 2007-02-16
Hello everybody out there !

   Here are the results of some commands I have typed in a terminal :

 ```
$ sudo hdparm /dev/sda

/dev/sda:
 IO_support    =  0 (default 16-bit)
 readonly        =  0  (off)
 readahead     = 256 (on)
 geometry       = 12161/255/63, sectors = 195371568, start = 0
```

 ```
$ sudo hdparm /dev/scd0

/dev/scd0:
 readonly        =  0  (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
```

```
$ uname -r
2.6.17-11-generic
```

   Best regards.

                                                                                                                                                 The Spacial Sprite

---

### Post by eeried on 2007-03-02
They say DMA doesn't need to be enabled for SATA HDD.

you can check perforamnces issuing this command:
```
 sudo hdparm -tT /dev/sda
```

This is the result on a 160MB  Maxtor :
```
/dev/sda:
 Timing cached reads:   2180 MB in  2.00 seconds = 1089.93 MB/sec
 Timing buffered disk reads:   78 MB in  3.00 seconds =  26.00 MB/sec
```
I doubt it's quite all right

here's another useful command:

```
sudo hdparm -I /dev/sda
```
and its ouput:
```

sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
        Model Number:       Maxtor 6L160M0
        Serial Number:      L41L1QHG
        Firmware Revision:  BACE1G10
Standards:
        Supported: 7 6 5 4
        Likely used: 7
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors:  320173056
        device size with M = 1024*1024:      156334 MBytes
        device size with M = 1000*1000:      163928 MBytes (163 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Advanced power management level: unknown setting (0x0000)
        Recommended acoustic management value: 192, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    NOP cmd
           *    READ BUFFER cmd
           *    WRITE BUFFER cmd
           *    Host Protected Area feature set
           *    Look-ahead
           *    Write cache
           *    Power Management feature set
                Security Mode feature set
           *    SMART feature set
           *    FLUSH CACHE EXT command
           *    Mandatory FLUSH CACHE command
           *    Device Configuration Overlay feature set
           *    48-bit Address feature set
           *    Automatic Acoustic Management feature set
                SET MAX security extension
                Advanced Power Management feature set
           *    DOWNLOAD MICROCODE cmd
           *    General Purpose Logging feature set
           *    SMART self-test
           *    SMART error logging
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
Checksum: correct
```

DMA doesn't seem to be supported (not in the "Commands/features"  list but that doesn't make much sense, does it?

Anyway what do you think of the HDD performances?

cheers, and have a good week-end :guitar:

---

### Post by The Spacial Sprite on 2007-03-02
Hello everybody out there !

   I thank you, Erieed, but I already know this commands, and it has not help me. Anyway, DMA optimisation does not have any sense for SATA peripherics.

   Actually, I think I know the reason of my problems : this this not a matter with my disks, but with my motherboard, which is not totally suported by the kernel I use. I need a much recent one.

   Best regards.

                                                                                                                                                   The Spacial Sprite

---

