---
title: "IT8212F ATA RAID Controller, 2 attached IDE disks not recognized"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by yammosk on 2007-05-03
Hi, the title basically saiys it all. I have an ITE made IT8212F RAID Controller that I use as an IDE Raid Controller (ATA 133); it is a PCI-Card, not an integrated chip.  2 120 Gig harddrives are attached and set up as RAID1. 

I also have another IDE harddrive that is not attached to the Raid Controller, but to the primary IDE controller of the motherboard instead. I boot from this harddrive (it's the MAXTOR harddrive). 

Ubuntu seems to recognize everything, including the two dics, but somehow seems to have a problem initializing them. Dmesg reads as follows (I **highlighted** what I think are the important messages): 

> sudo dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e8000 size: 0000000000018000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003feb0000 end: 000000003ffb0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003ffb0000 size: 0000000000010000 end: 000000003ffc0000 type: 3
[    0.000000] copy_e820_map() start: 000000003ffc0000 size: 0000000000030000 end: 000000003fff0000 type: 4
[    0.000000] copy_e820_map() start: 000000003fff0000 size: 0000000000010000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff7c0000 size: 0000000000840000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff7c0000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 262064) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262064
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262064
[    0.000000] On node 0 totalpages: 262064
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32433 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f9b10
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x03000620 MSFT 0x00000097) @ 0x3ffb0000
[    0.000000] ACPI: FADT (v001 A M I  OEMFACP  0x03000620 MSFT 0x00000097) @ 0x3ffb0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x03000620 MSFT 0x00000097) @ 0x3ffb0390
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x03000620 MSFT 0x00000097) @ 0x3ffc0040
[    0.000000] ACPI: DSDT (v001  939A8 939A8202 0x00000202 INTL 0x02002026) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf7c0000)
[    0.000000] Detected 1799.993 MHz processor.
[   28.496029] Built 1 zonelists.  Total pages: 260017
[   28.496033] Kernel command line: root=UUID=dcf8b479-8b61-4cef-8aff-c3a39b520162 ro quiet splash
[   28.496172] mapped APIC to ffffd000 (fee00000)
[   28.496175] mapped IOAPIC to ffffc000 (fec00000)
[   28.496178] Enabling fast FPU save and restore... done.
[   28.496180] Enabling unmasked SIMD FPU exception support... done.
[   28.496187] Initializing CPU#0
[   28.496225] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   28.496281] spurious 8259A interrupt: IRQ7.
[   28.497618] Console: colour VGA+ 80x25
[   28.497996] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   28.498404] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   28.518212] Memory: 1027808k/1048256k available (1992k kernel code, 19680k reserved, 893k data, 328k init, 130752k highmem)
[   28.518222] virtual kernel memory layout:
[   28.518223]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   28.518225]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   28.518226]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   28.518227]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   28.518229]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   28.518230]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   28.518231]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   28.518234] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   28.596075] Calibrating delay using timer specific routine.. 3601.89 BogoMIPS (lpj=7203781)
[   28.596116] Security Framework v1.0.0 initialized
[   28.596122] SELinux:  Disabled at boot.
[   28.596137] Mount-cache hash table entries: 512
[   28.596267] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   28.596275] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   28.596278] CPU: L2 Cache: 512K (64 bytes/line)
[   28.596281] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   28.596291] Compat vDSO mapped to ffffe000.
[   28.596295] Remapping vsyscall page to ffffe000
[   28.596305] Checking 'hlt' instruction... OK.
[   28.612187] SMP alternatives: switching to UP code
[   28.612395] Freeing SMP alternatives: 11k freed
[   28.612588] Early unpacking initramfs... done
[   28.929714] ACPI: Core revision 20060707
[   28.930167] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   28.931645] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 00
[   28.931660] Total of 1 processors activated (3601.89 BogoMIPS).
[   28.932155] ENABLING IO-APIC IRQs
[   28.932384] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   29.079364] Brought up 1 CPUs
[   29.079583] Booting paravirtualized kernel on bare hardware
[   29.079633] Time: 16:39:13  Date: 04/03/107
[   29.079659] NET: Registered protocol family 16
[   29.079733] EISA bus registered
[   29.079737] ACPI: bus type pci registered
[   29.080460] PCI: Using configuration type 1
[   29.080461] Setting up standard PCI resources
[   29.089829] ACPI: Interpreter enabled
[   29.089832] ACPI: Using IOAPIC for interrupt routing
[   29.090270] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   29.090274] PCI: Probing PCI hardware (bus 00)
[   29.090577] PCI quirk: region 0800-083f claimed by ali7101 ACPI
[   29.090857] Boot video device is 0000:01:00.0
[   29.091023] PCI: Transparent bridge - 0000:00:02.0
[   29.091042] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   29.100861] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   29.101106] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HTT_._PRT]
[   29.105717] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   29.105991] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   29.106263] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   29.106536] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[   29.106809] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[   29.107082] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   29.107371] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   29.107645] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[   29.107960] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   29.108022] Linux Plug and Play Support v0.97 (c) Adam Belay
[   29.108033] pnp: PnP ACPI init
[   29.110559] pnp: PnP ACPI: found 11 devices
[   29.110563] PnPBIOS: Disabled by ACPI PNP
[   29.110601] PCI: Using ACPI for IRQ routing
[   29.110604] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   29.110670] NET: Registered protocol family 8
[   29.110671] NET: Registered protocol family 20
[   29.111132] pnp: 00:09: ioport range 0x680-0x6ff has been reserved
[   29.111135] pnp: 00:09: ioport range 0x295-0x296 has been reserved
[   29.111367] PCI: Bridge: 0000:00:01.0
[   29.111370]   IO window: a000-cfff
[   29.111375]   MEM window: ff400000-ff4fffff
[   29.111378]   PREFETCH window: aeb00000-eeafffff
[   29.111383] PCI: Bridge: 0000:00:02.0
[   29.111386]   IO window: d000-dfff
[   29.111390]   MEM window: ff500000-ff5fffff
[   29.111394]   PREFETCH window: 50000000-500fffff
[   29.111404] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   29.111410] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   29.111434] NET: Registered protocol family 2
[   29.151292] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   29.151442] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   29.152269] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   29.152710] TCP: Hash tables configured (established 131072 bind 65536)
[   29.152713] TCP reno registered
[   29.163327] checking if image is initramfs... it is
[   29.788043] Freeing initrd memory: 6998k freed
[   29.788420] audit: initializing netlink socket (disabled)
[   29.788433] audit(1178210353.372:1): initialized
[   29.788488] highmem bounce pool size: 64 pages
[   29.788539] VFS: Disk quotas dquot_6.5.1
[   29.788554] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   29.788601] io scheduler noop registered
[   29.788603] io scheduler anticipatory registered
[   29.788605] io scheduler deadline registered
[   29.788612] io scheduler cfq registered (default)
[   29.854318] isapnp: Scanning for PnP cards...
[   30.207291] isapnp: No Plug & Play device found
[   30.228414] Real Time Clock Driver v1.12ac
[   30.228451] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.229017] mice: PS/2 mouse device common for all mice
[   30.229435] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   30.229657] input: Macintosh mouse button emulation as /class/input/input0
[   30.229682] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   30.229686] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   30.229833] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   30.232989] serio: i8042 KBD port at 0x60,0x64 irq 1
[   30.232994] serio: i8042 AUX port at 0x60,0x64 irq 12
[   30.233093] EISA: Probing bus 0 at eisa.0
[   30.233128] EISA: Detected 0 cards.
[   30.263159] TCP cubic registered
[   30.263167] NET: Registered protocol family 1
[   30.263185] Using IPI No-Shortcut mode
[   30.263236] ACPI: (supports S0 S1 S3 S4 S5)
[   30.263273]   Magic number: 7:48:691
[   30.263620] Freeing unused kernel memory: 328k freed
[   30.265511] Time: tsc clocksource has been installed.
[   30.277521] input: AT Translated Set 2 keyboard as /class/input/input1
[   31.515025] Capability LSM initialized
[   31.553105] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   32.081164] SCSI subsystem initialized
[   32.106832] libata version 2.20 loaded.
[   32.109244] ALI15X3: IDE controller at PCI slot 0000:00:0e.0
[   32.109257] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 19 (level, low) -> IRQ 16
[   32.109265] ALI15X3: chipset revision 199
[   32.109267] ALI15X3: not 100% native mode: will probe irqs later
[   32.109281]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[   32.109293] ALI15X3: simplex device: DMA forced
[   32.109295]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
[   32.109304] Probing IDE interface ide0...
[   32.124748] usbcore: registered new interface driver usbfs
[   32.124768] usbcore: registered new interface driver hub
[   32.124788] usbcore: registered new device driver usb
[   32.125422] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   32.192239] 8139too Fast Ethernet driver 0.9.28
[   32.438421] hda: Maxtor 33073H3, ATA DISK drive
[   32.893723] hdb: HL-DT-ST DVDRAM GSA-4165B, ATAPI CD/DVD-ROM drive
[   32.954410] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   32.986426] Probing IDE interface ide1...
[   33.555584] ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 20 (level, low) -> IRQ 17
[   33.555598] ohci_hcd 0000:00:0f.0: OHCI Host Controller
[   33.555831] ohci_hcd 0000:00:0f.0: new USB bus registered, assigned bus number 1
[   33.555851] ohci_hcd 0000:00:0f.0: irq 17, io mem 0xff6fd000
[   33.562217] hda: max request size: 128KiB
[   33.570324] hda: 60032448 sectors (30736 MB) w/2048KiB Cache, CHS=59556/16/63, UDMA(33)
[   33.570331] hda: cache flushes not supported
[   33.570366]  hda: hda1 hda2 hda3 <<6>usb usb1: configuration #1 chosen from 1 choice
[   33.614463] hub 1-0:1.0: USB hub found
[   33.614473] hub 1-0:1.0: 3 ports detected
[   33.617709]  hda5 >
[   33.629913] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   33.629921] Uniform CD-ROM driver Revision: 3.20
[   33.720289] ACPI: PCI Interrupt 0000:00:0f.1[B] -> GSI 21 (level, low) -> IRQ 18
[   33.720304] ohci_hcd 0000:00:0f.1: OHCI Host Controller
[   33.720323] ohci_hcd 0000:00:0f.1: new USB bus registered, assigned bus number 2
[   33.720342] ohci_hcd 0000:00:0f.1: irq 18, io mem 0xff6fc000
[   33.782156] usb usb2: configuration #1 chosen from 1 choice
[   33.782180] hub 2-0:1.0: USB hub found
[   33.782189] hub 2-0:1.0: 3 ports detected
[   33.888017] ACPI: PCI Interrupt 0000:00:0f.2[C] -> GSI 22 (level, low) -> IRQ 19
[   33.888031] ohci_hcd 0000:00:0f.2: OHCI Host Controller
[   33.888050] ohci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 3
[   33.888067] ohci_hcd 0000:00:0f.2: irq 19, io mem 0xff6fb000
[   33.949896] usb usb3: configuration #1 chosen from 1 choice
[   33.949925] hub 3-0:1.0: USB hub found
[   33.949934] hub 3-0:1.0: 3 ports detected
[   34.016891] Attempting manual resume
[   34.016895] swsusp: Resume From Partition 3:5
[   34.016897] PM: Checking swsusp image.
[   34.019725] usb 1-2: new full speed USB device using ohci_hcd and address 2
[   34.041139] PM: Resume from disk failed.
[   34.055848] ACPI: PCI Interrupt 0000:00:0f.3[D] -> GSI 23 (level, low) -> IRQ 20
[   34.055859] ehci_hcd 0000:00:0f.3: EHCI Host Controller
[   34.055880] ehci_hcd 0000:00:0f.3: new USB bus registered, assigned bus number 4
[   34.055905] ehci_hcd 0000:00:0f.3: debug port 1
[   34.083644] ehci_hcd 0000:00:0f.3: irq 20, io mem 0xff6fe800
[   34.083651] ehci_hcd 0000:00:0f.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.083744] usb usb4: configuration #1 chosen from 1 choice
[   34.083768] hub 4-0:1.0: USB hub found
[   34.083777] hub 4-0:1.0: 8 ports detected
[   34.107916] kjournald starting.  Commit interval 5 seconds
[   34.107927] EXT3-fs: mounted filesystem with ordered data mode.
[   34.191637] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 18 (level, low) -> IRQ 21
[   34.191945] eth0: RealTek RTL8139 at 0xf88dac00, 00:02:44:0d:4e:9c, IRQ 21
[   34.191948] eth0:  Identified 8139 chip type 'RTL-8139C'
[   34.194123] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
**[   34.194205] pata_it821x: controller in smart mode.**
[   34.194219] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 19 (level, low) -> IRQ 16
[   34.194232] PCI: Setting latency timer of device 0000:02:07.0 to 64
[B][   34.194278] ata1: PATA max MWDMA2 cmd 0x0001dc00 ctl 0x0001d482 bmdma 0x0001d000 irq 16
[   34.194302] ata2: PATA max MWDMA2 cmd 0x0001d400 ctl 0x0001d082 bmdma 0x0001d008 irq 16[/B]
**[   34.194317] scsi0 : pata_it821x**
[   34.758577] usb 1-2: new full speed USB device using ohci_hcd and address 3
[   34.963321] usb 1-2: configuration #1 chosen from 1 choice
[   34.966262] hub 1-2:1.0: USB hub found
[   34.969238] hub 1-2:1.0: 4 ports detected
[   35.327685] usb 1-2.1: new full speed USB device using ohci_hcd and address 4
[B][   35.381787] ata1.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   35.470532] usb 1-2.1: configuration #1 chosen from 1 choice
[   37.079170] ata1.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   37.079176] ata1.00: limiting speed to UDMA7:PIO5
[   38.776552] ata1.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   40.465828] scsi1 : pata_it821x[/B]
[   47.414246] eth0: link down
[   48.802292] NET: Registered protocol family 17
[   48.830341] ali15x3_smbus 0000:00:03.1: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   48.830346] ali15x3_smbus 0000:00:03.1: ALI15X3 not detected, module not inserted.
[   48.965842] ali1535_smbus 0000:00:03.1: ALI1535_smb region uninitialized - upgrade BIOS?
[   48.965847] ali1535_smbus 0000:00:03.1: ALI1535 not detected, module not inserted.
[   48.997686] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   49.002116] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   49.114862] uli526x: ULi M5261/M5263 net driver, version 0.9.3 (2005-7-29)
[   49.114913] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 17 (level, low) -> IRQ 22
[   49.135387] eth1: ULi M5263 at pci0000:00:0d.0, 00:13:8f:3f:9b:27, irq 22.
[   49.290702] Linux agpgart interface v0.102 (c) Dave Jones
[   49.292474] agpgart: Detected AGP bridge 0
[   49.292489] Setting up ULi AGP.
[   49.296715] agpgart: AGP aperture is 128M @ 0xf0000000
[   49.317977] ali1563: SMBus control = 0403
[   49.318021] ali1563_probe: Returning 0
[   49.968402] input: PC Speaker as /class/input/input2
[   50.263923] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   50.282961] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 18 (level, low) -> IRQ 21
[   50.323616] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0904
[   50.323631] usbcore: registered new interface driver usblp
[   50.323634] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   51.305072] AC'97 1 does not respond - RESET
[   51.305543] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   51.305548] Unable to initialize codec #1
[   51.364978] intel8x0_measure_ac97_clock: measured 59063 usecs
[   51.364980] intel8x0: clocking to 48000
[   51.556378] fuse init (API version 7.8)
[   51.627926] lp: driver loaded but no devices found
[   51.660196] Adding 417648k swap on /dev/disk/by-uuid/db3539e9-6d30-478b-b07b-172e63222493.  Priority:-1 extents:1 across:417648k
[   51.799554] EXT3 FS on hda2, internal journal
[   53.046700] uli526x: eth1 NIC Link is Up 100 Mbps Full duplex
[   56.078402] No dock devices found.
[   56.157193] ibm_acpi: ec object not found
[   56.200455] Using specific hotkey driver
[   56.292372] input: Power Button (FF) as /class/input/input4
[   56.296569] ACPI: Power Button (FF) [PWRF]
[   56.326655] input: Power Button (CM) as /class/input/input5
[   56.330846] ACPI: Power Button (CM) [PWRB]
[   56.430988] pcc_acpi: loading...
[   56.691694] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
[   56.697273] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   59.742161] NET: Registered protocol family 10
[   59.742252] lo: Disabled Privacy Extensions
[   59.742303] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   61.678452] [drm] Initialized drm 1.1.0 20060810
[   61.693436] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 23
[   61.696223] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   62.308157] ppdev: user-space parallel port driver
[   63.450114] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   63.450296] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[   63.450318] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[   63.761565] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   63.761570] apm: overridden by ACPI.
[   63.961756] Bluetooth: Core ver 2.11
[   63.961806] NET: Registered protocol family 31
[   63.961808] Bluetooth: HCI device and connection manager initialized
[   63.961812] Bluetooth: HCI socket layer initialized
[   63.994959] Bluetooth: L2CAP ver 2.8
[   63.994963] Bluetooth: L2CAP socket layer initialized
[   64.135497] Bluetooth: RFCOMM socket layer initialized
[   64.135510] Bluetooth: RFCOMM TTY layer initialized
[   64.135512] Bluetooth: RFCOMM ver 1.8
[   75.124310] eth1: no IPv6 routers present
[   79.808554] [drm] Setting GART location based on new memory map
[   79.808564] [drm] Loading R300 Microcode
[   79.808680] [drm] writeback test succeeded in 1 usecs


