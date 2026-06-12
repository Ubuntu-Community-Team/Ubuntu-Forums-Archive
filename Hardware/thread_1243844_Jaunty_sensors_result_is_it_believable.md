---
title: "Jaunty sensors result: is it believable?"
date: 2009-08-18
forum: Hardware
---

### Post by UbuKunubi on 2009-08-18
I keep noticing that the lights on my keyboard flash.
I wasnt sure if it was the result of bluetooth activity or something else.
When I run the sensors command in terminal I get the following result:
nigel@nigel-desktop:~$ sensors
w83627thf-isa-0290
Adapter: ISA adapter
VCore:       +1.69 V  (min =  +0.70 V, max =  +1.87 V)   
+12V:       +12.83 V  (min =  +8.21 V, max =  +8.82 V)   ALARM
+3.3V:       +3.15 V  (min =  +0.98 V, max =  +0.50 V)   ALARM
+5V:         +5.01 V  (min =  +0.53 V, max =  +2.53 V)   ALARM
-12V:       -12.61 V  (min =  -4.63 V, max =  -3.40 V)   ALARM
V5SB:        +5.05 V  (min =  +5.03 V, max =  +2.55 V)   ALARM
VBat:        +2.85 V  (min =  +0.34 V, max =  +3.92 V)   
fan1:          0 RPM  (min = 3082 RPM, div = 2)  ALARM
CPU Fan:    51923 RPM  (min =   -1 RPM, div = 2)  ALARM
fan3:          0 RPM  (min = 6490 RPM, div = 2)  ALARM
M/B Temp:    +34.0°C  (high = +34.0°C, hyst = +80.0°C)  sensor = thermistor
CPU Temp:    +38.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:       +39.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V
beep_enable:enabled

Is this to be trusted????

---

### Post by alex.pancescu on 2009-08-19
> **UbuKunubi said:**
> I keep noticing that the lights on my keyboard flash.
I wasnt sure if it was the result of bluetooth activity or something else.
When I run the sensors command in terminal I get the following result:
nigel@nigel-desktop:~$ sensors
w83627thf-isa-0290
Adapter: ISA adapter
VCore: +1.69 V (min = +0.70 V, max = +1.87 V) 
+12V: +12.83 V (min = +8.21 V, max = +8.82 V) ALARM
+3.3V: +3.15 V (min = +0.98 V, max = +0.50 V) ALARM
+5V: +5.01 V (min = +0.53 V, max = +2.53 V) ALARM
-12V: -12.61 V (min = -4.63 V, max = -3.40 V) ALARM
V5SB: +5.05 V (min = +5.03 V, max = +2.55 V) ALARM
VBat: +2.85 V (min = +0.34 V, max = +3.92 V) 
fan1: 0 RPM (min = 3082 RPM, div = 2) ALARM
CPU Fan: 51923 RPM (min = -1 RPM, div = 2) ALARM
fan3: 0 RPM (min = 6490 RPM, div = 2) ALARM
M/B Temp: +34.0°C (high = +34.0°C, hyst = +80.0°C) sensor = thermistor
CPU Temp: +38.0°C (high = +80.0°C, hyst = +75.0°C) sensor = diode
temp3: +39.0°C (high = +80.0°C, hyst = +75.0°C) sensor = thermistor
cpu0_vid: +0.000 V
beep_enable:enabled
 
Is this to be trusted????
 not really, the sensors that have ALARM attached to them are wrong for sure, no computer could run with just 8.82V on the 12V rail
depending on your hardware configuration, the CPU and MB values are possible and it seems that your CPU draws no power whatsoever :P i want one too...:P

---

### Post by tgalati4 on 2009-08-19
You can fix the ranges in /etc/sensors.conf.  Put realistic voltage/temperature ranges for your machine.

Your 3.3V seems low at 3.15V, but if your machine is not locking up then you should be OK.

Which LED's are flashing?  If it's the caplock and numclock flashing together, then that would indicate a kernel panic.  Which is not good.

Examine dmesg for errors:

dmesg | more  (spacebar to advance, q to quit)

---

