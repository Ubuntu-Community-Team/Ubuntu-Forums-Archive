---
title: "Leadtek DTV2000 H"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by tomek.vz on 2007-10-18
Hello.

I'm trying to enable analog TV and FM radio on this card for almost one week now but whitout sucess...does anybody know how to make it work?Here is some info:

root@venice:/home/tomek# dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: root=UUID=fd65dede-6d79-499c-8278-7da7b90af2f9 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 262128) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F69A0 checksum 0
[    0.000000] ACPI: RSDP 000F69A0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 3FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: FACP 3FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: DSDT 3FFF30C0, 49CE (r1 NVIDIA AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 3FFF0000, 0040
[    0.000000] ACPI: APIC 3FFF7AC0, 006E (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003fff0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 262128) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000003fff0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   262128
[    0.000000] On node 0 totalpages: 262031
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1124 pages reserved
[    0.000000]   DMA zone: 2819 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3527 pages used for memmap
[    0.000000]   DMA32 zone: 254505 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 257324
[    0.000000] Kernel command line: root=UUID=fd65dede-6d79-499c-8278-7da7b90af2f9 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   15.692706] time.c: Detected 2009.785 MHz processor.
[   15.694664] Console: colour VGA+ 80x25
[   15.694682] Checking aperture...
[   15.694685] CPU 0: aperture @ a0000000 size 512 MB
[   15.710337] Memory: 1021948k/1048512k available (2274k kernel code, 26176k reserved, 1181k data, 296k init)
[   15.710392] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   15.786617] Calibrating delay using timer specific routine.. 4022.07 BogoMIPS (lpj=8044153)
[   15.786657] Security Framework v1.0.0 initialized
[   15.786666] SELinux:  Disabled at boot.
[   15.786764] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   15.787876] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   15.788409] Mount-cache hash table entries: 256
[   15.788572] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   15.788575] CPU: L2 Cache: 512K (64 bytes/line)
[   15.788578] CPU 0/0 -> Node 0
[   15.788598] SMP alternatives: switching to UP code
[   15.788866] Freeing SMP alternatives: 24k freed
[   15.789336] Early unpacking initramfs... done
[   16.081688] ACPI: Core revision 20070126
[   16.081743] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.124488] Using local APIC timer interrupts.
[   16.174197] result 12561152
[   16.174199] Detected 12.561 MHz APIC timer.
[   16.174291] Brought up 1 CPUs
[   16.174495] NET: Registered protocol family 16
[   16.174584] ACPI: bus type pci registered
[   16.174590] PCI: Using configuration type 1
[   16.175546] ACPI: EC: Look up EC in DSDT
[   16.180757] ACPI: Interpreter enabled
[   16.180760] ACPI: (supports S0 S1 S4 S5)
[   16.180774] ACPI: Using IOAPIC for interrupt routing
[   16.188845] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.188852] PCI: Probing PCI hardware (bus 00)
[   16.189436] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.189582] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   16.189865] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[   16.236119] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.236265] ACPI: PCI Interrupt Link [LNK2] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   16.236413] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[   16.236556] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.236700] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   16.236847] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 *4 5 6 7 9 10 11 12 14 15)
[   16.236990] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 *4 5 6 7 9 10 11 12 14 15)
[   16.237134] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   16.237277] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.237420] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.237563] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.237707] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   16.237854] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 *4 5 6 7 9 10 11 12 14 15)
[   16.237998] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.238142] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.238290] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.238440] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.238590] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   16.238759] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   16.238914] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[   16.239073] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   16.239226] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   16.239336] ACPI: PCI Interrupt Link [APC5] (IRQs *16)
[   16.239494] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[   16.239651] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
[   16.239808] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
[   16.239964] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[   16.240121] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
[   16.240278] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[   16.240388] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
[   16.240544] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[   16.240700] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[   16.240858] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[   16.241016] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[   16.241180] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22) *0, disabled.
[   16.241344] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22) *0
[   16.241469] ACPI: Power Resource [ISAV] (on)
[   16.241484] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.241494] pnp: PnP ACPI init
[   16.241508] ACPI: bus type pnp registered
[   16.244862] pnp: PnP ACPI: found 10 devices
[   16.244865] ACPI: ACPI bus type pnp unregistered
[   16.244926] PCI: Using ACPI for IRQ routing
[   16.244930] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.244941] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[   16.245048] NET: Registered protocol family 8
[   16.245050] NET: Registered protocol family 20
[   16.245105] agpgart: Detected AGP bridge 0
[   16.245110] agpgart: Setting up Nforce3 AGP.
[   16.259787] agpgart: AGP aperture is 512M @ 0xa0000000
[   16.259858] pnp: 00:00: ioport range 0x1000-0x107f has been reserved
[   16.259861] pnp: 00:00: ioport range 0x1080-0x10ff has been reserved
[   16.259864] pnp: 00:00: ioport range 0x1400-0x147f has been reserved
[   16.259867] pnp: 00:00: ioport range 0x1480-0x14ff has been reserved
[   16.259870] pnp: 00:00: ioport range 0x1800-0x187f has been reserved
[   16.259872] pnp: 00:00: ioport range 0x1880-0x18ff has been reserved
[   16.259883] pnp: 00:01: iomem range 0xcde00-0xcffff has been reserved
[   16.259886] pnp: 00:01: iomem range 0xf0000-0xf7fff could not be reserved
[   16.259888] pnp: 00:01: iomem range 0xf8000-0xfbfff could not be reserved
[   16.259891] pnp: 00:01: iomem range 0xfc000-0xfffff could not be reserved
[   16.260139] PCI: Bridge: 0000:00:0b.0
[   16.260140]   IO window: disabled.
[   16.260144]   MEM window: d0000000-d2ffffff
[   16.260148]   PREFETCH window: c0000000-cfffffff
[   16.260152] PCI: Bridge: 0000:00:0e.0
[   16.260154]   IO window: 9000-9fff
[   16.260157]   MEM window: d3000000-d5ffffff
[   16.260159]   PREFETCH window: disabled.
[   16.260168] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   16.260206] NET: Registered protocol family 2
[   16.262166] Time: tsc clocksource has been installed.
[   16.298178] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   16.298547] TCP established hash table entries: 131072 (order: 9, 3145728 bytes)
[   16.301671] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   16.302787] TCP: Hash tables configured (established 131072 bind 65536)
[   16.302791] TCP reno registered
[   16.314256] checking if image is initramfs... it is
[   16.879410] Freeing initrd memory: 7209k freed
[   16.887413] audit: initializing netlink socket (disabled)
[   16.887427] audit(1192686748.156:1): initialized
[   16.889217] VFS: Disk quotas dquot_6.5.1
[   16.889274] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   16.889381] io scheduler noop registered
[   16.889383] io scheduler anticipatory registered
[   16.889385] io scheduler deadline registered
[   16.889477] io scheduler cfq registered (default)
[   16.890185] Boot video device is 0000:01:00.0
[   16.912404] Real Time Clock Driver v1.12ac
[   16.912520] Linux agpgart interface v0.102 (c) Dave Jones
[   16.912523] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.913502] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.913785] input: Macintosh mouse button emulation as /class/input/input0
[   16.913852] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   16.916900] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.916906] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.917093] mice: PS/2 mouse device common for all mice
[   16.917228] TCP cubic registered
[   16.917289] NET: Registered protocol family 1
[   16.917492] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   16.917499] Freeing unused kernel memory: 296k freed
[   16.977560] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.076993] fuse init (API version 7.8)
[   18.081529] Capability LSM initialized
[   18.751902] usbcore: registered new interface driver usbfs
[   18.751930] usbcore: registered new interface driver hub
[   18.751950] usbcore: registered new device driver usb
[   18.752667] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   18.752986] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   18.752993] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 22
[   18.753128] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   18.753135] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   18.753292] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   18.753311] ohci_hcd 0000:00:02.0: irq 22, io mem 0xd6002000
[   18.779969] SCSI subsystem initialized
[   18.784926] libata version 2.21 loaded.
[   18.797964] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   18.815369] usb usb1: configuration #1 chosen from 1 choice
[   18.815400] hub 1-0:1.0: USB hub found
[   18.815409] hub 1-0:1.0: 4 ports detected
[   18.919918] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[   18.919928] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 21
[   18.920055] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   18.920062] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   18.920119] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   18.920138] ohci_hcd 0000:00:02.1: irq 21, io mem 0xd6003000
[   18.981592] usb usb2: configuration #1 chosen from 1 choice
[   18.981617] hub 2-0:1.0: USB hub found
[   18.981628] hub 2-0:1.0: 4 ports detected
[   19.087844] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[   19.087853] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 20
[   19.088032] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   19.088039] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   19.088092] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   19.088122] ehci_hcd 0000:00:02.2: debug port 1
[   19.088126] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   19.088136] ehci_hcd 0000:00:02.2: irq 20, io mem 0xd6004000
[   19.088142] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   19.088225] usb usb3: configuration #1 chosen from 1 choice
[   19.088250] hub 3-0:1.0: USB hub found
[   19.088256] hub 3-0:1.0: 8 ports detected
[   19.199544] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   19.199551] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   19.200141] NFORCE3-250: IDE controller at PCI slot 0000:00:08.0
[   19.200236] NFORCE3-250: chipset revision 162
[   19.200238] NFORCE3-250: not 100% native mode: will probe irqs later
[   19.200244] NFORCE3-250: 0000:00:08.0 (rev a2) UDMA133 controller
[   19.200252]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   19.200261]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   19.200267] Probing IDE interface ide0...
[   19.734669] usb 2-4: new low speed USB device using ohci_hcd and address 2
[   19.770636] Probing IDE interface ide1...
[   19.940591] usb 2-4: configuration #1 chosen from 1 choice
[   19.953316] usbcore: registered new interface driver hiddev
[   19.962700] input: Logitech Logitech(R) Precision(TM) Gamepad as /class/input/input2
[   19.962707] input: USB HID v1.10 Joystick [Logitech Logitech(R) Precision(TM) Gamepad] on usb-0000:00:02.1-4
[   19.962723] usbcore: registered new interface driver usbhid
[   19.962726] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   20.513956] hdc: BENQ DVD DD DW1650, ATAPI CD/DVD-ROM drive
[   20.850484] ide1 at 0x170-0x177,0x376 on irq 15
[   20.853025] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[   20.853029] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [APCH] -> GSI 22 (level, high) -> IRQ 22
[   20.853035] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   20.862205] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   20.862215] Uniform CD-ROM driver Revision: 3.20
[   21.373446] eth0: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:05.0
[   21.373582] sata_nv 0000:00:0a.0: version 3.4
[   21.373936] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 21
[   21.373939] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APSJ] -> GSI 21 (level, high) -> IRQ 21
[   21.373985] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   21.374927] scsi0 : sata_nv
[   21.375122] scsi1 : sata_nv
[   21.375297] ata1: SATA max UDMA/133 cmd 0x00000000000109f0 ctl 0x0000000000010bf2 bmdma 0x000000000001c400 irq 21
[   21.375301] ata2: SATA max UDMA/133 cmd 0x0000000000010970 ctl 0x0000000000010b72 bmdma 0x000000000001c408 irq 21
[   21.688698] ata1: SATA link down (SStatus 0 SControl 300)
[   22.156232] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   22.164479] ata2.00: Host Protected Area detected:
[   22.164480]  current size: 321670847 sectors
[   22.164481]  native size: 321672960 sectors
[   22.164678] ata2.00: native size increased to 321672960 sectors
[   22.164683] ata2.00: ATA-7: Hitachi HDS721616PLA380, P22OAB3A, max UDMA/133
[   22.164686] ata2.00: 321672960 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   22.184461] ata2.00: configured for UDMA/133
[   22.184564] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDS72161 P22O PQ: 0 ANSI: 5
[   22.193129] sd 1:0:0:0: [sda] 321672960 512-byte hardware sectors (164697 MB)
[   22.193143] sd 1:0:0:0: [sda] Write Protect is off
[   22.193145] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.193157] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.193214] sd 1:0:0:0: [sda] 321672960 512-byte hardware sectors (164697 MB)
[   22.193222] sd 1:0:0:0: [sda] Write Protect is off
[   22.193224] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.193234] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.193239]  sda: sda1 sda2 < sda5 sda6 > sda3
[   22.226295] sd 1:0:0:0: [sda] Attached SCSI disk
[   22.230456] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   22.496865] JFS: nTxBlock = 8042, nTxLock = 64342
[   28.748643] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   28.748672] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
[   28.925001] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.926706] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   29.275269] usbcore: registered new interface driver xpad
[   29.275275] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   29.587277] Linux video capture interface: v2.00
[   29.609428] logips2pp: Detected unknown logitech mouse model 127
[   29.660145] input: PC Speaker as /class/input/input3
[   29.726633] nvidia: module license 'NVIDIA' taints kernel.
[   29.991102] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   29.991112] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 16
[   29.991298] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   30.074170] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input4
[   30.204615] cx2388x v4l2 driver version 0.0.6 loaded
[   30.204938] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   30.204945] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   30.204989] CORE cx88[0]: subsystem: 107d:665e, board: WinFast DTV2000 H [card=51,autodetected]
[   30.204993] TV tuner 63 at 0x1fe, Radio tuner -1 at 0x1fe
[   30.230893] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
[   30.302108] cx2388x alsa driver version 0.0.6 loaded
[   30.352251] input: cx88 IR (WinFast DTV2000 H) as /class/input/input5
[   30.352291] cx88[0]/0: found at 0000:02:0a.0, rev: 5, irq: 18, latency: 32, mmio: 0xd3000000
[   30.408260] tuner 2-0061: chip found @ 0xc2 (cx88[0])
[   30.410395] tuner 2-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   30.412496] tuner 2-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   30.413153] tuner 2-0063: chip found @ 0xc6 (cx88[0])
[   30.471413] cx88[0]/0: registered device video0 [v4l2]
[   30.471445] cx88[0]/0: registered device vbi0
[   30.472196] cx88[0]/2: cx2388x 8802 Driver Manager
[   30.472216] ACPI: PCI Interrupt 0000:02:0a.2[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   30.472224] cx88[0]/2: found at 0000:02:0a.2, rev: 5, irq: 18, latency: 32, mmio: 0xd5000000
[   30.472750] ACPI: PCI Interrupt 0000:02:0a.1[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   30.472791] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   30.528393] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   30.528402] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
[   30.528424] snd-ca0106: Model 1006 Rev 00000000 Serial 10061102
[   30.702312] cx2388x dvb driver version 0.0.6 loaded
[   30.702317] cx8802_register_driver() ->registering driver type=dvb access=shared
[   30.702321] CORE cx88[0]: subsystem: 107d:665e, board: WinFast DTV2000 H [card=51]
[   30.702324] cx88[0]/2: cx2388x based dvb card
[   30.795744] DVB: registering new adapter (cx88[0]).
[   30.795750] DVB: registering frontend 0 (Conexant CX22702 DVB-T)...
[   31.442039] it87: Found IT8712F chip at 0x290, revision 6
[   31.618979] Adding 489940k swap on /dev/sda5.  Priority:-1 extents:1 across:489940k
[   32.992632] kjournald starting.  Commit interval 5 seconds
[   32.992851] EXT3 FS on sda6, internal journal
[   32.992855] EXT3-fs: mounted filesystem with ordered data mode.
[   37.725831] lp: driver loaded but no devices found
[   37.826121] ppdev: user-space parallel port driver
[   43.025898] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   43.025917] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   43.025942] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   46.036678] NET: Registered protocol family 17
[   49.351918] NET: Registered protocol family 10
[   49.352074] lo: Disabled Privacy Extensions
[   59.614442] eth0: no IPv6 routers present

