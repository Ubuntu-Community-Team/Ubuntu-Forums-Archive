---
title: "ubuntu freezes"
date: 2008-10-31
forum: General Help
---

### Post by FFe_ on 2008-10-31
hello everybody. As the title says, my ubuntu freezes and i can't do anything but turn off my computer by pressing the power switch.

Same thing was happening with other ubuntu install, and with kubuntu, so i decided to install a basic console system, and installed other manually.
everything worked fine. 
so i decided to install the restricted drivers for video and wireless.
The video driver seemed to work fine, so i proecedeed with the wireless.
when i managed to my network running, the freezes started again.
Yesterday i was using my wireless connection and watching a movieclip, and it freezed 3 times in less than 5 minutes.
now i'm using wireless and everything works fine...
i don't know what can be making this happens.
anyone can give me a clue?

ah, i'm using a Compaq laptop V3415 with a geForce 6150 and a Broadcom 4311 (rev02)

thank you very much.

---

### Post by Titan8990 on 2008-10-31
Post the outputs of the following:

cat /var/log/syslog


cat /var/log/syslog.0

---

### Post by FFe_ on 2008-10-31
the second command returns a file doesn't exists error.
the first one throws a million lines, so i'm cutting it to post the instants before crashes.

this seems to be the first one:
```

Oct 31 02:08:58 miniub syslogd 1.5.0#1ubuntu1: restart.
Oct 31 02:08:58 miniub kernel: Inspecting /boot/System.map-2.6.24-21-generic
Oct 31 02:08:58 miniub kernel: Loaded 27897 symbols from /boot/System.map-2.6.24-21-generic.
Oct 31 02:08:58 miniub kernel: Symbols match kernel version 2.6.24.
Oct 31 02:08:58 miniub kernel: Loaded 33200 symbols from 77 modules.
Oct 31 02:08:58 miniub kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 31 02:08:58 miniub kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 31 02:08:58 miniub kernel: [    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:43:45 UTC 2008 (Ubuntu 2.6.24-21.43-generic)
Oct 31 02:08:58 miniub kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 31 02:08:58 miniub kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Oct 31 02:08:58 miniub kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Oct 31 02:08:58 miniub kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
Oct 31 02:08:58 miniub kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000057f10000 (usable)
Oct 31 02:08:58 miniub kernel: [    0.000000]  BIOS-e820: 0000000057f10000 - 0000000057f17000 (ACPI data)
Oct 31 02:08:58 miniub kernel: [    0.000000]  BIOS-e820: 0000000057f17000 - 0000000057f80000 (ACPI NVS)
Oct 31 02:08:58 miniub kernel: [    0.000000]  BIOS-e820: 0000000057f80000 - 0000000060000000 (reserved)
Oct 31 02:08:58 miniub kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Oct 31 02:08:58 miniub kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Oct 31 02:08:58 miniub kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Oct 31 02:08:58 miniub kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 31 02:08:58 miniub kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Oct 31 02:08:58 miniub kernel: [    0.000000] 511MB HIGHMEM available.
Oct 31 02:08:58 miniub kernel: [    0.000000] 896MB LOWMEM available.
Oct 31 02:08:58 miniub kernel: [    0.000000] found SMP MP-table at 000f8780
Oct 31 02:08:58 miniub kernel: [    0.000000] Entering add_active_range(0, 0, 360208) 0 entries of 256 used
Oct 31 02:08:58 miniub kernel: [    0.000000] Zone PFN ranges:
Oct 31 02:08:58 miniub kernel: [    0.000000]   DMA             0 ->     4096
Oct 31 02:08:58 miniub kernel: [    0.000000]   Normal       4096 ->   229376
Oct 31 02:08:58 miniub kernel: [    0.000000]   HighMem    229376 ->   360208
Oct 31 02:08:58 miniub kernel: [    0.000000] Movable zone start PFN for each node
Oct 31 02:08:58 miniub kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 31 02:08:58 miniub kernel: [    0.000000]     0:        0 ->   360208
Oct 31 02:08:58 miniub kernel: [    0.000000] On node 0 totalpages: 360208
Oct 31 02:08:58 miniub kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Oct 31 02:08:58 miniub kernel: [    0.000000]   DMA zone: 0 pages reserved
Oct 31 02:08:58 miniub kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Oct 31 02:08:58 miniub kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Oct 31 02:08:58 miniub kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Oct 31 02:08:58 miniub kernel: [    0.000000]   HighMem zone: 1022 pages used for memmap
Oct 31 02:08:58 miniub kernel: [    0.000000]   HighMem zone: 129810 pages, LIFO batch:31
Oct 31 02:08:58 miniub kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Oct 31 02:08:58 miniub kernel: [    0.000000] DMI present.
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F87B0 checksum 0
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: RSDP 000F87B0, 0024 (r3 HPQOEM)
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: XSDT 57F100CE, 005C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: FACP 57F16B42, 00F4 (r3 HPQOEM SLIC-MPC  6040000 PTL     F4240)
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: DSDT 57F1012A, 6A18 (r1 HPQOEM SLIC-MPC  6040000 MSFT  100000E)
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: FACS 57F17FC0, 0040
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: SLIC 57F16CAA, 0176 (r1 HPQOEM SLIC-MPC  6040000 HPQ         1)
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: MCFG 57F16E20, 003C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: HPET 57F16E5C, 0038 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: APIC 57F16E94, 0050 (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: BOOT 57F16EE4, 0028 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: SSDT 57F16F0C, 00F4 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: DMI detected: Hewlett-Packard
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct 31 02:08:58 miniub kernel: [    0.000000] Processor #0 15:12 APIC version 16
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Oct 31 02:08:58 miniub kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 31 02:08:58 miniub kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 31 02:08:58 miniub kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
Oct 31 02:08:58 miniub kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 31 02:08:58 miniub kernel: [    0.000000] Allocating PCI resources starting at 68000000 (gap: 60000000:80000000)
Oct 31 02:08:58 miniub kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
Oct 31 02:08:58 miniub kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
Oct 31 02:08:58 miniub kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
Oct 31 02:08:58 miniub kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
Oct 31 02:08:58 miniub kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 357394
Oct 31 02:08:58 miniub kernel: [    0.000000] Kernel command line: root=UUID=9c41d09f-5864-470d-a350-acfda4da607a ro quiet splash
Oct 31 02:08:58 miniub kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Oct 31 02:08:58 miniub kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Oct 31 02:08:58 miniub kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 31 02:08:58 miniub kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 31 02:08:58 miniub kernel: [    0.000000] Initializing CPU#0
Oct 31 02:08:58 miniub kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 31 02:08:58 miniub kernel: [    0.000000] Detected 1808.269 MHz processor.
Oct 31 02:08:58 miniub kernel: [   11.330269] spurious 8259A interrupt: IRQ7.
Oct 31 02:08:58 miniub kernel: [   11.333367] Console: colour VGA+ 80x25
Oct 31 02:08:58 miniub kernel: [   11.333371] console [tty0] enabled
Oct 31 02:08:58 miniub kernel: [   11.333793] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 31 02:08:58 miniub kernel: [   11.334226] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 31 02:08:58 miniub kernel: [   11.384246] Memory: 1416224k/1440832k available (2177k kernel code, 23352k reserved, 1005k data, 368k init, 523328k highmem)
Oct 31 02:08:58 miniub kernel: [   11.384255] virtual kernel memory layout:
Oct 31 02:08:58 miniub kernel: [   11.384256]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Oct 31 02:08:58 miniub kernel: [   11.384257]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 31 02:08:58 miniub kernel: [   11.384258]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Oct 31 02:08:58 miniub kernel: [   11.384260]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Oct 31 02:08:58 miniub kernel: [   11.384261]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Oct 31 02:08:58 miniub kernel: [   11.384262]       .data : 0xc03205e4 - 0xc041bdc4   (1005 kB)
Oct 31 02:08:58 miniub kernel: [   11.384263]       .text : 0xc0100000 - 0xc03205e4   (2177 kB)
Oct 31 02:08:58 miniub kernel: [   11.384266] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 31 02:08:58 miniub kernel: [   11.384306] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Oct 31 02:08:58 miniub kernel: [   11.384457] hpet clockevent registered
Oct 31 02:08:58 miniub kernel: [   11.464416] Calibrating delay using timer specific routine.. 3619.68 BogoMIPS (lpj=7239362)
Oct 31 02:08:58 miniub kernel: [   11.464439] Security Framework initialized
Oct 31 02:08:58 miniub kernel: [   11.464446] SELinux:  Disabled at boot.
Oct 31 02:08:58 miniub kernel: [   11.464462] AppArmor: AppArmor initialized
Oct 31 02:08:58 miniub kernel: [   11.464466] Failure registering capabilities with primary security module.
Oct 31 02:08:58 miniub kernel: [   11.464474] Mount-cache hash table entries: 512
Oct 31 02:08:58 miniub kernel: [   11.464590] Initializing cgroup subsys ns
Oct 31 02:08:58 miniub kernel: [   11.464594] Initializing cgroup subsys cpuacct
Oct 31 02:08:58 miniub kernel: [   11.464605] CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 00000019 00000000
Oct 31 02:08:58 miniub kernel: [   11.464614] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Oct 31 02:08:58 miniub kernel: [   11.464616] CPU: L2 Cache: 512K (64 bytes/line)
Oct 31 02:08:58 miniub kernel: [   11.464619] CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00020410 00002001 00000000 00000019 00000000
Oct 31 02:08:58 miniub kernel: [   11.464629] Compat vDSO mapped to ffffe000.
Oct 31 02:08:58 miniub kernel: [   11.464641] Checking 'hlt' instruction... OK.
Oct 31 02:08:58 miniub kernel: [   11.480730] SMP alternatives: switching to UP code
Oct 31 02:08:58 miniub kernel: [   11.481896] Freeing SMP alternatives: 11k freed
Oct 31 02:08:58 miniub kernel: [   11.482009] Early unpacking initramfs... done
Oct 31 02:08:58 miniub kernel: [   11.788227] ACPI: Core revision 20070126
Oct 31 02:08:58 miniub kernel: [   11.788314] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 31 02:08:58 miniub kernel: [   11.799057] CPU0: AMD Mobile AMD Sempron(tm) stepping 02
Oct 31 02:08:58 miniub kernel: [   11.799070] Total of 1 processors activated (3619.68 BogoMIPS).
Oct 31 02:08:58 miniub kernel: [   11.799371] ENABLING IO-APIC IRQs
Oct 31 02:08:58 miniub kernel: [   11.799600] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 31 02:08:58 miniub kernel: [   11.944209] Brought up 1 CPUs
Oct 31 02:08:58 miniub kernel: [   11.944256] CPU0 attaching sched-domain:
Oct 31 02:08:58 miniub kernel: [   11.944258]  domain 0: span 01
Oct 31 02:08:58 miniub kernel: [   11.944260]   groups: 01
Oct 31 02:08:58 miniub kernel: [   11.944410] net_namespace: 64 bytes
Oct 31 02:08:58 miniub kernel: [   11.944418] Booting paravirtualized kernel on bare hardware
Oct 31 02:08:58 miniub kernel: [   11.944864] Time:  2:08:35  Date: 10/31/08
Oct 31 02:08:58 miniub kernel: [   11.944886] NET: Registered protocol family 16
Oct 31 02:08:58 miniub kernel: [   11.945047] EISA bus registered
Oct 31 02:08:58 miniub kernel: [   11.945052] ACPI: bus type pci registered
Oct 31 02:08:58 miniub kernel: [   11.957100] PCI: BIOS BUG #81[49435000] found
Oct 31 02:08:58 miniub kernel: [   11.957143] PCI: Using configuration type 1
Oct 31 02:08:58 miniub kernel: [   11.957152] Setting up standard PCI resources
Oct 31 02:08:58 miniub kernel: [   11.958851] ACPI: EC: Look up EC in DSDT
Oct 31 02:08:58 miniub kernel: [   11.962958] ACPI: BIOS _OSI(Linux) query ignored via DMI
Oct 31 02:08:58 miniub kernel: [   11.963241] ACPI: Interpreter enabled
Oct 31 02:08:58 miniub kernel: [   11.963244] ACPI: (supports S0 S3 S4 S5)
Oct 31 02:08:58 miniub kernel: [   11.963256] ACPI: Using IOAPIC for interrupt routing
Oct 31 02:08:58 miniub kernel: [   11.963660] ACPI: EC: non-query interrupt received, switching to interrupt mode
Oct 31 02:08:58 miniub kernel: [   11.991317] ACPI: EC: GPE = 0x1, I/O: command/status = 0x66, data = 0x62
Oct 31 02:08:58 miniub kernel: [   11.991320] ACPI: EC: driver started in interrupt mode
Oct 31 02:08:58 miniub kernel: [   11.991360] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 31 02:08:58 miniub kernel: [   11.992368] PCI: Transparent bridge - 0000:00:10.0
Oct 31 02:08:58 miniub kernel: [   11.992383] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct 31 02:08:58 miniub kernel: [   11.992476] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
Oct 31 02:08:58 miniub kernel: [   11.992512] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
Oct 31 02:08:58 miniub kernel: [   11.992539] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
Oct 31 02:08:58 miniub kernel: [   12.121524] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 17 18 22 23) *0, disabled.
Oct 31 02:08:58 miniub kernel: [   12.121713] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 17 18 22 23) *10
Oct 31 02:08:58 miniub kernel: [   12.121897] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
Oct 31 02:08:58 miniub kernel: [   12.122083] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
Oct 31 02:08:58 miniub kernel: [   12.122268] ACPI: PCI Interrupt Link [LK1E] (IRQs 20) *0, disabled.
Oct 31 02:08:58 miniub kernel: [   12.122451] ACPI: PCI Interrupt Link [LK2E] (IRQs 19) *10
Oct 31 02:08:58 miniub kernel: [   12.122635] ACPI: PCI Interrupt Link [LK3E] (IRQs 21) *10
Oct 31 02:08:58 miniub kernel: [   12.122818] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 18 22 23) *0, disabled.
Oct 31 02:08:58 miniub kernel: [   12.123003] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 22 23) *10
Oct 31 02:08:58 miniub kernel: [   12.123193] ACPI: PCI Interrupt Link [LSMU] (IRQs 16 17 18 22 23) *11
Oct 31 02:08:58 miniub kernel: [   12.123378] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 22 23) *11
Oct 31 02:08:58 miniub kernel: [   12.123563] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 22 23) *7
Oct 31 02:08:58 miniub kernel: [   12.123747] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 22 23) *11
Oct 31 02:08:58 miniub kernel: [   12.123937] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 22 23) *0, disabled.
Oct 31 02:08:58 miniub kernel: [   12.124126] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 18 22 23) *0, disabled.
Oct 31 02:08:58 miniub kernel: [   12.124311] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 18 22 23) *0, disabled.
Oct 31 02:08:58 miniub kernel: [   12.124496] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 22 23) *0, disabled.
Oct 31 02:08:58 miniub kernel: [   12.124688] ACPI: PCI Interrupt Link [LTID] (IRQs 16 17 18 22 23) *5
Oct 31 02:08:58 miniub kernel: [   12.124878] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 22 23) *0
Oct 31 02:08:58 miniub kernel: [   12.124990] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 31 02:08:58 miniub kernel: [   12.125016] pnp: PnP ACPI init
Oct 31 02:08:58 miniub kernel: [   12.125023] ACPI: bus type pnp registered
Oct 31 02:08:58 miniub kernel: [   12.128684] pnp: PnP ACPI: found 11 devices
Oct 31 02:08:58 miniub kernel: [   12.128686] ACPI: ACPI bus type pnp unregistered
Oct 31 02:08:58 miniub kernel: [   12.128689] PnPBIOS: Disabled by ACPI PNP
Oct 31 02:08:58 miniub kernel: [   12.128873] PCI: Using ACPI for IRQ routing
Oct 31 02:08:58 miniub kernel: [   12.128876] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 31 02:08:58 miniub kernel: [   12.144071] NET: Registered protocol family 8
Oct 31 02:08:58 miniub kernel: [   12.144073] NET: Registered protocol family 20
Oct 31 02:08:58 miniub kernel: [   12.144103] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
Oct 31 02:08:58 miniub kernel: [   12.144108] hpet0: 3 32-bit timers, 25000000 Hz
Oct 31 02:08:58 miniub kernel: [   12.145151] AppArmor: AppArmor Filesystem Enabled
Oct 31 02:08:58 miniub kernel: [   12.148057] Time: tsc clocksource has been installed.
Oct 31 02:08:58 miniub kernel: [   12.148068] Switched to high resolution mode on CPU 0
Oct 31 02:08:58 miniub kernel: [   12.156046] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
Oct 31 02:08:58 miniub kernel: [   12.156051] system 00:02: ioport range 0x1000-0x107f has been reserved
Oct 31 02:08:58 miniub kernel: [   12.156054] system 00:02: ioport range 0x1080-0x10ff has been reserved
Oct 31 02:08:58 miniub kernel: [   12.156057] system 00:02: ioport range 0x1400-0x147f has been reserved
Oct 31 02:08:58 miniub kernel: [   12.156059] system 00:02: ioport range 0x1480-0x14ff has been reserved
Oct 31 02:08:58 miniub kernel: [   12.156062] system 00:02: ioport range 0x1800-0x187f has been reserved
Oct 31 02:08:58 miniub kernel: [   12.156065] system 00:02: ioport range 0x1880-0x18ff has been reserved
Oct 31 02:08:58 miniub kernel: [   12.156068] system 00:02: ioport range 0x2000-0x203f has been reserved
Oct 31 02:08:58 miniub kernel: [   12.156073] system 00:03: ioport range 0x360-0x361 has been reserved
Oct 31 02:08:58 miniub kernel: [   12.156076] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
Oct 31 02:08:58 miniub kernel: [   12.186407] PCI: Bridge: 0000:00:02.0
Oct 31 02:08:58 miniub kernel: [   12.186409]   IO window: disabled.
Oct 31 02:08:58 miniub kernel: [   12.186412]   MEM window: b3000000-b30fffff
Oct 31 02:08:58 miniub kernel: [   12.186414]   PREFETCH window: disabled.
Oct 31 02:08:58 miniub kernel: [   12.186417] PCI: Bridge: 0000:00:03.0
Oct 31 02:08:58 miniub kernel: [   12.186419]   IO window: 4000-4fff
Oct 31 02:08:58 miniub kernel: [   12.186421]   MEM window: b4000000-b7ffffff
Oct 31 02:08:58 miniub kernel: [   12.186424]   PREFETCH window: d0000000-d01fffff
Oct 31 02:08:58 miniub kernel: [   12.186426] PCI: Bridge: 0000:00:10.0
Oct 31 02:08:58 miniub kernel: [   12.186428]   IO window: disabled.
Oct 31 02:08:58 miniub kernel: [   12.186430]   MEM window: disabled.
Oct 31 02:08:58 miniub kernel: [   12.186433]   PREFETCH window: disabled.
Oct 31 02:08:58 miniub kernel: [   12.186445] PCI: Setting latency timer of device 0000:00:02.0 to 64
Oct 31 02:08:58 miniub kernel: [   12.186452] PCI: Setting latency timer of device 0000:00:03.0 to 64
Oct 31 02:08:58 miniub kernel: [   12.186460] PCI: Setting latency timer of device 0000:00:10.0 to 64
Oct 31 02:08:58 miniub kernel: [   12.186470] NET: Registered protocol family 2
Oct 31 02:08:58 miniub kernel: [   12.224057] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 31 02:08:58 miniub kernel: [   12.224352] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 31 02:08:58 miniub kernel: [   12.225301] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 31 02:08:58 miniub kernel: [   12.225808] TCP: Hash tables configured (established 131072 bind 65536)
Oct 31 02:08:58 miniub kernel: [   12.225811] TCP reno registered
Oct 31 02:08:58 miniub kernel: [   12.236103] checking if image is initramfs... it is
Oct 31 02:08:58 miniub kernel: [   12.828518] Freeing initrd memory: 7141k freed
Oct 31 02:08:58 miniub kernel: [   12.828658] Simple Boot Flag at 0x36 set to 0x1
Oct 31 02:08:58 miniub kernel: [   12.829064] audit: initializing netlink socket (disabled)
Oct 31 02:08:58 miniub kernel: [   12.829077] audit(1225418916.336:1): initialized
Oct 31 02:08:58 miniub kernel: [   12.829218] highmem bounce pool size: 64 pages
Oct 31 02:08:58 miniub kernel: [   12.830760] VFS: Disk quotas dquot_6.5.1
Oct 31 02:08:58 miniub kernel: [   12.830825] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 31 02:08:58 miniub kernel: [   12.830940] io scheduler noop registered
Oct 31 02:08:58 miniub kernel: [   12.830942] io scheduler anticipatory registered
Oct 31 02:08:58 miniub kernel: [   12.830944] io scheduler deadline registered
Oct 31 02:08:58 miniub kernel: [   12.830958] io scheduler cfq registered (default)
Oct 31 02:08:58 miniub kernel: [   12.830971] pci 0000:00:00.0: Enabling HT MSI Mapping
Oct 31 02:08:58 miniub kernel: [   12.831001] pci 0000:00:02.0: Enabling HT MSI Mapping
Oct 31 02:08:58 miniub kernel: [   12.831009] pci 0000:00:03.0: Enabling HT MSI Mapping
Oct 31 02:08:58 miniub kernel: [   12.831017] Boot video device is 0000:00:05.0
Oct 31 02:08:58 miniub kernel: [   12.831037] pci 0000:00:09.0: Enabling HT MSI Mapping
Oct 31 02:08:58 miniub kernel: [   13.035579] pci 0000:00:0e.0: Enabling HT MSI Mapping
Oct 31 02:08:58 miniub kernel: [   13.035588] pci 0000:00:10.0: Enabling HT MSI Mapping
Oct 31 02:08:58 miniub kernel: [   13.035599] pci 0000:00:10.1: Enabling HT MSI Mapping
Oct 31 02:08:58 miniub kernel: [   13.035704] PCI: Setting latency timer of device 0000:00:02.0 to 64
Oct 31 02:08:58 miniub kernel: [   13.035725] assign_interrupt_mode Found MSI capability
Oct 31 02:08:58 miniub kernel: [   13.035744] Allocate Port Service[0000:00:02.0:pcie00]
Oct 31 02:08:58 miniub kernel: [   13.035800] PCI: Setting latency timer of device 0000:00:03.0 to 64
Oct 31 02:08:58 miniub kernel: [   13.035820] assign_interrupt_mode Found MSI capability
Oct 31 02:08:58 miniub kernel: [   13.035835] Allocate Port Service[0000:00:03.0:pcie00]
Oct 31 02:08:58 miniub kernel: [   13.036017] isapnp: Scanning for PnP cards...
Oct 31 02:08:58 miniub kernel: [   13.388858] isapnp: No Plug & Play device found
Oct 31 02:08:58 miniub kernel: [   13.416362] Real Time Clock Driver v1.12ac
Oct 31 02:08:58 miniub kernel: [   13.416550] hpet_resources: 0xfed00000 is busy
Oct 31 02:08:58 miniub kernel: [   13.416587] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 31 02:08:58 miniub kernel: [   13.417534] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 31 02:08:58 miniub kernel: [   13.417591] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Oct 31 02:08:58 miniub kernel: [   13.417669] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct 31 02:08:58 miniub kernel: [   13.417975] i8042.c: Detected active multiplexing controller, rev 1.1.
Oct 31 02:08:58 miniub kernel: [   13.418045] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 31 02:08:58 miniub kernel: [   13.418049] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Oct 31 02:08:58 miniub kernel: [   13.418052] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Oct 31 02:08:58 miniub kernel: [   13.418054] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Oct 31 02:08:58 miniub kernel: [   13.418057] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Oct 31 02:08:58 miniub kernel: [   13.427423] mice: PS/2 mouse device common for all mice
Oct 31 02:08:58 miniub kernel: [   13.427520] EISA: Probing bus 0 at eisa.0
Oct 31 02:08:58 miniub kernel: [   13.427525] Cannot allocate resource for EISA slot 1
Oct 31 02:08:58 miniub kernel: [   13.427528] Cannot allocate resource for EISA slot 2
Oct 31 02:08:58 miniub kernel: [   13.427530] Cannot allocate resource for EISA slot 3
Oct 31 02:08:58 miniub kernel: [   13.427532] Cannot allocate resource for EISA slot 4
Oct 31 02:08:58 miniub kernel: [   13.427545] EISA: Detected 0 cards.
Oct 31 02:08:58 miniub kernel: [   13.427547] cpuidle: using governor ladder
Oct 31 02:08:58 miniub kernel: [   13.427549] cpuidle: using governor menu
Oct 31 02:08:58 miniub kernel: [   13.427630] NET: Registered protocol family 1
Oct 31 02:08:58 miniub kernel: [   13.427653] Using IPI No-Shortcut mode
Oct 31 02:08:58 miniub kernel: [   13.427681] registered taskstats version 1
Oct 31 02:08:58 miniub kernel: [   13.427793]   Magic number: 12:627:107
Oct 31 02:08:58 miniub kernel: [   13.427991] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 31 02:08:58 miniub kernel: [   13.427993] EDD information not available.
Oct 31 02:08:58 miniub kernel: [   13.428240] Freeing unused kernel memory: 368k freed
Oct 31 02:08:58 miniub kernel: [   13.428263] Write protecting the kernel read-only data: 801k
Oct 31 02:08:58 miniub kernel: [   13.430931] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Oct 31 02:08:58 miniub kernel: [   13.594548] fuse init (API version 7.9)
Oct 31 02:08:58 miniub kernel: [   13.614747] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Oct 31 02:08:58 miniub kernel: [   13.614753] ACPI: Processor [CPU0] (supports 8 throttling states)
Oct 31 02:08:58 miniub kernel: [   13.614766] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
Oct 31 02:08:58 miniub kernel: [   13.636021] ACPI: Thermal Zone [TZS0] (62 C)
Oct 31 02:08:58 miniub kernel: [   13.644742] ACPI: Thermal Zone [TZS1] (65 C)
Oct 31 02:08:58 miniub kernel: [   14.475166] ACPI: PCI Interrupt Link [LK2E] enabled at IRQ 19
Oct 31 02:08:58 miniub kernel: [   14.475178] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LK2E] -> GSI 19 (level, high) -> IRQ 16
Oct 31 02:08:58 miniub kernel: [   14.475187] PCI: Setting latency timer of device 0000:01:00.0 to 64
Oct 31 02:08:58 miniub kernel: [   14.494752] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x13, vendor 0x4243)
Oct 31 02:08:58 miniub kernel: [   14.494760] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0D, vendor 0x4243)
Oct 31 02:08:58 miniub kernel: [   14.494767] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x04, vendor 0x4243)
Oct 31 02:08:58 miniub kernel: [   14.494772] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x05, vendor 0x4243)
Oct 31 02:08:58 miniub kernel: [   14.534768] ssb: Sonics Silicon Backplane found on PCI device 0000:01:00.0
Oct 31 02:08:58 miniub kernel: [   14.578777] usbcore: registered new interface driver usbfs
Oct 31 02:08:58 miniub kernel: [   14.578801] usbcore: registered new interface driver hub
Oct 31 02:08:58 miniub kernel: [   14.585648] usbcore: registered new device driver usb
Oct 31 02:08:58 miniub kernel: [   14.595383] SCSI subsystem initialized
Oct 31 02:08:58 miniub kernel: [   14.627034] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Oct 31 02:08:58 miniub kernel: [   14.627402] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 23
Oct 31 02:08:58 miniub kernel: [   14.627412] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 23 (level, high) -> IRQ 17
Oct 31 02:08:58 miniub kernel: [   14.627425] PCI: Setting latency timer of device 0000:00:0b.0 to 64
Oct 31 02:08:58 miniub kernel: [   14.627428] ohci_hcd 0000:00:0b.0: OHCI Host Controller
Oct 31 02:08:58 miniub kernel: [   14.627710] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
Oct 31 02:08:58 miniub kernel: [   14.627730] ohci_hcd 0000:00:0b.0: irq 17, io mem 0xb0004000
Oct 31 02:08:58 miniub kernel: [   14.659006] libata version 3.00 loaded.
Oct 31 02:08:58 miniub kernel: [   14.684769] usb usb1: configuration #1 chosen from 1 choice
Oct 31 02:08:58 miniub kernel: [   14.684794] hub 1-0:1.0: USB hub found
Oct 31 02:08:58 miniub kernel: [   14.684803] hub 1-0:1.0: 8 ports detected
Oct 31 02:08:58 miniub kernel: [   14.787109] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
Oct 31 02:08:58 miniub kernel: [   14.787122] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 22 (level, high) -> IRQ 18
Oct 31 02:08:58 miniub kernel: [   14.787133] PCI: Setting latency timer of device 0000:00:0b.1 to 64
Oct 31 02:08:58 miniub kernel: [   14.787136] ehci_hcd 0000:00:0b.1: EHCI Host Controller
Oct 31 02:08:58 miniub kernel: [   14.787167] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
Oct 31 02:08:58 miniub kernel: [   14.787198] ehci_hcd 0000:00:0b.1: debug port 1
Oct 31 02:08:58 miniub kernel: [   14.787202] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
Oct 31 02:08:58 miniub kernel: [   14.787212] ehci_hcd 0000:00:0b.1: irq 18, io mem 0xb0005000
Oct 31 02:08:58 miniub kernel: [   14.798566] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 31 02:08:58 miniub kernel: [   14.798682] usb usb2: configuration #1 chosen from 1 choice
Oct 31 02:08:58 miniub kernel: [   14.798703] hub 2-0:1.0: USB hub found
Oct 31 02:08:58 miniub kernel: [   14.798709] hub 2-0:1.0: 8 ports detected
Oct 31 02:08:58 miniub kernel: [   14.902681] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Oct 31 02:08:58 miniub kernel: [   14.903020] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 18
Oct 31 02:08:58 miniub kernel: [   14.903030] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 18 (level, high) -> IRQ 19
Oct 31 02:08:58 miniub kernel: [   14.903037] PCI: Setting latency timer of device 0000:00:14.0 to 64
Oct 31 02:08:58 miniub kernel: [   15.422657] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:16:d3:ae:e1:cb
Oct 31 02:08:58 miniub kernel: [   15.422662] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
Oct 31 02:08:58 miniub kernel: [   15.422976] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Oct 31 02:08:58 miniub kernel: [   15.423000] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
Oct 31 02:08:58 miniub kernel: [   15.423319] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 17
Oct 31 02:08:58 miniub kernel: [   15.423330] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 17 (level, high) -> IRQ 20
Oct 31 02:08:58 miniub kernel: [   15.423349] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Oct 31 02:08:58 miniub kernel: [   15.423357] ACPI: PCI interrupt for device 0000:00:0e.0 disabled
Oct 31 02:08:58 miniub kernel: [   15.425928] sata_nv 0000:00:0e.0: version 3.5
Oct 31 02:08:58 miniub kernel: [   15.425936] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 17 (level, high) -> IRQ 20
Oct 31 02:08:58 miniub kernel: [   15.425964] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Oct 31 02:08:58 miniub kernel: [   15.427065] scsi0 : sata_nv
Oct 31 02:08:58 miniub kernel: [   15.427571] scsi1 : sata_nv
Oct 31 02:08:58 miniub kernel: [   15.427737] ata1: SATA max UDMA/133 cmd 0x30b0 ctl 0x30a4 bmdma 0x3090 irq 20
Oct 31 02:08:58 miniub kernel: [   15.427740] ata2: SATA max UDMA/133 cmd 0x30a8 ctl 0x30a0 bmdma 0x3098 irq 20
Oct 31 02:08:58 miniub kernel: [   15.434231] usb 1-6: new low speed USB device using ohci_hcd and address 2
Oct 31 02:08:58 miniub kernel: [   15.648258] usb 1-6: configuration #1 chosen from 1 choice
Oct 31 02:08:58 miniub kernel: [   15.666703] usbcore: registered new interface driver hiddev
Oct 31 02:08:58 miniub kernel: [   15.672329] input: Genius NetScroll + Traveler as /devices/pci0000:00/0000:00:0b.0/usb1/1-6/1-6:1.0/input/input2
Oct 31 02:08:58 miniub kernel: [   15.682121] input,hidraw0: USB HID v1.10 Mouse [Genius NetScroll + Traveler] on usb-0000:00:0b.0-6
Oct 31 02:08:58 miniub kernel: [   15.682137] usbcore: registered new interface driver usbhid
Oct 31 02:08:58 miniub kernel: [   15.682141] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Oct 31 02:08:58 miniub kernel: [   15.893984] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct 31 02:08:58 miniub kernel: [   15.902153] ata1.00: ATA-7: WDC WD800BEVS-60RST0, 04.01G04, max UDMA/100
Oct 31 02:08:58 miniub kernel: [   15.902156] ata1.00: 156301488 sectors, multi 16: LBA48 
Oct 31 02:08:58 miniub kernel: [   15.910150] ata1.00: configured for UDMA/100
Oct 31 02:08:58 miniub kernel: [   16.221784] ata2: SATA link down (SStatus 0 SControl 300)
Oct 31 02:08:58 miniub kernel: [   16.232426] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BEVS-60 04.0 PQ: 0 ANSI: 5
Oct 31 02:08:58 miniub kernel: [   16.233996] pata_amd 0000:00:0d.0: version 0.3.10
Oct 31 02:08:58 miniub kernel: [   16.234041] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Oct 31 02:08:58 miniub kernel: [   16.237106] scsi2 : pata_amd
Oct 31 02:08:58 miniub kernel: [   16.238068] scsi3 : pata_amd
Oct 31 02:08:58 miniub kernel: [   16.238626] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
Oct 31 02:08:58 miniub kernel: [   16.238629] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
Oct 31 02:08:58 miniub kernel: [   16.721796] ata4.00: ATAPI: Optiarc CD-RW CRX880A, KH18, max MWDMA2
Oct 31 02:08:58 miniub kernel: [   16.893636] ata4.00: configured for MWDMA2
Oct 31 02:08:58 miniub kernel: [   16.894589] scsi 3:0:0:0: CD-ROM            Optiarc  CD-RW CRX880A    KH18 PQ: 0 ANSI: 5
Oct 31 02:08:58 miniub kernel: [   16.901899] Driver 'sd' needs updating - please use bus_type methods
Oct 31 02:08:58 miniub kernel: [   16.901980] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Oct 31 02:08:58 miniub kernel: [   16.901991] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 02:08:58 miniub kernel: [   16.901994] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 31 02:08:58 miniub kernel: [   16.902008] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 02:08:58 miniub kernel: [   16.902049] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Oct 31 02:08:58 miniub kernel: [   16.902056] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 02:08:58 miniub kernel: [   16.902059] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 31 02:08:58 miniub kernel: [   16.902071] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 02:08:58 miniub kernel: [   16.902074]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Oct 31 02:08:58 miniub kernel: [   16.949061]  sda1 sda2 sda3 < sda5 sda6 > sda4
Oct 31 02:08:58 miniub kernel: [   16.971718] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 31 02:08:58 miniub kernel: [   16.976899] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 31 02:08:58 miniub kernel: [   16.976917] sr 3:0:0:0: Attached scsi generic sg1 type 5
Oct 31 02:08:58 miniub kernel: [   16.981794] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Oct 31 02:08:58 miniub kernel: [   16.981800] Uniform CD-ROM driver Revision: 3.20
Oct 31 02:08:58 miniub kernel: [   16.981848] sr 3:0:0:0: Attached scsi CD-ROM sr0
Oct 31 02:08:58 miniub kernel: [   17.513817] Attempting manual resume
Oct 31 02:08:58 miniub kernel: [   17.513821] swsusp: Resume From Partition 8:5
Oct 31 02:08:58 miniub kernel: [   17.513823] PM: Checking swsusp image.
Oct 31 02:08:58 miniub kernel: [   17.514085] PM: Resume from disk failed.
Oct 31 02:08:58 miniub kernel: [   17.529063] EXT3-fs: INFO: recovery required on readonly filesystem.
Oct 31 02:08:58 miniub kernel: [   17.529067] EXT3-fs: write access will be enabled during recovery.
Oct 31 02:08:58 miniub kernel: [   20.094073] kjournald starting.  Commit interval 5 seconds
Oct 31 02:08:58 miniub kernel: [   20.094089] EXT3-fs: sda6: orphan cleanup on readonly fs
Oct 31 02:08:58 miniub kernel: [   20.094095] ext3_orphan_cleanup: deleting unreferenced inode 677361
Oct 31 02:08:58 miniub kernel: [   20.094132] ext3_orphan_cleanup: deleting unreferenced inode 65299
Oct 31 02:08:58 miniub kernel: [   20.094137] EXT3-fs: sda6: 2 orphan inodes deleted
Oct 31 02:08:58 miniub kernel: [   20.094139] EXT3-fs: recovery complete.
Oct 31 02:08:58 miniub kernel: [   20.100698] EXT3-fs: mounted filesystem with ordered data mode.
Oct 31 02:08:58 miniub kernel: [   26.930201] input: PC Speaker as /devices/platform/pcspkr/input/input3
Oct 31 02:08:58 miniub kernel: [   27.503437] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 31 02:08:58 miniub kernel: [   27.559433] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 31 02:08:58 miniub kernel: [   27.583360] Linux agpgart interface v0.102
Oct 31 02:08:58 miniub kernel: [   27.635431] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
Oct 31 02:08:58 miniub kernel: [   27.635446] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
Oct 31 02:08:58 miniub kernel: [   27.764521] input: Power Button (FF) as /devices/virtual/input/input4
Oct 31 02:08:58 miniub kernel: [   27.795285] ACPI: Power Button (FF) [PWRF]
Oct 31 02:08:58 miniub kernel: [   27.795354] input: Sleep Button (CM) as /devices/virtual/input/input5
Oct 31 02:08:58 miniub kernel: [   27.823243] ACPI: Sleep Button (CM) [SLPB]
Oct 31 02:08:58 miniub kernel: [   27.823299] input: Power Button (CM) as /devices/virtual/input/input6
Oct 31 02:08:58 miniub kernel: [   27.855217] ACPI: Power Button (CM) [PWRB]
Oct 31 02:08:58 miniub kernel: [   27.950221] nvidia: module license 'NVIDIA' taints kernel.
Oct 31 02:08:58 miniub kernel: [   28.465648] ACPI: WMI-Acer: Mapper loaded
Oct 31 02:08:58 miniub kernel: [   29.059250] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input7
Oct 31 02:08:58 miniub kernel: [   29.086529] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Oct 31 02:08:58 miniub kernel: [   29.336498] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
Oct 31 02:08:58 miniub kernel: [   29.365806] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
Oct 31 02:08:58 miniub kernel: [   30.017322] eth0: no link during initialization.
Oct 31 02:08:58 miniub kernel: [   30.545873] ieee80211_crypt: registered algorithm 'NULL'
Oct 31 02:08:58 miniub kernel: [   30.760167] ACPI: AC Adapter [ADP1] (on-line)
Oct 31 02:08:58 miniub kernel: [   30.788778] ACPI: Battery Slot [BAT0] (battery absent)
Oct 31 02:08:58 miniub kernel: [   30.809913] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 21
Oct 31 02:08:58 miniub kernel: [   30.809925] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LK3E] -> GSI 21 (level, high) -> IRQ 21
Oct 31 02:08:58 miniub kernel: [   30.809933] PCI: Setting latency timer of device 0000:00:05.0 to 64
Oct 31 02:08:58 miniub kernel: [   30.810157] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
Oct 31 02:08:58 miniub kernel: [   30.816463] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 16
Oct 31 02:08:58 miniub kernel: [   30.816474] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 16 (level, high) -> IRQ 22
Oct 31 02:08:58 miniub kernel: [   30.816499] PCI: Setting latency timer of device 0000:00:10.1 to 64
Oct 31 02:08:58 miniub kernel: [   31.685628] NET: Registered protocol family 17
Oct 31 02:08:58 miniub kernel: [   32.299498] loop: module loaded
Oct 31 02:08:58 miniub kernel: [   32.376932] lp: driver loaded but no devices found
Oct 31 02:08:58 miniub kernel: [   32.710429] Adding 1172704k swap on /dev/sda5.  Priority:-1 extents:1 across:1172704k
Oct 31 02:08:58 miniub kernel: [   33.031759] EXT3 FS on sda6, internal journal
Oct 31 02:08:58 miniub kernel: [   34.149899] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 31 02:08:58 miniub kernel: [   35.011958] No dock devices found.
Oct 31 02:08:59 miniub NetworkManager: <info>  starting... 
Oct 31 02:08:59 miniub avahi-daemon[4769]: Found user 'avahi' (UID 105) and group 'avahi' (GID 115).
Oct 31 02:08:59 miniub avahi-daemon[4769]: Successfully dropped root privileges.
Oct 31 02:08:59 miniub avahi-daemon[4769]: avahi-daemon 0.6.22 starting up.
Oct 31 02:08:59 miniub avahi-daemon[4769]: Successfully called chroot().
Oct 31 02:08:59 miniub avahi-daemon[4769]: Successfully dropped remaining capabilities.
Oct 31 02:08:59 miniub avahi-daemon[4769]: No service file found in /etc/avahi/services.
Oct 31 02:08:59 miniub avahi-daemon[4769]: Network interface enumeration completed.
Oct 31 02:08:59 miniub avahi-daemon[4769]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 31 02:08:59 miniub avahi-daemon[4769]: Server startup complete. Host name is miniub.local. Local service cookie is 3553046126.
Oct 31 02:08:59 miniub kernel: [   36.440832] ppdev: user-space parallel port driver
Oct 31 02:08:59 miniub kernel: [   36.969280] audit(1225426139.917:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4796 profile="/usr/sbin/cupsd" namespace="default"
Oct 31 02:09:00 miniub dhcdbd: Started up.
Oct 31 02:09:01 miniub NetworkManager: <debug> [1225426141.682642] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CD_RW_CRX880A'). 
Oct 31 02:09:01 miniub /usr/sbin/cron[4994]: (CRON) INFO (pidfile fd = 3)
Oct 31 02:09:01 miniub /usr/sbin/cron[4995]: (CRON) STARTUP (fork ok)
Oct 31 02:09:01 miniub /usr/sbin/cron[4995]: (CRON) INFO (Running @reboot jobs)
Oct 31 02:09:05 miniub dhclient: DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
Oct 31 02:09:09 miniub kernel: [   46.566044] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
Oct 31 02:09:09 miniub kernel: [   46.566050] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
Oct 31 02:09:09 miniub kernel: [   46.566704] atkbd.c: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
Oct 31 02:09:09 miniub kernel: [   46.566708] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
Oct 31 02:09:16 miniub dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct 31 02:09:17 miniub kernel: [   54.152979] NET: Registered protocol family 10
Oct 31 02:09:17 miniub kernel: [   54.153176] lo: Disabled Privacy Extensions
Oct 31 02:09:17 miniub kernel: [   54.153608] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 31 02:09:19 miniub dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Oct 31 02:09:26 miniub dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Oct 31 02:09:26 miniub NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 31 02:09:41 miniub dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Oct 31 02:09:58 miniub dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Oct 31 02:10:10 miniub dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Oct 31 02:10:14 miniub kernel: [  111.971372] ACPI: PCI interrupt for device 0000:01:00.0 disabled
Oct 31 02:10:14 miniub NetworkManager: <debug> [1225426214.968236] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Oct 31 02:10:14 miniub NetworkManager: <debug> [1225426214.972362] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Oct 31 02:10:17 miniub dhclient: No DHCPOFFERS received.
Oct 31 02:10:17 miniub dhclient: Trying recorded lease 192.168.1.101
Oct 31 02:10:17 miniub avahi-daemon[4769]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
Oct 31 02:10:17 miniub avahi-daemon[4769]: New relevant interface eth0.IPv4 for mDNS.
Oct 31 02:10:17 miniub avahi-daemon[4769]: Registering new address record for 192.168.1.101 on eth0.IPv4.
Oct 31 02:10:20 miniub avahi-daemon[4769]: Withdrawing address record for 192.168.1.101 on eth0.
Oct 31 02:10:20 miniub avahi-daemon[4769]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
Oct 31 02:10:20 miniub avahi-daemon[4769]: Interface eth0.IPv4 no longer relevant for mDNS.
Oct 31 02:10:20 miniub dhclient: No working leases in persistent database - sleeping.
Oct 31 02:10:20 miniub ntpdate[5487]: can't find host ntp.ubuntu.com 
Oct 31 02:10:20 miniub ntpdate[5487]: no servers can be used, exiting
Oct 31 02:10:37 miniub kernel: [  134.110107] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LK2E] -> GSI 19 (level, high) -> IRQ 16
Oct 31 02:10:37 miniub kernel: [  134.110119] PCI: Setting latency timer of device 0000:01:00.0 to 64
Oct 31 02:10:37 miniub NetworkManager: <debug> [1225426237.134534] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_1a_73_95_a1_ea'). 
Oct 31 02:10:37 miniub kernel: [  134.295641] ieee80211_crypt: registered algorithm 'TKIP'
Oct 31 02:10:37 miniub kernel: [  134.295970] eth1: Broadcom BCM4311 802.11 Wireless Controller 5.10.27.6
Oct 31 02:10:37 miniub NetworkManager: <info>  eth1: Device is fully-supported using driver 'wl'. 
Oct 31 02:10:37 miniub NetworkManager: <info>  eth1: driver does not support SSID scans (scan_capa 0x00). 
Oct 31 02:10:37 miniub NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 31 02:10:37 miniub NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 31 02:10:37 miniub NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 31 02:10:37 miniub NetworkManager: <info>  Deactivating device eth1. 
Oct 31 02:10:37 miniub NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Invalid argument 
Oct 31 02:10:47 miniub NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 31 02:10:47 miniub dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 31 02:10:47 miniub NetworkManager: <info>  Will activate connection 'eth1/WiFi'. 
Oct 31 02:10:47 miniub NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 31 02:10:47 miniub NetworkManager: <info>  Activation (eth1) started... 
Oct 31 02:10:47 miniub NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 31 02:10:47 miniub NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 31 02:10:47 miniub NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 31 02:10:47 miniub NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 31 02:10:47 miniub NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 31 02:10:47 miniub NetworkManager: <info>  Activation (eth1/wireless): access point 'WiFi' is unencrypted, no key needed. 
Oct 31 02:10:49 miniub NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Oct 31 02:10:49 miniub NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Oct 31 02:10:49 miniub kernel: [  146.453092] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Oct 31 02:10:49 miniub NetworkManager: <info>  SUP: response was 'OK' 
Oct 31 02:10:49 miniub NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 31 02:10:49 miniub NetworkManager: <info>  SUP: response was 'OK' 
Oct 31 02:10:49 miniub NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 31 02:10:49 miniub NetworkManager: <info>  SUP: response was '0' 
Oct 31 02:10:49 miniub NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 57694669' 
Oct 31 02:10:49 miniub NetworkManager: <info>  SUP: response was 'OK' 
Oct 31 02:10:49 miniub NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 31 02:10:49 miniub NetworkManager: <info>  SUP: response was 'OK' 
Oct 31 02:10:49 miniub NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 31 02:10:49 miniub NetworkManager: <info>  SUP: response was 'OK' 
Oct 31 02:10:49 miniub NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 31 02:10:50 miniub NetworkManager: <info>  Supplicant state changed: 1 
Oct 31 02:10:50 miniub NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'WiFi'. 
Oct 31 02:10:50 miniub NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 31 02:10:50 miniub NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 31 02:10:51 miniub avahi-daemon[4769]: Registering new address record for fe80::21a:73ff:fe95:a1ea on eth1.*.
Oct 31 02:10:51 miniub NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 31 02:10:51 miniub NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 31 02:10:51 miniub NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 31 02:10:51 miniub dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 31 02:10:51 miniub NetworkManager: <debug> [1225426251.656892] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'WiFi' 
Oct 31 02:10:51 miniub NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / WiFi 
Oct 31 02:10:51 miniub NetworkManager: <info>  Deactivating device eth1. 
Oct 31 02:10:51 miniub NetworkManager: <info>  Activation (eth1): cancelling... 
Oct 31 02:10:51 miniub NetworkManager: <info>  Activation (eth1) cancellation handler scheduled... 
Oct 31 02:10:51 miniub NetworkManager: <info>  Activation (eth1): waiting for device to cancel activation. 
Oct 31 02:10:51 miniub dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Oct 31 02:10:51 miniub dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Oct 31 02:10:51 miniub dhclient: send_packet: Network is unreachable
Oct 31 02:10:51 miniub dhclient: send_packet: please consult README file regarding broadcast address.
Oct 31 02:10:52 miniub NetworkManager: <info>  Activation (eth1) cancellation handled. 
Oct 31 02:10:52 miniub NetworkManager: <info>  Activation (eth1): cancelled. 
Oct 31 02:10:52 miniub avahi-daemon[4769]: Withdrawing address record for fe80::21a:73ff:fe95:a1ea on eth1.
Oct 31 02:10:52 miniub NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Invalid argument 
Oct 31 02:10:52 miniub NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 31 02:10:52 miniub NetworkManager: <info>  Activation (eth1) started... 
Oct 31 02:10:52 miniub NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 31 02:10:52 miniub NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 31 02:10:52 miniub NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 31 02:10:52 miniub NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 31 02:10:52 miniub NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 31 02:10:52 miniub NetworkManager: <info>  Activation (eth1/wireless): access point 'WiFi' is unencrypted, no key needed. 
Oct 31 02:10:54 miniub dhclient: DHCPREQUEST of 192.168.1.100 on eth1 to 255.255.255.255 port 67
Oct 31 02:10:54 miniub dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
Oct 31 02:10:54 miniub avahi-daemon[4769]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Oct 31 02:10:54 miniub avahi-daemon[4769]: New relevant interface eth1.IPv4 for mDNS.
Oct 31 02:10:54 miniub avahi-daemon[4769]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Oct 31 02:10:54 miniub NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth1 
Oct 31 02:10:54 miniub dhclient: bound to 192.168.1.100 -- renewal in 42474 seconds.
Oct 31 02:10:54 miniub NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Oct 31 02:10:54 miniub NetworkManager: <info>  SUP: response was 'OK' 
Oct 31 02:10:54 miniub NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 31 02:10:54 miniub NetworkManager: <info>  SUP: response was 'OK' 
Oct 31 02:10:54 miniub NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 31 02:10:54 miniub NetworkManager: <info>  SUP: response was '0' 
Oct 31 02:10:54 miniub NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 57694669' 
Oct 31 02:10:54 miniub NetworkManager: <info>  SUP: response was 'OK' 
Oct 31 02:10:54 miniub NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 31 02:10:54 miniub NetworkManager: <info>  SUP: response was 'OK' 
Oct 31 02:10:54 miniub NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 31 02:10:54 miniub NetworkManager: <info>  SUP: response was 'OK' 
Oct 31 02:10:54 miniub NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 31 02:10:54 miniub kernel: [  151.714924] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Oct 31 02:10:54 miniub NetworkManager: <info>  Supplicant state changed: 1 
Oct 31 02:10:54 miniub NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'WiFi'. 
Oct 31 02:10:54 miniub NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 31 02:10:54 miniub NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 31 02:10:55 miniub avahi-daemon[4769]: Registering new address record for fe80::21a:73ff:fe95:a1ea on eth1.*.
Oct 31 02:10:56 miniub NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 31 02:10:56 miniub dhclient: Corrupt lease file - possible data loss!
Oct 31 02:10:56 miniub NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 31 02:10:56 miniub NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 31 02:10:56 miniub avahi-daemon[4769]: Withdrawing address record for 192.168.1.100 on eth1.
Oct 31 02:10:56 miniub avahi-daemon[4769]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Oct 31 02:10:56 miniub avahi-daemon[4769]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 31 02:10:57 miniub NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 31 02:10:59 miniub dhclient: DHCPREQUEST of 192.168.1.100 on eth1 to 255.255.255.255 port 67
Oct 31 02:10:59 miniub dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
Oct 31 02:10:59 miniub avahi-daemon[4769]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Oct 31 02:10:59 miniub avahi-daemon[4769]: New relevant interface eth1.IPv4 for mDNS.
Oct 31 02:10:59 miniub avahi-daemon[4769]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Oct 31 02:10:59 miniub NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth1 
Oct 31 02:10:59 miniub NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 31 02:10:59 miniub NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 31 02:10:59 miniub dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 31 02:10:59 miniub dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
Oct 31 02:10:59 miniub dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 31 02:10:59 miniub dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 31 02:10:59 miniub NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 31 02:10:59 miniub NetworkManager: <info>    address 192.168.1.100 
Oct 31 02:10:59 miniub NetworkManager: <info>    netmask 255.255.255.0 
Oct 31 02:10:59 miniub NetworkManager: <info>    broadcast 192.168.1.255 
Oct 31 02:10:59 miniub NetworkManager: <info>    gateway 192.168.1.1 
Oct 31 02:10:59 miniub NetworkManager: <info>    nameserver 200.42.0.111 
Oct 31 02:10:59 miniub NetworkManager: <info>    nameserver 200.42.97.111 
Oct 31 02:10:59 miniub NetworkManager: <info>    nameserver 200.42.97.110 
Oct 31 02:10:59 miniub dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Oct 31 02:10:59 miniub NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 31 02:10:59 miniub NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 31 02:10:59 miniub NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 31 02:10:59 miniub dhclient: bound to 192.168.1.100 -- renewal in 34534 seconds.
Oct 31 02:10:59 miniub avahi-daemon[4769]: Withdrawing address record for 192.168.1.100 on eth1.
Oct 31 02:10:59 miniub avahi-daemon[4769]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Oct 31 02:10:59 miniub avahi-daemon[4769]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 31 02:10:59 miniub avahi-daemon[4769]: Withdrawing address record for fe80::21a:73ff:fe95:a1ea on eth1.
Oct 31 02:10:59 miniub avahi-daemon[4769]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Oct 31 02:10:59 miniub avahi-daemon[4769]: New relevant interface eth1.IPv4 for mDNS.
Oct 31 02:10:59 miniub avahi-daemon[4769]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Oct 31 02:11:00 miniub NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 31 02:11:00 miniub NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 31 02:11:00 miniub NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 31 02:11:00 miniub NetworkManager: <debug> [1225426260.095597] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'WiFi' 
Oct 31 02:11:00 miniub NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 31 02:11:00 miniub NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 31 02:11:01 miniub ntpdate[5654]: step time server 91.189.94.4 offset 0.987597 sec
Oct 31 02:11:02 miniub avahi-daemon[4769]: Registering new address record for fe80::21a:73ff:fe95:a1ea on eth1.*.
Oct 31 02:11:02 miniub NetworkManager: <info>  Supplicant state changed: 1 
Oct 31 02:11:11 miniub kernel: [  167.692249] eth1: no IPv6 routers present
Oct 31 02:14:57 miniub syslogd 1.5.0#1ubuntu1: restart.

```

