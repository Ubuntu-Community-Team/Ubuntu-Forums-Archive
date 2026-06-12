---
title: "[urgent] CPU failing or just scaling problem?"
date: 2011-08-12
forum: Hardware
---

### Post by chimericidol on 2011-08-12
Hi guys,

I wrote urgent because I use this laptop for work :/ ...

I am using Ubuntu 1.04 with Unity2d on Dell Inspiron Laptop 1720. I have this notebook already for 3 years and it worked like charm whit Ubuntu until now. Since yesterday I have noticed that my system started to get pretty slow for some reason. I din't know what it was so I had shut down the machine. After a while when I switched it on again, it was the same. I had also noticed that the CPU was going to 100% practically for any reason like playing video or using browser etc. (it was not like this before, it would not go as high, at least not all the time).

Then I have realized that the problem is the scaling of CPU. I am using indicator-cpufreq for Unity and it was showing it being full (if u have the icon you know what I mean) but the scaling options would show that "ondemand" its only 0.8Ghz where my processor is 2.2GHz. There was no way I could change it for anything else, so changing to "performance" or specifically for 2.2GHz did nothing. Just to check I have used also the indicators in Ubuntu Classic desktop, it was the same, showing 800MHz.

In order to make sure that this is not just the fault of the indicators I used cpufreq-info and this is what I got:

```
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.20 GHz
  available frequency steps: 2.20 GHz, 2.20 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  **current policy: frequency should be within 800 MHz and 800 MHz.**
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  **cpufreq stats: 2.20 GHz:0.00%, 2.20 GHz:0.00%, 1.60 GHz:0.00%, 1.20 GHz:0.00%, 800 MHz:100.00%  (1)**
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.20 GHz
  available frequency steps: 2.20 GHz, 2.20 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  **current policy: frequency should be within 800 MHz and 800 MHz.**
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  **cpufreq stats: 2.20 GHz:0.00%, 2.20 GHz:0.00%, 1.60 GHz:0.00%, 1.20 GHz:0.00%, 800 MHz:100.00%  (1)**

```

So there it clearly says that the range in which it can scale the CPU is between 800MHz and 800Mhz (!) and therefore it never goes higher:

```
cpufreq stats: 2.20 GHz:0.00%, 2.20 GHz:0.00%, 1.60 GHz:0.00%, 1.20 GHz:0.00%, 800 MHz:100.00%
```

Now I have made some research and based on some suggestions I have modified:

```
/etc/init.d/cpufrequtils
```

from: 

```
ENABLE="true"
GOVERNOR="ondemand"
MAX_SPEED="0"
MIN_SPEED="0"
```

to:

```
ENABLE="true"
GOVERNOR="ondemand"
MAX_SPEED=800000
MIN_SPEED=2200000
```

Unfortunately it did not give any reasult since cpufreq-info gives exactly the same output as before.

