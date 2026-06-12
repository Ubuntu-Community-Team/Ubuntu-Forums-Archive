---
title: "microphone not working dell inspiron 6000"
date: 2012-01-21
forum: Hardware
---

### Post by niekas on 2012-01-21
Could someone help with my microphone problem in ubuntu. I have dell  inspiron 6000. Microphone works fine when booted in windows on the same  machine. Tried a lot of suggestions screwed settings. Reseted sound  settings to defaults again. I'm lost.

Microphone is regular not USB.

---

### Post by niekas on 2012-01-23
bump

---

### Post by madvinegar on 2012-01-23
Try to switch off one of your two speakers by setting the sound balance far left or far right.
If your mic will work, then download and install from ubuntu software center the "pulse audio volume control".

Open it. Go to the 4th tab (input devices), press the little button with a lock on it (so as to unlock the two channels from moving together), and switch off completely one of the two channels.

You can then set back your overall sound balance as it was before so as to get sound from both of your speakers.

This should do the trick.

---

### Post by niekas on 2012-01-23
Speaker balance trick didn't work.

---

### Post by madvinegar on 2012-01-23
Then download from ubuntu software center ```
gnome alsa mixer
``` and see if any option regarding the Mic etc is set to mute, and unmute it.

---

### Post by niekas on 2012-01-23
> **madvinegar said:**
> Then download from ubuntu software center ```
gnome alsa mixer
``` and see if any option regarding the Mic etc is set to mute, and unmute it.
None of them set to mute.

---

### Post by madvinegar on 2012-01-23
In your sound options, have you tried setting the audio to "duplex"?
Also, dowloand pulse audio control and check there as well to see if everything is unmuted etc.

---

### Post by niekas on 2012-01-23
> **madvinegar said:**
> In your sound options, have you tried setting the audio to "duplex"?
Also, dowloand pulse audio control and check there as well to see if everything is unmuted etc.
Sound options is set to "analog stereo duplex". Other options available are Off, Analog Stereo Input and Analog Stereo Output. I believe I tried setting all of them. 

There is nothing muted in pulse audio control.

---

### Post by madvinegar on 2012-01-23
Also,

Go into terminal and type

```
alsamixer
```

Change the option all the way on the right that is labeled "Digital" but above it says "Analog". Change that option to say Digital.

---

### Post by niekas on 2012-01-23
> **madvinegar said:**
> Also,

Go into terminal and type

```
alsamixer
```Change the option all the way on the right that is labeled "Digital" but above it says "Analog". Change that option to say Digital.


There is no option labeled Digital. All the way on the right there is option labeled "mono out". It has selected option "Mix". another option available is "Mic".

---

### Post by niekas on 2012-01-24
bump

---

### Post by madvinegar on 2012-01-24
I am trying to figure out what is going on.

There is one possibility that the pulse audio system is creating the problem and you would be better changing everything to the alsa audio system.

You can open terminal and write:

```
gstreamer-properties
```

From the window that will open, on the first tab (audio) change both pluging options (for default output and default input) to ALSA.

Especially, try with the "input" all the available options in "devices" and see if you can get it to work!

Let me know if you had any luck.

---

### Post by niekas on 2012-01-24
I changed to Alsa (it was set to custom before)

and tried all following options:
Default
Intel ICH6
Intel ICH6 - MIC2 ADC (error in sound recorder if try to record something about verifying settings and missing plugins)
Intel ICH6 - ADC2 (Same error)

Only with default settings there is "record from input" drop down box in sound recorder with the only option available "Capture". With other options there "record from input" is missing all together.

---

### Post by madvinegar on 2012-01-24
Is your mic recognised by the system?

In terminal if you write

```
lspci
```

can you see it in the list? Please post the results.



Also, plug out the mic and write
```

sudo dmesg -c
```

and then plug it it again and write

```
dmesg
```

Please post the results as well.

---

### Post by niekas on 2012-01-24
lspci. It doesn't look like it has anything about microphones

```
:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

```

