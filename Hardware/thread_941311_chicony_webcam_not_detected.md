---
title: "chicony webcam not detected"
date: 2008-10-08
forum: Hardware
---

### Post by nbhor on 2008-10-08
Hi I have installed ubuntu 8.04 on my laptop. I am trying to get my webcam working but so far no luck. Tried following 2 drivers but still web cam is not working.
1.Driver from this site [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)
2.Driver from [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
Both procedure failed so far.

I know I have following make and model of webcam 
Gateway USB 2.0 Webcam (Chicony) on 64 bit Intel machine

-USB\VID_04F2&PID_B027&REV_9324&MI_00

Vendor - 04F2 Device - B027

Here is output from lsusb
admin@linux:~$ lsusb
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Here is output from dmesg


[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 17:53:40 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] Command line: root=UUID=dbff3a2b-be36-4bcc-be38-cef201802fa2 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfed0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfed0000 - 00000000bfedf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfedf000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 786128) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1310720) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1310720
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7340 checksum 0
[    0.000000] ACPI: RSDP 000F7340, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT BFED37DA, 008C (r1 GATEWA SYSTEM    6040000  LTP        0)
[    0.000000] ACPI: FACP BFEDBBD2, 00F4 (r3 INTEL  CRESTLNE  6040000 ALAN        1)
[    0.000000] ACPI: DSDT BFED4D15, 6E49 (r2 INTEL  CRESTLNE  6040000 INTL 20050624)
[    0.000000] ACPI: FACS BFEDEFC0, 0040
[    0.000000] ACPI: APIC BFEDBCC6, 0068 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: HPET BFEDBD2E, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG BFEDBD66, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA BFEDBDA2, 0032 (r1 Intel   CRESTLN  6040000          5A52)
[    0.000000] ACPI: TMOR BFEDBDD4, 0026 (r1 PTLTD            6040000 PTL         3)
[    0.000000] ACPI: SLIC BFEDBDFA, 0176 (r1 GATEWA SYSTEM    6040000 Kevi        1)
[    0.000000] ACPI: APIC BFEDBF70, 0068 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT BFEDBFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT BFED4A38, 02DD (r1 SataRe SataAhci     1000 INTL 20050624)
[    0.000000] ACPI: SSDT BFED3DF2, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT BFED3D4C, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT BFED3866, 04E6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 786128) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1310720) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1310720
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   786128
[    0.000000]     0:  1048576 ->  1310720
[    0.000000] On node 0 totalpages: 1048175
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1222 pages reserved
[    0.000000]   DMA zone: 2721 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 767752 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 00000000000d4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d4000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000bfed0000 - 00000000bfedf000
[    0.000000] swsusp: Registered nosave memory region: 00000000bfedf000 - 00000000c0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000c0000000 - 00000000e0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000e0000000 - 00000000f0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000f0000000 - 00000000fec00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 00000000fec10000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec10000 - 00000000fed00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fed00000 - 00000000fed14000
[    0.000000] swsusp: Registered nosave memory region: 00000000fed14000 - 00000000fed1a000
[    0.000000] swsusp: Registered nosave memory region: 00000000fed1a000 - 00000000fed1c000
[    0.000000] swsusp: Registered nosave memory region: 00000000fed1c000 - 00000000fed90000
[    0.000000] swsusp: Registered nosave memory region: 00000000fed90000 - 00000000fee00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee00000 - 00000000fee01000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee01000 - 00000000ff000000
[    0.000000] swsusp: Registered nosave memory region: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1029033
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=dbff3a2b-be36-4bcc-be38-cef201802fa2 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   42.346812] Marking TSC unstable due to TSCs unsynchronized
[   42.346816] time.c: Detected 1994.992 MHz processor.
[   42.347990] Console: colour VGA+ 80x25
[   42.347995] console [tty0] enabled
[   42.348037] Checking aperture...
[   42.348053] Calgary: detecting Calgary via BIOS EBDA area
[   42.348057] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   42.348060] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[   42.394722] Placing software IO TLB between 0x103b000 - 0x503b000
[   42.450203] Memory: 4041932k/5242880k available (2489k kernel code, 150768k reserved, 1318k data, 320k init)
[   42.450253] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   42.528693] Calibrating delay using timer specific routine.. 3995.24 BogoMIPS (lpj=7990484)
[   42.528743] Security Framework initialized
[   42.528752] SELinux:  Disabled at boot.
[   42.528771] AppArmor: AppArmor initialized
[   42.528777] Failure registering capabilities with primary security module.
[   42.529552] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   42.532848] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   42.534302] Mount-cache hash table entries: 256
[   42.534505] Initializing cgroup subsys ns
[   42.534513] Initializing cgroup subsys cpuacct
[   42.534538] CPU: L1 I cache: 32K, L1 D cache: 32K
[   42.534541] CPU: L2 cache: 2048K
[   42.534545] CPU 0/0 -> Node 0
[   42.534548] using mwait in idle threads.
[   42.534551] CPU: Physical Processor ID: 0
[   42.534553] CPU: Processor Core ID: 0
[   42.534563] CPU0: Thermal monitoring handled by SMI
[   42.534584] SMP alternatives: switching to UP code
[   42.535890] Early unpacking initramfs... done
[   43.259305] ACPI: Core revision 20070126
[   43.259383] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   43.306733] Using local APIC timer interrupts.
[   43.356838] APIC timer calibration result 10390592
[   43.356841] Detected 10.390 MHz APIC timer.
[   43.356970] SMP alternatives: switching to SMP code
[   43.358111] Booting processor 1/2 APIC 0x1
[   43.368595] Initializing CPU#1
[   43.448796] Calibrating delay using timer specific routine.. 3990.07 BogoMIPS (lpj=7980142)
[   43.448807] CPU: L1 I cache: 32K, L1 D cache: 32K
[   43.448810] CPU: L2 cache: 2048K
[   43.448814] CPU 1/1 -> Node 0
[   43.448816] CPU: Physical Processor ID: 0
[   43.448818] CPU: Processor Core ID: 1
[   43.448829] CPU1: Thermal monitoring enabled (TM2)
[   43.449378] Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
[   43.449440] Brought up 2 CPUs
[   43.449556] CPU0 attaching sched-domain:
[   43.449559]  domain 0: span 03
[   43.449562]   groups: 01 02
[   43.449567]   domain 1: span 03
[   43.449570]    groups: 03
[   43.449574] CPU1 attaching sched-domain:
[   43.449576]  domain 0: span 03
[   43.449579]   groups: 02 01
[   43.449583]   domain 1: span 03
[   43.449586]    groups: 03
[   43.449936] net_namespace: 120 bytes
[   43.450575] Time: 23:41:59  Date: 10/07/08
[   43.450614] NET: Registered protocol family 16
[   43.450946] ACPI: bus type pci registered
[   43.451072] PCI: Using configuration type 1
[   43.453295] ACPI: EC: Look up EC in DSDT
[   43.457086] ACPI: BIOS _OSI(Linux) query ignored
[   43.457090] ACPI: DMI System Vendor: Gateway
[   43.457092] ACPI: DMI Product Name: M-6862
[   43.457094] ACPI: DMI Product Version: 91.22
[   43.457097] ACPI: DMI Board Name:
[   43.457099] ACPI: DMI BIOS Vendor: Gateway
[   43.457101] ACPI: DMI BIOS Date: 03/28/2008
[   43.457104] ACPI: Please send DMI info above to [email]linux-acpi@vger.kernel.org[/email]
[   43.457107] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
[   43.459802] ACPI: Interpreter enabled
[   43.459806] ACPI: (supports S0 S3 S4 S5)
[   43.459833] ACPI: Using IOAPIC for interrupt routing
[   43.469478] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[   43.469482] ACPI: EC: driver started in poll mode
[   43.469559] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   43.470763] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   43.470769] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   43.472104] PCI: Transparent bridge - 0000:00:1e.0
[   43.472166] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   43.472920] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[   43.473172] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   43.473407] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   43.473645] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   43.473914] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   43.493805] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[   43.493989] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   43.494168] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   43.494345] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   43.494522] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   43.494700] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   43.494877] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   43.495056] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   43.495321] Linux Plug and Play Support v0.97 (c) Adam Belay
[   43.495373] pnp: PnP ACPI init
[   43.495385] ACPI: bus type pnp registered
[   43.495941] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   43.499075] pnp: PnP ACPI: found 10 devices
[   43.499079] ACPI: ACPI bus type pnp unregistered
[   43.499542] PCI: Using ACPI for IRQ routing
[   43.499546] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   43.512814] NET: Registered protocol family 8
[   43.512818] NET: Registered protocol family 20
[   43.512875] PCI-GART: No AMD northbridge found.
[   43.512883] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   43.512890] hpet0: 3 64-bit timers, 14318180 Hz
[   43.513946] AppArmor: AppArmor Filesystem Enabled
[   43.516761] Time: hpet clocksource has been installed.
[   43.516775] Switched to high resolution mode on CPU 0
[   43.517366] Switched to high resolution mode on CPU 1
[   43.524759] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   43.524766] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   43.524771] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   43.524777] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   43.524782] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   43.524788] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   43.524794] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[   43.524799] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   43.524812] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   43.524823] system 00:06: ioport range 0x680-0x69f has been reserved
[   43.524828] system 00:06: ioport range 0x800-0x80f has been reserved
[   43.524834] system 00:06: ioport range 0x1000-0x107f has been reserved
[   43.524839] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   43.524844] system 00:06: ioport range 0x1640-0x164f has been reserved
[   43.524849] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[   43.525556] PCI: Bridge: 0000:00:01.0
[   43.525560]   IO window: 2000-2fff
[   43.525565]   MEM window: f3000000-f30fffff
[   43.525570]   PREFETCH window: d0000000-dfffffff
[   43.525576] PCI: Bridge: 0000:00:1c.0
[   43.525580]   IO window: 3000-3fff
[   43.525588]   MEM window: f0000000-f0ffffff
[   43.525594]   PREFETCH window: c2000000-c20fffff
[   43.525602] PCI: Bridge: 0000:00:1c.1
[   43.525606]   IO window: 4000-4fff
[   43.525614]   MEM window: f1000000-f1ffffff
[   43.525619]   PREFETCH window: disabled.
[   43.525627] PCI: Bridge: 0000:00:1c.2
[   43.525631]   IO window: 5000-5fff
[   43.525639]   MEM window: f2000000-f2ffffff
[   43.525644]   PREFETCH window: disabled.
[   43.525652] PCI: Bridge: 0000:00:1e.0
[   43.525654]   IO window: disabled.
[   43.525661]   MEM window: disabled.
[   43.525667]   PREFETCH window: disabled.
[   43.525692] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   43.525699] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   43.525731] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   43.525740] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   43.525770] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[   43.525779] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   43.525810] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   43.525819] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   43.525837] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   43.525852] NET: Registered protocol family 2
[   43.560942] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   43.563094] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   43.568880] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   43.569604] TCP: Hash tables configured (established 524288 bind 65536)
[   43.569608] TCP reno registered
[   43.580928] checking if image is initramfs... it is
[   45.004500] Freeing initrd memory: 7975k freed
[   45.009738] Simple Boot Flag at 0x36 set to 0x1
[   45.011097] audit: initializing netlink socket (disabled)
[   45.011123] audit(1223422920.620:1): initialized
[   45.014775] VFS: Disk quotas dquot_6.5.1
[   45.014884] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   45.015070] io scheduler noop registered
[   45.015074] io scheduler anticipatory registered
[   45.015077] io scheduler deadline registered
[   45.015252] io scheduler cfq registered (default)
[   45.018908] Boot video device is 0000:01:00.0
[   45.019131] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   45.019187] assign_interrupt_mode Found MSI capability
[   45.019232] Allocate Port Service[0000:00:01.0: pcie00]
[   45.019290] Allocate Port Service[0000:00:01.0: pcie02]
[   45.019417] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   45.019491] assign_interrupt_mode Found MSI capability
[   45.019551] Allocate Port Service[0000:00:1c.0: pcie00]
[   45.019603] Allocate Port Service[0000:00:1c.0: pcie02]
[   45.019744] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   45.019819] assign_interrupt_mode Found MSI capability
[   45.019880] Allocate Port Service[0000:00:1c.1: pcie00]
[   45.019937] Allocate Port Service[0000:00:1c.1: pcie02]
[   45.020076] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   45.020150] assign_interrupt_mode Found MSI capability
[   45.020209] Allocate Port Service[0000:00:1c.2: pcie00]
[   45.020263] Allocate Port Service[0000:00:1c.2: pcie02]
[   45.061925] Real Time Clock Driver v1.12ac
[   45.062280] hpet_resources: 0xfed00000 is busy
[   45.062317] Linux agpgart interface v0.102
[   45.062321] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   45.064321] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   45.064425] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   45.064572] PNP: PS/2 Controller [PNP0303: pS2K,PNP0f13: pS2M] at 0x60,0x64 irq 1,12
[   45.067168] serio: i8042 KBD port at 0x60,0x64 irq 1
[   45.067175] serio: i8042 AUX port at 0x60,0x64 irq 12
[   45.080882] mice: PS/2 mouse device common for all mice
[   45.080942] cpuidle: using governor ladder
[   45.080945] cpuidle: using governor menu
[   45.081148] NET: Registered protocol family 1
[   45.081296] registered taskstats version 1
[   45.081479]   Magic number: 12:124:706
[   45.081611] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   45.081616] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   45.081619] EDD information not available.
[   45.081632] Freeing unused kernel memory: 320k freed
[   45.112299] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   46.406853] fuse init (API version 7.9)
[   46.433455] ACPI: SSDT BFED4738, 0238 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   46.433862] ACPI: SSDT BFED4051, 0662 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   46.437560] Monitor-Mwait will be used to enter C-1 state
[   46.437565] Monitor-Mwait will be used to enter C-2 state
[   46.437569] Monitor-Mwait will be used to enter C-3 state
[   46.437772] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   46.437780] ACPI: Processor [CPU0] (supports 8 throttling states)
[   46.438208] ACPI: SSDT BFED4970, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   46.438585] ACPI: SSDT BFED46B3, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   46.440452] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   46.440461] ACPI: Processor [CPU1] (supports 8 throttling states)
[   46.444796] ACPI: Thermal Zone [TZ00] (61 C)
[   46.650948] usbcore: registered new interface driver usbfs
[   46.650984] usbcore: registered new interface driver hub
[   46.651530] usbcore: registered new device driver usb
[   46.652915] USB Universal Host Controller Interface driver v3.0
[   46.652978] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.652994] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   46.653000] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   46.653321] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   46.653363] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[   46.653581] usb usb1: configuration #1 chosen from 1 choice
[   46.653620] hub 1-0:1.0: USB hub found
[   46.653629] hub 1-0:1.0: 2 ports detected
[   46.754721] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   46.754739] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   46.754745] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   46.754783] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   46.754824] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[   46.754998] usb usb2: configuration #1 chosen from 1 choice
[   46.755035] hub 2-0:1.0: USB hub found
[   46.755045] hub 2-0:1.0: 2 ports detected
[   46.858688] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   46.858706] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   46.858712] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   46.858765] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   46.858808] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[   46.858981] usb usb3: configuration #1 chosen from 1 choice
[   46.859017] hub 3-0:1.0: USB hub found
[   46.859026] hub 3-0:1.0: 2 ports detected
[   46.962586] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   46.962605] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   46.962612] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   46.962647] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   46.962687] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[   46.962860] usb usb4: configuration #1 chosen from 1 choice
[   46.962895] hub 4-0:1.0: USB hub found

