---
title: "hard drives won't &quot;remember&quot; DMA settings"
date: 2006-05-26
forum: Hardware &amp; Laptops
---

### Post by bobdazzla on 2006-05-26
minor slipup... please note that the thread title should be "hard drives won't REMEMBER dma settings...

hi there, Fresh Kubuntu installation, I have 8 total hard drives in the system, and most of them had 32-bit IO access and DMA support disabled by default. I went through all the drives, using 

hdparm -c1 -d1 -k1 /dev/hdX 

to have hdparm enable 32-bit i/o, dma, and to "keep" the settings. this "fixed" most of my drives except TWO, /hda/ and /hdm/. 

After setting them using the above line, hdparm reports that DMA is enabled but as soon as I run a test (hdparm -tT /dev/hdX) the disks report extremely low read speeds (like 3MB/s) and hdparm then reports that DMA mode is disabled. 

/hda/ is a old 40GB IBM deskstar (not the click-of-death variety but still old). /hdm/ is a brand new Seagate 300GB drive (possibly a barracuda, i don't recall exactly). /hda/ is the boot/swap drive, hooked into IDE0 of my mainboard and is a master. /hdm/ currently has no partition, and is running through a promise Ultra33 ide controller (admittedly this is quite a slow controller, but still should allow dma!). 

The point I'm trying to make is that both drives are very different, are hooked into the mainboard via differing ways (native ide vs. controller expansion card), but have the same problem. 

Below is the hdparm -i -I info for each drive:
```


/dev/hda:

 Model=IBM-DTLA-307045, FwRev=TX6OA60A, SerialNo=YMEYMT5V110
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=40
 BuffType=DualPortCache, BuffSize=1916kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=90069840
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-5 T13 1321D revision 1:

 * signifies the current active mode


ATA device, with non-removable media
powers-up in standby; SET FEATURES subcmd spins-up.
        Model Number:       IBM-DTLA-307045
        Serial Number:      YMEYMT5V110
        Firmware Revision:  TX6OA60A
Standards:
        Used: ATA/ATAPI-5 T13 1321D revision 1
        Supported: 5 4 3 2 & some of 6
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:   90069840
        device size with M = 1024*1024:       43979 MBytes
        device size with M = 1000*1000:       46115 MBytes (46 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        bytes avail on r/w long: 40     Queue depth: 32
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 0
        Advanced power management level: unknown setting (0x0000)
        Recommended acoustic management value: 128, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    NOP cmd
           *    READ BUFFER cmd
           *    WRITE BUFFER cmd
           *    Host Protected Area feature set
                Release interrupt
           *    Look-ahead
           *    Write cache
           *    Power Management feature set
                Security Mode feature set
           *    SMART feature set
                Automatic Acoustic Management feature set
                SET MAX security extension
                Address Offset Reserved Area Boot
                SET FEATURES subcommand required to spinup after power up
                Power-Up In Standby feature set
                Advanced Power Management feature set
           *    READ/WRITE DMA QUEUED
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
        38min for SECURITY ERASE UNIT.
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper
Checksum: correct
bobdazzla@mmklinux:~$ sudo hdparm -i -I /dev/hdm

/dev/hdm:

 Model=ST3300631A, FwRev=3.04, SerialNo=5NF1GZCL
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: device does not report version:

 * signifies the current active mode


ATA device, with non-removable media
        Model Number:       ST3300631A
        Serial Number:      5NF1GZCL
        Firmware Revision:  3.04
Standards:
        Supported: 7 6 5 4
        Likely used: 7
Configuration:
        Logical         max     current
        cylinders       16383   65535
        heads           16      1
        sectors/track   63      63
        --
        CHS current addressable sectors:    4128705
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors:  586072368
        device size with M = 1024*1024:      286168 MBytes
        device size with M = 1000*1000:      300069 MBytes (300 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 1
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = ?
        Recommended acoustic management value: 128, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5
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
           *    General Purpose Logging feature set
           *    SMART self-test
           *    SMART error logging
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper
Checksum: correct

```

I don't mind /hda/ being slow, but i need /hdm/ up to DMA speeds since it will be part of a RAID5 array. 

If anyone has any suggestions on making those two drives run dma permanently, i'd apprecaite it. thanks in advance.

---

### Post by Fass on 2006-05-26
nm

---

### Post by bobdazzla on 2006-05-27
update:

I replaced the Promise Ultra33 controller with a Promise Ultra TX2 controller and swapped in a different ide cable (both were ATA/100 compatible so this might not have affected anything), and now the drive at dev/hdm works fine. The problem must have been with compatibility with the old ide controller (from the looks of it, it was manufactured in 1997... but I'm pretty sure dma access existed then and i think the card supports it).

 I'm still having difficulty with /dev/hda however. the hard drive  running slave on the same bus has no problem doing DMA. The only outstanding aspect of the hard drive at /dev/hda is the fact it is around 5 years old and has seen a lot of use; but i wouldn't think this could effect whether or not dma works.

Since this system is primarily intended as a server and very little disc access will be going over hda during normal use (this will be a file server which will exclusively use the other disks), this is an acceptable arrangement for me. however, if anyone else has any suggestions, I'd greatly appreciate a response. 

Furthermore, in the event hdparm has a dedicated forum for these issues elsewhere on the net, it'd be great if someone could point me in that direction.

---

### Post by sdbillin on 2006-06-07
Just thought I'd chime in and add say that I get the same thing.

I've got this in hdparm.conf - 

```
command_line {
hdparm -c1 -d1 -X70 -m16 -u1 -A1 -k1 /dev/hda
}
command_line {
hdparm -c1 -d1 -X69 -m16 -u1 -A1 -k1 /dev/hdb
}
```

On boot both hda and hdb have DMA etc enabled.
HDA supports UDMA mode 6 - I think -X70 is correct
HDB only suppors UDMA mode 5 - X69.
After some time (possble when the drives spin down) they lose DMA. I can re-enable it by using the same hdparm commands as listed in hdparm.conf.

Any ideas?

---

### Post by stanz on 2006-06-25
Maybe....A hdparm script in "/etc/init.d", for "rcS.d" :
S07hdparm, 
This brought me more joy, then the "hdparm.conf" file!
I'ld found advice, somewhere~ about using "single line" commands, as are below:
==================
[COLOR=Blue]#! /bin/sh

## [reminder to self]This is my file.[/COLOR]

command_line {
    hdparm -X69 /dev/hda
}

command_line {
    hdparm -d1 /dev/hda
}

command_line {
    hdparm -u1 /dev/hda
}

command_line {
    hdparm -m16 /dev/hda
}

command_line {
    hdparm -c3 /dev/hda
}

/dev/hdc {
    dma = on
}

/dev/hdd {
    dma = on
}
===============
No need for exit here.

---

