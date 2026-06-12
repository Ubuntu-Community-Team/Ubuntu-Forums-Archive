---
title: "help me improve my HD performance"
date: 2007-03-02
forum: Hardware &amp; Laptops
---

### Post by brazzmonkey on 2007-03-02
out of curiosity, tonite i ran hdparm -I on my laptop's HDs. here's what i got :```

$ sudo hdparm -I /dev/sda
Password:

/dev/sda:

ATA device, with non-removable media
        Model Number:       SAMSUNG HM120JI
        Serial Number:      S09GJ10L513326
        Firmware Revision:  YF100-10
Standards:
        Used: ATA/ATAPI-7 T13 1532D revision 0
        Supported: 7 6 5 4
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  234441648
        LBA48  user addressable sectors:  234441648
        device size with M = 1024*1024:      114473 MBytes
        device size with M = 1000*1000:      120034 MBytes (120 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Advanced power management level: unknown setting (0x0080)
        Recommended acoustic management value: 254, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 udma7
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
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
                NOP cmd
           *    DOWNLOAD_MICROCODE
                Advanced Power Management feature set
           *    SET_MAX security extension
           *    Automatic Acoustic Management feature set
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
                General Purpose Logging feature set
           *    IDLE_IMMEDIATE with UNLOAD
           *    SATA-I signaling speed (1.5Gb/s)
           *    Native Command Queueing (NCQ)
           *    Host-initiated interface power management
           *    Phy event counters
                DMA Setup Auto-Activate optimization
                Device-initiated interface power management
           *    Software settings preservation
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
                frozen
        not     expired: security count
                supported: enhanced erase
        88min for SECURITY ERASE UNIT. 88min for ENHANCED SECURITY ERASE UNIT.
Checksum: correct

```
i thought everything should already be quite optimized, but a few things make me believe it's not :
- "Supported: 7 6 5 4" and "*udma6" : i should be able to set it to udma7 instead, shouldn't i ?
- "Advanced Power Management feature set", " Device-initiated interface power management" : any tips to get good powersavings when needed ?
- "DMA Setup Auto-Activate optimization" : what does this mean ?

any other tips to improve performance when laptop is plugged-in, and powersaving when running on battery ?

tia !

---

### Post by sjrixon on 2007-03-02
Me too..

```
ATA device, with non-removable media
        Model Number:       HTS541080G9SA00                         
        Serial Number:      MPBDLAXKKEH6GG
        Firmware Revision:  MB4OC60R
Standards:
        Used: ATA/ATAPI-7 T13 1532D revision 1 
        Supported: 7 6 5 4 
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
        Queue depth: 32
        Standby timer values: spec'd by Vendor, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 0
        Advanced power management level: 128 (0x80)
        Recommended acoustic management value: 128, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=240ns  IORDY flow control=120ns

```

I think it's a SATA thing on the laptops.. Hence doing it to sd not hd.. I can't burn a DVD (well can but it's slow) and I think it's related.

---

### Post by brazzmonkey on 2007-03-02
weirdo... one noticeable difference, though : on my laptop, udma7 is explicitely listed, whereas yours lists udma5 (but i admit it "seems" to be supported). or maybe the ATA bus supports up to udma7, but HD supports up to udma5/6 ?

---

### Post by brazzmonkey on 2007-03-04
i haven't been able to switch to udma7 :(

---

### Post by brazzmonkey on 2007-03-04
eh i just found out that i should use sdparm instead of hdparm... or should i ?

---

