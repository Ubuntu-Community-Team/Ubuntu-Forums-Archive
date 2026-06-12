---
title: "kubuntu 9.10 &amp; SSD &gt; 10sec hangs, hard resetting link"
date: 2010-01-09
forum: Hardware
---

### Post by H.i.M on 2010-01-09
Hey guys i have fresh installed Kubuntu 9.10-64 on my Dell Latitude E6400. My SSD hangs quite often, which is really annoying because it takes about 10sec while you cant do anything.
I would be very happy, if someone could give me a hint or an advice. Thanks in advance.

greetings H.i.M

PS: i have searched the forum, but havent found anything related. If i have missed a topic, please let it know me.

syslog
```
Dec 18 13:34:22 mellhen-mobile kernel: [ 38.040067] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x6 frozen
Dec 18 13:34:22 mellhen-mobile kernel: [ 38.040077] ata1.00: cmd 60/08:00:d8:57:41/00:00:00:00:00/40 tag 0 ncq 4096 in
Dec 18 13:34:22 mellhen-mobile kernel: [ 38.040079] res 40/00:f0:08:f7:9d/00:00:00:00:00/40 Emask 0x4 (timeout)
Dec 18 13:34:22 mellhen-mobile kernel: [ 38.040082] ata1.00: status: { DRDY }
Dec 18 13:34:22 mellhen-mobile kernel: [ 38.040088] ata1: hard resetting link
Dec 18 13:34:23 mellhen-mobile kernel: [ 38.570249] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 18 13:34:23 mellhen-mobile kernel: [ 38.572967] ata1.00: configured for UDMA/133
Dec 18 13:34:23 mellhen-mobile kernel: [ 38.572977] ata1: EH complete

```

Full syslog: [http://paste.ubuntuusers.de/397139/](http://paste.ubuntuusers.de/397139/)

My best workaround is currently to pull the device out manually and plug in it again. This way i save 8 sec waiting :-?

Some data about the ssd:

```
mellhen@mellhen-mobile:~$ sudo hdparm -I /dev/sda 
[sudo] password for mellhen:                      

/dev/sda:

ATA device, with non-removable media
        Model Number:       STT_FTM64GX25H                          
        Serial Number:      P595418-TFBX-B049318                    
        Firmware Revision:  1819                                    
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
        LBA    user addressable sectors:  125045424                 
        LBA48  user addressable sectors:  125045424                 
        Logical  Sector size:                   512 bytes           
        Physical Sector size:                   512 bytes           
        device size with M = 1024*1024:       61057 MBytes          
        device size with M = 1000*1000:       64023 MBytes (64 GB)  
        cache/buffer size  = unknown                                
        Nominal Media Rotation Rate: Solid State Device             
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 1   Current = 1
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
           *    SMART self-test
           *    General Purpose Logging feature set
           *    Gen1 signaling speed (1.5Gb/s)
           *    Gen2 signaling speed (3.0Gb/s)
           *    Native Command Queueing (NCQ)
           *    Host-initiated interface power management
           *    Phy event counters
                DMA Setup Auto-Activate optimization
                Device-initiated interface power management
           *    Software settings preservation
           *    Data Set Management TRIM supported
           *    Deterministic read data after TRIM
Security:
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
Checksum: correct

```

TRIM support with wiper.sh and DiskTRIM

```
Start TRIM operation: 2009-12-18 13:34:33

>/sbin/wiper.sh  --commit --verbose /dev/sda1

wiper.sh: Linux SATA SSD TRIM utility, version 2.5, by Mark Lord.
rootdev=/dev/sda1 rdev=/dev/sda1
fsmode2: fsmode=read-write
/: fstype=ext4
freesize = 53039144 KB, reserved = 530391 KB
Preparing for online TRIM of free space on /dev/sda1 (ext4 mounted read-write at /).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (52508753 KB).. 
Syncing disks.. 
Beginning TRIM operations..
get_trimlist=/sbin/hdparm --fibmap WIPER_TMPFILE.1614

/dev/sda:
trimming 105017512 sectors from 1726 ranges
succeeded
Removing temporary file..
Syncing disks.. 
Done.

TRIM operation stopped: 2009-12-18 13:34:37
```

---