### Post by UbuKunubi on 2009-08-19
> **tgalati4 said:**
> You can fix the ranges in /etc/sensors.conf.  Put realistic voltage/temperature ranges for your machine.

Your 3.3V seems low at 3.15V, but if your machine is not locking up then you should be OK.

Which LED's are flashing?  If it's the caplock and numclock flashing together, then that would indicate a kernel panic.  Which is not good.

Examine dmesg for errors:

dmesg | more  (spacebar to advance, q to quit)
Thanks for the pointer!

While the PC is VERY reliable, it has only started to flash all the keyboard LEDs since I updated earlier this week, and appears to only occur when I am using firefox.....

I should add that this is the first time I have ever encountered a problem like this, and have very little experience with any form of kernel panic!

As is evident below I can see no error messages so Im stumped as to the cause.
Also, when I examine the voltages in the BIOS hardware monitor all appears to be within acceptable limits.

Perhaps this is an issue with something that was updated?
The only item which jumps at me is the final line "ondemand governor failed".
Here is a copy of the dump from dmesg | more:
(which, to me, might as well be written in martian!)
> 
desktop:~$ dmesg | more
nigel@nigel-desktop:~$ dmesg | more
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@rothera) (gcc version 4.3
.3 (Ubuntu 4.3.3-5ubuntu4) ) #48-Ubuntu SMP Wed Jul 29 08:54:56 UTC 2009 (Ubuntu
 2.6.28-15.48-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
