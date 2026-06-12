---
title: "Ricoh R5C843 SD Card Reader Sony Vaio G21VN"
date: 2012-05-21
forum: Hardware
---

### Post by mark909 on 2012-05-21
Hi people!

I just installed Ubuntu 12.04 and lovin' it. It was able to work out of the box with every device in my laptop (Sony VGN-G21VN) apart from the Ricoh R5C843 SD Card Reader.

the output of my lspci (I'm sure it's attached via PCI) is as follows:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
07:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
07:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
07:04.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
```

There is no Ricoh R5C843, nor R5C822 listed.

I've tried to boot the notebook with an SD card plugged in but no luck. I double checked that the sdhci module is running with modprobe but, again, no luck.

Here is the (I think relevant) modprobe -l output:
```
kernel/drivers/mmc/card/sdio_uart.ko
kernel/drivers/mmc/host/sdhci.ko
kernel/drivers/mmc/host/sdhci-pci.ko
kernel/drivers/mmc/host/wbsd.ko
kernel/drivers/mmc/host/tifm_sd.ko
kernel/drivers/mmc/host/sdricoh_cs.ko
kernel/drivers/mmc/host/via-sdmmc.ko
kernel/drivers/mmc/host/sdhci-pltfm.ko

```

NOTE: all packages (including kernel) updated to the latest versions with apt.

Thanks in advance!

Mark

---

### Post by mark909 on 2012-05-22
Update: tested against latest (3.4.0) mainstream kernel but no luck.

Thanks.

---

### Post by Whoopie on 2012-05-22
This is your card reader:
```

07:04.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)

```

Could you post dmesg and lsmod output?

---

### Post by mark909 on 2012-05-22
> **Whoopie said:**
> This is your card reader:
```

07:04.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)

