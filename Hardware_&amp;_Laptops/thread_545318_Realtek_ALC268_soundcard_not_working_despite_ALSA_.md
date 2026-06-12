---
title: "Realtek ALC268 soundcard not working despite ALSA 1.0.15rc1!"
date: 2007-09-07
forum: Hardware &amp; Laptops
---

### Post by Jeanpaul145 on 2007-09-07
I have a Zepto Znote 6625WD and have installed Gutsy tribe 5 on it (because of the gutsy kernel which provides me with wifi functionality), which has a Realtek ALC268 soundcard.

I have found that the ALSA driver to be used is snd-hda-intel  and so I've tried to install it using the [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
Also, I used ALSA 1.0.15rc1.

However, once I've done that, alsamixer crashes with the message: "alsamixer: function snd_ctl_open failed for default: No such device"

Also, this is the dmesg output:
```
[    0.000000] Linux version 2.6.22-10-generic (buildd@palmer) (gcc version 4.1.3 20070812 (prerelease) (Ubuntu 4.1.2-15ubuntu2)) #1 SMP Wed Aug 22 08:11:52 GMT 2007 (Ubuntu 2.6.22-10.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe70000 (usable)
[    0.000000]  BIOS-e820: 000000007fe70000 - 000000007fe80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fe80000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7540
[    0.000000] Entering add_active_range(0, 0, 523888) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   523888
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   523888
[    0.000000] On node 0 totalpages: 523888
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2300 pages used for memmap
[    0.000000]   HighMem zone: 292212 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000F7510, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 7FE770A7, 0094 (r1 PTLTD  	 XSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 7FE7ECDD, 00F4 (r3 INTEL  CRESTLNE  6040000 ALAN        1)
[    0.000000] ACPI: DSDT 7FE78E2E, 5E3B (r2 INTEL  CRESTLNE  6040000 INTL 20050624)
[    0.000000] ACPI: FACS 7FE7FFC0, 0040
[    0.000000] ACPI: APIC 7FE7EDD1, 0068 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 7FE7EE39, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 7FE7EE71, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA 7FE7EEAD, 0032 (r1 Intel   CRESTLN  6040000          5A52)
[    0.000000] ACPI: TMOR 7FE7EEDF, 0026 (r1 PTLTD            6040000 PTL         3)
[    0.000000] ACPI: ASF! 7FE7EF05, 006B (r32 OEMID  OEMTBL    6040000 PTL         1)
[    0.000000] ACPI: APIC 7FE7EF70, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 7FE7EFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 7FE787DF, 064F (r1 SataRe  SataPri     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FE78143, 069C (r1 SataRe  SataSec     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FE776C7, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FE77621, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 7FE7713B, 04E6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
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
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Built 1 zonelists.  Total pages: 519796
[    0.000000] Kernel command line: root=UUID=017f0582-9ccc-4818-8b4c-b91146f3b65a ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2194.661 MHz processor.
[   18.246627] Console: colour VGA+ 80x25
[   18.246916] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   18.247182] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.317771] Memory: 2066104k/2095552k available (2010k kernel code, 28152k reserved, 917k data, 364k init, 1178048k highmem)
[   18.317778] virtual kernel memory layout:
[   18.317779]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   18.317780]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.317780]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   18.317781]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   18.317782]       .init : 0xc03e1000 - 0xc043c000   ( 364 kB)
[   18.317783]       .data : 0xc02f69c6 - 0xc03dbe64   ( 917 kB)
[   18.317784]       .text : 0xc0100000 - 0xc02f69c6   (2010 kB)
[   18.317786] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.317816] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   18.317930] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   18.317933] hpet0: 3 64-bit timers, 14318180 Hz
[   18.398842] Calibrating delay using timer specific routine.. 4392.98 BogoMIPS (lpj=8785976)
[   18.398862] Security Framework v1.0.0 initialized
[   18.398867] SELinux:  Disabled at boot.
[   18.398877] Mount-cache hash table entries: 512
[   18.398980] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   18.398986] monitor/mwait feature present.
[   18.398987] using mwait in idle threads.
[   18.398991] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.398993] CPU: L2 cache: 4096K
[   18.398995] CPU: Physical Processor ID: 0
[   18.398996] CPU: Processor Core ID: 0
[   18.398998] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   18.399005] Compat vDSO mapped to ffffe000.
[   18.399015] Checking 'hlt' instruction... OK.
[   18.414908] SMP alternatives: switching to UP code
[   18.415248] Early unpacking initramfs... done
[   18.663760] ACPI: Core revision 20070126
[   18.663797] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   18.668844] CPU0: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0a
[   18.668857] SMP alternatives: switching to SMP code
[   18.668918] Booting processor 1/1 eip 3000
[   18.679301] Initializing CPU#1
[   18.758356] Calibrating delay using timer specific routine.. 4388.95 BogoMIPS (lpj=8777906)
[   18.758361] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   18.758365] monitor/mwait feature present.
[   18.758367] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.758369] CPU: L2 cache: 4096K
[   18.758370] CPU: Physical Processor ID: 0
[   18.758371] CPU: Processor Core ID: 1
[   18.758372] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   18.759027] CPU1: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0a
[   18.759046] Total of 2 processors activated (8781.94 BogoMIPS).
[   18.759201] ENABLING IO-APIC IRQs
[   18.759384] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.906231] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   18.926218] Brought up 2 CPUs
[   19.018073] migration_cost=32
[   19.018174] Booting paravirtualized kernel on bare hardware
[   19.018250] Time:  4:04:50  Date: 08/08/107
[   19.018265] NET: Registered protocol family 16
[   19.018329] EISA bus registered
[   19.018332] ACPI: bus type pci registered
[   19.018625] PCI: PCI BIOS revision 3.00 entry at 0xfddf1, last bus=7
[   19.018627] PCI: Using configuration type 1
[   19.018628] Setting up standard PCI resources
[   19.020570] ACPI: EC: Look up EC in DSDT
[   19.021065] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   19.022255] ACPI: System BIOS is requesting _OSI(Linux)
[   19.022257] ACPI: Please test with "acpi_osi=!Linux"
[   19.022257] Please send dmidecode to linux-acpi@vger.kernel.org
[   20.020692] ACPI: Interpreter enabled
[   20.020694] ACPI: (supports S0 S3 S4 S5)
[   20.020707] ACPI: Using IOAPIC for interrupt routing
[   20.029554] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   20.029596] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.029601] PCI: Probing PCI hardware (bus 00)
[   20.031628] PCI: Transparent bridge - 0000:00:1e.0
[   20.031683] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#07) (try 'pci=assign-busses')
[   20.031685] Please report the result to linux-kernel to fix this permanently
[   20.031764] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.031994] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[   20.032093] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   20.032188] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   20.032282] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   20.032376] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   20.032481] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   20.040975] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   20.041052] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   20.041128] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   20.041202] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   20.041277] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   20.041351] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[   20.041426] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   20.041500] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   20.041628] ACPI: Power Resource [FN00] (off)
[   20.041635] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.041642] pnp: PnP ACPI init
[   20.041648] ACPI: bus type pnp registered
[   20.045380] pnp: PnP ACPI: found 15 devices
[   20.045382] ACPI: ACPI bus type pnp unregistered
[   20.045385] PnPBIOS: Disabled by ACPI PNP
[   20.045419] PCI: Using ACPI for IRQ routing
[   20.045421] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.125478] NET: Registered protocol family 8
[   20.125480] NET: Registered protocol family 20
[   20.125515] pnp: 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   20.125518] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   20.125520] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   20.125523] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   20.125528] pnp: 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   20.128511] Time: tsc clocksource has been installed.
[   20.128518] Switched to high resolution mode on CPU 0
[   20.128589] Switched to high resolution mode on CPU 1
[   20.155725] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:01:00.0
[   20.155840] PCI: Bridge: 0000:00:01.0
[   20.155841]   IO window: 2000-2fff
[   20.155845]   MEM window: cc000000-ceffffff
[   20.155847]   PREFETCH window: d0000000-dfffffff
[   20.155850] PCI: Bridge: 0000:00:1c.0
[   20.155853]   IO window: 3000-3fff
[   20.155858]   MEM window: f0000000-f0ffffff
[   20.155861]   PREFETCH window: disabled.
[   20.155866] PCI: Bridge: 0000:00:1c.1
[   20.155868]   IO window: 4000-4fff
[   20.155873]   MEM window: f1000000-f1ffffff
[   20.155876]   PREFETCH window: disabled.
[   20.155881] PCI: Bridge: 0000:00:1c.2
[   20.155884]   IO window: 5000-5fff
[   20.155888]   MEM window: f2000000-f2ffffff
[   20.155892]   PREFETCH window: disabled.
[   20.155897] PCI: Bridge: 0000:00:1c.3
[   20.155899]   IO window: 6000-6fff
[   20.155904]   MEM window: f3000000-f3ffffff
[   20.155907]   PREFETCH window: disabled.
[   20.155914] PCI: Bus 7, cardbus bridge: 0000:06:06.0
[   20.155916]   IO window: 00007000-000070ff
[   20.155920]   IO window: 00007400-000074ff
[   20.155924]   PREFETCH window: 88000000-8bffffff
[   20.155929]   MEM window: 90000000-93ffffff
[   20.155933] PCI: Bridge: 0000:00:1e.0
[   20.155935]   IO window: 7000-7fff
[   20.155940]   MEM window: f4000000-f40fffff
[   20.155944]   PREFETCH window: 88000000-8bffffff
[   20.155957] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.155961] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   20.155981] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   20.155986] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.156005] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[   20.156009] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   20.156029] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   20.156034] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   20.156054] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   20.156059] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   20.156070] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   20.156083] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[   20.156093] NET: Registered protocol family 2
[   20.200347] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.200390] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   20.200895] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   20.201060] TCP: Hash tables configured (established 131072 bind 65536)
[   20.201062] TCP reno registered
[   20.216399] checking if image is initramfs... it is
[   20.705577] Freeing initrd memory: 7038k freed
[   20.705674] Simple Boot Flag at 0x36 set to 0x1
[   20.706024] audit: initializing netlink socket (disabled)
[   20.706036] audit(1189224291.116:1): initialized
[   20.706105] highmem bounce pool size: 64 pages
[   20.707455] VFS: Disk quotas dquot_6.5.1
[   20.707489] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.707557] io scheduler noop registered
[   20.707558] io scheduler anticipatory registered
[   20.707560] io scheduler deadline registered
[   20.707570] io scheduler cfq registered (default)
[   20.707693] Boot video device is 0000:01:00.0
[   20.707761] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   20.707793] assign_interrupt_mode Found MSI capability
[   20.707821] Allocate Port Service[0000:00:01.0:pcie00]
[   20.707845] Allocate Port Service[0000:00:01.0:pcie02]
[   20.707907] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   20.707956] assign_interrupt_mode Found MSI capability
[   20.707995] Allocate Port Service[0000:00:1c.0:pcie00]
[   20.708017] Allocate Port Service[0000:00:1c.0:pcie02]
[   20.708096] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   20.708146] assign_interrupt_mode Found MSI capability
[   20.708185] Allocate Port Service[0000:00:1c.1:pcie00]
[   20.708207] Allocate Port Service[0000:00:1c.1:pcie02]
[   20.708285] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   20.708335] assign_interrupt_mode Found MSI capability
[   20.708373] Allocate Port Service[0000:00:1c.2:pcie00]
[   20.708394] Allocate Port Service[0000:00:1c.2:pcie02]
[   20.708473] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   20.708522] assign_interrupt_mode Found MSI capability
[   20.708561] Allocate Port Service[0000:00:1c.3:pcie00]
[   20.708582] Allocate Port Service[0000:00:1c.3:pcie02]
[   20.708735] isapnp: Scanning for PnP cards...
[   21.062741] isapnp: No Plug & Play device found
[   21.077408] Real Time Clock Driver v1.12ac
[   21.077587] hpet_resources: 0xfed00000 is busy
[   21.077618] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.078518] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.078612] input: Macintosh mouse button emulation as /class/input/input0
[   21.078676] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   21.080841] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.080845] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.080963] mice: PS/2 mouse device common for all mice
[   21.081046] EISA: Probing bus 0 at eisa.0
[   21.081052] Cannot allocate resource for EISA slot 1
[   21.081055] Cannot allocate resource for EISA slot 2
[   21.081056] Cannot allocate resource for EISA slot 3
[   21.081058] Cannot allocate resource for EISA slot 4
[   21.081060] Cannot allocate resource for EISA slot 5
[   21.081061] Cannot allocate resource for EISA slot 6
[   21.081063] Cannot allocate resource for EISA slot 7
[   21.081068] EISA: Detected 0 cards.
[   21.081128] TCP cubic registered
[   21.081137] NET: Registered protocol family 1
[   21.081152] Using IPI No-Shortcut mode
[   21.081274]   Magic number: 7:552:59
[   21.081497] Freeing unused kernel memory: 364k freed
[   21.103204] input: AT Translated Set 2 keyboard as /class/input/input1
[   22.227198] AppArmor: AppArmor initialized
[   22.227203] audit(1189224292.616:2): AppArmor initialized
[   22.227204] 
[   22.232854] fuse init (API version 7.8)
[   22.236090] AppArmor: Registered secondary security module: capability.
[   22.236092] Capability LSM initialized as secondary
[   22.238571] ACPI: Transitioning device [FAN0] to D3
[   22.238573] ACPI: Transitioning device [FAN0] to D3
[   22.238575] ACPI: Fan [FAN0] (off)
[   22.241742] ACPI: SSDT 7FE77E85, 01F6 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   22.241907] ACPI: SSDT 7FE77926, 04DA (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   22.242326] Monitor-Mwait will be used to enter C-1 state
[   22.242329] Monitor-Mwait will be used to enter C-2 state
[   22.242332] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   22.242335] ACPI: Processor [CPU0] (supports 8 throttling states)
[   22.242507] ACPI: SSDT 7FE7807B, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   22.242660] ACPI: SSDT 7FE77E00, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   22.243099] ACPI: CPU1 (power states: C1[C1] C2[C2])
[   22.243102] ACPI: Processor [CPU1] (supports 8 throttling states)
[   22.243947] ACPI: Thermal Zone [TZ00] (56 C)
[    3.732000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.736000] Time: hpet clocksource has been installed.
[    3.744000] ACPI: Thermal Zone [TZ02] (57 C)
[    3.752000] ACPI: Thermal Zone [TZ01] (66 C)
[    4.148000] usbcore: registered new interface driver usbfs
[    4.148000] usbcore: registered new interface driver hub
[    4.148000] usbcore: registered new device driver usb
[    4.152000] USB Universal Host Controller Interface driver v3.0
[    4.152000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[    4.152000] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    4.152000] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.152000] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    4.152000] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    4.152000] usb usb1: configuration #1 chosen from 1 choice
[    4.152000] hub 1-0:1.0: USB hub found
[    4.152000] hub 1-0:1.0: 2 ports detected
[    4.212000] SCSI subsystem initialized
[    4.216000] libata version 2.21 loaded.
[    4.256000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
[    4.256000] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    4.256000] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.256000] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    4.256000] uhci_hcd 0000:00:1a.1: irq 20, io base 0x00001820
[    4.256000] usb usb2: configuration #1 chosen from 1 choice
[    4.256000] hub 2-0:1.0: USB hub found
[    4.256000] hub 2-0:1.0: 2 ports detected
[    4.360000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 21
[    4.360000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    4.360000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.360000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    4.360000] uhci_hcd 0000:00:1d.0: irq 21, io base 0x00001840
[    4.360000] usb usb3: configuration #1 chosen from 1 choice
[    4.360000] hub 3-0:1.0: USB hub found
[    4.360000] hub 3-0:1.0: 2 ports detected
[    4.464000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    4.464000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    4.464000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.464000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    4.464000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    4.464000] usb usb4: configuration #1 chosen from 1 choice
[    4.464000] hub 4-0:1.0: USB hub found
[    4.464000] hub 4-0:1.0: 2 ports detected
[    4.568000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    4.568000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    4.568000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.568000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    4.568000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    4.568000] usb usb5: configuration #1 chosen from 1 choice
[    4.568000] hub 5-0:1.0: USB hub found
[    4.568000] hub 5-0:1.0: 2 ports detected
[    4.672000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[    4.672000] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    4.672000] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.672000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    4.672000] ehci_hcd 0000:00:1a.7: debug port 1
[    4.672000] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[    4.672000] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf4304000
[    4.676000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.676000] usb usb6: configuration #1 chosen from 1 choice
[    4.676000] hub 6-0:1.0: USB hub found
[    4.676000] hub 6-0:1.0: 4 ports detected
[    4.780000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 21
[    4.780000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.780000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.780000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    4.780000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.780000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.780000] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xf4304400
[    4.784000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.784000] usb usb7: configuration #1 chosen from 1 choice
[    4.784000] hub 7-0:1.0: USB hub found
[    4.784000] hub 7-0:1.0: 6 ports detected
[    4.888000] ACPI: PCI Interrupt 0000:06:06.1[B] -> GSI 17 (level, low) -> IRQ 17
[    4.936000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f4006000-f40067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.936000] tg3.c:v3.77 (May 31, 2007)
[    4.936000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[    4.936000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[    4.964000] eth0: Tigon3 [partno(BCM95787m) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:a0:d1:c2:57:b4
[    4.964000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    4.964000] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    4.964000] ata_piix 0000:00:1f.1: version 2.11
[    4.964000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 19
[    4.964000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.964000] scsi0 : ata_piix
[    4.964000] scsi1 : ata_piix
[    4.964000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118a0 irq 14
[    4.964000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118a8 irq 15
[    5.048000] usb 6-4: new high speed USB device using ehci_hcd and address 2
[    5.196000] usb 6-4: configuration #1 chosen from 1 choice
[    5.320000] ata1.01: ATAPI: TSSTcorpCD/DVDW SN-S082D, SS03, max UDMA/33
[    5.516000] ata1.01: configured for UDMA/33
[    5.696000] scsi 0:0:1:0: CD-ROM            TSSTcorp CD/DVDW SN-S082D SS03 PQ: 0 ANSI: 5
[    5.696000] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    5.856000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[    5.856000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.856000] scsi2 : ata_piix
[    5.856000] scsi3 : ata_piix
[    5.856000] ata3: SATA max UDMA/133 cmd 0x000118f8 ctl 0x000118ce bmdma 0x000118e0 irq 19
[    5.856000] ata4: SATA max UDMA/133 cmd 0x000118f0 ctl 0x000118ca bmdma 0x000118e8 irq 19
[    6.020000] ata3.00: ATA-7: ST910021AS, 3.06, max UDMA/133
[    6.020000] ata3.00: 195371568 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.036000] ata3.00: configured for UDMA/133
[    6.072000] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    6.200000] scsi 2:0:0:0: Direct-Access     ATA      ST910021AS       3.06 PQ: 0 ANSI: 5
[    6.256000] usb 4-2: configuration #1 chosen from 1 choice
[    6.260000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.260000] Uniform CD-ROM driver Revision: 3.20
[    6.260000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    6.260000] sd 2:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[    6.260000] sd 2:0:0:0: [sda] Write Protect is off
[    6.260000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.260000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.260000] sd 2:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[    6.260000] sd 2:0:0:0: [sda] Write Protect is off
[    6.260000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.260000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.260000]  sda:<5>sr 0:0:1:0: Attached scsi generic sg0 type 5
[    6.260000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    6.280000] usbcore: registered new interface driver hiddev
[    6.292000] input: Logitech USB Receiver as /class/input/input2
[    6.292000] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2
[    6.328000] input: Logitech USB Receiver as /class/input/input3
[    6.328000] input,hiddev96: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2
[    6.328000] usbcore: registered new interface driver usbhid
[    6.328000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    6.340000]  sda1 sda2 < sda5 sda6 >
[    6.380000] sd 2:0:0:0: [sda] Attached SCSI disk
[    6.668000] Attempting manual resume
[    6.668000] swsusp: Resume From Partition 8:6
[    6.668000] PM: Checking swsusp image.
[    6.668000] PM: Resume from disk failed.
[    6.696000] kjournald starting.  Commit interval 5 seconds
[    6.696000] EXT3-fs: mounted filesystem with ordered data mode.
[   16.008000] PM: Writing back config space on device 0000:05:00.0 at offset 1 (was 40100506, writing 40100106)
[   16.680000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.684000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.812000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.288000] Yenta: CardBus bridge found at 0000:06:06.0 [1170:0040]
[   17.288000] Yenta: Enabling burst memory read transactions
[   17.288000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.288000] Yenta: Routing CardBus interrupts to PCI
[   17.288000] Yenta TI: socket 0000:06:06.0, mfunc 0x01aa1b22, devctl 0x64
[   17.328000] irda_init()
[   17.328000] NET: Registered protocol family 23
[   17.392000] tpm_inf_pnp 00:0a: Found TPM with ID IFX0102
[   17.392000] tpm_inf_pnp 00:0a: TPM found: config base 0x4e, data base 0x1670, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[   17.404000] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.0.0-1k
[   17.404000] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   17.444000] sdhci: Secure Digital Host Controller Interface driver
[   17.444000] sdhci: Copyright(c) Pierre Ossman
[   17.448000] NET: Registered protocol family 17
[   17.464000] usbcore: registered new interface driver xpad
[   17.464000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   17.524000] Yenta: ISA IRQ mask 0x0c78, PCI irq 18
[   17.524000] Socket status: 30000006
[   17.524000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   17.524000] pcmcia: parent PCI bridge I/O window: 0x7000 - 0x7fff
[   17.524000] cs: IO port probe 0x7000-0x7fff: clean.
[   17.524000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xf40fffff
[   17.524000] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[   17.524000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   17.524000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   17.524000] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   17.572000] ACPI: PCI Interrupt 0000:06:06.2[A] -> GSI 18 (level, low) -> IRQ 18
[   17.572000] sdhci: SDHCI controller found at 0000:06:06.3 [104c:803c] (rev 0)
[   17.572000] ACPI: PCI Interrupt 0000:06:06.3[A] -> GSI 18 (level, low) -> IRQ 18
[   17.572000] mmc0: SDHCI at 0xf4006800 irq 18 DMA
[   17.628000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   17.628000] tg3: eth0: Flow control is on for TX and on for RX.
[   17.812000] iwl4965: Channel 14 [2.4GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 183 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 184 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 185 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 187 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 188 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 189 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 192 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 196 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 7 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 8 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 11 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 12 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 16 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 34 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 38 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 42 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 46 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 145 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 149 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 153 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 157 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 161 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Channel 165 [5.2GHz] is Tx only -- skipping.
[   17.812000] iwl4965: Tunable channels: 13 802.11bg, 19 802.11a channels
[   17.812000] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   17.872000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   17.872000] snd_hda_intel: Unknown symbol snd_ctl_add
[   17.872000] snd_hda_intel: disagrees about version of symbol snd_card_register
[   17.872000] snd_hda_intel: Unknown symbol snd_card_register
[   17.872000] snd_hda_intel: disagrees about version of symbol snd_card_free
[   17.872000] snd_hda_intel: Unknown symbol snd_card_free
[   17.872000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[   17.872000] snd_hda_intel: Unknown symbol snd_card_proc_new
[   17.872000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[   17.872000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   17.872000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[   17.872000] snd_hda_intel: Unknown symbol snd_ctl_new1
[   17.872000] snd_hda_intel: disagrees about version of symbol snd_component_add
[   17.872000] snd_hda_intel: Unknown symbol snd_component_add
[   17.872000] snd_hda_intel: disagrees about version of symbol snd_card_new
[   17.872000] snd_hda_intel: Unknown symbol snd_card_new
[   17.872000] snd_hda_intel: disagrees about version of symbol snd_ctl_elem_read
[   17.872000] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[   17.876000] snd_hda_intel: disagrees about version of symbol snd_ctl_elem_write
[   17.876000] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[   17.876000] snd_hda_intel: disagrees about version of symbol snd_device_new
[   17.876000] snd_hda_intel: Unknown symbol snd_device_new
[   17.876000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[   17.876000] snd_hda_intel: Unknown symbol snd_card_disconnect
[   17.880000] iwl4965: Unhandled INTA bits 0x04000000
[   17.880000] iwl4965: Disabled INTA bits 0x04000000 were pending
[   17.880000] iwl4965:    with FH_INT = 0x00010000
[   17.884000] iwl4965: REPLY_CT_KILL_CONFIG_CMD succeeded
[   17.924000] cs: IO port probe 0x100-0x3af: excluding 0x228-0x22f 0x378-0x37f
[   17.928000] cs: IO port probe 0x3e0-0x4ff: excluding 0x400-0x427 0x4d0-0x4d7
[   17.928000] cs: IO port probe 0x820-0x8ff: clean.
[   17.928000] cs: IO port probe 0xc00-0xcf7: clean.
[   17.928000] cs: IO port probe 0xa00-0xaff: clean.
[   23.232000] input: ImPS/2 Generic Wheel Mouse as /class/input/input4
[   23.236000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x228 ; irq 3 ; dma 3.
[   23.236000] pnp: Device 00:09 disabled.
[   23.236000] parport_pc 00:0c: reported by Plug and Play ACPI
[   23.236000] parport0: PC-style at 0x378 (0x778), irq 5, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   23.484000] lp0: using parport0 (interrupt-driven).
[   23.568000] Adding 524624k swap on /dev/sda6.  Priority:-1 extents:1 across:524624k
[   23.952000] EXT3 FS on sda5, internal journal
[   24.260000] NET: Registered protocol family 10
[   24.260000] lo: Disabled Privacy Extensions
[   24.580000] AppArmor: Unregistered secondary security module: capability
[   25.068000] ACPI: Battery Slot [BAT0] (battery present)
[   25.164000] ACPI: AC Adapter [ADP0] (on-line)
[   25.180000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   25.192000] No dock devices found.
[   25.216000] input: Power Button (FF) as /class/input/input5
[   25.216000] ACPI: Power Button (FF) [PWRF]
[   25.216000] input: Lid Switch as /class/input/input6
[   25.216000] ACPI: Lid Switch [LID]
[   25.216000] input: Power Button (CM) as /class/input/input7
[   25.216000] ACPI: Power Button (CM) [PWRB]
[   26.560000] ppdev: user-space parallel port driver
[   26.884000] audit(1189224316.383:3): REJECTING m access to /etc/passwd (cupsd(5274) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
[   26.884000] audit(1189224316.383:4): REJECTING m access to /etc/group (cupsd(5274) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
[   26.884000] audit(1189224316.383:5): REJECTING m access to /etc/group (cupsd(5274) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
[   27.024000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.060000] audit(1189224316.383:6): REJECTING w access to /dev/tty (cupsd(5274) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
[   27.412000] apm: BIOS not found.
[   27.600000] AppArmor: Registered secondary security module: capability.
[   27.600000] Capability LSM initialized as secondary
[   27.840000] Bluetooth: Core ver 2.11
[   27.840000] NET: Registered protocol family 31
[   27.840000] Bluetooth: HCI device and connection manager initialized
[   27.840000] Bluetooth: HCI socket layer initialized
[   27.884000] Bluetooth: L2CAP ver 2.8
[   27.884000] Bluetooth: L2CAP socket layer initialized
[   28.112000] Bluetooth: RFCOMM socket layer initialized
[   28.112000] Bluetooth: RFCOMM TTY layer initialized
[   28.112000] Bluetooth: RFCOMM ver 1.8
[   35.132000] eth0: no IPv6 routers present
[   95.552000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   95.552000] snd_hda_intel: Unknown symbol snd_ctl_add
[   95.552000] snd_hda_intel: disagrees about version of symbol snd_card_register
[   95.552000] snd_hda_intel: Unknown symbol snd_card_register
[   95.552000] snd_hda_intel: disagrees about version of symbol snd_card_free
[   95.552000] snd_hda_intel: Unknown symbol snd_card_free
[   95.552000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[   95.552000] snd_hda_intel: Unknown symbol snd_card_proc_new
[   95.552000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[   95.552000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   95.552000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[   95.552000] snd_hda_intel: Unknown symbol snd_ctl_new1
[   95.552000] snd_hda_intel: disagrees about version of symbol snd_component_add
[   95.552000] snd_hda_intel: Unknown symbol snd_component_add
[   95.552000] snd_hda_intel: disagrees about version of symbol snd_card_new
[   95.552000] snd_hda_intel: Unknown symbol snd_card_new
[   95.552000] snd_hda_intel: disagrees about version of symbol snd_ctl_elem_read
[   95.552000] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[   95.552000] snd_hda_intel: disagrees about version of symbol snd_ctl_elem_write
[   95.552000] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[   95.552000] snd_hda_intel: disagrees about version of symbol snd_device_new
[   95.552000] snd_hda_intel: Unknown symbol snd_device_new
[   95.552000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[   95.552000] snd_hda_intel: Unknown symbol snd_card_disconnect

```

