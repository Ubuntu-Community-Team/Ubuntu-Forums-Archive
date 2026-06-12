---
title: "computer freezes seems hardware problem"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by sotanez on 2008-03-04
Hi.
Since a few months ago my computer freezes ocasionally without a visible pattern, and it seems a hardware problem.
When my computer freezes, the monitor displays an unintelligible mesh of colors and the only thing I can do is reboot the computer.

My computer is an AMD Athlon 64 Processor 3500+ and I'm using Kubuntu 7.04 for 64 bits.

I've checked the RAM, voltages and temperatures and does not seem to have problems.

Here is the kern.log of the last session until the computer froze at about 12:45:

-------------------------------------------------------------------------------------------------
Mar  4 10:57:28 karmapolice kernel: Inspecting /boot/System.map-2.6.22-14-generic
Mar  4 10:57:29 karmapolice kernel: Loaded 26085 symbols from /boot/System.map-2.6.22-14-generic.
Mar  4 10:57:29 karmapolice kernel: Symbols match kernel version 2.6.22.
Mar  4 10:57:29 karmapolice kernel: No module symbols loaded - kernel modules not enabled. 
Mar  4 10:57:29 karmapolice kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 02:46:46 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
Mar  4 10:57:29 karmapolice kernel: [    0.000000] Command line: root=UUID=6e794f24-c932-4f88-98ba-d695e620328a ro quiet splash locale=es_ES
Mar  4 10:57:29 karmapolice kernel: [    0.000000] BIOS-provided physical RAM map:
Mar  4 10:57:29 karmapolice kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Mar  4 10:57:29 karmapolice kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Mar  4 10:57:29 karmapolice kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Mar  4 10:57:29 karmapolice kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
Mar  4 10:57:29 karmapolice kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Mar  4 10:57:29 karmapolice kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Mar  4 10:57:29 karmapolice kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Mar  4 10:57:29 karmapolice kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Mar  4 10:57:29 karmapolice kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Mar  4 10:57:29 karmapolice kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Mar  4 10:57:29 karmapolice kernel: [    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
Mar  4 10:57:29 karmapolice kernel: [    0.000000] end_pfn_map = 1048576
Mar  4 10:57:29 karmapolice kernel: [    0.000000] DMI 2.3 present.
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7910 checksum 0
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: RSDP 000F7910, 0014 (r0 K8T890)
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: RSDT 7FEE3040, 0034 (r1 K8T890 AWRDACPI 42302E31 AWRD        0)
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 K8T890 AWRDACPI 42302E31 AWRD        0)
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: DSDT 7FEE3180, 7932 (r1 K8T890 AWRDACPI     1000 MSFT  100000E)
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: FACS 7FEE0000, 0040
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: SSDT 7FEEABC0, 00F7 (r1 PTLTD  POWERNOW        1  LTP        1)
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: MCFG 7FEEAD00, 003C (r1 K8T890 AWRDACPI 42302E31 AWRD        0)
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: APIC 7FEEAB00, 0074 (r1 K8T890 AWRDACPI 42302E31 AWRD        0)
Mar  4 10:57:29 karmapolice kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Mar  4 10:57:29 karmapolice kernel: [    0.000000] No NUMA configuration found
Mar  4 10:57:29 karmapolice kernel: [    0.000000] Faking a node at 0000000000000000-000000007fee0000
Mar  4 10:57:29 karmapolice kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Mar  4 10:57:29 karmapolice kernel: [    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
Mar  4 10:57:29 karmapolice kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000007fee0000
Mar  4 10:57:29 karmapolice kernel: [    0.000000] Zone PFN ranges:
Mar  4 10:57:29 karmapolice kernel: [    0.000000]   DMA             0 ->     4096
Mar  4 10:57:29 karmapolice kernel: [    0.000000]   DMA32        4096 ->  1048576
Mar  4 10:57:29 karmapolice kernel: [    0.000000]   Normal    1048576 ->  1048576
Mar  4 10:57:29 karmapolice kernel: [    0.000000] early_node_map[2] active PFN ranges
Mar  4 10:57:29 karmapolice kernel: [    0.000000]     0:        0 ->      159
Mar  4 10:57:29 karmapolice kernel: [    0.000000]     0:      256 ->   524000
Mar  4 10:57:29 karmapolice kernel: [    0.000000] On node 0 totalpages: 523903
Mar  4 10:57:29 karmapolice kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Mar  4 10:57:29 karmapolice kernel: [    0.000000]   DMA zone: 1127 pages reserved
Mar  4 10:57:29 karmapolice kernel: [    0.000000]   DMA zone: 2816 pages, LIFO batch:0
Mar  4 10:57:29 karmapolice kernel: [    0.000000]   DMA32 zone: 7108 pages used for memmap
Mar  4 10:57:29 karmapolice kernel: [    0.000000]   DMA32 zone: 512796 pages, LIFO batch:31
Mar  4 10:57:29 karmapolice kernel: [    0.000000]   Normal zone: 0 pages used for memmap
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar  4 10:57:29 karmapolice kernel: [    0.000000] Processor #0 (Bootup-CPU)
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Mar  4 10:57:29 karmapolice kernel: [    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
Mar  4 10:57:29 karmapolice kernel: [    0.000000] IOAPIC[1]: apic_id 3, address 0xfecc0000, GSI 24-47
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: IRQ0 used by override.
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: IRQ2 used by override.
Mar  4 10:57:29 karmapolice kernel: [    0.000000] ACPI: IRQ9 used by override.
Mar  4 10:57:29 karmapolice kernel: [    0.000000] Setting APIC routing to flat
Mar  4 10:57:29 karmapolice kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar  4 10:57:29 karmapolice kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Mar  4 10:57:29 karmapolice kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Mar  4 10:57:29 karmapolice kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Mar  4 10:57:29 karmapolice kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
Mar  4 10:57:29 karmapolice kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Mar  4 10:57:29 karmapolice kernel: [    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
Mar  4 10:57:29 karmapolice kernel: [    0.000000] Built 1 zonelists.  Total pages: 515612
Mar  4 10:57:29 karmapolice kernel: [    0.000000] Kernel command line: root=UUID=6e794f24-c932-4f88-98ba-d695e620328a ro quiet splash locale=es_ES
Mar  4 10:57:29 karmapolice kernel: [    0.000000] Initializing CPU#0
Mar  4 10:57:29 karmapolice kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Mar  4 10:57:29 karmapolice kernel: [   24.664244] time.c: Detected 2200.133 MHz processor.
Mar  4 10:57:29 karmapolice kernel: [   24.666590] Console: colour VGA+ 80x25
Mar  4 10:57:29 karmapolice kernel: [   24.666605] Checking aperture...
Mar  4 10:57:29 karmapolice kernel: [   24.666608] CPU 0: aperture @ feba000000 size 128 MB
Mar  4 10:57:29 karmapolice kernel: [   24.666610] Aperture beyond 4GB. Ignoring.
Mar  4 10:57:29 karmapolice kernel: [   24.666614] AGP bridge at 00:00:00
Mar  4 10:57:29 karmapolice kernel: [   24.666619] Aperture from AGP @ c0000000 size 128 MB (APSIZE f20)
Mar  4 10:57:29 karmapolice kernel: [   24.686359] Memory: 2055012k/2096000k available (2274k kernel code, 40600k reserved, 1185k data, 296k init)
Mar  4 10:57:29 karmapolice kernel: [   24.686402] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Mar  4 10:57:29 karmapolice kernel: [   24.766153] Calibrating delay using timer specific routine.. 4405.44 BogoMIPS (lpj=8810898)
Mar  4 10:57:29 karmapolice kernel: [   24.766182] Security Framework v1.0.0 initialized
Mar  4 10:57:29 karmapolice kernel: [   24.766189] SELinux:  Disabled at boot.
Mar  4 10:57:29 karmapolice kernel: [   24.766334] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Mar  4 10:57:29 karmapolice kernel: [   24.767615] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Mar  4 10:57:29 karmapolice kernel: [   24.768231] Mount-cache hash table entries: 256
Mar  4 10:57:29 karmapolice kernel: [   24.768353] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Mar  4 10:57:29 karmapolice kernel: [   24.768355] CPU: L2 Cache: 512K (64 bytes/line)
Mar  4 10:57:29 karmapolice kernel: [   24.768358] CPU 0/0 -> Node 0
Mar  4 10:57:29 karmapolice kernel: [   24.768374] SMP alternatives: switching to UP code
Mar  4 10:57:29 karmapolice kernel: [   24.768609] Early unpacking initramfs... done
Mar  4 10:57:29 karmapolice kernel: [   25.034931] ACPI: Core revision 20070126
Mar  4 10:57:29 karmapolice kernel: [   25.034991] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Mar  4 10:57:29 karmapolice kernel: [   25.079071] Using local APIC timer interrupts.
Mar  4 10:57:29 karmapolice kernel: [   25.124486] result 12500758
Mar  4 10:57:29 karmapolice kernel: [   25.124487] Detected 12.500 MHz APIC timer.
Mar  4 10:57:29 karmapolice kernel: [   25.125867] Brought up 1 CPUs
Mar  4 10:57:29 karmapolice kernel: [   25.126198] NET: Registered protocol family 16
Mar  4 10:57:29 karmapolice kernel: [   25.126261] ACPI: bus type pci registered
Mar  4 10:57:29 karmapolice kernel: [   25.126267] PCI: Using configuration type 1
Mar  4 10:57:29 karmapolice kernel: [   25.127197] ACPI: EC: Look up EC in DSDT
Mar  4 10:57:29 karmapolice kernel: [   25.133768] ACPI: Interpreter enabled
Mar  4 10:57:29 karmapolice kernel: [   25.133773] ACPI: (supports S0 S1 S3 S4 S5)
Mar  4 10:57:29 karmapolice kernel: [   25.133793] ACPI: Using IOAPIC for interrupt routing
Mar  4 10:57:29 karmapolice kernel: [   25.141391] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar  4 10:57:29 karmapolice kernel: [   25.141399] PCI: Probing PCI hardware (bus 00)
Mar  4 10:57:29 karmapolice kernel: [   25.142185] PCI: enabled onboard AC97/MC97 devices
Mar  4 10:57:29 karmapolice kernel: [   25.142838] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar  4 10:57:29 karmapolice kernel: [   25.143123] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEXG._PRT]
Mar  4 10:57:29 karmapolice kernel: [   25.143219] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Mar  4 10:57:29 karmapolice kernel: [   25.143309] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
Mar  4 10:57:29 karmapolice kernel: [   25.143398] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
Mar  4 10:57:29 karmapolice kernel: [   25.143490] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
Mar  4 10:57:29 karmapolice kernel: [   25.214904] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12) *5
Mar  4 10:57:29 karmapolice kernel: [   25.215047] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.215190] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.215335] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.215471] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.215604] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.215737] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.215879] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 *11 12)
Mar  4 10:57:29 karmapolice kernel: [   25.216038] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
Mar  4 10:57:29 karmapolice kernel: [   25.216188] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
Mar  4 10:57:29 karmapolice kernel: [   25.216337] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
Mar  4 10:57:29 karmapolice kernel: [   25.216507] ACPI: PCI Interrupt Link [ALKD] (IRQs *23), disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.216576] Linux Plug and Play Support v0.97 (c) Adam Belay
Mar  4 10:57:29 karmapolice kernel: [   25.216588] pnp: PnP ACPI init
Mar  4 10:57:29 karmapolice kernel: [   25.216595] ACPI: bus type pnp registered
Mar  4 10:57:29 karmapolice kernel: [   25.221010] pnp: PnP ACPI: found 16 devices
Mar  4 10:57:29 karmapolice kernel: [   25.221012] ACPI: ACPI bus type pnp unregistered
Mar  4 10:57:29 karmapolice kernel: [   25.221054] PCI: Using ACPI for IRQ routing
Mar  4 10:57:29 karmapolice kernel: [   25.221056] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Mar  4 10:57:29 karmapolice kernel: [   25.221062] PCI: Cannot allocate resource region 8 of bridge 0000:00:03.0
Mar  4 10:57:29 karmapolice kernel: [   25.221120] PCI: Cannot allocate resource region 8 of bridge 0000:00:03.1
Mar  4 10:57:29 karmapolice kernel: [   25.221177] PCI: Cannot allocate resource region 8 of bridge 0000:00:03.3
Mar  4 10:57:29 karmapolice kernel: [   25.221320] NET: Registered protocol family 8
Mar  4 10:57:29 karmapolice kernel: [   25.221322] NET: Registered protocol family 20
Mar  4 10:57:29 karmapolice kernel: [   25.221371] agpgart: Detected AGP bridge 0
Mar  4 10:57:29 karmapolice kernel: [   25.226697] agpgart: AGP aperture is 128M @ 0xc0000000
Mar  4 10:57:29 karmapolice kernel: [   25.226762] pnp: 00:01: ioport range 0x4000-0x407f has been reserved
Mar  4 10:57:29 karmapolice kernel: [   25.226765] pnp: 00:01: ioport range 0x5000-0x500f has been reserved
Mar  4 10:57:29 karmapolice kernel: [   25.226778] pnp: 00:0e: iomem range 0xe0000000-0xefffffff could not be reserved
Mar  4 10:57:29 karmapolice kernel: [   25.226783] pnp: 00:0f: iomem range 0xd5000-0xd7fff has been reserved
Mar  4 10:57:29 karmapolice kernel: [   25.226786] pnp: 00:0f: iomem range 0xf0000-0xf7fff could not be reserved
Mar  4 10:57:29 karmapolice kernel: [   25.226788] pnp: 00:0f: iomem range 0xf8000-0xfbfff could not be reserved
Mar  4 10:57:29 karmapolice kernel: [   25.226791] pnp: 00:0f: iomem range 0xfc000-0xfffff could not be reserved
Mar  4 10:57:29 karmapolice kernel: [   25.227020] PCI: Bridge: 0000:00:01.0
Mar  4 10:57:29 karmapolice kernel: [   25.227021]   IO window: disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.227024]   MEM window: disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.227027]   PREFETCH window: disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.227031] PCI: Bridge: 0000:00:02.0
Mar  4 10:57:29 karmapolice kernel: [   25.227032]   IO window: disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.227037]   MEM window: c8000000-cfffffff
Mar  4 10:57:29 karmapolice kernel: [   25.227041]   PREFETCH window: b0000000-bfffffff
Mar  4 10:57:29 karmapolice kernel: [   25.227045] PCI: Bridge: 0000:00:03.0
Mar  4 10:57:29 karmapolice kernel: [   25.227046]   IO window: disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.227050]   MEM window: disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.227053]   PREFETCH window: disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.227057] PCI: Bridge: 0000:00:03.1
Mar  4 10:57:29 karmapolice kernel: [   25.227058]   IO window: disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.227062]   MEM window: disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.227065]   PREFETCH window: disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.227069] PCI: Bridge: 0000:00:03.2
Mar  4 10:57:29 karmapolice kernel: [   25.227072]   IO window: b000-bfff
Mar  4 10:57:29 karmapolice kernel: [   25.227076]   MEM window: d0000000-d1ffffff
Mar  4 10:57:29 karmapolice kernel: [   25.227080]   PREFETCH window: disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.227084] PCI: Bridge: 0000:00:03.3
Mar  4 10:57:29 karmapolice kernel: [   25.227085]   IO window: disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.227089]   MEM window: disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.227092]   PREFETCH window: disabled.
Mar  4 10:57:29 karmapolice kernel: [   25.227106] PCI: Setting latency timer of device 0000:00:01.0 to 64
Mar  4 10:57:29 karmapolice kernel: [   25.227123] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 27
Mar  4 10:57:29 karmapolice kernel: [   25.227128] PCI: Setting latency timer of device 0000:00:02.0 to 64
Mar  4 10:57:29 karmapolice kernel: [   25.227140] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 31
Mar  4 10:57:29 karmapolice kernel: [   25.227145] PCI: Setting latency timer of device 0000:00:03.0 to 64
Mar  4 10:57:29 karmapolice kernel: [   25.227157] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 35 (level, low) -> IRQ 35
Mar  4 10:57:29 karmapolice kernel: [   25.227163] PCI: Setting latency timer of device 0000:00:03.1 to 64
Mar  4 10:57:29 karmapolice kernel: [   25.227175] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 39 (level, low) -> IRQ 39
Mar  4 10:57:29 karmapolice kernel: [   25.227179] PCI: Setting latency timer of device 0000:00:03.2 to 64
Mar  4 10:57:29 karmapolice kernel: [   25.227191] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 43 (level, low) -> IRQ 43
Mar  4 10:57:29 karmapolice kernel: [   25.227197] PCI: Setting latency timer of device 0000:00:03.3 to 64
Mar  4 10:57:29 karmapolice kernel: [   25.227255] NET: Registered protocol family 2
Mar  4 10:57:29 karmapolice kernel: [   25.229735] Time: tsc clocksource has been installed.
Mar  4 10:57:29 karmapolice kernel: [   25.261773] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Mar  4 10:57:29 karmapolice kernel: [   25.262370] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
Mar  4 10:57:29 karmapolice kernel: [   25.266062] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Mar  4 10:57:29 karmapolice kernel: [   25.266672] TCP: Hash tables configured (established 262144 bind 65536)
Mar  4 10:57:29 karmapolice kernel: [   25.266675] TCP reno registered
Mar  4 10:57:29 karmapolice kernel: [   25.277818] checking if image is initramfs... it is
Mar  4 10:57:29 karmapolice kernel: [   25.795125] Freeing initrd memory: 7236k freed
Mar  4 10:57:29 karmapolice kernel: [   25.799792] audit: initializing netlink socket (disabled)
Mar  4 10:57:29 karmapolice kernel: [   25.799803] audit(1204628228.096:1): initialized
Mar  4 10:57:29 karmapolice kernel: [   25.801314] VFS: Disk quotas dquot_6.5.1
Mar  4 10:57:29 karmapolice kernel: [   25.801357] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Mar  4 10:57:29 karmapolice kernel: [   25.801436] io scheduler noop registered
Mar  4 10:57:29 karmapolice kernel: [   25.801437] io scheduler anticipatory registered
Mar  4 10:57:29 karmapolice kernel: [   25.801439] io scheduler deadline registered
Mar  4 10:57:29 karmapolice kernel: [   25.801511] io scheduler cfq registered (default)
Mar  4 10:57:29 karmapolice kernel: [   25.801522] PCI: VIA PCI bridge detected. Disabling DAC.
Mar  4 10:57:29 karmapolice kernel: [   25.801795] Boot video device is 0000:02:00.0
Mar  4 10:57:29 karmapolice kernel: [   25.801923] PCI: Setting latency timer of device 0000:00:02.0 to 64
Mar  4 10:57:29 karmapolice kernel: [   25.801957] assign_interrupt_mode Found MSI capability
Mar  4 10:57:29 karmapolice kernel: [   25.801960] Allocate Port Service[0000:00:02.0:pcie00]
Mar  4 10:57:29 karmapolice kernel: [   25.801988] Allocate Port Service[0000:00:02.0:pcie02]
Mar  4 10:57:29 karmapolice kernel: [   25.802055] PCI: Setting latency timer of device 0000:00:03.0 to 64
Mar  4 10:57:29 karmapolice kernel: [   25.802089] assign_interrupt_mode Found MSI capability
Mar  4 10:57:29 karmapolice kernel: [   25.802091] Allocate Port Service[0000:00:03.0:pcie00]
Mar  4 10:57:29 karmapolice kernel: [   25.802116] Allocate Port Service[0000:00:03.0:pcie02]
Mar  4 10:57:29 karmapolice kernel: [   25.802179] PCI: Setting latency timer of device 0000:00:03.1 to 64
Mar  4 10:57:29 karmapolice kernel: [   25.802213] assign_interrupt_mode Found MSI capability
Mar  4 10:57:29 karmapolice kernel: [   25.802215] Allocate Port Service[0000:00:03.1:pcie00]
Mar  4 10:57:29 karmapolice kernel: [   25.802238] Allocate Port Service[0000:00:03.1:pcie02]
Mar  4 10:57:29 karmapolice kernel: [   25.802300] PCI: Setting latency timer of device 0000:00:03.2 to 64
Mar  4 10:57:29 karmapolice kernel: [   25.802334] assign_interrupt_mode Found MSI capability
Mar  4 10:57:29 karmapolice kernel: [   25.802336] Allocate Port Service[0000:00:03.2:pcie00]
Mar  4 10:57:29 karmapolice kernel: [   25.802358] Allocate Port Service[0000:00:03.2:pcie02]
Mar  4 10:57:29 karmapolice kernel: [   25.802422] PCI: Setting latency timer of device 0000:00:03.3 to 64
Mar  4 10:57:29 karmapolice kernel: [   25.802455] assign_interrupt_mode Found MSI capability
Mar  4 10:57:29 karmapolice kernel: [   25.802457] Allocate Port Service[0000:00:03.3:pcie00]
Mar  4 10:57:29 karmapolice kernel: [   25.802483] Allocate Port Service[0000:00:03.3:pcie02]
Mar  4 10:57:29 karmapolice kernel: [   25.821495] Real Time Clock Driver v1.12ac
Mar  4 10:57:29 karmapolice kernel: [   25.821563] Linux agpgart interface v0.102 (c) Dave Jones
Mar  4 10:57:29 karmapolice kernel: [   25.821566] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Mar  4 10:57:29 karmapolice kernel: [   25.821656] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar  4 10:57:29 karmapolice kernel: [   25.822169] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar  4 10:57:29 karmapolice kernel: [   25.822700] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Mar  4 10:57:29 karmapolice kernel: [   25.822841] input: Macintosh mouse button emulation as /class/input/input0
Mar  4 10:57:29 karmapolice kernel: [   25.822900] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Mar  4 10:57:29 karmapolice kernel: [   25.823312] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar  4 10:57:29 karmapolice kernel: [   25.823316] serio: i8042 AUX port at 0x60,0x64 irq 12
Mar  4 10:57:29 karmapolice kernel: [   25.823429] mice: PS/2 mouse device common for all mice
Mar  4 10:57:29 karmapolice kernel: [   25.823591] TCP cubic registered
Mar  4 10:57:29 karmapolice kernel: [   25.823649] NET: Registered protocol family 1
Mar  4 10:57:29 karmapolice kernel: [   25.823823] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Mar  4 10:57:29 karmapolice kernel: [   25.823829] Freeing unused kernel memory: 296k freed
Mar  4 10:57:29 karmapolice kernel: [   25.885217] input: AT Translated Set 2 keyboard as /class/input/input1
Mar  4 10:57:29 karmapolice kernel: [   26.985981] AppArmor: AppArmor initialized<5>audit(1204628229.284:2):  type=1505 info="AppArmor initialized" pid=1298
Mar  4 10:57:29 karmapolice kernel: [   26.991805] fuse init (API version 7.8)
Mar  4 10:57:29 karmapolice kernel: [   26.996012] Failure registering capabilities with primary security module.
Mar  4 10:57:29 karmapolice kernel: [   27.003250] ACPI: Fan [FAN] (on)
Mar  4 10:57:29 karmapolice kernel: [   27.006990] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
Mar  4 10:57:29 karmapolice kernel: [   27.008200] ACPI: Thermal Zone [THRM] (24 C)
Mar  4 10:57:29 karmapolice kernel: [   27.541664] SCSI subsystem initialized
Mar  4 10:57:29 karmapolice kernel: [   27.545948] libata version 2.21 loaded.
Mar  4 10:57:29 karmapolice kernel: [   27.547093] sata_via 0000:00:0f.0: version 2.2
Mar  4 10:57:29 karmapolice kernel: [   27.547330] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
Mar  4 10:57:29 karmapolice kernel: [   27.547337] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 20
Mar  4 10:57:29 karmapolice kernel: [   27.547373] sata_via 0000:00:0f.0: routed to hard irq line 11
Mar  4 10:57:29 karmapolice kernel: [   27.547458] scsi0 : sata_via
Mar  4 10:57:29 karmapolice kernel: [   27.547498] scsi1 : sata_via
Mar  4 10:57:29 karmapolice kernel: [   27.547704] ata1: SATA max UDMA/133 cmd 0x000000000001c000 ctl 0x000000000001c402 bmdma 0x000000000001d000 irq 20
Mar  4 10:57:29 karmapolice kernel: [   27.547708] ata2: SATA max UDMA/133 cmd 0x000000000001c800 ctl 0x000000000001cc02 bmdma 0x000000000001d008 irq 20
Mar  4 10:57:29 karmapolice kernel: [   27.578686] usbcore: registered new interface driver usbfs
Mar  4 10:57:29 karmapolice kernel: [   27.578711] usbcore: registered new interface driver hub
Mar  4 10:57:29 karmapolice kernel: [   27.578730] usbcore: registered new device driver usb
Mar  4 10:57:29 karmapolice kernel: [   27.612811] USB Universal Host Controller Interface driver v3.0
Mar  4 10:57:29 karmapolice kernel: [   27.659101] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Mar  4 10:57:29 karmapolice kernel: [   27.659106] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Mar  4 10:57:29 karmapolice kernel: [   27.693404] Floppy drive(s): fd0 is 1.44M
Mar  4 10:57:29 karmapolice kernel: [   27.739822] FDC 0 is a post-1991 82077
Mar  4 10:57:29 karmapolice kernel: [   27.755447] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar  4 10:57:29 karmapolice kernel: [   27.948723] ata1.00: ATA-6: WDC WD2500JD-40HBC0, 21.02J21, max UDMA/133
Mar  4 10:57:29 karmapolice kernel: [   27.948728] ata1.00: 488397168 sectors, multi 16: LBA48 
Mar  4 10:57:29 karmapolice kernel: [   27.972717] ata1.00: configured for UDMA/133
Mar  4 10:57:29 karmapolice kernel: [   28.179048] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Mar  4 10:57:29 karmapolice kernel: [   28.189759] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500JD-40H 21.0 PQ: 0 ANSI: 5
Mar  4 10:57:29 karmapolice kernel: [   28.190408] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
Mar  4 10:57:29 karmapolice kernel: [   28.190415] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
Mar  4 10:57:29 karmapolice kernel: [   28.190425] uhci_hcd 0000:00:10.0: UHCI Host Controller
Mar  4 10:57:29 karmapolice kernel: [   28.190577] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Mar  4 10:57:29 karmapolice kernel: [   28.190605] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000dc00
Mar  4 10:57:29 karmapolice kernel: [   28.190710] usb usb1: configuration #1 chosen from 1 choice
Mar  4 10:57:29 karmapolice kernel: [   28.190733] hub 1-0:1.0: USB hub found
Mar  4 10:57:29 karmapolice kernel: [   28.190739] hub 1-0:1.0: 2 ports detected
Mar  4 10:57:29 karmapolice kernel: [   28.197954] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Mar  4 10:57:29 karmapolice kernel: [   28.197965] sd 0:0:0:0: [sda] Write Protect is off
Mar  4 10:57:29 karmapolice kernel: [   28.197968] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar  4 10:57:29 karmapolice kernel: [   28.197977] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  4 10:57:29 karmapolice kernel: [   28.198021] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Mar  4 10:57:29 karmapolice kernel: [   28.198027] sd 0:0:0:0: [sda] Write Protect is off
Mar  4 10:57:29 karmapolice kernel: [   28.198029] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar  4 10:57:29 karmapolice kernel: [   28.198038] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  4 10:57:29 karmapolice kernel: [   28.198043]  sda: sda1 sda2 sda3 sda4
Mar  4 10:57:29 karmapolice kernel: [   28.265961] sd 0:0:0:0: [sda] Attached SCSI disk
Mar  4 10:57:29 karmapolice kernel: [   28.269283] sd 0:0:0:0: Attached scsi generic sg0 type 0
Mar  4 10:57:29 karmapolice kernel: [   28.295059] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
Mar  4 10:57:29 karmapolice kernel: [   28.295070] uhci_hcd 0000:00:10.1: UHCI Host Controller
Mar  4 10:57:29 karmapolice kernel: [   28.295092] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Mar  4 10:57:29 karmapolice kernel: [   28.295113] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000e000
Mar  4 10:57:29 karmapolice kernel: [   28.295197] usb usb2: configuration #1 chosen from 1 choice
Mar  4 10:57:29 karmapolice kernel: [   28.295217] hub 2-0:1.0: USB hub found
Mar  4 10:57:29 karmapolice kernel: [   28.295222] hub 2-0:1.0: 2 ports detected
Mar  4 10:57:29 karmapolice kernel: [   28.402946] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
Mar  4 10:57:29 karmapolice kernel: [   28.402960] uhci_hcd 0000:00:10.2: UHCI Host Controller
Mar  4 10:57:29 karmapolice kernel: [   28.402979] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Mar  4 10:57:29 karmapolice kernel: [   28.403000] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e400
Mar  4 10:57:29 karmapolice kernel: [   28.403087] usb usb3: configuration #1 chosen from 1 choice
Mar  4 10:57:29 karmapolice kernel: [   28.403106] hub 3-0:1.0: USB hub found
Mar  4 10:57:29 karmapolice kernel: [   28.403111] hub 3-0:1.0: 2 ports detected
Mar  4 10:57:29 karmapolice kernel: [   28.510865] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
Mar  4 10:57:29 karmapolice kernel: [   28.510878] uhci_hcd 0000:00:10.3: UHCI Host Controller
Mar  4 10:57:29 karmapolice kernel: [   28.510901] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Mar  4 10:57:29 karmapolice kernel: [   28.510923] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000e800
Mar  4 10:57:29 karmapolice kernel: [   28.511003] usb usb4: configuration #1 chosen from 1 choice
Mar  4 10:57:29 karmapolice kernel: [   28.511026] hub 4-0:1.0: USB hub found
Mar  4 10:57:29 karmapolice kernel: [   28.511031] hub 4-0:1.0: 2 ports detected
Mar  4 10:57:29 karmapolice kernel: [   28.551833] kjournald starting.  Commit interval 5 seconds
Mar  4 10:57:29 karmapolice kernel: [   28.551843] EXT3-fs: mounted filesystem with ordered data mode.
Mar  4 10:57:29 karmapolice kernel: [   28.618843] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
Mar  4 10:57:29 karmapolice kernel: [   28.618862] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 20
Mar  4 10:57:29 karmapolice kernel: [   28.618871] VP_IDE: chipset revision 6
Mar  4 10:57:29 karmapolice kernel: [   28.618873] VP_IDE: not 100%% native mode: will probe irqs later
Mar  4 10:57:29 karmapolice kernel: [   28.618883] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
Mar  4 10:57:29 karmapolice kernel: [   28.618890]     ide0: BM-DMA at 0xd800-0xd807, BIOS settings: hda:DMA, hdb:pio
Mar  4 10:57:29 karmapolice kernel: [   28.618899]     ide1: BM-DMA at 0xd808-0xd80f, BIOS settings: hdc:pio, hdd:pio
Mar  4 10:57:29 karmapolice kernel: [   28.618904] Probing IDE interface ide0...
Mar  4 10:57:29 karmapolice kernel: [   29.306036] usb 4-1: new full speed USB device using uhci_hcd and address 2
Mar  4 10:57:29 karmapolice kernel: [   29.461138] usb 4-1: configuration #1 chosen from 1 choice
Mar  4 10:57:29 karmapolice kernel: [   29.464084] hub 4-1:1.0: USB hub found
Mar  4 10:57:29 karmapolice kernel: [   29.467057] hub 4-1:1.0: 4 ports detected
Mar  4 10:57:29 karmapolice kernel: [   29.493945] hda: PIONEER DVD-RW DVR-110D, ATAPI CD/DVD-ROM drive
Mar  4 10:57:29 karmapolice kernel: [   29.934621] usb 4-1.4: new full speed USB device using uhci_hcd and address 3
Mar  4 10:57:29 karmapolice kernel: [   30.076562] usb 4-1.4: configuration #1 chosen from 1 choice
Mar  4 10:57:29 karmapolice kernel: [   30.165488] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Mar  4 10:57:29 karmapolice kernel: [   30.167668] Probing IDE interface ide1...
Mar  4 10:57:29 karmapolice kernel: [   30.736911] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
Mar  4 10:57:29 karmapolice kernel: [   30.737029] ehci_hcd 0000:00:10.4: EHCI Host Controller
Mar  4 10:57:29 karmapolice kernel: [   30.737076] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Mar  4 10:57:29 karmapolice kernel: [   30.737116] ehci_hcd 0000:00:10.4: irq 21, io mem 0xd2002000
Mar  4 10:57:29 karmapolice kernel: [   30.737122] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar  4 10:57:29 karmapolice kernel: [   30.737210] usb usb5: configuration #1 chosen from 1 choice
Mar  4 10:57:29 karmapolice kernel: [   30.737231] hub 5-0:1.0: USB hub found
Mar  4 10:57:29 karmapolice kernel: [   30.737237] hub 5-0:1.0: 8 ports detected
Mar  4 10:57:29 karmapolice kernel: [   31.088393] usb 5-7: new high speed USB device using ehci_hcd and address 2
Mar  4 10:57:29 karmapolice kernel: [   31.224696] usb 5-7: configuration #1 chosen from 1 choice
Mar  4 10:57:29 karmapolice kernel: [   31.224756] hub 5-7:1.0: USB hub found
Mar  4 10:57:29 karmapolice kernel: [   31.224861] hub 5-7:1.0: 4 ports detected
Mar  4 10:57:29 karmapolice kernel: [   31.332225] usb 4-1: USB disconnect, address 2
Mar  4 10:57:29 karmapolice kernel: [   31.332227] usb 4-1.4: USB disconnect, address 3
Mar  4 10:57:29 karmapolice kernel: [   31.672004] usb 5-7.4: new high speed USB device using ehci_hcd and address 3
Mar  4 10:57:29 karmapolice kernel: [   31.770118] usb 5-7.4: configuration #1 chosen from 1 choice
Mar  4 10:57:29 karmapolice kernel: [   37.723267] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar  4 10:57:29 karmapolice kernel: [   37.887302] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar  4 10:57:29 karmapolice kernel: [   38.154040] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar  4 10:57:29 karmapolice kernel: [   38.154046] rt2500 1.1.0 CVS 2007111211 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
Mar  4 10:57:29 karmapolice kernel: [   38.504727] input: PC Speaker as /class/input/input2
Mar  4 10:57:29 karmapolice kernel: [   38.770989] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 36 (level, low) -> IRQ 36
Mar  4 10:57:29 karmapolice kernel: [   38.771002] PCI: Setting latency timer of device 0000:05:00.0 to 64
Mar  4 10:57:29 karmapolice kernel: [   38.771005] PCI: Disallowing DAC for device 0000:05:00.0
Mar  4 10:57:29 karmapolice kernel: [   38.771104] sky2 0000:05:00.0: v1.18 addr 0xd1000000 irq 36 Yukon-EC (0xb6) rev 2
Mar  4 10:57:29 karmapolice kernel: [   38.771253] sky2 eth0: addr 00:13:d4:d9:b2:be
Mar  4 10:57:29 karmapolice kernel: [   38.830911] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
Mar  4 10:57:29 karmapolice kernel: [   38.830918] rt2500 EEPROM: 12 12 12 12 12 12 12 12 12 11 11 11 11 11  dBm Maximum
Mar  4 10:57:29 karmapolice kernel: [   38.978509] nvidia: module license 'NVIDIA' taints kernel.
Mar  4 10:57:29 karmapolice kernel: [   39.239939] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 24 (level, low) -> IRQ 24
Mar  4 10:57:29 karmapolice kernel: [   39.239948] PCI: Setting latency timer of device 0000:02:00.0 to 64
Mar  4 10:57:29 karmapolice kernel: [   39.240065] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-9639  Mon Apr 16 20:18:26 PDT 2007
Mar  4 10:57:29 karmapolice kernel: [   39.453189] usbcore: registered new interface driver libusual
Mar  4 10:57:29 karmapolice kernel: [   39.733506] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
Mar  4 10:57:29 karmapolice kernel: [   39.736165] parport_pc 00:09: reported by Plug and Play ACPI
Mar  4 10:57:29 karmapolice kernel: [   39.736217] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Mar  4 10:57:29 karmapolice kernel: [   40.036603] hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(66)
Mar  4 10:57:29 karmapolice kernel: [   40.036611] Uniform CD-ROM driver Revision: 3.20
Mar  4 10:57:29 karmapolice kernel: [   40.160873] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
Mar  4 10:57:29 karmapolice kernel: [   40.161069] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Mar  4 10:57:29 karmapolice kernel: [   40.161075] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 22
Mar  4 10:57:29 karmapolice kernel: [   40.369566] NET: Registered protocol family 10
Mar  4 10:57:29 karmapolice kernel: [   40.369642] lo: Disabled Privacy Extensions
Mar  4 10:57:29 karmapolice kernel: [   40.473023] Initializing USB Mass Storage driver...
Mar  4 10:57:29 karmapolice kernel: [   40.498663] scsi2 : SCSI emulation for USB Mass Storage devices
Mar  4 10:57:29 karmapolice kernel: [   40.511511] usbcore: registered new interface driver usb-storage
Mar  4 10:57:29 karmapolice kernel: [   40.511516] USB Mass Storage support registered.
Mar  4 10:57:29 karmapolice kernel: [   40.511607] usb-storage: device found at 3
Mar  4 10:57:29 karmapolice kernel: [   40.511609] usb-storage: waiting for device to settle before scanning
Mar  4 10:57:29 karmapolice kernel: [   40.915392] PCI: Setting latency timer of device 0000:00:11.6 to 64
Mar  4 10:57:29 karmapolice kernel: [   41.419123] ACPI: PCI interrupt for device 0000:00:11.6 disabled
Mar  4 10:57:29 karmapolice kernel: [   41.419133] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
Mar  4 10:57:29 karmapolice kernel: [   41.419262] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 22
Mar  4 10:57:29 karmapolice kernel: [   41.419397] PCI: Setting latency timer of device 0000:00:11.5 to 64
Mar  4 10:57:29 karmapolice kernel: [   42.635935] lp0: using parport0 (interrupt-driven).
Mar  4 10:57:29 karmapolice kernel: [   42.781345] Adding 5767324k swap on /dev/sda4.  Priority:-1 extents:1 across:5767324k
Mar  4 10:57:29 karmapolice kernel: [   43.065434] EXT3 FS on sda3, internal journal
Mar  4 10:57:29 karmapolice kernel: [   43.778336] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Mar  4 10:57:29 karmapolice kernel: [   43.780731] SGI XFS Quota Management subsystem
Mar  4 10:57:29 karmapolice kernel: [   43.840360] XFS mounting filesystem sda2
Mar  4 10:57:29 karmapolice kernel: [   43.912302] Ending clean XFS mount for filesystem: sda2
Mar  4 10:57:29 karmapolice kernel: [   45.102286] No dock devices found.
Mar  4 10:57:29 karmapolice kernel: [   45.159186] input: Power Button (FF) as /class/input/input4
Mar  4 10:57:29 karmapolice kernel: [   45.162886] ACPI: Power Button (FF) [PWRF]
Mar  4 10:57:29 karmapolice kernel: [   45.187947] input: Power Button (CM) as /class/input/input5
Mar  4 10:57:29 karmapolice kernel: [   45.191564] ACPI: Power Button (CM) [PWRB]
Mar  4 10:57:29 karmapolice kernel: [   45.464616] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (version 2.00.00)
Mar  4 10:57:29 karmapolice kernel: [   45.464653] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
Mar  4 10:57:29 karmapolice kernel: [   45.464655] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
Mar  4 10:57:29 karmapolice kernel: [   45.464657] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
Mar  4 10:57:29 karmapolice kernel: [   45.464660] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Mar  4 10:57:29 karmapolice kernel: [   45.507339] usb-storage: device scan complete
Mar  4 10:57:29 karmapolice kernel: [   45.507827] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Mar  4 10:57:29 karmapolice kernel: [   45.508324] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Mar  4 10:57:29 karmapolice kernel: [   45.508821] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Mar  4 10:57:29 karmapolice kernel: [   45.509320] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Mar  4 10:57:29 karmapolice kernel: [   45.510374] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Mar  4 10:57:29 karmapolice kernel: [   45.510412] sd 2:0:0:0: Attached scsi generic sg1 type 0
Mar  4 10:57:29 karmapolice kernel: [   45.511537] sd 2:0:0:1: [sdc] Attached SCSI removable disk
Mar  4 10:57:29 karmapolice kernel: [   45.511574] sd 2:0:0:1: Attached scsi generic sg2 type 0
Mar  4 10:57:29 karmapolice kernel: [   45.513295] sd 2:0:0:2: [sdd] Attached SCSI removable disk
Mar  4 10:57:29 karmapolice kernel: [   45.513332] sd 2:0:0:2: Attached scsi generic sg3 type 0
Mar  4 10:57:29 karmapolice kernel: [   45.515107] sd 2:0:0:3: [sde] Attached SCSI removable disk
Mar  4 10:57:29 karmapolice kernel: [   45.515149] sd 2:0:0:3: Attached scsi generic sg4 type 0
Mar  4 10:57:30 karmapolice kernel: [   47.749421] sky2 eth0: enabling interface
Mar  4 10:57:30 karmapolice kernel: [   47.752355] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar  4 10:57:33 karmapolice kernel: [   51.134024] ra0: no IPv6 routers present
Mar  4 10:57:35 karmapolice kernel: [   52.872614] Marking TSC unstable due to cpufreq changes
Mar  4 10:57:35 karmapolice kernel: [   52.873142] Time: acpi_pm clocksource has been installed.
Mar  4 10:57:36 karmapolice kernel: [   54.001040] ppdev: user-space parallel port driver
Mar  4 10:57:37 karmapolice kernel: [   54.482849] audit(1204624657.427:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5083 profile="/usr/sbin/cupsd"
Mar  4 10:58:31 karmapolice kernel: [  108.572441] BUG: scheduling while atomic: ktorrent/0x10010000/5386
Mar  4 10:58:31 karmapolice kernel: [  108.572446] 
Mar  4 10:58:31 karmapolice kernel: [  108.572447] Call Trace:
Mar  4 10:58:31 karmapolice kernel: [  108.572449]  <IRQ>  [thread_return+542/1737] thread_return+0x21e/0x6c9
Mar  4 10:58:31 karmapolice kernel: [  108.572475]  [netlink_broadcast+585/896] netlink_broadcast+0x249/0x380
Mar  4 10:58:31 karmapolice kernel: [  108.572488]  [__cond_resched+28/80] __cond_resched+0x1c/0x50
Mar  4 10:58:31 karmapolice kernel: [  108.572491]  [cond_resched+50/64] cond_resched+0x32/0x40
Mar  4 10:58:31 karmapolice kernel: [  108.572495]  [mutex_lock+9/32] mutex_lock+0x9/0x20
Mar  4 10:58:31 karmapolice kernel: [  108.572500]  [sysfs_hash_and_remove+108/352] sysfs_hash_and_remove+0x6c/0x160
Mar  4 10:58:31 karmapolice kernel: [  108.572507]  [sysfs_slab_alias+113/160] sysfs_slab_alias+0x71/0xa0
Mar  4 10:58:31 karmapolice kernel: [  108.572512]  [sysfs_slab_add+300/416] sysfs_slab_add+0x12c/0x1a0
Mar  4 10:58:31 karmapolice kernel: [  108.572519]  [create_kmalloc_cache+158/224] create_kmalloc_cache+0x9e/0xe0
Mar  4 10:58:31 karmapolice kernel: [  108.572526]  [get_slab+479/528] get_slab+0x1df/0x210
Mar  4 10:58:31 karmapolice kernel: [  108.572542]  [_end+129117458/2130324728] :rt2500:RTMPHandleDecryptionDoneInterrupt+0x96a/0x1200
Mar  4 10:58:31 karmapolice kernel: [  108.572547]  [__kmalloc_node_track_caller+37/176] __kmalloc_node_track_caller+0x25/0xb0
Mar  4 10:58:31 karmapolice kernel: [  108.572553]  [__alloc_skb+125/368] __alloc_skb+0x7d/0x170
Mar  4 10:58:31 karmapolice kernel: [  108.572570]  [_end+127782829/2130324728] :scsi_mod:scsi_end_request+0xd5/0x110
Mar  4 10:58:31 karmapolice kernel: [  108.572583]  [_end+129117458/2130324728] :rt2500:RTMPHandleDecryptionDoneInterrupt+0x96a/0x1200
Mar  4 10:58:31 karmapolice kernel: [  108.572589]  [task_rq_lock+76/144] task_rq_lock+0x4c/0x90
Mar  4 10:58:31 karmapolice kernel: [  108.572592]  [__activate_task+41/80] __activate_task+0x29/0x50
Mar  4 10:58:31 karmapolice kernel: [  108.572604]  [_end+129113358/2130324728] :rt2500:RTMPHandleRxDoneInterrupt+0x106/0x7a0
Mar  4 10:58:31 karmapolice kernel: [  108.572620]  [_end+129058791/2130324728] :rt2500:RTMPIsr+0xff/0x180
Mar  4 10:58:31 karmapolice kernel: [  108.572626]  [handle_IRQ_event+52/112] handle_IRQ_event+0x34/0x70
Mar  4 10:58:31 karmapolice kernel: [  108.572632]  [handle_fasteoi_irq+138/272] handle_fasteoi_irq+0x8a/0x110
Mar  4 10:58:31 karmapolice kernel: [  108.572639]  [do_IRQ+123/256] do_IRQ+0x7b/0x100
Mar  4 10:58:31 karmapolice kernel: [  108.572643]  [ret_from_intr+0/10] ret_from_intr+0x0/0xa
Mar  4 10:58:31 karmapolice kernel: [  108.572646]  <EOI> 
Mar  4 11:15:40 karmapolice kernel: [ 1130.942109] usb 5-7.4: reset high speed USB device using ehci_hcd and address 3
Mar  4 12:42:31 karmapolice kernel: [ 6307.651956] Unable to handle kernel NULL pointer dereference at 0000000000000001 RIP: 
Mar  4 12:42:31 karmapolice kernel: [ 6307.651962]  [swsusp_unset_page_free+16/48] swsusp_unset_page_free+0x10/0x30
Mar  4 12:42:31 karmapolice kernel: [ 6307.651970] PGD 73b5b067 PUD 7c125067 PMD 0 
Mar  4 12:42:31 karmapolice kernel: [ 6307.651973] Oops: 0000 [1] SMP 
Mar  4 12:42:31 karmapolice kernel: [ 6307.651976] CPU 0 
Mar  4 12:42:31 karmapolice kernel: [ 6307.651977] Modules linked in: binfmt_misc ppdev powernow_k8 cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative video sbs button dock container ac battery xfs lp usb_storage ipv6 snd_via82xx snd_via82xx_modem snd_ac97_codec snd_seq_dummy ide_cd cdrom ac97_bus snd_pcm_oss snd_mixer_oss snd_seq_oss libusual snd_pcm snd_mpu401 snd_mpu401_uart analog snd_seq_midi nvidia(P) parport_pc parport gameport psmouse snd_seq_midi_event snd_seq snd_timer sky2 snd_rawmidi snd_seq_device i2c_viapro serio_raw snd soundcore snd_page_alloc ata_generic pcspkr k8temp i2c_core rt2500 shpchp pci_hotplug evdev ext3 jbd mbcache sg sd_mod floppy ehci_hcd via82cxxx ide_core uhci_hcd usbcore sata_via libata scsi_mod thermal processor fan fuse apparmor commoncap
Mar  4 12:42:31 karmapolice kernel: [ 6307.652013] Pid: 4896, comm: Xorg Tainted: P       2.6.22-14-generic #1
Mar  4 12:42:31 karmapolice kernel: [ 6307.652015] RIP: 0010:[swsusp_unset_page_free+16/48]  [swsusp_unset_page_free+16/48] swsusp_unset_page_free+0x10/0x30
Mar  4 12:42:31 karmapolice kernel: [ 6307.652020] RSP: 0018:ffff81007cf55a10  EFLAGS: 00010286
Mar  4 12:42:31 karmapolice kernel: [ 6307.652023] RAX: 000000000000000a RBX: ffff81007cf55b10 RCX: 0000000000000001
Mar  4 12:42:31 karmapolice kernel: [ 6307.652026] RDX: ffff81007cf55dd0 RSI: ffff81007cf55b18 RDI: ffff8100734ad630
Mar  4 12:42:31 karmapolice kernel: [ 6307.652029] RBP: 0000000000000000 R08: 0000000000000000 R09: 0000000000000002
Mar  4 12:42:31 karmapolice kernel: [ 6307.652032] R10: ffff810032254000 R11: ffffffff80422270 R12: ffff81007b51e000
Mar  4 12:42:31 karmapolice kernel: [ 6307.652035] R13: ffff81007cf55af8 R14: 0000000000000304 R15: 0000000000000000
Mar  4 12:42:31 karmapolice kernel: [ 6307.652038] FS:  00002b1952a5be20(0000) GS:ffffffff80561000(0000) knlGS:00000000f71906b0
Mar  4 12:42:31 karmapolice kernel: [ 6307.652041] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Mar  4 12:42:31 karmapolice kernel: [ 6307.652043] CR2: 0000000000000001 CR3: 0000000073511000 CR4: 00000000000006e0
Mar  4 12:42:31 karmapolice kernel: [ 6307.652047] Process Xorg (pid: 4896, threadinfo ffff81007cf54000, task ffff8100754fd4a0)
Mar  4 12:42:31 karmapolice kernel: [ 6307.652049] Stack:  ffffffff802a78d1 ffff81007cf55b48 ffffffff802a790c 0000000000000004
Mar  4 12:42:31 karmapolice kernel: [ 6307.652054]  0000000000000027 0000004000000000 ffff810063c43e00 0000000000000000
Mar  4 12:42:31 karmapolice kernel: [ 6307.652058]  ffffffff802a8307 ffff81007ab34000 ffff81007cf55af8 ffff81007cf55f50
Mar  4 12:42:31 karmapolice kernel: [ 6307.652062] Call Trace:
Mar  4 12:42:31 karmapolice kernel: [ 6307.652067]  [free_poll_entry+17/32] free_poll_entry+0x11/0x20
Mar  4 12:42:31 karmapolice kernel: [ 6307.652070]  [poll_freewait+44/144] poll_freewait+0x2c/0x90
Mar  4 12:42:31 karmapolice kernel: [ 6307.652076]  [do_select+1303/1344] do_select+0x517/0x540
Mar  4 12:42:31 karmapolice kernel: [ 6307.652090]  [__pollwait+0/304] __pollwait+0x0/0x130
Mar  4 12:42:31 karmapolice kernel: [ 6307.652096]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar  4 12:42:31 karmapolice kernel: [ 6307.652103]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar  4 12:42:31 karmapolice kernel: [ 6307.652109]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar  4 12:42:31 karmapolice kernel: [ 6307.652115]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar  4 12:42:31 karmapolice kernel: [ 6307.652122]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar  4 12:42:31 karmapolice kernel: [ 6307.652128]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar  4 12:42:31 karmapolice kernel: [ 6307.652135]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar  4 12:42:31 karmapolice kernel: [ 6307.652141]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar  4 12:42:31 karmapolice kernel: [ 6307.652147]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar  4 12:42:31 karmapolice kernel: [ 6307.652154]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Mar  4 12:42:31 karmapolice kernel: [ 6307.652163]  [core_sys_select+517/768] core_sys_select+0x205/0x300
Mar  4 12:42:31 karmapolice kernel: [ 6307.652167]  [recalc_sigpending+14/48] recalc_sigpending+0xe/0x30
Mar  4 12:42:31 karmapolice kernel: [ 6307.652177]  [recalc_sigpending+14/48] recalc_sigpending+0xe/0x30
Mar  4 12:42:31 karmapolice kernel: [ 6307.652180]  [do_notify_resume+462/2032] do_notify_resume+0x1ce/0x7f0
Mar  4 12:42:31 karmapolice kernel: [ 6307.652188]  [init_fpu+70/160] init_fpu+0x46/0xa0
Mar  4 12:42:31 karmapolice kernel: [ 6307.652193]  [math_state_restore+60/80] math_state_restore+0x3c/0x50
Mar  4 12:42:31 karmapolice kernel: [ 6307.652197]  [error_exit+0/132] error_exit+0x0/0x84
Mar  4 12:42:31 karmapolice kernel: [ 6307.652209]  [sys_rt_sigreturn+701/752] sys_rt_sigreturn+0x2bd/0x2f0
Mar  4 12:42:31 karmapolice kernel: [ 6307.652215]  [sys_select+209/448] sys_select+0xd1/0x1c0
Mar  4 12:42:31 karmapolice kernel: [ 6307.652224]  [system_call+126/131] system_call+0x7e/0x83
Mar  4 12:42:31 karmapolice kernel: [ 6307.652234] 
Mar  4 12:42:31 karmapolice kernel: [ 6307.652235] 
Mar  4 12:42:31 karmapolice kernel: [ 6307.652236] Code: 6b 01 00 48 8b 3d f6 f3 3d 00 48 89 c6 48 83 c4 08 e9 1a ff 
Mar  4 12:42:31 karmapolice kernel: [ 6307.652243] RIP  [swsusp_unset_page_free+16/48] swsusp_unset_page_free+0x10/0x30
Mar  4 12:42:31 karmapolice kernel: [ 6307.652246]  RSP <ffff81007cf55a10>
Mar  4 12:42:31 karmapolice kernel: [ 6307.652248] CR2: 0000000000000001
Mar  4 12:42:31 karmapolice kernel: [ 6307.700621] Unable to handle kernel paging request at 0000004000000000 RIP: 
Mar  4 12:42:31 karmapolice kernel: [ 6307.700626]  [phys_startup_64+-2097152/-2147483648]
Mar  4 12:42:31 karmapolice kernel: [ 6307.700633] PGD 0 
Mar  4 12:42:31 karmapolice kernel: [ 6307.700635] Oops: 0010 [2] SMP 
Mar  4 12:42:31 karmapolice kernel: [ 6307.700638] CPU 0 
Mar  4 12:42:31 karmapolice kernel: [ 6307.700639] Modules linked in: binfmt_misc ppdev powernow_k8 cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative video sbs button dock container ac battery xfs lp usb_storage ipv6 snd_via82xx snd_via82xx_modem snd_ac97_codec snd_seq_dummy ide_cd cdrom ac97_bus snd_pcm_oss snd_mixer_oss snd_seq_oss libusual snd_pcm snd_mpu401 snd_mpu401_uart analog snd_seq_midi nvidia(P) parport_pc parport gameport psmouse snd_seq_midi_event snd_seq snd_timer sky2 snd_rawmidi snd_seq_device i2c_viapro serio_raw snd soundcore snd_page_alloc ata_generic pcspkr k8temp i2c_core rt2500 shpchp pci_hotplug evdev ext3 jbd mbcache sg sd_mod floppy ehci_hcd via82cxxx ide_core uhci_hcd usbcore sata_via libata scsi_mod thermal processor fan fuse apparmor commoncap
Mar  4 12:42:31 karmapolice kernel: [ 6307.700670] Pid: 4933, comm: kdm Tainted: P       2.6.22-14-generic #1
Mar  4 12:42:31 karmapolice kernel: [ 6307.700672] RIP: 0010:[phys_startup_64+-2097152/-2147483648]  [phys_startup_64+-2097152/-2147483648]
Mar  4 12:42:31 karmapolice kernel: [ 6307.700676] RSP: 0018:ffff81007d113d50  EFLAGS: 00010002
Mar  4 12:42:31 karmapolice kernel: [ 6307.700679] RAX: ffff81007cf55cb8 RBX: ffff81000000d9e8 RCX: 0000000000000000
Mar  4 12:42:31 karmapolice kernel: [ 6307.700682] RDX: 0000000000000000 RSI: 0000000000000001 RDI: ffff81007cf55ca0
Mar  4 12:42:31 karmapolice kernel: [ 6307.700684] RBP: ffff81007d113d88 R08: 0000000000000000 R09: 0000000000000004
Mar  4 12:42:31 karmapolice kernel: [ 6307.700687] R10: 0000000000000002 R11: 00000000000005bb R12: 00000000802736d1
Mar  4 12:42:31 karmapolice kernel: [ 6307.700689] R13: 0000000000000000 R14: ffff8100721e6b38 R15: 0000000000000000
Mar  4 12:42:31 karmapolice kernel: [ 6307.700693] FS:  00002b255b532af0(0000) GS:ffffffff80561000(0000) knlGS:00000000f682fb90
Mar  4 12:42:31 karmapolice kernel: [ 6307.700696] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Mar  4 12:42:31 karmapolice kernel: [ 6307.700698] CR2: 0000004000000000 CR3: 0000000000201000 CR4: 00000000000006e0
Mar  4 12:42:31 karmapolice kernel: [ 6307.700702] Process kdm (pid: 4933, threadinfo ffff81007d112000, task ffff81007c3aa6e0)
Mar  4 12:42:31 karmapolice kernel: [ 6307.700703] Stack:  ffffffff8022c307 0000000100000000 ffff8100721e6b30 0000000000000000
Mar  4 12:42:31 karmapolice kernel: [ 6307.700708]  0000000000000000 0000000000000282 0000000000000001 ffff81007d113dc8
Mar  4 12:42:31 karmapolice kernel: [ 6307.700712]  ffffffff8022ca03 ffff81007d113dd8 ffff81007d3522c0 ffff81007d3520b0
Mar  4 12:42:31 karmapolice kernel: [ 6307.700717] Call Trace:
Mar  4 12:42:31 karmapolice kernel: [ 6307.700723]  [__wake_up_common+71/128] __wake_up_common+0x47/0x80
Mar  4 12:42:31 karmapolice kernel: [ 6307.700730]  [__wake_up+67/112] __wake_up+0x43/0x70
Mar  4 12:42:31 karmapolice kernel: [ 6307.700739]  [sock_def_wakeup+62/64] sock_def_wakeup+0x3e/0x40
Mar  4 12:42:31 karmapolice kernel: [ 6307.700743]  [unix_release_sock+460/560] unix_release_sock+0x1cc/0x230
Mar  4 12:42:31 karmapolice kernel: [ 6307.700750]  [sock_release+33/144] sock_release+0x21/0x90
Mar  4 12:42:31 karmapolice kernel: [ 6307.700755]  [sock_close+30/64] sock_close+0x1e/0x40
Mar  4 12:42:31 karmapolice kernel: [ 6307.700760]  [__fput+193/480] __fput+0xc1/0x1e0
Mar  4 12:42:31 karmapolice kernel: [ 6307.700768]  [filp_close+84/144] filp_close+0x54/0x90
Mar  4 12:42:31 karmapolice kernel: [ 6307.700773]  [put_files_struct+237/288] put_files_struct+0xed/0x120
Mar  4 12:42:31 karmapolice kernel: [ 6307.700781]  [do_exit+413/2368] do_exit+0x19d/0x940
Mar  4 12:42:31 karmapolice kernel: [ 6307.700791]  [do_group_exit+44/128] do_group_exit+0x2c/0x80
Mar  4 12:42:31 karmapolice kernel: [ 6307.700796]  [system_call+126/131] system_call+0x7e/0x83
Mar  4 12:42:31 karmapolice kernel: [ 6307.700806] 
Mar  4 12:42:31 karmapolice kernel: [ 6307.700807] 
Mar  4 12:42:31 karmapolice kernel: [ 6307.700807] Code:  Bad RIP value.
Mar  4 12:42:31 karmapolice kernel: [ 6307.700809] RIP  [phys_startup_64+-2097152/-2147483648]
Mar  4 12:42:31 karmapolice kernel: [ 6307.700812]  RSP <ffff81007d113d50>
Mar  4 12:42:31 karmapolice kernel: [ 6307.700814] CR2: 0000004000000000
Mar  4 12:42:31 karmapolice kernel: [ 6307.700818] Fixing recursive fault but reboot is needed!
Mar  4 12:42:41 karmapolice kernel: [ 6317.837274] Unable to handle kernel NULL pointer dereference at 0000000000000008 RIP: 
Mar  4 12:42:41 karmapolice kernel: [ 6317.837280]  [task_rq_lock+64/144] task_rq_lock+0x40/0x90
Mar  4 12:42:41 karmapolice kernel: [ 6317.837287] PGD 67a12067 PUD 67a13067 PMD 0 
Mar  4 12:42:41 karmapolice kernel: [ 6317.837291] Oops: 0000 [3] SMP 
Mar  4 12:42:41 karmapolice kernel: [ 6317.837293] CPU 0 
Mar  4 12:42:41 karmapolice kernel: [ 6317.837295] Modules linked in: binfmt_misc ppdev powernow_k8 cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative video sbs button dock container ac battery xfs lp usb_storage ipv6 snd_via82xx snd_via82xx_modem snd_ac97_codec snd_seq_dummy ide_cd cdrom ac97_bus snd_pcm_oss snd_mixer_oss snd_seq_oss libusual snd_pcm snd_mpu401 snd_mpu401_uart analog snd_seq_midi nvidia(P) parport_pc parport gameport psmouse snd_seq_midi_event snd_seq snd_timer sky2 snd_rawmidi snd_seq_device i2c_viapro serio_raw snd soundcore snd_page_alloc ata_generic pcspkr k8temp i2c_core rt2500 shpchp pci_hotplug evdev ext3 jbd mbcache sg sd_mod floppy ehci_hcd via82cxxx ide_core uhci_hcd usbcore sata_via libata scsi_mod thermal processor fan fuse apparmor commoncap
Mar  4 12:42:41 karmapolice kernel: [ 6317.837330] Pid: 5386, comm: ktorrent Tainted: P       2.6.22-14-generic #1
Mar  4 12:42:41 karmapolice kernel: [ 6317.837333] RIP: 0010:[task_rq_lock+64/144]  [task_rq_lock+64/144] task_rq_lock+0x40/0x90
Mar  4 12:42:41 karmapolice kernel: [ 6317.837338] RSP: 0018:ffff810067b55b28  EFLAGS: 00010086
Mar  4 12:42:41 karmapolice kernel: [ 6317.837341] RAX: 0000000000000000 RBX: ffffffff805d0880 RCX: 0000000000000000
Mar  4 12:42:41 karmapolice kernel: [ 6317.837344] RDX: 0000000000000000 RSI: ffff810067b55b98 RDI: ffff8100754fd4a0
Mar  4 12:42:41 karmapolice kernel: [ 6317.837347] RBP: ffff810067b55b48 R08: 0000000000000000 R09: ffff8100719bb700
Mar  4 12:42:41 karmapolice kernel: [ 6317.837350] R10: 0000000001532120 R11: 0000000000000206 R12: ffffffff805d0880
Mar  4 12:42:41 karmapolice kernel: [ 6317.837353] R13: ffff8100754fd4a0 R14: ffff810067b55b98 R15: ffff810067b55b98
Mar  4 12:42:41 karmapolice kernel: [ 6317.837357] FS:  00002b43b742cd20(0000) GS:ffffffff80561000(0000) knlGS:00000000f682fb90
Mar  4 12:42:41 karmapolice kernel: [ 6317.837359] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar  4 12:42:41 karmapolice kernel: [ 6317.837362] CR2: 0000000000000008 CR3: 0000000067a11000 CR4: 00000000000006e0
Mar  4 12:42:41 karmapolice kernel: [ 6317.837365] Process ktorrent (pid: 5386, threadinfo ffff810067b54000, task ffff8100692554a0)
Mar  4 12:42:41 karmapolice kernel: [ 6317.837367] Stack:  0000000000000001 ffff8100754fd4a0 0000000000000001 ffff8100699570b8
Mar  4 12:42:41 karmapolice kernel: [ 6317.837372]  ffff810067b55bc8 ffffffff8022f2e2 00000000ffffffff 00000000000004d0
Mar  4 12:42:41 karmapolice kernel: [ 6317.837377]  ffffffff803ae891 ffffffff00000000 0000000000000000 0000000000000286
Mar  4 12:42:41 karmapolice kernel: [ 6317.837380] Call Trace:
Mar  4 12:42:41 karmapolice kernel: [ 6317.837387]  [try_to_wake_up+50/1008] try_to_wake_up+0x32/0x3f0
Mar  4 12:42:41 karmapolice kernel: [ 6317.837393]  [sock_alloc_send_skb+401/496] sock_alloc_send_skb+0x191/0x1f0
Mar  4 12:42:41 karmapolice kernel: [ 6317.837403]  [__wake_up_common+71/128] __wake_up_common+0x47/0x80
Mar  4 12:42:41 karmapolice kernel: [ 6317.837410]  [__wake_up+67/112] __wake_up+0x43/0x70
Mar  4 12:42:41 karmapolice kernel: [ 6317.837418]  [sock_def_readable+97/112] sock_def_readable+0x61/0x70
Mar  4 12:42:41 karmapolice kernel: [ 6317.837422]  [unix_stream_sendmsg+452/912] unix_stream_sendmsg+0x1c4/0x390
Mar  4 12:42:41 karmapolice kernel: [ 6317.837437]  [sock_aio_write+370/400] sock_aio_write+0x172/0x190
Mar  4 12:42:41 karmapolice kernel: [ 6317.837441]  [__wake_up+67/112] __wake_up+0x43/0x70
Mar  4 12:42:41 karmapolice kernel: [ 6317.837456]  [do_sync_write+217/288] do_sync_write+0xd9/0x120
Mar  4 12:42:41 karmapolice kernel: [ 6317.837467]  [autoremove_wake_function+0/48] autoremove_wake_function+0x0/0x30
Mar  4 12:42:41 karmapolice kernel: [ 6317.837475]  [_spin_lock_bh+9/32] _spin_lock_bh+0x9/0x20
Mar  4 12:42:41 karmapolice kernel: [ 6317.837478]  [unix_ioctl+225/240] unix_ioctl+0xe1/0xf0
Mar  4 12:42:41 karmapolice kernel: [ 6317.837482]  [mutex_lock+9/32] mutex_lock+0x9/0x20
Mar  4 12:42:41 karmapolice kernel: [ 6317.837486]  [pipe_ioctl+154/160] pipe_ioctl+0x9a/0xa0
Mar  4 12:42:41 karmapolice kernel: [ 6317.837490]  [pipe_ioctl+0/160] pipe_ioctl+0x0/0xa0
Mar  4 12:42:41 karmapolice kernel: [ 6317.837494]  [do_ioctl+154/224] do_ioctl+0x9a/0xe0
Mar  4 12:42:41 karmapolice kernel: [ 6317.837501]  [vfs_write+383/400] vfs_write+0x17f/0x190
Mar  4 12:42:41 karmapolice kernel: [ 6317.837506]  [sys_write+83/144] sys_write+0x53/0x90
Mar  4 12:42:41 karmapolice kernel: [ 6317.837513]  [system_call+126/131] system_call+0x7e/0x83
Mar  4 12:42:41 karmapolice kernel: [ 6317.837523] 
Mar  4 12:42:41 karmapolice kernel: [ 6317.837524] 
Mar  4 12:42:41 karmapolice kernel: [ 6317.837525] Code: 48 03 58 08 48 89 df e8 d4 5a 20 00 49 8b 45 08 8b 40 18 48 
Mar  4 12:42:41 karmapolice kernel: [ 6317.837532] RIP  [task_rq_lock+64/144] task_rq_lock+0x40/0x90
Mar  4 12:42:41 karmapolice kernel: [ 6317.837536]  RSP <ffff810067b55b28>
Mar  4 12:42:41 karmapolice kernel: [ 6317.837537] CR2: 0000000000000008
Mar  4 12:43:19 karmapolice kernel: [ 6355.236462] Unable to handle kernel NULL pointer dereference at 0000000000000008 RIP: 
Mar  4 12:43:19 karmapolice kernel: [ 6355.236466]  [task_rq_lock+64/144] task_rq_lock+0x40/0x90
Mar  4 12:43:19 karmapolice kernel: [ 6355.236472] PGD 69767067 PUD 69760067 PMD 0 
Mar  4 12:43:19 karmapolice kernel: [ 6355.236475] Oops: 0000 [4] SMP 
Mar  4 12:43:19 karmapolice kernel: [ 6355.236478] CPU 0 
Mar  4 12:43:19 karmapolice kernel: [ 6355.236479] Modules linked in: binfmt_misc ppdev powernow_k8 cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative video sbs button dock container ac battery xfs lp usb_storage ipv6 snd_via82xx snd_via82xx_modem snd_ac97_codec snd_seq_dummy ide_cd cdrom ac97_bus snd_pcm_oss snd_mixer_oss snd_seq_oss libusual snd_pcm snd_mpu401 snd_mpu401_uart analog snd_seq_midi nvidia(P) parport_pc parport gameport psmouse snd_seq_midi_event snd_seq snd_timer sky2 snd_rawmidi snd_seq_device i2c_viapro serio_raw snd soundcore snd_page_alloc ata_generic pcspkr k8temp i2c_core rt2500 shpchp pci_hotplug evdev ext3 jbd mbcache sg sd_mod floppy ehci_hcd via82cxxx ide_core uhci_hcd usbcore sata_via libata scsi_mod thermal processor fan fuse apparmor commoncap
Mar  4 12:43:19 karmapolice kernel: [ 6355.236511] Pid: 5368, comm: amarokapp Tainted: P       2.6.22-14-generic #1
Mar  4 12:43:19 karmapolice kernel: [ 6355.236514] RIP: 0010:[task_rq_lock+64/144]  [task_rq_lock+64/144] task_rq_lock+0x40/0x90
Mar  4 12:43:19 karmapolice kernel: [ 6355.236519] RSP: 0018:ffff8100695d5b28  EFLAGS: 00010086
Mar  4 12:43:19 karmapolice kernel: [ 6355.236521] RAX: 0000000000000000 RBX: ffffffff805d0880 RCX: 0000000000000000
Mar  4 12:43:19 karmapolice kernel: [ 6355.236524] RDX: 0000000000000000 RSI: ffff8100695d5b98 RDI: ffff8100754fd4a0
Mar  4 12:43:19 karmapolice kernel: [ 6355.236528] RBP: ffff8100695d5b48 R08: 0000000000000000 R09: ffff810071f26d00
Mar  4 12:43:19 karmapolice kernel: [ 6355.236531] R10: 00000000408029e0 R11: 0000000000000206 R12: ffffffff805d0880
Mar  4 12:43:19 karmapolice kernel: [ 6355.236534] R13: ffff8100754fd4a0 R14: ffff8100695d5b98 R15: ffff8100695d5b98
Mar  4 12:43:19 karmapolice kernel: [ 6355.236538] FS:  00002b0cbdf2b020(0000) GS:ffffffff80561000(0000) knlGS:00000000f682fb90
Mar  4 12:43:19 karmapolice kernel: [ 6355.236540] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Mar  4 12:43:19 karmapolice kernel: [ 6355.236543] CR2: 0000000000000008 CR3: 000000006f8e9000 CR4: 00000000000006e0
Mar  4 12:43:19 karmapolice kernel: [ 6355.236546] Process amarokapp (pid: 5368, threadinfo ffff8100695d4000, task ffff810069254dc0)
Mar  4 12:43:19 karmapolice kernel: [ 6355.236548] Stack:  0000000000000001 ffff8100754fd4a0 0000000000000001 ffff81006854e2f8
Mar  4 12:43:19 karmapolice kernel: [ 6355.236553]  ffff8100695d5bc8 ffffffff8022f2e2 00000000ffffffff 00000000000004d0
Mar  4 12:43:19 karmapolice kernel: [ 6355.236557]  ffffffff803ae891 ffffffff00000000 0000000000000000 0000000000000286
Mar  4 12:43:19 karmapolice kernel: [ 6355.236560] Call Trace:
Mar  4 12:43:19 karmapolice kernel: [ 6355.236567]  [try_to_wake_up+50/1008] try_to_wake_up+0x32/0x3f0
Mar  4 12:43:19 karmapolice kernel: [ 6355.236573]  [sock_alloc_send_skb+401/496] sock_alloc_send_skb+0x191/0x1f0
Mar  4 12:43:19 karmapolice kernel: [ 6355.236583]  [__wake_up_common+71/128] __wake_up_common+0x47/0x80
Mar  4 12:43:19 karmapolice kernel: [ 6355.236590]  [__wake_up+67/112] __wake_up+0x43/0x70
Mar  4 12:43:19 karmapolice kernel: [ 6355.236597]  [sock_def_readable+97/112] sock_def_readable+0x61/0x70
Mar  4 12:43:19 karmapolice kernel: [ 6355.236602]  [unix_stream_sendmsg+452/912] unix_stream_sendmsg+0x1c4/0x390
Mar  4 12:43:19 karmapolice kernel: [ 6355.236612]  [__rmqueue+172/288] __rmqueue+0xac/0x120
Mar  4 12:43:19 karmapolice kernel: [ 6355.236616]  [zone_statistics+125/128] zone_statistics+0x7d/0x80
Mar  4 12:43:19 karmapolice kernel: [ 6355.236623]  [sock_aio_write+370/400] sock_aio_write+0x172/0x190
Mar  4 12:43:19 karmapolice kernel: [ 6355.236626]  [__wake_up+67/112] __wake_up+0x43/0x70
Mar  4 12:43:19 karmapolice kernel: [ 6355.236641]  [do_sync_write+217/288] do_sync_write+0xd9/0x120
Mar  4 12:43:19 karmapolice kernel: [ 6355.236652]  [autoremove_wake_function+0/48] autoremove_wake_function+0x0/0x30
Mar  4 12:43:19 karmapolice kernel: [ 6355.236658]  [wake_up_new_task+478/656] wake_up_new_task+0x1de/0x290
Mar  4 12:43:19 karmapolice kernel: [ 6355.236668]  [_end+127582240/2130324728] :apparmor:apparmor_capable+0x18/0x50
Mar  4 12:43:19 karmapolice kernel: [ 6355.236672]  [mutex_lock+9/32] mutex_lock+0x9/0x20
Mar  4 12:43:19 karmapolice kernel: [ 6355.236676]  [pipe_ioctl+154/160] pipe_ioctl+0x9a/0xa0
Mar  4 12:43:19 karmapolice kernel: [ 6355.236685]  [vfs_write+383/400] vfs_write+0x17f/0x190
Mar  4 12:43:19 karmapolice kernel: [ 6355.236691]  [sys_write+83/144] sys_write+0x53/0x90
Mar  4 12:43:19 karmapolice kernel: [ 6355.236698]  [system_call+126/131] system_call+0x7e/0x83
Mar  4 12:43:19 karmapolice kernel: [ 6355.236708] 
Mar  4 12:43:19 karmapolice kernel: [ 6355.236709] 
Mar  4 12:43:19 karmapolice kernel: [ 6355.236709] Code: 48 03 58 08 48 89 df e8 d4 5a 20 00 49 8b 45 08 8b 40 18 48 
Mar  4 12:43:19 karmapolice kernel: [ 6355.236716] RIP  [task_rq_lock+64/144] task_rq_lock+0x40/0x90
Mar  4 12:43:19 karmapolice kernel: [ 6355.236720]  RSP <ffff8100695d5b28>
Mar  4 12:43:19 karmapolice kernel: [ 6355.236721] CR2: 0000000000000008
-----------------------------------------------------------------------------------------------

Thank you and sorry for my English.

---

### Post by fraia on 2008-03-04
If the screen is displaying crazy colors and lines it could be your video card

---

