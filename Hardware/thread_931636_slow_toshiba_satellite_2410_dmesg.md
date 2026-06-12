---
title: "slow toshiba satellite 2410 dmesg"
date: 2008-09-27
forum: Hardware
---

### Post by Bucky Ball on 2008-09-27
Hi. This machine belongs to a friend looking to convert from Windows and has 512mb ram and GeForce4 420 Go vid card.

```

tim@ubuntu:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
[    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000001ffd0000 - 000000001ffe0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffe0000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131024) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131024
[    0.000000]   HighMem    131024 ->   131024
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131024
[    0.000000] On node 0 totalpages: 131024
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125937 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F0180 checksum 0
[    0.000000] ACPI: RSDP 000F0180, 0014 (r0 TOSHIB)
[    0.000000] ACPI: RSDT 1FFD0000, 0030 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: FACP 1FFD0058, 0084 (r2 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: DSDT 1FFD0110, 5487 (r1 TOSHIB 2410     20020918 MSFT  100000A)
[    0.000000] ACPI: FACS 000EEE00, 0040
[    0.000000] ACPI: DBGP 1FFD00DC, 0034 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: BOOT 1FFD0030, 0028 (r1 TOSHIB 750        970814 TASM  4010000)
[    0.000000] ACPI: DMI detected: Toshiba
[    0.000000] ACPI: PM-Timer IO Port: 0xee08
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:deda0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 00000000000ee000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ee000 - 00000000000ef000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ef000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130001
[    0.000000] Kernel command line: root=UUID=54a2b662-b5fd-4040-85c0-7eccca024be9 ro
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0140d000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1992.958 MHz processor.
[ 1051.189836] Console: colour VGA+ 80x25
[ 1051.189899] console [tty0] enabled
[ 1051.216790] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 1051.220379] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 1051.347104] Memory: 507524k/524096k available (2177k kernel code, 15960k reserved, 1006k data, 368k init, 0k highmem)
[ 1051.347909] virtual kernel memory layout:
[ 1051.347910]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[ 1051.347939]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[ 1051.347941]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[ 1051.347942]     lowmem  : 0xc0000000 - 0xdffd0000   ( 511 MB)
[ 1051.347972]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[ 1051.347973]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[ 1051.348002]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[ 1051.351904] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 1051.353287] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[ 1051.434020] Calibrating delay using timer specific routine.. 4023.82 BogoMIPS (lpj=8047640)
[ 1051.435277] Security Framework initialized
[ 1051.435854] SELinux:  Disabled at boot.
[ 1051.436497] AppArmor: AppArmor initialized
[ 1051.437015] Failure registering capabilities with primary security module.
[ 1051.437599] Mount-cache hash table entries: 512
[ 1051.439783] Initializing cgroup subsys ns
[ 1051.440331] Initializing cgroup subsys cpuacct
[ 1051.440943] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00000400 00000000 00000000 00000000
[ 1051.441101] CPU: Trace cache: 12K uops, L1 D cache: 8K
[ 1051.442096] CPU: L2 cache: 512K
[ 1051.442613] CPU: Hyper-Threading is disabled
[ 1051.443129] CPU: After all inits, caps: bfebf9ff 00000000 00000000 0000b080 00000400 00000000 00000000 00000000
[ 1051.443287] Compat vDSO mapped to ffffe000.
[ 1051.443901] Checking 'hlt' instruction... OK.
[ 1051.463039] SMP alternatives: switching to UP code
[ 1051.483137] Freeing SMP alternatives: 11k freed
[ 1051.485292] Early unpacking initramfs... done
[ 1055.539828] ACPI: Core revision 20070126
[ 1055.541292] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[ 1055.563733] ACPI: setting ELCR to 0200 (from 0e00)
[ 1055.566298] CPU0: Intel Mobile Intel(R) Pentium(R) 4 - M CPU 2.00GHz stepping 07
[ 1055.569662] SMP motherboard not detected.
[ 1055.570756] Local APIC not detected. Using dummy APIC emulation.
[ 1055.573141] Brought up 1 CPUs
[ 1055.573819] CPU0 attaching sched-domain:
[ 1055.573852]  domain 0: span 01
[ 1055.573883]   groups: 01
[ 1055.576468] net_namespace: 64 bytes
[ 1055.577174] Booting paravirtualized kernel on bare hardware
[ 1055.586076] Time:  3:40:52  Date: 09/28/08
[ 1055.586941] NET: Registered protocol family 16
[ 1055.590510] EISA bus registered
[ 1055.591126] ACPI: bus type pci registered
[ 1055.593819] PCI: PCI BIOS revision 2.10 entry at 0xfd4df, last bus=5
[ 1055.594368] PCI: Using configuration type 1
[ 1055.594920] Setting up standard PCI resources
[ 1055.629904] ACPI: EC: Look up EC in DSDT
[ 1055.664013] ACPI: Interpreter enabled
[ 1055.665208] ACPI: (supports S0 S3 S4 S5)
[ 1055.668414] ACPI: Using PIC for interrupt routing
[ 1055.736998] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 1055.741188] PCI quirk: region ee00-ee7f claimed by ICH4 ACPI/GPIO/TCO
[ 1055.741767] PCI quirk: region eec0-eeff claimed by ICH4 GPIO
[ 1055.748991] PCI: Transparent bridge - 0000:00:1e.0
[ 1055.750864] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 1055.751243] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[ 1055.752027] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[ 1055.770046] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *11)
[ 1055.774680] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *11)
[ 1055.780527] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *11)
[ 1055.785034] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *11)
[ 1055.789387] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *11)
[ 1055.793771] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 *11)
[ 1055.798123] ACPI: PCI Interrupt Link [LNKG] (IRQs *10)
[ 1055.801091] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 *11)
[ 1055.806834] ACPI: Power Resource [PFAN] (off)
[ 1055.807979] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 1055.809061] pnp: PnP ACPI init
[ 1055.809643] ACPI: bus type pnp registered
[ 1055.829224] pnpacpi: exceeded the max number of IO resources: 40 
[ 1055.870101] pnp: PnP ACPI: found 12 devices
[ 1055.870620] ACPI: ACPI bus type pnp unregistered
[ 1055.871139] PnPBIOS: Disabled by ACPI PNP
[ 1055.874957] PCI: Using ACPI for IRQ routing
[ 1055.875449] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[ 1055.944540] NET: Registered protocol family 8
[ 1055.945057] NET: Registered protocol family 20
[ 1055.946491] AppArmor: AppArmor Filesystem Enabled
[ 1055.948421] Time: tsc clocksource has been installed.
[ 1055.956981] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[ 1055.957503] system 00:00: iomem range 0xe0000-0xeffff could not be reserved
[ 1055.958052] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[ 1055.958572] system 00:00: iomem range 0x100000-0x1ffcffff could not be reserved
[ 1055.959162] system 00:00: iomem range 0x1ffd0000-0x1ffdffff could not be reserved
[ 1055.959752] system 00:00: iomem range 0x1ffe0000-0x1fffffff could not be reserved
[ 1055.960437] system 00:00: iomem range 0xfeda0000-0xfedbffff could not be reserved
[ 1055.961028] system 00:00: iomem range 0xffb80000-0xffbfffff could not be reserved
[ 1055.961618] system 00:00: iomem range 0xfff00000-0xffffffff could not be reserved
[ 1055.962362] system 00:08: ioport range 0x1e0-0x1ef has been reserved
[ 1055.962883] system 00:08: ioport range 0x480-0x48f has been reserved
[ 1055.963404] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[ 1055.963923] system 00:08: ioport range 0x680-0x6ff has been reserved
[ 1055.964507] system 00:08: ioport range 0xe000-0xe07f has been reserved
[ 1055.965055] system 00:08: ioport range 0xe080-0xe0ff has been reserved
[ 1055.965574] system 00:08: ioport range 0xe400-0xe47f has been reserved
[ 1055.966097] system 00:08: ioport range 0xe480-0xe4ff has been reserved
[ 1055.966616] system 00:08: ioport range 0xe800-0xe87f has been reserved
[ 1055.967136] system 00:08: ioport range 0xe880-0xe8ff has been reserved
[ 1055.968388] system 00:08: ioport range 0xec00-0xec7f has been reserved
[ 1055.969668] system 00:08: ioport range 0xec80-0xecff has been reserved
[ 1055.970217] system 00:08: ioport range 0xee00-0xee87 could not be reserved
[ 1056.007165] PCI: Bridge: 0000:00:01.0
[ 1056.007681]   IO window: disabled.
[ 1056.008199]   MEM window: fd000000-fdffffff
[ 1056.008782]   PREFETCH window: dbf00000-dfffffff
[ 1056.009523] PCI: Bus 3, cardbus bridge: 0000:02:0b.0
[ 1056.010012]   IO window: 0000d000-0000d0ff
[ 1056.010532]   IO window: 0000d400-0000d4ff
[ 1056.011051]   PREFETCH window: 34000000-37ffffff
[ 1056.011569]   MEM window: 38000000-3bffffff
[ 1056.012088] PCI: Bus 5, cardbus bridge: 0000:02:0b.1
[ 1056.012640]   IO window: 0000d800-0000d8ff
[ 1056.013158]   IO window: 0000dc00-0000dcff
[ 1056.013676]   PREFETCH window: 3c000000-3fffffff
[ 1056.014194]   MEM window: 40000000-43ffffff
[ 1056.014713] PCI: Bridge: 0000:00:1e.0
[ 1056.015200]   IO window: d000-dfff
[ 1056.015719]   MEM window: fce00000-fcefffff
[ 1056.016237]   PREFETCH window: disabled.
[ 1056.016947] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[ 1056.017168] PCI: Enabling device 0000:02:0b.0 (0000 -> 0003)
[ 1056.020168] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[ 1056.020812] PCI: setting IRQ 11 as level-triggered
[ 1056.020872] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 1056.022362] PCI: Enabling device 0000:02:0b.1 (0000 -> 0003)
[ 1056.024953] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[ 1056.025500] ACPI: PCI Interrupt 0000:02:0b.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[ 1056.026990] NET: Registered protocol family 2
[ 1056.065295] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[ 1056.077438] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[ 1056.078944] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[ 1056.080447] TCP: Hash tables configured (established 16384 bind 16384)
[ 1056.080967] TCP reno registered
[ 1056.094022] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[ 1059.905739]  it is
[ 1064.097568] Freeing initrd memory: 7317k freed
[ 1064.104374] Simple Boot Flag at 0x7c set to 0x1
[ 1064.109364] audit: initializing netlink socket (disabled)
[ 1064.110045] audit(1222573260.756:1): initialized
[ 1064.141573] VFS: Disk quotas dquot_6.5.1
[ 1064.143512] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 1064.145761] io scheduler noop registered
[ 1064.146307] io scheduler anticipatory registered
[ 1064.146923] io scheduler deadline registered
[ 1064.147566] io scheduler cfq registered (default)
[ 1064.150084] Boot video device is 0000:01:00.0
[ 1064.150176] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[ 1064.154765] isapnp: Scanning for PnP cards...
[ 1064.521370] isapnp: No Plug & Play device found
[ 1064.950232] Real Time Clock Driver v1.12ac
[ 1064.952165] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 1064.961473] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
[ 1064.962370] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[ 1064.963762] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[ 1064.973694] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 1064.975229] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[ 1064.977388] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[ 1064.988465] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 1064.990610] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 1065.006561] mice: PS/2 mouse device common for all mice
[ 1065.008682] EISA: Probing bus 0 at eisa.0
[ 1065.009203] Cannot allocate resource for EISA slot 1
[ 1065.010008] EISA: Detected 0 cards.
[ 1065.011515] cpuidle: using governor ladder
[ 1065.012031] cpuidle: using governor menu
[ 1065.013936] NET: Registered protocol family 1
[ 1065.014801] Using IPI No-Shortcut mode
[ 1065.015758] registered taskstats version 1
[ 1065.017694]   Magic number: 8:570:665
[ 1065.019690] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 1065.020237] EDD information not available.
[ 1065.024652] Freeing unused kernel memory: 368k freed
[ 1065.055274] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[ 1067.619247] fuse init (API version 7.9)
[ 1067.815726] ACPI: Transitioning device [FAN] to D3
[ 1067.816308] ACPI: Transitioning device [FAN] to D3
[ 1067.816988] ACPI: Fan [FAN] (off)
[ 1067.897591] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[ 1067.917062] ACPI: Thermal Zone [THRM] (51 C)
[ 1073.387576] usbcore: registered new interface driver usbfs
[ 1073.388631] usbcore: registered new interface driver hub
[ 1073.448321] usbcore: registered new device driver usb
[ 1074.376637] SCSI subsystem initialized
[ 1074.430707] USB Universal Host Controller Interface driver v3.0
[ 1074.437502] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 1074.439268] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[ 1074.439331] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 1074.444008] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[ 1074.444912] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000efe0
[ 1074.447507] usb usb1: configuration #1 chosen from 1 choice
[ 1074.448464] hub 1-0:1.0: USB hub found
[ 1074.449043] hub 1-0:1.0: 2 ports detected
[ 1074.634612] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[ 1074.635198] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[ 1074.636649] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[ 1074.636711] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 1074.637955] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[ 1074.638767] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000ef80
[ 1074.644599] usb usb2: configuration #1 chosen from 1 choice
[ 1074.645466] hub 2-0:1.0: USB hub found
[ 1074.646204] hub 2-0:1.0: 2 ports detected
[ 1076.103515] libata version 3.00 loaded.
[ 1076.342836] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[ 1076.343609] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[ 1076.345451] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[ 1076.345638] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[ 1076.770740] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[ 1076.771324] e100: Copyright(c) 1999-2006 Intel Corporation
[ 1076.833755] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[ 1076.834591] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[ 1079.191995] e100: eth0: e100_probe: addr 0xfceff000, irq 11, MAC addr 00:08:0d:63:b2:5f
[ 1079.192956] ata_piix 0000:00:1f.1: version 2.12
[ 1079.193209] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[ 1079.195233] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[ 1079.254035] scsi0 : ata_piix
[ 1079.324447] scsi1 : ata_piix
[ 1079.331290] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xcfa0 irq 14
[ 1079.331842] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xcfa8 irq 15
[ 1079.497181] ata1.00: ATA-7: SAMSUNG HM080HC, AM100-16, max UDMA/100
[ 1079.497951] ata1.00: 156301488 sectors, multi 0: LBA48 
[ 1079.508849] ata1.00: configured for UDMA/100
[ 1079.871972] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-C2612, 1315, max UDMA/33
[ 1080.103402] ata2.00: configured for UDMA/33
[ 1080.105780] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM080HC  AM10 PQ: 0 ANSI: 5
[ 1080.117785] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-C2612 1315 PQ: 0 ANSI: 5
[ 1080.125419] PCI: Enabling device 0000:02:07.0 (0000 -> 0002)
[ 1080.128675] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[ 1080.129381] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[ 1080.183010] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fce06000-fce067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[ 1080.756445] Floppy drive(s): fd0 is 1.44M
[ 1080.782510] FDC 0 is a post-1991 82077
[ 1081.879591] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00003900003c2ff6]
[ 1088.811087] Driver 'sd' needs updating - please use bus_type methods
[ 1088.812774] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[ 1088.813481] sd 0:0:0:0: [sda] Write Protect is off
[ 1088.813971] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1088.814505] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1088.826172] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[ 1088.827290] sd 0:0:0:0: [sda] Write Protect is off
[ 1088.827809] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1088.851699] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1088.852414]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[ 1089.462024]  sda1 sda2 < sda5 sda6 >
[ 1089.503740] sd 0:0:0:0: [sda] Attached SCSI disk
[ 1089.564490] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[ 1089.565133] Uniform CD-ROM driver Revision: 3.20
[ 1089.566504] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 1089.667787] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 1089.668622] sr 1:0:0:0: Attached scsi generic sg1 type 5
[ 1091.181793] Attempting manual resume
[ 1091.182312] swsusp: Resume From Partition 8:6
[ 1091.182343] PM: Checking swsusp image.
[ 1091.183924] PM: Resume from disk failed.
[ 1091.479477] kjournald starting.  Commit interval 5 seconds
[ 1091.480243] EXT3-fs: mounted filesystem with ordered data mode.
[ 1109.416998] Clocksource tsc unstable (delta = -122247109 ns)
[ 1109.420950] Time: acpi_pm clocksource has been installed.
[ 1122.011665] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 1122.388552] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 1123.393393] iTCO_vendor_support: vendor-support=0
[ 1123.623645] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[ 1123.626212] iTCO_wdt: Found a ICH3-M TCO device (Version=1, TCOBASE=0xee60)
[ 1123.627328] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[ 1124.241892] input: PC Speaker as /devices/platform/pcspkr/input/input2
[ 1132.519731] ACPI: AC Adapter [ADP1] (on-line)
[ 1132.859010] input: Power Button (FF) as /devices/virtual/input/input3
[ 1132.868437] ACPI: Power Button (FF) [PWRF]
[ 1132.870530] input: Lid Switch as /devices/virtual/input/input4
[ 1132.871802] ACPI: Lid Switch [LID]
[ 1133.231862] ACPI: Battery Slot [BAT1] (battery present)
[ 1152.306146] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/LNXVIDEO:00/input/input5
[ 1152.386053] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[ 1154.040368] Yenta: CardBus bridge found at 0000:02:0b.0 [1179:0001]
[ 1154.169773] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[ 1154.170355] Socket status: 30000007
[ 1154.170901] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[ 1154.171609] cs: IO port probe 0xd000-0xdfff: clean.
[ 1154.174934] pcmcia: parent PCI bridge Memory window: 0xfce00000 - 0xfcefffff
[ 1154.250328] Yenta: CardBus bridge found at 0000:02:0b.1 [1179:0001]
[ 1154.381786] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[ 1154.382369] Socket status: 30000007
[ 1154.382885] Yenta: Raising subordinate bus# of parent bus (#02) from #05 to #08
[ 1154.383695] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[ 1154.384274] cs: IO port probe 0xd000-0xdfff: clean.
[ 1154.387757] pcmcia: parent PCI bridge Memory window: 0xfce00000 - 0xfcefffff
[ 1155.254486] Linux agpgart interface v0.102
[ 1157.220905] input: PS/2 Mouse as /devices/virtual/input/input6
[ 1157.258557] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input7
[ 1158.893383] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 1166.410385] parport_pc 00:0b: activated
[ 1166.411101] parport_pc 00:0b: reported by Plug and Play ACPI
[ 1166.416427] parport_pc 00:0b: disabled
[ 1166.781827] NET: Registered protocol family 17
[ 1167.306329] irda_init()
[ 1167.306610] NET: Registered protocol family 23
[ 1167.507635] Detected unconfigured Toshiba laptop with Intel 82801CAM ISA bridge SMSC IrDA chip, pre-configuring device.
[ 1167.508383] Setting up Intel 82801 controller and SMSC device
[ 1167.509030] Detected Chip id: 0x5a, setting up registers...
[ 1167.510242] found SMC SuperIO Chip (devid=0x5a rev=00 base=0x002e): LPC47N227
[ 1167.510919] smsc_superio_flat(): fir: 0x130, sir: 0x3f8, dma: 03, irq: 3, mode: 0x0a
[ 1167.511635] SMsC IrDA Controller found
[ 1167.511636]  IrCC version 2.0, firport 0x130, sirport 0x3f8 dma=3, irq=3
[ 1167.530169] smsc_ircc_set_sir_speed(), Setting speed to: 9600
[ 1167.530327] No transceiver found. Defaulting to Fast pin select
[ 1167.557784] IrDA: Registered device irda0
[ 1179.223833] PCI: Enabling device 0000:00:1f.5 (0000 -> 0001)
[ 1179.224508] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[ 1179.226186] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[ 1179.897147] intel8x0_measure_ac97_clock: measured 53566 usecs
[ 1179.897729] intel8x0: clocking to 48000
[ 1186.441439] cs: IO port probe 0x100-0x3af: clean.
[ 1186.453657] cs: IO port probe 0x3e0-0x4ff: clean.
[ 1186.459172] cs: IO port probe 0x820-0x8ff: clean.
[ 1186.510114] cs: IO port probe 0x100-0x3af: clean.
[ 1186.522438] cs: IO port probe 0x3e0-0x4ff: clean.
[ 1186.528424] cs: IO port probe 0x820-0x8ff: clean.
[ 1186.533560] cs: IO port probe 0xc00-0xcf7: clean.
[ 1186.633012] cs: IO port probe 0xc00-0xcf7: clean.
[ 1186.718295] cs: IO port probe 0xa00-0xaff: clean.
[ 1186.766216] cs: IO port probe 0xa00-0xaff: clean.
[ 1194.808009] loop: module loaded
[ 1195.256528] lp: driver loaded but no devices found
[ 1196.042722] Adding 1510068k swap on /dev/sda6.  Priority:-1 extents:1 across:1510068k
[ 1197.101619] EXT3 FS on sda1, internal journal
[ 1199.949628] NET: Registered protocol family 10
[ 1199.965662] lo: Disabled Privacy Extensions
[ 1200.688311] kjournald starting.  Commit interval 5 seconds
[ 1200.689573] EXT3 FS on sda5, internal journal
[ 1200.689608] EXT3-fs: mounted filesystem with ordered data mode.
[ 1204.973220] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 1210.502919] eth0: no IPv6 routers present
[ 1211.678330] No dock devices found.
[ 1212.215808] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[ 1212.215871] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
[ 1212.220535] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[ 1212.220567] toshiba_acpi: ktoshkeyd will check 2 times per second
[ 1212.237637] toshiba_acpi: Dropped 0 keys from the queue on startup
[ 1221.384612] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[ 1221.384676] apm: overridden by ACPI.
[ 1222.175819] ppdev: user-space parallel port driver
[ 1222.496603] audit(1222539220.573:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5500 profile="/usr/sbin/cupsd" namespace="default"
[ 2061.562272] Marking TSC unstable due to: cpufreq changes.
```