```
:~$ sudo dmesg -c
[sudo] password for adm: 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-15-generic (buildd@zirconium) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 (Ubuntu 3.0.0-15.26-generic 3.0.13)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Disabled fast string operations
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004ffd3800 (usable)
[    0.000000]  BIOS-e820: 000000004ffd3800 - 0000000050000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: Dell Inc. Inspiron 6000                   /0X9238, BIOS A09 09/28/2005
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x4ffd3 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 040000000 mask FF0000000 write-back
[    0.000000]   2 base 0FEDA0000 mask FFFFE0000 write-through
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 365ea000 - 372ed000
[    0.000000] ACPI: RSDP 000fc9b0 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 4ffd3fd3 00040 (v01 DELL    CPi R   27D5091C ASL  00000061)
[    0.000000] ACPI: FACP 4ffd4c00 00074 (v01 DELL    CPi R   27D5091C ASL  00000061)
[    0.000000] ACPI: DSDT 4ffd5800 03107 (v01 INT430 SYSFexxx 00001001 MSFT 0100000E)
[    0.000000] ACPI: FACS 4ffe4000 00040
[    0.000000] ACPI: APIC 4ffd5400 00068 (v01 DELL    CPi R   27D5091C ASL  00000047)
[    0.000000] ACPI: MCFG 4ffd53c0 0003E (v16 DELL    CPi R   27D5091C ASL  00000061)
[    0.000000] ACPI: BOOT 4ffd4fc0 00028 (v01 DELL    CPi R   27D5091C ASL  00000061)
[    0.000000] ACPI: SSDT 4ffd43e6 0023E (v01  PmRef  Cpu0Ist 00003000 INTL 20030522)
[    0.000000] ACPI: SSDT 4ffd420e 001D8 (v01  PmRef  Cpu0Cst 00003001 INTL 20030522)
[    0.000000] ACPI: SSDT 4ffd4013 001FB (v01  PmRef    CpuPm 00003000 INTL 20030522)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 391MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0004ffd3
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0004ffd3
[    0.000000] On node 0 totalpages: 327522
[    0.000000] free_area_init_node: node 0, pgdat c17b5400, node_mem_map f5bea200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 784 pages used for memmap
[    0.000000]   HighMem zone: 99525 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 50000000:90000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @f5400000 s26240 r0 d22912 u2097152
[    0.000000] pcpu-alloc: s26240 r0 d22912 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 324962
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-15-generic root=UUID=674fdbba-637f-4aa1-8c4f-da1e409fb6ba ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5241904 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0004ffd3)
[    0.000000] Memory: 1270920k/1310540k available (5336k kernel code, 39168k reserved, 2599k data, 696k init, 401236k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc17c1000 - 0xc186f000   ( 696 kB)
[    0.000000]       .data : 0xc1536144 - 0xc17c0080   (2599 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1536144   (5336 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f5008000 soft=f500a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.304 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.60 BogoMIPS (lpj=6385216)
[    0.004011] pid_max: default: 32768 minimum: 301
[    0.004044] Security Framework initialized
[    0.004077] AppArmor: AppArmor initialized
[    0.004080] Yama: becoming mindful.
[    0.004160] Mount-cache hash table entries: 512
[    0.004369] Initializing cgroup subsys cpuacct
[    0.004379] Initializing cgroup subsys memory
[    0.004392] Initializing cgroup subsys devices
[    0.004395] Initializing cgroup subsys freezer
[    0.004398] Initializing cgroup subsys net_cls
[    0.004402] Initializing cgroup subsys blkio
[    0.004414] Initializing cgroup subsys perf_event
[    0.004453] Disabled fast string operations
[    0.004463] mce: CPU supports 5 MCE banks
[    0.004476] CPU0: Thermal monitoring enabled (TM1)
[    0.004740] SMP alternatives: switching to UP code
[    0.013964] ACPI: Core revision 20110413
[    0.019006] ftrace: allocating 24882 entries in 49 pages
[    0.020082] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024276] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.063975] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 08
[    0.064003] Performance Events: p6 PMU driver.
[    0.064003] ... version:                0
[    0.064003] ... bit width:              32
[    0.064003] ... generic registers:      2
[    0.064003] ... value mask:             00000000ffffffff
[    0.064003] ... max period:             000000007fffffff
[    0.064003] ... fixed-purpose events:   0
[    0.064003] ... event mask:             0000000000000003
[    0.064003] Brought up 1 CPUs
[    0.064003] Total of 1 processors activated (3192.60 BogoMIPS).
[    0.064003] devtmpfs: initialized
[    0.064875] print_constraints: dummy: 
[    0.064907] Time: 12:41:45  Date: 01/24/12
[    0.064961] NET: Registered protocol family 16
[    0.065114] EISA bus registered
[    0.065125] ACPI: bus type pci registered
[    0.065206] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.065211] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.065213] PCI: Using MMCONFIG for extended config space
[    0.065216] PCI: Using configuration type 1 for base access
[    0.065224] dmi type 0xB1 record - unknown flag
[    0.066562] bio: create slab <bio-0> at 0
[    0.067561] ACPI: EC: Look up EC in DSDT
[    0.072244] ACPI: Interpreter enabled
[    0.072251] ACPI: (supports S0 S3 S4 S5)
[    0.072275] ACPI: Using IOAPIC for interrupt routing
[    0.093610] ACPI: No dock devices found.
[    0.093613] HEST: Table not found.
[    0.093619] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.101743] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.116725] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.116730] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.116734] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.116739] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.116743] pci_root PNP0A03:00: host bridge window [mem 0x50000000-0xdfffffff] (ignored)
[    0.116747] pci_root PNP0A03:00: host bridge window [mem 0xf0007000-0xf0007fff] (ignored)
[    0.116751] pci_root PNP0A03:00: host bridge window [mem 0xf000c000-0xfebfffff] (ignored)
[    0.116755] pci_root PNP0A03:00: host bridge window [mem 0xfec10000-0xfed1ffff] (ignored)
[    0.116759] pci_root PNP0A03:00: host bridge window [mem 0xfee10000-0xffafffff] (ignored)
[    0.116773] pci 0000:00:00.0: [8086:2590] type 0 class 0x000600
[    0.116820] pci 0000:00:01.0: [8086:2591] type 1 class 0x000604
[    0.116856] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.116861] pci 0000:00:01.0: PME# disabled
[    0.116916] pci 0000:00:1d.0: [8086:2658] type 0 class 0x000c03
[    0.116971] pci 0000:00:1d.0: reg 20: [io  0xbf80-0xbf9f]
[    0.117011] pci 0000:00:1d.1: [8086:2659] type 0 class 0x000c03
[    0.117066] pci 0000:00:1d.1: reg 20: [io  0xbf60-0xbf7f]
[    0.117105] pci 0000:00:1d.2: [8086:265a] type 0 class 0x000c03
[    0.117161] pci 0000:00:1d.2: reg 20: [io  0xbf40-0xbf5f]
[    0.117200] pci 0000:00:1d.3: [8086:265b] type 0 class 0x000c03
[    0.117255] pci 0000:00:1d.3: reg 20: [io  0xbf20-0xbf3f]
[    0.117306] pci 0000:00:1d.7: [8086:265c] type 0 class 0x000c03
[    0.117330] pci 0000:00:1d.7: reg 10: [mem 0xffa80800-0xffa80bff]
[    0.117416] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.117422] pci 0000:00:1d.7: PME# disabled
[    0.117446] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.117527] pci 0000:00:1e.2: [8086:266e] type 0 class 0x000401
[    0.117548] pci 0000:00:1e.2: reg 10: [io  0xed00-0xedff]
[    0.117561] pci 0000:00:1e.2: reg 14: [io  0xec40-0xec7f]
[    0.117575] pci 0000:00:1e.2: reg 18: [mem 0xdffffe00-0xdfffffff]
[    0.117587] pci 0000:00:1e.2: reg 1c: [mem 0xdffffd00-0xdffffdff]
[    0.117639] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.117645] pci 0000:00:1e.2: PME# disabled
[    0.117666] pci 0000:00:1e.3: [8086:266d] type 0 class 0x000703
[    0.117687] pci 0000:00:1e.3: reg 10: [io  0xee00-0xeeff]
[    0.117700] pci 0000:00:1e.3: reg 14: [io  0xec80-0xecff]
[    0.117770] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.117776] pci 0000:00:1e.3: PME# disabled
[    0.117800] pci 0000:00:1f.0: [8086:2641] type 0 class 0x000601
[    0.117911] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.117921] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.117929] pci 0000:00:1f.0: quirk: [io  0x1080-0x10bf] claimed by ICH6 GPIO
[    0.117935] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0900-097f
[    0.117961] pci 0000:00:1f.2: [8086:2653] type 0 class 0x000101
[    0.117983] pci 0000:00:1f.2: reg 10: [io  0x01f0-0x01f7]
[    0.117996] pci 0000:00:1f.2: reg 14: [io  0x03f4-0x03f7]
[    0.118009] pci 0000:00:1f.2: reg 18: [io  0x0170-0x0177]
[    0.118021] pci 0000:00:1f.2: reg 1c: [io  0x0374-0x0377]
[    0.118034] pci 0000:00:1f.2: reg 20: [io  0xbfa0-0xbfaf]
[    0.118078] pci 0000:00:1f.2: PME# supported from D3hot
[    0.118083] pci 0000:00:1f.2: PME# disabled
[    0.118138] pci 0000:01:00.0: [1002:5460] type 0 class 0x000300
[    0.118151] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xd7ffffff pref]
[    0.118160] pci 0000:01:00.0: reg 14: [io  0xde00-0xdeff]
[    0.118169] pci 0000:01:00.0: reg 18: [mem 0xdfdf0000-0xdfdfffff]
[    0.118196] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.118216] pci 0000:01:00.0: supports D1 D2
[    0.118228] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.118238] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.118242] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.118247] pci 0000:00:01.0:   bridge window [mem 0xdfd00000-0xdfefffff]
[    0.118252] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd7ffffff pref]
[    0.118297] pci 0000:03:00.0: [14e4:170c] type 0 class 0x000200
[    0.118319] pci 0000:03:00.0: reg 10: [mem 0xdfcfe000-0xdfcfffff]
[    0.118402] pci 0000:03:00.0: supports D1 D2
[    0.118405] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.118411] pci 0000:03:00.0: PME# disabled
[    0.118434] pci 0000:03:01.0: [1180:0476] type 2 class 0x000607
[    0.118459] pci 0000:03:01.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.118484] pci 0000:03:01.0: supports D1 D2
[    0.118487] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.118493] pci 0000:03:01.0: PME# disabled
[    0.118516] pci 0000:03:01.1: [1180:0552] type 0 class 0x000c00
[    0.118540] pci 0000:03:01.1: reg 10: [mem 0xdfcfc800-0xdfcfcfff]
[    0.118629] pci 0000:03:01.1: supports D1 D2
[    0.118632] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.118638] pci 0000:03:01.1: PME# disabled
[    0.118661] pci 0000:03:01.2: [1180:0822] type 0 class 0x000805
[    0.118684] pci 0000:03:01.2: reg 10: [mem 0xdfcfc700-0xdfcfc7ff]
[    0.118773] pci 0000:03:01.2: supports D1 D2
[    0.118777] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.118783] pci 0000:03:01.2: PME# disabled
[    0.118817] pci 0000:03:03.0: [8086:4220] type 0 class 0x000280
[    0.118843] pci 0000:03:03.0: reg 10: [mem 0xdfcfd000-0xdfcfdfff]
[    0.118944] pci 0000:03:03.0: PME# supported from D0 D3hot D3cold
[    0.118951] pci 0000:03:03.0: PME# disabled
[    0.119010] pci 0000:00:1e.0: PCI bridge to [bus 03-04] (subtractive decode)
[    0.119017] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.119023] pci 0000:00:1e.0:   bridge window [mem 0xdfc00000-0xdfcfffff]
[    0.119032] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.119037] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.119040] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.119088] pci_bus 0000:04: [bus 04-07] partially hidden behind transparent bridge 0000:03 [bus 03-04]
[    0.119103] pci_bus 0000:00: on NUMA node 0
[    0.119107] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.119479] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.119540] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.119677]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.119682]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.119685] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.127859] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.128031] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.128127] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    0.128221] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
[    0.128301] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.128388] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.128472] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.128605] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.128610] vgaarb: loaded
[    0.128613] vgaarb: bridge control possible 0000:01:00.0
[    0.128912] SCSI subsystem initialized
[    0.128962] libata version 3.00 loaded.
[    0.129020] usbcore: registered new interface driver usbfs
[    0.129036] usbcore: registered new interface driver hub
[    0.129067] usbcore: registered new device driver usb
[    0.129181] PCI: Using ACPI for IRQ routing
[    0.139143] PCI: pci_cache_line_size set to 64 bytes
[    0.139219] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.139223] reserve RAM buffer: 000000004ffd3800 - 000000004fffffff 
[    0.139351] NetLabel: Initializing
[    0.139354] NetLabel:  domain hash size = 128
[    0.139356] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.139370] NetLabel:  unlabeled traffic allowed by default
[    0.139565] hpet clockevent registered
[    0.139570] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.139579] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.139585] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.144029] Switching to clocksource hpet
[    0.147998] Switched to NOHz mode on CPU #0
[    0.153251] AppArmor: AppArmor Filesystem Enabled
[    0.153296] pnp: PnP ACPI init
[    0.153322] ACPI: bus type pnp registered
[    0.162976] pnp 00:00: [mem 0x00000000-0x0009fbff]
[    0.162980] pnp 00:00: [mem 0x0009fc00-0x0009ffff]
[    0.162983] pnp 00:00: [mem 0x000c0000-0x000cffff]
[    0.162987] pnp 00:00: [mem 0x000e0000-0x000fffff]
[    0.162990] pnp 00:00: [mem 0x00100000-0x4ffd37ff]
[    0.162994] pnp 00:00: [mem 0x4ffd3800-0x4fffffff]
[    0.162997] pnp 00:00: [mem 0xfeda0000-0xfedfffff]
[    0.163000] pnp 00:00: [mem 0xffb00000-0xffffffff]
[    0.163003] pnp 00:00: [mem 0xfec00000-0xfec0ffff]
[    0.163007] pnp 00:00: [mem 0xfee00000-0xfee0ffff]
[    0.163017] pnp 00:00: [mem 0xfed20000-0xfed9ffff]
[    0.163020] pnp 00:00: [mem 0xf0000000-0xf0003fff]
[    0.163023] pnp 00:00: [mem 0xf0004000-0xf0004fff]
[    0.163027] pnp 00:00: [mem 0xf0005000-0xf0005fff]
[    0.163030] pnp 00:00: [mem 0xf0006000-0xf0006fff]
[    0.163033] pnp 00:00: [mem 0xf0008000-0xf000bfff]
[    0.163037] pnp 00:00: [mem 0xe0000000-0xefffffff]
[    0.163126] system 00:00: [mem 0x00000000-0x0009fbff] could not be reserved
[    0.163130] system 00:00: [mem 0x0009fc00-0x0009ffff] could not be reserved
[    0.163135] system 00:00: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.163139] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.163144] system 00:00: [mem 0x00100000-0x4ffd37ff] could not be reserved
[    0.163148] system 00:00: [mem 0x4ffd3800-0x4fffffff] has been reserved
[    0.163152] system 00:00: [mem 0xfeda0000-0xfedfffff] has been reserved
[    0.163156] system 00:00: [mem 0xffb00000-0xffffffff] has been reserved
[    0.163161] system 00:00: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.163165] system 00:00: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.163169] system 00:00: [mem 0xfed20000-0xfed9ffff] has been reserved
[    0.163173] system 00:00: [mem 0xf0000000-0xf0003fff] has been reserved
[    0.163178] system 00:00: [mem 0xf0004000-0xf0004fff] has been reserved
[    0.163182] system 00:00: [mem 0xf0005000-0xf0005fff] has been reserved
[    0.163186] system 00:00: [mem 0xf0006000-0xf0006fff] has been reserved
[    0.163190] system 00:00: [mem 0xf0008000-0xf000bfff] has been reserved
[    0.163194] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.163200] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.170704] pnp 00:01: [bus 00-ff]
[    0.170708] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.170712] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.170715] pnp 00:01: [io  0x0d00-0xffff window]
[    0.170719] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.170722] pnp 00:01: [mem 0x000d0000-0x000dffff window]
[    0.170726] pnp 00:01: [mem 0x50000000-0xdfffffff window]
[    0.170729] pnp 00:01: [mem 0xf0007000-0xf0007fff window]
[    0.170733] pnp 00:01: [mem 0xf000c000-0xfebfffff window]
[    0.170736] pnp 00:01: [mem 0xfec10000-0xfed1ffff window]
[    0.170740] pnp 00:01: [mem 0xfeda0000-0xfed9ffff window disabled]
[    0.170744] pnp 00:01: [mem 0xfee10000-0xffafffff window]
[    0.170827] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.170852] pnp 00:02: [io  0x0092]
[    0.170855] pnp 00:02: [io  0x00b2]
[    0.170858] pnp 00:02: [io  0x0020-0x0021]
[    0.170862] pnp 00:02: [io  0x00a0-0x00a1]
[    0.170865] pnp 00:02: [irq 0 disabled]
[    0.170868] pnp 00:02: [io  0x04d0-0x04d1]
[    0.170872] pnp 00:02: [io  0x1000-0x1005]
[    0.170875] pnp 00:02: [io  0x1008-0x100f]
[    0.170891] pnp 00:02: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.170896] pnp 00:02: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.170939] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.170944] system 00:02: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.170968] pnp 00:03: [io  0xf400-0xf4fe]
[    0.170971] pnp 00:03: [io  0x0086]
[    0.170974] pnp 00:03: [io  0x00b3]
[    0.170977] pnp 00:03: [io  0x1006-0x1007]
[    0.170980] pnp 00:03: [io  0x100a-0x1059]
[    0.170983] pnp 00:03: [io  0x1060-0x107f]
[    0.170986] pnp 00:03: [io  0x1080-0x10bf]
[    0.170989] pnp 00:03: [io  0x10c0-0x10df]
[    0.170992] pnp 00:03: [io  0x10e0-0x10ff]
[    0.171008] pnp 00:03: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.171013] pnp 00:03: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.171018] pnp 00:03: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.171062] system 00:03: [io  0xf400-0xf4fe] has been reserved
[    0.171067] system 00:03: [io  0x1080-0x10bf] has been reserved
[    0.171071] system 00:03: [io  0x10c0-0x10df] has been reserved
[    0.171075] system 00:03: [io  0x10e0-0x10ff] has been reserved
[    0.171079] system 00:03: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.171116] pnp 00:04: [irq 12]
[    0.171156] pnp 00:04: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.171179] pnp 00:05: [io  0x0060]
[    0.171182] pnp 00:05: [io  0x0064]
[    0.171185] pnp 00:05: [io  0x0062]
[    0.171188] pnp 00:05: [io  0x0066]
[    0.171195] pnp 00:05: [irq 1]
[    0.171228] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.171249] pnp 00:06: [io  0x0070-0x0071]
[    0.171256] pnp 00:06: [irq 8]
[    0.171259] pnp 00:06: [io  0x0072-0x0077]
[    0.171298] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.171322] pnp 00:07: [io  0x0061]
[    0.171325] pnp 00:07: [io  0x0063]
[    0.171327] pnp 00:07: [io  0x0065]
[    0.171330] pnp 00:07: [io  0x0067]
[    0.171364] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.171386] pnp 00:08: [io  0x002e-0x002f]
[    0.171389] pnp 00:08: [io  0x0900-0x090f]
[    0.171392] pnp 00:08: [io  0x0910-0x091f]
[    0.171395] pnp 00:08: [io  0x0920-0x092f]
[    0.171398] pnp 00:08: [io  0x0930-0x093f]
[    0.171402] pnp 00:08: [io  0x0940-0x097f]
[    0.171454] system 00:08: [io  0x0900-0x090f] has been reserved
[    0.171459] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.171462] system 00:08: [io  0x0920-0x092f] has been reserved
[    0.171466] system 00:08: [io  0x0930-0x093f] has been reserved
[    0.171470] system 00:08: [io  0x0940-0x097f] has been reserved
[    0.171475] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.171500] pnp 00:09: [dma 4]
[    0.171503] pnp 00:09: [io  0x0000-0x000f]
[    0.171506] pnp 00:09: [io  0x0080-0x0085]
[    0.171509] pnp 00:09: [io  0x0087-0x008f]
[    0.171512] pnp 00:09: [io  0x00c0-0x00df]
[    0.171515] pnp 00:09: [io  0x0010-0x001f]
[    0.171518] pnp 00:09: [io  0x0090-0x0091]
[    0.171521] pnp 00:09: [io  0x0093-0x009f]
[    0.171556] pnp 00:09: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.171581] pnp 00:0a: [io  0x00f0-0x00ff]
[    0.171589] pnp 00:0a: [irq 13]
[    0.171629] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.172102] pnp: PnP ACPI: found 11 devices
[    0.172105] ACPI: ACPI bus type pnp unregistered
[    0.172110] PnPBIOS: Disabled by ACPI PNP
[    0.208875] PCI: max bus depth: 2 pci_try_num: 3
[    0.208909] pci 0000:00:1e.0: BAR 15: assigned [mem 0x50000000-0x53ffffff pref]
[    0.208914] pci 0000:00:1e.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.208919] pci 0000:01:00.0: BAR 6: assigned [mem 0xdfd00000-0xdfd1ffff pref]
[    0.208924] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.208928] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.208933] pci 0000:00:01.0:   bridge window [mem 0xdfd00000-0xdfefffff]
[    0.208938] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd7ffffff pref]
[    0.208945] pci 0000:03:01.0: BAR 15: assigned [mem 0x50000000-0x53ffffff pref]
[    0.208951] pci 0000:03:01.0: BAR 16: assigned [mem 0x54000000-0x57ffffff]
[    0.208955] pci 0000:03:01.0: BAR 0: assigned [mem 0xdfc00000-0xdfc00fff]
[    0.208963] pci 0000:03:01.0: BAR 0: set to [mem 0xdfc00000-0xdfc00fff] (PCI address [0xdfc00000-0xdfc00fff])
[    0.208967] pci 0000:03:01.0: BAR 13: assigned [io  0x2000-0x20ff]
[    0.208971] pci 0000:03:01.0: BAR 14: assigned [io  0x2400-0x24ff]
[    0.208975] pci 0000:03:01.0: CardBus bridge to [bus 04-07]
[    0.208978] pci 0000:03:01.0:   bridge window [io  0x2000-0x20ff]
[    0.208985] pci 0000:03:01.0:   bridge window [io  0x2400-0x24ff]
[    0.208991] pci 0000:03:01.0:   bridge window [mem 0x50000000-0x53ffffff pref]
[    0.208998] pci 0000:03:01.0:   bridge window [mem 0x54000000-0x57ffffff]
[    0.209004] pci 0000:00:1e.0: PCI bridge to [bus 03-04]
[    0.209008] pci 0000:00:1e.0:   bridge window [io  0x2000-0x2fff]
[    0.209016] pci 0000:00:1e.0:   bridge window [mem 0xdfc00000-0xdfcfffff]
[    0.209022] pci 0000:00:1e.0:   bridge window [mem 0x50000000-0x53ffffff pref]
[    0.209050] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.209055] pci 0000:00:01.0: setting latency timer to 64
[    0.209064] pci 0000:00:1e.0: setting latency timer to 64
[    0.209073] pci 0000:03:01.0: enabling device (0000 -> 0003)
[    0.209083] pci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.209092] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.209095] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.209099] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.209103] pci_bus 0000:01: resource 1 [mem 0xdfd00000-0xdfefffff]
[    0.209107] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xd7ffffff pref]
[    0.209111] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.209114] pci_bus 0000:03: resource 1 [mem 0xdfc00000-0xdfcfffff]
[    0.209118] pci_bus 0000:03: resource 2 [mem 0x50000000-0x53ffffff pref]
[    0.209122] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.209125] pci_bus 0000:03: resource 5 [mem 0x00000000-0xffffffff]
[    0.209129] pci_bus 0000:04: resource 0 [io  0x2000-0x20ff]
[    0.209132] pci_bus 0000:04: resource 1 [io  0x2400-0x24ff]
[    0.209136] pci_bus 0000:04: resource 2 [mem 0x50000000-0x53ffffff pref]
[    0.209140] pci_bus 0000:04: resource 3 [mem 0x54000000-0x57ffffff]
[    0.209198] NET: Registered protocol family 2
[    0.209291] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.209598] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.210713] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.211404] TCP: Hash tables configured (established 131072 bind 65536)
[    0.211408] TCP reno registered
[    0.211414] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.211440] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.211626] NET: Registered protocol family 1
[    0.211770] pci 0000:01:00.0: Boot video device
[    0.211791] PCI: CLS 64 bytes, default 64
[    0.211888] Simple Boot Flag at 0x79 set to 0x1
[    0.212271] audit: initializing netlink socket (disabled)
[    0.212286] type=2000 audit(1327408905.212:1): initialized
[    0.241354] Trying to unpack rootfs image as initramfs...
[    0.288128] highmem bounce pool size: 64 pages
[    0.288137] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.308338] VFS: Disk quotas dquot_6.5.2
[    0.308440] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.309422] fuse init (API version 7.16)
[    0.309558] msgmni has been set to 1698
[    0.324354] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.324399] io scheduler noop registered
[    0.324402] io scheduler deadline registered
[    0.324423] io scheduler cfq registered (default)
[    0.324579] pcieport 0000:00:01.0: setting latency timer to 64
[    0.324620] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.324709] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.324744] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.325275] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.325733] ACPI: AC Adapter [AC] (on-line)
[    0.326776] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.327342] ACPI: Lid Switch [LID]
[    0.327404] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.327410] ACPI: Power Button [PBTN]
[    0.327467] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.327472] ACPI: Sleep Button [SBTN]
[    0.327508] ACPI: acpi_idle registered with cpuidle
[    0.327702] Marking TSC unstable due to TSC halts in idle
[    0.336607] thermal LNXTHERM:00: registered as thermal_zone0
[    0.336612] ACPI: Thermal Zone [THM] (53 C)
[    0.336640] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.336705] ERST: Table is not found!
[    0.336810] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.338402] serial 0000:00:1e.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.338411] serial 0000:00:1e.3: PCI INT B disabled
[    0.338558] Linux agpgart interface v0.103
[    0.352106] isapnp: Scanning for PnP cards...
[    0.358044] brd: module loaded
[    0.358876] loop: module loaded
[    0.359079] ata_piix 0000:00:1f.2: version 2.13
[    0.359096] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.359104] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.512125] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.516293] scsi0 : ata_piix
[    0.516475] scsi1 : ata_piix
[    0.517107] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.517111] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.517634] Fixed MDIO Bus: probed
[    0.517669] PPP generic driver version 2.4.2
[    0.517768] tun: Universal TUN/TAP device driver, 1.6
[    0.517771] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.517885] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.517913] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.517935] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.517941] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.517986] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.518025] ehci_hcd 0000:00:1d.7: debug port 1
[    0.521918] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.524960] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
[    0.584086] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.584345] hub 1-0:1.0: USB hub found
[    0.584353] hub 1-0:1.0: 8 ports detected
[    0.584468] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.584495] uhci_hcd: USB Universal Host Controller Interface driver
[    0.584570] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.584584] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.584589] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.584645] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.584681] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[    0.584849] hub 2-0:1.0: USB hub found
[    0.584855] hub 2-0:1.0: 2 ports detected
[    0.584929] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.584937] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.584942] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.584989] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.585038] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[    0.585195] hub 3-0:1.0: USB hub found
[    0.585201] hub 3-0:1.0: 2 ports detected
[    0.585286] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.585294] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.585299] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.585343] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.585383] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf40
[    0.585549] hub 4-0:1.0: USB hub found
[    0.585554] hub 4-0:1.0: 2 ports detected
[    0.585632] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.585640] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.585645] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.585704] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.585744] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000bf20
[    0.585907] hub 5-0:1.0: USB hub found
[    0.585913] hub 5-0:1.0: 2 ports detected
[    0.586062] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.596723] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.596738] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.596926] mousedev: PS/2 mouse device common for all mice
[    0.597139] rtc_cmos 00:06: RTC can wake from S4
[    0.597266] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.597300] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.597461] device-mapper: uevent: version 1.0.3
[    0.597581] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.597625] EISA: Probing bus 0 at eisa.0
[    0.597634] Cannot allocate resource for EISA slot 1
[    0.597637] Cannot allocate resource for EISA slot 2
[    0.597663] EISA: Detected 0 cards.
[    0.597677] cpufreq-nforce2: No nForce2 chipset.
[    0.597736] cpuidle: using governor ladder
[    0.597821] cpuidle: using governor menu
[    0.597824] EFI Variables Facility v0.08 2004-May-17
[    0.598186] TCP cubic registered
[    0.598381] NET: Registered protocol family 10
[    0.599122] NET: Registered protocol family 17
[    0.599149] Registering the dns_resolver key type
[    0.599177] Using IPI No-Shortcut mode
[    0.599282] PM: Hibernation image not present or could not be loaded.
[    0.599297] registered taskstats version 1
[    0.607095] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.684645] ata2.00: ATAPI: SONY DVD+/-RW DW-D56A, PDS7, max UDMA/33
[    0.688947] ata1.00: ATA-6: HTS726060M9AT00, MH4OA6EA, max UDMA/100
[    0.688952] ata1.00: 117210240 sectors, multi 8: LBA48 
[    0.688956] ata1.00: applying bridge limits
[    0.700618] ata2.00: configured for UDMA/33
[    0.704330] ACPI: Battery Slot [BAT0] (battery present)
[    0.704897] ata1.00: configured for UDMA/100
[    0.927491] usb 1-6: new high speed USB device number 2 using ehci_hcd
[    0.983661] isapnp: No Plug & Play device found
[    0.983866] scsi 0:0:0:0: Direct-Access     ATA      HTS726060M9AT00  MH4O PQ: 0 ANSI: 5
[    0.984137] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.984366] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    0.984436] sd 0:0:0:0: [sda] Write Protect is off
[    0.984441] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.984472] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.985129] scsi 1:0:0:0: CD-ROM            SONY     DVD+-RW DW-D56A  PDS7 PQ: 0 ANSI: 5
[    0.987458] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.987464] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.987597] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.987674] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.004397]  sda: sda1 sda2 sda3
[    1.004834] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.110989] Freeing initrd memory: 13324k freed
[    1.131232]   Magic number: 12:177:684
[    1.131314] mem full: hash matches
[    1.131400] rtc_cmos 00:06: setting system clock to 2012-01-24 12:41:46 UTC (1327408906)
[    1.131869] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.131872] EDD information not available.
[    1.132144] Freeing unused kernel memory: 696k freed
[    1.132495] Write protecting the kernel text: 5340k
[    1.132546] Write protecting the kernel read-only data: 2192k
[    1.153661] udevd[83]: starting version 173
[    1.337860] sdhci: Secure Digital Host Controller Interface driver
[    1.337864] sdhci: Copyright(c) Pierre Ossman
[    1.338153] sdhci-pci 0000:03:01.2: SDHCI controller found [1180:0822] (rev 17)
[    1.338174] sdhci-pci 0000:03:01.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    1.339211] mmc0: no vmmc regulator found
[    1.373544] usbcore: registered new interface driver uas
[    1.376469] Registered led device: mmc0::
[    1.383563] Initializing USB Mass Storage driver...
[    1.385671] mmc0: SDHCI controller on PCI [0000:03:01.2] using DMA
[    1.385709] b44 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.388755] scsi2 : usb-storage 1-6:1.0
[    1.392100] usbcore: registered new interface driver usb-storage
[    1.392104] USB Mass Storage support registered.
[    1.404070] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    1.404080] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    1.404088] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    1.438028] usb 5-1: new low speed USB device number 2 using uhci_hcd
[    1.456148] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    1.456180] b44: b44.c:v2.0
[    1.456219] firewire_ohci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.508237] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:12:3f:d8:46:c6
[    1.520106] firewire_ohci: Added fw-ohci device 0000:03:01.1, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
[    1.654488] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input4
[    1.654746] generic-usb 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.3-1/input0
[    1.654937] usbcore: registered new interface driver usbhid
[    1.654940] usbhid: USB HID core driver
[    2.020141] firewire_core: created device fw0: GUID 484fc0000a83d8e1, S400
[    2.388983] scsi 2:0:0:0: Direct-Access     WD       15EADS External  1.75 PQ: 0 ANSI: 4
[    2.392247] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.392331] sd 2:0:0:0: [sdb] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    2.392825] sd 2:0:0:0: [sdb] Write Protect is off
[    2.392830] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    2.393325] sd 2:0:0:0: [sdb] No Caching mode page present
[    2.393329] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    2.395077] sd 2:0:0:0: [sdb] No Caching mode page present
[    2.395081] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    2.397962]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 sdb8 sdb9 >
[    2.400204] sd 2:0:0:0: [sdb] No Caching mode page present
[    2.400209] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    2.400213] sd 2:0:0:0: [sdb] Attached SCSI disk
[    3.420992] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    5.997828] Adding 3905532k swap on /dev/sdb9.  Priority:-1 extents:1 across:3905532k 
[    6.091862] udevd[302]: starting version 173
[    7.094243] lp: driver loaded but no devices found
[    8.665820] intel_rng: FWH not detected
[    8.849527] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/LNXVIDEO:00/input/input5
[    8.849656] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    8.849708] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[    9.039371] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    9.173148] lib80211: common routines for IEEE802.11 drivers
[    9.173179] lib80211_crypt: registered algorithm 'NULL'
[    9.455759] [drm] Initialized drm 1.1.0 20060810
[    9.662773] cfg80211: Calling CRDA to update world regulatory domain
[    9.714609] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:0188]
[    9.840813] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
[    9.840819] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[    9.840825] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[    9.840837] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [io  0x2000-0x2fff]
[    9.840841] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: excluding 0x2000-0x20ff 0x2400-0x24ff
[    9.847069] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0xdfc00000-0xdfcfffff]
[    9.847074] pcmcia_socket pcmcia_socket0: cs: memory probe 0xdfc00000-0xdfcfffff: excluding 0xdfc00000-0xdfc0ffff 0xdfcf0000-0xdfcfffff
[    9.847091] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0x50000000-0x53ffffff pref]
[    9.847095] pcmcia_socket pcmcia_socket0: cs: memory probe 0x50000000-0x53ffffff: excluding 0x50000000-0x53ffffff
[    9.964500] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input6
[    9.982517] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input7
[   10.389517] [drm] radeon defaulting to kernel modesetting.
[   10.389522] [drm] radeon kernel modesetting enabled.
[   10.389607] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.389614] radeon 0000:01:00.0: setting latency timer to 64
[   10.390046] [drm] initializing kernel modesetting (RV380 0x1002:0x5460 0x1028:0x2003).
[   10.390066] [drm] register mmio base: 0xDFDF0000
[   10.390068] [drm] register mmio size: 65536
[   10.390219] [drm] Generation 2 PCI interface, using max accessible memory
[   10.390226] radeon 0000:01:00.0: VRAM: 128M 0x00000000D0000000 - 0x00000000D7FFFFFF (128M used)
[   10.390231] radeon 0000:01:00.0: GTT: 512M 0x00000000B0000000 - 0x00000000CFFFFFFF
[   10.390243] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.390246] [drm] Driver supports precise vblank timestamp query.
[   10.390289] radeon 0000:01:00.0: irq 41 for MSI/MSI-X
[   10.390296] radeon 0000:01:00.0: radeon: using MSI.
[   10.390323] [drm] radeon: irq initialized.
[   10.390937] [drm] Detected VRAM RAM=128M, BAR=128M
[   10.390943] [drm] RAM width 128bits DDR
[   10.395253] [TTM] Zone  kernel: Available graphics memory: 441852 kiB.
[   10.395257] [TTM] Zone highmem: Available graphics memory: 642470 kiB.
[   10.395260] [TTM] Initializing pool allocator.
[   10.395289] [drm] radeon: 128M of VRAM memory ready
[   10.395293] [drm] radeon: 512M of GTT memory ready.
[   10.395313] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   10.396361] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   10.398151] [drm] PCIE GART of 512M enabled (table at 0xD0040000).
[   10.398177] radeon 0000:01:00.0: WB enabled
[   10.398938] [drm] Loading R300 Microcode
[   10.429148] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   10.430918] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   10.431675] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   10.432325] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   10.433026] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xf0000-0xfffff
[   10.433096] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   10.433164] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   10.433236] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   10.768363] libipw: 802.11 data/management/control stack, git-1.1.13
[   10.768367] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   10.871579] cfg80211: World regulatory domain updated:
[   10.871583] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.871588] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.871592] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.871596] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.871600] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.871604] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.548723] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   11.548727] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   11.548859] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.548887] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   11.564926] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.564955] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   11.576778] [drm] radeon: ring at 0x00000000B0001000
[   11.576802] [drm] ring test succeeded in 1 usecs
[   11.577008] [drm] radeon: ib pool ready.
[   11.578748] [drm] ib test succeeded in 0 usecs
[   11.581251] [drm] Panel ID String: F6253154W02
[   11.581253]            
[   11.581256] [drm] Panel Size 1680x1050
[   11.592823] [drm] radeon legacy LVDS backlight initialized
[   11.593027] [drm] Radeon Display Connectors
[   11.593030] [drm] Connector 0:
[   11.593033] [drm]   VGA
[   11.593036] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   11.593038] [drm]   Encoders:
[   11.593041] [drm]     CRT1: INTERNAL_DAC1
[   11.593043] [drm] Connector 1:
[   11.593045] [drm]   LVDS
[   11.593047] [drm]   Encoders:
[   11.593049] [drm]     LCD1: INTERNAL_LVDS
[   11.593051] [drm] Connector 2:
[   11.593053] [drm]   S-video
[   11.593055] [drm]   Encoders:
[   11.593057] [drm]     TV1: INTERNAL_DAC2
[   11.603769] [drm] Radeon display connector VGA-1: No monitor connected or invalid EDID
[   11.603790] [drm] radeon: power management initialized
[   11.644259] [drm] fb mappable at 0xD00C0000
[   11.644262] [drm] vram apper at 0xD0000000
[   11.644264] [drm] size 7057408
[   11.644266] [drm] fb depth is 24
[   11.644268] [drm]    pitch is 6720
[   11.644460] fbcon: radeondrmfb (fb0) is primary device
[   11.645424] Console: switching to colour frame buffer device 210x65
[   11.645501] fb0: radeondrmfb frame buffer device
[   11.645504] drm: registered panic notifier
[   11.645514] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:00.0 on minor 0
[   11.670109] type=1400 audit(1327401717.034:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=579 comm="apparmor_parser"
[   11.670726] type=1400 audit(1327401717.034:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=579 comm="apparmor_parser"
[   11.671120] type=1400 audit(1327401717.034:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=579 comm="apparmor_parser"
[   11.671853] type=1400 audit(1327401717.034:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=580 comm="apparmor_parser"
[   11.672490] type=1400 audit(1327401717.038:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=580 comm="apparmor_parser"
[   11.672881] type=1400 audit(1327401717.038:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=580 comm="apparmor_parser"
[   12.358212] ipw2200: Radio Frequency Kill Switch is On:
[   12.358215] Kill switch must be turned off for wireless networking to work.
[   12.360194] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   12.360199] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.360203] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   12.360207] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.360211] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   12.360215] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.360218] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   12.360222] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.360226] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   12.360230] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.360233] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   12.360237] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.360241] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   12.360245] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.360248] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   12.360252] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.360264] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   12.360268] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.360272] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   12.360276] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.360279] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   12.360283] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   12.362696] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   12.412035] intel8x0_measure_ac97_clock: measured 52063 usecs (2509 samples)
[   12.412041] intel8x0: clocking to 48000
[   45.881948] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[   47.183948] type=1400 audit(1327401752.547:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=843 comm="apparmor_parser"
[   47.310303] type=1400 audit(1327401752.675:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=844 comm="apparmor_parser"
[   47.313789] type=1400 audit(1327401752.679:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=845 comm="apparmor_parser"
[   47.314628] type=1400 audit(1327401752.679:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=845 comm="apparmor_parser"
[   47.315028] type=1400 audit(1327401752.679:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=845 comm="apparmor_parser"
[   47.531334] type=1400 audit(1327401752.895:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=846 comm="apparmor_parser"
[   47.541249] type=1400 audit(1327401752.907:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=846 comm="apparmor_parser"
[   47.546278] type=1400 audit(1327401752.911:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=846 comm="apparmor_parser"
[   47.701178] type=1400 audit(1327401753.067:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=848 comm="apparmor_parser"
[   47.701849] type=1400 audit(1327401753.067:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=848 comm="apparmor_parser"
[   48.279132] ppdev: user-space parallel port driver
[   49.461855] init: failsafe main process (800) killed by TERM signal
[   49.499705] init: apport pre-start process (935) terminated with status 1
[   49.505187] init: apport post-stop process (977) terminated with status 1
[   49.577127] init: gdm main process (972) killed by TERM signal
[   51.908464] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   54.816202] b44 ssb0:0: eth0: Link is up at 100 Mbps, full duplex
[   54.816209] b44 ssb0:0: eth0: Flow control is off for TX and off for RX
[   54.816530] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   63.230623] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=0
[   64.784043] ipw2200: Failed to send POWER_MODE: Command timed out.
[   65.477349] init: plymouth-stop pre-start process (1486) terminated with status 1
[   65.600025] eth0: no IPv6 routers present
[   81.166577] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=0
[   82.204034] ipw2200: Failed to send POWER_MODE: Command timed out.
[  189.243084] process `skype' is using obsolete setsockopt SO_BSDCOMPAT

