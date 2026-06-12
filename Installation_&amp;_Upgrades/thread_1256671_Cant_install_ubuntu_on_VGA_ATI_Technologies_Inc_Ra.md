---
title: "Cant install ubuntu on VGA ATI Technologies Inc Rage 128 PD/PRO TMDS"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by drvista on 2009-09-02
help please i cant install ubuntu on my computer it drops me into shell and i cant startx when i try VESA as driver it says it cant find screens here is my 

lspci

> 00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:01.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:02.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:03.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:04.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:05.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:06.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:07.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:08.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:09.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:0a.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:0b.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:0c.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:0d.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:0e.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:0f.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:10.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:11.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:12.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:13.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:14.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:15.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:16.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:17.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:18.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:19.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:1a.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:1b.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:1c.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:1d.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:1e.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
01:1f.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)



this is dmesg

#
[    0.000000] BIOS EBDA/lowmem at: 00000000/000a0000
#
[    0.000000] Initializing cgroup subsys cpuset
#
[    0.000000] Initializing cgroup subsys cpu
#
[    0.000000] Linux version 2.6.28-13-generic (buildd@vernadsky) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 (Ubuntu 2.6.28-13.45-generic)
#
[    0.000000] KERNEL supported cpus:
#
[    0.000000]   Intel GenuineIntel
#
[    0.000000]   AMD AuthenticAMD
#
[    0.000000]   NSC Geode by NSC
#
[    0.000000]   Cyrix CyrixInstead
#
[    0.000000]   Centaur CentaurHauls
#
[    0.000000]   Transmeta GenuineTMx86
#
[    0.000000]   Transmeta TransmetaCPU
#
[    0.000000]   UMC UMC UMC UMC
#
[    0.000000] BIOS-provided physical RAM map:
#
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
#
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
#
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
#
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
#
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
#
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
#
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
#
[    0.000000] DMI 2.3 present.
#
[    0.000000] last_pfn = 0x1fff0 max_arch_pfn = 0x100000
#
[    0.000000] Scanning 2 areas for low memory corruption
#
[    0.000000] modified physical RAM map:
#
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
#
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
#
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
#
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
#
[    0.000000]  modified: 0000000000010000 - 0000000000092c00 (usable)
#
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
#
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
#
[    0.000000]  modified: 0000000000100000 - 000000001fff0000 (usable)
#
[    0.000000]  modified: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
#
[    0.000000]  modified: 000000001fff3000 - 0000000020000000 (ACPI data)
#
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
#
[    0.000000] kernel direct mapping tables up to 1fff0000 @ 10000-16000
#
[    0.000000] RAMDISK: 1f858000 - 1ffbf973
#
[    0.000000] ACPI: RSDP 000F6570, 0014 (r0 GBT   )
#
[    0.000000] ACPI: RSDT 1FFF3000, 002C (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
#
[    0.000000] ACPI: FACP 1FFF3040, 0074 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
#
[    0.000000] ACPI: DSDT 1FFF30C0, 365B (r1 GBT    AWRDACPI     1000 MSFT  100000C)
#
[    0.000000] ACPI: FACS 1FFF0000, 0040
#
[    0.000000] ACPI: APIC 1FFF6740, 005A (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
#
[    0.000000] ACPI: Local APIC address 0xfee00000
#
[    0.000000] 0MB HIGHMEM available.
#
[    0.000000] 511MB LOWMEM available.
#
[    0.000000]   mapped low ram: 0 - 1fff0000
#
[    0.000000]   low ram: 00000000 - 1fff0000
#
[    0.000000]   bootmap 00012000 - 00016000
#
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001fff0000]
#
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
#
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
#
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
#
[    0.000000]   #3 [0000100000 - 00008760ac]    TEXT DATA BSS ==> [0000100000 - 00008760ac]
#
[    0.000000]   #4 [001f858000 - 001ffbf973]          RAMDISK ==> [001f858000 - 001ffbf973]
#
[    0.000000]   #5 [0000877000 - 000087b000]    INIT_PG_TABLE ==> [0000877000 - 000087b000]
#
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
#
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
#
[    0.000000]   #8 [0000012000 - 0000016000]          BOOTMAP ==> [0000012000 - 0000016000]
#
[    0.000000] found SMP MP-table at [c00f4a90] 000f4a90
#
[    0.000000] Zone PFN ranges:
#
[    0.000000]   DMA      0x00000000 -> 0x00001000
#
[    0.000000]   Normal   0x00001000 -> 0x0001fff0
#
[    0.000000]   HighMem  0x0001fff0 -> 0x0001fff0
#
[    0.000000] Movable zone start PFN for each node
#
[    0.000000] early_node_map[4] active PFN ranges
#
[    0.000000]     0: 0x00000000 -> 0x00000002
#
[    0.000000]     0: 0x00000006 -> 0x00000007
#
[    0.000000]     0: 0x00000010 -> 0x00000092
#
[    0.000000]     0: 0x00000100 -> 0x0001fff0
#
[    0.000000] On node 0 totalpages: 130933
#
[    0.000000] free_area_init_node: node 0, pgdat c06c9500, node_mem_map c1000000
#
[    0.000000]   DMA zone: 32 pages used for memmap
#
[    0.000000]   DMA zone: 0 pages reserved
#
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
#
[    0.000000]   Normal zone: 992 pages used for memmap
#
[    0.000000]   Normal zone: 125968 pages, LIFO batch:31
#
[    0.000000]   HighMem zone: 0 pages used for memmap
#
[    0.000000]   Movable zone: 0 pages used for memmap
#
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
#
[    0.000000] ACPI: Local APIC address 0xfee00000
#
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
#
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
#
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
#
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
#
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
#
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
#
[    0.000000] ACPI: IRQ0 used by override.
#
[    0.000000] ACPI: IRQ2 used by override.
#
[    0.000000] ACPI: IRQ9 used by override.
#
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
#
[    0.000000] Using ACPI (MADT) for SMP configuration information
#
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
#
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
#
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
#
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
#
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
#
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
#
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
#
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
#
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
#
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129909
#
[    0.000000] Kernel command line: file=/cdrom/preseed/custom.seed boot=casper initrd=/casper/initrd.gz quiet splash -- BOOT_IMAGE=/casper/vmlinuz
#
[    0.000000] Enabling fast FPU save and restore... done.
#
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
#
[    0.000000] Initializing CPU#0
#
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
#
[    0.000000] Fast TSC calibration using PIT
#
[    0.000000] Detected 1499.894 MHz processor.
#
[    0.004000] Console: colour VGA+ 80x25
#
[    0.004000] console [tty0] enabled
#
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
#
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
#
[    0.004000] allocated 2621120 bytes of page_cgroup
#
[    0.004000] please try cgroup_disable=memory option if you don't want
#
[    0.004000] Scanning for low memory corruption every 60 seconds
#
[    0.004000] Memory: 501120k/524224k available (4110k kernel code, 22392k reserved, 2196k data, 532k init, 0k highmem)
#
[    0.004000] virtual kernel memory layout:
#
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
#
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
#
[    0.004000]     vmalloc : 0xe07f0000 - 0xff3fe000   ( 492 MB)
#
[    0.004000]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
#
[    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)
#
[    0.004000]       .data : 0xc0503b9f - 0xc0728e60   (2196 kB)
#
[    0.004000]       .text : 0xc0100000 - 0xc0503b9f   (4110 kB)
#
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
#
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
#
[    0.004025] Calibrating delay loop (skipped), value calculated using timer frequency.. 2999.78 BogoMIPS (lpj=5999576)
#
[    0.004072] Security Framework initialized
#
[    0.004091] SELinux:  Disabled at boot.
#
[    0.004137] AppArmor: AppArmor initialized
#
[    0.004162] Mount-cache hash table entries: 512
#
[    0.004522] Initializing cgroup subsys ns
#
[    0.004535] Initializing cgroup subsys cpuacct
#
[    0.004542] Initializing cgroup subsys memory
#
[    0.004552] Initializing cgroup subsys freezer
#
[    0.004591] CPU: Trace cache: 12K uops, L1 D cache: 8K
#
[    0.004599] CPU: L2 cache: 256K
#
[    0.004606] CPU: Hyper-Threading is disabled
#
[    0.004647] Checking 'hlt' instruction... OK.
#
[    0.021424] SMP alternatives: switching to UP code
#
[    0.221638] Freeing SMP alternatives: 18k freed
#
[    0.221652] ACPI: Core revision 20080926
#
[    0.226220] ACPI: Checking initramfs for custom DSDT
#
[    0.833420] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
#
[    0.873126] CPU0: Intel(R) Pentium(R) 4 CPU 1.50GHz stepping 02
#
[    0.981125] Brought up 1 CPUs
#
[    0.981138] Total of 1 processors activated (2999.78 BogoMIPS).
#
[    0.981219] CPU0 attaching NULL sched-domain.
#
[    0.982294] net_namespace: 776 bytes
#
[    0.982320] Booting paravirtualized kernel on bare hardware
#
[    0.982925] Time:  4:50:03  Date: 01/01/02
#
[    0.982941] regulator: core version 0.5
#
[    0.983049] NET: Registered protocol family 16
#
[    0.983356] EISA bus registered
#
[    0.983388] ACPI: bus type pci registered
#
[    1.010475] PCI: PCI BIOS revision 2.10 entry at 0xf9d70, last bus=2
#
[    1.010482] PCI: Using configuration type 1 for base access
#
[    1.013830] ACPI: EC: Look up EC in DSDT
#
[    1.022979] ACPI: Interpreter enabled
#
[    1.022993] ACPI: (supports S0 S1 S4 S5)
#
[    1.023037] ACPI: Using IOAPIC for interrupt routing
#
[    1.030776] ACPI: No dock devices found.
#
[    1.030804] ACPI: PCI Root Bridge [PCI0] (0000:00)
#
[    1.030910] pci 0000:00:00.0: reg 10 32bit mmio: [0x60000000-0x67ffffff]
#
[    1.031138] pci 0000:00:1f.0: quirk: region 4000-407f claimed by ICH4 ACPI/GPIO/TCO
#
[    1.031145] pci 0000:00:1f.0: quirk: region 4080-40bf claimed by ICH4 GPIO
#
[    1.031206] pci 0000:00:1f.1: reg 20 io port: [0xf000-0xf00f]
#
[    1.031280] pci 0000:00:1f.2: reg 20 io port: [0xd000-0xd01f]
#
[    1.031351] pci 0000:00:1f.3: reg 20 io port: [0x5000-0x500f]
#
[    1.031422] pci 0000:00:1f.4: reg 20 io port: [0xd800-0xd81f]
#
[    1.031467] pci 0000:00:1f.5: reg 10 io port: [0xdc00-0xdcff]
#
[    1.031478] pci 0000:00:1f.5: reg 14 io port: [0xe000-0xe03f]
#
[    1.031564] pci 0000:01:00.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.031575] pci 0000:01:00.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.031585] pci 0000:01:00.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.031611] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.031625] pci 0000:01:00.0: supports D1
#
[    1.031666] pci 0000:01:01.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.031676] pci 0000:01:01.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.031686] pci 0000:01:01.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.031713] pci 0000:01:01.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.031726] pci 0000:01:01.0: supports D1
#
[    1.031770] pci 0000:01:02.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.031780] pci 0000:01:02.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.031791] pci 0000:01:02.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.031817] pci 0000:01:02.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.031830] pci 0000:01:02.0: supports D1
#
[    1.031871] pci 0000:01:03.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.031881] pci 0000:01:03.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.031892] pci 0000:01:03.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.031918] pci 0000:01:03.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.031931] pci 0000:01:03.0: supports D1
#
[    1.031972] pci 0000:01:04.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.031982] pci 0000:01:04.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.032024] pci 0000:01:04.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.032052] pci 0000:01:04.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.032066] pci 0000:01:04.0: supports D1
#
[    1.032107] pci 0000:01:05.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.032117] pci 0000:01:05.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.032127] pci 0000:01:05.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.032152] pci 0000:01:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.032166] pci 0000:01:05.0: supports D1
#
[    1.032206] pci 0000:01:06.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.032215] pci 0000:01:06.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.032225] pci 0000:01:06.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.032251] pci 0000:01:06.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.032264] pci 0000:01:06.0: supports D1
#
[    1.032304] pci 0000:01:07.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.032314] pci 0000:01:07.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.032324] pci 0000:01:07.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.032349] pci 0000:01:07.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.032362] pci 0000:01:07.0: supports D1
#
[    1.032403] pci 0000:01:08.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.032412] pci 0000:01:08.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.032422] pci 0000:01:08.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.032448] pci 0000:01:08.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.032461] pci 0000:01:08.0: supports D1
#
[    1.032501] pci 0000:01:09.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.032511] pci 0000:01:09.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.032520] pci 0000:01:09.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.032546] pci 0000:01:09.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.032559] pci 0000:01:09.0: supports D1
#
[    1.032603] pci 0000:01:0a.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.032613] pci 0000:01:0a.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.032623] pci 0000:01:0a.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.032648] pci 0000:01:0a.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.032661] pci 0000:01:0a.0: supports D1
#
[    1.032702] pci 0000:01:0b.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.032712] pci 0000:01:0b.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.032721] pci 0000:01:0b.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.032747] pci 0000:01:0b.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.032760] pci 0000:01:0b.0: supports D1
#
[    1.032800] pci 0000:01:0c.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.032810] pci 0000:01:0c.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.032820] pci 0000:01:0c.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.032845] pci 0000:01:0c.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.032858] pci 0000:01:0c.0: supports D1
#
[    1.032899] pci 0000:01:0d.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.032908] pci 0000:01:0d.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.032918] pci 0000:01:0d.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.032943] pci 0000:01:0d.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.032957] pci 0000:01:0d.0: supports D1
#
[    1.032996] pci 0000:01:0e.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.033006] pci 0000:01:0e.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.033016] pci 0000:01:0e.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.033042] pci 0000:01:0e.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.033055] pci 0000:01:0e.0: supports D1
#
[    1.033095] pci 0000:01:0f.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.033105] pci 0000:01:0f.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.033114] pci 0000:01:0f.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.033140] pci 0000:01:0f.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.033153] pci 0000:01:0f.0: supports D1
#
[    1.033193] pci 0000:01:10.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.033203] pci 0000:01:10.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.033212] pci 0000:01:10.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.033238] pci 0000:01:10.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.033251] pci 0000:01:10.0: supports D1
#
[    1.033291] pci 0000:01:11.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.033301] pci 0000:01:11.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.033310] pci 0000:01:11.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.033336] pci 0000:01:11.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.033349] pci 0000:01:11.0: supports D1
#
[    1.033393] pci 0000:01:12.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.033403] pci 0000:01:12.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.033412] pci 0000:01:12.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.033438] pci 0000:01:12.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.033451] pci 0000:01:12.0: supports D1
#
[    1.033491] pci 0000:01:13.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.033501] pci 0000:01:13.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.033511] pci 0000:01:13.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.033536] pci 0000:01:13.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.033549] pci 0000:01:13.0: supports D1
#
[    1.033590] pci 0000:01:14.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.033600] pci 0000:01:14.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.033609] pci 0000:01:14.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.033635] pci 0000:01:14.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.033648] pci 0000:01:14.0: supports D1
#
[    1.033688] pci 0000:01:15.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.033698] pci 0000:01:15.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.033708] pci 0000:01:15.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.033733] pci 0000:01:15.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.033746] pci 0000:01:15.0: supports D1
#
[    1.033786] pci 0000:01:16.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.033796] pci 0000:01:16.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.033806] pci 0000:01:16.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.033831] pci 0000:01:16.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.033844] pci 0000:01:16.0: supports D1
#
[    1.033885] pci 0000:01:17.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.033895] pci 0000:01:17.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.033904] pci 0000:01:17.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.033930] pci 0000:01:17.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.033943] pci 0000:01:17.0: supports D1
#
[    1.033983] pci 0000:01:18.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.033993] pci 0000:01:18.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.034003] pci 0000:01:18.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.034028] pci 0000:01:18.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.034041] pci 0000:01:18.0: supports D1
#
[    1.034082] pci 0000:01:19.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.034092] pci 0000:01:19.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.034102] pci 0000:01:19.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.034127] pci 0000:01:19.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.034140] pci 0000:01:19.0: supports D1
#
[    1.034183] pci 0000:01:1a.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.034193] pci 0000:01:1a.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.034203] pci 0000:01:1a.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.034229] pci 0000:01:1a.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.034242] pci 0000:01:1a.0: supports D1
#
[    1.034282] pci 0000:01:1b.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.034292] pci 0000:01:1b.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.034302] pci 0000:01:1b.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.034327] pci 0000:01:1b.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.034340] pci 0000:01:1b.0: supports D1
#
[    1.034381] pci 0000:01:1c.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.034391] pci 0000:01:1c.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.034400] pci 0000:01:1c.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.034426] pci 0000:01:1c.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.034439] pci 0000:01:1c.0: supports D1
#
[    1.034479] pci 0000:01:1d.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.034489] pci 0000:01:1d.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.034499] pci 0000:01:1d.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.034524] pci 0000:01:1d.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.034537] pci 0000:01:1d.0: supports D1
#
[    1.034578] pci 0000:01:1e.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.034587] pci 0000:01:1e.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.034597] pci 0000:01:1e.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.034623] pci 0000:01:1e.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.034636] pci 0000:01:1e.0: supports D1
#
[    1.034677] pci 0000:01:1f.0: reg 10 32bit mmio: [0xe4000000-0xe7ffffff]
#
[    1.034686] pci 0000:01:1f.0: reg 14 io port: [0xbc00-0xbcff]
#
[    1.034696] pci 0000:01:1f.0: reg 18 32bit mmio: [0xe907c000-0xe907ffff]
#
[    1.034722] pci 0000:01:1f.0: reg 30 32bit mmio: [0x000000-0x01ffff]
#
[    1.034735] pci 0000:01:1f.0: supports D1
#
[    1.034748] pci 0000:00:01.0: bridge io port: [0x4000-0xbfff]
#
[    1.034754] pci 0000:00:01.0: bridge 32bit mmio: [0xe8000000-0xe9ffffff]
#
[    1.034761] pci 0000:00:01.0: bridge 32bit mmio pref: [0x68000000-0xe7ffffff]
#
[    1.034818] pci 0000:02:02.0: reg 10 io port: [0xc000-0xc0ff]
#
[    1.034829] pci 0000:02:02.0: reg 14 32bit mmio: [0xea000000-0xea0000ff]
#
[    1.034872] pci 0000:02:02.0: supports D1 D2
#
[    1.034877] pci 0000:02:02.0: PME# supported from D1 D2 D3hot
#
[    1.034884] pci 0000:02:02.0: PME# disabled
#
[    1.034951] pci 0000:00:1e.0: transparent bridge
#
[    1.034958] pci 0000:00:1e.0: bridge io port: [0xc000-0xcfff]
#
[    1.034966] pci 0000:00:1e.0: bridge 32bit mmio: [0xea000000-0xea0fffff]
#
[    1.034986] bus 00 -> node 0
#
[    1.035008] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
#
[    1.035381] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
#
[    1.065250] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
#
[    1.065481] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
#
[    1.065701] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
#
[    1.065922] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
#
[    1.066141] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
#
[    1.066363] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
#
[    1.066585] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
#
[    1.066804] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
#
[    1.067105] ACPI: WMI: Mapper loaded
#
[    1.067719] SCSI subsystem initialized
#
[    1.067869] libata version 3.00 loaded.
#
[    1.068041] usbcore: registered new interface driver usbfs
#
[    1.068089] usbcore: registered new interface driver hub
#
[    1.068185] usbcore: registered new device driver usb
#
[    1.068498] PCI: Using ACPI for IRQ routing
#
[    1.068519] pci 0000:00:01.0: BAR 7: can't allocate resource
#
[    1.068567] pci 0000:01:00.0: BAR 1: can't allocate resource
#
[    1.068574] pci 0000:01:01.0: BAR 0: can't allocate resource
#
[    1.068579] pci 0000:01:01.0: BAR 1: can't allocate resource
#
[    1.068582] pci 0000:01:01.0: BAR 2: can't allocate resource
#
[    1.068589] pci 0000:01:02.0: BAR 0: can't allocate resource
#
[    1.068594] pci 0000:01:02.0: BAR 1: can't allocate resource
#
[    1.068597] pci 0000:01:02.0: BAR 2: can't allocate resource
#
[    1.068604] pci 0000:01:03.0: BAR 0: can't allocate resource
#
[    1.068608] pci 0000:01:03.0: BAR 1: can't allocate resource
#
[    1.068612] pci 0000:01:03.0: BAR 2: can't allocate resource
#
[    1.068619] pci 0000:01:04.0: BAR 0: can't allocate resource
#
[    1.068623] pci 0000:01:04.0: BAR 1: can't allocate resource
#
[    1.068627] pci 0000:01:04.0: BAR 2: can't allocate resource
#
[    1.068634] pci 0000:01:05.0: BAR 0: can't allocate resource
#
[    1.068638] pci 0000:01:05.0: BAR 1: can't allocate resource
#
[    1.068641] pci 0000:01:05.0: BAR 2: can't allocate resource
#
[    1.068648] pci 0000:01:06.0: BAR 0: can't allocate resource
#
[    1.068652] pci 0000:01:06.0: BAR 1: can't allocate resource
#
[    1.068656] pci 0000:01:06.0: BAR 2: can't allocate resource
#
[    1.068663] pci 0000:01:07.0: BAR 0: can't allocate resource
#
[    1.068667] pci 0000:01:07.0: BAR 1: can't allocate resource
#
[    1.068671] pci 0000:01:07.0: BAR 2: can't allocate resource
#
[    1.068678] pci 0000:01:08.0: BAR 0: can't allocate resource
#
[    1.068682] pci 0000:01:08.0: BAR 1: can't allocate resource
#
[    1.068686] pci 0000:01:08.0: BAR 2: can't allocate resource
#
[    1.068693] pci 0000:01:09.0: BAR 0: can't allocate resource
#
[    1.068697] pci 0000:01:09.0: BAR 1: can't allocate resource
#
[    1.068701] pci 0000:01:09.0: BAR 2: can't allocate resource
#
[    1.068708] pci 0000:01:0a.0: BAR 0: can't allocate resource
#
[    1.068712] pci 0000:01:0a.0: BAR 1: can't allocate resource
#
[    1.068715] pci 0000:01:0a.0: BAR 2: can't allocate resource
#
[    1.068722] pci 0000:01:0b.0: BAR 0: can't allocate resource
#
[    1.068726] pci 0000:01:0b.0: BAR 1: can't allocate resource
#
[    1.068730] pci 0000:01:0b.0: BAR 2: can't allocate resource
#
[    1.068737] pci 0000:01:0c.0: BAR 0: can't allocate resource
#
[    1.068741] pci 0000:01:0c.0: BAR 1: can't allocate resource
#
[    1.068745] pci 0000:01:0c.0: BAR 2: can't allocate resource
#
[    1.068752] pci 0000:01:0d.0: BAR 0: can't allocate resource
#
[    1.068756] pci 0000:01:0d.0: BAR 1: can't allocate resource
#
[    1.068760] pci 0000:01:0d.0: BAR 2: can't allocate resource
#
[    1.068767] pci 0000:01:0e.0: BAR 0: can't allocate resource
#
[    1.068771] pci 0000:01:0e.0: BAR 1: can't allocate resource
#
[    1.068774] pci 0000:01:0e.0: BAR 2: can't allocate resource
#
[    1.068781] pci 0000:01:0f.0: BAR 0: can't allocate resource
#
[    1.068785] pci 0000:01:0f.0: BAR 1: can't allocate resource
#
[    1.068789] pci 0000:01:0f.0: BAR 2: can't allocate resource
#
[    1.068796] pci 0000:01:10.0: BAR 0: can't allocate resource
#
[    1.068800] pci 0000:01:10.0: BAR 1: can't allocate resource
#
[    1.068804] pci 0000:01:10.0: BAR 2: can't allocate resource
#
[    1.068811] pci 0000:01:11.0: BAR 0: can't allocate resource
#
[    1.068815] pci 0000:01:11.0: BAR 1: can't allocate resource
#
[    1.068819] pci 0000:01:11.0: BAR 2: can't allocate resource
#
[    1.068826] pci 0000:01:12.0: BAR 0: can't allocate resource
#
[    1.068830] pci 0000:01:12.0: BAR 1: can't allocate resource
#
[    1.068834] pci 0000:01:12.0: BAR 2: can't allocate resource
#
[    1.068840] pci 0000:01:13.0: BAR 0: can't allocate resource
#
[    1.068844] pci 0000:01:13.0: BAR 1: can't allocate resource
#
[    1.068848] pci 0000:01:13.0: BAR 2: can't allocate resource
#
[    1.068855] pci 0000:01:14.0: BAR 0: can't allocate resource
#
[    1.068859] pci 0000:01:14.0: BAR 1: can't allocate resource
#
[    1.068863] pci 0000:01:14.0: BAR 2: can't allocate resource
#
[    1.068870] pci 0000:01:15.0: BAR 0: can't allocate resource
#
[    1.068874] pci 0000:01:15.0: BAR 1: can't allocate resource
#
[    1.068878] pci 0000:01:15.0: BAR 2: can't allocate resource
#
[    1.068885] pci 0000:01:16.0: BAR 0: can't allocate resource
#
[    1.068889] pci 0000:01:16.0: BAR 1: can't allocate resource
#
[    1.068893] pci 0000:01:16.0: BAR 2: can't allocate resource
#
[    1.068900] pci 0000:01:17.0: BAR 0: can't allocate resource
#
[    1.068904] pci 0000:01:17.0: BAR 1: can't allocate resource
#
[    1.068908] pci 0000:01:17.0: BAR 2: can't allocate resource
#
[    1.068915] pci 0000:01:18.0: BAR 0: can't allocate resource
#
[    1.068919] pci 0000:01:18.0: BAR 1: can't allocate resource
#
[    1.068923] pci 0000:01:18.0: BAR 2: can't allocate resource
#
[    1.068929] pci 0000:01:19.0: BAR 0: can't allocate resource
#
[    1.068933] pci 0000:01:19.0: BAR 1: can't allocate resource
#
[    1.068937] pci 0000:01:19.0: BAR 2: can't allocate resource
#
[    1.068945] pci 0000:01:1a.0: BAR 0: can't allocate resource
#
[    1.068949] pci 0000:01:1a.0: BAR 1: can't allocate resource
#
[    1.068952] pci 0000:01:1a.0: BAR 2: can't allocate resource
#
[    1.068959] pci 0000:01:1b.0: BAR 0: can't allocate resource
#
[    1.068963] pci 0000:01:1b.0: BAR 1: can't allocate resource
#
[    1.068967] pci 0000:01:1b.0: BAR 2: can't allocate resource
#
[    1.068974] pci 0000:01:1c.0: BAR 0: can't allocate resource
#
[    1.068978] pci 0000:01:1c.0: BAR 1: can't allocate resource
#
[    1.068982] pci 0000:01:1c.0: BAR 2: can't allocate resource
#
[    1.068989] pci 0000:01:1d.0: BAR 0: can't allocate resource
#
[    1.068993] pci 0000:01:1d.0: BAR 1: can't allocate resource
#
[    1.068997] pci 0000:01:1d.0: BAR 2: can't allocate resource
#
[    1.069004] pci 0000:01:1e.0: BAR 0: can't allocate resource
#
[    1.069008] pci 0000:01:1e.0: BAR 1: can't allocate resource
#
[    1.069012] pci 0000:01:1e.0: BAR 2: can't allocate resource
#
[    1.069018] pci 0000:01:1f.0: BAR 0: can't allocate resource
#
[    1.069022] pci 0000:01:1f.0: BAR 1: can't allocate resource
#
[    1.069026] pci 0000:01:1f.0: BAR 2: can't allocate resource
#
[    1.069259] Bluetooth: Core ver 2.13
#
[    1.069259] NET: Registered protocol family 31
#
[    1.069259] Bluetooth: HCI device and connection manager initialized
#
[    1.069259] Bluetooth: HCI socket layer initialized
#
[    1.069259] NET: Registered protocol family 8
#
[    1.069259] NET: Registered protocol family 20
#
[    1.069259] NetLabel: Initializing
#
[    1.069259] NetLabel:  domain hash size = 128
#
[    1.069259] NetLabel:  protocols = UNLABELED CIPSOv4
#
[    1.069259] NetLabel:  unlabeled traffic allowed by default
#
[    1.069259] AppArmor: AppArmor Filesystem Enabled
#
[    1.069259] pnp: PnP ACPI init
#
[    1.069259] ACPI: bus type pnp registered
#
[    1.069259] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:01.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:01.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:01.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:01.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:01.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:01.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:01.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:02.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:02.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:02.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:02.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:02.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:02.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:02.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:03.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:03.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:03.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:03.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:03.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:03.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:03.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:04.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:04.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:04.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:04.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:04.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:04.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:04.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:05.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:05.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:05.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:05.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:05.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:05.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:05.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:06.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:06.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:06.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:06.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:06.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:06.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:06.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:07.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:07.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:07.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:07.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:07.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:07.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:07.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:08.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:08.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:08.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:08.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:08.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:08.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:08.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:09.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:09.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:09.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:09.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:09.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:09.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:09.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069259] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:0a.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069263] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:0a.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069270] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:0a.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069276] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:0a.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069282] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:0a.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069288] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:0a.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069295] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:0a.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069305] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:0b.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069311] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:0b.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069318] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:0b.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069324] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:0b.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069330] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:0b.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069336] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:0b.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069343] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:0b.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069354] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:0c.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069360] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:0c.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069366] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:0c.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069372] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:0c.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069378] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:0c.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069384] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:0c.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069391] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:0c.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069402] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:0d.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069408] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:0d.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069414] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:0d.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069420] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:0d.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069426] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:0d.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069432] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:0d.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069439] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:0d.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069450] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:0e.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069456] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:0e.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069462] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:0e.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069469] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:0e.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069475] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:0e.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069481] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:0e.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069488] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:0e.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069498] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:0f.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069504] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:0f.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069510] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:0f.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069516] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:0f.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069522] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:0f.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069528] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:0f.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069535] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:0f.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069546] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:10.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069552] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:10.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069558] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:10.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069564] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:10.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069570] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:10.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069576] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:10.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069583] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:10.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069594] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:11.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069600] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:11.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069606] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:11.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069612] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:11.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069618] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:11.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069624] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:11.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069631] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:11.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069642] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:12.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069648] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:12.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069654] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:12.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069660] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:12.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069666] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:12.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069673] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:12.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069679] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:12.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069690] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:13.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069696] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:13.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069702] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:13.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069708] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:13.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069714] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:13.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069722] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:13.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069731] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:13.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069741] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:14.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069748] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:14.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069754] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:14.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069760] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:14.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069766] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:14.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069772] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:14.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069779] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:14.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069789] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:15.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069795] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:15.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069801] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:15.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069808] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:15.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069814] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:15.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069820] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:15.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069827] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:15.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069838] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:16.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069844] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:16.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069850] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:16.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069856] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:16.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069862] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:16.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069868] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:16.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069875] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:16.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069885] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:17.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069891] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:17.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069897] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:17.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069903] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:17.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069909] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:17.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069916] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:17.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069922] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:17.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069933] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:18.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069939] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:18.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069945] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:18.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069952] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:18.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069958] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:18.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069964] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:18.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069971] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:18.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069981] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:19.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069987] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:19.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069993] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:19.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.069999] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:19.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.070005] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:19.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.070012] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:19.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.070018] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:19.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.070029] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:1a.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.070035] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:1a.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.070041] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:1a.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.070047] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:1a.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.070054] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:1a.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.070060] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:1a.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.070066] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:1a.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.070077] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:1b.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.070083] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:1b.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072040] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:1b.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072048] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:1b.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072054] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:1b.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072060] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:1b.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072067] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:1b.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072078] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:1c.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072084] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:1c.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072090] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:1c.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072096] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:1c.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072102] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:1c.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072108] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:1c.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072115] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:1c.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072125] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:1d.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072131] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:1d.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072137] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:1d.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072143] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:1d.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072149] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:1d.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072155] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:1d.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072161] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:1d.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072172] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:1e.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072178] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:1e.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072183] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:1e.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072189] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:1e.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072195] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:1e.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072201] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:1e.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072208] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:1e.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072218] pnp 00:00: mem resource (0xcc000-0xcffff) overlaps 0000:01:1f.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072224] pnp 00:00: mem resource (0xf0000-0xf7fff) overlaps 0000:01:1f.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072230] pnp 00:00: mem resource (0xf8000-0xfbfff) overlaps 0000:01:1f.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072236] pnp 00:00: mem resource (0xfc000-0xfffff) overlaps 0000:01:1f.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072242] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:01:1f.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072248] pnp 00:00: mem resource (0x100000-0x1ffeffff) overlaps 0000:01:1f.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.072254] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:01:1f.0 BAR 0 (0x0-0x3ffffff), disabling
#
[    1.073425] pnp 00:02: io resource (0x10-0x1f) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
#
[    1.073433] pnp 00:02: io resource (0x22-0x3f) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
#
[    1.073438] pnp 00:02: io resource (0x44-0x5f) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
#
[    1.073444] pnp 00:02: io resource (0x62-0x63) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
#
[    1.073450] pnp 00:02: io resource (0x65-0x6f) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
#
[    1.073456] pnp 00:02: io resource (0x74-0x7f) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
#
[    1.073461] pnp 00:02: io resource (0x91-0x93) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
#
[    1.073467] pnp 00:02: io resource (0xa2-0xbf) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
#
[    1.073473] pnp 00:02: io resource (0xe0-0xef) overlaps 0000:01:00.0 BAR 1 (0x0-0xff), disabling
#
[    1.073481] pnp 00:02: io resource (0x10-0x1f) overlaps 0000:01:01.0 BAR 1 (0x0-0xff), disabling
#
[    1.073487] pnp 00:02: io resource (0x22-0x3f) overlaps 0000:01:01.0 BAR 1 (0x0-0xff), disabling
#
[    1.073492] pnp 00:02: io resource (0x44-0x5f) overlaps 0000:01:01.0 BAR 1 (0x0-0xff), disabling
#
[    1.073498] pnp 00:02: io resource (0x62-0x63) overlaps 0000:01:01.0 BAR 1 (0x0-0xff), disabling
#
[    1.073504] pnp 00:02: io resource (0x65-0x6f) overlaps 0000:01:01.0 BAR 1 (0x0-0xff), disabling
#
[    1.073509] pnp 00:02: io resource (0x74-0x7f) overlaps 0000:01:01.0 BAR 1 (0x0-0xff), disabling
#
[    1.073515] pnp 00:02: io resource (0x91-0x93) overlaps 0000:01:01.0 BAR 1 (0x0-0xff), disabling
#
[    1.073520] pnp 00:02: io resource (0xa2-0xbf) overlaps 0000:01:01.0 BAR 1 (0x0-0xff), disabling
#
[    1.073526] pnp 00:02: io resource (0xe0-0xef) overlaps 0000:01:01.0 BAR 1 (0x0-0xff), disabling
#
[    1.073534] pnp 00:02: io resource (0x10-0x1f) overlaps 0000:01:02.0 BAR 1 (0x0-0xff), disabling
#
[    1.073540] pnp 00:02: io resource (0x22-0x3f) overlaps 0000:01:02.0 BAR 1 (0x0-0xff), disabling
#
[    1.073545] pnp 00:02: io resource (0x44-0x5f) overlaps 0000:01:02.0 BAR 1 (0x0-0xff), disabling
#
[    1.073551] pnp 00:02: io resource (0x62-0x63) overlaps 0000:01:02.0 BAR 1 (0x0-0xff), disabling
#
[    1.073557] pnp 00:02: io resource (0x65-0x6f) overlaps 0000:01:02.0 BAR 1 (0x0-0xff), disabling
#
[    1.073562] pnp 00:02: io resource (0x74-0x7f) overlaps 0000:01:02.0 BAR 1 (0x0-0xff), disabling
#
[    1.073568] pnp 00:02: io resource (0x91-0x93) overlaps 0000:01:02.0 BAR 1 (0x0-0xff), disabling
#
[    1.073574] pnp 00:02: io resource (0xa2-0xbf) overlaps 0000:01:02.0 BAR 1 (0x0-0xff), disabling
#
[    1.073579] pnp 00:02: io resource (0xe0-0xef) overlaps 0000:01:02.0 BAR 1 (0x0-0xff), disabling
#
[    1.073587] pnp 00:02: io resource (0x10-0x1f) overlaps 0000:01:03.0 BAR 1 (0x0-0xff), disabling
#
[    1.073593] pnp 00:02: io resource (0x22-0x3f) overlaps 0000:01:03.0 BAR 1 (0x0-0xff), disabling
#
[    1.073599] pnp 00:02: io resource (0x44-0x5f) overlaps 0000:01:03.0 BAR 1 (0x0-0xff), disabling
#
[    1.073604] pnp 00:02: io resource (0x62-0x63) overlaps 0000:01:03.0 BAR 1 (0x0-0xff), disabling
#
[    1.073610] pnp 00:02: io resource (0x65-0x6f) overlaps 0000:01:03.0 BAR 1 (0x0-0xff), disabling
#
[    1.073615] pnp 00:02: io resource (0x74-0x7f) overlaps 0000:01:03.0 BAR 1 (0x0-0xff), disabling
#
[    1.073621] pnp 00:02: io resource (0x91-0x93) overlaps 0000:01:03.0 BAR 1 (0x0-0xff), disabling
#
[    1.073627] pnp 00:02: io resource (0xa2-0xbf) overlaps 0000:01:03.0 BAR 1 (0x0-0xff), disabling
#
[    1.073632] pnp 00:02: io resource (0xe0-0xef) overlaps 0000:01:03.0 BAR 1 (0x0-0xff), disabling
#
[    1.073641] pnp 00:02: io resource (0x10-0x1f) overlaps 0000:01:04.0 BAR 1 (0x0-0xff), disabling
#
[    1.073646] pnp 00:02: io resource (0x22-0x3f) overlaps 0000:01:04.0 BAR 1 (0x0-0xff), disabling
#
[    1.073652] pnp 00:02: io resource (0x44-0x5f) overlaps 0000:01:04.0 BAR 1 (0x0-0xff), disabling
#
[    1.073658] pnp 00:02: io resource (0x62-0x63) overlaps 0000:01:04.0 BAR 1 (0x0-0xff), disabling
#
[    1.073663] pnp 00:02: io resource (0x65-0x6f) overlaps 0000:01:04.0 BAR 1 (0x0-0xff), disabling
#
[    1.073669] pnp 00:02: io resource (0x74-0x7f) overlaps 0000:01:04.0 BAR 1 (0x0-0xff), disabling
#
[    1.073675] pnp 00:02: io resource (0x91-0x93) overlaps 0000:01:04.0 BAR 1 (0x0-0xff), disabling
#
[    1.073680] pnp 00:02: io resource (0xa2-0xbf) overlaps 0000:01:04.0 BAR 1 (0x0-0xff), disabling
#
[    1.073686] pnp 00:02: io resource (0xe0-0xef) overlaps 0000:01:04.0 BAR 1 (0x0-0xff), disabling
#
[    1.073694] pnp 00:02: io resource (0x10-0x1f) overlaps 0000:01:05.0 BAR 1 (0x0-0xff), disabling
#
[    1.073700] pnp 00:02: io resource (0x22-0x3f) overlaps 0000:01:05.0 BAR 1 (0x0-0xff), disabling
#
[    1.073706] pnp 00:02: io resource (0x44-0x5f) overlaps 0000:01:05.0 BAR 1 (0x0-0xff), disabling
#
[    1.073711] pnp 00:02: io resource (0x62-0x63) overlaps 0000:01:05.0 BAR 1 (0x0-0xff), disabling
#
[    1.073717] pnp 00:02: io resource (0x65-0x6f) overlaps 0000:01:05.0 BAR 1 (0x0-0xff), disabling
#
[    1.073722] pnp 00:02: io resource (0x74-0x7f) overlaps 0000:01:05.0 BAR 1 (0x0-0xff), disabling
#
[    1.073728] pnp 00:02: io resource (0x91-0x93) overlaps 0000:01:05.0 BAR 1 (0x0-0xff), disabling
#
[    1.073734] pnp 00:02: io resource (0xa2-0xbf) overlaps 0000:01:05.0 BAR 1 (0x0-0xff), disabling
#
[    1.073740] pnp 00:02: io resource (0xe0-0xef) overlaps 0000:01:05.0 BAR 1 (0x0-0xff), disabling
#
[    1.073748] pnp 00:02: io resource (0x10-0x1f) overlaps 0000:01:06.0 BAR 1 (0x0-0xff), disabling
#
[    1.073754] pnp 00:02: io resource (0x22-0x3f) overlaps 0000:01:06.0 BAR 1 (0x0-0xff), disabling
#
[    1.073759] pnp 00:02: io resource (0x44-0x5f) overlaps 0000:01:06.0 BAR 1 (0x0-0xff), disabling
#
[    1.073765] pnp 00:02: io resource (0x62-0x63) overlaps 0000:01:06.0 BAR 1 (0x0-0xff), disabling
#
[    1.073770] pnp 00:02: io resource (0x65-0x6f) overlaps 0000:01:06.0 BAR 1 (0x0-0xff), disabling
#
[    1.073776] pnp 00:02: io resource (0x74-0x7f) overlaps 0000:01:06.0 BAR 1 (0x0-0xff), disabling
#
[    1.073782] pnp 00:02: io resource (0x91-0x93) overlaps 0000:01:06.0 BAR 1 (0x0-0xff), disabling
#
[    1.073787] pnp 00:02: io resource (0xa2-0xbf) overlaps 0000:01:06.0 BAR 1 (0x0-0xff), disabling
#
[    1.073793] pnp 00:02: io resource (0xe0-0xef) overlaps 0000:01:06.0 BAR 1 (0x0-0xff), disabling
#
[    1.073801] pnp 00:02: io resource (0x10-0x1f) overlaps 0000:01:07.0 BAR 1 (0x0-0xff), disabling
#
[    1.073807] pnp 00:02: io resource (0x22-0x3f) overlaps 0000:01:07.0 BAR 1 (0x0-0xff), disabling
#
[    1.073813] pnp 00:02: io resource (0x44-0x5f) overlaps 0000:01:07.0 BAR 1 (0x0-0xff), disabling
#
[    1.073818] pnp 00:02: io resource (0x62-0x63) overlaps 0000:01:07.0 BAR 1 (0x0-0xff), disabling
#
[    1.073824] pnp 00:02: io resource (0x65-0x6f) overlaps 0000:01:07.0 BAR 1 (0x0-0xff), disabling
#
[    1.073830] pnp 00:02: io resource (0x74-0x7f) overlaps 0000:01:07.0 BAR 1 (0x0-0xff), disabling
#
[    1.073835] pnp 00:02: io resource (0x91-0x93) overlaps 0000:01:07.0 BAR 1 (0x0-0xff), disabling
#
[    1.073841] pnp 00:02: io resource (0xa2-0xbf) overlaps 0000:01:07.0 BAR 1 (0x0-0xff), disabling
#
[    1.073847] pnp 00:02: io resource (0xe0-0xef) overlaps 0000:01:07.0 BAR 1 (0x0-0xff), disabling
#
[    1.073854] pnp 00:02: io resource (0x10-0x1f) overlaps 0000:01:08.0 BAR 1 (0x0-0xff), disabling
#
[    1.073860] pnp 00:02: io resource (0x22-0x3f) overlaps 0000:01:08.0 BAR 1 (0x0-0xff), disabling
#
[    1.073866] pnp 00:02: io resource (0x44-0x5f) overlaps 0000:01:08.0 BAR 1 (0x0-0xff), disabling
#
[    1.073871] pnp 00:02: io resource (0x62-0x63) overlaps 0000:01:08.0 BAR 1 (0x0-0xff), disabling
#
[    1.073877] pnp 00:02: io resource (0x65-0x6f) overlaps 0000:01:08.0 BAR 1 (0x0-0xff), disabling
#
[    1.073882] pnp 00:02: io resource (0x74-0x7f) overlaps 0000:01:08.0 BAR 1 (0x0-0xff), disabling
#
[    1.073888] pnp 00:02: io resource (0x91-0x93) overlaps 0000:01:08.0 BAR 1 (0x0-0xff), disabling
#
[    1.073894] pnp 00:02: io resource (0xa2-0xbf) overlaps 0000:01:08.0 BAR 1 (0x0-0xff), disabling
#
[    1.073900] pnp 00:02: io resource (0xe0-0xef) overlaps 0000:01:08.0 BAR 1 (0x0-0xff), disabling
#
[    1.073907] pnp 00:02: io resource (0x10-0x1f) overlaps 0000:01:09.0 BAR 1 (0x0-0xff), disabling
#
[    1.073913] pnp 00:02: io resource (0x22-0x3f) overlaps 0000:01:09.0 BAR 1 (0x0-0xff), disabling
#
[    1.073919] pnp 00:02: io resource (0x44-0x5f) overlaps 0000:01:09.0 BAR 1 (0x0-0xff), disabling
#
[    1.073924] pnp 00:02: io resource (0x62-0x63) overlaps 0000:01:09.0 BAR 1 (0x0-0xff), disabling
#
[    1.073930] pnp 00:02: io resource (0x65-0x6f) overlaps 0000:01:09.0 BAR 1 (0x0-0xff), disabling
#
[    1.073938] pnp 00:02: io resource (0x74-0x7f) overlaps 0000:01:09.0 BAR 1 (0x0-0xff), disabling
#
[    1.073944] pnp 00:02: io resource (0x91-0x93) overlaps 0000:01:09.0 BAR 1 (0x0-0xff), disabling
#
[    1.073952] pnp 00:02: io resource (0xa2-0xbf) overlaps 0000:01:09.0 BAR 1 (0x0-0xff), disabling
#
[    1.073961] pnp 00:02: io resource (0xe0-0xef) overlaps 0000:01:09.0 BAR 1 (0x0-0xff), disabling
#
[    1.073969] pnp 00:02: io resource (0x10-0x1f) overlaps 0000:01:0a.0 BAR 1 (0x0-0xff), disabling
#
[    1.073975] pnp 00:02: io resource (0x22-0x3f) overlaps 0000:01:0a.0 BAR 1 (0x0-0xff), disabling
#
[    1.073980] pnp 00:02: io resource (0x44-0x5f) overlaps 0000:01:0a.0 BAR 1 (0x0-0xff), disabling
#
[    1.073986] pnp 00:02: io resource (0x62-0x63) overlaps 0000:01:0a.0 BAR 1 (0x0-0xff), disabling
#
[    1.073992] pnp 00:02: io resource (0x65-0x6f) overlaps 0000:01:0a.0 BAR 1 (0x0-0xff), disabling
#
[    1.073997] pnp 00:02: io resource (0x74-0x7f) overlaps 0000:01:0a.0 BAR 1 (0x0-0xff), disabling
#
[    1.074003] pnp 00:02: io resource (0x91-0x93) overlaps 0000:01:0a.0 BAR 1 (0x0-0xff), disabling
#
[    1.074009] pnp 00:02: io resource (0xa2-0xbf) overlaps 0000:01:0a.0 BAR 1 (0x0-0xff), disabling
#
[    1.074014] pnp 00:02: io resource (0xe0-0xef) overlaps 0000:01:0a.0 BAR 1 (0x0-0xff), disabling
#
[    1.074023] pnp 00:02: io resource (0x10-0x1f) overlaps 0000:01:0b.0 BAR 1 (0x0-0xff), disabling
#
[    1.074028] pnp 00:02: io resource (0x22-0x3f) overlaps 0000:01:0b.0 BAR 1 (0x0-0xff), disabling
#
[    1.074034] pnp 00:02: io resource (0x44-0x5f) overlaps 0000:01:0b.0 BAR 1 (0x0-0xff), disabling
#
[    1.074040] pnp 00:02: io resource (0x62-0x63) overlaps 0000:01:0b.0 BAR 1 (0x0-0xff), disabling
#
[    1.07


xorg.0.log

> 
#
X.Org X Server 1.6.0
#
Release Date: 2009-2-25
#
X Protocol Version 11, Revision 0
#
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
#
Current Operating System: Linux crunchbang 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686
#
Build Date: 09 April 2009  02:10:02AM
#
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd)
#
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
#
        to make sure that you have the latest version.
