---
title: "Gigabit ethernet not seen (thinkpad x60)"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by honeydew on 2007-07-16
I am using xubuntu 7.04 on my thinkpad x60.  Everything has been going fine and been working well.  Though I went to hook up via ethernet and I realized that there is no device recognized.  is it something different than eth0 for gb ethernet?  my chipset is intel pro 1000 lan adapter 

here is my lspci

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 09)
15:00.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
```

here is my dmesg I dont know if this will help anyone with this.. but I thought I might as well post it...

```
# dmesg 
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d2000 size: 0000000000002000 end: 00000000000d4000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007f5d0000 end: 000000007f6d0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007f6d0000 size: 000000000000f000 end: 000000007f6df000 type: 3
[    0.000000] copy_e820_map() start: 000000007f6df000 size: 0000000000021000 end: 000000007f700000 type: 4
[    0.000000] copy_e820_map() start: 000000007f700000 size: 0000000000900000 end: 0000000080000000 type: 2
[    0.000000] copy_e820_map() start: 00000000f0000000 size: 0000000004000000 end: 00000000f4000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed00000 size: 0000000000000400 end: 00000000fed00400 type: 2
[    0.000000] copy_e820_map() start: 00000000fed14000 size: 0000000000006000 end: 00000000fed1a000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed1c000 size: 0000000000074000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff800000 size: 0000000000800000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d0000 (usable)
[    0.000000]  BIOS-e820: 000000007f6d0000 - 000000007f6df000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f6df000 - 000000007f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f700000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f67f0
[    0.000000] Entering add_active_range(0, 0, 521936) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   521936
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   521936
[    0.000000] On node 0 totalpages: 521936
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2285 pages used for memmap
[    0.000000]   HighMem zone: 290275 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v002 LENOVO                                ) @ 0x000f67b0
[    0.000000] ACPI: XSDT (v001 LENOVO TP-7B    0x00002100  LTP 0x00000000) @ 0x7f6d1861
[    0.000000] ACPI: FADT (v003 LENOVO TP-7B    0x00002100 LNVO 0x00000001) @ 0x7f6d1900
[    0.000000] ACPI: SSDT (v001 LENOVO TP-7B    0x00002100 MSFT 0x0100000e) @ 0x7f6d1ab4
[    0.000000] ACPI: ECDT (v001 LENOVO TP-7B    0x00002100 LNVO 0x00000001) @ 0x7f6deb86
[    0.000000] ACPI: TCPA (v002 LENOVO TP-7B    0x00002100 LNVO 0x00000001) @ 0x7f6debd8
[    0.000000] ACPI: MADT (v001 LENOVO TP-7B    0x00002100 LNVO 0x00000001) @ 0x7f6dec0a
[    0.000000] ACPI: MCFG (v001 LENOVO TP-7B    0x00002100 LNVO 0x00000001) @ 0x7f6dec72
[    0.000000] ACPI: HPET (v001 LENOVO TP-7B    0x00002100 LNVO 0x00000001) @ 0x7f6decae
[    0.000000] ACPI: SLIC (v001 LENOVO TP-7B    0x00002100  LTP 0x00000000) @ 0x7f6dee62
[    0.000000] ACPI: BOOT (v001 LENOVO TP-7B    0x00002100  LTP 0x00000001) @ 0x7f6defd8
[    0.000000] ACPI: SSDT (v001 LENOVO TP-7B    0x00002100 INTL 0x20050513) @ 0x7f6f2645
[    0.000000] ACPI: SSDT (v001 LENOVO TP-7B    0x00002100 INTL 0x20050513) @ 0x7f6f28a4
[    0.000000] ACPI: SSDT (v001 LENOVO TP-7B    0x00002100 INTL 0x20050513) @ 0x7f6f294a
[    0.000000] ACPI: SSDT (v001 LENOVO TP-7B    0x00002100 INTL 0x20050513) @ 0x7f6f2e41
[    0.000000] ACPI: DSDT (v001 LENOVO TP-7B    0x00002100 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
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
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
[    0.000000] Detected 1662.570 MHz processor.
[   17.393980] Built 1 zonelists.  Total pages: 517859
[   17.393983] Kernel command line: root=UUID=f3fa22f5-0bb7-49fe-9631-acef3b177ef9 ro quiet splash
[   17.394128] mapped APIC to ffffd000 (fee00000)
[   17.394130] mapped IOAPIC to ffffc000 (fec00000)
[   17.394134] Enabling fast FPU save and restore... done.
[   17.394136] Enabling unmasked SIMD FPU exception support... done.
[   17.394143] Initializing CPU#0
[   17.394215] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   17.395818] Console: colour VGA+ 80x25
[   17.396094] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   17.396391] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.473300] Memory: 2058592k/2087744k available (1992k kernel code, 27860k reserved, 893k data, 328k init, 1170240k highmem)
[   17.473309] virtual kernel memory layout:
[   17.473310]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   17.473311]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.473312]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   17.473314]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   17.473315]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   17.473316]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   17.473317]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   17.473320] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.473494] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   17.473499] hpet0: 3 64-bit timers, 14318180 Hz
[   17.474505] Using HPET for base-timer
[   17.553375] Calibrating delay using timer specific routine.. 3328.81 BogoMIPS (lpj=6657627)
[   17.553417] Security Framework v1.0.0 initialized
[   17.553425] SELinux:  Disabled at boot.
[   17.553439] Mount-cache hash table entries: 512
[   17.553578] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   17.553585] monitor/mwait feature present.
[   17.553587] using mwait in idle threads.
[   17.553591] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.553594] CPU: L2 cache: 2048K
[   17.553596] CPU: Physical Processor ID: 0
[   17.553598] CPU: Processor Core ID: 0
[   17.553600] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   17.553609] Compat vDSO mapped to ffffe000.
[   17.553613] Remapping vsyscall page to ffffe000
[   17.553626] Checking 'hlt' instruction... OK.
[   17.569457] SMP alternatives: switching to UP code
[   17.569819] Early unpacking initramfs... done
[   17.895140] ACPI: Core revision 20060707
[   17.895413] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   17.922840] CPU0: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 02
[   17.922860] SMP alternatives: switching to SMP code
[   17.922943] Booting processor 1/1 eip 3000
[   17.933694] Initializing CPU#1
[   18.013014] Calibrating delay using timer specific routine.. 3325.09 BogoMIPS (lpj=6650190)
[   18.013020] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   18.013025] monitor/mwait feature present.
[   18.013028] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.013030] CPU: L2 cache: 2048K
[   18.013032] CPU: Physical Processor ID: 0
[   18.013033] CPU: Processor Core ID: 1
[   18.013035] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   18.013177] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 02
[   18.013199] Total of 2 processors activated (6653.90 BogoMIPS).
[   18.013395] ENABLING IO-APIC IRQs
[   18.013594] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.160450] checking TSC synchronization across 2 CPUs: 
[    0.000001] CPU#0 had -170 usecs TSC skew, fixed it up.
[    0.000003] CPU#1 had 170 usecs TSC skew, fixed it up.
[    0.003993] Brought up 2 CPUs
[    0.055305] migration_cost=36
[    0.055566] Booting paravirtualized kernel on bare hardware
[    0.055667] Time: 22:15:10  Date: 06/14/107
[    0.055695] NET: Registered protocol family 16
[    0.055779] EISA bus registered
[    0.055785] ACPI: bus type pci registered
[    0.055901] PCI: PCI BIOS revision 2.10 entry at 0xfd82b, last bus=24
[    0.055912] PCI: Using configuration type 1
[    0.055914] Setting up standard PCI resources
[    0.068151] ACPI: Interpreter enabled
[    0.068153] ACPI: Using IOAPIC for interrupt routing
[    0.068985] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.069578] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.070167] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.070754] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.071343] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.071938] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.072525] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    0.073112] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.073511] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.073515] PCI: Probing PCI hardware (bus 00)
[    0.074787] Boot video device is 0000:00:02.0
[    0.075486] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.075490] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.076709] PCI: Transparent bridge - 0000:00:1e.0
[    0.076862] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.081488] ACPI: Power Resource [PUBS] (on)
[    0.083122] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[    0.083303] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.083483] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.083701] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.083925] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.085563] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.085573] pnp: PnP ACPI init
[    0.089691] pnp: PnP ACPI: found 12 devices
[    0.089694] PnPBIOS: Disabled by ACPI PNP
[    0.089738] PCI: Using ACPI for IRQ routing
[    0.089740] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.154557] NET: Registered protocol family 8
[    0.154560] NET: Registered protocol family 20
[    0.155609] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    0.155613] PCI: Bridge: 0000:00:1c.0
[    0.155616]   IO window: 2000-2fff
[    0.155622]   MEM window: ee000000-ee0fffff
[    0.155628]   PREFETCH window: disabled.
[    0.155633] PCI: Bridge: 0000:00:1c.1
[    0.155637]   IO window: 3000-4fff
[    0.155643]   MEM window: ec000000-edffffff
[    0.155648]   PREFETCH window: e4000000-e40fffff
[    0.155653] PCI: Bridge: 0000:00:1c.2
[    0.155657]   IO window: 5000-6fff
[    0.155663]   MEM window: e8000000-e9ffffff
[    0.155668]   PREFETCH window: e4100000-e41fffff
[    0.155674] PCI: Bridge: 0000:00:1c.3
[    0.155677]   IO window: 7000-8fff
[    0.155683]   MEM window: ea000000-ebffffff
[    0.155688]   PREFETCH window: e4200000-e42fffff
[    0.155697] PCI: Bus 22, cardbus bridge: 0000:15:00.0
[    0.155699]   IO window: 00009000-000090ff
[    0.155704]   IO window: 00009400-000094ff
[    0.155710]   PREFETCH window: e0000000-e3ffffff
[    0.155716]   MEM window: 88000000-8bffffff
[    0.155721] PCI: Bridge: 0000:00:1e.0
[    0.155724]   IO window: 9000-cfff
[    0.155731]   MEM window: e4300000-e7ffffff
[    0.155735]   PREFETCH window: e0000000-e3ffffff
[    0.155773] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 16
[    0.155780] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.155805] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 21 (level, low) -> IRQ 17
[    0.155811] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.155835] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 18
[    0.155841] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.155865] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 23 (level, low) -> IRQ 19
[    0.155871] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.155882] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
[    0.155889] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.155908] ACPI: PCI Interrupt 0000:15:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[    0.155914] PCI: Setting latency timer of device 0000:15:00.0 to 64
[    0.155943] NET: Registered protocol family 2
[    0.207722] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.207824] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.208291] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.208534] TCP: Hash tables configured (established 131072 bind 65536)
[    0.208536] TCP reno registered
[    0.223768] checking if image is initramfs... it is
[    0.864134] Freeing initrd memory: 6994k freed
[    0.864309] Simple Boot Flag at 0x35 set to 0x1
[    0.864764] audit: initializing netlink socket (disabled)
[    0.864780] audit(1184451311.616:1): initialized
[    0.864876] highmem bounce pool size: 64 pages
[    0.864961] VFS: Disk quotas dquot_6.5.1
[    0.864980] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.865029] io scheduler noop registered
[    0.865032] io scheduler anticipatory registered
[    0.865034] io scheduler deadline registered
[    0.865045] io scheduler cfq registered (default)
[    0.865298] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.865357] assign_interrupt_mode Found MSI capability
[    0.865360] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.865395] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.865523] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.865582] assign_interrupt_mode Found MSI capability
[    0.865584] Allocate Port Service[0000:00:1c.1:pcie00]
[    0.865616] Allocate Port Service[0000:00:1c.1:pcie02]
[    0.865739] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.865798] assign_interrupt_mode Found MSI capability
[    0.865800] Allocate Port Service[0000:00:1c.2:pcie00]
[    0.865832] Allocate Port Service[0000:00:1c.2:pcie02]
[    0.865956] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.866015] assign_interrupt_mode Found MSI capability
[    0.866017] Allocate Port Service[0000:00:1c.3:pcie00]
[    0.866049] Allocate Port Service[0000:00:1c.3:pcie02]
[    0.866237] isapnp: Scanning for PnP cards...
[    1.219974] isapnp: No Plug & Play device found
[    1.240721] Real Time Clock Driver v1.12ac
[    1.240779] hpet_resources: 0xfed00000 is busy
[    1.240805] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.241490] mice: PS/2 mouse device common for all mice
[    1.242038] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.242286] input: Macintosh mouse button emulation as /class/input/input0
[    1.242321] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.242326] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.242620] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.255175] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.255178] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.255293] EISA: Probing bus 0 at eisa.0
[    1.255301] Cannot allocate resource for EISA slot 1
[    1.255305] Cannot allocate resource for EISA slot 2
[    1.255307] Cannot allocate resource for EISA slot 3
[    1.255309] Cannot allocate resource for EISA slot 4
[    1.255311] Cannot allocate resource for EISA slot 5
[    1.255313] Cannot allocate resource for EISA slot 6
[    1.255315] Cannot allocate resource for EISA slot 7
[    1.255317] Cannot allocate resource for EISA slot 8
[    1.255319] EISA: Detected 0 cards.
[    1.285366] TCP cubic registered
[    1.285375] NET: Registered protocol family 1
[    1.285395] Starting balanced_irq
[    1.285401] Using IPI No-Shortcut mode
[    1.285521] ACPI: (supports S0 S3 S4 S5)
[    1.285570]   Magic number: 15:112:300
[    1.285819] Freeing unused kernel memory: 328k freed
[    1.286037] Time: tsc clocksource has been installed.
[    1.290140] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.482415] Capability LSM initialized
[    2.518430] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    2.518794] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    2.519685] Monitor-Mwait will be used to enter C-1 state
[    2.519688] Monitor-Mwait will be used to enter C-2 state
[    2.519691] Monitor-Mwait will be used to enter C-3 state
[    2.519697] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.519701] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.520270] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    2.520545] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    2.521503] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.521510] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.092000] ACPI: Thermal Zone [THM0] (61 C)
[    3.096000] ACPI: Thermal Zone [THM1] (59 C)
[    3.100000] Time: hpet clocksource has been installed.
[    3.436000] usbcore: registered new interface driver usbfs
[    3.436000] usbcore: registered new interface driver hub
[    3.444000] usbcore: registered new device driver usb
[    3.496000] USB Universal Host Controller Interface driver v3.0
[    3.496000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 20
[    3.496000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.496000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.496000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.496000] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[    3.500000] usb usb1: configuration #1 chosen from 1 choice
[    3.500000] hub 1-0:1.0: USB hub found
[    3.500000] hub 1-0:1.0: 2 ports detected
[    3.524000] SCSI subsystem initialized
[    3.536000] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[    3.536000] Copyright (c) 1999-2006 Intel Corporation.
[    3.540000] libata version 2.20 loaded.
[    3.544000] ieee1394: Initialized config rom entry `ip1394'
[    3.604000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 21
[    3.604000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.604000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.604000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.604000] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001840
[    3.604000] usb usb2: configuration #1 chosen from 1 choice
[    3.604000] hub 2-0:1.0: USB hub found
[    3.604000] hub 2-0:1.0: 2 ports detected
[    3.708000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 22
[    3.708000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.708000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.708000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.708000] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00001860
[    3.708000] usb usb3: configuration #1 chosen from 1 choice
[    3.708000] hub 3-0:1.0: USB hub found
[    3.708000] hub 3-0:1.0: 2 ports detected
[    3.812000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 23
[    3.812000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.812000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.812000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.812000] uhci_hcd 0000:00:1d.3: irq 23, io base 0x00001880
[    3.812000] usb usb4: configuration #1 chosen from 1 choice
[    3.812000] hub 4-0:1.0: USB hub found
[    3.812000] hub 4-0:1.0: 2 ports detected
[    3.844000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    3.916000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[    3.916000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    3.976000] e1000: 0000:02:00.0: e1000_probe: The EEPROM Checksum Is Not Valid
[    3.996000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[    3.996000] e1000: probe of 0000:02:00.0 failed with error -5
[    3.996000] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.996000] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 20
[    3.996000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.996000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.000000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    4.000000] scsi0 : ata_piix
[    4.020000] usb 1-1: configuration #1 chosen from 1 choice
[    4.020000] hub 1-1:1.0: USB hub found
[    4.024000] hub 1-1:1.0: 3 ports detected
[    4.156000] ATA: abnormal status 0x7F on port 0x000101f7
[    4.160000] scsi1 : ata_piix
[    4.164000] ata2: port disabled. ignoring.
[    4.164000] ACPI: PCI Interrupt 0000:15:00.1[B] -> GSI 17 (level, low) -> IRQ 21
[    4.164000] PCI: Setting latency timer of device 0000:15:00.1 to 64
[    4.216000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[e4301000-e43017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.224000] ahci 0000:00:1f.2: version 2.1
[    4.224000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 20
[    4.388000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[    4.568000] usb 1-2: configuration #1 chosen from 1 choice
[    4.812000] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    4.988000] usb 4-2: configuration #1 chosen from 1 choice
[    5.196000] usb 1-1.2: new full speed USB device using uhci_hcd and address 4
[    5.228000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.228000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x1 impl SATA mode
[    5.228000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    5.228000] ata3: SATA max UDMA/133 cmd 0xf894c500 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.228000] ata4: SATA max UDMA/133 cmd 0xf894c580 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.228000] ata5: SATA max UDMA/133 cmd 0xf894c600 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.228000] ata6: SATA max UDMA/133 cmd 0xf894c680 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.228000] scsi2 : ahci
[    5.332000] usb 1-1.2: configuration #1 chosen from 1 choice
[    5.496000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000ae4070012206b]
[    5.536000] usb 1-1.3: new full speed USB device using uhci_hcd and address 5
[    5.672000] usb 1-1.3: configuration #1 chosen from 1 choice
[    5.676000] usbcore: registered new interface driver hiddev
[    5.692000] input: Microsoft Microsoft IntelliMouse&#65533; Optical as /class/input/input2
[    5.692000] input: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse&#65533; Optical] on usb-0000:00:1d.0-2
[    5.696000] input: Broadcom Corp BCM2045B3 ROM as /class/input/input3
[    5.696000] input: USB HID v1.11 Keyboard [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:1d.0-1.2
[    5.696000] input: Broadcom Corp BCM2045B3 ROM as /class/input/input4
[    5.696000] input: USB HID v1.11 Mouse [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:1d.0-1.3
[    5.696000] usbcore: registered new interface driver usbhid
[    5.696000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    5.712000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.712000] ata3.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[    5.712000] ata3.00: ATA-7: HTS721060G9SA00, MC3IC14V, max UDMA/100
[    5.712000] ata3.00: 117210240 sectors, multi 16: LBA48 
[    5.712000] ata3.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[    5.712000] ata3.00: configured for UDMA/100
[    5.712000] scsi3 : ahci
[    6.024000] ata4: SATA link down (SStatus 0 SControl 0)
[    6.024000] scsi4 : ahci
[    6.336000] ata5: SATA link down (SStatus 0 SControl 0)
[    6.336000] scsi5 : ahci
[    6.648000] ata6: SATA link down (SStatus 0 SControl 0)
[    6.648000] scsi 2:0:0:0: Direct-Access     ATA      HTS721060G9SA00  MC3I PQ: 0 ANSI: 5
[    6.652000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 23
[    6.652000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    6.652000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    6.652000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    6.652000] ehci_hcd 0000:00:1d.7: debug port 1
[    6.652000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    6.652000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xee444000
[    6.656000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.656000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    6.656000] sda: Write Protect is off
[    6.656000] sda: Mode Sense: 00 3a 00 00
[    6.656000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.656000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    6.656000] sda: Write Protect is off
[    6.656000] sda: Mode Sense: 00 3a 00 00
[    6.656000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.656000]  sda:<6>usb usb5: configuration #1 chosen from 1 choice
[    6.656000] hub 5-0:1.0: USB hub found
[    6.656000] hub 5-0:1.0: 8 ports detected
[    6.688000] usb 4-2: USB disconnect, address 2
[    6.984000]  sda2 < sda5 sda6 >
[    6.984000] sd 2:0:0:0: Attached scsi disk sda
[    6.988000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    7.152000] Attempting manual resume
[    7.152000] swsusp: Resume From Partition 8:5
[    7.152000] PM: Checking swsusp image.
[    7.152000] PM: Resume from disk failed.
[    7.188000] kjournald starting.  Commit interval 5 seconds
[    7.188000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.368000] usb 1-1: USB disconnect, address 2
[    7.368000] usb 1-1.2: USB disconnect, address 4
[    7.368000] usb 1-1.3: USB disconnect, address 5
[    7.608000] usb 1-1: new full speed USB device using uhci_hcd and address 6
[    7.788000] usb 1-1: configuration #1 chosen from 1 choice
[    7.792000] hub 1-1:1.0: USB hub found
[    7.792000] hub 1-1:1.0: 3 ports detected
[    7.904000] usb 1-2: USB disconnect, address 3
[    8.144000] usb 1-2: new low speed USB device using uhci_hcd and address 7
[    8.324000] usb 1-2: configuration #1 chosen from 1 choice
[    8.344000] input: Microsoft Microsoft IntelliMouse&#65533; Optical as /class/input/input5
[    8.344000] input: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse&#65533; Optical] on usb-0000:00:1d.0-2
[    8.584000] usb 4-2: new full speed USB device using uhci_hcd and address 3
[    8.760000] usb 4-2: configuration #1 chosen from 1 choice
[    8.968000] usb 1-1.2: new full speed USB device using uhci_hcd and address 8
[    9.112000] usb 1-1.2: configuration #1 chosen from 1 choice
[    9.120000] input: Broadcom Corp BCM2045B3 ROM as /class/input/input6
[    9.120000] input: USB HID v1.11 Keyboard [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:1d.0-1.2
[    9.320000] usb 1-1.3: new full speed USB device using uhci_hcd and address 9
[    9.464000] usb 1-1.3: configuration #1 chosen from 1 choice
[    9.468000] input: Broadcom Corp BCM2045B3 ROM as /class/input/input7
[    9.472000] input: USB HID v1.11 Mouse [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:1d.0-1.3
[   16.240000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.244000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.496000] input: PC Speaker as /class/input/input8
[   16.532000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.564000] agpgart: Detected an Intel 945GM Chipset.
[   16.564000] agpgart: Detected 7932K stolen memory.
[   16.580000] agpgart: AGP aperture is 256M @ 0xd0000000
[   16.716000] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:201c]
[   16.728000] iTCO_vendor_support: vendor-support=0
[   16.816000] irda_init()
[   16.816000] NET: Registered protocol family 23
[   16.840000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   16.840000] ath_hal: module license 'Proprietary' taints kernel.
[   16.844000] Yenta: ISA IRQ mask 0x04b8, PCI irq 20
[   16.844000] Socket status: 30000006
[   16.844000] pcmcia: parent PCI bridge I/O window: 0x9000 - 0xcfff
[   16.844000] cs: IO port probe 0x9000-0xcfff: clean.
[   16.844000] pcmcia: parent PCI bridge Memory window: 0xe4300000 - 0xe7ffffff
[   16.844000] pcmcia: parent PCI bridge Memory window: 0xe0000000 - 0xe3ffffff
[   16.844000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   16.968000] wlan: 0.8.4.2 (0.9.3)
[   16.984000] sdhci: Secure Digital Host Controller Interface driver
[   16.984000] sdhci: Copyright(c) Pierre Ossman
[   16.984000] sdhci: SDHCI controller found at 0000:15:00.2 [1180:0822] (rev 18)
[   16.984000] ACPI: PCI Interrupt 0000:15:00.2[C] -> GSI 18 (level, low) -> IRQ 22
[   16.984000] PCI: Setting latency timer of device 0000:15:00.2 to 64
[   16.984000] mmc0: SDHCI at 0xe4301800 irq 22 DMA
[   17.020000] ath_pci: 0.9.4.5 (0.9.3)
[   17.020000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 21
[   17.020000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   17.616000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   17.632000] cs: IO port probe 0x100-0x3af: clean.
[   17.636000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   17.636000] cs: IO port probe 0x820-0x8ff:<6>input: TPPS/2 IBM TrackPoint as /class/input/input9
[   17.636000]  clean.
[   17.636000] cs: IO port probe 0xc00-0xcf7: clean.
[   17.636000] cs: IO port probe 0xa00-0xaff: clean.
[   17.640000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   17.640000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.640000] pnp: Device 00:0a activated.
[   17.640000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   17.640000] nsc-ircc, chip->init
[   17.640000] nsc-ircc, Found chip at base=0x164e
[   17.640000] nsc-ircc, driver loaded (Dag Brattli)
[   17.640000] IrDA: Registered device irda0
[   17.640000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   17.660000] ath_rate_sample: 1.2 (0.9.3)
[   17.660000] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   17.660000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   17.660000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   17.660000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   17.660000] wifi0: mac 10.3 phy 6.1 radio 10.2
[   17.660000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   17.660000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   17.660000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   17.660000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   17.660000] wifi0: Use hw queue 8 for CAB traffic
[   17.660000] wifi0: Use hw queue 9 for beacons
[   17.724000] wifi0: Atheros 5212: mem=0xedf00000, irq=21
[   17.732000] intel_rng: FWH not detected
[   17.884000] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 21
[   17.884000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   18.316000] fuse init (API version 7.8)
[   18.376000] lp: driver loaded but no devices found
[   18.420000] Adding 2409708k swap on /dev/disk/by-uuid/5f230891-dbd2-44b5-b641-0c9df57def83.  Priority:-1 extents:1 across:2409708k
[   18.520000] EXT3 FS on sda6, internal journal
[   18.960000] NET: Registered protocol family 17
[   24.192000] ACPI: Battery Slot [BAT0] (battery present)
[   24.292000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   24.292000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   24.312000] input: Power Button (FF) as /class/input/input10
[   24.312000] ACPI: Power Button (FF) [PWRF]
[   24.312000] input: Lid Switch as /class/input/input11
[   24.312000] ACPI: Lid Switch [LID]
[   24.312000] input: Sleep Button (CM) as /class/input/input12
[   24.312000] ACPI: Sleep Button (CM) [SLPB]
[   24.364000] ACPI: AC Adapter [AC] (on-line)
[   24.412000] Using specific hotkey driver
[   24.460000] ibm_acpi: ThinkPad EC firmware 7BHT40WW-1.13
[   24.460000] ibm_acpi: IBM ThinkPad ACPI Extras v0.13
[   24.460000] ibm_acpi: http://ibm-acpi.sf.net/
[   24.512000] ACPI: ACPI Dock Station Driver 
[   24.580000] pcc_acpi: loading...
[   28.688000] NET: Registered protocol family 10
[   28.688000] lo: Disabled Privacy Extensions
[   29.948000] [drm] Initialized drm 1.1.0 20060810
[   29.948000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 20
[   29.948000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   30.584000] ppdev: user-space parallel port driver
[   31.324000] apm: BIOS not found.
[   31.456000] Non-volatile memory driver v1.2
[   31.472000] input: /usr/sbin/thinkpad-keys as /class/input/input13
[   31.600000] vboxdrv: Trying to deactivate NMI watchdog permanently...
[   31.600000] vboxdrv: Successfully done.
[   39.348000] ath0: no IPv6 routers present
[  890.732000] usb 5-5: new high speed USB device using ehci_hcd and address 5
[  890.864000] usb 5-5: configuration #1 chosen from 1 choice
[  891.280000] usbcore: registered new interface driver libusual
[  891.324000] Initializing USB Mass Storage driver...
[  891.324000] scsi6 : SCSI emulation for USB Mass Storage devices
[  891.324000] usb-storage: device found at 5
[  891.324000] usbcore: registered new interface driver usb-storage
[  891.324000] usb-storage: waiting for device to settle before scanning
[  891.324000] USB Mass Storage support registered.
[  896.324000] usb-storage: device scan complete
[  902.048000] usb 5-5: USB disconnect, address 5
[  902.048000] scsi 6:0:0:0: scsi: Device offlined - not ready after error recovery
[ 1052.220000] usb 5-5: new high speed USB device using ehci_hcd and address 6
[ 1052.352000] usb 5-5: configuration #1 chosen from 1 choice
[ 1052.352000] scsi7 : SCSI emulation for USB Mass Storage devices
[ 1052.352000] usb-storage: device found at 6
[ 1052.352000] usb-storage: waiting for device to settle before scanning
[ 1057.352000] usb-storage: device scan complete
[ 1057.356000] scsi 7:0:0:0: Direct-Access     ST312002 6A               0811 PQ: 0 ANSI: 0
[ 1057.356000] SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
[ 1057.356000] sdb: test WP failed, assume Write Enabled
[ 1057.356000] sdb: assuming drive cache: write through
[ 1057.360000] SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
[ 1057.360000] sdb: test WP failed, assume Write Enabled
[ 1057.360000] sdb: assuming drive cache: write through
[ 1057.360000]  sdb: unknown partition table
[ 1057.384000] sd 7:0:0:0: Attached scsi disk sdb
[ 1057.384000] sd 7:0:0:0: Attached scsi generic sg1 type 0
[ 1057.816000] kjournald starting.  Commit interval 5 seconds
[ 1057.816000] EXT3 FS on sdb, internal journal
[ 1057.816000] EXT3-fs: mounted filesystem with ordered data mode.
[ 1418.620000] usb 1-1.1: new full speed USB device using uhci_hcd and address 10
[ 1418.752000] usb 1-1.1: configuration #1 chosen from 1 choice
[ 1418.952000] Bluetooth: Core ver 2.11
[ 1418.952000] NET: Registered protocol family 31
[ 1418.952000] Bluetooth: HCI device and connection manager initialized
[ 1418.952000] Bluetooth: HCI socket layer initialized
[ 1418.984000] Bluetooth: HCI USB driver ver 2.9
[ 1418.984000] usbcore: registered new interface driver hci_usb
[63076.236000] usb 5-5: USB disconnect, address 6
[63076.744000] scsi 7:0:0:0: rejecting I/O to dead device
[63076.744000] Buffer I/O error on device sdb, logical block 1545
[63076.744000] lost page write due to I/O error on sdb
[63076.744000] scsi 7:0:0:0: rejecting I/O to dead device
[63076.744000] Buffer I/O error on device sdb, logical block 1545
[63076.744000] lost page write due to I/O error on sdb
[63076.744000] scsi 7:0:0:0: rejecting I/O to dead device
[63076.744000] Buffer I/O error on device sdb, logical block 1545
[63076.744000] lost page write due to I/O error on sdb
[63076.744000] scsi 7:0:0:0: rejecting I/O to dead device
[63076.744000] Buffer I/O error on device sdb, logical block 0
[63076.744000] lost page write due to I/O error on sdb
[164039.872000] ADDRCONF(NETDEV_UP): ath0: link is not ready
[164050.064000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[164060.964000] ath0: no IPv6 routers present
[164132.824000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[164148.156000] ath0: no IPv6 routers present

```

thanks for the help!

---

### Post by honeydew on 2007-07-17
any ideas?

---

### Post by gerni on 2007-07-18
i think i had the same problem. try to unload the e1000 module and then load it again:
rmmod e1000
modprobe e1000
If the interface (eth0) then appears you have the same problem than i had. If i remember correctly it was a bios update that solved the problem.

greets,
gernot

---

### Post by honeydew on 2007-08-07
thanks gernot.. I ended up reinstalling ubuntu and using eth0 as the port for networking during the install. Everything is working now.

---

### Post by Charkel on 2007-11-05
> **gerni said:**
> i think i had the same problem. try to unload the e1000 module and then load it again:
rmmod e1000
modprobe e1000
If the interface (eth0) then appears you have the same problem than i had. If i remember correctly it was a bios update that solved the problem.

greets,
gernot

Thank you! I had the same problem but that solved it :D

Dunno what the hell it did tho, but it worked. Would you like to explain exactly what I did?

---

### Post by honeydew on 2007-11-06
modprobe loads drivers.. the e1000 is a driver.. thus you loaded the driver and and then brought the interface up with ifconfig..

---

### Post by Verner on 2007-11-14
Sorry for bumping. What if i unload and load the drivers and then the interface doesnt show up with ifconfig? Hopeful for answer :)

---

### Post by honeydew on 2007-11-14
maybe try 

```
ifconfig up eth0   ## or other interface name..
```

---