```

dmesg nothing displayed:

---

### Post by madvinegar on 2012-01-24
Can you try one more thing...

Go again to terminal and write

```
alsamixer
```

and navigate using the left-right keys and the letter "M" to unmute the Mic.
Actually check that all the values in the boxes under the bars are highlighted (if not, use the letter "M" on the keyboard to unmute them).

The values should be highlighted so as to be **un**muted. If the channel is muted, the box is grey.

---

### Post by niekas on 2012-01-24
I guess it was muted either mic boost or mic itself. I'm not sure. Now i can hear microphone working when it's plugged in. If i blow on it or rub - i can hear it in headphones. 

But i still cant get mic to work in sound recorder or skype.

---

### Post by madvinegar on 2012-01-24
At least we made some progress!

Now that we got it to work, try to check again all options in sound, i.e. in gnome alsa mixer, in pulse audio volume control, in your sound preferences (check all bars are set to high).

Finally do the trick I told you on one of the 1st posts, i.e. in pulse audo volume control (4th tab - input) set to zero one of the channels (i.e. the left one).

Also, it just could be that you have to plug the mic better or not plug it all the way etc...


P.s.: Have you made sure that in alsamixer, all the bars were set to high (100)? You can do that by using the up-down keys.

---

### Post by niekas on 2012-01-24
I tried all these options, but doesn't seem to work.

btw i noticed that in alsa mixer mix and mix mono are off 

If i select F4 (capture) in alsa mixer - mic is also off. 

Line, CD, Mic, Video, Phone, Aux, Mix, Mix mono are off
Active are:
3d control center, 3d control depth and Capture R -100 

In pulse audio input tab there are 5 available input devices:
Analog Microphone 1
Analog Microphone 2
Analog Line in
Analog Input (always selected: even if i select microphone 1 and reopen it will be selected)
Video

---

### Post by madvinegar on 2012-01-24
Then try again with 

```
gstreamer-properties
```

to change the input plugin to default or pulse audio and see if you get any better results.

---

### Post by madvinegar on 2012-01-24
Have you also checked this?:

> **madvinegar said:**
> 

P.s.: Have you made sure that in alsamixer, all the bars were set to high (100)? You can do that by using the up-down keys.

And this:

> **madvinegar said:**
> 
Also, it just could be that you have to plug the mic better or not plug it all the way in etc... 

---

### Post by niekas on 2012-01-24
All bars are set to high. Mic is pushed all the way through - it works live, except for apps like skype and sound recording.

---

### Post by madvinegar on 2012-01-24
So probably now we will have to check the settings of Skype and make sure that it is directed to the right mic.

I will check and revert...

---

### Post by madvinegar on 2012-01-24
Open skype, go to options --> sound devices and check to see if you can alter the option "microphone" to something else, other than pulse audio server.

Also, see if you can get any better results if you untick the box that says "Allow skype to automatically adjust my mixer levels".

---

### Post by niekas on 2012-01-24
Only pulse audio server is available for microphone and that mixer level box is unticked.

---

### Post by madvinegar on 2012-01-24
Since the mic has been activated, all I can say now is that you have to keep trying with your sound settings.

Since pulse audio is selected by Skype, try running again ```
gstreamer-properties
``` and change the input to pulse audio or to some other setting that might work.

Maybe also change the analog stereo duplex to something else in your sound settings.

---

### Post by silverfilling on 2012-01-24
Hi guys,
please when you have a moment try to solve a similar problem that I have. Here is the thread:
[http://ubuntuforums.org/showthread.php?p=11637545#post11637545](http://ubuntuforums.org/showthread.php?p=11637545#post11637545)
cheers

---

### Post by rutlandn on 2012-01-25
I went into Pulse Audio Volume Control and hit the Configuration tab. I selected Analogue Stereo Duplex,then on Input devices I selected Front Microphone (I'm on a desktop). I set the volume controls a bit low (60%-ish) otherwise I got a lot of distortion. Hope this helps.

---

### Post by niekas on 2012-01-25
> **rutlandn said:**
> I went into Pulse Audio Volume Control and hit the Configuration tab. I selected Analogue Stereo Duplex,then on Input devices I selected Front Microphone (I'm on a desktop). I set the volume controls a bit low (60%-ish) otherwise I got a lot of distortion. Hope this helps.
Doesn't work for me. My setup is identical only instead of "front microphone" I can select Mic 1 and Mic2 (plus analog input and analog line in). Not sure why two microphones. In any case doesn't matter which one i select the input indicator doesn't move at all. I can hear that microphone is operational, but system doesn't detect it for some reason.

---

### Post by madvinegar on 2012-01-26
I hope its not just a case of not been plugged properly (or should not be plugged all the way in etc.)...

---

### Post by niekas on 2012-01-26
It is plugged in all the way

---

### Post by madvinegar on 2012-01-26
Yes, I am just saying that maybe it should not be plugged all the way in. Sometimes you have to toggle with it.
In anycase, I know it is a longshot. I am just running out of ideas...:cool:

---

