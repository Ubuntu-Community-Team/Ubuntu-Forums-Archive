---
title: "[SOLVED] noapic boot problems"
date: 2008-09-12
forum: Hardware
---

### Post by offchance on 2008-09-12
My 8.04, amd athlon dual core 64, compaq laptop has been freezing up when I use ndiswrapper/wireless. During my investigations into possible irq problems I have been booting with a variety of kernel commands.

I find that when I omit noapic my pc freezes here:
[  57.364362] ide0 at 0x1f0-0x1f7,0x3f7,0x3f6 on irq 14
Apparently this has something to do with my DVD-R drive. I have an unresolved problem of my cd drive thinking there is a cd in it when there isn't one. Could they be related? I don't know, and I don't know how to interpret the line above.

Any help is appreciated!

---

### Post by ice2921 on 2008-09-12
have you tried booting with these options:
```
apic=off  irqpoll
```

---

### Post by offchance on 2008-09-12
> **ice2921 said:**
> have you tried booting with these options:
```
apic=off  irqpoll
```
I will try that and report back. what does irqpoll do anyway? (I have used irqfixup and pci=routeirq in the past).

---

### Post by IntuitiveNipple on 2008-09-12
Please attach a (compressed) copy of /var/log/dmesg so we can get an idea of what Linux discovers as it starts. If it is possible, two versions, one for the "noapic" option and one without it - unless the start-up never gets far enough to write the log to disk, of course :)

---

### Post by ice2921 on 2008-09-12
Alot of times on laptops, the IRQ ports are grouped together/shared booting with this option is supposed to alleviate some of those problems. I have used it a few times and it has helped me. As mentioned by IntuitiveNipple the output of /var/log/dmesg would be helpful. If the first solution does not work. Remember you can test the boot options first in the boot GUI of the grub menu.

---

### Post by offchance on 2008-09-12
I booted without noapic or any other additional kernel commands. It froze up at "*Loading hardware drivers" like usual. I then rebooted into a livecd of Puppy Linux to check the dmesg on my Ubuntu hard drive to see if anything was recorded from the failed boot. Nothing new was written in dmesg or messages. The following is from the last successful bootup with noapic:

```
[    0.000000] Linux version 2.6.22-15-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Fri Jul 11 18:56:36 UTC 2008 (Ubuntu 2.6.22-15.56-generic)
[    0.000000] Command line: root=UUID=df76798a-def3-4925-bb31-21676250cec1 ro noapic irqfixup quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bf00000 (usable)
[    0.000000]  BIOS-e820: 000000003bf00000 - 000000003bf16000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003bf16000 - 000000003bf80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bf80000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 245504) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F88E0 checksum 0
[    0.000000] ACPI: RSDP 000F88E0, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 3BF0CB68, 0040 (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP 3BF15B58, 0074 (r1 HP     MCP51M    6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 3BF0CBA8, 8FB0 (r1 HP       MCP51M  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 3BF16FC0, 0040
[    0.000000] ACPI: SSDT 3BF15BCC, 01C4 (r1 HP     POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: MCFG 3BF15D90, 003C (r1 HP       MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET 3BF15DCC, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC 3BF15E04, 005E (r1 HP     	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 3BF15E62, 0028 (r1     HP $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC 3BF15E8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003bf00000
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 245504) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000003bf00000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      157
[    0.000000]     0:      256 ->   245504
[    0.000000] On node 0 totalpages: 245405
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1128 pages reserved
[    0.000000]   DMA zone: 2813 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3300 pages used for memmap
[    0.000000]   DMA32 zone: 238108 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000] MPTABLE: OEM ID: nVIDIA   MPTABLE: Product ID: C51-MCP51    MPTABLE: APIC at: 0xFEE00000
[    0.000000] I/O APIC #2 at 0xFEC00000.
[    0.000000] Setting APIC routing to flat
[    0.000000] Processors: 2
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 240921
[    0.000000] Kernel command line: root=UUID=df76798a-def3-4925-bb31-21676250cec1 ro noapic irqfixup quiet splash
[    0.000000] Misrouted IRQ fixup support enabled.
[    0.000000] This may impact system performance.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[   20.180465] time.c: Detected 1707.772 MHz processor.
[   20.183679] Console: colour VGA+ 80x25
[   20.183698] Checking aperture...
[   20.183702] CPU 0: aperture @ 9580000000 size 32 MB
[   20.183704] Aperture too small (32 MB)
[   20.190691] No AGP bridge found
[   20.203178] Memory: 956308k/982016k available (2274k kernel code, 25312k reserved, 1185k data, 300k init)
[   20.203229] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   20.281799] Calibrating delay using timer specific routine.. 3418.45 BogoMIPS (lpj=6836903)
[   20.281833] Security Framework v1.0.0 initialized
[   20.281839] SELinux:  Disabled at boot.
[   20.281942] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   20.282696] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   20.283004] Mount-cache hash table entries: 256
[   20.283143] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   20.283146] CPU: L2 Cache: 256K (64 bytes/line)
[   20.283149] CPU 0/0 -> Node 0
[   20.283151] CPU: Physical Processor ID: 0
[   20.283153] CPU: Processor Core ID: 0
[   20.283171] SMP alternatives: switching to UP code
[   20.283415] Early unpacking initramfs... done
[   20.628515] ACPI: Core revision 20070126
[   20.628597] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   20.631152] ACPI: setting ELCR to 0200 (from 0ca0)
[   20.635062] Using local APIC timer interrupts.
[   20.693561] result 12557141
[   20.693563] Detected 12.557 MHz APIC timer.
[   20.697449] SMP alternatives: switching to SMP code
[   20.697571] Booting processor 1/2 APIC 0x1
[   20.708133] Initializing CPU#1
[   20.709362] spurious 8259A interrupt: IRQ7.
[   20.785796] Calibrating delay using timer specific routine.. 3421.80 BogoMIPS (lpj=6843614)
[   20.785804] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   20.785807] CPU: L2 Cache: 256K (64 bytes/line)
[   20.785809] CPU 1/1 -> Node 0
[   20.785811] CPU: Physical Processor ID: 0
[   20.785813] CPU: Processor Core ID: 1
[   20.785894] AMD Athlon(tm) 64 X2 Dual Core Processor TK-53 stepping 01
[   20.789308] Brought up 2 CPUs
[   21.441307] migration_cost=115
[   21.441013] NET: Registered protocol family 16
[   21.441110] ACPI: bus type pci registered
[   21.441117] PCI: Using configuration type 1
[   21.442117] ACPI: EC: Look up EC in DSDT
[   21.442626] ACPI: EC: GPE=0x10, ports=0x66, 0x62
[   21.444234] ACPI: System BIOS is requesting _OSI(Linux)
[   21.444236] ACPI: Please test with "acpi_osi=!Linux"
[   21.444238] Please send dmidecode to linux-acpi@vger.kernel.org
[   21.444497] ACPI: Interpreter enabled
[   21.444499] ACPI: (supports S0 S3 S4 S5)
[   21.444518] ACPI: Using PIC for interrupt routing
[   21.453564] ACPI: EC: GPE=0x10, ports=0x66, 0x62
[   21.453669] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.453677] PCI: Probing PCI hardware (bus 00)
[   21.454671] PCI: Transparent bridge - 0000:00:10.0
[   21.454706] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.454817] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   21.454850] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   21.454885] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   21.490693] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   21.490877] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 *11 14 15)
[   21.491057] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   21.491234] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   21.491411] ACPI: PCI Interrupt Link [LK1E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   21.491589] ACPI: PCI Interrupt Link [LK2E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   21.491768] ACPI: PCI Interrupt Link [LK3E] (IRQs 5 7 9 10 *11 14 15)
[   21.491945] ACPI: PCI Interrupt Link [LK4E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   21.492125] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   21.492306] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 *10 11 14 15)
[   21.492485] ACPI: PCI Interrupt Link [LUS0] (IRQs 5 7 9 10 *11 14 15)
[   21.492697] ACPI: PCI Interrupt Link [LUS2] (IRQs 5 *7 9 10 11 14 15)
[   21.492877] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   21.493061] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   21.493241] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   21.493420] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   21.493598] ACPI: PCI Interrupt Link [LPID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   21.493786] ACPI: PCI Interrupt Link [LTID] (IRQs *5 7 9 10 11 14 15)
[   21.493966] ACPI: PCI Interrupt Link [LSI1] (IRQs 5 7 9 *10 11 14 15)
[   21.494097] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.494113] pnp: PnP ACPI init
[   21.494128] ACPI: bus type pnp registered
[   21.497133] pnp: PnP ACPI: found 13 devices
[   21.497136] ACPI: ACPI bus type pnp unregistered
[   21.497211] PCI: Using ACPI for IRQ routing
[   21.497215] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.497308] NET: Registered protocol family 8
[   21.497310] NET: Registered protocol family 20
[   21.497400] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   21.497406] hpet0: 3 32-bit timers, 25000000 Hz
[   21.498470] pnp: 00:00: iomem range 0xe0000000-0xefffffff could not be reserved
[   21.498478] pnp: 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
[   21.498482] pnp: 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   21.498486] pnp: 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[   21.498490] pnp: 00:01: iomem range 0xfed00000-0xfed00fff has been reserved
[   21.498497] pnp: 00:03: iomem range 0xe0000000-0xefffffff could not be reserved
[   21.498504] pnp: 00:04: ioport range 0x1000-0x107f has been reserved
[   21.498508] pnp: 00:04: ioport range 0x1080-0x10ff has been reserved
[   21.498511] pnp: 00:04: ioport range 0x1400-0x147f has been reserved
[   21.498514] pnp: 00:04: ioport range 0x1480-0x14ff has been reserved
[   21.498518] pnp: 00:04: ioport range 0x1800-0x187f has been reserved
[   21.498521] pnp: 00:04: ioport range 0x1880-0x18ff has been reserved
[   21.498524] pnp: 00:04: ioport range 0x2000-0x203f has been reserved
[   21.498878] PCI: Bridge: 0000:00:02.0
[   21.498881]   IO window: 4000-4fff
[   21.498885]   MEM window: b4000000-b5ffffff
[   21.498888]   PREFETCH window: d0000000-d01fffff
[   21.498891] PCI: Bridge: 0000:00:03.0
[   21.498893]   IO window: disabled.
[   21.498896]   MEM window: b6000000-b7ffffff
[   21.498899]   PREFETCH window: disabled.
[   21.498901] PCI: Bridge: 0000:00:10.0
[   21.498903]   IO window: disabled.
[   21.498906]   MEM window: disabled.
[   21.498908]   PREFETCH window: disabled.
[   21.498921] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   21.498928] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   21.498936] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   21.499012] NET: Registered protocol family 2
[   21.500568] Time: hpet clocksource has been installed.
[   21.540596] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   21.541041] TCP established hash table entries: 131072 (order: 9, 3145728 bytes)
[   21.543504] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   21.544287] TCP: Hash tables configured (established 131072 bind 65536)
[   21.544291] TCP reno registered
[   21.552659] checking if image is initramfs... it is
[   22.228073] Freeing initrd memory: 7207k freed
[   22.233286] Simple Boot Flag at 0x36 set to 0x1
[   22.234459] audit: initializing netlink socket (disabled)
[   22.234479] audit(1221259616.996:1): initialized
[   22.236736] VFS: Disk quotas dquot_6.5.1
[   22.236799] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   22.236906] io scheduler noop registered
[   22.236909] io scheduler anticipatory registered
[   22.236911] io scheduler deadline registered
[   22.237014] io scheduler cfq registered (default)
[   22.237037] Boot video device is 0000:00:05.0
[   22.452587] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   22.452612] assign_interrupt_mode Found MSI capability
[   22.452616] Allocate Port Service[0000:00:02.0:pcie00]
[   22.452688] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   22.452710] assign_interrupt_mode Found MSI capability
[   22.452712] Allocate Port Service[0000:00:03.0:pcie00]
[   22.486232] Real Time Clock Driver v1.12ac
[   22.486426] hpet_resources: 0xfed00000 is busy
[   22.486472] Linux agpgart interface v0.102 (c) Dave Jones
[   22.486474] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.487898] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.488166] input: Macintosh mouse button emulation as /class/input/input0
[   22.488254] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   22.505902] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.505910] serio: i8042 AUX port at 0x60,0x64 irq 12
[   22.506084] mice: PS/2 mouse device common for all mice
[   22.506239] TCP cubic registered
[   22.506299] NET: Registered protocol family 1
[   22.506521] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   22.506529] Freeing unused kernel memory: 300k freed
[   22.523533] input: AT Translated Set 2 keyboard as /class/input/input1
[   23.735143] AppArmor: AppArmor initialized<5>audit(1221259618.500:2):  type=1505 info="AppArmor initialized" pid=1272
[   23.743577] fuse init (API version 7.8)
[   23.749274] Failure registering capabilities with primary security module.
[   23.781082] ACPI: Thermal Zone [THRM] (59 C)
[   24.444050] usbcore: registered new interface driver usbfs
[   24.444079] usbcore: registered new interface driver hub
[   24.444105] usbcore: registered new device driver usb
[   24.445692] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 7
[   24.445697] PCI: setting IRQ 7 as level-triggered
[   24.445702] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 7 (level, low) -> IRQ 7
[   24.445831] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   24.445838] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   24.446050] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[   24.446086] ehci_hcd 0000:00:0b.1: debug port 1
[   24.446091] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   24.446101] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xb0005000
[   24.446108] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.446221] usb usb1: configuration #1 chosen from 1 choice
[   24.446253] hub 1-0:1.0: USB hub found
[   24.446261] hub 1-0:1.0: 8 ports detected
[   24.458761] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.458769] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.474294] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   24.482621] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   24.532084] SCSI subsystem initialized
[   24.539167] libata version 2.21 loaded.
[   24.554738] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 11
[   24.554745] PCI: setting IRQ 11 as level-triggered
[   24.554749] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 11 (level, low) -> IRQ 11
[   24.554925] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   24.554933] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   24.554994] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   24.555015] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xb0004000
[   24.612153] usb usb2: configuration #1 chosen from 1 choice
[   24.612196] hub 2-0:1.0: USB hub found
[   24.612208] hub 2-0:1.0: 8 ports detected
[   24.714532] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 10
[   24.714537] PCI: setting IRQ 10 as level-triggered
[   24.714541] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 10 (level, low) -> IRQ 10
[   24.714548] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   24.714558] forcedeth: using HIGHDMA
[   25.040963] usb 2-6: new low speed USB device using ohci_hcd and address 2
[   25.233687] eth0: forcedeth.c: subsystem: 0103c:30b7 bound to 0000:00:14.0
[   25.233879] sata_nv 0000:00:0e.0: version 3.4
[   25.233896] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[   25.234204] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 5
[   25.234207] PCI: setting IRQ 5 as level-triggered
[   25.234212] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 5 (level, low) -> IRQ 5
[   25.234381] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   25.234555] scsi0 : sata_nv
[   25.234614] scsi1 : sata_nv
[   25.234688] ata1: SATA max UDMA/133 cmd 0x00000000000130c0 ctl 0x00000000000130b6 bmdma 0x0000000000013090 irq 5
[   25.234693] ata2: SATA max UDMA/133 cmd 0x00000000000130b8 ctl 0x00000000000130b2 bmdma 0x0000000000013098 irq 5
[   25.254940] usb 2-6: configuration #1 chosen from 1 choice
[   25.269302] usbcore: registered new interface driver hiddev
[   25.275302] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[   25.275484] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-6
[   25.275502] usbcore: registered new interface driver usbhid
[   25.275506] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   25.700912] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   25.709166] ata1.00: ATA-7: ST980811AS, 3.BHD, max UDMA/100
[   25.709171] ata1.00: 156301488 sectors, multi 16: LBA48 
[   25.725054] ata1.00: configured for UDMA/100
[   26.036560] ata2: SATA link down (SStatus 0 SControl 300)
[   26.047382] scsi 0:0:0:0: Direct-Access     ATA      ST980811AS       3.BH PQ: 0 ANSI: 5
[   26.047295] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   26.047318] NFORCE-MCP51: chipset revision 241
[   26.047321] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   26.047326] NFORCE-MCP51: BIOS didn't set cable bits correctly. Enabling workaround.
[   26.047331] NFORCE-MCP51: 0000:00:0d.0 (rev f1) UDMA133 controller
[   26.047341]     ide0: BM-DMA at 0x3080-0x3087, BIOS settings: hda:DMA, hdb:pio
[   26.047350] Probing IDE interface ide0...
[   26.783314] hda: TSSTcorpCD/DVDW TS-L632D, ATAPI CD/DVD-ROM drive
[   27.455720] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   27.488421] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   27.488437] sd 0:0:0:0: [sda] Write Protect is off
[   27.488440] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.488457] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.488516] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   27.488525] sd 0:0:0:0: [sda] Write Protect is off
[   27.488528] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.488543] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.488548]  sda:<6>hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, DMA
[   27.505310] Uniform CD-ROM driver Revision: 3.20
[   27.506024]  sda1 sda2 < sda5 >
[   27.525914] sd 0:0:0:0: [sda] Attached SCSI disk
[   27.530645] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   27.805583] Attempting manual resume
[   27.805588] swsusp: Resume From Partition 8:5
[   27.805590] PM: Checking swsusp image.
[   27.805886] PM: Resume from disk failed.
[   27.846157] kjournald starting.  Commit interval 5 seconds
[   27.845622] EXT3-fs: mounted filesystem with ordered data mode.
[   42.578327] nvidia: module license 'NVIDIA' taints kernel.
[   42.835447] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 11
[   42.835453] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LK3E] -> GSI 11 (level, low) -> IRQ 11
[   42.835462] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   42.835688] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.12  Thu Jul 17 18:10:24 PDT 2008
[   42.835679] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.860515] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.999833] input: PC Speaker as /class/input/input3
[   43.115433] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   43.115465] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   43.941032] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   43.965378] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 10
[   43.965384] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 10 (level, low) -> IRQ 10
[   43.965524] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   44.003048] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   44.582723] lp: driver loaded but no devices found
[   44.701960] ndiswrapper version 1.45 loaded (smp=yes)
[   44.866508] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
[   44.868493] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   44.868571] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 9
[   44.868577] PCI: setting IRQ 9 as level-triggered
[   44.868581] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 9 (level, low) -> IRQ 9
[   44.868625] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   44.875352] ndiswrapper: using IRQ 9
[   45.228592] wlan0: ethernet device 00:1a:73:5b:1b:ca using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[   45.228634] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   45.228703] usbcore: registered new interface driver ndiswrapper
[   45.362162] Adding 2819368k swap on /dev/sda5.  Priority:-1 extents:1 across:2819368k
[   45.448672] ACPI: AC Adapter [ACAD] (on-line)
[   46.112130] EXT3 FS on sda1, internal journal
[   47.503183] audit(1221259643.175:3):  type=1505 operation="profile_load" info="failed to unpack profile" name="/usr/lib/cups/backend/cups-pdf" pid=4368
[   47.765421] ip_tables: (C) 2000-2006 Netfilter Core Team
```