---

### Post by IntuitiveNipple on 2008-09-27
I suspect you need to force the **clocksource** on the kernel's command-line (set in the GRUB menu or via the file /boot/grub/menu.lst):
```

	clocksource=	[GENERIC_TIME] Override the default clocksource
			Format: <string>
			Override the default clocksource and use the clocksource
			with the name specified.
			Some clocksource names to choose from, depending on
			the platform:
			[all] jiffies (this is the base, fallback clocksource)
			[ACPI] acpi_pm
			[ARM] imx_timer1,OSTS,netx_timer,mpu_timer2,
				pxa_timer,timer3,32k_counter,timer0_1
			[AVR32] avr32
			[X86-32] pit,hpet,tsc,vmi-timer;
				scx200_hrt on Geode; cyclone on IBM x440
			[MIPS] MIPS
			[PARISC] cr16
			[S390] tod
			[SH] SuperH
			[SPARC64] tick
			[X86-64] hpet,tsc

```
Try **clocksource=tsc** or **pit**

---

### Post by Bucky Ball on 2008-09-27
No change.

---

### Post by IntuitiveNipple on 2008-09-27
I noticed this:
```

[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"

```
Check the system BIOS for any option to enable *Advanced Programmable Interrupt Controller* or add **lapic** to the kernel command-line.

