---
title: "HD DMA &amp; BadCRC errors. Opinions?"
date: 2007-03-14
forum: Hardware &amp; Laptops
---

### Post by praxis22 on 2007-03-14
Hi,

I've been having troubles booting for a couple of weeks, but it never really bothered me, by which I mean I can no longer boot normally with grub, I have to use the recovery mode and then exit back out to multi-user, then it works. If I try to boot direct to multi-user, it hangs, my monitor goes into power save and my Caps Lock & Scroll Lock keyboard lights flash. They will do this for hours, it's a permanent state.

I have been having issues for a while with random resets in XP when streaming large amounts of data for an hour or more, but since I could replicate this on a different XP system I figured it was just the drive overheating. I found that if I put an ice pack on the drive it will stream for longer.

But tonight I decided to try to get to the bottom of the problem.

This is my setup:

AMD64 3800+ on an ASRock 939A8X-M, 1Gb RAM
hda: ST3320620A, ATA DISK drive (my 320Gb Seagate, primary master with a 50Gb Linux partition up front)
hdb: LITE-ON DVDRW SHW-16H5S, ATAPI CD/DVD-ROM drive (DVDRW primary slave)
hdc: WDC WD800JB-00CRA1, ATA DISK drive (XP disk Secondary master)
hdd: ST380020A, ATA DISK drive (secondary slave)

Ubuntu feisty (development branch) AMD64

