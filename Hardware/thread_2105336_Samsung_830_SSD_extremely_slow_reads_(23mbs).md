---
title: "Samsung 830 SSD extremely slow reads (23mb/s)"
date: 2013-01-15
forum: Hardware
---

### Post by EuleLL on 2013-01-15
Hi everyone,

i have been running 12.04 server for quite some time now with a Samsung 830 256GB SSD. For some reason read speed have become extremely slow - however only read speeds, writes are still in the above 200mb/s ball park.

my fstab line for the ssd is as follows:

```
UUID=864d7002-477e-473f-b5ba-534fad0a0caa /               ext4    defaults,noatime,nodiratime,discard,errors=remount-ro 0       1

```

hdparm -tT results in the following output:

```
sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1986 MB in  2.00 seconds = 992.73 MB/sec
 Timing buffered disk reads:  78 MB in  3.03 seconds =  25.77 MB/sec
```

hdparm and hdparm -i outputs:

```
/dev/sda:
 multcount     = 16 (on)
 IO_support    =  1 (32-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 31130/255/63, sectors = 500118192, start = 0

/dev/sda:

 Model=SAMSUNG SSD 830 Series, FwRev=CXM03B1Q, SerialNo=S0Z4NEAC947171
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=500118192
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode

```

the current scheduler is noop - but ive lso tried deadline and the other one - how that did not bring any improvements...

i also checked reads and writes with dd command (same results) and checked via iotop if there might be any background applications reading from the disk - but i could not find any abnormalities

I've had great write and read speed at first but that changed and I dont know why - any suggestions on how to fix this?

I am really thankful for your help - ive already tried everything I could think off...

cheers

---

### Post by tgalati4 on 2013-01-15
Have you performed any kernel updates recently?  Does dmesg look OK?  Any disk-related messages?  Normally write speeds slow down as the wear-leveler spends more time looking for unwritten blocks, but slow read speeds is strange.  Check the cables, reseat them or change them and rerun your tests.

---

### Post by EuleLL on 2013-01-16
I am running 3.2.0-35-generic kernel. I cant remember when I updated it - must have been some time before xmas.

I checked dmesg but I cant find any errors - however i am not really an expert :-)

