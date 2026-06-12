---
title: "intermmitent white screen"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by GOwin on 2007-06-08
I have a recurring problem with my laptop. I sometimes experience hanging with just a  blank white screen. keys are dead, i can't restart x or even switch to terminal mode. 

I haven't found any means to reproduce the problem. The problem is intermittent.

What is the best way of recovering relevant information AFTER a crash and a reboot? Because, the only way of getting my computer to work after experiencing this bug is to reboot the sytem. Also, I never encounter this problem on the same laptop on Windows.

I'm not using any dekstop effects and is using the default x.org driver.

I'm using an MSI S270 laptop (aka MS1013). Here are some information about my system:

```

Sat Jun  9 11:48:14 PHT 2007

$ uname -a
Linux kulasa 2.6.20-16-generic #2 SMP Wed May 23 00:30:47 UTC 2007 x86_64 GNU/Linux

```

```
$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@king) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Wed May 23 00:30:47 UTC 2007 (Ubuntu 2.6.20-16.28-generic)
[    0.000000] Command line: root=UUID=329cc213-f7ab-41b2-a998-885d7b5edee7 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001df40000 (usable)
[    0.000000]  BIOS-e820: 000000001df40000 - 000000001df50000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001df50000 - 000000001e000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001e000000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 122688) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 MSI                                   ) @ 0x00000000000f83d0
[    0.000000] ACPI: RSDT (v001 MSI    1013     0x01092006 MSFT 0x00000097) @ 0x000000001df40000
[    0.000000] ACPI: FADT (v002 MSI    1013     0x01092006 MSFT 0x00000097) @ 0x000000001df40200
[    0.000000] ACPI: MADT (v001 MSI    OEMAPIC  0x01092006 MSFT 0x00000097) @ 0x000000001df40300
[    0.000000] ACPI: WDRT (v001 MSI    MSI_OEM  0x01092006 MSFT 0x00000097) @ 0x000000001df40360
[    0.000000] ACPI: MCFG (v001 MSI    OEMMCFG  0x01092006 MSFT 0x00000097) @ 0x000000001df403b0
[    0.000000] ACPI: SSDT (v001 OEM_ID OEMTBLID 0x00000001 INTL 0x02002026) @ 0x000000001df43750
[    0.000000] ACPI: OEMB (v001 MSI    MSI_OEM  0x01092006 MSFT 0x00000097) @ 0x000000001df50040
[    0.000000] ACPI: DSDT (v001    MSI     1013 0x01092006 INTL 0x02002026) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000001df40000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 122688) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000001df40000
[    0.000000] No mptable found.
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   122688
[    0.000000] On node 0 totalpages: 122591
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1084 pages reserved
[    0.000000]   DMA zone: 2859 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 1621 pages used for memmap
[    0.000000]   DMA32 zone: 116971 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000e4000
[    0.000000] Nosave address range: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dff80000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 119830
[    0.000000] Kernel command line: root=UUID=329cc213-f7ab-41b2-a998-885d7b5edee7 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 16384 bytes)
[    7.598052] Console: colour VGA+ 80x25
[    7.598609] Dentry cache hash table entries: 65536 (order: 7, 524288 bytes)
[    7.599003] Inode-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    7.599069] Checking aperture...
[    7.599073] CPU 0: aperture @ 8000000 size 32 MB
[    7.599075] Aperture too small (32 MB)
[    7.611002] No AGP bridge found
[    7.618127] Memory: 471616k/490752k available (2217k kernel code, 18748k reserved, 1162k data, 304k init)
[    7.695138] Calibrating delay using timer specific routine.. 3187.15 BogoMIPS (lpj=6374316)
[    7.695207] Security Framework v1.0.0 initialized
[    7.695214] SELinux:  Disabled at boot.
[    7.695243] Mount-cache hash table entries: 256
[    7.695417] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    7.695420] CPU: L2 Cache: 1024K (64 bytes/line)
[    7.695424] CPU 0/0 -> Node 0
[    7.695446] SMP alternatives: switching to UP code
[    7.695721] Freeing SMP alternatives: 28k freed
[    7.695854] Early unpacking initramfs... done
[    8.064254] ACPI: Core revision 20060707
[    8.064745] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    8.107523] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    8.147600] Using local APIC timer interrupts.
[    8.210395] result 12436898
[    8.210397] Detected 12.436 MHz APIC timer.
[    8.211001] Brought up 1 CPUs
[    8.211044] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[    8.211047] time.c: Detected 1591.921 MHz processor.
[    8.211401] Time: 11:30:14  Date: 05/09/107
[    8.211443] NET: Registered protocol family 16
[    8.211534] ACPI: bus type pci registered
[    8.211542] PCI: Using configuration type 1
[    8.216369] ACPI: Interpreter enabled
[    8.216372] ACPI: Using IOAPIC for interrupt routing
[    8.216820] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.216826] PCI: Probing PCI hardware (bus 00)
[    8.217824] Boot video device is 0000:01:05.0
[    8.218415] PCI: Transparent bridge - 0000:00:14.4
[    8.218494] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#03) (try 'pci=assign-busses')
[    8.218497] Please report the result to linux-kernel to fix this permanently
[    8.218526] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.227330] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    8.234212] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.POP2._PRT]
[    8.236810] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[    8.237037] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[    8.237265] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[    8.237492] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[    8.237720] ACPI: PCI Interrupt Link [LNKE] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[    8.237946] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[    8.238179] ACPI: PCI Interrupt Link [LNKG] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[    8.238408] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[    8.238515] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.238526] pnp: PnP ACPI init
[    8.241370] pnp: PnP ACPI: found 11 devices
[    8.241424] PCI: Using ACPI for IRQ routing
[    8.241427] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.241535] NET: Registered protocol family 8
[    8.241537] NET: Registered protocol family 20
[    8.242498] PCI: Bridge: 0000:00:01.0
[    8.242501]   IO window: d000-dfff
[    8.242505]   MEM window: fbe00000-fbefffff
[    8.242509]   PREFETCH window: f4000000-faffffff
[    8.242520] PCI: Bus 3, cardbus bridge: 0000:02:05.0
[    8.242523]   IO window: 0000e000-0000e0ff
[    8.242529]   IO window: 0000e400-0000e4ff
[    8.242535]   PREFETCH window: 30000000-33ffffff
[    8.242542]   MEM window: 38000000-3bffffff
[    8.242547] PCI: Bridge: 0000:00:14.4
[    8.242551]   IO window: e000-efff
[    8.242558]   MEM window: fbf00000-fbffffff
[    8.242563]   PREFETCH window: 30000000-35ffffff
[    8.242603] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 19 (level, low) -> IRQ 19
[    8.242689] NET: Registered protocol family 2
[    8.275014] IP route cache hash table entries: 4096 (order: 3, 32768 bytes)
[    8.275127] TCP established hash table entries: 16384 (order: 6, 262144 bytes)
[    8.275398] TCP bind hash table entries: 8192 (order: 5, 131072 bytes)
[    8.275537] TCP: Hash tables configured (established 16384 bind 8192)
[    8.275540] TCP reno registered
[    8.287049] checking if image is initramfs... it is
[    9.014212] Freeing initrd memory: 6825k freed
[    9.021420] audit: initializing netlink socket (disabled)
[    9.021434] audit(1181388614.332:1): initialized
[    9.021590] VFS: Disk quotas dquot_6.5.1
[    9.021609] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    9.021661] io scheduler noop registered
[    9.021664] io scheduler anticipatory registered
[    9.021666] io scheduler deadline registered
[    9.021680] io scheduler cfq registered (default)
[    9.047580] Real Time Clock Driver v1.12ac
[    9.047630] Linux agpgart interface v0.102 (c) Dave Jones
[    9.047633] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.048183] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[    9.048192] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[    9.048272] mice: PS/2 mouse device common for all mice
[    9.048833] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.049046] input: Macintosh mouse button emulation as /class/input/input0
[    9.049082] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    9.049086] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    9.049369] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    9.049712] i8042.c: Detected active multiplexing controller, rev 1.1.
[    9.049792] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.049796] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    9.049799] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    9.049802] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    9.049805] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    9.049972] TCP cubic registered
[    9.049982] NET: Registered protocol family 1
[    9.050104] ACPI: (supports S0 S1 S3 S4 S5)
[    9.050157]   Magic number: 11:318:529
[    9.050294] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[    9.050419] Freeing unused kernel memory: 304k freed
[    9.053228] input: AT Translated Set 2 keyboard as /class/input/input1
[   10.260796] Capability LSM initialized
[   10.300193] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   10.305115] ACPI: Thermal Zone [THRM] (57 C)
[   10.822062] usbcore: registered new interface driver usbfs
[   10.822088] usbcore: registered new interface driver hub
[   10.822114] usbcore: registered new device driver usb
[   10.822907] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   10.822944] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   10.822960] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   10.823138] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   10.823160] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfbdfd000
[   10.906679] usb usb1: configuration #1 chosen from 1 choice
[   10.906707] hub 1-0:1.0: USB hub found
[   10.906721] hub 1-0:1.0: 4 ports detected
[   10.928220] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   10.973975] ieee1394: Initialized config rom entry `ip1394'
[   11.010040] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   11.010060] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   11.010084] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   11.010104] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfbdfe000
[   11.070031] usb usb2: configuration #1 chosen from 1 choice
[   11.070059] hub 2-0:1.0: USB hub found
[   11.070071] hub 2-0:1.0: 4 ports detected
[   11.174053] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   11.174073] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   11.174102] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   11.174166] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfbdff000
[   11.174179] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   11.174282] usb usb3: configuration #1 chosen from 1 choice
[   11.174306] hub 3-0:1.0: USB hub found
[   11.174313] hub 3-0:1.0: 8 ports detected
[   11.277980] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   11.278001] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   11.278013] ATIIXP: chipset revision 0
[   11.278015] ATIIXP: not 100% native mode: will probe irqs later
[   11.278025]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:pio
[   11.278042]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:pio
[   11.278052] Probing IDE interface ide0...
[   11.566125] hda: TOSHIBA MK8026GAX, ATA DISK drive
[   11.925550] usb 1-2: new low speed USB device using ohci_hcd and address 3
[   12.135082] usb 1-2: configuration #1 chosen from 1 choice
[   12.148073] usbcore: registered new interface driver hiddev
[   12.154258] input: Logitech USB Optical Mouse as /class/input/input2
[   12.154402] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:13.0-2
[   12.154417] usbcore: registered new interface driver usbhid
[   12.154420] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   12.237546] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   12.286813] Probing IDE interface ide1...
[   13.021570] hdc: HL-DT-ST DVD-RW GWA-4082N, ATAPI CD/DVD-ROM drive
[   13.357937] ide1 at 0x170-0x177,0x376 on irq 15
[   13.370115] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   13.370120] 8139cp 0000:02:03.0: Try the "8139too" driver instead.
[   13.370165] ACPI: PCI Interrupt 0000:02:05.4[A] -> GSI 19 (level, low) -> IRQ 19
[   13.421822] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fbffe000-fbffe7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   13.425604] SCSI subsystem initialized
[   13.432454] libata version 2.20 loaded.
[   13.437174] 8139too Fast Ethernet driver 0.9.28
[   13.437240] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 18 (level, low) -> IRQ 18
[   13.437905] eth0: RealTek RTL8139 at 0xffffc20000032c00, 00:13:d3:f0:2d:98, IRQ 18
[   13.437908] eth0:  Identified 8139 chip type 'RTL-8101'
[   13.446679] hda: max request size: 128KiB
[   13.453810] hda: 156301488 sectors (80026 MB), CHS=65535/16/63, UDMA(100)
[   13.453906] hda: cache flushes supported
[   13.453943]  hda: hda1 hda2 < hda5 hda6 hda7 hda8 >
[   13.589905] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   13.589914] Uniform CD-ROM driver Revision: 3.20
[   13.981691] Attempting manual resume
[   13.981695] swsusp: Resume From Partition 3:7
[   13.981697] PM: Checking swsusp image.
[   14.001530] PM: Resume from disk failed.
[   14.042355] EXT3-fs: INFO: recovery required on readonly filesystem.
[   14.042360] EXT3-fs: write access will be enabled during recovery.
[   14.692738] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[672f01006da337a0]
[   15.499354] kjournald starting.  Commit interval 5 seconds
[   15.499371] EXT3-fs: recovery complete.
[   15.507717] EXT3-fs: mounted filesystem with ordered data mode.
[   27.455349] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   27.593327] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.595407] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.728282] Yenta: CardBus bridge found at 0000:02:05.0 [1462:0221]
[   27.728313] Yenta O2: res at 0x94/0xD4: 00/ea
[   27.728315] Yenta O2: enabling read prefetch/write burst
[   27.826857] sdhci: Secure Digital Host Controller Interface driver
[   27.826861] sdhci: Copyright(c) Pierre Ossman
[   27.856864] Yenta: ISA IRQ mask 0x0eb8, PCI irq 19
[   27.856870] Socket status: 30000006
[   27.856874] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   27.856881] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xefff
[   27.856885] pcmcia: parent PCI bridge Memory window: 0xfbf00000 - 0xfbffffff
[   27.856889] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x35ffffff
[   27.857475] sdhci: SDHCI controller found at 0000:02:05.2 [1217:7120] (rev 1)
[   27.857503] ACPI: PCI Interrupt 0000:02:05.2[A] -> GSI 19 (level, low) -> IRQ 19
[   27.857527] sdhci:slot0: Unknown controller version (16). You may experience problems.
[   27.857584] mmc0: SDHCI at 0xfbfff800 irq 19 PIO
[   28.282723] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 22 (level, low) -> IRQ 22
[   28.282730] rt2500 1.1.0 BETA4 2006/06/18 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[   28.341969] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   28.466820] input: PC Speaker as /class/input/input3
[   28.856688] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   28.992599] input: ImPS/2 Logitech Wheel Mouse as /class/input/input4
[   29.231790] fuse init (API version 7.8)
[   29.289695] lp: driver loaded but no devices found
[   29.367539] Adding 530104k swap on /dev/disk/by-uuid/3aa8ad81-e402-41d9-ad29-f40c3b0d8ace.  Priority:-1 extents:1 across:530104k
[   29.515958] EXT3 FS on hda6, internal journal
[   30.995585] kjournald starting.  Commit interval 5 seconds
[   30.995705] EXT3 FS on hda8, internal journal
[   30.995710] EXT3-fs: mounted filesystem with ordered data mode.
[   31.037834] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   32.757620] NET: Registered protocol family 17
[   38.499047] Using specific hotkey driver
[   38.556459] input: Power Button (FF) as /class/input/input5
[   38.561064] ACPI: Power Button (FF) [PWRF]
[   38.590197] input: Lid Switch as /class/input/input6
[   38.594742] ACPI: Lid Switch [LID0]
[   38.623879] input: Sleep Button (CM) as /class/input/input7
[   38.628453] ACPI: Sleep Button (CM) [SLPB]
[   38.657350] input: Power Button (CM) as /class/input/input8
[   38.661873] ACPI: Power Button (CM) [PWRB]
[   38.695135] ibm_acpi: ec object not found
[   38.759132] ACPI: Battery Slot [BAT1] (battery present)
[   38.785701] ACPI: AC Adapter [ADP1] (on-line)
[   38.839970] No dock devices found.
[   38.939788] pcc_acpi: loading...
[   39.125509] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MT-30 processors (version 2.00.00)
[   39.125655] ACPI: Invalid package argument
[   39.125659] ACPI Exception (acpi_processor-0270): AE_BAD_PARAMETER, Invalid _PSS data [20060707]
[   39.133409] powernow-k8:    0 : fid 0x0 (800 MHz), vid 0x16
[   39.133412] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xa
[   39.134796] powernow-k8: ph2 null fid transition 0x8
[   40.615638] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[   40.615648] rt2500 EEPROM:  6  6  6  6  6  6  6  6  6  6  6  6  6  6  dBm Maximum
[   40.743353] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   42.356036] ppdev: user-space parallel port driver
[   43.517406] Bluetooth: Core ver 2.11
[   43.517471] NET: Registered protocol family 31
[   43.517474] Bluetooth: HCI device and connection manager initialized
[   43.517478] Bluetooth: HCI socket layer initialized
[   43.543788] Bluetooth: L2CAP ver 2.8
[   43.543793] Bluetooth: L2CAP socket layer initialized
[   43.619825] Bluetooth: RFCOMM socket layer initialized
[   43.619842] Bluetooth: RFCOMM TTY layer initialized
[   43.619844] Bluetooth: RFCOMM ver 1.8
[   43.777985] NET: Registered protocol family 10
[   43.778086] lo: Disabled Privacy Extensions
[   50.733116] ra0: no IPv6 routers present
[   52.484466] eth0: no IPv6 routers present
[  118.347823] Losing some ticks... checking if CPU frequency changed.

