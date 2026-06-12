---
title: "Problem with NVIDIA FX5700 in Kubuntu 16.10"
date: 2017-02-06
forum: Hardware
---

### Post by radamanthis78 on 2017-02-06
Hello,

I've decided to upgrade Kubuntu in my old computer. I made a clean installation of Kubuntu 16.10. The system is working, but I cannot change the resolution of my graphics card. Since I've read in many posts that privative drivers of NVIDIA don't cover my old graphics card, I'm using the nouveau driver and the DVI port. The maximum resolution that I've got was 1024x768. My screen could get better resolution, since it is an Acer K242HL. I would like to have a 1920x1080 screen resolution. I also installed the lubuntu-desktop package. Any ideas? How can I get a better resolution by using nouveau driver?

I copy at the end the output of xrandr and lspci.

Thank you for your help and advices.

```
javier@javier-D1675:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768      76.00* 

The output of xrandr -props | edid-decode is:
javier@javier-D1675:~$ xrandr --props | edid-decode 
xrandr: Failed to get size of gamma for output default
Extracted contents:
header:          53 63 72 65 65 6e 20 30
serial number:   3a 20 6d 69 6e 69 6d 75 6d 20
version:         31 30
basic params:    32 34 20 78 20
chroma info:     37 36 38 2c 20 63 75 72 72 65
established:     6e 74 20
standard:        31 30 32 34 20 78 20 37 36 38 2c 20 6d 61 78 69
descriptor 1:    6d 75 6d 20 31 30 32 34 20 78 20 37 36 38 0a 64 65 66
descriptor 2:    61 75 6c 74 20 63 6f 6e 6e 65 63 74 65 64 20 31 30 32
descriptor 3:    34 78 37 36 38 2b 30 2b 30 20 30 6d 6d 20 78 20 30 6d
descriptor 4:    6d 0a 20 20 20 31 30 32 34 78 37 36 38 20 20 20 20 20
extensions:      20
checksum:        37

No header found
Manufacturer: NQ@ Model 696d Serial Number 1970104686
EDID version: 49.48
Analog display, Input voltage level: 0.714/0.286 V
Configurable signal levels
Sync: SyncOnGreen 
Maximum image size: 52 cm x 32 cm
Gamma: 2.20
DPMS levels: Off
Monochrome or grayscale display
Established timings supported:
  720x400@88Hz
  640x480@60Hz
  640x480@72Hz
  640x480@75Hz
  800x600@56Hz
  800x600@75Hz
  832x624@75Hz
  1280x768@87Hz
  1024x768@70Hz
Standard timings supported:
  640x640@108Hz
  648x648@112Hz
  504x378@116Hz
  504x504@115Hz
  680x680@116Hz
  600x600@92Hz
  1120x840@93Hz
  1208x906@101Hz
Detailed mode: Clock 300.610 MHz, 54 mm x 2616 mm
                877  909 1797 1165 hborder 100
                816  834  882 1890 vborder 101
               +hsync +vsync analog composite four way interleaved
Detailed mode: Clock 300.490 MHz, 613 mm x 100 mm
                620  986 1855  736 hborder 49
               1635 1657 1660 5330 vborder 48
               +hsync -vsync digital composite field sequential L/R
Detailed mode: Clock 307.720 MHz, 1901 mm x 2080 mm
                823 1127 1671 2925 hborder 32
                555  606  622 3419 vborder 48
               -hsync +vsync bipolar analog composite side by side interleaved
Detailed mode: Clock 26.690 MHz, 568 mm x 32 mm
                544  596 1484  576 hborder 32
                817  836  875 1377 vborder 32
               -hsync -vsync analog composite field sequential L/R
Has 32 extension blocks
Checksum: 0x37 (should be 0x1f)
EDID block does not conform at all!
	Block has broken checksum
	Bad year of manufacture
	Bad week of manufacture
	Manufacturer name field contains garbage

lspci give me the following:
javier@javier-D1675:~$ lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 50)
	Flags: bus master, medium devsel, latency 64
	Memory at d0000000 (32-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-sis
	Kernel modules: sis_agp

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	Memory behind bridge: d5000000-d5ffffff
	Prefetchable memory behind bridge: e0000000-efffffff
	Kernel modules: shpchp

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] LPC Controller (rev 14)
	Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2/3 SMBus controller
	Flags: medium devsel, IRQ 11
	I/O ports at 8100 [size=32]
	Kernel driver in use: sis96x_smbus
	Kernel modules: i2c_sis96x

00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller (prog-if 10 [OHCI])
	Subsystem: Fujitsu Technology Solutions FireWire Controller
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at d4000000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at c0000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire_ohci

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller (prog-if 80 [Master])
	Subsystem: Fujitsu Technology Solutions 5513 IDE Controller
	Flags: bus master, medium devsel, latency 128, IRQ 9
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable)
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable)
	I/O ports at 1800 [size=16]
	Kernel driver in use: pata_sis
	Kernel modules: pata_acpi

00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Fujitsu Technology Solutions USB 1.1 Controller
	Flags: bus master, medium devsel, latency 64, IRQ 9
	Memory at d4001000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci-pci

00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Fujitsu Technology Solutions USB 1.1 Controller
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at d4002000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci-pci

00:03.2 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Fujitsu Technology Solutions USB 1.1 Controller
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at d4003000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci-pci

00:03.3 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
	Subsystem: Fujitsu Technology Solutions USB 2.0 Controller
	Flags: bus master, medium devsel, latency 64, IRQ 9
	Memory at d4004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci

00:06.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
	Subsystem: Fujitsu Technology Solutions Scenic N300 ADMtek AN983 10/100 Mbps PCI Adapter
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at 1000 [size=256]
	Memory at d4005000 (32-bit, non-prefetchable) [size=1K]
	[virtual] Expansion ROM at c0020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: tulip
	Kernel modules: tulip

00:0c.0 Multimedia audio controller: Creative Labs CA0106/CA0111 [SB Live!/Audigy/X-Fi Series]
	Subsystem: Creative Labs SB0570 [SB Audigy SE]
	Flags: bus master, medium devsel, latency 64, IRQ 5
	I/O ports at 1400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: snd_ca0106
	Kernel modules: snd_ca0106

00:0e.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
	Subsystem: Pinnacle Systems Inc. PCTV Stereo
	Flags: bus master, medium devsel, latency 254, IRQ 11
	Memory at d4005400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134

01:00.0 VGA compatible controller: NVIDIA Corporation NV36 [GeForce FX 5700VE] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: LeadTek Research Inc. NV36 [GeForce FX 5700VE]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 9
	Memory at d5000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	[virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: nvidiafb, nouveau

```

