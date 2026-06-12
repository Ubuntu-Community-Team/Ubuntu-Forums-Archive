---
title: "i may have screwed it up myself"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by linux000019 on 2009-05-25
when i installed crunchbang to my 8 gb usb harddrive(platter not flash) yesterday, i was interupted halfway through install; and pulled plug. today i have enough time to finish the install, only now there are problems. crunchbang(livecd) won't even acknowledge the usb hard drive anymore. i said "im sorry computer, please work for me" and it gave me the middle finger. help!

---

### Post by linux000019 on 2009-05-25
when i installed crunchbang to my 8 gb usb harddrive(platter not flash) yesterday, i was interupted halfway through install; and pulled plug. today i have enough time to finish the install, only now there are problems. crunchbang(livecd) won't even acknowledge the usb hard drive anymore. i said "im sorry computer, please work for me" and it gave me the middle finger. help!

---

### Post by albinootje on 2009-05-25
> **linux000019 said:**
> crunchbang(livecd) won't even acknowledge the usb hard drive anymore. 

Please post the output of the following in a terminal :
```

lsusb
sudo fdisk -l
dmesg

```

---

### Post by frodon on 2009-05-25
Duplicate thread closed.

Please use the following link if willing to contribute to this thread :
[http://ubuntuforums.org/showthread.php?t=1169562](http://ubuntuforums.org/showthread.php?t=1169562)

---

### Post by linux000019 on 2009-05-25
crunchbang@crunchbang:~$ lsusb
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 002: ID 0461:4d16 Primax Electronics, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 001 Device 003: ID 0aa6:1600 Perception Digital, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
crunchbang@crunchbang:~$ 

crunchbang@crunchbang:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92af92af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         702       30400   238557217+   7  HPFS/NTFS
/dev/sda2               1         701     5630751    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 16.2 GB, 16265510400 bytes
255 heads, 63 sectors/track, 1977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04b15c37

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1978    15884256    c  W95 FAT32 (LBA)
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037ff0000 (usable)
[    0.000000]  BIOS-e820: 0000000037ff0000 - 0000000037ff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037ff3000 - 0000000038000000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000038000000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x37ff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 37ff0000 @ 7000-d000
[    0.000000] RAMDISK: 377ce000 - 37fdffec
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP 000F7C10, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 37FF3040, 0034 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 37FF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 37FF3180, 63AB (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 37FF0000, 0040
[    0.000000] ACPI: SSDT 37FF9640, 0206 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: MCFG 37FF98C0, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 37FF9580, 0072 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 895MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37ff0000
[    0.000000]   low ram: 00000000 - 37ff0000
[    0.000000]   bootmap 00009000 - 00010000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0037ff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [00377ce000 - 0037fdffec]          RAMDISK ==> [00377ce000 - 0037fdffec]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
[    0.000000] found SMP MP-table at [c00f3cf0] 000f3cf0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037ff0
[    0.000000]   HighMem  0x00037ff0 -> 0x00037ff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00037ff0
[    0.000000] On node 0 totalpages: 229263
[    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223284 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 227247
[    0.000000] Kernel command line: noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/custom.seed boot=casper initrd=/casper/initrd.gz quiet splash -- BOOT_IMAGE=/casper/vmlinuz 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2210.017 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 894788k/917440k available (2572k kernel code, 22136k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf7ff0000   ( 895 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 4420.03 BogoMIPS (lpj=884006
[    0.004026] Security Framework initialized
[    0.004033] SELinux:  Disabled at boot.
[    0.004053] AppArmor: AppArmor initialized
[    0.004060] Mount-cache hash table entries: 512
[    0.004194] Initializing cgroup subsys ns
[    0.004199] Initializing cgroup subsys cpuacct
[    0.004201] Initializing cgroup subsys memory
[    0.004213] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004216] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004218] CPU 0(2) -> Core 0
[    0.004221] using C1E aware idle routine
[    0.004228] Checking 'hlt' instruction... OK.
[    0.021391] ACPI: Core revision 20080609
[    0.023562] ACPI: Checking initramfs for custom DSDT
[    0.343032] ENABLING IO-APIC IRQs
[    0.343258] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.348021] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.348021] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.348021] ..... (found apic 0 pin 0) ...
[    0.356022] ....... failed.
[    0.356022] ...trying to set up timer as Virtual Wire IRQ...
[    0.356022] ..... failed.
[    0.356022] ...trying to set up timer as ExtINT IRQ...
[    0.397492] ..... works.
[    0.397493] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[    0.400025] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.452028] Calibrating delay using timer specific routine.. 4420.40 BogoMIPS (lpj=8840804)
[    0.452028] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.452028] CPU: L2 Cache: 512K (64 bytes/line)
[    0.452028] CPU 1(2) -> Core 1
[    0.484167] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[    0.484194] Brought up 2 CPUs
[    0.484197] Total of 2 processors activated (8840.43 BogoMIPS).
[    0.484243] CPU0 attaching sched-domain:
[    0.484245]  domain 0: span 0-1 level CPU
[    0.484248]   groups: 0 1
[    0.484254] CPU1 attaching sched-domain:
[    0.484256]  domain 0: span 0-1 level CPU
[    0.484258]   groups: 1 0
[    0.484321] net_namespace: 840 bytes
[    0.484321] Booting paravirtualized kernel on bare hardware
[    0.484321] Time:  7:51:43  Date: 05/25/09
[    0.484321] NET: Registered protocol family 16
[    0.484321] EISA bus registered
[    0.484321] ACPI: bus type pci registered
[    0.484321] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.484321] PCI: MCFG area at f0000000 reserved in E820
[    0.484321] PCI: Using MMCONFIG for extended config space
[    0.484321] PCI: Using configuration type 1 for base access
[    0.484988] ACPI: EC: Look up EC in DSDT
[    0.496691] ACPI: Interpreter enabled
[    0.496694] ACPI: (supports S0 S3 S4 S5)
[    0.496709] ACPI: Using IOAPIC for interrupt routing
[    0.508212] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.508235] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.508239] pci 0000:00:02.0: PME# disabled
[    0.508262] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.508265] pci 0000:00:03.0: PME# disabled
[    0.508288] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.508290] pci 0000:00:04.0: PME# disabled
[    0.508303] PCI: 0000:00:05.0 reg 10 32bit mmio: [fc000000, fcffffff]
[    0.508307] PCI: 0000:00:05.0 reg 14 32bit mmio: [e0000000, efffffff]
[    0.508314] PCI: 0000:00:05.0 reg 1c 64bit mmio: [fb000000, fbffffff]
[    0.508319] PCI: 0000:00:05.0 reg 30 32bit mmio: [0, 1ffff]
[    0.508485] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.508525] PCI: 0000:00:0a.1 reg 20 io port: [1c00, 1c3f]
[    0.508531] PCI: 0000:00:0a.1 reg 24 io port: [1c40, 1c7f]
[    0.508549] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.508555] pci 0000:00:0a.1: PME# disabled
[    0.508609] PCI: 0000:00:0b.0 reg 10 32bit mmio: [fe02f000, fe02ffff]
[    0.508634] pci 0000:00:0b.0: supports D1
[    0.508636] pci 0000:00:0b.0: supports D2
[    0.508638] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.508642] pci 0000:00:0b.0: PME# disabled
[    0.508663] PCI: 0000:00:0b.1 reg 10 32bit mmio: [fe02e000, fe02e0ff]
[    0.508689] pci 0000:00:0b.1: supports D1
[    0.508691] pci 0000:00:0b.1: supports D2
[    0.508693] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.508696] pci 0000:00:0b.1: PME# disabled
[    0.508728] PCI: 0000:00:0d.0 reg 20 io port: [f400, f40f]
[    0.508763] PCI: 0000:00:0e.0 reg 10 io port: [9f0, 9f7]
[    0.508768] PCI: 0000:00:0e.0 reg 14 io port: [bf0, bf3]
[    0.508772] PCI: 0000:00:0e.0 reg 18 io port: [970, 977]
[    0.508777] PCI: 0000:00:0e.0 reg 1c io port: [b70, b73]
[    0.508781] PCI: 0000:00:0e.0 reg 20 io port: [e000, e00f]
[    0.508786] PCI: 0000:00:0e.0 reg 24 32bit mmio: [fe02d000, fe02dfff]
[    0.508823] PCI: 0000:00:0f.0 reg 10 io port: [9e0, 9e7]
[    0.508827] PCI: 0000:00:0f.0 reg 14 io port: [be0, be3]
[    0.508832] PCI: 0000:00:0f.0 reg 18 io port: [960, 967]
[    0.508836] PCI: 0000:00:0f.0 reg 1c io port: [b60, b63]
[    0.508841] PCI: 0000:00:0f.0 reg 20 io port: [cc00, cc0f]
[    0.508845] PCI: 0000:00:0f.0 reg 24 32bit mmio: [fe02c000, fe02cfff]
[    0.508910] PCI: 0000:00:10.1 reg 10 32bit mmio: [fe024000, fe027fff]
[    0.508939] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.508942] pci 0000:00:10.1: PME# disabled
[    0.508967] PCI: 0000:00:14.0 reg 10 32bit mmio: [fe02b000, fe02bfff]
[    0.508972] PCI: 0000:00:14.0 reg 14 io port: [c800, c807]
[    0.508992] pci 0000:00:14.0: supports D1
[    0.508994] pci 0000:00:14.0: supports D2
[    0.508996] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.508999] pci 0000:00:14.0: PME# disabled
[    0.509099] PCI: bridge 0000:00:02.0 io port: [a000, afff]
[    0.509102] PCI: bridge 0000:00:02.0 32bit mmio: [fd800000, fd8fffff]
[    0.509106] PCI: bridge 0000:00:02.0 64bit mmio pref: [fd700000, fd7fffff]
[    0.509144] PCI: bridge 0000:00:03.0 io port: [8000, 8fff]
[    0.509147] PCI: bridge 0000:00:03.0 32bit mmio: [fde00000, fdefffff]
[    0.509150] PCI: bridge 0000:00:03.0 64bit mmio pref: [fdd00000, fddfffff]
[    0.509188] PCI: bridge 0000:00:04.0 io port: [b000, bfff]
[    0.509190] PCI: bridge 0000:00:04.0 32bit mmio: [fdc00000, fdcfffff]
[    0.509194] PCI: bridge 0000:00:04.0 64bit mmio pref: [fd900000, fd9fffff]
[    0.509225] PCI: 0000:04:07.0 reg 10 32bit mmio: [fdbe0000, fdbeffff]
[    0.509231] PCI: 0000:04:07.0 reg 14 io port: [9c00, 9c07]
[    0.509259] pci 0000:04:07.0: PME# supported from D3hot D3cold
[    0.509262] pci 0000:04:07.0: PME# disabled
[    0.509286] PCI: 0000:04:09.0 reg 10 32bit mmio: [fdbff000, fdbff7ff]
[    0.509292] PCI: 0000:04:09.0 reg 14 io port: [9800, 987f]
[    0.509323] pci 0000:04:09.0: supports D2
[    0.509324] pci 0000:04:09.0: PME# supported from D2 D3hot D3cold
[    0.509328] pci 0000:04:09.0: PME# disabled
[    0.509352] pci 0000:00:10.0: transparent bridge
[    0.509356] PCI: bridge 0000:00:10.0 io port: [9000, 9fff]
[    0.509359] PCI: bridge 0000:00:10.0 32bit mmio: [fdb00000, fdbfffff]
[    0.509363] PCI: bridge 0000:00:10.0 32bit mmio pref: [fda00000, fdafffff]
[    0.509372] bus 00 -> node 0
[    0.509379] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.509855] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.638837] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.638837] ACPI: PCI Interrupt Link [LNK2] (IRQs *5 7 9 10 11 14 15)
[    0.638837] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.638837] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)
[    0.640166] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.640375] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.640586] ACPI: PCI Interrupt Link [LNK7] (IRQs *5 7 9 10 11 14 15)
[    0.640794] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.641004] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.641212] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.641423] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[    0.641631] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.641842] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.642053] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 *11 14 15)
[    0.642261] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.642473] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.642683] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[    0.642892] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.643103] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
[    0.643314] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
[    0.643578] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.643833] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[    0.644092] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.644346] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.644599] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.644852] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.645106] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
[    0.645359] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.645614] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.645869] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.646125] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.646379] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.646635] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0
[    0.646889] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.647144] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.647399] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.647654] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.647909] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.648170] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.648426] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.648682] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.648757] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.648757] pnp: PnP ACPI init
[    0.648757] ACPI: bus type pnp registered
[    0.656280] pnp: PnP ACPI: found 13 devices
[    0.656280] ACPI: ACPI bus type pnp unregistered
[    0.656280] PnPBIOS: Disabled by ACPI PNP
[    0.656280] PCI: Using ACPI for IRQ routing
[    0.664042] NET: Registered protocol family 8
[    0.664044] NET: Registered protocol family 20
[    0.664065] NetLabel: Initializing
[    0.664067] NetLabel:  domain hash size = 128
[    0.664069] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.664083] NetLabel:  unlabeled traffic allowed by default
[    0.664640] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.664643]    actual entries 65620
[    0.664788] AppArmor: AppArmor Filesystem Enabled
[    0.664818] ACPI: RTC can wake from S4
[    0.672054] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.672057] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.672060] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.672062] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.672065] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.672068] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.672071] system 00:01: ioport range 0x2000-0x207f has been reserved
[    0.672073] system 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.672077] system 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
[    0.672080] system 00:01: iomem range 0x38000000-0x3fffffff could not be reserved
[    0.672087] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.672090] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.672093] system 00:02: ioport range 0x290-0x297 has been reserved
[    0.672106] system 00:0c: iomem range 0xd0000-0xd3fff has been reserved
[    0.672109] system 00:0c: iomem range 0xd5800-0xd7fff has been reserved
[    0.672112] system 00:0c: iomem range 0xf0000-0xfbfff could not be reserved
[    0.672115] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.672118] system 00:0c: iomem range 0x37ff0000-0x37ffffff could not be reserved
[    0.672121] system 00:0c: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.672124] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.672127] system 00:0c: iomem range 0x100000-0x37feffff could not be reserved
[    0.672131] system 00:0c: iomem range 0x38000000-0x3fffffff could not be reserved
[    0.672134] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.672137] system 00:0c: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.672140] system 00:0c: iomem range 0xfefff000-0xfeffffff could not be reserved
[    0.672143] system 00:0c: iomem range 0xfff80000-0xfff80fff could not be reserved
[    0.672146] system 00:0c: iomem range 0xfff90000-0xfffbffff could not be reserved
[    0.672149] system 00:0c: iomem range 0xfffed000-0xfffeffff could not be reserved
[    0.707283] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.707286] pci 0000:00:02.0:   IO window: 0xa000-0xafff
[    0.707290] pci 0000:00:02.0:   MEM window: 0xfd800000-0xfd8fffff
[    0.707294] pci 0000:00:02.0:   PREFETCH window: 0x000000fd700000-0x000000fd7fffff
[    0.707298] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02
[    0.707300] pci 0000:00:03.0:   IO window: 0x8000-0x8fff
[    0.707303] pci 0000:00:03.0:   MEM window: 0xfde00000-0xfdefffff
[    0.707306] pci 0000:00:03.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.707310] pci 0000:00:04.0: PCI bridge, secondary bus 0000:03
[    0.707313] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
[    0.707316] pci 0000:00:04.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.707319] pci 0000:00:04.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
[    0.707323] pci 0000:00:10.0: PCI bridge, secondary bus 0000:04
[    0.707325] pci 0000:00:10.0:   IO window: 0x9000-0x9fff
[    0.707329] pci 0000:00:10.0:   MEM window: 0xfdb00000-0xfdbfffff
[    0.707332] pci 0000:00:10.0:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
[    0.707344] pci 0000:00:02.0: setting latency timer to 64
[    0.707349] pci 0000:00:03.0: setting latency timer to 64
[    0.707354] pci 0000:00:04.0: setting latency timer to 64
[    0.707358] pci 0000:00:10.0: setting latency timer to 64
[    0.707362] bus: 00 index 0 io port: [0, ffff]
[    0.707364] bus: 00 index 1 mmio: [0, ffffffff]
[    0.707366] bus: 01 index 0 io port: [a000, afff]
[    0.707369] bus: 01 index 1 mmio: [fd800000, fd8fffff]
[    0.707371] bus: 01 index 2 mmio: [fd700000, fd7fffff]
[    0.707373] bus: 01 index 3 mmio: [0, 0]
[    0.707375] bus: 02 index 0 io port: [8000, 8fff]
[    0.707377] bus: 02 index 1 mmio: [fde00000, fdefffff]
[    0.707379] bus: 02 index 2 mmio: [fdd00000, fddfffff]
[    0.707381] bus: 02 index 3 mmio: [0, 0]
[    0.707384] bus: 03 index 0 io port: [b000, bfff]
[    0.707386] bus: 03 index 1 mmio: [fdc00000, fdcfffff]
[    0.707388] bus: 03 index 2 mmio: [fd900000, fd9fffff]
[    0.707390] bus: 03 index 3 mmio: [0, 0]
[    0.707392] bus: 04 index 0 io port: [9000, 9fff]
[    0.707394] bus: 04 index 1 mmio: [fdb00000, fdbfffff]
[    0.707396] bus: 04 index 2 mmio: [fda00000, fdafffff]
[    0.707399] bus: 04 index 3 io port: [0, ffff]
[    0.707400] bus: 04 index 4 mmio: [0, ffffffff]
[    0.707414] NET: Registered protocol family 2
[    0.708052] Switched to high resolution mode on CPU 0
[    0.708211] Switched to high resolution mode on CPU 1
[    0.720068] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.720354] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.721062] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.721431] TCP: Hash tables configured (established 131072 bind 65536)
[    0.721434] TCP reno registered
[    0.728095] NET: Registered protocol family 1
[    0.728229] checking if image is initramfs... it is
[    1.382380] Freeing initrd memory: 8263k freed
[    1.383685] audit: initializing netlink socket (disabled)
[    1.383704] type=2000 audit(1243237903.380:1): initialized
[    1.389242] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.392387] VFS: Disk quotas dquot_6.5.1
[    1.392489] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.392592] msgmni has been set to 1764
[    1.392707] io scheduler noop registered
[    1.392710] io scheduler anticipatory registered
[    1.392712] io scheduler deadline registered
[    1.392723] io scheduler cfq registered (default)
[    1.392739] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.392774] pci 0000:00:02.0: Enabling HT MSI Mapping
[    1.392783] pci 0000:00:03.0: Enabling HT MSI Mapping
[    1.392793] pci 0000:00:04.0: Enabling HT MSI Mapping
[    1.392801] pci 0000:00:05.0: Boot video device
[    1.392823] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.409067] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.409078] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    1.409088] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.409100] pci 0000:00:10.1: Enabling HT MSI Mapping
[    1.409249] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.409270] pcieport-driver 0000:00:02.0: found MSI capability
[    1.409290] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.409356] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.409445] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.409467] pcieport-driver 0000:00:03.0: found MSI capability
[    1.409484] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.409547] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.409634] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.409656] pcieport-driver 0000:00:04.0: found MSI capability
[    1.409673] pci_express 0000:00:04.0:pcie00: allocate port service
[    1.409732] pci_express 0000:00:04.0:pcie03: allocate port service
[    1.410170] isapnp: Scanning for PnP cards...
[    1.762986] isapnp: No Plug & Play device found
[    1.803227] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.803377] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.804134] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.806461] brd: module loaded
[    1.806545] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.806686] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.806689] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.806853] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.809156] mice: PS/2 mouse device common for all mice
[    1.809306] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.809335] rtc0: alarms up to one year, y3k
[    1.809528] EISA: Probing bus 0 at eisa.0
[    1.809534] Cannot allocate resource for EISA slot 1
[    1.809537] Cannot allocate resource for EISA slot 2
[    1.809551] Cannot allocate resource for EISA slot 8
[    1.809553] EISA: Detected 0 cards.
[    1.809557] cpuidle: using governor ladder
[    1.809559] cpuidle: using governor menu
[    1.810047] TCP cubic registered
[    1.810074] Using IPI No-Shortcut mode
[    1.810313] registered taskstats version 1
[    1.810454]   Magic number: 9:950:875
[    1.810678] rtc_cmos 00:04: setting system clock to 2009-05-25 07:51:44 UTC (1243237904)
[    1.810682] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.810684] EDD information not available.
[    1.810965] Freeing unused kernel memory: 424k freed
[    1.811025] Write protecting the kernel text: 2576k
[    1.811065] Write protecting the kernel read-only data: 936k
[    1.830552] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.961911] fuse init (API version 7.9)
[    2.033253] fan PNP0C0B:00: registered as cooling_device0
[    2.033260] ACPI: Fan [FAN] (on)
[    2.041280] processor ACPI0007:00: registered as cooling_device1
[    2.041355] processor ACPI0007:01: registered as cooling_device2
[    2.044003] thermal LNXTHERM:01: registered as thermal_zone0
[    2.044418] ACPI: Thermal Zone [THRM] (40 C)
[    2.544929] No dock devices found.
[    2.581186] usbcore: registered new interface driver usbfs
[    2.581214] usbcore: registered new interface driver hub
[    2.581526] usbcore: registered new device driver usb
[    2.594510] SCSI subsystem initialized
[    2.622926] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[    2.622941] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 23 (level, low) -> IRQ 23
[    2.622956] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    2.622959] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    2.623029] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    2.623062] ehci_hcd 0000:00:0b.1: debug port 1
[    2.623066] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    2.623086] ehci_hcd 0000:00:0b.1: irq 23, io mem 0xfe02e000
[    2.623148] libata version 3.00 loaded.
[    2.623285] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.633037] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.633231] usb usb1: configuration #1 chosen from 1 choice
[    2.633257] hub 1-0:1.0: USB hub found
[    2.633268] hub 1-0:1.0: 8 ports detected
[    2.842443] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[    2.842457] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 22 (level, low) -> IRQ 22
[    2.842474] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    2.842477] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    2.842502] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    2.842531] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xfe02f000
[    2.899339] usb usb2: configuration #1 chosen from 1 choice
[    2.899368] hub 2-0:1.0: USB hub found
[    2.899381] hub 2-0:1.0: 8 ports detected
[    3.008032] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    3.104379] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    3.104881] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[    3.104893] pata_acpi 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
[    3.104910] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    3.104919] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    3.105365] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[    3.105373] pata_acpi 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 20 (level, low) -> IRQ 20
[    3.105390] pata_acpi 0000:00:0f.0: setting latency timer to 64
[    3.105398] pata_acpi 0000:00:0f.0: PCI INT A disabled
[    3.105514] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.105900] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    3.105903] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    3.105907] forcedeth 0000:00:14.0: setting latency timer to 64
[    3.105931] nv_probe: set workaround bit for reversed mac addr
[    3.153726] usb 1-5: configuration #1 chosen from 1 choice
[    3.376044] usb 1-8: new high speed USB device using ehci_hcd and address 5
[    3.509444] usb 1-8: configuration #1 chosen from 1 choice
[    3.624521] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x50ef @ 1, addr 00:19:21:5a:70:e0
[    3.624526] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[    3.626144] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    3.626161] ohci1394 0000:04:09.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    3.626167] ohci1394 0000:04:09.0: setting latency timer to 64
[    3.678909] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fdbff000-fdbff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.687410] usb 2-4: new low speed USB device using ohci_hcd and address 2
[    3.687508] pata_amd 0000:00:0d.0: version 0.3.10
[    3.689502] pata_amd 0000:00:0d.0: setting latency timer to 64
[    3.689605] scsi0 : pata_amd
[    3.689729] scsi1 : pata_amd
[    3.690612] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[    3.690615] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[    3.868519] ata1.00: ATA-7: HDT722525DLAT80, V44OA96A, max UDMA/133
[    3.868523] ata1.00: 488397168 sectors, multi 16: LBA48 
[    3.868539] ata1: nv_mode_filter: 0x7f39f&0x7f01f->0x7f01f, BIOS=0x7f000 (0xc700c000) ACPI=0x7f01f (15:600:0x13)
[    3.884434] ata1.00: configured for UDMA/133
[    3.897256] usb 2-4: configuration #1 chosen from 1 choice
[    4.048565] ata2.00: ATAPI: PHILIPS DVD8801, GW02, max UDMA/33
[    4.048580] ata2: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc700c000) ACPI=0x701f (60:600:0x13)
[    4.064491] ata2.00: configured for UDMA/33
[    4.064628] scsi 0:0:0:0: Direct-Access     ATA      HDT722525DLAT80  V44O PQ: 0 ANSI: 5
[    4.066655] scsi 1:0:0:0: CD-ROM            PHILIPS  DVD8801          GW02 PQ: 0 ANSI: 5
[    4.066897] sata_nv 0000:00:0e.0: version 3.5
[    4.066912] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
[    4.066915] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    4.066961] sata_nv 0000:00:0e.0: setting latency timer to 64
[    4.067119] scsi2 : sata_nv
[    4.067194] scsi3 : sata_nv
[    4.067399] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 21
[    4.067402] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 21
[    4.204051] usb 2-6: new full speed USB device using ohci_hcd and address 3
[    4.394463] ata3: SATA link down (SStatus 0 SControl 300)
[    4.420579] usb 2-6: configuration #1 chosen from 1 choice
[    4.425166] usbcore: registered new interface driver libusual
[    4.425661] usbcore: registered new interface driver hiddev
[    4.431386] input: USB Optical Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0/input/input2
[    4.433392] Initializing USB Mass Storage driver...
[    4.433993] scsi4 : SCSI emulation for USB Mass Storage devices
[    4.434661] scsi5 : SCSI emulation for USB Mass Storage devices
[    4.434761] usb-storage: device found at 5
[    4.434763] usb-storage: waiting for device to settle before scanning
[    4.435575] usb-storage: device found at 3
[    4.435578] usb-storage: waiting for device to settle before scanning
[    4.442817] input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:0b.0-4
[    4.443763] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.443799] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.444825] scsi6 : SCSI emulation for USB Mass Storage devices
[    4.444958] usb-storage: device found at 3
[    4.444960] usb-storage: waiting for device to settle before scanning
[    4.444984] usbcore: registered new interface driver usbhid
[    4.444988] usbhid: v2.6:USB HID core driver
[    4.444989] usbcore: registered new interface driver usb-storage
[    4.444995] USB Mass Storage support registered.
[    4.722455] ata4: SATA link down (SStatus 0 SControl 300)
[    4.722528] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 20 (level, low) -> IRQ 20
[    4.722533] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    4.722582] sata_nv 0000:00:0f.0: setting latency timer to 64
[    4.722739] scsi7 : sata_nv
[    4.723129] scsi8 : sata_nv
[    4.723348] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 20
[    4.723351] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 20
[    4.952245] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000ae6ff6f5627]
[    5.050456] ata5: SATA link down (SStatus 0 SControl 300)
[    5.378454] ata6: SATA link down (SStatus 0 SControl 300)
[    5.406975] Driver 'sd' needs updating - please use bus_type methods
[    5.407150] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    5.407179] sd 0:0:0:0: [sda] Write Protect is off
[    5.407182] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.407230] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.407323] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    5.407348] sd 0:0:0:0: [sda] Write Protect is off
[    5.407350] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.407398] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.407403]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    5.423765]  sda1 sda2
[    5.423915] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.432375] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    5.432381] Uniform CD-ROM driver Revision: 3.20
[    5.432480] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    9.432188] usb-storage: device scan complete
[    9.432411] usb-storage: device scan complete
[    9.434411] scsi 5:0:0:0: Direct-Access     SanDisk  Cruzer           8.02 PQ: 0 ANSI: 0 CCS
[    9.439154] sd 5:0:0:0: [sdb] 31768575 512-byte hardware sectors (16266 MB)
[    9.440284] sd 5:0:0:0: [sdb] Write Protect is off
[    9.440288] sd 5:0:0:0: [sdb] Mode Sense: 45 00 00 08
[    9.440291] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[    9.441759] sd 5:0:0:0: [sdb] 31768575 512-byte hardware sectors (16266 MB)
[    9.442167] usb-storage: device scan complete
[    9.442654] scsi 4:0:0:0: Direct-Access     CORNICE  Inc. Dragon      0811 PQ: 0 ANSI: 0
[    9.443363] sd 5:0:0:0: [sdb] Write Protect is off
[    9.443365] sd 5:0:0:0: [sdb] Mode Sense: 45 00 00 08
[    9.443368] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[    9.443373]  sdb: sdb1
[    9.445711] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[    9.445852] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    9.446892] sd 4:0:0:0: [sdc] 15625008 512-byte hardware sectors (8000 MB)
[    9.448661] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[    9.448668] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    9.450825] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    9.452066] sd 4:0:0:0: [sdc] 15625008 512-byte hardware sectors (8000 MB)
[    9.459666] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled
[    9.459672] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[    9.459680]  sdc:<5>scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    9.467177] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    9.474164] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   10.209787]  sdc1 sdc2 <<6>aufs 20080922
[   11.769029] loop: module loaded
[   11.830377] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   13.178550] kjournald starting.  Commit interval 5 seconds
[   13.178608] EXT3 FS on loop1, internal journal
[   13.178616] ext3_orphan_cleanup: deleting unreferenced inode 19
[   13.178761] ext3_orphan_cleanup: deleting unreferenced inode 17
[   13.178787] ext3_orphan_cleanup: deleting unreferenced inode 16
[   13.178811] ext3_orphan_cleanup: deleting unreferenced inode 15
[   13.178819] EXT3-fs: loop1: 4 orphan inodes deleted
[   13.178821] EXT3-fs: recovery complete.
[   13.179129] EXT3-fs: mounted filesystem with ordered data mode.
[   40.321035] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[   44.408718] udevd version 124 started
[   45.654086] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.667841] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   45.693247] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   45.693288] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   45.806810] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   45.833077] ACPI: Power Button (FF) [PWRF]
[   45.833166] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   45.865029] ACPI: Power Button (CM) [PWRB]
[   47.140344] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   48.220738] parport_pc 00:09: reported by Plug and Play ACPI
[   48.220806] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   50.041439] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   50.041447] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   50.041471] HDA Intel 0000:00:10.1: setting latency timer to 64
[   50.074847] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   70.588031] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[   78.378812] lp0: using parport0 (interrupt-driven).
[   79.320672] ip_tables: (C) 2000-2006 Netfilter Core Team
[   80.110163] ACPI: WMI: Mapper loaded
[   80.684766] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (2 cpu cores) (version 2.20.00)
[   80.684832] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xe
[   80.684836] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x10
[   80.684839] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x10
[   80.684841] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   81.191197] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   81.248916] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   81.248929] apm: disabled - APM is not SMP safe.
[   81.315109] ppdev: user-space parallel port driver
[   82.518929] Bluetooth: Core ver 2.13
[   82.521077] NET: Registered protocol family 31
[   82.521083] Bluetooth: HCI device and connection manager initialized
[   82.521087] Bluetooth: HCI socket layer initialized
[   82.539859] Bluetooth: L2CAP ver 2.11
[   82.539868] Bluetooth: L2CAP socket layer initialized
[   82.553602] Bluetooth: RFCOMM socket layer initialized
[   82.556407] Bluetooth: RFCOMM TTY layer initialized
[   82.556418] Bluetooth: RFCOMM ver 1.10
[   82.557174] Bluetooth: SCO (Voice Link) ver 0.6
[   82.557180] Bluetooth: SCO socket layer initialized
[   82.595359] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   82.595369] Bluetooth: BNEP filters: protocol multicast
[   82.610458] Bridge firewalling registered
[   82.611841] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   83.208025] Clocksource tsc unstable (delta = -91557697 ns)
[   85.299196] lxsession[8967]: segfault at 0 ip b7d7bd28 sp bff4597c error 4 in libc-2.8.90.so[b7d05000+158000]
[   86.508825] NET: Registered protocol family 10
[   86.509398] lo: Disabled Privacy Extensions
[   86.888565] NET: Registered protocol family 17
[   97.420032] eth0: no IPv6 routers present
[  100.844043] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  131.100056] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  161.360043] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  191.616044] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  191.762498] sd 4:0:0:0: [sdc] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[  191.762519] end_request: I/O error, dev sdc, sector 14844056
[  191.762532] Buffer I/O error on device sdc, logical block 1855507
[  221.872066] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  252.128060] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  282.384071] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  312.644889] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  342.900052] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  373.168069] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  373.317195] sd 4:0:0:0: [sdc] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[  373.317222] end_request: I/O error, dev sdc, sector 14844056
[  373.317237] Buffer I/O error on device sdc, logical block 1855507
[  373.317283]  >
[  373.317598] sd 4:0:0:0: [sdc] Attached SCSI disk
[  373.317841] sd 4:0:0:0: Attached scsi generic sg3 type 0
[  373.343102] sd 6:0:0:0: [sdd] Attached SCSI removable disk
[  373.343497] sd 6:0:0:0: Attached scsi generic sg4 type 0
[  373.353697] sd 6:0:0:1: [sde] Attached SCSI removable disk
[  373.353965] sd 6:0:0:1: Attached scsi generic sg5 type 0
[  373.364478] sd 6:0:0:2: [sdf] Attached SCSI removable disk
[  373.364621] sd 6:0:0:2: Attached scsi generic sg6 type 0
[  373.381982] sd 6:0:0:3: [sdg] Attached SCSI removable disk
[  373.382253] sd 6:0:0:3: Attached scsi generic sg7 type 0
[  416.769057] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  447.024060] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  477.280042] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  507.537098] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[  537.792065] usb 1-5: reset high speed USB device using ehci_hcd and address 3
```

---

### Post by albinootje on 2009-05-25
> **linux000019 said:**
> 
Disk /dev/sda: 250.0 GB, 250059350016 bytes
Disk /dev/sdb: 16.2 GB, 16265510400 bytes

I assume that your usb disk is not the 16 Gb disk, right ?
> 
```

[    9.459680]  sdc:<5>scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0

[  191.762498] sd 4:0:0:0: [sdc] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[  191.762519] end_request: I/O error, dev sdc, sector 14844056
[  191.762532] Buffer I/O error on device sdc, logical block 1855507

[  537.792065] usb 1-5: reset high speed USB device using ehci_hcd and address 3
```

Thanks. 
Your usb drive is recognized, but for some reason it doesn't show up in fdisk.
And you might have a bad block on it.

---

### Post by linux000019 on 2009-05-25
pulling plug mightve causes this; and yes, the sdc drive showed up find yesterday today it won't. funny thing is i can still boot fedora(the previous os i was trying to overwrite with crunchbang) if i select it in boot menu.

---

