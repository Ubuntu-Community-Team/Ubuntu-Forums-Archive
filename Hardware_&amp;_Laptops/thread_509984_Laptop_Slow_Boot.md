---
title: "Laptop Slow Boot"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by OOzypal on 2007-07-26
My lap top takes time when reboot. It is Toshiba Satellite A100-294. It is fairly new, Centrino Duo. How can I troubleshoot to see what program is slowing it. It is actually slow after I see the Splash screen.

here is dmesg and ps -ef

```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007f570000 end: 000000007f670000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007f670000 size: 0000000000090000 end: 000000007f700000 type: 4
[    0.000000] copy_e820_map() start: 000000007f700000 size: 0000000000900000 end: 0000000080000000 type: 2
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f670000 (usable)
[    0.000000]  BIOS-e820: 000000007f670000 - 000000007f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f700000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f65c0
[    0.000000] Entering add_active_range(0, 0, 521840) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   521840
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   521840
[    0.000000] On node 0 totalpages: 521840
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2284 pages used for memmap
[    0.000000]   HighMem zone: 290180 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 TOSINV                                ) @ 0x000f6510
[    0.000000] ACPI: RSDT (v001 TOSINV Capell00 0x06040000  LTP 0x00000000) @ 0x7f67e23a
[    0.000000] ACPI: FADT (v001 TOSINV CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x7f685dee
[    0.000000] ACPI: MADT (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x7f685e62
[    0.000000] ACPI: HPET (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x7f685eca
[    0.000000] ACPI: MCFG (v001 INTEL  CALISTGA 0x06040000 LOHR 0x0000005a) @ 0x7f685f02
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x7f685fd8
[    0.000000] ACPI: MADT (v001 TOSINV   APIC   0x06040000  LTP 0x00000000) @ 0x7f685f70
[    0.000000] ACPI: SSDT (v001 SataRe  SataPri 0x00001000 INTL 0x20050624) @ 0x7f67f29c
[    0.000000] ACPI: SSDT (v001 SataRe  SataSec 0x00001000 INTL 0x20050624) @ 0x7f67ec0a
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x7f67e282
[    0.000000] ACPI: DSDT (v001 TOSINV CALISTGA 0x06040000 INTL 0x20050624) @ 0x00000000
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
[    0.000000] Detected 1828.806 MHz processor.
[   23.027222] Built 1 zonelists.  Total pages: 517764
[   23.027226] Kernel command line: root=UUID=255d4a2f-3c8a-4f56-877a-1d6057c9601f ro quiet splash
[   23.027373] mapped APIC to ffffd000 (fee00000)
[   23.027375] mapped IOAPIC to ffffc000 (fec00000)
[   23.027378] Enabling fast FPU save and restore... done.
[   23.027380] Enabling unmasked SIMD FPU exception support... done.
[   23.027387] Initializing CPU#0
[   23.027461] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   23.029047] Console: colour VGA+ 80x25
[   23.029295] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   23.029632] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.124772] Memory: 2058468k/2087360k available (1992k kernel code, 27664k reserved, 900k data, 328k init, 1169856k highmem)
[   23.124782] virtual kernel memory layout:
[   23.124783]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   23.124784]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.124785]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   23.124787]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   23.124788]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   23.124789]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   23.124790]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   23.124793] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.124962] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   23.124967] hpet0: 3 64-bit timers, 14318180 Hz
[   23.125972] Using HPET for base-timer
[   23.204831] Calibrating delay using timer specific routine.. 3661.77 BogoMIPS (lpj=7323541)
[   23.204869] Security Framework v1.0.0 initialized
[   23.204878] SELinux:  Disabled at boot.
[   23.204893] Mount-cache hash table entries: 512
[   23.205023] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c1a9 00000000 00000000
[   23.205030] monitor/mwait feature present.
[   23.205032] using mwait in idle threads.
[   23.205037] CPU: L1 I cache: 32K, L1 D cache: 32K
[   23.205040] CPU: L2 cache: 2048K
[   23.205042] CPU: Physical Processor ID: 0
[   23.205044] CPU: Processor Core ID: 0
[   23.205046] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00002940 0000c1a9 00000000 00000000
[   23.205055] Compat vDSO mapped to ffffe000.
[   23.205059] Remapping vsyscall page to ffffe000
[   23.205070] Checking 'hlt' instruction... OK.
[   23.220913] SMP alternatives: switching to UP code
[   23.221272] Early unpacking initramfs... done
[   23.532120] ACPI: Core revision 20060707
[   23.532340] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   23.600921] CPU0: Intel Genuine Intel(R) CPU           T2400  @ 1.83GHz stepping 08
[   23.600941] SMP alternatives: switching to SMP code
[   23.601052] Booting processor 1/1 eip 3000
[   23.611452] Initializing CPU#1
[   23.692007] Calibrating delay using timer specific routine.. 3657.62 BogoMIPS (lpj=7315257)
[   23.692013] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c1a9 00000000 00000000
[   23.692018] monitor/mwait feature present.
[   23.692022] CPU: L1 I cache: 32K, L1 D cache: 32K
[   23.692023] CPU: L2 cache: 2048K
[   23.692026] CPU: Physical Processor ID: 0
[   23.692027] CPU: Processor Core ID: 1
[   23.692029] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00002940 0000c1a9 00000000 00000000
[   23.692484] CPU1: Intel Genuine Intel(R) CPU           T2400  @ 1.83GHz stepping 08
[   23.692507] Total of 2 processors activated (7319.39 BogoMIPS).
[   23.692709] ENABLING IO-APIC IRQs
[   23.692917] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   23.839756] checking TSC synchronization across 2 CPUs: passed.
[    0.003996] Brought up 2 CPUs
[    0.128578] migration_cost=49
[    0.128845] Booting paravirtualized kernel on bare hardware
[    0.128944] Time:  5:56:07  Date: 06/26/107
[    0.128973] NET: Registered protocol family 16
[    0.129053] EISA bus registered
[    0.129057] ACPI: bus type pci registered
[    0.129179] PCI: PCI BIOS revision 2.10 entry at 0xfd875, last bus=7
[    0.129181] PCI: Using configuration type 1
[    0.129183] Setting up standard PCI resources
[    0.139674] ACPI: Interpreter enabled
[    0.139677] ACPI: Using IOAPIC for interrupt routing
[    0.140351] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.140355] PCI: Probing PCI hardware (bus 00)
[    0.141227] Boot video device is 0000:00:02.0
[    0.141866] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.141870] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.142886] PCI: Firmware left 0000:07:08.0 e100 interrupts enabled, disabling
[    0.142973] PCI: Transparent bridge - 0000:00:1e.0
[    0.143043] PCI: Bus #08 (-#0b) is hidden behind transparent bridge #07 (-#07) (try 'pci=assign-busses')
[    0.143046] Please report the result to linux-kernel to fix this permanently
[    0.143112] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.304349] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.304598] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.304844] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.305935] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.335846] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.336085] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.336321] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.336561] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.336798] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.337033] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.337270] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.337507] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.399606] ACPI: Power Resource [FN00] (off)
[    0.399742] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.399750] pnp: PnP ACPI init
[    0.495335] pnp: PnP ACPI: found 10 devices
[    0.495339] PnPBIOS: Disabled by ACPI PNP
[    0.495377] PCI: Using ACPI for IRQ routing
[    0.495379] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.525802] NET: Registered protocol family 8
[    0.525804] NET: Registered protocol family 20
[    0.526239] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    0.526244] PCI: Bridge: 0000:00:1c.0
[    0.526245]   IO window: disabled.
[    0.526251]   MEM window: disabled.
[    0.526255]   PREFETCH window: disabled.
[    0.526261] PCI: Bridge: 0000:00:1c.1
[    0.526264]   IO window: 2000-2fff
[    0.526270]   MEM window: d8000000-d9ffffff
[    0.526275]   PREFETCH window: d2000000-d3ffffff
[    0.526281] PCI: Bridge: 0000:00:1c.2
[    0.526284]   IO window: 3000-3fff
[    0.526290]   MEM window: da000000-dbffffff
[    0.526295]   PREFETCH window: d4000000-d5ffffff
[    0.526307] PCI: Bus 8, cardbus bridge: 0000:07:06.0
[    0.526309]   IO window: 00004400-000044ff
[    0.526314]   IO window: 00004800-000048ff
[    0.526319]   PREFETCH window: 88000000-8bffffff
[    0.526324]   MEM window: 8c000000-8fffffff
[    0.526329] PCI: Bridge: 0000:00:1e.0
[    0.526332]   IO window: 4000-4fff
[    0.526338]   MEM window: dc000000-dc0fffff
[    0.526343]   PREFETCH window: 88000000-8bffffff
[    0.526372] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[    0.526379] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.526402] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[    0.526408] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.526432] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    0.526438] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.526452] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.526469] PCI: Enabling device 0000:07:06.0 (0000 -> 0003)
[    0.526472] ACPI: PCI Interrupt 0000:07:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[    0.526502] NET: Registered protocol family 2
[    0.571070] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.571163] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.571841] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.572190] TCP: Hash tables configured (established 131072 bind 65536)
[    0.572192] TCP reno registered
[    0.587121] checking if image is initramfs... it is
[    1.194505] Freeing initrd memory: 6791k freed
[    1.194676] Simple Boot Flag at 0x36 set to 0x1
[    1.195113] audit: initializing netlink socket (disabled)
[    1.195130] audit(1185429367.928:1): initialized
[    1.195218] highmem bounce pool size: 64 pages
[    1.195300] VFS: Disk quotas dquot_6.5.1
[    1.195319] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.195363] io scheduler noop registered
[    1.195366] io scheduler anticipatory registered
[    1.195368] io scheduler deadline registered
[    1.195379] io scheduler cfq registered (default)
[    1.195614] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    1.195672] assign_interrupt_mode Found MSI capability
[    1.195675] Allocate Port Service[0000:00:1c.0:pcie00]
[    1.195708] Allocate Port Service[0000:00:1c.0:pcie02]
[    1.195832] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    1.195890] assign_interrupt_mode Found MSI capability
[    1.195892] Allocate Port Service[0000:00:1c.1:pcie00]
[    1.195924] Allocate Port Service[0000:00:1c.1:pcie02]
[    1.196042] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    1.196100] assign_interrupt_mode Found MSI capability
[    1.196102] Allocate Port Service[0000:00:1c.2:pcie00]
[    1.196132] Allocate Port Service[0000:00:1c.2:pcie02]
[    1.196305] isapnp: Scanning for PnP cards...
[    1.549462] isapnp: No Plug & Play device found
[    1.571576] Real Time Clock Driver v1.12ac
[    1.571636] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.572231] mice: PS/2 mouse device common for all mice
[    1.572750] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.572885] input: Macintosh mouse button emulation as /class/input/input0
[    1.572920] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.572924] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.573212] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.575759] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.577420] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.577424] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.577427] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.577429] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.577432] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.577519] EISA: Probing bus 0 at eisa.0
[    1.577526] Cannot allocate resource for EISA slot 1
[    1.577529] Cannot allocate resource for EISA slot 2
[    1.577532] Cannot allocate resource for EISA slot 3
[    1.577534] Cannot allocate resource for EISA slot 4
[    1.577551] EISA: Detected 0 cards.
[    1.607600] TCP cubic registered
[    1.607609] NET: Registered protocol family 1
[    1.607630] Starting balanced_irq
[    1.607635] Using IPI No-Shortcut mode
[    1.607733] ACPI: (supports S0 S3 S4 S5)
[    1.607779]   Magic number: 15:378:922
[    1.608046] Freeing unused kernel memory: 328k freed
[    1.609285] Time: tsc clocksource has been installed.
[    1.610888] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.808871] Capability LSM initialized
[    2.837872] ACPI: Transitioning device [FAN0] to D3
[    2.837875] ACPI: Transitioning device [FAN0] to D3
[    2.837878] ACPI: Fan [FAN0] (off)
[    2.841304] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    2.841514] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    2.841776] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.841780] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.842255] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    2.842448] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    2.842750] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    2.842755] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.843532] ACPI: Thermal Zone [TZ00] (40 C)
[    2.844215] ACPI: Invalid passive threshold
[    2.849162] ACPI: Transitioning device [FAN0] to D0
[    2.849164] ACPI: Transitioning device [FAN0] to D0
[    2.849166] ACPI: Unable to turn cooling device [df8173b0] 'on'
[    2.849169] ACPI: Thermal Zone [TZ01] (37 C)
[    3.420000] Time: hpet clocksource has been installed.
[    3.728000] usbcore: registered new interface driver usbfs
[    3.728000] usbcore: registered new interface driver hub
[    3.728000] usbcore: registered new device driver usb
[    3.732000] USB Universal Host Controller Interface driver v3.0
[    3.732000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    3.732000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.732000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.732000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.732000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[    3.732000] usb usb1: configuration #1 chosen from 1 choice
[    3.732000] hub 1-0:1.0: USB hub found
[    3.732000] hub 1-0:1.0: 2 ports detected
[    3.764000] ieee1394: Initialized config rom entry `ip1394'
[    3.812000] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[    3.812000] e100: Copyright(c) 1999-2006 Intel Corporation
[    3.840000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[    3.840000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.840000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.840000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.840000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[    3.840000] usb usb2: configuration #1 chosen from 1 choice
[    3.840000] hub 2-0:1.0: USB hub found
[    3.840000] hub 2-0:1.0: 2 ports detected
[    3.944000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.944000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.944000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.944000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.944000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    3.944000] usb usb3: configuration #1 chosen from 1 choice
[    3.944000] hub 3-0:1.0: USB hub found
[    3.944000] hub 3-0:1.0: 2 ports detected
[    4.048000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[    4.048000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    4.048000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.048000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    4.048000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[    4.048000] usb usb4: configuration #1 chosen from 1 choice
[    4.048000] hub 4-0:1.0: USB hub found
[    4.048000] hub 4-0:1.0: 2 ports detected
[    4.152000] ACPI: PCI Interrupt 0000:07:06.1[B] -> GSI 17 (level, low) -> IRQ 16
[    4.204000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    4.204000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[dc006000-dc0067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.208000] ACPI: PCI Interrupt 0000:07:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[    4.236000] e100: eth0: e100_probe: addr 0xdc005000, irq 21, MAC addr 00:A0:D1:4B:BC:23
[    4.236000] SCSI subsystem initialized
[    4.240000] libata version 2.20 loaded.
[    4.240000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    4.240000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.240000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.240000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.240000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.240000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.240000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xdc444000
[    4.244000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.244000] usb usb5: configuration #1 chosen from 1 choice
[    4.244000] hub 5-0:1.0: USB hub found
[    4.244000] hub 5-0:1.0: 8 ports detected
[    4.348000] ata_piix 0000:00:1f.2: version 2.10ac1
[    4.348000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.508000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    4.508000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.508000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[    4.508000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
[    4.508000] scsi0 : ata_piix
[    4.660000] usb 5-3: new high speed USB device using ehci_hcd and address 2
[    4.672000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.672000] ata1.00: ATA-7: HTS541080G9SA00, MB4OC60R, max UDMA/100
[    4.672000] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.680000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.680000] ata1.00: configured for UDMA/100
[    4.680000] scsi1 : ata_piix
[    4.792000] usb 5-3: configuration #1 chosen from 1 choice
[    5.004000] ata2.00: ATAPI, max UDMA/33
[    5.168000] ata2.00: configured for UDMA/33
[    5.168000] scsi 0:0:0:0: Direct-Access     ATA      HTS541080G9SA00  MB4O PQ: 0 ANSI: 5
[    5.168000] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-841S  1.60 PQ: 0 ANSI: 5
[    5.188000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    5.188000] sda: Write Protect is off
[    5.188000] sda: Mode Sense: 00 3a 00 00
[    5.188000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.188000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    5.188000] sda: Write Protect is off
[    5.188000] sda: Mode Sense: 00 3a 00 00
[    5.188000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.188000]  sda: sda1 sda2 < sda5 > sda4
[    5.224000] sd 0:0:0:0: Attached scsi disk sda
[    5.224000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.224000] Uniform CD-ROM driver Revision: 3.20
[    5.224000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.228000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.228000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    5.296000] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    5.396000] Attempting manual resume
[    5.396000] swsusp: Resume From Partition 8:5
[    5.396000] PM: Checking swsusp image.
[    5.396000] PM: Resume from disk failed.
[    5.440000] kjournald starting.  Commit interval 5 seconds
[    5.440000] EXT3-fs: mounted filesystem with writeback data mode.
[    5.468000] usb 3-1: configuration #1 chosen from 1 choice
[    5.472000] usbcore: registered new interface driver libusual
[    5.476000] Initializing USB Mass Storage driver...
[    5.476000] scsi2 : SCSI emulation for USB Mass Storage devices
[    5.476000] usbcore: registered new interface driver usb-storage
[    5.476000] USB Mass Storage support registered.
[    5.476000] usb-storage: device found at 2
[    5.476000] usb-storage: waiting for device to settle before scanning
[   10.480000] usb-storage: device scan complete
[   10.480000] scsi 2:0:0:0: Direct-Access     TOSHIBA  MK8032GAX        0811 PQ: 0 ANSI: 0
[   10.480000] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
[   10.480000] sdb: test WP failed, assume Write Enabled
[   10.480000] sdb: assuming drive cache: write through
[   10.484000] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
[   10.484000] sdb: test WP failed, assume Write Enabled
[   10.484000] sdb: assuming drive cache: write through
[   10.484000]  sdb: sdb1
[   10.932000] sd 2:0:0:0: Attached scsi disk sdb
[   10.932000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   17.352000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   17.668000] NET: Registered protocol family 10
[   17.668000] lo: Disabled Privacy Extensions
[   18.168000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.176000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.228000] iTCO_vendor_support: vendor-support=0
[   18.232000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   18.232000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   18.232000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.268000] intel_rng: FWH not detected
[   18.312000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.320000] agpgart: Detected an Intel 945GM Chipset.
[   18.320000] agpgart: Detected 7932K stolen memory.
[   18.336000] agpgart: AGP aperture is 256M @ 0xc0000000
[   18.576000] sdhci: Secure Digital Host Controller Interface driver
[   18.576000] sdhci: Copyright(c) Pierre Ossman
[   18.576000] sdhci: SDHCI controller found at 0000:07:06.3 [104c:803c] (rev 0)
[   18.576000] ACPI: PCI Interrupt 0000:07:06.3[A] -> GSI 18 (level, low) -> IRQ 18
[   18.576000] mmc0: SDHCI at 0xdc006800 irq 18 DMA
[   18.724000] ieee80211_crypt: registered algorithm 'NULL'
[   18.736000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   18.736000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   18.820000] Yenta: CardBus bridge found at 0000:07:06.0 [1179:ff10]
[   18.820000] Yenta: Enabling burst memory read transactions
[   18.820000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   18.820000] Yenta: Routing CardBus interrupts to PCI
[   18.820000] Yenta TI: socket 0000:07:06.0, mfunc 0x01a01b22, devctl 0x66
[   18.896000] usbcore: registered new interface driver hiddev
[   18.916000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   18.916000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   19.008000] input: USB Optical Mouse as /class/input/input2
[   19.008000] input: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.2-1
[   19.008000] usbcore: registered new interface driver usbhid
[   19.008000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   19.052000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[   19.052000] Socket status: 30000006
[   19.052000] Yenta: Raising subordinate bus# of parent bus (#07) from #07 to #0b
[   19.052000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   19.052000] cs: IO port probe 0x4000-0x4fff: clean.
[   19.052000] pcmcia: parent PCI bridge Memory window: 0xdc000000 - 0xdc0fffff
[   19.052000] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[   19.056000] ACPI: PCI Interrupt 0000:07:06.2[A] -> GSI 18 (level, low) -> IRQ 18
[   19.056000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   19.056000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   19.056000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   19.176000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   19.176000] synaptics: Toshiba Satellite A100 detected, limiting rate to 40pps.
[   19.212000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   19.252000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   19.252000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   19.476000] cs: IO port probe 0x100-0x3af: clean.
[   19.480000] cs: IO port probe 0x3e0-0x4ff: excluding 0x400-0x407 0x4d0-0x4d7
[   19.480000] cs: IO port probe 0x820-0x8ff: clean.
[   19.480000] cs: IO port probe 0xc00-0xcf7: clean.
[   19.480000] cs: IO port probe 0xa00-0xaff: clean.
[   19.944000] fuse init (API version 7.8)
[   20.016000] lp: driver loaded but no devices found
[   20.100000] Adding 1477940k swap on /dev/disk/by-uuid/a661a088-24ce-4e14-a91a-f3a00a99be95.  Priority:-1 extents:1 across:1477940k
[   20.124000] EXT3 FS on sda1, internal journal
[   20.992000] ipw3945: Radio Frequency Kill Switch is On:
[   20.992000] Kill switch must be turned off for wireless networking to work.
[   21.240000] ACPI: ACPI Dock Station Driver 
[   21.260000] ACPI: Battery Slot [BAT0] (battery absent)
[   21.388000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   21.388000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   21.408000] ibm_acpi: ec object not found
[   21.448000] Using specific hotkey driver
[   21.592000] ACPI: AC Adapter [ADP0] (on-line)
[   21.608000] input: Power Button (FF) as /class/input/input4
[   21.608000] ACPI: Power Button (FF) [PWRF]
[   21.608000] input: Lid Switch as /class/input/input5
[   21.608000] ACPI: Lid Switch [LID]
[   21.608000] input: Power Button (CM) as /class/input/input6
[   21.608000] ACPI: Power Button (CM) [PWRB]
[   21.692000] pcc_acpi: loading...
[   27.720000] [drm] Initialized drm 1.1.0 20060810
[   27.724000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   27.724000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   28.416000] eth0: no IPv6 routers present
[   28.792000] ppdev: user-space parallel port driver
[   33.496000] apm: BIOS not found.
[   52.288000] kjournald starting.  Commit interval 5 seconds
[   52.288000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   52.288000] EXT3 FS on sdb1, internal journal
[   52.288000] EXT3-fs: mounted filesystem with ordered data mode.
[   54.416000] ISO 9660 Extensions: Microsoft Joliet Level 3
[   54.632000] ISOFS: changing to secondary root
```

```
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 08:56 ?        00:00:01 /sbin/init
root         2     1  0 08:56 ?        00:00:00 [migration/0]
root         3     1  0 08:56 ?        00:00:00 [ksoftirqd/0]
root         4     1  0 08:56 ?        00:00:00 [watchdog/0]
root         5     1  0 08:56 ?        00:00:00 [migration/1]
root         6     1  0 08:56 ?        00:00:00 [ksoftirqd/1]
root         7     1  0 08:56 ?        00:00:00 [watchdog/1]
root         8     1  0 08:56 ?        00:00:00 [events/0]
root         9     1  0 08:56 ?        00:00:00 [events/1]
root        10     1  0 08:56 ?        00:00:00 [khelper]
root        11     1  0 08:56 ?        00:00:00 [kthread]
root        35    11  0 08:56 ?        00:00:00 [kblockd/0]
root        36    11  0 08:56 ?        00:00:00 [kblockd/1]
root        37    11  0 08:56 ?        00:00:00 [kacpid]
root        38    11  0 08:56 ?        00:00:00 [kacpi_notify]
root       173    11  0 08:56 ?        00:00:00 [kseriod]
root       202    11  0 08:56 ?        00:00:00 [pdflush]
root       203    11  0 08:56 ?        00:00:00 [pdflush]
root       204    11  0 08:56 ?        00:00:00 [kswapd0]
root       205    11  0 08:56 ?        00:00:00 [aio/0]
root       206    11  0 08:56 ?        00:00:00 [aio/1]
root       836     1  0 08:56 ?        00:00:00 [kirqd]
root      2057    11  0 08:56 ?        00:00:00 [ksuspend_usbd]
root      2058    11  0 08:56 ?        00:00:00 [khubd]
root      2069    11  0 08:56 ?        00:00:00 [khpsbpkt]
root      2194    11  0 08:56 ?        00:00:00 [knodemgrd_0]
root      2204    11  0 08:56 ?        00:00:00 [ata/0]
root      2206    11  0 08:56 ?        00:00:00 [ata/1]
root      2207    11  0 08:56 ?        00:00:00 [ata_aux]
root      2225    11  0 08:56 ?        00:00:00 [scsi_eh_0]
root      2226    11  0 08:56 ?        00:00:00 [scsi_eh_1]
root      2413    11  0 08:56 ?        00:00:00 [kjournald]
root      2458    11  0 08:56 ?        00:00:00 [scsi_eh_2]
root      2459    11  0 08:56 ?        00:00:00 [usb-storage]
root      2620     1  0 08:56 ?        00:00:00 /sbin/udevd --daemon
root      3606    11  0 08:56 ?        00:00:00 [kpsmoused]
root      3626    11  0 08:56 ?        00:00:00 [kmmcd]
root      3667    11  0 08:56 ?        00:00:00 [tifm/0]
root      3668    11  0 08:56 ?        00:00:00 [tifm/1]
root      3780    11  0 08:56 ?        00:00:00 [pccardd]
root      3784    11  0 08:56 ?        00:00:00 [ipw3945/0]
root      3785    11  0 08:56 ?        00:00:00 [ipw3945/1]
root      3786    11  0 08:56 ?        00:00:00 [ipw3945/0]
root      3787    11  0 08:56 ?        00:00:00 [ipw3945/1]
root      3862    11  0 08:56 ?        00:00:00 [hda_codec]
root      3876     1  0 08:56 ?        00:00:00 /sbin/ipw3945d-2.6.20-16-generic --quiet
root      4360     1  0 08:56 tty4     00:00:00 /sbin/getty 38400 tty4
root      4361     1  0 08:56 tty5     00:00:00 /sbin/getty 38400 tty5
root      4366     1  0 08:56 tty2     00:00:00 /sbin/getty 38400 tty2
root      4367     1  0 08:56 tty3     00:00:00 /sbin/getty 38400 tty3
root      4368     1  0 08:56 tty1     00:00:00 /sbin/getty 38400 tty1
root      4369     1  0 08:56 tty6     00:00:00 /sbin/getty 38400 tty6
root      4640     1  0 08:56 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4758     1  0 08:56 ?        00:00:00 /sbin/syslogd
root      4810     1  0 08:56 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4812     1  0 08:56 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
103       4833     1  0 08:56 ?        00:00:00 /usr/bin/dbus-daemon --system
107       4849     1  0 08:56 ?        00:00:00 /usr/sbin/hald
root      4850  4849  0 08:56 ?        00:00:00 hald-runner
107       4856  4850  0 08:56 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event1
107       4857  4850  0 08:56 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event4
root      4859  4850  0 08:56 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
107       4860  4850  0 08:56 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
107       4861  4850  0 08:56 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event5
107       4862  4850  0 08:56 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event6
107       4875  4850  0 08:56 ?        00:00:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      4889     1  0 08:56 ?        00:00:00 /usr/sbin/dhcdbd --system
root      4904     1  0 08:56 ?        00:00:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
avahi     4922     1  0 08:56 ?        00:00:00 avahi-daemon: running [laptop.local]
avahi     4923  4922  0 08:56 ?        00:00:00 avahi-daemon: chroot helper
root      4936     1  0 08:56 ?        00:00:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      4949     1  0 08:56 ?        00:00:00 /usr/bin/system-tools-backends
root      4950  4949  0 08:56 ?        00:00:00 dbus-daemon --session --print-address --nofork
root      4985     1  0 08:56 ?        00:00:00 /usr/sbin/gdm
root      4986  4985  0 08:56 ?        00:00:00 /usr/sbin/gdm
root      4991  4986  1 08:56 tty7     00:00:21 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
cupsys    5080     1  0 08:56 ?        00:00:00 /usr/sbin/cupsd
root      5104     1  0 08:56 ?        00:00:00 /usr/sbin/hpiod
hplip     5107     1  0 08:56 ?        00:00:00 python /usr/sbin/hpssd
root      5169     1  0 08:56 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql     5211  5169  0 08:56 ?        00:00:05 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      5212  5169  0 08:56 ?        00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
clamav    5382     1  0 08:56 ?        00:00:00 /usr/bin/freshclam -p /var/run/clamav/freshclam.pid -d --quiet
root      5404    11  0 08:56 ?        00:00:00 [kondemand/0]
root      5405    11  0 08:56 ?        00:00:00 [kondemand/1]
root      5422     1  0 08:56 ?        00:00:00 /usr/sbin/nmbd -D
root      5424     1  0 08:56 ?        00:00:00 /usr/sbin/smbd -D
root      5453  5424  0 08:56 ?        00:00:00 /usr/sbin/smbd -D
ntp       5465     1  0 08:56 ?        00:00:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 111:121 -g
root      5501     1  0 08:56 ?        00:00:00 /usr/sbin/cron
hab       5549  4986  0 08:56 ?        00:00:00 x-session-manager
root      5574     1  0 08:56 ?        00:00:00 /usr/sbin/apache
www-data  5582  5574  0 08:56 ?        00:00:00 /usr/sbin/apache
www-data  5583  5574  1 08:56 ?        00:00:18 /usr/sbin/apache
www-data  5584  5574  0 08:56 ?        00:00:00 /usr/sbin/apache
www-data  5585  5574  0 08:56 ?        00:00:00 /usr/sbin/apache
www-data  5587  5574  0 08:56 ?        00:00:00 /usr/sbin/apache
hab       5672  5549  0 08:56 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
hab       5675     1  0 08:56 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
hab       5676     1  0 08:56 ?        00:00:00 /usr/bin/dbus-daemon --fork --print-pid 4 --print-address 8 --session
hab       5678     1  0 08:56 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 6
hab       5681     1  0 08:56 ?        00:00:00 /usr/bin/gnome-keyring-daemon
hab       5683     1  0 08:56 ?        00:00:00 /usr/lib/control-center/gnome-settings-daemon
hab       5691     1  0 08:56 ?        00:00:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 24
hab       5694  5549  0 08:56 ?        00:00:01 /usr/bin/metacity --sm-client-id=default0
hab       5698  5549  0 08:56 ?        00:00:02 gnome-panel --sm-client-id default1
hab       5701  5549  0 08:56 ?        00:00:01 nautilus --no-default-window --sm-client-id default2
hab       5706     1  0 08:56 ?        00:00:00 gnome-volume-manager --sm-client-id default4
hab       5708     1  0 08:56 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
hab       5717     1  0 08:56 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
hab       5743  5549  0 08:56 ?        00:00:01 beagle-search --debug /usr/lib/beagle/Search.exe --icon
root      5744    11  0 08:56 ?        00:00:00 [kjournald]
hab       5746  5549  0 08:56 ?        00:00:00 update-notifier
hab       5761  5549  0 08:56 ?        00:00:00 /usr/lib/evolution/2.10/evolution-alarm-notify
hab       5772     1  0 08:57 ?        00:00:00 /opt/google/desktop/bin/gdl_box start
hab       5776  5549  0 08:57 ?        00:00:00 nm-applet --sm-disable
hab       5777  5772  0 08:57 ?        00:00:00 /opt/google/desktop/bin/gdl_service --Verbose=ERROR
hab       5778  5549  0 08:57 ?        00:00:00 gnome-cups-icon --sm-client-id default3
hab       5781  5777  0 08:57 ?        00:00:00 /opt/google/desktop/bin/gdl_config
hab       5782  5777  0 08:57 ?        00:00:03 /opt/google/desktop/bin/gdl_indexer
hab       5783  5777  0 08:57 ?        00:00:10 /opt/google/desktop/bin/gdl_fs_crawler
hab       5784     1  0 08:57 ?        00:00:00 gnome-power-manager
hab       5788     1  0 08:57 ?        00:00:00 /usr/lib/nautilus-cd-burner/mapping-daemon
hab       5820     1  0 08:57 ?        00:00:00 /usr/lib/evolution/evolution-data-server-1.10 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=23
hab       5832     1  0 08:57 ?        00:00:00 /usr/lib/evolution/2.10/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=24
hab       5874     1  0 08:57 ?        00:00:00 gnome-screensaver
hab       5884     1  0 08:57 ?        00:00:00 /usr/lib/gnome-applets/gnome-keyboard-applet --oaf-activate-iid=OAFIID:GNOME_KeyboardApplet_Factory --oaf-ior-fd=25
hab       5886     1  0 08:57 ?        00:00:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=33
hab       5893     1  0 08:57 ?        00:00:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=31
hab       5949     1  0 08:58 ?        00:00:00 bluefish
hab       5951     1  3 08:58 ?        00:00:35 /usr/lib/firefox/firefox-bin
hab       5958     1  0 08:58 ?        00:00:07 galeon
www-data  6255  5574  0 09:01 ?        00:00:00 /usr/sbin/apache
www-data  6256  5574  0 09:01 ?        00:00:00 /usr/sbin/apache
www-data  6257  5574  0 09:01 ?        00:00:00 /usr/sbin/apache
www-data  6260  5574  0 09:01 ?        00:00:00 /usr/sbin/apache
www-data  6261  5574  0 09:01 ?        00:00:01 /usr/sbin/apache
hab       7795     1  1 09:16 ?        00:00:00 gnome-terminal
hab       7798  7795  0 09:16 ?        00:00:00 gnome-pty-helper
hab       7799  7795  0 09:16 pts/0    00:00:00 bash
hab       7878  7799  0 09:16 pts/0    00:00:00 ps -ef
hab       7879  5783  0 09:16 ?        00:00:00 file /home/hab/dem
```

---

### Post by buixuanduong1983 on 2007-07-26
I have problem with logout: my Ubuntu hang and display blank screen, no HDD activity, wating for a long time and have to shutdown by power button. And after resume from hibenate or suspend, the power led blink green. Can anybody point out what is the problem?

---

### Post by cazmatazzz on 2007-07-26
hey mine is also starting up very slow - all of a sudden - it used to start up fine and i can't seem to figure out what has changed. now when i first start it up it even freezes at the dell start up screen(i have a dell inspiron 9300) after which i turn it on and off, then it actually does start but much slower than usual. so i'd like to tag along in this thread and see if there are any solutions....:confused:

---

### Post by bex77 on 2007-07-27
I just bought a new Dell Inspiron 530, Ubuntu pre-installed.  **Right out of the box, I am experiencing the "Starting up..." screen for over 8 minutes before it finally starts.**  If this is helpful to anyone familiar with this problem, it appears to be quite consistently taking 8-9 minutes.  If anyone has any suggestions, I would welcome it!

Thanks, Bex

---

### Post by Tranquilo on 2007-08-03
Don't know if this is the reason for the slow boot since I'm a newbie myself. But I have the same problem and the same message as you in my dmsg:
[    0.131595] PCI: Bus #0a (-#0d) is hidden behind transparent bridge #09 (-#09) (try 'pci=assign-busses')
[    0.131600] Please report the result to linux-kernel to fix this permanently
I found this thread which tells you what to do with the message:
[http://ubuntuforums.org/showthread.php?t=462847&highlight=Please+report+the+result+to+linux-kernel+fix+this+permanently](http://ubuntuforums.org/showthread.php?t=462847&highlight=Please+report+the+result+to+linux-kernel+fix+this+permanently)
But haven't had time to try it out yet.
Edit:
I have now tried adding the pci=assign-busses to the kernel line in the grub menu, and my laptop now boots without freezing...

---