```

```

$ lspci -vnn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
	Subsystem: Micro-Star International Co., Ltd. Unknown device [1462:0131]
	Flags: bus master, 66MHz, medium devsel, latency 0

00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f] (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fbe00000-fbefffff
	Prefetchable memory behind bridge: 00000000f4000000-00000000faffffff
	Capabilities: [44] HyperTransport: MSI Mapping
	Capabilities: [b0] Subsystem: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]

00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (prog-if 10 [OHCI])
	Subsystem: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fbdfd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (prog-if 10 [OHCI])
	Subsystem: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fbdfe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (prog-if 20 [EHCI])
	Subsystem: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fbdff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 10)
	Subsystem: Micro-Star International Co., Ltd. Unknown device [1462:0131]
	Flags: 66MHz, medium devsel
	I/O ports at c800 [size=16]
	Memory at fbdfc400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [b0] HyperTransport: MSI Mapping

00:14.1 IDE interface [0101]: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI [1002:4376] (prog-if 8a [Master SecP PriP])
	Subsystem: Micro-Star International Co., Ltd. Unknown device [1462:0131]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff00 [size=16]
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=02, subordinate=06, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbf00000-fbffffff
	Prefetchable memory behind bridge: 30000000-35ffffff

00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Unknown device [1462:0131]
	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
	Memory at fbdfc800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:14.6 Modem [0703]: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller [1002:4378] (rev 01) (prog-if 00 [Generic])
	Subsystem: Micro-Star International Co., Ltd. Unknown device [1462:0131]
	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
	Memory at fbdfcc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Flags: fast devsel

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Flags: fast devsel

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE) [1002:5955] (prog-if 00 [VGA])
	Subsystem: Micro-Star International Co., Ltd. Unknown device [1462:0131]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
	Memory at f4000000 (32-bit, prefetchable) [size=64M]
	I/O ports at d800 [size=256]
	Memory at fbef0000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at fbec0000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2

