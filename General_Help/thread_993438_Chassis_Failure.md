---
title: "Chassis Failure"
date: 2008-11-25
forum: General Help
---

### Post by hyburn on 2008-11-25
at boot my computer gave me a message of Chassis Failure. then to press F2. I see that this can cause disk failure. how do I fix this problem?

---

### Post by linux_tech on 2008-11-25
What is the system configuration?

what is output of 
```
dmesg
```
```
lsmod
```
```
lspci
```
```
sudo lshw | less
```
```
sudo dmidecode
```

---

### Post by hyburn on 2008-11-25
dmesg
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
[    0.000000] Detected 2800.002 MHz processor.
[   40.336490] Console: colour VGA+ 80x25
[   40.336494] console [tty0] enabled
[   40.336797] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   40.337137] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   40.363600] Memory: 1025992k/1047552k available (2177k kernel code, 20488k reserved, 1005k data, 368k init, 129660k highmem)
[   40.363607] virtual kernel memory layout:
[   40.363609]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   40.363610]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   40.363611]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   40.363612]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   40.363613]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   40.363614]       .data : 0xc03205e4 - 0xc041bdc4   (1005 kB)
[   40.363615]       .text : 0xc0100000 - 0xc03205e4   (2177 kB)
[   40.363618] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   40.363657] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   40.443525] Calibrating delay using timer specific routine.. 5605.52 BogoMIPS (lpj=11211040)
[   40.443552] Security Framework initialized
[   40.443557] SELinux:  Disabled at boot.
[   40.443572] AppArmor: AppArmor initialized
[   40.443576] Failure registering capabilities with primary security module.
[   40.443585] Mount-cache hash table entries: 512
[   40.443715] Initializing cgroup subsys ns
[   40.443719] Initializing cgroup subsys cpuacct
[   40.443732] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000641d 00000000 00000000 00000000
[   40.443742] monitor/mwait feature present.
[   40.443744] using mwait in idle threads.
[   40.443751] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   40.443754] CPU: L2 cache: 1024K
[   40.443757] CPU: Physical Processor ID: 0
[   40.443758] CPU: Processor Core ID: 0
[   40.443761] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043180 0000641d 00000000 00000000 00000000
[   40.443772] Compat vDSO mapped to ffffe000.
[   40.443788] Checking 'hlt' instruction... OK.
[   40.459963] SMP alternatives: switching to UP code
[   40.461926] Early unpacking initramfs... done
[   40.776035] ACPI: Core revision 20070126
[   40.776087] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   40.778581] CPU0: Intel(R) Pentium(R) D CPU 2.80GHz stepping 04
[   40.778601] SMP alternatives: switching to SMP code
[   40.779429] Booting processor 1/1 eip 3000
[   40.789525] Initializing CPU#1
[   40.866704] Calibrating delay using timer specific routine.. 5600.32 BogoMIPS (lpj=11200649)
[   40.866713] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000641d 00000000 00000000 00000000
[   40.866719] monitor/mwait feature present.
[   40.866725] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   40.866727] CPU: L2 cache: 1024K
[   40.866729] CPU: Physical Processor ID: 0
[   40.866731] CPU: Processor Core ID: 1
[   40.866732] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043180 0000641d 00000000 00000000 00000000
[   40.867112] CPU1: Intel(R) Pentium(R) D CPU 2.80GHz stepping 04
[   40.867146] Total of 2 processors activated (11205.84 BogoMIPS).
[   40.867295] ENABLING IO-APIC IRQs
[   40.867468] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   41.014526] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   41.034513] Brought up 2 CPUs
[   41.034544] CPU0 attaching sched-domain:
[   41.034547]  domain 0: span 03
[   41.034550]   groups: 01 02
[   41.034554] CPU1 attaching sched-domain:
[   41.034556]  domain 0: span 03
[   41.034558]   groups: 02 01
[   41.034785] net_namespace: 64 bytes
[   41.034795] Booting paravirtualized kernel on bare hardware
[   41.035398] Time: 19:36:27  Date: 11/25/08
[   41.035424] NET: Registered protocol family 16
[   41.035676] EISA bus registered
[   41.035682] ACPI: bus type pci registered
[   41.038421] PCI: Using configuration type 1
[   41.038438] Setting up standard PCI resources
[   41.055086] ACPI: EC: Look up EC in DSDT
[   41.056885] ACPI: Interpreter enabled
[   41.056888] ACPI: (supports S0 S1 S3 S4 S5)
[   41.056907] ACPI: Using IOAPIC for interrupt routing
[   41.060940] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   41.061621] Force enabled HPET at base address 0xfed00000
[   41.061627] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   41.061631] PCI quirk: region 0500-053f claimed by ICH6 GPIO
[   41.062545] PCI: Transparent bridge - 0000:00:1e.0
[   41.062584] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   41.062938] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[   41.063325] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   41.063452] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[   41.063576] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[   41.066803] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[   41.066915] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[   41.067023] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[   41.067130] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[   41.067237] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[   41.067346] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[   41.067455] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[   41.067561] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11 12)
[   41.067717] Linux Plug and Play Support v0.97 (c) Adam Belay
[   41.067757] pnp: PnP ACPI init
[   41.067767] ACPI: bus type pnp registered
[   41.070173] pnp: PnP ACPI: found 10 devices
[   41.070176] ACPI: ACPI bus type pnp unregistered
[   41.070180] PnPBIOS: Disabled by ACPI PNP
[   41.070465] PCI: Using ACPI for IRQ routing
[   41.070469] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   41.082354] NET: Registered protocol family 8
[   41.082357] NET: Registered protocol family 20
[   41.082474] hpet clockevent registered
[   41.082479] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   41.082485] hpet0: 3 64-bit timers, 14318180 Hz
[   41.083525] AppArmor: AppArmor Filesystem Enabled
[   41.086291] Time: tsc clocksource has been installed.
[   41.094325] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[   41.094329] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
[   41.094332] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[   41.094335] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[   41.094338] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[   41.094340] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   41.094343] system 00:01: iomem range 0xfed20000-0xfed9ffff has been reserved
[   41.094346] system 00:01: iomem range 0xc0000-0xdffff could not be reserved
[   41.094349] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
[   41.094359] system 00:06: ioport range 0x500-0x53f has been reserved
[   41.094362] system 00:06: ioport range 0x400-0x47f has been reserved
[   41.094365] system 00:06: ioport range 0x680-0x6ff has been reserved
[   41.124835] PCI: Failed to allocate mem resource #6:20000@50000000 for 0000:01:00.0
[   41.124839] PCI: Bridge: 0000:00:01.0
[   41.124840]   IO window: disabled.
[   41.124845]   MEM window: 50000000-54ffffff
[   41.124849]   PREFETCH window: 40000000-4fffffff
[   41.124853] PCI: Bridge: 0000:00:1c.0
[   41.124857]   IO window: 2000-2fff
[   41.124862]   MEM window: 55100000-551fffff
[   41.124866]   PREFETCH window: disabled.
[   41.124871] PCI: Bridge: 0000:00:1c.2
[   41.124873]   IO window: disabled.
[   41.124878]   MEM window: 55300000-553fffff
[   41.124882]   PREFETCH window: disabled.
[   41.124887] PCI: Bridge: 0000:00:1c.3
[   41.124888]   IO window: disabled.
[   41.124894]   MEM window: 55400000-554fffff
[   41.124897]   PREFETCH window: disabled.
[   41.124903] PCI: Bridge: 0000:00:1e.0
[   41.124906]   IO window: 1000-1fff
[   41.124911]   MEM window: 55000000-550fffff
[   41.124915]   PREFETCH window: disabled.
[   41.124934] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   41.124940] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   41.124963] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   41.124969] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   41.124990] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   41.124997] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   41.125018] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   41.125023] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   41.125035] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   41.125048] NET: Registered protocol family 2
[   41.162220] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   41.162520] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   41.163139] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   41.163446] TCP: Hash tables configured (established 131072 bind 65536)
[   41.163449] TCP reno registered
[   41.174310] checking if image is initramfs... it is
[   41.581439] Switched to high resolution mode on CPU 1
[   41.585325] Switched to high resolution mode on CPU 0
[   41.790215] Freeing initrd memory: 7319k freed
[   41.791147] audit: initializing netlink socket (disabled)
[   41.791162] audit(1227641787.308:1): initialized
[   41.791361] highmem bounce pool size: 64 pages
[   41.793839] VFS: Disk quotas dquot_6.5.1
[   41.793942] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   41.794093] io scheduler noop registered
[   41.794095] io scheduler anticipatory registered
[   41.794098] io scheduler deadline registered
[   41.794111] io scheduler cfq registered (default)
[   41.794311] Boot video device is 0000:01:00.0
[   41.794441] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   41.794486] assign_interrupt_mode Found MSI capability
[   41.794522] Allocate Port Service[0000:00:01.0:pcie00]
[   41.794618] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   41.794664] assign_interrupt_mode Found MSI capability
[   41.794702] Allocate Port Service[0000:00:1c.0:pcie00]
[   41.794746] Allocate Port Service[0000:00:1c.0:pcie02]
[   41.794852] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   41.794898] assign_interrupt_mode Found MSI capability
[   41.794935] Allocate Port Service[0000:00:1c.2:pcie00]
[   41.794979] Allocate Port Service[0000:00:1c.2:pcie02]
[   41.795088] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   41.795134] assign_interrupt_mode Found MSI capability
[   41.795171] Allocate Port Service[0000:00:1c.3:pcie00]
[   41.795215] Allocate Port Service[0000:00:1c.3:pcie02]
[   41.795529] isapnp: Scanning for PnP cards...
[   42.146534] isapnp: No Plug & Play device found
[   42.183687] Real Time Clock Driver v1.12ac
[   42.183803] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   42.185503] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   42.185584] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   42.185704] PNP: PS/2 Controller [PNP0f03:PS2M] at 0x0,0x0 irq 12
[   42.185708] PNP: PS/2 controller has invalid data port 0x0; using default 0x60
[   42.185710] PNP: PS/2 controller has invalid command port 0x0; using default 0x64
[   42.185713] PNP: PS/2 controller doesn't have KBD irq; using default 1
[   42.188670] serio: i8042 KBD port at 0x60,0x64 irq 1
[   42.188677] serio: i8042 AUX port at 0x60,0x64 irq 12
[   42.200174] mice: PS/2 mouse device common for all mice
[   42.200326] EISA: Probing bus 0 at eisa.0
[   42.200333] Cannot allocate resource for EISA slot 1
[   42.200336] Cannot allocate resource for EISA slot 2
[   42.200338] Cannot allocate resource for EISA slot 3
[   42.200357] EISA: Detected 0 cards.
[   42.200361] cpuidle: using governor ladder
[   42.200363] cpuidle: using governor menu
[   42.200449] NET: Registered protocol family 1
[   42.200482] Using IPI No-Shortcut mode
[   42.200513] registered taskstats version 1
[   42.200624]   Magic number: 0:507:648
[   42.200679]   hash matches device ptydd
[   42.200755] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   42.200757] EDD information not available.
[   42.200965] Freeing unused kernel memory: 368k freed
[   42.200993] Write protecting the kernel read-only data: 801k
[   43.445709] fuse init (API version 7.9)
[   43.470048] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   43.470064] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   43.751136] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   43.751141] Copyright (c) 1999-2006 Intel Corporation.
[   43.751210] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   43.751225] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   43.753778] e1000: 0000:02:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:13:20:a2:95:32
[   43.814267] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   43.881421] usbcore: registered new interface driver usbfs
[   43.881449] usbcore: registered new interface driver hub
[   43.881614] usbcore: registered new device driver usb
[   43.883130] USB Universal Host Controller Interface driver v3.0
[   43.883184] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   43.883196] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   43.883200] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   43.883415] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   43.883444] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00003080
[   43.883595] usb usb1: configuration #1 chosen from 1 choice
[   43.883624] hub 1-0:1.0: USB hub found
[   43.883631] hub 1-0:1.0: 2 ports detected
[   43.985584] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   43.985597] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   43.985602] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   43.985630] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   43.985660] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003060
[   43.985791] usb usb2: configuration #1 chosen from 1 choice
[   43.985821] hub 2-0:1.0: USB hub found
[   43.985828] hub 2-0:1.0: 2 ports detected
[   44.004012] SCSI subsystem initialized
[   44.040603] libata version 3.00 loaded.
[   44.089408] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   44.089422] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   44.089427] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   44.089455] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   44.089485] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003040
[   44.089614] usb usb3: configuration #1 chosen from 1 choice
[   44.089644] hub 3-0:1.0: USB hub found
[   44.089651] hub 3-0:1.0: 2 ports detected
[   44.193145] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   44.193158] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   44.193162] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   44.193190] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   44.193220] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003020
[   44.193351] usb usb4: configuration #1 chosen from 1 choice
[   44.193382] hub 4-0:1.0: USB hub found
[   44.193389] hub 4-0:1.0: 2 ports detected
[   44.296989] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   44.297006] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   44.297011] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   44.297050] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   44.300945] ehci_hcd 0000:00:1d.7: debug port 1
[   44.300952] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   44.300960] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x55204400
[   44.331761] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   44.343733] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   44.343866] usb usb5: configuration #1 chosen from 1 choice
[   44.343898] hub 5-0:1.0: USB hub found
[   44.343905] hub 5-0:1.0: 8 ports detected
[   44.447765] ACPI: PCI Interrupt 0000:05:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   44.497491] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[55004000-550047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   44.498161] ahci 0000:00:1f.2: version 3.0
[   44.498194] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   44.982449] usb 5-8: new high speed USB device using ehci_hcd and address 3
[   45.188247] usb 5-8: configuration #1 chosen from 1 choice
[   45.425556] usb 2-1: new low speed USB device using uhci_hcd and address 3
[   45.498429] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl RAID mode
[   45.498434] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part 
[   45.498440] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   45.498727] scsi0 : ahci
[   45.498997] scsi1 : ahci
[   45.499201] scsi2 : ahci
[   45.499406] scsi3 : ahci
[   45.499503] ata1: SATA max UDMA/133 abar m1024@0x55204000 port 0x55204100 irq 219
[   45.499506] ata2: SATA max UDMA/133 abar m1024@0x55204000 port 0x55204180 irq 219
[   45.499510] ata3: SATA max UDMA/133 abar m1024@0x55204000 port 0x55204200 irq 219
[   45.499513] ata4: SATA max UDMA/133 abar m1024@0x55204000 port 0x55204280 irq 219
[   45.601634] usb 2-1: configuration #1 chosen from 1 choice
[   45.605215] usbcore: registered new interface driver libusual
[   45.611180] Initializing USB Mass Storage driver...
[   45.611953] scsi4 : SCSI emulation for USB Mass Storage devices
[   45.612034] usbcore: registered new interface driver usb-storage
[   45.612040] USB Mass Storage support registered.
[   45.612154] usb-storage: device found at 3
[   45.612156] usb-storage: waiting for device to settle before scanning
[   45.769007] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00902700019902b7]
[   45.808795] ata1: SATA link down (SStatus 0 SControl 300)
[   46.120159] ata2: SATA link down (SStatus 0 SControl 300)
[   46.432530] ata3: SATA link down (SStatus 0 SControl 300)
[   46.906579] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   46.907173] ata4.00: ATA-7: ST3250310AS, 3.AAC, max UDMA/133
[   46.907178] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   46.907895] ata4.00: configured for UDMA/133
[   46.908054] scsi 3:0:0:0: Direct-Access     ATA      ST3250310AS      3.AA PQ: 0 ANSI: 5
[   46.912861] ata_piix 0000:00:1f.1: version 2.12
[   46.912882] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   46.912922] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   46.914370] scsi5 : ata_piix
[   46.914433] scsi6 : ata_piix
[   46.914979] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x30b0 irq 14
[   46.914982] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x30b8 irq 15
[   46.920963] Driver 'sd' needs updating - please use bus_type methods
[   46.921053] sd 3:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   46.921069] sd 3:0:0:0: [sda] Write Protect is off
[   46.921073] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   46.921097] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.921155] sd 3:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   46.921170] sd 3:0:0:0: [sda] Write Protect is off
[   46.921173] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   46.921197] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.921201]  sda: sda1 sda2 < sda5 >
[   46.954895] sd 3:0:0:0: [sda] Attached SCSI disk
[   46.970779] usbcore: registered new interface driver hiddev
[   46.973529] sd 3:0:0:0: Attached scsi generic sg0 type 0
[   46.985103] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input1
[   47.007773] input,hidraw0: USB HID v1.10 Keyboard [CHESEN USB Keyboard] on usb-0000:00:1d.1-1
[   47.033803] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.1/input/input2
[   47.042428] input,hidraw1: USB HID v1.10 Device [CHESEN USB Keyboard] on usb-0000:00:1d.1-1
[   47.042451] usbcore: registered new interface driver usbhid
[   47.042456] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   47.421873] ata5.01: ATAPI: SONY DVD-ROM DDU1615, FFS1, max UDMA/66
[   47.593461] ata5.01: configured for UDMA/66
[   47.593505] ata6: port disabled. ignoring.
[   47.594078] scsi 5:0:1:0: CD-ROM            SONY     DVD-ROM DDU1615  FFS1 PQ: 0 ANSI: 5
[   47.594172] scsi 5:0:1:0: Attached scsi generic sg1 type 5
[   47.609061] Driver 'sr' needs updating - please use bus_type methods
[   47.612160] sr0: scsi3-mmc drive: 4x/40x cd/rw xa/form2 cdda tray
[   47.612164] Uniform CD-ROM driver Revision: 3.20
[   47.612220] sr 5:0:1:0: Attached scsi CD-ROM sr0
[   47.677332] Attempting manual resume
[   47.677336] swsusp: Resume From Partition 8:5
[   47.677338] PM: Checking swsusp image.
[   47.677488] PM: Resume from disk failed.
[   47.703816] kjournald starting.  Commit interval 5 seconds
[   47.703824] EXT3-fs: mounted filesystem with ordered data mode.
[   50.604919] usb-storage: device scan complete
[   50.609039] scsi 4:0:0:0: Direct-Access     Sony     USB   HS-MS      4.38 PQ: 0 ANSI: 0
[   50.612522] scsi 4:0:0:1: Direct-Access     Sony     USB   HS-CF      4.38 PQ: 0 ANSI: 0
[   50.616140] scsi 4:0:0:2: Direct-Access     Sony     USB   HS-SM/xD   4.38 PQ: 0 ANSI: 0
[   50.619383] scsi 4:0:0:3: Direct-Access     Sony     USB   HS-SD MMC  4.38 PQ: 0 ANSI: 0
[   50.624405] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   50.624444] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   50.628639] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   50.628675] sd 4:0:0:1: Attached scsi generic sg3 type 0
[   50.633505] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[   50.633541] sd 4:0:0:2: Attached scsi generic sg4 type 0
[   50.683280] sd 4:0:0:3: [sde] Attached SCSI removable disk
[   50.683319] sd 4:0:0:3: Attached scsi generic sg5 type 0
[   53.306800] Linux agpgart interface v0.102
[   53.416345] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   53.454576] intel_rng: Firmware space is locked read-only. If you can't or
[   53.454579] intel_rng: don't want to disable this in firmware setup, and if
[   53.454581] intel_rng: you are certain that your system has a functional
[   53.454582] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   53.469545] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   53.619121] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   53.658164] input: Power Button (FF) as /devices/virtual/input/input4
[   53.682207] ACPI: Power Button (FF) [PWRF]
[   53.682291] input: Sleep Button (CM) as /devices/virtual/input/input5
[   53.713892] ACPI: Sleep Button (CM) [SLPB]
[   53.797767] iTCO_vendor_support: vendor-support=0
[   53.826565] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   53.888679] logips2pp: Detected unknown logitech mouse model 101
[   54.242130] nvidia: module license 'NVIDIA' taints kernel.
[   54.364378] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[   54.566448] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   54.566485] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   54.618987] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   54.618998] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   54.619144] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   54.622893] parport_pc 00:07: reported by Plug and Play ACPI
[   54.622922] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   54.753334] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   54.753363] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   55.922383] lp0: using parport0 (interrupt-driven).
[   55.987578] Adding 3020180k swap on /dev/sda5.  Priority:-1 extents:1 across:3020180k
[   56.539888] EXT3 FS on sda1, internal journal
[   57.688709] ip_tables: (C) 2000-2006 Netfilter Core Team
[   58.111645] No dock devices found.
[   59.232880] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   59.232886] apm: disabled - APM is not SMP safe.
[   59.897205] ppdev: user-space parallel port driver
[   60.120164] audit(1227641805.292:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5189 profile="/usr/sbin/cupsd" namespace="default"
[   61.729827] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[   61.729834] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   61.818522] Bluetooth: Core ver 2.11
[   61.818850] NET: Registered protocol family 31
[   61.818854] Bluetooth: HCI device and connection manager initialized
[   61.818858] Bluetooth: HCI socket layer initialized
[   61.836183] Bluetooth: L2CAP ver 2.9
[   61.836189] Bluetooth: L2CAP socket layer initialized
[   61.897415] Bluetooth: RFCOMM socket layer initialized
[   61.897431] Bluetooth: RFCOMM TTY layer initialized
[   61.897433] Bluetooth: RFCOMM ver 1.8
[   66.048377] NET: Registered protocol family 17
[   71.393828] NET: Registered protocol family 10
[   71.394153] lo: Disabled Privacy Extensions
[   81.468977] eth0: no IPv6 routers present





