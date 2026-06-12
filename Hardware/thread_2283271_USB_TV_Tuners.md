---
title: "USB TV Tuners"
date: 2015-06-20
forum: Hardware
---

### Post by colonelpenguin on 2015-06-20
I have been dealing with a problem literally for years and am wondering if anyone can please help guide me down a path to a resolution.  I have three HVR-850 usb tuners attached to my computer running mythbuntu.  I have even tried different distributions and the same problem has persisted.  

After every reboot, all three devices are recognized only about 5 percent of the time.  Usually only one or two of them are functioning properly.  To fix the problem, I am required to unplug and replug the devices to make everything work.  At times I do not have physical access to the machine, and this is a very big problem for me.

I really really want to get this problem solved, but I am not sure where to start.  I know that these tuners have been released with different chips and mine seem to use cx231xx.  lsusb identifies them as "2040:b140 Hauppauge"

I am willing to try just about anything to get this resolved, but I just don't know where to get started.

---

### Post by TheFu on 2015-06-20
I had a 950Q that never quite worked. It was frustrating.

Switched to a pair of network tuners - HD-Homerun - and I've never looked back. They just work for the last 2-3 yrs and the newer versions have DLNA that any DLNA client on the network can access. That means liveTV on your Android devices, for example.

The HDHR tuners are extremely good. No USB in the way.  Basically, they sit on the network and I completely forget them for years at a time. Can't recall having to reboot them EVER. Extremely stable.

---

### Post by VMC on 2015-06-21
> **TheFu said:**
> I had a 950Q that never quite worked. It was frustrating.

Switched to a pair of network tuners - HD-Homerun - and I've never looked back. They just work for the last 2-3 yrs and the newer versions have DLNA that any DLNA client on the network can access. That means liveTV on your Android devices, for example.

The HDHR tuners are extremely good. No USB in the way.  Basically, they sit on the network and I completely forget them for years.

I have the 950q also, and never got it to work. I have never heard complaints about the HDHR.

---

### Post by Bucky Ball on 2015-06-21
Welcome. Does it work consistently when you only have one of the devices plugged in? Try it.

Just out of curiousity, why are you running three TV dongles on one machine? :-k

---

### Post by colonelpenguin on 2015-06-22
I can check again to see if it is stable with only one tuner... I think it will be, but I will try to check and report back.  

The reason I have three tuners is to be able to record up to three different television stations at the same time.

---

### Post by Bucky Ball on 2015-06-23
Are they all the same make/model?

Because every now and then all three drivers are recognised, I'm wondering if the driver is taking a lucky dip and allocating the first one it finds on other occasions, therefore negating the possibility the other two are going to get a look in. 

As it is working sometimes, there must be a chance of forcing the issue and getting the driver to pick up all three at boot.

To try and get some clues, perhaps boot with one in, make sure that's working, plug in another, open a terminal immediately, run:

```
dmesg
```

... and check the last part of the output. What does it say there about the device you've plugged and is it loading a driver for it? If all good, plug the next in and repeat the process. We might find some clues where, and if, this process falls over. If all three work with this one-by-one method we have a workaround at least, if not a solution or explanation of what's happening quite yet.

---

### Post by colonelpenguin on 2015-06-28
I do believe they are all the exact same device.  I have done some more testing over the week.  I have noticed a few things and listed them below.  I really need these to be recognized reliably on boot up.

1) I can't get even one tuner to initialize on boot 100% of the time with the other two disconnected.

2) Which devices are recognized during boot up is random if they are all plugged in during boot up.

3) As stated before, the devices always load properly if they are plugged in after booting up.


I looked for a way to make this easier to read, but I couldn't find much so I will be pasting several dmesg outputs below:

1 Tuner was plugged in and was not recognized after boot:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-55-generic (buildd@brownie) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #94-Ubuntu SMP Thu Jun 18 00:27:10 UTC 2015 (Ubuntu 3.13.0-55.94-generic 3.13.11-ckt20)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-55-generic root=UUID=dfea8c42-85ad-4d85-9a60-70d7bfd61c3e ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cfe7ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cfe80000-0x00000000cfe97fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cfe98000-0x00000000cfebffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cfec0000-0x00000000cfefffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000022fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: System manufacturer System Product Name/M5A78L-M LX, BIOS 0510    08/15/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x230000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000230000000 aka 8960M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcfe80 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x22fe00000-0x22fffffff]
[    0.000000]  [mem 0x22fe00000-0x22fffffff] page 2M
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x22c000000-0x22fdfffff]
[    0.000000]  [mem 0x22c000000-0x22fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x22bffffff]
[    0.000000]  [mem 0x200000000-0x22bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xcfe7ffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xcfdfffff] page 2M
[    0.000000]  [mem 0xcfe00000-0xcfe7ffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35b46000-0x36d9afff]
[    0.000000] ACPI: RSDP 00000000000fb490 000024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000cfe80100 000054 (v01 081511 XSDT0945 20110815 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cfe80290 0000F4 (v03 081511 FACP0945 20110815 MSFT 00000097)
[    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20131115/tbfadt-603)
[    0.000000] ACPI: DSDT 00000000cfe80460 00D6D6 (v01  A1860 A1860001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cfe98000 000040
[    0.000000] ACPI: APIC 00000000cfe80390 00008C (v01 081511 APIC0945 20110815 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cfe80420 00003C (v01 081511 OEMMCFG  20110815 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cfe98040 000072 (v01 081511 OEMB0945 20110815 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cfe8f460 000038 (v01 081511 OEMHPET  20110815 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cfe8f4a0 0008BC (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000022fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x22fffffff]
[    0.000000]   NODE_DATA [mem 0x22fff9000-0x22fffdfff]
[    0.000000]  [ffffea0000000000-ffffea0008bfffff] PMD -> [ffff880227600000-ffff88022f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x22fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xcfe7ffff]
[    0.000000]   node   0: [mem 0x100000000-0x22fffffff]
[    0.000000] On node 0 totalpages: 2096670
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13242 pages used for memmap
[    0.000000]   DMA32 zone: 847488 pages, LIFO batch:31
[    0.000000]   Normal zone: 19456 pages used for memmap
[    0.000000]   Normal zone: 1245184 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e4000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcfe80000-0xcfe97fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcfe98000-0xcfebffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcfec0000-0xcfefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcff00000-0xffdfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
[    0.000000] e820: [mem 0xcff00000-0xffdfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88022fc00000 s81536 r8192 d20864 u262144
[    0.000000] pcpu-alloc: s81536 r8192 d20864 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2063887
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-55-generic root=UUID=dfea8c42-85ad-4d85-9a60-70d7bfd61c3e ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 0 size 32 MB
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: [mem 0xc4000000-0xc7ffffff]
[    0.000000] Memory: 8087736K/8386680K available (7392K kernel code, 1146K rwdata, 3408K rodata, 1336K init, 1448K bss, 298944K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2812.848 MHz processor
[    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5625.69 BogoMIPS (lpj=11251392)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000035] Security Framework initialized
[    0.000055] AppArmor: AppArmor initialized
[    0.000056] Yama: becoming mindful.
[    0.000558] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002812] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003869] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.003879] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.004126] Initializing cgroup subsys memory
[    0.004132] Initializing cgroup subsys devices
[    0.004134] Initializing cgroup subsys freezer
[    0.004135] Initializing cgroup subsys blkio
[    0.004136] Initializing cgroup subsys perf_event
[    0.004139] Initializing cgroup subsys hugetlb
[    0.004156] tseg: 0000000000
[    0.004162] CPU: Physical Processor ID: 0
[    0.004163] CPU: Processor Core ID: 0
[    0.004165] mce: CPU supports 6 MCE banks
[    0.004170] LVT offset 0 assigned for vector 0xf9
[    0.004176] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
[    0.004176] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64
[    0.004176] tlb_flushall_shift: 4
[    0.004262] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
[    0.004999] ACPI: Core revision 20131115
[    0.008388] ACPI: All ACPI Tables successfully acquired
[    0.015677] ftrace: allocating 28579 entries in 112 pages
[    0.027196] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066880] smpboot: CPU0: AMD Phenom(tm) II X4 830 Processor (fam: 10, model: 04, stepping: 03)
[    0.171132] Performance Events: AMD PMU driver.
[    0.171135] ... version:                0
[    0.171136] ... bit width:              48
[    0.171137] ... generic registers:      4
[    0.171138] ... value mask:             0000ffffffffffff
[    0.171139] ... max period:             00007fffffffffff
[    0.171140] ... fixed-purpose events:   0
[    0.171141] ... event mask:             000000000000000f
[    0.172624] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.172690] x86: Booting SMP configuration:
[    0.172691] .... node  #0, CPUs:      #1 #2 #3
[    0.211932] x86: Booted up 1 node, 4 CPUs
[    0.211935] smpboot: Total of 4 processors activated (22502.78 BogoMIPS)
[    0.216697] devtmpfs: initialized
[    0.220503] EVM: security.selinux
[    0.220504] EVM: security.SMACK64
[    0.220505] EVM: security.ima
[    0.220506] EVM: security.capability
[    0.220589] PM: Registering ACPI NVS region [mem 0xcfe98000-0xcfebffff] (163840 bytes)
[    0.221496] pinctrl core: initialized pinctrl subsystem
[    0.221553] regulator-dummy: no parameters
[    0.221580] RTC time:  2:22:53, date: 06/29/15
[    0.221615] NET: Registered protocol family 16
[    0.221711] cpuidle: using governor ladder
[    0.221713] cpuidle: using governor menu
[    0.221717] node 0 link 0: io port [1000, ffffff]
[    0.221723] TOM: 00000000d0000000 aka 3328M
[    0.221726] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
[    0.221728] node 0 link 0: mmio [a0000, bffff]
[    0.221730] node 0 link 0: mmio [d0000000, dfffffff]
[    0.221732] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.221733] node 0 link 0: mmio [f0000000, ffdfffff]
[    0.221735] TOM2: 0000000230000000 aka 8960M
[    0.221736] bus: [bus 00-1f] on node 0 link 0
[    0.221737] bus: 00 [io  0x0000-0xffff]
[    0.221739] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.221740] bus: 00 [mem 0xd0000000-0xdfffffff]
[    0.221741] bus: 00 [mem 0xf0000000-0xffffffff]
[    0.221742] bus: 00 [mem 0x230000000-0xfcffffffff]
[    0.221789] ACPI: bus type PCI registered
[    0.221791] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.221844] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.221847] PCI: not using MMCONFIG
[    0.221848] PCI: Using configuration type 1 for base access
[    0.221849] PCI: Using configuration type 1 for extended access
[    0.222022] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.222023] mtrr: probably your BIOS does not setup all CPUs.
[    0.222024] mtrr: corrected configuration.
[    0.222805] bio: create slab <bio-0> at 0
[    0.222960] ACPI: Added _OSI(Module Device)
[    0.222961] ACPI: Added _OSI(Processor Device)
[    0.222962] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.222963] ACPI: Added _OSI(Processor Aggregator Device)
[    0.225330] ACPI: Executed 3 blocks of module-level executable AML code
[    0.299562] ACPI: Interpreter enabled
[    0.299574] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.299587] ACPI: (supports S0 S1 S3 S4 S5)
[    0.299589] ACPI: Using IOAPIC for interrupt routing
[    0.299606] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.300718] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.308963] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.309051] ACPI: No dock devices found.
[    0.360038] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.360044] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.360048] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.360308] PCI host bridge to bus 0000:00
[    0.360310] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.360312] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.360314] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.360316] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.360317] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.360319] pci_bus 0000:00: root bus resource [mem 0xcff00000-0xdfffffff]
[    0.360320] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
[    0.360330] pci 0000:00:00.0: [1022:9600] type 00 class 0x060000
[    0.360417] pci 0000:00:02.0: [1022:9603] type 01 class 0x060400
[    0.360446] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.360482] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.360507] pci 0000:00:04.0: [1022:9604] type 01 class 0x060400
[    0.360535] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.360569] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.360612] pci 0000:00:11.0: [1002:4390] type 00 class 0x01018f
[    0.360630] pci 0000:00:11.0: reg 0x10: [io  0xc000-0xc007]
[    0.360640] pci 0000:00:11.0: reg 0x14: [io  0xb000-0xb003]
[    0.360648] pci 0000:00:11.0: reg 0x18: [io  0xa000-0xa007]
[    0.360657] pci 0000:00:11.0: reg 0x1c: [io  0x9000-0x9003]
[    0.360666] pci 0000:00:11.0: reg 0x20: [io  0x8000-0x800f]
[    0.360675] pci 0000:00:11.0: reg 0x24: [mem 0xfcfffc00-0xfcffffff]
[    0.360694] pci 0000:00:11.0: set SATA to AHCI mode
[    0.360778] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.360791] pci 0000:00:12.0: reg 0x10: [mem 0xfcffe000-0xfcffefff]
[    0.360874] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.360902] pci 0000:00:12.1: [1002:4398] type 00 class 0x0c0310
[    0.360914] pci 0000:00:12.1: reg 0x10: [mem 0xfcffd000-0xfcffdfff]
[    0.360998] pci 0000:00:12.1: System wakeup disabled by ACPI
[    0.361026] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.361044] pci 0000:00:12.2: reg 0x10: [mem 0xfcfff800-0xfcfff8ff]
[    0.361123] pci 0000:00:12.2: supports D1 D2
[    0.361125] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.361162] pci 0000:00:12.2: System wakeup disabled by ACPI
[    0.361190] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.361203] pci 0000:00:13.0: reg 0x10: [mem 0xfcffc000-0xfcffcfff]
[    0.361285] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.361309] pci 0000:00:13.1: [1002:4398] type 00 class 0x0c0310
[    0.361321] pci 0000:00:13.1: reg 0x10: [mem 0xfcffb000-0xfcffbfff]
[    0.361404] pci 0000:00:13.1: System wakeup disabled by ACPI
[    0.361432] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.361450] pci 0000:00:13.2: reg 0x10: [mem 0xfcfff400-0xfcfff4ff]
[    0.361529] pci 0000:00:13.2: supports D1 D2
[    0.361530] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.361567] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.361600] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.361733] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
[    0.361749] pci 0000:00:14.1: reg 0x10: [io  0x0000-0x0007]
[    0.361758] pci 0000:00:14.1: reg 0x14: [io  0x0000-0x0003]
[    0.361767] pci 0000:00:14.1: reg 0x18: [io  0x0000-0x0007]
[    0.361775] pci 0000:00:14.1: reg 0x1c: [io  0x0000-0x0003]
[    0.361784] pci 0000:00:14.1: reg 0x20: [io  0xff00-0xff0f]
[    0.361876] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.361988] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.362051] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.362074] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.362087] pci 0000:00:14.5: reg 0x10: [mem 0xfcffa000-0xfcffafff]
[    0.362170] pci 0000:00:14.5: System wakeup disabled by ACPI
[    0.362198] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
[    0.362250] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
[    0.362300] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
[    0.362349] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
[    0.362400] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
[    0.362491] pci 0000:01:00.0: [10de:0de1] type 00 class 0x030000
[    0.362500] pci 0000:01:00.0: reg 0x10: [mem 0xfd000000-0xfdffffff]
[    0.362510] pci 0000:01:00.0: reg 0x14: [mem 0xd8000000-0xdfffffff 64bit pref]
[    0.362519] pci 0000:01:00.0: reg 0x1c: [mem 0xd6000000-0xd7ffffff 64bit pref]
[    0.362526] pci 0000:01:00.0: reg 0x24: [io  0xdc00-0xdc7f]
[    0.362532] pci 0000:01:00.0: reg 0x30: [mem 0xfeb00000-0xfeb7ffff pref]
[    0.362598] pci 0000:01:00.1: [10de:0bea] type 00 class 0x040300
[    0.362607] pci 0000:01:00.1: reg 0x10: [mem 0xfebf8000-0xfebfbfff]
[    0.367107] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.367112] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.367115] pci 0000:00:02.0:   bridge window [mem 0xfd000000-0xfebfffff]
[    0.367118] pci 0000:00:02.0:   bridge window [mem 0xd6000000-0xdfffffff 64bit pref]
[    0.367178] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
[    0.367191] pci 0000:02:00.0: reg 0x10: [io  0xe800-0xe8ff]
[    0.367211] pci 0000:02:00.0: reg 0x18: [mem 0xf7fff000-0xf7ffffff 64bit pref]
[    0.367223] pci 0000:02:00.0: reg 0x20: [mem 0xf7ff8000-0xf7ffbfff 64bit pref]
[    0.367275] pci 0000:02:00.0: supports D1 D2
[    0.367276] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.367304] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.375111] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.375116] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.375119] pci 0000:00:04.0:   bridge window [mem 0xf7f00000-0xf7ffffff 64bit pref]
[    0.375166] pci 0000:03:05.0: [4444:0016] type 00 class 0x040000
[    0.375188] pci 0000:03:05.0: reg 0x10: [mem 0xf8000000-0xfbffffff pref]
[    0.375349] pci 0000:00:14.4: PCI bridge to [bus 03] (subtractive decode)
[    0.375357] pci 0000:00:14.4:   bridge window [mem 0xf8000000-0xfbffffff pref]
[    0.375359] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.375360] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.375362] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.375364] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.375365] pci 0000:00:14.4:   bridge window [mem 0xcff00000-0xdfffffff] (subtractive decode)
[    0.375367] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.391168] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 12 14 15)
[    0.391206] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
[    0.391241] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.391273] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.391306] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 *10 11 12 14 15)
[    0.391339] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.391372] ACPI: PCI Interrupt Link [LNKG] (IRQs *11)
[    0.391404] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.391550] ACPI: Enabled 1 GPEs in block 00 to 1F
[    0.391556] ACPI: \_SB_.PCI0: notify handler is installed
[    0.391588] Found 1 acpi root devices
[    0.391678] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.391680] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.391681] vgaarb: loaded
[    0.391682] vgaarb: bridge control possible 0000:01:00.0
[    0.391827] SCSI subsystem initialized
[    0.391889] libata version 3.00 loaded.
[    0.391907] ACPI: bus type USB registered
[    0.391920] usbcore: registered new interface driver usbfs
[    0.391927] usbcore: registered new interface driver hub
[    0.391948] usbcore: registered new device driver usb
[    0.392055] PCI: Using ACPI for IRQ routing
[    0.400409] PCI: pci_cache_line_size set to 64 bytes
[    0.400458] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.400460] e820: reserve RAM buffer [mem 0xcfe80000-0xcfffffff]
[    0.400528] NetLabel: Initializing
[    0.400530] NetLabel:  domain hash size = 128
[    0.400530] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.400540] NetLabel:  unlabeled traffic allowed by default
[    0.400600] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.400603] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.402662] Switched to clocksource hpet
[    0.406854] AppArmor: AppArmor Filesystem Enabled
[    0.406875] pnp: PnP ACPI init
[    0.406885] ACPI: bus type PNP registered
[    0.407002] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.407034] pnp 00:01: [dma 4]
[    0.407050] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.407078] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.407094] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.407115] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.407550] pnp 00:05: [dma 0 disabled]
[    0.407700] pnp 00:05: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.407741] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.408064] pnp 00:07: [dma 0 disabled]
[    0.408124] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.408202] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.408204] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.408206] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.408387] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.408389] system 00:09: [io  0x040b] has been reserved
[    0.408390] system 00:09: [io  0x04d6] has been reserved
[    0.408392] system 00:09: [io  0x0c00-0x0c01] has been reserved
[    0.408394] system 00:09: [io  0x0c14] has been reserved
[    0.408396] system 00:09: [io  0x0c50-0x0c51] has been reserved
[    0.408398] system 00:09: [io  0x0c52] has been reserved
[    0.408399] system 00:09: [io  0x0c6c] has been reserved
[    0.408401] system 00:09: [io  0x0c6f] has been reserved
[    0.408403] system 00:09: [io  0x0cd0-0x0cd1] has been reserved
[    0.408405] system 00:09: [io  0x0cd2-0x0cd3] has been reserved
[    0.408407] system 00:09: [io  0x0cd4-0x0cd5] has been reserved
[    0.408409] system 00:09: [io  0x0cd6-0x0cd7] has been reserved
[    0.408410] system 00:09: [io  0x0cd8-0x0cdf] has been reserved
[    0.408412] system 00:09: [io  0x0b00-0x0b3f] has been reserved
[    0.408414] system 00:09: [io  0x0800-0x089f] could not be reserved
[    0.408416] system 00:09: [io  0x0b00-0x0b0f] has been reserved
[    0.408418] system 00:09: [io  0x0b20-0x0b3f] has been reserved
[    0.408420] system 00:09: [io  0x0900-0x090f] has been reserved
[    0.408421] system 00:09: [io  0x0910-0x091f] has been reserved
[    0.408423] system 00:09: [io  0xfe00-0xfefe] has been reserved
[    0.408426] system 00:09: [mem 0xcff00000-0xcfffffff] has been reserved
[    0.408428] system 00:09: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.408429] system 00:09: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.408431] system 00:09: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.408433] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.408567] system 00:0a: [io  0x0230-0x023f] has been reserved
[    0.408569] system 00:0a: [io  0x0290-0x029f] has been reserved
[    0.408571] system 00:0a: [io  0x0300-0x030f] has been reserved
[    0.408572] system 00:0a: [io  0x0a30-0x0a3f] has been reserved
[    0.408574] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.408618] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.408620] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.422830] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.422833] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.422835] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.422837] system 00:0c: [mem 0x00100000-0xcfefffff] could not be reserved
[    0.422839] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.422842] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.422920] pnp: PnP ACPI: found 13 devices
[    0.422922] ACPI: bus type PNP unregistered
[    0.429130] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.429133] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.429136] pci 0000:00:02.0:   bridge window [mem 0xfd000000-0xfebfffff]
[    0.429138] pci 0000:00:02.0:   bridge window [mem 0xd6000000-0xdfffffff 64bit pref]
[    0.429141] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.429143] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.429147] pci 0000:00:04.0:   bridge window [mem 0xf7f00000-0xf7ffffff 64bit pref]
[    0.429150] pci 0000:00:14.4: PCI bridge to [bus 03]
[    0.429156] pci 0000:00:14.4:   bridge window [mem 0xf8000000-0xfbffffff pref]
[    0.429163] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.429164] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.429166] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.429167] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.429169] pci_bus 0000:00: resource 8 [mem 0xcff00000-0xdfffffff]
[    0.429171] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.429172] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.429174] pci_bus 0000:01: resource 1 [mem 0xfd000000-0xfebfffff]
[    0.429176] pci_bus 0000:01: resource 2 [mem 0xd6000000-0xdfffffff 64bit pref]
[    0.429177] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.429179] pci_bus 0000:02: resource 2 [mem 0xf7f00000-0xf7ffffff 64bit pref]
[    0.429181] pci_bus 0000:03: resource 2 [mem 0xf8000000-0xfbffffff pref]
[    0.429183] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.429184] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.429186] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.429187] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.429189] pci_bus 0000:03: resource 8 [mem 0xcff00000-0xdfffffff]
[    0.429190] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.429218] NET: Registered protocol family 2
[    0.429437] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.429625] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.429897] TCP: Hash tables configured (established 65536 bind 65536)
[    0.429936] TCP: reno registered
[    0.429947] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.429995] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.430090] NET: Registered protocol family 1
[    0.854700] pci 0000:01:00.0: Video device with shadowed ROM
[    0.854715] PCI: CLS 64 bytes, default 64
[    0.854771] Trying to unpack rootfs image as initramfs...
[    1.138111] Freeing initrd memory: 18772K (ffff880035b46000 - ffff880036d9b000)
[    1.138346] PCI-DMA: Disabling AGP.
[    1.138431] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.138432] PCI-DMA: using GART IOMMU.
[    1.138435] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.141734] LVT offset 1 assigned for vector 0x400
[    1.141742] IBS: LVT offset 1 assigned
[    1.141767] perf: AMD IBS detected (0x0000001f)
[    1.141805] microcode: CPU0: patch_level=0x010000c8
[    1.141812] microcode: CPU1: patch_level=0x010000c8
[    1.141823] microcode: CPU2: patch_level=0x010000c8
[    1.141833] microcode: CPU3: patch_level=0x010000c8
[    1.141922] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.141925] Scanning for low memory corruption every 60 seconds
[    1.142156] Initialise system trusted keyring
[    1.142210] audit: initializing netlink socket (disabled)
[    1.142220] type=2000 audit(1435544573.028:1): initialized
[    1.168152] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.169371] zbud: loaded
[    1.169513] VFS: Disk quotas dquot_6.5.2
[    1.169551] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.169979] fuse init (API version 7.22)
[    1.170042] msgmni has been set to 15961
[    1.170090] Key type big_key registered
[    1.170597] Key type asymmetric registered
[    1.170600] Asymmetric key parser 'x509' registered
[    1.170653] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.170702] io scheduler noop registered
[    1.170704] io scheduler deadline registered (default)
[    1.170727] io scheduler cfq registered
[    1.170916] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.171025] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
[    1.171068] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.171079] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.171118] ipmi message handler version 39.2
[    1.171174] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.171178] ACPI: Power Button [PWRB]
[    1.171204] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.171206] ACPI: Power Button [PWRF]
[    1.172041] GHES: HEST is not enabled!
[    1.172120] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.192582] 00:07: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.193728] Linux agpgart interface v0.103
[    1.194885] brd: module loaded
[    1.195500] loop: module loaded
[    1.195808] libphy: Fixed MDIO Bus: probed
[    1.195879] tun: Universal TUN/TAP device driver, 1.6
[    1.195880] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.195911] PPP generic driver version 2.4.2
[    1.195946] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.195948] ehci-pci: EHCI PCI platform driver
[    1.196062] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.196067] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.196070] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.196081] ehci-pci 0000:00:12.2: debug port 1
[    1.196121] ehci-pci 0000:00:12.2: irq 17, io mem 0xfcfff800
[    1.206541] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.206586] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.206588] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.206589] usb usb1: Product: EHCI Host Controller
[    1.206591] usb usb1: Manufacturer: Linux 3.13.0-55-generic ehci_hcd
[    1.206592] usb usb1: SerialNumber: 0000:00:12.2
[    1.206700] hub 1-0:1.0: USB hub found
[    1.206707] hub 1-0:1.0: 6 ports detected
[    1.206919] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.206924] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.206927] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.206938] ehci-pci 0000:00:13.2: debug port 1
[    1.206975] ehci-pci 0000:00:13.2: irq 19, io mem 0xfcfff400
[    1.218527] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.218564] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.218566] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.218567] usb usb2: Product: EHCI Host Controller
[    1.218569] usb usb2: Manufacturer: Linux 3.13.0-55-generic ehci_hcd
[    1.218570] usb usb2: SerialNumber: 0000:00:13.2
[    1.218688] hub 2-0:1.0: USB hub found
[    1.218694] hub 2-0:1.0: 6 ports detected
[    1.218794] ehci-platform: EHCI generic platform driver
[    1.218800] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.218802] ohci-pci: OHCI PCI platform driver
[    1.218904] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.218909] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.218932] ohci-pci 0000:00:12.0: irq 16, io mem 0xfcffe000
[    1.278521] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.278524] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.278526] usb usb3: Product: OHCI PCI host controller
[    1.278527] usb usb3: Manufacturer: Linux 3.13.0-55-generic ohci_hcd
[    1.278528] usb usb3: SerialNumber: 0000:00:12.0
[    1.278635] hub 3-0:1.0: USB hub found
[    1.278642] hub 3-0:1.0: 3 ports detected
[    1.278794] ohci-pci 0000:00:12.1: OHCI PCI host controller
[    1.278799] ohci-pci 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.278811] ohci-pci 0000:00:12.1: irq 16, io mem 0xfcffd000
[    1.338504] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.338507] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.338508] usb usb4: Product: OHCI PCI host controller
[    1.338510] usb usb4: Manufacturer: Linux 3.13.0-55-generic ohci_hcd
[    1.338511] usb usb4: SerialNumber: 0000:00:12.1
[    1.338614] hub 4-0:1.0: USB hub found
[    1.338621] hub 4-0:1.0: 3 ports detected
[    1.338771] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.338776] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.338796] ohci-pci 0000:00:13.0: irq 18, io mem 0xfcffc000
[    1.398492] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.398494] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.398496] usb usb5: Product: OHCI PCI host controller
[    1.398497] usb usb5: Manufacturer: Linux 3.13.0-55-generic ohci_hcd
[    1.398498] usb usb5: SerialNumber: 0000:00:13.0
[    1.398601] hub 5-0:1.0: USB hub found
[    1.398610] hub 5-0:1.0: 3 ports detected
[    1.398759] ohci-pci 0000:00:13.1: OHCI PCI host controller
[    1.398763] ohci-pci 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.398776] ohci-pci 0000:00:13.1: irq 18, io mem 0xfcffb000
[    1.458482] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.458484] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.458486] usb usb6: Product: OHCI PCI host controller
[    1.458487] usb usb6: Manufacturer: Linux 3.13.0-55-generic ohci_hcd
[    1.458489] usb usb6: SerialNumber: 0000:00:13.1
[    1.458592] hub 6-0:1.0: USB hub found
[    1.458599] hub 6-0:1.0: 3 ports detected
[    1.458756] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    1.458760] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.458772] ohci-pci 0000:00:14.5: irq 18, io mem 0xfcffa000
[    1.518480] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.518483] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.518484] usb usb7: Product: OHCI PCI host controller
[    1.518486] usb usb7: Manufacturer: Linux 3.13.0-55-generic ohci_hcd
[    1.518489] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.518490] usb usb7: SerialNumber: 0000:00:14.5
[    1.518581] hub 7-0:1.0: USB hub found
[    1.518589] hub 7-0:1.0: 2 ports detected
[    1.518644] ohci-platform: OHCI generic platform driver
[    1.518652] uhci_hcd: USB Universal Host Controller Interface driver
[    1.518696] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.519063] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.519069] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.519158] mousedev: PS/2 mouse device common for all mice
[    1.519266] rtc_cmos 00:02: RTC can wake from S4
[    1.519364] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.519387] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.519443] device-mapper: uevent: version 1.0.3
[    1.519492] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.519498] ledtrig-cpu: registered to indicate activity on CPUs
[    1.519583] TCP: cubic registered
[    1.519643] NET: Registered protocol family 10
[    1.519779] NET: Registered protocol family 17
[    1.519786] Key type dns_resolver registered
[    1.520014] Loading compiled-in X.509 certificates
[    1.520988] Loaded X.509 cert 'Magrathea: Glacier signing key: 13dfa511f14d8706c6ace27e0c6a7d1469b9ea7f'
[    1.520995] registered taskstats version 1
[    1.523133] Key type trusted registered
[    1.526094] Key type encrypted registered
[    1.526098] AppArmor: AppArmor sha1 policy hashing enabled
[    1.526100] IMA: No TPM chip found, activating TPM-bypass!
[    1.526310] regulator-dummy: disabling
[    1.526354]   Magic number: 3:212:360
[    1.526438] rtc_cmos 00:02: setting system clock to 2015-06-29 02:22:54 UTC (1435544574)
[    1.526541] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.526924] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.526925] EDD information not available.
[    1.526944] PM: Hibernation image not present or could not be loaded.
[    1.528522] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    1.528524] Write protecting the kernel read-only data: 12288k
[    1.530613] Freeing unused kernel memory: 788K (ffff88000173b000 - ffff880001800000)
[    1.532335] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
[    1.542682] systemd-udevd[121]: starting version 204
[    1.559531] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.559544] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.559800] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.559981] r8169 0000:02:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000c64000, 54:04:a6:82:07:03, XID 0c900800 IRQ 42
[    1.559983] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.560214] scsi0 : pata_atiixp
[    1.560287] scsi1 : pata_atiixp
[    1.560337] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.560339] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.560370] ahci 0000:00:11.0: version 3.0
[    1.560555] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.560557] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.561064] scsi2 : ahci
[    1.561288] scsi3 : ahci
[    1.561345] scsi4 : ahci
[    1.561405] scsi5 : ahci
[    1.561450] ata3: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffd00 irq 22
[    1.561453] ata4: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffd80 irq 22
[    1.561455] ata5: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffe00 irq 22
[    1.561458] ata6: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffe80 irq 22
[    1.653360] usb 1-1: New USB device found, idVendor=2040, idProduct=b140
[    1.653364] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.653367] usb 1-1: Product: Hauppauge Device
[    1.653368] usb 1-1: Manufacturer: Hauppauge
[    1.653370] usb 1-1: SerialNumber: 4034729194
[    1.730969] ata2.00: ATA-9: ST3000DM001-1ER166, CC25, max UDMA/133
[    1.730972] ata2.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.730979] ata2.01: ATAPI: TSSTcorp CDDVDW SH-222AB, SB00, max UDMA/100
[    1.746954] ata2.00: configured for UDMA/100
[    1.762742] ata2.01: configured for UDMA/100
[    1.763235] scsi 1:0:0:0: Direct-Access     ATA      ST3000DM001-1ER1 CC25 PQ: 0 ANSI: 5
[    1.763366] sd 1:0:0:0: [sda] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    1.763369] sd 1:0:0:0: [sda] 4096-byte physical blocks
[    1.763388] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.763800] sd 1:0:0:0: [sda] Write Protect is off
[    1.763804] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.764104] scsi 1:0:1:0: CD-ROM            TSSTcorp CDDVDW SH-222AB  SB00 PQ: 0 ANSI: 5
[    1.764129] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.766747] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.766750] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.766853] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    1.766966] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    1.770444] usb 1-2: new high-speed USB device number 3 using ehci-pci
[    1.829712]  sda: sda1
[    1.830023] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.936489] usb 1-2: New USB device found, idVendor=1058, idProduct=1230
[    1.936492] usb 1-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[    1.936493] usb 1-2: Product: My Book 1230
[    1.936494] usb 1-2: Manufacturer: Western Digital
[    1.936496] usb 1-2: SerialNumber: 5743433445364C5658553133
[    1.939981] usb-storage 1-2:1.0: USB Mass Storage device detected
[    1.940051] scsi6 : usb-storage 1-2:1.0
[    1.940099] usbcore: registered new interface driver usb-storage
[    2.054391] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.054416] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.054441] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.054466] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.055134] ata6.00: ATA-8: ST1000DL002-9TT153, CC32, max UDMA/133
[    2.055137] ata6.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.055337] ata4.00: ATA-9: ST3000DM001-1CH166, CC27, max UDMA/133
[    2.055340] ata4.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.055365] ata3.00: ATA-9: ST3000DM001-1CH166, CC27, max UDMA/133
[    2.055367] ata3.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.055900] ata6.00: configured for UDMA/133
[    2.055969] ata4.00: configured for UDMA/133
[    2.056025] ata3.00: configured for UDMA/133
[    2.056129] scsi 2:0:0:0: Direct-Access     ATA      ST3000DM001-1CH1 CC27 PQ: 0 ANSI: 5
[    2.056248] sd 2:0:0:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.056250] sd 2:0:0:0: [sdb] 4096-byte physical blocks
[    2.056262] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.056363] sd 2:0:0:0: [sdb] Write Protect is off
[    2.056366] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.056398] scsi 3:0:0:0: Direct-Access     ATA      ST3000DM001-1CH1 CC27 PQ: 0 ANSI: 5
[    2.056405] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.056535] sd 3:0:0:0: [sdc] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.056537] sd 3:0:0:0: [sdc] 4096-byte physical blocks
[    2.056592] sd 3:0:0:0: [sdc] Write Protect is off
[    2.056594] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.056613] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    2.056616] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.057401] ata5.00: LPM support broken, forcing max_power
[    2.058715] ata5.00: ATA-6: WDC WD2500JD-22HBB0, 08.02D08, max UDMA/133
[    2.058717] ata5.00: 488397168 sectors, multi 16: LBA48 
[    2.062926] ata5.00: LPM support broken, forcing max_power
[    2.064234] ata5.00: configured for UDMA/133
[    2.078466] scsi 4:0:0:0: Direct-Access     ATA      WDC WD2500JD-22H 08.0 PQ: 0 ANSI: 5
[    2.078588] sd 4:0:0:0: [sdd] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.078595] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    2.078691] sd 4:0:0:0: [sdd] Write Protect is off
[    2.078694] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.078702] scsi 5:0:0:0: Direct-Access     ATA      ST1000DL002-9TT1 CC32 PQ: 0 ANSI: 5
[    2.078731] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.078804] sd 5:0:0:0: [sde] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.078829] sd 5:0:0:0: Attached scsi generic sg5 type 0
[    2.078895] sd 5:0:0:0: [sde] Write Protect is off
[    2.078897] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    2.078930] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.089584]  sdd: sdd1
[    2.089868] sd 4:0:0:0: [sdd] Attached SCSI disk
[    2.099118]  sdc: sdc1
[    2.099406] sd 3:0:0:0: [sdc] Attached SCSI disk
[    2.103926]  sdb: sdb1
[    2.104203] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.121654]  sde: sde1 sde2 < sde5 >
[    2.121999] sd 5:0:0:0: [sde] Attached SCSI disk
[    2.138341] tsc: Refined TSC clocksource calibration: 2812.627 MHz
[    2.315424] random: nonblocking pool is initialized
[    2.458284] usb 6-1: new full-speed USB device number 2 using ohci-pci
[    2.638260] usb 6-1: New USB device found, idVendor=0a5c, idProduct=2101
[    2.638264] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.638266] usb 6-1: Product: BCM2045A
[    2.638268] usb 6-1: Manufacturer: Broadcom Corp
[    2.638269] usb 6-1: SerialNumber: 00027210092C
[    2.830403] EXT4-fs (sde1): mounted filesystem with ordered data mode. Opts: (null)
[    2.939150] scsi 6:0:0:0: Direct-Access     WD       My Book 1230     1065 PQ: 0 ANSI: 6
[    2.939896] scsi 6:0:0:1: Enclosure         WD       SES Device       1065 PQ: 0 ANSI: 6
[    2.940110] sd 6:0:0:0: Attached scsi generic sg6 type 0
[    2.940205] scsi 6:0:0:1: Attached scsi generic sg7 type 13
[    2.943760] sd 6:0:0:0: [sdf] Spinning up disk...
[    3.138222] Switched to clocksource tsc
[    4.399830] init: plymouth-upstart-bridge main process (199) terminated with status 1
[    4.399840] init: plymouth-upstart-bridge main process ended, respawning
[    4.402253] init: plymouth-upstart-bridge main process (210) terminated with status 1
[    4.402261] init: plymouth-upstart-bridge main process ended, respawning
[    4.403935] init: plymouth-upstart-bridge main process (212) terminated with status 1
[    4.403943] init: plymouth-upstart-bridge main process ended, respawning
[    4.406298] init: plymouth-upstart-bridge main process (213) terminated with status 1
[    4.406307] init: plymouth-upstart-bridge main process ended, respawning
[    4.407962] init: plymouth-upstart-bridge main process (215) terminated with status 1
[    4.407970] init: plymouth-upstart-bridge main process ended, respawning
[    4.410320] init: plymouth-upstart-bridge main process (216) terminated with status 1
[    4.410329] init: plymouth-upstart-bridge main process ended, respawning
[    4.411981] init: plymouth-upstart-bridge main process (218) terminated with status 1
[    4.411988] init: plymouth-upstart-bridge main process ended, respawning
[    4.414291] init: plymouth-upstart-bridge main process (219) terminated with status 1
[    4.414299] init: plymouth-upstart-bridge main process ended, respawning
[    4.417026] init: plymouth-upstart-bridge main process (221) terminated with status 1
[    4.417033] init: plymouth-upstart-bridge main process ended, respawning
[    4.419474] init: plymouth-upstart-bridge main process (223) terminated with status 1
[    4.419484] init: plymouth-upstart-bridge main process ended, respawning
[    4.421261] init: plymouth-upstart-bridge main process (225) terminated with status 1
[    4.421269] init: plymouth-upstart-bridge respawning too fast, stopped
[    3.945983] ......ready
[    9.144975] sd 6:0:0:0: [sdf] 976746240 4096-byte logical blocks: (4.00 TB/3.63 TiB)
[    9.146226] sd 6:0:0:0: [sdf] Write Protect is off
[    9.146231] sd 6:0:0:0: [sdf] Mode Sense: 53 00 10 08
[    9.147475] sd 6:0:0:0: [sdf] No Caching mode page found
[    9.147479] sd 6:0:0:0: [sdf] Assuming drive cache: write through
[    9.148217] sd 6:0:0:0: [sdf] 976746240 4096-byte logical blocks: (4.00 TB/3.63 TiB)
[    9.150723] sd 6:0:0:0: [sdf] No Caching mode page found
[    9.150726] sd 6:0:0:0: [sdf] Assuming drive cache: write through
[    9.246827]  sdf: sdf1
[    9.247806] sd 6:0:0:0: [sdf] 976746240 4096-byte logical blocks: (4.00 TB/3.63 TiB)
[    9.250311] sd 6:0:0:0: [sdf] No Caching mode page found
[    9.250314] sd 6:0:0:0: [sdf] Assuming drive cache: write through
[    9.250316] sd 6:0:0:0: [sdf] Attached SCSI disk
[   17.484028] Adding 8384508k swap on /dev/sde5.  Priority:-1 extents:1 across:8384508k FS
[   17.539159] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.588212] systemd-udevd[330]: starting version 204
[   17.789732] lp: driver loaded but no devices found
[   17.795343] ppdev: user-space parallel port driver
[   17.798860] parport_pc 00:05: reported by Plug and Play ACPI
[   17.798913] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   17.800498] wmi: Mapper loaded
[   17.801196] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.812140] ATK0110 ATK0110:00: Overriding interface detection
[   17.816947] [drm] Initialized drm 1.1.0 20060810
[   17.827352] nvidia: module license 'NVIDIA' taints kernel.
[   17.827357] Disabling lock debugging due to kernel taint
[   17.836494] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   17.841889] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   17.842259] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[   17.842271] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  343.36  Mon Dec  1 16:18:58 PST 2014
[   17.852848] Bluetooth: Core ver 2.17
[   17.852871] NET: Registered protocol family 31
[   17.852873] Bluetooth: HCI device and connection manager initialized
[   17.852883] Bluetooth: HCI socket layer initialized
[   17.852884] Bluetooth: L2CAP socket layer initialized
[   17.852888] Bluetooth: SCO socket layer initialized
[   17.854570] usbcore: registered new interface driver btusb
[   17.858296] type=1400 audit(1435544590.828:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=390 comm="apparmor_parser"
[   17.858302] type=1400 audit(1435544590.828:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=390 comm="apparmor_parser"
[   17.858306] type=1400 audit(1435544590.828:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=390 comm="apparmor_parser"
[   17.858789] type=1400 audit(1435544590.828:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=390 comm="apparmor_parser"
[   17.858794] type=1400 audit(1435544590.828:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=390 comm="apparmor_parser"
[   17.859027] type=1400 audit(1435544590.828:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=390 comm="apparmor_parser"
[   17.861718] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SOR1 1 (20131115/utaddress-251)
[   17.861724] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SMRG 2 (20131115/utaddress-251)
[   17.861728] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \_SB_.PCI0.SBRG.ASOC.SMRG 3 (20131115/utaddress-251)
[   17.861731] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.862715] type=1400 audit(1435544590.832:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=404 comm="apparmor_parser"
[   17.874760] Linux video capture interface: v2.00
[   17.881603] MCE: In-kernel MCE decoding enabled.
[   17.883791] EDAC MC: Ver: 3.0.0
[   17.885727] AMD64 EDAC driver v3.4.0
[   17.885752] EDAC amd64: DRAM ECC disabled.
[   17.885757] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   17.885757]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   17.885757]  (Note that use of the override may cause unknown side effects.)
[   17.890812] ivtv: Start initialization, version 1.4.3
[   17.890851] ivtv0: Initializing card 0
[   17.890853] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   17.895456] lp0: using parport0 (interrupt-driven).
[   17.908843] hda_intel: Disabling MSI
[   17.908850] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   17.908872] hda-intel 0000:01:00.1: Disabling 64bit DMA
[   17.922082] kvm: disabled by bios
[   17.923736] hda-intel 0000:01:00.1: Enable delay in RIRB handling
[   17.953725] tveeprom 0-0050: Hauppauge model 32562, rev C168, serial# 7385361
[   17.953728] tveeprom 0-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[   17.953730] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   17.953732] tveeprom 0-0050: audio processor is MSP4448 (idx 27)
[   17.953733] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
[   17.953734] tveeprom 0-0050: has radio
[   17.953736] ivtv0: Autodetected Hauppauge WinTV PVR-250
[   17.983045] saa7115 0-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[   18.158733] cx231xx #0: New device Hauppauge Hauppauge Device @ 480 Mbps (2040:b140) with 6 interfaces
[   18.158737] cx231xx #0: registering interface 1
[   18.158905] cx231xx #0: Identified as Hauppauge EXETER (card=8)
[   18.171561] msp3400 0-0040: MSP4448G-A2 found @ 0x80 (ivtv i2c driver #0)
[   18.171564] msp3400 0-0040: msp3400 supports radio, mode is autodetect and autoselect
[   18.183161] tda9887 0-0043: creating new instance
[   18.183165] tda9887 0-0043: tda988[5/6/7] found
[   18.184313] tuner 0-0043: Tuner 74 found with type(s) Radio TV.
[   18.185662] scsi 6:0:0:1: Failed to get diagnostic page 0x8000002
[   18.185687] tuner 0-0061: Tuner -1 found with type(s) Radio TV.
[   18.185721] scsi 6:0:0:1: Failed to bind enclosure -19
[   18.185796] ses 6:0:0:1: Attached Enclosure device
[   18.191916] tuner-simple 0-0061: creating new instance
[   18.191919] tuner-simple 0-0061: type set to 47 (LG NTSC (TAPE series))
[   18.194467] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   18.194516] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   18.194545] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   18.194571] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   18.194597] ivtv0: Registered device radio0 for encoder radio
[   18.194598] ivtv0: Initialized card: Hauppauge WinTV PVR-250
[   18.194627] ivtv: End initialization
[   18.198134] ivtv-alsa: module loading...
[   18.366959] cx231xx #0: cx231xx_dif_set_standard: setStandard to ffffffff
[   18.379568] cx25840 1-0044: cx23102 A/V decoder found @ 0x88 (cx231xx #0)
[   18.397599] cx25840 1-0044:  Firmware download size changed to 16 bytes max length
[   18.731117] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input8
[   18.731196] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input7
[   18.731251] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input6
[   18.731302] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input5
[   18.938807] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   18.984229] EXT4-fs (sde1): re-mounted. Opts: errors=remount-ro
[   19.135142] ivtv0: Encoder revision: 0x02060039
[   19.171875] EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: (null)
[   19.210688] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   19.253033] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[   19.321502] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   19.406389] init: failsafe main process (740) killed by TERM signal
[   19.641055] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.641059] Bluetooth: BNEP filters: protocol multicast
[   19.641067] Bluetooth: BNEP socket layer initialized
[   19.644322] Bluetooth: RFCOMM TTY layer initialized
[   19.644331] Bluetooth: RFCOMM socket layer initialized
[   19.644337] Bluetooth: RFCOMM ver 1.11
[   19.712392] type=1400 audit(1435544592.684:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=862 comm="apparmor_parser"
[   19.712400] type=1400 audit(1435544592.684:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=862 comm="apparmor_parser"
[   19.712841] type=1400 audit(1435544592.684:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=862 comm="apparmor_parser"
[   19.970657] init: cups main process (863) killed by HUP signal
[   19.970667] init: cups main process ended, respawning
[   20.342107] init: apport-noui (/var/crash/_usr_bin_mythfrontend.real.1000.crash) main process (780) terminated with status 1
```

1 tuner attached and was recognized after boot:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-55-generic (buildd@brownie) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #94-Ubuntu SMP Thu Jun 18 00:27:10 UTC 2015 (Ubuntu 3.13.0-55.94-generic 3.13.11-ckt20)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-55-generic root=UUID=dfea8c42-85ad-4d85-9a60-70d7bfd61c3e ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cfe7ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cfe80000-0x00000000cfe97fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cfe98000-0x00000000cfebffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cfec0000-0x00000000cfefffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000022fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: System manufacturer System Product Name/M5A78L-M LX, BIOS 0510    08/15/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x230000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000230000000 aka 8960M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcfe80 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x22fe00000-0x22fffffff]
[    0.000000]  [mem 0x22fe00000-0x22fffffff] page 2M
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x22c000000-0x22fdfffff]
[    0.000000]  [mem 0x22c000000-0x22fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x22bffffff]
[    0.000000]  [mem 0x200000000-0x22bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xcfe7ffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xcfdfffff] page 2M
[    0.000000]  [mem 0xcfe00000-0xcfe7ffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35b46000-0x36d9afff]
[    0.000000] ACPI: RSDP 00000000000fb490 000024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000cfe80100 000054 (v01 081511 XSDT0945 20110815 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cfe80290 0000F4 (v03 081511 FACP0945 20110815 MSFT 00000097)
[    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20131115/tbfadt-603)
[    0.000000] ACPI: DSDT 00000000cfe80460 00D6D6 (v01  A1860 A1860001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cfe98000 000040
[    0.000000] ACPI: APIC 00000000cfe80390 00008C (v01 081511 APIC0945 20110815 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cfe80420 00003C (v01 081511 OEMMCFG  20110815 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cfe98040 000072 (v01 081511 OEMB0945 20110815 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cfe8f460 000038 (v01 081511 OEMHPET  20110815 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cfe8f4a0 0008BC (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000022fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x22fffffff]
[    0.000000]   NODE_DATA [mem 0x22fff9000-0x22fffdfff]
[    0.000000]  [ffffea0000000000-ffffea0008bfffff] PMD -> [ffff880227600000-ffff88022f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x22fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xcfe7ffff]
[    0.000000]   node   0: [mem 0x100000000-0x22fffffff]
[    0.000000] On node 0 totalpages: 2096670
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13242 pages used for memmap
[    0.000000]   DMA32 zone: 847488 pages, LIFO batch:31
[    0.000000]   Normal zone: 19456 pages used for memmap
[    0.000000]   Normal zone: 1245184 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e4000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcfe80000-0xcfe97fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcfe98000-0xcfebffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcfec0000-0xcfefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcff00000-0xffdfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
[    0.000000] e820: [mem 0xcff00000-0xffdfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88022fc00000 s81536 r8192 d20864 u262144
[    0.000000] pcpu-alloc: s81536 r8192 d20864 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2063887
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-55-generic root=UUID=dfea8c42-85ad-4d85-9a60-70d7bfd61c3e ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 0 size 32 MB
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: [mem 0xc4000000-0xc7ffffff]
[    0.000000] Memory: 8087736K/8386680K available (7392K kernel code, 1146K rwdata, 3408K rodata, 1336K init, 1448K bss, 298944K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.004000] tsc: Fast TSC calibration using PIT
[    0.008000] tsc: Detected 2812.487 MHz processor
[    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5624.97 BogoMIPS (lpj=11249948)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000035] Security Framework initialized
[    0.000053] AppArmor: AppArmor initialized
[    0.000054] Yama: becoming mindful.
[    0.000554] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002801] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003844] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.003853] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.004097] Initializing cgroup subsys memory
[    0.004104] Initializing cgroup subsys devices
[    0.004106] Initializing cgroup subsys freezer
[    0.004107] Initializing cgroup subsys blkio
[    0.004109] Initializing cgroup subsys perf_event
[    0.004111] Initializing cgroup subsys hugetlb
[    0.004128] tseg: 0000000000
[    0.004135] CPU: Physical Processor ID: 0
[    0.004136] CPU: Processor Core ID: 0
[    0.004138] mce: CPU supports 6 MCE banks
[    0.004143] LVT offset 0 assigned for vector 0xf9
[    0.004148] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
[    0.004148] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64
[    0.004148] tlb_flushall_shift: 4
[    0.004235] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
[    0.004974] ACPI: Core revision 20131115
[    0.008362] ACPI: All ACPI Tables successfully acquired
[    0.015622] ftrace: allocating 28579 entries in 112 pages
[    0.027145] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066821] smpboot: CPU0: AMD Phenom(tm) II X4 830 Processor (fam: 10, model: 04, stepping: 03)
[    0.171339] Performance Events: AMD PMU driver.
[    0.171343] ... version:                0
[    0.171344] ... bit width:              48
[    0.171345] ... generic registers:      4
[    0.171346] ... value mask:             0000ffffffffffff
[    0.171347] ... max period:             00007fffffffffff
[    0.171348] ... fixed-purpose events:   0
[    0.171348] ... event mask:             000000000000000f
[    0.172835] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.172903] x86: Booting SMP configuration:
[    0.172904] .... node  #0, CPUs:      #1 #2 #3
[    0.212143] x86: Booted up 1 node, 4 CPUs
[    0.212145] smpboot: Total of 4 processors activated (22499.89 BogoMIPS)
[    0.216905] devtmpfs: initialized
[    0.220708] EVM: security.selinux
[    0.220710] EVM: security.SMACK64
[    0.220711] EVM: security.ima
[    0.220712] EVM: security.capability
[    0.220794] PM: Registering ACPI NVS region [mem 0xcfe98000-0xcfebffff] (163840 bytes)
[    0.221702] pinctrl core: initialized pinctrl subsystem
[    0.221759] regulator-dummy: no parameters
[    0.221785] RTC time:  2:43:49, date: 06/29/15
[    0.221820] NET: Registered protocol family 16
[    0.221916] cpuidle: using governor ladder
[    0.221918] cpuidle: using governor menu
[    0.221922] node 0 link 0: io port [1000, ffffff]
[    0.221924] TOM: 00000000d0000000 aka 3328M
[    0.221926] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
[    0.221928] node 0 link 0: mmio [a0000, bffff]
[    0.221930] node 0 link 0: mmio [d0000000, dfffffff]
[    0.221936] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.221938] node 0 link 0: mmio [f0000000, ffdfffff]
[    0.221939] TOM2: 0000000230000000 aka 8960M
[    0.221941] bus: [bus 00-1f] on node 0 link 0
[    0.221942] bus: 00 [io  0x0000-0xffff]
[    0.221943] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.221944] bus: 00 [mem 0xd0000000-0xdfffffff]
[    0.221945] bus: 00 [mem 0xf0000000-0xffffffff]
[    0.221946] bus: 00 [mem 0x230000000-0xfcffffffff]
[    0.221995] ACPI: bus type PCI registered
[    0.221997] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.222050] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.222052] PCI: not using MMCONFIG
[    0.222053] PCI: Using configuration type 1 for base access
[    0.222054] PCI: Using configuration type 1 for extended access
[    0.222229] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.222229] mtrr: probably your BIOS does not setup all CPUs.
[    0.222230] mtrr: corrected configuration.
[    0.223011] bio: create slab <bio-0> at 0
[    0.223162] ACPI: Added _OSI(Module Device)
[    0.223164] ACPI: Added _OSI(Processor Device)
[    0.223165] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.223166] ACPI: Added _OSI(Processor Aggregator Device)
[    0.225514] ACPI: Executed 3 blocks of module-level executable AML code
[    0.299769] ACPI: Interpreter enabled
[    0.299781] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.299794] ACPI: (supports S0 S1 S3 S4 S5)
[    0.299796] ACPI: Using IOAPIC for interrupt routing
[    0.299813] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.300925] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.309171] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.309257] ACPI: No dock devices found.
[    0.360247] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.360253] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.360258] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.360517] PCI host bridge to bus 0000:00
[    0.360519] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.360521] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.360523] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.360525] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.360526] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.360528] pci_bus 0000:00: root bus resource [mem 0xcff00000-0xdfffffff]
[    0.360529] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
[    0.360539] pci 0000:00:00.0: [1022:9600] type 00 class 0x060000
[    0.360626] pci 0000:00:02.0: [1022:9603] type 01 class 0x060400
[    0.360656] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.360692] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.360717] pci 0000:00:04.0: [1022:9604] type 01 class 0x060400
[    0.360745] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.360779] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.360821] pci 0000:00:11.0: [1002:4390] type 00 class 0x01018f
[    0.360840] pci 0000:00:11.0: reg 0x10: [io  0xc000-0xc007]
[    0.360849] pci 0000:00:11.0: reg 0x14: [io  0xb000-0xb003]
[    0.360858] pci 0000:00:11.0: reg 0x18: [io  0xa000-0xa007]
[    0.360867] pci 0000:00:11.0: reg 0x1c: [io  0x9000-0x9003]
[    0.360876] pci 0000:00:11.0: reg 0x20: [io  0x8000-0x800f]
[    0.360885] pci 0000:00:11.0: reg 0x24: [mem 0xfcfffc00-0xfcffffff]
[    0.360904] pci 0000:00:11.0: set SATA to AHCI mode
[    0.360988] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.361001] pci 0000:00:12.0: reg 0x10: [mem 0xfcffe000-0xfcffefff]
[    0.361083] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.361111] pci 0000:00:12.1: [1002:4398] type 00 class 0x0c0310
[    0.361124] pci 0000:00:12.1: reg 0x10: [mem 0xfcffd000-0xfcffdfff]
[    0.361208] pci 0000:00:12.1: System wakeup disabled by ACPI
[    0.361236] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.361254] pci 0000:00:12.2: reg 0x10: [mem 0xfcfff800-0xfcfff8ff]
[    0.361333] pci 0000:00:12.2: supports D1 D2
[    0.361334] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.361371] pci 0000:00:12.2: System wakeup disabled by ACPI
[    0.361400] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.361412] pci 0000:00:13.0: reg 0x10: [mem 0xfcffc000-0xfcffcfff]
[    0.361495] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.361518] pci 0000:00:13.1: [1002:4398] type 00 class 0x0c0310
[    0.361530] pci 0000:00:13.1: reg 0x10: [mem 0xfcffb000-0xfcffbfff]
[    0.361613] pci 0000:00:13.1: System wakeup disabled by ACPI
[    0.361641] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.361659] pci 0000:00:13.2: reg 0x10: [mem 0xfcfff400-0xfcfff4ff]
[    0.361737] pci 0000:00:13.2: supports D1 D2
[    0.361739] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.361776] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.361809] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.361942] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
[    0.361958] pci 0000:00:14.1: reg 0x10: [io  0x0000-0x0007]
[    0.361966] pci 0000:00:14.1: reg 0x14: [io  0x0000-0x0003]
[    0.361975] pci 0000:00:14.1: reg 0x18: [io  0x0000-0x0007]
[    0.361984] pci 0000:00:14.1: reg 0x1c: [io  0x0000-0x0003]
[    0.361993] pci 0000:00:14.1: reg 0x20: [io  0xff00-0xff0f]
[    0.362085] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.362197] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.362260] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.362283] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.362296] pci 0000:00:14.5: reg 0x10: [mem 0xfcffa000-0xfcffafff]
[    0.362379] pci 0000:00:14.5: System wakeup disabled by ACPI
[    0.362406] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
[    0.362459] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
[    0.362509] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
[    0.362558] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
[    0.362610] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
[    0.362700] pci 0000:01:00.0: [10de:0de1] type 00 class 0x030000
[    0.362709] pci 0000:01:00.0: reg 0x10: [mem 0xfd000000-0xfdffffff]
[    0.362719] pci 0000:01:00.0: reg 0x14: [mem 0xd8000000-0xdfffffff 64bit pref]
[    0.362729] pci 0000:01:00.0: reg 0x1c: [mem 0xd6000000-0xd7ffffff 64bit pref]
[    0.362735] pci 0000:01:00.0: reg 0x24: [io  0xdc00-0xdc7f]
[    0.362742] pci 0000:01:00.0: reg 0x30: [mem 0xfeb00000-0xfeb7ffff pref]
[    0.362807] pci 0000:01:00.1: [10de:0bea] type 00 class 0x040300
[    0.362816] pci 0000:01:00.1: reg 0x10: [mem 0xfebf8000-0xfebfbfff]
[    0.367315] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.367320] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.367322] pci 0000:00:02.0:   bridge window [mem 0xfd000000-0xfebfffff]
[    0.367326] pci 0000:00:02.0:   bridge window [mem 0xd6000000-0xdfffffff 64bit pref]
[    0.367385] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
[    0.367398] pci 0000:02:00.0: reg 0x10: [io  0xe800-0xe8ff]
[    0.367417] pci 0000:02:00.0: reg 0x18: [mem 0xf7fff000-0xf7ffffff 64bit pref]
[    0.367430] pci 0000:02:00.0: reg 0x20: [mem 0xf7ff8000-0xf7ffbfff 64bit pref]
[    0.367482] pci 0000:02:00.0: supports D1 D2
[    0.367484] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.367511] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.375318] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.375323] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.375327] pci 0000:00:04.0:   bridge window [mem 0xf7f00000-0xf7ffffff 64bit pref]
[    0.375373] pci 0000:03:05.0: [4444:0016] type 00 class 0x040000
[    0.375396] pci 0000:03:05.0: reg 0x10: [mem 0xf8000000-0xfbffffff pref]
[    0.375555] pci 0000:00:14.4: PCI bridge to [bus 03] (subtractive decode)
[    0.375563] pci 0000:00:14.4:   bridge window [mem 0xf8000000-0xfbffffff pref]
[    0.375565] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.375567] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.375568] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.375570] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.375572] pci 0000:00:14.4:   bridge window [mem 0xcff00000-0xdfffffff] (subtractive decode)
[    0.375573] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.391375] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 12 14 15)
[    0.391413] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
[    0.391448] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.391480] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.391513] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 *10 11 12 14 15)
[    0.391546] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.391580] ACPI: PCI Interrupt Link [LNKG] (IRQs *11)
[    0.391611] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.391757] ACPI: Enabled 1 GPEs in block 00 to 1F
[    0.391763] ACPI: \_SB_.PCI0: notify handler is installed
[    0.391795] Found 1 acpi root devices
[    0.391886] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.391888] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.391889] vgaarb: loaded
[    0.391890] vgaarb: bridge control possible 0000:01:00.0
[    0.392036] SCSI subsystem initialized
[    0.392098] libata version 3.00 loaded.
[    0.392115] ACPI: bus type USB registered
[    0.392129] usbcore: registered new interface driver usbfs
[    0.392135] usbcore: registered new interface driver hub
[    0.392156] usbcore: registered new device driver usb
[    0.392264] PCI: Using ACPI for IRQ routing
[    0.400489] PCI: pci_cache_line_size set to 64 bytes
[    0.400538] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.400540] e820: reserve RAM buffer [mem 0xcfe80000-0xcfffffff]
[    0.400608] NetLabel: Initializing
[    0.400609] NetLabel:  domain hash size = 128
[    0.400610] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.400620] NetLabel:  unlabeled traffic allowed by default
[    0.400679] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.400683] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.402741] Switched to clocksource hpet
[    0.406936] AppArmor: AppArmor Filesystem Enabled
[    0.406957] pnp: PnP ACPI init
[    0.406967] ACPI: bus type PNP registered
[    0.407084] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.407116] pnp 00:01: [dma 4]
[    0.407132] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.407160] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.407177] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.407198] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.407632] pnp 00:05: [dma 0 disabled]
[    0.407783] pnp 00:05: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.407824] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.408146] pnp 00:07: [dma 0 disabled]
[    0.408207] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.408285] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.408287] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.408289] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.408470] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.408472] system 00:09: [io  0x040b] has been reserved
[    0.408473] system 00:09: [io  0x04d6] has been reserved
[    0.408475] system 00:09: [io  0x0c00-0x0c01] has been reserved
[    0.408477] system 00:09: [io  0x0c14] has been reserved
[    0.408479] system 00:09: [io  0x0c50-0x0c51] has been reserved
[    0.408481] system 00:09: [io  0x0c52] has been reserved
[    0.408482] system 00:09: [io  0x0c6c] has been reserved
[    0.408484] system 00:09: [io  0x0c6f] has been reserved
[    0.408486] system 00:09: [io  0x0cd0-0x0cd1] has been reserved
[    0.408488] system 00:09: [io  0x0cd2-0x0cd3] has been reserved
[    0.408490] system 00:09: [io  0x0cd4-0x0cd5] has been reserved
[    0.408491] system 00:09: [io  0x0cd6-0x0cd7] has been reserved
[    0.408493] system 00:09: [io  0x0cd8-0x0cdf] has been reserved
[    0.408495] system 00:09: [io  0x0b00-0x0b3f] has been reserved
[    0.408497] system 00:09: [io  0x0800-0x089f] could not be reserved
[    0.408499] system 00:09: [io  0x0b00-0x0b0f] has been reserved
[    0.408500] system 00:09: [io  0x0b20-0x0b3f] has been reserved
[    0.408502] system 00:09: [io  0x0900-0x090f] has been reserved
[    0.408504] system 00:09: [io  0x0910-0x091f] has been reserved
[    0.408506] system 00:09: [io  0xfe00-0xfefe] has been reserved
[    0.408508] system 00:09: [mem 0xcff00000-0xcfffffff] has been reserved
[    0.408510] system 00:09: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.408512] system 00:09: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.408514] system 00:09: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.408516] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.408649] system 00:0a: [io  0x0230-0x023f] has been reserved
[    0.408651] system 00:0a: [io  0x0290-0x029f] has been reserved
[    0.408653] system 00:0a: [io  0x0300-0x030f] has been reserved
[    0.408655] system 00:0a: [io  0x0a30-0x0a3f] has been reserved
[    0.408657] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.408701] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.408703] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.422908] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.422912] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.422914] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.422916] system 00:0c: [mem 0x00100000-0xcfefffff] could not be reserved
[    0.422918] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.422920] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.422999] pnp: PnP ACPI: found 13 devices
[    0.423000] ACPI: bus type PNP unregistered
[    0.429205] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.429208] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.429211] pci 0000:00:02.0:   bridge window [mem 0xfd000000-0xfebfffff]
[    0.429214] pci 0000:00:02.0:   bridge window [mem 0xd6000000-0xdfffffff 64bit pref]
[    0.429217] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.429219] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.429222] pci 0000:00:04.0:   bridge window [mem 0xf7f00000-0xf7ffffff 64bit pref]
[    0.429225] pci 0000:00:14.4: PCI bridge to [bus 03]
[    0.429232] pci 0000:00:14.4:   bridge window [mem 0xf8000000-0xfbffffff pref]
[    0.429238] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.429239] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.429241] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.429243] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.429244] pci_bus 0000:00: resource 8 [mem 0xcff00000-0xdfffffff]
[    0.429246] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.429248] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.429249] pci_bus 0000:01: resource 1 [mem 0xfd000000-0xfebfffff]
[    0.429251] pci_bus 0000:01: resource 2 [mem 0xd6000000-0xdfffffff 64bit pref]
[    0.429253] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.429254] pci_bus 0000:02: resource 2 [mem 0xf7f00000-0xf7ffffff 64bit pref]
[    0.429256] pci_bus 0000:03: resource 2 [mem 0xf8000000-0xfbffffff pref]
[    0.429258] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.429259] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.429261] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.429263] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.429264] pci_bus 0000:03: resource 8 [mem 0xcff00000-0xdfffffff]
[    0.429266] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.429294] NET: Registered protocol family 2
[    0.429512] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.429701] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.429978] TCP: Hash tables configured (established 65536 bind 65536)
[    0.430016] TCP: reno registered
[    0.430027] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.430076] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.430171] NET: Registered protocol family 1
[    0.854779] pci 0000:01:00.0: Video device with shadowed ROM
[    0.854794] PCI: CLS 64 bytes, default 64
[    0.854847] Trying to unpack rootfs image as initramfs...
[    1.138184] Freeing initrd memory: 18772K (ffff880035b46000 - ffff880036d9b000)
[    1.138421] PCI-DMA: Disabling AGP.
[    1.138506] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.138507] PCI-DMA: using GART IOMMU.
[    1.138510] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.141840] LVT offset 1 assigned for vector 0x400
[    1.141849] IBS: LVT offset 1 assigned
[    1.141873] perf: AMD IBS detected (0x0000001f)
[    1.141911] microcode: CPU0: patch_level=0x010000c8
[    1.141919] microcode: CPU1: patch_level=0x010000c8
[    1.141929] microcode: CPU2: patch_level=0x010000c8
[    1.141939] microcode: CPU3: patch_level=0x010000c8
[    1.142000] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.142002] Scanning for low memory corruption every 60 seconds
[    1.142209] Initialise system trusted keyring
[    1.142252] audit: initializing netlink socket (disabled)
[    1.142262] type=2000 audit(1435545830.032:1): initialized
[    1.168210] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.169423] zbud: loaded
[    1.169567] VFS: Disk quotas dquot_6.5.2
[    1.169608] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.170053] fuse init (API version 7.22)
[    1.170113] msgmni has been set to 15961
[    1.170162] Key type big_key registered
[    1.170603] Key type asymmetric registered
[    1.170606] Asymmetric key parser 'x509' registered
[    1.170654] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.170699] io scheduler noop registered
[    1.170700] io scheduler deadline registered (default)
[    1.170723] io scheduler cfq registered
[    1.170911] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.171022] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
[    1.171066] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.171077] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.171114] ipmi message handler version 39.2
[    1.171172] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.171175] ACPI: Power Button [PWRB]
[    1.171202] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.171204] ACPI: Power Button [PWRF]
[    1.172036] GHES: HEST is not enabled!
[    1.172131] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.192590] 00:07: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.193725] Linux agpgart interface v0.103
[    1.194908] brd: module loaded
[    1.195517] loop: module loaded
[    1.195826] libphy: Fixed MDIO Bus: probed
[    1.195901] tun: Universal TUN/TAP device driver, 1.6
[    1.195902] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.195938] PPP generic driver version 2.4.2
[    1.195973] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.195975] ehci-pci: EHCI PCI platform driver
[    1.196086] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.196091] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.196095] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.196106] ehci-pci 0000:00:12.2: debug port 1
[    1.196145] ehci-pci 0000:00:12.2: irq 17, io mem 0xfcfff800
[    1.206615] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.206655] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.206657] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.206659] usb usb1: Product: EHCI Host Controller
[    1.206660] usb usb1: Manufacturer: Linux 3.13.0-55-generic ehci_hcd
[    1.206662] usb usb1: SerialNumber: 0000:00:12.2
[    1.206769] hub 1-0:1.0: USB hub found
[    1.206777] hub 1-0:1.0: 6 ports detected
[    1.206989] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.206993] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.206997] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.207007] ehci-pci 0000:00:13.2: debug port 1
[    1.207044] ehci-pci 0000:00:13.2: irq 19, io mem 0xfcfff400
[    1.218606] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.218643] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.218645] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.218647] usb usb2: Product: EHCI Host Controller
[    1.218648] usb usb2: Manufacturer: Linux 3.13.0-55-generic ehci_hcd
[    1.218650] usb usb2: SerialNumber: 0000:00:13.2
[    1.218768] hub 2-0:1.0: USB hub found
[    1.218774] hub 2-0:1.0: 6 ports detected
[    1.218872] ehci-platform: EHCI generic platform driver
[    1.218879] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.218880] ohci-pci: OHCI PCI platform driver
[    1.218984] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.218988] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.219010] ohci-pci 0000:00:12.0: irq 16, io mem 0xfcffe000
[    1.278596] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.278599] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.278601] usb usb3: Product: OHCI PCI host controller
[    1.278602] usb usb3: Manufacturer: Linux 3.13.0-55-generic ohci_hcd
[    1.278604] usb usb3: SerialNumber: 0000:00:12.0
[    1.278710] hub 3-0:1.0: USB hub found
[    1.278718] hub 3-0:1.0: 3 ports detected
[    1.278868] ohci-pci 0000:00:12.1: OHCI PCI host controller
[    1.278872] ohci-pci 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.278885] ohci-pci 0000:00:12.1: irq 16, io mem 0xfcffd000
[    1.338582] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.338585] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.338586] usb usb4: Product: OHCI PCI host controller
[    1.338588] usb usb4: Manufacturer: Linux 3.13.0-55-generic ohci_hcd
[    1.338589] usb usb4: SerialNumber: 0000:00:12.1
[    1.338694] hub 4-0:1.0: USB hub found
[    1.338701] hub 4-0:1.0: 3 ports detected
[    1.338849] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.338853] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.338874] ohci-pci 0000:00:13.0: irq 18, io mem 0xfcffc000
[    1.398570] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.398572] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.398574] usb usb5: Product: OHCI PCI host controller
[    1.398575] usb usb5: Manufacturer: Linux 3.13.0-55-generic ohci_hcd
[    1.398576] usb usb5: SerialNumber: 0000:00:13.0
[    1.398679] hub 5-0:1.0: USB hub found
[    1.398688] hub 5-0:1.0: 3 ports detected
[    1.398839] ohci-pci 0000:00:13.1: OHCI PCI host controller
[    1.398843] ohci-pci 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.398855] ohci-pci 0000:00:13.1: irq 18, io mem 0xfcffb000
[    1.458563] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.458565] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.458567] usb usb6: Product: OHCI PCI host controller
[    1.458568] usb usb6: Manufacturer: Linux 3.13.0-55-generic ohci_hcd
[    1.458570] usb usb6: SerialNumber: 0000:00:13.1
[    1.458672] hub 6-0:1.0: USB hub found
[    1.458679] hub 6-0:1.0: 3 ports detected
[    1.458834] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    1.458839] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.458851] ohci-pci 0000:00:14.5: irq 18, io mem 0xfcffa000
[    1.518559] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.518561] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.518563] usb usb7: Product: OHCI PCI host controller
[    1.518564] usb usb7: Manufacturer: Linux 3.13.0-55-generic ohci_hcd
[    1.518567] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.518568] usb usb7: SerialNumber: 0000:00:14.5
[    1.518660] hub 7-0:1.0: USB hub found
[    1.518669] hub 7-0:1.0: 2 ports detected
[    1.518724] ohci-platform: OHCI generic platform driver
[    1.518731] uhci_hcd: USB Universal Host Controller Interface driver
[    1.518776] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.519143] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.519149] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.519245] mousedev: PS/2 mouse device common for all mice
[    1.519347] rtc_cmos 00:02: RTC can wake from S4
[    1.519447] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.519471] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.519526] device-mapper: uevent: version 1.0.3
[    1.519572] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.519578] ledtrig-cpu: registered to indicate activity on CPUs
[    1.519664] TCP: cubic registered
[    1.519725] NET: Registered protocol family 10
[    1.519858] NET: Registered protocol family 17
[    1.519865] Key type dns_resolver registered
[    1.520087] Loading compiled-in X.509 certificates
[    1.521055] Loaded X.509 cert 'Magrathea: Glacier signing key: 13dfa511f14d8706c6ace27e0c6a7d1469b9ea7f'
[    1.521063] registered taskstats version 1
[    1.523194] Key type trusted registered
[    1.526158] Key type encrypted registered
[    1.526162] AppArmor: AppArmor sha1 policy hashing enabled
[    1.526164] IMA: No TPM chip found, activating TPM-bypass!
[    1.526374] regulator-dummy: disabling
[    1.526418]   Magic number: 3:74:714
[    1.526503] rtc_cmos 00:02: setting system clock to 2015-06-29 02:43:50 UTC (1435545830)
[    1.526605] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.526985] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.526986] EDD information not available.
[    1.527006] PM: Hibernation image not present or could not be loaded.
[    1.528584] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    1.528586] Write protecting the kernel read-only data: 12288k
[    1.530677] Freeing unused kernel memory: 788K (ffff88000173b000 - ffff880001800000)
[    1.532399] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
[    1.542738] systemd-udevd[121]: starting version 204
[    1.559331] ahci 0000:00:11.0: version 3.0
[    1.559408] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.559419] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.559546] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.559550] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.559644] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.559799] r8169 0000:02:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000c7a000, 54:04:a6:82:07:03, XID 0c900800 IRQ 42
[    1.559801] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.560043] scsi0 : ahci
[    1.560152] scsi1 : ahci
[    1.560212] scsi2 : ahci
[    1.560522] scsi3 : ahci
[    1.560572] ata1: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffd00 irq 22
[    1.560575] ata2: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffd80 irq 22
[    1.560578] ata3: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffe00 irq 22
[    1.560580] ata4: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffe80 irq 22
[    1.563376] scsi4 : pata_atiixp
[    1.563437] scsi5 : pata_atiixp
[    1.563476] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.563478] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.653385] usb 1-1: New USB device found, idVendor=2040, idProduct=b140
[    1.653388] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.653391] usb 1-1: Product: Hauppauge Device
[    1.653392] usb 1-1: Manufacturer: Hauppauge
[    1.653394] usb 1-1: SerialNumber: 4034729194
[    1.743046] ata6.00: ATA-9: ST3000DM001-1ER166, CC25, max UDMA/133
[    1.743050] ata6.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.743056] ata6.01: ATAPI: TSSTcorp CDDVDW SH-222AB, SB00, max UDMA/100
[    1.759031] ata6.00: configured for UDMA/100
[    1.770541] usb 1-2: new high-speed USB device number 3 using ehci-pci
[    1.774821] ata6.01: configured for UDMA/100
[    1.936264] usb 1-2: New USB device found, idVendor=1058, idProduct=1230
[    1.936266] usb 1-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[    1.936268] usb 1-2: Product: My Book 1230
[    1.936269] usb 1-2: Manufacturer: Western Digital
[    1.936271] usb 1-2: SerialNumber: 5743433445364C5658553133
[    1.939588] usb-storage 1-2:1.0: USB Mass Storage device detected
[    1.939680] scsi6 : usb-storage 1-2:1.0
[    1.939741] usbcore: registered new interface driver usb-storage
[    2.050468] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.050494] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.050519] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.050544] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.051188] ata4.00: ATA-8: ST1000DL002-9TT153, CC32, max UDMA/133
[    2.051190] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.051422] ata2.00: ATA-9: ST3000DM001-1CH166, CC27, max UDMA/133
[    2.051424] ata2.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.051522] ata1.00: ATA-9: ST3000DM001-1CH166, CC27, max UDMA/133
[    2.051524] ata1.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.051943] ata4.00: configured for UDMA/133
[    2.052090] ata2.00: configured for UDMA/133
[    2.052126] ata1.00: configured for UDMA/133
[    2.052250] scsi 0:0:0:0: Direct-Access     ATA      ST3000DM001-1CH1 CC27 PQ: 0 ANSI: 5
[    2.052364] sd 0:0:0:0: [sda] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.052367] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.052395] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.052477] sd 0:0:0:0: [sda] Write Protect is off
[    2.052481] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.052526] scsi 1:0:0:0: Direct-Access     ATA      ST3000DM001-1CH1 CC27 PQ: 0 ANSI: 5
[    2.052528] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.052676] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.052727] sd 1:0:0:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.052729] sd 1:0:0:0: [sdb] 4096-byte physical blocks
[    2.052814] sd 1:0:0:0: [sdb] Write Protect is off
[    2.052817] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.052852] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.053449] ata3.00: LPM support broken, forcing max_power
[    2.054755] ata3.00: ATA-6: WDC WD2500JD-22HBB0, 08.02D08, max UDMA/133
[    2.054758] ata3.00: 488397168 sectors, multi 16: LBA48 
[    2.059006] ata3.00: LPM support broken, forcing max_power
[    2.060315] ata3.00: configured for UDMA/133
[    2.074551] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500JD-22H 08.0 PQ: 0 ANSI: 5
[    2.074647] sd 2:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.074673] sd 2:0:0:0: [sdc] Write Protect is off
[    2.074676] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.074681] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.074687] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.074803] scsi 3:0:0:0: Direct-Access     ATA      ST1000DL002-9TT1 CC32 PQ: 0 ANSI: 5
[    2.074904] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    2.074918] sd 3:0:0:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.075007] sd 3:0:0:0: [sdd] Write Protect is off
[    2.075009] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.075025] scsi 5:0:0:0: Direct-Access     ATA      ST3000DM001-1ER1 CC25 PQ: 0 ANSI: 5
[    2.075044] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.075126] sd 5:0:0:0: [sde] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.075129] sd 5:0:0:0: [sde] 4096-byte physical blocks
[    2.075144] sd 5:0:0:0: Attached scsi generic sg4 type 0
[    2.075174] sd 5:0:0:0: [sde] Write Protect is off
[    2.075177] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    2.075521] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.075824] scsi 5:0:1:0: CD-ROM            TSSTcorp CDDVDW SH-222AB  SB00 PQ: 0 ANSI: 5
[    2.078469] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.078472] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.078575] sr 5:0:1:0: Attached scsi CD-ROM sr0
[    2.078637] sr 5:0:1:0: Attached scsi generic sg5 type 5
[    2.094680]  sdc: sdc1
[    2.094836] sd 2:0:0:0: [sdc] Attached SCSI disk
[    2.098881]  sdb: sdb1
[    2.099225] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.103935]  sda: sda1
[    2.104209] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.126409]  sdd: sdd1 sdd2 < sdd5 >
[    2.126745] sd 3:0:0:0: [sdd] Attached SCSI disk
[    2.138420] tsc: Refined TSC clocksource calibration: 2812.627 MHz
[    2.144406]  sde: sde1
[    2.144692] sd 5:0:0:0: [sde] Attached SCSI disk
[    2.342319] random: nonblocking pool is initialized
[    2.458364] usb 6-1: new full-speed USB device number 2 using ohci-pci
[    2.634331] usb 6-1: New USB device found, idVendor=0a5c, idProduct=2101
[    2.634334] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.634337] usb 6-1: Product: BCM2045A
[    2.634338] usb 6-1: Manufacturer: Broadcom Corp
[    2.634340] usb 6-1: SerialNumber: 00027210092C
[    2.825045] EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: (null)
[    2.939176] scsi 6:0:0:0: Direct-Access     WD       My Book 1230     1065 PQ: 0 ANSI: 6
[    2.939922] scsi 6:0:0:1: Enclosure         WD       SES Device       1065 PQ: 0 ANSI: 6
[    2.940105] sd 6:0:0:0: Attached scsi generic sg6 type 0
[    2.940192] scsi 6:0:0:1: Attached scsi generic sg7 type 13
[    2.943783] sd 6:0:0:0: [sdf] Spinning up disk...
[    3.138309] Switched to clocksource tsc
[    4.535860] init: plymouth-upstart-bridge main process (199) terminated with status 1
[    4.535870] init: plymouth-upstart-bridge main process ended, respawning
[    4.537569] init: plymouth-upstart-bridge main process (213) terminated with status 1
[    4.537577] init: plymouth-upstart-bridge main process ended, respawning
[    4.538917] init: plymouth-upstart-bridge main process (215) terminated with status 1
[    4.538924] init: plymouth-upstart-bridge main process ended, respawning
[    4.540563] init: plymouth-upstart-bridge main process (216) terminated with status 1
[    4.540571] init: plymouth-upstart-bridge main process ended, respawning
[    4.541893] init: plymouth-upstart-bridge main process (218) terminated with status 1
[    4.541900] init: plymouth-upstart-bridge main process ended, respawning
[    4.543553] init: plymouth-upstart-bridge main process (219) terminated with status 1
[    4.543561] init: plymouth-upstart-bridge main process ended, respawning
[    4.544871] init: plymouth-upstart-bridge main process (221) terminated with status 1
[    4.544878] init: plymouth-upstart-bridge main process ended, respawning
[    4.546545] init: plymouth-upstart-bridge main process (222) terminated with status 1
[    4.546553] init: plymouth-upstart-bridge main process ended, respawning
[    4.547883] init: plymouth-upstart-bridge main process (224) terminated with status 1
[    4.547890] init: plymouth-upstart-bridge main process ended, respawning
[    4.549553] init: plymouth-upstart-bridge main process (225) terminated with status 1
[    4.549560] init: plymouth-upstart-bridge main process ended, respawning
[    4.550893] init: plymouth-upstart-bridge main process (227) terminated with status 1
[    4.550900] init: plymouth-upstart-bridge respawning too fast, stopped
[    3.946061] ......ready
[    9.145373] sd 6:0:0:0: [sdf] 976746240 4096-byte logical blocks: (4.00 TB/3.63 TiB)
[    9.146626] sd 6:0:0:0: [sdf] Write Protect is off
[    9.146630] sd 6:0:0:0: [sdf] Mode Sense: 53 00 10 08
[    9.147874] sd 6:0:0:0: [sdf] No Caching mode page found
[    9.147878] sd 6:0:0:0: [sdf] Assuming drive cache: write through
[    9.148616] sd 6:0:0:0: [sdf] 976746240 4096-byte logical blocks: (4.00 TB/3.63 TiB)
[    9.151122] sd 6:0:0:0: [sdf] No Caching mode page found
[    9.151126] sd 6:0:0:0: [sdf] Assuming drive cache: write through
[    9.247226]  sdf: sdf1
[    9.248204] sd 6:0:0:0: [sdf] 976746240 4096-byte logical blocks: (4.00 TB/3.63 TiB)
[    9.250710] sd 6:0:0:0: [sdf] No Caching mode page found
[    9.250713] sd 6:0:0:0: [sdf] Assuming drive cache: write through
[    9.250716] sd 6:0:0:0: [sdf] Attached SCSI disk
[   18.246581] Adding 8384508k swap on /dev/sdd5.  Priority:-1 extents:1 across:8384508k FS
[   18.320853] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.350232] systemd-udevd[330]: starting version 204
[   18.561502] lp: driver loaded but no devices found
[   18.567094] ppdev: user-space parallel port driver
[   18.570307] parport_pc 00:05: reported by Plug and Play ACPI
[   18.570360] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   18.572585] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.574063] wmi: Mapper loaded
[   18.579699] ATK0110 ATK0110:00: Overriding interface detection
[   18.588917] [drm] Initialized drm 1.1.0 20060810
[   18.598974] nvidia: module license 'NVIDIA' taints kernel.
[   18.598979] Disabling lock debugging due to kernel taint
[   18.606246] Bluetooth: Core ver 2.17
[   18.606273] NET: Registered protocol family 31
[   18.606274] Bluetooth: HCI device and connection manager initialized
[   18.606283] Bluetooth: HCI socket layer initialized
[   18.606285] Bluetooth: L2CAP socket layer initialized
[   18.606289] Bluetooth: SCO socket layer initialized
[   18.608180] usbcore: registered new interface driver btusb
[   18.609367] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   18.612374] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SOR1 1 (20131115/utaddress-251)
[   18.612381] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SMRG 2 (20131115/utaddress-251)
[   18.612385] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \_SB_.PCI0.SBRG.ASOC.SMRG 3 (20131115/utaddress-251)
[   18.612389] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   18.614927] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   18.615318] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[   18.615325] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  343.36  Mon Dec  1 16:18:58 PST 2014
[   18.623807] Linux video capture interface: v2.00
[   18.631283] MCE: In-kernel MCE decoding enabled.
[   18.633897] EDAC MC: Ver: 3.0.0
[   18.636066] AMD64 EDAC driver v3.4.0
[   18.636088] EDAC amd64: DRAM ECC disabled.
[   18.636094] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   18.636094]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   18.636094]  (Note that use of the override may cause unknown side effects.)
[   18.637054] ivtv: Start initialization, version 1.4.3
[   18.637098] ivtv0: Initializing card 0
[   18.637100] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   18.667464] lp0: using parport0 (interrupt-driven).
[   18.673953] hda_intel: Disabling MSI
[   18.673960] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   18.673985] hda-intel 0000:01:00.1: Disabling 64bit DMA
[   18.678247] kvm: disabled by bios
[   18.694286] hda-intel 0000:01:00.1: Enable delay in RIRB handling
[   18.696057] tveeprom 0-0050: Hauppauge model 32562, rev C168, serial# 7385361
[   18.696060] tveeprom 0-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[   18.696061] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   18.696063] tveeprom 0-0050: audio processor is MSP4448 (idx 27)
[   18.696064] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
[   18.696065] tveeprom 0-0050: has radio
[   18.696067] ivtv0: Autodetected Hauppauge WinTV PVR-250
[   18.701206] type=1400 audit(1435545847.672:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=407 comm="apparmor_parser"
[   18.701212] type=1400 audit(1435545847.672:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=407 comm="apparmor_parser"
[   18.701216] type=1400 audit(1435545847.672:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=407 comm="apparmor_parser"
[   18.701651] type=1400 audit(1435545847.672:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=407 comm="apparmor_parser"
[   18.701656] type=1400 audit(1435545847.672:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=407 comm="apparmor_parser"
[   18.701889] type=1400 audit(1435545847.672:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=407 comm="apparmor_parser"
[   18.704032] type=1400 audit(1435545847.676:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=418 comm="apparmor_parser"
[   18.731427] saa7115 0-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[   18.781707] cx231xx #0: New device Hauppauge Hauppauge Device @ 480 Mbps (2040:b140) with 6 interfaces
[   18.781710] cx231xx #0: registering interface 1
[   18.781828] cx231xx #0: Identified as Hauppauge EXETER (card=8)
[   18.806582] scsi 6:0:0:1: Failed to get diagnostic page 0x8000002
[   18.806644] scsi 6:0:0:1: Failed to bind enclosure -19
[   18.806722] ses 6:0:0:1: Attached Enclosure device
[   18.906042] msp3400 0-0040: MSP4448G-A2 found @ 0x80 (ivtv i2c driver #0)
[   18.906046] msp3400 0-0040: msp3400 supports radio, mode is autodetect and autoselect
[   18.925660] tda9887 0-0043: creating new instance
[   18.925664] tda9887 0-0043: tda988[5/6/7] found
[   18.926757] tuner 0-0043: Tuner 74 found with type(s) Radio TV.
[   18.928396] tuner 0-0061: Tuner -1 found with type(s) Radio TV.
[   18.935102] tuner-simple 0-0061: creating new instance
[   18.935106] tuner-simple 0-0061: type set to 47 (LG NTSC (TAPE series))
[   18.937672] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   18.937720] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   18.937748] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   18.937773] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   18.937799] ivtv0: Registered device radio0 for encoder radio
[   18.937800] ivtv0: Initialized card: Hauppauge WinTV PVR-250
[   18.937825] ivtv: End initialization
[   18.940183] ivtv-alsa: module loading...
[   18.987496] cx231xx #0: cx231xx_dif_set_standard: setStandard to ffffffff
[   19.000510] cx25840 1-0044: cx23102 A/V decoder found @ 0x88 (cx231xx #0)
[   19.018558] cx25840 1-0044:  Firmware download size changed to 16 bytes max length
[   19.491039] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input8
[   19.491119] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input7
[   19.491174] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input6
[   19.491225] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input5
[   19.650240] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   19.847079] ivtv0: Encoder revision: 0x02060039
[   20.081826] EXT4-fs (sdd1): re-mounted. Opts: errors=remount-ro
[   20.243032] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[   20.285322] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   20.322969] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   20.389637] EXT4-fs (sde1): mounted filesystem with ordered data mode. Opts: (null)
[   20.455742] init: failsafe main process (746) killed by TERM signal
[   20.681462] type=1400 audit(1435545849.652:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=839 comm="apparmor_parser"
[   20.681471] type=1400 audit(1435545849.652:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=839 comm="apparmor_parser"
[   20.681743] type=1400 audit(1435545849.652:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=839 comm="apparmor_parser"
[   20.714389] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.714393] Bluetooth: BNEP filters: protocol multicast
[   20.714402] Bluetooth: BNEP socket layer initialized
[   20.716639] Bluetooth: RFCOMM TTY layer initialized
[   20.716646] Bluetooth: RFCOMM socket layer initialized
[   20.716651] Bluetooth: RFCOMM ver 1.11
[   21.150344] cx25840 1-0044: loaded v4l-cx231xx-avcore-01.fw firmware (16382 bytes)
[   21.188310] Chip ID is not zero. It is not a TEA5767
[   21.188318] tuner 2-0060: Tuner -1 found with type(s) Radio TV.
[   21.190975] tda18271 2-0060: creating new instance
[   21.193695] TDA18271HD/C2 detected @ 2-0060
[   21.328241] init: cups main process (884) killed by HUP signal
[   21.328250] init: cups main process ended, respawning
[   21.366757] init: apport-noui (/var/crash/_usr_bin_mythfrontend.real.1000.crash) main process (783) terminated with status 1
[   21.675257] tda18271: performing RF tracking filter calibration
```

3 tuners attached but only 2 were recognized after boot:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-55-generic (buildd@brownie) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #94-Ubuntu SMP Thu Jun 18 00:27:10 UTC 2015 (Ubuntu 3.13.0-55.94-generic 3.13.11-ckt20)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-55-generic root=UUID=dfea8c42-85ad-4d85-9a60-70d7bfd61c3e ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cfe7ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cfe80000-0x00000000cfe97fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cfe98000-0x00000000cfebffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cfec0000-0x00000000cfefffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000022fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: System manufacturer System Product Name/M5A78L-M LX, BIOS 0510    08/15/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x230000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000230000000 aka 8960M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcfe80 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x22fe00000-0x22fffffff]
[    0.000000]  [mem 0x22fe00000-0x22fffffff] page 2M
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x22c000000-0x22fdfffff]
[    0.000000]  [mem 0x22c000000-0x22fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x22bffffff]
[    0.000000]  [mem 0x200000000-0x22bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xcfe7ffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xcfdfffff] page 2M
[    0.000000]  [mem 0xcfe00000-0xcfe7ffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35b46000-0x36d9afff]
[    0.000000] ACPI: RSDP 00000000000fb490 000024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000cfe80100 000054 (v01 081511 XSDT0945 20110815 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cfe80290 0000F4 (v03 081511 FACP0945 20110815 MSFT 00000097)
[    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20131115/tbfadt-603)
[    0.000000] ACPI: DSDT 00000000cfe80460 00D6D6 (v01  A1860 A1860001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cfe98000 000040
[    0.000000] ACPI: APIC 00000000cfe80390 00008C (v01 081511 APIC0945 20110815 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cfe80420 00003C (v01 081511 OEMMCFG  20110815 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cfe98040 000072 (v01 081511 OEMB0945 20110815 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cfe8f460 000038 (v01 081511 OEMHPET  20110815 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cfe8f4a0 0008BC (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000022fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x22fffffff]
[    0.000000]   NODE_DATA [mem 0x22fff9000-0x22fffdfff]
[    0.000000]  [ffffea0000000000-ffffea0008bfffff] PMD -> [ffff880227600000-ffff88022f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x22fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xcfe7ffff]
[    0.000000]   node   0: [mem 0x100000000-0x22fffffff]
[    0.000000] On node 0 totalpages: 2096670
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13242 pages used for memmap
[    0.000000]   DMA32 zone: 847488 pages, LIFO batch:31
[    0.000000]   Normal zone: 19456 pages used for memmap
[    0.000000]   Normal zone: 1245184 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000e3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e4000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcfe80000-0xcfe97fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcfe98000-0xcfebffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcfec0000-0xcfefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcff00000-0xffdfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
[    0.000000] e820: [mem 0xcff00000-0xffdfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88022fc00000 s81536 r8192 d20864 u262144
[    0.000000] pcpu-alloc: s81536 r8192 d20864 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2063887
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-55-generic root=UUID=dfea8c42-85ad-4d85-9a60-70d7bfd61c3e ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 0 size 32 MB
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: [mem 0xc4000000-0xc7ffffff]
[    0.000000] Memory: 8087736K/8386680K available (7392K kernel code, 1146K rwdata, 3408K rodata, 1336K init, 1448K bss, 298944K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.004000] tsc: Fast TSC calibration using PIT
[    0.008000] tsc: Detected 2812.846 MHz processor
[    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5625.69 BogoMIPS (lpj=11251384)
[    0.000007] pid_max: default: 32768 minimum: 301
[    0.000035] Security Framework initialized
[    0.000053] AppArmor: AppArmor initialized
[    0.000054] Yama: becoming mindful.
[    0.000554] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002806] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003849] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.003858] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.004103] Initializing cgroup subsys memory
[    0.004109] Initializing cgroup subsys devices
[    0.004111] Initializing cgroup subsys freezer
[    0.004113] Initializing cgroup subsys blkio
[    0.004114] Initializing cgroup subsys perf_event
[    0.004117] Initializing cgroup subsys hugetlb
[    0.004134] tseg: 0000000000
[    0.004141] CPU: Physical Processor ID: 0
[    0.004142] CPU: Processor Core ID: 0
[    0.004143] mce: CPU supports 6 MCE banks
[    0.004149] LVT offset 0 assigned for vector 0xf9
[    0.004154] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
[    0.004154] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64
[    0.004154] tlb_flushall_shift: 4
[    0.004240] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
[    0.004977] ACPI: Core revision 20131115
[    0.008366] ACPI: All ACPI Tables successfully acquired
[    0.015613] ftrace: allocating 28579 entries in 112 pages
[    0.027133] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066815] smpboot: CPU0: AMD Phenom(tm) II X4 830 Processor (fam: 10, model: 04, stepping: 03)
[    0.171125] Performance Events: AMD PMU driver.
[    0.171129] ... version:                0
[    0.171130] ... bit width:              48
[    0.171131] ... generic registers:      4
[    0.171132] ... value mask:             0000ffffffffffff
[    0.171133] ... max period:             00007fffffffffff
[    0.171133] ... fixed-purpose events:   0
[    0.171134] ... event mask:             000000000000000f
[    0.172620] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.172689] x86: Booting SMP configuration:
[    0.172690] .... node  #0, CPUs:      #1 #2 #3
[    0.211931] x86: Booted up 1 node, 4 CPUs
[    0.211933] smpboot: Total of 4 processors activated (22502.76 BogoMIPS)
[    0.216691] devtmpfs: initialized
[    0.220499] EVM: security.selinux
[    0.220501] EVM: security.SMACK64
[    0.220502] EVM: security.ima
[    0.220502] EVM: security.capability
[    0.220586] PM: Registering ACPI NVS region [mem 0xcfe98000-0xcfebffff] (163840 bytes)
[    0.221483] pinctrl core: initialized pinctrl subsystem
[    0.221541] regulator-dummy: no parameters
[    0.221567] RTC time:  2:57:52, date: 06/29/15
[    0.221603] NET: Registered protocol family 16
[    0.221700] cpuidle: using governor ladder
[    0.221701] cpuidle: using governor menu
[    0.221705] node 0 link 0: io port [1000, ffffff]
[    0.221707] TOM: 00000000d0000000 aka 3328M
[    0.221710] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
[    0.221712] node 0 link 0: mmio [a0000, bffff]
[    0.221714] node 0 link 0: mmio [d0000000, dfffffff]
[    0.221715] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.221717] node 0 link 0: mmio [f0000000, ffdfffff]
[    0.221718] TOM2: 0000000230000000 aka 8960M
[    0.221720] bus: [bus 00-1f] on node 0 link 0
[    0.221721] bus: 00 [io  0x0000-0xffff]
[    0.221722] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.221723] bus: 00 [mem 0xd0000000-0xdfffffff]
[    0.221724] bus: 00 [mem 0xf0000000-0xffffffff]
[    0.221725] bus: 00 [mem 0x230000000-0xfcffffffff]
[    0.221773] ACPI: bus type PCI registered
[    0.221775] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.221828] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.221830] PCI: not using MMCONFIG
[    0.221832] PCI: Using configuration type 1 for base access
[    0.221833] PCI: Using configuration type 1 for extended access
[    0.222007] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.222008] mtrr: probably your BIOS does not setup all CPUs.
[    0.222009] mtrr: corrected configuration.
[    0.222788] bio: create slab <bio-0> at 0
[    0.222941] ACPI: Added _OSI(Module Device)
[    0.222942] ACPI: Added _OSI(Processor Device)
[    0.222943] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.222944] ACPI: Added _OSI(Processor Aggregator Device)
[    0.225293] ACPI: Executed 3 blocks of module-level executable AML code
[    0.299555] ACPI: Interpreter enabled
[    0.299567] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.299579] ACPI: (supports S0 S1 S3 S4 S5)
[    0.299581] ACPI: Using IOAPIC for interrupt routing
[    0.299599] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.300714] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.308959] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.309046] ACPI: No dock devices found.
[    0.360027] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.360033] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.360037] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.360296] PCI host bridge to bus 0000:00
[    0.360299] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.360301] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.360303] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.360304] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.360306] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff]
[    0.360308] pci_bus 0000:00: root bus resource [mem 0xcff00000-0xdfffffff]
[    0.360309] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
[    0.360319] pci 0000:00:00.0: [1022:9600] type 00 class 0x060000
[    0.360405] pci 0000:00:02.0: [1022:9603] type 01 class 0x060400
[    0.360434] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.360470] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.360495] pci 0000:00:04.0: [1022:9604] type 01 class 0x060400
[    0.360523] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.360557] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.360599] pci 0000:00:11.0: [1002:4390] type 00 class 0x01018f
[    0.360618] pci 0000:00:11.0: reg 0x10: [io  0xc000-0xc007]
[    0.360627] pci 0000:00:11.0: reg 0x14: [io  0xb000-0xb003]
[    0.360636] pci 0000:00:11.0: reg 0x18: [io  0xa000-0xa007]
[    0.360645] pci 0000:00:11.0: reg 0x1c: [io  0x9000-0x9003]
[    0.360654] pci 0000:00:11.0: reg 0x20: [io  0x8000-0x800f]
[    0.360663] pci 0000:00:11.0: reg 0x24: [mem 0xfcfffc00-0xfcffffff]
[    0.360682] pci 0000:00:11.0: set SATA to AHCI mode
[    0.360766] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.360779] pci 0000:00:12.0: reg 0x10: [mem 0xfcffe000-0xfcffefff]
[    0.360862] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.360889] pci 0000:00:12.1: [1002:4398] type 00 class 0x0c0310
[    0.360902] pci 0000:00:12.1: reg 0x10: [mem 0xfcffd000-0xfcffdfff]
[    0.360986] pci 0000:00:12.1: System wakeup disabled by ACPI
[    0.361015] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.361033] pci 0000:00:12.2: reg 0x10: [mem 0xfcfff800-0xfcfff8ff]
[    0.361112] pci 0000:00:12.2: supports D1 D2
[    0.361113] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.361150] pci 0000:00:12.2: System wakeup disabled by ACPI
[    0.361179] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.361191] pci 0000:00:13.0: reg 0x10: [mem 0xfcffc000-0xfcffcfff]
[    0.361274] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.361297] pci 0000:00:13.1: [1002:4398] type 00 class 0x0c0310
[    0.361309] pci 0000:00:13.1: reg 0x10: [mem 0xfcffb000-0xfcffbfff]
[    0.361392] pci 0000:00:13.1: System wakeup disabled by ACPI
[    0.361420] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.361438] pci 0000:00:13.2: reg 0x10: [mem 0xfcfff400-0xfcfff4ff]
[    0.361517] pci 0000:00:13.2: supports D1 D2
[    0.361519] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.361555] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.361588] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.361722] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
[    0.361738] pci 0000:00:14.1: reg 0x10: [io  0x0000-0x0007]
[    0.361746] pci 0000:00:14.1: reg 0x14: [io  0x0000-0x0003]
[    0.361755] pci 0000:00:14.1: reg 0x18: [io  0x0000-0x0007]
[    0.361764] pci 0000:00:14.1: reg 0x1c: [io  0x0000-0x0003]
[    0.361773] pci 0000:00:14.1: reg 0x20: [io  0xff00-0xff0f]
[    0.361865] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.361977] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.362039] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.362063] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.362076] pci 0000:00:14.5: reg 0x10: [mem 0xfcffa000-0xfcffafff]
[    0.362159] pci 0000:00:14.5: System wakeup disabled by ACPI
[    0.362187] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
[    0.362239] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
[    0.362289] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
[    0.362338] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
[    0.362390] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
[    0.362481] pci 0000:01:00.0: [10de:0de1] type 00 class 0x030000
[    0.362490] pci 0000:01:00.0: reg 0x10: [mem 0xfd000000-0xfdffffff]
[    0.362499] pci 0000:01:00.0: reg 0x14: [mem 0xd8000000-0xdfffffff 64bit pref]
[    0.362509] pci 0000:01:00.0: reg 0x1c: [mem 0xd6000000-0xd7ffffff 64bit pref]
[    0.362515] pci 0000:01:00.0: reg 0x24: [io  0xdc00-0xdc7f]
[    0.362522] pci 0000:01:00.0: reg 0x30: [mem 0xfeb00000-0xfeb7ffff pref]
[    0.362588] pci 0000:01:00.1: [10de:0bea] type 00 class 0x040300
[    0.362597] pci 0000:01:00.1: reg 0x10: [mem 0xfebf8000-0xfebfbfff]
[    0.367100] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.367105] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.367108] pci 0000:00:02.0:   bridge window [mem 0xfd000000-0xfebfffff]
[    0.367111] pci 0000:00:02.0:   bridge window [mem 0xd6000000-0xdfffffff 64bit pref]
[    0.367170] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
[    0.367182] pci 0000:02:00.0: reg 0x10: [io  0xe800-0xe8ff]
[    0.367202] pci 0000:02:00.0: reg 0x18: [mem 0xf7fff000-0xf7ffffff 64bit pref]
[    0.367215] pci 0000:02:00.0: reg 0x20: [mem 0xf7ff8000-0xf7ffbfff 64bit pref]
[    0.367266] pci 0000:02:00.0: supports D1 D2
[    0.367268] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.367295] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.375104] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.375109] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.375112] pci 0000:00:04.0:   bridge window [mem 0xf7f00000-0xf7ffffff 64bit pref]
[    0.375159] pci 0000:03:05.0: [4444:0016] type 00 class 0x040000
[    0.375181] pci 0000:03:05.0: reg 0x10: [mem 0xf8000000-0xfbffffff pref]
[    0.375342] pci 0000:00:14.4: PCI bridge to [bus 03] (subtractive decode)
[    0.375350] pci 0000:00:14.4:   bridge window [mem 0xf8000000-0xfbffffff pref]
[    0.375352] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.375354] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.375355] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.375357] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.375359] pci 0000:00:14.4:   bridge window [mem 0xcff00000-0xdfffffff] (subtractive decode)
[    0.375360] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.391161] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 12 14 15)
[    0.391199] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
[    0.391233] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.391266] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.391299] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 *10 11 12 14 15)
[    0.391332] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.391365] ACPI: PCI Interrupt Link [LNKG] (IRQs *11)
[    0.391397] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.391543] ACPI: Enabled 1 GPEs in block 00 to 1F
[    0.391548] ACPI: \_SB_.PCI0: notify handler is installed
[    0.391581] Found 1 acpi root devices
[    0.391671] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.391673] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.391674] vgaarb: loaded
[    0.391675] vgaarb: bridge control possible 0000:01:00.0
[    0.391822] SCSI subsystem initialized
[    0.391883] libata version 3.00 loaded.
[    0.391900] ACPI: bus type USB registered
[    0.391914] usbcore: registered new interface driver usbfs
[    0.391920] usbcore: registered new interface driver hub
[    0.391941] usbcore: registered new device driver usb
[    0.392048] PCI: Using ACPI for IRQ routing
[    0.400308] PCI: pci_cache_line_size set to 64 bytes
[    0.400356] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.400358] e820: reserve RAM buffer [mem 0xcfe80000-0xcfffffff]
[    0.400427] NetLabel: Initializing
[    0.400428] NetLabel:  domain hash size = 128
[    0.400429] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.400439] NetLabel:  unlabeled traffic allowed by default
[    0.400499] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.400502] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.402560] Switched to clocksource hpet
[    0.406755] AppArmor: AppArmor Filesystem Enabled
[    0.406775] pnp: PnP ACPI init
[    0.406785] ACPI: bus type PNP registered
[    0.406904] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.406935] pnp 00:01: [dma 4]
[    0.406951] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.406979] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.406996] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.407016] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.407452] pnp 00:05: [dma 0 disabled]
[    0.407602] pnp 00:05: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.407643] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.407966] pnp 00:07: [dma 0 disabled]
[    0.408026] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.408104] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.408106] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.408109] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.408288] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.408290] system 00:09: [io  0x040b] has been reserved
[    0.408292] system 00:09: [io  0x04d6] has been reserved
[    0.408294] system 00:09: [io  0x0c00-0x0c01] has been reserved
[    0.408296] system 00:09: [io  0x0c14] has been reserved
[    0.408298] system 00:09: [io  0x0c50-0x0c51] has been reserved
[    0.408300] system 00:09: [io  0x0c52] has been reserved
[    0.408301] system 00:09: [io  0x0c6c] has been reserved
[    0.408303] system 00:09: [io  0x0c6f] has been reserved
[    0.408305] system 00:09: [io  0x0cd0-0x0cd1] has been reserved
[    0.408307] system 00:09: [io  0x0cd2-0x0cd3] has been reserved
[    0.408309] system 00:09: [io  0x0cd4-0x0cd5] has been reserved
[    0.408310] system 00:09: [io  0x0cd6-0x0cd7] has been reserved
[    0.408312] system 00:09: [io  0x0cd8-0x0cdf] has been reserved
[    0.408314] system 00:09: [io  0x0b00-0x0b3f] has been reserved
[    0.408316] system 00:09: [io  0x0800-0x089f] could not be reserved
[    0.408318] system 00:09: [io  0x0b00-0x0b0f] has been reserved
[    0.408319] system 00:09: [io  0x0b20-0x0b3f] has been reserved
[    0.408321] system 00:09: [io  0x0900-0x090f] has been reserved
[    0.408323] system 00:09: [io  0x0910-0x091f] has been reserved
[    0.408325] system 00:09: [io  0xfe00-0xfefe] has been reserved
[    0.408327] system 00:09: [mem 0xcff00000-0xcfffffff] has been reserved
[    0.408329] system 00:09: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.408331] system 00:09: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.408333] system 00:09: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.408335] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.408468] system 00:0a: [io  0x0230-0x023f] has been reserved
[    0.408471] system 00:0a: [io  0x0290-0x029f] has been reserved
[    0.408472] system 00:0a: [io  0x0300-0x030f] has been reserved
[    0.408474] system 00:0a: [io  0x0a30-0x0a3f] has been reserved
[    0.408476] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.408520] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.408522] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.422726] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.422730] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.422732] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.422734] system 00:0c: [mem 0x00100000-0xcfefffff] could not be reserved
[    0.422735] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.422738] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.422817] pnp: PnP ACPI: found 13 devices
[    0.422818] ACPI: bus type PNP unregistered
[    0.429026] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.429029] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.429032] pci 0000:00:02.0:   bridge window [mem 0xfd000000-0xfebfffff]
[    0.429034] pci 0000:00:02.0:   bridge window [mem 0xd6000000-0xdfffffff 64bit pref]
[    0.429037] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.429039] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.429042] pci 0000:00:04.0:   bridge window [mem 0xf7f00000-0xf7ffffff 64bit pref]
[    0.429045] pci 0000:00:14.4: PCI bridge to [bus 03]
[    0.429052] pci 0000:00:14.4:   bridge window [mem 0xf8000000-0xfbffffff pref]
[    0.429058] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.429060] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.429062] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.429063] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.429065] pci_bus 0000:00: resource 8 [mem 0xcff00000-0xdfffffff]
[    0.429066] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.429068] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.429070] pci_bus 0000:01: resource 1 [mem 0xfd000000-0xfebfffff]
[    0.429071] pci_bus 0000:01: resource 2 [mem 0xd6000000-0xdfffffff 64bit pref]
[    0.429073] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.429075] pci_bus 0000:02: resource 2 [mem 0xf7f00000-0xf7ffffff 64bit pref]
[    0.429077] pci_bus 0000:03: resource 2 [mem 0xf8000000-0xfbffffff pref]
[    0.429078] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.429080] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.429082] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.429083] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.429085] pci_bus 0000:03: resource 8 [mem 0xcff00000-0xdfffffff]
[    0.429086] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.429114] NET: Registered protocol family 2
[    0.429331] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.429521] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.429795] TCP: Hash tables configured (established 65536 bind 65536)
[    0.429835] TCP: reno registered
[    0.429846] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.429895] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.429989] NET: Registered protocol family 1
[    0.874591] pci 0000:01:00.0: Video device with shadowed ROM
[    0.874606] PCI: CLS 64 bytes, default 64
[    0.874659] Trying to unpack rootfs image as initramfs...
[    1.157830] Freeing initrd memory: 18772K (ffff880035b46000 - ffff880036d9b000)
[    1.158068] PCI-DMA: Disabling AGP.
[    1.158152] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.158154] PCI-DMA: using GART IOMMU.
[    1.158156] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.161472] LVT offset 1 assigned for vector 0x400
[    1.161480] IBS: LVT offset 1 assigned
[    1.161505] perf: AMD IBS detected (0x0000001f)
[    1.161543] microcode: CPU0: patch_level=0x010000c8
[    1.161550] microcode: CPU1: patch_level=0x010000c8
[    1.161561] microcode: CPU2: patch_level=0x010000c8
[    1.161571] microcode: CPU3: patch_level=0x010000c8
[    1.161631] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.161632] Scanning for low memory corruption every 60 seconds
[    1.161840] Initialise system trusted keyring
[    1.161882] audit: initializing netlink socket (disabled)
[    1.161892] type=2000 audit(1435546673.052:1): initialized
[    1.187836] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.189051] zbud: loaded
[    1.189195] VFS: Disk quotas dquot_6.5.2
[    1.189235] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.189680] fuse init (API version 7.22)
[    1.189741] msgmni has been set to 15961
[    1.189789] Key type big_key registered
[    1.190213] Key type asymmetric registered
[    1.190217] Asymmetric key parser 'x509' registered
[    1.190264] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.190309] io scheduler noop registered
[    1.190310] io scheduler deadline registered (default)
[    1.190333] io scheduler cfq registered
[    1.190533] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.190644] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
[    1.190689] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.190700] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.190737] ipmi message handler version 39.2
[    1.190793] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.190796] ACPI: Power Button [PWRB]
[    1.190823] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.190825] ACPI: Power Button [PWRF]
[    1.191647] GHES: HEST is not enabled!
[    1.191740] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.212204] 00:07: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.213347] Linux agpgart interface v0.103
[    1.214528] brd: module loaded
[    1.215140] loop: module loaded
[    1.215447] libphy: Fixed MDIO Bus: probed
[    1.215518] tun: Universal TUN/TAP device driver, 1.6
[    1.215519] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.215555] PPP generic driver version 2.4.2
[    1.215590] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.215593] ehci-pci: EHCI PCI platform driver
[    1.215703] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.215709] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.215712] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.215723] ehci-pci 0000:00:12.2: debug port 1
[    1.215763] ehci-pci 0000:00:12.2: irq 17, io mem 0xfcfff800
[    1.226429] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.226470] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.226472] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.226474] usb usb1: Product: EHCI Host Controller
[    1.226475] usb usb1: Manufacturer: Linux 3.13.0-55-generic ehci_hcd
[    1.226477] usb usb1: SerialNumber: 0000:00:12.2
[    1.226584] hub 1-0:1.0: USB hub found
[    1.226591] hub 1-0:1.0: 6 ports detected
[    1.226804] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.226808] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.226811] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.226822] ehci-pci 0000:00:13.2: debug port 1
[    1.226859] ehci-pci 0000:00:13.2: irq 19, io mem 0xfcfff400
[    1.238424] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.238462] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.238464] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.238466] usb usb2: Product: EHCI Host Controller
[    1.238467] usb usb2: Manufacturer: Linux 3.13.0-55-generic ehci_hcd
[    1.238469] usb usb2: SerialNumber: 0000:00:13.2
[    1.238588] hub 2-0:1.0: USB hub found
[    1.238595] hub 2-0:1.0: 6 ports detected
[    1.238693] ehci-platform: EHCI generic platform driver
[    1.238700] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.238701] ohci-pci: OHCI PCI platform driver
[    1.238806] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.238810] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.238833] ohci-pci 0000:00:12.0: irq 16, io mem 0xfcffe000
[    1.298411] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.298413] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.298415] usb usb3: Product: OHCI PCI host controller
[    1.298416] usb usb3: Manufacturer: Linux 3.13.0-55-generic ohci_hcd
[    1.298418] usb usb3: SerialNumber: 0000:00:12.0
[    1.298525] hub 3-0:1.0: USB hub found
[    1.298532] hub 3-0:1.0: 3 ports detected
[    1.298682] ohci-pci 0000:00:12.1: OHCI PCI host controller
[    1.298686] ohci-pci 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.298699] ohci-pci 0000:00:12.1: irq 16, io mem 0xfcffd000
[    1.358397] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.358399] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.358401] usb usb4: Product: OHCI PCI host controller
[    1.358402] usb usb4: Manufacturer: Linux 3.13.0-55-generic ohci_hcd
[    1.358404] usb usb4: SerialNumber: 0000:00:12.1
[    1.358508] hub 4-0:1.0: USB hub found
[    1.358515] hub 4-0:1.0: 3 ports detected
[    1.358663] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.358667] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.358689] ohci-pci 0000:00:13.0: irq 18, io mem 0xfcffc000
[    1.418385] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.418387] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.418389] usb usb5: Product: OHCI PCI host controller
[    1.418390] usb usb5: Manufacturer: Linux 3.13.0-55-generic ohci_hcd
[    1.418391] usb usb5: SerialNumber: 0000:00:13.0
[    1.418495] hub 5-0:1.0: USB hub found
[    1.418504] hub 5-0:1.0: 3 ports detected
[    1.418655] ohci-pci 0000:00:13.1: OHCI PCI host controller
[    1.418659] ohci-pci 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.418671] ohci-pci 0000:00:13.1: irq 18, io mem 0xfcffb000
[    1.478378] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.478380] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.478382] usb usb6: Product: OHCI PCI host controller
[    1.478383] usb usb6: Manufacturer: Linux 3.13.0-55-generic ohci_hcd
[    1.478385] usb usb6: SerialNumber: 0000:00:13.1
[    1.478487] hub 6-0:1.0: USB hub found
[    1.478494] hub 6-0:1.0: 3 ports detected
[    1.478649] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    1.478653] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.478665] ohci-pci 0000:00:14.5: irq 18, io mem 0xfcffa000
[    1.538374] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.538376] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.538378] usb usb7: Product: OHCI PCI host controller
[    1.538379] usb usb7: Manufacturer: Linux 3.13.0-55-generic ohci_hcd
[    1.538382] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.538383] usb usb7: SerialNumber: 0000:00:14.5
[    1.538475] hub 7-0:1.0: USB hub found
[    1.538483] hub 7-0:1.0: 2 ports detected
[    1.538537] ohci-platform: OHCI generic platform driver
[    1.538544] uhci_hcd: USB Universal Host Controller Interface driver
[    1.538589] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.538958] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.538964] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.539054] mousedev: PS/2 mouse device common for all mice
[    1.539157] rtc_cmos 00:02: RTC can wake from S4
[    1.539257] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.539281] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.539336] device-mapper: uevent: version 1.0.3
[    1.539384] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.539390] ledtrig-cpu: registered to indicate activity on CPUs
[    1.539477] TCP: cubic registered
[    1.539538] NET: Registered protocol family 10
[    1.539668] NET: Registered protocol family 17
[    1.539676] Key type dns_resolver registered
[    1.539899] Loading compiled-in X.509 certificates
[    1.540865] Loaded X.509 cert 'Magrathea: Glacier signing key: 13dfa511f14d8706c6ace27e0c6a7d1469b9ea7f'
[    1.540873] registered taskstats version 1
[    1.543006] Key type trusted registered
[    1.545961] Key type encrypted registered
[    1.545965] AppArmor: AppArmor sha1 policy hashing enabled
[    1.545967] IMA: No TPM chip found, activating TPM-bypass!
[    1.546177] regulator-dummy: disabling
[    1.546222]   Magic number: 3:830:966
[    1.546269] memory memory17: hash matches
[    1.546308] rtc_cmos 00:02: setting system clock to 2015-06-29 02:57:53 UTC (1435546673)
[    1.546402] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.546787] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.546788] EDD information not available.
[    1.546807] PM: Hibernation image not present or could not be loaded.
[    1.548381] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    1.548383] Write protecting the kernel read-only data: 12288k
[    1.550476] Freeing unused kernel memory: 788K (ffff88000173b000 - ffff880001800000)
[    1.552198] Freeing unused kernel memory: 688K (ffff880001b54000 - ffff880001c00000)
[    1.562528] systemd-udevd[121]: starting version 204
[    1.577838] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.577849] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.577982] ahci 0000:00:11.0: version 3.0
[    1.578063] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.578187] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.578190] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.578214] r8169 0000:02:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000c64000, 54:04:a6:82:07:03, XID 0c900800 IRQ 42
[    1.578217] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.578917] scsi0 : ahci
[    1.578998] scsi1 : ahci
[    1.579312] scsi2 : ahci
[    1.579388] scsi3 : ahci
[    1.579439] ata1: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffd00 irq 22
[    1.579442] ata2: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffd80 irq 22
[    1.579445] ata3: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffe00 irq 22
[    1.579447] ata4: SATA max UDMA/133 abar m1024@0xfcfffc00 port 0xfcfffe80 irq 22
[    1.582515] scsi4 : pata_atiixp
[    1.582592] scsi5 : pata_atiixp
[    1.582634] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.582636] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.673252] usb 1-1: New USB device found, idVendor=2040, idProduct=b140
[    1.673256] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.673258] usb 1-1: Product: Hauppauge Device
[    1.673259] usb 1-1: Manufacturer: Hauppauge
[    1.673261] usb 1-1: SerialNumber: 4034729194
[    1.762857] ata6.00: ATA-9: ST3000DM001-1ER166, CC25, max UDMA/133
[    1.762860] ata6.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.762867] ata6.01: ATAPI: TSSTcorp CDDVDW SH-222AB, SB00, max UDMA/100
[    1.778843] ata6.00: configured for UDMA/100
[    1.790331] usb 1-2: new high-speed USB device number 3 using ehci-pci
[    1.794637] ata6.01: configured for UDMA/100
[    1.956381] usb 1-2: New USB device found, idVendor=1058, idProduct=1230
[    1.956384] usb 1-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[    1.956385] usb 1-2: Product: My Book 1230
[    1.956387] usb 1-2: Manufacturer: Western Digital
[    1.956388] usb 1-2: SerialNumber: 5743433445364C5658553133
[    2.066278] usb 1-3: new high-speed USB device number 4 using ehci-pci
[    2.070278] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.070303] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.070328] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.070353] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.071010] ata4.00: ATA-8: ST1000DL002-9TT153, CC32, max UDMA/133
[    2.071012] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.071299] ata1.00: ATA-9: ST3000DM001-1CH166, CC27, max UDMA/133
[    2.071300] ata1.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.071350] ata2.00: ATA-9: ST3000DM001-1CH166, CC27, max UDMA/133
[    2.071352] ata2.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.071750] ata4.00: configured for UDMA/133
[    2.071897] ata1.00: configured for UDMA/133
[    2.071957] ata2.00: configured for UDMA/133
[    2.072031] scsi 0:0:0:0: Direct-Access     ATA      ST3000DM001-1CH1 CC27 PQ: 0 ANSI: 5
[    2.072159] sd 0:0:0:0: [sda] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.072161] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.072182] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.072283] sd 0:0:0:0: [sda] Write Protect is off
[    2.072287] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.072311] scsi 1:0:0:0: Direct-Access     ATA      ST3000DM001-1CH1 CC27 PQ: 0 ANSI: 5
[    2.072329] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.072434] sd 1:0:0:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.072436] sd 1:0:0:0: [sdb] 4096-byte physical blocks
[    2.072447] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.072484] sd 1:0:0:0: [sdb] Write Protect is off
[    2.072487] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.072524] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.073173] ata3.00: LPM support broken, forcing max_power
[    2.074487] ata3.00: ATA-6: WDC WD2500JD-22HBB0, 08.02D08, max UDMA/133
[    2.074490] ata3.00: 488397168 sectors, multi 16: LBA48 
[    2.078675] ata3.00: LPM support broken, forcing max_power
[    2.079994] ata3.00: configured for UDMA/133
[    2.094363] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500JD-22H 08.0 PQ: 0 ANSI: 5
[    2.094475] sd 2:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.094489] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.094501] sd 2:0:0:0: [sdc] Write Protect is off
[    2.094504] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.094516] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.094593] scsi 3:0:0:0: Direct-Access     ATA      ST1000DL002-9TT1 CC32 PQ: 0 ANSI: 5
[    2.094706] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    2.094739] sd 3:0:0:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.094823] sd 3:0:0:0: [sdd] Write Protect is off
[    2.094825] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.094828] scsi 5:0:0:0: Direct-Access     ATA      ST3000DM001-1ER1 CC25 PQ: 0 ANSI: 5
[    2.094857] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.094933] sd 5:0:0:0: [sde] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    2.094936] sd 5:0:0:0: [sde] 4096-byte physical blocks
[    2.094981] sd 5:0:0:0: Attached scsi generic sg4 type 0
[    2.095008] sd 5:0:0:0: [sde] Write Protect is off
[    2.095010] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    2.095045] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.095707] scsi 5:0:1:0: CD-ROM            TSSTcorp CDDVDW SH-222AB  SB00 PQ: 0 ANSI: 5
[    2.098313] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.098316] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.098413] sr 5:0:1:0: Attached scsi CD-ROM sr0
[    2.098474] sr 5:0:1:0: Attached scsi generic sg5 type 5
[    2.107900]  sdc: sdc1
[    2.108063] sd 2:0:0:0: [sdc] Attached SCSI disk
[    2.119595]  sda: sda1
[    2.119889] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.120016]  sdb: sdb1
[    2.120248] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.139682]  sdd: sdd1 sdd2 < sdd5 >
[    2.140033] sd 3:0:0:0: [sdd] Attached SCSI disk
[    2.158238] tsc: Refined TSC clocksource calibration: 2812.627 MHz
[    2.163785]  sde: sde1
[    2.164069] sd 5:0:0:0: [sde] Attached SCSI disk
[    2.205055] usb 1-3: New USB device found, idVendor=2040, idProduct=b140
[    2.205059] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.205061] usb 1-3: Product: Hauppauge Device
[    2.205063] usb 1-3: Manufacturer: Hauppauge
[    2.205064] usb 1-3: SerialNumber: 4034729253
[    2.322227] usb 1-4: new high-speed USB device number 5 using ehci-pci
[    2.349746] random: nonblocking pool is initialized
[    2.457087] usb 1-4: New USB device found, idVendor=2040, idProduct=b140
[    2.457091] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.457093] usb 1-4: Product: Hauppauge Device
[    2.457094] usb 1-4: Manufacturer: Hauppauge
[    2.457096] usb 1-4: SerialNumber: 4034729515
[    2.469026] usb-storage 1-2:1.0: USB Mass Storage device detected
[    2.469123] scsi6 : usb-storage 1-2:1.0
[    2.469220] usbcore: registered new interface driver usb-storage
[    2.828244] EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: (null)
[    2.990108] usb 6-1: new full-speed USB device number 2 using ohci-pci
[    3.158111] Switched to clocksource tsc
[    3.165007] usb 6-1: New USB device found, idVendor=0a5c, idProduct=2101
[    3.165011] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.165013] usb 6-1: Product: BCM2045A
[    3.165014] usb 6-1: Manufacturer: Broadcom Corp
[    3.165016] usb 6-1: SerialNumber: 00027210092C
[    3.466849] scsi 6:0:0:0: Direct-Access     WD       My Book 1230     1065 PQ: 0 ANSI: 6
[    3.467596] scsi 6:0:0:1: Enclosure         WD       SES Device       1065 PQ: 0 ANSI: 6
[    3.467795] sd 6:0:0:0: Attached scsi generic sg6 type 0
[    3.467875] scsi 6:0:0:1: Attached scsi generic sg7 type 13
[    3.471459] sd 6:0:0:0: [sdf] Spinning up disk...
[    4.579484] init: plymouth-upstart-bridge main process (199) terminated with status 1
[    4.579495] init: plymouth-upstart-bridge main process ended, respawning
[    4.581275] init: plymouth-upstart-bridge main process (213) terminated with status 1
[    4.581284] init: plymouth-upstart-bridge main process ended, respawning
[    4.582648] init: plymouth-upstart-bridge main process (215) terminated with status 1
[    4.582656] init: plymouth-upstart-bridge main process ended, respawning
[    4.584349] init: plymouth-upstart-bridge main process (216) terminated with status 1
[    4.584357] init: plymouth-upstart-bridge main process ended, respawning
[    4.585690] init: plymouth-upstart-bridge main process (218) terminated with status 1
[    4.585697] init: plymouth-upstart-bridge main process ended, respawning
[    4.587364] init: plymouth-upstart-bridge main process (219) terminated with status 1
[    4.587373] init: plymouth-upstart-bridge main process ended, respawning
[    4.588696] init: plymouth-upstart-bridge main process (221) terminated with status 1
[    4.588703] init: plymouth-upstart-bridge main process ended, respawning
[    4.590342] init: plymouth-upstart-bridge main process (222) terminated with status 1
[    4.590351] init: plymouth-upstart-bridge main process ended, respawning
[    4.591879] init: plymouth-upstart-bridge main process (224) terminated with status 1
[    4.591886] init: plymouth-upstart-bridge main process ended, respawning
[    4.593533] init: plymouth-upstart-bridge main process (225) terminated with status 1
[    4.593541] init: plymouth-upstart-bridge main process ended, respawning
[    4.594855] init: plymouth-upstart-bridge main process (227) terminated with status 1
[    4.594862] init: plymouth-upstart-bridge respawning too fast, stopped
[    4.473765] .....ready
[    8.668298] sd 6:0:0:0: [sdf] 976746240 4096-byte logical blocks: (4.00 TB/3.63 TiB)
[    8.669551] sd 6:0:0:0: [sdf] Write Protect is off
[    8.669556] sd 6:0:0:0: [sdf] Mode Sense: 53 00 10 08
[    8.670800] sd 6:0:0:0: [sdf] No Caching mode page found
[    8.670804] sd 6:0:0:0: [sdf] Assuming drive cache: write through
[    8.671541] sd 6:0:0:0: [sdf] 976746240 4096-byte logical blocks: (4.00 TB/3.63 TiB)
[    8.674048] sd 6:0:0:0: [sdf] No Caching mode page found
[    8.674052] sd 6:0:0:0: [sdf] Assuming drive cache: write through
[    8.770150]  sdf: sdf1
[    8.771141] sd 6:0:0:0: [sdf] 976746240 4096-byte logical blocks: (4.00 TB/3.63 TiB)
[    8.773637] sd 6:0:0:0: [sdf] No Caching mode page found
[    8.773640] sd 6:0:0:0: [sdf] Assuming drive cache: write through
[    8.773642] sd 6:0:0:0: [sdf] Attached SCSI disk
[   18.158915] Adding 8384508k swap on /dev/sdd5.  Priority:-1 extents:1 across:8384508k FS
[   18.233487] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.262574] systemd-udevd[330]: starting version 204
[   18.393042] lp: driver loaded but no devices found
[   18.398582] ppdev: user-space parallel port driver
[   18.402318] parport_pc 00:05: reported by Plug and Play ACPI
[   18.402370] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   18.500735] lp0: using parport0 (interrupt-driven).
[   18.502424] wmi: Mapper loaded
[   18.512639] ATK0110 ATK0110:00: Overriding interface detection
[   18.515298] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.526525] [drm] Initialized drm 1.1.0 20060810
[   18.537976] nvidia: module license 'NVIDIA' taints kernel.
[   18.537980] Disabling lock debugging due to kernel taint
[   18.545883] Bluetooth: Core ver 2.17
[   18.545927] NET: Registered protocol family 31
[   18.545929] Bluetooth: HCI device and connection manager initialized
[   18.545938] Bluetooth: HCI socket layer initialized
[   18.545940] Bluetooth: L2CAP socket layer initialized
[   18.545944] Bluetooth: SCO socket layer initialized
[   18.546213] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   18.551583] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   18.552102] usbcore: registered new interface driver btusb
[   18.552408] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[   18.552416] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  343.36  Mon Dec  1 16:18:58 PST 2014
[   18.554715] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SOR1 1 (20131115/utaddress-251)
[   18.554721] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \SMRG 2 (20131115/utaddress-251)
[   18.554724] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \_SB_.PCI0.SBRG.ASOC.SMRG 3 (20131115/utaddress-251)
[   18.554727] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   18.565188] Linux video capture interface: v2.00
[   18.565201] MCE: In-kernel MCE decoding enabled.
[   18.567249] EDAC MC: Ver: 3.0.0
[   18.580321] hda_intel: Disabling MSI
[   18.580327] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   18.580361] hda-intel 0000:01:00.1: Disabling 64bit DMA
[   18.581272] ivtv: Start initialization, version 1.4.3
[   18.581313] ivtv0: Initializing card 0
[   18.581315] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   18.584044] hda-intel 0000:01:00.1: Enable delay in RIRB handling
[   18.593774] kvm: disabled by bios
[   18.603460] AMD64 EDAC driver v3.4.0
[   18.603486] EDAC amd64: DRAM ECC disabled.
[   18.603491] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   18.603491]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   18.603491]  (Note that use of the override may cause unknown side effects.)
[   18.630134] type=1400 audit(1435546690.582:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=410 comm="apparmor_parser"
[   18.630140] type=1400 audit(1435546690.582:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=410 comm="apparmor_parser"
[   18.630144] type=1400 audit(1435546690.582:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=410 comm="apparmor_parser"
[   18.630595] type=1400 audit(1435546690.582:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=410 comm="apparmor_parser"
[   18.630599] type=1400 audit(1435546690.582:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=410 comm="apparmor_parser"
[   18.630832] type=1400 audit(1435546690.582:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=410 comm="apparmor_parser"
[   18.632983] type=1400 audit(1435546690.586:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=411 comm="apparmor_parser"
[   18.643059] tveeprom 0-0050: Hauppauge model 32562, rev C168, serial# 7385361
[   18.643062] tveeprom 0-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[   18.643064] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   18.643066] tveeprom 0-0050: audio processor is MSP4448 (idx 27)
[   18.643067] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
[   18.643068] tveeprom 0-0050: has radio
[   18.643070] ivtv0: Autodetected Hauppauge WinTV PVR-250
[   18.675730] saa7115 0-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[   18.797912] cx231xx #0: New device Hauppauge Hauppauge Device @ 480 Mbps (2040:b140) with 6 interfaces
[   18.797915] cx231xx #0: registering interface 1
[   18.798634] cx231xx #0: Identified as Hauppauge EXETER (card=8)
[   18.835906] msp3400 0-0040: MSP4448G-A2 found @ 0x80 (ivtv i2c driver #0)
[   18.835909] msp3400 0-0040: msp3400 supports radio, mode is autodetect and autoselect
[   18.842188] scsi 6:0:0:1: Failed to get diagnostic page 0x8000002
[   18.842245] scsi 6:0:0:1: Failed to bind enclosure -19
[   18.842312] ses 6:0:0:1: Attached Enclosure device
[   18.852407] tda9887 0-0043: creating new instance
[   18.852410] tda9887 0-0043: tda988[5/6/7] found
[   18.853516] tuner 0-0043: Tuner 74 found with type(s) Radio TV.
[   18.854838] tuner 0-0061: Tuner -1 found with type(s) Radio TV.
[   18.861145] tuner-simple 0-0061: creating new instance
[   18.861148] tuner-simple 0-0061: type set to 47 (LG NTSC (TAPE series))
[   18.863734] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   18.863762] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   18.863786] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   18.863812] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   18.863836] ivtv0: Registered device radio0 for encoder radio
[   18.863837] ivtv0: Initialized card: Hauppauge WinTV PVR-250
[   18.863862] ivtv: End initialization
[   18.866253] ivtv-alsa: module loading...
[   19.006985] cx231xx #0: cx231xx_dif_set_standard: setStandard to ffffffff
[   19.019629] cx25840 1-0044: cx23102 A/V decoder found @ 0x88 (cx231xx #0)
[   19.037660] cx25840 1-0044:  Firmware download size changed to 16 bytes max length
[   19.398879] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input8
[   19.398956] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input7
[   19.399006] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input6
[   19.399051] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input5
[   19.632306] EXT4-fs (sdd1): re-mounted. Opts: errors=remount-ro
[   19.811446] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   19.856156] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   19.889811] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[   19.960554] EXT4-fs (sde1): mounted filesystem with ordered data mode. Opts: (null)
[   20.191603] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.191606] Bluetooth: BNEP filters: protocol multicast
[   20.191614] Bluetooth: BNEP socket layer initialized
[   20.193770] Bluetooth: RFCOMM TTY layer initialized
[   20.193778] Bluetooth: RFCOMM socket layer initialized
[   20.193784] Bluetooth: RFCOMM ver 1.11
[   20.340522] type=1400 audit(1435546692.294:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=676 comm="apparmor_parser"
[   20.340530] type=1400 audit(1435546692.294:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=676 comm="apparmor_parser"
[   20.340959] type=1400 audit(1435546692.294:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=676 comm="apparmor_parser"
[   20.422482] init: cups main process (677) killed by HUP signal
[   20.422491] init: cups main process ended, respawning
[   20.517413] init: apport-noui (/var/crash/_usr_bin_mythfrontend.real.1000.crash) main process (645) terminated with status 1
[   21.361882] cx25840 1-0044: loaded v4l-cx231xx-avcore-01.fw firmware (16382 bytes)
[   21.400604] All bytes are equal. It is not a TEA5767
[   21.400610] tuner 2-0060: Tuner -1 found with type(s) Radio TV.
[   21.403330] tda18271 2-0060: creating new instance
[   21.405990] Unknown device (0) detected @ 2-0060, device not supported.
[   21.405993] tda18271_attach: [2-0060|M] error -22 on line 1285
[   21.406047] tda18271 2-0060: destroying instance
[   21.411490] tuner 2-0060: Tuner has no way to set tv freq
[   21.412613] cx231xx #0: cx231xx #0: v4l2 driver version 0.0.2
[   21.429356] cx231xx #0: cx231xx_dif_set_standard: setStandard to ff
[   21.517949] cx231xx #0: video_mux : 0
[   21.517952] cx231xx #0: do_mode_ctrl_overrides : 0xff
[   21.518685] cx231xx #0: do_mode_ctrl_overrides PAL
[   21.544690] tuner 2-0060: Tuner has no way to set tv freq
[   21.544776] cx231xx #0: cx231xx #0/0: registered device video1 [v4l2]
[   21.544824] cx231xx #0: cx231xx #0/0: registered device vbi1
[   21.544826] cx231xx #0: V4L2 device registered as video1 and vbi1
[   21.544828] cx231xx #0: EndPoint Addr 0x84, Alternate settings: 5
[   21.544830] cx231xx #0: Alternate setting 0, max size= 512
[   21.544831] cx231xx #0: Alternate setting 1, max size= 184
[   21.544832] cx231xx #0: Alternate setting 2, max size= 728
[   21.544833] cx231xx #0: Alternate setting 3, max size= 2892
[   21.544834] cx231xx #0: Alternate setting 4, max size= 1800
[   21.544835] cx231xx #0: EndPoint Addr 0x85, Alternate settings: 2
[   21.544837] cx231xx #0: Alternate setting 0, max size= 512
[   21.544838] cx231xx #0: Alternate setting 1, max size= 512
[   21.544839] cx231xx #0: EndPoint Addr 0x86, Alternate settings: 2
[   21.544840] cx231xx #0: Alternate setting 0, max size= 512
[   21.544841] cx231xx #0: Alternate setting 1, max size= 576
[   21.544842] cx231xx #0: EndPoint Addr 0x81, Alternate settings: 6
[   21.544843] cx231xx #0: Alternate setting 0, max size= 512
[   21.544844] cx231xx #0: Alternate setting 1, max size= 64
[   21.544845] cx231xx #0: Alternate setting 2, max size= 128
[   21.544846] cx231xx #0: Alternate setting 3, max size= 316
[   21.544847] cx231xx #0: Alternate setting 4, max size= 712
[   21.544848] cx231xx #0: Alternate setting 5, max size= 1424
[   21.544895] cx231xx #1: New device Hauppauge Hauppauge Device @ 480 Mbps (2040:b140) with 6 interfaces
[   21.544896] cx231xx #1: registering interface 1
[   21.545051] cx231xx #1: Identified as Hauppauge EXETER (card=8)
[   21.746853] cx231xx #1: cx231xx_dif_set_standard: setStandard to ffffffff
[   21.756988] cx25840 4-0044: cx23102 A/V decoder found @ 0x88 (cx231xx #1)
[   21.775042] cx25840 4-0044:  Firmware download size changed to 16 bytes max length
[   23.680530] cx25840 4-0044: loaded v4l-cx231xx-avcore-01.fw firmware (16382 bytes)
[   23.715503] Chip ID is not zero. It is not a TEA5767
[   23.715509] tuner 5-0060: Tuner -1 found with type(s) Radio TV.
[   23.715521] tda18271 5-0060: creating new instance
[   23.717640] TDA18271HD/C2 detected @ 5-0060
[   24.198575] tda18271: performing RF tracking filter calibration
[   25.824490] tda18271: RF tracking filter calibration complete
[   25.863228] cx231xx #1: cx231xx #1: v4l2 driver version 0.0.2
[   25.880721] cx231xx #1: cx231xx_dif_set_standard: setStandard to ff
[   25.969313] cx231xx #1: video_mux : 0
[   25.969316] cx231xx #1: do_mode_ctrl_overrides : 0xff
[   25.970062] cx231xx #1: do_mode_ctrl_overrides PAL
[   26.038360] cx231xx #1: cx231xx #1/0: registered device video2 [v4l2]
[   26.038396] cx231xx #1: cx231xx #1/0: registered device vbi2
[   26.038398] cx231xx #1: V4L2 device registered as video2 and vbi2
[   26.038400] cx231xx #1: EndPoint Addr 0x84, Alternate settings: 5
[   26.038402] cx231xx #1: Alternate setting 0, max size= 512
[   26.038403] cx231xx #1: Alternate setting 1, max size= 184
[   26.038404] cx231xx #1: Alternate setting 2, max size= 728
[   26.038405] cx231xx #1: Alternate setting 3, max size= 2892
[   26.038406] cx231xx #1: Alternate setting 4, max size= 1800
[   26.038407] cx231xx #1: EndPoint Addr 0x85, Alternate settings: 2
[   26.038410] cx231xx #1: Alternate setting 0, max size= 512
[   26.038411] cx231xx #1: Alternate setting 1, max size= 512
[   26.038412] cx231xx #1: EndPoint Addr 0x86, Alternate settings: 2
[   26.038413] cx231xx #1: Alternate setting 0, max size= 512
[   26.038414] cx231xx #1: Alternate setting 1, max size= 576
[   26.038415] cx231xx #1: EndPoint Addr 0x81, Alternate settings: 6
[   26.038416] cx231xx #1: Alternate setting 0, max size= 512
[   26.038418] cx231xx #1: Alternate setting 1, max size= 64
[   26.038419] cx231xx #1: Alternate setting 2, max size= 128
[   26.038420] cx231xx #1: Alternate setting 3, max size= 316
[   26.038421] cx231xx #1: Alternate setting 4, max size= 712
[   26.038422] cx231xx #1: Alternate setting 5, max size= 1424
[   26.038467] cx231xx #2: New device Hauppauge Hauppauge Device @ 480 Mbps (2040:b140) with 6 interfaces
[   26.038468] cx231xx #2: registering interface 1
[   26.038524] cx231xx #2: Identified as Hauppauge EXETER (card=8)
[   26.241950] cx231xx #2: cx231xx_dif_set_standard: setStandard to ffffffff
[   26.252085] cx25840 7-0044: cx23102 A/V decoder found @ 0x88 (cx231xx #2)
[   26.270140] cx25840 7-0044:  Firmware download size changed to 16 bytes max length
[   28.175753] cx25840 7-0044: loaded v4l-cx231xx-avcore-01.fw firmware (16382 bytes)
[   28.211475] All bytes are equal. It is not a TEA5767
[   28.211481] tuner 8-0060: Tuner -1 found with type(s) Radio TV.
[   28.211494] tda18271 8-0060: creating new instance
[   28.213612] Unknown device (0) detected @ 8-0060, device not supported.
[   28.213616] tda18271_attach: [8-0060|M] error -22 on line 1285
[   28.213668] tda18271 8-0060: destroying instance
[   28.219110] tuner 8-0060: Tuner has no way to set tv freq
[   28.220235] cx231xx #2: cx231xx #2: v4l2 driver version 0.0.2
[   28.239229] cx231xx #2: cx231xx_dif_set_standard: setStandard to ff
[   28.328570] cx231xx #2: video_mux : 0
[   28.328573] cx231xx #2: do_mode_ctrl_overrides : 0xff
[   28.329310] cx231xx #2: do_mode_ctrl_overrides PAL
[   28.355319] tuner 8-0060: Tuner has no way to set tv freq
[   28.355391] cx231xx #2: cx231xx #2/0: registered device video3 [v4l2]
[   28.355430] cx231xx #2: cx231xx #2/0: registered device vbi3
[   28.355431] cx231xx #2: V4L2 device registered as video3 and vbi3
[   28.355433] cx231xx #2: EndPoint Addr 0x84, Alternate settings: 5
[   28.355434] cx231xx #2: Alternate setting 0, max size= 512
[   28.355435] cx231xx #2: Alternate setting 1, max size= 184
[   28.355437] cx231xx #2: Alternate setting 2, max size= 728
[   28.355438] cx231xx #2: Alternate setting 3, max size= 2892
[   28.355439] cx231xx #2: Alternate setting 4, max size= 1800
[   28.355440] cx231xx #2: EndPoint Addr 0x85, Alternate settings: 2
[   28.355441] cx231xx #2: Alternate setting 0, max size= 512
[   28.355442] cx231xx #2: Alternate setting 1, max size= 512
[   28.355443] cx231xx #2: EndPoint Addr 0x86, Alternate settings: 2
[   28.355445] cx231xx #2: Alternate setting 0, max size= 512
[   28.355446] cx231xx #2: Alternate setting 1, max size= 576
[   28.355447] cx231xx #2: EndPoint Addr 0x81, Alternate settings: 6
[   28.355448] cx231xx #2: Alternate setting 0, max size= 512
[   28.355449] cx231xx #2: Alternate setting 1, max size= 64
[   28.355450] cx231xx #2: Alternate setting 2, max size= 128
[   28.355451] cx231xx #2: Alternate setting 3, max size= 316
[   28.355452] cx231xx #2: Alternate setting 4, max size= 712
[   28.355453] cx231xx #2: Alternate setting 5, max size= 1424
[   28.355493] usbcore: registered new interface driver cx231xx
[   28.356943] cx231xx #0: cx231xx-audio.c: probing for cx231xx non standard usbaudio
[   28.357086] cx231xx #0: EndPoint Addr 0x83, Alternate settings: 3
[   28.357088] cx231xx #0: Alternate setting 0, max size= 512
[   28.357089] cx231xx #0: Alternate setting 1, max size= 28
[   28.357090] cx231xx #0: Alternate setting 2, max size= 52
[   28.357091] cx231xx #1: cx231xx-audio.c: probing for cx231xx non standard usbaudio
[   28.357168] cx231xx #1: EndPoint Addr 0x83, Alternate settings: 3
[   28.357169] cx231xx #1: Alternate setting 0, max size= 512
[   28.357170] cx231xx #1: Alternate setting 1, max size= 28
[   28.357171] cx231xx #1: Alternate setting 2, max size= 52
[   28.357172] cx231xx #2: cx231xx-audio.c: probing for cx231xx non standard usbaudio
[   28.357255] cx231xx #2: EndPoint Addr 0x83, Alternate settings: 3
[   28.357256] cx231xx #2: Alternate setting 0, max size= 512
[   28.357257] cx231xx #2: Alternate setting 1, max size= 28
[   28.357258] cx231xx #2: Alternate setting 2, max size= 52
[   28.357259] cx231xx: Cx231xx Audio Extension initialized
[   28.413289] dvb_init: looking for tuner / demod on i2c bus: 2
[   28.424916] tda18271 2-0060: creating new instance
[   28.427158] TDA18271HD/C2 detected @ 2-0060
[   28.427302] cx231xx #0: UsbInterface::sendCommand, failed with status --32
[   28.427304] __tda18271_write_regs: [2-0060|M] ERROR: idx = 0x0, len = 39, i2c_transfer returned: -32
[   28.433504] cx231xx #1: called cx231xx_uninit_vbi_isoc
[   28.433508] cx231xx #1: cx231xx_stop_stream():: ep_mask = 10
[   28.434509] cx231xx #1:  setPowerMode::mode = 32, No Change req.
[   28.435911] cx231xx #2:  setPowerMode::mode = 32, No Change req.
[   28.439148] cx231xx #1: cx231xx_stop_stream():: ep_mask = 8
[   28.474134] cx231xx #2: UsbInterface::sendCommand, failed with status --71
[   28.484379] cx231xx #2: UsbInterface::sendCommand, failed with status --71
[   28.488931] init: failsafe main process (781) killed by TERM signal
[   28.492629] cx231xx #2: can't change interface 5 alt no. to 0 (err=-71)
[   28.492721] cx231xx #2: called cx231xx_uninit_vbi_isoc
[   28.492723] cx231xx #2: cx231xx_stop_stream():: ep_mask = 10
[   28.509252] cx231xx #2: can't change interface 5 alt no. to 0 (err=-71)
[   28.654063] DVB: registering new adapter (cx231xx #0)
[   28.654070] usb 1-1: DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3305 VSB/QAM Frontend)...
[   28.654338] Successfully loaded cx231xx-dvb
[   28.655179] cx231xx #0: called cx231xx_uninit_vbi_isoc
[   28.655183] cx231xx #0: cx231xx_stop_stream():: ep_mask = 10
[   28.655646] cx231xx #0:  setPowerMode::mode = 32, No Change req.
[   28.659982] cx231xx #0: cx231xx_stop_stream():: ep_mask = 8
[   28.673576] cx231xx #1: Changing the i2c master port to 1
[   28.718861] type=1400 audit(1435546700.674:12): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=957 comm="apparmor_parser"
[   28.718869] type=1400 audit(1435546700.674:13): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=957 comm="apparmor_parser"
[   28.719144] type=1400 audit(1435546700.674:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=957 comm="apparmor_parser"
[   28.721565] type=1400 audit(1435546700.678:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=958 comm="apparmor_parser"
[   28.721572] type=1400 audit(1435546700.678:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=958 comm="apparmor_parser"
[   28.721577] type=1400 audit(1435546700.678:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=958 comm="apparmor_parser"
[   28.722018] type=1400 audit(1435546700.678:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=958 comm="apparmor_parser"
[   28.722021] type=1400 audit(1435546700.678:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=958 comm="apparmor_parser"
[   28.722093] type=1400 audit(1435546700.678:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=961 comm="apparmor_parser"
[   28.722100] type=1400 audit(1435546700.678:21): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/telepathy-*" pid=961 comm="apparmor_parser"
[   28.825775] dvb_init: looking for tuner / demod on i2c bus: 5
[   28.828026] tda18271 5-0060: attaching existing instance
[   28.828030] DVB: registering new adapter (cx231xx #1)
[   28.828035] usb 1-3: DVB: registering adapter 1 frontend 0 (LG Electronics LGDT3305 VSB/QAM Frontend)...
[   28.829004] Successfully loaded cx231xx-dvb
[   28.921480] dvb_init: looking for tuner / demod on i2c bus: 8
[   28.929719] cx231xx #2: UsbInterface::sendCommand, failed with status --71
[   28.929724] lgdt3305_read_reg: error (addr 0e reg 0001 error (ret == -71)
[   28.929780] lgdt3305_attach: error -71 on line 1144
[   28.929829] lgdt3305_attach: unable to detect LGDT3305 hardware
[   28.929832] cx231xx: Failed to attach LG3305 front end
[   28.937969] cx231xx #2: UsbInterface::sendCommand, failed with status --71
[   28.946219] cx231xx #2: UsbInterface::sendCommand, failed with status --71
[   28.946223] cx231xx: Cx231xx dvb Extension initialized
[   29.165381] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
```

1st tuner plugged in after boot:
```
[   97.211463] usb 1-1: USB disconnect, device number 2
[   97.212056] cx231xx #0: V4L2 device vbi1 deregistered
[   97.212143] cx231xx #0: V4L2 device video1 deregistered
[   98.933489] usb 1-1: new high-speed USB device number 4 using ehci-pci
[   99.068267] usb 1-1: New USB device found, idVendor=2040, idProduct=b140
[   99.068280] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   99.068287] usb 1-1: Product: Hauppauge Device
[   99.068293] usb 1-1: Manufacturer: Hauppauge
[   99.068298] usb 1-1: SerialNumber: 4034729194
[   99.071840] cx231xx #0: New device Hauppauge Hauppauge Device @ 480 Mbps (2040:b140) with 6 interfaces
[   99.071847] cx231xx #0: registering interface 1
[   99.071975] cx231xx #0: Identified as Hauppauge EXETER (card=8)
[   99.274557] cx231xx #0: cx231xx_dif_set_standard: setStandard to ffffffff
[   99.287696] cx25840 1-0044: cx23102 A/V decoder found @ 0x88 (cx231xx #0)
[   99.305866] cx25840 1-0044:  Firmware download size changed to 16 bytes max length
[  101.355048] cx25840 1-0044: loaded v4l-cx231xx-avcore-01.fw firmware (16382 bytes)
[  101.393124] All bytes are equal. It is not a TEA5767
[  101.393151] tuner 2-0060: Tuner -1 found with type(s) Radio TV.
[  101.393186] tda18271 2-0060: creating new instance
[  101.395271] Unknown device (0) detected @ 2-0060, device not supported.
[  101.395283] tda18271_attach: [2-0060|M] error -22 on line 1285
[  101.395289] tda18271 2-0060: destroying instance
[  101.400901] tuner 2-0060: Tuner has no way to set tv freq
[  101.402018] cx231xx #0: cx231xx #0: v4l2 driver version 0.0.2
[  101.418891] cx231xx #0: cx231xx_dif_set_standard: setStandard to ff
[  101.508230] cx231xx #0: video_mux : 0
[  101.508240] cx231xx #0: do_mode_ctrl_overrides : 0xff
[  101.508990] cx231xx #0: do_mode_ctrl_overrides PAL
[  101.534985] tuner 2-0060: Tuner has no way to set tv freq
[  101.535205] cx231xx #0: cx231xx #0/0: registered device video1 [v4l2]
[  101.535333] cx231xx #0: cx231xx #0/0: registered device vbi1
[  101.535338] cx231xx #0: V4L2 device registered as video1 and vbi1
[  101.535343] cx231xx #0: cx231xx-audio.c: probing for cx231xx non standard usbaudio
[  101.535848] cx231xx #0: EndPoint Addr 0x83, Alternate settings: 3
[  101.535859] cx231xx #0: Alternate setting 0, max size= 512
[  101.535864] cx231xx #0: Alternate setting 1, max size= 28
[  101.535868] cx231xx #0: Alternate setting 2, max size= 52
[  101.581351] dvb_init: looking for tuner / demod on i2c bus: 2
[  101.583713] tda18271 2-0060: creating new instance
[  101.585833] TDA18271HD/C2 detected @ 2-0060
[  101.585927] cx231xx #0: UsbInterface::sendCommand, failed with status --32
[  101.585935] __tda18271_write_regs: [2-0060|M] ERROR: idx = 0x0, len = 39, i2c_transfer returned: -32
[  101.813975] DVB: registering new adapter (cx231xx #0)
[  101.813995] usb 1-1: DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3305 VSB/QAM Frontend)...
[  101.814711] Successfully loaded cx231xx-dvb
[  101.815347] cx231xx #0: EndPoint Addr 0x84, Alternate settings: 5
[  101.815357] cx231xx #0: Alternate setting 0, max size= 512
[  101.815361] cx231xx #0: Alternate setting 1, max size= 184
[  101.815365] cx231xx #0: Alternate setting 2, max size= 728
[  101.815369] cx231xx #0: Alternate setting 3, max size= 2892
[  101.815372] cx231xx #0: Alternate setting 4, max size= 1800
[  101.815376] cx231xx #0: EndPoint Addr 0x85, Alternate settings: 2
[  101.815380] cx231xx #0: Alternate setting 0, max size= 512
[  101.815384] cx231xx #0: Alternate setting 1, max size= 512
[  101.815387] cx231xx #0: EndPoint Addr 0x86, Alternate settings: 2
[  101.815391] cx231xx #0: Alternate setting 0, max size= 512
[  101.815394] cx231xx #0: Alternate setting 1, max size= 576
[  101.815398] cx231xx #0: EndPoint Addr 0x81, Alternate settings: 6
[  101.815402] cx231xx #0: Alternate setting 0, max size= 512
[  101.815405] cx231xx #0: Alternate setting 1, max size= 64
[  101.815409] cx231xx #0: Alternate setting 2, max size= 128
[  101.815413] cx231xx #0: Alternate setting 3, max size= 316
[  101.815416] cx231xx #0: Alternate setting 4, max size= 712
[  101.815419] cx231xx #0: Alternate setting 5, max size= 1424
[  101.850979] cx231xx #0: called cx231xx_uninit_vbi_isoc
[  101.850983] cx231xx #0: cx231xx_stop_stream():: ep_mask = 10
[  101.852258] cx231xx #0:  setPowerMode::mode = 32, No Change req.
[  101.859671] cx231xx #0: cx231xx_stop_stream():: ep_mask = 8
[  101.866082] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[  101.866563] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[  101.866885] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[  101.871579] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[  101.872063] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[  101.872379] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[  101.877080] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[  101.877561] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[  101.877917] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[  101.882722] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[  101.883188] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[  101.884030] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[  101.890225] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[  101.890687] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[  101.896192] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[  101.901320] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[  101.901802] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[  101.902153] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[  101.906942] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[  101.907424] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[  101.907744] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[  101.912439] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[  101.912928] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[  101.913274] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[  101.918084] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[  101.918550] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[  101.919393] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[  101.931559] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[  101.932039] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[  101.936367] cx231xx #0: cx231xx_init_audio_isoc: Starting ISO AUDIO transfers
[  106.941501] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
```

2nd tuner plugged in after boot:
```
[  244.597043] usb 1-3: new high-speed USB device number 5 using ehci-pci
[  244.731838] usb 1-3: New USB device found, idVendor=2040, idProduct=b140
[  244.731849] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  244.731857] usb 1-3: Product: Hauppauge Device
[  244.731863] usb 1-3: Manufacturer: Hauppauge
[  244.731867] usb 1-3: SerialNumber: 4034729253
[  244.735412] cx231xx #1: New device Hauppauge Hauppauge Device @ 480 Mbps (2040:b140) with 6 interfaces
[  244.735420] cx231xx #1: registering interface 1
[  244.735549] cx231xx #1: Identified as Hauppauge EXETER (card=8)
[  244.938728] cx231xx #1: cx231xx_dif_set_standard: setStandard to ffffffff
[  244.951877] cx25840 7-0044: cx23102 A/V decoder found @ 0x88 (cx231xx #1)
[  244.970134] cx25840 7-0044:  Firmware download size changed to 16 bytes max length
[  247.020743] cx25840 7-0044: loaded v4l-cx231xx-avcore-01.fw firmware (16382 bytes)
[  247.058818] Chip ID is not zero. It is not a TEA5767
[  247.058841] tuner 8-0060: Tuner -1 found with type(s) Radio TV.
[  247.058873] tda18271 8-0060: creating new instance
[  247.060960] TDA18271HD/C2 detected @ 8-0060
[  247.541142] tda18271: performing RF tracking filter calibration
[  249.252053] tda18271: RF tracking filter calibration complete
[  249.293913] cx231xx #1: cx231xx #1: v4l2 driver version 0.0.2
[  249.311407] cx231xx #1: cx231xx_dif_set_standard: setStandard to ff
[  249.399234] cx231xx #1: video_mux : 0
[  249.399243] cx231xx #1: do_mode_ctrl_overrides : 0xff
[  249.399987] cx231xx #1: do_mode_ctrl_overrides PAL
[  249.468643] cx231xx #1: cx231xx #1/0: registered device video2 [v4l2]
[  249.468737] cx231xx #1: cx231xx #1/0: registered device vbi2
[  249.468742] cx231xx #1: V4L2 device registered as video2 and vbi2
[  249.468748] cx231xx #1: cx231xx-audio.c: probing for cx231xx non standard usbaudio
[  249.469043] cx231xx #1: EndPoint Addr 0x83, Alternate settings: 3
[  249.469048] cx231xx #1: Alternate setting 0, max size= 512
[  249.469052] cx231xx #1: Alternate setting 1, max size= 28
[  249.469055] cx231xx #1: Alternate setting 2, max size= 52
[  249.516321] dvb_init: looking for tuner / demod on i2c bus: 8
[  249.518587] tda18271 8-0060: attaching existing instance
[  249.518598] DVB: registering new adapter (cx231xx #1)
[  249.518610] usb 1-3: DVB: registering adapter 1 frontend 0 (LG Electronics LGDT3305 VSB/QAM Frontend)...
[  249.519294] Successfully loaded cx231xx-dvb
[  249.519917] cx231xx #1: EndPoint Addr 0x84, Alternate settings: 5
[  249.519925] cx231xx #1: Alternate setting 0, max size= 512
[  249.519933] cx231xx #1: Alternate setting 1, max size= 184
[  249.519936] cx231xx #1: Alternate setting 2, max size= 728
[  249.519940] cx231xx #1: Alternate setting 3, max size= 2892
[  249.519943] cx231xx #1: Alternate setting 4, max size= 1800
[  249.519955] cx231xx #1: EndPoint Addr 0x85, Alternate settings: 2
[  249.519970] cx231xx #1: Alternate setting 0, max size= 512
[  249.519973] cx231xx #1: Alternate setting 1, max size= 512
[  249.519977] cx231xx #1: EndPoint Addr 0x86, Alternate settings: 2
[  249.519981] cx231xx #1: Alternate setting 0, max size= 512
[  249.519984] cx231xx #1: Alternate setting 1, max size= 576
[  249.519993] cx231xx #1: EndPoint Addr 0x81, Alternate settings: 6
[  249.520007] cx231xx #1: Alternate setting 0, max size= 512
[  249.520011] cx231xx #1: Alternate setting 1, max size= 64
[  249.520014] cx231xx #1: Alternate setting 2, max size= 128
[  249.520017] cx231xx #1: Alternate setting 3, max size= 316
[  249.520021] cx231xx #1: Alternate setting 4, max size= 712
[  249.520037] cx231xx #1: Alternate setting 5, max size= 1424
[  249.555813] cx231xx #1:  setPowerMode::mode = 32, No Change req.
[  249.563661] cx231xx #1: cx231xx_initialize_stream_xfer: Audio enter HANC
[  249.564139] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
[  249.564451] cx231xx #1: called cx231xx_uninit_vbi_isoc
[  249.564460] cx231xx #1: cx231xx_stop_stream():: ep_mask = 10
[  249.564773] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
[  249.569532] cx231xx #1: cx231xx_initialize_stream_xfer: Audio enter HANC
[  249.570013] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
[  249.570339] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
[  249.575027] cx231xx #1: cx231xx_initialize_stream_xfer: Audio enter HANC
[  249.575511] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
[  249.575871] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
[  249.580669] cx231xx #1: cx231xx_initialize_stream_xfer: Audio enter HANC
[  249.581139] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
[  249.581966] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
[  249.588300] cx231xx #1: cx231xx_initialize_stream_xfer: Audio enter HANC
[  249.588761] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
[  249.594545] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
[  249.599393] cx231xx #1: cx231xx_initialize_stream_xfer: Audio enter HANC
[  249.599878] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
[  249.600209] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
[  249.604891] cx231xx #1: cx231xx_initialize_stream_xfer: Audio enter HANC
[  249.605375] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
[  249.605688] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
[  249.610389] cx231xx #1: cx231xx_initialize_stream_xfer: Audio enter HANC
[  249.610873] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
[  249.611207] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
[  249.615907] cx231xx #1: cx231xx_initialize_stream_xfer: Audio enter HANC
[  249.616377] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
[  249.616897] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
[  249.624918] cx231xx #1: cx231xx_initialize_stream_xfer: Audio enter HANC
[  249.625377] cx231xx #1: cx231xx_start_stream():: ep_mask = 4
[  249.632630] cx231xx #1: cx231xx_init_audio_isoc: Starting ISO AUDIO transfers
[  254.637811] cx231xx #1: cx231xx_stop_stream():: ep_mask = 4
```

3rd tuner plugged in after boot:
```
[  367.897694] usb 1-4: new high-speed USB device number 6 using ehci-pci
[  368.032508] usb 1-4: New USB device found, idVendor=2040, idProduct=b140
[  368.032520] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  368.032528] usb 1-4: Product: Hauppauge Device
[  368.032534] usb 1-4: Manufacturer: Hauppauge
[  368.032538] usb 1-4: SerialNumber: 4034729515
[  368.036208] cx231xx #2: New device Hauppauge Hauppauge Device @ 480 Mbps (2040:b140) with 6 interfaces
[  368.036216] cx231xx #2: registering interface 1
[  368.036344] cx231xx #2: Identified as Hauppauge EXETER (card=8)
[  368.238024] cx231xx #2: cx231xx_dif_set_standard: setStandard to ffffffff
[  368.251299] cx25840 10-0044: cx23102 A/V decoder found @ 0x88 (cx231xx #2)
[  368.269427] cx25840 10-0044:  Firmware download size changed to 16 bytes max length
[  370.320039] cx25840 10-0044: loaded v4l-cx231xx-avcore-01.fw firmware (16382 bytes)
[  370.358114] All bytes are equal. It is not a TEA5767
[  370.358138] tuner 11-0060: Tuner -1 found with type(s) Radio TV.
[  370.358172] tda18271 11-0060: creating new instance
[  370.360267] Unknown device (0) detected @ 11-0060, device not supported.
[  370.360278] tda18271_attach: [11-0060|M] error -22 on line 1285
[  370.360284] tda18271 11-0060: destroying instance
[  370.365888] tuner 11-0060: Tuner has no way to set tv freq
[  370.367012] cx231xx #2: cx231xx #2: v4l2 driver version 0.0.2
[  370.383020] cx231xx #2: cx231xx_dif_set_standard: setStandard to ff
[  370.472733] cx231xx #2: video_mux : 0
[  370.472743] cx231xx #2: do_mode_ctrl_overrides : 0xff
[  370.473579] cx231xx #2: do_mode_ctrl_overrides PAL
[  370.499724] tuner 11-0060: Tuner has no way to set tv freq
[  370.499921] cx231xx #2: cx231xx #2/0: registered device video3 [v4l2]
[  370.500010] cx231xx #2: cx231xx #2/0: registered device vbi3
[  370.500015] cx231xx #2: V4L2 device registered as video3 and vbi3
[  370.500021] cx231xx #2: cx231xx-audio.c: probing for cx231xx non standard usbaudio
[  370.500412] cx231xx #2: EndPoint Addr 0x83, Alternate settings: 3
[  370.500420] cx231xx #2: Alternate setting 0, max size= 512
[  370.500425] cx231xx #2: Alternate setting 1, max size= 28
[  370.500428] cx231xx #2: Alternate setting 2, max size= 52
[  370.549829] dvb_init: looking for tuner / demod on i2c bus: 11
[  370.552080] tda18271 11-0060: creating new instance
[  370.554196] TDA18271HD/C2 detected @ 11-0060
[  370.554294] cx231xx #2: UsbInterface::sendCommand, failed with status --32
[  370.554302] __tda18271_write_regs: [11-0060|M] ERROR: idx = 0x0, len = 39, i2c_transfer returned: -32
[  370.782087] DVB: registering new adapter (cx231xx #2)
[  370.782103] usb 1-4: DVB: registering adapter 2 frontend 0 (LG Electronics LGDT3305 VSB/QAM Frontend)...
[  370.782817] Successfully loaded cx231xx-dvb
[  370.783460] cx231xx #2: EndPoint Addr 0x84, Alternate settings: 5
[  370.783469] cx231xx #2: Alternate setting 0, max size= 512
[  370.783473] cx231xx #2: Alternate setting 1, max size= 184
[  370.783477] cx231xx #2: Alternate setting 2, max size= 728
[  370.783480] cx231xx #2: Alternate setting 3, max size= 2892
[  370.783484] cx231xx #2: Alternate setting 4, max size= 1800
[  370.783488] cx231xx #2: EndPoint Addr 0x85, Alternate settings: 2
[  370.783492] cx231xx #2: Alternate setting 0, max size= 512
[  370.783495] cx231xx #2: Alternate setting 1, max size= 512
[  370.783499] cx231xx #2: EndPoint Addr 0x86, Alternate settings: 2
[  370.783502] cx231xx #2: Alternate setting 0, max size= 512
[  370.783506] cx231xx #2: Alternate setting 1, max size= 576
[  370.783509] cx231xx #2: EndPoint Addr 0x81, Alternate settings: 6
[  370.783514] cx231xx #2: Alternate setting 0, max size= 512
[  370.783517] cx231xx #2: Alternate setting 1, max size= 64
[  370.783521] cx231xx #2: Alternate setting 2, max size= 128
[  370.783524] cx231xx #2: Alternate setting 3, max size= 316
[  370.783527] cx231xx #2: Alternate setting 4, max size= 712
[  370.783531] cx231xx #2: Alternate setting 5, max size= 1424
[  370.815077] cx231xx #2: called cx231xx_uninit_vbi_isoc
[  370.815082] cx231xx #2: cx231xx_stop_stream():: ep_mask = 10
[  370.820491] cx231xx #2:  setPowerMode::mode = 32, No Change req.
[  370.827455] cx231xx #2: cx231xx_initialize_stream_xfer: Audio enter HANC
[  370.827956] cx231xx #2: cx231xx_start_stream():: ep_mask = 4
[  370.828230] cx231xx #2: cx231xx_stop_stream():: ep_mask = 8
[  370.830584] cx231xx #2: cx231xx_stop_stream():: ep_mask = 4
[  370.835690] cx231xx #2: cx231xx_initialize_stream_xfer: Audio enter HANC
[  370.836179] cx231xx #2: cx231xx_start_stream():: ep_mask = 4
[  370.836475] cx231xx #2: cx231xx_stop_stream():: ep_mask = 4
[  370.841342] cx231xx #2: cx231xx_initialize_stream_xfer: Audio enter HANC
[  370.841810] cx231xx #2: cx231xx_start_stream():: ep_mask = 4
[  370.842240] cx231xx #2: cx231xx_stop_stream():: ep_mask = 4
[  370.846964] cx231xx #2: cx231xx_initialize_stream_xfer: Audio enter HANC
[  370.847433] cx231xx #2: cx231xx_start_stream():: ep_mask = 4
[  370.848256] cx231xx #2: cx231xx_stop_stream():: ep_mask = 4
[  370.854588] cx231xx #2: cx231xx_initialize_stream_xfer: Audio enter HANC
[  370.855055] cx231xx #2: cx231xx_start_stream():: ep_mask = 4
[  370.861951] cx231xx #2: cx231xx_stop_stream():: ep_mask = 4
[  370.867182] cx231xx #2: cx231xx_initialize_stream_xfer: Audio enter HANC
[  370.867669] cx231xx #2: cx231xx_start_stream():: ep_mask = 4
[  370.867985] cx231xx #2: cx231xx_stop_stream():: ep_mask = 4
[  370.872678] cx231xx #2: cx231xx_initialize_stream_xfer: Audio enter HANC
[  370.873173] cx231xx #2: cx231xx_start_stream():: ep_mask = 4
[  370.873533] cx231xx #2: cx231xx_stop_stream():: ep_mask = 4
[  370.878325] cx231xx #2: cx231xx_initialize_stream_xfer: Audio enter HANC
[  370.878796] cx231xx #2: cx231xx_start_stream():: ep_mask = 4
[  370.879209] cx231xx #2: cx231xx_stop_stream():: ep_mask = 4
[  370.883949] cx231xx #2: cx231xx_initialize_stream_xfer: Audio enter HANC
[  370.884418] cx231xx #2: cx231xx_start_stream():: ep_mask = 4
[  370.885304] cx231xx #2: cx231xx_stop_stream():: ep_mask = 4
[  370.897549] cx231xx #2: cx231xx_initialize_stream_xfer: Audio enter HANC
[  370.898033] cx231xx #2: cx231xx_start_stream():: ep_mask = 4
[  370.904538] cx231xx #2: cx231xx_init_audio_isoc: Starting ISO AUDIO transfers
[  375.905566] cx231xx #2: cx231xx_stop_stream():: ep_mask = 4
```

Sorry about the long post...

---

### Post by colonelpenguin on 2015-07-02
Does anyone see anything revealing in the dmesg output posted above?

---

### Post by VMC on 2015-07-02
What about those crashes your getting from the first two logs:
```
init: apport-noui (/var/crash/_usr_bin_mythfrontend.real.1000.crash) main process (780) terminated with status 1
```

---

### Post by blm-ubunet on 2015-07-03
One possible problem with USB dongles is that they may not get a actual power-on reset (cold start) because of standby power on USB ports.

Do your devices behave differently after a full power off cold start ?

Could try to force logical power off/on reset with below.
Use "lsusb" or your dmesg logs to determine which ports are used by tuner dongles.
```
echo 0 | sudo tee /sys/bus/usb/devices/usb2/power/autosuspend_delay_ms
echo "auto" | sudo tee /sys/bus/usb/devices/usb2/power/control
```
from [http://askubuntu.com/questions/342061/power-on-off-usb-ports](http://askubuntu.com/questions/342061/power-on-off-usb-ports)

That above link has some links to interesting information on h/w & power control.

---

### Post by colonelpenguin on 2015-07-09
Unfortunately my settings were already set to 0 and auto in those two files.  The problem still persists.  I noticed that the following line (along with some others after it) usually occurs in dmesg when the tuners are recognized properly, but not when a tuner isn't recognized: 
```
All bytes are equal. It is not a TEA5767
```
Not sure if this is helpful to anyone, but I thought the differences in dmesg output might be helpful in tracking down the issue for someone who knows more about how these things work.

---

### Post by blm-ubunet on 2015-07-10
To do a logical power cycle you need:
```
echo 0 | sudo tee /sys/bus/usb/devices/usb2/power/autosuspend_delay_ms
echo "auto" | sudo tee /sys/bus/usb/devices/usb2/power/control
```
These only just allow device suspending if it becomes idle but the real power off reset is only possible if USB device or hub hardware supports it.

These links has some other ideas..
[http://stackoverflow.com/questions/4702216/controlling-a-usb-power-supply-on-off-with-linux](http://stackoverflow.com/questions/4702216/controlling-a-usb-power-supply-on-off-with-linux)
[https://loginroot.com/power-off-and-on-usb-device-in-linux-ubuntu/](https://loginroot.com/power-off-and-on-usb-device-in-linux-ubuntu/)

Can use :
```
tree /sys/bus/usb/drivers/hub/
lsusb -t
```
to find device path/node.

This disconnects & reconnects the webcam in my netbook:
```
echo "1-4" | sudo tee /sys/bus/usb/drivers/usb/unbind
echo "1-4" | sudo tee /sys/bus/usb/drivers/usb/bind
dmesg
```

The thought was that the above could run in script during reboot but before mythbackend is started.
Would need to run the above code per tuner dongle.
You have to find the right usb port numbers to match your dongles.

---

### Post by colonelpenguin on 2015-07-14
I have finally had some success but need help getting the commands to run at startup.  I tied the unbind and bind commands listed above and saw some some response but could not revive the failed tuners.  The tuners have lights on them and the lights would turn off for the tuners that loaded properly, but the failed tuners' lights would remain on and never work unless they were unpluged and pluged back in.  I then stumbled on the usb_modeswitch command.  To understand what to pass to this command I had to run lsusb and it returned the following:

```
Bus 001 Device 005: ID 2040:b140 Hauppauge 
Bus 001 Device 004: ID 2040:b140 Hauppauge 
Bus 001 Device 002: ID 2040:b140 Hauppauge
```

Knowing this information... I was able to create the following script:

```
#!/bin/bash 
service mythtv-backend stop
usb_modeswitch -v 0x2040 -p 0xb140 --reset-usb -b 1 -g 2
usb_modeswitch -v 0x2040 -p 0xb140 --reset-usb -b 1 -g 4
usb_modeswitch -v 0x2040 -p 0xb140 --reset-usb -b 1 -g 5
service mythtv-backend start
```

Executing this script after the computer has fully booted seems to cause all of the tuners to work without removing them from the computer!

However, when I try to add this script or the individual commands to /etc/rc.local, the commands don't work properly.  I am thinking this may be due to how the mythtv-backend backend service initializes.  Can anyone think of a way to get these commands to run at boot?  Note that mythtv-backend has to be stopped or the usb_modeswitch command doesn't work.  Thanks!

---

### Post by colonelpenguin on 2015-07-17
Hopefully something will be updated some day to make this all unnecessary.  However, for now, I think I finally have a workaround to get these tuners working at boot every time.  I had to make the mythtv-backend service startup a manual process by running the following command:

```
echo manual | sudo tee /etc/init/mythtv-backend.override
```

Then I had to add the following to rc.local

```
usb_modeswitch -v 0x2040 -p 0xb140 --reset-usb -b 1 -g 2
usb_modeswitch -v 0x2040 -p 0xb140 --reset-usb -b 1 -g 4
usb_modeswitch -v 0x2040 -p 0xb140 --reset-usb -b 1 -g 5
service mythtv-backend start
```

Remember that you have to run lsusb verify your -v (vendor), -p (product), -b (bus number), and -g (device number) values if you attempt this on a different computer.

Overall I have been pretty happy with these tuners, but this problem has been a real headache.  I have rebooted the computer numerous times now with my changes and all of the tuners have initialized properly.

---

### Post by blm-ubunet on 2015-07-20
That's a great find & lot's of people should find this helpful & to think that usb-modeswitch was already installed here..

Had suspected that bind/unbind was only going to work with a device that was not locked up.

A udev rule is a potential solution to this problem now that you have the required tool.
Udev has all the device parameters available as variables.
A udev rule that matches the device by usb-ids would call a script (passing bus & device number) that contains one line (+shebang):
/usr/sbin/usb_modeswitch -v 0x2040 -p 0xb140 --reset-usb -b $1 -g $2
Could be cleaner to pass vendor & product ids as well.

The udev script needs to have correct permissions & a good location helps (/usr/local/bin/).
Some clues here:
[http://ubuntuforums.org/showthread.php?t=2249102&p=13302905#post13302905](http://ubuntuforums.org/showthread.php?t=2249102&p=13302905#post13302905)
[http://ubuntuforums.org/showthread.php?t=2276012&page=2](http://ubuntuforums.org/showthread.php?t=2276012&page=2)

---

