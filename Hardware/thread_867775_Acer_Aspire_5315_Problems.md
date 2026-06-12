---
title: "Acer Aspire 5315 Problems"
date: 2008-07-23
forum: Hardware
---

### Post by osmoTR on 2008-07-23
Hi All
sorry for my bad english 

i have a aspire 5315 installed hardy desktop (gnome)
brightness adjust don't work every restart after go back from %100 to %0  

UPDATED : problem has been resolved compiled from vanilla kernel works very well

but still brightness adjust don't work

after bios v1.43 update 
problem when on boot system freeze don't start ( i set manual brightness level %100 on grub menu or post screen )  
but if i set brightness level zero i mean no light :)
on boot system just hangs about 55-60 seconds after going well booting

system freeze or hangs on line
```
[30.354993] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
```

lspci | grep 1f.2 :
```

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)

```

dmesg :
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f4fd000 (usable)
[    0.000000]  BIOS-e820: 000000001f4fd000 - 000000001f508000 (reserved)
[    0.000000]  BIOS-e820: 000000001f508000 - 000000001f552000 (usable)
[    0.000000]  BIOS-e820: 000000001f552000 - 000000001f555000 (reserved)
[    0.000000]  BIOS-e820: 000000001f555000 - 000000001f5bb000 (usable)
[    0.000000]  BIOS-e820: 000000001f5bb000 - 000000001f5bf000 (reserved)
[    0.000000]  BIOS-e820: 000000001f5bf000 - 000000001f672000 (usable)
[    0.000000]  BIOS-e820: 000000001f672000 - 000000001f6bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f6bf000 - 000000001f700000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe1b0
[    0.000000] Entering add_active_range(0, 0, 128626) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128626
[    0.000000]   HighMem    128626 ->   128626
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128626
[    0.000000] On node 0 totalpages: 128626
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 972 pages used for memmap
[    0.000000]   Normal zone: 123558 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FE020 checksum 0
[    0.000000] ACPI: RSDP 000FE020, 0024 (r2 ACRSYS)
[    0.000000] ACPI: XSDT 1F6FE120, 0064 (r1 ACRSYS ACRPRDCT        1       1000013)
[    0.000000] ACPI: FACP 1F6FD000, 00F4 (r4 ACRSYS ACRPRDCT        1 MSFT  1000013)
[    0.000000] ACPI: DSDT 1F6F4000, 8968 (r1 ACRSYS ACRPRDCT        1 MSFT  1000013)
[    0.000000] ACPI: FACS 1F675000, 0040
[    0.000000] ACPI: APIC 1F6F3000, 0068 (r2 ACRSYS ACRPRDCT        1 MSFT  1000013)
[    0.000000] ACPI: MCFG 1F6F2000, 003C (r1 ACRSYS ACRPRDCT        1 MSFT  1000013)
[    0.000000] ACPI: NSLI 1F6F1000, 0176 (r1 ACRSYS ACRPRDCT        1 MSFT  1000013)
[    0.000000] ACPI: HPET 1F6F0000, 0038 (r1 ACRSYS ACRPRDCT        1 MSFT  1000013)
[    0.000000] ACPI: SSDT 1F6EF000, 05D7 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    0.000000] ACPI: SSDT 1F6EE000, 04C4 (r1  PmRef    CpuPm     3000 INTL 20051117)
[    0.000000] ACPI: SSDT 1F6ED000, 0232 (r1  PmRef  Cpu0Tst     3000 INTL 20051117)
[    0.000000] ACPI: DMI detected: Acer
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 7:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 000000001f4fd000 - 000000001f508000
[    0.000000] swsusp: Registered nosave memory region: 000000001f552000 - 000000001f555000
[    0.000000] swsusp: Registered nosave memory region: 000000001f5bb000 - 000000001f5bf000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127622
[    0.000000] Kernel command line: root=UUID=68F8B16EF8B13AE0 loop=/ubuntu/disks/root.disk ro
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1729.079 MHz processor.
[   26.511194] Console: colour VGA+ 80x25
[   26.511198] console [tty0] enabled
[   26.515591] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   26.515822] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.523324] Memory: 497284k/514504k available (2177k kernel code, 16116k reserved, 1006k data, 368k init, 0k highmem)
[   26.523405] virtual kernel memory layout:
[   26.523406]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   26.523407]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   26.523408]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   26.523409]     lowmem  : 0xc0000000 - 0xdf672000   ( 502 MB)
[   26.523410]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   26.523411]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   26.523412]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   26.523841] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   26.523974] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   26.524185] hpet clockevent registered
[   26.604158] Calibrating delay using timer specific routine.. 3462.14 BogoMIPS (lpj=6924295)
[   26.604280] Security Framework initialized
[   26.604336] SELinux:  Disabled at boot.
[   26.604398] AppArmor: AppArmor initialized
[   26.604453] Failure registering capabilities with primary security module.
[   26.604515] Mount-cache hash table entries: 512
[   26.604675] Initializing cgroup subsys ns
[   26.604731] Initializing cgroup subsys cpuacct
[   26.604792] CPU: After generic identify, caps: afebfbff 20100000 00000000 00000000 0000e31d 00000000 00000001 00000000
[   26.604799] monitor/mwait feature present.
[   26.604852] using mwait in idle threads.
[   26.604907] CPU: L1 I cache: 32K, L1 D cache: 32K
[   26.604994] CPU: L2 cache: 1024K
[   26.605047] CPU: After all inits, caps: afebfbff 20100000 00000000 00003940 0000e31d 00000000 00000001 00000000
[   26.605055] Compat vDSO mapped to ffffe000.
[   26.605117] Checking 'hlt' instruction... OK.
[   26.620595] SMP alternatives: switching to UP code
[   26.622225] Freeing SMP alternatives: 11k freed
[   26.622368] Early unpacking initramfs... done
[   26.969678] ACPI: Core revision 20070126
[   26.969784] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   27.022022] CPU0: Intel(R) Celeron(R) CPU          530  @ 1.73GHz stepping 01
[   27.022169] Total of 1 processors activated (3462.14 BogoMIPS).
[   27.022416] ENABLING IO-APIC IRQs
[   27.022656] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   27.167955] Brought up 1 CPUs
[   27.168026] CPU0 attaching sched-domain:
[   27.168028]  domain 0: span 01
[   27.168030]   groups: 01
[   27.168176] net_namespace: 64 bytes
[   27.168234] Booting paravirtualized kernel on bare hardware
[   27.168731] Time:  7:31:05  Date: 07/23/08
[   27.168804] NET: Registered protocol family 16
[   27.169033] EISA bus registered
[   27.169087] ACPI: bus type pci registered
[   27.169362] PCI: Using configuration type 1
[   27.169425] Setting up standard PCI resources
[   27.171212] ACPI: EC: Look up EC in DSDT
[   27.173955] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   27.174011] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
[   27.176254] ACPI: Interpreter enabled
[   27.176308] ACPI: (supports S0 S3 S4 S5)
[   27.176505] ACPI: Using IOAPIC for interrupt routing
[   27.177706] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   27.226845] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   27.226905] ACPI: EC: driver started in interrupt mode
[   27.227003] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   27.228160] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   27.228219] PCI quirk: region 0500-053f claimed by ICH6 GPIO
[   27.229237] PCI: Transparent bridge - 0000:00:1e.0
[   27.229345] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   27.229655] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[   27.229803] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[   27.229950] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[   27.230097] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[   27.238090] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[   27.238613] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[   27.239132] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[   27.239647] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[   27.240168] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[   27.240761] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
[   27.241279] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[   27.241797] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[   27.242334] Linux Plug and Play Support v0.97 (c) Adam Belay
[   27.242418] pnp: PnP ACPI init
[   27.242477] ACPI: bus type pnp registered
[   27.264164] pnp: PnP ACPI: found 9 devices
[   27.264218] ACPI: ACPI bus type pnp unregistered
[   27.264274] PnPBIOS: Disabled by ACPI PNP
[   27.264524] PCI: Using ACPI for IRQ routing
[   27.264578] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   27.275882] NET: Registered protocol family 8
[   27.275936] NET: Registered protocol family 20
[   27.276019] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   27.276207] hpet0: 3 64-bit timers, 14318180 Hz
[   27.277295] AppArmor: AppArmor Filesystem Enabled
[   27.279868] Time: tsc clocksource has been installed.
[   27.279934] Switched to high resolution mode on CPU 0
[   27.287864] system 00:01: ioport range 0x164e-0x164f has been reserved
[   27.287922] system 00:01: ioport range 0x600-0x60f has been reserved
[   27.287979] system 00:01: ioport range 0x610-0x610 has been reserved
[   27.288035] system 00:01: ioport range 0x800-0x80f has been reserved
[   27.288092] system 00:01: ioport range 0x810-0x817 has been reserved
[   27.288148] system 00:01: ioport range 0x400-0x47f has been reserved
[   27.288204] system 00:01: ioport range 0x500-0x53f has been reserved
[   27.288262] system 00:01: ioport range 0xff2c-0xff2f has been reserved
[   27.288319] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   27.288390] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   27.288461] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   27.289364] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   27.289435] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   27.289506] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   27.289576] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   27.289647] system 00:01: iomem range 0x32000000-0x320000ff has been reserved
[   27.320108] PCI: Bridge: 0000:00:1c.0
[   27.320163]   IO window: 4000-4fff
[   27.320218]   MEM window: 37300000-382fffff
[   27.320273]   PREFETCH window: 30000000-30ffffff
[   27.320330] PCI: Bridge: 0000:00:1c.1
[   27.320383]   IO window: 3000-3fff
[   27.320440]   MEM window: 36300000-372fffff
[   27.320496]   PREFETCH window: 31000000-31ffffff
[   27.320554] PCI: Bridge: 0000:00:1c.2
[   27.320607]   IO window: 2000-2fff
[   27.320663]   MEM window: 35200000-362fffff
[   27.320719]   PREFETCH window: 32000000-32ffffff
[   27.320777] PCI: Bridge: 0000:00:1c.3
[   27.320831]   IO window: 1000-1fff
[   27.320887]   MEM window: 34100000-351fffff
[   27.320943]   PREFETCH window: 33000000-33ffffff
[   27.321000] PCI: Bridge: 0000:00:1e.0
[   27.321051]   IO window: disabled.
[   27.321107]   MEM window: disabled.
[   27.321162]   PREFETCH window: disabled.
[   27.321249] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.321358] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   27.321385] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   27.321498] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   27.321523] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   27.321634] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   27.321660] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   27.321771] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   27.321786] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   27.321796] NET: Registered protocol family 2
[   27.359865] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   27.360103] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   27.360234] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   27.360351] TCP: Hash tables configured (established 16384 bind 16384)
[   27.360407] TCP reno registered
[   27.371905] checking if image is initramfs... it is
[   28.046256] Freeing initrd memory: 7543k freed
[   28.046973] audit: initializing netlink socket (disabled)
[   28.047041] audit(1216798266.368:1): initialized
[   28.049061] VFS: Disk quotas dquot_6.5.1
[   28.049184] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   28.049369] io scheduler noop registered
[   28.049423] io scheduler anticipatory registered
[   28.049477] io scheduler deadline registered
[   28.049537] io scheduler cfq registered (default)
[   28.049601] Boot video device is 0000:00:02.0
[   28.050247] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   28.050311] assign_interrupt_mode Found MSI capability
[   28.050418] Allocate Port Service[0000:00:1c.0:pcie00]
[   28.050451] Allocate Port Service[0000:00:1c.0:pcie02]
[   28.050557] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   28.050620] assign_interrupt_mode Found MSI capability
[   28.050723] Allocate Port Service[0000:00:1c.1:pcie00]
[   28.050753] Allocate Port Service[0000:00:1c.1:pcie02]
[   28.050858] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   28.050921] assign_interrupt_mode Found MSI capability
[   28.051023] Allocate Port Service[0000:00:1c.2:pcie00]
[   28.051055] Allocate Port Service[0000:00:1c.2:pcie02]
[   28.051160] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   28.051223] assign_interrupt_mode Found MSI capability
[   28.051326] Allocate Port Service[0000:00:1c.3:pcie00]
[   28.051357] Allocate Port Service[0000:00:1c.3:pcie02]
[   28.051608] isapnp: Scanning for PnP cards...
[   28.406046] isapnp: No Plug & Play device found
[   28.430869] Real Time Clock Driver v1.12ac
[   28.431139] hpet_resources: 0xfed00000 is busy
[   28.431187] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.432667] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   28.432801] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   28.432960] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   28.467255] serio: i8042 KBD port at 0x60,0x64 irq 1
[   28.467312] serio: i8042 AUX port at 0x60,0x64 irq 12
[   28.479403] mice: PS/2 mouse device common for all mice
[   28.479560] EISA: Probing bus 0 at eisa.0
[   28.479618] Cannot allocate resource for EISA slot 1
[   28.479672] Cannot allocate resource for EISA slot 2
[   28.479726] Cannot allocate resource for EISA slot 3
[   28.479781] Cannot allocate resource for EISA slot 4
[   28.479835] Cannot allocate resource for EISA slot 5
[   28.479902] EISA: Detected 0 cards.
[   28.479955] cpuidle: using governor ladder
[   28.480007] cpuidle: using governor menu
[   28.480139] NET: Registered protocol family 1
[   28.480216] Using IPI No-Shortcut mode
[   28.480295] registered taskstats version 1
[   28.480445]   Magic number: 0:951:521
[   28.480580] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   28.480636] EDD information not available.
[   28.480866] Freeing unused kernel memory: 368k freed
[   28.507348] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   28.653391] fuse init (API version 7.9)
[   28.674003] Monitor-Mwait will be used to enter C-1 state
[   28.674006] Monitor-Mwait will be used to enter C-2 state
[   28.674009] Monitor-Mwait will be used to enter C-3 state
[   28.674123] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   28.674317] ACPI: Processor [CPU0] (supports 8 throttling states)
[   28.674451] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   28.678807] ACPI: Thermal Zone [TZ01] (60 C)
[   28.975236] usbcore: registered new interface driver usbfs
[   28.975317] usbcore: registered new interface driver hub
[   28.990075] usbcore: registered new device driver usb
[   28.995173] USB Universal Host Controller Interface driver v3.0
[   28.995292] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   28.995405] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   28.995410] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   28.995714] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   28.995821] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000050c0
[   28.996004] usb usb1: configuration #1 chosen from 1 choice
[   28.996079] hub 1-0:1.0: USB hub found
[   28.996134] hub 1-0:1.0: 2 ports detected
[   29.099196] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
[   29.099315] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   29.099320] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   29.099394] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   29.099495] uhci_hcd 0000:00:1a.1: irq 20, io base 0x000050a0
[   29.099652] usb usb2: configuration #1 chosen from 1 choice
[   29.099727] hub 2-0:1.0: USB hub found
[   29.099782] hub 2-0:1.0: 2 ports detected