02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Micro-Star International Co., Ltd. Unknown device [1462:0131]
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at e800 [size=256]
	Memory at fbfffc00 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at 34000000 [disabled] [size=64K]
	Capabilities: [50] Power Management version 2

02:05.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller [1217:7134] (rev 21)
	Subsystem: Micro-Star International Co., Ltd. Unknown device [1462:0221]
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 19
	Memory at fbf00000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 30000000-33fff000 (prefetchable)
	Memory window 1: 38000000-3bfff000
	I/O window 0: 0000e000-0000e0ff
	I/O window 1: 0000e400-0000e4ff
	16-bit legacy interface ports at 0001

02:05.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Unknown device [1462:0221]
	Flags: slow devsel, IRQ 19
	Memory at fbfff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a0] Power Management version 2

02:05.3 Bridge [0680]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Unknown device [1462:0221]
	Flags: slow devsel, IRQ 11
	Memory at fbffd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [a0] Power Management version 2

02:05.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02) (prog-if 10 [OHCI])
	Subsystem: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7]
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at fbffe000 (32-bit, non-prefetchable) [size=4K]
	Memory at fbfff000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [60] Power Management version 2

02:09.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Unknown device [1462:6833]
	Flags: bus master, slow devsel, latency 64, IRQ 22
	Memory at fbffa000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [40] Power Management version 2


```

---

