---
title: "HP Xe3-GF PCMCIA issues"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by Squider on 2007-02-11
Hello... I cannot get any pcmcia cards work on my laptop. (They did work under windows).

[FONT="Courier New"]# pccardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

# lspci -vv
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 03)
        Subsystem: Intel Corporation Unknown device 1969
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Region 0: Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 03) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 0021
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 9
        Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Region 1: Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
        Subsystem: Hewlett-Packard Company Unknown device 0021
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (2250ns max)
        Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Region 1: Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 0021
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 9
        Region 4: I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 0021
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 5
        Region 4: I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 0021
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 5
        Region 4: I/O ports at 1840 [size=32]

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=01, subordinate=09, sec-latency=64
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: e0200000-e02fffff
        Prefetchable memory behind bridge: 40000000-43ffffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 0021
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 5
        Region 0: I/O ports at <ignored>
        Region 1: I/O ports at <ignored>
        Region 2: I/O ports at <ignored>
        Region 3: I/O ports at <ignored>
        Region 4: I/O ports at 1860 [size=16]
        Region 5: Memory at e0100000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 0021
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 9
        Region 4: I/O ports at 1880 [size=32]

01:02.0 Communication controller: ESS Technology ES2838/2839 SuperLink Modem (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 0020
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 5
        Region 0: I/O ports at 2440 [size=16]
        Capabilities: <access denied>

01:03.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 0021
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (500ns min, 6000ns max)
        Interrupt: pin A routed to IRQ 5
        Region 0: I/O ports at 2000 [size=256]
        Capabilities: <access denied>

01:04.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 0021
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168
        Interrupt: pin A routed to IRQ 9
        Region 0: Memory at e0201000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 40000000-41fff000 (prefetchable)
        Memory window 1: 44000000-45fff000
        I/O window 0: 00002800-000028ff
        I/O window 1: 00002c00-00002cff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

01:04.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 0021
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168
        Interrupt: pin B routed to IRQ 9
        Region 0: Memory at e0202000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=01, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 42000000-43fff000 (prefetchable)
        Memory window 1: 46000000-47fff000
        I/O window 0: 00001400-000014ff
        I/O window 1: 00001c00-00001cff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

01:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
        Subsystem: Hewlett-Packard Company Unknown device 0021
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 66 (2000ns min, 14000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at e0200000 (32-bit, non-prefetchable) [size=4K]
        Region 1: I/O ports at 2400 [size=64]
        Capabilities: <access denied>

# dmesg
[17179570.392000] checking if image is initramfs... it is
[17179571.368000] Freeing initrd memory: 6614k freed
[17179571.368000] ACPI: Core revision 20060707
[17179571.368000] ACPI: Looking for DSDT ... not found!
[17179571.372000] ACPI: setting ELCR to 0200 (from 0620)
[17179571.380000] NET: Registered protocol family 16
[17179571.380000] EISA bus registered
[17179571.380000] ACPI: bus type pci registered
[17179571.380000] PCI: PCI BIOS revision 2.10 entry at 0xfd98a, last bus=2
[17179571.380000] PCI: Using configuration type 1
[17179571.380000] Setting up standard PCI resources
[17179571.396000] ACPI: Interpreter enabled
[17179571.396000] ACPI: Using PIC for interrupt routing
[17179571.396000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.396000] PCI: Probing PCI hardware (bus 00)
[17179571.404000] Boot video device is 0000:00:02.0
[17179571.404000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179571.404000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179571.404000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179571.404000] PCI: Transparent bridge - 0000:00:1e.0
[17179571.404000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.412000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179571.412000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[17179571.412000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[17179571.412000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[17179571.412000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[17179571.412000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[17179571.412000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179571.412000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179571.416000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179571.420000] ACPI: Embedded Controller [EC0] (gpe 28) interrupt mode.
[17179571.420000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.420000] pnp: PnP ACPI init
[17179571.428000] pnp: PnP ACPI: found 10 devices
[17179571.428000] PnPBIOS: Disabled by ACPI PNP
[17179571.428000] PCI: Using ACPI for IRQ routing
[17179571.428000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.432000] pnp: 00:01: ioport range 0x7b0-0x7bb has been reserved
[17179571.432000] pnp: 00:01: ioport range 0x7c0-0x7df has been reserved
[17179571.432000] pnp: 00:01: ioport range 0xbb0-0xbbb has been reserved
[17179571.432000] pnp: 00:01: ioport range 0xbc0-0xbdf has been reserved
[17179571.432000] pnp: 00:01: ioport range 0xfb0-0xfbb has been reserved
[17179571.432000] pnp: 00:01: ioport range 0xfc0-0xfdf has been reserved
[17179571.432000] pnp: 00:01: ioport range 0x13b0-0x13bb has been reserved
[17179571.432000] pnp: 00:01: ioport range 0x13c0-0x13df has been reserved
[17179571.432000] pnp: 00:05: ioport range 0x580-0x587 has been reserved
[17179571.432000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179571.432000] PCI: Bus 2, cardbus bridge: 0000:01:04.0
[17179571.432000]   IO window: 00002800-000028ff
[17179571.432000]   IO window: 00002c00-00002cff
[17179571.432000]   PREFETCH window: 40000000-41ffffff
[17179571.432000]   MEM window: 44000000-45ffffff
[17179571.432000] PCI: Bus 6, cardbus bridge: 0000:01:04.1
[17179571.432000]   IO window: 00001400-000014ff
[17179571.432000]   IO window: 00001c00-00001cff
[17179571.432000]   PREFETCH window: 42000000-43ffffff
[17179571.432000]   MEM window: 46000000-47ffffff
[17179571.432000] PCI: Bridge: 0000:00:1e.0
[17179571.432000]   IO window: 2000-2fff
[17179571.432000]   MEM window: e0200000-e02fffff
[17179571.432000]   PREFETCH window: 40000000-43ffffff
[17179571.432000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.432000] PCI: Enabling device 0000:01:04.0 (0081 -> 0083)
[17179571.432000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[17179571.432000] PCI: setting IRQ 9 as level-triggered
[17179571.432000] ACPI: PCI Interrupt 0000:01:04.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[17179571.432000] PCI: Enabling device 0000:01:04.1 (0081 -> 0083)
[17179571.432000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[17179571.432000] ACPI: PCI Interrupt 0000:01:04.1[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[17179571.432000] NET: Registered protocol family 2
[17179571.468000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.468000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.468000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.468000] TCP: Hash tables configured (established 131072 bind 65536)
[17179571.468000] TCP reno registered
[17179571.472000] audit: initializing netlink socket (disabled)
[17179571.472000] audit(1171191519.472:1): initialized
[17179571.472000] VFS: Disk quotas dquot_6.5.1
[17179571.472000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.472000] Initializing Cryptographic API
[17179571.472000] io scheduler noop registered
[17179571.472000] io scheduler anticipatory registered
[17179571.472000] io scheduler deadline registered
[17179571.472000] io scheduler cfq registered (default)
[17179571.472000] isapnp: Scanning for PnP cards...
[17179571.824000] isapnp: No Plug & Play device found
[17179571.868000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.868000] mice: PS/2 mouse device common for all mice
[17179571.868000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.868000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.868000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.868000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.872000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179571.876000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179571.876000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179571.876000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179571.876000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179571.876000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.876000] EISA: Probing bus 0 at eisa.0
[17179571.876000] Cannot allocate resource for EISA slot 1
[17179571.876000] Cannot allocate resource for EISA slot 2
[17179571.876000] EISA: Detected 0 cards.
[17179571.876000] TCP bic registered
[17179571.876000] NET: Registered protocol family 1
[17179571.876000] NET: Registered protocol family 8
[17179571.876000] NET: Registered protocol family 20
[17179571.876000] Using IPI Shortcut mode
[17179571.876000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.876000] Freeing unused kernel memory: 288k freed
[17179571.960000] Capability LSM initialized
[17179572.012000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179572.508000] ICH3M: IDE controller at PCI slot 0000:00:1f.1
[17179572.508000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179572.508000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[17179572.508000] PCI: setting IRQ 5 as level-triggered
[17179572.508000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[17179572.508000] ICH3M: chipset revision 1
[17179572.508000] ICH3M: not 100% native mode: will probe irqs later
[17179572.508000]     ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
[17179572.508000]     ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:DMA, hdd:pio
[17179572.508000] Probing IDE interface ide0...
[17179572.808000] hda: TOSHIBA MK2018GAP, ATA DISK drive
[17179573.096000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.480000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.920000] Probing IDE interface ide1...
[17179574.656000] hdc: HITACHI DVD-ROM GD-S250, ATAPI CD/DVD-ROM drive
[17179575.344000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.356000] hda: max request size: 128KiB
[17179575.368000] hda: 39070080 sectors (20003 MB), CHS=38760/16/63, UDMA(100)
[17179575.368000] hda: cache flushes supported
[17179575.368000]  hda: hda1 hda2 < hda5 >
[17179575.500000] hdc: ATAPI 24X DVD-ROM drive, 512kB Cache, UDMA(33)
[17179575.500000] Uniform CD-ROM driver Revision: 3.20
[17179575.872000] usbcore: registered new driver usbfs
[17179575.872000] usbcore: registered new driver hub
[17179575.876000] USB Universal Host Controller Interface driver v3.0
[17179575.876000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[17179575.876000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179575.876000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179575.880000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179575.880000] uhci_hcd 0000:00:1d.0: irq 9, io base 0x00001800
[17179575.880000] usb usb1: configuration #1 chosen from 1 choice
[17179575.880000] hub 1-0:1.0: USB hub found
[17179575.880000] hub 1-0:1.0: 2 ports detected
[17179575.984000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[17179575.984000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179575.984000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179575.984000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179575.984000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179575.984000] uhci_hcd 0000:00:1d.1: irq 5, io base 0x00001820
[17179575.984000] usb usb2: configuration #1 chosen from 1 choice
[17179575.984000] hub 2-0:1.0: USB hub found
[17179575.984000] hub 2-0:1.0: 2 ports detected
[17179576.088000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[17179576.088000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179576.088000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179576.088000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179576.088000] uhci_hcd 0000:00:1d.2: irq 5, io base 0x00001840
[17179576.088000] usb usb3: configuration #1 chosen from 1 choice
[17179576.088000] hub 3-0:1.0: USB hub found
[17179576.088000] hub 3-0:1.0: 2 ports detected
[17179576.224000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[17179576.392000] usb 1-2: configuration #1 chosen from 1 choice
[17179576.416000] usbcore: registered new driver libusual
[17179576.432000] usbcore: registered new driver hiddev
[17179576.452000] SCSI subsystem initialized
[17179576.456000] Initializing USB Mass Storage driver...
[17179576.460000] input: Western Digital External HDD as /class/input/input1
[17179576.460000] input: USB HID v1.11 Device [Western Digital External HDD] on usb-0000:00:1d.0-2
[17179576.464000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179576.464000] usb-storage: device found at 2
[17179576.464000] usb-storage: waiting for device to settle before scanning
[17179576.464000] usbcore: registered new driver usb-storage
[17179576.464000] USB Mass Storage support registered.
[17179576.464000] usbcore: registered new driver usbhid
[17179576.464000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179577.056000] kjournald starting.  Commit interval 5 seconds
[17179577.056000] EXT3-fs: mounted filesystem with ordered data mode.
[17179581.464000] usb-storage: device scan complete
[17179581.468000]   Vendor: WD        Model: 3200JS External   Rev: 106a
[17179581.468000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[17179597.348000] Linux agpgart interface v0.101 (c) Dave Jones
[17179597.356000] agpgart: Detected an Intel 830M Chipset.
[17179597.356000] agpgart: Detected 8060K stolen memory.
[17179597.368000] agpgart: AGP aperture is 128M @ 0xe8000000
[17179597.968000] Floppy drive(s): fd0 is 1.44M
[17179598.004000] FDC 0 is a National Semiconductor PC87306
[17179598.008000] Real Time Clock Driver v1.12ac
[17179598.280000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179598.472000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179598.476000] parport: PnPBIOS parport detected.
[17179598.476000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[17179598.528000] Synaptics Touchpad, model: 1, fw: 5.1, id: 0x8f40b1, caps: 0x80471b/0x0
[17179598.568000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179598.644000] hw_random: cannot enable RNG, aborting
[17179599.080000] ts: Compaq touchscreen protocol output
[17179599.360000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[17179599.364000] sda: Write Protect is off
[17179599.364000] sda: Mode Sense: 11 00 00 00
[17179599.364000] sda: assuming drive cache: write through
[17179599.372000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[17179599.376000] sda: Write Protect is off
[17179599.376000] sda: Mode Sense: 11 00 00 00
[17179599.376000] sda: assuming drive cache: write through
[17179599.376000]  sda: sda1
[17179599.384000] sd 0:0:0:0: Attached scsi disk sda
[17179599.420000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179599.492000] ACPI: PCI Interrupt 0000:01:04.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[17179599.492000] Yenta: CardBus bridge found at 0000:01:04.0 [103c:0021]
[17179599.492000] Yenta O2: res at 0x94/0xD4: ca/00
[17179599.492000] Yenta O2: enabling read prefetch/write burst
[17179599.672000] Yenta: ISA IRQ mask 0x0c18, PCI irq 9
[17179599.672000] Socket status: 30000006
[17179599.672000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[17179599.672000] cs: IO port probe 0x2000-0x2fff: clean.
[17179599.672000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[17179599.672000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[17179599.792000] ACPI: PCI Interrupt 0000:01:04.1[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[17179599.792000] Yenta: CardBus bridge found at 0000:01:04.1 [103c:0021]
[17179599.820000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179599.820000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179599.920000] Yenta: ISA IRQ mask 0x0c18, PCI irq 9
[17179599.920000] Socket status: 30000006
[17179599.920000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[17179599.920000] cs: IO port probe 0x2000-0x2fff: clean.
[17179599.920000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[17179599.920000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[17179599.948000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[17179599.948000] PCI: setting IRQ 10 as level-triggered
[17179599.948000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[17179599.972000] e100: eth0: e100_probe: addr 0xe0200000, irq 10, MAC addr 00:02:3F:31:CB:AE
[17179600.112000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179600.288000] ACPI: PCI Interrupt 0000:01:03.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179600.632000] cs: IO port probe 0x100-0x4ff: excluding 0x200-0x20f 0x4d0-0x4d7
[17179600.636000] cs: IO port probe 0xc00-0xcf7: clean.
[17179600.636000] cs: IO port probe 0xa00-0xaff: clean.
[17179600.640000] cs: IO port probe 0x100-0x4ff: excluding 0x200-0x20f 0x4d0-0x4d7
[17179600.640000] cs: IO port probe 0xc00-0xcf7: clean.
[17179600.640000] cs: IO port probe 0xa00-0xaff: clean.
[17179601.440000] lp0: using parport0 (interrupt-driven).
[17179601.596000] Adding 827308k swap on /dev/disk/by-uuid/3a25fc67-8cd5-4602-909c-c5fc63b1b498.  Priority:-1 extents:1 across:827308k
[17179601.876000] EXT3 FS on hda1, internal journal
[17179602.172000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179602.172000] md: bitmap version 4.39
[17179602.536000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [email]dm-devel@redhat.com[/email]
[17179607.448000] ACPI: AC Adapter [ACAD] (on-line)
[17179607.516000] ACPI: Battery Slot [BAT1] (battery present)
[17179607.544000] ACPI: Power Button (FF) [PWRF]
[17179607.544000] ACPI: Lid Switch [LID]
[17179607.544000] ACPI: Power Button (CM) [PWRB]
[17179607.544000] ACPI: Sleep Button (CM) [SLPB]
[17179607.756000] ibm_acpi: ec object not found
[17179607.804000] pcc_acpi: loading...
[17179607.984000] ACPI: Video Device [GRFX] (multi-head: yes  rom: no  post: no)
[17179608.436000] cpufreq: change failed with new_state 2 and result 0
[17179608.436000] cpufreq: change failed with new_state 2 and result 0
[17179610.032000] acpi_cpufreq: Unknown symbol cpu_online_map
[17179618.696000] NET: Registered protocol family 10
[17179618.696000] lo: Disabled Privacy Extensions
[17179618.696000] IPv6 over IPv4 tunneling driver
[17179619.620000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179619.620000] apm: overridden by ACPI.
[17179628.732000] eth0: no IPv6 routers present
[17179631.940000] Bluetooth: Core ver 2.8
[17179631.940000] NET: Registered protocol family 31
[17179631.940000] Bluetooth: HCI device and connection manager initialized
[17179631.940000] Bluetooth: HCI socket layer initialized
[17179631.964000] Bluetooth: L2CAP ver 2.8
[17179631.964000] Bluetooth: L2CAP socket layer initialized
[17179632.024000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179632.052000] Bluetooth: RFCOMM socket layer initialized
[17179632.052000] Bluetooth: RFCOMM TTY layer initialized
[17179632.052000] Bluetooth: RFCOMM ver 1.7
[17179632.568000] NET: Registered protocol family 17
[/FONT]

---

