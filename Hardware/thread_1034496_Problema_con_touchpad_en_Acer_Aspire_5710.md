---
title: "Problema con touchpad en Acer Aspire 5710"
date: 2009-01-08
forum: Hardware
---

### Post by emiliano_raso on 2009-01-08
Tengo una notebook Acer Aspire 5710-4900.
Cuando apenas enciendo la maquina, si uso el touchpad anda solo. Es decir, lo tocas y se va hacia cualquier lado, hace clicks, abre cosas. Un desastre...

- No es suciedad. Lo limpié y sigue pasando.
- No esta roto. En Window$ Vi$ta anda bien.

Pasa solamente cuando se enciende la maquina durante 1 hora aproximadamente. Despues lo deja de hacer y funciona bien.
Me pasó siempre en la notebook con Ubuntu. La primer version que instale fue 7.04 y siguió sucediendo con las siguientes hasta incluso ahora que tengo 8.10

En un foro encontre que una solucion que a mi no me funcionó, y es agregar al xorg.conf esto:
Section "InputDevice"
 Identifier "Mouse0"
 Driver "mouse"
 Option "Device" "/dev/input/mice"
 Option "Protocol" "ImPS/2"
 Option "ZAxisMapping" "4 5"
 Option "Emulate3Buttons" "true"
EndSection


Desde ya les agradezco la ayuda...

---

### Post by Hei Ku on 2009-01-08
cuando te pase, en una terminal pone el comando dmesg y postea el resultado acá.

PD: Movido a Hardware.

---

### Post by emiliano_raso on 2009-01-08
Gracias por responder.