[    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x2fff0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000002fff0000 (usable)
[    0.000000]  modified: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
[    0.000000]  modified: 000000002fff3000 - 0000000030000000 (ACPI data)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 2fff0000 @ 10000-16000
[    0.000000] RAMDISK: 2f8af000 - 2ffdf7c9
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 2fff0000
[    0.000000]   low ram: 00000000 - 2fff0000
[    0.000000]   bootmap 00012000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [002f8af000 - 002ffdf7c9]          RAMDISK ==> [002f8af000 - 002ffdf7c9]
[    0.000000]   #5 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000018000]          BOOTMAP ==> [0000012000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f5b50] 000f5b50
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0002fff0
[    0.000000]   HighMem  0x0002fff0 -> 0x0002fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0002fff0
[    0.000000] On node 0 totalpages: 196479
[    0.000000] free_area_init_node: node 0, pgdat c06cb500, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1504 pages used for memmap
[    0.000000]   Normal zone: 190992 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] MPTABLE: OEM ID: OEM00000
[    0.000000] MPTABLE: Product ID: PROD00000000
[    0.000000] MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 1
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194943
[    0.000000] Kernel command line: root=UUID=e974e86b-1b77-46a4-a308-bda439ae15eb ro acpi=off quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1100.032 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 3931520 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 759852k/786368k available (4115k kernel code, 25896k reserved, 2199k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf07f0000 - 0xff3fe000   ( 236 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0504f5f   (4115 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004017] Calibrating delay loop (skipped), value calculated using timer frequency.. 2200.06 BogoMIPS (lpj=4400128)
[    0.004054] Security Framework initialized
[    0.004066] SELinux:  Disabled at boot.
[    0.004112] AppArmor: AppArmor initialized
[    0.004128] Mount-cache hash table entries: 512
[    0.004378] Initializing cgroup subsys ns
[    0.004386] Initializing cgroup subsys cpuacct
[    0.004390] Initializing cgroup subsys memory
[    0.004399] Initializing cgroup subsys freezer
[    0.004420] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004425] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004450] Checking 'hlt' instruction... OK.
[    0.020693] SMP alternatives: switching to UP code
[    0.252804] Freeing SMP alternatives: 18k freed
[    0.253022] ExtINT not setup in hardware but reported by MP table
[    0.253669] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.256001] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.256001] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.256001] ..... (found apic 0 pin 0) ...
[    0.294232] ....... works.
[    0.294236] CPU0: AMD Athlon(tm)  stepping 00
[    0.400656] Brought up 1 CPUs
[    0.400662] Total of 1 processors activated (2200.06 BogoMIPS).
[    0.400750] CPU0 attaching NULL sched-domain.
[    0.401320] net_namespace: 776 bytes
[    0.401334] Booting paravirtualized kernel on bare hardware
[    0.401716] Time: 11:29:01  Date: 08/19/09
[    0.401728] regulator: core version 0.5
[    0.401798] NET: Registered protocol family 16
[    0.402055] EISA bus registered
[    0.434484] PCI: PCI BIOS revision 2.10 entry at 0xfbe50, last bus=2
[    0.434489] PCI: Using configuration type 1 for base access
[    0.436265] ACPI: Interpreter disabled.
[    0.436543] SCSI subsystem initialized
[    0.436629] libata version 3.00 loaded.
[    0.436725] usbcore: registered new interface driver usbfs
[    0.436754] usbcore: registered new interface driver hub
[    0.436814] usbcore: registered new device driver usb
[    0.437045] PCI: Probing PCI hardware
[    0.437051] PCI: Probing PCI hardware (bus 00)
[    0.437118] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.437425] pci 0000:00:01.1: reg 10 io port: [0xec00-0xec1f]
[    0.437467] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.437474] pci 0000:00:01.1: PME# disabled
[    0.437517] pci 0000:00:02.0: reg 10 32bit mmio: [0xea001000-0xea001fff]
[    0.437557] pci 0000:00:02.0: supports D1 D2
[    0.437561] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.437568] pci 0000:00:02.0: PME# disabled
[    0.437602] pci 0000:00:02.1: reg 10 32bit mmio: [0xea002000-0xea002fff]
[    0.437642] pci 0000:00:02.1: supports D1 D2
[    0.437646] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.437652] pci 0000:00:02.1: PME# disabled
[    0.437695] pci 0000:00:02.2: reg 10 32bit mmio: [0xea003000-0xea0030ff]
[    0.437738] pci 0000:00:02.2: supports D1 D2
[    0.437741] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.437748] pci 0000:00:02.2: PME# disabled
[    0.437792] pci 0000:00:04.0: reg 10 32bit mmio: [0xea000000-0xea000fff]
[    0.437802] pci 0000:00:04.0: reg 14 io port: [0xe800-0xe807]
[    0.437837] pci 0000:00:04.0: supports D1 D2
[    0.437841] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.437847] pci 0000:00:04.0: PME# disabled
[    0.437883] pci 0000:00:06.0: reg 10 io port: [0xe000-0xe0ff]
[    0.437892] pci 0000:00:06.0: reg 14 io port: [0xe400-0xe47f]
[    0.437901] pci 0000:00:06.0: reg 18 32bit mmio: [0xea004000-0xea004fff]
[    0.437932] pci 0000:00:06.0: supports D1 D2
[    0.438016] pci 0000:00:09.0: reg 20 io port: [0xf000-0xf00f]
[    0.438202] pci 0000:01:00.0: reg 10 32bit mmio: [0xd0000000-0xd7ffffff]
[    0.438211] pci 0000:01:00.0: reg 14 io port: [0xd000-0xd0ff]
[    0.438221] pci 0000:01:00.0: reg 18 32bit mmio: [0xe9000000-0xe900ffff]
[    0.438245] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.438260] pci 0000:01:00.0: supports D1 D2
[    0.438297] pci 0000:01:00.1: reg 10 32bit mmio: [0xd8000000-0xdfffffff]
[    0.438307] pci 0000:01:00.1: reg 14 32bit mmio: [0xe9010000-0xe901ffff]
[    0.438344] pci 0000:01:00.1: supports D1 D2
[    0.438399] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.438406] pci 0000:00:1e.0: bridge 32bit mmio: [0xe8000000-0xe9ffffff]
[    0.438413] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.439121] pci 0000:00:00.0: default IRQ router [10de:01e0]
[    0.439309] Bluetooth: Core ver 2.13
[    0.439309] NET: Registered protocol family 31
[    0.439309] Bluetooth: HCI device and connection manager initialized
[    0.439309] Bluetooth: HCI socket layer initialized
[    0.439309] NET: Registered protocol family 8
[    0.439309] NET: Registered protocol family 20
[    0.439309] NetLabel: Initializing
[    0.439309] NetLabel:  domain hash size = 128
[    0.439309] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.439309] NetLabel:  unlabeled traffic allowed by default
[    0.439309] AppArmor: AppArmor Filesystem Enabled
[    0.439309] pnp: PnP ACPI: disabled
[    0.439309] PnPBIOS: Scanning system for PnP BIOS support...
[    0.439309] PnPBIOS: Found PnP BIOS installation structure at 0xc00fc8c0
[    0.439309] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc8f0, dseg 0xf0000
[    0.440311] PnPBIOS: 13 nodes reported by PnP BIOS; 13 recorded by driver
[    0.440333] system 00:07: iomem range 0x0-0x9ffff could not be reserved
[    0.440340] system 00:07: iomem range 0xfffe0000-0xffffffff could not be reserved
[    0.440346] system 00:07: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.440352] system 00:07: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    0.440357] system 00:07: iomem range 0x100000-0xffffff could not be reserved
[    0.440367] system 00:08: iomem range 0xf0000-0xf3fff could not be reserved
[    0.440373] system 00:08: iomem range 0xf4000-0xf7fff could not be reserved
[    0.440378] system 00:08: iomem range 0xf8000-0xfffff could not be reserved
[    0.440383] system 00:08: iomem range 0xd1800-0xd3fff has been reserved
[    0.440743] pci 0000:00:08.0: PCI bridge, secondary bus 0000:02
[    0.440747] pci 0000:00:08.0:   IO window: disabled
[    0.440755] pci 0000:00:08.0:   MEM window: disabled
[    0.440761] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.440775] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.440781] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.440788] pci 0000:00:1e.0:   MEM window: 0xe8000000-0xe9ffffff
[    0.440795] pci 0000:00:1e.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.440813] pci 0000:00:08.0: setting latency timer to 64
[    0.440825] bus: 00 index 0 io port: [0x00-0xffff]
[    0.440829] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.440833] bus: 02 index 0 mmio: [0x0-0x0]
[    0.440837] bus: 02 index 1 mmio: [0x0-0x0]
[    0.440840] bus: 02 index 2 mmio: [0x0-0x0]
[    0.440843] bus: 02 index 3 mmio: [0x0-0x0]
[    0.440847] bus: 01 index 0 io port: [0xd000-0xdfff]
[    0.440851] bus: 01 index 1 mmio: [0xe8000000-0xe9ffffff]
[    0.440856] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.440859] bus: 01 index 3 mmio: [0x0-0x0]
[    0.440874] NET: Registered protocol family 2
[    0.441087] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.441785] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.444311] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.445601] TCP: Hash tables configured (established 131072 bind 65536)
[    0.445606] TCP reno registered
[    0.445826] NET: Registered protocol family 1
[    0.446079] checking if image is initramfs... it is
[    1.580883] Freeing initrd memory: 7361k freed
[    1.581060] cpufreq: Detected nForce2 chipset revision C1
[    1.581064] cpufreq: FSB changing is maybe unstable and can lead to crashes and data loss.
[    1.581085] cpufreq: FSB currently at 100 MHz, FID 11.0
[    1.581403] audit: initializing netlink socket (disabled)
[    1.581434] type=2000 audit(1250681341.580:1): initialized
[    1.595534] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.598009] VFS: Disk quotas dquot_6.5.1
[    1.598116] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.599238] fuse init (API version 7.10)
[    1.599395] msgmni has been set to 1498
[    1.599732] alg: No test for stdrng (krng)
[    1.599757] io scheduler noop registered
[    1.599761] io scheduler anticipatory registered
[    1.599765] io scheduler deadline registered
[    1.599793] io scheduler cfq registered (default)
[    1.600077] pci 0000:01:00.0: Boot video device
[    1.600248] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.600265] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.600391] isapnp: Scanning for PnP cards...
[    1.954879] isapnp: No Plug & Play device found
[    1.956923] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.957052] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.957586] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.958959] brd: module loaded
[    1.959512] loop: module loaded
[    1.959642] Fixed MDIO Bus: probed
[    1.959653] PPP generic driver version 2.4.2
[    1.959765] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.959814] Driver 'sd' needs updating - please use bus_type methods
[    1.959831] Driver 'sr' needs updating - please use bus_type methods
[    1.960260] pata_amd 0000:00:09.0: version 0.3.10
[    1.960366] pata_amd 0000:00:09.0: setting latency timer to 64
[    1.960551] scsi0 : pata_amd
[    1.960742] scsi1 : pata_amd
[    1.960816] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.960821] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    2.180669] ata1.00: ATA-6: ST380011A, 8.01, max UDMA/100
[    2.180675] ata1.00: 156301488 sectors, multi 1: LBA48 
[    2.180715] ata1: nv_mode_filter: 0x3f39f&0x3f07f->0x3f01f, BIOS=0x3f000 (0xc600c000) ACPI=0x0
[    2.196594] ata1.00: configured for UDMA/100
[    2.360432] ata2.00: ATAPI: LITE-ON DVDRW SOHW-1633S, BS0C, max UDMA/66
[    2.360472] ata2: nv_mode_filter: 0x1f39f&0x707f->0x701f, BIOS=0x7000 (0xc600c000) ACPI=0x0
[    2.376407] ata2.00: configured for UDMA/33
[    2.377074] scsi 0:0:0:0: Direct-Access     ATA      ST380011A        8.01 PQ: 0 ANSI: 5
[    2.377259] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.377298] sd 0:0:0:0: [sda] Write Protect is off
[    2.377303] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.377363] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.377500] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.377534] sd 0:0:0:0: [sda] Write Protect is off
[    2.377539] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.377596] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.377605]  sda: sda1 sda2 < sda5 >
[    2.404315] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.404422] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.405389] scsi 1:0:0:0: CD-ROM            LITE-ON  DVDRW SOHW-1633S BS0C PQ: 0 ANSI: 5
[    2.409418] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    2.409425] Uniform CD-ROM driver Revision: 3.20
[    2.409599] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.409666] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.410498] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.410572] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    2.410578] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    2.410690] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[    2.410757] ehci_hcd 0000:00:02.2: debug port 1
[    2.410766] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    2.410792] ehci_hcd 0000:00:02.2: irq 9, io mem 0xea003000
[    2.420078] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    2.420222] usb usb1: configuration #1 chosen from 1 choice
[    2.420273] hub 1-0:1.0: USB hub found
[    2.420294] hub 1-0:1.0: 8 ports detected
[    2.420487] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.420528] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    2.420534] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.420608] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    2.420642] ohci_hcd 0000:00:02.0: irq 3, io mem 0xea001000
[    2.478156] usb usb2: configuration #1 chosen from 1 choice
[    2.478211] hub 2-0:1.0: USB hub found
[    2.478230] hub 2-0:1.0: 4 ports detected
[    2.478384] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    2.478390] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    2.478467] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    2.478500] ohci_hcd 0000:00:02.1: irq 11, io mem 0xea002000
[    2.534166] usb usb3: configuration #1 chosen from 1 choice
[    2.534211] hub 3-0:1.0: USB hub found
[    2.534231] hub 3-0:1.0: 4 ports detected
[    2.534370] uhci_hcd: USB Universal Host Controller Interface driver
[    2.534516] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    2.536871] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.536882] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.537070] mice: PS/2 mouse device common for all mice
[    2.537231] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.537263] rtc0: alarms up to one day, 114 bytes nvram
[    2.537367] device-mapper: uevent: version 1.0.3
[    2.537597] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.537702] device-mapper: multipath: version 1.0.5 loaded
[    2.537708] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.537859] EISA: Probing bus 0 at eisa.0
[    2.537912] EISA: Detected 0 cards.
[    2.537988] cpuidle: using governor ladder
[    2.537992] cpuidle: using governor menu
[    2.538945] TCP cubic registered
[    2.539123] NET: Registered protocol family 10
[    2.539870] lo: Disabled Privacy Extensions
[    2.540466] NET: Registered protocol family 17
[    2.540500] Bluetooth: L2CAP ver 2.11
[    2.540503] Bluetooth: L2CAP socket layer initialized
[    2.540509] Bluetooth: SCO (Voice Link) ver 0.6
[    2.540512] Bluetooth: SCO socket layer initialized
[    2.540568] Bluetooth: RFCOMM socket layer initialized
[    2.540583] Bluetooth: RFCOMM TTY layer initialized
[    2.540587] Bluetooth: RFCOMM ver 1.10
[    2.540625] powernow-k8: Processor cpuid 6a0 not supported
[    2.540639] Using IPI No-Shortcut mode
[    2.540768] registered taskstats version 1
[    2.540952]   Magic number: 5:531:479
[    2.541074] rtc_cmos 00:03: setting system clock to 2009-08-19 11:29:03 UTC (1250681343)
[    2.541080] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.541084] EDD information not available.
[    2.542086] Freeing unused kernel memory: 532k freed
[    2.542310] Write protecting the kernel text: 4116k
[    2.542396] Write protecting the kernel read-only data: 1528k
[    2.574974] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.732172] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    2.865998] usb 1-6: configuration #1 chosen from 1 choice
[    3.321219] Initializing USB Mass Storage driver...
[    3.332759] scsi2 : SCSI emulation for USB Mass Storage devices
[    3.333738] usbcore: registered new interface driver usb-storage
[    3.333746] USB Mass Storage support registered.
[    3.334083] usb-storage: device found at 2
[    3.334087] usb-storage: waiting for device to settle before scanning
[    3.367820] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.367853] forcedeth 0000:00:04.0: setting latency timer to 64
[    3.367955] nv_probe: set workaround bit for reversed mac addr
[    3.889849] forcedeth 0000:00:04.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:11:09:60:8f:c4
[    3.889860] forcedeth 0000:00:04.0: csum timirq lnktim desc-v2
[    4.290787] PM: Starting manual resume from disk
[    4.290795] PM: Resume from partition 8:5
[    4.290798] PM: Checking hibernation image.
[    4.291016] PM: Resume from disk failed.
[    4.339652] kjournald starting.  Commit interval 5 seconds
[    4.339674] EXT3-fs: mounted filesystem with ordered data mode.
[    8.332593] usb-storage: device scan complete
[    8.333171] scsi 2:0:0:0: Direct-Access     BUFFALO  External HDD          PQ: 0 ANSI: 2 CCS
[    8.334391] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    8.334885] sd 2:0:0:0: [sdb] Write Protect is off
[    8.334890] sd 2:0:0:0: [sdb] Mode Sense: 34 00 00 00
[    8.334896] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.335637] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    8.336134] sd 2:0:0:0: [sdb] Write Protect is off
[    8.336140] sd 2:0:0:0: [sdb] Mode Sense: 34 00 00 00
[    8.336144] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.336151]  sdb: sdb1
[    8.342355] sd 2:0:0:0: [sdb] Attached SCSI disk
[    8.342474] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   10.695203] udev: starting version 141
[   11.038738] Linux agpgart interface v0.103
[   11.337173] agpgart: Detected NVIDIA nForce2 chipset
[   11.351083] agpgart-nvidia 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[   11.604801] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   11.604892] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5100
[   11.651395] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.871686] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   12.012604] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   12.088538] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.270589] nf_conntrack version 0.5.0 (12287 buckets, 49148 max)
[   12.271171] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   12.271177] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   12.271182] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   12.286243] Intel ICH 0000:00:06.0: setting latency timer to 64
[   12.476154] psmouse serio1: ID: 10 00 64<6>intel8x0_measure_ac97_clock: measured 54463 usecs
[   12.608494] intel8x0: clocking to 48000
[   12.872486] lp: driver loaded but no devices found
[   12.908892] w83627hf: Found W83627THF chip at 0x290
[   12.909026] w83627hf w83627hf.656: Reading VID from GPIO5
[   13.012991] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   13.125977] Adding 2241028k swap on /dev/sda5.  Priority:-1 extents:1 across:2241028k
[   13.695278] EXT3 FS on sda1, internal journal
[   15.008398] type=1505 audit(1250681355.963:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1815
[   15.117474] type=1505 audit(1250681356.075:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1819
[   15.117853] type=1505 audit(1250681356.075:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1819
[   15.117983] type=1505 audit(1250681356.075:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1819
[   15.118107] type=1505 audit(1250681356.075:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1819
[   15.440802] type=1505 audit(1250681356.399:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1824
[   15.441335] type=1505 audit(1250681356.399:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1824
[   15.504326] type=1505 audit(1250681356.459:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1828
[   15.776653] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   24.490256] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.490264] Bluetooth: BNEP filters: protocol multicast
[   24.512462] Bridge firewalling registered
[   25.942777] ppdev: user-space parallel port driver
[   26.136046] [drm] Initialized drm 1.1.0 20060810
[   26.172399] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   26.622209] agpgart-nvidia 0000:00:00.0: AGP 2.0 bridge
[   26.622245] agpgart-nvidia 0000:00:00.0: putting AGP V2 device into 4x mode
[   26.622318] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   26.873535] [drm] Setting GART location based on new memory map
[   26.873551] [drm] Loading R200 Microcode
[   26.873606] [drm] writeback test succeeded in 1 usecs
[   36.441442] eth0: no IPv6 routers present
[   78.940180] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[   93.948167] ondemand governor failed, too long transition latency of HW, fallback to performance governor
nigel@nigel-desktop:~$  



---

### Post by UbuKunubi on 2009-08-19
> **alex.pancescu said:**
> not really, the sensors that have ALARM attached to them are wrong for sure, no computer could run with just 8.82V on the 12V rail
depending on your hardware configuration, the CPU and MB values are possible and it seems that your CPU draws no power whatsoever :P i want one too...:P

Alex,
I'm quite handy with a multimeter and a similar thought ran through my mind too.
Not really sure what is going on here, but my spidey senses are telling me somethings up!
Cheers,
Ubu

---

### Post by tgalati4 on 2009-08-19
What version of Firefox?  If you are using 3.0.13, try 3.5.2 or vice versa.

The ondemand speed governer is used for Intel chips that support SpeedStep. You have an AMD Athlon.  I'm not sure if it supports stepping.  The AMD stepping module (powernow) says that your cpu is not supported. Your video card supports bus-slowing, but it is turned off because it causes stability problems.

Of course if the LED's are just annoying, use some electrical tape to cover them.

It's not the best solution, but it is the linux way!

---

### Post by mcduck on 2009-08-19
> **UbuKunubi said:**
> I keep noticing that the lights on my keyboard flash.
I wasnt sure if it was the result of bluetooth activity or something else.
When I run the sensors command in terminal I get the following result:
nigel@nigel-desktop:~$ sensors
w83627thf-isa-0290
Adapter: ISA adapter
VCore:       +1.69 V  (min =  +0.70 V, max =  +1.87 V)   
+12V:       +12.83 V  (min =  +8.21 V, max =  +8.82 V)   ALARM
+3.3V:       +3.15 V  (min =  +0.98 V, max =  +0.50 V)   ALARM
+5V:         +5.01 V  (min =  +0.53 V, max =  +2.53 V)   ALARM
-12V:       -12.61 V  (min =  -4.63 V, max =  -3.40 V)   ALARM
V5SB:        +5.05 V  (min =  +5.03 V, max =  +2.55 V)   ALARM
VBat:        +2.85 V  (min =  +0.34 V, max =  +3.92 V)   
fan1:          0 RPM  (min = 3082 RPM, div = 2)  ALARM
CPU Fan:    51923 RPM  (min =   -1 RPM, div = 2)  ALARM
fan3:          0 RPM  (min = 6490 RPM, div = 2)  ALARM
M/B Temp:    +34.0°C  (high = +34.0°C, hyst = +80.0°C)  sensor = thermistor
CPU Temp:    +38.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:       +39.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V
beep_enable:enabled

Is this to be trusted????

To some level.

You should never trust lm-sensors data unless you have compared it to data from some other source. Lm-sensors outputs the data it gets from the sensor chip, without taking any consideration on your motherboard model and how the sensors are actually implemented on that motherboard. Because of this you should never take it's output for granted, but instead compare it to some other source, and then adjust sensors.conf to assign sensor data to correct readings, and in many cases add suitable calculation formulas to convert the data your motherboard sensors give to correct values.

For example take a look at your fan speed, it clearly needs higher divider than 2, unless you are cooling your CPU with a jet turbine.. ;)

Also pretty much every reading has insane range settings (like -4,6 to -3.4 for -12V rail :D).

But apart from those details, your actual voltage readings & temperatures seem quite correct, and are well within normal ranges. Based on that, whatever your actual problem is, it's not caused by bad voltages or temperature problems. Perhaps the jet turbine cooling your CPU.. :D

---

### Post by mcduck on 2009-08-19
What comes to the blinking lights, do you have a seaparate light for wireless network or bluetooth? Is it working normally?

If everything else is working normally it could very well be that for some reason or other your keyboard leds are used instead of wifi led, leds on laptops are often implemented in rather unique ways and can be pretty strange sometimes. Every manufacturer and model seems to have their own non-standard ways to implement the lights, and when using rather generic drivers based on the chip models (the Linux way) instead of drivers specifically built for your laptop model (windows drivers that come with the laptop) there can be some strange side-effects.

Try turning network and/or bluetooth off. If the lights stop blinking, you have just found out the problem. If not, we'll try to figure something else. :)

---

### Post by UbuKunubi on 2009-08-19
> **mcduck said:**
> What comes to the blinking lights, do you have a seaparate light for wireless network or bluetooth? Is it working normally?

If everything else is working normally it could very well be that for some reason or other your keyboard leds are used instead of wifi led, leds on laptops are often implemented in rather unique ways and can be pretty strange sometimes. Every manufacturer and model seems to have their own non-standard ways to implement the lights, and when using rather generic drivers based on the chip models (the Linux way) instead of drivers specifically built for your laptop model (windows drivers that come with the laptop) there can be some strange side-effects.

Try turning network and/or bluetooth off. If the lights stop blinking, you have just found out the problem. If not, we'll try to figure something else. :)

mcduck,
Thanks for your suggestions, but the machine is a desktop, with ethernet connection and no wifi nor bluetooth devices are plugged into it.

---

### Post by mcduck on 2009-08-20
> **UbuKunubi said:**
> mcduck,
Thanks for your suggestions, but the machine is a desktop, with ethernet connection and no wifi nor bluetooth devices are plugged into it.

oh, for some reason I was pretty sure it must be a laptop.. :)

I tried looking through te dmesg output, but I can't see anything strange there.

The failed CPU governor looked slightly strange, but it seems that you have AMD Athlon CPU (?) so it only makes sense, those processors don't support frequency scaling..

Perhaps there's something in the kernel.log.. Could you attach that here as well? (it's probably pretty log so it might be a good idea to attach it as a text file..)

---

### Post by UbuKunubi on 2009-08-20
> **mcduck said:**
> oh, for some reason I was pretty sure it must be a laptop.. :)
I tried looking through te dmesg output, but I can't see anything strange there.
The failed CPU governor looked slightly strange, but it seems that you have AMD Athlon CPU (?) so it only makes sense, those processors don't support frequency scaling..
Perhaps there's something in the kernel.log.. Could you attach that here as well? (it's probably pretty log so it might be a good idea to attach it as a text file..)

Many thanks for spending time on helping me with this.
I've attached the log file as .tar because of the size limits imposed on text file attachments.

Ubu

---

### Post by mcduck on 2009-08-20
Sorry, I read through that log as well but I can't find anything relevant there either.

If you want, you can attach syslog and debug logs, and I'll check if I find anything in them. But since everything seems to work fine I think you can safely just ignore the blinking lights. :)

---

### Post by UbuKunubi on 2009-08-21
> **mcduck said:**
> Sorry, I read through that log as well but I can't find anything relevant there either.

If you want, you can attach syslog and debug logs, and I'll check if I find anything in them. But since everything seems to work fine I think you can safely just ignore the blinking lights. :)

mcduck,
I have now seen that the keyboard LEDs are only blinking when the system is under a load for a while, and seeing as collectively nothing in software seems wrong I'll have to investigate the hardware and check the fan, see if the heatsink is secure, etc.

Thanks for your efforts - its highly appreciated.

All the best,
Ubu

---

