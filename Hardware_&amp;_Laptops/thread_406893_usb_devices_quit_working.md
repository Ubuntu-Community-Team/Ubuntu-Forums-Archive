---
title: "usb devices quit working"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by adothompson on 2007-04-11
**Intro**
Sometime in the last 2 weeks my usb devices stopped responding.  I've been using Ubuntu on my Dell Latitude X300 since last spring.  I have a USB printer, thumb-drive, connector to my canon digital camera and connector to my samsung blackjack that all worked fine about 2 weeks ago.

**Attempted Fixes**
1. add **irqpoll** to boot parameter (seen here: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Workaround_for_random_device_disconnections](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Workaround_for_random_device_disconnections))
2. blacklist usb2.0 (from same source as #1)
3. tried various boot parameters (seen here: [http://www.linuxquestions.org/questions/showthread.php?p=1777297#post1777297](http://www.linuxquestions.org/questions/showthread.php?p=1777297#post1777297))
-- acpi=noirq
-- pci=noacpi acpi=noirq
-- pci=noacpi acpi=noirq noapic
4. tried boot parameters mentioned in dmesg output
-- lapic pci=assign-busses
-- lapic pci=assign-busses pci=routeirq

**Results**
1. output of **lsusb** was

```

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000

```

or missing bus 004 when usb2.0 was blacklisted

```

Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000

```

2. output of dmesg is as follows with all default boot parameters

```

[17179569.184000] Linux version 2.6.17-11-386 (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Tue Mar 13 23:30:30 UTC 2007 (Ubuntu 2.6.17-11.37-386)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000004767e000 (usable)
[17179569.184000]  BIOS-e820: 000000004767e000 - 00000000476e0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000476e0000 - 00000000476eb000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000476eb000 - 0000000047700000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 0000000047700000 - 0000000048000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[17179569.184000] 246MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 292478
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 63102 pages, LIFO batch:15
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000f5ea0
[17179569.184000] ACPI: RSDT (v001 DELL   Montara  0x06040000  LTP 0x00000000) @ 0x476e4e2e
[17179569.184000] ACPI: FADT (v001 DELL   MONTARA  0x06040000 PTL  0x00000050) @ 0x476eae9e
[17179569.184000] ACPI: BOOT (v001 DELL   $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x476eafa4
[17179569.184000] ACPI: ASF! (v001 DELL   MONTARA  0x06040000 PTL  0x00000001) @ 0x476eafcc
[17179569.184000] ACPI: SSDT (v001 INTEL  CPU0CST  0x00000001 INTL 0x20020725) @ 0x476e52c4
[17179569.184000] ACPI: SSDT (v001 DELL   MONTARA  0x06040000 INTL 0x20020725) @ 0x476e4e66
[17179569.184000] ACPI: DSDT (v001 INTEL  MONTARAG 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 48000000:b6c10000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=19ef2271-d853-49cb-b018-f35f863cca9c ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (018f4000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1399.071 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.560000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.560000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.608000] Memory: 1148464k/1169912k available (1829k kernel code, 20520k reserved, 1041k data, 288k init, 252408k highmem)
[17179570.608000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.688000] Calibrating delay using timer specific routine.. 2800.12 BogoMIPS (lpj=5600253)
[17179570.688000] Security Framework v1.0.0 initialized
[17179570.688000] SELinux:  Disabled at boot.
[17179570.688000] Mount-cache hash table entries: 512
[17179570.688000] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[17179570.688000] CPU: After vendor identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[17179570.688000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179570.688000] CPU: L2 cache: 2048K
[17179570.688000] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00000040 00000180 00000000 00000000
[17179570.688000] CPU: Intel(R) Pentium(R) M processor 1.40GHz stepping 06
[17179570.688000] Checking 'hlt' instruction... OK.
[17179570.704000] SMP alternatives: switching to UP code
[17179570.704000] Freeing SMP alternatives: 0k freed
[17179570.704000] checking if image is initramfs... it is
[17179571.508000] Freeing initrd memory: 6990k freed
[17179571.508000] ACPI: Core revision 20060707
[17179571.508000] ACPI: Looking for DSDT ... not found!
[17179571.508000] ACPI: setting ELCR to 0200 (from 0c20)
[17179571.536000] NET: Registered protocol family 16
[17179571.536000] EISA bus registered
[17179571.536000] ACPI: bus type pci registered
[17179571.536000] PCI: PCI BIOS revision 2.10 entry at 0xfd9b0, last bus=2
[17179571.536000] PCI: Using configuration type 1
[17179571.536000] Setting up standard PCI resources
[17179571.544000] ACPI: Interpreter enabled
[17179571.544000] ACPI: Using PIC for interrupt routing
[17179571.548000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.548000] PCI: Probing PCI hardware (bus 00)
[17179571.552000] Boot video device is 0000:00:02.0
[17179571.552000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179571.552000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179571.552000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179571.552000] PCI: Transparent bridge - 0000:00:1e.0
[17179571.552000] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[17179571.552000] Please report the result to linux-kernel to fix this permanently
[17179571.552000] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[17179571.552000] Please report the result to linux-kernel to fix this permanently
[17179571.552000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.556000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179571.556000] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[17179571.556000] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[17179571.556000] ACPI: PCI Interrupt Link [LNKC] (IRQs *11)
[17179571.556000] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[17179571.556000] ACPI: PCI Interrupt Link [LNKE] (IRQs *5)
[17179571.556000] ACPI: PCI Interrupt Link [LNKF] (IRQs 5) *0, disabled.
[17179571.556000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10) *0, disabled.
[17179571.556000] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[17179571.560000] ACPI: Embedded Controller [H_EC] (gpe 28) interrupt mode.
[17179571.564000] ACPI: Power Resource [PFAN] (on)
[17179571.564000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.564000] pnp: PnP ACPI init
[17179571.572000] pnp: PnP ACPI: found 9 devices
[17179571.572000] PnPBIOS: Disabled by ACPI PNP
[17179571.572000] PCI: Using ACPI for IRQ routing
[17179571.572000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.576000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179571.576000] PCI: Bus 3, cardbus bridge: 0000:02:03.0
[17179571.576000]   IO window: 00003000-000030ff
[17179571.576000]   IO window: 00003400-000034ff
[17179571.576000]   PREFETCH window: 50000000-51ffffff
[17179571.576000]   MEM window: 56000000-57ffffff
[17179571.576000] PCI: Bus 7, cardbus bridge: 0000:02:03.1
[17179571.576000]   IO window: 00003800-000038ff
[17179571.576000]   IO window: 00003c00-00003cff
[17179571.576000]   PREFETCH window: 52000000-53ffffff
[17179571.576000]   MEM window: 58000000-59ffffff
[17179571.576000] PCI: Bridge: 0000:00:1e.0
[17179571.576000]   IO window: 3000-3fff
[17179571.576000]   MEM window: e0200000-e02fffff
[17179571.576000]   PREFETCH window: 50000000-53ffffff
[17179571.576000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.576000] PCI: Enabling device 0000:02:03.0 (0000 -> 0003)
[17179571.576000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[17179571.576000] PCI: setting IRQ 10 as level-triggered
[17179571.576000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179571.576000] PCI: Setting latency timer of device 0000:02:03.0 to 64
[17179571.576000] PCI: Enabling device 0000:02:03.1 (0000 -> 0003)
[17179571.576000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[17179571.576000] ACPI: PCI Interrupt 0000:02:03.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179571.576000] PCI: Setting latency timer of device 0000:02:03.1 to 64
[17179571.576000] NET: Registered protocol family 2
[17179571.616000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.616000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179571.616000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.616000] TCP: Hash tables configured (established 262144 bind 65536)
[17179571.616000] TCP reno registered
[17179571.616000] Simple Boot Flag at 0x38 set to 0x1
[17179571.616000] audit: initializing netlink socket (disabled)
[17179571.616000] audit(1176315328.616:1): initialized
[17179571.616000] highmem bounce pool size: 64 pages
[17179571.616000] VFS: Disk quotas dquot_6.5.1
[17179571.616000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.616000] Initializing Cryptographic API
[17179571.616000] io scheduler noop registered
[17179571.616000] io scheduler anticipatory registered
[17179571.616000] io scheduler deadline registered
[17179571.616000] io scheduler cfq registered (default)
[17179571.616000] isapnp: Scanning for PnP cards...
[17179571.968000] isapnp: No Plug & Play device found
[17179571.992000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.992000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179571.992000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179571.992000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179571.992000] mice: PS/2 mouse device common for all mice
[17179571.996000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.996000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.996000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.996000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.996000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179572.000000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179572.000000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179572.000000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179572.000000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179572.000000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.000000] EISA: Probing bus 0 at eisa.0
[17179572.000000] Cannot allocate resource for EISA slot 1
[17179572.000000] Cannot allocate resource for EISA slot 2
[17179572.000000] Cannot allocate resource for EISA slot 3
[17179572.000000] EISA: Detected 0 cards.
[17179572.000000] TCP bic registered
[17179572.000000] NET: Registered protocol family 1
[17179572.000000] NET: Registered protocol family 8
[17179572.000000] NET: Registered protocol family 20
[17179572.000000] Using IPI Shortcut mode
[17179572.000000] ACPI: (supports S0 S3 S4 S5)
[17179572.000000] Freeing unused kernel memory: 288k freed
[17179572.152000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.132000] Capability LSM initialized
[17179573.160000] ACPI: Fan [FAN0] (on)
[17179573.164000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179573.164000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179573.168000] ACPI: Thermal Zone [THRM] (50 C)
[17179573.484000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179573.484000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179573.484000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179573.484000] PCI: setting IRQ 11 as level-triggered
[17179573.484000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179573.484000] ICH4: chipset revision 1
[17179573.484000] ICH4: not 100% native mode: will probe irqs later
[17179573.484000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
[17179573.484000] Probing IDE interface ide0...
[17179573.996000] hda: FUJITSU MHT2060AH, ATA DISK drive
[17179574.668000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.756000] hda: max request size: 128KiB
[17179574.756000] hda: 117210240 sectors (60011 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[17179574.760000] hda: cache flushes supported
[17179574.760000]  hda: hda1 hda2 < hda5 >
[17179574.956000] Probing IDE interface ide1...
[17179574.976000] usbcore: registered new driver usbfs
[17179574.976000] usbcore: registered new driver hub
[17179574.976000] USB Universal Host Controller Interface driver v3.0
[17179574.976000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179574.976000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179574.976000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179574.980000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179574.980000] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001820
[17179574.980000] usb usb1: configuration #1 chosen from 1 choice
[17179574.980000] hub 1-0:1.0: USB hub found
[17179574.980000] hub 1-0:1.0: 2 ports detected
[17179575.052000] ieee1394: Initialized config rom entry `ip1394'
[17179575.084000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[17179575.084000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[17179575.084000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179575.084000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179575.084000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[17179575.084000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179575.084000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xe0100000
[17179575.088000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.088000] usb usb2: configuration #1 chosen from 1 choice
[17179575.088000] hub 2-0:1.0: USB hub found
[17179575.088000] hub 2-0:1.0: 6 ports detected
[17179575.192000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179575.192000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179575.192000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179575.192000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179575.192000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[17179575.192000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[17179575.192000] usb usb3: configuration #1 chosen from 1 choice
[17179575.192000] hub 3-0:1.0: USB hub found
[17179575.192000] hub 3-0:1.0: 2 ports detected
[17179575.296000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179575.296000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179575.296000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179575.296000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[17179575.296000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001860
[17179575.296000] usb usb4: configuration #1 chosen from 1 choice
[17179575.296000] hub 4-0:1.0: USB hub found
[17179575.296000] hub 4-0:1.0: 2 ports detected
[17179575.428000] ACPI: PCI Interrupt 0000:02:03.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179575.480000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[e0211000-e02117ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[17179575.664000] Attempting manual resume
[17179575.716000] kjournald starting.  Commit interval 5 seconds
[17179575.716000] EXT3-fs: mounted filesystem with ordered data mode.
[17179576.760000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00065b4004fe3fcd]
[17179590.484000] Real Time Clock Driver v1.12ac
[17179591.524000] Linux agpgart interface v0.101 (c) Dave Jones
[17179591.536000] agpgart: Detected an Intel 855 Chipset.
[17179591.536000] agpgart: Detected 8060K stolen memory.
[17179591.544000] agpgart: AGP aperture is 128M @ 0xe8000000
[17179591.576000] irda_init()
[17179591.576000] NET: Registered protocol family 23
[17179591.700000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa54ab1, caps: 0x804713/0x0
[17179591.740000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179591.740000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[17179591.740000] nsc-ircc, chip->init
[17179591.740000] nsc-ircc, Found chip at base=0x02e
[17179591.740000] nsc-ircc, driver loaded (Dag Brattli)
[17179591.740000] nsc_ircc_open(), can't get iobase of 0x2f8
[17179591.740000] nsc-ircc, Found chip at base=0x02e
[17179591.740000] nsc-ircc, driver loaded (Dag Brattli)
[17179591.740000] nsc_ircc_open(), can't get iobase of 0x2f8
[17179591.744000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179591.744000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179591.744000] pnp: Device 00:06 disabled.
[17179592.124000] ts: Compaq touchscreen protocol output
[17179592.132000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179592.564000] intel8x0_measure_ac97_clock: measured 59152 usecs
[17179592.564000] intel8x0: clocking to 50948
[17179592.564000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179592.592000] hw_random: RNG not detected
[17179592.888000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179592.888000] Yenta: CardBus bridge found at 0000:02:03.0 [1028:014f]
[17179593.016000] Yenta: ISA IRQ mask 0x00b8, PCI irq 10
[17179593.016000] Socket status: 30000006
[17179593.016000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[17179593.016000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179593.016000] cs: IO port probe 0x3000-0x3fff: clean.
[17179593.016000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[17179593.016000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[17179593.016000] ACPI: PCI Interrupt 0000:02:03.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179593.016000] Yenta: CardBus bridge found at 0000:02:03.1 [1028:014f]
[17179593.096000] ieee80211_crypt: registered algorithm 'NULL'
[17179593.108000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179593.108000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179593.144000] Yenta: ISA IRQ mask 0x0038, PCI irq 10
[17179593.144000] Socket status: 30000006
[17179593.144000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[17179593.144000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179593.144000] cs: IO port probe 0x3000-0x3fff: clean.
[17179593.144000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[17179593.144000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[17179593.144000] tg3.c:v3.59.1 (August 25, 2006)
[17179593.144000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179593.220000] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0f:1f:44:fb:d6
[17179593.220000] eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[17179593.220000] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[17179593.252000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179593.252000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179593.252000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179593.252000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 5
[17179593.252000] PCI: setting IRQ 5 as level-triggered
[17179593.252000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[17179593.252000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179593.452000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[17179593.840000] cs: IO port probe 0x100-0x3af: clean.
[17179593.844000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179593.844000] cs: IO port probe 0x820-0x8ff: clean.
[17179593.844000] cs: IO port probe 0xc00-0xcf7: clean.
[17179593.844000] cs: IO port probe 0xa00-0xaff: clean.
[17179593.868000] cs: IO port probe 0x100-0x3af: clean.
[17179593.868000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179593.868000] cs: IO port probe 0x820-0x8ff: clean.
[17179593.868000] cs: IO port probe 0xc00-0xcf7: clean.
[17179593.868000] cs: IO port probe 0xa00-0xaff: clean.
[17179594.020000] lp: driver loaded but no devices found
[17179594.080000] SCSI subsystem initialized
[17179594.092000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179594.092000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179594.132000] fuse init (API version 7.6)
[17179594.176000] Adding 1863500k swap on /dev/disk/by-uuid/769edc7c-16fd-4cb1-94bc-d92cb3112e58.  Priority:-1 extents:1 across:1863500k
[17179594.256000] EXT3 FS on hda1, internal journal
[17179594.500000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179594.500000] md: bitmap version 4.39
[17179594.760000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: dm-devel@redhat.com
[17179597.232000] NET: Registered protocol family 17
[17179600.600000] ACPI: AC Adapter [ADP1] (on-line)
[17179600.640000] ACPI: Battery Slot [BAT1] (battery present)
[17179600.640000] ACPI: Battery Slot [BAT2] (battery absent)
[17179600.660000] ACPI: Power Button (FF) [PWRF]
[17179600.660000] ACPI: Lid Switch [LID0]
[17179600.660000] ACPI: Sleep Button (CM) [SLPB]
[17179600.660000] ACPI: Power Button (CM) [PWRB]
[17179600.708000] ACPI: ACPI Dock Station Driver 
[17179600.804000] ibm_acpi: ec object not found
[17179600.836000] pcc_acpi: loading...
[17179600.960000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[17179603.376000] [drm] Initialized drm 1.0.1 20051102
[17179603.392000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179603.392000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179603.396000] [drm] Initialized i915 1.5.0 20060119 on minor 1
[17179610.740000] apm: BIOS not found.
[17179613.044000] ttyS1: LSR safety check engaged!
[17179616.624000] PM: Writing back config space on device 0000:02:05.0 at offset b (was 165d14e4, writing 20031028)
[17179616.624000] PM: Writing back config space on device 0000:02:05.0 at offset 3 (was 0, writing 4008)
[17179616.624000] PM: Writing back config space on device 0000:02:05.0 at offset 2 (was 2000000, writing 2000001)
[17179616.624000] PM: Writing back config space on device 0000:02:05.0 at offset 1 (was 2b00000, writing 2b00106)
[17179620.048000] NET: Registered protocol family 10
[17179620.048000] lo: Disabled Privacy Extensions
[17179620.048000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179620.048000] IPv6 over IPv4 tunneling driver
[17179630.108000] eth1: no IPv6 routers present
[17179646.840000] vmmon: module license 'unspecified' taints kernel.
[17179646.840000] /dev/vmmon[4805]: Module vmmon: registered with major=10 minor=165
[17179646.840000] /dev/vmmon[4805]: Module vmmon: initialized
[17179648.968000] /dev/vmnet: open called by PID 4849 (vmnet-bridge)
[17179648.968000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17179648.968000] /dev/vmnet: port on hub 0 successfully opened
[17179648.968000] bridge-eth0: enabling the bridge
[17179648.968000] bridge-eth0: up
[17179648.968000] bridge-eth0: already up
[17179648.968000] bridge-eth0: attached
[17179650.100000] /dev/vmnet: open called by PID 4885 (vmnet-netifup)
[17179650.100000] /dev/vmnet: hub 1 does not exist, allocating memory.
[17179650.100000] /dev/vmnet: port on hub 1 successfully opened
[17179650.112000] /dev/vmnet: open called by PID 4886 (vmnet-netifup)
[17179650.112000] /dev/vmnet: hub 8 does not exist, allocating memory.
[17179650.112000] /dev/vmnet: port on hub 8 successfully opened
[17179650.176000] /dev/vmnet: open called by PID 4875 (vmnet-natd)
[17179650.180000] /dev/vmnet: port on hub 8 successfully opened
[17179653.168000] /dev/vmnet: open called by PID 4908 (vmnet-dhcpd)
[17179653.168000] /dev/vmnet: port on hub 8 successfully opened
[17179653.420000] /dev/vmnet: open called by PID 4913 (vmnet-dhcpd)
[17179653.420000] /dev/vmnet: port on hub 1 successfully opened
[17179654.176000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17179657.568000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179657.584000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17179657.676000] ieee80211_crypt: registered algorithm 'WEP'
[17179660.664000] vmnet1: no IPv6 routers present
[17179661.112000] vmnet8: no IPv6 routers present
[17179671.644000] eth1: no IPv6 routers present
[17180462.364000] eth1: no IPv6 routers present
[17180521.576000] eth1: no IPv6 routers present

```

**Help**
Any and all help is appreciated.  I really need to get usb working again.

---

### Post by adothompson on 2007-04-16
Ok now I'm up to using Feisty Fawn Beta.  Still no USB.  I'm not finding any luck here.

Is this a bug that might need to be reported?

Thanks.

---

### Post by dkaddict on 2007-04-18
Have you tried editing /boot/grub/menu.lst and adding 'noapic' to the end of the line beginning with 'kernel'? ie, so it looks like this

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=77f9d071-f5ae-49d9-b480-60a41e1eca7b ro quiet splash noapic
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=77f9d071-f5ae-49d9-b480-60a41e1eca7b ro single noapic
initrd		/boot/initrd.img-2.6.20-15-generic


It sorted out the USB problem for me. 

good luck

dkaddict

ps, I just read that using 'irqpoll' instead of 'noapic' works too. I am gonna try it now. Apparently it will enable USB devices and a wireless connection at the same time whereas 'noapic' will not allow USB and wireless to work at the same time

---

### Post by mengtze on 2007-04-18
I have given up on this (tried all the suggestions and options). Went back to DAPPER and everything is working fine. All my USB devices work well, even in VMWARE.  Feisty still has these issues....

---

### Post by dkaddict on 2007-04-18
Ok. Sorry you had to give up.

I tried the 'irqpoll' option in /boot/grub/menu.lst' instead of 'noapic' and everything is working now in Feisty.

If you return to Feisty, give it a try, it may work for you.

peace

dkaddict

---

### Post by adothompson on 2007-04-18
I've tried "noapic" and "irqpoll" and a number of other boot options with no luck.  I'm hanging in with out USB but it's a bit of a hassle.  Is this something that will be fixed in the kernel soon?  Am I still missing something?

---

### Post by mushr00m on 2007-04-18
**Fixed!? USB2 is still broken for sure.**  adothompson, I would stay at Dapper untill they fix this problem with the ehci_hcd kernel module.

Try removing the module with: "sudo modprobe -r ehci_hcd" and see if your devices are recognized.

edit- added bold because this problem is messing with my serenity.

---

### Post by teripittman on 2007-05-07
I am seeing a similar problem in Feisty with pilot link. If I run *modprobe visor product=0x70 vendor=0c80* (after doing the other modprobe commands), I can sync with pilot link. I did try running *sudo modprobe -r ehci_hcd* first, but it gives an error without also running that first command. Definitely something that needs fixing in Feisty.

---

### Post by nythacker on 2007-05-21
Try this solution as this worked for me:

1.) Make sure no Guest Virtual Machine is running.
2.) Open up a Terminal window or go to command line.
3.) Type

> **[COLOR="Blue"]sudo mount -t usbfs none /proc/bus/usb[/COLOR]**

4.) Open up and run your Guest Virtual Machine.

Your USB ports on your Guest Virtual Machine should now work.

Hope this helps...

---

### Post by adothompson on 2007-05-21
I'll try this but I don't really understand what a "Guest Virtual Machine" is.

Can someone explain?

---

### Post by nythacker on 2007-05-22
> **adothompson said:**
> I'll try this but I don't really understand what a "Guest Virtual Machine" is.

Can someone explain?

**[COLOR="Blue"]Host Machine[/COLOR]** =  The operating system where you installed VMware on. **[COLOR="Red"](e.g. Ubuntu)[/COLOR]**
**[COLOR="Blue"]Guest Virtual Machine[/COLOR]** = The operating system which is being run on a virtual machine (VM) using VMware. **[COLOR="Red"](e.g. M$ Windows)[/COLOR]**

Hope this clarifies things...

---

### Post by jrickard on 2007-08-08
Did this thread just die????

I have the same problem.  My USB devices worked perfectly.  I went to Florida for a week and on return, found NONE of them worked.  Put in a new 2.0 7-port hub with all new cables, STILL no printer, no Wacom tablet, no camera, no nothing on USB.

Found THIS in dmesg

```
[  109.540950] usb 5-4: new high speed USB device using ehci_hcd and address 11
[  110.411607] hub 5-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  110.523167] usb 5-4: new high speed USB device using ehci_hcd and address 12
[  111.393803] hub 5-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  111.505379] usb 5-4: new high speed USB device using ehci_hcd and address 13
[  111.912637] usb 5-4: device not accepting address 13, error -71
[  112.024510] usb 5-4: new high speed USB device using ehci_hcd and address 14
[  112.431694] usb 5-4: device not accepting address 14, error -71
[  121.411386] usb 5-4: new high speed USB device using ehci_hcd and address 15
[  122.282015] hub 5-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  122.393607] usb 5-4: new high speed USB device using ehci_hcd and address 16
[  123.264338] hub 5-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  123.375818] usb 5-4: new high speed USB device using ehci_hcd and address 17
[  123.783075] usb 5-4: device not accepting address 17, error -71
[  123.894874] usb 5-4: new high speed USB device using ehci_hcd and address 18
[  124.302132] usb 5-4: device not accepting address 18, error -71
[  143.838650] usb 5-4: new high speed USB device using ehci_hcd and address 19
[  144.709290] hub 5-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  144.820864] usb 5-4: new high speed USB device using ehci_hcd and address 20
[  145.691489] hub 5-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  145.803082] usb 5-4: new high speed USB device using ehci_hcd and address 21
[  146.210330] usb 5-4: device not accepting address 21, error -71
[  146.322134] usb 5-4: new high speed USB device using ehci_hcd and address 22
[  146.729387] usb 5-4: device not accepting address 22, error -71
[  146.770201] ppdev0: registered pardevice
[  146.821295] ppdev0: unregistered pardevice
[  146.973357] ppdev0: registered pardevice
[  147.024882] ppdev0: unregistered pardevice
[  388.889465] usb 5-4: new high speed USB device using ehci_hcd and address 23
[  389.760108] hub 5-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  389.871686] usb 5-4: new high speed USB device using ehci_hcd and address 24
[  390.742306] hub 5-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  390.853974] usb 5-4: new high speed USB device using ehci_hcd and address 25
[  391.261148] usb 5-4: device not accepting address 25, error -71
[  391.372948] usb 5-4: new high speed USB device using ehci_hcd and address 26
[  391.780204] usb 5-4: device not accepting address 26, error -71
jrickard@jrickard-desktop:~$ 

```

I have removed ehci_hcd using instructions here. No change.  (sudo modprobe ehci_hcd) It showed up, but no USB devices.  I added irqpoll to /boot/grub/menu.lst.  No USB.


There are literally dozens of much more confused messages on the Ubuntu forums going back nearly a year over disappearing USB ports and so forth with almost no useful answers of any kind.  The description in this thread matches my own situation most closely, and it is relatively recent by date.  But it too trails off into the ether.

Oddly, all my devices DO appear in lsusb.

```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 03f0:040c Hewlett-Packard 
Bus 004 Device 003: ID 058f:9360 Alcor Micro Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c51a Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:0b04 Logitech, Inc. 
Bus 002 Device 004: ID 046d:c713 Logitech, Inc. 
Bus 002 Device 005: ID 046d:c714 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  

```

And I DO have USB receivers for the mouse and keyboard plugged directly into the computer - and they work.  But the hub (the old hub that WAS working and quit) and the rehub (new hub just added to replace it) doesn't allow me to add the printer listed above or anything else on the hub.

Yes, it is a powered hub.  Yes, it is plugged in to AC.

This machine has been running for months successfully with these same USB devices, (although not the new hub).  It quit two weeks ago.  I think it was an update to kernel/Ubuntu that killed them.  

Does anyone have a fix????

BUMP BUMP BUMP

Jack Rickard

---

### Post by the2ndHare on 2007-10-15
I was quite desperate when the same bug occurred in my Feisty. External HDD and a DVD-writer were attached, and then suddenly stopped operating. Never were they rediscovered without unloading the ehci_hcd module, and the low speed without it rendered them pretty useless..

The solution, that seemingly worked for me (at least I`ve connected an external HDD now, and it transfers data at full speed) is adding```
irqpoll pci=routeirq
```at the end of the kernel line in the boot-options of **/boot/grub/menu.lst** .
It didn`t really work out after the first restart, but in a day or so, after a couple of power-offs, looks like everything`s back on the track.

---

