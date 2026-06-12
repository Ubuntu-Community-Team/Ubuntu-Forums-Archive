---
title: "Wired (82567LM) networking @ Ubuntu 8.042 on a DELL E6500"
date: 2009-01-26
forum: Hardware
---

### Post by Supercows on 2009-01-26
I am having troubles getting my wired network up on a new Ubuntu 8.04 install. Uname -a gives me:
Linux lt-666 2.6.24-23-generic #1 SMP Thu Nov 27 18:13:46 UTC 2008 x86_64 GNU/Linux

It seems a problem with the 82567LM card inside.

dmesg gives me:
> 
0.000000 Initializing cgroup subsys cpuset
    0.000000 Initializing cgroup subsys cpu
    0.000000 Linux version 2.6.24-23-generic (buildd@crested) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Thu Nov 27 18:13:46 UTC 2008 (Ubuntu 2.6.24-23.46-generic)
    0.000000 Command line: root=UUID=6fc8386b-c2c9-44c1-89b2-22db5bb3e854 ro quiet splash
    0.000000 BIOS-provided physical RAM map:
    0.000000  BIOS-e820: 0000000000000000 - 000000000009bc00 (usable)
    0.000000  BIOS-e820: 000000000009bc00 - 00000000000a0000 (reserved)
    0.000000  BIOS-e820: 0000000000100000 - 00000000dd04d400 (usable)
    0.000000  BIOS-e820: 00000000dd04d400 - 00000000dd04f400 (ACPI NVS)
    0.000000  BIOS-e820: 00000000dd04f400 - 00000000e0000000 (reserved)
    0.000000  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
    0.000000  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
    0.000000  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
    0.000000  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
    0.000000  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
    0.000000  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
    0.000000  BIOS-e820: 00000000ffe60000 - 0000000100000000 (reserved)
    0.000000  BIOS-e820: 0000000100000000 - 000000011c000000 (usable)
    0.000000 Entering add_active_range(0, 0, 155) 0 entries of 3200 used
    0.000000 Entering add_active_range(0, 256, 905293) 1 entries of 3200 used
    0.000000 Entering add_active_range(0, 1048576, 1163264) 2 entries of 3200 used
    0.000000 end_pfn_map = 1163264
    0.000000 DMI 2.4 present.
    0.000000 ACPI: RSDP signature @ 0xFFFF8100000FB9C0 checksum 0
    0.000000 ACPI: RSDP 000FB9C0, 0024 (r2 DELL  )
    0.000000 ACPI: XSDT DD051E00, 006C (r1 DELL    M09     27D80C12 ASL        61)
    0.000000 ACPI: FACP DD051C9C, 00F4 (r4 DELL    M09     27D80C12 ASL        61)
    0.000000 ACPI: DSDT DD052400, 6987 (r2 INT430 SYSFexxx     1001 INTL 20050624)
    0.000000 ACPI: FACS DD060C00, 0040
    0.000000 ACPI: HPET DD051F00, 0038 (r1 DELL    M09            1 ASL        61)
    0.000000 ACPI: DMAR DD060400, 0120 (r1 DELL    M09     27D80C12 ASL        61)
    0.000000 ACPI: APIC DD052000, 0068 (r1 DELL    M09     27D80C12 ASL        47)
    0.000000 ACPI: ASF! DD051C00, 006A (r32 DELL    M09     27D80C12 ASL        61)
    0.000000 ACPI: MCFG DD051FC0, 003E (r16 DELL    M09     27D80C12 ASL        61)
    0.000000 ACPI: TCPA DD052300, 0032 (r1                        0 ASL         0)
    0.000000 ACPI: SLIC DD05209C, 0176 (r1 DELL    M09     27D80C12 ASL        61)
    0.000000 ACPI: SSDT DD05032D, 066C (r1  PmRef    CpuPm     3000 INTL 20050624)
    0.000000 No NUMA configuration found
    0.000000 Faking a node at 0000000000000000-000000011c000000
    0.000000 Entering add_active_range(0, 0, 155) 0 entries of 3200 used
    0.000000 Entering add_active_range(0, 256, 905293) 1 entries of 3200 used
    0.000000 Entering add_active_range(0, 1048576, 1163264) 2 entries of 3200 used
    0.000000 Bootmem setup node 0 0000000000000000-000000011c000000
    0.000000 No mptable found.
    0.000000 Zone PFN ranges:
    0.000000   DMA             0 ->     4096
    0.000000   DMA32        4096 ->  1048576
    0.000000   Normal    1048576 ->  1163264
    0.000000 Movable zone start PFN for each node
    0.000000 early_node_map3 active PFN ranges
    0.000000     0:        0 ->      155
    0.000000     0:      256 ->   905293
    0.000000     0:  1048576 ->  1163264
    0.000000 On node 0 totalpages: 1019880
    0.000000   DMA zone: 56 pages used for memmap
    0.000000   DMA zone: 1224 pages reserved
    0.000000   DMA zone: 2715 pages, LIFO batch:0
    0.000000   DMA32 zone: 14280 pages used for memmap
    0.000000   DMA32 zone: 886917 pages, LIFO batch:31
    0.000000   Normal zone: 1568 pages used for memmap
    0.000000   Normal zone: 113120 pages, LIFO batch:31
    0.000000   Movable zone: 0 pages used for memmap
    0.000000 ACPI: PM-Timer IO Port: 0x1008
    0.000000 ACPI: Local APIC address 0xfee00000
    0.000000 ACPI: LAPIC (acpi_id0x00 lapic_id0x00 enabled)
    0.000000 Processor #0 (Bootup-CPU)
    0.000000 ACPI: LAPIC (acpi_id0x01 lapic_id0x01 enabled)
    0.000000 Processor #1
    0.000000 ACPI: LAPIC_NMI (acpi_id0x00 high edge lint0x1)
    0.000000 ACPI: LAPIC_NMI (acpi_id0x01 high edge lint0x1)
    0.000000 ACPI: IOAPIC (id0x02 address0xfec00000 gsi_base0)
    0.000000 IOAPIC0: apic_id 2, address 0xfec00000, GSI 0-23
    0.000000 ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
    0.000000 ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
    0.000000 ACPI: IRQ0 used by override.
    0.000000 ACPI: IRQ2 used by override.
    0.000000 ACPI: IRQ9 used by override.
    0.000000 Setting APIC routing to flat
    0.000000 ACPI: HPET id: 0x8086a201 base: 0xfed00000
    0.000000 Using ACPI (MADT) for SMP configuration information
    0.000000 swsusp: Registered nosave memory region: 000000000009b000 - 000000000009c000
    0.000000 swsusp: Registered nosave memory region: 000000000009c000 - 00000000000a0000
    0.000000 swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
    0.000000 swsusp: Registered nosave memory region: 00000000dd04d000 - 00000000dd04e000
    0.000000 swsusp: Registered nosave memory region: 00000000dd04e000 - 00000000dd04f000
    0.000000 swsusp: Registered nosave memory region: 00000000dd04f000 - 00000000dd050000
    0.000000 swsusp: Registered nosave memory region: 00000000dd050000 - 00000000e0000000
    0.000000 swsusp: Registered nosave memory region: 00000000e0000000 - 00000000f8000000
    0.000000 swsusp: Registered nosave memory region: 00000000f8000000 - 00000000fc000000
    0.000000 swsusp: Registered nosave memory region: 00000000fc000000 - 00000000fec00000
    0.000000 swsusp: Registered nosave memory region: 00000000fec00000 - 00000000fec10000
    0.000000 swsusp: Registered nosave memory region: 00000000fec10000 - 00000000fed18000
    0.000000 swsusp: Registered nosave memory region: 00000000fed18000 - 00000000fed1c000
    0.000000 swsusp: Registered nosave memory region: 00000000fed1c000 - 00000000fed20000
    0.000000 swsusp: Registered nosave memory region: 00000000fed20000 - 00000000fed90000
    0.000000 swsusp: Registered nosave memory region: 00000000fed90000 - 00000000feda0000
    0.000000 swsusp: Registered nosave memory region: 00000000feda0000 - 00000000feda6000
    0.000000 swsusp: Registered nosave memory region: 00000000feda6000 - 00000000fee00000
    0.000000 swsusp: Registered nosave memory region: 00000000fee00000 - 00000000fee10000
    0.000000 swsusp: Registered nosave memory region: 00000000fee10000 - 00000000ffe60000
    0.000000 swsusp: Registered nosave memory region: 00000000ffe60000 - 0000000100000000
    0.000000 Allocating PCI resources starting at e2000000 (gap: e0000000:18000000)
    0.000000 SMP: Allowing 2 CPUs, 0 hotplug CPUs
    0.000000 PERCPU: Allocating 34656 bytes of per cpu data
    0.000000 Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1002752
    0.000000 Policy zone: Normal
    0.000000 Kernel command line: root=UUID=6fc8386b-c2c9-44c1-89b2-22db5bb3e854 ro quiet splash
    0.000000 Initializing CPU#0
    0.000000 PID hash table entries: 4096 (order: 12, 32768 bytes)
    0.000000 Extended CMOS year: 2000
    0.000000 hpet clockevent registered
    0.000000 TSC calibrated against HPET
   11.885589 Marking TSC unstable due to TSCs unsynchronized
   11.885591 time.c: Detected 2393.982 MHz processor.
   11.886732 Console: colour VGA+ 80x25
   11.886735 console tty0 enabled
   11.886753 Checking aperture...
   11.886763 Calgary: detecting Calgary via BIOS EBDA area
   11.886764 Calgary: Unable to locate Rio Grande table in EBDA - bailing!
   11.886766 PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
   11.917929 Placing software IO TLB between 0x1038000 - 0x5038000
   11.949997 Memory: 3937264k/4653056k available (2491k kernel code, 142256k reserved, 1317k data, 320k init)
   11.950028 SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
   12.027333 Calibrating delay using timer specific routine.. 4791.86 BogoMIPS (lpj=9583725)
   12.027362 Security Framework initialized
   12.027368 SELinux:  Disabled at boot.
   12.027377 AppArmor: AppArmor initialized
   12.027380 Failure registering capabilities with primary security module.
   12.027676 Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
   12.029819 Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
   12.030822 Mount-cache hash table entries: 256
   12.030938 Initializing cgroup subsys ns
   12.030944 Initializing cgroup subsys cpuacct
   12.030958 CPU: L1 I cache: 32K, L1 D cache: 32K
   12.030960 CPU: L2 cache: 3072K
   12.030962 CPU 0/0 -> Node 0
   12.030963 using mwait in idle threads.
   12.030964 CPU: Physical Processor ID: 0
   12.030965 CPU: Processor Core ID: 0
   12.030970 CPU0: Thermal monitoring enabled (TM2)
   12.030982 SMP alternatives: switching to UP code
   12.031730 Early unpacking initramfs... done
   12.319249 ACPI: Core revision 20070126
   12.319287 ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
   12.372497 Using local APIC timer interrupts.
   12.414200 APIC timer calibration result 16624883
   12.414201 Detected 16.624 MHz APIC timer.
   12.414264 SMP alternatives: switching to SMP code
   12.414896 Booting processor 1/2 APIC 0x1
   12.425259 Initializing CPU#1
   12.502052 Calibrating delay using timer specific routine.. 4787.97 BogoMIPS (lpj=9575947)
   12.502058 CPU: L1 I cache: 32K, L1 D cache: 32K
   12.502059 CPU: L2 cache: 3072K
   12.502060 CPU 1/1 -> Node 0
   12.502061 CPU: Physical Processor ID: 0
   12.502062 CPU: Processor Core ID: 1
   12.502067 CPU1: Thermal monitoring enabled (TM2)
   12.502489 Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 06
   12.502564 Brought up 2 CPUs
   12.502635 CPU0 attaching sched-domain:
   12.502637  domain 0: span 03
   12.502638   groups: 01 02
   12.502640   domain 1: span 03
   12.502641    groups: 03
   12.502643 CPU1 attaching sched-domain:
   12.502644  domain 0: span 03
   12.502645   groups: 02 01
   12.502646   domain 1: span 03
   12.502647    groups: 03
   12.502822 net_namespace: 120 bytes
   12.503109 Time: 15:24:26  Date: 01/26/09
   12.503130 NET: Registered protocol family 16
   12.503281 ACPI: bus type pci registered
   12.503337 PCI: Using configuration type 1
   12.514209 ACPI: EC: Look up EC in DSDT
   12.514319 ACPI: BIOS _OSI(Linux) query ignored
   12.514320 ACPI: DMI System Vendor: Dell Inc.
   12.514321 ACPI: DMI Product Name: Latitude E6500                  
   12.514322 ACPI: DMI Product Version: 
   12.514323 ACPI: DMI Board Name:       
   12.514324 ACPI: DMI BIOS Vendor: Dell Inc.
   12.514325 ACPI: DMI BIOS Date: 12/18/2008
   12.514326 ACPI: Please send DMI info above to [email]emaillinux-acpi@vger.kernel.org[/email]/email
   12.514327 ACPI: If "acpi_osi=Linux" works better, please notify [email]emaillinux-acpi@vger.kernel.org[/email]/email
   12.530732 ACPI: Interpreter enabled
   12.530734 ACPI: (supports S0 S3 S4 S5)
   12.530745 ACPI: Using IOAPIC for interrupt routing
   12.594575 ACPI: EC: GPE = 0x11, I/O: command/status = 0x934, data = 0x930
   12.594576 ACPI: EC: driver started in poll mode
   12.594619 ACPI: PCI Root Bridge PCI0 (0000:00)
   12.597002 PCI: Transparent bridge - 0000:00:1e.0
   12.597081 ACPI: PCI Interrupt Routing Table \_SB_.PCI0._PRT
   12.597540 ACPI: PCI Interrupt Routing Table \_SB_.PCI0.PCIE._PRT
   12.597686 ACPI: PCI Interrupt Routing Table \_SB_.PCI0.RP01._PRT
   12.597787 ACPI: PCI Interrupt Routing Table \_SB_.PCI0.RP02._PRT
   12.597884 ACPI: PCI Interrupt Routing Table \_SB_.PCI0.RP03._PRT
   12.597988 ACPI: PCI Interrupt Routing Table \_SB_.PCI0.RP04._PRT
   12.609835 ACPI: PCI Interrupt Link LNKA (IRQs 10 *11)
   12.609934 ACPI: PCI Interrupt Link LNKB (IRQs *5 7)
   12.610029 ACPI: PCI Interrupt Link LNKC (IRQs 10 *11)
   12.610123 ACPI: PCI Interrupt Link LNKD (IRQs 5 7 *10 11)
   12.610217 ACPI: PCI Interrupt Link LNKE (IRQs *3 4 5 6 7 10 11 12 14 15)
   12.610312 ACPI: PCI Interrupt Link LNKF (IRQs 3 4 5 6 7 *10 11 12 14 15)
   12.610407 ACPI: PCI Interrupt Link LNKG (IRQs 3 4 5 6 7 *10 11 12 14 15)
   12.610495 ACPI: PCI Interrupt Link LNKH (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
   12.610608 Linux Plug and Play Support v0.97 (c) Adam Belay
   12.610630 pnp: PnP ACPI init
   12.610635 ACPI: bus type pnp registered
   12.697620 pnpacpi: exceeded the max number of mem resources: 12
   12.697767 pnp: PnP ACPI: found 15 devices
   12.697768 ACPI: ACPI bus type pnp unregistered
   12.697941 PCI: Using ACPI for IRQ routing
   12.697943 PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
   12.709705 NET: Registered protocol family 8
   12.709706 NET: Registered protocol family 20
   12.709730 PCI-GART: No AMD northbridge found.
   12.709736 hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
   12.709739 hpet0: 4 64-bit timers, 14318180 Hz
   12.710765 AppArmor: AppArmor Filesystem Enabled
   12.713686 Time: hpet clocksource has been installed.
   12.713694 Switched to high resolution mode on CPU 0
   12.714136 Switched to high resolution mode on CPU 1
   12.721657 system 00:05: ioport range 0xc80-0xcaf has been reserved
   12.721660 system 00:05: ioport range 0xcc0-0xcff could not be reserved
   12.721664 system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
   12.721669 system 00:0b: ioport range 0xcb0-0xcbb has been reserved
   12.721671 system 00:0b: iomem range 0xfed40000-0xfed44fff could not be reserved
   12.721675 system 00:0c: ioport range 0x900-0x92f has been reserved
   12.721676 system 00:0c: ioport range 0x931-0x933 has been reserved
   12.721678 system 00:0c: ioport range 0x935-0x97f has been reserved
   12.721680 system 00:0c: ioport range 0x4d0-0x4d1 has been reserved
   12.721681 system 00:0c: ioport range 0x1000-0x1005 has been reserved
   12.721683 system 00:0c: ioport range 0x1008-0x100f has been reserved
   12.721687 system 00:0d: ioport range 0xf400-0xf4fe has been reserved
   12.721689 system 00:0d: ioport range 0x1006-0x1007 has been reserved
   12.721690 system 00:0d: ioport range 0x100a-0x1059 could not be reserved
   12.721692 system 00:0d: ioport range 0x1060-0x107f has been reserved
   12.721694 system 00:0d: ioport range 0x1080-0x10bf has been reserved
   12.721695 system 00:0d: ioport range 0x1100-0x111f has been reserved
   12.721697 system 00:0d: ioport range 0x1010-0x102f has been reserved
   12.721699 system 00:0d: ioport range 0x809-0x809 has been reserved
   12.721703 system 00:0e: iomem range 0x0-0x9efff could not be reserved
   12.721704 system 00:0e: iomem range 0x9f000-0x9ffff could not be reserved
   12.721706 system 00:0e: iomem range 0xc0000-0xd7fff has been reserved
   12.721708 system 00:0e: iomem range 0xe0000-0xfffff has been reserved
   12.721710 system 00:0e: iomem range 0x100000-0xdd04d3ff could not be reserved
   12.721711 system 00:0e: iomem range 0xdd04d400-0xddafffff could not be reserved
   12.721713 system 00:0e: iomem range 0xddb00000-0xddbfffff could not be reserved
   12.721715 system 00:0e: iomem range 0xffe00000-0xffffffff could not be reserved
   12.721717 system 00:0e: iomem range 0xffa00000-0xffbfffff has been reserved
   12.721719 system 00:0e: iomem range 0xfec00000-0xfec0ffff could not be reserved
   12.721721 system 00:0e: iomem range 0xfee00000-0xfee0ffff could not be reserved
   12.721723 system 00:0e: iomem range 0xfed20000-0xfed3ffff could not be reserved
   12.722040 PCI: Bridge: 0000:00:1c.0
   12.722041   IO window: disabled.
   12.722046   MEM window: disabled.
   12.722049   PREFETCH window: disabled.
   12.722054 PCI: Bridge: 0000:00:1c.1
   12.722055   IO window: disabled.
   12.722060   MEM window: f6900000-f69fffff
   12.722063   PREFETCH window: disabled.
   12.722068 PCI: Bridge: 0000:00:1c.2
   12.722069   IO window: disabled.
   12.722073   MEM window: disabled.
   12.722076   PREFETCH window: disabled.
   12.722081 PCI: Bridge: 0000:00:1c.3
   12.722083   IO window: d000-dfff
   12.722088   MEM window: f6600000-f68fffff
   12.722091   PREFETCH window: f0000000-f01fffff
   12.722102 PCI: Bus 4, cardbus bridge: 0000:03:01.0
   12.722104   IO window: 00001400-000014ff
   12.722107   IO window: 00001800-000018ff
   12.722111   PREFETCH window: 11c000000-11fffffff
   12.722114   MEM window: 120000000-123ffffff
   12.722118 PCI: Bridge: 0000:00:1e.0
   12.722119   IO window: disabled.
   12.722123   MEM window: f6500000-f65fffff
   12.722126   PREFETCH window: disabled.
   12.722152 ACPI: PCI Interrupt 0000:00:1c.0A -> GSI 16 (level, low) -> IRQ 16
   12.722157 PCI: Setting latency timer of device 0000:00:1c.0 to 64
   12.722177 ACPI: PCI Interrupt 0000:00:1c.1B -> GSI 17 (level, low) -> IRQ 17
   12.722181 PCI: Setting latency timer of device 0000:00:1c.1 to 64
   12.722202 ACPI: PCI Interrupt 0000:00:1c.2C -> GSI 18 (level, low) -> IRQ 18
   12.722206 PCI: Setting latency timer of device 0000:00:1c.2 to 64
   12.722226 ACPI: PCI Interrupt 0000:00:1c.3D -> GSI 19 (level, low) -> IRQ 19
   12.722231 PCI: Setting latency timer of device 0000:00:1c.3 to 64
   12.722243 PCI: Setting latency timer of device 0000:00:1e.0 to 64
   12.722256 ACPI: PCI Interrupt 0000:03:01.0A -> GSI 19 (level, low) -> IRQ 19
   12.722265 NET: Registered protocol family 2
   12.757675 IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
   12.758509 TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
   12.762077 TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
   12.762555 TCP: Hash tables configured (established 524288 bind 65536)
   12.762557 TCP reno registered
   12.773669 checking if image is initramfs... it is
   13.338817 Freeing initrd memory: 7537k freed
   13.342138 audit: initializing netlink socket (disabled)
   13.342155 audit(1232983466.416:1): initialized
   13.343799 VFS: Disk quotas dquot_6.5.1
   13.343848 Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
   13.343937 io scheduler noop registered
   13.343938 io scheduler anticipatory registered
   13.343939 io scheduler deadline registered
   13.344017 io scheduler cfq registered (default)
   13.344026 Boot video device is 0000:00:02.0
   13.347282 PCI: Setting latency timer of device 0000:00:1c.0 to 64
   13.347333 assign_interrupt_mode Found MSI capability
   13.347376 Allocate Port Service0000:00:1c.0:pcie00
   13.347403 Allocate Port Service0000:00:1c.0:pcie02
   13.347490 PCI: Setting latency timer of device 0000:00:1c.1 to 64
   13.347540 assign_interrupt_mode Found MSI capability
   13.347580 Allocate Port Service0000:00:1c.1:pcie00
   13.347605 Allocate Port Service0000:00:1c.1:pcie02
   13.347688 PCI: Setting latency timer of device 0000:00:1c.2 to 64
   13.347738 assign_interrupt_mode Found MSI capability
   13.347778 Allocate Port Service0000:00:1c.2:pcie00
   13.347806 Allocate Port Service0000:00:1c.2:pcie02
   13.347889 PCI: Setting latency timer of device 0000:00:1c.3 to 64
   13.347939 assign_interrupt_mode Found MSI capability
   13.347979 Allocate Port Service0000:00:1c.3:pcie00
   13.348002 Allocate Port Service0000:00:1c.3:pcie02
   13.366682 Real Time Clock Driver v1.12ac
   13.366804 hpet_resources: 0xfed00000 is busy
   13.366855 Linux agpgart interface v0.102
   13.366857 Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
   13.366985 serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
   13.367439 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
   13.367530 ACPI: PCI Interrupt 0000:00:03.3B -> GSI 17 (level, low) -> IRQ 17
   13.367601 0000:00:03.3: ttyS1 at I/O 0xef88 (irq = 17) is a 16550A
   13.368092 RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
   13.368141 input: Macintosh mouse button emulation as /devices/virtual/input/input0
   13.368209 PNP: PS/2 Controller PNP0303:KBC,PNP0f13:PS2M at 0x60,0x64 irq 1,12
   13.368479 i8042.c: Warning: Keylock active.
   13.372312 serio: i8042 KBD port at 0x60,0x64 irq 1
   13.372315 serio: i8042 AUX port at 0x60,0x64 irq 12
   13.389517 mice: PS/2 mouse device common for all mice
   13.389543 cpuidle: using governor ladder
   13.389545 cpuidle: using governor menu
   13.389640 NET: Registered protocol family 1
   13.389710 registered taskstats version 1
   13.389824   Magic number: 9:886:437
   13.389890 /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
   13.389892 BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
   13.389893 EDD information not available.
   13.389899 Freeing unused kernel memory: 320k freed
   13.390828 Write protecting the kernel read-only data: 1036k
   13.392175 input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
   14.523050 fuse init (API version 7.9)
   14.535014 ACPI: SSDT DD050999, 0281 (r1  PmRef   BspIst     3000 INTL 20050624)
   14.535168 ACPI: SSDT DD050DF1, 05C6 (r1  PmRef   BspCst     3001 INTL 20050624)
   14.535860 Monitor-Mwait will be used to enter C-1 state
   14.535862 Monitor-Mwait will be used to enter C-2 state
   14.535865 Monitor-Mwait will be used to enter C-3 state
   14.535955 ACPI: CPU0 (power states: C1C1 C2C2 C3C3)
   14.535958 ACPI: Processor CPU0 (supports 8 throttling states)
   14.536199 ACPI: SSDT DD050C1A, 01D7 (r1  PmRef    ApIst     3000 INTL 20050624)
   14.536387 ACPI: SSDT DD0513B7, 008D (r1  PmRef    ApCst     3000 INTL 20050624)
   14.537216 ACPI: CPU1 (power states: C1C1 C2C2 C3C3)
   14.537220 ACPI: Processor CPU1 (supports 8 throttling states)
   14.537231 ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present 20070126
   14.537239 ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present 20070126
   14.544717 ACPI: Thermal Zone THM (47 C)
   14.719248 SCSI subsystem initialized
   14.722818 libata version 3.00 loaded.
   14.723602 ACPI: PCI Interrupt 0000:00:03.2C -> GSI 18 (level, low) -> IRQ 18
   14.723628 PCI: Setting latency timer of device 0000:00:03.2 to 64
   14.723635 ACPI: PCI interrupt for device 0000:00:03.2 disabled
   14.769950 usbcore: registered new interface driver usbfs
   14.769968 usbcore: registered new interface driver hub
   14.770039 ahci 0000:00:1f.2: version 3.0
   14.770063 ACPI: PCI Interrupt 0000:00:1f.2D -> GSI 19 (level, low) -> IRQ 19
   14.770937 usbcore: registered new device driver usb
   14.771571 USB Universal Host Controller Interface driver v3.0
   15.087142 Clocksource tsc unstable (delta = -334515776 ns)
   15.114311 ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl RAID mode
   15.114315 ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part 
   15.114321 PCI: Setting latency timer of device 0000:00:1f.2 to 64
   15.114565 scsi0 : ahci
   15.114606 scsi1 : ahci
   15.114631 scsi2 : ahci
   15.114657 scsi3 : ahci
   15.114685 scsi4 : ahci
   15.114713 scsi5 : ahci
   15.115111 ata1: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1c900 irq 507
   15.115114 ata2: SATA max UDMA/133 irq_stat 0x00000040, connection status changed irq 507
   15.115116 ata3: DUMMY
   15.115116 ata4: DUMMY
   15.115119 ata5: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1cb00 irq 507
   15.115121 ata6: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1cb80 irq 507
   15.193811 ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
   15.207306 ata1.00: ATA-8: Hitachi HTS723216L9A362, FC2OC30F, max UDMA/133
   15.207308 ata1.00: 312581808 sectors, multi 0: LBA48 NCQ (depth 31/32)
   15.208902 ata1.00: configured for UDMA/133
   15.276144 ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
   15.282619 ata2.00: ATAPI: MATSHITA DVD+/-RW UJ862A, 1.02, max UDMA/33
   15.292849 ata2.00: configured for UDMA/33
   15.314232 ata5: SATA link down (SStatus 0 SControl 300)
   15.333087 ata6: SATA link down (SStatus 0 SControl 300)
   15.333186 scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS72321 FC2O PQ: 0 ANSI: 5
   15.335043 scsi 1:0:0:0: CD-ROM            MATSHITA DVD+-RW UJ862A   1.02 PQ: 0 ANSI: 5
   15.335162 ACPI: PCI Interrupt 0000:00:1a.0A -> GSI 20 (level, low) -> IRQ 20
   15.335173 PCI: Setting latency timer of device 0000:00:1a.0 to 64
   15.335176 uhci_hcd 0000:00:1a.0: UHCI Host Controller
   15.335392 uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
   15.335421 uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f60
   15.335522 usb usb1: configuration #1 chosen from 1 choice
   15.335539 hub 1-0:1.0: USB hub found
   15.335544 hub 1-0:1.0: 2 ports detected
   15.340093 Driver 'sd' needs updating - please use bus_type methods
   15.341830 Driver 'sr' needs updating - please use bus_type methods
   15.345164 sd 0:0:0:0: sda 312581808 512-byte hardware sectors (160042 MB)
   15.345177 sd 0:0:0:0: sda Write Protect is off
   15.345180 sd 0:0:0:0: sda Mode Sense: 00 3a 00 00
   15.345196 sd 0:0:0:0: sda Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
   15.345235 sd 0:0:0:0: sda 312581808 512-byte hardware sectors (160042 MB)
   15.345242 sd 0:0:0:0: sda Write Protect is off
   15.345243 sd 0:0:0:0: sda Mode Sense: 00 3a 00 00
   15.345253 sd 0:0:0:0: sda Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
   15.345256  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
   15.404159 sd 0:0:0:0: sda Attached SCSI disk
   15.407107 sd 0:0:0:0: Attached scsi generic sg0 type 0
   15.407120 sr 1:0:0:0: Attached scsi generic sg1 type 5
   15.411222 sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
   15.411224 Uniform CD-ROM driver Revision: 3.20
   15.411255 sr 1:0:0:0: Attached scsi CD-ROM sr0
   15.432840 ACPI: PCI Interrupt 0000:00:1a.1B -> GSI 21 (level, low) -> IRQ 21
   15.432859 PCI: Setting latency timer of device 0000:00:1a.1 to 64
   15.432862 uhci_hcd 0000:00:1a.1: UHCI Host Controller
   15.432881 uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
   15.432909 uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f80
   15.432987 usb usb2: configuration #1 chosen from 1 choice
   15.433004 hub 2-0:1.0: USB hub found
   15.433008 hub 2-0:1.0: 2 ports detected
   15.536714 ACPI: PCI Interrupt 0000:00:1a.2C -> GSI 22 (level, low) -> IRQ 22
   15.536728 PCI: Setting latency timer of device 0000:00:1a.2 to 64
   15.536731 uhci_hcd 0000:00:1a.2: UHCI Host Controller
   15.536749 uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
   15.536778 uhci_hcd 0000:00:1a.2: irq 22, io base 0x00006fa0
   15.536864 usb usb3: configuration #1 chosen from 1 choice
   15.536881 hub 3-0:1.0: USB hub found
   15.536885 hub 3-0:1.0: 2 ports detected
   15.612055 ACPI: PCI Interrupt 0000:00:1d.0A -> GSI 20 (level, low) -> IRQ 20
   15.612070 PCI: Setting latency timer of device 0000:00:1d.0 to 64
   15.612074 uhci_hcd 0000:00:1d.0: UHCI Host Controller
   15.612087 uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
   15.612113 uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f00
   15.612186 usb usb4: configuration #1 chosen from 1 choice
   15.612201 hub 4-0:1.0: USB hub found
   15.612205 hub 4-0:1.0: 2 ports detected
   15.624102 ACPI: PCI Interrupt 0000:00:1d.1B -> GSI 21 (level, low) -> IRQ 21
   15.624110 PCI: Setting latency timer of device 0000:00:1d.1 to 64
   15.624113 uhci_hcd 0000:00:1d.1: UHCI Host Controller
   15.624127 uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
   15.624154 uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f20
   15.624223 usb usb5: configuration #1 chosen from 1 choice
   15.624238 hub 5-0:1.0: USB hub found
   15.624242 hub 5-0:1.0: 2 ports detected
   15.627248 usb 2-1: new full speed USB device using uhci_hcd and address 2
   15.629938 ACPI: PCI Interrupt 0000:00:1d.2C -> GSI 22 (level, low) -> IRQ 22
   15.629946 PCI: Setting latency timer of device 0000:00:1d.2 to 64
   15.629949 uhci_hcd 0000:00:1d.2: UHCI Host Controller
   15.629971 uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
   15.629995 uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
   15.630062 usb usb6: configuration #1 chosen from 1 choice
   15.630076 hub 6-0:1.0: USB hub found
   15.630080 hub 6-0:1.0: 2 ports detected
   15.640057 usb 2-1: configuration #1 chosen from 1 choice
   15.642997 hub 2-1:1.0: USB hub found
   15.643700 hub 2-1:1.0: 3 ports detected
   15.662078 ACPI: PCI Interrupt 0000:03:01.1B -> GSI 17 (level, low) -> IRQ 17
   15.694023 ACPI: PCI Interrupt 0000:00:1a.7C -> GSI 22 (level, low) -> IRQ 22
   15.694772 PCI: Setting latency timer of device 0000:00:1a.7 to 64
   15.694778 ehci_hcd 0000:00:1a.7: EHCI Host Controller
   15.694819 ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
   15.698733 ehci_hcd 0000:00:1a.7: debug port 1
   15.698738 PCI: cache line size of 32 is not supported by device 0000:00:1a.7
   15.698744 ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
   15.713881 ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
   15.713963 usb usb7: configuration #1 chosen from 1 choice
   15.713981 hub 7-0:1.0: USB hub found
   15.713986 hub 7-0:1.0: 6 ports detected
   15.715457 ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=17  MMIO=f65ff800-f65fffff  Max Packet=2048  IR/IT contexts=4/4
   15.729914 ACPI: PCI Interrupt 0000:00:1d.7A -> GSI 20 (level, low) -> IRQ 20
   15.730670 PCI: Setting latency timer of device 0000:00:1d.7 to 64
   15.730676 ehci_hcd 0000:00:1d.7: EHCI Host Controller
   15.730721 ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
   15.734619 ehci_hcd 0000:00:1d.7: debug port 1
   15.734631 PCI: cache line size of 32 is not supported by device 0000:00:1d.7
   15.734636 ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
   15.739252 ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
   15.739356 usb usb8: configuration #1 chosen from 1 choice
   15.739373 hub 8-0:1.0: USB hub found
   15.739377 hub 8-0:1.0: 6 ports detected
   15.775383 Attempting manual resume
   15.775385 swsusp: Resume From Partition 8:6
   15.775386 PM: Checking swsusp image.
   15.775522 PM: Resume from disk failed.
   15.801953 usb 2-1: USB disconnect, address 2
   15.806494 kjournald starting.  Commit interval 5 seconds
   15.806528 EXT3-fs: mounted filesystem with ordered data mode.
   16.168288 usb 7-3: new high speed USB device using ehci_hcd and address 2
   16.304536 usb 7-3: configuration #1 chosen from 1 choice
   16.304629 hub 7-3:1.0: USB hub found
   16.304715 hub 7-3:1.0: 3 ports detected
   16.647432 usb 7-4: new high speed USB device using ehci_hcd and address 3
   16.780636 usb 7-4: configuration #1 chosen from 1 choice
   16.780820 hub 7-4:1.0: USB hub found
   16.780913 hub 7-4:1.0: 3 ports detected
   16.791249 ieee1394: Host added: ID:BUS0-00:1023  GUID354fc0001e838490
   17.323352 usb 7-3.2: new full speed USB device using ehci_hcd and address 5
   17.433503 usb 7-3.2: configuration #1 chosen from 1 choice
   17.633808 usb 7-4.1: new low speed USB device using ehci_hcd and address 6
   17.748938 usb 7-4.1: configuration #1 chosen from 1 choice
   17.989036 usb 3-1: new full speed USB device using uhci_hcd and address 2
   18.162142 usb 3-1: configuration #0 chosen from 1 choice
   18.162144 usb 3-1: config 0 descriptor??
   21.135446 e1000e-ich9m: Intel(R) PRO/1000 Network Driver - 0.2.9.5
   21.135449 e1000e-ich9m: Copyright (c) 1999-2008 Intel Corporation.
   21.135493 ACPI: PCI Interrupt 0000:00:19.0A -> GSI 22 (level, low) -> IRQ 22
   21.135506 PCI: Setting latency timer of device 0000:00:19.0 to 64
   21.185806 0000:00:19.0: 0000:00:19.0: The NVM Checksum Is Not Valid
   21.196080 ACPI: PCI interrupt for device 0000:00:19.0 disabled
   21.213862 e1000e-ich9m: probe of 0000:00:19.0 failed with error -5
   21.336943 parport_pc 00:0a: reported by Plug and Play ACPI
   21.337017 parport0: PC-style at 0x378 (0x778), irq 7, dma 1 PCSPP,TRISTATE,COMPAT,ECP,DMA
   21.361420 dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
   21.370397 input: PC Speaker as /devices/platform/pcspkr/input/input2
   21.374299 pci_hotplug: PCI Hot Plug PCI Core version: 0.5
   21.376598 shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
   21.379405 agpgart: Detected an Intel Intel Integrated Graphics Device Chipset.
   21.380820 agpgart: Detected 32252K stolen memory.
   21.397162 agpgart: AGP aperture is 256M @ 0xe0000000
   21.600434 ACPI: AC Adapter AC (on-line)
   21.745061 input: Lid Switch as /devices/virtual/input/input3
   21.767610 ACPI: Lid Switch LID
   21.767651 input: Power Button (CM) as /devices/virtual/input/input4
   21.778008 ACPI: EC: non-query interrupt received, switching to interrupt mode
   21.846180 ACPI: Power Button (CM) PBTN
   21.846227 input: Sleep Button (CM) as /devices/virtual/input/input5
   21.849730 Yenta: CardBus bridge found at 0000:03:01.0 1028:024f
   21.857282 ricoh-mmc: Ricoh MMC Controller disabling driver
   21.857284 ricoh-mmc: Copyright(c) Philip Langdale
   21.910056 ACPI: Sleep Button (CM) SBTN
   21.948518 ACPI: Battery Slot BAT0 (battery present)
   21.948570 ACPI: Battery Slot BAT1 (battery absent)
   21.980358 input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:34/LNXVIDEO:00/input/input6
   21.980652 Yenta: ISA IRQ mask 0x0c38, PCI irq 19
   21.980655 Socket status: 30000006
   21.980657 Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
   21.980660 pcmcia: parent PCI bridge Memory window: 0xf6500000 - 0xf65fffff
   21.990599 ricoh-mmc: Ricoh MMC controller found at 0000:03:01.3 1180:0843 (rev 11)
   21.990612 ricoh-mmc: Controller is now disabled.
   21.996023 sdhci: Secure Digital Host Controller Interface driver
   21.996025 sdhci: Copyright(c) Pierre Ossman
   21.996060 sdhci: SDHCI controller found at 0000:03:01.2 1180:0822 (rev 21)
   21.996079 ACPI: PCI Interrupt 0000:03:01.2C -> GSI 18 (level, low) -> IRQ 18
   21.996878 mmc0: SDHCI at 0xf65ff600 irq 18 DMA
   22.018093 input: DualPoint Stick as /devices/virtual/input/input7
   22.042840 ACPI: Video Device VID (multi-head: yes  rom: no  post: no)
   22.042890 ACPI: WMI-Acer: Mapper loaded
   22.063330 input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input8
   22.084686 ACPI: PCI Interrupt 0000:00:1b.0A -> GSI 21 (level, low) -> IRQ 21
   22.085407 PCI: Setting latency timer of device 0000:00:1b.0 to 64
   22.127349 input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input9
   22.169975 ieee80211_crypt: registered algorithm 'NULL'
   22.172234 wl: module license 'unspecified' taints kernel.
   22.174589 ACPI: Video Device VID1 (multi-head: yes  rom: no  post: no)
   22.174721 input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input10
   22.190341 ACPI: PCI Interrupt 0000:0c:00.0A -> GSI 17 (level, low) -> IRQ 17
   22.190354 PCI: Setting latency timer of device 0000:0c:00.0 to 64
   22.240264 ieee80211_crypt: registered algorithm 'TKIP'
   22.240691 eth0: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.12
   22.242499 ACPI: Video Device VID2 (multi-head: yes  rom: no  post: no)
   22.292552 usbcore: registered new interface driver hiddev
   22.293957 input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.7/usb7/7-3/7-3.2/7-3.2:1.0/input/input11
   22.374266 input,hidraw0: USB HID v1.11 Mouse Logitech USB Receiver on usb-0000:00:1a.7-3.2
   22.376690 input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.7/usb7/7-3/7-3.2/7-3.2:1.1/input/input12
   22.409204 input,hiddev96,hidraw1: USB HID v1.11 Device Logitech USB Receiver on usb-0000:00:1a.7-3.2
   22.412401 input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1a.7/usb7/7-4/7-4.1/7-4.1:1.0/input/input13
   22.454125 input,hidraw2: USB HID v1.10 Keyboard Dell Dell USB Keyboard on usb-0000:00:1a.7-4.1
   22.454142 usbcore: registered new interface driver usbhid
   22.454145 /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
   23.739567 lp0: using parport0 (interrupt-driven).
   23.796657 Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
   23.796659 Copyright (c) 1999-2006 Intel Corporation.
   23.831846 Adding 8723252k swap on /dev/sda6.  Priority:-1 extents:1 across:8723252k
   24.355658 EXT3 FS on sda5, internal journal
   25.071855 kjournald starting.  Commit interval 5 seconds
   25.080575 EXT3 FS on sda3, internal journal
   25.080579 EXT3-fs: mounted filesystem with ordered data mode.
   25.372003 ip_tables: (C) 2000-2006 Netfilter Core Team
   25.732664 No dock devices found.
   26.620864 ppdev: user-space parallel port driver
   26.749412 audit(1232979884.092:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5366 profile="/usr/sbin/cupsd" namespace="default"
   27.838614 Bluetooth: Core ver 2.11
   27.838820 NET: Registered protocol family 31
   27.838825 Bluetooth: HCI device and connection manager initialized
   27.838833 Bluetooth: HCI socket layer initialized
   27.875682 Bluetooth: L2CAP ver 2.9
   27.875687 Bluetooth: L2CAP socket layer initialized
   27.969226 Bluetooth: RFCOMM socket layer initialized
   27.969752 Bluetooth: RFCOMM TTY layer initialized
   27.969758 Bluetooth: RFCOMM ver 1.8
   30.119901 drm Initialized drm 1.1.0 20060810
   30.133402 ACPI: PCI Interrupt 0000:00:02.0A -> GSI 16 (level, low) -> IRQ 16
   30.133417 PCI: Setting latency timer of device 0000:00:02.0 to 64
   30.133522 drm Initialized i915 1.6.0 20060119 on minor 0
   30.168447 mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
   31.110818 set status page addr 0x03940000
   37.355574 NET: Registered protocol family 10
   37.356197 lo: Disabled Privacy Extensions
   41.698862 CPU0 attaching NULL sched-domain.
   41.698866 CPU1 attaching NULL sched-domain.
   41.729655 CPU0 attaching sched-domain:
   41.729660  domain 0: span 03
   41.729661   groups: 01 02
   41.729664   domain 1: span 03
   41.729665    groups: 03
   41.729666 CPU1 attaching sched-domain:
   41.729667  domain 0: span 03
   41.729668   groups: 02 01
   41.729669   domain 1: span 03
   41.729670    groups: 03
   46.481849 eth0: no IPv6 routers present
  163.911745 usb 8-2: new high speed USB device using ehci_hcd and address 2
  163.920562 usb 8-2: configuration #1 chosen from 1 choice
  163.997753 usbcore: registered new interface driver libusual
  164.012055 Initializing USB Mass Storage driver...
  164.012236 scsi6 : SCSI emulation for USB Mass Storage devices
  164.012364 usbcore: registered new interface driver usb-storage
  164.012366 USB Mass Storage support registered.
  164.012578 usb-storage: device found at 2
  164.012579 usb-storage: waiting for device to settle before scanning
  165.407102 usb-storage: device scan complete
  165.407955 scsi 6:0:0:0: Direct-Access     usb2.0   flash disk       2.20 PQ: 0 ANSI: 2
  165.410655 sd 6:0:0:0: sdb 4136960 512-byte hardware sectors (2118 MB)
  165.418951 sd 6:0:0:0: sdb Write Protect is off
  165.418958 sd 6:0:0:0: sdb Mode Sense: 0b 00 00 08
  165.418962 sd 6:0:0:0: sdb Assuming drive cache: write through
  165.421703 sd 6:0:0:0: sdb 4136960 512-byte hardware sectors (2118 MB)
  165.422318 sd 6:0:0:0: sdb Write Protect is off
  165.422325 sd 6:0:0:0: sdb Mode Sense: 0b 00 00 08
  165.422328 sd 6:0:0:0: sdb Assuming drive cache: write through
  165.422336  sdb: unknown partition table
  165.424917 sd 6:0:0:0: sdb Attached SCSI removable disk
  165.424989 sd 6:0:0:0: Attached scsi generic sg2 type 0
  184.745100 e1000e: Intel(R) PRO/1000 Network Driver - 0.5.11.2-NAPI
  184.745109 e1000e: Copyright (c) 1999-2008 Intel Corporation.
  184.745198 ACPI: PCI Interrupt 0000:00:19.0A -> GSI 22 (level, low) -> IRQ 22
  184.745221 PCI: Setting latency timer of device 0000:00:19.0 to 64
[B]  184.821671 0000:00:19.0: 0000:00:19.0: The NVM Checksum Is Not Valid/
  184.832076 ACPI: PCI interrupt for device 0000:00:19.0 disabled
  184.832102 e1000e: probe of 0000:00:19.0 failed with error -5[/B]

The checksum error is not good I think. Searching google gives me:
[https://bugzilla.redhat.com/show_bug.cgi?id=459202](https://bugzilla.redhat.com/show_bug.cgi?id=459202) and
[http://lkml.org/lkml/2008/9/25/515](http://lkml.org/lkml/2008/9/25/515)

Is there a workaround in Ubuntu? Someone?

---

### Post by Supercows on 2009-01-27
Nobody? :(

---

### Post by ifkm on 2009-04-28
Maybe this helps:

[https://bugs.launchpad.net/debian/+bug/322737/comments/6](https://bugs.launchpad.net/debian/+bug/322737/comments/6)

Just found this cause I'm installing 08.04.2 just now at a system with this chip and it said that there's no ethernet adapter available - so after the installation is finished I will try this.

Kind regards

ifkm

---

### Post by ciampix on 2009-11-12
No, I've got the very same problem 

The NVM Checksum Is Not Valid/
ACPI: PCI interrupt for device 0000:00:19.0 disabled
e1000e: probe of 0000:00:19.0 failed with error -5

with the same dell latitude 6500 & karmic (64). It should be fixed by ages!!! :-(

---

