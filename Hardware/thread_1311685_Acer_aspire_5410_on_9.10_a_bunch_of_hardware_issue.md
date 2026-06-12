---
title: "Acer aspire 5410 on 9.10 a bunch of hardware issues"
date: 2009-11-02
forum: Hardware
---

### Post by frojnd on 2009-11-02
Hello there.
I don't know where to begin so I'll begin with CDROM. Somehow it doesn't work as it should. First of all it doesn't recognize  any of the CDs I put in. Second of all when I press the button for ejecting it won't eject! There is a sound that it wanna eject but it's caught in a loop. Hpwever when I put cd during the boot bios recognize the bootable cd so does eject it. There is something wrong with cdrom!
I have no idea how can I provide info about cdrom...
lspci -v gives me this: 
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4110 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: fast devsel
	Memory at 94500000 (64-bit, non-prefetchable) [disabled] [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 40e0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 40c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at 94405c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 94400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 93400000-943fffff
	Prefetchable memory behind bridge: 0000000090400000-00000000913fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 92400000-933fffff
	Prefetchable memory behind bridge: 0000000091400000-00000000923fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 40a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 4080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 4060 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 4040 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at 94405800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 26
	I/O ports at 4108 [size=8]
	I/O ports at 411c [size=4]
	I/O ports at 4100 [size=8]
	I/O ports at 4118 [size=4]
	I/O ports at 4020 [size=32]
	Memory at 94405000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: medium devsel, IRQ 11
	Memory at 94406000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 4000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: fast devsel, IRQ 11
	Memory at 94404000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

01:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)
	Subsystem: Acer Incorporated [ALI] Device 022b
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at 93400000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 3000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: atl1c
	Kernel modules: atl1c

02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Device 1a32:0303
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at 92400000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

