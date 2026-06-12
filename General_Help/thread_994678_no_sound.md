---
title: "no sound"
date: 2008-11-27
forum: General Help
---

### Post by hyburn on 2008-11-27
I have no sound, please view the available info listed below: dmesg, lshw, lsmod, lspci, dmidecode.  and thanks for any help

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:43:45 UTC 2008 (Ubuntu 2.6.24-21.43-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000099000 (usable)
[    0.000000]  BIOS-e820: 0000000000099000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fe9a000 (usable)
[    0.000000]  BIOS-e820: 000000003fe9a000 - 000000003fee9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fee9000 - 000000003feed000 (usable)
[    0.000000]  BIOS-e820: 000000003feed000 - 000000003feff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003feff000 - 000000003ff00000 (usable)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe860
[    0.000000] Entering add_active_range(0, 0, 261888) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261888
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261888
[    0.000000] On node 0 totalpages: 261888
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 254 pages used for memmap
[    0.000000]   HighMem zone: 32258 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FE020 checksum 0
[    0.000000] ACPI: RSDP 000FE020, 0014 (r0 INTEL )
[    0.000000] ACPI: RSDT 3FEFDE48, 0038 (r1 INTEL  D945PPR1       50 MSFT  1000013)
[    0.000000] ACPI: FACP 3FEFCF10, 0074 (r1 INTEL  D945PPR1       50 MSFT  1000013)
[    0.000000] ACPI: DSDT 3FEF8010, 3EEE (r1 INTEL  D945PPR1       50 MSFT  1000013)
[    0.000000] ACPI: FACS 3FEE3C40, 0040
[    0.000000] ACPI: APIC 3FEFCE10, 0078 (r1 INTEL  D945PPR1       50 MSFT  1000013)
[    0.000000] ACPI: WDDT 3FEF7F90, 0040 (r1 INTEL  D945PPR1       50 MSFT  1000013)
[    0.000000] ACPI: MCFG 3FEF7F10, 003C (r1 INTEL  D945PPR1       50 MSFT  1000013)
[    0.000000] ACPI: ASF! 3FEFCD10, 00A6 (r32 INTEL  D945PPR1       50 MSFT  1000013)
[    0.000000] ACPI: DMI detected: Sony
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:c0100000)
[    0.000000] swsusp: Registered nosave memory region: 0000000000099000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259842
[    0.000000] Kernel command line: root=UUID=cb2ad040-245e-4363-b16d-5f83b9b01cc8 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2800.012 MHz processor.
[   23.221921] Console: colour VGA+ 80x25
[   23.221925] console [tty0] enabled
[   23.222225] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   23.222568] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.249047] Memory: 1025992k/1047552k available (2177k kernel code, 20488k reserved, 1005k data, 368k init, 129660k highmem)
[   23.249055] virtual kernel memory layout:
[   23.249056]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   23.249057]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.249058]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   23.249060]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   23.249061]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   23.249062]       .data : 0xc03205e4 - 0xc041bdc4   (1005 kB)
[   23.249063]       .text : 0xc0100000 - 0xc03205e4   (2177 kB)
[   23.249066] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.249106] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   23.328974] Calibrating delay using timer specific routine.. 5605.55 BogoMIPS (lpj=11211111)
[   23.329001] Security Framework initialized
[   23.329006] SELinux:  Disabled at boot.
[   23.329020] AppArmor: AppArmor initialized
[   23.329025] Failure registering capabilities with primary security module.
[   23.329034] Mount-cache hash table entries: 512
[   23.329163] Initializing cgroup subsys ns
[   23.329168] Initializing cgroup subsys cpuacct
[   23.329181] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000641d 00000000 00000000 00000000
[   23.329191] monitor/mwait feature present.
[   23.329193] using mwait in idle threads.
[   23.329200] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   23.329203] CPU: L2 cache: 1024K
[   23.329206] CPU: Physical Processor ID: 0
[   23.329208] CPU: Processor Core ID: 0
[   23.329210] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043180 0000641d 00000000 00000000 00000000
[   23.329221] Compat vDSO mapped to ffffe000.
[   23.329238] Checking 'hlt' instruction... OK.
[   23.345410] SMP alternatives: switching to UP code
[   23.347373] Early unpacking initramfs... done
[   23.659802] ACPI: Core revision 20070126
[   23.659854] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   23.662339] CPU0: Intel(R) Pentium(R) D CPU 2.80GHz stepping 04
[   23.662359] SMP alternatives: switching to SMP code
[   23.663164] Booting processor 1/1 eip 3000
[   23.678868] Initializing CPU#1
[   23.756144] Calibrating delay using timer specific routine.. 5600.33 BogoMIPS (lpj=11200664)
[   23.756154] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000641d 00000000 00000000 00000000
[   23.756160] monitor/mwait feature present.
[   23.756166] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   23.756168] CPU: L2 cache: 1024K
[   23.756170] CPU: Physical Processor ID: 0
[   23.756171] CPU: Processor Core ID: 1
[   23.756173] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043180 0000641d 00000000 00000000 00000000
[   23.756546] CPU1: Intel(R) Pentium(R) D CPU 2.80GHz stepping 04
[   23.756580] Total of 2 processors activated (11205.88 BogoMIPS).
[   23.756729] ENABLING IO-APIC IRQs
[   23.756901] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   23.903966] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   23.923953] Brought up 2 CPUs
[   23.923984] CPU0 attaching sched-domain:
[   23.923987]  domain 0: span 03
[   23.923990]   groups: 01 02
[   23.923994] CPU1 attaching sched-domain:
[   23.923996]  domain 0: span 03
[   23.923998]   groups: 02 01
[   23.924225] net_namespace: 64 bytes
[   23.924236] Booting paravirtualized kernel on bare hardware
[   23.924835] Time: 18:39:10  Date: 11/26/08
[   23.924861] NET: Registered protocol family 16
[   23.925108] EISA bus registered
[   23.925114] ACPI: bus type pci registered
[   23.927835] PCI: Using configuration type 1
[   23.927852] Setting up standard PCI resources
[   23.944521] ACPI: EC: Look up EC in DSDT
[   23.946318] ACPI: Interpreter enabled
[   23.946321] ACPI: (supports S0 S1 S3 S4 S5)
[   23.946340] ACPI: Using IOAPIC for interrupt routing
[   23.950376] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.951059] Force enabled HPET at base address 0xfed00000
[   23.951066] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   23.951070] PCI quirk: region 0500-053f claimed by ICH6 GPIO
[   23.951983] PCI: Transparent bridge - 0000:00:1e.0
[   23.952023] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.952378] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[   23.952764] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   23.952891] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[   23.953014] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[   23.956241] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[   23.956353] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[   23.956461] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[   23.956567] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[   23.956674] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[   23.956783] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[   23.956891] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[   23.956998] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11 12)
[   23.957154] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.957194] pnp: PnP ACPI init
[   23.957204] ACPI: bus type pnp registered
[   23.959629] pnp: PnP ACPI: found 10 devices
[   23.959632] ACPI: ACPI bus type pnp unregistered
[   23.959636] PnPBIOS: Disabled by ACPI PNP
[   23.959924] PCI: Using ACPI for IRQ routing
[   23.959927] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.971799] NET: Registered protocol family 8
[   23.971802] NET: Registered protocol family 20
[   23.971920] hpet clockevent registered
[   23.971926] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   23.971931] hpet0: 3 64-bit timers, 14318180 Hz
[   23.972974] AppArmor: AppArmor Filesystem Enabled
[   23.975734] Time: tsc clocksource has been installed.
[   23.983768] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[   23.983771] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
[   23.983775] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[   23.983778] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[   23.983781] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[   23.983783] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   23.983786] system 00:01: iomem range 0xfed20000-0xfed9ffff has been reserved
[   23.983790] system 00:01: iomem range 0xc0000-0xdffff could not be reserved
[   23.983792] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
[   23.983803] system 00:06: ioport range 0x500-0x53f has been reserved
[   23.983806] system 00:06: ioport range 0x400-0x47f has been reserved
[   23.983809] system 00:06: ioport range 0x680-0x6ff has been reserved
[   24.014282] PCI: Failed to allocate mem resource #6:20000@50000000 for 0000:01:00.0
[   24.014286] PCI: Bridge: 0000:00:01.0
[   24.014287]   IO window: disabled.
[   24.014292]   MEM window: 50000000-54ffffff
[   24.014296]   PREFETCH window: 40000000-4fffffff
[   24.014300] PCI: Bridge: 0000:00:1c.0
[   24.014303]   IO window: 2000-2fff
[   24.014308]   MEM window: 55100000-551fffff
[   24.014312]   PREFETCH window: disabled.
[   24.014318] PCI: Bridge: 0000:00:1c.2
[   24.014319]   IO window: disabled.
[   24.014324]   MEM window: 55300000-553fffff
[   24.014328]   PREFETCH window: disabled.
[   24.014333] PCI: Bridge: 0000:00:1c.3
[   24.014335]   IO window: disabled.
[   24.014340]   MEM window: 55400000-554fffff
[   24.014343]   PREFETCH window: disabled.
[   24.014349] PCI: Bridge: 0000:00:1e.0
[   24.014352]   IO window: 1000-1fff
[   24.014357]   MEM window: 55000000-550fffff
[   24.014361]   PREFETCH window: disabled.
[   24.014379] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   24.014385] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   24.014408] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   24.014414] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   24.014435] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   24.014441] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   24.014461] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   24.014467] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   24.014478] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   24.014491] NET: Registered protocol family 2
[   24.051663] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.051962] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.052580] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   24.052886] TCP: Hash tables configured (established 131072 bind 65536)
[   24.052890] TCP reno registered
[   24.063753] checking if image is initramfs... it is
[   24.470891] Switched to high resolution mode on CPU 1
[   24.474778] Switched to high resolution mode on CPU 0
[   24.679968] Freeing initrd memory: 7319k freed
[   24.680916] audit: initializing netlink socket (disabled)
[   24.680932] audit(1227724750.312:1): initialized
[   24.681132] highmem bounce pool size: 64 pages
[   24.683654] VFS: Disk quotas dquot_6.5.1
[   24.683751] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.683898] io scheduler noop registered
[   24.683901] io scheduler anticipatory registered
[   24.683903] io scheduler deadline registered
[   24.683915] io scheduler cfq registered (default)
[   24.684115] Boot video device is 0000:01:00.0
[   24.684246] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   24.684290] assign_interrupt_mode Found MSI capability
[   24.684326] Allocate Port Service[0000:00:01.0:pcie00]
[   24.684423] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   24.684469] assign_interrupt_mode Found MSI capability
[   24.684507] Allocate Port Service[0000:00:1c.0:pcie00]
[   24.684551] Allocate Port Service[0000:00:1c.0:pcie02]
[   24.684657] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   24.684703] assign_interrupt_mode Found MSI capability
[   24.684740] Allocate Port Service[0000:00:1c.2:pcie00]
[   24.684785] Allocate Port Service[0000:00:1c.2:pcie02]
[   24.684887] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   24.684933] assign_interrupt_mode Found MSI capability
[   24.684970] Allocate Port Service[0000:00:1c.3:pcie00]
[   24.685014] Allocate Port Service[0000:00:1c.3:pcie02]
[   24.685334] isapnp: Scanning for PnP cards...
[   25.036341] isapnp: No Plug & Play device found
[   25.073755] Real Time Clock Driver v1.12ac
[   25.073871] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.075381] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.075462] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   25.075582] PNP: PS/2 Controller [PNP0f03:PS2M] at 0x0,0x0 irq 12
[   25.075585] PNP: PS/2 controller has invalid data port 0x0; using default 0x60
[   25.075588] PNP: PS/2 controller has invalid command port 0x0; using default 0x64
[   25.075590] PNP: PS/2 controller doesn't have KBD irq; using default 1
[   25.078597] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.078605] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.089633] mice: PS/2 mouse device common for all mice
[   25.089784] EISA: Probing bus 0 at eisa.0
[   25.089791] Cannot allocate resource for EISA slot 1
[   25.089794] Cannot allocate resource for EISA slot 2
[   25.089796] Cannot allocate resource for EISA slot 3
[   25.089815] EISA: Detected 0 cards.
[   25.089818] cpuidle: using governor ladder
[   25.089820] cpuidle: using governor menu
[   25.089905] NET: Registered protocol family 1
[   25.089939] Using IPI No-Shortcut mode
[   25.089970] registered taskstats version 1
[   25.090081]   Magic number: 0:29:697
[   25.090210] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   25.090212] EDD information not available.
[   25.090423] Freeing unused kernel memory: 368k freed
[   25.090451] Write protecting the kernel read-only data: 801k
[   26.335753] fuse init (API version 7.9)
[   26.360122] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   26.360137] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   26.699824] usbcore: registered new interface driver usbfs
[   26.699853] usbcore: registered new interface driver hub
[   26.700376] usbcore: registered new device driver usb
[   26.701737] USB Universal Host Controller Interface driver v3.0
[   26.701791] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   26.701803] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   26.701807] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   26.702013] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   26.702044] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00003080
[   26.702194] usb usb1: configuration #1 chosen from 1 choice
[   26.702226] hub 1-0:1.0: USB hub found
[   26.702233] hub 1-0:1.0: 2 ports detected
[   26.740015] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   26.740020] Copyright (c) 1999-2006 Intel Corporation.
[   26.798125] SCSI subsystem initialized
[   26.806362] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   26.806375] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   26.806379] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   26.806408] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   26.806438] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003060
[   26.806564] usb usb2: configuration #1 chosen from 1 choice
[   26.806594] hub 2-0:1.0: USB hub found
[   26.806600] hub 2-0:1.0: 2 ports detected
[   26.831138] libata version 3.00 loaded.
[   26.909961] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   26.909975] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   26.909979] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   26.910007] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   26.910037] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003040
[   26.910165] usb usb3: configuration #1 chosen from 1 choice
[   26.910194] hub 3-0:1.0: USB hub found
[   26.910200] hub 3-0:1.0: 2 ports detected
[   27.013740] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   27.013752] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   27.013757] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   27.013787] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   27.013818] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003020
[   27.013946] usb usb4: configuration #1 chosen from 1 choice
[   27.013975] hub 4-0:1.0: USB hub found
[   27.013982] hub 4-0:1.0: 2 ports detected
[   27.117558] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.117576] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   27.120149] e1000: 0000:02:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:13:20:a2:95:32
[   27.146367] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   27.182668] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   27.182748] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   27.182767] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   27.182772] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   27.182812] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   27.186721] ehci_hcd 0000:00:1d.7: debug port 1
[   27.186728] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   27.186737] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x55204400
[   27.277100] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.277238] usb usb5: configuration #1 chosen from 1 choice
[   27.277268] hub 5-0:1.0: USB hub found
[   27.277276] hub 5-0:1.0: 8 ports detected
[   27.381034] ACPI: PCI Interrupt 0000:05:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   27.431148] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[55004000-550047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   27.431486] ahci 0000:00:1f.2: version 3.0
[   27.431519] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   27.668315] usb 2-1: device not accepting address 2, error -71
[   28.275099] usb 5-8: new high speed USB device using ehci_hcd and address 3
[   28.430802] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl RAID mode
[   28.430806] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part 
[   28.430812] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   28.431102] scsi0 : ahci
[   28.431347] scsi1 : ahci
[   28.431509] scsi2 : ahci
[   28.431668] scsi3 : ahci
[   28.431765] ata1: SATA max UDMA/133 abar m1024@0x55204000 port 0x55204100 irq 219
[   28.431769] ata2: SATA max UDMA/133 abar m1024@0x55204000 port 0x55204180 irq 219
[   28.431773] ata3: SATA max UDMA/133 abar m1024@0x55204000 port 0x55204200 irq 219
[   28.431776] ata4: SATA max UDMA/133 abar m1024@0x55204000 port 0x55204280 irq 219
[   28.480968] usb 5-8: configuration #1 chosen from 1 choice
[   28.698357] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00902700019902b7]
[   28.718717] usb 2-1: new low speed USB device using uhci_hcd and address 4
[   28.742164] ata1: SATA link down (SStatus 0 SControl 300)
[   28.898480] usb 2-1: configuration #1 chosen from 1 choice
[   28.902189] usbcore: registered new interface driver libusual
[   28.907605] Initializing USB Mass Storage driver...
[   28.908972] scsi4 : SCSI emulation for USB Mass Storage devices
[   28.909891] usbcore: registered new interface driver usb-storage
[   28.909896] USB Mass Storage support registered.
[   28.909976] usb-storage: device found at 3
[   28.909980] usb-storage: waiting for device to settle before scanning
[   28.929146] usbcore: registered new interface driver hiddev
[   28.943812] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input1
[   28.961784] input,hidraw0: USB HID v1.10 Keyboard [CHESEN USB Keyboard] on usb-0000:00:1d.1-1
[   28.988277] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.1/input/input2
[   28.998184] input,hidraw1: USB HID v1.10 Device [CHESEN USB Keyboard] on usb-0000:00:1d.1-1
[   28.998202] usbcore: registered new interface driver usbhid
[   28.998207] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   29.053543] ata2: SATA link down (SStatus 0 SControl 300)
[   29.364907] ata3: SATA link down (SStatus 0 SControl 300)
[   29.839954] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   29.840521] ata4.00: ATA-7: ST3250310AS, 3.AAC, max UDMA/133
[   29.840525] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   29.841215] ata4.00: configured for UDMA/133
[   29.841370] scsi 3:0:0:0: Direct-Access     ATA      ST3250310AS      3.AA PQ: 0 ANSI: 5
[   29.846262] ata_piix 0000:00:1f.1: version 2.12
[   29.846281] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   29.846319] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   29.847070] scsi5 : ata_piix
[   29.850967] scsi6 : ata_piix
[   29.851503] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x30b0 irq 14
[   29.851506] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x30b8 irq 15
[   29.853979] Driver 'sd' needs updating - please use bus_type methods
[   29.854076] sd 3:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   29.854094] sd 3:0:0:0: [sda] Write Protect is off
[   29.854097] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.854122] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.854187] sd 3:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   29.854202] sd 3:0:0:0: [sda] Write Protect is off
[   29.854205] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.854230] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.854234]  sda: sda1 sda2 < sda5 >
[   29.892081] sd 3:0:0:0: [sda] Attached SCSI disk
[   29.898055] sd 3:0:0:0: Attached scsi generic sg0 type 0
[   30.355753] ata5.01: ATAPI: SONY DVD-ROM DDU1615, FFS1, max UDMA/66
[   30.526842] ata5.01: configured for UDMA/66
[   30.526886] ata6: port disabled. ignoring.
[   30.527446] scsi 5:0:1:0: CD-ROM            SONY     DVD-ROM DDU1615  FFS1 PQ: 0 ANSI: 5
[   30.527537] scsi 5:0:1:0: Attached scsi generic sg1 type 5
[   30.539918] Driver 'sr' needs updating - please use bus_type methods
[   30.542935] sr0: scsi3-mmc drive: 4x/40x cd/rw xa/form2 cdda tray
[   30.542941] Uniform CD-ROM driver Revision: 3.20
[   30.542997] sr 5:0:1:0: Attached scsi CD-ROM sr0
[   30.695780] Attempting manual resume
[   30.695784] swsusp: Resume From Partition 8:5
[   30.695786] PM: Checking swsusp image.
[   30.695943] PM: Resume from disk failed.
[   30.749095] kjournald starting.  Commit interval 5 seconds
[   30.749107] EXT3-fs: mounted filesystem with ordered data mode.
[   33.908670] usb-storage: device scan complete
[   33.912116] scsi 4:0:0:0: Direct-Access     Sony     USB   HS-MS      4.38 PQ: 0 ANSI: 0
[   33.915615] scsi 4:0:0:1: Direct-Access     Sony     USB   HS-CF      4.38 PQ: 0 ANSI: 0
[   33.919221] scsi 4:0:0:2: Direct-Access     Sony     USB   HS-SM/xD   4.38 PQ: 0 ANSI: 0
[   33.922462] scsi 4:0:0:3: Direct-Access     Sony     USB   HS-SD MMC  4.38 PQ: 0 ANSI: 0
[   33.927482] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   33.927539] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   33.931716] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   33.931761] sd 4:0:0:1: Attached scsi generic sg3 type 0
[   33.936579] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[   33.936615] sd 4:0:0:2: Attached scsi generic sg4 type 0
[   33.987485] sd 4:0:0:3: [sde] Attached SCSI removable disk
[   33.987522] sd 4:0:0:3: Attached scsi generic sg5 type 0
[   36.359025] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.407125] Linux agpgart interface v0.102
[   36.467215] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   36.501207] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.550564] intel_rng: Firmware space is locked read-only. If you can't or
[   36.550567] intel_rng: don't want to disable this in firmware setup, and if
[   36.550569] intel_rng: you are certain that your system has a functional
[   36.550570] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   36.583569] input: Power Button (FF) as /devices/virtual/input/input4
[   36.606378] ACPI: Power Button (FF) [PWRF]
[   36.606467] input: Sleep Button (CM) as /devices/virtual/input/input5
[   36.638317] ACPI: Sleep Button (CM) [SLPB]
[   36.648707] iTCO_vendor_support: vendor-support=0
[   36.661415] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   36.661515] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   36.661550] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   37.095343] logips2pp: Detected unknown logitech mouse model 101
[   37.348466] nvidia: module license 'NVIDIA' taints kernel.
[   37.679938] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[   37.722127] parport_pc 00:07: reported by Plug and Play ACPI
[   37.722158] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   37.732163] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   37.732176] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   37.732342] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   37.899717] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   37.899759] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   39.107938] lp0: using parport0 (interrupt-driven).
[   39.174262] Adding 3020180k swap on /dev/sda5.  Priority:-1 extents:1 across:3020180k
[   39.724783] EXT3 FS on sda1, internal journal
[   40.866820] ip_tables: (C) 2000-2006 Netfilter Core Team
[   41.298295] No dock devices found.
[   42.444513] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   42.444519] apm: disabled - APM is not SMP safe.
[   43.100528] ppdev: user-space parallel port driver
[   43.323431] audit(1227724769.314:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5182 profile="/usr/sbin/cupsd" namespace="default"
[   44.918771] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[   44.918780] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   45.005088] Bluetooth: Core ver 2.11
[   45.005350] NET: Registered protocol family 31
[   45.005354] Bluetooth: HCI device and connection manager initialized
[   45.005358] Bluetooth: HCI socket layer initialized
[   45.022361] Bluetooth: L2CAP ver 2.9
[   45.022366] Bluetooth: L2CAP socket layer initialized
[   45.093855] Bluetooth: RFCOMM socket layer initialized
[   45.093868] Bluetooth: RFCOMM TTY layer initialized
[   45.093870] Bluetooth: RFCOMM ver 1.8
[   49.491627] NET: Registered protocol family 17
[   52.672932] NET: Registered protocol family 10
[   52.673239] lo: Disabled Privacy Extensions
[   63.196912] eth0: no IPv6 routers present









