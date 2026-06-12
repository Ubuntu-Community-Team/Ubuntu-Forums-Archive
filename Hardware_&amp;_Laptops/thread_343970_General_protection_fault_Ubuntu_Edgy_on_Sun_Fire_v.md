---
title: "General protection fault: Ubuntu Edgy on Sun Fire v40z server"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by barwil on 2007-01-22
Hi all, 

I've installed Edgy on a new server Sun Fire v40z sporting 8 dual core opterons 880.

The installer run fine (I've used the alternate install iso and installed the "command line" version of the system), however when the machine boots I can see a kernel OOOPS (output from dmesg below). Even more interestingly I can see a login prompt and after some tweaking (remounting file systems in read/write, starting networking ) the server seems to run fine. 

Any ideas what may be the cause ?

regards Bartek


Output of dmesg with the oops:

[    0.000000] Bootdata ok (command line is root=/dev/mapper/Ubuntu-root ro console=ttyS0,57600n8 )
[    0.000000] Linux version 2.6.17-10-generic (root@crested) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 15:34:39 U
TC 2006 (Ubuntu 2.6.17-10.33-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b000 (usable)
[    0.000000]  BIOS-e820: 000000000009b000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000fbf70000 (usable)
[    0.000000]  BIOS-e820: 00000000fbf70000 - 00000000fbf77000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fbf77000 - 00000000fbf80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fbf80000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000400000000 (usable)
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v002 PTLTD                                 ) @ 0x00000000000f7820
[    0.000000] ACPI: XSDT (v001 PTLTD    XSDT   0x06040000  LTP 0x00000000) @ 0x00000000fbf71241
[    0.000000] ACPI: FADT (v003 SUN    V40z     0x06040000 PTEC 0x000f4240) @ 0x00000000fbf76314
[    0.000000] ACPI: HPET (v001 Sun    V40z     0x06040000 PTEC 0x00000000) @ 0x00000000fbf76408
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x00000000fbf76440
[    0.000000] ACPI: SPCR (v001 PTLTD  $UCRTBL$ 0x06040000 PTL  0x00000001) @ 0x00000000fbf7653a
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x00000000fbf7658a
[    0.000000] ACPI: SSDT (v001 SUN    FireV40z 0x06040000  LTP 0x00000001) @ 0x00000000fbf76d4e
[    0.000000] ACPI: SSDT (v001 SUN    FireV40z 0x06040000  LTP 0x00000001) @ 0x00000000fbf76deb
[    0.000000] ACPI: SRAT (v001 SUN    FireV40z 0x06040000 SUN  0x00000001) @ 0x00000000fbf76e88
[    0.000000] ACPI: DSDT (v001   Sun      V40z 0x06040000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] SRAT: PXM 0 -> APIC 0 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 1 -> Node 0
[    0.000000] SRAT: PXM 1 -> APIC 2 -> Node 1
[    0.000000] SRAT: PXM 1 -> APIC 3 -> Node 1
[    0.000000] SRAT: PXM 2 -> APIC 4 -> Node 2
[    0.000000] SRAT: PXM 2 -> APIC 5 -> Node 2
[    0.000000] SRAT: PXM 3 -> APIC 6 -> Node 3
[    0.000000] SRAT: PXM 3 -> APIC 7 -> Node 3
[    0.000000] SRAT: Node 0 PXM 0 0-a0000
[    0.000000] SRAT: Node 0 PXM 0 0-fc000000
[    0.000000] SRAT: Node 1 PXM 1 100000000-200000000
[    0.000000] SRAT: Node 2 PXM 2 200000000-300000000
[    0.000000] SRAT: Node 3 PXM 3 300000000-400000000
[    0.000000] NUMA: Using 32 for the hash shift.
[    0.000000] Bootmem setup node 0 0000000000000000-00000000fc000000
[    0.000000] Bootmem setup node 1 0000000100000000-0000000200000000
[    0.000000] Bootmem setup node 2 0000000200000000-0000000300000000
[    0.000000] Bootmem setup node 3 0000000300000000-0000000400000000
[    0.000000] On node 0 totalpages: 1016470
[    0.000000]   DMA zone: 2574 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 1013896 pages, LIFO batch:31
[    0.000000] On node 1 totalpages: 1034240
[    0.000000]   Normal zone: 1034240 pages, LIFO batch:31
[    0.000000] On node 2 totalpages: 1034240
[    0.000000]   Normal zone: 1034240 pages, LIFO batch:31
[    0.000000] On node 3 totalpages: 1034240
[    0.000000]   Normal zone: 1034240 pages, LIFO batch:31
 [    0.000000] ACPI: PM-Timer IO Port: 0xf008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:1 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:1 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] Processor #2 15:1 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] Processor #3 15:1 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] enabled)
