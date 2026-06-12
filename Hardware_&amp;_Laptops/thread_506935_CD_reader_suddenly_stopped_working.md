---
title: "CD reader suddenly stopped working"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by Enselic on 2007-07-22
I have a new laptop on which I run both Feisty and Gutsy.

When I first installed Gutsy, the CD reader/recorder was working fine, but the touchpad did not work at all. Suddenly, the CD reader stopped working. I don't have a /dev/hda and when I double click on the CD in Nautilus, I get an error:

mount: special device /dev/hda does not exist.

After it stopped working, I completely reinstalled both Feisty and Gutsy (so that I dual boot them), but the CD reader still don't work! This is strange, since with the exact same CD it worked previoulsly.

I've tried to experiement with settings in the BIOS to get the CD reader to work again, but with no luck. Interestingly enough, I can move the cursor with the touchpad now. I don't know if that has anything to do with the CD reader, but I wanted to mention it in case it has.

I had some output from dmesg which has made me experiemtn with some kernel boot options, like pci=assign-busses and pci=routeirq, and also noacpi, noapic and nolapic, but wihout result.

I don't understand how it can be so hard to get the CD working when it once worked out of the box!

Btw, this is likely not a hardware problem, because I can with no prolems boot from and install both Gutsy and Fesity (using the alternate CDs).

Does anyone have any clue of what I can do to get it back?

For reference, here is my current dmesg and lspci output:

