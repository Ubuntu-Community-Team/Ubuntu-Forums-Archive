---
title: "ACPI on Toshiba M45-S359 - Help me shut down and stanby!"
date: 2007-09-21
forum: Hardware &amp; Laptops
---

### Post by cdmwebs on 2007-09-21
I have a Toshiba M45-S359 that won't play nice with Ubuntu.  Currently running Gutsy, but have had problems back to Edgy.  Yes, I've tried the stuff [here]("http://cantrip.org/toshiba-m45.html") with no effect.

Here's my dmesg:

```

[    0.000000] Linux version 2.6.22-12-generic (buildd@rothera) (gcc version 4.1.3 20070831 (prerelease) (Ubuntu 4.1.2-16ubuntu1)) #1 SMP Thu Sep 20 18:51:18 GMT 2007 (Ubuntu 2.6.22-12.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005f7dfffc (usable)
[    0.000000]  BIOS-e820: 000000005f7dfffc - 000000005f7fffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000005f7fffc0 - 000000005f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 631MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 391135) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   391135
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   391135
[    0.000000] On node 0 totalpages: 391135
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1263 pages used for memmap
[    0.000000]   HighMem zone: 160496 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000E5010, 0014 (r0 TOSINV)
[    0.000000] ACPI: RSDT 5F7F86C7, 0034 (r1 TOSINV RSDT_000      100 ABCD    10200)
[    0.000000] ACPI: FACP 5F7FFB30, 0074 (r1 TOSINV FACP_000      100 0000    10200)
[    0.000000] ACPI: DSDT 5F7F8D10, 6E19 (r1 TOSINV SONOMA       1004 INTL  2002036)
[    0.000000] ACPI: FACS 5F7FFFC0, 0040
[    0.000000] ACPI: MCFG 5F7FFBC0, 003C (r1 INSYDE MCFG_000 30303030 0000 30303030)
[    0.000000] ACPI: SSDT 5F7F88B5, 0279 (r1  PmRef  Cpu0Ist     3000 INTL 20030522)
[    0.000000] ACPI: SSDT 5F7F86FB, 01BA (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 5f800000:a0700000)
[    0.000000] Built 1 zonelists.  Total pages: 388080
[    0.000000] Kernel command line: root=UUID=412d9908-9ec7-403a-875d-bbad7595c11e ro quiet splash acpi_irq_balance
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (01c01000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.121 MHz processor.
[   14.373817] Console: colour VGA+ 80x25
[   14.374143] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.374541] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.444446] Memory: 1539352k/1564540k available (2017k kernel code, 23964k reserved, 918k data, 364k init, 647036k highmem)
[   14.444455] virtual kernel memory layout:
[   14.444456]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   14.444458]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.444459]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.444460]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.444461]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   14.444462]       .data : 0xc02f8456 - 0xc03ddea4   ( 918 kB)
[   14.444463]       .text : 0xc0100000 - 0xc02f8456   (2017 kB)
[   14.444466] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.444512] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   14.524500] Calibrating delay using timer specific routine.. 3994.14 BogoMIPS (lpj=7988290)
[   14.524534] Security Framework v1.0.0 initialized
[   14.524544] SELinux:  Disabled at boot.
[   14.524559] Mount-cache hash table entries: 512
[   14.524712] CPU: After generic identify, caps: afe9f9ff 00000000 00000000 00000000 00000180 00000000 00000000
[   14.524724] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.524726] CPU: L2 cache: 2048K
[   14.524730] CPU: After all inits, caps: afe9f9ff 00000000 00000000 00002040 00000180 00000000 00000000
[   14.524740] Compat vDSO mapped to ffffe000.
[   14.524757] Checking 'hlt' instruction... OK.
[   14.540627] SMP alternatives: switching to UP code
[   14.540877] Freeing SMP alternatives: 11k freed
[   14.541140] Early unpacking initramfs... done
[   14.832462] ACPI: Core revision 20070126
[   14.832535] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.834863] ACPI: setting ELCR to 0200 (from 0c20)
[   14.906335] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 08
[   14.906342] SMP motherboard not detected.
[   14.906344] Local APIC not detected. Using dummy APIC emulation.
[   14.906373] Brought up 1 CPUs
[   14.906471] Booting paravirtualized kernel on bare hardware
[   14.906537] Time: 20:04:00  Date: 08/21/107
[   14.906558] NET: Registered protocol family 16
[   14.906629] EISA bus registered
[   14.906649] ACPI: bus type pci registered
[   14.906696] PCI: PCI BIOS revision 2.10 entry at 0xea814, last bus=5
[   14.906698] PCI: Using configuration type 1
[   14.906699] Setting up standard PCI resources
[   14.908865] ACPI: EC: Look up EC in DSDT
[   14.915125] ACPI: EC: GPE=0x10, ports=0x66, 0x62
[   14.920004] ACPI: Interpreter enabled
[   14.920007] ACPI: (supports S0 S3 S4 S5)
[   14.920020] ACPI: Using PIC for interrupt routing
[   14.937172] ACPI: EC: GPE=0x10, ports=0x66, 0x62
[   14.937212] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.937219] PCI: Probing PCI hardware (bus 00)
[   14.937883] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   14.937887] PCI quirk: region 1300-133f claimed by ICH6 GPIO
[   14.938612] PCI: Transparent bridge - 0000:00:1e.0
[   14.938740] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.939069] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   14.939209] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   14.939360] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   14.962851] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *11)
[   14.962976] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *10 11)
[   14.963058] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 *11)
[   14.963139] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10 *11)
[   14.963220] ACPI: PCI Interrupt Link [LNKE] (IRQs *5 11)
[   14.963303] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 10) *0, disabled.
[   14.963417] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *11
[   14.963497] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 10) *11
[   14.963608] ACPI: Power Resource [PFA1] (off)
[   14.963614] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.963621] pnp: PnP ACPI init
[   14.963627] ACPI: bus type pnp registered
[   14.971741] pnp: PnP ACPI: found 9 devices
[   14.971743] ACPI: ACPI bus type pnp unregistered
[   14.971746] PnPBIOS: Disabled by ACPI PNP
[   14.971778] PCI: Using ACPI for IRQ routing
[   14.971780] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.971812] PCI: Cannot allocate resource region 0 of device 0000:05:06.0
[   14.980801] NET: Registered protocol family 8
[   14.980803] NET: Registered protocol family 20
[   14.980841] pnp: 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[   14.980844] pnp: 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[   14.980846] pnp: 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[   14.980849] pnp: 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[   14.980854] pnp: 00:05: iomem range 0xe0000000-0xefffffff has been reserved
[   14.980857] pnp: 00:05: iomem range 0xf0008000-0xf000bfff has been reserved
[   14.980860] pnp: 00:05: iomem range 0xfed14000-0xfed17fff has been reserved
[   14.980862] pnp: 00:05: iomem range 0xfed18000-0xfed18fff has been reserved
[   14.982617] Time: tsc clocksource has been installed.
[   15.011081] PCI: Bridge: 0000:00:1c.0
[   15.011084]   IO window: c000-dfff
[   15.011089]   MEM window: cc000000-cfffffff
[   15.011094]   PREFETCH window: 9c000000-9fffffff
[   15.011099] PCI: Bridge: 0000:00:1c.1
[   15.011102]   IO window: a000-bfff
[   15.011107]   MEM window: c8000000-cbffffff
[   15.011111]   PREFETCH window: 98000000-9bffffff
[   15.011125] PCI: Bus 6, cardbus bridge: 0000:05:06.0
[   15.011127]   IO window: 00008000-000080ff
[   15.011132]   IO window: 00008400-000084ff
[   15.011137]   PREFETCH window: 88000000-8bffffff
[   15.011141]   MEM window: bc000000-bfffffff
[   15.011146] PCI: Bridge: 0000:00:1e.0
[   15.011149]   IO window: 8000-9fff
[   15.011154]   MEM window: b8000000-c7ffffff
[   15.011159]   PREFETCH window: 88000000-97ffffff
[   15.011314] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   15.011317] PCI: setting IRQ 10 as level-triggered
[   15.011321] ACPI: PCI Interrupt 0000:00:1c.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   15.011328] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.011470] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   15.011472] PCI: setting IRQ 11 as level-triggered
[   15.011476] ACPI: PCI Interrupt 0000:00:1c.1[B] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   15.011482] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   15.011494] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   15.011629] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   15.011631] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   15.011646] NET: Registered protocol family 2
[   15.050608] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.050663] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   15.051847] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   15.052437] TCP: Hash tables configured (established 131072 bind 65536)
[   15.052440] TCP reno registered
[   15.062745] checking if image is initramfs... it is
[   15.514386] Switched to high resolution mode on CPU 0
[   15.633126] Freeing initrd memory: 7050k freed
[   15.633471] audit: initializing netlink socket (disabled)
[   15.633485] audit(1190405040.972:1): initialized
[   15.633556] highmem bounce pool size: 64 pages
[   15.635106] VFS: Disk quotas dquot_6.5.1
[   15.635149] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.635229] io scheduler noop registered
[   15.635231] io scheduler anticipatory registered
[   15.635233] io scheduler deadline registered
[   15.635248] io scheduler cfq registered (default)
[   15.635261] Boot video device is 0000:00:02.0
[   15.635405] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.635456] assign_interrupt_mode Found MSI capability
[   15.635501] Allocate Port Service[0000:00:1c.0:pcie00]
[   15.635529] Allocate Port Service[0000:00:1c.0:pcie02]
[   15.635613] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   15.635663] assign_interrupt_mode Found MSI capability
[   15.635703] Allocate Port Service[0000:00:1c.1:pcie00]
[   15.635729] Allocate Port Service[0000:00:1c.1:pcie02]
[   15.635886] isapnp: Scanning for PnP cards...
[   15.989920] isapnp: No Plug & Play device found
[   16.011601] Real Time Clock Driver v1.12ac
[   16.011715] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.012525] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   16.012530] ACPI: PCI Interrupt 0000:00:1e.3[B] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   16.012540] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   16.013013] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.013205] input: Macintosh mouse button emulation as /class/input/input0
[   16.013269] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   16.018546] i8042.c: Detected active multiplexing controller, rev 1.1.
[   16.020570] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.020575] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   16.020577] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   16.020579] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   16.020581] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   16.020725] mice: PS/2 mouse device common for all mice
[   16.021051] EISA: Probing bus 0 at eisa.0
[   16.021059] Cannot allocate resource for EISA slot 1
[   16.021082] Cannot allocate resource for EISA slot 8
[   16.021083] EISA: Detected 0 cards.
[   16.021184] TCP cubic registered
[   16.021199] NET: Registered protocol family 1
[   16.021221] Using IPI No-Shortcut mode
[   16.022544]   Magic number: 7:232:94
[   16.022830] Freeing unused kernel memory: 364k freed
[   16.102984] input: AT Translated Set 2 keyboard as /class/input/input1
[   17.193381] AppArmor: AppArmor initialized<5>audit(1190405042.472:2):  info="AppArmor initialized" pid=1211
[   17.200237] fuse init (API version 7.8)
[   17.203570] Failure registering capabilities with primary security module.
[   17.208361] ACPI: Transitioning device [FAN1] to D3
[   17.208363] ACPI: Transitioning device [FAN1] to D3
[   17.208366] ACPI: Fan [FAN1] (off)
[   17.212030] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   17.212035] ACPI: Processor [CPU0] (supports 8 throttling states)
[   17.212044] ACPI Exception (processor_core-0781): AE_NOT_FOUND, Processor Device is not present [20070126]
[    2.732000] Marking TSC unstable due to: possible TSC halt in C2.
[    2.736000] Time: acpi_pm clocksource has been installed.
[    2.764000] ACPI: Thermal Zone [TZCR] (75 C)
[    2.772000] ACPI: Thermal Zone [TZCL] (49 C)
[    3.000000] Clocksource tsc unstable (delta = -307126069 ns)
[    3.124000] usbcore: registered new interface driver usbfs
[    3.124000] usbcore: registered new interface driver hub
[    3.124000] usbcore: registered new device driver usb
[    3.128000] USB Universal Host Controller Interface driver v3.0
[    3.128000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    3.128000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[    3.128000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.128000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.128000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.128000] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200
[    3.128000] usb usb1: configuration #1 chosen from 1 choice
[    3.128000] hub 1-0:1.0: USB hub found
[    3.128000] hub 1-0:1.0: 2 ports detected
[    3.220000] SCSI subsystem initialized
[    3.224000] libata version 2.21 loaded.
[    3.232000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[    3.232000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[    3.232000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.232000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.232000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.232000] uhci_hcd 0000:00:1d.1: irq 10, io base 0x00001220
[    3.232000] usb usb2: configuration #1 chosen from 1 choice
[    3.232000] hub 2-0:1.0: USB hub found
[    3.232000] hub 2-0:1.0: 2 ports detected
[    3.336000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.336000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.336000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.336000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.336000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001240
[    3.336000] usb usb3: configuration #1 chosen from 1 choice
[    3.336000] hub 3-0:1.0: USB hub found
[    3.336000] hub 3-0:1.0: 2 ports detected
[    3.440000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.440000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.440000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.440000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.440000] uhci_hcd 0000:00:1d.3: irq 11, io base 0x00001260
[    3.440000] usb usb4: configuration #1 chosen from 1 choice
[    3.440000] hub 4-0:1.0: USB hub found
[    3.440000] hub 4-0:1.0: 2 ports detected
[    3.472000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    3.544000] ahci 0000:00:1f.2: version 2.2
[    3.544000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[    3.544000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[    3.544000] ahci: probe of 0000:00:1f.2 failed with error -22
[    3.548000] ata_piix 0000:00:1f.2: version 2.11
[    3.548000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    3.644000] usb 1-2: configuration #1 chosen from 1 choice
[    3.656000] usbcore: registered new interface driver hiddev
[    3.676000] input: Logitech USB Receiver as /class/input/input2
[    3.676000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
[    3.676000] usbcore: registered new interface driver usbhid
[    3.676000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    3.704000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[    3.704000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    3.704000] scsi0 : ata_piix
[    3.704000] scsi1 : ata_piix
[    3.704000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011100 irq 14
[    3.704000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011108 irq 15
[    3.868000] ata1.00: ATA-7: ST910021AS, 3.04, max UDMA/133
[    3.868000] ata1.00: 195371568 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.884000] ata1.00: configured for UDMA/133
[    4.204000] ata2.00: ATAPI: MATSHITADVD-RAM UJ-841S, 1.00, max UDMA/33
[    4.376000] ata2.00: configured for UDMA/33
[    4.376000] scsi 0:0:0:0: Direct-Access     ATA      ST910021AS       3.04 PQ: 0 ANSI: 5
[    4.376000] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-841S  1.00 PQ: 0 ANSI: 5
[    4.380000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 6
[    4.380000] PCI: setting IRQ 6 as level-triggered
[    4.380000] ACPI: PCI Interrupt 0000:05:06.2[C] -> Link [LNKG] -> GSI 6 (level, low) -> IRQ 6
[    4.428000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[    4.428000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[    4.428000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.428000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.428000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.428000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.428000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.428000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xf4000000
[    4.432000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.436000] usb usb5: configuration #1 chosen from 1 choice
[    4.436000] hub 5-0:1.0: USB hub found
[    4.436000] hub 5-0:1.0: 8 ports detected
[    4.436000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.444000] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[    4.444000] sd 0:0:0:0: [sda] Write Protect is off
[    4.444000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.444000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.444000] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[    4.444000] sd 0:0:0:0: [sda] Write Protect is off
[    4.444000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.444000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.444000]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    4.492000] usb 1-2: USB disconnect, address 2
[    4.512000] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.516000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.516000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.528000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.528000] Uniform CD-ROM driver Revision: 3.20
[    4.528000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.896000] Attempting manual resume
[    4.896000] swsusp: Resume From Partition 8:3
[    4.896000] PM: Checking swsusp image.
[    4.896000] PM: Resume from disk failed.
[    4.908000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    4.908000] EXT3-fs: write access will be enabled during recovery.
[    5.236000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[    5.408000] usb 1-2: configuration #1 chosen from 1 choice
[    5.432000] input: Logitech USB Receiver as /class/input/input3
[    5.432000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
[    5.708000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00080da0d1256106]
[    7.516000] kjournald starting.  Commit interval 5 seconds
[    7.516000] EXT3-fs: sda2: orphan cleanup on readonly fs
[    7.516000] ext3_orphan_cleanup: deleting unreferenced inode 98120
[    7.516000] ext3_orphan_cleanup: deleting unreferenced inode 98119
[    7.516000] ext3_orphan_cleanup: deleting unreferenced inode 98118
[    7.516000] ext3_orphan_cleanup: deleting unreferenced inode 98117
[    7.516000] ext3_orphan_cleanup: deleting unreferenced inode 98116
[    7.516000] EXT3-fs: sda2: 5 orphan inodes deleted
[    7.516000] EXT3-fs: recovery complete.
[    7.520000] EXT3-fs: mounted filesystem with ordered data mode.
[   15.660000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.700000] agpgart: Detected an Intel 915GM Chipset.
[   15.700000] agpgart: Detected 7932K stolen memory.
[   15.716000] agpgart: AGP aperture is 256M @ 0xa0000000
[   15.756000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.820000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.980000] ieee80211_crypt: registered algorithm 'NULL'
[   16.984000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.984000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   17.016000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   17.016000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   17.016000] sky2 0000:01:00.0: v1.14 addr 0xcc000000 irq 11 Yukon-FE (0xb7) rev 1
[   17.116000] sky2 0000:01:00.0: No interrupt generated using MSI, switching to INTx mode.
[   17.116000] sky2 eth0: addr 00:a0:d1:25:61:06
[   17.116000] Yenta: CardBus bridge found at 0000:05:06.0 [1179:ff10]
[   17.116000] Yenta: Enabling burst memory read transactions
[   17.116000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.116000] Yenta: Routing CardBus interrupts to PCI
[   17.116000] Yenta TI: socket 0000:05:06.0, mfunc 0x01aa1b22, devctl 0x66
[   17.124000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   17.124000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   17.132000] iTCO_vendor_support: vendor-support=0
[   17.160000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   17.212000] sdhci: Secure Digital Host Controller Interface driver
[   17.212000] sdhci: Copyright(c) Pierre Ossman
[   17.348000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[   17.348000] Socket status: 30000006
[   17.348000] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   17.348000] pcmcia: parent PCI bridge I/O window: 0x8000 - 0x9fff
[   17.348000] cs: IO port probe 0x8000-0x9fff: clean.
[   17.348000] pcmcia: parent PCI bridge Memory window: 0xb8000000 - 0xc7ffffff
[   17.348000] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x97ffffff
[   17.348000] ACPI: PCI Interrupt 0000:05:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   17.348000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   17.528000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   17.528000] sdhci: SDHCI controller found at 0000:05:06.4 [104c:8034] (rev 0)
[   17.528000] ACPI: PCI Interrupt 0000:05:06.4[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   17.528000] mmc0: SDHCI at 0xb800a000 irq 11 DMA
[   17.532000] mmc1: SDHCI at 0xb800a100 irq 11 DMA
[   17.532000] mmc2: SDHCI at 0xb800a200 irq 11 DMA
[   17.532000] ACPI: PCI Interrupt 0000:05:06.3[D] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   17.656000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   17.656000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   17.800000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[   17.800000] synaptics: Toshiba Satellite M45 detected, limiting rate to 40pps.
[   17.828000] cs: IO port probe 0x100-0x3af: excluding 0x300-0x307 0x310-0x31f
[   17.832000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   17.832000] cs: IO port probe 0x820-0x8ff: clean.
[   17.832000] cs: IO port probe 0xc00-0xcf7: clean.
[   17.832000] cs: IO port probe 0xa00-0xaff: clean.
[   17.856000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   17.864000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   17.864000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.884000] intel_rng: FWH not detected
[   18.584000] intel8x0_measure_ac97_clock: measured 55502 usecs
[   18.584000] intel8x0: clocking to 48000
[   19.228000] lp: driver loaded but no devices found
[   19.280000] Adding 1461904k swap on /dev/sda3.  Priority:-1 extents:1 across:1461904k
[   19.460000] EXT3 FS on sda2, internal journal
[   34.752000] kjournald starting.  Commit interval 5 seconds
[   34.756000] EXT3 FS on sda1, internal journal
[   34.756000] EXT3-fs: mounted filesystem with ordered data mode.
[   34.792000] ReiserFS: sda5: found reiserfs format "3.6" with standard journal
[   34.792000] ReiserFS: sda5: using ordered data mode
[   34.800000] ReiserFS: sda5: journal params: device sda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   34.800000] ReiserFS: sda5: checking transaction log (sda5)
[   34.820000] ReiserFS: sda5: Using r5 hash to sort names
[   34.868000] ReiserFS: sda5: Removing [4606 8979 0x0 SD]..done
[   34.872000] ReiserFS: sda5: There were 1 uncompleted unlinks/truncates. Completed
[   35.708000] input: Power Button (FF) as /class/input/input5
[   35.712000] ACPI: Power Button (FF) [PWRF]
[   35.752000] input: Lid Switch as /class/input/input6
[   35.752000] ACPI: Lid Switch [LID0]
[   35.792000] input: Power Button (CM) as /class/input/input7
[   35.796000] ACPI: Power Button (CM) [PWRB]
[   35.852000] ACPI: ACPI Dock Station Driver 
[   35.876000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   35.920000] ACPI: Battery Slot [BAT1] (battery present)
[   35.932000] ACPI: AC Adapter [AC] (off-line)
[   36.972000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   36.972000] PCI: Setting latency timer of device 0000:00:1e.3 to 64
[   37.544000] sky2 eth0: enabling interface
[   37.544000] sky2 eth0: ram buffer 4K
[   37.944000] ppdev: user-space parallel port driver
[   38.380000] audit(1190405079.092:3): operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4957 profile="/usr/sbin/cupsd"
[   40.000000] apm: BIOS not found.
[   40.884000] Failure registering capabilities with primary security module.
[   41.084000] Bluetooth: Core ver 2.11
[   41.084000] NET: Registered protocol family 31
[   41.084000] Bluetooth: HCI device and connection manager initialized
[   41.084000] Bluetooth: HCI socket layer initialized
[   41.116000] Bluetooth: L2CAP ver 2.8
[   41.116000] Bluetooth: L2CAP socket layer initialized
[   41.176000] Bluetooth: RFCOMM socket layer initialized
[   41.176000] Bluetooth: RFCOMM TTY layer initialized
[   41.176000] Bluetooth: RFCOMM ver 1.8
[   42.484000] [drm] Initialized drm 1.1.0 20060810
[   42.488000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   42.488000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   51.236000] NET: Registered protocol family 10
[   51.236000] lo: Disabled Privacy Extensions
[   51.236000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   51.236000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   63.784000] NET: Registered protocol family 17
[   64.268000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   64.396000] ieee80211_crypt: registered algorithm 'TKIP'
[   81.416000] eth1: no IPv6 routers present

```

