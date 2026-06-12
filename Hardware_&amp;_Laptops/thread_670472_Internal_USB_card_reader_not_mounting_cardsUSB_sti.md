---
title: "Internal USB card reader not mounting cards/USB sticks"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by Prodromoi on 2008-01-17
I have just replaced the card reader in my machine and the new one is being seen by the BIOS, but not by Ubuntu.

I am running 64-bit 7.10 on an AMD64 4000+.  The motherboard has two 9-pin USB connectors.  The previous card read was a bit over-fancy and required connections into both USB connectors on the motherboard.  The new one is a bit simpler and only requires one - thus freeing up the second.

The card reader does work - I've tested it in another machine.
The BIOS seems to be able to see the reader - in "USB Configuration" it reports 1 mouse and 4 drives, which would seem to be correct.

When I insert a CF card, SD card or USB stick into the reader - nothing happens.  Nothing mounts, the USB light does not start flickering (it lights just once for a split second).  

The power light on the card reader remains on constantly.  Nothing causes the access light to flicker or light.

Could it be that the configuration of the previous card reader has been retained and is conflicting with the new one?  Can someone please give me some (newbie-friendly!) guidelines as to how to get the new reader recognised by my OS?

Thanks in advance.

---

### Post by theophile on 2008-01-17
Could we have the outputs of 'lsusb', 'lspci -v' and 'dmesg'?

---

### Post by Prodromoi on 2008-01-17
```
~$ lsusb
Bus 009 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1267:0212 Logic3 / SpectraVideo plc 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 04a9:2220 Canon, Inc. 
Bus 002 Device 001: ID 0000:0000  
```

The Canon entry will be the scanner, the Logic3 entry will be the mouse I assume, although it's not a Logitech.


```
~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
        Subsystem: VIA Technologies, Inc. K8M890CE Host Bridge
        Flags: bus master, medium devsel, latency 64
        Memory at c8000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
        Subsystem: ASUSTeK Computer Inc. Unknown device 80ed
        Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
        Subsystem: ASUSTeK Computer Inc. Unknown device 80ed
        Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
        Subsystem: ASUSTeK Computer Inc. Unknown device 80ed
        Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
        Subsystem: ASUSTeK Computer Inc. Unknown device 80ed
        Flags: bus master, medium devsel, latency 0

00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller (prog-if 20 [IO(X)-APIC])
        Subsystem: ASUSTeK Computer Inc. Unknown device 80ed
        Flags: bus master, fast devsel, latency 0

00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6290
        Subsystem: Unknown device 0008:0000
        Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
        Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Capabilities: <access denied>

00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: f9000000-fbcfffff
        Prefetchable memory behind bridge: 0000000090000000-000000009fffffff
        Capabilities: <access denied>

00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fbd00000-fbdfffff
        Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 80ed
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at cc00 [size=8]
        I/O ports at c880 [size=4]
        I/O ports at c800 [size=8]
        I/O ports at c480 [size=4]
        I/O ports at c400 [size=16]
        I/O ports at c000 [size=256]
        Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 32
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at fc00 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at bc00 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 22
        I/O ports at b880 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at b800 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 23
        I/O ports at b480 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at f8fffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
        Subsystem: ASUSTeK Computer Inc. Unknown device 80ed
        Flags: medium devsel
        Capabilities: <access denied>

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
        Subsystem: VIA Technologies, Inc. Unknown device 337e
        Flags: bus master, medium devsel, latency 128
        Capabilities: <access denied>

00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: fbe00000-fbefffff
        Capabilities: <access denied>

00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fbf00000-fbffffff
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc. Unknown device 2208
        Flags: bus master, fast devsel, latency 0, IRQ 24
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at 90000000 (64-bit, prefetchable) [size=256M]
        Memory at f9000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fbce0000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81e4
        Flags: bus master, fast devsel, latency 0, IRQ 28
        Memory at fbdfe000 (32-bit, non-prefetchable) [size=8K]
        Expansion ROM at fbde0000 [disabled] [size=64K]
        Capabilities: <access denied>

03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81e4
        Flags: bus master, fast devsel, latency 0, IRQ 29
        I/O ports at dc00 [size=8]
        I/O ports at d880 [size=4]
        I/O ports at d800 [size=8]
        I/O ports at d480 [size=4]
        I/O ports at d400 [size=16]
        Capabilities: <access denied>

04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8249
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fbefc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

05:07.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fbfff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

05:07.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at fbffe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

05:07.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at fbffd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

05:07.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: ALi Corporation Unknown device 5272
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at fbffcc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

05:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at e800 [size=256]
        Memory at fbffc800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

```



The output of dmesg is too long, I think to get in the terminal window at once.  I cannot scroll back to the command line and start of the report.  Can I output it to a file to copy?

---