lsmod
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
snd_hda_intel         344856  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
evdev                  13056  4 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
nvidia               7825536  34 
snd_seq_dummy           4868  0 
i2c_core               24832  1 nvidia
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
serio_raw               7940  0 
snd_timer              24836  2 snd_pcm,snd_seq
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                40336  0 
button                  9232  0 
pcspkr                  4224  0 
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              25492  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
soundcore               8800  1 snd
agpgart                34760  2 nvidia,intel_agp
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
pata_acpi               8320  0 
sg                     36880  0 
usbhid                 32128  0 
hid                    38784  1 usbhid
sd_mod                 30720  3 
ata_piix               19588  0 
usb_storage            73664  0 
libusual               19108  1 usb_storage
ata_generic             8324  0 
ahci                   28548  2 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
libata                159344  4 pata_acpi,ata_piix,ata_generic,ahci
scsi_mod              151436  6 sbp2,sr_mod,sg,sd_mod,usb_storage,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  6 usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
e1000                 126016  0 
thermal                16796  0 
processor              37384  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 




lspci
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




sudo lswh | less
 description: Desktop Computer
    product: VGC-RB54G
    vendor: Sony Corporation
    version: R4953933
    serial: 28223831-3002054
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=63079234-2D07-11DA-85D8-001320A29532
  *-core
       description: Motherboard
       product: PRAGUE
       vendor: Intel Corporation
       physical id: 0
       version: AAD12395-205
       serial: BTPR53901281
       slot: Base Board Chassis Location
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 15.4.4
          serial: 0000-0F44-0000-0000-0000-0000
          size: 2800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 cl