Unfortunately, I do not know how to proceed from this point on. As I am currently in the transitional phase from Windows to Ubuntu, I need to be able to access my RAID1-hdds. 

If anyone needs any more information, I will gladly give it. ANY suggestion is greatly appreciated. 

Thank you

Yammosk

---

### Post by yammosk on 2007-05-05
OK, it's getting interesting. I just booted with a Puppy-Linux CD (V. 2.13) and it loaded and configured my Raid PCI card without any problems. Here's the readout from Pupscan: 

> DESCRIPTION: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (PCI version seems to be IT8212, embedded seems to be ITE8212)
VENDOR: 1283  DEVICE: 8212  KERNEL MODULE: unknown

I don't know if that helps, but I'm amazed that Puppy could correctly load something that Ubuntu could not. After all, Puppy is maintained by only a handful of people. 

I would really appreciate any sort of reply at this point, as I'm starting to wonder whether I reported my problem in the correct place. If this is not the right place, I would really be thankful if someone told me so. 

Thank you 

Yammosk

---

### Post by jocko on 2007-05-08
> **yammosk said:**
> OK, it's getting interesting. I just booted with a Puppy-Linux CD (V. 2.13) and it loaded and configured my Raid PCI card without any problems. Here's the readout from Pupscan: 



I don't know if that helps, but I'm amazed that Puppy could correctly load something that Ubuntu could not. After all, Puppy is maintained by only a handful of people. 

