---
title: "Slow disk performance"
date: 2008-07-29
forum: General Help
---

### Post by isecore on 2008-07-29
I've posted about this before, maybe six months back but I'm giving it another attempt.

I'm running Hardy x64 with all updates currently applied as of July 29th. I've been an Ubuntu convert since January 2007 and have used Linux on and off again for the better part of a decade and a half.

However there is one thing which annoys the cr*p out of me. Disk performance under Hardy is miserably slow. Or rather, the disks are fine but whenever I do something fairly disk-intense such as unpacking archives, burning a dvd at high speed or copying large files the CPU-usage goes through the roof - at least three cores on my quadcore just bottoms out. Applications turn grey, commands take longer to execute. Multitasking for all intents and purposes ceases to exist whenever I do something like this.

What is this, Windows 3.11? I never had this problem under Edgy, Feisty or Gutsy.

Some information that might be useful:

uname -a:
```
Linux superbeast 2.6.24-20-generic #1 SMP Mon Jul 28 13:06:07 UTC 2008 x86_64 GNU/Linux
```

dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-20-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jul 28 13:06:07 UTC 2008 (Ubuntu 2.6.24-20.38-generic)
[    0.000000] Command line: root=/dev/mapper/superbeast-root ro quiet splash vga=normal
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 158) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 851680) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1245184
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6FC0 checksum 0
[    0.000000] ACPI: RSDP 000F6FC0, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT CFEE3000, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP CFEE3040, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT CFEE30C0, 66F8 (r1 GBT    GBTUACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS CFEE0000, 0040
[    0.000000] ACPI: SSDT CFEE9880, 0544 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: HPET CFEE9E00, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG CFEE9E40, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC CFEE97C0, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Entering add_active_range(0, 0, 158) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 851680) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1245184
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      158
[    0.000000]     0:      256 ->   851680
[    0.000000]     0:  1048576 ->  1245184
[    0.000000] On node 0 totalpages: 1048190
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1222 pages reserved
[    0.000000]   DMA zone: 2720 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833304 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] Processor #2
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] Processor #3
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000cfee0000 - 00000000cfee3000
[    0.000000] swsusp: Registered nosave memory region: 00000000cfee3000 - 00000000cfef0000
[    0.000000] swsusp: Registered nosave memory region: 00000000cfef0000 - 00000000cff00000
[    0.000000] swsusp: Registered nosave memory region: 00000000cff00000 - 00000000e0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000e0000000 - 00000000f0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000f0000000 - 00000000fec00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: cff00000:10100000)
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1029944
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=/dev/mapper/superbeast-root ro quiet splash vga=normal
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   35.171790] Marking TSC unstable due to TSCs unsynchronized
[   35.171792] time.c: Detected 2210.074 MHz processor.
[   35.173199] Console: colour VGA+ 80x25
[   35.173202] console [tty0] enabled
[   35.173219] Checking aperture...
[   35.173221] CPU 0: aperture @ 4000000 size 32 MB
[   35.173222] Aperture too small (32 MB)
[   35.182516] No AGP bridge found
[   35.182517] Your BIOS doesn't leave a aperture memory hole
[   35.182519] Please enable the IOMMU option in the BIOS setup
[   35.182520] This costs you 64 MB of RAM
[   35.203894] Mapping aperture over 65536 KB of RAM @ 4000000
[   35.203899] swsusp: Registered nosave memory region: 0000000004000000 - 0000000008000000
[   35.230484] Memory: 4045692k/4980736k available (2489k kernel code, 147068k reserved, 1318k data, 320k init)
[   35.230514] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   35.309672] Calibrating delay using timer specific routine.. 4423.42 BogoMIPS (lpj=8846845)
[   35.309697] Security Framework initialized
[   35.309703] SELinux:  Disabled at boot.
[   35.309713] AppArmor: AppArmor initialized
[   35.309716] Failure registering capabilities with primary security module.
[   35.309966] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   35.311599] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   35.312325] Mount-cache hash table entries: 256
[   35.312432] Initializing cgroup subsys ns
[   35.312436] Initializing cgroup subsys cpuacct
[   35.312447] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   35.312449] CPU: L2 Cache: 512K (64 bytes/line)
[   35.312451] CPU 0/0 -> Node 0
[   35.312453] CPU: Physical Processor ID: 0
[   35.312454] CPU: Processor Core ID: 0
[   35.312474] SMP alternatives: switching to UP code
[   35.312995] Early unpacking initramfs... done
[   35.584124] ACPI: Core revision 20070126
[   35.584178] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   35.652983] Using local APIC timer interrupts.
[   35.698205] APIC timer calibration result 12557229
[   35.698206] Detected 12.557 MHz APIC timer.
[   35.698282] SMP alternatives: switching to SMP code
[   35.698720] Booting processor 1/4 APIC 0x1
[   35.708991] Initializing CPU#1
[   35.786149] Calibrating delay using timer specific routine.. 4420.19 BogoMIPS (lpj=8840392)
[   35.786155] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   35.786156] CPU: L2 Cache: 512K (64 bytes/line)
[   35.786158] CPU 1/1 -> Node 0
[   35.786160] CPU: Physical Processor ID: 0
[   35.786161] CPU: Processor Core ID: 1
[   35.786452] AMD Phenom(tm) 9500 Quad-Core Processor stepping 02
[   35.786518] SMP alternatives: switching to SMP code
[   35.786822] Booting processor 2/4 APIC 0x2
[   35.797093] Initializing CPU#2
[   35.874085] Calibrating delay using timer specific routine.. 4420.19 BogoMIPS (lpj=8840397)
[   35.874091] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   35.874093] CPU: L2 Cache: 512K (64 bytes/line)
[   35.874095] CPU 2/2 -> Node 0
[   35.874097] CPU: Physical Processor ID: 0
[   35.874098] CPU: Processor Core ID: 3
[   35.874389] AMD Phenom(tm) 9500 Quad-Core Processor stepping 02
[   35.874519] SMP alternatives: switching to SMP code
[   35.874824] Booting processor 3/4 APIC 0x3
[   35.885095] Initializing CPU#3
[   35.962022] Calibrating delay using timer specific routine.. 4420.20 BogoMIPS (lpj=8840404)
[   35.962028] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   35.962030] CPU: L2 Cache: 512K (64 bytes/line)
[   35.962031] CPU 3/3 -> Node 0
[   35.962033] CPU: Physical Processor ID: 0
[   35.962034] CPU: Processor Core ID: 2
[   35.962325] AMD Phenom(tm) 9500 Quad-Core Processor stepping 02
[   35.962386] Brought up 4 CPUs
[   35.962520] CPU0 attaching sched-domain:
[   35.962522]  domain 0: span 0f
[   35.962524]   groups: 01 02 04 08
[   35.962527]   domain 1: span 0f
[   35.962528]    groups: 0f
[   35.962530] CPU1 attaching sched-domain:
[   35.962531]  domain 0: span 0f
[   35.962532]   groups: 02 04 08 01
[   35.962534]   domain 1: span 0f
[   35.962535]    groups: 0f
[   35.962536] CPU2 attaching sched-domain:
[   35.962537]  domain 0: span 0f
[   35.962538]   groups: 04 08 01 02
[   35.962540]   domain 1: span 0f
[   35.962542]    groups: 0f
[   35.962543] CPU3 attaching sched-domain:
[   35.962544]  domain 0: span 0f
[   35.962545]   groups: 08 01 02 04
[   35.962547]   domain 1: span 0f
[   35.962548]    groups: 0f
[   35.962785] net_namespace: 120 bytes
[   35.963115] Time: 10:34:01  Date: 07/29/08
[   35.963138] NET: Registered protocol family 16
[   35.963276] ACPI: bus type pci registered
[   35.963332] PCI: Using configuration type 1
[   35.964476] ACPI: EC: Look up EC in DSDT
[   35.969229] ACPI: Interpreter enabled
[   35.969231] ACPI: (supports S0 S1 S4 S5)
[   35.969242] ACPI: Using IOAPIC for interrupt routing
[   35.972912] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   35.974307] PCI: Transparent bridge - 0000:00:14.4
[   35.974330] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   35.974555] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   35.974662] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[   35.974751] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[   35.990787] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   35.990893] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   35.990997] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   35.991101] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   35.991204] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   35.991307] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   35.991410] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   35.991513] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[   35.991609] Linux Plug and Play Support v0.97 (c) Adam Belay
[   35.991630] pnp: PnP ACPI init
[   35.991636] ACPI: bus type pnp registered
[   35.993627] pnp: PnP ACPI: found 10 devices
[   35.993629] ACPI: ACPI bus type pnp unregistered
[   35.993780] PCI: Using ACPI for IRQ routing
[   35.993783] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   36.006025] NET: Registered protocol family 8
[   36.006026] NET: Registered protocol family 20
[   36.006082] PCI-DMA: Disabling AGP.
[   36.007109] PCI-DMA: aperture base @ 4000000 size 65536 KB
[   36.007113] PCI-DMA: using GART IOMMU.
[   36.007120] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[   36.008033] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   36.008037] hpet0: 4 32-bit timers, 14318180 Hz
[   36.009089] AppArmor: AppArmor Filesystem Enabled
[   36.009992] Time: hpet clocksource has been installed.
[   36.010008] Switched to high resolution mode on CPU 0
[   36.010330] Switched to high resolution mode on CPU 3
[   36.010335] Switched to high resolution mode on CPU 2
[   36.010340] Switched to high resolution mode on CPU 1
[   36.018024] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   36.018028] system 00:01: ioport range 0x220-0x225 has been reserved
[   36.018030] system 00:01: ioport range 0x290-0x294 has been reserved
[   36.018036] system 00:02: ioport range 0x4100-0x411f has been reserved
[   36.018039] system 00:02: ioport range 0x228-0x22f has been reserved
[   36.018041] system 00:02: ioport range 0x40b-0x40b has been reserved
[   36.018043] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
[   36.018045] system 00:02: ioport range 0xc00-0xc01 has been reserved
[   36.018047] system 00:02: ioport range 0xc14-0xc14 has been reserved
[   36.018049] system 00:02: ioport range 0xc50-0xc52 has been reserved
[   36.018050] system 00:02: ioport range 0xc6c-0xc6d has been reserved
[   36.018052] system 00:02: ioport range 0xc6f-0xc6f has been reserved
[   36.018054] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
[   36.018056] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
[   36.018058] system 00:02: ioport range 0xcd4-0xcdf has been reserved
[   36.018060] system 00:02: ioport range 0x4000-0x40fe has been reserved
[   36.018062] system 00:02: ioport range 0x4210-0x4217 has been reserved
[   36.018065] system 00:02: ioport range 0xb00-0xb1f could not be reserved
[   36.018067] system 00:02: ioport range 0x238-0x23f has been reserved
[   36.018076] system 00:08: iomem range 0xe0000000-0xefffffff could not be reserved
[   36.018082] system 00:09: iomem range 0xd2800-0xd3fff has been reserved
[   36.018084] system 00:09: iomem range 0xf0000-0xf7fff could not be reserved
[   36.018086] system 00:09: iomem range 0xf8000-0xfbfff could not be reserved
[   36.018088] system 00:09: iomem range 0xfc000-0xfffff could not be reserved
[   36.018090] system 00:09: iomem range 0xcfee0000-0xcfefffff could not be reserved
[   36.018093] system 00:09: iomem range 0xffff0000-0xffffffff has been reserved
[   36.018095] system 00:09: iomem range 0x0-0x9ffff could not be reserved
[   36.018097] system 00:09: iomem range 0x100000-0xcfedffff could not be reserved
[   36.018099] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[   36.018101] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[   36.018103] system 00:09: iomem range 0xfff80000-0xfffeffff has been reserved
[   36.018433] PCI: Bridge: 0000:00:02.0
[   36.018435]   IO window: d000-dfff
[   36.018438]   MEM window: f8000000-fbffffff
[   36.018441]   PREFETCH window: d0000000-dfffffff
[   36.018445] PCI: Bridge: 0000:00:07.0
[   36.018447]   IO window: e000-efff
[   36.018449]   MEM window: fdf00000-fdffffff
[   36.018451]   PREFETCH window: fde00000-fdefffff
[   36.018455] PCI: Bridge: 0000:00:14.4
[   36.018457]   IO window: c000-cfff
[   36.018462]   MEM window: fdd00000-fddfffff
[   36.018466]   PREFETCH window: fdc00000-fdcfffff
[   36.018482] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   36.018488] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   36.018502] NET: Registered protocol family 2
[   36.054035] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   36.054939] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   36.058026] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   36.058426] TCP: Hash tables configured (established 524288 bind 65536)
[   36.058428] TCP reno registered
[   36.070044] checking if image is initramfs... it is
[   36.598001] Freeing initrd memory: 8197k freed
[   36.602406] audit: initializing netlink socket (disabled)
[   36.602418] audit(1217327641.372:1): initialized
[   36.603996] VFS: Disk quotas dquot_6.5.1
[   36.604051] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   36.604149] io scheduler noop registered
[   36.604151] io scheduler anticipatory registered
[   36.604152] io scheduler deadline registered
[   36.604224] io scheduler cfq registered (default)
[   36.747141] Boot video device is 0000:01:00.0
[   36.747290] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   36.747309] assign_interrupt_mode Found MSI capability
[   36.747331] Allocate Port Service[0000:00:02.0:pcie00]
[   36.747384] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   36.747402] assign_interrupt_mode Found MSI capability
[   36.747420] Allocate Port Service[0000:00:07.0:pcie00]
[   36.765313] Real Time Clock Driver v1.12ac
[   36.765492] hpet_resources: 0xfed00000 is busy
[   36.765535] Linux agpgart interface v0.102
[   36.765538] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   36.766665] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   36.766715] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   36.766807] PNP: No PS/2 controller found. Probing ports directly.
[   36.767140] serio: i8042 KBD port at 0x60,0x64 irq 1
[   36.767148] serio: i8042 AUX port at 0x60,0x64 irq 12
[   36.778441] mice: PS/2 mouse device common for all mice
[   36.778477] cpuidle: using governor ladder
[   36.778479] cpuidle: using governor menu
[   36.778589] NET: Registered protocol family 1
[   36.778676] registered taskstats version 1
[   36.778790]   Magic number: 0:275:579
[   36.778896] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   36.778899] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   36.778901] EDD information not available.
[   36.778910] Freeing unused kernel memory: 320k freed
[   37.984025] fuse init (API version 7.9)
[   38.008367] device-mapper: uevent: version 1.0.3
[   38.008403] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   38.183136] usbcore: registered new interface driver usbfs
[   38.183143] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   38.183150] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   38.183174] usbcore: registered new interface driver hub
[   38.183726] usbcore: registered new device driver usb
[   38.183776] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
[   38.183796] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   38.183806] SB600_PATA: not 100% native mode: will probe irqs later
[   38.183813]     ide0: BM-DMA at 0xf900-0xf907, BIOS settings: hda:DMA, hdb:DMA
[   38.183832] Probing IDE interface ide0...
[   38.200249] SCSI subsystem initialized
[   38.221642] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   38.256358] libata version 3.00 loaded.
[   38.473416] hdb: ST3160021A, ATA DISK drive
[   38.920054] hda: _NEC DVD_RW ND-3540A, ATAPI CD/DVD-ROM drive
[   38.920066] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   38.920110] hda: UDMA/33 mode selected
[   38.920304] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   38.920690] hdb: host side 80-wire cable detection failed, limiting max speed to UDMA33
[   38.920692] hdb: UDMA/33 mode selected
[   38.920953] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   38.926249] ahci 0000:00:12.0: version 3.0
[   38.926284] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
[   38.926978] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[   38.926983] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
[   39.926994] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   39.926999] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
[   39.929558] scsi0 : ahci
[   39.929608] scsi1 : ahci
[   39.929644] scsi2 : ahci
[   39.929681] scsi3 : ahci
[   39.929737] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[   39.929740] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[   39.929743] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[   39.929746] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[   40.514482] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   40.521837] ata1.00: HPA unlocked: 390719855 -> 390721968, native 390721968
[   40.521843] ata1.00: ATA-6: ST3200822AS, 3.01, max UDMA/133
[   40.521845] ata1.00: 390721968 sectors, multi 16: LBA48 
[   40.525666] ata1.00: configured for UDMA/133
[   40.834227] ata2: SATA link down (SStatus 0 SControl 300)
[   41.309862] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   41.310539] ata3.00: ATA-8: WDC WD6400AAKS-65A7B0, 01.03B01, max UDMA/133
[   41.310542] ata3.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   41.311262] ata3.00: configured for UDMA/133
[   41.621615] ata4: SATA link down (SStatus 0 SControl 300)
[   41.621718] scsi 0:0:0:0: Direct-Access     ATA      ST3200822AS      3.01 PQ: 0 ANSI: 5
[   41.621799] scsi 2:0:0:0: Direct-Access     ATA      WDC WD6400AAKS-6 01.0 PQ: 0 ANSI: 5
[   41.621910] pata_pdc2027x 0000:03:07.0: version 1.0
[   41.621951] ACPI: PCI Interrupt 0000:03:07.0[A] -> GSI 21 (level, low) -> IRQ 21
[   41.722577] pata_pdc2027x 0000:03:07.0: PLL input clock 16571 kHz
[   41.752640] scsi4 : pata_pdc2027x
[   41.752696] scsi5 : pata_pdc2027x
[   41.752716] ata5: PATA max UDMA/100 mmio m16384@0xfddf8000 cmd 0xfddf97c0 irq 21
[   41.752718] ata6: PATA max UDMA/100 mmio m16384@0xfddf8000 cmd 0xfddf95c0 irq 21
[   42.097837] ata5.00: HPA unlocked: 390719855 -> 390721968, native 390721968
[   42.097843] ata5.00: ATA-6: ST3200822A, 3.01, max UDMA/100
[   42.097845] ata5.00: 390721968 sectors, multi 16: LBA48 
[   42.098206] ata5.01: ATA-6: ST3120022A, 3.54, max UDMA/100
[   42.098207] ata5.01: 234441648 sectors, multi 16: LBA48 
[   42.114027] ata5.00: configured for UDMA/100
[   42.129994] ata5.01: configured for UDMA/100
[   42.297419] scsi 4:0:0:0: Direct-Access     ATA      ST3200822A       3.01 PQ: 0 ANSI: 5
[   42.297493] scsi 4:0:1:0: Direct-Access     ATA      ST3120022A       3.54 PQ: 0 ANSI: 5
[   42.297573] r8169 Gigabit Ethernet driver 2.2LK loaded
[   42.297605] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   42.297624] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   42.297865] eth0: RTL8168b/8111b at 0xffffc2000103a000, 00:1a:4d:5d:c0:8f, XID 38000000 IRQ 509
[   42.298988] ACPI: PCI Interrupt 0000:03:06.2[B] -> GSI 21 (level, low) -> IRQ 21
[   42.349130] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fddff000-fddff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   42.349205] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
[   42.349209] Driver 'sd' needs updating - please use bus_type methods
[   42.349719] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   42.349729] sd 0:0:0:0: [sda] Write Protect is off
[   42.349732] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   42.349742] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.349789] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   42.349795] sd 0:0:0:0: [sda] Write Protect is off
[   42.349797] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   42.349806] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.349809]  sda:<6>ehci_hcd 0000:00:13.5: EHCI Host Controller
[   42.350109] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[   42.350150] ehci_hcd 0000:00:13.5: debug port 1
[   42.350168] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
[   42.356180]  unknown partition table
[   42.356232] sd 0:0:0:0: [sda] Attached SCSI disk
[   42.356567] sd 2:0:0:0: [sdb] 1250263728 512-byte hardware sectors (640135 MB)
[   42.356576] sd 2:0:0:0: [sdb] Write Protect is off
[   42.356578] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   42.356589] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.356624] sd 2:0:0:0: [sdb] 1250263728 512-byte hardware sectors (640135 MB)
[   42.356630] sd 2:0:0:0: [sdb] Write Protect is off
[   42.356632] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   42.356641] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.356644]  sdb:<6>ACPI: PCI Interrupt 0000:03:0e.0[A] -> GSI 22 (level, low) -> IRQ 22
[   42.378100]  sdb1 sdb2 <<6>ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   42.378259] usb usb1: configuration #1 chosen from 1 choice
[   42.378279] hub 1-0:1.0: USB hub found
[   42.378288] hub 1-0:1.0: 10 ports detected
[   42.384392]  sdb5 >
[   42.384467] sd 2:0:0:0: [sdb] Attached SCSI disk
[   42.384520] sd 4:0:0:0: [sdc] 390721968 512-byte hardware sectors (200050 MB)
[   42.384529] sd 4:0:0:0: [sdc] Write Protect is off
[   42.384531] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   42.384541] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.384571] sd 4:0:0:0: [sdc] 390721968 512-byte hardware sectors (200050 MB)
[   42.384577] sd 4:0:0:0: [sdc] Write Protect is off
[   42.384579] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   42.384588] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.384591]  sdc: unknown partition table
[   42.398483] sd 4:0:0:0: [sdc] Attached SCSI disk
[   42.398518] sd 4:0:1:0: [sdd] 234441648 512-byte hardware sectors (120034 MB)
[   42.398525] sd 4:0:1:0: [sdd] Write Protect is off
[   42.398526] sd 4:0:1:0: [sdd] Mode Sense: 00 3a 00 00
[   42.398536] sd 4:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.398562] sd 4:0:1:0: [sdd] 234441648 512-byte hardware sectors (120034 MB)
[   42.398568] sd 4:0:1:0: [sdd] Write Protect is off
[   42.398569] sd 4:0:1:0: [sdd] Mode Sense: 00 3a 00 00
[   42.398578] sd 4:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.398580]  sdd: unknown partition table
[   42.407160] sd 4:0:1:0: [sdd] Attached SCSI disk
[   42.407242] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fddfe000-fddfe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   42.410381] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   42.410399] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   42.410414] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   42.410428] sd 4:0:1:0: Attached scsi generic sg3 type 0
[   42.482039] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
[   42.482728] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   42.482790] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[   42.482812] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
[   42.545000] usb usb2: configuration #1 chosen from 1 choice
[   42.545022] hub 2-0:1.0: USB hub found
[   42.545037] hub 2-0:1.0: 2 ports detected
[   42.644879] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
[   42.645601] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   42.645656] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[   42.645680] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
[   42.704855] usb usb3: configuration #1 chosen from 1 choice
[   42.704876] hub 3-0:1.0: USB hub found
[   42.704884] hub 3-0:1.0: 2 ports detected
[   42.812738] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
[   42.813373] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   42.813433] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[   42.813456] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
[   42.872739] usb usb4: configuration #1 chosen from 1 choice
[   42.872758] hub 4-0:1.0: USB hub found
[   42.872766] hub 4-0:1.0: 2 ports detected
[   42.980601] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
[   42.981241] ohci_hcd 0000:00:13.3: OHCI Host Controller
[   42.981304] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[   42.981322] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
[   43.040648] usb usb5: configuration #1 chosen from 1 choice
[   43.040667] hub 5-0:1.0: USB hub found
[   43.040675] hub 5-0:1.0: 2 ports detected
[   43.092455] usb 1-3: new high speed USB device using ehci_hcd and address 4
[   43.144465] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
[   43.145093] ohci_hcd 0000:00:13.4: OHCI Host Controller
[   43.145154] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[   43.145172] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
[   43.204473] usb usb6: configuration #1 chosen from 1 choice
[   43.204492] hub 6-0:1.0: USB hub found
[   43.204500] hub 6-0:1.0: 2 ports detected
[   43.226622] usb 1-3: configuration #1 chosen from 1 choice
[   43.339858] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[   43.339865] Uniform CD-ROM driver Revision: 3.20
[   43.342696] hdb: max request size: 512KiB
[   43.349307] hdb: Host Protected Area detected.
[   43.349309] 	current capacity is 312579695 sectors (160040 MB)
[   43.349310] 	native  capacity is 312581808 sectors (160041 MB)
[   43.349753] hdb: Host Protected Area disabled.
[   43.349756] hdb: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63
[   43.349903] hdb: cache flushes supported
[   43.349936]  hdb: hdb1
[   43.625637] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c01510fbd1b]
[   43.659738] Attempting manual resume
[   43.659741] swsusp: Resume From Partition 254:1
[   43.659743] PM: Checking swsusp image.
[   43.659877] PM: Resume from disk failed.
[   43.686635] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[00cd8cde00001a4d]
[   43.714855] kjournald starting.  Commit interval 5 seconds
[   43.714862] EXT3-fs: mounted filesystem with ordered data mode.
[   44.444407] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   44.668460] usb 2-1: configuration #1 chosen from 1 choice
[   44.979982] usb 2-2: new low speed USB device using ohci_hcd and address 3
[   45.201067] usb 2-2: configuration #1 chosen from 1 choice
[   45.203123] usbcore: registered new interface driver libusual
[   45.639467] usb 3-2: new full speed USB device using ohci_hcd and address 2
[   45.851589] usb 3-2: configuration #1 chosen from 1 choice
[   46.162063] usb 4-1: new full speed USB device using ohci_hcd and address 2
[   46.606046] usb 4-1: configuration #1 chosen from 1 choice
[   46.921470] usb 5-2: new full speed USB device using ohci_hcd and address 2
[   47.141693] usb 5-2: configuration #1 chosen from 1 choice
[   47.457051] usb 6-1: new low speed USB device using ohci_hcd and address 2
[   47.684243] usb 6-1: configuration #1 chosen from 1 choice
[   49.450982] Initializing USB Mass Storage driver...
[   49.451055] scsi6 : SCSI emulation for USB Mass Storage devices
[   49.451102] usb-storage: device found at 4
[   49.451106] usb-storage: waiting for device to settle before scanning
[   49.451154] usbcore: registered new interface driver usb-storage
[   49.451157] USB Mass Storage support registered.
[   50.904094] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   50.915928] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   50.944789] input: Power Button (FF) as /devices/virtual/input/input1
[   50.967827] ACPI: Power Button (FF) [PWRF]
[   50.967899] input: Power Button (CM) as /devices/virtual/input/input2
[   50.999799] ACPI: Power Button (CM) [PWRB]
[   51.128593] ACPI: WMI-Acer: Mapper loaded
[   51.248048] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   51.318595] Bluetooth: Core ver 2.11
[   51.355432] NET: Registered protocol family 31
[   51.355435] Bluetooth: HCI device and connection manager initialized
[   51.355440] Bluetooth: HCI socket layer initialized
[   51.644274] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   51.884213] nvidia: module license 'NVIDIA' taints kernel.
[   52.138157] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   52.138167] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   52.138266] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  171.06  Wed Feb 20 09:02:26 PST 2008
[   52.169419] Bluetooth: HCI USB driver ver 2.9
[   52.170326] usbcore: registered new interface driver hci_usb
[   52.195031] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x0686 pid 0x3009
[   52.195044] usbcore: registered new interface driver usblp
[   52.202994] Linux video capture interface: v2.00
[   52.299517] gameport: EMU10K1 is pci0000:03:06.1/gameport0, io 0xce00, speed 608kHz
[   52.350358] usbcore: registered new interface driver hiddev
[   52.359984] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input4
[   52.399522] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-1
[   52.403963] input: Logitech USB Multimedia Keyboard as /devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.0/input/input5
[   52.630095] input,hidraw1: USB HID v1.10 Keyboard [Logitech USB Multimedia Keyboard] on usb-0000:00:13.0-2
[   52.639657] input: Logitech USB Multimedia Keyboard as /devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.1/input/input6
[   52.676484] ACPI: PCI Interrupt 0000:03:06.0[A] -> GSI 20 (level, low) -> IRQ 20
[   52.683027] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emufx.c:1544: Installing spdif_bug patch: Audigy 2 ZS [SB0350]
[   52.713990] input,hidraw2: USB HID v1.10 Device [Logitech USB Multimedia Keyboard] on usb-0000:00:13.0-2
[   52.714061] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[   52.714064] quickcam: Kernel:2.6.24-20-generic bus:3 class:FF subclass:FF vendor:046D product:0850
[   52.740536] quickcam: Sensor VV6410 detected
[   52.744570] quickcam: Registered device: /dev/video0
[   54.443841] usb-storage: device scan complete
[   54.445075] scsi 6:0:0:0: Direct-Access     Generic  IC1210        CF 1.9C PQ: 0 ANSI: 0 CCS
[   54.446183] scsi 6:0:0:1: Direct-Access     Generic  IC1210        MS 1.9C PQ: 0 ANSI: 0 CCS
[   54.447306] scsi 6:0:0:2: Direct-Access     Generic  IC1210    MMC/SD 1.9C PQ: 0 ANSI: 0 CCS
[   54.448430] scsi 6:0:0:3: Direct-Access     Generic  IC1210        SM 1.9C PQ: 0 ANSI: 0 CCS
[   54.456635] sd 6:0:0:0: [sde] Attached SCSI removable disk
[   54.456675] sd 6:0:0:0: Attached scsi generic sg4 type 0
[   54.457849] sd 6:0:0:1: [sdf] Attached SCSI removable disk
[   54.457883] sd 6:0:0:1: Attached scsi generic sg5 type 0
[   54.458968] sd 6:0:0:2: [sdg] Attached SCSI removable disk
[   54.459000] sd 6:0:0:2: Attached scsi generic sg6 type 0
[   54.460102] sd 6:0:0:3: [sdh] Attached SCSI removable disk
[   54.460138] sd 6:0:0:3: Attached scsi generic sg7 type 0
[   62.713291] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
[   62.713303] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: timeout initializing reports
[   62.713371] input: Logitech Logitech Dual Action as /devices/pci0000:00/0000:00:13.4/usb6/6-1/6-1:1.0/input/input7
[   62.722166] input,hidraw3: USB HID v1.10 Joystick [Logitech Logitech Dual Action] on usb-0000:00:13.4-1
[   62.722185] usbcore: registered new interface driver usbhid
[   62.722188] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   62.722313] usbcore: registered new interface driver lmpcm_usb
[   62.722316] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   62.722417] usbcore: registered new interface driver quickcam
[   62.722675] usbcore: registered new interface driver snd-usb-audio
[   63.510310] loop: module loaded
[   63.599529] lp: driver loaded but no devices found
[   63.779709] it87: Found IT8718F chip at 0x228, revision 4
[   63.779719] it87: in3 is VCC (+5V)
[   63.779959] hwmon-vid: Unknown VRM version of your x86 CPU
[   63.809579] Adding 12161016k swap on /dev/mapper/superbeast-swap_1.  Priority:-1 extents:1 across:12161016k
[   64.455922] EXT3 FS on dm-0, internal journal
[   65.158317] kjournald starting.  Commit interval 5 seconds
[   65.158550] EXT3 FS on sdb1, internal journal
[   65.158556] EXT3-fs: mounted filesystem with ordered data mode.
[   65.638642] ip_tables: (C) 2000-2006 Netfilter Core Team
[   65.982640] No dock devices found.
[   66.798851] ppdev: user-space parallel port driver
[   67.515297] audit(1217327673.087:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6350 profile="/usr/sbin/cupsd" namespace="default"
[   71.627613] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   71.627617] vboxdrv: Successfully done.
[   71.627618] vboxdrv: Found 4 processor cores.
[   71.627699] vboxdrv: fAsync=0 u64DiffCores=14851.
[   71.627739] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   71.627742] vboxdrv: Successfully loaded version 1.6.2 (interface 0x00070002).
[   71.920221] NET: Registered protocol family 10
[   71.920399] lo: Disabled Privacy Extensions
[   73.320126] r8169: eth0: link up
[   73.320136] r8169: eth0: link up
[   73.405643] Bluetooth: L2CAP ver 2.9
[   73.405648] Bluetooth: L2CAP socket layer initialized
[   73.426059] Bluetooth: RFCOMM socket layer initialized
[   73.426075] Bluetooth: RFCOMM TTY layer initialized
[   73.426077] Bluetooth: RFCOMM ver 1.8
[   79.155931] NET: Registered protocol family 17
[   94.120913] eth0: no IPv6 routers present
[  362.185954] TCP: Treason uncloaked! Peer 62.131.117.163:24967/44167 shrinks window 3764812307:3764814195. Repaired.
[  364.372394] TCP: Treason uncloaked! Peer 62.131.117.163:24967/44167 shrinks window 3764887955:3764890427. Repaired.
[  420.085395] Status code returned 0xc0000054 NT_STATUS_FILE_LOCK_CONFLICT
[  420.085403]  CIFS VFS: Send error in read = -13
[  420.086764] Status code returned 0xc0000054 NT_STATUS_FILE_LOCK_CONFLICT
[  420.086767]  CIFS VFS: Send error in read = -13
[  669.825691] TCP: Treason uncloaked! Peer 62.131.117.163:24967/44167 shrinks window 3770606993:3770612641. Repaired.
[ 1032.060320] TCP: Treason uncloaked! Peer 62.131.117.163:24967/44167 shrinks window 3776052260:3776054812. Repaired.
[ 1445.425563] TCP: Treason uncloaked! Peer 62.131.117.163:24967/44167 shrinks window 3785475162:3785480514. Repaired.
[ 1552.601138] TCP: Treason uncloaked! Peer 62.131.117.163:24967/44167 shrinks window 3788462422:3788464389. Repaired.
[ 1555.814844] TCP: Treason uncloaked! Peer 62.131.117.163:24967/44167 shrinks window 3788600789:3788608373. Repaired.
[ 1755.800244] TCP: Treason uncloaked! Peer 62.131.117.163:24967/44167 shrinks window 3794124018:3794129666. Repaired.
[ 2010.042958] TCP: Treason uncloaked! Peer 62.131.117.163:24967/44167 shrinks window 3798473499:3798478955. Repaired.
[ 2258.805574] TCP: Treason uncloaked! Peer 62.131.117.163:24967/44167 shrinks window 3802655024:3802658984. Repaired.
[ 2267.799161] TCP: Treason uncloaked! Peer 62.131.117.163:24967/44167 shrinks window 3802856968:3802859720. Repaired.
[ 2281.841147] TCP: Treason uncloaked! Peer 62.131.117.163:24967/44167 shrinks window 3803412018:3803420562. Repaired.
[ 2563.995955] TCP: Treason uncloaked! Peer 62.131.117.163:24967/44167 shrinks window 3811092254:3811095006. Repaired.
[ 2686.756422] TCP: Treason uncloaked! Peer 62.131.117.163:24967/44167 shrinks window 3813646132:3813646392. Repaired.
[ 2699.671218] TCP: Treason uncloaked! Peer 62.131.117.163:24967/44167 shrinks window 3814054579:3814057331. Repaired.
[ 2723.614145] TCP: Treason uncloaked! Peer 62.131.117.163:24967/44167 shrinks window 3814986386:3814992034. Repaired.
[ 2757.653868] TCP: Treason uncloaked! Peer 62.131.117.163:24967/44167 shrinks window 3815912857:3815915609. Repaired.
[ 2908.034646] TCP: Treason uncloaked! Peer 62.131.117.163:24967/44167 shrinks window 3817809516:3817814972. Repaired.
[ 3090.428653] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 79833854:79836606. Repaired.
[ 3091.084129] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 79833854:79836606. Repaired.
[ 3092.395196] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 79833854:79836606. Repaired.
[ 3225.935979] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 80925439:80927350. Repaired.
[ 3357.754535] python[10605]: segfault at 3c rip 7ffc7d956983 rsp 7fff89e9c930 error 4
[ 3572.025221] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 87710395:87712979. Repaired.
[ 3712.887874] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 90099934:90104134. Repaired.
[ 3728.308276] UDP: bad checksum. From 122.19.48.193:18256 to 213.112.41.44:55678 ulen 109
[ 3729.964612] usb 3-2: reset full speed USB device using ohci_hcd and address 2
[ 3806.266200] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 91843954:91846538. Repaired.
[ 4214.218341] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 98936924:98942572. Repaired.
[ 4369.875421] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 102438367:102441119. Repaired.
[ 4446.588663] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 103530760:103533512. Repaired.
[ 4447.292160] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 103530760:103533512. Repaired.
[ 4719.295229] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 108501943:108507591. Repaired.
[ 4826.634697] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 110637921:110640673. Repaired.
[ 5086.192658] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 114838955:114843523. Repaired.
[ 5139.498690] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 115616234:115623126. Repaired.
[ 5379.660399] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 120781712:120783444. Repaired.
[ 5398.206978] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 121395882:121401530. Repaired.
[ 5562.555081] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 124662701:124668029. Repaired.
[ 5690.742362] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 126888530:126891282. Repaired.
[ 5835.535867] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 130206244:130211700. Repaired.

