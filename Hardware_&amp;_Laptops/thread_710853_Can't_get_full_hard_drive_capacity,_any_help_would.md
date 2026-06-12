---
title: "Can't get full hard drive capacity, any help would be entirely grateful."
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by t0dk0n on 2008-02-28
Hello, I've had this hard drive for about 4/5 years now, within those years, its hosted many different distributions (Slackware, Gentoo, Ubuntu, Zenwalk, then Ubuntu again). I'm not quite sure what company manufactures it anymore, but its a 160GB hard drive. After buying it, I actually read the box and it had said I need Windows XP Pro SP2 in order to get that full capacity, but I personally can't stand Windows even having a partition. Using Linux, I only get about 32GB out of that whole 160GB. I've been told that a Ultra ATA or SATA card should resolve this problem, but I guess I don't have the proper software to accompany this. I'd love to finally solve this problem once and for all, without having to install a windows partition.

Here's my dmesg:

> [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fffc000 (usable)
[    0.000000]  BIOS-e820: 000000002fffc000 - 000000002ffff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002ffff000 - 0000000030000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 196604) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196604
[    0.000000]   HighMem    196604 ->   196604
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196604
[    0.000000] On node 0 totalpages: 196604
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1503 pages used for memmap
[    0.000000]   Normal zone: 191005 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F5DC0 checksum 0
[    0.000000] ACPI: RSDP 000F5DC0, 0014 (r0 ASUS  )
[    0.000000] ACPI: RSDT 2FFFC000, 0030 (r1 ASUS   A7V8X-X  42302E31 MSFT 31313031)
[    0.000000] ACPI: FACP 2FFFC0B2, 0074 (r1 ASUS   A7V8X-X  42302E31 MSFT 31313031)
[    0.000000] ACPI: DSDT 2FFFC126, 297E (r1   ASUS A7V8X-X      1000 MSFT  100000B)
[    0.000000] ACPI: FACS 2FFFF000, 0040
[    0.000000] ACPI: BOOT 2FFFC030, 0028 (r1 ASUS   A7V8X-X  42302E31 MSFT 31313031)
[    0.000000] ACPI: APIC 2FFFC058, 005A (r1 ASUS   A7V8X-X  42302E31 MSFT 31313031)
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
[    0.000000] Built 1 zonelists.  Total pages: 195069
[    0.000000] Kernel command line: root=UUID=0ea93f02-68a0-4d7d-bbaf-e950ca21677b ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1800.231 MHz processor.
[   25.386246] Console: colour VGA+ 80x25
[   25.387294] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   25.389038] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   25.418186] Memory: 767756k/786416k available (2015k kernel code, 17940k reserved, 915k data, 364k init, 0k highmem)
[   25.418199] virtual kernel memory layout:
[   25.418200]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   25.418201]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   25.418203]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   25.418204]     lowmem  : 0xc0000000 - 0xefffc000   ( 767 MB)
[   25.418206]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   25.418207]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   25.418209]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   25.418213] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   25.418268] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   25.498176] Calibrating delay using timer specific routine.. 3603.57 BogoMIPS (lpj=7207145)
[   25.498217] Security Framework v1.0.0 initialized
[   25.498227] SELinux:  Disabled at boot.
[   25.498247] Mount-cache hash table entries: 512
[   25.498432] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[   25.498445] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   25.498448] CPU: L2 Cache: 256K (64 bytes/line)
[   25.498451] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[   25.498465] Compat vDSO mapped to ffffe000.
[   25.498482] Checking 'hlt' instruction... OK.
[   25.514331] SMP alternatives: switching to UP code
[   25.514693] Freeing SMP alternatives: 11k freed
[   25.515196] Early unpacking initramfs... done
[   25.875400] ACPI: Core revision 20070126
[   25.875515] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   25.879611] CPU0: AMD Athlon(TM) XP 2200+ stepping 00
[   25.879639] Total of 1 processors activated (3603.57 BogoMIPS).
[   25.880375] ENABLING IO-APIC IRQs
[   25.880703] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   26.025490] Brought up 1 CPUs
[   26.025713] Booting paravirtualized kernel on bare hardware
[   26.025813] Time: 17:34:06  Date: 01/28/108
[   26.025857] NET: Registered protocol family 16
[   26.026003] EISA bus registered
[   26.026021] ACPI: bus type pci registered
[   26.027394] PCI: PCI BIOS revision 2.10 entry at 0xf15e0, last bus=1
[   26.027398] PCI: Using configuration type 1
[   26.027400] Setting up standard PCI resources
[   26.040499] ACPI: EC: Look up EC in DSDT
[   26.045896] ACPI: Interpreter enabled
[   26.045901] ACPI: (supports S0 S1 S4 S5)
[   26.045919] ACPI: Using IOAPIC for interrupt routing
[   26.052066] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.052079] PCI: Probing PCI hardware (bus 00)
[   26.052604] PCI quirk: region e400-e47f claimed by vt8235 PM
[   26.052609] PCI quirk: region e800-e80f claimed by vt8235 SMB
[   26.052846] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.053040] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   26.054557] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   26.054639] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   26.054716] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   26.054792] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[   26.054877] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14) *9
[   26.054990] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 *15), disabled.
[   26.055071] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[   26.055163] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.055179] pnp: PnP ACPI init
[   26.055192] ACPI: bus type pnp registered
[   26.059291] pnp: PnP ACPI: found 14 devices
[   26.059294] ACPI: ACPI bus type pnp unregistered
[   26.059300] PnPBIOS: Disabled by ACPI PNP
[   26.059387] PCI: Using ACPI for IRQ routing
[   26.059391] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   26.064399] NET: Registered protocol family 8
[   26.064402] NET: Registered protocol family 20
[   26.064501] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   26.064504] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   26.064508] pnp: 00:00: iomem range 0x100000-0x2fffffff could not be reserved
[   26.064511] pnp: 00:00: iomem range 0xfec00000-0xfec000ff could not be reserved
[   26.064518] pnp: 00:02: ioport range 0xe400-0xe47f has been reserved
[   26.064522] pnp: 00:02: ioport range 0xe800-0xe81f could not be reserved
[   26.064526] pnp: 00:02: iomem range 0xfff80000-0xffffffff could not be reserved
[   26.064529] pnp: 00:02: iomem range 0xffb80000-0xffbfffff has been reserved
[   26.064543] pnp: 00:0d: ioport range 0x290-0x297 has been reserved
[   26.064546] pnp: 00:0d: ioport range 0x370-0x375 has been reserved
[   26.065367] Time: tsc clocksource has been installed.
[   26.094885] PCI: Bridge: 0000:00:01.0
[   26.094889]   IO window: d000-dfff
[   26.094895]   MEM window: ef000000-efdfffff
[   26.094899]   PREFETCH window: eff00000-f7ffffff
[   26.094922] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   26.094941] NET: Registered protocol family 2
[   26.133345] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.133642] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   26.137170] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   26.138402] TCP: Hash tables configured (established 131072 bind 65536)
[   26.138408] TCP reno registered
[   26.149474] checking if image is initramfs... it is
[   26.596617] Switched to high resolution mode on CPU 0
[   26.826869] Freeing initrd memory: 7120k freed
[   26.827070] Simple Boot Flag at 0x3a set to 0x1
[   26.827545] audit: initializing netlink socket (disabled)
[   26.827569] audit(1204220047.044:1): initialized
[   26.830245] VFS: Disk quotas dquot_6.5.1
[   26.830328] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   26.830484] io scheduler noop registered
[   26.830487] io scheduler anticipatory registered
[   26.830490] io scheduler deadline registered
[   26.830506] io scheduler cfq registered (default)
[   26.830526] PCI: VIA PCI bridge detected. Disabling DAC.
[   26.830591] Boot video device is 0000:01:00.0
[   26.830836] isapnp: Scanning for PnP cards...
[   27.183922] isapnp: No Plug & Play device found
[   27.230884] Real Time Clock Driver v1.12ac
[   27.231023] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   27.231129] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.232536] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.233641] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   27.234015] input: Macintosh mouse button emulation as /class/input/input0
[   27.234176] PNP: No PS/2 controller found. Probing ports directly.
[   27.237666] serio: i8042 KBD port at 0x60,0x64 irq 1
[   27.237677] serio: i8042 AUX port at 0x60,0x64 irq 12
[   27.237994] mice: PS/2 mouse device common for all mice
[   27.238158] EISA: Probing bus 0 at eisa.0
[   27.238195] Cannot allocate resource for EISA slot 8
[   27.238198] EISA: Detected 0 cards.
[   27.238351] TCP cubic registered
[   27.238362] NET: Registered protocol family 1
[   27.238391] Using IPI No-Shortcut mode
[   27.238645]   Magic number: 12:910:593
[   27.239577] Freeing unused kernel memory: 364k freed
[   28.500412] AppArmor: AppArmor initialized<5>audit(1204220048.544:2):  type=1505 info="AppArmor initialized" pid=1182
[   28.508983] fuse init (API version 7.8)
[   28.515429] Failure registering capabilities with primary security module.
[   29.290142] SCSI subsystem initialized
[   29.296154] libata version 2.21 loaded.
[   29.297692] pata_sil680 0000:00:0b.0: version 0.4.6
[   29.297707] sil680: BA5_EN = 1 clock = 00
[   29.297712] sil680: BA5_EN = 1 clock = 10
[   29.297726] sil680: 133MHz clock.
[   29.297758] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 16
[   29.298000] scsi0 : pata_sil680
[   29.298086] scsi1 : pata_sil680
[   29.298118] ata1: PATA max UDMA/133 cmd 0x0001b800 ctl 0x0001b402 bmdma 0x0001a400 irq 16
[   29.298122] ata2: PATA max UDMA/133 cmd 0x0001b000 ctl 0x0001a802 bmdma 0x0001a408 irq 16
[   29.375179] usbcore: registered new interface driver usbfs
[   29.375223] usbcore: registered new interface driver hub
[   29.375265] usbcore: registered new device driver usb
[   29.376562] USB Universal Host Controller Interface driver v3.0
[   29.429918] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   29.461951] ata1.00: Host Protected Area detected:
[   29.461955]  current size: 66055244 sectors
[   29.461956]  native size: 312581808 sectors
[   29.464177] ata1.00: ATA-6: WDC WD1600JB-00HUA0, 15.05R15, max UDMA/100
[   29.464181] ata1.00: 66055244 sectors, multi 16: LBA48 
[   29.481726] ata1.00: Host Protected Area detected:
[   29.481729]  current size: 66055244 sectors
[   29.481730]  native size: 312581808 sectors
[   29.483892] ata1.00: configured for UDMA/100
[   29.581790] Floppy drive(s): fd0 is 1.44M
[   29.655281] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600JB-00H 15.0 PQ: 0 ANSI: 5
[   29.655617] PCI: Enabling device 0000:00:0e.2 (0014 -> 0016)
[   29.655635] ACPI: PCI Interrupt 0000:00:0e.2[B] -> GSI 18 (level, low) -> IRQ 17
[   29.706574] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[ee000000-ee0007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   29.710257] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 18
[   29.710276] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   29.710640] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   29.710680] uhci_hcd 0000:00:10.0: irq 18, io base 0x00009400
[   29.710909] usb usb1: configuration #1 chosen from 1 choice
[   29.710949] hub 1-0:1.0: USB hub found
[   29.710963] hub 1-0:1.0: 2 ports detected
[   29.715233] FDC 0 is a post-1991 82077
[   29.751905] sd 0:0:0:0: [sda] 66055244 512-byte hardware sectors (33820 MB)
[   29.751930] sd 0:0:0:0: [sda] Write Protect is off
[   29.751933] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.751956] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.752057] sd 0:0:0:0: [sda] 66055244 512-byte hardware sectors (33820 MB)
[   29.752069] sd 0:0:0:0: [sda] Write Protect is off
[   29.752072] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.752090] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.752098]  sda: sda1 sda2 sda3
[   29.781613] sd 0:0:0:0: [sda] Attached SCSI disk
[   29.788326] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   29.812080] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 18
[   29.812102] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   29.812139] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   29.812168] uhci_hcd 0000:00:10.1: irq 18, io base 0x00009000
[   29.812320] usb usb2: configuration #1 chosen from 1 choice
[   29.812357] hub 2-0:1.0: USB hub found
[   29.812366] hub 2-0:1.0: 2 ports detected
[   29.915850] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 18
[   29.915871] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   29.915910] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   29.915939] uhci_hcd 0000:00:10.2: irq 18, io base 0x00008800
[   29.916108] usb usb3: configuration #1 chosen from 1 choice
[   29.916148] hub 3-0:1.0: USB hub found
[   29.916162] hub 3-0:1.0: 2 ports detected
[   29.970522] Attempting manual resume
[   29.970528] swsusp: Resume From Partition 8:2
[   29.970530] PM: Checking swsusp image.
[   29.970817] PM: Resume from disk failed.
[   30.017466] kjournald starting.  Commit interval 5 seconds
[   30.017486] EXT3-fs: mounted filesystem with ordered data mode.
[   30.026556] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 19
[   30.026731] eth0: VIA Rhine II at 0x18000, 00:0c:6e:3d:8f:f0, IRQ 19.
[   30.027476] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[   30.027521] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 18
[   30.027534] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   30.027581] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   30.027647] ehci_hcd 0000:00:10.3: irq 18, io mem 0xed000000
[   30.027692] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   30.027697] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   30.051520] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   30.051549] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   30.051781] usb usb4: configuration #1 chosen from 1 choice
[   30.051821] hub 4-0:1.0: USB hub found
[   30.051838] hub 4-0:1.0: 6 ports detected
[   30.155675] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   30.155707] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   30.155710] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[   30.155724] VP_IDE: chipset revision 6
[   30.155727] VP_IDE: not 100% native mode: will probe irqs later
[   30.155739] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[   30.155750]     ide0: BM-DMA at 0x8400-0x8407, BIOS settings: hda:pio, hdb:pio
[   30.155766]     ide1: BM-DMA at 0x8408-0x840f, BIOS settings: hdc:DMA, hdd:DMA
[   30.155778] Probing IDE interface ide0...
[   30.722425] Probing IDE interface ide1...
[   30.978228] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c00210543cb]
[   30.994023] usb 4-1: new high speed USB device using ehci_hcd and address 2
[   31.129967] usb 4-1: configuration #1 chosen from 1 choice
[   31.369458] usb 4-2: new high speed USB device using ehci_hcd and address 3
[   31.503405] usb 4-2: configuration #1 chosen from 2 choices
[   31.585219] hdc: SAMSUNG DVD-ROM SD-616T, ATAPI CD/DVD-ROM drive
[   32.164264] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   32.338298] usb 3-2: configuration #1 chosen from 1 choice
[   32.344153] hub 3-2:1.0: USB hub found
[   32.346114] hub 3-2:1.0: 3 ports detected
[   32.368047] hdd: 48X12, ATAPI CD/DVD-ROM drive
[   32.424361] ide1 at 0x170-0x177,0x376 on irq 15
[   32.691481] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   32.874153] usb 2-2: configuration #1 chosen from 1 choice
[   33.080872] usb 3-2.1: new full speed USB device using uhci_hcd and address 3
[   33.217793] usb 3-2.1: configuration #1 chosen from 1 choice
[   41.689317] Linux agpgart interface v0.102 (c) Dave Jones
[   41.744611] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[   41.749686] agpgart: AGP aperture is 64M @ 0xf8000000
[   41.776543] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.814138] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.857430] PCI: Enabling device 0000:00:0e.1 (0004 -> 0005)
[   42.872969] gameport: EMU10K1 is pci0000:00:0e.1/gameport0, io 0x9800, speed 1242kHz
[   42.944470] input: PC Speaker as /class/input/input1
[   43.150663] irda_init()
[   43.150701] NET: Registered protocol family 23
[   43.269538] parport_pc 00:0a: reported by Plug and Play ACPI
[   43.269609] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   43.508277] hdc: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[   43.508289] Uniform CD-ROM driver Revision: 3.20
[   43.510301] hdd: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   43.582388] usbcore: registered new interface driver hiddev
[   43.711368] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
[   43.711452] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.1-2
[   43.732753] input: HP Multimedia Keyboard Hub as /class/input/input3
[   43.732817] input: USB HID v1.00 Keyboard [HP Multimedia Keyboard Hub] on usb-0000:00:10.2-2.1
[   43.732868] usbcore: registered new interface driver libusual
[   43.783103] input: HP Multimedia Keyboard Hub as /class/input/input4
[   43.783255] input,hiddev96: USB HID v1.00 Device [HP Multimedia Keyboard Hub] on usb-0000:00:10.2-2.1
[   43.783283] usbcore: registered new interface driver usbhid
[   43.783289] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   43.862346] Initializing USB Mass Storage driver...
[   43.880351] scsi2 : SCSI emulation for USB Mass Storage devices
[   43.916339] usb-storage: device found at 2
[   43.916346] usb-storage: waiting for device to settle before scanning
[   43.916414] scsi3 : SCSI emulation for USB Mass Storage devices
[   43.916618] usbcore: registered new interface driver usb-storage
[   43.916624] USB Mass Storage support registered.
[   43.916795] usb-storage: device found at 3
[   43.916798] usb-storage: waiting for device to settle before scanning
[   44.069699] usbcore: registered new interface driver xpad
[   44.069708] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   44.183337] PCI: Enabling device 0000:00:0e.0 (0004 -> 0005)
[   44.183359] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 17 (level, low) -> IRQ 20
[   45.231705] lp0: using parport0 (interrupt-driven).
[   45.318227] Adding 996020k swap on /dev/sda2.  Priority:-1 extents:1 across:996020k
[   45.499401] EXT3 FS on sda1, internal journal
[   46.159358] kjournald starting.  Commit interval 5 seconds
[   46.159750] EXT3 FS on sda3, internal journal
[   46.159757] EXT3-fs: mounted filesystem with ordered data mode.
[   47.361155] input: Power Button (FF) as /class/input/input5
[   47.367739] ACPI: Power Button (FF) [PWRF]
[   47.414840] input: Power Button (CM) as /class/input/input6
[   47.421523] ACPI: Power Button (CM) [PWRB]
[   47.510047] No dock devices found.
[   48.907582] usb-storage: device scan complete
[   48.907732] usb-storage: device scan complete
[   48.908495] scsi 3:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[   48.908541] scsi 2:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9601 PQ: 0 ANSI: 0
[   48.910938] sd 3:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[   48.912036] sd 3:0:0:0: [sdb] Write Protect is off
[   48.912044] sd 3:0:0:0: [sdb] Mode Sense: 6c 00 00 08
[   48.912047] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[   48.913774] sd 3:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[   48.914772] sd 3:0:0:0: [sdb] Write Protect is off
[   48.914776] sd 3:0:0:0: [sdb] Mode Sense: 6c 00 00 08
[   48.914778] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[   48.914785]  sdb: sdb1 sdb2
[   48.955912] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[   48.955987] sd 3:0:0:0: Attached scsi generic sg1 type 0
[   49.594314] scsi 2:0:0:1: Direct-Access     Generic  STORAGE DEVICE   9601 PQ: 0 ANSI: 0
[   49.598305] scsi 2:0:0:2: Direct-Access     Generic  STORAGE DEVICE   9601 PQ: 0 ANSI: 0
[   49.602302] scsi 2:0:0:3: Direct-Access     Generic  STORAGE DEVICE   9601 PQ: 0 ANSI: 0
[   49.616804] sd 2:0:0:0: [sdc] 8043840 512-byte hardware sectors (4118 MB)
[   49.617924] sd 2:0:0:0: [sdc] Write Protect is off
[   49.617928] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   49.617932] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   49.619919] sd 2:0:0:0: [sdc] 8043840 512-byte hardware sectors (4118 MB)
[   49.621168] sd 2:0:0:0: [sdc] Write Protect is off
[   49.621172] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   49.621174] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   49.621215]  sdc: sdc1
[   49.622148] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[   49.622234] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   49.626358] sd 2:0:0:1: [sdd] Attached SCSI removable disk
[   49.626431] sd 2:0:0:1: Attached scsi generic sg3 type 0
[   49.630350] sd 2:0:0:2: [sde] Attached SCSI removable disk
[   49.630425] sd 2:0:0:2: Attached scsi generic sg4 type 0
[   49.631876] sd 2:0:0:3: [sdf] Attached SCSI removable disk
[   49.631936] sd 2:0:0:3: Attached scsi generic sg5 type 0
[   50.247367] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   51.155653] [drm] Initialized drm 1.1.0 20060810
[   51.206111] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
[   51.210620] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   52.406762] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   52.407194] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   52.407482] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   52.493861] NET: Registered protocol family 10
[   52.494151] lo: Disabled Privacy Extensions
[   52.722253] [drm] Setting GART location based on new memory map
[   52.722272] [drm] Loading R200 Microcode
[   52.722316] [drm] writeback test succeeded in 1 usecs
[   52.751460] ppdev: user-space parallel port driver
[   53.300651] audit(1204220073.950:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4945 profile="/usr/sbin/cupsd"
[   53.435267] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   53.435276] apm: overridden by ACPI.
[   53.885729] Failure registering capabilities with primary security module.
[   54.102594] Bluetooth: Core ver 2.11
[   54.102788] NET: Registered protocol family 31
[   54.102791] Bluetooth: HCI device and connection manager initialized
[   54.102796] Bluetooth: HCI socket layer initialized
[   54.141545] Bluetooth: L2CAP ver 2.8
[   54.141553] Bluetooth: L2CAP socket layer initialized
[   54.205713] Bluetooth: RFCOMM socket layer initialized
[   54.205845] Bluetooth: RFCOMM TTY layer initialized
[   54.205848] Bluetooth: RFCOMM ver 1.8
[   59.515838] NET: Registered protocol family 17
[   75.148064] eth0: no IPv6 routers present
[ 4013.029585] usb 4-2: USB disconnect, address 3
[11182.279102] usb 4-2: new high speed USB device using ehci_hcd and address 6
[11182.412896] usb 4-2: configuration #1 chosen from 2 choices
[11182.413366] scsi4 : SCSI emulation for USB Mass Storage devices
[11182.413568] usb-storage: device found at 6
[11182.413571] usb-storage: waiting for device to settle before scanning
[11187.403715] usb-storage: device scan complete
[11187.404647] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[11187.407657] sd 4:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[11187.408518] sd 4:0:0:0: [sdb] Write Protect is off
[11187.408523] sd 4:0:0:0: [sdb] Mode Sense: 6c 00 00 08
[11187.408526] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[11187.410262] sd 4:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[11187.411261] sd 4:0:0:0: [sdb] Write Protect is off
[11187.411265] sd 4:0:0:0: [sdb] Mode Sense: 6c 00 00 08
[11187.411267] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[11187.411271]  sdb: sdb1 sdb2
[11187.443505] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[11187.443595] sd 4:0:0:0: Attached scsi generic sg1 type 0

