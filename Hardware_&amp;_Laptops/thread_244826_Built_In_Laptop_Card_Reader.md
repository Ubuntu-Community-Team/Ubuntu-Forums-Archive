---
title: "Built In Laptop Card Reader"
date: 2006-08-27
forum: Hardware &amp; Laptops
---

### Post by neil_707 on 2006-08-27
Hi

   Im new to Ubuntu and so far its been a breeze. However my built in card reader on my Presario V2000 does not seem to work. 

I think my card reader is pci interface and not usb. Here are the outputs of dmesg and lspci respectivelyneil@neil-laptop:/media$ dmesg
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT  Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[4294667.296000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001f6e0000 (usable)
[4294667.296000]  BIOS-e820: 000000001f6e0000 - 000000001f6eb000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001f6eb000 - 000000001f700000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[4294667.296000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[4294667.296000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 502MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 128736
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 124640 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI present.
[4294667.296000] ACPI: RSDP (v000 HP                                    ) @ 0x000f7b10
[4294667.296000] ACPI: RSDT (v001 HP     308F     0x20041222  LTP 0x00000000) @ 0x1f6e5586
[4294667.296000] ACPI: MADT (v001 HP     308F     0x20041222 LOHR 0x0000005f) @ 0x1f6eae88
[4294667.296000] ACPI: FADT (v001 HP     308F     0x20041222 PTL  0x0000005f) @ 0x1f6eaef0
[4294667.296000] ACPI: HPET (v001 HP     308F     0x20041222 LOHR 0x0000005f) @ 0x1f6eaf64
[4294667.296000] ACPI: MCFG (v001 HP     308F     0x20041222 LOHR 0x0000005f) @ 0x1f6eaf9c
[4294667.296000] ACPI: BOOT (v001 HP     308F     0x20041222  LTP 0x00000001) @ 0x1f6eafd8
[4294667.296000] ACPI: SSDT (v001 HP     308F     0x00003001 INTL 0x20030224) @ 0x1f6e57b4
[4294667.296000] ACPI: SSDT (v001 HP     308F     0x00003000 INTL 0x20030224) @ 0x1f6e55c6
[4294667.296000] ACPI: DSDT (v001 HP     308F     0x20041222 MSFT 0x0100000e) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x1008
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 6:13 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[4294667.296000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] ACPI: HPET id: 0x8086a201 base: 0x0
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1397.113 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294668.510000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294668.510000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294668.524000] Memory: 499892k/514944k available (1976k kernel code, 14568k reserved, 606k data, 288k init, 0k hig hmem)
[4294668.524000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294668.584000] Calibrating delay using timer specific routine.. 2796.07 BogoMIPS (lpj=1398035)
[4294668.584000] Security Framework v1.0.0 initialized
[4294668.584000] SELinux:  Disabled at boot.
[4294668.584000] Mount-cache hash table entries: 512
[4294668.584000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[4294668.584000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[4294668.584000] CPU: L1 I cache: 32K, L1 D cache: 32K
[4294668.584000] CPU: L2 cache: 1024K
[4294668.584000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000000 00000000 00000000
[4294668.584000] mtrr: v2.0 (20020519)
[4294668.584000] CPU: Intel(R) Celeron(R) M processor         1.40GHz stepping 08
[4294668.584000] Enabling fast FPU save and restore... done.
[4294668.584000] Enabling unmasked SIMD FPU exception support... done.
[4294668.584000] Checking 'hlt' instruction... OK.
[4294668.588000] checking if image is initramfs... it is
[4294669.366000] Freeing initrd memory: 6836k freed
[4294669.375000] ACPI: Looking for DSDT ... not found!
[4294669.397000] ENABLING IO-APIC IRQs
[4294669.398000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294669.509000] NET: Registered protocol family 16
[4294669.509000] EISA bus registered
[4294669.509000] ACPI: bus type pci registered
[4294669.509000] PCI: PCI BIOS revision 2.10 entry at 0xfd96e, last bus=6
[4294669.509000] PCI: Using MMCONFIG
[4294669.510000] ACPI: Subsystem revision 20051216
[4294669.511000] ACPI: Interpreter enabled
[4294669.511000] ACPI: Using IOAPIC for interrupt routing
[4294669.512000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294669.512000] PCI: Probing PCI hardware (bus 00)
[4294669.514000] Boot video device is 0000:00:02.0
[4294669.514000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[4294669.514000] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[4294669.514000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294669.515000] PCI: Transparent bridge - 0000:00:1e.0
[4294669.515000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.521000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[4294669.522000] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[4294669.522000] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[4294669.523000] ACPI: PCI Interrupt Link [LNKC] (IRQs *4)
[4294669.523000] ACPI: PCI Interrupt Link [LNKD] (IRQs *3)
[4294669.523000] ACPI: PCI Interrupt Link [LNKE] (IRQs *11)
[4294669.524000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3) *0, disabled.
[4294669.524000] ACPI: PCI Interrupt Link [LNKG] (IRQs *4)
[4294669.524000] ACPI: PCI Interrupt Link [LNKH] (IRQs *3)
[4294669.525000] ACPI: Embedded Controller [EC0] (gpe 28) interrupt mode.
[4294669.525000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.525000] pnp: PnP ACPI init
[4294669.527000] pnp: PnP ACPI: found 10 devices
[4294669.527000] PnPBIOS: Disabled by ACPI PNP
[4294669.527000] PCI: Using ACPI for IRQ routing
[4294669.527000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294669.543000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[4294669.543000] PCI: Bus 7, cardbus bridge: 0000:06:09.0
[4294669.543000]   IO window: 00003400-000034ff
[4294669.543000]   IO window: 00003800-000038ff
[4294669.543000]   PREFETCH window: 30000000-31ffffff
[4294669.543000]   MEM window: 34000000-35ffffff
[4294669.543000] PCI: Bridge: 0000:00:1e.0
[4294669.543000]   IO window: 3000-3fff
[4294669.543000]   MEM window: b0100000-b01fffff
[4294669.543000]   PREFETCH window: 30000000-31ffffff
[4294669.543000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294669.543000] ACPI: PCI Interrupt 0000:06:09.0[A] -> GSI 20 (level, low) -> IRQ 169
[4294669.543000] Simple Boot Flag at 0x36 set to 0x1
[4294669.544000] audit: initializing netlink socket (disabled)
[4294669.544000] audit(1156563045.543:1): initialized
[4294669.544000] VFS: Disk quotas dquot_6.5.1
[4294669.544000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.544000] Initializing Cryptographic API
[4294669.544000] io scheduler noop registered
[4294669.544000] io scheduler anticipatory registered
[4294669.544000] io scheduler deadline registered
[4294669.544000] io scheduler cfq registered
[4294669.544000] isapnp: Scanning for PnP cards...
[4294669.902000] isapnp: No Plug & Play device found
[4294669.918000] hpet_acpi_add: no address or irqs in _CRS
[4294669.918000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PSM1] at 0x60,0x64 irq 1,12
[4294669.927000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.927000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.928000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294669.930000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 169
[4294669.930000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[4294669.931000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.931000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294669.931000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294669.931000] mice: PS/2 mouse device common for all mice
[4294669.932000] EISA: Probing bus 0 at eisa.0
[4294669.932000] Cannot allocate resource for EISA slot 1
[4294669.932000] Cannot allocate resource for EISA slot 2
[4294669.932000] Cannot allocate resource for EISA slot 3
[4294669.932000] EISA: Detected 0 cards.
[4294669.932000] NET: Registered protocol family 2
[4294669.942000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[4294669.942000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[4294669.942000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294669.942000] TCP: Hash tables configured (established 16384 bind 16384)
[4294669.942000] TCP reno registered
[4294669.942000] TCP bic registered
[4294669.942000] NET: Registered protocol family 1
[4294669.942000] NET: Registered protocol family 8
[4294669.942000] NET: Registered protocol family 20
[4294669.942000] Using IPI Shortcut mode
[4294669.942000] ACPI wakeup devices:
[4294669.942000] PCIB PS2K PSM1
[4294669.942000] ACPI: (supports S0 S3 S4 S5)
[4294669.942000] Freeing unused kernel memory: 288k freed
[4294669.968000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294669.997000] vga16fb: initializing
[4294669.997000] vga16fb: mapped to 0xc00a0000
[4294670.132000] Console: switching to colour frame buffer device 80x25
[4294670.132000] fb0: VGA16 VGA frame buffer device
[4294671.241000] Capability LSM initialized
[4294671.273000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294671.273000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294671.275000] ACPI: Thermal Zone [THRM] (36 C)
[4294671.712000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[4294671.712000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 177
[4294671.712000] ICH6: chipset revision 3
[4294671.712000] ICH6: not 100% native mode: will probe irqs later
[4294671.712000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:DMA
[4294671.712000] Probing IDE interface ide0...
[4294671.976000] hda: ST9402112A, ATA DISK drive
[4294672.690000] hdb: TSSTcorpCDW/DVD TS-L462C, ATAPI CD/DVD-ROM drive
[4294672.741000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.775000] hda: max request size: 128KiB
[4294672.775000] hda: 78140160 sectors (40007 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[4294672.782000] hda: cache flushes supported
[4294672.782000]  hda: hda1 hda2 < hda5 >
[4294672.827000] hdb: ATAPI 24X DVD-ROM CD-R/RW drive, 1536kB Cache, DMA
[4294672.827000] Uniform CD-ROM driver Revision: 3.20
[4294673.180000] usbcore: registered new driver usbfs
[4294673.180000] usbcore: registered new driver hub
[4294673.181000] USB Universal Host Controller Interface driver v2.3
[4294673.182000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 185
[4294673.182000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294673.182000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294673.183000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294673.183000] uhci_hcd 0000:00:1d.0: irq 185, io base 0x00001820
[4294673.184000] hub 1-0:1.0: USB hub found
[4294673.184000] hub 1-0:1.0: 2 ports detected
[4294673.258000] ieee1394: Initialized config rom entry `ip1394'
[4294673.285000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
[4294673.285000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294673.285000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294673.285000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294673.285000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x00001840
[4294673.285000] hub 2-0:1.0: USB hub found
[4294673.285000] hub 2-0:1.0: 2 ports detected
[4294673.386000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 177
[4294673.386000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294673.386000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294673.386000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294673.386000] uhci_hcd 0000:00:1d.2: irq 177, io base 0x00001860
[4294673.386000] hub 3-0:1.0: USB hub found
[4294673.386000] hub 3-0:1.0: 2 ports detected
[4294673.487000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 201
[4294673.487000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294673.487000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[4294673.487000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294673.487000] uhci_hcd 0000:00:1d.3: irq 201, io base 0x00001880
[4294673.487000] hub 4-0:1.0: USB hub found
[4294673.487000] hub 4-0:1.0: 2 ports detected
[4294673.590000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294673.590000] ACPI: PCI Interrupt 0000:06:09.2[C] -> GSI 22 (level, low) -> IRQ 209
[4294673.609000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 185
[4294673.609000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294673.609000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[4294673.609000] ehci_hcd 0000:00:1d.7: debug port 1
[4294673.609000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294673.609000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294673.609000] ehci_hcd 0000:00:1d.7: irq 185, io mem 0xb0040000
[4294673.613000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294673.613000] hub 5-0:1.0: USB hub found
[4294673.613000] hub 5-0:1.0: 8 ports detected
[4294673.644000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[209]  MMIO=[b0108800-b0108fff]  Max Packet=[2048]
[4294673.738000] Probing IDE interface ide1...
[4294674.315000] Attempting manual resume
[4294674.366000] EXT3-fs: mounted filesystem with ordered data mode.
[4294674.379000] kjournald starting.  Commit interval 5 seconds
[4294687.352000] hw_random: RNG not detected
[4294687.393000] Linux agpgart interface v0.101 (c) Dave Jones
[4294687.454000] agpgart: Detected an Intel 915GM Chipset.
[4294687.454000] agpgart: Detected 7932K stolen memory.
[4294687.544000] agpgart: AGP aperture is 256M @ 0xc0000000
[4294687.667000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 217
[4294687.667000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[4294687.975000] Real Time Clock Driver v1.12
[4294688.029000] intel8x0_measure_ac97_clock: measured 50722 usecs
[4294688.029000] intel8x0: clocking to 48000
[4294688.522000] ieee80211_crypt: registered algorithm 'NULL'
[4294688.533000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[4294688.533000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294688.588000] ACPI: PCI Interrupt 0000:06:09.0[A] -> GSI 20 (level, low) -> IRQ 169
[4294688.588000] Yenta: CardBus bridge found at 0000:06:09.0 [103c:3080]
[4294688.588000] Yenta: Enabling burst memory read transactions
[4294688.588000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294688.588000] Yenta: Routing CardBus interrupts to PCI
[4294688.588000] Yenta TI: socket 0000:06:09.0, mfunc 0x01a01b22, devctl 0x64
[4294688.729000] bcm43xx driver
[4294688.729000] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 18 (level, low) -> IRQ 177
[4294688.762000] sdhci: Secure Digital Host Controller Interface driver, 0.10
[4294688.762000] sdhci: Copyright(c) Pierre Ossman
[4294688.797000] 8139too Fast Ethernet driver 0.9.27
[4294688.797000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 16 (level, low) -> IRQ 201
[4294688.798000] eth1: RealTek RTL8139 at 0xe0334000, 00:16:36:21:ea:95, IRQ 201
[4294688.798000] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294688.811000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 169
[4294688.811000] Socket status: 30000006
[4294688.811000] Yenta: Raising subordinate bus# of parent bus (#06) from #06 to #0a
[4294688.811000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[4294688.811000] cs: IO port probe 0x3000-0x3fff: clean.
[4294688.812000] pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
[4294688.812000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x31ffffff
[4294688.829000] ACPI: PCI Interrupt 0000:06:09.4[A] -> GSI 20 (level, low) -> IRQ 169
[4294688.879000] sdhci: ============== REGISTER DUMP ==============
[4294688.879000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[4294688.879000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[4294688.879000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[4294688.879000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[4294688.879000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[4294688.879000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[4294688.879000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[4294688.879000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[4294688.879000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[4294688.879000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[4294688.879000] sdhci: ===========================================
[4294688.929000] mmc0: SDHCI at 0xb0109400 irq 169 DMA
[4294689.073000] sdhci: ============== REGISTER DUMP ==============
[4294689.073000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[4294689.073000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[4294689.073000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[4294689.073000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[4294689.073000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[4294689.073000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[4294689.073000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[4294689.073000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[4294689.073000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[4294689.073000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[4294689.073000] sdhci: ===========================================
[4294689.124000] mmc1: SDHCI at 0xb0109000 irq 169 DMA
[4294689.224000] sdhci: ============== REGISTER DUMP ==============
[4294689.224000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[4294689.224000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[4294689.224000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[4294689.224000] sdhci: Present:  0x000a0000 | Host ctl: 0x00000000
[4294689.224000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[4294689.224000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[4294689.224000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[4294689.224000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[4294689.224000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[4294689.224000] sdhci: Caps:     0x01821898 | Max curr: 0x00000000
[4294689.224000] sdhci: ===========================================
[4294689.274000] mmc2: SDHCI at 0xb0108400 irq 169 DMA
[4294689.382000] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[4294689.416000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[4294689.543000] ts: Compaq touchscreen protocol output
[4294689.584000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294689.820000] eth0: link down
[4294689.883000] cs: IO port probe 0x100-0x3af: clean.
[4294689.885000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294689.885000] cs: IO port probe 0x820-0x8ff: clean.
[4294689.886000] cs: IO port probe 0xc00-0xcf7: clean.
[4294689.886000] cs: IO port probe 0xa00-0xaff: clean.
[4294689.910000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4294689.919000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4294690.240000] lp: driver loaded but no devices found
[4294690.302000] SCSI subsystem initialized
[4294690.310000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294690.310000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[4294690.310000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294690.374000] Adding 1485972k swap on /dev/hda5.  Priority:-1 extents:1 across:1485972k
[4294690.508000] EXT3 FS on hda1, internal journal
[4294690.691000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294690.691000] md: bitmap version 4.39
[4294690.880000] NET: Registered protocol family 17
[4294691.161000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294691.863000] cdrom: open failed.
[4294697.344000] ACPI: AC Adapter [ACAD] (on-line)
[4294697.485000] ACPI: Battery Slot [BAT0] (battery present)
[4294697.546000] ACPI: Power Button (FF) [PWRF]
[4294697.546000] ACPI: Power Button (CM) [PRWB]
[4294697.546000] ACPI: Sleep Button (CM) [SLPB]
[4294697.546000] ACPI: Lid Switch [LID]
[4294697.646000] ibm_acpi: ec object not found
[4294697.668000] pcc_acpi: loading...
[4294697.710000] wmi_add device=de1ae000
[4294697.710000] calling WQBA
[4294697.766000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[4294702.856000] [drm] Initialized drm 1.0.1 20051102
[4294702.858000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 201
[4294702.859000] [drm] Initialized i915 1.4.0 20060119 on minor 0
[4294703.299000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4294704.935000] ppdev: user-space parallel port driver
[4294705.323000] apm: BIOS not found.
[4294708.519000] Bluetooth: Core ver 2.8
[4294708.519000] NET: Registered protocol family 31
[4294708.519000] Bluetooth: HCI device and connection manager initialized
[4294708.519000] Bluetooth: HCI socket layer initialized
[4294708.864000] Bluetooth: L2CAP ver 2.8
[4294708.864000] Bluetooth: L2CAP socket layer initialized
[4294708.893000] Bluetooth: RFCOMM socket layer initialized
[4294708.893000] Bluetooth: RFCOMM TTY layer initialized
[4294708.893000] Bluetooth: RFCOMM ver 1.7
[4294712.262000] NET: Registered protocol family 10
[4294712.262000] lo: Disabled Privacy Extensions
[4294712.262000] IPv6 over IPv4 tunneling driver
[4294722.263000] eth0: no IPv6 routers present
[4295182.135000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[4295182.396000] usbcore: registered new driver hiddev
[4295182.415000] drivers/usb/input/hid-core.c: ctrl urb status -71 received
[4295182.415000] input: USB Mouse as /class/input/input2
[4295182.415000] input: USB HID v1.00 Mouse [USB Mouse] on usb-0000:00:1d.1-1
[4295182.415000] usbcore: registered new driver usbhid
[4295182.415000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4295208.671000] eth0: link down
[4295209.128000] hub 2-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[4295209.128000] usb 2-1: USB disconnect, address 2
[4295209.231000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[4295209.403000] drivers/usb/input/hid-core.c: ctrl urb status -71 received
[4295209.403000] input: USB Mouse as /class/input/input3
[4295209.403000] input: USB HID v1.00 Mouse [USB Mouse] on usb-0000:00:1d.1-1
[4295210.560000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4295221.471000] eth0: link down
[4295222.998000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4295384.705000] CSLIP: code copyright 1989 Regents of the University of California
[4295384.711000] PPP generic driver version 2.4.2
[4295384.811000] NET: Registered protocol family 24
[4295388.411000] ip_tables: (C) 2000-2002 Netfilter core team
[4296215.023000] pcmcia: Detected deprecated PCMCIA ioctl usage.
[4296215.023000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgr ade to new tools.
[4296215.023000] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
neil@neil-laptop:/media$



0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:06:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:06:09.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller


Any help would be appreciated

Thanx

---

### Post by darkshadow on 2006-08-27
According to the lspci output I have the exact same one in my laptop. Out of all the cards it can read I have only been capable of testing 2 SD works perfect in a clean install and XD does not work but I only have very sporadic times when I get access to one so I have not been able to try fixing it.

I am using 64bit Ubuntu

---

### Post by neil_707 on 2006-08-27
I need to read a SD card too..Any idea how to proceed?

---

### Post by Tom Tiger on 2006-09-02
I've got the same problem with my Toshiba Portege R100 and my Toshiba Satellite Pro 6100.  The SD reader onboard is a PCI one and is seen by Ubuntu but it refuses to work, my other usb reader works but won't allow me to write more than 600 mb on a 1GB card,  an interesting puzzle indeed.

Actually... I'm a bit lost on this one.

---

