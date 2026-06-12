---
title: "no sound on thinkpad t23"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by kamilczauz on 2006-11-07
after i upgraded to edgy eft, i have no sound on my thinkpad t23.

From what i understand, my sound device is installed, but i have no "speaker" icon on my top panels notification area.

When i press the volume up and down button on the thinkpad, a little volume bar shows up on the screen and moves accordingly.

When i open up SYSTEM PREFRENCES SOUND and press the TEST button, i dont hear anything.  I also dont hear anyhting from music player or anything.

here is my dmesg:

```
kamil@kamil-laptop:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[17179569.184000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000ff70000 (usable)
[17179569.184000]  BIOS-e820: 000000000ff70000 - 000000000ff7e000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000ff7e000 - 000000000ff80000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000000ff80000 - 0000000010000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 255MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65392
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61296 pages, LIFO batch:15
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v002 IBM                                   ) @ 0x000f7450
[17179569.184000] ACPI: XSDT (v001 IBM    TP-1A    0x00001180  LTP 0x00000000) @ 0x0ff73af2
[17179569.184000] ACPI: FADT (v001 IBM    TP-1A    0x00001180 IBM  0x00000001) @ 0x0ff73c00
[17179569.184000] ACPI: SSDT (v001 IBM    TP-1A    0x00001180 MSFT 0x0100000d) @ 0x0ff73cb4
[17179569.184000] ACPI: ECDT (v001 IBM    TP-1A    0x00001180 IBM  0x00000001) @ 0x0ff7ded1
[17179569.184000] ACPI: BOOT (v001 IBM    TP-1A    0x00001180  LTP 0x00000001) @ 0x0ff7dfd8
[17179569.184000] ACPI: DSDT (v001 IBM    TP-1A    0x00001180 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:ef800000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0120a000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[17179569.184000] Detected 1199.133 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179573.120000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.120000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179573.136000] Memory: 249448k/261568k available (1910k kernel code, 11600k reserved, 1070k data, 308k init, 0k highmem)
[17179573.136000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.216000] Calibrating delay using timer specific routine.. 2400.29 BogoMIPS (lpj=4800595)
[17179573.216000] Security Framework v1.0.0 initialized
[17179573.216000] SELinux:  Disabled at boot.
[17179573.216000] Mount-cache hash table entries: 512
[17179573.216000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179573.216000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179573.216000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179573.216000] CPU: L2 cache: 512K
[17179573.216000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179573.216000] Checking 'hlt' instruction... OK.
[17179573.232000] SMP alternatives: switching to UP code
[17179573.232000] Freeing SMP alternatives: 16k freed
[17179573.232000] checking if image is initramfs... it is
[17179574.024000] Freeing initrd memory: 5564k freed
[17179574.024000] ACPI: Core revision 20060707
[17179574.028000] ACPI: Looking for DSDT ... not found!
[17179574.032000] ACPI: setting ELCR to 0200 (from 0800)
[17179574.256000] CPU0: Intel Mobile Intel(R) Pentium(R) III CPU - M  1200MHz stepping 04
[17179574.256000] SMP motherboard not detected.
[17179574.256000] Local APIC not detected. Using dummy APIC emulation.
[17179574.256000] Brought up 1 CPUs
[17179574.256000] migration_cost=0
[17179574.256000] NET: Registered protocol family 16
[17179574.256000] EISA bus registered
[17179574.256000] ACPI: bus type pci registered
[17179574.256000] PCI: PCI BIOS revision 2.10 entry at 0xfd8fe, last bus=8
[17179574.256000] PCI: Using configuration type 1
[17179574.256000] Setting up standard PCI resources
[17179574.256000] ACPI: Found ECDT
[17179574.268000] ACPI: Interpreter enabled
[17179574.268000] ACPI: Using PIC for interrupt routing
[17179574.272000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[17179574.272000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[17179574.272000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[17179574.272000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[17179574.272000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[17179574.276000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[17179574.276000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[17179574.276000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[17179574.276000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179574.276000] PCI: Probing PCI hardware (bus 00)
[17179574.280000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179574.280000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179574.280000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179574.280000] Boot video device is 0000:01:00.0
[17179574.280000] PCI: Transparent bridge - 0000:00:1e.0
[17179574.280000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.288000] ACPI: Embedded Controller [EC] (gpe 28) interrupt mode.
[17179574.288000] ACPI: Power Resource [PUBS] (on)
[17179574.292000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179574.292000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179574.296000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.296000] pnp: PnP ACPI init
[17179574.300000] pnp: PnP ACPI: found 13 devices
[17179574.300000] PnPBIOS: Disabled by ACPI PNP
[17179574.300000] PCI: Using ACPI for IRQ routing
[17179574.300000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.308000] PCI: Bridge: 0000:00:01.0
[17179574.308000]   IO window: disabled.
[17179574.308000]   MEM window: c0100000-c01fffff
[17179574.308000]   PREFETCH window: e0000000-ebffffff
[17179574.308000] PCI: Bus 3, cardbus bridge: 0000:02:00.0
[17179574.308000]   IO window: 00002000-000020ff
[17179574.308000]   IO window: 00002400-000024ff
[17179574.308000]   PREFETCH window: f0000000-f1ffffff
[17179574.308000]   MEM window: c2000000-c3ffffff
[17179574.308000] PCI: Bus 7, cardbus bridge: 0000:02:00.1
[17179574.308000]   IO window: 00002800-000028ff
[17179574.308000]   IO window: 00002c00-00002cff
[17179574.308000]   PREFETCH window: f2000000-f3ffffff
[17179574.308000]   MEM window: c4000000-c5ffffff
[17179574.308000] PCI: Bridge: 0000:00:1e.0
[17179574.308000]   IO window: 2000-6fff
[17179574.308000]   MEM window: c0200000-cfffffff
[17179574.308000]   PREFETCH window: f0000000-f7ffffff
[17179574.308000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179574.312000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179574.312000] PCI: setting IRQ 11 as level-triggered
[17179574.312000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179574.312000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[17179574.312000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179574.312000] NET: Registered protocol family 2
[17179574.352000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179574.352000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[17179574.352000] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[17179574.352000] TCP: Hash tables configured (established 8192 bind 4096)
[17179574.352000] TCP reno registered
[17179574.352000] Simple Boot Flag at 0x35 set to 0x1
[17179574.352000] audit: initializing netlink socket (disabled)
[17179574.352000] audit(1162922755.352:1): initialized
[17179574.352000] VFS: Disk quotas dquot_6.5.1
[17179574.352000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.352000] Initializing Cryptographic API
[17179574.352000] io scheduler noop registered
[17179574.352000] io scheduler anticipatory registered
[17179574.352000] io scheduler deadline registered
[17179574.352000] io scheduler cfq registered (default)
[17179574.352000] isapnp: Scanning for PnP cards...
[17179574.704000] isapnp: No Plug & Play device found
[17179574.748000] Real Time Clock Driver v1.12ac
[17179574.748000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.748000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[17179574.748000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[17179574.748000] mice: PS/2 mouse device common for all mice
[17179574.748000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.748000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.748000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.752000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[17179574.756000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.756000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.756000] EISA: Probing bus 0 at eisa.0
[17179574.756000] Cannot allocate resource for EISA slot 1
[17179574.756000] Cannot allocate resource for EISA slot 2
[17179574.756000] Cannot allocate resource for EISA slot 3
[17179574.756000] Cannot allocate resource for EISA slot 4
[17179574.756000] Cannot allocate resource for EISA slot 5
[17179574.756000] Cannot allocate resource for EISA slot 6
[17179574.756000] EISA: Detected 0 cards.
[17179574.756000] TCP bic registered
[17179574.756000] NET: Registered protocol family 1
[17179574.756000] NET: Registered protocol family 8
[17179574.756000] NET: Registered protocol family 20
[17179574.756000] Using IPI No-Shortcut mode
[17179574.756000] ACPI: (supports S0 S3 S4 S5)
[17179574.760000] Freeing unused kernel memory: 308k freed
[17179574.768000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.928000] Capability LSM initialized
[17179575.984000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179575.984000] ACPI: Thermal Zone [THM0] (41 C)
[17179576.464000] ICH3M: IDE controller at PCI slot 0000:00:1f.1
[17179576.464000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179576.464000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179576.464000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179576.464000] ICH3M: chipset revision 2
[17179576.464000] ICH3M: not 100% native mode: will probe irqs later
[17179576.464000]     ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
[17179576.464000]     ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:DMA, hdd:pio
[17179576.464000] Probing IDE interface ide0...
[17179576.752000] hda: ST94019A, ATA DISK drive
[17179577.424000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.624000] Probing IDE interface ide1...
[17179578.360000] hdc: TSSTcorpCDW/DVD TS-L462A, ATAPI CD/DVD-ROM drive
[17179579.032000] ide1 at 0x170-0x177,0x376 on irq 15
[17179579.040000] hda: max request size: 512KiB
[17179579.048000] hda: 78140160 sectors (40007 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179579.056000] hda: cache flushes supported
[17179579.056000]  hda: hda1 hda2 hda3 < hda5 >
[17179579.316000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179579.316000] Uniform CD-ROM driver Revision: 3.20
[17179579.688000] usbcore: registered new driver usbfs
[17179579.688000] usbcore: registered new driver hub
[17179579.692000] USB Universal Host Controller Interface driver v3.0
[17179579.692000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179579.692000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179579.692000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179579.696000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179579.696000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[17179579.696000] usb usb1: configuration #1 chosen from 1 choice
[17179579.696000] hub 1-0:1.0: USB hub found
[17179579.696000] hub 1-0:1.0: 2 ports detected
[17179579.800000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179579.800000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179579.800000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179579.800000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179579.800000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179579.800000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[17179579.800000] usb usb2: configuration #1 chosen from 1 choice
[17179579.800000] hub 2-0:1.0: USB hub found
[17179579.800000] hub 2-0:1.0: 2 ports detected
[17179579.904000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179579.904000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179579.904000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179579.904000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179579.904000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[17179579.904000] usb usb3: configuration #1 chosen from 1 choice
[17179579.904000] hub 3-0:1.0: USB hub found
[17179579.904000] hub 3-0:1.0: 2 ports detected
[17179580.104000] Attempting manual resume
[17179580.144000] kjournald starting.  Commit interval 5 seconds
[17179580.144000] EXT3-fs: mounted filesystem with ordered data mode.
[17179593.376000] Linux agpgart interface v0.101 (c) Dave Jones
[17179593.380000] agpgart: Detected an Intel 830M Chipset.
[17179593.396000] agpgart: AGP aperture is 256M @ 0xd0000000
[17179593.432000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179593.440000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.696000] hw_random hardware driver 1.0.0 loaded
[17179593.856000] Floppy drive(s): fd0 is 1.44M
[17179593.872000] FDC 0 is a National Semiconductor PC87306
[17179594.172000] input: PC Speaker as /class/input/input1
[17179594.216000] parport: PnPBIOS parport detected.
[17179594.216000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[17179594.584000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0001)
[17179594.584000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179594.584000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179594.660000] irda_init()
[17179594.660000] NET: Registered protocol family 23
[17179594.720000] pnp: Device 00:0c activated.
[17179594.720000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[17179594.720000] nsc-ircc, chip->init
[17179594.720000] nsc-ircc, Found chip at base=0x02e
[17179594.720000] nsc-ircc, driver loaded (Dag Brattli)
[17179594.720000] IrDA: Registered device irda0
[17179594.720000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[17179595.200000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179595.200000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179595.308000] intel8x0_measure_ac97_clock: measured 55292 usecs
[17179595.308000] intel8x0: clocking to 48000
[17179595.308000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179595.308000] Yenta: CardBus bridge found at 0000:02:00.0 [1014:023b]
[17179595.308000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179595.308000] Yenta: Routing CardBus interrupts to PCI
[17179595.308000] Yenta TI: socket 0000:02:00.0, mfunc 0x01d21022, devctl 0x64
[17179595.396000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[17179595.416000] input: TPPS/2 IBM TrackPoint as /class/input/input2
[17179595.456000] ts: Compaq touchscreen protocol output
[17179595.540000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[17179595.540000] Socket status: 30000006
[17179595.540000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x6fff
[17179595.540000] cs: IO port probe 0x2000-0x6fff: clean.
[17179595.540000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[17179595.540000] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf7ffffff
[17179595.540000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179595.540000] Yenta: CardBus bridge found at 0000:02:00.1 [1014:023b]
[17179595.540000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179595.540000] Yenta: Routing CardBus interrupts to PCI
[17179595.540000] Yenta TI: socket 0000:02:00.1, mfunc 0x01d21022, devctl 0x64
[17179595.772000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[17179595.772000] Socket status: 30000006
[17179595.772000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x6fff
[17179595.772000] cs: IO port probe 0x2000-0x6fff: clean.
[17179595.772000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[17179595.772000] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf7ffffff
[17179595.784000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[17179595.784000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[17179595.808000] e100: eth0: e100_probe: addr 0xc0200000, irq 11, MAC addr 00:02:8A:21:4B:F8
[17179595.920000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179596.432000] cs: IO port probe 0x100-0x3af: clean.
[17179596.436000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179596.436000] cs: IO port probe 0x820-0x8ff: clean.
[17179596.436000] cs: IO port probe 0xc00-0xcf7: clean.
[17179596.436000] cs: IO port probe 0xa00-0xaff: clean.
[17179596.436000] cs: IO port probe 0x100-0x3af: clean.
[17179596.436000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179596.436000] cs: IO port probe 0x820-0x8ff: clean.
[17179596.440000] cs: IO port probe 0xc00-0xcf7: clean.
[17179596.440000] cs: IO port probe 0xa00-0xaff: clean.
[17179596.556000] lp0: using parport0 (interrupt-driven).
[17179596.596000] Adding 746980k swap on /dev/disk/by-uuid/449b5883-f5f7-4f62-9b92-37c4d365294f.  Priority:-1 extents:1 across:746980k
[17179596.664000] EXT3 FS on hda2, internal journal
[17179596.904000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179596.964000] NET: Registered protocol family 17
[17179597.040000] NTFS volume version 3.0.
[17179597.856000] NET: Registered protocol family 10
[17179597.856000] lo: Disabled Privacy Extensions
[17179597.856000] IPv6 over IPv4 tunneling driver
[17179603.568000] ACPI: AC Adapter [AC] (on-line)
[17179603.636000] ACPI: Battery Slot [BAT0] (battery present)
[17179603.668000] ACPI: Power Button (FF) [PWRF]
[17179603.668000] ACPI: Lid Switch [LID]
[17179603.668000] ACPI: Sleep Button (CM) [SLPB]
[17179603.764000] ACPI: ACPI Dock Station Driver 
[17179603.884000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
[17179603.884000] ibm_acpi: http://ibm-acpi.sf.net/
[17179603.920000] pcc_acpi: loading...
[17179604.104000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179608.232000] [drm] Initialized drm 1.0.1 20051102
[17179608.268000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179608.272000] [drm] Initialized savage 2.4.1 20050313 on minor 0
[17179608.272000] mtrr: 0xe8000000,0x4000000 overlaps existing 0xe8000000,0x1000000
[17179608.272000] mtrr: base(0xe4000000) is not aligned on a size(0x5000000) boundary
[17179608.272000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179608.272000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17179608.272000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[17179608.612000] eth0: no IPv6 routers present
[17179609.072000] IBM machine detected. Enabling interrupts during APM calls.
[17179609.072000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179609.072000] apm: overridden by ACPI.
[17179621.588000] Non-volatile memory driver v1.2
[17179621.728000] input: /usr/sbin/thinkpad-keys as /class/input/input3
[17179621.992000] Bluetooth: Core ver 2.8
[17179621.992000] NET: Registered protocol family 31
[17179621.992000] Bluetooth: HCI device and connection manager initialized
[17179621.992000] Bluetooth: HCI socket layer initialized
[17179622.020000] Bluetooth: L2CAP ver 2.8
[17179622.020000] Bluetooth: L2CAP socket layer initialized
[17179622.056000] Bluetooth: RFCOMM socket layer initialized
[17179622.056000] Bluetooth: RFCOMM TTY layer initialized
[17179622.056000] Bluetooth: RFCOMM ver 1.7
[17179630.648000] cdrom: hdc: mrw address space DMA selected
[17179630.816000] cdrom: hdc: mrw address space DMA selected
[17182786.484000] input: /usr/sbin/thinkpad-keys as /class/input/input4

```

---

### Post by rattusdatorum on 2006-11-16
I have a similar problem on the T60p, the sound is extremely silent so I need to turn it up to 100 % to even hear something in WindowsXP (dual boot) it is really loud compared to other notebooks.

---

### Post by rattusdatorum on 2006-11-16
ahh fund the solution, in alsamixer nearly everything was muted (but I can remember to put it all up in the gui (this time I used the text-based version)) 

further info here:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

