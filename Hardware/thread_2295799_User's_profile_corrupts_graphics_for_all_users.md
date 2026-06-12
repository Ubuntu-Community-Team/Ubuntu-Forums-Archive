---
title: "User's profile corrupts graphics for all users???"
date: 2015-09-21
forum: Hardware
---

### Post by tornadof3 on 2015-09-21
So,

I can log in to my Ubuntu 15.04 machine and use it no problem; I can log off and log in repeatedly and it works fine. It has the Nvidia closed-source graphics drivers and two monitors (one DVI, one VGA). However, my wife also has a user account on this machine. When she logs in, it works fine but after she has logged out, anyone else attempting to log in gets an error message saying the graphics are not correctly configured; the machine then hangs.

What on earth could cause this? Are there any (corrupt) folders in the wife's /home that I could delete that might help? Happy to post any output that might be useful.... thanks

---

### Post by Bucky Ball on 2015-09-21
Has your wife's user account got the same permissions as yours?

---

### Post by tornadof3 on 2015-09-21
Both her /home/username1 and my /home/username2 are owned by each of us respectively and each in the same group; I am a sudo user and she is not. She doesn't appear to have any problems saving or opening any files in her home

---

### Post by Bucky Ball on 2015-09-21
> **tornadof3 said:**
> She doesn't appear to have any problems saving or opening any files in her home

She doesn't need to sudo for that. Can she open a terminal and 'sudo apt-get update' for instance? I guess not. So ... 

Are you saying that she logs in, uses all fine, logs out, you log in, graphics is screwed? How are the graphics looking exactly?

Out of curiousity, is she using the same desktop wallpaper?

---

### Post by tornadof3 on 2015-09-21
> **Bucky Ball said:**
> Are you saying that she logs in, uses all fine, logs out, you log in, graphics is screwed?

That's exactly it. Including even if she herself logs back in.... Only solution (that I've found) is to restart machine

---

### Post by Bucky Ball on 2015-09-21
When you log in and the graphics are screwed, you could hit control+alt+F1, log in there, and run:

```
dmesg
```

Toward the end of the output might be some clues as to what's happening. There are logs you can check from there but unsure which you would. Hopefully someone else can throw some light.

---

### Post by tornadof3 on 2015-09-21
Thank you for this suggestion of running dmesg; that has helped to get a bit more info. So it appears the lightdm is segfaulting. Now to work out why...

