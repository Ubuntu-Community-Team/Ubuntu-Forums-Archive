---
title: "Only half the speed of the disk in ubuntu?!"
date: 2008-03-17
forum: Hardware &amp; Laptops
---

### Post by 3molo on 2008-03-17
Hi,

I've got a SanDisk SSD UATA 5000 1.8 drive.
I installed debian previous to my ubuntu installation, and I noticed that the timed buffer and cache reads (using hdparm) was MUCH faster in debian. This goes for gentoo too.
I would really like some help configuring my drive so I get the same performance as in debian/gentoo.

###### Gentoo

/dev/hda:
 Timing cached reads:   3076 MB in  2.00 seconds = 1537.25 MB/sec
  Timing buffered disk reads:  166 MB in  3.01 seconds =  55.22 MB/sec


/dev/hda:

 Model=SanDisk SSD UATA 5000 1.8, FwRev=1.27, SerialNo=7AQ1641
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=0kB, MaxMultSect=1, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=61734912
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 
 AdvancedPM=yes: unknown setting WriteCache=disabled
 Drive conforms to: unknown:  ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode


/dev/hda:

ATA device, with non-removable media
        Model Number:       SanDisk SSD UATA 5000 1.8               
        Serial Number:      7AQ1641
        Firmware Revision:  1.27    
Standards:
        Used: Reserved 
        Supported: 7 6 5 4 
Configuration:
        Logical         max     current
        cylinders       16383   65535
        heads           16      1
        sectors/track   63      63
        --
        CHS current addressable sectors:    4128705
        LBA    user addressable sectors:   61734912
        LBA48  user addressable sectors:   61734912
        device size with M = 1024*1024:       30144 MBytes
        device size with M = 1000*1000:       31608 MBytes (31 GB)
Capabilities:
        LBA, IORDY(cannot be disabled)
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 1   Current = 1
        Advanced power management level: unknown setting (0x0000)
        Recommended acoustic management value: 254, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
                Power Management feature set
           *    Write cache
                Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    NOP cmd
           *    DOWNLOAD_MICROCODE
           *    Advanced Power Management feature set
                Automatic Acoustic Management feature set
           *    48-bit Address feature set
           *    Mandatory FLUSH_CACHE
                SMART error logging
           *    SMART self-test
Security: 
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
                frozen
        not     expired: security count
                supported: enhanced erase
        10min for SECURITY ERASE UNIT. 
HW reset results:
        CBLID- below Vih
        Device num = 0
Checksum: correct


###### Ubuntu
/dev/sda:
 Timing cached reads:   1442 MB in  2.00 seconds = 721.29 MB/sec
 Timing buffered disk reads:   82 MB in  3.05 seconds =  26.92 MB/sec


/dev/sda:

 Model=SanDisk SSD UATA 5000 1.8               , FwRev=1.27    , SerialNo=             7AQ1641
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=0kB, MaxMultSect=1, MultSect=?1?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=61734912
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5 
 AdvancedPM=yes: unknown setting WriteCache=disabled
 Drive conforms to: unknown:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode


/dev/sda:

ATA device, with non-removable media
        Model Number:       SanDisk SSD UATA 5000 1.8               
        Serial Number:      7AQ1641
        Firmware Revision:  1.27    
Standards:
        Used: ATA/ATAPI-7 T13 1532D revision 4a 
        Supported: 7 6 5 4 
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:   61734912
        LBA48  user addressable sectors:   61734912
        device size with M = 1024*1024:       30144 MBytes
        device size with M = 1000*1000:       31608 MBytes (31 GB)
Capabilities:
        LBA, IORDY(cannot be disabled)
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 1   Current = 1
        Advanced power management level: unknown setting (0x0000)
        Recommended acoustic management value: 254, current value: 254
        DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
                Power Management feature set
                Write cache
                Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    NOP cmd
           *    DOWNLOAD_MICROCODE
           *    Advanced Power Management feature set
                Automatic Acoustic Management feature set
           *    48-bit Address feature set
           *    Mandatory FLUSH_CACHE
                SMART error logging
           *    SMART self-test
Security: 
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
                frozen
        not     expired: security count
                supported: enhanced erase
        10min for SECURITY ERASE UNIT. 
HW reset results:
        CBLID- below Vih
        Device num = 0
Checksum: correct


,
 Timing cached reads:   3076 MB in  2.00 seconds = 1537.25 MB/sec
  Timing buffered disk reads:  166 MB in  3.01 seconds =  55.22 MB/sec

 Timing cached reads:   1442 MB in  2.00 seconds = 721.29 MB/sec
 Timing buffered disk reads:   82 MB in  3.05 seconds =  26.92 MB/sec

Speaks for itself?
Also notice that gentoo (and debian) calls the disk "hda" while ubuntu calls it sda (as in scsi) - could this be one of the reasons?

Please help!

---

### Post by Anders Kvist on 2008-04-03
I have the same problem. Just booted a Debian Live CD, and it gave me the double read speeds than Ubuntu.

hdparm -i /dev/hda (debian) - showed udma5 mode active while udma2 mode were active in Ubuntu. Maybe this is the problem?

/Anders

---

### Post by hokah on 2008-04-07
I have been looking for solution for over 3 days, seems that there is no solution. 
hdparm doesnt work, Im little sick of this, I wasted another hours with something what doesnt work. 
Maybe instead of nice looking windows someone should focus on make it work, I belive that HD is nothing new under linux.

---