[   46.962904] hub 4-0:1.0: 2 ports detected
[   47.037601] SCSI subsystem initialized
[   47.066524] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   47.066543] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   47.066549] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   47.066587] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   47.066630] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[   47.066803] usb usb5: configuration #1 chosen from 1 choice
[   47.066844] hub 5-0:1.0: USB hub found
[   47.066854] hub 5-0:1.0: 2 ports detected
[   47.073409] libata version 3.00 loaded.
[   47.170550] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 19
[   47.170616] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   47.170634] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   47.170742] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   47.171615] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   47.171624] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   47.171693] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   47.175620] ehci_hcd 0000:00:1a.7: debug port 1
[   47.175629] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   47.175639] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf3304800
[   47.190308] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   47.190487] usb usb6: configuration #1 chosen from 1 choice
[   47.190526] hub 6-0:1.0: USB hub found
[   47.190537] hub 6-0:1.0: 4 ports detected
[   47.294412] r8169 Gigabit Ethernet driver 2.2LK loaded
[   47.294460] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   47.294490] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   47.294948] eth0: RTL8101e at 0xffffc2000104c000, 00:00:00:00:00:00, XID 34200000 IRQ 507
[   47.295880] ahci 0000:00:1f.2: version 3.0
[   47.295916] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   47.903351] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   47.903358] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part
[   47.903366] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   47.904179] scsi0 : ahci
[   47.904726] scsi1 : ahci
[   47.904814] scsi2 : ahci
[   47.904955] ata1: SATA max UDMA/133 abar m2048@0xf3304000 port 0xf3304100 irq 506
[   47.904961] ata2: SATA max UDMA/133 abar m2048@0xf3304000 port 0xf3304180 irq 506
[   47.904966] ata3: SATA max UDMA/133 abar m2048@0xf3304000 port 0xf3304200 irq 506
[   47.912854] Clocksource tsc unstable (delta = -460286996 ns)
[   47.943571] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   47.973925] ata1.00: ATA-8: WDC WD2500BEVS-22UST0, 01.01A01, max UDMA/133
[   47.973932] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   47.974835] ata1.00: configured for UDMA/133
[   47.998712] ata2: SATA link down (SStatus 0 SControl 300)
[   48.024583] ata3: SATA link down (SStatus 0 SControl 300)
[   48.024788] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-2 01.0 PQ: 0 ANSI: 5
[   48.025491] ata_piix 0000:00:1f.1: version 2.12
[   48.025514] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 19
[   48.025562] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   48.025656] scsi3 : ata_piix
[   48.025940] scsi4 : ata_piix
[   48.026908] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[   48.026913] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[   48.036832] Driver 'sd' needs updating - please use bus_type methods
[   48.039173] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   48.039194] sd 0:0:0:0: [sda] Write Protect is off
[   48.039198] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   48.039226] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   48.039300] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   48.039316] sd 0:0:0:0: [sda] Write Protect is off

