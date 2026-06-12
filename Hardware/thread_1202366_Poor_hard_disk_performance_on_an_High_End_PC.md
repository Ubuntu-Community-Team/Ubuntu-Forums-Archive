---
title: "Poor hard disk performance on an High End PC"
date: 2009-07-02
forum: Hardware
---

### Post by xomoxo on 2009-07-02
Hi,

I've Kubuntu Jaunty 64 bits installed on my computer, its hardware is:
- Processor Intel Core i7 920 overclocked at 3.0Ghz
- Motherboard Gigabyte EX58-DS4
- RAM 3Gb DDR3
- Harddisk Seagate ST3640323AS
- SATA controller (in motherboard) 82801JI (ICH10 Family) SATA AHCI Controller  

My filesystem is XFS.

When I make a system update, copy something from network to my computer, when I try to copy something to a USB memory, try to unrar some files, etc. The system gets very very slow until the disk access finish, sometimes appears that all is hanged.

I've the system updated, my kernel is 2.6.28-13-generic #44-Ubuntu SMP x86_64 GNU/Linux

Please, help to me, I don't know what to do. It isn't normal that this things succeed on this PC.

My hard disk information:
```
/dev/sda:

ATA device, with non-removable media
        Model Number:       ST3640323AS                             
        Serial Number:      5VK04VS9                                
        Firmware Revision:  SD35                                    
        Transport:          Serial                                  
Standards:                                                          
        Used: unknown (minor revision code 0x0029)                  
        Supported: 8 7 6 5                                          
        Likely used: 8                                              
Configuration:                                                      
        Logical         max     current                             
        cylinders       16383   16383                               
        heads           16      16                                  
        sectors/track   63      63                                  
        --                                                          
        CHS current addressable sectors:   16514064                 
        LBA    user addressable sectors:  268435455                 
        LBA48  user addressable sectors: 1250263728                 
        device size with M = 1024*1024:      610480 MBytes          
        device size with M = 1000*1000:      640135 MBytes (640 GB) 
Capabilities:                                                       
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = ?
        Recommended acoustic management value: 254, current value: 0
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
           *    DOWNLOAD_MICROCODE
                SET_MAX security extension
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    64-bit World wide name
           *    Write-Read-Verify feature set
           *    WRITE_UNCORRECTABLE_EXT command
           *    {READ,WRITE}_DMA_EXT_GPL commands
           *    Segmented DOWNLOAD_MICROCODE
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-II signaling speed (3.0Gb/s)
           *    Native Command Queueing (NCQ)
           *    Phy event counters
                Device-initiated interface power management
           *    Software settings preservation
           *    SMART Command Transport (SCT) feature set
           *    SCT Long Sector Access (AC1)
           *    SCT Error Recovery Control (AC3)
           *    SCT Features Control (AC4)
           *    SCT Data Tables (AC5)
                unknown 206[12] (vendor specific)
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
                supported: enhanced erase
        116min for SECURITY ERASE UNIT. 116min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 5000c500101a1726
        NAA             : 5
        IEEE OUI        : c50
        Unique ID       : 0101a1726
Checksum: correct

```

Performance with hdparm:
/dev/sda:
 Timing cached reads:   16690 MB in  2.00 seconds = 8353.43 MB/sec
 Timing buffered disk reads:  340 MB in  3.02 seconds = 112.72 MB/sec

Thanks for all.

---

### Post by snek on 2009-07-02
Strange, those hdparm timings are quite good for a single drive tbh..
Here's one from my machine at work (iMac 20"):

> 
/dev/sda3:
 Timing cached reads:   5866 MB in  2.00 seconds = 2939.56 MB/sec
 Timing buffered disk reads:  188 MB in  3.02 seconds =  62.23 MB/sec
 

I don't notice any slowdowns, but my speeds are much lower..
Mind you this is using EXT3, but at home I have 3 XFS drives which are even slower but also they don't have any kind of slowdown on the system.

Maybe it has something to do with the driver for your harddrive controller?
Does your load increase greatly and does your CPU usage jump up as well?

---

### Post by xomoxo on 2009-07-02
The CPU load didn't grow, only a 33% in one core. A friend said to me that he get the same problem with a seagate harddisk at home and Ubuntu.

---

