---
title: "Hardware errors after upgrade to Gutsy"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by jimmiet on 2007-11-07
Ok.  I've been working in Feisty on and off for a few months.  Like many of the users I read about here, I would eventually like to do a complete migrate from M$.  As I learn how things work, I can see it will probably become a reality sometime in the Spring.

However, I must still consider myself a relative noob.  I just upgraded my duel-boot Presario C500 to Gutsy and I have some new symptoms that have appeared that I can't figure out.  I'm not even sure if they make a difference to my performance or anything. (I told you I was a noob)

When I make the selection to load Gutsy from the boot-loader, the first thing that quickly pops up is this series of error messages.  

[  7.995818] PCI: Cannot allocate resource region 7 of bridge 000:00:1c.0
[  7.995882] PCI: Cannot allocate resource region 8 of bridge 000:00:1c.0
[  7.995943] PCI: Cannot allocate resource region 7 of bridge 000:00:1c.2
[  7.996005] PCI: Cannot allocate resource region 8 of bridge 000:00:1c.2
[  7.996101] PCI: Cannot allocate resource region 0 of bridge 000:00:1c.0

The machine sits with this message against a black screen for a few seconds and them proceeds to boot normally.

They look like some sort of hardware error messages... but they didn't happen when I was using Feisty.

Does anyone know what these errors mean and, I guess most importantly, does anyone know how to fix them?

Jimmiet

---

### Post by ROBarber on 2007-11-07
Do you have an ATI video card?

for more information you shoult type on a command terminal

sudo lspci -v 

and

dmesg an post them here.

good luck

---

### Post by jimmiet on 2007-11-08
[SIZE="3"][COLOR="DarkRed"]OK... here is what I got from the first command:[/COLOR][/SIZE]

jim@jim-laptop:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Power Management version 2

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, fast devsel, latency 0
        Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Hewlett-Packard Company Unknown device 30a5
        Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Memory behind bridge: 30000000-300fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Hewlett-Packard Company Unknown device 30a5
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at d0544000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=08, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0100000-d01fffff
        Capabilities: [50] Subsystem: Hewlett-Packard Company Unknown device 30a5

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01) (prog-if 01 [AHCI 1.0])
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 18b0 [size=8]
        I/O ports at 18a4 [size=4]
        I/O ports at 18a8 [size=8]
        I/O ports at 18a0 [size=4]
        I/O ports at 1890 [size=16]
        Memory at d0544400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [70] Power Management version 2

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: medium devsel, IRQ 10
        I/O ports at 18c0 [size=32]

06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 1363
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at 30000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 2
        Capabilities: [58] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Express Legacy Endpoint IRQ 0

08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at 2000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

jim@jim-laptop:~$ 


[SIZE="3"][COLOR="DarkRed"]And this is the pile of gobbletegook that resulted from the second:[/COLOR][/SIZE]

