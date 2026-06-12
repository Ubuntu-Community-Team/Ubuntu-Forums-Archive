---
title: "Noisy Hard drive"
date: 2011-05-15
forum: Hardware
---

### Post by natkill on 2011-05-15
I recently installed Ubuntu 11.04 on a new 60GB hard drive we had around the house since it didn't have an operating system on it. While I've been using it, the past couple of hours I have noticed it making a clicking sound a few times a minute when the drive is idle.  When I ran some self-tests using the Disk Utility, the results came back stating the drive is healthy, and for the duration of the tests, the hard drive was silent.  

Any idea what it could be?

Thanks for your help!

---

### Post by mikewhatever on 2011-05-15
Probably the head parking sound. Check the power management with the following command:
```
sudo hdparm -I /dev/sda | grep 'Advanced power management'
```.

 Some hard drive's power management levels are too aggressive and needs resetting.
You should get the output similar to this:
```
Advanced power management level: 254
```

---

### Post by natkill on 2011-05-18
Thanks for your reply. 

I ran the command as you said, and it said the power management is disabled.

ATA device, with non-removable media
    Model Number:       FUJITSU MHV2060BH PL                    
    Serial Number:      NW9AT662BCVE
    Firmware Revision:  00000029
Standards:
    Used: ATA/ATAPI-7 T13 1532D revision 4a 
    Supported: 7 6 5 4 & some of 8
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  117210240
    LBA48  user addressable sectors:  117210240
    Logical  Sector size:                   512 bytes
    Physical Sector size:                   512 bytes
    device size with M = 1024*1024:       57231 MBytes
    device size with M = 1000*1000:       60011 MBytes (60 GB)
    cache/buffer size  = 8192 KBytes (type=DualPortCache)
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Advanced power management level: disabled
    Recommended acoustic management value: 254, current value: 254
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set

How can I fix that?

---