[ 5859.562235] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 130627400:130633048. Repaired.
[ 5897.942487] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 131471187:131476643. Repaired.
[ 6267.383454] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 136492256:136497584. Repaired.
[ 6499.557915] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 142687526:142690278. Repaired.
[ 6502.487825] TCP: Treason uncloaked! Peer 62.131.117.163:24967/60199 shrinks window 142798494:142801078. Repaired.
```

My system is an AMD Phenom on a Gigabyte GA-MA790FX-DS5, four gigs of RAM and a bunch of drives totalling about 1.1 terabyte in an LVM-volume. Everything runs off of the LVM, and before anyone says that's why it's slow, I also had this problem with my previous installation which ran off of "native" drives. This current install is a fresh install.

Also, when I run hdparm -Tt I get very decent results:
```
/dev/sda:
 Timing cached reads:   3902 MB in  2.00 seconds = 1952.61 MB/sec
 Timing buffered disk reads:  184 MB in  3.00 seconds =  61.31 MB/sec
```

This is run off of my SATA/300 drive, but the numbers apply for anyone of the drives in the group. The SATA/150-drive gets maybe five megabytes less in timing buffered reads, and the regular IDE-drives maybe seven megabytes less. All of this leads me to believe there is nothing wrong with the disks and the problem is somewhere else - the process that uses all the CPU is very low-level and doesn't show up in top which leads me to believe it's init consuming all the cpu.

Why???

---

### Post by kurros on 2008-07-31
I've been putting up with the same thing since about halfway into the hardy dev cycle. Theories have included changes in libata, ext3, the io scheduler, or the kernel scheduler in general.

I recently reinstalled using 8.04.1 and fresh ext3 volumes and there was no noticeible difference.

I'm using Intel P35 hardware with Core 2 Duo. -generic i386 kernel.

Some reading material:
[Bug #131094 in linux (Ubuntu): “Heavy Disk I/O harms desktop responsiveness”]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094")

[Bug #119730 in linux-source-2.6.20 (Ubuntu): “Slow SATA performance”:]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119730")

---

### Post by isecore on 2008-08-01
For what it's worth, the same phenomenon also occurs when copying large files to USB-thumbdrives. CPU goes through the roof, apps stall and the copying itself takes forever since the CPU is busy doing whatever the heck it's doing rather than moving 1's and 0's to the device.

---