flush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 1
             slot: Unknown
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 2
 slot: Unknown
             size: 1MiB
             capacity: 1MiB
             capabilities: asynchronous internal write-back unified
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
     *-cpu:1
          description: CPU
          vendor: Intel(R) Corporation
          physical id: 3
          bus info: cpu@1
          version: 15.4.4
          serial: 0000-0F44-0000-0000-0000-0000
          size: 2800MHz
          capacity: 4GHz
          clock: 200MHz
          capabilities: ht
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 4
             slot: Unknown
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 5
             slot: Unknown
             size: 1MiB
             capacity: 1MiB
             capabilities: asynchronous internal write-back unified
 *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 6
          version: PR94510J.04T.0080.2005.0916.1738 (09/16/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: 0x36345436343030304855332E374120202020
             vendor: 0xC100000000000000
             physical id: 0
             serial: 0x0122CA14
             slot: J6H1
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 1
             serial: NO DIMM
             slot: J6H2
        *-bank:2
description: DIMM Synchronous 533 MHz (1.9 ns)
             product: 0x36345436343030304855332E374120202020
             vendor: 0xC100000000000000
             physical id: 2
             serial: 0x0122DE12
             slot: J6J1
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 3
             serial: NO DIMM
             slot: J6J2
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
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
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
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
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
             capabilities: pm msi pciexpress bus_master cap_list
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
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
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
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=1.0-1 ip=192.168.0.180 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
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
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
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
             capabilities: pm debug ehci bus_master cap_list
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
                capabilities: pm bus_master cap_list
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
                capabilities: pm ohci bus_master cap_list
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
             logical name: scsi5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD reader
                product: DVD-ROM DDU1615
                vendor: SONY
                physical id: 0.1.0
                bus info: scsi@5:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: FFS1
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=open
        *-storage
             description: RAID bus controller
             product: 82801GR/GH (ICH7 Family) SATA RAID Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
product: ST3250310AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 5RY0TP5F
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00038e00
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: cb2ad040-245e-4363-b16d-5f83b9b01cc8
                   size: 230GiB
                   capacity: 230GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2004-01-18 21:54:36 filesystem=ext3 modified=2008-11-25 14:36:41 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-11-25 14:36:41 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sda2
                   size: 2949MiB
                   capacity: 2949MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2949MiB
capabilities: nofs
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
          bus info: usb@5:8
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: USB   HS-MS
             vendor: Sony
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 4.38
             serial: 3
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             product: USB   HS-CF
             vendor: Sony
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
             version: 4.38
             capabilities: removable
           *-medium
 physical id: 0
                logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             product: USB   HS-SM/xD
             vendor: Sony
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
             version: 4.38
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             product: USB   HS-SD MMC
             vendor: Sony
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
             version: 4.38
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sde






sudo dmidecode
# dmidecode 2.9
SMBIOS 2.3 present.
36 structures occupying 1598 bytes.
Table at 0x000E5BC0.

Handle 0x0000, DMI type 4, 35 bytes
Processor Information
	Socket Designation: Not Specified
	Type: Central Processor
	Family: Pentium 4
	Manufacturer: Intel(R) Corporation
	ID: 44 0F 00 00 FF FB EB BF
	Signature: Type 0, Family 15, Model 4, Stepping 4
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Hyper-threading technology)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Intel(R) Pentium(R) D CPU 2.80GHz
	Voltage: 3.0 V
	External Clock: 200 MHz
	Max Speed: 4000 MHz
	Current Speed: 2800 MHz
	Status: Populated, Enabled
	Upgrade: Other
	L1 Cache Handle: 0x0001
	L2 Cache Handle: 0x0002
	L3 Cache Handle: Not Provided
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

