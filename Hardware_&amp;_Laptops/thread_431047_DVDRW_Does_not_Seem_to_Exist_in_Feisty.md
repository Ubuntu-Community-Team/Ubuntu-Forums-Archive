---
title: "DVDRW Does not Seem to Exist in Feisty"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by USSJoin on 2007-05-02
Hello! I have a Clevo M570U (essentially an alienware Area51 without the alien head on it; it's a laptop) that works nearly perfectly.

However, I am unable to mount the DVDRW (that works perfectly on WIndows). I looked for why it wouldn't mount /dev/cdrom-- only to find it didn't exist. I looked through the entire dev list, and there's nothing there that would indicate a CDROM of any sort; the only one that might be it is /dev/sg0.

There's no record of a problem in the dmesg; it doesn't seem to mention it at all.

The specific DVD I'm testing is the Feisty installer; the laptop can boot off it fine.

Thanks for any help you might have.

The Dmesg output from bootup:

[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007fd80000 end: 000000007fe80000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007fe80000 size: 000000000000b000 end: 000000007fe8b000 type: 3
[    0.000000] copy_e820_map() start: 000000007fe8b000 size: 0000000000075000 end: 000000007ff00000 type: 4
[    0.000000] copy_e820_map() start: 000000007ff00000 size: 0000000000100000 end: 0000000080000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed00000 size: 0000000000000400 end: 00000000fed00400 type: 2
[    0.000000] copy_e820_map() start: 00000000fed14000 size: 0000000000006000 end: 00000000fed1a000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed1c000 size: 0000000000074000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff000000 size: 0000000001000000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe80000 (usable)
[    0.000000]  BIOS-e820: 000000007fe80000 - 000000007fe8b000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fe8b000 - 000000007ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7760
[    0.000000] Entering add_active_range(0, 0, 523904) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   523904
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   523904
[    0.000000] On node 0 totalpages: 523904
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292227 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f76b0
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x7fe85724
[    0.000000] ACPI: FADT (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x7fe8ae20
[    0.000000] ACPI: MADT (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x7fe8ae94
[    0.000000] ACPI: HPET (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x7fe8aefc
[    0.000000] ACPI: MCFG (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x7fe8af34
[    0.000000] ACPI: MADT (v001 PTLTD  	 APIC   0x06040000  LTP 0x00000000) @ 0x7fe8af70
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x7fe8afd8
[    0.000000] ACPI: SSDT (v001 SataRe  SataPri 0x00001000 INTL 0x20050624) @ 0x7fe867d2
[    0.000000] ACPI: SSDT (v001 SataRe  SataSec 0x00001000 INTL 0x20050624) @ 0x7fe86136
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x7fe8576c
[    0.000000] ACPI: DSDT (v001 INTEL  CALISTGA 0x06040000 INTL 0x20050624) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: 2 duplicate APIC table ignored.
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
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
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Detected 2161.433 MHz processor.
[   30.726531] Built 1 zonelists.  Total pages: 519811
[   30.726536] Kernel command line: root=UUID=182cefee-8371-441f-84ab-350a3913bfb6 ro quiet splash
[   30.726794] mapped APIC to ffffd000 (fee00000)
[   30.726798] mapped IOAPIC to ffffc000 (fec00000)
[   30.726803] Enabling fast FPU save and restore... done.
[   30.726807] Enabling unmasked SIMD FPU exception support... done.
[   30.726817] Initializing CPU#0
[   30.726899] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   30.729560] Console: colour VGA+ 80x25
[   30.729838] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   30.730368] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   30.887769] Memory: 2066532k/2095616k available (1992k kernel code, 27704k reserved, 893k data, 328k init, 1178112k highmem)
[   30.887785] virtual kernel memory layout:
[   30.887787]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   30.887789]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   30.887792]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   30.887794]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   30.887796]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   30.887798]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   30.887801]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   30.887807] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   30.888027] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   30.888036] hpet0: 3 64-bit timers, 14318180 Hz
[   30.889042] Using HPET for base-timer
[   30.967897] Calibrating delay using timer specific routine.. 4328.12 BogoMIPS (lpj=8656257)
[   30.967959] Security Framework v1.0.0 initialized
[   30.967969] SELinux:  Disabled at boot.
[   30.967993] Mount-cache hash table entries: 512
[   30.968180] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[   30.968194] monitor/mwait feature present.
[   30.968197] using mwait in idle threads.
[   30.968203] CPU: L1 I cache: 32K, L1 D cache: 32K
[   30.968207] CPU: L2 cache: 2048K
[   30.968211] CPU: Physical Processor ID: 0
[   30.968214] CPU: Processor Core ID: 0
[   30.968218] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
[   30.968232] Compat vDSO mapped to ffffe000.
[   30.968238] Remapping vsyscall page to ffffe000
[   30.968256] Checking 'hlt' instruction... OK.
[   30.984032] SMP alternatives: switching to UP code
[   30.984577] Early unpacking initramfs... done
[   31.538605] ACPI: Core revision 20060707
[   31.538916] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   31.545026] CPU0: Intel Genuine Intel(R) CPU           T2600  @ 2.16GHz stepping 08
[   31.545054] SMP alternatives: switching to SMP code
[   31.545195] Booting processor 1/1 eip 3000
[   31.555780] Initializing CPU#1
[   31.710641] Calibrating delay using timer specific routine.. 12677.07 BogoMIPS (lpj=25354141)
[   31.710651] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[   31.710660] monitor/mwait feature present.
[   31.710665] CPU: L1 I cache: 32K, L1 D cache: 32K
[   31.710669] CPU: L2 cache: 2048K
[   31.710672] CPU: Physical Processor ID: 0
[   31.710675] CPU: Processor Core ID: 1
[   31.710678] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
[   31.711400] CPU1: Intel Genuine Intel(R) CPU           T2600  @ 2.16GHz stepping 08
[   31.711435] Total of 2 processors activated (17005.19 BogoMIPS).
[   31.711637] ENABLING IO-APIC IRQs
[   31.711869] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   31.858391] checking TSC synchronization across 2 CPUs: passed.
[    0.003997] Brought up 2 CPUs
[    0.120500] migration_cost=59
[    0.120902] Booting paravirtualized kernel on bare hardware
[    0.121027] Time: 17:45:03  Date: 03/24/107
[    0.121069] NET: Registered protocol family 16
[    0.121193] EISA bus registered
[    0.121200] ACPI: bus type pci registered
[    0.121356] PCI: BIOS BUG #81[49435000] found
[    0.121419] PCI: Using configuration type 1
[    0.121422] Setting up standard PCI resources
[    0.126581] ACPI: Interpreter enabled
[    0.126586] ACPI: Using IOAPIC for interrupt routing
[    0.127794] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.127802] PCI: Probing PCI hardware (bus 00)
[    0.129812] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.129819] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.130098] Boot video device is 0000:01:00.0
[    0.131406] PCI: Transparent bridge - 0000:00:1e.0
[    0.131504] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#07) (try 'pci=assign-busses')
[    0.131509] Please report the result to linux-kernel to fix this permanently
[    0.131602] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.135892] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.136693] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.137112] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.137525] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.137935] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.138920] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.139300] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.139670] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.140056] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.140422] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.140790] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.141158] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.141529] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.144356] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.144375] pnp: PnP ACPI init
[    0.148513] pnp: PnP ACPI: found 13 devices
[    0.148520] PnPBIOS: Disabled by ACPI PNP
[    0.148583] PCI: Using ACPI for IRQ routing
[    0.148588] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.148768] NET: Registered protocol family 8
[    0.148771] NET: Registered protocol family 20
[    0.149200] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
[    0.149205] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
[    0.149670] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0
[    0.149735] PCI: Bridge: 0000:00:01.0
[    0.149739]   IO window: 2000-2fff
[    0.149745]   MEM window: d8000000-d9ffffff
[    0.149750]   PREFETCH window: c0000000-cfffffff
[    0.149756] PCI: Bridge: 0000:00:1c.0
[    0.149761]   IO window: 3000-3fff
[    0.149769]   MEM window: d4000000-d5ffffff
[    0.149775]   PREFETCH window: d0000000-d1ffffff
[    0.149783] PCI: Bridge: 0000:00:1c.1
[    0.149788]   IO window: 4000-4fff
[    0.149796]   MEM window: d6000000-d7ffffff
[    0.149803]   PREFETCH window: d2000000-d3ffffff
[    0.149811] PCI: Bridge: 0000:00:1c.2
[    0.149813]   IO window: disabled.
[    0.149820]   MEM window: disabled.
[    0.149826]   PREFETCH window: disabled.
[    0.149839] PCI: Bus 7, cardbus bridge: 0000:06:07.0
[    0.149843]   IO window: 00005400-000054ff
[    0.149850]   IO window: 00005800-000058ff
[    0.149857]   PREFETCH window: 88000000-8bffffff
[    0.149865]   MEM window: 90000000-93ffffff
[    0.149872] PCI: Bridge: 0000:00:1e.0
[    0.149877]   IO window: 5000-5fff
[    0.149885]   MEM window: da000000-da0fffff
[    0.149892]   PREFETCH window: 88000000-8dffffff
[    0.149914] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.149922] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.149952] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[    0.149961] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.149989] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[    0.149997] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.150027] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    0.150036] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.150053] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.150074] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.150120] NET: Registered protocol family 2
[    0.203718] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.203860] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.205052] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.205661] TCP: Hash tables configured (established 131072 bind 65536)
[    0.205666] TCP reno registered
[    0.219814] checking if image is initramfs... it is
[    1.318844] Freeing initrd memory: 6773k freed
[    1.319082] Simple Boot Flag at 0x36 set to 0x1
[    1.319778] audit: initializing netlink socket (disabled)
[    1.319798] audit(1177436703.296:1): initialized
[    1.319937] highmem bounce pool size: 64 pages
[    1.320066] VFS: Disk quotas dquot_6.5.1
[    1.320093] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.320160] io scheduler noop registered
[    1.320165] io scheduler anticipatory registered
[    1.320169] io scheduler deadline registered
[    1.320187] io scheduler cfq registered (default)
[    1.320553] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    1.320604] assign_interrupt_mode Found MSI capability
[    1.320609] Allocate Port Service[0000:00:01.0:pcie00]
[    1.320741] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    1.320809] assign_interrupt_mode Found MSI capability
[    1.320814] Allocate Port Service[0000:00:1c.0:pcie00]
[    1.320870] Allocate Port Service[0000:00:1c.0:pcie02]
[    1.321028] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    1.321095] assign_interrupt_mode Found MSI capability
[    1.321099] Allocate Port Service[0000:00:1c.1:pcie00]
[    1.321152] Allocate Port Service[0000:00:1c.1:pcie02]
[    1.321305] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    1.321373] assign_interrupt_mode Found MSI capability
[    1.321377] Allocate Port Service[0000:00:1c.2:pcie00]
[    1.321428] Allocate Port Service[0000:00:1c.2:pcie02]
[    1.321679] isapnp: Scanning for PnP cards...
[    2.352971] isapnp: No Plug & Play device found
[    2.390867] Real Time Clock Driver v1.12ac
[    2.390948] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    2.391120] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.391275] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 8250
[    2.392073] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.392430] mice: PS/2 mouse device common for all mice
[    2.393311] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    2.393536] input: Macintosh mouse button emulation as /class/input/input0
[    2.393592] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    2.393598] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    2.393953] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.397489] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.399341] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.399348] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.399352] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.399357] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.399361] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.399510] EISA: Probing bus 0 at eisa.0
[    2.399519] Cannot allocate resource for EISA slot 1
[    2.399524] Cannot allocate resource for EISA slot 2
[    2.399528] Cannot allocate resource for EISA slot 3
[    2.399532] Cannot allocate resource for EISA slot 4
[    2.399536] Cannot allocate resource for EISA slot 5
[    2.399556] EISA: Detected 0 cards.
[    2.422368] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.429650] TCP cubic registered
[    2.429664] NET: Registered protocol family 1
[    2.429699] Starting balanced_irq
[    2.429714] Using IPI No-Shortcut mode
[    2.429843] ACPI: (supports S0 S3 S4 S5)
[    2.429913]   Magic number: 3:829:795
[    2.430000]   hash matches device ptyr3
[    2.430216] Freeing unused kernel memory: 328k freed
[    2.431898] Time: tsc clocksource has been installed.
[    3.759455] Capability LSM initialized
[    3.820317] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    3.820645] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    3.821073] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    3.821081] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.821885] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    3.822185] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    3.822671] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    3.822679] ACPI: Processor [CPU1] (supports 8 throttling states)
[    4.628000] Time: hpet clocksource has been installed.
[    4.840000] ACPI: Invalid passive threshold
[    5.060000] ACPI: Thermal Zone [THM0] (37 C)
[    5.732000] SCSI subsystem initialized
[    5.740000] libata version 2.20 loaded.
[    5.744000] ata_piix 0000:00:1f.2: version 2.10ac1
[    5.744000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    5.800000] usbcore: registered new interface driver usbfs
[    5.800000] usbcore: registered new interface driver hub
[    5.800000] usbcore: registered new device driver usb
[    5.804000] USB Universal Host Controller Interface driver v3.0
[    5.828000] ieee1394: Initialized config rom entry `ip1394'
[    5.900000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[    5.900000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.904000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[    5.904000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
[    5.904000] scsi0 : ata_piix
[    6.076000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[    6.076000] ata1.00: ATA-7: ST910021AS, 3.04, max UDMA/133
[    6.076000] ata1.00: 195371568 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.088000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[    6.088000] ata1.00: configured for UDMA/133
[    6.088000] scsi1 : ata_piix
[    6.276000] ATA: abnormal status 0x7F on port 0x00010177
[    6.280000] scsi 0:0:0:0: Direct-Access     ATA      ST910021AS       3.04 PQ: 0 ANSI: 5
[    6.280000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[    6.280000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    6.280000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    6.280000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    6.280000] ehci_hcd 0000:00:1d.7: debug port 1
[    6.280000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    6.280000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xda304000
[    6.284000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.284000] usb usb1: configuration #1 chosen from 1 choice
[    6.284000] hub 1-0:1.0: USB hub found
[    6.284000] hub 1-0:1.0: 8 ports detected
[    6.392000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[    6.392000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    6.392000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    6.392000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    6.392000] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001800
[    6.392000] usb usb2: configuration #1 chosen from 1 choice
[    6.392000] hub 2-0:1.0: USB hub found
[    6.392000] hub 2-0:1.0: 2 ports detected
[    6.500000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    6.500000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    6.500000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    6.500000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    6.500000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
[    6.500000] usb usb3: configuration #1 chosen from 1 choice
[    6.500000] hub 3-0:1.0: USB hub found
[    6.500000] hub 3-0:1.0: 2 ports detected
[    6.608000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    6.608000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    6.608000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    6.608000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    6.608000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    6.608000] usb usb4: configuration #1 chosen from 1 choice
[    6.608000] hub 4-0:1.0: USB hub found
[    6.608000] hub 4-0:1.0: 2 ports detected
[    6.636000] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    6.716000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    6.716000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    6.716000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    6.716000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    6.716000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    6.716000] usb usb5: configuration #1 chosen from 1 choice
[    6.716000] hub 5-0:1.0: USB hub found
[    6.716000] hub 5-0:1.0: 2 ports detected
[    6.788000] usb 1-6: configuration #1 chosen from 1 choice
[    6.824000] r8169 Gigabit Ethernet driver 2.2LK loaded
[    6.824000] ACPI: PCI Interrupt 0000:06:0b.0[A] -> GSI 17 (level, low) -> IRQ 17
[    6.824000] eth0: RTL8169sb/8110sb at 0xf8856400, 00:90:f5:4f:f9:00, IRQ 17
[    6.828000] ACPI: PCI Interrupt 0000:06:07.1[B] -> GSI 17 (level, low) -> IRQ 17
[    6.972000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[da006800-da006fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.984000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[    6.984000] sda: Write Protect is off
[    6.984000] sda: Mode Sense: 00 3a 00 00
[    6.984000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.984000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[    6.984000] sda: Write Protect is off
[    6.984000] sda: Mode Sense: 00 3a 00 00
[    6.984000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.984000]  sda: sda1 sda2 sda3
[    7.080000] sd 0:0:0:0: Attached scsi disk sda
[    7.084000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.436000] Attempting manual resume
[    7.436000] swsusp: Resume From Partition 8:2
[    7.436000] PM: Checking swsusp image.
[    7.436000] PM: Resume from disk failed.
[    7.472000] kjournald starting.  Commit interval 5 seconds
[    7.472000] EXT3-fs: mounted filesystem with ordered data mode.
[    8.252000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[08003856004ff900]
[   18.832000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.832000] agpgart: Detected an Intel 945GM Chipset.
[   18.852000] agpgart: AGP aperture is 256M @ 0x0
[   19.008000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.008000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.616000] intel_rng: FWH not detected
[   19.648000] Linux video capture interface: v2.00
[   19.708000] ACPI: PCI Interrupt 0000:06:07.2[C] -> GSI 18 (level, low) -> IRQ 18
[   19.916000] saa7130/34: v4l2 driver version 0.2.14 loaded
[   19.916000] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 18 (level, low) -> IRQ 18
[   19.916000] saa7133[0]: found at 0000:06:04.0, rev: 208, irq: 18, latency: 181, mmio: 0xda006000
[   19.916000] saa7133[0]: subsystem: 5168:3307, board: UNKNOWN/GENERIC [card=0,autodetected]
[   19.916000] saa7133[0]: board init: gpio is 10000
[   19.968000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[   19.972000] iTCO_vendor_support: vendor-support=0
[   20.016000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   20.016000] iTCO_wdt: Found a ICH7-M DH TCO device (Version=2, TCOBASE=0x1060)
[   20.016000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.060000] saa7133[0]: i2c eeprom 00: 68 51 07 33 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   20.060000] saa7133[0]: i2c eeprom 10: 00 00 62 08 ff 20 ff ff ff ff ff ff ff ff ff ff
[   20.060000] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 01 03 08 ff 01 17 ff ff ff ff
[   20.060000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.060000] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 05 01 01 16 22 15 ff ff ff ff
[   20.060000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.060000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.060000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   20.064000] saa7133[0]: registered device video0 [v4l2]
[   20.064000] saa7133[0]: registered device vbi0
[   20.080000] nvidia: module license 'NVIDIA' taints kernel.
[   20.816000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.816000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   20.816000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   20.832000] ieee80211_crypt: registered algorithm 'NULL'
[   20.892000] sdhci: Secure Digital Host Controller Interface driver
[   20.892000] sdhci: Copyright(c) Pierre Ossman
[   20.892000] sdhci: SDHCI controller found at 0000:06:07.3 [104c:803c] (rev 0)
[   20.892000] ACPI: PCI Interrupt 0000:06:07.3[D] -> GSI 19 (level, low) -> IRQ 19
[   20.892000] mmc0: SDHCI at 0xda007000 irq 19 PIO
[   20.904000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   20.904000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   21.028000] Yenta: CardBus bridge found at 0000:06:07.0 [1558:0571]
[   21.028000] Yenta: Enabling burst memory read transactions
[   21.028000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   21.028000] Yenta: Routing CardBus interrupts to PCI
[   21.028000] Yenta TI: socket 0000:06:07.0, mfunc 0x01aa1b22, devctl 0x64
[   21.052000] irda_init()
[   21.052000] NET: Registered protocol family 23
[   21.100000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   21.100000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   21.144000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   21.144000] nsc-ircc, chip->init
[   21.144000] nsc-ircc, Found chip at base=0x02e
[   21.144000] nsc-ircc, driver loaded (Dag Brattli)
[   21.144000] nsc_ircc_open(), can't get iobase of 0x2f8
[   21.144000] nsc-ircc, Found chip at base=0x02e
[   21.144000] nsc-ircc, driver loaded (Dag Brattli)
[   21.144000] nsc_ircc_open(), can't get iobase of 0x2f8
[   21.144000] nsc-ircc, chip->init
[   21.144000] nsc-ircc, Found chip at base=0x02e
[   21.144000] nsc-ircc, driver loaded (Dag Brattli)
[   21.144000] pnp: Device 00:0a disabled.
[   21.228000] saa7134 ALSA driver for DMA sound loaded
[   21.228000] saa7133[0]/alsa: saa7133[0] at 0xda006000 irq 18 registered as card -2
[   21.264000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   21.264000] Socket status: 30000006
[   21.264000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   21.264000] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   21.264000] cs: IO port probe 0x5000-0x5fff: clean.
[   21.264000] pcmcia: parent PCI bridge Memory window: 0xda000000 - 0xda0fffff
[   21.264000] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8dffffff
[   21.264000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.264000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   21.264000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   21.432000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   21.432000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   21.620000] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   21.684000] cs: IO port probe 0x100-0x3af: clean.
[   21.684000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   21.688000] cs: IO port probe 0x820-0x8ff: clean.
[   21.688000] cs: IO port probe 0xc00-0xcf7: clean.
[   21.688000] cs: IO port probe 0xa00-0xaff: clean.
[   22.184000] fuse init (API version 7.8)
[   22.252000] lp: driver loaded but no devices found
[   22.312000] Adding 2000084k swap on /dev/disk/by-uuid/d4935a6f-6d30-4e38-a426-bae5782dcaee.  Priority:-1 extents:1 across:2000084k
[   22.456000] EXT3 FS on sda3, internal journal
[   22.720000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   22.784000] NTFS volume version 3.1.
[   23.200000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   24.768000] NET: Registered protocol family 17
[   28.096000] ibm_acpi: ec object not found
[   28.144000] ACPI: Battery Slot [BAT0] (battery present)
[   28.144000] ACPI: Battery Slot [BAT1] (battery absent)
[   28.156000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   28.212000] No dock devices found.
[   28.220000] Using specific hotkey driver
[   28.488000] ACPI: AC Adapter [ADP0] (on-line)
[   28.508000] input: Lid Switch as /class/input/input3
[   28.508000] ACPI: Lid Switch [LID0]
[   28.508000] input: Power Button (CM) as /class/input/input4
[   28.508000] ACPI: Power Button (CM) [PWRB]
[   28.508000] input: Sleep Button (CM) as /class/input/input5
[   28.508000] ACPI: Sleep Button (CM) [SLPB]
[   28.680000] pcc_acpi: loading...
[   30.892000] ttyS1: LSR safety check engaged!
[   31.652000] r8169: eth0: link down
[   33.964000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 1:00.0] forgot to specify physical device; fix it!
[   33.964000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 1:00.0] forgot to specify physical device; fix it!
[   33.968000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 1:00.0] forgot to specify physical device; fix it!
[   35.356000] ppdev: user-space parallel port driver
[   36.072000] apm: BIOS not found.
[   36.268000] Bluetooth: Core ver 2.11
[   36.268000] NET: Registered protocol family 31
[   36.268000] Bluetooth: HCI device and connection manager initialized
[   36.268000] Bluetooth: HCI socket layer initialized
[   36.308000] Bluetooth: L2CAP ver 2.8
[   36.308000] Bluetooth: L2CAP socket layer initialized
[   36.464000] Bluetooth: RFCOMM socket layer initialized
[   36.464000] Bluetooth: RFCOMM TTY layer initialized
[   36.464000] Bluetooth: RFCOMM ver 1.8
[   43.928000] r8169: eth0: link up
[   50.744000] NET: Registered protocol family 10
[   50.744000] lo: Disabled Privacy Extensions
[   50.744000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   61.440000] eth0: no IPv6 routers present

---

