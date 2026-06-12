---
title: "Toshiba Laptop problems"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by PeterWalgreens on 2007-08-25
i, everyone.

Okay, let me set everything up for all of you. I'm a mac user, who just purchaced a $399 toshiba from best buy, with hopes of learning Ubuntu and other forms of linux. I've gotten most of the things set up, but the Wifi befundles me. Same with the audio and bluetooth.

Leave this in mind, I'm used to a strictly graphic interface. No typing in a bunch o' text. I know what terminal is but barely understand it. I did predict tat you folks would need to know what happens when I type$ sudo dmesg though.

1f691fd8
[ 0.000000] ACPI: MADT (v001 PTLTD APIC 0x06040000 LTP 0x00000000) @ 0x1f691f7e
[ 0.000000] ACPI: SSDT (v001 SataRe SataPri 0x00001000 INTL 0x20050624) @ 0x1f68afe8
[ 0.000000] ACPI: SSDT (v001 SataRe SataSec 0x00001000 INTL 0x20050624) @ 0x1f68a956
[ 0.000000] ACPI: SSDT (v001 PmRef Cpu0Cst 0x00003001 INTL 0x20050624) @ 0x1f68a494
[ 0.000000] ACPI: SSDT (v001 PmRef Cpu0Tst 0x00003000 INTL 0x20050624) @ 0x1f68a235
[ 0.000000] ACPI: SSDT (v001 PmRef CpuPm 0x00003000 INTL 0x20050624) @ 0x1f689d4f
[ 0.000000] ACPI: DSDT (v001 TOSCPL CALISTGA 0x06040000 INTL 0x2006060 @ 0x00000000
[ 0.000000] ACPI: PM-Timer IO Port: 0x1008
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: 2 duplicate APIC table ignored.
[ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[ 0.000000] Processor #0 7:6 APIC version 20
[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[ 0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[ 0.000000] Detected 1596.144 MHz processor.
[ 13.245475] Built 1 zonelists. Total pages: 127635
[ 13.245480] Kernel command line: root=UUID=651d231a-7486-4805-94eb-63e8facdffe1 ro quiet splash
[ 13.245633] mapped APIC to ffffd000 (fee00000)
[ 13.245635] mapped IOAPIC to ffffc000 (fec00000)
[ 13.245638] Enabling fast FPU save and restore... done.
[ 13.245641] Enabling unmasked SIMD FPU exception support... done.
[ 13.245650] Initializing CPU#0
[ 13.245725] PID hash table entries: 2048 (order: 11, 8192 bytes)
[ 13.247587] Console: colour VGA+ 80x25
[ 13.247761] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 13.247927] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 13.258274] Memory: 498880k/514560k available (1992k kernel code, 15128k reserved, 893k data, 328k init, 0k highmem)
[ 13.258283] virtual kernel memory layout:
[ 13.258284] fixmap : 0xfff4e000 - 0xfffff000 ( 708 kB)
[ 13.258285] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 13.258286] vmalloc : 0xe0000000 - 0xff7fe000 ( 503 MB)
[ 13.258287] lowmem : 0xc0000000 - 0xdf680000 ( 502 MB)
[ 13.258288] .init : 0xc03d7000 - 0xc0429000 ( 328 kB)
[ 13.258290] .data : 0xc02f2264 - 0xc03d16d4 ( 893 kB)
[ 13.258291] .text : 0xc0100000 - 0xc02f2264 (1992 kB)
[ 13.258294] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 13.258462] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[ 13.258467] hpet0: 3 64-bit timers, 14318180 Hz
[ 13.259473] Using HPET for base-timer
[ 13.338391] Calibrating delay using timer specific routine.. 3195.81 BogoMIPS (lpj=6391620)
[ 13.338431] Security Framework v1.0.0 initialized
[ 13.338436] SELinux: Disabled at boot.
[ 13.338452] Mount-cache hash table entries: 512
[ 13.338578] CPU: After generic identify, caps: afebfbff 20000000 00000000 00000000 0000e31d 00000000 00000001
[ 13.338586] monitor/mwait feature present.
[ 13.338587] using mwait in idle threads.
[ 13.338591] CPU: L1 I cache: 32K, L1 D cache: 32K
[ 13.338594] CPU: L2 cache: 1024K
[ 13.338597] CPU: After all inits, caps: afebfbff 20000000 00000000 00003940 0000e31d 00000000 00000001
[ 13.338607] Compat vDSO mapped to ffffe000.
[ 13.338610] Remapping vsyscall page to ffffe000
[ 13.338621] Checking 'hlt' instruction... OK.
[ 13.354475] SMP alternatives: switching to UP code
[ 13.354652] Freeing SMP alternatives: 11k freed
[ 13.354828] Early unpacking initramfs... done
[ 13.698424] ACPI: Core revision 20060707
[ 13.698742] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[ 13.725647] CPU0: Intel(R) Celeron(R) M CPU 520 @ 1.60GHz stepping 01
[ 13.725675] Total of 1 processors activated (3195.81 BogoMIPS).
[ 13.725873] ENABLING IO-APIC IRQs
[ 13.726089] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 13.869922] Brought up 1 CPUs
[ 13.870153] Booting paravirtualized kernel on bare hardware
[ 13.870247] Time: 14:21:34 Date: 07/25/107
[ 13.870273] NET: Registered protocol family 16
[ 13.870355] EISA bus registered
[ 13.870359] ACPI: bus type pci registered
[ 13.870448] PCI: BIOS BUG #81[49435000] found
[ 13.870506] PCI: Using configuration type 1
[ 13.870508] Setting up standard PCI resources
[ 13.881842] ACPI: Interpreter enabled
[ 13.881845] ACPI: Using IOAPIC for interrupt routing
[ 13.882314] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 13.882319] PCI: Probing PCI hardware (bus 00)
[ 13.883068] Boot video device is 0000:00:02.0
[ 13.883762] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[ 13.883767] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[ 13.884801] PCI: Transparent bridge - 0000:00:1e.0
[ 13.884873] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#06) (try 'pci=assign-busses')
[ 13.884876] Please report the result to linux-kernel to fix this permanently
[ 13.884946] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 13.892403] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[ 13.892657] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[ 13.892998] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[ 13.893837] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[ 13.894498] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[ 13.894743] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[ 13.894987] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[ 13.895239] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[ 13.895481] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[ 13.895724] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[ 13.895967] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[ 13.896213] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[ 13.942483] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 13.942495] pnp: PnP ACPI init
[ 13.969970] pnp: PnP ACPI: found 10 devices
[ 13.969974] PnPBIOS: Disabled by ACPI PNP
[ 13.970017] PCI: Using ACPI for IRQ routing
[ 13.970020] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report
[ 13.970132] NET: Registered protocol family 8
[ 13.970134] NET: Registered protocol family 20
[ 13.970375] pnp: 00:01: ioport range 0xfe00-0xfe7f has been reserved
[ 13.970379] pnp: 00:01: ioport range 0xfe80-0xfeff has been reserved
[ 13.970381] pnp: 00:01: ioport range 0xff00-0xff7f has been reserved
[ 13.970651] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[ 13.970657] PCI: Bridge: 0000:00:1c.0
[ 13.970661] IO window: 2000-2fff
[ 13.970667] MEM window: d6000000-d7ffffff
[ 13.970672] PREFETCH window: d0000000-d1ffffff
[ 13.970678] PCI: Bridge: 0000:00:1c.1
[ 13.970682] IO window: 3000-3fff
[ 13.970688] MEM window: d8000000-d9ffffff
[ 13.970693] PREFETCH window: d2000000-d3ffffff
[ 13.970700] PCI: Bridge: 0000:00:1c.2
[ 13.970703] IO window: 4000-4fff
[ 13.970709] MEM window: da000000-dbffffff
[ 13.970714] PREFETCH window: d4000000-d5ffffff
[ 13.970726] PCI: Bus 7, cardbus bridge: 0000:06:04.0
[ 13.970728] IO window: 00005000-000050ff
[ 13.970734] IO window: 00005400-000054ff
[ 13.970739] PREFETCH window: 30000000-33ffffff
[ 13.970745] MEM window: 34000000-37ffffff
[ 13.970750] PCI: Bridge: 0000:00:1e.0
[ 13.970753] IO window: 5000-5fff
[ 13.970759] MEM window: dc000000-dc0fffff
[ 13.970764] PREFETCH window: 30000000-33ffffff
[ 13.970799] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[ 13.970806] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[ 13.970832] ACPI: PCI Interrupt 0000:00:1c.1[b] -> GSI 16 (level, low) -> IRQ 17
[ 13.970838] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[ 13.970863] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[ 13.970869] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[ 13.970884] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[ 13.970901] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 16 (level, low) -> IRQ 17
[ 13.970926] NET: Registered protocol family 2
[ 14.005819] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[ 14.005891] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[ 14.005959] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[ 14.005991] TCP: Hash tables configured (established 16384 bind 8192)
[ 14.005994] TCP reno registered
[ 14.017852] checking if image is initramfs... it is
[ 14.690152] Freeing initrd memory: 7006k freed
[ 14.690364] Simple Boot Flag at 0x36 set to 0x1
[ 14.690668] audit: initializing netlink socket (disabled)
[ 14.690683] audit(1188051694.496:1): initialized
[ 14.690794] VFS: Disk quotas dquot_6.5.1
[ 14.690810] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 14.690855] io scheduler noop registered
[ 14.690858] io scheduler anticipatory registered
[ 14.690860] io scheduler deadline registered
[ 14.690867] io scheduler cfq registered (default)
[ 14.691112] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[ 14.691174] assign_interrupt_mode Found MSI capability
[ 14.691177] Allocate Port Service[0000:00:1c.0cie00]
[ 14.691208] Allocate Port Service[0000:00:1c.0cie02]
[ 14.691336] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[ 14.691397] assign_interrupt_mode Found MSI capability
[ 14.691399] Allocate Port Service[0000:00:1c.1cie00]
[ 14.691428] Allocate Port Service[0000:00:1c.1cie02]
[ 14.691554] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[ 14.691615] assign_interrupt_mode Found MSI capability
[ 14.691617] Allocate Port Service[0000:00:1c.2cie00]
[ 14.691646] Allocate Port Service[0000:00:1c.2cie02]
[ 14.691818] isapnp: Scanning for PnP cards...
[ 15.045820] isapnp: No Plug & Play device found
[ 15.067061] Real Time Clock Driver v1.12ac
[ 15.067127] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 15.067782] mice: PS/2 mouse device common for all mice
[ 15.068286] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 15.068490] input: Macintosh mouse button emulation as /class/input/input0
[ 15.068522] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 15.068525] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 15.068845] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[ 15.069927] i8042.c: Detected active multiplexing controller, rev 1.1.
[ 15.070009] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 15.070014] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[ 15.070016] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[ 15.070019] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[ 15.070021] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[ 15.070154] EISA: Probing bus 0 at eisa.0
[ 15.070163] Cannot allocate resource for EISA slot 1
[ 15.070165] Cannot allocate resource for EISA slot 2
[ 15.070168] Cannot allocate resource for EISA slot 3
[ 15.070170] Cannot allocate resource for EISA slot 4
[ 15.070172] Cannot allocate resource for EISA slot 5
[ 15.070186] EISA: Detected 0 cards.
[ 15.100257] TCP cubic registered
[ 15.100264] NET: Registered protocol family 1
[ 15.100283] Using IPI No-Shortcut mode
[ 15.100344] ACPI: (supports S0 S3 S4 S5)
[ 15.100391] Magic number: 3:199:385
[ 15.100648] Freeing unused kernel memory: 328k freed
[ 15.100736] Time: tsc clocksource has been installed.
[ 15.102243] input: AT Translated Set 2 keyboard as /class/input/input1
[ 16.312968] Capability LSM initialized
[ 16.347029] Monitor-Mwait will be used to enter C-1 state
[ 16.347034] Monitor-Mwait will be used to enter C-2 state
[ 16.347036] Monitor-Mwait will be used to enter C-3 state
[ 16.347040] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[ 16.347049] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[ 16.738943] usbcore: registered new interface driver usbfs
[ 16.738965] usbcore: registered new interface driver hub
[ 16.738986] usbcore: registered new device driver usb
[ 16.739793] USB Universal Host Controller Interface driver v3.0
[ 16.739840] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[ 16.739851] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[ 16.739855] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 16.739983] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[ 16.740019] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[ 16.740111] usb usb1: configuration #1 chosen from 1 choice
[ 16.740133] hub 1-0:1.0: USB hub found
[ 16.740138] hub 1-0:1.0: 2 ports detected
[ 16.819741] ieee1394: Initialized config rom entry `ip1394'
[ 16.843247] ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 19 (level, low) -> IRQ 20
[ 16.843259] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[ 16.843263] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 16.843283] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[ 16.843319] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[ 16.843403] usb usb2: configuration #1 chosen from 1 choice
[ 16.843431] hub 2-0:1.0: USB hub found
[ 16.843437] hub 2-0:1.0: 2 ports detected
[ 16.889762] SCSI subsystem initialized
[ 16.894799] libata version 2.20 loaded.
[ 16.947149] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[ 16.947161] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[ 16.947165] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 16.947186] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[ 16.947221] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[ 16.947305] usb usb3: configuration #1 chosen from 1 choice
[ 16.947331] hub 3-0:1.0: USB hub found
[ 16.947336] hub 3-0:1.0: 2 ports detected
[ 3.668000] Time: hpet clocksource has been installed.
[ 3.676000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[ 3.676000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[ 3.676000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[ 3.676000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[ 3.676000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[ 3.676000] usb usb4: configuration #1 chosen from 1 choice
[ 3.676000] hub 4-0:1.0: USB hub found
[ 3.676000] hub 4-0:1.0: 2 ports detected
[ 3.780000] r8169 Gigabit Ethernet driver 2.2LK loaded
[ 3.780000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[ 3.780000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[ 3.780000] eth0: RTL8101e at 0xe00bc000, 00:1b:38:3f:bb:53, IRQ 18
[ 3.788000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[ 3.788000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[ 3.788000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 3.788000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[ 3.788000] ehci_hcd 0000:00:1d.7: debug port 1
[ 3.788000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[ 3.788000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xdc444000
[ 3.792000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 3.792000] usb usb5: configuration #1 chosen from 1 choice
[ 3.792000] hub 5-0:1.0: USB hub found
[ 3.792000] hub 5-0:1.0: 8 ports detected
[ 3.896000] ACPI: PCI Interrupt 0000:06:04.1[b] -> GSI 17 (level, low) -> IRQ 16
[ 3.944000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16] MMIO=[dc005000-dc0057ff] Max Packet=[2048] IR/IT contexts=[4/8]
[ 3.944000] ata_piix 0000:00:1f.2: version 2.10ac1
[ 3.944000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[ 4.100000] ACPI: PCI Interrupt 0000:00:1f.2[b] -> GSI 19 (level, low) -> IRQ 20
[ 4.100000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[ 4.100000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[ 4.100000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
[ 4.100000] scsi0 : ata_piix
[ 4.264000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[ 4.264000] ata1.00: ATA-7: Hitachi HTS541680J9SA00, SB2OC7DP, max UDMA/100
[ 4.264000] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[ 4.272000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[ 4.272000] ata1.00: configured for UDMA/100
[ 4.272000] scsi1 : ata_piix
[ 4.608000] ata2.00: ATAPI, max UDMA/33
[ 4.788000] ata2.00: configured for UDMA/33
[ 4.788000] scsi 0:0:0:0: Direct-Access ATA Hitachi HTS54168 SB2O PQ: 0 ANSI: 5
[ 4.804000] scsi 1:0:0:0: CD-ROM TSSTcorp CD/DVDW TS-L632D TO03 PQ: 0 ANSI: 5
[ 4.836000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[ 4.836000] sda: Write Protect is off
[ 4.836000] sda: Mode Sense: 00 3a 00 00
[ 4.840000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4.840000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[ 4.840000] sda: Write Protect is off
[ 4.840000] sda: Mode Sense: 00 3a 00 00
[ 4.840000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4.840000] sda: sda1 sda2 < sda5 >
[ 4.888000] sd 0:0:0:0: Attached scsi disk sda
[ 4.896000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 4.896000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[ 4.988000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[ 4.988000] Uniform CD-ROM driver Revision: 3.20
[ 4.988000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 5.188000] Attempting manual resume
[ 5.188000] swsusp: Resume From Partition 8:5
[ 5.188000] PM: Checking swsusp image.
[ 5.188000] PM: Resume from disk failed.
[ 5.216000] ieee1394: Host added: ID:BUS[0-00:1023] GUID[00023f78a840056a]
[ 5.244000] kjournald starting. Commit interval 5 seconds
[ 5.244000] EXT3-fs: mounted filesystem with ordered data mode.
[ 5.276000] irq 16: nobody cared (try booting with the "irqpoll" option)
[ 5.276000] [<c0154394>] __report_bad_irq+0x24/0x80
[ 5.276000] [<c0105b75>] do_IRQ+0x45/0x80
[ 5.276000] [<c015464e>] note_interrupt+0x25e/0x290
[ 5.276000] [<c01538c0>] handle_IRQ_event+0x30/0x60
[ 5.276000] [<c0154f81>] handle_fasteoi_irq+0xc1/0xf0
[ 5.276000] [<c0105b70>] do_IRQ+0x40/0x80
[ 5.276000] [<e00cb3f8>] ohci_irq_handler+0x48/0x990 [ohci1394]
[ 5.276000] [<c0104233>] common_interrupt+0x23/0x30
[ 5.276000] [<c02f06b9>] do_page_fault+0x349/0x5f0
[ 5.276000] [<c01173a0>] ack_ioapic_quirk_irq+0x40/0xa0
[ 5.276000] [<c02f0370>] do_page_fault+0x0/0x5f0
[ 5.276000] [<c02eeb4c>] error_code+0x7c/0x90
[ 5.276000] =======================
[ 5.276000] handlers:
[ 5.276000] [<e00cb3b0>] (ohci_irq_handler+0x0/0x990 [ohci1394])
[ 5.276000] Disabling IRQ #16
[ 13.924000] r8169: eth0: link down
[ 15.248000] NET: Registered protocol family 17
[ 15.452000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 15.452000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 15.468000] iTCO_vendor_support: vendor-support=0
[ 15.468000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[ 15.468000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[ 15.468000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[ 15.500000] intel_rng: FWH not detected
[ 15.680000] Linux agpgart interface v0.102 (c) Dave Jones
[ 15.692000] agpgart: Detected an Intel 945GM Chipset.
[ 15.692000] agpgart: Detected 7932K stolen memory.
[ 15.708000] agpgart: AGP aperture is 256M @ 0xc0000000
[ 16.160000] ath_hal: module license 'Proprietary' taints kernel.
[ 16.164000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[ 16.208000] ACPI: PCI Interrupt 0000:06:04.2[C] -> GSI 18 (level, low) -> IRQ 18
[ 16.308000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[ 16.308000] synaptics: Toshiba Satellite A135 detected, limiting rate to 40pps.
[ 16.316000] wlan: 0.8.4.2 (0.9.3)
[ 16.336000] ath_pci: 0.9.4.5 (0.9.3)
[ 16.336000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[ 16.336000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[ 16.840000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[ 16.896000] ath_rate_sample: 1.2 (0.9.3)
[ 16.896000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[ 16.896000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[ 16.896000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[ 16.896000] wifi0: mac 10.0 phy 6.1 radio 10.2
[ 16.896000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[ 16.896000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[ 16.896000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[ 16.896000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[ 16.896000] wifi0: Use hw queue 8 for CAB traffic
[ 16.896000] wifi0: Use hw queue 9 for beacons
[ 16.908000] sdhci: Secure Digital Host Controller Interface driver
[ 16.908000] sdhci: Copyright(c) Pierre Ossman
[ 16.944000] wifi0: Atheros 5424/2424: mem=0xd8000000, irq=16
[ 16.944000] Yenta: CardBus bridge found at 0000:06:04.0 [1179:ff00]
[ 16.944000] Yenta: Enabling burst memory read transactions
[ 16.944000] Yenta: Using CSCINT to route CSC interrupts to PCI
[ 16.944000] Yenta: Routing CardBus interrupts to PCI
[ 16.944000] Yenta TI: socket 0000:06:04.0, mfunc 0x10aa1b22, devctl 0x64
[ 17.176000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[ 17.176000] Socket status: 30000006
[ 17.176000] Yenta: Raising subordinate bus# of parent bus (#06) from #06 to #0a
[ 17.176000] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[ 17.176000] cs: IO port probe 0x5000-0x5fff: clean.
[ 17.176000] pcmcia: parent PCI bridge Memory window: 0xdc000000 - 0xdc0fffff
[ 17.176000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[ 17.180000] sdhci: SDHCI controller found at 0000:06:04.3 [104c:803c] (rev 0)
[ 17.180000] ACPI: PCI Interrupt 0000:06:04.3[D] -> GSI 19 (level, low) -> IRQ 20
[ 17.180000] mmc0: SDHCI at 0xdc005800 irq 20 DMA
[ 17.188000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[ 17.188000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[ 17.400000] hda_codec: Unknown model for ALC660VD/ALC861VD, trying auto-probe from BIOS...
[ 17.536000] cs: IO port probe 0x100-0x3af: clean.
[ 17.536000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[ 17.536000] cs: IO port probe 0x820-0x8ff: clean.
[ 17.536000] cs: IO port probe 0xc00-0xcf7: clean.
[ 17.540000] cs: IO port probe 0xa00-0xaff: clean.
[ 18.160000] si3054: cannot initialize. EXT MID = 0000
[ 18.348000] fuse init (API version 7.
[ 18.440000] lp: driver loaded but no devices found
[ 18.520000] Adding 1477940k swap on /dev/disk/by-uuid/e8dcbf6b-2b74-43f8-a6b9-6dd9ed509987. Priority:-1 extents:1 across:1477940k
[ 18.664000] EXT3 FS on sda1, internal journal
[ 22.804000] input: Power Button (FF) as /class/input/input3
[ 22.808000] ACPI: Power Button (FF) [PWRF]
[ 22.836000] input: Lid Switch as /class/input/input4
[ 22.840000] ACPI: Lid Switch [LID0]
[ 22.868000] input: Power Button (CM) as /class/input/input5
[ 22.872000] ACPI: Power Button (CM) [PWRB]
[ 22.880000] No dock devices found.
[ 22.908000] ibm_acpi: ec object not found
[ 22.996000] ACPI: Battery Slot [BAT1] (battery present)
[ 23.036000] ACPI: Video Device [VGA] (multi-head: yes rom: no post: no)
[ 23.036000] ACPI: Video Device [GFX0] (multi-head: yes rom: no post: no)
[ 23.052000] Using specific hotkey driver
[ 23.112000] ACPI: AC Adapter [ACAD] (on-line)
[ 23.136000] pcc_acpi: loading...
[ 27.660000] [drm] Initialized drm 1.1.0 20060810
[ 27.664000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[ 27.668000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[ 28.508000] ppdev: user-space parallel port driver
[ 29.144000] apm: BIOS not found.
[ 29.312000] Bluetooth: Core ver 2.11
[ 29.312000] NET: Registered protocol family 31
[ 29.312000] Bluetooth: HCI device and connection manager initialized
[ 29.312000] Bluetooth: HCI socket layer initialized
[ 29.344000] Bluetooth: L2CAP ver 2.8
[ 29.344000] Bluetooth: L2CAP socket layer initialized
[ 29.492000] Bluetooth: RFCOMM socket layer initialized
[ 29.492000] Bluetooth: RFCOMM TTY layer initialized
[ 29.492000] Bluetooth: RFCOMM ver 1.8
[ 55.800000] NET: Registered protocol family 10
[ 55.800000] lo: Disabled Privacy Extensions
[ 55.800000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 66.756000] ath0: no IPv6 routers present
[ 260.380000] ath0: no IPv6 routers present
[ 276.248000] r8169: eth0: link down
[ 276.248000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 286.360000] ath0: no IPv6 routers present
[ 631.616000] r8169: eth0: link up
[ 631.616000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 645.628000] eth0: no IPv6 routers present
walgreens@Skynet-Tuxbox:~$
__________________

---

### Post by loza on 2007-08-25
Hello

What Tosh are you using? I'm running on a Satellite Pro L10 with sound working.

loza

---

### Post by PeterWalgreens on 2007-08-25
Toshiba Satellite A135-S4656

Or, the "cheapest laptop at best buy"

It's a bummer, really, becuse everything else in ubuntu is running so well...

---

### Post by PeterWalgreens on 2007-08-25
Here's whats inside!

walgreens@Skynet-Tuxbox:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
walgreens@Skynet-Tuxbox:~$

---

### Post by SilverDragonStar on 2007-08-25
I bought the same laptop with the same problem with the sound. The wifi is working perfectly and I would be absolutely thrilled with the system if I could only get the sound to work.

---

### Post by PeterWalgreens on 2007-08-25
> **SilverDragonStar said:**
> I bought the same laptop with the same problem with the sound. The wifi is working perfectly and I would be absolutely thrilled with the system if I could only get the sound to work.

How did you set up the wifi? I'm used to Mac/windows systems.

---

### Post by PeterWalgreens on 2007-08-25
Ok, Got the Wifi working. Just needed a special app...

---

### Post by SilverDragonStar on 2007-08-26
Have you figured out how to fix the sound issue yet? I read some posts where the headphones work but the speakers don't. I didn't even get that. Everything seems to be working correctly but no sound comes out.

---

### Post by PeterWalgreens on 2007-08-26
> **SilverDragonStar said:**
> Have you figured out how to fix the sound issue yet? I read some posts where the headphones work but the speakers don't. I didn't even get that. Everything seems to be working correctly but no sound comes out.

Watch this post-
[http://ubuntuforums.org/showthread.php?t=535001](http://ubuntuforums.org/showthread.php?t=535001)

---

### Post by loza on 2007-08-26
Have a look at this...


[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/85869](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/85869)

---

