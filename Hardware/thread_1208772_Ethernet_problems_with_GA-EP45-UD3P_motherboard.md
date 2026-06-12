---
title: "Ethernet problems with GA-EP45-UD3P motherboard"
date: 2009-07-09
forum: Hardware
---

### Post by TheBlackSun on 2009-07-09
This motherboard has two Realtek 8111C ethernet controllers, but ubuntu is only detecting one of them. The one that is detected is fully functional. Both ethernet controllers are enabled in the BIOS and I see no reason why both shouldn't be working. What should I do to get the other one working?

Thanks

```

$ lspci | grep -i ethernet
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

```

$ sudo lspci -v
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, fast devsel, latency 0, IRQ 2298
	I/O ports at b000 [size=256]
	Memory at e8010000 (64-bit, prefetchable) [size=4K]
	Memory at e8000000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at e8020000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [d0] Vital Product Data <?>
	Capabilities: [100] AdvaInced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 78-56-34-12-78-56-34-12
	Kernel driver in use: r8169
	Kernel modules: r8169

```

```

$ lsmod | grep r8169
r8169                  46596  0 
mii                    14464  1 r8169

```

```

$ cat /etc/network/interfaces
auto lo eth0
iface lo inet loopback

iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask xxx.xxx.xxx.xxx
network xxx.xxx.xxx.xxx
broadcasst xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx

```

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:9d:95:d7  
          inet addr:xxx.xxx.xxx.xxx  Bcast:xxx.xxx.xxx.xxx  Mask:xxx.xxx.xxx.xxx
          inet6 addr: xxx.xxx.xxx.xxx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33437 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7033 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10464636 (10.4 MB)  TX bytes:1242561 (1.2 MB)
          Interrupt:250 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

```