---

### Post by tomek.vz on 2007-10-18
root@venice:/home/tomek# lspci
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)
02:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
02:0a.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:0a.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
02:0a.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)


root@venice:/home/tomek# lsmod
Module                  Size  Used by
ipv6                  317192  8 
af_packet              28172  2 
binfmt_misc            14860  1 
ppdev                  11272  0 
parport_pc             41896  0 
lp                     15048  0 
parport                44172  3 ppdev,parport_pc,lp
battery                12424  0 
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
it87                   25232  0 
hwmon_vid               4864  1 it87
i2c_isa                 6400  1 it87
cx22702                 8452  1 
cx88_dvb               19076  0 
cx88_vp3054_i2c         5760  1 cx88_dvb
dvb_pll                18436  2 cx88_dvb
video_buf_dvb           8708  1 cx88_dvb
dvb_core               94768  1 video_buf_dvb
snd_ca0106             40480  3 
snd_ac97_codec        122200  1 snd_ca0106
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
tuner                  70184  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
cx88_alsa              17032  0 
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cx8802                 22276  1 cx88_dvb
cx8800                 41580  0 
snd_pcm                94344  5 snd_ca0106,snd_ac97_codec,cx88_alsa,snd_pcm_oss
cx88xx                 75556  4 cx88_dvb,cx88_alsa,cx8802,cx8800
snd_timer              27272  3 snd_seq,snd_pcm
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ir_common              38916  1 cx88xx
snd                    69288  15 snd_ca0106,snd_ac97_codec,snd_seq_oss,snd_rawmidi,cx88_alsa,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_timer,snd_seq_device
soundcore              10272  1 snd
ac97_bus                4096  1 snd_ac97_codec
snd_page_alloc         12560  2 snd_ca0106,snd_pcm
i2c_algo_bit            8324  2 cx88_vp3054_i2c,cx88xx
nvidia               7013492  24 
pcspkr                  4608  0 
video_buf              30084  6 cx88_dvb,video_buf_dvb,cx88_alsa,cx8802,cx8800,cx88xx
tveeprom               20496  1 cx88xx
videodev               31360  2 cx8800,cx88xx
v4l1_compat            15364  1 videodev
compat_ioctl32         11136  1 cx8800
v4l2_common            21888  5 tuner,cx8800,cx88xx,videodev,compat_ioctl32
k8temp                  7680  0 
psmouse                45596  0 
btcx_risc               6792  4 cx88_alsa,cx8802,cx8800,cx88xx
serio_raw               9092  0 
xpad                   11400  0 
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
i2c_nforce2             7808  0 
i2c_core               30208  12 it87,i2c_isa,cx22702,cx88_dvb,cx88_vp3054_i2c,dvb_pll,tuner,cx88xx,i2c_algo_bit,nvidia,tveeprom,i2c_nforce2
evdev                  13056  2 
joydev                 13440  0 
jfs                   189136  1 
sg                     41384  0 
sd_mod                 32512  4 
ide_cd                 35488  0 
cdrom                  41768  1 ide_cd
usbhid                 32576  0 
hid                    33408  1 usbhid
sata_nv                24068  4 
amd74xx                17328  0 [permanent]
ide_core              141200  2 ide_cd,amd74xx
forcedeth              55048  0 
ata_generic             9988  0 
libata                138928  2 sata_nv,ata_generic
scsi_mod              172856  3 sg,sd_mod,libata
ehci_hcd               40076  0 
ohci_hcd               25092  0 
usbcore               161584  5 xpad,usbhid,ehci_hcd,ohci_hcd
thermal                16528  0 
processor              36232  1 thermal
fan                     6920  0 
capability              7048  0 
commoncap               9472  1 capability
fuse                   52528  1 

