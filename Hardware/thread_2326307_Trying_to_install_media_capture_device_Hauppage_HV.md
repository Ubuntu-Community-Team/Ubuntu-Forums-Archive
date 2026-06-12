---
title: "Trying to install media capture device Hauppage HVR-1800"
date: 2016-05-30
forum: Hardware
---

### Post by deamon_knight on 2016-05-30
I'm having some problems with a new install of Lubuntu 16.04. I have the following hardware, 
AMD Athlon 7850
[Gigabyte GA-MA78GM-US2H]("http://www.gigabyte.com/products/product-page.aspx?pid=2995#ov")
4GB RAM
a 500GB HDD, a USB 3.0 Card, and a Hauppauge 1800 PCI tv capture card.

I'm looking into setting up a Linux based Media Center setup and using this a testbed, ultimately a TV Headend backend and Kodi as a front end. I'm trying to get the radio functionality to work on this HVR-1800 card. It looks like there is missing firmware? Here is the output of my dmesg tail:

```

[   18.083650] Adding 3665916k swap on /dev/sda5.  Priority:-1 extents:1 across:3665916k FS
[   18.095978] tda829x 6-0042: type set to tda8295+18271
[   20.334523] cx23885[0]: registered device video0 [v4l2]
[   20.334563] cx23885[0]: registered device vbi0
[   20.334682] cx23885[0]: registered ALSA audio device
[   20.334751] cx23885[0]: registered device video1 [mpeg]
[   20.334766] Firmware and/or mailbox pointer not initialized or corrupted, signature = 0xdbf79db9, cmd = PING_FW
[   20.334872] cx23885 0000:02:00.0: Direct firmware load for v4l-cx23885-enc.fw failed with error -2
[   20.334874] ERROR: Hotplug firmware request failed (v4l-cx23885-enc.fw).
[   20.334875] Please fix your hotplug setup, the board will not work without firmware loaded!
[   20.334877] cx23885_initialize_codec() f/w load failed
[   20.334879] cx23885_dvb_register() allocating 1 frontend(s)
[   20.334882] cx23885[0]: cx23885 based dvb card
[   21.004283] MT2131: successfully identified at address 0x61
[   21.005926] DVB: registering new adapter (cx23885[0])
[   21.005933] cx23885 0000:02:00.0: DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   21.006363] cx23885_dev_checkrevision() Hardware revision = 0xb1
[   21.006372] cx23885[0]/0: found at 0000:02:00.0, rev: 15, irq: 18, latency: 0, mmio: 0xfd400000
[   23.314928] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   23.325026] r8169 0000:04:00.0 enp4s0: link down
[   23.325028] r8169 0000:04:00.0 enp4s0: link down
[   23.325078] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   25.831410] r8169 0000:04:00.0 enp4s0: link up
[   25.831424] IPv6: ADDRCONF(NETDEV_CHANGE): enp4s0: link becomes ready
[  908.859783] CE: hpet increased min_delta_ns to 20115 nsec


```

I think that "[   20.334872] cx23885 0000:02:00.0: Direct firmware load for v4l-cx23885-enc.fw failed with error -2" is the key message.

Looking at my /lib/firmware , I did not see a v4l-cx23885-enc.fw file. Following the [linuxTV instructions]("https://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800") at for extracting the v4l-cx23885-enc.fw and moving the file. However, after modprobing I'm still getting the same error in dmesg. Any suggestions on how to get the analog portions of this card to work?

---

### Post by MartyBuntu on 2016-05-30
What is the card hooked up to?

I have the same card, running on Ubuntu Studio 14.04, using Kaffeine for my OTA TV watching. Works fine.

---

### Post by deamon_knight on 2016-05-31
OTA ATSC Digital Broadcasts work with Kafffine. I'm trying to get FM radio working in Gnomeradio.

---

### Post by MartyBuntu on 2016-05-31
You have an antenna attached?

---

### Post by deamon_knight on 2016-06-02
Looks like I may have need a cold reboot. I'm no longer seeing the firmware error. I also had a Hauppauge PVR-150 card previously installed. The radio on that card works. It seems like the installation of the PVR-150 creates a device /dev/radio0 , and gnomeradio reads from that, I think that /dev/radio0 is part of the Video4Linux framework. With the PRV-150 removed and the HVR-1800 installed, I don't see a /dev/radio device. I thought I was on to something when I added the v4l-cx23885-enc.fw, but now I'm stumped. I do have an antenna installed.

