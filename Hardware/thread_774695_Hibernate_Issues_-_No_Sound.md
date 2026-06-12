---
title: "Hibernate Issues - No Sound"
date: 2008-04-29
forum: Hardware
---

### Post by El Chupacabras on 2008-04-29
I finally upgraded to Hardy Heron from Gutsy the other day, and when I hibernated my Desktop, I was so happy to find out that it didn't freeze, as it did in Gutsy. However, I noticed that the swap space was significantly used (I cleared it with a script I wrote in order to speed up the cached memory). I figured that it was no big deal, used my computer as normal, and then finished. 

Rather than waiting for it to boot again, I decided to hibernate again. When I turned it back on today, I received a small pop-up warning, saying something like "Ubuntu failed to suspend correctly. See The Help for more info." I'd already seen this before when this used to happen in Feisty, so I decided to do a quick [FONT="Fixedsys"]$ dmesg > dmesg.log[/FONT], so that I could ask what was wrong on the forums. As I started up Firefox, I opened rhythmbox and realized I had no audio. Mplayer has no audio. I checked the headphone jack on my computer with my headphones. No Audio. 

I did [FONT="Fixedsys"]dmesg | grep nvidia[/FONT], as my sound chip is branded NVidia. I got this:
```
[    0.000000] ACPI: RSDP 000F7BC0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 3FEE3040, 0034 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FEE30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: MCFG 3FEE97C0, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 3FEE95C0, 0072 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
```
Perhaps the ACPI timer override is what is causing this?