---

### Post by Bucky Ball on 2008-09-27
Nice thought and just what I am looking for, some fresh ideas. But unfortunately no different. Changed in the kernel line, couldn't find anything in BIOS.

When the block slides back and to before loading progress bar, makes it up about halfway through the first time then gets stutters and flickering and slow, does that for a bit, then back to normal. Progress bar itself takes forever to crawl up. Strange thing is, all seems to be working okay, just so slow is unusable.

[QUOTE=IntuitiveNipple]Check the system BIOS for any option to enable *Advanced Programmable Interrupt Controller* or add **lapic** to the kernel command-line.[/QUOTE]

None such in the BIOS

---

### Post by IntuitiveNipple on 2008-09-27
The explanation is right there in the log-file. Look at the time-stamp of the messages. There is a big difference between:
```

[    0.000000] Detected 1992.958 MHz processor.
[ 1051.189836] Console: colour VGA+ 80x25

```
After that differences between the messages are as expected.

There is further confirmation at the end of the log-file with:
```

[ 1222.496603] audit(1222539220.573:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5500 profile="/usr/sbin/cupsd" namespace="default"
[ 2061.562272] Marking TSC unstable due to: cpufreq changes.

```
Here's a comparison:
```

[    0.000000] Kernel command line: root=/dev/mapper/VGencrypted-root ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   16.182650] Marking TSC unstable due to TSCs unsynchronized
[   16.182652] time.c: Detected 1995.002 MHz processor.
[   16.185515] Console: colour VGA+ 80x25
[   16.185519] console [tty0] enabled

```
What might be more revealing is to remove the current /var/log/kern.log and reboot so it is recorded fresh, and then attach a (compressed) copy of that here:
```

cd ~
cat /var/log/kern.log | gzip > kern.log.gz

```
That will show messages after dmesg stops logging.

