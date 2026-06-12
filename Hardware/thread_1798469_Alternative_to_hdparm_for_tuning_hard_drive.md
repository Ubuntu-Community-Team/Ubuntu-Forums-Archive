---
title: "Alternative to hdparm for tuning hard drive?"
date: 2011-07-06
forum: Hardware
---

### Post by acimmarusti on 2011-07-06
Dear all,

I've been experiencing very annoying performance issues. System very unresponsive at times and sometimes very fast. At times, HQ videos won't play with mplayer nor vlc.

I'm running Debian wheezy here, on an old hp pavilion dv5035nr laptop (2 Gb RAM DDR, 2.2 GHz AMD 64-bit processor, 120 Gb WD 100 MB/s HD).
Squeeze and Ubuntu 10.04 LTS run well on this machine except for touchpad issue losing sync often.

I've been trying to find what the performance problem is. I was running gnome and switched to xfce, but that didn't fix it. I've tried several kernels, and I've noticed with older than 2.6.34 everything is fine. I also think my problem is the HD.

I've been using hdparm to monitor it and I see dramatic drops in read speeds overtime:

> 
/dev/sda:
Timing cached reads: 480 MB in 2.00 seconds = 239.92 MB/sec
Timing buffered disk reads: 116 MB in 3.03 seconds = 38.25 MB/sec

/dev/sda:
Timing cached reads: 624 MB in 2.00 seconds = 311.96 MB/sec
Timing buffered disk reads: 144 MB in 3.02 seconds = 47.64 MB/sec

/dev/sda:
Timing cached reads: 558 MB in 2.00 seconds = 278.85 MB/sec
Timing buffered disk reads: 126 MB in 3.04 seconds = 41.41 MB/sec

/dev/sda:
Timing cached reads: 494 MB in 2.00 seconds = 246.61 MB/sec
Timing buffered disk reads: 114 MB in 3.05 seconds = 37.38 MB/sec

/dev/sda:
Timing cached reads: 208 MB in 2.00 seconds = 103.98 MB/sec
Timing buffered disk reads: 104 MB in 3.01 seconds = 34.58 MB/sec

/dev/sda:
Timing cached reads: 840 MB in 2.00 seconds = 419.34 MB/sec
Timing buffered disk reads: 162 MB in 3.03 seconds = 53.52 MB/sec

/dev/sda:
Timing cached reads: 922 MB in 2.00 seconds = 460.40 MB/sec
Timing buffered disk reads: 162 MB in 3.01 seconds = 53.75 MB/sec

/dev/sda:
Timing cached reads: 464 MB in 2.01 seconds = 230.53 MB/sec
Timing buffered disk reads: 132 MB in 3.05 seconds = 43.29 MB/sec

/dev/sda:
Timing cached reads: 792 MB in 2.00 seconds = 395.97 MB/sec
Timing buffered disk reads: 160 MB in 3.01 seconds = 53.24 MB/sec

/dev/sda:
Timing cached reads: 168 MB in 2.01 seconds = 83.51 MB/sec
Timing buffered disk reads: 110 MB in 3.03 seconds = 36.32 MB/sec

/dev/sda:
Timing cached reads: 668 MB in 2.00 seconds = 333.68 MB/sec
Timing buffered disk reads: 128 MB in 3.04 seconds = 42.09 MB/sec

/dev/sda:
Timing cached reads: 518 MB in 2.02 seconds = 256.76 MB/sec
Timing buffered disk reads: 122 MB in 3.05 seconds = 39.96 MB/sec

/dev/sda:
Timing cached reads: 502 MB in 2.02 seconds = 248.94 MB/sec
Timing buffered disk reads: 110 MB in 3.05 seconds = 36.02 MB/sec

/dev/sda:
Timing cached reads: 834 MB in 2.00 seconds = 416.43 MB/sec
Timing buffered disk reads: 150 MB in 3.01 seconds = 49.90 MB/sec

/dev/sda:
Timing cached reads: 842 MB in 2.00 seconds = 420.91 MB/sec
Timing buffered disk reads: 162 MB in 3.02 seconds = 53.60 MB/sec

/dev/sda:
Timing cached reads: 796 MB in 2.00 seconds = 397.52 MB/sec
Timing buffered disk reads: 162 MB in 3.01 seconds = 53.73 MB/sec

/dev/sda:
Timing cached reads: 400 MB in 2.02 seconds = 198.36 MB/sec
Timing buffered disk reads: 114 MB in 3.02 seconds = 37.69 MB/sec

/dev/sda:
Timing cached reads: 156 MB in 2.02 seconds = 77.24 MB/sec
Timing buffered disk reads: 144 MB in 3.00 seconds = 47.95 MB/sec

/dev/sda:
Timing cached reads: 638 MB in 2.00 seconds = 319.04 MB/sec
Timing buffered disk reads: 146 MB in 3.02 seconds = 48.33 MB/sec

/dev/sda:
Timing cached reads: 626 MB in 2.00 seconds = 312.93 MB/sec
Timing buffered disk reads: 134 MB in 3.05 seconds = 43.96 MB/sec

