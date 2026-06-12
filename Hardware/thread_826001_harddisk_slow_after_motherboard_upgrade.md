---
title: "harddisk slow after motherboard upgrade"
date: 2008-06-11
forum: Hardware
---

### Post by drsar on 2008-06-11
Hi,
I had to install a new motherboard (Asus P5N-MX) after the old one died. I was pleasently surprised to find that I could still boot and X still worked since I am using an external graphics card.

The problem is that everything seems so slow. I think it has to do with the harddisk:
```
$ time dd if=/dev/zero of=/tmp/test bs=512k count=128
128+0 records in
128+0 records out
67108864 bytes (67 MB) copied, 10.7213 seconds, 6.3 MB/s

real    0m12.355s
user    0m0.244s
sys     0m12.101s

```
The same on a similar computer comes back with a factor 50 faster write rate. The following test seems OK:
```
$ sudo hdparm -T /dev/sda

/dev/sda:
 Timing cached reads:   1794 MB in  2.00 seconds = 897.45 MB/sec
```

Sometimes I am getting errors doing a health check with smartmontools:
```

$ sudo smartctl -H /dev/sda
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Warning! SMART Attribute Data Structure error: invalid SMART checksum.
Warning! SMART Attribute Thresholds Structure error: invalid SMART checksum.
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
Please note the following marginal Attributes:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
 50 Unknown_Attribute       0x2100   000   000   000    Old_age   Offline  FAILING_NOW 51677046505472
109 Unknown_Attribute       0x6170   116   046   112    Old_age   Offline  In_the_past 36284725620595
108 Unknown_Attribute       0x732e   111   046   046    Old_age   Always   In_the_past 3298534817841
 97 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 215586600906752
 97 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 215586600906752
 97 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 1640845312
 74 Unknown_Attribute       0xc413   042   000   019    Pre-fail  Always   In_the_past 0
 97 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 215586600906752

```

And finally, here is some more diagnostics:
```

$ sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
        Model Number:       WDC WD800JD-60LSA0                      
        Serial Number:      WD-WCAM9D045445
        Firmware Revision:  07.01D07
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
        LBA    user addressable sectors:  156301488
        LBA48  user addressable sectors:  156301488
        device size with M = 1024*1024:       76319 MBytes
        device size with M = 1000*1000:       80026 MBytes (80 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard, with device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 1
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
                SMART feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    NOP cmd
           *    DOWNLOAD_MICROCODE
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    SATA-I signaling speed (1.5Gb/s)
           *    Host-initiated interface power management
           *    Phy event counters
                Device-initiated interface power management
           *    Software settings preservation
           *    SMART Command Transport (SCT) feature set
           *    SCT Long Sector Access (AC1)
           *    SCT LBA Segment Access (AC2)
           *    SCT Error Recovery Control (AC3)
           *    SCT Features Control (AC4)
           *    SCT Data Tables (AC5)
                unknown 206[12]
Checksum: correct

```

So the main problem is the slow speed which leads I would think to very slow loading of X, login scripts etc.

Any help would be much appreciated.

drsar.

---