---

### Post by Bucky Ball on 2008-09-27
[quote=IntuitiveNipple]Console: colour VGA+ 80x25[/quote]

Ah ha! The plot thickens and I draw forever closer to the source of this enigma ...

Thinks I follow what you're saying
The first positive lead I've had in 3 days ... thanks.

[[quote=IntuitiveNipple]attach a (compressed) copy of that here[/QUOTE] :)

Like I say, that could take some time. "(

---

### Post by Bucky Ball on 2008-09-27
I've run these commands:

cd ~
cat /var/log/kern.log | gzip > kern.log.gz

But now how do I post it? Where is it saved to?

No matter, here it is:

Thanks for guiding me through it. I can see in point form at the moment but not quite getting the bigger picture.

---

### Post by IntuitiveNipple on 2008-09-27
> **Bucky Ball said:**
> Thanks for guiding me through it. I can see in point form at the moment but not quite getting the bigger picture.
The trick is to reduce the scope of the problem using the log files and so forth.

That kern.log is helpful but could you do another one. Follow the same procedure (delete the existing kern.log before rebooting) but when the system reboots go into the GRUB menu, edit the kernel command-line to remove "quiet splash" and *add* **lapic**.

Compress the resulting /var/log/kern.log and attach it to a reply as before. Hopefully it will give a clue.