[   29.203156] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 21
[   29.203273] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   29.203278] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   29.203353] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   29.203455] uhci_hcd 0000:00:1d.0: irq 21, io base 0x00005080
[   29.203618] usb usb3: configuration #1 chosen from 1 choice
[   29.203693] hub 3-0:1.0: USB hub found
[   29.203748] hub 3-0:1.0: 2 ports detected
[   29.307132] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   29.307251] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   29.307255] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   29.307332] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   29.307437] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00005060
[   29.307599] usb usb4: configuration #1 chosen from 1 choice
[   29.307673] hub 4-0:1.0: USB hub found
[   29.307728] hub 4-0:1.0: 2 ports detected
[   29.411075] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   29.411193] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   29.411198] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   29.411275] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   29.411377] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00005040
[   29.411538] usb usb5: configuration #1 chosen from 1 choice
[   29.411612] hub 5-0:1.0: USB hub found
[   29.411667] hub 5-0:1.0: 2 ports detected
[   29.437237] SCSI subsystem initialized
[   29.484121] libata version 3.00 loaded.
[   29.515137] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   29.515258] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   29.515262] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   29.515340] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   29.519332] ehci_hcd 0000:00:1a.7: debug port 1
[   29.519391] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   29.519397] ehci_hcd 0000:00:1a.7: irq 18, io mem 0x38304c00
[   29.534897] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.535088] usb usb6: configuration #1 chosen from 1 choice
[   29.535167] hub 6-0:1.0: USB hub found
[   29.535224] hub 6-0:1.0: 4 ports detected
[   29.638965] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 21
[   29.639087] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   29.639091] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   29.639167] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   29.643151] ehci_hcd 0000:00:1d.7: debug port 1
[   29.643210] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   29.643216] ehci_hcd 0000:00:1d.7: irq 21, io mem 0x38304800
[   29.658866] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.659055] usb usb7: configuration #1 chosen from 1 choice
[   29.659132] hub 7-0:1.0: USB hub found
[   29.659188] hub 7-0:1.0: 6 ports detected
[   29.763057] tg3.c:v3.86 (November 9, 2007)
[   29.763144] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   29.763257] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   30.295748] eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:1b:38:65:fc:4a
[   30.296030] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[1]
[   30.296100] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   30.296433] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   30.296549] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   30.314592] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   30.314666] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   30.314748] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   30.314830] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   30.354607] ssb: Sonics Silicon Backplane found on PCI device 0000:06:00.0
[   30.354964] ahci 0000:00:1f.2: version 3.0
[   30.354993] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19 #### wait about 55 seconds 
[   30.674402] Clocksource tsc unstable (delta = -26291581880 ns)
[   30.678397] Time: hpet clocksource has been installed.
[   30.683880] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   30.683956] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   30.684029] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   30.684248] scsi0 : ahci
[   30.684524] scsi1 : ahci
[   30.684716] scsi2 : ahci
[   30.684860] ata1: SATA max UDMA/133 abar m2048@0x38304000 port 0x38304100 irq 219
[   30.684932] ata2: SATA max UDMA/133 abar m2048@0x38304000 port 0x38304180 irq 219
[   30.685004] ata3: SATA max UDMA/133 abar m2048@0x38304000 port 0x38304200 irq 219
[   30.745243] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   30.746205] ata1.00: ATA-7: Hitachi HTS541680J9SA00, SB2OC70P, max UDMA/100
[   30.746263] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   30.747407] ata1.00: configured for UDMA/100
[   30.837458] ata2: SATA link down (SStatus 0 SControl 300)
[   30.840400] ata3: SATA link down (SStatus 0 SControl 300)
[   30.840568] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54168 SB2O PQ: 0 ANSI: 5
[   30.842135] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   30.842277] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   30.842291] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   30.848603] ata_piix 0000:00:1f.1: version 2.12
[   30.848622] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   30.848762] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   30.849106] scsi3 : ata_piix
[   30.854624] scsi4 : ata_piix
[   30.855216] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x50e0 irq 14
[   30.855274] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x50e8 irq 15
[   30.855911] Driver 'sd' needs updating - please use bus_type methods
[   30.856404] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   30.856472] sd 0:0:0:0: [sda] Write Protect is off
[   30.856527] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.856542] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.856657] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   30.856721] sd 0:0:0:0: [sda] Write Protect is off
[   30.856776] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.856790] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.856864]  sda:<6>ata4.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.61, max UDMA/33
[   31.260393]  sda1 sda2 < sda5 >
[   31.284667] sd 0:0:0:0: [sda] Attached SCSI disk
[   31.290501] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   31.344568] ata4.00: configured for UDMA/33
[   31.513304] scsi 3:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.61 PQ: 0 ANSI: 5
[   31.513451] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   31.523313] Driver 'sr' needs updating - please use bus_type methods
[   31.530174] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   31.530250] Uniform CD-ROM driver Revision: 3.20
[   31.530353] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   31.873199] loop: module loaded
[   31.903959] kjournald starting.  Commit interval 5 seconds
[   31.904028] EXT3-fs: mounted filesystem with ordered data mode.
[   41.140267] input: PS/2 Mouse as /devices/virtual/input/input2
[   41.170442] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   41.219745] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input4
[   41.239395] iTCO_vendor_support: vendor-support=0
[   41.283377] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   41.283526] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x0460)
[   41.283620] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   41.391433] ACPI: WMI-Acer: Mapper loaded
[   41.431322] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.448584] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.486984] Linux agpgart interface v0.102
[   41.771247] input: Power Button (FF) as /devices/virtual/input/input5
[   41.795147] ACPI: Power Button (FF) [PWRF]
[   41.795268] input: Power Button (CM) as /devices/virtual/input/input6
[   41.819141] ACPI: Power Button (CM) [PWRB]
[   41.819262] input: Lid Switch as /devices/virtual/input/input7
[   41.835209] ACPI: Lid Switch [LID0]
[   41.835321] input: Sleep Button (CM) as /devices/virtual/input/input8
[   41.863115] ACPI: Sleep Button (CM) [SLPB]
[   41.975088] agpgart: Detected an Intel 965GM Chipset.
[   41.975443] agpgart: Detected 7676K stolen memory.
[   41.989871] agpgart: AGP aperture is 256M @ 0x20000000
[   42.071017] acer_acpi: Acer Laptop ACPI Extras version 0.11.2
[   42.071082] acer_acpi: Detected Acer WMID interface
[   42.249537] ACPI: AC Adapter [AC] (on-line)
[   42.463285] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:34/LNXVIDEO:00/input/input9
[   42.494810] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   42.597632] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input10
[   42.618762] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   43.022631] ACPI: Battery Slot [BAT0] (battery present)
[   43.896963] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   43.897099] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   44.068506] b43-phy0: Broadcom 4311 WLAN found
[   44.110038] b43-phy0 debug: Found PHY: Analog 4, Type 2, Revision 8
[   44.110059] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   44.135518] phy0: Selected rate control algorithm 'simple'
[   45.517217] lp: driver loaded but no devices found
[   46.052695] EXT3 FS on loop0, internal journal
[   46.787915] UDF-fs: No VRS found
[   46.864181] ISO 9660 Extensions: Microsoft Joliet Level 3
[   46.881225] ISO 9660 Extensions: RRIP_1991A
[   56.120161] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:21 across:26650104k
[   57.023138] ip_tables: (C) 2000-2006 Netfilter Core Team
[   57.730356] No dock devices found.
[   58.876607] apm: BIOS not found.
[   59.026455] ppdev: user-space parallel port driver
[   59.164462] audit(1216787529.877:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5259 profile="/usr/sbin/cupsd" namespace="default"
[   62.293438] input: b43-phy0 as /devices/virtual/input/input11
[   62.517014] Bluetooth: Core ver 2.11
[   62.517340] NET: Registered protocol family 31
[   62.517343] Bluetooth: HCI device and connection manager initialized
[   62.517347] Bluetooth: HCI socket layer initialized
[   62.570614] Bluetooth: L2CAP ver 2.9
[   62.570618] Bluetooth: L2CAP socket layer initialized
[   62.716965] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   62.726530] Bluetooth: RFCOMM socket layer initialized
[   62.726545] Bluetooth: RFCOMM TTY layer initialized
[   62.726547] Bluetooth: RFCOMM ver 1.8
[   64.726174] b43-phy0 debug: Chip initialized
[   64.726366] b43-phy0 debug: 32-bit DMA initialized
[   64.734279] Registered led device: b43-phy0:tx
[   64.734302] Registered led device: b43-phy0:rx
[   64.734329] Registered led device: b43-phy0:radio
[   64.734367] b43-phy0 debug: Wireless interface started
[   64.734371] b43-phy0 debug: Adding Interface type 2
[   65.176028] [drm] Initialized drm 1.1.0 20060810
[   65.178924] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   65.178933] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   65.179005] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   76.732789] NET: Registered protocol family 10
[   76.733223] lo: Disabled Privacy Extensions
[   76.733707] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   76.734237] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```[/QUOTE]


if i disable acpi after system don't start gives errors like  " ata soft reset "

also i tried ubuntu 7.10 without problems (just no sound because alsa driver didn't come with realtek.patch for hda-intel ) 
i can't go back v1.42 because new bios v1.43 fixes important problems

---

