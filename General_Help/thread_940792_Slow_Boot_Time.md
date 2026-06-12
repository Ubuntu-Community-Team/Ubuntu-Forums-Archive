---
title: "Slow Boot Time"
date: 2008-10-07
forum: General Help
---

### Post by Heftiger on 2008-10-07
Hello,

I recently installed Ubuntu 8.04 and I have been experiencing very slow boot times. I researched this topic on the forums and people suggested that I remove quiet boot and the splash screen. This fix corrected many of people's problems. This however did now work for me, although I can now see where it hangs during boot.

While booting it hangs on this line for a couple mins or more:

forcing PORTS_IMPL 0xf


Does anybody have suggestion to speed up my extremely slow boot time?

Thanks!

---

### Post by Pelham123 on 2008-10-07
Can you post your /var/log/dmesg log please.

---

### Post by Heftiger on 2008-10-07
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fe90000 (usable)
[    0.000000]  BIOS-e820: 000000001fe90000 - 000000001fe9d000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fe9d000 - 000000001ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 130704) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130704
[    0.000000]   HighMem    130704 ->   130704
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130704
[    0.000000] On node 0 totalpages: 130704
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 989 pages used for memmap
[    0.000000]   Normal zone: 125619 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6780 checksum 0
[    0.000000] ACPI: RSDP 000F6780, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 1FE97449, 0048 (r1   Sony       V0 20050523 PTL         0)
[    0.000000] ACPI: FACP 1FE9CE78, 0084 (r2   Sony       V0 20050523 PTL        50)
[    0.000000] ACPI: DSDT 1FE989FD, 447B (r1   Sony       V0 20050523 PTL   100000E)
[    0.000000] ACPI: FACS 1FEADFC0, 0040
[    0.000000] ACPI: APIC 1FE9CEFC, 0068 (r1   Sony       V0 20050523 PTL        50)
[    0.000000] ACPI: BOOT 1FE9CFD8, 0028 (r1   Sony       V0 20050523 PTL         1)
[    0.000000] ACPI: MCFG 1FE9CF9C, 003C (r1   Sony       V0 20050523 PTL        5F)
[    0.000000] ACPI: SSDT 1FE983AA, 064F (r1   Sony       V0 20050523 PTL  20030224)
[    0.000000] ACPI: SSDT 1FE97D0E, 069C (r1   Sony       V0 20050523 PTL  20030224)
[    0.000000] ACPI: SSDT 1FE978C9, 0235 (r1   Sony       V0 20050523 PTL  20030224)
[    0.000000] ACPI: SSDT 1FE976AA, 021F (r1   Sony       V0 20050523 PTL  20030224)
[    0.000000] ACPI: SSDT 1FE97491, 0219 (r1   Sony       V0 20050523 PTL  20030224)
[    0.000000] ACPI: DMI detected: Sony
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
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d8000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d8000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129683
[    0.000000] Kernel command line: root=UUID=827bab9e-52cb-42ba-b860-3b2c06fa6575
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 798.016 MHz processor.
[   17.607568] Console: colour VGA+ 80x25
[   17.607576] console [tty0] enabled
[   17.611848] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.612275] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.630507] Memory: 506244k/522816k available (2177k kernel code, 15956k reserved, 1006k data, 368k init, 0k highmem)
[   17.630605] virtual kernel memory layout:
[   17.630607]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   17.630610]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.630613]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   17.630616]     lowmem  : 0xc0000000 - 0xdfe90000   ( 510 MB)
[   17.630618]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   17.630621]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   17.630624]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   17.631125] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.631300] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   17.711401] Calibrating delay using timer specific routine.. 1598.24 BogoMIPS (lpj=3196482)
[   17.711564] Security Framework initialized
[   17.711636] SELinux:  Disabled at boot.
[   17.711721] AppArmor: AppArmor initialized
[   17.711791] Failure registering capabilities with primary security module.
[   17.711870] Mount-cache hash table entries: 512
[   17.712135] Initializing cgroup subsys ns
[   17.712205] Initializing cgroup subsys cpuacct
[   17.712280] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000 00000000
[   17.712302] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.712416] CPU: L2 cache: 2048K
[   17.712480] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000 00000000
[   17.712498] Compat vDSO mapped to ffffe000.
[   17.712580] Checking 'hlt' instruction... OK.
[   17.728108] SMP alternatives: switching to UP code
[   17.731676] Freeing SMP alternatives: 11k freed
[   17.731933] Early unpacking initramfs... done
[   18.483256] ACPI: Core revision 20070126
[   18.483434] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   18.491276] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[   18.491511] Total of 1 processors activated (1598.24 BogoMIPS).
[   18.491779] ENABLING IO-APIC IRQs
[   18.492056] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.639389] Brought up 1 CPUs
[   18.639492] CPU0 attaching sched-domain:
[   18.639497]  domain 0: span 01
[   18.639501]   groups: 01
[   18.639793] net_namespace: 64 bytes
[   18.639873] Booting paravirtualized kernel on bare hardware
[   18.640848] Time: 19:35:36  Date: 10/07/08
[   18.640957] NET: Registered protocol family 16
[   18.641392] EISA bus registered
[   18.641488] ACPI: bus type pci registered
[   18.642138] PCI: PCI BIOS revision 2.10 entry at 0xfd911, last bus=7
[   18.642210] PCI: Using configuration type 1
[   18.642302] Setting up standard PCI resources
[   18.715621] ACPI: EC: Look up EC in DSDT
[   18.718811] ACPI: Interpreter enabled
[   18.718882] ACPI: (supports S0 S3 S4 S5)
[   18.719152] ACPI: Using IOAPIC for interrupt routing
[   18.725619] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   18.728066] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[   18.728141] ACPI: EC: driver started in interrupt mode
[   18.728282] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.729092] Force enabled HPET at base address 0xfed00000
[   18.729102] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   18.729178] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   18.730261] PCI: Transparent bridge - 0000:00:1e.0
[   18.730447] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.731042] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[   18.731363] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   18.744614] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[   18.744999] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[   18.745381] ACPI: PCI Interrupt Link [LNKC] (IRQs 10) *5
[   18.745811] ACPI: PCI Interrupt Link [LNKD] (IRQs *10)
[   18.746187] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[   18.746560] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *3
[   18.746980] ACPI: PCI Interrupt Link [LNKG] (IRQs *10)
[   18.747358] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[   18.747799] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.747926] pnp: PnP ACPI init
[   18.748002] ACPI: bus type pnp registered
[   18.751330] pnp: PnP ACPI: found 10 devices
[   18.751400] ACPI: ACPI bus type pnp unregistered
[   18.751468] PnPBIOS: Disabled by ACPI PNP
[   18.751939] PCI: Using ACPI for IRQ routing
[   18.752008] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.787311] NET: Registered protocol family 8
[   18.787380] NET: Registered protocol family 20
[   18.787763] hpet clockevent registered
[   18.787773] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   18.788032] hpet0: 3 64-bit timers, 14318180 Hz
[   18.789152] AppArmor: AppArmor Filesystem Enabled
[   18.791298] Time: tsc clocksource has been installed.
[   18.799368] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   18.799455] system 00:01: iomem range 0xf0000000-0xf0003fff could not be reserved
[   18.799537] system 00:01: iomem range 0xf0004000-0xf0004fff could not be reserved
[   18.799620] system 00:01: iomem range 0xf0005000-0xf0005fff could not be reserved
[   18.799703] system 00:01: iomem range 0xf0008000-0xf000bfff could not be reserved
[   18.799786] system 00:01: iomem range 0xfed20000-0xfed8ffff could not be reserved
[   18.799876] system 00:05: ioport range 0x680-0x68f has been reserved
[   18.799946] system 00:05: ioport range 0x800-0x80f has been reserved
[   18.800017] system 00:05: ioport range 0x1000-0x107f has been reserved
[   18.800088] system 00:05: ioport range 0x1180-0x11bf has been reserved
[   18.800158] system 00:05: ioport range 0xfe00-0xfe01 has been reserved
[   18.800229] system 00:05: iomem range 0xd000c000-0xd000ffff has been reserved
[   18.831080] PCI: Bridge: 0000:00:01.0
[   18.831148]   IO window: disabled.
[   18.831215]   MEM window: 90000000-afffffff
[   18.831282]   PREFETCH window: c0000000-cfffffff
[   18.831366] PCI: Bus 7, cardbus bridge: 0000:06:05.0
[   18.831435]   IO window: 00002400-000024ff
[   18.831505]   IO window: 00002800-000028ff
[   18.831575]   PREFETCH window: 30000000-33ffffff
[   18.831645]   MEM window: 34000000-37ffffff
[   18.831714] PCI: Bridge: 0000:00:1e.0
[   18.831780]   IO window: 2000-2fff
[   18.831849]   MEM window: b0000000-b00fffff
[   18.831918]   PREFETCH window: disabled.
[   18.832003] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   18.832137] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   18.832154] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   18.832184] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 21 (level, low) -> IRQ 17
[   18.832334] NET: Registered protocol family 2
[   18.871395] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   18.871850] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   18.872123] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   18.872381] TCP: Hash tables configured (established 16384 bind 16384)
[   18.872453] TCP reno registered
[   18.883498] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   19.605187]  it is
[   20.368907] Freeing initrd memory: 7319k freed
[   20.369243] Simple Boot Flag at 0x36 set to 0x1
[   20.370016] audit: initializing netlink socket (disabled)
[   20.370104] audit(1223408137.632:1): initialized
[   20.374190] VFS: Disk quotas dquot_6.5.1
[   20.374405] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.374723] io scheduler noop registered
[   20.374792] io scheduler anticipatory registered
[   20.374858] io scheduler deadline registered
[   20.374942] io scheduler cfq registered (default)
[   20.375156] Boot video device is 0000:01:00.0
[   20.375171] PCI: Firmware left 0000:06:08.0 e100 interrupts enabled, disabling
[   20.375436] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   20.375481] assign_interrupt_mode Found MSI capability
[   20.375585] Allocate Port Service[0000:00:01.0:pcie00]
[   20.375996] isapnp: Scanning for PnP cards...
[   20.731584] isapnp: No Plug & Play device found
[   20.785550] Real Time Clock Driver v1.12ac
[   20.785800] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.788207] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.788422] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   20.788685] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   20.791122] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.791196] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.803006] mice: PS/2 mouse device common for all mice
[   20.803281] EISA: Probing bus 0 at eisa.0
[   20.803357] Cannot allocate resource for EISA slot 1
[   20.803425] Cannot allocate resource for EISA slot 2
[   20.803528] EISA: Detected 0 cards.
[   20.803596] cpuidle: using governor ladder
[   20.803662] cpuidle: using governor menu
[   20.803880] NET: Registered protocol family 1
[   20.803992] Using IPI No-Shortcut mode
[   20.804099] registered taskstats version 1
[   20.804352]   Magic number: 12:594:596
[   20.804462]   hash matches device ptyd0
[   20.804603] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   20.804673] EDD information not available.
[   20.805030] Freeing unused kernel memory: 368k freed
[   20.838874] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   21.161341] fuse init (API version 7.9)
[   21.208133] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   21.208447] ACPI: Processor [CPU0] (supports 8 throttling states)
[   21.208634] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   21.212257] ACPI: Thermal Zone [ATF0] (34 C)
[   21.778772] usbcore: registered new interface driver usbfs
[   21.778885] usbcore: registered new interface driver hub
[   21.794726] usbcore: registered new device driver usb
[   21.822715] USB Universal Host Controller Interface driver v3.0
[   21.822865] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 17 (level, low) -> IRQ 18
[   21.823008] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   21.823016] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   21.823481] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   21.823601] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00001800
[   21.823913] usb usb1: configuration #1 chosen from 1 choice
[   21.824026] hub 1-0:1.0: USB hub found
[   21.824101] hub 1-0:1.0: 2 ports detected
[   21.926800] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   21.926947] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   21.926955] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   21.927063] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   21.927182] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
[   21.927452] usb usb2: configuration #1 chosen from 1 choice
[   21.927564] hub 2-0:1.0: USB hub found
[   21.927639] hub 2-0:1.0: 2 ports detected
[   22.030776] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 21 (level, low) -> IRQ 17
[   22.030924] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   22.030932] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.031039] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   22.031158] uhci_hcd 0000:00:1d.2: irq 17, io base 0x00001840
[   22.031434] usb usb3: configuration #1 chosen from 1 choice
[   22.031546] hub 3-0:1.0: USB hub found
[   22.031620] hub 3-0:1.0: 2 ports detected
[   22.134752] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 17 (level, low) -> IRQ 18
[   22.134901] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   22.134909] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   22.135017] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   22.135130] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00001860
[   22.135406] usb usb4: configuration #1 chosen from 1 choice
[   22.135518] hub 4-0:1.0: USB hub found
[   22.135593] hub 4-0:1.0: 2 ports detected
[   22.553160] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
[   22.553314] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   22.553321] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   22.553436] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   22.557432] ehci_hcd 0000:00:1d.7: debug port 1
[   22.557507] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   22.557524] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x80004000
[   22.614536] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.614830] usb usb5: configuration #1 chosen from 1 choice
[   22.614953] hub 5-0:1.0: USB hub found
[   22.615028] hub 5-0:1.0: 8 ports detected
[   22.730852] SCSI subsystem initialized
[   22.819431] libata version 3.00 loaded.
[   22.898940] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   22.899020] e100: Copyright(c) 1999-2006 Intel Corporation
[   22.902246] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   23.014896] e100: eth0: e100_probe: addr 0xb0006000, irq 21, MAC addr 00:01:4a:22:bf:7c
[   23.020479] ACPI: PCI Interrupt 0000:06:05.2[C] -> GSI 20 (level, low) -> IRQ 21
[   23.174475] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[b0004000-b00047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   23.180050] ahci 0000:00:1f.2: version 3.0
[   23.180092] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 18 (level, low) -> IRQ 22
[   23.180248] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0xf
[   24.182241] ahci 0000:00:1f.2: AHCI 0001.0000 32 slots 4 ports 1.5 Gbps 0xf impl IDE mode
[   24.182336] ahci 0000:00:1f.2: flags: 64bit ncq pm led pmp slum part 
[   24.182409] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   24.182824] scsi0 : ahci
[   24.183203] scsi1 : ahci
[   24.183524] scsi2 : ahci
[   24.183839] scsi3 : ahci
[   24.184058] ata1: SATA max UDMA/133 abar m1024@0x80004400 port 0x80004500 irq 22
[   24.184144] ata2: SATA max UDMA/133 abar m1024@0x80004400 port 0x80004580 irq 22
[   24.184227] ata3: SATA max UDMA/133 abar m1024@0x80004400 port 0x80004600 irq 22
[   24.184310] ata4: SATA max UDMA/133 abar m1024@0x80004400 port 0x80004680 irq 22
[   24.286183] Clocksource tsc unstable (delta = -134120733305 ns)
[   24.290193] Time: hpet clocksource has been installed.
[   24.293140] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460301dae25d]
[   24.312586] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   24.312828] ata1.00: ATA-7: FUJITSU MHT2080BH, 40000049, max UDMA/100
[   24.312899] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   24.313209] ata1.00: configured for UDMA/100
[   24.317379] ata2: SATA link down (SStatus 0 SControl 0)
[   24.321508] ata3: SATA link down (SStatus 0 SControl 300)
[   24.325725] ata4: SATA link down (SStatus 0 SControl 0)
[   24.325975] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2080B 4000 PQ: 0 ANSI: 5
[   24.327764] ata_piix 0000:00:1f.1: version 2.12
[   24.327789] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 18 (level, low) -> IRQ 22
[   24.327969] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   24.328055] scsi4 : ata_piix
[   24.328388] scsi5 : ata_piix
[   24.329381] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[   24.329457] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[   24.334638] ata5.00: ATAPI: MATSHITAUJ-832D, 1.03, max UDMA/33
[   24.338088] ata5.00: configured for UDMA/33
[   24.338205] ata6: port disabled. ignoring.
[   24.338703] scsi 4:0:0:0: CD-ROM            MATSHITA UJ-832D          1.03 PQ: 0 ANSI: 5
[   24.359609] Driver 'sd' needs updating - please use bus_type methods
[   24.359813] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   24.359908] sd 0:0:0:0: [sda] Write Protect is off
[   24.359979] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.360013] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.360175] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   24.360265] sd 0:0:0:0: [sda] Write Protect is off
[   24.360335] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.360368] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.360456]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   24.382850]  sda1 sda2 < sda5 >
[   24.384997] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.396567] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.396673] sr 4:0:0:0: Attached scsi generic sg1 type 5
[   24.400494] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   24.400571] Uniform CD-ROM driver Revision: 3.20
[   24.400708] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   24.550740] Attempting manual resume
[   24.550828] swsusp: Resume From Partition 8:5
[   24.550831] PM: Checking swsusp image.
[   24.550954] PM: Resume from disk failed.
[   24.583710] kjournald starting.  Commit interval 5 seconds
[   24.583796] EXT3-fs: mounted filesystem with ordered data mode.
[   28.407345] Linux agpgart interface v0.102
[   28.627319] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.671291] iTCO_vendor_support: vendor-support=0
[   28.723273] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   28.724795] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   28.724891] iTCO_wdt: No card detected
[   28.795361] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   29.023196] intel_rng: FWH not detected
[   30.427588] input: Lid Switch as /devices/virtual/input/input2
[   30.450945] ACPI: Lid Switch [LID0]
[   30.451171] input: Power Button (CM) as /devices/virtual/input/input3
[   30.462865] ACPI: Power Button (CM) [PWRB]
[   30.899798] Yenta: CardBus bridge found at 0000:06:05.0 [104d:818f]
[   30.899902] Yenta: Enabling burst memory read transactions
[   30.899976] Yenta: Using CSCINT to route CSC interrupts to PCI
[   30.900045] Yenta: Routing CardBus interrupts to PCI
[   30.900117] Yenta TI: socket 0000:06:05.0, mfunc 0x01001b22, devctl 0x64
[   31.066763] ieee80211_crypt: registered algorithm 'NULL'
[   31.131550] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   31.131628] Socket status: 30000006
[   31.131693] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   31.131778] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   31.131847] cs: IO port probe 0x2000-0x2fff: clean.
[   31.132483] pcmcia: parent PCI bridge Memory window: 0xb0000000 - 0xb00fffff
[   31.139924] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   31.139998] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   31.211148] ACPI: PCI Interrupt 0000:06:05.3[B] -> GSI 23 (level, low) -> IRQ 20
[   31.234700] tifm_core: MMC/SD card detected in socket 0:0
[   31.267167] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   31.267255] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   31.267484] ACPI: PCI Interrupt 0000:06:0b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   31.330685] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   32.570614] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   32.979051] input: PS/2 Mouse as /devices/virtual/input/input5
[   33.005284] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input6
[   33.822898] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7
[   33.834128] ACPI: Video Device [NGFX] (multi-head: yes  rom: no  post: no)
[   33.835226] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8
[   33.850119] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   35.920007] sony-laptop: Sony Programmable IO Control Driver v0.5.
[   35.920092] sony-laptop: detected Type3 model
[   35.973360] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:18/SNY6001:00/input/input9
[   35.981776] input: Sony Vaio Jogdial as /devices/virtual/input/input10
[   35.997786] sony-laptop: device allocated minor is 63
[   36.022119] sony-laptop: Sony Notebook Control Driver v0.5.
[   36.913058] ACPI: AC Adapter [ACAD] (off-line)
[   36.966802] ACPI: Battery Slot [BAT1] (battery present)
[   36.997905] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 19 (level, low) -> IRQ 19
[   36.998074] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   38.551759] cs: IO port probe 0x100-0x3af: clean.
[   38.554371] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   38.555648] cs: IO port probe 0x820-0x8ff: clean.
[   38.556641] cs: IO port probe 0xc00-0xcf7: clean.
[   38.557942] cs: IO port probe 0xa00-0xaff: clean.
[   39.156062] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   39.730194] lp: driver loaded but no devices found
[   40.131490] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
[   40.164921] EXT3 FS on sda1, internal journal
[   40.830733] ip_tables: (C) 2000-2006 Netfilter Core Team
```

---

### Post by cj2003 on 2008-10-07
Perhaps you can find ideas in this guide:

[Improving boot performance of Ubuntu Hardy Heron ]("http://ubuntu-news.net/modules/news/article.php?storyid=5083")

---

### Post by Heftiger on 2008-10-07
> **cj2003 said:**
> Perhaps you can find ideas in this guide:

[Improving boot performance of Ubuntu Hardy Heron ]("http://ubuntu-news.net/modules/news/article.php?storyid=5083")

I'll take a look. 
Thank You.

---