At the same time, also compress and attach the file **/var/log/messages**.

---

### Post by Bucky Ball on 2008-09-27
Hope these are some good to you. Thanks for your time with this. These are with the grub minus 'quiet splash' and lapic added. :)



```
tim@ubuntu:/etc/init.d$ dir
acpid                 mountnfs-bootclean.sh
acpi-support             mountoverflowtmp
alsa-utils             mtab.sh
anacron                 networking
apmd                 nvidia-kernel
apparmor             pcmciautils
apport                 policykit
atd                 powernowd
avahi-daemon             powernowd.early
bluetooth             pppd-dns
bootclean             procps
bootlogd             pulseaudio
bootmisc.sh             rc
brltty                 rc.local
checkfs.sh             rcS
checkroot.sh             readahead
console-screen.sh         readahead-desktop
console-setup             README
cron                 reboot
cupsys                 rmnologin
dbus                 rsync
dhcdbd                 screen-cleanup
dns-clean             sendsigs
gdm                 single
glibc.sh             skeleton
hal                 stop-bootlogd
halt                 stop-bootlogd-single
hostname.sh             stop-readahead
hotkey-setup             sysklogd
hwclockfirst.sh             udev
hwclock.sh             udev-finish
keyboard-setup             ufw
killprocs             umountfs
klogd                 umountnfs.sh
laptop-mode             umountroot
linux-restricted-modules-common  urandom
loopback             usplash
module-init-tools         vbesave
mountall-bootclean.sh         waitnfs.sh
mountall.sh             wpa-ifupdown
mountdevsubfs.sh         x11-common
mountkernfs.sh             xserver-xorg-input-wacom
```