### Post by Prodromoi on 2008-01-17
Aha, worked out how to output dmesg to file:

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 05:28:27 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] Command line: root=UUID=524f95fa-19a4-4a98-85b6-8a4adb3cd71f ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b000 (usable)
[    0.000000]  BIOS-e820: 000000000009b000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e9c40 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffbe000 - 000000007ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecc0000 - 00000000fecc1000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 155) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524208) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FA910 checksum 0
[    0.000000] ACPI: RSDP 000FA910, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FFB0000, 0040 (r1 NEC              5000715 MSFT       97)
[    0.000000] ACPI: FACP 7FFB0200, 0084 (r2 A_M_I_ OEMFACP   5000715 MSFT       97)
[    0.000000] ACPI: DSDT 7FFB05C0, 5A0E (r1  A0654 A0654000        0 INTL  2002026)
[    0.000000] ACPI: FACS 7FFBE000, 0040
[    0.000000] ACPI: APIC 7FFB0390, 0068 (r1 A_M_I_ OEMAPIC   5000715 MSFT       97)
[    0.000000] ACPI: SLIC 7FFB0400, 0176 (r1 NEC              5000715 MSFT       97)
[    0.000000] ACPI: MCFG 7FFB0580, 003C (r1 A_M_I_ OEMMCFG   5000715 MSFT       97)
[    0.000000] ACPI: OEMB 7FFBE040, 0046 (r1 A_M_I_ AMI_OEM   5000715 MSFT       97)
[    0.000000] ACPI: HPET 7FFB5FD0, 0038 (r1 A_M_I_ OEMHPET   5000715 MSFT       97)
[    0.000000] ACPI: SSDT 7FFB6010, 0206 (r1 A_M_I_ POWERNOW        1 AMD         1)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007ffb0000
[    0.000000] Entering add_active_range(0, 0, 155) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524208) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007ffb0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      155
[    0.000000]     0:      256 ->   524208
[    0.000000] On node 0 totalpages: 524107
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1125 pages reserved
[    0.000000]   DMA zone: 2814 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7110 pages used for memmap
[    0.000000]   DMA32 zone: 513002 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x11068201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009b000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000ea000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ea000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515816
[    0.000000] Kernel command line: root=UUID=524f95fa-19a4-4a98-85b6-8a4adb3cd71f ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[   21.344181] time.c: Detected 2099.999 MHz processor.
[   21.346687] Console: colour VGA+ 80x25
[   21.346703] Checking aperture...
[   21.346706] CPU 0: aperture @ d0000000 size 128 MB
[   21.363306] Memory: 2055856k/2096832k available (2274k kernel code, 40572k reserved, 1181k data, 296k init)
[   21.363350] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   21.440439] Calibrating delay using timer specific routine.. 4202.25 BogoMIPS (lpj=8404502)
[   21.440468] Security Framework v1.0.0 initialized
[   21.440473] SELinux:  Disabled at boot.
[   21.440622] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   21.441672] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   21.442169] Mount-cache hash table entries: 256
[   21.442288] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.442291] CPU: L2 Cache: 512K (64 bytes/line)
[   21.442293] CPU 0/0 -> Node 0
[   21.442295] CPU: Physical Processor ID: 0
[   21.442297] CPU: Processor Core ID: 0
[   21.442314] SMP alternatives: switching to UP code
[   21.442541] Early unpacking initramfs... done
[   21.720526] ACPI: Core revision 20070126
[   21.720579] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.763598] Using local APIC timer interrupts.
[   21.811159] result 12499988
[   21.811161] Detected 12.499 MHz APIC timer.
[   21.812024] SMP alternatives: switching to SMP code
[   21.812126] Booting processor 1/2 APIC 0x1
[   21.822406] Initializing CPU#1
[   21.899999] Calibrating delay using timer specific routine.. 4200.07 BogoMIPS (lpj=8400145)
[   21.900006] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.900008] CPU: L2 Cache: 512K (64 bytes/line)
[   21.900010] CPU 1/1 -> Node 0
[   21.900012] CPU: Physical Processor ID: 0
[   21.900013] CPU: Processor Core ID: 1
[   21.900105] AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ stepping 01
[   21.903858] Brought up 2 CPUs
[   22.667478] migration_cost=183
[   22.667511] NET: Registered protocol family 16
[   22.667593] ACPI: bus type pci registered
[   22.667599] PCI: Using configuration type 1
[   22.669901] ACPI: EC: Look up EC in DSDT
[   22.675911] ACPI: Interpreter enabled
[   22.675914] ACPI: (supports S0 S1 S3 S4 S5)
[   22.675931] ACPI: Using IOAPIC for interrupt routing
[   22.676133] Error attaching device data
[   22.676137] Error attaching device data
[   22.686029] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.686038] PCI: Probing PCI hardware (bus 00)
[   22.687774] PCI: Transparent bridge - 0000:00:13.1
[   22.687838] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.687993] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   22.688073] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBPG._PRT]
[   22.688160] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP0._PRT]
[   22.688269] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[   22.688346] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]
[   22.705543] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   22.705664] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   22.705779] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   22.705893] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   22.706006] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   22.706121] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   22.706236] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   22.706351] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   22.706440] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.706449] pnp: PnP ACPI init
[   22.706458] ACPI: bus type pnp registered
[   22.711666] pnp: PnP ACPI: found 16 devices
[   22.711669] ACPI: ACPI bus type pnp unregistered
[   22.711724] PCI: Using ACPI for IRQ routing
[   22.711726] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.711732] PCI: Cannot allocate resource region 9 of bridge 0000:00:02.0
[   22.711838] PCI: Cannot allocate resource region 1 of device 0000:02:00.0
[   22.711976] NET: Registered protocol family 8
[   22.711978] NET: Registered protocol family 20
[   22.712033] agpgart: Detected AGP bridge 0
[   22.716661] agpgart: AGP aperture is 128M @ 0xd0000000
[   22.716699] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   22.716703] hpet0: 3 32-bit timers, 14318180 Hz
[   22.717764] pnp: 00:06: ioport range 0xc00-0xc0f has been reserved
[   22.717767] pnp: 00:06: ioport range 0xd00-0xd0f has been reserved
[   22.717769] pnp: 00:06: ioport range 0xa20-0xa2f has been reserved
[   22.717772] pnp: 00:06: ioport range 0xa30-0xa3f has been reserved
[   22.717781] pnp: 00:08: iomem range 0x1c000000-0x1fffffff could not be reserved
[   22.717784] pnp: 00:08: iomem range 0x3c000000-0x3fffffff could not be reserved
[   22.717793] pnp: 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[   22.717796] pnp: 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
[   22.717802] pnp: 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[   22.717807] pnp: 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   22.717810] pnp: 00:0f: iomem range 0xc0000-0xcffff has been reserved
[   22.717813] pnp: 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[   22.717816] pnp: 00:0f: iomem range 0x100000-0x7fffffff could not be reserved
[   22.718111] PCI: Bridge: 0000:00:01.0
[   22.718112]   IO window: disabled.
[   22.718116]   MEM window: disabled.
[   22.718119]   PREFETCH window: disabled.
[   22.718127] PCI: Bridge: 0000:00:02.0
[   22.718128]   IO window: disabled.
[   22.718133]   MEM window: f9000000-fbcfffff
[   22.718137]   PREFETCH window: 90000000-9fffffff
[   22.718142] PCI: Bridge: 0000:00:03.0
[   22.718145]   IO window: d000-dfff
[   22.718150]   MEM window: fbd00000-fbdfffff
[   22.718154]   PREFETCH window: disabled.
[   22.718158] PCI: Bridge: 0000:00:13.0
[   22.718159]   IO window: disabled.
[   22.718164]   MEM window: fbe00000-fbefffff
[   22.718166]   PREFETCH window: disabled.
[   22.718171] PCI: Bridge: 0000:00:13.1
[   22.718173]   IO window: e000-efff
[   22.718178]   MEM window: fbf00000-fbffffff
[   22.718181]   PREFETCH window: disabled.
[   22.718197] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   22.718214] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 27
[   22.718219] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   22.718232] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 31
[   22.718237] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   22.718248] PCI: Setting latency timer of device 0000:00:13.0 to 64
[   22.718258] PCI: Setting latency timer of device 0000:00:13.1 to 64
[   22.718309] NET: Registered protocol family 2
[   22.718965] Time: hpet clocksource has been installed.
[   22.762805] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   22.763473] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   22.766270] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   22.766771] TCP: Hash tables configured (established 262144 bind 65536)
[   22.766774] TCP reno registered
[   22.778844] checking if image is initramfs... it is
[   23.322505] Freeing initrd memory: 7205k freed
[   23.326783] audit: initializing netlink socket (disabled)
[   23.326798] audit(1200596598.940:1): initialized
[   23.328687] VFS: Disk quotas dquot_6.5.1
[   23.328738] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   23.328826] io scheduler noop registered
[   23.328828] io scheduler anticipatory registered
[   23.328830] io scheduler deadline registered
[   23.328917] io scheduler cfq registered (default)
[   23.328935] PCI: VIA PCI bridge detected. Disabling DAC.
[   23.329411] Boot video device is 0000:02:00.0
[   23.330648] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   23.330691] assign_interrupt_mode Found MSI capability
[   23.330694] Allocate Port Service[0000:00:02.0:pcie00]
[   23.330730] Allocate Port Service[0000:00:02.0:pcie02]
[   23.330808] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   23.330848] assign_interrupt_mode Found MSI capability
[   23.330850] Allocate Port Service[0000:00:03.0:pcie00]
[   23.330875] Allocate Port Service[0000:00:03.0:pcie02]
[   23.354737] Real Time Clock Driver v1.12ac
[   23.354980] hpet_acpi_add: no address or irqs in _CRS
[   23.355006] Linux agpgart interface v0.102 (c) Dave Jones
[   23.355008] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.355102] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.355742] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.356383] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.356589] input: Macintosh mouse button emulation as /class/input/input0
[   23.356656] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   23.356658] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   23.357255] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.357261] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.357397] mice: PS/2 mouse device common for all mice
[   23.357512] TCP cubic registered
[   23.357563] NET: Registered protocol family 1
[   23.357793] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   23.357800] Freeing unused kernel memory: 296k freed
[   23.381988] input: AT Translated Set 2 keyboard as /class/input/input1
[   24.539401] AppArmor: AppArmor initialized<5>audit(1200596600.156:2):  type=1505 info="AppArmor initialized" pid=1275
[   24.545361] fuse init (API version 7.8)
[   24.552183] Failure registering capabilities with primary security module.
[   24.592452] ACPI: Processor [P001] (supports 16 throttling states)
[   25.174774] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.174781] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.177514] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   25.177540] VP_IDE: chipset revision 7
[   25.177542] VP_IDE: not 100% native mode: will probe irqs later
[   25.177554] VP_IDE: VIA vt8237a (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   25.177562]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[   25.177572]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
[   25.177580] Probing IDE interface ide0...
[   25.188864] SCSI subsystem initialized
[   25.315554] libata version 2.21 loaded.
[   25.315669] usbcore: registered new interface driver usbfs
[   25.315694] usbcore: registered new interface driver hub
[   25.315720] usbcore: registered new device driver usb
[   25.316625] USB Universal Host Controller Interface driver v3.0
[   25.325769] 8139too Fast Ethernet driver 0.9.28
[   25.333161] Floppy drive(s): fd0 is 1.44M
[   25.335103] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   25.355644] FDC 0 is a post-1991 82077
[   26.058753] hda: PHILIPS DVDR1660P1, ATAPI CD/DVD-ROM drive
[   26.399207] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   26.401200] Probing IDE interface ide1...
[   26.969472] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 20
[   26.969486] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   26.969682] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   26.969710] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000bc00
[   26.969841] usb usb1: configuration #1 chosen from 1 choice
[   26.969867] hub 1-0:1.0: USB hub found
[   26.969874] hub 1-0:1.0: 2 ports detected
[   27.077304] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 22
[   27.077315] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   27.077339] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   27.077362] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000b880
[   27.077450] usb usb2: configuration #1 chosen from 1 choice
[   27.077475] hub 2-0:1.0: USB hub found
[   27.077480] hub 2-0:1.0: 2 ports detected
[   27.185138] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 21
[   27.185147] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   27.185169] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   27.185192] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000b800
[   27.185278] usb usb3: configuration #1 chosen from 1 choice
[   27.185301] hub 3-0:1.0: USB hub found
[   27.185306] hub 3-0:1.0: 2 ports detected
[   27.293000] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 23
[   27.293009] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   27.293030] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   27.293052] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000b480
[   27.293145] usb usb4: configuration #1 chosen from 1 choice
[   27.293169] hub 4-0:1.0: USB hub found
[   27.293175] hub 4-0:1.0: 2 ports detected
[   27.316878] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   27.400975] ahci 0000:03:00.0: version 2.2
[   27.401001] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 28 (level, low) -> IRQ 28
[   27.401211] PCI: Disallowing DAC for device 0000:03:00.0
[   27.491313] usb 1-1: configuration #1 chosen from 1 choice
[   27.864316] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   28.043396] usb 2-1: configuration #1 chosen from 1 choice
[   28.407504] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   28.407510] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   28.407516] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   28.407739] scsi0 : ahci
[   28.407799] scsi1 : ahci
[   28.407859] ata1: SATA max UDMA/133 cmd 0xffffc2000032c100 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 28
[   28.407864] ata2: SATA max UDMA/133 cmd 0xffffc2000032c180 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 28
[   28.543441] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   28.723215] ata1: SATA link down (SStatus 0 SControl 300)
[   28.779423] usb 3-2: configuration #1 chosen from 1 choice
[   29.034814] ata2: SATA link down (SStatus 0 SControl 300)
[   29.034889] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 20 (level, low) -> IRQ 20
[   29.035664] eth0: RealTek RTL8139 at 0xffffc20000330800, 00:1b:fc:1b:29:df, IRQ 20
[   29.035668] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   29.035775] ACPI: PCI Interrupt 0000:05:07.0[B] -> GSI 18 (level, low) -> IRQ 18
[   29.035942] ohci_hcd 0000:05:07.0: OHCI Host Controller
[   29.036012] ohci_hcd 0000:05:07.0: new USB bus registered, assigned bus number 5
[   29.036031] ohci_hcd 0000:05:07.0: irq 18, io mem 0xfbfff000
[   29.037759] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   29.038707] usbcore: registered new interface driver hiddev
[   29.051414] input: PS/2+USB Mouse as /class/input/input2
[   29.051436] input: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:10.0-1
[   29.051456] usbcore: registered new interface driver usbhid
[   29.051460] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   29.052965] usbcore: registered new interface driver libusual
[   29.057063] Initializing USB Mass Storage driver...
[   29.057135] scsi2 : SCSI emulation for USB Mass Storage devices
[   29.057190] usb-storage: device found at 2
[   29.057192] usb-storage: waiting for device to settle before scanning
[   29.057207] usbcore: registered new interface driver usb-storage
[   29.057209] USB Mass Storage support registered.
[   29.096720] usb usb5: configuration #1 chosen from 1 choice
[   29.096750] hub 5-0:1.0: USB hub found
[   29.096760] hub 5-0:1.0: 2 ports detected
[   29.202562] ACPI: PCI Interrupt 0000:05:07.1[C] -> GSI 19 (level, low) -> IRQ 19
[   29.202729] ohci_hcd 0000:05:07.1: OHCI Host Controller
[   29.202797] ohci_hcd 0000:05:07.1: new USB bus registered, assigned bus number 6
[   29.202816] ohci_hcd 0000:05:07.1: irq 19, io mem 0xfbffe000
[   29.264490] usb usb6: configuration #1 chosen from 1 choice
[   29.264519] hub 6-0:1.0: USB hub found
[   29.264535] hub 6-0:1.0: 2 ports detected
[   29.370345] ACPI: PCI Interrupt 0000:05:07.2[D] -> GSI 16 (level, low) -> IRQ 16
[   29.370509] ohci_hcd 0000:05:07.2: OHCI Host Controller
[   29.370572] ohci_hcd 0000:05:07.2: new USB bus registered, assigned bus number 7
[   29.370590] ohci_hcd 0000:05:07.2: irq 16, io mem 0xfbffd000
[   29.432254] usb usb7: configuration #1 chosen from 1 choice
[   29.432278] hub 7-0:1.0: USB hub found
[   29.432286] hub 7-0:1.0: 2 ports detected
[   29.539342] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
[   29.539531] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   29.539589] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 8
[   29.539632] ehci_hcd 0000:00:10.4: irq 21, io mem 0xf8fffc00
[   29.539640] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.539745] usb usb8: configuration #1 chosen from 1 choice
[   29.539774] hub 8-0:1.0: USB hub found
[   29.539780] hub 8-0:1.0: 8 ports detected
[   29.558178] usb 3-2: USB disconnect, address 2
[   29.646185] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
[   29.646200] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 29 (level, low) -> IRQ 29
[   29.646246] PCI: Setting latency timer of device 0000:03:00.1 to 64
[   29.646295] scsi3 : pata_jmicron
[   29.646339] scsi4 : pata_jmicron
[   29.646363] ata3: PATA max UDMA/100 cmd 0x000000000001dc00 ctl 0x000000000001d882 bmdma 0x000000000001d400 irq 29
[   29.646367] ata4: PATA max UDMA/100 cmd 0x000000000001d800 ctl 0x000000000001d482 bmdma 0x000000000001d408 irq 29
[   29.655299] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   29.655307] Uniform CD-ROM driver Revision: 3.20
[   29.689995] usb 1-1: USB disconnect, address 2
[   29.972763] sata_via 0000:00:0f.0: version 2.2
[   29.972914] ACPI: PCI Interrupt 0000:05:07.3[A] -> GSI 17 (level, low) -> IRQ 17
[   29.972786] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 21
[   29.972928] sata_via 0000:00:0f.0: routed to hard irq line 10
[   29.973091] ehci_hcd 0000:05:07.3: EHCI Host Controller
[   29.973001] scsi5 : sata_via
[   29.973186] ehci_hcd 0000:05:07.3: new USB bus registered, assigned bus number 9
[   29.973081] scsi6 : sata_via
[   29.973235] ehci_hcd 0000:05:07.3: debug port 1
[   29.973343] ata5: SATA max UDMA/133 cmd 0x000000000001cc00 ctl 0x000000000001c882 bmdma 0x000000000001c400 irq 21
[   29.973348] ata6: SATA max UDMA/133 cmd 0x000000000001c800 ctl 0x000000000001c482 bmdma 0x000000000001c408 irq 21
[   29.997575] ehci_hcd 0000:05:07.3: irq 17, io mem 0xfbffcc00
[   30.013572] ehci_hcd 0000:05:07.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   30.013680] usb usb9: configuration #1 chosen from 1 choice
[   30.013712] hub 9-0:1.0: USB hub found
[   30.013718] hub 9-0:1.0: 6 ports detected
[   30.177338] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   30.365666] ata5.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[   30.365670] ata5.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   30.385637] ata5.00: configured for UDMA/133
[   30.508909] usb 8-6: new high speed USB device using ehci_hcd and address 4
[   30.592800] ata6: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   30.603456] scsi 5:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[   30.609058] sd 5:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   30.609071] sd 5:0:0:0: [sda] Write Protect is off
[   30.609073] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.609086] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.609133] sd 5:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   30.609141] sd 5:0:0:0: [sda] Write Protect is off
[   30.609143] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.609154] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.609158]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 >
[   30.672593] sd 5:0:0:0: [sda] Attached SCSI disk
[   30.675975] sd 5:0:0:0: Attached scsi generic sg0 type 0
[   30.913883] Attempting manual resume
[   30.913888] swsusp: Resume From Partition 8:9
[   30.913889] PM: Checking swsusp image.
[   30.914450] PM: Resume from disk failed.
[   30.951805] kjournald starting.  Commit interval 5 seconds
[   30.951816] EXT3-fs: mounted filesystem with ordered data mode.
[   31.408022] hub 8-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   31.527612] usb 8-6: new high speed USB device using ehci_hcd and address 5
[   32.418747] hub 8-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   32.538294] usb 8-6: new high speed USB device using ehci_hcd and address 6
[   32.945767] usb 8-6: device not accepting address 6, error -71
[   33.061621] usb 8-6: new high speed USB device using ehci_hcd and address 7
[   33.469094] usb 8-6: device not accepting address 7, error -71
[   33.469132] usb 2-1: USB disconnect, address 2
[   33.708786] usb 2-1: new full speed USB device using uhci_hcd and address 3
[   33.886995] usb 2-1: configuration #1 chosen from 1 choice
[   34.132254] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   34.307675] usb 1-1: configuration #1 chosen from 1 choice
[   34.323749] input: PS/2+USB Mouse as /class/input/input3
[   34.323766] input: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:10.0-1
[   35.121379] ip_tables: (C) 2000-2006 Netfilter Core Team
[   35.252956] Netfilter messages via NETLINK v0.30.
[   35.264544] nf_conntrack version 0.5.0 (8192 buckets, 65536 max)
[   37.073342] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.076363] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.460165] input: PC Speaker as /class/input/input4
[   37.525284] parport_pc 00:05: reported by Plug and Play ACPI
[   37.525331] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   37.673607] nvidia: module license 'NVIDIA' taints kernel.
[   37.927629] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 24 (level, low) -> IRQ 24
[   37.927639] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   37.927808] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   38.121413] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 17 (level, low) -> IRQ 17
[   38.121608] PCI: Setting latency timer of device 0000:04:01.0 to 64
[   38.330882] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   39.140971] lp0: using parport0 (interrupt-driven).
[   39.177633] usbcore: registered new interface driver usbserial
[   39.177648] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   39.177674] usbcore: registered new interface driver usbserial_generic
[   39.177677] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   39.179360] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
[   39.179375] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5
[   39.179386] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0
[   39.179413] usbcore: registered new interface driver visor
[   39.179416] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
[   39.218164] Adding 4980108k swap on /dev/sda9.  Priority:-1 extents:1 across:4980108k
[   39.517980] EXT3 FS on sda1, internal journal
[   40.982630] kjournald starting.  Commit interval 5 seconds
[   40.983221] EXT3 FS on sda5, internal journal
[   40.983228] EXT3-fs: mounted filesystem with ordered data mode.
[   41.057968] kjournald starting.  Commit interval 5 seconds
[   41.058885] EXT3 FS on sda6, internal journal
[   41.058889] EXT3-fs: mounted filesystem with ordered data mode.
[   41.112048] kjournald starting.  Commit interval 5 seconds
[   41.112736] EXT3 FS on sda8, internal journal
[   41.112740] EXT3-fs: mounted filesystem with ordered data mode.
[   41.132177] kjournald starting.  Commit interval 5 seconds
[   41.132754] EXT3 FS on sda7, internal journal
[   41.132757] EXT3-fs: mounted filesystem with ordered data mode.
[   43.135398] No dock devices found.
[   43.223339] input: Power Button (FF) as /class/input/input5
[   43.223600] ACPI: Power Button (FF) [PWRF]
[   43.224802] input: Power Button (CM) as /class/input/input6
[   43.225058] ACPI: Power Button (CM) [PWRB]
[   43.473950] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ processors (version 2.00.00)
[   43.474773] powernow-k8:    0 : fid 0xd (2100 MHz), vid 0xa
[   43.474778] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xb
[   43.474781] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xd
[   43.474783] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   44.288479] NET: Registered protocol family 10
[   44.288578] lo: Disabled Privacy Extensions
[   44.523102] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   44.527408] ppdev: user-space parallel port driver
[   44.663304] audit(1200596620.676:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5515 profile="/usr/sbin/cupsd"
[   44.843874] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   44.917872] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   44.928359] NFSD: starting 90-second grace period
[   45.950072] Bluetooth: Core ver 2.11
[   45.950175] NET: Registered protocol family 31
[   45.950177] Bluetooth: HCI device and connection manager initialized
[   45.950180] Bluetooth: HCI socket layer initialized
[   45.968027] Bluetooth: L2CAP ver 2.8
[   45.968031] Bluetooth: L2CAP socket layer initialized
[   46.002160] Bluetooth: RFCOMM socket layer initialized
[   46.002234] Bluetooth: RFCOMM TTY layer initialized
[   46.002237] Bluetooth: RFCOMM ver 1.8
[   46.029357] usb 8-6: new high speed USB device using ehci_hcd and address 8
[   46.464982] usb 8-6: new high speed USB device using ehci_hcd and address 9
[   46.881690] hub 8-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   46.934853] usb 8-6: new high speed USB device using ehci_hcd and address 10
[   47.265865] usb 8-6: new high speed USB device using ehci_hcd and address 12
[   47.686370] hub 8-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   47.739527] usb 8-6: new high speed USB device using ehci_hcd and address 13
[   47.882218] usb 8-6: new high speed USB device using ehci_hcd and address 14
[   48.012578] Failure registering capabilities with primary security module.
[   48.178948] NET: Registered protocol family 17
[   48.345622] hub 8-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   48.489044] usb 8-6: new high speed USB device using ehci_hcd and address 16
[   48.903856] hub 8-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   48.957007] usb 8-6: new high speed USB device using ehci_hcd and address 17
[   49.394373] usb 8-6: new high speed USB device using ehci_hcd and address 18
[   49.537042] usb 8-6: new high speed USB device using ehci_hcd and address 19
[   50.157374] usb 8-6: new high speed USB device using ehci_hcd and address 21
[   50.494085] usb 8-6: new high speed USB device using ehci_hcd and address 22
[   50.825858] hda-intel: Invalid position buffer, using LPIB read method instead.
[   51.297182] hub 8-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   51.408729] usb 8-6: new high speed USB device using ehci_hcd and address 23
[   51.948420] usb 8-6: new high speed USB device using ehci_hcd and address 24
[   52.363247] hub 8-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   52.505798] usb 8-6: new high speed USB device using ehci_hcd and address 26
[   52.920593] hub 8-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   52.973771] usb 8-6: new high speed USB device using ehci_hcd and address 27
[   53.388569] hub 8-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   53.441737] usb 8-6: new high speed USB device using ehci_hcd and address 28
[   53.635769] usb 8-6: device not accepting address 28, error -71
[   53.689041] usb 8-6: new high speed USB device using ehci_hcd and address 29
[   53.883069] usb 8-6: device not accepting address 29, error -71
[   54.263527] eth0: no IPv6 routers present
[   56.504140] compiz.real[6399]: segfault at 00000000000008a0 rip 00002b513e8368c9 rsp 00007fff6de0e428 error 4
[  187.927321] end_request: I/O error, dev fd0, sector 0
[  193.719531] end_request: I/O error, dev fd0, sector 0
[  199.512354] end_request: I/O error, dev fd0, sector 0
[  205.302747] end_request: I/O error, dev fd0, sector 0
[  211.093291] end_request: I/O error, dev fd0, sector 0
[  211.093298] Buffer I/O error on device fd0, logical block 0
[  216.908700] end_request: I/O error, dev fd0, sector 0
[  216.908706] Buffer I/O error on device fd0, logical block 0
[  222.731611] end_request: I/O error, dev fd0, sector 0
[  222.731618] Buffer I/O error on device fd0, logical block 0
[  228.549026] end_request: I/O error, dev fd0, sector 0
[  228.549033] Buffer I/O error on device fd0, logical block 0
[  234.358945] end_request: I/O error, dev fd0, sector 0
[  234.358951] Buffer I/O error on device fd0, logical block 0
[  240.168366] end_request: I/O error, dev fd0, sector 0
[  240.168373] Buffer I/O error on device fd0, logical block 0
[  245.970391] end_request: I/O error, dev fd0, sector 0
[  245.970398] Buffer I/O error on device fd0, logical block 0
[  251.766667] end_request: I/O error, dev fd0, sector 0
[  251.766674] Buffer I/O error on device fd0, logical block 0
[  257.562980] end_request: I/O error, dev fd0, sector 0
[  257.562987] Buffer I/O error on device fd0, logical block 0
[  263.359317] end_request: I/O error, dev fd0, sector 0
[  263.359323] Buffer I/O error on device fd0, logical block 0
[  269.151692] end_request: I/O error, dev fd0, sector 0
[  269.151699] Buffer I/O error on device fd0, logical block 0
[  274.944229] end_request: I/O error, dev fd0, sector 0
[  274.944236] Buffer I/O error on device fd0, logical block 0
[  280.735001] end_request: I/O error, dev fd0, sector 0
[  280.735008] Buffer I/O error on device fd0, logical block 0
[  286.525482] end_request: I/O error, dev fd0, sector 0
[  286.525489] Buffer I/O error on device fd0, logical block 0
[  292.316245] end_request: I/O error, dev fd0, sector 0
[  292.316252] Buffer I/O error on device fd0, logical block 0
[  298.139151] end_request: I/O error, dev fd0, sector 0
[  298.139158] Buffer I/O error on device fd0, logical block 0
[  303.962076] end_request: I/O error, dev fd0, sector 0
[  309.775570] end_request: I/O error, dev fd0, sector 0
[  316.883630] end_request: I/O error, dev fd0, sector 0
[  326.527338] end_request: I/O error, dev fd0, sector 0
[  326.527345] Buffer I/O error on device fd0, logical block 0
[  332.327336] end_request: I/O error, dev fd0, sector 0
[  332.327342] Buffer I/O error on device fd0, logical block 0
[  607.215037] usb 8-6: new high speed USB device using ehci_hcd and address 30
[  607.629831] hub 8-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[  607.683006] usb 8-6: new high speed USB device using ehci_hcd and address 31
[  607.825678] usb 8-6: new high speed USB device using ehci_hcd and address 32
[  608.240506] hub 8-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[  608.293646] usb 8-6: new high speed USB device using ehci_hcd and address 33
[  608.708486] hub 8-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[  608.761614] usb 8-6: new high speed USB device using ehci_hcd and address 34
[  608.955649] usb 8-6: device not accepting address 34, error -71
[  609.008915] usb 8-6: new high speed USB device using ehci_hcd and address 35
[  609.202948] usb 8-6: device not accepting address 35, error -71
```

---

### Post by theophile on 2008-01-17
dmesg reveals some significant USB controller errors. What did you replace? Did you replace the USB controller or just the connectors from the case to the motherboard? What do you mean by card reader?

---

### Post by Prodromoi on 2008-01-17
The only physical item to be replaced was the card reader.

The one that came out was this:
[http://www.silverstonetek.com/products/p_contents.php?pno=fp34](http://www.silverstonetek.com/products/p_contents.php?pno=fp34)

The one that replaced it is similar but simpler:
A 3.5" internal reader with a single USB2 socket, and CF, SD, SM and MS slots.
Similar, but not identical to this:
[http://cgi.ebay.co.uk/3-5-USB-Internal-Memory-Card-Reader-For-Camera-CF-MS_W0QQitemZ140198710205QQihZ004QQcategoryZ51082QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.co.uk/3-5-USB-Internal-Memory-Card-Reader-For-Camera-CF-MS_W0QQitemZ140198710205QQihZ004QQcategoryZ51082QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

The motherboard, an ASUS M2V-MX has its own USB (USB2) controller for the two motherboard connections and the four rear-panel USB2 sockets.

I also have a PCI USB card to provide four extra rear-panel USB2 sockets - although none are currently being used for anything (I used to use more USB devices on this machine than I currently do.)

The new card reader is plugged into the same connector that the old one was.  The (now free) second motherboard USB connector is connected to a pair of front panel USB ports - which work fine.

---

### Post by theophile on 2008-01-17
So when you replaced the reader, USB devices plugged into the rear USB ports stopped working where they worked previously?

Have you tried with a LiveCD to see if it's a kernel error?

---

### Post by Prodromoi on 2008-01-17
> **theophile said:**
> So when you replaced the reader, USB devices plugged into the rear USB ports stopped working where they worked previously?

Have you tried with a LiveCD to see if it's a kernel error?

No, the USB scanner works and the USB mouse works - both plugged into the rear-panel sockets.

The front panel USB sockets connected to one of the motherboard USB connectors are working.

The card reader, which works on other machines, which is plugged into the other motherboard socket (and this socket was working the other card reader) is not working.

I get the same "cannot enable port 6" message when booting from the Live CD.

---

### Post by theophile on 2008-01-21
Sounds like those IRQ errors that aren't supposed to happen with USB. Make sure you have the card reader's cable attached to the header properly. If so, try attaching it to one of the headers for the working ports and see if that makes a difference.

---