```
martin@ltop:~/Kallkod/C/ubuntu-gutsy$ dmesg
[    0.000000] Linux version 2.6.22-8-generic (buildd@palmer) (gcc version 4.1.3 20070629 (prerelease) (Ubuntu 4.1.2-13ubuntu2)) #1 SMP Thu Jul 12 15:59:45 GMT 2007
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f670000 (usable)
[    0.000000]  BIOS-e820: 000000003f670000 - 000000003f67f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f67f000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7fb0
[    0.000000] Entering add_active_range(0, 0, 259696) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259696
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259696
[    0.000000] On node 0 totalpages: 259696
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 236 pages used for memmap
[    0.000000]   HighMem zone: 30084 pages, LIFO batch:7
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000F7F80, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 3F676D59, 0094 (r1 PTLTD       XSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 3F67DCDD, 00F4 (r3 INTEL  CRESTLNE  6040000 ALAN        1)
[    0.000000] ACPI: DSDT 3F678AE7, 5182 (r2 INTEL  CRESTLNE  6040000 INTL 20050624)
[    0.000000] ACPI: FACS 3F67EFC0, 0040
[    0.000000] ACPI: APIC 3F67DDD1, 0068 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 3F67DE39, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 3F67DE71, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA 3F67DEAD, 0032 (r1 Intel   CRESTLN  6040000          5A52)
[    0.000000] ACPI: TMOR 3F67DEDF, 0026 (r1 PTLTD            6040000 PTL         3)
[    0.000000] ACPI: ASF! 3F67DF05, 006B (r32 OEMID  OEMTBL    6040000 PTL         1)
[    0.000000] ACPI: APIC 3F67DF70, 0068 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 3F67DFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 3F678498, 064F (r1 SataRe  SataPri     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 3F677DFC, 069C (r1 SataRe  SataSec     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 3F677379, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 3F6772D3, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 3F676DED, 04E6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: INTEL    Product ID: S. Rosa CRB  APIC at: 0xFEE00000
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] I/O APIC #2 Version 32 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Built 1 zonelists.  Total pages: 257668
[    0.000000] Kernel command line: root=UUID=0acdaa04-6cba-4001-beda-f7dea5ef81ef ro quiet splash noacpi noapic nolapic
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.070 MHz processor.
[   61.390529] Console: colour VGA+ 80x25
[   61.390908] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   61.391224] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   61.413555] Memory: 1018428k/1038784k available (2009k kernel code, 19600k reserved, 918k data, 364k init, 121280k highmem)
[   61.413562] virtual kernel memory layout:
[   61.413563]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   61.413564]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   61.413565]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   61.413566]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   61.413567]       .init : 0xc03e1000 - 0xc043c000   ( 364 kB)
[   61.413568]       .data : 0xc02f6606 - 0xc03dbe64   ( 918 kB)
[   61.413568]       .text : 0xc0100000 - 0xc02f6606   (2009 kB)
[   61.413571] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   61.413598] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   61.413615] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   61.413619] hpet0: 3 64-bit timers, 14318180 Hz
[   61.494590] Calibrating delay using timer specific routine.. 3993.57 BogoMIPS (lpj=7987154)
[   61.494608] Security Framework v1.0.0 initialized
[   61.494611] SELinux:  Disabled at boot.
[   61.494621] Mount-cache hash table entries: 512
[   61.494714] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   61.494721] monitor/mwait feature present.
[   61.494723] using mwait in idle threads.
[   61.494726] CPU: L1 I cache: 32K, L1 D cache: 32K
[   61.494728] CPU: L2 cache: 4096K
[   61.494730] CPU: Physical Processor ID: 0
[   61.494731] CPU: Processor Core ID: 0
[   61.494733] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   61.494740] Compat vDSO mapped to ffffe000.
[   61.494749] Checking 'hlt' instruction... OK.
[   61.510662] SMP alternatives: switching to UP code
[   61.510916] ACPI: Core revision 20070126
[   61.512926] ACPI: setting ELCR to 0200 (from 0ca0)
[   61.578261] CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[   61.578274] SMP alternatives: switching to SMP code
[   61.578289] Booting processor 1/1 eip 3000
[   61.588760] Initializing CPU#1
[   61.666492] Calibrating delay using timer specific routine.. 3990.03 BogoMIPS (lpj=7980067)
[   61.666497] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   61.666501] monitor/mwait feature present.
[   61.666504] CPU: L1 I cache: 32K, L1 D cache: 32K
[   61.666505] CPU: L2 cache: 4096K
[   61.666507] CPU: Physical Processor ID: 0
[   61.666508] CPU: Processor Core ID: 1
[   61.666510] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   61.667170] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[   61.667191] Total of 2 processors activated (7983.61 BogoMIPS).
[   61.774516] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   61.794518] Brought up 2 CPUs
[   62.085239] migration_cost=60
[   62.085358] Booting paravirtualized kernel on bare hardware
[   62.085437] Time: 14:06:10  Date: 06/22/107
[   62.085454] NET: Registered protocol family 16
[   62.085524] EISA bus registered
[   62.085527] ACPI: bus type pci registered
[   62.085536] PCI: Using MMCONFIG
[   62.086244] Setting up standard PCI resources
[   62.088395] ACPI: EC: Look up EC in DSDT
[   62.088924] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   62.090158] ACPI: System BIOS is requesting _OSI(Linux)
[   62.090160] ACPI: Please test with "acpi_osi=!Linux"
[   62.090161] Please send dmidecode to linux-acpi@vger.kernel.org
[   62.090609] ACPI: Interpreter enabled
[   62.090611] ACPI: (supports S0 S3 S4 S5)
[   62.090625] ACPI: Using PIC for interrupt routing
[   62.101817] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   62.101863] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   62.101869] PCI: Probing PCI hardware (bus 00)
[   62.103553] PCI: Transparent bridge - 0000:00:1e.0
[   62.103604] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#07) (try 'pci=assign-busses')
[   62.103606] Please report the result to linux-kernel to fix this permanently
[   62.103654] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   62.104001] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   62.104129] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   62.104253] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   62.104377] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   62.104513] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   62.114352] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[   62.114438] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   62.114524] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   62.114606] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   62.114688] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   62.114771] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   62.114852] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   62.114934] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   62.115092] ACPI: Power Resource [FN00] (off)
[   62.115101] Linux Plug and Play Support v0.97 (c) Adam Belay
[   62.115111] pnp: PnP ACPI init
[   62.115118] ACPI: bus type pnp registered
[   62.120081] pnp: PnP ACPI: found 13 devices
[   62.120083] ACPI: ACPI bus type pnp unregistered
[   62.120086] PnPBIOS: Disabled by ACPI PNP
[   62.120123] PCI: Using ACPI for IRQ routing
[   62.120125] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   62.120320] NET: Registered protocol family 8
[   62.120321] NET: Registered protocol family 20
[   62.120360] pnp: 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   62.120362] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   62.120365] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   62.120368] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   62.120373] pnp: 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   62.122242] Time: tsc clocksource has been installed.
[   62.122263] Switched to high resolution mode on CPU 0
[   62.122328] Switched to high resolution mode on CPU 1
[   62.150613] PCI: Bridge: 0000:00:1c.0
[   62.150615]   IO window: disabled.
[   62.150619]   MEM window: f0200000-f02fffff
[   62.150622]   PREFETCH window: disabled.
[   62.150626] PCI: Bridge: 0000:00:1c.1
[   62.150627]   IO window: disabled.
[   62.150631]   MEM window: disabled.
[   62.150633]   PREFETCH window: disabled.
[   62.150637] PCI: Bridge: 0000:00:1c.2
[   62.150638]   IO window: disabled.
[   62.150643]   MEM window: f0300000-f03fffff
[   62.150645]   PREFETCH window: disabled.
[   62.150648] PCI: Bridge: 0000:00:1c.3
[   62.150650]   IO window: disabled.
[   62.150653]   MEM window: disabled.
[   62.150656]   PREFETCH window: disabled.
[   62.150662] PCI: Bus 7, cardbus bridge: 0000:06:06.0
[   62.150663]   IO window: 00002000-000020ff
[   62.150667]   IO window: 00002400-000024ff
[   62.150671]   PREFETCH window: 50000000-53ffffff
[   62.150675]   MEM window: 58000000-5bffffff
[   62.150679] PCI: Bridge: 0000:00:1e.0
[   62.150681]   IO window: 2000-2fff
[   62.150685]   MEM window: f0400000-f04fffff
[   62.150688]   PREFETCH window: 50000000-53ffffff
[   62.150834] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7
[   62.150836] PCI: setting IRQ 7 as level-triggered
[   62.150840] ACPI: PCI Interrupt 0000:00:1c.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[   62.150846] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   62.150978] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[   62.150980] PCI: setting IRQ 5 as level-triggered
[   62.150985] ACPI: PCI Interrupt 0000:00:1c.1[B] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[   62.150990] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   62.151119] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 7
[   62.151121] ACPI: PCI Interrupt 0000:00:1c.2[C] -> Link [LNKC] -> GSI 7 (level, low) -> IRQ 7
[   62.151127] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   62.151258] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
[   62.151260] PCI: setting IRQ 6 as level-triggered
[   62.151264] ACPI: PCI Interrupt 0000:00:1c.3[D] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
[   62.151269] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   62.151278] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   62.151291] ACPI: PCI Interrupt 0000:06:06.0[A] -> Link [LNKC] -> GSI 7 (level, low) -> IRQ 7
[   62.151302] NET: Registered protocol family 2
[   62.198194] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   62.198245] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   62.198819] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   62.199017] TCP: Hash tables configured (established 131072 bind 65536)
[   62.199019] TCP reno registered
[   62.214276] checking if image is initramfs... it is
[   62.734111] Freeing initrd memory: 6767k freed
[   62.734219] Simple Boot Flag at 0x36 set to 0x1
[   62.734605] audit: initializing netlink socket (disabled)
[   62.734618] audit(1185113170.024:1): initialized
[   62.734697] highmem bounce pool size: 64 pages
[   62.736181] VFS: Disk quotas dquot_6.5.1
[   62.736220] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   62.736298] io scheduler noop registered
[   62.736300] io scheduler anticipatory registered
[   62.736302] io scheduler deadline registered
[   62.736313] io scheduler cfq registered (default)
[   62.736325] Boot video device is 0000:00:02.0
[   62.736497] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   62.736537] assign_interrupt_mode Found MSI capability
[   62.736571] Allocate Port Service[0000:00:1c.0:pcie00]
[   62.736598] Allocate Port Service[0000:00:1c.0:pcie02]
[   62.736623] Allocate Port Service[0000:00:1c.0:pcie03]
[   62.736694] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   62.736734] assign_interrupt_mode Found MSI capability
[   62.736764] Allocate Port Service[0000:00:1c.1:pcie00]
[   62.736789] Allocate Port Service[0000:00:1c.1:pcie02]
[   62.736813] Allocate Port Service[0000:00:1c.1:pcie03]
[   62.736883] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   62.736923] assign_interrupt_mode Found MSI capability
[   62.736954] Allocate Port Service[0000:00:1c.2:pcie00]
[   62.736979] Allocate Port Service[0000:00:1c.2:pcie02]
[   62.737003] Allocate Port Service[0000:00:1c.2:pcie03]
[   62.737074] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   62.737114] assign_interrupt_mode Found MSI capability
[   62.737144] Allocate Port Service[0000:00:1c.3:pcie00]
[   62.737169] Allocate Port Service[0000:00:1c.3:pcie02]
[   62.737194] Allocate Port Service[0000:00:1c.3:pcie03]
[   62.737346] isapnp: Scanning for PnP cards...
[   63.091444] isapnp: No Plug & Play device found
[   63.107753] Real Time Clock Driver v1.12ac
[   63.107920] hpet_resources: 0xfed00000 is busy
[   63.107949] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   63.108815] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   63.108981] input: Macintosh mouse button emulation as /class/input/input0
[   63.109050] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   63.112408] serio: i8042 KBD port at 0x60,0x64 irq 1
[   63.112412] serio: i8042 AUX port at 0x60,0x64 irq 12
[   63.112498] mice: PS/2 mouse device common for all mice
[   63.112574] EISA: Probing bus 0 at eisa.0
[   63.112580] Cannot allocate resource for EISA slot 1
[   63.112583] Cannot allocate resource for EISA slot 2
[   63.112606] EISA: Detected 0 cards.
[   63.112672] TCP cubic registered
[   63.112681] NET: Registered protocol family 1
[   63.112699] Using IPI No-Shortcut mode
[   63.112831]   Magic number: 15:208:132
[   63.112894]   hash matches device device:07
[   63.113082] Freeing unused kernel memory: 364k freed
[   63.132853] input: AT Translated Set 2 keyboard as /class/input/input1
[   64.276420] Capability LSM initialized
[   64.279504] ACPI: Transitioning device [FAN0] to D3
[   64.279506] ACPI: Transitioning device [FAN0] to D3
[   64.279508] ACPI: Fan [FAN0] (off)
[   64.283329] ACPI: SSDT 3F677B3E, 01F6 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   64.283504] ACPI: SSDT 3F6775D8, 04E1 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   64.283951] Monitor-Mwait will be used to enter C-1 state
[   64.283953] Monitor-Mwait will be used to enter C-2 state
[   64.283957] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   64.283961] ACPI: Processor [CPU0] (supports 8 throttling states)
[   64.284149] ACPI: SSDT 3F677D34, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   64.284312] ACPI: SSDT 3F677AB9, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   64.284782] ACPI: CPU1 (power states: C1[C1] C2[C2])
[   64.284787] ACPI: Processor [CPU1] (supports 8 throttling states)
[   64.289558] ACPI: Thermal Zone [TZ00] (60 C)
[    2.692000] Marking TSC unstable due to: possible TSC halt in C2.
[    2.696000] Time: hpet clocksource has been installed.
[    2.696000] ACPI: Thermal Zone [TZ01] (0 C)
[    2.696000] ACPI: Thermal Zone [TZ02] (0 C)
[    3.080000] usbcore: registered new interface driver usbfs
[    3.080000] usbcore: registered new interface driver hub
[    3.080000] usbcore: registered new device driver usb
[    3.080000] USB Universal Host Controller Interface driver v3.0
[    3.080000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[    3.080000] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    3.080000] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.080000] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    3.080000] uhci_hcd 0000:00:1a.0: irq 5, io base 0x00001820
[    3.080000] usb usb1: configuration #1 chosen from 1 choice
[    3.080000] hub 1-0:1.0: USB hub found
[    3.080000] hub 1-0:1.0: 2 ports detected
[    3.160000] SCSI subsystem initialized
[    3.164000] libata version 2.21 loaded.
[    3.184000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[    3.184000] PCI: setting IRQ 11 as level-triggered
[    3.184000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[    3.184000] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    3.184000] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.184000] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    3.184000] uhci_hcd 0000:00:1a.1: irq 11, io base 0x00001840
[    3.184000] usb usb2: configuration #1 chosen from 1 choice
[    3.184000] hub 2-0:1.0: USB hub found
[    3.184000] hub 2-0:1.0: 2 ports detected
[    3.288000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 6
[    3.288000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKH] -> GSI 6 (level, low) -> IRQ 6
[    3.288000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.288000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.288000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    3.288000] uhci_hcd 0000:00:1d.0: irq 6, io base 0x00001860
[    3.288000] usb usb3: configuration #1 chosen from 1 choice
[    3.288000] hub 3-0:1.0: USB hub found
[    3.288000] hub 3-0:1.0: 2 ports detected
[    3.392000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
[    3.392000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.392000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.392000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    3.392000] uhci_hcd 0000:00:1d.1: irq 6, io base 0x00001880
[    3.392000] usb usb4: configuration #1 chosen from 1 choice
[    3.392000] hub 4-0:1.0: USB hub found
[    3.392000] hub 4-0:1.0: 2 ports detected
[    3.496000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 7 (level, low) -> IRQ 7
[    3.496000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.496000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.496000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    3.496000] uhci_hcd 0000:00:1d.2: irq 7, io base 0x000018a0
[    3.496000] usb usb5: configuration #1 chosen from 1 choice
[    3.496000] hub 5-0:1.0: USB hub found
[    3.496000] hub 5-0:1.0: 2 ports detected
[    3.600000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> Link [LNKC] -> GSI 7 (level, low) -> IRQ 7
[    3.600000] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    3.600000] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.600000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    3.600000] ehci_hcd 0000:00:1a.7: debug port 1
[    3.600000] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[    3.600000] ehci_hcd 0000:00:1a.7: irq 7, io mem 0xf0704000
[    3.604000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.604000] usb usb6: configuration #1 chosen from 1 choice
[    3.604000] hub 6-0:1.0: USB hub found
[    3.604000] hub 6-0:1.0: 4 ports detected
[    3.708000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> Link [LNKH] -> GSI 6 (level, low) -> IRQ 6
[    3.708000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.708000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.708000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    3.708000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.708000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.708000] ehci_hcd 0000:00:1d.7: irq 6, io mem 0xf0704400
[    3.712000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.712000] usb usb7: configuration #1 chosen from 1 choice
[    3.712000] hub 7-0:1.0: USB hub found
[    3.712000] hub 7-0:1.0: 6 ports detected
[    3.816000] tg3.c:v3.77 (May 31, 2007)
[    3.816000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[    3.816000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    3.840000] eth0: Tigon3 [partno(BCM95787m) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:a0:d1:c2:37:b0
[    3.840000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    3.840000] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    3.840000] ata_piix 0000:00:1f.2: version 2.11
[    3.840000] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    3.996000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
[    3.996000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    3.996000] scsi0 : ata_piix
[    3.996000] scsi1 : ata_piix
[    3.996000] ata1: SATA max UDMA/133 cmd 0x00011c00 ctl 0x000118f6 bmdma 0x000118e0 irq 6
[    3.996000] ata2: SATA max UDMA/133 cmd 0x000118f8 ctl 0x000118f2 bmdma 0x000118e8 irq 6
[    4.160000] ata1.00: ATA-7: HTS721080G9SA00, MC4OC10V, max UDMA/100
[    4.160000] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.176000] ata1.00: configured for UDMA/100
[    4.340000] scsi 0:0:0:0: Direct-Access     ATA      HTS721080G9SA00  MC4O PQ: 0 ANSI: 5
[    4.340000] ACPI: PCI Interrupt 0000:06:06.1[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[    4.392000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[7]  MMIO=[f0406000-f04067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.392000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.392000] sd 0:0:0:0: [sda] Write Protect is off
[    4.392000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.392000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.392000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    4.392000] sd 0:0:0:0: [sda] Write Protect is off
[    4.392000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.392000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.392000]  sda: sda1 < sda5 sda6 sda7 >
[    4.440000] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.444000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.504000] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    4.668000] Attempting manual resume
[    4.668000] swsusp: Resume From Partition 8:5
[    4.668000] PM: Checking swsusp image.
[    4.668000] PM: Resume from disk failed.
[    4.684000] usb 4-1: configuration #1 chosen from 1 choice
[    4.696000] usbcore: registered new interface driver hiddev
[    4.704000] kjournald starting.  Commit interval 5 seconds
[    4.704000] EXT3-fs: mounted filesystem with ordered data mode.
[    4.708000] input: Logitech USB Receiver as /class/input/input2
[    4.708000] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-1
[    4.736000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: Fixing up Logitech keyboard report descriptor
[    4.736000] input: Logitech USB Receiver as /class/input/input3
[    4.736000] input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1
[    4.736000] usbcore: registered new interface driver usbhid
[    4.736000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   14.008000] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 100506, writing 100106)
[   14.904000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.936000] agpgart: Detected an Intel 965GM Chipset.
[   14.936000] agpgart: Detected 7676K stolen memory.
[   14.952000] agpgart: AGP aperture is 256M @ 0xd0000000
[   15.004000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.068000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.328000] ACPI: PCI Interrupt 0000:06:06.2[A] -> Link [LNKC] -> GSI 7 (level, low) -> IRQ 7
[   15.332000] NET: Registered protocol family 17
[   15.332000] sdhci: Secure Digital Host Controller Interface driver
[   15.332000] sdhci: Copyright(c) Pierre Ossman
[   15.332000] sdhci: SDHCI controller found at 0000:06:06.3 [104c:803c] (rev 0)
[   15.332000] ACPI: PCI Interrupt 0000:06:06.3[A] -> Link [LNKC] -> GSI 7 (level, low) -> IRQ 7
[   15.332000] mmc0: SDHCI at 0xf0406800 irq 7 DMA
[   15.424000] irda_init()
[   15.424000] NET: Registered protocol family 23
[   15.456000] Yenta: CardBus bridge found at 0000:06:06.0 [1170:0040]
[   15.456000] Yenta: Enabling burst memory read transactions
[   15.456000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   15.456000] Yenta: Routing CardBus interrupts to PCI
[   15.456000] Yenta TI: socket 0000:06:06.0, mfunc 0x01aa1b22, devctl 0x64
[   15.468000] tpm_inf_pnp 00:0a: Found TPM with ID IFX0102
[   15.468000] tpm_inf_pnp 00:0a: TPM found: config base 0x4e, data base 0x1670, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[   15.688000] Yenta: ISA IRQ mask 0x0408, PCI irq 7
[   15.688000] Socket status: 30000006
[   15.688000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   15.688000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   15.688000] cs: IO port probe 0x2000-0x2fff: clean.
[   15.688000] pcmcia: parent PCI bridge Memory window: 0xf0400000 - 0xf04fffff
[   15.688000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   15.688000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   15.688000] tg3: eth0: Flow control is on for TX and on for RX.
[   15.704000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[   15.704000] PCI: setting IRQ 10 as level-triggered
[   15.704000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> Link [LNKG] -> GSI 10 (level, low) -> IRQ 10
[   15.704000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   15.988000] cs: IO port probe 0x100-0x3af: excluding 0x228-0x22f
[   15.992000] cs: IO port probe 0x3e0-0x4ff: excluding 0x400-0x427 0x4d0-0x4d7
[   15.992000] cs: IO port probe 0x820-0x8ff: clean.
[   15.992000] cs: IO port probe 0xc00-0xcf7: clean.
[   15.992000] cs: IO port probe 0xa00-0xaff: clean.
[   16.036000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x92a0b1, caps: 0xa04713/0x200000
[   16.068000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   16.072000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x228 ; irq 3 ; dma 3.
[   16.072000] pnp: Device 00:09 disabled.
[   16.736000] lp: driver loaded but no devices found
[   16.808000] Adding 2931788k swap on /dev/disk/by-uuid/6a7c91d4-ede0-4f17-a045-40248008f214.  Priority:-1 extents:1 across:2931788k
[   17.212000] EXT3 FS on sda7, internal journal
[   17.752000] kjournald starting.  Commit interval 5 seconds
[   17.756000] EXT3 FS on sda6, internal journal
[   17.756000] EXT3-fs: mounted filesystem with ordered data mode.
[   18.192000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   18.212000] ACPI: AC Adapter [ADP0] (on-line)
[   18.252000] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
[   18.272000] ACPI: Battery Slot [BAT0] (battery present)
[   18.292000] input: Power Button (FF) as /class/input/input5
[   18.292000] ACPI: Power Button (FF) [PWRF]
[   18.296000] input: Lid Switch as /class/input/input6
[   18.296000] ACPI: Lid Switch [LID]
[   18.304000] input: Power Button (CM) as /class/input/input7
[   18.304000] ACPI: Power Button (CM) [PWRB]
[   18.328000] No dock devices found.
[   22.532000] NET: Registered protocol family 10
[   22.532000] lo: Disabled Privacy Extensions
[   23.256000] apm: BIOS not found.
[   23.628000] [drm] Initialized drm 1.1.0 20060810
[   23.676000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[   23.676000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   24.476000] Bluetooth: Core ver 2.11
[   24.476000] NET: Registered protocol family 31
[   24.476000] Bluetooth: HCI device and connection manager initialized
[   24.476000] Bluetooth: HCI socket layer initialized
[   24.508000] Bluetooth: L2CAP ver 2.8
[   24.508000] Bluetooth: L2CAP socket layer initialized
[   24.696000] Bluetooth: RFCOMM socket layer initialized
[   24.696000] Bluetooth: RFCOMM TTY layer initialized
[   24.696000] Bluetooth: RFCOMM ver 1.8
[   33.384000] eth0: no IPv6 routers present
martin@ltop:~/Kallkod/C/ubuntu-gutsy$ 

```