---

### Post by wildmanne39 on 2017-02-06
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by radamanthis78 on 2017-02-08
Thank you for your help.

I provide you the output of dmesg.

```

[    0.000000] Linux version 4.8.0-37-generic (buildd@lcy01-11) (gcc version 6.2.0 20161005 (Ubuntu 6.2.0-5ubuntu12) ) #39-Ubuntu SMP Thu Jan 26 02:25:32 UTC 2017 (Ubuntu 4.8.0-37.39-generic 4.8.16)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] x86/fpu: Legacy x87 FPU detected.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f3ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f400-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000d8000-0x00000000000dffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bfeeffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfef0000-0x00000000bfefefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bfeff000-0x00000000bfefffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bff00000-0x00000000bff7ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bff80000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fecfffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000feefffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] SMBIOS 2.3 present.
[    0.000000] DMI: FUJITSU SIEMENS D1675/D1675, BIOS 4.06  Rev. 1.01.1675             09/19/2003
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0xbff80 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0BFF80000 mask FFFF80000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
[    0.000000] total RAM covered: 3071M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 1M 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x0d3fffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] BRK [0x0ce60000, 0x0ce60fff] PGTABLE
[    0.000000] BRK [0x0ce61000, 0x0ce61fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x33338000-0x35993fff]
[    0.000000] 2179MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   Normal   [mem 0x0000000001000000-0x0000000037bfdfff]
[    0.000000]   HighMem  [mem 0x0000000037bfe000-0x00000000bff7ffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009efff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000bfeeffff]
[    0.000000]   node   0: [mem 0x00000000bff00000-0x00000000bff7ffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x00000000bff7ffff]
[    0.000000] On node 0 totalpages: 786190
[    0.000000]   DMA zone: 40 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 2190 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 557938 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] SFI: Simple Firmware Interface v0.81 http://simplefirmware.org
[    0.000000] Found and enabled local APIC!
[    0.000000] smpboot: Boot CPU (id 0) not listed by BIOS
[    0.000000] smpboot: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000d7fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000d8000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000e3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e4000-0x000fffff]
[    0.000000] e820: [mem 0xc0000000-0xfebfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] percpu: Embedded 21 pages/cpu @f5dc2000 s54732 r0 d31284 u86016
[    0.000000] pcpu-alloc: s54732 r0 d31284 u86016 alloc=21*4096
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 783960
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.8.0-37-generic root=UUID=488b5f28-7c2e-474b-b093-3617d07bc33d ro acpi=off quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] microcode: microcode updated early to revision 0x2e, date = 2004-08-11
[    0.000000] Initializing CPU#0
[    0.000000] Initializing HighMem for node 0 (00037bfe:000bff80)
[    0.000000] Initializing Movable for node 0 (00000000:00000000)
[    0.000000] Memory: 3058920K/3144760K available (8236K kernel code, 844K rwdata, 3320K rodata, 988K init, 852K bss, 85840K reserved, 0K cma-reserved, 2231752K highmem)
[    0.000000] virtual kernel memory layout:
                   fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
                   pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
                   vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
                   lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
                     .init : 0xccc21000 - 0xccd18000   ( 988 kB)
                     .data : 0xcc80b597 - 0xccc1f040   (4174 kB)
                     .text : 0xcc000000 - 0xcc80b597   (8237 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	Build-time adjustment of leaf fanout to 32.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=1.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=32, nr_cpu_ids=1
[    0.000000] NR_IRQS:2304 nr_irqs:32 16
[    0.000000] CPU 0 irqstacks, hard=f2c38000 soft=f2c3a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 3145728 bytes of page_ext
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 3199.974 MHz processor
[    0.004027] Calibrating delay loop (skipped), value calculated using timer frequency.. 6399.94 BogoMIPS (lpj=12799896)
[    0.004034] pid_max: default: 32768 minimum: 301
[    0.004153] Security Framework initialized
[    0.004157] Yama: becoming mindful.
[    0.004201] AppArmor: AppArmor initialized
[    0.004272] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004275] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004741] CPU: Physical Processor ID: 0
[    0.004744] CPU: Processor Core ID: 0
[    0.004752] mce: CPU supports 4 MCE banks
[    0.004762] CPU0: Thermal monitoring enabled (TM1)
[    0.004782] Last level iTLB entries: 4KB 64, 2MB 64, 4MB 64
[    0.004784] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 64, 1GB 0
[    0.026160] Freeing SMP alternatives memory: 32K (ccd18000 - ccd20000)
[    0.028472] ftrace: allocating 32549 entries in 64 pages
[    0.040218] smpboot: APIC(0) Converting physical 0 to logical package 0
[    0.040222] smpboot: Max logical packages: 1
[    0.040226] smpboot: SMP motherboard not detected
[    0.040227] smpboot: SMP disabled
[    0.040231] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.148021] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[    0.148036] ... version:                0
[    0.148037] ... bit width:              40
[    0.148038] ... generic registers:      18
[    0.148039] ... value mask:             000000ffffffffff
[    0.148040] ... max period:             0000007fffffffff
[    0.148041] ... fixed-purpose events:   0
[    0.148042] ... event mask:             000000000003ffff
[    0.149484] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.149525] x86: Booted up 1 node, 1 CPUs
[    0.149528] smpboot: Total of 1 processors activated (6399.94 BogoMIPS)
[    0.150032] devtmpfs: initialized
[    0.150525] evm: security.selinux
[    0.150526] evm: security.SMACK64
[    0.150527] evm: security.SMACK64EXEC
[    0.150527] evm: security.SMACK64TRANSMUTE
[    0.150528] evm: security.SMACK64MMAP
[    0.150529] evm: security.ima
[    0.150530] evm: security.capability
[    0.150656] PM: Registering ACPI NVS region [mem 0xbfeff000-0xbfefffff] (4096 bytes)
[    0.150760] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.150805] pinctrl core: initialized pinctrl subsystem
[    0.150993] RTC time: 10:05:26, date: 02/08/17
[    0.151154] NET: Registered protocol family 16
[    0.151448] EISA bus registered
[    0.151451] cpuidle: using governor ladder
[    0.151452] cpuidle: using governor menu
[    0.197507] PCI: PCI BIOS revision 2.10 entry at 0xfd99d, last bus=1
[    0.197509] PCI: Using configuration type 1 for base access
[    0.199949] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.200392] ACPI: Interpreter disabled.
[    0.200782] SCSI subsystem initialized
[    0.200847] libata version 3.00 loaded.
[    0.200926] vgaarb: loaded
[    0.201011] usbcore: registered new interface driver usbfs
[    0.201028] usbcore: registered new interface driver hub
[    0.201042] usbcore: registered new device driver usb
[    0.201237] PCI: Probing PCI hardware
[    0.201240] PCI: root bus 00: using default resources
[    0.201241] PCI: Probing PCI hardware (bus 00)
[    0.201296] PCI host bridge to bus 0000:00
[    0.201303] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.201305] pci_bus 0000:00: root bus resource [mem 0x00000000-0xfffffffff]
[    0.201307] pci_bus 0000:00: No busn resource found for root bus, will use [bus 00-ff]
[    0.201326] pci 0000:00:00.0: [1039:0648] type 00 class 0x060000
[    0.201339] pci 0000:00:00.0: reg 0x10: [mem 0xd0000000-0xd3ffffff]
[    0.201479] pci 0000:00:01.0: [1039:0003] type 01 class 0x060400
[    0.201573] pci 0000:00:02.0: [1039:0008] type 00 class 0x060100
[    0.201648] pci 0000:00:02.0: Enabling SiS 96x SMBus
[    0.201721] pci 0000:00:02.1: [1039:0016] type 00 class 0x0c0500
[    0.201772] pci 0000:00:02.1: reg 0x20: [io  0x8100-0x811f]
[    0.201865] pci 0000:00:02.3: [1039:7007] type 00 class 0x0c0010
[    0.201884] pci 0000:00:02.3: reg 0x10: [mem 0xd4000000-0xd4000fff]
[    0.201941] pci 0000:00:02.3: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.201972] pci 0000:00:02.3: supports D1 D2
[    0.201974] pci 0000:00:02.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.202049] pci 0000:00:02.5: [1039:5513] type 00 class 0x01018a
[    0.202065] pci 0000:00:02.5: reg 0x10: [io  0x01f0-0x01f7]
[    0.202076] pci 0000:00:02.5: reg 0x14: [io  0x03f4-0x03f7]
[    0.202087] pci 0000:00:02.5: reg 0x18: [io  0x0170-0x0177]
[    0.202097] pci 0000:00:02.5: reg 0x1c: [io  0x0374-0x0377]
[    0.202107] pci 0000:00:02.5: reg 0x20: [io  0x1800-0x180f]
[    0.202130] pci 0000:00:02.5: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.202131] pci 0000:00:02.5: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.202133] pci 0000:00:02.5: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.202135] pci 0000:00:02.5: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.202206] pci 0000:00:03.0: [1039:7001] type 00 class 0x0c0310
[    0.202221] pci 0000:00:03.0: reg 0x10: [mem 0xd4001000-0xd4001fff]
[    0.202338] pci 0000:00:03.1: [1039:7001] type 00 class 0x0c0310
[    0.202354] pci 0000:00:03.1: reg 0x10: [mem 0xd4002000-0xd4002fff]
[    0.202475] pci 0000:00:03.2: [1039:7001] type 00 class 0x0c0310
[    0.202490] pci 0000:00:03.2: reg 0x10: [mem 0xd4003000-0xd4003fff]
[    0.202615] pci 0000:00:03.3: [1039:7002] type 00 class 0x0c0320
[    0.202633] pci 0000:00:03.3: reg 0x10: [mem 0xd4004000-0xd4004fff]
[    0.202712] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.202795] pci 0000:00:06.0: [1317:0985] type 00 class 0x020000
[    0.202813] pci 0000:00:06.0: reg 0x10: [io  0x1000-0x10ff]
[    0.202825] pci 0000:00:06.0: reg 0x14: [mem 0xd4005000-0xd40053ff]
[    0.202871] pci 0000:00:06.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.202901] pci 0000:00:06.0: supports D1 D2
[    0.202903] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.203002] pci 0000:00:0c.0: [1102:0007] type 00 class 0x040100
[    0.203020] pci 0000:00:0c.0: reg 0x10: [io  0x1400-0x141f]
[    0.203101] pci 0000:00:0c.0: supports D1 D2
[    0.203169] pci 0000:00:0e.0: [1131:7134] type 00 class 0x048000
[    0.203187] pci 0000:00:0e.0: reg 0x10: [mem 0xd4005400-0xd40057ff]
[    0.203269] pci 0000:00:0e.0: supports D1 D2
[    0.203399] pci 0000:01:00.0: [10de:0344] type 00 class 0x030000
[    0.203415] pci 0000:01:00.0: reg 0x10: [mem 0xd5000000-0xd5ffffff]
[    0.203424] pci 0000:01:00.0: reg 0x14: [mem 0xe0000000-0xefffffff pref]
[    0.203458] pci 0000:01:00.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.203533] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.203535] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.203574] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.203582] pci 0000:00:01.0:   bridge window [mem 0xd5000000-0xd5ffffff]
[    0.203586] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff pref]
[    0.203597] pci_bus 0000:00: busn_res: [bus 00-ff] end is updated to 01
[    0.203648] pci 0000:00:02.0: SIS IRQ router [1039:0963]
[    0.203661] PCI: setting IRQ 11 as level-triggered
[    0.203664] pci 0000:00:02.1: found PCI INT B -> IRQ 11
[    0.203673] pci 0000:00:02.1: sharing IRQ 11 with 0000:00:02.3
[    0.203691] PCI: setting IRQ 9 as level-triggered
[    0.203693] pci 0000:00:02.5: found PCI INT A -> IRQ 9
[    0.203724] PCI: pci_cache_line_size set to 64 bytes
[    0.203773] e820: reserve RAM buffer [mem 0x0009f400-0x0009ffff]
[    0.203776] e820: reserve RAM buffer [mem 0xbfef0000-0xbfffffff]
[    0.203778] e820: reserve RAM buffer [mem 0xbff80000-0xbfffffff]
[    0.203986] NetLabel: Initializing
[    0.203988] NetLabel:  domain hash size = 128
[    0.203989] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.204065] NetLabel:  unlabeled traffic allowed by default
[    0.204392] clocksource: Switched to clocksource refined-jiffies
[    0.220841] VFS: Disk quotas dquot_6.6.0
[    0.220874] VFS: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.221055] AppArmor: AppArmor Filesystem Enabled
[    0.221158] pnp: PnP ACPI: disabled
[    0.221165] PnPBIOS: Scanning system for PnP BIOS support...
[    0.221194] PnPBIOS: Found PnP BIOS installation structure at 0xc00f8310
[    0.221196] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xa70e, dseg 0x400
[    0.221462] pnp 00:00: [io  0x0080]
[    0.221464] pnp 00:00: [io  0x0800-0x082f]
[    0.221467] pnp 00:00: [mem 0xfffffffffff00000-0xffffffffffffffff]
[    0.221469] pnp 00:00: [io  0xf200-0xf27f]
[    0.221470] pnp 00:00: [io  0xf280-0xf2ff]
[    0.221472] pnp 00:00: [io  0xfe00]
[    0.221548] system 00:00: [io  0x0800-0x082f] has been reserved
[    0.221551] system 00:00: [io  0xf200-0xf27f] has been reserved
[    0.221553] system 00:00: [io  0xf280-0xf2ff] has been reserved
[    0.221555] system 00:00: [io  0xfe00] has been reserved
[    0.221565] system 00:00: [mem 0xfffffffffff00000-0xffffffffffffffff] could not be reserved
[    0.221570] system 00:00: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.221579] pnp 00:01: [mem 0x00000000-0x0009ffff]
[    0.221581] pnp 00:01: [mem 0x000e0000-0x000fffff]
[    0.221584] pnp 00:01: [mem 0x00100000-0xffffffffbff7ffff disabled]
[    0.221623] system 00:01: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.221626] system 00:01: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.221629] system 00:01: Plug and Play BIOS device, IDs PNP0c01 (active)
[    0.221637] pnp 00:02: [io  0x0000-0x000f]
[    0.221639] pnp 00:02: [io  0x0081-0x008f]
[    0.221640] pnp 00:02: [io  0x00c0-0x00df]
[    0.221642] pnp 00:02: [dma 4]
[    0.221675] pnp 00:02: Plug and Play BIOS device, IDs PNP0200 (active)
[    0.221686] pnp 00:03: [io  0x0020-0x0021]
[    0.221688] pnp 00:03: [io  0x00a0-0x00a1]
[    0.221690] pnp 00:03: [irq 2]
[    0.221718] pnp 00:03: Plug and Play BIOS device, IDs PNP0000 (active)
[    0.221725] pnp 00:04: [io  0x0040-0x0043]
[    0.221727] pnp 00:04: [irq 0]
[    0.221754] pnp 00:04: Plug and Play BIOS device, IDs PNP0100 (active)
[    0.221761] pnp 00:05: [io  0x0070-0x0071]
[    0.221763] pnp 00:05: [irq 8]
[    0.221795] pnp 00:05: Plug and Play BIOS device, IDs PNP0b00 (active)
[    0.221802] pnp 00:06: [io  0x0060]
[    0.221804] pnp 00:06: [io  0x0064]
[    0.221805] pnp 00:06: [irq 1]
[    0.221832] pnp 00:06: Plug and Play BIOS device, IDs PNP0303 (active)
[    0.221840] pnp 00:07: [io  0x00f0-0x00ff]
[    0.221842] pnp 00:07: [irq 13]
[    0.221869] pnp 00:07: Plug and Play BIOS device, IDs PNP0c04 (active)
[    0.221879] pnp 00:08: [io  0x0061]
[    0.221912] pnp 00:08: Plug and Play BIOS device, IDs PNP0800 (active)
[    0.221919] pnp 00:09: [mem 0x000d8000-0x000dffff]
[    0.221958] system 00:09: [mem 0x000d8000-0x000dffff] could not be reserved
[    0.221962] system 00:09: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.221969] pnp 00:0a: [io  0x0cf8-0x0cff]
[    0.221997] pnp 00:0a: Plug and Play BIOS device, IDs PNP0a03 (active)
[    0.222005] pnp 00:0b: [io  0x0480-0x048f]
[    0.222007] pnp 00:0b: [io  0x04d0-0x04d1]
[    0.222009] pnp 00:0b: [io  0xf000-0xf0fe]
[    0.222011] pnp 00:0b: [io  0xf0ff]
[    0.222012] pnp 00:0b: [io  0x8100-0x811f]
[    0.222014] pnp 00:0b: [mem 0xffffffffffee0000-0xffffffffffefffff]
[    0.222059] system 00:0b: [io  0x0480-0x048f] has been reserved
[    0.222062] system 00:0b: [io  0x04d0-0x04d1] has been reserved
[    0.222064] system 00:0b: [io  0xf000-0xf0fe] has been reserved
[    0.222066] system 00:0b: [io  0xf0ff] has been reserved
[    0.222069] system 00:0b: [io  0x8100-0x811f] has been reserved
[    0.222071] system 00:0b: [mem 0xffffffffffee0000-0xffffffffffefffff] could not be reserved
[    0.222075] system 00:0b: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.222111] pnp 00:0c: [mem 0x000cfc00-0x000cffff]
[    0.222150] system 00:0c: [mem 0x000cfc00-0x000cffff] has been reserved
[    0.222153] system 00:0c: Plug and Play BIOS device, IDs PNP0c02 (active)
[    0.222287] pnp 00:0d: [irq 12]
[    0.222319] pnp 00:0d: Plug and Play BIOS device, IDs PNP0f13 (active)
[    0.222556] pnp 00:0e: [io  0x03f8-0x03ff]
[    0.222558] pnp 00:0e: [irq 4]
[    0.222606] pnp 00:0e: Plug and Play BIOS device, IDs PNP0501 (active)
[    0.222885] pnp 00:10: [io  0x03f0-0x03f5]
[    0.222887] pnp 00:10: [io  0x03f7]
[    0.222889] pnp 00:10: [irq 6]
[    0.222890] pnp 00:10: [dma 2]
[    0.222934] pnp 00:10: Plug and Play BIOS device, IDs PNP0700 (active)
[    0.223161] pnp 00:14: [io  0x0378-0x037f]
[    0.223163] pnp 00:14: [irq 7]
[    0.223206] pnp 00:14: Plug and Play BIOS device, IDs PNP0400 (active)
[    0.223211] PnPBIOS: 17 nodes reported by PnP BIOS; 17 recorded by driver
[    0.226281] pci 0000:00:02.3: BAR 6: assigned [mem 0xc0000000-0xc001ffff pref]
[    0.226288] pci 0000:00:06.0: BAR 6: assigned [mem 0xc0020000-0xc003ffff pref]
[    0.226292] pci 0000:01:00.0: BAR 6: no space for [mem size 0x00020000 pref]
[    0.226295] pci 0000:01:00.0: BAR 6: failed to assign [mem size 0x00020000 pref]
[    0.226298] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.226305] pci 0000:00:01.0:   bridge window [mem 0xd5000000-0xd5ffffff]
[    0.226309] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff pref]
[    0.226317] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.226319] pci_bus 0000:00: resource 5 [mem 0x00000000-0xfffffffff]
[    0.226322] pci_bus 0000:01: resource 1 [mem 0xd5000000-0xd5ffffff]
[    0.226324] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff pref]
[    0.226382] NET: Registered protocol family 2
[    0.226700] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.226724] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.226766] TCP: Hash tables configured (established 8192 bind 8192)
[    0.226818] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.226829] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.226893] NET: Registered protocol family 1
[    0.226949] pci 0000:00:03.0: found PCI INT A -> IRQ 9
[    0.227020] pci 0000:00:03.1: found PCI INT B -> IRQ 11
[    0.227060] PCI: setting IRQ 10 as level-triggered
[    0.227063] pci 0000:00:03.2: found PCI INT C -> IRQ 10
[    0.227104] pci 0000:00:03.3: found PCI INT D -> IRQ 9
[    0.227158] pci 0000:01:00.0: Video device with shadowed ROM at [mem 0x000c0000-0x000dffff]
[    0.227161] PCI: CLS 16 bytes, default 64
[    0.227281] Trying to unpack rootfs image as initramfs...
[    1.210289] Freeing initrd memory: 39280K (f3338000 - f5994000)
[    1.210643] Scanning for low memory corruption every 60 seconds
[    1.211243] futex hash table entries: 256 (order: 2, 16384 bytes)
[    1.211284] audit: initializing netlink subsys (disabled)
[    1.211328] audit: type=2000 audit(1486548327.208:1): initialized
[    1.211702] Initialise system trusted keyrings
[    1.211857] workingset: timestamp_bits=14 max_order=20 bucket_order=6
[    1.214833] zbud: loaded
[    1.215498] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    1.215899] fuse init (API version 7.25)
[    1.216218] Allocating IMA blacklist keyring.
[    1.217729] Key type asymmetric registered
[    1.217732] Asymmetric key parser 'x509' registered
[    1.217753] bounce: pool size: 64 pages
[    1.217840] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 248)
[    1.217886] io scheduler noop registered
[    1.217888] io scheduler deadline registered (default)
[    1.217993] io scheduler cfq registered
[    1.218234] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.218243] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.218297] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    1.218298] vesafb: scrolling: redraw
[    1.218301] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.218327] vesafb: framebuffer at 0xe0000000, mapped to 0xf8600000, using 3072k, total 3072k
[    1.218536] Console: switching to colour frame buffer device 128x48
[    1.218557] fb0: VESA VGA frame buffer device
[    1.218841] isapnp: Scanning for PnP cards...
[    1.224437] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.228138] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.275154] Linux agpgart interface v0.103
[    1.280159] brd: module loaded
[    1.282735] loop: module loaded
[    1.283039] pata_sis 0000:00:02.5: version 0.5.2
[    1.283058] pata_sis 0000:00:02.5: found PCI INT A -> IRQ 9
[    1.283102] pata_sis 0000:00:02.5: SiS 962/963 MuTIOL IDE UDMA133 controller
[    1.283718] scsi host0: pata_sis
[    1.327445] scsi host1: pata_sis
[    1.327527] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1800 irq 14
[    1.327530] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1808 irq 15
[    1.327670] libphy: Fixed MDIO Bus: probed
[    1.327671] tun: Universal TUN/TAP device driver, 1.6
[    1.327672] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.327803] PPP generic driver version 2.4.2
[    1.327893] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.327901] ehci-pci: EHCI PCI platform driver
[    1.327937] ehci-pci 0000:00:03.3: found PCI INT D -> IRQ 9
[    1.327996] ehci-pci 0000:00:03.3: EHCI Host Controller
[    1.328006] ehci-pci 0000:00:03.3: new USB bus registered, assigned bus number 1
[    1.328056] ehci-pci 0000:00:03.3: cache line size of 16 is not supported
[    1.328070] ehci-pci 0000:00:03.3: irq 9, io mem 0xd4004000
[    1.371826] ehci-pci 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    1.371937] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.371940] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.371942] usb usb1: Product: EHCI Host Controller
[    1.371943] usb usb1: Manufacturer: Linux 4.8.0-37-generic ehci_hcd
[    1.371945] usb usb1: SerialNumber: 0000:00:03.3
[    1.372171] hub 1-0:1.0: USB hub found
[    1.372183] hub 1-0:1.0: 6 ports detected
[    1.372476] ehci-platform: EHCI generic platform driver
[    1.372497] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.372505] ohci-pci: OHCI PCI platform driver
[    1.372533] ohci-pci 0000:00:03.0: found PCI INT A -> IRQ 9
[    1.372583] ohci-pci 0000:00:03.0: OHCI PCI host controller
[    1.372591] ohci-pci 0000:00:03.0: new USB bus registered, assigned bus number 2
[    1.372617] ohci-pci 0000:00:03.0: irq 9, io mem 0xd4001000
[    1.461769] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.461771] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.461773] usb usb2: Product: OHCI PCI host controller
[    1.461775] usb usb2: Manufacturer: Linux 4.8.0-37-generic ohci_hcd
[    1.461776] usb usb2: SerialNumber: 0000:00:03.0
[    1.461974] hub 2-0:1.0: USB hub found
[    1.461985] hub 2-0:1.0: 2 ports detected
[    1.462150] ohci-pci 0000:00:03.1: found PCI INT B -> IRQ 11
[    1.462192] ohci-pci 0000:00:03.1: OHCI PCI host controller
[    1.462200] ohci-pci 0000:00:03.1: new USB bus registered, assigned bus number 3
[    1.462229] ohci-pci 0000:00:03.1: irq 11, io mem 0xd4002000
[    1.549494] isapnp: No Plug & Play device found
[    1.551856] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.551858] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.551860] usb usb3: Product: OHCI PCI host controller
[    1.551862] usb usb3: Manufacturer: Linux 4.8.0-37-generic ohci_hcd
[    1.551863] usb usb3: SerialNumber: 0000:00:03.1
[    1.552071] hub 3-0:1.0: USB hub found
[    1.552092] hub 3-0:1.0: 2 ports detected
[    1.552381] ohci-pci 0000:00:03.2: found PCI INT C -> IRQ 10
[    1.552434] ohci-pci 0000:00:03.2: OHCI PCI host controller
[    1.552446] ohci-pci 0000:00:03.2: new USB bus registered, assigned bus number 4
[    1.552485] ohci-pci 0000:00:03.2: irq 10, io mem 0xd4003000
[    1.572337] ata1.00: ATA-6: WDC WD1600LB-55EDA0, 15.05R15, max UDMA/100
[    1.572337] ata1.00: 312581808 sectors, multi 16: LBA48 
[    1.572337] ata1.01: ATA-8: WDC WD5000AAKB-00H8A0, 05.04E05, max UDMA/133
[    1.572337] ata1.01: 976773168 sectors, multi 16: LBA48 
[    1.580319] ata1.00: configured for UDMA/100
[    1.588318] ata1.01: configured for UDMA/133
[    1.588326] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600LB-55E 5R15 PQ: 0 ANSI: 5
[    1.588671] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.588838] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.588891] sd 0:0:0:0: [sda] Write Protect is off
[    1.588894] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.588917] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.608163]  sda: sda1
[    1.608323] scsi 0:0:1:0: Direct-Access     ATA      WDC WD5000AAKB-0 4E05 PQ: 0 ANSI: 5
[    1.608655] sd 0:0:1:0: [sdb] 976773168 512-byte logical blocks: (500 GB/466 GiB)
[    1.608717] sd 0:0:1:0: [sdb] Write Protect is off
[    1.608720] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.608956] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.614270] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.614335] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.614532] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.614534] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.614536] usb usb4: Product: OHCI PCI host controller
[    1.614538] usb usb4: Manufacturer: Linux 4.8.0-37-generic ohci_hcd
[    1.614539] usb usb4: SerialNumber: 0000:00:03.2
[    1.614743] hub 4-0:1.0: USB hub found
[    1.614756] hub 4-0:1.0: 2 ports detected
[    1.614985] ohci-platform: OHCI generic platform driver
[    1.615008] uhci_hcd: USB Universal Host Controller Interface driver
[    1.615157] i8042: PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    1.617324] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.617324] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.617348] mousedev: PS/2 mouse device common for all mice
[    1.617608] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.617632] rtc_cmos 00:05: alarms up to one day, 114 bytes nvram
[    1.617648] i2c /dev entries driver
[    1.617764] device-mapper: uevent: version 1.0.3
[    1.618060] device-mapper: ioctl: 4.35.0-ioctl (2016-06-23) initialised: dm-devel@redhat.com
[    1.618112] platform eisa.0: Probing EISA bus 0
[    1.618125] platform eisa.0: Cannot allocate resource for EISA slot 1
[    1.618156] platform eisa.0: EISA: Detected 0 cards
[    1.618168] cpufreq_nforce2: No nForce2 chipset
[    1.618186] ledtrig-cpu: registered to indicate activity on CPUs
[    1.618573] NET: Registered protocol family 10
[    1.620363] NET: Registered protocol family 17
[    1.620380] Key type dns_resolver registered
[    1.620707] microcode: sig=0xf29, pf=0x4, revision=0x2e
[    1.620774] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.620784] Using IPI No-Shortcut mode
[    1.620984] registered taskstats version 1
[    1.620994] Loading compiled-in X.509 certificates
[    1.621536]  sdb: sdb1 < sdb5 > sdb2 sdb3
[    1.622160] sd 0:0:1:0: [sdb] Attached SCSI disk
[    1.630881] Loaded X.509 cert 'Build time autogenerated kernel key: a757feba6d4cefcef6dbda704f0cfca54ec1cf78'
[    1.630932] zswap: loaded using pool lzo/zbud
[    1.663552] Key type big_key registered
[    1.667496] Key type trusted registered
[    1.671790] Key type encrypted registered
[    1.671798] AppArmor: AppArmor sha1 policy hashing enabled
[    1.671802] ima: No TPM chip found, activating TPM-bypass!
[    1.671846] evm: HMAC attrs: 0x1
[    1.672187]   Magic number: 5:148:72
[    1.672330] rtc_cmos 00:05: setting system clock to 2017-02-08 10:05:27 UTC (1486548327)
[    1.672411] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.672412] EDD information not available.
[    1.672494] PM: Hibernation image not present or could not be loaded.
[    1.672567] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
[    1.728108] usb 1-3: new high-speed USB device number 2 using ehci-pci
[    1.800330] ata2.00: ATAPI: HL-DT-STDVD-ROM GDR8162B, 0017, max UDMA/33
[    1.800336] ata2.01: ATAPI: _NEC DVD_RW ND-2500A, 1.9A, max UDMA/33
[    1.808322] ata2.00: configured for UDMA/33
[    1.816402] ata2.01: configured for UDMA/33
[    1.820220] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8162B 0017 PQ: 0 ANSI: 5
[    1.864129] sr 1:0:0:0: [sr0] scsi3-mmc drive: 32x/32x cd/rw xa/form2 cdda tray
[    1.864133] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.864361] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.864515] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    1.864713] scsi 1:0:1:0: CD-ROM            _NEC     DVD_RW ND-2500A  1.9A PQ: 0 ANSI: 5
[    1.880220] sr 1:0:1:0: [sr1] scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[    1.880352] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.880534] sr 1:0:1:0: Attached scsi generic sg3 type 5
[    1.881626] Freeing unused kernel memory: 988K (ccc21000 - ccd18000)
[    1.881671] Write protecting the kernel text: 8240k
[    1.881768] Write protecting the kernel read-only data: 3328k
[    1.887255] usb 1-3: New USB device found, idVendor=05e3, idProduct=0760
[    1.887259] usb 1-3: New USB device strings: Mfr=0, Product=3, SerialNumber=4
[    1.887261] usb 1-3: Product: Flash Reader
[    1.887263] usb 1-3: SerialNumber: 02692
[    1.913589] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    1.913749] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    1.913776] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[    1.915153] random: udevadm: uninitialized urandom read (16 bytes read)
[    1.915494] random: udevadm: uninitialized urandom read (16 bytes read)
[    1.916660] random: udevadm: uninitialized urandom read (16 bytes read)
[    1.916809] random: udevadm: uninitialized urandom read (16 bytes read)
[    1.917468] random: udevadm: uninitialized urandom read (16 bytes read)
[    1.917618] random: udevadm: uninitialized urandom read (16 bytes read)
[    1.917733] random: udevadm: uninitialized urandom read (16 bytes read)
[    2.032873] agpgart-sis 0000:00:00.0: SiS chipset [1039/0648]
[    2.067986] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xd0000000
[    2.129058] firewire_ohci 0000:00:02.3: found PCI INT B -> IRQ 11
[    2.129069] firewire_ohci 0000:00:02.3: sharing IRQ 11 with 0000:00:02.1
[    2.131777] tulip: Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[    2.139455] usb-storage 1-3:1.0: USB Mass Storage device detected
[    2.146071] [drm] Initialized drm 1.1.0 20060810
[    2.157691] scsi host2: usb-storage 1-3:1.0
[    2.157885] usbcore: registered new interface driver usb-storage
[    2.181819] usbcore: registered new interface driver uas
[    2.188251] firewire_ohci 0000:00:02.3: added OHCI v1.0 device as card 0, 4 IR + 6 IT contexts, quirks 0x0
[    2.188375] tulip 0000:00:06.0: found PCI INT A -> IRQ 11
[    2.188397] tulip 0000:00:06.0: sharing IRQ 11 with 0000:00:0e.0
[    2.188434] tulip: tulip_init_one: Enabled WOL support for AN983B
[    2.188983] tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1
[    2.201520] net eth0: ADMtek Comet rev 17 at Port 0x1000, 00:30:05:63:2b:9e, IRQ 11
[    2.240174] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2e203148d5a, max_idle_ns: 440795292336 ns
[    2.240270] clocksource: Switched to clocksource tsc
[    2.354852] tulip 0000:00:06.0 enp0s6: renamed from eth0
[    2.469038] random: fast init done
[    2.720436] firewire_core 0000:00:02.3: created device fw0: GUID 00300531000c604f, S400
[    3.169942] scsi 2:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0125 PQ: 0 ANSI: 0
[    3.171040] scsi 2:0:0:1: Direct-Access     Generic  STORAGE DEVICE   0125 PQ: 0 ANSI: 0
[    3.172181] scsi 2:0:0:2: Direct-Access     Generic  STORAGE DEVICE   0125 PQ: 0 ANSI: 0
[    3.173287] scsi 2:0:0:3: Direct-Access     Generic  STORAGE DEVICE   0125 PQ: 0 ANSI: 0
[    3.174971] sd 2:0:0:0: Attached scsi generic sg4 type 0
[    3.175324] sd 2:0:0:1: Attached scsi generic sg5 type 0
[    3.175652] sd 2:0:0:2: Attached scsi generic sg6 type 0
[    3.176769] sd 2:0:0:3: Attached scsi generic sg7 type 0
[    3.189467] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[    3.191086] sd 2:0:0:1: [sdd] Attached SCSI removable disk
[    3.192708] sd 2:0:0:2: [sde] Attached SCSI removable disk
[    3.194329] sd 2:0:0:3: [sdf] Attached SCSI removable disk
[    3.350249] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input2
[    5.128909] random: crng init done
[    6.565437] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[    7.487336] ip_tables: (C) 2000-2006 Netfilter Core Team
[    7.584711] systemd[1]: systemd 231 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD +IDN)
[    7.584955] systemd[1]: Detected architecture x86.
[    7.594750] systemd[1]: Set hostname to <javier-D1675>.
[    8.542879] systemd[1]: Listening on udev Control Socket.
[    8.543148] systemd[1]: Listening on fsck to fsckd communication Socket.
[    8.543491] systemd[1]: Created slice System Slice.
[    8.543772] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    8.543981] systemd[1]: Created slice User and Session Slice.
[    8.544071] systemd[1]: Listening on udev Kernel Socket.
[    8.544405] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    9.302188] lp: driver loaded but no devices found
[    9.328183] ppdev: user-space parallel port driver
[    9.551614] parport_pc 00:14: reported by Plug and Play BIOS
[    9.551680] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[    9.648938] lp0: using parport0 (interrupt-driven).
[   14.197628] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro
[   14.289702] systemd-journald[311]: Received request to flush runtime journal from PID 1
[   14.822645] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
[   14.872287] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.064235] media: Linux media interface: v0.10
[   15.388236] Linux video capture interface: v2.00
[   15.884743] PCI: setting IRQ 5 as level-triggered
[   15.884751] snd_ca0106 0000:00:0c.0: found PCI INT A -> IRQ 5
[   15.884807] snd_ca0106 0000:00:0c.0: Model 100a Rev 00000000 Serial 100a1102
[   16.317696] saa7134: saa7130/34: v4l2 driver version 0, 2, 17 loaded
[   16.317794] saa7134 0000:00:0e.0: found PCI INT A -> IRQ 11
[   16.317814] saa7134 0000:00:0e.0: sharing IRQ 11 with 0000:00:06.0
[   16.317827] saa7134: saa7134[0]: found at 0000:00:0e.0, rev: 1, irq: 11, latency: 254, mmio: 0xd4005400
[   16.317833] saa7134: saa7134[0]: subsystem: 11bd:002b, board: Pinnacle PCTV Stereo (saa7134) [card=26,autodetected]
[   16.317858] saa7134: saa7134[0]: board init: gpio is 0
[   16.540489] Adding 7999484k swap on /dev/sdb5.  Priority:-1 extents:1 across:7999484k FS
[   16.925333] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
[   16.932716] saa7134: i2c eeprom 00: bd 11 2b 00 f8 f8 1c 00 43 43 a9 1c 55 d2 b2 92
[   16.932720] saa7134: i2c eeprom 10: 00 00 19 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[   16.932721] saa7134: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 53 ff ff ff ff
[   16.932722] saa7134: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.932723] saa7134: i2c eeprom 40: ff 07 00 c0 86 ff 01 01 ff ff ff ff ff ff ff ff
[   16.932724] saa7134: i2c eeprom 50: 0c 22 17 09 02 14 d2 c3 ff ff ff ff ff ff ff ff
[   16.932725] saa7134: i2c eeprom 60: 03 03 19 71 fb ff ff ff ff ff ff ff ff ff ff ff
[   16.932726] saa7134: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.932727] saa7134: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.932728] saa7134: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.932729] saa7134: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.932730] saa7134: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.932731] saa7134: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.932732] saa7134: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.932733] saa7134: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.932734] saa7134: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.253679] tda9887 1-0043: creating new instance
[   17.253682] tda9887 1-0043: tda988[5/6/7] found
[   17.266551] tuner 1-0043: Tuner 74 found with type(s) Radio TV.
[   17.313570] Chip ID is not zero. It is not a TEA5767
[   17.313590] tuner 1-0060: Tuner -1 found with type(s) Radio TV.
[   17.364261] mt20xx 1-0060: microtune: companycode=3cbf part=42 rev=2f
[   17.416413] mt20xx 1-0060: microtune MT2050 found, OK
[   17.553650] saa7134: saa7134[0]: registered device video0 [v4l2]
[   17.553713] saa7134: saa7134[0]: registered device vbi0
[   17.573276] saa7134_alsa: saa7134 ALSA driver for DMA sound loaded
[   17.573326] saa7134_alsa: saa7134[0]/alsa: saa7134[0] at 0xd4005400 irq 11 registered as card -2
[   17.587077] audit: type=1400 audit(1486548343.412:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=711 comm="apparmor_parser"
[   17.587090] audit: type=1400 audit(1486548343.412:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//chromium" pid=711 comm="apparmor_parser"
[   17.598833] audit: type=1400 audit(1486548343.424:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=713 comm="apparmor_parser"
[   17.598849] audit: type=1400 audit(1486548343.424:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=713 comm="apparmor_parser"
[   17.598856] audit: type=1400 audit(1486548343.424:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=713 comm="apparmor_parser"
[   17.598864] audit: type=1400 audit(1486548343.424:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=713 comm="apparmor_parser"
[   17.655517] audit: type=1400 audit(1486548343.480:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=714 comm="apparmor_parser"
[   17.655532] audit: type=1400 audit(1486548343.480:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince//sanitized_helper" pid=714 comm="apparmor_parser"
[   17.655540] audit: type=1400 audit(1486548343.480:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=714 comm="apparmor_parser"
[   17.655548] audit: type=1400 audit(1486548343.480:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer//sanitized_helper" pid=714 comm="apparmor_parser"
[   22.194684] IPv6: ADDRCONF(NETDEV_UP): enp0s6: link is not ready
[   25.315908] tulip 0000:00:06.0 enp0s6: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[   25.315921] net enp0s6: Setting full-duplex based on MII#1 link partner capability of c5e1
[ 1628.512061] perf: interrupt took too long (2521 > 2500), lowering kernel.perf_event_max_sample_rate to 79250
[ 2792.076883] perf: interrupt took too long (3153 > 3151), lowering kernel.perf_event_max_sample_rate to 63250
[ 4391.045367] perf: interrupt took too long (3958 > 3941), lowering kernel.perf_event_max_sample_rate to 50500
[ 6934.557799] perf: interrupt took too long (4973 > 4947), lowering kernel.perf_event_max_sample_rate to 40000
[11582.033601] perf: interrupt took too long (6219 > 6216), lowering kernel.perf_event_max_sample_rate to 32000
[27291.022566] perf: interrupt took too long (7774 > 7773), lowering kernel.perf_event_max_sample_rate to 25500

```

---

### Post by cariboo on 2017-02-09
You may want to try a different cable from the graphics card to the monitor, as you are getting an error message, that needs to be fixed before you can do anything else:

```
xrandr: Failed to get size of gamma for output default
Screen 0: **minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768**
default connected 1024x768+0+0 0mm x 0mm
   1024x768      76.00* 
```

---