---

### Post by IntuitiveNipple on 2008-09-12
What you need to do is remove the splash-screen and quiet options when booting so you get to see more kernel messages. You can do that from the GrUB menu when the PC starts. That should enable you to see more messages than the "Loading hardware drivers" that is generated by the init scripts.

When it hangs you can then either photograph or copy the last few lines which *should* give a clue as to what is causing the lock-up.

---

### Post by IntuitiveNipple on 2008-09-12
Just a pointer to what *might* be causing this issue. It is a dual-core/CPU system. Each core/CPU has its own APIC (Advanced Programmable Interrupt Controller), referred to as the **lapic** (Local APIC).

It is known that on SMP (Symmetrical Multi-Processor) systems in some circumstances interrupts meant for one CPU can end up on another CPU which doesn't know what to do and panics, causing a lock-up.

You could try using the **nolapic** setting (see the kernel [Documentation/kernel-parameters.txt](http://lxr.linux.no/linux+v2.6.24.7/Documentation/kernel-parameters.txt#L1194)). Also, look at the associated options such as **lapic**.

---

### Post by offchance on 2008-09-12
> **IntuitiveNipple said:**
> What you need to do is remove the splash-screen and quiet options when booting so you get to see more kernel messages. You can do that from the GrUB menu when the PC starts. That should enable you to see more messages than the "Loading hardware drivers" that is generated by the init scripts.

When it hangs you can then either photograph or copy the last few lines which *should* give a clue as to what is causing the lock-up.
when I boot w/o quiet and w/o splash the last thing it shows is "*Loading hardware drivers," that's it. 

booting with nolapic alone results in a freeze or no x configuration.

I will give those commands on that list a shot. thanks for pointing those out.

---

### Post by ice2921 on 2008-09-12
IntuitiveNipple appears to more knowlable in this area than I am but, you may want to check this link out for available boot options. [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions). Hope is helps.

---

### Post by offchance on 2008-09-23
Looks like the kernel boot commands are not consistently helping with the problem. The computer still freezes on a regular basis. 

Could it be a problem with the kernel? The Hardy upgrade still only comes with version .15, while most other distributions are using the .25 or greater versions of the linux kernel. What's the deal? And could this be part of my problem?

---

### Post by offchance on 2008-10-01
Solved by a fresh install from cd. The updated kernel appears to be the fix I needed.

---