In case this needs to be seen in context, here is my [FONT="Fixedsys"]dmesg[/FONT] log. I cut out some parts from before I hibernated, (especially the part with my Mac Address and Local IP address) as it was mostly just logs from my Wireless Card's driver.
```
[    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] Command line: root=UUID=f4b9dab6-9ea6-4410-aad4-a8f942e2533b ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
[    0.000000]  BIOS-e820: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261856) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7BC0 checksum 0
[    0.000000] ACPI: RSDP 000F7BC0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 3FEE3040, 0034 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FEE30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FEE3180, 63FD (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FEE0000, 0040
[    0.000000] ACPI: SSDT 3FEE9680, 00F7 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: MCFG 3FEE97C0, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 3FEE95C0, 0072 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 1 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003fee0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 261856) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000003fee0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   261856
[    0.000000] On node 0 totalpages: 261759
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1222 pages reserved
[    0.000000]   DMA zone: 2721 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3524 pages used for memmap
[    0.000000]   DMA32 zone: 254236 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 256957
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=f4b9dab6-9ea6-4410-aad4-a8f942e2533b ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[   22.982256] time.c: Detected 2210.182 MHz processor.
[   22.983681] Console: colour VGA+ 80x25
[   22.983684] console [tty0] enabled
[   22.983698] Checking aperture...
[   22.983700] CPU 0: aperture @ 8082000000 size 32 MB
[   22.983701] Aperture too small (32 MB)
[   22.990259] No AGP bridge found
[   22.997875] Memory: 1020192k/1047424k available (2466k kernel code, 26844k reserved, 1309k data, 316k init)
[   22.997906] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   23.076184] Calibrating delay using timer specific routine.. 4424.23 BogoMIPS (lpj=8848475)
[   23.076211] Security Framework initialized
[   23.076216] SELinux:  Disabled at boot.
[   23.076228] AppArmor: AppArmor initialized
[   23.076231] Failure registering capabilities with primary security module.
[   23.076310] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   23.076823] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   23.077067] Mount-cache hash table entries: 256
[   23.077179] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   23.077181] CPU: L2 Cache: 512K (64 bytes/line)
[   23.077183] CPU 0/0 -> Node 0
[   23.077203] SMP alternatives: switching to UP code
[   23.077804] Early unpacking initramfs... done
[   23.351706] ACPI: Core revision 20070126
[   23.351757] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   23.397279] Using local APIC timer interrupts.
[   23.442497] APIC timer calibration result 12557855
[   23.442499] Detected 12.557 MHz APIC timer.
[   23.442546] Brought up 1 CPUs
[   23.442657] CPU0 attaching sched-domain:
[   23.442659]  domain 0: span 01
[   23.442660]   groups: 01
[   23.442788] net_namespace: 120 bytes
[   23.443156] Time: 19:50:11  Date: 04/28/08
[   23.443180] NET: Registered protocol family 16
[   23.443322] ACPI: bus type pci registered
[   23.443378] PCI: Using configuration type 1
[   23.444489] ACPI: EC: Look up EC in DSDT
[   23.450868] ACPI: Interpreter enabled
[   23.450871] ACPI: (supports S0 S3 S4 S5)
[   23.450882] ACPI: Using IOAPIC for interrupt routing
[   23.460170] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.461155] PCI: Transparent bridge - 0000:00:10.0
[   23.461171] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.461456] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   23.552529] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
[   23.552720] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.552911] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 *10 11 14 15)
[   23.553101] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)
[   23.553291] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 *11 14 15)
[   23.553480] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.553669] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.553859] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.554049] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[   23.554238] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.554429] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
[   23.554622] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.554812] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[   23.555003] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 *11 14 15)
[   23.555194] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.555385] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   23.555575] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[   23.555770] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.555961] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   23.556156] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   23.556377] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   23.556593] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   23.556808] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   23.557022] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   23.557237] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[   23.557451] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   23.557666] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   23.557881] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   23.558096] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   23.558311] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   23.558532] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   23.558747] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   23.558962] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0
[   23.559178] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   23.559394] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   23.559610] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   23.559825] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   23.560041] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   23.560257] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   23.560476] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   23.560692] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[   23.560810] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.560832] pnp: PnP ACPI init
[   23.560839] ACPI: bus type pnp registered
[   23.565731] pnpacpi: exceeded the max number of mem resources: 12
[   23.565784] pnp: PnP ACPI: found 12 devices
[   23.565786] ACPI: ACPI bus type pnp unregistered
[   23.565966] PCI: Using ACPI for IRQ routing
[   23.565969] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.574451] NET: Registered protocol family 8
[   23.574452] NET: Registered protocol family 20
[   23.574547] AppArmor: AppArmor Filesystem Enabled
[   23.578423] Time: tsc clocksource has been installed.
[   23.586444] system 00:01: ioport range 0x1000-0x107f has been reserved
[   23.586447] system 00:01: ioport range 0x1080-0x10ff has been reserved
[   23.586449] system 00:01: ioport range 0x1400-0x147f has been reserved
[   23.586451] system 00:01: ioport range 0x1480-0x14ff has been reserved
[   23.586453] system 00:01: ioport range 0x1800-0x187f has been reserved
[   23.586455] system 00:01: ioport range 0x1880-0x18ff has been reserved
[   23.586457] system 00:01: ioport range 0x2000-0x207f has been reserved
[   23.586459] system 00:01: ioport range 0x2080-0x20ff has been reserved
[   23.586462] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[   23.586464] system 00:01: iomem range 0x0-0x0 could not be reserved
[   23.586470] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   23.586473] system 00:02: ioport range 0x800-0x87f has been reserved
[   23.586480] system 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
[   23.586484] system 00:0b: iomem range 0xd1800-0xd3fff has been reserved
[   23.586486] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
[   23.586488] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[   23.586491] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[   23.586493] system 00:0b: iomem range 0x3fee0000-0x3fefffff could not be reserved
[   23.586495] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
[   23.586497] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   23.586499] system 00:0b: iomem range 0x100000-0x3fedffff could not be reserved
[   23.586502] system 00:0b: iomem range 0x0-0x0 could not be reserved
[   23.586504] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[   23.586506] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[   23.586508] system 00:0b: iomem range 0xfefff000-0xfeffffff has been reserved
[   23.586815] PCI: Bridge: 0000:00:02.0
[   23.586817]   IO window: c000-cfff
[   23.586819]   MEM window: fda00000-fdafffff
[   23.586821]   PREFETCH window: fd900000-fd9fffff
[   23.586823] PCI: Bridge: 0000:00:03.0
[   23.586824]   IO window: b000-bfff
[   23.586826]   MEM window: fde00000-fdefffff
[   23.586827]   PREFETCH window: fdd00000-fddfffff
[   23.586831] PCI: Bridge: 0000:00:04.0
[   23.586832]   IO window: 9000-9fff
[   23.586834]   MEM window: fa000000-fcffffff
[   23.586836]   PREFETCH window: d0000000-dfffffff
[   23.586838] PCI: Bridge: 0000:00:10.0
[   23.586840]   IO window: a000-afff
[   23.586842]   MEM window: fdc00000-fdcfffff
[   23.586845]   PREFETCH window: fdb00000-fdbfffff
[   23.586856] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   23.586861] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   23.586866] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   23.586872] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   23.586881] NET: Registered protocol family 2
[   23.622465] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   23.622839] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   23.623841] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   23.624329] TCP: Hash tables configured (established 131072 bind 65536)
[   23.624332] TCP reno registered
[   23.634510] checking if image is initramfs... it is
[   24.090086] Switched to high resolution mode on CPU 0
[   24.182010] Freeing initrd memory: 7512k freed
[   24.186340] audit: initializing netlink socket (disabled)
[   24.186350] audit(1209412212.172:1): initialized
[   24.187864] VFS: Disk quotas dquot_6.5.1
[   24.187919] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   24.188022] io scheduler noop registered
[   24.188024] io scheduler anticipatory registered
[   24.188026] io scheduler deadline registered
[   24.188108] io scheduler cfq registered (default)
[   32.196155] 0000:00:0b.1 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   32.196237] Boot video device is 0000:03:00.0
[   32.196369] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   32.196386] assign_interrupt_mode Found MSI capability
[   32.196401] Allocate Port Service[0000:00:02.0:pcie00]
[   32.196447] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   32.196464] assign_interrupt_mode Found MSI capability
[   32.196476] Allocate Port Service[0000:00:03.0:pcie00]
[   32.196518] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   32.196534] assign_interrupt_mode Found MSI capability
[   32.196546] Allocate Port Service[0000:00:04.0:pcie00]
[   32.218242] Real Time Clock Driver v1.12ac
[   32.218326] Linux agpgart interface v0.102
[   32.218329] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   32.218450] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   32.218907] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   32.219476] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   32.219528] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   32.219591] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   32.219593] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   32.220096] serio: i8042 KBD port at 0x60,0x64 irq 1
[   32.224519] mice: PS/2 mouse device common for all mice
[   32.224549] cpuidle: using governor ladder
[   32.224551] cpuidle: using governor menu
[   32.224673] NET: Registered protocol family 1
[   32.224719] registered taskstats version 1
[   32.224843]   Magic number: 4:894:850
[   32.224908]   hash matches device ptyv2
[   32.224958] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   32.224961] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   32.224963] EDD information not available.
[   32.224969] Freeing unused kernel memory: 316k freed
[   32.252128] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   33.386525] fuse init (API version 7.9)
[   33.397286] ACPI: Fan [FAN] (on)
[   33.401071] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   33.404886] ACPI: Thermal Zone [THRM] (40 C)
[   34.175305] usbcore: registered new interface driver usbfs
[   34.175323] usbcore: registered new interface driver hub
[   34.184843] usbcore: registered new device driver usb
[   34.204800] SCSI subsystem initialized
[   34.225377] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   34.225777] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   34.225787] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 23
[   34.225855] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   34.225861] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   34.226032] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   34.226050] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xfe02f000
[   34.254254] libata version 3.00 loaded.
[   34.280782] usb usb1: configuration #1 chosen from 1 choice
[   34.280804] hub 1-0:1.0: USB hub found
[   34.280812] hub 1-0:1.0: 8 ports detected
[   34.383156] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   34.383166] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 22
[   34.383242] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   34.383248] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   34.383290] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   34.383316] ehci_hcd 0000:00:0b.1: debug port 1
[   34.383320] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   34.383331] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xfe02e000
[   34.394571] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.394672] usb usb2: configuration #1 chosen from 1 choice
[   34.394690] hub 2-0:1.0: USB hub found
[   34.394696] hub 2-0:1.0: 8 ports detected
[   34.500486] sata_nv 0000:00:0e.0: version 3.5
[   34.500853] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   34.500863] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 21
[   34.500952] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   34.502657] scsi0 : sata_nv
[   34.503294] scsi1 : sata_nv
[   34.503476] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 21
[   34.503479] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 21
[   34.814284] ata1: SATA link down (SStatus 0 SControl 300)
[   35.134023] ata2: SATA link down (SStatus 0 SControl 300)
[   35.146034] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   35.146406] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[   35.146415] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 20 (level, low) -> IRQ 20
[   35.146420] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   35.666021] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x50ef @ 1, addr 00:40:ca:b2:52:e3
[   35.666026] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[   35.666664] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   35.666674] ACPI: PCI Interrupt 0000:04:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   35.719800] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fdcff000-fdcff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   35.724859] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   35.726235] usb 1-3: new low speed USB device using ohci_hcd and address 2
[   35.729833] pata_amd 0000:00:0d.0: version 0.3.10
[   35.729872] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   35.730859] scsi2 : pata_amd
[   35.731209] scsi3 : pata_amd
[   35.731898] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[   35.731901] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[   35.901921] ata3.00: ATA-7: HDT722520DLAT80, V44OA70A, max UDMA/133
[   35.901924] ata3.00: 390721968 sectors, multi 16: LBA48 
[   35.933626] ata3.01: ATA-7: ST3120814A, 3.AAD, max UDMA/100
[   35.933629] ata3.01: 234441648 sectors, multi 16: LBA48 
[   35.937640] usb 1-3: configuration #1 chosen from 1 choice
[   35.949861] ata3.00: configured for UDMA/133
[   36.008739] ata3.01: configured for UDMA/100
[   36.241216] usb 1-4: new low speed USB device using ohci_hcd and address 3
[   36.365420] ata4.00: ATAPI: TSSTcorpCD/DVDW TS-H552D, GA01, max UDMA/33
[   36.456296] usb 1-4: configuration #1 chosen from 1 choice
[   36.577212] ata4.00: configured for UDMA/33
[   36.577300] scsi 2:0:0:0: Direct-Access     ATA      HDT722520DLAT80  V44O PQ: 0 ANSI: 5
[   36.577624] scsi 2:0:1:0: Direct-Access     ATA      ST3120814A       3.AA PQ: 0 ANSI: 5
[   36.578600] scsi 3:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H552D GA01 PQ: 0 ANSI: 5
[   36.585648] Driver 'sd' needs updating - please use bus_type methods
[   36.585716] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   36.585726] sd 2:0:0:0: [sda] Write Protect is off
[   36.585728] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   36.585740] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.585774] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   36.585781] sd 2:0:0:0: [sda] Write Protect is off
[   36.585783] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   36.585793] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.585796]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   36.594521]  sda1 sda2
[   36.594583] sd 2:0:0:0: [sda] Attached SCSI disk
[   36.594636] sd 2:0:1:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   36.594646] sd 2:0:1:0: [sdb] Write Protect is off
[   36.594648] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   36.594661] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.594699] sd 2:0:1:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   36.594706] sd 2:0:1:0: [sdb] Write Protect is off
[   36.594709] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   36.594719] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.594723]  sdb: sdb1 sdb2 sdb3
[   36.640367] sd 2:0:1:0: [sdb] Attached SCSI disk
[   36.647282] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   36.647298] sd 2:0:1:0: Attached scsi generic sg1 type 0
[   36.647311] sr 3:0:0:0: Attached scsi generic sg2 type 5
[   36.656532] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   36.656536] Uniform CD-ROM driver Revision: 3.20
[   36.656579] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   36.760843] usb 1-5: new full speed USB device using ohci_hcd and address 4
[   36.976022] usb 1-5: configuration #1 chosen from 1 choice
[   36.978992] usbcore: registered new interface driver hiddev
[   36.984022] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.0/input/input2
[   36.992737] input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:0b.0-4
[   36.992754] usbcore: registered new interface driver usbhid
[   36.992757] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   36.993964] usbcore: registered new interface driver libusual
[   36.996887] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0040ca070303b4b3]
[   36.998544] Initializing USB Mass Storage driver...
[   37.008292] scsi4 : SCSI emulation for USB Mass Storage devices
[   37.009031] usbcore: registered new interface driver usb-storage
[   37.009036] USB Mass Storage support registered.
[   37.009122] usb-storage: device found at 4
[   37.009124] usb-storage: waiting for device to settle before scanning
[   37.214097] Attempting manual resume
[   37.214100] swsusp: Resume From Partition 8:19
[   37.214102] PM: Checking swsusp image.
[   37.214252] PM: Resume from disk failed.
[   37.224735] EXT3-fs: INFO: recovery required on readonly filesystem.
[   37.224739] EXT3-fs: write access will be enabled during recovery.
[   42.006587] usb-storage: device scan complete
[   42.013566] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   42.020561] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   42.027555] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   42.034550] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   42.045590] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   42.045621] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   42.057595] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[   42.057629] sd 4:0:0:1: Attached scsi generic sg4 type 0
[   42.068590] sd 4:0:0:2: [sde] Attached SCSI removable disk
[   42.068623] sd 4:0:0:2: Attached scsi generic sg5 type 0
[   42.079604] sd 4:0:0:3: [sdf] Attached SCSI removable disk
[   42.079643] sd 4:0:0:3: Attached scsi generic sg6 type 0
[   48.490116] kjournald starting.  Commit interval 5 seconds
[   48.490131] EXT3-fs: sdb1: orphan cleanup on readonly fs
[   48.490136] ext3_orphan_cleanup: deleting unreferenced inode 7929869
[   48.490171] EXT3-fs: sdb1: 1 orphan inode deleted
[   48.490173] EXT3-fs: recovery complete.
[   48.524277] EXT3-fs: mounted filesystem with ordered data mode.
[   54.763767] ip_tables: (C) 2000-2006 Netfilter Core Team
[   54.846820] nf_conntrack version 0.5.0 (8192 buckets, 32768 max)
[   55.823116] input: Power Button (FF) as /devices/virtual/input/input3
[   55.838973] ACPI: Power Button (FF) [PWRF]
[   55.839067] input: Power Button (CM) as /devices/virtual/input/input4
[   55.854959] ACPI: Power Button (CM) [PWRB]
[   56.126791] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   56.181802] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   56.294802] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   56.294824] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   58.388410] nvidia: module license 'NVIDIA' taints kernel.
[   58.896873] input: Wacom Graphire3 as /devices/pci0000:00/0000:00:0b.0/usb1/1-3/1-3:1.0/input/input5
[   58.916741] usbcore: registered new interface driver wacom
[   58.916747] /build/buildd/linux-2.6.24/drivers/input/tablet/wacom_sys.c: v1.47:USB Wacom Graphire and Wacom Intuos tablet driver
[   58.946745] eth0: no link during initialization.
[   59.136126] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   59.324474] wlan: 0.9.4
[   59.376433] ath_pci: 0.9.4
[   59.376846] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   59.376855] ACPI: PCI Interrupt 0000:04:06.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   60.227703] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   60.687299] parport_pc 00:08: reported by Plug and Play ACPI
[   60.687329] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   61.221360] ath_rate_sample: 1.2 (0.9.4)
[   61.221763] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   61.221767] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   61.221773] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   61.221775] wifi0: mac 7.8 phy 4.5 radio 5.6
[   61.221778] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   61.221780] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   61.221781] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   61.221783] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   61.221784] wifi0: Use hw queue 8 for CAB traffic
[   61.221786] wifi0: Use hw queue 9 for beacons
[   61.235627] wifi0: Atheros 5212: mem=0xfdcd0000, irq=18
[   61.236021] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   61.236024] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 23 (level, low) -> IRQ 23
[   61.236103] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   61.269500] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   61.301407] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   61.301412] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 16
[   61.301418] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   61.301556] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   62.552845] lp0: using parport0 (interrupt-driven).
[   62.712195] Adding 2096472k swap on /dev/sdb3.  Priority:-1 extents:1 across:2096472k
[   63.246848] EXT3 FS on sdb1, internal journal
[   84.641048] kjournald starting.  Commit interval 5 seconds
[   84.641191] EXT3 FS on sdb2, internal journal
[   84.641195] EXT3-fs: mounted filesystem with ordered data mode.
[   85.645624] No dock devices found.
[   85.956137] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (1 cpu cores) (version 2.20.00)
[   85.956170] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
[   85.956172] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
[   85.956174] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[   85.956176] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   88.371744] Marking TSC unstable due to cpufreq changes
[   88.375298] Time: acpi_pm clocksource has been installed.
[   88.449802] Clocksource tsc unstable (delta = -93813731 ns)
[   88.677209] ppdev: user-space parallel port driver
[   89.567533] audit(1209426679.589:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6393 profile="/usr/sbin/cupsd" namespace="default"
[   98.704844] NET: Registered protocol family 10
[   98.705332] lo: Disabled Privacy Extensions
[   98.706007] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  104.377718] ath0: no IPv6 routers present
[  112.113871] NET: Registered protocol family 17
[  141.117746] Inbound IN=eth0 OUT= MAC= SRC=192.168.0.1 DST=192.168.0.255 LEN=265 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=245 
[  141.497418] ath0: no IPv6 routers present
<< Wireless Driver Logging goes here. Removed due to Privacy concerns. >>
[ 4916.253901] ACPI: PCI interrupt for device 0000:04:06.0 disabled
[ 4916.253932] ath_pci: driver unloaded
[ 4916.363818] ACPI: PCI interrupt for device 0000:00:14.0 disabled
[ 4916.920921] PM: suspend-to-disk mode set to 'platform'
[ 4916.924441] swsusp: Marking nosave pages: 000000000009f000 - 0000000000100000
[ 4916.924448] swsusp: Basic memory bitmaps created
[ 4916.924450] Syncing filesystems ... done.
[ 4916.928592] Freezing user space processes ... (elapsed 0.02 seconds) done.
[ 4916.954181] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 4916.954210] Shrinking memory...  -\|/-\|/-\|done (124282 pages freed)
[ 4925.594658] Freed 497128 kbytes in 8.64 seconds (57.53 MB/s)
[ 4925.594660] Suspending console(s)
[ 4925.794856] sd 2:0:1:0: [sdb] Synchronizing SCSI cache
[ 4925.794966] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[ 4925.809128] wacom 1-3:1.0: no suspend for driver wacom?
[ 4925.809262] ACPI handle has no context!
[ 4925.809519] parport_pc 00:08: disabled
[ 4925.809740] serial 00:07: disabled
[ 4925.814802] ACPI handle has no context!
[ 4925.826873] ACPI handle has no context!
[ 4925.826889] NVRM: RmPowerManagement: 3
[ 4926.182601] ACPI: PCI interrupt for device 0000:00:10.1 disabled
[ 4926.198622] ACPI: PCI interrupt for device 0000:00:0e.0 disabled
[ 4926.198683] ACPI: PCI interrupt for device 0000:00:0b.1 disabled
[ 4926.214581] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
[ 4926.348195] Disabling non-boot CPUs ...
[ 4926.348431] swsusp: critical section: 
[ 4926.389086] swsusp: Need to copy 122025 pages
[ 4926.389089] swsusp: Normal pages needed: 122025 + 1024 + 22, available pages: 139733
[   60.796607] ACPI: Unable to turn cooling device [ffff81003edb7f60] 'off'
[   60.796686] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   60.796703] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   60.796718] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   60.811044] PCI: Enabling device 0000:00:0b.0 (0000 -> 0002)
[   60.811048] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 23
[   60.811053] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   60.811059] PM: Writing back config space on device 0000:00:0b.0 at offset f (was 1030100, writing 103010b)
[   60.811067] PM: Writing back config space on device 0000:00:0b.0 at offset 4 (was 0, writing fe02f000)
[   60.811072] PM: Writing back config space on device 0000:00:0b.0 at offset 1 (was b00006, writing b00007)
[   60.851014] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 22
[   60.851018] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   60.851036] usb usb2: root hub lost power or was reset
[   60.851044] ehci_hcd 0000:00:0b.1: debug port 1
[   60.851047] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   60.970944] PM: Writing back config space on device 0000:00:0d.0 at offset 1 (was b00001, writing b00005)
[   60.970953] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   60.972718] PM: Writing back config space on device 0000:00:0e.0 at offset 1 (was b00003, writing b00007)
[   60.972729] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 21
[   60.972733] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   60.974058] PM: Writing back config space on device 0000:00:10.0 at offset 7 (was 280a0a0, writing 8280a0a0)
[   60.974071] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   60.986928] PM: Writing back config space on device 0000:00:10.1 at offset 1 (was b00006, writing b00002)
[   60.986940] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 23 (level, low) -> IRQ 23
[   60.986944] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   61.083572] PM: Writing back config space on device 0000:00:14.0 at offset 1 (was b00007, writing b00003)
[   61.083613] NVRM: RmPowerManagement: 5
[   61.194022] ata3.01: ACPI cmd ef/03:45:00:00:00:b0 filtered out
[   61.194026] ata3.01: ACPI cmd ef/03:0c:00:00:00:b0 filtered out
[   61.195665] PM: Writing back config space on device 0000:04:06.0 at offset 3 (was 2008, writing a808)
[   61.195672] PM: Writing back config space on device 0000:04:06.0 at offset 1 (was 2900006, writing 2900002)
[   61.263814] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fdcff000-fdcff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   61.271814] serial 00:07: activated
[   61.272482] parport_pc 00:08: activated
[   61.272490] i8042 kbd 00:09: activation failed
[   61.278993] ata3.00: ACPI cmd ef/03:46:00:00:00:a0 filtered out
[   61.278996] ata3.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[   61.294697] ata1: SATA link down (SStatus 0 SControl 300)
[   61.305211] ata2: SATA link down (SStatus 0 SControl 300)
[   61.316213] ata3.00: configured for UDMA/133
[   61.362941] ata4.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[   61.362943] ata4.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[   61.363020] ata3.01: configured for UDMA/100
[   61.363049] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   61.363058] sd 2:0:0:0: [sda] Write Protect is off
[   61.363059] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   61.363071] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   61.363084] sd 2:0:1:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   61.363091] sd 2:0:1:0: [sdb] Write Protect is off
[   61.363092] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   61.363102] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   61.363113] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   61.363119] sd 2:0:0:0: [sda] Write Protect is off
[   61.363121] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   61.363130] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   61.363141] sd 2:0:1:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[   61.363147] sd 2:0:1:0: [sdb] Write Protect is off
[   61.363149] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   61.363159] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   61.380656] usb usb1: root hub lost power or was reset
[   61.574714] ata4.00: configured for UDMA/33
[   61.646441] sd 2:0:0:0: [sda] Starting disk
[   61.652496] sd 2:0:1:0: [sdb] Starting disk
[   61.678016] PM: Image restored successfully.
[   61.711739] Restarting tasks ... <6>usb 1-3: USB disconnect, address 2
[   61.713269] done.
[   61.713277] swsusp: Basic memory bitmaps freed
[   62.038211] usb 1-3: new low speed USB device using ohci_hcd and address 5
[   62.250152] usb 1-3: configuration #1 chosen from 1 choice
[   62.253131] input: Wacom Graphire3 as /devices/pci0000:00/0000:00:0b.0/usb1/1-3/1-3:1.0/input/input7
[   62.278093] usb 1-4: USB disconnect, address 3
[   62.605751] usb 1-4: new low speed USB device using ohci_hcd and address 6
[   62.819765] usb 1-4: configuration #1 chosen from 1 choice
[   62.829823] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.0/input/input8
[   62.853590] input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:0b.0-4
[   62.853632] usb 1-5: USB disconnect, address 4
[   63.157347] usb 1-5: new full speed USB device using ohci_hcd and address 7
[   63.372392] usb 1-5: configuration #1 chosen from 1 choice
[   63.375403] scsi5 : SCSI emulation for USB Mass Storage devices
[   63.375543] usb-storage: device found at 7
[   63.375545] usb-storage: waiting for device to settle before scanning
[   68.371025] usb-storage: device scan complete
[   68.378000] scsi 5:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   68.385001] scsi 5:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   68.391997] scsi 5:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   68.398993] scsi 5:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   68.410016] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[   68.410046] sd 5:0:0:0: Attached scsi generic sg3 type 0
[   68.420990] sd 5:0:0:1: [sdd] Attached SCSI removable disk
[   68.421017] sd 5:0:0:1: Attached scsi generic sg4 type 0
[   68.431990] sd 5:0:0:2: [sde] Attached SCSI removable disk
[   68.432013] sd 5:0:0:2: Attached scsi generic sg5 type 0
[   68.442981] sd 5:0:0:3: [sdf] Attached SCSI removable disk
[   68.443011] sd 5:0:0:3: Attached scsi generic sg6 type 0
[   76.970302] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   76.970321] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 20 (level, low) -> IRQ 20
[   76.970326] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   77.440782] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x50ef @ 1, addr 00:40:ca:b2:52:e3
[   77.440788] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[   77.581294] ath_pci: 0.9.4
[   77.581343] ACPI: PCI Interrupt 0000:04:06.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   78.097114] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   78.097122] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   78.097128] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   78.097131] wifi0: mac 7.8 phy 4.5 radio 5.6
[   78.097137] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   78.097139] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   78.097140] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   78.097142] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   78.097143] wifi0: Use hw queue 8 for CAB traffic
[   78.097144] wifi0: Use hw queue 9 for beacons
[   78.100147] wifi0: Atheros 5212: mem=0xfdcd0000, irq=18
[   79.508141] eth0: no link during initialization.
[   79.508763] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  248.857916] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  262.754333] ath0: no IPv6 routers present
```

If I can pinpoint the problem, I would like to file a bug, so all help is appreciated. I still know next to nothing about the Kernel, so I guess this can be a learning experience?

EDIT: The same thing happened when I attempted to Suspend =[

---

### Post by El Chupacabras on 2008-06-06
Bump?

Did I bombard you guys with too much information, or something? XD

---

### Post by isparkes on 2008-06-14
I have the same problem on an Acer 5720. So far no idea what is going on.

---

### Post by isparkes on 2008-06-14
OK, followed this:

[http://ubuntuforums.org/showpost.php?p=5017453&postcount=2](http://ubuntuforums.org/showpost.php?p=5017453&postcount=2)

and it solved the problem.

Good luck!

---

### Post by isparkes on 2008-10-21
The problem came back with Hardy, and after a resume from hibernate I was once again without any sound. It's a different problem and is a logged Kernel issue.

My sound card is (using lspci):

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

I'm getting around it by doing this after a resume:

 sudo /sbin/alsa force-reload

but it kills of the volume applet. I just restart it again.

---