Al tirar ese comando me dice lo siguiente:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Fri Dec 19 16:29:52 UTC 2008 (Ubuntu 2.6.27-11.22-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f680000 (usable)
[    0.000000]  BIOS-e820: 000000003f680000 - 000000003f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x3f680 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 37820000 - 37fefe4e
[    0.000000] ACPI: RSDP 000F6CB0, 0024 (r2 ACRSYS)
[    0.000000] ACPI: XSDT 3F6859C1, 0084 (r1 ACRSYS ACRPRDCT  6040000  LTP        0)
[    0.000000] ACPI: APIC 3F68CBF6, 0068 (r1 Acer   Acadia    6040000 LOHR       5A)
[    0.000000] ACPI: HPET 3F68CC5E, 0038 (r1 Acer   Acadia    6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 3F68CC96, 003C (r1 Acer   Acadia    6040000 LOHR       5A)
[    0.000000] ACPI: SLIC 3F68CCD2, 0176 (r1 ACRSYS ACRPRDCT  6040000 LOHR        0)
[    0.000000] ACPI: DBGP 3F68CE48, 0034 (r1 Acer   Acadia    6040000 LOHR        0)
[    0.000000] ACPI: FACP 3F68CE7C, 00F4 (r3 Acer   Acadia    6040000 LOHR        1)
[    0.000000] ACPI: DSDT 3F686CA9, 5ED9 (r1 Acer   CALISTGA  6040000 INTL 20060608)
[    0.000000] ACPI: FACS 3F68DFC0, 0040
[    0.000000] ACPI: APIC 3F68CF70, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 3F68CFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 3F686A9F, 020A (r1 SataRe SataAhci     1000 INTL 20050228)
[    0.000000] ACPI: SSDT 3F685FB7, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 3F685F11, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 3F685A45, 04CC (r1  PmRef    CpuPm     3000 INTL 20050228)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: DMI detected: Acer
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [0037820000 - 0037fefe4e]          RAMDISK ==> [0037820000 - 0037fefe4e]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f6d60] 000f6d60
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0003f680
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f680
[    0.000000] On node 0 totalpages: 259615
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 30069 pages, LIFO batch:7
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257332
[    0.000000] Kernel command line: root=UUID=4e07ffe6-a1fc-417a-9481-e0f6a358af53 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1994.988 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1015200k/1038848k available (2576k kernel code, 22960k reserved, 1165k data, 424k init, 121344k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.97 BogoMIPS (lpj=7979952)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018289] ACPI: Core revision 20080609
[    0.020665] ACPI: Checking initramfs for custom DSDT
[    0.372277] ENABLING IO-APIC IRQs
[    0.372477] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.414038] CPU0: Intel(R) Core(TM) Duo CPU      T2450  @ 2.00GHz stepping 0c
[    0.416026] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3990.00 BogoMIPS (lpj=7980002)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.500537] CPU1: Intel(R) Core(TM) Duo CPU      T2450  @ 2.00GHz stepping 0c
[    0.500559] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.504056] Brought up 2 CPUs
[    0.504059] Total of 2 processors activated (7979.97 BogoMIPS).
[    0.504085] CPU0 attaching sched-domain:
[    0.504088]  domain 0: span 0-1 level MC
[    0.504091]   groups: 0 1
[    0.504098] CPU1 attaching sched-domain:
[    0.504100]  domain 0: span 0-1 level MC
[    0.504102]   groups: 1 0
[    0.504194] net_namespace: 840 bytes
[    0.504194] Booting paravirtualized kernel on bare hardware
[    0.504314] Time:  1:18:43  Date: 01/09/09
[    0.504345] NET: Registered protocol family 16
[    0.504368] EISA bus registered
[    0.504368] ACPI: bus type pci registered
[    0.504368] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.504368] PCI: MCFG area at e0000000 reserved in E820
[    0.504368] PCI: Using MMCONFIG for extended config space
[    0.504368] PCI: Using configuration type 1 for base access
[    0.508187] ACPI: EC: Look up EC in DSDT
[    0.512664] ACPI: BIOS _OSI(Linux) query ignored via DMI
[    0.513476] ACPI: Interpreter enabled
[    0.513481] ACPI: (supports S0 S3 S4 S5)
[    0.513497] ACPI: Using IOAPIC for interrupt routing
[    0.516970] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.584366] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.584366] ACPI: EC: driver started in interrupt mode
[    0.584366] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.584366] PCI: 0000:00:02.0 reg 10 32bit mmio: [d0300000, d037ffff]
[    0.584366] PCI: 0000:00:02.0 reg 14 io port: [5088, 508f]
[    0.584366] PCI: 0000:00:02.0 reg 18 32bit mmio: [c0000000, cfffffff]
[    0.584366] PCI: 0000:00:02.0 reg 1c 32bit mmio: [d0400000, d043ffff]
[    0.584366] PCI: 0000:00:02.1 reg 10 32bit mmio: [d0380000, d03fffff]
[    0.584366] PCI: 0000:00:1b.0 reg 10 64bit mmio: [d0440000, d0443fff]
[    0.584366] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.584366] pci 0000:00:1b.0: PME# disabled
[    0.584402] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.584408] pci 0000:00:1c.0: PME# disabled
[    0.584479] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.584485] pci 0000:00:1c.2: PME# disabled
[    0.584555] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.584560] pci 0000:00:1c.3: PME# disabled
[    0.584611] PCI: 0000:00:1d.0 reg 20 io port: [50a0, 50bf]
[    0.584674] PCI: 0000:00:1d.1 reg 20 io port: [50c0, 50df]
[    0.584738] PCI: 0000:00:1d.2 reg 20 io port: [50e0, 50ff]
[    0.584801] PCI: 0000:00:1d.3 reg 20 io port: [5400, 541f]
[    0.584868] PCI: 0000:00:1d.7 reg 10 32bit mmio: [d0644000, d06443ff]
[    0.584925] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.584931] pci 0000:00:1d.7: PME# disabled
[    0.585090] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.585095] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.585124] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.585133] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.585141] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.585149] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.585157] PCI: 0000:00:1f.1 reg 20 io port: [5090, 509f]
[    0.585221] PCI: 0000:00:1f.2 reg 10 io port: [5478, 547f]
[    0.585229] PCI: 0000:00:1f.2 reg 14 io port: [5470, 5473]
[    0.585238] PCI: 0000:00:1f.2 reg 18 io port: [5468, 546f]
[    0.585246] PCI: 0000:00:1f.2 reg 1c io port: [545c, 545f]
[    0.585254] PCI: 0000:00:1f.2 reg 20 io port: [5440, 544f]
[    0.585262] PCI: 0000:00:1f.2 reg 24 32bit mmio: [d0644400, d06447ff]
[    0.585292] pci 0000:00:1f.2: PME# supported from D3hot
[    0.585298] pci 0000:00:1f.2: PME# disabled
[    0.585355] PCI: 0000:00:1f.3 reg 20 io port: [5420, 543f]
[    0.585445] PCI: bridge 0000:00:1c.0 io port: [0, fff]
[    0.585450] PCI: bridge 0000:00:1c.0 32bit mmio: [0, fffff]
[    0.585549] PCI: 0000:04:00.0 reg 10 64bit mmio: [d0000000, d000ffff]
[    0.585619] pci 0000:04:00.0: PME# supported from D3hot D3cold
[    0.585626] pci 0000:04:00.0: PME# disabled
[    0.585680] PCI: bridge 0000:00:1c.2 32bit mmio: [d0000000, d00fffff]
[    0.585832] PCI: 0000:05:00.0 reg 10 32bit mmio: [d0100000, d0100fff]
[    0.588154] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
[    0.588167] pci 0000:05:00.0: PME# disabled
[    0.588221] PCI: bridge 0000:00:1c.3 32bit mmio: [d0100000, d01fffff]
[    0.588275] PCI: 0000:06:00.0 reg 10 32bit mmio: [d0200000, d020007f]
[    0.588339] pci 0000:06:00.0: supports D1
[    0.588341] pci 0000:06:00.0: supports D2
[    0.588343] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot
[    0.588349] pci 0000:06:00.0: PME# disabled
[    0.588390] PCI: 0000:06:00.1 reg 10 32bit mmio: [d0200400, d02004ff]
[    0.588454] pci 0000:06:00.1: supports D1
[    0.588456] pci 0000:06:00.1: supports D2
[    0.588458] pci 0000:06:00.1: PME# supported from D0 D1 D2 D3hot
[    0.588464] pci 0000:06:00.1: PME# disabled
[    0.588504] PCI: 0000:06:00.2 reg 10 32bit mmio: [d0200800, d020087f]
[    0.588568] pci 0000:06:00.2: supports D1
[    0.588570] pci 0000:06:00.2: supports D2
[    0.588572] pci 0000:06:00.2: PME# supported from D0 D1 D2 D3hot
[    0.588578] pci 0000:06:00.2: PME# disabled
[    0.588619] PCI: 0000:06:00.3 reg 10 32bit mmio: [0, ff]
[    0.588684] pci 0000:06:00.3: supports D1
[    0.588686] pci 0000:06:00.3: supports D2
[    0.588688] pci 0000:06:00.3: PME# supported from D0 D1 D2 D3hot
[    0.588694] pci 0000:06:00.3: PME# disabled
[    0.588759] pci 0000:00:1e.0: transparent bridge
[    0.588768] PCI: bridge 0000:00:1e.0 32bit mmio: [d0200000, d02fffff]
[    0.588803] bus 00 -> node 0
[    0.588811] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.589235] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.589409] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.589585] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.589769] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.592196] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 5 *6 10 12 14 15)
[    0.592298] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 5 6 *11 12 14 15)
[    0.592435] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 5 6 10 12 14 15) *11
[    0.592572] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 5 6 11 12 14 15) *10
[    0.592708] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 5 6 *10 12 14 15)
[    0.592845] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 5 6 11 12 14 15) *0, disabled.
[    0.592982] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 5 6 *10 12 14 15)
[    0.593119] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 *5 6 11 12 14 15)
[    0.593199] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.593199] pnp: PnP ACPI init
[    0.593199] ACPI: bus type pnp registered
[    0.632263] pnp 00:06: io resource (0x2e-0x2f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.632263] pnp 00:06: io resource (0x4e-0x4f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.632263] pnp 00:06: io resource (0x61-0x61) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.632263] pnp 00:06: io resource (0x63-0x63) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.632263] pnp 00:06: io resource (0x65-0x65) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.632263] pnp 00:06: io resource (0x67-0x67) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.632263] pnp 00:06: io resource (0x70-0x70) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.632263] pnp 00:06: io resource (0x80-0x80) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.632263] pnp 00:06: io resource (0x92-0x92) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.632263] pnp 00:06: io resource (0xb2-0xb3) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.632263] pnp 00:06: io resource (0x800-0x80f) overlaps 0000:00:1c.0 BAR 7 (0x0-0xfff), disabling
[    0.632263] pnp: PnP ACPI: found 10 devices
[    0.632263] ACPI: ACPI bus type pnp unregistered
[    0.632263] PnPBIOS: Disabled by ACPI PNP
[    0.632263] PCI: Using ACPI for IRQ routing
[    0.632263] pci 0000:00:1c.0: BAR 7: can't allocate resource
[    0.632263] pci 0000:00:1c.0: BAR 8: can't allocate resource
[    0.640041] NET: Registered protocol family 8
[    0.640043] NET: Registered protocol family 20
[    0.640060] NetLabel: Initializing
[    0.640060] NetLabel:  domain hash size = 128
[    0.640060] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.640072] NetLabel:  unlabeled traffic allowed by default
[    0.640080] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.640085] hpet0: 3 64-bit timers, 14318180 Hz
[    0.641641] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.641644]    actual entries 65620
[    0.641745] AppArmor: AppArmor Filesystem Enabled
[    0.641773] ACPI: RTC can wake from S4
[    0.644042] Switched to high resolution mode on CPU 0
[    0.644580] Switched to high resolution mode on CPU 1
[    0.648024] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.648028] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[    0.648032] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[    0.648035] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    0.648038] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.648042] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    0.648050] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[    0.648058] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.648061] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.648064] system 00:06: ioport range 0x1640-0x164f has been reserved
[    0.648068] system 00:06: ioport range 0xfe00-0xfefe has been reserved
[    0.648071] system 00:06: ioport range 0xff2c-0xff2f has been reserved
[    0.683291] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.683294] pci 0000:00:1c.0:   IO window: disabled
[    0.683301] pci 0000:00:1c.0:   MEM window: disabled
[    0.683306] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.683314] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.683317] pci 0000:00:1c.2:   IO window: disabled
[    0.683323] pci 0000:00:1c.2:   MEM window: 0xd0000000-0xd00fffff
[    0.683329] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.683337] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.683339] pci 0000:00:1c.3:   IO window: disabled
[    0.683346] pci 0000:00:1c.3:   MEM window: 0xd0100000-0xd01fffff
[    0.683351] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.683365] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.683367] pci 0000:00:1e.0:   IO window: disabled
[    0.683374] pci 0000:00:1e.0:   MEM window: 0xd0200000-0xd02fffff
[    0.683379] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.683398] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.683406] pci 0000:00:1c.0: setting latency timer to 64
[    0.683416] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.683422] pci 0000:00:1c.2: setting latency timer to 64
[    0.683432] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.683438] pci 0000:00:1c.3: setting latency timer to 64
[    0.683444] pci 0000:00:1e.0: enabling device (0004 -> 0006)
[    0.683451] pci 0000:00:1e.0: setting latency timer to 64
[    0.683455] bus: 00 index 0 io port: [0, ffff]
[    0.683457] bus: 00 index 1 mmio: [0, ffffffff]
[    0.683460] bus: 02 index 0 mmio: [0, fff]
[    0.683462] bus: 02 index 1 mmio: [0, fffff]
[    0.683464] bus: 02 index 2 mmio: [0, 0]
[    0.683466] bus: 02 index 3 mmio: [0, 0]
[    0.683468] bus: 04 index 0 mmio: [0, 0]
[    0.683471] bus: 04 index 1 mmio: [d0000000, d00fffff]
[    0.683473] bus: 04 index 2 mmio: [0, 0]
[    0.683475] bus: 04 index 3 mmio: [0, 0]
[    0.683477] bus: 05 index 0 mmio: [0, 0]
[    0.683479] bus: 05 index 1 mmio: [d0100000, d01fffff]
[    0.683482] bus: 05 index 2 mmio: [0, 0]
[    0.683484] bus: 05 index 3 mmio: [0, 0]
[    0.683486] bus: 06 index 0 mmio: [0, 0]
[    0.683488] bus: 06 index 1 mmio: [d0200000, d02fffff]
[    0.683490] bus: 06 index 2 mmio: [0, 0]
[    0.683493] bus: 06 index 3 io port: [0, ffff]
[    0.683495] bus: 06 index 4 mmio: [0, ffffffff]
[    0.683505] NET: Registered protocol family 2
[    0.696053] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.696302] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.696842] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.697147] TCP: Hash tables configured (established 131072 bind 65536)
[    0.697151] TCP reno registered
[    0.704103] NET: Registered protocol family 1
[    0.704227] checking if image is initramfs... it is
[    1.410571] Freeing initrd memory: 7999k freed
[    1.410963] Simple Boot Flag at 0x36 set to 0x1
[    1.411855] audit: initializing netlink socket (disabled)
[    1.411882] type=2000 audit(1231463923.409:1): initialized
[    1.418090] highmem bounce pool size: 64 pages
[    1.418097] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.420791] VFS: Disk quotas dquot_6.5.1
[    1.420883] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.420995] msgmni has been set to 1762
[    1.421134] io scheduler noop registered
[    1.421137] io scheduler anticipatory registered
[    1.421140] io scheduler deadline registered
[    1.421152] io scheduler cfq registered (default)
[    1.421168] pci 0000:00:02.0: Boot video device
[    1.421393] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.421444] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.421495] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.421538] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.421579] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.421694] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.421743] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.421790] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.421833] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.421875] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.421987] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.422035] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.422083] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.422123] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.422163] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.422512] isapnp: Scanning for PnP cards...
[    1.776492] isapnp: No Plug & Play device found
[    1.815178] hpet_resources: 0xfed00000 is busy
[    1.815256] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.817818] brd: module loaded
[    1.817900] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.818038] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.855136] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.855143] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.856135] mice: PS/2 mouse device common for all mice
[    1.857196] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.857227] rtc0: alarms up to one month, y3k, hpet irqs
[    1.857376] EISA: Probing bus 0 at eisa.0
[    1.857384] Cannot allocate resource for EISA slot 1
[    1.857398] Cannot allocate resource for EISA slot 5
[    1.857413] EISA: Detected 0 cards.
[    1.857416] cpuidle: using governor ladder
[    1.857419] cpuidle: using governor menu
[    1.857946] TCP cubic registered
[    1.857977] Using IPI No-Shortcut mode
[    1.858187] registered taskstats version 1
[    1.858315]   Magic number: 9:18:306
[    1.858381] tty tty35: hash matches
[    1.858438] rtc_cmos 00:07: setting system clock to 2009-01-09 01:18:44 UTC (1231463924)
[    1.858441] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.858443] EDD information not available.
[    1.858718] Freeing unused kernel memory: 424k freed
[    1.858767] Write protecting the kernel text: 2580k
[    1.858796] Write protecting the kernel read-only data: 940k
[    1.878138] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.045043] fuse init (API version 7.9)
[    2.108537] ACPI: SSDT 3F68675D, 027A (r1  PmRef  Cpu0Ist     3000 INTL 20050228)
[    2.109017] ACPI: SSDT 3F686216, 04C2 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
[    2.116177] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.116239] processor ACPI0007:00: registered as cooling_device0
[    2.116244] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.116628] ACPI: SSDT 3F6869D7, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050228)
[    2.117055] ACPI: SSDT 3F6866D8, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050228)
[    2.120019] Marking TSC unstable due to TSC halts in idle
[    2.124204] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.124252] processor ACPI0007:01: registered as cooling_device1
[    2.124256] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.143825] thermal LNXTHERM:01: registered as thermal_zone0
[    2.177678] ACPI: Thermal Zone [TZ00] (55 C)
[    2.225069] thermal LNXTHERM:02: registered as thermal_zone1
[    2.258810] ACPI: Thermal Zone [TZ01] (55 C)
[    2.580774] usbcore: registered new interface driver usbfs
[    2.580800] usbcore: registered new interface driver hub
[    2.580865] usbcore: registered new device driver usb
[    2.583203] USB Universal Host Controller Interface driver v3.0
[    2.583262] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.583272] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.583277] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.583331] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    2.583369] uhci_hcd 0000:00:1d.0: irq 23, io base 0x000050a0
[    2.583551] usb usb1: configuration #1 chosen from 1 choice
[    2.583580] hub 1-0:1.0: USB hub found
[    2.583588] hub 1-0:1.0: 2 ports detected
[    2.653751] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.685322] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.685333] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.685338] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.685366] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    2.685410] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000050c0
[    2.685514] usb usb2: configuration #1 chosen from 1 choice
[    2.685543] hub 2-0:1.0: USB hub found
[    2.685551] hub 2-0:1.0: 2 ports detected
[    2.694945] No dock devices found.
[    2.719199] SCSI subsystem initialized
[    2.738391] libata version 3.00 loaded.
[    2.893325] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.893338] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.893343] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.893370] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    2.893412] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000050e0
[    2.893518] usb usb3: configuration #1 chosen from 1 choice
[    2.893547] hub 3-0:1.0: USB hub found
[    2.893561] hub 3-0:1.0: 2 ports detected
[    2.996597] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.996609] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.996614] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.996641] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    2.996681] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00005400
[    2.996782] usb usb4: configuration #1 chosen from 1 choice
[    2.996813] hub 4-0:1.0: USB hub found
[    2.996820] hub 4-0:1.0: 2 ports detected
[    3.005150] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.100768] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.100784] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.100788] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.100821] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.104752] ehci_hcd 0000:00:1d.7: debug port 1
[    3.104761] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.104770] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0644000
[    3.136056] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.136380] usb usb5: configuration #1 chosen from 1 choice
[    3.136430] hub 5-0:1.0: USB hub found
[    3.136439] hub 5-0:1.0: 8 ports detected
[    3.340681] ata_piix 0000:00:1f.1: version 2.12
[    3.340697] ata_piix 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.340743] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.340825] scsi0 : ata_piix
[    3.340930] scsi1 : ata_piix
[    3.341631] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x5090 irq 14
[    3.341635] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x5098 irq 15
[    3.500137] Clocksource tsc unstable (delta = -355709705 ns)
[    3.504635] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WP03, max UDMA/33
[    3.520575] ata1.00: configured for UDMA/33
[    3.520658] ata2: port disabled. ignoring.
[    3.524419] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WP03 PQ: 0 ANSI: 5
[    3.524649] tg3.c:v3.94 (August 14, 2008)
[    3.524673] tg3 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.524689] tg3 0000:04:00.0: setting latency timer to 64
[    3.524842] ahci 0000:00:1f.2: version 3.0
[    3.524853] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.524961] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x1 impl SATA mode
[    3.524965] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    3.524971] ahci 0000:00:1f.2: setting latency timer to 64
[    3.525080] scsi2 : ahci
[    3.525147] scsi3 : ahci
[    3.525208] scsi4 : ahci
[    3.525275] scsi5 : ahci
[    3.525379] ata3: SATA max UDMA/133 abar m1024@0xd0644400 port 0xd0644500 irq 220
[    3.525382] ata4: DUMMY
[    3.525384] ata5: DUMMY
[    3.525385] ata6: DUMMY
[    3.532411] usb 2-1: device not accepting address 2, error -71
[    3.567650] eth0: Tigon3 [partno(BCM95787m) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:16:d4:e3:67:59
[    3.567655] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    3.567658] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    3.588173] hub 2-0:1.0: unable to enumerate USB device on port 1
[    3.884134] usb 5-4: new high speed USB device using ehci_hcd and address 3
[    4.025871] usb 5-4: configuration #1 chosen from 1 choice
[    4.068112] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.069334] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    4.069515] ata3.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC70P, max UDMA/100
[    4.069523] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.071031] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    4.071210] ata3.00: configured for UDMA/100
[    4.084369] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
[    4.098246] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    4.098288] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    4.112774] Driver 'sd' needs updating - please use bus_type methods
[    4.112892] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.112910] sd 2:0:0:0: [sda] Write Protect is off
[    4.112913] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.112939] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.113026] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.113041] sd 2:0:0:0: [sda] Write Protect is off
[    4.113044] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.113071] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.113075]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.136276] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.136286] Uniform CD-ROM driver Revision: 3.20
[    4.136470] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.272074] usb 2-1: new low speed USB device using uhci_hcd and address 4
[    4.446288] usb 2-1: configuration #1 chosen from 1 choice
[    4.474772] usbcore: registered new interface driver hiddev
[    4.489011] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input2
[    4.489298] input,hidraw0: USB HID v1.10 Mouse [Genius Optical Mouse] on usb-0000:00:1d.1-1
[    4.489316] usbcore: registered new interface driver usbhid
[    4.489319] usbhid: v2.6:USB HID core driver
[    4.518226]  sda1 sda2 sda3 < sda5 >
[    4.537819] sd 2:0:0:0: [sda] Attached SCSI disk
[    5.043413] kjournald starting.  Commit interval 5 seconds
[    5.043435] EXT3-fs: mounted filesystem with ordered data mode.
[   12.504690] udevd version 124 started
[   13.164164] Linux agpgart interface v0.103
[   13.205454] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   13.205979] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   13.223647] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   13.393764] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.426619] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.591040] intel_rng: FWH not detected
[   13.680170] sdhci: Secure Digital Host Controller Interface driver
[   13.680174] sdhci: Copyright(c) Pierre Ossman
[   13.696155] sdhci-pci 0000:06:00.1: SDHCI controller found [1524:0750] (rev 0)
[   13.696171] sdhci-pci 0000:06:00.1: enabling device (0000 -> 0002)
[   13.696184] sdhci-pci 0000:06:00.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   13.696892] mmc0: SDHCI controller on PCI [0000:06:00.1] using PIO
[   13.696912] sdhci-pci 0000:06:00.3: SDHCI controller found [1524:0751] (rev 0)
[   13.696927] sdhci-pci 0000:06:00.3: enabling device (0000 -> 0002)
[   13.696934] sdhci-pci 0000:06:00.3: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   13.697032] mmc1: SDHCI controller on PCI [0000:06:00.3] using PIO
[   13.765623] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   13.784037] ACPI: Power Button (FF) [PWRF]
[   13.784123] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   13.784206] ACPI: Lid Switch [LID]
[   13.784261] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   13.792139] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   13.816032] ACPI: Sleep Button (CM) [SLPB]
[   13.816123] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input7
[   13.832018] ACPI: Power Button (CM) [PWRB]
[   13.933440] ACPI: WMI: Mapper loaded
[   14.011054] iTCO_vendor_support: vendor-support=0
[   14.052708] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   14.054957] ACPI: EC: GPE storm detected, transactions will use polling mode
[   14.170178] acpi device:07: registered as cooling_device2
[   14.170333] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/input/input8
[   14.193335] Linux video capture interface: v2.00
[   14.289464] uvcvideo: Found UVC 1.00 device Acer CrystalEye webcam (064e:a101)
[   14.290634] input: Acer CrystalEye webcam as /devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4:1.0/input/input9
[   14.487856] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input10
[   14.488252] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   14.520227] usbcore: registered new interface driver uvcvideo
[   14.520232] USB Video Class driver (v0.1.0)
[   14.608854] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
[   14.666731] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   14.666812] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.800164] acer-wmi: Acer Laptop ACPI-WMI Extras
[   14.828277] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   14.828281] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   14.828360] iwl3945 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.828375] iwl3945 0000:05:00.0: setting latency timer to 64
[   14.828399] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   14.905753] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   14.906233] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   14.933047] ACPI: EC: missing confirmations, switch off interrupt mode.
[   14.961183] ACPI: Battery Slot [BAT1] (battery present)
[   15.006206] ACPI: AC Adapter [ACAD] (off-line)
[   15.429581] iwl3945 0000:05:00.0: PCI INT A disabled
[   15.612305] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.612337] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.525021] lp: driver loaded but no devices found
[   16.765344] EXT3 FS on sda5, internal journal
[   17.869776] type=1505 audit(1231471140.509:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4210
[   18.057440] type=1505 audit(1231471140.697:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4215
[   18.057678] type=1505 audit(1231471140.697:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4215
[   18.218742] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.959389] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   20.066831] apm: BIOS not found.
[   20.238423] ppdev: user-space parallel port driver
[   23.335316] Bluetooth: Core ver 2.13
[   23.336214] NET: Registered protocol family 31
[   23.336224] Bluetooth: HCI device and connection manager initialized
[   23.336231] Bluetooth: HCI socket layer initialized
[   23.366190] Bluetooth: L2CAP ver 2.11
[   23.366202] Bluetooth: L2CAP socket layer initialized
[   23.390489] Bluetooth: SCO (Voice Link) ver 0.6
[   23.390501] Bluetooth: SCO socket layer initialized
[   23.413131] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.413143] Bluetooth: BNEP filters: protocol multicast
[   23.445083] Bluetooth: RFCOMM socket layer initialized
[   23.459923] Bluetooth: RFCOMM TTY layer initialized
[   23.459938] Bluetooth: RFCOMM ver 1.10
[   23.460353] Bridge firewalling registered
[   27.869616] iwl3945 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   27.869767] iwl3945 0000:05:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   27.871339] firmware: requesting iwlwifi-3945-1.ucode
[   27.994884] Registered led device: iwl-phy0:radio
[   27.994958] Registered led device: iwl-phy0:assoc
[   27.994988] Registered led device: iwl-phy0:RX
[   27.995017] Registered led device: iwl-phy0:TX
[   28.078444] NET: Registered protocol family 17
[   28.116278] [drm] Initialized drm 1.1.0 20060810
[   28.121990] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.122001] pci 0000:00:02.0: setting latency timer to 64
[   28.122728] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   30.862529] wlan0: authenticate with AP 00:15:6d:63:48:4e
[   31.060038] wlan0: authenticate with AP 00:15:6d:63:48:4e
[   31.264041] wlan0: authenticate with AP 00:15:6d:63:48:4e
[   31.460135] wlan0: authentication with AP 00:15:6d:63:48:4e timed out
[   42.333643] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[   42.352444] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[   43.591327] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[   43.615372] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[   44.806258] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[   44.828489] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[   45.762951] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[   45.785286] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[   47.016112] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[   47.038409] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[   48.398350] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[   48.417232] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[   52.411387] NET: Registered protocol family 10
[   52.412485] lo: Disabled Privacy Extensions
[   52.413599] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.414742] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   52.804869] CPU0 attaching NULL sched-domain.
[   52.804880] CPU1 attaching NULL sched-domain.
[   52.829085] CPU0 attaching sched-domain:
[   52.829091]  domain 0: span 0-1 level MC
[   52.829095]   groups: 0 1
[   52.829100]   domain 1: span 0-1 level CPU
[   52.829103]    groups: 0-1
[   52.829107] CPU1 attaching sched-domain:
[   52.829110]  domain 0: span 0-1 level MC
[   52.829112]   groups: 1 0
[   52.829117]   domain 1: span 0-1 level CPU
[   52.829120]    groups: 0-1
[   56.243787] wlan0: authenticate with AP 00:14:bf:d3:23:cb
[   56.245307] wlan0: authenticated
[   56.245313] wlan0: associate with AP 00:14:bf:d3:23:cb
[   56.247381] wlan0: RX AssocResp from 00:14:bf:d3:23:cb (capab=0x451 status=0 aid=1)
[   56.247385] wlan0: associated
[   56.250847] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   65.832520] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[   65.856334] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[   66.748102] wlan0: no IPv6 routers present
[   67.035427] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[   67.057260] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[   68.938290] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[   68.958939] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[   70.038204] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[   70.059724] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[   77.520741] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[   77.546244] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[   82.737004] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[   82.757311] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[   84.150246] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[   84.355669] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[   96.356350] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[   96.375579] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[   98.465933] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[   98.485162] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[   99.630855] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[   99.650801] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[  108.334708] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[  108.359929] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[  110.216579] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[  110.235999] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[  130.597056] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[  130.745134] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[  227.568172] usb 2-1: USB disconnect, address 4