```

Actually that is the (separate) Memory Stick Reader that works. Thanks anyway.

> **Whoopie said:**
> Could you post dmesg and lsmod output?

Yep! (after inserting a SD card in the reader)

dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-24-generic (buildd@komainu) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #38-Ubuntu SMP Tue May 1 16:18:50 UTC 2012 (Ubuntu 3.2.0-24.38-generic 3.2.16)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=6bd04d78-2cc1-4602-aa72-cb15d7dde368 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f670000 (usable)
[    0.000000]  BIOS-e820: 000000007f670000 - 000000007f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f700000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: Sony Corporation VGN-G21VN_B/VAIO                            , BIOS R0021N9 08/21/2007
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x7f670 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 07F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2039MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] total RAM covered: 2039M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 16M 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2039MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [ffff8800000f6b90] f6b90
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-000000007f670000
[    0.000000]  0000000000 - 007f600000 page 2M
[    0.000000]  007f600000 - 007f670000 page 4k
[    0.000000] kernel direct mapping tables up to 7f670000 @ 1fffc000-20000000
[    0.000000] RAMDISK: 364e8000 - 3726c000
[    0.000000] ACPI: RSDP 00000000000f6ac0 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 000000007f6764e3 0007C (v01   Sony     VAIO 06040000 PTL  00000000)
[    0.000000] ACPI: FACP 000000007f67cbf8 000F4 (v03   Sony     VAIO 20070821 PTL  00000001)
[    0.000000] ACPI: DSDT 000000007f677538 0563C (v01   Sony     VAIO 20070821 PTL  20050624)
[    0.000000] ACPI: FACS 000000007f67dfc0 00040
[    0.000000] ACPI: APIC 000000007f67ccec 00068 (v01   Sony     VAIO 20070821 PTL  0000005A)
[    0.000000] ACPI: HPET 000000007f67cd54 00038 (v01   Sony     VAIO 20070821 PTL  0000005A)
[    0.000000] ACPI: MCFG 000000007f67cd8c 0003C (v01   Sony     VAIO 20070821 PTL  0000005A)
[    0.000000] ACPI: TCPA 000000007f67cdc8 00032 (v01   Sony     VAIO 20070821 PTL  00005A52)
[    0.000000] ACPI: SLIC 000000007f67cdfa 00176 (v01   Sony     VAIO 20070821 PTL  01000000)
[    0.000000] ACPI: APIC 000000007f67cf70 00068 (v01   Sony     VAIO 20070821 PTL  00000000)
[    0.000000] ACPI: BOOT 000000007f67cfd8 00028 (v01   Sony     VAIO 20070821 PTL  00000001)
[    0.000000] ACPI: SSDT 000000007f676aeb 0025F (v01   Sony     VAIO 20070821 PTL  20050624)
[    0.000000] ACPI: SSDT 000000007f676a45 000A6 (v01   Sony     VAIO 20070821 PTL  20050624)
[    0.000000] ACPI: SSDT 000000007f67655f 004E6 (v01   Sony     VAIO 20070821 PTL  20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007f670000
[    0.000000] Initmem setup node 0 0000000000000000-000000007f670000
[    0.000000]   NODE_DATA [000000007f66b000 - 000000007f66ffff]
[    0.000000]  [ffffea0000000000-ffffea0001ffffff] PMD -> [ffff88007ce00000-ffff88007edfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f670
[    0.000000] On node 0 totalpages: 521727
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3914 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 8090 pages used for memmap
[    0.000000]   DMA32 zone: 509654 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007f400000 s83072 r8192 d23424 u1048576
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 513568
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=6bd04d78-2cc1-4602-aa72-cb15d7dde368 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2024248k/2087360k available (6567k kernel code, 452k absent, 62660k reserved, 6636k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1064.049 MHz processor.
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 2128.09 BogoMIPS (lpj=4256196)
[    0.004017] pid_max: default: 32768 minimum: 301
[    0.004070] Security Framework initialized
[    0.004106] AppArmor: AppArmor initialized
[    0.004109] Yama: becoming mindful.
[    0.004616] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.006645] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.009438] Mount-cache hash table entries: 256
[    0.009725] Initializing cgroup subsys cpuacct
[    0.009736] Initializing cgroup subsys memory
[    0.009754] Initializing cgroup subsys devices
[    0.009759] Initializing cgroup subsys freezer
[    0.009763] Initializing cgroup subsys blkio
[    0.009776] Initializing cgroup subsys perf_event
[    0.009842] CPU: Physical Processor ID: 0
[    0.009846] CPU: Processor Core ID: 0
[    0.009851] mce: CPU supports 6 MCE banks
[    0.009868] CPU0: Thermal monitoring enabled (TM2)
[    0.009876] using mwait in idle threads.
[    0.015133] ACPI: Core revision 20110623
[    0.024022] ftrace: allocating 27050 entries in 107 pages
[    0.032600] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.074352] CPU0: Intel(R) Core(TM)2 CPU         U7500  @ 1.06GHz stepping 02
[    0.076004] Performance Events: PEBS fmt0-, Core2 events, Intel PMU driver.
[    0.076004] PEBS disabled due to CPU errata.
[    0.076004] ... version:                2
[    0.076004] ... bit width:              40
[    0.076004] ... generic registers:      2
[    0.076004] ... value mask:             000000ffffffffff
[    0.076004] ... max period:             000000007fffffff
[    0.076004] ... fixed-purpose events:   3
[    0.076004] ... event mask:             0000000700000003
[    0.076004] NMI watchdog enabled, takes one hw-pmu counter.
[    0.076004] Booting Node   0, Processors  #1 Ok.
[    0.076004] smpboot cpu 1: start_ip = 9a000
[    0.164060] NMI watchdog enabled, takes one hw-pmu counter.
[    0.164134] Brought up 2 CPUs
[    0.164139] Total of 2 processors activated (4256.09 BogoMIPS).
[    0.166456] devtmpfs: initialized
[    0.170330] EVM: security.selinux
[    0.170334] EVM: security.SMACK64
[    0.170337] EVM: security.capability
[    0.170359] PM: Registering ACPI NVS region at 7f670000 (589824 bytes)
[    0.170359] print_constraints: dummy: 
[    0.170359] RTC time: 17:38:18, date: 05/22/12
[    0.170359] NET: Registered protocol family 16
[    0.172174] Trying to unpack rootfs image as initramfs...
[    0.172273] ACPI: bus type pci registered
[    0.172401] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.172407] PCI: not using MMCONFIG
[    0.172410] PCI: Using configuration type 1 for base access
[    0.174617] bio: create slab <bio-0> at 0
[    0.174790] ACPI: Added _OSI(Module Device)
[    0.174795] ACPI: Added _OSI(Processor Device)
[    0.174800] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.174804] ACPI: Added _OSI(Processor Aggregator Device)
[    0.176950] ACPI: EC: Look up EC in DSDT
[    0.180659] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.183982] ACPI: SSDT 000000007f6772bc 001B4 (v01   Sony     VAIO 20070821 PTL  20050624)
[    0.184541] ACPI: Dynamic OEM Table Load:
[    0.184548] ACPI: SSDT           (null) 001B4 (v01   Sony     VAIO 20070821 PTL  20050624)
[    0.184761] ACPI: SSDT 000000007f676d4a 004ED (v01   Sony     VAIO 20070821 PTL  20050624)
[    0.185269] ACPI: Dynamic OEM Table Load:
[    0.185275] ACPI: SSDT           (null) 004ED (v01   Sony     VAIO 20070821 PTL  20050624)
[    0.185683] ACPI: SSDT 000000007f677470 000C8 (v01   Sony     VAIO 20070821 PTL  20050624)
[    0.186203] ACPI: Dynamic OEM Table Load:
[    0.186209] ACPI: SSDT           (null) 000C8 (v01   Sony     VAIO 20070821 PTL  20050624)
[    0.186363] ACPI: SSDT 000000007f677237 00085 (v01   Sony     VAIO 20070821 PTL  20050624)
[    0.186871] ACPI: Dynamic OEM Table Load:
[    0.186878] ACPI: SSDT           (null) 00085 (v01   Sony     VAIO 20070821 PTL  20050624)
[    0.187329] ACPI: Interpreter enabled
[    0.187338] ACPI: (supports S0 S3 S4 S5)
[    0.187373] ACPI: Using IOAPIC for interrupt routing
[    0.187407] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.187701] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.257519] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.257790] ACPI: No dock devices found.
[    0.257796] HEST: Table not found.
[    0.257803] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.258340] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.259367] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.259374] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.259380] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.259386] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    0.259391] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.259397] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.259403] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xfebfffff] (ignored)
[    0.259409] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff] (ignored)
[    0.259432] pci 0000:00:00.0: [8086:27a0] type 0 class 0x000600
[    0.259520] pci 0000:00:02.0: [8086:27a2] type 0 class 0x000300
[    0.259541] pci 0000:00:02.0: reg 10: [mem 0xf4200000-0xf427ffff]
[    0.259555] pci 0000:00:02.0: reg 14: [io  0x1800-0x1807]
[    0.259567] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.259580] pci 0000:00:02.0: reg 1c: [mem 0xf4300000-0xf433ffff]
[    0.259660] pci 0000:00:02.1: [8086:27a6] type 0 class 0x000380
[    0.259678] pci 0000:00:02.1: reg 10: [mem 0xf4280000-0xf42fffff]
[    0.260084] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.260117] pci 0000:00:1b.0: reg 10: [mem 0xf4540000-0xf4543fff 64bit]
[    0.260270] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.260281] pci 0000:00:1b.0: PME# disabled
[    0.260332] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.260491] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.260499] pci 0000:00:1c.0: PME# disabled
[    0.260548] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.260705] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.260714] pci 0000:00:1c.1: PME# disabled
[    0.260769] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.260853] pci 0000:00:1d.0: reg 20: [io  0x1820-0x183f]
[    0.260919] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.261002] pci 0000:00:1d.1: reg 20: [io  0x1840-0x185f]
[    0.261067] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.261151] pci 0000:00:1d.2: reg 20: [io  0x1860-0x187f]
[    0.261217] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.261300] pci 0000:00:1d.3: reg 20: [io  0x1880-0x189f]
[    0.261383] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.261419] pci 0000:00:1d.7: reg 10: [mem 0xf4544000-0xf45443ff]
[    0.261576] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.261584] pci 0000:00:1d.7: PME# disabled
[    0.261620] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.261762] pci 0000:00:1f.0: [8086:27b9] type 0 class 0x000601
[    0.261901] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.261911] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.261920] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.262001] pci 0000:00:1f.1: [8086:27df] type 0 class 0x000101
[    0.262027] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.262047] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.262066] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.262086] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.262105] pci 0000:00:1f.1: reg 20: [io  0x1810-0x181f]
[    0.262176] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.262264] pci 0000:00:1f.3: reg 20: [io  0x18a0-0x18bf]
[    0.262482] pci 0000:02:00.0: [8086:4229] type 0 class 0x000280
[    0.262552] pci 0000:02:00.0: reg 10: [mem 0xf2000000-0xf2001fff 64bit]
[    0.262890] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.262904] pci 0000:02:00.0: PME# disabled
[    0.268064] pci 0000:00:1c.0: PCI bridge to [bus 02-05]
[    0.268074] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.268083] pci 0000:00:1c.0:   bridge window [mem 0xf2000000-0xf3ffffff]
[    0.268096] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.268381] pci 0000:06:00.0: [11ab:4363] type 0 class 0x000200
[    0.268548] pci 0000:06:00.0: reg 10: [mem 0xf4000000-0xf4003fff 64bit]
[    0.268642] pci 0000:06:00.0: reg 18: [io  0x3000-0x30ff]
[    0.268979] pci 0000:06:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.269522] pci 0000:06:00.0: supports D1 D2
[    0.269527] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.269553] pci 0000:06:00.0: PME# disabled
[    0.269788] pci 0000:00:1c.1: PCI bridge to [bus 06-06]
[    0.269796] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.269806] pci 0000:00:1c.1:   bridge window [mem 0xf4000000-0xf40fffff]
[    0.269893] pci 0000:07:04.0: [1180:0476] type 2 class 0x000607
[    0.269923] pci 0000:07:04.0: proprietary Ricoh MMC controller disabled (via cardbus function)
[    0.269928] pci 0000:07:04.0: MMC cards are now supported by standard SDHCI controller
[    0.269951] pci 0000:07:04.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.270002] pci 0000:07:04.0: supports D1 D2
[    0.270007] pci 0000:07:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.270015] pci 0000:07:04.0: PME# disabled
[    0.270047] pci 0000:07:04.1: [1180:0832] type 0 class 0x000c00
[    0.270080] pci 0000:07:04.1: reg 10: [mem 0xf4100000-0xf41007ff]
[    0.270215] pci 0000:07:04.1: PME# supported from D0 D3hot D3cold
[    0.270224] pci 0000:07:04.1: PME# disabled
[    0.270259] pci 0000:07:04.4: [1180:0592] type 0 class 0x000880
[    0.270292] pci 0000:07:04.4: reg 10: [mem 0xf4100c00-0xf4100cff]
[    0.270427] pci 0000:07:04.4: supports D1 D2
[    0.270431] pci 0000:07:04.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.270440] pci 0000:07:04.4: PME# disabled
[    0.270521] pci 0000:00:1e.0: PCI bridge to [bus 07-08] (subtractive decode)
[    0.270534] pci 0000:00:1e.0:   bridge window [mem 0xf4100000-0xf41fffff]
[    0.270548] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.270553] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
[    0.270618] pci_bus 0000:08: [bus 08-0b] partially hidden behind transparent bridge 0000:07 [bus 07-08]
[    0.270661] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.270903] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.270991] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.271105] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.271290]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.271297]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.271301] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.278226] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[    0.278316] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    0.278401] ACPI: PCI Interrupt Link [LNKC] (IRQs 10) *0, disabled.
[    0.278488] ACPI: PCI Interrupt Link [LNKD] (IRQs *10)
[    0.278579] ACPI: PCI Interrupt Link [LNKE] (IRQs 10) *0, disabled.
[    0.278665] ACPI: PCI Interrupt Link [LNKF] (IRQs *10)
[    0.278750] ACPI: PCI Interrupt Link [LNKG] (IRQs *10)
[    0.278834] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[    0.279081] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.279105] vgaarb: loaded
[    0.279108] vgaarb: bridge control possible 0000:00:02.0
[    0.279348] i2c-core: driver [aat2870] using legacy suspend method
[    0.279352] i2c-core: driver [aat2870] using legacy resume method
[    0.279496] SCSI subsystem initialized
[    0.279614] libata version 3.00 loaded.
[    0.279722] usbcore: registered new interface driver usbfs
[    0.279746] usbcore: registered new interface driver hub
[    0.279803] usbcore: registered new device driver usb
[    0.280017] PCI: Using ACPI for IRQ routing
[    0.294592] PCI: pci_cache_line_size set to 64 bytes
[    0.294793] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.294799] reserve RAM buffer: 000000007f670000 - 000000007fffffff 
[    0.295036] NetLabel: Initializing
[    0.295040] NetLabel:  domain hash size = 128
[    0.295044] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.295067] NetLabel:  unlabeled traffic allowed by default
[    0.295178] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.295188] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.295198] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.304146] Switching to clocksource hpet
[    0.320696] AppArmor: AppArmor Filesystem Enabled
[    0.320760] pnp: PnP ACPI init
[    0.320802] ACPI: bus type pnp registered
[    0.321416] pnp 00:00: [bus 00-ff]
[    0.321422] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.321427] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.321432] pnp 00:00: [io  0x0d00-0xffff window]
[    0.321438] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.321442] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.321447] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.321452] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.321457] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.321461] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.321466] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.321471] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.321476] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.321480] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.321485] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.321490] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.321494] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.321499] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.321504] pnp 00:00: [mem 0x80000000-0xfebfffff window]
[    0.321509] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.321633] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.321682] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.321687] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.321691] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.321696] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.321700] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.321705] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.321709] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
[    0.321837] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.321844] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.321849] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.321855] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.321861] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.321867] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.321872] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.321880] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.322387] pnp 00:02: [io  0x0000-0x001f]
[    0.322392] pnp 00:02: [io  0x0081-0x0091]
[    0.322397] pnp 00:02: [io  0x0093-0x009f]
[    0.322401] pnp 00:02: [io  0x00c0-0x00df]
[    0.322405] pnp 00:02: [dma 4]
[    0.322488] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.322507] pnp 00:03: [mem 0xff000000-0xffffffff]
[    0.322586] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    0.322708] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.322793] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.322827] pnp 00:05: [io  0x00f0]
[    0.322848] pnp 00:05: [irq 13]
[    0.322933] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.322980] pnp 00:06: [io  0x004e-0x004f]
[    0.322985] pnp 00:06: [io  0x0061]
[    0.322988] pnp 00:06: [io  0x0063]
[    0.322992] pnp 00:06: [io  0x0065]
[    0.322996] pnp 00:06: [io  0x0067]
[    0.322999] pnp 00:06: [io  0x0070]
[    0.323003] pnp 00:06: [io  0x0080]
[    0.323006] pnp 00:06: [io  0x0092]
[    0.323010] pnp 00:06: [io  0x00b2-0x00b3]
[    0.323014] pnp 00:06: [io  0x0680-0x06ff]
[    0.323018] pnp 00:06: [io  0x0800-0x080f]
[    0.323022] pnp 00:06: [io  0x1000-0x107f]
[    0.323026] pnp 00:06: [io  0x1180-0x11bf]
[    0.323030] pnp 00:06: [io  0x1640-0x164f]
[    0.323034] pnp 00:06: [io  0xfe00-0xfe01]
[    0.323169] system 00:06: [io  0x0680-0x06ff] has been reserved
[    0.323175] system 00:06: [io  0x0800-0x080f] has been reserved
[    0.323181] system 00:06: [io  0x1000-0x107f] has been reserved
[    0.323187] system 00:06: [io  0x1180-0x11bf] has been reserved
[    0.323192] system 00:06: [io  0x1640-0x164f] has been reserved
[    0.323198] system 00:06: [io  0xfe00-0xfe01] has been reserved
[    0.323205] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.323231] pnp 00:07: [io  0x0070-0x0077]
[    0.323242] pnp 00:07: [irq 8]
[    0.323318] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.323622] pnp 00:08: Plug and Play ACPI device, IDs SNY6001 (disabled)
[    0.323668] pnp 00:09: [mem 0xfed40000-0xfed44fff]
[    0.323756] pnp 00:09: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active)
[    0.323776] pnp 00:0a: [io  0x0060]
[    0.323780] pnp 00:0a: [io  0x0064]
[    0.323790] pnp 00:0a: [irq 1]
[    0.323870] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.323894] pnp 00:0b: [irq 12]
[    0.323979] pnp 00:0b: Plug and Play ACPI device, IDs SNY9001 PNP0f13 (active)
[    0.324041] pnp: PnP ACPI: found 12 devices
[    0.324045] ACPI: ACPI bus type pnp unregistered
[    0.332596] PCI: max bus depth: 2 pci_try_num: 3
[    0.332672] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80000000-0x800fffff pref]
[    0.332680] pci 0000:00:1e.0: BAR 15: assigned [mem 0x84000000-0x87ffffff pref]
[    0.332689] pci 0000:00:1e.0: BAR 13: assigned [io  0x4000-0x4fff]
[    0.332696] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80000000-0x802fffff pref]
[    0.332705] pci 0000:00:1c.0: PCI bridge to [bus 02-05]
[    0.332712] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.332723] pci 0000:00:1c.0:   bridge window [mem 0xf2000000-0xf3ffffff]
[    0.332732] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.332747] pci 0000:06:00.0: BAR 6: assigned [mem 0x80000000-0x8001ffff pref]
[    0.332752] pci 0000:00:1c.1: PCI bridge to [bus 06-06]
[    0.332759] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.332769] pci 0000:00:1c.1:   bridge window [mem 0xf4000000-0xf40fffff]
[    0.332778] pci 0000:00:1c.1:   bridge window [mem 0x80000000-0x802fffff pref]
[    0.332795] pci 0000:07:04.0: BAR 0: assigned [mem 0x88000000-0x88000fff]
[    0.332806] pci 0000:07:04.0: BAR 0: set to [mem 0x88000000-0x88000fff] (PCI address [0x88000000-0x88000fff])
[    0.332814] pci 0000:07:04.0: BAR 16: assigned [mem 0x8c000000-0x8fffffff]
[    0.332819] pci 0000:07:04.0: BAR 15: assigned [mem 0x84000000-0x87ffffff pref]
[    0.332825] pci 0000:07:04.0: BAR 14: assigned [io  0x4000-0x40ff]
[    0.332830] pci 0000:07:04.0: BAR 13: assigned [io  0x4400-0x44ff]
[    0.332836] pci 0000:07:04.0: CardBus bridge to [bus 08-0b]
[    0.332840] pci 0000:07:04.0:   bridge window [io  0x4400-0x44ff]
[    0.332849] pci 0000:07:04.0:   bridge window [io  0x4000-0x40ff]
[    0.332857] pci 0000:07:04.0:   bridge window [mem 0x84000000-0x87ffffff pref]
[    0.332866] pci 0000:07:04.0:   bridge window [mem 0x8c000000-0x8fffffff]
[    0.332875] pci 0000:00:1e.0: PCI bridge to [bus 07-08]
[    0.332881] pci 0000:00:1e.0:   bridge window [io  0x4000-0x4fff]
[    0.332892] pci 0000:00:1e.0:   bridge window [mem 0xf4100000-0xf41fffff]
[    0.332901] pci 0000:00:1e.0:   bridge window [mem 0x84000000-0x87ffffff pref]
[    0.332943] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.332953] pci 0000:00:1c.0: setting latency timer to 64
[    0.332974] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.332984] pci 0000:00:1c.1: setting latency timer to 64
[    0.332998] pci 0000:00:1e.0: setting latency timer to 64
[    0.333018] pci 0000:07:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.333029] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.333034] pci_bus 0000:00: resource 1 [mem 0x00000000-0xfffffffff]
[    0.333040] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.333046] pci_bus 0000:02: resource 1 [mem 0xf2000000-0xf3ffffff]
[    0.333053] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.333061] pci_bus 0000:06: resource 0 [io  0x3000-0x3fff]
[    0.333067] pci_bus 0000:06: resource 1 [mem 0xf4000000-0xf40fffff]
[    0.333074] pci_bus 0000:06: resource 2 [mem 0x80000000-0x802fffff pref]
[    0.333081] pci_bus 0000:07: resource 0 [io  0x4000-0x4fff]
[    0.333088] pci_bus 0000:07: resource 1 [mem 0xf4100000-0xf41fffff]
[    0.333095] pci_bus 0000:07: resource 2 [mem 0x84000000-0x87ffffff pref]
[    0.333101] pci_bus 0000:07: resource 4 [io  0x0000-0xffff]
[    0.333108] pci_bus 0000:07: resource 5 [mem 0x00000000-0xfffffffff]
[    0.333115] pci_bus 0000:08: resource 0 [io  0x4400-0x44ff]
[    0.333119] pci_bus 0000:08: resource 1 [io  0x4000-0x40ff]
[    0.333125] pci_bus 0000:08: resource 2 [mem 0x84000000-0x87ffffff pref]
[    0.333130] pci_bus 0000:08: resource 3 [mem 0x8c000000-0x8fffffff]
[    0.333216] NET: Registered protocol family 2
[    0.333451] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.334838] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.338923] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.339971] TCP: Hash tables configured (established 262144 bind 65536)
[    0.339976] TCP reno registered
[    0.339990] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.340086] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.340318] NET: Registered protocol family 1
[    0.340355] pci 0000:00:02.0: Boot video device
[    0.340397] pci 0000:00:1d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.340425] pci 0000:00:1d.0: PCI INT A disabled
[    0.340460] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.340486] pci 0000:00:1d.1: PCI INT B disabled
[    0.340513] pci 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.340539] pci 0000:00:1d.2: PCI INT C disabled
[    0.340555] pci 0000:00:1d.3: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.340580] pci 0000:00:1d.3: PCI INT A disabled
[    0.340603] pci 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.340647] pci 0000:00:1d.7: PCI INT D disabled
[    0.340714] PCI: CLS 64 bytes, default 64
[    0.340735] Simple Boot Flag at 0x36 set to 0x1
[    0.341446] audit: initializing netlink socket (disabled)
[    0.341464] type=2000 audit(1337708298.336:1): initialized
[    0.396961] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.420342] VFS: Disk quotas dquot_6.5.2
[    0.420461] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.421528] fuse init (API version 7.17)
[    0.421718] msgmni has been set to 3953
[    0.422354] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.422411] io scheduler noop registered
[    0.422416] io scheduler deadline registered
[    0.422487] io scheduler cfq registered (default)
[    0.422702] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.422794] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.422927] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.423008] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.423176] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.423225] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.423343] intel_idle: MWAIT substates: 0x22220
[    0.423347] intel_idle: does not run on family 6 model 15
[    0.423621] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.423864] ACPI: AC Adapter [ACAD] (on-line)
[    0.423994] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.424190] ACPI: Lid Switch [LID0]
[    0.424292] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.424301] ACPI: Power Button [PWRB]
[    0.436360] Monitor-Mwait will be used to enter C-1 state
[    0.444096] Monitor-Mwait will be used to enter C-2 state
[    0.444167] Monitor-Mwait will be used to enter C-3 state
[    0.444185] Marking TSC unstable due to TSC halts in idle
[    0.444210] ACPI: acpi_idle registered with cpuidle
[    0.449024] thermal LNXTHERM:00: registered as thermal_zone0
[    0.449030] ACPI: Thermal Zone [ATF0] (42 C)
[    0.449896] thermal LNXTHERM:01: registered as thermal_zone1
[    0.449901] ACPI: Thermal Zone [DTS0] (42 C)
[    0.450777] thermal LNXTHERM:02: registered as thermal_zone2
[    0.450782] ACPI: Thermal Zone [DTS1] (45 C)
[    0.450830] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.450849] ACPI: Battery Slot [BAT1] (battery present)
[    0.450946] ERST: Table is not found!
[    0.450949] GHES: HEST is not enabled!
[    0.451127] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.455579] ACPI: Battery Slot [BAT1] (battery present)
[    0.775148] Freeing initrd memory: 13840k freed
[    0.832904] Linux agpgart interface v0.103
[    0.833048] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    0.833245] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    0.834338] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.834575] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.837788] brd: module loaded
[    0.839460] loop: module loaded
[    0.839811] ata_piix 0000:00:1f.1: version 2.13
[    0.839830] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    0.839837] ata_piix 0000:00:1f.1: power state changed by ACPI to D0
[    0.839865] ata_piix 0000:00:1f.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.839923] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.840596] scsi0 : ata_piix
[    0.840781] scsi1 : ata_piix
[    0.841446] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    0.841452] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    0.841529] ata2: port disabled--ignoring
[    0.842169] Fixed MDIO Bus: probed
[    0.842214] tun: Universal TUN/TAP device driver, 1.6
[    0.842217] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.842337] PPP generic driver version 2.4.2
[    0.842559] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.842591] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.842621] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.842628] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.842730] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.842764] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.842783] ehci_hcd 0000:00:1d.7: debug port 1
[    0.846684] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.846712] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf4544000
[    0.860035] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.860287] hub 1-0:1.0: USB hub found
[    0.860296] hub 1-0:1.0: 8 ports detected
[    0.860456] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.860482] uhci_hcd: USB Universal Host Controller Interface driver
[    0.860518] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.860532] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.860538] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.860627] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.860683] uhci_hcd 0000:00:1d.0: irq 17, io base 0x00001820
[    0.860956] hub 2-0:1.0: USB hub found
[    0.860965] hub 2-0:1.0: 2 ports detected
[    0.861094] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.861108] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.861114] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.861210] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.861261] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    0.861522] hub 3-0:1.0: USB hub found
[    0.861531] hub 3-0:1.0: 2 ports detected
[    0.861660] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.861673] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.861680] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.861767] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.861818] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00001860
[    0.862091] hub 4-0:1.0: USB hub found
[    0.862110] hub 4-0:1.0: 2 ports detected
[    0.862237] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.862250] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.862257] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.862344] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.862381] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[    0.862640] hub 5-0:1.0: USB hub found
[    0.862649] hub 5-0:1.0: 2 ports detected
[    0.862859] usbcore: registered new interface driver libusual
[    0.862940] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.864823] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.864836] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.865112] mousedev: PS/2 mouse device common for all mice
[    0.865422] rtc_cmos 00:07: RTC can wake from S4
[    0.865621] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.865662] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.865820] device-mapper: uevent: version 1.0.3
[    0.865974] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.866109] cpuidle: using governor ladder
[    0.866299] cpuidle: using governor menu
[    0.866303] EFI Variables Facility v0.08 2004-May-17
[    0.866784] TCP cubic registered
[    0.867004] NET: Registered protocol family 10
[    0.867989] NET: Registered protocol family 17
[    0.868056] Registering the dns_resolver key type
[    0.868371] PM: Hibernation image not present or could not be loaded.
[    0.868393] registered taskstats version 1
[    0.891123]   Magic number: 12:32:644
[    0.891297] rtc_cmos 00:07: setting system clock to 2012-05-22 17:38:19 UTC (1337708299)
[    0.891981] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.891985] EDD information not available.
[    0.893167] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.996916] ata1.00: ATA-5: MCBQE64GKMPQ-M1A, 2.9.00, max UDMA/66
[    0.996923] ata1.00: 125304832 sectors, multi 16: LBA 
[    0.997619] ata1.00: configured for UDMA/66
[    0.997886] scsi 0:0:0:0: Direct-Access     ATA      MCBQE64GKMPQ-M1A 2.9. PQ: 0 ANSI: 5
[    0.998135] sd 0:0:0:0: [sda] 125304832 512-byte logical blocks: (64.1 GB/59.7 GiB)
[    0.998169] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.998249] sd 0:0:0:0: [sda] Write Protect is off
[    0.998255] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.998330] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.999636]  sda: sda1 sda2 sda3 sda4
[    1.000609] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.004062] Freeing unused kernel memory: 920k freed
[    1.004495] Write protecting the kernel read-only data: 12288k
[    1.016168] Freeing unused kernel memory: 1608k freed
[    1.025620] Freeing unused kernel memory: 1196k freed
[    1.060192] udevd[94]: starting version 175
[    1.157976] sky2: driver version 1.30
[    1.158209] sky2 0000:06:00.0: power state changed by ACPI to D0
[    1.158239] sky2 0000:06:00.0: power state changed by ACPI to D0
[    1.158296] sky2 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.158416] sky2 0000:06:00.0: setting latency timer to 64
[    1.159276] sky2 0000:06:00.0: Yukon-2 EC Ultra chip revision 3
[    1.160208] sky2 0000:06:00.0: irq 42 for MSI/MSI-X
[    1.166865] sky2 0000:06:00.0: eth0: addr 00:1a:80:58:f1:6c
[    1.245675] firewire_ohci 0000:07:04.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.308156] firewire_ohci: Added fw-ohci device 0000:07:04.1, OHCI v1.0, 4 IR + 4 IT contexts, quirks 0x11
[    1.328543] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[    1.532125] usb 4-1: new full-speed USB device number 2 using uhci_hcd
[    1.808272] firewire_core: created device fw0: GUID 080046030295805b, S400
[    1.944077] usb 5-1: new full-speed USB device number 2 using uhci_hcd
[    2.119663] hub 5-1:1.0: USB hub found
[    2.121475] hub 5-1:1.0: 3 ports detected
[    2.401478] usb 5-1.1: new full-speed USB device number 3 using uhci_hcd
[    2.613487] usb 5-1.2: new full-speed USB device number 4 using uhci_hcd
[    2.809477] usb 5-1.3: new full-speed USB device number 5 using uhci_hcd
[    6.108163] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.122188] udevd[326]: starting version 175
[    6.155988] Adding 1000444k swap on /dev/sda3.  Priority:-1 extents:1 across:1000444k 
[    6.219194] lp: driver loaded but no devices found
[    6.281633] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro
[    6.507630] cfg80211: Calling CRDA to update world regulatory domain
[    6.531121] tpm_tis 00:09: 1.2 TPM (device-id 0xB, rev-id 16)
[    6.645965] type=1400 audit(1337701105.250:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=561 comm="apparmor_parser"
[    6.652425] type=1400 audit(1337701105.258:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=561 comm="apparmor_parser"
[    6.660420] type=1400 audit(1337701105.266:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=561 comm="apparmor_parser"
[    6.672888] ppdev: user-space parallel port driver
[    6.703254] Bluetooth: Core ver 2.16
[    6.707923] NET: Registered protocol family 31
[    6.707931] Bluetooth: HCI device and connection manager initialized
[    6.707938] Bluetooth: HCI socket layer initialized
[    6.707943] Bluetooth: L2CAP socket layer initialized
[    6.707962] Bluetooth: SCO socket layer initialized
[    6.735275] type=1400 audit(1337701105.338:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=600 comm="apparmor_parser"
[    6.740912] type=1400 audit(1337701105.346:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=600 comm="apparmor_parser"
[    6.747811] Bluetooth: RFCOMM TTY layer initialized
[    6.747823] Bluetooth: RFCOMM socket layer initialized
[    6.747828] Bluetooth: RFCOMM ver 1.11
[    6.756421] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.756427] Bluetooth: BNEP filters: protocol multicast
[    6.781162] sony_laptop: Sony Programmable IO Control Driver v0.6
[    6.781189] sony_laptop: detected Type3 model
[    6.800186] acpi device:02: registered as cooling_device2
[    6.812348] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    6.812538] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/SNY6001:00/input/input3
[    6.812659] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    6.813404] input: Sony Vaio Jogdial as /devices/virtual/input/input5
[    6.813774] sony_laptop: device allocated minor is 57
[    6.844306] sony_laptop: Sony Notebook Control Driver v0.6
[    6.844321] sony_laptop: brightness ignored, must be controlled by ACPI video driver
[    6.886400] sky2 0000:06:00.0: eth0: enabling interface
[    6.894409] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.897039] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.923804] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    6.928747] usbcore: registered new interface driver btusb
[    6.946332] intel_rng: FWH not detected
[    6.963366] [drm] Initialized drm 1.1.0 20060810
[    6.976970] leds_ss4200: no LED devices found
[    7.052270] yenta_cardbus 0000:07:04.0: CardBus bridge found [104d:9026]
[    7.052580] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.052589] i915 0000:00:02.0: setting latency timer to 64
[    7.127282] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[    7.127288] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[    7.127410] iwl4965 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.127427] iwl4965 0000:02:00.0: setting latency timer to 64
[    7.140446] iwl4965 0000:02:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[    7.183501] iwl4965 0000:02:00.0: device EEPROM VER=0x36, CALIB=0x5
[    7.185992] input: HID 044e:3013 as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1.2/5-1.2:1.0/input/input6
[    7.186364] generic-usb 0003:044E:3013.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 044e:3013] on usb-0000:00:1d.3-1.2/input0
[    7.189010] yenta_cardbus 0000:07:04.0: ISA IRQ mask 0x0cb8, PCI irq 20
[    7.189018] yenta_cardbus 0000:07:04.0: Socket status: 30000006
[    7.189026] pci_bus 0000:07: Raising subordinate bus# of parent bus (#07) from #08 to #0b
[    7.189261] yenta_cardbus 0000:07:04.0: pcmcia: parent PCI bridge window: [io  0x4000-0x4fff]
[    7.189269] yenta_cardbus 0000:07:04.0: pcmcia: parent PCI bridge window: [mem 0xf4100000-0xf41fffff]
[    7.189276] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf4100000-0xf41fffff: excluding 0xf4100000-0xf410ffff
[    7.189304] yenta_cardbus 0000:07:04.0: pcmcia: parent PCI bridge window: [mem 0x84000000-0x87ffffff pref]
[    7.189310] pcmcia_socket pcmcia_socket0: cs: memory probe 0x84000000-0x87ffffff: excluding 0x84000000-0x87ffffff
[    7.192301] input: HID 044e:3012 as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1.3/5-1.3:1.0/input/input7
[    7.192726] generic-usb 0003:044E:3012.0002: input,hidraw1: USB HID v1.11 Mouse [HID 044e:3012] on usb-0000:00:1d.3-1.3/input0
[    7.192839] usbcore: registered new interface driver usbhid
[    7.192844] usbhid: USB HID core driver
[    7.195448] usb 5-1.2: input irq status -75 received
[    7.203124] r592 0000:07:04.4: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    7.211449] usb 5-1.2: input irq status -75 received
[    7.220251] r592: driver successfully loaded
[    7.227454] usb 5-1.2: input irq status -75 received
[    7.234567] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    7.234573] [drm] Driver supports precise vblank timestamp query.
[    7.243446] usb 5-1.2: input irq status -75 received
[    7.256149] tpm_tis 00:09: Adjusting TPM timeout parameters.
[    7.259445] usb 5-1.2: input irq status -75 received
[    7.259873] iwl4965 0000:02:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
[    7.260139] iwl4965 0000:02:00.0: irq 43 for MSI/MSI-X
[    7.297611] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    7.376952] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.410019] init: failsafe main process (717) killed by TERM signal
[    7.503049] type=1400 audit(1337701106.106:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=812 comm="apparmor_parser"
[    7.507769] type=1400 audit(1337701106.110:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=811 comm="apparmor_parser"
[    7.510296] type=1400 audit(1337701106.114:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=812 comm="apparmor_parser"
[    7.510800] type=1400 audit(1337701106.114:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=812 comm="apparmor_parser"
[    7.538368] type=1400 audit(1337701106.142:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=820 comm="apparmor_parser"
[    7.604700] [drm] initialized overlay support
[    7.654699] fbcon: inteldrmfb (fb0) is primary device
[    7.654909] Console: switching to colour frame buffer device 128x48
[    7.654950] fb0: inteldrmfb frame buffer device
[    7.654954] drm: registered panic notifier
[    7.655029] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    7.713391] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    7.713497] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[    7.713550] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[    7.838009] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[    7.849179] init: alsa-restore main process (891) terminated with status 19
[    7.849602] cfg80211: World regulatory domain updated:
[    7.849607] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    7.849614] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.849620] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.849625] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.849631] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.849636] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.855209] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[    7.947189] hda_codec: ALC262: SKU not ready 0x411111f0
[    7.947272] hda_codec: ALC262: BIOS auto-probing.
[    7.963693] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    7.963986] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    8.054684] iwl4965 0000:02:00.0: loaded firmware version 228.61.2.24
[    8.055064] Registered led device: phy0-led
[    8.055134] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[    8.055722] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xdc000-0xfffff
[    8.055784] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[    8.055842] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[    8.080182] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'
[    8.361061] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.362379] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.939103] init: plymouth-upstart-bridge main process (552) killed by TERM signal
[   14.366876] wlan0: authenticate with 00:1b:2f:98:91:f0 (try 1)
[   14.368476] wlan0: authenticated
[   14.387006] wlan0: waiting for beacon from 00:1b:2f:98:91:f0
[   14.396701] wlan0: beacon received
[   14.404116] wlan0: associate with 00:1b:2f:98:91:f0 (try 1)
[   14.407201] wlan0: RX AssocResp from 00:1b:2f:98:91:f0 (capab=0x411 status=0 aid=3)
[   14.407206] wlan0: associated
[   14.435554] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   25.776036] wlan0: no IPv6 routers present

```

