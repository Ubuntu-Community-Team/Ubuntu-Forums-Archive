---
title: "Sony Vaio C220E boot problems"
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by thelanlegend on 2007-08-12
I have a Sony Vaio C220E with a 160GB hard drive with two 15GB partitions, one for feisty (sda1) and one for gutsy(sda2) and the rest partitioned for home(sda4). The problem I have is: everytime I boot my laptop (into either feisty or gutsy), it gets about an inch and a half into the progress indicator and goes verbose (during the file system check I think). All I can catch is "file system is clean" which doesn't seem like a good reason to go verbose. Sometimes it also plays back the transactions for one of my partitions.

I recently did a fresh install of gutsy tribe 4 and switched it to a ext3 partition to see if there was a change but to no avail. I'm not sure where to check for more information or what to try next. Any ideas?

Here is the output of dmesg:
```
[    0.000000] Linux version 2.6.20-16-generic (root@3v1) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #1 SMP Thu Jun 21 09:30:14 CEST 2007 (Ubuntu 2.6.20-16.29+suspend2~2.2.10+3v1ubuntu0-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003f590000 end: 000000003f690000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003f690000 size: 0000000000008000 end: 000000003f698000 type: 3
[    0.000000] copy_e820_map() start: 000000003f698000 size: 0000000000068000 end: 000000003f700000 type: 4
[    0.000000] copy_e820_map() start: 000000003f700000 size: 0000000000900000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed00000 size: 0000000000000400 end: 00000000fed00400 type: 2
[    0.000000] copy_e820_map() start: 00000000fed14000 size: 0000000000006000 end: 00000000fed1a000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed1c000 size: 0000000000074000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff000000 size: 0000000001000000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f690000 (usable)
[    0.000000]  BIOS-e820: 000000003f690000 - 000000003f698000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f698000 - 000000003f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f71a0
[    0.000000] Entering add_active_range(0, 0, 259728) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259728
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259728
[    0.000000] On node 0 totalpages: 259728
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 237 pages used for memmap
[    0.000000]   HighMem zone: 30115 pages, LIFO batch:7
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f70d0
[    0.000000] ACPI: RSDT (v001   Sony     VAIO 0x20061219 PTL  0x00000000) @ 0x3f6904eb
[    0.000000] ACPI: FADT (v002   Sony     VAIO 0x20061219 PTL  0x0000005a) @ 0x3f697c9a
[    0.000000] ACPI: MADT (v001   Sony     VAIO 0x20061219 PTL  0x0000005a) @ 0x3f697d1e
[    0.000000] ACPI: HPET (v001   Sony     VAIO 0x20061219 PTL  0x0000005a) @ 0x3f697d86
[    0.000000] ACPI: MCFG (v001   Sony     VAIO 0x20061219 PTL  0x0000005a) @ 0x3f697dbe
[    0.000000] ACPI: SLIC (v001   Sony     VAIO 0x20061219 PTL  0x01000000) @ 0x3f697dfa
[    0.000000] ACPI: MADT (v001   Sony     VAIO 0x20061219 PTL  0x00000000) @ 0x3f697f70
[    0.000000] ACPI: BOOT (v001   Sony     VAIO 0x20061219 PTL  0x00000001) @ 0x3f697fd8
[    0.000000] ACPI: SSDT (v001   Sony     VAIO 0x20061219 PTL  0x20050624) @ 0x3f69161d
[    0.000000] ACPI: SSDT (v001   Sony     VAIO 0x20061219 PTL  0x20050624) @ 0x3f690b16
[    0.000000] ACPI: SSDT (v001   Sony     VAIO 0x20061219 PTL  0x20050624) @ 0x3f690a75
[    0.000000] ACPI: SSDT (v001   Sony     VAIO 0x20061219 PTL  0x20050624) @ 0x3f69053b
[    0.000000] ACPI: DSDT (v001   Sony     VAIO 0x20061219 PTL  0x20050624) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: 2 duplicate APIC table ignored.
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
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Detected 1662.515 MHz processor.
[   16.805683] Built 1 zonelists.  Total pages: 257699
[   16.805686] Kernel command line: root=UUID=da533003-0a2b-4966-8bc7-a3ab7125139e ro quiet splash
[   16.805833] mapped APIC to ffffd000 (fee00000)
[   16.805835] mapped IOAPIC to ffffc000 (fec00000)
[   16.805838] Enabling fast FPU save and restore... done.
[   16.805842] Enabling unmasked SIMD FPU exception support... done.
[   16.805850] Initializing CPU#0
[   16.805914] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   16.807412] Console: colour VGA+ 80x25
[   16.807807] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.808161] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.833690] Memory: 1018632k/1038912k available (2049k kernel code, 19536k reserved, 1052k data, 332k init, 121408k highmem)
[   16.833699] virtual kernel memory layout:
[   16.833700]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   16.833701]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.833702]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.833704]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.833705]       .init : 0xc040e000 - 0xc0461000   ( 332 kB)
[   16.833706]       .data : 0xc0300544 - 0xc04076d4   (1052 kB)
[   16.833707]       .text : 0xc0100000 - 0xc0300544   (2049 kB)
[   16.833710] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.833861] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   16.833866] hpet0: 3 64-bit timers, 14318180 Hz
[   16.834871] Using HPET for base-timer
[   16.913741] Calibrating delay using timer specific routine.. 3328.82 BogoMIPS (lpj=6657654)
[   16.913779] Security Framework v1.0.0 initialized
[   16.913783] SELinux:  Disabled at boot.
[   16.913799] Mount-cache hash table entries: 512
[   16.913918] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   16.913925] monitor/mwait feature present.
[   16.913927] using mwait in idle threads.
[   16.913931] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.913933] CPU: L2 cache: 2048K
[   16.913935] CPU: Physical Processor ID: 0
[   16.913937] CPU: Processor Core ID: 0
[   16.913939] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   16.913947] Compat vDSO mapped to ffffe000.
[   16.913950] Remapping vsyscall page to ffffe000
[   16.913961] Checking 'hlt' instruction... OK.
[   16.929810] SMP alternatives: switching to UP code
[   16.930136] Early unpacking initramfs... done
[   17.247894] ACPI: Core revision 20060707
[   17.248178] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   17.283790] CPU0: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[   17.283810] SMP alternatives: switching to SMP code
[   17.283890] Booting processor 1/1 eip 3000
[   17.294264] Initializing CPU#1
[   17.373041] Calibrating delay using timer specific routine.. 3325.11 BogoMIPS (lpj=6650225)
[   17.373048] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   17.373053] monitor/mwait feature present.
[   17.373055] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.373057] CPU: L2 cache: 2048K
[   17.373059] CPU: Physical Processor ID: 0
[   17.373061] CPU: Processor Core ID: 1
[   17.373062] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   17.373539] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[   17.373559] Total of 2 processors activated (6653.93 BogoMIPS).
[   17.373755] ENABLING IO-APIC IRQs
[   17.373951] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   17.520813] checking TSC synchronization across 2 CPUs: passed.
[    0.003997] Brought up 2 CPUs
[    0.166384] migration_cost=165
[    0.166656] Booting paravirtualized kernel on bare hardware
[    0.166743] Time: 15:26:56  Date: 06/29/107
[    0.166771] NET: Registered protocol family 16
[    0.166850] EISA bus registered
[    0.166857] ACPI: bus type pci registered
[    0.166977] PCI: PCI BIOS revision 2.10 entry at 0xfd863, last bus=10
[    0.166979] PCI: Using configuration type 1
[    0.166981] Setting up standard PCI resources
[    0.283752] ACPI: Interpreter enabled
[    0.283754] ACPI: Using IOAPIC for interrupt routing
[    0.307971] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.307979] PCI: Probing PCI hardware (bus 00)
[    0.320391] Boot video device is 0000:00:02.0
[    0.321090] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.321095] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.322354] PCI: Transparent bridge - 0000:00:1e.0
[    0.322426] PCI: Bus #0b (-#0e) is hidden behind transparent bridge #0a (-#0b) (try 'pci=assign-busses')
[    0.322429] Please report the result to linux-kernel to fix this permanently
[    0.322511] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.354060] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.354423] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.354783] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.355141] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.356545] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.357665] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.357909] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 *3 4 5 6 7 11 12 14 15)
[    0.358149] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.358394] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.358635] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.358877] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.359118] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 *4 5 6 7 10 12 14 15)
[    0.359356] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 11 12 14 15)
[    0.363890] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.363899] pnp: PnP ACPI init
[    0.378605] pnp: PnP ACPI: found 10 devices
[    0.378610] PnPBIOS: Disabled by ACPI PNP
[    0.378650] PCI: Using ACPI for IRQ routing
[    0.378653] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.416698] NET: Registered protocol family 8
[    0.416700] NET: Registered protocol family 20
[    0.417161] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    0.417167] PCI: Bridge: 0000:00:1c.0
[    0.417170]   IO window: 2000-2fff
[    0.417176]   MEM window: c8000000-c9ffffff
[    0.417181]   PREFETCH window: c0000000-c1ffffff
[    0.417187] PCI: Bridge: 0000:00:1c.1
[    0.417190]   IO window: 3000-3fff
[    0.417197]   MEM window: ca000000-cbffffff
[    0.417201]   PREFETCH window: c2000000-c3ffffff
[    0.417207] PCI: Bridge: 0000:00:1c.2
[    0.417210]   IO window: 4000-4fff
[    0.417217]   MEM window: cc000000-cdffffff
[    0.417221]   PREFETCH window: c4000000-c5ffffff
[    0.417228] PCI: Bridge: 0000:00:1c.3
[    0.417231]   IO window: 5000-5fff
[    0.417237]   MEM window: ce000000-cfffffff
[    0.417242]   PREFETCH window: c6000000-c7ffffff
[    0.417254] PCI: Bus 11, cardbus bridge: 0000:0a:03.0
[    0.417256]   IO window: 00006000-000060ff
[    0.417262]   IO window: 00006400-000064ff
[    0.417268]   PREFETCH window: 50000000-53ffffff
[    0.417273]   MEM window: 54000000-57ffffff
[    0.417278] PCI: Bridge: 0000:00:1e.0
[    0.417281]   IO window: 6000-6fff
[    0.417287]   MEM window: d0000000-d00fffff
[    0.417292]   PREFETCH window: 50000000-53ffffff
[    0.417322] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[    0.417329] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.417353] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[    0.417359] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.417383] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    0.417389] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.417413] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 21 (level, low) -> IRQ 19
[    0.417419] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.417430] PCI: Enabling device 0000:00:1e.0 (0004 -> 0007)
[    0.417436] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.417453] PCI: Enabling device 0000:0a:03.0 (0000 -> 0003)
[    0.417457] ACPI: PCI Interrupt 0000:0a:03.0[A] -> GSI 16 (level, low) -> IRQ 17
[    0.417488] NET: Registered protocol family 2
[    0.471324] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.471438] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.471908] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.472160] TCP: Hash tables configured (established 131072 bind 65536)
[    0.472163] TCP reno registered
[    0.487371] checking if image is initramfs... it is
[    1.114066] Simple Boot Flag at 0x36 set to 0x1
[    1.114556] audit: initializing netlink socket (disabled)
[    1.114574] audit(1185722816.856:1): initialized
[    1.114677] highmem bounce pool size: 64 pages
[    1.114766] VFS: Disk quotas dquot_6.5.1
[    1.114788] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.114838] io scheduler noop registered
[    1.114841] io scheduler anticipatory registered
[    1.114843] io scheduler deadline registered
[    1.114854] io scheduler cfq registered (default)
[    1.115116] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    1.115175] assign_interrupt_mode Found MSI capability
[    1.115178] Allocate Port Service[0000:00:1c.0:pcie00]
[    1.115213] Allocate Port Service[0000:00:1c.0:pcie02]
[    1.115342] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    1.115401] assign_interrupt_mode Found MSI capability
[    1.115404] Allocate Port Service[0000:00:1c.1:pcie00]
[    1.115438] Allocate Port Service[0000:00:1c.1:pcie02]
[    1.115561] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    1.115620] assign_interrupt_mode Found MSI capability
[    1.115622] Allocate Port Service[0000:00:1c.2:pcie00]
[    1.115655] Allocate Port Service[0000:00:1c.2:pcie02]
[    1.115780] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    1.115839] assign_interrupt_mode Found MSI capability
[    1.115841] Allocate Port Service[0000:00:1c.3:pcie00]
[    1.115872] Allocate Port Service[0000:00:1c.3:pcie02]
[    1.116057] isapnp: Scanning for PnP cards...
[    1.469400] isapnp: No Plug & Play device found
[    1.490544] Real Time Clock Driver v1.12ac
[    1.490753] hpet_resources: 0xfed00000 is busy
[    1.490771] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.491418] mice: PS/2 mouse device common for all mice
[    1.491989] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.492142] input: Macintosh mouse button emulation as /class/input/input0
[    1.492183] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.492186] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.492433] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.496472] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.502154] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.502157] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.502160] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.502162] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.502164] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.502234] PCI driver pci_eisa lacks driver specific resume support.
[    1.502645] EISA: Probing bus 0 at eisa.0
[    1.502653] Cannot allocate resource for EISA slot 1
[    1.502657] Cannot allocate resource for EISA slot 2
[    1.502659] Cannot allocate resource for EISA slot 3
[    1.502662] Cannot allocate resource for EISA slot 4
[    1.502664] Cannot allocate resource for EISA slot 5
[    1.502666] Cannot allocate resource for EISA slot 6
[    1.502677] EISA: Detected 0 cards.
[    1.532809] TCP cubic registered
[    1.532818] NET: Registered protocol family 1
[    1.532841] Starting balanced_irq
[    1.532847] Using IPI No-Shortcut mode
[    1.532849] Suspend v2.2.10
[    1.532941] Suspend2 Userspace Storage Manager support registered.
[    1.532965] Suspend2 Basic User Interface support registered.
[    1.532988] Suspend2 Compressor support registered.
[    1.533010] Suspend2 Block I/O support registered.
[    1.533032] Suspend2 Swap Allocator support registered.
[    1.533058] Suspend2 File Allocator support registered.
[    1.533062] Suspend2 Userspace UI support registered.
[    1.533116] ACPI: (supports S0 S3 S4 S5)
[    1.533162]   Magic number: 15:151:438
[    1.533662] Time: tsc clocksource has been installed.
[    1.708254] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.762089] Capability LSM initialized
[    2.808019] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [  Sony] OemTableId [    VAIO] [20060707]
[    2.808526] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [  Sony] OemTableId [    VAIO] [20060707]
[    2.809040] Monitor-Mwait will be used to enter C-1 state
[    2.809044] Monitor-Mwait will be used to enter C-2 state
[    2.809048] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.809053] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.815981] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [  Sony] OemTableId [    VAIO] [20060707]
[    2.816178] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [  Sony] OemTableId [    VAIO] [20060707]
[    2.816803] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    2.816808] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.376000] ACPI Exception (acpi_thermal-0412): AE_NOT_FOUND, Invalid active threshold [0] [20060707]
[    3.380000] ACPI: Thermal Zone [TZ00] (55 C)
[    3.380000] ACPI Exception (acpi_thermal-0412): AE_NOT_FOUND, Invalid active threshold [0] [20060707]
[    3.380000] ACPI: Thermal Zone [TZ01] (55 C)
[    3.384000] Time: hpet clocksource has been installed.
[    3.800000] usbcore: registered new interface driver usbfs
[    3.800000] USB driver usbfs lacks resume support.
[    3.800000] usbcore: registered new interface driver hub
[    3.800000] usbcore: registered new device driver usb
[    3.804000] USB Universal Host Controller Interface driver v3.0
[    3.804000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[    3.804000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.804000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.804000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.804000] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[    3.804000] usb usb1: configuration #1 chosen from 1 choice
[    3.804000] hub 1-0:1.0: USB hub found
[    3.804000] hub 1-0:1.0: 2 ports detected
[    3.868000] ieee1394: Initialized config rom entry `ip1394'
[    3.876000] SCSI subsystem initialized
[    3.888000] libata version 2.20 loaded.
[    3.912000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 16
[    3.912000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.912000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.912000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.912000] uhci_hcd 0000:00:1d.1: irq 16, io base 0x00001840
[    3.912000] usb usb2: configuration #1 chosen from 1 choice
[    3.912000] hub 2-0:1.0: USB hub found
[    3.912000] hub 2-0:1.0: 2 ports detected
[    4.016000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    4.016000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    4.016000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.016000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    4.016000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    4.016000] usb usb3: configuration #1 chosen from 1 choice
[    4.016000] hub 3-0:1.0: USB hub found
[    4.016000] hub 3-0:1.0: 2 ports detected
[    4.120000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[    4.120000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    4.120000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.120000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    4.120000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[    4.120000] usb usb4: configuration #1 chosen from 1 choice
[    4.120000] hub 4-0:1.0: USB hub found
[    4.120000] hub 4-0:1.0: 2 ports detected
[    4.152000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    4.224000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[    4.224000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.224000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.224000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.224000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.224000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.224000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd0444000
[    4.228000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.228000] usb usb5: configuration #1 chosen from 1 choice
[    4.228000] hub 5-0:1.0: USB hub found
[    4.228000] hub 5-0:1.0: 8 ports detected
[    4.332000] PCI: Enabling device 0000:0a:03.1 (0000 -> 0002)
[    4.332000] ACPI: PCI Interrupt 0000:0a:03.1[A] -> GSI 16 (level, low) -> IRQ 17
[    4.384000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[d0005000-d00057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.384000] ata_piix 0000:00:1f.1: version 2.10ac1
[    4.384000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[    4.384000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.384000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.384000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    4.388000] scsi0 : ata_piix
[    4.688000] usb 1-1: device not accepting address 2, error -71
[    4.708000] ata1.00: ATAPI, max UDMA/33
[    4.872000] ata1.00: configured for UDMA/33
[    4.872000] scsi1 : ata_piix
[    4.872000] ata2: port disabled. ignoring.
[    4.876000] scsi 0:0:0:0: CD-ROM            SONY     DVD RW AW-G540A  1.74 PQ: 0 ANSI: 5
[    4.876000] ata_piix 0000:00:1f.2: MAP [ P0 P2 XX XX ]
[    4.876000] ata_piix 0000:00:1f.2: invalid MAP value 0
[    5.032000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
[    5.036000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.036000] ata3: SATA max UDMA/133 cmd 0x000118d0 ctl 0x000118c6 bmdma 0x000118b0 irq 21
[    5.036000] ata4: SATA max UDMA/133 cmd 0x000118c8 ctl 0x000118c2 bmdma 0x000118b8 irq 21
[    5.036000] scsi2 : ata_piix
[    5.200000] ata3.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[    5.200000] ata3.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC74P, max UDMA/100
[    5.200000] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.208000] ata3.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[    5.208000] ata3.00: configured for UDMA/100
[    5.208000] scsi3 : ata_piix
[    5.296000] usb 5-6: new high speed USB device using ehci_hcd and address 3
[    5.364000] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
[    5.364000] PCI driver PCI_IDE lacks driver specific resume support.
[    5.380000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.380000] Uniform CD-ROM driver Revision: 3.20
[    5.380000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.380000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[    5.380000] sda: Write Protect is off
[    5.380000] sda: Mode Sense: 00 3a 00 00
[    5.380000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.380000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[    5.380000] sda: Write Protect is off
[    5.380000] sda: Mode Sense: 00 3a 00 00
[    5.380000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.380000]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[    5.384000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    5.408000]  sda1 sda2 sda3 sda4
[    5.416000] sd 2:0:0:0: Attached scsi disk sda
[    5.496000] usb 5-6: configuration #1 chosen from 1 choice
[    5.656000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[08004603024f0dc4]
[    5.696000] Attempting manual resume
[    5.696000] Replacing swsusp.
[    5.696000] No storage allocator is currently active. Rechecking whether we can use one.
[    5.696000] Suspend2: Resume2 parameter is empty. Suspending will be disabled.
[    5.696000] Compression Driver: Argh! Nothing follows me in the pipeline!
[    5.696000] Compressor didn't initialise okay.
[    5.696000] Suspend2: Initialise modules failed!
[    5.696000] swsusp: Resume From Partition 8:3
[    5.696000] PM: Checking swsusp image.
[    5.696000] PM: Resume from disk failed.
[    5.704000] ReiserFS: sda2: found reiserfs format "3.6" with standard journal
[    5.704000] ReiserFS: sda2: using ordered data mode
[    5.716000] ReiserFS: sda2: journal params: device sda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    5.716000] ReiserFS: sda2: checking transaction log (sda2)
[    5.736000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[    5.740000] ReiserFS: sda2: Using r5 hash to sort names
[    5.916000] usb 1-1: configuration #1 chosen from 1 choice
[    5.932000] usbcore: registered new interface driver libusual
[    5.932000] USB driver libusual lacks resume support.
[    6.412000] Initializing USB Mass Storage driver...
[    6.412000] scsi4 : SCSI emulation for USB Mass Storage devices
[    6.412000] usbcore: registered new interface driver usb-storage
[    6.412000] USB Mass Storage support registered.
[    6.412000] usb-storage: device found at 3
[    6.412000] usb-storage: waiting for device to settle before scanning
[   11.420000] usb-storage: device scan complete
[   11.420000] scsi 4:0:0:0: Direct-Access     Sony     USB   HS-CARD    4.52 PQ: 0 ANSI: 0
[   11.472000] sd 4:0:0:0: Attached scsi removable disk sdb
[   11.472000] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   15.324000] intel_rng: FWH not detected
[   15.356000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.356000] PCI driver shpchp lacks driver specific resume support.
[   15.356000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.420000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.632000] ieee80211_crypt: registered algorithm 'NULL'
[   15.720000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   15.720000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   15.732000] agpgart: Detected an Intel 945GM Chipset.
[   15.732000] agpgart: Detected 7932K stolen memory.
[   15.748000] agpgart: AGP aperture is 256M @ 0xb0000000
[   15.772000] iTCO_vendor_support: vendor-support=0
[   15.832000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   15.832000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   15.832000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.896000] usbcore: registered new interface driver hiddev
[   15.896000] USB driver hiddev lacks resume support.
[   15.932000] Yenta: CardBus bridge found at 0000:0a:03.0 [104d:820f]
[   15.932000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   15.932000] Yenta: Routing CardBus interrupts to PCI
[   15.932000] Yenta TI: socket 0000:0a:03.0, mfunc 0x01121b22, devctl 0x64
[   16.008000] input: Logitech USB Receiver as /class/input/input2
[   16.008000] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
[   16.044000] input: Logitech USB Receiver as /class/input/input3
[   16.044000] input,hiddev96: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1
[   16.044000] usbcore: registered new interface driver usbhid
[   16.044000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   16.140000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   16.140000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   16.164000] usbcore: registered new interface driver xpad
[   16.164000] USB driver xpad lacks resume support.
[   16.164000] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   16.164000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   16.164000] Socket status: 30000006
[   16.164000] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   16.164000] pcmcia: parent PCI bridge I/O window: 0x6000 - 0x6fff
[   16.164000] cs: IO port probe 0x6000-0x6fff: clean.
[   16.164000] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd00fffff
[   16.164000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   16.164000] PCI: Enabling device 0000:0a:03.2 (0000 -> 0002)
[   16.164000] ACPI: PCI Interrupt 0000:0a:03.2[B] -> GSI 17 (level, low) -> IRQ 16
[   16.164000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   16.164000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   16.164000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   16.164000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   16.164000] sky2 0000:02:00.0: v1.13 addr 0xc8000000 irq 17 Yukon-FE (0xb7) rev 1
[   16.164000] sky2 eth0: addr 00:13:a9:a3:82:17
[   16.168000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   16.296000] input: PS/2 Mouse as /class/input/input4
[   16.316000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input5
[   16.448000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   16.448000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   16.524000] cs: IO port probe 0x100-0x3af: clean.
[   16.528000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   16.528000] cs: IO port probe 0x820-0x8ff: clean.
[   16.528000] cs: IO port probe 0xc00-0xcf7: clean.
[   16.528000] cs: IO port probe 0xa00-0xaff: clean.
[   16.648000] hda_codec: Unknown model for ALC262, trying auto-probe from BIOS...
[   16.968000] fuse init (API version 7.8)
[   17.028000] PCI driver parport_pc lacks driver specific resume support.
[   17.032000] lp: driver loaded but no devices found
[   17.080000] Adding 1494036k swap on /dev/disk/by-uuid/9d78dcfa-26f0-4eec-87c1-25618cdc10a4.  Priority:-1 extents:1 across:1494036k
[   18.072000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   40.464000] ReiserFS: sda4: found reiserfs format "3.6" with standard journal
[   40.464000] ReiserFS: sda4: using ordered data mode
[   40.472000] ReiserFS: sda4: journal params: device sda4, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   40.472000] ReiserFS: sda4: checking transaction log (sda4)
[   40.524000] ReiserFS: sda4: Using r5 hash to sort names
[   41.136000] Using specific hotkey driver
[   41.240000] ACPI: AC Adapter [ADP1] (on-line)
[   41.272000] ACPI: ACPI Dock Station Driver 
[   41.348000] input: Lid Switch as /class/input/input6
[   41.348000] ACPI: Lid Switch [LID0]
[   41.372000] input: Power Button (CM) as /class/input/input7
[   41.372000] ACPI: Power Button (CM) [PWRB]
[   41.420000] ibm_acpi: ec object not found
[   41.464000] ACPI: Battery Slot [BAT0] (battery absent)
[   41.476000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   41.500000] ACPI Sony Notebook Control Driver v0.2 successfully installed
[   41.508000] pcc_acpi: loading...
[   42.708000] sky2 eth0: enabling interface
[   42.712000] sky2 eth0: ram buffer 4K
[   43.132000] ppdev: user-space parallel port driver
[   44.072000] apm: BIOS not found.
[   44.172000] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   44.172000] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[   44.172000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[   44.172000] sonypi: device allocated minor is 62
[   44.176000] input: Sony Vaio Jogdial as /class/input/input8
[   44.176000] input: Sony Vaio Keys as /class/input/input9
[   44.176000] vmmon: module license 'unspecified' taints kernel.
[   44.180000] /dev/vmmon[7644]: Module vmmon: registered with major=10 minor=165
[   44.180000] /dev/vmmon[7644]: Module vmmon: initialized
[   44.224000] sonypi command failed at drivers/char/sonypi.c : sonypi_call1 (line 646)
[   44.268000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 657)
[   44.304000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 659)
[   44.344000] sonypi command failed at drivers/char/sonypi.c : sonypi_call1 (line 646)
[   44.472000] [drm] Initialized drm 1.1.0 20060810
[   44.600000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   44.604000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   44.968000] /dev/vmnet: open called by PID 7810 (vmnet-bridge)
[   44.968000] /dev/vmnet: hub 0 does not exist, allocating memory.
[   44.968000] /dev/vmnet: port on hub 0 successfully opened
[   44.968000] bridge-eth0: enabling the bridge
[   44.968000] bridge-eth0: up
[   44.968000] bridge-eth0: already up
[   44.968000] bridge-eth0: attached
[   45.284000] /dev/vmnet: open called by PID 7823 (vmnet-netifup)
[   45.284000] /dev/vmnet: hub 1 does not exist, allocating memory.
[   45.284000] /dev/vmnet: port on hub 1 successfully opened
[   45.288000] /dev/vmnet: open called by PID 7845 (vmnet-netifup)
[   45.288000] /dev/vmnet: hub 8 does not exist, allocating memory.
[   45.288000] /dev/vmnet: port on hub 8 successfully opened
[   45.352000] /dev/vmnet: open called by PID 7844 (vmnet-natd)
[   45.352000] /dev/vmnet: port on hub 8 successfully opened
[   45.580000] /dev/vmnet: open called by PID 7881 (vmnet-dhcpd)
[   45.580000] /dev/vmnet: port on hub 1 successfully opened
[   45.584000] /dev/vmnet: open called by PID 7874 (vmnet-dhcpd)
[   45.584000] /dev/vmnet: port on hub 8 successfully opened
[   45.772000] Bluetooth: Core ver 2.11
[   45.772000] NET: Registered protocol family 31
[   45.772000] Bluetooth: HCI device and connection manager initialized
[   45.772000] Bluetooth: HCI socket layer initialized
[   45.804000] Bluetooth: L2CAP ver 2.8
[   45.804000] Bluetooth: L2CAP socket layer initialized
[   45.920000] Bluetooth: RFCOMM socket layer initialized
[   45.920000] Bluetooth: RFCOMM TTY layer initialized
[   45.920000] Bluetooth: RFCOMM ver 1.8
[   72.676000] NET: Registered protocol family 10
[   72.676000] lo: Disabled Privacy Extensions
[   72.676000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   72.676000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   83.336000] vmnet1: no IPv6 routers present
[   83.512000] vmnet8: no IPv6 routers present
[   85.780000] NET: Registered protocol family 17
[   85.812000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  103.688000] eth1: no IPv6 routers present

```

For good measure, here is the output of /var/log/messages:
```
Aug 12 01:58:19 node6 syslogd 1.4.1#21ubuntu2: restart.
Aug 12 02:10:17 node6 kernel: [ 1363.504000] pcmcia: Detected deprecated PCMCIA ioctl usage from process: discover.
Aug 12 02:10:17 node6 kernel: [ 1363.504000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
Aug 12 02:10:17 node6 kernel: [ 1363.504000] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
Aug 12 02:10:36 node6 kernel: [ 1381.992000] ppdev: user-space parallel port driver
Aug 12 02:28:15 node6 -- MARK --
Aug 12 02:48:15 node6 -- MARK --
Aug 12 03:08:15 node6 -- MARK --
Aug 12 03:28:15 node6 -- MARK --
Aug 12 03:38:22 node6 gnome-power-manager: (tech) Suspending computer because the power button has been pressed
Aug 12 03:38:22 node6 dhcdbd: Unrequested down ?:3
Aug 12 03:38:22 node6 kernel: [ 6648.724000] sky2 eth0: disabling interface
Aug 12 03:38:23 node6 kernel: [ 6649.196000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Aug 12 03:38:23 node6 kernel: [ 6649.408000] ACPI: PCI interrupt for device 0000:06:00.0 disabled
Aug 12 04:29:50 node6 kernel: [ 6652.972000] Stopping tasks ... done.
Aug 12 04:29:50 node6 kernel: [ 6653.108000] Suspending console(s)
Aug 12 04:29:50 node6 kernel: [ 6653.148000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 663)
Aug 12 04:29:50 node6 kernel: [ 6653.192000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 665)
Aug 12 04:29:50 node6 kernel: [ 6653.212000] sd 3:0:0:0: [sda] Synchronizing SCSI cache
Aug 12 04:29:50 node6 kernel: [ 6653.320000] sd 3:0:0:0: [sda] Stopping disk
Aug 12 04:29:50 node6 kernel: [ 6654.328000] ACPI: PCI interrupt for device 0000:0a:03.2 disabled
Aug 12 04:29:50 node6 kernel: [ 6654.360000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Aug 12 04:29:50 node6 kernel: [ 6654.376000] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Aug 12 04:29:50 node6 kernel: [ 6654.376000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Aug 12 04:29:50 node6 kernel: [ 6654.392000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
Aug 12 04:29:50 node6 kernel: [ 6654.392000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Aug 12 04:29:50 node6 kernel: [ 6654.392000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Aug 12 04:29:50 node6 kernel: [ 6654.392000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Aug 12 04:29:50 node6 kernel: [ 6654.400000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Aug 12 04:29:50 node6 kernel: [ 6654.992000] Disabling non-boot CPUs ...
Aug 12 04:29:50 node6 kernel: [ 6655.108000] CPU 1 is now offline
Aug 12 04:29:50 node6 kernel: [ 6655.108000] SMP alternatives: switching to UP code
Aug 12 04:29:50 node6 kernel: [ 6655.108000] CPU1 is down
Aug 12 04:29:50 node6 kernel: [ 6655.108000] Enabling non-boot CPUs ...
Aug 12 04:29:50 node6 kernel: [ 6655.120000] SMP alternatives: switching to SMP code
Aug 12 04:29:50 node6 kernel: [ 6655.120000] Booting processor 1/1 eip 3000
Aug 12 04:29:50 node6 kernel: [ 6655.128000] Initializing CPU#1
Aug 12 04:29:50 node6 kernel: [ 6655.208000] Calibrating delay using timer specific routine.. 3324.93 BogoMIPS (lpj=6649869)
Aug 12 04:29:50 node6 kernel: [ 6655.208000] monitor/mwait feature present.
Aug 12 04:29:50 node6 kernel: [ 6655.208000] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug 12 04:29:50 node6 kernel: [ 6655.208000] CPU: L2 cache: 2048K
Aug 12 04:29:50 node6 kernel: [ 6655.208000] CPU: Physical Processor ID: 0
Aug 12 04:29:50 node6 kernel: [ 6655.208000] CPU: Processor Core ID: 1
Aug 12 04:29:50 node6 kernel: [ 6655.208000] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
Aug 12 04:29:50 node6 kernel: [ 6655.208000] Switched to high resolution mode on CPU 1
Aug 12 04:29:50 node6 kernel: [ 6655.208000] CPU1 is up
Aug 12 04:29:50 node6 kernel: [ 6655.724000] ACPI Exception (evregion-0420): AE_TIME, Returned by Handler for [EmbeddedControl] [20070126]
Aug 12 04:29:50 node6 kernel: [ 6655.724000] ACPI Exception (dswexec-0462): AE_TIME, While resolving operands for [OpcodeName unavailable] [20070126]
Aug 12 04:29:50 node6 kernel: [ 6655.724000] ACPI Error (psparse-0537): Method parse/execution failed [\_WAK] (Node df848228), AE_TIME
Aug 12 04:29:50 node6 kernel: [ 6655.724000] ACPI Exception (hwsleep-0581): AE_TIME, During Method _WAK [20070126]
Aug 12 04:29:50 node6 kernel: [ 6655.748000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
Aug 12 04:29:50 node6 kernel: [ 6655.764000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Aug 12 04:29:50 node6 gnome-power-manager: (tech) Resuming computer
Aug 12 04:29:50 node6 kernel: [ 6655.828000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
Aug 12 04:29:50 node6 kernel: [ 6655.828000] usb usb1: root hub lost power or was reset
Aug 12 04:29:50 node6 kernel: [ 6655.828000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 16
Aug 12 04:29:50 node6 kernel: [ 6655.828000] usb usb2: root hub lost power or was reset
Aug 12 04:29:50 node6 kernel: [ 6655.828000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Aug 12 04:29:50 node6 kernel: [ 6655.828000] usb usb3: root hub lost power or was reset
Aug 12 04:29:50 node6 kernel: [ 6655.828000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
Aug 12 04:29:50 node6 kernel: [ 6655.828000] usb usb4: root hub lost power or was reset
Aug 12 04:29:50 node6 kernel: [ 6655.844000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
Aug 12 04:29:50 node6 kernel: [ 6655.844000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Aug 12 04:29:50 node6 kernel: [ 6655.860000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
Aug 12 04:29:50 node6 kernel: [ 6655.924000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[d0005000-d00057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Aug 12 04:29:50 node6 kernel: [ 6655.940000] ACPI: PCI Interrupt 0000:0a:03.2[B] -> GSI 17 (level, low) -> IRQ 16
Aug 12 04:29:50 node6 kernel: [ 6656.336000] ata1.00: configured for UDMA/33
Aug 12 04:29:50 node6 kernel: [ 6656.428000] sd 3:0:0:0: [sda] Starting disk
Aug 12 04:29:50 node6 kernel: [ 6657.440000] ata3.00: configured for UDMA/100
Aug 12 04:29:50 node6 kernel: [ 6657.456000] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Aug 12 04:29:50 node6 kernel: [ 6657.484000] sd 3:0:0:0: [sda] Write Protect is off
Aug 12 04:29:50 node6 kernel: [ 6657.484000] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 12 04:29:50 node6 gnome-power-manager: (tech) suspend failed
Aug 12 04:29:50 node6 kernel: [ 6657.540000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
Aug 12 04:29:50 node6 kernel: [ 6657.580000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 663)
Aug 12 04:29:50 node6 kernel: [ 6657.620000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 665)
Aug 12 04:29:50 node6 kernel: [ 6657.660000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
Aug 12 04:29:50 node6 kernel: [ 6657.664000] Restarting tasks ... <6>usb 5-6: USB disconnect, address 2
Aug 12 04:29:50 node6 kernel: [ 6657.664000] done.
Aug 12 04:29:50 node6 kernel: [ 6657.776000] usb 5-6: new high speed USB device using ehci_hcd and address 3
Aug 12 04:29:51 node6 kernel: [ 6657.968000] usb 5-6: configuration #1 chosen from 1 choice
Aug 12 04:29:51 node6 kernel: [ 6657.972000] scsi6 : SCSI emulation for USB Mass Storage devices
Aug 12 04:29:51 node6 kernel: [ 6658.240000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
Aug 12 04:29:51 node6 kernel: [ 6658.240000] sky2 0000:02:00.0: v1.14 addr 0xc8000000 irq 17 Yukon-FE (0xb7) rev 1
Aug 12 04:29:51 node6 kernel: [ 6658.244000] sky2 eth0: addr 00:13:a9:a3:82:17
Aug 12 04:29:51 node6 kernel: [ 6658.324000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Aug 12 04:29:51 node6 kernel: [ 6658.324000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Aug 12 04:29:51 node6 kernel: [ 6658.336000] sky2 eth0: enabling interface
Aug 12 04:29:51 node6 kernel: [ 6658.340000] sky2 eth0: ram buffer 4K
Aug 12 04:29:51 node6 kernel: [ 6658.340000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 12 04:29:51 node6 kernel: [ 6658.380000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.1mp
Aug 12 04:29:51 node6 kernel: [ 6658.380000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Aug 12 04:29:51 node6 kernel: [ 6658.380000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Aug 12 04:29:51 node6 kernel: [ 6658.380000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Aug 12 04:29:52 node6 kernel: [ 6659.188000] input: Lid Switch as /class/input/input8
Aug 12 04:29:52 node6 kernel: [ 6659.192000] ACPI: Lid Switch [LID0]
Aug 12 04:29:52 node6 kernel: [ 6659.204000] input: Power Button (CM) as /class/input/input9
Aug 12 04:29:52 node6 kernel: [ 6659.204000] ACPI: Power Button (CM) [PWRB]
Aug 12 04:29:52 node6 kernel: [ 6659.352000] ACPI Exception (thermal-0400): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
Aug 12 04:29:52 node6 kernel: [ 6659.356000] ACPI: Thermal Zone [TZ00] (34 C)
Aug 12 04:29:52 node6 kernel: [ 6659.356000] ACPI Exception (thermal-0400): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
Aug 12 04:29:52 node6 kernel: [ 6659.356000] ACPI: Thermal Zone [TZ01] (34 C)
Aug 12 04:29:52 node6 kernel: [ 6659.412000] ACPI: AC Adapter [ADP1] (off-line)
Aug 12 04:29:53 node6 kernel: [ 6660.212000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 12 04:29:53 node6 kernel: [ 6660.452000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Aug 12 04:29:54 node6 kernel: [ 6662.012000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Aug 12 04:29:55 node6 kernel: [ 6662.980000] scsi 6:0:0:0: Direct-Access     Sony     USB   HS-CARD    4.52 PQ: 0 ANSI: 0
Aug 12 04:29:56 node6 kernel: [ 6663.028000] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Aug 12 04:29:56 node6 kernel: [ 6663.028000] sd 6:0:0:0: Attached scsi generic sg2 type 0
Aug 12 04:30:03 node6 kernel: [ 6670.608000] UDF-fs: No VRS found
Aug 12 04:31:10 node6 kernel: [ 6737.768000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Aug 12 04:32:13 node6 kernel: [ 6800.116000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Aug 12 04:34:21 node6 kernel: [ 6928.264000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Aug 12 04:34:36 node6 kernel: [ 6943.516000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Aug 12 04:35:47 node6 kernel: [ 7014.852000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Aug 12 04:36:51 node6 exiting on signal 15
Aug 12 04:38:01 node6 syslogd 1.4.1#21ubuntu2: restart.
Aug 12 04:38:01 node6 kernel: Inspecting /boot/System.map-2.6.22-9-generic
Aug 12 04:38:01 node6 kernel: Loaded 25417 symbols from /boot/System.map-2.6.22-9-generic.
Aug 12 04:38:01 node6 kernel: Symbols match kernel version 2.6.22.
Aug 12 04:38:01 node6 kernel: No module symbols loaded - kernel modules not enabled. 
Aug 12 04:38:01 node6 kernel: [    0.000000] Linux version 2.6.22-9-generic (buildd@palmer) (gcc version 4.1.3 20070718 (prerelease) (Ubuntu 4.1.2-14ubuntu1)) #1 SMP Fri Aug 3 00:50:37 GMT 2007 (Ubuntu 2.6.22-9.25-generic)
Aug 12 04:38:01 node6 kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 12 04:38:01 node6 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Aug 12 04:38:01 node6 kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Aug 12 04:38:01 node6 kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Aug 12 04:38:01 node6 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f690000 (usable)
Aug 12 04:38:01 node6 kernel: [    0.000000]  BIOS-e820: 000000003f690000 - 000000003f698000 (ACPI data)
Aug 12 04:38:01 node6 kernel: [    0.000000]  BIOS-e820: 000000003f698000 - 000000003f700000 (ACPI NVS)
Aug 12 04:38:01 node6 kernel: [    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
Aug 12 04:38:01 node6 kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Aug 12 04:38:01 node6 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Aug 12 04:38:01 node6 kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Aug 12 04:38:01 node6 kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Aug 12 04:38:01 node6 kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Aug 12 04:38:01 node6 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 12 04:38:01 node6 kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Aug 12 04:38:01 node6 kernel: [    0.000000] 118MB HIGHMEM available.
Aug 12 04:38:01 node6 kernel: [    0.000000] 896MB LOWMEM available.
Aug 12 04:38:01 node6 kernel: [    0.000000] found SMP MP-table at 000f71a0
Aug 12 04:38:01 node6 kernel: [    0.000000] Zone PFN ranges:
Aug 12 04:38:01 node6 kernel: [    0.000000]   DMA             0 ->     4096
Aug 12 04:38:01 node6 kernel: [    0.000000]   Normal       4096 ->   229376
Aug 12 04:38:01 node6 kernel: [    0.000000]   HighMem    229376 ->   259728
Aug 12 04:38:01 node6 kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 12 04:38:01 node6 kernel: [    0.000000]     0:        0 ->   259728
Aug 12 04:38:01 node6 kernel: [    0.000000] DMI present.
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: RSDP 000F70D0, 0014 (r0 PTLTD )
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: RSDT 3F6904EB, 0050 (r1   Sony     VAIO 20061219 PTL         0)
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: FACP 3F697C9A, 0084 (r2   Sony     VAIO 20061219 PTL        5A)
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: DSDT 3F691DF7, 5EA3 (r1   Sony     VAIO 20061219 PTL  20050624)
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: FACS 3F698FC0, 0040
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: APIC 3F697D1E, 0068 (r1   Sony     VAIO 20061219 PTL        5A)
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: HPET 3F697D86, 0038 (r1   Sony     VAIO 20061219 PTL        5A)
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: MCFG 3F697DBE, 003C (r1   Sony     VAIO 20061219 PTL        5A)
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: SLIC 3F697DFA, 0176 (r1   Sony     VAIO 20061219 PTL   1000000)
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: APIC 3F697F70, 0068 (r1   Sony     VAIO 20061219 PTL         0)
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: BOOT 3F697FD8, 0028 (r1   Sony     VAIO 20061219 PTL         1)
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: SSDT 3F69161D, 07DA (r1   Sony     VAIO 20061219 PTL  20050624)
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: SSDT 3F690B16, 028F (r1   Sony     VAIO 20061219 PTL  20050624)
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: SSDT 3F690A75, 00A1 (r1   Sony     VAIO 20061219 PTL  20050624)
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: SSDT 3F69053B, 053A (r1   Sony     VAIO 20061219 PTL  20050624)
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 12 04:38:01 node6 kernel: [    0.000000] Processor #0 6:15 APIC version 20
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 12 04:38:01 node6 kernel: [    0.000000] Processor #1 6:15 APIC version 20
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Aug 12 04:38:01 node6 kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug 12 04:38:01 node6 kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 12 04:38:01 node6 kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Aug 12 04:38:01 node6 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 12 04:38:01 node6 kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
Aug 12 04:38:01 node6 kernel: [    0.000000] Built 1 zonelists.  Total pages: 257699
Aug 12 04:38:01 node6 kernel: [    0.000000] Kernel command line: root=UUID=0628370b-8483-4f24-afe1-9064b5bd3d5c ro quiet splash
Aug 12 04:38:01 node6 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 12 04:38:01 node6 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 12 04:38:01 node6 kernel: [    0.000000] Initializing CPU#0
Aug 12 04:38:01 node6 kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 12 04:38:01 node6 kernel: [    0.000000] Detected 1662.664 MHz processor.
Aug 12 04:38:01 node6 kernel: [   15.302485] Console: colour VGA+ 80x25
Aug 12 04:38:01 node6 kernel: [   15.302945] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 12 04:38:01 node6 kernel: [   15.303443] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 12 04:38:01 node6 kernel: [   15.345351] Memory: 1018568k/1038912k available (2010k kernel code, 19644k reserved, 917k data, 364k init, 121408k highmem)
Aug 12 04:38:01 node6 kernel: [   15.345366] virtual kernel memory layout:
Aug 12 04:38:01 node6 kernel: [   15.345367]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Aug 12 04:38:01 node6 kernel: [   15.345369]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 12 04:38:01 node6 kernel: [   15.345371]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 12 04:38:01 node6 kernel: [   15.345373]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 12 04:38:01 node6 kernel: [   15.345375]       .init : 0xc03e1000 - 0xc043c000   ( 364 kB)
Aug 12 04:38:01 node6 kernel: [   15.345376]       .data : 0xc02f6806 - 0xc03dbe64   ( 917 kB)
Aug 12 04:38:01 node6 kernel: [   15.345378]       .text : 0xc0100000 - 0xc02f6806   (2010 kB)
Aug 12 04:38:01 node6 kernel: [   15.345383] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 12 04:38:01 node6 kernel: [   15.345429] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug 12 04:38:01 node6 kernel: [   15.345459] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Aug 12 04:38:01 node6 kernel: [   15.345467] hpet0: 3 64-bit timers, 14318180 Hz
Aug 12 04:38:01 node6 kernel: [   15.426366] Calibrating delay using timer specific routine.. 3329.39 BogoMIPS (lpj=6658795)
Aug 12 04:38:01 node6 kernel: [   15.426397] Security Framework v1.0.0 initialized
Aug 12 04:38:01 node6 kernel: [   15.426403] SELinux:  Disabled at boot.
Aug 12 04:38:01 node6 kernel: [   15.426422] Mount-cache hash table entries: 512
Aug 12 04:38:01 node6 kernel: [   15.426595] monitor/mwait feature present.
Aug 12 04:38:01 node6 kernel: [   15.426598] using mwait in idle threads.
Aug 12 04:38:01 node6 kernel: [   15.426603] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug 12 04:38:01 node6 kernel: [   15.426607] CPU: L2 cache: 2048K
Aug 12 04:38:01 node6 kernel: [   15.426611] CPU: Physical Processor ID: 0
Aug 12 04:38:01 node6 kernel: [   15.426614] CPU: Processor Core ID: 0
Aug 12 04:38:01 node6 kernel: [   15.426630] Compat vDSO mapped to ffffe000.
Aug 12 04:38:01 node6 kernel: [   15.426649] Checking 'hlt' instruction... OK.
Aug 12 04:38:01 node6 kernel: [   15.442492] SMP alternatives: switching to UP code
Aug 12 04:38:01 node6 kernel: [   15.443110] Early unpacking initramfs... done
Aug 12 04:38:01 node6 kernel: [   15.968621] ACPI: Core revision 20070126
Aug 12 04:38:01 node6 kernel: [   15.968693] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 12 04:38:01 node6 kernel: [   16.006773] CPU0: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
Aug 12 04:38:01 node6 kernel: [   16.006799] SMP alternatives: switching to SMP code
Aug 12 04:38:01 node6 kernel: [   16.006892] Booting processor 1/1 eip 3000
Aug 12 04:38:01 node6 kernel: [   16.017231] Initializing CPU#1
Aug 12 04:38:01 node6 kernel: [   16.097330] Calibrating delay using timer specific routine.. 3325.10 BogoMIPS (lpj=6650203)
Aug 12 04:38:01 node6 kernel: [   16.097347] monitor/mwait feature present.
Aug 12 04:38:01 node6 kernel: [   16.097351] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug 12 04:38:01 node6 kernel: [   16.097355] CPU: L2 cache: 2048K
Aug 12 04:38:01 node6 kernel: [   16.097358] CPU: Physical Processor ID: 0
Aug 12 04:38:01 node6 kernel: [   16.097360] CPU: Processor Core ID: 1
Aug 12 04:38:01 node6 kernel: [   16.098186] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
Aug 12 04:38:01 node6 kernel: [   16.098217] Total of 2 processors activated (6654.49 BogoMIPS).
Aug 12 04:38:01 node6 kernel: [   16.098422] ENABLING IO-APIC IRQs
Aug 12 04:38:01 node6 kernel: [   16.098641] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 12 04:38:01 node6 kernel: [   16.245233] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug 12 04:38:01 node6 kernel: [   16.265227] Brought up 2 CPUs
Aug 12 04:38:01 node6 kernel: [   16.370595] migration_cost=39
Aug 12 04:38:01 node6 kernel: [   16.370781] Booting paravirtualized kernel on bare hardware
Aug 12 04:38:01 node6 kernel: [   16.370874] Time: 10:37:17  Date: 07/12/107
Aug 12 04:38:01 node6 kernel: [   16.370902] NET: Registered protocol family 16
Aug 12 04:38:01 node6 kernel: [   16.371030] EISA bus registered
Aug 12 04:38:01 node6 kernel: [   16.371038] ACPI: bus type pci registered
Aug 12 04:38:01 node6 kernel: [   16.371188] PCI: PCI BIOS revision 2.10 entry at 0xfd863, last bus=10
Aug 12 04:38:01 node6 kernel: [   16.371191] PCI: Using configuration type 1
Aug 12 04:38:01 node6 kernel: [   16.371194] Setting up standard PCI resources
Aug 12 04:38:01 node6 kernel: [   16.386219] ACPI: EC: GPE=0x17, ports=0x66, 0x62
Aug 12 04:38:01 node6 kernel: [   16.504976] ACPI: Interpreter enabled
Aug 12 04:38:01 node6 kernel: [   16.504980] ACPI: (supports S0 S3 S4 S5)
Aug 12 04:38:01 node6 kernel: [   16.505008] ACPI: Using IOAPIC for interrupt routing
Aug 12 04:38:01 node6 kernel: [   16.533365] ACPI: EC: GPE=0x17, ports=0x66, 0x62
Aug 12 04:38:01 node6 kernel: [   16.533450] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 12 04:38:01 node6 kernel: [   16.534494] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Aug 12 04:38:01 node6 kernel: [   16.534500] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
Aug 12 04:38:01 node6 kernel: [   16.536033] PCI: Transparent bridge - 0000:00:1e.0
Aug 12 04:38:01 node6 kernel: [   16.536137] PCI: Bus #0b (-#0e) is hidden behind transparent bridge #0a (-#0b) (try 'pci=assign-busses')
Aug 12 04:38:01 node6 kernel: [   16.536141] Please report the result to linux-kernel to fix this permanently
Aug 12 04:38:01 node6 kernel: [   16.577998] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
Aug 12 04:38:01 node6 kernel: [   16.578159] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 *3 4 5 6 7 11 12 14 15)
Aug 12 04:38:01 node6 kernel: [   16.578315] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Aug 12 04:38:01 node6 kernel: [   16.578471] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Aug 12 04:38:01 node6 kernel: [   16.578627] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Aug 12 04:38:01 node6 kernel: [   16.578784] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Aug 12 04:38:01 node6 kernel: [   16.578939] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 *4 5 6 7 10 12 14 15)
Aug 12 04:38:01 node6 kernel: [   16.579093] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 11 12 14 15)
Aug 12 04:38:01 node6 kernel: [   16.579288] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 12 04:38:01 node6 kernel: [   16.579303] pnp: PnP ACPI init
Aug 12 04:38:01 node6 kernel: [   16.579316] ACPI: bus type pnp registered
Aug 12 04:38:01 node6 kernel: [   16.588784] pnp: PnP ACPI: found 10 devices
Aug 12 04:38:01 node6 kernel: [   16.588788] ACPI: ACPI bus type pnp unregistered
Aug 12 04:38:01 node6 kernel: [   16.588795] PnPBIOS: Disabled by ACPI PNP
Aug 12 04:38:01 node6 kernel: [   16.588864] PCI: Using ACPI for IRQ routing
Aug 12 04:38:01 node6 kernel: [   16.588868] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 12 04:38:01 node6 kernel: [   16.633248] NET: Registered protocol family 8
Aug 12 04:38:01 node6 kernel: [   16.633252] NET: Registered protocol family 20
Aug 12 04:38:01 node6 kernel: [   16.633331] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
Aug 12 04:38:01 node6 kernel: [   16.633337] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
Aug 12 04:38:01 node6 kernel: [   16.633342] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
Aug 12 04:38:01 node6 kernel: [   16.633348] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
Aug 12 04:38:01 node6 kernel: [   16.636511] Time: tsc clocksource has been installed.
Aug 12 04:38:01 node6 kernel: [   16.636528] Switched to high resolution mode on CPU 0
Aug 12 04:38:01 node6 kernel: [   16.636657] Switched to high resolution mode on CPU 1
Aug 12 04:38:01 node6 kernel: [   16.663837] PCI: Bridge: 0000:00:1c.0
Aug 12 04:38:01 node6 kernel: [   16.663843]   IO window: 2000-2fff
Aug 12 04:38:01 node6 kernel: [   16.663851]   MEM window: c8000000-c9ffffff
Aug 12 04:38:01 node6 kernel: [   16.663858]   PREFETCH window: c0000000-c1ffffff
Aug 12 04:38:01 node6 kernel: [   16.663866] PCI: Bridge: 0000:00:1c.1
Aug 12 04:38:01 node6 kernel: [   16.663871]   IO window: 3000-3fff
Aug 12 04:38:01 node6 kernel: [   16.663879]   MEM window: ca000000-cbffffff
Aug 12 04:38:01 node6 kernel: [   16.663886]   PREFETCH window: c2000000-c3ffffff
Aug 12 04:38:01 node6 kernel: [   16.663894] PCI: Bridge: 0000:00:1c.2
Aug 12 04:38:01 node6 kernel: [   16.663898]   IO window: 4000-4fff
Aug 12 04:38:01 node6 kernel: [   16.663906]   MEM window: cc000000-cdffffff
Aug 12 04:38:01 node6 kernel: [   16.663913]   PREFETCH window: c4000000-c5ffffff
Aug 12 04:38:01 node6 kernel: [   16.663921] PCI: Bridge: 0000:00:1c.3
Aug 12 04:38:01 node6 kernel: [   16.663925]   IO window: 5000-5fff
Aug 12 04:38:01 node6 kernel: [   16.663934]   MEM window: ce000000-cfffffff
Aug 12 04:38:01 node6 kernel: [   16.663940]   PREFETCH window: c6000000-c7ffffff
Aug 12 04:38:01 node6 kernel: [   16.663958] PCI: Bus 11, cardbus bridge: 0000:0a:03.0
Aug 12 04:38:01 node6 kernel: [   16.663961]   IO window: 00006000-000060ff
Aug 12 04:38:01 node6 kernel: [   16.663968]   IO window: 00006400-000064ff
Aug 12 04:38:01 node6 kernel: [   16.663975]   PREFETCH window: 50000000-53ffffff
Aug 12 04:38:01 node6 kernel: [   16.663983]   MEM window: 54000000-57ffffff
Aug 12 04:38:01 node6 kernel: [   16.663989] PCI: Bridge: 0000:00:1e.0
Aug 12 04:38:01 node6 kernel: [   16.663994]   IO window: 6000-6fff
Aug 12 04:38:01 node6 kernel: [   16.664002]   MEM window: d0000000-d00fffff
Aug 12 04:38:01 node6 kernel: [   16.664009]   PREFETCH window: 50000000-53ffffff
Aug 12 04:38:01 node6 kernel: [   16.664047] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
Aug 12 04:38:01 node6 kernel: [   16.664089] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
Aug 12 04:38:01 node6 kernel: [   16.664129] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
Aug 12 04:38:01 node6 kernel: [   16.664169] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 21 (level, low) -> IRQ 19
Aug 12 04:38:01 node6 kernel: [   16.664192] PCI: Enabling device 0000:00:1e.0 (0004 -> 0007)
Aug 12 04:38:01 node6 kernel: [   16.664223] PCI: Enabling device 0000:0a:03.0 (0000 -> 0003)
Aug 12 04:38:01 node6 kernel: [   16.664229] ACPI: PCI Interrupt 0000:0a:03.0[A] -> GSI 16 (level, low) -> IRQ 17
Aug 12 04:38:01 node6 kernel: [   16.664253] NET: Registered protocol family 2
Aug 12 04:38:01 node6 kernel: [   16.708384] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 12 04:38:01 node6 kernel: [   16.708479] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Aug 12 04:38:01 node6 kernel: [   16.709492] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 12 04:38:01 node6 kernel: [   16.709856] TCP: Hash tables configured (established 131072 bind 65536)
Aug 12 04:38:01 node6 kernel: [   16.709860] TCP reno registered
Aug 12 04:38:01 node6 kernel: [   16.724543] checking if image is initramfs... it is
Aug 12 04:38:01 node6 kernel: [   17.762701] Freeing initrd memory: 6804k freed
Aug 12 04:38:01 node6 kernel: [   17.762866] Simple Boot Flag at 0x36 set to 0x1
Aug 12 04:38:01 node6 kernel: [   17.763626] audit: initializing netlink socket (disabled)
Aug 12 04:38:01 node6 kernel: [   17.763649] audit(1186915037.136:1): initialized
Aug 12 04:38:01 node6 kernel: [   17.763808] highmem bounce pool size: 64 pages
Aug 12 04:38:01 node6 kernel: [   17.766882] VFS: Disk quotas dquot_6.5.1
Aug 12 04:38:01 node6 kernel: [   17.766963] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 12 04:38:01 node6 kernel: [   17.767100] io scheduler noop registered
Aug 12 04:38:01 node6 kernel: [   17.767104] io scheduler anticipatory registered
Aug 12 04:38:01 node6 kernel: [   17.767107] io scheduler deadline registered
Aug 12 04:38:01 node6 kernel: [   17.767129] io scheduler cfq registered (default)
Aug 12 04:38:01 node6 kernel: [   17.767451] assign_interrupt_mode Found MSI capability
Aug 12 04:38:01 node6 kernel: [   17.767782] assign_interrupt_mode Found MSI capability
Aug 12 04:38:01 node6 kernel: [   17.768105] assign_interrupt_mode Found MSI capability
Aug 12 04:38:01 node6 kernel: [   17.768428] assign_interrupt_mode Found MSI capability
Aug 12 04:38:01 node6 kernel: [   17.768844] isapnp: Scanning for PnP cards...
Aug 12 04:38:01 node6 kernel: [   18.122390] isapnp: No Plug & Play device found
Aug 12 04:38:01 node6 kernel: [   18.155884] Real Time Clock Driver v1.12ac
Aug 12 04:38:01 node6 kernel: [   18.156260] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 12 04:38:01 node6 kernel: [   18.157925] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 12 04:38:01 node6 kernel: [   18.158321] input: Macintosh mouse button emulation as /class/input/input0
Aug 12 04:38:01 node6 kernel: [   18.158455] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug 12 04:38:01 node6 kernel: [   18.163607] i8042.c: Detected active multiplexing controller, rev 1.1.
Aug 12 04:38:01 node6 kernel: [   18.167678] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 12 04:38:01 node6 kernel: [   18.167685] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Aug 12 04:38:01 node6 kernel: [   18.167689] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Aug 12 04:38:01 node6 kernel: [   18.167693] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Aug 12 04:38:01 node6 kernel: [   18.167697] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Aug 12 04:38:01 node6 kernel: [   18.167974] mice: PS/2 mouse device common for all mice
Aug 12 04:38:01 node6 kernel: [   18.168431] EISA: Probing bus 0 at eisa.0
Aug 12 04:38:01 node6 kernel: [   18.168441] Cannot allocate resource for EISA slot 1
Aug 12 04:38:01 node6 kernel: [   18.168447] Cannot allocate resource for EISA slot 2
Aug 12 04:38:01 node6 kernel: [   18.168451] Cannot allocate resource for EISA slot 3
Aug 12 04:38:01 node6 kernel: [   18.168454] Cannot allocate resource for EISA slot 4
Aug 12 04:38:01 node6 kernel: [   18.168458] Cannot allocate resource for EISA slot 5
Aug 12 04:38:01 node6 kernel: [   18.168461] Cannot allocate resource for EISA slot 6
Aug 12 04:38:01 node6 kernel: [   18.168475] EISA: Detected 0 cards.
Aug 12 04:38:01 node6 kernel: [   18.168747] TCP cubic registered
Aug 12 04:38:01 node6 kernel: [   18.168769] NET: Registered protocol family 1
Aug 12 04:38:01 node6 kernel: [   18.168799] Using IPI No-Shortcut mode
Aug 12 04:38:01 node6 kernel: [   18.169070]   Magic number: 3:553:628
Aug 12 04:38:01 node6 kernel: [   18.169474] Freeing unused kernel memory: 364k freed
Aug 12 04:38:01 node6 kernel: [   18.175098] input: AT Translated Set 2 keyboard as /class/input/input1
Aug 12 04:38:01 node6 kernel: [   19.499752] AppArmor: AppArmor initialized
Aug 12 04:38:01 node6 kernel: [   19.499762] audit(1186915038.636:2): AppArmor initialized
Aug 12 04:38:01 node6 kernel: [   19.499764] 
Aug 12 04:38:01 node6 kernel: [   19.505510] AppArmor: Registered secondary security module: capability.
Aug 12 04:38:01 node6 kernel: [   19.505514] Capability LSM initialized as secondary
Aug 12 04:38:01 node6 kernel: [   19.524575] ACPI: SSDT 3F691300, 0240 (r1   Sony     VAIO 20061219 PTL  20050624)
Aug 12 04:38:01 node6 kernel: [   19.525277] ACPI: SSDT 3F690DA5, 04C9 (r1   Sony     VAIO 20061219 PTL  20050624)
Aug 12 04:38:01 node6 kernel: [   19.525933] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Aug 12 04:38:01 node6 kernel: [   19.525941] ACPI: Processor [CPU0] (supports 8 throttling states)
Aug 12 04:38:01 node6 kernel: [   19.528515] ACPI: SSDT 3F691540, 00DD (r1   Sony     VAIO 20061219 PTL  20050624)
Aug 12 04:38:01 node6 kernel: [   19.528854] ACPI: SSDT 3F69126E, 0092 (r1   Sony     VAIO 20061219 PTL  20050624)
Aug 12 04:38:01 node6 kernel: [   19.529616] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Aug 12 04:38:01 node6 kernel: [   19.529624] ACPI: Processor [CPU1] (supports 8 throttling states)
Aug 12 04:38:01 node6 kernel: [   19.531907] ACPI Exception (thermal-0400): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
Aug 12 04:38:01 node6 kernel: [   19.532801] ACPI: Thermal Zone [TZ00] (48 C)
Aug 12 04:38:01 node6 kernel: [    4.036000] Marking TSC unstable due to: possible TSC halt in C2.
Aug 12 04:38:01 node6 kernel: [    4.036000] ACPI Exception (thermal-0400): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
Aug 12 04:38:01 node6 kernel: [    4.036000] ACPI: Thermal Zone [TZ01] (48 C)
Aug 12 04:38:01 node6 kernel: [    4.040000] Time: hpet clocksource has been installed.
Aug 12 04:38:01 node6 kernel: [    4.772000] usbcore: registered new interface driver usbfs
Aug 12 04:38:01 node6 kernel: [    4.772000] usbcore: registered new interface driver hub
Aug 12 04:38:01 node6 kernel: [    4.772000] usbcore: registered new device driver usb
Aug 12 04:38:01 node6 kernel: [    4.772000] USB Universal Host Controller Interface driver v3.0
Aug 12 04:38:01 node6 kernel: [    4.772000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
Aug 12 04:38:01 node6 kernel: [    4.772000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug 12 04:38:01 node6 kernel: [    4.772000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Aug 12 04:38:01 node6 kernel: [    4.772000] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
Aug 12 04:38:01 node6 kernel: [    4.772000] usb usb1: configuration #1 chosen from 1 choice
Aug 12 04:38:01 node6 kernel: [    4.772000] hub 1-0:1.0: USB hub found
Aug 12 04:38:01 node6 kernel: [    4.772000] hub 1-0:1.0: 2 ports detected
Aug 12 04:38:01 node6 kernel: [    4.876000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 16
Aug 12 04:38:01 node6 kernel: [    4.876000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug 12 04:38:01 node6 kernel: [    4.876000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Aug 12 04:38:01 node6 kernel: [    4.876000] uhci_hcd 0000:00:1d.1: irq 16, io base 0x00001840
Aug 12 04:38:01 node6 kernel: [    4.876000] usb usb2: configuration #1 chosen from 1 choice
Aug 12 04:38:01 node6 kernel: [    4.876000] hub 2-0:1.0: USB hub found
Aug 12 04:38:01 node6 kernel: [    4.876000] hub 2-0:1.0: 2 ports detected
Aug 12 04:38:01 node6 kernel: [    4.908000] SCSI subsystem initialized
Aug 12 04:38:01 node6 kernel: [    4.980000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Aug 12 04:38:01 node6 kernel: [    4.980000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug 12 04:38:01 node6 kernel: [    4.980000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Aug 12 04:38:01 node6 kernel: [    4.980000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
Aug 12 04:38:01 node6 kernel: [    4.980000] usb usb3: configuration #1 chosen from 1 choice
Aug 12 04:38:01 node6 kernel: [    4.980000] hub 3-0:1.0: USB hub found
Aug 12 04:38:01 node6 kernel: [    4.980000] hub 3-0:1.0: 2 ports detected
Aug 12 04:38:01 node6 kernel: [    5.084000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
Aug 12 04:38:01 node6 kernel: [    5.084000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Aug 12 04:38:01 node6 kernel: [    5.084000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Aug 12 04:38:01 node6 kernel: [    5.084000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
Aug 12 04:38:01 node6 kernel: [    5.084000] usb usb4: configuration #1 chosen from 1 choice
Aug 12 04:38:01 node6 kernel: [    5.084000] hub 4-0:1.0: USB hub found
Aug 12 04:38:01 node6 kernel: [    5.084000] hub 4-0:1.0: 2 ports detected
Aug 12 04:38:01 node6 kernel: [    5.188000] PCI: Enabling device 0000:0a:03.1 (0000 -> 0002)
Aug 12 04:38:01 node6 kernel: [    5.188000] ACPI: PCI Interrupt 0000:0a:03.1[A] -> GSI 16 (level, low) -> IRQ 17
Aug 12 04:38:01 node6 kernel: [    5.188000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
Aug 12 04:38:01 node6 kernel: [    5.188000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug 12 04:38:01 node6 kernel: [    5.188000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Aug 12 04:38:01 node6 kernel: [    5.188000] ehci_hcd 0000:00:1d.7: debug port 1
Aug 12 04:38:01 node6 kernel: [    5.188000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd0444000
Aug 12 04:38:01 node6 kernel: [    5.192000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 12 04:38:01 node6 kernel: [    5.192000] usb usb5: configuration #1 chosen from 1 choice
Aug 12 04:38:01 node6 kernel: [    5.196000] hub 5-0:1.0: USB hub found
Aug 12 04:38:01 node6 kernel: [    5.196000] hub 5-0:1.0: 8 ports detected
Aug 12 04:38:01 node6 kernel: [    5.240000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[d0005000-d00057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Aug 12 04:38:01 node6 kernel: [    5.300000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Aug 12 04:38:01 node6 kernel: [    5.300000] scsi0 : ata_piix
Aug 12 04:38:01 node6 kernel: [    5.300000] scsi1 : ata_piix
Aug 12 04:38:01 node6 kernel: [    5.300000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
Aug 12 04:38:01 node6 kernel: [    5.300000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
Aug 12 04:38:01 node6 kernel: [    5.500000] Clocksource tsc unstable (delta = -377338877 ns)
Aug 12 04:38:01 node6 kernel: [    5.612000] usb 5-6: new high speed USB device using ehci_hcd and address 2
Aug 12 04:38:01 node6 kernel: [    5.620000] ata1.00: ATAPI: SONY    DVD RW AW-G540A, 1.74, max UDMA/33
Aug 12 04:38:01 node6 kernel: [    5.792000] ata1.00: configured for UDMA/33
Aug 12 04:38:01 node6 kernel: [    5.792000] scsi 0:0:0:0: CD-ROM            SONY     DVD RW AW-G540A  1.74 PQ: 0 ANSI: 5
Aug 12 04:38:01 node6 kernel: [    5.792000] ata_piix 0000:00:1f.2: MAP [ P0 P2 XX XX ]
Aug 12 04:38:01 node6 kernel: [    5.804000] usb 5-6: configuration #1 chosen from 1 choice
Aug 12 04:38:01 node6 kernel: [    5.824000] usbcore: registered new interface driver libusual
Aug 12 04:38:01 node6 kernel: [    5.832000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Aug 12 04:38:01 node6 kernel: [    5.832000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Aug 12 04:38:01 node6 kernel: [    5.836000] Initializing USB Mass Storage driver...
Aug 12 04:38:01 node6 kernel: [    5.836000] scsi2 : SCSI emulation for USB Mass Storage devices
Aug 12 04:38:01 node6 kernel: [    5.836000] usbcore: registered new interface driver usb-storage
Aug 12 04:38:01 node6 kernel: [    5.836000] USB Mass Storage support registered.
Aug 12 04:38:01 node6 kernel: [    5.952000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
Aug 12 04:38:01 node6 kernel: [    5.952000] scsi3 : ata_piix
Aug 12 04:38:01 node6 kernel: [    5.952000] scsi4 : ata_piix
Aug 12 04:38:01 node6 kernel: [    5.952000] ata3: SATA max UDMA/133 cmd 0x000118d0 ctl 0x000118c6 bmdma 0x000118b0 irq 21
Aug 12 04:38:01 node6 kernel: [    5.952000] ata4: SATA max UDMA/133 cmd 0x000118c8 ctl 0x000118c2 bmdma 0x000118b8 irq 21
Aug 12 04:38:01 node6 kernel: [    6.116000] ata3.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC74P, max UDMA/100
Aug 12 04:38:01 node6 kernel: [    6.116000] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
Aug 12 04:38:01 node6 kernel: [    6.132000] ata3.00: configured for UDMA/100
Aug 12 04:38:01 node6 kernel: [    6.288000] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
Aug 12 04:38:01 node6 kernel: [    6.308000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 12 04:38:01 node6 kernel: [    6.308000] Uniform CD-ROM driver Revision: 3.20
Aug 12 04:38:01 node6 kernel: [    6.308000] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Aug 12 04:38:01 node6 kernel: [    6.308000] sd 3:0:0:0: [sda] Write Protect is off
Aug 12 04:38:01 node6 kernel: [    6.308000] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 12 04:38:01 node6 kernel: [    6.308000] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Aug 12 04:38:01 node6 kernel: [    6.308000] sd 3:0:0:0: [sda] Write Protect is off
Aug 12 04:38:01 node6 kernel: [    6.308000] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 12 04:38:01 node6 kernel: [    6.308000]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
Aug 12 04:38:01 node6 kernel: [    6.316000] sd 3:0:0:0: Attached scsi generic sg1 type 0
Aug 12 04:38:01 node6 kernel: [    6.720000]  sda1 sda2 sda3 sda4
Aug 12 04:38:01 node6 kernel: [    6.744000] sd 3:0:0:0: [sda] Attached SCSI disk
Aug 12 04:38:01 node6 kernel: [    7.048000] Attempting manual resume
Aug 12 04:38:01 node6 kernel: [    7.096000] kjournald starting.  Commit interval 5 seconds
Aug 12 04:38:01 node6 kernel: [    7.096000] EXT3-fs: mounted filesystem with ordered data mode.
Aug 12 04:38:01 node6 kernel: [   10.844000] scsi 2:0:0:0: Direct-Access     Sony     USB   HS-CARD    4.52 PQ: 0 ANSI: 0
Aug 12 04:38:01 node6 kernel: [   10.892000] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Aug 12 04:38:01 node6 kernel: [   10.892000] sd 2:0:0:0: Attached scsi generic sg2 type 0
Aug 12 04:38:01 node6 kernel: [   15.732000] Linux agpgart interface v0.102 (c) Dave Jones
Aug 12 04:38:01 node6 kernel: [   15.744000] agpgart: Detected an Intel 945GM Chipset.
Aug 12 04:38:01 node6 kernel: [   15.744000] agpgart: Detected 7932K stolen memory.
Aug 12 04:38:01 node6 kernel: [   15.764000] agpgart: AGP aperture is 256M @ 0xb0000000
Aug 12 04:38:01 node6 kernel: [   15.812000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 12 04:38:01 node6 kernel: [   15.816000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 12 04:38:01 node6 kernel: [   16.156000] iTCO_vendor_support: vendor-support=0
Aug 12 04:38:01 node6 kernel: [   16.156000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Aug 12 04:38:01 node6 kernel: [   16.156000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Aug 12 04:38:01 node6 kernel: [   16.156000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Aug 12 04:38:01 node6 kernel: [   16.604000] Yenta: CardBus bridge found at 0000:0a:03.0 [104d:820f]
Aug 12 04:38:01 node6 kernel: [   16.604000] Yenta: Using CSCINT to route CSC interrupts to PCI
Aug 12 04:38:01 node6 kernel: [   16.604000] Yenta: Routing CardBus interrupts to PCI
Aug 12 04:38:01 node6 kernel: [   16.604000] Yenta TI: socket 0000:0a:03.0, mfunc 0x01121b22, devctl 0x64
Aug 12 04:38:01 node6 kernel: [   16.836000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
Aug 12 04:38:01 node6 kernel: [   16.836000] Socket status: 30000006
Aug 12 04:38:01 node6 kernel: [   16.836000] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
Aug 12 04:38:01 node6 kernel: [   16.836000] pcmcia: parent PCI bridge I/O window: 0x6000 - 0x6fff
Aug 12 04:38:01 node6 kernel: [   16.836000] cs: IO port probe 0x6000-0x6fff: clean.
Aug 12 04:38:01 node6 kernel: [   16.836000] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd00fffff
Aug 12 04:38:01 node6 kernel: [   16.836000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
Aug 12 04:38:01 node6 kernel: [   16.836000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
Aug 12 04:38:01 node6 kernel: [   16.836000] sky2 0000:02:00.0: v1.14 addr 0xc8000000 irq 17 Yukon-FE (0xb7) rev 1
Aug 12 04:38:01 node6 kernel: [   16.836000] sky2 eth0: addr 00:13:a9:a3:82:17
Aug 12 04:38:01 node6 kernel: [   16.836000] PCI: Enabling device 0000:0a:03.2 (0000 -> 0002)
Aug 12 04:38:01 node6 kernel: [   16.836000] ACPI: PCI Interrupt 0000:0a:03.2[B] -> GSI 17 (level, low) -> IRQ 16
Aug 12 04:38:01 node6 kernel: [   16.928000] input: PS/2 Mouse as /class/input/input2
Aug 12 04:38:01 node6 kernel: [   16.936000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Aug 12 04:38:01 node6 kernel: [   16.936000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Aug 12 04:38:01 node6 kernel: [   16.944000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
Aug 12 04:38:01 node6 kernel: [   17.000000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.1mp
Aug 12 04:38:01 node6 kernel: [   17.000000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Aug 12 04:38:01 node6 kernel: [   17.000000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Aug 12 04:38:01 node6 kernel: [   17.064000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Aug 12 04:38:01 node6 kernel: [   17.080000] sky2 eth0: enabling interface
Aug 12 04:38:01 node6 kernel: [   17.084000] sky2 eth0: ram buffer 4K
Aug 12 04:38:01 node6 kernel: [   17.412000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Aug 12 04:38:01 node6 kernel: [   17.500000] cs: IO port probe 0x100-0x3af: clean.
Aug 12 04:38:01 node6 kernel: [   17.500000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Aug 12 04:38:01 node6 kernel: [   17.500000] cs: IO port probe 0x820-0x8ff: clean.
Aug 12 04:38:01 node6 kernel: [   17.504000] cs: IO port probe 0xc00-0xcf7: clean.
Aug 12 04:38:01 node6 kernel: [   17.504000] cs: IO port probe 0xa00-0xaff: clean.
Aug 12 04:38:01 node6 kernel: [   17.612000] hda_codec: Unknown model for ALC262, trying auto-probe from BIOS...
Aug 12 04:38:01 node6 kernel: [   17.972000] fuse init (API version 7.8)
Aug 12 04:38:01 node6 kernel: [   18.068000] lp: driver loaded but no devices found
Aug 12 04:38:01 node6 kernel: [   18.208000] Adding 1494036k swap on /dev/sda3.  Priority:-1 extents:1 across:1494036k
Aug 12 04:38:01 node6 kernel: [   18.280000] NET: Registered protocol family 17
Aug 12 04:38:01 node6 kernel: [   18.764000] EXT3 FS on sda1, internal journal
Aug 12 04:38:01 node6 kernel: [   19.024000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 12 04:38:01 node6 kernel: [   39.484000] ReiserFS: sda4: found reiserfs format "3.6" with standard journal
Aug 12 04:38:01 node6 kernel: [   39.484000] ReiserFS: sda4: using ordered data mode
Aug 12 04:38:01 node6 kernel: [   39.492000] ReiserFS: sda4: journal params: device sda4, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
Aug 12 04:38:01 node6 kernel: [   39.492000] ReiserFS: sda4: checking transaction log (sda4)
Aug 12 04:38:01 node6 kernel: [   39.532000] ReiserFS: sda4: Using r5 hash to sort names
Aug 12 04:38:01 node6 kernel: [   39.592000] ReiserFS: sda2: found reiserfs format "3.6" with standard journal
Aug 12 04:38:01 node6 kernel: [   39.592000] ReiserFS: sda2: using ordered data mode
Aug 12 04:38:01 node6 kernel: [   39.604000] ReiserFS: sda2: journal params: device sda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
Aug 12 04:38:01 node6 kernel: [   39.604000] ReiserFS: sda2: checking transaction log (sda2)
Aug 12 04:38:01 node6 kernel: [   39.624000] ReiserFS: sda2: Using r5 hash to sort names
Aug 12 04:38:01 node6 kernel: [   39.832000] AppArmor: Unregistered secondary security module: capability
Aug 12 04:38:01 node6 kernel: [   44.464000] ACPI: ACPI Dock Station Driver 
Aug 12 04:38:01 node6 kernel: [   44.576000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Aug 12 04:38:01 node6 kernel: [   44.596000] ACPI: AC Adapter [ADP1] (off-line)
Aug 12 04:38:01 node6 kernel: [   44.708000] ACPI: Battery Slot [BAT0] (battery present)
Aug 12 04:38:01 node6 kernel: [   44.748000] input: Lid Switch as /class/input/input4
Aug 12 04:38:01 node6 kernel: [   44.748000] ACPI: Lid Switch [LID0]
Aug 12 04:38:01 node6 kernel: [   44.748000] input: Power Button (CM) as /class/input/input5
Aug 12 04:38:01 node6 kernel: [   44.748000] ACPI: Power Button (CM) [PWRB]
Aug 12 04:38:02 node6 kernel: [   46.652000] ppdev: user-space parallel port driver
Aug 12 04:38:03 node6 kernel: [   46.928000] audit(1186915082.708:3): REJECTING m access to /etc/passwd (cupsd(5194) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
Aug 12 04:38:03 node6 kernel: [   46.928000] audit(1186915082.708:4): REJECTING m access to /etc/group (cupsd(5194) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
Aug 12 04:38:03 node6 kernel: [   46.932000] audit(1186915082.708:5): REJECTING m access to /etc/group (cupsd(5194) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
Aug 12 04:38:03 node6 hpiod: 1.7.3 accepting connections at 2208... 
Aug 12 04:38:03 node6 kernel: [   47.628000] audit(1186915083.708:6): REJECTING m access to /etc/passwd (cupsd(5194) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
Aug 12 04:38:03 node6 kernel: [   47.628000] audit(1186915083.708:7): REJECTING m access to /etc/group (cupsd(5194) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
Aug 12 04:38:03 node6 kernel: [   47.628000] audit(1186915083.708:8): REJECTING m access to /etc/group (cupsd(5194) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
Aug 12 04:38:03 node6 kernel: [   47.660000] apm: BIOS not found.
Aug 12 04:38:03 node6 kernel: [   47.724000] sonypi: Sony Programmable I/O Controller Driver v1.26.
Aug 12 04:38:03 node6 kernel: [   47.724000] sonypi: please try the sony-laptop module instead and report failures, see also http://www.linux.it/~malattia/wiki/index.php/Sony_drivers
Aug 12 04:38:03 node6 kernel: [   47.728000] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
Aug 12 04:38:03 node6 kernel: [   47.728000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
Aug 12 04:38:03 node6 kernel: [   47.728000] sonypi: device allocated minor is 63
Aug 12 04:38:03 node6 kernel: [   47.728000] input: Sony Vaio Jogdial as /class/input/input6
Aug 12 04:38:03 node6 kernel: [   47.728000] input: Sony Vaio Keys as /class/input/input7
Aug 12 04:38:03 node6 kernel: [   47.808000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
Aug 12 04:38:04 node6 kernel: [   47.848000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 663)
Aug 12 04:38:04 node6 kernel: [   47.888000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 665)
Aug 12 04:38:04 node6 kernel: [   47.928000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
Aug 12 04:38:04 node6 kernel: [   48.056000] AppArmor: Registered secondary security module: capability.
Aug 12 04:38:04 node6 kernel: [   48.056000] Capability LSM initialized as secondary
Aug 12 04:38:04 node6 dhcdbd: Started up.
Aug 12 04:38:04 node6 kernel: [   48.256000] Bluetooth: Core ver 2.11
Aug 12 04:38:04 node6 kernel: [   48.256000] NET: Registered protocol family 31
Aug 12 04:38:04 node6 kernel: [   48.256000] Bluetooth: HCI device and connection manager initialized
Aug 12 04:38:04 node6 kernel: [   48.256000] Bluetooth: HCI socket layer initialized
Aug 12 04:38:04 node6 kernel: [   48.272000] Bluetooth: L2CAP ver 2.8
Aug 12 04:38:04 node6 kernel: [   48.272000] Bluetooth: L2CAP socket layer initialized
Aug 12 04:38:04 node6 kernel: [   48.388000] Bluetooth: RFCOMM socket layer initialized
Aug 12 04:38:04 node6 kernel: [   48.388000] Bluetooth: RFCOMM TTY layer initialized
Aug 12 04:38:04 node6 kernel: [   48.388000] Bluetooth: RFCOMM ver 1.8
Aug 12 04:38:07 node6 kernel: [   51.164000] [drm] Initialized drm 1.1.0 20060810
Aug 12 04:38:07 node6 kernel: [   51.164000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
Aug 12 04:38:07 node6 kernel: [   51.164000] [drm] Initialized i915 1.6.0 20060119 on minor 0
Aug 12 04:38:16 node6 kernel: [   60.620000] NET: Registered protocol family 10
Aug 12 04:38:16 node6 kernel: [   60.620000] lo: Disabled Privacy Extensions
Aug 12 04:38:16 node6 kernel: [   60.620000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 12 04:38:26 node6 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Aug 12 04:40:05 node6 gnome-power-manager: (tech) Suspending computer because the power button has been pressed
Aug 12 04:40:05 node6 kernel: [  169.548000] sky2 eth0: disabling interface
Aug 12 04:40:06 node6 kernel: [  170.316000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Aug 12 04:40:06 node6 kernel: [  170.528000] ACPI: PCI interrupt for device 0000:06:00.0 disabled
Aug 12 16:15:50 node6 kernel: [  173.316000] Stopping tasks ... done.
Aug 12 16:15:50 node6 kernel: [  173.328000] Suspending console(s)
Aug 12 16:15:50 node6 kernel: [  173.368000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 663)
Aug 12 16:15:50 node6 kernel: [  173.408000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 665)
Aug 12 16:15:50 node6 kernel: [  173.412000] sd 3:0:0:0: [sda] Synchronizing SCSI cache
Aug 12 16:15:50 node6 kernel: [  173.532000] sd 3:0:0:0: [sda] Stopping disk
Aug 12 16:15:50 node6 kernel: [  174.564000] ACPI: PCI interrupt for device 0000:0a:03.2 disabled
Aug 12 16:15:50 node6 kernel: [  174.596000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Aug 12 16:15:50 node6 kernel: [  174.612000] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Aug 12 16:15:50 node6 kernel: [  174.612000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Aug 12 16:15:50 node6 kernel: [  174.628000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
Aug 12 16:15:50 node6 kernel: [  174.628000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Aug 12 16:15:50 node6 kernel: [  174.628000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Aug 12 16:15:50 node6 kernel: [  174.628000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Aug 12 16:15:50 node6 kernel: [  174.636000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Aug 12 16:15:50 node6 kernel: [  175.228000] Disabling non-boot CPUs ...
Aug 12 16:15:50 node6 kernel: [  175.344000] CPU 1 is now offline
Aug 12 16:15:50 node6 kernel: [  175.344000] SMP alternatives: switching to UP code
Aug 12 16:15:50 node6 kernel: [  175.344000] CPU1 is down
Aug 12 16:15:50 node6 kernel: [  175.344000] Enabling non-boot CPUs ...
Aug 12 16:15:50 node6 kernel: [  175.356000] SMP alternatives: switching to SMP code
Aug 12 16:15:50 node6 kernel: [  175.356000] Booting processor 1/1 eip 3000
Aug 12 16:15:50 node6 kernel: [  175.364000] Initializing CPU#1
Aug 12 16:15:50 node6 kernel: [  175.444000] Calibrating delay using timer specific routine.. 3324.94 BogoMIPS (lpj=6649882)
Aug 12 16:15:50 node6 kernel: [  175.444000] monitor/mwait feature present.
Aug 12 16:15:50 node6 kernel: [  175.444000] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug 12 16:15:50 node6 kernel: [  175.444000] CPU: L2 cache: 2048K
Aug 12 16:15:50 node6 kernel: [  175.444000] CPU: Physical Processor ID: 0
Aug 12 16:15:50 node6 kernel: [  175.444000] CPU: Processor Core ID: 1
Aug 12 16:15:50 node6 kernel: [  175.444000] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
Aug 12 16:15:50 node6 kernel: [  175.444000] Switched to high resolution mode on CPU 1
Aug 12 16:15:50 node6 kernel: [  175.444000] CPU1 is up
Aug 12 16:15:50 node6 kernel: [  175.960000] ACPI Exception (evregion-0420): AE_TIME, Returned by Handler for [EmbeddedControl] [20070126]
Aug 12 16:15:50 node6 kernel: [  175.960000] ACPI Exception (dswexec-0462): AE_TIME, While resolving operands for [OpcodeName unavailable] [20070126]
Aug 12 16:15:50 node6 kernel: [  175.960000] ACPI Error (psparse-0537): Method parse/execution failed [\_WAK] (Node df938228), AE_TIME
Aug 12 16:15:50 node6 kernel: [  175.960000] ACPI Exception (hwsleep-0581): AE_TIME, During Method _WAK [20070126]
Aug 12 16:15:50 node6 kernel: [  175.992000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
Aug 12 16:15:50 node6 kernel: [  176.160000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Aug 12 16:15:50 node6 kernel: [  176.224000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
Aug 12 16:15:50 node6 kernel: [  176.224000] usb usb1: root hub lost power or was reset
Aug 12 16:15:50 node6 kernel: [  176.224000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 16
Aug 12 16:15:50 node6 kernel: [  176.224000] usb usb2: root hub lost power or was reset
Aug 12 16:15:50 node6 kernel: [  176.224000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Aug 12 16:15:50 node6 kernel: [  176.224000] usb usb3: root hub lost power or was reset
Aug 12 16:15:50 node6 kernel: [  176.224000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
Aug 12 16:15:50 node6 kernel: [  176.224000] usb usb4: root hub lost power or was reset
Aug 12 16:15:50 node6 kernel: [  176.240000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
Aug 12 16:15:50 node6 kernel: [  176.240000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Aug 12 16:15:50 node6 kernel: [  176.256000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
Aug 12 16:15:50 node6 kernel: [  176.320000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[d0005000-d00057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Aug 12 16:15:50 node6 kernel: [  176.336000] ACPI: PCI Interrupt 0000:0a:03.2[B] -> GSI 17 (level, low) -> IRQ 16
Aug 12 16:15:50 node6 kernel: [  176.732000] ata1.00: configured for UDMA/33
Aug 12 16:15:50 node6 kernel: [  176.864000] sd 3:0:0:0: [sda] Starting disk
Aug 12 16:15:50 node6 kernel: [  177.900000] ata3.00: configured for UDMA/100
Aug 12 16:15:50 node6 kernel: [  177.916000] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Aug 12 16:15:50 node6 kernel: [  177.916000] sd 3:0:0:0: [sda] Write Protect is off
Aug 12 16:15:50 node6 kernel: [  177.916000] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 12 16:15:50 node6 kernel: [  177.964000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
Aug 12 16:15:50 node6 kernel: [  178.004000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 663)
Aug 12 16:15:50 node6 kernel: [  178.044000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 665)
Aug 12 16:15:50 node6 kernel: [  178.080000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
Aug 12 16:15:50 node6 kernel: [  178.084000] Restarting tasks ... <6>usb 5-6: USB disconnect, address 2
Aug 12 16:15:50 node6 kernel: [  178.084000] done.
Aug 12 16:15:50 node6 gnome-power-manager: (tech) Resuming computer
Aug 12 16:15:50 node6 gnome-power-manager: (tech) suspend failed
Aug 12 16:15:50 node6 kernel: [  178.196000] usb 5-6: new high speed USB device using ehci_hcd and address 3
Aug 12 16:15:50 node6 kernel: [  178.388000] usb 5-6: configuration #1 chosen from 1 choice
Aug 12 16:15:50 node6 kernel: [  178.392000] scsi5 : SCSI emulation for USB Mass Storage devices
Aug 12 16:15:50 node6 kernel: [  178.600000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
Aug 12 16:15:50 node6 kernel: [  178.600000] sky2 0000:02:00.0: v1.14 addr 0xc8000000 irq 17 Yukon-FE (0xb7) rev 1
Aug 12 16:15:50 node6 kernel: [  178.604000] sky2 eth0: addr 00:13:a9:a3:82:17
Aug 12 16:15:50 node6 kernel: [  178.616000] sky2 eth0: enabling interface
Aug 12 16:15:50 node6 kernel: [  178.616000] sky2 eth0: ram buffer 4K
Aug 12 16:15:50 node6 kernel: [  178.620000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 12 16:15:50 node6 kernel: [  178.632000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Aug 12 16:15:50 node6 kernel: [  178.632000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Aug 12 16:15:50 node6 kernel: [  178.648000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.1mp
Aug 12 16:15:50 node6 kernel: [  178.648000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Aug 12 16:15:50 node6 kernel: [  178.652000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Aug 12 16:15:50 node6 kernel: [  178.652000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Aug 12 16:15:51 node6 kernel: [  179.488000] input: Lid Switch as /class/input/input8
Aug 12 16:15:51 node6 kernel: [  179.488000] ACPI: Lid Switch [LID0]
Aug 12 16:15:51 node6 kernel: [  179.520000] input: Power Button (CM) as /class/input/input9
Aug 12 16:15:51 node6 kernel: [  179.520000] ACPI: Power Button (CM) [PWRB]
Aug 12 16:15:51 node6 kernel: [  179.588000] ACPI Exception (thermal-0400): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
Aug 12 16:15:51 node6 kernel: [  179.592000] ACPI: Thermal Zone [TZ00] (36 C)
Aug 12 16:15:51 node6 kernel: [  179.592000] ACPI Exception (thermal-0400): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
Aug 12 16:15:51 node6 kernel: [  179.592000] ACPI: Thermal Zone [TZ01] (36 C)
Aug 12 16:15:51 node6 kernel: [  179.648000] ACPI: AC Adapter [ADP1] (off-line)
Aug 12 16:15:51 node6 kernel: [  179.692000] ACPI: Battery Slot [BAT0] (battery present)
Aug 12 16:15:52 node6 kernel: [  180.452000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 12 16:15:52 node6 kernel: [  180.716000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Aug 12 16:15:54 node6 kernel: [  182.308000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Aug 12 16:15:55 node6 kernel: [  183.400000] scsi 5:0:0:0: Direct-Access     Sony     USB   HS-CARD    4.52 PQ: 0 ANSI: 0
Aug 12 16:15:55 node6 kernel: [  183.452000] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Aug 12 16:15:55 node6 kernel: [  183.452000] sd 5:0:0:0: Attached scsi generic sg2 type 0
Aug 12 16:16:02 node6 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Aug 12 16:16:16 node6 kernel: [  204.252000] ACPI Error (dswload-0774): [MULV] Namespace lookup failure, AE_ALREADY_EXISTS
Aug 12 16:16:16 node6 kernel: [  204.252000] ACPI Exception (psloop-0225): AE_ALREADY_EXISTS, During name lookup/catalog [20070126]
Aug 12 16:16:16 node6 kernel: [  204.252000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.BAT0._BIF] (Node df9388e8), AE_ALREADY_EXISTS
Aug 12 16:16:16 node6 kernel: [  204.252000] ACPI: Marking method _BIF as Serialized
Aug 12 16:16:16 node6 kernel: [  204.252000] ACPI Exception (battery-0147): AE_ALREADY_EXISTS, Evaluating _BIF [20070126]
Aug 12 16:16:16 node6 kernel: [  204.252000] ACPI Error (psargs-0355): [MULV] Namespace lookup failure, AE_NOT_FOUND
Aug 12 16:16:16 node6 kernel: [  204.252000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.BAT0._BIF] (Node df9388e8), AE_NOT_FOUND
Aug 12 16:16:16 node6 kernel: [  204.252000] ACPI Exception (battery-0147): AE_NOT_FOUND, Evaluating _BIF [20070126]
Aug 12 16:16:16 node6 kernel: [  204.260000] ACPI Error (dswload-0774): [PKG0] Namespace lookup failure, AE_ALREADY_EXISTS
Aug 12 16:16:16 node6 kernel: [  204.260000] ACPI Exception (psloop-0225): AE_ALREADY_EXISTS, During name lookup/catalog [20070126]
Aug 12 16:16:16 node6 kernel: [  204.260000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.BAT0._BST] (Node df938900), AE_ALREADY_EXISTS
Aug 12 16:16:16 node6 kernel: [  204.260000] ACPI: Marking method _BST as Serialized
Aug 12 16:16:16 node6 kernel: [  204.260000] ACPI Exception (battery-0206): AE_ALREADY_EXISTS, Evaluating _BST [20070126]
Aug 12 16:16:16 node6 kernel: [  204.260000] ACPI Error (psargs-0355): [PKG0] Namespace lookup failure, AE_NOT_FOUND
Aug 12 16:16:16 node6 kernel: [  204.260000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.BAT0._BST] (Node df938900), AE_NOT_FOUND
Aug 12 16:16:16 node6 kernel: [  204.260000] ACPI Exception (battery-0206): AE_NOT_FOUND, Evaluating _BST [20070126]
Aug 12 16:18:04 node6 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Aug 12 16:18:05 node6 kernel: [  313.888000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Aug 12 16:18:46 node6 dhcdbd: dhco_input_option: Value -1 cannot be converted to type L 
Aug 12 16:18:46 node6 dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_lease_time = -1 
Aug 12 16:18:55 node6 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Aug 12 16:18:55 node6 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
Aug 12 16:18:55 node6 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Aug 12 16:18:55 node6 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Aug 12 16:19:50 node6 kernel: [  418.944000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Aug 12 16:21:49 node6 gnome-power-manager: (tech) Suspending computer because the power button has been pressed
Aug 12 16:21:49 node6 kernel: [  537.512000] ACPI Error (evevent-0305): No installed handler for fixed event [00000002] [20070126]
Aug 12 16:21:49 node6 kernel: [  537.632000] sky2 eth0: disabling interface
Aug 12 16:21:51 node6 kernel: [  539.988000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Aug 12 16:21:52 node6 kernel: [  540.568000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Aug 12 16:21:52 node6 kernel: [  540.788000] ACPI: PCI interrupt for device 0000:06:00.0 disabled
Aug 12 16:32:40 node6 kernel: [  543.584000] Stopping tasks ... done.
Aug 12 16:32:40 node6 kernel: [  543.592000] Suspending console(s)
Aug 12 16:32:40 node6 kernel: [  543.644000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 663)
Aug 12 16:32:40 node6 kernel: [  543.684000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 665)
Aug 12 16:32:40 node6 kernel: [  543.688000] sd 3:0:0:0: [sda] Synchronizing SCSI cache
Aug 12 16:32:40 node6 kernel: [  543.792000] sd 3:0:0:0: [sda] Stopping disk
Aug 12 16:32:40 node6 kernel: [  544.808000] ACPI: PCI interrupt for device 0000:0a:03.2 disabled
Aug 12 16:32:40 node6 kernel: [  544.840000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Aug 12 16:32:40 node6 kernel: [  544.856000] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Aug 12 16:32:40 node6 kernel: [  544.856000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Aug 12 16:32:40 node6 kernel: [  544.872000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
Aug 12 16:32:40 node6 kernel: [  544.872000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Aug 12 16:32:40 node6 kernel: [  544.872000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Aug 12 16:32:40 node6 kernel: [  544.872000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Aug 12 16:32:40 node6 kernel: [  544.880000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Aug 12 16:32:40 node6 kernel: [  545.472000] Disabling non-boot CPUs ...
Aug 12 16:32:40 node6 kernel: [  545.588000] CPU 1 is now offline
Aug 12 16:32:40 node6 kernel: [  545.588000] SMP alternatives: switching to UP code
Aug 12 16:32:40 node6 kernel: [  545.588000] CPU1 is down
Aug 12 16:32:40 node6 kernel: [  545.588000] Enabling non-boot CPUs ...
Aug 12 16:32:40 node6 kernel: [  545.600000] SMP alternatives: switching to SMP code
Aug 12 16:32:40 node6 kernel: [  545.600000] Booting processor 1/1 eip 3000
Aug 12 16:32:40 node6 kernel: [  545.608000] Initializing CPU#1
Aug 12 16:32:40 node6 kernel: [  545.688000] Calibrating delay using timer specific routine.. 3326.57 BogoMIPS (lpj=6653158)
Aug 12 16:32:40 node6 kernel: [  545.688000] monitor/mwait feature present.
Aug 12 16:32:40 node6 kernel: [  545.688000] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug 12 16:32:40 node6 kernel: [  545.688000] CPU: L2 cache: 2048K
Aug 12 16:32:40 node6 kernel: [  545.688000] CPU: Physical Processor ID: 0
Aug 12 16:32:40 node6 kernel: [  545.688000] CPU: Processor Core ID: 1
Aug 12 16:32:40 node6 kernel: [  545.688000] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
Aug 12 16:32:40 node6 kernel: [  545.688000] Switched to high resolution mode on CPU 1
Aug 12 16:32:40 node6 kernel: [  545.688000] CPU1 is up
Aug 12 16:32:40 node6 kernel: [  546.060000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
Aug 12 16:32:40 node6 kernel: [  546.076000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Aug 12 16:32:40 node6 kernel: [  546.140000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
Aug 12 16:32:40 node6 kernel: [  546.140000] usb usb1: root hub lost power or was reset
Aug 12 16:32:40 node6 kernel: [  546.140000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 16
Aug 12 16:32:40 node6 kernel: [  546.140000] usb usb2: root hub lost power or was reset
Aug 12 16:32:40 node6 kernel: [  546.140000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Aug 12 16:32:40 node6 kernel: [  546.140000] usb usb3: root hub lost power or was reset
Aug 12 16:32:40 node6 kernel: [  546.140000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
Aug 12 16:32:40 node6 kernel: [  546.140000] usb usb4: root hub lost power or was reset
Aug 12 16:32:40 node6 kernel: [  546.156000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
Aug 12 16:32:40 node6 kernel: [  546.156000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Aug 12 16:32:40 node6 kernel: [  546.172000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
Aug 12 16:32:40 node6 kernel: [  546.236000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[d0005000-d00057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Aug 12 16:32:40 node6 kernel: [  546.252000] ACPI: PCI Interrupt 0000:0a:03.2[B] -> GSI 17 (level, low) -> IRQ 16
Aug 12 16:32:40 node6 kernel: [  546.784000] sd 3:0:0:0: [sda] Starting disk
Aug 12 16:32:40 node6 kernel: [  546.972000] ata1.00: configured for UDMA/33
Aug 12 16:32:40 node6 kernel: [  548.268000] ata3.00: configured for UDMA/100
Aug 12 16:32:40 node6 kernel: [  548.284000] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Aug 12 16:32:40 node6 kernel: [  548.284000] sd 3:0:0:0: [sda] Write Protect is off
Aug 12 16:32:40 node6 kernel: [  548.284000] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 12 16:32:40 node6 kernel: [  548.328000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
Aug 12 16:32:40 node6 kernel: [  548.368000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 663)
Aug 12 16:32:40 node6 kernel: [  548.408000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 665)
Aug 12 16:32:40 node6 kernel: [  548.448000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
Aug 12 16:32:40 node6 kernel: [  548.448000] Restarting tasks ... <6>usb 5-6: USB disconnect, address 3
Aug 12 16:32:40 node6 kernel: [  548.448000] done.
Aug 12 16:32:40 node6 kernel: [  548.560000] usb 5-6: new high speed USB device using ehci_hcd and address 4
Aug 12 16:32:40 node6 gnome-power-manager: (tech) Resuming computer
Aug 12 16:32:40 node6 gnome-power-manager: (tech) suspend failed
Aug 12 16:32:40 node6 kernel: [  548.764000] usb 5-6: configuration #1 chosen from 1 choice
Aug 12 16:32:40 node6 kernel: [  548.768000] scsi6 : SCSI emulation for USB Mass Storage devices
Aug 12 16:32:40 node6 kernel: [  548.900000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
Aug 12 16:32:40 node6 kernel: [  548.900000] sky2 0000:02:00.0: v1.14 addr 0xc8000000 irq 17 Yukon-FE (0xb7) rev 1
Aug 12 16:32:40 node6 kernel: [  548.900000] sky2 eth0: addr 00:13:a9:a3:82:17
Aug 12 16:32:40 node6 kernel: [  548.924000] sky2 eth0: enabling interface
Aug 12 16:32:40 node6 kernel: [  548.928000] sky2 eth0: ram buffer 4K
Aug 12 16:32:40 node6 kernel: [  548.928000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 12 16:32:40 node6 kernel: [  548.948000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Aug 12 16:32:40 node6 kernel: [  548.948000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Aug 12 16:32:40 node6 kernel: [  548.964000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.1mp
Aug 12 16:32:40 node6 kernel: [  548.964000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Aug 12 16:32:40 node6 kernel: [  548.964000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Aug 12 16:32:40 node6 kernel: [  548.964000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Aug 12 16:32:41 node6 kernel: [  549.656000] input: Lid Switch as /class/input/input10
Aug 12 16:32:41 node6 kernel: [  549.656000] ACPI: Lid Switch [LID0]
Aug 12 16:32:41 node6 kernel: [  549.688000] input: Power Button (CM) as /class/input/input11
Aug 12 16:32:41 node6 kernel: [  549.704000] ACPI: Power Button (CM) [PWRB]
Aug 12 16:32:41 node6 kernel: [  549.824000] ACPI Exception (thermal-0400): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
Aug 12 16:32:41 node6 kernel: [  549.840000] ACPI: Thermal Zone [TZ00] (40 C)
Aug 12 16:32:41 node6 kernel: [  549.852000] ACPI Exception (thermal-0400): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
Aug 12 16:32:41 node6 kernel: [  549.856000] ACPI: Thermal Zone [TZ01] (40 C)
Aug 12 16:32:41 node6 kernel: [  549.916000] ACPI: AC Adapter [ADP1] (off-line)
Aug 12 16:32:41 node6 kernel: [  549.976000] ACPI: Battery Slot [BAT0] (battery present)
Aug 12 16:32:42 node6 kernel: [  550.780000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
Aug 12 16:32:42 node6 kernel: [  551.072000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Aug 12 16:32:44 node6 kernel: [  552.684000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Aug 12 16:32:45 node6 kernel: [  553.776000] scsi 6:0:0:0: Direct-Access     Sony     USB   HS-CARD    4.52 PQ: 0 ANSI: 0
Aug 12 16:32:45 node6 kernel: [  553.824000] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Aug 12 16:32:45 node6 kernel: [  553.824000] sd 6:0:0:0: Attached scsi generic sg2 type 0

```

Thanks in advance!
-thelanlegend

---