```

---

### Post by Hei Ku on 2009-01-09
[  227.568172] usb 2-1: USB disconnect, address 4

Es como que se desconectara. Probaste de reconectarlo en esos casos?

---

### Post by luks911 on 2009-01-09
Buenas,
Buscando por este mensaje
```
psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
```
encontré este thread[0] en el que plantean una solución.
Consiste en pasarle unos parámetros al kernel modificando el grub, es decir el archivo /boot/grub/menu.lst.
Para probarlo sin cambiar nada de forma permanente y ver si funciona, hacé lo siguiente:
1) en el inicio apretás la tecla ESC para entrar en el menú de GRUB.
2) sobre la línea del kernel que usás siempre presionás "e" para editar
3) bajás a la línea que comienza con "kernel /boot/vmlinuz..."
4) presionás "e" para editarla
5) al final de esa línea le agregás "i8042.reset i8042.nomux" (sin las comillas)
6) le das Enter para aceptar el cambio y apretás la tecla "b" para iniciar el sistema

Si funcionó, para que el cambio se vuelva permanente hay que editar la misma línea en el menu.lst:

1) backup del archivo por si las dudas, en terminal
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
2) editas el archivo
```
sudo gedit /boot/grub/menu.lst
```
3) otra vez al final de la línea que empieza con "kernel /boot/vmlinuz..." agregás "i8042.reset i8042.nomux", siempre sin las comillas.
4) guardás el archivo

[0] [http://ubuntuforums.org/archive/index.php/t-794670.html](http://ubuntuforums.org/archive/index.php/t-794670.html)

---

### Post by emiliano_raso on 2009-01-09
Gracias por responder pero. No tengo muchos conocimientos :-P Uso linux hace poco...

Voy a probar que puedo hacer.

Muchas gracias...

---

### Post by Mauro22 on 2009-01-09
Yo tengo la 5730z y anda lo mas bien, en el xorg.conf no tengo nada referente al mouse, solo video.

Yo instale el 8.10 hace 2 semanas practicamente, por ahi tiene alguna actualizacion que te falta o algo asi. Lo tenes al dia?


Te digo, porque es raro que a mi me ande siendo un modelo mayor que supuestamente tiene que manejar correctamente este touchpad y sus precesores.


No se me ocurre otra cosa, salvo probar con algun mouse USB, a ver que pasa, si falla tambien es algo de la controladora de mouse y no del touchpad en si.


Saludos!

---

### Post by z37a on 2009-01-10
Yo tengo una 5310 con un problema similar, el touchpad ALS(creo que es la marca, por que no es el synaptics) no anda nada bien en linux y si anda en Windows, se me vuelve loco, me hace clicks demás cuando paso el dedo o se mueve para otros lados de forma violenta.

---

### Post by emiliano_raso on 2009-01-24
> **Mauro22 said:**
> 
No se me ocurre otra cosa, salvo probar con algun mouse USB, a ver que pasa, si falla tambien es algo de la controladora de mouse y no del touchpad en si.

Gracias gente por responder.
En cuanto a eso Mauro, tengo un mouse usb genius y anda barbaro. No tengo ninguno de los problemas que tengo con el touchpad.

---

### Post by emiliano_raso on 2009-05-15
Bueno. Ya es un poquito viejo el thread, pero encontre una "solucion".
Debo aclarar que esto solamente pasa en Ubuntu 8.04 y 8.10
En Ubuntu 9.04 no me esta pasando.
Para las versiones anteriores encontre una solucion parcial:
- Abrimos el xorg.conf:
```
sudo gedit /etc/X11/xorg.conf
```
-Agregamos esta seccion al final:
```
Section "InputDevice"
	Identifier "Synaptics Mouse"
	Driver "synaptics"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "LeftEdge" "120"
	Option "RightEdge" "930"
	Option "TopEdge" "120"
	Option "BottomEdge" "650"
	Option "FingerLow" "14"
	Option "FingerHigh" "15"
	Option "MaxTapTime" "0"
	Option "MaxTapMove" "110"
	Option "VertScrollDelta" "20"
	Option "MinSpeed" "0.3"
	Option "MaxSpeed" "0.75"
	Option "AccelFactor" "0.030"
	Option "EdgeMotionMinSpeed" "200"
	Option "EdgeMotionMaxSpeed" "200"
	Option "UpDownScrolling" "1"
	Option "CircularScrolling" "1"
	Option "CircScrollDelta" "0.1"
	Option "CircScrollTrigger" "2"
EndSection
```
- Guardamos el archivo y reiniciamos la maquina.

Porque digo que es una solucion parcial? Porque cuando encendemos la maquina, el sistema no "toma" esta seccion, y es necesario una vez que termino de encender, volver a reiniciar la notebook.
Realmente no se porque sucede eso.
La seccion esa me la robé del xorg.conf de PuppyLinux. Cuando boteé Puppy en mi notebook me di cuenta que no pasaba, revise el xorg.conf y encontré eso.

Lastima que no funcione apenas enciende la maquina. Pero bueno, al menos es una solucion parcial. En internet he estado buscando meses y no encontre nada de nada.
Si tienen este problema y pueden actualizarse a 9.04 mejor, porque ahi no pasa, pero si se quieren quedar en 8.x entonces es lo unico que les puedo ofrecer. Otra solucion no encontré xP

Espero que sirva.

---

