---
title: "Hard drive is noiser in Ubuntu than other OS's"
date: 2011-05-09
forum: Hardware
---

### Post by Ubom on 2011-05-09
For some reason my Acer Travelmate 8371 seems to experience much louder hdd noise under Ubuntu 11.04 than other distributions such as Debian or even Windows XP and 7.

Here is the output of hdparm incase it is important
```
/dev/sda:

ATA device, with non-removable media
    Model Number:       WDC WD3200BEVT-22ZCT0                   
    Serial Number:      WD-WXC0A6922599
    Firmware Revision:  11.01A11
    Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5
Standards:
    Supported: 8 7 6 5 
    Likely used: 8
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  268435455
    LBA48  user addressable sectors:  625142448
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:      305245 MBytes
    device size with M = 1000*1000:      320072 MBytes (320 GB)
    cache/buffer size  = 8192 KBytes
    Nominal Media Rotation Rate: 5400
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, with device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 0
    Advanced power management level: 128
    Recommended acoustic management value: 128, current value: 128
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    NOP cmd
       *    DOWNLOAD_MICROCODE
       *    Advanced Power Management feature set
            SET_MAX security extension
       *    Automatic Acoustic Management feature set
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    WRITE_{DMA|MULTIPLE}_FUA_EXT
       *    64-bit World wide name
       *    IDLE_IMMEDIATE with UNLOAD
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
       *    DMA Setup Auto-Activate optimization
            Device-initiated interface power management
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT Long Sector Access (AC1)
       *    SCT LBA Segment Access (AC2)
       *    SCT Error Recovery Control (AC3)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
            unknown 206[12] (vendor specific)
            unknown 206[13] (vendor specific)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
    not    frozen
    not    expired: security count
        supported: enhanced erase
    102min for SECURITY ERASE UNIT. 102min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee2adaf90aa
    NAA        : 5
    IEEE OUI    : 0014ee
    Unique ID    : 2adaf90aa
Checksum: correct

```

---

