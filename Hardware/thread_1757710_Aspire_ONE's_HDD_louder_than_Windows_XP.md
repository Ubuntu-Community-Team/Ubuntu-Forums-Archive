---
title: "Aspire ONE's HDD louder than Windows XP?"
date: 2011-05-13
forum: Hardware
---

### Post by the_mouse on 2011-05-13
I've been using Kubuntu (9.10, I know it's outdated) on my netbook (Aspire ONE 150) for a while, but there's one thing that annoys me. It's TOSHIBA HDD is much louder when skeeking in Ubuntu, than in Windows XP. 

Here's the output of 
```
/dev/sda:

ATA device, with non-removable media
        Model Number:       TOSHIBA MK1652GSX                       
        Serial Number:      X8K7P0R5T                               
        Firmware Revision:  LV020J                                  
        Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5
Standards:                                                                               
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
        LBA48  user addressable sectors:  312581808                                      
        device size with M = 1024*1024:      152627 MBytes                               
        device size with M = 1000*1000:      160041 MBytes (160 GB)                      
Capabilities:                                                                            
        LBA, IORDY(can be disabled)                                                      
        Queue depth: 32                                                                  
        Standby timer values: spec'd by Standard, no device specific minimum             
        R/W multiple sector transfer: Max = 16  Current = 16                             
        Advanced power management level: 254                                             
        DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5    
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
           *    SATA-I signaling speed (1.5Gb/s)                                         
           *    Native Command Queueing (NCQ)                                            
           *    Host-initiated interface power management                                
           *    Phy event counters                                                       
           *    unknown 76[11]                                                           
                DMA Setup Auto-Activate optimization
                Device-initiated interface power management
           *    Software settings preservation
           *    SMART Command Transport (SCT) feature set
           *    SCT Error Recovery Control (AC3)
           *    SCT Features Control (AC4)
           *    SCT Data Tables (AC5)
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
        66min for SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 5000391524871a4
        NAA             : 5
        IEEE OUI        : 39
        Unique ID       : 1524871a4
Checksum: correct
```

I tried setting accoustic management settigns via hdparm, but I get an error saying it's not supported by the HDD. However there seems to be some way to control the noise comming out of the HDD in Windows, since it's not that loud on seeking.

```
sudo hdparm -M /dev/sda

/dev/sda:
 acoustic      = not supported
```


The noise is different from the famous clicking head park.
PS. I've set advanced power management to 190, because otherwise the temperature goes higher than under Windows.

Any help would be appreciated :).

---