Ctrl-Alt-F1 on "Running in low graphics mode" error message; ran dmesg > file.txt. Reboot; dmesg output:
```
[    0.000000] CPU0 microcode updated early to revision 0x1b, date = 2014-05-29
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.19.0-15-generic (buildd@komainu) (gcc version 4.9.2 (Ubuntu 4.9.2-10ubuntu13) ) #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 (Ubuntu 3.19.0-15.15-generic 3.19.3)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-15-generic root=UUID=d7c5c94e-0b3d-43eb-b7ca-201afc635724 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009ebff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009ec00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000dde79fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000dde7a000-0x00000000de002fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000de003000-0x00000000de004fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000de005000-0x00000000de60afff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000de60b000-0x00000000de860fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000de861000-0x00000000de86cfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000de86d000-0x00000000de88afff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000de88b000-0x00000000de88ffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000de890000-0x00000000de8d2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000de8d3000-0x00000000dece0fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000dece1000-0x00000000deff3fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000deff4000-0x00000000deffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000041effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: System manufacturer System Product Name/P8H61-MX R2.0, BIOS 0504 06/29/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x41f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask C00000000 write-back
[    0.000000]   1 base 400000000 mask FF0000000 write-back
[    0.000000]   2 base 410000000 mask FF8000000 write-back
[    0.000000]   3 base 418000000 mask FFC000000 write-back
[    0.000000]   4 base 41C000000 mask FFE000000 write-back
[    0.000000]   5 base 41E000000 mask FFF000000 write-back
[    0.000000]   6 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 16GB, type WB
[    0.000000] reg 1, base: 16GB, range: 256MB, type WB
[    0.000000] reg 2, base: 16640MB, range: 128MB, type WB
[    0.000000] reg 3, base: 16768MB, range: 64MB, type WB
[    0.000000] reg 4, base: 16832MB, range: 32MB, type WB
[    0.000000] reg 5, base: 16864MB, range: 16MB, type WB
[    0.000000] reg 6, base: 3584MB, range: 512MB, type UC
[    0.000000] total RAM covered: 16368M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 32M 	num_reg: 7  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 8GB, type WB
[    0.000000] reg 5, base: 16GB, range: 512MB, type WB
[    0.000000] reg 6, base: 16880MB, range: 16MB, type UC
[    0.000000] e820: update [mem 0xe0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xdf000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fcc60-0x000fcc6f] mapped at [ffff8800000fcc60]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] BRK [0x01fe6000, 0x01fe6fff] PGTABLE
[    0.000000] BRK [0x01fe7000, 0x01fe7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x41ee00000-0x41effffff]
[    0.000000]  [mem 0x41ee00000-0x41effffff] page 2M
[    0.000000] BRK [0x01fe8000, 0x01fe8fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x400000000-0x41edfffff]
[    0.000000]  [mem 0x400000000-0x41edfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x3e0000000-0x3ffffffff]
[    0.000000]  [mem 0x3e0000000-0x3ffffffff] page 2M
[    0.000000] BRK [0x01fe9000, 0x01fe9fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x00100000-0xdde79fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xdddfffff] page 2M
[    0.000000]  [mem 0xdde00000-0xdde79fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xde003000-0xde004fff]
[    0.000000]  [mem 0xde003000-0xde004fff] page 4k
[    0.000000] BRK [0x01fea000, 0x01feafff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xde8d3000-0xdece0fff]
[    0.000000]  [mem 0xde8d3000-0xde9fffff] page 4k
[    0.000000]  [mem 0xdea00000-0xdebfffff] page 2M
[    0.000000]  [mem 0xdec00000-0xdece0fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xdeff4000-0xdeffffff]
[    0.000000]  [mem 0xdeff4000-0xdeffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x3dfffffff]
[    0.000000]  [mem 0x100000000-0x3dfffffff] page 2M
[    0.000000] RAMDISK: [mem 0x3583a000-0x36c14fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F0450 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0x00000000DE861078 000064 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000DE86A470 0000F4 (v04 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x00000000DE861170 009300 (v02 ALASKA A M I    00000015 INTL 20051117)
[    0.000000] ACPI: FACS 0x00000000DE889F80 000040
[    0.000000] ACPI: APIC 0x00000000DE86A568 000092 (v03 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x00000000DE86A600 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000DE86A640 000038 (v01 ALASKA A M I    01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 0x00000000DE86A678 000495 (v01 IdeRef IdeTable 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 0x00000000DE86AB10 0009AA (v01 PmRef  Cpu0Ist  00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 0x00000000DE86B4C0 000A92 (v01 PmRef  CpuPm    00003000 INTL 20051117)
[    0.000000] ACPI: DMAR 0x00000000DE86BF58 000078 (v01 INTEL  SNB      00000001 INTL 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000041effffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x41efe9000-0x41efedfff]
[    0.000000]  [ffffea0000000000-ffffea00107fffff] PMD -> [ffff88040e600000-ffff88041e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x41effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0xdde79fff]
[    0.000000]   node   0: [mem 0xde003000-0xde004fff]
[    0.000000]   node   0: [mem 0xde8d3000-0xdece0fff]
[    0.000000]   node   0: [mem 0xdeff4000-0xdeffffff]
[    0.000000]   node   0: [mem 0x100000000-0x41effffff]
[    0.000000] Initmem setup node 0 [mem 0x00001000-0x41effffff]
[    0.000000] On node 0 totalpages: 4182579
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14155 pages used for memmap
[    0.000000]   DMA32 zone: 905878 pages, LIFO batch:31
[    0.000000]   Normal zone: 51136 pages used for memmap
[    0.000000]   Normal zone: 3272704 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdde7a000-0xde002fff]
[    0.000000] PM: Registered nosave memory: [mem 0xde005000-0xde60afff]
[    0.000000] PM: Registered nosave memory: [mem 0xde60b000-0xde860fff]
[    0.000000] PM: Registered nosave memory: [mem 0xde861000-0xde86cfff]
[    0.000000] PM: Registered nosave memory: [mem 0xde86d000-0xde88afff]
[    0.000000] PM: Registered nosave memory: [mem 0xde88b000-0xde88ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xde890000-0xde8d2fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdece1000-0xdeff3fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xdf000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 31 pages/cpu @ffff88041ec00000 s87040 r8192 d31744 u262144
[    0.000000] pcpu-alloc: s87040 r8192 d31744 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 4117203
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-15-generic root=UUID=d7c5c94e-0b3d-43eb-b7ca-201afc635724 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340 using standard form
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16364068K/16730316K available (7993K kernel code, 1232K rwdata, 3752K rodata, 1408K init, 1300K bss, 366248K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:488 16
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 3400.049 MHz processor
[    0.000024] Calibrating delay loop (skipped), value calculated using timer frequency.. 6800.09 BogoMIPS (lpj=13600196)
[    0.000026] pid_max: default: 32768 minimum: 301
[    0.000030] ACPI: Core revision 20141107
[    0.004142] ACPI: All ACPI Tables successfully acquired
[    0.004361] Security Framework initialized
[    0.004373] AppArmor: AppArmor initialized
[    0.004373] Yama: becoming mindful.
[    0.005067] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.007959] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.009256] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.009269] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.009453] Initializing cgroup subsys memory
[    0.009457] Initializing cgroup subsys devices
[    0.009459] Initializing cgroup subsys freezer
[    0.009460] Initializing cgroup subsys net_cls
[    0.009462] Initializing cgroup subsys blkio
[    0.009464] Initializing cgroup subsys perf_event
[    0.009465] Initializing cgroup subsys net_prio
[    0.009467] Initializing cgroup subsys hugetlb
[    0.009484] CPU: Physical Processor ID: 0
[    0.009485] CPU: Processor Core ID: 0
[    0.009488] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.009749] mce: CPU supports 9 MCE banks
[    0.009758] CPU0: Thermal monitoring enabled (TM1)
[    0.009767] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[    0.009859] Freeing SMP alternatives memory: 32K (ffffffff81e96000 - ffffffff81e9e000)
[    0.010797] ftrace: allocating 30078 entries in 118 pages
[    0.020815] dmar: Host address width 36
[    0.020817] dmar: DRHD base: 0x000000fed90000 flags: 0x1
[    0.020823] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.020824] dmar: RMRR base: 0x000000de582000 end: 0x000000de59efff
[    0.020893] IOAPIC id 2 under DRHD base  0xfed90000 IOMMU 0
[    0.020894] HPET id 0 under DRHD base 0xfed90000
[    0.020895] Queued invalidation will be enabled to support x2apic and Intr-remapping.
[    0.020949] Enabled IRQ remapping in x2apic mode
[    0.020950] Enabling x2apic
[    0.020950] Enabled x2apic
[    0.020954] Switched APIC routing to cluster x2apic.
[    0.021354] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.061014] smpboot: CPU0: Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz (fam: 06, model: 3a, stepping: 09)
[    0.061019] TSC deadline timer enabled
[    0.061037] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.061050] ... version:                3
[    0.061051] ... bit width:              48
[    0.061052] ... generic registers:      4
[    0.061052] ... value mask:             0000ffffffffffff
[    0.061053] ... max period:             0000ffffffffffff
[    0.061053] ... fixed-purpose events:   3
[    0.061054] ... event mask:             000000070000000f
[    0.061647] x86: Booting SMP configuration:
[    0.061648] .... node  #0, CPUs:      #1
[    0.072826] CPU1 microcode updated early to revision 0x1b, date = 2014-05-29
[    0.075228] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.075303]  #2
[    0.086480] CPU2 microcode updated early to revision 0x1b, date = 2014-05-29
[    0.088904]  #3
[    0.100082] CPU3 microcode updated early to revision 0x1b, date = 2014-05-29
[    0.102505]  #4 #5 #6 #7
[    0.156111] x86: Booted up 1 node, 8 CPUs
[    0.156113] smpboot: Total of 8 processors activated (54400.78 BogoMIPS)
[    0.162775] devtmpfs: initialized
[    0.165104] evm: security.selinux
[    0.165105] evm: security.SMACK64
[    0.165105] evm: security.SMACK64EXEC
[    0.165106] evm: security.SMACK64TRANSMUTE
[    0.165107] evm: security.SMACK64MMAP
[    0.165107] evm: security.ima
[    0.165108] evm: security.capability
[    0.165146] PM: Registering ACPI NVS region [mem 0xde60b000-0xde860fff] (2449408 bytes)
[    0.165166] PM: Registering ACPI NVS region [mem 0xde86d000-0xde88afff] (122880 bytes)
[    0.165167] PM: Registering ACPI NVS region [mem 0xde890000-0xde8d2fff] (274432 bytes)
[    0.165292] pinctrl core: initialized pinctrl subsystem
[    0.165372] RTC time: 17:11:28, date: 09/21/15
[    0.165448] NET: Registered protocol family 16
[    0.166618] cpuidle: using governor ladder
[    0.170614] cpuidle: using governor menu
[    0.170689] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.170690] ACPI: bus type PCI registered
[    0.170691] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.170742] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.170744] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.170799] PCI: Using configuration type 1 for base access
[    0.174932] ACPI: Added _OSI(Module Device)
[    0.174933] ACPI: Added _OSI(Processor Device)
[    0.174934] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.174935] ACPI: Added _OSI(Processor Aggregator Device)
[    0.176581] ACPI: Executed 1 blocks of module-level executable AML code
[    0.178082] ACPI: Dynamic OEM Table Load:
[    0.178087] ACPI: SSDT 0xFFFF88040BCF9000 00083B (v01 PmRef  Cpu0Cst  00003001 INTL 20051117)
[    0.178417] ACPI: Dynamic OEM Table Load:
[    0.178420] ACPI: SSDT 0xFFFF88040BC74400 000303 (v01 PmRef  ApIst    00003000 INTL 20051117)
[    0.178707] ACPI: Dynamic OEM Table Load:
[    0.178710] ACPI: SSDT 0xFFFF88040BC47600 000119 (v01 PmRef  ApCst    00003000 INTL 20051117)
[    0.179603] ACPI: Interpreter enabled
[    0.179611] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
[    0.179620] ACPI: (supports S0 S1 S3 S4 S5)
[    0.179621] ACPI: Using IOAPIC for interrupt routing
[    0.179637] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.182650] ACPI: Power Resource [FN00] (off)
[    0.182701] ACPI: Power Resource [FN01] (off)
[    0.182752] ACPI: Power Resource [FN02] (off)
[    0.182801] ACPI: Power Resource [FN03] (off)
[    0.182851] ACPI: Power Resource [FN04] (off)
[    0.183231] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.183234] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.183304] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
[    0.183366] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
[    0.183728] PCI host bridge to bus 0000:00
[    0.183730] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.183731] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.183732] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.183734] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.183735] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.183736] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.183737] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.183738] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.183739] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.183740] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.183741] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfeafffff]
[    0.183746] pci 0000:00:00.0: [8086:0150] type 00 class 0x060000
[    0.183805] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    0.183830] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.183854] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.183906] pci 0000:00:16.0: [8086:1c3a] type 00 class 0x078000
[    0.183927] pci 0000:00:16.0: reg 0x10: [mem 0xf7109000-0xf710900f 64bit]
[    0.183998] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.184059] pci 0000:00:1a.0: [8086:1c2d] type 00 class 0x0c0320
[    0.184078] pci 0000:00:1a.0: reg 0x10: [mem 0xf7107000-0xf71073ff]
[    0.184161] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.184198] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.184228] pci 0000:00:1b.0: [8086:1c20] type 00 class 0x040300
[    0.184242] pci 0000:00:1b.0: reg 0x10: [mem 0xf7100000-0xf7103fff 64bit]
[    0.184310] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.184338] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.184365] pci 0000:00:1c.0: [8086:1c10] type 01 class 0x060400
[    0.184440] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.184470] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.184500] pci 0000:00:1c.5: [8086:1c1a] type 01 class 0x060400
[    0.184575] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.184606] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.184636] pci 0000:00:1d.0: [8086:1c26] type 00 class 0x0c0320
[    0.184655] pci 0000:00:1d.0: reg 0x10: [mem 0xf7106000-0xf71063ff]
[    0.184737] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.184774] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.184802] pci 0000:00:1f.0: [8086:1c5c] type 00 class 0x060100
[    0.184942] pci 0000:00:1f.2: [8086:1c00] type 00 class 0x01018f
[    0.184955] pci 0000:00:1f.2: reg 0x10: [io  0xf0d0-0xf0d7]
[    0.184961] pci 0000:00:1f.2: reg 0x14: [io  0xf0c0-0xf0c3]
[    0.184968] pci 0000:00:1f.2: reg 0x18: [io  0xf0b0-0xf0b7]
[    0.184974] pci 0000:00:1f.2: reg 0x1c: [io  0xf0a0-0xf0a3]
[    0.184980] pci 0000:00:1f.2: reg 0x20: [io  0xf090-0xf09f]
[    0.184986] pci 0000:00:1f.2: reg 0x24: [io  0xf080-0xf08f]
[    0.185055] pci 0000:00:1f.3: [8086:1c22] type 00 class 0x0c0500
[    0.185068] pci 0000:00:1f.3: reg 0x10: [mem 0xf7105000-0xf71050ff 64bit]
[    0.185086] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
[    0.185144] pci 0000:00:1f.5: [8086:1c08] type 00 class 0x010185
[    0.185157] pci 0000:00:1f.5: reg 0x10: [io  0xf070-0xf077]
[    0.185163] pci 0000:00:1f.5: reg 0x14: [io  0xf060-0xf063]
[    0.185169] pci 0000:00:1f.5: reg 0x18: [io  0xf050-0xf057]
[    0.185175] pci 0000:00:1f.5: reg 0x1c: [io  0xf040-0xf043]
[    0.185181] pci 0000:00:1f.5: reg 0x20: [io  0xf030-0xf03f]
[    0.185188] pci 0000:00:1f.5: reg 0x24: [io  0xf020-0xf02f]
[    0.185287] pci 0000:01:00.0: [10de:0a65] type 00 class 0x030000
[    0.185295] pci 0000:01:00.0: reg 0x10: [mem 0xf6000000-0xf6ffffff]
[    0.185302] pci 0000:01:00.0: reg 0x14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.185309] pci 0000:01:00.0: reg 0x1c: [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.185313] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
[    0.185318] pci 0000:01:00.0: reg 0x30: [mem 0xf7000000-0xf707ffff pref]
[    0.185377] pci 0000:01:00.1: [10de:0be3] type 00 class 0x040300
[    0.185384] pci 0000:01:00.1: reg 0x10: [mem 0xf7080000-0xf7083fff]
[    0.190621] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.190625] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.190628] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
[    0.190633] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.190702] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.190781] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    0.190802] pci 0000:03:00.0: reg 0x10: [io  0xd000-0xd0ff]
[    0.190834] pci 0000:03:00.0: reg 0x18: [mem 0xf2104000-0xf2104fff 64bit pref]
[    0.190854] pci 0000:03:00.0: reg 0x20: [mem 0xf2100000-0xf2103fff 64bit pref]
[    0.190970] pci 0000:03:00.0: supports D1 D2
[    0.190971] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.191004] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.198623] pci 0000:00:1c.5: PCI bridge to [bus 03]
[    0.198628] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
[    0.198637] pci 0000:00:1c.5:   bridge window [mem 0xf2100000-0xf21fffff 64bit pref]
[    0.198662] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.198916] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.198950] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.198980] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 *14 15)
[    0.199010] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.199040] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.199071] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 *15)
[    0.199100] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.199131] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.199288] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.199351] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.199353] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.199353] vgaarb: loaded
[    0.199354] vgaarb: bridge control possible 0000:01:00.0
[    0.199510] SCSI subsystem initialized
[    0.199538] libata version 3.00 loaded.
[    0.199555] ACPI: bus type USB registered
[    0.199567] usbcore: registered new interface driver usbfs
[    0.199573] usbcore: registered new interface driver hub
[    0.199588] usbcore: registered new device driver usb
[    0.199676] PCI: Using ACPI for IRQ routing
[    0.201062] PCI: pci_cache_line_size set to 64 bytes
[    0.201094] e820: reserve RAM buffer [mem 0x0009ec00-0x0009ffff]
[    0.201095] e820: reserve RAM buffer [mem 0xdde7a000-0xdfffffff]
[    0.201096] e820: reserve RAM buffer [mem 0xde005000-0xdfffffff]
[    0.201097] e820: reserve RAM buffer [mem 0xdece1000-0xdfffffff]
[    0.201098] e820: reserve RAM buffer [mem 0xdf000000-0xdfffffff]
[    0.201099] e820: reserve RAM buffer [mem 0x41f000000-0x41fffffff]
[    0.201176] NetLabel: Initializing
[    0.201176] NetLabel:  domain hash size = 128
[    0.201177] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.201186] NetLabel:  unlabeled traffic allowed by default
[    0.201227] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.201231] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.203258] Switched to clocksource hpet
[    0.207069] AppArmor: AppArmor Filesystem Enabled
[    0.207108] pnp: PnP ACPI init
[    0.207163] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.207165] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.207213] system 00:01: [io  0x0680-0x069f] has been reserved
[    0.207214] system 00:01: [io  0x0200-0x020f] has been reserved
[    0.207215] system 00:01: [io  0xffff] has been reserved
[    0.207216] system 00:01: [io  0xffff] has been reserved
[    0.207218] system 00:01: [io  0x0400-0x0453] could not be reserved
[    0.207219] system 00:01: [io  0x0458-0x047f] has been reserved
[    0.207220] system 00:01: [io  0x0500-0x057f] has been reserved
[    0.207221] system 00:01: [io  0x164e-0x164f] has been reserved
[    0.207223] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.207251] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.207288] system 00:03: [io  0x0454-0x0457] has been reserved
[    0.207289] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.207355] system 00:04: [io  0x0a00-0x0a1f] has been reserved
[    0.207356] system 00:04: [io  0x0290-0x029f] has been reserved
[    0.207358] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.207389] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.207391] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.207522] system 00:06: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.207524] system 00:06: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.207525] system 00:06: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.207526] system 00:06: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.207527] system 00:06: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.207528] system 00:06: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.207530] system 00:06: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.207531] system 00:06: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.207532] system 00:06: [mem 0xff000000-0xffffffff] has been reserved
[    0.207534] system 00:06: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.207535] system 00:06: [mem 0xf2200000-0xf2200fff] has been reserved
[    0.207536] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.207607] pnp: PnP ACPI: found 7 devices
[    0.213462] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.213464] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.213466] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
[    0.213468] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.213470] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.213480] pci 0000:00:1c.5: PCI bridge to [bus 03]
[    0.213482] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
[    0.213488] pci 0000:00:1c.5:   bridge window [mem 0xf2100000-0xf21fffff 64bit pref]
[    0.213493] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.213494] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.213495] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.213496] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.213497] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.213498] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.213499] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.213500] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.213502] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.213503] pci_bus 0000:00: resource 13 [mem 0xe0000000-0xfeafffff]
[    0.213504] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.213505] pci_bus 0000:01: resource 1 [mem 0xf6000000-0xf70fffff]
[    0.213506] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.213507] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.213508] pci_bus 0000:03: resource 2 [mem 0xf2100000-0xf21fffff 64bit pref]
[    0.213526] NET: Registered protocol family 2
[    0.213663] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.213826] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.213935] TCP: Hash tables configured (established 131072 bind 65536)
[    0.213945] TCP: reno registered
[    0.213957] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.213998] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.214054] NET: Registered protocol family 1
[    0.251338] pci 0000:01:00.0: Video device with shadowed ROM
[    0.251348] PCI: CLS mismatch (64 != 32), using 64 bytes
[    0.251384] Trying to unpack rootfs image as initramfs...
[    0.472584] Freeing initrd memory: 20332K (ffff88003583a000 - ffff880036c15000)
[    0.472614] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.472616] software IO TLB [mem 0xd9e7a000-0xdde7a000] (64MB) mapped at [ffff8800d9e7a000-ffff8800dde79fff]
[    0.472823] RAPL PMU detected, hw unit 2^-16 Joules, API unit is 2^-32 Joules, 3 fixed counters 163840 ms ovfl timer
[    0.472905] microcode: CPU0 sig=0x306a9, pf=0x2, revision=0x1b
[    0.472909] microcode: CPU1 sig=0x306a9, pf=0x2, revision=0x1b
[    0.472914] microcode: CPU2 sig=0x306a9, pf=0x2, revision=0x1b
[    0.472920] microcode: CPU3 sig=0x306a9, pf=0x2, revision=0x1b
[    0.472925] microcode: CPU4 sig=0x306a9, pf=0x2, revision=0x1b
[    0.472931] microcode: CPU5 sig=0x306a9, pf=0x2, revision=0x1b
[    0.472935] microcode: CPU6 sig=0x306a9, pf=0x2, revision=0x1b
[    0.472940] microcode: CPU7 sig=0x306a9, pf=0x2, revision=0x1b
[    0.472981] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.472999] Scanning for low memory corruption every 60 seconds
[    0.473238] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.473257] Initialise system trusted keyring
[    0.473273] audit: initializing netlink subsys (disabled)
[    0.473285] audit: type=2000 audit(1442855488.468:1): initialized
[    0.473557] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.474463] zpool: loaded
[    0.474465] zbud: loaded
[    0.474579] VFS: Disk quotas dquot_6.5.2
[    0.474601] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.474887] fuse init (API version 7.23)
[    0.474977] Key type big_key registered
[    0.475265] Key type asymmetric registered
[    0.475268] Asymmetric key parser 'x509' registered
[    0.475290] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.475327] io scheduler noop registered
[    0.475329] io scheduler deadline registered (default)
[    0.475347] io scheduler cfq registered
[    0.475675] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.475685] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.475711] intel_idle: MWAIT substates: 0x1120
[    0.475712] intel_idle: v0.4 model 0x3A
[    0.475712] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.475931] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.475935] ACPI: Power Button [PWRB]
[    0.475959] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.475961] ACPI: Power Button [PWRF]
[    0.476517] thermal LNXTHERM:00: registered as thermal_zone0
[    0.476519] ACPI: Thermal Zone [TZ00] (28 C)
[    0.476660] thermal LNXTHERM:01: registered as thermal_zone1
[    0.476661] ACPI: Thermal Zone [TZ01] (30 C)
[    0.476684] GHES: HEST is not enabled!
[    0.476748] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.477771] Linux agpgart interface v0.103
[    0.478605] brd: module loaded
[    0.479019] loop: module loaded
[    0.479136] ata_piix 0000:00:1f.2: version 2.13
[    0.479191] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.635259] scsi host0: ata_piix
[    0.635345] scsi host1: ata_piix
[    0.635369] ata1: SATA max UDMA/133 cmd 0xf0d0 ctl 0xf0c0 bmdma 0xf090 irq 19
[    0.635373] ata2: SATA max UDMA/133 cmd 0xf0b0 ctl 0xf0a0 bmdma 0xf098 irq 19
[    0.635432] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.790931] ata_piix 0000:00:1f.5: SCR access via SIDPR is available but doesn't work
[    0.791111] scsi host2: ata_piix
[    0.791192] scsi host3: ata_piix
[    0.791214] ata3: SATA max UDMA/133 cmd 0xf070 ctl 0xf060 bmdma 0xf030 irq 19
[    0.791215] ata4: SATA max UDMA/133 cmd 0xf050 ctl 0xf040 bmdma 0xf038 irq 19
[    0.791278] libphy: Fixed MDIO Bus: probed
[    0.791281] tun: Universal TUN/TAP device driver, 1.6
[    0.791281] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.791323] PPP generic driver version 2.4.2
[    0.791385] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.791391] ehci-pci: EHCI PCI platform driver
[    0.791471] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.791475] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.791486] ehci-pci 0000:00:1a.0: debug port 2
[    0.795372] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.795381] ehci-pci 0000:00:1a.0: irq 23, io mem 0xf7107000
[    0.806918] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.806945] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.806946] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.806947] usb usb1: Product: EHCI Host Controller
[    0.806948] usb usb1: Manufacturer: Linux 3.19.0-15-generic ehci_hcd
[    0.806949] usb usb1: SerialNumber: 0000:00:1a.0
[    0.807030] hub 1-0:1.0: USB hub found
[    0.807034] hub 1-0:1.0: 2 ports detected
[    0.807179] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.807182] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.807192] ehci-pci 0000:00:1d.0: debug port 2
[    0.811079] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.811082] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7106000
[    0.822908] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.822927] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.822928] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.822929] usb usb2: Product: EHCI Host Controller
[    0.822930] usb usb2: Manufacturer: Linux 3.19.0-15-generic ehci_hcd
[    0.822931] usb usb2: SerialNumber: 0000:00:1d.0
[    0.823009] hub 2-0:1.0: USB hub found
[    0.823014] hub 2-0:1.0: 2 ports detected
[    0.823092] ehci-platform: EHCI generic platform driver
[    0.823098] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.823101] ohci-pci: OHCI PCI platform driver
[    0.823108] ohci-platform: OHCI generic platform driver
[    0.823112] uhci_hcd: USB Universal Host Controller Interface driver
[    0.823142] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.825415] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.825420] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.825512] mousedev: PS/2 mouse device common for all mice
[    0.825608] rtc_cmos 00:02: RTC can wake from S4
[    0.825716] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.825741] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.825752] i2c /dev entries driver
[    0.825793] device-mapper: uevent: version 1.0.3
[    0.825836] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    0.825847] Intel P-state driver initializing.
[    0.826043] Consider also installing thermald for improved thermal control.
[    0.826047] ledtrig-cpu: registered to indicate activity on CPUs
[    0.826611] PCCT header not found.
[    0.826613] ACPI PCC probe failed.
[    0.826710] TCP: cubic registered
[    0.826768] NET: Registered protocol family 10
[    0.826965] NET: Registered protocol family 17
[    0.826981] Key type dns_resolver registered
[    0.827226] Loading compiled-in X.509 certificates
[    0.827774] Loaded X.509 cert 'Magrathea: Glacier signing key: 9e64807092f3a6a8f66f3b7ea4cb3767fdfae08a'
[    0.827783] registered taskstats version 1
[    0.829290] Key type trusted registered
[    0.832184] Key type encrypted registered
[    0.832189] AppArmor: AppArmor sha1 policy hashing enabled
[    0.832192] ima: No TPM chip found, activating TPM-bypass!
[    0.832207] evm: HMAC attrs: 0x1
[    0.832465]   Magic number: 15:17:189
[    0.832489] acpi device:1b: hash matches
[    0.832595] rtc_cmos 00:02: setting system clock to 2015-09-21 17:11:29 UTC (1442855489)
[    0.832663] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.832664] EDD information not available.
[    0.832713] PM: Hibernation image not present or could not be loaded.
[    1.118771] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.134762] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.251406] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.251408] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.251818] hub 1-1:1.0: USB hub found
[    1.252027] hub 1-1:1.0: 4 ports detected
[    1.267396] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.267398] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.267795] hub 2-1:1.0: USB hub found
[    1.268013] hub 2-1:1.0: 6 ports detected
[    1.470722] tsc: Refined TSC clocksource calibration: 3400.025 MHz
[    1.522667] usb 1-1.3: new low-speed USB device number 3 using ehci-pci
[    1.538646] usb 2-1.4: new low-speed USB device number 3 using ehci-pci
[    1.621607] usb 1-1.3: New USB device found, idVendor=045e, idProduct=003c
[    1.621611] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.621614] usb 1-1.3: Product: SideWinder Joystick
[    1.621616] usb 1-1.3: Manufacturer: Microsoft
[    1.636593] usb 2-1.4: New USB device found, idVendor=413c, idProduct=2107
[    1.636597] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.636600] usb 2-1.4: Product: Dell USB Entry Keyboard
[    1.636602] usb 2-1.4: Manufacturer: DELL
[    1.694552] usb 1-1.4: new full-speed USB device number 4 using ehci-pci
[    1.706549] usb 2-1.6: new high-speed USB device number 4 using ehci-pci
[    1.792499] usb 1-1.4: New USB device found, idVendor=045e, idProduct=0745
[    1.792504] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.792506] usb 1-1.4: Product: Microsoft® Nano Transceiver v2.0
[    1.792508] usb 1-1.4: Manufacturer: Microsoft
[    1.841752] usb 2-1.6: New USB device found, idVendor=0c45, idProduct=62f1
[    1.841756] usb 2-1.6: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    1.841759] usb 2-1.6: Product: USB 2.0 Camera
[    1.841761] usb 2-1.6: Manufacturer: Sonix Technology Co., Ltd.
[    1.982267] ata1.01: failed to resume link (SControl 0)
[    1.982345] ata2.01: failed to resume link (SControl 0)
[    2.138229] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 330)
[    2.138250] ata1.01: SATA link down (SStatus 0 SControl 0)
[    2.138404] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 330)
[    2.138418] ata2.01: SATA link down (SStatus 0 SControl 0)
[    2.138427] ata2.01: link offline, clearing class 3 to NONE
[    2.146564] ata2.00: ATAPI: ATAPI   iHAS122   C, XL09, max UDMA/100
[    2.147189] ata1.00: ATA-9: WDC WD20EZRX-00DC0B0, 80.00A80, max UDMA/133
[    2.147193] ata1.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.155179] ata1.00: configured for UDMA/133
[    2.155409] scsi 0:0:0:0: Direct-Access     ATA      WDC WD20EZRX-00D 0A80 PQ: 0 ANSI: 5
[    2.155784] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.155791] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.155793] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.156017] sd 0:0:0:0: [sda] Write Protect is off
[    2.156028] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.156156] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.162384] ata2.00: configured for UDMA/100
[    2.164680] scsi 1:0:0:0: CD-ROM            ATAPI    iHAS122   C      XL09 PQ: 0 ANSI: 5
[    2.175983]  sda: sda1 sda2 sda3
[    2.176716] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.181069] sr 1:0:0:0: [sr0] scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.181073] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.181240] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.181326] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.181787] Freeing unused kernel memory: 1408K (ffffffff81d36000 - ffffffff81e96000)
[    2.181789] Write protecting the kernel read-only data: 12288k
[    2.182022] Freeing unused kernel memory: 188K (ffff8800017d1000 - ffff880001800000)
[    2.182157] Freeing unused kernel memory: 344K (ffff880001baa000 - ffff880001c00000)
[    2.188130] random: systemd-udevd urandom read with 19 bits of entropy available
[    2.201883] hidraw: raw HID events driver (C) Jiri Kosina
[    2.203070] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.203080] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    2.203854] r8169 0000:03:00.0 eth0: RTL8168f/8111f at 0xffffc900018b4000, 30:85:a9:f7:33:41, XID 08000800 IRQ 26
[    2.203857] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.220900] usbcore: registered new interface driver usbhid
[    2.220911] usbhid: USB HID core driver
[    2.222371] input: Microsoft SideWinder Joystick as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/0003:045E:003C.0001/input/input5
[    2.222455] hid-generic 0003:045E:003C.0001: input,hidraw0: USB HID v1.10 Joystick [Microsoft SideWinder Joystick] on usb-0000:00:1a.0-1.3/input0
[    2.222548] input: DELL Dell USB Entry Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/0003:413C:2107.0002/input/input6
[    2.278246] hid-generic 0003:413C:2107.0002: input,hidraw1: USB HID v1.11 Keyboard [DELL Dell USB Entry Keyboard] on usb-0000:00:1d.0-1.4/input0
[    2.278367] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/0003:045E:0745.0003/input/input7
[    2.334328] hid-generic 0003:045E:0745.0003: input,hidraw2: USB HID v1.11 Keyboard [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:1a.0-1.4/input0
[    2.334540] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.1/0003:045E:0745.0004/input/input8
[    2.390371] hid-generic 0003:045E:0745.0004: input,hidraw3: USB HID v1.11 Mouse [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:1a.0-1.4/input1
[    2.400670] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.2/0003:045E:0745.0005/input/input9
[    2.454137] hid-generic 0003:045E:0745.0005: input,hiddev0,hidraw4: USB HID v1.11 Device [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:1a.0-1.4/input2
[    2.470162] Switched to clocksource tsc
[    2.680819] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.252033] systemd[1]: Inserted module 'autofs4'
[    3.326361] systemd[1]: systemd 219 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT -GNUTLS +ACL +XZ -LZ4 -SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[    3.326477] systemd[1]: Detected architecture x86-64.
[    3.329030] systemd[1]: Set hostname to <blacktower>.
[    3.575131] random: nonblocking pool is initialized
[    4.355584] systemd[1]: Cannot add dependency job for unit gssproxy.service, ignoring: Unit gssproxy.service failed to load: No such file or directory.
[    4.355960] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    4.355967] systemd[1]: Starting Forward Password Requests to Wall Directory Watch.
[    4.356171] systemd[1]: Dependency failed for pNFS block layout mapping daemon.
[    4.356204] systemd[1]: Job nfs-blkmap.service/start failed with result 'dependency'.
[    4.356371] systemd[1]: Reached target Encrypted Volumes.
[    4.356376] systemd[1]: Starting Encrypted Volumes.
[    4.356539] systemd[1]: Reached target Swap.
[    4.356543] systemd[1]: Starting Swap.
[    4.356802] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    4.356808] systemd[1]: Starting Arbitrary Executable File Formats File System Automount Point.
[    4.356989] systemd[1]: Created slice Root Slice.
[    4.356995] systemd[1]: Starting Root Slice.
[    4.357171] systemd[1]: Listening on udev Control Socket.
[    4.357177] systemd[1]: Starting udev Control Socket.
[    4.357349] systemd[1]: Listening on udev Kernel Socket.
[    4.357353] systemd[1]: Starting udev Kernel Socket.
[    4.357564] systemd[1]: Created slice System Slice.
[    4.357573] systemd[1]: Starting System Slice.
[    4.357781] systemd[1]: Created slice system-getty.slice.
[    4.357786] systemd[1]: Starting system-getty.slice.
[    4.358060] systemd[1]: Starting Increase datagram queue length...
[    4.358442] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    4.358450] systemd[1]: Starting system-systemd\x2dfsck.slice.
[    4.358676] systemd[1]: Listening on Journal Audit Socket.
[    4.358681] systemd[1]: Starting Journal Audit Socket.
[    4.358858] systemd[1]: Listening on fsck to fsckd communication Socket.
[    4.358863] systemd[1]: Starting fsck to fsckd communication Socket.
[    4.359051] systemd[1]: Listening on Journal Socket.
[    4.359059] systemd[1]: Starting Journal Socket.
[    4.359316] systemd[1]: Starting Setup Virtual Console...
[    4.359717] systemd[1]: Starting Uncomplicated firewall...
[    4.448731] systemd[1]: Starting Load Kernel Modules...
[    4.449195] systemd[1]: Mounting Huge Pages File System...
[    4.449601] systemd[1]: Mounting Debug File System...
[    4.449974] systemd[1]: Mounting RPC Pipe File System...
[    4.450361] systemd[1]: Mounting POSIX Message Queue File System...
[    4.450956] systemd[1]: Started Read required files in advance.
[    4.451107] systemd[1]: Starting Read required files in advance...
[    4.451532] systemd[1]: Starting Nameserver information manager...
[    4.452145] systemd[1]: Started Braille Device Support.
[    4.452175] systemd[1]: Starting Braille Device Support...
[    4.452572] systemd[1]: Mounting NFSD configuration filesystem...
[    4.541858] systemd[1]: Started Set Up Additional Binary Formats.
[    4.542173] systemd[1]: Starting udev Coldplug all Devices...
[    4.542323] systemd[1]: Started Kernel Module supporting RPCSEC_GSS.
[    4.542646] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    4.543019] systemd[1]: Created slice User and Session Slice.
[    4.543028] systemd[1]: Starting User and Session Slice.
[    4.543203] systemd[1]: Reached target Slices.
[    4.543208] systemd[1]: Starting Slices.
[    4.543405] systemd[1]: Listening on Journal Socket (/dev/log).
[    4.543412] systemd[1]: Starting Journal Socket (/dev/log).
[    4.543604] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    4.543609] systemd[1]: Starting /dev/initctl Compatibility Named Pipe.
[    4.543801] systemd[1]: Listening on Delayed Shutdown Socket.
[    4.543808] systemd[1]: Starting Delayed Shutdown Socket.
[    4.544510] systemd[1]: Started Setup Virtual Console.
[    4.558909] systemd[1]: Started Uncomplicated firewall.
[    4.650542] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    4.651434] systemd[1]: Starting Create Static Device Nodes in /dev...
[    4.715714] systemd[1]: Mounted POSIX Message Queue File System.
[    4.715943] systemd[1]: Mounted Debug File System.
[    4.716138] systemd[1]: Mounted Huge Pages File System.
[    4.716639] systemd[1]: Started Increase datagram queue length.
[    4.721959] systemd[1]: Listening on Syslog Socket.
[    4.721967] systemd[1]: Starting Syslog Socket.
[    4.722266] systemd[1]: Starting Journal Service...
[    4.750909] systemd[1]: Started Nameserver information manager.
[    4.804779] systemd[1]: Started udev Coldplug all Devices.
[    4.805603] systemd[1]: Starting udev Wait for Complete Device Initialization...
[    4.853571] lp: driver loaded but no devices found
[    4.888624] ppdev: user-space parallel port driver
[    4.944361] RPC: Registered named UNIX socket transport module.
[    4.944363] RPC: Registered udp transport module.
[    4.944363] RPC: Registered tcp transport module.
[    4.944364] RPC: Registered tcp NFSv4.1 backchannel transport module.
[    4.945005] systemd[1]: Mounted RPC Pipe File System.
[    5.226931] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[    5.227561] systemd[1]: Mounted NFSD configuration filesystem.
[    5.257150] nct6775: Found NCT6779D or compatible chip at 0x2e:0x290
[    5.258228] systemd[1]: Started Load Kernel Modules.
[    5.259087] systemd[1]: Mounting FUSE Control File System...
[    5.259514] systemd[1]: Starting Apply Kernel Variables...
[    5.259677] systemd[1]: Mounted Configuration File System.
[    5.260397] systemd[1]: Mounted FUSE Control File System.
[    5.342537] systemd[1]: Started Journal Service.
[    6.462765] wmi: Mapper loaded
[    6.601361] EDAC MC: Ver: 3.0.0
[    6.613470] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20141107/utaddress-258)
[    6.613475] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    6.613477] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20141107/utaddress-258)
[    6.613479] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\_SB_.PCI0.LPCB.GPBX) (20141107/utaddress-258)
[    6.613481] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    6.613482] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20141107/utaddress-258)
[    6.613483] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\_SB_.PCI0.LPCB.GPBX) (20141107/utaddress-258)
[    6.613485] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    6.613485] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20141107/utaddress-258)
[    6.613487] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\_SB_.PCI0.LPCB.GPBX) (20141107/utaddress-258)
[    6.613490] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    6.613491] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    6.686827] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    6.787784] asus_wmi: ASUS WMI generic driver loaded
[    6.822823] asus_wmi: Initialization: 0x0
[    6.822836] asus_wmi: BIOS WMI version: 0.9
[    6.822857] asus_wmi: SFUN value: 0x0
[    6.823030] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input10
[    6.823511] asus_wmi: Disabling ACPI video driver
[    6.927892] AVX version of gcm_enc/dec engaged.
[    6.927894] AES CTR mode by8 optimization enabled
[    7.132682] snd_hda_intel 0000:01:00.1: Disabling MSI
[    7.132687] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    7.135177] [drm] Initialized drm 1.1.0 20060810
[    7.219055] sound hdaudioC0D0: autoconfig: line_outs=1 (0x1c/0x0/0x0/0x0/0x0) type:line
[    7.219058] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    7.219059] sound hdaudioC0D0:    hp_outs=1 (0x1d/0x0/0x0/0x0/0x0)
[    7.219060] sound hdaudioC0D0:    mono: mono_out=0x0
[    7.219061] sound hdaudioC0D0:    inputs:
[    7.219062] sound hdaudioC0D0:      Rear Mic=0x1a
[    7.219063] sound hdaudioC0D0:      Front Mic=0x1e
[    7.219064] sound hdaudioC0D0:      Line=0x1b
[    7.223967] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    7.224008] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    7.224042] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    7.224080] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    7.224124] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    7.691906] intel_rapl: Found RAPL domain package
[    7.691910] intel_rapl: Found RAPL domain core
[    7.749165] media: Linux media interface: v0.10
[    7.806220] Linux video capture interface: v2.00
[    7.830697] usb 2-1.6: 3:1: cannot get freq at ep 0x84
[    7.845254] usbcore: registered new interface driver snd-usb-audio
[    7.947163] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[    7.947213] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input17
[    7.947257] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input18
[    7.947322] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input19
[    8.178846] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62f1)
[    8.183306] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input20
[    8.183379] usbcore: registered new interface driver uvcvideo
[    8.183380] USB Video Class driver (1.1.1)
[    9.258916] nvidia: module license 'NVIDIA' taints kernel.
[    9.258919] Disabling lock debugging due to kernel taint
[    9.261291] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[    9.264378] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    9.264568] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 0
[    9.264573] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  340.76  Thu Jan 22 12:11:08 PST 2015
[    9.971787] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.183421] systemd-journald[279]: Received request to flush runtime journal from PID 1
[   10.784166] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   10.901360] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   11.682603] audit: type=1400 audit(1442855500.350:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=626 comm="apparmor_parser"
[   11.682610] audit: type=1400 audit(1442855500.350:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=626 comm="apparmor_parser"
[   11.743411] audit: type=1400 audit(1442855500.414:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=626 comm="apparmor_parser"
[   11.743415] audit: type=1400 audit(1442855500.414:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=626 comm="apparmor_parser"
[   11.743418] audit: type=1400 audit(1442855500.414:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=626 comm="apparmor_parser"
[   11.743420] audit: type=1400 audit(1442855500.414:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=626 comm="apparmor_parser"
[   11.829571] audit: type=1400 audit(1442855500.498:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=626 comm="apparmor_parser"
[   11.829575] audit: type=1400 audit(1442855500.498:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=626 comm="apparmor_parser"
[   11.829578] audit: type=1400 audit(1442855500.498:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=626 comm="apparmor_parser"
[   11.829580] audit: type=1400 audit(1442855500.498:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=626 comm="apparmor_parser"
[   12.218036] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.234778] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   21.055349] cgroup: new mount options do not match the existing superblock, will be ignored
[   22.437487] cfg80211: Calling CRDA to update world regulatory domain
[   22.454499] cfg80211: World regulatory domain updated:
[   22.454501] cfg80211:  DFS Master region: unset
[   22.454502] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   22.454504] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   22.454505] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   22.454506] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   22.454507] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   22.454508] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   22.454509] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   22.454510] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   22.454511] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   22.509173] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   22.534635] NFSD: starting 90-second grace period (net ffffffff81ce4e40)
[   22.741094] r8169 0000:03:00.0 eth0: link down
[   22.741113] r8169 0000:03:00.0 eth0: link down
[   24.295499] r8169 0000:03:00.0 eth0: link up
[   30.000390] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   30.127916] vboxdrv: Found 8 processor cores.
[   30.128208] vboxdrv: fAsync=0 offMin=0x1e2 offMax=0xfac2
[   30.128264] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   30.128265] vboxdrv: Successfully loaded version 4.3.26_Ubuntu (interface 0x001a000a).
[   30.136925] vboxpci: IOMMU not found (not registered)
[   37.492849] usb 2-1.6: 3:1: cannot get freq at ep 0x84
[   37.514806] usb 2-1.6: 3:1: cannot get freq at ep 0x84
[   37.543923] usb 2-1.6: 3:1: cannot get freq at ep 0x84
[   37.566033] usb 2-1.6: 3:1: cannot get freq at ep 0x84
[   47.014850] usb 2-1.6: 3:1: cannot get freq at ep 0x84
[   47.036812] usb 2-1.6: 3:1: cannot get freq at ep 0x84
[   47.066924] usb 2-1.6: 3:1: cannot get freq at ep 0x84
[   47.088929] usb 2-1.6: 3:1: cannot get freq at ep 0x84
[ 3294.093796] usb 2-1.6: 3:1: cannot get freq at ep 0x84
[ 3294.115782] usb 2-1.6: 3:1: cannot get freq at ep 0x84
[ 3294.153923] usb 2-1.6: 3:1: cannot get freq at ep 0x84
[ 3294.175870] usb 2-1.6: 3:1: cannot get freq at ep 0x84
[ 3299.009042] show_signal_msg: 48 callbacks suppressed
[ 3299.009049] lightdm[1354]: segfault at 10 ip 00007fe8c44bcc84 sp 00007ffde8cb84e0 error 4 in libpthread-2.21.so[7fe8c44b3000+18000]
```

---

### Post by Bucky Ball on 2015-09-21
You login, check this file with this command:

```
nano /etc/lightdm/lightdm.conf
```

... and look for this line:

```
greeter-session=unity-greeter 
```

Do you have the same or is that line not there?

Get your wife to log in and check that file and that line. Is it the same? Just a (very wild) stab in the dark ...

---

### Post by tornadof3 on 2015-09-23
Thank you for the response; sorry for delay

so in /etc/lightdm there is no lightdm.conf; the only file is users.conf:

```
:/etc/lightdm$ cat users.conf 
#
# User accounts configuration
#
# NOTE: If you have AccountsService installed on your system, then LightDM will
# use this instead and these settings will be ignored
#
# minimum-uid = Minimum UID required to be shown in greeter
# hidden-users = Users that are not shown to the user
# hidden-shells = Shells that indicate a user cannot login
#
[UserList]
minimum-uid=500
hidden-users=nobody nobody4 noaccess
hidden-shells=/bin/false /usr/sbin/nologin

```

is this good or bad?

---

