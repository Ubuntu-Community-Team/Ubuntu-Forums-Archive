---
title: "Warm disk in 9.10"
date: 2009-11-25
forum: Hardware
---

### Post by uncledeath on 2009-11-25
Hi,

After installing ubuntu 9.10 32Bit (earlier 9.04, 8.10 and 8.04) I noticed extensive heat going from my harddrive. Currently after many hours of Idle my drive holds at 49 degrees Celcius which makes the whole laptop warm. 

Hardware:
6710b HP Compaq laptop
Samsung HM320JI 320GB

I suspect bad hdparm settings causing these problems. I also have to mention that I have a huge load/unload cycle problem when I run on battery and that makes me force hdparm -B 254 /dev/sda each time I plug AC power off to avoid disk damage. This bug was never solved for me since ubuntu 8.04 and I have to deal with it the hard way. Nevertheless extensive heat was produced since the installation and -B 254 had nothing to do with it. If there will be no suggestions I will try installing older ubuntu version to confirm that it is not a hardware issue (temperatures on earlier ubuntu versions were noticeably lower but I can't remember exact values).

My hdparm -I:
```

qba@6710b:~$ sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
    Model Number:       SAMSUNG HM320JI                         
    Serial Number:      S16LJD0Q319885      
    Firmware Revision:  2SS00_01
    Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5
Standards:
    Used: ATA/ATAPI-7 T13 1532D revision 0 
    Supported: 8 7 6 5 & some of 8
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
    cache/buffer size  = 8192 KBytes (type=DualPortCache)
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Advanced power management level: 254
    Recommended acoustic management value: 254, current value: 254
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 udma7 
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
       *    64-bit World wide name
       *    IDLE_IMMEDIATE with UNLOAD
       *    Write-Read-Verify feature set
       *    WRITE_UNCORRECTABLE_EXT command
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
            DMA Setup Auto-Activate optimization
            Device-initiated interface power management
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT Long Sector Access (AC1)
       *    SCT LBA Segment Access (AC2)
       *    SCT Error Recovery Control (AC3)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
    not    frozen
    not    expired: security count
        supported: enhanced erase
    116min for SECURITY ERASE UNIT. 116min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50f0000001319885
    NAA        : 5
    IEEE OUI    : 0f0000
    Unique ID    : 001319885
Checksum: correct

```I guess my battery time will be affected too by the extensive heat generation but I haven't checked that yet. If this turns into a bug it may be dangerous to other users too.

---

### Post by Sentience on 2009-11-28
Check the other threads. Karmic has probably done millions of dollars worth of damage, maybe tens of millions. It has been destroying peoples laptops and external harddrives.

---

