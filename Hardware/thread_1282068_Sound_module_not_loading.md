---
title: "Sound module not loading"
date: 2009-10-03
forum: Hardware
---

### Post by takiama on 2009-10-03
Hey guys.  I am new to the forum this is my first post, so hello.  Anyway, here is my issue.  I recently installed Ubuntu 9.04 on my laptop.  I have gotten everything to work fine except for my audio.  To my knowledge, my audio controller is the Intel High Definition Audio ICH9 Series.  I did some research and found that this device should be supported by the latest version of ALSA (1.0.21) which I have complied and installed.  However, whenever I try to load the snd-hda-intel module (which I believe to be the correct one for my device) using "sudo modprobe snd-hda-intel", I get the following error:
```
FATAL: Error inserting snd (/lib/modules/2.6.28-15-generic/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.28-15-generic/updates/alsa/acore/snd-page-alloc.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.28-15-generic/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_pcm (/lib/modules/2.6.28-15-generic/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.28-15-generic/updates/alsa/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```So , since it asks for the dmesg, here it is:
```
[    0.000000] BIOS EBDA/lowmem at: 00097c00/00097c00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 (Ubuntu 2.6.28-15.52-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000097c00 (usable)
[    0.000000]  BIOS-e820: 0000000000097c00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e1000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bdd80000 (usable)
[    0.000000]  BIOS-e820: 00000000bdd80000 - 00000000bdd8f000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bdd8f000 - 00000000bdde0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bdde0000 - 00000000bde00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed40000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.5 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xbdd80 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000097c00 (usable)
[    0.000000]  modified: 0000000000097c00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e1000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bdd80000 (usable)
[    0.000000]  modified: 00000000bdd80000 - 00000000bdd8f000 (ACPI data)
[    0.000000]  modified: 00000000bdd8f000 - 00000000bdde0000 (ACPI NVS)
[    0.000000]  modified: 00000000bdde0000 - 00000000bde00000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed40000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378b8000 - 37fef413
[    0.000000] Allocated new RAMDISK: 0087d000 - 00fb4413
[    0.000000] Move RAMDISK from 00000000378b8000 - 0000000037fef412 to 0087d000 - 00fb4412
[    0.000000] ACPI: RSDP 000F93E0, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT BDD80100, 0084 (r1 _ASUS_ Notebook 20090508 MSFT       97)
[    0.000000] ACPI: FACP BDD80290, 00F4 (r3 050809 FACP1447 20090508 MSFT       97)
[    0.000000] ACPI: DSDT BDD80680, C7B4 (r1  K50IJ K50IJ207      207 INTL 20051117)
[    0.000000] ACPI: FACS BDD8F000, 0040
[    0.000000] ACPI: APIC BDD80390, 005C (r1 050809 APIC1447 20090508 MSFT       97)
[    0.000000] ACPI: MCFG BDD80430, 003C (r1 050809 OEMMCFG  20090508 MSFT       97)
[    0.000000] ACPI: SLIC BDD80470, 0176 (r1 _ASUS_ Notebook 20090508 MSFT       97)
[    0.000000] ACPI: ECDT BDD80620, 0054 (r1 050809 OEMECDT  20090508 MSFT       97)
[    0.000000] ACPI: DBGP BDD803F0, 0034 (r1 050809 DBGP1447 20090508 MSFT       97)
[    0.000000] ACPI: BOOT BDD805F0, 0028 (r1 050809 BOOT1447 20090508 MSFT       97)
[    0.000000] ACPI: OEMB BDD8F040, 0071 (r1 050809 OEMB1447 20090508 MSFT       97)
[    0.000000] ACPI: HPET BDD8CE40, 0038 (r1 050809 OEMHPET  20090508 MSFT       97)
[    0.000000] ACPI: GSCI BDD8F0C0, 2024 (r1 050809 GMCHSCI  20090508 MSFT       97)
[    0.000000] ACPI: ATKG BDD912F0, 8024 (r1 022008  OEMATKG 20080220 MSFT       97)
[    0.000000] ACPI: SSDT BDD99E00, 04F0 (r1  PmRef    CpuPm     3000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2153MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #5 [0000097c00 - 0000100000]    BIOS reserved ==> [0000097c00 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087d000 - 0000fb4413]      NEW RAMDISK ==> [000087d000 - 0000fb4413]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000bdd80
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x00000097
[    0.000000]     0: 0x00000100 -> 0x000bdd80
[    0.000000] On node 0 totalpages: 777479
[    0.000000] free_area_init_node: node 0, pgdat c06cb780, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3943 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4308 pages used for memmap
[    0.000000]   HighMem zone: 546990 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000097000 - 0000000000098000
[    0.000000] PM: Registered nosave memory: 0000000000098000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
[    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: bde00000:40f20000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 771403
[    0.000000] Kernel command line: root=UUID=8349250c-5200-4662-b55c-38cedcf2e4c4 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1999.807 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 15551680 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 3053412k/3110400k available (4116k kernel code, 55540k reserved, 2199k data, 532k init, 2205192k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc05050ff - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05050ff   (4116 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3999.61 BogoMIPS (lpj=7999228)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.020007] ACPI: Core revision 20080926
[    0.025597] ACPI: Checking initramfs for custom DSDT
[    0.536179] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.576591] CPU0: Intel Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz stepping 0a
[    0.580002] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4000.14 BogoMIPS (lpj=8000288)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.664530] CPU1: Intel Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz stepping 0a
[    0.664555] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.668043] Brought up 2 CPUs
[    0.668047] Total of 2 processors activated (7999.75 BogoMIPS).
[    0.668110] CPU0 attaching sched-domain:
[    0.668114]  domain 0: span 0-1 level MC
[    0.668118]   groups: 0 1
[    0.668127] CPU1 attaching sched-domain:
[    0.668130]  domain 0: span 0-1 level MC
[    0.668133]   groups: 1 0
[    0.668227] net_namespace: 776 bytes
[    0.668227] Booting paravirtualized kernel on bare hardware
[    0.668475] Time: 16:08:48  Date: 10/03/09
[    0.668475] regulator: core version 0.5
[    0.668475] NET: Registered protocol family 16
[    0.668475] EISA bus registered
[    0.668475] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.668475] ACPI: bus type pci registered
[    0.668475] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.668475] PCI: Not using MMCONFIG.
[    0.668578] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=7
[    0.668581] PCI: Using configuration type 1 for base access
[    0.673993] ACPI: EC: EC description table is found, configuring boot EC
[    0.672026] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.694106] ACPI: BIOS _OSI(Linux) query ignored
[    0.699782] ACPI: Interpreter enabled
[    0.699794] ACPI: (supports S0 S1 S3 S4 S5)
[    0.699832] ACPI: Using IOAPIC for interrupt routing
[    0.700038] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.707146] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.707150] PCI: Using MMCONFIG for extended config space
[    0.725250] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
[    0.725253] ACPI: EC: driver started in interrupt mode
[    0.725670] ACPI: No dock devices found.
[    0.725843] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.725969] pci 0000:00:02.0: reg 10 64bit mmio: [0xfd800000-0xfdbfffff]
[    0.725980] pci 0000:00:02.0: reg 18 64bit mmio: [0xd0000000-0xdfffffff]
[    0.725987] pci 0000:00:02.0: reg 20 io port: [0xcc00-0xcc07]
[    0.726036] pci 0000:00:02.1: reg 10 64bit mmio: [0xfdd00000-0xfddfffff]
[    0.726193] pci 0000:00:1a.0: reg 20 io port: [0xc880-0xc89f]
[    0.726301] pci 0000:00:1a.1: reg 20 io port: [0xc800-0xc81f]
[    0.726410] pci 0000:00:1a.2: reg 20 io port: [0xc480-0xc49f]
[    0.726520] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfdefbc00-0xfdefbfff]
[    0.726581] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.726588] pci 0000:00:1a.7: PME# disabled
[    0.726663] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfdef4000-0xfdef7fff]
[    0.726715] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.726722] pci 0000:00:1b.0: PME# disabled
[    0.726806] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.726813] pci 0000:00:1c.0: PME# disabled
[    0.726901] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.726907] pci 0000:00:1c.1: PME# disabled
[    0.726995] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.727002] pci 0000:00:1c.2: PME# disabled
[    0.727090] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.727096] pci 0000:00:1c.3: PME# disabled
[    0.727186] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.727192] pci 0000:00:1c.5: PME# disabled
[    0.727288] pci 0000:00:1d.0: reg 20 io port: [0xc400-0xc41f]
[    0.727397] pci 0000:00:1d.1: reg 20 io port: [0xc080-0xc09f]
[    0.727504] pci 0000:00:1d.2: reg 20 io port: [0xc000-0xc01f]
[    0.727613] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfdefb800-0xfdefbbff]
[    0.727673] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.727680] pci 0000:00:1d.7: PME# disabled
[    0.727955] pci 0000:00:1f.2: reg 10 io port: [0xbc00-0xbc07]
[    0.727965] pci 0000:00:1f.2: reg 14 io port: [0xb880-0xb883]
[    0.727975] pci 0000:00:1f.2: reg 18 io port: [0xb800-0xb807]
[    0.727986] pci 0000:00:1f.2: reg 1c io port: [0xb480-0xb483]
[    0.727996] pci 0000:00:1f.2: reg 20 io port: [0xb400-0xb41f]
[    0.728011] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfdefb000-0xfdefb7ff]
[    0.728038] pci 0000:00:1f.2: PME# supported from D3hot
[    0.728044] pci 0000:00:1f.2: PME# disabled
[    0.728240] pci 0000:02:00.0: reg 10 64bit mmio: [0xfdff0000-0xfdffffff]
[    0.728306] pci 0000:02:00.0: supports D1
[    0.728309] pci 0000:02:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.728316] pci 0000:02:00.0: PME# disabled
[    0.728413] pci 0000:00:1c.1: bridge 32bit mmio: [0xfdf00000-0xfdffffff]
[    0.728496] pci 0000:00:1c.2: bridge io port: [0xd000-0xdfff]
[    0.728504] pci 0000:00:1c.2: bridge 32bit mmio: [0xfe000000-0xfeafffff]
[    0.728515] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xfa000000-0xfcffffff]
[    0.728682] pci 0000:06:00.0: reg 10 64bit mmio: [0xfebc0000-0xfebfffff]
[    0.728696] pci 0000:06:00.0: reg 18 io port: [0xec00-0xec7f]
[    0.728753] pci 0000:06:00.0: PME# supported from D3hot D3cold
[    0.728760] pci 0000:06:00.0: PME# disabled
[    0.728849] pci 0000:00:1c.5: bridge io port: [0xe000-0xefff]
[    0.728856] pci 0000:00:1c.5: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.728950] pci 0000:00:1e.0: transparent bridge
[    0.729014] bus 00 -> node 0
[    0.729028] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.729540] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.729762] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.730058] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.778659] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12)
[    0.778976] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 10 12)
[    0.779286] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[    0.779594] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 12)
[    0.779904] ACPI: PCI Interrupt Link [LNKE] (IRQs 6) *0, disabled.
[    0.780220] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 12)
[    0.780532] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 12)
[    0.780844] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 12)
[    0.785621] ACPI Warning (tbutils-0217): Incorrect checksum in table [ATKG] - C3, should be E5 [20080926]
[    0.785668] ACPI: WMI: Mapper loaded
[    0.785751] SCSI subsystem initialized
[    0.785751] libata version 3.00 loaded.
[    0.785751] usbcore: registered new interface driver usbfs
[    0.785751] usbcore: registered new interface driver hub
[    0.785751] usbcore: registered new device driver usb
[    0.785751] PCI: Using ACPI for IRQ routing
[    0.792013] Bluetooth: Core ver 2.13
[    0.792031] NET: Registered protocol family 31
[    0.792031] Bluetooth: HCI device and connection manager initialized
[    0.792031] Bluetooth: HCI socket layer initialized
[    0.792031] NET: Registered protocol family 8
[    0.792034] NET: Registered protocol family 20
[    0.792050] NetLabel: Initializing
[    0.792053] NetLabel:  domain hash size = 128
[    0.792056] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.792074] NetLabel:  unlabeled traffic allowed by default
[    0.792096] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.792104] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.796089] AppArmor: AppArmor Filesystem Enabled
[    0.800012] Switched to high resolution mode on CPU 0
[    0.800595] Switched to high resolution mode on CPU 1
[    0.804016] pnp: PnP ACPI init
[    0.804030] ACPI: bus type pnp registered
[    0.809046] pnp: PnP ACPI: found 15 devices
[    0.809049] ACPI: ACPI bus type pnp unregistered
[    0.809055] PnPBIOS: Disabled by ACPI PNP
[    0.809070] system 00:01: iomem range 0xfed10000-0xfed19fff has been reserved
[    0.809084] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.809089] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.809092] system 00:08: ioport range 0x400-0x41f has been reserved
[    0.809096] system 00:08: ioport range 0x500-0x57f has been reserved
[    0.809101] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.809105] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.809109] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
[    0.809114] system 00:08: iomem range 0xfed90000-0xfed90fff has been reserved
[    0.809118] system 00:08: iomem range 0xfed91000-0xfed91fff has been reserved
[    0.809122] system 00:08: iomem range 0xfed92000-0xfed92fff has been reserved
[    0.809126] system 00:08: iomem range 0xfed93000-0xfed93fff has been reserved
[    0.809131] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.809135] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved
[    0.809145] system 00:0a: iomem range 0xffa00000-0xffbfffff could not be reserved
[    0.809149] system 00:0a: iomem range 0xffe00000-0xffffffff could not be reserved
[    0.809158] system 00:0b: iomem range 0xffc00000-0xffdfffff has been reserved
[    0.809167] system 00:0c: ioport range 0x250-0x253 has been reserved
[    0.809170] system 00:0c: ioport range 0x256-0x25f has been reserved
[    0.809174] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.809179] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.809183] system 00:0c: iomem range 0xfec10000-0xfec17fff has been reserved
[    0.809187] system 00:0c: iomem range 0xfec18000-0xfec1ffff has been reserved
[    0.809191] system 00:0c: iomem range 0xfec20000-0xfec27fff has been reserved
[    0.809195] system 00:0c: iomem range 0xfec28000-0xfec2ffff has been reserved
[    0.809199] system 00:0c: iomem range 0xfec38000-0xfec3ffff has been reserved
[    0.809207] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.809216] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.809220] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[    0.809224] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.809228] system 00:0e: iomem range 0x100000-0xbddfffff could not be reserved
[    0.844063] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.844066] pci 0000:00:1c.0:   IO window: disabled
[    0.844075] pci 0000:00:1c.0:   MEM window: disabled
[    0.844081] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.844092] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.844095] pci 0000:00:1c.1:   IO window: disabled
[    0.844103] pci 0000:00:1c.1:   MEM window: 0xfdf00000-0xfdffffff
[    0.844110] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.844120] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.844125] pci 0000:00:1c.2:   IO window: 0xd000-0xdfff
[    0.844133] pci 0000:00:1c.2:   MEM window: 0xfe000000-0xfeafffff
[    0.844141] pci 0000:00:1c.2:   PREFETCH window: 0x000000fa000000-0x000000fcffffff
[    0.844151] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.844154] pci 0000:00:1c.3:   IO window: disabled
[    0.844162] pci 0000:00:1c.3:   MEM window: disabled
[    0.844168] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.844179] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:06
[    0.844184] pci 0000:00:1c.5:   IO window: 0xe000-0xefff
[    0.844192] pci 0000:00:1c.5:   MEM window: 0xfeb00000-0xfebfffff
[    0.844199] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.844209] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
[    0.844212] pci 0000:00:1e.0:   IO window: disabled
[    0.844220] pci 0000:00:1e.0:   MEM window: disabled
[    0.844226] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.844251] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.844259] pci 0000:00:1c.0: setting latency timer to 64
[    0.844273] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.844279] pci 0000:00:1c.1: setting latency timer to 64
[    0.844293] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.844300] pci 0000:00:1c.2: setting latency timer to 64
[    0.844313] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.844320] pci 0000:00:1c.3: setting latency timer to 64
[    0.844332] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.844339] pci 0000:00:1c.5: setting latency timer to 64
[    0.844350] pci 0000:00:1e.0: setting latency timer to 64
[    0.844357] bus: 00 index 0 io port: [0x00-0xffff]
[    0.844360] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.844364] bus: 01 index 0 mmio: [0x0-0x0]
[    0.844367] bus: 01 index 1 mmio: [0x0-0x0]
[    0.844369] bus: 01 index 2 mmio: [0x0-0x0]
[    0.844372] bus: 01 index 3 mmio: [0x0-0x0]
[    0.844375] bus: 02 index 0 mmio: [0x0-0x0]
[    0.844378] bus: 02 index 1 mmio: [0xfdf00000-0xfdffffff]
[    0.844381] bus: 02 index 2 mmio: [0x0-0x0]
[    0.844384] bus: 02 index 3 mmio: [0x0-0x0]
[    0.844387] bus: 03 index 0 io port: [0xd000-0xdfff]
[    0.844390] bus: 03 index 1 mmio: [0xfe000000-0xfeafffff]
[    0.844393] bus: 03 index 2 mmio: [0xfa000000-0xfcffffff]
[    0.844396] bus: 03 index 3 mmio: [0x0-0x0]
[    0.844399] bus: 05 index 0 mmio: [0x0-0x0]
[    0.844401] bus: 05 index 1 mmio: [0x0-0x0]
[    0.844404] bus: 05 index 2 mmio: [0x0-0x0]
[    0.844407] bus: 05 index 3 mmio: [0x0-0x0]
[    0.844410] bus: 06 index 0 io port: [0xe000-0xefff]
[    0.844413] bus: 06 index 1 mmio: [0xfeb00000-0xfebfffff]
[    0.844416] bus: 06 index 2 mmio: [0x0-0x0]
[    0.844418] bus: 06 index 3 mmio: [0x0-0x0]
[    0.844421] bus: 07 index 0 mmio: [0x0-0x0]
[    0.844424] bus: 07 index 1 mmio: [0x0-0x0]
[    0.844426] bus: 07 index 2 mmio: [0x0-0x0]
[    0.844429] bus: 07 index 3 io port: [0x00-0xffff]
[    0.844432] bus: 07 index 4 mmio: [0x000000-0xffffffff]
[    0.844444] NET: Registered protocol family 2
[    0.856079] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.856424] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.856875] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.857170] TCP: Hash tables configured (established 131072 bind 65536)
[    0.857174] TCP reno registered
[    0.864128] NET: Registered protocol family 1
[    0.864295] checking if image is initramfs... it is
[    1.872465] Freeing initrd memory: 7389k freed
[    1.872507] Simple Boot Flag at 0x51 set to 0x1
[    1.872719] cpufreq: No nForce2 chipset.
[    1.872907] audit: initializing netlink socket (disabled)
[    1.872934] type=2000 audit(1254586128.872:1): initialized
[    1.885042] highmem bounce pool size: 64 pages
[    1.885050] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.887070] VFS: Disk quotas dquot_6.5.1
[    1.887159] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.888070] fuse init (API version 7.10)
[    1.888206] msgmni has been set to 1673
[    1.888444] alg: No test for stdrng (krng)
[    1.888460] io scheduler noop registered
[    1.888463] io scheduler anticipatory registered
[    1.888466] io scheduler deadline registered
[    1.888487] io scheduler cfq registered (default)
[    1.888502] pci 0000:00:02.0: Boot video device
[    1.894650] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.894713] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.894759] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    1.894780] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.894802] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.894898] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.894958] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.895000] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X
[    1.895021] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.895039] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.895134] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.895196] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.895238] pcieport-driver 0000:00:1c.2: irq 2301 for MSI/MSI-X
[    1.895259] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.895277] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.895296] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.895394] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.895454] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.895496] pcieport-driver 0000:00:1c.3: irq 2300 for MSI/MSI-X
[    1.895517] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.895535] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.895630] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.895692] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.895734] pcieport-driver 0000:00:1c.5: irq 2299 for MSI/MSI-X
[    1.895755] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.895774] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.895792] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.895899] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.896611] pciehp 0000:00:1c.2:pcie02: HPC vendor_id 8086 device_id 2944 ss_vid 0 ss_did 0
[    1.896669] pciehp 0000:00:1c.2:pcie02: service driver pciehp loaded
[    1.897348] pciehp 0000:00:1c.5:pcie02: HPC vendor_id 8086 device_id 294a ss_vid 0 ss_did 0
[    1.897400] pciehp 0000:00:1c.5:pcie02: service driver pciehp loaded
[    1.897413] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.897713] ACPI: AC Adapter [AC0] (off-line)
[    1.955267] ACPI: Battery Slot [BAT0] (battery present)
[    1.955372] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.955377] ACPI: Power Button (FF) [PWRF]
[    1.955464] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.955476] ACPI: Sleep Button (CM) [SLPB]
[    1.955543] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.965051] ACPI: Lid Switch [LID]
[    1.966131] ACPI: SSDT BDD993F0, 0206 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[    1.967004] ACPI: SSDT BDD99690, 0765 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    1.968320] Monitor-Mwait will be used to enter C-1 state
[    1.968325] Monitor-Mwait will be used to enter C-2 state
[    1.968330] Monitor-Mwait will be used to enter C-3 state
[    1.968351] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.968388] processor ACPI_CPU:00: registered as cooling_device0
[    1.968394] ACPI: Processor [P001] (supports 8 throttling states)
[    1.968905] ACPI: SSDT BDD99320, 00CC (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
[    1.969718] ACPI: SSDT BDD99600, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
[    1.971252] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.971282] processor ACPI_CPU:01: registered as cooling_device1
[    1.971288] ACPI: Processor [P002] (supports 8 throttling states)
[    1.984790] thermal LNXTHERM:01: registered as thermal_zone0
[    1.986673] ACPI: Thermal Zone [THRM] (36 C)
[    1.986755] isapnp: Scanning for PnP cards...
[    2.341123] isapnp: No Plug & Play device found
[    2.349349] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.351033] brd: module loaded
[    2.351482] loop: module loaded
[    2.351576] Fixed MDIO Bus: probed
[    2.351584] PPP generic driver version 2.4.2
[    2.351668] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.351712] Driver 'sd' needs updating - please use bus_type methods
[    2.351726] Driver 'sr' needs updating - please use bus_type methods
[    2.351791] ahci 0000:00:1f.2: version 3.0
[    2.351807] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.351863] ahci 0000:00:1f.2: irq 2298 for MSI/MSI-X
[    2.351963] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x23 impl SATA mode
[    2.351968] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems 
[    2.351975] ahci 0000:00:1f.2: setting latency timer to 64
[    2.352254] scsi0 : ahci
[    2.352392] scsi1 : ahci
[    2.352473] scsi2 : ahci
[    2.352560] scsi3 : ahci
[    2.352642] scsi4 : ahci
[    2.352732] scsi5 : ahci
[    2.353083] ata1: SATA max UDMA/133 abar m2048@0xfdefb000 port 0xfdefb100 irq 2298
[    2.353089] ata2: SATA max UDMA/133 abar m2048@0xfdefb000 port 0xfdefb180 irq 2298
[    2.353092] ata3: DUMMY
[    2.353094] ata4: DUMMY
[    2.353096] ata5: DUMMY
[    2.353100] ata6: SATA max UDMA/133 abar m2048@0xfdefb000 port 0xfdefb380 irq 2298
[    2.672028] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.673868] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    2.674063] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    2.674068] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.728852] ata1.00: ATA-8: ST9320325AS, 0002SDM1, max UDMA/133
[    2.728856] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.731611] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    2.731915] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    2.731920] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.733764] ata1.00: configured for UDMA/133
[    3.472027] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.474812] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    3.474817] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    3.476721] ata2.00: ATAPI: HL-DT-STDVDRAM GT10N, 1.00, max UDMA/100
[    3.480832] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    3.480836] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    3.482868] ata2.00: configured for UDMA/100
[    3.816024] ata6: SATA link down (SStatus 0 SControl 300)
[    3.832156] scsi 0:0:0:0: Direct-Access     ATA      ST9320325AS      0002 PQ: 0 ANSI: 5
[    3.832293] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.832318] sd 0:0:0:0: [sda] Write Protect is off
[    3.832322] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.832360] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.832456] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.832478] sd 0:0:0:0: [sda] Write Protect is off
[    3.832482] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.832520] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.832525]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    3.925311] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.925380] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.940770] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT10N     1.00 PQ: 0 ANSI: 5
[    3.948422] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.948427] Uniform CD-ROM driver Revision: 3.20
[    3.948563] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.948620] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.949638] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.949667] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.949693] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.949698] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.949784] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.953693] ehci_hcd 0000:00:1a.7: debug port 1
[    3.953703] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.953724] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdefbc00
[    3.968022] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.968110] usb usb1: configuration #1 chosen from 1 choice
[    3.968153] hub 1-0:1.0: USB hub found
[    3.968163] hub 1-0:1.0: 6 ports detected
[    3.968314] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.968330] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.968335] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.968395] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.972310] ehci_hcd 0000:00:1d.7: debug port 1
[    3.972319] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.972339] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdefb800
[    3.988014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.988095] usb usb2: configuration #1 chosen from 1 choice
[    3.988135] hub 2-0:1.0: USB hub found
[    3.988143] hub 2-0:1.0: 6 ports detected
[    3.988279] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.988304] uhci_hcd: USB Universal Host Controller Interface driver
[    3.988336] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.988346] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.988351] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.988413] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.988457] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c880
[    3.988572] usb usb3: configuration #1 chosen from 1 choice
[    3.988612] hub 3-0:1.0: USB hub found
[    3.988621] hub 3-0:1.0: 2 ports detected
[    3.988740] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.988749] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.988754] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.988814] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.988853] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000c800
[    3.988963] usb usb4: configuration #1 chosen from 1 choice
[    3.989002] hub 4-0:1.0: USB hub found
[    3.989010] hub 4-0:1.0: 2 ports detected
[    3.989124] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.989133] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    3.989138] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    3.989205] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    3.989245] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000c480
[    3.989346] usb usb5: configuration #1 chosen from 1 choice
[    3.989382] hub 5-0:1.0: USB hub found
[    3.989390] hub 5-0:1.0: 2 ports detected
[    3.989512] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.989520] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.989525] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.989585] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    3.989614] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c400
[    3.989711] usb usb6: configuration #1 chosen from 1 choice
[    3.989752] hub 6-0:1.0: USB hub found
[    3.989760] hub 6-0:1.0: 2 ports detected
[    3.989875] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.989883] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.989888] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.989948] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    3.989977] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c080
[    3.990080] usb usb7: configuration #1 chosen from 1 choice
[    3.990116] hub 7-0:1.0: USB hub found
[    3.990125] hub 7-0:1.0: 2 ports detected
[    3.990244] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.990253] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.990258] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.990318] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    3.990347] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c000
[    3.990446] usb usb8: configuration #1 chosen from 1 choice
[    3.990485] hub 8-0:1.0: USB hub found
[    3.990497] hub 8-0:1.0: 2 ports detected
[    3.990707] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    3.995757] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.997430] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.997439] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.997443] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.997447] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.997450] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    4.000066] mice: PS/2 mouse device common for all mice
[    4.016105] rtc_cmos 00:03: RTC can wake from S4
[    4.016153] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.016190] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    4.016289] device-mapper: uevent: version 1.0.3
[    4.016423] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.016520] device-mapper: multipath: version 1.0.5 loaded
[    4.016524] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.016638] EISA: Probing bus 0 at eisa.0
[    4.016685] EISA: Detected 0 cards.
[    4.016855] cpuidle: using governor ladder
[    4.017034] cpuidle: using governor menu
[    4.017803] TCP cubic registered
[    4.017952] NET: Registered protocol family 10
[    4.018578] lo: Disabled Privacy Extensions
[    4.019081] NET: Registered protocol family 17
[    4.019120] Bluetooth: L2CAP ver 2.11
[    4.019122] Bluetooth: L2CAP socket layer initialized
[    4.019126] Bluetooth: SCO (Voice Link) ver 0.6
[    4.019129] Bluetooth: SCO socket layer initialized
[    4.019172] Marking TSC unstable due to TSC halts in idle
[    4.019176] Bluetooth: RFCOMM socket layer initialized
[    4.019185] Bluetooth: RFCOMM TTY layer initialized
[    4.019188] Bluetooth: RFCOMM ver 1.10
[    4.020316] Using IPI No-Shortcut mode
[    4.020385] registered taskstats version 1
[    4.020488]   Magic number: 13:11:135
[    4.020509] block ram0: hash matches
[    4.020582] rtc_cmos 00:03: setting system clock to 2009-10-03 16:08:52 UTC (1254586132)
[    4.020585] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.020587] EDD information not available.
[    4.020808] Freeing unused kernel memory: 532k freed
[    4.020950] Write protecting the kernel text: 4120k
[    4.021019] Write protecting the kernel read-only data: 1524k
[    4.052848] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    4.289904] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    4.343120] ATL1E 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.343134] ATL1E 0000:06:00.0: setting latency timer to 64
[    4.465387] usb 1-3: configuration #1 chosen from 1 choice
[    4.930461] PM: Starting manual resume from disk
[    4.930465] PM: Resume from partition 8:5
[    4.930466] PM: Checking hibernation image.
[    4.930777] PM: Resume from disk failed.
[    4.965197] kjournald starting.  Commit interval 5 seconds
[    4.965210] EXT3-fs: mounted filesystem with ordered data mode.
[    5.000046] Clocksource tsc unstable (delta = -384366222 ns)
[   10.039397] udev: starting version 141
[   10.245617] Linux agpgart interface v0.103
[   10.261397] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[   10.261969] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[   10.265565] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   10.331271] asus-laptop: Asus Laptop Support version 0.42
[   10.336631] asus-laptop:   K50IJ model detected
[   10.337811] asus-laptop: Brightness ignored, must be controlled by ACPI video driver
[   10.343654] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   10.396425] cfg80211: Calling CRDA to update world regulatory domain
[   10.424522] iTCO_vendor_support: vendor-support=0
[   10.427301] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   10.427491] iTCO_wdt: Found a ICH9M TCO device (Version=2, TCOBASE=0x0860)
[   10.427576] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   10.451464] Linux video capture interface: v2.00
[   10.478393] acpi device:1c: registered as cooling_device2
[   10.478637] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19/input/input6
[   10.481963] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   10.498871] cfg80211: World regulatory domain updated:
[   10.498874]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.498877]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.498879]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.498882]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.498884]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.498886]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.623146] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   10.631461] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
[   10.633152] input: CNF7129 as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input7
[   10.635124] usbcore: registered new interface driver uvcvideo
[   10.635153] USB Video Class driver (v0.1.0)
[   10.721546] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.721559] ath9k 0000:02:00.0: setting latency timer to 64
[   10.927406] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   10.928080] Registered led device: ath9k-phy0::radio
[   10.928096] Registered led device: ath9k-phy0::assoc
[   10.928110] Registered led device: ath9k-phy0::tx
[   10.928127] Registered led device: ath9k-phy0::rx
[   10.928145] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf81e0000, irq=17
[   11.074653] psmouse serio4: ID: 10 00 64<6>lp: driver loaded but no devices found
[   11.338199] Adding 995988k swap on /dev/sda5.  Priority:-1 extents:1 across:995988k
[   11.362159] EXT3 FS on sda6, internal journal
[   11.707008] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio4/input/input8
[   11.856451] type=1505 audit(1254600540.332:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2019
[   11.900513] type=1505 audit(1254600540.376:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2023
[   11.900635] type=1505 audit(1254600540.376:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2023
[   11.900678] type=1505 audit(1254600540.376:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2023
[   11.900715] type=1505 audit(1254600540.376:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2023
[   12.023639] type=1505 audit(1254600540.500:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2028
[   12.023820] type=1505 audit(1254600540.500:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2028
[   12.050354] type=1505 audit(1254600540.528:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2032
[   13.578507] oss_hdaudio 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.582858] oss_hdaudio: HDA codec 0x11060397 not known yet
[   13.672357] oss_hdaudio: HDA codec 0x11060397 not known yet
[   13.717258] usbcore: registered new interface driver oss_usb
[   15.725934] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.725937] Bluetooth: BNEP filters: protocol multicast
[   15.749135] Bridge firewalling registered
[   17.009043] ppdev: user-space parallel port driver
[   18.621618] [drm] Initialized drm 1.1.0 20060810
[   18.636701] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.636706] pci 0000:00:02.0: setting latency timer to 64
[   18.636914] pci 0000:00:02.0: irq 2297 for MSI/MSI-X
[   18.636993] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   18.638576] [drm:i915_setparam] *ERROR* unknown parameter 4
[   21.521891] ATL1E 0000:06:00.0: irq 2296 for MSI/MSI-X
[   21.522226] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.545096] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.993829] wlan0: direct probe to AP f62906b8 try 1
[   23.192044] wlan0: direct probe to AP f62906b8 try 2
[   23.393133] wlan0: direct probe to AP f62906b8 try 3
[   23.593095] wlan0: direct probe to AP f62906b8 timed out
[   87.375161] wlan0: authenticate with AP f62906b8
[   87.377193] wlan0: authenticated
[   87.377196] wlan0: associate with AP f62906b8
[   87.381686] wlan0: RX AssocResp from f5d9a02a (capab=0x431 status=0 aid=1)
[   87.381689] wlan0: associated
[   87.382232] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   87.427183] cfg80211: Calling CRDA for country: US
[   87.430499] cfg80211: Current regulatory domain updated by AP to: US
[   87.430503]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   87.430505]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   97.624090] wlan0: no IPv6 routers present
[  786.972126] usb 2-2: new high speed USB device using ehci_hcd and address 2
[  787.105391] usb 2-2: configuration #1 chosen from 1 choice
[  787.171564] Initializing USB Mass Storage driver...
[  787.171789] scsi6 : SCSI emulation for USB Mass Storage devices
[  787.171927] usb-storage: device found at 2
[  787.171931] usb-storage: waiting for device to settle before scanning
[  787.171944] usbcore: registered new interface driver usb-storage
[  787.171949] USB Mass Storage support registered.
[  792.168251] usb-storage: device scan complete
[  792.168786] scsi 6:0:0:0: Direct-Access     ChipBank SD/MM Reader     4080 PQ: 0 ANSI: 2
[  792.189212] sd 6:0:0:0: [sdb] 3862528 512-byte hardware sectors: (1.97 GB/1.84 GiB)
[  792.192336] sd 6:0:0:0: [sdb] Write Protect is off
[  792.192341] sd 6:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[  792.192345] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  792.194115] sd 6:0:0:0: [sdb] 3862528 512-byte hardware sectors: (1.97 GB/1.84 GiB)
[  792.194962] sd 6:0:0:0: [sdb] Write Protect is off
[  792.194968] sd 6:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[  792.194972] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  792.194980]  sdb: sdb1
[  792.197818] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  792.197918] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 4249.181071] CE: hpet increasing min_delta_ns to 15000 nsec
[ 4273.067406] snd: Unknown symbol unregister_sound_special
[ 4273.067896] snd: Unknown symbol register_sound_special_device
[ 4273.069183] snd: Unknown symbol sound_class
[ 4273.070365] snd_hwdep: Unknown symbol snd_hidden_kzalloc
[ 4273.070501] snd_hwdep: Unknown symbol snd_info_register
[ 4273.070670] snd_hwdep: Unknown symbol snd_info_create_module_entry
[ 4273.070805] snd_hwdep: Unknown symbol snd_info_free_entry
[ 4273.070947] snd_hwdep: Unknown symbol snd_hidden_kfree
[ 4273.071078] snd_hwdep: Unknown symbol snd_unregister_oss_device
[ 4273.071224] snd_hwdep: Unknown symbol snd_verbose_printk
[ 4273.071355] snd_hwdep: Unknown symbol snd_register_oss_device
[ 4273.071492] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[ 4273.071624] snd_hwdep: Unknown symbol snd_card_file_add
[ 4273.071768] snd_hwdep: Unknown symbol snd_iprintf
[ 4273.071899] snd_hwdep: Unknown symbol snd_major
[ 4273.072149] snd_hwdep: Unknown symbol snd_unregister_device
[ 4273.072292] snd_hwdep: Unknown symbol snd_device_new
[ 4273.072429] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[ 4273.072596] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[ 4273.072738] snd_hwdep: Unknown symbol snd_lookup_minor_data
[ 4273.072878] snd_hwdep: Unknown symbol snd_card_file_remove
[ 4273.073009] snd_hwdep: Unknown symbol snd_register_device_for_dev
[ 4313.202842] snd: Unknown symbol unregister_sound_special
[ 4313.203331] snd: Unknown symbol register_sound_special_device
[ 4313.204609] snd: Unknown symbol sound_class
[ 4313.205978] snd_hwdep: Unknown symbol snd_hidden_kzalloc
[ 4313.206112] snd_hwdep: Unknown symbol snd_info_register
[ 4313.206280] snd_hwdep: Unknown symbol snd_info_create_module_entry
[ 4313.206414] snd_hwdep: Unknown symbol snd_info_free_entry
[ 4313.206566] snd_hwdep: Unknown symbol snd_hidden_kfree
[ 4313.206698] snd_hwdep: Unknown symbol snd_unregister_oss_device
[ 4313.206843] snd_hwdep: Unknown symbol snd_verbose_printk
[ 4313.206975] snd_hwdep: Unknown symbol snd_register_oss_device
[ 4313.207112] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[ 4313.207244] snd_hwdep: Unknown symbol snd_card_file_add
[ 4313.207387] snd_hwdep: Unknown symbol snd_iprintf
[ 4313.207518] snd_hwdep: Unknown symbol snd_major
[ 4313.207730] snd_hwdep: Unknown symbol snd_unregister_device
[ 4313.207871] snd_hwdep: Unknown symbol snd_device_new
[ 4313.208029] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[ 4313.208198] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[ 4313.208340] snd_hwdep: Unknown symbol snd_lookup_minor_data
[ 4313.208481] snd_hwdep: Unknown symbol snd_card_file_remove
[ 4313.208613] snd_hwdep: Unknown symbol snd_register_device_for_dev
[ 6112.817863] snd: Unknown symbol unregister_sound_special
[ 6112.818366] snd: Unknown symbol register_sound_special_device
[ 6112.819649] snd: Unknown symbol sound_class
[ 6112.824437] snd_hwdep: Unknown symbol snd_hidden_kzalloc
[ 6112.824574] snd_hwdep: Unknown symbol snd_info_register
[ 6112.824747] snd_hwdep: Unknown symbol snd_info_create_module_entry
[ 6112.824880] snd_hwdep: Unknown symbol snd_info_free_entry
[ 6112.825022] snd_hwdep: Unknown symbol snd_hidden_kfree
[ 6112.825155] snd_hwdep: Unknown symbol snd_unregister_oss_device
[ 6112.825305] snd_hwdep: Unknown symbol snd_verbose_printk
[ 6112.825438] snd_hwdep: Unknown symbol snd_register_oss_device
[ 6112.825577] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[ 6112.825711] snd_hwdep: Unknown symbol snd_card_file_add
[ 6112.825857] snd_hwdep: Unknown symbol snd_iprintf
[ 6112.825990] snd_hwdep: Unknown symbol snd_major
[ 6112.826202] snd_hwdep: Unknown symbol snd_unregister_device
[ 6112.826347] snd_hwdep: Unknown symbol snd_device_new
[ 6112.826484] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[ 6112.826655] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[ 6112.826799] snd_hwdep: Unknown symbol snd_lookup_minor_data
[ 6112.826948] snd_hwdep: Unknown symbol snd_card_file_remove
[ 6112.827084] snd_hwdep: Unknown symbol snd_register_device_for_dev
[ 6200.899135] ACPI: BIOS _OSI(Linux) query ignored
[ 6200.899701] ACPI: BIOS _OSI(Linux) query ignored
[17773.090648] ACPI: BIOS _OSI(Linux) query ignored
[17773.091239] ACPI: BIOS _OSI(Linux) query ignored
[18781.480138] wlan0: no probe response from AP f62906b8 - disassociating
[18782.360925] wlan0: authenticate with AP f62906b8
[18782.362837] wlan0: authenticated
[18782.362841] wlan0: associate with AP f62906b8
[18782.365726] wlan0: RX ReassocResp from f4b0402a (capab=0x431 status=0 aid=1)
[18782.365730] wlan0: associated
[18872.281753] wlan0: deauthenticated (Reason: 7)
[18873.280097] wlan0: direct probe to AP f62906b8 try 1
[18873.282130] wlan0 direct probe responded
[18873.282134] wlan0: authenticate with AP f62906b8
[18873.284252] wlan0: authenticated
[18873.284256] wlan0: associate with AP f62906b8
[18873.286885] wlan0: RX ReassocResp from f5edc02a (capab=0x431 status=0 aid=1)
[18873.286889] wlan0: associated
[18963.259048] snd: Unknown symbol unregister_sound_special
[18963.259424] snd: Unknown symbol register_sound_special_device
[18963.260191] snd: Unknown symbol sound_class
[18963.261279] snd_hwdep: Unknown symbol snd_hidden_kzalloc
[18963.261361] snd_hwdep: Unknown symbol snd_info_register
[18963.261465] snd_hwdep: Unknown symbol snd_info_create_module_entry
[18963.261568] snd_hwdep: Unknown symbol snd_info_free_entry
[18963.261657] snd_hwdep: Unknown symbol snd_hidden_kfree
[18963.261738] snd_hwdep: Unknown symbol snd_unregister_oss_device
[18963.261827] snd_hwdep: Unknown symbol snd_verbose_printk
[18963.261910] snd_hwdep: Unknown symbol snd_register_oss_device
[18963.261993] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[18963.262074] snd_hwdep: Unknown symbol snd_card_file_add
[18963.262162] snd_hwdep: Unknown symbol snd_iprintf
[18963.262242] snd_hwdep: Unknown symbol snd_major
[18963.262372] snd_hwdep: Unknown symbol snd_unregister_device
[18963.262460] snd_hwdep: Unknown symbol snd_device_new
[18963.262543] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[18963.262644] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[18963.262730] snd_hwdep: Unknown symbol snd_lookup_minor_data
[18963.262815] snd_hwdep: Unknown symbol snd_card_file_remove
[18963.262895] snd_hwdep: Unknown symbol snd_register_device_for_dev
[19592.273681] wlan0: deauthenticated (Reason: 7)
[19594.272098] wlan0: direct probe to AP f62906b8 try 1
[19594.274104] wlan0 direct probe responded
[19594.274108] wlan0: authenticate with AP f62906b8
[19594.276214] wlan0: authenticated
[19594.276219] wlan0: associate with AP f62906b8
[19594.278833] wlan0: RX ReassocResp from f05ea02a (capab=0x431 status=0 aid=1)
[19594.278837] wlan0: associated
```

---

