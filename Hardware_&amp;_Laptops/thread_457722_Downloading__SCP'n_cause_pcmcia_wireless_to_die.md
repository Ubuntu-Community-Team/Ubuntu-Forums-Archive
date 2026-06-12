---
title: "Downloading / SCP'n cause pcmcia wireless to die"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by newpey on 2007-05-28
HI this is real strange. After doing a clean install to fiesty, i am faced with a new issue. My Belkin and my RealTech PCMCIA wireless cards, both cause the same thing. After surfing for a few minutes, downloading, of ecure file coping stuff, the card no longer can see the router.. I have an identical hardware laptop, running breezy, it does not have these issues. I had to change the kernel to i386 instead of smp default for the realtech card, but i tried that also on feisty...  I have all the latest updates, and i just cant get my lappy to stay on the wireless!

Below is my dmesg when i get booted. The only fix is to completly reboot.. I can bring down or up the device (ath0) its just dead... cant see router ect...

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Wed May 23 01:46:23 UTC 2007 (Ubuntu 2.6.20-16.28-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000002bda0000 end: 000000002bea0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000002bea0000 size: 0000000000013000 end: 000000002beb3000 type: 3
[    0.000000] copy_e820_map() start: 000000002beb3000 size: 000000000004d000 end: 000000002bf00000 type: 4
[    0.000000] copy_e820_map() start: 000000002bf00000 size: 0000000000100000 end: 000000002c000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002bea0000 (usable)
[    0.000000]  BIOS-e820: 000000002bea0000 - 000000002beb3000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002beb3000 - 000000002bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002bf00000 - 000000002c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 702MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f73b0
[    0.000000] Entering add_active_range(0, 0, 179872) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   179872
[    0.000000]   HighMem    179872 ->   179872
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   179872
[    0.000000] On node 0 totalpages: 179872
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1373 pages used for memmap
[    0.000000]   Normal zone: 174403 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7450
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x2beae1d6
[    0.000000] ACPI: FADT (v001 ATI    Goldfish 0x06040000 ATI  0x000f4240) @ 0x2beb2f00
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x2beb2f74
[    0.000000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x2beb2fc4
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030224) @ 0x2beae410
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x2beae20e
[    0.000000] ACPI: DSDT (v001    ATI    SB400 0x06040000 MSFT 0x0100000c) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 2c000000:b4000000)
[    0.000000] Detected 1396.529 MHz processor.
[   12.516001] Built 1 zonelists.  Total pages: 178467
[   12.516007] Kernel command line: root=UUID=c4e0964e-702c-44a3-94e6-f8cabd8b4e8d ro quiet splash
[   12.516217] mapped APIC to ffffd000 (fee00000)
[   12.516220] mapped IOAPIC to ffffc000 (fec00000)
[   12.516225] Enabling fast FPU save and restore... done.
[   12.516229] Enabling unmasked SIMD FPU exception support... done.
[   12.516246] Initializing CPU#0
[   12.516349] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   12.517585] Console: colour VGA+ 80x25
[   12.518625] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   12.519645] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   12.546919] Memory: 702008k/719488k available (1992k kernel code, 16912k reserved, 896k data, 328k init, 0k highmem)
[   12.546931] virtual kernel memory layout:
[   12.546932]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   12.546934]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   12.546935]     vmalloc : 0xec800000 - 0xff7fe000   ( 303 MB)
[   12.546937]     lowmem  : 0xc0000000 - 0xebea0000   ( 702 MB)
[   12.546938]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   12.546940]       .data : 0xc02f2354 - 0xc03d26d4   ( 896 kB)
[   12.546941]       .text : 0xc0100000 - 0xc02f2354   (1992 kB)
[   12.546946] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.624325] Calibrating delay using timer specific routine.. 2796.35 BogoMIPS (lpj=5592703)
[   12.624376] Security Framework v1.0.0 initialized
[   12.624386] SELinux:  Disabled at boot.
[   12.624407] Mount-cache hash table entries: 512
[   12.624578] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 00000000 00000000 00000000
[   12.624593] CPU: L1 I cache: 32K, L1 D cache: 32K
[   12.624596] CPU: L2 cache: 1024K
[   12.624600] CPU: After all inits, caps: afe9fbff 00000000 00000000 00002040 00000000 00000000 00000000
[   12.624612] Compat vDSO mapped to ffffe000.
[   12.624617] Remapping vsyscall page to ffffe000
[   12.624630] Checking 'hlt' instruction... OK.
[   12.640431] SMP alternatives: switching to UP code
[   12.640652] Freeing SMP alternatives: 11k freed
[   12.640868] Early unpacking initramfs... done
[   13.044022] ACPI: Core revision 20060707
[   13.044336] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   13.053822] CPU0: Intel(R) Celeron(R) M processor         1.40GHz stepping 08
[   13.053853] Total of 1 processors activated (2796.35 BogoMIPS).
[   13.054046] ENABLING IO-APIC IRQs
[   13.054262] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   13.093988] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   13.094042] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   13.094045] ...trying to set up timer as Virtual Wire IRQ... works.
[   13.240194] Brought up 1 CPUs
[   13.240489] Booting paravirtualized kernel on bare hardware
[   13.240592] Time:  3:13:26  Date: 04/29/107
[   13.240630] NET: Registered protocol family 16
[   13.240736] EISA bus registered
[   13.240741] ACPI: bus type pci registered
[   13.240842] PCI: PCI BIOS revision 2.10 entry at 0xfd69c, last bus=14
[   13.240845] PCI: Using configuration type 1
[   13.240847] Setting up standard PCI resources
[   13.244678] ACPI: Interpreter enabled
[   13.244681] ACPI: Using IOAPIC for interrupt routing
[   13.245171] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.245178] PCI: Probing PCI hardware (bus 00)
[   13.246775] Boot video device is 0000:01:05.0
[   13.247071] PCI: Transparent bridge - 0000:00:14.4
[   13.247189] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.251225] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   13.251505] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   13.251790] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   13.252066] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   13.252379] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   13.252653] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   13.252928] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   13.253201] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   13.315818] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   13.316401] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   13.316917] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.316929] pnp: PnP ACPI init
[   13.319216] pnp: PnP ACPI: found 10 devices
[   13.319222] PnPBIOS: Disabled by ACPI PNP
[   13.319285] PCI: Using ACPI for IRQ routing
[   13.319288] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.349920] NET: Registered protocol family 8
[   13.349922] NET: Registered protocol family 20
[   13.350149] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   13.350153] pnp: 00:08: ioport range 0x200-0x20f has been reserved
[   13.350156] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   13.350475] PCI: Bridge: 0000:00:01.0
[   13.350478]   IO window: 9000-9fff
[   13.350483]   MEM window: d0100000-d01fffff
[   13.350487]   PREFETCH window: d8000000-dfffffff
[   13.350500] PCI: Bus 10, cardbus bridge: 0000:09:01.0
[   13.350503]   IO window: 0000a400-0000a4ff
[   13.350510]   IO window: 0000a800-0000a8ff
[   13.350517]   PREFETCH window: 30000000-33ffffff
[   13.350524]   MEM window: 34000000-37ffffff
[   13.350531] PCI: Bridge: 0000:00:14.4
[   13.350535]   IO window: a000-afff
[   13.350543]   MEM window: d0200000-d02fffff
[   13.350549]   PREFETCH window: 30000000-33ffffff
[   13.350597] PCI: Enabling device 0000:09:01.0 (0000 -> 0003)
[   13.350606] ACPI: PCI Interrupt 0000:09:01.0[A] -> GSI 20 (level, low) -> IRQ 16
[   13.350645] NET: Registered protocol family 2
[   13.384208] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.384434] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   13.386518] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   13.388010] TCP: Hash tables configured (established 131072 bind 65536)
[   13.388017] TCP reno registered
[   13.396353] checking if image is initramfs... it is
[   14.193685] Freeing initrd memory: 6780k freed
[   14.194368] audit: initializing netlink socket (disabled)
[   14.194390] audit(1180408407.716:1): initialized
[   14.194571] VFS: Disk quotas dquot_6.5.1
[   14.194598] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   14.194668] io scheduler noop registered
[   14.194672] io scheduler anticipatory registered
[   14.194675] io scheduler deadline registered
[   14.194688] io scheduler cfq registered (default)
[   14.876045] isapnp: Scanning for PnP cards...
[   15.231031] isapnp: No Plug & Play device found
[   15.271522] Real Time Clock Driver v1.12ac
[   15.271682] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.272726] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   15.272741] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   15.272829] mice: PS/2 mouse device common for all mice
[   15.273496] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.273809] input: Macintosh mouse button emulation as /class/input/input0
[   15.273852] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   15.273857] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   15.274196] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   15.277579] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.277583] serio: i8042 AUX port at 0x60,0x64 irq 12
[   15.277729] EISA: Probing bus 0 at eisa.0
[   15.277741] Cannot allocate resource for EISA slot 1
[   15.277774] Cannot allocate resource for EISA slot 8
[   15.277777] EISA: Detected 0 cards.
[   15.307912] TCP cubic registered
[   15.307927] NET: Registered protocol family 1
[   15.307959] Using IPI No-Shortcut mode
[   15.308059] ACPI: (supports S0 S3 S4 S5)
[   15.308122]   Magic number: 7:655:210
[   15.308188]   hash matches device ttyt8
[   15.308212]   hash matches device ttyqb
[   15.308788] Freeing unused kernel memory: 328k freed
[   15.311518] Time: tsc clocksource has been installed.
[   15.324828] input: AT Translated Set 2 keyboard as /class/input/input1
[   16.547154] Capability LSM initialized
[   16.587197] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   16.587206] ACPI: Processor [CPU0] (supports 8 throttling states)
[   16.587215] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   16.597980] ACPI: Thermal Zone [THRM] (41 C)
[   17.041579] usbcore: registered new interface driver usbfs
[   17.041609] usbcore: registered new interface driver hub
[   17.041639] usbcore: registered new device driver usb
[   17.042523] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   17.042580] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 18
[   17.042597] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   17.042809] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   17.042832] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd0000000
[   17.095418] SCSI subsystem initialized
[   17.102057] libata version 2.20 loaded.
[   17.143634] usb usb1: configuration #1 chosen from 1 choice
[   17.143677] hub 1-0:1.0: USB hub found
[   17.143694] hub 1-0:1.0: 4 ports detected
[   17.179863] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   17.247172] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 18
[   17.247199] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   17.247226] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   17.247248] ohci_hcd 0000:00:13.1: irq 18, io mem 0xd0001000
[   17.307122] usb usb2: configuration #1 chosen from 1 choice
[   17.307158] hub 2-0:1.0: USB hub found
[   17.307172] hub 2-0:1.0: 4 ports detected
[    4.024000] Time: acpi_pm clocksource has been installed.
[    4.108000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 18
[    4.108000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    4.108000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    4.108000] ehci_hcd 0000:00:13.2: irq 18, io mem 0xd0002000
[    4.108000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.108000] usb usb3: configuration #1 chosen from 1 choice
[    4.108000] hub 3-0:1.0: USB hub found
[    4.108000] hub 3-0:1.0: 8 ports detected
[    4.212000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    4.212000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 19
[    4.212000] ATIIXP: chipset revision 0
[    4.212000] ATIIXP: not 100% native mode: will probe irqs later
[    4.212000]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[    4.212000]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[    4.212000] Probing IDE interface ide0...
[    4.504000] hda: TOSHIBA MK4026GAX, ATA DISK drive
[    5.176000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.224000] Probing IDE interface ide1...
[    5.960000] hdc: TSSTcorpCDW/DVD TS-L462C, ATAPI CD/DVD-ROM drive
[    6.632000] ide1 at 0x170-0x177,0x376 on irq 15
[    6.680000] 8139cp 0000:09:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    6.680000] 8139cp 0000:09:02.0: Try the "8139too" driver instead.
[    6.684000] 8139too Fast Ethernet driver 0.9.28
[    6.684000] ACPI: PCI Interrupt 0000:09:02.0[A] -> GSI 21 (level, low) -> IRQ 20
[    6.688000] eth0: RealTek RTL8139 at 0xec858000, 00:c0:9f:ee:f2:47, IRQ 20
[    6.688000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    6.692000] hda: max request size: 128KiB
[    6.704000] hda: 78140160 sectors (40007 MB), CHS=65535/16/63, UDMA(100)
[    6.704000] hda: cache flushes supported
[    6.704000]  hda: hda1 hda2 < hda5 >
[    6.800000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 1536kB Cache, UDMA(33)
[    6.800000] Uniform CD-ROM driver Revision: 3.20
[    6.932000] Attempting manual resume
[    6.932000] swsusp: Resume From Partition 3:5
[    6.932000] PM: Checking swsusp image.
[    6.932000] PM: Resume from disk failed.
[    6.976000] kjournald starting.  Commit interval 5 seconds
[    6.976000] EXT3-fs: mounted filesystem with ordered data mode.
[   17.420000] eth0: link down
[   18.724000] NET: Registered protocol family 17
[   19.092000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   19.336000] Linux agpgart interface v0.102 (c) Dave Jones
[   19.400000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.752000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.008000] input: PC Speaker as /class/input/input2
[   20.164000] Yenta: CardBus bridge found at 0000:09:01.0 [1179:ff31]
[   20.164000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   20.164000] Yenta: Routing CardBus interrupts to PCI
[   20.164000] Yenta TI: socket 0000:09:01.0, mfunc 0x015c1d22, devctl 0x44
[   20.380000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   20.380000] synaptics: Toshiba Satellite L25                     detected, limiting rate to 40pps.
[   20.416000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   20.440000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   20.440000] Socket status: 30000020
[   20.440000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   20.440000] cs: IO port probe 0xa000-0xafff: clean.
[   20.440000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   20.440000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   20.440000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   20.552000] MC'97 0 converters and GPIO not ready (0x1)
[   20.552000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   21.092000] pccard: CardBus card inserted into slot 0
[   21.132000] ath_hal: module license 'Proprietary' taints kernel.
[   21.132000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   21.184000] cs: IO port probe 0x100-0x3af: clean.
[   21.188000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   21.188000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[   21.192000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   21.192000] cs: IO port probe 0xa00-0xaff: clean.
[   21.324000] wlan: 0.8.4.2 (0.9.3)
[   21.368000] ath_pci: 0.9.4.5 (0.9.3)
[   21.368000] PCI: Enabling device 0000:0a:00.0 (0000 -> 0002)
[   21.368000] ACPI: PCI Interrupt 0000:0a:00.0[A] -> GSI 20 (level, low) -> IRQ 16
[   22.024000] ath_rate_sample: 1.2 (0.9.3)
[   22.028000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   22.028000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   22.028000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   22.028000] wifi0: mac 7.8 phy 4.5 radio 5.6
[   22.028000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   22.028000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   22.028000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   22.028000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   22.028000] wifi0: Use hw queue 8 for CAB traffic
[   22.028000] wifi0: Use hw queue 9 for beacons
[   22.048000] wifi0: Atheros 5212: mem=0x34000000, irq=16
[   22.252000] fuse init (API version 7.8)
[   22.352000] lp: driver loaded but no devices found
[   22.380000] Adding 1646620k swap on /dev/disk/by-uuid/28311693-b741-4414-a576-c4d558b2c159.  Priority:-1 extents:1 across:1646620k
[   22.512000] EXT3 FS on hda1, internal journal
[   26.912000] NET: Registered protocol family 10
[   26.912000] lo: Disabled Privacy Extensions
[   26.912000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.272000] ibm_acpi: ec object not found
[   27.464000] ACPI: Battery Slot [BAT1] (battery present)
[   27.524000] input: Power Button (FF) as /class/input/input4
[   27.528000] ACPI: Power Button (FF) [PWRF]
[   27.576000] input: Lid Switch as /class/input/input5
[   27.580000] ACPI: Lid Switch [LID]
[   27.624000] input: Power Button (CM) as /class/input/input6
[   27.632000] ACPI: Power Button (CM) [PWRB]
[   27.648000] Using specific hotkey driver
[   27.720000] ACPI: AC Adapter [ACAD] (on-line)
[   27.736000] No dock devices found.
[   27.776000] pcc_acpi: loading...
[   33.048000] [fglrx] Maximum main memory to use for locked dma buffers: 616 MBytes.
[   33.048000] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   33.084000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   33.364000] ppdev: user-space parallel port driver
[   34.856000] [fglrx] total      GART = 130023424
[   34.856000] [fglrx] free       GART = 114032640
[   34.856000] [fglrx] max single GART = 114032640
[   34.856000] [fglrx] total      LFB  = 67108864
[   34.856000] [fglrx] free       LFB  = 55570432
[   34.856000] [fglrx] max single LFB  = 55570432
[   34.856000] [fglrx] total      Inv  = 0
[   34.856000] [fglrx] free       Inv  = 0
[   34.856000] [fglrx] max single Inv  = 0
[   34.856000] [fglrx] total      TIM  = 0
[   35.872000] apm: BIOS not found.
[   36.644000] Bluetooth: Core ver 2.11
[   36.644000] NET: Registered protocol family 31
[   36.644000] Bluetooth: HCI device and connection manager initialized
[   36.644000] Bluetooth: HCI socket layer initialized
[   36.664000] Bluetooth: L2CAP ver 2.8
[   36.664000] Bluetooth: L2CAP socket layer initialized
[   36.792000] Bluetooth: RFCOMM socket layer initialized
[   36.792000] Bluetooth: RFCOMM TTY layer initialized
[   36.792000] Bluetooth: RFCOMM ver 1.8
[   37.768000] ath0: no IPv6 routers present
chris@chris-laptop:~$

---

### Post by newpey on 2007-06-01
bump.. please help my next step is fedora 7 and i would rather stay on ubuntu but its unussable like this...

---

### Post by cptcrunch on 2007-06-01
I am also having problems staying connected to my router via wireless. I can surf for a few minutes then it cuts out and dies. The only way to get it back is to reboot. Ever since I upgraded to the latest Kernel, 2.6.20-16-generic, I have been having this problem :(

---