```
martin@ltop:~/Kallkod/C/ubuntu-gutsy$ sudo lspci -v
[sudo] password for martin:
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at f0000000 (64-bit, non-prefetchable) [size=1M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Power Management version 3

00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, fast devsel, latency 0
        Memory at f0100000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 1820 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1840 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, medium devsel, latency 0, IRQ 7
        Memory at f0704000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Unknown (5)

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: f0200000-f02fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [90] Subsystem: Inventec Corporation Unknown device 0040
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel
        Capabilities: [180] Unknown (5)

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [90] Subsystem: Inventec Corporation Unknown device 0040
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel
        Capabilities: [180] Unknown (5)

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: f0300000-f03fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [90] Subsystem: Inventec Corporation Unknown device 0040
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel
        Capabilities: [180] Unknown (5)

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [90] Subsystem: Inventec Corporation Unknown device 0040
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel
        Capabilities: [180] Unknown (5)

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, medium devsel, latency 0, IRQ 6
        I/O ports at 1860 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, medium devsel, latency 0, IRQ 6
        I/O ports at 1880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, medium devsel, latency 0, IRQ 7
        I/O ports at 18a0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, medium devsel, latency 0, IRQ 6
        Memory at f0704400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=0a, sec-latency=56
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: f0400000-f04fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000053ffffff
        Capabilities: [50] Subsystem: Inventec Corporation Unknown device 0040

00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, medium devsel, latency 0, IRQ 255
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]

00:1f.2 IDE interface: Intel Corporation Mobile SATA IDE Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 6
        I/O ports at 1c00 [size=8]
        I/O ports at 18f4 [size=4]
        I/O ports at 18f8 [size=8]
        I/O ports at 18f0 [size=4]
        I/O ports at 18e0 [size=16]
        I/O ports at 18d0 [size=16]
        Capabilities: [70] Power Management version 3

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: medium devsel, IRQ 10
        Memory at 54000000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1c20 [size=32]

02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, fast devsel, latency 0, IRQ 219
        Memory at f0200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [48] Power Management version 3
        Capabilities: [50] Vital Product Data
        Capabilities: [58] Vendor Specific Information
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [d0] Express Endpoint IRQ 0
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [13c] Virtual Channel
        Capabilities: [160] Device Serial Number b0-37-c2-fe-ff-d1-a0-00
        Capabilities: [16c] Power Budgeting

04:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
        Subsystem: Intel Corporation Unknown device 1101
        Flags: bus master, fast devsel, latency 0, IRQ 7
        Memory at f0300000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [c8] Power Management version 3
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Endpoint IRQ 0
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Device Serial Number fb-62-24-ff-ff-e8-13-00

06:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, medium devsel, latency 168, IRQ 7
        Memory at f0404000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 50000000-53fff000 (prefetchable)
        Memory window 1: 58000000-5bfff000
        I/O window 0: 00002000-000020ff
        I/O window 1: 00002400-000024ff
        16-bit legacy interface ports at 0001

06:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, medium devsel, latency 32, IRQ 7
        Memory at f0406000 (32-bit, non-prefetchable) [size=2K]
        Memory at f0400000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

06:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, medium devsel, latency 57, IRQ 7
        Memory at f0405000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

06:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, medium devsel, latency 57, IRQ 7
        Memory at f0406800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

martin@ltop:~/Kallkod/C/ubuntu-gutsy$ 

```

