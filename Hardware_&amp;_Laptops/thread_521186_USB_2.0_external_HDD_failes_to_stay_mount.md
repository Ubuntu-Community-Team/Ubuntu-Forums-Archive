---
title: "USB 2.0 external HDD failes to stay mount"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by pPrdrm on 2007-08-09
First, i want to say hi to all since this is my first post!
I've tried to search the forum for an answer to my problem but i couldn't find anything, so here it is. I have an external USB 2.0 hard drive and Feisty recognize it the minute i plug it in. The problem is that it fails to stay mounted. It just keeps mounts and umounts endlessly. The olny solution i've found that seems to work is to remove the ehci_hcd module. But doing that my USB 2.0 drive works with USB 1.1 interface which is way to slooooow. Any ideas would be appreciated.

P.S. I don't speak English very well.

---

### Post by pPrdrm on 2007-08-09
:?:

---

### Post by pPrdrm on 2007-08-09
Well, i guess no one seems to have a clew :-( .

---

### Post by pPrdrm on 2007-08-24
I am trying to download Ubuntu's repositories for off line use following this tread: [[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=352460&highlight=make+offlie+dvds[/COLOR]]("http://ubuntuforums.org/showthread.php?t=352460&highlight=make+offlie+dvds")
But the problem I am having with my external USB drive stops me from doing it. It just doesn't want to stay mounted. I don't know what to do. I've installed all the updates, including those from backports with no luck. And I have searched the forum but no one seems to have a similar problem. If it's a bug, does anyone knows about it or is it just a hardware compatibility issue?

---

### Post by jsf9k on 2007-08-24
I may be having a similar problem with a USB to IDE adapter.  My hard drive suddenly unmounts itself uncleanly and the drive is corrupted.  I also get an oops from the kernel.  Here is the dmesg output:
```
[17179569.184000] Linux version 2.6.17-12-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Mon Jul 16 19:37:58 UTC 2007 (Ubuntu 2.6.17-12.39-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001ffea800 (usable)
[17179569.184000]  BIOS-e820: 000000001ffea800 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000feea0000 - 00000000fef00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 131050
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126954 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fde50
[17179569.184000] ACPI: RSDT (v001 DELL    CPi R   0x27d10b1a ASL  0x00000061) @ 0x000fde64
[17179569.184000] ACPI: FADT (v001 DELL    CPi R   0x27d10b1a ASL  0x00000061) @ 0x000fde90
[17179569.184000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:deea0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda4 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0140b000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 996.787 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.448000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.452000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.480000] Memory: 510048k/524200k available (1911k kernel code, 13616k reserved, 1073k data, 308k init, 0k highmem)
[17179569.480000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.560000] Calibrating delay using timer specific routine.. 1995.39 BogoMIPS (lpj=3990797)
[17179569.560000] Security Framework v1.0.0 initialized
[17179569.560000] SELinux:  Disabled at boot.
[17179569.560000] Mount-cache hash table entries: 512
[17179569.560000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.560000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.560000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179569.560000] CPU: L2 cache: 512K
[17179569.560000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179569.560000] Checking 'hlt' instruction... OK.
[17179569.576000] SMP alternatives: switching to UP code
[17179569.576000] Freeing SMP alternatives: 16k freed
[17179569.576000] checking if image is initramfs... it is
[17179570.504000] Freeing initrd memory: 5326k freed
[17179570.504000] ACPI: Core revision 20060707
[17179570.512000] ACPI: Looking for DSDT ... not found!
[17179570.540000] ACPI: setting ELCR to 0200 (from 0c20)
[17179570.540000] CPU0: Intel(R) Pentium(R) III Mobile CPU      1000MHz stepping 01
[17179570.540000] SMP motherboard not detected.
[17179570.540000] Local APIC not detected. Using dummy APIC emulation.
[17179570.540000] Brought up 1 CPUs
[17179570.540000] migration_cost=0
[17179570.540000] NET: Registered protocol family 16
[17179570.540000] EISA bus registered
[17179570.540000] ACPI: bus type pci registered
[17179570.552000] PCI: PCI BIOS revision 2.10 entry at 0xfc06e, last bus=8
[17179570.552000] PCI: Using configuration type 1
[17179570.552000] Setting up standard PCI resources
[17179570.604000] ACPI: Interpreter enabled
[17179570.604000] ACPI: Using PIC for interrupt routing
[17179570.608000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.608000] PCI: Probing PCI hardware (bus 00)
[17179570.612000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.680000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[17179570.680000] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[17179570.680000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.680000] Boot video device is 0000:01:00.0
[17179570.680000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.680000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.800000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179570.800000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[17179570.800000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179570.800000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179570.804000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179570.804000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[17179570.804000] ACPI: Power Resource [PADA] (on)
[17179570.804000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.804000] pnp: PnP ACPI init
[17179571.008000] pnp: PnP ACPI: found 15 devices
[17179571.008000] PnPBIOS: Disabled by ACPI PNP
[17179571.008000] PCI: Using ACPI for IRQ routing
[17179571.008000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.052000] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[17179571.052000] pnp: 00:02: ioport range 0x800-0x805 could not be reserved
[17179571.052000] pnp: 00:02: ioport range 0x808-0x80f could not be reserved
[17179571.052000] pnp: 00:03: ioport range 0x806-0x807 has been reserved
[17179571.052000] pnp: 00:03: ioport range 0x810-0x85f could not be reserved
[17179571.052000] pnp: 00:03: ioport range 0x860-0x87f has been reserved
[17179571.052000] pnp: 00:03: ioport range 0x880-0x8bf has been reserved
[17179571.052000] pnp: 00:03: ioport range 0x8c0-0x8ff has been reserved
[17179571.052000] pnp: 00:03: ioport range 0x600-0x67f has been reserved
[17179571.052000] pnp: 00:03: ioport range 0x680-0x6ff has been reserved
[17179571.052000] pnp: 00:04: ioport range 0xf000-0xf0fe has been reserved
[17179571.052000] pnp: 00:04: ioport range 0xf100-0xf1fe has been reserved
[17179571.052000] pnp: 00:04: ioport range 0xf200-0xf2fe has been reserved
[17179571.052000] pnp: 00:04: ioport range 0xf400-0xf4fe has been reserved
[17179571.052000] pnp: 00:04: ioport range 0xf500-0xf5fe has been reserved
[17179571.052000] pnp: 00:04: ioport range 0xf600-0xf6fe has been reserved
[17179571.052000] pnp: 00:04: ioport range 0xf800-0xf8fe has been reserved
[17179571.052000] pnp: 00:04: ioport range 0xf900-0xf9fe has been reserved
[17179571.052000] pnp: 00:09: ioport range 0x900-0x91f has been reserved
[17179571.052000] pnp: 00:09: ioport range 0x3f0-0x3f1 has been reserved
[17179571.052000] PCI: Bridge: 0000:00:01.0
[17179571.052000]   IO window: c000-cfff
[17179571.052000]   MEM window: fc000000-fdffffff
[17179571.052000]   PREFETCH window: e0000000-e7ffffff
[17179571.052000] PCI: Bridge: 0000:02:06.0
[17179571.052000]   IO window: e000-efff
[17179571.052000]   MEM window: f8000000-f9ffffff
[17179571.052000]   PREFETCH window: disabled.
[17179571.052000] PCI: Bus 9, cardbus bridge: 0000:02:0f.0
[17179571.052000]   IO window: 0000d000-0000d0ff
[17179571.052000]   IO window: 0000d400-0000d4ff
[17179571.052000]   PREFETCH window: 30000000-31ffffff
[17179571.052000]   MEM window: f2000000-f3ffffff
[17179571.052000] PCI: Bus 13, cardbus bridge: 0000:02:0f.1
[17179571.052000]   IO window: 0000d800-0000d8ff
[17179571.052000]   IO window: 00001000-000010ff
[17179571.052000]   PREFETCH window: 32000000-33ffffff
[17179571.052000]   MEM window: f4000000-f5ffffff
[17179571.052000] PCI: Bridge: 0000:00:1e.0
[17179571.052000]   IO window: d000-ffff
[17179571.052000]   MEM window: f2000000-fbffffff
[17179571.052000]   PREFETCH window: 30000000-33ffffff
[17179571.052000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.052000] PCI: Enabling device 0000:02:0f.0 (0000 -> 0003)
[17179571.052000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[17179571.052000] PCI: setting IRQ 10 as level-triggered
[17179571.052000] ACPI: PCI Interrupt 0000:02:0f.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179571.052000] PCI: Enabling device 0000:02:0f.1 (0000 -> 0003)
[17179571.052000] ACPI: PCI Interrupt 0000:02:0f.1[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179571.052000] NET: Registered protocol family 2
[17179571.092000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179571.092000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179571.092000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179571.092000] TCP: Hash tables configured (established 16384 bind 8192)
[17179571.092000] TCP reno registered
[17179571.092000] audit: initializing netlink socket (disabled)
[17179571.092000] audit(1187870988.092:1): initialized
[17179571.092000] VFS: Disk quotas dquot_6.5.1
[17179571.092000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.092000] Initializing Cryptographic API
[17179571.092000] io scheduler noop registered
[17179571.092000] io scheduler anticipatory registered
[17179571.092000] io scheduler deadline registered
[17179571.092000] io scheduler cfq registered (default)
[17179571.092000] isapnp: Scanning for PnP cards...
[17179571.448000] isapnp: No Plug & Play device found
[17179571.496000] Real Time Clock Driver v1.12ac
[17179571.496000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.496000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.496000] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.496000] mice: PS/2 mouse device common for all mice
[17179571.500000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.500000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.500000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.500000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.504000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.504000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.504000] EISA: Probing bus 0 at eisa.0
[17179571.504000] Cannot allocate resource for EISA slot 1
[17179571.504000] EISA: Detected 0 cards.
[17179571.504000] TCP bic registered
[17179571.504000] NET: Registered protocol family 1
[17179571.508000] NET: Registered protocol family 8
[17179571.508000] NET: Registered protocol family 20
[17179571.508000] Using IPI No-Shortcut mode
[17179571.508000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.508000] Freeing unused kernel memory: 308k freed
[17179571.516000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.680000] Capability LSM initialized
[17179572.744000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179572.772000] ACPI: Thermal Zone [THM] (25 C)
[17179573.320000] ICH2M: IDE controller at PCI slot 0000:00:1f.1
[17179573.320000] ICH2M: chipset revision 3
[17179573.320000] ICH2M: not 100% native mode: will probe irqs later
[17179573.320000]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:DMA
[17179573.320000]     ide1: BM-DMA at 0xbfa8-0xbfaf, BIOS settings: hdc:pio, hdd:pio
[17179573.320000] Probing IDE interface ide0...
[17179573.608000] hda: HITACHI_DK23CA-30, ATA DISK drive
[17179574.056000] hdb: LG DVD-ROM DRN-8080B, ATAPI CD/DVD-ROM drive
[17179574.112000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.116000] Probing IDE interface ide1...
[17179574.696000] hda: max request size: 128KiB
[17179574.712000] hda: 58605120 sectors (30005 MB) w/2048KiB Cache, CHS=58140/16/63, UDMA(100)
[17179574.712000] hda: cache flushes not supported
[17179574.712000]  hda: hda1 hda2 hda3 hda4
[17179574.800000] hdb: ATAPI 24X DVD-ROM drive, 512kB Cache, DMA
[17179574.800000] Uniform CD-ROM driver Revision: 3.20
[17179575.164000] Probing IDE interface ide1...
[17179575.312000] usbcore: registered new driver usbfs
[17179575.312000] usbcore: registered new driver hub
[17179575.316000] USB Universal Host Controller Interface driver v3.0
[17179575.316000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179575.316000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179575.316000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[17179575.316000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[17179575.316000] uhci_hcd 0000:00:1f.2: irq 10, io base 0x0000bce0
[17179575.316000] usb usb1: configuration #1 chosen from 1 choice
[17179575.316000] hub 1-0:1.0: USB hub found
[17179575.316000] hub 1-0:1.0: 2 ports detected
[17179575.332000] ieee1394: Initialized config rom entry `ip1394'
[17179575.420000] ACPI: PCI Interrupt 0000:02:0f.2[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179575.468000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[f6ffd800-f6ffdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[17179575.816000] Attempting manual resume
[17179575.884000] kjournald starting.  Commit interval 5 seconds
[17179575.884000] EXT3-fs: mounted filesystem with ordered data mode.
[17179576.744000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[394fc0000e071021]
[17179596.624000] input: PC Speaker as /class/input/input1
[17179597.680000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179597.688000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179598.100000] Linux agpgart interface v0.101 (c) Dave Jones
[17179598.164000] agpgart: Detected an Intel i815 Chipset.
[17179598.168000] agpgart: AGP aperture is 64M @ 0xe8000000
[17179598.216000] parport: PnPBIOS parport detected.
[17179598.216000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179598.288000] Synaptics Touchpad, model: 1, fw: 5.7, id: 0x8146b1, caps: 0x804793/0x0
[17179598.288000] serio: Synaptics pass-through port at isa0060/serio1/input0
[17179598.332000] Floppy drive(s): fd0 is 1.44M
[17179598.336000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179598.348000] FDC 0 is a post-1991 82077
[17179598.368000] hw_random: RNG not detected
[17179598.472000] ts: Compaq touchscreen protocol output
[17179599.776000] ACPI: PCI Interrupt 0000:02:0f.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179599.776000] Yenta: CardBus bridge found at 0000:02:0f.0 [1028:00e6]
[17179599.776000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179599.776000] Yenta: Routing CardBus interrupts to PCI
[17179599.776000] Yenta TI: socket 0000:02:0f.0, mfunc 0x05033002, devctl 0x64
[17179599.872000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179599.872000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179600.008000] Yenta: ISA IRQ mask 0x0838, PCI irq 10
[17179600.008000] Socket status: 30000006
[17179600.008000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xffff
[17179600.008000] cs: IO port probe 0xd000-0xffff: clean.
[17179600.008000] pcmcia: parent PCI bridge Memory window: 0xf2000000 - 0xfbffffff
[17179600.008000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[17179600.008000] ACPI: PCI Interrupt 0000:02:0f.1[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179600.008000] Yenta: CardBus bridge found at 0000:02:0f.1 [1028:00e6]
[17179600.008000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179600.008000] Yenta: Routing CardBus interrupts to PCI
[17179600.008000] Yenta TI: socket 0000:02:0f.1, mfunc 0x05033002, devctl 0x64
[17179600.240000] Yenta: ISA IRQ mask 0x0838, PCI irq 10
[17179600.240000] Socket status: 30000006
[17179600.240000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xffff
[17179600.240000] cs: IO port probe 0xd000-0xffff: clean.
[17179600.240000] pcmcia: parent PCI bridge Memory window: 0xf2000000 - 0xfbffffff
[17179600.240000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[17179600.252000] ACPI: PCI Interrupt 0000:08:04.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179600.296000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[17179600.296000] PCI: setting IRQ 5 as level-triggered
[17179600.296000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179600.296000] maestro3: enabled hack for 'Dell Inspiron 8100'
[17179600.300000] e100: eth0: e100_probe: addr 0xf8fff000, irq 10, MAC addr 00:20:E0:70:99:1B
[17179600.928000] cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x200-0x207 0x370-0x37f
[17179600.932000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179600.932000] cs: IO port probe 0x820-0x8ff: clean.
[17179600.932000] cs: IO port probe 0xc00-0xcf7: clean.
[17179600.932000] cs: IO port probe 0xa00-0xaff: clean.
[17179600.984000] cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x200-0x207 0x370-0x37f
[17179600.984000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179600.988000] cs: IO port probe 0x820-0x8ff: clean.
[17179600.988000] cs: IO port probe 0xc00-0xcf7: clean.
[17179600.988000] cs: IO port probe 0xa00-0xaff: clean.
[17179601.536000] NET: Registered protocol family 17
[17179602.964000] lp0: using parport0 (interrupt-driven).
[17179603.072000] SCSI subsystem initialized
[17179603.092000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179603.092000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179603.144000] Adding 1028152k swap on /dev/disk/by-uuid/494931a7-76e3-42a4-a98c-737f290dcfde.  Priority:-1 extents:1 across:1028152k
[17179603.336000] EXT3 FS on hda4, internal journal
[17179603.756000] IBM TrackPoint firmware: 0x0b, buttons: 2/3
[17179604.036000] input: TPPS/2 IBM TrackPoint as /class/input/input3
[17179604.040000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179604.440000] NTFS volume version 3.1.
[17179611.740000] ACPI: AC Adapter [AC] (on-line)
[17179611.852000] ACPI: Battery Slot [BAT0] (battery absent)
[17179611.980000] ACPI: Battery Slot [BAT1] (battery present)
[17179612.012000] ACPI: Lid Switch [LID]
[17179612.012000] ACPI: Power Button (CM) [PBTN]
[17179612.012000] ACPI: Sleep Button (CM) [SBTN]
[17179612.088000] ACPI: ACPI Dock Station Driver 
[17179612.196000] ibm_acpi: ec object not found
[17179612.248000] pcc_acpi: loading...
[17179612.456000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179612.864000] cpufreq: change failed with new_state 1 and result 0
[17179618.208000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179618.208000] apm: overridden by ACPI.
[17179624.840000] ondemand governor failed to load due to too long transition latency
[17179625.408000] NET: Registered protocol family 10
[17179625.408000] lo: Disabled Privacy Extensions
[17179625.408000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179625.408000] IPv6 over IPv4 tunneling driver
[17179625.832000] Bluetooth: Core ver 2.8
[17179625.832000] NET: Registered protocol family 31
[17179625.832000] Bluetooth: HCI device and connection manager initialized
[17179625.832000] Bluetooth: HCI socket layer initialized
[17179625.884000] Bluetooth: L2CAP ver 2.8
[17179625.884000] Bluetooth: L2CAP socket layer initialized
[17179625.896000] Bluetooth: RFCOMM socket layer initialized
[17179625.896000] Bluetooth: RFCOMM TTY layer initialized
[17179625.896000] Bluetooth: RFCOMM ver 1.7
[17179628.916000] cpufreq: change failed with new_state 1 and result 0
[17179669.924000] cpufreq: change failed with new_state 1 and result 0
[17179690.176000] cpufreq: change failed with new_state 1 and result 0
[17180747.576000] cpufreq: change failed with new_state 1 and result 0
[17180789.268000] cpufreq: change failed with new_state 1 and result 0
[17180971.668000] pccard: PCMCIA card inserted into slot 0
[17180971.668000] cs: memory probe 0xf2000000-0xfbffffff: excluding 0xf2000000-0xf6ffffff 0xf8000000-0xf9ffffff
[17180971.668000] pcmcia: registering new device pcmcia0.0
[17180971.932000] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17180971.940000] orinoco_cs 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17180972.260000] eth1: firmware ALLOC bug detected (old Symbol firmware?). Trying to work around... ok.
[17180972.260000] eth1: Hardware identity 8000:0001:0000:0000
[17180972.260000] eth1: Station identity  001f:0002:0002:0001
[17180972.264000] eth1: Firmware determined as Symbol V2.50-14
[17180972.264000] eth1: Ad-hoc demo mode supported
[17180972.264000] eth1: IEEE standard IBSS ad-hoc mode supported
[17180972.264000] eth1: WEP supported, 104-bit key
[17180972.264000] eth1: MAC address 00:50:DA:03:37:7F
[17180972.264000] eth1: Station name "Prism  I"
[17180972.264000] eth1: ready
[17180972.268000] eth1: index 0x01: , irq 3, io 0xd100-0xd147
[17180972.384000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17180973.080000] eth1: New link status: Connected (0001)
[17180973.080000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17180979.880000] cpufreq: change failed with new_state 1 and result 0
[17180983.336000] eth1: no IPv6 routers present
[17180998.520000] cpufreq: change failed with new_state 1 and result 0
[17181042.020000] cpufreq: change failed with new_state 1 and result 0
[17194962.856000] cpufreq: change failed with new_state 1 and result 0
[17261946.660000] cpufreq: change failed with new_state 1 and result 0
[17261956.848000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[17261957.020000] usb 1-2: configuration #1 chosen from 1 choice
[17261957.300000] usbcore: registered new driver libusual
[17261957.412000] Initializing USB Mass Storage driver...
[17261957.412000] scsi0 : SCSI emulation for USB Mass Storage devices
[17261957.412000] usb-storage: device found at 2
[17261957.412000] usb-storage: waiting for device to settle before scanning
[17261957.412000] usbcore: registered new driver usb-storage
[17261957.412000] USB Mass Storage support registered.
[17261962.412000] usb-storage: device scan complete
[17261962.416000]   Vendor: HTS54808  Model: 0M9AT00           Rev: A53A
[17261962.416000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17261962.572000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17261962.576000] sda: Write Protect is off
[17261962.576000] sda: Mode Sense: 00 38 00 00
[17261962.576000] sda: assuming drive cache: write through
[17261962.580000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17261962.584000] sda: Write Protect is off
[17261962.584000] sda: Mode Sense: 00 38 00 00
[17261962.584000] sda: assuming drive cache: write through
[17261962.588000]  sda: sda1
[17261962.612000] sd 0:0:0:0: Attached scsi disk sda
[17261962.640000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17261964.172000] kjournald starting.  Commit interval 5 seconds
[17261964.196000] EXT3 FS on sda1, internal journal
[17261964.196000] EXT3-fs: mounted filesystem with journal data mode.
[17261967.416000] cpufreq: change failed with new_state 1 and result 0
[17261971.460000] cpufreq: change failed with new_state 1 and result 0
[17261996.236000] cpufreq: change failed with new_state 1 and result 0
[17262023.532000] cpufreq: change failed with new_state 1 and result 0
[17262058.096000] cpufreq: change failed with new_state 1 and result 0
[17262116.848000] cpufreq: change failed with new_state 1 and result 0
[17262155.468000] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
[17262155.468000] cpufreq: change failed with new_state 1 and result 0
[17262187.964000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[17262188.132000] usb 1-1: configuration #1 chosen from 1 choice
[17262188.140000] scsi1 : SCSI emulation for USB Mass Storage devices
[17262188.140000] usb-storage: device found at 3
[17262188.140000] usb-storage: waiting for device to settle before scanning
[17262188.452000] usbcore: registered new driver hiddev
[17262188.464000] input: Western Digital External HDD as /class/input/input4
[17262188.464000] input: USB HID v1.11 Device [Western Digital External HDD] on usb-0000:00:1f.2-1
[17262188.464000] usbcore: registered new driver usbhid
[17262188.464000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17262193.140000] usb-storage: device scan complete
[17262193.144000]   Vendor: WD        Model: 5000AAKS Externa  Rev: 107a
[17262193.144000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[17262193.148000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
[17262193.152000] sdb: Write Protect is off
[17262193.152000] sdb: Mode Sense: 11 00 00 00
[17262193.152000] sdb: assuming drive cache: write through
[17262193.156000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
[17262193.160000] sdb: Write Protect is off
[17262193.160000] sdb: Mode Sense: 11 00 00 00
[17262193.160000] sdb: assuming drive cache: write through
[17262193.160000]  sdb: sdb1
[17262193.172000] sd 1:0:0:0: Attached scsi disk sdb
[17262193.176000] sd 1:0:0:0: Attached scsi generic sg1 type 0
[17262194.168000] hfs: write access to a jounaled filesystem is not supported, use the force option at your own risk, mounting read-only.
[17262198.672000] cpufreq: change failed with new_state 1 and result 0
[17262640.936000] usb 1-1: USB disconnect, address 3
[17262729.572000] usb 1-2: reset full speed USB device using uhci_hcd and address 2
[17262729.892000] hub 1-0:1.0: over-current change on port 2
[17262759.832000] usb 1-2: reset full speed USB device using uhci_hcd and address 2
[17262770.092000] usb 1-2: reset full speed USB device using uhci_hcd and address 2
[17262772.796000] cpufreq: change failed with new_state 1 and result 0
[17262776.576000] hub 1-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[17262776.576000] hub 1-0:1.0: over-current change on port 2
[17262776.680000] usb 1-2: USB disconnect, address 2
[17262776.680000] sd 0:0:0:0: rejecting I/O to device being removed
[17262776.680000] Buffer I/O error on device sda1, logical block 10584066
[17262776.680000] lost page write due to I/O error on sda1
[17262776.680000] sd 0:0:0:0: rejecting I/O to device being removed
[17262776.680000] Buffer I/O error on device sda1, logical block 8
[17262776.680000] lost page write due to I/O error on sda1
[17262776.800000] usb 1-2: new full speed USB device using uhci_hcd and address 4
[17262776.920000]  0:0:0:0: rejecting I/O to dead device
[17262776.920000] Buffer I/O error on device sda1, logical block 525
[17262776.920000] lost page write due to I/O error on sda1
[17262776.920000]  0:0:0:0: rejecting I/O to dead device
[17262776.920000] Buffer I/O error on device sda1, logical block 525
[17262776.920000] lost page write due to I/O error on sda1
[17262776.920000]  0:0:0:0: rejecting I/O to dead device
[17262776.920000] Buffer I/O error on device sda1, logical block 525
[17262776.920000] lost page write due to I/O error on sda1
[17262776.924000]  0:0:0:0: rejecting I/O to dead device
[17262776.924000] Buffer I/O error on device sda1, logical block 0
[17262776.924000] lost page write due to I/O error on sda1
[17262776.972000] usb 1-2: configuration #1 chosen from 1 choice
[17262776.980000] scsi2 : SCSI emulation for USB Mass Storage devices
[17262776.980000] usb-storage: device found at 4
[17262776.980000] usb-storage: waiting for device to settle before scanning
[17262781.980000] usb-storage: device scan complete
[17262781.984000]   Vendor: HTS54808  Model: 0M9AT00           Rev: A53A
[17262781.984000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17262781.988000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17262781.992000] sda: Write Protect is off
[17262781.992000] sda: Mode Sense: 00 38 00 00
[17262781.992000] sda: assuming drive cache: write through
[17262781.996000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17262782.000000] sda: Write Protect is off
[17262782.000000] sda: Mode Sense: 00 38 00 00
[17262782.000000] sda: assuming drive cache: write through
[17262782.000000]  sda: sda1
[17262782.028000] sd 2:0:0:0: Attached scsi disk sda
[17262782.028000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17262783.092000] kjournald starting.  Commit interval 5 seconds
[17262783.100000] EXT3 FS on sda1, internal journal
[17262783.100000] EXT3-fs: recovery complete.
[17262783.104000] EXT3-fs: mounted filesystem with journal data mode.
[17262783.632000] hub 1-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[17262783.632000] hub 1-0:1.0: over-current change on port 2
[17262783.736000] usb 1-2: USB disconnect, address 4
[17262783.736000] sd 2:0:0:0: rejecting I/O to device being removed
[17262783.736000] Buffer I/O error on device sda1, logical block 525
[17262783.736000] lost page write due to I/O error on sda1
[17262783.736000] sd 2:0:0:0: rejecting I/O to device being removed
[17262783.736000] sd 2:0:0:0: rejecting I/O to device being removed
[17262783.736000] Buffer I/O error on device sda1, logical block 528
[17262783.736000] lost page write due to I/O error on sda1
[17262783.736000] Aborting journal on device sda1.
[17262783.736000] journal commit I/O error
[17262783.736000] sd 2:0:0:0: rejecting I/O to device being removed
[17262783.736000] Buffer I/O error on device sda1, logical block 8
[17262783.736000] lost page write due to I/O error on sda1
[17262783.856000] usb 1-2: new full speed USB device using uhci_hcd and address 5
[17262784.028000] usb 1-2: configuration #1 chosen from 1 choice
[17262784.036000] scsi3 : SCSI emulation for USB Mass Storage devices
[17262784.036000] usb-storage: device found at 5
[17262784.036000] usb-storage: waiting for device to settle before scanning
[17262784.296000]  2:0:0:0: rejecting I/O to dead device
[17262784.296000] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[17262784.308000]  2:0:0:0: rejecting I/O to dead device
[17262784.660000]  2:0:0:0: rejecting I/O to dead device
[17262784.660000] ext3_abort called.
[17262784.660000] EXT3-fs error (device sda1): ext3_journal_start_sb: Detected aborted journal
[17262784.660000] Remounting filesystem read-only
[17262785.256000]  2:0:0:0: rejecting I/O to dead device
[17262787.296000] cpufreq: change failed with new_state 1 and result 0
[17262789.036000] usb-storage: device scan complete
[17262789.040000]   Vendor: HTS54808  Model: 0M9AT00           Rev: A53A
[17262789.040000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17262789.044000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17262789.048000] sda: Write Protect is off
[17262789.048000] sda: Mode Sense: 00 38 00 00
[17262789.048000] sda: assuming drive cache: write through
[17262789.052000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17262789.056000] sda: Write Protect is off
[17262789.056000] sda: Mode Sense: 00 38 00 00
[17262789.056000] sda: assuming drive cache: write through
[17262789.056000]  sda: sda1
[17262789.084000] sd 3:0:0:0: Attached scsi disk sda
[17262789.084000] sd 3:0:0:0: Attached scsi generic sg0 type 0
[17262790.072000] kjournald starting.  Commit interval 5 seconds
[17262790.088000] EXT3 FS on sda1, internal journal
[17262790.088000] EXT3-fs: recovery complete.
[17262790.088000] EXT3-fs: mounted filesystem with journal data mode.
[17262790.572000] hub 1-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[17262790.572000] printk: 2 messages suppressed.
[17262790.572000] hub 1-0:1.0: over-current change on port 2
[17262790.676000] usb 1-2: USB disconnect, address 5
[17262790.700000] usb 1-2: reset full speed USB device using uhci_hcd and address 5
[17262790.812000] usb 1-2: device descriptor read/64, error -19
[17262791.028000] usb 1-2: device descriptor read/64, error -19
[17262791.244000] usb 1-2: reset full speed USB device using uhci_hcd and address 5
[17262791.356000] usb 1-2: device descriptor read/64, error -19
[17262791.572000] usb 1-2: device descriptor read/64, error -19
[17262791.788000] usb 1-2: reset full speed USB device using uhci_hcd and address 5
[17262792.196000] usb 1-2: device not accepting address 5, error -22
[17262792.308000] usb 1-2: reset full speed USB device using uhci_hcd and address 5
[17262792.716000] usb 1-2: device not accepting address 5, error -22
[17262792.716000] sd 3:0:0:0: rejecting I/O to device being removed
[17262792.716000] Buffer I/O error on device sda1, logical block 525
[17262792.716000] lost page write due to I/O error on sda1
[17262792.716000] sd 3:0:0:0: rejecting I/O to device being removed
[17262792.716000] sd 3:0:0:0: rejecting I/O to device being removed
[17262792.716000] Aborting journal on device sda1.
[17262792.716000] journal commit I/O error
[17262792.716000] sd 3:0:0:0: rejecting I/O to device being removed
[17262792.720000] sd 3:0:0:0: SCSI error: return code = 0x10000
[17262792.720000] end_request: I/O error, dev sda, sector 2359423
[17262792.744000] EXT3-fs error (device sda1): ext3_get_inode_loc: unable to read inode block - inode=147457, block=294920
[17262792.744000]  3:0:0:0: rejecting I/O to dead device
[17262792.836000] usb 1-2: new full speed USB device using uhci_hcd and address 6
[17262793.008000] usb 1-2: configuration #1 chosen from 1 choice
[17262793.016000] scsi4 : SCSI emulation for USB Mass Storage devices
[17262793.016000] usb-storage: device found at 6
[17262793.016000] usb-storage: waiting for device to settle before scanning
[17262793.048000]  3:0:0:0: rejecting I/O to dead device
[17262793.048000] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[17262793.060000]  3:0:0:0: rejecting I/O to dead device
[17262793.260000]  3:0:0:0: rejecting I/O to dead device
[17262793.260000] ext3_abort called.
[17262793.260000] EXT3-fs error (device sda1): ext3_journal_start_sb: Detected aborted journal
[17262793.260000] Remounting filesystem read-only
[17262795.112000]  3:0:0:0: rejecting I/O to dead device
[17262798.964000] cpufreq: change failed with new_state 1 and result 0
[17262798.964000] usb-storage: device scan complete
[17262798.968000]   Vendor: HTS54808  Model: 0M9AT00           Rev: A53A
[17262798.968000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17262798.976000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17262798.980000] sda: Write Protect is off
[17262798.980000] sda: Mode Sense: 00 38 00 00
[17262798.980000] sda: assuming drive cache: write through
[17262798.984000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17262798.988000] sda: Write Protect is off
[17262798.988000] sda: Mode Sense: 00 38 00 00
[17262798.988000] sda: assuming drive cache: write through
[17262798.988000]  sda:<6>usb 1-2: reset full speed USB device using uhci_hcd and address 6
[17262799.720000] printk: 5 messages suppressed.
[17262799.720000] hub 1-0:1.0: over-current change on port 2
[17262829.344000] usb 1-2: USB disconnect, address 6
[17262829.344000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
[17262829.344000]  printing eip:
[17262829.344000] c0246ae7
[17262829.344000] *pde = 00000000
[17262829.344000] Oops: 0000 [#1]
[17262829.344000] SMP 
[17262829.344000] Modules linked in: hfsplus usbhid sg sd_mod usb_storage libusual orinoco_cs orinoco hermes binfmt_misc rfcomm l2cap bluetooth ipv6 speedstep_smi speedstep_lib cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sbs sony_acpi pcc_acpi i2c_ec hotkey dock dev_acpi button battery container ac asus_acpi nls_utf8 ntfs nls_iso8859_1 nls_cp437 vfat fat sbp2 scsi_mod lp af_packet pcmcia snd_maestro3 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd_page_alloc snd soundcore e100 mii yenta_socket rsrc_nonstatic pcmcia_core joydev i2c_core evdev tsdev serio_raw floppy parport_pc parport intel_agp agpgart shpchp pci_hotplug psmouse pcspkr ext3 jbd ohci1394 ieee1394 uhci_hcd usbcore ide_generic ide_cd cdrom ide_disk piix generic thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
[17262829.344000] CPU:    0
[17262829.344000] EIP:    0060:[<c0246ae7>]    Not tainted VLI
[17262829.344000] EFLAGS: 00010202   (2.6.17-12-generic #2) 
[17262829.344000] EIP is at make_class_name+0x37/0xb0
[17262829.344000] eax: 00000000   ebx: ffffffff   ecx: ffffffff   edx: 0000000b
[17262829.344000] esi: dc2ea5d4   edi: 00000000   ebp: 00000000   esp: dee95e54
[17262829.344000] ds: 007b   es: 007b   ss: 0068
[17262829.344000] Process khubd (pid: 1705, threadinfo=dee94000 task=dfe2a580)
[17262829.344000] Stack: dc2ea5d4 e0b2e858 dc2ea5d4 e0b2e858 dc2ea5dc c0246d8e e0b2e7e0 00000000 
[17262829.344000]        00000000 dc2ea5d4 d8068800 00000246 cfeafe14 c0246e68 dc2ea400 e0b15ca0 
[17262829.344000]        dc2ea400 d8068800 e0b133fb d8068830 d8068800 e0b0da55 d8068ac0 e0cfeca0 
[17262829.344000] Call Trace:
[17262829.344000]  <c0246d8e> class_device_del+0x9e/0x170  <c0246e68> class_device_unregister+0x8/0x10
[17262829.344000]  <e0b15ca0> __scsi_remove_device+0x30/0x80 [scsi_mod]  <e0b133fb> scsi_forget_host+0x4b/0x60 [scsi_mod]
[17262829.344000]  <e0b0da55> scsi_remove_host+0x55/0xe4 [scsi_mod]  <e0cefd8e> storage_disconnect+0xe/0x20 [usb_storage]
[17262829.344000]  <e08ab994> usb_unbind_interface+0x34/0x70 [usbcore]  <c024600b> __device_release_driver+0x5b/0xa0
[17262829.344000]  <c02462cc> device_release_driver+0x1c/0x30  <c0245837> bus_remove_device+0x77/0x90
[17262829.344000]  <c02448a5> device_del+0x35/0x70  <e08a9bc6> usb_disable_device+0x86/0xe0 [usbcore]
[17262829.344000]  <e08a5927> usb_disconnect+0x97/0xf0 [usbcore]  <e08a698a> hub_thread+0x27a/0xc80 [usbcore]
[17262829.344000]  <c0136180> autoremove_wake_function+0x0/0x50  <e08a6710> hub_thread+0x0/0xc80 [usbcore]
[17262829.344000]  <c0135f8b> kthread+0xab/0xe0  <c0135ee0> kthread+0x0/0xe0
[17262829.344000]  <c0101005> kernel_thread_helper+0x5/0x10 
[17262829.344000] Code: 89 6c 24 10 31 ed 89 d9 89 74 24 08 89 7c 24 0c 89 04 24 8b 40 48 8b 38 89 e8 f2 ae f7 d1 49 8b 04 24 89 ca 89 d9 8b 78 08 89 e8 <f2> ae f7 d1 49 8d 44 0a 02 ba d0 00 00 00 e8 86 04 f2 ff ba f4 
[17262829.344000] EIP: [<c0246ae7>] make_class_name+0x37/0xb0 SS:ESP 0068:dee95e54
[17262829.344000]  <6>sd 4:0:0:0: SCSI error: return code = 0x10000
[17262829.348000] end_request: I/O error, dev sda, sector 0
[17262829.348000] Buffer I/O error on device sda, logical block 0
[17262829.348000] sd 4:0:0:0: rejecting I/O to device being removed
[17262829.348000] Buffer I/O error on device sda, logical block 0
[17262829.348000]  unable to read partition table
[17262829.348000] sd 4:0:0:0: Attached scsi disk sda
[17262829.348000] sd 4:0:0:0: Attached scsi generic sg0 type 0
[17264058.924000] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
[17264058.924000] cpufreq: change failed with new_state 1 and result 0
[17264096.704000] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
[17264096.704000] cpufreq: change failed with new_state 1 and result 0
[17265354.336000] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 4 bytes away.
[17265354.336000] cpufreq: change failed with new_state 1 and result 0
[17265357.556000] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[17265357.556000] cpufreq: change failed with new_state 1 and result 0
[17265361.456000] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[17265361.456000] cpufreq: change failed with new_state 1 and result 0

```

---

### Post by ev5unleash1 on 2007-08-24
I just got a Laptop Harddrive case for USB to IDE. And it work perfectly with Ubuntu, I did not have any Ubuntu Disks (gave then all away) so i used edubuntu. This problem concerns me because it might happen to me. Or should it have already? Try edubuntu, on the text based installation you have moreoptions.

---

### Post by pPrdrm on 2007-08-24
And here is my **dmesg | grep USB** output:

```
[20094.518564] usb 3-5: USB disconnect, address 21
[20094.758311] usb 3-5: new high speed USB device using ehci_hcd and address 22
[20094.892735] scsi21 : SCSI emulation for USB Mass Storage devices
[21826.853932] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[21826.965831] usb 3-5: reset high speed USB device using ehci_hcd and address 22
[21831.845106] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[21831.957007] usb 3-5: reset high speed USB device using ehci_hcd and address 22
[21836.164924] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[21836.284814] usb 3-5: reset high speed USB device using ehci_hcd and address 22
[22073.447286] usb 3-5: USB disconnect, address 22
[22073.854894] usb 3-5: new high speed USB device using ehci_hcd and address 23
[22073.989237] scsi22 : SCSI emulation for USB Mass Storage devices
[22501.944573] usb 3-5: USB disconnect, address 23
[22504.198378] usb 3-5: new high speed USB device using ehci_hcd and address 24
[22504.332730] scsi23 : SCSI emulation for USB Mass Storage devices
[22528.630746] usb 3-5: USB disconnect, address 24
[22529.374013] usb 3-5: new high speed USB device using ehci_hcd and address 25
[22529.508321] scsi24 : SCSI emulation for USB Mass Storage devices
[22702.346617] usb 3-5: USB disconnect, address 25
[22702.590377] usb 3-5: new high speed USB device using ehci_hcd and address 26
[22702.724765] scsi25 : SCSI emulation for USB Mass Storage devices
[23723.278528] usb 3-5: USB disconnect, address 26
[23723.522277] usb 3-5: new high speed USB device using ehci_hcd and address 27
[23723.656442] scsi26 : SCSI emulation for USB Mass Storage devices
[24225.796175] usb 3-5: USB disconnect, address 27
[24226.039926] usb 3-5: new high speed USB device using ehci_hcd and address 28
[24226.175195] scsi27 : SCSI emulation for USB Mass Storage devices
[25774.181608] usb 3-5: USB disconnect, address 28
[25774.425352] usb 3-5: new high speed USB device using ehci_hcd and address 29
[25774.559557] scsi28 : SCSI emulation for USB Mass Storage devices
[25787.776467] usb 3-5: USB disconnect, address 29
[25788.020204] usb 3-5: new high speed USB device using ehci_hcd and address 30
[25788.154632] scsi29 : SCSI emulation for USB Mass Storage devices
[26163.165157] usb 3-5: USB disconnect, address 30
[26163.412889] usb 3-5: new high speed USB device using ehci_hcd and address 31
[26163.559057] scsi30 : SCSI emulation for USB Mass Storage devices
[26253.545657] usb 3-5: USB disconnect, address 31
[26253.789414] usb 3-5: new high speed USB device using ehci_hcd and address 32
[26253.923912] scsi31 : SCSI emulation for USB Mass Storage devices
[27616.870195] usb 3-5: USB disconnect, address 32
[27617.113936] usb 3-5: new high speed USB device using ehci_hcd and address 33
[27617.248421] scsi32 : SCSI emulation for USB Mass Storage devices
[27752.566860] usb 3-5: USB disconnect, address 33
[27752.810605] usb 3-5: new high speed USB device using ehci_hcd and address 34
[27752.944964] scsi33 : SCSI emulation for USB Mass Storage devices
[27858.320505] usb 3-5: USB disconnect, address 34
[27858.564262] usb 3-5: new high speed USB device using ehci_hcd and address 35
[27858.698598] scsi34 : SCSI emulation for USB Mass Storage devices
[28294.885986] usb 3-5: USB disconnect, address 35
[28295.129749] usb 3-5: new high speed USB device using ehci_hcd and address 36
[28295.264248] scsi35 : SCSI emulation for USB Mass Storage devices
[30280.823941] usb 3-5: USB disconnect, address 36
[30281.203562] usb 3-5: new high speed USB device using ehci_hcd and address 37
[30281.338021] scsi36 : SCSI emulation for USB Mass Storage devices
[31043.921386] usb 3-5: USB disconnect, address 37
[31044.165155] usb 3-5: new high speed USB device using ehci_hcd and address 38
[31044.299757] scsi37 : SCSI emulation for USB Mass Storage devices
[32168.077384] usb 3-5: USB disconnect, address 38
[32168.321154] usb 3-5: new high speed USB device using ehci_hcd and address 39
[32168.455643] scsi38 : SCSI emulation for USB Mass Storage devices
[32962.420593] usb 3-5: USB disconnect, address 39
[32962.704306] usb 3-5: new high speed USB device using ehci_hcd and address 40
[32962.838736] scsi39 : SCSI emulation for USB Mass Storage devices
[32995.400674] usb 3-5: USB disconnect, address 40
[32995.644454] usb 3-5: new high speed USB device using ehci_hcd and address 41
[32995.778799] scsi40 : SCSI emulation for USB Mass Storage devices
[32996.407704] usb 3-5: USB disconnect, address 41
[32996.647459] usb 3-5: new high speed USB device using ehci_hcd and address 42
[32996.781757] scsi41 : SCSI emulation for USB Mass Storage devices
[33221.234110] usb 3-5: USB disconnect, address 42
[33221.477857] usb 3-5: new high speed USB device using ehci_hcd and address 43
[33221.612212] scsi42 : SCSI emulation for USB Mass Storage devices

```

(I don't know much but I think all these addresses: **"...address 42"** must be some kind of indication about how many time this has happened  until now)

It just keeps doing that. It mounts and unmounts with no obvious reason. Now that I remember, I think Dapper also did this after the last update I did just before I move to Feisty.

---

### Post by Digital Magi on 2007-08-26
I am having a similar issue with a 2 gig pen drive. It mounts and unmounts continuously and is unusable at present. I have an older 512K pen drive that functions normally when inserted into the same USB port.

No idea why. This device performs normally in the other computers I use at work or home, only does this on my stock Feisty machine at home.

However, my USB external HD on the same machine performs normally.

---

### Post by Tsega on 2007-08-26
Hello People! I have the same problem too. But as for me I bet it's my computer that's causing this to happen. I've used my USB 2.0 1GB pend drive with another Machine somewhere else and it worked just fine! So maybe the problem is with the USB slots of your machines. **Suggestion:** use it on another machine with Fiesty installed and check if it has the same problem.

---

### Post by Golyadkin on 2007-08-26
> **ev5unleash1 said:**
> I just got a Laptop Harddrive case for USB to IDE. And it work perfectly with Ubuntu,

Same for me here, I bought an Icy Box external 2.5" laptop harddrive enclosure: 

[[IMG]http://farm2.static.flickr.com/1258/1214195566_e8e22ec894.jpg[/IMG]]("http://www.flickr.com/photos/yjanse/1214195566/")

It has a 7200rpm Toshiba harddisk and has been mounted for 14 hours now without interruption. It's connected with a USB cable on the USB 2.0 port of my MSI K9N Neo-F motherboard. I was also afraid that it would shut down or that I would have to use it at crawling USB 1.0 speed, but luckily that is not the case. 

My Ubuntu version is Feisty Fawn 7.04 / 32 bits.
> 
Linux venti 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux


---

### Post by pPrdrm on 2007-08-26
I don't think that it has to do with my computer because I also have a **1GB Flash Drive** with **USB 2.0** interface that works just fine. I don't have other USB 2.0 devices to double check this but I am almost sure that it's a software problem. I also checked it on the same computer under Windows and it works OK. And, as I've mentioned, if I remove the [COLOR="Red"]**ehci_hcd**[/COLOR] module it work OK but painfully slow.

---

### Post by pPrdrm on 2007-09-03
Well, I gave up. I've formated a 30GB partition of my internal hard drive from **NTFS** to **fat32** and continue from there. At least if I knew what was the problem or where to look for it my self...
I hope this will be solved in Gutsy Gibbon's release.

---

### Post by BrendanAJS on 2007-09-03
Hi All,

Up in the middle of the night in Switerland and actually have the answer to this one.

This problem occurs when the external HD goes to sleep and something in the wake-up cuases the disk not to remain mounted or a range of other issues with access such as corruption.

The work around is to do a cron job to carry out some simple operation on the disk every 10 min or so, so that the little devil (limeme) never gets to go to sleep.

The method I used was simple:

1. Create 2 hidden text files in the USB HD root called .wakesource and .wakedest
2. Open .wakesource and enter a few characters of text (file cannot be empty)
3. Write the following script to a file or enter into the /etc/crontab:

* * * * * root touch /mnt/media/.wakesource ; cp /mnt/media/.wakesource /mnt/media/.wakedest

Alter the paths acordingly for your mounter USB HD
This cron callls every min, but you can adjust it to call it every 10 min (as I do)

---

### Post by pPrdrm on 2007-09-04
Hello **BrendanAJS**,
By saying that the drive is going to **sleep**, do you mean that no program is accessing the hard drive for some time? If yes, I don't thing it's this case here because the problem occurs even when I am working with files stored in the USB drive e.g. it happens even when I am watching a video file. Vlc player need to have access to the video file every few seconds. So I don't think that it could fall "asleep".

P.S. Having people staying awake late at night just to help others is very hopeful for our world :)

---

### Post by taggat on 2007-10-31
I have the same problem. A 500gb USB 2.0 harddrive that refuses to act properly. 
It will sometimes not show up at all sometimes it does show up but then disappears and VLC will be playing something off of it and it will just stop working.
This is a major issue and might make we have to go get a copy of XP which would suck.

---

### Post by konungursvia on 2007-11-05
I have the same problem with a 300 Gb external usb drive, half of which is fat32, half ntfs. When I run Amarok and try to read my 2000 songs, but the ntfs half is idle, the thing unmounts uncleanly, freezing amarok and eventually x. Also, I noted a "failed to mount region 5 of device" message or some such words every time i boot gutsy, which may be related to an earlier post. Now that I have a film downloading into the ntfs half, and am playing mp3s off the fat32 half, it is not unmounting at all. Maybe this has been a bad fix for the "ubuntu may be wrecking your hdd" problem now seen on digg: a hastily re-written stop / start spinning algorithm?

---

### Post by zman58 on 2007-11-14
i would suspect faulty hardware; cable, connectors, or the drive itself.

---

