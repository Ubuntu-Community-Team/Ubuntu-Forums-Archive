---
title: "Setting sleep state fails"
date: 2013-03-25
forum: Hardware
---

### Post by Flynsarmy on 2013-03-25
I have some Western Digital 2TB blacks plugged into a RocketRaid 2760A RAID card on Ubuntu 12.10. When I do a
```
sudo hdparm -S 180 /dev/sdj
```
I get
> /dev/sdj:
 setting standby to 180 (15 minutes)
 HDIO_DRIVE_CMD(setidle) failed: Operation not permitted
Why is the operation not permitted?

Here are the relevant details of the drive:
> $ sudo hdparm -I /dev/sdj

/dev/sdj:

ATA device, with non-removable media
    Model Number:       WDC WD2002FAEX-007BA0                   
    Serial Number:      WD-xxxxxxxxx
    Firmware Revision:  05.01D05
    Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
    Supported: 8 7 6 5 
    Likely used: 8
Configuration:
    Logical     max current
    cylinders   16383   16383
    heads       16  16
    sectors/track   63  63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  268435455
    LBA48  user addressable sectors: 3907029168
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:     1907729 MBytes
    device size with M = 1000*1000:     2000398 MBytes (2000 GB)
    cache/buffer size  = unknown
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, with device specific minimum
    R/W multiple sector transfer: Max = 16  Current = 0
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
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
       *    NOP cmd
       *    DOWNLOAD_MICROCODE
            Power-Up In Standby feature set
       *    SET_FEATURES required to spinup after power up
            SET_MAX security extension
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    64-bit World wide name
       *    WRITE_UNCORRECTABLE_EXT command
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Gen3 signaling speed (6.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
       *    NCQ priority information
            DMA Setup Auto-Activate optimization
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT Long Sector Access (AC1)
       *    SCT LBA Segment Access (AC2)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
            unknown 206[12] (vendor specific)
            unknown 206[13] (vendor specific)
Security: 
    Master password revision code = 65534
        supported
    not enabled
    not locked
    not frozen
    not expired: security count
        supported: enhanced erase
    308min for SECURITY ERASE UNIT. 308min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee2b238ee75
    NAA     : 5
    IEEE OUI    : 0014ee
    Unique ID   : 2b238ee75
Checksum: correct

---