```
Tasks:  98 total,   1 running,  97 sleeping,   0 stopped,   0 zombie
Cpu(s): 21.0%us,  5.3%sy,  0.8%ni, 71.9%id,  0.7%wa,  0.2%hi,  0.1%si,  0.0%
Mem:    515452k total,   443532k used,    71920k free,    18712k buffers
Swap:  1510068k total,      172k used,  1509896k free,   236328k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND        
 5764 root      20   0 54108  13m 7572 S 12.2  2.7   5:23.38 Xorg           
 9002 tim       20   0  2304 1004  764 R  8.1  0.2   0:00.16 top            
   44 root      15  -5     0    0    0 S  2.7  0.0   0:01.36 kacpid         
 2888 root      16  -4  2404  948  380 S  2.7  0.2   0:11.14 udevd          
 5211 root      20   0  2456 1368  692 S  2.7  0.3   0:02.76 acpid          
 5615 haldaemo  20   0  6192 4200 3572 S  2.7  0.8   0:13.76 hald           
 6062 tim       20   0 36440  19m  12m S  1.4  3.9   1:04.81 gnome-panel    
 6118 tim       20   0 25352  11m 8020 S  1.4  2.3   1:09.40 nm-applet      
 8872 tim       20   0  124m  48m  20m S  1.4  9.6   1:49.74 firefox        
    1 root      20   0  2844 1688  544 S  0.0  0.3   0:09.82 init           
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kthreadd       
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0    
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0    
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0     
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.80 events/0    
```

---