When I try do "sudo modprobe snd-hda-intel" I get the message:
"FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-10-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)"

Combining this error message with dmesg, I'm guessing that the relevant part of dmesg is the last part, where the driver disagrees about everything.
Can anybody please help, since I don't know what's going on?

---

### Post by nille on 2007-09-10
I'm not sure about the 6625WD, but on my 6224W (with the same card?) I get sound if I compile ALSA 1.0.14 using the instructions here:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

But before compiling alsa-driver I manually replace the file patch_realtek.c (if you follow the instructions it's found in /usr/src/alsa/alsa-driver-1.0.14/alsa-kernel/pci/hda/) with the one found here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326/comments/61](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326/comments/61)


I hope this helps!


EDIT:
I have tried ALSA 1.0.15rc1, and it works great BUT you will have to add this line at the end of the file /etc/modprobe.d/alsa-base:
```
options snd-hda-intel model=toshiba
```

---

### Post by sebastiansjoberg on 2007-09-10
On my Zepto 6324 I get the same problems with versioning of the symbols. I have to do modprobe -f snd-hda-intel to make the module load but I still don't get any sound :confused:.

---

### Post by sebastiansjoberg on 2007-09-10
Finally sound working. For some reason I had to move the ubuntu supplied snd-hda-intel module out of the way and then running depmod -a to have the dependencies calculated correctly. Also I think I had to add the --with-kernel-dir=<insert path to kernel headers here> option to the configure script in alsa-driver to get rid of the kernel version mismatch.

---

### Post by juvalencia on 2007-09-11
> **nille said:**
> I'm not sure about the 6625WD, but on my 6224W (with the same card?) I get sound if I compile ALSA 1.0.14 using the instructions here:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

But before compiling alsa-driver I manually replace the file patch_realtek.c (if you follow the instructions it's found in /usr/src/alsa/alsa-driver-1.0.14/alsa-kernel/pci/hda/) with the one found here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326/comments/61](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326/comments/61)


I hope this helps!


EDIT:
I have tried ALSA 1.0.15rc1, and it works great BUT you will have to add this line at the end of the file /etc/modprobe.d/alsa-base:
```
options snd-hda-intel model=toshiba
```


I did two, but the utils i cannot install becaouse it say this packages need a curses library
i did the modprobe with snd-hda-intel, etc
but i cannot find the alsa-base file in /etc/modprobe.d/

Please Advaise!!!!!!!!!

---

### Post by nero_86 on 2007-09-12
> **juvalencia said:**
> I did two, but the utils i cannot install becaouse it say this packages need a curses library
i did the modprobe with snd-hda-intel, etc
but i cannot find the alsa-base file in /etc/modprobe.d/

Please Advaise!!!!!!!!!

In Debian I've installed libncurses5-dev and compiling goes fine. But I cannot make the alsa-utils...

I'll retry whit the alsa source on the realtek web site!

---

### Post by nero_86 on 2007-09-12
I've made an automatic installation of the driver 4.06 founded in the realtek site.

Everything goes fine and rebooting and playing a cd the volume monitor indicates that the sound is working. But there is still no sound...

Any idea?

---

### Post by nero_86 on 2007-09-12
Finally I did it!!! :popcorn:

The sound have a decent volume.

I've recompiled the alsa-driver 1.0.14 whit the realtek patch [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104) realtek12.tar.gz

tar the driver and the patch. Put te 2 files of the patch in alsa-kernel/pci/hda/ in the alsa-driver source.
Then ./configure , make, make install.
In the file /etc/modprobe.d/alsa-base control that there is the 

```
options snd-hda-intel model=auto

```

line. Instead of auto you can put your model if you know it. (in my case is toshiba)
Then in /etc/modprobe.d/sound put this line

```
options snd-hda-intel index=0
options snd-hda-intel model=toshiba

```

And last create a file named snd-hda-intel.modprobe in /etc/modprobe.d/ too. In this file put the well known line

```
options snd-hda-intel model=toshiba

```

It worked for me! Hope could be helpfull!!!:)

---

### Post by Jeanpaul145 on 2007-09-13
> **nille said:**
> I'm not sure about the 6625WD, but on my 6224W (with the same card?) I get sound if I compile ALSA 1.0.14 using the instructions here:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

But before compiling alsa-driver I manually replace the file patch_realtek.c (if you follow the instructions it's found in /usr/src/alsa/alsa-driver-1.0.14/alsa-kernel/pci/hda/) with the one found here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326/comments/61](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326/comments/61)


I hope this helps!


EDIT:
I have tried ALSA 1.0.15rc1, and it works great BUT you will have to add this line at the end of the file /etc/modprobe.d/alsa-base:
```
options snd-hda-intel model=toshiba
```


I have tried adding the last line to alsa-base, and the sound still doen't work. The weird thing is that according to ALSA itself, nothing is wrong (meaning, of course, that everything SHOULD be in working order).
That said, I tried your solution with alsa 1.0.15[COLOR="Red"]rc2[/COLOR]...

---

### Post by Corentin38 on 2007-09-15
I also have a zepto6224W notebook but i couldn't make the sound working by the two method of Nille :
-compiling the 1.0.15rc1 with the toshiba line
-compiling the 1.0.14rc4 with the realtek patch from the launchpad...

The first method doesn't give me sound but the card is recognised twice ! Realtek ID268 and hda-intel
The second method doesn't give me soud either butno recognised card at all. Even I can't manage the volume.

I'm also using Ubuntu gusty tribe 5 !
Could you give more precision on what have done the first time you made it work ?
Like the version of alsa-driver 1.0.14 or 1.0.14rc1/2/3/4 ??
And the place you found the realtek patch ? Launchpad ubuntu ? Alsa bug report ?

Thanks !!

---

### Post by kimi2013 on 2007-09-15
Hi,

i have the same problem with realteak 268 and ubuntu kernel 2.6.22.11
my solution is:
i take the latest driver from here . [ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/)
compile it without any patches.
./configure --with-cards=hda-intel
make
 make install
copy the module snd-hda-intel from 
/lib/modules/2.6.22.11/kernel/sound/pci/hda/snd-hda-intel
 to 
/lib/modules/2.6.22.11/ubuntu/media/snd-hda-intel/snd-hda-intel

and sound works for me.

greetings

Kimi

---

### Post by csgrad on 2007-09-15
I have a toshiba U300 Satellite Laptop and have tried many of the suggestions in many of the topics in this forums with no luck.  I have the ALC 268 sound and tried the ```
options snd-hda-intel model=
``` with toshiba, test, auto and all of the other suggestions. None worked until for some reason i tried acer which is working great :) So maybe this will help someone else also :). Also, if you are looking for an easy way to install alsa you can get it from the realtek website packaged together with an install script that does many of the steps listed in the guides automatically.

