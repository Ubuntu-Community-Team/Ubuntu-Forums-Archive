---
title: "Cannot enter on my second hardisk"
date: 2008-10-19
forum: Hardware
---

### Post by RevolutionnaireY on 2008-10-19
Hi here the problem, I have two hard disk, and my big one got the videos, text, music and all data on it. Now when I<m triyng to connect on it with a system ( its on my old system that I cant access because it just doesnt want to and I didnt format because I was waiting the new ubuntu to do it so I just installed an other ubuntu on my other hard drive) anyway here is what happen when I try to connect to that hard drive.

mount wrong fs type, bad option, bad supeblock on /dev/hdb1, missing codepage or helped program or other error In some cases useful info is found in syslog -try dmesg tail or so

so here I tried:

 0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff30000 (usable)
[    0.000000]  BIOS-e820: 000000001ff30000 - 000000001ff40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff40000 - 000000001fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff0000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 130864) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130864
[    0.000000]   HighMem    130864 ->   130864
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130864
[    0.000000] On node 0 totalpages: 130864
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 990 pages used for memmap
[    0.000000]   Normal zone: 125778 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FAAC0 checksum 0
[    0.000000] ACPI: RSDP 000FAAC0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 1FF30000, 0030 (r1 A M I  OEMRSDT   8000403 MSFT       97)
[    0.000000] ACPI: FACP 1FF30200, 0081 (r1 A M I  OEMFACP   8000403 MSFT       97)
[    0.000000] ACPI: DSDT 1FF303E0, 362A (r1  A0091 A0091006        6 MSFT  100000D)
[    0.000000] ACPI: FACS 1FF40000, 0040
[    0.000000] ACPI: APIC 1FF30390, 004A (r1 A M I  OEMAPIC   8000403 MSFT       97)
[    0.000000] ACPI: OEMB 1FF40040, 003F (r1 A M I  OEMBIOS   8000403 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dff80000)
[    0.000000] Built 1 zonelists.  Total pages: 129842
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1802.484 MHz processor.
[   30.437370] Console: colour VGA+ 80x25
[   30.437642] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   30.437855] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   30.447281] Memory: 507148k/523456k available (2015k kernel code, 15680k reserved, 916k data, 364k init, 0k highmem)
[   30.447292] virtual kernel memory layout:
[   30.447293]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   30.447294]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   30.447296]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   30.447297]     lowmem  : 0xc0000000 - 0xdff30000   ( 511 MB)
[   30.447298]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   30.447300]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   30.447301]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   30.447304] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   30.447339] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   30.527348] Calibrating delay using timer specific routine.. 3608.85 BogoMIPS (lpj=7217716)
[   30.527371] Security Framework v1.0.0 initialized
[   30.527378] SELinux:  Disabled at boot.
[   30.527391] Mount-cache hash table entries: 512
[   30.527495] CPU: After generic identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[   30.527503] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   30.527506] CPU: L2 Cache: 512K (64 bytes/line)
[   30.527509] CPU: After all inits, caps: 078bfbff e1d3fbff 00000000 00000410 00000000 00000000 00000000
[   30.527518] Compat vDSO mapped to ffffe000.
[   30.527527] Checking 'hlt' instruction... OK.
[   30.543452] SMP alternatives: switching to UP code
[   30.543582] Freeing SMP alternatives: 11k freed
[   30.543838] Early unpacking initramfs... done
[   30.872602] ACPI: Core revision 20070126
[   30.872664] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   30.885397] CPU0: AMD Athlon(tm) 64 Processor 2800+ stepping 00
[   30.885418] Total of 1 processors activated (3608.85 BogoMIPS).
[   30.885911] ENABLING IO-APIC IRQs
[   30.886229] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   31.031281] Brought up 1 CPUs
[   31.031434] Booting paravirtualized kernel on bare hardware
[   31.031523] Time:  1:18:17  Date: 09/20/108
[   31.031545] NET: Registered protocol family 16
[   31.031624] EISA bus registered
[   31.031640] ACPI: bus type pci registered
[   31.032292] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   31.032295] PCI: Using configuration type 1
[   31.032297] Setting up standard PCI resources
[   31.038543] ACPI: EC: Look up EC in DSDT
[   31.041221] ACPI: Interpreter enabled
[   31.041223] ACPI: (supports S0 S1 S3 S4 S5)
[   31.041238] ACPI: Using IOAPIC for interrupt routing
[   31.046374] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   31.046384] PCI: Probing PCI hardware (bus 00)
[   31.046868] PCI: enabled onboard AC97/MC97 devices
[   31.047073] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   31.052305] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[   31.052392] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
[   31.052477] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[   31.052561] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   31.052646] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   31.052730] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   31.052815] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   31.052900] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   31.052965] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.052974] pnp: PnP ACPI init
[   31.052982] ACPI: bus type pnp registered
[   31.055534] pnp: PnP ACPI: found 11 devices
[   31.055537] ACPI: ACPI bus type pnp unregistered
[   31.055540] PnPBIOS: Disabled by ACPI PNP
[   31.055583] PCI: Using ACPI for IRQ routing
[   31.055586] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   31.058370] NET: Registered protocol family 8
[   31.058372] NET: Registered protocol family 20
[   31.058428] pnp: 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
[   31.058431] pnp: 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[   31.058434] pnp: 00:08: iomem range 0xfff80000-0xffffffff could not be reserved
[   31.058439] pnp: 00:0a: iomem range 0x0-0x9ffff could not be reserved
[   31.058442] pnp: 00:0a: iomem range 0xc0000-0xdffff could not be reserved
[   31.058445] pnp: 00:0a: iomem range 0xe0000-0xfffff could not be reserved
[   31.058448] pnp: 00:0a: iomem range 0x100000-0x1ffeffff could not be reserved
[   31.059245] Time: tsc clocksource has been installed.
[   31.088703] PCI: Bridge: 0000:00:01.0
[   31.088705]   IO window: disabled.
[   31.088709]   MEM window: f3700000-f58fffff
[   31.088712]   PREFETCH window: e3400000-f35fffff
[   31.088727] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   31.088740] NET: Registered protocol family 2
[   31.127271] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   31.127318] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   31.127490] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   31.127606] TCP: Hash tables configured (established 16384 bind 16384)
[   31.127609] TCP reno registered
[   31.139339] checking if image is initramfs... it is
[   31.591133] Switched to high resolution mode on CPU 0
[   31.786422] Freeing initrd memory: 7305k freed
[   31.786776] audit: initializing netlink socket (disabled)
[   31.786789] audit(1224465497.000:1): initialized
[   31.788358] VFS: Disk quotas dquot_6.5.1
[   31.788399] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   31.788483] io scheduler noop registered
[   31.788485] io scheduler anticipatory registered
[   31.788487] io scheduler deadline registered
[   31.788501] io scheduler cfq registered (default)
[   31.788511] PCI: VIA PCI bridge detected. Disabling DAC.
[   31.788577] Boot video device is 0000:01:00.0
[   31.788695] isapnp: Scanning for PnP cards...
[   32.142364] isapnp: No Plug & Play device found
[   32.162314] Real Time Clock Driver v1.12ac
[   32.162394] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   32.162476] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   32.162971] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   32.163552] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   32.163716] input: Macintosh mouse button emulation as /class/input/input0
[   32.163808] PNP: No PS/2 controller found. Probing ports directly.
[   32.164197] serio: i8042 KBD port at 0x60,0x64 irq 1
[   32.164202] serio: i8042 AUX port at 0x60,0x64 irq 12
[   32.164334] mice: PS/2 mouse device common for all mice
[   32.164428] EISA: Probing bus 0 at eisa.0
[   32.164436] Cannot allocate resource for EISA slot 1
[   32.164467] EISA: Detected 0 cards.
[   32.164621] TCP cubic registered
[   32.164638] NET: Registered protocol family 1
[   32.164658] Using IPI No-Shortcut mode
[   32.164816]   Magic number: 12:899:306
[   32.164926]   hash matches device tty35
[   32.165270] Freeing unused kernel memory: 364k freed
[   33.359667] AppArmor: AppArmor initialized<5>audit(1224465498.500:2):  type=1505 info="AppArmor initialized" pid=1180
[   33.367171] fuse init (API version 7.8)
[   33.372277] Failure registering capabilities with primary security module.
[   33.859443] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 16
[   33.859477] skge 1.11 addr 0xf7e00000 irq 16 chip Yukon-Lite rev 7
[   33.859597] skge eth0: addr 00:11:2f:a1:57:49
[   33.886758] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   33.886764] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   33.887320] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   33.887343] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 17
[   33.887353] VP_IDE: chipset revision 6
[   33.887356] VP_IDE: not 100% native mode: will probe irqs later
[   33.887366] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   33.887375]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[   33.887386]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[   33.887393] Probing IDE interface ide0...
[   33.920816] SCSI subsystem initialized
[   33.925171] libata version 2.21 loaded.
[   33.943903] usbcore: registered new interface driver usbfs
[   33.943929] usbcore: registered new interface driver hub
[   33.943948] usbcore: registered new device driver usb
[   33.944642] USB Universal Host Controller Interface driver v3.0
[   34.087724] Floppy drive(s): fd0 is 1.44M
[   34.154310] FDC 0 is a post-1991 82077
[   34.302556] hda: WDC WD800JB-00JJA0, ATA DISK drive
[   34.582489] hdb: ST3320620A, ATA DISK drive
[   34.639057] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   43.163790] Probing IDE interface ide1...
[   44.028203] hdc: HL-DT-ST RW/DVD GCC-4521B, ATAPI CD/DVD-ROM drive
[   44.812013] hdd: HL-DT-ST DVDRAM GSA-4160B, ATAPI CD/DVD-ROM drive
[   44.870931] ide1 at 0x170-0x177,0x376 on irq 15
[   44.878325] sata_via 0000:00:0f.0: version 2.2
[   44.878343] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 17
[   44.878385] sata_via 0000:00:0f.0: routed to hard irq line 10
[   44.878456] scsi0 : sata_via
[   44.878654] scsi1 : sata_via
[   44.878781] ata1: SATA max UDMA/133 cmd 0x0001e800 ctl 0x0001e402 bmdma 0x0001d400 irq 17
[   44.878785] ata2: SATA max UDMA/133 cmd 0x0001e000 ctl 0x0001d802 bmdma 0x0001d408 irq 17
[   44.884052] hda: max request size: 128KiB
[   44.896362] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(33)
[   44.897169] hda: cache flushes supported
[   44.897209]  hda: hda1 hda2 < hda5 > hda3 hda4
[   44.957644] hdb: max request size: 512KiB
[   45.000500] hdb: 625142448 sectors (320072 MB) w/16384KiB Cache, CHS=38913/255/63, UDMA(33)
[   45.024867] hdb: cache flushes supported
[   45.024891]  hdb: hdb1 hdb2
[   45.068774] hdc: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   45.068783] Uniform CD-ROM driver Revision: 3.20
[   45.072385] hdd: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   45.079871] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   45.291825] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   45.303294] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 18
[   45.303306] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   45.303453] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   45.303483] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000dc00
[   45.303603] usb usb1: configuration #1 chosen from 1 choice
[   45.303628] hub 1-0:1.0: USB hub found
[   45.303636] hub 1-0:1.0: 2 ports detected
[   45.403909] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 18
[   45.403923] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   45.403945] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   45.403967] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000ec00
[   45.404060] usb usb2: configuration #1 chosen from 1 choice
[   45.404087] hub 2-0:1.0: USB hub found
[   45.404093] hub 2-0:1.0: 2 ports detected
[   45.507863] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 18
[   45.507876] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   45.507899] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   45.507921] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000c000
[   45.508012] usb usb3: configuration #1 chosen from 1 choice
[   45.508036] hub 3-0:1.0: USB hub found
[   45.508042] hub 3-0:1.0: 2 ports detected
[   45.611845] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 18
[   45.611858] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   45.611880] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   45.611902] uhci_hcd 0000:00:10.3: irq 18, io base 0x0000c400
[   45.611992] usb usb4: configuration #1 chosen from 1 choice
[   45.612020] hub 4-0:1.0: USB hub found
[   45.612027] hub 4-0:1.0: 2 ports detected
[   45.715855] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 18
[   45.715864] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   45.715883] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   45.715913] ehci_hcd 0000:00:10.4: irq 18, io mem 0xf7f00000
[   45.771708] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   45.771724] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   45.771835] usb usb5: configuration #1 chosen from 1 choice
[   45.771861] hub 5-0:1.0: USB hub found
[   45.771868] hub 5-0:1.0: 8 ports detected
[   47.023604] end_request: I/O error, dev fd0, sector 0
[   47.211342] usb 5-8: new high speed USB device using ehci_hcd and address 4
[   47.345236] usb 5-8: configuration #1 chosen from 2 choices
[   47.583254] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   47.758045] usb 4-1: configuration #1 chosen from 1 choice
[   47.761559] usbcore: registered new interface driver libusual
[   47.765139] Initializing USB Mass Storage driver...
[   47.999151] usb 1-2: new low speed USB device using uhci_hcd and address 3
[   48.170305] usb 1-2: configuration #1 chosen from 1 choice
[   48.173420] scsi2 : SCSI emulation for USB Mass Storage devices
[   48.173455] usb-storage: device found at 4
[   48.173457] usb-storage: waiting for device to settle before scanning
[   48.173478] usbcore: registered new interface driver usb-storage
[   48.173480] USB Mass Storage support registered.
[   48.173571] usbcore: registered new interface driver hiddev
[   48.190993] input: Logitech USB Receiver as /class/input/input1
[   48.191016] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:10.3-1
[   48.205371] input: USB-compliant keyboard as /class/input/input2
[   48.205382] input: USB HID v1.10 Keyboard [USB-compliant keyboard] on usb-0000:00:10.0-2
[   48.218351] input: USB-compliant keyboard as /class/input/input3
[   48.218356] input: USB HID v1.10 Device [USB-compliant keyboard] on usb-0000:00:10.0-2
[   48.218366] usbcore: registered new interface driver usbhid
[   48.218369] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   53.170192] usb-storage: device scan complete
[   53.170815] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[   53.177795] sd 2:0:0:0: [sda] 14651280 2048-byte hardware sectors (30006 MB)
[   53.178793] sd 2:0:0:0: [sda] Write Protect is off
[   53.178796] sd 2:0:0:0: [sda] Mode Sense: 68 00 00 08
[   53.178798] sd 2:0:0:0: [sda] Assuming drive cache: write through
[   53.180942] sd 2:0:0:0: [sda] 14651280 2048-byte hardware sectors (30006 MB)
[   53.181934] sd 2:0:0:0: [sda] Write Protect is off
[   53.181937] sd 2:0:0:0: [sda] Mode Sense: 68 00 00 08
[   53.181939] sd 2:0:0:0: [sda] Assuming drive cache: write through
[   53.181943]  sda: sda1 sda2
[   53.201366] sd 2:0:0:0: [sda] Attached SCSI removable disk
[   53.205339] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   59.176632] end_request: I/O error, dev fd0, sector 0
[   59.176639] Buffer I/O error on device fd0, logical block 0
[   71.334623] end_request: I/O error, dev fd0, sector 0
[   71.334626] Buffer I/O error on device fd0, logical block 0
[   84.502681] end_request: I/O error, dev fd0, sector 0
[   96.659752] end_request: I/O error, dev fd0, sector 0
[   96.659756] Buffer I/O error on device fd0, logical block 0
[  108.809186] end_request: I/O error, dev fd0, sector 0
[  108.809188] Buffer I/O error on device fd0, logical block 0
[  108.885265] kjournald starting.  Commit interval 5 seconds
[  108.885276] EXT3-fs: mounted filesystem with ordered data mode.
[  108.916292] kjournald starting.  Commit interval 5 seconds
[  108.916303] EXT3-fs: mounted filesystem with ordered data mode.
[  109.484260] ISO 9660 Extensions: Microsoft Joliet Level 3
[  109.538638] ISO 9660 Extensions: RRIP_1991A
[  109.836707] Registering unionfs 1.4
[  109.836711] unionfs: debugging is not enabled
[  109.852491] loop: module loaded
[  110.184715] squashfs: version 3.2-UBUNTU (2007/07/26) Phillip Lougher
[  191.172519] Linux agpgart interface v0.102 (c) Dave Jones
[  191.391778] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  191.519182] agpgart: Detected AGP bridge 0
[  191.522356] agpgart: AGP aperture is 64M @ 0xf8000000
[  193.074189] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  194.154060] Linux video capture interface: v2.00
[  195.202912] input: PC Speaker as /class/input/input4
[  195.209804] parport_pc 00:06: reported by Plug and Play ACPI
[  195.209845] parport0: PC-style at 0x378, irq 7 [PCSPP]
[  196.450687] cx2388x v4l2 driver version 0.0.6 loaded
[  196.450740] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 17 (level, low) -> IRQ 16
[  196.450784] CORE cx88[0]: subsystem: 107d:6613, board: Leadtek Winfast 2000XP Expert [card=5,autodetected]
[  196.450788] TV tuner 44 at 0x1fe, Radio tuner -1 at 0x1fe
[  196.595631] cx88[0]: Leadtek Winfast 2000XP Expert config: tuner=43, eeprom[0]=0x01
[  196.595797] input: cx88 IR (Leadtek Winfast 2000XP as /class/input/input5
[  196.595836] cx88[0]/0: found at 0000:00:0c.0, rev: 5, irq: 16, latency: 64, mmio: 0xf6000000
[  197.400992] tuner 1-0043: chip found @ 0x86 (cx88[0])
[  197.401024] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[  197.402896] tuner 1-0060: All bytes are equal. It is not a TEA5767
[  197.402899] tuner 1-0060: chip found @ 0xc0 (cx88[0])
[  197.402910] tuner 1-0060: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[  197.402913] tuner 1-0060: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[  197.410208] cx88[0]/0: registered device video0 [v4l2]
[  197.410234] cx88[0]/0: registered device vbi0
[  197.410262] cx88[0]/0: registered device radio0
[  197.411535] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 19
[  197.415067] PCI: Setting latency timer of device 0000:00:11.5 to 64
[  197.929612] codec_read: codec 0 is not valid [0xfe0000]
[  197.936131] codec_read: codec 0 is not valid [0xfe0000]
[  197.942691] codec_read: codec 0 is not valid [0xfe0000]
[  197.949213] codec_read: codec 0 is not valid [0xfe0000]
[  197.968038] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[  197.968045] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 19
[  198.718732] PCI: Setting latency timer of device 0000:00:11.6 to 64
[  199.222787] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[  199.222797] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[  200.988922] Adding 3486096k swap on /dev/hda4.  Priority:-1 extents:1 across:3486096k
[  200.989965] Adding 1510036k swap on /dev/hda5.  Priority:-2 extents:1 across:1510036k
[  204.272485] No dock devices found.
[  204.408503] input: Power Button (FF) as /class/input/input6
[  204.412576] ACPI: Power Button (FF) [PWRF]
[  204.452035] input: Power Button (CM) as /class/input/input7
[  204.456137] ACPI: Power Button (CM) [PWRB]
[  204.495451] input: Sleep Button (CM) as /class/input/input8
[  204.499523] ACPI: Sleep Button (CM) [SLPB]
[  205.304642] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 2800+ processors (version 2.00.00)
[  205.305770] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[  212.110177] lp0: using parport0 (interrupt-driven).
[  212.766553] ppdev: user-space parallel port driver
[  215.833590] skge eth0: enabling interface
[  215.961526] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  215.961531] apm: overridden by ACPI.
[  216.362618] Failure registering capabilities with primary security module.
[  218.062292] Bluetooth: Core ver 2.11
[  218.062507] NET: Registered protocol family 31
[  218.062509] Bluetooth: HCI device and connection manager initialized
[  218.062513] Bluetooth: HCI socket layer initialized
[  218.115428] Bluetooth: L2CAP ver 2.8
[  218.115432] Bluetooth: L2CAP socket layer initialized
[  218.156529] Bluetooth: RFCOMM socket layer initialized
[  218.156723] Bluetooth: RFCOMM TTY layer initialized
[  218.156726] Bluetooth: RFCOMM ver 1.8
[  218.785771] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[  227.012495] NET: Registered protocol family 17
[  232.670627] NET: Registered protocol family 10
[  232.670733] lo: Disabled Privacy Extensions
[  242.716410] eth0: no IPv6 routers present
[  335.787014] JFS: nTxBlock = 4024, nTxLock = 32192


ps: sorry for the log I dont understand anything so I just put it all there

Thanx!

---