```

$ dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-13-generic (buildd@yellow) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 (Ubuntu 2.6.28-13.45-generic)
[    0.000000] Command line: root=UUID=3ec3def8-3b61-460e-9c07-8fed2050406f ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfeb0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfeb0000 - 00000000cfee2000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfee2000 - 00000000cfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000e4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xcfeb0 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000008000 (usable)
[    0.000000]  modified: 0000000000008000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cfeb0000 (usable)
[    0.000000]  modified: 00000000cfeb0000 - 00000000cfee2000 (ACPI NVS)
[    0.000000]  modified: 00000000cfee2000 - 00000000cfef0000 (ACPI data)
[    0.000000]  modified: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000e4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfeb0000
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cfeb0000 page 4k
[    0.000000] kernel direct mapping tables up to cfeb0000 @ 10000-16000
[    0.000000] last_map_addr: cfeb0000 end: cfeb0000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ 14000-1a000
[    0.000000] last_map_addr: 130000000 end: 130000000
[    0.000000] RAMDISK: 3781b000 - 37fef6cf
[    0.000000] ACPI: RSDP 000F7830, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT CFEE2040, 0040 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP CFEE20C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT CFEE2180, 50F5 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS CFEB0000, 0040
[    0.000000] ACPI: EUDS CFEE7A00, 0500 (r1 GBT                    0             0)
[    0.000000] ACPI: HPET CFEE78C0, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG CFEE7940, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: TCPA CFEE79C0, 0032 (r1 HTC    HTCACPI  42302E31 GBTU        0)
[    0.000000] ACPI: APIC CFEE72C0, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: SSDT CFEE8570, 03AB (r1  PmRef    CpuPm     3000 INTL 20040311)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0130000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b7bbb0]    TEXT DATA BSS ==> [0000200000 - 0000b7bbb0]
[    0.000000]   #3 [003781b000 - 0037fef6cf]          RAMDISK ==> [003781b000 - 0037fef6cf]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]
[    0.000000]   #6 [0000014000 - 0000015000]          PGTABLE ==> [0000014000 - 0000015000]
[    0.000000] found SMP MP-table at [ffff8800000f5a00] 000f5a00
[    0.000000]  [ffffe20000000000-ffffe200043fffff] PMD -> [ffff880028200000-ffff88002c5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x00000008
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x000cfeb0
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1048117
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2533 pages reserved
[    0.000000]   DMA zone: 1384 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833256 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000008000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfeb0000 - 00000000cfee2000
[    0.000000] PM: Registered nosave memory: 00000000cfee2000 - 00000000cfef0000
[    0.000000] PM: Registered nosave memory: 00000000cfef0000 - 00000000cff00000
[    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000e4000000
[    0.000000] PM: Registered nosave memory: 00000000e4000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e6000000 (gap: e4000000:1ac00000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1028560
[    0.000000] Kernel command line: root=UUID=3ec3def8-3b61-460e-9c07-8fed2050406f ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3330.286 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] allocated 49807360 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.004000] Placing software IO TLB between 0x20000000 - 0x24000000
[    0.004000] Memory: 3982960k/4980736k available (4743k kernel code, 788268k absent, 208612k reserved, 2525k data, 532k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 6660.57 BogoMIPS (lpj=13321144)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] ACPI: Core revision 20080926
[    0.004000] ACPI: Checking initramfs for custom DSDT
[    0.210011] Setting APIC routing to flat
[    0.210342] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.250036] CPU0: Intel(R) Core(TM)2 Duo CPU     E7300  @ 2.66GHz stepping 06
[    0.252001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 6659.89 BogoMIPS (lpj=13319781)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.336479] CPU1: Intel(R) Core(TM)2 Duo CPU     E7300  @ 2.66GHz stepping 06
[    0.336494] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.340032] Brought up 2 CPUs
[    0.340034] Total of 2 processors activated (13320.46 BogoMIPS).
[    0.340073] CPU0 attaching sched-domain:
[    0.340074]  domain 0: span 0-1 level MC
[    0.340076]   groups: 0 1
[    0.340079] CPU1 attaching sched-domain:
[    0.340080]  domain 0: span 0-1 level MC
[    0.340081]   groups: 1 0
[    0.340125] net_namespace: 1400 bytes
[    0.340125] Booting paravirtualized kernel on bare hardware
[    0.340180] Time: 18:30:51  Date: 07/09/09
[    0.340180] regulator: core version 0.5
[    0.340180] NET: Registered protocol family 16
[    0.340180] ACPI: bus type pci registered
[    0.340180] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.340180] PCI: MCFG area at e0000000 reserved in E820
[    0.341670] PCI: Using MMCONFIG at e0000000 - e3ffffff
[    0.341671] PCI: Using configuration type 1 for base access
[    0.342043] ACPI: EC: Look up EC in DSDT
[    0.347342] ACPI: Interpreter enabled
[    0.347345] ACPI: (supports S0 S3 S4 S5)
[    0.347358] ACPI: Using IOAPIC for interrupt routing
[    0.350585] ACPI: No dock devices found.
[    0.350592] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.350643] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.350644] pci 0000:00:01.0: PME# disabled
[    0.350694] pci 0000:00:1a.0: reg 20 io port: [0xd000-0xd01f]
[    0.350739] pci 0000:00:1a.1: reg 20 io port: [0xd100-0xd11f]
[    0.350785] pci 0000:00:1a.2: reg 20 io port: [0xd200-0xd21f]
[    0.350823] pci 0000:00:1a.7: reg 10 32bit mmio: [0xe8405000-0xe84053ff]
[    0.350875] pci 0000:00:1b.0: reg 10 64bit mmio: [0xe8400000-0xe8403fff]
[    0.350895] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.350897] pci 0000:00:1b.0: PME# disabled
[    0.350929] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.350931] pci 0000:00:1c.0: PME# disabled
[    0.350965] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.350967] pci 0000:00:1c.3: PME# disabled
[    0.350999] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.351001] pci 0000:00:1c.4: PME# disabled
[    0.351034] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.351036] pci 0000:00:1c.5: PME# disabled
[    0.351074] pci 0000:00:1d.0: reg 20 io port: [0xd300-0xd31f]
[    0.351119] pci 0000:00:1d.1: reg 20 io port: [0xd400-0xd41f]
[    0.351164] pci 0000:00:1d.2: reg 20 io port: [0xd500-0xd51f]
[    0.351201] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe8404000-0xe84043ff]
[    0.351335] pci 0000:00:1f.2: reg 10 io port: [0xd600-0xd607]
[    0.351339] pci 0000:00:1f.2: reg 14 io port: [0xd700-0xd703]
[    0.351343] pci 0000:00:1f.2: reg 18 io port: [0xd800-0xd807]
[    0.351346] pci 0000:00:1f.2: reg 1c io port: [0xd900-0xd903]
[    0.351350] pci 0000:00:1f.2: reg 20 io port: [0xda00-0xda0f]
[    0.351353] pci 0000:00:1f.2: reg 24 io port: [0xdb00-0xdb0f]
[    0.351378] pci 0000:00:1f.3: reg 10 64bit mmio: [0xe8406000-0xe84060ff]
[    0.351387] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.351416] pci 0000:00:1f.5: reg 10 io port: [0xdd00-0xdd07]
[    0.351420] pci 0000:00:1f.5: reg 14 io port: [0xde00-0xde03]
[    0.351423] pci 0000:00:1f.5: reg 18 io port: [0xdf00-0xdf07]
[    0.351427] pci 0000:00:1f.5: reg 1c io port: [0xe000-0xe003]
[    0.351431] pci 0000:00:1f.5: reg 20 io port: [0xe100-0xe10f]
[    0.351434] pci 0000:00:1f.5: reg 24 io port: [0xe200-0xe20f]
[    0.351467] pci 0000:01:00.0: reg 10 64bit mmio: [0xd0000000-0xdfffffff]
[    0.351473] pci 0000:01:00.0: reg 18 64bit mmio: [0xe5000000-0xe500ffff]
[    0.351477] pci 0000:01:00.0: reg 20 io port: [0x9000-0x90ff]
[    0.351483] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.351488] pci 0000:01:00.0: supports D1 D2
[    0.351511] pci 0000:01:00.1: reg 10 64bit mmio: [0xe5010000-0xe5013fff]
[    0.351529] pci 0000:01:00.1: supports D1 D2
[    0.351560] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.351561] pci 0000:00:01.0: bridge 32bit mmio: [0xe4000000-0xe5ffffff]
[    0.351564] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.351668] pci 0000:03:00.0: reg 24 32bit mmio: [0xe8100000-0xe8101fff]
[    0.351684] pci 0000:03:00.0: PME# supported from D3hot
[    0.351688] pci 0000:03:00.0: PME# disabled
[    0.351731] pci 0000:03:00.1: reg 10 io port: [0xa000-0xa007]
[    0.351738] pci 0000:03:00.1: reg 14 io port: [0xa100-0xa103]
[    0.351745] pci 0000:03:00.1: reg 18 io port: [0xa200-0xa207]
[    0.351752] pci 0000:03:00.1: reg 1c io port: [0xa300-0xa303]
[    0.351759] pci 0000:03:00.1: reg 20 io port: [0xa400-0xa40f]
[    0.351818] pci 0000:00:1c.3: bridge io port: [0xa000-0xafff]
[    0.351821] pci 0000:00:1c.3: bridge 32bit mmio: [0xe8100000-0xe81fffff]
[    0.351860] pci 0000:04:00.0: reg 10 io port: [0xb000-0xb0ff]
[    0.351876] pci 0000:04:00.0: reg 18 64bit mmio: [0xe8010000-0xe8010fff]
[    0.351887] pci 0000:04:00.0: reg 20 64bit mmio: [0xe8000000-0xe800ffff]
[    0.351893] pci 0000:04:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.351901] pci 0000:04:00.0: supports D1 D2
[    0.351902] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.351906] pci 0000:04:00.0: PME# disabled
[    0.351945] pci 0000:00:1c.4: bridge io port: [0xb000-0xbfff]
[    0.351948] pci 0000:00:1c.4: bridge 32bit mmio: [0xe6000000-0xe6ffffff]
[    0.351951] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xe8000000-0xe80fffff]
[    0.351978] pci 0000:00:1c.5: bridge io port: [0xc000-0xcfff]
[    0.351981] pci 0000:00:1c.5: bridge 32bit mmio: [0xe7000000-0xe7ffffff]
[    0.351985] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xe8200000-0xe82fffff]
[    0.352029] pci 0000:06:07.0: reg 10 32bit mmio: [0xe8304000-0xe83047ff]
[    0.352034] pci 0000:06:07.0: reg 14 32bit mmio: [0xe8300000-0xe8303fff]
[    0.352061] pci 0000:06:07.0: supports D1 D2
[    0.352062] pci 0000:06:07.0: PME# supported from D0 D1 D2 D3hot
[    0.352065] pci 0000:06:07.0: PME# disabled
[    0.352093] pci 0000:00:1e.0: transparent bridge
[    0.352097] pci 0000:00:1e.0: bridge 32bit mmio: [0xe8300000-0xe83fffff]
[    0.352116] bus 00 -> node 0
[    0.352120] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.352271] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.352333] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.352393] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.352452] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[    0.352511] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.363276] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.363348] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 *14 15)
[    0.363420] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.363491] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 *15)
[    0.363561] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.363639] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.363709] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.363781] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.363983] ACPI: WMI: Mapper loaded
[    0.364062] SCSI subsystem initialized
[    0.364071] libata version 3.00 loaded.
[    0.364071] usbcore: registered new interface driver usbfs
[    0.364071] usbcore: registered new interface driver hub
[    0.364071] usbcore: registered new device driver usb
[    0.364071] PCI: Using ACPI for IRQ routing
[    0.376010] Bluetooth: Core ver 2.13
[    0.376021] NET: Registered protocol family 31
[    0.376021] Bluetooth: HCI device and connection manager initialized
[    0.376021] Bluetooth: HCI socket layer initialized
[    0.376021] NET: Registered protocol family 8
[    0.376021] NET: Registered protocol family 20
[    0.376037] NetLabel: Initializing
[    0.376037] NetLabel:  domain hash size = 128
[    0.376038] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.376046] NetLabel:  unlabeled traffic allowed by default
[    0.376065] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.376068] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.380055] AppArmor: AppArmor Filesystem Enabled
[    0.392008] pnp: PnP ACPI init
[    0.392015] ACPI: bus type pnp registered
[    0.394036] pnp: PnP ACPI: found 17 devices
[    0.394037] ACPI: ACPI bus type pnp unregistered
[    0.394042] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.394043] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.394045] system 00:01: ioport range 0x800-0x805 has been reserved
[    0.394046] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.394047] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.394049] system 00:01: ioport range 0x4c0-0x4ff could not be reserved
[    0.394053] system 00:0d: ioport range 0x400-0x4bf has been reserved
[    0.394056] system 00:0e: iomem range 0xe0000000-0xe3ffffff has been reserved
[    0.394059] system 00:0f: iomem range 0xcf800-0xcffff has been reserved
[    0.394060] system 00:0f: iomem range 0xf0000-0xf7fff could not be reserved
[    0.394062] system 00:0f: iomem range 0xf8000-0xfbfff could not be reserved
[    0.394063] system 00:0f: iomem range 0xfc000-0xfffff could not be reserved
[    0.394065] system 00:0f: iomem range 0xcfeb0000-0xcfefffff could not be reserved
[    0.394066] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[    0.394067] system 00:0f: iomem range 0x100000-0xcfeaffff could not be reserved
[    0.394069] system 00:0f: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.394070] system 00:0f: iomem range 0xfed10000-0xfed1dfff has been reserved
[    0.394071] system 00:0f: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.394073] system 00:0f: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.394074] system 00:0f: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.394075] system 00:0f: iomem range 0xfff00000-0xffffffff has been reserved
[    0.394077] system 00:0f: iomem range 0xe0000-0xeffff has been reserved
[    0.398670] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.398672] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.398674] pci 0000:00:01.0:   MEM window: 0xe4000000-0xe5ffffff
[    0.398676] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.398678] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.398679] pci 0000:00:1c.0:   IO window: disabled
[    0.398682] pci 0000:00:1c.0:   MEM window: disabled
[    0.398684] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.398688] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:03
[    0.398690] pci 0000:00:1c.3:   IO window: 0xa000-0xafff
[    0.398693] pci 0000:00:1c.3:   MEM window: 0xe8100000-0xe81fffff
[    0.398695] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.398699] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:04
[    0.398700] pci 0000:00:1c.4:   IO window: 0xb000-0xbfff
[    0.398703] pci 0000:00:1c.4:   MEM window: 0xe6000000-0xe6ffffff
[    0.398706] pci 0000:00:1c.4:   PREFETCH window: 0x000000e8000000-0x000000e80fffff
[    0.398709] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:05
[    0.398711] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
[    0.398714] pci 0000:00:1c.5:   MEM window: 0xe7000000-0xe7ffffff
[    0.398716] pci 0000:00:1c.5:   PREFETCH window: 0x000000e8200000-0x000000e82fffff
[    0.398720] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.398721] pci 0000:00:1e.0:   IO window: disabled
[    0.398724] pci 0000:00:1e.0:   MEM window: 0xe8300000-0xe83fffff
[    0.398726] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.398734] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.398736] pci 0000:00:01.0: setting latency timer to 64
[    0.398740] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.398743] pci 0000:00:1c.0: setting latency timer to 64
[    0.398748] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.398750] pci 0000:00:1c.3: setting latency timer to 64
[    0.398754] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.398757] pci 0000:00:1c.4: setting latency timer to 64
[    0.398761] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.398764] pci 0000:00:1c.5: setting latency timer to 64
[    0.398768] pci 0000:00:1e.0: setting latency timer to 64
[    0.398770] bus: 00 index 0 io port: [0x00-0xffff]
[    0.398771] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.398772] bus: 01 index 0 io port: [0x9000-0x9fff]
[    0.398773] bus: 01 index 1 mmio: [0xe4000000-0xe5ffffff]
[    0.398774] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.398775] bus: 01 index 3 mmio: [0x0-0x0]
[    0.398776] bus: 02 index 0 mmio: [0x0-0x0]
[    0.398777] bus: 02 index 1 mmio: [0x0-0x0]
[    0.398778] bus: 02 index 2 mmio: [0x0-0x0]
[    0.398779] bus: 02 index 3 mmio: [0x0-0x0]
[    0.398779] bus: 03 index 0 io port: [0xa000-0xafff]
[    0.398780] bus: 03 index 1 mmio: [0xe8100000-0xe81fffff]
[    0.398781] bus: 03 index 2 mmio: [0x0-0x0]
[    0.398782] bus: 03 index 3 mmio: [0x0-0x0]
[    0.398783] bus: 04 index 0 io port: [0xb000-0xbfff]
[    0.398784] bus: 04 index 1 mmio: [0xe6000000-0xe6ffffff]
[    0.398785] bus: 04 index 2 mmio: [0xe8000000-0xe80fffff]
[    0.398786] bus: 04 index 3 mmio: [0x0-0x0]
[    0.398787] bus: 05 index 0 io port: [0xc000-0xcfff]
[    0.398788] bus: 05 index 1 mmio: [0xe7000000-0xe7ffffff]
[    0.398789] bus: 05 index 2 mmio: [0xe8200000-0xe82fffff]
[    0.398790] bus: 05 index 3 mmio: [0x0-0x0]
[    0.398791] bus: 06 index 0 mmio: [0x0-0x0]
[    0.398792] bus: 06 index 1 mmio: [0xe8300000-0xe83fffff]
[    0.398793] bus: 06 index 2 mmio: [0x0-0x0]
[    0.398794] bus: 06 index 3 io port: [0x00-0xffff]
[    0.398795] bus: 06 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.398800] NET: Registered protocol family 2
[    0.432048] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.432285] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.433394] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.433764] TCP: Hash tables configured (established 262144 bind 65536)
[    0.433766] TCP reno registered
[    0.444100] NET: Registered protocol family 1
[    0.444176] checking if image is initramfs...<7>Switched to high resolution mode on CPU 1
[    0.503996] Switched to high resolution mode on CPU 0
[    0.644975]  it is
[    0.857324] Freeing initrd memory: 8017k freed
[    0.859618] audit: initializing netlink socket (disabled)
[    0.859638] type=2000 audit(1247164250.856:1): initialized
[    0.864764] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.865444] VFS: Disk quotas dquot_6.5.1
[    0.865473] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.865786] fuse init (API version 7.10)
[    0.865829] msgmni has been set to 7796
[    0.865924] alg: No test for stdrng (krng)
[    0.865930] io scheduler noop registered
[    0.865932] io scheduler anticipatory registered
[    0.865933] io scheduler deadline registered
[    0.865954] io scheduler cfq registered (default)
[    0.866065] pci 0000:01:00.0: Boot video device
[    0.867690] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.867708] pcieport-driver 0000:00:01.0: found MSI capability
[    0.867721] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    0.867726] pci_express 0000:00:01.0:pcie00: allocate port service
[    0.867733] pci_express 0000:00:01.0:pcie03: allocate port service
[    0.867759] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.867781] pcieport-driver 0000:00:1c.0: found MSI capability
[    0.867797] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    0.867804] pci_express 0000:00:1c.0:pcie00: allocate port service
[    0.867812] pci_express 0000:00:1c.0:pcie02: allocate port service
[    0.867820] pci_express 0000:00:1c.0:pcie03: allocate port service
[    0.867855] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.867877] pcieport-driver 0000:00:1c.3: found MSI capability
[    0.867893] pcieport-driver 0000:00:1c.3: irq 2301 for MSI/MSI-X
[    0.867900] pci_express 0000:00:1c.3:pcie00: allocate port service
[    0.867907] pci_express 0000:00:1c.3:pcie02: allocate port service
[    0.867913] pci_express 0000:00:1c.3:pcie03: allocate port service
[    0.867947] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    0.867970] pcieport-driver 0000:00:1c.4: found MSI capability
[    0.867985] pcieport-driver 0000:00:1c.4: irq 2300 for MSI/MSI-X
[    0.867993] pci_express 0000:00:1c.4:pcie00: allocate port service
[    0.867999] pci_express 0000:00:1c.4:pcie02: allocate port service
[    0.868005] pci_express 0000:00:1c.4:pcie03: allocate port service
[    0.868042] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.868064] pcieport-driver 0000:00:1c.5: found MSI capability
[    0.868080] pcieport-driver 0000:00:1c.5: irq 2299 for MSI/MSI-X
[    0.868087] pci_express 0000:00:1c.5:pcie00: allocate port service
[    0.868093] pci_express 0000:00:1c.5:pcie02: allocate port service
[    0.868100] pci_express 0000:00:1c.5:pcie03: allocate port service
[    0.868140] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.868372] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.868460] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.868462] ACPI: Power Button (FF) [PWRF]
[    0.868486] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.868488] ACPI: Power Button (CM) [PWRB]
[    0.868783] ACPI: SSDT CFEE7F50, 026C (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
[    0.868899] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    0.868912] processor ACPI_CPU:00: registered as cooling_device0
[    0.868914] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.869046] ACPI: SSDT CFEE8410, 0152 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[    0.869157] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    0.869166] processor ACPI_CPU:01: registered as cooling_device1
[    0.869168] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.900636] Linux agpgart interface v0.103
[    0.900641] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    0.900716] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.900916] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.901349] brd: module loaded
[    0.901515] loop: module loaded
[    0.901553] Fixed MDIO Bus: probed
[    0.901556] PPP generic driver version 2.4.2
[    0.901587] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.901601] Driver 'sd' needs updating - please use bus_type methods
[    0.901606] Driver 'sr' needs updating - please use bus_type methods
[    0.901630] ahci 0000:03:00.0: version 3.0
[    0.901640] ahci 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.916530] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    0.916533] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    0.916539] ahci 0000:03:00.0: setting latency timer to 64
[    0.916652] scsi0 : ahci
[    0.916701] scsi1 : ahci
[    0.916737] ata1: SATA max UDMA/133 abar m8192@0xe8100000 port 0xe8100100 irq 19
[    0.916739] ata2: SATA max UDMA/133 abar m8192@0xe8100000 port 0xe8100180 irq 19
[    1.400017] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.408904] ata1.00: ATA-8: WDC WD1600AAJS-07WAA0, 58.01D58, max UDMA/133
[    1.408907] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.409678] ata1.00: configured for UDMA/133
[    1.908020] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.908731] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S223F, SB00, max UDMA/100, ATAPI AN
[    1.909688] ata2.00: configured for UDMA/100
[    1.924088] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-0 58.0 PQ: 0 ANSI: 5
[    1.924137] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    1.924146] sd 0:0:0:0: [sda] Write Protect is off
[    1.924148] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.924161] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.924196] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    1.924204] sd 0:0:0:0: [sda] Write Protect is off
[    1.924205] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.924218] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.924220]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 sda12 sda13 sda14 sda15 >
[    2.034787] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.034811] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.035296] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223F  SB00 PQ: 0 ANSI: 5
[    2.038374] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.038377] Uniform CD-ROM driver Revision: 3.20
[    2.038444] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.038464] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.038491] ata_piix 0000:00:1f.2: version 2.12
[    2.038497] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.038499] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    2.038524] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.038556] scsi2 : ata_piix
[    2.038586] scsi3 : ata_piix
[    2.039046] ata3: SATA max UDMA/133 cmd 0xd600 ctl 0xd700 bmdma 0xda00 irq 19
[    2.039049] ata4: SATA max UDMA/133 cmd 0xd800 ctl 0xd900 bmdma 0xda08 irq 19
[    2.832051] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.832061] ata3.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.856173] ata3.00: HPA unlocked: 1953523055 -> 1953525168, native 1953525168
[    2.856175] ata3.00: ATA-8: WDC WD10EACS-00D6B1, 01.01A01, max UDMA/133
[    2.856176] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.856331] ata3.01: ATA-8: WDC WD10EACS-00D6B0, 01.01A01, max UDMA/133
[    2.856333] ata3.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.873139] ata3.00: configured for UDMA/133
[    2.888434] ata3.01: configured for UDMA/133
[    3.684051] ata4.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.684059] ata4.01: SATA link down (SStatus 0 SControl 300)
[    3.692731] ata4.00: ATA-8: WDC WD10EACS-00D6B1, 01.01A01, max UDMA/133
[    3.692733] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.700730] ata4.00: configured for UDMA/133
[    3.700784] scsi 2:0:0:0: Direct-Access     ATA      WDC WD10EACS-00D 01.0 PQ: 0 ANSI: 5
[    3.700828] sd 2:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    3.700837] sd 2:0:0:0: [sdb] Write Protect is off
[    3.700838] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.700852] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.700879] sd 2:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    3.700887] sd 2:0:0:0: [sdb] Write Protect is off
[    3.700889] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.700905] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.700907]  sdb: sdb1
[    3.711850] sd 2:0:0:0: [sdb] Attached SCSI disk
[    3.711868] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    3.711902] scsi 2:0:1:0: Direct-Access     ATA      WDC WD10EACS-00D 01.0 PQ: 0 ANSI: 5
[    3.711944] sd 2:0:1:0: [sdc] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    3.711952] sd 2:0:1:0: [sdc] Write Protect is off
[    3.711953] sd 2:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[    3.711967] sd 2:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.711993] sd 2:0:1:0: [sdc] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    3.712004] sd 2:0:1:0: [sdc] Write Protect is off
[    3.712005] sd 2:0:1:0: [sdc] Mode Sense: 00 3a 00 00
[    3.712019] sd 2:0:1:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.712021]  sdc: sdc1
[    3.738109] sd 2:0:1:0: [sdc] Attached SCSI disk
[    3.738127] sd 2:0:1:0: Attached scsi generic sg3 type 0
[    3.738162] scsi 3:0:0:0: Direct-Access     ATA      WDC WD10EACS-00D 01.0 PQ: 0 ANSI: 5
[    3.738206] sd 3:0:0:0: [sdd] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    3.738214] sd 3:0:0:0: [sdd] Write Protect is off
[    3.738215] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    3.738229] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.738255] sd 3:0:0:0: [sdd] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    3.738263] sd 3:0:0:0: [sdd] Write Protect is off
[    3.738264] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    3.738277] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.738279]  sdd: sdd1
[    3.762018] sd 3:0:0:0: [sdd] Attached SCSI disk
[    3.762039] sd 3:0:0:0: Attached scsi generic sg4 type 0
[    3.762049] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.762051] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    3.762073] ata_piix 0000:00:1f.5: setting latency timer to 64
[    3.762097] scsi4 : ata_piix
[    3.762126] scsi5 : ata_piix
[    3.762466] ata5: SATA max UDMA/133 cmd 0xdd00 ctl 0xde00 bmdma 0xe100 irq 19
[    3.762468] ata6: SATA max UDMA/133 cmd 0xdf00 ctl 0xe000 bmdma 0xe108 irq 19
[    4.090530] ata5: SATA link down (SStatus 0 SControl 300)
[    4.418530] ata6: SATA link down (SStatus 0 SControl 300)
[    4.418713] pata_jmicron 0000:03:00.1: enabling device (0000 -> 0001)
[    4.418717] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    4.418735] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    4.418772] scsi6 : pata_jmicron
[    4.418800] scsi7 : pata_jmicron
[    4.419198] ata7: PATA max UDMA/100 cmd 0xa000 ctl 0xa100 bmdma 0xa400 irq 16
[    4.419200] ata8: PATA max UDMA/100 cmd 0xa200 ctl 0xa300 bmdma 0xa408 irq 16
[    4.739468] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.739480] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.739488] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    4.739490] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.739520] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    4.743420] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    4.743428] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xe8405000
[    4.756006] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    4.756059] usb usb1: configuration #1 chosen from 1 choice
[    4.756078] hub 1-0:1.0: USB hub found
[    4.756082] hub 1-0:1.0: 6 ports detected
[    4.756141] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.756146] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.756148] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.756175] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.760086] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.760094] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe8404000
[    4.772007] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.772051] usb usb2: configuration #1 chosen from 1 choice
[    4.772072] hub 2-0:1.0: USB hub found
[    4.772075] hub 2-0:1.0: 6 ports detected
[    4.772126] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.772135] uhci_hcd: USB Universal Host Controller Interface driver
[    4.772149] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.772152] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.772154] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.772177] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.772195] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000d000
[    4.772234] usb usb3: configuration #1 chosen from 1 choice
[    4.772247] hub 3-0:1.0: USB hub found
[    4.772250] hub 3-0:1.0: 2 ports detected
[    4.772297] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.772300] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    4.772302] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.772325] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.772347] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000d100
[    4.772387] usb usb4: configuration #1 chosen from 1 choice
[    4.772399] hub 4-0:1.0: USB hub found
[    4.772402] hub 4-0:1.0: 2 ports detected
[    4.772445] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.772449] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    4.772451] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    4.772473] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    4.772490] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000d200
[    4.772529] usb usb5: configuration #1 chosen from 1 choice
[    4.772541] hub 5-0:1.0: USB hub found
[    4.772544] hub 5-0:1.0: 2 ports detected
[    4.772588] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.772592] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.772593] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.772619] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    4.772636] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d300
[    4.772676] usb usb6: configuration #1 chosen from 1 choice
[    4.772689] hub 6-0:1.0: USB hub found
[    4.772692] hub 6-0:1.0: 2 ports detected
[    4.772736] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.772739] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.772741] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.772763] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    4.772781] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d400
[    4.772824] usb usb7: configuration #1 chosen from 1 choice
[    4.772837] hub 7-0:1.0: USB hub found
[    4.772840] hub 7-0:1.0: 2 ports detected
[    4.772888] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.772891] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.772893] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.772913] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    4.772931] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d500
[    4.772970] usb usb8: configuration #1 chosen from 1 choice
[    4.772982] hub 8-0:1.0: USB hub found
[    4.772985] hub 8-0:1.0: 2 ports detected
[    4.773058] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    4.773334] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.773338] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.784531] mice: PS/2 mouse device common for all mice
[    4.820546] rtc_cmos 00:04: RTC can wake from S4
[    4.820575] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    4.820595] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    4.820626] device-mapper: uevent: version 1.0.3
[    4.820670] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.820709] device-mapper: multipath: version 1.0.5 loaded
[    4.820711] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.820777] cpuidle: using governor ladder
[    4.820808] cpuidle: using governor menu
[    4.821030] TCP cubic registered
[    4.821064] NET: Registered protocol family 10
[    4.821279] lo: Disabled Privacy Extensions
[    4.821426] NET: Registered protocol family 17
[    4.821437] Bluetooth: L2CAP ver 2.11
[    4.821438] Bluetooth: L2CAP socket layer initialized
[    4.821441] Bluetooth: SCO (Voice Link) ver 0.6
[    4.821441] Bluetooth: SCO socket layer initialized
[    4.821461] Bluetooth: RFCOMM socket layer initialized
[    4.821465] Bluetooth: RFCOMM TTY layer initialized
[    4.821466] Bluetooth: RFCOMM ver 1.10
[    4.823030] registered taskstats version 1
[    4.823126]   Magic number: 1:70:544
[    4.823142] scsi_generic sg0: hash matches
[    4.823204] rtc_cmos 00:04: setting system clock to 2009-07-09 18:30:55 UTC (1247164255)
[    4.823206] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.823207] EDD information not available.
[    4.823233] Freeing unused kernel memory: 532k freed
[    4.823324] Write protecting the kernel read-only data: 6684k
[    4.838512] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.896406] md: linear personality registered for level -1
[    4.901489] md: multipath personality registered for level -4
[    4.902458] md: raid0 personality registered for level 0
[    4.904000] md: raid1 personality registered for level 1
[    4.904877] xor: automatically using best checksumming function: generic_sse
[    4.924502]    generic_sse: 12371.000 MB/sec
[    4.924503] xor: using function: generic_sse (12371.000 MB/sec)
[    4.925093] async_tx: api initialized (async)
[    4.992508] raid6: int64x1   2639 MB/s
[    5.060514] raid6: int64x2   3623 MB/s
[    5.128518] raid6: int64x4   2773 MB/s
[    5.196504] raid6: int64x8   2460 MB/s
[    5.264504] raid6: sse2x1    5326 MB/s
[    5.332502] raid6: sse2x2    5816 MB/s
[    5.400506] raid6: sse2x4    9822 MB/s
[    5.400506] raid6: using algorithm sse2x4 (9822 MB/s)
[    5.400508] md: raid6 personality registered for level 6
[    5.400509] md: raid5 personality registered for level 5
[    5.400510] md: raid4 personality registered for level 4
[    5.403862] md: raid10 personality registered for level 10
[    5.429731] Floppy drive(s): fd0 is 1.44M
[    5.451876] FDC 0 is a post-1991 82077
[    5.451963] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.451977] r8169 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.451989] r8169 0000:04:00.0: setting latency timer to 64
[    5.452065] r8169 0000:04:00.0: irq 2298 for MSI/MSI-X
[    5.452407] eth0: RTL8168c/8111c at 0xffffc20000074000, 00:1f:d0:9d:95:d7, XID 3c4000c0 IRQ 2298
[    5.465339] ohci1394 0000:06:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.515029] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[e8304000-e83047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.178835] PM: Starting manual resume from disk
[    6.178837] PM: Resume from partition 8:14
[    6.178838] PM: Checking hibernation image.
[    6.178967] PM: Resume from disk failed.
[    6.203808] kjournald starting.  Commit interval 5 seconds
[    6.203815] EXT3-fs: mounted filesystem with ordered data mode.
[    6.784091] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[007c8bef00001fd0]
[    8.306034] udev: starting version 141
[    8.477926] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    8.498405] [fglrx] Maximum main memory to use for locked dma buffers: 3737 MBytes.
[    8.498471] [fglrx]   vendor: 1002 device: 95c5 count: 1
[    8.498686] [fglrx] ioport: bar 4, base 0x9000, size: 0x100
[    8.498695] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.498698] pci 0000:01:00.0: setting latency timer to 64
[    8.499892] [fglrx] Driver built-in PAT support is enabled successfully
[    8.499917] [fglrx] module loaded - fglrx 8.60.40 [Mar 14 2009] with 1 minors
[    8.810461] md: bind<sdd1>
[    8.827882] md: bind<sdb1>
[    8.829195] md: bind<sdc1>
[    8.865628] parport_pc 00:09: reported by Plug and Play ACPI
[    8.865672] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    8.867214] iTCO_vendor_support: vendor-support=0
[    8.868082] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    8.868186] iTCO_wdt: Found a ICH10R TCO device (Version=2, TCOBASE=0x0460)
[    8.868241] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    8.869677] input: PC Speaker as /devices/platform/pcspkr/input/input4
[    8.875586] raid5: device sdc1 operational as raid disk 1
[    8.875587] raid5: device sdb1 operational as raid disk 0
[    8.875588] raid5: device sdd1 operational as raid disk 2
[    8.875824] raid5: allocated 3234kB for md0
[    8.875826] raid5: raid level 5 set md0 active with 3 out of 3 devices, algorithm 2
[    8.875827] RAID5 conf printout:
[    8.875827]  --- rd:3 wd:3
[    8.875828]  disk 0, o:1, dev:sdb1
[    8.875829]  disk 1, o:1, dev:sdc1
[    8.875830]  disk 2, o:1, dev:sdd1
[    8.877269]  md0: unknown partition table
[    8.960085] tpm_inf_pnp 00:0c: Found TPM with ID IFX0102
[    8.960121] tpm_inf_pnp 00:0c: TPM found: config base 0x4e, data base 0x4700, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[    8.975780] ppdev: user-space parallel port driver
[    8.997341] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    9.034195] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.034239] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.065909] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[    9.098924] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    9.098959] HDA Intel 0000:01:00.1: setting latency timer to 64
[    9.795591] lp0: using parport0 (interrupt-driven).
[    9.870691] it87: Found IT8718F chip at 0x290, revision 5
[    9.870698] it87: in3 is VCC (+5V)
[    9.894016] coretemp coretemp.0: Using relative temperature scale!
[    9.894039] coretemp coretemp.1: Using relative temperature scale!
[    9.958357] Adding 2000052k swap on /dev/sda14.  Priority:-1 extents:1 across:2000052k
[    9.983775] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   10.479221] EXT3 FS on sda13, internal journal
[   13.114912] kjournald starting.  Commit interval 5 seconds
[   13.115121] EXT3 FS on sda1, internal journal
[   13.115125] EXT3-fs: mounted filesystem with ordered data mode.
[   13.172504] kjournald starting.  Commit interval 5 seconds
[   13.172718] EXT3 FS on sda15, internal journal
[   13.172722] EXT3-fs: mounted filesystem with ordered data mode.
[   13.207305] kjournald starting.  Commit interval 5 seconds
[   13.207525] EXT3 FS on sda10, internal journal
[   13.207528] EXT3-fs: mounted filesystem with ordered data mode.
[   13.237347] kjournald starting.  Commit interval 5 seconds
[   13.237542] EXT3 FS on sda12, internal journal
[   13.237546] EXT3-fs: mounted filesystem with ordered data mode.
[   13.255775] kjournald starting.  Commit interval 5 seconds
[   13.255974] EXT3 FS on sda11, internal journal
[   13.255977] EXT3-fs: mounted filesystem with ordered data mode.
[   13.293163] kjournald starting.  Commit interval 5 seconds
[   13.293369] EXT3 FS on sda5, internal journal
[   13.293373] EXT3-fs: mounted filesystem with ordered data mode.
[   13.369395] kjournald starting.  Commit interval 5 seconds
[   13.369613] EXT3 FS on sda6, internal journal
[   13.369617] EXT3-fs: mounted filesystem with ordered data mode.
[   13.399949] kjournald starting.  Commit interval 5 seconds
[   13.400171] EXT3 FS on sda7, internal journal
[   13.400174] EXT3-fs: mounted filesystem with ordered data mode.
[   13.451567] kjournald starting.  Commit interval 5 seconds
[   13.451756] EXT3 FS on sda8, internal journal
[   13.451760] EXT3-fs: mounted filesystem with ordered data mode.
[   13.489631] kjournald starting.  Commit interval 5 seconds
[   13.489851] EXT3 FS on sda9, internal journal
[   13.489854] EXT3-fs: mounted filesystem with ordered data mode.
[   13.507635] kjournald starting.  Commit interval 5 seconds
[   13.524896] EXT3 FS on md0, internal journal
[   13.524901] EXT3-fs: mounted filesystem with ordered data mode.
[   15.163536] type=1505 audit(1247164265.836:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2377
[   15.185786] type=1505 audit(1247164265.860:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2381
[   15.185851] type=1505 audit(1247164265.860:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2381
[   15.185873] type=1505 audit(1247164265.860:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2381
[   15.185893] type=1505 audit(1247164265.860:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2381
[   15.246435] type=1505 audit(1247164265.920:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2386
[   15.246531] type=1505 audit(1247164265.920:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2386
[   15.279034] type=1505 audit(1247164265.952:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2390
[   15.292685] type=1505 audit(1247164265.968:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2394
[   15.798046] r8169: eth0: link up
[   15.798051] r8169: eth0: link up
[   16.370608] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.458112] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   16.458231] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   16.458232] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   16.458233] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.

```

---

### Post by TheBlackSun on 2009-07-14
can anyone help me?

---

### Post by TheBlackSun on 2009-07-15
For those with the same motherboard and the same problem:

The solution is to disable the "Green Lan" feature of the BIOS if you do not have an ethernet cable plugged into a port, then that port will be disabled and linux won't detedt it. Once I disabled the green lan feature it worked right away.

---