/dev/sda:
Timing cached reads: 194 MB in 2.00 seconds = 96.78 MB/sec
Timing buffered disk reads: 102 MB in 3.00 seconds = 33.97 MB/sec

/dev/sda:
Timing cached reads: 160 MB in 2.02 seconds = 79.13 MB/sec
Timing buffered disk reads: 102 MB in 3.03 seconds = 33.72 MB/sec

/dev/sda:
Timing cached reads: 508 MB in 2.01 seconds = 252.28 MB/sec
Timing buffered disk reads: 142 MB in 3.04 seconds = 46.76 MB/sec

/dev/sda:
Timing cached reads: 660 MB in 2.00 seconds = 329.56 MB/sec
Timing buffered disk reads: 144 MB in 3.00 seconds = 47.93 MB/sec

/dev/sda:
Timing cached reads: 736 MB in 2.01 seconds = 366.22 MB/sec
Timing buffered disk reads: 152 MB in 3.04 seconds = 50.05 MB/sec

/dev/sda:
Timing cached reads: 756 MB in 2.00 seconds = 377.43 MB/sec
Timing buffered disk reads: 122 MB in 3.04 seconds = 40.11 MB/sec


I honestly don't know if this is normal, but I think this might be the root of my performance problem. This is my harddrive

```

# hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
   Model Number:       WDC WD1200BEVE-00A0HT0                  
   Serial Number:      WD-WXJ0EB9DFS86
   Firmware Revision:  11.01A11
   Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5
Standards:
   Supported: 8 7 6 5 
   Likely used: 8
Configuration:
   Logical      max   current
   cylinders   16383   16383
   heads      16   16
   sectors/track   63   63
   --
   CHS current addressable sectors:   16514064
   LBA    user addressable sectors:  234441648
   LBA48  user addressable sectors:  234441648
   Logical/Physical Sector size:           512 bytes
   device size with M = 1024*1024:      114473 MBytes
   device size with M = 1000*1000:      120034 MBytes (120 GB)
   cache/buffer size  = 8192 KBytes
   Nominal Media Rotation Rate: 5400
Capabilities:
   LBA, IORDY(can be disabled)
   Standby timer values: spec'd by Standard, with device specific minimum
   R/W multiple sector transfer: Max = 16   Current = 16
   Advanced power management level: 128
   Recommended acoustic management value: 128, current value: 254
   DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
        Cycle time: min=120ns recommended=120ns
   PIO: pio0 pio1 pio2 pio3 pio4 
        Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
   Enabled   Supported:
      *   SMART feature set
          Security Mode feature set
      *   Power Management feature set
      *   Write cache
      *   Look-ahead
      *   Host Protected Area feature set
      *   WRITE_BUFFER command
      *   READ_BUFFER command
      *   NOP cmd
      *   DOWNLOAD_MICROCODE
      *   Advanced Power Management feature set
          SET_MAX security extension
          Automatic Acoustic Management feature set
      *   48-bit Address feature set
      *   Device Configuration Overlay feature set
      *   Mandatory FLUSH_CACHE
      *   FLUSH_CACHE_EXT
      *   SMART error logging
      *   SMART self-test
      *   General Purpose Logging feature set
      *   64-bit World wide name
      *   IDLE_IMMEDIATE with UNLOAD
      *   Segmented DOWNLOAD_MICROCODE
      *   SMART Command Transport (SCT) feature set
      *   SCT Long Sector Access (AC1)
      *   SCT LBA Segment Access (AC2)
      *   SCT Features Control (AC4)
      *   SCT Data Tables (AC5)
          unknown 206[13] (vendor specific)
Security: 
   Master password revision code = 65534
      supported
   not   enabled
   not   locked
      frozen
   not   expired: security count
      supported: enhanced erase
   46min for SECURITY ERASE UNIT. 46min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee2aea4fed1
   NAA      : 5
   IEEE OUI   : 0014ee
   Unique ID   : 2aea4fed1
HW reset results:
   CBLID- above Vih
   Device num = 0 determined by the jumper
Checksum: correct

```

```

# hdparm -i /dev/sda

/dev/sda:

Model=WDC WD1200BEVE-00A0HT0, FwRev=11.01A11, SerialNo=WD-WXJ0EB9DFS86
Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=16
CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=234441648
IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
PIO modes:  pio0 pio3 pio4 
DMA modes:  mdma0 mdma1 mdma2 
UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
AdvancedPM=yes: unknown setting WriteCache=enabled
Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

* signifies the current active mode

```

```

# hdparm /dev/sda

/dev/sda:
multcount = 16 (on)
IO_support = 0 (default) 
readonly = 0 (off)
readahead = 256 (on)
geometry = 14593/255/63, sectors = 234441648, start = 0

```

Sadly I can't use hdparm to try to tune and or tweak my hard drive to attain a better performance. It doesn't seem to work anymore, after the change to libata.

Does anyone know how to address these issues?

Thanks a lot

---