Handle 0x0001, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Unknown
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 16 KB
	Maximum Size: 16 KB
	Supported SRAM Types:
		Asynchronous
	Installed SRAM Type: Asynchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Data
	Associativity: 8-way Set-associative

Handle 0x0002, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Unknown
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 1024 KB
	Maximum Size: 1024 KB
	Supported SRAM Types:
		Asynchronous
	Installed SRAM Type: Asynchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 8-way Set-associative

Handle 0x0003, DMI type 4, 35 bytes
Processor Information
	Socket Designation: Not Specified
	Type: Central Processor
	Family: Pentium 4
	Manufacturer: Intel(R) Corporation
	ID: 44 0F 00 00 FF FB EB BF
	Signature: Type 0, Family 15, Model 4, Stepping 4
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Hyper-threading technology)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Intel(R) Pentium(R) D CPU 2.80GHz
	Voltage: 3.0 V
	External Clock: 200 MHz
	Max Speed: 4000 MHz
	Current Speed: 2800 MHz
	Status: Populated, Enabled
	Upgrade: Other
	L1 Cache Handle: 0x0004
	L2 Cache Handle: 0x0005
	L3 Cache Handle: Not Provided
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

Handle 0x0004, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Unknown
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 16 KB
	Maximum Size: 16 KB
	Supported SRAM Types:
		Asynchronous
	Installed SRAM Type: Asynchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Data
	Associativity: 8-way Set-associative

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Unknown
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 1024 KB
	Maximum Size: 1024 KB
	Supported SRAM Types:
		Asynchronous
	Installed SRAM Type: Asynchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 8-way Set-associative