this is the next```

Oct 31 02:14:57 miniub syslogd 1.5.0#1ubuntu1: restart.
Oct 31 02:14:57 miniub kernel: Inspecting /boot/System.map-2.6.24-21-generic
Oct 31 02:14:57 miniub kernel: Loaded 27897 symbols from /boot/System.map-2.6.24-21-generic.
Oct 31 02:14:57 miniub kernel: Symbols match kernel version 2.6.24.
Oct 31 02:14:57 miniub kernel: Loaded 33200 symbols from 77 modules.
Oct 31 02:14:57 miniub kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 31 02:14:57 miniub kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 31 02:14:57 miniub kernel: [    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:43:45 UTC 2008 (Ubuntu 2.6.24-21.43-generic)
Oct 31 02:14:57 miniub kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 31 02:14:57 miniub kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Oct 31 02:14:57 miniub kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Oct 31 02:14:57 miniub kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
Oct 31 02:14:57 miniub kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000057f10000 (usable)
Oct 31 02:14:57 miniub kernel: [    0.000000]  BIOS-e820: 0000000057f10000 - 0000000057f17000 (ACPI data)
Oct 31 02:14:57 miniub kernel: [    0.000000]  BIOS-e820: 0000000057f17000 - 0000000057f80000 (ACPI NVS)
Oct 31 02:14:57 miniub kernel: [    0.000000]  BIOS-e820: 0000000057f80000 - 0000000060000000 (reserved)
Oct 31 02:14:57 miniub kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Oct 31 02:14:57 miniub kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Oct 31 02:14:57 miniub kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Oct 31 02:14:57 miniub kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 31 02:14:57 miniub kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Oct 31 02:14:57 miniub kernel: [    0.000000] 511MB HIGHMEM available.
Oct 31 02:14:57 miniub kernel: [    0.000000] 896MB LOWMEM available.
Oct 31 02:14:57 miniub kernel: [    0.000000] found SMP MP-table at 000f8780
Oct 31 02:14:57 miniub kernel: [    0.000000] Entering add_active_range(0, 0, 360208) 0 entries of 256 used
Oct 31 02:14:57 miniub kernel: [    0.000000] Zone PFN ranges:
Oct 31 02:14:57 miniub kernel: [    0.000000]   DMA             0 ->     4096
Oct 31 02:14:57 miniub kernel: [    0.000000]   Normal       4096 ->   229376
Oct 31 02:14:57 miniub kernel: [    0.000000]   HighMem    229376 ->   360208
Oct 31 02:14:57 miniub kernel: [    0.000000] Movable zone start PFN for each node
Oct 31 02:14:57 miniub kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 31 02:14:57 miniub kernel: [    0.000000]     0:        0 ->   360208
Oct 31 02:14:57 miniub kernel: [    0.000000] On node 0 totalpages: 360208
Oct 31 02:14:57 miniub kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Oct 31 02:14:57 miniub kernel: [    0.000000]   DMA zone: 0 pages reserved
Oct 31 02:14:57 miniub kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Oct 31 02:14:57 miniub kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Oct 31 02:14:57 miniub kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Oct 31 02:14:57 miniub kernel: [    0.000000]   HighMem zone: 1022 pages used for memmap
Oct 31 02:14:57 miniub kernel: [    0.000000]   HighMem zone: 129810 pages, LIFO batch:31
Oct 31 02:14:57 miniub kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Oct 31 02:14:57 miniub kernel: [    0.000000] DMI present.
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F87B0 checksum 0
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: RSDP 000F87B0, 0024 (r3 HPQOEM)
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: XSDT 57F100CE, 005C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: FACP 57F16B42, 00F4 (r3 HPQOEM SLIC-MPC  6040000 PTL     F4240)
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: DSDT 57F1012A, 6A18 (r1 HPQOEM SLIC-MPC  6040000 MSFT  100000E)
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: FACS 57F17FC0, 0040
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: SLIC 57F16CAA, 0176 (r1 HPQOEM SLIC-MPC  6040000 HPQ         1)
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: MCFG 57F16E20, 003C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: HPET 57F16E5C, 0038 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: APIC 57F16E94, 0050 (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: BOOT 57F16EE4, 0028 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: SSDT 57F16F0C, 00F4 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: DMI detected: Hewlett-Packard
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct 31 02:14:57 miniub kernel: [    0.000000] Processor #0 15:12 APIC version 16
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Oct 31 02:14:57 miniub kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 31 02:14:57 miniub kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 31 02:14:57 miniub kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
Oct 31 02:14:57 miniub kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 31 02:14:57 miniub kernel: [    0.000000] Allocating PCI resources starting at 68000000 (gap: 60000000:80000000)
Oct 31 02:14:57 miniub kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
Oct 31 02:14:57 miniub kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
Oct 31 02:14:57 miniub kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
Oct 31 02:14:57 miniub kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
Oct 31 02:14:57 miniub kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 357394
Oct 31 02:14:57 miniub kernel: [    0.000000] Kernel command line: root=UUID=9c41d09f-5864-470d-a350-acfda4da607a ro quiet splash
Oct 31 02:14:57 miniub kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Oct 31 02:14:57 miniub kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Oct 31 02:14:57 miniub kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 31 02:14:57 miniub kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 31 02:14:57 miniub kernel: [    0.000000] Initializing CPU#0
Oct 31 02:14:57 miniub kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 31 02:14:57 miniub kernel: [    0.000000] Detected 1808.260 MHz processor.
Oct 31 02:14:57 miniub kernel: [   10.195194] spurious 8259A interrupt: IRQ7.
Oct 31 02:14:57 miniub kernel: [   10.198299] Console: colour VGA+ 80x25
Oct 31 02:14:57 miniub kernel: [   10.198302] console [tty0] enabled
Oct 31 02:14:57 miniub kernel: [   10.198726] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 31 02:14:57 miniub kernel: [   10.199162] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 31 02:14:57 miniub kernel: [   10.249091] Memory: 1416224k/1440832k available (2177k kernel code, 23352k reserved, 1005k data, 368k init, 523328k highmem)
Oct 31 02:14:57 miniub kernel: [   10.249100] virtual kernel memory layout:
Oct 31 02:14:57 miniub kernel: [   10.249101]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Oct 31 02:14:57 miniub kernel: [   10.249102]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 31 02:14:57 miniub kernel: [   10.249103]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Oct 31 02:14:57 miniub kernel: [   10.249104]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Oct 31 02:14:57 miniub kernel: [   10.249106]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Oct 31 02:14:57 miniub kernel: [   10.249107]       .data : 0xc03205e4 - 0xc041bdc4   (1005 kB)
Oct 31 02:14:57 miniub kernel: [   10.249108]       .text : 0xc0100000 - 0xc03205e4   (2177 kB)
Oct 31 02:14:57 miniub kernel: [   10.249111] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 31 02:14:57 miniub kernel: [   10.249151] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Oct 31 02:14:57 miniub kernel: [   10.249301] hpet clockevent registered
Oct 31 02:14:57 miniub kernel: [   10.329261] Calibrating delay using timer specific routine.. 3619.77 BogoMIPS (lpj=7239541)
Oct 31 02:14:57 miniub kernel: [   10.329284] Security Framework initialized
Oct 31 02:14:57 miniub kernel: [   10.329291] SELinux:  Disabled at boot.
Oct 31 02:14:57 miniub kernel: [   10.329307] AppArmor: AppArmor initialized
Oct 31 02:14:57 miniub kernel: [   10.329311] Failure registering capabilities with primary security module.
Oct 31 02:14:57 miniub kernel: [   10.329319] Mount-cache hash table entries: 512
Oct 31 02:14:57 miniub kernel: [   10.329437] Initializing cgroup subsys ns
Oct 31 02:14:57 miniub kernel: [   10.329440] Initializing cgroup subsys cpuacct
Oct 31 02:14:57 miniub kernel: [   10.329451] CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 00000019 00000000
Oct 31 02:14:57 miniub kernel: [   10.329460] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Oct 31 02:14:57 miniub kernel: [   10.329462] CPU: L2 Cache: 512K (64 bytes/line)
Oct 31 02:14:57 miniub kernel: [   10.329465] CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00020410 00002001 00000000 00000019 00000000
Oct 31 02:14:57 miniub kernel: [   10.329475] Compat vDSO mapped to ffffe000.
Oct 31 02:14:57 miniub kernel: [   10.329487] Checking 'hlt' instruction... OK.
Oct 31 02:14:57 miniub kernel: [   10.345569] SMP alternatives: switching to UP code
Oct 31 02:14:57 miniub kernel: [   10.346740] Freeing SMP alternatives: 11k freed
Oct 31 02:14:57 miniub kernel: [   10.346854] Early unpacking initramfs... done
Oct 31 02:14:57 miniub kernel: [   10.653001] ACPI: Core revision 20070126
Oct 31 02:14:57 miniub kernel: [   10.653077] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 31 02:14:57 miniub kernel: [   10.663705] CPU0: AMD Mobile AMD Sempron(tm) stepping 02
Oct 31 02:14:57 miniub kernel: [   10.663718] Total of 1 processors activated (3619.77 BogoMIPS).
Oct 31 02:14:57 miniub kernel: [   10.664018] ENABLING IO-APIC IRQs
Oct 31 02:14:57 miniub kernel: [   10.664250] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 31 02:14:57 miniub kernel: [   10.809053] Brought up 1 CPUs
Oct 31 02:14:57 miniub kernel: [   10.809100] CPU0 attaching sched-domain:
Oct 31 02:14:57 miniub kernel: [   10.809103]  domain 0: span 01
Oct 31 02:14:57 miniub kernel: [   10.809105]   groups: 01
Oct 31 02:14:57 miniub kernel: [   10.809255] net_namespace: 64 bytes
Oct 31 02:14:57 miniub kernel: [   10.809263] Booting paravirtualized kernel on bare hardware
Oct 31 02:14:57 miniub kernel: [   10.809710] Time:  2:14:36  Date: 10/31/08
Oct 31 02:14:57 miniub kernel: [   10.809731] NET: Registered protocol family 16
Oct 31 02:14:57 miniub kernel: [   10.809892] EISA bus registered
Oct 31 02:14:57 miniub kernel: [   10.809896] ACPI: bus type pci registered
Oct 31 02:14:57 miniub kernel: [   10.821930] PCI: BIOS BUG #81[49435000] found
Oct 31 02:14:57 miniub kernel: [   10.821974] PCI: Using configuration type 1
Oct 31 02:14:57 miniub kernel: [   10.821982] Setting up standard PCI resources
Oct 31 02:14:57 miniub kernel: [   10.823683] ACPI: EC: Look up EC in DSDT
Oct 31 02:14:57 miniub kernel: [   10.827727] ACPI: BIOS _OSI(Linux) query ignored via DMI
Oct 31 02:14:57 miniub kernel: [   10.828010] ACPI: Interpreter enabled
Oct 31 02:14:57 miniub kernel: [   10.828012] ACPI: (supports S0 S3 S4 S5)
Oct 31 02:14:57 miniub kernel: [   10.828024] ACPI: Using IOAPIC for interrupt routing
Oct 31 02:14:57 miniub kernel: [   10.828429] ACPI: EC: non-query interrupt received, switching to interrupt mode
Oct 31 02:14:57 miniub kernel: [   10.855227] ACPI: EC: GPE = 0x1, I/O: command/status = 0x66, data = 0x62
Oct 31 02:14:57 miniub kernel: [   10.855230] ACPI: EC: driver started in interrupt mode
Oct 31 02:14:57 miniub kernel: [   10.855270] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 31 02:14:57 miniub kernel: [   10.856269] PCI: Transparent bridge - 0000:00:10.0
Oct 31 02:14:57 miniub kernel: [   10.856284] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct 31 02:14:57 miniub kernel: [   10.856373] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
Oct 31 02:14:57 miniub kernel: [   10.856409] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
Oct 31 02:14:57 miniub kernel: [   10.856435] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
Oct 31 02:14:57 miniub kernel: [   10.990888] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 17 18 22 23) *0, disabled.
Oct 31 02:14:57 miniub kernel: [   10.991077] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 17 18 22 23) *10
Oct 31 02:14:57 miniub kernel: [   10.991262] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
Oct 31 02:14:57 miniub kernel: [   10.991448] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
Oct 31 02:14:57 miniub kernel: [   10.991633] ACPI: PCI Interrupt Link [LK1E] (IRQs 20) *0, disabled.
Oct 31 02:14:57 miniub kernel: [   10.991816] ACPI: PCI Interrupt Link [LK2E] (IRQs 19) *10
Oct 31 02:14:57 miniub kernel: [   10.992000] ACPI: PCI Interrupt Link [LK3E] (IRQs 21) *10
Oct 31 02:14:57 miniub kernel: [   10.992183] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 18 22 23) *0, disabled.
Oct 31 02:14:57 miniub kernel: [   10.992368] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 22 23) *10
Oct 31 02:14:57 miniub kernel: [   10.992559] ACPI: PCI Interrupt Link [LSMU] (IRQs 16 17 18 22 23) *11
Oct 31 02:14:57 miniub kernel: [   10.992743] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 22 23) *11
Oct 31 02:14:57 miniub kernel: [   10.992932] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 22 23) *7
Oct 31 02:14:57 miniub kernel: [   10.993118] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 22 23) *11
Oct 31 02:14:57 miniub kernel: [   10.993308] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 22 23) *0, disabled.
Oct 31 02:14:57 miniub kernel: [   10.993493] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 18 22 23) *0, disabled.
Oct 31 02:14:57 miniub kernel: [   10.993678] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 18 22 23) *0, disabled.
Oct 31 02:14:57 miniub kernel: [   10.993864] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 22 23) *0, disabled.
Oct 31 02:14:57 miniub kernel: [   10.994055] ACPI: PCI Interrupt Link [LTID] (IRQs 16 17 18 22 23) *5
Oct 31 02:14:57 miniub kernel: [   10.994246] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 22 23) *0
Oct 31 02:14:57 miniub kernel: [   10.994358] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 31 02:14:57 miniub kernel: [   10.994383] pnp: PnP ACPI init
Oct 31 02:14:57 miniub kernel: [   10.994389] ACPI: bus type pnp registered
Oct 31 02:14:57 miniub kernel: [   10.998039] pnp: PnP ACPI: found 11 devices
Oct 31 02:14:57 miniub kernel: [   10.998042] ACPI: ACPI bus type pnp unregistered
Oct 31 02:14:57 miniub kernel: [   10.998045] PnPBIOS: Disabled by ACPI PNP
Oct 31 02:14:57 miniub kernel: [   10.998231] PCI: Using ACPI for IRQ routing
Oct 31 02:14:57 miniub kernel: [   10.998235] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 31 02:14:57 miniub kernel: [   11.008922] NET: Registered protocol family 8
Oct 31 02:14:57 miniub kernel: [   11.008925] NET: Registered protocol family 20
Oct 31 02:14:57 miniub kernel: [   11.008955] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
Oct 31 02:14:57 miniub kernel: [   11.008959] hpet0: 3 32-bit timers, 25000000 Hz
Oct 31 02:14:57 miniub kernel: [   11.010002] AppArmor: AppArmor Filesystem Enabled
Oct 31 02:14:57 miniub kernel: [   11.012897] Time: tsc clocksource has been installed.
Oct 31 02:14:57 miniub kernel: [   11.012909] Switched to high resolution mode on CPU 0
Oct 31 02:14:57 miniub kernel: [   11.020886] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
Oct 31 02:14:57 miniub kernel: [   11.020891] system 00:02: ioport range 0x1000-0x107f has been reserved
Oct 31 02:14:57 miniub kernel: [   11.020894] system 00:02: ioport range 0x1080-0x10ff has been reserved
Oct 31 02:14:57 miniub kernel: [   11.020897] system 00:02: ioport range 0x1400-0x147f has been reserved
Oct 31 02:14:57 miniub kernel: [   11.020900] system 00:02: ioport range 0x1480-0x14ff has been reserved
Oct 31 02:14:57 miniub kernel: [   11.020902] system 00:02: ioport range 0x1800-0x187f has been reserved
Oct 31 02:14:57 miniub kernel: [   11.020905] system 00:02: ioport range 0x1880-0x18ff has been reserved
Oct 31 02:14:57 miniub kernel: [   11.020908] system 00:02: ioport range 0x2000-0x203f has been reserved
Oct 31 02:14:57 miniub kernel: [   11.020913] system 00:03: ioport range 0x360-0x361 has been reserved
Oct 31 02:14:57 miniub kernel: [   11.020916] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
Oct 31 02:14:57 miniub kernel: [   11.051247] PCI: Bridge: 0000:00:02.0
Oct 31 02:14:57 miniub kernel: [   11.051249]   IO window: disabled.
Oct 31 02:14:57 miniub kernel: [   11.051252]   MEM window: b3000000-b30fffff
Oct 31 02:14:57 miniub kernel: [   11.051254]   PREFETCH window: disabled.
Oct 31 02:14:57 miniub kernel: [   11.051257] PCI: Bridge: 0000:00:03.0
Oct 31 02:14:57 miniub kernel: [   11.051259]   IO window: 4000-4fff
Oct 31 02:14:57 miniub kernel: [   11.051261]   MEM window: b4000000-b7ffffff
Oct 31 02:14:57 miniub kernel: [   11.051263]   PREFETCH window: d0000000-d01fffff
Oct 31 02:14:57 miniub kernel: [   11.051266] PCI: Bridge: 0000:00:10.0
Oct 31 02:14:57 miniub kernel: [   11.051267]   IO window: disabled.
Oct 31 02:14:57 miniub kernel: [   11.051270]   MEM window: disabled.
Oct 31 02:14:57 miniub kernel: [   11.051272]   PREFETCH window: disabled.
Oct 31 02:14:57 miniub kernel: [   11.051285] PCI: Setting latency timer of device 0000:00:02.0 to 64
Oct 31 02:14:57 miniub kernel: [   11.051292] PCI: Setting latency timer of device 0000:00:03.0 to 64
Oct 31 02:14:57 miniub kernel: [   11.051299] PCI: Setting latency timer of device 0000:00:10.0 to 64
Oct 31 02:14:57 miniub kernel: [   11.051309] NET: Registered protocol family 2
Oct 31 02:14:57 miniub kernel: [   11.088898] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 31 02:14:57 miniub kernel: [   11.089195] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 31 02:14:57 miniub kernel: [   11.090140] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 31 02:14:57 miniub kernel: [   11.090647] TCP: Hash tables configured (established 131072 bind 65536)
Oct 31 02:14:57 miniub kernel: [   11.090650] TCP reno registered
Oct 31 02:14:57 miniub kernel: [   11.100940] checking if image is initramfs... it is
Oct 31 02:14:57 miniub kernel: [   11.692942] Freeing initrd memory: 7141k freed
Oct 31 02:14:57 miniub kernel: [   11.693080] Simple Boot Flag at 0x36 set to 0x1
Oct 31 02:14:57 miniub kernel: [   11.693490] audit: initializing netlink socket (disabled)
Oct 31 02:14:57 miniub kernel: [   11.693503] audit(1225419276.332:1): initialized
Oct 31 02:14:57 miniub kernel: [   11.693644] highmem bounce pool size: 64 pages
Oct 31 02:14:57 miniub kernel: [   11.695182] VFS: Disk quotas dquot_6.5.1
Oct 31 02:14:57 miniub kernel: [   11.695246] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 31 02:14:57 miniub kernel: [   11.695361] io scheduler noop registered
Oct 31 02:14:57 miniub kernel: [   11.695363] io scheduler anticipatory registered
Oct 31 02:14:57 miniub kernel: [   11.695365] io scheduler deadline registered
Oct 31 02:14:57 miniub kernel: [   11.695378] io scheduler cfq registered (default)
Oct 31 02:14:57 miniub kernel: [   11.695392] pci 0000:00:00.0: Enabling HT MSI Mapping
Oct 31 02:14:57 miniub kernel: [   11.695422] pci 0000:00:02.0: Enabling HT MSI Mapping
Oct 31 02:14:57 miniub kernel: [   11.695430] pci 0000:00:03.0: Enabling HT MSI Mapping
Oct 31 02:14:57 miniub kernel: [   11.695438] Boot video device is 0000:00:05.0
Oct 31 02:14:57 miniub kernel: [   11.695458] pci 0000:00:09.0: Enabling HT MSI Mapping
Oct 31 02:14:57 miniub kernel: [   11.900416] pci 0000:00:0e.0: Enabling HT MSI Mapping
Oct 31 02:14:57 miniub kernel: [   11.900425] pci 0000:00:10.0: Enabling HT MSI Mapping
Oct 31 02:14:57 miniub kernel: [   11.900436] pci 0000:00:10.1: Enabling HT MSI Mapping
Oct 31 02:14:57 miniub kernel: [   11.900543] PCI: Setting latency timer of device 0000:00:02.0 to 64
Oct 31 02:14:57 miniub kernel: [   11.900564] assign_interrupt_mode Found MSI capability
Oct 31 02:14:57 miniub kernel: [   11.900584] Allocate Port Service[0000:00:02.0:pcie00]
Oct 31 02:14:57 miniub kernel: [   11.900639] PCI: Setting latency timer of device 0000:00:03.0 to 64
Oct 31 02:14:57 miniub kernel: [   11.900659] assign_interrupt_mode Found MSI capability
Oct 31 02:14:57 miniub kernel: [   11.900674] Allocate Port Service[0000:00:03.0:pcie00]
Oct 31 02:14:57 miniub kernel: [   11.900856] isapnp: Scanning for PnP cards...
Oct 31 02:14:57 miniub kernel: [   12.253704] isapnp: No Plug & Play device found
Oct 31 02:14:57 miniub kernel: [   12.281232] Real Time Clock Driver v1.12ac
Oct 31 02:14:57 miniub kernel: [   12.281421] hpet_resources: 0xfed00000 is busy
Oct 31 02:14:57 miniub kernel: [   12.281457] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 31 02:14:57 miniub kernel: [   12.282405] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 31 02:14:57 miniub kernel: [   12.282463] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Oct 31 02:14:57 miniub kernel: [   12.282541] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct 31 02:14:57 miniub kernel: [   12.282846] i8042.c: Detected active multiplexing controller, rev 1.1.
Oct 31 02:14:57 miniub kernel: [   12.282916] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 31 02:14:57 miniub kernel: [   12.282920] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Oct 31 02:14:57 miniub kernel: [   12.282923] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Oct 31 02:14:57 miniub kernel: [   12.282925] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Oct 31 02:14:57 miniub kernel: [   12.282928] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Oct 31 02:14:57 miniub kernel: [   12.292258] mice: PS/2 mouse device common for all mice
Oct 31 02:14:57 miniub kernel: [   12.292355] EISA: Probing bus 0 at eisa.0
Oct 31 02:14:57 miniub kernel: [   12.292360] Cannot allocate resource for EISA slot 1
Oct 31 02:14:57 miniub kernel: [   12.292363] Cannot allocate resource for EISA slot 2
Oct 31 02:14:57 miniub kernel: [   12.292365] Cannot allocate resource for EISA slot 3
Oct 31 02:14:57 miniub kernel: [   12.292367] Cannot allocate resource for EISA slot 4
Oct 31 02:14:57 miniub kernel: [   12.292380] EISA: Detected 0 cards.
Oct 31 02:14:57 miniub kernel: [   12.292383] cpuidle: using governor ladder
Oct 31 02:14:57 miniub kernel: [   12.292385] cpuidle: using governor menu
Oct 31 02:14:57 miniub kernel: [   12.292466] NET: Registered protocol family 1
Oct 31 02:14:57 miniub kernel: [   12.292489] Using IPI No-Shortcut mode
Oct 31 02:14:57 miniub kernel: [   12.292516] registered taskstats version 1
Oct 31 02:14:57 miniub kernel: [   12.292628]   Magic number: 12:730:208
Oct 31 02:14:57 miniub kernel: [   12.292685]   hash matches device ttyt6
Oct 31 02:14:57 miniub kernel: [   12.292792]   hash matches device vcsa
Oct 31 02:14:57 miniub kernel: [   12.292831] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 31 02:14:57 miniub kernel: [   12.292833] EDD information not available.
Oct 31 02:14:57 miniub kernel: [   12.293076] Freeing unused kernel memory: 368k freed
Oct 31 02:14:57 miniub kernel: [   12.293100] Write protecting the kernel read-only data: 801k
Oct 31 02:14:57 miniub kernel: [   12.295977] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Oct 31 02:14:57 miniub kernel: [   12.470272] fuse init (API version 7.9)
Oct 31 02:14:57 miniub kernel: [   12.490343] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Oct 31 02:14:57 miniub kernel: [   12.490349] ACPI: Processor [CPU0] (supports 8 throttling states)
Oct 31 02:14:57 miniub kernel: [   12.490362] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
Oct 31 02:14:57 miniub kernel: [   12.511723] ACPI: Thermal Zone [TZS0] (59 C)
Oct 31 02:14:57 miniub kernel: [   12.519635] ACPI: Thermal Zone [TZS1] (62 C)
Oct 31 02:14:57 miniub kernel: [   13.328005] ACPI: PCI Interrupt Link [LK2E] enabled at IRQ 19
Oct 31 02:14:57 miniub kernel: [   13.328018] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LK2E] -> GSI 19 (level, high) -> IRQ 16
Oct 31 02:14:57 miniub kernel: [   13.328028] PCI: Setting latency timer of device 0000:01:00.0 to 64
Oct 31 02:14:57 miniub kernel: [   13.347588] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x13, vendor 0x4243)
Oct 31 02:14:57 miniub kernel: [   13.347596] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0D, vendor 0x4243)
Oct 31 02:14:57 miniub kernel: [   13.347602] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x04, vendor 0x4243)
Oct 31 02:14:57 miniub kernel: [   13.347608] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x05, vendor 0x4243)
Oct 31 02:14:57 miniub kernel: [   13.387622] ssb: Sonics Silicon Backplane found on PCI device 0000:01:00.0
Oct 31 02:14:57 miniub kernel: [   13.451579] usbcore: registered new interface driver usbfs
Oct 31 02:14:57 miniub kernel: [   13.451603] usbcore: registered new interface driver hub
Oct 31 02:14:57 miniub kernel: [   13.457138] usbcore: registered new device driver usb
Oct 31 02:14:57 miniub kernel: [   13.470760] SCSI subsystem initialized
Oct 31 02:14:57 miniub kernel: [   13.511515] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Oct 31 02:14:57 miniub kernel: [   13.511893] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 23
Oct 31 02:14:57 miniub kernel: [   13.511904] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 23 (level, high) -> IRQ 17
Oct 31 02:14:57 miniub kernel: [   13.511917] PCI: Setting latency timer of device 0000:00:0b.0 to 64
Oct 31 02:14:57 miniub kernel: [   13.511920] ohci_hcd 0000:00:0b.0: OHCI Host Controller
Oct 31 02:14:57 miniub kernel: [   13.512199] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
Oct 31 02:14:57 miniub kernel: [   13.512219] ohci_hcd 0000:00:0b.0: irq 17, io mem 0xb0004000
Oct 31 02:14:57 miniub kernel: [   13.543475] libata version 3.00 loaded.
Oct 31 02:14:57 miniub kernel: [   13.569563] usb usb1: configuration #1 chosen from 1 choice
Oct 31 02:14:57 miniub kernel: [   13.569588] hub 1-0:1.0: USB hub found
Oct 31 02:14:57 miniub kernel: [   13.569597] hub 1-0:1.0: 8 ports detected
Oct 31 02:14:57 miniub kernel: [   13.671949] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
Oct 31 02:14:57 miniub kernel: [   13.671961] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 22 (level, high) -> IRQ 18
Oct 31 02:14:57 miniub kernel: [   13.671975] PCI: Setting latency timer of device 0000:00:0b.1 to 64
Oct 31 02:14:57 miniub kernel: [   13.671978] ehci_hcd 0000:00:0b.1: EHCI Host Controller
Oct 31 02:14:57 miniub kernel: [   13.672002] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
Oct 31 02:14:57 miniub kernel: [   13.672032] ehci_hcd 0000:00:0b.1: debug port 1
Oct 31 02:14:57 miniub kernel: [   13.672037] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
Oct 31 02:14:57 miniub kernel: [   13.672047] ehci_hcd 0000:00:0b.1: irq 18, io mem 0xb0005000
Oct 31 02:14:57 miniub kernel: [   13.683379] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 31 02:14:57 miniub kernel: [   13.683499] usb usb2: configuration #1 chosen from 1 choice
Oct 31 02:14:57 miniub kernel: [   13.683520] hub 2-0:1.0: USB hub found
Oct 31 02:14:57 miniub kernel: [   13.683526] hub 2-0:1.0: 8 ports detected
Oct 31 02:14:57 miniub kernel: [   13.787486] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Oct 31 02:14:57 miniub kernel: [   13.787825] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 18
Oct 31 02:14:57 miniub kernel: [   13.787836] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 18 (level, high) -> IRQ 19
Oct 31 02:14:57 miniub kernel: [   13.787842] PCI: Setting latency timer of device 0000:00:14.0 to 64
Oct 31 02:14:57 miniub kernel: [   14.307466] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:16:d3:ae:e1:cb
Oct 31 02:14:57 miniub kernel: [   14.307472] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
Oct 31 02:14:57 miniub kernel: [   14.307788] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Oct 31 02:14:57 miniub kernel: [   14.307811] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
Oct 31 02:14:57 miniub kernel: [   14.308132] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 17
Oct 31 02:14:57 miniub kernel: [   14.308142] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 17 (level, high) -> IRQ 20
Oct 31 02:14:57 miniub kernel: [   14.308163] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Oct 31 02:14:57 miniub kernel: [   14.308170] ACPI: PCI interrupt for device 0000:00:0e.0 disabled
Oct 31 02:14:57 miniub kernel: [   14.310745] sata_nv 0000:00:0e.0: version 3.5
Oct 31 02:14:57 miniub kernel: [   14.310753] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 17 (level, high) -> IRQ 20
Oct 31 02:14:57 miniub kernel: [   14.310781] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Oct 31 02:14:57 miniub kernel: [   14.311893] scsi0 : sata_nv
Oct 31 02:14:57 miniub kernel: [   14.312397] scsi1 : sata_nv
Oct 31 02:14:57 miniub kernel: [   14.312563] ata1: SATA max UDMA/133 cmd 0x30b0 ctl 0x30a4 bmdma 0x3090 irq 20
Oct 31 02:14:57 miniub kernel: [   14.312567] ata2: SATA max UDMA/133 cmd 0x30a8 ctl 0x30a0 bmdma 0x3098 irq 20
Oct 31 02:14:57 miniub kernel: [   14.319050] usb 1-6: new low speed USB device using ohci_hcd and address 2
Oct 31 02:14:57 miniub kernel: [   14.533064] usb 1-6: configuration #1 chosen from 1 choice
Oct 31 02:14:57 miniub kernel: [   14.551764] usbcore: registered new interface driver hiddev
Oct 31 02:14:57 miniub kernel: [   14.557128] input: Genius NetScroll + Traveler as /devices/pci0000:00/0000:00:0b.0/usb1/1-6/1-6:1.0/input/input2
Oct 31 02:14:57 miniub kernel: [   14.566931] input,hidraw0: USB HID v1.10 Mouse [Genius NetScroll + Traveler] on usb-0000:00:0b.0-6
Oct 31 02:14:57 miniub kernel: [   14.566947] usbcore: registered new interface driver usbhid
Oct 31 02:14:57 miniub kernel: [   14.566951] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Oct 31 02:14:57 miniub kernel: [   14.778794] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct 31 02:14:57 miniub kernel: [   14.786962] ata1.00: ATA-7: WDC WD800BEVS-60RST0, 04.01G04, max UDMA/100
Oct 31 02:14:57 miniub kernel: [   14.786965] ata1.00: 156301488 sectors, multi 16: LBA48 
Oct 31 02:14:57 miniub kernel: [   14.794959] ata1.00: configured for UDMA/100
Oct 31 02:14:57 miniub kernel: [   15.106595] ata2: SATA link down (SStatus 0 SControl 300)
Oct 31 02:14:57 miniub kernel: [   15.117243] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BEVS-60 04.0 PQ: 0 ANSI: 5
Oct 31 02:14:57 miniub kernel: [   15.118812] pata_amd 0000:00:0d.0: version 0.3.10
Oct 31 02:14:57 miniub kernel: [   15.118856] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Oct 31 02:14:57 miniub kernel: [   15.121490] scsi2 : pata_amd
Oct 31 02:14:57 miniub kernel: [   15.122126] scsi3 : pata_amd
Oct 31 02:14:57 miniub kernel: [   15.122693] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
Oct 31 02:14:57 miniub kernel: [   15.122696] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
Oct 31 02:14:57 miniub kernel: [   15.606601] ata4.00: ATAPI: Optiarc CD-RW CRX880A, KH18, max MWDMA2
Oct 31 02:14:57 miniub kernel: [   15.778442] ata4.00: configured for MWDMA2
Oct 31 02:14:57 miniub kernel: [   15.779390] scsi 3:0:0:0: CD-ROM            Optiarc  CD-RW CRX880A    KH18 PQ: 0 ANSI: 5
Oct 31 02:14:57 miniub kernel: [   15.786752] Driver 'sd' needs updating - please use bus_type methods
Oct 31 02:14:57 miniub kernel: [   15.786832] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Oct 31 02:14:57 miniub kernel: [   15.786843] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 02:14:57 miniub kernel: [   15.786846] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 31 02:14:57 miniub kernel: [   15.786860] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 02:14:57 miniub kernel: [   15.786900] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Oct 31 02:14:57 miniub kernel: [   15.786907] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 02:14:57 miniub kernel: [   15.786910] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 31 02:14:57 miniub kernel: [   15.786922] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 02:14:57 miniub kernel: [   15.786925]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Oct 31 02:14:57 miniub kernel: [   15.835923]  sda1 sda2 sda3 < sda5 sda6 > sda4
Oct 31 02:14:57 miniub kernel: [   15.858576] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 31 02:14:57 miniub kernel: [   15.863897] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 31 02:14:57 miniub kernel: [   15.863915] sr 3:0:0:0: Attached scsi generic sg1 type 5
Oct 31 02:14:57 miniub kernel: [   15.868622] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Oct 31 02:14:57 miniub kernel: [   15.868628] Uniform CD-ROM driver Revision: 3.20
Oct 31 02:14:57 miniub kernel: [   15.868677] sr 3:0:0:0: Attached scsi CD-ROM sr0
Oct 31 02:14:57 miniub kernel: [   16.444759] Attempting manual resume
Oct 31 02:14:57 miniub kernel: [   16.444762] swsusp: Resume From Partition 8:5
Oct 31 02:14:57 miniub kernel: [   16.444764] PM: Checking swsusp image.
Oct 31 02:14:57 miniub kernel: [   16.445008] PM: Resume from disk failed.
Oct 31 02:14:57 miniub kernel: [   16.460087] EXT3-fs: INFO: recovery required on readonly filesystem.
Oct 31 02:14:57 miniub kernel: [   16.460091] EXT3-fs: write access will be enabled during recovery.
Oct 31 02:14:57 miniub kernel: [   16.754449] kjournald starting.  Commit interval 5 seconds
Oct 31 02:14:57 miniub kernel: [   16.754463] EXT3-fs: sda6: orphan cleanup on readonly fs
Oct 31 02:14:57 miniub kernel: [   16.754469] ext3_orphan_cleanup: deleting unreferenced inode 677361
Oct 31 02:14:57 miniub kernel: [   16.754508] ext3_orphan_cleanup: deleting unreferenced inode 65299
Oct 31 02:14:57 miniub kernel: [   16.754513] EXT3-fs: sda6: 2 orphan inodes deleted
Oct 31 02:14:57 miniub kernel: [   16.754515] EXT3-fs: recovery complete.
Oct 31 02:14:57 miniub kernel: [   16.766632] EXT3-fs: mounted filesystem with ordered data mode.
Oct 31 02:14:57 miniub kernel: [   23.337964] input: PC Speaker as /devices/platform/pcspkr/input/input3
Oct 31 02:14:57 miniub kernel: [   23.942594] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 31 02:14:57 miniub kernel: [   23.992589] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 31 02:14:57 miniub kernel: [   24.040084] Linux agpgart interface v0.102
Oct 31 02:14:57 miniub kernel: [   24.089535] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
Oct 31 02:14:57 miniub kernel: [   24.089551] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
Oct 31 02:14:57 miniub kernel: [   24.233540] input: Power Button (FF) as /devices/virtual/input/input4
Oct 31 02:14:57 miniub kernel: [   24.261414] ACPI: Power Button (FF) [PWRF]
Oct 31 02:14:57 miniub kernel: [   24.261486] input: Sleep Button (CM) as /devices/virtual/input/input5
Oct 31 02:14:57 miniub kernel: [   24.293367] ACPI: Sleep Button (CM) [SLPB]
Oct 31 02:14:57 miniub kernel: [   24.293420] input: Power Button (CM) as /devices/virtual/input/input6
Oct 31 02:14:57 miniub kernel: [   24.321344] ACPI: Power Button (CM) [PWRB]
Oct 31 02:14:57 miniub kernel: [   24.643058] nvidia: module license 'NVIDIA' taints kernel.
Oct 31 02:14:57 miniub kernel: [   25.128965] ACPI: WMI-Acer: Mapper loaded
Oct 31 02:14:57 miniub kernel: [   25.369057] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input7
Oct 31 02:14:57 miniub kernel: [   25.396743] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Oct 31 02:14:57 miniub kernel: [   25.767655] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
Oct 31 02:14:57 miniub kernel: [   25.797042] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
Oct 31 02:14:57 miniub kernel: [   26.257440] eth0: no link during initialization.
Oct 31 02:14:57 miniub kernel: [   26.592045] ieee80211_crypt: registered algorithm 'NULL'
Oct 31 02:14:57 miniub kernel: [   27.125754] ACPI: AC Adapter [ADP1] (on-line)
Oct 31 02:14:57 miniub kernel: [   27.247764] ACPI: Battery Slot [BAT0] (battery absent)
Oct 31 02:14:57 miniub kernel: [   27.299337] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 21
Oct 31 02:14:57 miniub kernel: [   27.299350] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LK3E] -> GSI 21 (level, high) -> IRQ 21
Oct 31 02:14:57 miniub kernel: [   27.299358] PCI: Setting latency timer of device 0000:00:05.0 to 64
Oct 31 02:14:57 miniub kernel: [   27.299576] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
Oct 31 02:14:57 miniub kernel: [   27.413709] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 16
Oct 31 02:14:57 miniub kernel: [   27.413721] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 16 (level, high) -> IRQ 22
Oct 31 02:14:57 miniub kernel: [   27.413747] PCI: Setting latency timer of device 0000:00:10.1 to 64
Oct 31 02:14:57 miniub kernel: [   28.501813] NET: Registered protocol family 17
Oct 31 02:14:57 miniub kernel: [   28.832665] loop: module loaded
Oct 31 02:14:57 miniub kernel: [   28.910668] lp: driver loaded but no devices found
Oct 31 02:14:57 miniub kernel: [   29.232491] Adding 1172704k swap on /dev/sda5.  Priority:-1 extents:1 across:1172704k
Oct 31 02:14:57 miniub kernel: [   29.665589] EXT3 FS on sda6, internal journal
Oct 31 02:14:57 miniub kernel: [   30.783000] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 31 02:14:57 miniub kernel: [   31.634467] No dock devices found.
Oct 31 02:14:58 miniub dhclient: DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
Oct 31 02:14:58 miniub NetworkManager: <info>  starting... 
Oct 31 02:14:58 miniub avahi-daemon[4772]: Found user 'avahi' (UID 105) and group 'avahi' (GID 115).
Oct 31 02:14:58 miniub avahi-daemon[4772]: Successfully dropped root privileges.
Oct 31 02:14:58 miniub avahi-daemon[4772]: avahi-daemon 0.6.22 starting up.
Oct 31 02:14:58 miniub avahi-daemon[4772]: Successfully called chroot().
Oct 31 02:14:58 miniub avahi-daemon[4772]: Successfully dropped remaining capabilities.
Oct 31 02:14:58 miniub avahi-daemon[4772]: No service file found in /etc/avahi/services.
Oct 31 02:14:58 miniub avahi-daemon[4772]: Network interface enumeration completed.
Oct 31 02:14:58 miniub avahi-daemon[4772]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 31 02:14:58 miniub avahi-daemon[4772]: Server startup complete. Host name is miniub.local. Local service cookie is 2903597960.
Oct 31 02:14:58 miniub kernel: [   33.140441] ppdev: user-space parallel port driver
Oct 31 02:14:59 miniub kernel: [   33.657884] audit(1225426499.019:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4799 profile="/usr/sbin/cupsd" namespace="default"
Oct 31 02:14:59 miniub dhcdbd: Started up.
Oct 31 02:15:00 miniub NetworkManager: <debug> [1225426500.804870] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CD_RW_CRX880A'). 
Oct 31 02:15:00 miniub /usr/sbin/cron[4997]: (CRON) INFO (pidfile fd = 3)
Oct 31 02:15:00 miniub /usr/sbin/cron[4998]: (CRON) STARTUP (fork ok)
Oct 31 02:15:00 miniub /usr/sbin/cron[4998]: (CRON) INFO (Running @reboot jobs)
Oct 31 02:15:05 miniub dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct 31 02:15:08 miniub dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Oct 31 02:15:10 miniub kernel: [   45.596004] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
Oct 31 02:15:10 miniub kernel: [   45.596009] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
Oct 31 02:15:10 miniub kernel: [   45.596705] atkbd.c: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
Oct 31 02:15:10 miniub kernel: [   45.596709] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
Oct 31 02:15:13 miniub dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Oct 31 02:15:14 miniub kernel: [   48.871481] ACPI: PCI interrupt for device 0000:01:00.0 disabled
Oct 31 02:15:14 miniub NetworkManager: <debug> [1225426514.245161] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Oct 31 02:15:14 miniub NetworkManager: <debug> [1225426514.247214] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ssb__null_'). 
Oct 31 02:15:20 miniub dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Oct 31 02:15:23 miniub kernel: [   58.004132] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LK2E] -> GSI 19 (level, high) -> IRQ 16
Oct 31 02:15:23 miniub kernel: [   58.004143] PCI: Setting latency timer of device 0000:01:00.0 to 64
Oct 31 02:15:23 miniub NetworkManager: <debug> [1225426523.397569] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_1a_73_95_a1_ea'). 
Oct 31 02:15:23 miniub kernel: [   58.171604] ieee80211_crypt: registered algorithm 'TKIP'
Oct 31 02:15:23 miniub kernel: [   58.171923] eth1: Broadcom BCM4311 802.11 Wireless Controller 5.10.27.6
Oct 31 02:15:23 miniub NetworkManager: <info>  eth1: Device is fully-supported using driver 'wl'. 
Oct 31 02:15:23 miniub NetworkManager: <info>  eth1: driver does not support SSID scans (scan_capa 0x00). 
Oct 31 02:15:23 miniub NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 31 02:15:23 miniub NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 31 02:15:23 miniub NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct 31 02:15:23 miniub NetworkManager: <info>  Deactivating device eth1. 
Oct 31 02:15:23 miniub NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Invalid argument 
Oct 31 02:15:30 miniub dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Oct 31 02:15:35 miniub kernel: [   70.049415] NET: Registered protocol family 10
Oct 31 02:15:35 miniub kernel: [   70.049839] lo: Disabled Privacy Extensions
Oct 31 02:15:35 miniub kernel: [   70.050468] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 31 02:15:36 miniub avahi-daemon[4772]: Registering new address record for fe80::21a:73ff:fe95:a1ea on eth1.*.
Oct 31 02:15:45 miniub kernel: [   80.177478] eth1: no IPv6 routers present
Oct 31 02:15:45 miniub NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 31 02:15:45 miniub NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 31 02:15:45 miniub dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 31 02:15:45 miniub NetworkManager: <info>  Will activate connection 'eth1/WiFi'. 
Oct 31 02:15:45 miniub NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 31 02:15:45 miniub NetworkManager: <info>  Activation (eth1) started... 
Oct 31 02:15:45 miniub NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 31 02:15:45 miniub NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 31 02:15:45 miniub NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 31 02:15:45 miniub NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 31 02:15:45 miniub NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 31 02:15:45 miniub NetworkManager: <info>  Activation (eth1/wireless): access point 'WiFi' is unencrypted, no key needed. 
Oct 31 02:15:47 miniub NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Oct 31 02:15:47 miniub NetworkManager: <info>  SUP: response was 'OK' 
Oct 31 02:15:47 miniub NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 31 02:15:47 miniub NetworkManager: <info>  SUP: response was 'OK' 
Oct 31 02:15:47 miniub NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 31 02:15:47 miniub NetworkManager: <info>  SUP: response was '0' 
Oct 31 02:15:47 miniub NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 57694669' 
Oct 31 02:15:47 miniub NetworkManager: <info>  SUP: response was 'OK' 
Oct 31 02:15:47 miniub NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 31 02:15:47 miniub NetworkManager: <info>  SUP: response was 'OK' 
Oct 31 02:15:47 miniub NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 31 02:15:47 miniub NetworkManager: <info>  SUP: response was 'OK' 
Oct 31 02:15:47 miniub NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 31 02:15:47 miniub NetworkManager: <info>  Supplicant state changed: 1 
Oct 31 02:15:47 miniub NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'WiFi'. 
Oct 31 02:15:47 miniub NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 31 02:15:47 miniub NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 31 02:15:48 miniub dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Oct 31 02:15:48 miniub NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 31 02:15:48 miniub NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 31 02:15:48 miniub NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 31 02:15:49 miniub NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 31 02:15:51 miniub dhclient: DHCPREQUEST of 192.168.1.100 on eth1 to 255.255.255.255 port 67
Oct 31 02:15:51 miniub dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
Oct 31 02:15:51 miniub avahi-daemon[4772]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Oct 31 02:15:51 miniub avahi-daemon[4772]: New relevant interface eth1.IPv4 for mDNS.
Oct 31 02:15:51 miniub avahi-daemon[4772]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Oct 31 02:15:51 miniub NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth1 
Oct 31 02:15:51 miniub NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 31 02:15:51 miniub NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 31 02:15:51 miniub dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 31 02:15:51 miniub dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
Oct 31 02:15:51 miniub dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 31 02:15:51 miniub dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 31 02:15:51 miniub NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 31 02:15:51 miniub NetworkManager: <info>    address 192.168.1.100 
Oct 31 02:15:51 miniub NetworkManager: <info>    netmask 255.255.255.0 
Oct 31 02:15:51 miniub NetworkManager: <info>    broadcast 192.168.1.255 
Oct 31 02:15:51 miniub NetworkManager: <info>    gateway 192.168.1.1 
Oct 31 02:15:51 miniub NetworkManager: <info>    nameserver 200.42.0.111 
Oct 31 02:15:51 miniub NetworkManager: <info>    nameserver 200.42.97.111 
Oct 31 02:15:51 miniub NetworkManager: <info>    nameserver 200.42.97.110 
Oct 31 02:15:51 miniub dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Oct 31 02:15:51 miniub NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 31 02:15:51 miniub NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 31 02:15:51 miniub NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 31 02:15:51 miniub avahi-daemon[4772]: Withdrawing address record for 192.168.1.100 on eth1.
Oct 31 02:15:51 miniub avahi-daemon[4772]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Oct 31 02:15:51 miniub avahi-daemon[4772]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 31 02:15:51 miniub avahi-daemon[4772]: Withdrawing address record for fe80::21a:73ff:fe95:a1ea on eth1.
Oct 31 02:15:51 miniub dhclient: bound to 192.168.1.100 -- renewal in 35198 seconds.
Oct 31 02:15:51 miniub avahi-daemon[4772]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.100.
Oct 31 02:15:51 miniub avahi-daemon[4772]: New relevant interface eth1.IPv4 for mDNS.
Oct 31 02:15:51 miniub avahi-daemon[4772]: Registering new address record for 192.168.1.100 on eth1.IPv4.
Oct 31 02:15:52 miniub NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 31 02:15:52 miniub NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 31 02:15:52 miniub NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 31 02:15:52 miniub NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 31 02:15:52 miniub NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 31 02:15:53 miniub avahi-daemon[4772]: Registering new address record for fe80::21a:73ff:fe95:a1ea on eth1.*.
Oct 31 02:15:53 miniub ntpdate[5511]: adjust time server 91.189.94.4 offset 0.294450 sec
Oct 31 02:15:57 miniub NetworkManager: <info>  Supplicant state changed: 1 
Oct 31 02:16:02 miniub kernel: [   96.908015] eth1: no IPv6 routers present
Oct 31 02:16:06 miniub dhclient: No DHCPOFFERS received.
Oct 31 02:16:06 miniub dhclient: Trying recorded lease 192.168.1.101
Oct 31 02:16:06 miniub avahi-daemon[4772]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
Oct 31 02:16:06 miniub avahi-daemon[4772]: New relevant interface eth0.IPv4 for mDNS.
Oct 31 02:16:06 miniub avahi-daemon[4772]: Registering new address record for 192.168.1.101 on eth0.IPv4.
Oct 31 02:16:06 miniub dhclient: bound: renewal in 33681 seconds.
Oct 31 02:16:07 miniub ntpdate[5552]: adjust time server 91.189.94.4 offset 0.283689 sec
Oct 31 02:17:01 miniub /USR/SBIN/CRON[5612]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 02:19:34 miniub syslogd 1.5.0#1ubuntu1: restart.

```

