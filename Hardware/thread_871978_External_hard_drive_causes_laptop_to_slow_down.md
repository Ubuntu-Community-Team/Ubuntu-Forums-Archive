---
title: "External hard drive causes laptop to slow down"
date: 2008-07-27
forum: Hardware
---

### Post by purplepaint on 2008-07-27
When I connect my external USB hard drive to my Ubuntu laptop, it causes the computer to slow down and the mouse to become less responsive.  I'm not sure if it's the format (NTFS) or the fact that it's too big, perhaps (120GB).  I don't know if it's relevant, but I have to connect it to an AC power source and switch it on to use it.  Could it be that my laptop's USB ports aren't powering it properly (I don't know much about this stuff, but I've heard that laptop USB ports give out less power than desktop ones)?

---

### Post by argosreality on 2008-07-27
Neither the drive size (120Gb) or the file system should cause any slow down issues with the laptop. NTFS supports quite a bit larger file systems and Ubuntu (latest releases) can write to NTFS without issue as well. It's also quite normal for external hard drives based upon desktop 3.5in drives to require a seperate AC power source. Even many laptop drives cannot run solely off the USB source (or require two connectors)

Whats the rest of the specifications of your computer? CPU, memory, etc.? What version of ubuntu are you using?

---

### Post by purplepaint on 2008-07-28
> **argosreality said:**
> Neither the drive size (120Gb) or the file system should cause any slow down issues with the laptop. NTFS supports quite a bit larger file systems and Ubuntu (latest releases) can write to NTFS without issue as well. It's also quite normal for external hard drives based upon desktop 3.5in drives to require a seperate AC power source. Even many laptop drives cannot run solely off the USB source (or require two connectors)

Whats the rest of the specifications of your computer? CPU, memory, etc.? What version of ubuntu are you using?

I'm using a Dell Inspiron 1525 that came with Ubuntu 7.10 pre-installed which I have since upgraded to 8.04.  It has a 1.8GHz Intel Celeron processor and 2GB of RAM.

---

### Post by argosreality on 2008-07-28
Do you do a fresh install or an inplace upgrade? I've had issues in the past with doing upgrades of Ubuntu and its possible you're running into some kind of an issue with that. Could you post you /var/log/dmesg file?

---

### Post by purplepaint on 2008-07-29
> **argosreality said:**
> Do you do a fresh install or an inplace upgrade? I've had issues in the past with doing upgrades of Ubuntu and its possible you're running into some kind of an issue with that. Could you post you /var/log/dmesg file?

I upgraded through the update manager.