Handle 0x0006, DMI type 0, 20 bytes
BIOS Information
	Vendor: Intel Corp.
	Version: PR94510J.04T.0080.2005.0916.1738
	Release Date: 09/16/2005
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 512 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported

Handle 0x0007, DMI type 1, 25 bytes
System Information
	Manufacturer: Sony Corporation
	Product Name: VGC-RB54G
	Version: R4953933
	Serial Number: 28223831-3002054
	UUID: 63079234-2D07-11DA-85D8-001320A29532
	Wake-up Type: Power Switch

Handle 0x0008, DMI type 2, 20 bytes
Base Board Information
	Manufacturer: Intel Corporation
	Product Name: PRAGUE
	Version: AAD12395-205
	Serial Number: BTPR53901281
	Asset Tag: Base Board Asset Tag
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Base Board Chassis Location
	Chassis Handle: 0x0009
	Type: Unknown
	Contained Object Handles: 0

Handle 0x0009, DMI type 3, 17 bytes
Chassis Information
	Manufacturer: Sony Corporation
	Type: Desktop
	Lock: Not Present
	Version: Chassis Version
	Serial Number: Chassis Serial
	Asset Tag: no asset tag
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Other
	Security Status: Other
	OEM Information: 0x00000000

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: PRIMARY
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: SECONDARY
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: ATX_PWR
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x000D, DMI type 9, 13 bytes
System Slot Information
	Designation: PCIE X16 SLOT
	Type: x16 PCI Express
	Current Usage: In Use
	Length: Short
	ID: 11
	Characteristics:
		3.3 V is provided

