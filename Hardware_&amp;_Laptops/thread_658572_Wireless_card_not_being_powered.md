---
title: "Wireless card not being powered?"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by Kreuger on 2008-01-04
Alright so the other day my wireless card which is PCMCIA stopped working. The lights on it don't come on anymore and I can't seem to get it detected by Ubuntu (feisty) at all. I can still get a wired connection so I'm not sure what's wrong. I thought maybe because I've had trouble sticking the card into the slot lately that I bent a pin or something but seeing as it was in for a few days without being removed at all, I can't see how that could've ruined it. It was working one day and the next it stopped. It really doesn't make sense to me at all. I didn't change anything at all on the computer. The only thing I had done is used msn and copied a few music files from it to my desktop.

dmesg shows:
> [ 0.000000] Linux version 2.6.20-16-386 (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 Tue Dec 18 05:41:44 UTC 2007 (Ubuntu 2.6.20-16.33-386)
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] sanitize start
[ 0.000000] sanitize end
[ 0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
[ 0.000000] copy_e820_map() type is E820_RAM
[ 0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
[ 0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[ 0.000000] copy_e820_map() start: 0000000000100000 size: 000000001f670000 end: 000000001f770000 type: 1
[ 0.000000] copy_e820_map() type is E820_RAM
[ 0.000000] copy_e820_map() start: 000000001f770000 size: 000000000000e000 end: 000000001f77e000 type: 3
[ 0.000000] copy_e820_map() start: 000000001f77e000 size: 0000000000002000 end: 000000001f780000 type: 4
[ 0.000000] copy_e820_map() start: 000000001f780000 size: 0000000000880000 end: 0000000020000000 type: 2
[ 0.000000] copy_e820_map() start: 00000000ff800000 size: 0000000000800000 end: 0000000100000000 type: 2
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[ 0.000000] BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000001f770000 (usable)
[ 0.000000] BIOS-e820: 000000001f770000 - 000000001f77e000 (ACPI data)
[ 0.000000] BIOS-e820: 000000001f77e000 - 000000001f780000 (ACPI NVS)
[ 0.000000] BIOS-e820: 000000001f780000 - 0000000020000000 (reserved)
[ 0.000000] BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[ 0.000000] 0MB HIGHMEM available.
[ 0.000000] 503MB LOWMEM available.
[ 0.000000] Entering add_active_range(0, 0, 128880) 0 entries of 256 used
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0 -> 4096
[ 0.000000] Normal 4096 -> 128880
[ 0.000000] HighMem 128880 -> 128880
[ 0.000000] early_node_map[1] active PFN ranges
[ 0.000000] 0: 0 -> 128880
[ 0.000000] On node 0 totalpages: 128880
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 4064 pages, LIFO batch:0
[ 0.000000] Normal zone: 974 pages used for memmap
[ 0.000000] Normal zone: 123810 pages, LIFO batch:31
[ 0.000000] HighMem zone: 0 pages used for memmap
[ 0.000000] DMI present.
[ 0.000000] ACPI: RSDP (v002 IBM ) @ 0x000f7090
[ 0.000000] ACPI: XSDT (v001 IBM TP-1K 0x00001070 LTP 0x00000000) @ 0x1f772a76
[ 0.000000] ACPI: FADT (v001 IBM TP-1K 0x00001070 IBM 0x00000001) @ 0x1f772b00
[ 0.000000] ACPI: SSDT (v001 IBM TP-1K 0x00001070 MSFT 0x0100000d) @ 0x1f772bb4
[ 0.000000] ACPI: ECDT (v001 IBM TP-1K 0x00001070 IBM 0x00000001) @ 0x1f77de13
[ 0.000000] ACPI: TCPA (v001 IBM TP-1K 0x00001070 PTL 0x00000001) @ 0x1f77de65
[ 0.000000] ACPI: BOOT (v001 IBM TP-1K 0x00001070 LTP 0x00000001) @ 0x1f77dfd8
[ 0.000000] ACPI: DSDT (v001 IBM TP-1K 0x00001070 MSFT 0x0100000d) @ 0x00000000
[ 0.000000] ACPI: PM-Timer IO Port: 0x1008
[ 0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:df800000)
[ 0.000000] Detected 1199.016 MHz processor.
[ 11.816894] Built 1 zonelists. Total pages: 127874
[ 11.816899] Kernel command line: root=UUID=696183fc-30e3-4360-b617-8ac28d15dcbe ro quiet splash vga=792
[ 11.817254] Local APIC disabled by BIOS -- you can enable it with "lapic"
[ 11.817266] mapped APIC to ffffd000 (013f2000)
[ 11.817273] Enabling fast FPU save and restore... done.
[ 11.817278] Enabling unmasked SIMD FPU exception support... done.
[ 11.817290] Initializing CPU#0
[ 11.817365] PID hash table entries: 2048 (order: 11, 8192 bytes)
[ 11.817475] Console: colour dummy device 80x25
[ 11.817988] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 11.818634] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 11.851726] Memory: 496584k/515520k available (1917k kernel code, 18360k reserved, 867k data, 328k init, 0k highmem)
[ 11.851745] virtual kernel memory layout:
[ 11.851747] fixmap : 0xfffa9000 - 0xfffff000 ( 344 kB)
[ 11.851750] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 11.851752] vmalloc : 0xe0000000 - 0xff7fe000 ( 503 MB)
[ 11.851755] lowmem : 0xc0000000 - 0xdf770000 ( 503 MB)
[ 11.851757] .init : 0xc03bc000 - 0xc040e000 ( 328 kB)
[ 11.851760] .data : 0xc02df4d8 - 0xc03b8434 ( 867 kB)
[ 11.851762] .text : 0xc0100000 - 0xc02df4d8 (1917 kB)
[ 11.851768] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 11.929368] Calibrating delay using timer specific routine.. 2399.64 BogoMIPS (lpj=4799288)
[ 11.929428] Security Framework v1.0.0 initialized
[ 11.929444] SELinux: Disabled at boot.
[ 11.929467] Mount-cache hash table entries: 512
[ 11.929655] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[ 11.929673] CPU: L1 I cache: 16K, L1 D cache: 16K
[ 11.929677] CPU: L2 cache: 512K
[ 11.929681] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[ 11.929695] Compat vDSO mapped to ffffe000.
[ 11.929702] Remapping vsyscall page to ffffe000
[ 11.929716] CPU: Intel Mobile Intel® Pentium® III CPU - M 1200MHz stepping 04
[ 11.929728] Checking 'hlt' instruction... OK.
[ 11.945870] Early unpacking initramfs... done
[ 12.645062] ACPI: Core revision 20060707
[ 12.645956] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[ 12.653518] ACPI: setting ELCR to 0200 (from 0800)
[ 12.663227] Booting paravirtualized kernel on bare hardware
[ 12.663324] Time: 19:48:25 Date: 00/03/108
[ 12.663388] NET: Registered protocol family 16
[ 12.663568] EISA bus registered
[ 12.663577] ACPI: bus type pci registered
[ 12.663905] PCI: PCI BIOS revision 2.10 entry at 0xfd90e, last bus=7
[ 12.663909] PCI: Using configuration type 1
[ 12.663912] Setting up standard PCI resources
[ 12.681004] ACPI: Interpreter enabled
[ 12.681011] ACPI: Using PIC for interrupt routing
[ 12.682210] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[ 12.683118] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[ 12.684023] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[ 12.684927] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[ 12.685839] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[ 12.686664] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[ 12.687489] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[ 12.688312] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[ 12.688877] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 12.688886] PCI: Probing PCI hardware (bus 00)
[ 12.690805] Boot video device is 0000:00:02.0
[ 12.691026] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[ 12.691031] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[ 12.691317] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[ 12.691366] PCI: Transparent bridge - 0000:00:1e.0
[ 12.691489] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 12.696574] ACPI: Power Resource [PUBS] (on)
[ 12.698385] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[ 12.701268] Linux Plug and Play Support v0.97 © Adam Belay
[ 12.701291] pnp: PnP ACPI init
[ 12.708107] pnp: PnP ACPI: found 12 devices
[ 12.708116] PnPBIOS: Disabled by ACPI PNP
[ 12.708204] PCI: Using ACPI for IRQ routing
[ 12.708212] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report
[ 12.714968] NET: Registered protocol family 8
[ 12.714972] NET: Registered protocol family 20
[ 12.716192] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[ 12.716216] PCI: Bus 2, cardbus bridge: 0000:01:00.0
[ 12.716220] IO window: 00003000-000030ff
[ 12.716226] IO window: 00003400-000034ff
[ 12.716231] PREFETCH window: f0000000-f3ffffff
[ 12.716237] MEM window: d4000000-d7ffffff
[ 12.716242] PCI: Bus 6, cardbus bridge: 0000:01:00.1
[ 12.716245] IO window: 00003800-000038ff
[ 12.716250] IO window: 00003c00-00003cff
[ 12.716256] PREFETCH window: f4000000-f7ffffff
[ 12.716261] MEM window: d8000000-dbffffff
[ 12.716266] PCI: Bridge: 0000:00:1e.0
[ 12.716270] IO window: 3000-7fff
[ 12.716276] MEM window: d0200000-dfffffff
[ 12.716282] PREFETCH window: f0000000-f7ffffff
[ 12.716300] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[ 12.717008] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[ 12.717014] PCI: setting IRQ 11 as level-triggered
[ 12.717020] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 12.717699] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[ 12.717704] ACPI: PCI Interrupt 0000:01:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[ 12.717754] NET: Registered protocol family 2
[ 12.757461] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[ 12.757597] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[ 12.757762] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[ 12.757848] TCP: Hash tables configured (established 16384 bind 8192)
[ 12.757852] TCP reno registered
[ 12.769567] checking if image is initramfs... it is
[ 14.102969] Freeing initrd memory: 10400k freed
[ 14.103500] Simple Boot Flag at 0x35 set to 0x1
[ 14.103826] audit: initializing netlink socket (disabled)
[ 14.103859] audit(1199389706.464:1): initialized
[ 14.104112] VFS: Disk quotas dquot_6.5.1
[ 14.104158] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 14.104268] io scheduler noop registered
[ 14.104274] io scheduler anticipatory registered
[ 14.104278] io scheduler deadline registered
[ 14.104298] io scheduler cfq registered (default)
[ 14.104812] isapnp: Scanning for PnP cards...
[ 14.457673] isapnp: No Plug & Play device found
[ 14.508295] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 14.510443] pnp: Device 00:09 activated.
[ 14.510729] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[ 14.511142] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[ 14.511158] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[ 14.511261] mice: PS/2 mouse device common for all mice
[ 14.512145] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 14.512592] input: Macintosh mouse button emulation as /class/input/input0
[ 14.512647] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 14.512654] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 14.512898] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[ 14.519849] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 14.519860] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 14.520112] EISA: Probing bus 0 at eisa.0
[ 14.520127] Cannot allocate resource for EISA slot 1
[ 14.520133] Cannot allocate resource for EISA slot 2
[ 14.520137] Cannot allocate resource for EISA slot 3
[ 14.520140] Cannot allocate resource for EISA slot 4
[ 14.520144] Cannot allocate resource for EISA slot 5
[ 14.520148] Cannot allocate resource for EISA slot 6
[ 14.520152] Cannot allocate resource for EISA slot 7
[ 14.520158] EISA: Detected 0 cards.
[ 14.550314] TCP cubic registered
[ 14.550331] NET: Registered protocol family 1
[ 14.550366] Using IPI Shortcut mode
[ 14.550466] ACPI: (supports S0 S3 S4 S5)
[ 14.550548] Magic number: 8:994:848
[ 14.550699] hash matches device ptyv0
[ 14.551184] Freeing unused kernel memory: 328k freed
[ 14.553021] input: AT Translated Set 2 keyboard as /class/input/input1
[ 14.553422] Time: tsc clocksource has been installed.
[ 14.660388] vesafb: framebuffer at 0xe0000000, mapped to 0xe0080000, using 6144k, total 8000k
[ 14.660397] vesafb: mode is 1024x768x32, linelength=4096, pages=1
[ 14.660402] vesafb: protected mode interface info at 00ff:44f0
[ 14.660405] vesafb: scrolling: redraw
[ 14.660410] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[ 14.703289] Console: switching to colour frame buffer device 128x48
[ 14.745756] fb0: VESA VGA frame buffer device
[ 15.893626] Capability LSM initialized
[ 15.916923] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[ 15.961663] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[ 15.961674] ACPI: Processor [CPU] (supports 8 throttling states)
[ 15.964565] ACPI: Thermal Zone [THM0] (52 C)
[ 16.064384] md: linear personality registered for level -1
[ 16.079071] md: multipath personality registered for level -4
[ 16.110928] md: raid0 personality registered for level 0
[ 16.118804] md: raid1 personality registered for level 1
[ 16.124615] raid5: automatically using best checksumming function: pIII_sse
[ 16.141324] pIII_sse : 2729.000 MB/sec
[ 16.141328] raid5: using function: pIII_sse (2729.000 MB/sec)
[ 16.209389] raid6: int32x1 360 MB/s
[ 16.277416] raid6: int32x2 431 MB/s
[ 16.345414] raid6: int32x4 350 MB/s
[ 16.413358] raid6: int32x8 305 MB/s
[ 16.481346] raid6: mmxx1 1091 MB/s
[ 16.549333] raid6: mmxx2 1301 MB/s
[ 16.617359] raid6: sse1x1 964 MB/s
[ 16.685358] raid6: sse1x2 1340 MB/s
[ 16.685362] raid6: using algorithm sse1x2 (1340 MB/s)
[ 16.685369] md: raid6 personality registered for level 6
[ 16.685372] md: raid5 personality registered for level 5
[ 16.685376] md: raid4 personality registered for level 4
[ 16.754891] md: raid10 personality registered for level 10
[ 17.377940] usbcore: registered new interface driver usbfs
[ 17.377999] usbcore: registered new interface driver hub
[ 17.378041] usbcore: registered new device driver usb
[ 17.380423] USB Universal Host Controller Interface driver v3.0
[ 17.380518] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 17.380538] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[ 17.380545] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 17.380808] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[ 17.380841] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[ 17.381024] usb usb1: configuration #1 chosen from 1 choice
[ 17.381066] hub 1-0:1.0: USB hub found
[ 17.381077] hub 1-0:1.0: 2 ports detected
[ 17.482480] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[ 17.482490] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[ 17.482508] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[ 17.482514] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 17.482555] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[ 17.482587] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[ 17.482743] usb usb2: configuration #1 chosen from 1 choice
[ 17.482790] hub 2-0:1.0: USB hub found
[ 17.482803] hub 2-0:1.0: 2 ports detected
[ 17.569609] ieee1394: Initialized config rom entry `ip1394'
[ 17.586496] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[ 17.586506] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[ 17.586525] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[ 17.586531] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 17.586574] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[ 17.586606] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[ 17.586765] usb usb3: configuration #1 chosen from 1 choice
[ 17.586813] hub 3-0:1.0: USB hub found
[ 17.586829] hub 3-0:1.0: 2 ports detected
[ 17.628983] e100: Intel® PRO/100 Network Driver, 3.5.17-k2-NAPI
[ 17.628990] e100: Copyright© 1999-2006 Intel Corporation
[ 17.726038] ACPI: PCI Interrupt 0000:01:00.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[ 17.779038] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11] MMIO=[d0201000-d02017ff] Max Packet=[2048] IR/IT contexts=[4/4]
[ 17.787079] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[ 17.787084] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[ 17.818258] SCSI subsystem initialized
[ 17.834480] libata version 2.20 loaded.
[ 17.871130] e100: eth0: e100_probe: addr 0xd0200000, irq 11, MAC addr 00:09:6B:CD:3E:16
[ 17.876709] ata_piix 0000:00:1f.1: version 2.10ac1
[ 17.876734] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[ 17.876750] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[ 17.876777] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[ 17.876907] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
[ 17.876946] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
[ 17.876973] scsi0 : ata_piix
[ 6.200000] Time: acpi_pm clocksource has been installed.
[ 6.216000] ata1.00: ata_hpa_resize 1: sectors = 78140160, hpa_sectors = 78140160
[ 6.216000] ata1.00: ATA-5: IC25N040ATCS04-0, CA4OA71A, max UDMA/100
[ 6.216000] ata1.00: 78140160 sectors, multi 16: LBA
[ 6.224000] ata1.00: ata_hpa_resize 1: sectors = 78140160, hpa_sectors = 78140160
[ 6.224000] ata1.00: configured for UDMA/100
[ 6.224000] scsi1 : ata_piix
[ 6.380000] scsi 0:0:0:0: Direct-Access ATA IC25N040ATCS04-0 CA4O PQ: 0 ANSI: 5
[ 6.392000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[ 6.392000] sda: Write Protect is off
[ 6.392000] sda: Mode Sense: 00 3a 00 00
[ 6.392000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6.392000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[ 6.392000] sda: Write Protect is off
[ 6.392000] sda: Mode Sense: 00 3a 00 00
[ 6.392000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6.392000] sda: sda1 sda2 sda3 < sda5 >
[ 6.440000] sd 0:0:0:0: Attached scsi disk sda
[ 6.448000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 6.808000] kjournald starting. Commit interval 5 seconds
[ 6.808000] EXT3-fs: mounted filesystem with ordered data mode.
[ 7.236000] ieee1394: Host added: ID:BUS[0-00:1023] GUID[00061b0201202351]
[ 27.816000] iTCO_vendor_support: vendor-support=0
[ 27.816000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[ 27.816000] iTCO_wdt: Found a ICH3-M TCO device (Version=1, TCOBASE=0x1060)
[ 27.816000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[ 27.860000] intel_rng: FWH not detected
[ 27.884000] Linux agpgart interface v0.102 © Dave Jones
[ 27.888000] agpgart: Detected an Intel 830M Chipset.
[ 27.888000] agpgart: Detected 8060K stolen memory.
[ 27.900000] agpgart: AGP aperture is 128M @ 0xe0000000
[ 28.224000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 28.236000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 28.532000] input: PC Speaker as /class/input/input2
[ 29.368000] Real Time Clock Driver v1.12ac
[ 29.448000] Yenta: CardBus bridge found at 0000:01:00.0 [1014:0185]
[ 29.576000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[ 29.576000] Socket status: 30000006
[ 29.576000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[ 29.576000] cs: IO port probe 0x3000-0x7fff: clean.
[ 29.576000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xdfffffff
[ 29.576000] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf7ffffff
[ 29.576000] Yenta: CardBus bridge found at 0000:01:00.1 [1014:0185]
[ 29.704000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[ 29.704000] Socket status: 30000006
[ 29.704000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[ 29.704000] cs: IO port probe 0x3000-0x7fff: clean.
[ 29.704000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xdfffffff
[ 29.704000] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf7ffffff
[ 29.752000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[ 29.768000] input: TPPS/2 IBM TrackPoint as /class/input/input3
[ 30.100000] irda_init()
[ 30.100000] NET: Registered protocol family 23
[ 30.152000] parport: PnPBIOS parport detected.
[ 30.152000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[ 30.252000] pnp: Device 00:0b activated.
[ 30.252000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[ 30.252000] nsc-ircc, chip->init
[ 30.252000] nsc-ircc, Found chip at base=0x02e
[ 30.252000] nsc-ircc, driver loaded (Dag Brattli)
[ 30.252000] IrDA: Registered device irda0
[ 30.252000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[ 30.816000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[ 30.816000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[ 31.008000] cs: IO port probe 0x100-0x3af: clean.
[ 31.012000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[ 31.012000] cs: IO port probe 0x820-0x8ff: clean.
[ 31.012000] cs: IO port probe 0xc00-0xcf7: clean.
[ 31.012000] cs: IO port probe 0xa00-0xaff: clean.
[ 31.052000] cs: IO port probe 0x100-0x3af: clean.
[ 31.052000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[ 31.052000] cs: IO port probe 0x820-0x8ff: clean.
[ 31.052000] cs: IO port probe 0xc00-0xcf7: clean.
[ 31.052000] cs: IO port probe 0xa00-0xaff: clean.
[ 31.384000] intel8x0_measure_ac97_clock: measured 55421 usecs
[ 31.384000] intel8x0: clocking to 48000
[ 31.656000] lp0: using parport0 (interrupt-driven).
[ 31.808000] fuse init (API version 7.8)
[ 31.892000] ndiswrapper version 1.38 loaded (preempt=no,smp=no)
[ 32.004000] usbcore: registered new interface driver ndiswrapper
[ 32.228000] Adding 1028120k swap on /dev/disk/by-uuid/115e7025-78ed-4d79-aaf7-fb2263e266a5. Priority:-1 extents:1 across:1028120k
[ 32.332000] EXT3 FS on sda2, internal journal
[ 34.964000] Adding 1028120k swap on /dev/disk/by-uuid/115e7025-78ed-4d79-aaf7-fb2263e266a5. Priority:-2 extents:1 across:1028120k
[ 37.120000] ACPI: AC Adapter [AC] (off-line)
[ 37.204000] ACPI: Battery Slot [BAT0] (battery present)
[ 37.308000] input: Power Button (FF) as /class/input/input4
[ 37.328000] ACPI: Power Button (FF) [PWRF]
[ 37.396000] input: Lid Switch as /class/input/input5
[ 37.412000] ACPI: Lid Switch [LID]
[ 37.480000] input: Sleep Button (CM) as /class/input/input6
[ 37.480000] ACPI: Sleep Button (CM) [SLPB]
[ 37.788000] Using specific hotkey driver
[ 37.864000] ACPI: ACPI Dock Station Driver
[ 38.024000] ibm_acpi: ThinkPad EC firmware 1KHT16WW-1.04
[ 38.024000] ibm_acpi: IBM ThinkPad ACPI Extras v0.13
[ 38.024000] ibm_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[ 38.028000] ibm_acpi: bay device not present
[ 38.160000] ACPI: Video Device [VID] (multi-head: yes rom: no post: no)
[ 38.228000] pcc_acpi: loading...
[ 40.924000] IBM machine detected. Enabling interrupts during APM calls.
[ 40.924000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[ 40.924000] apm: overridden by ACPI.
[ 42.460000] Non-volatile memory driver v1.2
[ 44.308000] [drm] Initialized drm 1.1.0 20060810
[ 44.316000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 44.320000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[ 44.320000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[ 56.700000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 58.888000] NET: Registered protocol family 17
[ 61.476000] NET: Registered protocol family 10
[ 61.476000] lo: Disabled Privacy Extensions
[ 72.424000] eth0: no IPv6 routers present
[ 1851.832000] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[ 1851.832000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[ 1851.832000] pcmcia: see [http://www.kernel.org/pub/linux/utils/kern...cia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kern...cia/pcmcia.html) for details. But that page was of no help. Not sure what else to do. Hopefully I'll be able to test my card in another laptop tomorrow to see if that's the problem or if it's the laptop itself.

lspci shows:
> kreuger@kreuger-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
01:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
01:00.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller
01:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
kreuger@kreuger-laptop:~$ 
 Not sure what bridge it's using (or if there's any difference?) I only have the one PCMCIA slot on my laptop.

---

### Post by Kreuger on 2008-01-06
Anybody have any ideas?

---

### Post by Vadi on 2008-01-06
Are you using ndiswrapper for the card, or did it work out of the box?

---

### Post by Kreuger on 2008-01-06
ndiswrapper with the net8185.inf driver using [this tutorial]("http://ubuntuforums.org/showpost.php?p=2402378&postcount=16") but with the latest version of ndiswrapper of course. In that tutorial, at the end where it shows the lspci output, I don't see my card listed anymore (it was there when I first did it a few months ago)

---

### Post by Vadi on 2008-01-06
I got the same driver!

Do **sudo modprobe ndiswrapper**, that should get the lights back on.

---

### Post by Kreuger on 2008-01-06
Nope, no luck :( I checked before to see if it was loaded using lsmod and it seemed to be.

---

### Post by Vadi on 2008-01-06
Hrm. Do **sudo lshw -C network**, what does it report?

---

### Post by Kreuger on 2008-01-06
> kreuger@kreuger-laptop:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:cd:3e:16
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 1                               00bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion                               =3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.1.102 latency=66 link=yes ma                               xlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:d0200000-d0200fff ioport:7000-703f irq:11
kreuger@kreuger-laptop:~$ 
 I think that's just my wired?

---

### Post by Vadi on 2008-01-07
Yeah that is just your wired.

What card model?

---

### Post by Kreuger on 2008-01-07
Belkin F5D7010 Ver.7000 Wireless G

---

### Post by Vadi on 2008-01-07
Okay, I have exactly the same card.

Try the following steps:

sudo ndiswrapper -a 1799:701F net8185
sudo modprobe ndiswrapper
pullout / turnoff the wireless card, and put back in / turnon the card.

And sudo lshw -C network once more.

---

### Post by Kreuger on 2008-01-07
> kreuger@kreuger-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:cd:3e:16
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 1                               00bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion                               =3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.1.102 latency=66 link=yes ma                               xlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:d0200000-d0200fff ioport:7000-703f irq:11
kreuger@kreuger-laptop:~$ 

Looks like no difference. I had the card out and looked into the slot, looks like the pins are all fine but it has trouble sliding into the caddy, i think it's bent but I dont think that's the cause of the problem as when it was last working, it was in and not removed.

---

### Post by Vadi on 2008-01-08
I'm not sure then. Could you file this as a bug report on launchpad?

I'd try reinstalling ndiswrapper and the drivers in this case.

---

### Post by Kreuger on 2008-01-08
I have a feeling it's not really a problem with ubuntu so much as the hardware. I bought a desktop PCI to PCMCIA card off ebay so I can test it because the last laptop I tried it in, the slot seemed to not want to take the card all the way in but anyway, once that comes and I can test it..maybe I'll file a report anyway just to be sure

---

### Post by Kreuger on 2008-01-15
So I made a bug report on Launchpad a few days ago and nobody has replied. I guess nobody has much of a clue? My pcmcia to PCI adapter for my desktop should be here in a couple days so I'll be able to see if my card is still any good at least

---

### Post by Vadi on 2008-01-15
Possibly yes. The same card works for me okay (with encryption and everything).

---

### Post by Kreuger on 2008-01-16
Yeah it worked before. I just don't get why it stopped. I mean I could understand if I dropped it or spilt something on it or whatever, you know?

---

### Post by Kreuger on 2008-01-22
Okay so I got the adapter today and it seems to detect the card on my desktop. I take it that means there's something wrong with the laptop port?

> kreuger@kreuger-desktop:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge                                                                                                    (rev 80)
        Subsystem: ASUSTeK Computer Inc. A7V8X motherboard
        Flags: bus master, 66MHz, medium devsel, latency 0
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal                                                                                                    decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: dd000000-dfefffff
        Prefetchable memory behind bridge: dff00000-f7ffffff
        Capabilities: <access denied>

00:09.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell]                                                                                                    (rev 12)
        Subsystem: ASUSTeK Computer Inc. A7V600/P4P800/K8V motherboard
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
        Memory at dc800000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at d800 [size=256]
        Capabilities: <access denied>

00:0a.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 81)
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at 90000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 88000000-8bfff000 (prefetchable)
        Memory window 1: 8c000000-8ffff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

00:0e.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs SB Audigy 2 ZS (SB0350)
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at d400 [size=64]
        Capabilities: <access denied>

00:0e.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 32
        I/O ports at d000 [size=8]
        Capabilities: <access denied>

00:0e.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) (pr                                                                                                   og-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at dc000000 (32-bit, non-prefetchable) [size=2K]
        Memory at db800000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Control                                                                                                   ler (rev 80)
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V Deluxe/K8V-X/A8V Deluxe moth                                                                                                   erboard
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at b800 [size=8]
        I/O ports at b400 [size=4]
        I/O ports at b000 [size=8]
        I/O ports at a800 [size=4]
        I/O ports at a400 [size=16]
        I/O ports at a000 [size=256]
        Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/                                                                                                   C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 18
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at 9800 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller                                                                                                    (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at 9400 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller                                                                                                    (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at 9000 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller                                                                                                    (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at 8800 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller                                                                                                    (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at 8400 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHC                                                                                                   I])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at db000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T89                                                                                                   0 South]
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 A                                                                                                   C97 Audio Controller (rev 60)
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/K8V Deluxe motherboard (AD                                                                                                   I AD1980 codec [SoundMAX])
        Flags: medium devsel, IRQ 20
        I/O ports at e000 [size=256]
        Capabilities: <access denied>

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller                                                                                                    (rev 80)
        Flags: medium devsel, IRQ 20
        I/O ports at e500 [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev                                                                                                    a1) (prog-if 00 [VGA])
        Subsystem: Chaintech Computer Co. Ltd Unknown device 1974
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
        Memory at de000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at dffe0000 [disabled] [size=128K]
        Capabilities: <access denied>

[B]02:00.0 Ethernet controller: Belkin Unknown device 701f (rev 20)
        Subsystem: Belkin Unknown device 701f
        Flags: medium devsel, IRQ 16
        I/O ports at 1000 [disabled] [size=256]
        Memory at 8c000000 (32-bit, non-prefetchable) [disabled] [size=1K]
        Capabilities: <access denied>[/B]

kreuger@kreuger-desktop:~$ 


> 
kreuger@kreuger-desktop:~$ sudo lshw -C network
[sudo] password for kreuger:
  *-network               
       description: Ethernet interface
       product: 3c940 10/100/1000Base-T [Marvell]
       vendor: 3Com Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 12
       serial: 00:0c:6e:e1:c0:87
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.11 duplex=full firmware=N/A ip=192.168.1.101 latency=32 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: Belkin
       vendor: Belkin
       physical id: 1
       bus info: pci@0000:02:00.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0 maxlatency=64 mingnt=32
kreuger@kreuger-desktop:~$ 


---

### Post by Vadi on 2008-01-23
Oh. I really hate that network unclaimed thing.

I think I solved it by doing "sudo modprobe ndiswrapper" and try reinserting the card. What we're looking for is this:

> $ sudo lshw -C network
[sudo] password for vadi:
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:0d:60:5d:5d:6d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: Belkin
       vendor: Belkin
       physical id: 1
       bus info: pci@0000:03:00.0
       **logical name:** wlan0
       version: 20
       serial: 00:17:3f:2f:ef:99
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.51+Realtek,02/01/2007,5.1097.0 ip=(edit) latency=64 link=yes maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

And also do sudo ndiswrapper -l if that doesn't work, it should show the net8185 driver installed.

---

### Post by rosegarden78 on 2008-01-23
You say you check it's there in lsmod like not turned on?  Did you check roaming mode in Settings - Network?  Do you have wireless bars in system dock or do you need to run Network Manager by typing nm-applet?  I don't know sounds like software somewhere turning it off.

---

### Post by Kreuger on 2008-01-23
I use the network manager. I'll have a look in the roaming mode but I can't even get the card to go into the slot, I think the caddy might be bent in some place. My wired connection was set to roaming mode so I put it back to DHCP like it should be.

---

### Post by grogger13 on 2008-01-23
do you use ndisgtk- the gtk front end for ndiswrapper

Try installing it if you haven't and see if the wireless driver is in the list and that it says hardware present.  My wireless card light at start up doesn't go on but in ndisgtk it still says hardware present. I have to uninstall it then reinstall it before the light goes on and its detected by the system.  I still haven't been able to fix it so i can't give you a solutions, but it might help to know this.

---

### Post by Kreuger on 2008-01-23
I tried using that today and after I click install the driver, nothing happens. I got the card into the slot again though. But for some reason my laptop stopped working. Whenever I tried to run a program nothing happens so I tried from terminal and it kept saying -bash /usr/bin/_appname_ input/output error. I restarted and it was very slow and nothing seemed to be loading so I pulled out the card and rebooted again and it seems to be working but still very slow.

---

