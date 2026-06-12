---
title: "No SMP Support on a AMD Sempron LE-1250"
date: 2009-03-04
forum: Hardware
---

### Post by Lean 946 on 2009-03-04
Hi There:
Here's my problem:
I  Recently bought a new PC, to replace my old one, and I bought it with a Dual Core Processor for Multimedia and Gaming. Here are my specs:
AMD X2 Sempron LE-1250
1GB RAM DDR2
80GB HDD
Pionner DVD-ROM
Gigabyte M61PME-S2 Motherboard with a nForce430 Chipset
nVidia 6100 GPU (onboard)

My problem is: Ubuntu doesn't recognize the Dual Core chip, just one CPU:

lean@Ubuntu:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 127
model name	: AMD Sempron(tm) Processor LE-1250
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up pni cx16 lahf_lm extapic cr8_legacy 3dnowprefetch
bogomips	: 2009.07
clflush size	: 64
power management: ts fid vid ttp tm stc 100mhzsteps

I have investigated and done some work ([http://ubuntuforums.org/showthread.php?t=1084622&highlight=smp](http://ubuntuforums.org/showthread.php?t=1084622&highlight=smp)) but still no progress.

Some more info:
erased some commentaries:
```
lean@Ubuntu:~$ cat /boot/grub/menu.lst

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-13-generic
uuid		c4b399e0-1c14-471f-bd11-d11305fc946f
kernel		/boot/vmlinuz-2.6.27-13-generic root=UUID=c4b399e0-1c14-471f-bd11-d11305fc946f ro crashkernel=384M-2G:64M@16M,2G-:128M@16M vga=791
initrd		/boot/initrd.img-2.6.27-13-generic

title		Ubuntu 8.10, kernel 2.6.27-13-generic (recovery mode)
uuid		c4b399e0-1c14-471f-bd11-d11305fc946f
kernel		/boot/vmlinuz-2.6.27-13-generic root=UUID=c4b399e0-1c14-471f-bd11-d11305fc946f ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd		/boot/initrd.img-2.6.27-13-generic

title		Ubuntu 8.10, kernel 2.6.27-12-generic
uuid		c4b399e0-1c14-471f-bd11-d11305fc946f
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=c4b399e0-1c14-471f-bd11-d11305fc946f ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.27-12-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-12-generic (recovery mode)
uuid		c4b399e0-1c14-471f-bd11-d11305fc946f
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=c4b399e0-1c14-471f-bd11-d11305fc946f ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd		/boot/initrd.img-2.6.27-12-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c4b399e0-1c14-471f-bd11-d11305fc946f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c4b399e0-1c14-471f-bd11-d11305fc946f ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c4b399e0-1c14-471f-bd11-d11305fc946f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c4b399e0-1c14-471f-bd11-d11305fc946f ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c4b399e0-1c14-471f-bd11-d11305fc946f
kernel		/boot/memtest86+.bin
quiet

title		Ubuntu 8.10, kernel 2.6.27-13-generic normal
uuid		c4b399e0-1c14-471f-bd11-d11305fc946f
kernel		/boot/vmlinuz-2.6.27-13-generic root=UUID=c4b399e0-1c14-471f-bd11-d11305fc946f ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.27-13-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-13-generic splashy
uuid		c4b399e0-1c14-471f-bd11-d11305fc946f
kernel		/boot/vmlinuz-2.6.27-13-generic root=UUID=c4b399e0-1c14-471f-bd11-d11305fc946f ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M vga=791 splashy
initrd		/boot/initrd.img-2.6.27-13-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-13-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) ) #1 SMP Thu Feb 26 07:26:43 UTC 2009 (Ubuntu 2.6.27-13.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bff0000 (usable)
[    0.000000]  BIOS-e820: 000000003bff0000 - 000000003bff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bff3000 - 000000003c000000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003c000000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x3bff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 37556000 - 37fefb50
[    0.000000] ACPI: RSDP 000F6250, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 3BFF3000, 0038 (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] ACPI: FACP 3BFF3040, 0074 (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] ACPI: DSDT 3BFF30C0, 43ED (r1 GBT    NVDAACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 3BFF0000, 0040
[    0.000000] ACPI: SSDT 3BFF7580, 0115 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: HPET 3BFF76C0, 0038 (r1 GBT    NVDAACPI 42302E31 NVDA       98)
[    0.000000] ACPI: MCFG 3BFF7700, 003C (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] ACPI: APIC 3BFF74C0, 0098 (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] 63MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c39e0]    TEXT DATA BSS ==> [0000100000 - 00005c39e0]
[    0.000000]   #4 [0037556000 - 0037fefb50]          RAMDISK ==> [0037556000 - 0037fefb50]
[    0.000000]   #5 [00005c4000 - 00005c7000]    INIT_PG_TABLE ==> [00005c4000 - 00005c7000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f4880] 000f4880
[    0.000000] Reserving 64MB of memory at 16MB for crashkernel (System RAM: 959MB)
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0003bff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003bff0
[    0.000000] On node 0 totalpages: 245647
[    0.000000] free_area_init_node: node 0, pgdat c048c700, node_mem_map c5000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 16224 pages, LIFO batch:3
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243487
[    0.000000] Kernel command line: root=UUID=c4b399e0-1c14-471f-bd11-d11305fc946f ro crashkernel=384M-2G:64M@16M,2G-:128M@16M vga=791
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2209.985 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour dummy device 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 891328k/982976k available (2577k kernel code, 90936k reserved, 1163k data, 428k init, 65472k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0518000   ( 428 kB)
[    0.004000]       .data : 0xc038478a - 0xc04a7680   (1163 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038478a   (2577 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4419.97 BogoMIPS (lpj=8839940)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] using C1E aware idle routine
[    0.004000] Checking 'hlt' instruction... OK.
[    0.016371] SMP alternatives: switching to UP code
[    0.021335] ACPI: Core revision 20080609
[    0.022749] ACPI: Checking initramfs for custom DSDT
[    0.387579] ENABLING IO-APIC IRQs
[    0.387785] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.427481] CPU0: AMD Sempron(tm) Processor LE-1250 stepping 02
[    0.428026] Brought up 1 CPUs
[    0.428026] Total of 1 processors activated (4419.97 BogoMIPS).
[    0.428026] CPU0 attaching NULL sched-domain.
[    0.428026] net_namespace: 840 bytes
[    0.428026] Booting paravirtualized kernel on bare hardware
[    0.428026] Time: 15:34:52  Date: 03/04/09
[    0.428026] NET: Registered protocol family 16
[    0.428026] EISA bus registered
[    0.428026] ACPI: bus type pci registered
[    0.428026] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
[    0.428026] PCI: MCFG area at f0000000 reserved in E820
[    0.428026] PCI: Using MMCONFIG for extended config space
[    0.428026] PCI: Using configuration type 1 for base access
[    0.428026] ACPI: EC: Look up EC in DSDT
[    0.432447] ACPI: Interpreter enabled
[    0.432457] ACPI: (supports S0 S1 S4 S5)
[    0.432472] ACPI: Using IOAPIC for interrupt routing
[    0.442209] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.442443] PCI: 0000:00:01.1 reg 10 io port: [c000, c03f]
[    0.442453] PCI: 0000:00:01.1 reg 20 io port: [1c00, 1c3f]
[    0.442457] PCI: 0000:00:01.1 reg 24 io port: [c800, c83f]
[    0.442480] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.442489] pci 0000:00:01.1: PME# disabled
[    0.442530] PCI: 0000:00:02.0 reg 10 32bit mmio: [fb005000, fb005fff]
[    0.442554] pci 0000:00:02.0: supports D1
[    0.442556] pci 0000:00:02.0: supports D2
[    0.442558] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.442563] pci 0000:00:02.0: PME# disabled
[    0.442583] PCI: 0000:00:02.1 reg 10 32bit mmio: [fb004000, fb0040ff]
[    0.442613] pci 0000:00:02.1: supports D1
[    0.442614] pci 0000:00:02.1: supports D2
[    0.442616] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.442622] pci 0000:00:02.1: PME# disabled
[    0.442676] PCI: 0000:00:05.0 reg 10 32bit mmio: [fb000000, fb003fff]
[    0.442706] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.442712] pci 0000:00:05.0: PME# disabled
[    0.442740] PCI: 0000:00:06.0 reg 20 io port: [f000, f00f]
[    0.442774] PCI: 0000:00:07.0 reg 10 32bit mmio: [fb006000, fb006fff]
[    0.442778] PCI: 0000:00:07.0 reg 14 io port: [cc00, cc07]
[    0.442804] pci 0000:00:07.0: supports D1
[    0.442805] pci 0000:00:07.0: supports D2
[    0.442807] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.442814] pci 0000:00:07.0: PME# disabled
[    0.442831] PCI: 0000:00:08.0 reg 10 io port: [9f0, 9f7]
[    0.442834] PCI: 0000:00:08.0 reg 14 io port: [bf0, bf3]
[    0.442838] PCI: 0000:00:08.0 reg 18 io port: [970, 977]
[    0.442841] PCI: 0000:00:08.0 reg 1c io port: [b70, b73]
[    0.442845] PCI: 0000:00:08.0 reg 20 io port: [e000, e00f]
[    0.442848] PCI: 0000:00:08.0 reg 24 32bit mmio: [fb007000, fb007fff]
[    0.442883] PCI: 0000:00:0d.0 reg 10 32bit mmio: [f8000000, f8ffffff]
[    0.442888] PCI: 0000:00:0d.0 reg 14 64bit mmio: [e0000000, efffffff]
[    0.442893] PCI: 0000:00:0d.0 reg 1c 64bit mmio: [f9000000, f9ffffff]
[    0.442897] PCI: 0000:00:0d.0 reg 30 32bit mmio: [0, 1ffff]
[    0.442996] pci 0000:00:04.0: transparent bridge
[    0.443002] PCI: bridge 0000:00:04.0 io port: [b000, bfff]
[    0.443009] bus 00 -> node 0
[    0.443015] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.443331] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.475609] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.475775] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.475939] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.476109] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.476273] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.476437] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.476600] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.476763] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.476929] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
[    0.477091] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.477260] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[    0.477429] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[    0.477592] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.477755] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.477920] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[    0.478084] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[    0.478248] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.478413] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.478578] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.478789] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.478993] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.479194] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.479397] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.479599] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.479801] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.480004] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.480214] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.480415] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
[    0.480616] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.480818] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.481019] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.481221] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.481422] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.481623] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.481824] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.482027] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.482230] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.482431] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.482603] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.482635] pnp: PnP ACPI init
[    0.482644] ACPI: bus type pnp registered
[    0.487067] pnp: PnP ACPI: found 13 devices
[    0.487072] ACPI: ACPI bus type pnp unregistered
[    0.487078] PnPBIOS: Disabled by ACPI PNP
[    0.487387] PCI: Using ACPI for IRQ routing
[    0.487482] NET: Registered protocol family 8
[    0.487482] NET: Registered protocol family 20
[    0.487482] NetLabel: Initializing
[    0.487482] NetLabel:  domain hash size = 128
[    0.487482] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.487482] NetLabel:  unlabeled traffic allowed by default
[    0.487482] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.487482] hpet0: 3 32-bit timers, 25000000 Hz
[    0.489040] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.489046]    actual entries 65620
[    0.489185] AppArmor: AppArmor Filesystem Enabled
[    0.489214] ACPI: RTC can wake from S4
[    0.489223] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.489223] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.489223] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.489223] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.489223] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.489223] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.489223] system 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
[    0.489223] system 00:01: iomem range 0xfefe1000-0xfefe10ff could not be reserved
[    0.489223] system 00:01: iomem range 0x3c000000-0x3fffffff could not be reserved
[    0.489223] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.489223] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.489223] system 00:02: ioport range 0x295-0x314 has been reserved
[    0.489223] system 00:02: ioport range 0x290-0x294 has been reserved
[    0.489223] system 00:0b: iomem range 0xf0000000-0xf7ffffff could not be reserved
[    0.489223] system 00:0c: iomem range 0xf0000-0xf3fff could not be reserved
[    0.489223] system 00:0c: iomem range 0xf4000-0xf7fff could not be reserved
[    0.489223] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.489223] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.489223] system 00:0c: iomem range 0x3bff0000-0x3bffffff could not be reserved
[    0.489223] system 00:0c: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.489223] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.489223] system 00:0c: iomem range 0x100000-0x3bfeffff could not be reserved
[    0.489223] system 00:0c: iomem range 0x3c000000-0x3fffffff could not be reserved
[    0.489223] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.489223] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.492045] Switched to high resolution mode on CPU 0
[    0.524998] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[    0.525005] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
[    0.525011] pci 0000:00:04.0:   MEM window: disabled
[    0.525016] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.525028] pci 0000:00:04.0: setting latency timer to 64
[    0.525031] bus: 00 index 0 io port: [0, ffff]
[    0.525035] bus: 00 index 1 mmio: [0, ffffffff]
[    0.525039] bus: 01 index 0 io port: [b000, bfff]
[    0.525043] bus: 01 index 1 mmio: [0, 0]
[    0.525046] bus: 01 index 2 mmio: [0, 0]
[    0.525050] bus: 01 index 3 io port: [0, ffff]
[    0.525054] bus: 01 index 4 mmio: [0, ffffffff]
[    0.525067] NET: Registered protocol family 2
[    0.525222] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.525516] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.526306] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.526750] TCP: Hash tables configured (established 131072 bind 65536)
[    0.526757] TCP reno registered
[    0.526886] NET: Registered protocol family 1
[    0.527002] checking if image is initramfs... it is
[    1.281213] Freeing initrd memory: 10854k freed
[    1.281870] audit: initializing netlink socket (disabled)
[    1.281888] type=2000 audit(1236180892.280:1): initialized
[    1.287297] highmem bounce pool size: 64 pages
[    1.287307] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.289242] VFS: Disk quotas dquot_6.5.1
[    1.289317] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.289412] msgmni has been set to 1634
[    1.289531] io scheduler noop registered
[    1.289536] io scheduler anticipatory registered
[    1.289540] io scheduler deadline registered
[    1.289553] io scheduler cfq registered (default)
[    1.289589] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.316044] pci 0000:00:04.0: Enabling HT MSI Mapping
[    1.316064] pci 0000:00:05.0: Enabling HT MSI Mapping
[    1.316092] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.316108] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.316124] pci 0000:00:0d.0: Boot video device
[    1.316377] isapnp: Scanning for PnP cards...
[    1.669030] isapnp: No Plug & Play device found
[    1.702520] hpet_resources: 0xfeff0000 is busy
[    1.702595] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.702722] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.703356] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.704910] brd: module loaded
[    1.704982] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.705091] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.705096] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.705229] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.705634] mice: PS/2 mouse device common for all mice
[    1.705765] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.705798] rtc0: alarms up to one year, y3k, hpet irqs
[    1.705906] EISA: Probing bus 0 at eisa.0
[    1.705914] Cannot allocate resource for EISA slot 1
[    1.705934] EISA: Detected 0 cards.
[    1.705938] cpuidle: using governor ladder
[    1.705942] cpuidle: using governor menu
[    1.706383] TCP cubic registered
[    1.706412] Using IPI No-Shortcut mode
[    1.706584] registered taskstats version 1
[    1.706688]   Magic number: 1:899:587
[    1.706769] tty ptyc5: hash matches
[    1.706897] rtc_cmos 00:05: setting system clock to 2009-03-04 15:34:53 UTC (1236180893)
[    1.706904] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.706909] EDD information not available.
[    1.707191] Freeing unused kernel memory: 428k freed
[    1.707248] Write protecting the kernel text: 2580k
[    1.707284] Write protecting the kernel read-only data: 940k
[    1.735668] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.769664] vesafb: framebuffer at 0xe0000000, mapped to 0xf8880000, using 3072k, total 65536k
[    1.769677] vesafb: mode is 1024x768x16, linelength=2048, pages=1
[    1.769682] vesafb: protected mode interface info at c000:d180
[    1.769687] vesafb: pmi: set display start = c00cd1b6, set palette = c00cd220
[    1.769691] vesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
[    1.769709] vesafb: scrolling: redraw
[    1.769713] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[    1.769915] Console: switching to colour frame buffer device 128x48
[    1.778358] fb0: VESA VGA frame buffer device
[    1.859815] fuse init (API version 7.9)
[    1.878272] processor ACPI0007:00: registered as cooling_device0
[    1.896634] device-mapper: uevent: version 1.0.3
[    1.896912] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.653874] usbcore: registered new interface driver usbfs
[    2.653990] usbcore: registered new interface driver hub
[    2.668196] No dock devices found.
[    2.696062] usbcore: registered new device driver usb
[    2.723698] SCSI subsystem initialized
[    2.723850] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    2.724376] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    2.724476] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    2.724614] forcedeth 0000:00:07.0: setting latency timer to 64
[    2.729348] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.784134] libata version 3.00 loaded.
[    3.244714] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:d0:b3:26:b7
[    3.244859] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[    3.248784] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[    3.252331] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 22 (level, low) -> IRQ 22
[    3.255957] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    3.255960] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    3.259623] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    3.263320] ohci_hcd 0000:00:02.0: irq 22, io mem 0xfb005000
[    3.322151] usb usb1: configuration #1 chosen from 1 choice
[    3.325964] hub 1-0:1.0: USB hub found
[    3.329542] hub 1-0:1.0: 10 ports detected
[    3.541088] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    3.544690] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    3.548349] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    3.548352] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    3.552017] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    3.555680] ehci_hcd 0000:00:02.1: debug port 1
[    3.559265] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    3.559279] ehci_hcd 0000:00:02.1: irq 21, io mem 0xfb004000
[    3.572011] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.575642] usb usb2: configuration #1 chosen from 1 choice
[    3.579162] hub 2-0:1.0: USB hub found
[    3.582807] hub 2-0:1.0: 10 ports detected
[    3.795931] pata_amd 0000:00:06.0: version 0.3.10
[    3.795979] pata_amd 0000:00:06.0: setting latency timer to 64
[    3.800028] scsi0 : pata_amd
[    3.804914] scsi1 : pata_amd
[    3.808945] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    3.812314] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    3.984016] usb 2-6: new high speed USB device using ehci_hcd and address 3
[    4.119636] usb 2-6: configuration #1 chosen from 1 choice
[    4.256328] ata1.00: ATAPI: Pioneer DVD-ROM ATAPIModel DVD-115  0122, E1.22, max UDMA/33
[    4.259751] ata1: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:600:0x13)
[    4.272266] ata1.00: configured for UDMA/33
[    4.275656] ata2: port disabled. ignoring.
[    4.276932] scsi 0:0:0:0: CD-ROM            PIONEER  DVD-ROM DVD-115  1.22 PQ: 0 ANSI: 5
[    4.280513] sata_nv 0000:00:08.0: version 3.5
[    4.280884] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[    4.284354] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
[    4.287893] sata_nv 0000:00:08.0: setting latency timer to 64
[    4.291445] scsi2 : sata_nv
[    4.295941] scsi3 : sata_nv
[    4.299491] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 20
[    4.302916] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 20
[    4.416019] usb 1-4: new low speed USB device using ohci_hcd and address 2
[    4.630858] usb 1-4: configuration #1 chosen from 1 choice
[    4.644071] usbcore: registered new interface driver libusual
[    4.657598] Initializing USB Mass Storage driver...
[    4.668542] scsi4 : SCSI emulation for USB Mass Storage devices
[    4.673285] usbcore: registered new interface driver usb-storage
[    4.676886] usbcore: registered new interface driver hiddev
[    4.680403] USB Mass Storage support registered.
[    4.684015] usb-storage: device found at 3
[    4.684017] usb-storage: waiting for device to settle before scanning
[    4.687319] input: USB Mouse as /devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4:1.0/input/input2
[    4.695706] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    4.700182] input,hidraw0: USB HID v1.10 Mouse [USB Mouse] on usb-0000:00:02.0-4
[    4.703824] usbcore: registered new interface driver usbhid
[    4.707405] usbhid: v2.6:USB HID core driver
[    4.772039] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.788107] ata3.00: HPA unlocked: 156299375 -> 156301488, native 156301488
[    4.791680] ata3.00: ATA-7: WDC WD800JD-22MSA1, 10.01E01, max UDMA/133
[    4.795224] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.804218] ata3.00: configured for UDMA/133
[    5.116104] scsi 2:0:0:0: Direct-Access     ATA      WDC WD800JD-22MS 10.0 PQ: 0 ANSI: 5
[    5.119881] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    5.153068] Driver 'sr' needs updating - please use bus_type methods
[    5.162264] sr0: scsi3-mmc drive: 16x/40x cd/rw xa/form2 cdda tray
[    5.165951] Uniform CD-ROM driver Revision: 3.20
[    5.169678] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.188132] Driver 'sd' needs updating - please use bus_type methods
[    5.191860] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    5.195540] sd 2:0:0:0: [sda] Write Protect is off
[    5.199175] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.202327] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.206124] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    5.210492] sd 2:0:0:0: [sda] Write Protect is off
[    5.214230] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.214275] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.218037]  sda: sda1 sda2 sda3
[    5.252723] sd 2:0:0:0: [sda] Attached SCSI disk
[    5.459314] PM: Starting manual resume from disk
[    5.463182] PM: Resume from partition 8:3
[    5.463184] PM: Checking hibernation image.
[    5.463311] PM: Resume from disk failed.
[    5.531491] kjournald starting.  Commit interval 5 seconds
[    5.535295] EXT3-fs: mounted filesystem with ordered data mode.
[    9.684240] usb-storage: device scan complete
[    9.684604] scsi 4:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[    9.689212] sd 4:0:0:0: [sdb] 984576 512-byte hardware sectors (504 MB)
[    9.693585] sd 4:0:0:0: [sdb] Write Protect is off
[    9.697417] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    9.697419] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    9.702960] sd 4:0:0:0: [sdb] 984576 512-byte hardware sectors (504 MB)
[    9.707335] sd 4:0:0:0: [sdb] Write Protect is off
[    9.711221] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    9.711223] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    9.715074]  sdb: sdb1 sdb3
[    9.719711] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    9.723547] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   12.172636] udevd version 124 started
[   13.044731] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   13.048370] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xc800
[   13.084122] Linux agpgart interface v0.103
[   13.303329] nvidia: module license 'NVIDIA' taints kernel.
[   13.762623] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   13.831442] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   13.844205] ACPI: Power Button (FF) [PWRF]
[   13.847927] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   13.864019] ACPI: Power Button (CM) [PWRB]
[   14.720570] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   14.724281] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[   14.728080] HDA Intel 0000:00:05.0: setting latency timer to 64
[   14.762854] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   15.722795] parport_pc 00:09: reported by Plug and Play ACPI
[   15.726596] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   15.743519] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 22
[   15.747311] nvidia 0000:00:0d.0: PCI INT A -> Link[AIGP] -> GSI 22 (level, low) -> IRQ 22
[   15.751167] nvidia 0000:00:0d.0: setting latency timer to 64
[   15.784085] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.82  Tue Nov  4 13:35:57 PST 2008
[   16.274550] device-mapper: multipath: version 1.0.5 loaded
[   19.013558] lp0: using parport0 (interrupt-driven).
[   19.036806] it87: Found IT8716F chip at 0x290, revision 3
[   19.040755] it87: in3 is VCC (+5V)
[   19.044648] it87: in7 is VCCH (+5V Stand-By)
[   19.198055] Adding 3686908k swap on /dev/sda3.  Priority:-1 extents:1 across:3686908k
[   19.499405] EXT3 FS on sda1, internal journal
[   20.169318] kjournald starting.  Commit interval 5 seconds
[   20.169501] EXT3 FS on sda2, internal journal
[   20.169505] EXT3-fs: mounted filesystem with ordered data mode.
[   20.432046] type=1505 audit(1236180912.514:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3809
[   20.632377] type=1505 audit(1236180912.714:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3814
[   20.632609] type=1505 audit(1236180912.714:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3814
[   20.805047] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.840908] nf_conntrack version 0.5.0 (15360 buckets, 61440 max)
[   20.841056] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   20.841059] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   20.841061] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   20.994980] NET: Registered protocol family 10
[   20.995487] lo: Disabled Privacy Extensions
[   21.011392] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   23.446375] ACPI: WMI: Mapper loaded
[   23.817062] powernow-k8: Found 1 AMD Sempron(tm) Processor LE-1250 processors (1 cpu cores) (version 2.20.00)
[   23.817100] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xc
[   23.817103] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xe
[   23.817105] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x10
[   23.817107] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   24.431975] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   24.520126] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   24.520131] apm: overridden by ACPI.
[   24.850542] ppdev: user-space parallel port driver
[   30.000040] Clocksource tsc unstable (delta = -272724884 ns)
[   31.994086] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   31.994097] vboxdrv: Successfully done.
[   31.994102] vboxdrv: Found 1 processor cores.
[   31.996984] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   31.996992] vboxdrv: Successfully loaded version 2.1.4 (interface 0x000a0009).
[   38.983584] NET: Registered protocol family 17

```
Thanks for the replies.

---

### Post by neppakyo on 2009-03-04
"The LE-1250 is a single-core processor. The only dual-core Semprons are the Sempron X2 2100, 2200, and 2300"

From AMD's forum on specs

I dont think the LE-1250 model is a dual core one..

---

### Post by Lean 946 on 2009-03-04
First, thank you for your quick reply.
And, you're right. I just checked at AMD Forums.
I'll call the computer store where i bought it, see if I can get a dual-cored one.
Thank You

---

### Post by neppakyo on 2009-03-04
> **Lean 946 said:**
> First, thank you for your quick reply.
And, you're right. I just checked at AMD Forums.
I'll call the computer store where i bought it, see if I can get a dual-cored one.
Thank You

You're welcome! that was the easiest problem to figure out ;)

If I were you, and if you mobo supports it, get a phenom quad core (older ones are cheap now) or a X2 dual core.

---

### Post by questioning on 2009-03-04
> **neppakyo said:**
> 
If I were you, and if you mobo supports it, get a phenom quad core (older ones are cheap now) or a X2 dual core.


sorry but are you retarded?

its obvious that the threadstarter wants something cheap and he doesnt need a quadcore for sure. i even doubt that you need a quadcore.

---

### Post by neppakyo on 2009-03-04
> **questioning said:**
> sorry but are you retarded?

its obvious that the threadstarter wants something cheap and he doesnt need a quadcore for sure. i even doubt that you need a quadcore.

:p older phenoms(1st gen) ive seen going for around $60, which is cheap and why i mentioned it.

Now, don't be an arseface and go with the name calling :p

---

### Post by questioning on 2009-03-04
> **neppakyo said:**
> :p older phenoms(1st gen) ive seen going for around $60, which is cheap and why i mentioned it.

Now, don't be an arseface and go with the name calling :p



:p

---