Thank you for reading my query.

---

### Post by kpkeerthi on 2008-02-29
Can you post the output of ```
sudo fdisk -l
```?
(Thats probably easier to read than the complete dmesg)
Thanks.

---

### Post by t0dk0n on 2008-02-29
heh, sorry, I knew I forgot something important.

> Disk /dev/sda: 33.8 GB, 33820284928 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f800100

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         498     4000153+  83  Linux
/dev/sda2             499         622      996030   82  Linux swap / Solaris
/dev/sda3             623        4111    28025392+  83  Linux


Edit: I posted the dmesg for my Ultra ATA card and perhaps any other important hardware.

---

### Post by Yellow Pasque on 2008-02-29
Sounds like a BIOS limit.
You can get an add-in IDE card or look for a BIOS update for your motherboard.
[http://www.deinmeister.de/e_over8mb.htm](http://www.deinmeister.de/e_over8mb.htm)

What motherboard do you have? Try this:
```
sudo dmidecode -t bios
```

---

### Post by t0dk0n on 2008-02-29
Hmm, I haven't updated my bios ever since I bought it, but there's been a few times I thought about updating the bios, I know there's a few newer versions.

> # dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: Award Software, Inc.
	Version: ASUS A7V8X-X ACPI BIOS Revision 1003
	Release Date: 02/13/2003
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 256 kB
	Characteristics:
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/360 KB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		AGP is supported

Handle 0x0025, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

---

### Post by SmallFish on 2008-03-14
I have similar problem. It's maxtor 60 gig but now running at 30 gig. I have tried to reformat it with maxtor disk utility and partition magic but couldn't get it back. I talked to a friend used to work in hard drive industry and she told me it is possible that the "plate" already damaged what left is the working "plate" .  I assume plate means the platinum color disk in the hard drive.

---

### Post by imronak on 2008-03-14
You can use gparted for this. Its pretty good.

Use 
sudo apt-get install gparted

and then after the install

sudo gparted &.


This will launch a partion editor. In that select your hard drive on the right hand upper corner, like /dev/sda1

and then manage the partitions. If you dont know how to do that, paste watever partitions are there.

---

