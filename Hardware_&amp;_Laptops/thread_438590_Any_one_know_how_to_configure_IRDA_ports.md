---
title: "Any one know how to configure IRDA ports?"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by grahams on 2007-05-09
I thought setting up irda on my Compaq n610 laptop would be easy as it's old technology, but I confess I'm stump.

I'm running 6.10 - 2.6.17-11
The ir port is turned on in bios and works with Windoze.


This is what i've done so far:

install irda-utils and toshset, also gammu and wammu as I'm hoping to talk with my Nokia 6800 phone.

I've added  irda and smc-ircc (I believe my machine has a smc ircc controller) to /etc/modules and rebooted.

My dmesg output does not look promising (interrupt mismatch at 17179623.620000)

```
[17179569.380000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.384000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.420000] Memory: 1029516k/1048384k available (1911k kernel code, 18124k reserved, 1073k data, 308k init, 130880k highmem)
[17179569.420000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.500000] Calibrating delay using timer specific routine.. 3992.43 BogoMIPS (lpj=7984876)
[17179569.500000] Security Framework v1.0.0 initialized
[17179569.500000] SELinux:  Disabled at boot.
[17179569.500000] Mount-cache hash table entries: 512
[17179569.500000] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[17179569.500000] CPU: After vendor identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[17179569.500000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179569.500000] CPU: L2 cache: 512K
[17179569.500000] CPU: Hyper-Threading is disabled
[17179569.500000] CPU: After all inits, caps: bfebf9ff 00000000 00000000 00000080 00004400 00000000 00000000
[17179569.500000] Checking 'hlt' instruction... OK.
[17179569.516000] SMP alternatives: switching to UP code
[17179569.516000] Freeing SMP alternatives: 16k freed
[17179569.516000] checking if image is initramfs... it is
[17179570.136000] Freeing initrd memory: 5343k freed
[17179570.136000] ACPI: Core revision 20060707
[17179570.136000] ACPI: Looking for DSDT ... not found!
[17179570.140000] ACPI: setting ELCR to 0200 (from 0c00)
[17179570.176000] CPU0: Intel Mobile Intel(R) Pentium(R) 4 - M CPU 2.00GHz stepping 07
[17179570.176000] SMP motherboard not detected.
[17179570.176000] Local APIC not detected. Using dummy APIC emulation.
[17179570.176000] Brought up 1 CPUs
[17179570.176000] migration_cost=0
[17179570.176000] NET: Registered protocol family 16
[17179570.176000] EISA bus registered
[17179570.176000] ACPI: bus type pci registered
[17179570.176000] PCI: PCI BIOS revision 2.10 entry at 0xf03a2, last bus=4
[17179570.176000] PCI: Using configuration type 1
[17179570.176000] Setting up standard PCI resources
[17179570.192000] ACPI: Interpreter enabled
[17179570.192000] ACPI: Using PIC for interrupt routing
[17179570.192000] ACPI: PCI Root Bridge [C045] (0000:00)
[17179570.192000] PCI: Probing PCI hardware (bus 00)
[17179570.192000] ACPI: Assume root bridge [\_SB_.C045] bus is 0
[17179570.204000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179570.204000] PCI quirk: region 1100-113f claimed by ICH4 GPIO
[17179570.204000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.204000] Boot video device is 0000:01:00.0
[17179570.204000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.204000] PCI: Bus #04 (-#07) is hidden behind transparent bridge #02 (-#04) (try 'pci=assign-busses')
[17179570.204000] Please report the result to linux-kernel to fix this permanently
[17179570.204000] ACPI: PCI Interrupt Routing Table [\_SB_.C045._PRT]
[17179570.212000] ACPI: PCI Interrupt Routing Table [\_SB_.C045.C046._PRT]
[17179570.212000] ACPI: PCI Interrupt Routing Table [\_SB_.C045.C058._PRT]
[17179570.216000] ACPI: Power Resource [C15D] (on)
[17179570.216000] ACPI: Power Resource [C171] (on)
[17179570.220000] ACPI: Power Resource [C175] (on)
[17179570.220000] ACPI: Power Resource [C178] (on)
[17179570.220000] ACPI: Power Resource [C181] (on)
[17179570.224000] ACPI: PCI Interrupt Link [C0C0] (IRQs 5 10 *11)
[17179570.224000] ACPI: PCI Interrupt Link [C0C1] (IRQs 5 10 *11)
[17179570.224000] ACPI: PCI Interrupt Link [C0C2] (IRQs 5 10 11) *0, disabled.
[17179570.228000] ACPI: PCI Interrupt Link [C0C3] (IRQs 5 10 *11)
[17179570.228000] ACPI: PCI Interrupt Link [C0C4] (IRQs 5 *10 11)
[17179570.228000] ACPI: Blank IRQ resource
[17179570.228000] ACPI: Resource is not an IRQ entry
[17179570.228000] ACPI: PCI Interrupt Link [C0C5] (IRQs) *0, disabled.
[17179570.228000] ACPI: Blank IRQ resource
[17179570.228000] ACPI: Resource is not an IRQ entry
[17179570.228000] ACPI: PCI Interrupt Link [C0C6] (IRQs) *0, disabled.
[17179570.228000] ACPI: Blank IRQ resource
[17179570.228000] ACPI: Resource is not an IRQ entry
[17179570.228000] ACPI: PCI Interrupt Link [C0C7] (IRQs) *0, disabled.
[17179570.232000] ACPI: Power Resource [C1FC] (off)
[17179570.232000] ACPI: Power Resource [C1FD] (off)
[17179570.232000] ACPI: Power Resource [C1FE] (off)
[17179570.232000] ACPI: Power Resource [C1FF] (off)
[17179570.232000] ACPI: Power Resource [C200] (off)
[17179570.232000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.232000] pnp: PnP ACPI init
[17179570.252000] pnp: PnP ACPI: found 14 devices
[17179570.252000] PnPBIOS: Disabled by ACPI PNP
[17179570.252000] PCI: Using ACPI for IRQ routing
[17179570.252000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.300000] pnp: 00:0c: ioport range 0x140-0x14f has been reserved
[17179570.300000] pnp: 00:0d: ioport range 0x4d0-0x4d1 has been reserved
[17179570.300000] pnp: 00:0d: ioport range 0x1000-0x107f could not be reserved
[17179570.300000] pnp: 00:0d: ioport range 0x1100-0x113f has been reserved
[17179570.300000] pnp: 00:0d: ioport range 0x1200-0x121f has been reserved
[17179570.300000] PCI: Bridge: 0000:00:01.0
[17179570.300000]   IO window: 3000-3fff
[17179570.300000]   MEM window: 40400000-404fffff
[17179570.300000]   PREFETCH window: 48000000-4fffffff
[17179570.300000] PCI: Bus 3, cardbus bridge: 0000:02:06.0
[17179570.300000]   IO window: 00002800-000028ff
[17179570.300000]   IO window: 00002c00-00002cff
[17179570.300000]   PREFETCH window: 50000000-51ffffff
[17179570.300000]   MEM window: 56000000-57ffffff
[17179570.300000] PCI: Bus 4, cardbus bridge: 0000:02:06.1
[17179570.300000]   IO window: 00001400-000014ff
[17179570.300000]   IO window: 00001800-000018ff
[17179570.304000]   PREFETCH window: 52000000-53ffffff
[17179570.304000]   MEM window: 58000000-59ffffff
[17179570.304000] PCI: Bridge: 0000:00:1e.0
[17179570.304000]   IO window: 2000-2fff
[17179570.304000]   MEM window: 40000000-403fffff
[17179570.304000]   PREFETCH window: 50000000-53ffffff
[17179570.304000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.304000] ACPI: PCI Interrupt Link [C0C3] enabled at IRQ 11
[17179570.304000] PCI: setting IRQ 11 as level-triggered
[17179570.304000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [C0C3] -> GSI 11 (level, low) -> IRQ 11
[17179570.304000] ACPI: PCI Interrupt 0000:02:06.1[A] -> Link [C0C3] -> GSI 11 (level, low) -> IRQ 11
[17179570.304000] NET: Registered protocol family 2
[17179570.340000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.340000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179570.340000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179570.340000] TCP: Hash tables configured (established 131072 bind 65536)
[17179570.340000] TCP reno registered
[17179570.344000] audit: initializing netlink socket (disabled)
[17179570.344000] audit(1178736805.344:1): initialized
[17179570.344000] highmem bounce pool size: 64 pages
[17179570.344000] VFS: Disk quotas dquot_6.5.1
[17179570.344000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.344000] Initializing Cryptographic API
[17179570.344000] io scheduler noop registered
[17179570.344000] io scheduler anticipatory registered
[17179570.344000] io scheduler deadline registered
[17179570.344000] io scheduler cfq registered (default)
[17179570.344000] isapnp: Scanning for PnP cards...
[17179570.696000] isapnp: No Plug & Play device found
[17179570.728000] Real Time Clock Driver v1.12ac
[17179570.728000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.728000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.728000] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[17179570.728000] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.728000] mice: PS/2 mouse device common for all mice
[17179570.732000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.732000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.732000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.732000] PNP: PS/2 Controller [PNP0303:C17E,PNP0f13:C17F] at 0x60,0x64 irq 1,12
[17179570.732000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179570.732000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179570.732000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179570.732000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179570.732000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179570.732000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.736000] EISA: Probing bus 0 at eisa.0
[17179570.736000] Cannot allocate resource for EISA slot 1
[17179570.736000] Cannot allocate resource for EISA slot 2
[17179570.736000] Cannot allocate resource for EISA slot 3
[17179570.736000] Cannot allocate resource for EISA slot 4
[17179570.736000] EISA: Detected 0 cards.
[17179570.736000] TCP bic registered
[17179570.736000] NET: Registered protocol family 1
[17179570.736000] NET: Registered protocol family 8
[17179570.736000] NET: Registered protocol family 20
[17179570.736000] Using IPI No-Shortcut mode
[17179570.736000] ACPI: (supports S0 S3 S4 S5)
[17179570.736000] Freeing unused kernel memory: 308k freed
[17179570.788000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179570.816000] Capability LSM initialized
[17179570.864000] ACPI: Transitioning device [C201] to D3
[17179570.864000] ACPI: Transitioning device [C201] to D3
[17179570.864000] ACPI: Fan [C201] (off)
[17179570.864000] ACPI: Transitioning device [C202] to D3
[17179570.864000] ACPI: Transitioning device [C202] to D3
[17179570.864000] ACPI: Fan [C202] (off)
[17179570.864000] ACPI: Transitioning device [C203] to D3
[17179570.864000] ACPI: Transitioning device [C203] to D3
[17179570.864000] ACPI: Fan [C203] (off)
[17179570.864000] ACPI: Transitioning device [C204] to D3
[17179570.864000] ACPI: Transitioning device [C204] to D3
[17179570.864000] ACPI: Fan [C204] (off)
[17179570.864000] ACPI: Transitioning device [C205] to D3
[17179570.864000] ACPI: Transitioning device [C205] to D3
[17179570.864000] ACPI: Fan [C205] (off)
[17179570.872000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179570.872000] ACPI: Processor [C000] (supports 8 throttling states)
[17179570.884000] ACPI: Thermal Zone [TZ1] (60 C)
[17179570.884000] ACPI: Thermal Zone [C1FA] (45 C)
[17179570.884000] ACPI: Thermal Zone [C1FB] (16 C)
[17179571.524000] ICH3M: IDE controller at PCI slot 0000:00:1f.1
[17179571.524000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179571.524000] ACPI: PCI Interrupt Link [C0C2] enabled at IRQ 10
[17179571.524000] PCI: setting IRQ 10 as level-triggered
[17179571.524000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [C0C2] -> GSI 10 (level, low) -> IRQ 10
[17179571.524000] ICH3M: chipset revision 2
[17179571.524000] ICH3M: not 100% native mode: will probe irqs later
[17179571.524000]     ide0: BM-DMA at 0x4440-0x4447, BIOS settings: hda:DMA, hdb:pio
[17179571.524000]     ide1: BM-DMA at 0x4448-0x444f, BIOS settings: hdc:DMA, hdd:pio
[17179571.524000] Probing IDE interface ide0...
[17179571.816000] hda: FUJITSU MHS2040AT D, ATA DISK drive
[17179572.488000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179572.508000] Probing IDE interface ide1...
[17179573.244000] hdc: DW-224E, ATAPI CD/DVD-ROM drive
[17179573.916000] ide1 at 0x170-0x177,0x376 on irq 15
[17179573.928000] hda: max request size: 128KiB
[17179573.940000] hda: 78140160 sectors (40007 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179573.940000] hda: cache flushes supported
[17179573.940000]  hda: hda1 hda2 hda3 hda4
[17179573.988000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 1658kB Cache, DMA
[17179573.988000] Uniform CD-ROM driver Revision: 3.20
[17179574.480000] usbcore: registered new driver usbfs
[17179574.480000] usbcore: registered new driver hub
[17179574.484000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179574.484000] ACPI: PCI Interrupt Link [C0C4] enabled at IRQ 10
[17179574.484000] ACPI: PCI Interrupt 0000:02:0e.0[A] -> Link [C0C4] -> GSI 10 (level, low) -> IRQ 10
[17179574.484000] ohci_hcd 0000:02:0e.0: OHCI Host Controller
[17179574.484000] ohci_hcd 0000:02:0e.0: new USB bus registered, assigned bus number 1
[17179574.484000] ohci_hcd 0000:02:0e.0: irq 10, io mem 0x40180000
[17179575.044000] usb usb1: configuration #1 chosen from 1 choice
[17179575.044000] hub 1-0:1.0: USB hub found
[17179575.044000] hub 1-0:1.0: 3 ports detected
[17179575.560000] ACPI: PCI Interrupt 0000:02:0e.2[C] -> Link [C0C4] -> GSI 10 (level, low) -> IRQ 10
[17179575.560000] ehci_hcd 0000:02:0e.2: EHCI Host Controller
[17179575.560000] ehci_hcd 0000:02:0e.2: new USB bus registered, assigned bus number 2
[17179575.584000] ehci_hcd 0000:02:0e.2: irq 10, io mem 0x40300000
[17179575.584000] ehci_hcd 0000:02:0e.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[17179575.584000] usb usb2: configuration #1 chosen from 1 choice
[17179575.584000] hub 2-0:1.0: USB hub found
[17179575.584000] hub 2-0:1.0: 5 ports detected
[17179575.688000] ACPI: PCI Interrupt 0000:02:0e.1[B] -> Link [C0C4] -> GSI 10 (level, low) -> IRQ 10
[17179575.688000] ohci_hcd 0000:02:0e.1: OHCI Host Controller
[17179575.688000] ohci_hcd 0000:02:0e.1: new USB bus registered, assigned bus number 3
[17179575.688000] ohci_hcd 0000:02:0e.1: irq 10, io mem 0x40200000
[17179576.248000] usb usb3: configuration #1 chosen from 1 choice
[17179576.248000] hub 3-0:1.0: USB hub found
[17179576.248000] hub 3-0:1.0: 2 ports detected
[17179576.768000] usb 2-2: new high speed USB device using ehci_hcd and address 3
[17179576.860000] Attempting manual resume
[17179576.900000] usb 2-2: configuration #1 chosen from 1 choice
[17179576.916000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179576.916000] EXT3-fs: write access will be enabled during recovery.
[17179577.084000] usbcore: registered new driver libusual
[17179577.096000] SCSI subsystem initialized
[17179577.100000] Initializing USB Mass Storage driver...
[17179577.388000] usb 1-1: new full speed USB device using ohci_hcd and address 2
[17179577.600000] usb 1-1: configuration #1 chosen from 1 choice
[17179577.600000] hub 1-1:1.0: USB hub found
[17179577.604000] hub 1-1:1.0: 4 ports detected
[17179578.032000] usb 1-3: new full speed USB device using ohci_hcd and address 3
[17179578.244000] usb 1-3: configuration #1 chosen from 1 choice
[17179578.244000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179578.244000] usb-storage: device found at 3
[17179578.244000] usb-storage: waiting for device to settle before scanning
[17179578.256000] usbcore: registered new driver usb-storage
[17179578.256000] USB Mass Storage support registered.
[17179583.244000] usb-storage: device scan complete
[17179583.244000]   Vendor: _NEC      Model: DVD+RW ND-2100AD  Rev: 1.28
[17179583.244000]   Type:   CD-ROM                             ANSI SCSI revision: 00
[17179583.288000] kjournald starting.  Commit interval 5 seconds
[17179583.288000] EXT3-fs: recovery complete.
[17179583.300000] EXT3-fs: mounted filesystem with ordered data mode.
[17179600.984000] input: PC Speaker as /class/input/input1
[17179601.396000] hw_random: RNG not detected
[17179601.468000] parport: PnPBIOS parport detected.
[17179601.468000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[17179602.084000] Linux agpgart interface v0.101 (c) Dave Jones
[17179602.108000] Floppy drive(s): fd0 is 1.44M
[17179602.124000] FDC 0 is a post-1991 82077
[17179602.296000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179602.352000] irda_init()
[17179602.352000] NET: Registered protocol family 23
[17179602.512000] input: PS2++ Logitech Wheel Mouse as /class/input/input2
[17179602.576000] agpgart: Detected an Intel i845 Chipset.
[17179602.592000] agpgart: AGP aperture is 256M @ 0x60000000
[17179602.676000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179602.788000] ACPI: PCI Interrupt Link [C0C1] enabled at IRQ 11
[17179602.788000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [C0C1] -> GSI 11 (level, low) -> IRQ 11
[17179602.788000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179603.016000] ts: Compaq touchscreen protocol output
[17179603.104000] intel8x0_measure_ac97_clock: measured 54723 usecs
[17179603.104000] intel8x0: clocking to 48000
[17179603.220000] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9b48b1, caps: 0x884793/0x0
[17179603.220000] serio: Synaptics pass-through port at isa0060/serio4/input0
[17179603.252000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179603.252000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179603.256000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [C0C4] -> GSI 10 (level, low) -> IRQ 10
[17179603.360000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[17179603.364000] found SMC SuperIO Chip (devid=0x0e rev=01 base=0x002e): LPC47N252
[17179603.364000] smsc_ircc_present: can't get sir_base of 0x3e8
[17179603.396000] e100: eth0: e100_probe: addr 0x40100000, irq 10, MAC addr 00:08:02:94:7A:8E
[17179603.500000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [C0C3] -> GSI 11 (level, low) -> IRQ 11
[17179603.500000] Yenta: CardBus bridge found at 0000:02:06.0 [0e11:00b7]
[17179603.500000] Yenta: Enabling burst memory read transactions
[17179603.500000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179603.500000] Yenta: Routing CardBus interrupts to PCI
[17179603.500000] Yenta TI: socket 0000:02:06.0, mfunc 0x01001002, devctl 0x64
[17179603.764000] Yenta: ISA IRQ mask 0x0038, PCI irq 11
[17179603.764000] Socket status: 30000010
[17179603.764000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[17179603.764000] cs: IO port probe 0x2000-0x2fff: clean.
[17179603.764000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x403fffff
[17179603.764000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[17179603.764000] ACPI: PCI Interrupt 0000:02:06.1[A] -> Link [C0C3] -> GSI 11 (level, low) -> IRQ 11
[17179603.764000] Yenta: CardBus bridge found at 0000:02:06.1 [0e11:00b7]
[17179603.764000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179603.764000] Yenta: Routing CardBus interrupts to PCI
[17179603.764000] Yenta TI: socket 0000:02:06.1, mfunc 0x01001002, devctl 0x64
[17179603.996000] Yenta: ISA IRQ mask 0x0038, PCI irq 11
[17179603.996000] Socket status: 30000010
[17179603.996000] Yenta: Raising subordinate bus# of parent bus (#02) from #04 to #07
[17179603.996000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[17179603.996000] cs: IO port probe 0x2000-0x2fff: clean.
[17179603.996000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x403fffff
[17179603.996000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[17179604.004000] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179604.128000] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[17179604.132000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[17179604.148000] orinoco_usb: Unknown symbol __orinoco_ev_rx
[17179604.148000] orinoco_usb: Unknown symbol __orinoco_ev_info
[17179604.148000] orinoco_usb: disagrees about version of symbol alloc_orinocodev
[17179604.148000] orinoco_usb: Unknown symbol alloc_orinocodev
[17179604.200000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[17179604.400000] pccard: PCMCIA card inserted into slot 0
[17179604.400000] cs: memory probe 0x50000000-0x53ffffff: excluding 0x50000000-0x53ffffff
[17179604.400000] cs: memory probe 0x40000000-0x403fffff: excluding 0x40000000-0x4003ffff 0x40080000-0x400bffff 0x40100000-0x4013ffff 0x40180000-0x401bffff 0x40200000-0x4023ffff 0x40280000-0x402bffff 0x40300000-0x4033ffff
[17179604.404000] pcmcia: registering new device pcmcia0.0
[17179604.636000] pccard: PCMCIA card inserted into slot 1
[17179604.664000] cs: memory probe 0x50000000-0x53ffffff: excluding 0x50000000-0x53ffffff
[17179604.664000] cs: memory probe 0x40000000-0x403fffff: excluding 0x40000000-0x400bffff 0x40100000-0x4013ffff 0x40180000-0x401bffff 0x40200000-0x4023ffff 0x40280000-0x402bffff 0x40300000-0x4033ffff
[17179604.668000] pcmcia: registering new device pcmcia1.0
[17179604.700000] cs: IO port probe 0x100-0x3af: excluding 0x100-0x107
[17179604.700000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179604.700000] cs: IO port probe 0x820-0x8ff: clean.
[17179604.700000] cs: IO port probe 0xc00-0xcf7: clean.
[17179604.700000] cs: IO port probe 0xa00-0xaff: clean.
[17179604.724000] orinoco_cs 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179604.768000] cs: IO port probe 0x100-0x3af: excluding 0x100-0x107
[17179604.768000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179604.768000] cs: IO port probe 0x820-0x8ff: clean.
[17179604.768000] cs: IO port probe 0xc00-0xcf7: clean.
[17179604.768000] cs: IO port probe 0xa00-0xaff: clean.
[17179604.812000] eth1: Hardware identity 0001:0001:0004:0000
[17179604.812000] eth1: Station identity  001f:0001:0006:0010
[17179604.812000] eth1: Firmware determined as Lucent/Agere 6.16
[17179604.812000] eth1: Ad-hoc demo mode supported
[17179604.812000] eth1: IEEE standard IBSS ad-hoc mode supported
[17179604.812000] eth1: WEP supported, 104-bit key
[17179604.812000] eth1: MAC address 00:60:1D:F1:71:A2
[17179604.812000] eth1: Station name "HERMES I"
[17179604.812000] eth1: ready
[17179604.812000] eth1: index 0x01: , irq 3, io 0x2100-0x213f
[17179604.992000] eth1: New link status: Connected (0001)
[17179605.128000] NET: Registered protocol family 17
[17179606.600000] NET: Registered protocol family 10
[17179606.600000] lo: Disabled Privacy Extensions
[17179606.600000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179606.600000] IPv6 over IPv4 tunneling driver
[17179607.484000] lp0: using parport0 (interrupt-driven).
[17179607.548000] fuse init (API version 7.8)
[17179607.548000] fuse distribution version: 2.6.3
[17179607.584000] found SMC SuperIO Chip (devid=0x0e rev=01 base=0x002e): LPC47N252
[17179607.584000] smsc_ircc_present: can't get sir_base of 0x3e8
[17179607.660000] IrCOMM protocol (Dag Brattli)
[17179607.776000] Adding 1116508k swap on /dev/disk/by-uuid/2747d182-d6fa-4ed1-94e9-81639b1bc508.  Priority:-1 extents:1 across:1116508k
[17179607.892000] EXT3 FS on hda3, internal journal
[17179608.768000] kjournald starting.  Commit interval 5 seconds
[17179608.776000] EXT3 FS on hda2, internal journal
[17179608.776000] EXT3-fs: mounted filesystem with ordered data mode.
[17179610.304000] IBM TrackPoint firmware: 0x0b, buttons: 2/3
[17179610.644000] input: TPPS/2 IBM TrackPoint as /class/input/input4
[17179612.956000] pnp: Device 00:04 disabled.
[17179612.964000] pnp: Device 00:04 activated.
[17179612.984000] found SMC SuperIO Chip (devid=0x0e rev=01 base=0x002e): LPC47N252
[17179612.984000] SMsC IrDA Controller found
[17179612.984000]  IrCC version 2.0, firport 0x100, sirport 0x3e8 dma=1, irq=3
[17179612.984000] smsc_ircc_set_sir_speed(), Setting speed to: 9600
[17179612.984000] No transceiver found. Defaulting to Fast pin select
[17179612.992000] IrDA: Registered device irda0
[17179614.364000] wmi_add device=dff50800
[17179614.364000] calling WQBA
[17179614.532000] ACPI: Battery Slot [C198] (battery present)
[17179614.532000] ACPI: Battery Slot [C199] (battery absent)
[17179614.572000] ACPI: Video Device [C0CE] (multi-head: yes  rom: no  post: no)
[17179614.592000] pcc_acpi: loading...
[17179614.808000] ACPI: Power Button (FF) [PWRF]
[17179614.808000] ACPI: Sleep Button (CM) [C19B]
[17179614.808000] ACPI: Lid Switch [C19C]
[17179614.824000] ACPI: AC Adapter [C19A] (on-line)
[17179614.848000] ibm_acpi: ec object not found
[17179617.020000] [drm] Initialized drm 1.0.1 20051102
[17179617.040000] eth1: no IPv6 routers present
[17179617.044000] ACPI: PCI Interrupt Link [C0C0] enabled at IRQ 11
[17179617.044000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [C0C0] -> GSI 11 (level, low) -> IRQ 11
[17179617.048000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179618.268000] mtrr: 0x48000000,0x8000000 overlaps existing 0x48000000,0x2000000
[17179618.268000] mtrr: 0x48000000,0x8000000 overlaps existing 0x48000000,0x2000000
[17179618.268000] mtrr: 0x48000000,0x8000000 overlaps existing 0x48000000,0x2000000
[17179618.268000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179618.268000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[17179618.268000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[17179618.524000] [drm] Setting GART location based on new memory map
[17179618.524000] [drm] writeback test succeeded in 1 usecs
[17179623.620000] setup_irq: irq handler mismatch
[17179623.620000]  <c01497d7> setup_irq+0x127/0x140  <f8b422c0> smsc_ircc_interrupt+0x0/0x830 [smsc_ircc2]
[17179623.620000]  <c0149889> request_irq+0x99/0xb0  <f8b41bef> smsc_ircc_net_open+0x4f/0x1c0 [smsc_ircc2]
[17179623.620000]  <c02724d1> dev_open+0x31/0x70  <c0270ebc> dev_change_flags+0xfc/0x130
[17179623.620000]  <c0266900> sock_ioctl+0x0/0x220  <c0272773> dev_ioctl+0x263/0x380
[17179623.620000]  <c0158f41> __handle_mm_fault+0x211/0x900  <c0266a14> sock_ioctl+0x114/0x220
[17179623.620000]  <c0266900> sock_ioctl+0x0/0x220  <c017d52b> do_ioctl+0x2b/0x90
[17179623.620000]  <c017d5ec> vfs_ioctl+0x5c/0x2b0  <c017d8b2> sys_ioctl+0x72/0x90
[17179623.620000]  <c0102fbb> sysenter_past_esp+0x54/0x79 
[17179623.620000] smsc_ircc_net_open(), unable to allocate irq=3
[17179625.092000] QEMU Accelerator Module version 1.3.0, Copyright (c) 2005-2007 Fabrice Bellard
[17179625.096000] KQEMU installed, max_locked_mem=517768kB.
[17179625.176000] tun: Universal TUN/TAP device driver, 1.6
[17179625.176000] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[17179629.604000] vmmon: module license 'unspecified' taints kernel.
[17179629.612000] /dev/vmmon[4820]: Module vmmon: registered with major=10 minor=165
[17179629.612000] /dev/vmmon[4820]: Module vmmon: initialized
[17179630.628000] /dev/vmnet: open called by PID 4846 (vmnet-bridge)
[17179630.628000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17179630.632000] /dev/vmnet: port on hub 0 successfully opened
[17179630.632000] bridge-eth1: enabling the bridge
[17179630.632000] bridge-eth1: is a Wireless Adapter
[17179630.632000] bridge-eth1: up
[17179630.632000] bridge-eth1: already up
[17179630.632000] bridge-eth1: attached
[17179630.836000] /dev/vmnet: open called by PID 4860 (vmnet-natd)
[17179630.836000] /dev/vmnet: hub 8 does not exist, allocating memory.
[17179630.836000] /dev/vmnet: port on hub 8 successfully opened
[17179640.824000] /dev/vmnet: open called by PID 5004 (vmnet-netifup)
[17179640.824000] /dev/vmnet: hub 1 does not exist, allocating memory.
[17179640.824000] /dev/vmnet: port on hub 1 successfully opened
[17179640.828000] /dev/vmnet: open called by PID 5005 (vmnet-netifup)
[17179640.828000] /dev/vmnet: port on hub 8 successfully opened
[17179642.512000] /dev/vmnet: open called by PID 5031 (vmnet-dhcpd)
[17179642.512000] /dev/vmnet: port on hub 8 successfully opened
[17179642.804000] /dev/vmnet: open called by PID 5026 (vmnet-dhcpd)
[17179642.804000] /dev/vmnet: port on hub 1 successfully opened
[17179651.824000] vmnet8: no IPv6 routers present
[17179651.844000] vmnet1: no IPv6 routers present

```

It doesn't look like my device was claimed. 

if I sudo irattach irda0 -s 
suso irdadump 

I don't see any devices out there (they are turned on)

I've tried attaching to /dev/ttyS0 thru ttyS3 and irdadump doesn't find anything.

Any help is greatly appreciated.

---

### Post by grahams on 2007-05-27
bump

---

### Post by grahams on 2007-06-12
bump

---

### Post by grahams on 2007-06-12
bump

---

### Post by Offoffoff on 2007-06-30
I have the same problem.... I would like to use IrDA, but I cannot. How to understand, is it works or not? I have Compaq Evo n400c...

---

### Post by dotweb on 2007-07-02
Hi I have the same problem with a Compaq Evo N620C, and the only problem left for me to solve after converting from Windows to Linux.

---

### Post by Offoffoff on 2007-08-09
I change my laptop and I use now HP Compaq nc4000 - again I can't install irda...

---

