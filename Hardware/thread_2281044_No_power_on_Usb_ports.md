---
title: "No power on Usb ports"
date: 2015-06-04
forum: Hardware
---

### Post by raptorhunter3 on 2015-06-04
There's no power going to my usb ports. The mouse doesn't light up at all (it works on live distros) and the usb 3 hard drive turns on, but I can't see it in fdisk. I've already tried enabling all the tunables in powertop. I also tried the first two solutions here by editing by grub and it still doesn't work???

[http://askubuntu.com/questions/526082/2-usb-ports-stopped-working](http://askubuntu.com/questions/526082/2-usb-ports-stopped-working)

---

I'm running Mint 17 x64 on a Lenovo Flex 2 14.

uname -a: 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

lsusb: Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

dmesg | grep usb

[    9.186006] usb 1-6: Device not responding to set address.
[    9.389925] usb 1-6: device not accepting address 6, error -71
[    9.502117] usb 1-6: new full-speed USB device number 7 using xhci_hcd
[    9.519628] usb 1-6: New USB device found, idVendor=0cf3, idProduct=3004
[    9.519638] usb 1-6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    9.578010] usb 1-3: USB disconnect, device number 2
[    9.626383] usb 1-4: USB disconnect, device number 3
[    9.682308] usb 1-6: USB disconnect, device number 7
[    9.682542] usb 1-8: USB disconnect, device number 5
[    9.743187] usb 2-1: USB disconnect, device number 2
[    9.743243] usb 2-1: Failed to set U1 timeout to 0x0,error code -19
[    9.743248] usb 2-1: Failed to set U1 timeout to 0x32,error code -19
[    9.743252] usb 2-1: Failed to set U2 timeout to 0x28,error code -19
[   14.751254] usb 2-1: Failed to set U1 timeout to 0x0,error code -19
[   14.751267] usb 2-1: Failed to set U1 timeout to 0x1e,error code -19
[   14.751276] usb 2-1: Failed to set U2 timeout to 0x28,error code -19

---

### Post by dino99 on 2015-06-04
****** device not accepting address 6 ************

maybe check again the usb bios settings, and/or plug that mouse into an other usb port (i suppose the mouse is an usb2 one, so select a usb port)

you can also update the ids:

> sudo update-usbids
sudo update-pciids

---

### Post by raptorhunter3 on 2015-06-04
I tried your commands and still nothing. The mouse doesn't work in ANY usb port (it works fine on windows and other linux) and the usb hard drive can only work in the usb 3 port. 