#
Markers: (--) probed, (**) from config file, (==) default setting,
#
        (++) from command line, (!!) notice, (II) informational,
#
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
#
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan  1 04:52:14 2002
#
(==) Using config file: "/etc/X11/xorg.conf"
#
(==) No Layout section.  Using the first Screen section.
#
(**) |-->Screen "Default Screen" (0)
#
(**) |   |-->Monitor "Configured Monitor"
#
(**) |   |-->Device "Configured Video Device"
#
(==) Automatically adding devices
#
(==) Automatically enabling devices
#
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
#
        Entry deleted from font path.
#
(==) FontPath set to:
#
        /usr/share/fonts/X11/misc,
#
        /usr/share/fonts/X11/100dpi/:unscaled,
#
        /usr/share/fonts/X11/75dpi/:unscaled,
#
        /usr/share/fonts/X11/Type1,
#
        /usr/share/fonts/X11/100dpi,
#
        /usr/share/fonts/X11/75dpi,
#
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
#
        built-ins
#
(==) ModulePath set to "/usr/lib/xorg/modules"
#
(II) Cannot locate a core pointer device.
#
(II) Cannot locate a core keyboard device.
#
(II) The server relies on HAL to provide the list of input devices.
#
        If no devices become available, reconfigure HAL or disable AllowEmptyInput.
