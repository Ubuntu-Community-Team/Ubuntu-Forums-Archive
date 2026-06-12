---
title: "[SOLVED] USplash stops showing after modifying partitions"
date: 2008-08-04
forum: General Help
---

### Post by muadnu on 2008-08-04
A couple of days ago I installed Intrepid Alpha 3 in a separate partition. After doing that, when booting in my Hardy partition USplash shows as usual but after a couple of seconds it disappears and I get the "normal" (not quiet) boot up. This has happened to me before, in particular if I forget to change my /etc/fstab file to reflect changes in the UUID's of my disks. I did forget it this time (the Intrepid installation formatted my swap partition), but I corrected it and still get this problem.

I'm not sure what might be the problem when booting, I've looked at /var/log/dmesg but haven't seen anything that I can point out as an error. But I don't know a lot about the boot up sequence anyway. Any ideas? I'm putting here the /var/log/dmesg file...

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 21:01:46 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] Command line: root=UUID=7a7d6af2-f834-4054-8c16-fc548693450d ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe6d800 (usable)
[    0.000000]  BIOS-e820: 000000007fe6d800 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 523885) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FBBF0 checksum 0
[    0.000000] ACPI: RSDP 000FBBF0, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT 7FE6F200, 005C (r1 DELL    M08     27D80203 ASL        61)
[    0.000000] ACPI: FACP 7FE6F09C, 00F4 (r4 DELL    M08     27D80203 ASL        61)
[    0.000000] ACPI: DSDT 7FE6F800, 5676 (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS 7FE7E000, 0040
[    0.000000] ACPI: HPET 7FE6F300, 0038 (r1 DELL    M08            1 ASL        61)
[    0.000000] ACPI: APIC 7FE6F400, 0068 (r1 DELL    M08     27D80203 ASL        47)
[    0.000000] ACPI: MCFG 7FE6F3C0, 003E (r16 DELL    M08     27D80203 ASL        61)
[    0.000000] ACPI: SLIC 7FE6F49C, 0176 (r1 DELL    M08     27D80203 ASL        61)
[    0.000000] ACPI: BOOT 7FE6EFC0, 0028 (r1 DELL    M08     27D80203 ASL        61)
[    0.000000] ACPI: SSDT 7FE6D9BC, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fe6d000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 523885) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fe6d000
[    0.000000] No mptable found.
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   523885
[    0.000000] On node 0 totalpages: 523788
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1218 pages reserved
[    0.000000]   DMA zone: 2725 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7106 pages used for memmap