Here's my full dmesg if you want it:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-37-generic (buildd@kapok) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 (Ubuntu 3.13.0-37.64-generic 3.13.11.7)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.13.0-37-generic root=UUID=07629e35-dfa6-431a-9143-99416af1dd9c ro acpi=force irqpoll quiet splash usbcore.autosuspend=-1 vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009cfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bac4dfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bac4e000-0x00000000bae4ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bae50000-0x00000000cb067fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cb068000-0x00000000cce8efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cce8f000-0x00000000ccf9efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ccf9f000-0x00000000ccffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000ccfff000-0x00000000ccffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cd000000-0x00000000cf9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fe101000-0x00000000fe112fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed08000-0x00000000fed08fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffa00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000022f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: LENOVO 20404/Lenovo Flex 2-14, BIOS A0CN36WW 04/30/2015
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x22f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: write-back
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 00E0000000 mask 7FE0000000 uncachable
[    0.000000]   1 base 00D0000000 mask 7FF0000000 uncachable
[    0.000000]   2 base 00CE000000 mask 7FFE000000 uncachable
[    0.000000]   3 base 00CD000000 mask 7FFF000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xcd000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f0130-0x000f013f] mapped at [ffff8800000f0130]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x22f400000-0x22f5fffff]
[    0.000000]  [mem 0x22f400000-0x22f5fffff] page 2M
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x22c000000-0x22f3fffff]
[    0.000000]  [mem 0x22c000000-0x22f3fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x22bffffff]
[    0.000000]  [mem 0x200000000-0x22bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbac4dfff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0xbabfffff] page 2M
[    0.000000]  [mem 0xbac00000-0xbac4dfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbae50000-0xcb067fff]
[    0.000000]  [mem 0xbae50000-0xbaffffff] page 4k
[    0.000000]  [mem 0xbb000000-0xcaffffff] page 2M
[    0.000000]  [mem 0xcb000000-0xcb067fff] page 4k
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] BRK [0x01fe6000, 0x01fe6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xccfff000-0xccffffff]
[    0.000000]  [mem 0xccfff000-0xccffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x348b0000-0x3644ffff]
[    0.000000] ACPI: RSDP 00000000000f0150 000024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 00000000ccffe170 0000B4 (v01 LENOVO CB-01    00000001 LENO 00000001)
[    0.000000] ACPI: FACP 00000000ccffb000 00010C (v05 LENOVO CB-01    00000001 LENO 00000001)
[    0.000000] ACPI Error: Gpe0Block - 32-bit FADT register is too long (32 bytes, 256 bits) to convert to GAS struct - 255 bits max, truncating (20131115/tbfadt-202)
[    0.000000] ACPI: DSDT 00000000ccfe6000 010A81 (v02 LENOVO  HSW-LPT 00000000 INTL 20120711)
[    0.000000] ACPI: FACS 00000000ccf9c000 000040
[    0.000000] ACPI: ASF! 00000000ccffd000 0000A5 (v32 LENOVO CB-01    00000001 LENO 00000001)
[    0.000000] ACPI: HPET 00000000ccffa000 000038 (v01 LENOVO CB-01    00000001 LENO 00000001)
[    0.000000] ACPI: LPIT 00000000ccff9000 000094 (v01 LENOVO CB-01    00000001 LENO 00000001)
[    0.000000] ACPI: APIC 00000000ccff8000 000098 (v01 LENOVO CB-01    00000001 LENO 00000001)
[    0.000000] ACPI: MCFG 00000000ccff7000 00003C (v01 LENOVO CB-01    00000001 LENO 00000001)
[    0.000000] ACPI: SSDT 00000000ccfe5000 000228 (v01 LENOVO sensrhub 00000000 INTL 20120711)
[    0.000000] ACPI: SSDT 00000000ccfe2000 002028 (v01 LENOVO PtidDevc 00001000 INTL 20120711)
[    0.000000] ACPI: SSDT 00000000ccfe1000 000539 (v01 LENOVO  Cpu0Ist 00003000 INTL 20120711)
[    0.000000] ACPI: SSDT 00000000ccfe0000 000AD8 (v01 LENOVO    CpuPm 00003000 INTL 20120711)
[    0.000000] ACPI: SSDT 00000000ccfdc000 003536 (v01 LENOVO  SaSsdt  00003000 INTL 20120711)
[    0.000000] ACPI: UEFI 00000000ccfdb000 000042 (v01 LENOVO CB-01    00000001 LENO 00000001)
[    0.000000] ACPI: MSDM 00000000ccf76000 000055 (v03 LENOVO CB-01    00000001 LENO 00000001)
[    0.000000] ACPI: BATB 00000000ccfda000 000046 (v01 LENOVO CB-01    00000001 LENO 00000001)
[    0.000000] ACPI: FPDT 00000000ccfd9000 000064 (v01 LENOVO CB-01    00000001 LENO 00000001)
[    0.000000] ACPI: SLIC 00000000ccfd8000 000176 (v01 LENOVO CB-01    00000001 LENO 00000001)
[    0.000000] ACPI: UEFI 00000000ccfd7000 0002A6 (v01 LENOVO CB-01    00000001 LENO 00000001)
[    0.000000] ACPI: CSRT 00000000ccfd5000 0000C4 (v01 LENOVO CB-01    00000001 LENO 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000022f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x22f5fffff]
[    0.000000]   NODE_DATA [mem 0x22f5f7000-0x22f5fbfff]
[    0.000000]  [ffffea0000000000-ffffea0008bfffff] PMD -> [ffff880226c00000-ffff88022ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x22f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xbac4dfff]
[    0.000000]   node   0: [mem 0xbae50000-0xcb067fff]
[    0.000000]   node   0: [mem 0xccfff000-0xccffffff]
[    0.000000]   node   0: [mem 0x100000000-0x22f5fffff]
[    0.000000] On node 0 totalpages: 2073603
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12922 pages used for memmap
[    0.000000]   DMA32 zone: 826983 pages, LIFO batch:31
[    0.000000]   Normal zone: 19416 pages used for memmap
[    0.000000]   Normal zone: 1242624 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 56
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbac4e000-0xbae4ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcb068000-0xcce8efff]
[    0.000000] PM: Registered nosave memory: [mem 0xcce8f000-0xccf9efff]
[    0.000000] PM: Registered nosave memory: [mem 0xccf9f000-0xccffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xcd000000-0xcf9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcfa00000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfe100fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe101000-0xfe112fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe113000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed07fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed08000-0xfed08fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed09000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffffffff]
[    0.000000] e820: [mem 0xcfa00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88022f200000 s86400 r8192 d24192 u262144
[    0.000000] pcpu-alloc: s86400 r8192 d24192 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2041180
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-37-generic root=UUID=07629e35-dfa6-431a-9143-99416af1dd9c ro acpi=force irqpoll quiet splash usbcore.autosuspend=-1 vt.handoff=7
[    0.000000] Misrouted IRQ fixup and polling support enabled
[    0.000000] This may significantly impact system performance
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8051416K/8294412K available (7375K kernel code, 1144K rwdata, 3404K rodata, 1336K init, 1444K bss, 242996K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:1016 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2593.955 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5187.91 BogoMIPS (lpj=10375820)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000035] Security Framework initialized
[    0.000054] AppArmor: AppArmor initialized
[    0.000055] Yama: becoming mindful.
[    0.000692] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002623] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003433] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.003445] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.003681] Initializing cgroup subsys memory
[    0.003687] Initializing cgroup subsys devices
[    0.003689] Initializing cgroup subsys freezer
[    0.003690] Initializing cgroup subsys blkio
[    0.003692] Initializing cgroup subsys perf_event
[    0.003694] Initializing cgroup subsys hugetlb
[    0.003718] CPU: Physical Processor ID: 0
[    0.003719] CPU: Processor Core ID: 0
[    0.003723] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.003723] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.004819] mce: CPU supports 7 MCE banks
[    0.004832] CPU0: Thermal monitoring enabled (TM1)
[    0.004844] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.004844] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0
[    0.004844] tlb_flushall_shift: 6
[    0.004967] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
[    0.006084] ACPI: Core revision 20131115
[    0.016998] ACPI: All ACPI Tables successfully acquired
[    0.022469] ftrace: allocating 28541 entries in 112 pages
[    0.037001] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076711] smpboot: CPU0: Intel(R) Core(TM) i7-4510U CPU @ 2.00GHz (fam: 06, model: 45, stepping: 01)
[    0.076718] TSC deadline timer enabled
[    0.076727] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.076734] ... version:                3
[    0.076735] ... bit width:              48
[    0.076736] ... generic registers:      4
[    0.076737] ... value mask:             0000ffffffffffff
[    0.076738] ... max period:             0000ffffffffffff
[    0.076739] ... fixed-purpose events:   3
[    0.076740] ... event mask:             000000070000000f
[    0.078489] x86: Booting SMP configuration:
[    0.092982] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.078491] .... node  #0, CPUs:      #1 #2 #3
[    0.121639] x86: Booted up 1 node, 4 CPUs
[    0.121643] smpboot: Total of 4 processors activated (20751.64 BogoMIPS)
[    0.126802] devtmpfs: initialized
[    0.129082] EVM: security.selinux
[    0.129084] EVM: security.SMACK64
[    0.129085] EVM: security.ima
[    0.129086] EVM: security.capability
[    0.129142] PM: Registering ACPI NVS region [mem 0xcce8f000-0xccf9efff] (1114112 bytes)
[    0.129942] pinctrl core: initialized pinctrl subsystem
[    0.130000] regulator-dummy: no parameters
[    0.130031] RTC time:  8:46:47, date: 06/04/15
[    0.130064] NET: Registered protocol family 16
[    0.130172] cpuidle: using governor ladder
[    0.130174] cpuidle: using governor menu
[    0.130222] ACPI: bus type PCI registered
[    0.130224] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.130282] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.130284] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.136455] PCI: Using configuration type 1 for base access
[    0.137385] bio: create slab <bio-0> at 0
[    0.137530] ACPI: Added _OSI(Module Device)
[    0.137531] ACPI: Added _OSI(Processor Device)
[    0.137533] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.137534] ACPI: Added _OSI(Processor Aggregator Device)
[    0.142210] ACPI: Executed 1 blocks of module-level executable AML code
[    0.145448] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.146718] ACPI: SSDT 00000000cce82c18 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20120711)
[    0.147299] ACPI: Dynamic OEM Table Load:
[    0.147301] ACPI: SSDT           (null) 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20120711)
[    0.150881] ACPI: SSDT 00000000cce82618 0005AA (v01  PmRef    ApIst 00003000 INTL 20120711)
[    0.151536] ACPI: Dynamic OEM Table Load:
[    0.151538] ACPI: SSDT           (null) 0005AA (v01  PmRef    ApIst 00003000 INTL 20120711)
[    0.154712] ACPI: SSDT 00000000cce81d98 000119 (v01  PmRef    ApCst 00003000 INTL 20120711)
[    0.155287] ACPI: Dynamic OEM Table Load:
[    0.155288] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20120711)
[    0.168268] ACPI: Interpreter enabled
[    0.168283] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.168301] ACPI: (supports S0 S1 S3 S4 S5)
[    0.168303] ACPI: Using IOAPIC for interrupt routing
[    0.168330] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.168554] ACPI: No dock devices found.
[    0.184478] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.184484] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.184554] \_SB_.PCI0:_OSC invalid UUID
[    0.184555] _OSC request data:1 1f 0 
[    0.184559] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.185419] PCI host bridge to bus 0000:00
[    0.185422] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.185425] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.185426] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.185428] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.185430] pci_bus 0000:00: root bus resource [mem 0xcfa00000-0xfeafffff]
[    0.185438] pci 0000:00:00.0: [8086:0a04] type 00 class 0x060000
[    0.185602] pci 0000:00:02.0: [8086:0a16] type 00 class 0x030000
[    0.185615] pci 0000:00:02.0: reg 0x10: [mem 0xe0000000-0xe03fffff 64bit]
[    0.185622] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.185628] pci 0000:00:02.0: reg 0x20: [io  0x4000-0x403f]
[    0.185783] pci 0000:00:03.0: [8086:0a0c] type 00 class 0x040300
[    0.185792] pci 0000:00:03.0: reg 0x10: [mem 0xe0610000-0xe0613fff 64bit]
[    0.185970] pci 0000:00:14.0: [8086:9c31] type 00 class 0x0c0330
[    0.185988] pci 0000:00:14.0: reg 0x10: [mem 0xe0600000-0xe060ffff 64bit]
[    0.186045] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.186159] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.186190] pci 0000:00:16.0: [8086:9c3a] type 00 class 0x078000
[    0.186210] pci 0000:00:16.0: reg 0x10: [mem 0xe0619000-0xe061901f 64bit]
[    0.186278] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.186427] pci 0000:00:1b.0: [8086:9c20] type 00 class 0x040300
[    0.186440] pci 0000:00:1b.0: reg 0x10: [mem 0xe0614000-0xe0617fff 64bit]
[    0.186501] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.186616] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.186642] pci 0000:00:1c.0: [8086:9c10] type 01 class 0x060400
[    0.186708] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.186826] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.186854] pci 0000:00:1c.2: [8086:9c14] type 01 class 0x060400
[    0.186915] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.187032] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.187061] pci 0000:00:1c.3: [8086:9c16] type 01 class 0x060400
[    0.187122] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.187240] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.187274] pci 0000:00:1f.0: [8086:9c43] type 00 class 0x060100
[    0.187516] pci 0000:00:1f.2: [8086:9c03] type 00 class 0x010601
[    0.187531] pci 0000:00:1f.2: reg 0x10: [io  0x4088-0x408f]
[    0.187538] pci 0000:00:1f.2: reg 0x14: [io  0x4094-0x4097]
[    0.187545] pci 0000:00:1f.2: reg 0x18: [io  0x4080-0x4087]
[    0.187552] pci 0000:00:1f.2: reg 0x1c: [io  0x4090-0x4093]
[    0.187559] pci 0000:00:1f.2: reg 0x20: [io  0x4060-0x407f]
[    0.187566] pci 0000:00:1f.2: reg 0x24: [mem 0xe061c000-0xe061c7ff]
[    0.187601] pci 0000:00:1f.2: PME# supported from D3hot
[    0.187733] pci 0000:00:1f.3: [8086:9c22] type 00 class 0x0c0500
[    0.187746] pci 0000:00:1f.3: reg 0x10: [mem 0xe0618000-0xe06180ff 64bit]
[    0.187765] pci 0000:00:1f.3: reg 0x20: [io  0xefa0-0xefbf]
[    0.187956] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.188028] pci 0000:02:00.0: [168c:0036] type 00 class 0x028000
[    0.188050] pci 0000:02:00.0: reg 0x10: [mem 0xe0500000-0xe057ffff 64bit]
[    0.188103] pci 0000:02:00.0: reg 0x30: [mem 0xffff0000-0xffffffff pref]
[    0.188155] pci 0000:02:00.0: supports D1 D2
[    0.188157] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.188183] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.194681] pci 0000:00:1c.2: PCI bridge to [bus 02]
[    0.194686] pci 0000:00:1c.2:   bridge window [mem 0xe0500000-0xe05fffff]
[    0.194759] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    0.194776] pci 0000:03:00.0: reg 0x10: [io  0x3000-0x30ff]
[    0.194804] pci 0000:03:00.0: reg 0x18: [mem 0xe0404000-0xe0404fff 64bit]
[    0.194821] pci 0000:03:00.0: reg 0x20: [mem 0xe0400000-0xe0403fff 64bit]
[    0.194895] pci 0000:03:00.0: supports D1 D2
[    0.194897] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.194930] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.206691] pci 0000:00:1c.3: PCI bridge to [bus 03]
[    0.206694] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.206698] pci 0000:00:1c.3:   bridge window [mem 0xe0400000-0xe04fffff]
[    0.211125] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.211174] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.211220] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.211266] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *7
[    0.211314] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.211360] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.211406] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.211451] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.211875] ACPI: Enabled 10 GPEs in block 00 to 7F
[    0.211882] ACPI: \_SB_.PCI0: notify handler is installed
[    0.211960] Found 1 acpi root devices
[    0.212004] ACPI : EC: GPE = 0x22, I/O: command/status = 0x66, data = 0x62
[    0.212094] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.212097] vgaarb: loaded
[    0.212098] vgaarb: bridge control possible 0000:00:02.0
[    0.212245] SCSI subsystem initialized
[    0.212288] libata version 3.00 loaded.
[    0.212304] ACPI: bus type USB registered
[    0.212319] usbcore: registered new interface driver usbfs
[    0.212326] usbcore: registered new interface driver hub
[    0.212345] usbcore: registered new device driver usb
[    0.212442] PCI: Using ACPI for IRQ routing
[    0.213757] PCI: pci_cache_line_size set to 64 bytes
[    0.213792] e820: reserve RAM buffer [mem 0x0009d000-0x0009ffff]
[    0.213794] e820: reserve RAM buffer [mem 0xbac4e000-0xbbffffff]
[    0.213795] e820: reserve RAM buffer [mem 0xcb068000-0xcbffffff]
[    0.213797] e820: reserve RAM buffer [mem 0xcd000000-0xcfffffff]
[    0.213798] e820: reserve RAM buffer [mem 0x22f600000-0x22fffffff]
[    0.213869] NetLabel: Initializing
[    0.213871] NetLabel:  domain hash size = 128
[    0.213872] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.213884] NetLabel:  unlabeled traffic allowed by default
[    0.213940] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.213946] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.215977] Switched to clocksource hpet
[    0.220495] AppArmor: AppArmor Filesystem Enabled
[    0.220517] pnp: PnP ACPI init
[    0.220530] ACPI: bus type PNP registered
[    0.220563] pnp 00:00: [dma 4]
[    0.220581] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.220600] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.220702] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.220744] system 00:03: [io  0xffff] has been reserved
[    0.220746] system 00:03: [io  0xffff] has been reserved
[    0.220747] system 00:03: [io  0xffff] has been reserved
[    0.220749] system 00:03: [io  0x1800-0x18fe] could not be reserved
[    0.220752] system 00:03: [mem 0xfe800000-0xfe80ffff] has been reserved
[    0.220755] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.220801] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.220842] system 00:05: [io  0x1854-0x1857] has been reserved
[    0.220845] system 00:05: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.220918] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.220940] pnp 00:07: Plug and Play ACPI device, IDs SYN2b3a PNP0f13 SYN2b00 SYN0002 (active)
[    0.221065] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.221068] system 00:08: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.221070] system 00:08: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.221071] system 00:08: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.221073] system 00:08: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.221075] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.221077] system 00:08: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.221079] system 00:08: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.221081] system 00:08: [mem 0xff000000-0xffffffff] could not be reserved
[    0.221083] system 00:08: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.221085] system 00:08: [mem 0xcfa00000-0xcfa0ffff] has been reserved
[    0.221087] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.224052] system 00:09: [mem 0xfe102000-0xfe102fff] has been reserved
[    0.224055] system 00:09: [mem 0xfe104000-0xfe104fff] has been reserved
[    0.224056] system 00:09: [mem 0xfe106000-0xfe106fff] has been reserved
[    0.224058] system 00:09: [mem 0xfe108000-0xfe108fff] has been reserved
[    0.224060] system 00:09: [mem 0xfe10a000-0xfe10afff] has been reserved
[    0.224062] system 00:09: [mem 0xfe10c000-0xfe10cfff] has been reserved
[    0.224064] system 00:09: [mem 0xfe10e000-0xfe10efff] has been reserved
[    0.224066] system 00:09: [mem 0xfe112000-0xfe112fff] has been reserved
[    0.224067] system 00:09: [mem 0xfe111000-0xfe111007] has been reserved
[    0.224069] system 00:09: [mem 0xfe111014-0xfe111fff] has been reserved
[    0.224072] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.228467] pnp: PnP ACPI: found 10 devices
[    0.228468] ACPI: bus type PNP unregistered
[    0.234416] pci 0000:02:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.234441] pci 0000:00:1c.2: BAR 15: assigned [mem 0xcfb00000-0xcfbfffff pref]
[    0.234443] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.234454] pci 0000:02:00.0: BAR 6: assigned [mem 0xcfb00000-0xcfb0ffff pref]
[    0.234456] pci 0000:00:1c.2: PCI bridge to [bus 02]
[    0.234460] pci 0000:00:1c.2:   bridge window [mem 0xe0500000-0xe05fffff]
[    0.234464] pci 0000:00:1c.2:   bridge window [mem 0xcfb00000-0xcfbfffff pref]
[    0.234469] pci 0000:00:1c.3: PCI bridge to [bus 03]
[    0.234471] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.234476] pci 0000:00:1c.3:   bridge window [mem 0xe0400000-0xe04fffff]
[    0.234483] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.234485] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.234487] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.234489] pci_bus 0000:00: resource 7 [mem 0xcfa00000-0xfeafffff]
[    0.234491] pci_bus 0000:02: resource 1 [mem 0xe0500000-0xe05fffff]
[    0.234492] pci_bus 0000:02: resource 2 [mem 0xcfb00000-0xcfbfffff pref]
[    0.234494] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    0.234496] pci_bus 0000:03: resource 1 [mem 0xe0400000-0xe04fffff]
[    0.234526] NET: Registered protocol family 2
[    0.234738] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.234900] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.235080] TCP: Hash tables configured (established 65536 bind 65536)
[    0.235097] TCP: reno registered
[    0.235110] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.235142] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.235216] NET: Registered protocol family 1
[    0.235226] pci 0000:00:02.0: Boot video device
[    0.235296] pci 0000:00:14.0: can't derive routing for PCI INT A
[    0.235298] pci 0000:00:14.0: PCI INT A: no GSI - using ISA IRQ 11
[    0.235380] pci 0000:00:14.0: can't derive routing for PCI INT A
[    0.235400] PCI: CLS 64 bytes, default 64
[    0.235453] Trying to unpack rootfs image as initramfs...
[    0.754846] Freeing initrd memory: 28288K (ffff8800348b0000 - ffff880036450000)
[    0.754851] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.754854] software IO TLB [mem 0xc7068000-0xcb068000] (64MB) mapped at [ffff8800c7068000-ffff8800cb067fff]
[    0.755106] microcode: CPU0 sig=0x40651, pf=0x40, revision=0x1c
[    0.755112] microcode: CPU1 sig=0x40651, pf=0x40, revision=0x1c
[    0.755117] microcode: CPU2 sig=0x40651, pf=0x40, revision=0x1c
[    0.755125] microcode: CPU3 sig=0x40651, pf=0x40, revision=0x1c
[    0.755174] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.755176] Scanning for low memory corruption every 60 seconds
[    0.755418] Initialise system trusted keyring
[    0.755462] audit: initializing netlink socket (disabled)
[    0.755475] type=2000 audit(1433407607.744:1): initialized
[    0.786094] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.787115] zbud: loaded
[    0.787256] VFS: Disk quotas dquot_6.5.2
[    0.787292] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.787672] fuse init (API version 7.22)
[    0.787735] msgmni has been set to 15780
[    0.787784] Key type big_key registered
[    0.788104] Key type asymmetric registered
[    0.788106] Asymmetric key parser 'x509' registered
[    0.788135] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.788167] io scheduler noop registered
[    0.788169] io scheduler deadline registered (default)
[    0.788191] io scheduler cfq registered
[    0.788576] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.788588] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.788621] vesafb: mode is 1920x1080x32, linelength=7680, pages=0
[    0.788622] vesafb: scrolling: redraw
[    0.788624] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.789452] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90004e80000, using 8128k, total 8128k
[    0.993904] Console: switching to colour frame buffer device 240x67
[    1.197555] fb0: VESA VGA frame buffer device
[    1.197571] intel_idle: MWAIT substates: 0x11142120
[    1.197572] intel_idle: v0.4 model 0x45
[    1.197573] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.197703] ipmi message handler version 39.2
[    1.204643] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.204698] ACPI: AC Adapter [ADP1] (on-line)
[    1.204802] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.204824] ACPI: Lid Switch [LID0]
[    1.204853] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.204857] ACPI: Sleep Button [SLPB]
[    1.204885] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.204888] ACPI: Power Button [PWRF]
[    1.205598] thermal LNXTHERM:00: registered as thermal_zone0
[    1.205600] ACPI: Thermal Zone [TZS0] (38 C)
[    1.205766] thermal LNXTHERM:01: registered as thermal_zone1
[    1.205767] ACPI: Thermal Zone [TZS1] (32 C)
[    1.205790] GHES: HEST is not enabled!
[    1.205855] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.206521] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.206529] ACPI: Battery Slot [BAT0] (battery present)
[    1.207050] Linux agpgart interface v0.103
[    1.208091] brd: module loaded
[    1.208631] loop: module loaded
[    1.208930] libphy: Fixed MDIO Bus: probed
[    1.209003] tun: Universal TUN/TAP device driver, 1.6
[    1.209004] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.209043] PPP generic driver version 2.4.2
[    1.209075] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.209079] ehci-pci: EHCI PCI platform driver
[    1.209087] ehci-platform: EHCI generic platform driver
[    1.209094] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.209095] ohci-pci: OHCI PCI platform driver
[    1.209101] ohci-platform: OHCI generic platform driver
[    1.209107] uhci_hcd: USB Universal Host Controller Interface driver
[    1.209184] xhci_hcd 0000:00:14.0: can't derive routing for PCI INT A
[    1.209186] xhci_hcd 0000:00:14.0: PCI INT A: no GSI - using ISA IRQ 11
[    1.209215] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.209220] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    1.209297] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.209314] xhci_hcd 0000:00:14.0: irq 56 for MSI/MSI-X
[    1.209372] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.209374] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.209376] usb usb1: Product: xHCI Host Controller
[    1.209377] usb usb1: Manufacturer: Linux 3.13.0-37-generic xhci_hcd
[    1.209379] usb usb1: SerialNumber: 0000:00:14.0
[    1.209462] hub 1-0:1.0: USB hub found
[    1.209472] hub 1-0:1.0: 9 ports detected
[    1.211650] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.211653] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    1.211684] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    1.211686] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.211688] usb usb2: Product: xHCI Host Controller
[    1.211689] usb usb2: Manufacturer: Linux 3.13.0-37-generic xhci_hcd
[    1.211690] usb usb2: SerialNumber: 0000:00:14.0
[    1.211763] hub 2-0:1.0: USB hub found
[    1.211771] hub 2-0:1.0: 4 ports detected
[    1.216653] i8042: PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.219502] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.219508] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.219633] mousedev: PS/2 mouse device common for all mice
[    1.219810] rtc_cmos 00:04: RTC can wake from S4
[    1.219943] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.219970] rtc_cmos 00:04: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.220025] device-mapper: uevent: version 1.0.3
[    1.220084] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.220092] ledtrig-cpu: registered to indicate activity on CPUs
[    1.220181] TCP: cubic registered
[    1.220266] NET: Registered protocol family 10
[    1.220434] NET: Registered protocol family 17
[    1.220444] Key type dns_resolver registered
[    1.220729] Loading compiled-in X.509 certificates
[    1.221658] Loaded X.509 cert 'Magrathea: Glacier signing key: 2cb1133b35f95a9e24deabeeb12ba449bcbabbc9'
[    1.221667] registered taskstats version 1
[    1.223677] Key type trusted registered
[    1.225316] Key type encrypted registered
[    1.226843] AppArmor: AppArmor sha1 policy hashing enabled
[    1.226847] IMA: No TPM chip found, activating TPM-bypass!
[    1.227157] regulator-dummy: disabling
[    1.227202]   Magic number: 3:382:775
[    1.227207] misc psaux: hash matches
[    1.227217] misc fuse: hash matches
[    1.227288] rtc_cmos 00:04: setting system clock to 2015-06-04 08:46:49 UTC (1433407609)
[    1.227967] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.227968] EDD information not available.
[    1.228003] PM: Hibernation image not present or could not be loaded.
[    1.228711] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    1.228712] Write protecting the kernel read-only data: 12288k
[    1.230265] Freeing unused kernel memory: 804K (ffff880001737000 - ffff880001800000)
[    1.231435] Freeing unused kernel memory: 692K (ffff880001b53000 - ffff880001c00000)
[    1.240609] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.243498] systemd-udevd[123]: starting version 204
[    1.259014] wmi: Mapper loaded
[    1.263360] [drm] Initialized drm 1.1.0 20060810
[    1.263948] ahci 0000:00:1f.2: version 3.0
[    1.263972] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.263982] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.264080] ahci 0000:00:1f.2: irq 57 for MSI/MSI-X
[    1.269012] r8169 0000:03:00.0: irq 58 for MSI/MSI-X
[    1.269157] r8169 0000:03:00.0 eth0: RTL8168g/8111g at 0xffffc90004ca0000, 54:ee:75:46:e3:18, XID 10900800 IRQ 58
[    1.269159] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.276645] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x1 impl SATA mode
[    1.276649] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo only pio slum part deso sadm sds apst 
[    1.277503] scsi0 : ahci
[    1.277590] scsi1 : ahci
[    1.277664] scsi2 : ahci
[    1.280490] scsi3 : ahci
[    1.280552] ata1: SATA max UDMA/133 abar m2048@0xe061c000 port 0xe061c100 irq 57
[    1.280555] ata2: DUMMY
[    1.280557] ata3: DUMMY
[    1.280558] ata4: DUMMY
[    1.283638] [drm] Memory usable by graphics device = 2048M
[    1.283642] checking generic (d0000000 7f0000) vs hw (d0000000 10000000)
[    1.283644] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[    1.283658] Console: switching to colour dummy device 80x25
[    1.328794] i915 0000:00:02.0: irq 59 for MSI/MSI-X
[    1.328807] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.328808] [drm] Driver supports precise vblank timestamp query.
[    1.328876] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.396251] fbcon: inteldrmfb (fb0) is primary device
[    1.524885] usb 1-4: new high-speed USB device number 2 using xhci_hcd
[    1.585602] usb 1-4: New USB device found, idVendor=5986, idProduct=0652
[    1.585604] usb 1-4: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    1.585605] usb 1-4: Product: Lenovo EasyCamera
[    1.585606] usb 1-4: Manufacturer: Generic
[    1.585607] usb 1-4: SerialNumber: 200901010001
[    1.596879] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.597161] ata1.00: supports DRM functions and may not be fully accessible
[    1.597249] ata1.00: ATA-9: Samsung SSD 840 EVO 250GB, EXT0DB6Q, max UDMA/133
[    1.597251] ata1.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.597503] ata1.00: supports DRM functions and may not be fully accessible
[    1.597591] ata1.00: configured for UDMA/133
[    1.597822] scsi 0:0:0:0: Direct-Access     ATA      Samsung SSD 840  EXT0 PQ: 0 ANSI: 5
[    1.597952] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.597990] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.598000] sd 0:0:0:0: [sda] Write Protect is off
[    1.598002] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.598017] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.608606]  sda: sda1 sda2 sda3 sda4 sda5 sda6
[    1.609134] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.662331] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x127c00, board id: 2334, fw id: 1508589
[    1.697431] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    1.753000] tsc: Refined TSC clocksource calibration: 2593.995 MHz
[    1.753022] usb 1-5: new low-speed USB device number 3 using xhci_hcd
[    1.772642] usb 1-5: New USB device found, idVendor=045e, idProduct=0797
[    1.772644] usb 1-5: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    1.772645] usb 1-5: Product: USB Optical Mouse
[    1.772795] usb 1-5: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.775651] hidraw: raw HID events driver (C) Jiri Kosina
[    1.778336] usbcore: registered new interface driver usbhid
[    1.778337] usbhid: USB HID core driver
[    1.779608] input: USB Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/input/input6
[    1.779691] hid-generic 0003:045E:0797.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:14.0-5/input0
[    1.885104] usb 1-6: new full-speed USB device number 4 using xhci_hcd
[    1.902535] usb 1-6: New USB device found, idVendor=0cf3, idProduct=3004
[    1.902538] usb 1-6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.069228] usb 1-8: new full-speed USB device number 5 using xhci_hcd
[    2.085918] usb 1-8: No LPM exit latency info found.  Power management will be impacted.
[    2.087400] usb 1-8: New USB device found, idVendor=04f3, idProduct=0447
[    2.087402] usb 1-8: New USB device strings: Mfr=4, Product=14, SerialNumber=0
[    2.087403] usb 1-8: Product: Touchscreen
[    2.087404] usb 1-8: Manufacturer: ELAN
[    2.087563] usb 1-8: ep 0x2 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.753758] Switched to clocksource tsc
[    2.825764] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[    3.001706] Console: switching to colour frame buffer device 240x67
[    3.008403] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    3.008405] i915 0000:00:02.0: registered panic notifier
[    3.010724] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.011121] acpi device:4c: registered as cooling_device4
[    3.011173] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[    3.011227] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.098732] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    3.201692] random: init urandom read with 52 bits of entropy available
[    3.378516] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.415306] systemd-udevd[378]: starting version 204
[    3.452450] lp: driver loaded but no devices found
[    3.454696] mei_me 0000:00:16.0: irq 60 for MSI/MSI-X
[    3.465810] ppdev: user-space parallel port driver
[    3.472225] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[    3.472231] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PPPP 2 (20131115/utaddress-251)
[    3.472234] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.472236] ACPI Warning: 0x0000000000000830-0x000000000000083f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
[    3.472238] ACPI Warning: 0x0000000000000830-0x000000000000083f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
[    3.472240] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.472241] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
[    3.472242] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
[    3.472244] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \IO_D 3 (20131115/utaddress-251)
[    3.472246] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.472247] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    3.474850] cfg80211: Calling CRDA to update world regulatory domain
[    3.480005] Bluetooth: Core ver 2.17
[    3.480018] NET: Registered protocol family 31
[    3.480020] Bluetooth: HCI device and connection manager initialized
[    3.480026] Bluetooth: HCI socket layer initialized
[    3.480028] Bluetooth: L2CAP socket layer initialized
[    3.480030] Bluetooth: SCO socket layer initialized
[    3.491532] usbcore: registered new interface driver btusb
[    3.508667] HDA driver get symbol successfully from i915 module
[    3.508790] snd_hda_intel 0000:00:1b.0: irq 61 for MSI/MSI-X
[    3.510701] input: Ideapad extra buttons as /devices/platform/VPC2004:00/input/input8
[    3.512098] ath: phy0: Set BT/WLAN RX diversity capability
[    3.514030] snd_hda_intel 0000:00:03.0: irq 62 for MSI/MSI-X
[    3.525230] ath: phy0: Enable LNA combining
[    3.526350] ath: phy0: ASPM enabled: 0x42
[    3.526353] ath: EEPROM regdomain: 0x6a
[    3.526355] ath: EEPROM indicates we should expect a direct regpair map
[    3.526357] ath: Country alpha2 being used: 00
[    3.526358] ath: Regpair used: 0x6a
[    3.533884] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input11
[    3.534379] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input10
[    3.534512] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input9
[    3.539509] input: ELAN Touchscreen as /devices/pci0000:00/0000:00:14.0/usb1/1-8/1-8:1.0/input/input12
[    3.541674] Linux video capture interface: v2.00
[    3.542537] SKU: Nid=0x0 sku_cfg=0x00003817
[    3.542540] SKU: port_connectivity=0x0
[    3.542542] SKU: enable_pcbeep=0x1
[    3.542543] SKU: check_sum=0x00000000
[    3.542545] SKU: customization=0x00000000
[    3.542546] SKU: external_amp=0x2
[    3.542547] SKU: platform_type=0x1
[    3.542549] SKU: swap=0x1
[    3.542550] SKU: override=0x1
[    3.543273] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    3.543276]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.543277]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    3.543278]    mono: mono_out=0x0
[    3.543279]    inputs:
[    3.543280]      Mic=0x19
[    3.543282]      Internal Mic=0x12
[    3.543283] realtek: Enabling init ASM_ID=0x3817 CODEC_ID=10ec0233
[    3.548631] hid-multitouch 0003:04F3:0447.0002: input,hiddev0,hidraw1: USB HID v1.10 Device [ELAN Touchscreen] on usb-0000:00:14.0-8/input0
[    3.549382] usbcore: registered new interface driver ath3k
[    3.549676] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    3.550403] usb 1-6: USB disconnect, device number 4
[    3.552640] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (5986:0652)
[    3.555403] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/input/input14
[    3.555587] usbcore: registered new interface driver uvcvideo
[    3.555588] USB Video Class driver (1.1.1)
[    3.556267] random: nonblocking pool is initialized
[    3.557746] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    3.560323] ieee80211 phy0: Atheros AR9565 Rev:1 mem=0xffffc90004f00000, irq=18
[    3.560988] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input16
[    3.561119] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input15
[    3.639536] device-mapper: multipath: version 1.6.0 loaded
[    3.639892] EXT4-fs (sda6): mounting ext2 file system using the ext4 subsystem
[    3.655948] EXT4-fs (sda6): mounted filesystem without journal. Opts: (null)
[    3.698341] asus_wmi: Asus Management GUID not found
[    3.789185] intel_rapl: domain uncore energy ctr 26451:26451 not working, skip
[    3.822220] usb 1-6: new full-speed USB device number 6 using xhci_hcd
[    3.822696] cfg80211: World regulatory domain updated:
[    3.822698] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    3.822701] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.822703] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.822704] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    3.822706] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.822708] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    3.845322] init: failsafe main process (667) killed by TERM signal
[    3.938895] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.938899] Bluetooth: BNEP filters: protocol multicast
[    3.938907] Bluetooth: BNEP socket layer initialized
[    3.950705] Bluetooth: RFCOMM TTY layer initialized
[    3.950717] Bluetooth: RFCOMM socket layer initialized
[    3.950722] Bluetooth: RFCOMM ver 1.11
[    4.188182] init: samba-ad-dc main process (814) terminated with status 1
[    4.202651] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.202959] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.216494] r8169 0000:03:00.0 eth0: link down
[    4.216549] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.217209] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.557837] init: plymouth-upstart-bridge main process ended, respawning
[    4.562355] init: plymouth-upstart-bridge main process (1326) terminated with status 1
[    4.562363] init: plymouth-upstart-bridge main process ended, respawning
[    4.604492] init: plymouth-stop pre-start process (1360) terminated with status 1
[    5.946846] wlan0: authenticate with 14:cc:20:c8:d8:24
[    5.964486] wlan0: send auth to 14:cc:20:c8:d8:24 (try 1/3)
[    5.966917] wlan0: authenticated
[    5.967539] wlan0: associate with 14:cc:20:c8:d8:24 (try 1/3)
[    5.971953] wlan0: RX AssocResp from 14:cc:20:c8:d8:24 (capab=0x431 status=0 aid=1)
[    5.971996] wlan0: associated
[    5.972004] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    5.989588] wlan0: deauthenticating from 14:cc:20:c8:d8:24 by local choice (reason=2)
[    5.997484] cfg80211: Calling CRDA to update world regulatory domain
[    5.997512] wlan0: authenticate with 14:cc:20:c8:d8:24
[    6.012239] wlan0: send auth to 14:cc:20:c8:d8:24 (try 1/3)
[    6.012355] cfg80211: World regulatory domain updated:
[    6.012357] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    6.012359] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.012361] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.012363] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.012364] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.012365] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.014643] wlan0: authenticated
[    6.015574] wlan0: associate with 14:cc:20:c8:d8:24 (try 1/3)
[    6.022275] wlan0: RX AssocResp from 14:cc:20:c8:d8:24 (capab=0x431 status=0 aid=1)
[    6.022316] wlan0: associated
[    8.825384] xhci_hcd 0000:00:14.0: Timeout while waiting for address device command
[    8.825419] ------------[ cut here ]------------
[    8.825439] WARNING: CPU: 0 PID: 0 at /build/buildd/linux-3.13.0/drivers/usb/host/xhci-ring.c:1579 handle_cmd_completion+0xe46/0xe50()
[    8.825443] Modules linked in: ctr ccm rfcomm bnep binfmt_misc intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm dm_multipath scsi_dh crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd uvcvideo videobuf2_vmalloc joydev videobuf2_memops videobuf2_core serio_raw snd_hda_codec_realtek videodev hid_multitouch snd_hda_codec_hdmi arc4 ath9k ideapad_laptop ath9k_common snd_hda_intel sparse_keymap ath9k_hw snd_hda_codec ath snd_hwdep ath3k snd_seq_midi btusb snd_seq_midi_event mac_hid mac80211 snd_pcm bluetooth cfg80211 lpc_ich snd_rawmidi parport_pc snd_seq snd_page_alloc snd_seq_device snd_timer ppdev mei_me snd mei soundcore lp parport dm_mirror dm_region_hash dm_log hid_generic usbhid hid i915 psmouse i2c_algo_bit drm_kms_helper ahci r8169 drm libahci mii wmi video
[    8.825551] CPU: 0 PID: 0 Comm: swapper/0 Not tainted 3.13.0-37-generic #64-Ubuntu
[    8.825554] Hardware name: LENOVO 20404/Lenovo Flex 2-14, BIOS A0CN36WW 04/30/2015
[    8.825557]  0000000000000009 ffff88022f203da8 ffffffff8171ed09 0000000000000000
[    8.825566]  ffff88022f203de0 ffffffff8106773d ffff88021e1f1740 ffff88021e1f11b0
[    8.825572]  0000000000000005 000000021e1f11b0 ffff880223636000 ffff88022f203df0
[    8.825579] Call Trace:
[    8.825582]  <IRQ>  [<ffffffff8171ed09>] dump_stack+0x45/0x56
[    8.825599]  [<ffffffff8106773d>] warn_slowpath_common+0x7d/0xa0
[    8.825606]  [<ffffffff8106781a>] warn_slowpath_null+0x1a/0x20
[    8.825614]  [<ffffffff8157be86>] handle_cmd_completion+0xe46/0xe50
[    8.825622]  [<ffffffff8157d893>] xhci_irq+0x333/0xa60
[    8.825629]  [<ffffffff8157dfd1>] xhci_msi_irq+0x11/0x20
[    8.825637]  [<ffffffff810bf8ae>] handle_irq_event_percpu+0x3e/0x1d0
[    8.825643]  [<ffffffff810bfa7d>] handle_irq_event+0x3d/0x60
[    8.825650]  [<ffffffff810c2507>] handle_edge_irq+0x77/0x130
[    8.825660]  [<ffffffff81015cde>] handle_irq+0x1e/0x30
[    8.825669]  [<ffffffff81731b4d>] do_IRQ+0x4d/0xc0
[    8.825678]  [<ffffffff8172722d>] common_interrupt+0x6d/0x6d
[    8.825680]  <EOI>  [<ffffffff815d1862>] ? cpuidle_enter_state+0x52/0xc0
[    8.825697]  [<ffffffff815d1989>] cpuidle_idle_call+0xb9/0x1f0
[    8.825706]  [<ffffffff8101d1de>] arch_cpu_idle+0xe/0x30
[    8.825712]  [<ffffffff810bed85>] cpu_startup_entry+0xc5/0x290
[    8.825719]  [<ffffffff8170d217>] rest_init+0x77/0x80
[    8.825727]  [<ffffffff81d36f70>] start_kernel+0x438/0x443
[    8.825732]  [<ffffffff81d36941>] ? repair_env_string+0x5c/0x5c
[    8.825737]  [<ffffffff81d36120>] ? early_idt_handlers+0x120/0x120
[    8.825743]  [<ffffffff81d365ee>] x86_64_start_reservations+0x2a/0x2c
[    8.825748]  [<ffffffff81d36733>] x86_64_start_kernel+0x143/0x152
[    8.825752] ---[ end trace a4389cadb5bd3872 ]---
[    9.029614] usb 1-6: Device not responding to set address.
[    9.233643] usb 1-6: device not accepting address 6, error -71
[    9.345746] usb 1-6: new full-speed USB device number 7 using xhci_hcd
[    9.363252] usb 1-6: New USB device found, idVendor=0cf3, idProduct=3004
[    9.363262] usb 1-6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    9.465693] xhci_hcd 0000:00:14.0: xHCI host not responding to stop endpoint command.
[    9.465699] xhci_hcd 0000:00:14.0: Assuming host is dying, halting host.
[    9.465725] Bluetooth: hci0 urb ffff88021e253e40 failed to resubmit (22)
[    9.465731] Bluetooth: hci0 urb ffff88021e253a80 failed to resubmit (22)
[    9.465735] Bluetooth: hci0 urb ffff88021e253cc0 failed to resubmit (22)
[    9.465741] xhci_hcd 0000:00:14.0: HC died; cleaning up
[    9.465760] usb 1-4: USB disconnect, device number 2
[    9.475791] Bluetooth: hci0 sending frame failed
[    9.502110] usb 1-5: USB disconnect, device number 3
[    9.538273] usb 1-6: USB disconnect, device number 7
[    9.539409] usb 1-8: USB disconnect, device number 5
```

---