here is the dmesg output - maybe anyone spot something unusual...

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-35-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 (Ubuntu 3.2.0-35.55-generic 3.2.34)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-35-generic root=UUID=864d7002-477e-473f-b5ba-534fad0a0caa ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009794b000 (usable)
[    0.000000]  BIOS-e820: 000000009794b000 - 0000000097995000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000097995000 - 000000009799d000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009799d000 - 00000000979a0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000979a0000 - 0000000097a71000 (reserved)
[    0.000000]  BIOS-e820: 0000000097a71000 - 0000000097a72000 (usable)
[    0.000000]  BIOS-e820: 0000000097a72000 - 0000000097a82000 (reserved)
[    0.000000]  BIOS-e820: 0000000097a82000 - 0000000097a8a000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000097a8a000 - 0000000097ab4000 (reserved)
[    0.000000]  BIOS-e820: 0000000097ab4000 - 0000000097af7000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000097af7000 - 0000000097d71000 (usable)
[    0.000000]  BIOS-e820: 0000000097d71000 - 0000000097ef7000 (reserved)
[    0.000000]  BIOS-e820: 0000000097ef7000 - 0000000097f00000 (usable)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec11000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed61000 - 00000000fed71000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed80000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fef00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100001000 - 000000024f000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.7 present.
[    0.000000] DMI: MotherBoard By ZOTAC MotherBoard Fusion350-B-B/E/J/U/Fusion350-B-B/E/J/U, BIOS 4.6.4 11/14/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x24f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF write-through
[    0.000000]   C0000-CEFFF write-protect
[    0.000000]   CF000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 097F00000 mask FFFF00000 uncachable
[    0.000000]   2 base 098000000 mask FF8000000 uncachable
[    0.000000]   3 base 0A0000000 mask FE0000000 uncachable
[    0.000000]   4 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000024f000000 aka 9456M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 2431MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2432MB, range: 128MB, type UC
[    0.000000] reg 3, base: 2560MB, range: 512MB, type UC
[    0.000000] reg 4, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 2431M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 2M 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 256MB, type WB
[    0.000000] reg 2, base: 2304MB, range: 128MB, type WB
[    0.000000] reg 3, base: 2431MB, range: 1MB, type UC
[    0.000000] e820 update range: 0000000097f00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x97f00 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fcde0] fcde0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-0000000097f00000
[    0.000000]  0000000000 - 0080000000 page 1G
[    0.000000]  0080000000 - 0097e00000 page 2M
[    0.000000]  0097e00000 - 0097f00000 page 4k
[    0.000000] kernel direct mapping tables up to 97f00000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000024f000000
[    0.000000]  0100000000 - 0240000000 page 1G
[    0.000000]  0240000000 - 024f000000 page 2M
[    0.000000] kernel direct mapping tables up to 24f000000 @ 97efe000-97f00000
[    0.000000] RAMDISK: 364d8000 - 37264000
[    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0000000097995068 00054 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 000000009799a4c8 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110623/tbfadt-560)
[    0.000000] ACPI: DSDT 0000000097995150 05371 (v02 ALASKA    A M I 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 0000000097a89f80 00040
[    0.000000] ACPI: APIC 000000009799a5c0 00062 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 000000009799a628 0003C (v01 ALASKA    A M I 01072009 MSFT 00010013)
[    0.000000] ACPI: HPET 000000009799a668 00038 (v01 ALASKA    A M I 01072009 AMI  00000004)
[    0.000000] ACPI: SSDT 000000009799a6a0 003DE (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: SSDT 000000009799aa80 0168E (v02    AMD     ALIB 00000001 MSFT 04000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000024f000000
[    0.000000] Initmem setup node 0 0000000000000000-000000024f000000
[    0.000000]   NODE_DATA [000000024effb000 - 000000024effffff]
[    0.000000]  [ffffea0000000000-ffffea00093fffff] PMD -> [ffff880246c00000-ffff88024e5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0024f000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0009794b
[    0.000000]     0: 0x00097a71 -> 0x00097a72
[    0.000000]     0: 0x00097af7 -> 0x00097d71
[    0.000000]     0: 0x00097ef7 -> 0x00097f00
[    0.000000]     0: 0x00100001 -> 0x0024f000
[    0.000000] On node 0 totalpages: 1993563
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3912 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 601103 pages, LIFO batch:31
[    0.000000]   Normal zone: 21440 pages used for memmap
[    0.000000]   Normal zone: 1350719 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000009794b000 - 0000000097995000
[    0.000000] PM: Registered nosave memory: 0000000097995000 - 000000009799d000
[    0.000000] PM: Registered nosave memory: 000000009799d000 - 00000000979a0000
[    0.000000] PM: Registered nosave memory: 00000000979a0000 - 0000000097a71000
[    0.000000] PM: Registered nosave memory: 0000000097a72000 - 0000000097a82000
[    0.000000] PM: Registered nosave memory: 0000000097a82000 - 0000000097a8a000
[    0.000000] PM: Registered nosave memory: 0000000097a8a000 - 0000000097ab4000
[    0.000000] PM: Registered nosave memory: 0000000097ab4000 - 0000000097af7000
[    0.000000] PM: Registered nosave memory: 0000000097d71000 - 0000000097ef7000
[    0.000000] PM: Registered nosave memory: 0000000097f00000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fec11000
[    0.000000] PM: Registered nosave memory: 00000000fec11000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed01000
[    0.000000] PM: Registered nosave memory: 00000000fed01000 - 00000000fed61000
[    0.000000] PM: Registered nosave memory: 00000000fed61000 - 00000000fed71000
[    0.000000] PM: Registered nosave memory: 00000000fed71000 - 00000000fed80000
[    0.000000] PM: Registered nosave memory: 00000000fed80000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000fef00000
[    0.000000] PM: Registered nosave memory: 00000000fef00000 - 0000000100000000
[    0.000000] PM: Registered nosave memory: 0000000100000000 - 0000000100001000
[    0.000000] Allocating PCI resources starting at 97f00000 (gap: 97f00000:66d00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88024ec00000 s83136 r8192 d23360 u1048576
[    0.000000] pcpu-alloc: s83136 r8192 d23360 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1955734
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-35-generic root=UUID=864d7002-477e-473f-b5ba-534fad0a0caa ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7753344k/9682944k available (6569k kernel code, 1708692k absent, 220908k reserved, 6634k data, 924k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 63963136 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1600.168 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3200.33 BogoMIPS (lpj=6400672)
[    0.004022] pid_max: default: 32768 minimum: 301
[    0.004070] Security Framework initialized
[    0.004102] AppArmor: AppArmor initialized
[    0.004109] Yama: becoming mindful.
[    0.005324] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.011624] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.014162] Mount-cache hash table entries: 256
[    0.014424] Initializing cgroup subsys cpuacct
[    0.014440] Initializing cgroup subsys memory
[    0.014459] Initializing cgroup subsys devices
[    0.014467] Initializing cgroup subsys freezer
[    0.014473] Initializing cgroup subsys blkio
[    0.014488] Initializing cgroup subsys perf_event
[    0.014550] tseg: 0097f00000
[    0.014555] CPU: Physical Processor ID: 0
[    0.014562] CPU: Processor Core ID: 0
[    0.014570] mce: CPU supports 6 MCE banks
[    0.019207] ACPI: Core revision 20110623
[    0.026043] ftrace: allocating 27030 entries in 107 pages
[    0.028547] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.068698] CPU0: AMD E-350 Processor stepping 00
[    0.072003] Performance Events: AMD PMU driver.
[    0.072003] ... version:                0
[    0.072003] ... bit width:              48
[    0.072003] ... generic registers:      4
[    0.072003] ... value mask:             0000ffffffffffff
[    0.072003] ... max period:             00007fffffffffff
[    0.072003] ... fixed-purpose events:   0
[    0.072003] ... event mask:             000000000000000f
[    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.072003] Booting Node   0, Processors  #1 Ok.
[    0.072003] smpboot cpu 1: start_ip = 98000
[    0.160046] NMI watchdog enabled, takes one hw-pmu counter.
[    0.160095] Brought up 2 CPUs
[    0.160102] Total of 2 processors activated (6400.55 BogoMIPS).
[    0.160703] devtmpfs: initialized
[    0.164543] EVM: security.selinux
[    0.164551] EVM: security.SMACK64
[    0.164556] EVM: security.capability
[    0.164601] PM: Registering ACPI NVS region at 9794b000 (303104 bytes)
[    0.164601] PM: Registering ACPI NVS region at 9799d000 (12288 bytes)
[    0.164601] PM: Registering ACPI NVS region at 97a82000 (32768 bytes)
[    0.164601] PM: Registering ACPI NVS region at 97ab4000 (274432 bytes)
[    0.165814] print_constraints: dummy: 
[    0.165896] RTC time:  9:40:58, date: 01/16/13
[    0.165970] NET: Registered protocol family 16
[    0.166118] Trying to unpack rootfs image as initramfs...
[    0.166397] Extended Config Space enabled on 0 nodes
[    0.166440] ACPI: bus type pci registered
[    0.166558] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.166571] PCI: not using MMCONFIG
[    0.166576] PCI: Using configuration type 1 for base access
[    0.166582] PCI: Using configuration type 1 for extended access
[    0.169336] bio: create slab <bio-0> at 0
[    0.169525] ACPI: Added _OSI(Module Device)
[    0.169533] ACPI: Added _OSI(Processor Device)
[    0.169540] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.169546] ACPI: Added _OSI(Processor Aggregator Device)
[    0.171115] ACPI: EC: Look up EC in DSDT
[    0.172910] ACPI: Executed 2 blocks of module-level executable AML code
[    0.204858] ACPI: Interpreter enabled
[    0.204878] ACPI: (supports S0 S3 S4 S5)
[    0.204930] ACPI: Using IOAPIC for interrupt routing
[    0.205019] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.205105] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.299799] ACPI: No dock devices found.
[    0.299815] HEST: Table not found.
[    0.299825] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.300227] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.300724] pci_root PNP0A08:00: host bridge window [io  0x0000-0x03af]
[    0.300734] pci_root PNP0A08:00: host bridge window [io  0x03e0-0x0cf7]
[    0.300742] pci_root PNP0A08:00: host bridge window [io  0x03b0-0x03df]
[    0.300750] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.300758] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.300767] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000dffff]
[    0.300776] pci_root PNP0A08:00: host bridge window [mem 0xb0000000-0xffffffff]
[    0.300803] pci 0000:00:00.0: [1022:1510] type 0 class 0x000600
[    0.300866] pci 0000:00:01.0: [1002:9802] type 0 class 0x000300
[    0.300882] pci 0000:00:01.0: reg 10: [mem 0xb0000000-0xbfffffff pref]
[    0.300893] pci 0000:00:01.0: reg 14: [io  0xf000-0xf0ff]
[    0.300903] pci 0000:00:01.0: reg 18: [mem 0xfeb00000-0xfeb3ffff]
[    0.300967] pci 0000:00:01.0: supports D1 D2
[    0.300993] pci 0000:00:01.1: [1002:1314] type 0 class 0x000403
[    0.301007] pci 0000:00:01.1: reg 10: [mem 0xfeb44000-0xfeb47fff]
[    0.301082] pci 0000:00:01.1: supports D1 D2
[    0.301116] pci 0000:00:04.0: [1022:1512] type 1 class 0x000604
[    0.301196] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.301203] pci 0000:00:04.0: PME# disabled
[    0.301259] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    0.301286] pci 0000:00:11.0: reg 10: [io  0xf190-0xf197]
[    0.301300] pci 0000:00:11.0: reg 14: [io  0xf180-0xf183]
[    0.301314] pci 0000:00:11.0: reg 18: [io  0xf170-0xf177]
[    0.301328] pci 0000:00:11.0: reg 1c: [io  0xf160-0xf163]
[    0.301343] pci 0000:00:11.0: reg 20: [io  0xf150-0xf15f]
[    0.301357] pci 0000:00:11.0: reg 24: [mem 0xfeb4f000-0xfeb4f3ff]
[    0.301439] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.301459] pci 0000:00:12.0: reg 10: [mem 0xfeb4e000-0xfeb4efff]
[    0.301558] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.301584] pci 0000:00:12.2: reg 10: [mem 0xfeb4d000-0xfeb4d0ff]
[    0.301695] pci 0000:00:12.2: supports D1 D2
[    0.301699] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.301706] pci 0000:00:12.2: PME# disabled
[    0.301737] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.301756] pci 0000:00:13.0: reg 10: [mem 0xfeb4c000-0xfeb4cfff]
[    0.301855] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.301882] pci 0000:00:13.2: reg 10: [mem 0xfeb4b000-0xfeb4b0ff]
[    0.301993] pci 0000:00:13.2: supports D1 D2
[    0.301996] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.302003] pci 0000:00:13.2: PME# disabled
[    0.302034] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.302137] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.302156] pci 0000:00:14.1: reg 10: [io  0xf140-0xf147]
[    0.302170] pci 0000:00:14.1: reg 14: [io  0xf130-0xf133]
[    0.302184] pci 0000:00:14.1: reg 18: [io  0xf120-0xf127]
[    0.302198] pci 0000:00:14.1: reg 1c: [io  0xf110-0xf113]
[    0.302212] pci 0000:00:14.1: reg 20: [io  0xf100-0xf10f]
[    0.302267] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.302297] pci 0000:00:14.2: reg 10: [mem 0xfeb40000-0xfeb43fff 64bit]
[    0.302386] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.302393] pci 0000:00:14.2: PME# disabled
[    0.302417] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.302522] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.302581] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.302601] pci 0000:00:14.5: reg 10: [mem 0xfeb4a000-0xfeb4afff]
[    0.302701] pci 0000:00:15.0: [1002:43a0] type 1 class 0x000604
[    0.302810] pci 0000:00:15.0: supports D1 D2
[    0.302849] pci 0000:00:15.2: [1002:43a2] type 1 class 0x000604
[    0.302956] pci 0000:00:15.2: supports D1 D2
[    0.302994] pci 0000:00:15.3: [1002:43a3] type 1 class 0x000604
[    0.303100] pci 0000:00:15.3: supports D1 D2
[    0.303139] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
[    0.303158] pci 0000:00:16.0: reg 10: [mem 0xfeb49000-0xfeb49fff]
[    0.303257] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
[    0.303283] pci 0000:00:16.2: reg 10: [mem 0xfeb48000-0xfeb480ff]
[    0.303394] pci 0000:00:16.2: supports D1 D2
[    0.303398] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.303405] pci 0000:00:16.2: PME# disabled
[    0.303441] pci 0000:00:18.0: [1022:1700] type 0 class 0x000600
[    0.303492] pci 0000:00:18.1: [1022:1701] type 0 class 0x000600
[    0.303538] pci 0000:00:18.2: [1022:1702] type 0 class 0x000600
[    0.303585] pci 0000:00:18.3: [1022:1703] type 0 class 0x000600
[    0.303646] pci 0000:00:18.4: [1022:1704] type 0 class 0x000600
[    0.303691] pci 0000:00:18.5: [1022:1718] type 0 class 0x000600
[    0.303737] pci 0000:00:18.6: [1022:1716] type 0 class 0x000600
[    0.303783] pci 0000:00:18.7: [1022:1719] type 0 class 0x000600
[    0.303925] pci 0000:00:04.0: PCI bridge to [bus 01-01]
[    0.304038] pci 0000:00:14.4: PCI bridge to [bus 02-02] (subtractive decode)
[    0.304056] pci 0000:00:14.4:   bridge window [io  0x0000-0x03af] (subtractive decode)
[    0.304061] pci 0000:00:14.4:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
[    0.304065] pci 0000:00:14.4:   bridge window [io  0x03b0-0x03df] (subtractive decode)
[    0.304069] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.304074] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.304079] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.304083] pci 0000:00:14.4:   bridge window [mem 0xb0000000-0xffffffff] (subtractive decode)
[    0.304155] pci 0000:00:15.0: PCI bridge to [bus 03-05]
[    0.304167] pci 0000:00:15.0:   bridge window [io  0xe000-0xefff]
[    0.304173] pci 0000:00:15.0:   bridge window [mem 0xfe000000-0xfe9fffff]
[    0.304183] pci 0000:00:15.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.304279] pci 0000:06:00.0: [1106:3432] type 0 class 0x000c03
[    0.304301] pci 0000:06:00.0: reg 10: [mem 0xfea00000-0xfea00fff]
[    0.304439] pci 0000:06:00.0: supports D1 D2
[    0.304443] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.304450] pci 0000:06:00.0: PME# disabled
[    0.312082] pci 0000:00:15.2: PCI bridge to [bus 06-06]
[    0.312111] pci 0000:00:15.2:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.312227] pci 0000:07:00.0: [10ec:8168] type 0 class 0x000200
[    0.312256] pci 0000:07:00.0: reg 10: [io  0xd000-0xd0ff]
[    0.312296] pci 0000:07:00.0: reg 18: [mem 0xd0004000-0xd0004fff 64bit pref]
[    0.312322] pci 0000:07:00.0: reg 20: [mem 0xd0000000-0xd0003fff 64bit pref]
[    0.312432] pci 0000:07:00.0: supports D1 D2
[    0.312436] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.312445] pci 0000:07:00.0: PME# disabled
[    0.320087] pci 0000:00:15.3: PCI bridge to [bus 07-07]
[    0.320113] pci 0000:00:15.3:   bridge window [io  0xd000-0xdfff]
[    0.320127] pci 0000:00:15.3:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.320177] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.320494] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE20._PRT]
[    0.320557] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE22._PRT]
[    0.320613] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE23._PRT]
[    0.320674] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR14._PRT]
[    0.320732]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.320743]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.320752] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.331535] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *7 10 11 14 15)
[    0.331742] ACPI: PCI Interrupt Link [LNKB] (IRQs *4 7 10 11 14 15)
[    0.331908] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 *11 14 15)
[    0.332050] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 14 15)
[    0.332156] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 14 15) *0
[    0.332242] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 14 15) *0
[    0.332328] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 11 14 15) *0
[    0.332452] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 14 15) *0
[    0.332691] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    0.332726] vgaarb: loaded
[    0.332731] vgaarb: bridge control possible 0000:00:01.0
[    0.332955] i2c-core: driver [aat2870] using legacy suspend method
[    0.332963] i2c-core: driver [aat2870] using legacy resume method
[    0.333092] SCSI subsystem initialized
[    0.333215] libata version 3.00 loaded.
[    0.333320] usbcore: registered new interface driver usbfs
[    0.333347] usbcore: registered new interface driver hub
[    0.333406] usbcore: registered new device driver usb
[    0.333590] PCI: Using ACPI for IRQ routing
[    0.344689] PCI: pci_cache_line_size set to 64 bytes
[    0.344853] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    0.344858] reserve RAM buffer: 000000009794b000 - 0000000097ffffff 
[    0.344865] reserve RAM buffer: 0000000097a72000 - 0000000097ffffff 
[    0.344870] reserve RAM buffer: 0000000097d71000 - 0000000097ffffff 
[    0.344874] reserve RAM buffer: 0000000097f00000 - 0000000097ffffff 
[    0.344878] reserve RAM buffer: 000000024f000000 - 000000024fffffff 
[    0.345076] NetLabel: Initializing
[    0.345085] NetLabel:  domain hash size = 128
[    0.345090] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.345114] NetLabel:  unlabeled traffic allowed by default
[    0.345218] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.345232] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.347272] Switching to clocksource hpet
[    0.357259] AppArmor: AppArmor Filesystem Enabled
[    0.357334] pnp: PnP ACPI init
[    0.357374] ACPI: bus type pnp registered
[    0.357713] pnp 00:00: [bus 00-ff]
[    0.357718] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.357722] pnp 00:00: [io  0x0000-0x03af window]
[    0.357727] pnp 00:00: [io  0x03e0-0x0cf7 window]
[    0.357731] pnp 00:00: [io  0x03b0-0x03df window]
[    0.357736] pnp 00:00: [io  0x0d00-0xffff window]
[    0.357740] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.357745] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.357749] pnp 00:00: [mem 0xb0000000-0xffffffff window]
[    0.357753] pnp 00:00: [mem 0x00000000 window]
[    0.357851] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.357918] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.358023] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.358036] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.358795] pnp 00:02: [io  0x040b]
[    0.358799] pnp 00:02: [io  0x04d6]
[    0.358802] pnp 00:02: [io  0x0c00-0x0c01]
[    0.358806] pnp 00:02: [io  0x0c14]
[    0.358809] pnp 00:02: [io  0x0c50-0x0c51]
[    0.358812] pnp 00:02: [io  0x0c52]
[    0.358815] pnp 00:02: [io  0x0c6c]
[    0.358818] pnp 00:02: [io  0x0c6f]
[    0.358821] pnp 00:02: [io  0x0cd0-0x0cd1]
[    0.358824] pnp 00:02: [io  0x0cd2-0x0cd3]
[    0.358828] pnp 00:02: [io  0x0cd4-0x0cd5]
[    0.358831] pnp 00:02: [io  0x0cd6-0x0cd7]
[    0.358834] pnp 00:02: [io  0x0cd8-0x0cdf]
[    0.358841] pnp 00:02: [io  0x0800-0x089f]
[    0.358845] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
[    0.358849] pnp 00:02: [io  0x0000-0x000f]
[    0.358852] pnp 00:02: [io  0x0b20-0x0b3f]
[    0.358856] pnp 00:02: [io  0x0900-0x090f]
[    0.358859] pnp 00:02: [io  0x0910-0x091f]
[    0.358862] pnp 00:02: [io  0xfe00-0xfefe]
[    0.358866] pnp 00:02: [io  0x0060-0x005f disabled]
[    0.358869] pnp 00:02: [io  0x0064-0x0063 disabled]
[    0.358873] pnp 00:02: [mem 0xfec00000-0xfec00fff]
[    0.358876] pnp 00:02: [mem 0xfee00000-0xfee00fff]
[    0.358880] pnp 00:02: [mem 0xfed80000-0xfed8ffff]
[    0.358884] pnp 00:02: [mem 0xfed61000-0xfed70fff]
[    0.358887] pnp 00:02: [mem 0xfec10000-0xfec10fff]
[    0.358891] pnp 00:02: [mem 0xfed00000-0xfed00fff]
[    0.358894] pnp 00:02: [mem 0xffc00000-0xffffffff]
[    0.359022] system 00:02: [io  0x040b] has been reserved
[    0.359032] system 00:02: [io  0x04d6] has been reserved
[    0.359039] system 00:02: [io  0x0c00-0x0c01] has been reserved
[    0.359047] system 00:02: [io  0x0c14] has been reserved
[    0.359055] system 00:02: [io  0x0c50-0x0c51] has been reserved
[    0.359063] system 00:02: [io  0x0c52] has been reserved
[    0.359070] system 00:02: [io  0x0c6c] has been reserved
[    0.359077] system 00:02: [io  0x0c6f] has been reserved
[    0.359085] system 00:02: [io  0x0cd0-0x0cd1] has been reserved
[    0.359092] system 00:02: [io  0x0cd2-0x0cd3] has been reserved
[    0.359100] system 00:02: [io  0x0cd4-0x0cd5] has been reserved
[    0.359108] system 00:02: [io  0x0cd6-0x0cd7] has been reserved
[    0.359116] system 00:02: [io  0x0cd8-0x0cdf] has been reserved
[    0.359123] system 00:02: [io  0x0800-0x089f] has been reserved
[    0.359131] system 00:02: [io  0x0b20-0x0b3f] has been reserved
[    0.359139] system 00:02: [io  0x0900-0x090f] has been reserved
[    0.359147] system 00:02: [io  0x0910-0x091f] has been reserved
[    0.359155] system 00:02: [io  0xfe00-0xfefe] has been reserved
[    0.359165] system 00:02: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.359174] system 00:02: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.359182] system 00:02: [mem 0xfed80000-0xfed8ffff] has been reserved
[    0.359191] system 00:02: [mem 0xfed61000-0xfed70fff] has been reserved
[    0.359200] system 00:02: [mem 0xfec10000-0xfec10fff] has been reserved
[    0.359209] system 00:02: [mem 0xfed00000-0xfed00fff] has been reserved
[    0.359217] system 00:02: [mem 0xffc00000-0xffffffff] has been reserved
[    0.359227] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.359540] pnp 00:03: [dma 4]
[    0.359544] pnp 00:03: [io  0x0000-0x000f]
[    0.359547] pnp 00:03: [io  0x0081-0x0083]
[    0.359551] pnp 00:03: [io  0x0087]
[    0.359554] pnp 00:03: [io  0x0089-0x008b]
[    0.359557] pnp 00:03: [io  0x008f]
[    0.359560] pnp 00:03: [io  0x00c0-0x00df]
[    0.359612] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.359632] pnp 00:04: [io  0x0070-0x0071]
[    0.359652] pnp 00:04: [irq 8]
[    0.359699] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.359716] pnp 00:05: [io  0x0061]
[    0.359774] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.359823] pnp 00:06: [io  0x0010-0x001f]
[    0.359826] pnp 00:06: [io  0x0022-0x003f]
[    0.359830] pnp 00:06: [io  0x0044-0x005f]
[    0.359833] pnp 00:06: [io  0x0072-0x007f]
[    0.359836] pnp 00:06: [io  0x0080]
[    0.359839] pnp 00:06: [io  0x0084-0x0086]
[    0.359842] pnp 00:06: [io  0x0088]
[    0.359845] pnp 00:06: [io  0x008c-0x008e]
[    0.359849] pnp 00:06: [io  0x0090-0x009f]
[    0.359852] pnp 00:06: [io  0x00a2-0x00bf]
[    0.359855] pnp 00:06: [io  0x00e0-0x00ef]
[    0.359858] pnp 00:06: [io  0x04d0-0x04d1]
[    0.359959] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.359970] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.359988] pnp 00:07: [io  0x00f0-0x00ff]
[    0.360087] pnp 00:07: [irq 13]
[    0.360135] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.360247] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.360511] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.360520] pnp 00:09: [io  0x0a00-0x0a0f]
[    0.360523] pnp 00:09: [io  0x0a10-0x0a1f]
[    0.360526] pnp 00:09: [io  0x0a20-0x0a2f]
[    0.360530] pnp 00:09: [io  0x0a30-0x0a3f]
[    0.360620] system 00:09: [io  0x0a00-0x0a0f] has been reserved
[    0.360630] system 00:09: [io  0x0a10-0x0a1f] has been reserved
[    0.360639] system 00:09: [io  0x0a20-0x0a2f] has been reserved
[    0.360647] system 00:09: [io  0x0a30-0x0a3f] has been reserved
[    0.360656] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.360726] pnp 00:0a: [io  0x0060]
[    0.360730] pnp 00:0a: [io  0x0064]
[    0.360740] pnp 00:0a: [irq 12]
[    0.360809] pnp 00:0a: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.361049] pnp 00:0b: [mem 0x98000000-0xafffffff]
[    0.361149] system 00:0b: [mem 0x98000000-0xafffffff] has been reserved
[    0.361161] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.361438] pnp 00:0c: [mem 0xfed00000-0xfed003ff]
[    0.361504] pnp 00:0c: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.361513] pnp: PnP ACPI: found 13 devices
[    0.361521] ACPI: ACPI bus type pnp unregistered
[    0.370040] PCI: max bus depth: 1 pci_try_num: 2
[    0.370152] pci 0000:00:04.0: BAR 14: assigned [mem 0xd0100000-0xd02fffff]
[    0.370170] pci 0000:00:04.0: BAR 15: assigned [mem 0xd0300000-0xd04fffff 64bit pref]
[    0.370183] pci 0000:00:04.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.370192] pci 0000:00:04.0: PCI bridge to [bus 01-01]
[    0.370201] pci 0000:00:04.0:   bridge window [io  0x1000-0x1fff]
[    0.370212] pci 0000:00:04.0:   bridge window [mem 0xd0100000-0xd02fffff]
[    0.370222] pci 0000:00:04.0:   bridge window [mem 0xd0300000-0xd04fffff 64bit pref]
[    0.370235] pci 0000:00:14.4: PCI bridge to [bus 02-02]
[    0.370293] pci 0000:00:15.0: PCI bridge to [bus 03-05]
[    0.370301] pci 0000:00:15.0:   bridge window [io  0xe000-0xefff]
[    0.370312] pci 0000:00:15.0:   bridge window [mem 0xfe000000-0xfe9fffff]
[    0.370323] pci 0000:00:15.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.370338] pci 0000:00:15.2: PCI bridge to [bus 06-06]
[    0.370349] pci 0000:00:15.2:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.370364] pci 0000:00:15.3: PCI bridge to [bus 07-07]
[    0.370373] pci 0000:00:15.3:   bridge window [io  0xd000-0xdfff]
[    0.370387] pci 0000:00:15.3:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.370436] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.370449] pci 0000:00:04.0: setting latency timer to 64
[    0.370467] pci 0000:00:15.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.370477] pci 0000:00:15.0: setting latency timer to 64
[    0.370488] pci 0000:00:15.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.370498] pci 0000:00:15.2: setting latency timer to 64
[    0.370509] pci 0000:00:15.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.370519] pci 0000:00:15.3: setting latency timer to 64
[    0.370526] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
[    0.370530] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
[    0.370534] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
[    0.370538] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff]
[    0.370542] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
[    0.370546] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
[    0.370550] pci_bus 0000:00: resource 10 [mem 0xb0000000-0xffffffff]
[    0.370554] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    0.370559] pci_bus 0000:01: resource 1 [mem 0xd0100000-0xd02fffff]
[    0.370564] pci_bus 0000:01: resource 2 [mem 0xd0300000-0xd04fffff 64bit pref]
[    0.370569] pci_bus 0000:02: resource 4 [io  0x0000-0x03af]
[    0.370574] pci_bus 0000:02: resource 5 [io  0x03e0-0x0cf7]
[    0.370578] pci_bus 0000:02: resource 6 [io  0x03b0-0x03df]
[    0.370583] pci_bus 0000:02: resource 7 [io  0x0d00-0xffff]
[    0.370587] pci_bus 0000:02: resource 8 [mem 0x000a0000-0x000bffff]
[    0.370592] pci_bus 0000:02: resource 9 [mem 0x000c0000-0x000dffff]
[    0.370597] pci_bus 0000:02: resource 10 [mem 0xb0000000-0xffffffff]
[    0.370602] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.370607] pci_bus 0000:03: resource 1 [mem 0xfe000000-0xfe9fffff]
[    0.370612] pci_bus 0000:03: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.370617] pci_bus 0000:06: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.370622] pci_bus 0000:07: resource 0 [io  0xd000-0xdfff]
[    0.370627] pci_bus 0000:07: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.370702] NET: Registered protocol family 2
[    0.371090] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.373686] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.378855] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.379469] TCP: Hash tables configured (established 524288 bind 65536)
[    0.379482] TCP reno registered
[    0.379517] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.379623] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.379878] NET: Registered protocol family 1
[    0.379915] pci 0000:00:01.0: Boot video device
[    0.380057] pci 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.228137] pci 0000:00:12.0: PCI INT A disabled
[    1.228201] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.228256] pci 0000:00:12.2: PCI INT B disabled
[    1.228274] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.308147] pci 0000:00:13.0: PCI INT A disabled
[    1.308191] pci 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.308247] pci 0000:00:13.2: PCI INT B disabled
[    1.308283] pci 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.388138] pci 0000:00:14.5: PCI INT C disabled
[    1.388192] pci 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.437924] Freeing initrd memory: 13872k freed
[    1.468308] pci 0000:00:16.0: PCI INT A disabled
[    1.468351] pci 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.468489] pci 0000:00:16.2: PCI INT B disabled
[    1.468533] pci 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.468652] pci 0000:06:00.0: PCI INT A disabled
[    1.468667] PCI: CLS 64 bytes, default 64
[    1.468672] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.468679] Placing 64MB software IO TLB between ffff88009394b000 - ffff88009794b000
[    1.468688] software IO TLB at phys 0x9394b000 - 0x9794b000
[    1.469421] perf: AMD IBS detected (0x000000ff)
[    1.469953] audit: initializing netlink socket (disabled)
[    1.469987] type=2000 audit(1358329259.468:1): initialized
[    1.514784] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.520093] VFS: Disk quotas dquot_6.5.2
[    1.520209] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.521509] fuse init (API version 7.17)
[    1.521952] msgmni has been set to 15170
[    1.523842] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.524046] io scheduler noop registered
[    1.524063] io scheduler deadline registered
[    1.524184] io scheduler cfq registered (default)
[    1.524741] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.524793] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.525045] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.525062] ACPI: Power Button [PWRB]
[    1.525153] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.525165] ACPI: Power Button [PWRF]
[    1.525358] ACPI: acpi_idle registered with cpuidle
[    1.577591] ERST: Table is not found!
[    1.577606] GHES: HEST is not enabled!
[    1.577980] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.646034] Linux agpgart interface v0.103
[    1.652673] brd: module loaded
[    1.656444] loop: module loaded
[    1.656726] ahci 0000:00:11.0: version 3.0
[    1.656804] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.657082] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    1.657095] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part sxs 
[    1.658598] scsi0 : ahci
[    1.659030] scsi1 : ahci
[    1.659464] scsi2 : ahci
[    1.659903] scsi3 : ahci
[    1.660646] ata1: SATA max UDMA/133 abar m1024@0xfeb4f000 port 0xfeb4f100 irq 19
[    1.660660] ata2: SATA max UDMA/133 abar m1024@0xfeb4f000 port 0xfeb4f180 irq 19
[    1.660670] ata3: SATA max UDMA/133 abar m1024@0xfeb4f000 port 0xfeb4f200 irq 19
[    1.660681] ata4: SATA max UDMA/133 abar m1024@0xfeb4f000 port 0xfeb4f280 irq 19
[    1.661037] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.661771] Fixed MDIO Bus: probed
[    1.661819] tun: Universal TUN/TAP device driver, 1.6
[    1.661826] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.662174] PPP generic driver version 2.4.2
[    1.662812] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.662910] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.662998] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.663320] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.663390] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.663442] QUIRK: Enable AMD PLL fix
[    1.663499] ehci_hcd 0000:00:12.2: debug port 1
[    1.663550] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfeb4d000
[    1.672325] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.672841] hub 1-0:1.0: USB hub found
[    1.672863] hub 1-0:1.0: 5 ports detected
[    1.673091] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.673177] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.673487] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.673557] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.673606] ehci_hcd 0000:00:13.2: debug port 1
[    1.673636] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfeb4b000
[    1.684299] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.684807] hub 2-0:1.0: USB hub found
[    1.684828] hub 2-0:1.0: 5 ports detected
[    1.685059] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.685146] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    1.685475] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.685544] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.685594] ehci_hcd 0000:00:16.2: debug port 1
[    1.685624] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfeb48000
[    1.696298] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.696815] hub 3-0:1.0: USB hub found
[    1.696836] hub 3-0:1.0: 4 ports detected
[    1.697025] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.697102] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.697189] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.697508] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.697622] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfeb4e000
[    1.756798] hub 4-0:1.0: USB hub found
[    1.756860] hub 4-0:1.0: 5 ports detected
[    1.757038] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.757126] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.757431] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.757538] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfeb4c000
[    1.816787] hub 5-0:1.0: USB hub found
[    1.816848] hub 5-0:1.0: 5 ports detected
[    1.817029] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.817118] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.817441] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    1.817538] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfeb4a000
[    1.876803] hub 6-0:1.0: USB hub found
[    1.876865] hub 6-0:1.0: 2 ports detected
[    1.877043] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.877131] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    1.877439] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    1.877545] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfeb49000
[    1.936771] hub 7-0:1.0: USB hub found
[    1.936833] hub 7-0:1.0: 4 ports detected
[    1.936975] uhci_hcd: USB Universal Host Controller Interface driver
[    1.937097] xhci_hcd 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.937187] xhci_hcd 0000:06:00.0: setting latency timer to 64
[    1.937194] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    1.937499] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 8
[    1.937797] xhci_hcd 0000:06:00.0: irq 18, io mem 0xfea00000
[    1.937896] xhci_hcd 0000:06:00.0: irq 40 for MSI/MSI-X
[    1.938354] xHCI xhci_add_endpoint called for root hub
[    1.938361] xHCI xhci_check_bandwidth called for root hub
[    1.938428] hub 8-0:1.0: USB hub found
[    1.938486] hub 8-0:1.0: 1 port detected
[    1.938605] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    1.938915] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 9
[    1.939360] xHCI xhci_add_endpoint called for root hub
[    1.939367] xHCI xhci_check_bandwidth called for root hub
[    1.939436] hub 9-0:1.0: USB hub found
[    1.939497] hub 9-0:1.0: 4 ports detected
[    1.952518] usbcore: registered new interface driver libusual
[    1.952599] i8042: PNP: PS/2 Controller [PNP0f03:PS2M] at 0x60,0x64 irq 12
[    1.952608] i8042: PNP: PS/2 controller doesn't have KBD irq; using default 1
[    1.953087] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.953108] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.953738] mousedev: PS/2 mouse device common for all mice
[    1.954607] rtc_cmos 00:04: RTC can wake from S4
[    1.954965] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.955018] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.955182] device-mapper: uevent: version 1.0.3
[    1.955500] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.955626] cpuidle: using governor ladder
[    1.955789] cpuidle: using governor menu
[    1.955796] EFI Variables Facility v0.08 2004-May-17
[    1.956310] TCP cubic registered
[    1.956515] NET: Registered protocol family 10
[    1.957363] NET: Registered protocol family 17
[    1.957376] Registering the dns_resolver key type
[    1.958273] PM: Hibernation image not present or could not be loaded.
[    1.958309] registered taskstats version 1
[    1.977314]   Magic number: 13:256:677
[    1.977538] rtc_cmos 00:04: setting system clock to 2013-01-16 09:41:00 UTC (1358329260)
[    1.977569] powernow-k8: Found 1 AMD E-350 Processor (2 cpu cores) (version 2.20.00)
[    1.977637] powernow-k8:    0 : pstate 0 (1600 MHz)
[    1.977644] powernow-k8:    1 : pstate 1 (1280 MHz)
[    1.977650] powernow-k8:    2 : pstate 2 (800 MHz)
[    1.978585] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.978601] EDD information not available.
[    1.980303] ata1: SATA link down (SStatus 0 SControl 300)
[    2.152321] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.152379] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.152425] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.153410] ata3.00: ATA-9: WDC WD30EFRX-68AX9N0, 80.00A80, max UDMA/133
[    2.153428] ata3.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.154234] ata4.00: ATA-9: WDC WD30EFRX-68AX9N0, 80.00A80, max UDMA/133
[    2.154251] ata4.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.154317] ata3.00: configured for UDMA/133
[    2.155118] ata4.00: configured for UDMA/133
[    2.177259] ata2.00: ATA-9: SAMSUNG SSD 830 Series, CXM03B1Q, max UDMA/133
[    2.177277] ata2.00: 500118192 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.217245] ata2.00: configured for UDMA/133
[    2.217866] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG SSD 830  CXM0 PQ: 0 ANSI: 5
[    2.218226] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    2.218335] sd 1:0:0:0: [sda] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[    2.218499] scsi 2:0:0:0: Direct-Access     ATA      WDC WD30EFRX-68A 80.0 PQ: 0 ANSI: 5
[    2.218509] sd 1:0:0:0: [sda] Write Protect is off
[    2.218517] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.218562] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.218789] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.218999] sd 2:0:0:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.219011] sd 2:0:0:0: [sdb] 4096-byte physical blocks
[    2.219055] scsi 3:0:0:0: Direct-Access     ATA      WDC WD30EFRX-68A 80.0 PQ: 0 ANSI: 5
[    2.219323] sd 3:0:0:0: [sdc] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.219333] sd 3:0:0:0: [sdc] 4096-byte physical blocks
[    2.219399] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    2.219426] sd 2:0:0:0: [sdb] Write Protect is off
[    2.219438] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.219513] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.219619] sd 3:0:0:0: [sdc] Write Protect is off
[    2.219632] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.220112] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.229036]  sda: sda1 sda2
[    2.231840] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.248312] usb 8-1: new high-speed USB device number 2 using xhci_hcd
[    2.267896] hub 8-1:1.0: USB hub found
[    2.268394] hub 8-1:1.0: 4 ports detected
[    2.286878]  sdb: sdb1
[    2.287722] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.292357]  sdc: sdc1
[    2.293212] sd 3:0:0:0: [sdc] Attached SCSI disk
[    2.296382] Freeing unused kernel memory: 924k freed
[    2.296895] Write protecting the kernel read-only data: 12288k
[    2.307300] Freeing unused kernel memory: 1604k freed
[    2.315852] Freeing unused kernel memory: 1196k freed
[    2.363809] udevd[92]: starting version 175
[    2.468117] Refined TSC clocksource calibration: 1600.000 MHz.
[    2.468141] Switching to clocksource tsc
[    2.492575] hub 8-1:1.0: unable to enumerate USB device on port 2
[    2.564349] usb 8-1.3: new low-speed USB device number 4 using xhci_hcd
[    2.573072] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.573124] r8169 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.573181] r8169 0000:07:00.0: setting latency timer to 64
[    2.573263] r8169 0000:07:00.0: irq 41 for MSI/MSI-X
[    2.574127] r8169 0000:07:00.0: eth0: RTL8168e/8111e at 0xffffc90000c1a000, 00:01:2e:3c:15:52, XID 0c200000 IRQ 41
[    2.574141] r8169 0000:07:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.574194] scsi4 : pata_atiixp
[    2.574844] scsi5 : pata_atiixp
[    2.576366] ata5: PATA max UDMA/100 cmd 0xf140 ctl 0xf130 bmdma 0xf100 irq 17
[    2.576378] ata6: PATA max UDMA/100 cmd 0xf120 ctl 0xf110 bmdma 0xf108 irq 17
[    2.621414] usb 8-1.3: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.621441] usb 8-1.3: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.649162] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:15.2/0000:06:00.0/usb8/8-1/8-1.3/8-1.3:1.0/input/input2
[    2.649711] generic-usb 0003:046D:C30E.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech HID compliant keyboard] on usb-0000:06:00.0-1.3/input0
[    2.681009] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:15.2/0000:06:00.0/usb8/8-1/8-1.3/8-1.3:1.1/input/input3
[    2.681437] generic-usb 0003:046D:C30E.0002: input,hidraw1: USB HID v1.10 Device [Logitech HID compliant keyboard] on usb-0000:06:00.0-1.3/input1
[    2.681493] usbcore: registered new interface driver usbhid
[    2.681501] usbhid: USB HID core driver
[    2.782914] ata5.00: ATA-9: WDC WD30EFRX-68AX9N0, 80.00A80, max UDMA/133
[    2.782932] ata5.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.782947] ata5.00: limited to UDMA/33 due to 40-wire cable
[    2.788974] ata5.00: configured for UDMA/33
[    2.789557] scsi 4:0:0:0: Direct-Access     ATA      WDC WD30EFRX-68A 80.0 PQ: 0 ANSI: 5
[    2.789995] sd 4:0:0:0: [sdd] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.790006] sd 4:0:0:0: [sdd] 4096-byte physical blocks
[    2.790088] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    2.790259] sd 4:0:0:0: [sdd] Write Protect is off
[    2.790268] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.790325] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.865224] usb 9-2: new SuperSpeed USB device number 2 using xhci_hcd
[    2.870167]  sdd: sdd1
[    2.871038] sd 4:0:0:0: [sdd] Attached SCSI disk
[    2.889192] Initializing USB Mass Storage driver...
[    2.890344] scsi6 : usb-storage 9-2:1.0
[    2.890550] usbcore: registered new interface driver usb-storage
[    2.890560] USB Mass Storage support registered.
[    3.890425] scsi 6:0:0:0: Direct-Access     Seagate  USB 3.0 Cable    0211 PQ: 0 ANSI: 0
[    3.892632] sd 6:0:0:0: Attached scsi generic sg4 type 0
[    3.892850] sd 6:0:0:0: [sde] 2930277167 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    3.895194] sd 6:0:0:0: [sde] Write Protect is off
[    3.895215] sd 6:0:0:0: [sde] Mode Sense: 0f 00 00 00
[    3.896327] sd 6:0:0:0: [sde] No Caching mode page present
[    3.896347] sd 6:0:0:0: [sde] Assuming drive cache: write through
[    3.899809] sd 6:0:0:0: [sde] No Caching mode page present
[    3.899838] sd 6:0:0:0: [sde] Assuming drive cache: write through
[    3.901260]  sde: sde1
[    3.905808] sd 6:0:0:0: [sde] No Caching mode page present
[    3.905826] sd 6:0:0:0: [sde] Assuming drive cache: write through
[    3.905835] sd 6:0:0:0: [sde] Attached SCSI disk
[    3.998684] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    8.187941] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.281700] udevd[489]: starting version 175
[    8.788675] lp: driver loaded but no devices found
[    9.250570] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    9.294295] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[    9.294474] SP5100 TCO timer: mmio address 0xbafe00 already in use
[    9.304845] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    9.304856] Disabling lock debugging due to kernel taint
[    9.444238] [fglrx] Maximum main memory to use for locked dma buffers: 7362 MBytes.
[    9.444737] [fglrx]   vendor: 1002 device: 9802 count: 1
[    9.447190] [fglrx] ioport: bar 1, base 0xf000, size: 0x100
[    9.447216] pci 0000:00:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.447224] pci 0000:00:01.0: setting latency timer to 64
[    9.448499] [fglrx] Kernel PAT support is enabled
[    9.448544] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] with 1 minors
[    9.504352] EXT4-fs (sda1): re-mounted. Opts: discard,errors=remount-ro
[    9.745360] type=1400 audit(1358329268.264:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=709 comm="apparmor_parser"
[    9.745731] type=1400 audit(1358329268.264:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=601 comm="apparmor_parser"
[    9.746032] type=1400 audit(1358329268.264:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=709 comm="apparmor_parser"
[    9.746426] type=1400 audit(1358329268.264:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=709 comm="apparmor_parser"
[    9.746446] type=1400 audit(1358329268.264:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=601 comm="apparmor_parser"
[    9.746852] type=1400 audit(1358329268.264:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=601 comm="apparmor_parser"
[    9.753920] snd_hda_intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    9.754027] snd_hda_intel 0000:00:01.1: irq 42 for MSI/MSI-X
[    9.754068] snd_hda_intel 0000:00:01.1: setting latency timer to 64
[    9.798034] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[    9.798205] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input4
[    9.798699] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.836996] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    9.874817] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card1/input5
[    9.877461] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input6
[    9.878345] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input7
[    9.878696] input: HDA ATI SB Line-Out as /devices/pci0000:00/0000:00:14.2/sound/card1/input8
[   10.031487] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: discard
[   10.141459] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[   10.372053] r8169 0000:07:00.0: eth0: link down
[   10.372068] r8169 0000:07:00.0: eth0: link down
[   10.373769] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.930085] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   10.930093] vesafb: scrolling: redraw
[   10.930098] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   10.930698] vesafb: framebuffer at 0xb0000000, mapped to 0xffffc90011800000, using 1216k, total 1216k
[   10.931008] Console: switching to colour frame buffer device 80x30
[   10.932805] fb0: VESA VGA frame buffer device
[   11.122185] EXT4-fs (sde1): mounted filesystem with ordered data mode. Opts: (null)
[   12.322640] r8169 0000:07:00.0: eth0: link up
[   12.324414] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   13.468611] init: failsafe main process (881) killed by TERM signal
[   13.717209] type=1400 audit(1358329272.236:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1105 comm="apparmor_parser"
[   13.717933] type=1400 audit(1358329272.236:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1105 comm="apparmor_parser"
[   13.718338] type=1400 audit(1358329272.236:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1105 comm="apparmor_parser"
[   13.765408] type=1400 audit(1358329272.284:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1107 comm="apparmor_parser"
[   18.251706] fglrx_pci 0000:00:01.0: irq 43 for MSI/MSI-X
[   18.253224] [fglrx] Firegl kernel thread PID: 1355
[   18.253691] [fglrx] Firegl kernel thread PID: 1356
[   18.254090] [fglrx] Firegl kernel thread PID: 1357
[   18.254313] [fglrx] IRQ 43 Enabled
[   18.671101] [fglrx] Gart USWC size:1280 M.
[   18.671109] [fglrx] Gart cacheable size:508 M.
[   18.671118] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   18.671123] [fglrx] Reserved FB block: Unshared offset:fbfd000, size:403000 
[   18.671127] [fglrx] Reserved FB block: Unshared offset:17ff4000, size:c000 
[   19.225237] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=0
[   19.225265] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   19.226671] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=1
[   19.226701] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   19.524239] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   19.824242] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   20.124284] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   20.424291] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   20.724140] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   21.024131] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   21.324276] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   21.628262] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   21.782843] init: plymouth-upstart-bridge main process (915) killed by TERM signal
[   22.928252] eth0: no IPv6 routers present
[   34.876100] init: plymouth-stop pre-start process (1860) terminated with status 1
[   38.092705] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   38.092732] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   38.092773] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[   38.092789] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[   38.120508] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=0
[   38.120536] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   38.121935] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=1
[   38.121963] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   38.392081] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   38.692077] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   38.992080] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   39.292168] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   39.592085] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   39.892069] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   40.192086] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   40.492313] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
```

thanks again - love the great community support around here!

p.s.: i will reset the cables tonight - but I dont think that is it...will keep you posted on the results though.

---

### Post by tgalati4 on 2013-01-16
You have a mixture of SATA spinners, SSD, and PATA drives.  Try disconnecting the PATA drive, and turning off the PATA compatibility in BIOS and rerun the tests.  It could be a BIOS issue or a SATA timing issue on the motherboard.  Or it could be a kernel regression from an update.  How long have you been running your current setup and when did you first notice the speed problem?

---

### Post by EuleLL on 2013-01-16
I have been running this setup for a month now and i only realized it a couple of days ago - however i was not constantly monitoring the SSD speed - so this could have been going on for some while now.
the pata drive must actually be the usb drive with a sata hdd inside - i was gonna make it an internal drive anyway. I will check bios settings, recheck all cables and then report the status...

thanks!

---

### Post by EuleLL on 2013-01-16
so - ive swichted and replugged cables, changed the sata port of the drive, checked the bios settings, set them to default and enabled ahci, connected the usb drive via sata and still no luck.

There was no pata setting in the bios as there are only sata connectors on the mainboard...

to be clear: i have 4 spinning sata drives connected and 1 SSD - all via SATA 6GB/s cables - nothing else is connected the mainboard (not pata drives or other USB equipment except for a keyboard and a mouse)

any suggestions?

this seems very strange...

just in case - the current dmesg output:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-35-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 (Ubuntu 3.2.0-35.55-generic 3.2.34)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-35-generic root=UUID=864d7002-477e-473f-b5ba-534fad0a0caa ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009794a000 (usable)
[    0.000000]  BIOS-e820: 000000009794a000 - 0000000097995000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000097995000 - 000000009799d000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009799d000 - 00000000979a0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000979a0000 - 0000000097a71000 (reserved)
[    0.000000]  BIOS-e820: 0000000097a71000 - 0000000097a72000 (usable)
[    0.000000]  BIOS-e820: 0000000097a72000 - 0000000097a82000 (reserved)
[    0.000000]  BIOS-e820: 0000000097a82000 - 0000000097a8a000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000097a8a000 - 0000000097ab4000 (reserved)
[    0.000000]  BIOS-e820: 0000000097ab4000 - 0000000097af7000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000097af7000 - 0000000097d71000 (usable)
[    0.000000]  BIOS-e820: 0000000097d71000 - 0000000097ef7000 (reserved)
[    0.000000]  BIOS-e820: 0000000097ef7000 - 0000000097f00000 (usable)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec11000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed61000 - 00000000fed71000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed80000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fef00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100001000 - 000000024f000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.7 present.
[    0.000000] DMI: MotherBoard By ZOTAC MotherBoard Fusion350-B-B/E/J/U/Fusion350-B-B/E/J/U, BIOS 4.6.4 11/14/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x24f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF write-through
[    0.000000]   C0000-CEFFF write-protect
[    0.000000]   CF000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 097F00000 mask FFFF00000 uncachable
[    0.000000]   2 base 098000000 mask FF8000000 uncachable
[    0.000000]   3 base 0A0000000 mask FE0000000 uncachable
[    0.000000]   4 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000024f000000 aka 9456M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 2431MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2432MB, range: 128MB, type UC
[    0.000000] reg 3, base: 2560MB, range: 512MB, type UC
[    0.000000] reg 4, base: 3GB, range: 1GB, type UC
[    0.000000] total RAM covered: 2431M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 2M 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 256MB, type WB
[    0.000000] reg 2, base: 2304MB, range: 128MB, type WB
[    0.000000] reg 3, base: 2431MB, range: 1MB, type UC
[    0.000000] e820 update range: 0000000097f00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x97f00 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000fcdf0] fcdf0
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-0000000097f00000
[    0.000000]  0000000000 - 0080000000 page 1G
[    0.000000]  0080000000 - 0097e00000 page 2M
[    0.000000]  0097e00000 - 0097f00000 page 4k
[    0.000000] kernel direct mapping tables up to 97f00000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-000000024f000000
[    0.000000]  0100000000 - 0240000000 page 1G
[    0.000000]  0240000000 - 024f000000 page 2M
[    0.000000] kernel direct mapping tables up to 24f000000 @ 97efe000-97f00000
[    0.000000] RAMDISK: 364d8000 - 37264000
[    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0000000097995068 00054 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 000000009799a4c8 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110623/tbfadt-560)
[    0.000000] ACPI: DSDT 0000000097995150 05371 (v02 ALASKA    A M I 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 0000000097a89f80 00040
[    0.000000] ACPI: APIC 000000009799a5c0 00062 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 000000009799a628 0003C (v01 ALASKA    A M I 01072009 MSFT 00010013)
[    0.000000] ACPI: HPET 000000009799a668 00038 (v01 ALASKA    A M I 01072009 AMI  00000004)
[    0.000000] ACPI: SSDT 000000009799a6a0 003DE (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: SSDT 000000009799aa80 0168E (v02    AMD     ALIB 00000001 MSFT 04000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000024f000000
[    0.000000] Initmem setup node 0 0000000000000000-000000024f000000
[    0.000000]   NODE_DATA [000000024effb000 - 000000024effffff]
[    0.000000]  [ffffea0000000000-ffffea00093fffff] PMD -> [ffff880246c00000-ffff88024e5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0024f000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0009794a
[    0.000000]     0: 0x00097a71 -> 0x00097a72
[    0.000000]     0: 0x00097af7 -> 0x00097d71
[    0.000000]     0: 0x00097ef7 -> 0x00097f00
[    0.000000]     0: 0x00100001 -> 0x0024f000
[    0.000000] On node 0 totalpages: 1993562
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3912 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 601102 pages, LIFO batch:31
[    0.000000]   Normal zone: 21440 pages used for memmap
[    0.000000]   Normal zone: 1350719 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000009794a000 - 0000000097995000
[    0.000000] PM: Registered nosave memory: 0000000097995000 - 000000009799d000
[    0.000000] PM: Registered nosave memory: 000000009799d000 - 00000000979a0000
[    0.000000] PM: Registered nosave memory: 00000000979a0000 - 0000000097a71000
[    0.000000] PM: Registered nosave memory: 0000000097a72000 - 0000000097a82000
[    0.000000] PM: Registered nosave memory: 0000000097a82000 - 0000000097a8a000
[    0.000000] PM: Registered nosave memory: 0000000097a8a000 - 0000000097ab4000
[    0.000000] PM: Registered nosave memory: 0000000097ab4000 - 0000000097af7000
[    0.000000] PM: Registered nosave memory: 0000000097d71000 - 0000000097ef7000
[    0.000000] PM: Registered nosave memory: 0000000097f00000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fec11000
[    0.000000] PM: Registered nosave memory: 00000000fec11000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed01000
[    0.000000] PM: Registered nosave memory: 00000000fed01000 - 00000000fed61000
[    0.000000] PM: Registered nosave memory: 00000000fed61000 - 00000000fed71000
[    0.000000] PM: Registered nosave memory: 00000000fed71000 - 00000000fed80000
[    0.000000] PM: Registered nosave memory: 00000000fed80000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000fef00000
[    0.000000] PM: Registered nosave memory: 00000000fef00000 - 0000000100000000
[    0.000000] PM: Registered nosave memory: 0000000100000000 - 0000000100001000
[    0.000000] Allocating PCI resources starting at 97f00000 (gap: 97f00000:66d00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88024ec00000 s83136 r8192 d23360 u1048576
[    0.000000] pcpu-alloc: s83136 r8192 d23360 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1955733
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-35-generic root=UUID=864d7002-477e-473f-b5ba-534fad0a0caa ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7753340k/9682944k available (6569k kernel code, 1708696k absent, 220908k reserved, 6634k data, 924k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 63963136 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1600.143 MHz processor.
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3200.28 BogoMIPS (lpj=6400572)
[    0.004022] pid_max: default: 32768 minimum: 301
[    0.004071] Security Framework initialized
[    0.004102] AppArmor: AppArmor initialized
[    0.004110] Yama: becoming mindful.
[    0.005320] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.011710] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.014253] Mount-cache hash table entries: 256
[    0.014513] Initializing cgroup subsys cpuacct
[    0.014529] Initializing cgroup subsys memory
[    0.014549] Initializing cgroup subsys devices
[    0.014556] Initializing cgroup subsys freezer
[    0.014563] Initializing cgroup subsys blkio
[    0.014578] Initializing cgroup subsys perf_event
[    0.014639] tseg: 0097f00000
[    0.014645] CPU: Physical Processor ID: 0
[    0.014651] CPU: Processor Core ID: 0
[    0.014659] mce: CPU supports 6 MCE banks
[    0.019293] ACPI: Core revision 20110623
[    0.028040] ftrace: allocating 27030 entries in 107 pages
[    0.036443] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076164] CPU0: AMD E-350 Processor stepping 00
[    0.080004] Performance Events: AMD PMU driver.
[    0.080004] ... version:                0
[    0.080004] ... bit width:              48
[    0.080004] ... generic registers:      4
[    0.080004] ... value mask:             0000ffffffffffff
[    0.080004] ... max period:             00007fffffffffff
[    0.080004] ... fixed-purpose events:   0
[    0.080004] ... event mask:             000000000000000f
[    0.080004] NMI watchdog enabled, takes one hw-pmu counter.
[    0.080004] Booting Node   0, Processors  #1 Ok.
[    0.080004] smpboot cpu 1: start_ip = 98000
[    0.168047] NMI watchdog enabled, takes one hw-pmu counter.
[    0.168095] Brought up 2 CPUs
[    0.168103] Total of 2 processors activated (6399.99 BogoMIPS).
[    0.168733] devtmpfs: initialized
[    0.172446] EVM: security.selinux
[    0.172454] EVM: security.SMACK64
[    0.172459] EVM: security.capability
[    0.172494] PM: Registering ACPI NVS region at 9794a000 (307200 bytes)
[    0.172494] PM: Registering ACPI NVS region at 9799d000 (12288 bytes)
[    0.172494] PM: Registering ACPI NVS region at 97a82000 (32768 bytes)
[    0.172494] PM: Registering ACPI NVS region at 97ab4000 (274432 bytes)
[    0.173817] print_constraints: dummy: 
[    0.173888] RTC time: 18:53:40, date: 01/16/13
[    0.173961] NET: Registered protocol family 16
[    0.174110] Trying to unpack rootfs image as initramfs...
[    0.174388] Extended Config Space enabled on 0 nodes
[    0.174433] ACPI: bus type pci registered
[    0.174551] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.174564] PCI: not using MMCONFIG
[    0.174570] PCI: Using configuration type 1 for base access
[    0.174576] PCI: Using configuration type 1 for extended access
[    0.177300] bio: create slab <bio-0> at 0
[    0.177488] ACPI: Added _OSI(Module Device)
[    0.177497] ACPI: Added _OSI(Processor Device)
[    0.177503] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.177510] ACPI: Added _OSI(Processor Aggregator Device)
[    0.179079] ACPI: EC: Look up EC in DSDT
[    0.180872] ACPI: Executed 2 blocks of module-level executable AML code
[    0.212858] ACPI: Interpreter enabled
[    0.212877] ACPI: (supports S0 S3 S4 S5)
[    0.212930] ACPI: Using IOAPIC for interrupt routing
[    0.213025] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.213111] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.307770] ACPI: No dock devices found.
[    0.307786] HEST: Table not found.
[    0.307796] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.308188] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.308684] pci_root PNP0A08:00: host bridge window [io  0x0000-0x03af]
[    0.308694] pci_root PNP0A08:00: host bridge window [io  0x03e0-0x0cf7]
[    0.308702] pci_root PNP0A08:00: host bridge window [io  0x03b0-0x03df]
[    0.308710] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.308718] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.308727] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000dffff]
[    0.308736] pci_root PNP0A08:00: host bridge window [mem 0xb0000000-0xffffffff]
[    0.308764] pci 0000:00:00.0: [1022:1510] type 0 class 0x000600
[    0.308826] pci 0000:00:01.0: [1002:9802] type 0 class 0x000300
[    0.308842] pci 0000:00:01.0: reg 10: [mem 0xb0000000-0xbfffffff pref]
[    0.308853] pci 0000:00:01.0: reg 14: [io  0xf000-0xf0ff]
[    0.308863] pci 0000:00:01.0: reg 18: [mem 0xfeb00000-0xfeb3ffff]
[    0.308927] pci 0000:00:01.0: supports D1 D2
[    0.308953] pci 0000:00:01.1: [1002:1314] type 0 class 0x000403
[    0.308967] pci 0000:00:01.1: reg 10: [mem 0xfeb44000-0xfeb47fff]
[    0.309042] pci 0000:00:01.1: supports D1 D2
[    0.309113] pci 0000:00:04.0: [1022:1512] type 1 class 0x000604
[    0.309194] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.309201] pci 0000:00:04.0: PME# disabled
[    0.309257] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    0.309283] pci 0000:00:11.0: reg 10: [io  0xf190-0xf197]
[    0.309298] pci 0000:00:11.0: reg 14: [io  0xf180-0xf183]
[    0.309312] pci 0000:00:11.0: reg 18: [io  0xf170-0xf177]
[    0.309326] pci 0000:00:11.0: reg 1c: [io  0xf160-0xf163]
[    0.309340] pci 0000:00:11.0: reg 20: [io  0xf150-0xf15f]
[    0.309354] pci 0000:00:11.0: reg 24: [mem 0xfeb4f000-0xfeb4f3ff]
[    0.309437] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.309456] pci 0000:00:12.0: reg 10: [mem 0xfeb4e000-0xfeb4efff]
[    0.309555] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.309582] pci 0000:00:12.2: reg 10: [mem 0xfeb4d000-0xfeb4d0ff]
[    0.309693] pci 0000:00:12.2: supports D1 D2
[    0.309697] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.309704] pci 0000:00:12.2: PME# disabled
[    0.309734] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.309753] pci 0000:00:13.0: reg 10: [mem 0xfeb4c000-0xfeb4cfff]
[    0.309852] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.309879] pci 0000:00:13.2: reg 10: [mem 0xfeb4b000-0xfeb4b0ff]
[    0.309990] pci 0000:00:13.2: supports D1 D2
[    0.309993] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.310000] pci 0000:00:13.2: PME# disabled
[    0.310032] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.310134] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.310153] pci 0000:00:14.1: reg 10: [io  0xf140-0xf147]
[    0.310168] pci 0000:00:14.1: reg 14: [io  0xf130-0xf133]
[    0.310182] pci 0000:00:14.1: reg 18: [io  0xf120-0xf127]
[    0.310196] pci 0000:00:14.1: reg 1c: [io  0xf110-0xf113]
[    0.310210] pci 0000:00:14.1: reg 20: [io  0xf100-0xf10f]
[    0.310264] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.310294] pci 0000:00:14.2: reg 10: [mem 0xfeb40000-0xfeb43fff 64bit]
[    0.310384] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.310390] pci 0000:00:14.2: PME# disabled
[    0.310414] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.310519] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.310578] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.310598] pci 0000:00:14.5: reg 10: [mem 0xfeb4a000-0xfeb4afff]
[    0.310698] pci 0000:00:15.0: [1002:43a0] type 1 class 0x000604
[    0.310807] pci 0000:00:15.0: supports D1 D2
[    0.310846] pci 0000:00:15.2: [1002:43a2] type 1 class 0x000604
[    0.310953] pci 0000:00:15.2: supports D1 D2
[    0.310991] pci 0000:00:15.3: [1002:43a3] type 1 class 0x000604
[    0.311098] pci 0000:00:15.3: supports D1 D2
[    0.311136] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
[    0.311155] pci 0000:00:16.0: reg 10: [mem 0xfeb49000-0xfeb49fff]
[    0.311254] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
[    0.311281] pci 0000:00:16.2: reg 10: [mem 0xfeb48000-0xfeb480ff]
[    0.311392] pci 0000:00:16.2: supports D1 D2
[    0.311395] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.311402] pci 0000:00:16.2: PME# disabled
[    0.311438] pci 0000:00:18.0: [1022:1700] type 0 class 0x000600
[    0.311489] pci 0000:00:18.1: [1022:1701] type 0 class 0x000600
[    0.311535] pci 0000:00:18.2: [1022:1702] type 0 class 0x000600
[    0.311583] pci 0000:00:18.3: [1022:1703] type 0 class 0x000600
[    0.311643] pci 0000:00:18.4: [1022:1704] type 0 class 0x000600
[    0.311688] pci 0000:00:18.5: [1022:1718] type 0 class 0x000600
[    0.311733] pci 0000:00:18.6: [1022:1716] type 0 class 0x000600
[    0.311779] pci 0000:00:18.7: [1022:1719] type 0 class 0x000600
[    0.311925] pci 0000:00:04.0: PCI bridge to [bus 01-01]
[    0.312079] pci 0000:00:14.4: PCI bridge to [bus 02-02] (subtractive decode)
[    0.312098] pci 0000:00:14.4:   bridge window [io  0x0000-0x03af] (subtractive decode)
[    0.312102] pci 0000:00:14.4:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
[    0.312107] pci 0000:00:14.4:   bridge window [io  0x03b0-0x03df] (subtractive decode)
[    0.312111] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.312115] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.312120] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.312124] pci 0000:00:14.4:   bridge window [mem 0xb0000000-0xffffffff] (subtractive decode)
[    0.312196] pci 0000:00:15.0: PCI bridge to [bus 03-05]
[    0.312208] pci 0000:00:15.0:   bridge window [io  0xe000-0xefff]
[    0.312215] pci 0000:00:15.0:   bridge window [mem 0xfe000000-0xfe9fffff]
[    0.312224] pci 0000:00:15.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.312320] pci 0000:06:00.0: [1106:3432] type 0 class 0x000c03
[    0.312342] pci 0000:06:00.0: reg 10: [mem 0xfea00000-0xfea00fff]
[    0.312481] pci 0000:06:00.0: supports D1 D2
[    0.312484] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.312492] pci 0000:06:00.0: PME# disabled
[    0.320119] pci 0000:00:15.2: PCI bridge to [bus 06-06]
[    0.320147] pci 0000:00:15.2:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.320264] pci 0000:07:00.0: [10ec:8168] type 0 class 0x000200
[    0.320292] pci 0000:07:00.0: reg 10: [io  0xd000-0xd0ff]
[    0.320332] pci 0000:07:00.0: reg 18: [mem 0xd0004000-0xd0004fff 64bit pref]
[    0.320358] pci 0000:07:00.0: reg 20: [mem 0xd0000000-0xd0003fff 64bit pref]
[    0.320467] pci 0000:07:00.0: supports D1 D2
[    0.320471] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.320480] pci 0000:07:00.0: PME# disabled
[    0.328111] pci 0000:00:15.3: PCI bridge to [bus 07-07]
[    0.328137] pci 0000:00:15.3:   bridge window [io  0xd000-0xdfff]
[    0.328151] pci 0000:00:15.3:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.328202] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.328524] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE20._PRT]
[    0.328587] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE22._PRT]
[    0.328643] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE23._PRT]
[    0.328704] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR14._PRT]
[    0.328762]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.328774]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.328782] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.339581] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *7 10 11 14 15)
[    0.339794] ACPI: PCI Interrupt Link [LNKB] (IRQs *4 7 10 11 14 15)
[    0.339997] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 *11 14 15)
[    0.340138] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 14 15)
[    0.340242] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 14 15) *0
[    0.340328] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 14 15) *0
[    0.340412] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 11 14 15) *0
[    0.340536] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 14 15) *0
[    0.340778] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    0.340813] vgaarb: loaded
[    0.340818] vgaarb: bridge control possible 0000:00:01.0
[    0.341039] i2c-core: driver [aat2870] using legacy suspend method
[    0.341047] i2c-core: driver [aat2870] using legacy resume method
[    0.341175] SCSI subsystem initialized
[    0.341305] libata version 3.00 loaded.
[    0.341411] usbcore: registered new interface driver usbfs
[    0.341438] usbcore: registered new interface driver hub
[    0.341497] usbcore: registered new device driver usb
[    0.341683] PCI: Using ACPI for IRQ routing
[    0.352751] PCI: pci_cache_line_size set to 64 bytes
[    0.352915] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    0.352919] reserve RAM buffer: 000000009794a000 - 0000000097ffffff 
[    0.352926] reserve RAM buffer: 0000000097a72000 - 0000000097ffffff 
[    0.352931] reserve RAM buffer: 0000000097d71000 - 0000000097ffffff 
[    0.352935] reserve RAM buffer: 0000000097f00000 - 0000000097ffffff 
[    0.352939] reserve RAM buffer: 000000024f000000 - 000000024fffffff 
[    0.353133] NetLabel: Initializing
[    0.353142] NetLabel:  domain hash size = 128
[    0.353148] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.353171] NetLabel:  unlabeled traffic allowed by default
[    0.353282] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.353295] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.355337] Switching to clocksource hpet
[    0.365269] AppArmor: AppArmor Filesystem Enabled
[    0.365346] pnp: PnP ACPI init
[    0.365385] ACPI: bus type pnp registered
[    0.365723] pnp 00:00: [bus 00-ff]
[    0.365729] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.365733] pnp 00:00: [io  0x0000-0x03af window]
[    0.365738] pnp 00:00: [io  0x03e0-0x0cf7 window]
[    0.365742] pnp 00:00: [io  0x03b0-0x03df window]
[    0.365747] pnp 00:00: [io  0x0d00-0xffff window]
[    0.365751] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.365756] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.365760] pnp 00:00: [mem 0xb0000000-0xffffffff window]
[    0.365765] pnp 00:00: [mem 0x00000000 window]
[    0.365864] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.365930] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.366038] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.366051] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.366810] pnp 00:02: [io  0x040b]
[    0.366814] pnp 00:02: [io  0x04d6]
[    0.366818] pnp 00:02: [io  0x0c00-0x0c01]
[    0.366821] pnp 00:02: [io  0x0c14]
[    0.366825] pnp 00:02: [io  0x0c50-0x0c51]
[    0.366828] pnp 00:02: [io  0x0c52]
[    0.366831] pnp 00:02: [io  0x0c6c]
[    0.366834] pnp 00:02: [io  0x0c6f]
[    0.366837] pnp 00:02: [io  0x0cd0-0x0cd1]
[    0.366840] pnp 00:02: [io  0x0cd2-0x0cd3]
[    0.366843] pnp 00:02: [io  0x0cd4-0x0cd5]
[    0.366846] pnp 00:02: [io  0x0cd6-0x0cd7]
[    0.366850] pnp 00:02: [io  0x0cd8-0x0cdf]
[    0.366857] pnp 00:02: [io  0x0800-0x089f]
[    0.366861] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
[    0.366865] pnp 00:02: [io  0x0000-0x000f]
[    0.366868] pnp 00:02: [io  0x0b20-0x0b3f]
[    0.366871] pnp 00:02: [io  0x0900-0x090f]
[    0.366874] pnp 00:02: [io  0x0910-0x091f]
[    0.366878] pnp 00:02: [io  0xfe00-0xfefe]
[    0.366881] pnp 00:02: [io  0x0060-0x005f disabled]
[    0.366885] pnp 00:02: [io  0x0064-0x0063 disabled]
[    0.366888] pnp 00:02: [mem 0xfec00000-0xfec00fff]
[    0.366892] pnp 00:02: [mem 0xfee00000-0xfee00fff]
[    0.366896] pnp 00:02: [mem 0xfed80000-0xfed8ffff]
[    0.366899] pnp 00:02: [mem 0xfed61000-0xfed70fff]
[    0.366903] pnp 00:02: [mem 0xfec10000-0xfec10fff]
[    0.366906] pnp 00:02: [mem 0xfed00000-0xfed00fff]
[    0.366909] pnp 00:02: [mem 0xffc00000-0xffffffff]
[    0.367036] system 00:02: [io  0x040b] has been reserved
[    0.367046] system 00:02: [io  0x04d6] has been reserved
[    0.367054] system 00:02: [io  0x0c00-0x0c01] has been reserved
[    0.367062] system 00:02: [io  0x0c14] has been reserved
[    0.367070] system 00:02: [io  0x0c50-0x0c51] has been reserved
[    0.367077] system 00:02: [io  0x0c52] has been reserved
[    0.367085] system 00:02: [io  0x0c6c] has been reserved
[    0.367092] system 00:02: [io  0x0c6f] has been reserved
[    0.367100] system 00:02: [io  0x0cd0-0x0cd1] has been reserved
[    0.367108] system 00:02: [io  0x0cd2-0x0cd3] has been reserved
[    0.367115] system 00:02: [io  0x0cd4-0x0cd5] has been reserved
[    0.367123] system 00:02: [io  0x0cd6-0x0cd7] has been reserved
[    0.367131] system 00:02: [io  0x0cd8-0x0cdf] has been reserved
[    0.367138] system 00:02: [io  0x0800-0x089f] has been reserved
[    0.367147] system 00:02: [io  0x0b20-0x0b3f] has been reserved
[    0.367154] system 00:02: [io  0x0900-0x090f] has been reserved
[    0.367162] system 00:02: [io  0x0910-0x091f] has been reserved
[    0.367170] system 00:02: [io  0xfe00-0xfefe] has been reserved
[    0.367180] system 00:02: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.367189] system 00:02: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.367198] system 00:02: [mem 0xfed80000-0xfed8ffff] has been reserved
[    0.367207] system 00:02: [mem 0xfed61000-0xfed70fff] has been reserved
[    0.367216] system 00:02: [mem 0xfec10000-0xfec10fff] has been reserved
[    0.367229] system 00:02: [mem 0xfed00000-0xfed00fff] has been reserved
[    0.367239] system 00:02: [mem 0xffc00000-0xffffffff] has been reserved
[    0.367249] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.367779] pnp 00:03: [io  0x02f8-0x02ff]
[    0.367800] pnp 00:03: [irq 3]
[    0.367804] pnp 00:03: [dma 0 disabled]
[    0.367911] pnp 00:03: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.367934] pnp 00:04: [dma 4]
[    0.367938] pnp 00:04: [io  0x0000-0x000f]
[    0.367941] pnp 00:04: [io  0x0081-0x0083]
[    0.367944] pnp 00:04: [io  0x0087]
[    0.367948] pnp 00:04: [io  0x0089-0x008b]
[    0.367951] pnp 00:04: [io  0x008f]
[    0.367954] pnp 00:04: [io  0x00c0-0x00df]
[    0.368097] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.368118] pnp 00:05: [io  0x0070-0x0071]
[    0.368169] pnp 00:05: [irq 8]
[    0.368229] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.368246] pnp 00:06: [io  0x0061]
[    0.368292] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.368342] pnp 00:07: [io  0x0010-0x001f]
[    0.368346] pnp 00:07: [io  0x0022-0x003f]
[    0.368349] pnp 00:07: [io  0x0044-0x005f]
[    0.368352] pnp 00:07: [io  0x0072-0x007f]
[    0.368356] pnp 00:07: [io  0x0080]
[    0.368359] pnp 00:07: [io  0x0084-0x0086]
[    0.368362] pnp 00:07: [io  0x0088]
[    0.368365] pnp 00:07: [io  0x008c-0x008e]
[    0.368368] pnp 00:07: [io  0x0090-0x009f]
[    0.368371] pnp 00:07: [io  0x00a2-0x00bf]
[    0.368374] pnp 00:07: [io  0x00e0-0x00ef]
[    0.368378] pnp 00:07: [io  0x04d0-0x04d1]
[    0.368479] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.368491] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.368510] pnp 00:08: [io  0x00f0-0x00ff]
[    0.368557] pnp 00:08: [irq 13]
[    0.368608] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.368714] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.368974] pnp 00:0a: [io  0x0000-0xffffffffffffffff disabled]
[    0.368978] pnp 00:0a: [io  0x0a00-0x0a0f]
[    0.368981] pnp 00:0a: [io  0x0a10-0x0a1f]
[    0.368985] pnp 00:0a: [io  0x0a20-0x0a2f]
[    0.368988] pnp 00:0a: [io  0x0a30-0x0a3f]
[    0.369082] system 00:0a: [io  0x0a00-0x0a0f] has been reserved
[    0.369092] system 00:0a: [io  0x0a10-0x0a1f] has been reserved
[    0.369101] system 00:0a: [io  0x0a20-0x0a2f] has been reserved
[    0.369109] system 00:0a: [io  0x0a30-0x0a3f] has been reserved
[    0.369118] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.369226] pnp 00:0b: [io  0x0060]
[    0.369230] pnp 00:0b: [io  0x0064]
[    0.369279] pnp 00:0b: [irq 12]
[    0.369344] pnp 00:0b: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.369586] pnp 00:0c: [mem 0x98000000-0xafffffff]
[    0.369686] system 00:0c: [mem 0x98000000-0xafffffff] has been reserved
[    0.369698] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.369940] pnp 00:0d: [mem 0xfed00000-0xfed003ff]
[    0.370010] pnp 00:0d: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.370020] pnp: PnP ACPI: found 14 devices
[    0.370027] ACPI: ACPI bus type pnp unregistered
[    0.378444] PCI: max bus depth: 1 pci_try_num: 2
[    0.378556] pci 0000:00:04.0: BAR 14: assigned [mem 0xd0100000-0xd02fffff]
[    0.378572] pci 0000:00:04.0: BAR 15: assigned [mem 0xd0300000-0xd04fffff 64bit pref]
[    0.378585] pci 0000:00:04.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.378594] pci 0000:00:04.0: PCI bridge to [bus 01-01]
[    0.378602] pci 0000:00:04.0:   bridge window [io  0x1000-0x1fff]
[    0.378613] pci 0000:00:04.0:   bridge window [mem 0xd0100000-0xd02fffff]
[    0.378623] pci 0000:00:04.0:   bridge window [mem 0xd0300000-0xd04fffff 64bit pref]
[    0.378636] pci 0000:00:14.4: PCI bridge to [bus 02-02]
[    0.378656] pci 0000:00:15.0: PCI bridge to [bus 03-05]
[    0.378665] pci 0000:00:15.0:   bridge window [io  0xe000-0xefff]
[    0.378676] pci 0000:00:15.0:   bridge window [mem 0xfe000000-0xfe9fffff]
[    0.378687] pci 0000:00:15.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.378702] pci 0000:00:15.2: PCI bridge to [bus 06-06]
[    0.378713] pci 0000:00:15.2:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.378729] pci 0000:00:15.3: PCI bridge to [bus 07-07]
[    0.378737] pci 0000:00:15.3:   bridge window [io  0xd000-0xdfff]
[    0.378751] pci 0000:00:15.3:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.378798] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.378810] pci 0000:00:04.0: setting latency timer to 64
[    0.378828] pci 0000:00:15.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.378839] pci 0000:00:15.0: setting latency timer to 64
[    0.378849] pci 0000:00:15.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.378859] pci 0000:00:15.2: setting latency timer to 64
[    0.378870] pci 0000:00:15.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.378881] pci 0000:00:15.3: setting latency timer to 64
[    0.378887] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
[    0.378892] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
[    0.378895] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
[    0.378899] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff]
[    0.378903] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
[    0.378907] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
[    0.378912] pci_bus 0000:00: resource 10 [mem 0xb0000000-0xffffffff]
[    0.378916] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    0.378920] pci_bus 0000:01: resource 1 [mem 0xd0100000-0xd02fffff]
[    0.378926] pci_bus 0000:01: resource 2 [mem 0xd0300000-0xd04fffff 64bit pref]
[    0.378931] pci_bus 0000:02: resource 4 [io  0x0000-0x03af]
[    0.378936] pci_bus 0000:02: resource 5 [io  0x03e0-0x0cf7]
[    0.378940] pci_bus 0000:02: resource 6 [io  0x03b0-0x03df]
[    0.378945] pci_bus 0000:02: resource 7 [io  0x0d00-0xffff]
[    0.378950] pci_bus 0000:02: resource 8 [mem 0x000a0000-0x000bffff]
[    0.378954] pci_bus 0000:02: resource 9 [mem 0x000c0000-0x000dffff]
[    0.378959] pci_bus 0000:02: resource 10 [mem 0xb0000000-0xffffffff]
[    0.378964] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.378969] pci_bus 0000:03: resource 1 [mem 0xfe000000-0xfe9fffff]
[    0.378974] pci_bus 0000:03: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.378979] pci_bus 0000:06: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.378984] pci_bus 0000:07: resource 0 [io  0xd000-0xdfff]
[    0.378989] pci_bus 0000:07: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.379066] NET: Registered protocol family 2
[    0.379447] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.382042] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.387258] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.387872] TCP: Hash tables configured (established 524288 bind 65536)
[    0.387884] TCP reno registered
[    0.387920] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.388113] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.388365] NET: Registered protocol family 1
[    0.388401] pci 0000:00:01.0: Boot video device
[    0.388492] pci 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.236139] pci 0000:00:12.0: PCI INT A disabled
[    1.236206] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.236261] pci 0000:00:12.2: PCI INT B disabled
[    1.236278] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.316144] pci 0000:00:13.0: PCI INT A disabled
[    1.316190] pci 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.316246] pci 0000:00:13.2: PCI INT B disabled
[    1.316281] pci 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.396140] pci 0000:00:14.5: PCI INT C disabled
[    1.396193] pci 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.444673] Freeing initrd memory: 13872k freed
[    1.476303] pci 0000:00:16.0: PCI INT A disabled
[    1.476346] pci 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.476484] pci 0000:00:16.2: PCI INT B disabled
[    1.476528] pci 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.476647] pci 0000:06:00.0: PCI INT A disabled
[    1.476662] PCI: CLS 64 bytes, default 64
[    1.476667] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.476675] Placing 64MB software IO TLB between ffff88009394a000 - ffff88009794a000
[    1.476684] software IO TLB at phys 0x9394a000 - 0x9794a000
[    1.477401] perf: AMD IBS detected (0x000000ff)
[    1.477933] audit: initializing netlink socket (disabled)
[    1.477966] type=2000 audit(1358362421.476:1): initialized
[    1.522769] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.528074] VFS: Disk quotas dquot_6.5.2
[    1.528190] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.529493] fuse init (API version 7.17)
[    1.529945] msgmni has been set to 15170
[    1.531827] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.532051] io scheduler noop registered
[    1.532067] io scheduler deadline registered
[    1.532181] io scheduler cfq registered (default)
[    1.532745] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.532798] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.533050] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.533068] ACPI: Power Button [PWRB]
[    1.533155] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.533167] ACPI: Power Button [PWRF]
[    1.533430] ACPI: acpi_idle registered with cpuidle
[    1.585636] ERST: Table is not found!
[    1.585650] GHES: HEST is not enabled!
[    1.586022] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.607109] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.685830] 00:03: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.687364] Linux agpgart interface v0.103
[    1.693561] brd: module loaded
[    1.696415] loop: module loaded
[    1.696695] ahci 0000:00:11.0: version 3.0
[    1.696773] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.697020] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    1.697033] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part sxs 
[    1.698525] scsi0 : ahci
[    1.698954] scsi1 : ahci
[    1.699388] scsi2 : ahci
[    1.699829] scsi3 : ahci
[    1.700572] ata1: SATA max UDMA/133 abar m1024@0xfeb4f000 port 0xfeb4f100 irq 19
[    1.700585] ata2: SATA max UDMA/133 abar m1024@0xfeb4f000 port 0xfeb4f180 irq 19
[    1.700596] ata3: SATA max UDMA/133 abar m1024@0xfeb4f000 port 0xfeb4f200 irq 19
[    1.700607] ata4: SATA max UDMA/133 abar m1024@0xfeb4f000 port 0xfeb4f280 irq 19
[    1.700899] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.701593] Fixed MDIO Bus: probed
[    1.701640] tun: Universal TUN/TAP device driver, 1.6
[    1.701647] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.701972] PPP generic driver version 2.4.2
[    1.702603] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.702702] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.702789] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.703086] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.703156] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.703210] QUIRK: Enable AMD PLL fix
[    1.703267] ehci_hcd 0000:00:12.2: debug port 1
[    1.703315] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfeb4d000
[    1.712325] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.712861] hub 1-0:1.0: USB hub found
[    1.712882] hub 1-0:1.0: 5 ports detected
[    1.713113] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.713200] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.713507] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.713577] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.713629] ehci_hcd 0000:00:13.2: debug port 1
[    1.713666] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfeb4b000
[    1.724297] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.724820] hub 2-0:1.0: USB hub found
[    1.724841] hub 2-0:1.0: 5 ports detected
[    1.725072] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.725162] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    1.725462] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.725531] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.725584] ehci_hcd 0000:00:16.2: debug port 1
[    1.725615] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfeb48000
[    1.736297] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.736820] hub 3-0:1.0: USB hub found
[    1.736841] hub 3-0:1.0: 4 ports detected
[    1.737039] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.737116] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.737204] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.737516] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.737634] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfeb4e000
[    1.796762] hub 4-0:1.0: USB hub found
[    1.796824] hub 4-0:1.0: 5 ports detected
[    1.797001] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.797090] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.797419] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.797517] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfeb4c000
[    1.856759] hub 5-0:1.0: USB hub found
[    1.856820] hub 5-0:1.0: 5 ports detected
[    1.857002] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.857093] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.857418] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    1.857516] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfeb4a000
[    1.916819] hub 6-0:1.0: USB hub found
[    1.916881] hub 6-0:1.0: 2 ports detected
[    1.917057] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.917146] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    1.917450] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    1.917552] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfeb49000
[    1.976818] hub 7-0:1.0: USB hub found
[    1.976880] hub 7-0:1.0: 4 ports detected
[    1.977019] uhci_hcd: USB Universal Host Controller Interface driver
[    1.977139] xhci_hcd 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.977229] xhci_hcd 0000:06:00.0: setting latency timer to 64
[    1.977236] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    1.977532] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 8
[    1.977957] xhci_hcd 0000:06:00.0: irq 18, io mem 0xfea00000
[    1.978053] xhci_hcd 0000:06:00.0: irq 40 for MSI/MSI-X
[    1.978504] xHCI xhci_add_endpoint called for root hub
[    1.978511] xHCI xhci_check_bandwidth called for root hub
[    1.978583] hub 8-0:1.0: USB hub found
[    1.978640] hub 8-0:1.0: 1 port detected
[    1.978763] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    1.979066] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 9
[    1.979549] xHCI xhci_add_endpoint called for root hub
[    1.979556] xHCI xhci_check_bandwidth called for root hub
[    1.979628] hub 9-0:1.0: USB hub found
[    1.979689] hub 9-0:1.0: 4 ports detected
[    1.996464] usbcore: registered new interface driver libusual
[    1.996546] i8042: PNP: PS/2 Controller [PNP0f03:PS2M] at 0x60,0x64 irq 12
[    1.996555] i8042: PNP: PS/2 controller doesn't have KBD irq; using default 1
[    1.997155] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.997172] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.997816] mousedev: PS/2 mouse device common for all mice
[    1.998807] rtc_cmos 00:05: RTC can wake from S4
[    1.999228] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.999289] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.999465] device-mapper: uevent: version 1.0.3
[    1.999832] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.999954] cpuidle: using governor ladder
[    2.000149] cpuidle: using governor menu
[    2.000156] EFI Variables Facility v0.08 2004-May-17
[    2.000581] TCP cubic registered
[    2.000786] NET: Registered protocol family 10
[    2.001633] NET: Registered protocol family 17
[    2.001645] Registering the dns_resolver key type
[    2.002647] PM: Hibernation image not present or could not be loaded.
[    2.002683] registered taskstats version 1
[    2.021976]   Magic number: 13:419:898
[    2.022201] rtc_cmos 00:05: setting system clock to 2013-01-16 18:53:42 UTC (1358362422)
[    2.022231] powernow-k8: Found 1 AMD E-350 Processor (2 cpu cores) (version 2.20.00)
[    2.022303] powernow-k8:    0 : pstate 0 (1600 MHz)
[    2.022311] powernow-k8:    1 : pstate 1 (1280 MHz)
[    2.022317] powernow-k8:    2 : pstate 2 (800 MHz)
[    2.023030] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.023045] EDD information not available.
[    2.192312] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.192370] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.192416] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.192449] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.193473] ata2.00: ATA-8: ST1500LM003-9YH148, CC94, max UDMA/133
[    2.193501] ata2.00: 2930277168 sectors, multi 16: LBA48 
[    2.194090] ata4.00: ATA-9: WDC WD30EFRX-68AX9N0, 80.00A80, max UDMA/133
[    2.194108] ata4.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.194188] ata3.00: ATA-9: WDC WD30EFRX-68AX9N0, 80.00A80, max UDMA/133
[    2.194206] ata3.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.195005] ata2.00: configured for UDMA/133
[    2.195064] ata4.00: configured for UDMA/133
[    2.195121] ata3.00: configured for UDMA/133
[    2.225614] ata1.00: ATA-9: SAMSUNG SSD 830 Series, CXM03B1Q, max UDMA/133
[    2.225632] ata1.00: 500118192 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.268825] ata1.00: configured for UDMA/133
[    2.269420] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SSD 830  CXM0 PQ: 0 ANSI: 5
[    2.269778] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.269899] sd 0:0:0:0: [sda] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[    2.270064] scsi 1:0:0:0: Direct-Access     ATA      ST1500LM003-9YH1 CC94 PQ: 0 ANSI: 5
[    2.270074] sd 0:0:0:0: [sda] Write Protect is off
[    2.270082] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.270127] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.270356] sd 1:0:0:0: [sdb] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    2.270369] sd 1:0:0:0: [sdb] 4096-byte physical blocks
[    2.270432] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.270661] scsi 2:0:0:0: Direct-Access     ATA      WDC WD30EFRX-68A 80.0 PQ: 0 ANSI: 5
[    2.270874] sd 1:0:0:0: [sdb] Write Protect is off
[    2.270884] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.270931] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.271056] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.271083] sd 2:0:0:0: [sdc] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.271106] sd 2:0:0:0: [sdc] 4096-byte physical blocks
[    2.271241] sd 2:0:0:0: [sdc] Write Protect is off
[    2.271251] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.271300] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.271311] scsi 3:0:0:0: Direct-Access     ATA      WDC WD30EFRX-68A 80.0 PQ: 0 ANSI: 5
[    2.271608] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    2.271717] sd 3:0:0:0: [sdd] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.271727] sd 3:0:0:0: [sdd] 4096-byte physical blocks
[    2.271836] sd 3:0:0:0: [sdd] Write Protect is off
[    2.271845] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.271891] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.279395]  sda: sda1 sda2
[    2.279980]  sdb: sdb1
[    2.280956] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.281727] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.288163] usb 8-1: new high-speed USB device number 2 using xhci_hcd
[    2.307494] hub 8-1:1.0: USB hub found
[    2.307965] hub 8-1:1.0: 4 ports detected
[    2.335069]  sdc: sdc1
[    2.335333]  sdd: sdd1
[    2.335708] sd 2:0:0:0: [sdc] Attached SCSI disk
[    2.335873] sd 3:0:0:0: [sdd] Attached SCSI disk
[    2.338931] Freeing unused kernel memory: 924k freed
[    2.339422] Write protecting the kernel read-only data: 12288k
[    2.349842] Freeing unused kernel memory: 1604k freed
[    2.358353] Freeing unused kernel memory: 1196k freed
[    2.406062] udevd[92]: starting version 175
[    2.476101] Refined TSC clocksource calibration: 1599.999 MHz.
[    2.476124] Switching to clocksource tsc
[    2.588160] usb 8-1.2: new low-speed USB device number 3 using xhci_hcd
[    2.606920] scsi4 : pata_atiixp
[    2.611694] scsi5 : pata_atiixp
[    2.614681] usb 8-1.2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.619926] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.619979] r8169 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.626332] ata5: PATA max UDMA/100 cmd 0xf140 ctl 0xf130 bmdma 0xf100 irq 17
[    2.626351] ata6: PATA max UDMA/100 cmd 0xf120 ctl 0xf110 bmdma 0xf108 irq 17
[    2.628686] r8169 0000:07:00.0: setting latency timer to 64
[    2.628777] r8169 0000:07:00.0: irq 41 for MSI/MSI-X
[    2.629582] r8169 0000:07:00.0: eth0: RTL8168e/8111e at 0xffffc90000c1a000, 00:01:2e:3c:15:52, XID 0c200000 IRQ 41
[    2.629601] r8169 0000:07:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.688730] usb 8-1.3: new low-speed USB device number 4 using xhci_hcd
[    2.754067] usb 8-1.3: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.754089] usb 8-1.3: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.777183] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:15.2/0000:06:00.0/usb8/8-1/8-1.3/8-1.3:1.0/input/input2
[    2.777769] generic-usb 0003:046D:C30E.0002: input,hidraw0: USB HID v1.10 Keyboard [Logitech HID compliant keyboard] on usb-0000:06:00.0-1.3/input0
[    2.792637] ata5.00: ATA-9: WDC WD30EFRX-68AX9N0, 80.00A80, max UDMA/133
[    2.792655] ata5.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.792669] ata5.00: limited to UDMA/33 due to 40-wire cable
[    2.801118] ata5.00: configured for UDMA/33
[    2.801670] scsi 4:0:0:0: Direct-Access     ATA      WDC WD30EFRX-68A 80.0 PQ: 0 ANSI: 5
[    2.802110] sd 4:0:0:0: [sde] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.802121] sd 4:0:0:0: [sde] 4096-byte physical blocks
[    2.802192] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    2.802319] sd 4:0:0:0: [sde] Write Protect is off
[    2.802341] sd 4:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    2.802535] sd 4:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.803421] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:15.2/0000:06:00.0/usb8/8-1/8-1.3/8-1.3:1.1/input/input3
[    2.803830] generic-usb 0003:046D:C30E.0003: input,hidraw1: USB HID v1.10 Device [Logitech HID compliant keyboard] on usb-0000:06:00.0-1.3/input1
[    2.803886] usbcore: registered new interface driver usbhid
[    2.803894] usbhid: USB HID core driver
[    2.874093]  sde: sde1
[    2.875074] sd 4:0:0:0: [sde] Attached SCSI disk
[    2.889409] input: Primax Electronics Apple Optical USB Mouse as /devices/pci0000:00/0000:00:15.2/0000:06:00.0/usb8/8-1/8-1.2/8-1.2:1.0/input/input4
[    2.890428] apple 0003:05AC:0304.0001: input,hidraw2: USB HID v1.10 Mouse [Primax Electronics Apple Optical USB Mouse] on usb-0000:06:00.0-1.2/input0
[    4.095782] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    7.348208] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.358244] udevd[493]: starting version 175
[    7.455068] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    7.455078] Disabling lock debugging due to kernel taint
[    7.461021] lp: driver loaded but no devices found
[    7.669236] [fglrx] Maximum main memory to use for locked dma buffers: 7362 MBytes.
[    7.669399] [fglrx]   vendor: 1002 device: 9802 count: 1
[    7.671399] [fglrx] ioport: bar 1, base 0xf000, size: 0x100
[    7.671425] pci 0000:00:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.671434] pci 0000:00:01.0: setting latency timer to 64
[    7.672689] [fglrx] Kernel PAT support is enabled
[    7.672733] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] with 1 minors
[    7.735561] EXT4-fs (sda1): re-mounted. Opts: discard,errors=remount-ro
[    7.778235] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    7.779210] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[    7.779386] SP5100 TCO timer: mmio address 0xbafe00 already in use
[    7.849702] snd_hda_intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    7.849866] snd_hda_intel 0000:00:01.1: irq 42 for MSI/MSI-X
[    7.849906] snd_hda_intel 0000:00:01.1: setting latency timer to 64
[    7.900189] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[    7.911133] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input5
[    7.911860] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.026767] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card1/input6
[    8.027042] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input7
[    8.027270] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input8
[    8.027490] input: HDA ATI SB Line-Out as /devices/pci0000:00/0000:00:14.2/sound/card1/input9
[    8.096773] type=1400 audit(1358362428.571:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=683 comm="apparmor_parser"
[    8.097776] type=1400 audit(1358362428.571:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=683 comm="apparmor_parser"
[    8.098175] type=1400 audit(1358362428.571:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=683 comm="apparmor_parser"
[    8.221322] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: discard
[    8.336635] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[    8.485671] EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: (null)
[    8.903728] r8169 0000:07:00.0: eth0: link down
[    8.903747] r8169 0000:07:00.0: eth0: link down
[    8.905477] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.432424] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    9.432432] vesafb: scrolling: redraw
[    9.432438] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    9.433045] vesafb: framebuffer at 0xb0000000, mapped to 0xffffc90011800000, using 1216k, total 1216k
[    9.437224] Console: switching to colour frame buffer device 80x30
[    9.438965] fb0: VESA VGA frame buffer device
[   10.870099] r8169 0000:07:00.0: eth0: link up
[   10.871754] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.024010] eth0: no IPv6 routers present
[   69.014601] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   69.098199] init: failsafe main process (1037) killed by TERM signal
[   69.222799] type=1400 audit(1358362489.105:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1115 comm="apparmor_parser"
[   69.223565] type=1400 audit(1358362489.105:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1115 comm="apparmor_parser"
[   69.223966] type=1400 audit(1358362489.105:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1115 comm="apparmor_parser"
[   69.226898] type=1400 audit(1358362489.109:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1114 comm="apparmor_parser"
[   69.232140] type=1400 audit(1358362489.117:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1117 comm="apparmor_parser"
[   71.572219] fglrx_pci 0000:00:01.0: irq 43 for MSI/MSI-X
[   71.573413] [fglrx] Firegl kernel thread PID: 1477
[   71.580090] [fglrx] Firegl kernel thread PID: 1478
[   71.584311] [fglrx] Firegl kernel thread PID: 1479
[   71.584539] [fglrx] IRQ 43 Enabled
[   71.835123] [fglrx] Gart USWC size:1280 M.
[   71.835131] [fglrx] Gart cacheable size:508 M.
[   71.835141] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   71.835146] [fglrx] Reserved FB block: Unshared offset:fbfd000, size:403000 
[   71.835150] [fglrx] Reserved FB block: Unshared offset:17ff4000, size:c000 
[   72.012168] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=0
[   72.012195] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   72.013693] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=1
[   72.013709] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   72.312157] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   72.612043] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   72.912039] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   73.212283] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   73.512280] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   73.812280] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   74.112094] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   74.412095] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   76.014678] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   76.014706] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   76.014874] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[   76.014891] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[   76.061338] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=0
[   76.061367] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   76.062846] HDMI hot plug event: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=1
[   76.062863] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   76.312061] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   76.612055] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   76.912080] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   77.212098] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   77.512071] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   77.629555] init: plymouth-stop pre-start process (2091) terminated with status 1
[   77.812084] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   78.112075] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
[   78.412076] HDMI status: Codec=0 Pin=3 Presence_Detect=1 ELD_Valid=1
```