```

Another problem is built in microphone. I can't hear myself after recording myself. I've tryed to unmute all the channels in alsamixer but nothing helped :S

And hardware incompatibility continuous :)

I can't regulate brightness of display when pressing fn+left/right ???
When I press the button that disables touchpad the only option is for me to reboot in order to get working touchpad again.

Here is the dmesg output:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007b9f0000 (usable)
[    0.000000]  BIOS-e820: 000000007b9f0000 - 000000007ba3f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ba3f000 - 000000007ba57000 (usable)
[    0.000000]  BIOS-e820: 000000007ba57000 - 000000007babf000 (reserved)
[    0.000000]  BIOS-e820: 000000007babf000 - 000000007bade000 (usable)
[    0.000000]  BIOS-e820: 000000007bade000 - 000000007baf7000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007baf7000 - 000000007bb00000 (usable)
[    0.000000]  BIOS-e820: 000000007bb00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.6 present.
[    0.000000] last_pfn = 0x7bb00 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   2 base 040000000 mask FC0000000 write-back
[    0.000000]   3 base 07C000000 mask FFC000000 uncachable
[    0.000000]   4 base 07BC00000 mask FFFC00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009e000 (usable)
[    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007b9f0000 (usable)
[    0.000000]  modified: 000000007b9f0000 - 000000007ba3f000 (ACPI NVS)
[    0.000000]  modified: 000000007ba3f000 - 000000007ba57000 (usable)
[    0.000000]  modified: 000000007ba57000 - 000000007babf000 (reserved)
[    0.000000]  modified: 000000007babf000 - 000000007bade000 (usable)
[    0.000000]  modified: 000000007bade000 - 000000007baf7000 (ACPI data)
[    0.000000]  modified: 000000007baf7000 - 000000007bb00000 (usable)
[    0.000000]  modified: 000000007bb00000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 378a6000 - 37fef91b
[    0.000000] Allocated new RAMDISK: 008ad000 - 00ff691b
[    0.000000] Move RAMDISK from 00000000378a6000 - 0000000037fef91a to 008ad000 - 00ff691a
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 7baf6120 0007C (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP 7baf4000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 000F4240)
[    0.000000] ACPI: DSDT 7bae5000 0A592 (v01 ACER   ACER     00000001 1025 20051117)
[    0.000000] ACPI: FACS 7b9fd000 00040
[    0.000000] ACPI: DMAR 7baf5000 00060 (v01                00000001      00000000)
[    0.000000] ACPI: HPET 7baf3000 00038 (v01 ACER   ACER     00000001 1025 000F4240)
[    0.000000] ACPI: APIC 7baf2000 0006C (v02 ACER   ACER     00000001 1025 000F4240)
[    0.000000] ACPI: MCFG 7baf1000 0003C (v01 ACER   ACER     00000001 1025 000F4240)
[    0.000000] ACPI: ASF! 7baf0000 000A5 (v32 ACER   ACER     00000001 1025 000F4240)
[    0.000000] ACPI: SLIC 7bae4000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 000F4240)
[    0.000000] ACPI: BOOT 7bae3000 00028 (v01 ACER   ACER     00000001 1025 00000001)
[    0.000000] ACPI: SSDT 7bae2000 0031A (v01 ACER   ACER     00001000 1025 20051117)
[    0.000000] ACPI: SSDT 7badf000 00537 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.000000] ACPI: SSDT 7bade000 00655 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1091MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac258]              BRK ==> [00008a9000 - 00008ac258]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 0000ff691b]      NEW RAMDISK ==> [00008ad000 - 0000ff691b]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007bb00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x0007b9f0
[    0.000000]     0: 0x0007ba3f -> 0x0007ba57
[    0.000000]     0: 0x0007babf -> 0x0007bade
[    0.000000]     0: 0x0007baf7 -> 0x0007bb00
[    0.000000] On node 0 totalpages: 506314
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3962 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2183 pages used for memmap
[    0.000000]   HighMem zone: 276907 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:78000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1f82000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 502355
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=a808f8e3-9fca-4328-ac37-bae2d9ed0268 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 10132480 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007bb00)
[    0.000000] Memory: 1982164k/2026496k available (4565k kernel code, 42148k reserved, 2143k data, 540k init, 1116360k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1197.045 MHz processor.
[    0.001487] Console: colour VGA+ 80x25
[    0.001493] console [tty0] enabled
[    0.001747] hpet clockevent registered
[    0.001752] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.001760] Calibrating delay loop (skipped), value calculated using timer frequency.. 2394.09 BogoMIPS (lpj=4788180)
[    0.001784] Security Framework initialized
[    0.001811] AppArmor: AppArmor initialized
[    0.001821] Mount-cache hash table entries: 512
[    0.001991] Initializing cgroup subsys ns
[    0.001997] Initializing cgroup subsys cpuacct
[    0.002004] Initializing cgroup subsys memory
[    0.002013] Initializing cgroup subsys freezer
[    0.002017] Initializing cgroup subsys net_cls
[    0.002037] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.002041] CPU: L2 cache: 1024K
[    0.002048] mce: CPU supports 6 MCE banks
[    0.002057] CPU0: Thermal monitoring handled by SMI
[    0.002062] using mwait in idle threads.
[    0.002072] Performance Counters: Core2 events, Intel PMU driver.
[    0.002084] ... version:                 2
[    0.002087] ... bit width:               40
[    0.002089] ... generic counters:        2
[    0.002092] ... value mask:              000000ffffffffff
[    0.002095] ... max period:              000000007fffffff
[    0.002098] ... fixed-purpose counters:  3
[    0.002101] ... counter mask:            0000000700000003
[    0.002109] Checking 'hlt' instruction... OK.
[    0.017277] SMP alternatives: switching to UP code
[    0.028007] ACPI: Core revision 20090521
[    0.052423] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.094054] CPU0: Intel(R) Celeron(R) CPU          723  @ 1.20GHz stepping 0a
[    0.096001] Brought up 1 CPUs
[    0.096001] Total of 1 processors activated (2394.09 BogoMIPS).
[    0.096001] CPU0 attaching NULL sched-domain.
[    0.096001] Booting paravirtualized kernel on bare hardware
[    0.096001] regulator: core version 0.5
[    0.096001] Time: 20:10:52  Date: 11/02/09
[    0.096001] NET: Registered protocol family 16
[    0.096001] EISA bus registered
[    0.096001] ACPI: bus type pci registered
[    0.096001] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.096001] PCI: MCFG area at f8000000 reserved in E820
[    0.096001] PCI: Using MMCONFIG for extended config space
[    0.096001] PCI: Using configuration type 1 for base access
[    0.096001] bio: create slab <bio-0> at 0
[    0.096302] ACPI: EC: Look up EC in DSDT
[    0.104704] ACPI: BIOS _OSI(Linux) query ignored
[    0.105782] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.136163] ACPI: Interpreter enabled
[    0.136170] ACPI: (supports S0 S3 S4 S5)
[    0.136215] ACPI: Using IOAPIC for interrupt routing
[    0.169621] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.169625] ACPI: EC: driver started in interrupt mode
[    0.170146] ACPI: No dock devices found.
[    0.170910] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.172125] pci 0000:00:02.0: reg 10 64bit mmio: [0x90000000-0x903fffff]
[    0.172136] pci 0000:00:02.0: reg 18 64bit mmio: [0x80000000-0x8fffffff]
[    0.172143] pci 0000:00:02.0: reg 20 io port: [0x4110-0x4117]
[    0.172199] pci 0000:00:02.1: reg 10 64bit mmio: [0x000000-0x0fffff]
[    0.172361] pci 0000:00:1a.0: reg 20 io port: [0x40e0-0x40ff]
[    0.172499] pci 0000:00:1a.1: reg 20 io port: [0x40c0-0x40df]
[    0.172620] pci 0000:00:1a.7: reg 10 32bit mmio: [0x94405c00-0x94405fff]
[    0.172700] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.172707] pci 0000:00:1a.7: PME# disabled
[    0.172772] pci 0000:00:1b.0: reg 10 64bit mmio: [0x94400000-0x94403fff]
[    0.172841] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.172847] pci 0000:00:1b.0: PME# disabled
[    0.172944] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.172950] pci 0000:00:1c.0: PME# disabled
[    0.173048] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.173054] pci 0000:00:1c.1: PME# disabled
[    0.173157] pci 0000:00:1d.0: reg 20 io port: [0x40a0-0x40bf]
[    0.173297] pci 0000:00:1d.1: reg 20 io port: [0x4080-0x409f]
[    0.173438] pci 0000:00:1d.2: reg 20 io port: [0x4060-0x407f]
[    0.173577] pci 0000:00:1d.3: reg 20 io port: [0x4040-0x405f]
[    0.173696] pci 0000:00:1d.7: reg 10 32bit mmio: [0x94405800-0x94405bff]
[    0.173776] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.173783] pci 0000:00:1d.7: PME# disabled
[    0.174037] pci 0000:00:1f.2: reg 10 io port: [0x4108-0x410f]
[    0.174046] pci 0000:00:1f.2: reg 14 io port: [0x411c-0x411f]
[    0.174055] pci 0000:00:1f.2: reg 18 io port: [0x4100-0x4107]
[    0.174065] pci 0000:00:1f.2: reg 1c io port: [0x4118-0x411b]
[    0.174074] pci 0000:00:1f.2: reg 20 io port: [0x4020-0x403f]
[    0.174084] pci 0000:00:1f.2: reg 24 32bit mmio: [0x94405000-0x944057ff]
[    0.174134] pci 0000:00:1f.2: PME# supported from D3hot
[    0.174140] pci 0000:00:1f.2: PME# disabled
[    0.174185] pci 0000:00:1f.3: reg 10 64bit mmio: [0x94406000-0x944060ff]
[    0.174208] pci 0000:00:1f.3: reg 20 io port: [0x4000-0x401f]
[    0.174283] pci 0000:00:1f.6: reg 10 64bit mmio: [0x94404000-0x94404fff]
[    0.174425] pci 0000:01:00.0: reg 10 64bit mmio: [0x93400000-0x9343ffff]
[    0.174438] pci 0000:01:00.0: reg 18 io port: [0x3000-0x307f]
[    0.174526] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.174533] pci 0000:01:00.0: PME# disabled
[    0.174612] pci 0000:00:1c.0: bridge io port: [0x3000-0x3fff]
[    0.174619] pci 0000:00:1c.0: bridge 32bit mmio: [0x93400000-0x943fffff]
[    0.174629] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x90400000-0x913fffff]
[    0.174704] pci 0000:02:00.0: reg 10 64bit mmio: [0x92400000-0x9240ffff]
[    0.174797] pci 0000:02:00.0: supports D1
[    0.174800] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
[    0.174808] pci 0000:02:00.0: PME# disabled
[    0.174894] pci 0000:00:1c.1: bridge io port: [0x2000-0x2fff]
[    0.174900] pci 0000:00:1c.1: bridge 32bit mmio: [0x92400000-0x933fffff]
[    0.174909] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x91400000-0x923fffff]
[    0.174975] pci 0000:00:1e.0: transparent bridge
[    0.175012] pci_bus 0000:00: on NUMA node 0
[    0.175023] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.175461] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.175553] ACPI Warning: \_SB_.PCI0.P32_._PRT: Return Package has no elements (empty) 20090521 nspredef-434
[    0.175664] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.175831] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.203709] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.203935] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.204165] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.204385] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.204605] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.204826] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
[    0.205049] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.205269] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.205576] SCSI subsystem initialized
[    0.205641] libata version 3.00 loaded.
[    0.205738] usbcore: registered new interface driver usbfs
[    0.205760] usbcore: registered new interface driver hub
[    0.205793] usbcore: registered new device driver usb
[    0.206093] ACPI: WMI: Mapper loaded
[    0.206096] PCI: Using ACPI for IRQ routing
[    0.206312] Bluetooth: Core ver 2.15
[    0.206349] NET: Registered protocol family 31
[    0.206352] Bluetooth: HCI device and connection manager initialized
[    0.206356] Bluetooth: HCI socket layer initialized
[    0.206358] NetLabel: Initializing
[    0.206361] NetLabel:  domain hash size = 128
[    0.206363] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.206380] NetLabel:  unlabeled traffic allowed by default
[    0.206418] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.206426] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.213903] pnp: PnP ACPI init
[    0.213927] ACPI: bus type pnp registered
[    0.217086] pnp: PnP ACPI: found 9 devices
[    0.217090] ACPI: ACPI bus type pnp unregistered
[    0.217094] PnPBIOS: Disabled by ACPI PNP
[    0.217111] system 00:01: ioport range 0x164e-0x164f has been reserved
[    0.217117] system 00:01: ioport range 0x600-0x60f has been reserved
[    0.217121] system 00:01: ioport range 0x610-0x610 has been reserved
[    0.217125] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.217129] system 00:01: ioport range 0x810-0x817 has been reserved
[    0.217134] system 00:01: ioport range 0x820-0x823 has been reserved
[    0.217138] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.217142] system 00:01: ioport range 0x500-0x53f has been reserved
[    0.217147] system 00:01: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.217152] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.217156] system 00:01: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.217161] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.217165] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.217170] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.217174] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.217179] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.217183] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.217188] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.217192] system 00:01: iomem range 0xff800000-0xff800fff has been reserved
[    0.251914] AppArmor: AppArmor Filesystem Enabled
[    0.251970] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.251976] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.251985] pci 0000:00:1c.0:   MEM window: 0x93400000-0x943fffff
[    0.251991] pci 0000:00:1c.0:   PREFETCH window: 0x00000090400000-0x000000913fffff
[    0.252007] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.252012] pci 0000:00:1c.1:   IO window: 0x2000-0x2fff
[    0.252020] pci 0000:00:1c.1:   MEM window: 0x92400000-0x933fffff
[    0.252026] pci 0000:00:1c.1:   PREFETCH window: 0x00000091400000-0x000000923fffff
[    0.252036] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.252039] pci 0000:00:1e.0:   IO window: disabled
[    0.252046] pci 0000:00:1e.0:   MEM window: disabled
[    0.252052] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.252069]   alloc irq_desc for 16 on node -1
[    0.252072]   alloc kstat_irqs on node -1
[    0.252080] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.252087] pci 0000:00:1c.0: setting latency timer to 64
[    0.252097]   alloc irq_desc for 17 on node -1
[    0.252100]   alloc kstat_irqs on node -1
[    0.252105] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.252112] pci 0000:00:1c.1: setting latency timer to 64
[    0.252121] pci 0000:00:1e.0: setting latency timer to 64
[    0.252128] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.252132] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.252137] pci_bus 0000:01: resource 0 io:  [0x3000-0x3fff]
[    0.252141] pci_bus 0000:01: resource 1 mem: [0x93400000-0x943fffff]
[    0.252145] pci_bus 0000:01: resource 2 pref mem [0x90400000-0x913fffff]
[    0.252149] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.252153] pci_bus 0000:02: resource 1 mem: [0x92400000-0x933fffff]
[    0.252157] pci_bus 0000:02: resource 2 pref mem [0x91400000-0x923fffff]
[    0.252161] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.252165] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.252211] NET: Registered protocol family 2
[    0.252339] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.252744] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.253341] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.253686] TCP: Hash tables configured (established 131072 bind 65536)
[    0.253690] TCP reno registered
[    0.253831] NET: Registered protocol family 1
[    0.253913] Trying to unpack rootfs image as initramfs...
[    0.503999] Switched to high resolution mode on CPU 0
[    0.559040] Freeing initrd memory: 7462k freed
[    0.563091] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.563096] Simple Boot Flag at 0x44 set to 0x1
[    0.563264] cpufreq-nforce2: No nForce2 chipset.
[    0.563301] Scanning for low memory corruption every 60 seconds
[    0.563442] audit: initializing netlink socket (disabled)
[    0.563464] type=2000 audit(1257192652.560:1): initialized
[    0.577616] highmem bounce pool size: 64 pages
[    0.577624] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.579639] VFS: Disk quotas dquot_6.5.2
[    0.579717] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.580515] fuse init (API version 7.12)
[    0.580635] msgmni has been set to 1707
[    0.580880] alg: No test for stdrng (krng)
[    0.580896] io scheduler noop registered
[    0.580899] io scheduler anticipatory registered
[    0.580902] io scheduler deadline registered
[    0.580965] io scheduler cfq registered (default)
[    0.580980] pci 0000:00:02.0: Boot video device
[    2.180009] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    3.780008] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    3.780288]   alloc irq_desc for 24 on node -1
[    3.780291]   alloc kstat_irqs on node -1
[    3.780306] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    3.780320] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    3.780508]   alloc irq_desc for 25 on node -1
[    3.780512]   alloc kstat_irqs on node -1
[    3.780523] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    3.780536] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    3.780665] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.780842] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.783918] ACPI: AC Adapter [ADP1] (on-line)
[    3.784014] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    3.784020] ACPI: Power Button [PWRF]
[    3.784087] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    3.787281] ACPI: Lid Switch [LID0]
[    3.787347] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    3.787355] ACPI: Sleep Button [SLPB]
[    3.788866] Monitor-Mwait will be used to enter C-1 state
[    3.788900] Monitor-Mwait will be used to enter C-2 state
[    3.788911] Marking TSC unstable due to TSC halts in idle
[    3.788931] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    3.788963] processor LNXCPU:00: registered as cooling_device0
[    3.824455] thermal LNXTHERM:01: registered as thermal_zone0
[    3.824467] ACPI: Thermal Zone [TZS0] (24 C)
[    3.839461] thermal LNXTHERM:02: registered as thermal_zone1
[    3.839472] ACPI: Thermal Zone [TZS1] (24 C)
[    3.839538] isapnp: Scanning for PnP cards...
[    3.888773] ACPI: Battery Slot [BAT0] (battery absent)
[    4.193822] isapnp: No Plug & Play device found
[    4.195492] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    4.197270] brd: module loaded
[    4.197872] loop: module loaded
[    4.197972] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    4.198066] ahci 0000:00:1f.2: version 3.0
[    4.198084]   alloc irq_desc for 19 on node -1
[    4.198088]   alloc kstat_irqs on node -1
[    4.198097] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.198136]   alloc irq_desc for 26 on node -1
[    4.198139]   alloc kstat_irqs on node -1
[    4.198151] ahci 0000:00:1f.2: irq 26 for MSI/MSI-X
[    4.198205] ahci: SSS flag set, parallel bus scan disabled
[    4.198253] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    4.198258] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part ems 
[    4.198266] ahci 0000:00:1f.2: setting latency timer to 64
[    4.220089] scsi0 : ahci
[    4.220220] scsi1 : ahci
[    4.220288] scsi2 : ahci
[    4.220358] scsi3 : ahci
[    4.220436] scsi4 : ahci
[    4.220504] scsi5 : ahci
[    4.220875] ata1: SATA max UDMA/133 abar m2048@0x94405000 port 0x94405100 irq 26
[    4.220881] ata2: SATA max UDMA/133 abar m2048@0x94405000 port 0x94405180 irq 26
[    4.220884] ata3: DUMMY
[    4.220887] ata4: DUMMY
[    4.220891] ata5: SATA max UDMA/133 abar m2048@0x94405000 port 0x94405300 irq 26
[    4.220896] ata6: SATA max UDMA/133 abar m2048@0x94405000 port 0x94405380 irq 26
[    4.222025] Fixed MDIO Bus: probed
[    4.222074] PPP generic driver version 2.4.2
[    4.222207] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.222233] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    4.222255] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    4.222260] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.222327] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    4.226242] ehci_hcd 0000:00:1a.7: debug port 1
[    4.226250] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    4.226394] ehci_hcd 0000:00:1a.7: irq 19, io mem 0x94405c00
[    4.240020] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    4.240114] usb usb1: configuration #1 chosen from 1 choice
[    4.240155] hub 1-0:1.0: USB hub found
[    4.240165] hub 1-0:1.0: 4 ports detected
[    4.240235]   alloc irq_desc for 23 on node -1
[    4.240238]   alloc kstat_irqs on node -1
[    4.240246] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.240260] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.240264] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.240305] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.244216] ehci_hcd 0000:00:1d.7: debug port 1
[    4.244224] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.244241] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x94405800
[    4.260020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.260119] usb usb2: configuration #1 chosen from 1 choice
[    4.260156] hub 2-0:1.0: USB hub found
[    4.260165] hub 2-0:1.0: 8 ports detected
[    4.260244] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.260268] uhci_hcd: USB Universal Host Controller Interface driver
[    4.260304] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.260314] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.260319] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.260361] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.260404] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000040e0
[    4.260505] usb usb3: configuration #1 chosen from 1 choice
[    4.260541] hub 3-0:1.0: USB hub found
[    4.260550] hub 3-0:1.0: 2 ports detected
[    4.260610]   alloc irq_desc for 21 on node -1
[    4.260613]   alloc kstat_irqs on node -1
[    4.260620] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.260629] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    4.260634] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.260673] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.260713] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000040c0
[    4.260814] usb usb4: configuration #1 chosen from 1 choice
[    4.260850] hub 4-0:1.0: USB hub found
[    4.260858] hub 4-0:1.0: 2 ports detected
[    4.260923] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.260932] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.260936] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.260981] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    4.261012] uhci_hcd 0000:00:1d.0: irq 23, io base 0x000040a0
[    4.261116] usb usb5: configuration #1 chosen from 1 choice
[    4.261156] hub 5-0:1.0: USB hub found
[    4.261164] hub 5-0:1.0: 2 ports detected
[    4.261221] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.261229] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.261234] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.261273] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    4.261304] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00004080
[    4.261405] usb usb6: configuration #1 chosen from 1 choice
[    4.261446] hub 6-0:1.0: USB hub found
[    4.261455] hub 6-0:1.0: 2 ports detected
[    4.261514] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    4.261523] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.261527] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.261569] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    4.261600] uhci_hcd 0000:00:1d.2: irq 16, io base 0x00004060
[    4.261703] usb usb7: configuration #1 chosen from 1 choice
[    4.261740] hub 7-0:1.0: USB hub found
[    4.261752] hub 7-0:1.0: 2 ports detected
[    4.261808]   alloc irq_desc for 18 on node -1
[    4.261811]   alloc kstat_irqs on node -1
[    4.261818] uhci_hcd 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.261828] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    4.261833] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.261873] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    4.261914] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00004040
[    4.262020] usb usb8: configuration #1 chosen from 1 choice
[    4.262057] hub 8-0:1.0: USB hub found
[    4.262065] hub 8-0:1.0: 2 ports detected
[    4.262191] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    4.273508] i8042.c: Detected active multiplexing controller, rev 1.1.
[    4.281486] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.281494] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    4.281498] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    4.281503] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    4.281507] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    4.281582] mice: PS/2 mouse device common for all mice
[    4.281721] rtc_cmos 00:03: RTC can wake from S4
[    4.281769] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.281804] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    4.281947] device-mapper: uevent: version 1.0.3
[    4.282069] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    4.282172] device-mapper: multipath: version 1.1.0 loaded
[    4.282176] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.282326] EISA: Probing bus 0 at eisa.0
[    4.282338] Cannot allocate resource for EISA slot 2
[    4.282341] Cannot allocate resource for EISA slot 3
[    4.282344] Cannot allocate resource for EISA slot 4
[    4.282364] EISA: Detected 0 cards.
[    4.282458] cpuidle: using governor ladder
[    4.282520] cpuidle: using governor menu
[    4.283156] TCP cubic registered
[    4.283373] NET: Registered protocol family 10
[    4.283945] lo: Disabled Privacy Extensions
[    4.284365] NET: Registered protocol family 17
[    4.284389] Bluetooth: L2CAP ver 2.13
[    4.284391] Bluetooth: L2CAP socket layer initialized
[    4.284395] Bluetooth: SCO (Voice Link) ver 0.6
[    4.284397] Bluetooth: SCO socket layer initialized
[    4.284431] Bluetooth: RFCOMM TTY layer initialized
[    4.284435] Bluetooth: RFCOMM socket layer initialized
[    4.284438] Bluetooth: RFCOMM ver 1.11
[    4.284472] Using IPI No-Shortcut mode
[    4.284574] PM: Resume from disk failed.
[    4.284589] registered taskstats version 1
[    4.284741]   Magic number: 1:917:193
[    4.284786] acpi device:1f: hash matches
[    4.284834] rtc_cmos 00:03: setting system clock to 2009-11-02 20:10:56 UTC (1257192656)
[    4.284838] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.284840] EDD information not available.
[    4.303725] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    4.558034] ata1: SATA link down (SStatus 0 SControl 300)
[    4.612027] usb 2-5: new high speed USB device using ehci_hcd and address 2
[    5.003231] usb 2-5: configuration #1 chosen from 1 choice
[    5.096040] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.097455] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    5.097596] ata2.00: ATA-8: Hitachi HTS545025B9A300, PB2OC60F, max UDMA/133
[    5.097601] ata2.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    5.099166] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    5.099344] ata2.00: configured for UDMA/133
[    5.112242] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HTS54502 PB2O PQ: 0 ANSI: 5
[    5.112401] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    5.112455] sd 1:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    5.112518] sd 1:0:0:0: [sda] Write Protect is off
[    5.112523] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.112556] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.112721]  sda: sda1 sda2 sda3
[    5.135577] sd 1:0:0:0: [sda] Attached SCSI disk
[    6.000037] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.003926] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    6.003934] ata5.00: ATAPI: MATSHITADVD-RAM UJ862AS, 1.00, max UDMA/33
[    6.011869] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    6.011913] ata5.00: configured for UDMA/33
[    6.035460] scsi 4:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ862AS  1.00 PQ: 0 ANSI: 5
[    6.050430] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.050434] Uniform CD-ROM driver Revision: 3.20
[    6.050539] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    6.050598] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    6.368036] ata6: SATA link down (SStatus 0 SControl 300)
[    6.384042] Freeing unused kernel memory: 540k freed
[    6.384328] Write protecting the kernel text: 4568k
[    6.384372] Write protecting the kernel read-only data: 1836k
[    6.656771] Linux agpgart interface v0.103
[    6.661430] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[    6.661834] agpgart-intel 0000:00:00.0: detected 65532K stolen memory
[    6.664901] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
[    6.817606] [drm] Initialized drm 1.1.0 20060810
[    6.837277] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.837285] i915 0000:00:02.0: setting latency timer to 64
[    6.839555]   alloc irq_desc for 27 on node -1
[    6.839559]   alloc kstat_irqs on node -1
[    6.839571] i915 0000:00:02.0: irq 27 for MSI/MSI-X
[    6.947894] [drm] i2c_init DPDDC-B
[    6.959159] [drm] i2c_init DPDDC-D
[    7.090275] i2c-adapter i2c-2: unable to read EDID block.
[    7.090281] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    7.100284] [drm] fb0: inteldrmfb frame buffer device
[    7.125358] acpi device:03: registered as cooling_device1
[    7.125867] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input5
[    7.125914] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[    7.125985] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    7.507697] [drm] LVDS-8: set mode 1366x768 14
[    8.073221] Console: switching to colour frame buffer device 170x48
[    8.507860] PM: Starting manual resume from disk
[    8.507866] PM: Resume from partition 8:1
[    8.507869] PM: Checking hibernation image.
[    8.507999] PM: Resume from disk failed.
[    8.533051] EXT4-fs (sda2): barriers enabled
[    8.546384] kjournald2 starting: pid 379, dev sda2:8, commit interval 5 seconds
[    8.546400] EXT4-fs (sda2): delayed allocation enabled
[    8.546404] EXT4-fs: file extents enabled
[    8.547756] EXT4-fs: mballoc enabled
[    8.547774] EXT4-fs (sda2): mounted filesystem with ordered data mode
[    9.128513] type=1505 audit(1257192661.343:2): operation="profile_load" pid=402 name=/usr/share/gdm/guest-session/Xsession
[    9.131590] type=1505 audit(1257192661.343:3): operation="profile_load" pid=403 name=/sbin/dhclient3
[    9.132819] type=1505 audit(1257192661.347:4): operation="profile_load" pid=403 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.133475] type=1505 audit(1257192661.347:5): operation="profile_load" pid=403 name=/usr/lib/connman/scripts/dhclient-script
[    9.182288] type=1505 audit(1257192661.395:6): operation="profile_load" pid=404 name=/usr/bin/evince
[    9.201019] type=1505 audit(1257192661.415:7): operation="profile_load" pid=404 name=/usr/bin/evince-previewer
[    9.212094] type=1505 audit(1257192661.427:8): operation="profile_load" pid=404 name=/usr/bin/evince-thumbnailer
[    9.236169] type=1505 audit(1257192661.451:9): operation="profile_load" pid=406 name=/usr/lib/cups/backend/cups-pdf
[    9.237573] type=1505 audit(1257192661.451:10): operation="profile_load" pid=406 name=/usr/sbin/cupsd
[    9.270022] type=1505 audit(1257192661.483:11): operation="profile_load" pid=407 name=/usr/sbin/ntpd
[    9.867540] Adding 4104568k swap on /dev/sda1.  Priority:-1 extents:1 across:4104568k 
[   10.191302] udev: starting version 147
[   10.515439] EXT4-fs (sda2): internal journal on sda2:8
[   11.037868] atl1c 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.037883] atl1c 0000:01:00.0: setting latency timer to 64
[   11.037934] atl1c 0000:01:00.0: PME# disabled
[   11.037941] atl1c 0000:01:00.0: PME# disabled
[   11.144958] atl1c 0000:01:00.0: version 1.0.0.1-NAPI
[   11.196770] acer-wmi: Acer Laptop ACPI-WMI Extras
[   11.206008] acer-wmi: Brightness must be controlled by generic video driver
[   11.349568] lp: driver loaded but no devices found
[   11.635030] cfg80211: Calling CRDA to update world regulatory domain
[   11.695595] Linux video capture interface: v2.00
[   12.117662] uvcvideo: Found UVC 1.00 device CNF9113 (04f2:b160)
[   12.129415] input: CNF9113 as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input6
[   12.129478] usbcore: registered new interface driver uvcvideo
[   12.129486] USB Video Class driver (v0.1.0)
[   12.159518] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
[   12.219241] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input7
[   12.400031] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   12.570197] usb 3-2: configuration #1 chosen from 1 choice
[   13.053368] EXT4-fs (sda3): barriers enabled
[   13.053636] kjournald2 starting: pid 714, dev sda3:8, commit interval 5 seconds
[   13.062931] EXT4-fs (sda3): internal journal on sda3:8
[   13.062937] EXT4-fs (sda3): delayed allocation enabled
[   13.062941] EXT4-fs: file extents enabled
[   13.087183] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.102579] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   13.102741] usbcore: registered new interface driver btusb
[   13.111155] EXT4-fs: mballoc enabled
[   13.111179] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   13.799053] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.799070] ath9k 0000:02:00.0: setting latency timer to 64
[   14.234038] ath: EEPROM regdomain: 0x65
[   14.234041] ath: EEPROM indicates we should expect a direct regpair map
[   14.234046] ath: Country alpha2 being used: 00
[   14.234049] ath: Regpair used: 0x65
[   14.364044] cfg80211: World regulatory domain updated:
[   14.364050] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.364055] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.364059] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.364063] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.364066] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.364070] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.686287] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.687191] Registered led device: ath9k-phy0::radio
[   14.687218] Registered led device: ath9k-phy0::assoc
[   14.687242] Registered led device: ath9k-phy0::tx
[   14.687267] Registered led device: ath9k-phy0::rx
[   14.687295] phy0: Atheros AR9280 MAC/BB Rev:2 AR5133 RF Rev:d0: mem=0xf9600000, irq=17
[   15.365345] __ratelimit: 3 callbacks suppressed
[   15.365350] type=1505 audit(1257192667.579:13): operation="profile_replace" pid=809 name=/usr/share/gdm/guest-session/Xsession
[   15.368146] type=1505 audit(1257192667.583:14): operation="profile_replace" pid=810 name=/sbin/dhclient3
[   15.369415] type=1505 audit(1257192667.583:15): operation="profile_replace" pid=810 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   15.370074] type=1505 audit(1257192667.583:16): operation="profile_replace" pid=810 name=/usr/lib/connman/scripts/dhclient-script
[   15.376640] type=1505 audit(1257192667.591:17): operation="profile_replace" pid=811 name=/usr/bin/evince
[   15.395751] type=1505 audit(1257192667.607:18): operation="profile_replace" pid=811 name=/usr/bin/evince-previewer
[   15.407625] type=1505 audit(1257192667.619:19): operation="profile_replace" pid=811 name=/usr/bin/evince-thumbnailer
[   15.428281]   alloc irq_desc for 22 on node -1
[   15.428286]   alloc kstat_irqs on node -1
[   15.428296] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.428344] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.430413] type=1505 audit(1257192667.643:20): operation="profile_replace" pid=813 name=/usr/lib/cups/backend/cups-pdf
[   15.431863] type=1505 audit(1257192667.643:21): operation="profile_replace" pid=813 name=/usr/sbin/cupsd
[   15.435936] type=1505 audit(1257192667.647:22): operation="profile_replace" pid=814 name=/usr/sbin/ntpd
[   15.621379] hda_codec: Unknown model for ALC269, trying auto-probe from BIOS...
[   15.621501] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   21.784146]   alloc irq_desc for 28 on node -1
[   21.784151]   alloc kstat_irqs on node -1
[   21.784172] atl1c 0000:01:00.0: irq 28 for MSI/MSI-X
[   21.784706] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.032229] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.561350] ppdev: user-space parallel port driver
[   24.773505] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.773509] Bluetooth: BNEP filters: protocol multicast
[   24.902725] Bridge firewalling registered
[   26.145288] i2c-adapter i2c-2: unable to read EDID block.
[   26.145295] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   26.150415] i2c-adapter i2c-2: unable to read EDID block.
[   26.150421] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   26.405051] i2c-adapter i2c-2: unable to read EDID block.
[   26.405059] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   26.411013] i2c-adapter i2c-2: unable to read EDID block.
[   26.411020] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   31.860308] i2c-adapter i2c-2: unable to read EDID block.
[   31.860315] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   31.864740] i2c-adapter i2c-2: unable to read EDID block.
[   31.864744] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   32.011667] i2c-adapter i2c-2: unable to read EDID block.
[   32.011674] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   32.016636] i2c-adapter i2c-2: unable to read EDID block.
[   32.016641] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   32.183830] i2c-adapter i2c-2: unable to read EDID block.
[   32.183837] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   32.188808] i2c-adapter i2c-2: unable to read EDID block.
[   32.188812] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   48.893689] i2c-adapter i2c-2: unable to read EDID block.
[   48.893696] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   48.898789] i2c-adapter i2c-2: unable to read EDID block.
[   48.898794] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   49.059028] i2c-adapter i2c-2: unable to read EDID block.
[   49.059034] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   49.063990] i2c-adapter i2c-2: unable to read EDID block.
[   49.063994] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   49.211708] i2c-adapter i2c-2: unable to read EDID block.
[   49.211715] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   49.216677] i2c-adapter i2c-2: unable to read EDID block.
[   49.216681] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   52.232569] i2c-adapter i2c-2: unable to read EDID block.
[   52.232575] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   52.237673] i2c-adapter i2c-2: unable to read EDID block.
[   52.237679] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[  135.264501] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[  135.464032] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[  135.467548] wlan0: authenticated
[  135.467552] wlan0: associate with AP 00:1d:7e:60:fd:fd
[  135.664051] wlan0: associate with AP 00:1d:7e:60:fd:fd
[  135.864030] wlan0: associate with AP 00:1d:7e:60:fd:fd
[  135.869279] wlan0: RX AssocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[  135.869284] wlan0: associated
[  135.869776] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  136.951033] padlock: VIA PadLock not detected.
[  146.484034] wlan0: no IPv6 routers present
[  173.844030] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[  175.030859] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[  175.034725] wlan0: authenticated
[  175.034732] wlan0: associate with AP 00:1d:7e:60:fd:fd
[  175.037249] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[  175.037254] wlan0: associated
[  203.856032] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[  205.049885] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[  205.054624] wlan0: authenticated
[  205.054632] wlan0: associate with AP 00:1d:7e:60:fd:fd
[  205.058548] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[  205.058554] wlan0: associated
[  218.016037] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[  219.170896] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[  219.368032] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[  219.371218] wlan0: authenticated
[  219.371224] wlan0: associate with AP 00:1d:7e:60:fd:fd
[  219.374460] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[  219.374466] wlan0: associated
[  263.868026] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[  265.049735] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[  265.052249] wlan0: authenticated
[  265.052255] wlan0: associate with AP 00:1d:7e:60:fd:fd
[  265.054775] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[  265.054782] wlan0: associated
[  724.072029] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[  725.250896] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[  725.253769] wlan0: authenticated
[  725.253776] wlan0: associate with AP 00:1d:7e:60:fd:fd
[  725.257282] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[  725.257288] wlan0: associated
[  834.815572] wlan0: deauthenticated (Reason: 7)
[  835.812041] wlan0: direct probe to AP 00:1d:7e:60:fd:fd try 1
[  835.814799] wlan0 direct probe responded
[  835.814803] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[  835.816784] wlan0: authenticated
[  835.816788] wlan0: associate with AP 00:1d:7e:60:fd:fd
[  835.819314] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[  835.819318] wlan0: associated
[  845.822701] wlan0: disassociating by local choice (reason=3)
[  847.924958] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[  848.124027] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[  848.324033] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[  848.524024] wlan0: authentication with AP 00:1d:7e:60:fd:fd timed out
[  863.978737] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[  863.991596] wlan0: authenticated
[  863.991602] wlan0: associate with AP 00:1d:7e:60:fd:fd
[  863.994030] wlan0: RX AssocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[  863.994035] wlan0: associated
[  963.580025] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[  988.958752] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[  989.156027] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[  989.356029] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[  989.556026] wlan0: authentication with AP 00:1d:7e:60:fd:fd timed out
[ 1030.298759] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 1030.303088] wlan0: authenticated
[ 1030.303094] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 1030.306834] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 1030.306839] wlan0: associated
[ 1233.616024] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[ 1313.506727] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 1313.508756] wlan0: authenticated
[ 1313.508762] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 1313.524455] wlan0: deauthenticated (Reason: 6)
[ 1314.524026] wlan0: direct probe to AP 00:1d:7e:60:fd:fd try 1
[ 1314.526281] wlan0 direct probe responded
[ 1314.526285] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 1314.528498] wlan0: authenticated
[ 1314.528503] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 1314.533364] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 1314.533368] wlan0: associated
[ 1320.584026] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[ 1321.738719] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 1321.742017] wlan0: authenticated
[ 1321.742023] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 1321.756720] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 1321.756726] wlan0: associated
[ 1331.796033] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[ 1345.058065] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 1345.060056] wlan0: authenticated
[ 1345.060062] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 1345.067494] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 1345.067500] wlan0: associated
[ 1355.080024] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[ 1362.290867] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 1362.292953] wlan0: authenticated
[ 1362.292961] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 1362.295558] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 1362.295563] wlan0: associated
[ 1405.909099] wlan0: deauthenticated (Reason: 7)
[ 1406.908024] wlan0: direct probe to AP 00:1d:7e:60:fd:fd try 1
[ 1406.910780] wlan0 direct probe responded
[ 1406.910784] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 1406.912729] wlan0: authenticated
[ 1406.912733] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 1406.915302] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 1406.915306] wlan0: associated
[ 1437.568036] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[ 1438.722761] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 1438.724811] wlan0: authenticated
[ 1438.724817] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 1438.727341] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 1438.727346] wlan0: associated
[ 1497.428786] wlan0: deauthenticated (Reason: 7)
[ 1498.428029] wlan0: direct probe to AP 00:1d:7e:60:fd:fd try 1
[ 1498.628028] wlan0: direct probe to AP 00:1d:7e:60:fd:fd try 2
[ 1498.828028] wlan0: direct probe to AP 00:1d:7e:60:fd:fd try 3
[ 1499.028029] wlan0: direct probe to AP 00:1d:7e:60:fd:fd timed out
[ 1506.139048] wlan0: direct probe to AP 00:1d:7e:60:fd:fd try 1
[ 1506.141917] wlan0 direct probe responded
[ 1506.141924] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 1506.143898] wlan0: authenticated
[ 1506.143903] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 1506.146392] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 1506.146396] wlan0: associated
[ 1550.164026] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[ 1563.430752] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 1563.432795] wlan0: authenticated
[ 1563.432801] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 1563.435320] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 1563.435325] wlan0: associated
[ 1581.448028] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[ 1582.602732] wlan0: direct probe to AP 00:1d:7e:60:fd:fd try 1
[ 1582.606789] wlan0 direct probe responded
[ 1582.606795] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 1582.609025] wlan0: authenticated
[ 1582.609029] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 1582.611597] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 1582.611601] wlan0: associated
[ 1669.904035] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[ 1677.122978] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 1677.126361] wlan0: authenticated
[ 1677.126367] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 1677.128929] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 1677.128934] wlan0: associated
[ 1699.164028] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[ 1706.373360] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 1706.375413] wlan0: authenticated
[ 1706.375420] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 1706.378429] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 1706.378435] wlan0: associated
[ 1720.396028] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[ 1733.666751] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 1733.669096] wlan0: authenticated
[ 1733.669102] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 1733.671633] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 1733.671638] wlan0: associated
[ 1777.904032] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[ 1785.114736] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 1785.118090] wlan0: authenticated
[ 1785.118097] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 1785.120701] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 1785.120705] wlan0: associated
[ 1803.476029] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[ 1804.634731] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 1804.638072] wlan0: authenticated
[ 1804.638079] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 1804.640671] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 1804.640675] wlan0: associated
[ 1965.904043] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[ 1973.130742] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 1973.133071] wlan0: authenticated
[ 1973.133079] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 1973.135690] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 1973.135695] wlan0: associated
[ 2372.515776] wlan0: deauthenticated (Reason: 7)
[ 2373.512025] wlan0: direct probe to AP 00:1d:7e:60:fd:fd try 1
[ 2373.514781] wlan0 direct probe responded
[ 2373.514785] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 2373.516785] wlan0: authenticated
[ 2373.516789] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 2373.520304] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 2373.520308] wlan0: associated
[ 2720.440034] wlan0: deauthenticated (Reason: 7)
[ 2721.440031] wlan0: direct probe to AP 00:1d:7e:60:fd:fd try 1
[ 2721.467562] wlan0 direct probe responded
[ 2721.467568] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 2721.664025] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 2721.864026] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 2721.868232] wlan0: authenticated
[ 2721.868236] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 2721.883559] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 2721.883564] wlan0: associated
[ 2731.894209] wlan0: disassociating by local choice (reason=3)
[ 2733.996958] wlan0: direct probe to AP 00:1d:7e:60:fd:fd try 1
[ 2734.001115] wlan0 direct probe responded
[ 2734.001122] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 2734.200028] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 2734.201968] wlan0: authenticated
[ 2734.201972] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 2734.204513] wlan0: RX AssocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 2734.204518] wlan0: associated
[ 2797.452830] wlan0: disassociating by local choice (reason=3)
[ 2808.562868] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 2808.565799] wlan0: authenticated
[ 2808.565815] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 2808.568325] wlan0: RX AssocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 2808.568329] wlan0: associated
[ 2999.124032] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[ 3000.303008] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 3000.305069] wlan0: authenticated
[ 3000.305075] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 3000.308340] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 3000.308346] wlan0: associated
[ 3031.880327] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[ 3033.050960] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 3033.053697] wlan0: authenticated
[ 3033.053703] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 3033.062951] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 3033.062957] wlan0: associated
[ 3175.428048] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[ 3176.606907] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 3176.611065] wlan0: authenticated
[ 3176.611072] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 3176.616793] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 3176.616798] wlan0: associated
[ 3238.764030] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[ 3245.974912] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 3245.978342] wlan0: authenticated
[ 3245.978349] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 3245.980827] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 3245.980832] wlan0: associated
[ 3251.992022] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
[ 3288.942854] wlan0: authenticate with AP 00:1d:7e:60:fd:fd
[ 3288.944888] wlan0: authenticated
[ 3288.944895] wlan0: associate with AP 00:1d:7e:60:fd:fd
[ 3288.948574] wlan0: RX ReassocResp from 00:1d:7e:60:fd:fd (capab=0x411 status=0 aid=4)
[ 3288.948580] wlan0: associated
[ 3326.640042] wlan0: no probe response from AP 00:1d:7e:60:fd:fd - disassociating
```

