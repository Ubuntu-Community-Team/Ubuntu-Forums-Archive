---
title: "Dell Inspiron 6000d - Multiple minor issues"
date: 2005-10-25
forum: Hardware &amp; Laptops
---

### Post by ScatterBrain on 2005-10-25
I've had my Inspiron for two days and in those two days, I've ran into several little issues.  I'm hoping that someone here can help me.

[LIST=1]
[*]8x DVD Burner - can't enable DMA.  Makes DVD playback choppy.  I think has a lot to do with the fact that this macine has a SATA hard drive and both it and the DVD are run from the same controller.  I've read that it takes a kernel patch to get this right.  Can anyone confirm that?  Anyone done it?
[*]ipw2200 WiFi - Can't seem to connect to any Access Point with great success.  I do get connected, but I have to manually make the connection.  Neither WiFi-Radar nor NetworkMonitor will establish the connection automatically.  Is this the driver?
[*]SATA Hard Drive - It seems as thought I'm not getting all I can out this drive.  There is a noticable lag, for example, when I'm sitting at the console and type part of command and then hit tab to complete it.  During this lag, I can see the HD light come on solid and go out at the exact moment that I get the console control back.  See below for 'hdparm -Tt' timings.
[*]SpeedStep - It appears as though it's not throttling correctly.  I fired up vmWare on it this afternoon and the CPU was idling around 800MHz.  vmWare was *very* slow.  Only when the CPU is maxed out (2Ghz) do I get acceptable perfomance from vmWare, but it rarely hits that mark.  Can I force this?
[/LIST]

```
[COLOR="Blue"]enterprise ~ # hdparm -Tt /dev/sda[/COLOR]
/dev/sda:
 Timing cached reads:   3172 MB in  2.00 seconds = 1584.66 MB/sec
 Timing buffered disk reads:   92 MB in  3.02 seconds =  30.51 MB/sec

[COLOR="Blue"]enterprise ~ # hdparm -Iv /dev/sda[/COLOR]
/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 9729/255/63, sectors = 156301488, start = 0

ATA device, with non-removable media
        Model Number:       WDC WD800VE-75HDT1
        Serial Number:      WD-WXE805152772
        Firmware Revision:  11.07D11
Standards:
        Supported: 6 5 4 3
        Likely used: 6
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
        bytes avail on r/w long: 50     Queue depth: 1
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 8
        Advanced power management level: unknown setting (0x0080)
        Recommended acoustic management value: 128, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
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
           *    Mandatory FLUSH CACHE command
           *    Device Configuration Overlay feature set
                Automatic Acoustic Management feature set
                SET MAX security extension
           *    Advanced Power Management feature set
           *    DOWNLOAD MICROCODE cmd
           *    SMART self-test
           *    SMART error logging
Security:
                supported
        not     enabled
        not     locked
                frozen
        not     expired: security count
        not     supported: enhanced erase
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper
Checksum: correct

```

---

### Post by ScatterBrain on 2005-10-25
Seems like a little searching has helped me solve one of my issues:

[QUOTE=ScatterBrain]
SpeedStep - It appears as though it's not throttling correctly.  I fired up vmWare on it this afternoon and the CPU was idling around 800MHz.  vmWare was *very* slow.  Only when the CPU is maxed out (2Ghz) do I get acceptable perfomance from vmWare, but it rarely hits that mark.  Can I force this?
[/QUOTE]

I found this post which let's me set the CPU speed:

[http://ubuntuforums.org/showthread.php?t=75810]("http://ubuntuforums.org/showthread.php?t=75810") 

Look down to reply No. 7 for the answer.

---

### Post by ScatterBrain on 2005-10-26
*BUMP*

Does no one have any idea about these problems?

---