---

### Post by tgalati4 on 2013-01-16
Do a search using "Samsung 830 SSD" and see if others are experiencing the same thing.  It could be a hardware issue.  Also, unplug the spinners and just leave the SSD plugged in and boot.  If you can't boot, then use a Live CD/DVD to boot and run tests with just the single SSD drive.

---

### Post by EuleLL on 2013-01-16
I've already checked the forums and the web ;-) but i will disconnect the other drives and will check if there is any improvement. The SSD is the root drive so booting without a LIVE CD will work...I will give an updated once I've done that...

---

### Post by EuleLL on 2013-01-16
I've disconnected all other drives - still the same result 17-25mb/s :-(

so this must be a kernel regression? or could it be anything else?

---

### Post by ahallubuntu on 2013-01-16
For fun, try booting a 12.10 live CD and check there to see how fast it is with a newer kernel.  Or, if you're worried about a kernel update having slowed it down, try a 12.04 live CD which will have an earlier kernel.

While you're fussing, try another SATA port on the board, for fun.

---

### Post by EuleLL on 2013-01-16
so back again - tried different SATA ports and cables a second time and ran tests (dd & hdparm) using the 12.04 and 12.10 live cd - unfortunately all with the same disappointing results...

could it be that there are some parameter of the ext4 partition set wrong? since it is not the OS thats the only thing I can think of besides a hardware damage...

