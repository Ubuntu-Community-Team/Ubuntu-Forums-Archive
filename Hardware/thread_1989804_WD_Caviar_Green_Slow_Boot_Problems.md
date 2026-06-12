---
title: "WD Caviar Green Slow Boot Problems"
date: 2012-05-28
forum: Hardware
---

### Post by Alaric on 2012-05-28
I'm having pretty aggravating problems with my WD15EARS and WD20EARS sata hard disks running with my Gigabyte 880GA-UD3H motherboard ([http://www.gigabyte.us/products/product-page.aspx?pid=3758](http://www.gigabyte.us/products/product-page.aspx?pid=3758)).  I'm booting off of a smaller seagate sata drive and I manage to start up in about 45 seconds from grub to login (also odd since I'm running a 6-core 3.2ghz processor).  When I connect either of the WD Caviar Green drives the boot time shoots up to about 3 and a half minutes, which is clearly unacceptable.  Additionally, all methods of installing any version of ubuntu onto  the drive fails because it appears that it would take more than a day to finish.  I've lost my most dmesg log, but I'll try to grab a new one and post it soon.  

Once the drives get booted properly I can manage to read and write to single files with approximately expected speeds, but booting, mounting, and running LS on a drive lag beyond all expectations.  I've checked the drive with WD align and attempted to format it several times with partitions starting on the 2048, 64, and 63 sectors with no performance increase using NTFS or EXT3/4.  My Windows Dual-boot boots up a bit slower with the drives, but nothing close to 3.5 minutes.  

Is this drive incompatible with recent Ubuntu distributions (I'm trying 11.10 and 12.04)?  Does the motherboard have known issues with SATA III?  Has anyone had any luck getting help from WD on this type of issue (I bought the drives on EBay, so there's probably no warranty)? Any information you can provide would be much appreciated. 

The closest thing I've found on the forums to this issue is linked below, but although the hardware is similar they seem to be experiencing different symptoms.  They're also using Caviar Green and a gigabyte board, but can't seem to even have the drive appear in the BIOS.  
[http://ubuntuforums.org/showthread.php?t=1968693](http://ubuntuforums.org/showthread.php?t=1968693)

---

### Post by ahallubuntu on 2012-05-28
I have a couple of these green WD drives too.  You definitely want partitions aligned on the 2048 byte boundary.   I found that starting with Ubuntu 11.04 Gparted automatically recognizes them as advanced format drives and will align the partitions for you.  You can verify that with fdisk - sounds like you already know how to do that, but if not, try

sudo fdisk -lu /dev/sda

if /dev/sda is your drive.  If it starts at 63, you need to align the partition - really recommend 2048 as Gparted will automatically do with the newer OSes.

My drives do not have any performance issues in Ubuntu 10.04 LTS (though I created the partitions with an 11.04 installation).  Boot isn't slow, mounting isn't slow, performance is a bit slow compared to "regular" drives, but these are for data storage and are low power/5900RPM drives, so I don't expect them to be fast.

NTFS will be slower than ext3/4 because the fuse driver in Ubuntu seems to eat CPU especially operating on large files.

For fun, have you checked S.M.A.R.T. on these drives to confirm that there is nothing wrong with them?  Did you consider looking at how the BIOS of your motherboard is configured for SATA?

---

### Post by ahallubuntu on 2012-05-28
Oh, and I wouldn't recommend trying to install an OS on a Green drive myself - you can but even if you fix whatever performance conflict you now seem to have, at 5900 RPM you're not going to get good performance.

---

### Post by Alaric on 2012-05-28
Thanks for the response Ahallu, I'm glad to hear someone has gotten these drives to work.  I'll definitely have to take that recommendation on not installing it as an OS drive into consideration, but with my current wimpy power supply I might still resort to it due to limited SATA plugs.  I believe it would be noticable, but I'm more concerned about redundancy at the moment, which is why I'm attempting to install both caviar drives (the 1.5TB drive actually came out of an external).  

My 3.5 minute time came from the 1.5TB that I believe is formatted to initial sector 63, so I started up the 2TB formatted to 2048s, and came up with 2.75, so there might be some improvement, but in my mind it's probably read-speed based which would support the theory that there's a deeper underlying issue here.  

Back to the matter at hand, I've been up and down the BIOS screen looking for SATA options to tweak, but haven't really come up with much.  For good measure I also tried resetting the BIOS settings to factory default and "failsafe" modes to no avail.  Here's the fdisk you asked for.  Is the sector size supposed to be reported as 512-bytes?  That's one place that had concerned me earlier, but I haven't found any example fdisk's that actually show the 4096, probably because of the Windows XP compatability "virtual sectors" or whatever.  

```
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001edb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1048578047   524288000    7  HPFS/NTFS/exFAT
/dev/sdb2      1048578048  3907028991  1429225472    5  Extended
/dev/sdb5      1048580096  3145732095  1048576000   83  Linux
/dev/sdb6      3145734144  3355449343   104857600   83  Linux
/dev/sdb7      3355451392  3565166591   104857600   83  Linux
/dev/sdb8      3565168640  3774883839   104857600   83  Linux
/dev/sdb9      3774885888  3907028991    66071552   82  Linux swap / Solaris
```

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-17-generic (buildd@yellow) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 (Ubuntu 3.0.0-17.30-generic 3.0.22)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=15df7561-2088-479e-a23b-b91bea21181d ro quiet splash radeon.audio=1 vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfdf0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfdf0000 - 00000000cfdf1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfdf1000 - 00000000cfe00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfe00000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000330000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. GA-880GA-UD3H/GA-880GA-UD3H, BIOS FF 03/07/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x330000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 base 0000CFE00000 mask FFFFFFE00000 uncachable
[    0.000000]   4 base 000100000000 mask FFFF00000000 write-back
[    0.000000]   5 base 000200000000 mask FFFF00000000 write-back
[    0.000000]   6 base 000300000000 mask FFFFE0000000 write-back
[    0.000000]   7 base 000320000000 mask FFFFF0000000 write-back
[    0.000000] TOM2: 0000000330000000 aka 13056M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3326MB, range: 2MB, type UC
[    0.000000] reg 4, base: 4GB, range: 4GB, type WB
[    0.000000] reg 5, base: 8GB, range: 4GB, type WB
[    0.000000] reg 6, base: 12GB, range: 512MB, type WB
[    0.000000] reg 7, base: 12800MB, range: 256MB, type WB
[    0.000000] total RAM covered: 3326M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 4M 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3326MB, range: 2MB, type UC
[    0.000000] e820 update range: 00000000cfe00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcfdf0 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000f4a20] f4a20
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfdf0000
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfc00000 page 2M
[    0.000000]  00cfc00000 - 00cfdf0000 page 4k
[    0.000000] kernel direct mapping tables up to cfdf0000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000330000000
[    0.000000]  0100000000 - 0300000000 page 1G
[    0.000000]  0300000000 - 0330000000 page 2M
[    0.000000] kernel direct mapping tables up to 330000000 @ cfdee000-cfdf0000
[    0.000000] RAMDISK: 35a82000 - 36d39000
[    0.000000] ACPI: RSDP 00000000000f6470 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 00000000cfdf1000 00040 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 00000000cfdf1080 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 00000000cfdf1100 076DC (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000cfdf0000 00040
[    0.000000] ACPI: SSDT 00000000cfdf88c0 00EDC (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 00000000cfdf97c0 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 00000000cfdf9800 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: MATS 00000000cfdf9840 00034 (v01 GBT             00000000      00000000)
[    0.000000] ACPI: TAMG 00000000cfdf98b0 00202 (v01 GBT    GBT   B0 5455312E BG?? 53450101)
[    0.000000] ACPI: APIC 00000000cfdf8800 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000330000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000330000000
[    0.000000]   NODE_DATA [000000032fffb000 - 000000032fffffff]
[    0.000000]  [ffffea0000000000-ffffea000b3fffff] PMD -> [ffff880323600000-ffff88032dffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00330000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cfdf0
[    0.000000]     0: 0x00100000 -> 0x00330000
[    0.000000] On node 0 totalpages: 3145087
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3922 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833064 pages, LIFO batch:31
[    0.000000]   Normal zone: 31360 pages used for memmap
[    0.000000]   Normal zone: 2262400 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfdf0000 - 00000000cfdf1000
[    0.000000] PM: Registered nosave memory: 00000000cfdf1000 - 00000000cfe00000
[    0.000000] PM: Registered nosave memory: 00000000cfe00000 - 00000000cff00000
[    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at cff00000 (gap: cff00000:10100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88032fc00000 s79616 r8192 d22784 u262144
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 3099386
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=15df7561-2088-479e-a23b-b91bea21181d ro quiet splash radeon.audio=1 vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ c4000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 12239036k/13369344k available (6140k kernel code, 788996k absent, 341312k reserved, 6894k data, 988k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 100663296 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3214.505 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 6429.01 BogoMIPS (lpj=12858020)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004029] Security Framework initialized
[    0.004039] AppArmor: AppArmor initialized
[    0.004040] Yama: becoming mindful.
[    0.005153] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.011456] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.013513] Mount-cache hash table entries: 256
[    0.013621] Initializing cgroup subsys cpuacct
[    0.013626] Initializing cgroup subsys memory
[    0.013633] Initializing cgroup subsys devices
[    0.013635] Initializing cgroup subsys freezer
[    0.013636] Initializing cgroup subsys net_cls
[    0.013638] Initializing cgroup subsys blkio
[    0.013644] Initializing cgroup subsys perf_event
[    0.013665] tseg: 00cff00000
[    0.013667] CPU: Physical Processor ID: 0
[    0.013668] CPU: Processor Core ID: 0
[    0.013670] mce: CPU supports 6 MCE banks
[    0.013678] using AMD E400 aware idle routine
[    0.014778] ACPI: Core revision 20110413
[    0.020031] ftrace: allocating 25750 entries in 101 pages
[    0.024586] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.064978] CPU0: AMD Phenom(tm) II X6 1090T Processor stepping 00
[    0.068003] Performance Events: AMD PMU driver.
[    0.068003] ... version:                0
[    0.068003] ... bit width:              48
[    0.068003] ... generic registers:      4
[    0.068003] ... value mask:             0000ffffffffffff
[    0.068003] ... max period:             00007fffffffffff
[    0.068003] ... fixed-purpose events:   0
[    0.068003] ... event mask:             000000000000000f
[    0.068003] Booting Node   0, Processors  #1
[    0.068003] smpboot cpu 1: start_ip = 9a000
[    0.156020] System has AMD C1E enabled
[    0.156035] Switch to broadcast mode on CPU1
[    0.156062]  #2
[    0.156063] smpboot cpu 2: start_ip = 9a000
[    0.248029] Switch to broadcast mode on CPU2
[    0.248068]  #3
[    0.248069] smpboot cpu 3: start_ip = 9a000
[    0.340035] Switch to broadcast mode on CPU3
[    0.340075]  #4
[    0.340076] smpboot cpu 4: start_ip = 9a000
[    0.432044] Switch to broadcast mode on CPU4
[    0.432088]  #5
[    0.432089] smpboot cpu 5: start_ip = 9a000
[    0.524055] Brought up 6 CPUs
[    0.524057] Total of 6 processors activated (38570.56 BogoMIPS).
[    0.524054] Switch to broadcast mode on CPU5
[    0.527745] Switch to broadcast mode on CPU0
[    0.527745] devtmpfs: initialized
[    0.527745] PM: Registering ACPI NVS region at cfdf0000 (4096 bytes)
[    0.528930] print_constraints: dummy: 
[    0.528950] Time: 23:26:51  Date: 05/28/12
[    0.528977] NET: Registered protocol family 16
[    0.529066] node 0 link 0: io port [9000, ffff]
[    0.529068] TOM: 00000000d0000000 aka 3328M
[    0.529070] Fam 10h mmconf [mem 0xe0000000-0xe00fffff]
[    0.529072] node 0 link 0: mmio [a0000, bffff]
[    0.529075] node 0 link 0: mmio [d0000000, dfffffff]
[    0.529077] node 0 link 0: mmio [f0000000, fe02ffff]
[    0.529078] node 0 link 0: mmio [e0000000, e06fffff] ==> [e0100000, e06fffff]
[    0.529081] TOM2: 0000000330000000 aka 13056M
[    0.529082] bus: [00, 06] on node 0 link 0
[    0.529084] bus: 00 index 0 [io  0x0000-0xffff]
[    0.529085] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.529086] bus: 00 index 2 [mem 0xd0000000-0xdfffffff]
[    0.529088] bus: 00 index 3 [mem 0xe0700000-0xffffffff]
[    0.529089] bus: 00 index 4 [mem 0xe0100000-0xe06fffff]
[    0.529090] bus: 00 index 5 [mem 0x330000000-0xfcffffffff]
[    0.529098] Extended Config Space enabled on 1 nodes
[    0.529133] ACPI: bus type pci registered
[    0.528984] Trying to unpack rootfs image as initramfs...
[    0.529174] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.529177] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.545632] PCI: Using configuration type 1 for base access
[    0.546097] bio: create slab <bio-0> at 0
[    0.546097] ACPI: EC: Look up EC in DSDT
[    0.546097] ACPI: Actual Package length (1) is larger than NumElements field (0), truncated
[    0.546097] 
[    0.546097] ACPI: Actual Package length (1) is larger than NumElements field (0), truncated
[    0.546097] 
[    0.546097] ACPI: Actual Package length (1) is larger than NumElements field (0), truncated
[    0.546097] 
[    0.546097] ACPI: Actual Package length (1) is larger than NumElements field (0), truncated
[    0.546097] 
[    0.552121] ACPI Warning: Incorrect checksum in table [TAMG] - 0x45, should be 0x44 (20110413/tbutils-314)
[    0.552214] ACPI: Interpreter enabled
[    0.552217] ACPI: (supports S0 S3 S4 S5)
[    0.552231] ACPI: Using IOAPIC for interrupt routing
[    0.701543] ACPI: No dock devices found.
[    0.701545] HEST: Table not found.
[    0.701548] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.701591] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.701671] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.701673] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.701675] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.701676] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
[    0.701678] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xfebfffff]
[    0.701690] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
[    0.701700] pci 0000:00:00.0: reg 1c: [mem 0xe0000000-0xffffffff 64bit]
[    0.701735] pci 0000:00:02.0: [1022:9603] type 1 class 0x000604
[    0.701763] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.701766] pci 0000:00:02.0: PME# disabled
[    0.701782] pci 0000:00:09.0: [1022:9608] type 1 class 0x000604
[    0.701809] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    0.701811] pci 0000:00:09.0: PME# disabled
[    0.701821] pci 0000:00:0a.0: [1022:9609] type 1 class 0x000604
[    0.701848] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.701850] pci 0000:00:0a.0: PME# disabled
[    0.701872] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
[    0.701888] pci 0000:00:11.0: reg 10: [io  0xff00-0xff07]
[    0.701896] pci 0000:00:11.0: reg 14: [io  0xfe00-0xfe03]
[    0.701904] pci 0000:00:11.0: reg 18: [io  0xfd00-0xfd07]
[    0.701912] pci 0000:00:11.0: reg 1c: [io  0xfc00-0xfc03]
[    0.701920] pci 0000:00:11.0: reg 20: [io  0xfb00-0xfb0f]
[    0.701928] pci 0000:00:11.0: reg 24: [mem 0xfe02f000-0xfe02f3ff]
[    0.701945] pci 0000:00:11.0: set SATA to AHCI mode
[    0.701987] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.701998] pci 0000:00:12.0: reg 10: [mem 0xfe02e000-0xfe02efff]
[    0.702061] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.702077] pci 0000:00:12.2: reg 10: [mem 0xfe02d000-0xfe02d0ff]
[    0.702147] pci 0000:00:12.2: supports D1 D2
[    0.702149] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.702152] pci 0000:00:12.2: PME# disabled
[    0.702169] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.702180] pci 0000:00:13.0: reg 10: [mem 0xfe02c000-0xfe02cfff]
[    0.702241] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.702257] pci 0000:00:13.2: reg 10: [mem 0xfe02b000-0xfe02b0ff]
[    0.702327] pci 0000:00:13.2: supports D1 D2
[    0.702328] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.702332] pci 0000:00:13.2: PME# disabled
[    0.702349] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.702411] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.702422] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.702430] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.702438] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.702446] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.702454] pci 0000:00:14.1: reg 20: [io  0xfa00-0xfa0f]
[    0.702486] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.702504] pci 0000:00:14.2: reg 10: [mem 0xfe024000-0xfe027fff 64bit]
[    0.702560] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.702564] pci 0000:00:14.2: PME# disabled
[    0.702575] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.702639] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.702676] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.702688] pci 0000:00:14.5: reg 10: [mem 0xfe02a000-0xfe02afff]
[    0.702748] pci 0000:00:15.0: [1002:43a0] type 1 class 0x000604
[    0.702812] pci 0000:00:15.0: supports D1 D2
[    0.702833] pci 0000:00:15.1: [1002:43a1] type 1 class 0x000604
[    0.702897] pci 0000:00:15.1: supports D1 D2
[    0.702920] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
[    0.702931] pci 0000:00:16.0: reg 10: [mem 0xfe029000-0xfe029fff]
[    0.702992] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
[    0.703008] pci 0000:00:16.2: reg 10: [mem 0xfe028000-0xfe0280ff]
[    0.703078] pci 0000:00:16.2: supports D1 D2
[    0.703079] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.703083] pci 0000:00:16.2: PME# disabled
[    0.703099] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.703111] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.703122] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.703134] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.703147] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.703189] pci 0000:01:00.0: [1002:6758] type 0 class 0x000300
[    0.703202] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.703212] pci 0000:01:00.0: reg 18: [mem 0xfdec0000-0xfdedffff 64bit]
[    0.703219] pci 0000:01:00.0: reg 20: [io  0xee00-0xeeff]
[    0.703231] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.703262] pci 0000:01:00.0: supports D1 D2
[    0.703282] pci 0000:01:00.1: [1002:aa90] type 0 class 0x000403
[    0.703295] pci 0000:01:00.1: reg 10: [mem 0xfdefc000-0xfdefffff 64bit]
[    0.703353] pci 0000:01:00.1: supports D1 D2
[    0.708063] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.708067] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.708070] pci 0000:00:02.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.708073] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.708108] pci 0000:02:00.0: [1033:0194] type 0 class 0x000c03
[    0.708122] pci 0000:02:00.0: reg 10: [mem 0xfdbfe000-0xfdbfffff 64bit]
[    0.708191] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.708194] pci 0000:02:00.0: PME# disabled
[    0.716062] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.716067] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
[    0.716069] pci 0000:00:09.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.716072] pci 0000:00:09.0:   bridge window [mem 0xfd600000-0xfd6fffff 64bit pref]
[    0.716106] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
[    0.716118] pci 0000:03:00.0: reg 10: [io  0xce00-0xceff]
[    0.716136] pci 0000:03:00.0: reg 18: [mem 0xfdfff000-0xfdffffff 64bit pref]
[    0.716148] pci 0000:03:00.0: reg 20: [mem 0xfdff8000-0xfdffbfff 64bit pref]
[    0.716201] pci 0000:03:00.0: supports D1 D2
[    0.716202] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.716206] pci 0000:03:00.0: PME# disabled
[    0.724064] pci 0000:00:0a.0: PCI bridge to [bus 03-03]
[    0.724068] pci 0000:00:0a.0:   bridge window [io  0xc000-0xcfff]
[    0.724071] pci 0000:00:0a.0:   bridge window [mem 0xfd500000-0xfd5fffff]
[    0.724074] pci 0000:00:0a.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.724107] pci 0000:04:06.0: [168c:001a] type 0 class 0x000200
[    0.724127] pci 0000:04:06.0: reg 10: [mem 0xfdde0000-0xfddeffff]
[    0.724258] pci 0000:00:14.4: PCI bridge to [bus 04-04] (subtractive decode)
[    0.724262] pci 0000:00:14.4:   bridge window [io  0xb000-0xbfff]
[    0.724265] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.724268] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff pref]
[    0.724270] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.724272] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.724274] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.724275] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.724277] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xfebfffff] (subtractive decode)
[    0.724334] pci 0000:05:00.0: [197b:2363] type 0 class 0x000101
[    0.724422] pci 0000:05:00.0: reg 24: [mem 0xfdafe000-0xfdafffff]
[    0.724485] pci 0000:05:00.0: PME# supported from D3hot
[    0.724490] pci 0000:05:00.0: PME# disabled
[    0.724523] pci 0000:05:00.1: [197b:2363] type 0 class 0x000101
[    0.724547] pci 0000:05:00.1: reg 10: [io  0xaf00-0xaf07]
[    0.724560] pci 0000:05:00.1: reg 14: [io  0xae00-0xae03]
[    0.724573] pci 0000:05:00.1: reg 18: [io  0xad00-0xad07]
[    0.724586] pci 0000:05:00.1: reg 1c: [io  0xac00-0xac03]
[    0.724599] pci 0000:05:00.1: reg 20: [io  0xab00-0xab0f]
[    0.724682] pci 0000:05:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.724695] pci 0000:00:15.0: PCI bridge to [bus 05-05]
[    0.724699] pci 0000:00:15.0:   bridge window [io  0xa000-0xafff]
[    0.724702] pci 0000:00:15.0:   bridge window [mem 0xfda00000-0xfdafffff]
[    0.724707] pci 0000:00:15.0:   bridge window [mem 0xfd900000-0xfd9fffff 64bit pref]
[    0.724748] pci 0000:00:15.1: PCI bridge to [bus 06-06]
[    0.724753] pci 0000:00:15.1:   bridge window [io  0x9000-0x9fff]
[    0.724756] pci 0000:00:15.1:   bridge window [mem 0xfd800000-0xfd8fffff]
[    0.724760] pci 0000:00:15.1:   bridge window [mem 0xfd700000-0xfd7fffff 64bit pref]
[    0.724781] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.724957] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.724977] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.725001] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.725044] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.725070] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]
[    0.725089] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.725110]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.725112]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.725113] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.732464] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0
[    0.732493] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0
[    0.732518] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0
[    0.732543] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0
[    0.732567] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0
[    0.732592] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0
[    0.732616] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0
[    0.732641] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0
[    0.732723] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.732726] vgaarb: loaded
[    0.732727] vgaarb: bridge control possible 0000:01:00.0
[    0.732854] SCSI subsystem initialized
[    0.732875] libata version 3.00 loaded.
[    0.732875] usbcore: registered new interface driver usbfs
[    0.732875] usbcore: registered new interface driver hub
[    0.732875] usbcore: registered new device driver usb
[    0.732875] PCI: Using ACPI for IRQ routing
[    0.740453] PCI: pci_cache_line_size set to 64 bytes
[    0.740460] pci 0000:00:00.0: no compatible bridge window for [mem 0xe0000000-0xffffffff 64bit]
[    0.740538] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.740540] reserve RAM buffer: 00000000cfdf0000 - 00000000cfffffff 
[    0.740608] NetLabel: Initializing
[    0.740610] NetLabel:  domain hash size = 128
[    0.740611] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.740620] NetLabel:  unlabeled traffic allowed by default
[    0.740648] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.740651] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.742681] Switching to clocksource hpet
[    0.742685] Switched to NOHz mode on CPU #2
[    0.742697] Switched to NOHz mode on CPU #4
[    0.742810] Switched to NOHz mode on CPU #1
[    0.742702] Switched to NOHz mode on CPU #5
[    0.742691] Switched to NOHz mode on CPU #3
[    0.742815] Switched to NOHz mode on CPU #0
[    0.744131] AppArmor: AppArmor Filesystem Enabled
[    0.744148] pnp: PnP ACPI init
[    0.744157] ACPI: bus type pnp registered
[    0.744228] pnp 00:00: [bus 00-ff]
[    0.744230] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.744232] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.744233] pnp 00:00: [io  0x0d00-0xffff window]
[    0.744235] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.744236] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.744238] pnp 00:00: [mem 0xd0000000-0xfebfffff window]
[    0.744275] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.744282] pnp 00:01: [io  0x0010-0x001f]
[    0.744283] pnp 00:01: [io  0x0022-0x003f]
[    0.744285] pnp 00:01: [io  0x0044-0x005f]
[    0.744286] pnp 00:01: [io  0x0062-0x0063]
[    0.744287] pnp 00:01: [io  0x0065-0x006f]
[    0.744289] pnp 00:01: [io  0x0074-0x007f]
[    0.744290] pnp 00:01: [io  0x0091-0x0093]
[    0.744291] pnp 00:01: [io  0x00a2-0x00bf]
[    0.744292] pnp 00:01: [io  0x00e0-0x00ef]
[    0.744294] pnp 00:01: [io  0x04d0-0x04d1]
[    0.744295] pnp 00:01: [io  0x0220-0x0225]
[    0.744296] pnp 00:01: [io  0x0290-0x0294]
[    0.744337] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.744339] system 00:01: [io  0x0220-0x0225] has been reserved
[    0.744341] system 00:01: [io  0x0290-0x0294] has been reserved
[    0.744343] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.790158] Freeing initrd memory: 19164k freed
[    0.848398] pnp 00:02: [io  0x4100-0x411f]
[    0.848401] pnp 00:02: [io  0x0228-0x022f]
[    0.848402] pnp 00:02: [io  0x040b]
[    0.848404] pnp 00:02: [io  0x04d6]
[    0.848405] pnp 00:02: [io  0x0c00-0x0c01]
[    0.848406] pnp 00:02: [io  0x0c14]
[    0.848407] pnp 00:02: [io  0x0c50-0x0c52]
[    0.848408] pnp 00:02: [io  0x0c6c-0x0c6d]
[    0.848409] pnp 00:02: [io  0x0c6f]
[    0.848410] pnp 00:02: [io  0x0cd0-0x0cd1]
[    0.848411] pnp 00:02: [io  0x0cd2-0x0cd3]
[    0.848412] pnp 00:02: [io  0x0cd4-0x0cdf]
[    0.848414] pnp 00:02: [io  0x4000-0x40fe]
[    0.848415] pnp 00:02: [io  0x4210-0x4217]
[    0.848416] pnp 00:02: [io  0x0b00-0x0b0f]
[    0.848417] pnp 00:02: [io  0x0b10-0x0b1f]
[    0.848418] pnp 00:02: [io  0x0b20-0x0b3f]
[    0.848420] pnp 00:02: [mem 0x00000000-0x00000fff window]
[    0.848421] pnp 00:02: [mem 0xfee00400-0xfee00fff window]
[    0.848429] pnp 00:02: disabling [mem 0x00000000-0x00000fff window] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.848456] pnp 00:02: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:01:00.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    0.848505] system 00:02: [io  0x4100-0x411f] has been reserved
[    0.848507] system 00:02: [io  0x0228-0x022f] has been reserved
[    0.848509] system 00:02: [io  0x040b] has been reserved
[    0.848510] system 00:02: [io  0x04d6] has been reserved
[    0.848512] system 00:02: [io  0x0c00-0x0c01] has been reserved
[    0.848514] system 00:02: [io  0x0c14] has been reserved
[    0.848515] system 00:02: [io  0x0c50-0x0c52] has been reserved
[    0.848517] system 00:02: [io  0x0c6c-0x0c6d] has been reserved
[    0.848518] system 00:02: [io  0x0c6f] has been reserved
[    0.848519] system 00:02: [io  0x0cd0-0x0cd1] has been reserved
[    0.848521] system 00:02: [io  0x0cd2-0x0cd3] has been reserved
[    0.848523] system 00:02: [io  0x0cd4-0x0cdf] has been reserved
[    0.848524] system 00:02: [io  0x4000-0x40fe] has been reserved
[    0.848526] system 00:02: [io  0x4210-0x4217] has been reserved
[    0.848527] system 00:02: [io  0x0b00-0x0b0f] has been reserved
[    0.848529] system 00:02: [io  0x0b10-0x0b1f] has been reserved
[    0.848530] system 00:02: [io  0x0b20-0x0b3f] has been reserved
[    0.848532] system 00:02: [mem 0xfee00400-0xfee00fff window] has been reserved
[    0.848535] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.848600] pnp 00:03: [dma 4]
[    0.848602] pnp 00:03: [io  0x0000-0x000f]
[    0.848603] pnp 00:03: [io  0x0080-0x0090]
[    0.848604] pnp 00:03: [io  0x0094-0x009f]
[    0.848605] pnp 00:03: [io  0x00c0-0x00df]
[    0.848623] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.848654] pnp 00:04: [io  0x0070-0x0073]
[    0.848665] pnp 00:04: [irq 8]
[    0.848684] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.848689] pnp 00:05: [io  0x0061]
[    0.848705] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.848710] pnp 00:06: [io  0x00f0-0x00ff]
[    0.848717] pnp 00:06: [irq 13]
[    0.848733] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.848832] pnp 00:07: [io  0x03f0-0x03f5]
[    0.848833] pnp 00:07: [io  0x03f7]
[    0.848839] pnp 00:07: [irq 6]
[    0.848841] pnp 00:07: [dma 2]
[    0.848871] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.848937] pnp 00:08: [io  0x0060]
[    0.848938] pnp 00:08: [io  0x0064]
[    0.848944] pnp 00:08: [irq 1]
[    0.848966] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.848985] pnp 00:09: [mem 0xe0000000-0xefffffff]
[    0.849019] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.849021] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.849102] pnp 00:0a: [mem 0x000f0000-0x000f3fff]
[    0.849104] pnp 00:0a: [mem 0x000f4000-0x000f7fff]
[    0.849107] pnp 00:0a: [mem 0x000f8000-0x000fbfff]
[    0.849108] pnp 00:0a: [mem 0x000fc000-0x000fffff]
[    0.849109] pnp 00:0a: [mem 0xcfdf0000-0xcfdfffff]
[    0.849111] pnp 00:0a: [mem 0xffff0000-0xffffffff]
[    0.849112] pnp 00:0a: [mem 0x00000000-0x0009ffff]
[    0.849113] pnp 00:0a: [mem 0x00100000-0xcfdeffff]
[    0.849115] pnp 00:0a: [mem 0xcfe00000-0xcfefffff]
[    0.849116] pnp 00:0a: [mem 0xcff00000-0xcfffffff]
[    0.849118] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.849119] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    0.849120] pnp 00:0a: [mem 0xfee00000-0xfee00fff]
[    0.849122] pnp 00:0a: [mem 0xfff80000-0xfffeffff]
[    0.849124] pnp 00:0a: disabling [mem 0x000f0000-0x000f3fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.849127] pnp 00:0a: disabling [mem 0x000f4000-0x000f7fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.849129] pnp 00:0a: disabling [mem 0x000f8000-0x000fbfff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.849132] pnp 00:0a: disabling [mem 0x000fc000-0x000fffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.849134] pnp 00:0a: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.849137] pnp 00:0a: disabling [mem 0x00100000-0xcfdeffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.849160] pnp 00:0a: [Firmware Bug]: [mem 0x00000000-0xffffffffffffffff disabled] covers only part of AMD MMCONFIG area [mem 0xe0000000-0xe00fffff]; adding more reservations
[    0.849182] system 00:0a: [mem 0xcfdf0000-0xcfdfffff] could not be reserved
[    0.849184] system 00:0a: [mem 0xffff0000-0xffffffff] has been reserved
[    0.849186] system 00:0a: [mem 0xcfe00000-0xcfefffff] has been reserved
[    0.849188] system 00:0a: [mem 0xcff00000-0xcfffffff] could not be reserved
[    0.849190] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.849192] system 00:0a: [mem 0xfee00000-0xfee00fff] could not be reserved
[    0.849193] system 00:0a: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.849195] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.849209] pnp: PnP ACPI: found 11 devices
[    0.849210] ACPI: ACPI bus type pnp unregistered
[    0.854624] PCI: max bus depth: 1 pci_try_num: 2
[    0.854654] pci 0000:01:00.0: BAR 6: assigned [mem 0xfde00000-0xfde1ffff pref]
[    0.854656] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.854659] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.854661] pci 0000:00:02.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.854663] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.854667] pci 0000:00:09.0: PCI bridge to [bus 02-02]
[    0.854668] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
[    0.854671] pci 0000:00:09.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.854673] pci 0000:00:09.0:   bridge window [mem 0xfd600000-0xfd6fffff 64bit pref]
[    0.854676] pci 0000:00:0a.0: PCI bridge to [bus 03-03]
[    0.854678] pci 0000:00:0a.0:   bridge window [io  0xc000-0xcfff]
[    0.854680] pci 0000:00:0a.0:   bridge window [mem 0xfd500000-0xfd5fffff]
[    0.854682] pci 0000:00:0a.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.854685] pci 0000:00:14.4: PCI bridge to [bus 04-04]
[    0.854688] pci 0000:00:14.4:   bridge window [io  0xb000-0xbfff]
[    0.854692] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.854695] pci 0000:00:14.4:   bridge window [mem 0xfdc00000-0xfdcfffff pref]
[    0.854701] pci 0000:00:15.0: PCI bridge to [bus 05-05]
[    0.854703] pci 0000:00:15.0:   bridge window [io  0xa000-0xafff]
[    0.854707] pci 0000:00:15.0:   bridge window [mem 0xfda00000-0xfdafffff]
[    0.854710] pci 0000:00:15.0:   bridge window [mem 0xfd900000-0xfd9fffff 64bit pref]
[    0.854715] pci 0000:00:15.1: PCI bridge to [bus 06-06]
[    0.854717] pci 0000:00:15.1:   bridge window [io  0x9000-0x9fff]
[    0.854721] pci 0000:00:15.1:   bridge window [mem 0xfd800000-0xfd8fffff]
[    0.854724] pci 0000:00:15.1:   bridge window [mem 0xfd700000-0xfd7fffff 64bit pref]
[    0.854742] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.854745] pci 0000:00:02.0: setting latency timer to 64
[    0.854755] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.854757] pci 0000:00:09.0: setting latency timer to 64
[    0.854761] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.854763] pci 0000:00:0a.0: setting latency timer to 64
[    0.854771] pci 0000:00:15.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.854774] pci 0000:00:15.0: setting latency timer to 64
[    0.854779] pci 0000:00:15.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.854782] pci 0000:00:15.1: setting latency timer to 64
[    0.854785] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.854787] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.854789] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.854790] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.854792] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xfebfffff]
[    0.854794] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.854796] pci_bus 0000:01: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.854797] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.854799] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.854801] pci_bus 0000:02: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    0.854803] pci_bus 0000:02: resource 2 [mem 0xfd600000-0xfd6fffff 64bit pref]
[    0.854805] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    0.854806] pci_bus 0000:03: resource 1 [mem 0xfd500000-0xfd5fffff]
[    0.854808] pci_bus 0000:03: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.854810] pci_bus 0000:04: resource 0 [io  0xb000-0xbfff]
[    0.854811] pci_bus 0000:04: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.854813] pci_bus 0000:04: resource 2 [mem 0xfdc00000-0xfdcfffff pref]
[    0.854815] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.854816] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.854818] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.854820] pci_bus 0000:04: resource 7 [mem 0x000c0000-0x000dffff]
[    0.854821] pci_bus 0000:04: resource 8 [mem 0xd0000000-0xfebfffff]
[    0.854823] pci_bus 0000:05: resource 0 [io  0xa000-0xafff]
[    0.854825] pci_bus 0000:05: resource 1 [mem 0xfda00000-0xfdafffff]
[    0.854826] pci_bus 0000:05: resource 2 [mem 0xfd900000-0xfd9fffff 64bit pref]
[    0.854828] pci_bus 0000:06: resource 0 [io  0x9000-0x9fff]
[    0.854830] pci_bus 0000:06: resource 1 [mem 0xfd800000-0xfd8fffff]
[    0.854832] pci_bus 0000:06: resource 2 [mem 0xfd700000-0xfd7fffff 64bit pref]
[    0.854863] NET: Registered protocol family 2
[    0.855158] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.856626] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.858666] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.858923] TCP: Hash tables configured (established 524288 bind 65536)
[    0.858925] TCP reno registered
[    0.858944] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.859032] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.859198] NET: Registered protocol family 1
[    1.148173] pci 0000:01:00.0: Boot video device
[    1.148216] PCI: CLS 4 bytes, default 64
[    1.149792] PCI-DMA: Disabling AGP.
[    1.149894] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.149895] PCI-DMA: using GART IOMMU.
[    1.149898] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.153171] audit: initializing netlink socket (disabled)
[    1.153180] type=2000 audit(1338247610.148:1): initialized
[    1.191621] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.239044] VFS: Disk quotas dquot_6.5.2
[    1.239089] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.239557] fuse init (API version 7.16)
[    1.239610] msgmni has been set to 24070
[    1.240025] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.240059] io scheduler noop registered
[    1.240061] io scheduler deadline registered
[    1.240087] io scheduler cfq registered (default)
[    1.240200] pcieport 0000:00:02.0: setting latency timer to 64
[    1.240225] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.240332] pcieport 0000:00:09.0: setting latency timer to 64
[    1.240350] pcieport 0000:00:09.0: irq 41 for MSI/MSI-X
[    1.240424] pcieport 0000:00:0a.0: setting latency timer to 64
[    1.240442] pcieport 0000:00:0a.0: irq 42 for MSI/MSI-X
[    1.240672] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.240698] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.240786] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.240791] ACPI: Power Button [PWRB]
[    1.240821] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.240824] ACPI: Power Button [PWRF]
[    1.240840] ACPI: acpi_idle registered with cpuidle
[    1.240857] ACPI: processor limited to max C-state 1
[    1.416656] ERST: Table is not found!
[    1.416700] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.421387] Linux agpgart interface v0.103
[    1.422042] brd: module loaded
[    1.422330] loop: module loaded
[    1.422505] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.422610] pata_acpi 0000:05:00.1: enabling device (0000 -> 0001)
[    1.422615] pata_acpi 0000:05:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.422632] pata_acpi 0000:05:00.1: setting latency timer to 64
[    1.422641] pata_acpi 0000:05:00.1: PCI INT B disabled
[    1.422938] Fixed MDIO Bus: probed
[    1.422953] PPP generic driver version 2.4.2
[    1.422983] tun: Universal TUN/TAP device driver, 1.6
[    1.422985] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.423037] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.423084] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.423118] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.423148] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.423155] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.423169] QUIRK: Enable AMD PLL fix
[    1.423179] ehci_hcd 0000:00:12.2: debug port 1
[    1.423204] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02d000
[    1.432095] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.432178] hub 1-0:1.0: USB hub found
[    1.432181] hub 1-0:1.0: 5 ports detected
[    1.432306] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.432317] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.432347] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.432353] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.432371] ehci_hcd 0000:00:13.2: debug port 1
[    1.432382] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfe02b000
[    1.444096] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.444171] hub 2-0:1.0: USB hub found
[    1.444174] hub 2-0:1.0: 5 ports detected
[    1.444295] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.444306] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    1.444328] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.444336] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.444354] ehci_hcd 0000:00:16.2: debug port 1
[    1.444365] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfe028000
[    1.456097] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.456171] hub 3-0:1.0: USB hub found
[    1.456174] hub 3-0:1.0: 4 ports detected
[    1.456234] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.456310] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.456321] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.456343] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.456369] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfe02e000
[    1.516145] hub 4-0:1.0: USB hub found
[    1.516151] hub 4-0:1.0: 5 ports detected
[    1.516293] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.516304] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.516329] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.516342] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02c000
[    1.576141] hub 5-0:1.0: USB hub found
[    1.576146] hub 5-0:1.0: 5 ports detected
[    1.576291] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.576302] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.576326] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    1.576339] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe02a000
[    1.636147] hub 6-0:1.0: USB hub found
[    1.636152] hub 6-0:1.0: 2 ports detected
[    1.636287] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.636298] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    1.636321] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    1.636334] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfe029000
[    1.696139] hub 7-0:1.0: USB hub found
[    1.696145] hub 7-0:1.0: 4 ports detected
[    1.696214] uhci_hcd: USB Universal Host Controller Interface driver
[    1.696256] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.696258] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.696380] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.696426] mousedev: PS/2 mouse device common for all mice
[    1.696487] rtc_cmos 00:04: RTC can wake from S4
[    1.696554] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.696583] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.696646] device-mapper: uevent: version 1.0.3
[    1.696689] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.696695] cpuidle: using governor ladder
[    1.696696] cpuidle: using governor menu
[    1.696697] EFI Variables Facility v0.08 2004-May-17
[    1.696843] TCP cubic registered
[    1.696915] NET: Registered protocol family 10
[    1.697229] NET: Registered protocol family 17
[    1.697239] Registering the dns_resolver key type
[    1.697299] PM: Hibernation image not present or could not be loaded.
[    1.697306] registered taskstats version 1
[    1.725622]   Magic number: 12:912:454
[    1.725725] rtc_cmos 00:04: setting system clock to 2012-05-28 23:26:52 UTC (1338247612)
[    1.725749] powernow-k8: Found 1 AMD Phenom(tm) II X6 1090T Processor (6 cpu cores) (version 2.20.00)
[    1.725767] powernow-k8: Core Performance Boosting: on.
[    1.725797] powernow-k8:    0 : pstate 0 (3200 MHz)
[    1.725798] powernow-k8:    1 : pstate 1 (2400 MHz)
[    1.725800] powernow-k8:    2 : pstate 2 (1600 MHz)
[    1.725801] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.726199] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.726201] EDD information not available.
[    1.727359] Freeing unused kernel memory: 988k freed
[    1.727535] Write protecting the kernel read-only data: 12288k
[    1.732605] Freeing unused kernel memory: 2032k freed
[    1.736364] Freeing unused kernel memory: 1388k freed
[    1.741687] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.749596] udevd[142]: starting version 173
[    1.763276] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.763303] xhci_hcd 0000:02:00.0: setting latency timer to 64
[    1.763306] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.763379] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
[    1.763508] xhci_hcd 0000:02:00.0: irq 17, io mem 0xfdbfe000
[    1.763517] wmi: Mapper loaded
[    1.763557] xhci_hcd 0000:02:00.0: irq 43 for MSI/MSI-X
[    1.763563] xhci_hcd 0000:02:00.0: irq 44 for MSI/MSI-X
[    1.763566] xhci_hcd 0000:02:00.0: irq 45 for MSI/MSI-X
[    1.763570] xhci_hcd 0000:02:00.0: irq 46 for MSI/MSI-X
[    1.763573] xhci_hcd 0000:02:00.0: irq 47 for MSI/MSI-X
[    1.763577] xhci_hcd 0000:02:00.0: irq 48 for MSI/MSI-X
[    1.763582] xhci_hcd 0000:02:00.0: irq 49 for MSI/MSI-X
[    1.763729] xHCI xhci_add_endpoint called for root hub
[    1.763731] xHCI xhci_check_bandwidth called for root hub
[    1.763751] hub 8-0:1.0: USB hub found
[    1.763757] hub 8-0:1.0: 2 ports detected
[    1.763810] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.763833] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[    1.765940] Floppy drive(s): fd0 is 1.44M
[    1.766992] xHCI xhci_add_endpoint called for root hub
[    1.766994] xHCI xhci_check_bandwidth called for root hub
[    1.767008] hub 9-0:1.0: USB hub found
[    1.767014] hub 9-0:1.0: 2 ports detected
[    1.767054] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.767068] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.767099] r8169 0000:03:00.0: setting latency timer to 64
[    1.767138] r8169 0000:03:00.0: irq 50 for MSI/MSI-X
[    1.767435] r8169 0000:03:00.0: eth0: RTL8168e/8111e at 0xffffc900125c6000, 1c:6f:65:d5:e9:23, XID 0c200000 IRQ 50
[    1.767451] ahci 0000:00:11.0: version 3.0
[    1.767465] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.767568] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    1.767571] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.768172] scsi0 : ahci
[    1.768299] scsi1 : ahci
[    1.768436] scsi2 : ahci
[    1.768503] scsi3 : ahci
[    1.768574] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 19
[    1.768577] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 19
[    1.768580] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 19
[    1.768582] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 19
[    1.768901] ahci 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.774895] scsi4 : pata_atiixp
[    1.775007] scsi5 : pata_atiixp
[    1.775391] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    1.775394] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    1.783796] FDC 0 is a post-1991 82077
[    1.784101] ahci 0000:05:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.784105] ahci 0000:05:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.784111] ahci 0000:05:00.0: setting latency timer to 64
[    1.784371] scsi6 : ahci
[    1.784744] scsi7 : ahci
[    1.784785] ata7: SATA max UDMA/133 abar m8192@0xfdafe000 port 0xfdafe100 irq 17
[    1.784789] ata8: SATA max UDMA/133 abar m8192@0xfdafe000 port 0xfdafe180 irq 17
[    1.784930] pata_jmicron 0000:05:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.784959] pata_jmicron 0000:05:00.1: setting latency timer to 64
[    1.785237] scsi8 : pata_jmicron
[    1.785294] scsi9 : pata_jmicron
[    1.785319] ata9: PATA max UDMA/100 cmd 0xaf00 ctl 0xae00 bmdma 0xab00 irq 17
[    1.785321] ata10: PATA max UDMA/100 cmd 0xad00 ctl 0xac00 bmdma 0xab08 irq 17
[    1.808110] usb 1-3: new high speed USB device number 3 using ehci_hcd
[    1.956669] ata9.01: ATAPI: NU CD-RW/DVD-ROM DBW-521, GX01, max UDMA/33
[    1.959729] usbcore: registered new interface driver uas
[    1.972700] ata9.01: configured for UDMA/33
[    2.068113] usb 1-4: new high speed USB device number 4 using ehci_hcd
[    2.092120] ata1: SATA link down (SStatus 0 SControl 300)
[    2.092155] ata2: SATA link down (SStatus 0 SControl 300)
[    2.096093] ata3: SATA link down (SStatus 0 SControl 300)
[    2.096137] ata4: SATA link down (SStatus 0 SControl 300)
[    2.152086] Refined TSC clocksource calibration: 3214.162 MHz.
[    2.152095] Switching to clocksource tsc
[    2.276098] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.276881] ata7.00: ATA-7: ST3320820AS, 3.AHG, max UDMA/100
[    2.276883] ata7.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.277855] ata7.00: configured for UDMA/100
[    2.277998] scsi 6:0:0:0: Direct-Access     ATA      ST3320820AS      3.AH PQ: 0 ANSI: 5
[    2.278122] sd 6:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.278124] sd 6:0:0:0: Attached scsi generic sg0 type 0
[    2.278202] sd 6:0:0:0: [sda] Write Protect is off
[    2.278204] sd 6:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.278244] sd 6:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.341841]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    2.342154] sd 6:0:0:0: [sda] Attached SCSI disk
[    2.392105] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.395794] ata8.00: ATA-8: WDC WD20EARS-00MVWB0, 50.0AB50, max UDMA/133
[    2.395796] ata8.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.399399] ata8.00: configured for UDMA/133
[    2.399509] scsi 7:0:0:0: Direct-Access     ATA      WDC WD20EARS-00M 50.0 PQ: 0 ANSI: 5
[    2.399618] sd 7:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.399621] sd 7:0:0:0: Attached scsi generic sg1 type 0
[    2.399714] sd 7:0:0:0: [sdb] Write Protect is off
[    2.399715] sd 7:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.399748] sd 7:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.400243] scsi 8:0:1:0: CD-ROM            NU       CDRW/DVD DBW-521 GX01 PQ: 0 ANSI: 5
[    2.401722] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[    2.401724] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.401814] sr 8:0:1:0: Attached scsi CD-ROM sr0
[    2.401963] sr 8:0:1:0: Attached scsi generic sg2 type 5
[    2.468093] usb 4-1: new low speed USB device number 2 using ohci_hcd
[    2.494429]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 sdb8 sdb9 >
[    2.494785] sd 7:0:0:0: [sdb] Attached SCSI disk
[    2.568379] Initializing USB Mass Storage driver...
[    2.568904] scsi10 : usb-storage 1-3:1.0
[    2.569222] usbcore: registered new interface driver usb-storage
[    2.569224] USB Mass Storage support registered.
[    2.649246] input: HID 1241:1166 as /devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.0/input/input3
[    2.649311] generic-usb 0003:1241:1166.0001: input,hidraw0: USB HID v1.10 Mouse [HID 1241:1166] on usb-0000:00:12.0-1/input0
[    2.649322] usbcore: registered new interface driver usbhid
[    2.649324] usbhid: USB HID core driver
[    2.821787] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    2.821790] vesafb: scrolling: redraw
[    2.821792] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    2.825301] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90012600000, using 3072k, total 3072k
[    2.825424] Console: switching to colour frame buffer device 128x48
[    2.825438] fb0: VESA VGA frame buffer device
[    3.569086] scsi 10:0:0:0: Direct-Access     Android    UMS Composite    00 PQ: 0 ANSI: 2
[    3.569706] scsi 10:0:0:1: Direct-Access     Android    UMS Composite    00 PQ: 0 ANSI: 2
[    3.744286] sd 10:0:0:0: Attached scsi generic sg3 type 0
[    3.744381] sd 10:0:0:1: Attached scsi generic sg4 type 0
[    3.748670] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[    3.754295] sd 10:0:0:1: [sdd] Attached SCSI removable disk
[    4.600221] Btrfs loaded
[    4.603797] xor: automatically using best checksumming function: generic_sse
[    4.620002]    generic_sse: 13180.000 MB/sec
[    4.620006] xor: using function: generic_sse (13180.000 MB/sec)
[    4.620371] device-mapper: dm-raid45: initialized v0.2594b
[   22.028570] end_request: I/O error, dev fd0, sector 0
[   22.080894] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[  134.171588] ata8.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  134.171592] ata8.00: irq_stat 0x48000000
[  134.171594] ata8.00: failed command: READ FPDMA QUEUED
[  134.171599] ata8.00: cmd 60/00:00:d0:30:00/01:00:cb:00:00/40 tag 0 ncq 131072 in
[  134.171599]          res 41/40:00:30:31:00/00:00:cb:00:00/40 Emask 0x409 (media error) <F>
[  134.171601] ata8.00: status: { DRDY ERR }
[  134.171603] ata8.00: error: { UNC }
[  134.179436] ata8.00: configured for UDMA/133
[  134.179445] ata8: EH complete
[  146.346757] udevd[484]: starting version 173
[  146.374923] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[  146.374927] Disabling lock debugging due to kernel taint
[  146.377635] lp: driver loaded but no devices found
[  146.391359] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [io 0xb00-0xb0f]
[  146.391362] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[  146.397831] cfg80211: Calling CRDA to update world regulatory domain
[  146.408816] ath5k 0000:04:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[  146.408868] ath5k 0000:04:06.0: registered as 'phy0'
[  146.411378] MCE: In-kernel MCE decoding enabled.
[  146.412090] EDAC MC: Ver: 2.1.0
[  146.414782] AMD64 EDAC driver v3.4.0
[  146.420364] type=1400 audit(1338262157.193:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=545 comm="apparmor_parser"
[  146.420693] type=1400 audit(1338262157.193:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=545 comm="apparmor_parser"
[  146.420901] type=1400 audit(1338262157.193:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=545 comm="apparmor_parser"
[  146.422740] type=1400 audit(1338262157.193:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=653 comm="apparmor_parser"
[  146.426091] [fglrx] Maximum main memory to use for locked dma buffers: 11735 MBytes.
[  146.426190] [fglrx]   vendor: 1002 device: 6758 count: 1
[  146.426567] [fglrx] ioport: bar 4, base 0xee00, size: 0x100
[  146.426585] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  146.426590] pci 0000:01:00.0: setting latency timer to 64
[  146.426770] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  146.426884] [fglrx] Kernel PAT support is enabled
[  146.426900] [fglrx] module loaded - fglrx 8.88.7 [Jul 28 2011] with 1 minors
[  146.477998] cfg80211: World regulatory domain updated:
[  146.478000] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  146.478003] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  146.478005] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  146.478006] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  146.478008] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  146.478009] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  146.505864] Adding 4882428k swap on /dev/sda5.  Priority:-1 extents:1 across:4882428k 
[  146.934848] EDAC amd64: DRAM ECC disabled.
[  146.934884] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[  146.934885]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[  146.934886]  (Note that use of the override may cause unknown side effects.)
[  146.983910] ath: EEPROM regdomain: 0x60
[  146.983912] ath: EEPROM indicates we should expect a direct regpair map
[  146.983914] ath: Country alpha2 being used: 00
[  146.983916] ath: Regpair used: 0x60
[  146.983939] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  146.984059] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  146.984061] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  146.984063] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  146.984064] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  146.984066] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  146.984068] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  146.984069] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  146.984071] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  146.984073] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  146.984075] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  146.984076] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  146.984078] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  146.984080] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  146.984082] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  146.984083] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  146.984085] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  146.984086] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  146.984088] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  146.984090] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  146.984092] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  146.984093] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  146.984095] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  146.984096] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  146.984098] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  146.984100] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  146.984102] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  146.984103] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  146.984105] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  146.984131] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  146.985850] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[  146.986215] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[  147.034356] hda_codec: ALC889: BIOS auto-probing.
[  147.046783] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input4
[  147.046986] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  147.047059] HDA Intel 0000:01:00.1: irq 51 for MSI/MSI-X
[  147.047081] HDA Intel 0000:01:00.1: setting latency timer to 64
[  147.066759] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[  147.066858] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input5
[  147.069139] usbcore: registered new interface driver ndiswrapper
[  148.164136] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[  148.272523] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[  150.411948] type=1400 audit(1338262161.181:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1108 comm="apparmor_parser"
[  150.411993] type=1400 audit(1338262161.181:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1104 comm="apparmor_parser"
[  150.412299] type=1400 audit(1338262161.185:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1108 comm="apparmor_parser"
[  150.413542] type=1400 audit(1338262161.185:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=1110 comm="apparmor_parser"
[  150.413944] type=1400 audit(1338262161.185:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1109 comm="apparmor_parser"
[  150.414047] type=1400 audit(1338262161.185:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1105 comm="apparmor_parser"
[  150.604082] init: failsafe main process (1037) killed by TERM signal
[  150.604618] init: apport pre-start process (1180) terminated with status 1
[  150.611798] init: apport post-stop process (1213) terminated with status 1
[  150.613205] init: lxdm main process (1191) killed by TERM signal
[  150.614229] init: gdm main process (1218) killed by TERM signal
[  150.715690] r8169 0000:03:00.0: eth0: link down
[  150.717221] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  150.728462] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  150.814578] Bluetooth: Core ver 2.16
[  150.814601] NET: Registered protocol family 31
[  150.814602] Bluetooth: HCI device and connection manager initialized
[  150.814605] Bluetooth: HCI socket layer initialized
[  150.814606] Bluetooth: L2CAP socket layer initialized
[  150.814662] Bluetooth: SCO socket layer initialized
[  150.816165] Bluetooth: RFCOMM TTY layer initialized
[  150.816169] Bluetooth: RFCOMM socket layer initialized
[  150.816170] Bluetooth: RFCOMM ver 1.11
[  150.816442] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  150.816444] Bluetooth: BNEP filters: protocol multicast
[  150.957916] fglrx_pci 0000:01:00.0: irq 52 for MSI/MSI-X
[  150.958352] [fglrx] Firegl kernel thread PID: 1769
[  150.958404] [fglrx] Firegl kernel thread PID: 1770
[  150.958460] [fglrx] Firegl kernel thread PID: 1771
[  150.958895] [fglrx] IRQ 52 Enabled
[  151.333535] [fglrx] Gart USWC size:1280 M.
[  151.333538] [fglrx] Gart cacheable size:508 M.
[  151.333542] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[  151.333544] [fglrx] Reserved FB block: Unshared offset:f8fd000, size:403000 
[  151.333545] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[  151.562962] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
[  151.618938] EXT4-fs (sda6): re-mounted. Opts: commit=0
[  151.625352] HDMI hot plug event: Pin=3 Presence_Detect=1 ELD_Valid=0
[  151.625368] HDMI status: Pin=3 Presence_Detect=1 ELD_Valid=1
[  151.626747] HDMI hot plug event: Pin=3 Presence_Detect=0 ELD_Valid=1
[  151.626759] HDMI status: Pin=3 Presence_Detect=1 ELD_Valid=1
[  151.829774] init: plymouth-stop pre-start process (1850) terminated with status 1
[  153.751650] wlan0: authenticate with 00:1d:d0:68:28:b0 (try 1)
[  153.753105] wlan0: authenticated
[  153.753217] wlan0: associate with 00:1d:d0:68:28:b0 (try 1)
[  153.755676] wlan0: RX AssocResp from 00:1d:d0:68:28:b0 (capab=0xc11 status=0 aid=4)
[  153.755678] wlan0: associated
[  153.757484] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  153.757561] cfg80211: Calling CRDA for country: US
[  153.759913] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  153.759916] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  153.759918] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  153.759919] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  153.759921] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  153.759922] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  153.759924] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  153.759925] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  153.759927] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  153.759928] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  153.759930] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  153.759931] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  153.759933] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  153.759934] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  153.759936] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  153.759937] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  153.759939] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  153.759940] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  153.759942] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  153.759943] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  153.759945] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  153.759946] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  153.759947] cfg80211: Disabling freq 2467 MHz
[  153.759949] cfg80211: Disabling freq 2472 MHz
[  153.759949] cfg80211: Disabling freq 2484 MHz
[  153.759953] cfg80211: Regulatory domain changed to country: US
[  153.759954] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  153.759956] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  153.759957] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  153.759959] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  153.759961] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  153.759962] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  153.759964] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  155.014595] wlan0: IPv6 duplicate address fe80::211:50ff:fe6f:d4da detected!
[  155.451507] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
[  155.631549] EXT4-fs (sda6): re-mounted. Opts: commit=0
[  178.918061] cdrom: sr0: mrw address space DMA selected
[  178.939868] ISO 9660 Extensions: Microsoft Joliet Level 3
[  180.039435] ISO 9660 Extensions: RRIP_1991A
[  192.523789] ppdev: user-space parallel port driver
[  192.529147] audit_printk_skb: 24 callbacks suppressed
[  192.529150] type=1400 audit(1338262203.300:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=2420 comm="apparmor_parser"
[  192.529528] type=1400 audit(1338262203.300:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=2420 comm="apparmor_parser"
```

And a dmesg for good measure.  It gets interesting around the 2 minute mark where some errors crop up.  Can't believe I haven't noticed those before, I guess I was looking before the gap in time rather than after it?  Or maybe I was using the other drive last time?  In any case, I'll spend some time trying to decode that, and maybe see if it happens on the other drive.  Ubuntu's disk utility claims that I have 1379 bad sectors, which seems a bit high to me, but I've owned this drive for over a year now and the drive is reporting 277.4 powered on days... so maybe it's natural, I'm not familliar enough with hard disks (especially ones this size) to really have a good idea of when to worry.  Should I try to find a copy of spinrite?

Reallocated sectors are in red with a warning at 95
So pending sectors are in red with a warning at 1284
Spinup time is only 5.6 seconds.

---

### Post by Alaric on 2012-05-29
Also interesting:  It looks like the Oneric kernel doesn't support large blocks.  Maybe I just need to update the kernel?  

[http://www.unixmen.com/how-to-upgrade-to-kernel-3-2-in-ubuntu11-10-and-linuxmint12/](http://www.unixmen.com/how-to-upgrade-to-kernel-3-2-in-ubuntu11-10-and-linuxmint12/)

I'm attempting to update to 3.4 at the moment.

---

### Post by ahallubuntu on 2012-05-29
> **Alaric said:**
> Reallocated sectors are in red with a warning at 95
So pending sectors are in red with a warning at 1284

Well, you can stop right there.  1284 pending sectors is catastrophic.  The drive surface is probably failing.  Get any data you care about off the drive ASAP if you still can.  Then, if the drive  is an internal drive, try to RMA it under warranty; if it's the one you pulled out of an external case, I guess you are probably out of luck with the warranty.

You could try zeroing out the drive (I like DBAN - [www.dban.org](www.dban.org) ) but you've got 95 reallocated sectors already and that's bad too (not catastrophic yet - it means 95 bad sectors were already replaced but eventually you'll run out of spares to replace them with).

You mention a "wimpy" power supply.  I foolishly had a crap power supply in this same Ubuntu server that has my green drives in it, and when this power supply finally started failing a few months ago, it corrupted one of the green drives.  I probably could have kept it and would have been fine after writing zeros (all pending sectors went away) but it was under warranty so I just RMA'ed it for a new drive.  I now look for good quality power supplies on sale - often can be had for under $30 USD after rebate - and won't be using any more junky power supplies in computers I care about.

---

### Post by ahallubuntu on 2012-05-29
On second thought, what are the RAW values for pending sector count and reallocated sector count?  Maybe you didn't read those off.  Those are what matter.  If you really only have a few pending sectors it might not be that bad, but you need to clear them if you want to use the drive effectively, by zeroing the drive (hope they either go away or get reallocated).  If you can't get rid of all the pending sectors, you need to replace the drive.

---

### Post by Alaric on 2012-05-29
Hmm, glad I've found someone so familiar with HDD stats :)   

Ubuntu claims 197 normalized, 196 worst, threshold: 0, value: 1284.  I'm not sure which of those would be raw.  

At the top, it claims 1379 bad sectors, I remember knowing the difference between raw and reported at some point, but can't for the life of me recall it now.  Do these numbers help you discern, or should I use a program you might be more familiar with?

---

### Post by ahallubuntu on 2012-05-29
> **Alaric said:**
> Hmm, glad I've found someone so familiar with HDD stats :)   

Ubuntu claims 197 normalized, 196 worst, threshold: 0, value: 1284.  I'm not sure which of those would be raw.  

At the top, it claims 1379 bad sectors, I remember knowing the difference between raw and reported at some point, but can't for the life of me recall it now.  Do these numbers help you discern, or should I use a program you might be more familiar with?

OK, I think that last column ("value") is "RAW" so if it's 1284, then that's really bad - so yeah, I think you're done. :-(  Backup any data you cared about if you can, try DBANing the drive to clear the bad sectors...but I would expect you probably won't have any luck with so many failed sectors.  If the drive isn't under warranty, you now have a paperweight.  Bummer.

---

### Post by Alaric on 2012-05-29
Bah, I was holding out hope that it would be something fixable because of the the fact that two drives were exhibiting the same behavior.  Maybe that means I have two paper weights :(  Damn Ubunutu's liberal use of soothing green hues!  One of them doesn't really matter, and it's in the process of zero-ing now (another 5 hours or so to go).  I'll have to get on ordering a new drive I guess. 

Thanks for your help, I never would have caught the few red marks within the sea of green in Ubuntu's disk utility.

---

### Post by ahallubuntu on 2012-05-29
S.M.A.R.T. has been a lifesaver for me.  It has helped me catch corruptions very early and avoid any catastrophes.  Google published a study a few years ago claiming S.M.A.R.T. isn't a great predictor of imminent hard drive failure, but it sure seems to improve your odds of catching a problem early.  I check it religiously on my hard drives.

I hope your other green drive is OK and boots up at proper speed!

---

### Post by MadmanRB on 2012-05-29
> **ahallubuntu said:**
> Oh, and I wouldn't recommend trying to install an OS on a Green drive myself - you can but even if you fix whatever performance conflict you now seem to have, at 5900 RPM you're not going to get good performance.

I have two green drives and never had one issue with them, one has both win7 and Ubuntu on it and it works just fine

---

### Post by ahallubuntu on 2012-05-29
> **MadmanRB said:**
> I have two green drives and never had one issue with them, one has both win7 and Ubuntu on it and it works just fine

Right, I have five WD green drives and only one of them has had any problems - and that was probably caused by my crappy power supply.  Otherwise, all of them have worked beautifully for me in Ubuntu.

But I don't use them for OS drives, and I don't recommend a green drive for an OS drive just because of the reduced performance vs. a  7200RPM drive.  But you can certainly use a green drive for an OS.  The most important thing is to make sure the partitions are aligned properly - should be automatic starting with Ubuntu 11.04 I think.

---