Let me know if you need more info!  Thanks!!

---

### Post by cdmwebs on 2007-10-06
Bump.  No suspend experts?  

After a clean reload of Gutsy, updates and the installation of the omnibook kernel module, it worked for a while.  Then another round of updates seems to have broken it.  It makes all the motions of a suspend, minus the actual shutdown and flashing light.  I have to power it off and basically cold boot.

How can I even troubleshoot this stuff?  It can't power itself off either.  I get to the point where the last message is Power down, but I have to physically turn it off.

Thanks for any help!!

---

### Post by TheCanuck on 2007-10-07
I've had this happen before on a laptop when the kernel wasn't compiled properly.  I fogot to select a few things in ACPI.  You could try recompiling the kernel to the latest stable version and go through the ACPI modules and enable all the relevant ones for your laptop.  Other options that can help are by appending different options to the kernel before startup (i.e. edit /boot/grub/grub.conf and add these after root=/dev etc)

acpi=force lapic

You can also try acpi=power-off   if the above two don't work.  But I do see in your printout that lapic is disabled which may have something to do with your power-off problem, so adding lapic to grub may fix it.

---

### Post by cdmwebs on 2007-10-07
Thanks for the input Canuck.

With your suggestion, I googled lapic and found [this page]("http://toshsoft.de/wiki/index.php/Toshiba_Satellite_M40_with_ATI_Graphics_Adapter") for a similar Toshiba.  I wonder if the below snippet is relevant?