drew
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1009MiB
     *-cpu
          product: Intel(R) Pentium(R) D CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.4.4
          serial: 0000-0F44-0000-0000-0000-0000
          size: 18EHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: NV43 [GeForce 6600]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 82573V Gigabit Ethernet Controller (Copper)
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 03
                serial: 00:13:20:a2:95:32
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=1.0-1 ip=192.168.0.180 latency=0 module=e1000 multicast=yes
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-communication UNCLAIMED
                description: Communication controller
                product: V.92 56K WinModem
                vendor: Agere Systems
                physical id: 1
                bus info: pci@0000:05:01.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=32 maxlatency=14 mingnt=252
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 5
                bus info: pci@0000:05:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-storage
             description: RAID bus controller
             product: 82801GR/GH (ICH7 Family) SATA RAID Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0 module=ahci
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage










Module                  Size  Used by
ipv6                  267780  10 
af_packet              23812  2 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
dock                   11280  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
sbp2                   24072  0 
lp                     12324  0 
snd_hda_intel         344856  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
evdev                  13056  4 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
nvidia               7825536  56 
snd_seq_dummy           4868  0 
i2c_core               24832  1 nvidia
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
serio_raw               7940  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
psmouse                40336  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
intel_agp              25492  0 
shpchp                 34452  0 
pcspkr                  4224  0 
soundcore               8800  1 snd
agpgart                34760  2 nvidia,intel_agp
pci_hotplug            30880  1 shpchp
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
pata_acpi               8320  0 
sg                     36880  0 
sd_mod                 30720  3 
ata_piix               19588  0 
usbhid                 32128  0 
hid                    38784  1 usbhid
usb_storage            73664  0 
libusual               19108  1 usb_storage
ahci                   28548  2 
ata_generic             8324  0 
ohci1394               33584  0 
libata                159344  4 pata_acpi,ata_piix,ahci,ata_generic
scsi_mod              151436  6 sbp2,sr_mod,sg,sd_mod,usb_storage,libata
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
e1000                 126016  0 
uhci_hcd               27024  0 
usbcore               146412  6 usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              37384  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
Module                  Size  Used by
ipv6                  267780  10 
af_packet              23812  2 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
dock                   11280  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
sbp2                   24072  0 
lp                     12324  0 
snd_hda_intel         344856  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
evdev                  13056  4 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
nvidia               7825536  56 
snd_seq_dummy           4868  0 
i2c_core               24832  1 nvidia
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
serio_raw               7940  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
psmouse                40336  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
intel_agp              25492  0 
shpchp                 34452  0 
pcspkr                  4224  0 
soundcore               8800  1 snd
agpgart                34760  2 nvidia,intel_agp
pci_hotplug            30880  1 shpchp
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
pata_acpi               8320  0 
sg                     36880  0 
sd_mod                 30720  3 
ata_piix               19588  0 
usbhid                 32128  0 
hid                    38784  1 usbhid
usb_storage            73664  0 
libusual               19108  1 usb_storage
ahci                   28548  2 
ata_generic             8324  0 
ohci1394               33584  0 
libata                159344  4 pata_acpi,ata_piix,ahci,ata_generic
scsi_mod              151436  6 sbp2,sr_mod,sg,sd_mod,usb_storage,libata
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
e1000                 126016  0 
uhci_hcd               27024  0 
usbcore               146412  6 usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              37384  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 










00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
02:00.0 Ethernet controller: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) (rev 03)
05:01.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
05:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)









# dmidecode 2.9



thanks for any help, 

it is an onboard HD sound system of a sony vaio using "intel Desktop Board D945PPR/D945GPR" hope that helps

-hyburn

P.S.

Just a thought, is it possible to access the sound device in my TV through my S-Video cable to use as my sound card?

---

### Post by hyburn on 2008-11-28
so I ended up buying a Sound Blaster Live 24-bit sound card today. with the data above can someone help me get the right driver?

---

