---
title: "dual touchpad/point-stick on Toshiba Tecra M2"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by TimTams on 2007-06-24
I've just installed feisty on a toshi tecra m2
neither the built-in touchpad or point-stick work
everything ive read say i should expect them to function out of the as a standard ps/2 device (albeit without scroll or tap functionality on the pad)

they work fine under windoze

external usb mouse works fine

tried disabling acpi (said to often cause probs on toshi's)
tried moving the mouse during boot (some forum post seemed to think it could help someone else)

any ideas???

here's my dmsg, if it helps (the few ps/2 & i8042 refs are around 8.8) :

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 000000000000ee00 end: 00000000000eee00 type: 2
[    0.000000] copy_e820_map() start: 00000000000eee00 size: 0000000000000200 end: 00000000000ef000 type: 4
[    0.000000] copy_e820_map() start: 00000000000ef000 size: 0000000000011000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fec0000 end: 000000001ffc0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001ffc0000 size: 0000000000010000 end: 000000001ffd0000 type: 2
[    0.000000] copy_e820_map() start: 000000001ffd0000 size: 0000000000010000 end: 000000001ffe0000 type: 3
[    0.000000] copy_e820_map() start: 000000001ffe0000 size: 0000000000020000 end: 0000000020000000 type: 2
[    0.000000] copy_e820_map() start: 00000000feda0000 size: 0000000000020000 end: 00000000fedc0000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000100000 end: 00000000ffc00000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffe80000 size: 0000000000180000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
[    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000001ffc0000 - 000000001ffd0000 (reserved)
[    0.000000]  BIOS-e820: 000000001ffd0000 - 000000001ffe0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffe0000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131008) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131008
[    0.000000]   HighMem    131008 ->   131008
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131008
[    0.000000] On node 0 totalpages: 131008
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125921 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 TOSHIB                                ) @ 0x000f01b0
[    0.000000] ACPI: RSDT (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x1ffd0000
[    0.000000] ACPI: FADT (v002 TOSHIB 750      0x20030101 TASM 0x04010000) @ 0x1ffd005c
[    0.000000] ACPI: SSDT (v001 TOSHIB A000B    0x20031217 MSFT 0x0100000e) @ 0x1ffd6af2
[    0.000000] ACPI: DBGP (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x1ffd00e0
[    0.000000] ACPI: DSDT (v001 TOSHIB A000B    0x20031217 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0xd808
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:deda0000)
[    0.000000] Detected 1995.091 MHz processor.
[    7.406499] Built 1 zonelists.  Total pages: 129985
[    7.406503] Kernel command line: root=UUID=896241c0-7a3c-455e-bb8e-2c904744b6d4 ro quiet splash
[    7.406650] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    7.406658] mapped APIC to ffffd000 (0140b000)
[    7.406662] Enabling fast FPU save and restore... done.
[    7.406664] Enabling unmasked SIMD FPU exception support... done.
[    7.406676] Initializing CPU#0
[    7.406743] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    7.408729] Console: colour VGA+ 80x25
[    7.409025] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.409275] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    7.423690] Memory: 508472k/524032k available (1992k kernel code, 14992k reserved, 900k data, 328k init, 0k highmem)
[    7.423699] virtual kernel memory layout:
[    7.423700]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    7.423701]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.423703]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[    7.423704]     lowmem  : 0xc0000000 - 0xdffc0000   ( 511 MB)
[    7.423705]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    7.423706]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[    7.423707]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[    7.423710] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.502701] Calibrating delay using timer specific routine.. 3992.68 BogoMIPS (lpj=7985369)
[    7.502738] Security Framework v1.0.0 initialized
[    7.502747] SELinux:  Disabled at boot.
[    7.502762] Mount-cache hash table entries: 512
[    7.502888] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[    7.502899] CPU: L1 I cache: 32K, L1 D cache: 32K
[    7.502901] CPU: L2 cache: 2048K
[    7.502904] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
[    7.502912] Compat vDSO mapped to ffffe000.
[    7.502916] Remapping vsyscall page to ffffe000
[    7.502926] Checking 'hlt' instruction... OK.
[    7.518783] SMP alternatives: switching to UP code
[    7.518977] Freeing SMP alternatives: 11k freed
[    7.519134] Early unpacking initramfs... done
[    7.803601] ACPI: Core revision 20060707
[    7.803740] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    7.805468] ACPI: setting ELCR to 0200 (from 0e00)
[    7.805594] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 06
[    7.805599] SMP motherboard not detected.
[    7.805601] Local APIC not detected. Using dummy APIC emulation.
[    7.805633] Brought up 1 CPUs
[    7.805845] Booting paravirtualized kernel on bare hardware
[    7.805901] Time: 23:24:00  Date: 05/24/107
[    7.805927] NET: Registered protocol family 16
[    7.805999] EISA bus registered
[    7.806003] ACPI: bus type pci registered
[    7.806072] PCI: PCI BIOS revision 2.10 entry at 0xfd67c, last bus=5
[    7.806074] PCI: Using configuration type 1
[    7.806076] Setting up standard PCI resources
[    7.808863] ACPI: Interpreter enabled
[    7.808865] ACPI: Using PIC for interrupt routing
[    7.809310] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *11)
[    7.809569] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
[    7.809891] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
[    7.810148] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
[    7.810404] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
[    7.810726] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
[    7.810985] ACPI: PCI Interrupt Link [LNKG] (IRQs *10)
[    7.811240] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
[    7.811364] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    7.811368] PCI: Probing PCI hardware (bus 00)
[    7.811902] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    7.812286] PCI quirk: region d800-d87f claimed by ICH4 ACPI/GPIO/TCO
[    7.812289] PCI quirk: region eec0-eeff claimed by ICH4 GPIO
[    7.812474] Boot video device is 0000:01:00.0
[    7.812851] PCI: Transparent bridge - 0000:00:1e.0
[    7.812941] PCI: Bus #05 (-#08) is hidden behind transparent bridge #02 (-#05) (try 'pci=assign-busses')
[    7.812944] Please report the result to linux-kernel to fix this permanently
[    7.812959] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    7.816156] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    7.819487] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    7.820284] ACPI: Power Resource [PFAN] (off)
[    7.820350] Linux Plug and Play Support v0.97 (c) Adam Belay
[    7.820362] pnp: PnP ACPI init
[    7.825787] pnp: PnP ACPI: found 12 devices
[    7.825790] PnPBIOS: Disabled by ACPI PNP
[    7.825824] PCI: Using ACPI for IRQ routing
[    7.825827] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    7.831435] NET: Registered protocol family 8
[    7.831437] NET: Registered protocol family 20
[    7.832245] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:01:00.0
[    7.832296] PCI: Bridge: 0000:00:01.0
[    7.832298]   IO window: disabled.
[    7.832301]   MEM window: fd000000-fdffffff
[    7.832304]   PREFETCH window: d0000000-dfffffff
[    7.832316] PCI: Bus 3, cardbus bridge: 0000:02:0b.0
[    7.832318]   IO window: 0000c000-0000c0ff
[    7.832321]   IO window: 0000c400-0000c4ff
[    7.832326]   PREFETCH window: 30000000-33ffffff
[    7.832330]   MEM window: 3c000000-3fffffff
[    7.832333] PCI: Bus 5, cardbus bridge: 0000:02:0b.1
[    7.832335]   IO window: 0000c800-0000c8ff
[    7.832339]   IO window: 0000cc00-0000ccff
[    7.832343]   PREFETCH window: 34000000-37ffffff
[    7.832347]   MEM window: 40000000-43ffffff
[    7.832350] PCI: Bridge: 0000:00:1e.0
[    7.832353]   IO window: c000-cfff
[    7.832358]   MEM window: fce00000-fcefffff
[    7.832361]   PREFETCH window: 30000000-37ffffff
[    7.832375] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    7.832387] PCI: Enabling device 0000:02:0b.0 (0000 -> 0003)
[    7.832577] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    7.832580] PCI: setting IRQ 11 as level-triggered
[    7.832583] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    7.832599] PCI: Enabling device 0000:02:0b.1 (0000 -> 0003)
[    7.832780] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    7.832782] ACPI: PCI Interrupt 0000:02:0b.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    7.832805] NET: Registered protocol family 2
[    7.870575] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    7.870639] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    7.870739] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    7.870794] TCP: Hash tables configured (established 16384 bind 8192)
[    7.870796] TCP reno registered
[    7.882604] checking if image is initramfs... it is
[    8.441067] Freeing initrd memory: 6789k freed
[    8.441489] audit: initializing netlink socket (disabled)
[    8.441505] audit(1182727440.216:1): initialized
[    8.441630] VFS: Disk quotas dquot_6.5.1
[    8.441650] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    8.441699] io scheduler noop registered
[    8.441701] io scheduler anticipatory registered
[    8.441703] io scheduler deadline registered
[    8.441712] io scheduler cfq registered (default)
[    8.442003] isapnp: Scanning for PnP cards...
[    8.794617] isapnp: No Plug & Play device found
[    8.815802] Real Time Clock Driver v1.12ac
[    8.815866] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    8.815982] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    8.816559] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    8.817034] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    8.817038] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    8.817047] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[    8.817123] mice: PS/2 mouse device common for all mice
[    8.817595] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    8.817794] input: Macintosh mouse button emulation as /class/input/input0
[    8.817826] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    8.817829] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    8.818001] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    8.822507] serio: i8042 KBD port at 0x60,0x64 irq 1
[    8.822512] serio: i8042 AUX port at 0x60,0x64 irq 12
[    8.822610] EISA: Probing bus 0 at eisa.0
[    8.822632] EISA: Detected 0 cards.
[    8.852707] TCP cubic registered
[    8.852715] NET: Registered protocol family 1
[    8.852737] Using IPI No-Shortcut mode
[    8.852792] ACPI: (supports S0 S3 S4 S5)
[    8.852830]   Magic number: 11:618:454
[    8.853187] Freeing unused kernel memory: 328k freed
[    8.854035] Time: tsc clocksource has been installed.
[    8.864586] input: AT Translated Set 2 keyboard as /class/input/input1
[   10.037973] Capability LSM initialized
[   10.061552] ACPI: Transitioning device [FAN] to D3
[   10.061555] ACPI: Transitioning device [FAN] to D3
[   10.061558] ACPI: Fan [FAN] (off)
[   10.064978] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   10.065711] ACPI: Thermal Zone [THRM] (18 C)
[   10.307058] usbcore: registered new interface driver usbfs
[   10.307079] usbcore: registered new interface driver hub
[   10.307098] usbcore: registered new device driver usb
[   10.307786] USB Universal Host Controller Interface driver v3.0
[   10.307834] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   10.307849] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   10.307852] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   10.308030] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   10.308052] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000efe0
[   10.308141] usb usb1: configuration #1 chosen from 1 choice
[   10.308163] hub 1-0:1.0: USB hub found
[   10.308167] hub 1-0:1.0: 2 ports detected
[   10.355838] SCSI subsystem initialized
[   10.360286] libata version 2.20 loaded.
[   10.405892] ieee1394: Initialized config rom entry `ip1394'
[   10.409395] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   10.409410] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   10.409413] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   10.409433] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   10.409456] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000ef80
[   10.409536] usb usb2: configuration #1 chosen from 1 choice
[   10.409557] hub 2-0:1.0: USB hub found
[   10.409562] hub 2-0:1.0: 2 ports detected
[   10.415863] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[   10.415866] Copyright (c) 1999-2006 Intel Corporation.
[   10.513606] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   10.513612] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   10.513625] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   10.513629] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   10.513651] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   10.513674] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000ef60
[   10.513758] usb usb3: configuration #1 chosen from 1 choice
[   10.513779] hub 3-0:1.0: USB hub found
[   10.513785] hub 3-0:1.0: 2 ports detected
[    3.168000] Time: acpi_pm clocksource has been installed.
[    3.212000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    3.212000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[    3.212000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.212000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.212000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    3.212000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.212000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.212000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xfcfffc00
[    3.216000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.216000] usb usb4: configuration #1 chosen from 1 choice
[    3.216000] hub 4-0:1.0: USB hub found
[    3.216000] hub 4-0:1.0: 6 ports detected
[    3.320000] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.320000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.320000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.320000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[    3.320000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[    3.320000] scsi0 : ata_piix
[    3.484000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    3.484000] ata1.00: ATA-6: HTS548080M9AT00, MG4OA53A, max UDMA/100
[    3.484000] ata1.00: 156301488 sectors, multi 0: LBA48 
[    3.492000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    3.492000] ata1.00: configured for UDMA/100
[    3.492000] scsi1 : ata_piix
[    3.876000] ata2.00: ATAPI, max UDMA/33
[    4.064000] ata2.00: configured for UDMA/33
[    4.064000] scsi 0:0:0:0: Direct-Access     ATA      HTS548080M9AT00  MG4O PQ: 0 ANSI: 5
[    4.072000] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-C2612 1315 PQ: 0 ANSI: 5
[    4.076000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[    4.076000] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[    4.124000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fcefe800-fcefefff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.124000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    4.124000] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[    4.136000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.136000] sda: Write Protect is off
[    4.136000] sda: Mode Sense: 00 3a 00 00
[    4.136000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.136000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.136000] sda: Write Protect is off
[    4.136000] sda: Mode Sense: 00 3a 00 00
[    4.136000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.136000]  sda:<6>e1000: 0000:02:09.0: e1000_probe: (PCI:33MHz:32-bit) 00:0e:7b:ba:ee:5f
[    4.376000]  sda1 sda2 <<6>e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    4.444000]  sda5 >
[    4.444000] sd 0:0:0:0: Attached scsi disk sda
[    4.488000] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[    4.488000] Uniform CD-ROM driver Revision: 3.20
[    4.488000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.492000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.492000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.640000] Attempting manual resume
[    4.640000] swsusp: Resume From Partition 8:5
[    4.640000] PM: Checking swsusp image.
[    4.640000] PM: Resume from disk failed.
[    4.692000] kjournald starting.  Commit interval 5 seconds
[    4.692000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.004000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    5.180000] usb 2-2: configuration #1 chosen from 1 choice
[    5.396000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000390000680e91]
[   17.156000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.160000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.356000] iTCO_vendor_support: vendor-support=0
[   17.360000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   17.360000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x5860)
[   17.360000] iTCO_wdt: heartbeat value must be 2<heartbeat<39 (TCO v1) or 613 (TCO v2), using 30
[   17.360000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.384000] intel_rng: FWH not detected
[   17.576000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.584000] agpgart: Detected an Intel 855PM Chipset.
[   17.596000] agpgart: AGP aperture is 256M @ 0xe0000000
[   17.952000] NET: Registered protocol family 17
[   18.000000] ieee80211_crypt: registered algorithm 'NULL'
[   18.000000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   18.000000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   18.020000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   18.020000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   18.024000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   18.024000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   18.440000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   18.440000] Yenta: CardBus bridge found at 0000:02:0b.0 [1179:0001]
[   18.480000] input: PC Speaker as /class/input/input2
[   18.552000] parport: PnPBIOS parport detected.
[   18.552000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   18.564000] usbcore: registered new interface driver hiddev
[   18.568000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[   18.568000] Socket status: 30000011
[   18.568000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[   18.568000] cs: IO port probe 0xc000-0xcfff: clean.
[   18.568000] pcmcia: parent PCI bridge Memory window: 0xfce00000 - 0xfcefffff
[   18.568000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
[   18.568000] Yenta: CardBus bridge found at 0000:02:0b.1 [1179:0001]
[   18.580000] input: Logitech USB Receiver as /class/input/input3
[   18.580000] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2
[   18.600000] nvidia: module license 'NVIDIA' taints kernel.
[   18.852000] input: Logitech USB Receiver as /class/input/input4
[   18.852000] input,hiddev96: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2
[   18.852000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[   18.852000] Socket status: 30000007
[   18.852000] Yenta: Raising subordinate bus# of parent bus (#02) from #05 to #08
[   18.852000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[   18.852000] cs: IO port probe 0xc000-0xcfff: clean.
[   18.852000] pcmcia: parent PCI bridge Memory window: 0xfce00000 - 0xfcefffff
[   18.852000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
[   18.852000] usbcore: registered new interface driver xpad
[   18.852000] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   18.864000] usbcore: registered new interface driver usbhid
[   18.864000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   18.940000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[   18.940000] PCI: setting IRQ 10 as level-triggered
[   18.940000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKG] -> GSI 10 (level, low) -> IRQ 10
[   18.940000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   19.136000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   19.136000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   19.372000] pccard: PCMCIA card inserted into slot 0
[   19.372000] cs: memory probe 0xfce00000-0xfcefffff: excluding 0xfce00000-0xfce0ffff 0xfceb0000-0xfcedffff 0xfcef0000-0xfcefffff
[   19.380000] pcmcia: registering new device pcmcia0.0
[   19.668000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7
[   19.668000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.668000] cs: IO port probe 0x820-0x8ff: clean.
[   19.668000] cs: IO port probe 0xc00-0xcf7: clean.
[   19.668000] cs: IO port probe 0xa00-0xaff: clean.
[   19.688000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7
[   19.688000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.688000] cs: IO port probe 0x820-0x8ff: clean.
[   19.688000] cs: IO port probe 0xc00-0xcf7: clean.
[   19.688000] cs: IO port probe 0xa00-0xaff: clean.
[   19.744000] eth2: Xircom: port 0xc300, irq 3, hwaddr 00:10:A4:F9:5F:5F
[   19.956000] intel8x0_measure_ac97_clock: measured 55486 usecs
[   19.956000] intel8x0: clocking to 48000
[   20.060000] fuse init (API version 7.8)
[   20.076000] lp0: using parport0 (interrupt-driven).
[   20.116000] Adding 1510068k swap on /dev/disk/by-uuid/40a586ef-eeb5-4a77-83b3-378a4938b727.  Priority:-1 extents:1 across:1510068k
[   20.260000] EXT3 FS on sda1, internal journal
[   23.032000] eth2: MII link partner: 45e1
[   23.032000] eth2: MII selected
[   23.056000] eth2: media 100BaseT, silicon revision 4
[   25.908000] ACPI: ACPI Dock Station Driver 
[   25.928000] ACPI: AC Adapter [ADP1] (on-line)
[   25.980000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[   25.980000] toshiba_acpi:     HCI method: \_SB_.VALZ.GHCI
[   25.980000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[   25.980000] toshiba_acpi: ktoshkeyd will check 2 times per second
[   25.988000] Using specific hotkey driver
[   25.988000] toshiba_acpi: Dropped 0 keys from the queue on startup
[   26.012000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   26.032000] ibm_acpi: ec object not found
[   26.096000] input: Power Button (FF) as /class/input/input5
[   26.100000] ACPI: Power Button (FF) [PWRF]
[   26.132000] input: Power Button (CM) as /class/input/input6
[   26.136000] ACPI: Power Button (CM) [PWRB]
[   26.164000] input: Lid Switch as /class/input/input7
[   26.168000] ACPI: Lid Switch [LID]
[   26.176000] ACPI: Battery Slot [BAT1] (battery present)
[   26.176000] ACPI: Battery Slot [BAT2] (battery absent)
[   26.204000] pcc_acpi: loading...
[   27.472000] NET: Registered protocol family 10
[   27.472000] lo: Disabled Privacy Extensions
[   27.472000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.184000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   31.184000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   31.184000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   31.424000] ppdev: user-space parallel port driver
[   36.984000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   36.984000] apm: overridden by ACPI.
[   37.104000] Bluetooth: Core ver 2.11
[   37.104000] NET: Registered protocol family 31
[   37.104000] Bluetooth: HCI device and connection manager initialized
[   37.104000] Bluetooth: HCI socket layer initialized
[   37.132000] Bluetooth: L2CAP ver 2.8
[   37.132000] Bluetooth: L2CAP socket layer initialized
[   37.232000] Bluetooth: RFCOMM socket layer initialized
[   37.232000] Bluetooth: RFCOMM TTY layer initialized
[   37.232000] Bluetooth: RFCOMM ver 1.8
[   46.148000] eth2: no IPv6 routers present

---

### Post by LazyTownRocks on 2007-07-02
Dapper-Drake 6.06 works great on the M2 if that's any help;)

---