I opened /var/log/dmesg in Gedit and this was displayed:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f66d800 (usable)
[    0.000000]  BIOS-e820: 000000007f66d800 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 521837) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   521837
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   521837
[    0.000000] On node 0 totalpages: 521837
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2284 pages used for memmap
[    0.000000]   HighMem zone: 290177 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FBC60 checksum 0
[    0.000000] ACPI: RSDP 000FBC60, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT 7F66F200, 006C (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: FACP 7F66F09C, 00F4 (r4 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: DSDT 7F66F800, 5495 (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS 7F67E000, 0040
[    0.000000] ACPI: HPET 7F66F300, 0038 (r1 DELL    M08            1 ASL        61)
[    0.000000] ACPI: APIC 7F66F400, 0068 (r1 DELL    M08     27D8030A ASL        47)
[    0.000000] ACPI: MCFG 7F66F3C0, 003E (r16 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: SLIC 7F66F49C, 0024 (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: OSFR 7F66EA00, 002C (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: BOOT 7F66EFC0, 0028 (r1 DELL    M08     27D8030A ASL        61)
[    0.000000] ACPI: SSDT 7F66E25B, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    0.000000] ACPI: SSDT 7F66DD8F, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 7:6 APIC version 20
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
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:78000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517761
[    0.000000] Kernel command line: root=UUID=1dea034e-a9e2-4cdb-9bdb-889631456f67 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1862.023 MHz processor.
[    8.617670] Console: colour VGA+ 80x25
[    8.617674] console [tty0] enabled
[    8.618019] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.618309] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.703240] Memory: 2057520k/2087348k available (2177k kernel code, 28596k reserved, 1006k data, 368k init, 1169844k highmem)
[    8.703247] virtual kernel memory layout:
[    8.703248]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    8.703249]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.703249]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.703250]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.703251]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    8.703252]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[    8.703253]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[    8.703256] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.703300] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    8.703442] hpet clockevent registered
[    8.783312] Calibrating delay using timer specific routine.. 3728.52 BogoMIPS (lpj=7457059)
[    8.783334] Security Framework initialized
[    8.783341] SELinux:  Disabled at boot.
[    8.783354] AppArmor: AppArmor initialized
[    8.783359] Failure registering capabilities with primary security module.
[    8.783367] Mount-cache hash table entries: 512
[    8.783493] Initializing cgroup subsys ns
[    8.783499] Initializing cgroup subsys cpuacct
[    8.783509] CPU: After generic identify, caps: afebfbff 20000000 00000000 00000000 0000e31d 00000000 00000001 00000000
[    8.783516] monitor/mwait feature present.
[    8.783517] using mwait in idle threads.
[    8.783521] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.783523] CPU: L2 cache: 1024K
[    8.783526] CPU: After all inits, caps: afebfbff 20000000 00000000 00003940 0000e31d 00000000 00000001 00000000
[    8.783535] Compat vDSO mapped to ffffe000.
[    8.783548] Checking 'hlt' instruction... OK.
[    8.799671] SMP alternatives: switching to UP code
[    8.801174] Freeing SMP alternatives: 11k freed
[    8.801267] Early unpacking initramfs... done
[    9.109306] ACPI: Core revision 20070126
[    9.109348] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.113945] CPU0: Intel(R) Celeron(R) CPU          540  @ 1.86GHz stepping 01
[    9.113967] Total of 1 processors activated (3728.52 BogoMIPS).
[    9.114167] ENABLING IO-APIC IRQs
[    9.114356] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.258528] Brought up 1 CPUs
[    9.258548] CPU0 attaching sched-domain:
[    9.258551]  domain 0: span 01
[    9.258552]   groups: 01
[    9.258692] net_namespace: 64 bytes
[    9.258702] Booting paravirtualized kernel on bare hardware
[    9.259115] Time: 14:06:24  Date: 07/29/08
[    9.259136] NET: Registered protocol family 16
[    9.259301] EISA bus registered
[    9.259306] ACPI: bus type pci registered
[    9.271181] PCI: PCI BIOS revision 2.10 entry at 0xfad46, last bus=13
[    9.271183] PCI: Using configuration type 1
[    9.271197] Setting up standard PCI resources
[    9.278670] ACPI: EC: Look up EC in DSDT
[    9.278792] ACPI: BIOS _OSI(Linux) query ignored
[    9.278794] ACPI: DMI System Vendor: Dell Inc.
[    9.278795] ACPI: DMI Product Name: Inspiron 1525                   
[    9.278797] ACPI: DMI Product Version: 
[    9.278798] ACPI: DMI Board Name: 0U990C
[    9.278800] ACPI: DMI BIOS Vendor: Dell Inc.
[    9.278801] ACPI: DMI BIOS Date: 03/10/2008
[    9.278802] ACPI: Please send DMI info above to linux-acpi@vger.kernel.org
[    9.278804] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
[    9.288589] ACPI: Interpreter enabled
[    9.288593] ACPI: (supports S0 S3 S4 S5)
[    9.288604] ACPI: Using IOAPIC for interrupt routing
[    9.312704] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.313764] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    9.313769] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    9.315253] PCI: Transparent bridge - 0000:00:1e.0
[    9.315300] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.315731] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    9.315876] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    9.315987] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    9.316098] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    9.326557] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    9.326666] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    9.326771] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
[    9.326867] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
[    9.326973] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    9.327080] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    9.327186] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    9.327283] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    9.327410] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.327437] pnp: PnP ACPI init
[    9.327444] ACPI: bus type pnp registered
[    9.365161] pnpacpi: exceeded the max number of mem resources: 12
[    9.365352] pnp: PnP ACPI: found 13 devices
[    9.365355] ACPI: ACPI bus type pnp unregistered
[    9.365358] PnPBIOS: Disabled by ACPI PNP
[    9.365544] PCI: Using ACPI for IRQ routing
[    9.365547] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.446170] NET: Registered protocol family 8
[    9.446171] NET: Registered protocol family 20
[    9.446203] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    9.446206] hpet0: 3 64-bit timers, 14318180 Hz
[    9.447238] AppArmor: AppArmor Filesystem Enabled
[    9.450156] Time: tsc clocksource has been installed.
[    9.450171] Switched to high resolution mode on CPU 0
[    9.458141] system 00:01: iomem range 0xff800000-0xff8fffff has been reserved
[    9.458144] system 00:01: iomem range 0xffc00000-0xffcfffff has been reserved
[    9.458151] system 00:06: ioport range 0xc80-0xcff could not be reserved
[    9.458157] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[    9.458162] system 00:0a: ioport range 0x900-0x97f has been reserved
[    9.458164] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    9.458167] system 00:0a: ioport range 0x1000-0x1005 has been reserved
[    9.458169] system 00:0a: ioport range 0x1008-0x100f has been reserved
[    9.458174] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
[    9.458176] system 00:0b: ioport range 0x1006-0x1007 has been reserved
[    9.458179] system 00:0b: ioport range 0x100a-0x1059 could not be reserved
[    9.458181] system 00:0b: ioport range 0x1060-0x107f has been reserved
[    9.458183] system 00:0b: ioport range 0x1080-0x10bf has been reserved
[    9.458186] system 00:0b: ioport range 0x10c0-0x10df has been reserved
[    9.458188] system 00:0b: ioport range 0x1010-0x102f has been reserved
[    9.458190] system 00:0b: ioport range 0x809-0x809 has been reserved
[    9.458195] system 00:0c: iomem range 0x0-0x9efff could not be reserved
[    9.458198] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
[    9.458200] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    9.458202] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    9.458205] system 00:0c: iomem range 0x100000-0x7f66d7ff could not be reserved
[    9.458207] system 00:0c: iomem range 0x7f66d800-0x7f6fffff could not be reserved
[    9.458210] system 00:0c: iomem range 0x7f700000-0x7f7fffff could not be reserved
[    9.458212] system 00:0c: iomem range 0x7f700000-0x7fefffff could not be reserved
[    9.458215] system 00:0c: iomem range 0xffe00000-0xffffffff could not be reserved
[    9.458217] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
[    9.458219] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    9.458222] system 00:0c: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    9.488546] PCI: Bridge: 0000:00:1c.0
[    9.488549]   IO window: d000-dfff
[    9.488556]   MEM window: fe800000-fe8fffff
[    9.488560]   PREFETCH window: disabled.
[    9.488566] PCI: Bridge: 0000:00:1c.1
[    9.488568]   IO window: disabled.
[    9.488574]   MEM window: fe700000-fe7fffff
[    9.488578]   PREFETCH window: disabled.
[    9.488584] PCI: Bridge: 0000:00:1c.4
[    9.488587]   IO window: c000-cfff
[    9.488593]   MEM window: fe400000-fe6fffff
[    9.488597]   PREFETCH window: f0000000-f01fffff
[    9.488604] PCI: Bridge: 0000:00:1e.0
[    9.488605]   IO window: disabled.
[    9.488611]   MEM window: fe300000-fe3fffff
[    9.488616]   PREFETCH window: disabled.
[    9.488652] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    9.488659] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.488685] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    9.488691] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.488716] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[    9.488721] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    9.488736] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.488747] NET: Registered protocol family 2
[    9.526045] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.526253] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.526754] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.527101] TCP: Hash tables configured (established 131072 bind 65536)
[    9.527104] TCP reno registered
[    9.538116] checking if image is initramfs... it is
[   10.138882] Freeing initrd memory: 7313k freed
[   10.139045] Simple Boot Flag at 0x79 set to 0x1
[   10.139488] audit: initializing netlink socket (disabled)
[   10.139502] audit(1217340384.328:1): initialized
[   10.139677] highmem bounce pool size: 64 pages
[   10.141382] VFS: Disk quotas dquot_6.5.1
[   10.141447] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.141566] io scheduler noop registered
[   10.141569] io scheduler anticipatory registered
[   10.141570] io scheduler deadline registered
[   10.141579] io scheduler cfq registered (default)
[   10.141590] Boot video device is 0000:00:02.0
[   10.141812] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   10.141876] assign_interrupt_mode Found MSI capability
[   10.141930] Allocate Port Service[0000:00:1c.0:pcie00]
[   10.141960] Allocate Port Service[0000:00:1c.0:pcie02]
[   10.142069] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   10.142132] assign_interrupt_mode Found MSI capability
[   10.142182] Allocate Port Service[0000:00:1c.1:pcie00]
[   10.142210] Allocate Port Service[0000:00:1c.1:pcie02]
[   10.142314] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   10.142377] assign_interrupt_mode Found MSI capability
[   10.142427] Allocate Port Service[0000:00:1c.4:pcie00]
[   10.142455] Allocate Port Service[0000:00:1c.4:pcie02]
[   10.142689] isapnp: Scanning for PnP cards...
[   10.496626] isapnp: No Plug & Play device found
[   10.519764] Real Time Clock Driver v1.12ac
[   10.519901] hpet_resources: 0xfed00000 is busy
[   10.519941] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.520989] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.521047] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   10.521133] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.538296] i8042.c: Detected active multiplexing controller, rev 1.1.
[   10.549616] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.549620] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   10.549622] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   10.549624] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   10.549626] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   10.560243] mice: PS/2 mouse device common for all mice
[   10.560341] EISA: Probing bus 0 at eisa.0
[   10.560349] Cannot allocate resource for EISA slot 1
[   10.560379] EISA: Detected 0 cards.
[   10.560381] cpuidle: using governor ladder
[   10.560383] cpuidle: using governor menu
[   10.560457] NET: Registered protocol family 1
[   10.560482] Using IPI No-Shortcut mode
[   10.560509] registered taskstats version 1
[   10.560622]   Magic number: 0:734:132
[   10.560697]   hash matches device device:07
[   10.560703] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   10.560704] EDD information not available.
[   10.560879] Freeing unused kernel memory: 368k freed
[   10.588151] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   11.825109] fuse init (API version 7.9)
[   11.848145] Monitor-Mwait will be used to enter C-1 state
[   11.848149] Monitor-Mwait will be used to enter C-2 state
[   11.848151] Monitor-Mwait will be used to enter C-3 state
[   11.848258] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   11.848262] ACPI: Processor [CPU0] (supports 8 throttling states)
[   11.848276] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   11.849409] ACPI: Thermal Zone [THM] (31 C)
[   12.432946] usbcore: registered new interface driver usbfs
[   12.432968] usbcore: registered new interface driver hub
[   12.438354] usbcore: registered new device driver usb
[   12.445613] USB Universal Host Controller Interface driver v3.0
[   12.445666] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 18
[   12.445677] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   12.445682] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   12.445902] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   12.445936] uhci_hcd 0000:00:1a.0: irq 18, io base 0x00006f20
[   12.446057] usb usb1: configuration #1 chosen from 1 choice
[   12.446077] hub 1-0:1.0: USB hub found
[   12.446081] hub 1-0:1.0: 2 ports detected
[   12.548785] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 19
[   12.548797] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   12.548802] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   12.548824] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   12.548856] uhci_hcd 0000:00:1a.1: irq 19, io base 0x00006f00
[   12.548957] usb usb2: configuration #1 chosen from 1 choice
[   12.548976] hub 2-0:1.0: USB hub found
[   12.548980] hub 2-0:1.0: 2 ports detected
[   12.652608] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
[   12.652621] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   12.652625] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   12.652648] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   12.652679] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00006f80
[   12.652780] usb usb3: configuration #1 chosen from 1 choice
[   12.652799] hub 3-0:1.0: USB hub found
[   12.652804] hub 3-0:1.0: 2 ports detected
[   12.653012] SCSI subsystem initialized
[   12.696795] libata version 3.00 loaded.
[   12.756414] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 19
[   12.756427] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   12.756432] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   12.756453] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   12.756483] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00006f60
[   12.756586] usb usb4: configuration #1 chosen from 1 choice
[   12.756610] hub 4-0:1.0: USB hub found
[   12.756615] hub 4-0:1.0: 2 ports detected
[   12.860230] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 20
[   12.860242] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   12.860247] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   12.860268] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   12.860301] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00006f40
[   12.860404] usb usb5: configuration #1 chosen from 1 choice
[   12.860424] hub 5-0:1.0: USB hub found
[   12.860428] hub 5-0:1.0: 2 ports detected
[   12.964156] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 20
[   12.964171] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   12.964175] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   12.964200] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   12.968111] ehci_hcd 0000:00:1a.7: debug port 1
[   12.968119] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   12.968124] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfed1c400
[   12.983913] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.984025] usb usb6: configuration #1 chosen from 1 choice
[   12.984047] hub 6-0:1.0: USB hub found
[   12.984053] hub 6-0:1.0: 4 ports detected
[   13.087849] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
[   13.087865] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.087869] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.087891] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   13.091793] ehci_hcd 0000:00:1d.7: debug port 1
[   13.091800] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   13.091806] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xfed1c000
[   13.107713] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.107823] usb usb7: configuration #1 chosen from 1 choice
[   13.107845] hub 7-0:1.0: USB hub found
[   13.107850] hub 7-0:1.0: 6 ports detected
[   13.211770] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.264454] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fe3ff800-fe3fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   13.274493] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   13.274530] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   13.274543] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   13.277012] ahci 0000:00:1f.2: version 3.0
[   13.277039] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   13.277087] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x5) don't match, using nr_ports
[   13.277089] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   13.802463] Clocksource tsc unstable (delta = -23623699122 ns)
[   13.806616] Time: hpet clocksource has been installed.
[   13.820205] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   13.820209] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   13.820215] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   13.820431] scsi0 : ahci
[   13.820639] scsi1 : ahci
[   13.820762] scsi2 : ahci
[   13.821007] ata1: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fb900 irq 220
[   13.821011] ata2: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fb980 irq 220
[   13.821014] ata3: SATA max UDMA/133 abar m2048@0xfe9fb800 port 0xfe9fba00 irq 220
[   13.827621] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[364fc00028454c70]
[   13.834667] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   14.223080] ata1.00: ATA-8: TOSHIBA MK1246GSX, LB213D, max UDMA/100
[   14.223084] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 31/32)
[   14.223985] ata1.00: configured for UDMA/100
[   14.231313] ata2: SATA link down (SStatus 0 SControl 0)
[   14.238811] ata3: SATA link down (SStatus 0 SControl 300)
[   14.238923] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1246GS LB21 PQ: 0 ANSI: 5
[   14.240177] ata_piix 0000:00:1f.1: version 2.12
[   14.240194] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   14.240231] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   14.240904] scsi3 : ata_piix
[   14.241266] scsi4 : ata_piix
[   14.241857] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[   14.241859] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[   14.248196] Driver 'sd' needs updating - please use bus_type methods
[   14.249477] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   14.249488] sd 0:0:0:0: [sda] Write Protect is off
[   14.249490] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.249504] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.249547] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   14.249555] sd 0:0:0:0: [sda] Write Protect is off
[   14.249557] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.249569] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.249572]  sda: sda1 sda2 sda3 sda4 < sda5 >
[   14.354473] sd 0:0:0:0: [sda] Attached SCSI disk
[   14.359982] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   14.543196] ata4.00: ATAPI: HL-DT-ST DVD+/-RW GSA-T21N, A102, max UDMA/33
[   14.566580] Attempting manual resume
[   14.566583] swsusp: Resume From Partition 8:5
[   14.566584] PM: Checking swsusp image.
[   14.566753] PM: Resume from disk failed.
[   14.614066] kjournald starting.  Commit interval 5 seconds
[   14.614076] EXT3-fs: mounted filesystem with ordered data mode.
[   14.695383] ata4.00: configured for UDMA/33
[   14.695436] ata5: port disabled. ignoring.
[   14.699062] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T21N A102 PQ: 0 ANSI: 5
[   14.699140] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   23.887143] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.951884] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   24.960677] Linux agpgart interface v0.102
[   25.060608] agpgart: Detected an Intel 965GM Chipset.
[   25.060876] agpgart: Detected 7676K stolen memory.
[   25.089564] agpgart: AGP aperture is 256M @ 0xe0000000
[   25.217424] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   25.362773] ACPI: AC Adapter [AC] (on-line)
[   25.423894] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.587118] ACPI: Battery Slot [BAT0] (battery present)
[   25.607634] input: Lid Switch as /devices/virtual/input/input2
[   25.608325] ACPI: Lid Switch [LID]
[   25.608366] input: Power Button (CM) as /devices/virtual/input/input3
[   25.619495] ACPI: Power Button (CM) [PBTN]
[   25.619564] input: Sleep Button (CM) as /devices/virtual/input/input4
[   25.635456] ACPI: Sleep Button (CM) [SBTN]
[   25.699453] ACPI: WMI-Acer: Mapper loaded
[   26.111250] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input5
[   26.127643] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   26.127830] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input6
[   26.142555] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   27.021065] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
[   27.021089] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   27.108902] patch_cxthsfmodem: symbol_request(cnxthwhda_probe) failed
[   27.336478] iTCO_vendor_support: vendor-support=0
[   27.361348] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   27.361480] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   27.361534] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   27.472441] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.472457] PCI: Setting latency timer of device 0000:09:00.0 to 64
[   27.472494] sky2 0000:09:00.0: v1.20 addr 0xfe8fc000 irq 16 Yukon-FE+ (0xb8) rev 0
[   27.472927] sky2 eth0: addr 00:1d:09:4d:d6:c3
[   27.796177] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   27.796181] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   27.796356] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   27.796371] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[   27.796396] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   27.938920] ricoh-mmc: Ricoh MMC Controller disabling driver
[   27.938924] ricoh-mmc: Copyright(c) Philip Langdale
[   27.995289] sdhci: Secure Digital Host Controller Interface driver
[   27.995293] sdhci: Copyright(c) Pierre Ossman
[   28.039007] Driver 'sr' needs updating - please use bus_type methods
[   28.056604] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   28.056609] Uniform CD-ROM driver Revision: 3.20
[   28.056692] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   28.163310] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   28.438566] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   28.716144] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
[   28.716265] ricoh-mmc: Ricoh MMC controller found at 0000:02:09.2 [1180:0843] (rev 12)
[   28.716277] ricoh-mmc: Controller is now disabled.
[   28.716588] sdhci: SDHCI controller found at 0000:02:09.1 [1180:0822] (rev 22)
[   28.716616] ACPI: PCI Interrupt 0000:02:09.1[B] -> GSI 18 (level, low) -> IRQ 21
[   28.716678] mmc0: SDHCI at 0xfe3ff400 irq 21 DMA
[   29.048240] input: PS/2 Mouse as /devices/virtual/input/input8
[   29.082595] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input9
[   29.353759] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   30.325086] udev: renamed network interface wlan0 to eth1
[   30.736079] lp: driver loaded but no devices found
[   30.932005] Adding 4594548k swap on /dev/sda5.  Priority:-1 extents:1 across:4594548k
[   31.396415] EXT3 FS on sda3, internal journal
```

Thanks for taking the time to help!

---

### Post by argosreality on 2008-07-29
Hmm. To be honest Im at a bit of a loss, nothing appears to be obviously wrong or throwing major errors. There was a bunch of messages related to ACPI possibly being an issue and also information about a failed resume in there but...thats a bit outside of my experience.

I'll do some more research into it as well but hopefully someone else can chime in with a better idea. I'd thought orginally it was a DMA issue but it appears that most of the devices are SATA so that shouldn't be an issue really.

---

### Post by purplepaint on 2008-07-30
> **argosreality said:**
> Hmm. To be honest Im at a bit of a loss, nothing appears to be obviously wrong or throwing major errors. There was a bunch of messages related to ACPI possibly being an issue and also information about a failed resume in there but...thats a bit outside of my experience.

I'll do some more research into it as well but hopefully someone else can chime in with a better idea. I'd thought orginally it was a DMA issue but it appears that most of the devices are SATA so that shouldn't be an issue really.

OK, thanks again for the help.

---

### Post by purplepaint on 2008-07-30
In case it's helpful, before I got my Ubuntu laptop I used it on a Windows XP desktop for about 2-3 years without any problems (until Windows stopped showing the filenames of the videos I had stored on it when in thumbnail view, but I think that was a Windows issue and was one of the many reasons that caused me to make the switch).  I don't know if it's relevant, and I can't tell if it's an OS-related issue or hardware-related.

---