Oct 18 07:52:47 venice kernel: [    0.000000] Command line: root=UUID=fd65dede-6d79-499c-8278-7da7b90af2f9 ro quiet splash
Oct 18 07:52:47 venice kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 18 07:52:47 venice kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Oct 18 07:52:47 venice kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Oct 18 07:52:47 venice kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Oct 18 07:52:47 venice kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
Oct 18 07:52:47 venice kernel: [    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
Oct 18 07:52:47 venice kernel: [    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
Oct 18 07:52:47 venice kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Oct 18 07:52:47 venice kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 18 07:52:47 venice kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Oct 18 07:52:47 venice kernel: [    0.000000] end_pfn_map = 1048576
Oct 18 07:52:47 venice kernel: [    0.000000] DMI 2.3 present.
Oct 18 07:52:47 venice kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F69A0 checksum 0
Oct 18 07:52:47 venice kernel: [    0.000000] ACPI: RSDP 000F69A0, 0014 (r0 Nvidia)
Oct 18 07:52:47 venice kernel: [    0.000000] ACPI: RSDT 3FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
Oct 18 07:52:47 venice kernel: [    0.000000] ACPI: FACP 3FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
Oct 18 07:52:47 venice kernel: [    0.000000] ACPI: DSDT 3FFF30C0, 49CE (r1 NVIDIA AWRDACPI     1000 MSFT  100000C)
Oct 18 07:52:47 venice kernel: [    0.000000] ACPI: FACS 3FFF0000, 0040
Oct 18 07:52:47 venice kernel: [    0.000000] ACPI: APIC 3FFF7AC0, 006E (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
Oct 18 07:52:47 venice kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Oct 18 07:52:47 venice kernel: [    0.000000] No NUMA configuration found
Oct 18 07:52:47 venice kernel: [    0.000000] Faking a node at 0000000000000000-000000003fff0000
Oct 18 07:52:47 venice kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000003fff0000
Oct 18 07:52:47 venice kernel: [    0.000000] Zone PFN ranges:
Oct 18 07:52:47 venice kernel: [    0.000000]   DMA             0 ->     4096
Oct 18 07:52:47 venice kernel: [    0.000000]   DMA32        4096 ->  1048576
Oct 18 07:52:47 venice kernel: [    0.000000]   Normal    1048576 ->  1048576
Oct 18 07:52:47 venice kernel: [    0.000000] early_node_map[2] active PFN ranges
Oct 18 07:52:47 venice kernel: [    0.000000]     0:        0 ->      159
Oct 18 07:52:47 venice kernel: [    0.000000]     0:      256 ->   262128
Oct 18 07:52:47 venice kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Oct 18 07:52:47 venice kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Oct 18 07:52:47 venice kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Oct 18 07:52:47 venice kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct 18 07:52:47 venice kernel: [    0.000000] Processor #0 (Bootup-CPU)
Oct 18 07:52:47 venice kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Oct 18 07:52:47 venice kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 18 07:52:47 venice kernel: [    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
Oct 18 07:52:47 venice kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 18 07:52:47 venice kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
Oct 18 07:52:47 venice kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 18 07:52:47 venice kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Oct 18 07:52:47 venice kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Oct 18 07:52:47 venice kernel: [    0.000000] Setting APIC routing to flat
Oct 18 07:52:47 venice kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 18 07:52:47 venice kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Oct 18 07:52:47 venice kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Oct 18 07:52:47 venice kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Oct 18 07:52:47 venice kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
Oct 18 07:52:47 venice kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Oct 18 07:52:47 venice kernel: [    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
Oct 18 07:52:47 venice kernel: [    0.000000] Built 1 zonelists.  Total pages: 257324
Oct 18 07:52:47 venice kernel: [    0.000000] Kernel command line: root=UUID=fd65dede-6d79-499c-8278-7da7b90af2f9 ro quiet splash
Oct 18 07:52:47 venice kernel: [    0.000000] Initializing CPU#0
Oct 18 07:52:47 venice kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Oct 18 07:52:47 venice kernel: [   15.692706] time.c: Detected 2009.785 MHz processor.
Oct 18 07:52:47 venice kernel: [   15.694664] Console: colour VGA+ 80x25
Oct 18 07:52:47 venice kernel: [   15.694682] Checking aperture...
Oct 18 07:52:47 venice kernel: [   15.694685] CPU 0: aperture @ a0000000 size 512 MB
Oct 18 07:52:47 venice kernel: [   15.710337] Memory: 1021948k/1048512k available (2274k kernel code, 26176k reserved, 1181k data, 296k init)
Oct 18 07:52:47 venice kernel: [   15.710392] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Oct 18 07:52:47 venice kernel: [   15.786617] Calibrating delay using timer specific routine.. 4022.07 BogoMIPS (lpj=8044153)
Oct 18 07:52:47 venice kernel: [   15.786657] Security Framework v1.0.0 initialized
Oct 18 07:52:47 venice kernel: [   15.786666] SELinux:  Disabled at boot.
Oct 18 07:52:47 venice kernel: [   15.786764] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 18 07:52:47 venice kernel: [   15.787876] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
Oct 18 07:52:47 venice kernel: [   15.788409] Mount-cache hash table entries: 256
Oct 18 07:52:47 venice kernel: [   15.788572] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Oct 18 07:52:47 venice kernel: [   15.788575] CPU: L2 Cache: 512K (64 bytes/line)
Oct 18 07:52:47 venice kernel: [   15.788578] CPU 0/0 -> Node 0
Oct 18 07:52:47 venice kernel: [   15.788598] SMP alternatives: switching to UP code
Oct 18 07:52:47 venice kernel: [   15.788866] Freeing SMP alternatives: 24k freed
Oct 18 07:52:47 venice kernel: [   15.789336] Early unpacking initramfs... done
Oct 18 07:52:47 venice kernel: [   16.081688] ACPI: Core revision 20070126
Oct 18 07:52:47 venice kernel: [   16.081743] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 18 07:52:47 venice kernel: [   16.124488] Using local APIC timer interrupts.
Oct 18 07:52:47 venice kernel: [   16.174197] result 12561152
Oct 18 07:52:47 venice kernel: [   16.174199] Detected 12.561 MHz APIC timer.
Oct 18 07:52:47 venice kernel: [   16.174291] Brought up 1 CPUs
Oct 18 07:52:47 venice kernel: [   16.174495] NET: Registered protocol family 16
Oct 18 07:52:47 venice kernel: [   16.174584] ACPI: bus type pci registered
Oct 18 07:52:47 venice kernel: [   16.174590] PCI: Using configuration type 1
Oct 18 07:52:47 venice kernel: [   16.180757] ACPI: Interpreter enabled
Oct 18 07:52:47 venice kernel: [   16.180760] ACPI: (supports S0 S1 S4 S5)
Oct 18 07:52:47 venice kernel: [   16.180774] ACPI: Using IOAPIC for interrupt routing
Oct 18 07:52:47 venice kernel: [   16.188845] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 18 07:52:47 venice kernel: [   16.236119] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 18 07:52:47 venice kernel: [   16.236265] ACPI: PCI Interrupt Link [LNK2] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Oct 18 07:52:47 venice kernel: [   16.236413] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Oct 18 07:52:47 venice kernel: [   16.236556] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 18 07:52:47 venice kernel: [   16.236700] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Oct 18 07:52:47 venice kernel: [   16.236847] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 *4 5 6 7 9 10 11 12 14 15)
Oct 18 07:52:47 venice kernel: [   16.236990] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 *4 5 6 7 9 10 11 12 14 15)
Oct 18 07:52:47 venice kernel: [   16.237134] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Oct 18 07:52:47 venice kernel: [   16.237277] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 18 07:52:47 venice kernel: [   16.237420] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 18 07:52:47 venice kernel: [   16.237563] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 18 07:52:47 venice kernel: [   16.237707] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Oct 18 07:52:47 venice kernel: [   16.237854] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 *4 5 6 7 9 10 11 12 14 15)
Oct 18 07:52:47 venice kernel: [   16.237998] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 18 07:52:47 venice kernel: [   16.238142] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 18 07:52:47 venice kernel: [   16.238290] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 18 07:52:47 venice kernel: [   16.238440] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 18 07:52:47 venice kernel: [   16.238590] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Oct 18 07:52:47 venice kernel: [   16.238759] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
Oct 18 07:52:47 venice kernel: [   16.238914] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
Oct 18 07:52:47 venice kernel: [   16.239073] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
Oct 18 07:52:47 venice kernel: [   16.239226] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Oct 18 07:52:47 venice kernel: [   16.239336] ACPI: PCI Interrupt Link [APC5] (IRQs *16)
Oct 18 07:52:47 venice kernel: [   16.239494] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
Oct 18 07:52:47 venice kernel: [   16.239651] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
Oct 18 07:52:47 venice kernel: [   16.239808] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
Oct 18 07:52:47 venice kernel: [   16.239964] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
Oct 18 07:52:47 venice kernel: [   16.240121] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
Oct 18 07:52:47 venice kernel: [   16.240278] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
Oct 18 07:52:47 venice kernel: [   16.240388] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
Oct 18 07:52:47 venice kernel: [   16.240544] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
Oct 18 07:52:47 venice kernel: [   16.240700] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
Oct 18 07:52:47 venice kernel: [   16.240858] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
Oct 18 07:52:47 venice kernel: [   16.241016] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
Oct 18 07:52:47 venice kernel: [   16.241180] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22) *0, disabled.
Oct 18 07:52:47 venice kernel: [   16.241344] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22) *0
Oct 18 07:52:47 venice kernel: [   16.241469] ACPI: Power Resource [ISAV] (on)
Oct 18 07:52:47 venice kernel: [   16.241484] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 18 07:52:47 venice kernel: [   16.241494] pnp: PnP ACPI init
Oct 18 07:52:47 venice kernel: [   16.241508] ACPI: bus type pnp registered
Oct 18 07:52:47 venice kernel: [   16.244862] pnp: PnP ACPI: found 10 devices
Oct 18 07:52:47 venice kernel: [   16.244865] ACPI: ACPI bus type pnp unregistered
Oct 18 07:52:47 venice kernel: [   16.244926] PCI: Using ACPI for IRQ routing
Oct 18 07:52:47 venice kernel: [   16.244930] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 18 07:52:47 venice kernel: [   16.245048] NET: Registered protocol family 8
Oct 18 07:52:47 venice kernel: [   16.245050] NET: Registered protocol family 20
Oct 18 07:52:47 venice kernel: [   16.245105] agpgart: Detected AGP bridge 0
Oct 18 07:52:47 venice kernel: [   16.245110] agpgart: Setting up Nforce3 AGP.
Oct 18 07:52:47 venice kernel: [   16.259787] agpgart: AGP aperture is 512M @ 0xa0000000
Oct 18 07:52:47 venice kernel: [   16.259858] pnp: 00:00: ioport range 0x1000-0x107f has been reserved
Oct 18 07:52:47 venice kernel: [   16.259861] pnp: 00:00: ioport range 0x1080-0x10ff has been reserved
Oct 18 07:52:47 venice kernel: [   16.259864] pnp: 00:00: ioport range 0x1400-0x147f has been reserved
Oct 18 07:52:47 venice kernel: [   16.259867] pnp: 00:00: ioport range 0x1480-0x14ff has been reserved
Oct 18 07:52:47 venice kernel: [   16.259870] pnp: 00:00: ioport range 0x1800-0x187f has been reserved
Oct 18 07:52:47 venice kernel: [   16.259872] pnp: 00:00: ioport range 0x1880-0x18ff has been reserved
Oct 18 07:52:47 venice kernel: [   16.259883] pnp: 00:01: iomem range 0xcde00-0xcffff has been reserved
Oct 18 07:52:47 venice kernel: [   16.259886] pnp: 00:01: iomem range 0xf0000-0xf7fff could not be reserved
Oct 18 07:52:47 venice kernel: [   16.259888] pnp: 00:01: iomem range 0xf8000-0xfbfff could not be reserved
Oct 18 07:52:47 venice kernel: [   16.259891] pnp: 00:01: iomem range 0xfc000-0xfffff could not be reserved
Oct 18 07:52:47 venice kernel: [   16.260139] PCI: Bridge: 0000:00:0b.0
Oct 18 07:52:47 venice kernel: [   16.260140]   IO window: disabled.
Oct 18 07:52:47 venice kernel: [   16.260144]   MEM window: d0000000-d2ffffff
Oct 18 07:52:47 venice kernel: [   16.260148]   PREFETCH window: c0000000-cfffffff
Oct 18 07:52:47 venice kernel: [   16.260152] PCI: Bridge: 0000:00:0e.0
Oct 18 07:52:47 venice kernel: [   16.260154]   IO window: 9000-9fff
Oct 18 07:52:47 venice kernel: [   16.260157]   MEM window: d3000000-d5ffffff
Oct 18 07:52:47 venice kernel: [   16.260159]   PREFETCH window: disabled.
Oct 18 07:52:47 venice kernel: [   16.260206] NET: Registered protocol family 2
Oct 18 07:52:47 venice kernel: [   16.262166] Time: tsc clocksource has been installed.
Oct 18 07:52:47 venice kernel: [   16.298178] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
Oct 18 07:52:47 venice kernel: [   16.298547] TCP established hash table entries: 131072 (order: 9, 3145728 bytes)
Oct 18 07:52:47 venice kernel: [   16.301671] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Oct 18 07:52:47 venice kernel: [   16.302787] TCP: Hash tables configured (established 131072 bind 65536)
Oct 18 07:52:47 venice kernel: [   16.302791] TCP reno registered
Oct 18 07:52:47 venice kernel: [   16.314256] checking if image is initramfs... it is
Oct 18 07:52:47 venice kernel: [   16.879410] Freeing initrd memory: 7209k freed
Oct 18 07:52:47 venice kernel: [   16.887413] audit: initializing netlink socket (disabled)
Oct 18 07:52:47 venice kernel: [   16.887427] audit(1192686748.156:1): initialized
Oct 18 07:52:47 venice kernel: [   16.889217] VFS: Disk quotas dquot_6.5.1
Oct 18 07:52:47 venice kernel: [   16.889274] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Oct 18 07:52:47 venice kernel: [   16.889381] io scheduler noop registered
Oct 18 07:52:47 venice kernel: [   16.889383] io scheduler anticipatory registered
Oct 18 07:52:47 venice kernel: [   16.889385] io scheduler deadline registered
Oct 18 07:52:47 venice kernel: [   16.889477] io scheduler cfq registered (default)
Oct 18 07:52:47 venice kernel: [   16.912404] Real Time Clock Driver v1.12ac
Oct 18 07:52:47 venice kernel: [   16.912520] Linux agpgart interface v0.102 (c) Dave Jones
Oct 18 07:52:47 venice kernel: [   16.912523] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 18 07:52:47 venice kernel: [   16.913502] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 18 07:52:47 venice kernel: [   16.913785] input: Macintosh mouse button emulation as /class/input/input0
Oct 18 07:52:47 venice kernel: [   16.913852] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct 18 07:52:47 venice kernel: [   16.916900] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 18 07:52:47 venice kernel: [   16.916906] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 18 07:52:47 venice kernel: [   16.917093] mice: PS/2 mouse device common for all mice
Oct 18 07:52:47 venice kernel: [   16.917228] TCP cubic registered
Oct 18 07:52:47 venice kernel: [   16.917289] NET: Registered protocol family 1
Oct 18 07:52:47 venice kernel: [   16.917492] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Oct 18 07:52:47 venice kernel: [   16.917499] Freeing unused kernel memory: 296k freed
Oct 18 07:52:47 venice kernel: [   16.977560] input: AT Translated Set 2 keyboard as /class/input/input1
Oct 18 07:52:47 venice kernel: [   18.076993] fuse init (API version 7.8)
Oct 18 07:52:47 venice kernel: [   18.081529] Capability LSM initialized
Oct 18 07:52:47 venice kernel: [   18.751902] usbcore: registered new interface driver usbfs
Oct 18 07:52:47 venice kernel: [   18.751930] usbcore: registered new interface driver hub
Oct 18 07:52:47 venice kernel: [   18.751950] usbcore: registered new device driver usb
Oct 18 07:52:47 venice kernel: [   18.752986] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
Oct 18 07:52:47 venice kernel: [   18.752993] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 22
Oct 18 07:52:47 venice kernel: [   18.753135] ohci_hcd 0000:00:02.0: OHCI Host Controller
Oct 18 07:52:47 venice kernel: [   18.753292] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
Oct 18 07:52:47 venice kernel: [   18.753311] ohci_hcd 0000:00:02.0: irq 22, io mem 0xd6002000
Oct 18 07:52:47 venice kernel: [   18.779969] SCSI subsystem initialized
Oct 18 07:52:47 venice kernel: [   18.797964] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
Oct 18 07:52:47 venice kernel: [   18.815369] usb usb1: configuration #1 chosen from 1 choice
Oct 18 07:52:47 venice kernel: [   18.815400] hub 1-0:1.0: USB hub found
Oct 18 07:52:47 venice kernel: [   18.815409] hub 1-0:1.0: 4 ports detected
Oct 18 07:52:47 venice kernel: [   18.919918] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
Oct 18 07:52:47 venice kernel: [   18.919928] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 21
Oct 18 07:52:47 venice kernel: [   18.920062] ohci_hcd 0000:00:02.1: OHCI Host Controller
Oct 18 07:52:47 venice kernel: [   18.920119] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
Oct 18 07:52:47 venice kernel: [   18.920138] ohci_hcd 0000:00:02.1: irq 21, io mem 0xd6003000
Oct 18 07:52:47 venice kernel: [   18.981592] usb usb2: configuration #1 chosen from 1 choice
Oct 18 07:52:47 venice kernel: [   18.981617] hub 2-0:1.0: USB hub found
Oct 18 07:52:47 venice kernel: [   18.981628] hub 2-0:1.0: 4 ports detected
Oct 18 07:52:47 venice kernel: [   19.087844] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
Oct 18 07:52:47 venice kernel: [   19.087853] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 20
Oct 18 07:52:47 venice kernel: [   19.088039] ehci_hcd 0000:00:02.2: EHCI Host Controller
Oct 18 07:52:47 venice kernel: [   19.088092] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
Oct 18 07:52:47 venice kernel: [   19.088122] ehci_hcd 0000:00:02.2: debug port 1
Oct 18 07:52:47 venice kernel: [   19.088136] ehci_hcd 0000:00:02.2: irq 20, io mem 0xd6004000
Oct 18 07:52:47 venice kernel: [   19.088142] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 18 07:52:47 venice kernel: [   19.088225] usb usb3: configuration #1 chosen from 1 choice
Oct 18 07:52:47 venice kernel: [   19.088250] hub 3-0:1.0: USB hub found
Oct 18 07:52:47 venice kernel: [   19.088256] hub 3-0:1.0: 8 ports detected
Oct 18 07:52:47 venice kernel: [   19.199544] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Oct 18 07:52:47 venice kernel: [   19.199551] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Oct 18 07:52:47 venice kernel: [   19.200141] NFORCE3-250: IDE controller at PCI slot 0000:00:08.0
Oct 18 07:52:47 venice kernel: [   19.200236] NFORCE3-250: chipset revision 162
Oct 18 07:52:47 venice kernel: [   19.200238] NFORCE3-250: not 100%% native mode: will probe irqs later
Oct 18 07:52:47 venice kernel: [   19.200244] NFORCE3-250: 0000:00:08.0 (rev a2) UDMA133 controller
Oct 18 07:52:47 venice kernel: [   19.200252]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
Oct 18 07:52:47 venice kernel: [   19.200261]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
Oct 18 07:52:47 venice kernel: [   19.734669] usb 2-4: new low speed USB device using ohci_hcd and address 2
Oct 18 07:52:47 venice kernel: [   19.940591] usb 2-4: configuration #1 chosen from 1 choice
Oct 18 07:52:47 venice kernel: [   19.953316] usbcore: registered new interface driver hiddev
Oct 18 07:52:47 venice kernel: [   19.962700] input: Logitech Logitech(R) Precision(TM) Gamepad as /class/input/input2
Oct 18 07:52:47 venice kernel: [   19.962707] input: USB HID v1.10 Joystick [Logitech Logitech(R) Precision(TM) Gamepad] on usb-0000:00:02.1-4
Oct 18 07:52:47 venice kernel: [   19.962723] usbcore: registered new interface driver usbhid
Oct 18 07:52:47 venice kernel: [   19.962726] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Oct 18 07:52:47 venice kernel: [   20.513956] hdc: BENQ DVD DD DW1650, ATAPI CD/DVD-ROM drive
Oct 18 07:52:47 venice kernel: [   20.850484] ide1 at 0x170-0x177,0x376 on irq 15
Oct 18 07:52:47 venice kernel: [   20.853025] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
Oct 18 07:52:47 venice kernel: [   20.853029] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [APCH] -> GSI 22 (level, high) -> IRQ 22
Oct 18 07:52:47 venice kernel: [   20.862205] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
Oct 18 07:52:47 venice kernel: [   20.862215] Uniform CD-ROM driver Revision: 3.20
Oct 18 07:52:47 venice kernel: [   21.373446] eth0: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:05.0
Oct 18 07:52:47 venice kernel: [   21.373936] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 21
Oct 18 07:52:47 venice kernel: [   21.373939] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APSJ] -> GSI 21 (level, high) -> IRQ 21
Oct 18 07:52:47 venice kernel: [   21.374927] scsi0 : sata_nv
Oct 18 07:52:47 venice kernel: [   21.375122] scsi1 : sata_nv
Oct 18 07:52:47 venice kernel: [   21.375297] ata1: SATA max UDMA/133 cmd 0x00000000000109f0 ctl 0x0000000000010bf2 bmdma 0x000000000001c400 irq 21
Oct 18 07:52:47 venice kernel: [   21.375301] ata2: SATA max UDMA/133 cmd 0x0000000000010970 ctl 0x0000000000010b72 bmdma 0x000000000001c408 irq 21
Oct 18 07:52:47 venice kernel: [   21.688698] ata1: SATA link down (SStatus 0 SControl 300)
Oct 18 07:52:47 venice kernel: [   22.156232] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct 18 07:52:47 venice kernel: [   22.164479] ata2.00: Host Protected Area detected:
Oct 18 07:52:47 venice kernel: [   22.164480] ^Icurrent size: 321670847 sectors
Oct 18 07:52:47 venice kernel: [   22.164481] ^Inative size: 321672960 sectors
Oct 18 07:52:47 venice kernel: [   22.164678] ata2.00: native size increased to 321672960 sectors
Oct 18 07:52:47 venice kernel: [   22.164683] ata2.00: ATA-7: Hitachi HDS721616PLA380, P22OAB3A, max UDMA/133
Oct 18 07:52:47 venice kernel: [   22.164686] ata2.00: 321672960 sectors, multi 16: LBA48 NCQ (depth 0/32)
Oct 18 07:52:47 venice kernel: [   22.184461] ata2.00: configured for UDMA/133
Oct 18 07:52:47 venice kernel: [   22.184564] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDS72161 P22O PQ: 0 ANSI: 5
Oct 18 07:52:47 venice kernel: [   22.193129] sd 1:0:0:0: [sda] 321672960 512-byte hardware sectors (164697 MB)
Oct 18 07:52:47 venice kernel: [   22.193143] sd 1:0:0:0: [sda] Write Protect is off
Oct 18 07:52:47 venice kernel: [   22.193157] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 18 07:52:47 venice kernel: [   22.193214] sd 1:0:0:0: [sda] 321672960 512-byte hardware sectors (164697 MB)
Oct 18 07:52:47 venice kernel: [   22.193222] sd 1:0:0:0: [sda] Write Protect is off
Oct 18 07:52:47 venice kernel: [   22.193234] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 18 07:52:47 venice kernel: [   22.193239]  sda: sda1 sda2 < sda5 sda6 > sda3
Oct 18 07:52:47 venice kernel: [   22.226295] sd 1:0:0:0: [sda] Attached SCSI disk
Oct 18 07:52:47 venice kernel: [   22.230456] sd 1:0:0:0: Attached scsi generic sg0 type 0
Oct 18 07:52:47 venice kernel: [   22.496865] JFS: nTxBlock = 8042, nTxLock = 64342
Oct 18 07:52:47 venice kernel: [   28.748643] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Oct 18 07:52:47 venice kernel: [   28.748672] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
Oct 18 07:52:47 venice kernel: [   28.925001] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 18 07:52:47 venice kernel: [   28.926706] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 18 07:52:47 venice kernel: [   29.275269] usbcore: registered new interface driver xpad
Oct 18 07:52:47 venice kernel: [   29.275275] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
Oct 18 07:52:47 venice kernel: [   29.587277] Linux video capture interface: v2.00
Oct 18 07:52:47 venice kernel: [   29.609428] logips2pp: Detected unknown logitech mouse model 127
Oct 18 07:52:47 venice kernel: [   29.660145] input: PC Speaker as /class/input/input3
Oct 18 07:52:47 venice kernel: [   29.726633] nvidia: module license 'NVIDIA' taints kernel.
Oct 18 07:52:47 venice kernel: [   29.991102] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
Oct 18 07:52:47 venice kernel: [   29.991112] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 16
Oct 18 07:52:47 venice kernel: [   29.991298] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
Oct 18 07:52:47 venice kernel: [   30.074170] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input4
Oct 18 07:52:47 venice kernel: [   30.204615] cx2388x v4l2 driver version 0.0.6 loaded
Oct 18 07:52:47 venice kernel: [   30.204938] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Oct 18 07:52:47 venice kernel: [   30.204945] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
Oct 18 07:52:47 venice kernel: [   30.204989] CORE cx88[0]: subsystem: 107d:665e, board: WinFast DTV2000 H [card=51,autodetected]
Oct 18 07:52:47 venice kernel: [   30.204993] TV tuner 63 at 0x1fe, Radio tuner -1 at 0x1fe
Oct 18 07:52:47 venice kernel: [   30.230893] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
Oct 18 07:52:47 venice kernel: [   30.302108] cx2388x alsa driver version 0.0.6 loaded
Oct 18 07:52:47 venice kernel: [   30.352251] input: cx88 IR (WinFast DTV2000 H) as /class/input/input5
Oct 18 07:52:47 venice kernel: [   30.352291] cx88[0]/0: found at 0000:02:0a.0, rev: 5, irq: 18, latency: 32, mmio: 0xd3000000
Oct 18 07:52:47 venice kernel: [   30.408260] tuner 2-0061: chip found @ 0xc2 (cx88[0])
Oct 18 07:52:47 venice kernel: [   30.410395] tuner 2-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
Oct 18 07:52:47 venice kernel: [   30.412496] tuner 2-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
Oct 18 07:52:47 venice kernel: [   30.413153] tuner 2-0063: chip found @ 0xc6 (cx88[0])
Oct 18 07:52:47 venice kernel: [   30.471413] cx88[0]/0: registered device video0 [v4l2]
Oct 18 07:52:47 venice kernel: [   30.471445] cx88[0]/0: registered device vbi0
Oct 18 07:52:47 venice kernel: [   30.472196] cx88[0]/2: cx2388x 8802 Driver Manager
Oct 18 07:52:47 venice kernel: [   30.472216] ACPI: PCI Interrupt 0000:02:0a.2[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
Oct 18 07:52:47 venice kernel: [   30.472224] cx88[0]/2: found at 0000:02:0a.2, rev: 5, irq: 18, latency: 32, mmio: 0xd5000000
Oct 18 07:52:47 venice kernel: [   30.472750] ACPI: PCI Interrupt 0000:02:0a.1[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
Oct 18 07:52:47 venice kernel: [   30.472791] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
Oct 18 07:52:47 venice kernel: [   30.528393] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
Oct 18 07:52:47 venice kernel: [   30.528402] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
Oct 18 07:52:47 venice kernel: [   30.528424] snd-ca0106: Model 1006 Rev 00000000 Serial 10061102
Oct 18 07:52:47 venice kernel: [   30.702312] cx2388x dvb driver version 0.0.6 loaded
Oct 18 07:52:47 venice kernel: [   30.702317] cx8802_register_driver() ->registering driver type=dvb access=shared
Oct 18 07:52:47 venice kernel: [   30.702321] CORE cx88[0]: subsystem: 107d:665e, board: WinFast DTV2000 H [card=51]
Oct 18 07:52:47 venice kernel: [   30.702324] cx88[0]/2: cx2388x based dvb card
Oct 18 07:52:47 venice kernel: [   30.795744] DVB: registering new adapter (cx88[0]).
Oct 18 07:52:47 venice kernel: [   30.795750] DVB: registering frontend 0 (Conexant CX22702 DVB-T)...
Oct 18 07:52:47 venice kernel: [   31.442039] it87: Found IT8712F chip at 0x290, revision 6
Oct 18 07:52:47 venice kernel: [   31.618979] Adding 489940k swap on /dev/sda5.  Priority:-1 extents:1 across:489940k
Oct 18 07:52:47 venice kernel: [   32.992632] kjournald starting.  Commit interval 5 seconds
Oct 18 07:52:47 venice kernel: [   32.992851] EXT3 FS on sda6, internal journal
Oct 18 07:52:47 venice kernel: [   32.992855] EXT3-fs: mounted filesystem with ordered data mode.
Oct 18 07:52:49 venice kernel: [   37.725831] lp: driver loaded but no devices found
Oct 18 07:52:49 venice kernel: [   37.826121] ppdev: user-space parallel port driver
Oct 18 07:52:52 venice dhcdbd: Started up.
Oct 18 07:52:54 venice dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 18 07:52:55 venice kernel: [   43.025898] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Oct 18 07:52:55 venice kernel: [   43.025917] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Oct 18 07:52:55 venice kernel: [   43.025942] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Oct 18 07:52:57 venice kernel: [   46.036678] NET: Registered protocol family 17
Oct 18 07:52:59 venice dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 18 07:52:59 venice dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Oct 18 07:52:59 venice dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 18 07:52:59 venice dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 18 07:53:01 venice kernel: [   49.351918] NET: Registered protocol family 10
Oct 18 07:53:01 venice kernel: [   49.352074] lo: Disabled Privacy Extensions
Oct 18 08:12:47 venice -- MARK --

---

### Post by tomek.vz on 2007-10-21
bump

---