---

### Post by ilkkal on 2007-09-16
No succes with Zepto 6024W either. Tried all of above solutions.

---

### Post by nille on 2007-09-16
Huh, this is wierd. It got it to work on my 6224W by doing this in Xubuntu Gutsy:

Install dependencies:
```
sudo apt-get install libncurses5-dev build-essential ncurses-dev gettext linux-headers-`uname -r`
```

Download the files needed (latest stable version is 1.0.15):
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
[ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)

I save mine on separate home-partition first (in case of reinstall) to a directory called ~/ALSA/1.0.15 and then I do the following:

```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/ALSA/1.0.15/* .
sudo tar xjf alsa-driver-1.0.15.tar.bz2
sudo tar xjf alsa-lib-1.0.15.tar.bz2
sudo tar xjf alsa-utils-1.0.15.tar.bz2
```

Then compile (I'm not sure if the --with-oss=yes is needed):
```
cd alsa-driver-1.0.15/
sudo ./configure --with-cards=hda-intel --with-oss=yes
sudo make
sudo make install
cd ../alsa-lib-1.0.15/
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils-1.0.15/
sudo ./configure
sudo make
sudo make install
```

Then edit alsa-base in /etc/modprobe.d:
```
sudo vim /etc/modprobe.d/alsa-base
```

And add the following line at the end:
> options snd-hda-intel model=toshiba

Reboot.

Well, I don't know.. it works for me. To get alsamixer detect the proper channels I have to play a sound (like the file "ubuntu Sax.ogg" in ~/Examples).

Are you using Feisty, perhaps?


**EDIT:** One thing that might help is to do the following (solution provided by: sebastiansjoberg):
```
sudo mv /lib/modules/2.6.22-11-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko /tmp
sudo depmod -a
```

**EDIT2:** Updated post since ALSA 1.0.15 is released. Please note that some people need to replace model=toshiba with something else (like model=acer). Search this post, or test some other model. All models available is listed in the file /usr/src/alsa/alsa-driver-1.0.15/alsa-kernel/Documentation/ALSA-Configuration.txt somewhere (search for "ALC268").

**EDIT3:** New info! As some other members have pointed out it should now be fine just to install the package(s) **linux-backports-modules** and edit the /etc/modprobe.d/alsa-base file as usual, to get sound. THIS MEANS YOU PROBABLY WON'T HAVE TO COMPILE ALSA TO GET SOUND WORKING ANYMORE! :)

---

### Post by Corentin38 on 2007-09-16
I'm sorry, but followed exactly your way to compile the alsa driver on my 6224W and I'm also using Gusty Tribe5 (with gnome) and it's not working.

In the dmesg, there are many lines talking about some unknown symbols or disagree ... and one which says that the driver is loaded, but that no devces were found !

That's terrible ! Same laptop, same distro, same way and one is working and the other not !! :(

Thank you for trying helping me, by the way !

---

### Post by sebastiansjoberg on 2007-09-19
> **Corentin38 said:**
> I'm sorry, but followed exactly your way to compile the alsa driver on my 6224W and I'm also using Gusty Tribe5 (with gnome) and it's not working.

In the dmesg, there are many lines talking about some unknown symbols or disagree ... and one which says that the driver is loaded, but that no devces were found !

That's terrible ! Same laptop, same distro, same way and one is working and the other not !! :(

Thank you for trying helping me, by the way !

The problem I had was that the module in /lib/modules/2.6.22-11-generic/ubuntu/media/snd-hda-intel conflicted with the one I had built from alsa. So I just moved it to /tmp and ran "sudo depmod -a" and then it worked. Step by step:
```

sudo mv /lib/modules/2.6.22-11-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko /tmp
sudo depmod -a

```

Hope it helps!

---

### Post by Scotty562 on 2007-09-20
Fantastic guys! I've been trying to get my sound working for weeks! Thanks!

---

### Post by sascha70 on 2007-09-20
Super! is running perfect von my Acer Extensa 5220!

Greetings form germany:)