lsmod:
```
Module                  Size  Used by
tpm_infineon           17536  0 
arc4                   12529  2 
joydev                 17693  0 
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
pcmcia                 49310  0 
usbhid                 47199  0 
iwl4965               127900  0 
snd_seq_midi_event     14899  1 snd_seq_midi
r592                   18144  0 
iwl_legacy             83037  1 iwl4965
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
i915                  468764  4 
psmouse                87692  0 
hid                    99559  1 usbhid
drm_kms_helper         46978  1 i915
memstick               16569  1 r592
serio_raw              13211  0 
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              506816  2 iwl4965,iwl_legacy
drm                   242038  5 i915,drm_kms_helper
btusb                  18288  2 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13423  1 i915
sony_laptop            45393  0 
bnep                   18281  2 
rfcomm                 47604  12 
bluetooth             180104  23 btusb,bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tpm_tis                18804  0 
mac_hid                13253  0 
cfg80211              205544  3 iwl4965,iwl_legacy,mac80211
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sky2                   59043  0 

```


Thanks!

---

### Post by mark909 on 2012-05-23
Quick update: I've noticed that if I boot directly into Ubuntu and then i reboot (without turning the machine off) into Windows, Windows cannot find my SD Card Reader too (it correctly finds the Memory Stick reader).
Windows correctly finds and manages the SD card reader if I boot directly into Windows on power on.

Can this be of any help?

Thanks.

---

### Post by mark909 on 2012-05-24
Update: with the help of a friend that has the same ricoh controller, I discovered that the modules that the SD Card Reader uses are sdhci and sdhci_pci. I've tried to load both but nothing changes...

Thanks.

---