jim@jim-laptop:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f680000 (usable)
[    0.000000]  BIOS-e820: 000000001f680000 - 000000001f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f65c0
[    0.000000] Entering add_active_range(0, 0, 128640) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128640
[    0.000000]   HighMem    128640 ->   128640
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128640
[    0.000000] On node 0 totalpages: 128640
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123571 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6510 checksum 0
[    0.000000] ACPI: RSDP 000F6510, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 1F68CC21, 004C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP 1F693C86, 0074 (r1 HP     NISSAN    6040000 LOHR       5A)
[    0.000000] ACPI: DSDT 1F68D54D, 6739 (r1 HP     NISSAN    6040000 INTL 20060608)
[    0.000000] ACPI: FACS 1F694FC0, 0040
[    0.000000] ACPI: APIC 1F693CFA, 0068 (r1 HP     NISSAN    6040000 LOHR       5A)
[    0.000000] ACPI: HPET 1F693D62, 0038 (r1 HP     NISSAN    6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 1F693D9A, 003C (r1 HP     NISSAN    6040000 LOHR       5A)
[    0.000000] ACPI: BOOT 1F693FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC 1F693E08, 0176 (r1 HPQOEM SLIC-MPC  6040000 LOHR        0)
[    0.000000] ACPI: APIC 1F693F7E, 005A (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: SSDT 1F68D33F, 020A (r1 SataRe SataAhci     1000 INTL 20060217)
[    0.000000] ACPI: SSDT 1F68D163, 01DC (r1  PmRef  Cpu0Cst     3001 INTL 20060217)
[    0.000000] ACPI: SSDT 1F68CC6D, 04F6 (r1  PmRef    CpuPm     3000 INTL 20060217)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
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
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] Built 1 zonelists.  Total pages: 127635
[    0.000000] Kernel command line: root=UUID=7db77f3a-dc96-4c78-b85d-68f7696b9a5a ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1596.138 MHz processor.
[    7.814773] Console: colour VGA+ 80x25
[    7.814944] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.815114] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    7.825803] Memory: 498316k/514560k available (2015k kernel code, 15652k reserved, 916k data, 364k init, 0k highmem)
[    7.825812] virtual kernel memory layout:
[    7.825813]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    7.825814]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.825816]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[    7.825817]     lowmem  : 0xc0000000 - 0xdf680000   ( 502 MB)
[    7.825818]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    7.825819]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[    7.825820]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[    7.825823] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.825857] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    7.826008] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    7.826014] hpet0: 3 64-bit timers, 14318180 Hz
[    7.906957] Calibrating delay using timer specific routine.. 3195.69 BogoMIPS (lpj=6391390)
[    7.906978] Security Framework v1.0.0 initialized
[    7.906983] SELinux:  Disabled at boot.
[    7.906995] Mount-cache hash table entries: 512
[    7.907110] CPU: After generic identify, caps: afebfbff 20100000 00000000 00000000 0000e31d 00000000 00000001
[    7.907118] monitor/mwait feature present.
[    7.907119] using mwait in idle threads.
[    7.907124] CPU: L1 I cache: 32K, L1 D cache: 32K
[    7.907126] CPU: L2 cache: 1024K
[    7.907129] CPU: After all inits, caps: afebfbff 20100000 00000000 00003940 0000e31d 00000000 00000001
[    7.907137] Compat vDSO mapped to ffffe000.
[    7.907149] Checking 'hlt' instruction... OK.
[    7.923047] SMP alternatives: switching to UP code
[    7.923225] Freeing SMP alternatives: 11k freed
[    7.923484] Early unpacking initramfs... done
[    8.280001] ACPI: Core revision 20070126
[    8.280057] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    8.314588] CPU0: Intel(R) Celeron(R) M CPU        520  @ 1.60GHz stepping 06
[    8.314615] Total of 1 processors activated (3195.69 BogoMIPS).
[    8.314811] ENABLING IO-APIC IRQs
[    8.315012] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    8.462465] Brought up 1 CPUs
[    8.462569] Booting paravirtualized kernel on bare hardware
[    8.462657] Time:  0:23:25  Date: 10/08/107
[    8.462675] NET: Registered protocol family 16
[    8.462752] EISA bus registered
[    8.462757] ACPI: bus type pci registered
[    8.462877] PCI: PCI BIOS revision 2.10 entry at 0xfd873, last bus=8
[    8.462879] PCI: Using configuration type 1
[    8.462881] Setting up standard PCI resources
[    8.464843] ACPI: EC: Look up EC in DSDT
[    8.465429] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[    8.466622] ACPI: System BIOS is requesting _OSI(Linux)
[    8.466625] ACPI: Please test with "acpi_osi=!Linux"
[    8.466626] Please send dmidecode to [email]linux-acpi@vger.kernel.org[/email]
[    8.467074] ACPI: Interpreter enabled
[    8.467078] ACPI: (supports S0 S3 S4 S5)
[    8.467095] ACPI: Using IOAPIC for interrupt routing
[    8.511490] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[    8.511538] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.511553] PCI: Probing PCI hardware (bus 00)
[    8.512267] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    8.512272] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    8.513130] PCI: Transparent bridge - 0000:00:1e.0
[    8.513196] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.513492] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    8.513612] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    8.513741] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    8.516118] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    8.516212] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[    8.516301] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    8.516390] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    8.516480] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    8.516570] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    8.516660] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    8.516749] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    8.516855] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.516865] pnp: PnP ACPI init
[    8.516872] ACPI: bus type pnp registered
[    8.538925] pnp: PnP ACPI: found 10 devices
[    8.538927] ACPI: ACPI bus type pnp unregistered
[    8.538932] PnPBIOS: Disabled by ACPI PNP
[    8.538976] PCI: Using ACPI for IRQ routing
[    8.538979] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.538984] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[    8.539048] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[    8.539109] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[    8.539170] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[    8.539267] PCI: Cannot allocate resource region 0 of device 0000:06:00.0
[    8.558343] NET: Registered protocol family 8
[    8.558345] NET: Registered protocol family 20
[    8.558401] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    8.558405] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[    8.558408] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[    8.558411] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    8.558419] pnp: 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[    8.562336] Time: tsc clocksource has been installed.
[    8.562351] Switched to high resolution mode on CPU 0
[    8.588689] PCI: Bridge: 0000:00:1c.0
[    8.588690]   IO window: disabled.
[    8.588696]   MEM window: disabled.
[    8.588701]   PREFETCH window: disabled.
[    8.588720] PCI: Bridge: 0000:00:1c.2
[    8.588721]   IO window: disabled.
[    8.588728]   MEM window: 30000000-300fffff
[    8.588732]   PREFETCH window: disabled.
[    8.588738] PCI: Bridge: 0000:00:1e.0
[    8.588742]   IO window: 2000-2fff
[    8.588748]   MEM window: d0100000-d01fffff
[    8.588753]   PREFETCH window: disabled.
[    8.588784] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[    8.588793] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    8.588817] PCI: Enabling device 0000:00:1c.2 (0100 -> 0102)
[    8.588822] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 17
[    8.588830] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    8.588845] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.588855] NET: Registered protocol family 2
[    8.626277] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    8.626317] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[    8.626425] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    8.626493] TCP: Hash tables configured (established 16384 bind 16384)
[    8.626496] TCP reno registered
[    8.638350] checking if image is initramfs... it is
[    9.335139] Freeing initrd memory: 7341k freed
[    9.335282] Simple Boot Flag at 0x36 set to 0x1
[    9.335623] audit: initializing netlink socket (disabled)
[    9.335638] audit(1194481405.100:1): initialized
[    9.337390] VFS: Disk quotas dquot_6.5.1
[    9.337435] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.337522] io scheduler noop registered
[    9.337525] io scheduler anticipatory registered
[    9.337527] io scheduler deadline registered
[    9.337541] io scheduler cfq registered (default)
[    9.337558] Boot video device is 0000:00:02.0
[   17.330330] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   17.330421] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   17.330483] assign_interrupt_mode Found MSI capability
[   17.330485] Allocate Port Service[0000:00:1c.0:pcie00]
[   17.330519] Allocate Port Service[0000:00:1c.0:pcie02]
[   17.330620] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   17.330681] assign_interrupt_mode Found MSI capability
[   17.330683] Allocate Port Service[0000:00:1c.2:pcie00]
[   17.330714] Allocate Port Service[0000:00:1c.2:pcie02]
[   17.330866] isapnp: Scanning for PnP cards...
[   17.684871] isapnp: No Plug & Play device found
[   17.705462] Real Time Clock Driver v1.12ac
[   17.705677] hpet_resources: 0xfed00000 is busy
[   17.705703] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.706851] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.707044] input: Macintosh mouse button emulation as /class/input/input0
[   17.707118] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   17.730151] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.730157] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.730315] mice: PS/2 mouse device common for all mice
[   17.731399] EISA: Probing bus 0 at eisa.0
[   17.731407] Cannot allocate resource for EISA slot 1
[   17.731410] Cannot allocate resource for EISA slot 2
[   17.731436] EISA: Detected 0 cards.
[   17.731527] TCP cubic registered
[   17.731541] NET: Registered protocol family 1
[   17.731564] Using IPI No-Shortcut mode
[   17.731708]   Magic number: 15:449:354
[   17.731997] Freeing unused kernel memory: 364k freed
[   17.765997] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.919498] AppArmor: AppArmor initialized<5>audit(1194481414.600:2):  type=1505 info="AppArmor initialized" pid=1203
[   18.927056] fuse init (API version 7.8)
[   18.931086] Failure registering capabilities with primary security module.
[   18.945664] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   18.945670] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.945681] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   18.957550] ACPI: Thermal Zone [TZ01] (53 C)
[   18.957670] ACPI: Thermal Zone [TZ02] (27 C)
[   19.399380] usbcore: registered new interface driver usbfs
[   19.399403] usbcore: registered new interface driver hub
[   19.399422] usbcore: registered new device driver usb
[   19.400165] USB Universal Host Controller Interface driver v3.0
[   19.400229] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[   19.400240] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   19.400245] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   19.400393] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   19.400426] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00001820
[   19.400549] usb usb1: configuration #1 chosen from 1 choice
[   19.400573] hub 1-0:1.0: USB hub found
[   19.400578] hub 1-0:1.0: 2 ports detected
[   19.476734] SCSI subsystem initialized
[   19.481672] libata version 2.21 loaded.
[   19.504487] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   19.504499] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   19.504503] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   19.504526] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   19.504562] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[   19.504656] usb usb2: configuration #1 chosen from 1 choice
[   19.504678] hub 2-0:1.0: USB hub found
[   19.504683] hub 2-0:1.0: 2 ports detected
[   19.579350] 8139too Fast Ethernet driver 0.9.28
[   19.608396] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 17
[   19.608409] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   19.608414] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   19.608436] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   19.608472] uhci_hcd 0000:00:1d.2: irq 17, io base 0x00001860
[   19.608566] usb usb3: configuration #1 chosen from 1 choice
[   19.608590] hub 3-0:1.0: USB hub found
[   19.608596] hub 3-0:1.0: 2 ports detected
[   11.664000] Marking TSC unstable due to: possible TSC halt in C2.
[   11.668000] Time: hpet clocksource has been installed.
[   11.760000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[   11.760000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   11.760000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   11.760000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   11.760000] ehci_hcd 0000:00:1d.7: debug port 1
[   11.760000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   11.760000] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xd0544000
[   11.792000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   11.792000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   11.792000] usb usb4: configuration #1 chosen from 1 choice
[   11.792000] hub 4-0:1.0: USB hub found
[   11.792000] hub 4-0:1.0: 6 ports detected
[   11.896000] ata_piix 0000:00:1f.1: version 2.11
[   11.896000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 19
[   11.896000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   11.896000] scsi0 : ata_piix
[   11.896000] scsi1 : ata_piix
[   11.896000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[   11.896000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[   12.000000] Clocksource tsc unstable (delta = -253822272 ns)
[   12.216000] ata1.00: ATAPI: Optiarc CD-RW CRX880A, KH17, max MWDMA2
[   12.356000] usb 4-1: new high speed USB device using ehci_hcd and address 2
[   12.388000] ata1.00: configured for MWDMA2
[   12.388000] ata2: port disabled. ignoring.
[   12.388000] scsi 0:0:0:0: CD-ROM            Optiarc  CD-RW CRX880A    KH17 PQ: 0 ANSI: 5
[   12.388000] ahci 0000:00:1f.2: version 2.2
[   12.388000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   12.400000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   12.400000] Uniform CD-ROM driver Revision: 3.20
[   12.400000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   12.404000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   12.488000] usb 4-1: configuration #1 chosen from 1 choice
[   12.856000] usbcore: registered new interface driver libusual
[   12.860000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   12.860000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   12.864000] Initializing USB Mass Storage driver...
[   13.096000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   13.268000] usb 2-2: configuration #1 chosen from 1 choice
[   13.392000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0xf impl SATA mode
[   13.392000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[   13.392000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   13.392000] scsi2 : ahci
[   13.392000] scsi3 : ahci
[   13.392000] scsi4 : ahci
[   13.392000] scsi5 : ahci
[   13.392000] ata3: SATA max UDMA/133 cmd 0xe0048500 ctl 0x00000000 bmdma 0x00000000 irq 19
[   13.392000] ata4: SATA max UDMA/133 cmd 0xe0048580 ctl 0x00000000 bmdma 0x00000000 irq 19
[   13.392000] ata5: SATA max UDMA/133 cmd 0xe0048600 ctl 0x00000000 bmdma 0x00000000 irq 19
[   13.392000] ata6: SATA max UDMA/133 cmd 0xe0048680 ctl 0x00000000 bmdma 0x00000000 irq 19
[   13.512000] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   13.664000] usb 3-2: configuration #1 chosen from 1 choice
[   13.668000] scsi6 : SCSI emulation for USB Mass Storage devices
[   13.668000] usb-storage: device found at 2
[   13.668000] usb-storage: waiting for device to settle before scanning
[   13.668000] usbcore: registered new interface driver usb-storage
[   13.668000] USB Mass Storage support registered.
[   13.668000] usbcore: registered new interface driver hiddev
[   13.680000] input: HID 062a:0000 as /class/input/input2
[   13.680000] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:1d.2-2
[   13.680000] usbcore: registered new interface driver usbhid
[   13.680000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   13.876000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   13.876000] ata3.00: ATA-7: Hitachi HTS541680J9SA00, SB2OC7BP, max UDMA/100
[   13.876000] ata3.00: 156301488 sectors, multi 16: LBA48 
[   13.876000] ata3.00: configured for UDMA/100
[   14.188000] ata4: SATA link down (SStatus 0 SControl 0)
[   14.500000] ata5: SATA link down (SStatus 0 SControl 0)
[   14.812000] ata6: SATA link down (SStatus 0 SControl 0)
[   14.812000] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54168 SB2O PQ: 0 ANSI: 5
[   14.812000] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   14.812000] PCI: Enabling device 0000:08:08.0 (0105 -> 0107)
[   14.812000] ACPI: PCI Interrupt 0000:08:08.0[A] -> GSI 16 (level, low) -> IRQ 20
[   14.812000] eth0: RealTek RTL8139 at 0xe004a000, 00:16:d4:e6:93:e6, IRQ 20
[   14.812000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   14.816000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   14.824000] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   14.824000] sd 2:0:0:0: [sda] Write Protect is off
[   14.824000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.824000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.824000] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   14.824000] sd 2:0:0:0: [sda] Write Protect is off
[   14.824000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.824000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.824000]  sda: sda1 sda2 sda3 sda4 < sda5 >
[   15.248000] sd 2:0:0:0: [sda] Attached SCSI disk
[   15.552000] Attempting manual resume
[   15.552000] swsusp: Resume From Partition 8:5
[   15.552000] PM: Checking swsusp image.
[   15.552000] PM: Resume from disk failed.
[   15.596000] kjournald starting.  Commit interval 5 seconds
[   15.596000] EXT3-fs: mounted filesystem with ordered data mode.
[   18.668000] usb-storage: device scan complete
[   18.668000] scsi 6:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  2.15 PQ: 0 ANSI: 2
[   18.672000] sd 6:0:0:0: [sdb] 990865 512-byte hardware sectors (507 MB)
[   18.676000] sd 6:0:0:0: [sdb] Write Protect is off
[   18.676000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   18.676000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   18.688000] sd 6:0:0:0: [sdb] 990865 512-byte hardware sectors (507 MB)
[   18.688000] sd 6:0:0:0: [sdb] Write Protect is off
[   18.688000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   18.688000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   18.688000]  sdb: sdb1
[   18.692000] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   18.692000] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   22.012000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.032000] Netfilter messages via NETLINK v0.30.
[   22.048000] nf_conntrack version 0.5.0 (4020 buckets, 32160 max)
[   23.696000] Linux agpgart interface v0.102 (c) Dave Jones
[   23.796000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.872000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.884000] agpgart: Detected an Intel 945GM Chipset.
[   23.884000] agpgart: Detected 7932K stolen memory.
[   23.900000] agpgart: AGP aperture is 256M @ 0xc0000000
[   24.192000] intel_rng: FWH not detected
[   24.244000] iTCO_vendor_support: vendor-support=0
[   24.244000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   24.244000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   24.244000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   25.044000] input: Wacom Graphire as /class/input/input3
[   25.052000] usbcore: registered new interface driver wacom
[   25.052000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/tablet/wacom_sys.c: v1.46:USB Wacom Graphire and Wacom Intuos tablet driver
[   25.332000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   25.332000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   25.384000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   25.452000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   25.848000] lp: driver loaded but no devices found
[   25.884000] ndiswrapper version 1.45 loaded (smp=yes)
[   25.992000] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[   25.992000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 17
[   25.992000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   26.000000] ndiswrapper: using IRQ 17
[   26.396000] wlan0: ethernet device 00:1a:73:39:d5:e1 using NDIS driver: bcmwl5, version: 0x4281300, NDIS version: 0x501, vendor: '', 14E4:4311.5.conf
[   26.396000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   26.396000] usbcore: registered new interface driver ndiswrapper
[   26.436000] Adding 1485972k swap on /dev/sda5.  Priority:-1 extents:1 across:1485972k
[   26.496000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   27.024000] EXT3 FS on sda3, internal journal
[   28.984000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   29.004000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   29.020000] ACPI: AC Adapter [ACAD] (on-line)
[   29.032000] No dock devices found.
[   29.100000] ACPI: Battery Slot [BAT1] (battery present)
[   29.220000] input: Power Button (FF) as /class/input/input5
[   29.224000] ACPI: Power Button (FF) [PWRF]
[   29.224000] ACPI Error (evxfevnt-0186): Could not enable SleepButton event [20070126]
[   29.224000] ACPI Warning (evxface-0145): Could not enable fixed event 3 [20070126]
[   29.256000] input: Lid Switch as /class/input/input6
[   29.260000] ACPI: Lid Switch [LID]
[   29.296000] input: Power Button (CM) as /class/input/input7
[   29.296000] ACPI: Power Button (CM) [PWRB]
[   30.544000] ppdev: user-space parallel port driver
[   30.616000] eth0: link down
[   30.912000] audit(1194499435.105:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5068 profile="/usr/sbin/cupsd"
[   31.108000] apm: BIOS not found.
[   31.356000] Failure registering capabilities with primary security module.
[   31.516000] Bluetooth: Core ver 2.11
[   31.516000] NET: Registered protocol family 31
[   31.516000] Bluetooth: HCI device and connection manager initialized
[   31.516000] Bluetooth: HCI socket layer initialized
[   31.524000] Bluetooth: L2CAP ver 2.8
[   31.524000] Bluetooth: L2CAP socket layer initialized
[   31.604000] Bluetooth: RFCOMM socket layer initialized
[   31.604000] Bluetooth: RFCOMM TTY layer initialized
[   31.604000] Bluetooth: RFCOMM ver 1.8
[   35.148000] [drm] Initialized drm 1.1.0 20060810
[   35.152000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 20
[   35.156000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   65.544000] NET: Registered protocol family 17
[   80.152000] NET: Registered protocol family 10
[   80.152000] lo: Disabled Privacy Extensions
[   80.152000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   90.400000] eth1: no IPv6 routers present
[SIZE="3"][COLOR="DarkRed"]
It looks like every bit of info on my laptop is in there someplace... but, damned if I know what any of it means.  Can someone help?

Jimmiet[/COLOR][/SIZE]

---