---

### Post by Immortalis on 2007-09-21
I also own a Zepto 6224w and have until today, had no sound. I'm running Gutsy Gibbon tribe 5.

The following two solutions, that **nille** and afterwards **sebastiansjoberg** presents, solved my problem. I however omitted the " --with-oss=yes"  that nille is questioning.

---

### Post by nille on 2007-09-21
I don't know if it works, but you can try setting your model= to something else than toshiba. Available models for the ALC268 are:

acer, auto, toshiba and 3stack

Since you are using a Zepto-computer, please go to [http://www.alsa-project.org](http://www.alsa-project.org), go to bugtracker and locate bug 3388 (called "No sound on the zepto notebooks") and post your aadebug output.

[http://alsa.opensrc.org/aadebug](http://alsa.opensrc.org/aadebug)

---

### Post by Tavathlon on 2007-09-23
Hm, this is really strange...  a couple of days ago, I followed the steps provided by Nille, which gave me sound. Thank you for that, Nille! However, when I started my computer yesterday, there were no sound anymore...  I haven't got the slightest idea of why. I can't really remember whether I rebooted any other times in between and if the sound in that case worked in between those reboots, but that should on the other hand not matter the least, right?

Anyway, I've tried the solutions provided by sebastian and nille later in this thread, without any result. I'm going to try the solution provided by kimi, but I wanted to tell you guys about this anyway. Anyone else experienced the same?

Btw, I have a Zepto Znote 6625WD and running Gutsy Tribe 5...

---

### Post by sebastiansjoberg on 2007-09-23
> **Tavathlon said:**
> Hm, this is really strange...  a couple of days ago, I followed the steps provided by Nille, which gave me sound. Thank you for that, Nille! However, when I started my computer yesterday, there were no sound anymore...  I haven't got the slightest idea of why. I can't really remember whether I rebooted any other times in between and if the sound in that case worked in between those reboots, but that should on the other hand not matter the least, right?

Anyway, I've tried the solutions provided by sebastian and nille later in this thread, without any result. I'm going to try the solution provided by kimi, but I wanted to tell you guys about this anyway. Anyone else experienced the same?

Btw, I have a Zepto Znote 6625WD and running Gutsy Tribe 5...

Wouldn't that be due to a kernel upgrade to 2.6.22-12? After every kernel and maybe modules upgrade you need to redo the procedures. I had the same issue about two days ago.

---

### Post by Tavathlon on 2007-09-23
Er..  well..  that was my first thought as well, when I noticed that the sound was gone..  so I thought I should go through nille's guide again. Apparently, I forgot to do that, and have instead been installing lots of other drives without result...  >.<

It works now anyway. Thanks!  =D

---

### Post by Corentin38 on 2007-09-23
Hum ... the alsa bug repport about the zepto notebooks ... It's me who created it !
And I got the sound working !!

But know you say that you can't have sound anymore with the kernel update, I'm really affraid of updating all the system !!

I will see tomorow ...

Corentin

---

### Post by sebastiansjoberg on 2007-09-23
You can definitely have sound with the kernel upgrade, don't worry. You just have to perform some of the steps again. In my case, I just went to where I have my alsa-driver sources and did the following (your case might not be the same):
```

make clean && make
sudo make install

```
I also had to remove the ubuntu supplied snd-hda-intel.ko module again:
```

sudo rm /lib/modules/2.6.22-12-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko

```

Good luck keeping your sound!

---

### Post by Tavathlon on 2007-10-05
One question to you guys..  are you experiencing low sound quality? Whenever I play music, and regardless of volume, I hear scrapings in the sound, like faint crackles. I'm pretty sure it has to have something to do with the soundcard, and _not_ the speakers, since I have the same problem regardless of what speakers I'm using - different external speakers as well as the internal speakers.

And the speakers are not broken, I'm fairly sure about that - since I've used several ones, of which some usually gives a really nice sound, and I have not really tested to have any loud volumes yet.

Anyone else experiencing the same problem? Is it a hardware problem with my speakers, or is it a problem with the driver?

Best regards
Patrik

---

### Post by Tavathlon on 2007-10-07
Hm, could it be a codec problem? I just realized that the problem is less significant with *.ogg than with *.mp3. The problem is still there though, but only if you raise the volume a little.

Perhaps I should only wait..

---

### Post by Jeanpaul145 on 2007-10-10
> **nille said:**
> Huh, this is wierd. It got it to work on my 6224W by doing this in Xubuntu Gutsy:

Install dependencies:
```
sudo apt-get install libncurses5-dev build-essential ncurses-dev gettext linux-headers-`uname -r`
```

Download the files needed (this is version 1.0.15rc2):
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc2.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc2.tar.bz2)
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc2.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc2.tar.bz2)
[ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2)

