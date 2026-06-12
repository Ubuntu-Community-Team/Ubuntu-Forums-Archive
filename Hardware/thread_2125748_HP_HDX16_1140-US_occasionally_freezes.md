---
title: "HP HDX16 1140-US occasionally freezes"
date: 2013-03-14
forum: Hardware
---

### Post by Dural on 2013-03-14
I have this random problem where I can't use Ubuntu 12.04. Everything locks up, but my screen stays on (the screen doesn't go blank) and it doesn't update. I can't enter any keyboard commands (so no entering the console or Alt-SysRq-REISUB), the mouse cursor won't move, and I have no choice but to turn my computer off and switch it back on. This happens whether I'm using Unity, Unity2D, or Gnome Classic. It happens whether I'm using the NVIDIA driver for my computer or Noveau. This persists even with kernel updates. From what I can tell, it might have something to do with my BIOS but this is the latest version I can use to my knowledge. At this point I'm stumped and I'm not sure what to do.

Hardware Specs: 
Processor:  Intel Core 2 Duo P8600 @ 2.4 GHz
BIOS: F.32 Rev 1
Memory: 2GB out of a total 4GB (one of the modules is damaged, but I ran MemTest86+ multiple times and it said everything was fine with the remaining working stick; it did not detect the damaged stick)
Video Card: NVidia 9600M GT
-Version-
Kernel		: Linux 3.2.0-38-generic (x86_64)
Compiled		: #61-Ubuntu SMP Tue Feb 19 12:18:21 UTC 2013
C Library		: Unknown
Default C Compiler		: GNU C Compiler version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) 
Distribution		: Ubuntu 12.04.2 LTS

Relevant part of dmesg

> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-38-generic (buildd@akateko) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #61-Ubuntu SMP Tue Feb 19 12:18:21 UTC 2013 (Ubuntu 3.2.0-38.61-generic 3.2.37)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-38-generic root=UUID=20d4d398-c254-49b0-b7c6-17f0c12e1a3a ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fca8000 (usable)
[    0.000000]  BIOS-e820: 000000007fca8000 - 000000007fcbf000 (reserved)
[    0.000000]  BIOS-e820: 000000007fcbf000 - 000000007fd81000 (usable)
[    0.000000]  BIOS-e820: 000000007fd81000 - 000000007fdbf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fdbf000 - 000000007fde1000 (usable)
[    0.000000]  BIOS-e820: 000000007fde1000 - 000000007fdf7000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fdf7000 - 000000007fe00000 (usable)
[    0.000000]  BIOS-e820: 000000007fe00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Hewlett-Packard HP HDX 16 Notebook PC/361B, BIOS F.32 10/26/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x7fe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 040000000 mask FC0000000 write-back
[    0.000000]   2 base 0FFF00000 mask FFFF00000 write-protect
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-000000007fe00000
[    0.000000]  0000000000 - 007fe00000 page 2M
[    0.000000] kernel direct mapping tables up to 7fe00000 @ 1fffd000-20000000
[    0.000000] RAMDISK: 364d8000 - 37264000
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 000000007fdf6120 0006C (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 000000007fdf4000 000F4 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 000000007fde4000 0B7CC (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 000000007fd8d000 00040
[    0.000000] ACPI: DMAR 000000007fdf5000 00040 (v01               ? 00000001      00000000)
[    0.000000] ACPI: HPET 000000007fdf3000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 000000007fdf2000 0006C (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 000000007fdf1000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: ASF! 000000007fdf0000 000A5 (v32 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 000000007fde3000 00176 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
[    0.000000] ACPI: BOOT 000000007fde2000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 000000007fde1000 00655 (v01  PmRef    CpuPm 00003000 INTL 20060317)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fe00000
[    0.000000] Initmem setup node 0 0000000000000000-000000007fe00000
[    0.000000]   NODE_DATA [000000007fdfb000 - 000000007fdfffff]
[    0.000000]  [ffffea0000000000-ffffea0001ffffff] PMD -> [ffff88007d400000-ffff88007f3fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x0007fca8
[    0.000000]     0: 0x0007fcbf -> 0x0007fd81
[    0.000000]     0: 0x0007fdbf -> 0x0007fde1
[    0.000000]     0: 0x0007fdf7 -> 0x0007fe00
[    0.000000] On node 0 totalpages: 523555
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 8120 pages used for memmap
[    0.000000]   DMA32 zone: 511453 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000007fca8000 - 000000007fcbf000
[    0.000000] PM: Registered nosave memory: 000000007fd81000 - 000000007fdbf000
[    0.000000] PM: Registered nosave memory: 000000007fde1000 - 000000007fdf7000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:78000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007fa00000 s83136 r8192 d23360 u524288
[    0.000000] pcpu-alloc: s83136 r8192 d23360 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515366
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-38-generic root=UUID=20d4d398-c254-49b0-b7c6-17f0c12e1a3a ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] ------------[ cut here ]------------
[b][    0.000000] WARNING: at /build/buildd/linux-3.2.0/drivers/iommu/dmar.c:492 warn_invalid_dmar+0x8f/0xa0()
[    0.000000] Hardware name: HP HDX 16 Notebook PC
[    0.000000] Your BIOS is broken; DMAR reported at address 0![/b]
[    0.000000] BIOS vendor: Hewlett-Packard; Ver: F.32; Product Version: Rev 1
[    0.000000] Modules linked in:
[    0.000000] Pid: 0, comm: swapper Not tainted 3.2.0-38-generic #61-Ubuntu
[    0.000000] Call Trace:
[    0.000000]  [<ffffffff81067e3f>] warn_slowpath_common+0x7f/0xc0
[    0.000000]  [<ffffffff8166a8cc>] ? bad_to_user+0x7f6/0x7f6
[    0.000000]  [<ffffffff81067edf>] warn_slowpath_fmt_taint+0x3f/0x50
[    0.000000]  [<ffffffff81d093de>] ? __acpi_map_table+0x13/0x19
[    0.000000]  [<ffffffff8138fbe5>] ? acpi_tb_checksum+0x9/0x1e
[    0.000000]  [<ffffffff8151fcff>] warn_invalid_dmar+0x8f/0xa0
[    0.000000]  [<ffffffff81d39dd0>] check_zero_address+0x57/0xf7
[    0.000000]  [<ffffffff8166a8cc>] ? bad_to_user+0x7f6/0x7f6
[    0.000000]  [<ffffffff81d39e87>] detect_intel_iommu+0x17/0xb8
[    0.000000]  [<ffffffff81d04acb>] pci_iommu_alloc+0x44/0x6f
[    0.000000]  [<ffffffff81d11f75>] mem_init+0x19/0xec
[    0.000000]  [<ffffffff81cfca2d>] start_kernel+0x1da/0x3bd
[    0.000000]  [<ffffffff81cfc388>] x86_64_start_reservations+0x132/0x136
[    0.000000]  [<ffffffff81cfc140>] ? early_idt_handlers+0x140/0x140
[    0.000000]  [<ffffffff81cfc459>] x86_64_start_kernel+0xcd/0xdc
[    0.000000] ---[ end trace cd5781ab433d2f2e ]---
[    0.000000] Memory: 2031308k/2095104k available (6570k kernel code, 884k absent, 62912k reserved, 6635k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2394.349 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4788.69 BogoMIPS (lpj=9577396)
[    0.004009] pid_max: default: 32768 minimum: 301

---

### Post by Dural on 2013-03-15
Update:
Something i've noticed is that Ubuntu 12.04 seems to only freeze up completely when i have 10+ tabs open in Firefox. Does anyone else have a similar problem?

---