[    0.000000]   DMA32 zone: 512683 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:74000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515408
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=7a7d6af2-f834-4054-8c16-fc548693450d ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   10.452780] Marking TSC unstable due to TSCs unsynchronized
[   10.452782] time.c: Detected 1994.998 MHz processor.
[   10.454921] Console: colour VGA+ 80x25
[   10.454924] console [tty0] enabled
[   10.454940] Checking aperture...
[   10.454952] Calgary: detecting Calgary via BIOS EBDA area
[   10.454954] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   10.474778] Memory: 2053704k/2095540k available (2489k kernel code, 41448k reserved, 1318k data, 320k init)
[   10.474814] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   10.554711] Calibrating delay using timer specific routine.. 3994.50 BogoMIPS (lpj=7989002)
[   10.554744] Security Framework initialized
[   10.554750] SELinux:  Disabled at boot.
[   10.554763] AppArmor: AppArmor initialized
[   10.554767] Failure registering capabilities with primary security module.
[   10.554966] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   10.556286] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   10.556867] Mount-cache hash table entries: 256
[   10.556996] Initializing cgroup subsys ns
[   10.557001] Initializing cgroup subsys cpuacct
[   10.557015] CPU: L1 I cache: 32K, L1 D cache: 32K
[   10.557017] CPU: L2 cache: 4096K
[   10.557019] CPU 0/0 -> Node 0
[   10.557021] using mwait in idle threads.
[   10.557022] CPU: Physical Processor ID: 0
[   10.557024] CPU: Processor Core ID: 0
[   10.557030] CPU0: Thermal monitoring enabled (TM2)
[   10.557043] SMP alternatives: switching to UP code
[   10.557802] Early unpacking initramfs... done
[   10.910411] ACPI: Core revision 20070126
[   10.910451] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   10.954435] Using local APIC timer interrupts.
[   11.004536] APIC timer calibration result 12468749
[   11.004538] Detected 12.468 MHz APIC timer.
[   11.004613] SMP alternatives: switching to SMP code
[   11.005263] Booting processor 1/2 APIC 0x1
[   11.015761] Initializing CPU#1
[   11.092493] Calibrating delay using timer specific routine.. 3989.97 BogoMIPS (lpj=7979942)
[   11.092499] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.092500] CPU: L2 cache: 4096K
[   11.092502] CPU 1/1 -> Node 0
[   11.092504] CPU: Physical Processor ID: 0
[   11.092505] CPU: Processor Core ID: 1
[   11.092510] CPU1: Thermal monitoring enabled (TM2)
[   11.093005] Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[   11.093091] Brought up 2 CPUs
[   11.093173] CPU0 attaching sched-domain:
[   11.093175]  domain 0: span 03
[   11.093176]   groups: 01 02
[   11.093179]   domain 1: span 03
[   11.093180]    groups: 03
[   11.093182] CPU1 attaching sched-domain:
[   11.093183]  domain 0: span 03
[   11.093184]   groups: 02 01
[   11.093186]   domain 1: span 03
[   11.093187]    groups: 03
[   11.093394] net_namespace: 120 bytes
[   11.093747] Time: 12:40:01  Date: 08/04/08
[   11.093771] NET: Registered protocol family 16
[   11.093947] ACPI: bus type pci registered
[   11.094013] PCI: Using configuration type 1
[   11.100938] ACPI: EC: Look up EC in DSDT
[   11.144243] ACPI: Interpreter enabled
[   11.144245] ACPI: (supports S0 S3 S4 S5)
[   11.144258] ACPI: Using IOAPIC for interrupt routing
[   11.163796] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.164753] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   11.164757] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[   11.166541] PCI: Transparent bridge - 0000:00:1e.0
[   11.166592] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.167069] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[   11.167217] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   11.167312] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   11.167427] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   11.167539] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   11.167650] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[   11.178463] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
[   11.178571] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[   11.178676] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
[   11.178781] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[   11.178885] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   11.178993] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   11.179099] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   11.179195] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   11.179328] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.179354] pnp: PnP ACPI init
[   11.179360] ACPI: bus type pnp registered
[   11.216841] pnpacpi: exceeded the max number of mem resources: 12
[   11.217029] pnp: PnP ACPI: found 12 devices
[   11.217031] ACPI: ACPI bus type pnp unregistered
[   11.217235] PCI: Using ACPI for IRQ routing
[   11.217237] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.232431] NET: Registered protocol family 8
[   11.232433] NET: Registered protocol family 20
[   11.232463] PCI-GART: No AMD northbridge found.
[   11.232468] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   11.232471] hpet0: 3 64-bit timers, 14318180 Hz
[   11.233504] AppArmor: AppArmor Filesystem Enabled
[   11.236412] Time: hpet clocksource has been installed.
[   11.236422] Switched to high resolution mode on CPU 0
[   11.236940] Switched to high resolution mode on CPU 1
[   11.244402] system 00:05: ioport range 0xc80-0xcff could not be reserved
[   11.244409] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
[   11.244414] system 00:09: ioport range 0x900-0x97f has been reserved
[   11.244417] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   11.244419] system 00:09: ioport range 0x1000-0x1005 has been reserved
[   11.244422] system 00:09: ioport range 0x1008-0x100f has been reserved
[   11.244427] system 00:0a: ioport range 0xf400-0xf4fe has been reserved
[   11.244430] system 00:0a: ioport range 0x1006-0x1007 has been reserved
[   11.244433] system 00:0a: ioport range 0x100a-0x1059 could not be reserved
[   11.244435] system 00:0a: ioport range 0x1060-0x107f has been reserved
[   11.244438] system 00:0a: ioport range 0x1080-0x10bf has been reserved
[   11.244441] system 00:0a: ioport range 0x10c0-0x10df has been reserved
[   11.244443] system 00:0a: ioport range 0x1010-0x102f has been reserved
[   11.244446] system 00:0a: ioport range 0x809-0x809 has been reserved
[   11.244451] system 00:0b: iomem range 0x0-0x9efff could not be reserved
[   11.244454] system 00:0b: iomem range 0x9f000-0x9ffff could not be reserved
[   11.244456] system 00:0b: iomem range 0xc0000-0xcffff has been reserved
[   11.244459] system 00:0b: iomem range 0xe0000-0xfffff has been reserved
[   11.244461] system 00:0b: iomem range 0x100000-0x7fe6d7ff could not be reserved
[   11.244464] system 00:0b: iomem range 0x7fe6d800-0x7fefffff could not be reserved
[   11.244467] system 00:0b: iomem range 0x7ff00000-0x7fffffff could not be reserved
[   11.244469] system 00:0b: iomem range 0x7ff00000-0x806fffff could not be reserved
[   11.244472] system 00:0b: iomem range 0xfff00000-0xffffffff could not be reserved
[   11.244475] system 00:0b: iomem range 0xffa00000-0xffafffff has been reserved
[   11.244478] system 00:0b: iomem range 0xfec00000-0xfec0ffff could not be reserved
[   11.244480] system 00:0b: iomem range 0xfee00000-0xfee0ffff could not be reserved
[   11.244853] PCI: Bridge: 0000:00:01.0
[   11.244855]   IO window: e000-efff
[   11.244858]   MEM window: fa000000-feafffff
[   11.244861]   PREFETCH window: e0000000-efffffff
[   11.244864] PCI: Bridge: 0000:00:1c.0
[   11.244865]   IO window: disabled.
[   11.244870]   MEM window: disabled.
[   11.244874]   PREFETCH window: disabled.
[   11.244879] PCI: Bridge: 0000:00:1c.1
[   11.244880]   IO window: disabled.
[   11.244886]   MEM window: f9f00000-f9ffffff
[   11.244890]   PREFETCH window: disabled.
[   11.244895] PCI: Bridge: 0000:00:1c.3
[   11.244898]   IO window: d000-dfff
[   11.244903]   MEM window: f9c00000-f9efffff
[   11.244907]   PREFETCH window: f0000000-f01fffff
[   11.244913] PCI: Bridge: 0000:00:1c.5
[   11.244914]   IO window: disabled.
[   11.244919]   MEM window: f9b00000-f9bfffff
[   11.244923]   PREFETCH window: disabled.
[   11.244929] PCI: Bridge: 0000:00:1e.0
[   11.244930]   IO window: disabled.
[   11.244935]   MEM window: f9a00000-f9afffff
[   11.244939]   PREFETCH window: disabled.
[   11.244954] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   11.244958] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   11.244981] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   11.244986] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   11.245010] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   11.245015] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   11.245039] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   11.245044] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   11.245067] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 17
[   11.245072] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   11.245085] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   11.245094] NET: Registered protocol family 2
[   11.280439] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   11.281050] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   11.282490] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   11.282985] TCP: Hash tables configured (established 262144 bind 65536)
[   11.282988] TCP reno registered
[   11.292489] checking if image is initramfs... it is
[   11.986223] Freeing initrd memory: 7714k freed
[   11.989783] Simple Boot Flag at 0x79 set to 0x1
[   11.990552] audit: initializing netlink socket (disabled)
[   11.990570] audit(1217853602.492:1): initialized
[   11.992437] VFS: Disk quotas dquot_6.5.1
[   11.992496] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   11.992602] io scheduler noop registered
[   11.992604] io scheduler anticipatory registered
[   11.992605] io scheduler deadline registered
[   11.992694] io scheduler cfq registered (default)
[   11.996542] Boot video device is 0000:01:00.0
[   11.996691] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   11.996724] assign_interrupt_mode Found MSI capability
[   11.996750] Allocate Port Service[0000:00:01.0:pcie00]
[   11.996783] Allocate Port Service[0000:00:01.0:pcie02]
[   11.996856] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   11.996914] assign_interrupt_mode Found MSI capability
[   11.996970] Allocate Port Service[0000:00:1c.0:pcie00]
[   11.996999] Allocate Port Service[0000:00:1c.0:pcie02]
[   11.997094] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   11.997152] assign_interrupt_mode Found MSI capability
[   11.997198] Allocate Port Service[0000:00:1c.1:pcie00]
[   11.997226] Allocate Port Service[0000:00:1c.1:pcie02]
[   11.997321] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   11.997379] assign_interrupt_mode Found MSI capability
[   11.997424] Allocate Port Service[0000:00:1c.3:pcie00]
[   11.997452] Allocate Port Service[0000:00:1c.3:pcie02]
[   11.997547] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   11.997605] assign_interrupt_mode Found MSI capability
[   11.997650] Allocate Port Service[0000:00:1c.5:pcie00]
[   11.997679] Allocate Port Service[0000:00:1c.5:pcie02]
[   12.018977] Real Time Clock Driver v1.12ac
[   12.019105] hpet_resources: 0xfed00000 is busy
[   12.019158] Linux agpgart interface v0.102
[   12.019160] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.020385] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.020439] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   12.020518] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   12.023598] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.023602] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.036972] mice: PS/2 mouse device common for all mice
[   12.037005] cpuidle: using governor ladder
[   12.037007] cpuidle: using governor menu
[   12.037118] NET: Registered protocol family 1
[   12.037212] registered taskstats version 1
[   12.037326]   Magic number: 4:715:682
[   12.037396] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   12.037398] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   12.037400] EDD information not available.
[   12.037405] Freeing unused kernel memory: 320k freed
[   12.040355] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   13.204245] fuse init (API version 7.9)
[   13.217742] ACPI: SSDT 7FE6E4F2, 0286 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   13.217934] ACPI: SSDT 7FE6DE88, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   13.218464] Monitor-Mwait will be used to enter C-1 state
[   13.218467] Monitor-Mwait will be used to enter C-2 state
[   13.218468] Monitor-Mwait will be used to enter C-3 state
[   13.218583] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   13.218587] ACPI: Processor [CPU0] (supports 8 throttling states)
[   13.218793] ACPI: SSDT 7FE6E778, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   13.218968] ACPI: SSDT 7FE6E46D, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   13.219613] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   13.219617] ACPI: Processor [CPU1] (supports 8 throttling states)
[   13.225229] ACPI: Thermal Zone [THM] (26 C)
[   13.490636] usbcore: registered new interface driver usbfs
[   13.490655] usbcore: registered new interface driver hub
[   13.490689] usbcore: registered new device driver usb
[   13.491850] USB Universal Host Controller Interface driver v3.0
[   13.491900] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 20
[   13.491911] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   13.491914] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   13.492141] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   13.492173] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[   13.492284] usb usb1: configuration #1 chosen from 1 choice
[   13.492310] hub 1-0:1.0: USB hub found
[   13.492315] hub 1-0:1.0: 2 ports detected
[   13.596067] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   13.596079] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   13.596083] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   13.596103] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   13.596134] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[   13.596224] usb usb2: configuration #1 chosen from 1 choice
[   13.596244] hub 2-0:1.0: USB hub found
[   13.596248] hub 2-0:1.0: 2 ports detected
[   13.623324] SCSI subsystem initialized
[   13.633555] libata version 3.00 loaded.
[   13.700084] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 22
[   13.701112] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   13.701119] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   13.701163] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[   13.705091] ehci_hcd 0000:00:1a.7: debug port 1
[   13.705097] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   13.705107] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[   13.718897] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.718994] usb usb3: configuration #1 chosen from 1 choice
[   13.719016] hub 3-0:1.0: USB hub found
[   13.719022] hub 3-0:1.0: 4 ports detected
[   13.822985] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[   13.822996] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   13.823000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   13.823025] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[   13.823055] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[   13.823151] usb usb4: configuration #1 chosen from 1 choice
[   13.823174] hub 4-0:1.0: USB hub found
[   13.823178] hub 4-0:1.0: 2 ports detected
[   13.926876] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 21
[   13.926886] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.926890] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.926908] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[   13.926937] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[   13.927031] usb usb5: configuration #1 chosen from 1 choice
[   13.927051] hub 5-0:1.0: USB hub found
[   13.927055] hub 5-0:1.0: 2 ports detected
[   13.996610] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 22
[   13.996623] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   13.996628] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.996659] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[   13.996691] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[   13.996794] usb usb6: configuration #1 chosen from 1 choice
[   13.996813] hub 6-0:1.0: USB hub found
[   13.996818] hub 6-0:1.0: 2 ports detected
[   14.023491] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
[   14.024439] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   14.024445] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   14.024503] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   14.028418] ehci_hcd 0000:00:1d.7: debug port 1
[   14.028425] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   14.028431] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[   14.048388] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   14.048485] usb usb7: configuration #1 chosen from 1 choice
[   14.048507] hub 7-0:1.0: USB hub found
[   14.048512] hub 7-0:1.0: 6 ports detected
[   14.085924] tg3.c:v3.86 (November 9, 2007)
[   14.085976] ata_piix 0000:00:1f.1: version 2.12
[   14.085984] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   14.085991] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   14.086001] PCI: Setting latency timer of device 0000:09:00.0 to 64
[   14.086029] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   14.087697] scsi0 : ata_piix
[   14.088392] scsi1 : ata_piix
[   14.088977] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[   14.088980] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[   14.125695] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   14.158382] Clocksource tsc unstable (delta = -331274616 ns)
[   14.172377] usb 1-2: configuration #1 chosen from 1 choice
[   14.173682] hub 1-2:1.0: USB hub found
[   14.175645] hub 1-2:1.0: 3 ports detected
[   14.198918] eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:1a:a0:fd:64:0b
[   14.198923] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[0]
[   14.198925] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   14.198975] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 19
[   14.228715] ata1.00: ATAPI: PIONEER DVD+/-RW DR-K17Y, 0.95, max UDMA/33
[   14.252127] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f9aff800-f9afffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   14.298939] ata1.00: configured for UDMA/33
[   14.299032] ata2: port disabled. ignoring.
[   14.308341] scsi 0:0:0:0: CD-ROM            PIONEER  DVD+-RW DR-K17Y  0.95 PQ: 0 ANSI: 5
[   14.310763] ahci 0000:00:1f.2: version 3.0
[   14.310786] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   14.311715] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x5) don't match, using nr_ports
[   14.311718] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   14.361701] usb 7-6: new high speed USB device using ehci_hcd and address 2
[   14.498690] usb 7-6: configuration #1 chosen from 1 choice
[   14.672373] usb 1-2.1: new full speed USB device using uhci_hcd and address 3
[   14.737782] usb 1-2.1: configuration #1 chosen from 1 choice
[   14.864418] usb 1-2.2: new full speed USB device using uhci_hcd and address 4
[   14.925882] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   14.925887] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   14.925894] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   14.926101] scsi2 : ahci
[   14.926270] scsi3 : ahci
[   14.926400] scsi4 : ahci
[   14.926643] ata3: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb900 irq 506
[   14.926647] ata4: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb980 irq 506
[   14.926652] ata5: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfba00 irq 506
[   14.931937] usb 1-2.2: configuration #1 chosen from 1 choice
[   14.969878] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[474fc0000bd1b581]
[   15.043372] usb 1-2.3: new full speed USB device using uhci_hcd and address 5
[   15.106640] usb 1-2.3: configuration #1 chosen from 1 choice
[   15.110028] usbcore: registered new interface driver hiddev
[   15.113211] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2.2/1-2.2:1.0/input/input2
[   15.127568] input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2
[   15.132324] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2.3/1-2.3:1.0/input/input3
[   15.145530] input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3
[   15.145547] usbcore: registered new interface driver usbhid
[   15.145551] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   15.173754] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   15.566421] ata3.00: ATA-7: TOSHIBA MK1237GSX, DL140D, max UDMA/100
[   15.566424] ata3.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 31/32)
[   15.567354] ata3.00: configured for UDMA/100
[   15.630324] ata4: SATA link down (SStatus 0 SControl 0)
[   15.696990] ata5: SATA link down (SStatus 0 SControl 300)
[   15.697119] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK1237GS DL14 PQ: 0 ANSI: 5
[   15.707056] Driver 'sd' needs updating - please use bus_type methods
[   15.711875] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   15.711886] sd 2:0:0:0: [sda] Write Protect is off
[   15.711888] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.711901] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.711938] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   15.711945] sd 2:0:0:0: [sda] Write Protect is off
[   15.711947] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.711960] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.711963]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   15.761059] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   15.761063] Uniform CD-ROM driver Revision: 3.20
[   15.761117] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   15.774382]  sda1 sda2 < sda5 sda6 sda7 sda8 >
[   15.822982] sd 2:0:0:0: [sda] Attached SCSI disk
[   15.826706] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   15.826722] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   17.385359] kjournald starting.  Commit interval 5 seconds
[   17.385366] EXT3-fs: mounted filesystem with ordered data mode.
[   30.506179] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   30.606480] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.766715] iTCO_vendor_support: vendor-support=0
[   30.781235] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   30.834249] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.874911] input: PS/2 Mouse as /devices/virtual/input/input5
[   30.936862] input: Lid Switch as /devices/virtual/input/input6
[   30.940468] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input7
[   30.957578] ACPI: Lid Switch [LID]
[   30.957625] input: Power Button (CM) as /devices/virtual/input/input8
[   31.017267] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   31.017325] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   31.017362] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   31.069056] ACPI: Power Button (CM) [PBTN]
[   31.069108] input: Sleep Button (CM) as /devices/virtual/input/input9
[   31.103823] ricoh-mmc: Ricoh MMC Controller disabling driver
[   31.103826] ricoh-mmc: Copyright(c) Philip Langdale
[   31.103863] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 12)
[   31.103875] ricoh-mmc: Controller is now disabled.
[   31.133009] ACPI: Sleep Button (CM) [SBTN]
[   31.160580] ACPI: Battery Slot [BAT0] (battery present)
[   31.160652] ACPI: AC Adapter [AC] (on-line)
[   31.160902] ACPI: WMI-Acer: Mapper loaded
[   31.352476] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/LNXVIDEO:00/input/input10
[   31.405826] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   31.414753] sdhci: Secure Digital Host Controller Interface driver
[   31.414755] sdhci: Copyright(c) Pierre Ossman
[   31.414787] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 22)
[   31.414810] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 18
[   31.418756] mmc0: SDHCI at 0xf9aff400 irq 18 DMA
[   31.423764] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input11
[   31.485781] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   31.485922] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input12
[   31.549735] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   31.619516] nvidia: module license 'NVIDIA' taints kernel.
[   31.899471] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.899482] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   31.899562] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   31.917554] Linux video capture interface: v2.00
[   32.021678] Bluetooth: Core ver 2.11
[   32.023550] NET: Registered protocol family 31
[   32.023552] Bluetooth: HCI device and connection manager initialized
[   32.023555] Bluetooth: HCI socket layer initialized
[   32.060568] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   32.060571] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   32.060707] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   32.060722] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   32.061620] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   32.081223] Bluetooth: HCI USB driver ver 2.9
[   32.083130] usbcore: registered new interface driver hci_usb
[   32.101139] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   32.101570] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   32.158712] usbcore: registered new interface driver uvcvideo
[   32.158716] USB Video Class driver (v0.1.0)
[   32.336096] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
[   32.337043] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   32.988729] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   32.997188] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   33.782703] lp: driver loaded but no devices found
[   33.931568] Adding 4096532k swap on /dev/sda6.  Priority:-1 extents:1 across:4096532k
[   34.232946] EXT3 FS on sda8, internal journal
[   34.778246] kjournald starting.  Commit interval 5 seconds
[   34.778473] EXT3 FS on sda1, internal journal
[   34.778478] EXT3-fs: mounted filesystem with ordered data mode.
[   35.261909] ip_tables: (C) 2000-2006 Netfilter Core Team
```

---

### Post by coffeecat on 2008-08-04
[Here you go](http://ubuntuforums.org/showthread.php?t=857565). :wink: Look at my first post in that thread.

---

### Post by muadnu on 2008-08-04
Thanks for the quick answer! That was exactly it, back to normal now.

---

### Post by coffeecat on 2008-08-04
Glad it's working. I didn't even have to read your post (I did though). Your title told me exactly which thread to link to. You couldn't give some lessons to all the "helppppppp plzzzzzzz!!!!" merchants, could you? :)

---

### Post by muadnu on 2008-08-04
I have to say that I did give some thought to the title of the thread, I wasn't sure how to put it. So I'm glad it was good enough :). Thanks again...

---