I save mine on separate home-partition first (in case of reinstall) to a directory called ~/ALSA/1.0.15rc2 and then I do the following:

```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/ALSA/1.0.15rc2/* .
sudo tar xjf alsa-driver-1.0.15rc2.tar.bz2
sudo tar xjf alsa-lib-1.0.15rc2.tar.bz2
sudo tar xjf alsa-utils-1.0.15rc1.tar.bz2
```

Then compile (I'm not sure if the --with-oss=yes is needed):
```
cd alsa-driver-1.0.15rc2/
sudo ./configure --with-cards=hda-intel --with-oss=yes
sudo make
sudo make install
cd ../alsa-lib-1.0.15rc2/
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils-1.0.15rc1/
sudo ./configure
sudo make
sudo make install
```

Then edit alsa-base in /etc/modprobe.d:
```
sudo vim /etc/modprobe.d/alsa-base
```

And add the following line at the end:


Reboot.

Well, I don't know.. it works for me. To get alsamixer detect the proper channels I have to play a sound (like the file "ubuntu Sax.ogg" in ~/Examples).

Are you using Feisty, perhaps?


**EDIT:** One thing that might help is to do the following (solution provided by: sebastiansjoberg):
```
sudo mv /lib/modules/2.6.22-11-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko /tmp
sudo depmod -a
```


This also worked for me!
I owe you a ** *LOT*** of thanks!!\\:D/ I've been trying to get sound working since Gutsy Tribe 4:-P
I tried this before, with the difference that I didn't copy the sources to /urs/src, but did it straight from my homedir.
btw: This time I did NOT use the --with-oss=yes switch when *./configure*ing the driver package. 
Probably also worth noting: I have sound from BOTH my internal speakers and my speakers connected through the headphones jack.:)
Also, I did a kernel update to 2.6.22.14.20 just moments before :)

