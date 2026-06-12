---
title: "dv5-1004nr issues"
date: 2008-08-09
forum: Hardware
---

### Post by bambam123 on 2008-08-09
I have experiencing a multitude of issues with this laptop and would like get some help resolving them!

_**Fan and Thermal Issues**_

I decompiled the DSDT and then recompiled it to see what issues it was having with it.  Here is my output.

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  9413:             Method (_HOT, 0, Serialized)
Warning  1086 -                        ^ Not all control paths return a value (_HOT)

dsdt.dsl  9413:             Method (_HOT, 0, Serialized)
Warning  1079 -                        ^ Reserved method must return a value (_HOT)

dsdt.dsl  9421:             Method (_CRT, 0, Serialized)
Warning  1086 -                        ^ Not all control paths return a value (_CRT)

dsdt.dsl  9421:             Method (_CRT, 0, Serialized)
Warning  1079 -                        ^ Reserved method must return a value (_CRT)

ASL Input:  dsdt.dsl - 9508 lines, 317607 bytes, 4008 keywords
AML Output: dsdt.aml - 38699 bytes 825 named objects 3183 executable opcodes

Compilation complete. 0 Errors, 4 Warnings, 0 Remarks, 14 Optimizations

```

_**Battery Issues**_
My battery shows that I have am only receiving about 73% capacity.  I know that the battery is good (it was tested in Vista before installing Ubuntu.  Not really sure how to troubleshoot this one.  

_**Other Notes**_
I have modified the menu.lst to include the following:
acpi_osi="Linux".

I found a thread that suggested attempting that, I have not seen any difference between the two, however here is the "cat" of dmesg before and after


**_Before_**
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] Command line: root=UUID=e8bc8c58-4515-46ab-9a31-dc3cf31695e2 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000afd70000 (usable)
[    0.000000]  BIOS-e820: 00000000afd70000 - 00000000afdbf000 (reserved)
[    0.000000]  BIOS-e820: 00000000afdbf000 - 00000000afe58000 (usable)
[    0.000000]  BIOS-e820: 00000000afe58000 - 00000000afebf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afebf000 - 00000000afeed000 (usable)
[    0.000000]  BIOS-e820: 00000000afeed000 - 00000000afeff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000afeff000 - 00000000aff00000 (usable)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000e4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 720240) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 720319, 720472) 2 entries of 3200 used
[    0.000000] Entering add_active_range(0, 720575, 720621) 3 entries of 3200 used
[    0.000000] Entering add_active_range(0, 720639, 720640) 4 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1310720) 5 entries of 3200 used
[    0.000000] end_pfn_map = 1310720
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FE020 checksum 0
[    0.000000] ACPI: RSDP 000FE020, 0024 (r2 HP    )
[    0.000000] ACPI: XSDT AFEFE120, 005C (r1 HPQOEM SLIC-MPC        3       1000013)
[    0.000000] ACPI: FACP AFEFD000, 00F4 (r4 HP     30F2            3 MSFT  1000013)
[    0.000000] ACPI: DSDT AFEF0000, 972F (r1 HP     30F2     F0000000 MSFT  1000013)
[    0.000000] ACPI: FACS AFE61000, 0040
[    0.000000] ACPI: HPET AFEFC000, 0038 (r1 HP     30F2            1 MSFT  1000013)
[    0.000000] ACPI: APIC AFEFB000, 0084 (r2 HP     30F2            1 MSFT  1000013)
[    0.000000] ACPI: MCFG AFEFA000, 003C (r1 HP     30F2            1 MSFT  1000013)
[    0.000000] ACPI: BOOT AFEEF000, 0028 (r1 HP     30F2            1 MSFT  1000013)
[    0.000000] ACPI: SLIC AFEEE000, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: SSDT AFEED000, 0386 (r1 AMD    PowerNow        1 AMD         1)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 720240) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 720319, 720472) 2 entries of 3200 used
[    0.000000] Entering add_active_range(0, 720575, 720621) 3 entries of 3200 used
[    0.000000] Entering add_active_range(0, 720639, 720640) 4 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1310720) 5 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000] No mptable found.
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1310720
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   720240
[    0.000000]     0:   720319 ->   720472
[    0.000000]     0:   720575 ->   720621
[    0.000000]     0:   720639 ->   720640
[    0.000000]     0:  1048576 ->  1310720
[    0.000000] On node 0 totalpages: 982487
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1220 pages reserved
[    0.000000]   DMA zone: 2723 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 702064 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000afd70000 - 00000000afdbf000
[    0.000000] swsusp: Registered nosave memory region: 00000000afe58000 - 00000000afebf000
[    0.000000] swsusp: Registered nosave memory region: 00000000afeed000 - 00000000afeff000
[    0.000000] swsusp: Registered nosave memory region: 00000000aff00000 - 00000000e0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000e0000000 - 00000000e4000000
[    0.000000] swsusp: Registered nosave memory region: 00000000e4000000 - 00000000fec00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 00000000fec01000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec01000 - 00000000fee00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee00000 - 00000000fee01000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee01000 - 00000000fff00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at b0000000 (gap: aff00000:30100000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 963347
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=e8bc8c58-4515-46ab-9a31-dc3cf31695e2 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   17.732490] Marking TSC unstable due to TSCs unsynchronized
[   17.732494] time.c: Detected 2100.072 MHz processor.
[   17.733443] Console: colour VGA+ 80x25
[   17.733448] console [tty0] enabled
[   17.733487] Checking aperture...
[   17.733535] Calgary: detecting Calgary via BIOS EBDA area
[   17.733541] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   17.733545] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[   17.788954] Placing software IO TLB between 0x104d000 - 0x504d000
[   17.850639] Memory: 3779548k/5242880k available (2489k kernel code, 150400k reserved, 1318k data, 320k init)
[   17.850698] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   17.929622] Calibrating delay using timer specific routine.. 4193.68 BogoMIPS (lpj=8387364)
[   17.929679] Security Framework initialized
[   17.929688] SELinux:  Disabled at boot.
[   17.929710] AppArmor: AppArmor initialized
[   17.929716] Failure registering capabilities with primary security module.
[   17.930352] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   17.934409] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   17.936276] Mount-cache hash table entries: 256
[   17.936488] Initializing cgroup subsys ns
[   17.936494] Initializing cgroup subsys cpuacct
[   17.936516] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.936520] CPU: L2 Cache: 1024K (64 bytes/line)
[   17.936525] CPU 0/0 -> Node 0
[   17.936528] CPU: Physical Processor ID: 0
[   17.936531] CPU: Processor Core ID: 0
[   17.936573] SMP alternatives: switching to UP code
[   17.937885] Early unpacking initramfs... done
[   18.523848] ACPI: Core revision 20070126
[   18.524008] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   18.585495] Using local APIC timer interrupts.
[   18.633066] APIC timer calibration result 12500417
[   18.633069] Detected 12.500 MHz APIC timer.
[   18.633249] SMP alternatives: switching to SMP code
[   18.634428] Booting processor 1/2 APIC 0x1
[   18.547944] Initializing CPU#1
[   18.628336] Calibrating delay using timer specific routine.. 4200.36 BogoMIPS (lpj=8400732)
[   18.628343] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   18.628345] CPU: L2 Cache: 1024K (64 bytes/line)
[   18.628348] CPU 1/1 -> Node 0
[   18.628350] CPU: Physical Processor ID: 0
[   18.628351] CPU: Processor Core ID: 1
[   18.628517] AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80 stepping 01
[   18.725216] Brought up 2 CPUs
[   18.725359] CPU0 attaching sched-domain:
[   18.725363]  domain 0: span 03
[   18.725367]   groups: 01 02
[   18.725372]   domain 1: span 03
[   18.725375]    groups: 03
[   18.725378] CPU1 attaching sched-domain:
[   18.725381]  domain 0: span 03
[   18.725384]   groups: 02 01
[   18.725388]   domain 1: span 03
[   18.725390]    groups: 03
[   18.725773] net_namespace: 120 bytes
[   18.726457] Time: 14:08:55  Date: 08/09/08
[   18.726509] NET: Registered protocol family 16
[   18.726836] ACPI: bus type pci registered
[   18.726961] PCI: Using configuration type 1
[   18.730222] ACPI: EC: Look up EC in DSDT
[   18.736286] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   18.744971] ACPI: Interpreter enabled
[   18.744976] ACPI: (supports S0 S3 S4 S5)
[   18.745015] ACPI: Using IOAPIC for interrupt routing
[   18.658194] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   18.661049] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[   18.661052] ACPI: EC: driver started in interrupt mode
[   18.661121] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.663021] PCI: Transparent bridge - 0000:00:14.4
[   18.663057] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.663348] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   18.663464] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[   18.663602] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[   18.663735] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   18.663901] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   18.677957] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   18.678149] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   18.678310] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   18.678510] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   18.678638] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   18.678799] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   18.678999] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   18.679145] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   18.679309] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.679430] pnp: PnP ACPI init
[   18.679436] ACPI: bus type pnp registered
[   18.683189] pnp: PnP ACPI: found 13 devices
[   18.683191] ACPI: ACPI bus type pnp unregistered
[   18.683723] PCI: Using ACPI for IRQ routing
[   18.683726] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.696462] NET: Registered protocol family 8
[   18.696464] NET: Registered protocol family 20
[   18.696569] PCI-GART: No AMD northbridge found.
[   18.696577] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   18.696581] hpet0: 4 32-bit timers, 14318180 Hz
[   18.697637] AppArmor: AppArmor Filesystem Enabled
[   18.796915] Time: hpet clocksource has been installed.
[   18.796933] Switched to high resolution mode on CPU 0
[   18.700459] Switched to high resolution mode on CPU 1
[   18.708817] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   18.708820] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   18.708827] system 00:09: ioport range 0x400-0x4cf has been reserved
[   18.708829] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   18.708831] system 00:09: ioport range 0x4d6-0x4d6 has been reserved
[   18.708833] system 00:09: ioport range 0x680-0x6ff has been reserved
[   18.708836] system 00:09: ioport range 0x77a-0x77a has been reserved
[   18.708838] system 00:09: ioport range 0xc00-0xc01 has been reserved
[   18.708840] system 00:09: ioport range 0xc14-0xc14 has been reserved
[   18.708842] system 00:09: ioport range 0xc50-0xc52 has been reserved
[   18.708844] system 00:09: ioport range 0xc6c-0xc6c has been reserved
[   18.708846] system 00:09: ioport range 0xc6f-0xc6f has been reserved
[   18.708849] system 00:09: ioport range 0xcd0-0xcdb has been reserved
[   18.708853] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
[   18.708856] system 00:0a: iomem range 0xfff00000-0xffffffff could not be reserved
[   18.709720] PCI: Bridge: 0000:00:01.0
[   18.709723]   IO window: 5000-5fff
[   18.709726]   MEM window: d2200000-d23fffff
[   18.709729]   PREFETCH window: c0000000-cfffffff
[   18.709732] PCI: Bridge: 0000:00:04.0
[   18.709734]   IO window: 3000-4fff
[   18.709737]   MEM window: d1200000-d21fffff
[   18.709740]   PREFETCH window: d0000000-d0ffffff
[   18.709743] PCI: Bridge: 0000:00:05.0
[   18.709744]   IO window: disabled.
[   18.709747]   MEM window: d1100000-d11fffff
[   18.709749]   PREFETCH window: disabled.
[   18.709753] PCI: Bridge: 0000:00:06.0
[   18.709755]   IO window: 2000-2fff
[   18.709758]   MEM window: b0000000-b00fffff
[   18.709760]   PREFETCH window: d1000000-d10fffff
[   18.709764] PCI: Bridge: 0000:00:14.4
[   18.709785]   IO window: 1000-1fff
[   18.709790]   MEM window: disabled.
[   18.709794]   PREFETCH window: disabled.
[   18.709808] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   18.709819] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   18.709823] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   18.709831] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   18.709835] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   18.709842] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[   18.709846] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   18.709860] NET: Registered protocol family 2
[   18.752724] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   18.754061] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   18.758430] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   18.758963] TCP: Hash tables configured (established 524288 bind 65536)
[   18.758965] TCP reno registered
[   18.768683] checking if image is initramfs... it is
[   19.344062] Freeing initrd memory: 7533k freed
[   19.348040] Simple Boot Flag at 0x44 set to 0x1
[   19.349954] audit: initializing netlink socket (disabled)
[   19.349965] audit(1218290935.668:1): initialized
[   19.353631] VFS: Disk quotas dquot_6.5.1
[   19.353784] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   19.354014] io scheduler noop registered
[   19.354017] io scheduler anticipatory registered
[   19.354018] io scheduler deadline registered
[   19.354211] io scheduler cfq registered (default)
[   19.505741] Boot video device is 0000:01:05.0
[   19.506103] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   19.506132] assign_interrupt_mode Found MSI capability
[   19.506163] Allocate Port Service[0000:00:04.0:pcie00]
[   19.506293] Allocate Port Service[0000:00:04.0:pcie02]
[   19.506378] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   19.506406] assign_interrupt_mode Found MSI capability
[   19.506432] Allocate Port Service[0000:00:05.0:pcie00]
[   19.506551] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   19.506578] assign_interrupt_mode Found MSI capability
[   19.506604] Allocate Port Service[0000:00:06.0:pcie00]
[   19.564499] Real Time Clock Driver v1.12ac
[   19.564766] hpet_resources: 0xfed00000 is busy
[   19.564834] Linux agpgart interface v0.102
[   19.564836] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.566935] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.567015] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   19.567221] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   19.593602] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.593608] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.613417] mice: PS/2 mouse device common for all mice
[   19.613481] cpuidle: using governor ladder
[   19.613483] cpuidle: using governor menu
[   19.613667] NET: Registered protocol family 1
[   19.613942] registered taskstats version 1
[   19.614108]   Magic number: 4:237:131
[   19.614220]   hash matches device device:06
[   19.614225] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   19.614228] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   19.614230] EDD information not available.
[   19.614242] Freeing unused kernel memory: 320k freed
[   19.633235] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   20.982968] fuse init (API version 7.9)
[   21.005603] ACPI: Processor [CPU0] (supports 8 throttling states)
[   20.911008] ACPI Exception (thermal-0339): AE_BAD_DATA, No critical threshold [20070126]
[   21.092475] SCSI subsystem initialized
[   21.106989] libata version 3.00 loaded.
[   21.205544] ahci 0000:00:11.0: version 3.0
[   21.205623] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 22 (level, low) -> IRQ 22
[   21.206085] ahci 0000:00:11.0: controller can't do PMP, turning off CAP_PMP
[   21.432220] usbcore: registered new interface driver usbfs
[   21.432261] usbcore: registered new interface driver hub
[   21.432338] usbcore: registered new device driver usb
[   21.457965] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   21.451022] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   21.451029] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   22.203934] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[   22.203943] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck led clo pio 
[   22.204978] scsi0 : ahci
[   22.205110] scsi1 : ahci
[   22.205207] scsi2 : ahci
[   22.205271] scsi3 : ahci
[   22.205371] scsi4 : ahci
[   22.205467] scsi5 : ahci
[   22.205523] ata1: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408100 irq 22
[   22.205528] ata2: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408180 irq 22
[   22.205534] ata3: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408200 irq 22
[   22.205539] ata4: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408280 irq 22
[   22.205544] ata5: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408300 irq 22
[   22.205550] ata6: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408380 irq 22
[   22.678082] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   22.581910] ata1.00: ATA-8: WDC WD2500BEVS-60UST0, 01.01A01, max UDMA/100
[   22.581915] ata1.00: 488397168 sectors, multi 16: LBA48 
[   22.582483] ata1.00: configured for UDMA/100
[   23.152251] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   23.215546] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T30L, GC04, max UDMA/100
[   23.374936] ata2.00: configured for UDMA/100
[   23.781810] ata3: SATA link down (SStatus 0 SControl 300)
[   24.092616] ata4: SATA link down (SStatus 0 SControl 300)
[   24.403420] ata5: SATA link down (SStatus 0 SControl 300)
[   24.714227] ata6: SATA link down (SStatus 0 SControl 300)
[   24.714413] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-6 01.0 PQ: 0 ANSI: 5
[   24.717979] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T30L  GC04 PQ: 0 ANSI: 5
[   24.621524] ACPI: PCI Interrupt 0000:00:12.2[B] -> GSI 17 (level, low) -> IRQ 17
[   24.621969] PCI: Setting latency timer of device 0000:00:12.2 to 64
[   24.621977] ehci_hcd 0000:00:12.2: EHCI Host Controller
[   24.622310] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[   24.622398] ehci_hcd 0000:00:12.2: debug port 1
[   24.622414] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd2408500
[   24.634025] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.634173] usb usb1: configuration #1 chosen from 1 choice
[   24.634196] hub 1-0:1.0: USB hub found
[   24.634205] hub 1-0:1.0: 6 ports detected
[   24.739620] Driver 'sd' needs updating - please use bus_type methods
[   24.741246] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   24.741268] sd 0:0:0:0: [sda] Write Protect is off
[   24.741274] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.741301] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.741382] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   24.741398] sd 0:0:0:0: [sda] Write Protect is off
[   24.741403] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.741428] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.741435]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   24.696658]  sda1 sda2 < sda5 >
[   24.725347] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.830575] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.830613] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   24.737792] ACPI: PCI Interrupt 0000:00:13.2[B] -> GSI 19 (level, low) -> IRQ 19
[   24.738233] PCI: Setting latency timer of device 0000:00:13.2 to 64
[   24.738242] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   24.738309] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[   24.738400] ehci_hcd 0000:00:13.2: debug port 1
[   24.738418] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd2408400
[   24.747623] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   24.747628] Uniform CD-ROM driver Revision: 3.20
[   24.747672] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   24.750756] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.750861] usb usb2: configuration #1 chosen from 1 choice
[   24.750885] hub 2-0:1.0: USB hub found
[   24.750894] hub 2-0:1.0: 6 ports detected
[   24.949731] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
[   24.950188] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   24.950200] ohci_hcd 0000:00:12.0: OHCI Host Controller
[   24.950294] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[   24.950368] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd2407000
[   25.013285] usb usb3: configuration #1 chosen from 1 choice
[   25.013331] hub 3-0:1.0: USB hub found
[   25.013382] hub 3-0:1.0: 3 ports detected
[   25.076870] usb 1-3: new high speed USB device using ehci_hcd and address 2
[   25.116803] ACPI: PCI Interrupt 0000:00:12.1[A] -> GSI 16 (level, low) -> IRQ 16
[   25.117274] PCI: Setting latency timer of device 0000:00:12.1 to 64
[   25.117286] ohci_hcd 0000:00:12.1: OHCI Host Controller
[   25.117398] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[   25.117431] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd2406000
[   25.134416] Attempting manual resume
[   25.134421] swsusp: Resume From Partition 8:5
[   25.134424] PM: Checking swsusp image.
[   25.134715] PM: Resume from disk failed.
[   25.180650] usb usb4: configuration #1 chosen from 1 choice
[   25.180693] hub 4-0:1.0: USB hub found
[   25.180745] hub 4-0:1.0: 3 ports detected
[   25.193169] kjournald starting.  Commit interval 5 seconds
[   25.096572] EXT3-fs: mounted filesystem with ordered data mode.
[   25.131402] usb 1-3: configuration #1 chosen from 1 choice
[   25.284210] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 18
[   25.284803] PCI: Setting latency timer of device 0000:00:13.0 to 64
[   25.284816] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   25.284908] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[   25.284976] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd2405000
[   25.344095] usb usb5: configuration #1 chosen from 1 choice
[   25.344136] hub 5-0:1.0: USB hub found
[   25.344187] hub 5-0:1.0: 3 ports detected
[   25.447573] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 18 (level, low) -> IRQ 18
[   25.448078] PCI: Setting latency timer of device 0000:00:13.1 to 64
[   25.448090] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   25.448184] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[   25.448246] ohci_hcd 0000:00:13.1: irq 18, io mem 0xd2404000
[   25.371206] usb 1-4: new high speed USB device using ehci_hcd and address 3
[   25.507370] usb usb6: configuration #1 chosen from 1 choice
[   25.507411] hub 6-0:1.0: USB hub found
[   25.507459] hub 6-0:1.0: 3 ports detected
[   25.615072] r8169 Gigabit Ethernet driver 2.2LK loaded
[   25.615112] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   25.615143] PCI: Setting latency timer of device 0000:09:00.0 to 64
[   25.615155] r8169 0000:09:00.0: unknown MAC (37a00000)
[   25.615554] eth0: RTL8169 at 0xffffc20001050000, 00:1e:68:87:0d:a5, XID 34a00000 IRQ 508
[   25.617232] ATIIXP: IDE controller (0x1002:0x439c rev 0x00) at  PCI slot 0000:00:14.1
[   25.617248] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   25.617261] ATIIXP: not 100% native mode: will probe irqs later
[   25.617273]     ide0: BM-DMA at 0x6000-0x6007, BIOS settings: hda:DMA, hdb:DMA
[   25.617293]     ide1: BM-DMA at 0x6008-0x600f, BIOS settings: hdc:pio, hdd:pio
[   25.617310] Probing IDE interface ide0...
[   25.755089] usb 1-4: configuration #1 chosen from 1 choice
[   26.176619] Probing IDE interface ide1...
[   33.259574] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   33.292100] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.301736] shpchp: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[   33.301744] shpchp: shpc_init: cannot reserve MMIO region
[   33.301784] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.377146] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   33.723296] ACPI: Battery Slot [BAT0] (battery present)
[   33.890748] input: Power Button (FF) as /devices/virtual/input/input3
[   33.934994] ACPI: Power Button (FF) [PWRF]
[   33.935155] input: Power Button (CM) as /devices/virtual/input/input4
[   33.998638] ACPI: Power Button (CM) [PWRB]
[   33.998734] input: Sleep Button (CM) as /devices/virtual/input/input5
[   34.062409] ACPI: Sleep Button (CM) [SLPB]
[   34.062561] input: Lid Switch as /devices/virtual/input/input6
[   34.094731] ACPI: Lid Switch [LID]
[   34.096071] ACPI: AC Adapter [ACAD] (on-line)
[   34.096947] ACPI: WMI-Acer: Mapper loaded
[   34.422490] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7
[   34.468320] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   34.471385] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/LNXVIDEO:01/input/input8
[   34.508143] ACPI: Video Device [DVGA] (multi-head: yes  rom: no  post: no)
[   34.781383] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   34.781836] PCI: Setting latency timer of device 0000:00:14.2 to 64
[   34.691795] ath_hal: module license 'Proprietary' taints kernel.
[   34.710906] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   34.904079] ACPI: PCI Interrupt 0000:01:05.1[B] -> GSI 19 (level, low) -> IRQ 19
[   34.904519] PCI: Setting latency timer of device 0000:01:05.1 to 64
[   34.916750] wlan: 0.9.4
[   34.966948] ath_pci: 0.9.4
[   34.967029] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   34.967046] PCI: Setting latency timer of device 0000:08:00.0 to 64
[   34.991440] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   34.991977] ACPI: PCI interrupt for device 0000:08:00.0 disabled
[   35.177122] Linux video capture interface: v2.00
[   35.205052] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04751/0xa00000
[   35.221429] uvcvideo: Found UVC 1.00 device HP Webcam (0408:03ba)
[   35.225026] usbcore: registered new interface driver uvcvideo
[   35.225031] USB Video Class driver (v0.1.0)
[   35.375202] usbcore: registered new interface driver libusual
[   35.285171] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   35.292712] Initializing USB Mass Storage driver...
[   35.292805] scsi6 : SCSI emulation for USB Mass Storage devices
[   35.292875] usbcore: registered new interface driver usb-storage
[   35.292878] USB Mass Storage support registered.
[   35.293012] usb-storage: device found at 3
[   35.293014] usb-storage: waiting for device to settle before scanning
[   36.930865] loop: module loaded
[   36.988181] lp: driver loaded but no devices found
[   37.171771] Adding 9936160k swap on /dev/sda5.  Priority:-1 extents:1 across:9936160k
[   37.737226] EXT3 FS on sda1, internal journal
[   38.972086] ip_tables: (C) 2000-2006 Netfilter Core Team
[   39.626272] No dock devices found.
[   40.270332] usb-storage: device scan complete
[   40.272190] scsi 6:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   40.280214] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   40.280256] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   41.015120] ppdev: user-space parallel port driver
[   41.264231] audit(1218290958.618:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5366 profile="/usr/sbin/cupsd" namespace="default"
[   43.095455] r8169: eth0: link up
[   42.998836] r8169: eth0: link up
[   43.079767] Bluetooth: Core ver 2.11
[   43.080159] NET: Registered protocol family 31
[   43.080164] Bluetooth: HCI device and connection manager initialized
[   43.080168] Bluetooth: HCI socket layer initialized
[   43.200942] Bluetooth: L2CAP ver 2.9
[   43.200950] Bluetooth: L2CAP socket layer initialized
[   43.172561] Bluetooth: RFCOMM socket layer initialized
[   43.172580] Bluetooth: RFCOMM TTY layer initialized
[   43.172583] Bluetooth: RFCOMM ver 1.8
[   46.205309] NET: Registered protocol family 17
[   50.357775] NET: Registered protocol family 10
[   50.358431] lo: Disabled Privacy Extensions
[   51.403992] hda-intel: Invalid position buffer, using LPIB read method instead.
[   60.552662] eth0: no IPv6 routers present
[   65.154094] CPU0 attaching NULL sched-domain.
[   65.154102] CPU1 attaching NULL sched-domain.
[   65.182385] CPU0 attaching sched-domain:
[   65.182389]  domain 0: span 03
[   65.182391]   groups: 01 02
[   65.182394]   domain 1: span 03
[   65.182396]    groups: 03
[   65.182398] CPU1 attaching sched-domain:
[   65.182400]  domain 0: span 03
[   65.182402]   groups: 02 01
[   65.182404]   domain 1: span 03
[   65.182406]    groups: 03
```