Here is the current "dmesg tail"

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.4.0-22-generic (buildd@lgw01-41) (gcc version 5.3.1 20160413 (Ubuntu 5.3.1-14ubuntu2) ) #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 (Ubuntu 4.4.0-22.40-generic 4.4.8)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-22-generic root=UUID=37d1154b-62ff-41da-9e36-6867179b54d3 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] tseg: 00afe00000
[    0.000000] x86/fpu: Legacy x87 FPU detected.
[    0.000000] x86/fpu: Using 'lazy' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x00000000000983ff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000098400-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000afd80fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000afde0000-0x00000000afde2fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000afde3000-0x00000000afdeffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000afdf0000-0x00000000afdfffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000012fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. GA-MA78GM-US2H/GA-MA78GM-US2H, BIOS F9d 08/04/2010
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFE0000000 write-back
[    0.000000]   2 base 0000A0000000 mask FFFFF0000000 write-back
[    0.000000]   3 base 0000AFE00000 mask FFFFFFE00000 uncachable
[    0.000000]   4 base 000100000000 mask FFFFE0000000 write-back
[    0.000000]   5 base 000120000000 mask FFFFF0000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 256MB, type WB
[    0.000000] reg 3, base: 2814MB, range: 2MB, type UC
[    0.000000] reg 4, base: 4GB, range: 512MB, type WB
[    0.000000] reg 5, base: 4608MB, range: 256MB, type WB
[    0.000000] total RAM covered: 2814M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 4M 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 512MB, type WB
[    0.000000] reg 2, base: 2560MB, range: 256MB, type WB
[    0.000000] reg 3, base: 2814MB, range: 2MB, type UC
[    0.000000] e820: update [mem 0xafe00000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xafd81 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f57f0-0x000f57ff] mapped at [ffff8800000f57f0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000092000] 92000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] BRK [0x021ff000, 0x021fffff] PGTABLE
[    0.000000] BRK [0x02200000, 0x02200fff] PGTABLE
[    0.000000] BRK [0x02201000, 0x02201fff] PGTABLE
[    0.000000] BRK [0x02202000, 0x02202fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x33b6e000-0x35daefff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F7170 000014 (v00 GBT   )
[    0.000000] ACPI: RSDT 0x00000000AFDE3000 000038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 0x00000000AFDE3040 000074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 0x00000000AFDE30C0 006B58 (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 0x00000000AFDE0000 000040
[    0.000000] ACPI: SSDT 0x00000000AFDE9D00 0007BA (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 0x00000000AFDEA4C0 000038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 0x00000000AFDEA500 00003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: APIC 0x00000000AFDE9C40 0000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000012fffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x12fff9000-0x12fffdfff]
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000012fffffff]
[    0.000000]   Device   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x0000000000097fff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000afd80fff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000012fffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000012fffffff]
[    0.000000] On node 0 totalpages: 916760
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3991 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11191 pages used for memmap
[    0.000000]   DMA32 zone: 716161 pages, LIFO batch:31
[    0.000000]   Normal zone: 3072 pages used for memmap
[    0.000000]   Normal zone: 196608 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00098000-0x00098fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00099000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xafd81000-0xafddffff]
[    0.000000] PM: Registered nosave memory: [mem 0xafde0000-0xafde2fff]
[    0.000000] PM: Registered nosave memory: [mem 0xafde3000-0xafdeffff]
[    0.000000] PM: Registered nosave memory: [mem 0xafdf0000-0xafdfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xafe00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xffffffff]
[    0.000000] e820: [mem 0xafe00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88012fc00000 s98008 r8192 d28968 u262144
[    0.000000] pcpu-alloc: s98008 r8192 d28968 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 902412
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-22-generic root=UUID=37d1154b-62ff-41da-9e36-6867179b54d3 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] AGP: Node 0: aperture [bus addr 0x6a30000000-0x6a31ffffff] (32MB)
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] AGP: Your BIOS doesn't leave an aperture memory hole
[    0.000000] AGP: Please enable the IOMMU option in the BIOS setup
[    0.000000] AGP: This costs you 64MB of RAM
[    0.000000] AGP: Mapping aperture over RAM [mem 0xa4000000-0xa7ffffff] (65536KB)
[    0.000000] PM: Registered nosave memory: [mem 0xa4000000-0xa7ffffff]
[    0.000000] Memory: 3423164K/3667040K available (8359K kernel code, 1278K rwdata, 3920K rodata, 1480K init, 1292K bss, 243876K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	Build-time adjustment of leaf fanout to 64.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:488 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484873504 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2812.622 MHz processor
[    0.000028] Calibrating delay loop (skipped), value calculated using timer frequency.. 5625.24 BogoMIPS (lpj=11250488)
[    0.000031] pid_max: default: 32768 minimum: 301
[    0.000039] ACPI: Core revision 20150930
[    0.003242] ACPI: 2 ACPI AML tables successfully acquired and loaded
[    0.003271] Security Framework initialized
[    0.003274] Yama: becoming mindful.
[    0.003294] AppArmor: AppArmor initialized
[    0.003572] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.005266] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.006091] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.006097] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.006403] Initializing cgroup subsys io
[    0.006409] Initializing cgroup subsys memory
[    0.006418] Initializing cgroup subsys devices
[    0.006422] Initializing cgroup subsys freezer
[    0.006426] Initializing cgroup subsys net_cls
[    0.006428] Initializing cgroup subsys perf_event
[    0.006431] Initializing cgroup subsys net_prio
[    0.006435] Initializing cgroup subsys hugetlb
[    0.006439] Initializing cgroup subsys pids
[    0.006463] CPU: Physical Processor ID: 0
[    0.006464] CPU: Processor Core ID: 0
[    0.006466] mce: CPU supports 6 MCE banks
[    0.006473] LVT offset 0 assigned for vector 0xf9
[    0.006477] process: using AMD E400 aware idle routine
[    0.006480] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
[    0.006481] Last level dTLB entries: 4KB 512, 2MB 128, 4MB 64, 1GB 0
[    0.006739] Freeing SMP alternatives memory: 28K (ffffffff820b3000 - ffffffff820ba000)
[    0.041936] ftrace: allocating 31906 entries in 125 pages
[    0.055217] smpboot: Max logical packages: 4
[    0.055221] smpboot: APIC(0) Converting physical 0 to logical package 0
[    0.055764] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.203386] smpboot: CPU0: AMD Athlon(tm) 7850 Dual-Core Processor (family: 0x10, model: 0x2, stepping: 0x3)
[    0.203405] Performance Events: AMD PMU driver.
[    0.203411] ... version:                0
[    0.203412] ... bit width:              48
[    0.203413] ... generic registers:      4
[    0.203414] ... value mask:             0000ffffffffffff
[    0.203415] ... max period:             00007fffffffffff
[    0.203416] ... fixed-purpose events:   0
[    0.203417] ... event mask:             000000000000000f
[    0.204211] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.204303] x86: Booting SMP configuration:
[    0.204304] .... node  #0, CPUs:      #1
[    0.206619] x86: Booted up 1 node, 2 CPUs
[    0.206621] smpboot: Total of 2 processors activated (11250.48 BogoMIPS)
[    0.206686] process: System has AMD C1E enabled
[    0.206703] process: Switch to broadcast mode on CPU1
[    0.207892] process: Switch to broadcast mode on CPU0
[    0.207991] devtmpfs: initialized
[    0.211327] evm: security.selinux
[    0.211329] evm: security.SMACK64
[    0.211330] evm: security.SMACK64EXEC
[    0.211330] evm: security.SMACK64TRANSMUTE
[    0.211331] evm: security.SMACK64MMAP
[    0.211332] evm: security.ima
[    0.211333] evm: security.capability
[    0.211427] PM: Registering ACPI NVS region [mem 0xafde0000-0xafde2fff] (12288 bytes)
[    0.211517] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.211607] pinctrl core: initialized pinctrl subsystem
[    0.211741] RTC time: 12:21:19, date: 06/02/16
[    0.211872] NET: Registered protocol family 16
[    0.226838] cpuidle: using governor ladder
[    0.238838] cpuidle: using governor menu
[    0.238847] PCCT header not found.
[    0.238855] node 0 link 0: io port [a000, ffff]
[    0.238857] TOM: 00000000d0000000 aka 3328M
[    0.238860] Fam 10h mmconf [mem 0xe0000000-0xe00fffff]
[    0.238862] node 0 link 0: mmio [a0000, bffff]
[    0.238865] node 0 link 0: mmio [d0000000, dfffffff]
[    0.238867] node 0 link 0: mmio [f0000000, fe02ffff]
[    0.238868] node 0 link 0: mmio [e0000000, e05fffff] ==> [e0100000, e05fffff]
[    0.238871] TOM2: 0000000130000000 aka 4864M
[    0.238872] bus: [bus 00-05] on node 0 link 0
[    0.238874] bus: 00 [io  0x0000-0xffff]
[    0.238875] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.238877] bus: 00 [mem 0xd0000000-0xdfffffff]
[    0.238878] bus: 00 [mem 0xe0600000-0xffffffff]
[    0.238879] bus: 00 [mem 0xe0100000-0xe05fffff]
[    0.238880] bus: 00 [mem 0x130000000-0xfcffffffff]
[    0.238973] ACPI: bus type PCI registered
[    0.238976] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.239067] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.239070] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.239086] PCI: Using configuration type 1 for base access
[    0.251328] ACPI: Added _OSI(Module Device)
[    0.251331] ACPI: Added _OSI(Processor Device)
[    0.251333] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.251334] ACPI: Added _OSI(Processor Aggregator Device)
[    0.255040] ACPI: Interpreter enabled
[    0.255050] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150930/hwxface-580)
[    0.255054] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150930/hwxface-580)
[    0.255066] ACPI: (supports S0 S3 S4 S5)
[    0.255067] ACPI: Using IOAPIC for interrupt routing
[    0.255127] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.259339] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.259345] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.259350] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.259570] PCI host bridge to bus 0000:00
[    0.259573] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.259575] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.259577] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.259579] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff window]
[    0.259581] pci_bus 0000:00: root bus resource [mem 0xcff00000-0xfebfffff window]
[    0.259583] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.259592] pci 0000:00:00.0: [1022:9600] type 00 class 0x060000
[    0.259609] pci 0000:00:00.0: [Firmware Bug]: reg 0x1c: invalid BAR (can't size)
[    0.259696] pci 0000:00:01.0: [1022:9602] type 01 class 0x060400
[    0.259784] pci 0000:00:02.0: [1022:9603] type 01 class 0x060400
[    0.259819] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.259861] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.259898] pci 0000:00:04.0: [1022:9604] type 01 class 0x060400
[    0.259930] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.259971] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.260012] pci 0000:00:0a.0: [1022:9609] type 01 class 0x060400
[    0.260044] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.260084] pci 0000:00:0a.0: System wakeup disabled by ACPI
[    0.260128] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
[    0.260154] pci 0000:00:11.0: reg 0x10: [io  0xff00-0xff07]
[    0.260163] pci 0000:00:11.0: reg 0x14: [io  0xfe00-0xfe03]
[    0.260172] pci 0000:00:11.0: reg 0x18: [io  0xfd00-0xfd07]
[    0.260181] pci 0000:00:11.0: reg 0x1c: [io  0xfc00-0xfc03]
[    0.260190] pci 0000:00:11.0: reg 0x20: [io  0xfb00-0xfb0f]
[    0.260200] pci 0000:00:11.0: reg 0x24: [mem 0xfe02f000-0xfe02f3ff]
[    0.260296] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.260311] pci 0000:00:12.0: reg 0x10: [mem 0xfe02e000-0xfe02efff]
[    0.260402] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.260438] pci 0000:00:12.1: [1002:4398] type 00 class 0x0c0310
[    0.260453] pci 0000:00:12.1: reg 0x10: [mem 0xfe02d000-0xfe02dfff]
[    0.260543] pci 0000:00:12.1: System wakeup disabled by ACPI
[    0.260581] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.260606] pci 0000:00:12.2: reg 0x10: [mem 0xfe02c000-0xfe02c0ff]
[    0.260674] pci 0000:00:12.2: supports D1 D2
[    0.260676] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.260718] pci 0000:00:12.2: System wakeup disabled by ACPI
[    0.260759] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.260774] pci 0000:00:13.0: reg 0x10: [mem 0xfe02b000-0xfe02bfff]
[    0.260864] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.260900] pci 0000:00:13.1: [1002:4398] type 00 class 0x0c0310
[    0.260915] pci 0000:00:13.1: reg 0x10: [mem 0xfe02a000-0xfe02afff]
[    0.261005] pci 0000:00:13.1: System wakeup disabled by ACPI
[    0.261044] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.261069] pci 0000:00:13.2: reg 0x10: [mem 0xfe029000-0xfe0290ff]
[    0.261137] pci 0000:00:13.2: supports D1 D2
[    0.261138] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.261182] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.261226] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.261374] pci 0000:00:14.1: [1002:439c] type 00 class 0x01018a
[    0.261397] pci 0000:00:14.1: reg 0x10: [io  0x0000-0x0007]
[    0.261406] pci 0000:00:14.1: reg 0x14: [io  0x0000-0x0003]
[    0.261415] pci 0000:00:14.1: reg 0x18: [io  0x0000-0x0007]
[    0.261424] pci 0000:00:14.1: reg 0x1c: [io  0x0000-0x0003]
[    0.261433] pci 0000:00:14.1: reg 0x20: [io  0xfa00-0xfa0f]
[    0.261452] pci 0000:00:14.1: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.261454] pci 0000:00:14.1: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.261456] pci 0000:00:14.1: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.261457] pci 0000:00:14.1: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.261540] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.261566] pci 0000:00:14.2: reg 0x10: [mem 0xfe024000-0xfe027fff 64bit]
[    0.261624] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.261666] pci 0000:00:14.2: System wakeup disabled by ACPI
[    0.261701] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.261832] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.261904] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.261939] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.261954] pci 0000:00:14.5: reg 0x10: [mem 0xfe028000-0xfe028fff]
[    0.262044] pci 0000:00:14.5: System wakeup disabled by ACPI
[    0.262082] pci 0000:00:18.0: [1022:1200] type 00 class 0x060000
[    0.262151] pci 0000:00:18.1: [1022:1201] type 00 class 0x060000
[    0.262217] pci 0000:00:18.2: [1022:1202] type 00 class 0x060000
[    0.262283] pci 0000:00:18.3: [1022:1203] type 00 class 0x060000
[    0.262349] pci 0000:00:18.4: [1022:1204] type 00 class 0x060000
[    0.262454] pci 0000:01:05.0: [1002:9610] type 00 class 0x030000
[    0.262465] pci 0000:01:05.0: reg 0x10: [mem 0xd0000000-0xdfffffff pref]
[    0.262469] pci 0000:01:05.0: reg 0x14: [io  0xce00-0xceff]
[    0.262474] pci 0000:01:05.0: reg 0x18: [mem 0xfdce0000-0xfdceffff]
[    0.262483] pci 0000:01:05.0: reg 0x24: [mem 0xfdb00000-0xfdbfffff]
[    0.262497] pci 0000:01:05.0: supports D1 D2
[    0.262530] pci 0000:01:05.1: [1002:960f] type 00 class 0x040300
[    0.262540] pci 0000:01:05.1: reg 0x10: [mem 0xfdcfc000-0xfdcfffff]
[    0.262566] pci 0000:01:05.1: supports D1 D2
[    0.262625] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.262628] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
[    0.262631] pci 0000:00:01.0:   bridge window [mem 0xfdb00000-0xfdcfffff]
[    0.262634] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.262681] pci 0000:02:00.0: [14f1:8880] type 00 class 0x040000
[    0.262749] pci 0000:02:00.0: reg 0x10: [mem 0xfd400000-0xfd5fffff 64bit]
[    0.262892] pci 0000:02:00.0: supports D1 D2
[    0.262893] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[    0.262957] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.262967] pci 0000:00:02.0: PCI bridge to [bus 02]
[    0.262971] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
[    0.262973] pci 0000:00:02.0:   bridge window [mem 0xfd400000-0xfd5fffff]
[    0.262976] pci 0000:00:02.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.263022] pci 0000:03:00.0: [1912:0014] type 00 class 0x0c0330
[    0.263068] pci 0000:03:00.0: reg 0x10: [mem 0xfd7fe000-0xfd7fffff 64bit]
[    0.263174] pci 0000:03:00.0: PME# supported from D0 D3hot
[    0.270850] pci 0000:00:04.0: PCI bridge to [bus 03]
[    0.270853] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.270855] pci 0000:00:04.0:   bridge window [mem 0xfd700000-0xfd7fffff]
[    0.270859] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.270899] pci 0000:04:00.0: [10ec:8168] type 00 class 0x020000
[    0.270927] pci 0000:04:00.0: reg 0x10: [io  0xde00-0xdeff]
[    0.270946] pci 0000:04:00.0: reg 0x18: [mem 0xfddff000-0xfddfffff 64bit pref]
[    0.270959] pci 0000:04:00.0: reg 0x20: [mem 0xfdde0000-0xfddeffff 64bit pref]
[    0.270968] pci 0000:04:00.0: reg 0x30: [mem 0x00000000-0x0000ffff pref]
[    0.271011] pci 0000:04:00.0: supports D1 D2
[    0.271012] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.278847] pci 0000:00:0a.0: PCI bridge to [bus 04]
[    0.278851] pci 0000:00:0a.0:   bridge window [io  0xd000-0xdfff]
[    0.278853] pci 0000:00:0a.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.278856] pci 0000:00:0a.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
[    0.278913] pci 0000:05:0e.0: [104c:8024] type 00 class 0x0c0010
[    0.278943] pci 0000:05:0e.0: reg 0x10: [mem 0xfd9ff000-0xfd9ff7ff]
[    0.278955] pci 0000:05:0e.0: reg 0x14: [mem 0xfd9f8000-0xfd9fbfff]
[    0.279037] pci 0000:05:0e.0: supports D1 D2
[    0.279038] pci 0000:05:0e.0: PME# supported from D0 D1 D2 D3hot
[    0.279102] pci 0000:00:14.4: PCI bridge to [bus 05] (subtractive decode)
[    0.279106] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
[    0.279110] pci 0000:00:14.4:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.279113] pci 0000:00:14.4:   bridge window [mem 0xfd800000-0xfd8fffff pref]
[    0.279116] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.279117] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.279119] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.279121] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff window] (subtractive decode)
[    0.279123] pci 0000:00:14.4:   bridge window [mem 0xcff00000-0xfebfffff window] (subtractive decode)
[    0.279346] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.279391] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.279433] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.279474] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.279519] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.279560] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.279600] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.279640] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.280320] vgaarb: setting as boot device: PCI:0000:01:05.0
[    0.280322] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.280325] vgaarb: loaded
[    0.280326] vgaarb: bridge control possible 0000:01:05.0
[    0.280587] SCSI subsystem initialized
[    0.280648] libata version 3.00 loaded.
[    0.280673] ACPI: bus type USB registered
[    0.280691] usbcore: registered new interface driver usbfs
[    0.280701] usbcore: registered new interface driver hub
[    0.280717] usbcore: registered new device driver usb
[    0.280876] PCI: Using ACPI for IRQ routing
[    0.289121] PCI: pci_cache_line_size set to 64 bytes
[    0.289183] e820: reserve RAM buffer [mem 0x00098400-0x0009ffff]
[    0.289185] e820: reserve RAM buffer [mem 0xafd81000-0xafffffff]
[    0.289311] NetLabel: Initializing
[    0.289312] NetLabel:  domain hash size = 128
[    0.289313] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.289325] NetLabel:  unlabeled traffic allowed by default
[    0.289403] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.289407] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.291454] clocksource: Switched to clocksource hpet
[    0.299319] AppArmor: AppArmor Filesystem Enabled
[    0.299418] pnp: PnP ACPI init
[    0.299579] system 00:00: [io  0x04d0-0x04d1] has been reserved
[    0.299582] system 00:00: [io  0x0220-0x0225] has been reserved
[    0.299584] system 00:00: [io  0x0290-0x0294] has been reserved
[    0.299589] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.299843] pnp 00:01: disabling [mem 0x00000000-0x00000fff window] because it overlaps 0000:04:00.0 BAR 6 [mem 0x00000000-0x0000ffff pref]
[    0.299869] system 00:01: [io  0x4100-0x411f] has been reserved
[    0.299872] system 00:01: [io  0x0228-0x022f] has been reserved
[    0.299874] system 00:01: [io  0x0238-0x023f] has been reserved
[    0.299876] system 00:01: [io  0x040b] has been reserved
[    0.299877] system 00:01: [io  0x04d6] has been reserved
[    0.299879] system 00:01: [io  0x0c00-0x0c01] has been reserved
[    0.299881] system 00:01: [io  0x0c14] has been reserved
[    0.299883] system 00:01: [io  0x0c50-0x0c52] has been reserved
[    0.299885] system 00:01: [io  0x0c6c-0x0c6d] has been reserved
[    0.299887] system 00:01: [io  0x0c6f] has been reserved
[    0.299889] system 00:01: [io  0x0cd0-0x0cd1] has been reserved
[    0.299891] system 00:01: [io  0x0cd2-0x0cd3] has been reserved
[    0.299892] system 00:01: [io  0x0cd4-0x0cdf] has been reserved
[    0.299895] system 00:01: [io  0x4000-0x40fe] could not be reserved
[    0.299897] system 00:01: [io  0x4210-0x4217] has been reserved
[    0.299899] system 00:01: [io  0x0b00-0x0b0f] has been reserved
[    0.299901] system 00:01: [io  0x0b10-0x0b1f] has been reserved
[    0.299902] system 00:01: [io  0x0b20-0x0b3f] has been reserved
[    0.299905] system 00:01: [mem 0xfee00400-0xfee00fff window] has been reserved
[    0.299908] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.300050] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.300414] system 00:03: [mem 0xe0000000-0xefffffff] has been reserved
[    0.300416] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.300610] system 00:04: [mem 0x000d4400-0x000d7fff] has been reserved
[    0.300612] system 00:04: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.300614] system 00:04: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.300616] system 00:04: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.300618] system 00:04: [mem 0xafde0000-0xafdeffff] could not be reserved
[    0.300620] system 00:04: [mem 0xffff0000-0xffffffff] has been reserved
[    0.300622] system 00:04: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.300624] system 00:04: [mem 0x00100000-0xafddffff] could not be reserved
[    0.300626] system 00:04: [mem 0xafdf0000-0xafdfffff] has been reserved
[    0.300628] system 00:04: [mem 0xafe00000-0xafefffff] could not be reserved
[    0.300630] system 00:04: [mem 0xaff00000-0xcfefffff] could not be reserved
[    0.300632] system 00:04: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.300634] system 00:04: [mem 0xfee00000-0xfee00fff] could not be reserved
[    0.300636] system 00:04: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.300638] system 00:04: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.300655] pnp: PnP ACPI: found 5 devices
[    0.308242] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.308273] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.308276] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
[    0.308280] pci 0000:00:01.0:   bridge window [mem 0xfdb00000-0xfdcfffff]
[    0.308282] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.308286] pci 0000:00:02.0: PCI bridge to [bus 02]
[    0.308288] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
[    0.308290] pci 0000:00:02.0:   bridge window [mem 0xfd400000-0xfd5fffff]
[    0.308293] pci 0000:00:02.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.308296] pci 0000:00:04.0: PCI bridge to [bus 03]
[    0.308298] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    0.308301] pci 0000:00:04.0:   bridge window [mem 0xfd700000-0xfd7fffff]
[    0.308303] pci 0000:00:04.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.308310] pci 0000:04:00.0: BAR 6: assigned [mem 0xfde00000-0xfde0ffff pref]
[    0.308313] pci 0000:00:0a.0: PCI bridge to [bus 04]
[    0.308315] pci 0000:00:0a.0:   bridge window [io  0xd000-0xdfff]
[    0.308317] pci 0000:00:0a.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.308320] pci 0000:00:0a.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
[    0.308324] pci 0000:00:14.4: PCI bridge to [bus 05]
[    0.308327] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
[    0.308331] pci 0000:00:14.4:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.308335] pci 0000:00:14.4:   bridge window [mem 0xfd800000-0xfd8fffff pref]
[    0.308343] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.308345] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.308347] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.308348] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff window]
[    0.308350] pci_bus 0000:00: resource 8 [mem 0xcff00000-0xfebfffff window]
[    0.308352] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.308354] pci_bus 0000:01: resource 1 [mem 0xfdb00000-0xfdcfffff]
[    0.308356] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.308358] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
[    0.308359] pci_bus 0000:02: resource 1 [mem 0xfd400000-0xfd5fffff]
[    0.308361] pci_bus 0000:02: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.308363] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.308365] pci_bus 0000:03: resource 1 [mem 0xfd700000-0xfd7fffff]
[    0.308366] pci_bus 0000:03: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.308368] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    0.308370] pci_bus 0000:04: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.308372] pci_bus 0000:04: resource 2 [mem 0xfdd00000-0xfddfffff 64bit pref]
[    0.308374] pci_bus 0000:05: resource 0 [io  0xa000-0xafff]
[    0.308375] pci_bus 0000:05: resource 1 [mem 0xfd900000-0xfd9fffff]
[    0.308377] pci_bus 0000:05: resource 2 [mem 0xfd800000-0xfd8fffff pref]
[    0.308379] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7 window]
[    0.308381] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff window]
[    0.308383] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.308384] pci_bus 0000:05: resource 7 [mem 0x000c0000-0x000dffff window]
[    0.308386] pci_bus 0000:05: resource 8 [mem 0xcff00000-0xfebfffff window]
[    0.308427] NET: Registered protocol family 2
[    0.308632] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.308764] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.308974] TCP: Hash tables configured (established 32768 bind 32768)
[    0.309035] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.309068] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.309150] NET: Registered protocol family 1
[    0.309163] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.679720] pci 0000:01:05.0: Video device with shadowed ROM
[    0.679869] PCI: CLS 64 bytes, default 64
[    0.679937] Trying to unpack rootfs image as initramfs...
[    1.239490] Freeing initrd memory: 35076K (ffff880033b6e000 - ffff880035daf000)
[    1.239795] PCI-DMA: Disabling AGP.
[    1.239878] PCI-DMA: aperture base @ a4000000 size 65536 KB
[    1.239879] PCI-DMA: using GART IOMMU.
[    1.239882] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.243565] LVT offset 1 assigned for vector 0x400
[    1.243580] IBS: LVT offset 1 assigned
[    1.243600] perf: AMD IBS detected (0x00000007)
[    1.243723] Scanning for low memory corruption every 60 seconds
[    1.244133] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    1.244182] audit: initializing netlink subsys (disabled)
[    1.244202] audit: type=2000 audit(1464870080.116:1): initialized
[    1.244519] Initialise system trusted keyring
[    1.244688] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    1.244690] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.246231] zbud: loaded
[    1.246470] VFS: Disk quotas dquot_6.6.0
[    1.246508] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.247049] fuse init (API version 7.23)
[    1.247208] Key type big_key registered
[    1.247234] Allocating IMA MOK and blacklist keyrings.
[    1.248117] Key type asymmetric registered
[    1.248121] Asymmetric key parser 'x509' registered
[    1.248162] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    1.248217] io scheduler noop registered
[    1.248220] io scheduler deadline registered (default)
[    1.248252] io scheduler cfq registered
[    1.248783] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.248790] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.248823] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    1.248825] vesafb: scrolling: redraw
[    1.248827] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    1.248845] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90000800000, using 3072k, total 3072k
[    1.248959] Console: switching to colour frame buffer device 128x48
[    1.248976] fb0: VESA VGA frame buffer device
[    1.249070] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.249075] ACPI: Power Button [PWRB]
[    1.249117] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.249119] ACPI: Power Button [PWRF]
[    1.249147] ACPI: processor limited to max C-state 1
[    1.249294] GHES: HEST is not enabled!
[    1.249413] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.251338] Linux agpgart interface v0.103
[    1.254452] brd: module loaded
[    1.255914] loop: module loaded
[    1.256180] libphy: Fixed MDIO Bus: probed
[    1.256183] tun: Universal TUN/TAP device driver, 1.6
[    1.256184] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.256235] PPP generic driver version 2.4.2
[    1.256313] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.256318] ehci-pci: EHCI PCI platform driver
[    1.256467] QUIRK: Enable AMD PLL fix
[    1.256493] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.256500] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.256505] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.256507] ehci-pci 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.256519] ehci-pci 0000:00:12.2: debug port 1
[    1.256570] ehci-pci 0000:00:12.2: irq 17, io mem 0xfe02c000
[    1.267686] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.267759] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.267762] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.267763] usb usb1: Product: EHCI Host Controller
[    1.267765] usb usb1: Manufacturer: Linux 4.4.0-22-generic ehci_hcd
[    1.267767] usb usb1: SerialNumber: 0000:00:12.2
[    1.267918] hub 1-0:1.0: USB hub found
[    1.267924] hub 1-0:1.0: 6 ports detected
[    1.268264] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.268272] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.268277] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.268279] ehci-pci 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.268291] ehci-pci 0000:00:13.2: debug port 1
[    1.268344] ehci-pci 0000:00:13.2: irq 19, io mem 0xfe029000
[    1.283667] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.283712] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.283714] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.283716] usb usb2: Product: EHCI Host Controller
[    1.283717] usb usb2: Manufacturer: Linux 4.4.0-22-generic ehci_hcd
[    1.283719] usb usb2: SerialNumber: 0000:00:13.2
[    1.283833] hub 2-0:1.0: USB hub found
[    1.283839] hub 2-0:1.0: 6 ports detected
[    1.283994] ehci-platform: EHCI generic platform driver
[    1.284012] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.284016] ohci-pci: OHCI PCI platform driver
[    1.284141] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.284146] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.284179] ohci-pci 0000:00:12.0: irq 16, io mem 0xfe02e000
[    1.343704] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.343706] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.343708] usb usb3: Product: OHCI PCI host controller
[    1.343709] usb usb3: Manufacturer: Linux 4.4.0-22-generic ohci_hcd
[    1.343711] usb usb3: SerialNumber: 0000:00:12.0
[    1.343814] hub 3-0:1.0: USB hub found
[    1.343821] hub 3-0:1.0: 3 ports detected
[    1.344021] ohci-pci 0000:00:12.1: OHCI PCI host controller
[    1.344026] ohci-pci 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.344045] ohci-pci 0000:00:12.1: irq 16, io mem 0xfe02d000
[    1.403699] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.403701] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.403702] usb usb4: Product: OHCI PCI host controller
[    1.403704] usb usb4: Manufacturer: Linux 4.4.0-22-generic ohci_hcd
[    1.403706] usb usb4: SerialNumber: 0000:00:12.1
[    1.403812] hub 4-0:1.0: USB hub found
[    1.403820] hub 4-0:1.0: 3 ports detected
[    1.404017] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.404024] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.404057] ohci-pci 0000:00:13.0: irq 18, io mem 0xfe02b000
[    1.463704] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.463706] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.463707] usb usb5: Product: OHCI PCI host controller
[    1.463709] usb usb5: Manufacturer: Linux 4.4.0-22-generic ohci_hcd
[    1.463710] usb usb5: SerialNumber: 0000:00:13.0
[    1.463812] hub 5-0:1.0: USB hub found
[    1.463819] hub 5-0:1.0: 3 ports detected
[    1.464015] ohci-pci 0000:00:13.1: OHCI PCI host controller
[    1.464020] ohci-pci 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.464036] ohci-pci 0000:00:13.1: irq 18, io mem 0xfe02a000
[    1.523714] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.523716] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.523718] usb usb6: Product: OHCI PCI host controller
[    1.523720] usb usb6: Manufacturer: Linux 4.4.0-22-generic ohci_hcd
[    1.523721] usb usb6: SerialNumber: 0000:00:13.1
[    1.523829] hub 6-0:1.0: USB hub found
[    1.523837] hub 6-0:1.0: 3 ports detected
[    1.524041] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    1.524047] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.524067] ohci-pci 0000:00:14.5: irq 18, io mem 0xfe028000
[    1.583709] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.583711] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.583712] usb usb7: Product: OHCI PCI host controller
[    1.583714] usb usb7: Manufacturer: Linux 4.4.0-22-generic ohci_hcd
[    1.583715] usb usb7: SerialNumber: 0000:00:14.5
[    1.583829] hub 7-0:1.0: USB hub found
[    1.583837] hub 7-0:1.0: 2 ports detected
[    1.583930] ohci-platform: OHCI generic platform driver
[    1.583943] uhci_hcd: USB Universal Host Controller Interface driver
[    1.584031] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.584036] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 8
[    1.589413] xhci_hcd 0000:03:00.0: hcc params 0x014051c7 hci version 0x100 quirks 0x00000010
[    1.589528] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
[    1.589530] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.589532] usb usb8: Product: xHCI Host Controller
[    1.589533] usb usb8: Manufacturer: Linux 4.4.0-22-generic xhci-hcd
[    1.589535] usb usb8: SerialNumber: 0000:03:00.0
[    1.589646] hub 8-0:1.0: USB hub found
[    1.589656] hub 8-0:1.0: 4 ports detected
[    1.589771] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.589774] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 9
[    1.593025] usb usb9: We don't know the algorithms for LPM for this host, disabling LPM.
[    1.593041] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
[    1.593043] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.593044] usb usb9: Product: xHCI Host Controller
[    1.593046] usb usb9: Manufacturer: Linux 4.4.0-22-generic xhci-hcd
[    1.593047] usb usb9: SerialNumber: 0000:03:00.0
[    1.593149] hub 9-0:1.0: USB hub found
[    1.593158] hub 9-0:1.0: 4 ports detected
[    1.593307] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.593967] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.593971] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.594132] mousedev: PS/2 mouse device common for all mice
[    1.594298] rtc_cmos 00:02: RTC can wake from S4
[    1.594424] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.594460] rtc_cmos 00:02: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.594466] i2c /dev entries driver
[    1.594529] device-mapper: uevent: version 1.0.3
[    1.594611] device-mapper: ioctl: 4.34.0-ioctl (2015-10-28) initialised: dm-devel@redhat.com
[    1.594631] ledtrig-cpu: registered to indicate activity on CPUs
[    1.595091] NET: Registered protocol family 10
[    1.595345] NET: Registered protocol family 17
[    1.595357] Key type dns_resolver registered
[    1.595593] microcode: CPU0: patch_level=0x010000c9
[    1.595601] microcode: CPU1: patch_level=0x010000c9
[    1.595649] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.595852] registered taskstats version 1
[    1.595871] Loading compiled-in X.509 certificates
[    1.596907] Loaded X.509 cert 'Build time autogenerated kernel key: 10281ca0c0463cd0680138fff55319c9bd7d63b8'
[    1.596927] zswap: loaded using pool lzo/zbud
[    1.598971] Key type trusted registered
[    1.602527] Key type encrypted registered
[    1.602536] AppArmor: AppArmor sha1 policy hashing enabled
[    1.602540] ima: No TPM chip found, activating TPM-bypass!
[    1.602570] evm: HMAC attrs: 0x1
[    1.602893]   Magic number: 4:244:379
[    1.603014] rtc_cmos 00:02: setting system clock to 2016-06-02 12:21:21 UTC (1464870081)
[    1.603125] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.603187] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.603188] EDD information not available.
[    1.603238] PM: Hibernation image not present or could not be loaded.
[    1.605065] Freeing unused kernel memory: 1480K (ffffffff81f41000 - ffffffff820b3000)
[    1.605069] Write protecting the kernel read-only data: 14336k
[    1.606028] Freeing unused kernel memory: 1868K (ffff88000182d000 - ffff880001a00000)
[    1.606529] Freeing unused kernel memory: 176K (ffff880001dd4000 - ffff880001e00000)
[    1.617769] random: systemd-udevd urandom read with 7 bits of entropy available
[    1.655473] ahci 0000:00:11.0: version 3.0
[    1.661794] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    1.667151] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.667157] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.673907] scsi host0: ahci
[    1.674184] scsi host1: ahci
[    1.674559] scsi host2: ahci
[    1.674652] scsi host3: ahci
[    1.674837] scsi host4: ahci
[    1.674920] scsi host5: ahci
[    1.674970] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[    1.674973] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[    1.674976] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[    1.674979] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[    1.674981] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f300 irq 22
[    1.674984] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f380 irq 22
[    1.676465] wmi: Mapper loaded
[    1.681867] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.681882] r8169 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.682287] r8169 0000:04:00.0 eth0: RTL8168c/8111c at 0xffffc90000646000, 00:24:1d:2a:5e:e7, XID 1c4000c0 IRQ 30
[    1.682290] r8169 0000:04:00.0 eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[    1.685607] [drm] Initialized drm 1.1.0 20060810
[    1.692191] scsi host6: pata_atiixp
[    1.699622] scsi host7: pata_atiixp
[    1.699711] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    1.699714] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    1.720342] [drm] radeon kernel modesetting enabled.
[    1.722799] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[    1.722803] AMD IOMMUv2 functionality not available on this system
[    1.725901] CRAT table not found
[    1.725905] Finished initializing topology ret=0
[    1.725961] kfd kfd: Initialized module
[    1.726204] checking generic (d0000000 300000) vs hw (d0000000 10000000)
[    1.726206] fb: switching to radeondrmfb from VESA VGA
[    1.726242] Console: switching to colour dummy device 80x25
[    1.726588] [drm] initializing kernel modesetting (RS780 0x1002:0x9610 0x1458:0xD000).
[    1.726604] [drm] register mmio base: 0xFDCE0000
[    1.726605] [drm] register mmio size: 65536
[    1.726940] ATOM BIOS: B27722
[    1.726960] radeon 0000:01:05.0: VRAM: 512M 0x00000000C0000000 - 0x00000000DFFFFFFF (512M used)
[    1.726963] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[    1.726967] [drm] Detected VRAM RAM=512M, BAR=256M
[    1.726968] [drm] RAM width 32bits DDR
[    1.727036] [TTM] Zone  kernel: Available graphics memory: 1763872 kiB
[    1.727037] [TTM] Initializing pool allocator
[    1.727044] [TTM] Initializing DMA pool allocator
[    1.727066] [drm] radeon: 512M of VRAM memory ready
[    1.727067] [drm] radeon: 512M of GTT memory ready.
[    1.727081] [drm] Loading RS780 Microcode
[    1.727152] [drm] radeon: power management initialized
[    1.727234] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    1.739477] [drm] PCIE GART of 512M enabled (table at 0x00000000C0258000).
[    1.739516] radeon 0000:01:05.0: WB enabled
[    1.739519] radeon 0000:01:05.0: fence driver on ring 0 use gpu addr 0x00000000a0000c00 and cpu addr 0xffff8800aec10c00
[    1.740240] radeon 0000:01:05.0: fence driver on ring 5 use gpu addr 0x00000000c0056038 and cpu addr 0xffffc90000c16038
[    1.740267] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.740268] [drm] Driver supports precise vblank timestamp query.
[    1.740270] radeon 0000:01:05.0: radeon: MSI limited to 32-bit
[    1.740284] [drm] radeon: irq initialized.
[    1.755614] firewire_ohci 0000:05:0e.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x2
[    1.771391] [drm] ring test on 0 succeeded in 1 usecs
[    1.787566] usb 3-3: new low-speed USB device number 2 using ohci-pci
[    1.827063] r8169 0000:04:00.0 enp4s0: renamed from eth0
[    1.899587] usb 4-1: new full-speed USB device number 2 using ohci-pci
[    1.946032] [drm] ring test on 5 succeeded in 1 usecs
[    1.946037] [drm] UVD initialized successfully.
[    1.946157] [drm] ib test on ring 0 succeeded in 0 usecs
[    1.958786] usb 3-3: New USB device found, idVendor=1bcf, idProduct=0005
[    1.958789] usb 3-3: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    1.958792] usb 3-3: Product: USB Optical Mouse
[    1.966757] hidraw: raw HID events driver (C) Jiri Kosina
[    1.973939] usbcore: registered new interface driver usbhid
[    1.973942] usbhid: USB HID core driver
[    1.975741] input: USB Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/0003:1BCF:0005.0001/input/input5
[    1.975837] hid-generic 0003:1BCF:0005.0001: input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:12.0-3/input0
[    1.999601] ata3: SATA link down (SStatus 0 SControl 300)
[    2.007604] ata4: SATA link down (SStatus 0 SControl 300)
[    2.011600] ata5: SATA link down (SStatus 0 SControl 300)
[    2.011629] ata6: SATA link down (SStatus 0 SControl 300)
[    2.066648] usb 4-1: New USB device found, idVendor=058f, idProduct=9254
[    2.066650] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.066652] usb 4-1: Product: Generic USB Hub
[    2.066654] usb 4-1: Manufacturer: ALCOR
[    2.068680] hub 4-1:1.0: USB hub found
[    2.070646] hub 4-1:1.0: 4 ports detected
[    2.167747] ata2: softreset failed (device not ready)
[    2.167751] ata2: applying PMP SRST workaround and retrying
[    2.167769] ata1: softreset failed (device not ready)
[    2.167774] ata1: applying PMP SRST workaround and retrying
[    2.243738] tsc: Refined TSC clocksource calibration: 2812.809 MHz
[    2.243741] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x288b84f9b90, max_idle_ns: 440795272445 ns
[    2.267837] firewire_core 0000:05:0e.0: created device fw0: GUID 004250c80000241d, S400
[    2.339755] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.339784] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.340427] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S203N, SB01, max UDMA/100
[    2.341001] ata1.00: ATA-8: Hitachi HDS721050CLA362, JP2OA50E, max UDMA/133
[    2.341006] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.341672] ata2.00: configured for UDMA/100
[    2.342539] ata1.00: configured for UDMA/133
[    2.342777] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72105 A50E PQ: 0 ANSI: 5
[    2.343051] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/466 GiB)
[    2.343093] sd 0:0:0:0: [sda] Write Protect is off
[    2.343095] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.343113] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.343181] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.344172] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203N  SB01 PQ: 0 ANSI: 5
[    2.363739] usb 4-1.1: new full-speed USB device number 3 using ohci-pci
[    2.366635] sr 1:0:0:0: [sr0] scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.366638] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.366750] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.366803] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.387469]  sda: sda1 sda2 < sda5 >
[    2.387836] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.470819] usb 4-1.1: New USB device found, idVendor=2222, idProduct=0013
[    2.470824] usb 4-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.470827] usb 4-1.1: Product: Macally iKeySlim
[    2.470828] usb 4-1.1: Manufacturer: Macally Peripherals 
[    2.480072] input: Macally Peripherals  Macally iKeySlim as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1.1/4-1.1:1.0/0003:2222:0013.0002/input/input6
[    2.535921] hid-generic 0003:2222:0013.0002: input,hidraw1: USB HID v1.10 Keyboard [Macally Peripherals  Macally iKeySlim] on usb-0000:00:12.1-1.1/input0
[    2.540045] input: Macally Peripherals  Macally iKeySlim as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1.1/4-1.1:1.1/0003:2222:0013.0003/input/input7
[    2.591784] [drm] ib test on ring 5 succeeded
[    2.592313] [drm] Radeon Display Connectors
[    2.592315] [drm] Connector 0:
[    2.592316] [drm]   VGA-1
[    2.592318] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    2.592319] [drm]   Encoders:
[    2.592320] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.592321] [drm] Connector 1:
[    2.592322] [drm]   DVI-D-1
[    2.592323] [drm]   HPD1
[    2.592324] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    2.592325] [drm]   Encoders:
[    2.592326] [drm]     DFP1: INTERNAL_KLDSCP_LVTMA
[    2.622339] hid-generic 0003:2222:0013.0003: input,hidraw2: USB HID v1.10 Mouse [Macally Peripherals  Macally iKeySlim] on usb-0000:00:12.1-1.1/input1
[    2.624794] [drm] fb mappable at 0xD0359000
[    2.624797] [drm] vram apper at 0xD0000000
[    2.624799] [drm] size 3145728
[    2.624800] [drm] fb depth is 24
[    2.624800] [drm]    pitch is 4096
[    2.624883] fbcon: radeondrmfb (fb0) is primary device
[    2.624961] Console: switching to colour frame buffer device 128x48
[    2.624979] radeon 0000:01:05.0: fb0: radeondrmfb frame buffer device
[    2.639784] [drm] Initialized radeon 2.43.0 20080528 for 0000:01:05.0 on minor 0
[    3.243915] clocksource: Switched to clocksource tsc
[    7.064338] floppy0: no floppy controllers found
[    7.428192] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    7.688786] random: nonblocking pool is initialized
[    8.283898] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[    8.284064] systemd[1]: Detected architecture x86-64.
[    8.297395] systemd[1]: Set hostname to <mctest>.
[    9.178129] systemd[1]: Created slice User and Session Slice.
[    9.178211] systemd[1]: Listening on fsck to fsckd communication Socket.
[    9.178222] systemd[1]: Reached target User and Group Name Lookups.
[    9.178257] systemd[1]: Listening on udev Control Socket.
[    9.178297] systemd[1]: Listening on Journal Socket (/dev/log).
[    9.178309] systemd[1]: Reached target Encrypted Volumes.
[    9.178379] systemd[1]: Created slice System Slice.
[    9.178451] systemd[1]: Created slice system-getty.slice.
[    9.178475] systemd[1]: Listening on Syslog Socket.
[    9.178508] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    9.178546] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    9.178576] systemd[1]: Listening on Journal Socket.
[    9.188269] systemd[1]: Mounting POSIX Message Queue File System...
[    9.188871] systemd[1]: Mounting Huge Pages File System...
[    9.189532] systemd[1]: Mounting Debug File System...
[    9.348560] systemd[1]: Starting Load Kernel Modules...
[    9.349199] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    9.350001] systemd[1]: Started Read required files in advance.
[    9.350778] systemd[1]: Starting Uncomplicated firewall...
[    9.350855] systemd[1]: Listening on udev Kernel Socket.
[    9.351050] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    9.414995] systemd[1]: Reached target Slices.
[    9.415111] systemd[1]: Listening on Journal Audit Socket.
[    9.424360] systemd[1]: Starting Journal Service...
[    9.424963] systemd[1]: Starting Nameserver information manager...
[    9.424995] systemd[1]: Reached target Remote File Systems (Pre).
[    9.425028] systemd[1]: Reached target Remote File Systems.
[    9.663506] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    9.684426] systemd[1]: Starting Create Static Device Nodes in /dev...
[    9.684845] systemd[1]: Started Uncomplicated firewall.
[    9.831226] it87: Found IT8718F chip at 0x228, revision 5
[    9.831250] it87: Beeping is supported
[    9.832006] systemd[1]: Started Load Kernel Modules.
[    9.848417] systemd[1]: Starting Apply Kernel Variables...
[    9.849122] systemd[1]: Mounting FUSE Control File System...
[    9.945854] systemd[1]: Started Journal Service.
[   12.054263] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   12.234618] systemd-journald[246]: Received request to flush runtime journal from PID 1
[   12.546157] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.933176] ACPI Warning: SystemIO range 0x0000000000000B00-0x0000000000000B07 conflicts with OpRegion 0x0000000000000B00-0x0000000000000B0F (\SOR1) (20150930/utaddress-254)
[   12.933184] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.997462] k10temp 0000:00:18.3: unreliable CPU thermal sensor; monitoring disabled
[   13.098632] EDAC MC: Ver: 3.0.0
[   13.151094] MCE: In-kernel MCE decoding enabled.
[   13.159659] AMD64 EDAC driver v3.4.0
[   13.159698] EDAC amd64: DRAM ECC disabled.
[   13.159703] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
                Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
                (Note that use of the override may cause unknown side effects.)
