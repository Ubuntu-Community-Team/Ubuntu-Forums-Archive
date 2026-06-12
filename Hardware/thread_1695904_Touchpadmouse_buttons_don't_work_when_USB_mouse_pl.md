---
title: "Touchpad/mouse buttons don't work when USB mouse plugged in"
date: 2011-02-26
forum: Hardware
---

### Post by iki23 on 2011-02-26
Hi all,

the laptop is old Toshiba Staellite (A50?) with Xubuntu Maverick.
Also dmesg is reporting pnp 00:08 disabling due to overlaps with pci 0000:00:1d.0-2 (USB ports) and 0000:00:1f.5-6 (audio, modem).

Any ideas what does it mean?

iki23

```

k@satellite:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)

```

```

k@satellite:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-25-generic (buildd@palmer) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 (Ubuntu 2.6.35-25.44-generic 2.6.35.10)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
[    0.000000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ef40000 (usable)
[    0.000000]  BIOS-e820: 000000001ef40000 - 000000001ef50000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ef50000 - 000000001f000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x1ef40 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-back
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FEDA0000 mask FFFFE0000 write-back
[    0.000000]   1 base 01F000000 mask FFF000000 uncachable
[    0.000000]   2 base 0FFF80000 mask FFFF80000 write-protect
[    0.000000]   3 base 000000000 mask FE0000000 write-back
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 00000000000eee00 (reserved)
[    0.000000]  modified: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[    0.000000]  modified: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001ef40000 (usable)
[    0.000000]  modified: 000000001ef40000 - 000000001ef50000 (ACPI data)
[    0.000000]  modified: 000000001ef50000 - 000000001f000000 (reserved)
[    0.000000]  modified: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  modified: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001ef40000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001ec00000 page 2M
[    0.000000]  001ec00000 - 001ef40000 page 4k
[    0.000000] kernel direct mapping tables up to 1ef40000 @ 15000-1a000
[    0.000000] RAMDISK: 1696c000 - 173b0000
[    0.000000] ACPI: RSDP 000f0180 00014 (v00 TOSHIB)
[    0.000000] ACPI: RSDT 1ef40000 00038 (v01 TOSHIB 750      00970814 TASM 04010000)
[    0.000000] ACPI: FACP 1ef40060 00084 (v02 TOSHIB 750      20030101 TASM 04010000)
[    0.000000] ACPI: DSDT 1ef40118 044B9 (v01 TOSHIB A0015    20040426 MSFT 0100000E)
[    0.000000] ACPI: FACS 000eee00 00040
[    0.000000] ACPI: SSDT 1ef445d1 00231 (v01 TOSHIB LNK10SS  20040226 MSFT 0100000E)
[    0.000000] ACPI: DBGP 1ef400e4 00034 (v01 TOSHIB 750      00970814 TASM 04010000)
[    0.000000] ACPI: BOOT 1ef40038 00028 (v01 TOSHIB 750      00970814 TASM 04010000)
[    0.000000] ACPI: SSDT 1ef44802 006C4 (v01 TOSHIB A0015    20040226 MSFT 0100000E)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 495MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1ef40000
[    0.000000]   low ram: 0 - 1ef40000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001ef40
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001ef40
[    0.000000] On node 0 totalpages: 126672
[    0.000000] free_area_init_node: node 0, pgdat c07fffc0, node_mem_map c1001020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 959 pages used for memmap
[    0.000000]   Normal zone: 121729 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0xd808
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] APIC: switched to apic NOOP
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000ee000
[    0.000000] PM: Registered nosave memory: 00000000000ee000 - 00000000000ef000
[    0.000000] PM: Registered nosave memory: 00000000000ef000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 1f000000 (gap: 1f000000:dfc10000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1400000 s36416 r0 d20928 u4194304
[    0.000000] pcpu-alloc: s36416 r0 d20928 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 125681
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=7902b5b8-0051-4118-b03d-209b9d990f40 ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2535660 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (43 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a2adc]   TEXT DATA BSS
[    0.000000]   #3 [001696c000 - 00173b0000]         RAMDISK
[    0.000000]   #4 [000009fc00 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00009a3000 - 00009a61e4]             BRK
[    0.000000]   #6 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #7 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #8 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #9 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #10 [0001001000 - 00013e1000]         BOOTMEM
[    0.000000]   #11 [00013e1000 - 00013e1004]         BOOTMEM
[    0.000000]   #12 [00013e1040 - 00013e1100]         BOOTMEM
[    0.000000]   #13 [00013e1100 - 00013e1130]         BOOTMEM
[    0.000000]   #14 [00013e1140 - 00013e2940]         BOOTMEM
[    0.000000]   #15 [00013e2940 - 00013e2ae4]         BOOTMEM
[    0.000000]   #16 [00013e2b00 - 00013e2b40]         BOOTMEM
[    0.000000]   #17 [00013e2b40 - 00013e2b80]         BOOTMEM
[    0.000000]   #18 [00013e2b80 - 00013e2bc0]         BOOTMEM
[    0.000000]   #19 [00013e2bc0 - 00013e2c00]         BOOTMEM
[    0.000000]   #20 [00013e2c00 - 00013e2c40]         BOOTMEM
[    0.000000]   #21 [00013e2c40 - 00013e2c80]         BOOTMEM
[    0.000000]   #22 [00013e2c80 - 00013e2cc0]         BOOTMEM
[    0.000000]   #23 [00013e2cc0 - 00013e2d00]         BOOTMEM
[    0.000000]   #24 [00013e2d00 - 00013e2d40]         BOOTMEM
[    0.000000]   #25 [00013e2d40 - 00013e2d80]         BOOTMEM
[    0.000000]   #26 [00013e2d80 - 00013e2dc0]         BOOTMEM
[    0.000000]   #27 [00013e2dc0 - 00013e2e00]         BOOTMEM
[    0.000000]   #28 [00013e2e00 - 00013e2e10]         BOOTMEM
[    0.000000]   #29 [00013e2e40 - 00013e2e50]         BOOTMEM
[    0.000000]   #30 [00013e2e80 - 00013e2eea]         BOOTMEM
[    0.000000]   #31 [00013e2f00 - 00013e2f6a]         BOOTMEM
[    0.000000]   #32 [0001400000 - 000140e000]         BOOTMEM
[    0.000000]   #33 [00013e4f80 - 00013e4f84]         BOOTMEM
[    0.000000]   #34 [00013e4fc0 - 00013e4fc4]         BOOTMEM
[    0.000000]   #35 [00013e5000 - 00013e5004]         BOOTMEM
[    0.000000]   #36 [00013e5040 - 00013e5044]         BOOTMEM
[    0.000000]   #37 [00013e5080 - 00013e5130]         BOOTMEM
[    0.000000]   #38 [00013e5140 - 00013e51e8]         BOOTMEM
[    0.000000]   #39 [00013e2f80 - 00013e4f80]         BOOTMEM
[    0.000000]   #40 [000140e000 - 000144e000]         BOOTMEM
[    0.000000]   #41 [000144e000 - 000146e000]         BOOTMEM
[    0.000000]   #42 [000146e000 - 00016d90ec]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 480376k/507136k available (4933k kernel code, 26312k reserved, 2331k data, 688k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xdf740000 - 0xff7fe000   ( 512 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdef40000   ( 495 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c5000   ( 688 kB)
[    0.000000]       .data : 0xc05d17ce - 0xc08187a8   (2331 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d17ce   (4933 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]  RCU-based detection of stalled CPUs is disabled.
[    0.000000]  Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.125 MHz processor.
[    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.25 BogoMIPS (lpj=6384500)
[    0.008012] pid_max: default: 32768 minimum: 301
[    0.008034] Security Framework initialized
[    0.008062] AppArmor: AppArmor initialized
[    0.008065] Yama: becoming mindful.
[    0.008142] Mount-cache hash table entries: 512
[    0.012079] Initializing cgroup subsys ns
[    0.012085] Initializing cgroup subsys cpuacct
[    0.012091] Initializing cgroup subsys memory
[    0.012103] Initializing cgroup subsys devices
[    0.012106] Initializing cgroup subsys freezer
[    0.012110] Initializing cgroup subsys net_cls
[    0.012148] mce: CPU supports 5 MCE banks
[    0.012165] Performance Events:
[    0.012168] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.012171] no hardware sampling interrupt available.
[    0.012174] p6 PMU driver.
[    0.012193] ... version:                0
[    0.012195] ... bit width:              32
[    0.012198] ... generic registers:      2
[    0.012200] ... value mask:             00000000ffffffff
[    0.012203] ... max period:             000000007fffffff
[    0.012206] ... fixed-purpose events:   0
[    0.012209] ... event mask:             0000000000000003
[    0.013346] SMP alternatives: switching to UP code
[    0.022072] Freeing SMP alternatives: 24k freed
[    0.022083] ACPI: Core revision 20100428
[    0.022086] TOSHIBA Satellite detected - force copy of DSDT to local memory
[    0.027261] ACPI: Forced DSDT copy: length 0x044B9 copied locally, original unmapped
[    0.031079] ACPI: setting ELCR to 0200 (from 0e00)
[    0.031516] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.031520] ftrace: allocating 21756 entries in 43 pages
[    0.032090] weird, boot CPU (#0) not listed by the BIOS.
[    0.032093] SMP motherboard not detected.
[    0.032096] Local APIC not detected. Using dummy APIC emulation.
[    0.032099] SMP disabled
[    0.032236] Brought up 1 CPUs
[    0.032239] Total of 1 processors activated (3192.25 BogoMIPS).
[    0.036210] devtmpfs: initialized
[    0.037927] regulator: core version 0.5
[    0.037949] Time: 17:36:48  Date: 02/26/11
[    0.037994] NET: Registered protocol family 16
[    0.038142] EISA bus registered
[    0.038152] ACPI: bus type pci registered
[    0.038338] PCI: PCI BIOS revision 2.10 entry at 0xfd480, last bus=3
[    0.038341] PCI: Using configuration type 1 for base access
[    0.041197] bio: create slab <bio-0> at 0
[    0.042401] ACPI: EC: Look up EC in DSDT
[    0.043866] ACPI: Actual Package length (16) is larger than NumElements field (6), truncated
[    0.043872]
[    0.046313] ACPI: Interpreter enabled
[    0.046319] ACPI: (supports S0 S3 S4 S5)
[    0.046345] ACPI: Using PIC for interrupt routing
[    0.049815] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.051832] ACPI: Power Resource [PFAN] (off)
[    0.052312] ACPI: No dock devices found.
[    0.052318] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.052384] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.052509] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.052513] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.052517] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.052521] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.052525] pci_root PNP0A03:00: host bridge window [mem 0x80100000-0xfec0ffff] (ignored)
[    0.052529] pci_root PNP0A03:00: host bridge window [mem 0xfec20000-0xfed9ffff] (ignored)
[    0.052532] pci_root PNP0A03:00: host bridge window [mem 0xfedc0000-0xffb7ffff] (ignored)
[    0.052536] pci_root PNP0A03:00: host bridge window [mem 0xffc00000-0xffefffff] (ignored)
[    0.052656] pci 0000:00:02.0: reg 10: [mem 0xd8000000-0xdfffffff pref]
[    0.052661] pci 0000:00:02.0: reg 14: [mem 0xd0000000-0xd007ffff]
[    0.052667] pci 0000:00:02.0: reg 18: [io  0xeff8-0xefff]
[    0.052687] pci 0000:00:02.0: supports D1
[    0.052704] pci 0000:00:02.1: reg 10: [mem 0x00000000-0x07ffffff pref]
[    0.052710] pci 0000:00:02.1: reg 14: [mem 0x00000000-0x0007ffff]
[    0.052733] pci 0000:00:02.1: supports D1
[    0.052802] pci 0000:00:1d.0: reg 20: [io  0xcfe0-0xcfff]
[    0.052851] pci 0000:00:1d.1: reg 20: [io  0xcf80-0xcf9f]
[    0.052899] pci 0000:00:1d.2: reg 20: [io  0xcf60-0xcf7f]
[    0.052949] pci 0000:00:1d.7: reg 10: [mem 0x00000000-0x000003ff]
[    0.053002] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.053008] pci 0000:00:1d.7: PME# disabled
[    0.053088] pci 0000:00:1f.0: quirk: [io  0xd800-0xd87f] claimed by ICH4 ACPI/GPIO/TCO
[    0.053093] pci 0000:00:1f.0: quirk: [io  0xeec0-0xeeff] claimed by ICH4 GPIO
[    0.053116] pci 0000:00:1f.1: reg 10: [io  0xbff8-0xbfff]
[    0.053123] pci 0000:00:1f.1: reg 14: [io  0xbff4-0xbff7]
[    0.053130] pci 0000:00:1f.1: reg 18: [io  0xbfe8-0xbfef]
[    0.053137] pci 0000:00:1f.1: reg 1c: [io  0xbfe4-0xbfe7]
[    0.053144] pci 0000:00:1f.1: reg 20: [io  0xbfa0-0xbfaf]
[    0.053151] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.053188] pci 0000:00:1f.5: reg 10: [io  0x0000-0x00ff]
[    0.053195] pci 0000:00:1f.5: reg 14: [io  0x0000-0x003f]
[    0.053201] pci 0000:00:1f.5: reg 18: [mem 0x00000000-0x000001ff]
[    0.053208] pci 0000:00:1f.5: reg 1c: [mem 0x00000000-0x000000ff]
[    0.053236] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.053240] pci 0000:00:1f.5: PME# disabled
[    0.053266] pci 0000:00:1f.6: reg 10: [io  0x0000-0x00ff]
[    0.053272] pci 0000:00:1f.6: reg 14: [io  0x0000-0x007f]
[    0.053307] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.053312] pci 0000:00:1f.6: PME# disabled
[    0.053355] pci 0000:01:05.0: reg 10: [mem 0xcffff000-0xcfffffff]
[    0.053396] pci 0000:01:05.0: PME# supported from D0 D3hot D3cold
[    0.053401] pci 0000:01:05.0: PME# disabled
[    0.053428] pci 0000:01:07.0: reg 10: [mem 0x00000000-0x000007ff]
[    0.053436] pci 0000:01:07.0: reg 14: [mem 0x00000000-0x00003fff]
[    0.053473] pci 0000:01:07.0: supports D1 D2
[    0.053475] pci 0000:01:07.0: PME# supported from D0 D1 D2 D3hot
[    0.053480] pci 0000:01:07.0: PME# disabled
[    0.053505] pci 0000:01:08.0: reg 10: [mem 0xcfffe000-0xcfffefff]
[    0.053512] pci 0000:01:08.0: reg 14: [io  0xcf00-0xcf3f]
[    0.053546] pci 0000:01:08.0: supports D1 D2
[    0.053549] pci 0000:01:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.053553] pci 0000:01:08.0: PME# disabled
[    0.053584] pci 0000:01:0b.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.053628] pci 0000:00:1e.0: PCI bridge to [bus 01-03] (subtractive decode)
[    0.053634] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
[    0.053639] pci 0000:00:1e.0:   bridge window [mem 0xcff00000-0xcfffffff]
[    0.053645] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.053649] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.053653] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.053695] pci_bus 0000:00: on NUMA node 0
[    0.053699] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.053759] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.056611] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[    0.056745] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
[    0.056878] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
[    0.057011] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
[    0.057143] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
[    0.057275] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
[    0.057407] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
[    0.057539] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
[    0.057586] HEST: Table is not found!
[    0.057668] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.057679] vgaarb: loaded
[    0.057879] SCSI subsystem initialized
[    0.057924] libata version 3.00 loaded.
[    0.058002] usbcore: registered new interface driver usbfs
[    0.058019] usbcore: registered new interface driver hub
[    0.058050] usbcore: registered new device driver usb
[    0.058200] ACPI: WMI: Mapper loaded
[    0.058203] PCI: Using ACPI for IRQ routing
[    0.058234] PCI: pci_cache_line_size set to 64 bytes
[    0.058248] pci 0000:00:1d.0: address space collision: [io  0xcfe0-0xcfff] conflicts with PCI Bus 0000:01 [io  0xc000-0xcfff]
[    0.058255] pci 0000:00:1d.1: address space collision: [io  0xcf80-0xcf9f] conflicts with PCI Bus 0000:01 [io  0xc000-0xcfff]
[    0.058261] pci 0000:00:1d.2: address space collision: [io  0xcf60-0xcf7f] conflicts with PCI Bus 0000:01 [io  0xc000-0xcfff]
[    0.058310] reserve RAM buffer: 0000000000002000 - 000000000000ffff
[    0.058314] reserve RAM buffer: 000000000009fc00 - 000000000009ffff
[    0.058317] reserve RAM buffer: 000000001ef40000 - 000000001fffffff
[    0.058433] NetLabel: Initializing
[    0.058436] NetLabel:  domain hash size = 128
[    0.058438] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.058455] NetLabel:  unlabeled traffic allowed by default
[    0.058501] Switching to clocksource tsc
[    0.069561] AppArmor: AppArmor Filesystem Enabled
[    0.069594] pnp: PnP ACPI init
[    0.069630] ACPI: bus type pnp registered
[    0.070802] pnp 00:00: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:02.1 BAR 0 [mem 0x00000000-0x07ffffff pref]
[    0.070809] pnp 00:00: disabling [mem 0x000e0000-0x000effff] because it overlaps 0000:00:02.1 BAR 0 [mem 0x00000000-0x07ffffff pref]
[    0.070814] pnp 00:00: disabling [mem 0x000f0000-0x000fffff] because it overlaps 0000:00:02.1 BAR 0 [mem 0x00000000-0x07ffffff pref]
[    0.070819] pnp 00:00: disabling [mem 0x00100000-0x1ef3ffff] because it overlaps 0000:00:02.1 BAR 0 [mem 0x00000000-0x07ffffff pref]
[    0.071137] ERROR: Unable to locate IOAPIC for GSI 13
[    0.071215] ERROR: Unable to locate IOAPIC for GSI 1
[    0.071292] ERROR: Unable to locate IOAPIC for GSI 12
[    0.071339] ERROR: Unable to locate IOAPIC for GSI 8
[    0.071436] pnp 00:08: disabling [io  0x0010-0x001f] because it overlaps 0000:00:1d.0 BAR 4 [io  0x0000-0x001f]
[    0.071447] pnp 00:08: disabling [io  0x0010-0x001f disabled] because it overlaps 0000:00:1d.1 BAR 4 [io  0x0000-0x001f]
[    0.071458] pnp 00:08: disabling [io  0x0010-0x001f disabled] because it overlaps 0000:00:1d.2 BAR 4 [io  0x0000-0x001f]
[    0.071511] pnp 00:08: disabling [io  0x002e-0x002f] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071515] pnp 00:08: disabling [io  0x0062] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071520] pnp 00:08: disabling [io  0x0066] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071524] pnp 00:08: disabling [io  0x0080] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071529] pnp 00:08: disabling [io  0x0084-0x0086] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071533] pnp 00:08: disabling [io  0x0088] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071538] pnp 00:08: disabling [io  0x008c-0x008e] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071543] pnp 00:08: disabling [io  0x00e0-0x00ef] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071549] pnp 00:08: disabling [io  0x0010-0x001f disabled] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071554] pnp 00:08: disabling [io  0x0024-0x0025] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071559] pnp 00:08: disabling [io  0x0028-0x0029] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071563] pnp 00:08: disabling [io  0x002c-0x002d] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071568] pnp 00:08: disabling [io  0x0030-0x0031] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071573] pnp 00:08: disabling [io  0x0034-0x0035] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071578] pnp 00:08: disabling [io  0x0038-0x0039] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071582] pnp 00:08: disabling [io  0x003c-0x003d] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071587] pnp 00:08: disabling [io  0x0050-0x0053] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071592] pnp 00:08: disabling [io  0x0063] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071596] pnp 00:08: disabling [io  0x0065] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071601] pnp 00:08: disabling [io  0x0072-0x0077] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071606] pnp 00:08: disabling [io  0x0090-0x009f] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071611] pnp 00:08: disabling [io  0x00a4-0x00a5] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071616] pnp 00:08: disabling [io  0x00a8-0x00a9] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071620] pnp 00:08: disabling [io  0x00ac-0x00ad] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071625] pnp 00:08: disabling [io  0x00b0-0x00b5] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071630] pnp 00:08: disabling [io  0x00b8-0x00b9] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071635] pnp 00:08: disabling [io  0x00bc-0x00bd] because it overlaps 0000:00:1f.5 BAR 0 [io  0x0000-0x00ff]
[    0.071640] pnp 00:08: disabling [io  0x002e-0x002f disabled] because it overlaps 0000:00:1f.5 BAR 1 [io  0x0000-0x003f]
[    0.071647] pnp 00:08: disabling [io  0x0010-0x001f disabled] because it overlaps 0000:00:1f.5 BAR 1 [io  0x0000-0x003f]
[    0.071652] pnp 00:08: disabling [io  0x0024-0x0025 disabled] because it overlaps 0000:00:1f.5 BAR 1 [io  0x0000-0x003f]
[    0.071657] pnp 00:08: disabling [io  0x0028-0x0029 disabled] because it overlaps 0000:00:1f.5 BAR 1 [io  0x0000-0x003f]
[    0.071662] pnp 00:08: disabling [io  0x002c-0x002d disabled] because it overlaps 0000:00:1f.5 BAR 1 [io  0x0000-0x003f]
[    0.071667] pnp 00:08: disabling [io  0x0030-0x0031 disabled] because it overlaps 0000:00:1f.5 BAR 1 [io  0x0000-0x003f]
[    0.071672] pnp 00:08: disabling [io  0x0034-0x0035 disabled] because it overlaps 0000:00:1f.5 BAR 1 [io  0x0000-0x003f]
[    0.071677] pnp 00:08: disabling [io  0x0038-0x0039 disabled] because it overlaps 0000:00:1f.5 BAR 1 [io  0x0000-0x003f]
[    0.071682] pnp 00:08: disabling [io  0x003c-0x003d disabled] because it overlaps 0000:00:1f.5 BAR 1 [io  0x0000-0x003f]
[    0.071691] pnp 00:08: disabling [io  0x002e-0x002f disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071696] pnp 00:08: disabling [io  0x0062 disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071700] pnp 00:08: disabling [io  0x0066 disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071705] pnp 00:08: disabling [io  0x0080 disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071710] pnp 00:08: disabling [io  0x0084-0x0086 disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071715] pnp 00:08: disabling [io  0x0088 disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071720] pnp 00:08: disabling [io  0x008c-0x008e disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071725] pnp 00:08: disabling [io  0x00e0-0x00ef disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071731] pnp 00:08: disabling [io  0x0010-0x001f disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071736] pnp 00:08: disabling [io  0x0024-0x0025 disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071741] pnp 00:08: disabling [io  0x0028-0x0029 disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071746] pnp 00:08: disabling [io  0x002c-0x002d disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071751] pnp 00:08: disabling [io  0x0030-0x0031 disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071756] pnp 00:08: disabling [io  0x0034-0x0035 disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071761] pnp 00:08: disabling [io  0x0038-0x0039 disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071766] pnp 00:08: disabling [io  0x003c-0x003d disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071772] pnp 00:08: disabling [io  0x0050-0x0053 disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071776] pnp 00:08: disabling [io  0x0063 disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071781] pnp 00:08: disabling [io  0x0065 disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071786] pnp 00:08: disabling [io  0x0072-0x0077 disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071791] pnp 00:08: disabling [io  0x0090-0x009f disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071796] pnp 00:08: disabling [io  0x00a4-0x00a5 disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071802] pnp 00:08: disabling [io  0x00a8-0x00a9 disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071807] pnp 00:08: disabling [io  0x00ac-0x00ad disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071812] pnp 00:08: disabling [io  0x00b0-0x00b5 disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071817] pnp 00:08: disabling [io  0x00b8-0x00b9 disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071822] pnp 00:08: disabling [io  0x00bc-0x00bd disabled] because it overlaps 0000:00:1f.6 BAR 0 [io  0x0000-0x00ff]
[    0.071827] pnp 00:08: disabling [io  0x002e-0x002f disabled] because it overlaps 0000:00:1f.6 BAR 1 [io  0x0000-0x007f]
[    0.071832] pnp 00:08: disabling [io  0x0062 disabled] because it overlaps 0000:00:1f.6 BAR 1 [io  0x0000-0x007f]
[    0.071837] pnp 00:08: disabling [io  0x0066 disabled] because it overlaps 0000:00:1f.6 BAR 1 [io  0x0000-0x007f]
[    0.071844] pnp 00:08: disabling [io  0x0010-0x001f disabled] because it overlaps 0000:00:1f.6 BAR 1 [io  0x0000-0x007f]
[    0.071849] pnp 00:08: disabling [io  0x0024-0x0025 disabled] because it overlaps 0000:00:1f.6 BAR 1 [io  0x0000-0x007f]
[    0.071854] pnp 00:08: disabling [io  0x0028-0x0029 disabled] because it overlaps 0000:00:1f.6 BAR 1 [io  0x0000-0x007f]
[    0.071859] pnp 00:08: disabling [io  0x002c-0x002d disabled] because it overlaps 0000:00:1f.6 BAR 1 [io  0x0000-0x007f]
[    0.071864] pnp 00:08: disabling [io  0x0030-0x0031 disabled] because it overlaps 0000:00:1f.6 BAR 1 [io  0x0000-0x007f]
[    0.071869] pnp 00:08: disabling [io  0x0034-0x0035 disabled] because it overlaps 0000:00:1f.6 BAR 1 [io  0x0000-0x007f]
[    0.071874] pnp 00:08: disabling [io  0x0038-0x0039 disabled] because it overlaps 0000:00:1f.6 BAR 1 [io  0x0000-0x007f]
[    0.071879] pnp 00:08: disabling [io  0x003c-0x003d disabled] because it overlaps 0000:00:1f.6 BAR 1 [io  0x0000-0x007f]
[    0.071884] pnp 00:08: disabling [io  0x0050-0x0053 disabled] because it overlaps 0000:00:1f.6 BAR 1 [io  0x0000-0x007f]
[    0.071889] pnp 00:08: disabling [io  0x0063 disabled] because it overlaps 0000:00:1f.6 BAR 1 [io  0x0000-0x007f]
[    0.071894] pnp 00:08: disabling [io  0x0065 disabled] because it overlaps 0000:00:1f.6 BAR 1 [io  0x0000-0x007f]
[    0.071899] pnp 00:08: disabling [io  0x0072-0x0077 disabled] because it overlaps 0000:00:1f.6 BAR 1 [io  0x0000-0x007f]
[    0.072301] pnp: PnP ACPI: found 9 devices
[    0.072304] ACPI: ACPI bus type pnp unregistered
[    0.072309] PnPBIOS: Disabled by ACPI PNP
[    0.072327] system 00:00: [mem 0x1ef40000-0x1ef4ffff] could not be reserved
[    0.072331] system 00:00: [mem 0x1ef50000-0x1effffff] has been reserved
[    0.072335] system 00:00: [mem 0xfec10000-0xfec1ffff] has been reserved
[    0.072339] system 00:00: [mem 0xfeda0000-0xfedbffff] has been reserved
[    0.072343] system 00:00: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.072347] system 00:00: [mem 0xfff00000-0xffffffff] has been reserved
[    0.072357] system 00:08: [io  0x01e0-0x01e7] has been reserved
[    0.072361] system 00:08: [io  0x0480-0x048f] has been reserved
[    0.072365] system 00:08: [io  0x0680-0x06ff] has been reserved
[    0.072369] system 00:08: [io  0xd800-0xd87f] has been reserved
[    0.072372] system 00:08: [io  0xd880-0xd89f] has been reserved
[    0.072376] system 00:08: [io  0xd8a0-0xd8bf] has been reserved
[    0.072380] system 00:08: [io  0xe000-0xe07f] has been reserved
[    0.072383] system 00:08: [io  0xe080-0xe0ff] has been reserved
[    0.072387] system 00:08: [io  0xe400-0xe47f] has been reserved
[    0.072391] system 00:08: [io  0xe480-0xe4ff] has been reserved
[    0.072395] system 00:08: [io  0xe800-0xe87f] has been reserved
[    0.072398] system 00:08: [io  0xe880-0xe8ff] has been reserved
[    0.072402] system 00:08: [io  0xec00-0xec7f] has been reserved
[    0.072406] system 00:08: [io  0xec80-0xecff] has been reserved
[    0.072410] system 00:08: [io  0xeeac] has been reserved
[    0.072413] system 00:08: [io  0xeeb0-0xeebf] has been reserved
[    0.072417] system 00:08: [io  0xeec0-0xeeff] has been reserved
[    0.072424] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.109007] pci 0000:00:02.1: BAR 0: assigned [mem 0x20000000-0x27ffffff pref]
[    0.109014] pci 0000:00:02.1: BAR 0: set to [mem 0x20000000-0x27ffffff pref] (PCI address [0x20000000-0x27ffffff]
[    0.109020] pci 0000:00:1e.0: BAR 15: assigned [mem 0x28000000-0x2bffffff pref]
[    0.109024] pci 0000:00:02.1: BAR 1: assigned [mem 0x2c000000-0x2c07ffff]
[    0.109030] pci 0000:00:02.1: BAR 1: set to [mem 0x2c000000-0x2c07ffff] (PCI address [0x2c000000-0x2c07ffff]
[    0.109035] pci 0000:00:1d.7: BAR 0: assigned [mem 0x2c080000-0x2c0803ff]
[    0.109041] pci 0000:00:1d.7: BAR 0: set to [mem 0x2c080000-0x2c0803ff] (PCI address [0x2c080000-0x2c0803ff]
[    0.109046] pci 0000:00:1f.1: BAR 5: assigned [mem 0x2c080400-0x2c0807ff]
[    0.109052] pci 0000:00:1f.1: BAR 5: set to [mem 0x2c080400-0x2c0807ff] (PCI address [0x2c080400-0x2c0807ff]
[    0.109057] pci 0000:00:1f.5: BAR 2: assigned [mem 0x2c080800-0x2c0809ff]
[    0.109063] pci 0000:00:1f.5: BAR 2: set to [mem 0x2c080800-0x2c0809ff] (PCI address [0x2c080800-0x2c0809ff]
[    0.109067] pci 0000:00:1f.5: BAR 0: assigned [io  0x1000-0x10ff]
[    0.109073] pci 0000:00:1f.5: BAR 0: set to [io  0x1000-0x10ff] (PCI address [0x1000-0x10ff]
[    0.109078] pci 0000:00:1f.5: BAR 3: assigned [mem 0x2c080a00-0x2c080aff]
[    0.109084] pci 0000:00:1f.5: BAR 3: set to [mem 0x2c080a00-0x2c080aff] (PCI address [0x2c080a00-0x2c080aff]
[    0.109088] pci 0000:00:1f.6: BAR 0: assigned [io  0x1400-0x14ff]
[    0.109094] pci 0000:00:1f.6: BAR 0: set to [io  0x1400-0x14ff] (PCI address [0x1400-0x14ff]
[    0.109098] pci 0000:00:1f.6: BAR 1: assigned [io  0x1800-0x187f]
[    0.109104] pci 0000:00:1f.6: BAR 1: set to [io  0x1800-0x187f] (PCI address [0x1800-0x187f]
[    0.109108] pci 0000:00:1f.5: BAR 1: assigned [io  0x1880-0x18bf]
[    0.109114] pci 0000:00:1f.5: BAR 1: set to [io  0x1880-0x18bf] (PCI address [0x1880-0x18bf]
[    0.109118] pci 0000:00:1d.0: BAR 4: assigned [io  0x18c0-0x18df]
[    0.109124] pci 0000:00:1d.0: BAR 4: set to [io  0x18c0-0x18df] (PCI address [0x18c0-0x18df]
[    0.109128] pci 0000:00:1d.1: BAR 4: assigned [io  0x18e0-0x18ff]
[    0.109134] pci 0000:00:1d.1: BAR 4: set to [io  0x18e0-0x18ff] (PCI address [0x18e0-0x18ff]
[    0.109139] pci 0000:00:1d.2: BAR 4: assigned [io  0x1c00-0x1c1f]
[    0.109145] pci 0000:00:1d.2: BAR 4: set to [io  0x1c00-0x1c1f] (PCI address [0x1c00-0x1c1f]
[    0.109150] pci 0000:01:0b.0: BAR 15: assigned [mem 0x28000000-0x2bffffff pref]
[    0.109155] pci 0000:01:0b.0: BAR 16: assigned [mem 0x30000000-0x33ffffff]
[    0.109159] pci 0000:01:07.0: BAR 1: assigned [mem 0xcff00000-0xcff03fff]
[    0.109165] pci 0000:01:07.0: BAR 1: set to [mem 0xcff00000-0xcff03fff] (PCI address [0xcff00000-0xcff03fff]
[    0.109169] pci 0000:01:0b.0: BAR 0: assigned [mem 0xcff04000-0xcff04fff]
[    0.109175] pci 0000:01:0b.0: BAR 0: set to [mem 0xcff04000-0xcff04fff] (PCI address [0xcff04000-0xcff04fff]
[    0.109180] pci 0000:01:07.0: BAR 0: assigned [mem 0xcff05000-0xcff057ff]
[    0.109186] pci 0000:01:07.0: BAR 0: set to [mem 0xcff05000-0xcff057ff] (PCI address [0xcff05000-0xcff057ff]
[    0.109190] pci 0000:01:0b.0: BAR 13: assigned [io  0xc000-0xc0ff]
[    0.109194] pci 0000:01:0b.0: BAR 14: assigned [io  0xc400-0xc4ff]
[    0.109198] pci 0000:01:0b.0: CardBus bridge to [bus 02-02]
[    0.109201] pci 0000:01:0b.0:   bridge window [io  0xc000-0xc0ff]
[    0.109207] pci 0000:01:0b.0:   bridge window [io  0xc400-0xc4ff]
[    0.109212] pci 0000:01:0b.0:   bridge window [mem 0x28000000-0x2bffffff pref]
[    0.109218] pci 0000:01:0b.0:   bridge window [mem 0x30000000-0x33ffffff]
[    0.109224] pci 0000:00:1e.0: PCI bridge to [bus 01-03]
[    0.109229] pci 0000:00:1e.0:   bridge window [io  0xc000-0xcfff]
[    0.109235] pci 0000:00:1e.0:   bridge window [mem 0xcff00000-0xcfffffff]
[    0.109240] pci 0000:00:1e.0:   bridge window [mem 0x28000000-0x2bffffff pref]
[    0.109258] pci 0000:00:1e.0: setting latency timer to 64
[    0.109269] pci 0000:01:0b.0: enabling device (0000 -> 0003)
[    0.109500] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.109504] PCI: setting IRQ 11 as level-triggered
[    0.109510] pci 0000:01:0b.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.109519] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.109522] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.109526] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.109529] pci_bus 0000:01: resource 1 [mem 0xcff00000-0xcfffffff]
[    0.109533] pci_bus 0000:01: resource 2 [mem 0x28000000-0x2bffffff pref]
[    0.109536] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
[    0.109539] pci_bus 0000:01: resource 5 [mem 0x00000000-0xffffffff]
[    0.109543] pci_bus 0000:02: resource 0 [io  0xc000-0xc0ff]
[    0.109546] pci_bus 0000:02: resource 1 [io  0xc400-0xc4ff]
[    0.109549] pci_bus 0000:02: resource 2 [mem 0x28000000-0x2bffffff pref]
[    0.109553] pci_bus 0000:02: resource 3 [mem 0x30000000-0x33ffffff]
[    0.109609] NET: Registered protocol family 2
[    0.109697] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.109952] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.110093] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.110238] TCP: Hash tables configured (established 16384 bind 16384)
[    0.110241] TCP reno registered
[    0.110246] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.110261] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.110359] NET: Registered protocol family 1
[    0.110383] pci 0000:00:02.0: Boot video device
[    0.110464] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
[    0.110476] PCI: CLS 32 bytes, default 64
[    0.110579] Simple Boot Flag at 0x7c set to 0x1
[    0.110687] cpufreq-nforce2: No nForce2 chipset.
[    0.110725] Scanning for low memory corruption every 60 seconds
[    0.110939] audit: initializing netlink socket (disabled)
[    0.110958] type=2000 audit(1298741808.108:1): initialized
[    0.125393] Trying to unpack rootfs image as initramfs...
[    0.141708] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.147631] VFS: Disk quotas dquot_6.5.2
[    0.147714] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.153721] fuse init (API version 7.14)
[    0.153855] msgmni has been set to 938
[    0.162160] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.162165] io scheduler noop registered
[    0.162168] io scheduler deadline registered
[    0.162189] io scheduler cfq registered (default)
[    0.162377] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.162406] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.162703] ACPI: AC Adapter [ADP1] (on-line)
[    0.162797] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.162841] ACPI: Lid Switch [LID]
[    0.162902] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.162912] ACPI: Power Button [PWRB]
[    0.162976] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.162980] ACPI: Power Button [PWRF]
[    0.163277] ACPI: Fan [FAN] (off)
[    0.163420] ACPI: acpi_idle registered with cpuidle
[    0.163454] Marking TSC unstable due to TSC halts in idle
[    0.165721] thermal LNXTHERM:01: registered as thermal_zone0
[    0.165737] ACPI: Thermal Zone [THRM] (54 C)
[    0.165831] ERST: Table is not found!
[    0.166015] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.166448] serial 0000:00:1f.6: power state changed by ACPI to D0
[    0.166484] serial 0000:00:1f.6: power state changed by ACPI to D0
[    0.166490] serial 0000:00:1f.6: enabling device (0000 -> 0001)
[    0.166685] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    0.166691] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.166699] serial 0000:00:1f.6: PCI INT B disabled
[    0.168172] brd: module loaded
[    0.168877] loop: module loaded
[    0.169098] ata_piix 0000:00:1f.1: version 2.13
[    0.169111] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.169157] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.169251] Switching to clocksource acpi_pm
[    0.170225] ACPI: Battery Slot [BAT1] (battery present)
[    0.170239] isapnp: Scanning for PnP cards...
[    0.219088] scsi0 : ata_piix
[    0.224037] scsi1 : ata_piix
[    0.224619] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.224623] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.225104] Fixed MDIO Bus: probed
[    0.225150] PPP generic driver version 2.4.2
[    0.225224] tun: Universal TUN/TAP device driver, 1.6
[    0.225227] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.225336] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.225359] ehci_hcd 0000:00:1d.7: enabling device (0000 -> 0002)
[    0.225549] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.225555] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.225578] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.225583] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.225637] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.225673] ehci_hcd 0000:00:1d.7: debug port 1
[    0.229574] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.232511] ehci_hcd 0000:00:1d.7: irq 11, io mem 0x2c080000
[    0.252412] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.252663] hub 1-0:1.0: USB hub found
[    0.252671] hub 1-0:1.0: 6 ports detected
[    0.252781] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.252802] uhci_hcd: USB Universal Host Controller Interface driver
[    0.253110] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[    0.253114] PCI: setting IRQ 10 as level-triggered
[    0.253121] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[    0.253133] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.253137] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.253188] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.253218] uhci_hcd 0000:00:1d.0: irq 10, io base 0x000018c0
[    0.253377] hub 2-0:1.0: USB hub found
[    0.253383] hub 2-0:1.0: 2 ports detected
[    0.253626] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.253631] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.253639] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.253643] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.253685] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.253709] uhci_hcd 0000:00:1d.1: irq 11, io base 0x000018e0
[    0.253852] hub 3-0:1.0: USB hub found
[    0.253857] hub 3-0:1.0: 2 ports detected
[    0.253920] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.253927] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.253931] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.253977] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.253998] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001c00
[    0.254157] hub 4-0:1.0: USB hub found
[    0.254162] hub 4-0:1.0: 2 ports detected
[    0.254302] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.264997] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.265012] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.265189] mice: PS/2 mouse device common for all mice
[    0.265429] rtc_cmos 00:07: RTC can wake from S4
[    0.265486] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.265505] rtc0: alarms up to one year, 114 bytes nvram
[    0.265672] device-mapper: uevent: version 1.0.3
[    0.267771] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.271826] device-mapper: multipath: version 1.1.1 loaded
[    0.271830] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.274341] EISA: Probing bus 0 at eisa.0
[    0.274350] Cannot allocate resource for EISA slot 1
[    0.274370] EISA: Detected 0 cards.
[    0.279378] cpuidle: using governor ladder
[    0.279453] cpuidle: using governor menu
[    0.279843] TCP cubic registered
[    0.280059] NET: Registered protocol family 10
[    0.280603] lo: Disabled Privacy Extensions
[    0.280874] NET: Registered protocol family 17
[    0.281318] Using IPI No-Shortcut mode
[    0.281455] PM: Resume from disk failed.
[    0.281472] registered taskstats version 1
[    0.281690]   Magic number: 15:313:644
[    0.281859] rtc_cmos 00:07: setting system clock to 2011-02-26 17:36:48 UTC (1298741808)
[    0.281864] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.281867] EDD information not available.
[    0.283206] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.428494] ata1.00: ATA-6: TOSHIBA MK4025GAS, KA101A, max UDMA/100
[    0.428500] ata1.00: 78140160 sectors, multi 16: LBA
[    0.444555] ata1.00: configured for UDMA/100
[    0.452564] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-R2512, 1320, max UDMA/33
[    0.468721] ata2.00: configured for UDMA/33
[    0.683882] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    0.859711] isapnp: No Plug & Play device found
[    0.859965] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK4025GA KA10 PQ: 0 ANSI: 5
[    0.860269] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.860512] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    0.860583] sd 0:0:0:0: [sda] Write Protect is off
[    0.860587] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.860627] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.860868]  sda:
[    0.877857] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2512 1320 PQ: 0 ANSI: 5
[    0.886510]  sda1 sda2
[    0.886613] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.886619] Uniform CD-ROM driver Revision: 3.20
[    0.886800] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.886901] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.894050] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.915146] Freeing initrd memory: 10512k freed
[    0.925748] Freeing unused kernel memory: 688k freed
[    0.926570] Write protecting the kernel text: 4936k
[    0.926617] Write protecting the kernel read-only data: 1976k
[    0.944260] udev[68]: starting version 163
[    1.132098] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    1.228488] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.228493] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.228793] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    1.228799] e100 0000:01:08.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[    1.251987] e100 0000:01:08.0: PME# disabled
[    1.255977] Initializing USB Mass Storage driver...
[    1.256970] e100 0000:01:08.0: eth0: addr 0xcfffe000, irq 11, MAC addr 00:0e:7b:b3:b9:21
[    1.256996] firewire_ohci 0000:01:07.0: enabling device (0000 -> 0002)
[    1.257217] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[    1.257222] firewire_ohci 0000:01:07.0: PCI INT A -> Link[LNKF] -> GSI 11 (level, low) -> IRQ 11
[    1.258016] scsi2 : usb-storage 1-6:1.0
[    1.258174] usbcore: registered new interface driver usb-storage
[    1.258177] USB Mass Storage support registered.
[    1.312060] firewire_ohci: Added fw-ohci device 0000:01:07.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    1.315219] usb 1-6: USB disconnect, address 3
[    1.334314] usbcore: registered new interface driver hiddev
[    1.349776] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input4
[    1.350022] generic-usb 0003:046D:C01B.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1/input0
[    1.350214] usbcore: registered new interface driver usbhid
[    1.350217] usbhid: USB HID core driver
[    1.388653] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
[    1.388660] EXT4-fs (sda2): write access will be enabled during recovery
[    1.812236] firewire_core: created device fw0: GUID 0000390000638391, S400
[    3.767815] EXT4-fs (sda2): orphan cleanup on readonly fs
[    3.767828] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 1967027
[    3.767911] EXT4-fs (sda2): 1 orphan inode deleted
[    3.767916] EXT4-fs (sda2): recovery complete
[    4.123230] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    7.896051] usb 1-6: new high speed USB device using ehci_hcd and address 4
[    8.044962] scsi6 : usb-storage 1-6:1.3
[    9.050456] scsi 6:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[    9.050998] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    9.061428] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   25.523647] Adding 1464316k swap on /dev/sda1.  Priority:-1 extents:1 across:1464316k
[   25.784154] udev[338]: starting version 163
[   26.000900] intel_rng: FWH not detected
[   26.058443] lp: driver loaded but no devices found
[   26.060808] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.127208] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   26.127542] acpi device:0c: registered as cooling_device2
[   26.127715] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input5
[   26.127789] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   26.270342] Linux agpgart interface v0.103
[   26.284281] input: Toshiba input device as /devices/virtual/input/input6
[   26.284356] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19
[   26.284359] toshiba_acpi:     HCI method: \_SB_.VALZ.GHCI
[   26.291576] lib80211: common routines for IEEE802.11 drivers
[   26.291580] lib80211_crypt: registered algorithm 'NULL'
[   26.415640] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   26.472902] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   26.473708] agpgart-intel 0000:00:00.0: detected 16252K stolen memory
[   26.497157] yenta_cardbus 0000:01:0b.0: CardBus bridge found [1179:0001]
[   26.521392] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
[   26.535363] usbcore: registered new interface driver usbserial
[   26.535418] USB Serial support registered for generic
[   26.535979] usbcore: registered new interface driver usbserial_generic
[   26.535982] usbserial: USB Serial Driver core
[   26.613289] USB Serial support registered for GSM modem (1-port)
[   26.613620] option 1-6:1.0: GSM modem (1-port) converter detected
[   26.613939] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
[   26.613957] option 1-6:1.1: GSM modem (1-port) converter detected
[   26.614200] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
[   26.614215] option 1-6:1.2: GSM modem (1-port) converter detected
[   26.614419] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2
[   26.614736] usbcore: registered new interface driver option
[   26.614739] option: v0.7.2:USB Driver for GSM modems
[   26.648211] yenta_cardbus 0000:01:0b.0: ISA IRQ mask 0x00b8, PCI irq 11
[   26.648216] yenta_cardbus 0000:01:0b.0: Socket status: 30000007
[   26.648227] yenta_cardbus 0000:01:0b.0: pcmcia: parent PCI bridge window: [io  0xc000-0xcfff]
[   26.648232] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc000-0xcfff: excluding 0xc000-0xc0ff 0xc400-0xc4ff 0xcf00-0xcf3f
[   26.650948] yenta_cardbus 0000:01:0b.0: pcmcia: parent PCI bridge window: [mem 0xcff00000-0xcfffffff]
[   26.650953] pcmcia_socket pcmcia_socket0: cs: memory probe 0xcff00000-0xcfffffff: excluding 0xcff00000-0xcff0ffff 0xcfff0000-0xcfffffff
[   26.650971] yenta_cardbus 0000:01:0b.0: pcmcia: parent PCI bridge window: [mem 0x28000000-0x2bffffff pref]
[   26.650975] pcmcia_socket pcmcia_socket0: cs: memory probe 0x28000000-0x2bffffff: excluding 0x28000000-0x2bffffff
[   26.702160] cfg80211: Calling CRDA to update world regulatory domain
[   26.727958] type=1400 audit(1298741834.939:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=636 comm="apparmor_parser"
[   26.728809] type=1400 audit(1298741834.943:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=636 comm="apparmor_parser"
[   26.729250] type=1400 audit(1298741834.943:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=636 comm="apparmor_parser"
[   26.748994] type=1400 audit(1298741834.963:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=659 comm="apparmor_parser"
[   26.760694] cfg80211: World regulatory domain updated:
[   26.760699]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   26.760703]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.760707]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.760711]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.760714]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.760718]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.773363] libipw: 802.11 data/management/control stack, git-1.1.13
[   26.773368] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   26.782641] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input7
[   26.793444] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1e0-0x1e7 0x1f0-0x1f7 0x370-0x377
[   26.794350] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x480-0x48f 0x4d0-0x4d7
[   26.794721] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   26.795046] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   26.795399] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   26.795469] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   26.795540] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   26.795615] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   26.811520] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[   26.837761] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   26.837767] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   26.838143] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[   26.838150] ipw2200 0000:01:05.0: PCI INT A -> Link[LNKG] -> GSI 11 (level, low) -> IRQ 11
[   26.850992] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   26.858334] [drm] Initialized drm 1.1.0 20060810
[   27.197609] i915 0000:00:02.0: power state changed by ACPI to D0
[   27.197741] i915 0000:00:02.0: power state changed by ACPI to D0
[   27.197752] i915 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[   27.197759] i915 0000:00:02.0: setting latency timer to 64
[   27.223868] [drm] set up 15M of stolen space
[   27.353967] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   27.354466] [drm] initialized overlay support
[   27.386633] type=1400 audit(1298741835.599:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=839 comm="apparmor_parser"
[   27.387432] type=1400 audit(1298741835.599:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=839 comm="apparmor_parser"
[   27.387872] type=1400 audit(1298741835.599:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=839 comm="apparmor_parser"
[   27.407901] type=1400 audit(1298741835.619:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=841 comm="apparmor_parser"
[   27.421633] type=1400 audit(1298741835.635:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=841 comm="apparmor_parser"
[   27.432080] type=1400 audit(1298741835.647:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=841 comm="apparmor_parser"
[   27.450359] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   27.627675] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.693467] Console: switching to colour frame buffer device 128x48
[   28.697927] fb0: inteldrmfb frame buffer device
[   28.697929] drm: registered panic notifier
[   28.699278] Slow work thread pool: Starting up
[   28.702260] Slow work thread pool: Ready
[   28.702278] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   28.702569] Intel ICH 0000:00:1f.5: power state changed by ACPI to D0
[   28.702605] Intel ICH 0000:00:1f.5: power state changed by ACPI to D0
[   28.702611] Intel ICH 0000:00:1f.5: enabling device (0000 -> 0003)
[   28.702623] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   28.702657] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   29.532064] intel8x0_measure_ac97_clock: measured 55433 usecs (2671 samples)
[   29.532068] intel8x0: clocking to 48000
[   29.929487] ppdev: user-space parallel port driver
[   32.374068] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[   33.650176] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[   38.464043] eth1: no IPv6 routers present
[   52.060431] PPP BSD Compression module registered
[   52.100989] PPP Deflate Compression module registered
[  102.576119] usb 2-1: USB disconnect, address 2

```

---

### Post by Dumpy Dumpster on 2011-07-01
I have no idea what all the extracts you gave, mean, but if it is of any comfort to you, my touchpad/mouse buttons do not work when I have a wireless mouse sender plugged in to a USB port - but then one would not expect them to ,would one?

---

### Post by Toz on 2011-07-01
Suggestions to try would be:
1. update the bios
2. try disabling pnp in bios
3. try enabling/setting HPET ACPI in bios
4. try booting with **irqpoll** kernel parameter

---