_**After**_
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] Command line: root=UUID=e8bc8c58-4515-46ab-9a31-dc3cf31695e2 ro quiet splash acpi_osi="Linux"
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000afd70000 (usable)
[    0.000000]  BIOS-e820: 00000000afd70000 - 00000000afdbf000 (reserved)
[    0.000000]  BIOS-e820: 00000000afdbf000 - 00000000afe58000 (usable)
[    0.000000]  BIOS-e820: 00000000afe58000 - 00000000afebf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afebf000 - 00000000afeed000 (usable)
[    0.000000]  BIOS-e820: 00000000afeed000 - 00000000afeff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000afeff000 - 00000000aff00000 (usable)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000e4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 720240) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 720319, 720472) 2 entries of 3200 used
[    0.000000] Entering add_active_range(0, 720575, 720621) 3 entries of 3200 used
[    0.000000] Entering add_active_range(0, 720639, 720640) 4 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1310720) 5 entries of 3200 used
[    0.000000] end_pfn_map = 1310720
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FE020 checksum 0
[    0.000000] ACPI: RSDP 000FE020, 0024 (r2 HP    )
[    0.000000] ACPI: XSDT AFEFE120, 005C (r1 HPQOEM SLIC-MPC        3       1000013)
[    0.000000] ACPI: FACP AFEFD000, 00F4 (r4 HP     30F2            3 MSFT  1000013)
[    0.000000] ACPI: DSDT AFEF0000, 972F (r1 HP     30F2     F0000000 MSFT  1000013)
[    0.000000] ACPI: FACS AFE61000, 0040
[    0.000000] ACPI: HPET AFEFC000, 0038 (r1 HP     30F2            1 MSFT  1000013)
[    0.000000] ACPI: APIC AFEFB000, 0084 (r2 HP     30F2            1 MSFT  1000013)
[    0.000000] ACPI: MCFG AFEFA000, 003C (r1 HP     30F2            1 MSFT  1000013)
[    0.000000] ACPI: BOOT AFEEF000, 0028 (r1 HP     30F2            1 MSFT  1000013)
[    0.000000] ACPI: SLIC AFEEE000, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: SSDT AFEED000, 0386 (r1 AMD    PowerNow        1 AMD         1)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 720240) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 720319, 720472) 2 entries of 3200 used
[    0.000000] Entering add_active_range(0, 720575, 720621) 3 entries of 3200 used
[    0.000000] Entering add_active_range(0, 720639, 720640) 4 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1310720) 5 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000] No mptable found.
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1310720
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   720240
[    0.000000]     0:   720319 ->   720472
[    0.000000]     0:   720575 ->   720621
[    0.000000]     0:   720639 ->   720640
[    0.000000]     0:  1048576 ->  1310720
[    0.000000] On node 0 totalpages: 982487
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1220 pages reserved
[    0.000000]   DMA zone: 2723 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 702064 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000afd70000 - 00000000afdbf000
[    0.000000] swsusp: Registered nosave memory region: 00000000afe58000 - 00000000afebf000
[    0.000000] swsusp: Registered nosave memory region: 00000000afeed000 - 00000000afeff000
[    0.000000] swsusp: Registered nosave memory region: 00000000aff00000 - 00000000e0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000e0000000 - 00000000e4000000
[    0.000000] swsusp: Registered nosave memory region: 00000000e4000000 - 00000000fec00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 00000000fec01000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec01000 - 00000000fee00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee00000 - 00000000fee01000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee01000 - 00000000fff00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at b0000000 (gap: aff00000:30100000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 963347
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=e8bc8c58-4515-46ab-9a31-dc3cf31695e2 ro quiet splash acpi_osi="Linux"
[    0.000000] ACPI: Added _OSI(Linux)
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   17.424644] Marking TSC unstable due to TSCs unsynchronized
[   17.424649] time.c: Detected 2100.063 MHz processor.
[   17.425562] Console: colour VGA+ 80x25
[   17.425567] console [tty0] enabled
[   17.425607] Checking aperture...
[   17.425621] Calgary: detecting Calgary via BIOS EBDA area
[   17.425626] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   17.425630] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[   17.481020] Placing software IO TLB between 0x104d000 - 0x504d000
[   17.543277] Memory: 3779548k/5242880k available (2489k kernel code, 150400k reserved, 1318k data, 320k init)
[   17.543337] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   17.621743] Calibrating delay using timer specific routine.. 4193.71 BogoMIPS (lpj=8387436)
[   17.621800] Security Framework initialized
[   17.621809] SELinux:  Disabled at boot.
[   17.621831] AppArmor: AppArmor initialized
[   17.621838] Failure registering capabilities with primary security module.
[   17.622474] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   17.626527] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   17.628391] Mount-cache hash table entries: 256
[   17.628603] Initializing cgroup subsys ns
[   17.628609] Initializing cgroup subsys cpuacct
[   17.628631] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.628635] CPU: L2 Cache: 1024K (64 bytes/line)
[   17.628640] CPU 0/0 -> Node 0
[   17.628644] CPU: Physical Processor ID: 0
[   17.628646] CPU: Processor Core ID: 0
[   17.628688] SMP alternatives: switching to UP code
[   17.630010] Early unpacking initramfs... done
[   18.215944] ACPI: Core revision 20070126
[   18.216103] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   18.277002] Using local APIC timer interrupts.
[   18.324573] APIC timer calibration result 12500358
[   18.324576] Detected 12.500 MHz APIC timer.
[   18.324757] SMP alternatives: switching to SMP code
[   18.325931] Booting processor 1/2 APIC 0x1
[   18.239416] Initializing CPU#1
[   18.319812] Calibrating delay using timer specific routine.. 4200.35 BogoMIPS (lpj=8400715)
[   18.319819] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   18.319821] CPU: L2 Cache: 1024K (64 bytes/line)
[   18.319824] CPU 1/1 -> Node 0
[   18.319826] CPU: Physical Processor ID: 0
[   18.319827] CPU: Processor Core ID: 1
[   18.319993] AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80 stepping 01
[   18.416720] Brought up 2 CPUs
[   18.416832] CPU0 attaching sched-domain:
[   18.416836]  domain 0: span 03
[   18.416839]   groups: 01 02
[   18.416844]   domain 1: span 03
[   18.416847]    groups: 03
[   18.416851] CPU1 attaching sched-domain:
[   18.416853]  domain 0: span 03
[   18.416856]   groups: 02 01
[   18.416860]   domain 1: span 03
[   18.416863]    groups: 03
[   18.417247] net_namespace: 120 bytes
[   18.417930] Time: 14:14:41  Date: 08/09/08
[   18.417982] NET: Registered protocol family 16
[   18.418308] ACPI: bus type pci registered
[   18.418467] PCI: Using configuration type 1
[   18.421700] ACPI: EC: Look up EC in DSDT
[   18.427772] ACPI: BIOS _OSI(Linux) query honored via cmdline
[   18.436761] ACPI: Interpreter enabled
[   18.436766] ACPI: (supports S0 S3 S4 S5)
[   18.436805] ACPI: Using IOAPIC for interrupt routing
[   18.350141] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   18.351948] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[   18.351950] ACPI: EC: driver started in interrupt mode
[   18.352017] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.353939] PCI: Transparent bridge - 0000:00:14.4
[   18.353974] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.354274] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   18.354392] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[   18.354531] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[   18.354664] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   18.354830] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   18.368788] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   18.368992] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   18.369153] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   18.369354] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   18.369499] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   18.369660] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   18.369826] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   18.370025] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   18.370182] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.370308] pnp: PnP ACPI init
[   18.370314] ACPI: bus type pnp registered
[   18.374021] pnp: PnP ACPI: found 13 devices
[   18.374023] ACPI: ACPI bus type pnp unregistered
[   18.374556] PCI: Using ACPI for IRQ routing
[   18.374558] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.387938] NET: Registered protocol family 8
[   18.387940] NET: Registered protocol family 20
[   18.388045] PCI-GART: No AMD northbridge found.
[   18.388076] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   18.388080] hpet0: 4 32-bit timers, 14318180 Hz
[   18.389135] AppArmor: AppArmor Filesystem Enabled
[   18.488390] Time: hpet clocksource has been installed.
[   18.488408] Switched to high resolution mode on CPU 0
[   18.391935] Switched to high resolution mode on CPU 1
[   18.400261] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   18.400263] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   18.400270] system 00:09: ioport range 0x400-0x4cf has been reserved
[   18.400272] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   18.400275] system 00:09: ioport range 0x4d6-0x4d6 has been reserved
[   18.400277] system 00:09: ioport range 0x680-0x6ff has been reserved
[   18.400279] system 00:09: ioport range 0x77a-0x77a has been reserved
[   18.400281] system 00:09: ioport range 0xc00-0xc01 has been reserved
[   18.400283] system 00:09: ioport range 0xc14-0xc14 has been reserved
[   18.400285] system 00:09: ioport range 0xc50-0xc52 has been reserved
[   18.400288] system 00:09: ioport range 0xc6c-0xc6c has been reserved
[   18.400290] system 00:09: ioport range 0xc6f-0xc6f has been reserved
[   18.400292] system 00:09: ioport range 0xcd0-0xcdb has been reserved
[   18.400297] system 00:0a: iomem range 0xe0000-0xfffff could not be reserved
[   18.400300] system 00:0a: iomem range 0xfff00000-0xffffffff could not be reserved
[   18.401259] PCI: Bridge: 0000:00:01.0
[   18.401261]   IO window: 5000-5fff
[   18.401265]   MEM window: d2200000-d23fffff
[   18.401268]   PREFETCH window: c0000000-cfffffff
[   18.401271] PCI: Bridge: 0000:00:04.0
[   18.401273]   IO window: 3000-4fff
[   18.401276]   MEM window: d1200000-d21fffff
[   18.401278]   PREFETCH window: d0000000-d0ffffff
[   18.401282] PCI: Bridge: 0000:00:05.0
[   18.401283]   IO window: disabled.
[   18.401286]   MEM window: d1100000-d11fffff
[   18.401288]   PREFETCH window: disabled.
[   18.401292] PCI: Bridge: 0000:00:06.0
[   18.401293]   IO window: 2000-2fff
[   18.401296]   MEM window: b0000000-b00fffff
[   18.401299]   PREFETCH window: d1000000-d10fffff
[   18.401302] PCI: Bridge: 0000:00:14.4
[   18.401338]   IO window: 1000-1fff
[   18.401343]   MEM window: disabled.
[   18.401347]   PREFETCH window: disabled.
[   18.401360] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   18.401372] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   18.401376] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   18.401384] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   18.401387] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   18.401395] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[   18.401399] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   18.401413] NET: Registered protocol family 2
[   18.444134] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   18.445470] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   18.449816] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   18.450348] TCP: Hash tables configured (established 524288 bind 65536)
[   18.450351] TCP reno registered
[   18.460091] checking if image is initramfs... it is
[   19.034618] Freeing initrd memory: 7533k freed
[   19.038572] Simple Boot Flag at 0x44 set to 0x1
[   19.040406] audit: initializing netlink socket (disabled)
[   19.040418] audit(1218291281.664:1): initialized
[   19.044115] VFS: Disk quotas dquot_6.5.1
[   19.044266] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   19.044402] io scheduler noop registered
[   19.044404] io scheduler anticipatory registered
[   19.044406] io scheduler deadline registered
[   19.044553] io scheduler cfq registered (default)
[   19.197183] Boot video device is 0000:01:05.0
[   19.197544] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   19.197573] assign_interrupt_mode Found MSI capability
[   19.197604] Allocate Port Service[0000:00:04.0:pcie00]
[   19.197734] Allocate Port Service[0000:00:04.0:pcie02]
[   19.197819] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   19.197847] assign_interrupt_mode Found MSI capability
[   19.197873] Allocate Port Service[0000:00:05.0:pcie00]
[   19.197989] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   19.198016] assign_interrupt_mode Found MSI capability
[   19.198042] Allocate Port Service[0000:00:06.0:pcie00]
[   19.250788] Real Time Clock Driver v1.12ac
[   19.251058] hpet_resources: 0xfed00000 is busy
[   19.251123] Linux agpgart interface v0.102
[   19.251126] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.253202] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.253360] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   19.253490] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   19.280215] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.280221] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.288920] mice: PS/2 mouse device common for all mice
[   19.288975] cpuidle: using governor ladder
[   19.288977] cpuidle: using governor menu
[   19.289163] NET: Registered protocol family 1
[   19.289280] registered taskstats version 1
[   19.289452]   Magic number: 4:340:232
[   19.289474]   hash matches device ttyv2
[   19.289578] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   19.289581] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   19.289583] EDD information not available.
[   19.289596] Freeing unused kernel memory: 320k freed
[   19.316704] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   20.680193] fuse init (API version 7.9)
[   20.703724] ACPI: Processor [CPU0] (supports 8 throttling states)
[   20.706009] ACPI Exception (thermal-0339): AE_BAD_DATA, No critical threshold [20070126]
[   21.039947] r8169 Gigabit Ethernet driver 2.2LK loaded
[   21.039974] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   21.039995] PCI: Setting latency timer of device 0000:09:00.0 to 64
[   21.040006] r8169 0000:09:00.0: unknown MAC (37a00000)
[   21.040240] eth0: RTL8169 at 0xffffc20001042000, 00:1e:68:87:0d:a5, XID 34a00000 IRQ 508
[   21.197505] usbcore: registered new interface driver usbfs
[   21.197544] usbcore: registered new interface driver hub
[   21.200862] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   21.200870] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   21.201832] usbcore: registered new device driver usb
[   21.202027] ATIIXP: IDE controller (0x1002:0x439c rev 0x00) at  PCI slot 0000:00:14.1
[   21.202050] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   21.202067] ATIIXP: not 100% native mode: will probe irqs later
[   21.202079]     ide0: BM-DMA at 0x6000-0x6007, BIOS settings: hda:DMA, hdb:DMA
[   21.202107]     ide1: BM-DMA at 0x6008-0x600f, BIOS settings: hdc:pio, hdd:pio
[   21.202122] Probing IDE interface ide0...
[   21.287897] SCSI subsystem initialized
[   21.207814] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   21.335656] libata version 3.00 loaded.
[   21.759866] Probing IDE interface ide1...
[   22.325838] ahci 0000:00:11.0: version 3.0
[   22.325893] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 22 (level, low) -> IRQ 22
[   22.326396] ahci 0000:00:11.0: controller can't do PMP, turning off CAP_PMP
[   23.325969] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[   23.325977] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck led clo pio 
[   23.327010] scsi0 : ahci
[   23.327136] scsi1 : ahci
[   23.327230] scsi2 : ahci
[   23.327325] scsi3 : ahci
[   23.327420] scsi4 : ahci
[   23.327514] scsi5 : ahci
[   23.327602] ata1: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408100 irq 22
[   23.327608] ata2: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408180 irq 22
[   23.327615] ata3: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408200 irq 22
[   23.327621] ata4: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408280 irq 22
[   23.327628] ata5: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408300 irq 22
[   23.327634] ata6: SATA max UDMA/133 abar m1024@0xd2408000 port 0xd2408380 irq 22
[   23.800087] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   23.703889] ata1.00: ATA-8: WDC WD2500BEVS-60UST0, 01.01A01, max UDMA/100
[   23.703893] ata1.00: 488397168 sectors, multi 16: LBA48 
[   23.704465] ata1.00: configured for UDMA/100
[   24.274260] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   24.337534] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T30L, GC04, max UDMA/100
[   24.496424] ata2.00: configured for UDMA/100
[   24.903815] ata3: SATA link down (SStatus 0 SControl 300)
[   25.214607] ata4: SATA link down (SStatus 0 SControl 300)
[   25.527670] ata5: SATA link down (SStatus 0 SControl 300)
[   25.836233] ata6: SATA link down (SStatus 0 SControl 300)
[   25.836417] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-6 01.0 PQ: 0 ANSI: 5
[   25.839957] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T30L  GC04 PQ: 0 ANSI: 5
[   25.743451] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.743898] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   25.743906] ohci_hcd 0000:00:12.0: OHCI Host Controller
[   25.744247] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[   25.744313] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd2407000
[   25.860250] Driver 'sd' needs updating - please use bus_type methods
[   25.861870] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   25.861893] sd 0:0:0:0: [sda] Write Protect is off
[   25.861897] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.861925] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.861998] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   25.862014] sd 0:0:0:0: [sda] Write Protect is off
[   25.862018] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   25.862042] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   25.862048]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   25.803952] usb usb1: configuration #1 chosen from 1 choice
[   25.803977] hub 1-0:1.0: USB hub found
[   25.804021] hub 1-0:1.0: 3 ports detected
[   25.817357]  sda1 sda2 < sda5 >
[   25.846037] sd 0:0:0:0: [sda] Attached SCSI disk
[   25.850206] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   25.850229] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   25.865203] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   25.865208] Uniform CD-ROM driver Revision: 3.20
[   25.865251] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   25.907537] ACPI: PCI Interrupt 0000:00:12.1[A] -> GSI 16 (level, low) -> IRQ 16
[   25.907988] PCI: Setting latency timer of device 0000:00:12.1 to 64
[   25.907996] ohci_hcd 0000:00:12.1: OHCI Host Controller
[   25.908059] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
[   25.908079] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd2406000
[   25.966823] usb usb2: configuration #1 chosen from 1 choice
[   25.966848] hub 2-0:1.0: USB hub found
[   25.966893] hub 2-0:1.0: 3 ports detected
[   26.066895] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 18
[   26.067340] PCI: Setting latency timer of device 0000:00:13.0 to 64
[   26.067348] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   26.067411] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
[   26.067468] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd2405000
[   26.126701] usb usb3: configuration #1 chosen from 1 choice
[   26.126728] hub 3-0:1.0: USB hub found
[   26.126773] hub 3-0:1.0: 3 ports detected
[   26.225428] Attempting manual resume
[   26.225435] swsusp: Resume From Partition 8:5
[   26.225438] PM: Checking swsusp image.
[   26.225735] PM: Resume from disk failed.
[   26.280684] kjournald starting.  Commit interval 5 seconds
[   26.184035] EXT3-fs: mounted filesystem with ordered data mode.
[   26.314393] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   26.230321] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 18 (level, low) -> IRQ 18
[   26.230774] PCI: Setting latency timer of device 0000:00:13.1 to 64
[   26.230782] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   26.230842] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
[   26.230895] ohci_hcd 0000:00:13.1: irq 18, io mem 0xd2404000
[   26.290122] usb usb4: configuration #1 chosen from 1 choice
[   26.290145] hub 4-0:1.0: USB hub found
[   26.290189] hub 4-0:1.0: 3 ports detected
[   26.393822] ACPI: PCI Interrupt 0000:00:12.2[B] -> GSI 17 (level, low) -> IRQ 17
[   26.394254] PCI: Setting latency timer of device 0000:00:12.2 to 64
[   26.394262] ehci_hcd 0000:00:12.2: EHCI Host Controller
[   26.394323] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 5
[   26.394368] ehci_hcd 0000:00:12.2: debug port 1
[   26.394385] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd2408500
[   26.409472] usb 1-3: device descriptor read/64, error -62
[   26.420926] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   26.421034] usb usb5: configuration #1 chosen from 1 choice
[   26.421055] hub 5-0:1.0: USB hub found
[   26.421063] hub 5-0:1.0: 6 ports detected
[   26.524643] ACPI: PCI Interrupt 0000:00:13.2[B] -> GSI 19 (level, low) -> IRQ 19
[   26.525137] PCI: Setting latency timer of device 0000:00:13.2 to 64
[   26.525145] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   26.525206] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 6
[   26.525285] ehci_hcd 0000:00:13.2: debug port 1
[   26.525302] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd2408400
[   26.584791] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   26.584888] usb usb6: configuration #1 chosen from 1 choice
[   26.584909] hub 6-0:1.0: USB hub found
[   26.584916] hub 6-0:1.0: 6 ports detected
[   27.066954] usb 5-3: new high speed USB device using ehci_hcd and address 2
[   27.217273] usb 5-3: configuration #1 chosen from 1 choice
[   27.456950] usb 5-4: new high speed USB device using ehci_hcd and address 3
[   27.837845] usb 5-4: configuration #1 chosen from 1 choice
[   34.783883] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.835133] shpchp: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[   34.835139] shpchp: shpc_init: cannot reserve MMIO region
[   34.835166] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.966878] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   34.961842] input: Power Button (FF) as /devices/virtual/input/input3
[   34.996757] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   35.020536] ACPI: Power Button (FF) [PWRF]
[   35.020647] input: Power Button (CM) as /devices/virtual/input/input4
[   35.076244] ACPI: Power Button (CM) [PWRB]
[   35.076304] input: Sleep Button (CM) as /devices/virtual/input/input5
[   35.120083] ACPI: Sleep Button (CM) [SLPB]
[   35.120169] input: Lid Switch as /devices/virtual/input/input6
[   35.152379] ACPI: Lid Switch [LID]
[   35.152807] ACPI: AC Adapter [ACAD] (on-line)
[   35.340435] ACPI: WMI-Acer: Mapper loaded
[   35.584477] ACPI: Battery Slot [BAT0] (battery present)
[   35.641516] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   35.641958] PCI: Setting latency timer of device 0000:00:14.2 to 64
[   35.754280] ACPI: PCI Interrupt 0000:01:05.1[B] -> GSI 19 (level, low) -> IRQ 19
[   35.754703] PCI: Setting latency timer of device 0000:01:05.1 to 64
[   35.872266] ath_hal: module license 'Proprietary' taints kernel.
[   35.941588] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   36.012181] wlan: 0.9.4
[   36.107973] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7
[   36.152110] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   36.154081] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/LNXVIDEO:01/input/input8
[   36.154509] ath_pci: 0.9.4
[   36.154562] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   36.154599] PCI: Setting latency timer of device 0000:08:00.0 to 64
[   36.178699] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   36.178715] ACPI: PCI interrupt for device 0000:08:00.0 disabled
[   36.235792] ACPI: Video Device [DVGA] (multi-head: yes  rom: no  post: no)
[   36.398871] usbcore: registered new interface driver libusual
[   36.416927] Initializing USB Mass Storage driver...
[   36.421320] scsi6 : SCSI emulation for USB Mass Storage devices
[   36.423264] usbcore: registered new interface driver usb-storage
[   36.423269] USB Mass Storage support registered.
[   36.423410] usb-storage: device found at 3
[   36.423412] usb-storage: waiting for device to settle before scanning
[   36.585318] Linux video capture interface: v2.00
[   36.626563] uvcvideo: Found UVC 1.00 device HP Webcam (0408:03ba)
[   36.630141] usbcore: registered new interface driver uvcvideo
[   36.630144] USB Video Class driver (v0.1.0)
[   37.127780] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04751/0xa00000
[   37.211327] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   38.483817] loop: module loaded
[   38.530737] lp: driver loaded but no devices found
[   38.669761] Adding 9936160k swap on /dev/sda5.  Priority:-1 extents:1 across:9936160k
[   39.225334] EXT3 FS on sda1, internal journal
[   40.501703] ip_tables: (C) 2000-2006 Netfilter Core Team
[   41.132679] No dock devices found.
[   41.404174] usb-storage: device scan complete
[   41.407041] scsi 6:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   41.409322] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   41.409362] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   42.648537] ppdev: user-space parallel port driver
[   42.861493] audit(1218291306.531:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5146 profile="/usr/sbin/cupsd" namespace="default"
[   44.204334] r8169: eth0: link up
[   44.204344] r8169: eth0: link up
[   44.301994] Bluetooth: Core ver 2.11
[   44.302371] NET: Registered protocol family 31
[   44.302374] Bluetooth: HCI device and connection manager initialized
[   44.302379] Bluetooth: HCI socket layer initialized
[   44.331851] Bluetooth: L2CAP ver 2.9
[   44.331856] Bluetooth: L2CAP socket layer initialized
[   44.396484] Bluetooth: RFCOMM socket layer initialized
[   44.396503] Bluetooth: RFCOMM TTY layer initialized
[   44.396505] Bluetooth: RFCOMM ver 1.8
[   47.447814] NET: Registered protocol family 17
[   49.678307] NET: Registered protocol family 10
[   49.678688] lo: Disabled Privacy Extensions
[   52.702180] hda-intel: Invalid position buffer, using LPIB read method instead.
[   59.777376] eth0: no IPv6 routers present
[   76.401469] CPU0 attaching NULL sched-domain.
[   76.401477] CPU1 attaching NULL sched-domain.
[   76.410639] CPU0 attaching sched-domain:
[   76.410646]  domain 0: span 03
[   76.410648]   groups: 01 02
[   76.410651]   domain 1: span 03
[   76.410653]    groups: 03
[   76.410655] CPU1 attaching sched-domain:
[   76.410656]  domain 0: span 03
[   76.410657]   groups: 02 01
[   76.410660]   domain 1: span 03
[   76.410661]    groups: 03
```


I appreciate any help!



Specs:
AMD Turion X2 Ultra 64-bit processor
4GB Memory
Came pre-installed with Vista

---

### Post by wanderlust on 2008-08-26
> **bambam123 said:**
> 
_**Battery Issues**_
My battery shows that I have am only receiving about 73% capacity.  I know that the battery is good (it was tested in Vista before installing Ubuntu.  Not really sure how to troubleshoot this one.  

This is really bad battery ;) I checked it under the Vista with the HP utility and it really has such bad capacity. In any case, capacity of my battery is near 66%, so you are lucky :)

> 
_**Other Notes**_
I have modified the menu.lst to include the following:
acpi_osi="Linux".

I found a thread that suggested attempting that, I have not seen any difference between the two, however here is the "cat" of dmesg before and after


Can you post link on the thread? I cannot figure out what is it trying to do.

---

