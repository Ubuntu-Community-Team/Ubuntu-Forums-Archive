---
title: "Serial ATA Liteon DVD Burner is not recognized"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by MrMinute on 2007-02-08
I am using Ubuntu Edgy for some time without any problem installed on a SATA harddisk connected to an external SATA controller with Sil3112 chipset. Yesterday I purchased a Liteon SH-16A DVD burner with SATA interface. After I connected it to the SATA controller Ubuntu Edgy did not boot anymore. It stops directly after the splash screen shows up and does not do any disk activity. Also other distributions had problems accessing the harddisk which was either very slow or did not worked out at all. (Sorry, don't have the exact error messages, it was asking to use irqpoll kernel option and might had some IRQ problems but I did not managed to solve it.) Disconnecting the DVD burner again solved the problem. Windows also installed on the same SATA harddisk runs without any problem and is able to use the DVD burner. Next I upgraded the kernel to 2.6.20 from Feisty and Ubuntu does boot again and runs quite very well. But it seems not to recognize the SATA DVD burner at all. I could also not find any usefull error message. Any help is very appreciated!! The file /var/log/dmesg and output from "lspci -vv" are following:

**_Interesting entry from "lspci -vv":_**
00:0c.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 01)
        Subsystem: Silicon Image, Inc. SiI 3112 SATARaid Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at a800 [size=8]
        Region 1: I/O ports at a400 [size=4]
        Region 2: I/O ports at a000 [size=8]
        Region 3: I/O ports at 9800 [size=4]
        Region 4: I/O ports at 9400 [size=16]
        Region 5: Memory at d4000000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 20000000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 2
                Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-