---

### Post by Tavathlon on 2007-10-10
Also I have the sound from both internal and external..  but is it really supposed to be like that? I mean, if you plug in external speakers, then I would not want it to be any sound coming from the relatively crappy internal ones..  of course I can mute the internal sound, but still..

---

### Post by nille on 2007-10-10
First things first: I'm running (X)Ubuntu Gutsy, and I'm using alsa-driver-1.0.15rc3, alsa-lib-1.0.15rc3 and alsa-utils-1.0.15rc1 and the 2.6.22-14-generic kernel.

I have compiled with --with-oss=yes, but I still think it doesn't matter.

I have found that if the external speakers are connected to the headphone jack when I boot the sound will appear in both speakers, but if I unplug the external ones, and them plug them right back in, the internal speakers will get muted.

With the 1.0.14(a)-version and the patch the internal speakers never got muted, but now it works with 1.0.15(rc).

I have heard that some ppl using the Znote 6224W (the same computer as I am using) had to use model=acer instead of model=toshiba in alsa-base.

---

### Post by Tavathlon on 2007-10-12
nille, you don't have the problem with scrapings in the sound on the 6224?

---

### Post by LittleReinhart on 2007-10-12
Thanks nille & sebastiansjoberg,

Sound works, but....

When i'm playing a song in xmms, at, lets say 74% sound-level, the sound is increased in time (although all levels stay the same). If is change the sound-level and put it back on 74%, the sound-level sounds the same as befor, but increases in time.