Handle 0x000E, DMI type 9, 13 bytes
System Slot Information
	Designation: PCIE X1 SLOT 1
	Type: x1 PCI Express
	Current Usage: Available
	Length: Short
	ID: 12
	Characteristics:
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x000F, DMI type 9, 13 bytes
System Slot Information
	Designation: PCIE X1 SLOT 2
	Type: x1 PCI Express
	Current Usage: Available
	Length: Short
	ID: 13
	Characteristics:
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0010, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI SLOT 1
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 1
	Characteristics:
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0011, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI SLOT 2
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 2
	Characteristics:
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0012, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Disabled
	Description: Intel(R) Extreme Graphics 3 Controller

Handle 0x0013, DMI type 10, 6 bytes
On Board Device Information
	Type: Ethernet
	Status: Enabled
	Description: Intel (R) 82562 Ethernet Device

Handle 0x0014, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Enabled
	Description: Intel(R) Azalia Audio Device

Handle 0x0015, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		enUS
	Currently Installed Language: enUS

Handle 0x0016, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x0017, DMI type 11, 5 bytes
OEM Strings
	String 1: UCV162CEUM
	String 2: RB
	String 3: P1920000000070C8E1B8F98F6634
	String 4: NTSC
	String 5: OEM String 5

Handle 0x0018, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Error Information Handle: Not Provided
	Number Of Devices: 4

