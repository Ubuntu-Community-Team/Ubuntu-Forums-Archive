---
title: "attempt to access beyond end of device, annoyances"
date: 2009-02-18
forum: Hardware
---

### Post by eilenbeb on 2009-02-18
Athalon64 FX-51
Nvidia nForce3 mainboard
SiI 3112 SATARAID fakeraid controller, onboard
2 SATA drives as RAID0 (where windows still lives)
--->sda
--->sdb
2 IDE drives (each with separate installs of Ubuntu)
--->sdc
--->sdd

In Hardy (2.6.24-19-generic unmodified), each disk driver that loads keeps trying to play with the individual SATA drives, oblivious to the fact that they are part of a striped array.
I get the "attempt to ..." a lot while booting.  No real problem in 2.6.24-19-generic, just annoying.

The -real- annoyance comes in when I try to use a newer kernel.  (Intrepid just barely boots on my system)
In all of the newer kernels I've tried (I've tried 10+ other different distro's as well) the drivers choke, and booting takes forever.  If it boots at all.
The 'sr' driver (isn't that for cdrom drives?) chokes on -every- drive in my system.

Here's my kern.log:
```

Feb 18 12:55:59 uCore64 kernel: Cannot find map file.
Feb 18 12:55:59 uCore64 kernel: Loaded 60882 symbols from 75 modules.
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Command line: BOOT_IMAGE=UbuntuIce2 root=831
Feb 18 12:55:59 uCore64 kernel: [    0.000000] BIOS-provided physical RAM map:
Feb 18 12:55:59 uCore64 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb 18 12:55:59 uCore64 kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb 18 12:55:59 uCore64 kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Feb 18 12:55:59 uCore64 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
Feb 18 12:55:59 uCore64 kernel: [    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
Feb 18 12:55:59 uCore64 kernel: [    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
Feb 18 12:55:59 uCore64 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Feb 18 12:55:59 uCore64 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb 18 12:55:59 uCore64 kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Entering add_active_range(0, 256, 262128) 1 entries of 3200 used
Feb 18 12:55:59 uCore64 kernel: [    0.000000] end_pfn_map = 1048576
Feb 18 12:55:59 uCore64 kernel: [    0.000000] DMI 2.3 present.
Feb 18 12:55:59 uCore64 kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6C00 checksum 0
Feb 18 12:55:59 uCore64 kernel: [    0.000000] ACPI: RSDP 000F6C00, 0014 (r0 Nvidia)
Feb 18 12:55:59 uCore64 kernel: [    0.000000] ACPI: RSDT 3FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
Feb 18 12:55:59 uCore64 kernel: [    0.000000] ACPI: FACP 3FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
Feb 18 12:55:59 uCore64 kernel: [    0.000000] ACPI: DSDT 3FFF30C0, 4B22 (r1 NVIDIA AWRDACPI     1000 MSFT  100000C)
Feb 18 12:55:59 uCore64 kernel: [    0.000000] ACPI: FACS 3FFF0000, 0040
Feb 18 12:55:59 uCore64 kernel: [    0.000000] ACPI: APIC 3FFF7C00, 005A (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Feb 18 12:55:59 uCore64 kernel: [    0.000000] CPU has 1 num_cores
Feb 18 12:55:59 uCore64 kernel: [    0.000000] No NUMA configuration found
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Faking a node at 0000000000000000-000000003fff0000
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Entering add_active_range(0, 256, 262128) 1 entries of 3200 used
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000003fff0000
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Zone PFN ranges:
Feb 18 12:55:59 uCore64 kernel: [    0.000000]   DMA             0 ->     4096
Feb 18 12:55:59 uCore64 kernel: [    0.000000]   DMA32        4096 ->  1048576
Feb 18 12:55:59 uCore64 kernel: [    0.000000]   Normal    1048576 ->  1048576
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Movable zone start PFN for each node
Feb 18 12:55:59 uCore64 kernel: [    0.000000] early_node_map[2] active PFN ranges
Feb 18 12:55:59 uCore64 kernel: [    0.000000]     0:        0 ->      159
Feb 18 12:55:59 uCore64 kernel: [    0.000000]     0:      256 ->   262128
Feb 18 12:55:59 uCore64 kernel: [    0.000000] On node 0 totalpages: 262031
Feb 18 12:55:59 uCore64 kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Feb 18 12:55:59 uCore64 kernel: [    0.000000]   DMA zone: 3040 pages reserved
Feb 18 12:55:59 uCore64 kernel: [    0.000000]   DMA zone: 903 pages, LIFO batch:0
Feb 18 12:55:59 uCore64 kernel: [    0.000000]   DMA32 zone: 3527 pages used for memmap
Feb 18 12:55:59 uCore64 kernel: [    0.000000]   DMA32 zone: 254505 pages, LIFO batch:31
Feb 18 12:55:59 uCore64 kernel: [    0.000000]   Normal zone: 0 pages used for memmap
Feb 18 12:55:59 uCore64 kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Feb 18 12:55:59 uCore64 kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Feb 18 12:55:59 uCore64 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Feb 18 12:55:59 uCore64 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 18 12:55:59 uCore64 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Processor #0 (Bootup-CPU)
Feb 18 12:55:59 uCore64 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Feb 18 12:55:59 uCore64 kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Feb 18 12:55:59 uCore64 kernel: [    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
Feb 18 12:55:59 uCore64 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb 18 12:55:59 uCore64 kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
Feb 18 12:55:59 uCore64 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb 18 12:55:59 uCore64 kernel: [    0.000000] ACPI: IRQ9 used by override.
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Setting APIC routing to flat
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb 18 12:55:59 uCore64 kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Feb 18 12:55:59 uCore64 kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Feb 18 12:55:59 uCore64 kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
Feb 18 12:55:59 uCore64 kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Feb 18 12:55:59 uCore64 kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 255408
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Policy zone: DMA32
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=UbuntuIce2 root=831
Feb 18 12:55:59 uCore64 kernel: [    0.000000] Initializing CPU#0
Feb 18 12:55:59 uCore64 kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Feb 18 12:55:59 uCore64 kernel: [    0.000000] TSC calibrated against PM_TIMER
Feb 18 12:55:59 uCore64 kernel: [   32.728679] time.c: Detected 2194.337 MHz processor.
Feb 18 12:55:59 uCore64 kernel: [   32.730791] Console: colour VGA+ 80x25
Feb 18 12:55:59 uCore64 kernel: [   32.730794] console [tty0] enabled
Feb 18 12:55:59 uCore64 kernel: [   32.734887] Checking aperture...
Feb 18 12:55:59 uCore64 kernel: [   32.734949] CPU 0: aperture @ a0000000 size 512 MB
Feb 18 12:55:59 uCore64 kernel: [   32.745650] Memory: 1021484k/1048512k available (2489k kernel code, 26640k reserved, 1318k data, 320k init)
Feb 18 12:55:59 uCore64 kernel: [   32.745760] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Feb 18 12:55:59 uCore64 kernel: [   32.822539] Calibrating delay using timer specific routine.. 4391.48 BogoMIPS (lpj=8782977)
Feb 18 12:55:59 uCore64 kernel: [   32.822694] Security Framework initialized
Feb 18 12:55:59 uCore64 kernel: [   32.822762] SELinux:  Disabled at boot.
Feb 18 12:55:59 uCore64 kernel: [   32.822836] AppArmor: AppArmor initialized
Feb 18 12:55:59 uCore64 kernel: [   32.822900] Failure registering capabilities with primary security module.
Feb 18 12:55:59 uCore64 kernel: [   32.823051] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
Feb 18 12:55:59 uCore64 kernel: [   32.823899] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
Feb 18 12:55:59 uCore64 kernel: [   32.824329] Mount-cache hash table entries: 256
Feb 18 12:55:59 uCore64 kernel: [   32.824513] Initializing cgroup subsys ns
Feb 18 12:55:59 uCore64 kernel: [   32.824578] Initializing cgroup subsys cpuacct
Feb 18 12:55:59 uCore64 kernel: [   32.824650] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb 18 12:55:59 uCore64 kernel: [   32.824716] CPU: L2 Cache: 1024K (64 bytes/line)
Feb 18 12:55:59 uCore64 kernel: [   32.824781] CPU 0/0 -> Node 0
Feb 18 12:55:59 uCore64 kernel: [   32.824860] SMP alternatives: switching to UP code
Feb 18 12:55:59 uCore64 kernel: [   32.825436] Freeing SMP alternatives: 24k freed
Feb 18 12:55:59 uCore64 kernel: [   32.826140] Early unpacking initramfs... done
Feb 18 12:55:59 uCore64 kernel: [   33.081413] ACPI: Core revision 20070126
Feb 18 12:55:59 uCore64 kernel: [   33.081527] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Feb 18 12:55:59 uCore64 kernel: [   33.124053] Using local APIC timer interrupts.
Feb 18 12:55:59 uCore64 kernel: [   33.169627] APIC timer calibration result 12467827
Feb 18 12:55:59 uCore64 kernel: [   33.169629] Detected 12.467 MHz APIC timer.
Feb 18 12:55:59 uCore64 kernel: [   33.169736] Brought up 1 CPUs
Feb 18 12:55:59 uCore64 kernel: [   33.169862] CPU0 attaching sched-domain:
Feb 18 12:55:59 uCore64 kernel: [   33.169864]  domain 0: span 01
Feb 18 12:55:59 uCore64 kernel: [   33.169865]   groups: 01
Feb 18 12:55:59 uCore64 kernel: [   33.169992] net_namespace: 120 bytes
Feb 18 12:55:59 uCore64 kernel: [   33.170399] Time: 12:55:35  Date: 02/18/09
Feb 18 12:55:59 uCore64 kernel: [   33.170485] NET: Registered protocol family 16
Feb 18 12:55:59 uCore64 kernel: [   33.170695] ACPI: bus type pci registered
Feb 18 12:55:59 uCore64 kernel: [   33.170814] PCI: Using configuration type 1
Feb 18 12:55:59 uCore64 kernel: [   33.171758] ACPI: EC: Look up EC in DSDT
Feb 18 12:55:59 uCore64 kernel: [   33.175921] ACPI: Interpreter enabled
Feb 18 12:55:59 uCore64 kernel: [   33.175984] ACPI: (supports S0 S3 S4 S5)
Feb 18 12:55:59 uCore64 kernel: [   33.176251] ACPI: Using IOAPIC for interrupt routing
Feb 18 12:55:59 uCore64 kernel: [   33.182731] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb 18 12:55:59 uCore64 kernel: [   33.183364] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Feb 18 12:55:59 uCore64 kernel: [   33.183484] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Feb 18 12:55:59 uCore64 kernel: [   33.183724] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
Feb 18 12:55:59 uCore64 kernel: [   33.221043] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Feb 18 12:55:59 uCore64 kernel: [   33.221875] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Feb 18 12:55:59 uCore64 kernel: [   33.222705] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.223630] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.224558] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Feb 18 12:55:59 uCore64 kernel: [   33.225387] ACPI: PCI Interrupt Link [LUBA] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Feb 18 12:55:59 uCore64 kernel: [   33.226219] ACPI: PCI Interrupt Link [LUBB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Feb 18 12:55:59 uCore64 kernel: [   33.227046] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Feb 18 12:55:59 uCore64 kernel: [   33.227872] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.228797] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.229724] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.230650] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Feb 18 12:55:59 uCore64 kernel: [   33.231480] ACPI: PCI Interrupt Link [LUB2] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Feb 18 12:55:59 uCore64 kernel: [   33.232308] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.233233] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.234161] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.235092] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.235994] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
Feb 18 12:55:59 uCore64 kernel: [   33.236293] ACPI: PCI Interrupt Link [APC2] (IRQs *17)
Feb 18 12:55:59 uCore64 kernel: [   33.236592] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.236941] ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.237290] ACPI: PCI Interrupt Link [APC5] (IRQs *16)
Feb 18 12:55:59 uCore64 kernel: [   33.237635] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
Feb 18 12:55:59 uCore64 kernel: [   33.238127] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
Feb 18 12:55:59 uCore64 kernel: [   33.238614] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
Feb 18 12:55:59 uCore64 kernel: [   33.239100] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.239637] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.240174] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.240671] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
Feb 18 12:55:59 uCore64 kernel: [   33.241010] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
Feb 18 12:55:59 uCore64 kernel: [   33.241497] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.242036] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.242573] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.243116] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22) *0, disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.243614] ACPI: Power Resource [ISAV] (on)
Feb 18 12:55:59 uCore64 kernel: [   33.243712] Linux Plug and Play Support v0.97 (c) Adam Belay
Feb 18 12:55:59 uCore64 kernel: [   33.243797] pnp: PnP ACPI init
Feb 18 12:55:59 uCore64 kernel: [   33.243863] ACPI: bus type pnp registered
Feb 18 12:55:59 uCore64 kernel: [   33.246886] pnp: PnP ACPI: found 11 devices
Feb 18 12:55:59 uCore64 kernel: [   33.246950] ACPI: ACPI bus type pnp unregistered
Feb 18 12:55:59 uCore64 kernel: [   33.247193] PCI: Using ACPI for IRQ routing
Feb 18 12:55:59 uCore64 kernel: [   33.247259] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Feb 18 12:55:59 uCore64 kernel: [   33.247341] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
Feb 18 12:55:59 uCore64 kernel: [   33.257604] NET: Registered protocol family 8
Feb 18 12:55:59 uCore64 kernel: [   33.257668] NET: Registered protocol family 20
Feb 18 12:55:59 uCore64 kernel: [   33.257780] agpgart: Detected AGP bridge 0
Feb 18 12:55:59 uCore64 kernel: [   33.257847] agpgart: Setting up Nforce3 AGP.
Feb 18 12:55:59 uCore64 kernel: [   33.280353] agpgart: AGP aperture is 512M @ 0xa0000000
Feb 18 12:55:59 uCore64 kernel: [   33.280481] AppArmor: AppArmor Filesystem Enabled
Feb 18 12:55:59 uCore64 kernel: [   33.281548] Time: tsc clocksource has been installed.
Feb 18 12:55:59 uCore64 kernel: [   33.293563] system 00:00: ioport range 0x1000-0x107f has been reserved
Feb 18 12:55:59 uCore64 kernel: [   33.293630] system 00:00: ioport range 0x1080-0x10ff has been reserved
Feb 18 12:55:59 uCore64 kernel: [   33.295182] system 00:00: ioport range 0x1400-0x147f has been reserved
Feb 18 12:55:59 uCore64 kernel: [   33.295248] system 00:00: ioport range 0x1480-0x14ff has been reserved
Feb 18 12:55:59 uCore64 kernel: [   33.295314] system 00:00: ioport range 0x1800-0x187f has been reserved
Feb 18 12:55:59 uCore64 kernel: [   33.295380] system 00:00: ioport range 0x1880-0x18ff has been reserved
Feb 18 12:55:59 uCore64 kernel: [   33.295451] system 00:01: iomem range 0xd4800-0xd7fff has been reserved
Feb 18 12:55:59 uCore64 kernel: [   33.295517] system 00:01: iomem range 0xf0000-0xf7fff could not be reserved
Feb 18 12:55:59 uCore64 kernel: [   33.295584] system 00:01: iomem range 0xf8000-0xfbfff could not be reserved
Feb 18 12:55:59 uCore64 kernel: [   33.295651] system 00:01: iomem range 0xfc000-0xfffff could not be reserved
Feb 18 12:55:59 uCore64 kernel: [   33.295717] system 00:01: iomem range 0x3fff0000-0x3fffffff could not be reserved
Feb 18 12:55:59 uCore64 kernel: [   33.295795] system 00:01: iomem range 0xffff0000-0xffffffff could not be reserved
Feb 18 12:55:59 uCore64 kernel: [   33.295871] system 00:01: iomem range 0x0-0x9ffff could not be reserved
Feb 18 12:55:59 uCore64 kernel: [   33.295937] system 00:01: iomem range 0x100000-0x3ffeffff could not be reserved
Feb 18 12:55:59 uCore64 kernel: [   33.296013] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
Feb 18 12:55:59 uCore64 kernel: [   33.296090] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
Feb 18 12:55:59 uCore64 kernel: [   33.296170] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
Feb 18 12:55:59 uCore64 kernel: [   33.296236] system 00:03: ioport range 0x800-0x805 has been reserved
Feb 18 12:55:59 uCore64 kernel: [   33.296611] PCI: Bridge: 0000:00:0a.0
Feb 18 12:55:59 uCore64 kernel: [   33.296675]   IO window: 9000-afff
Feb 18 12:55:59 uCore64 kernel: [   33.296738]   MEM window: e3000000-e4ffffff
Feb 18 12:55:59 uCore64 kernel: [   33.296801]   PREFETCH window: 50000000-500fffff
Feb 18 12:55:59 uCore64 kernel: [   33.296866] PCI: Bridge: 0000:00:0b.0
Feb 18 12:55:59 uCore64 kernel: [   33.296928]   IO window: disabled.
Feb 18 12:55:59 uCore64 kernel: [   33.296992]   MEM window: e0000000-e2ffffff
Feb 18 12:55:59 uCore64 kernel: [   33.297056]   PREFETCH window: d0000000-dfffffff
Feb 18 12:55:59 uCore64 kernel: [   33.297126] PCI: Setting latency timer of device 0000:00:0a.0 to 64
Feb 18 12:55:59 uCore64 kernel: [   33.297163] NET: Registered protocol family 2
Feb 18 12:55:59 uCore64 kernel: [   33.329550] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
Feb 18 12:55:59 uCore64 kernel: [   33.329959] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
Feb 18 12:55:59 uCore64 kernel: [   33.331427] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Feb 18 12:55:59 uCore64 kernel: [   33.332225] TCP: Hash tables configured (established 131072 bind 65536)
Feb 18 12:55:59 uCore64 kernel: [   33.332291] TCP reno registered
Feb 18 12:55:59 uCore64 kernel: [   33.341591] checking if image is initramfs... it is
Feb 18 12:55:59 uCore64 kernel: [   33.796830] Switched to high resolution mode on CPU 0
Feb 18 12:55:59 uCore64 kernel: [   33.837905] Freeing initrd memory: 7284k freed
Feb 18 12:55:59 uCore64 kernel: [   33.843244] audit: initializing netlink socket (disabled)
Feb 18 12:55:59 uCore64 kernel: [   33.843320] audit(1234961735.080:1): initialized
Feb 18 12:55:59 uCore64 kernel: [   33.844902] VFS: Disk quotas dquot_6.5.1
Feb 18 12:55:59 uCore64 kernel: [   33.845020] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Feb 18 12:55:59 uCore64 kernel: [   33.845181] io scheduler noop registered
Feb 18 12:55:59 uCore64 kernel: [   33.845245] io scheduler anticipatory registered
Feb 18 12:55:59 uCore64 kernel: [   33.845308] io scheduler deadline registered
Feb 18 12:55:59 uCore64 kernel: [   33.845449] io scheduler cfq registered (default)
Feb 18 12:55:59 uCore64 kernel: [   33.846419] Boot video device is 0000:02:00.0
Feb 18 12:55:59 uCore64 kernel: [   33.867454] Real Time Clock Driver v1.12ac
Feb 18 12:55:59 uCore64 kernel: [   33.867594] Linux agpgart interface v0.102
Feb 18 12:55:59 uCore64 kernel: [   33.867658] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Feb 18 12:55:59 uCore64 kernel: [   33.868540] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Feb 18 12:55:59 uCore64 kernel: [   33.868674] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Feb 18 12:55:59 uCore64 kernel: [   33.869139] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Feb 18 12:55:59 uCore64 kernel: [   33.872080] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 18 12:55:59 uCore64 kernel: [   33.872146] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb 18 12:55:59 uCore64 kernel: [   33.880718] mice: PS/2 mouse device common for all mice
Feb 18 12:55:59 uCore64 kernel: [   33.880807] cpuidle: using governor ladder
Feb 18 12:55:59 uCore64 kernel: [   33.880870] cpuidle: using governor menu
Feb 18 12:55:59 uCore64 kernel: [   33.881046] NET: Registered protocol family 1
Feb 18 12:55:59 uCore64 kernel: [   33.881184] registered taskstats version 1
Feb 18 12:55:59 uCore64 kernel: [   33.881343]   Magic number: 13:489:936
Feb 18 12:55:59 uCore64 kernel: [   33.881539] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Feb 18 12:55:59 uCore64 kernel: [   33.881616] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb 18 12:55:59 uCore64 kernel: [   33.881681] EDD information not available.
Feb 18 12:55:59 uCore64 kernel: [   33.881749] Freeing unused kernel memory: 320k freed
Feb 18 12:55:59 uCore64 kernel: [   33.908642] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Feb 18 12:55:59 uCore64 kernel: [   34.010062] ACPI: processor limited to max C-state 1
Feb 18 12:55:59 uCore64 kernel: [   34.551488] usbcore: registered new interface driver usbfs
Feb 18 12:55:59 uCore64 kernel: [   34.551573] usbcore: registered new interface driver hub
Feb 18 12:55:59 uCore64 kernel: [   34.559400] usbcore: registered new device driver usb
Feb 18 12:55:59 uCore64 kernel: [   34.567237] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Feb 18 12:55:59 uCore64 kernel: [   34.567573] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
Feb 18 12:55:59 uCore64 kernel: [   34.567644] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [APCH] -> GSI 22 (level, high) -> IRQ 22
Feb 18 12:55:59 uCore64 kernel: [   34.567826] PCI: Setting latency timer of device 0000:00:05.0 to 64
Feb 18 12:55:59 uCore64 kernel: [   34.579393] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Feb 18 12:55:59 uCore64 kernel: [   34.600618] SCSI subsystem initialized
Feb 18 12:55:59 uCore64 kernel: [   34.635595] libata version 3.00 loaded.
Feb 18 12:55:59 uCore64 kernel: [   34.764072] Floppy drive(s): fd0 is 1.44M
Feb 18 12:55:59 uCore64 kernel: [   34.783185] FDC 0 is a post-1991 82077
Feb 18 12:55:59 uCore64 kernel: [   35.087240] forcedeth 0000:00:05.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:0d:61:30:f8:8e
Feb 18 12:55:59 uCore64 kernel: [   35.087322] forcedeth 0000:00:05.0: timirq lnktim desc-v1
Feb 18 12:55:59 uCore64 kernel: [   35.087745] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
Feb 18 12:55:59 uCore64 kernel: [   35.087815] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, high) -> IRQ 21
Feb 18 12:55:59 uCore64 kernel: [   35.088253] PCI: Setting latency timer of device 0000:00:02.0 to 64
Feb 18 12:55:59 uCore64 kernel: [   35.088259] ohci_hcd 0000:00:02.0: OHCI Host Controller
Feb 18 12:55:59 uCore64 kernel: [   35.088507] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
Feb 18 12:55:59 uCore64 kernel: [   35.088597] ohci_hcd 0000:00:02.0: irq 21, io mem 0xe5002000
Feb 18 12:55:59 uCore64 kernel: [   35.144920] usb usb1: configuration #1 chosen from 1 choice
Feb 18 12:55:59 uCore64 kernel: [   35.145004] hub 1-0:1.0: USB hub found
Feb 18 12:55:59 uCore64 kernel: [   35.145071] hub 1-0:1.0: 3 ports detected
Feb 18 12:55:59 uCore64 kernel: [   35.246962] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
Feb 18 12:55:59 uCore64 kernel: [   35.247033] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 20 (level, high) -> IRQ 20
Feb 18 12:55:59 uCore64 kernel: [   35.247388] PCI: Setting latency timer of device 0000:00:02.1 to 64
Feb 18 12:55:59 uCore64 kernel: [   35.247394] ohci_hcd 0000:00:02.1: OHCI Host Controller
Feb 18 12:55:59 uCore64 kernel: [   35.247512] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
Feb 18 12:55:59 uCore64 kernel: [   35.247605] ohci_hcd 0000:00:02.1: irq 20, io mem 0xe5003000
Feb 18 12:55:59 uCore64 kernel: [   35.304665] usb usb2: configuration #1 chosen from 1 choice
Feb 18 12:55:59 uCore64 kernel: [   35.304749] hub 2-0:1.0: USB hub found
Feb 18 12:55:59 uCore64 kernel: [   35.304816] hub 2-0:1.0: 3 ports detected
Feb 18 12:55:59 uCore64 kernel: [   35.406816] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
Feb 18 12:55:59 uCore64 kernel: [   35.406883] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 22 (level, high) -> IRQ 22
Feb 18 12:55:59 uCore64 kernel: [   35.407182] PCI: Setting latency timer of device 0000:00:02.2 to 64
Feb 18 12:55:59 uCore64 kernel: [   35.407188] ehci_hcd 0000:00:02.2: EHCI Host Controller
Feb 18 12:55:59 uCore64 kernel: [   35.407322] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
Feb 18 12:55:59 uCore64 kernel: [   35.407421] ehci_hcd 0000:00:02.2: debug port 1
Feb 18 12:55:59 uCore64 kernel: [   35.407486] PCI: cache line size of 64 is not supported by device 0000:00:02.2
Feb 18 12:55:59 uCore64 kernel: [   35.407498] ehci_hcd 0000:00:02.2: irq 22, io mem 0xe5004000
Feb 18 12:55:59 uCore64 kernel: [   35.418450] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Feb 18 12:55:59 uCore64 kernel: [   35.418622] usb usb3: configuration #1 chosen from 1 choice
Feb 18 12:55:59 uCore64 kernel: [   35.418707] hub 3-0:1.0: USB hub found
Feb 18 12:55:59 uCore64 kernel: [   35.418775] hub 3-0:1.0: 6 ports detected
Feb 18 12:55:59 uCore64 kernel: [   35.523962] sata_sil 0000:01:0d.0: version 2.3
Feb 18 12:55:59 uCore64 kernel: [   35.524149] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
Feb 18 12:55:59 uCore64 kernel: [   35.524222] ACPI: PCI Interrupt 0000:01:0d.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
Feb 18 12:55:59 uCore64 kernel: [   35.524623] sata_sil 0000:01:0d.0: Applying R_ERR on DMA activate FIS errata fix
Feb 18 12:55:59 uCore64 kernel: [   35.525914] scsi0 : sata_sil
Feb 18 12:55:59 uCore64 kernel: [   35.526487] scsi1 : sata_sil
Feb 18 12:55:59 uCore64 kernel: [   35.526574] ata1: SATA max UDMA/100 mmio m512@0xe4004000 tf 0xe4004080 irq 17
Feb 18 12:55:59 uCore64 kernel: [   35.526641] ata2: SATA max UDMA/100 mmio m512@0xe4004000 tf 0xe40040c0 irq 17
Feb 18 12:55:59 uCore64 kernel: [   35.993596] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Feb 18 12:55:59 uCore64 kernel: [   36.003046] ata1.00: ATA-6: WDC WD360GD-00FNA0, 34.06J34, max UDMA/133
Feb 18 12:55:59 uCore64 kernel: [   36.003112] ata1.00: 72303840 sectors, multi 16: LBA48 
Feb 18 12:55:59 uCore64 kernel: [   36.003176] ata1.00: applying bridge limits
Feb 18 12:55:59 uCore64 kernel: [   36.019063] ata1.00: configured for UDMA/100
Feb 18 12:55:59 uCore64 kernel: [   36.484873] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Feb 18 12:55:59 uCore64 kernel: [   36.494321] ata2.00: ATA-6: WDC WD360GD-00FNA0, 35.06K35, max UDMA/133
Feb 18 12:55:59 uCore64 kernel: [   36.494387] ata2.00: 72303840 sectors, multi 16: LBA48 
Feb 18 12:55:59 uCore64 kernel: [   36.494451] ata2.00: applying bridge limits
Feb 18 12:55:59 uCore64 kernel: [   36.510324] ata2.00: configured for UDMA/100
Feb 18 12:55:59 uCore64 kernel: [   36.510479] scsi 0:0:0:0: Direct-Access     ATA      WDC WD360GD-00FN 34.0 PQ: 0 ANSI: 5
Feb 18 12:55:59 uCore64 kernel: [   36.510629] scsi 1:0:0:0: Direct-Access     ATA      WDC WD360GD-00FN 35.0 PQ: 0 ANSI: 5
Feb 18 12:55:59 uCore64 kernel: [   36.510843] ACPI: PCI Interrupt 0000:01:08.2[B] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
Feb 18 12:55:59 uCore64 kernel: [   36.561093] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[e4005000-e40057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Feb 18 12:55:59 uCore64 kernel: [   36.561436] PCI: Setting latency timer of device 0000:00:08.0 to 64
Feb 18 12:55:59 uCore64 kernel: [   36.568577] Driver 'sd' needs updating - please use bus_type methods
Feb 18 12:55:59 uCore64 kernel: [   36.568719] sd 0:0:0:0: [sda] 72303840 512-byte hardware sectors (37020 MB)
Feb 18 12:55:59 uCore64 kernel: [   36.568805] sd 0:0:0:0: [sda] Write Protect is off
Feb 18 12:55:59 uCore64 kernel: [   36.568870] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 18 12:55:59 uCore64 kernel: [   36.568883] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 18 12:55:59 uCore64 kernel: [   36.568995] sd 0:0:0:0: [sda] 72303840 512-byte hardware sectors (37020 MB)
Feb 18 12:55:59 uCore64 kernel: [   36.569066] sd 0:0:0:0: [sda] Write Protect is off
Feb 18 12:55:59 uCore64 kernel: [   36.569129] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 18 12:55:59 uCore64 kernel: [   36.569140] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 18 12:55:59 uCore64 kernel: [   36.569218]  sda:<7>pata_amd 0000:00:08.0: version 0.3.10
Feb 18 12:55:59 uCore64 kernel: [   36.573030] PCI: Setting latency timer of device 0000:00:08.0 to 64
Feb 18 12:55:59 uCore64 kernel: [   36.573699] scsi2 : pata_amd
Feb 18 12:55:59 uCore64 kernel: [   36.574167] scsi3 : pata_amd
Feb 18 12:55:59 uCore64 kernel: [   36.574805] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Feb 18 12:55:59 uCore64 kernel: [   36.574872] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Feb 18 12:55:59 uCore64 kernel: [   36.577687]  sda1
Feb 18 12:55:59 uCore64 kernel: [   36.577799]  sda: p1 exceeds device capacity
Feb 18 12:55:59 uCore64 kernel: [   36.577905] sd 0:0:0:0: [sda] Attached SCSI disk
Feb 18 12:55:59 uCore64 kernel: [   36.578017] sd 1:0:0:0: [sdb] 72303840 512-byte hardware sectors (37020 MB)
Feb 18 12:55:59 uCore64 kernel: [   36.578091] sd 1:0:0:0: [sdb] Write Protect is off
Feb 18 12:55:59 uCore64 kernel: [   36.578155] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Feb 18 12:55:59 uCore64 kernel: [   36.578168] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 18 12:55:59 uCore64 kernel: [   36.578275] sd 1:0:0:0: [sdb] 72303840 512-byte hardware sectors (37020 MB)
Feb 18 12:55:59 uCore64 kernel: [   36.578346] sd 1:0:0:0: [sdb] Write Protect is off
Feb 18 12:55:59 uCore64 kernel: [   36.578410] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Feb 18 12:55:59 uCore64 kernel: [   36.578421] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 18 12:55:59 uCore64 kernel: [   36.578499]  sdb: unknown partition table
Feb 18 12:55:59 uCore64 kernel: [   36.587688] sd 1:0:0:0: [sdb] Attached SCSI disk
Feb 18 12:55:59 uCore64 kernel: [   36.594895] sd 0:0:0:0: Attached scsi generic sg0 type 0
Feb 18 12:55:59 uCore64 kernel: [   36.594977] sd 1:0:0:0: Attached scsi generic sg1 type 0
Feb 18 12:55:59 uCore64 kernel: [   36.655698] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.655768] sda: rw=0, want=72308417, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.655833] Buffer I/O error on device sda1, logical block 36154176
Feb 18 12:55:59 uCore64 kernel: [   36.655898] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.655973] sda: rw=0, want=72308419, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.656037] Buffer I/O error on device sda1, logical block 36154177
Feb 18 12:55:59 uCore64 kernel: [   36.656102] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.656165] sda: rw=0, want=72308421, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.656229] Buffer I/O error on device sda1, logical block 36154178
Feb 18 12:55:59 uCore64 kernel: [   36.656294] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.656357] sda: rw=0, want=72308423, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.656421] Buffer I/O error on device sda1, logical block 36154179
Feb 18 12:55:59 uCore64 kernel: [   36.656486] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.656549] sda: rw=0, want=72308417, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.656625] Buffer I/O error on device sda1, logical block 36154176
Feb 18 12:55:59 uCore64 kernel: [   36.656690] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.656753] sda: rw=0, want=72308419, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.656817] Buffer I/O error on device sda1, logical block 36154177
Feb 18 12:55:59 uCore64 kernel: [   36.656882] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.656945] sda: rw=0, want=72308421, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.657009] Buffer I/O error on device sda1, logical block 36154178
Feb 18 12:55:59 uCore64 kernel: [   36.657074] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.657137] sda: rw=0, want=72308423, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.657200] Buffer I/O error on device sda1, logical block 36154179
Feb 18 12:55:59 uCore64 kernel: [   36.657271] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.657335] sda: rw=0, want=72308545, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.657399] Buffer I/O error on device sda1, logical block 36154240
Feb 18 12:55:59 uCore64 kernel: [   36.657464] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.657527] sda: rw=0, want=72308547, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.657591] Buffer I/O error on device sda1, logical block 36154241
Feb 18 12:55:59 uCore64 kernel: [   36.657656] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.657720] sda: rw=0, want=72308549, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.657783] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.657847] sda: rw=0, want=72308551, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.657911] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.657975] sda: rw=0, want=72308545, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.658038] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.658102] sda: rw=0, want=72308547, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.658165] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.658229] sda: rw=0, want=72308549, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.658293] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.658356] sda: rw=0, want=72308551, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.658488] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.658601] sda: rw=0, want=72308561, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.658666] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.658738] sda: rw=0, want=72308563, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.658802] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.658866] sda: rw=0, want=72308565, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.658930] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.658994] sda: rw=0, want=72308561, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.659057] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.659121] sda: rw=0, want=72308563, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.659184] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.659248] sda: rw=0, want=72308565, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.659317] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.659381] sda: rw=0, want=72308561, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.659445] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.659509] sda: rw=0, want=72308563, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.659573] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.659637] sda: rw=0, want=72308565, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.659703] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.659767] sda: rw=0, want=72308561, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.659831] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.659895] sda: rw=0, want=72308563, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.659959] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.660023] sda: rw=0, want=72308565, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.660089] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.660153] sda: rw=0, want=72308561, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.660217] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.660280] sda: rw=0, want=72308563, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.660345] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.660408] sda: rw=0, want=72308565, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.660475] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.660539] sda: rw=0, want=72308561, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.660606] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.660670] sda: rw=0, want=72308563, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.660734] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.660798] sda: rw=0, want=72308565, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.660865] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.660929] sda: rw=0, want=72308561, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.660993] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.661056] sda: rw=0, want=72308563, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.661120] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.661184] sda: rw=0, want=72308565, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.661253] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.661317] sda: rw=0, want=72308497, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.661382] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.661446] sda: rw=0, want=72308499, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.661510] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.661574] sda: rw=0, want=72308501, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.661638] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.661702] sda: rw=0, want=72308503, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.661769] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.661833] sda: rw=0, want=72308553, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.661897] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.661961] sda: rw=0, want=72308555, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.662025] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.662089] sda: rw=0, want=72308557, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.662153] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.662217] sda: rw=0, want=72308559, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.662284] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.662348] sda: rw=0, want=72308561, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.662412] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.662475] sda: rw=0, want=72308563, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.662540] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.662603] sda: rw=0, want=72308565, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.662670] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.662734] sda: rw=0, want=72308561, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.662798] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.662862] sda: rw=0, want=72308563, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.662926] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   36.662990] sda: rw=0, want=72308565, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   36.744812] ata3.00: ATA-6: TOSHIBA MK6026GAX, PA202G, max UDMA/100
Feb 18 12:55:59 uCore64 kernel: [   36.744881] ata3.00: 117210240 sectors, multi 16: LBA 
Feb 18 12:55:59 uCore64 kernel: [   36.745036] ata3.01: ATA-6: TOSHIBA MK6026GAX, PA202G, max UDMA/100
Feb 18 12:55:59 uCore64 kernel: [   36.745102] ata3.01: 117210240 sectors, multi 16: LBA 
Feb 18 12:55:59 uCore64 kernel: [   36.752727] ata3.00: configured for UDMA/100
Feb 18 12:55:59 uCore64 kernel: [   36.760714] ata3.01: configured for UDMA/100
Feb 18 12:55:59 uCore64 kernel: [   37.080233] ata4.00: ATAPI: OPTORITEDVD RW DD0201, 2.17, max UDMA/33
Feb 18 12:55:59 uCore64 kernel: [   37.251921] ata4.00: configured for UDMA/33
Feb 18 12:55:59 uCore64 kernel: [   37.252055] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK6026GA PA20 PQ: 0 ANSI: 5
Feb 18 12:55:59 uCore64 kernel: [   37.252189] sd 2:0:0:0: [sdc] 117210240 512-byte hardware sectors (60012 MB)
Feb 18 12:55:59 uCore64 kernel: [   37.252263] sd 2:0:0:0: [sdc] Write Protect is off
Feb 18 12:55:59 uCore64 kernel: [   37.252327] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Feb 18 12:55:59 uCore64 kernel: [   37.252339] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 18 12:55:59 uCore64 kernel: [   37.252451] sd 2:0:0:0: [sdc] 117210240 512-byte hardware sectors (60012 MB)
Feb 18 12:55:59 uCore64 kernel: [   37.252522] sd 2:0:0:0: [sdc] Write Protect is off
Feb 18 12:55:59 uCore64 kernel: [   37.252586] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Feb 18 12:55:59 uCore64 kernel: [   37.252597] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 18 12:55:59 uCore64 kernel: [   37.252676]  sdc: sdc1 sdc2 < sdc5 >
Feb 18 12:55:59 uCore64 kernel: [   37.319809] sd 2:0:0:0: [sdc] Attached SCSI disk
Feb 18 12:55:59 uCore64 kernel: [   37.319894] sd 2:0:0:0: Attached scsi generic sg2 type 0
Feb 18 12:55:59 uCore64 kernel: [   37.319996] scsi 2:0:1:0: Direct-Access     ATA      TOSHIBA MK6026GA PA20 PQ: 0 ANSI: 5
Feb 18 12:55:59 uCore64 kernel: [   37.320110] sd 2:0:1:0: [sdd] 117210240 512-byte hardware sectors (60012 MB)
Feb 18 12:55:59 uCore64 kernel: [   37.320181] sd 2:0:1:0: [sdd] Write Protect is off
Feb 18 12:55:59 uCore64 kernel: [   37.320246] sd 2:0:1:0: [sdd] Mode Sense: 00 3a 00 00
Feb 18 12:55:59 uCore64 kernel: [   37.320257] sd 2:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 18 12:55:59 uCore64 kernel: [   37.320355] sd 2:0:1:0: [sdd] 117210240 512-byte hardware sectors (60012 MB)
Feb 18 12:55:59 uCore64 kernel: [   37.320426] sd 2:0:1:0: [sdd] Write Protect is off
Feb 18 12:55:59 uCore64 kernel: [   37.320490] sd 2:0:1:0: [sdd] Mode Sense: 00 3a 00 00
Feb 18 12:55:59 uCore64 kernel: [   37.320501] sd 2:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 18 12:55:59 uCore64 kernel: [   37.320579]  sdd: sdd1 sdd2 < sdd5 >
Feb 18 12:55:59 uCore64 kernel: [   37.400896] sd 2:0:1:0: [sdd] Attached SCSI disk
Feb 18 12:55:59 uCore64 kernel: [   37.400976] sd 2:0:1:0: Attached scsi generic sg3 type 0
Feb 18 12:55:59 uCore64 kernel: [   37.402156] scsi 3:0:0:0: CD-ROM            OPTORITE DVD RW DD0201    2.17 PQ: 0 ANSI: 5
Feb 18 12:55:59 uCore64 kernel: [   37.402271] scsi 3:0:0:0: Attached scsi generic sg4 type 5
Feb 18 12:55:59 uCore64 kernel: [   37.421735] Driver 'sr' needs updating - please use bus_type methods
Feb 18 12:55:59 uCore64 kernel: [   37.428590] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Feb 18 12:55:59 uCore64 kernel: [   37.428660] Uniform CD-ROM driver Revision: 3.20
Feb 18 12:55:59 uCore64 kernel: [   37.428768] sr 3:0:0:0: Attached scsi CD-ROM sr0
Feb 18 12:55:59 uCore64 kernel: [   37.765825] device-mapper: uevent: version 1.0.3
Feb 18 12:55:59 uCore64 kernel: [   37.765915] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
Feb 18 12:55:59 uCore64 kernel: [   37.838960] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c0151027595]
Feb 18 12:55:59 uCore64 kernel: [   43.194141] kjournald starting.  Commit interval 5 seconds
Feb 18 12:55:59 uCore64 kernel: [   43.194219] EXT3-fs: mounted filesystem with ordered data mode.
Feb 18 12:55:59 uCore64 kernel: [   49.725876] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.725958] sda: rw=0, want=72308417, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.726022] printk: 41 messages suppressed.
Feb 18 12:55:59 uCore64 kernel: [   49.726086] Buffer I/O error on device sda1, logical block 36154176
Feb 18 12:55:59 uCore64 kernel: [   49.726151] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.727700] sda: rw=0, want=72308419, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.727764] Buffer I/O error on device sda1, logical block 36154177
Feb 18 12:55:59 uCore64 kernel: [   49.727829] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.727893] sda: rw=0, want=72308421, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.727956] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.728020] sda: rw=0, want=72308423, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.728084] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.728147] sda: rw=0, want=72308417, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.728211] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.728274] sda: rw=0, want=72308419, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.728338] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.728402] sda: rw=0, want=72308421, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.728465] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.728529] sda: rw=0, want=72308423, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.728598] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.728661] sda: rw=0, want=72308545, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.728725] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.728789] sda: rw=0, want=72308547, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.728852] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.728916] sda: rw=0, want=72308549, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.728980] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.729043] sda: rw=0, want=72308551, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.729107] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.729171] sda: rw=0, want=72308545, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.729234] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.729298] sda: rw=0, want=72308547, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.729362] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.729425] sda: rw=0, want=72308549, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.729496] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.729560] sda: rw=0, want=72308551, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.729699] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.729812] sda: rw=0, want=72308561, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.729879] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.729953] sda: rw=0, want=72308563, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.730017] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.730081] sda: rw=0, want=72308565, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.730145] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.730209] sda: rw=0, want=72308561, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.730273] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.730337] sda: rw=0, want=72308563, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.730401] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.730465] sda: rw=0, want=72308565, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.730535] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.730599] sda: rw=0, want=72308561, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.730663] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.730727] sda: rw=0, want=72308563, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.730791] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.730855] sda: rw=0, want=72308565, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.730922] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.730986] sda: rw=0, want=72308561, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.731050] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.731114] sda: rw=0, want=72308563, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.731178] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.731242] sda: rw=0, want=72308565, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.731309] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.731373] sda: rw=0, want=72308561, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.731437] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.731501] sda: rw=0, want=72308563, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.731565] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.731629] sda: rw=0, want=72308565, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.731696] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.731760] sda: rw=0, want=72308561, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.731824] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.731888] sda: rw=0, want=72308563, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.731952] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.732016] sda: rw=0, want=72308565, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.732083] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.732147] sda: rw=0, want=72308561, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.732211] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.732275] sda: rw=0, want=72308563, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.732339] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.732402] sda: rw=0, want=72308565, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.732471] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.732535] sda: rw=0, want=72308497, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.732599] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.732663] sda: rw=0, want=72308499, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.732727] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.732791] sda: rw=0, want=72308501, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.732855] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.732919] sda: rw=0, want=72308503, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.732986] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.733050] sda: rw=0, want=72308553, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.733115] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.733178] sda: rw=0, want=72308555, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.733243] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.733306] sda: rw=0, want=72308557, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.733371] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.733434] sda: rw=0, want=72308559, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.734723] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.734791] sda: rw=0, want=72308561, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.734856] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.734919] sda: rw=0, want=72308563, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.734983] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.735046] sda: rw=0, want=72308565, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.735113] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.735176] sda: rw=0, want=72308561, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.735240] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.735304] sda: rw=0, want=72308563, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   49.735368] attempt to access beyond end of device
Feb 18 12:55:59 uCore64 kernel: [   49.735431] sda: rw=0, want=72308565, limit=72303840
Feb 18 12:55:59 uCore64 kernel: [   50.903947] input: PC Speaker as /devices/platform/pcspkr/input/input2
Feb 18 12:55:59 uCore64 kernel: [   51.167396] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 18 12:55:59 uCore64 kernel: [   51.183412] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb 18 12:55:59 uCore64 kernel: [   51.215390] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Feb 18 12:55:59 uCore64 kernel: [   51.215469] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
Feb 18 12:55:59 uCore64 kernel: [   51.251387] input: Power Button (FF) as /devices/virtual/input/input3
Feb 18 12:55:59 uCore64 kernel: [   51.283235] ACPI: Power Button (FF) [PWRF]
Feb 18 12:55:59 uCore64 kernel: [   51.283352] input: Power Button (CM) as /devices/virtual/input/input4
Feb 18 12:55:59 uCore64 kernel: [   51.311710] ACPI: Power Button (CM) [PWRB]
Feb 18 12:55:59 uCore64 kernel: [   51.551204] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
Feb 18 12:55:59 uCore64 kernel: [   53.352164] gameport: EMU10K1 is pci0000:01:08.1/gameport0, io 0x9400, speed 1194kHz
Feb 18 12:55:59 uCore64 kernel: [   53.562537] nvidia: module license 'NVIDIA' taints kernel.
Feb 18 12:55:59 uCore64 kernel: [   53.895155] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
Feb 18 12:55:59 uCore64 kernel: [   53.895230] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 16
Feb 18 12:55:59 uCore64 kernel: [   53.895584] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
Feb 18 12:55:59 uCore64 kernel: [   53.909092] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Feb 18 12:55:59 uCore64 kernel: [   53.909163] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
Feb 18 12:55:59 uCore64 kernel: [   53.912037] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emufx.c:1544: Installing spdif_bug patch: Audigy 2 ZS [SB0350]
Feb 18 12:55:59 uCore64 kernel: [   54.588772] NET: Registered protocol family 17
Feb 18 12:55:59 uCore64 kernel: [   55.227074] loop: module loaded
Feb 18 12:55:59 uCore64 kernel: [   55.309444] lp: driver loaded but no devices found
Feb 18 12:55:59 uCore64 kernel: [   55.681457] Adding 2441840k swap on /dev/sdd5.  Priority:-1 extents:1 across:2441840k
Feb 18 12:55:59 uCore64 kernel: [   56.079836] EXT3 FS on sdd1, internal journal
Feb 18 12:55:59 uCore64 kernel: [   56.671549] kjournald starting.  Commit interval 5 seconds
Feb 18 12:55:59 uCore64 kernel: [   56.679629] EXT3 FS on sdc1, internal journal
Feb 18 12:55:59 uCore64 kernel: [   56.679633] EXT3-fs: mounted filesystem with ordered data mode.
Feb 18 12:55:59 uCore64 kernel: [   57.450232] NET: Registered protocol family 10
Feb 18 12:55:59 uCore64 kernel: [   57.450394] lo: Disabled Privacy Extensions
Feb 18 12:55:59 uCore64 kernel: [   58.239741] No dock devices found.
Feb 18 12:56:08 uCore64 kernel: [   67.755068] eth0: no IPv6 routers present
Feb 18 12:56:18 uCore64 kernel: [   77.539269] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Feb 18 12:56:18 uCore64 kernel: [   77.539286] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Feb 18 12:56:18 uCore64 kernel: [   77.539320] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode

```

Does anyone have any ideas?  I'm stuck at 2.6.24 kernels otherwise.
Thanks,
b

---

### Post by cariboo on 2009-02-18
Have a look at the [FakeRaid]("http://help.ubuntu.com/community/FakeRaidHowto") howto, this may help.

Just out of curiosity what is the output of:

```
sudo fdisk -l
```

I have a feeling that one of your drives doesn't have a valid partition, and thet may be causing your problem. I only partitoned one drive of my raid array the first time I set it up, assuming that because I was using mirroring that the second disk would be an exact duplicate the first, which led to problems after a while.

Jim

---

### Post by eilenbeb on 2009-02-18
I read the link, thanks Jim.  I'm not using my fakeraid for linux or using grub, and my fakraid array works fine from Ubuntu.  There was some info in there worth bookmarking, though.

```

sudo fdisk -l

```

gives:

```

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c393c38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4501    36154251    c  W95 FAT32 (LBA)

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92323287

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        6992    56163208+  83  Linux
/dev/sdc2            6993        7296     2441880    5  Extended
/dev/sdc5            6993        7296     2441848+  82  Linux swap / Solaris

Disk /dev/sdd: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92323286

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        6992    56163208+  83  Linux
/dev/sdd2            6993        7296     2441880    5  Extended
/dev/sdd5            6993        7296     2441848+  82  Linux swap / Solaris

Disk /dev/dm-0: 74.0 GB, 74035986432 bytes
255 heads, 63 sectors/track, 9001 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c393c38

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1        4501    36154251    c  W95 FAT32 (LBA)

Disk /dev/dm-1: 37.0 GB, 37021953024 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69737369

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?      116388      126889    84344761   69  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?      105915      222310   934940732+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?           1           1           0   74  Unknown
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4          179626      179629       26207+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

I'm using dmraid, btw.
I was under the impression that both sda and sdb should look like sdb in the above as they're RAID0 and formatted fat32.
Don't know anything about the /dev/dm entries as I've never seen them before.

---

