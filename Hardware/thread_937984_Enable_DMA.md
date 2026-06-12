---
title: "Enable DMA"
date: 2008-10-04
forum: Hardware
---

### Post by andrewyoungisgreat on 2008-10-04
I've just upgraded from 7.04 to 8.04, but I'm experiencing a lot of system slow downs. I think I've tracked this down to a lack of DMA on hda.

I've tried

```
$ sudo hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma     =  0 (off)
```

I have an IDE and a SATA hard drive as well as an IDE DVD writer connected.

What else can I try?

---

### Post by andrewyoungisgreat on 2008-10-05
I hope the following can help somebody. Unfortunately, I don't understand it.
```
$ sudo hdparm /dev/hda

/dev/hda:
 multcount     = 16 (on)
 IO_support    =  0 (default)
16-bit)
 unmaskirq     =  0 (off)
 using_dma     =  0 (off)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 65535/16/63, sectors = 156301488, start = 0
```

```
$ sudo hdparm  -I /dev/hda

/dev/hda:

ATA device, with non-removable media
        Model Number:       WDC WD800JB-00JJC0
        Serial Number:      WD-WCAM9R509930
        Firmware Revision:  05.01C05
Standards:
        Supported: 6 5 4
        Likely used: 8
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  156301488
        device size with M = 1024*1024:       76319 MBytes
        device size with M = 1000*1000:       80026 MBytes (80 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard, with device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Recommended acoustic management value: 128, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
                Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
                SET_MAX security extension
                Automatic Acoustic Management feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    SMART error logging
           *    SMART self-test
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
        not     supported: enhanced erase
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper
Checksum: correct
```

```
$ sudo hdparm /dev/hdc

/dev/hdc:
 IO_support    =  0 (default)
16-bit)
 unmaskirq     =  0 (off)
 using_dma     =  0 (off)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
```

```
$ sudo hdparm  -I /dev/hdc

/dev/hdc:

ATAPI CD-ROM, with removable media
        Model Number:       Optiarc DVD RW AD-5170A
        Serial Number:
        Firmware Revision:  1.11
Standards:
        Likely used CD-ROM ATAPI-1
Configuration:
        DRQ response: 50us.
        Packet size: 12 bytes
Capabilities:
        LBA, IORDY(cannot be disabled)
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 *udma4
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
HW reset results:
        CBLID- above Vih
        Device num = 1
```

```
$ sudo hdparm /dev/sda

/dev/sda:
 IO_support    =  0 (default)
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 60801/255/63, sectors = 976773168, start = 0
```

```
$ sudo hdparm  -I /dev/sda

/dev/sda:

ATA device, with non-removable media
        Model Number:       SAMSUNG HD501LJ
        Serial Number:      S0MUJ2MP802625
        Firmware Revision:  CR100-10
        Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SAT
A Rev 2.5
Standards:
        Used: ATA-8-ACS revision 3b
        Supported: 8 7 6 5
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors:  976773168
        device size with M = 1024*1024:      476940 MBytes
        device size with M = 1000*1000:      500107 MBytes (500 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Recommended acoustic management value: 254, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 udma7
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
                SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    NOP cmd
           *    DOWNLOAD_MICROCODE
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
           *    SATA-I signaling speed (1.5Gb/s)
           *    SATA-II signaling speed (3.0Gb/s)
           *    Native Command Queueing (NCQ)
           *    Host-initiated interface power management
           *    Phy event counters
                DMA Setup Auto-Activate optimization
                Device-initiated interface power management
           *    Software settings preservation
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
        168min for SECURITY ERASE UNIT. 168min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 5000f002b802625
        NAA             : 5
        IEEE OUI        : f0
        Unique ID       : 02b802625
Checksum: correct
```

```
$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
```

/etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
```

---

### Post by mdramige on 2008-10-05
Post the output of ```
dmesg | grep hda
```
Is your OS on hda or sda?

---

### Post by andrewyoungisgreat on 2008-10-06
My OS is on hda.

$ dmesg | grep hda```
[  152.013680] hda: WDC WD800JB-00JJC0, ATA DISK drive
[  152.024441] hda: max request size: 128KiB
[  152.028545] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63
[  152.028630] hda: cache flushes supported
[  152.028674]  hda: hda1 < hda5 hda6 > hda2 hda3
[  188.081652] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[  189.304492] Adding 9759476k swap on /dev/hda5.  Priority:-1 extents:1 across:9759476k
[  190.084268] EXT3 FS on hda3, internal journal
[  662.998074] EXT3 FS on hda6, internal journal
[  663.040330] EXT3 FS on hda2, internal journal
[  849.655812] hda-intel: Invalid position buffer, using LPIB read method instead.
```

---