I would really appreciate any sort of reply at this point, as I'm starting to wonder whether I reported my problem in the correct place. If this is not the right place, I would really be thankful if someone told me so. 

Thank you 

Yammosk

The problem is caused by a change in the driver in the feisty kernel.
Older kernels used an ide driver module called it821x, but now it uses a pata module named pata_it821x.
I have a built in ite8212 controller that has worked fine since dapper, but now it's totally useless.
It is detected ok, but whenever anything tries to read or write from/to the disk the entire system becomes extremely slow (without increased processor or memory usage...).
The only working solution I have found was to compile a custom kernel and made sure to include the old it821x module.

---

### Post by yammosk on 2007-05-09
Thank you very much for your reply, Jocko. Is this a bug or a feature? Is it possible that this might be fixed (maybe in the Gutsy Gibbon)? Maybe all that needs to be done is for someone to file a proper bug report...(I'd happily do that)...

Greetz

Yammosk

PS: I've never compiled a kernel. Should I - as a Linux noob - try this or is that something best left to the pros?

---

### Post by goodwill on 2007-05-20
****... I think I come across the same issue as yours. It just fails to mount at all!!! I think it is telling me to give up Ubuntu.
So far I have not good experience on Ubuntu's compatibility- I wonder if its linux kernel or something else... I just thinking to buy a Mac as I feel the Mac OS build are far more consistent and I can do mostly what I want to do on Linux similarly on Mac...

---

### Post by Afflictedmonkey on 2007-06-25
Yep, it seems that the IT8212 driver was taken out of the kernel for Feisty. Previously it worked fine in Edgy.

Is there some way to petition the pros to update the kernel. Compiling the kernel is not exactly easy...

---

### Post by Afflictedmonkey on 2007-06-25
I downloaded the latest kernel-source and it seems to be correctly configured for IT8212. 

Not sure what is going on then...

I'm trying to recompile the kernel and see if that makes a difference...

---

### Post by Horatio on 2007-07-19
I'm trying Kubuntu after I have been using Gentoo for years. I wanted some thing more easy to fix.

The kernel is 2.6.20-16-generic, and the driver pata_it821x is shown in the output.

Is there a standard amd64 linux kernel with the it821x module available in any repository, or how does this new module work

p.s. All worked well with Gentoo's kernel, and I was thinking I could use that one.

---

### Post by katanacb on 2007-07-24
I've been fighting this very problem for a few weeks now with Feisty, and one night decided to sit down and see if I couldn't get it solved.  I like Ubuntu, and I figured it was just time to roll up the sleeves and geek out for a bit (and I've been using Linux WAY WAY too long to let it get the best of me!).  In my case,  I have an ITE8212F PCI RAID card running on a 64-bit machine, and things were working fine with every distribution until I tried to use Feisty (In fairness, I tried Fedora 7 and it has the same problem too).  Actually, things were fine until the last Feisty beta, and that's when everything broke on me.  But since my RAID drives just have MP3's and video files, going without for a few weeks wasn't a big deal.

Biut I digress.

The short answer is yes, I did get the RAID card working under Feisty, but it wasn't pretty.  I'll list the high-level steps below, but if you aren't comfy recompiling the kernel then I'd stay on Edgy or Dapper for now.  The problem is that the IDE interface seems to be moving to a new kernel module architecture and structure, whereas all the drives that we normally see as IDE drives (/dev/hd*) are now listed as SCSI drives (/dev/sd*).  In this case, the old it821x module is being replaced with the pata_it821x module and the libata interface.  I'm really pretty surprised that the major distros made this switch so early, because in the kernel it's very clearly marked as EXPERIMENTAL, and it quite obviously is broken in the Feisty kernel.  I'm thinking several people got hosed because the distros jumped the gun on making the switch.

To get things going, you'll need to :

* download the kernel source tree
* alter the kernel config to compile the IT821x module and NOT the pata_it821x one
* re-compile your kernel
* install your new custom kernel
* reboot and JOY!


Interestingly enough (and this is what I ultimately did), you can also re-compile the kernel, but instead of installing it, you can just copy the it821x module to the kernel structure in /lib/modules.  Then, you'll want to  delete the pata_it821x module from there so Feisty doesn't ever try to load it at run-time.  But this doesn't solve everything, because the driver for the module is in the initrd and is loaded at boot anyways.  So, to solve that, you'll have to edit the initrd (un-gzip it, cpio, etc), delete the pata_it821x module from the tree  ... re-cpio and compress the initrd, copy it back to /boot, reboot and viola!  (not for the faint of heart here).  MAKE SURE YOU BACKUP YOUR INITRD BEFORE YOU DO THIS!!!!!!

I downloaded the latest beta of gutsy to see if the libata problem has been fixed; there were several bug reports about the it821x kernel module being hosed in the libata interface and it is supposed to be fixed in 2.6.23 I think.  So I'm gonna try it out and see.

Good luck!

---

### Post by Brucmack on 2007-07-30
Hi!

katanacb, can you provide any details about what config options need to be changed? I've found the guide for rebuilding the kernel, but I'm a linux noob so I'm afraid I need some more details :)

Thanks!
Bruce

---

### Post by Brucmack on 2007-08-01
Ok, maybe someone else can help me...

I got the kernel and have tried to modify the config files by setting:

CONFIG_BLK_DEV_IT821X=m

and commenting out:

CONFIG_PATA_IT821X

I then regenerated the configs using the command on the kernel recompile guide ([https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild))

It seems to compile everything, but then I get the following error:

Checking module listings...
Modules have gone missing:
pata_it821x

Will not continue!
make: *** [build] Error 1

So it looks like it's still trying to build with the old package. What else do I have to change?

Thanks,
Bruce

---

### Post by jocko on 2007-08-06
> **Brucmack said:**
> I got the kernel and have tried to modify the config files by setting:

CONFIG_BLK_DEV_IT821X=m

and commenting out:

CONFIG_PATA_IT821X

I then regenerated the configs using the command on the kernel recompile guide ([https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild))

This is what worked for me (but now I have upgraded to gutsy where the pata driver seems to work fine):
I installed the kernel source (sudo apt-get install linux-source)
and followed the instructions in [the master kernel thread]("http://ubuntuforums.org/showpost.php?p=1835811&postcount=1") to build it.
During the configuration (xconfig) I made sure to say "M" (module) to "Device drivers"-->"ATA/ATAPI/MFM/RLL"-->..-->"IT821X IDE Support" and "N" (No) to "Serial ATA and Parallell ATA drivers"-->"IT8211/2 Pata support"
(Im sure this results in the same changes in the config file as you did, but perhaps it also changes something else?)
I did some more changes, like removing a few modules I know I don't need, but nothing that should affect ata/pata.

---

### Post by bond711 on 2007-08-23
anychange on this?
like a simpler fix?

---

### Post by jocko on 2007-08-28
> **bond711 said:**
> anychange on this?
like a simpler fix?
No change as far as I know. There are two ways to fix it: Either compile your own kernel (see my post above) or upgrade to gutsy (but that's still under development, so some things will probably break now and then...).

Compiling the kernel isn't that hard if you just follow the instructions in the guide I linked to above + make the two changes (above) during the configuration.

---

### Post by macjunkie999 on 2007-10-13
Hi I recently acquired a semi decent peecee that I would like to turn into some sort of linux station (maybe various different networking protocols such as samba netbios ect) . I have some experience with linux via openwrt and xwrt (wireless router embedded linux). The peecee im using is an earlier intel mobo (supports p2 and p3 slot1) , sadly the onboard bios even with the latest bios cannot handle a 160 gb hd (only spare drive I have). I am using an ite8212f raid controller with very little success. I was able to install the os on the drive (took an insane amount of time). Currently I have the boot loader files on a 2.5 gb hd that is connected to the onboard ide controller. The computer begins to boot, (ubuntu boot screen) but simply hangs after a few accesses to the 2.5 gb hd. From what I have read I need to compile the driver and a custom kernel, but how do I do this when I dont even have a bootable computer? Is it possible to compile using the livecd, and if so how? All of the linux distributions I have tried (ubuntu (partitioned and formated the os installed) and debian) fail to access the hd correctly EXCEPT for gentoo (just barely enough to partition and format the drive.) Itd just use gentoo but its a pain to install, pretty much I want a quick easy install that dosnt take up allot of hd space and allows me to customize whats installed later. HEH kinda like how openwrt is now with the ipkg system. I would REALLY REALLY preffer NOT to do a bunch of source code compiling, I cant stand the vauge error messages such as "missing separator on line _" or the incredibly vague error "error on line _"

---

### Post by yammosk on 2007-10-22
> **jocko said:**
> No change as far as I know. There are two ways to fix it: Either compile your own kernel (see my post above) or upgrade to gutsy (but that's still under development, so some things will probably break now and then...).

Compiling the kernel isn't that hard if you just follow the instructions in the guide I linked to above + make the two changes (above) during the configuration.

I just booted of the final Gutsy Gibbon live CD and my IT8212F ATA Raid controller (pci card) still is not working. 

lscpi -vnn offers the following:
02:07.0 RAID bus controller [0104]: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller [1283:8212] (rev 13)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        I/O ports at dc00 [size=8]
        I/O ports at d480 [size=4]
        I/O ports at d400 [size=8]
        I/O ports at d080 [size=4]
        I/O ports at d000 [size=16]
        Expansion ROM at 50020000 [disabled] [size=128K]
        Capabilities: <access denied



dmesg offers the following (excerpt):

[   42.125077] eth0: RealTek RTL8139 at 0xf883ec00, 00:02:44:0d:4e:9c, IRQ 19
[   42.125080] eth0:  Identified 8139 chip type 'RTL-8139C'
[   42.125832] pata_it821x: controller in smart mode.
[   42.125844] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 19 (level, low) -> IRQ 18
[   42.125881] PCI: Setting latency timer of device 0000:02:07.0 to 64
[   42.125972] scsi0 : pata_it821x
[   42.126160] scsi1 : pata_it821x
[   42.126308] ata1: PATA max MWDMA2 cmd 0x0001dc00 ctl 0x0001d482 bmdma 0x0001d000 irq 18
[   42.126312] ata2: PATA max MWDMA2 cmd 0x0001d400 ctl 0x0001d082 bmdma 0x0001d008 irq 18
[   42.127152] ACPI: PCI Interrupt 0000:00:0f.1[B] -> GSI 21 (level, low) -> IRQ 20
[   42.127166] ohci_hcd 0000:00:0f.1: OHCI Host Controller
[   42.127388] ohci_hcd 0000:00:0f.1: new USB bus registered, assigned bus number 3
[   42.127405] ohci_hcd 0000:00:0f.1: irq 20, io mem 0xff6fc000
[   42.134018] hda: max request size: 128KiB
[   42.143566] hda: 60032448 sectors (30736 MB) w/2048KiB Cache, CHS=59556/16/63, UDMA(100)
[   42.143574] hda: cache flushes not supported
[   42.143625]  hda: hda1 hda2 hda3 <<6>usb usb3: configuration #1 chosen from 1 choice
[   42.184786] hub 3-0:1.0: USB hub found
[   42.184797] hub 3-0:1.0: 3 ports detected
[   42.185377]  hda5 >
[   42.230492] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   42.230501] Uniform CD-ROM driver Revision: 3.20
[   42.286618] ACPI: PCI Interrupt 0000:00:0f.2[C] -> GSI 22 (level, low) -> IRQ 21
[   42.286633] ohci_hcd 0000:00:0f.2: OHCI Host Controller
[   42.286821] ohci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 4
[   42.286838] ohci_hcd 0000:00:0f.2: irq 21, io mem 0xff6fb000
[   42.344372] usb usb4: configuration #1 chosen from 1 choice
[   42.344578] hub 4-0:1.0: USB hub found
[   42.344589] hub 4-0:1.0: 3 ports detected
[   43.312565] ata1.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   43.829408] kjournald starting.  Commit interval 5 seconds
[   43.829420] EXT3-fs: mounted filesystem with ordered data mode.
[   44.177991] ISO 9660 Extensions: Microsoft Joliet Level 3
[   44.216659] ISO 9660 Extensions: RRIP_1991A
[   44.524310] Registering unionfs 1.4
[   44.524314] unionfs: debugging is not enabled
[   44.533334] loop: module loaded
[   45.001803] ata1.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   45.001810] ata1.00: limiting speed to UDMA7:PIO5
[   46.691034] ata1.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)