Thank you for taking the time to read this

---

### Post by TradiZ on 2007-08-19
I have the exact same problem,

Tried Gutsy trib4, now back in Fiesty.

Cdrom is fully functional at setup, but when logged in, nothing,  

mount: special device /dev/hda does not exist.

I am on the Santa Rosa Platform.

Also, Sound does not work but have not tried to figure that out yet.

My cdrom is IDE, my Hdd is Sata...

Any Ideas?


Regards
T

---

### Post by binger on 2007-08-23
I am having a very similar problem on my laptop.  my cd/dvd drive will boot to a disc but when I get into win xp for fiesty there is nothing connected to the SATA controller but my hard drive.  this started when I installed fiesty.  I found out today that its not the hardware, for I bought another drive which didn't fix the problem.

---

### Post by TradiZ on 2007-08-23
Hi,

Here is the solution: [http://bugzilla.kernel.org/show_bug.cgi?id=8835](http://bugzilla.kernel.org/show_bug.cgi?id=8835)
In order to apply the patch you need your kernel sources, and re-compile the kernel you have.

OR make a kernel update from kernel.org to at least 2.6.22.3

Vanilla kernel guide: [http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)

It worked for me, BUT, regardless of if you have a SATA or PATA Cdrom, it only worked when I changed fstab to /dev/scd0 

TradiZ

---

