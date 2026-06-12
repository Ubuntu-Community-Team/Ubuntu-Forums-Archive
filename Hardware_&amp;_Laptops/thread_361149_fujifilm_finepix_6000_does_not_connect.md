---
title: "fujifilm finepix 6000 does not connect"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by kroiz on 2007-02-14
My wify bought a new camera fujifilm 6500 AKA 6000.
It connects to the pc using a USB cable.
but when I connect it nothing happen. ( It works fine on my other os ).
any ideas?

---

### Post by yabbadabbadont on 2007-02-14
Plug in the camera and then from a terminal window run the following commands and then please post the output back here:
```
dmesg
lsusb
ls -lR /dev/bus/usb
grep "usb_device" /etc/udev/rules.d/*
id
```

---

### Post by kroiz on 2007-02-16
dmesg:
```
[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[17179569.184000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000004ff50000 (usable)
[17179569.184000]  BIOS-e820: 000000004ff50000 - 000000004ff67000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000004ff67000 - 000000004ff79000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000004ff80000 - 0000000050000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[17179569.184000] 383MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 327504
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 98128 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v002 IBM                                   ) @ 0x000f6d70
[17179569.184000] ACPI: XSDT (v001 IBM    TP-1R    0x00003210  LTP 0x00000000) @ 0x4ff5a6bd
[17179569.184000] ACPI: FADT (v003 IBM    TP-1R    0x00003210 IBM  0x00000001) @ 0x4ff5a800
[17179569.184000] ACPI: SSDT (v001 IBM    TP-1R    0x00003210 MSFT 0x0100000e) @ 0x4ff5a9b4
[17179569.184000] ACPI: ECDT (v001 IBM    TP-1R    0x00003210 IBM  0x00000001) @ 0x4ff66ecc
[17179569.184000] ACPI: TCPA (v001 IBM    TP-1R    0x00003210 PTL  0x00000001) @ 0x4ff66f1e
[17179569.184000] ACPI: BOOT (v001 IBM    TP-1R    0x00003210  LTP 0x00000001) @ 0x4ff66fd8
[17179569.184000] ACPI: DSDT (v001 IBM    TP-1R    0x00003210 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 60000000 (gap: 50000000:af800000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=5ef1d9fe-482e-47ca-b87c-80b97e2afc02 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01a0d000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1598.859 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.524000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.524000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.576000] Memory: 1287168k/1310016k available (1911k kernel code, 21612k reserved, 1073k data, 308k init, 392512k highmem)
[17179569.576000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.656000] Calibrating delay using timer specific routine.. 3200.49 BogoMIPS (lpj=6400992)
[17179569.656000] Security Framework v1.0.0 initialized
[17179569.656000] SELinux:  Disabled at boot.
[17179569.656000] Mount-cache hash table entries: 512
[17179569.656000] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[17179569.656000] CPU: After vendor identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[17179569.656000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.656000] CPU: L2 cache: 1024K
[17179569.656000] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00000040 00000180 00000000 00000000
[17179569.656000] Checking 'hlt' instruction... OK.
[17179569.672000] SMP alternatives: switching to UP code
[17179569.672000] Freeing SMP alternatives: 16k freed
[17179569.672000] checking if image is initramfs... it is
[17179570.376000] Freeing initrd memory: 6779k freed
[17179570.376000] ACPI: Core revision 20060707
[17179570.376000] ACPI: Looking for DSDT ... not found!
[17179570.380000] ACPI: setting ELCR to 0200 (from 0800)
[17179570.392000] CPU0: Intel(R) Pentium(R) M processor 1600MHz stepping 05
[17179570.392000] SMP motherboard not detected.
[17179570.392000] Local APIC not detected. Using dummy APIC emulation.
[17179570.392000] Brought up 1 CPUs
[17179570.392000] migration_cost=0
[17179570.392000] NET: Registered protocol family 16
[17179570.392000] EISA bus registered
[17179570.392000] ACPI: bus type pci registered
[17179570.392000] PCI: PCI BIOS revision 2.10 entry at 0xfd8d6, last bus=8
[17179570.392000] PCI: Using configuration type 1
[17179570.392000] Setting up standard PCI resources
[17179570.396000] ACPI: Found ECDT
[17179570.404000] ACPI: Interpreter enabled
[17179570.404000] ACPI: Using PIC for interrupt routing
[17179570.404000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[17179570.404000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[17179570.404000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[17179570.408000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[17179570.408000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[17179570.408000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[17179570.408000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[17179570.408000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[17179570.408000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.408000] PCI: Probing PCI hardware (bus 00)
[17179570.412000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179570.412000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179570.412000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.412000] Boot video device is 0000:01:00.0
[17179570.412000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.412000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.420000] ACPI: Embedded Controller [EC] (gpe 28) interrupt mode.
[17179570.420000] ACPI: Power Resource [PUBS] (on)
[17179570.420000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179570.420000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179570.420000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.420000] pnp: PnP ACPI init
[17179570.424000] pnp: PnP ACPI: found 13 devices
[17179570.424000] PnPBIOS: Disabled by ACPI PNP
[17179570.424000] PCI: Using ACPI for IRQ routing
[17179570.424000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.436000] PCI: Bridge: 0000:00:01.0
[17179570.436000]   IO window: 3000-3fff
[17179570.436000]   MEM window: c0100000-c01fffff
[17179570.436000]   PREFETCH window: e0000000-e7ffffff
[17179570.436000] PCI: Bus 3, cardbus bridge: 0000:02:00.0
[17179570.436000]   IO window: 00004000-000040ff
[17179570.436000]   IO window: 00004400-000044ff
[17179570.436000]   PREFETCH window: e8000000-e9ffffff
[17179570.436000]   MEM window: c2000000-c3ffffff
[17179570.436000] PCI: Bus 7, cardbus bridge: 0000:02:00.1
[17179570.436000]   IO window: 00004800-000048ff
[17179570.436000]   IO window: 00004c00-00004cff
[17179570.436000]   PREFETCH window: ea000000-ebffffff
[17179570.436000]   MEM window: c4000000-c5ffffff
[17179570.436000] PCI: Bridge: 0000:00:1e.0
[17179570.436000]   IO window: 4000-8fff
[17179570.436000]   MEM window: c0200000-cfffffff
[17179570.436000]   PREFETCH window: e8000000-efffffff
[17179570.436000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.440000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179570.440000] PCI: setting IRQ 11 as level-triggered
[17179570.440000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179570.440000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[17179570.440000] ACPI: PCI Interrupt 0000:02:00.1[b] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179570.440000] NET: Registered protocol family 2
[17179570.476000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.476000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[17179570.476000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179570.480000] TCP: Hash tables configured (established 262144 bind 65536)
[17179570.480000] TCP reno registered
[17179570.480000] Simple Boot Flag at 0x35 set to 0x1
[17179570.480000] audit: initializing netlink socket (disabled)
[17179570.480000] audit(1171616210.480:1): initialized
[17179570.480000] highmem bounce pool size: 64 pages
[17179570.480000] VFS: Disk quotas dquot_6.5.1
[17179570.480000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.480000] Initializing Cryptographic API
[17179570.480000] io scheduler noop registered
[17179570.480000] io scheduler anticipatory registered
[17179570.480000] io scheduler deadline registered
[17179570.480000] io scheduler cfq registered (default)
[17179570.480000] isapnp: Scanning for PnP cards...
[17179570.832000] isapnp: No Plug & Play device found
[17179570.864000] Real Time Clock Driver v1.12ac
[17179570.864000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.864000] pnp: Device 00:0a activated.
[17179570.864000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[17179570.864000] ACPI: PCI Interrupt 0000:00:1f.6[b] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179570.864000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179570.864000] mice: PS/2 mouse device common for all mice
[17179570.864000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.864000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.864000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.864000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[17179570.872000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.872000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.872000] EISA: Probing bus 0 at eisa.0
[17179570.872000] Cannot allocate resource for EISA slot 1
[17179570.872000] Cannot allocate resource for EISA slot 2
[17179570.872000] Cannot allocate resource for EISA slot 3
[17179570.872000] Cannot allocate resource for EISA slot 4
[17179570.872000] Cannot allocate resource for EISA slot 5
[17179570.872000] Cannot allocate resource for EISA slot 6
[17179570.872000] Cannot allocate resource for EISA slot 7
[17179570.872000] Cannot allocate resource for EISA slot 8
[17179570.872000] EISA: Detected 0 cards.
[17179570.872000] TCP bic registered
[17179570.872000] NET: Registered protocol family 1
[17179570.872000] NET: Registered protocol family 8
[17179570.872000] NET: Registered protocol family 20
[17179570.872000] Using IPI No-Shortcut mode
[17179570.872000] ACPI: (supports S0 S3 S4 S5)
[17179570.872000] Freeing unused kernel memory: 308k freed
[17179570.880000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.000000] Capability LSM initialized
[17179572.036000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179572.036000] ACPI: Processor [CPU] (supports 8 throttling states)
[17179572.040000] ACPI: Thermal Zone [THM0] (46 C)
[17179572.356000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179572.356000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179572.356000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179572.356000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179572.356000] ICH4: chipset revision 1
[17179572.356000] ICH4: not 100% native mode: will probe irqs later
[17179572.356000]     ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
[17179572.356000]     ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:DMA, hdd:pio
[17179572.356000] Probing IDE interface ide0...
[17179572.644000] hda: HTS548080M9AT00, ATA DISK drive
[17179573.316000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.332000] Probing IDE interface ide1...
[17179574.068000] hdc: HL-DT-STCD-RW/DVD DRIVE GCC-4242N, ATAPI CD/DVD-ROM drive
[17179574.404000] ide1 at 0x170-0x177,0x376 on irq 15
[17179574.412000] hda: max request size: 512KiB
[17179574.420000] hda: 156301488 sectors (80026 MB) w/7877KiB Cache, CHS=16383/255/63, UDMA(100)
[17179574.420000] hda: cache flushes supported
[17179574.420000]  hda: hda1 hda2 hda3 < hda5 >
[17179574.492000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179574.492000] Uniform CD-ROM driver Revision: 3.20
[17179574.844000] usbcore: registered new driver usbfs
[17179574.844000] usbcore: registered new driver hub
[17179574.848000] USB Universal Host Controller Interface driver v3.0
[17179574.848000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179574.848000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179574.848000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179574.848000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179574.848000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[17179574.848000] usb usb1: configuration #1 chosen from 1 choice
[17179574.848000] hub 1-0:1.0: USB hub found
[17179574.848000] hub 1-0:1.0: 2 ports detected
[17179574.952000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179574.952000] ACPI: PCI Interrupt 0000:00:1d.1[b] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179574.952000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179574.952000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179574.952000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179574.952000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[17179574.952000] usb usb2: configuration #1 chosen from 1 choice
[17179574.952000] hub 2-0:1.0: USB hub found
[17179574.952000] hub 2-0:1.0: 2 ports detected
[17179575.056000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179575.056000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179575.056000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179575.056000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179575.056000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[17179575.056000] usb usb3: configuration #1 chosen from 1 choice
[17179575.056000] hub 3-0:1.0: USB hub found
[17179575.056000] hub 3-0:1.0: 2 ports detected
[17179575.176000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[17179575.176000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[17179575.176000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179575.176000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179575.180000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179575.180000] ehci_hcd 0000:00:1d.7: debug port 1
[17179575.180000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179575.180000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
[17179575.180000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.184000] usb usb4: configuration #1 chosen from 1 choice
[17179575.184000] hub 4-0:1.0: USB hub found
[17179575.184000] hub 4-0:1.0: 6 ports detected
[17179575.800000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[17179575.980000] usb 2-1: configuration #1 chosen from 1 choice
[17179575.980000] kjournald starting.  Commit interval 5 seconds
[17179575.980000] EXT3-fs: mounted filesystem with ordered data mode.
[17179575.992000] usbcore: registered new driver hiddev
[17179576.016000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input1
[17179576.016000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.1-1
[17179576.016000] usbcore: registered new driver usbhid
[17179576.016000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179594.016000] parport: PnPBIOS parport detected.
[17179594.016000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[17179594.060000] Linux agpgart interface v0.101 (c) Dave Jones
[17179594.076000] agpgart: Detected an Intel 855PM Chipset.
[17179594.088000] agpgart: AGP aperture is 256M @ 0xd0000000
[17179594.124000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179594.132000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179594.220000] Floppy drive(s): fd0 is 1.44M
[17179594.236000] FDC 0 is a National Semiconductor PC87306
[17179594.444000] hw_random: RNG not detected
[17179594.460000] input: PC Speaker as /class/input/input2
[17179594.648000] irda_init()
[17179594.648000] NET: Registered protocol family 23
[17179594.864000] ts: Compaq touchscreen protocol output
[17179594.876000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
[17179594.876000] serio: Synaptics pass-through port at isa0060/serio1/input0
[17179594.916000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[17179594.920000] pnp: Device 00:0c activated.
[17179594.920000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[17179594.920000] nsc-ircc, chip->init
[17179594.920000] nsc-ircc, Found chip at base=0x02e
[17179594.920000] nsc-ircc, driver loaded (Dag Brattli)
[17179594.920000] IrDA: Registered device irda0
[17179594.920000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[17179595.024000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179595.024000] Yenta: CardBus bridge found at 0000:02:00.0 [1014:0552]
[17179595.024000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179595.024000] Yenta: Routing CardBus interrupts to PCI
[17179595.024000] Yenta TI: socket 0000:02:00.0, mfunc 0x01d21b22, devctl 0x64
[17179595.232000] Intel(R) PRO/1000 Network Driver - version 7.1.9-k4
[17179595.232000] Copyright (c) 1999-2006 Intel Corporation.
[17179595.256000] Yenta: ISA IRQ mask 0x0430, PCI irq 11
[17179595.256000] Socket status: 30000086
[17179595.256000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[17179595.256000] cs: IO port probe 0x4000-0x8fff: clean.
[17179595.256000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[17179595.256000] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[17179595.256000] ACPI: PCI Interrupt 0000:00:1f.5[b] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179595.256000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179595.256000] ACPI: PCI Interrupt 0000:02:00.1[b] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179595.256000] Yenta: CardBus bridge found at 0000:02:00.1 [1014:0552]
[17179595.256000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179595.256000] Yenta: Routing CardBus interrupts to PCI
[17179595.256000] Yenta TI: socket 0000:02:00.1, mfunc 0x01d21b22, devctl 0x64
[17179595.276000] ieee80211_crypt: registered algorithm 'NULL'
[17179595.280000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179595.280000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179595.304000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[17179595.304000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[17179595.488000] Yenta: ISA IRQ mask 0x0430, PCI irq 11
[17179595.488000] Socket status: 30000086
[17179595.488000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[17179595.488000] cs: IO port probe 0x4000-0x8fff: clean.
[17179595.488000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[17179595.488000] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[17179596.076000] intel8x0_measure_ac97_clock: measured 55356 usecs
[17179596.076000] intel8x0: clocking to 48000
[17179596.076000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179596.336000] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:11:25:2f:ec:e2
[17179596.372000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[17179596.372000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179596.372000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[17179596.400000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[17179596.400000] cs: IO port probe 0xc00-0xcf7: clean.
[17179596.400000] cs: IO port probe 0xa00-0xaff: clean.
[17179596.404000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[17179596.404000] cs: IO port probe 0xc00-0xcf7: clean.
[17179596.404000] cs: IO port probe 0xa00-0xaff: clean.
[17179597.976000] NET: Registered protocol family 17
[17179599.192000] lp0: using parport0 (interrupt-driven).
[17179599.384000] Adding 1172704k swap on /dev/disk/by-uuid/b5876757-3de3-48bf-8790-935a62132b6b.  Priority:-1 extents:1 across:1172704k
[17179599.472000] EXT3 FS on hda2, internal journal
[17179599.696000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179599.696000] md: bitmap version 4.39
[17179599.896000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[17179600.124000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[17179600.392000] input: TPPS/2 IBM TrackPoint as /class/input/input4
[17179601.156000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179601.224000] NTFS volume version 3.1.
[17179602.532000] ACPI: AC Adapter [AC] (on-line)
[17179602.576000] NET: Registered protocol family 10
[17179602.576000] lo: Disabled Privacy Extensions
[17179602.576000] IPv6 over IPv4 tunneling driver
[17179602.628000] ACPI: Battery Slot [BAT0] (battery present)
[17179602.644000] ACPI: Power Button (FF) [PWRF]
[17179602.644000] ACPI: Lid Switch [LID]
[17179602.644000] ACPI: Sleep Button (CM) [SLPB]
[17179602.684000] ACPI: ACPI Dock Station Driver 
[17179602.776000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
[17179602.776000] ibm_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[17179602.800000] pcc_acpi: loading...
[17179602.908000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179607.348000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179609.836000] [drm] Initialized drm 1.0.1 20051102
[17179609.960000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179609.960000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179611.404000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x2000000
[17179611.404000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x2000000
[17179611.404000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x2000000
[17179611.404000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179611.404000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17179611.404000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[17179611.692000] [drm] Setting GART location based on new memory map
[17179611.692000] [drm] Loading R200 Microcode
[17179611.696000] [drm] writeback test succeeded in 2 usecs
[17179612.520000] Non-volatile memory driver v1.2
[17179612.572000] input: /usr/sbin/thinkpad-keys as /class/input/input5
[17179612.640000] eth1: no IPv6 routers present
[17179612.864000] Bluetooth: Core ver 2.8
[17179612.864000] NET: Registered protocol family 31
[17179612.864000] Bluetooth: HCI device and connection manager initialized
[17179612.864000] Bluetooth: HCI socket layer initialized
[17179612.908000] Bluetooth: L2CAP ver 2.8
[17179612.908000] Bluetooth: L2CAP socket layer initialized
[17179612.948000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179612.980000] Bluetooth: RFCOMM socket layer initialized
[17179612.980000] Bluetooth: RFCOMM TTY layer initialized
[17179612.980000] Bluetooth: RFCOMM ver 1.7
[17182153.236000] usb 4-4: new high speed USB device using ehci_hcd and address 3
[17182153.368000] usb 4-4: configuration #1 chosen from 1 choice

```lsusb:
> Bus 004 Device 003: ID 04cb:01bf Fuji Photo Film Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  ls -lR /dev/bus/usb:
> /dev/bus/usb:
total 0
drwxr-xr-x 2 root root 60 2007-02-16 10:56 001
drwxr-xr-x 2 root root 80 2007-02-16 10:56 002
drwxr-xr-x 2 root root 60 2007-02-16 10:56 003
drwxr-xr-x 2 root root 80 2007-02-16 09:39 004
lrwxrwxrwx 1 root root 14 2007-02-16 08:57 devices -> .usbfs/devices

