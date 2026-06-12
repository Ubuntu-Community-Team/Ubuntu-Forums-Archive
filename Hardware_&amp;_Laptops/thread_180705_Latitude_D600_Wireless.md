---
title: "Latitude D600 Wireless"
date: 2006-05-22
forum: Hardware &amp; Laptops
---

### Post by jdavidson on 2006-05-22
The one and only hurdle from me making the permanent switch to Ubuntu here is my wireless.  I'll post the info I get from a few commands.  I've tried using Ndiswrapper with all different kinds of drivers from Linuxant ones, to Dell ones, to Acer ones.  I'm using Dapper Drake and the latest version of ndiswrapper.  My System > Administration > Networking shows Eth1 as a wireless connection but I cannot get it to activate.  Please help, I wish to cast of the shackles of windows once and for all.

lspci

0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless  LAN Controller (rev 02)

_*dmesg*_
[4294667.296000] Linux version 2.6.15-22-386 (buildd@vernadsky) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sun May 7 15:49:09 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[4294667.296000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001ffae000 (usable)
[4294667.296000]  BIOS-e820: 000000001ffae000 - 0000000020000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 511MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 130990
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 126894 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fdf00
[4294667.296000] ACPI: RSDT (v001 DELL    CPi R   0x27d30c0f ASL  0x00000061) @ 0x1fff0000
[4294667.296000] ACPI: FADT (v001 DELL    CPi R   0x27d30c0f ASL  0x00000061) @ 0x1fff0400
[4294667.296000] ACPI: ASF! (v016 DELL    CPi R   0x27d30c0f ASL  0x00000061) @ 0x1fff0800
[4294667.296000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] Allocating PCI resources starting at 30000000 (gap: 20000000:deda0000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/mapper/Ubuntu-root ro quiet splash
[4294667.296000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01401000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1399.034 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.726000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294670.727000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294670.744000] Memory: 508596k/523960k available (1975k kernel code, 14792k reserved, 607k data, 288k init, 0k highmem)
[4294670.744000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.804000] Calibrating delay using timer specific routine.. 2799.18 BogoMIPS (lpj=1399590)
[4294670.804000] Security Framework v1.0.0 initialized
[4294670.804000] SELinux:  Disabled at boot.
[4294670.804000] Mount-cache hash table entries: 512
[4294670.804000] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[4294670.804000] CPU: After vendor identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[4294670.804000] CPU: L1 I cache: 32K, L1 D cache: 32K
[4294670.804000] CPU: L2 cache: 1024K
[4294670.804000] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00000040 00000180 00000000 00000000
[4294670.804000] mtrr: v2.0 (20020519)
[4294670.804000] CPU: Intel(R) Pentium(R) M processor 1400MHz stepping 05
[4294670.804000] Enabling fast FPU save and restore... done.
[4294670.804000] Enabling unmasked SIMD FPU exception support... done.
[4294670.804000] Checking 'hlt' instruction... OK.
[4294670.808000] checking if image is initramfs... it is
[4294671.868000] Freeing initrd memory: 6607k freed
[4294671.887000] ACPI: Looking for DSDT ... not found!
[4294671.888000] ACPI: setting ELCR to 0200 (from 0800)
[4294671.891000] NET: Registered protocol family 16
[4294671.891000] EISA bus registered
[4294671.891000] ACPI: bus type pci registered
[4294671.908000] PCI: PCI BIOS revision 2.10 entry at 0xfc97e, last bus=2
[4294671.908000] PCI: Using configuration type 1
[4294671.908000] ACPI: Subsystem revision 20051216
[4294671.920000] ACPI: Interpreter enabled
[4294671.920000] ACPI: Using PIC for interrupt routing
[4294671.921000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.921000] PCI: Probing PCI hardware (bus 00)
[4294671.921000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294671.933000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[4294671.933000] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[4294671.933000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294671.934000] Boot video device is 0000:01:00.0
[4294671.934000] PCI: Transparent bridge - 0000:00:1e.0
[4294671.934000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.957000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[4294671.957000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[4294671.958000] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[4294671.958000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[4294671.958000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294671.958000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294671.960000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294671.961000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[4294671.961000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.961000] pnp: PnP ACPI init
[4294671.979000] pnp: PnP ACPI: found 11 devices
[4294671.979000] PnPBIOS: Disabled by ACPI PNP
[4294671.979000] PCI: Using ACPI for IRQ routing
[4294671.979000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.991000] pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
[4294671.991000] pnp: 00:01: ioport range 0x800-0x805 could not be reserved
[4294671.991000] pnp: 00:01: ioport range 0x808-0x80f could not be reserved
[4294671.991000] pnp: 00:02: ioport range 0xf400-0xf4fe has been reserved
[4294671.991000] pnp: 00:02: ioport range 0x806-0x807 has been reserved
[4294671.991000] pnp: 00:02: ioport range 0x810-0x85f could not be reserved
[4294671.991000] pnp: 00:02: ioport range 0x860-0x87f has been reserved
[4294671.991000] pnp: 00:02: ioport range 0x880-0x8bf has been reserved
[4294671.991000] pnp: 00:02: ioport range 0x8c0-0x8df has been reserved
[4294671.991000] pnp: 00:07: ioport range 0x900-0x97f has been reserved
[4294671.992000] PCI: Bridge: 0000:00:01.0
[4294671.992000]   IO window: c000-cfff
[4294671.992000]   MEM window: fc000000-fdffffff
[4294671.992000]   PREFETCH window: e8000000-efffffff
[4294671.992000] PCI: Bus 3, cardbus bridge: 0000:02:01.0
[4294671.992000]   IO window: 0000d000-0000d0ff
[4294671.992000]   IO window: 0000d400-0000d4ff
[4294671.992000]   PREFETCH window: 30000000-31ffffff
[4294671.992000]   MEM window: f6000000-f7ffffff
[4294671.992000] PCI: Bus 7, cardbus bridge: 0000:02:01.1
[4294671.992000]   IO window: 0000d800-0000d8ff
[4294671.992000]   IO window: 0000dc00-0000dcff
[4294671.992000]   PREFETCH window: 32000000-33ffffff
[4294671.992000]   MEM window: f8000000-f9ffffff
[4294671.992000] PCI: Bridge: 0000:00:1e.0
[4294671.992000]   IO window: d000-efff
[4294671.992000]   MEM window: f6000000-fbffffff
[4294671.992000]   PREFETCH window: 30000000-33ffffff
[4294671.992000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294671.992000] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
[4294671.992000] **** SET: Misaligned resource pointer: dfe9c5c2 Type 07 Len 0
[4294671.992000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294671.992000] PCI: setting IRQ 11 as level-triggered
[4294671.992000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294671.992000] PCI: Enabling device 0000:02:01.1 (0000 -> 0003)
[4294671.992000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294671.992000] audit: initializing netlink socket (disabled)
[4294671.992000] audit(1148140402.991:1): initialized
[4294671.993000] VFS: Disk quotas dquot_6.5.1
[4294671.993000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.993000] Initializing Cryptographic API
[4294671.993000] io scheduler noop registered
[4294671.993000] io scheduler anticipatory registered
[4294671.993000] io scheduler deadline registered
[4294671.993000] io scheduler cfq registered
[4294671.993000] isapnp: Scanning for PnP cards...
[4294672.349000] isapnp: No Plug & Play device found
[4294672.363000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294672.367000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294672.368000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.368000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294672.368000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.370000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.370000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294672.370000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294672.370000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294672.370000] mice: PS/2 mouse device common for all mice
[4294672.371000] EISA: Probing bus 0 at eisa.0
[4294672.371000] EISA: Detected 0 cards.
[4294672.371000] NET: Registered protocol family 2
[4294672.380000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294672.381000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[4294672.381000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[4294672.381000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294672.381000] TCP: Hash tables configured (established 32768 bind 32768)
[4294672.381000] TCP reno registered
[4294672.381000] TCP bic registered
[4294672.381000] NET: Registered protocol family 1
[4294672.381000] NET: Registered protocol family 8
[4294672.381000] NET: Registered protocol family 20
[4294672.381000] Using IPI Shortcut mode
[4294672.381000] ACPI wakeup devices:
[4294672.381000]  LID PBTN PCI0 USB0 USB1 USB2 USB3 MODM PCIE
[4294672.381000] ACPI: (supports S0 S1 S3 S4 S5)
[4294672.381000] Freeing unused kernel memory: 288k freed
[4294672.432000] vga16fb: initializing
[4294672.432000] vga16fb: mapped to 0xc00a0000
[4294672.545000] Console: switching to colour frame buffer device 80x25
[4294672.545000] fb0: VGA16 VGA frame buffer device
[4294673.610000] Capability LSM initialized
[4294673.775000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[4294673.775000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294673.779000] ACPI: Thermal Zone [THM] (27 C)
[4294674.237000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[4294674.237000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294674.237000] **** SET: Misaligned resource pointer: dfc851c2 Type 07 Len 0
[4294674.238000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294674.238000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294674.238000] ICH4: chipset revision 1
[4294674.238000] ICH4: not 100% native mode: will probe irqs later

[4294674.238000] Probing IDE interface ide0...
[4294674.502000] hda: IC25N020ATMR04-0, ATA DISK drive
[4294675.114000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294675.136000] Probing IDE interface ide1...
[4294675.808000] hdc: HL-DT-STCD-RW/DVD-ROM GCC-4243N, ATAPI CD/DVD-ROM drive
[4294676.114000] ide1 at 0x170-0x177,0x376 on irq 15
[4294676.122000] hda: max request size: 1024KiB
[4294676.130000] hda: 39070080 sectors (20003 MB) w/1740KiB Cache, CHS=16383/255/63, UDMA(100)
[4294676.130000] hda: cache flushes supported
[4294676.130000]  hda: hda1 < hda5 hda6 >
[4294676.180000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294676.180000] Uniform CD-ROM driver Revision: 3.20
[4294676.448000] usbcore: registered new driver usbfs
[4294676.448000] usbcore: registered new driver hub
[4294676.450000] USB Universal Host Controller Interface driver v2.3
[4294676.450000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294676.450000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294676.450000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294676.451000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294676.451000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[4294676.451000] hub 1-0:1.0: USB hub found
[4294676.451000] hub 1-0:1.0: 2 ports detected
[4294676.552000] ACPI: PCI Interrupt 0000:00:1d.1[b] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294676.552000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294676.552000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294676.552000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294676.552000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[4294676.552000] hub 2-0:1.0: USB hub found
[4294676.552000] hub 2-0:1.0: 2 ports detected
[4294676.653000] **** SET: Misaligned resource pointer: de9bcdc2 Type 07 Len 0
[4294676.653000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294676.653000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294676.653000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294676.653000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294676.653000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294676.653000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[4294676.653000] hub 3-0:1.0: USB hub found
[4294676.653000] hub 3-0:1.0: 2 ports detected
[4294676.755000] **** SET: Misaligned resource pointer: de9bcac2 Type 07 Len 0
[4294676.755000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[4294676.755000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[4294676.755000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294676.755000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[4294676.755000] ehci_hcd 0000:00:1d.7: debug port 1
[4294676.755000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294676.756000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[4294676.756000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
[4294676.760000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294676.760000] hub 4-0:1.0: USB hub found
[4294676.760000] hub 4-0:1.0: 6 ports detected
[4294676.980000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[4294677.359000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[4294677.525000] usbcore: registered new driver hiddev
[4294677.546000] input: PS/2+USB Mouse as /class/input/input1
[4294677.546000] input: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.1-1
[4294677.546000] usbcore: registered new driver usbhid
[4294677.546000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294677.783000] Attempting manual resume
[4294677.845000] EXT3-fs: mounted filesystem with ordered data mode.
[4294677.857000] kjournald starting.  Commit interval 5 seconds
[4294690.605000] ts: Compaq touchscreen protocol output
[4294691.907000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294691.941000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294691.953000] Linux agpgart interface v0.101 (c) Dave Jones
[4294691.974000] agpgart: Detected an Intel 855PM Chipset.
[4294691.982000] agpgart: AGP aperture is 128M @ 0xe0000000
[4294692.003000] hw_random: cannot enable RNG, aborting
[4294692.294000] tg3.c:v3.47 (Dec 28, 2005)
[4294692.294000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294692.647000] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0d:56:e3:5e:dc
[4294692.647000] eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1]
[4294692.647000] eth0: dma_rwctrl[763f0000]
[4294692.660000] Real Time Clock Driver v1.12
[4294692.692000] input: PC Speaker as /class/input/input2
[4294692.881000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294692.881000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:011d]
[4294692.881000] Yenta O2: res at 0x94/0xD4: 00/ea
[4294692.881000] Yenta O2: enabling read prefetch/write burst
[4294693.003000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[4294693.003000] Socket status: 30000006
[4294693.003000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[4294693.003000] cs: IO port probe 0xd000-0xefff: clean.
[4294693.004000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[4294693.004000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[4294693.032000] **** SET: Misaligned resource pointer: dbeba5c2 Type 07 Len 0
[4294693.032000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7
[4294693.032000] PCI: setting IRQ 7 as level-triggered
[4294693.032000] ACPI: PCI Interrupt 0000:00:1f.5[b] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[4294693.032000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294693.098000] input: DualPoint Stick as /class/input/input3
[4294693.100000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294693.100000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:011d]
[4294693.120000] ieee80211_crypt: registered algorithm 'NULL'
[4294693.120000] input: AlpsPS/2 ALPS DualPoint TouchPad as /class/input/input4
[4294693.169000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[4294693.169000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294693.226000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[4294693.226000] Socket status: 30000410
[4294693.226000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[4294693.226000] cs: IO port probe 0xd000-0xefff: clean.
[4294693.226000] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[4294693.226000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[4294693.233000] bcm43xx driver
[4294693.843000] intel8x0_measure_ac97_clock: measured 50440 usecs
[4294693.843000] intel8x0: clocking to 48000
[4294693.847000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[4294693.861000] pccard: PCMCIA card inserted into slot 1
[4294694.025000] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xfa1fffff 0xfae00000-0xfb3fffff
[4294694.029000] pcmcia: registering new device pcmcia1.0
[4294694.096000] cs: IO port probe 0x100-0x3af: clean.
[4294694.097000] cs: IO port probe 0x3e0-0x4ff: clean.
[4294694.097000] cs: IO port probe 0x820-0x8ff: clean.
[4294694.097000] cs: IO port probe 0xc00-0xcf7: clean.
[4294694.098000] cs: IO port probe 0xa00-0xaff: clean.
[4294694.099000] cs: IO port probe 0x100-0x3af: clean.
[4294694.100000] cs: IO port probe 0x3e0-0x4ff: clean.
[4294694.100000] cs: IO port probe 0x820-0x8ff: clean.
[4294694.100000] cs: IO port probe 0xc00-0xcf7: clean.
[4294694.101000] cs: IO port probe 0xa00-0xaff: clean.
[4294694.532000] lp: driver loaded but no devices found
[4294694.597000] Adding 819192k swap on /dev/mapper/Ubuntu-swap_1.  Priority:-1 extents:1 across:819192k
[4294694.790000] EXT3 FS on dm-0, internal journal
[4294694.984000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294694.984000] md: bitmap version 4.39
[4294697.255000] kjournald starting.  Commit interval 5 seconds
[4294697.255000] EXT3 FS on hda5, internal journal
[4294697.255000] EXT3-fs: mounted filesystem with ordered data mode.
[4294698.812000] ACPI: AC Adapter [AC] (on-line)
[4294699.086000] ACPI: Battery Slot [BAT0] (battery present)
[4294699.086000] ACPI: Battery Slot [BAT1] (battery absent)
[4294699.163000] ACPI: Lid Switch [LID]
[4294699.163000] ACPI: Power Button (CM) [PBTN]
[4294699.163000] ACPI: Sleep Button (CM) [SBTN]
[4294699.273000] ibm_acpi: ec object not found
[4294699.296000] pcc_acpi: loading...
[4294699.383000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294704.651000] [drm] Initialized drm 1.0.0 20040925
[4294704.668000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294704.669000] [drm] Initialized radeon 1.19.0 20050911 on minor 0:
[4294705.859000] ppdev: user-space parallel port driver
[4294706.077000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294706.077000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[4294706.077000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[4294706.446000] [drm] Loading R200 Microcode
[4294706.594000] apm: BIOS not found.
[4294712.989000] Bluetooth: Core ver 2.8
[4294712.989000] NET: Registered protocol family 31
[4294712.989000] Bluetooth: HCI device and connection manager initialized
[4294712.989000] Bluetooth: HCI socket layer initialized
[4294713.005000] Bluetooth: L2CAP ver 2.8
[4294713.005000] Bluetooth: L2CAP socket layer initialized
[4294713.010000] Bluetooth: RFCOMM socket layer initialized
[4294713.010000] Bluetooth: RFCOMM TTY layer initialized
[4294713.010000] Bluetooth: RFCOMM ver 1.7
[4369188.740000] ibm_acpi: ec object not found
[4385416.673000] NET: Registered protocol family 10
[4385416.673000] lo: Disabled Privacy Extensions
[4385416.673000] IPv6 over IPv4 tunneling driver
[4385422.767000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4385422.930000] ISO 9660 Extensions: RRIP_1991A
[4385480.133000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[4385482.117000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[4385482.117000] tg3: eth0: Flow control is off for TX and off for RX.
[4385482.118000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[4385492.596000] eth0: no IPv6 routers present

*_iwconfig_*

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

*_ndiswrapper -l_*

Installed ndis drivers:
bcmwl5          driver present, hardware present

---

### Post by joshmachine on 2006-05-22
Judging from the output of your dmesg, it looks like the other driver for you hardware is being loaded instead of ndiswrapper.

...
[4294693.233000] bcm43xx driver
...

disabling this has been covered fairly extensively on the forums.

try this at the command line:

sudo rmmod bcm43xx
sudo modprobe ndiswrapper

sometimes you have to 'rmmod ndiswrapper' 'modprobe ndiswrapper' a second time to get it working.


add the following line in the '/etc/modprobe.d/blacklist'

blacklist bcm43xx


it should work fine the next time you reboot.

let us know how it works out.

---

