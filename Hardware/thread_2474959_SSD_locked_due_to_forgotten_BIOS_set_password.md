---
title: "SSD locked due to forgotten BIOS set password"
date: 2022-05-12
forum: Hardware
---

### Post by erotavlas on 2022-05-12
Hi,
                                            
          I have a problem with a 512 SSD made by Intenso. I forgot the  password set by BIOS. Afterwards I used a live USB and tried with the  hdparm tool. I followed [this guide]("https://rotadev.com/how-to-unlock-an-ssd-disk-with-hdparm-server-fault/"), but I was unsuccessful. What can I do?

```

sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
        Model Number:       JAJS600M512C                            
        Serial Number:      AB202100000002201011
        Firmware Revision:  U0309A0 
        Media Serial Num:   
        Media Manufacturer: 
        Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
        Used: unknown (minor revision code 0x011b) 
        Supported: 10 9 8 7 6 5 
        Likely used: 10
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:    16514064
        LBA    user addressable sectors:   268435455
        LBA48  user addressable sectors:  1000215216
        Logical  Sector size:                   512 bytes
        Physical Sector size:                   512 bytes
        Logical Sector-0 offset:                  0 bytes
        device size with M = 1024*1024:      488386 MBytes
        device size with M = 1000*1000:      512110 MBytes (512 GB)
        cache/buffer size  = unknown
        Form Factor: 2.5 inch
        Nominal Media Rotation Rate: Solid State Device
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 1   Current = 1
        Advanced power management level: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
           *    Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    NOP cmd
           *    DOWNLOAD_MICROCODE
           *    Advanced Power Management feature set
           *    48-bit Address feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    General Purpose Logging feature set
           *    WRITE_{DMA|MULTIPLE}_FUA_EXT
           *    WRITE_UNCORRECTABLE_EXT command
           *    {READ,WRITE}_DMA_EXT_GPL commands
           *    Segmented DOWNLOAD_MICROCODE
           *    Gen1 signaling speed (1.5Gb/s)
           *    Gen2 signaling speed (3.0Gb/s)
           *    Gen3 signaling speed (6.0Gb/s)
           *    Native Command Queueing (NCQ)
           *    Phy event counters
           *    READ_LOG_DMA_EXT equivalent to READ_LOG_EXT
           *    DMA Setup Auto-Activate optimization
           *    Software settings preservation
           *    DOWNLOAD MICROCODE DMA command
           *    WRITE BUFFER DMA command
           *    READ BUFFER DMA command
           *    Data Set Management TRIM supported (limit 8 blocks)
Security: 
        Master password revision code = 65534
                supported
                enabled
                locked
        not     frozen
        not     expired: security count
                supported: enhanced erase
        Security level high
        6min for SECURITY ERASE UNIT. 6min for ENHANCED SECURITY ERASE UNIT.
Checksum: correct

hdparm --user-master u --security-set-pass p /dev/sda 
security_password: "p"

/dev/sda:
 Issuing SECURITY_SET_PASS command, password="p", user=user, mode=high
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 04 51 40 00 21 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
hdparm --user-master u --security-erase p /dev/sda 
security_password: "p"

/dev/sda:
 Issuing SECURITY_ERASE command, password="p", user=user
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 04 51 40 00 21 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
hdparm --user-master u --security-disable NULL /dev/sda 
security_password: ""

/dev/sda:
 Issuing SECURITY_DISABLE command, password="", user=user
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 04 51 40 00 21 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 04 51 40 00 21 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00


```

---

