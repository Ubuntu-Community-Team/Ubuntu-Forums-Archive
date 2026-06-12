---
title: "sda or hda :( ?"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by Catch-me-if-you-Can on 2007-04-11
Hi guys...
I was working on windows on my laptop (what can I say... I can't use thegimp so I have to use photoshop :( ) and suddently my system crashed (it was working very nicely a minute ago) and then I rebooted and it did not boot into windows and later I made a "chkdsk" with the windows xp cd.... It said that my hardrive had no problems although windows didn't still start... But later I booted with Ubuntu 7.04 beta, and I found out that I had 17 bad sectors :( .... So I configured a quick FTP server on my desktop computer and I saved important data there... And then I decided that I don't want to see windows again in my life so I installed Ubuntu 7.04 Beta, witch I'm running now... 

But the problem is that my hardrive is now recognized as /dev/sda :(  and before it was /dev/hda normally... And when I boot into ubuntu, it takes a lot of time... So I would like to know what happened to me, and also if possible, how to disable the graphical thing that I see when booting... I would like to see everything behind to see what's wrong...

Here's what dmesg says:

```
[   72.404000] Yenta: Routing CardBus interrupts to PCI
[   72.404000] Yenta TI: socket 0000:02:04.0, mfunc 0x89501212, devctl 0x44
[   72.460000] ieee80211_crypt: registered algorithm 'NULL'
[   72.464000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   72.464000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   72.608000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   72.608000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   72.612000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[   72.612000] sdhci: Copyright(c) Pierre Ossman
[   72.676000] Yenta: ISA IRQ mask 0x0c48, PCI irq 16
[   72.676000] Socket status: 30000006
[   72.676000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   72.676000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   72.676000] cs: IO port probe 0x4000-0x4fff: clean.
[   72.676000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   72.676000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   72.676000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 23
[   72.676000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   72.872000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   72.872000] sdhci: SDHCI controller found at 0000:02:04.2 [1524:0550] (rev 0)
[   72.872000] ACPI: PCI Interrupt 0000:02:04.2[B] -> GSI 17 (level, low) -> IRQ 17
[   72.872000] mmc0: SDHCI at 0xd0202000 irq 17 DMA
[   72.880000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
[   72.880000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   73.708000] intel8x0_measure_ac97_clock: measured 55439 usecs
[   73.708000] intel8x0: clocking to 48000
[   73.852000] cs: IO port probe 0x100-0x3af: excluding 0x130-0x137
[   73.852000] cs: IO port probe 0x3e0-0x4ff: excluding 0x3f8-0x3ff 0x4d0-0x4d7
[   73.852000] cs: IO port probe 0x820-0x8ff: clean.
[   73.852000] cs: IO port probe 0xc00-0xcf7: clean.
[   73.856000] cs: IO port probe 0xa00-0xaff: clean.
[   74.080000] fuse init (API version 7.8)
[   74.128000] lp0: using parport0 (interrupt-driven).
[   92.856000] NET: Registered protocol family 10
[   92.856000] lo: Disabled Privacy Extensions
[   92.856000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  103.816000] eth1: no IPv6 routers present
[  116.604000] ReiserFS: sda2: found reiserfs format "3.6" with standard journal
[  116.604000] ReiserFS: sda2: using ordered data mode
[  116.608000] ReiserFS: sda2: journal params: device sda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  116.608000] ReiserFS: sda2: checking transaction log (sda2)
[  116.624000] ReiserFS: sda2: Using r5 hash to sort names
[  121.012000] Using specific hotkey driver
[  121.080000] ACPI: AC Adapter [ACAD] (on-line)
[  121.088000] No dock devices found.
[  121.228000] input: Power Button (FF) as /class/input/input4
[  121.240000] ACPI: Power Button (FF) [PWRF]
[  121.284000] input: Lid Switch as /class/input/input5
[  121.296000] ACPI: Lid Switch [LID]
[  121.344000] input: Power Button (CM) as /class/input/input6
[  121.356000] ACPI: Power Button (CM) [PWRB]
[  121.408000] ibm_acpi: ec object not found
[  121.452000] ACPI: Battery Slot [BAT1] (battery present)
[  121.460000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  121.508000] pcc_acpi: loading...
[  124.176000] ttyS1: LSR safety check engaged!
[  125.608000] ppdev: user-space parallel port driver
[  126.268000] [drm] Initialized drm 1.1.0 20060810
[  126.276000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  126.280000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[  127.424000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  127.424000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[  127.424000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[  127.776000] [drm] Setting GART location based on new memory map
[  127.776000] [drm] Loading R300 Microcode
[  127.776000] [drm] writeback test succeeded in 1 usecs
[  128.828000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  128.828000] apm: overridden by ACPI.
[  129.024000] Bluetooth: Core ver 2.11
[  129.024000] NET: Registered protocol family 31
[  129.024000] Bluetooth: HCI device and connection manager initialized
[  129.024000] Bluetooth: HCI socket layer initialized
[  129.072000] Bluetooth: L2CAP ver 2.8
[  129.072000] Bluetooth: L2CAP socket layer initialized
[  129.208000] Bluetooth: RFCOMM socket layer initialized
[  129.208000] Bluetooth: RFCOMM TTY layer initialized
[  129.208000] Bluetooth: RFCOMM ver 1.8
[  173.324000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  191.700000] eth1: no IPv6 routers present
xavito@xavito-laptop:~$ dmesg
[    0.000000] Linux version 2.6.20-12-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Wed Mar 21 20:55:46 UTC 2007 (Ubuntu 2.6.20-12.20-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d4000 size: 0000000000004000 end: 00000000000d8000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000002fdf0000 end: 000000002fef0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000002fef0000 size: 000000000000b000 end: 000000002fefb000 type: 3
[    0.000000] copy_e820_map() start: 000000002fefb000 size: 0000000000005000 end: 000000002ff00000 type: 4
[    0.000000] copy_e820_map() start: 000000002ff00000 size: 0000000000100000 end: 0000000030000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec10000 size: 0000000000010000 end: 00000000fec20000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff800000 size: 0000000000400000 end: 00000000ffc00000 type: 2
[    0.000000] copy_e820_map() start: 00000000fffffc00 size: 0000000000000400 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d4000 - 00000000000d8000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fef0000 (usable)
[    0.000000]  BIOS-e820: 000000002fef0000 - 000000002fefb000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002fefb000 - 000000002ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002ff00000 - 0000000030000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 766MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 196336) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196336
[    0.000000]   HighMem    196336 ->   196336
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196336
[    0.000000] On node 0 totalpages: 196336
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1501 pages used for memmap
[    0.000000]   Normal zone: 190739 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 TOSCPL                                ) @ 0x000f6970
[    0.000000] ACPI: RSDT (v001 TOSCPL          0x06040000  LTP 0x00000000) @ 0x2fef522c
[    0.000000] ACPI: FADT (v001 TOSCPL MONTARA  0x06040000 PTL  0x00000050) @ 0x2fefaeec
[    0.000000] ACPI: MADT (v001 INTEL  MONTARA  0x06040000 LOHR 0x00000064) @ 0x2fefaf98
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030224) @ 0x2fef5655
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030224) @ 0x2fef547d
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x2fef5264
[    0.000000] ACPI: DSDT (v001 TOSCPL MONTARAG 0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
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
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec10000)
[    0.000000] Detected 1598.698 MHz processor.
[    9.260268] Built 1 zonelists.  Total pages: 194803
[    9.260272] Kernel command line: root=UUID=c5986e3a-d346-4d24-b37d-fd0b44abb1eb ro quiet splash
[    9.260449] mapped APIC to ffffd000 (fee00000)
[    9.260452] mapped IOAPIC to ffffc000 (fec00000)
[    9.260455] Enabling fast FPU save and restore... done.
[    9.260458] Enabling unmasked SIMD FPU exception support... done.
[    9.260469] Initializing CPU#0
[    9.260541] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    9.261587] Console: colour VGA+ 80x25
[    9.261991] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    9.262483] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    9.284882] Memory: 767168k/785344k available (1990k kernel code, 17584k reserved, 890k data, 328k init, 0k highmem)
[    9.284892] virtual kernel memory layout:
[    9.284893]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    9.284895]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    9.284896]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[    9.284897]     lowmem  : 0xc0000000 - 0xefef0000   ( 766 MB)
[    9.284899]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[    9.284900]       .data : 0xc02f1b04 - 0xc03d06d4   ( 890 kB)
[    9.284902]       .text : 0xc0100000 - 0xc02f1b04   (1990 kB)
[    9.284905] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    9.364463] Calibrating delay using timer specific routine.. 3199.37 BogoMIPS (lpj=6398753)
[    9.364506] Security Framework v1.0.0 initialized
[    9.364514] SELinux:  Disabled at boot.
[    9.364531] Mount-cache hash table entries: 512
[    9.364676] CPU: After generic identify, caps: afe9fbbf 00000000 00000000 00000000 00000180 00000000 00000000
[    9.364688] CPU: L1 I cache: 32K, L1 D cache: 32K
[    9.364691] CPU: L2 cache: 2048K
[    9.364694] CPU: After all inits, caps: afe9fbbf 00000000 00000000 00002040 00000180 00000000 00000000
[    9.364704] Compat vDSO mapped to ffffe000.
[    9.364708] Remapping vsyscall page to ffffe000
[    9.364719] Checking 'hlt' instruction... OK.
[    9.380549] SMP alternatives: switching to UP code
[    9.380747] Freeing SMP alternatives: 11k freed
[    9.380929] Early unpacking initramfs... done
[    9.737410] ACPI: Core revision 20060707
[    9.737787] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.749837] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 06
[    9.749861] Total of 1 processors activated (3199.37 BogoMIPS).
[    9.749995] ENABLING IO-APIC IRQs
[    9.750175] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.896083] Brought up 1 CPUs
[    9.896319] Booting paravirtualized kernel on bare hardware
[    9.896389] Time: 16:11:14  Date: 03/11/107
[    9.896417] NET: Registered protocol family 16
[    9.896503] EISA bus registered
[    9.896508] ACPI: bus type pci registered
[    9.896840] PCI: PCI BIOS revision 2.10 entry at 0xfd962, last bus=2
[    9.896843] PCI: Using configuration type 1
[    9.896845] Setting up standard PCI resources
[    9.904798] ACPI: Interpreter enabled
[    9.904800] ACPI: Using IOAPIC for interrupt routing
[    9.905348] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.905354] PCI: Probing PCI hardware (bus 00)
[    9.906373] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    9.906377] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[    9.906595] Boot video device is 0000:01:00.0
[    9.906947] PCI: Transparent bridge - 0000:00:1e.0
[    9.906999] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[    9.907002] Please report the result to linux-kernel to fix this permanently
[    9.907020] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.913718] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    9.914195] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    9.914937] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    9.915172] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    9.915407] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 *4 5 6 7 10 12 14 15)
[    9.915639] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    9.915874] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    9.916128] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    9.916358] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    9.916592] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    9.960911] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.960920] pnp: PnP ACPI init
[    9.984099] pnp: PnP ACPI: found 10 devices
[    9.984103] PnPBIOS: Disabled by ACPI PNP
[    9.984142] PCI: Using ACPI for IRQ routing
[    9.984145] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.990013] NET: Registered protocol family 8
[    9.990015] NET: Registered protocol family 20
[    9.990337] PCI: Bridge: 0000:00:01.0
[    9.990340]   IO window: 3000-3fff
[    9.990344]   MEM window: d0100000-d01fffff
[    9.990347]   PREFETCH window: d8000000-dfffffff
[    9.990356] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[    9.990358]   IO window: 00004800-000048ff
[    9.990362]   IO window: 00004c00-00004cff
[    9.990366]   PREFETCH window: 40000000-43ffffff
[    9.990370]   MEM window: 48000000-4bffffff
[    9.990374] PCI: Bridge: 0000:00:1e.0
[    9.990377]   IO window: 4000-4fff
[    9.990382]   MEM window: d0200000-d02fffff
[    9.990386]   PREFETCH window: 40000000-43ffffff
[    9.990400] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.990415] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[    9.990439] NET: Registered protocol family 2
[   10.027992] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.028103] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   10.029121] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   10.029821] TCP: Hash tables configured (established 131072 bind 65536)
[   10.029825] TCP reno registered
[   10.040101] checking if image is initramfs... it is
[   10.742156] Freeing initrd memory: 6948k freed
[   10.742682] audit: initializing netlink socket (disabled)
[   10.742702] audit(1176307875.552:1): initialized
[   10.742837] VFS: Disk quotas dquot_6.5.1
[   10.742859] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.742918] io scheduler noop registered
[   10.742921] io scheduler anticipatory registered
[   10.742923] io scheduler deadline registered
[   10.742933] io scheduler cfq registered (default)
[   10.743279] isapnp: Scanning for PnP cards...
[   11.096625] isapnp: No Plug & Play device found
[   11.121150] Real Time Clock Driver v1.12ac
[   11.121213] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.121424] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   11.121966] ACPI: PCI Interrupt 0000:00:1f.6[B] -> GSI 17 (level, low) -> IRQ 17
[   11.121975] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   11.122054] mice: PS/2 mouse device common for all mice
[   11.122623] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.122846] input: Macintosh mouse button emulation as /class/input/input0
[   11.122882] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   11.122886] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   11.123156] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.123341] i8042.c: Detected active multiplexing controller, rev 1.1.
[   11.123387] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.123391] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   11.123394] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   11.123397] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   11.123399] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   11.123513] EISA: Probing bus 0 at eisa.0
[   11.123520] Cannot allocate resource for EISA slot 1
[   11.123523] Cannot allocate resource for EISA slot 2
[   11.123526] Cannot allocate resource for EISA slot 3
[   11.123528] Cannot allocate resource for EISA slot 4
[   11.123545] EISA: Detected 0 cards.
[   11.153715] TCP cubic registered
[   11.153729] NET: Registered protocol family 1
[   11.153754] Using IPI No-Shortcut mode
[   11.153830] ACPI: (supports S0 S3 S4 S5)
[   11.153875]   Magic number: 3:127:186
[   11.154262] Freeing unused kernel memory: 328k freed
[   11.155048] Time: tsc clocksource has been installed.
[   11.155762] input: AT Translated Set 2 keyboard as /class/input/input1
[   12.363014] Capability LSM initialized
[   12.578093] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   12.578100] ACPI: Processor [CPU0] (supports 8 throttling states)
[   12.578107] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   13.480697] usbcore: registered new interface driver usbfs
[   13.480722] usbcore: registered new interface driver hub
[   13.480743] usbcore: registered new device driver usb
[   13.481559] USB Universal Host Controller Interface driver v3.0
[   13.481611] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.481622] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   13.481626] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   13.481818] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   13.481843] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
[   13.481942] usb usb1: configuration #1 chosen from 1 choice
[   13.481968] hub 1-0:1.0: USB hub found
[   13.481973] hub 1-0:1.0: 2 ports detected
[   13.582242] ieee1394: Initialized config rom entry `ip1394'
[   13.585284] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   13.585298] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.585302] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.585325] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   13.585352] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00001820
[   13.585439] usb usb2: configuration #1 chosen from 1 choice
[   13.585462] hub 2-0:1.0: USB hub found
[   13.585469] hub 2-0:1.0: 2 ports detected
[   13.593613] 8139too Fast Ethernet driver 0.9.28
[   13.629403] SCSI subsystem initialized
[   13.634695] libata version 2.20 loaded.
[   13.689218] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   13.689232] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   13.689236] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.689262] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   13.689290] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00001840
[   13.689379] usb usb3: configuration #1 chosen from 1 choice
[   13.689403] hub 3-0:1.0: USB hub found
[   13.689408] hub 3-0:1.0: 2 ports detected
[   13.794210] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
[   13.794232] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.794236] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.794267] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   13.794302] ehci_hcd 0000:00:1d.7: debug port 1
[   13.794308] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   13.794319] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd0000000
[   13.798190] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.798271] usb usb4: configuration #1 chosen from 1 choice
[   13.798297] hub 4-0:1.0: USB hub found
[   13.798304] hub 4-0:1.0: 6 ports detected
[    4.492000] Time: acpi_pm clocksource has been installed.
[    4.532000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 21
[    4.584000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[d0201000-d02017ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.588000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 22
[    4.588000] eth0: RealTek RTL8139 at 0xf08d2800, 00:0f:b0:5a:c0:f1, IRQ 22
[    4.588000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.592000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.592000] ata_piix 0000:00:1f.1: version 2.10ac1
[    4.592000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    4.592000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[    4.592000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.592000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
[    4.592000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
[    4.592000] scsi0 : ata_piix
[    4.760000] ata1.00: ATA-6: TOSHIBA MK6025GAS, KA200K, max UDMA/100
[    4.760000] ata1.00: 117210240 sectors, multi 16: LBA 
[    4.768000] ata1.00: configured for UDMA/100
[    4.768000] scsi1 : ata_piix
[    5.088000] ata2.00: ATAPI, max UDMA/33
[    5.252000] ata2.00: configured for UDMA/33
[    5.252000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6025GA KA20 PQ: 0 ANSI: 5
[    5.252000] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-831S  1.50 PQ: 0 ANSI: 5
[    5.268000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    5.268000] sda: Write Protect is off
[    5.268000] sda: Mode Sense: 00 3a 00 00
[    5.268000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.268000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    5.268000] sda: Write Protect is off
[    5.268000] sda: Mode Sense: 00 3a 00 00
[    5.268000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.268000]  sda: sda1 sda2
[    5.320000] sd 0:0:0:0: Attached scsi disk sda
[    5.324000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.324000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.328000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.328000] Uniform CD-ROM driver Revision: 3.20
[    5.328000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.496000] ReiserFS: sda1: found reiserfs format "3.6" with standard journal
[    5.496000] ReiserFS: sda1: using ordered data mode
[    5.512000] ReiserFS: sda1: journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    5.512000] ReiserFS: sda1: checking transaction log (sda1)
[    5.544000] ReiserFS: sda1: Using r5 hash to sort names
[    5.860000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f5265413401]
[   68.176000] eth0: link down
[   70.096000] input: PS/2 Mouse as /class/input/input2
[   70.116000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[   70.172000] Linux agpgart interface v0.101 (c) Dave Jones
[   70.292000] agpgart: Detected an Intel 855GM Chipset.
[   70.312000] agpgart: AGP aperture is 256M @ 0xe0000000
[   71.060000] intel_rng: FWH not detected
[   71.076000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   71.084000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   71.092000] parport: PnPBIOS parport detected.
[   71.092000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   71.272000] NET: Registered protocol family 17
[   71.304000] irda_init()
[   71.304000] NET: Registered protocol family 23
[   71.324000] Detected unconfigured Toshiba laptop with Intel 8281DBM LPC bridge SMSC IrDA chip, pre-configuring device.
[   71.324000] Setting up Intel 82801 controller and SMSC device
[   71.324000] Detected Chip id: 0x7a, setting up registers...
[   72.276000] iTCO_vendor_support: vendor-support=0
[   72.348000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   72.348000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   72.348000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   72.404000] Yenta: CardBus bridge found at 0000:02:04.0 [1179:ff01]
[   72.404000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   72.404000] Yenta: Routing CardBus interrupts to PCI
[   72.404000] Yenta TI: socket 0000:02:04.0, mfunc 0x89501212, devctl 0x44
[   72.460000] ieee80211_crypt: registered algorithm 'NULL'
[   72.464000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   72.464000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   72.608000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   72.608000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   72.612000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[   72.612000] sdhci: Copyright(c) Pierre Ossman
[   72.676000] Yenta: ISA IRQ mask 0x0c48, PCI irq 16
[   72.676000] Socket status: 30000006
[   72.676000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   72.676000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   72.676000] cs: IO port probe 0x4000-0x4fff: clean.
[   72.676000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   72.676000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   72.676000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 23
[   72.676000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   72.872000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   72.872000] sdhci: SDHCI controller found at 0000:02:04.2 [1524:0550] (rev 0)
[   72.872000] ACPI: PCI Interrupt 0000:02:04.2[B] -> GSI 17 (level, low) -> IRQ 17
[   72.872000] mmc0: SDHCI at 0xd0202000 irq 17 DMA
[   72.880000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
[   72.880000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   73.708000] intel8x0_measure_ac97_clock: measured 55439 usecs
[   73.708000] intel8x0: clocking to 48000
[   73.852000] cs: IO port probe 0x100-0x3af: excluding 0x130-0x137
[   73.852000] cs: IO port probe 0x3e0-0x4ff: excluding 0x3f8-0x3ff 0x4d0-0x4d7
[   73.852000] cs: IO port probe 0x820-0x8ff: clean.
[   73.852000] cs: IO port probe 0xc00-0xcf7: clean.
[   73.856000] cs: IO port probe 0xa00-0xaff: clean.
[   74.080000] fuse init (API version 7.8)
[   74.128000] lp0: using parport0 (interrupt-driven).
[   92.856000] NET: Registered protocol family 10
[   92.856000] lo: Disabled Privacy Extensions
[   92.856000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  103.816000] eth1: no IPv6 routers present
[  116.604000] ReiserFS: sda2: found reiserfs format "3.6" with standard journal
[  116.604000] ReiserFS: sda2: using ordered data mode
[  116.608000] ReiserFS: sda2: journal params: device sda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  116.608000] ReiserFS: sda2: checking transaction log (sda2)
[  116.624000] ReiserFS: sda2: Using r5 hash to sort names
[  121.012000] Using specific hotkey driver
[  121.080000] ACPI: AC Adapter [ACAD] (on-line)
[  121.088000] No dock devices found.
[  121.228000] input: Power Button (FF) as /class/input/input4
[  121.240000] ACPI: Power Button (FF) [PWRF]
[  121.284000] input: Lid Switch as /class/input/input5
[  121.296000] ACPI: Lid Switch [LID]
[  121.344000] input: Power Button (CM) as /class/input/input6
[  121.356000] ACPI: Power Button (CM) [PWRB]
[  121.408000] ibm_acpi: ec object not found
[  121.452000] ACPI: Battery Slot [BAT1] (battery present)
[  121.460000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  121.508000] pcc_acpi: loading...
[  124.176000] ttyS1: LSR safety check engaged!
[  125.608000] ppdev: user-space parallel port driver
[  126.268000] [drm] Initialized drm 1.1.0 20060810
[  126.276000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  126.280000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[  127.424000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  127.424000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[  127.424000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[  127.776000] [drm] Setting GART location based on new memory map
[  127.776000] [drm] Loading R300 Microcode
[  127.776000] [drm] writeback test succeeded in 1 usecs
[  128.828000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  128.828000] apm: overridden by ACPI.
[  129.024000] Bluetooth: Core ver 2.11
[  129.024000] NET: Registered protocol family 31
[  129.024000] Bluetooth: HCI device and connection manager initialized
[  129.024000] Bluetooth: HCI socket layer initialized
[  129.072000] Bluetooth: L2CAP ver 2.8
[  129.072000] Bluetooth: L2CAP socket layer initialized
[  129.208000] Bluetooth: RFCOMM socket layer initialized
[  129.208000] Bluetooth: RFCOMM TTY layer initialized
[  129.208000] Bluetooth: RFCOMM ver 1.8
[  173.324000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  191.700000] eth1: no IPv6 routers present
```

I hope it can help...

---

### Post by floke on 2007-04-11
I think its ctrl-alt F1 (F something anyway).
Whereabouts is the hold up? Is it just slow all the way through or at a particular point?

EDIT: I think the sda thing is a new standardisation from a recent kernel update - nothing to worry about.

---

### Post by Catch-me-if-you-Can on 2007-04-11
It slows down at the very beguining... It looks like at 5% but I can't be sure...  Ctrl+Alt+F1 ? Isen't that used to switch to terminal 1 on text mode ? (just like Ctrl+Alt+F2 is for terminal 2 ?) But anyways, thank you, I will try that...

And about the sda.... I also booted in SimplyMepis 6.5 and I think it used kernel 2.6.15... and it also detected sda :( and a lot of time before, when I used 2.6.15 on gentoo or maybe slackware, it showed hda... It has been showing hda since 2.4 versions to 2.6.19... and now ```
~$ uname -a
Linux xavito-laptop 2.6.20-12-generic #2 SMP Wed Mar 21 20:55:46 UTC 2007 i686 GNU/Linux

```
but I hope you're correct... 

Thanks :D

---

### Post by Catch-me-if-you-Can on 2007-04-12
Update: Things are getting better now... It doesen't take to much time to boot now, maybe that time took a lot of time because it was the first boot...
But I would still like to know why is my hardisk is still apearing as sda :(

---

### Post by daxumaming on 2007-04-13
I actually filed a bug(1) regarding this but was rejected since developers are changing the format from hdx to sdx. I didn't know about the transition back then.

Here's Oliver Lacroix's comments:

> this is due to the new way the kernel deals with PATA devices : SATA and PATA are now used in a more unified way I believe, and as a result, no more "hdX"...

to fix any problem you may encounter, change your /etc/fstab accordingly.

by the way, my cdrom drive is now /dev/scd0.

A good solution would be to use UUID in fstab to manage your partitions.

Feel free to ask for any help. But this is not a bug... let's say an evolution

(1) [https://bugs.launchpad.net/ubuntu/+source/asmounter/+bug/104437](https://bugs.launchpad.net/ubuntu/+source/asmounter/+bug/104437)

---

### Post by CC_machine on 2007-04-13
i thought sdX and hdX was to distinct between hard drives and external (usb) drives?

i noticed my SATA drive appears as sda, and it's no problem installing ubuntu... yet it tells me it installs the bootloader to (hda) yet i can't mount hda1 or anything!

---

### Post by ghoshe on 2007-05-04
To disable the "graphical thing" you must edit the boot line in grub's booting menu, pressing "e", and delete "splash", accepting and pressing "b" to boot, or you can edit your grub.lst (/boot/grub/menu.lst) and delete ""splash" too in the "boot= ... " lines.

---