What I don't understand here is that this laptop came with preinstalled linpus. I've installed ubuntu 9.10 over it thinking: "If it came with preinstalled Linux, great all the hardware is supported" Neeeeeeein. Mistake and burn I'll learn from it now trying to fix problems. I hope someone here would help  me fix those problems? 

What else do I have to show from my hardare what outputs in order for you to help me out?

---

### Post by frojnd on 2009-11-03
I've tried to add applet for brightness but nothing happened. Can someone please help me solve one of multiple issues?

---

### Post by frojnd on 2009-11-04
Bump Bump any ideas?

---

### Post by frojnd on 2009-11-04
Hm.. So Ubuntu 9.10 uses some kind of a device kit instead of HAL. How does this thing work? I would add some outputs but I don't know how for known problems. Should I report this as a bug that CDROM doesn't work, brightness control doesn't work. After pressing the button for disabling touch pad the only work around is reboot?

---

### Post by doubi on 2009-11-07
Hello frojnd, 

I'm afraid I can't help you at all :-/ Instead I have a question for you: What's the "button for disabling the touchpad" that you speak of?

I have an Aspire 5720 and after the Karmic upgrade my touchpad won't work at all. I haven't seen anyone report any similar problems, but I didn't know there was a button for controlling the touchpad... is this on the desktop somewhere or one of the hardware 'media keys' or whatever they're called?

Sorry I can't be any help for your problems. At least you're not the only Acer user who's been a bit screwed by 9.10 :|

---

### Post by frojnd on 2009-11-07
doubi. That's too bad. I was hoping at least someone will tell me how to disable this button if it's not implemented :S I'd rather not have it than restart it, if I accidentally press it :S 
I've added photo under attachment.

Also can someone please tell me how can I make change of brightness control make it happen?

---

### Post by frojnd on 2009-11-07
Does anyone even know how thus button is called? How can I get info from dmesg why I need to reboot? So I can report a bug.

---

### Post by frojnd on 2009-11-19
CD/DVD drive now works thanks to hiemanshu from freenode.oerg
I just had to change AHCI to IDE mode in bios since I have sata :)

---

### Post by stgreg399 on 2009-12-25
Hi frojnd,
I've been having a lot of hardware issues as well with the exact same model. Same problem with the CD/DVD drive, it doesn't recognise any CDs and the icon disappears from My Computer when I try to do open or eject it.
I've also had to force it to shutdown so many times (it seems to get stuck on the 'Shutting Down' screen).
What did you do to sort out the CD drive? because that's what's bugging me most of all.
Thanks :)

---