**_/var/log/dmesg_**
[    0.000000] Linux version 2.6.20-6-generic (root@palmer) (gcc version 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)) #2 SMP Wed Jan 31 20:53:39 UTC 2007 (Ubuntu 2.6.20-6.11-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001beec000 end: 000000001bfec000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001bfec000 size: 0000000000003000 end: 000000001bfef000 type: 3
[    0.000000] copy_e820_map() start: 000000001bfef000 size: 0000000000010000 end: 000000001bfff000 type: 2
[    0.000000] copy_e820_map() start: 000000001bfff000 size: 0000000000001000 end: 000000001c000000 type: 4
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001bfec000 (usable)
[    0.000000]  BIOS-e820: 000000001bfec000 - 000000001bfef000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001bfef000 - 000000001bfff000 (reserved)
[    0.000000]  BIOS-e820: 000000001bfff000 - 000000001c000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 447MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 114668) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   114668
[    0.000000]   HighMem    114668 ->   114668
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   114668
[    0.000000] On node 0 totalpages: 114668
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 863 pages used for memmap
[    0.000000]   Normal zone: 109709 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f5a90
[    0.000000] ACPI: RSDT (v001 ASUS   CUBX-L   0x30303031 MSFT 0x31313031) @ 0x1bfec000
[    0.000000] ACPI: FADT (v001 ASUS   CUBX-L   0x30303031 MSFT 0x31313031) @ 0x1bfec080
[    0.000000] ACPI: BOOT (v001 ASUS   CUBX-L   0x30303031 MSFT 0x31313031) @ 0x1bfec040
[    0.000000] ACPI: DSDT (v001   ASUS CUBX-L   0x00001000 MSFT 0x0100000b) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e3ff0000)
[    0.000000] Detected 1104.199 MHz processor.
[   27.656765] Built 1 zonelists.  Total pages: 113773
[   27.656774] Kernel command line: root=UUID=cac3a6b7-4b12-44f7-91a5-02cb33db0e81 ro quiet splash
[   27.657154] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   27.657176] mapped APIC to ffffd000 (0138a000)
[   27.657184] Enabling fast FPU save and restore... done.
[   27.657190] Enabling unmasked SIMD FPU exception support... done.
[   27.657211] Initializing CPU#0
[   27.657311] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   27.658908] Console: colour VGA+ 80x25
[   27.660165] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   27.661937] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   27.704592] Memory: 442724k/458672k available (1975k kernel code, 15420k reserved, 878k data, 324k init, 0k highmem)
[   27.704614] virtual kernel memory layout:
[   27.704616]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   27.704619]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   27.704622]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
[   27.704624]     lowmem  : 0xc0000000 - 0xdbfec000   ( 447 MB)
[   27.704627]       .init : 0xc03cf000 - 0xc0420000   ( 324 kB)
[   27.704630]       .data : 0xc02edd14 - 0xc03c96d4   ( 878 kB)
[   27.704632]       .text : 0xc0100000 - 0xc02edd14   (1975 kB)
[   27.704639] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   27.781264] Calibrating delay using timer specific routine.. 2209.89 BogoMIPS (lpj=4419795)
[   27.781349] Security Framework v1.0.0 initialized
[   27.781365] SELinux:  Disabled at boot.
[   27.781398] Mount-cache hash table entries: 512
[   27.781666] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   27.781687] CPU: L1 I cache: 16K, L1 D cache: 16K
[   27.781693] CPU: L2 cache: 256K
[   27.781699] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   27.781744] Checking 'hlt' instruction... OK.
[   27.797437] SMP alternatives: switching to UP code
[   27.797752] Freeing SMP alternatives: 11k freed
[   27.797903] ACPI: Core revision 20060707
[   27.800971] ACPI: setting ELCR to 0200 (from 0e20)
[   27.801340] CPU0: Intel Pentium III (Coppermine) stepping 0a
[   27.801352] SMP motherboard not detected.
[   27.801357] Local APIC not detected. Using dummy APIC emulation.
[   27.801453] Brought up 1 CPUs
[   27.801989] Booting paravirtualized kernel on bare hardware
[   27.802164] NET: Registered protocol family 16
[   27.802393] EISA bus registered
[   27.802405] ACPI: bus type pci registered
[   27.803872] PCI: PCI BIOS revision 2.10 entry at 0xf08c0, last bus=1
[   27.803877] PCI: Using configuration type 1
[   27.803881] Setting up standard PCI resources
[   27.817148] ACPI: Interpreter enabled
[   27.817160] ACPI: Using PIC for interrupt routing
[   27.818360] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   27.818759] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   27.819142] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   27.819524] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   27.819845] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   27.819858] PCI: Probing PCI hardware (bus 00)
[   27.820200] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   27.820678] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   27.820682] * this clock source is slow. Consider trying other clock sources
[   27.820726] PCI quirk: region e400-e43f claimed by PIIX4 ACPI
[   27.820733] PCI quirk: region e800-e80f claimed by PIIX4 SMB
[   27.821193] Boot video device is 0000:01:00.0
[   27.821270] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   27.831212] Linux Plug and Play Support v0.97 (c) Adam Belay
[   27.831239] pnp: PnP ACPI init
[   27.838229] pnp: PnP ACPI: found 14 devices
[   27.838242] PnPBIOS: Disabled by ACPI PNP
[   27.838359] PCI: Using ACPI for IRQ routing
[   27.838366] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   27.840151] PCI: BIOS reporting unknown device 00:58
[   27.840155] PCI: Device 0000:00:0b.1 not found by BIOS
[   27.841975] pnp: 00:03: ioport range 0xe400-0xe43f could not be reserved
[   27.841982] pnp: 00:03: ioport range 0xe800-0xe80f has been reserved
[   27.842530] PCI: Bridge: 0000:00:01.0
[   27.842536]   IO window: disabled.
[   27.842544]   MEM window: d6000000-d7dfffff
[   27.842551]   PREFETCH window: d7f00000-e3ffffff
[   27.842618] NET: Registered protocol family 2
[   27.881411] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   27.881613] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   27.882026] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   27.882280] TCP: Hash tables configured (established 16384 bind 8192)
[   27.882287] TCP reno registered
[   27.893558] checking if image is initramfs... it is
[   29.211732] Freeing initrd memory: 7779k freed
[   29.212252] Simple Boot Flag at 0x3a set to 0x1
[   29.212672] audit: initializing netlink socket (disabled)
[   29.212734] audit(1170940794.740:1): initialized
[   29.213029] VFS: Disk quotas dquot_6.5.1
[   29.213081] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   29.213196] io scheduler noop registered
[   29.213202] io scheduler anticipatory registered
[   29.213207] io scheduler deadline registered
[   29.213229] io scheduler cfq registered (default)
[   29.213248] Limiting direct PCI/PCI transfers.
[   29.213826] isapnp: Scanning for PnP cards...
[   29.567590] isapnp: No Plug & Play device found
[   29.636980] Real Time Clock Driver v1.12ac
[   29.637072] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   29.637281] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.637656] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   29.638879] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.639383] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   29.639885] mice: PS/2 mouse device common for all mice
[   29.641144] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   29.641539] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   29.641549] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   29.641980] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   29.644803] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.644814] serio: i8042 AUX port at 0x60,0x64 irq 12
[   29.645119] EISA: Probing bus 0 at eisa.0
[   29.645163] Cannot allocate resource for EISA slot 8
[   29.645167] EISA: Detected 0 cards.
[   29.675330] TCP cubic registered
[   29.675348] NET: Registered protocol family 1
[   29.675361] NET: Registered protocol family 8
[   29.675365] NET: Registered protocol family 20
[   29.675431] Using IPI No-Shortcut mode
[   29.675564] ACPI: (supports S0 S1 S4 S5)
[   29.676539] Time: tsc clocksource has been installed.
[   29.676787] Freeing unused kernel memory: 324k freed
[   29.696905] input: AT Translated Set 2 keyboard as /class/input/input0
[   31.213087] Capability LSM initialized
[   31.249541] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[   31.305131] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   31.305143] ACPI: Processor [CPU0] (supports 8 throttling states)
[   31.440802] md: linear personality registered for level -1
[   31.468409] md: multipath personality registered for level -4
[   31.474000] md: raid0 personality registered for level 0
[   31.481386] md: raid1 personality registered for level 1
[   31.486679] raid5: automatically using best checksumming function: pIII_sse
[   31.503800]    pIII_sse  :  2196.000 MB/sec
[   31.503805] raid5: using function: pIII_sse (2196.000 MB/sec)
[   31.575888] raid6: int32x1    338 MB/s
[   31.643886] raid6: int32x2    397 MB/s
[   31.711744] raid6: int32x4    320 MB/s
[   31.779850] raid6: int32x8    286 MB/s
[   31.847679] raid6: mmxx1     1001 MB/s
[   31.915671] raid6: mmxx2     1253 MB/s
[   31.983612] raid6: sse1x1     884 MB/s
[   32.051602] raid6: sse1x2    1242 MB/s
[   32.051606] raid6: using algorithm sse1x2 (1242 MB/s)
[   32.051613] md: raid6 personality registered for level 6
[   32.051618] md: raid5 personality registered for level 5
[   32.051622] md: raid4 personality registered for level 4
[   32.132670] md: raid10 personality registered for level 10
[   33.115895] SCSI subsystem initialized
[   33.130986] libata version 2.00 loaded.
[   33.140580] ata_piix 0000:00:04.1: version 2.00ac7
[   33.140721] ata1: PATA max UDMA/33 cmd 0x1F0 ctl 0x3F6 bmdma 0xD800 irq 14
[   33.140780] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0xD808 irq 15
[   33.140808] scsi0 : ata_piix
[   33.163054] usbcore: registered new interface driver usbfs
[   33.163099] usbcore: registered new interface driver hub
[   33.163169] usbcore: registered new device driver usb
[   33.166145] USB Universal Host Controller Interface driver v3.0
[   33.292661] ieee1394: Initialized config rom entry `ip1394'
[   33.451501] ata1.00: ATAPI, max UDMA/33
[   33.607398] ata1.00: configured for UDMA/33
[   33.607428] scsi1 : ata_piix
[    6.108000] Time: acpi_pm clocksource has been installed.
[    6.108000] scsi 0:0:0:0: CD-ROM            JLMS     XJ-HD163         GH5Y PQ: 0 ANSI: 5
[    6.116000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[    6.116000] PCI: setting IRQ 9 as level-triggered
[    6.116000] ACPI: PCI Interrupt 0000:00:04.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[    6.116000] uhci_hcd 0000:00:04.2: UHCI Host Controller
[    6.116000] uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
[    6.116000] uhci_hcd 0000:00:04.2: irq 9, io base 0x0000d400
[    6.120000] usb usb1: configuration #1 chosen from 1 choice
[    6.120000] hub 1-0:1.0: USB hub found
[    6.120000] hub 1-0:1.0: 2 ports detected
[    6.148000] sr0: scsi3-mmc drive: 0x/48x cd/rw xa/form2 cdda tray
[    6.148000] Uniform CD-ROM driver Revision: 3.20
[    6.148000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    6.160000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    6.224000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    6.224000] PCI: setting IRQ 10 as level-triggered
[    6.224000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[    6.224000] uhci_hcd 0000:00:0b.0: UHCI Host Controller
[    6.224000] uhci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    6.224000] uhci_hcd 0000:00:0b.0: irq 10, io base 0x0000b800
[    6.224000] usb usb2: configuration #1 chosen from 1 choice
[    6.224000] hub 2-0:1.0: USB hub found
[    6.224000] hub 2-0:1.0: 2 ports detected
[    6.328000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[    6.328000] PCI: setting IRQ 5 as level-triggered
[    6.328000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[    6.328000] uhci_hcd 0000:00:0b.1: UHCI Host Controller
[    6.328000] uhci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 3
[    6.328000] uhci_hcd 0000:00:0b.1: irq 5, io base 0x0000b400
[    6.328000] usb usb3: configuration #1 chosen from 1 choice
[    6.328000] hub 3-0:1.0: USB hub found
[    6.328000] hub 3-0:1.0: 2 ports detected
[    6.432000] ACPI: PCI Interrupt 0000:00:0b.2[C] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[    6.432000] ehci_hcd 0000:00:0b.2: EHCI Host Controller
[    6.432000] ehci_hcd 0000:00:0b.2: new USB bus registered, assigned bus number 4
[    6.432000] ehci_hcd 0000:00:0b.2: irq 9, io mem 0xd5000000
[    6.432000] ehci_hcd 0000:00:0b.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.432000] usb usb4: configuration #1 chosen from 1 choice
[    6.432000] hub 4-0:1.0: USB hub found
[    6.432000] hub 4-0:1.0: 4 ports detected
[    6.464000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    6.536000] ACPI: PCI Interrupt 0000:00:0b.3[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[    6.588000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[d4800000-d48007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.596000] sata_sil 0000:00:0c.0: version 2.0
[    6.596000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    6.596000] PCI: setting IRQ 11 as level-triggered
[    6.596000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    6.596000] ata3: SATA max UDMA/100 cmd 0xDC996080 ctl 0xDC99608A bmdma 0xDC996000 irq 11
[    6.596000] ata4: SATA max UDMA/100 cmd 0xDC9960C0 ctl 0xDC9960CA bmdma 0xDC996008 irq 11
[    6.596000] scsi2 : sata_sil
[    6.648000] usb 1-2: configuration #1 chosen from 1 choice
[    6.648000] hub 1-2:1.0: USB hub found
[    6.652000] hub 1-2:1.0: 4 ports detected
[    7.176000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    7.184000] ata3.00: ATA-6, max UDMA/133, 390721968 sectors: LBA48 
[    7.184000] ata3.00: ata3: dev 0 multi count 16
[    7.192000] ata3.00: configured for UDMA/100
[    7.192000] scsi3 : sata_sil
[    7.660000] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    7.700000] usb 4-2: new high speed USB device using ehci_hcd and address 3
[    7.828000] ata4.00: zero err_mask for failed internal command, assuming AC_ERR_OTHER
[    7.828000] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[    7.832000] usb 4-2: configuration #1 chosen from 1 choice
[    7.832000] hub 4-2:1.0: USB hub found
[    7.832000] hub 4-2:1.0: 4 ports detected
[    7.868000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001106664567594a]
[    8.180000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    8.372000] usb 2-1: configuration #1 chosen from 1 choice
[    8.576000] usb 4-2.3: new full speed USB device using ehci_hcd and address 4
[    8.652000] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    8.792000] usb 4-2.3: configuration #1 chosen from 1 choice
[    8.820000] ata4.00: zero err_mask for failed internal command, assuming AC_ERR_OTHER
[    8.820000] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[    8.992000] usb 4-2.4: new high speed USB device using ehci_hcd and address 5
[    9.084000] usb 4-2.4: configuration #1 chosen from 1 choice
[    9.120000] usbcore: registered new interface driver libusual
[    9.132000] Initializing USB Mass Storage driver...
[    9.132000] scsi4 : SCSI emulation for USB Mass Storage devices
[    9.132000] usbcore: registered new interface driver usb-storage
[    9.132000] USB Mass Storage support registered.
[    9.132000] usb-storage: device found at 5
[    9.132000] usb-storage: waiting for device to settle before scanning
[    9.644000] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    9.812000] ata4.00: zero err_mask for failed internal command, assuming AC_ERR_OTHER
[    9.812000] ata4.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[   10.636000] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   10.636000] scsi 2:0:0:0: Direct-Access     ATA      ST3200822AS      3.01 PQ: 0 ANSI: 5
[   10.636000] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   10.636000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   10.636000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[   10.636000] 0000:00:0a.0: 3Com PCI 3c905B Cyclone 100baseTx at dc8e2000.
[   10.680000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[   10.680000] sda: Write Protect is off
[   10.680000] sda: Mode Sense: 00 3a 00 00
[   10.680000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.684000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[   10.684000] sda: Write Protect is off
[   10.684000] sda: Mode Sense: 00 3a 00 00
[   10.684000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.684000]  sda: sda1 sda2 sda3 sda4
[   10.712000] sd 2:0:0:0: Attached scsi disk sda
[   11.004000] ReiserFS: sda2: found reiserfs format "3.6" with standard journal
[   11.004000] ReiserFS: sda2: using ordered data mode
[   11.020000] ReiserFS: sda2: journal params: device sda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   11.024000] ReiserFS: sda2: checking transaction log (sda2)
[   11.060000] ReiserFS: sda2: Using r5 hash to sort names
[   14.132000] usb-storage: device scan complete
[   14.660000] scsi 4:0:0:0: Direct-Access     ST340083 2A               3.03 PQ: 0 ANSI: 0
[   14.660000] SCSI device sdb: 781422768 512-byte hdwr sectors (400088 MB)
[   14.660000] sdb: Write Protect is off
[   14.660000] sdb: Mode Sense: 10 00 00 00
[   14.660000] sdb: assuming drive cache: write through
[   14.664000] SCSI device sdb: 781422768 512-byte hdwr sectors (400088 MB)
[   14.664000] sdb: Write Protect is off
[   14.664000] sdb: Mode Sense: 10 00 00 00
[   14.664000] sdb: assuming drive cache: write through
[   14.664000]  sdb: sdb1
[   14.688000] sd 4:0:0:0: Attached scsi disk sdb
[   14.688000] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   24.224000] eth0:  setting half-duplex.
[   25.108000] NET: Registered protocol family 10
[   25.108000] lo: Disabled Privacy Extensions
[   27.324000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.348000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.952000] Linux agpgart interface v0.101 (c) Dave Jones
[   27.976000] input: PC Speaker as /class/input/input1
[   28.008000] piix4_smbus 0000:00:04.3: Found 0000:00:04.3 device
[   28.520000] agpgart: Detected an Intel 440BX Chipset.
[   28.524000] agpgart: AGP aperture is 64M @ 0xe4000000
[   28.808000] nvidia: module license 'NVIDIA' taints kernel.
[   29.468000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   29.468000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   29.692000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[   30.484000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x043D pid 0x0100
[   30.484000] usbcore: registered new interface driver usblp
[   30.484000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   30.536000] parport: PnPBIOS parport detected.
[   30.536000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   30.688000] Floppy drive(s): fd0 is 1.44M
[   30.724000] FDC 0 is a post-1991 82077
[   30.760000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   30.876000] usbcore: registered new interface driver snd-usb-audio
[   31.980000] lp0: using parport0 (interrupt-driven).
[   32.188000] Adding 2048276k swap on /dev/disk/by-uuid/9050f562-7ecd-43b3-8d73-266ee8df2484.  Priority:-1 extents:1 across:2048276k
[   35.884000] eth0: no IPv6 routers present
[   62.484000] ReiserFS: dm-2: found reiserfs format "3.6" with standard journal
[   62.484000] ReiserFS: dm-2: using ordered data mode
[   62.488000] ReiserFS: dm-2: journal params: device dm-2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   62.492000] ReiserFS: dm-2: checking transaction log (dm-2)
[   62.544000] ReiserFS: dm-2: Using r5 hash to sort names
[   62.652000] Adding 2048276k swap on /dev/disk/by-uuid/9050f562-7ecd-43b3-8d73-266ee8df2484.  Priority:-2 extents:1 across:2048276k

---

