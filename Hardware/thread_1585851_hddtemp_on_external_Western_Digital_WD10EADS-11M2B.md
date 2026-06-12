---
title: "hddtemp on external Western Digital WD10EADS-11M2B1 harddisk"
date: 2010-10-01
forum: Hardware
---

### Post by Zendoin on 2010-10-01
Hoi!

I'm trying to read out the temperature of my external WD10EADS-11M2B1 hard drive, which should be done via S.M.A.R.T.

This is what I get when trying:

```
~$ hddtemp /dev/sdb
/dev/sdb: WD 10EADS External: [COLOR=Red]S.M.A.R.T. not available[/COLOR]
```But if I check the drive with hdparm I get:

```
~$ sudo hdparm -I /dev/sdb
/dev/sdb:

ATA device, with non-removable media
    Model Number:       WDC WD10EADS-11M2B1                     
    Serial Number:      WD-WCAV53508824
    Firmware Revision:  01.00A01
    Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
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
    Logical  Sector size:                   512 bytes
    Physical Sector size:                  4096 bytes
    Logical Sector-0 offset:                  0 bytes
    device size with M = 1024*1024:      953869 MBytes
    device size with M = 1000*1000:     1000204 MBytes (1000 GB)
    cache/buffer size  = unknown
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, with device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 0
    Recommended acoustic management value: 128, current value: 254
    DMA: mdma0 mdma1 *mdma2 udma0 udma1 udma2 udma3 udma4 udma5 udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       [COLOR=Red]*    SMART feature set[/COLOR]
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
       [COLOR=Red]*    SMART error logging
       *    SMART self-test[/COLOR]
       *    General Purpose Logging feature set
       *    64-bit World wide name
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
       *    NCQ priority information
            DMA Setup Auto-Activate optimization
       *    Software settings preservation
       [COLOR=Red]*    SMART Command Transport (SCT) feature set[/COLOR]
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
    212min for SECURITY ERASE UNIT. 212min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee258e23cf0
    NAA        : 5
    IEEE OUI    : 0014ee
    Unique ID    : 258e23cf0
Checksum: correct
```As far as I understand, this means that SMART should work on this specific disk - but it doesn't. I tried to add a line with the drive name in /etc/hddtemp.db which didn't make any difference in both commands.

I would be thankfull for any suggestions... :)

---

### Post by Zendoin on 2010-10-03
Maybe someone has the same drive (it's quite a common one I think...) running under Ubuntu 10.4 and can report me if there is the same behaviour?

---

### Post by efflandt on 2010-10-03
The key word is "external".  How is it connected?

The drive may be S.M.A.R.T. capable, but even WD diagnostic software cannot check S.M.A.R.T. on a WD USB drive (I have several WD Passports and have also tested/imaged/repaired WD laptop drives in USB enclosure).

Not sure if S.M.A.R.T. would work for eSATA.

---

### Post by Zendoin on 2010-10-06
The drive is connected via USB, so this should answer my question... Thanks :)

Now I noticed that on boot I get some message like "...drive S.M.A.R.T. capable but not enabled..." (gone too quickly to read it completely...). So this doesn't look to me as if it would be principally impossible but just not set correctly (however to set this). Maybe it just means (as you say) "the drive would be S.M.A.R.T. capable but not if connected via USB".

Anyway, it's not THAT important to measure the external drive temperature, would have been just interesting.

---

### Post by cascade9 on 2010-10-06
> **efflandt said:**
> Not sure if S.M.A.R.T. would work for eSATA.

It should do, but there could be issues on some of the junk eSATA controllers a lot of manufacturers use for the eSATA ports.

---

