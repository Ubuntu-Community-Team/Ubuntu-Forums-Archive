---
title: "Slow hdd cache speed"
date: 2008-05-15
forum: Hardware
---

### Post by MatusZ on 2008-05-15
Hi,
i am running Ubuntu 7.10, but my hdd performance is quite bad.
When i type sudo hdparm  -tT /dev/hda i get:

/dev/hda:
 Timing cached reads:   354 MB in  2.00 seconds = 176.63 MB/sec
 Timing buffered disk reads:   54 MB in  3.09 seconds =  17.45 MB/sec

The problem is with cached reads - 176 MB is slow - especially when others have values around 1000MB.

sudo hdparm  -i /dev/hda
/dev/hda:

 Model=ST310211A, FwRev=3.39, SerialNo=7DB1VAXW
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=1024kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=19541088
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5

sudo hdparm  /dev/hda

/dev/hda:
 multcount     = 16 (on)
 IO_support    =  3 (32-bit w/sync)
 unmaskirq     =  1 (on)
 using_dma     =  1 (on)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 19386/16/63, sectors = 19541088, start = 0


lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

DMA cannot be boosted to UATA100, because right now i am using an UATA33 cable.
I was trying to solve the problem like in this thread
[http://ubuntuforums.org/showthread.php?t=19519](http://ubuntuforums.org/showthread.php?t=19519)
but no luck. 
Can anyone help??

---

