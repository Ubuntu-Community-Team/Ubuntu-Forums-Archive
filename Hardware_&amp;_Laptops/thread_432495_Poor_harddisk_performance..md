---
title: "Poor harddisk performance."
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by Deksan on 2007-05-04
Hi I have noticed poor hard disk performance since i have upgraded to fiesty from edgy.

Here some numbers :
```
time dd if=/dev/zero of=/tmp/test bs=512k count=2048
2048+0 records in
2048+0 records out
1073741824 bytes (1.1 GB) copied, 101.287 seconds, 10.6 MB/s

real    1m41.622s
user    0m0.000s
sys     0m5.812s
```

 ```
vmstat 1
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 0  4  33972  40364   8628 1089244    0    0   132  9480  655 4760  4 20 48 27
 0  4  33972  35528   8628 1089408    0    0     0  1480  699 4587  6  4  0 90
 0  4  33972  39744   8628 1089408    0    0     0  1560  784 2752  6  4  0 91
 0  4  33972  39720   8632 1089536    0    0   132  1836  818 3328  6  4 28 61
 1  4  33972  39720   8632 1089536    0    0     0  1328  698 3077  2  2  0 96
 0  5  33972  38764   8632 1089664    0    0   128 30616  850 2795  2  4  0 94
 0  5  33972  38268   8632 1089664    0    0     0 28336  549 3064  2  2  0 96
 0  5  33972  38456   8640 1089660    0    0     0  1428  739 3057  6  4  2 88
 2  5  33972  38580   8648 1089652    0    0     0   824  608 2801  2  1  0 97
 0  5  33972  38708   8648 1089792    0    0   128   692  621 3060  6  2  0 92
 0  4  33972  39700   8656 1089784    0    0     0  1100  682 3167  6  5  0 89
 0  5  33972  32920   7452 1097332    0    0     0 16592  684 5185  2 17  0 81
```

```

lspci | grep IDE
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
```


```
hdparm -I /dev/sdc

/dev/sdc:

ATA device, with non-removable media
        Model Number:       ST340014A                               
        Serial Number:      3JX2ESE7            
        Firmware Revision:  3.06    
Standards:
        Used: ATA/ATAPI-6 T13 1410D revision 2 
        Supported: 6 5 4 
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:   78165360
        LBA48  user addressable sectors:   78165360
        device size with M = 1024*1024:       38166 MBytes
        device size with M = 1000*1000:       40020 MBytes (40 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard
        R/W multiple sector transfer: Max = 16  Current = 16
        Recommended acoustic management value: 128, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
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
           *    DOWNLOAD_MICROCODE
                SET_MAX security extension
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
Security: 
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
HW reset results:
        CBLID- above Vih
        Device num = 1 determined by the jumper
Checksum: correct

```


Thanks for any help.

---

