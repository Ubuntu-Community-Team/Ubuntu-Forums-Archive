---
title: "Synaptics touchpad does not work after upgrading to Hardy"
date: 2008-10-07
forum: Hardware
---

### Post by bdw on 2008-10-07
:confused:
I upgraded to Hardy Heron from Gutsy Gibbon and now the Synaptics Touchpad will not work.  It did work before but now won't work.  The Logitech USB wireless mouse works OK.  It appears that /dev/wacom is not present so the touchpad will not work.  The touchpad is detected by the kernel and X.

The laptop is an Asus S96J.

The dmesg file:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Aug 25 17:32:09 UTC 2008 (Ubuntu 2.6.24-21.42-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffbe000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 524208) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524208
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524208
[    0.000000] On node 0 totalpages: 524208
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292529 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00FB720 checksum 0
[    0.000000] ACPI: RSDP 000FB720, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FFB0000, 0038 (r1 A M I  OEMRSDT   8000629 MSFT       97)
[    0.000000] ACPI: FACP 7FFB0200, 0084 (r2 A M I  OEMFACP   8000629 MSFT       97)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000820/0 [20070126]
[    0.000000] ACPI: DSDT 7FFB0430, 600E (r1  A0504 A0504000        0 INTL 20060113)
[    0.000000] ACPI: FACS 7FFBE000, 0040
[    0.000000] ACPI: APIC 7FFB0390, 005C (r1 A M I  OEMAPIC   8000629 MSFT       97)
[    0.000000] ACPI: MCFG 7FFB03F0, 003C (r1 A M I  OEMMCFG   8000629 MSFT       97)
[    0.000000] ACPI: OEMB 7FFBE040, 0060 (r1 A M I  AMI_OEM   8000629 MSFT       97)
[    0.000000] ACPI: TCPA 7FFB6440, 0032 (r1 A M I  TBLOEMID        1 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520113
[    0.000000] Kernel command line: root=UUID=a03cc65e-59e4-45fb-8ca3-d91e85d276d8 ro quiet splash vga=771
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1662.599 MHz processor.
[   12.973822] Console: colour dummy device 80x25
[   12.973826] console [tty0] enabled
[   12.974081] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   12.974374] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   13.070363] Memory: 2066432k/2096832k available (2177k kernel code, 29104k reserved, 1006k data, 368k init, 1179328k highmem)
[   13.070370] virtual kernel memory layout:
[   13.070371]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   13.070372]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.070373]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   13.070374]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   13.070375]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   13.070376]       .data : 0xc0320514 - 0xc041bdc4   (1006 kB)
[   13.070377]       .text : 0xc0100000 - 0xc0320514   (2177 kB)
[   13.070381] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.070423] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   13.150332] Calibrating delay using timer specific routine.. 3329.20 BogoMIPS (lpj=6658400)
[   13.150361] Security Framework initialized
[   13.150367] SELinux:  Disabled at boot.
[   13.150381] AppArmor: AppArmor initialized
[   13.150385] Failure registering capabilities with primary security module.
[   13.150394] Mount-cache hash table entries: 512
[   13.150525] Initializing cgroup subsys ns
[   13.150530] Initializing cgroup subsys cpuacct
[   13.150541] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   13.150549] monitor/mwait feature present.
[   13.150550] using mwait in idle threads.
[   13.150554] CPU: L1 I cache: 32K, L1 D cache: 32K
[   13.150556] CPU: L2 cache: 2048K
[   13.150559] CPU: Physical Processor ID: 0
[   13.150561] CPU: Processor Core ID: 0
[   13.150563] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
[   13.150572] Compat vDSO mapped to ffffe000.
[   13.150586] Checking 'hlt' instruction... OK.
[   13.166713] SMP alternatives: switching to UP code
[   13.168391] Early unpacking initramfs... done
[   13.529489] ACPI: Core revision 20070126
[   13.529537] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   13.544281] CPU0: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[   13.544297] SMP alternatives: switching to SMP code
[   13.545028] Booting processor 1/1 eip 3000
[   13.555240] Initializing CPU#1
[   13.633619] Calibrating delay using timer specific routine.. 3325.26 BogoMIPS (lpj=6650531)
[   13.633626] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   13.633631] monitor/mwait feature present.
[   13.633634] CPU: L1 I cache: 32K, L1 D cache: 32K
[   13.633635] CPU: L2 cache: 2048K
[   13.633637] CPU: Physical Processor ID: 0
[   13.633639] CPU: Processor Core ID: 1
[   13.633640] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
[   13.634170] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[   13.634192] Total of 2 processors activated (6654.46 BogoMIPS).
[   13.634391] ENABLING IO-APIC IRQs
[   13.634582] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   13.797382] APIC calibration not consistent with PM Timer: 116ms instead of 100ms
[   13.797385] APIC delta adjusted to PM-Timer: 1039062 (1205386)
[   13.797504] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   13.817490] Brought up 2 CPUs
[   13.817515] CPU0 attaching sched-domain:
[   13.817518]  domain 0: span 03
[   13.817520]   groups: 01 02
[   13.817523] CPU1 attaching sched-domain:
[   13.817524]  domain 0: span 03
[   13.817526]   groups: 02 01
[   13.817767] net_namespace: 64 bytes
[   13.817778] Booting paravirtualized kernel on bare hardware
[   13.818249] Time:  6:59:10  Date: 10/07/08
[   13.818276] NET: Registered protocol family 16
[   13.818488] EISA bus registered
[   13.818493] ACPI: bus type pci registered
[   13.818745] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[   13.818748] PCI: Using configuration type 1
[   13.818769] Setting up standard PCI resources
[   13.830106] ACPI: EC: Look up EC in DSDT
[   13.909075] ACPI: Interpreter enabled
[   13.909078] ACPI: (supports S0 S1 S3 S4 S5)
[   13.909095] ACPI: Using IOAPIC for interrupt routing
[   13.911269] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   13.919936] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   13.919939] ACPI: EC: driver started in interrupt mode
[   13.920053] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.920864] Force enabled HPET at base address 0xfed00000
[   13.920870] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   13.920874] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   13.922439] PCI: Transparent bridge - 0000:00:1e.0
[   13.922488] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.922625] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   13.922710] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   13.922809] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   13.922899] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[   13.923004] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[   13.961430] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   13.961563] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   13.961693] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   13.961823] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   13.961952] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   13.962083] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   13.962213] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   13.962343] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   13.962483] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.962516] pnp: PnP ACPI init
[   13.962523] ACPI: bus type pnp registered
[   13.966107] pnp: PnP ACPI: found 13 devices
[   13.966110] ACPI: ACPI bus type pnp unregistered
[   13.966114] PnPBIOS: Disabled by ACPI PNP
[   13.966357] PCI: Using ACPI for IRQ routing
[   13.966360] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.009195] NET: Registered protocol family 8
[   14.009198] NET: Registered protocol family 20
[   14.009362] hpet clockevent registered
[   14.009368] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   14.009373] hpet0: 3 64-bit timers, 14318180 Hz
[   14.010406] AppArmor: AppArmor Filesystem Enabled
[   14.013069] Time: tsc clocksource has been installed.
[   14.029195] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   14.029206] system 00:08: ioport range 0x25c-0x25f has been reserved
[   14.029208] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   14.029211] system 00:08: ioport range 0x800-0x87f has been reserved
[   14.029213] system 00:08: ioport range 0x480-0x4bf has been reserved
[   14.029216] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   14.029219] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[   14.029222] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[   14.029224] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[   14.029227] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   14.029233] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[   14.029236] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[   14.029242] system 00:0b: iomem range 0xe0000000-0xe3ffffff has been reserved
[   14.029248] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   14.029251] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[   14.029254] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   14.029257] system 00:0c: iomem range 0x100000-0x7fffffff could not be reserved
[   14.029259] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   14.059677] PCI: Bridge: 0000:00:01.0
[   14.059679]   IO window: 9000-bfff
[   14.059683]   MEM window: fef00000-feffffff
[   14.059687]   PREFETCH window: bdf00000-ddefffff
[   14.059690] PCI: Bridge: 0000:00:1c.0
[   14.059692]   IO window: disabled.
[   14.059697]   MEM window: disabled.
[   14.059701]   PREFETCH window: disabled.
[   14.059707] PCI: Bridge: 0000:00:1c.1
[   14.059708]   IO window: disabled.
[   14.059714]   MEM window: ff800000-ff8fffff
[   14.059718]   PREFETCH window: disabled.
[   14.059724] PCI: Bridge: 0000:00:1c.2
[   14.059727]   IO window: c000-cfff
[   14.059733]   MEM window: ff000000-ff7fffff
[   14.059737]   PREFETCH window: ddf00000-dfefffff
[   14.059745] PCI: Bridge: 0000:00:1e.0
[   14.059749]   IO window: d000-dfff
[   14.059754]   MEM window: ff900000-ff9fffff
[   14.059759]   PREFETCH window: disabled.
[   14.059776] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.059782] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   14.059805] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.059811] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   14.059836] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   14.059842] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   14.059867] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   14.059873] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   14.059888] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   14.059898] NET: Registered protocol family 2
[   14.097107] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.097326] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.097776] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   14.097999] TCP: Hash tables configured (established 131072 bind 65536)
[   14.098001] TCP reno registered
[   14.109161] checking if image is initramfs... it is
[   14.512307] Switched to high resolution mode on CPU 0
[   14.512417] Switched to high resolution mode on CPU 1
[   14.819286] Freeing initrd memory: 7719k freed
[   14.820145] audit: initializing netlink socket (disabled)
[   14.820159] audit(1223362750.540:1): initialized
[   14.820388] highmem bounce pool size: 64 pages
[   14.822517] VFS: Disk quotas dquot_6.5.1
[   14.822596] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   14.822732] io scheduler noop registered
[   14.822734] io scheduler anticipatory registered
[   14.822736] io scheduler deadline registered
[   14.822754] io scheduler cfq registered (default)
[   14.822856] Boot video device is 0000:01:00.0
[   14.822974] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   14.823013] assign_interrupt_mode Found MSI capability
[   14.823046] Allocate Port Service[0000:00:01.0:pcie00]
[   14.823131] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   14.823191] assign_interrupt_mode Found MSI capability
[   14.823240] Allocate Port Service[0000:00:1c.0:pcie00]
[   14.823275] Allocate Port Service[0000:00:1c.0:pcie02]
[   14.823384] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   14.823445] assign_interrupt_mode Found MSI capability
[   14.823493] Allocate Port Service[0000:00:1c.1:pcie00]
[   14.823528] Allocate Port Service[0000:00:1c.1:pcie02]
[   14.823634] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   14.823695] assign_interrupt_mode Found MSI capability
[   14.823743] Allocate Port Service[0000:00:1c.2:pcie00]
[   14.823777] Allocate Port Service[0000:00:1c.2:pcie02]
[   14.824064] isapnp: Scanning for PnP cards...
[   15.178499] isapnp: No Plug & Play device found
[   15.205225] Real Time Clock Driver v1.12ac
[   15.205342] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.206664] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.206734] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   15.206844] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   15.208627] i8042.c: Detected active multiplexing controller, rev 1.1.
[   15.210045] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.210050] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   15.210052] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   15.210055] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   15.210057] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   15.228287] mice: PS/2 mouse device common for all mice
[   15.228409] EISA: Probing bus 0 at eisa.0
[   15.228448] EISA: Detected 0 cards.
[   15.228451] cpuidle: using governor ladder
[   15.228453] cpuidle: using governor menu
[   15.228536] NET: Registered protocol family 1
[   15.228562] Using IPI No-Shortcut mode
[   15.228591] registered taskstats version 1
[   15.228705]   Magic number: 12:625:973
[   15.228712]   hash matches device ttyc0
[   15.228777] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   15.228778] EDD information not available.
[   15.228961] Freeing unused kernel memory: 368k freed
[   15.260941] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   15.445563] vesafb: framebuffer at 0xc0000000, mapped to 0xf8880000, using 975k, total 16384k
[   15.445568] vesafb: mode is 800x600x8, linelength=832, pages=31
[   15.445570] vesafb: protected mode interface info at c000:acaa
[   15.445572] vesafb: pmi: set display start = c00cad38, set palette = c00cadfa
[   15.445574] vesafb: scrolling: redraw
[   15.445577] vesafb: Pseudocolor: size=8:8:8:8, shift=0:0:0:0
[   15.445691] Console: switching to colour frame buffer device 100x37
[   15.453884] fb0: VESA VGA frame buffer device
[   16.581219] fuse init (API version 7.9)
[   16.604045] ACPI: SSDT 7FFB6480, 043D (r1    AMI   CPU1PM        1 INTL 20060113)
[   16.604516] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   16.604521] ACPI: Processor [CPU1] (supports 8 throttling states)
[   16.604576] ACPI: SSDT 7FFB68C0, 043D (r1    AMI   CPU2PM        1 INTL 20060113)
[   16.605052] ACPI: CPU1 (power states: C1[C1] C2[C2])
[   16.605057] ACPI: Processor [CPU2] (supports 8 throttling states)
[   16.608845] ACPI: Thermal Zone [TZ00] (34 C)
[   16.964996] usbcore: registered new interface driver usbfs
[   16.965019] usbcore: registered new interface driver hub
[   16.965056] usbcore: registered new device driver usb
[   16.966205] USB Universal Host Controller Interface driver v3.0
[   16.966256] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   16.966267] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   16.966271] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   16.966499] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   16.966530] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000e480
[   16.966663] usb usb1: configuration #1 chosen from 1 choice
[   16.966690] hub 1-0:1.0: USB hub found
[   16.966695] hub 1-0:1.0: 2 ports detected
[   17.069501] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   17.069515] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   17.069520] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   17.069544] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   17.069575] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000e800
[   17.069690] usb usb2: configuration #1 chosen from 1 choice
[   17.069714] hub 2-0:1.0: USB hub found
[   17.069719] hub 2-0:1.0: 2 ports detected
[   17.085565] SCSI subsystem initialized
[   17.102726] libata version 3.00 loaded.
[   17.173373] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   17.173386] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   17.173391] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   17.173417] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   17.173453] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e880
[   17.173572] usb usb3: configuration #1 chosen from 1 choice
[   17.173600] hub 3-0:1.0: USB hub found
[   17.173605] hub 3-0:1.0: 2 ports detected
[   17.277186] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   17.277199] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   17.277204] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   17.277230] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   17.277264] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ec00
[   17.277381] usb usb4: configuration #1 chosen from 1 choice
[   17.277406] hub 4-0:1.0: USB hub found
[   17.277411] hub 4-0:1.0: 2 ports detected
[   17.309048] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   17.381084] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   17.381101] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   17.381105] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   17.381131] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   17.385039] ehci_hcd 0000:00:1d.7: debug port 1
[   17.385047] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   17.385055] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffaffc00
[   17.439843] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.439966] usb usb5: configuration #1 chosen from 1 choice
[   17.439992] hub 5-0:1.0: USB hub found
[   17.439998] hub 5-0:1.0: 8 ports detected
[   17.543785] r8169 Gigabit Ethernet driver 2.2LK loaded
[   17.543813] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 18 (level, low) -> IRQ 18
[   17.544082] eth0: RTL8169sb/8110sb at 0xf89c6c00, 00:18:f3:64:e0:da, XID 10000000 IRQ 18
[   17.544761] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.597404] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[ff9fe000-ff9fe7ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   17.622650] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   17.622691] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   17.622705] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   17.626547] ata_piix 0000:00:1f.2: version 2.12
[   17.626553] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   17.626571] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   17.626604] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   17.627036] scsi0 : ata_piix
[   17.627439] scsi1 : ata_piix
[   17.630245] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   17.630248] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   17.791948] ata1.00: ATA-7: Hitachi HTS541210H9SA00, HPBOC20F, max UDMA/100
[   17.791956] ata1.00: 195371568 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   17.808919] ata1.00: configured for UDMA/100
[   17.843237] usb 1-1: device not accepting address 2, error -71
[   18.127316] ata2.01: ATAPI: HL-DT-ST DVDRAM GMA-4082N, HJ02, max UDMA/33
[   18.298966] ata2.01: configured for UDMA/33
[   18.299110] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54121 HPBO PQ: 0 ANSI: 5
[   18.303129] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRAM GMA-4082N HJ02 PQ: 0 ANSI: 5
[   18.310112] Driver 'sd' needs updating - please use bus_type methods
[   18.310187] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   18.310199] sd 0:0:0:0: [sda] Write Protect is off
[   18.310201] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.310219] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.310268] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   18.310278] sd 0:0:0:0: [sda] Write Protect is off
[   18.310281] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.310297] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.310301]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   18.334960]  sda1 sda2 sda3
[   18.335846] sd 0:0:0:0: [sda] Attached SCSI disk
[   18.340534] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.340554] sr 1:0:1:0: Attached scsi generic sg1 type 5
[   18.346125] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[   18.346129] Uniform CD-ROM driver Revision: 3.20
[   18.346178] sr 1:0:1:0: Attached scsi CD-ROM sr0
[   18.637951] Attempting manual resume
[   18.637955] swsusp: Resume From Partition 8:1
[   18.637957] PM: Checking swsusp image.
[   18.638175] PM: Resume from disk failed.
[   18.642975] swsusp: Marking nosave pages: 000000000009f000 - 0000000000100000
[   18.642983] swsusp: Basic memory bitmaps created
[   18.652987] swsusp: Basic memory bitmaps freed
[   18.682048] kjournald starting.  Commit interval 5 seconds
[   18.682063] EXT3-fs: mounted filesystem with ordered data mode.
[   18.817768] usb 5-6: new high speed USB device using ehci_hcd and address 4
[   18.885942] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800036adbb2]
[   18.957468] usb 5-6: configuration #1 chosen from 1 choice
[   19.197178] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   19.372039] usb 1-1: configuration #1 chosen from 1 choice
[   19.612537] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   19.857544] usb 3-1: configuration #1 chosen from 1 choice
[   31.700114] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   31.839607] tpm_inf_pnp 00:0a: Found TPM with ID IFX0102
[   31.839663] tpm_inf_pnp 00:0a: TPM found: config base 0x4e, data base 0x4700, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[   31.907573] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.938949] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.978764] iTCO_vendor_support: vendor-support=0
[   32.006683] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   32.006776] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0860)
[   32.006812] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   32.078561] Linux agpgart interface v0.102
[   32.222327] intel_rng: FWH not detected
[   32.238449] input: Power Button (FF) as /devices/virtual/input/input3
[   32.290270] ACPI: Power Button (FF) [PWRF]
[   32.290374] input: Lid Switch as /devices/virtual/input/input4
[   32.324324] ACPI: Lid Switch [LID]
[   32.324402] input: Sleep Button (CM) as /devices/virtual/input/input5
[   32.386070] ACPI: Sleep Button (CM) [SLPB]
[   32.386134] input: Power Button (CM) as /devices/virtual/input/input6
[   32.449975] ACPI: Power Button (CM) [PWRB]
[   32.564941] asus-laptop: Asus Laptop Support version 0.42
[   32.565033] asus-laptop: Error calling BSTS
[   32.565098] asus-laptop:   Z96JS model detected
[   32.579007] Registered led device: asus:mail
[   32.638893] sdhci: Secure Digital Host Controller Interface driver
[   32.638896] sdhci: Copyright(c) Pierre Ossman
[   32.638938] sdhci: SDHCI controller found at 0000:06:01.1 [1180:0822] (rev 19)
[   32.638959] ACPI: PCI Interrupt 0000:06:01.1[B] -> GSI 17 (level, low) -> IRQ 17
[   32.638974] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   32.639024] mmc0: SDHCI at 0xff9fec00 irq 17 DMA
[   32.724599] ricoh-mmc: Ricoh MMC Controller disabling driver
[   32.724602] ricoh-mmc: Copyright(c) Philip Langdale
[   32.724645] ricoh-mmc: Ricoh MMC controller found at 0000:06:01.2 [1180:0843] (rev 1)
[   32.724657] ricoh-mmc: Controller is now disabled.
[   33.109327] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7
[   33.157775] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   33.183116] ACPI: AC Adapter [AC0] (on-line)
[   33.321375] ACPI: Battery Slot [BAT0] (battery present)
[   33.445716] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.445740] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   33.477343] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   33.672321] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   33.699708] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[   33.699747] [fglrx]   vendor: 1002 device: 71c5 count: 1
[   33.699803] [fglrx] ioport: bar 1, base 0xb000, size: 0x100
[   33.699843] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.699856] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   33.700968] [fglrx] PAT is enabled successfully!
[   33.701316] [fglrx] module loaded - fglrx 8.53.4 [Sep  8 2008] with 1 minors
[   33.753259] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[   33.757974] input: Logitech USB RECEIVER as /devices/virtual/input/input8
[   33.784609] Bluetooth: Core ver 2.11
[   33.784696] NET: Registered protocol family 31
[   33.784698] Bluetooth: HCI device and connection manager initialized
[   33.784702] Bluetooth: HCI socket layer initialized
[   33.795629] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   33.832639] Bluetooth: HCI USB driver ver 2.9
[   33.836603] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   33.836606] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   33.836736] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   33.836752] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   33.836771] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   33.838900] lmpcm_usb.c: Detected device: Logitech USB RECEIVER
[   33.838922] usbcore: registered new interface driver lmpcm_usb
[   33.838926] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   33.855818] usbcore: registered new interface driver hci_usb
[   33.889986] usbcore: registered new interface driver hiddev
[   33.890008] usbcore: registered new interface driver usbhid
[   33.890012] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   34.925063] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   34.929895] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   35.074033] udev: renamed network interface wlan0 to eth1
[   35.215297] lp: driver loaded but no devices found
[   35.268009] snd-bt-sco revision 1.19 $
[   35.268031] snd-bt-sco: snd-bt-scod thread starting
[   35.304625] Bluetooth: L2CAP ver 2.9
[   35.304629] Bluetooth: L2CAP socket layer initialized
[   35.314474] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   35.355703] usbcore: registered new interface driver usbserial
[   35.355721] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   35.355756] usbcore: registered new interface driver usbserial_generic
[   35.355759] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   35.556548] Adding 2096440k swap on /dev/sda1.  Priority:-1 extents:1 across:2096440k
[   36.116464] EXT3 FS on sda3, internal journal
[   36.352085] device-mapper: uevent: version 1.0.3
[   36.352115] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   38.274222] ip_tables: (C) 2000-2006 Netfilter Core Team
[   39.179182] NET: Registered protocol family 10
[   39.179465] lo: Disabled Privacy Extensions
[   40.473267] No dock devices found.
[   55.012022] ppdev: user-space parallel port driver
[   55.762931] audit(1223362791.757:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5909 profile="/usr/sbin/cupsd" namespace="default"
[   56.283951] apm: BIOS not found.
[   58.895425] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   58.895433] [fglrx] Reserved FB block: Unshared offset:1000000, size:5000 
[   58.895436] [fglrx] Reserved FB block: Unshared offset:ffbf000, size:40000 
[   58.895438] [fglrx] Reserved FB block: Unshared offset:ffff000, size:1000 
[   69.831370] r8169: eth0: link down
[   69.834917] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   69.882192] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   70.115324] Bluetooth: RFCOMM socket layer initialized
[   70.115340] Bluetooth: RFCOMM TTY layer initialized
[   70.115343] Bluetooth: RFCOMM ver 1.8
[   72.926053] video1394: Installed video1394 module
[ 1834.489555] CPU0 attaching NULL sched-domain.
[ 1834.489563] CPU1 attaching NULL sched-domain.
[ 1834.499963] CPU0 attaching sched-domain:
[ 1834.499970]  domain 0: span 03
[ 1834.499973]   groups: 01 02
[ 1834.499979] CPU1 attaching sched-domain:
[ 1834.499982]  domain 0: span 03
[ 1834.499984]   groups: 02 01
[ 1853.305224] NET: Registered protocol family 17
[ 1855.343144] eth1: Initial auth_alg=0
[ 1855.343152] eth1: authenticate with AP 00:18:39:e7:a8:7f
[ 1855.348871] eth1: RX authentication from 00:18:39:e7:a8:7f (alg=0 transaction=2 status=0)
[ 1855.348879] eth1: authenticated
[ 1855.348883] eth1: associate with AP 00:18:39:e7:a8:7f
[ 1855.372625] eth1: RX AssocResp from 00:18:39:e7:a8:7f (capab=0x411 status=0 aid=1)
[ 1855.372632] eth1: associated
[ 1855.376172] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1861.589729] eth1: deauthenticate(reason=3)
[ 1871.835145] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835152] eth1: deauthenticated
[ 1871.835159] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835164] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835170] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835215] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835220] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835226] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835231] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835236] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835241] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835247] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835251] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835257] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835262] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835267] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835272] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835277] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835282] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835288] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835292] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835297] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835303] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835308] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835313] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835318] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835323] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835328] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835333] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835338] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835344] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835349] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835354] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835360] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835365] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835370] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835374] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835380] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835385] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835390] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835395] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835400] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835406] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835411] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835418] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835423] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835429] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835435] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835442] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835448] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835454] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835460] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835465] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835471] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835477] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835483] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835489] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835494] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835500] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835506] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835512] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835518] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835524] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835531] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835537] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835542] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835548] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835554] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835560] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835565] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835571] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835577] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835583] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835589] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835594] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835600] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835606] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835612] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835618] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835624] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835630] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835635] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.835641] eth1: RX deauthentication from 00:18:39:e7:a8:7f (reason=7)
[ 1871.842234] eth1: Initial auth_alg=0
[ 1871.842240] eth1: authenticate with AP 00:18:39:e7:a8:7f
[ 1871.842976] eth1: Initial auth_alg=0
[ 1871.842982] eth1: authenticate with AP 00:18:39:e7:a8:7f
[ 1871.847962] eth1: Initial auth_alg=0
[ 1871.847968] eth1: authenticate with AP 00:1d:5a:03:b0:31
[ 1871.849007] eth1: Initial auth_alg=0
[ 1871.849012] eth1: authenticate with AP 00:1d:5a:03:b0:31
[ 1871.912689] eth1: RX authentication from 00:1d:5a:03:b0:31 (alg=0 transaction=2 status=0)
[ 1871.912697] eth1: authenticated
[ 1871.912701] eth1: associate with AP 00:1d:5a:03:b0:31
[ 1871.918682] eth1: authentication frame received from 00:1d:5a:03:b0:31, but not in authenticate state - ignored
[ 1871.919891] eth1: RX AssocResp from 00:1d:5a:03:b0:31 (capab=0x431 status=0 aid=1)
[ 1871.919896] eth1: associated
[ 1871.919901] eth1: CTS protection enabled (BSSID=00:1d:5a:03:b0:31)
[ 1871.923609] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1872.301489] eth1: CTS protection disabled (BSSID=00:1d:5a:03:b0:31)
[ 1893.259310] eth1: no IPv6 routers present
[ 3534.926916] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[ 3534.926924] [fglrx] Reserved FB block: Unshared offset:1000000, size:5000 
[ 3534.926927] [fglrx] Reserved FB block: Unshared offset:ffbf000, size:40000 
[ 3534.926929] [fglrx] Reserved FB block: Unshared offset:ffff000, size:1000 
[ 3559.751501] CPU0 attaching NULL sched-domain.
[ 3559.751507] CPU1 attaching NULL sched-domain.
[ 3559.776217] CPU0 attaching sched-domain:
[ 3559.776222]  domain 0: span 03
[ 3559.776224]   groups: 01 02
[ 3559.776228] CPU1 attaching sched-domain:
[ 3559.776230]  domain 0: span 03
[ 3559.776231]   groups: 02 01
[ 3947.178148] usb 1-1: USB disconnect, address 4
[ 3954.306207] usb 1-2: new low speed USB device using uhci_hcd and address 5
[ 3954.538059] usb 1-2: configuration #1 chosen from 1 choice
[ 3954.555960] input: Logitech USB RECEIVER as /devices/virtual/input/input10
[ 3954.614971] lmpcm_usb.c: Detected device: Logitech USB RECEIVER