[   13.352489] media: Linux media interface: v0.10
[   13.451238] kvm: Nested Virtualization enabled
[   13.451246] kvm: Nested Paging enabled
[   13.467988] Linux video capture interface: v2.00
[   13.551753] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:05.1/sound/card1/input8
[   13.563156] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC889A: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   13.563161] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   13.563166] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   13.563168] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   13.563169] snd_hda_codec_realtek hdaudioC0D0:    dig-out=0x1e/0x0
[   13.563171] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   13.563174] snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
[   13.563176] snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
[   13.563177] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
[   13.563179] snd_hda_codec_realtek hdaudioC0D0:      CD=0x1c
[   13.563180] snd_hda_codec_realtek hdaudioC0D0:    dig-in=0x1f
[   13.586333] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[   13.586394] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[   13.586446] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[   13.586498] input: HDA ATI SB Line Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
[   13.586550] input: HDA ATI SB Line Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input13
[   13.586601] input: HDA ATI SB Line Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input14
[   13.586654] input: HDA ATI SB Line Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input15
[   13.736484] ppdev: user-space parallel port driver
[   14.416313] cx23885 driver version 0.0.4 loaded
[   14.416790] CORE cx23885[0]: subsystem: 0070:7801, board: Hauppauge WinTV-HVR1800 [card=2,autodetected]
[   14.801838] tveeprom 5-0050: Hauppauge model 78521, rev C1E9, serial# 4029866930
[   14.801841] tveeprom 5-0050: MAC address is 00:0d:fe:32:e3:b2
[   14.801843] tveeprom 5-0050: tuner model is Philips 18271_8295 (idx 149, type 54)
[   14.801845] tveeprom 5-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   14.801847] tveeprom 5-0050: audio processor is CX23887 (idx 42)
[   14.801848] tveeprom 5-0050: decoder processor is CX23887 (idx 37)
[   14.801849] tveeprom 5-0050: has radio
[   14.801851] cx23885[0]: hauppauge eeprom: model=78521
[   15.006706] cx25840 7-0044: cx23887 A/V decoder found @ 0x88 (cx23885[0])
[   15.517352] audit: type=1400 audit(1464870095.408:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=538 comm="apparmor_parser"
[   15.517363] audit: type=1400 audit(1464870095.408:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=538 comm="apparmor_parser"
[   15.517368] audit: type=1400 audit(1464870095.408:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=538 comm="apparmor_parser"
[   15.517373] audit: type=1400 audit(1464870095.408:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=538 comm="apparmor_parser"
[   15.593904] audit: type=1400 audit(1464870095.484:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=537 comm="apparmor_parser"
[   15.593915] audit: type=1400 audit(1464870095.484:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//chromium" pid=537 comm="apparmor_parser"
[   15.629628] audit: type=1400 audit(1464870095.520:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=541 comm="apparmor_parser"
[   15.632578] floppy0: no floppy controllers found
[   15.632598] work still pending
[   15.664840] audit: type=1400 audit(1464870095.556:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=543 comm="apparmor_parser"
[   15.716319] audit: type=1400 audit(1464870095.604:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=539 comm="apparmor_parser"
[   15.716332] audit: type=1400 audit(1464870095.604:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince//sanitized_helper" pid=539 comm="apparmor_parser"
[   15.826663] cx25840 7-0044: loaded v4l-cx23885-avcore-01.fw firmware (16382 bytes)
[   18.200952] tuner 6-0042: Tuner -1 found with type(s) Radio TV.
[   18.237723] tda829x 6-0042: could not clearly identify tuner address, defaulting to 60
[   18.261036] tda18271 6-0060: creating new instance
[   18.297027] TDA18271HD/C1 detected @ 6-0060
[   18.299700] Adding 3665916k swap on /dev/sda5.  Priority:-1 extents:1 across:3665916k FS
[   18.725177] tda829x 6-0042: type set to tda8295+18271
[   21.019939] cx23885[0]: registered device video0 [v4l2]
[   21.020073] cx23885[0]: registered device vbi0
[   21.020401] cx23885[0]: registered ALSA audio device
[   21.020493] cx23885[0]: registered device video1 [mpeg]
[   21.020508] Firmware and/or mailbox pointer not initialized or corrupted, signature = 0xdbf79dbd, cmd = PING_FW
[   21.825680] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   21.834160] r8169 0000:04:00.0 enp4s0: link down
[   21.834224] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   23.060288] r8169 0000:04:00.0 enp4s0: link down
[   23.465015] cx23885_dvb_register() allocating 1 frontend(s)
[   23.465022] cx23885[0]: cx23885 based dvb card
[   23.563898] MT2131: successfully identified at address 0x61
[   23.565545] DVB: registering new adapter (cx23885[0])
[   23.565551] cx23885 0000:02:00.0: DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   23.565953] cx23885_dev_checkrevision() Hardware revision = 0xb1
[   23.565959] cx23885[0]/0: found at 0000:02:00.0, rev: 15, irq: 18, latency: 0, mmio: 0xfd400000
[   24.092905] r8169 0000:04:00.0 enp4s0: link up
[   24.092920] IPv6: ADDRCONF(NETDEV_CHANGE): enp4s0: link becomes ready
[   41.023021] CE: hpet increased min_delta_ns to 20115 nsec


```

---