---

### Post by FFe_ on 2008-10-31
this was the last one:
```
Oct 31 02:19:34 miniub syslogd 1.5.0#1ubuntu1: restart.
Oct 31 02:19:34 miniub kernel: Inspecting /boot/System.map-2.6.24-21-generic
Oct 31 02:19:34 miniub kernel: Loaded 27897 symbols from /boot/System.map-2.6.24-21-generic.
Oct 31 02:19:34 miniub kernel: Symbols match kernel version 2.6.24.
Oct 31 02:19:34 miniub kernel: Loaded 34477 symbols from 78 modules.
Oct 31 02:19:34 miniub kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 31 02:19:34 miniub kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 31 02:19:34 miniub kernel: [    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:43:45 UTC 2008 (Ubuntu 2.6.24-21.43-generic)
Oct 31 02:19:34 miniub kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 31 02:19:34 miniub kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Oct 31 02:19:34 miniub kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Oct 31 02:19:34 miniub kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
Oct 31 02:19:34 miniub kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000057f10000 (usable)
Oct 31 02:19:34 miniub kernel: [    0.000000]  BIOS-e820: 0000000057f10000 - 0000000057f17000 (ACPI data)
Oct 31 02:19:34 miniub kernel: [    0.000000]  BIOS-e820: 0000000057f17000 - 0000000057f80000 (ACPI NVS)
Oct 31 02:19:34 miniub kernel: [    0.000000]  BIOS-e820: 0000000057f80000 - 0000000060000000 (reserved)
Oct 31 02:19:34 miniub kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Oct 31 02:19:34 miniub kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Oct 31 02:19:34 miniub kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Oct 31 02:19:34 miniub kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 31 02:19:34 miniub kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Oct 31 02:19:34 miniub kernel: [    0.000000] 511MB HIGHMEM available.
Oct 31 02:19:34 miniub kernel: [    0.000000] 896MB LOWMEM available.
Oct 31 02:19:34 miniub kernel: [    0.000000] found SMP MP-table at 000f8780
Oct 31 02:19:34 miniub kernel: [    0.000000] Entering add_active_range(0, 0, 360208) 0 entries of 256 used
Oct 31 02:19:34 miniub kernel: [    0.000000] Zone PFN ranges:
Oct 31 02:19:34 miniub kernel: [    0.000000]   DMA             0 ->     4096
Oct 31 02:19:34 miniub kernel: [    0.000000]   Normal       4096 ->   229376
Oct 31 02:19:34 miniub kernel: [    0.000000]   HighMem    229376 ->   360208
Oct 31 02:19:34 miniub kernel: [    0.000000] Movable zone start PFN for each node
Oct 31 02:19:34 miniub kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 31 02:19:34 miniub kernel: [    0.000000]     0:        0 ->   360208
Oct 31 02:19:34 miniub kernel: [    0.000000] On node 0 totalpages: 360208
Oct 31 02:19:34 miniub kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Oct 31 02:19:34 miniub kernel: [    0.000000]   DMA zone: 0 pages reserved
Oct 31 02:19:34 miniub kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Oct 31 02:19:34 miniub kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Oct 31 02:19:34 miniub kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Oct 31 02:19:34 miniub kernel: [    0.000000]   HighMem zone: 1022 pages used for memmap
Oct 31 02:19:34 miniub kernel: [    0.000000]   HighMem zone: 129810 pages, LIFO batch:31
Oct 31 02:19:34 miniub kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Oct 31 02:19:34 miniub kernel: [    0.000000] DMI present.
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F87B0 checksum 0
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: RSDP 000F87B0, 0024 (r3 HPQOEM)
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: XSDT 57F100CE, 005C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: FACP 57F16B42, 00F4 (r3 HPQOEM SLIC-MPC  6040000 PTL     F4240)
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: DSDT 57F1012A, 6A18 (r1 HPQOEM SLIC-MPC  6040000 MSFT  100000E)
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: FACS 57F17FC0, 0040
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: SLIC 57F16CAA, 0176 (r1 HPQOEM SLIC-MPC  6040000 HPQ         1)
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: MCFG 57F16E20, 003C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: HPET 57F16E5C, 0038 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: APIC 57F16E94, 0050 (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: BOOT 57F16EE4, 0028 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: SSDT 57F16F0C, 00F4 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: DMI detected: Hewlett-Packard
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct 31 02:19:34 miniub kernel: [    0.000000] Processor #0 15:12 APIC version 16
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Oct 31 02:19:34 miniub kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 31 02:19:34 miniub kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 31 02:19:34 miniub kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
Oct 31 02:19:34 miniub kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 31 02:19:34 miniub kernel: [    0.000000] Allocating PCI resources starting at 68000000 (gap: 60000000:80000000)
Oct 31 02:19:34 miniub kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
Oct 31 02:19:34 miniub kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
Oct 31 02:19:34 miniub kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
Oct 31 02:19:34 miniub kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
Oct 31 02:19:34 miniub kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 357394
Oct 31 02:19:34 miniub kernel: [    0.000000] Kernel command line: root=UUID=9c41d09f-5864-470d-a350-acfda4da607a ro quiet splash
Oct 31 02:19:34 miniub kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Oct 31 02:19:34 miniub kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Oct 31 02:19:34 miniub kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 31 02:19:34 miniub kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 31 02:19:34 miniub kernel: [    0.000000] Initializing CPU#0
Oct 31 02:19:34 miniub kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 31 02:19:34 miniub kernel: [    0.000000] Detected 1808.265 MHz processor.
Oct 31 02:19:34 miniub kernel: [   14.703902] spurious 8259A interrupt: IRQ7.
Oct 31 02:19:34 miniub kernel: [   14.707009] Console: colour VGA+ 80x25
Oct 31 02:19:34 miniub kernel: [   14.707012] console [tty0] enabled
Oct 31 02:19:34 miniub kernel: [   14.707432] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 31 02:19:34 miniub kernel: [   14.707865] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 31 02:19:34 miniub kernel: [   14.757779] Memory: 1416224k/1440832k available (2177k kernel code, 23352k reserved, 1005k data, 368k init, 523328k highmem)
Oct 31 02:19:34 miniub kernel: [   14.757788] virtual kernel memory layout:
Oct 31 02:19:34 miniub kernel: [   14.757789]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Oct 31 02:19:34 miniub kernel: [   14.757790]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 31 02:19:34 miniub kernel: [   14.757792]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Oct 31 02:19:34 miniub kernel: [   14.757793]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Oct 31 02:19:34 miniub kernel: [   14.757794]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Oct 31 02:19:34 miniub kernel: [   14.757795]       .data : 0xc03205e4 - 0xc041bdc4   (1005 kB)
Oct 31 02:19:34 miniub kernel: [   14.757797]       .text : 0xc0100000 - 0xc03205e4   (2177 kB)
Oct 31 02:19:34 miniub kernel: [   14.757800] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 31 02:19:34 miniub kernel: [   14.757840] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Oct 31 02:19:34 miniub kernel: [   14.757991] hpet clockevent registered
Oct 31 02:19:34 miniub kernel: [   14.837950] Calibrating delay using timer specific routine.. 3619.67 BogoMIPS (lpj=7239350)
Oct 31 02:19:34 miniub kernel: [   14.837973] Security Framework initialized
Oct 31 02:19:34 miniub kernel: [   14.837980] SELinux:  Disabled at boot.
Oct 31 02:19:34 miniub kernel: [   14.837996] AppArmor: AppArmor initialized
Oct 31 02:19:34 miniub kernel: [   14.838000] Failure registering capabilities with primary security module.
Oct 31 02:19:34 miniub kernel: [   14.838009] Mount-cache hash table entries: 512
Oct 31 02:19:34 miniub kernel: [   14.838125] Initializing cgroup subsys ns
Oct 31 02:19:34 miniub kernel: [   14.838129] Initializing cgroup subsys cpuacct
Oct 31 02:19:34 miniub kernel: [   14.838139] CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 00000019 00000000
Oct 31 02:19:34 miniub kernel: [   14.838148] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Oct 31 02:19:34 miniub kernel: [   14.838151] CPU: L2 Cache: 512K (64 bytes/line)
Oct 31 02:19:34 miniub kernel: [   14.838154] CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00020410 00002001 00000000 00000019 00000000
Oct 31 02:19:34 miniub kernel: [   14.838164] Compat vDSO mapped to ffffe000.
Oct 31 02:19:34 miniub kernel: [   14.838176] Checking 'hlt' instruction... OK.
Oct 31 02:19:34 miniub kernel: [   14.854260] SMP alternatives: switching to UP code
Oct 31 02:19:34 miniub kernel: [   14.855430] Freeing SMP alternatives: 11k freed
Oct 31 02:19:34 miniub kernel: [   14.855545] Early unpacking initramfs... done
Oct 31 02:19:34 miniub kernel: [   15.161729] ACPI: Core revision 20070126
Oct 31 02:19:34 miniub kernel: [   15.161816] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 31 02:19:34 miniub kernel: [   15.171708] CPU0: AMD Mobile AMD Sempron(tm) stepping 02
Oct 31 02:19:34 miniub kernel: [   15.171721] Total of 1 processors activated (3619.67 BogoMIPS).
Oct 31 02:19:34 miniub kernel: [   15.172022] ENABLING IO-APIC IRQs
Oct 31 02:19:34 miniub kernel: [   15.172252] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 31 02:19:34 miniub kernel: [   15.317743] Brought up 1 CPUs
Oct 31 02:19:34 miniub kernel: [   15.317790] CPU0 attaching sched-domain:
Oct 31 02:19:34 miniub kernel: [   15.317793]  domain 0: span 01
Oct 31 02:19:34 miniub kernel: [   15.317795]   groups: 01
Oct 31 02:19:34 miniub kernel: [   15.317944] net_namespace: 64 bytes
Oct 31 02:19:34 miniub kernel: [   15.317952] Booting paravirtualized kernel on bare hardware
Oct 31 02:19:34 miniub kernel: [   15.318398] Time:  2:19:13  Date: 10/31/08
Oct 31 02:19:34 miniub kernel: [   15.318419] NET: Registered protocol family 16
Oct 31 02:19:34 miniub kernel: [   15.318579] EISA bus registered
Oct 31 02:19:34 miniub kernel: [   15.318584] ACPI: bus type pci registered
Oct 31 02:19:34 miniub kernel: [   15.330624] PCI: BIOS BUG #81[49435000] found
Oct 31 02:19:34 miniub kernel: [   15.330667] PCI: Using configuration type 1
Oct 31 02:19:34 miniub kernel: [   15.330676] Setting up standard PCI resources
Oct 31 02:19:34 miniub kernel: [   15.332378] ACPI: EC: Look up EC in DSDT
Oct 31 02:19:34 miniub kernel: [   15.335764] ACPI: BIOS _OSI(Linux) query ignored via DMI
Oct 31 02:19:34 miniub kernel: [   15.336047] ACPI: Interpreter enabled
Oct 31 02:19:34 miniub kernel: [   15.336050] ACPI: (supports S0 S3 S4 S5)
Oct 31 02:19:34 miniub kernel: [   15.336061] ACPI: Using IOAPIC for interrupt routing
Oct 31 02:19:34 miniub kernel: [   15.336464] ACPI: EC: non-query interrupt received, switching to interrupt mode
Oct 31 02:19:34 miniub kernel: [   15.363347] ACPI: EC: GPE = 0x1, I/O: command/status = 0x66, data = 0x62
Oct 31 02:19:34 miniub kernel: [   15.363349] ACPI: EC: driver started in interrupt mode
Oct 31 02:19:34 miniub kernel: [   15.363390] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 31 02:19:34 miniub kernel: [   15.364389] PCI: Transparent bridge - 0000:00:10.0
Oct 31 02:19:34 miniub kernel: [   15.364404] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct 31 02:19:34 miniub kernel: [   15.364494] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
Oct 31 02:19:34 miniub kernel: [   15.364531] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
Oct 31 02:19:34 miniub kernel: [   15.364557] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
Oct 31 02:19:34 miniub kernel: [   15.495909] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 17 18 22 23) *0, disabled.
Oct 31 02:19:34 miniub kernel: [   15.496098] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 17 18 22 23) *10
Oct 31 02:19:34 miniub kernel: [   15.496283] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
Oct 31 02:19:34 miniub kernel: [   15.496469] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
Oct 31 02:19:34 miniub kernel: [   15.496654] ACPI: PCI Interrupt Link [LK1E] (IRQs 20) *0, disabled.
Oct 31 02:19:34 miniub kernel: [   15.496837] ACPI: PCI Interrupt Link [LK2E] (IRQs 19) *10
Oct 31 02:19:34 miniub kernel: [   15.497021] ACPI: PCI Interrupt Link [LK3E] (IRQs 21) *10
Oct 31 02:19:34 miniub kernel: [   15.497205] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 18 22 23) *0, disabled.
Oct 31 02:19:34 miniub kernel: [   15.497390] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 22 23) *10
Oct 31 02:19:34 miniub kernel: [   15.497580] ACPI: PCI Interrupt Link [LSMU] (IRQs 16 17 18 22 23) *11
Oct 31 02:19:34 miniub kernel: [   15.497771] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 22 23) *11
Oct 31 02:19:34 miniub kernel: [   15.497956] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 22 23) *7
Oct 31 02:19:34 miniub kernel: [   15.498141] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 22 23) *11
Oct 31 02:19:34 miniub kernel: [   15.498331] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 22 23) *0, disabled.
Oct 31 02:19:34 miniub kernel: [   15.498516] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 18 22 23) *0, disabled.
Oct 31 02:19:34 miniub kernel: [   15.498701] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 18 22 23) *0, disabled.
Oct 31 02:19:34 miniub kernel: [   15.498887] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 22 23) *0, disabled.
Oct 31 02:19:34 miniub kernel: [   15.499078] ACPI: PCI Interrupt Link [LTID] (IRQs 16 17 18 22 23) *5
Oct 31 02:19:34 miniub kernel: [   15.499269] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 22 23) *0
Oct 31 02:19:34 miniub kernel: [   15.499381] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 31 02:19:34 miniub kernel: [   15.499407] pnp: PnP ACPI init
Oct 31 02:19:34 miniub kernel: [   15.499413] ACPI: bus type pnp registered
Oct 31 02:19:34 miniub kernel: [   15.503069] pnp: PnP ACPI: found 11 devices
Oct 31 02:19:34 miniub kernel: [   15.503071] ACPI: ACPI bus type pnp unregistered
Oct 31 02:19:34 miniub kernel: [   15.503075] PnPBIOS: Disabled by ACPI PNP
Oct 31 02:19:34 miniub kernel: [   15.503260] PCI: Using ACPI for IRQ routing
Oct 31 02:19:34 miniub kernel: [   15.503263] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 31 02:19:34 miniub kernel: [   15.517606] NET: Registered protocol family 8
Oct 31 02:19:34 miniub kernel: [   15.517609] NET: Registered protocol family 20
Oct 31 02:19:34 miniub kernel: [   15.517641] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
Oct 31 02:19:34 miniub kernel: [   15.517645] hpet0: 3 32-bit timers, 25000000 Hz
Oct 31 02:19:34 miniub kernel: [   15.518687] AppArmor: AppArmor Filesystem Enabled
Oct 31 02:19:34 miniub kernel: [   15.521592] Time: tsc clocksource has been installed.
Oct 31 02:19:34 miniub kernel: [   15.521603] Switched to high resolution mode on CPU 0
Oct 31 02:19:34 miniub kernel: [   15.529581] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
Oct 31 02:19:34 miniub kernel: [   15.529586] system 00:02: ioport range 0x1000-0x107f has been reserved
Oct 31 02:19:34 miniub kernel: [   15.529589] system 00:02: ioport range 0x1080-0x10ff has been reserved
Oct 31 02:19:34 miniub kernel: [   15.529592] system 00:02: ioport range 0x1400-0x147f has been reserved
Oct 31 02:19:34 miniub kernel: [   15.529595] system 00:02: ioport range 0x1480-0x14ff has been reserved
Oct 31 02:19:34 miniub kernel: [   15.529597] system 00:02: ioport range 0x1800-0x187f has been reserved
Oct 31 02:19:34 miniub kernel: [   15.529600] system 00:02: ioport range 0x1880-0x18ff has been reserved
Oct 31 02:19:34 miniub kernel: [   15.529603] system 00:02: ioport range 0x2000-0x203f has been reserved
Oct 31 02:19:34 miniub kernel: [   15.529608] system 00:03: ioport range 0x360-0x361 has been reserved
Oct 31 02:19:34 miniub kernel: [   15.529611] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
Oct 31 02:19:34 miniub kernel: [   15.559942] PCI: Bridge: 0000:00:02.0
Oct 31 02:19:34 miniub kernel: [   15.559944]   IO window: disabled.
Oct 31 02:19:34 miniub kernel: [   15.559947]   MEM window: b3000000-b30fffff
Oct 31 02:19:34 miniub kernel: [   15.559949]   PREFETCH window: disabled.
Oct 31 02:19:34 miniub kernel: [   15.559951] PCI: Bridge: 0000:00:03.0
Oct 31 02:19:34 miniub kernel: [   15.559953]   IO window: 4000-4fff
Oct 31 02:19:34 miniub kernel: [   15.559956]   MEM window: b4000000-b7ffffff
Oct 31 02:19:34 miniub kernel: [   15.559958]   PREFETCH window: d0000000-d01fffff
Oct 31 02:19:34 miniub kernel: [   15.559961] PCI: Bridge: 0000:00:10.0
Oct 31 02:19:34 miniub kernel: [   15.559962]   IO window: disabled.
Oct 31 02:19:34 miniub kernel: [   15.559965]   MEM window: disabled.
Oct 31 02:19:34 miniub kernel: [   15.559968]   PREFETCH window: disabled.
Oct 31 02:19:34 miniub kernel: [   15.559981] PCI: Setting latency timer of device 0000:00:02.0 to 64
Oct 31 02:19:34 miniub kernel: [   15.559988] PCI: Setting latency timer of device 0000:00:03.0 to 64
Oct 31 02:19:34 miniub kernel: [   15.559995] PCI: Setting latency timer of device 0000:00:10.0 to 64
Oct 31 02:19:34 miniub kernel: [   15.560005] NET: Registered protocol family 2
Oct 31 02:19:34 miniub kernel: [   15.597593] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 31 02:19:34 miniub kernel: [   15.597889] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 31 02:19:34 miniub kernel: [   15.598835] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 31 02:19:34 miniub kernel: [   15.599342] TCP: Hash tables configured (established 131072 bind 65536)
Oct 31 02:19:34 miniub kernel: [   15.599345] TCP reno registered
Oct 31 02:19:34 miniub kernel: [   15.609636] checking if image is initramfs... it is
Oct 31 02:19:34 miniub kernel: [   16.201560] Freeing initrd memory: 7141k freed
Oct 31 02:19:34 miniub kernel: [   16.201697] Simple Boot Flag at 0x36 set to 0x1
Oct 31 02:19:34 miniub kernel: [   16.202106] audit: initializing netlink socket (disabled)
Oct 31 02:19:34 miniub kernel: [   16.202119] audit(1225419554.336:1): initialized
Oct 31 02:19:34 miniub kernel: [   16.202260] highmem bounce pool size: 64 pages
Oct 31 02:19:34 miniub kernel: [   16.203800] VFS: Disk quotas dquot_6.5.1
Oct 31 02:19:34 miniub kernel: [   16.203865] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 31 02:19:34 miniub kernel: [   16.203981] io scheduler noop registered
Oct 31 02:19:34 miniub kernel: [   16.203983] io scheduler anticipatory registered
Oct 31 02:19:34 miniub kernel: [   16.203985] io scheduler deadline registered
Oct 31 02:19:34 miniub kernel: [   16.203999] io scheduler cfq registered (default)
Oct 31 02:19:34 miniub kernel: [   16.204012] pci 0000:00:00.0: Enabling HT MSI Mapping
Oct 31 02:19:34 miniub kernel: [   16.204041] pci 0000:00:02.0: Enabling HT MSI Mapping
Oct 31 02:19:34 miniub kernel: [   16.204050] pci 0000:00:03.0: Enabling HT MSI Mapping
Oct 31 02:19:34 miniub kernel: [   16.204057] Boot video device is 0000:00:05.0
Oct 31 02:19:34 miniub kernel: [   16.204078] pci 0000:00:09.0: Enabling HT MSI Mapping
Oct 31 02:19:34 miniub kernel: [   16.406328] pci 0000:00:0e.0: Enabling HT MSI Mapping
Oct 31 02:19:34 miniub kernel: [   16.406337] pci 0000:00:10.0: Enabling HT MSI Mapping
Oct 31 02:19:34 miniub kernel: [   16.406348] pci 0000:00:10.1: Enabling HT MSI Mapping
Oct 31 02:19:34 miniub kernel: [   16.406452] PCI: Setting latency timer of device 0000:00:02.0 to 64
Oct 31 02:19:34 miniub kernel: [   16.406473] assign_interrupt_mode Found MSI capability
Oct 31 02:19:34 miniub kernel: [   16.406493] Allocate Port Service[0000:00:02.0:pcie00]
Oct 31 02:19:34 miniub kernel: [   16.406548] PCI: Setting latency timer of device 0000:00:03.0 to 64
Oct 31 02:19:34 miniub kernel: [   16.406568] assign_interrupt_mode Found MSI capability
Oct 31 02:19:34 miniub kernel: [   16.406583] Allocate Port Service[0000:00:03.0:pcie00]
Oct 31 02:19:34 miniub kernel: [   16.406766] isapnp: Scanning for PnP cards...
Oct 31 02:19:34 miniub kernel: [   16.759595] isapnp: No Plug & Play device found
Oct 31 02:19:34 miniub kernel: [   16.786850] Real Time Clock Driver v1.12ac
Oct 31 02:19:34 miniub kernel: [   16.787040] hpet_resources: 0xfed00000 is busy
Oct 31 02:19:34 miniub kernel: [   16.787079] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 31 02:19:34 miniub kernel: [   16.788029] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 31 02:19:34 miniub kernel: [   16.788087] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Oct 31 02:19:34 miniub kernel: [   16.788162] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct 31 02:19:34 miniub kernel: [   16.788468] i8042.c: Detected active multiplexing controller, rev 1.1.
Oct 31 02:19:34 miniub kernel: [   16.788539] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 31 02:19:34 miniub kernel: [   16.788543] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Oct 31 02:19:34 miniub kernel: [   16.788546] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Oct 31 02:19:34 miniub kernel: [   16.788548] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Oct 31 02:19:34 miniub kernel: [   16.788550] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Oct 31 02:19:34 miniub kernel: [   16.789144] mice: PS/2 mouse device common for all mice
Oct 31 02:19:34 miniub kernel: [   16.789246] EISA: Probing bus 0 at eisa.0
Oct 31 02:19:34 miniub kernel: [   16.789252] Cannot allocate resource for EISA slot 1
Oct 31 02:19:34 miniub kernel: [   16.789254] Cannot allocate resource for EISA slot 2
Oct 31 02:19:34 miniub kernel: [   16.789256] Cannot allocate resource for EISA slot 3
Oct 31 02:19:34 miniub kernel: [   16.789258] Cannot allocate resource for EISA slot 4
Oct 31 02:19:34 miniub kernel: [   16.789271] EISA: Detected 0 cards.
Oct 31 02:19:34 miniub kernel: [   16.789274] cpuidle: using governor ladder
Oct 31 02:19:34 miniub kernel: [   16.789276] cpuidle: using governor menu
Oct 31 02:19:34 miniub kernel: [   16.789358] NET: Registered protocol family 1
Oct 31 02:19:34 miniub kernel: [   16.789382] Using IPI No-Shortcut mode
Oct 31 02:19:34 miniub kernel: [   16.789410] registered taskstats version 1
Oct 31 02:19:34 miniub kernel: [   16.789519]   Magic number: 12:833:309
Oct 31 02:19:34 miniub kernel: [   16.789553]   hash matches device ttyxc
Oct 31 02:19:34 miniub kernel: [   16.789669]   hash matches device tty38
Oct 31 02:19:34 miniub kernel: [   16.789712] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 31 02:19:34 miniub kernel: [   16.789714] EDD information not available.
Oct 31 02:19:34 miniub kernel: [   16.789970] Freeing unused kernel memory: 368k freed
Oct 31 02:19:34 miniub kernel: [   16.789993] Write protecting the kernel read-only data: 801k
Oct 31 02:19:34 miniub kernel: [   16.792853] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Oct 31 02:19:34 miniub kernel: [   16.956285] fuse init (API version 7.9)
Oct 31 02:19:34 miniub kernel: [   16.976359] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Oct 31 02:19:34 miniub kernel: [   16.976365] ACPI: Processor [CPU0] (supports 8 throttling states)
Oct 31 02:19:34 miniub kernel: [   16.976379] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
Oct 31 02:19:34 miniub kernel: [   16.997095] ACPI: Thermal Zone [TZS0] (60 C)
Oct 31 02:19:34 miniub kernel: [   17.005668] ACPI: Thermal Zone [TZS1] (63 C)
Oct 31 02:19:34 miniub kernel: [   17.812720] ACPI: PCI Interrupt Link [LK2E] enabled at IRQ 19
Oct 31 02:19:34 miniub kernel: [   17.812733] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LK2E] -> GSI 19 (level, high) -> IRQ 16
Oct 31 02:19:34 miniub kernel: [   17.812742] PCI: Setting latency timer of device 0000:01:00.0 to 64
Oct 31 02:19:34 miniub kernel: [   17.832301] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x13, vendor 0x4243)
Oct 31 02:19:34 miniub kernel: [   17.832310] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0D, vendor 0x4243)
Oct 31 02:19:34 miniub kernel: [   17.832316] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x04, vendor 0x4243)
Oct 31 02:19:34 miniub kernel: [   17.832322] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x05, vendor 0x4243)
Oct 31 02:19:34 miniub kernel: [   17.872323] ssb: Sonics Silicon Backplane found on PCI device 0000:01:00.0
Oct 31 02:19:34 miniub kernel: [   17.952289] usbcore: registered new interface driver usbfs
Oct 31 02:19:34 miniub kernel: [   17.952311] usbcore: registered new interface driver hub
Oct 31 02:19:34 miniub kernel: [   17.960425] SCSI subsystem initialized
Oct 31 02:19:34 miniub kernel: [   17.976237] usbcore: registered new device driver usb
Oct 31 02:19:34 miniub kernel: [   18.012581] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 23
Oct 31 02:19:34 miniub kernel: [   18.012594] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 23 (level, high) -> IRQ 17
Oct 31 02:19:34 miniub kernel: [   18.012606] PCI: Setting latency timer of device 0000:00:0b.1 to 64
Oct 31 02:19:34 miniub kernel: [   18.012610] ehci_hcd 0000:00:0b.1: EHCI Host Controller
Oct 31 02:19:34 miniub kernel: [   18.012881] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
Oct 31 02:19:34 miniub kernel: [   18.012914] ehci_hcd 0000:00:0b.1: debug port 1
Oct 31 02:19:34 miniub kernel: [   18.012918] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
Oct 31 02:19:34 miniub kernel: [   18.012928] ehci_hcd 0000:00:0b.1: irq 17, io mem 0xb0005000
Oct 31 02:19:34 miniub kernel: [   18.024189] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 31 02:19:34 miniub kernel: [   18.024325] usb usb1: configuration #1 chosen from 1 choice
Oct 31 02:19:34 miniub kernel: [   18.024346] hub 1-0:1.0: USB hub found
Oct 31 02:19:34 miniub kernel: [   18.024352] hub 1-0:1.0: 8 ports detected
Oct 31 02:19:34 miniub kernel: [   18.024382] libata version 3.00 loaded.
Oct 31 02:19:34 miniub kernel: [   18.032195] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Oct 31 02:19:34 miniub kernel: [   18.128649] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
Oct 31 02:19:34 miniub kernel: [   18.128661] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 22 (level, high) -> IRQ 18
Oct 31 02:19:34 miniub kernel: [   18.128673] PCI: Setting latency timer of device 0000:00:0b.0 to 64
Oct 31 02:19:34 miniub kernel: [   18.128677] ohci_hcd 0000:00:0b.0: OHCI Host Controller
Oct 31 02:19:34 miniub kernel: [   18.128700] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
Oct 31 02:19:34 miniub kernel: [   18.128720] ohci_hcd 0000:00:0b.0: irq 18, io mem 0xb0004000
Oct 31 02:19:34 miniub kernel: [   18.186205] usb usb2: configuration #1 chosen from 1 choice
Oct 31 02:19:34 miniub kernel: [   18.186229] hub 2-0:1.0: USB hub found
Oct 31 02:19:34 miniub kernel: [   18.186238] hub 2-0:1.0: 8 ports detected
Oct 31 02:19:34 miniub kernel: [   18.288285] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Oct 31 02:19:34 miniub kernel: [   18.288620] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 18
Oct 31 02:19:34 miniub kernel: [   18.288631] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 18 (level, high) -> IRQ 19
Oct 31 02:19:34 miniub kernel: [   18.288638] PCI: Setting latency timer of device 0000:00:14.0 to 64
Oct 31 02:19:34 miniub kernel: [   18.615870] usb 2-6: new low speed USB device using ohci_hcd and address 2
Oct 31 02:19:34 miniub kernel: [   18.808164] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:16:d3:ae:e1:cb
Oct 31 02:19:34 miniub kernel: [   18.808169] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
Oct 31 02:19:34 miniub kernel: [   18.808486] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Oct 31 02:19:34 miniub kernel: [   18.808510] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
Oct 31 02:19:34 miniub kernel: [   18.808825] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 17
Oct 31 02:19:34 miniub kernel: [   18.808835] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 17 (level, high) -> IRQ 20
Oct 31 02:19:34 miniub kernel: [   18.808855] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Oct 31 02:19:34 miniub kernel: [   18.808862] ACPI: PCI interrupt for device 0000:00:0e.0 disabled
Oct 31 02:19:34 miniub kernel: [   18.811447] sata_nv 0000:00:0e.0: version 3.5
Oct 31 02:19:34 miniub kernel: [   18.811456] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 17 (level, high) -> IRQ 20
Oct 31 02:19:34 miniub kernel: [   18.811483] PCI: Setting latency timer of device 0000:00:0e.0 to 64
Oct 31 02:19:34 miniub kernel: [   18.813005] scsi0 : sata_nv
Oct 31 02:19:34 miniub kernel: [   18.813191] scsi1 : sata_nv
Oct 31 02:19:34 miniub kernel: [   18.813350] ata1: SATA max UDMA/133 cmd 0x30b0 ctl 0x30a4 bmdma 0x3090 irq 20
Oct 31 02:19:34 miniub kernel: [   18.813353] ata2: SATA max UDMA/133 cmd 0x30a8 ctl 0x30a0 bmdma 0x3098 irq 20
Oct 31 02:19:34 miniub kernel: [   18.830876] usb 2-6: configuration #1 chosen from 1 choice
Oct 31 02:19:34 miniub kernel: [   18.849383] usbcore: registered new interface driver hiddev
Oct 31 02:19:34 miniub kernel: [   18.854950] input: Genius NetScroll + Traveler as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/input/input2
Oct 31 02:19:34 miniub kernel: [   18.867746] input,hidraw0: USB HID v1.10 Mouse [Genius NetScroll + Traveler] on usb-0000:00:0b.0-6
Oct 31 02:19:34 miniub kernel: [   18.867763] usbcore: registered new interface driver usbhid
Oct 31 02:19:34 miniub kernel: [   18.867766] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Oct 31 02:19:34 miniub kernel: [   19.279510] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct 31 02:19:34 miniub kernel: [   19.287674] ata1.00: ATA-7: WDC WD800BEVS-60RST0, 04.01G04, max UDMA/100
Oct 31 02:19:34 miniub kernel: [   19.287677] ata1.00: 156301488 sectors, multi 16: LBA48 
Oct 31 02:19:34 miniub kernel: [   19.295669] ata1.00: configured for UDMA/100
Oct 31 02:19:34 miniub kernel: [   19.607304] ata2: SATA link down (SStatus 0 SControl 300)
Oct 31 02:19:34 miniub kernel: [   19.617942] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BEVS-60 04.0 PQ: 0 ANSI: 5
Oct 31 02:19:34 miniub kernel: [   19.619516] pata_amd 0000:00:0d.0: version 0.3.10
Oct 31 02:19:34 miniub kernel: [   19.619562] PCI: Setting latency timer of device 0000:00:0d.0 to 64
Oct 31 02:19:34 miniub kernel: [   19.622202] scsi2 : pata_amd
Oct 31 02:19:34 miniub kernel: [   19.622819] scsi3 : pata_amd
Oct 31 02:19:34 miniub kernel: [   19.623382] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
Oct 31 02:19:34 miniub kernel: [   19.623385] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
Oct 31 02:19:34 miniub kernel: [   20.107313] ata4.00: ATAPI: Optiarc CD-RW CRX880A, KH18, max MWDMA2
Oct 31 02:19:34 miniub kernel: [   20.279157] ata4.00: configured for MWDMA2
Oct 31 02:19:34 miniub kernel: [   20.280117] scsi 3:0:0:0: CD-ROM            Optiarc  CD-RW CRX880A    KH18 PQ: 0 ANSI: 5
Oct 31 02:19:34 miniub kernel: [   20.287417] Driver 'sd' needs updating - please use bus_type methods
Oct 31 02:19:34 miniub kernel: [   20.287498] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Oct 31 02:19:34 miniub kernel: [   20.287509] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 02:19:34 miniub kernel: [   20.287512] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 31 02:19:34 miniub kernel: [   20.287525] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 02:19:34 miniub kernel: [   20.287564] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Oct 31 02:19:34 miniub kernel: [   20.287572] sd 0:0:0:0: [sda] Write Protect is off
Oct 31 02:19:34 miniub kernel: [   20.287574] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 31 02:19:34 miniub kernel: [   20.287586] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 31 02:19:34 miniub kernel: [   20.287590]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Oct 31 02:19:34 miniub kernel: [   20.333333]  sda1 sda2 sda3 < sda5 sda6 > sda4
Oct 31 02:19:34 miniub kernel: [   20.355986] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 31 02:19:34 miniub kernel: [   20.361299] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 31 02:19:34 miniub kernel: [   20.361317] sr 3:0:0:0: Attached scsi generic sg1 type 5
Oct 31 02:19:34 miniub kernel: [   20.365715] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Oct 31 02:19:34 miniub kernel: [   20.365721] Uniform CD-ROM driver Revision: 3.20
Oct 31 02:19:34 miniub kernel: [   20.365769] sr 3:0:0:0: Attached scsi CD-ROM sr0
Oct 31 02:19:34 miniub kernel: [   20.931015] Attempting manual resume
Oct 31 02:19:34 miniub kernel: [   20.931019] swsusp: Resume From Partition 8:5
Oct 31 02:19:34 miniub kernel: [   20.931021] PM: Checking swsusp image.
Oct 31 02:19:34 miniub kernel: [   20.931232] PM: Resume from disk failed.
Oct 31 02:19:34 miniub kernel: [   20.946217] EXT3-fs: INFO: recovery required on readonly filesystem.
Oct 31 02:19:34 miniub kernel: [   20.946221] EXT3-fs: write access will be enabled during recovery.
Oct 31 02:19:34 miniub kernel: [   21.176541] kjournald starting.  Commit interval 5 seconds
Oct 31 02:19:34 miniub kernel: [   21.176556] EXT3-fs: sda6: orphan cleanup on readonly fs
Oct 31 02:19:34 miniub kernel: [   21.176561] ext3_orphan_cleanup: deleting unreferenced inode 677361
Oct 31 02:19:34 miniub kernel: [   21.176599] ext3_orphan_cleanup: deleting unreferenced inode 65299
Oct 31 02:19:34 miniub kernel: [   21.176604] EXT3-fs: sda6: 2 orphan inodes deleted
Oct 31 02:19:34 miniub kernel: [   21.176606] EXT3-fs: recovery complete.
Oct 31 02:19:34 miniub kernel: [   21.180202] EXT3-fs: mounted filesystem with ordered data mode.
Oct 31 02:19:34 miniub kernel: [   27.782732] input: PC Speaker as /devices/platform/pcspkr/input/input3
Oct 31 02:19:34 miniub kernel: [   28.202445] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 31 02:19:34 miniub kernel: [   28.310372] Linux agpgart interface v0.102
Oct 31 02:19:34 miniub kernel: [   28.359931] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
Oct 31 02:19:34 miniub kernel: [   28.359948] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
Oct 31 02:19:34 miniub kernel: [   28.418356] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 31 02:19:34 miniub kernel: [   28.582347] input: Power Button (FF) as /devices/virtual/input/input4
Oct 31 02:19:34 miniub kernel: [   28.610240] ACPI: Power Button (FF) [PWRF]
Oct 31 02:19:34 miniub kernel: [   28.610309] input: Sleep Button (CM) as /devices/virtual/input/input5
Oct 31 02:19:34 miniub kernel: [   28.642292] ACPI: Sleep Button (CM) [SLPB]
Oct 31 02:19:34 miniub kernel: [   28.642358] input: Power Button (CM) as /devices/virtual/input/input6
Oct 31 02:19:34 miniub kernel: [   28.670202] ACPI: Power Button (CM) [PWRB]
Oct 31 02:19:34 miniub kernel: [   28.835565] nvidia: module license 'NVIDIA' taints kernel.
Oct 31 02:19:34 miniub kernel: [   29.369850] ACPI: WMI-Acer: Mapper loaded
Oct 31 02:19:34 miniub kernel: [   29.933457] ieee80211_crypt: registered algorithm 'NULL'
Oct 31 02:19:34 miniub kernel: [   30.122312] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
Oct 31 02:19:34 miniub kernel: [   30.124752] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input7
Oct 31 02:19:34 miniub kernel: [   30.149347] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Oct 31 02:19:34 miniub kernel: [   30.151610] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
Oct 31 02:19:34 miniub kernel: [   30.729361] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 21
Oct 31 02:19:34 miniub kernel: [   30.729373] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LK3E] -> GSI 21 (level, high) -> IRQ 21
Oct 31 02:19:34 miniub kernel: [   30.729381] PCI: Setting latency timer of device 0000:00:05.0 to 64
Oct 31 02:19:34 miniub kernel: [   30.729595] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
Oct 31 02:19:34 miniub kernel: [   30.959425] ACPI: AC Adapter [ADP1] (on-line)
Oct 31 02:19:34 miniub kernel: [   31.012906] ACPI: Battery Slot [BAT0] (battery absent)
Oct 31 02:19:34 miniub kernel: [   31.232715] NET: Registered protocol family 17
Oct 31 02:19:34 miniub kernel: [   31.986741] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 16
Oct 31 02:19:34 miniub kernel: [   31.986753] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 16 (level, high) -> IRQ 22
Oct 31 02:19:34 miniub kernel: [   31.986778] PCI: Setting latency timer of device 0000:00:10.1 to 64
Oct 31 02:19:34 miniub kernel: [   33.307840] loop: module loaded
Oct 31 02:19:34 miniub kernel: [   33.385393] lp: driver loaded but no devices found
Oct 31 02:19:34 miniub kernel: [   33.718730] Adding 1172704k swap on /dev/sda5.  Priority:-1 extents:1 across:1172704k
Oct 31 02:19:34 miniub kernel: [   34.114972] EXT3 FS on sda6, internal journal
Oct 31 02:19:34 miniub kernel: [   35.346984] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 31 02:19:34 miniub kernel: [   35.898679] NET: Registered protocol family 10
Oct 31 02:19:34 miniub kernel: [   35.898869] lo: Disabled Privacy Extensions
Oct 31 02:19:34 miniub kernel: [   36.408272] No dock devices found.
Oct 31 02:19:35 miniub ntpdate[4454]: step time server 91.189.94.4 offset 0.597251 sec
Oct 31 02:19:36 miniub NetworkManager: <info>  starting... 
Oct 31 02:19:36 miniub avahi-daemon[4833]: Found user 'avahi' (UID 105) and group 'avahi' (GID 115).
Oct 31 02:19:36 miniub avahi-daemon[4833]: Successfully dropped root privileges.
Oct 31 02:19:36 miniub avahi-daemon[4833]: avahi-daemon 0.6.22 starting up.
Oct 31 02:19:36 miniub avahi-daemon[4833]: Successfully called chroot().
Oct 31 02:19:36 miniub avahi-daemon[4833]: Successfully dropped remaining capabilities.
Oct 31 02:19:36 miniub avahi-daemon[4833]: No service file found in /etc/avahi/services.
Oct 31 02:19:36 miniub avahi-daemon[4833]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
Oct 31 02:19:36 miniub avahi-daemon[4833]: New relevant interface eth0.IPv4 for mDNS.
Oct 31 02:19:36 miniub avahi-daemon[4833]: Network interface enumeration completed.
Oct 31 02:19:36 miniub avahi-daemon[4833]: Registering new address record for fe80::216:d3ff:feae:e1cb on eth0.*.
Oct 31 02:19:36 miniub avahi-daemon[4833]: Registering new address record for 192.168.1.101 on eth0.IPv4.
Oct 31 02:19:36 miniub avahi-daemon[4833]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 31 02:19:36 miniub kernel: [   37.970912] ppdev: user-space parallel port driver
Oct 31 02:19:36 miniub kernel: [   38.443917] audit(1225426776.992:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4860 profile="/usr/sbin/cupsd" namespace="default"
Oct 31 02:19:37 miniub avahi-daemon[4833]: Server startup complete. Host name is miniub.local. Local service cookie is 895977184.
Oct 31 02:19:37 miniub dhcdbd: Started up.
Oct 31 02:19:38 miniub NetworkManager: <debug> [1225426778.735271] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CD_RW_CRX880A'). 
Oct 31 02:19:38 miniub /usr/sbin/cron[5058]: (CRON) INFO (pidfile fd = 3)
Oct 31 02:19:38 miniub /usr/sbin/cron[5059]: (CRON) STARTUP (fork ok)
Oct 31 02:19:38 miniub /usr/sbin/cron[5059]: (CRON) INFO (Running @reboot jobs)
Oct 31 02:19:44 miniub kernel: [   46.068302] eth0: no IPv6 routers present
Oct 31 02:19:48 miniub kernel: [   49.934837] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
Oct 31 02:19:48 miniub kernel: [   49.934842] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
Oct 31 02:19:48 miniub kernel: [   49.935513] atkbd.c: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
Oct 31 02:19:48 miniub kernel: [   49.935517] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
Oct 31 02:20:06 miniub NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 31 02:25:45 miniub syslogd 1.5.0#1ubuntu1: restart.
```

any ideas?

---

### Post by FFe_ on 2008-10-31
bump?

---