[   48.039319] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   48.039346] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   48.039353]  sda: sda1 sda2 sda3 sda4
[   48.070803] sd 0:0:0:0: [sda] Attached SCSI disk
[   48.077727] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   48.236552] ata4.00: ATAPI: Optiarc DVD RW AD-7563A, WX05, max UDMA/33
[   48.319337] ata4.00: configured for UDMA/33
[   48.339483] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7563A  WX05 PQ: 0 ANSI: 5
[   48.339624] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   48.340344] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   48.341190] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   48.341199] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   48.341272] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   48.345187] ehci_hcd 0000:00:1d.7: debug port 1
[   48.345196] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   48.345205] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf3304c00
[   48.352199] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   48.352392] usb usb7: configuration #1 chosen from 1 choice
[   48.352435] hub 7-0:1.0: USB hub found
[   48.352447] hub 7-0:1.0: 6 ports detected
[   48.392208] Driver 'sr' needs updating - please use bus_type methods
[   48.399454] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   48.399461] Uniform CD-ROM driver Revision: 3.20
[   48.399538] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   48.485032] Attempting manual resume
[   48.485037] swsusp: Resume From Partition 8:4
[   48.485040] PM: Checking swsusp image.
[   48.485233] PM: Resume from disk failed.
[   48.513822] kjournald starting.  Commit interval 5 seconds
[   48.513870] EXT3-fs: mounted filesystem with ordered data mode.
[   48.573062] usb 7-4: new high speed USB device using ehci_hcd and address 2
[   48.638844] usb 7-4: configuration #1 chosen from 1 choice
[   52.816697] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   52.858540] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   52.906907] iTCO_vendor_support: vendor-support=0
[   52.946395] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   52.946580] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   52.946655] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   52.999654] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   53.576279] ACPI: Battery Slot [BAT0] (battery present)
[   53.576532] input: Power Button (FF) as /devices/virtual/input/input3
[   53.576745] ACPI: AC Adapter [AC] (off-line)
[   53.604833] ACPI: Power Button (FF) [PWRF]
[   53.604954] input: Lid Switch as /devices/virtual/input/input4
[   53.605229] ACPI: Lid Switch [LID0]
[   53.605344] input: Power Button (CM) as /devices/virtual/input/input5
[   53.625848] ACPI: Power Button (CM) [PWRB]
[   53.625960] input: Sleep Button (CM) as /devices/virtual/input/input6
[   53.657822] ACPI: Sleep Button (CM) [SLPB]
[   54.046444] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input7
[   54.065545] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   54.066570] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8
[   54.085452] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   54.093535] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   54.301522] [fglrx] Maximum main memory to use for locked dma buffers: 3793 MBytes.
[   54.301586] [fglrx] ASYNCIO init succeed!
[   54.303230] [fglrx] PAT is enabled successfully!
[   54.305834] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   54.509469] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   54.510340] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   54.618046] ACPI: PCI Interrupt 0000:01:00.1[B] -> GSI 17 (level, low) -> IRQ 17
[   54.618932] PCI: Setting latency timer of device 0000:01:00.1 to 64
[   55.129494] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   55.129500] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   55.129639] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   55.129652] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   55.130507] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   55.233149] usbcore: registered new interface driver libusual
[   55.273066] Initializing USB Mass Storage driver...
[   55.278332] scsi5 : SCSI emulation for USB Mass Storage devices
[   55.278479] usbcore: registered new interface driver usb-storage
[   55.278484] USB Mass Storage support registered.
[   55.278489] usb-storage: device found at 2
[   55.278491] usb-storage: waiting for device to settle before scanning
[   55.586832] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04711/0x0
[   55.617363] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   57.438720] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels
[   57.439541] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   57.859041] lp: driver loaded but no devices found
[   58.039093] Adding 6000268k swap on /dev/sda4.  Priority:-1 extents:1 across:6000268k
[   58.077686] EXT3 FS on sda3, internal journal
[   58.175669] device-mapper: uevent: version 1.0.3
[   58.175725] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   59.129605] ip_tables: (C) 2000-2006 Netfilter Core Team
[   59.453636] usb-storage: device scan complete
[   59.458537] scsi 5:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   59.632810] No dock devices found.
[   60.956213] ppdev: user-space parallel port driver
[   61.306724] audit(1223437345.499:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5166 profile="/usr/sbin/cupsd" namespace="default"
[   62.153688] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[   62.153764] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   62.315552] Bluetooth: Core ver 2.11
[   62.315827] NET: Registered protocol family 31
[   62.315832] Bluetooth: HCI device and connection manager initialized
[   62.315838] Bluetooth: HCI socket layer initialized
[   62.342728] Bluetooth: L2CAP ver 2.9
[   62.342734] Bluetooth: L2CAP socket layer initialized
[   62.407703] Bluetooth: RFCOMM socket layer initialized
[   62.407732] Bluetooth: RFCOMM TTY layer initialized
[   62.407734] Bluetooth: RFCOMM ver 1.8
[   63.430091] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   65.604439] [fglrx] Reserve Block - 0 offset =  0X1fffc000 length = 0X4000
[   65.604449] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   65.604453] [fglrx] Reserve Block - 2 offset =  0Xff7f000 length = 0X80000
[   65.909277] [fglrx] interrupt source 10000000 successfully enabled
[   65.909282] [fglrx] enable ID = 0x00000006
[   65.909552] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   65.922066] [fglrx] interrupt source 60000001 successfully enabled
[   65.922070] [fglrx] enable ID = 0x00000007
[   65.922263] [fglrx] Receive enable interrupt message with irqEnableMask: 60000001
[   65.922414] [fglrx] interrupt source 00000040 successfully enabled
[   65.922416] [fglrx] enable ID = 0x00000008
[   65.922592] [fglrx] Receive enable interrupt message with irqEnableMask: 00000040
[   65.934948] [fglrx] interrupt source ff00002c successfully enabled
[   65.934953] [fglrx] enable ID = 0x00000009
[   65.935301] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002c
[   65.935599] [fglrx] interrupt source ff00002d successfully enabled
[   65.935604] [fglrx] enable ID = 0x0000000A
[   65.935948] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002d
[   65.936231] [fglrx] interrupt source 20000400 successfully enabled
[   65.936236] [fglrx] enable ID = 0x0000000B
[   65.936582] [fglrx] Receive enable interrupt message with irqEnableMask: 20000400
[   70.649574] NET: Registered protocol family 10
[   70.650179] lo: Disabled Privacy Extensions
[   70.651717] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   75.077980] CPU0 attaching NULL sched-domain.
[   75.077986] CPU1 attaching NULL sched-domain.
[   75.087692] CPU0 attaching sched-domain:
[   75.087696]  domain 0: span 03
[   75.087698]   groups: 01 02
[   75.087701]   domain 1: span 03
[   75.087703]    groups: 03
[   75.087705]    domain 2: span 03
[   75.087707]     groups: 03
[   75.087709] CPU1 attaching sched-domain:
[   75.087710]  domain 0: span 03
[   75.087712]   groups: 02 01
[   75.087714]   domain 1: span 03
[   75.087716]    groups: 03
[   75.087717]    domain 2: span 03
[   75.087719]     groups: 03
[   77.800462] NET: Registered protocol family 17
[   79.426921] wlan0: Initial auth_alg=0
[   79.426932] wlan0: authenticate with AP 00:15:e9:78:0b:76
[   79.429397] wlan0: RX authentication from 00:15:e9:78:0b:76 (alg=0 transaction=2 status=0)
[   79.429404] wlan0: authenticated
[   79.429408] wlan0: associate with AP 00:15:e9:78:0b:76
[   79.432722] wlan0: RX AssocResp from 00:15:e9:78:0b:76 (capab=0x431 status=0 aid=1)
[   79.432730] wlan0: associated
[   79.432736] wlan0: CTS protection enabled (BSSID=00:15:e9:78:0b:76)
[   79.443195] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   86.819723] wlan0: no IPv6 routers present

---

### Post by patrickballeux on 2008-10-12
Hi, 

Your main problem is that you webcam is not even detected as being connected

> 
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


The only USB device found seems to be a network device.  You have to find out why it is not showing first.  This is why your drivers are not working since they are not able to see the device.

Is it bultin or external.  If it is external, disconect it and plug it again, and see the "dmesg" log for new details.  

Are you using a usb hub?  If there are to many devices, you can have some devices not recognized...  

If it is internal, could it be disabled in your BIOS setting?

Let me know!

---

