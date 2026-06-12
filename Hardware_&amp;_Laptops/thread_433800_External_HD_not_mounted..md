---
title: "External HD not mounted."
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by shriphani on 2007-05-05
hello all,
i just switched to feisty this morning and basically it was a clean install. I plugged in an external HD and the LED glowed indicating that it is powered. Nothing happened after that. It isnt mounted at all. I tried a USB flash drive and that didnt work either. Can someone tell me what is wrong? here is an output of my dmesg.



[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000ce000 size: 0000000000002000 end: 00000000000d0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000000f5e0000 end: 000000000f6e0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000f6e0000 size: 000000000000c000 end: 000000000f6ec000 type: 3
[    0.000000] copy_e820_map() start: 000000000f6ec000 size: 0000000000014000 end: 000000000f700000 type: 4
[    0.000000] copy_e820_map() start: 000000000f700000 size: 0000000000900000 end: 0000000010000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec10000 size: 0000000000010000 end: 00000000fec20000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff800000 size: 0000000000400000 end: 00000000ffc00000 type: 2
[    0.000000] copy_e820_map() start: 00000000fffffc00 size: 0000000000000400 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000f6e0000 (usable)
[    0.000000]  BIOS-e820: 000000000f6e0000 - 000000000f6ec000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000f6ec000 - 000000000f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000f700000 - 0000000010000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 246MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 63200) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    63200
[    0.000000]   HighMem     63200 ->    63200
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    63200
[    0.000000] On node 0 totalpages: 63200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 461 pages used for memmap
[    0.000000]   Normal zone: 58643 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 ACER                                  ) @ 0x000f62e0
[    0.000000] ACPI: RSDT (v001 ACER   Kestrel  0x20020806  LTP 0x00000000) @ 0x0f6e66d8
[    0.000000] ACPI: FADT (v001 ACER   Kestrel  0x20020806 PTL  0x00000050) @ 0x0f6ebf2c
[    0.000000] ACPI: HPET (v001 ACER   Kestrel  0x20020806 PTL  0x00000000) @ 0x0f6ebfa0
[    0.000000] ACPI: BOOT (v001 ACER   Kestrel  0x20020806  LTP 0x00000001) @ 0x0f6ebfd8
[    0.000000] ACPI: DSDT (v001 ACER   Kestrel  0x20020806 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0x0
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:eec10000)
[    0.000000] Detected 1598.661 MHz processor.
[    9.517469] Built 1 zonelists.  Total pages: 62707
[    9.517474] Kernel command line: root=UUID=1a97343a-e3ed-48e2-9db4-ea67228fb1aa ro quiet splash
[    9.517646] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    9.517652] mapped APIC to ffffd000 (011fa000)
[    9.517656] Enabling fast FPU save and restore... done.
[    9.517659] Enabling unmasked SIMD FPU exception support... done.
[    9.517669] Initializing CPU#0
[    9.517741] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    9.519191] Console: colour VGA+ 80x25
[    9.519314] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.519424] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    9.525135] Memory: 239296k/252800k available (1992k kernel code, 12892k reserved, 893k data, 328k init, 0k highmem)
[    9.525145] virtual kernel memory layout:
[    9.525146]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    9.525147]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    9.525149]     vmalloc : 0xd0000000 - 0xff7fe000   ( 759 MB)
[    9.525150]     lowmem  : 0xc0000000 - 0xcf6e0000   ( 246 MB)
[    9.525151]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[    9.525153]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[    9.525154]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[    9.525158] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    9.601679] Calibrating delay using timer specific routine.. 3199.37 BogoMIPS (lpj=6398757)
[    9.601724] Security Framework v1.0.0 initialized
[    9.601735] SELinux:  Disabled at boot.
[    9.601752] Mount-cache hash table entries: 512
[    9.601913] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[    9.601927] CPU: L1 I cache: 32K, L1 D cache: 32K
[    9.601930] CPU: L2 cache: 2048K
[    9.601933] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
[    9.601944] Compat vDSO mapped to ffffe000.
[    9.601949] Remapping vsyscall page to ffffe000
[    9.601961] Checking 'hlt' instruction... OK.
[    9.617794] SMP alternatives: switching to UP code
[    9.618050] Freeing SMP alternatives: 11k freed
[    9.618257] Early unpacking initramfs... done
[    9.976158] ACPI: Core revision 20060707
[    9.976846] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    9.978967] ACPI: setting ELCR to 0200 (from 0440)
[   10.016610] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 06
[   10.016617] SMP motherboard not detected.
[   10.016619] Local APIC not detected. Using dummy APIC emulation.
[   10.016654] Brought up 1 CPUs
[   10.016897] Booting paravirtualized kernel on bare hardware
[   10.016962] Time: 15:05:46  Date: 04/05/107
[   10.016989] NET: Registered protocol family 16
[   10.017070] EISA bus registered
[   10.017075] ACPI: bus type pci registered
[   10.018189] PCI: PCI BIOS revision 2.10 entry at 0xfd792, last bus=2
[   10.018192] PCI: Using configuration type 1
[   10.018194] Setting up standard PCI resources
[   10.034911] ACPI: Interpreter enabled
[   10.034914] ACPI: Using PIC for interrupt routing
[   10.035139] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.035143] PCI: Probing PCI hardware (bus 00)
[   10.036037] Boot video device is 0000:00:02.0
[   10.036322] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   10.036326] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[   10.036731] PCI: Transparent bridge - 0000:00:1e.0
[   10.036780] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[   10.036783] Please report the result to linux-kernel to fix this permanently
[   10.036798] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   10.039341] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   10.040260] ACPI: PCI Interrupt Link [LNKA] (IRQs *6)
[   10.040494] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[   10.040727] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[   10.040960] ACPI: PCI Interrupt Link [LNKD] (IRQs *6)
[   10.041191] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[   10.041432] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[   10.041665] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *0, disabled.
[   10.041896] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[   10.061812] ACPI: Power Resource [PFN0] (off)
[   10.061920] ACPI: Power Resource [PFN1] (off)
[   10.061961] Linux Plug and Play Support v0.97 (c) Adam Belay
[   10.061973] pnp: PnP ACPI init
[   10.066402] pnp: PnP ACPI: found 11 devices
[   10.066406] PnPBIOS: Disabled by ACPI PNP
[   10.066443] PCI: Using ACPI for IRQ routing
[   10.066445] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.071923] NET: Registered protocol family 8
[   10.071925] NET: Registered protocol family 20
[   10.072010] pnp: 00:04: ioport range 0x164e-0x164f has been reserved
[   10.072262] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   10.072273] PCI: Bus 3, cardbus bridge: 0000:02:06.0
[   10.072276]   IO window: 00003000-000030ff
[   10.072280]   IO window: 00003400-000034ff
[   10.072284]   PREFETCH window: 20000000-23ffffff
[   10.072288]   MEM window: 28000000-2bffffff
[   10.072292] PCI: Bridge: 0000:00:1e.0
[   10.072295]   IO window: 3000-3fff
[   10.072300]   MEM window: e0200000-e05fffff
[   10.072304]   PREFETCH window: 20000000-25ffffff
[   10.072316] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   10.072327] PCI: Enabling device 0000:02:06.0 (0104 -> 0107)
[   10.072507] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[   10.072510] PCI: setting IRQ 10 as level-triggered
[   10.072513] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[   10.072537] NET: Registered protocol family 2
[   10.101333] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   10.101401] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   10.101454] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   10.101483] TCP: Hash tables configured (established 8192 bind 4096)
[   10.101486] TCP reno registered
[   10.113378] checking if image is initramfs... it is
[   10.823274] Freeing initrd memory: 7011k freed
[   10.824141] Simple Boot Flag at 0x37 set to 0x1
[   10.824457] audit: initializing netlink socket (disabled)
[   10.824473] audit(1178377546.456:1): initialized
[   10.824605] VFS: Disk quotas dquot_6.5.1
[   10.824625] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.824677] io scheduler noop registered
[   10.824680] io scheduler anticipatory registered
[   10.824682] io scheduler deadline registered
[   10.824692] io scheduler cfq registered (default)
[   10.825019] isapnp: Scanning for PnP cards...
[   11.178475] isapnp: No Plug & Play device found
[   11.203295] Real Time Clock Driver v1.12ac
[   11.203356] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.203473] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   11.203609] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[   11.204218] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   11.204670] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   11.204674] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   11.204684] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   11.204767] mice: PS/2 mouse device common for all mice
[   11.205321] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.205534] input: Macintosh mouse button emulation as /class/input/input0
[   11.205575] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   11.205579] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   11.205802] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOU2] at 0x60,0x64 irq 1,12
[   11.210627] i8042.c: Detected active multiplexing controller, rev 1.1.
[   11.212503] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.212507] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   11.212510] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   11.212512] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   11.212515] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   11.212634] EISA: Probing bus 0 at eisa.0
[   11.212642] Cannot allocate resource for EISA slot 1
[   11.212645] Cannot allocate resource for EISA slot 2
[   11.212648] Cannot allocate resource for EISA slot 3
[   11.212668] EISA: Detected 0 cards.
[   11.242748] TCP cubic registered
[   11.242757] NET: Registered protocol family 1
[   11.242779] Using IPI No-Shortcut mode
[   11.242831] ACPI: (supports S0 S3 S4 S5)
[   11.242871]   Magic number: 7:471:82
[   11.243195] Freeing unused kernel memory: 328k freed
[   11.244379] Time: tsc clocksource has been installed.
[   11.259478] input: AT Translated Set 2 keyboard as /class/input/input1
[   12.456766] Capability LSM initialized
[   12.484594] ACPI: Transitioning device [FAN0] to D3
[   12.484598] ACPI: Transitioning device [FAN0] to D3
[   12.484601] ACPI: Fan [FAN0] (off)
[   12.484706] ACPI: Transitioning device [FAN1] to D3
[   12.484708] ACPI: Transitioning device [FAN1] to D3
[   12.484711] ACPI: Fan [FAN1] (off)
[   12.488786] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   12.488792] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.952000] ACPI: Thermal Zone [THRM] (62 C)
[    2.956000] Time: acpi_pm clocksource has been installed.
[    3.292000] usbcore: registered new interface driver usbfs
[    3.292000] usbcore: registered new interface driver hub
[    3.292000] usbcore: registered new device driver usb
[    3.296000] USB Universal Host Controller Interface driver v3.0
[    3.296000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 6
[    3.296000] PCI: setting IRQ 6 as level-triggered
[    3.296000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 6 (level, low) -> IRQ 6
[    3.296000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.296000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.296000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.296000] uhci_hcd 0000:00:1d.0: irq 6, io base 0x00001820
[    3.296000] usb usb1: configuration #1 chosen from 1 choice
[    3.296000] hub 1-0:1.0: USB hub found
[    3.296000] hub 1-0:1.0: 2 ports detected
[    3.348000] SCSI subsystem initialized
[    3.352000] libata version 2.20 loaded.
[    3.396000] ieee1394: Initialized config rom entry `ip1394'
[    3.400000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
[    3.400000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
[    3.400000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.400000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.400000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.400000] uhci_hcd 0000:00:1d.1: irq 6, io base 0x00001840
[    3.400000] usb usb2: configuration #1 chosen from 1 choice
[    3.400000] hub 2-0:1.0: USB hub found
[    3.400000] hub 2-0:1.0: 2 ports detected
[    3.504000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 6
[    3.504000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 6 (level, low) -> IRQ 6
[    3.504000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.504000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.504000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.504000] uhci_hcd 0000:00:1d.2: irq 6, io base 0x00001860
[    3.504000] usb usb3: configuration #1 chosen from 1 choice
[    3.504000] hub 3-0:1.0: USB hub found
[    3.504000] hub 3-0:1.0: 2 ports detected
[    3.608000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    3.608000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[    3.608000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.608000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.608000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    3.608000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.608000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.608000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xe0100000
[    3.612000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.612000] usb usb4: configuration #1 chosen from 1 choice
[    3.612000] hub 4-0:1.0: USB hub found
[    3.612000] hub 4-0:1.0: 6 ports detected
[    3.716000] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.716000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    3.716000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 6 (level, low) -> IRQ 6
[    3.716000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.716000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    3.716000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    3.716000] scsi0 : ata_piix
[    3.880000] ata1.00: ata_hpa_resize 1: sectors = 78140160, hpa_sectors = 78140160
[    3.880000] ata1.00: ATA-6: HTS424040M9AT00, MA2OA71A, max UDMA/100
[    3.880000] ata1.00: 78140160 sectors, multi 16: LBA48 
[    3.888000] ata1.00: ata_hpa_resize 1: sectors = 78140160, hpa_sectors = 78140160
[    3.888000] ata1.00: configured for UDMA/100
[    3.888000] scsi1 : ata_piix
[    4.128000] usb 4-4: new high speed USB device using ehci_hcd and address 2
[    4.208000] ata2.00: ATAPI, max UDMA/33
[    4.264000] usb 4-4: configuration #1 chosen from 1 choice
[    4.372000] ata2.00: configured for UDMA/33
[    4.372000] scsi 0:0:0:0: Direct-Access     ATA      HTS424040M9AT00  MA2O PQ: 0 ANSI: 5
[    4.372000] scsi 1:0:0:0: CD-ROM            QSI      CDRW/DVD SBW242C UQ81 PQ: 0 ANSI: 5
[    4.376000] b44.c:v1.01 (Jun 16, 2006)
[    4.376000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
[    4.376000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:c0:9f:70:67:43
[    4.376000] ACPI: PCI Interrupt 0000:02:06.2[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[    4.428000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[e020a000-e020a7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.440000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[    4.440000] sda: Write Protect is off
[    4.440000] sda: Mode Sense: 00 3a 00 00
[    4.440000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.440000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[    4.440000] sda: Write Protect is off
[    4.440000] sda: Mode Sense: 00 3a 00 00
[    4.440000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.440000]  sda: sda1 sda2 sda3 sda4
[    4.504000] sd 0:0:0:0: Attached scsi disk sda
[    4.508000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.508000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.512000] sr0: scsi3-mmc drive: 1x/24x writer cd/rw xa/form2 cdda tray
[    4.512000] Uniform CD-ROM driver Revision: 3.20
[    4.512000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.540000] usb 4-6: new high speed USB device using ehci_hcd and address 3
[    4.996000] Attempting manual resume
[    4.996000] swsusp: Resume From Partition 8:4
[    4.996000] PM: Checking swsusp image.
[    4.996000] PM: Resume from disk failed.
[    5.040000] kjournald starting.  Commit interval 5 seconds
[    5.040000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.700000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f00003581d5]
[    6.652000] usb 4-6: configuration #1 chosen from 1 choice
[    6.700000] usbcore: registered new interface driver libusual
[    7.232000] Initializing USB Mass Storage driver...
[    7.232000] scsi2 : SCSI emulation for USB Mass Storage devices
[    7.232000] usb-storage: device found at 2
[    7.232000] usb-storage: waiting for device to settle before scanning
[    7.232000] scsi3 : SCSI emulation for USB Mass Storage devices
[    7.232000] usbcore: registered new interface driver usb-storage
[    7.232000] USB Mass Storage support registered.
[    7.232000] usb-storage: device found at 3
[    7.232000] usb-storage: waiting for device to settle before scanning
[   12.232000] usb-storage: device scan complete
[   12.232000] usb-storage: device scan complete
[   12.232000] scsi 3:0:0:0: Direct-Access     Generic  USB Disk         9.02 PQ: 0 ANSI: 2
[   12.232000] scsi 2:0:0:0: Direct-Access     OTi      Flash Disk       2.00 PQ: 0 ANSI: 2
[   12.232000] SCSI device sdb: 39070080 512-byte hdwr sectors (20004 MB)
[   12.232000] sdb: Write Protect is off
[   12.232000] sdb: Mode Sense: 03 00 00 00
[   12.232000] sdb: assuming drive cache: write through
[   12.232000] SCSI device sdb: 39070080 512-byte hdwr sectors (20004 MB)
[   12.236000] sdb: Write Protect is off
[   12.236000] sdb: Mode Sense: 03 00 00 00
[   12.236000] sdb: assuming drive cache: write through
[   12.236000]  sdb: sdb1
[   12.260000] sd 3:0:0:0: Attached scsi disk sdb
[   12.260000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   12.264000] SCSI device sdc: 512000 512-byte hdwr sectors (262 MB)
[   12.264000] sdc: Write Protect is off
[   12.264000] sdc: Mode Sense: 03 00 00 00
[   12.264000] sdc: assuming drive cache: write through
[   12.264000] SCSI device sdc: 512000 512-byte hdwr sectors (262 MB)
[   12.268000] sdc: Write Protect is off
[   12.268000] sdc: Mode Sense: 03 00 00 00
[   12.268000] sdc: assuming drive cache: write through
[   12.268000]  sdc: sdc1
[   12.268000] sd 2:0:0:0: Attached scsi removable disk sdc
[   12.268000] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   20.856000] NET: Registered protocol family 10
[   20.856000] lo: Disabled Privacy Extensions
[   20.856000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.948000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.956000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.280000] intel_rng: FWH not detected
[   22.336000] Linux agpgart interface v0.102 (c) Dave Jones
[   22.352000] iTCO_vendor_support: vendor-support=0
[   22.356000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   22.356000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   22.356000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   22.372000] agpgart: Detected an Intel 855 Chipset.
[   22.372000] agpgart: Detected 8060K stolen memory.
[   22.380000] agpgart: AGP aperture is 128M @ 0xe8000000
[   23.108000] Yenta: CardBus bridge found at 0000:02:06.0 [1025:0064]
[   23.108000] Yenta: Enabling burst memory read transactions
[   23.108000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   23.108000] Yenta: Routing CardBus interrupts to PCI
[   23.108000] Yenta TI: socket 0000:02:06.0, mfunc 0x01a21b22, devctl 0x64
[   23.172000] ieee80211_crypt: registered algorithm 'NULL'
[   23.188000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   23.188000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   23.232000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   23.232000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   23.340000] Yenta: ISA IRQ mask 0x08b8, PCI irq 10
[   23.340000] Socket status: 30000006
[   23.340000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   23.340000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   23.340000] cs: IO port probe 0x3000-0x3fff: clean.
[   23.340000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe05fffff
[   23.340000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x25ffffff
[   23.340000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   23.340000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   23.460000] parport: PnPBIOS parport detected.
[   23.460000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   23.652000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   23.680000] ACPI: PCI Interrupt 0000:02:06.3[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[   23.824000] irda_init()
[   23.824000] NET: Registered protocol family 23
[   23.868000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   23.912000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   23.968000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   23.968000] nsc-ircc, chip->init
[   23.968000] nsc-ircc, Found chip at base=0x164e
[   23.968000] nsc-ircc, driver loaded (Dag Brattli)
[   23.968000] nsc_ircc_open(), can't get iobase of 0x2f8
[   23.968000] nsc-ircc, Found chip at base=0x164e
[   23.968000] nsc-ircc, driver loaded (Dag Brattli)
[   23.968000] nsc_ircc_open(), can't get iobase of 0x2f8
[   23.968000] pnp: Device 00:0a disabled.
[   24.048000] cs: IO port probe 0x100-0x3af: clean.
[   24.048000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   24.048000] cs: IO port probe 0x820-0x8ff: clean.
[   24.052000] cs: IO port probe 0xc00-0xcf7: clean.
[   24.052000] cs: IO port probe 0xa00-0xaff: clean.
[   24.156000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   24.156000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   24.472000] intel8x0_measure_ac97_clock: measured 54123 usecs
[   24.472000] intel8x0: clocking to 48000
[   24.624000] fuse init (API version 7.8)
[   24.660000] lp0: using parport0 (interrupt-driven).
[   24.712000] Adding 867500k swap on /dev/disk/by-uuid/da271254-066a-46f4-b1a0-75ba2c4b494f.  Priority:-1 extents:1 across:867500k
[   24.924000] NET: Registered protocol family 17
[   24.972000] EXT3 FS on sda3, internal journal
[   25.464000] kjournald starting.  Commit interval 5 seconds
[   25.464000] EXT3 FS on sda1, internal journal
[   25.464000] EXT3-fs: mounted filesystem with ordered data mode.
[   30.044000] **WARNING** I2C adapter driver [] forgot to specify physical device; fix it!
[   30.044000] ACPI: EC HC smbus [SMBC]
[   30.196000] Using specific hotkey driver
[   30.232000] ibm_acpi: ec object not found
[   30.284000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   30.296000] No dock devices found.
[   31.196000] ACPI: Smart Battery System [SBS0]
[   31.288000] input: Power Button (FF) as /class/input/input3
[   31.292000] ACPI: Power Button (FF) [PWRF]
[   31.352000] input: Lid Switch as /class/input/input4
[   31.356000] ACPI: Lid Switch [LID]
[   31.356000] input: Sleep Button (CM) as /class/input/input5
[   31.356000] ACPI: Sleep Button (CM) [SLPB]
[   31.524000] pcc_acpi: loading...
[   34.184000] ttyS1: LSR safety check engaged!
[   34.628000] eth1: no IPv6 routers present
[   36.312000] [drm] Initialized drm 1.1.0 20060810
[   36.316000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 6 (level, low) -> IRQ 6
[   36.320000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   36.320000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   36.988000] ppdev: user-space parallel port driver
[   37.860000] apm: BIOS not found.
[   38.060000] Bluetooth: Core ver 2.11
[   38.060000] NET: Registered protocol family 31
[   38.060000] Bluetooth: HCI device and connection manager initialized
[   38.060000] Bluetooth: HCI socket layer initialized
[   38.088000] Bluetooth: L2CAP ver 2.8
[   38.088000] Bluetooth: L2CAP socket layer initialized
[   38.192000] Bluetooth: RFCOMM socket layer initialized
[   38.192000] Bluetooth: RFCOMM TTY layer initialized
[   38.192000] Bluetooth: RFCOMM ver 1.8
[  103.676000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  120.520000] eth1: no IPv6 routers present

---

### Post by nobodie on 2007-05-15
I'm sorry I took so long to get to this. I have a similar problem and am in the process of working it out.

Here are the first steps:

Open Applications>accessories>terminal
type (# means "enter"):

ls /media #

you should see a list of the various drives on your system. choose the one you want to work with, for fun I will call it "sdc1" but it might have another name for you. now type:

sudo chown <your username> /dev/sdc1#

this should change the ownership to you. to check type:

mount /dev/sdc1#

and your device should popup on the screen and you should have an icon on the desktop.

repeat with any other devices based on their listing in "ls /media" above.

Now, here is the problem I am still having: if i try to change the ownership (that's "chown") in "/media" it won't change. I can manually mount the device using the "/dev" mount above, but when I restart and reload I have to remount because it looks to the "/media" file to automount. It doesn't want to accept a "chown" in "/media". 

If you can get it to accept it (sudo chown <username> /media/sdc1) then you should and you are good to go.

good luck and I'll check back once I get it fixed

---

