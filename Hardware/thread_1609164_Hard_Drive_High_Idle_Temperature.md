---
title: "Hard Drive High Idle Temperature"
date: 2010-10-30
forum: Hardware
---

### Post by abdusamed on 2010-10-30
I can't change mine though with the help of laptop-mode-tools.. i was  able stop it spinning all the time but it still averages around 50  degree!!!!! I know its hot.
 this is what i get after run the acoustic command


A solution from 2008 exist but I don't know if safes to try
[url]http://www.networkedmediatank.com/showthread.php?tid=4037[url]

I'm on Ubuntu Lucid 10.04.1
2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64 GNU/Linux


hdparm version -

```

hdparm v9.15

```
 ```

~$ sudo hdparm -M 128 /dev/sda
 /dev/sda:
 setting acoustic management to 128
 HDIO_DRIVE_CMD:ACOUSTIC failed: Input/output error
 HDIO_DRIVE_CMD(identify) failed: Input/output error
~$

```This the info on it
 Note I have two physic HD
 ```

bahie@bahie-laptop:~$ sudo hdparm -I /dev/sda
 /dev/sda:
 ATA device, with non-removable media
    Model Number:       TOSHIBA MK4058GSX
    Serial Number:      Y8UBP1H0T
    Firmware Revision:  FF011M
    Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
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
    LBA48  user addressable sectors:  781422768
    Logical  Sector size:                   512 bytes
    Physical Sector size:                   512 bytes
    device size with M = 1024*1024:      381554 MBytes
    device size with M = 1000*1000:      400088 MBytes (400 GB)
    cache/buffer size  = 8192 KBytes
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Advanced power management level: 254
    DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5
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
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
       *    Idle-Unload when NCQ is active
       *    DMA Setup Auto-Activate optimization
            Device-initiated interface power management
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT Error Recovery Control (AC3)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
Security:
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        frozen
    not    expired: security count
    not    supported: enhanced erase
    166min for SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 5000039162685611
    NAA        : 5
    IEEE OUI    : 000039
    Unique ID    : 162685611
Checksum: correct

```

**2nd HDD**
```

bahie@bahie-laptop:~$ sudo hdparm -I /dev/sdb
 /dev/sdb:
 ATA device, with non-removable media
    Model Number:       TOSHIBA MK3252GSX
    Serial Number:      Y8I9COUQT
    Firmware Revision:  LV010M
    Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
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
    Logical  Sector size:                   512 bytes
    Physical Sector size:                   512 bytes
    device size with M = 1024*1024:      305245 MBytes
    device size with M = 1000*1000:      320072 MBytes (320 GB)
    cache/buffer size  = 8192 KBytes
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Advanced power management level: 254
    DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5
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
       *    Gen1 signaling speed (1.5Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
       *    Idle-Unload when NCQ is active
       *    DMA Setup Auto-Activate optimization
            Device-initiated interface power management
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT Error Recovery Control (AC3)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
Security:
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        frozen
    not    expired: security count
    not    supported: enhanced erase
    130min for SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50000391637048df
    NAA        : 5
    IEEE OUI    : 000039
    Unique ID    : 1637048df
Checksum: correct

```

---