Handle 0x0019, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0018
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: J6H1
	Bank Locator: CHAN A DIMM 0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 533 MHz (1.9 ns)
	Manufacturer: 0xC100000000000000
	Serial Number: 0x0122CA14
	Asset Tag: Unknown
	Part Number: 0x36345436343030304855332E374120202020

Handle 0x001A, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0001FFFFFFF
	Range Size: 512 MB
	Physical Device Handle: 0x0019
	Memory Array Mapped Address Handle: 0x001F
	Partition Row Position: 1
	Interleave Position: 1
	Interleaved Data Depth: 1

Handle 0x001B, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0018
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: J6H2
	Bank Locator: CHAN A DIMM 1
	Type: DDR2
	Type Detail: None
	Speed: Unknown
	Manufacturer: NO DIMM
	Serial Number: NO DIMM
	Asset Tag: NO DIMM
	Part Number: NO DIMM

Handle 0x001C, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0018
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: J6J1
	Bank Locator: CHAN B DIMM 0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 533 MHz (1.9 ns)
	Manufacturer: 0xC100000000000000
	Serial Number: 0x0122DE12
	Asset Tag: Unknown
	Part Number: 0x36345436343030304855332E374120202020

Handle 0x001D, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00020000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 512 MB
	Physical Device Handle: 0x001C
	Memory Array Mapped Address Handle: 0x001F
	Partition Row Position: 2
	Interleave Position: 2
	Interleaved Data Depth: 1

