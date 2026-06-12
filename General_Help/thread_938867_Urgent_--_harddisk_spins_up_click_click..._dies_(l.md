---
title: "Urgent -- harddisk spins up *click* *click*... dies (laptop-mode-tools?)"
date: 2008-10-05
forum: General Help
---

### Post by mrowth on 2008-10-05
Okay, I have /dev/sdb, PATA drive, Linux on it.

Wanted to use laptop_mode not to control harddisks but for DPMS - two hulking CRTs, one without an off switch, really want standby.

That worked. Then sdb started "falling asleep" somehow and it won't wake back up properly. I hear it spin up "a little", then a click, another,... then that's it, Linux emits an unending stream of messages on tty1 re: I/O and offline devices and whatnot.

I've long since purged laptop-mode-tools, and also tried to use laptop_mode to re-set the drives into a previous state (however I'm not sure what state that was so I basically just reset laptop_mode's conf to the default (no laptop mode on AC), ran laptop_mode with that, then purged it. 

That's why I'm typing fast. So little time. (Haven't got my passwords written down physically so fiddling with live CDs in also-broken optical drives is no fun.)

hparm -I /dev/sdb

ATA device, with non-removable media
        Model Number:       SAMSUNG HD400LD
        Serial Number:      S0AXJ1CPB00654
        Firmware Revision:  WQ100-15
Standards:
        Used: ATA/ATAPI-7 T13 1532D revision 4a
        Supported: 7 6 5 4 & some of 8
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors:  781422768
        device size with M = 1024*1024:      381554 MBytes
        device size with M = 1000*1000:      400088 MBytes (400 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Recommended acoustic management value: 254, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=240ns  IORDY flow control=120ns
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
                SET_FEATURES required to spinup after power up
                SET_MAX security extension
           *    Automatic Acoustic Management feature set
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
                Media Card Pass-Through
           *    General Purpose Logging feature set
           *    SMART Command Transport (SCT) feature set
           *    SCT Long Sector Access (AC1)
           *    SCT LBA Segment Access (AC2)
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
                supported: enhanced erase
        228min for SECURITY ERASE UNIT. 228min for ENHANCED SECURITY ERASE UNIT.
HW reset results:
        CBLID- above Vih
        Device num = 1 determined by the jumper
Checksum: correct

hdparm /dev/sdb

/dev/sdb:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 48641/255/63, sectors = 781422768, start = 0

sda seems unaffected *crosses fingers* but gives the same "inappropriate ioctl" output.

Will post more info if I can think of any.

---

### Post by earthpigg on 2008-10-05
[link in case it does die :)]("http://geeksaresexy.blogspot.com/2006/01/freeze-your-hard-drive-to-recover-data.html")

---

### Post by mrowth on 2008-10-05
I'm already doing backups, though I'm running out of space... (now if only DVD burners worked...)

...

From hdparm manpage: 

   -S     Set the standby (spindown) timeout for the drive.  This value is used by the drive to determine how long to wait (with no disk activity) before turning off the spindle motor to save power.  Under such  circum             stances,  the  drive  may take as long as 30 seconds to respond to a subsequent disk access, though most drives are much quicker.  The encoding of the timeout value is somewhat peculiar.  A value of zero means "timeouts  are  disabled":  the  device will not automatically enter standby mode.  Values from 1 to 240 specify multiples of 5 seconds, yielding timeouts from 5 seconds to 20 minutes.  Values from 241 to  251 specify  from  1  to 11 units of 30 minutes, yielding timeouts from 30 minutes to 5.5 hours.  A value of 252 signifies a timeout of 21 minutes. A value of 253 sets a vendor-defined timeout period between 8 and 12  hours,  and the value 254 is reserved.  255 is interpreted as 21 minutes plus 15 seconds.  Note that some older drives may have very different interpretations of these values.

From laptop-mode.conf:

NOLM_HD_IDLE_TIMEOUT_SECONDS=7200

If it's been running with a timeout of 7200 (= 2h) all this time, why wasn't that a problem before?

And why should standby be a problem in the first place? It used to work; I just disabled it because this isn't actually a laptop and its HDs may not be as "resilient" when it comes to frequent spinning-down-and-up-again.

Should I try to get the drive out of its somnambulism with hdparm -S with ...what values? But then wouldn't that just postpone the inevitable crash unless I do hdparm -S 0 to disable standby timeouts altogether? And would that be a workaround -- don't touch it if it hurts?

---

### Post by mrowth on 2008-10-05
After trying Windows (sda) and it crashing along with the other drive (sdb), I can't get at the data on my (several) NTFS partitions (both sda/sdb) anymore, can't mount them (there're some on both sda and sdb). 

This should be fixable by booting Windows (sda) and letting it repair the NTFS partitions (sda and sdb), but when the XP splash screen appears, I hear a gentle *scrape* *scrape* *scrape*, there's a BSOD for a split second, and the machine resets. 

I can still read from and write to the lone FAT32 partition on sda, so the drive itself isn't destroyed (or not entirely). Also, GRUB is on it and it'll still boot Ubuntu (sdb). I get some instructions (?) during boot (of Ubuntu) but they scroll past too fast to read. Something about ntfs-3g.

Suppose if I replace the Windows drive and reinstall Windows, I have to find a way to restore GRUB.

/dev/sda:

ATA device, with non-removable media
powers-up in standby; SET FEATURES subcmd spins-up.
        Model Number:       ExcelStor Technology J880
        Serial Number:      PFD200K207N01A
        Firmware Revision:  PF2OA21B
Standards:
        Used: ATA/ATAPI-7 T13 1532D revision 1
        Supported: 7 6 5 4
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  160836480
        LBA48  user addressable sectors:  160836480
        device size with M = 1024*1024:       78533 MBytes
        device size with M = 1000*1000:       82348 MBytes (82 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Advanced power management level: disabled
        **Recommended acoustic management value: 128, current value: 254** <- could this be it? No, eh?
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=240ns  IORDY flow control=120ns
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
                Advanced Power Management feature set
                Power-Up In Standby feature set
                SET_FEATURES required to spinup after power up
                Address Offset Reserved Area Boot
                SET_MAX security extension
           *    Automatic Acoustic Management feature set
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
                Media Card Pass-Through
           *    General Purpose Logging feature set
           *    64-bit World wide name
           *    URG for READ_STREAM[_DMA]_EXT
           *    URG for WRITE_STREAM[_DMA]_EXT
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
                frozen
        not     expired: security count
        not     supported: enhanced erase
        44min for SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 0000
        NAA             : 0
        IEEE OUI        : 0
        Unique ID       : 00
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper
Checksum: correct

---

### Post by mrowth on 2008-10-06
> **mrowth said:**
> ... That worked. Then sdb started "falling asleep" somehow and it won't wake back up properly. I hear it spin up "a little", then a click, another,... then that's it, Linux emits an unending stream of messages on tty1 re: I/O and offline devices and whatnot. ...

Anybody? 

Please?

I tried

```
sudo hdparm -B255 /dev/sdb 

/dev/sdb:
 setting Advanced Power Management level to disabled
 HDIO_DRIVE_CMD failed: Input/output error
```

and

```
sudo hdparm -S0 /dev/sdb

/dev/sdb:
 setting standby to 0 (off)
```

But...

(Also I don't see why I shouldn't have some degree of power management... not that it seems to matter)

---