/dev/bus/usb/001:
total 0
crw-rw-r-- 1 root root 189, 0 2007-02-16 10:56 001

/dev/bus/usb/002:
total 0
crw-rw-r-- 1 root root 189, 128 2007-02-16 10:56 001
crw-rw-r-- 1 root root 189, 129 2007-02-16 10:56 002

/dev/bus/usb/003:
total 0
crw-rw-r-- 1 root root 189, 256 2007-02-16 10:56 001

/dev/bus/usb/004:
total 0
crw-rw-r-- 1 root root 189, 384 2007-02-16 10:56 001
crw-rw-r-- 1 root root 189, 386 2007-02-16 09:39 003
grep "usb_device" /etc/udev/rules.d/*:
> /etc/udev/rules.d/20-names.rules:SUBSYSTEM!="usb_device", GOTO="usb_device_end"
/etc/udev/rules.d/20-names.rules:IMPORT{program}="usb_device_name --export %k"
/etc/udev/rules.d/20-names.rules:LABEL="usb_device_end"
/etc/udev/rules.d/40-permissions.rules:SUBSYSTEM=="usb_device",         MODE="0664"
/etc/udev/rules.d/45-hplip.rules:SUBSYSTEM!="usb_device", GOTO="hplip_rules_end"
/etc/udev/rules.d/45-libgphoto2.rules:SUBSYSTEM=="usb_device", GOTO="libgphoto2_rules_real"
/etc/udev/rules.d/45-libsane.rules:SUBSYSTEM!="usb_device", GOTO="libsane_rules_end"
id:
> uid=1000(kroiz) gid=1000(kroiz) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(lpadmin),105(scanner),106(admin),116(nvram),1000(kroiz)


---

### Post by yabbadabbadont on 2007-02-16
> /etc/udev/rules.d/40-permissions.rules:SUBSYSTEM=="usb_device", MODE="0664"
Use sudo to edit /etc/udev/rules.d/40-permissions.rules with your favorite editor.  Find that line in the file.  Append:

, GROUP="plugdev"

(note the comma)  The line should look something like this when done:

SUBSYSTEM=="usb_device",                MODE="0664", GROUP="plugdev"

Save your changes, logout, and reboot.  It should work after that.

---

### Post by kroiz on 2007-02-16
still no success.
anything else I could try?
Should anything be triggered by the camera plugining, or should I be able to get to the camera some other way?

---

### Post by kroiz on 2007-02-16
should I add my camera to 45-libgphoto2.rules too?

---

### Post by yabbadabbadont on 2007-02-16
You could try that too.  The change I had you make is a long standing bug in the default udev configuration.  (It is the same on Gentoo, so it is probably an upstream issue.)

You might check the settings on your camera to see if it can be switched to something like "USB mass storage" or similar.  If it can, then you should be able to mount the camera as a usb drive and copy your images off of it.  You should probably also check your settings in the removable media control under System->Settings and verify that it is set to autolaunch a photo application whenever a camera is detected.  (assuming that you want that to happen)

---

### Post by kroiz on 2007-02-17
Yeh you did it. Thanks alot.
after adding it to 45-libgphoto2.rules too I just had to fix the settings in System->Prefereces->Removable Drives and Media.

---

### Post by kroiz on 2007-02-17
just another quick on. Do I need to unmount before i disconnect the usb? and if so how?

---

### Post by yabbadabbadont on 2007-02-17
> **kroiz said:**
> just another quick on. Do I need to unmount before i disconnect the usb? and if so how?

I would say yes... just to be safe.  How... hmmmm.  Does the camera show up on your desktop when you plug it in?  If so, you might try right-clicking on it and see if there is an umount or stop or ... option.  If all else fails, when the camera is mounted, try running "mount" in a terminal window and see what it says next to the entry for your camera (if any).  If it shows "ro" in there somewhere, or there isn't any entry listed for your camera, then it is probably safe to just unplug it...  You might even look in gphoto2 to see if there is an option there somewhere.

---

### Post by kroiz on 2007-02-17
It does not show on my desktop and I see nothing obviose to me in the mount output
> /dev/hda2 on / type ext3 (rw,errors=remount-ro,commit=600)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/windows type ntfs (ro,noexec,nosuid,nodev,umask=0222,nls=utf8)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
BTW what is gphoto2

---

### Post by yabbadabbadont on 2007-02-17
```
Package: gphoto2
New: yes
State: not installed
Version: 2.1.6-2.1
Priority: extra
Section: universe/utils
Maintainer: Frederic Peters <fpeters@debian.org>
Uncompressed Size: 823k
Depends: libc6 (>= 2.3.4-1), libcdk4, libexif12, libgphoto2-2 (>= 2.1.6-5.2ubuntu3), libgphoto2-port0 (>= 2.1.6-5.2ubuntu3),
         libjpeg62, libncurses5 (>= 5.4-5), libreadline5 (>= 5.1)
Suggests: gtkam, gthumb
Description: The gphoto2 digital camera command-line client
 The gphoto2 library can be used by applications to access various digital camera models. 
 
 This package provide the gphoto2 command-line frontend.

```
It isn't the GUI software that I thought it was apparently...:???:

It might be gthumb that I was thinking of.

---