```

The xorg.conf file:

```


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad" "AlwaysCore"
EndSection

Section "Extensions"
        Option "Composite" "false"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection


Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "Emulate3Buttons" "yes"
	Option	    "SHMConfig" "on"
	Option	    "MaxTapTime" "0"
	Option	    "HorizScrollDelta" "0"
	Option	    "FingerLow" "38"
	Option	    "FingerHigh" "43"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 50.0
	VertRefresh  43.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Extensions"
        Option "Composite" "False"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

And the Xorg.log file:

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux r3-mobile 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct  7 00:57:50 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. ATI Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(==) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 8086,27a0 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1043,1343 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1043,1347 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1043,1347 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1043,1347 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1043,1347 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1043,1347 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 1043,1347 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c4 card 1043,1347 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1043,1347 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,71c5 card 1043,10b2 rev 00 class 03,00,00 hdr 00
(II) PCI: 04:00:0: chip 8086,4222 card 8086,1000 rev 02 class 02,80,00 hdr 00
(II) PCI: 06:01:0: chip 1180,0832 card 1043,1347 rev 00 class 0c,00,10 hdr 80
(II) PCI: 06:01:1: chip 1180,0822 card 1043,1347 rev 19 class 08,05,00 hdr 80
(II) PCI: 06:01:2: chip 1180,0843 card 1043,1347 rev 01 class 08,80,00 hdr 80
(II) PCI: 06:01:3: chip 1180,0592 card 1043,1347 rev 0a class 08,80,00 hdr 80
(II) PCI: 06:01:4: chip 1180,0852 card 1043,1347 rev 05 class 08,80,00 hdr 80
(II) PCI: 06:07:0: chip 10ec,8169 card 1043,11e5 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x0000bfff (0x3000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfef00000 - 0xfeffffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbdf00000 - 0xddefffff (0x20000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:0), (0,5,5), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:1), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xff800000 - 0xff8fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:2), (0,2,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xff000000 - 0xff7fffff (0x800000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xddf00000 - 0xdfefffff (0x2000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:30:0), (0,6,6), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xff900000 - 0xff9fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc M56P [Radeon Mobility X1600] rev 0, Mem @ 0xc0000000/28, 0xfeff0000/16, I/O @ 0xb000/8, BIOS @ 0xfefc0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xff9ffc00 - 0xff9ffcff (0x100) MX[B]
	[1] -1	0	0xff9ff800 - 0xff9ff8ff (0x100) MX[B]
	[2] -1	0	0xff9ff400 - 0xff9ff4ff (0x100) MX[B]
	[3] -1	0	0xff9ff000 - 0xff9ff0ff (0x100) MX[B]
	[4] -1	0	0xff9fec00 - 0xff9fecff (0x100) MX[B]
	[5] -1	0	0xff9fe000 - 0xff9fe7ff (0x800) MX[B]
	[6] -1	0	0xff8ff000 - 0xff8fffff (0x1000) MX[B]
	[7] -1	0	0xffaffc00 - 0xffafffff (0x400) MX[B]
	[8] -1	0	0xffaf8000 - 0xffafbfff (0x4000) MX[B]
	[9] -1	0	0xfefc0000 - 0xfefdffff (0x20000) MX[B](B)
	[10] -1	0	0xfeff0000 - 0xfeffffff (0x10000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[13] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[20] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[22] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xff9ffc00 - 0xff9ffcff (0x100) MX[B]
	[1] -1	0	0xff9ff800 - 0xff9ff8ff (0x100) MX[B]
	[2] -1	0	0xff9ff400 - 0xff9ff4ff (0x100) MX[B]
	[3] -1	0	0xff9ff000 - 0xff9ff0ff (0x100) MX[B]
	[4] -1	0	0xff9fec00 - 0xff9fecff (0x100) MX[B]
	[5] -1	0	0xff9fe000 - 0xff9fe7ff (0x800) MX[B]
	[6] -1	0	0xff8ff000 - 0xff8fffff (0x1000) MX[B]
	[7] -1	0	0xffaffc00 - 0xffafffff (0x400) MX[B]
	[8] -1	0	0xffaf8000 - 0xffafbfff (0x4000) MX[B]
	[9] -1	0	0xfefc0000 - 0xfefdffff (0x20000) MX[B](B)
	[10] -1	0	0xfeff0000 - 0xfeffffff (0x10000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[13] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[20] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[22] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff9ffc00 - 0xff9ffcff (0x100) MX[B]
	[5] -1	0	0xff9ff800 - 0xff9ff8ff (0x100) MX[B]
	[6] -1	0	0xff9ff400 - 0xff9ff4ff (0x100) MX[B]
	[7] -1	0	0xff9ff000 - 0xff9ff0ff (0x100) MX[B]
	[8] -1	0	0xff9fec00 - 0xff9fecff (0x100) MX[B]
	[9] -1	0	0xff9fe000 - 0xff9fe7ff (0x800) MX[B]
	[10] -1	0	0xff8ff000 - 0xff8fffff (0x1000) MX[B]
	[11] -1	0	0xffaffc00 - 0xffafffff (0x400) MX[B]
	[12] -1	0	0xffaf8000 - 0xffafbfff (0x4000) MX[B]
	[13] -1	0	0xfefc0000 - 0xfefdffff (0x20000) MX[B](B)
	[14] -1	0	0xfeff0000 - 0xfeffffff (0x10000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[26] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[28] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[29] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.53.4
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Wacom driver level: 47-0.7.9-8 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.53.4
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.532                    
(II) ATI Proprietary Linux Driver Build Date: Sep  8 2008 16:31:48
(--) Chipset Supported AMD Graphics Processor (0x71C5) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff9ffc00 - 0xff9ffcff (0x100) MX[B]
	[5] -1	0	0xff9ff800 - 0xff9ff8ff (0x100) MX[B]
	[6] -1	0	0xff9ff400 - 0xff9ff4ff (0x100) MX[B]
	[7] -1	0	0xff9ff000 - 0xff9ff0ff (0x100) MX[B]
	[8] -1	0	0xff9fec00 - 0xff9fecff (0x100) MX[B]
	[9] -1	0	0xff9fe000 - 0xff9fe7ff (0x800) MX[B]
	[10] -1	0	0xff8ff000 - 0xff8fffff (0x1000) MX[B]
	[11] -1	0	0xffaffc00 - 0xffafffff (0x400) MX[B]
	[12] -1	0	0xffaf8000 - 0xffafbfff (0x4000) MX[B]
	[13] -1	0	0xfefc0000 - 0xfefdffff (0x20000) MX[B](B)
	[14] -1	0	0xfeff0000 - 0xfeffffff (0x10000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[26] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[28] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[29] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x820eb30
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xff9ffc00 - 0xff9ffcff (0x100) MX[B]
	[5] -1	0	0xff9ff800 - 0xff9ff8ff (0x100) MX[B]
	[6] -1	0	0xff9ff400 - 0xff9ff4ff (0x100) MX[B]
	[7] -1	0	0xff9ff000 - 0xff9ff0ff (0x100) MX[B]
	[8] -1	0	0xff9fec00 - 0xff9fecff (0x100) MX[B]
	[9] -1	0	0xff9fe000 - 0xff9fe7ff (0x800) MX[B]
	[10] -1	0	0xff8ff000 - 0xff8fffff (0x1000) MX[B]
	[11] -1	0	0xffaffc00 - 0xffafffff (0x400) MX[B]
	[12] -1	0	0xffaf8000 - 0xffafbfff (0x4000) MX[B]
	[13] -1	0	0xfefc0000 - 0xfefdffff (0x20000) MX[B](B)
	[14] -1	0	0xfeff0000 - 0xfeffffff (0x10000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[29] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[30] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[31] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[32] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(**) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Mobility Radeon X1600" (Chipset = 0x71c5)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x10b2)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xfeff0000
(--) fglrx(0): I/O port at 0x0000b000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M56P
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.53.4
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 1:0.0.
(II) fglrx(0): [FB] Find the MC FB aperturs range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
(--) fglrx(0): Video RAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000002, disabled=0x00000000
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: CMO  Model: 1523  Serial#: 0
(II) fglrx(0): Year: 1990  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 20
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.626 redY: 0.354   greenX: 0.294 greenY: 0.589
(II) fglrx(0): blueX: 0.144 blueY: 0.097   whiteX: 0.309 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 119.0 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) fglrx(0):  N154Z1-L02
(II) fglrx(0):  CMO
(II) fglrx(0):  N154Z1-L02
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff000daf231500000000
(II) fglrx(0): 	00000103802114780a77f1a05a4b9624
(II) fglrx(0): 	184f5400000001010101010101010101
(II) fglrx(0): 	0101010101017c2e90a0601a1e403020
(II) fglrx(0): 	36004bcf10000018000000fe004e3135
(II) fglrx(0): 	345a312d4c30320a2020000000fe0043
(II) fglrx(0): 	4d4f0a202020202020202020000000fe
(II) fglrx(0): 	004e3135345a312d4c30320a202000f8
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  5 power states available:
(II) fglrx(0):   1. 446/369MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 128/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   3. 209/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   4. 324/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   5. 392/252MHz @ 60Hz [enable sleep]
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 15 modes found for primary display.
(--) fglrx(0): Virtual size is 1680x1050 (pitch 0)
(**) fglrx(0): *Mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"x60.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1024x768": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0  119.00  1024 1728 1760 1840  768 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "800x600": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0  119.00  800 1728 1760 1840  600 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "640x480": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0  119.00  640 1728 1760 1840  480 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "1440x900": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  119.00  1440 1728 1760 1840  900 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "1400x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  119.00  1400 1728 1760 1840  1050 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "1280x1024": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  119.00  1280 1728 1760 1840  1024 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "1280x960": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  119.00  1280 1728 1760 1840  960 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "1280x768": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0  119.00  1280 1728 1760 1840  768 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "1152x864": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0  119.00  1152 1728 1760 1840  864 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "640x400": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0  119.00  640 1728 1760 1840  400 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "512x384": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0  119.00  512 1728 1760 1840  384 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "400x300": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"x60.0  119.00  400 1728 1760 1840  300 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "320x240": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"x60.0  119.00  320 1728 1760 1840  240 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "320x200": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"x60.0  119.00  320 1728 1760 1840  200 1053 1059 1080 +hsync +vsync (64.7 kHz)
(--) fglrx(0): Display dimensions: (330, 200) mm
(--) fglrx(0): DPI set to (129, 133)
(--) fglrx(0): Virtual size is 1680x1050 (pitch 1728)
(**) fglrx(0): *Mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"x60.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "1024x768": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0  119.00  1024 1728 1760 1840  768 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "800x600": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0  119.00  800 1728 1760 1840  600 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0): *Mode "640x480": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0  119.00  640 1728 1760 1840  480 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "1440x900": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  119.00  1440 1728 1760 1840  900 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "1400x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  119.00  1400 1728 1760 1840  1050 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "1280x1024": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  119.00  1280 1728 1760 1840  1024 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "1280x960": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  119.00  1280 1728 1760 1840  960 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "1280x768": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0  119.00  1280 1728 1760 1840  768 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "1152x864": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0  119.00  1152 1728 1760 1840  864 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "640x400": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0  119.00  640 1728 1760 1840  400 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "512x384": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0  119.00  512 1728 1760 1840  384 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "400x300": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"x60.0  119.00  400 1728 1760 1840  300 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "320x240": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"x60.0  119.00  320 1728 1760 1840  240 1053 1059 1080 +hsync +vsync (64.7 kHz)
(**) fglrx(0):  Default mode "320x200": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"x60.0  119.00  320 1728 1760 1840  200 1053 1059 1080 +hsync +vsync (64.7 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 255 MB
(II) fglrx(0): [pcie] 261120 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): Direct rendering enabled
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfeff0000 - 0xfeffffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xff9ffc00 - 0xff9ffcff (0x100) MX[B]
	[7] -1	0	0xff9ff800 - 0xff9ff8ff (0x100) MX[B]
	[8] -1	0	0xff9ff400 - 0xff9ff4ff (0x100) MX[B]
	[9] -1	0	0xff9ff000 - 0xff9ff0ff (0x100) MX[B]
	[10] -1	0	0xff9fec00 - 0xff9fecff (0x100) MX[B]
	[11] -1	0	0xff9fe000 - 0xff9fe7ff (0x800) MX[B]
	[12] -1	0	0xff8ff000 - 0xff8fffff (0x1000) MX[B]
	[13] -1	0	0xffaffc00 - 0xffafffff (0x400) MX[B]
	[14] -1	0	0xffaf8000 - 0xffafbfff (0x4000) MX[B]
	[15] -1	0	0xfefc0000 - 0xfefdffff (0x20000) MX[B](B)
	[16] -1	0	0xfeff0000 - 0xfeffffff (0x10000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[21] 0	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[25] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[32] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[33] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[34] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[35] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-1)
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit for fglrx driver
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x47000
(II) fglrx(0): [drm] mapped SAREA 0x47000 to 0xb7fb2000
(II) fglrx(0): [drm] framebuffer handle = 0x48000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.53.4
(II) fglrx(0):     Date: Sep  8 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.24-21-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00049000
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc1005000 FBMappedSize: 0x01008000
(II) fglrx(0): FBMM initialized for area (0,0)-(1728,2432)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1728,1050) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1728 x 1382
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 16
(II) fglrx(0): GLESX is enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		8 256x256 slots
		4 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/modules//amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(**) Option "SHMConfig" "on"
(**) Option "HorizScrollDelta" "0"
(**) Option "FingerLow" "38"
(**) Option "FingerHigh" "43"
(**) Option "MaxTapTime" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "AlwaysCore"
(**) Synaptics Touchpad: doesn't report core events
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) evaluating device (eraser)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) evaluating device (cursor)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) evaluating device (stylus)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Resource temporarily unavailable
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Resource temporarily unavailable
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Resource temporarily unavailable
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Resource temporarily unavailable
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Resource temporarily unavailable
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success

```


Many thanks,
Brian

---

### Post by 3rag0n on 2008-10-07
Similar Problem in my Acer Aspire 4530.

Well, synaptics touchpad did work in the virgin Hardy install, just stopped working after i installed the driver for my nvidia card.

Did sumthing similar happen in ur case?... like it stopped working after installing the ATI driver ?

---

### Post by bdw on 2008-10-07
:) That did the trick!

I had installed the ATI driver on Gutsy and it worked OK and I had reinstalled immediately after I upgraded to Hardy.

I uninstalled the ATI driver and reinstalled the generic fglrx driver and it worked fine.

Yet another instance of a proprietary accelerated graphics driver screwing up a system....

---

### Post by bdw on 2008-10-07
I should also note that reinstalling the ATI driver while using the default xorg.conf did not knock out the Synaptics Touchpad. :)

---