> now edit your grub.conf and change your kernel line to

kernel (hd0,1)/mm-2.6.16 resume=/dev/sda6 vmalloc=256M video=vesafb:1024x768-16@70 vga=791 acpi_os_name="Microsoft Windows XP" lapic

substitute mm-2.6.16 with your kernel. The vesafb Param is for a neat 1024x768 framebuffer-console, acpi_os_name is to make the notebook think its running Windows, so it enables the ACPI features and lapic enables your local apic. 


Not sure, but I'm off to try.  I'll report back...

---

### Post by TheCanuck on 2007-10-07
Hmm the os_name is one I haven't tried before but some of the newer bios' do have specific calls for Windows in the DSDT.  So that may work or even telling it a different OS name like Windows 2001.1, Windows 2001 etc may do the trick.  This DSDT for an M45-s169 makes reference to that:

[http://acpi.sourceforge.net/dsdt/view.php?id=521](http://acpi.sourceforge.net/dsdt/view.php?id=521)

Your DSDT may have some errors in it that are preventing shutdown.  Fixing them and then adding the revised DSDT to the initramfs may help.

---

### Post by cdmwebs on 2007-10-07
Agreed.  I tried it both ways - once with the os_name and once without, both times with lapic.  Without os_name had negative results - wireless didn't work, no battery status, etc.  With os_name it seems much better in the dmesg output, but it still doesn't want to suspend.  I can't find anything in the message log indicating problems, to me anyway.  Included below for reference.

**/var/log/messages/** (with os_name off)
```

Oct  7 20:01:10 hemingway kernel: [    0.000000]  BIOS-e820: 000000005f7dfffc - 000000005f7fffc0 (ACPI data)
Oct  7 20:01:10 hemingway kernel: [    0.000000]  BIOS-e820: 000000005f7fffc0 - 000000005f800000 (ACPI NVS)
Oct  7 20:01:10 hemingway kernel: [    0.000000] ACPI: RSDP signature @ 0xC00E5010 checksum 0
Oct  7 20:01:10 hemingway kernel: [    0.000000] ACPI: RSDP 000E5010, 0014 (r0 TOSINV)
Oct  7 20:01:10 hemingway kernel: [    0.000000] ACPI: RSDT 5F7F86C7, 0034 (r1 TOSINV RSDT_000      100 ABCD    10200)
Oct  7 20:01:10 hemingway kernel: [    0.000000] ACPI: FACP 5F7FFB30, 0074 (r1 TOSINV FACP_000      100 0000    10200)
Oct  7 20:01:10 hemingway kernel: [    0.000000] ACPI: DSDT 5F7F8D10, 6E19 (r1 TOSINV SONOMA       1004 INTL  2002036)
Oct  7 20:01:10 hemingway kernel: [    0.000000] ACPI: FACS 5F7FFFC0, 0040
Oct  7 20:01:10 hemingway kernel: [    0.000000] ACPI: MCFG 5F7FFBC0, 003C (r1 INSYDE MCFG_000 30303030 0000 30303030)
Oct  7 20:01:10 hemingway kernel: [    0.000000] ACPI: SSDT 5F7F88B5, 0279 (r1  PmRef  Cpu0Ist     3000 INTL 20030522)
Oct  7 20:01:10 hemingway kernel: [    0.000000] ACPI: SSDT 5F7F86FB, 01BA (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
Oct  7 20:01:10 hemingway kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Oct  7 20:01:10 hemingway kernel: [   21.498617] ACPI: Core revision 20070126
Oct  7 20:01:10 hemingway kernel: [   21.498746] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct  7 20:01:10 hemingway kernel: [   21.501191] ACPI: setting ELCR to 0200 (from 0c20)
Oct  7 20:01:10 hemingway kernel: [   21.506199] ACPI Error (hwacpi-0142): Hardware did not change modes [20070126]
Oct  7 20:01:10 hemingway kernel: [   21.506335] ACPI Error (evxfevnt-0086): Could not transition to ACPI mode [20070126]
Oct  7 20:01:10 hemingway kernel: [   21.506473] ACPI Warning (utxface-0139): AcpiEnable failed [20070126]
Oct  7 20:01:10 hemingway kernel: [   21.613191] ACPI: Interpreter disabled.
Oct  7 20:01:10 hemingway kernel: [   21.613310] pnp: PnP ACPI: disabled
Oct  7 20:01:10 hemingway kernel: [   21.614762] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Oct  7 20:01:10 hemingway kernel: [   23.010445] thermal: Unknown symbol acpi_processor_set_thermal_limit
Oct  7 20:01:10 hemingway kernel: [   71.164811] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
Oct  7 20:01:10 hemingway kernel: [   71.164847] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
Oct  7 20:01:10 hemingway kernel: [   71.164941] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
Oct  7 20:01:10 hemingway kernel: [   71.164986] acpi_cpufreq: Unknown symbol acpi_processor_register_performance

```

**dmesg | grep -i ACPI** (with os_name set)
```

[    0.000000]  BIOS-e820: 000000005f7dfffc - 000000005f7fffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000005f7fffc0 - 000000005f800000 (ACPI NVS)
[    0.000000] ACPI: RSDP signature @ 0xC00E5010 checksum 0
[    0.000000] ACPI: RSDP 000E5010, 0014 (r0 TOSINV)
[    0.000000] ACPI: RSDT 5F7F86C7, 0034 (r1 TOSINV RSDT_000      100 ABCD    10200)
[    0.000000] ACPI: FACP 5F7FFB30, 0074 (r1 TOSINV FACP_000      100 0000    10200)
[    0.000000] ACPI: DSDT 5F7F8D10, 6E19 (r1 TOSINV SONOMA       1004 INTL  2002036)
[    0.000000] ACPI: FACS 5F7FFFC0, 0040
[    0.000000] ACPI: MCFG 5F7FFBC0, 003C (r1 INSYDE MCFG_000 30303030 0000 30303030)
[    0.000000] ACPI: SSDT 5F7F88B5, 0279 (r1  PmRef  Cpu0Ist     3000 INTL 20030522)
[    0.000000] ACPI: SSDT 5F7F86FB, 01BA (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Kernel command line: root=UUID=d4eec8aa-f7dd-46e5-bc22-0c6f444da237 ro acpi_os_name="Microsoft Windows XP" lapic
[   11.441749] ACPI: Core revision 20070126
[   11.441834] ACPI: Overriding _OS definition to 'Microsoft Windows XP'
[   11.441934] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   11.444359] ACPI: setting ELCR to 0200 (from 0c20)
[   11.613888] ACPI: bus type pci registered
[   11.616418] ACPI: EC: Look up EC in DSDT
[   11.621769] ACPI: EC: GPE=0x10, ports=0x66, 0x62
[   11.626671] ACPI: Interpreter enabled
[   11.626726] ACPI: (supports S0 S3 S4 S5)
[   11.626939] ACPI: Using PIC for interrupt routing
[   11.643812] ACPI: EC: GPE=0x10, ports=0x66, 0x62
[   11.643902] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.644631] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   11.645649] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.645978] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   11.646117] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   11.646268] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   11.669508] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *11)
[   11.669807] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *10 11)
[   11.670093] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 *11)
[   11.670348] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10 *11)
[   11.670631] ACPI: PCI Interrupt Link [LNKE] (IRQs *5 11)
[   11.670888] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 10) *0, disabled.
[   11.671238] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *11
[   11.671493] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 10) *11
[   11.671807] ACPI: Power Resource [PFA1] (off)
[   11.671930] pnp: PnP ACPI init
[   11.671986] ACPI: bus type pnp registered
[   11.682401] pnp: PnP ACPI: found 9 devices
[   11.682456] ACPI: ACPI bus type pnp unregistered
[   11.682513] PnPBIOS: Disabled by ACPI PNP
[   11.682597] PCI: Using ACPI for IRQ routing
[   11.723722] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   11.723785] ACPI: PCI Interrupt 0000:00:1c.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   11.724069] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   11.724132] ACPI: PCI Interrupt 0000:00:1c.1[B] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   11.724422] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   11.724480] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   12.722397] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 5
[   12.722462] ACPI: PCI Interrupt 0000:00:1e.3[B] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   12.722608] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   12.979163] ACPI: Transitioning device [FAN1] to D3
[   12.979221] ACPI: Transitioning device [FAN1] to D3
[   12.979278] ACPI: Fan [FAN1] (off)
[   12.982564] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   12.982742] ACPI: Processor [CPU0] (supports 8 throttling states)
[   12.982868] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[    1.808000] Time: acpi_pm clocksource has been installed.
[    1.828000] ACPI: Thermal Zone [TZCR] (70 C)
[    1.836000] ACPI: Thermal Zone [TZCL] (47 C)
[    2.332000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    2.332000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[    2.436000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    2.436000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    2.540000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    2.644000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    2.768000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[    3.036000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.712000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 6
[    3.712000] ACPI: PCI Interrupt 0000:05:06.2[C] -> Link [LNKG] -> GSI 6 (level, low) -> IRQ 6
[   14.480000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   15.432000] ACPI: PCI Interrupt 0000:05:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   15.640000] ACPI: PCI Interrupt 0000:05:06.3[D] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   15.640000] ACPI: PCI Interrupt 0000:05:06.4[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   16.008000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   32.240000] ACPI: AC Adapter [AC] (on-line)
[   32.268000] ACPI: ACPI Dock Station Driver 
[   32.316000] ACPI: Battery Slot [BAT1] (battery present)
[   32.372000] ACPI: Power Button (FF) [PWRF]
[   32.412000] ACPI: Lid Switch [LID0]
[   32.452000] ACPI: Power Button (CM) [PWRB]
[   32.532000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   36.204000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11

```

**/var/log/messages** just as suspend is requested with os_name set:
```

Oct  7 19:58:36 hemingway dhcdbd: Unrequested down ?:3
Oct  7 19:58:36 hemingway kernel: [  729.376000] sky2 eth0: disabling interface
Oct  7 19:58:37 hemingway kernel: [  729.952000] ACPI: PCI interrupt for device 0000:01:00.0 disabled
Oct  7 19:58:38 hemingway kernel: [  730.764000] ACPI: PCI interrupt for device 0000:05:04.0 disabled
Oct  7 20:01:10 hemingway syslogd 1.4.1#21ubuntu3: restart.

```

---

### Post by cdmwebs on 2007-10-07
Also, I checked out the DSDT link you sent.  The problem is (from what I've learned) that there are three different BIOSes for Toshiba laptops: Toshiba BIOS, Phoenix BIOS, and ACPI BIOS.  I'm led to believe that I have the ACPI BIOS version.  I've been trying to figure out a similar laptop model with the same ACPI BIOS with no luck so far.  I guess I could try that DSDT and see what happens.  I doubt I can cause irreversible damage, can I?

Also, here's a PDF of the specs of my laptop from Toshiba, in case anyone is interested.  I had to tar it because it was bigger than 19kb.

---

### Post by TheCanuck on 2007-10-07
What happens if you just run:   sudo echo -n mem > /sys/power/state  ?

Also, messing with the DSDT seems to be quite safe.  I've tried using DSDT's that were from completely different laptops and if there was a problem I either got a kernel panic or it just wouldn't boot.  Best thing though is to compare that one to yours and see if there are any differences.  Probably what you should do is just extract your DSDT, run the iasl compiler on it to see what errors (if any) come up and then try to fix them.  


Or you could just try installing apmd and then run apm -z for suspending.  That may work.


I don't use the default suspend with any of the distros.  I actually use a custom script that I found in this article:  [http://www.linux.com/articles/54610](http://www.linux.com/articles/54610)

Good read, and it may give you some pointers.  Whenever I used stock suspend/hibernate I had issues with resuming.  Now suspend / hibernate works great -- the other day I left it in suspend for 6 hours and the battery had only depleted 10%.

---

### Post by Ambiguity on 2007-11-02
If you have only used Gutsy, Your problem sounds like the same one others have been having with ATI video cards. There is a bug tracker for it here:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653)

---

