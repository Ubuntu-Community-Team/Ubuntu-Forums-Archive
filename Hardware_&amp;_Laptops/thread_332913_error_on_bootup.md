---
title: "error on bootup"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by firstc624 on 2007-01-06
ok how can i view the output of boot seguence?  I am trying to get all pieces of this laptop running, but i don't think ubuntu is picking up on all of it, but not sure.   can anyone help?

> firstc624@firstc624-laptop:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000077ea0000 (usable)
[17179569.184000]  BIOS-e820: 0000000077ea0000 - 0000000077eac000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000077eac000 - 0000000077f00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 0000000077f00000 - 0000000080000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 1022MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f7c70
[17179569.184000] On node 0 totalpages: 491168
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 261792 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7c40
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x77ea3ed3
[17179569.184000] ACPI: FADT (v001 HP     Piranha  0x06040000 ATI  0x000f4240) @ 0x77eabdf9
[17179569.184000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x77eabe6d
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x06040000  LTP 0x00000000) @ 0x77eabf7e
[17179569.184000] ACPI: MCFG (v001 HP     PORSCHE  0x06040000 LOHR 0x00000000) @ 0x77eabfc4
[17179569.184000] ACPI: DSDT (v001     HP     309B 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 2189.340 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.996000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.996000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.048000] Memory: 1937804k/1964672k available (1910k kernel code, 25572k reserved, 1069k data, 308k init, 1047168k highmem)
[17179571.048000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.128000] Calibrating delay using timer specific routine.. 4384.79 BogoMIPS (lpj=8769588)
[17179571.128000] Security Framework v1.0.0 initialized
[17179571.128000] SELinux:  Disabled at boot.
[17179571.128000] Mount-cache hash table entries: 512
[17179571.128000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179571.128000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179571.128000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179571.128000] CPU: L2 Cache: 1024K (64 bytes/line)
[17179571.128000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[17179571.128000] Checking 'hlt' instruction... OK.
[17179571.144000] SMP alternatives: switching to UP code
[17179571.144000] Freeing SMP alternatives: 16k freed
[17179571.144000] checking if image is initramfs... it is
[17179571.572000] Freeing initrd memory: 5623k freed
[17179571.572000] ACPI: Core revision 20060707
[17179571.572000] ACPI: Looking for DSDT ... not found!
[17179572.212000] CPU0: AMD Turion(tm) 64 Mobile Technology ML-40 stepping 02
[17179572.212000] Total of 1 processors activated (4384.79 BogoMIPS).
[17179572.212000] ENABLING IO-APIC IRQs
[17179572.212000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179572.356000] Brought up 1 CPUs
[17179572.356000] migration_cost=0
[17179572.356000] NET: Registered protocol family 16
[17179572.356000] EISA bus registered
[17179572.356000] ACPI: bus type pci registered
[17179572.356000] PCI: Using MMCONFIG
[17179572.356000] PCI: No mmconfig possible on 0:18
[17179572.356000] Setting up standard PCI resources
[17179572.356000] ACPI: Interpreter enabled
[17179572.356000] ACPI: Using IOAPIC for interrupt routing
[17179572.356000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.356000] PCI: Probing PCI hardware (bus 00)
[17179572.380000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[17179572.380000] Boot video device is 0000:01:05.0
[17179572.380000] PCI: Transparent bridge - 0000:00:14.4
[17179572.380000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.380000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[17179572.380000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[17179572.384000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[17179572.384000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[17179572.384000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[17179572.384000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[17179572.384000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[17179572.384000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[17179572.384000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[17179572.384000] ACPI: Embedded Controller [EC0] (gpe 26) interrupt mode.
[17179572.424000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[17179572.424000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179572.424000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.424000] pnp: PnP ACPI init
[17179572.448000] pnp: PnP ACPI: found 10 devices
[17179572.448000] PnPBIOS: Disabled by ACPI PNP
[17179572.448000] PCI: Using ACPI for IRQ routing
[17179572.448000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.448000] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[17179572.448000] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[17179572.448000] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[17179572.448000] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[17179572.448000] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[17179572.448000] pnp: 00:08: ioport range 0x4d6-0x4d6 has been reserved
[17179572.448000] pnp: 00:08: ioport range 0x870-0x87f has been reserved
[17179572.448000] PCI: Bridge: 0000:00:01.0
[17179572.448000]   IO window: 9000-9fff
[17179572.448000]   MEM window: b0100000-b01fffff
[17179572.448000]   PREFETCH window: c0000000-cfffffff
[17179572.448000] PCI: Bridge: 0000:00:05.0
[17179572.448000]   IO window: disabled.
[17179572.448000]   MEM window: disabled.
[17179572.448000]   PREFETCH window: disabled.
[17179572.448000] PCI: Bus 7, cardbus bridge: 0000:06:04.0
[17179572.448000]   IO window: 0000a400-0000a4ff
[17179572.448000]   IO window: 0000a800-0000a8ff
[17179572.448000]   PREFETCH window: 88000000-89ffffff
[17179572.448000]   MEM window: 8a000000-8bffffff
[17179572.448000] PCI: Bridge: 0000:00:14.4
[17179572.448000]   IO window: a000-afff
[17179572.448000]   MEM window: b0200000-b02fffff
[17179572.448000]   PREFETCH window: 88000000-89ffffff
[17179572.448000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[17179572.448000] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 20 (level, low) -> IRQ 177
[17179572.448000] NET: Registered protocol family 2
[17179572.484000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.484000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[17179572.484000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179572.484000] TCP: Hash tables configured (established 262144 bind 65536)
[17179572.484000] TCP reno registered
[17179572.484000] audit: initializing netlink socket (disabled)
[17179572.484000] audit(1168103656.484:1): initialized
[17179572.484000] highmem bounce pool size: 64 pages
[17179572.484000] VFS: Disk quotas dquot_6.5.1
[17179572.484000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.484000] Initializing Cryptographic API
[17179572.484000] io scheduler noop registered
[17179572.484000] io scheduler anticipatory registered
[17179572.484000] io scheduler deadline registered
[17179572.484000] io scheduler cfq registered (default)
[17179572.484000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[17179572.484000] pcie_portdrv_probe->Dev[5a37:1002] has invalid IRQ. Check vendor BIOS
[17179572.488000] assign_interrupt_mode Found MSI capability
[17179572.488000] Allocate Port Service[0000:00:05.0:pcie00]
[17179572.488000] Allocate Port Service[0000:00:05.0:pcie01]
[17179572.488000] isapnp: Scanning for PnP cards...
[17179572.840000] isapnp: No Plug & Play device found
[17179572.856000] Real Time Clock Driver v1.12ac
[17179572.856000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.856000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 201
[17179572.856000] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[17179572.856000] mice: PS/2 mouse device common for all mice
[17179572.860000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.860000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.860000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.860000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179572.876000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.880000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.884000] EISA: Probing bus 0 at eisa.0
[17179572.884000] Cannot allocate resource for EISA slot 1
[17179572.884000] Cannot allocate resource for EISA slot 8
[17179572.884000] EISA: Detected 0 cards.
[17179572.884000] TCP bic registered
[17179572.884000] NET: Registered protocol family 1
[17179572.884000] NET: Registered protocol family 8
[17179572.884000] NET: Registered protocol family 20
[17179572.884000] Using IPI No-Shortcut mode
[17179572.884000] ACPI: (supports S0 S3 S4 S5)
[17179572.884000] Freeing unused kernel memory: 308k freed
[17179572.908000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.956000] Capability LSM initialized
[17179573.984000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179573.984000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179573.992000] ACPI Exception (acpi_thermal-0417): AE_NOT_FOUND, Invalid active threshold [0] [20060707]
[17179573.996000] ACPI: Thermal Zone [THRM] (0 C)
[17179574.320000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[17179574.320000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 209
[17179574.320000] ATIIXP: chipset revision 0
[17179574.320000] ATIIXP: not 100% native mode: will probe irqs later
[17179574.320000]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[17179574.320000]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[17179574.320000] Probing IDE interface ide0...
[17179574.608000] hda: ST9100822A, ATA DISK drive
[17179575.280000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.360000] Probing IDE interface ide1...
[17179576.096000] hdc: TSSTcorpCD/DVDW TS-L532M, ATAPI CD/DVD-ROM drive
[17179576.780000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.800000] hda: max request size: 512KiB
[17179576.800000] hda: 195371568 sectors (100030 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[17179576.808000] hda: cache flushes supported
[17179576.808000]  hda: hda1 hda2 hda3 < hda5 > hda4
[17179576.940000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, DMA
[17179576.940000] Uniform CD-ROM driver Revision: 3.20
[17179578.792000] usbcore: registered new driver usbfs
[17179578.792000] usbcore: registered new driver hub
[17179578.792000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.792000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 217
[17179578.792000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[17179578.796000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[17179578.796000] ohci_hcd 0000:00:13.0: irq 217, io mem 0xb0000000
[17179578.856000] usb usb1: configuration #1 chosen from 1 choice
[17179578.856000] hub 1-0:1.0: USB hub found
[17179578.856000] hub 1-0:1.0: 4 ports detected
[17179578.868000] ieee1394: Initialized config rom entry `ip1394'
[17179578.960000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 217
[17179578.960000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[17179578.960000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[17179578.960000] ohci_hcd 0000:00:13.1: irq 217, io mem 0xb0001000
[17179579.020000] usb usb2: configuration #1 chosen from 1 choice
[17179579.020000] hub 2-0:1.0: USB hub found
[17179579.020000] hub 2-0:1.0: 4 ports detected
[17179579.124000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 217
[17179579.124000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[17179579.124000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[17179579.124000] ehci_hcd 0000:00:13.2: irq 217, io mem 0xb0002000
[17179579.124000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.124000] usb usb3: configuration #1 chosen from 1 choice
[17179579.124000] hub 3-0:1.0: USB hub found
[17179579.124000] hub 3-0:1.0: 8 ports detected
[17179579.228000] ACPI: PCI Interrupt 0000:06:04.2[C] -> GSI 23 (level, low) -> IRQ 225
[17179579.276000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[225]  MMIO=[b0209000-b02097ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179579.356000] Attempting manual resume
[17179579.392000] kjournald starting.  Commit interval 5 seconds
[17179579.392000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.556000] ohci_hcd 0000:00:13.0: wakeup
[17179579.940000] usb 1-4: new full speed USB device using ohci_hcd and address 3
[17179580.152000] usb 1-4: configuration #1 chosen from 1 choice
[17179590.896000] input: PC Speaker as /class/input/input1
[17179591.068000] Linux agpgart interface v0.101 (c) Dave Jones
[17179591.164000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.172000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179592.028000] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 20 (level, low) -> IRQ 177
[17179592.028000] Yenta: CardBus bridge found at 0000:06:04.0 [103c:30a4]
[17179592.028000] Yenta: Enabling burst memory read transactions
[17179592.028000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179592.028000] Yenta: Routing CardBus interrupts to ISA
[17179592.028000] Yenta TI: socket 0000:06:04.0, mfunc 0x00a61b22, devctl 0x64
[17179592.260000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 177
[17179592.260000] Socket status: 30000006
[17179592.260000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[17179592.260000] cs: IO port probe 0xa000-0xafff: clean.
[17179592.260000] pcmcia: parent PCI bridge Memory window: 0xb0200000 - 0xb02fffff
[17179592.260000] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x89ffffff
[17179592.372000] ACPI: PCI Interrupt 0000:06:04.3[B] -> GSI 23 (level, low) -> IRQ 225
[17179592.936000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[17179592.936000] sdhci: Copyright(c) Pierre Ossman
[17179592.936000] sdhci: SDHCI controller found at 0000:06:04.4 [104c:8034] (rev 0)
[17179592.936000] ACPI: PCI Interrupt 0000:06:04.4[A] -> GSI 20 (level, low) -> IRQ 177
[17179592.936000] mmc0: SDHCI at 0xb020a000 irq 177 DMA
[17179592.936000] mmc1: SDHCI at 0xb0209c00 irq 177 DMA
[17179592.936000] mmc2: SDHCI at 0xb0209800 irq 177 DMA
[17179593.092000] ieee80211_crypt: registered algorithm 'NULL'
[17179593.216000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179593.216000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179593.448000] Bluetooth: Core ver 2.8
[17179593.448000] NET: Registered protocol family 31
[17179593.448000] Bluetooth: HCI device and connection manager initialized
[17179593.448000] Bluetooth: HCI socket layer initialized
[17179593.560000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[17179593.616000] 8139too Fast Ethernet driver 0.9.27
[17179593.616000] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 22 (level, low) -> IRQ 233
[17179593.616000] eth0: RealTek RTL8139 at 0xf89f4400, 00:0f:b0:c5:47:44, IRQ 233
[17179593.616000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179593.628000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179593.780000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179593.980000] eth0: link down
[17179594.124000] Bluetooth: HCI USB driver ver 2.9
[17179594.128000] usbcore: registered new driver hci_usb
[17179594.236000] ts: Compaq touchscreen protocol output
[17179594.416000] bcm43xx driver
[17179594.416000] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 21 (level, low) -> IRQ 50
[17179594.536000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 201
[17179594.648000] MC'97 0 converters and GPIO not ready (0x1)
[17179594.648000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 201
[17179594.788000] cs: IO port probe 0x100-0x3af: clean.
[17179594.792000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179594.792000] cs: IO port probe 0x820-0x8ff: clean.
[17179594.796000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[17179594.796000] cs: IO port probe 0xa00-0xaff: clean.
[17179595.124000] NET: Registered protocol family 17
[17179595.168000] fuse init (API version 7.8)
[17179595.168000] fuse distribution version: 2.6.1
[17179595.208000] Adding 787144k swap on /dev/disk/by-uuid/f00fbd27-2b0b-4c15-a91c-a05b4c819be3.  Priority:-1 extents:1 across:787144k
[17179595.384000] EXT3 FS on hda2, internal journal
[17179601.180000] ACPI: AC Adapter [ACAD] (on-line)
[17179601.248000] ACPI: Battery Slot [BAT1] (battery present)
[17179601.260000] ACPI: Power Button (FF) [PWRF]
[17179601.260000] ACPI: Sleep Button (FF) [SLPF]
[17179601.260000] ACPI: Lid Switch [LID]
[17179601.260000] ACPI: Power Button (CM) [PWRB]
[17179601.396000] ibm_acpi: ec object not found
[17179601.420000] pcc_acpi: loading...
[17179601.460000] wmi_add device=dffa0400
[17179601.460000] calling WQBA
[17179601.508000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179601.692000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179601.692000] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x4 (1450 mV)
[17179601.692000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x6 (1400 mV)
[17179601.692000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x8 (1350 mV)
[17179601.692000] powernow-k8:    3 : fid 0x8 (1600 MHz), vid 0xa (1300 mV)
[17179601.692000] powernow-k8:    4 : fid 0x0 (800 MHz), vid 0x16 (1000 mV)
[17179601.692000] cpu_init done, current fid 0xe, vid 0x2
[17179601.696000] powernow-k8: ph2 null fid transition 0xe
[17179602.996000] lp: driver loaded but no devices found
[17179603.016000] ppdev: user-space parallel port driver
[17179603.916000] apm: BIOS not found.
[17179610.996000] Bluetooth: L2CAP ver 2.8
[17179610.996000] Bluetooth: L2CAP socket layer initialized
[17179611.012000] Bluetooth: RFCOMM socket layer initialized
[17179611.012000] Bluetooth: RFCOMM TTY layer initialized
[17179611.012000] Bluetooth: RFCOMM ver 1.7
[17179616.960000] NET: Registered protocol family 10
[17179616.960000] lo: Disabled Privacy Extensions
[17179616.960000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179616.960000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179616.960000] IPv6 over IPv4 tunneling driver
[17179636.244000] SoftMAC: Open Authentication completed with 00:12:17:ff:90:7a
[17179636.296000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17179636.700000] ieee80211_crypt: registered algorithm 'TKIP'
[17179652.788000] eth1: no IPv6 routers present
[17179654.256000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000000b2 received TSC 0000000000b2
[17179654.340000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000000ca received TSC 0000000000ca
[17179654.356000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000000d7 received TSC 0000000000d7
[17179667.388000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 000000000229 received TSC 000000000229
[17179668.424000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 000000000262 received TSC 000000000262
[17179670.340000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000002bb received TSC 0000000002bb
[17179695.228000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000003e5 received TSC 0000000003e5
[17179754.068000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 00000000042d received TSC 00000000042d
[17179860.320000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 00000000044a received TSC 00000000044a
[17179860.320000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 00000000044a received TSC 00000000044a
[17179860.324000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 00000000044a received TSC 00000000044a
[17179860.328000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 00000000044a received TSC 00000000044a
[17179860.332000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 00000000044a received TSC 00000000044a
[17179910.676000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 00000000044c received TSC 00000000044c
[17179910.676000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 00000000044c received TSC 00000000044c
[17179910.676000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 00000000044c received TSC 00000000044c
[17179910.680000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 00000000044d received TSC 00000000044d
[17179910.680000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 00000000044d received TSC 00000000044d
[17179910.680000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 00000000044d received TSC 00000000044d
[17179910.684000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 00000000044e received TSC 00000000044e
[17179910.684000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 00000000044e received TSC 00000000044e
[17179910.688000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 00000000044e received TSC 00000000044e
[17179910.688000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 00000000044f received TSC 00000000044f
[17179915.948000] printk: 46 messages suppressed.
[17179915.948000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000004c5 received TSC 0000000004c5
[17180608.708000] printk: 12 messages suppressed.
[17180608.708000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 00000000055d received TSC 00000000055d
[17180609.008000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 00000000056c received TSC 00000000056c
[17180610.740000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000005c5 received TSC 0000000005c5
[17180610.848000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000005c8 received TSC 0000000005c8
[17180610.884000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000005ce received TSC 0000000005ce
[17180610.956000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000005d0 received TSC 0000000005d0
[17180610.960000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000005d0 received TSC 0000000005d0
[17180610.984000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000005d1 received TSC 0000000005d1
[17180631.796000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000005da received TSC 0000000005da
[17180635.764000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000005e6 received TSC 0000000005e6
[17180635.860000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000005e8 received TSC 0000000005e8
[17180636.040000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000005f6 received TSC 0000000005f6
[17180636.040000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000005f6 received TSC 0000000005f6
[17180636.044000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000005f6 received TSC 0000000005f6
[17180636.044000] TKIP: replay detected: STA=00:12:17:ff:90:7a previous TSC 0000000005f7 received TSC 0000000005f7
[17180644.432000] usb 3-6: new high speed USB device using ehci_hcd and address 3
[17180644.572000] usb 3-6: configuration #1 chosen from 1 choice
[17180644.868000] usbcore: registered new driver libusual
[17180644.988000] SCSI subsystem initialized
[17180644.996000] Initializing USB Mass Storage driver...
[17180644.996000] scsi0 : SCSI emulation for USB Mass Storage devices
[17180644.996000] usbcore: registered new driver usb-storage
[17180644.996000] USB Mass Storage support registered.
[17180644.996000] usb-storage: device found at 3
[17180644.996000] usb-storage: waiting for device to settle before scanning
[17180649.996000] usb-storage: device scan complete
[17180650.004000]   Vendor: FUJITSU   Model: MHT2040AT         Rev: 0811
[17180650.004000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17180650.080000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[17180650.084000] sda: test WP failed, assume Write Enabled
[17180650.084000] sda: assuming drive cache: write through
[17180650.088000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[17180650.088000] sda: test WP failed, assume Write Enabled
[17180650.088000] sda: assuming drive cache: write through
[17180650.092000]  sda: sda1
[17180650.120000] sd 0:0:0:0: Attached scsi disk sda
[17180650.140000] sd 0:0:0:0: Attached scsi generic sg0 type 0


and here is the output of lspci

> firstc624@firstc624-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation Dell Wireless 1470 DualBand WLAN (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


Thanks in advance for any help someone has.


Another thing that is weird is out of nowhere my touchpad will freak out and move across the screen.  it is very annoying

thanks again

---

### Post by MrSoussey on 2007-01-14
try a bios update... worked for me

---

### Post by firstc624 on 2007-01-14
i am currently running the newest bios update that hp offers for this laptop.  dv5040us.  

anyone have an idea?

---

### Post by erothoff on 2007-01-20
It took my a long time to find on this site, that if you use "noapic nolapic" in the boot options, that my DV6119 will boot. I am still having some problems in my 64 version with a driver that freezes startup 2 times. (And the third boot it works. I was actually looking for that solution when I found your thread.)
Good Luck

---