btw: the drive is only 37% filled with data - so that can also not be the problem...

---

### Post by ahallubuntu on 2013-01-16
Are the partition(s) aligned?  I doubt that would matter for hdparm anyway - I assume it reads random sectors from the drive not from filesystems.  If you created the partition(s) using Ubuntu 11.04 or newer they should automatically be aligned, anyway.

---

### Post by EuleLL on 2013-01-16
yep - i used gparted and also already checked alignment with parted "align-check opt" command - so this should not be the problem - by now I have no idea what this could be...hope somebody has an idea.
I am currently creating an image of the disk from another computer via dd and then plan on formatting the disk to see if speed is back if i format it completely...however i hope i can restore the dd image afterwards :-)

---

### Post by serre on 2013-02-16
I have had the extremely slow reads and writes from a Samsung 830 SSD, under Ubuntu 12.04 LTS, with a 3.5 kernel.  The thing is I all ready had a working linux distro on this box before hand. So I knew it was not the hardware messing up.  After copying over the kernel( 3.6.6 main line), the SSD work fine under Ubuntu.

---

### Post by EuleLL on 2013-02-18
hey there,

i my case it was definitely a hardware error - had the ssd sent in to samsung service and after it came back and performed significantly better - i get now on avg 200mb+ speeds read and write. I was and am now running 3.2.0-35-generic kernel.

cheers

---

### Post by Hreinsi on 2013-02-18
My 830 120 gb says.

/dev/sdb:
 Timing cached reads:   4756 MB in  2.00 seconds = 2377.74 MB/sec
 Timing buffered disk reads: 760 MB in  3.00 seconds = 253.23 MB/sec
 
Using Trim. [http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

---

### Post by EuleLL on 2013-02-18
similar here (well now :-)):
------------------------------
--- Simple hdd speed test  ---
---  by Julius Beckmann    ---
------------------------------
[Info] Performing WRITE test
4194304000 bytes (4.2 GB) copied, 14.7385 s, 285 MB/s
[Info] Finished WRITE test
------------------------------
[Clearing Cache]
3
------------------------------
[Info] Performing unbuffered READ test
4194304000 bytes (4.2 GB) copied, 15.765 s, 266 MB/s
[Info] Finished unbuffered READ test
------------------------------
[Info] Performing buffered READ test
4194304000 bytes (4.2 GB) copied, 13.1346 s, 319 MB/s
[Info] Finished buffered READ test
------------------------------
[Info] Removing tmp file
------------------------------


however buffered read is slower - dont know why but actually dont care :-)

---

