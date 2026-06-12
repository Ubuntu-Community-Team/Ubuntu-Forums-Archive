---
title: "Extremely slow sata drive"
date: 2013-12-20
forum: Hardware
---

### Post by patrick.lafrance on 2013-12-20
Hi,
I have two different sata HDD showing extremely poor performances on various Linux distros including ubuntu 12.04 and 13.10. They work perfectly well under Windows XP.

 for both drives, "hdparm -Tt" shows :
Timing cached reads:   1032 MB in  2.00 seconds = 516.09 MB/sec
 Timing buffered disk reads:   8 MB in  3.13 seconds =   2.55 MB/sec

When copying a file using cp or dd, I get a transfert rate of around 5MB/s.

I get approximatively the same results with different kernels : 3.8.0-34-generic, mainline 3.12.5-031205-generic or even 2.6.32-25-generic-pae. Whenever I try with Ubuntu 12.04, 13.10, Archlinux or Fedora, they all show the same results. Live cds makes no difference.

Interestingly, palimpsests benchmark shows transfer rates for reading around 90MB/s wich is the expected rating. HDTune under Windows XP benchmark at 110MB/s.

any suggestions of where to look now?

Thanks for your help,

Here are some details on my system :

uname -a :
Linux rocinante 3.2.0-57-generic-pae #87-Ubuntu SMP Tue Nov 12 21:57:43 UTC 2013 i686 athlon i386 GNU/Linux

HDDs are : 
ATA WDC WD30EZRX-00D
ATA WDC WD10EAVS-00D

hdparm -I for both drives :

/dev/sda:

ATA device, with non-removable media
    Model Number:       WDC WD30EZRX-00D8PB0                    
    Serial Number:      WD-WCC4N0147228
    Firmware Revision:  80.00A80
    Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
    Supported: 9 8 7 6 5 
    Likely used: 9
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  268435455
    LBA48  user addressable sectors: 5860533168
    Logical  Sector size:                   512 bytes
    Physical Sector size:                  4096 bytes
    device size with M = 1024*1024:     2861588 MBytes
    device size with M = 1000*1000:     3000592 MBytes (3000 GB)
    cache/buffer size  = unknown
    Nominal Media Rotation Rate: 5400
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, with device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
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
       *    unknown 76[15]
       *    DMA Setup Auto-Activate optimization
            Device-initiated interface power management
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT LBA Segment Access (AC2)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
            unknown 206[12] (vendor specific)
            unknown 206[13] (vendor specific)
            unknown 206[14] (vendor specific)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
    not    frozen
    not    expired: security count
        supported: enhanced erase
    428min for SECURITY ERASE UNIT. 428min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee20928f748
    NAA        : 5
    IEEE OUI    : 0014ee
    Unique ID    : 20928f748
Checksum: correct

/dev/sdb:

ATA device, with non-removable media
    Model Number:       WDC WD10EAVS-00D7B1                     
    Serial Number:      WD-WCAU4A130358
    Firmware Revision:  01.01A01
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
    LBA48  user addressable sectors: 1953525168
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:      953869 MBytes
    device size with M = 1000*1000:     1000204 MBytes (1000 GB)
    cache/buffer size  = 8192 KBytes
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, with device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Recommended acoustic management value: 128, current value: 254
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
            Power-Up In Standby feature set
       *    SET_FEATURES required to spinup after power up
            SET_MAX security extension
            Automatic Acoustic Management feature set
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    64-bit World wide name
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
       *    DMA Setup Auto-Activate optimization
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
    238min for SECURITY ERASE UNIT. 238min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee1ac63d260
    NAA        : 5
    IEEE OUI    : 0014ee
    Unique ID    : 1ac63d260
Checksum: correct

---

### Post by patrick.lafrance on 2014-01-02
I finaly found the answer to my question. If it can help anyone, It seems the sata controller conflicted with the video card (Asus 210 with nvidia driver). Adding noapic to the kernel options solved the problem and my HDDs now transfer at >80MB/s.

---