Any idea where I can start looking to solve this?

Thanks,
Reinhart

P.S. It's on a Dell Latitude D830 with Xubuntu 7.10

---

### Post by LittleReinhart on 2007-10-13
Eerrgh.... nevermind my post above. It seems to be a xmms-problem. Sound works fine when playing a movie or so.

My dad never plays mp3's, so I'm gonna ignore this problem.

Greetings,
Reinhart

---

### Post by brainout on 2007-10-13
[QUOTE=nille;3374613]Huh, this is wierd. It got it to work on my 6224W by doing this in Xubuntu Gutsy:

Install dependencies:
```
sudo apt-get install libncurses5-dev build-essential ncurses-dev gettext linux-headers-`uname -r`
```

Download the files needed (this is version 1.0.15rc2):
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc2.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc2.tar.bz2)
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc2.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc2.tar.bz2)
[ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2)

I save mine on separate home-partition first (in case of reinstall) to a directory called ~/ALSA/1.0.15rc2 and then I do the following:

```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/ALSA/1.0.15rc2/* .
sudo tar xjf alsa-driver-1.0.15rc2.tar.bz2
sudo tar xjf alsa-lib-1.0.15rc2.tar.bz2
sudo tar xjf alsa-utils-1.0.15rc1.tar.bz2
```

