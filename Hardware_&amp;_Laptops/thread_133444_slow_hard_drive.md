---
title: "slow hard drive"
date: 2006-02-20
forum: Hardware &amp; Laptops
---

### Post by muszek on 2006-02-20
Hi.

I have two hard drives.  Ubuntu is installed on 120GB SATA (/dev/sda) and there's also 250GB IDE (/dev/hda).  

While /dev/hda seems to be fine:
```

/dev/hda:
 Timing cached reads:   1620 MB in  2.00 seconds = 808.91 MB/sec
 Timing buffered disk reads:  194 MB in  3.03 seconds =  63.99 MB/sec

```

/dev/sda is awfully slow:

```

/dev/sda:
 Timing cached reads:   1588 MB in  2.00 seconds = 792.14 MB/sec
 Timing buffered disk reads:   46 MB in  3.10 seconds =  14.86 MB/sec

```
While moving files from sda to hda, I get around 7MB/s transfer.

dmesg | grep sda
```

muszek@muszek:~$ dmesg | grep sda
[4294677.823000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[4294677.823000] SCSI device sda: drive cache: write back
[4294677.823000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[4294677.823000] SCSI device sda: drive cache: write back
[4294677.858000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4294682.646000] Adding 1020088k swap on /dev/sda6.  Priority:-1 extents:1
[4294682.939000] EXT3 FS on sda1, internal journal
[4294736.824000] ReiserFS: sda7: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda7
[4294736.885000] ReiserFS: sda5: found reiserfs format "3.6" with standard journal
[4294739.883000] ReiserFS: sda5: using ordered data mode
[4294739.898000] ReiserFS: sda5: journal params: device sda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294739.899000] ReiserFS: sda5: checking transaction log (sda5)
[4294739.938000] ReiserFS: sda5: Using r5 hash to sort names

```

sudo hdparm -I /dev/sda
```

ATA device, with non-removable media
        Model Number:       ST3120026AS
        Serial Number:      3JT17H7H
        Firmware Revision:  3.05
Standards:
        Used: ATA/ATAPI-6 T13 1410D revision 2
        Supported: 6 5 4 3
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  234441648
        LBA48  user addressable sectors:  234441648
        device size with M = 1024*1024:      114473 MBytes
        device size with M = 1000*1000:      120034 MBytes (120 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        bytes avail on r/w long: 4      Queue depth: 1
        Standby timer values: spec'd by Standard
        R/W multiple sector transfer: Max = 16  Current = 16
        Recommended acoustic management value: 254, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 udma6
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    READ BUFFER cmd
           *    WRITE BUFFER cmd
           *    Host Protected Area feature set
           *    Look-ahead
           *    Write cache
           *    Power Management feature set
                Security Mode feature set
           *    SMART feature set
           *    FLUSH CACHE EXT command
           *    Mandatory FLUSH CACHE command
           *    Device Configuration Overlay feature set
           *    48-bit Address feature set
                SET MAX security extension
           *    DOWNLOAD MICROCODE cmd
           *    SMART self-test
           *    SMART error logging
Security:
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
Checksum: correct

```

when I try to run sudo hdparm -i /dev/sda, I get this:
```

muszek@muszek:~$ sudo hdparm -i /dev/sda

/dev/sda:
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device

```

while output for /dev/hda is:
```

 Model=ST3250824A, FwRev=3.AAD, SerialNo=4ND1N6KS
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: device does not report version:

 * signifies the current active mode

```


Do you see anything wrong?  What can I do to improve sda'a performance?

---

### Post by yorick on 2006-03-31
I've had a similar thread some month ago:
[http://www.ubuntuforums.org/showthread.php?t=81056&highlight=sata+working+slow](http://www.ubuntuforums.org/showthread.php?t=81056&highlight=sata+working+slow)

It seems in my case it is an unfortunate combination of hard-drive/controller, and I have to wait until a fix is found... 

Hope you have more luck...

---