Handle 0x001E, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0018
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: J6J2
	Bank Locator: CHAN B DIMM 1
	Type: DDR2
	Type Detail: None
	Speed: Unknown
	Manufacturer: NO DIMM
	Serial Number: NO DIMM
	Asset Tag: NO DIMM
	Part Number: NO DIMM

Handle 0x001F, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 1 GB
	Physical Array Handle: 0x0018
	Partition Width: 0

Handle 0x0020, DMI type 187, 9 bytes
OEM-specific Type
	Header and Data:
		BB 09 20 00 19 00 03 15 02

Handle 0x0021, DMI type 187, 9 bytes
OEM-specific Type
	Header and Data:
		BB 09 21 00 1C 00 03 15 02

Handle 0x0022, DMI type 136, 6 bytes
OEM-specific Type
	Header and Data:
		88 06 22 00 5A 5A

Handle 0xFFFD, DMI type 127, 4 bytes
End Of Table


hope this is helpful

---

### Post by linux_tech on 2008-11-25
Try running harddrive diagnostics test, if possible use the manufacturers diagnostics as they are usually the best

---

### Post by hyburn on 2008-11-25
it says no errors logged, thats good right?

here is the output from the smartctl

smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

```
=== START OF INFORMATION SECTION ===
Device Model:     ST3250310AS
Serial Number:    5RY0TP5F
Firmware Version: 3.AAC
User Capacity:    250,059,350,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Nov 25 21:13:24 2008 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 430) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  64) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   118   100   006    Pre-fail  Always       -       197708587
  3 Spin_Up_Time            0x0003   097   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       49
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   065   060   030    Pre-fail  Always       -       3516075
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       406
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       49
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   061   048   045    Old_age   Always       -       655884327
194 Temperature_Celsius     0x0022   039   052   000    Old_age   Always       -       39 (Lifetime Min/Max 0/17)
195 Hardware_ECC_Recovered  0x001a   073   064   000    Old_age   Always       -       122572415
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

---

### Post by psusi on 2008-11-25
What make you think this has anything to do with your hard disk?  "Chassis Failure" literally means someone backed a dump truck over your computer, or something similar that would crush the case.  Since that wouldn't make much sense, my next best guess is that it is a bad translation on the part of the bios authors and they are trying to tell you that someone has opened the case and possibly tampered with the innards of the machine.

---

### Post by hyburn on 2008-11-25
I am working with an open case. is this going to lock me out?

---

### Post by linux_tech on 2008-11-25
I don't see any problems so far.  Do you get the error every time you boot?

---

### Post by hyburn on 2008-11-25
no not every time, just every now and then

can I get your help with something else?

I want to have little shell scripts written so I can run it from my desktop and have the basic commands like dmesg, lsmod, and all that which you needed to help me out. im just trying to use my ubuntu to stay effiecient

heres what I have so far

#!/bin/sh
echo “here are your dmesg results”
dmesg

it doesnt hold the results. I think im missing a line in this code. can you tell me what that command is?

---

### Post by linux_tech on 2008-11-26
Here are 2 ways to hold results in window using your script-
```
#!/bin/sh
xterm -hold -e dmesg
```
or
```
#!/bin/sh
stay=`dmesg`
xmessage "$stay" 
```

note-You need to make executable-
```
chmod u+x script.sh
```
(chmod 755 script.sh or chmod +x script.sh will also work)

Some other good cmds to gather info are :
```

lshw 
uname -a 
lspci 
free -m
df -h
lsmod | head
htop
cat /proc/cpuinfo
sudo dmidecode

``` 

You may also like sysinfo but you will need to install it 1st-
```
sudo apt-get install sysinfo
```

/var/log contains system messages for troubleshooting
To view logs in a graphical display is easier-
```
gnome-system-log & 
```

A good hardware report generator-
```
sudo apt-get install hardinfo
```
To start type-hardinfo

Another good application called installation-report can be installed through Synaptic, (try scripting output to a file)  
```
#!/bin/sh
report-hw>>hw_inventory

```

---