#
(II) Loader magic: 0x3bc0
#
(II) Module ABI versions:
#
        X.Org ANSI C Emulation: 0.4
#
        X.Org Video Driver: 5.0
#
        X.Org XInput driver : 4.0
#
        X.Org Server Extension : 2.0
#
(II) Loader running on linux
#
(--) using VT number 9
#
 
#
(--) PCI: (0@1:0:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0xe4000000/67108864, 0xe907c000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:1:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0x68000000/67108864, 0xe8400000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:2:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0x6c000000/67108864, 0xe8404000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:3:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0x70000000/67108864, 0xe8408000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:4:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0x74000000/67108864, 0xe840c000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:5:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0x78000000/67108864, 0xe8410000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:6:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0x7c000000/67108864, 0xe8414000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:7:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0x80000000/67108864, 0xe8418000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:8:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0x84000000/67108864, 0xe841c000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:9:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0x88000000/67108864, 0xe8420000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:10:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0x8c000000/67108864, 0xe8424000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:11:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0x90000000/67108864, 0xe8428000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:12:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0x94000000/67108864, 0xe842c000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:13:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0x98000000/67108864, 0xe8430000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:14:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0x9c000000/67108864, 0xe8434000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:15:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0xa0000000/67108864, 0xe8438000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:16:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0xa4000000/67108864, 0xe843c000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:17:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0xa8000000/67108864, 0xe8440000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:18:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0xac000000/67108864, 0xe8444000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:19:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0xb0000000/67108864, 0xe8448000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:20:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0xb4000000/67108864, 0xe844c000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:21:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0xb8000000/67108864, 0xe8450000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:22:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0xbc000000/67108864, 0xe8454000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:23:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0xc0000000/67108864, 0xe8458000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:24:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0xc4000000/67108864, 0xe845c000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:25:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0xc8000000/67108864, 0xe8460000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:26:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0xcc000000/67108864, 0xe8464000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:27:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0xd0000000/67108864, 0xe8468000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:28:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0xd4000000/67108864, 0xe846c000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:29:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0xd8000000/67108864, 0xe8470000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:30:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0xdc000000/67108864, 0xe8474000/16384, BIOS @ 0x????????/131072
#
(--) PCI: (0@1:31:0) ATI Technologies Inc Rage 128 PD/PRO TMDS rev 0, Mem @ 0xe0000000/67108864, 0xe8478000/16384, BIOS @ 0x????????/131072
#
(II) Open ACPI successful (/var/run/acpid.socket)
#
(II) System resource ranges:
#
        [0] -1  0 0xffffffff - 0xffffffff (0x1) MX[B]
#
        [1] -1  0 0x000f0000 - 0x000fffff (0x10000) MX[B]
#
        [2] -1  0 0x000c0000 - 0x000effff (0x30000) MX[B]
#
        [3] -1  0 0x00000000 - 0x0009ffff (0xa0000) MX[B]
#
        [4] -1  0 0x0000ffff - 0x0000ffff (0x1) IX[B]
#
        [5] -1  0 0x00000000 - 0x00000000 (0x1) IX[B]
#
(II) LoadModule: "extmod"
#
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
#
(II) Module extmod: vendor="X.Org Foundation"
#
        compiled for 1.6.0, module version = 1.0.0
#
        Module class: X.Org Server Extension
#
        ABI class: X.Org Server Extension, version 2.0
#
(II) Loading extension MIT-SCREEN-SAVER
#
(II) Loading extension XFree86-VidModeExtension
#
(II) Loading extension XFree86-DGA
#
(II) Loading extension DPMS
#
(II) Loading extension XVideo
#
(II) Loading extension XVideo-MotionCompensation
#
(II) Loading extension X-Resource
#
(II) LoadModule: "dbe"
#
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
#
(II) Module dbe: vendor="X.Org Foundation"
#
        compiled for 1.6.0, module version = 1.0.0
#
        Module class: X.Org Server Extension
#
        ABI class: X.Org Server Extension, version 2.0
#
(II) Loading extension DOUBLE-BUFFER
#
(II) LoadModule: "glx"
#
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
#
(II) Module glx: vendor="X.Org Foundation"
#
        compiled for 1.6.0, module version = 1.0.0
#
        ABI class: X.Org Server Extension, version 2.0
#
(==) AIGLX enabled
#
(II) Loading extension GLX
#
(II) LoadModule: "record"
#
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
#
(II) Module record: vendor="X.Org Foundation"
#
        compiled for 1.6.0, module version = 1.13.0
#
        Module class: X.Org Server Extension
#
        ABI class: X.Org Server Extension, version 2.0
#
(II) Loading extension RECORD
#
(II) LoadModule: "dri"
#
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
#
(II) Module dri: vendor="X.Org Foundation"
#
        compiled for 1.6.0, module version = 1.0.0
#
        ABI class: X.Org Server Extension, version 2.0
#
(II) Loading extension XFree86-DRI
#
(II) LoadModule: "dri2"
#
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
#
(II) Module dri2: vendor="X.Org Foundation"
#
        compiled for 1.6.0, module version = 1.0.0
#
        ABI class: X.Org Server Extension, version 2.0
#
(II) Loading extension DRI2
#
Primary device is not PCI
#
(==) Matched vesa for the autoconfigured driver
#
(==) Assigned the driver to the xf86ConfigLayout
#
(II) LoadModule: "vesa"
#
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
#
(II) Module vesa: vendor="X.Org Foundation"
#
        compiled for 1.5.99.902, module version = 1.3.0
#
        Module class: X.Org Video Driver
#
        ABI class: X.Org Video Driver, version 5.0
#
(II) VESA: driver for VESA chipsets: vesa
#
(WW) Falling back to old probe method for vesa
#
(EE) No devices detected.
#
 
#
Fatal server error:
#
no screens found
#
 
#
Please consult the The X.Org Foundation support
#
         at [http://wiki.x.org](http://wiki.x.org)
#
 for help.
#
Please also check the log file at "/var/log/Xorg.0.log" for additional information.
#
 
#
 ddxSigGiveUp: Closing log 

---

### Post by fateinabox on 2009-09-02
Take a look at the thread i just wrote the problem your having seems similiar in nature. [http://ubuntuforums.org/showthread.php?t=1256691]("http://ubuntuforums.org/showthread.php?t=1256691")

---