I would like to add that I have used Windows 7 on the same machine and it seems to have similar problem. It is slow and CPU is working always on 100%. This led me to a conclusion that it might be a CPU hardware issue (hope not :( )

Please help me guys since I need this machine for work! If you think it might be the hardware failure let me know how I can confirm that. Thanks!!

---

### Post by .... on 2011-08-12
Use htop and find out what's eating your CPU. It might also be helpful to monitor the CPU temp because the CPU could be throttling down to avoid overheating (IIRC, some systems do that to protect the CPU before they outright shut off).

---

### Post by chimericidol on 2011-08-12
Thanks for fast reply!

Top is not showing anything using too much the CPU but the system keeps being slow. It actually feels like it would be running on 800Mhz CPU even if the system is no using 100% of it.

I am using gkrellm with gkrellm-i8k in order to control the temperature and fan speed. Normally the temperature would be between 40C and 80C max where apparently the critical is 100C for my CPU. Anyway, which is strange, now it never goes higher then 45C. Which on the other hand make sense if its running only at 800MHz.

Anyway, I get this behavior just after I start the machine even if it is being totally cold after night of rest.

---

### Post by prshah on 2011-08-12
Have you made any changes to BIOS settings? Some laptops allow for a "performance" setting, which will lock the CPU to max or min (to save battery time).

Unfortunately the exact option varies from board to board, and there is nothing specific I can mention. The most common wordings will be "Battery Saver" or "Processor Power Saving" or "Performance mode" or "Intel SpeedStep", EIST, PowerNow (AMD only) etc.

If you have not made any changes to the BIOS recently, then this is probably not your problem.

---

### Post by .... on 2011-08-12
Then I suspect a kernel update caused the issue and you should try booting into your previous kernel. Also, looking through dmesg output might be helpful.

---

### Post by chimericidol on 2011-08-12
The only thing I have changed to my BIOS (already months ago) was the HD set to Performance. I never touched the CPU settings, though. Is there a way of forcing CPU to work in performance mode from BIOS?

I am not sure if its the kernel since after what happend (i forgot to mention it) I have reinstalled the Ubuntu. The clean install was behaving the same. It's true that I have updated eveyrthing now, which includes kernel. I will try to change to the original kernel from the installation just to double check that this is not the issue. Anyway, as I said, I am having similar experience in Windows 7 (dual boot).

Thanks for reply's!

Btw this is the, rather huge, output of dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-10-generic (buildd@yellow) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 (Ubuntu 2.6.38-10.46-generic 2.6.38.7)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=a84a2480-d762-4d53-af20-be3cf895892c ro quiet splash vt.handoff=7
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfe6d800 (usable)
[    0.000000]  BIOS-e820: 00000000dfe6d800 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100002000 - 0000000120000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Dell Inc. Inspiron 1720                   /0UK437, BIOS A09 07/11/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FE0000000 write-back
[    0.000000]   3 base 100000000 mask F00000000 write-back
[    0.000000]   4 base 0DFF00000 mask FFFF00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000dff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdfe6d max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000dfe6d000
[    0.000000]  0000000000 - 00dfe00000 page 2M
[    0.000000]  00dfe00000 - 00dfe6d000 page 4k
[    0.000000] kernel direct mapping tables up to dfe6d000 @ 1fffa000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
[    0.000000]  0100000000 - 0120000000 page 2M
[    0.000000] kernel direct mapping tables up to 120000000 @ dfe67000-dfe6d000
[    0.000000] RAMDISK: 366cc000 - 3735e000
[    0.000000] ACPI: RSDP 00000000000fbbf0 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000dfe6f200 0005C (v01 DELL    M08     27D8070B ASL  00000061)
[    0.000000] ACPI: FACP 00000000dfe6f09c 000F4 (v04 DELL    M08     27D8070B ASL  00000061)
[    0.000000] ACPI: DSDT 00000000dfe6f800 05658 (v02 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS 00000000dfe7e000 00040
[    0.000000] ACPI: HPET 00000000dfe6f300 00038 (v01 DELL    M08     00000001 ASL  00000061)
[    0.000000] ACPI: APIC 00000000dfe6f400 00068 (v01 DELL    M08     27D8070B ASL  00000047)
[    0.000000] ACPI: MCFG 00000000dfe6f3c0 0003E (v16 DELL    M08     27D8070B ASL  00000061)
[    0.000000] ACPI: SLIC 00000000dfe6f49c 00176 (v01 DELL    M08     27D8070B ASL  00000061)
[    0.000000] ACPI: BOOT 00000000dfe6efc0 00028 (v01 DELL    M08     27D8070B ASL  00000061)
[    0.000000] ACPI: SSDT 00000000dfe6d9bc 004CC (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000120000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000120000000
[    0.000000]   NODE_DATA [000000011fffb000 - 000000011fffffff]
[    0.000000]  [ffffea0000000000-ffffea0003ffffff] PMD -> [ffff88011be00000-ffff88011f7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000dfe6d
[    0.000000]     0: 0x00100002 -> 0x00120000
[    0.000000] On node 0 totalpages: 1048058
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3921 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 898725 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129278 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
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
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000dfe6d000 - 00000000dfe6e000
[    0.000000] PM: Registered nosave memory: 00000000dfe6e000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f4000000
[    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000feda0000
[    0.000000] PM: Registered nosave memory: 00000000feda0000 - 00000000feda6000
[    0.000000] PM: Registered nosave memory: 00000000feda6000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee10000
[    0.000000] PM: Registered nosave memory: 00000000fee10000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] PM: Registered nosave memory: 0000000100000000 - 0000000100002000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:14000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800dfc00000 s84416 r8192 d22080 u1048576
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031924
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=a84a2480-d762-4d53-af20-be3cf895892c ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 4040252k/4718592k available (5941k kernel code, 526360k absent, 151980k reserved, 5016k data, 956k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2193.857 MHz processor.
[    0.010007] Calibrating delay loop (skipped), value calculated using timer frequency.. 4387.71 BogoMIPS (lpj=21938570)
[    0.010017] pid_max: default: 32768 minimum: 301
[    0.010082] Security Framework initialized
[    0.010122] AppArmor: AppArmor initialized
[    0.010125] Yama: becoming mindful.
[    0.011234] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.020953] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.022835] Mount-cache hash table entries: 256
[    0.023171] Initializing cgroup subsys ns
[    0.023182] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.023190] Initializing cgroup subsys cpuacct
[    0.023199] Initializing cgroup subsys memory
[    0.023219] Initializing cgroup subsys devices
[    0.023226] Initializing cgroup subsys freezer
[    0.023231] Initializing cgroup subsys net_cls
[    0.023237] Initializing cgroup subsys blkio
[    0.023322] CPU: Physical Processor ID: 0
[    0.023327] CPU: Processor Core ID: 0
[    0.023333] mce: CPU supports 6 MCE banks
[    0.023352] CPU0: Thermal monitoring enabled (TM2)
[    0.023361] using mwait in idle threads.
[    0.030061] ACPI: Core revision 20110112
[    0.039221] ftrace: allocating 24323 entries in 96 pages
[    0.050112] Setting APIC routing to flat
[    0.050620] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.155824] CPU0: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0b
[    0.160000] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.160000] PEBS disabled due to CPU errata.
[    0.160000] ... version:                2
[    0.160000] ... bit width:              40
[    0.160000] ... generic registers:      2
[    0.160000] ... value mask:             000000ffffffffff
[    0.160000] ... max period:             000000007fffffff
[    0.160000] ... fixed-purpose events:   3
[    0.160000] ... event mask:             0000000700000003
[    0.160000] Booting Node   0, Processors  #1 Ok.
[    0.320038] Brought up 2 CPUs
[    0.320046] Total of 2 processors activated (8777.08 BogoMIPS).
[    0.322334] devtmpfs: initialized
[    0.322334] print_constraints: dummy: 
[    0.322334] Time: 11:45:39  Date: 08/12/11
[    0.322406] NET: Registered protocol family 16
[    0.322464] Trying to unpack rootfs image as initramfs...
[    0.322699] ACPI: bus type pci registered
[    0.322867] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf4000000-0xf7ffffff] (base 0xf4000000)
[    0.322875] PCI: MMCONFIG at [mem 0xf4000000-0xf7ffffff] reserved in E820
[    0.347803] PCI: Using configuration type 1 for base access
[    0.347821] dmi type 0xB1 record - unknown flag
[    0.360538] bio: create slab <bio-0> at 0
[    0.363333] ACPI: EC: Look up EC in DSDT
[    0.377658] ACPI: SSDT 00000000dfe6e4f2 00286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.378385] ACPI: Dynamic OEM Table Load:
[    0.378394] ACPI: SSDT           (null) 00286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.378744] ACPI: SSDT 00000000dfe6de88 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.379429] ACPI: Dynamic OEM Table Load:
[    0.379437] ACPI: SSDT           (null) 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.380050] ACPI: SSDT 00000000dfe6e778 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.380760] ACPI: Dynamic OEM Table Load:
[    0.380768] ACPI: SSDT           (null) 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.381009] ACPI: SSDT 00000000dfe6e46d 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.381698] ACPI: Dynamic OEM Table Load:
[    0.381706] ACPI: SSDT           (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.382181] ACPI: Interpreter enabled
[    0.382188] ACPI: (supports S0 S3 S4 S5)
[    0.382231] ACPI: Using IOAPIC for interrupt routing
[    0.570465] ACPI: No dock devices found.
[    0.570476] HEST: Table not found.
[    0.570485] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.588987] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.626497] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.626506] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.626513] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.626520] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.626526] pci_root PNP0A03:00: host bridge window [mem 0xe0000000-0xf3ffffff]
[    0.626533] pci_root PNP0A03:00: host bridge window [mem 0xf8000000-0xfebfffff]
[    0.626539] pci_root PNP0A03:00: host bridge window [mem 0xfec10000-0xfecfffff]
[    0.626546] pci_root PNP0A03:00: host bridge window [mem 0xfed1c000-0xfed1ffff]
[    0.626552] pci_root PNP0A03:00: host bridge window [mem 0xfed90000-0xfed9ffff]
[    0.626558] pci_root PNP0A03:00: host bridge window [mem 0xfeda7000-0xfedfffff]
[    0.626565] pci_root PNP0A03:00: host bridge window [mem 0xfee10000-0xff9fffff]
[    0.626571] pci_root PNP0A03:00: host bridge window [mem 0xffb00000-0xffefffff]
[    0.626578] pci_root PNP0A03:00: host bridge window [mem 0x120000000-0x317ffffff]
[    0.626619] pci 0000:00:00.0: [8086:2a00] type 0 class 0x000600
[    0.626721] pci 0000:00:01.0: [8086:2a01] type 1 class 0x000604
[    0.626799] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.626809] pci 0000:00:01.0: PME# disabled
[    0.626907] pci 0000:00:1a.0: [8086:2834] type 0 class 0x000c03
[    0.627005] pci 0000:00:1a.0: reg 20: [io  0x6f20-0x6f3f]
[    0.627080] pci 0000:00:1a.1: [8086:2835] type 0 class 0x000c03
[    0.627177] pci 0000:00:1a.1: reg 20: [io  0x6f00-0x6f1f]
[    0.627287] pci 0000:00:1a.7: [8086:283a] type 0 class 0x000c03
[    0.627331] pci 0000:00:1a.7: reg 10: [mem 0xfed1c400-0xfed1c7ff]
[    0.627486] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.627496] pci 0000:00:1a.7: PME# disabled
[    0.627551] pci 0000:00:1b.0: [8086:284b] type 0 class 0x000403
[    0.627592] pci 0000:00:1b.0: reg 10: [mem 0xfebfc000-0xfebfffff 64bit]
[    0.627739] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.627748] pci 0000:00:1b.0: PME# disabled
[    0.627802] pci 0000:00:1c.0: [8086:283f] type 1 class 0x000604
[    0.627951] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.627962] pci 0000:00:1c.0: PME# disabled
[    0.628019] pci 0000:00:1c.1: [8086:2841] type 1 class 0x000604
[    0.628169] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.628180] pci 0000:00:1c.1: PME# disabled
[    0.628239] pci 0000:00:1c.3: [8086:2845] type 1 class 0x000604
[    0.628390] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.628399] pci 0000:00:1c.3: PME# disabled
[    0.628461] pci 0000:00:1d.0: [8086:2830] type 0 class 0x000c03
[    0.628559] pci 0000:00:1d.0: reg 20: [io  0x6f80-0x6f9f]
[    0.628634] pci 0000:00:1d.1: [8086:2831] type 0 class 0x000c03
[    0.628732] pci 0000:00:1d.1: reg 20: [io  0x6f60-0x6f7f]
[    0.628807] pci 0000:00:1d.2: [8086:2832] type 0 class 0x000c03
[    0.628906] pci 0000:00:1d.2: reg 20: [io  0x6f40-0x6f5f]
[    0.629009] pci 0000:00:1d.7: [8086:2836] type 0 class 0x000c03
[    0.629053] pci 0000:00:1d.7: reg 10: [mem 0xfed1c000-0xfed1c3ff]
[    0.629207] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.629217] pci 0000:00:1d.7: PME# disabled
[    0.629264] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.629416] pci 0000:00:1f.0: [8086:2815] type 0 class 0x000601
[    0.629607] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.629620] pci 0000:00:1f.0: quirk: [io  0x1080-0x10bf] claimed by ICH6 GPIO
[    0.629629] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
[    0.629643] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.629720] pci 0000:00:1f.1: [8086:2850] type 0 class 0x000101
[    0.629750] pci 0000:00:1f.1: reg 10: [io  0x01f0-0x01f7]
[    0.629775] pci 0000:00:1f.1: reg 14: [io  0x03f4-0x03f7]
[    0.629797] pci 0000:00:1f.1: reg 18: [io  0x0170-0x0177]
[    0.629819] pci 0000:00:1f.1: reg 1c: [io  0x0374-0x0377]
[    0.629842] pci 0000:00:1f.1: reg 20: [io  0x6fa0-0x6faf]
[    0.629935] pci 0000:00:1f.2: [8086:2829] type 0 class 0x000106
[    0.629983] pci 0000:00:1f.2: reg 10: [io  0x6eb0-0x6eb7]
[    0.630025] pci 0000:00:1f.2: reg 14: [io  0x6eb8-0x6ebb]
[    0.630048] pci 0000:00:1f.2: reg 18: [io  0x6ec0-0x6ec7]
[    0.630070] pci 0000:00:1f.2: reg 1c: [io  0x6ec8-0x6ecb]
[    0.630095] pci 0000:00:1f.2: reg 20: [io  0x6ee0-0x6eff]
[    0.630117] pci 0000:00:1f.2: reg 24: [mem 0xfebfb800-0xfebfbfff]
[    0.630203] pci 0000:00:1f.2: PME# supported from D3hot
[    0.630212] pci 0000:00:1f.2: PME# disabled
[    0.630254] pci 0000:00:1f.3: [8086:283e] type 0 class 0x000c05
[    0.630287] pci 0000:00:1f.3: reg 10: [mem 0xfebfb700-0xfebfb7ff]
[    0.630361] pci 0000:00:1f.3: reg 20: [io  0x10c0-0x10df]
[    0.630530] pci 0000:01:00.0: [10de:0407] type 0 class 0x000300
[    0.630564] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.630600] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.630637] pci 0000:01:00.0: reg 1c: [mem 0xfa000000-0xfbffffff 64bit]
[    0.630664] pci 0000:01:00.0: reg 24: [io  0xef00-0xef7f]
[    0.630688] pci 0000:01:00.0: reg 30: [mem 0xfea00000-0xfea1ffff pref]
[    0.650040] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.650052] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.650060] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfeafffff]
[    0.650072] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.650185] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.650195] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.650208] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.650224] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.650458] pci 0000:0c:00.0: [8086:4222] type 0 class 0x000280
[    0.650543] pci 0000:0c:00.0: reg 10: [mem 0xf9fff000-0xf9ffffff]
[    0.651036] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
[    0.651057] pci 0000:0c:00.0: PME# disabled
[    0.651159] pci 0000:0c:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.651204] pci 0000:00:1c.1: PCI bridge to [bus 0c-0c]
[    0.651214] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.651226] pci 0000:00:1c.1:   bridge window [mem 0xf9f00000-0xf9ffffff]
[    0.651242] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.651351] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.651360] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.651372] pci 0000:00:1c.3:   bridge window [mem 0xf9c00000-0xf9efffff]
[    0.651387] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.651478] pci 0000:03:00.0: [14e4:170c] type 0 class 0x000200
[    0.651516] pci 0000:03:00.0: reg 10: [mem 0xf9bfe000-0xf9bfffff]
[    0.651661] pci 0000:03:00.0: supports D1 D2
[    0.651667] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.651677] pci 0000:03:00.0: PME# disabled
[    0.651718] pci 0000:03:01.0: [1180:0832] type 0 class 0x000c00
[    0.651747] pci 0000:03:01.0: proprietary Ricoh MMC controller disabled (via firewire function)
[    0.651753] pci 0000:03:01.0: MMC cards are now supported by standard SDHCI controller
[    0.651782] pci 0000:03:01.0: reg 10: [mem 0xf9bfd800-0xf9bfdfff]
[    0.651931] pci 0000:03:01.0: supports D1 D2
[    0.651937] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.651947] pci 0000:03:01.0: PME# disabled
[    0.651989] pci 0000:03:01.1: [1180:0822] type 0 class 0x000805
[    0.652028] pci 0000:03:01.1: reg 10: [mem 0xf9bfd400-0xf9bfd4ff]
[    0.652179] pci 0000:03:01.1: supports D1 D2
[    0.652184] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.652196] pci 0000:03:01.1: PME# disabled
[    0.652236] pci 0000:03:01.2: [1180:0592] type 0 class 0x000880
[    0.652277] pci 0000:03:01.2: reg 10: [mem 0xf9bfd600-0xf9bfd6ff]
[    0.652430] pci 0000:03:01.2: supports D1 D2
[    0.652434] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.652445] pci 0000:03:01.2: PME# disabled
[    0.652485] pci 0000:03:01.3: [1180:0852] type 0 class 0x000880
[    0.652526] pci 0000:03:01.3: reg 10: [mem 0xf9bfd700-0xf9bfd7ff]
[    0.652677] pci 0000:03:01.3: supports D1 D2
[    0.652681] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.652692] pci 0000:03:01.3: PME# disabled
[    0.652819] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.652831] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.652841] pci 0000:00:1e.0:   bridge window [mem 0xf9b00000-0xf9bfffff]
[    0.652859] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.652866] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.652872] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.652879] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.652886] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.652892] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xf3ffffff] (subtractive decode)
[    0.652899] pci 0000:00:1e.0:   bridge window [mem 0xf8000000-0xfebfffff] (subtractive decode)
[    0.652906] pci 0000:00:1e.0:   bridge window [mem 0xfec10000-0xfecfffff] (subtractive decode)
[    0.652912] pci 0000:00:1e.0:   bridge window [mem 0xfed1c000-0xfed1ffff] (subtractive decode)
[    0.652919] pci 0000:00:1e.0:   bridge window [mem 0xfed90000-0xfed9ffff] (subtractive decode)
[    0.652932] pci 0000:00:1e.0:   bridge window [mem 0xfeda7000-0xfedfffff] (subtractive decode)
[    0.652939] pci 0000:00:1e.0:   bridge window [mem 0xfee10000-0xff9fffff] (subtractive decode)
[    0.652946] pci 0000:00:1e.0:   bridge window [mem 0xffb00000-0xffefffff] (subtractive decode)
[    0.652952] pci 0000:00:1e.0:   bridge window [mem 0x120000000-0x317ffffff] (subtractive decode)
[    0.653019] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.653645] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.653889] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.653996] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.654114] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.654239] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.654366]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.676586] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
[    0.676765] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.676939] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *4
[    0.677111] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    0.677284] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.677461] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.677650] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.677802] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.678137] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.678152] vgaarb: loaded
[    0.678650] SCSI subsystem initialized
[    0.678811] libata version 3.00 loaded.
[    0.678926] usbcore: registered new interface driver usbfs
[    0.678956] usbcore: registered new interface driver hub
[    0.679020] usbcore: registered new device driver usb
[    0.679594] wmi: Mapper loaded
[    0.679600] PCI: Using ACPI for IRQ routing
[    0.679607] PCI: pci_cache_line_size set to 64 bytes
[    0.679859] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.679866] reserve RAM buffer: 00000000dfe6d800 - 00000000dfffffff 
[    0.680136] NetLabel: Initializing
[    0.680142] NetLabel:  domain hash size = 128
[    0.680146] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.680178] NetLabel:  unlabeled traffic allowed by default
[    0.680261] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.680272] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.680284] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.700137] Switching to clocksource hpet
[    0.709724] Switched to NOHz mode on CPU #0
[    0.709843] Switched to NOHz mode on CPU #1
[    0.719121] AppArmor: AppArmor Filesystem Enabled
[    0.719187] pnp: PnP ACPI init
[    0.719230] ACPI: bus type pnp registered
[    0.738005] pnp 00:00: [bus 00-ff]
[    0.738013] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.738020] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.738026] pnp 00:00: [io  0x0d00-0xffff window]
[    0.738032] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.738038] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.738042] pnp 00:00: [mem 0xe0000000-0xf3ffffff window]
[    0.738049] pnp 00:00: [mem 0xf8000000-0xfebfffff window]
[    0.738055] pnp 00:00: [mem 0xfec10000-0xfecfffff window]
[    0.738067] pnp 00:00: [mem 0xfed1c000-0xfed1ffff window]
[    0.738073] pnp 00:00: [mem 0xfed90000-0xfed9ffff window]
[    0.738079] pnp 00:00: [mem 0xfeda7000-0xfedfffff window]
[    0.738085] pnp 00:00: [mem 0xfee10000-0xff9fffff window]
[    0.738092] pnp 00:00: [mem 0xffb00000-0xffefffff window]
[    0.738096] pnp 00:00: [mem 0x120000000-0x317ffffff window]
[    0.738289] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.738356] pnp 00:01: [irq 12]
[    0.738420] pnp 00:01: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.738464] pnp 00:02: [io  0x0060]
[    0.738470] pnp 00:02: [io  0x0064]
[    0.738473] pnp 00:02: [io  0x0062]
[    0.738479] pnp 00:02: [io  0x0066]
[    0.738492] pnp 00:02: [irq 1]
[    0.738561] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.738602] pnp 00:03: [io  0x0070-0x0071]
[    0.738615] pnp 00:03: [irq 8]
[    0.738621] pnp 00:03: [io  0x0072-0x0077]
[    0.738683] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.738728] pnp 00:04: [io  0x0061]
[    0.738733] pnp 00:04: [io  0x0063]
[    0.738737] pnp 00:04: [io  0x0065]
[    0.738742] pnp 00:04: [io  0x0067]
[    0.738814] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.738851] pnp 00:05: [io  0x0c80-0x0cff]
[    0.739004] system 00:05: [io  0x0c80-0x0cff] could not be reserved
[    0.739013] system 00:05: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.739061] pnp 00:06: [dma 4]
[    0.739066] pnp 00:06: [io  0x0000-0x000f]
[    0.739072] pnp 00:06: [io  0x0080-0x0085]
[    0.739078] pnp 00:06: [io  0x0087-0x008f]
[    0.739081] pnp 00:06: [io  0x00c0-0x00df]
[    0.739086] pnp 00:06: [io  0x0010-0x001f]
[    0.739092] pnp 00:06: [io  0x0090-0x0091]
[    0.739098] pnp 00:06: [io  0x0093-0x009f]
[    0.739172] pnp 00:06: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.739209] pnp 00:07: [io  0x00f0-0x00ff]
[    0.739223] pnp 00:07: [irq 13]
[    0.739293] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.739391] pnp 00:08: [mem 0xfed00000-0xfed003ff]
[    0.739523] system 00:08: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.739532] system 00:08: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.739881] pnp 00:09: [io  0x0900-0x097f]
[    0.739886] pnp 00:09: [io  0x0092]
[    0.739890] pnp 00:09: [io  0x00b2-0x00b3]
[    0.739895] pnp 00:09: [io  0x0020-0x0021]
[    0.739901] pnp 00:09: [io  0x00a0-0x00a1]
[    0.739907] pnp 00:09: [irq 0 disabled]
[    0.739910] pnp 00:09: [io  0x04d0-0x04d1]
[    0.739916] pnp 00:09: [io  0x1000-0x1005]
[    0.739921] pnp 00:09: [io  0x1008-0x100f]
[    0.739964] pnp 00:09: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.739974] pnp 00:09: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.740159] system 00:09: [io  0x0900-0x097f] has been reserved
[    0.740169] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.740177] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.740227] pnp 00:0a: [io  0xf400-0xf4fe]
[    0.740233] pnp 00:0a: [io  0x0086]
[    0.740245] pnp 00:0a: [io  0x1006-0x1007]
[    0.740251] pnp 00:0a: [io  0x100a-0x1059]
[    0.740254] pnp 00:0a: [io  0x1060-0x107f]
[    0.740259] pnp 00:0a: [io  0x1080-0x10bf]
[    0.740265] pnp 00:0a: [io  0x10c0-0x10df]
[    0.740270] pnp 00:0a: [io  0x1010-0x102f]
[    0.740273] pnp 00:0a: [io  0x0809]
[    0.740317] pnp 00:0a: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.740325] pnp 00:0a: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.740333] pnp 00:0a: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.740341] pnp 00:0a: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.740486] system 00:0a: [io  0xf400-0xf4fe] has been reserved
[    0.740493] system 00:0a: [io  0x1080-0x10bf] has been reserved
[    0.740500] system 00:0a: [io  0x10c0-0x10df] has been reserved
[    0.740507] system 00:0a: [io  0x0809] has been reserved
[    0.740515] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.763664] pnp 00:0b: [mem 0x00000000-0x0009efff]
[    0.763674] pnp 00:0b: [mem 0x0009f000-0x0009ffff]
[    0.763678] pnp 00:0b: [mem 0x000c0000-0x000cffff]
[    0.763684] pnp 00:0b: [mem 0x000e0000-0x000fffff]
[    0.763690] pnp 00:0b: [mem 0x00100000-0xdfe6d7ff]
[    0.763695] pnp 00:0b: [mem 0xdfe6d800-0xdfefffff]
[    0.763701] pnp 00:0b: [mem 0xdff00000-0xdfffffff]
[    0.763705] pnp 00:0b: [mem 0xdff00000-0xe06fffff]
[    0.763710] pnp 00:0b: [mem 0xfff00000-0xffffffff]
[    0.763716] pnp 00:0b: [mem 0xffa00000-0xffafffff]
[    0.763721] pnp 00:0b: [mem 0xfec00000-0xfec0ffff]
[    0.763725] pnp 00:0b: [mem 0xfee00000-0xfee0ffff]
[    0.763730] pnp 00:0b: [mem 0xfed20000-0xfed8ffff]
[    0.763736] pnp 00:0b: [mem 0xfeda0000-0xfeda3fff]
[    0.763742] pnp 00:0b: [mem 0xfeda4000-0xfeda4fff]
[    0.763747] pnp 00:0b: [mem 0xfeda5000-0xfeda5fff]
[    0.763751] pnp 00:0b: [mem 0xfeda6000-0xfeda6fff]
[    0.763756] pnp 00:0b: [mem 0xfed18000-0xfed1bfff]
[    0.763762] pnp 00:0b: [mem 0xf4000000-0xf7ffffff]
[    0.763783] pnp 00:0b: disabling [mem 0xdff00000-0xe06fffff] because it overlaps 0000:00:01.0 BAR 15 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.763855] pnp 00:0b: disabling [mem 0xdff00000-0xe06fffff disabled] because it overlaps 0000:01:00.0 BAR 1 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.764061] system 00:0b: [mem 0x00000000-0x0009efff] could not be reserved
[    0.764071] system 00:0b: [mem 0x0009f000-0x0009ffff] could not be reserved
[    0.764078] system 00:0b: [mem 0x000c0000-0x000cffff] has been reserved
[    0.764085] system 00:0b: [mem 0x000e0000-0x000fffff] has been reserved
[    0.764093] system 00:0b: [mem 0x00100000-0xdfe6d7ff] could not be reserved
[    0.764099] system 00:0b: [mem 0xdfe6d800-0xdfefffff] has been reserved
[    0.764106] system 00:0b: [mem 0xdff00000-0xdfffffff] has been reserved
[    0.764113] system 00:0b: [mem 0xfff00000-0xffffffff] has been reserved
[    0.764120] system 00:0b: [mem 0xffa00000-0xffafffff] has been reserved
[    0.764127] system 00:0b: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.764134] system 00:0b: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.764141] system 00:0b: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.764148] system 00:0b: [mem 0xfeda0000-0xfeda3fff] has been reserved
[    0.764154] system 00:0b: [mem 0xfeda4000-0xfeda4fff] has been reserved
[    0.764161] system 00:0b: [mem 0xfeda5000-0xfeda5fff] has been reserved
[    0.764168] system 00:0b: [mem 0xfeda6000-0xfeda6fff] has been reserved
[    0.764175] system 00:0b: [mem 0xfed18000-0xfed1bfff] has been reserved
[    0.764182] system 00:0b: [mem 0xf4000000-0xf7ffffff] has been reserved
[    0.764192] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.764343] pnp: PnP ACPI: found 12 devices
[    0.764349] ACPI: ACPI bus type pnp unregistered
[    0.773569] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf0200000-0xf03fffff]
[    0.773582] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.773595] pci 0000:00:1c.1: BAR 15: assigned [mem 0xf0600000-0xf07fffff 64bit pref]
[    0.773603] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.773611] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.773618] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.773627] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.773636] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfeafffff]
[    0.773644] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.773656] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.773664] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.773677] pci 0000:00:1c.0:   bridge window [mem 0xf0200000-0xf03fffff]
[    0.773689] pci 0000:00:1c.0:   bridge window [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.773705] pci 0000:00:1c.1: PCI bridge to [bus 0c-0c]
[    0.773712] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.773725] pci 0000:00:1c.1:   bridge window [mem 0xf9f00000-0xf9ffffff]
[    0.773735] pci 0000:00:1c.1:   bridge window [mem 0xf0600000-0xf07fffff 64bit pref]
[    0.773753] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.773760] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.773773] pci 0000:00:1c.3:   bridge window [mem 0xf9c00000-0xf9efffff]
[    0.773783] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.773802] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.773807] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.773820] pci 0000:00:1e.0:   bridge window [mem 0xf9b00000-0xf9bfffff]
[    0.773830] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.773877] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.773887] pci 0000:00:01.0: setting latency timer to 64
[    0.773905] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.773914] pci 0000:00:1c.0: setting latency timer to 64
[    0.773939] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.773949] pci 0000:00:1c.1: setting latency timer to 64
[    0.773973] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.773983] pci 0000:00:1c.3: setting latency timer to 64
[    0.774001] pci 0000:00:1e.0: setting latency timer to 64
[    0.774010] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.774016] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.774022] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.774028] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.774035] pci_bus 0000:00: resource 8 [mem 0xe0000000-0xf3ffffff]
[    0.774039] pci_bus 0000:00: resource 9 [mem 0xf8000000-0xfebfffff]
[    0.774045] pci_bus 0000:00: resource 10 [mem 0xfec10000-0xfecfffff]
[    0.774051] pci_bus 0000:00: resource 11 [mem 0xfed1c000-0xfed1ffff]
[    0.774057] pci_bus 0000:00: resource 12 [mem 0xfed90000-0xfed9ffff]
[    0.774063] pci_bus 0000:00: resource 13 [mem 0xfeda7000-0xfedfffff]
[    0.774070] pci_bus 0000:00: resource 14 [mem 0xfee10000-0xff9fffff]
[    0.774076] pci_bus 0000:00: resource 15 [mem 0xffb00000-0xffefffff]
[    0.774082] pci_bus 0000:00: resource 16 [mem 0x120000000-0x317ffffff]
[    0.774089] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.774095] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfeafffff]
[    0.774099] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.774106] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]
[    0.774112] pci_bus 0000:0b: resource 1 [mem 0xf0200000-0xf03fffff]
[    0.774118] pci_bus 0000:0b: resource 2 [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.774125] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]
[    0.774131] pci_bus 0000:0c: resource 1 [mem 0xf9f00000-0xf9ffffff]
[    0.774137] pci_bus 0000:0c: resource 2 [mem 0xf0600000-0xf07fffff 64bit pref]
[    0.774144] pci_bus 0000:0d: resource 0 [io  0xd000-0xdfff]
[    0.774150] pci_bus 0000:0d: resource 1 [mem 0xf9c00000-0xf9efffff]
[    0.774156] pci_bus 0000:0d: resource 2 [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.774163] pci_bus 0000:03: resource 1 [mem 0xf9b00000-0xf9bfffff]
[    0.774167] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.774173] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.774179] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.774185] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.774191] pci_bus 0000:03: resource 8 [mem 0xe0000000-0xf3ffffff]
[    0.774197] pci_bus 0000:03: resource 9 [mem 0xf8000000-0xfebfffff]
[    0.774203] pci_bus 0000:03: resource 10 [mem 0xfec10000-0xfecfffff]
[    0.774210] pci_bus 0000:03: resource 11 [mem 0xfed1c000-0xfed1ffff]
[    0.774214] pci_bus 0000:03: resource 12 [mem 0xfed90000-0xfed9ffff]
[    0.774220] pci_bus 0000:03: resource 13 [mem 0xfeda7000-0xfedfffff]
[    0.774226] pci_bus 0000:03: resource 14 [mem 0xfee10000-0xff9fffff]
[    0.774232] pci_bus 0000:03: resource 15 [mem 0xffb00000-0xffefffff]
[    0.774238] pci_bus 0000:03: resource 16 [mem 0x120000000-0x317ffffff]
[    0.774322] NET: Registered protocol family 2
[    0.774699] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.777556] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.785123] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.786073] TCP: Hash tables configured (established 524288 bind 65536)
[    0.786079] TCP reno registered
[    0.786100] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.786179] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.786453] NET: Registered protocol family 1
[    0.786837] pci 0000:01:00.0: Boot video device
[    0.786885] PCI: CLS 64 bytes, default 64
[    0.786892] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.786899] Placing 64MB software IO TLB between ffff8800dbc00000 - ffff8800dfc00000
[    0.786905] software IO TLB at phys 0xdbc00000 - 0xdfc00000
[    0.786990] Simple Boot Flag at 0x79 set to 0x1
[    0.787773] audit: initializing netlink socket (disabled)
[    0.787798] type=2000 audit(1313149539.780:1): initialized
[    0.823458] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.828127] VFS: Disk quotas dquot_6.5.2
[    0.828273] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.829866] fuse init (API version 7.16)
[    0.830136] msgmni has been set to 7891
[    0.830685] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.830747] io scheduler noop registered
[    0.830752] io scheduler deadline registered
[    0.830855] io scheduler cfq registered (default)
[    0.831128] pcieport 0000:00:01.0: setting latency timer to 64
[    0.831208] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.831332] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.831431] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.831588] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.831687] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.831844] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.831943] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.832157] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.832214] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.832331] intel_idle: MWAIT substates: 0x22220
[    0.832335] intel_idle: does not run on family 6 model 15
[    0.832518] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.832649] ACPI: AC Adapter [AC] (on-line)
[    0.832834] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.960044] ACPI: Lid Switch [LID]
[    0.960213] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.053458] Freeing initrd memory: 12872k freed
[    1.090045] ACPI: Power Button [PBTN]
[    1.090251] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.090265] ACPI: Sleep Button [SBTN]
[    1.090815] ACPI: acpi_idle registered with cpuidle
[    1.091255] Monitor-Mwait will be used to enter C-1 state
[    1.091317] Monitor-Mwait will be used to enter C-2 state
[    1.091464] Monitor-Mwait will be used to enter C-3 state
[    1.091482] Marking TSC unstable due to TSC halts in idle
[    1.102191] thermal LNXTHERM:00: registered as thermal_zone0
[    1.102198] ACPI: Thermal Zone [THM] (28 C)
[    1.102353] ERST: Table is not found!
[    1.102561] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.140053] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.140071] ACPI: Battery Slot [BAT0] (battery present)
[    1.251280] Linux agpgart interface v0.103
[    1.254627] brd: module loaded
[    1.256008] loop: module loaded
[    1.256218] i2c-core: driver [adp5520] using legacy suspend method
[    1.256224] i2c-core: driver [adp5520] using legacy resume method
[    1.256464] ata_piix 0000:00:1f.1: version 2.13
[    1.256489] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.256570] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.257348] scsi0 : ata_piix
[    1.257558] scsi1 : ata_piix
[    1.258347] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    1.258355] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    1.258483] ata2: port disabled. ignoring.
[    1.259172] Fixed MDIO Bus: probed
[    1.259245] PPP generic driver version 2.4.2
[    1.259341] tun: Universal TUN/TAP device driver, 1.6
[    1.259346] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.259544] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.259592] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.259639] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.259649] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.259736] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.259864] ehci_hcd 0000:00:1a.7: debug port 1
[    1.263772] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    1.263807] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    1.280034] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.280339] hub 1-0:1.0: USB hub found
[    1.280351] hub 1-0:1.0: 4 ports detected
[    1.280556] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.280584] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.280592] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.280685] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.280799] ehci_hcd 0000:00:1d.7: debug port 1
[    1.284703] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.284738] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    1.300032] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.300319] hub 2-0:1.0: USB hub found
[    1.300330] hub 2-0:1.0: 6 ports detected
[    1.300521] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.300552] uhci_hcd: USB Universal Host Controller Interface driver
[    1.300676] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.300691] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.300699] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.300800] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.300897] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    1.301191] hub 3-0:1.0: USB hub found
[    1.301203] hub 3-0:1.0: 2 ports detected
[    1.301376] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.301391] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.301399] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.301500] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.301616] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    1.301900] hub 4-0:1.0: USB hub found
[    1.301909] hub 4-0:1.0: 2 ports detected
[    1.302083] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.302098] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.302106] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.302218] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.302312] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    1.302597] hub 5-0:1.0: USB hub found
[    1.302608] hub 5-0:1.0: 2 ports detected
[    1.302776] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.302791] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.302798] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.302892] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.302988] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    1.303280] hub 6-0:1.0: USB hub found
[    1.303289] hub 6-0:1.0: 2 ports detected
[    1.303457] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.303472] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.303479] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.303577] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.303669] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    1.303968] hub 7-0:1.0: USB hub found
[    1.303977] hub 7-0:1.0: 2 ports detected
[    1.304288] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.307348] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.307363] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.307664] mousedev: PS/2 mouse device common for all mice
[    1.308019] rtc_cmos 00:03: RTC can wake from S4
[    1.308170] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.308245] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.308487] device-mapper: uevent: version 1.0.3
[    1.308670] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.308812] device-mapper: multipath: version 1.2.0 loaded
[    1.308818] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.309238] cpuidle: using governor ladder
[    1.309469] cpuidle: using governor menu
[    1.310066] TCP cubic registered
[    1.310379] NET: Registered protocol family 10
[    1.311568] NET: Registered protocol family 17
[    1.311602] Registering the dns_resolver key type
[    1.311959] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.317590] PM: Hibernation image not present or could not be loaded.
[    1.317648] registered taskstats version 1
[    1.318607]   Magic number: 7:315:782
[    1.318900] rtc_cmos 00:03: setting system clock to 2011-08-12 11:45:40 UTC (1313149540)
[    1.318909] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.318917] EDD information not available.
[    1.430761] ata1.00: ATAPI: MATSHITA DVDRW/BDROM UJ-110, 1Y00, max UDMA/33
[    1.470591] ata1.00: configured for UDMA/33
[    1.481643] scsi 0:0:0:0: CD-ROM            MATSHITA DVDRWBD UJ-110   1Y00 PQ: 0 ANSI: 5
[    1.485110] sr0: scsi3-mmc drive: 62x/62x writer cd/rw xa/form2 cdda tray
[    1.485122] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.485530] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.485753] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.492834] Freeing unused kernel memory: 956k freed
[    1.493529] Write protecting the kernel read-only data: 10240k
[    1.496626] Freeing unused kernel memory: 184k freed
[    1.516484] Freeing unused kernel memory: 1440k freed
[    1.577533] <30>udev[72]: starting version 167
[    1.720095] usb 2-6: new high speed USB device using ehci_hcd and address 2
[    1.945288] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.956663] ahci 0000:00:1f.2: version 3.0
[    1.956694] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.956829] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.956986] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[    1.956999] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc ems 
[    1.957015] ahci 0000:00:1f.2: setting latency timer to 64
[    1.964123] sdhci: Secure Digital Host Controller Interface driver
[    1.964134] sdhci: Copyright(c) Pierre Ossman
[    1.974546] scsi2 : ahci
[    1.977597] scsi3 : ahci
[    1.977875] scsi4 : ahci
[    1.978422] ata3: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb900 irq 44
[    1.978433] ata4: DUMMY
[    1.978440] ata5: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfba00 irq 44
[    2.020495] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
[    2.020700] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.060243] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    2.060267] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    2.060283] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    2.140452] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    2.140552] b44: b44.c:v2.0
[    2.140665] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[    2.140731] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.141907] mmc0: no vmmc regulator found
[    2.143050] Registered led device: mmc0::
[    2.144195] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    2.150136] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    2.182202] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:c7:4f:6e
[    2.320230] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.330124] ata5: SATA link down (SStatus 0 SControl 300)
[    2.336204] hub 3-2:1.0: USB hub found
[    2.338028] hub 3-2:1.0: 3 ports detected
[    2.376312] ata3.00: ATA-8: TOSHIBA MK3252GSX, LV010D, max UDMA/100
[    2.376325] ata3.00: 625142448 sectors, multi 8: LBA48 NCQ (depth 31/32), AA
[    2.377690] ata3.00: configured for UDMA/100
[    2.378136] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK3252GS LV01 PQ: 0 ANSI: 5
[    2.378774] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.378883] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.379149] sd 2:0:0:0: [sda] Write Protect is off
[    2.379163] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.379320] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.461821]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    2.463242] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.520505] firewire_core: created device fw0: GUID 334fc0000ee4bc70, S400
[    2.622056] usb 3-2.1: new full speed USB device using uhci_hcd and address 3
[    2.842146] usb 3-2.2: new full speed USB device using uhci_hcd and address 4
[    3.057803] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.2/3-2.2:1.0/input/input4
[    3.058147] generic-usb 0003:0A5C:4502.0001: input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2/input0
[    3.058211] usbcore: registered new interface driver usbhid
[    3.058216] usbhid: USB HID core driver
[    3.062036] usb 3-2.3: new full speed USB device using uhci_hcd and address 5
[    3.224359] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input5
[    3.224746] generic-usb 0003:0A5C:4503.0002: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0
[    3.399896] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.662863] Adding 7875580k swap on /dev/sda6.  Priority:-1 extents:1 across:7875580k 
[    5.948083] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    6.419907] <30>udev[321]: starting version 167
[    8.256761] type=1400 audit(1313142347.429:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=562 comm="apparmor_parser"
[    8.256799] type=1400 audit(1313142347.429:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=470 comm="apparmor_parser"
[    8.260223] type=1400 audit(1313142347.439:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=562 comm="apparmor_parser"
[    8.260659] type=1400 audit(1313142347.439:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=470 comm="apparmor_parser"
[    8.262349] type=1400 audit(1313142347.439:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=562 comm="apparmor_parser"
[    8.262806] type=1400 audit(1313142347.439:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=470 comm="apparmor_parser"
[    8.420980] cfg80211: Calling CRDA to update world regulatory domain
[    8.608526] Bluetooth: Core ver 2.15
[    8.608696] NET: Registered protocol family 31
[    8.608702] Bluetooth: HCI device and connection manager initialized
[    8.608712] Bluetooth: HCI socket layer initialized
[    8.794820] input: Dell WMI hotkeys as /devices/virtual/input/input6
[    8.948941] acpi device:31: registered as cooling_device2
[    8.950440] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/LNXVIDEO:00/input/input7
[    8.950740] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    8.950888] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[    9.015113] Linux video capture interface: v2.00
[    9.043294] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    9.053118] usbcore: registered new interface driver btusb
[    9.130502] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[    9.131086] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[    9.132553] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input8
[    9.132946] usbcore: registered new interface driver uvcvideo
[    9.132956] USB Video Class driver (v1.0.0)
[    9.272217] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input9
[    9.290441] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10
[    9.301648] lp: driver loaded but no devices found
[    9.606496] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    9.780718] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[    9.780730] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[    9.780920] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.780948] iwl3945 0000:0c:00.0: setting latency timer to 64
[    9.846884] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[    9.846898] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[    9.847138] iwl3945 0000:0c:00.0: irq 45 for MSI/MSI-X
[    9.847753] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   10.021542] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   10.100734] r852 0000:03:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   10.100981] r852: driver loaded succesfully
[   10.712211] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   10.712227] cfg80211: World regulatory domain updated:
[   10.712236] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.712248] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.712260] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.712267] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.712278] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.712289] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.160696] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.160885] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   11.160969] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.744211] type=1400 audit(1313142350.919:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=795 comm="apparmor_parser"
[   11.747677] type=1400 audit(1313142350.919:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=795 comm="apparmor_parser"
[   11.750745] type=1400 audit(1313142350.929:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=795 comm="apparmor_parser"
[   11.820961] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   11.821777] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   12.052194] type=1400 audit(1313142351.229:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=794 comm="apparmor_parser"
[   12.083752] Bluetooth: L2CAP ver 2.15
[   12.083759] Bluetooth: L2CAP socket layer initialized
[   12.176215] nvidia: module license 'NVIDIA' taints kernel.
[   12.176226] Disabling lock debugging due to kernel taint
[   14.518273] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.518305] nvidia 0000:01:00.0: setting latency timer to 64
[   14.518321] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   14.520102] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.06  Mon Apr 18 14:53:56 PDT 2011
[   14.912050] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.912062] Bluetooth: BNEP filters: protocol multicast
[   15.640220] Bluetooth: SCO (Voice Link) ver 0.6
[   15.640231] Bluetooth: SCO socket layer initialized
[   16.150092] Bluetooth: RFCOMM TTY layer initialized
[   16.150115] Bluetooth: RFCOMM socket layer initialized
[   16.150124] Bluetooth: RFCOMM ver 1.11
[   16.272110] ppdev: user-space parallel port driver
[   16.299331] vesafb: framebuffer at 0xfb000000, mapped to 0xffffc90005880000, using 9024k, total 9024k
[   16.299345] vesafb: mode is 1920x1200x32, linelength=7680, pages=0
[   16.299354] vesafb: scrolling: redraw
[   16.299361] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   16.310200] Console: switching to colour frame buffer device 240x75
[   16.310364] fb0: VESA VGA frame buffer device
[   17.203618] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[   17.288784] iwl3945 0000:0c:00.0: Error setting Tx power (-5).
[   17.291960] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.321522] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.889342] type=1400 audit(1313142357.059:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=812 comm="apparmor_parser"
[   17.891614] type=1400 audit(1313142357.069:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=812 comm="apparmor_parser"
[   18.047953] type=1400 audit(1313142357.219:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=946 comm="apparmor_parser"
[   19.728666] type=1400 audit(1313142358.899:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=861 comm="apparmor_parser"
[   19.730134] type=1400 audit(1313142358.909:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=861 comm="apparmor_parser"
[   32.482035] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   36.769634] type=1400 audit(1313142375.939:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=798 comm="apparmor_parser"
[   36.774562] type=1400 audit(1313142375.949:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=798 comm="apparmor_parser"
[   36.777121] type=1400 audit(1313142375.949:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=798 comm="apparmor_parser"
[   55.844567] wlan0: authenticate with b4:74:9f:2a:91:d5 (try 1)
[   55.846373] wlan0: authenticated
[   55.850192] wlan0: associate with b4:74:9f:2a:91:d5 (try 1)
[   55.858475] wlan0: RX AssocResp from b4:74:9f:2a:91:d5 (capab=0x411 status=0 aid=2)
[   55.858488] wlan0: associated
[   55.862149] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   56.184994] Intel AES-NI instructions are not detected.
[   56.246149] padlock_aes: VIA PadLock not detected.
[   66.310048] wlan0: no IPv6 routers present
[   79.620233] usb 5-2: new low speed USB device using uhci_hcd and address 2
[   79.815577] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input13
[   79.816007] generic-usb 0003:046D:C047.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-2/input0
[  327.337034] i8k: unable to get SMM BIOS version
[  327.337071] Dell laptop SMM driver v1.14 21/02/2005 Massimo Dal Zotto (dz@debian.org)
[  341.000228] CE: hpet increased min_delta_ns to 20113 nsec
[  362.141347] exe (2071): /proc/2071/oom_adj is deprecated, please use /proc/2071/oom_score_adj instead.
[  385.864428] CE: hpet increased min_delta_ns to 30169 nsec
[ 4406.170261] usb 2-1: new high speed USB device using ehci_hcd and address 4
[ 4406.387363] usbcore: registered new interface driver uas
[ 4406.417296] Initializing USB Mass Storage driver...
[ 4406.417748] scsi5 : usb-storage 2-1:1.0
[ 4406.418972] usbcore: registered new interface driver usb-storage
[ 4406.418983] USB Mass Storage support registered.
[ 4407.448129] scsi 5:0:0:0: Direct-Access              USB Flash Memory PMAP PQ: 0 ANSI: 0 CCS
[ 4407.451023] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 4408.715697] sd 5:0:0:0: [sdb] 31375360 512-byte logical blocks: (16.0 GB/14.9 GiB)
[ 4408.716292] sd 5:0:0:0: [sdb] Write Protect is off
[ 4408.716305] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 4408.716312] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 4411.687458] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 4411.718394]  sdb: sdb1
[ 4411.720649] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 4411.720664] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 5532.643407] EXT3-fs: barriers not enabled
[ 5532.651279] kjournald starting.  Commit interval 5 seconds
[ 5532.651835] EXT3-fs (sda5): using internal journal
[ 5532.651849] EXT3-fs (sda5): mounted filesystem with ordered data mode
[ 5715.266895] wlan0: deauthenticating from b4:74:9f:2a:91:d5 by local choice (reason=3)
[ 5715.310551] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 5715.310567] cfg80211: Restoring regulatory settings
[ 5715.310586] cfg80211: Calling CRDA to update world regulatory domain
[ 5715.323672] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 5715.323687] cfg80211: World regulatory domain updated:
[ 5715.323695] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 5715.323707] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5715.323715] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5715.323726] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5715.323737] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5715.323748] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5715.520299] b44 ssb0:0: eth0: powering down PHY
[ 5716.539662] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 5720.304736] usb 2-1: USB disconnect, address 4
[ 5724.100221] PM: Syncing filesystems ... done.
[ 5724.114805] PM: Preparing system for mem sleep
[ 5724.114849] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 5724.130359] Freezing remaining freezable tasks ... (elapsed 0.02 seconds) done.
[ 5724.150401] PM: Entering mem sleep
[ 5724.150439] Suspending console(s) (use no_console_suspend to debug)
[ 5724.153010] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[ 5724.165847] b44 0000:03:00.0: PCI INT A disabled
[ 5724.165863] ACPI handle has no context!
[ 5724.165869] ACPI handle has no context!
[ 5724.165885] sdhci-pci 0000:03:01.1: PCI INT B disabled
[ 5724.165905] ACPI handle has no context!
[ 5724.169487] sd 2:0:0:0: [sda] Stopping disk
[ 5724.170182] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 5724.170210] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 5724.170237] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 5724.171200] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[ 5724.171227] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[ 5724.171261] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 5724.171485] ata_piix 0000:00:1f.1: PCI INT A disabled
[ 5724.190184] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[ 5724.410170] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 5724.430050] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 259.747 msecs
[ 5724.647718] PM: suspend of drv:sd dev:2:0:0:0 complete after 494.719 msecs
[ 5724.647753] PM: suspend of drv:scsi dev:target2:0:0 complete after 494.507 msecs
[ 5724.647790] PM: suspend of drv:scsi dev:host2 complete after 494.193 msecs
[ 5724.660060] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 493.993 msecs
[ 5724.660090] PM: suspend of drv: dev:pci0000:00 complete after 488.567 msecs
[ 5724.660112] PM: suspend of devices complete after 508.347 msecs
[ 5724.660119] PM: suspend devices took 0.510 seconds
[ 5724.740507] PM: late suspend of devices complete after 80.376 msecs
[ 5724.741517] ACPI: Preparing to enter system sleep state S3
[ 5724.750072] PM: Saving platform NVS memory
[ 5724.750078] Disabling non-boot CPUs ...
[ 5724.860040] CPU 1 is now offline
[ 5724.861116] Extended CMOS year: 2000
[ 5724.861116] Back to C!
[ 5724.861116] PM: Restoring platform NVS memory
[ 5724.861116] Extended CMOS year: 2000
[ 5724.861116] Enabling non-boot CPUs ...
[ 5724.861116] Booting Node 0 Processor 1 APIC 0x1
[ 5725.030031] Switched to NOHz mode on CPU #1
[ 5725.030179] CPU1 is up
[ 5725.033229] ACPI: Waking up from system sleep state S3
[ 5725.045567] pcieport 0000:00:01.0: restoring config space at offset 0xf (was 0x100, writing 0x1a0100)
[ 5725.045590] pcieport 0000:00:01.0: restoring config space at offset 0xa (was 0xf, writing 0x0)
[ 5725.045604] pcieport 0000:00:01.0: restoring config space at offset 0x9 (was 0x1fff1, writing 0xeff1e001)
[ 5725.045619] pcieport 0000:00:01.0: restoring config space at offset 0x7 (was 0xf0, writing 0xe0e0)
[ 5725.045632] pcieport 0000:00:01.0: restoring config space at offset 0x6 (was 0x0, writing 0x10100)
[ 5725.045647] pcieport 0000:00:01.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
[ 5725.045662] pcieport 0000:00:01.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100507)
[ 5725.045737] uhci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 5725.045769] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x8 (was 0x1, writing 0x6f21)
[ 5725.045805] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[ 5725.045838] uhci_hcd 0000:00:1a.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 5725.045874] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x8 (was 0x1, writing 0x6f01)
[ 5725.045906] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[ 5725.045958] ehci_hcd 0000:00:1a.7: restoring config space at offset 0xf (was 0x300, writing 0x309)
[ 5725.046003] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x4 (was 0x0, writing 0xfed1c400)
[ 5725.046026] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900102)
[ 5725.046105] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 5725.046151] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 5725.046172] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[ 5725.046247] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x20100)
[ 5725.046281] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0xf051f041)
[ 5725.046295] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xf030f020)
[ 5725.046310] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x0, writing 0x2020)
[ 5725.046324] pcieport 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0xb0b00)
[ 5725.046343] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 5725.046364] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 5725.046480] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x20200)
[ 5725.046513] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0xf071f061)
[ 5725.046528] pcieport 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xf9f0f9f0)
[ 5725.046542] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0x0, writing 0x3030)
[ 5725.046557] pcieport 0000:00:1c.1: restoring config space at offset 0x6 (was 0x0, writing 0xc0c00)
[ 5725.046576] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 5725.046596] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 5725.046711] pcieport 0000:00:1c.3: restoring config space at offset 0xf (was 0x400, writing 0x20400)
[ 5725.046745] pcieport 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0xf011f001)
[ 5725.046760] pcieport 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xf9e0f9c0)
[ 5725.046774] pcieport 0000:00:1c.3: restoring config space at offset 0x7 (was 0x0, writing 0xd0d0)
[ 5725.046788] pcieport 0000:00:1c.3: restoring config space at offset 0x6 (was 0x0, writing 0xe0d00)
[ 5725.046807] pcieport 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 5725.046828] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 5725.046966] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 5725.046998] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 5725.047033] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x8 (was 0x1, writing 0x6f61)
[ 5725.047065] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[ 5725.047101] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x309)
[ 5725.047132] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x8 (was 0x1, writing 0x6f41)
[ 5725.047168] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[ 5725.047263] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[ 5725.047338] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x100f1, writing 0x1fff1)
[ 5725.047357] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0xb0, writing 0xf9b0f9b0)
[ 5725.047371] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x2280e0f0, writing 0x228000f0)
[ 5725.047401] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100107)
[ 5725.047503] pci 0000:00:1f.0: restoring config space at offset 0x1 (was 0x2100007, writing 0x2100107)
[ 5725.047551] ata_piix 0000:00:1f.1: restoring config space at offset 0xf (was 0x100, writing 0x107)
[ 5725.047606] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2880005)
[ 5725.047662] ahci 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 5725.047692] ahci 0000:00:1f.2: restoring config space at offset 0x9 (was 0x0, writing 0xfebfb800)
[ 5725.047729] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00407)
[ 5725.047810] pci 0000:00:1f.3: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 5725.047855] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x0, writing 0xfebfb700)
[ 5725.047873] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800103)
[ 5725.047938] nvidia 0000:01:00.0: restoring config space at offset 0xf (was 0x100, writing 0x107)
[ 5725.047968] nvidia 0000:01:00.0: restoring config space at offset 0x9 (was 0x1, writing 0xef01)
[ 5725.047990] nvidia 0000:01:00.0: restoring config space at offset 0x7 (was 0x4, writing 0xfa000004)
[ 5725.048007] nvidia 0000:01:00.0: restoring config space at offset 0x5 (was 0xc, writing 0xe000000c)
[ 5725.048022] nvidia 0000:01:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xfd000000)
[ 5725.048046] nvidia 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 5725.048226] iwl3945 0000:0c:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 5725.048329] iwl3945 0000:0c:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xf9fff000)
[ 5725.048355] iwl3945 0000:0c:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 5725.048391] iwl3945 0000:0c:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[ 5725.048594] b44 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 5725.048639] b44 0000:03:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xf9bfe000)
[ 5725.048653] b44 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
[ 5725.048670] b44 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[ 5725.048725] firewire_ohci 0000:03:01.0: restoring config space at offset 0xf (was 0x4020100, writing 0x4020105)
[ 5725.048777] firewire_ohci 0000:03:01.0: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 5725.048795] firewire_ohci 0000:03:01.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 5725.048842] firewire_ohci 0000:03:01.0: proprietary Ricoh MMC controller disabled (via firewire function)
[ 5725.048847] firewire_ohci 0000:03:01.0: MMC cards are now supported by standard SDHCI controller
[ 5725.048883] sdhci-pci 0000:03:01.1: restoring config space at offset 0xf (was 0x200, writing 0x204)
[ 5725.048930] sdhci-pci 0000:03:01.1: restoring config space at offset 0x4 (was 0x0, writing 0xf9bfd400)
[ 5725.048945] sdhci-pci 0000:03:01.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 5725.048966] sdhci-pci 0000:03:01.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 5725.049021] pci 0000:03:01.2: restoring config space at offset 0xf (was 0x200, writing 0x204)
[ 5725.049067] pci 0000:03:01.2: restoring config space at offset 0x4 (was 0x0, writing 0xf9bfd600)
[ 5725.049081] pci 0000:03:01.2: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 5725.049102] pci 0000:03:01.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 5725.049157] r852 0000:03:01.3: restoring config space at offset 0xf (was 0x200, writing 0x204)
[ 5725.049203] r852 0000:03:01.3: restoring config space at offset 0x4 (was 0x0, writing 0xf9bfd700)
[ 5725.049222] r852 0000:03:01.3: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 5725.049239] r852 0000:03:01.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 5725.050625] PM: early resume of devices complete after 5.447 msecs
[ 5725.060519] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 5725.060542] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[ 5725.060595] usb usb3: root hub lost power or was reset
[ 5725.060635] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 5725.060651] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[ 5725.060698] usb usb4: root hub lost power or was reset
[ 5725.060737] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[ 5725.060760] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[ 5725.060906] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 5725.060928] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 5725.061066] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[ 5725.061220] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 5725.061237] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 5725.061300] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 5725.061305] usb usb5: root hub lost power or was reset
[ 5725.061320] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 5725.061344] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[ 5725.061362] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 5725.061386] usb usb6: root hub lost power or was reset
[ 5725.061428] usb usb7: root hub lost power or was reset
[ 5725.061439] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 5725.061457] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 5725.061476] pci 0000:00:1e.0: setting latency timer to 64
[ 5725.061511] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 5725.061524] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 5725.061596] ahci 0000:00:1f.2: setting latency timer to 64
[ 5725.061733] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 5725.061842] ata1.00: _GTF evaluation failed (AE 0x1001)
[ 5725.062157] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[ 5725.065143] sd 2:0:0:0: [sda] Starting disk
[ 5725.066921] ata2: port disabled. ignoring.
[ 5725.140588] firewire_core: skipped bus generations, destroying all nodes
[ 5725.165982] PM: resume of drv:button dev:PNP0C0D:00 complete after 104.731 msecs
[ 5725.203678] PM: resume of drv:usb dev:usb4 complete after 140.105 msecs
[ 5725.203794] PM: resume of drv:usb dev:usb6 complete after 139.749 msecs
[ 5725.203851] PM: resume of drv:usb dev:usb7 complete after 139.569 msecs
[ 5725.203878] PM: resume of drv:hub dev:4-0:1.0 complete after 140.243 msecs
[ 5725.203901] PM: resume of drv: dev:ep_00 complete after 140.152 msecs
[ 5725.203916] PM: resume of drv:hub dev:6-0:1.0 complete after 139.804 msecs
[ 5725.203939] PM: resume of drv: dev:ep_00 complete after 139.705 msecs
[ 5725.203954] PM: resume of drv:hub dev:7-0:1.0 complete after 139.606 msecs
[ 5725.203972] PM: resume of drv: dev:ep_00 complete after 139.508 msecs
[ 5725.203992] PM: resume of drv: dev:ep_81 complete after 140.299 msecs
[ 5725.204007] PM: resume of drv: dev:ep_81 complete after 139.829 msecs
[ 5725.204022] PM: resume of drv: dev:ep_81 complete after 139.608 msecs
[ 5725.310126] PM: resume of drv:usb dev:usb3 complete after 246.694 msecs
[ 5725.310180] PM: resume of drv:usb dev:usb5 complete after 246.369 msecs
[ 5725.310219] PM: resume of drv:hub dev:5-0:1.0 complete after 246.342 msecs
[ 5725.310243] PM: resume of drv: dev:ep_00 complete after 246.250 msecs
[ 5725.310261] PM: resume of drv: dev:ep_81 complete after 246.329 msecs
[ 5725.310340] PM: resume of drv: dev:ep_00 complete after 246.873 msecs
[ 5725.310369] PM: resume of drv:hub dev:3-0:1.0 complete after 246.923 msecs
[ 5725.310394] PM: resume of drv: dev:ep_81 complete after 246.938 msecs
[ 5725.340078] PM: resume of drv:usb dev:usb1 complete after 276.756 msecs
[ 5725.340112] PM: resume of drv:usb dev:usb2 complete after 276.740 msecs
[ 5725.340190] PM: resume of drv:usb dev:3-2 complete after 275.274 msecs
[ 5725.340231] PM: resume of drv:hub dev:2-0:1.0 complete after 276.844 msecs
[ 5725.340272] PM: resume of drv:usb dev:2-6 complete after 275.706 msecs
[ 5725.340341] PM: resume of drv:hub dev:3-2:1.0 complete after 275.369 msecs
[ 5725.340366] PM: resume of drv:usb dev:3-2.1 complete after 275.030 msecs
[ 5725.340406] PM: resume of drv:usb dev:3-2.3 complete after 274.114 msecs
[ 5725.340432] PM: resume of drv: dev:ep_81 complete after 277.030 msecs
[ 5725.340448] PM: resume of drv:uvcvideo dev:2-6:1.0 complete after 275.819 msecs
[ 5725.340471] PM: resume of drv: dev:ep_00 complete after 275.676 msecs
[ 5725.340486] PM: resume of drv: dev:ep_81 complete after 275.462 msecs
[ 5725.340502] PM: resume of drv:btusb dev:3-2.1:1.0 complete after 275.113 msecs
[ 5725.340530] PM: resume of drv:btusb dev:3-2.1:1.1 complete after 274.911 msecs
[ 5725.340557] PM: resume of drv:usb dev:3-2.1:1.3 complete after 274.601 msecs
[ 5725.340573] PM: resume of drv: dev:ep_00 complete after 274.562 msecs
[ 5725.340592] PM: resume of drv:usbhid dev:3-2.3:1.0 complete after 274.242 msecs
[ 5725.340611] PM: resume of drv: dev:ep_83 complete after 275.932 msecs
[ 5725.340626] PM: resume of drv: dev:ep_81 complete after 275.182 msecs
[ 5725.340645] PM: resume of drv: dev:ep_82 complete after 275.143 msecs
[ 5725.340661] PM: resume of drv: dev:ep_02 complete after 275.099 msecs
[ 5725.340676] PM: resume of drv: dev:ep_83 complete after 274.982 msecs
[ 5725.340691] PM: resume of drv: dev:ep_03 complete after 274.943 msecs
[ 5725.340707] PM: resume of drv: dev:ep_81 complete after 274.305 msecs
[ 5725.340740] PM: resume of drv: dev:ep_00 complete after 274.272 msecs
[ 5725.340768] PM: resume of drv:usb dev:3-2.1:1.2 complete after 274.961 msecs
[ 5725.340794] PM: resume of drv: dev:ep_84 complete after 274.935 msecs
[ 5725.340809] PM: resume of drv: dev:ep_04 complete after 274.903 msecs
[ 5725.340837] PM: resume of drv:uvcvideo dev:2-6:1.1 complete after 276.098 msecs
[ 5725.340865] PM: resume of drv:usb dev:3-2.2 complete after 274.796 msecs
[ 5725.340891] PM: resume of drv:usbhid dev:3-2.2:1.0 complete after 274.762 msecs
[ 5725.340910] PM: resume of drv: dev:ep_00 complete after 274.686 msecs
[ 5725.340928] PM: resume of drv: dev:ep_81 complete after 274.747 msecs
[ 5725.340955] PM: resume of drv: dev:ep_00 complete after 275.875 msecs
[ 5725.340984] PM: resume of drv: dev:ep_00 complete after 277.570 msecs
[ 5725.341011] PM: resume of drv: dev:ep_00 complete after 277.649 msecs
[ 5725.341039] PM: resume of drv:hub dev:1-0:1.0 complete after 277.703 msecs
[ 5725.341063] PM: resume of drv: dev:ep_81 complete after 277.715 msecs
[ 5725.410845] ata5: SATA link down (SStatus 0 SControl 300)
[ 5725.780082] usb 5-2: reset low speed USB device using uhci_hcd and address 2
[ 5726.020549] ata1.00: configured for UDMA/33
[ 5726.093891] PM: resume of drv:usb dev:5-2 complete after 1027.368 msecs
[ 5726.093927] PM: resume of drv:usbhid dev:5-2:1.0 complete after 1027.344 msecs
[ 5726.093948] PM: resume of drv: dev:ep_81 complete after 1027.313 msecs
[ 5726.093982] PM: resume of drv: dev:ep_00 complete after 1027.291 msecs
[ 5726.620097] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 5726.622126] ata3.00: configured for UDMA/100
[ 5726.644171] PM: resume of drv:sd dev:2:0:0:0 complete after 1579.025 msecs
[ 5726.644207] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 1578.932 msecs
[ 5726.644225] PM: resume of drv:scsi_disk dev:2:0:0:0 complete after 1374.097 msecs
[ 5727.491564] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 2429.946 msecs
[ 5727.491631] PM: resume of drv:i2c dev:i2c-0 complete after 841.341 msecs
[ 5727.491771] firewire_core: rediscovered device fw0
[ 5727.492158] PM: resume of devices complete after 2431.729 msecs
[ 5727.493152] PM: resume devices took 2.440 seconds
[ 5727.493323] PM: Finishing wakeup.
[ 5727.493327] Restarting tasks ... 
[ 5727.494990] usb 3-2: USB disconnect, address 2
[ 5727.494997] usb 3-2.1: USB disconnect, address 3
[ 5727.585166] done.
[ 5727.614254] video LNXVIDEO:00: Restoring backlight state
[ 5727.744071] usb 3-2.2: USB disconnect, address 4
[ 5728.712907] iwl3945 0000:0c:00.0: Error setting Tx power (-5).
[ 5728.716618] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5728.729265] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5728.890504] usb 3-2.3: USB disconnect, address 5
[ 5729.290928] usb 2-6: USB disconnect, address 2
[ 5729.670098] usb 2-6: new high speed USB device using ehci_hcd and address 5
[ 5730.078042] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[ 5730.078558] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[ 5730.079433] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input14
[ 5730.350115] usb 3-2: new full speed USB device using uhci_hcd and address 6
[ 5730.538588] hub 3-2:1.0: USB hub found
[ 5730.540431] hub 3-2:1.0: 3 ports detected
[ 5730.890121] usb 2-1: new high speed USB device using ehci_hcd and address 6
[ 5731.060190] scsi6 : usb-storage 2-1:1.0
[ 5731.151471] usb 3-2.1: new full speed USB device using uhci_hcd and address 7
[ 5731.380495] usb 3-2.2: new full speed USB device using uhci_hcd and address 8
[ 5731.441744] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 5731.560441] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.2/3-2.2:1.0/input/input15
[ 5731.560835] generic-usb 0003:0A5C:4502.0004: input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2/input0
[ 5731.640481] usb 3-2.3: new full speed USB device using uhci_hcd and address 9
[ 5731.786889] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input16
[ 5731.787430] generic-usb 0003:0A5C:4503.0005: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0
[ 5732.107429] scsi 6:0:0:0: Direct-Access              USB Flash Memory PMAP PQ: 0 ANSI: 0 CCS
[ 5732.109211] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 5732.538600] sd 6:0:0:0: [sdb] 31375360 512-byte logical blocks: (16.0 GB/14.9 GiB)
[ 5732.539208] sd 6:0:0:0: [sdb] Write Protect is off
[ 5732.539226] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 5732.539233] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 5732.542963] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 5732.573840]  sdb: sdb1
[ 5732.579208] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 5732.579224] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 5736.424539] wlan0: authenticate with b4:74:9f:2a:91:d5 (try 1)
[ 5736.426659] wlan0: authenticated
[ 5736.426732] wlan0: associate with b4:74:9f:2a:91:d5 (try 1)
[ 5736.435111] wlan0: RX AssocResp from b4:74:9f:2a:91:d5 (capab=0x411 status=0 aid=2)
[ 5736.435125] wlan0: associated
[ 5736.438902] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5746.490056] wlan0: no IPv6 routers present
[ 6530.810856] unity-2d-panel[1465]: segfault at 47a0dc ip 00007fb5571c4d38 sp 00007ffffe3ddf20 error 4 in libgobject-2.0.so.0.2800.6[7fb5571a5000+4e000]
[ 7789.006444] CE: hpet increased min_delta_ns to 45253 nsec
```

---

### Post by chimericidol on 2011-08-12
I have tried previous kernel but it didn't work. And actually I just confirmed that it was hardware fault because I fixed it by... blowing into the CPU fan :) I just thought that I will give it a shot just to see if there is something stuck... and LUCKILY it solved the problem. Now all the programs, indicators and cpufreq-info gives proper outputs! So for now the problem is solved. I assume I will have to take a closer look later on, but for now I am happy :DD

Thanks again guys for your fast feedback!

How can I change the title to SOLVED?

---

### Post by sbraz on 2011-08-12
> **chimericidol said:**
> How can I change the title to SOLVED?
i think it's the "Thread Tools" button at the top. :)

---

### Post by .... on 2011-08-12
There is a thread tools menu at the top of the page to mark it solved. I guess your system detected 0 RPM for the fan and applied a speed limit. Some laptops won't even turn on without a running fan. I learned something new. I'm glad it's fixed.

---