Then compile (I'm not sure if the --with-oss=yes is needed):
```
cd alsa-driver-1.0.15rc2/
sudo ./configure --with-cards=hda-intel --with-oss=yes
sudo make
sudo make install
cd ../alsa-lib-1.0.15rc2/
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils-1.0.15rc1/
sudo ./configure
sudo make
sudo make install
```

Then edit alsa-base in /etc/modprobe.d:
```
sudo vim /etc/modprobe.d/alsa-base
```

And add the following line at the end:

```
options snd-hda-intel model=toshiba
```

Reboot.


Fantastic my laptop Acer Travelmate 5720 work perfectly with your suggets.

**PS:** for Acer users, before operate step by step, read the alsa documentation (/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz) and you can find 
the supported options for your model.
I replaced

```
options snd-hda-intel model=toshiba
```

with

```
options snd-hda-intel model=acer
```


Thanks so much i love open source :KS

---

### Post by FractalBrain on 2007-11-01
Thanks for the work going into post #14!!!  It got me up an running right away!  Let me share:

I have an Acer Extensa 4620Z with a intel 82801H rev03 sound system.

Problem:  Sound came through the front speakers, but not through the headphone jack.  I dont know if the microphone would have worked or line in, I did not try.

Solution:  I followed the instructions in post #14 with a few differences.  In summary, I used the latest version of ALSA and replaced model=toshiba with model=acer.  Everything else was exactly the same.

In detail:

1.  I went to the ALSA website 
[http://www.alsa-project.org/main/index.php/Download]("http://www.alsa-project.org/main/index.php/Download")
and downloaded the most recent versions (in this case 15 at the end with no release candidate).  I downloaded the files with the same name as mentioned in post #14 (move the cursor over the package version numbers to see the actual name of the file to download).  

2.  I used
> options snd-hda-intel model=acer

I finished the last step, rebooted and ta da, it worked!!!  Thanks for the help!!!!  If anyone the same computer and problem, I hope you find this :-).

---

### Post by Laellis on 2007-11-03
So which one of you guys got the optical output working? People are saying "I got the sounds working" but through what? I've managed to get everything else to work except for the s/pdif. 

Got Znote 6625WD and got the "basic" sounds to work by installing ALSA 1.0.15 and adding that model=acer line at the end of alsa-basic.

---

### Post by nille on 2007-11-03
Laellis: I have got sound through speakers, and via a normal 3.5mm TRS connector. I doubt the 7.1-sound works, but I have not tried yet. Neither have I tried microphone.

---

### Post by Laellis on 2007-11-03
Yeah I know those work with ease but it's enabling the optical output I'm having problems with. And it seems none has really made that work.

---

### Post by hpalma on 2007-11-03
I followed the steps nille described except i used alsa-1.0.15 final version.
I can't get the sound to work. I have a Toshiba P100 and running gutsy.
I tried every possible value in the model parameter.

Any idea or any way i can find more information about what's wrong ?

---

### Post by Ruddigger on 2007-11-18
I have an HP with ALC268 and nothing I did helped at all. The one thing that made the sound card work was changing the model to acer.
Hope this helps...
Thanks for all the info!

---

### Post by jhvillegas2 on 2007-11-21
> **nille said:**
> 

Install dependencies:
```
sudo apt-get install libncurses5-dev build-essential ncurses-dev gettext linux-headers-`uname -r`
```

Hey, Folks--I am pretty much stuck in the mud on this part (sudo, above).  I downloaded the file and I don't know what to do with it or how to handle it.  Your help is appreciated.

John Villegas

> I save mine on separate home-partition first (in case of reinstall) to a directory called ~/ALSA/1.0.15rc2 and then I do the following:



And with this, so what directories do you actually save the file to?

Thanks,
John--I will bug you later about the rest of this post when I get the first two things right.

---

### Post by Jeanpaul145 on 2007-11-21
> **jhvillegas2 said:**
> Hey, Folks--I am pretty much stuck in the mud on this part (sudo, above).  I downloaded the file and I don't know what to do with it or how to handle it.  Your help is appreciated.

John Villegas



And with this, so what directories do you actually save the file to?

Thanks,
John--I will bug you later about the rest of this post when I get the first two things right.

the idea of the sudo apt-get install command is to type it into a bash shell :popcorn:
By doing that you'll install some very-much-needed dependencies.

Alternatively, you could try the scripts I've made for myself so simplify the whole compilation process.

Be aware though that I've **not** tested this script thoroughly - Any help on that part would be greatly appreciated.

In regard of this (and any other) script and/or command: I've just read [this]("http://ubuntuforums.org/announcement.php?a=54") and so should you all.

If you're not in a position to check what scripts do, have someone else check them for you:popcorn:

---

### Post by jhvillegas2 on 2007-11-21
> **nille said:**
> 

Install dependencies:
```
sudo apt-get install libncurses5-dev build-essential ncurses-dev gettext linux-headers-`uname -r`
```


I tried this command and I got the following:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libncurses5-dev

```

Any suggestions, please.

Thanks,
John Villegas

---

### Post by nille on 2007-11-22
Perhaps you have to enable some additional repositories? Are you running Gutsy (7.10)? Have you enabled universe/main (found in System -> Administration, or via the repository settings in Synaptic).

Otherwise you can find the package here:
[http://packages.ubuntu.com/gutsy/libdevel/libncurses5-dev](http://packages.ubuntu.com/gutsy/libdevel/libncurses5-dev)

(Change gutsy in the above link if you're using some other version).


~/ALSA/1.0.15/ is the same as /home/$USER/ALSA/1.0.15, but just keep an eye on your cd- and cp-commands and you'll do fine if you save the files elsewhere.

Note that ALSA 1.0.15 is now released - which means you should use that one instead of the rc-versions, causing som minor differences in my previous post.

I'll se if I can update the previous post :)

---

### Post by LeslieL on 2007-11-25
Sounds like you guys have the solution for my problem - ALC268 chip in a laptop, no sound whatever I do. (The Arch Linux discussion group says support for that chip is enabled in kernel 2.6.23, which they've had since August, but who knows when we'll get it). 

Is there any way you experts could put together a tidy step-by-step howto for us newbies to follow?

---

### Post by Jeanpaul145 on 2007-11-25
> **LeslieL said:**
> Sounds like you guys have the solution for my problem - ALC268 chip in a laptop, no sound whatever I do. (The Arch Linux discussion group says support for that chip is enabled in kernel 2.6.23, which they've had since August, but who knows when we'll get it). 

Is there any way you experts could put together a tidy step-by-step howto for us newbies to follow?

Since you have an ALC268 chip you might wanna try my script-collection (see my previous post).

---

### Post by LeslieL on 2007-11-25
Thanks. I realized I'd skipped a page or two of posts and missed your solution. I'll read through this thread more carefully when I have more time.

---

### Post by LeslieL on 2007-11-26
Thank you, Nille and Jeanpaul145. It was so good to reboot and be greeted by a cheerful little tune. I didn't even need the last file-move step. I'd tried recompiling alsa before, but the key thing was Nille's getting the complete set of files to recompile. You guys ought to get a medal.

The people who sold me this laptop were telling me I should just give up on Linux and go back to Windows - that Linux just couldn't handle the latest hardware. They don't know the power of the Linux community!

---

### Post by Jeanpaul145 on 2007-11-26
> **LeslieL said:**
> Thank you, Nille and Jeanpaul145. It was so good to reboot and be greeted by a cheerful little tune. I didn't even need the last file-move step. I'd tried recompiling alsa before, but the key thing was Nille's getting the complete set of files to recompile. You guys ought to get a medal.

The people who sold me this laptop were telling me I should just give up on Linux and go back to Windows - that Linux just couldn't handle the latest hardware. They don't know the power of the Linux community!

Indeed, but what do salesmen know?

Those who can do, do, those who can't, sell:popcorn:

---

### Post by anjoze on 2007-11-26
I just instaled Ubuntu 7.10 on my Dell Latitude D830 and then:
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Reboot computer and it's perfect

---

### Post by CremeDeLaCreme on 2007-12-13
post14 and post16 made my sound working. BIG THX. my laptop model is medion MD98000.

in /etc/modprobe.d/alsa-base I just added 'auto' instead of 'toshiba'

---

### Post by Jeanpaul145 on 2007-12-14
> **Jeanpaul145 said:**
> the idea of the sudo apt-get install command is to type it into a bash shell :popcorn:
By doing that you'll install some very-much-needed dependencies.

Alternatively, you could try the scripts I've made for myself so simplify the whole compilation process.

Be aware though that I've **not** tested this script thoroughly - Any help on that part would be greatly appreciated.

In regard of this (and any other) script and/or command: I've just read [this]("http://ubuntuforums.org/announcement.php?a=54") and so should you all.

If you're not in a position to check what scripts do, have someone else check them for you:popcorn:

Hey btw: I've found out that linux-backports-modules might also work instead of compiling from source. You still have to add a line like
```
 "options snd-hda-intel model=acer" 
``` 
to /etc/modprobe.d/alsa-base manually though.

---

### Post by LeslieL on 2007-12-15
I tried that before using Jeanpaul's script. It didn't work - I needed the script. 

Thanks again to our brilliant fixers.

---

### Post by Jeanpaul145 on 2007-12-15
> **LeslieL said:**
> I tried that before using Jeanpaul's script. It didn't work - I needed the script. 

Thanks again to our brilliant fixers.

About those scripts: I found a couple of bugs in there (I compiled before I used the backports):lolflag:

Here is a new revision (including some feedback as to what is happening). 

Still the same rules though: if it eats your data and tries to take over the world, I'm not responsible :popcorn:

And I still appreciate feedback on those scripts:)

---

### Post by DakoCwerf on 2007-12-20
here is the script that worked for me with acer sound.

download and install alsa-driver, alsa-lib, alsa-util (all vers 1.0.15)
when you will install driver - configure it with hda-intel card.
> 
cd alsa-driver-1.0.15
./configure --with-cards=hda-intel
make
sudo make install

next -  upgrade for backports-modules
> sudo aptitude install linux-backports-modules-generic

last step - edit your modprobe - add 1 line at the end
> sudo gedit /etc/modprobe.d/alsa-base
add this line:
> options snd-hda-intel model=acer

reboot.

would be glad to hear some feedback - did it work for you?

---

### Post by Jeanpaul145 on 2008-03-09
> **nille said:**
> First things first: I'm running (X)Ubuntu Gutsy, and I'm using alsa-driver-1.0.15rc3, alsa-lib-1.0.15rc3 and alsa-utils-1.0.15rc1 and the 2.6.22-14-generic kernel.

I have compiled with --with-oss=yes, but I still think it doesn't matter.

I have found that if the external speakers are connected to the headphone jack when I boot the sound will appear in both speakers, but if I unplug the external ones, and them plug them right back in, the internal speakers will get muted.

With the 1.0.14(a)-version and the patch the internal speakers never got muted, but now it works with 1.0.15(rc).

I have heard that some ppl using the Znote 6224W (the same computer as I am using) had to use model=acer instead of model=toshiba in alsa-base.

Alsa 1.0.16 is out. most of currrent day audio cards should be fixed.

---