It seems that the controller is recognized, but somehow not initialized. Unfortunately, I still do not know the exact cause of failure nor any cure for the problem. Does the Gutsy Gibbon Alternate CD have different drivers (maybe the old it821x driver that is supposed to be working)? If anyone knows anything, any contribution would greatly be appreciated. 

Greetz

Yammosk

---

### Post by that guy on 2007-10-24
Gutsy is not recognizing this card for me either.  I can set the RAID up in the card's BIOS and the computer's BIOS also recognizes it, but Ubuntu doesn't seem to want to.  I would assume that if it could, the Live CD would mount it, but maybe I'm wrong.

Anyway a little searching turned up the following link:

[http://www.ite.com.tw/software_download/software_download2.asp#IT8212%20ATA133%20Controller]("http://www.ite.com.tw/software_download/software_download2.asp#IT8212%20ATA133%20Controller")

The driver from ite is here, but they only list Mandrake, Red Hat, Suse and Turbo Linux.  It says "others version and kernel 2.6.x please compile source code with your own kernel"

I don't know Jack about doing that, but they have the binary and the source code for download, so maybe somebody could fire that up into something useful for Ubuntu.  It would make a lot of people happy. :)

---

### Post by watagan on 2007-10-25
I run openSUSE but this may work for you:

[http://forums.suselinuxsupport.de/index.php?showtopic=62035&st=0&gopid=251601&#entry251601](http://forums.suselinuxsupport.de/index.php?showtopic=62035&st=0&gopid=251601&#entry251601)

Is working for me so far, but on a different system so no guarantees.

Good luck...

---

### Post by chrislau on 2007-10-25
I spent many time on that problem. There is a bug in the driver pata_it821x and in the old driver it821x.

If you recompile the old driver (it821x) you will probably face problem due to slow bit/rate on your drive ( about 3 Mbyte/s ) (I face it on openSUSE 10.3)

After spending much time on Internet for a solution, I found the following solution in the kernel list : 
- delete the hard raid array
- boot using the parameter noraid=1 for the module pata_it821x
- create a soft raid array.

If you cannot afford loosing your hard raid array, you need to recompile the old IT821x driver and appliy the patch.

Here's the thread where you'll find the information : [http://lkml.org/lkml/2007/5/15/107]("http://lkml.org/lkml/2007/5/15/107")

----
Wish it helps.

---

### Post by watagan on 2007-10-25
I have not recompiled the it821x driver, but disabled the pata_it821x and 'replaced' it with the it821x driver in the latest openSUSE kernel update.

Transfer rate is not a problem here:

hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   484 MB in  2.00 seconds = 241.50 MB/sec
 Timing buffered disk reads:  184 MB in  3.01 seconds =  61.20 MB/sec

hdparm -tT /dev/hdb

/dev/hdb:
 Timing cached reads:   498 MB in  2.00 seconds = 248.66 MB/sec
 Timing buffered disk reads:  184 MB in  3.03 seconds =  60.78 MB/sec

Regards...

---

### Post by chrislau on 2007-10-25
Watagan,

Please, correct me if I am wrong, but I think you have not configured any raid Array on your device, that's why you have good bitrate. In that case, you don't need to remove the new pata_it821x driver and replace it twith the old it821x driver, you just need to add the parameter noraid=1 when you load the new pata_it821x driver. (add pata_it821x.noraid=1 on the kernel parameter line in grub)
 
The problem is, if you configure a raid array, for example I have four 160 GBytes disks I put in one big raid 0 array of about 600 GBytes. I had error message when I tried to activate the DMA transfert, and I had a very bitrate for write access (3 Mbytes/s), as well under Ubuntu 7.10 as under openSUSE 10.3.

Another problem with Ubuntu 7.10 is that the old module it821x is not delivered with the kernel,  that's why it is necessary to recompile the kernel if we want that module. I suppose the Ubuntu kernel development team found the experimental module pata_it821x was at least as good, or as bad (!), as the old module, so they prefered to keep the new one.

Regards

---

### Post by watagan on 2007-10-26
Correct, no raid is configured, just using  the it821x for extra drive slots (see my original openSUSE post). However noraid=1 does not do the job either when pata_it821x activated. The drives attached are not activated. Ubuntu may be different but this is my experience with openSUSE (confirmed again just now).

If it821x is not visible with lsmod then looks like your only option is to recompile the kernel with it821x activated and either remove the pata driver at the same time or do a modprobe -r on it early in the boot process. But I guess that really returns you to the slow transfer rate problem you have with it821x.

Sorry I don't know anything about Ubuntu, but seems strange they would ditch it821x and replace it with an experimental pata driver.

Regards...

---

### Post by pefdus on 2007-12-23
I am running two PCI it821x cards and found the solution as follows (and some corrections on previous posts).

the kernel option pata_it821x.noraid=1 when supplied in grub menu.lst such as 

     [FONT="Courier New"]kernel /boot/vmlinuz-2.6.22-14-server root=/dev/md0 ro quiet splash **pata_it821x.noraid=1**[/FONT]

is only relevant if the pata_it821x module is compiled into the kernel, which is not the default for Ubuntu.

The following is my setup
2 x 40G drives on the Motherboard IDE bus
6 x IDE drives on 2 PCI IT 8212 RAID cards. None of these are running hardware RAID from the card. I am using the cards as IDE buses only.

The fix is .. 

add the following to [FONT="Courier New"]/etc/modprobe.d/options[/FONT]
[FONT="Courier New"]
options pata_it821x noraid=1[/FONT]

Now, once you have that, recreate the initramfs so that the "setting" is available on the initial boot (before the drives are booted and mounted).
[FONT="Courier New"]
update-initramfs -k all -c -t -v[/FONT]

Reboot and you should now see all the drives as /dev/sd devices.

reply if you need help, I have spent 3 days working this out.

Ramon Buckland

---

### Post by joni8135 on 2007-12-25
> **katanacb said:**
> 

I downloaded the latest beta of gutsy to see if the libata problem has been fixed; there were several bug reports about the it821x kernel module being hosed in the libata interface and it is supposed to be fixed in 2.6.23 I think.  So I'm gonna try it out and see.

Good luck!

I'm not at home now, but i wonder 3 thing.
1. Have ubuntu get the stable kernel: 2.6.23.12  [http://www.kernel.org/](http://www.kernel.org/)

2. Does pata_it821x working with it?

3. If 1 is false but 2 true, is it possible to use 2.6.23.12 in gutsy and how-to do that?

/joni

---

### Post by fowie on 2007-12-27
Ok, I followed katancb's advice and recompiled the kernel--easier than I thought, I might add.  

I had a problem not being able to mount them but that turned out to be simply because I had dmraid and mdadm installed.  Once those were removed I could mount the drives, 
fdisk shows
```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b151b14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3037    24393678+   7  HPFS/NTFS
/dev/sda2            3038        4756    13807867+  83  Linux
/dev/sda3            4757        4865      875542+   5  Extended
/dev/sda5            4757        4865      875511   82  Linux swap / Solaris

Disk /dev/hda: 160.0 GB, 160052674560 bytes
255 heads, 63 sectors/track, 19458 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007997c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19458   156296353+   b  W95 FAT32

```

However, after trying to copy a lot of files suddenly the drives will simply stop responding.  In the middle of a copy I'll get
```

cp: Input/Output Error

```
and suddenly I can't do anything with the drives until I reboot.  Any ideas?

---

### Post by fowie on 2007-12-29
Found a quick workaround--the RAID controller doesn't seem to handle Raid 0 (striping) very well, so I switched the RAID to do JBOD instead and it works fine (granted, not as nice as striped, but at least it's working)

--EDIT--
Hmm, maybe not so great.  It worked for a while but trying to do something like rip a DVD to the hard drives makes it crash back into the "input/output error" mode again.  ARGH!  Any ideas?  I can get a "linux driver" from the ITE website but I don't know how to compile it into the kernel?

---

### Post by andersja on 2008-01-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182949](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182949) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've posted Launchpad bug 182949 regarding my it8212 experiences. Please feel free to contribute your logs, fixes etc to that thread so this bug can be fixed before Heron is published as an LTS release!

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182949](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182949)

Related bug reports include:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/106931/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/106931/)
[http://bugzilla.kernel.org/show_bug.cgi?id=9587](http://bugzilla.kernel.org/show_bug.cgi?id=9587)

Thanks!

---

### Post by andersja on 2008-01-25
> **pefdus said:**
> The fix is .. 

add the following to [FONT="Courier New"]/etc/modprobe.d/options[/FONT]
[FONT="Courier New"]
options pata_it821x noraid=1[/FONT]

Now, once you have that, recreate the initramfs so that the "setting" is available on the initial boot (before the drives are booted and mounted).
[FONT="Courier New"]
update-initramfs -k all -c -t -v[/FONT]

Reboot and you should now see all the drives as /dev/sd devices.

Thanks for sharing, Ramon. 
I'm downloading the latest hardy heron kernel now (2.6.24-5.9) and will test your 'hack' & report back here.

---

### Post by andersja on 2008-01-25
Yep, I can confirm that this worked. Thank you Ramon/pefdus!
 :KS :KS :KS

---

### Post by pefdus on 2008-02-24
I should point out, once you have the drives showing up as sd's go through the steps to setup your RAID in linux (software raid) using all the mdadm stuff.

This is how I run my kit.

r.

---

### Post by ShultZ666 on 2008-03-16
my little hack to get RAID0 array on IT8212F working with pata_it821x driver on 2.6.24.3

```

pata_it821x: controller in smart mode.
ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 20 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:02:0c.0 to 64
scsi0 : pata_it821x
scsi1 : pata_it821x
ata1: PATA max MWDMA2 cmd 0xdf68 ctl 0xdf7c bmdma 0xdf40 irq 18
ata2: PATA max MWDMA2 cmd 0xdf60 ctl 0xdf5c bmdma 0xdf48 irq 18
it821x: RAID volume: performing ID fixups...
ata1.00: ATA-4: Integrated Technology Express Inc, , max MWDMA2
ata1.00: 312598720 sectors, multi 0: LBA48 
ata1.00: Drive reports diagnostics failure. This may indicate a drive
ata1.00: fault or invalid emulation. Contact drive vendor for information.
IT821x Bootable RAID0 volume(8K stripe).
ata1.00: configured for DMA
scsi 0:0:0:0: Direct-Access     ATA      Integrated Techn n/a  PQ: 0 ANSI: 5
sd 0:0:0:0: [sda] 312598720 512-byte hardware sectors (160051 MB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
sd 0:0:0:0: [sda] 312598720 512-byte hardware sectors (160051 MB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
 sda: sda1 sda2 sda3 sda4
sd 0:0:0:0: [sda] Attached SCSI disk
sd 0:0:0:0: Attached scsi generic sg0 type 0
```

```

hdparm -t /dev/sda

/dev/sda:
 Timing buffered disk reads:  166 MB in  3.01 seconds =  55.23 MB/sec
```

also patch to enable DMA in old it821x driver for 2.6.24.3 attached:

```

root@satan:/usr/src# hdparm -t /dev/hda

/dev/hda:
 Timing buffered disk reads:  180 MB in  3.02 seconds =  59.69 MB/sec
```

---

