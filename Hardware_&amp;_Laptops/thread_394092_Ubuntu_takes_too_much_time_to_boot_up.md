---
title: "Ubuntu takes too much time to boot up"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by octavio on 2007-03-26
Hi, since i instaled ubuntu 6.10 on my toshiba laptop, i have noticed that it takes a lot of time when it boot up.

I am really upset about this boot time. But i can't determine why it takes so much time.

In fact it takes about 4 minutes until i get this message:
```

[17179771.828000] atiixp: codec reset timeout

```

Then it loads in a few seconds the login screen.

This is my dmesg output, if anybody may help me will be great. 

Thank you very much.

```

[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001bff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001bff0000 - 000000001bffffc0 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001bffffc0 - 000000001c000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 447MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 114672
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 110576 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 OID_00                                ) @ 0x000e6010
[17179569.184000] ACPI: RSDT (v001 INSYDE RSDT_000 0x00000001 _CSI 0x00010101) @ 0x1bffb1f6
[17179569.184000] ACPI: FADT (v001 INSYDE FACP_000 0x00000100 _CSI 0x00010101) @ 0x1bfffa90
[17179569.184000] ACPI: MADT (v001 INSYDE APIC_000 0x30303030 0000 0x30303030) @ 0x1bfffb20
[17179569.184000] ACPI: BOOT (v001 INSYDE SYS_BOOT 0x00000100 _CSI 0x00010101) @ 0x1bfffb90
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030522) @ 0x1bffb58b
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030522) @ 0x1bffb40d
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030522) @ 0x1bffb232
[17179569.184000] ACPI: DSDT (v001 TOSINV   Avani2 0x00001004 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e3f80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash locale=es_ES
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 2800.580 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.544000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.544000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.556000] Memory: 444768k/458688k available (1911k kernel code, 13400k reserved, 1073k data, 308k init, 0k highmem)
[17179569.556000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.636000] Calibrating delay using timer specific routine.. 5604.47 BogoMIPS (lpj=11208954)
[17179569.636000] Security Framework v1.0.0 initialized
[17179569.636000] SELinux:  Disabled at boot.
[17179569.636000] Mount-cache hash table entries: 512
[17179569.636000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179569.636000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179569.636000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179569.636000] CPU: L2 cache: 512K
[17179569.636000] CPU: Hyper-Threading is disabled
[17179569.636000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[17179569.636000] Checking 'hlt' instruction... OK.
[17179569.652000] SMP alternatives: switching to UP code
[17179569.652000] Freeing SMP alternatives: 16k freed
[17179569.652000] checking if image is initramfs... it is
[17179570.140000] Freeing initrd memory: 5624k freed
[17179570.140000] ACPI: Core revision 20060707
[17179570.140000] ACPI: Looking for DSDT ... not found!
[17179570.184000] CPU0: Intel Mobile Intel(R) Pentium(R) 4     CPU 2.80GHz stepping 09
[17179570.184000] Total of 1 processors activated (5604.47 BogoMIPS).
[17179570.184000] ENABLING IO-APIC IRQs
[17179570.184000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.184000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[17179570.184000] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[17179570.184000] ...trying to set up timer as Virtual Wire IRQ... works.
[17179570.368000] Brought up 1 CPUs
[17179570.368000] migration_cost=0
[17179570.368000] NET: Registered protocol family 16
[17179570.368000] EISA bus registered
[17179570.368000] ACPI: bus type pci registered
[17179570.368000] PCI: PCI BIOS revision 2.10 entry at 0xe9964, last bus=2
[17179570.368000] PCI: Using configuration type 1
[17179570.368000] Setting up standard PCI resources
[17179570.380000] ACPI: Interpreter enabled
[17179570.380000] ACPI: Using IOAPIC for interrupt routing
[17179570.384000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.384000] PCI: Probing PCI hardware (bus 00)
[17179570.384000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.384000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[17179570.384000] Boot video device is 0000:01:05.0
[17179570.384000] PCI: Transparent bridge - 0000:00:14.4
[17179570.384000] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[17179570.384000] Please report the result to linux-kernel to fix this permanently
[17179570.384000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.384000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179570.388000] ACPI: PCI Interrupt Link [LNK0] (IRQs 5 7 10 *11)
[17179570.388000] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 *10 11)
[17179570.388000] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 *11)
[17179570.388000] ACPI: PCI Interrupt Link [LNK3] (IRQs *5 7 10 11)
[17179570.388000] ACPI: Embedded Controller [EC0] (gpe 7) interrupt mode.
[17179570.400000] ACPI: Power Resource [PUT2] (on)
[17179570.400000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[17179570.400000] ACPI: Power Resource [PFA1] (off)
[17179570.400000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.400000] pnp: PnP ACPI init
[17179570.404000] pnp: PnP ACPI: found 11 devices
[17179570.404000] PnPBIOS: Disabled by ACPI PNP
[17179570.404000] PCI: Using ACPI for IRQ routing
[17179570.404000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.408000] pnp: 00:07: ioport range 0x280-0x29f has been reserved
[17179570.408000] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
[17179570.408000] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[17179570.408000] PCI: Bridge: 0000:00:01.0
[17179570.408000]   IO window: c000-dfff
[17179570.408000]   MEM window: e0000000-efffffff
[17179570.408000]   PREFETCH window: a0000000-afffffff
[17179570.408000] PCI: Bus 3, cardbus bridge: 0000:02:06.0
[17179570.408000]   IO window: 0000a400-0000a4ff
[17179570.408000]   IO window: 0000a800-0000a8ff
[17179570.408000]   PREFETCH window: 90000000-91ffffff
[17179570.408000]   MEM window: d2000000-d3ffffff
[17179570.408000] PCI: Bridge: 0000:00:14.4
[17179570.408000]   IO window: a000-bfff
[17179570.408000]   MEM window: d0000000-dfffffff
[17179570.408000]   PREFETCH window: 90000000-9fffffff
[17179570.408000] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179570.408000] NET: Registered protocol family 2
[17179570.440000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.440000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179570.440000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179570.440000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.440000] TCP reno registered
[17179570.440000] Simple Boot Flag at 0x37 set to 0x1
[17179570.440000] audit: initializing netlink socket (disabled)
[17179570.440000] audit(1174904622.440:1): initialized
[17179570.440000] VFS: Disk quotas dquot_6.5.1
[17179570.440000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.440000] Initializing Cryptographic API
[17179570.440000] io scheduler noop registered
[17179570.440000] io scheduler anticipatory registered
[17179570.440000] io scheduler deadline registered
[17179570.440000] io scheduler cfq registered (default)
[17179570.440000] isapnp: Scanning for PnP cards...
[17179570.792000] isapnp: No Plug & Play device found
[17179570.820000] Real Time Clock Driver v1.12ac
[17179570.820000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.820000] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[17179570.820000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 185
[17179570.820000] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[17179570.820000] mice: PS/2 mouse device common for all mice
[17179570.820000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.820000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.820000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.820000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179570.824000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.824000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.824000] EISA: Probing bus 0 at eisa.0
[17179570.824000] Cannot allocate resource for EISA slot 4
[17179570.824000] Cannot allocate resource for EISA slot 8
[17179570.824000] EISA: Detected 0 cards.
[17179570.824000] TCP bic registered
[17179570.824000] NET: Registered protocol family 1
[17179570.824000] NET: Registered protocol family 8
[17179570.824000] NET: Registered protocol family 20
[17179570.824000] Using IPI No-Shortcut mode
[17179570.824000] ACPI: (supports S0 S3 S4 S5)
[17179570.824000] Freeing unused kernel memory: 308k freed
[17179570.892000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.052000] Capability LSM initialized
[17179572.484000] ACPI: Transitioning device [FAN1] to D3
[17179572.484000] ACPI: Transitioning device [FAN1] to D3
[17179572.484000] ACPI: Fan [FAN1] (off)
[17179572.488000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179572.488000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179572.488000] ACPI: Getting cpuindex for acpiid 0x1
[17179572.840000] ACPI: Thermal Zone [THZN] (47 C)
[17179573.560000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[17179573.560000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 193
[17179573.560000] ATIIXP: chipset revision 0
[17179573.560000] ATIIXP: not 100% native mode: will probe irqs later
[17179573.560000]     ide0: BM-DMA at 0x8070-0x8077, BIOS settings: hda:DMA, hdb:pio
[17179573.560000]     ide1: BM-DMA at 0x8078-0x807f, BIOS settings: hdc:DMA, hdd:pio
[17179573.560000] Probing IDE interface ide0...
[17179573.852000] hda: IC25N040ATMR04-0, ATA DISK drive
[17179574.528000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.548000] Probing IDE interface ide1...
[17179575.288000] hdc: TOSHIBA DVD-ROM SD-R6112, ATAPI CD/DVD-ROM drive
[17179576.012000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.032000] hda: max request size: 512KiB
[17179576.044000] hda: 78140160 sectors (40007 MB) w/1740KiB Cache, CHS=16383/255/63, UDMA(100)
[17179576.044000] hda: cache flushes supported
[17179576.044000]  hda: hda1 hda2 < hda5 > hda3
[17179576.144000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179576.144000] Uniform CD-ROM driver Revision: 3.20
[17179579.188000] usbcore: registered new driver usbfs
[17179579.188000] usbcore: registered new driver hub
[17179579.188000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179579.188000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179579.188000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[17179579.192000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[17179579.192000] ohci_hcd 0000:00:13.0: irq 177, io mem 0xf0001000
[17179579.256000] usb usb1: configuration #1 chosen from 1 choice
[17179579.256000] hub 1-0:1.0: USB hub found
[17179579.256000] hub 1-0:1.0: 3 ports detected
[17179579.256000] ieee1394: Initialized config rom entry `ip1394'
[17179579.364000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 177
[17179579.364000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[17179579.364000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[17179579.364000] ohci_hcd 0000:00:13.1: irq 177, io mem 0xf0002000
[17179579.428000] usb usb2: configuration #1 chosen from 1 choice
[17179579.428000] hub 2-0:1.0: USB hub found
[17179579.428000] hub 2-0:1.0: 3 ports detected
[17179579.536000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 177
[17179579.536000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[17179579.536000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[17179579.536000] ehci_hcd 0000:00:13.2: irq 177, io mem 0xf0003000
[17179579.536000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.536000] usb usb3: configuration #1 chosen from 1 choice
[17179579.536000] hub 3-0:1.0: USB hub found
[17179579.536000] hub 3-0:1.0: 6 ports detected
[17179579.644000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179579.692000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[177]  MMIO=[d0000000-d00007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179579.828000] Attempting manual resume
[17179579.976000] ohci_hcd 0000:00:13.0: wakeup
[17179580.000000] kjournald starting.  Commit interval 5 seconds
[17179580.000000] EXT3-fs: mounted filesystem with ordered data mode.
[17179580.360000] usb 1-2: new low speed USB device using ohci_hcd and address 3
[17179580.564000] usb 1-2: configuration #1 chosen from 1 choice
[17179580.972000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00080da0d1dda34f]
[17179770.920000] input: PC Speaker as /class/input/input1
[17179770.956000] Linux agpgart interface v0.101 (c) Dave Jones
[17179770.960000] agpgart: Detected Ati IGP7000/M chipset
[17179770.968000] agpgart: AGP aperture is 64M @ 0xb0000000
[17179771.104000] 8139too Fast Ethernet driver 0.9.27
[17179771.104000] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 18 (level, low) -> IRQ 201
[17179771.104000] eth0: RealTek RTL8139 at 0xdc9ea000, 00:a0:d1:dd:a3:4f, IRQ 201
[17179771.104000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179771.116000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179771.136000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179771.188000] irda_init()
[17179771.188000] NET: Registered protocol family 23
[17179771.220000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179771.292000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179771.304000] parport: PnPBIOS parport detected.
[17179771.304000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179771.412000] usbcore: registered new driver hiddev
[17179771.416000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[17179771.416000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-2
[17179771.416000] usbcore: registered new driver usbhid
[17179771.416000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179771.576000] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179771.576000] Yenta: CardBus bridge found at 0000:02:06.0 [1179:ff10]
[17179771.576000] Yenta: Enabling burst memory read transactions
[17179771.576000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179771.576000] Yenta: Routing CardBus interrupts to PCI
[17179771.576000] Yenta TI: socket 0000:02:06.0, mfunc 0x01111122, devctl 0x64
[17179771.624000] NET: Registered protocol family 10
[17179771.624000] lo: Disabled Privacy Extensions
[17179771.624000] IPv6 over IPv4 tunneling driver
[17179771.712000] ts: Compaq touchscreen protocol output
[17179771.808000] Yenta: ISA IRQ mask 0x0c78, PCI irq 177
[17179771.808000] Socket status: 30000006
[17179771.808000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[17179771.808000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xbfff
[17179771.808000] cs: IO port probe 0xa000-0xbfff: clean.
[17179771.808000] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xdfffffff
[17179771.808000] pcmcia: parent PCI bridge Memory window: 0x90000000 - 0x9fffffff
[17179771.828000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 185
[17179771.828000] atiixp: codec reset timeout
[17179772.212000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa56eb1, caps: 0x804713/0x0
[17179772.212000] synaptics: Toshiba Satellite A60 detected, limiting rate to 40pps.
[17179772.264000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[17179772.336000] cs: IO port probe 0x100-0x3af: excluding 0x220-0x227 0x300-0x307 0x310-0x317
[17179772.336000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179772.336000] cs: IO port probe 0x820-0x8ff: clean.
[17179772.336000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcd7
[17179772.336000] cs: IO port probe 0xa00-0xaff: clean.
[17179772.632000] lp0: using parport0 (interrupt-driven).
[17179772.696000] SCSI subsystem initialized
[17179772.716000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179772.716000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179772.752000] Adding 1317288k swap on /dev/disk/by-uuid/cbcba43f-353e-4bb8-8ca0-75b99deea074.  Priority:-1 extents:1 across:1317288k
[17179773.256000] EXT3 FS on hda1, internal journal
[17179774.028000] kjournald starting.  Commit interval 5 seconds
[17179774.036000] EXT3 FS on hda3, internal journal
[17179774.036000] EXT3-fs: mounted filesystem with ordered data mode.
[17179775.416000] NET: Registered protocol family 17
[17179780.412000] ACPI: AC Adapter [AC] (on-line)
[17179780.484000] ACPI: Battery Slot [BAT1] (battery present)
[17179780.500000] ACPI: Power Button (FF) [PWRF]
[17179780.500000] ACPI: Lid Switch [LID]
[17179780.500000] ACPI: Power Button (CM) [PWRB]
[17179780.640000] ibm_acpi: ec object not found
[17179780.672000] pcc_acpi: loading...
[17179781.104000] acpi-cpufreq: CPU0 - ACPI performance management activated.
[17179782.572000] eth0: no IPv6 routers present
[17179785.592000] [drm] Initialized drm 1.0.1 20051102
[17179785.604000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 16 (level, low) -> IRQ 193
[17179785.608000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179786.784000] mtrr: 0xa0000000,0x8000000 overlaps existing 0xa0000000,0x4000000
[17179786.784000] mtrr: 0xa0000000,0x8000000 overlaps existing 0xa0000000,0x4000000
[17179786.784000] mtrr: 0xa0000000,0x8000000 overlaps existing 0xa0000000,0x4000000
[17179786.784000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179786.784000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179786.784000] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
[17179786.956000] [drm] Setting GART location based on new memory map
[17179786.956000] [drm] writeback test succeeded in 1 usecs
[17179787.444000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179787.444000] apm: overridden by ACPI.


```

---

### Post by K.Mandla on 2007-03-26
That is kind of odd. I can read some specs in dmesg, but exactly what kind of machine is this? 

Just as an idea, you might reboot, hit Esc when you see the Grub boot menu appear, and edit "splash" and "quiet" out of your boot line for that startup (it'll only affect that boot). 

If you can see the boot process happening, it might give you an idea what's holding things up.

---

### Post by octavio on 2007-03-26
I will try to do what you say and see what happen.

By the way is a PIV 2.8GHz with 470MB of RAM. Toshiba Satellite A60

---

### Post by octavio on 2007-03-27
I did what you suggested to me and i have realized that the boot takes a lot of time (several minutes) when it reaches:

* Reading files needed to boot

Do you know any way to speed this up?

Thank you very much.

---

### Post by alanandhispc on 2007-03-27
could you force your system to check the disk and see what that throws up.

load a terminal and type:

sudo touch /forcefsck

then reboot.

it just seems like you may have a disk issue to me, but i could be wrong.


no harm in checking it anyway.


Thanks

Alan

---