This is the relevant section from dmesg:
```

[   20.143299] Probing IDE interface ide0...
[   20.164403] usbcore: registered new interface driver usbfs
[   20.164478] usbcore: registered new interface driver hub
[   20.164544] usbcore: registered new device driver usb
[   20.165206] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Dr
iver
[   20.285472] Floppy drive(s): fd0 is 1.44M
[   20.316483] FDC 0 is a post-1991 82077
[   20.467394] hda: ST3320620A, ATA DISK drive
[   20.918668] hdb: LITE-ON DVDRW SHW-16H5S, ATAPI CD/DVD-ROM drive
[   20.978842] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   20.979192] Probing IDE interface ide1...
[   21.270105] hdc: WDC WD800JB-00CRA1, ATA DISK drive
[   21.553651] hdd: ST380020A, ATA DISK drive
[   21.617075] ide1 at 0x170-0x177,0x376 on irq 15
[   21.624902] SCSI subsystem initialized
[   21.629445] libata version 2.00 loaded.
[   21.631315] ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 20 (level, low) -> IRQ
 20
[   21.631422] ohci_hcd 0000:00:0f.0: OHCI Host Controller
[   21.631766] ohci_hcd 0000:00:0f.0: new USB bus registered, assigned bus numbe
r 1
[   21.631854] ohci_hcd 0000:00:0f.0: irq 20, io mem 0xff6fd000
[   21.638369] hda: max request size: 512KiB
[   21.684576] hda: 625142448 sectors (320072 MB) w/16384KiB Cache, CHS=38913/25
5/63, UDMA(100)
[   21.691276] usb usb1: configuration #1 chosen from 1 choice
[   21.691957] hub 1-0:1.0: USB hub found
[   21.692010] hub 1-0:1.0: 3 ports detected
[   21.708970] hda: cache flushes supported
[   21.709056]  hda: hda1 hda2 hda3 hda4
[   21.732905] hdc: max request size: 128KiB
[   21.734764] hdb: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66
)
[   21.734992] Uniform CD-ROM driver Revision: 3.20
[   21.750415] hdc: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/6
3, UDMA(100)
[   21.750567] hdc: cache flushes not supported
[   21.750626]  hdc: hdc1 hdc2 < hdc5 >
[   21.769167] hdd: max request size: 128KiB
[   21.770394] hdd: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/6
3, UDMA(100)
[   21.770546] hdd: cache flushes not supported
[   21.770613]  hdd:<6>ACPI: PCI Interrupt 0000:00:0f.1[B] -> GSI 21 (level, low
) -> IRQ 21
[   21.797187] ohci_hcd 0000:00:0f.1: OHCI Host Controller
[   21.797253] ohci_hcd 0000:00:0f.1: new USB bus registered, assigned bus numbe
r 2
[   21.797338] ohci_hcd 0000:00:0f.1: irq 21, io mem 0xff6fc000
[   21.801740]  hdd1 hdd3
[   21.858998] usb usb2: configuration #1 chosen from 1 choice
[   21.859070] hub 2-0:1.0: USB hub found
[   21.859122] hub 2-0:1.0: 3 ports detected
[   21.964844] ACPI: PCI Interrupt 0000:00:0f.2[C] -> GSI 22 (level, low) -> IRQ
 22
[   21.964952] ohci_hcd 0000:00:0f.2: OHCI Host Controller
[   21.965023] ohci_hcd 0000:00:0f.2: new USB bus registered, assigned bus numbe
r 3
[   21.965108] ohci_hcd 0000:00:0f.2: irq 22, io mem 0xff6fb000
[   21.968837] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   21.968973] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   21.969102] ide: failed opcode was: unknown
[   22.026726] usb usb3: configuration #1 chosen from 1 choice
[   22.026798] hub 3-0:1.0: USB hub found
[   22.026850] hub 3-0:1.0: 3 ports detected
[   22.090940] Attempting manual resume
[   22.090988] swsusp: Resume From Partition 3:2
[   22.090989] PM: Checking swsusp image.
[   22.098138] PM: Resume from disk failed.
[   22.118354] kjournald starting.  Commit interval 5 seconds
[   22.118414] EXT3-fs: mounted filesystem with ordered data mode.
[   22.132687] ACPI: PCI Interrupt 0000:00:0f.3[D] -> GSI 23 (level, low) -> IRQ
 23
[   22.132793] ehci_hcd 0000:00:0f.3: EHCI Host Controller
[   22.132859] ehci_hcd 0000:00:0f.3: new USB bus registered, assigned bus numbe
r 4
[   22.132954] ehci_hcd 0000:00:0f.3: debug port 1
[   22.160450] ehci_hcd 0000:00:0f.3: irq 23, io mem 0xff6fe800
[   22.160507] ehci_hcd 0000:00:0f.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 
2004
[   22.160666] usb usb4: configuration #1 chosen from 1 choice
[   22.160733] hub 4-0:1.0: USB hub found
[   22.160784] hub 4-0:1.0: 8 ports detected
[   22.213180] hdd: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   22.213317] hdd: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   22.213446] ide: failed opcode was: unknown
[   22.214211] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   22.214342] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   22.214470] ide: failed opcode was: unknown
[   22.216117] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   22.216248] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   22.216376] ide: failed opcode was: unknown
[   22.217140] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   22.217271] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   22.217399] ide: failed opcode was: unknown
[   22.268467] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 19 (level, low) -> IRQ
 19
[   22.268568] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.htm
l
[   22.268642] 0000:02:07.0: 3Com PCI 3c905B Cyclone 100baseTx at ffffc20000024c
00.
[   22.272235] ide1: reset: success
[   22.276515] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   22.276646] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   22.276774] ide: failed opcode was: unknown
[   22.277801] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   22.277932] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   22.278060] ide: failed opcode was: unknown
[   22.285023] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   22.285153] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   22.285281] ide: failed opcode was: unknown
[   22.286314] hdc: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   22.286445] hdc: dma_intr: error=0x84 { DriveStatusError BadCRC }
[   22.286574] ide: failed opcode was: unknown
[   22.287684] hdd: DMA disabled
[   22.336132] ide1: reset: success
```

This is my lspci output:
```
$ lspci
00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:01.0 PCI bridge: ALi Corporation AGP8X Controller
00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
00:0d.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc R420 JK [Radeon X800]
01:00.1 Display controller: ATI Technologies Inc R420 [Radeon X800] (Secondary)
02:07.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
```

This is my fstab, as you can see I only use the primary master:

```
more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=111f9bb2-32ee-4059-bb0e-7cb0e62b33ed /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=82AD-8AFF  /fat            vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=8406c546-a9dc-484e-9700-573c86dba576 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

This is the contents of /boot:
```
ls /boot
abi-2.6.17-10-generic                  initrd.img-2.6.20-8-generic
abi-2.6.17-11-generic                  initrd.img-2.6.20-8-generic.bak
abi-2.6.20-10-generic                  initrd.img-2.6.20-9-generic
abi-2.6.20-8-generic                   initrd.img-2.6.20-9-generic.bak
abi-2.6.20-9-generic                   memtest86+.bin
config-2.6.17-10-generic               System.map-2.6.17-10-generic
config-2.6.17-11-generic               System.map-2.6.17-11-generic
config-2.6.20-10-generic               System.map-2.6.20-10-generic
config-2.6.20-8-generic                System.map-2.6.20-8-generic
config-2.6.20-9-generic                System.map-2.6.20-9-generic
grub                                   vmlinuz-2.6.17-10-generic
initrd.img-2.6.17-10-generic           vmlinuz-2.6.17-11-generic
initrd.img-2.6.17-11-generic           vmlinuz-2.6.20-10-generic
initrd.img-2.6.17-11-generic.dpkg-bak  vmlinuz-2.6.20-8-generic
initrd.img-2.6.20-10-generic           vmlinuz-2.6.20-9-generic
```

Now I've been having problems with ubuntu not booting for a couple of kernel revisions, even before I upgraded to feisty around herd4 release time. However, given that my box often stays up for a while I never thought much of it. 

From what I can see from google, and assorted forums, it looks like it could be cable, drive or motherboard issue. Also, it appears the drive with the problem is actually my XP boot disk, and not my Ubuntu partition/drive. They're not even on the same IDE channel. So can DMA issues on one channel be affecting the other? How likely is it that this is the real problem?

This is my DMA setup:
```
sudo hdparm -d /dev/hda
/dev/hda:
 using_dma    =  1 (on)

sudo hdparm -d /dev/hdb

/dev/hdb:
 using_dma    =  1 (on)

sudo hdparm -d /dev/hdc

/dev/hdc:
 using_dma    =  1 (on)

sudo hdparm -d /dev/hdd

/dev/hdd:
 using_dma    =  0 (off)

$ sudo hdparm -i /dev/hda
Password:

/dev/hda:

 Model=ST3320620A, FwRev=3.AAC, SerialNo=5QF04XA5
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode

$ sudo hdparm -i /dev/hdb

/dev/hdb:

 Model=LITE-ON DVDRW SHW-16H5S, FwRev=LS0W, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 sdma? mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode

$ sudo hdparm -i /dev/hdc

/dev/hdc:

 Model=WDC WD800JB-00CRA1, FwRev=17.07W17, SerialNo=WD-WMA8E3351303
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=40
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 *udma3 udma4 udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5

 * signifies the current active mode

$ sudo hdparm -i /dev/hdd

/dev/hdd:

 Model=ST380020A, FwRev=3.39, SerialNo=5GCMJ2ZT
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode
```
The only thing I can see here is that the DMA level on hdc my XP drive seems to be reduced. 

I'm going to back it up, and experiment with my IDE cables, etc. But I just wondered if anyone had any opinions or had seen this before?

---

### Post by praxis22 on 2007-03-15
anyone?

---

### Post by ChrisNiemy on 2007-03-18
for me a new IDE-cable solved the problem. even the old one looked good though. Had this errors for a long time, and now everything seems to work fine.

Or maybe try to set the IO32_support mode with hdparm (-c Option) to "3" rather than "1". this option is a little bit slower, but works better, if you get error messages like this. so "hdparm -c3 /dev/hdX"

Try to let settings in BIOS concerning HD/IDE to default or auto settings.

When using DMA you should/must have enabled also the IO32_support (-c option ,see above) Perhaps that was missing.

Further troubleshooting could be to disable the multisector-count (-m option). It brings hardly an advantage when DMA is working. Also try to disable the unmask IRQ option (-u). See "man hdparm" oder the comments in "/etc/hdparm.conf"

Just look, how your IDEs are connected and change the cables.

---

### Post by praxis22 on 2007-03-19
Thanks for the reply.

I plan on removing both my old XP drives, (hand me down's from my wife :) and replacing them with another single 320Gb Seagate. I'll yank the cable too, see how it goes. I think I may be having kernel module problems too, but I'll check that after I replace the drives.

---

### Post by ChrisNiemy on 2007-03-19
Seagate is a good choice, also Samsung. I personally dislike WD a little bit. Too loud.

Check if the cable is well handled and connected.

---