[    0.000000] Processor #4 15:1 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] enabled)
[    0.000000] Processor #5 15:1 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] enabled)
[    0.000000] Processor #6 15:1 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] enabled)
[    0.000000] Processor #7 15:1 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x09] address[0xfc800000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 9, version 17, address 0xfc800000, GSI 24-27
[    0.000000] ACPI: IOAPIC (id[0x0a] address[0xfc801000] gsi_base[28])
[    0.000000] IOAPIC[2]: apic_id 10, version 17, address 0xfc801000, GSI 28-31
[    0.000000] ACPI: IOAPIC (id[0x0b] address[0xfe501000] gsi_base[32])
[    0.000000] IOAPIC[3]: apic_id 11, version 17, address 0xfe501000, GSI 32-35
[    0.000000] ACPI: IOAPIC (id[0x0c] address[0xfe503000] gsi_base[36])
[    0.000000] IOAPIC[4]: apic_id 12, version 17, address 0xfe503000, GSI 36-39
[    0.000000] ACPI: IOAPIC (id[0x0d] address[0xfe505000] gsi_base[40])
[    0.000000] IOAPIC[5]: apic_id 13, version 17, address 0xfe505000, GSI 40-43
[    0.000000] ACPI: IOAPIC (id[0x0e] address[0xfe507000] gsi_base[44])
[    0.000000] IOAPIC[6]: apic_id 14, version 17, address 0xfe507000, GSI 44-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] ACPI: HPET id: 0x102282a0 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at fc400000 (gap: fc000000:2c00000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ 0 size 32 MB
[    0.000000] No AGP bridge found
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 4000000
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] Built 4 zonelists
[    0.000000] Kernel command line: root=/dev/mapper/Ubuntu-root ro console=ttyS0,57600n8 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] time.c: Using 14.318180 MHz WALL HPET GTOD HPET timer.
[    0.000000] time.c: Detected 2389.497 MHz processor.
[  120.873126] Console: colour VGA+ 80x25
[  121.899949] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[  121.927057] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[  122.555442] Memory: 16379416k/16777216k available (2129k kernel code, 331284k reserved, 1424k data, 188k init)
[  122.655610] Calibrating delay using timer specific routine.. 4785.58 BogoMIPS (lpj=9571173)
[  122.672427] Security Framework v1.0.0 initialized
[  122.681822] SELinux:  Disabled at boot.
[  122.689541] Mount-cache hash table entries: 256
[  122.698763] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[  122.712989] CPU: L2 Cache: 1024K (64 bytes/line)
[  122.722213] CPU 0/0(2) -> Node 0 -> Core 0
[  122.730392] SMP alternatives: switching to UP code
[  122.740166] checking if image is initramfs... it is
[  123.259593] Freeing initrd memory: 6476k freed
[  123.271975] ACPI: Core revision 20060707
[  123.280128] ACPI: Looking for DSDT ... not found!
[  123.332355] Using local APIC timer interrupts.
[  123.383017] result 12445312
[  123.388581] Detected 12.445 MHz APIC timer.
[  123.398906] SMP alternatives: switching to SMP code
[  123.408723] Booting processor 1/8 APIC 0x1
[  123.427189] Initializing CPU#1
[  123.506417] Calibrating delay using timer specific routine.. 4778.36 BogoMIPS (lpj=9556724)
[  123.506424] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[  123.506426] CPU: L2 Cache: 1024K (64 bytes/line)
[  123.506428] CPU 1/1(2) -> Node 0 -> Core 1
[  123.506535] Dual Core AMD Opteron(tm) Processor 880 stepping 02
[  123.510410] CPU 1: Syncing TSC to CPU 0.
[  123.510538] CPU 1: synchronized TSC with CPU 0 (last diff 6 cycles, maxerr 842 cycles)
[  123.510782] SMP alternatives: switching to SMP code
[  123.610293] Booting processor 2/8 APIC 0x2
[  123.628770] Initializing CPU#2
[  123.706139] Calibrating delay using timer specific routine.. 4778.45 BogoMIPS (lpj=9556918)
[  123.706146] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[  123.706148] CPU: L2 Cache: 1024K (64 bytes/line)
[  123.706151] CPU 2/2(2) -> Node 1 -> Core 0
[  123.706261] Dual Core AMD Opteron(tm) Processor 880 stepping 02
[  123.710132] CPU 2: Syncing TSC to CPU 0.
[  123.710261] CPU 2: synchronized TSC with CPU 0 (last diff -121 cycles, maxerr 886 cycles)
[  123.710491] SMP alternatives: switching to SMP code
[  123.810522] Booting processor 3/8 APIC 0x3
[  123.828981] Initializing CPU#3
[  123.909853] Calibrating delay using timer specific routine.. 4778.39 BogoMIPS (lpj=9556790)
[  123.909860] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[  123.909862] CPU: L2 Cache: 1024K (64 bytes/line)
[  123.909864] CPU 3/3(2) -> Node 1 -> Core 1
[  123.909974] Dual Core AMD Opteron(tm) Processor 880 stepping 02
[  123.913845] CPU 3: Syncing TSC to CPU 0.
[  123.913975] CPU 3: synchronized TSC with CPU 0 (last diff -122 cycles, maxerr 886 cycles)
[  123.914227] SMP alternatives: switching to SMP code
[  124.014250] Booting processor 4/8 APIC 0x4
[  124.032709] Initializing CPU#4
[  124.113566] Calibrating delay using timer specific routine.. 4778.38 BogoMIPS (lpj=9556773)
[  124.113573] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[  124.113575] CPU: L2 Cache: 1024K (64 bytes/line)
[  124.113578] CPU 4/4(2) -> Node 2 -> Core 0
[  124.113689] Dual Core AMD Opteron(tm) Processor 880 stepping 02
[  124.117558] CPU 4: Syncing TSC to CPU 0.
[  124.117690] CPU 4: synchronized TSC with CPU 0 (last diff -127 cycles, maxerr 912 cycles)
[  124.117928] SMP alternatives: switching to SMP code
[  124.217956] Booting processor 5/8 APIC 0x5
[  124.236413] Initializing CPU#5
[  124.317278] Calibrating delay using timer specific routine.. 4778.45 BogoMIPS (lpj=9556916)
[  124.317285] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[  124.317287] CPU: L2 Cache: 1024K (64 bytes/line)
[  124.317290] CPU 5/5(2) -> Node 2 -> Core 1
[  124.317399] Dual Core AMD Opteron(tm) Processor 880 stepping 02
[  124.321272] CPU 5: Syncing TSC to CPU 0.
[  124.321404] CPU 5: synchronized TSC with CPU 0 (last diff -115 cycles, maxerr 890 cycles)
[  124.321650] SMP alternatives: switching to SMP code
[  124.421684] Booting processor 6/8 APIC 0x6
[  124.440146] Initializing CPU#6
[  124.520996] Calibrating delay using timer specific routine.. 4778.55 BogoMIPS (lpj=9557102)
[  124.521003] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[  124.521005] CPU: L2 Cache: 1024K (64 bytes/line)
[  124.521008] CPU 6/6(2) -> Node 3 -> Core 0
[  124.521125] Dual Core AMD Opteron(tm) Processor 880 stepping 02
[  124.524989] CPU 6: Syncing TSC to CPU 0.
[  124.525206] CPU 6: synchronized TSC with CPU 0 (last diff -162 cycles, maxerr 1548 cycles)
[  124.525438] SMP alternatives: switching to SMP code
[  124.625641] Booting processor 7/8 APIC 0x7
[  124.644101] Initializing CPU#7
[  124.724717] Calibrating delay using timer specific routine.. 4778.62 BogoMIPS (lpj=9557249)
[  124.724724] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[  124.724726] CPU: L2 Cache: 1024K (64 bytes/line)
[  124.724729] CPU 7/7(2) -> Node 3 -> Core 1
[  124.724846] Dual Core AMD Opteron(tm) Processor 880 stepping 02
[  124.728710] CPU 7: Syncing TSC to CPU 0.
[  124.728928] CPU 7: synchronized TSC with CPU 0 (last diff -164 cycles, maxerr 1548 cycles)
[  124.728933] Brought up 8 CPUs
[  124.825333] testing NMI watchdog ... OK.
[  125.695208] migration_cost=349,433
[  125.702683] NET: Registered protocol family 16
[  125.711584] ACPI: bus type pci registered
[  125.719588] PCI: Using configuration type 1
[  125.734804] ACPI: Interpreter enabled
[  125.742118] ACPI: Using IOAPIC for interrupt routing
[  125.753293] ACPI: PCI Root Bridge [PCI0] (0000:00)
[  125.762852] PCI: Probing PCI hardware (bus 00)
[  125.773138] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
[  125.785510] Boot video device is 0000:01:05.0
[  125.801690] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 5 *10 11)
[  125.813752] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *5 10 11)
[  125.825799] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 5 10 11) *7
[  125.838228] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 5 10 *11)
[  125.851885] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.THOR._PRT]
[  125.852561] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.Z000._PRT]
[  125.852884] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.Z002._PRT]
[  125.853174] ACPI: PCI Root Bridge [PCI1] (0000:20)
[  125.862730] PCI: Probing PCI hardware (bus 20)
[  125.873835] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[  125.876490] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1.Z003._PRT]
[  125.876853] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1.Z004._PRT]
[  125.877217] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1.Z005._PRT]
[  125.877582] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1.Z006._PRT]
[  125.877852] Linux Plug and Play Support v0.97 (c) Adam Belay
[  125.889151] pnp: PnP ACPI init
[  125.905235] GSI 16 sharing vector 0xA9 and IRQ 16
[  125.914614] Losing some ticks... checking if CPU frequency changed.
[  125.920655] pnp: PnP ACPI: found 15 devices
[  125.929055] PCI: Using ACPI for IRQ routing
[  125.937409] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[  125.953997] hpet0: at MMIO 0xfed00000 (virtual 0xffffffffff5fe000), IRQs 2, 8, 0
[  125.968884] hpet0: 3 32-bit timers, 14318180 Hz
[  125.978988] PCI-DMA: Disabling AGP.
[  125.985996] PCI-DMA: aperture base @ 4000000 size 65536 KB
[  125.996945] PCI-DMA: using GART IOMMU.
[  126.004421] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[  126.017640] pnp: 00:09: ioport range 0x4d0-0x4d1 has been reserved
[  126.029966] pnp: 00:09: ioport range 0x1100-0x117f has been reserved
[  126.042633] pnp: 00:09: ioport range 0x1180-0x11ff has been reserved
[  126.055658] PCI: Bridge: 0000:00:06.0
[  126.062969]   IO window: disabled.
[  126.069756]   MEM window: fc900000-fdffffff
[  126.078098]   PREFETCH window: fc400000-fc4fffff
[  126.087309] PCI: Failed to allocate mem resource #6:100000@fe500000 for 0000:02:04.0
[  126.102759] PCI: Bridge: 0000:02:05.0
[  126.110060]   IO window: disabled.
[  126.116846]   MEM window: fe100000-fe1fffff
[  126.125188]   PREFETCH window: fe400000-fe4fffff
[  126.134396] PCI: Bridge: 0000:00:0a.0
[  126.141697]   IO window: 2000-2fff
[  126.148483]   MEM window: fe000000-fe1fffff
[  126.156824]   PREFETCH window: fe400000-fe4fffff
[  126.166031] PCI: Bridge: 0000:00:0b.0
[  126.173334]   IO window: disabled.
[  126.180120]   MEM window: disabled.
[  126.187077]   PREFETCH window: disabled.
[  126.194929] PCI: Bridge: 0000:20:01.0
[  126.202236]   IO window: disabled.
[  126.209022]   MEM window: disabled.
[  126.215979]   PREFETCH window: disabled.
[  126.223803] PCI: Bridge: 0000:20:02.0
[  126.231105]   IO window: disabled.
[  126.237891]   MEM window: disabled.
[  126.244848]   PREFETCH window: disabled.
[  126.252672] PCI: Bridge: 0000:20:03.0
[  126.259972]   IO window: disabled.
[  126.266759]   MEM window: disabled.
[  126.273716]   PREFETCH window: disabled.
[  126.281538] PCI: Bridge: 0000:20:04.0
[  126.288840]   IO window: disabled.
[  126.295629]   MEM window: disabled.
[  126.302584]   PREFETCH window: disabled.
[  126.310421] GSI 17 sharing vector 0xB1 and IRQ 17
[  126.319804] ACPI: PCI Interrupt 0000:20:01.0[A] -> GSI 32 (level, low) -> IRQ 177
[  126.334769] GSI 18 sharing vector 0xB9 and IRQ 18
[  126.344155] ACPI: PCI Interrupt 0000:20:02.0[A] -> GSI 36 (level, low) -> IRQ 185
[  126.359122] GSI 19 sharing vector 0xC1 and IRQ 19
[  126.368507] ACPI: PCI Interrupt 0000:20:03.0[A] -> GSI 40 (level, low) -> IRQ 193
[  126.383474] GSI 20 sharing vector 0xC9 and IRQ 20
[  126.392857] ACPI: PCI Interrupt 0000:20:04.0[A] -> GSI 44 (level, low) -> IRQ 201
[  126.407952] NET: Registered protocol family 2
[  126.454790] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
[  126.471628] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[  126.489208] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[  126.503243] TCP: Hash tables configured (established 262144 bind 65536)
[  126.516431] TCP reno registered
[  126.524071] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[  126.539133] audit: initializing netlink socket (disabled)
[  126.549911] audit(1168945124.688:1): initialized
[  126.559677] VFS: Disk quotas dquot_6.5.1
[  126.567538] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[  126.580468] Initializing Cryptographic API
[  126.588639] io scheduler noop registered
[  126.596509] io scheduler anticipatory registered
[  126.605766] io scheduler deadline registered
[  126.614379] io scheduler cfq registered (default)
[  126.623835] PCI: MSI quirk detected. PCI_BUS_FLAGS_NO_MSI set for subordinate bus.
[  126.638930] PCI: MSI quirk detected. PCI_BUS_FLAGS_NO_MSI set for subordinate bus.
[  126.654036] PCI: MSI quirk detected. PCI_BUS_FLAGS_NO_MSI set for subordinate bus.
[  126.669131] PCI: MSI quirk detected. PCI_BUS_FLAGS_NO_MSI set for subordinate bus.
[  126.684221] PCI: MSI quirk detected. PCI_BUS_FLAGS_NO_MSI set for subordinate bus.
[  126.699311] PCI: MSI quirk detected. PCI_BUS_FLAGS_NO_MSI set for subordinate bus.
[  126.744608] Real Time Clock Driver v1.12ac
[  126.752940] hpet_resources: 0xfed00000 is busy
[  126.752956] Linux agpgart interface v0.101 (c) Dave Jones
[  126.763721] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[  126.779309] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  126.791439] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[  126.803967] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  126.815332] mice: PS/2 mouse device common for all mice
[  126.826617] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  126.841859] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  126.854531] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  126.870788] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[  126.887733] serio: i8042 AUX port at 0x60,0x64 irq 12
[  126.897873] serio: i8042 KBD port at 0x60,0x64 irq 1
[  126.907915] TCP bic registered
[  126.914035] NET: Registered protocol family 1
[  126.922720] NET: Registered protocol family 8
[  126.931403] NET: Registered protocol family 20
[  126.940400] ACPI: (supports S0 S1 S5)
[  126.947865] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[  126.960382] Freeing unused kernel memory: 188k freed
[  127.015564] Capability LSM initialized
[  127.088215] input: AT Translated Set 2 keyboard as /class/input/input0
[  127.261412] AMD8111: IDE controller at PCI slot 0000:00:07.1
[  127.272716] AMD8111: chipset revision 3
[  127.280369] AMD8111: not 100% native mode: will probe irqs later
[  127.292351] AMD8111: 0000:00:07.1 (rev 03) UDMA133 controller
[  127.303811]     ide0: BM-DMA at 0x1000-0x1007, BIOS settings: hda:pio, hdb:pio
[  127.318272]     ide1: BM-DMA at 0x1008-0x100f, BIOS settings: hdc:DMA, hdd:pio
[  127.332740] Probing IDE interface ide0...
[  127.900840] Probing IDE interface ide1...
[  128.636021] hdc: MATSHITADVD-ROM SR-8178, ATAPI CD/DVD-ROM drive
[  128.984011] ide1 at 0x170-0x177,0x376 on irq 15
[  128.999830] hdc: ATAPI 24X DVD-ROM drive, 256kB Cache, UDMA(33)
[  129.011841] Uniform CD-ROM driver Revision: 3.20
[  129.089380] SCSI subsystem initialized
[  129.099372] Fusion MPT base driver 3.03.09
[  129.107544] Copyright (c) 1999-2005 LSI Logic Corporation
[  129.120814] Fusion MPT SPI Host driver 3.03.09
[  129.129733] GSI 21 sharing vector 0xD1 and IRQ 21
[  129.139119] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 27 (level, low) -> IRQ 209
[  129.154110] mptbase: Initiating ioc0 bringup
[  129.634653] ioc0: 53C1030: Capabilities={Initiator}
[  130.301884] scsi0 : ioc0: LSI53C1030, FwRev=01032920h, Ports=1, MaxQ=222, IRQ=209
[  130.702429] megaraid cmm: 2.20.2.6 (Release Date: Mon Mar 7 00:01:03 EST 2005)
[  130.717619] megaraid: 2.20.4.8 (Release Date: Mon Apr 11 12:27:22 EST 2006)
[  130.731536] megaraid: probe new device 0x1000:0x0407:0x1000:0x0532: bus 3:slot 0:func 0
[  130.747545] GSI 22 sharing vector 0xD9 and IRQ 22
[  130.756927] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 24 (level, low) -> IRQ 217
[  130.789217] megaraid: fw version:[413Y] bios version:[H420]
[  130.800732] scsi1 : LSI Logic MegaRAID driver
[  130.809655] scsi[1]: scanning scsi channel 0 [Phy 0] for non-raid devices
[  130.823401] Probing IDE interface ide0...
[  130.841980] usbcore: registered new driver usbfs
[  130.851213] usbcore: registered new driver hub
[  130.860907] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[  130.860942] ACPI: PCI Interrupt 0000:01:00.0[D] -> GSI 19 (level, low) -> IRQ 169
[  130.876372] ohci_hcd 0000:01:00.0: OHCI Host Controller
[  130.886987] ohci_hcd 0000:01:00.0: new USB bus registered, assigned bus number 1
[  131.104795] ohci_hcd 0000:01:00.0: irq 169, io mem 0xfc900000
[  131.174772] usb usb1: configuration #1 chosen from 1 choice
[  131.185894] hub 1-0:1.0: USB hub found
[  131.193377] hub 1-0:1.0: 3 ports detected
[  131.304564] ACPI: PCI Interrupt 0000:01:00.1[D] -> GSI 19 (level, low) -> IRQ 169
[  131.319692] ohci_hcd 0000:01:00.1: OHCI Host Controller
[  131.330180] ohci_hcd 0000:01:00.1: new USB bus registered, assigned bus number 2
[  131.548231] ohci_hcd 0000:01:00.1: irq 169, io mem 0xfc901000
[  131.618213] usb usb2: configuration #1 chosen from 1 choice
[  131.629341] hub 2-0:1.0: USB hub found
[  131.636824] hub 2-0:1.0: 3 ports detected
[  131.779299] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [email]dm-devel@redhat.com[/email]
[  134.795913] scsi[1]: scanning scsi channel 1 [Phy 1] for non-raid devices
[  135.111583]   Vendor: SDR       Model: GEM318P           Rev: 1   
[  135.124973]   Type:   Processor                          ANSI SCSI revision: 02
[  137.139379] scsi[1]: scanning scsi channel 2 [virtual] for logical drives
[  137.153104]   Vendor: MegaRAID  Model: LD 0 RAID5 1140G  Rev: 413Y
[  137.166503]   Type:   Direct-Access                      ANSI SCSI revision: 02
[  137.188523] SCSI device sda: 2335932416 512-byte hdwr sectors (1195997 MB)
[  137.202240] sda: Write Protect is off
[  137.209548] sda: Mode Sense: 00 00 00 00
[  137.209557] sda: asking for cache data failed
[  137.218250] sda: assuming drive cache: write through
[  137.228314] SCSI device sda: 2335932416 512-byte hdwr sectors (1195997 MB)
[  137.242035] sda: Write Protect is off
[  137.249345] sda: Mode Sense: 00 00 00 00
[  137.249353] sda: asking for cache data failed
[  137.258047] sda: assuming drive cache: write through
[  137.267954]  sda: sda1 sda2 < sda5 sda6 >
[  137.295746] sd 1:2:0:0: Attached scsi disk sda
[  138.635872] Attempting manual resume
[  138.652705] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[  138.672545] SGI XFS Quota Management subsystem
[  138.689892] XFS mounting filesystem dm-0
[  138.813440] Ending clean XFS mount for filesystem: dm-0
[  141.162305] input: PC Speaker as /class/input/input1
[  141.210476] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  141.230597] Floppy drive(s): fd0 is 1.44M
[  141.260123] FDC 0 is a post-1991 82077
[  141.268062] shpchp: HPC vendor_id 1022 device_id 7460 ss_vid 0 ss_did 0
[  141.281883] shpchp: shpc_init: cannot reserve MMIO region
[  141.292856] shpchp: HPC vendor_id 1022 device_id 7450 ss_vid 0 ss_did 0
[  141.306099] shpchp: shpc_init: cannot reserve MMIO region
[  141.316881] shpchp: HPC vendor_id 1022 device_id 7450 ss_vid 0 ss_did 0
[  141.330093] shpchp: shpc_init: cannot reserve MMIO region
[  141.346141] shpchp: HPC vendor_id 1022 device_id 7450 ss_vid 0 ss_did 0
[  141.359348] ACPI: PCI Interrupt 0000:20:01.0[A] -> GSI 32 (level, low) -> IRQ 177
[  141.374355] hw_random: AMD768 system management I/O registers at 0xF000.
[  141.374416] general protection fault: 0000 [1] SMP 
[  141.374419] CPU 2 
[  141.374421] Modules linked in: hw_random i2c_amd756 shpchp i2c_core serio_raw floppy pci_hotplug psmouse evdev pcspkr xfs sd_mod dm_mod ohci_hcd usbcore i
de_generic megaraid_mbox megaraid_mm mptspi mptscsih mptbase scsi_transport_spi scsi_mod ide_cd cdrom generic amd74xx thermal processor fan fbcon tileblit fo
nt bitblit softcursor vesafb cfbcopyarea cfbimgblt cfbfillrect capability commoncap
[  141.374434] Pid: 3520, comm: modprobe Not tainted 2.6.17-10-generic #2
[  141.374437] RIP: 0010:[<ffffffff803340d2>] <ffffffff803340d2>{strlen+2}
[  141.374445] RSP: 0018:ffff8100fb433c80  EFLAGS: 00010246
[  141.374447] RAX: 0000000000000000 RBX: ffffffff805e32b0 RCX: 00000000fffffff4
[  141.374450] RDX: 0000000000000000 RSI: babababababababa RDI: babababababababa
[  141.374453] RBP: ffffffff80632a00 R08: 0000000000029000 R09: 0000000000000000
[  141.374455] R10: 0000000000000000 R11: 0000000000000003 R12: babababababababa
[  141.374457] R13: ffff8100099cf800 R14: 0000000000000001 R15: 0000000000000000
[  141.374460] FS:  00002b801a3f66d0(0000) GS:ffff8101fc73e540(0000) knlGS:0000000000000000
[  141.374462] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  141.374465] CR2: 00002ae32478c000 CR3: 00000001fbdb2000 CR4: 00000000000006e0
[  141.374468] Process modprobe (pid: 3520, threadinfo ffff8100fb432000, task ffff810037edb0e0)
[  141.374469] Stack: ffffffff80334200 0000000000000000 ffffffff80632a00 0000000000000000 
[  141.374476]        ffffffff803aff83 ffff8100099cf800 0000000000000001 00000000000000b1 
[  141.374480]        ffffffff80342c00 00000000fe4d8000 
[  141.374484] Call Trace: <ffffffff80334200>{strstr+32} <ffffffff803aff83>{dmi_check_system+51}
[  141.374494]        <ffffffff80342c00>{msi_init+32} <ffffffff80343993>{pci_enable_msi+99}
[  141.374503]        <ffffffff8820987a>{:shpchp:shpc_init+1626} <ffffffff80269ebc>{cond_resched+60}
[  141.374518]        <ffffffff80269f0f>{wait_for_completion+31} <ffffffff88205703>{:shpchp:shpc_probe+147}
[  141.374532]        <ffffffff8033ea83>{pci_device_probe+243} <ffffffff80393685>{driver_probe_device+101}
[  141.374541]        <ffffffff80393802>{__driver_attach+114} <ffffffff80393790>{__driver_attach+0}
[  141.374547]        <ffffffff80392f19>{bus_for_each_dev+73} <ffffffff80392abd>{bus_add_driver+141}
[  141.374556]        <ffffffff8033ed07>{__pci_register_driver+87} <ffffffff880ce036>{:shpchp:shpcd_init+54}
[  141.374565]        <ffffffff802a8eb7>{sys_init_module+199} <ffffffff8026580e>{system_call+126}
[  141.374578] 
[  141.374579] Code: 80 3f 00 74 15 48 89 f8 66 66 90 66 66 90 48 83 c0 01 80 38 
[  141.374586] RIP <ffffffff803340d2>{strlen+2} RSP <ffff8100fb433c80>
[  141.374590]  <6>hw_random hardware driver 1.0.0 loaded
[  186.110004] ACPI: Power Button (FF) [PWRF]
[  186.110014] ACPI: Power Button (CM) [PWRB]
[  186.208566] ibm_acpi: ec object not found
[  186.241615] pcc_acpi: loading...
[  295.960778] NET: Registered protocol family 17
[  320.535697] Filesystem "dm-0": Disabling barriers, not supported by the underlying device
[  320.771032] tg3.c:v3.59.1 (August 25, 2006)
[  320.779429] GSI 23 sharing vector 0xE1 and IRQ 23
[  320.788857] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 25 (level, low) -> IRQ 225
[  320.836881] eth0: Tigon3 [partno(BCM95704A6) rev 2003 PHY(5704)] (PCIX:66MHz:64-bit) 10/100/1000BaseT Ethernet 00:09:3d:14:c2:26
[  320.860144] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[  320.876798] eth0: dma_rwctrl[769f0000] dma_mask[64-bit]
[  320.887257] GSI 24 sharing vector 0xE9 and IRQ 24
[  320.896647] ACPI: PCI Interrupt 0000:02:02.1[B] -> GSI 26 (level, low) -> IRQ 233
[  320.951311] eth1: Tigon3 [partno(BCM95704A6) rev 2003 PHY(5704)] (PCIX:66MHz:64-bit) 10/100/1000BaseT Ethernet 00:09:3d:14:c2:27
[  320.974584] eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[  320.991238] eth1: dma_rwctrl[769f0000] dma_mask[64-bit]
[  341.137478] PM: Writing back config space on device 0000:02:02.0 at offset b (was 164814e4, writing 1017c2)
[  341.156912] PM: Writing back config space on device 0000:02:02.0 at offset 3 (was 804000, writing 804010)
[  341.175994] PM: Writing back config space on device 0000:02:02.0 at offset 2 (was 2000000, writing 2000003)
[  341.195410] PM: Writing back config space on device 0000:02:02.0 at offset 1 (was 2b00000, writing 2b00146)
[  343.011152] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  343.022272] tg3: eth0: Flow control is off for TX and off for RX.
[  346.742405] NET: Registered protocol family 10
[  346.751463] lo: Disabled Privacy Extensions
[  346.759945] IPv6 over IPv4 tunneling driver
[  357.082013] eth0: no IPv6 routers present
[  500.501333]  1:1:6:0: Attached scsi generic sg0 type 3
[  500.511630] sd 1:2:0:0: Attached scsi generic sg1 type 0
[  935.029294] Filesystem "dm-1": Disabling barriers, not supported by the underlying device
[  935.059128] XFS mounting filesystem dm-1
[  935.383423] Ending clean XFS mount for filesystem: dm-1
[ 1000.277538] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[ 1000.289526] md: bitmap version 4.39

---

