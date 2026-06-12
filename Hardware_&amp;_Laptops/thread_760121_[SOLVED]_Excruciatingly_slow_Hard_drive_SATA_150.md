---
title: "[SOLVED] Excruciatingly slow Hard drive SATA 150"
date: 2008-04-19
forum: Hardware &amp; Laptops
---

### Post by bretticus on 2008-04-19
Just put together a new computer. Vista was already installed and I just installed 8.04 RC 1 amd64 on it today (dual boot.) Performance is more than acceptable in Vista, horrid in Ubuntu. 

Here is my hardware inventory:
AMD Athlon 64 X2 5400
Gigabyte GA-MA78GM-S2H (Native IDE mode for SATA controller. Fw. ver. F3)
2GB (2 x 1GB) DDR2 800 (PC2 6400)
[250 GB Seagate SATA 150]("http://tinyurl.com/66dfea")

As you can see my hard drive performance is abysmal:

```
$ sudo hdparm -tT /dev/sda
[sudo] password for brett: 

/dev/sda:
 Timing cached reads:   1080 MB in  2.00 seconds = 539.97 MB/sec
 Timing buffered disk reads:    6 MB in  3.59 seconds =   1.67 MB/sec
```

```
$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=ST3250823AS                             , FwRev=3.06    , SerialNo=            4ND2SHP7
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=488397168
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

```

Kernel:
```
$ uname -a
Linux brett-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
```

More information...

```
$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
```

ATA device information on startup:

```
~$ dmesg | grep ata
[    0.000000]  BIOS-e820: 000000006fee3000 - 000000006fef0000 (ACPI data)
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Memory: 1795152k/1833856k available (2466k kernel code, 38316k reserved, 1309k data, 316k init)
[    0.000000] libata version 3.00 loaded.
[    0.000000] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 509
[    0.000000] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 509
[    0.000000] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 509
[    0.000000] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 509
[    0.000000] ata1: SATA link down (SStatus 0 SControl 300)
[    0.000000] ata2: SATA link down (SStatus 0 SControl 300)
[    0.000000] ata3: SATA link down (SStatus 0 SControl 300)
[    0.000000] ata4: SATA link down (SStatus 0 SControl 300)
[    0.000000] scsi6 : pata_atiixp
[    0.000000] scsi7 : pata_atiixp
[    0.000000] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    0.000000] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    0.000000] ata5.00: ATAPI: SONY    CD-RW  CRX320E, NYK5, max UDMA/33
[    0.000000] ata5.01: ATAPI: _NEC DVD_RW ND-3550A, 1.07, max UDMA/33
[    0.000000] ata5.00: configured for UDMA/33
[    0.000000] ata5.01: configured for UDMA/33
[    0.000000] ata6.00: HPA unlocked: 488395055 -> 488397168, native 488397168
[    0.000000] ata6.00: ATA-7: ST3250823AS, 3.06, max UDMA/133
[    0.000000] ata6.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.000000] ata6.00: simplex DMA is claimed by other device, disabling DMA
[    0.000000] ata6.00: configured for PIO4
[    0.000000] EXT3-fs: mounted filesystem with ordered data mode.
[    0.000000] EXT3-fs: mounted filesystem with ordered data mode.
[    0.000000] ata5.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[    0.000000] ata5.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[    0.000000] ata5.01: status: { DRDY ERR }
[    0.000000] ata5.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[    0.000000] ata5.01: cmd a0/00:00:00:08:00/00:00:00:00:00/b0 tag 0 pio 8 in
[    0.000000] ata5.01: status: { DRDY ERR }

```

Looks like one of my dvd/cdrom drives could be having race conditions (never saw this behavior with drive in old board.) Possibly connected? 

I saw some similar posts where this issue was solved by disabling acpi. This had no effect (improvement)  for me. You can see parameters passed to kernel below. 
```

$ dmesg | head
[    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] Command line: root=UUID=bec3e5ee-25af-49b4-8723-c4e8da6054a3 ro quiet splash acpi=off
```

Storage modules...
```
$ lsmod | grep ata
ata_generic             9988  0 
pata_atiixp            10496  3 
pata_acpi               9856  0 
libata                176304  4 ata_generic,pata_atiixp,pata_acpi,ahci
scsi_mod              178488  6 sbp2,sg,sd_mod,sr_mod,usb_storage,libata
```

I saw one post mentioning that the owners pata devices were sharing ata modules with the owner's sata drive. I wouldn't even knwo where to begin to remedy that if that has something to do with this.

I'd appreciate any direction. I'm stumped.

Thanks!

---

### Post by bretticus on 2008-04-19
Reading over my post, I saw that, during startup, something was disabling dma for my hard drive:

> [    0.000000] ata6.00: HPA unlocked: 488395055 -> 488397168, native 488397168
[    0.000000] ata6.00: ATA-7: ST3250823AS, 3.06, max UDMA/133
[    0.000000] ata6.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.000000] ata6.00: simplex DMA is claimed by other device, disabling DMA


So I googled and found this [very helpful post]("http://ubuntuforums.org/showthread.php?t=678153").

I followed the instructions there...

> So I blacklisted ata_generic and added pata_atiixp to /etc/initramfs-tools/modules
Code:

pata_atiixp
blacklist ata_generic

and recreated the initramfs with
Code:

sudo update-initramfs -u

and, after a reboot, the speed was better:

My performance is MUCH better as well.

```
$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   2778 MB in  2.00 seconds = 1388.23 MB/sec
 Timing buffered disk reads:  196 MB in  3.02 seconds =  64.95 MB/sec
```

---

