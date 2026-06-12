---
title: "Understanding and solving boot errors and warnings"
date: 2010-03-16
forum: Hardware
---

### Post by HotForLinux on 2010-03-16
After booting this system, the graphical session was half freezed. I just logged out and in and everything seems to work fine.

Anyway I'd like to understand what happened before it is too late. I decided to post here the output of **dmesg** because there are many other old errors/warnings for which i'd like to receive help, advice and support for understanding, handling, reparing or improving all these things.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-27-generic (buildd@vernadsky) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)) #1 SMP Mon Feb 22 19:00:31 UTC 2010 (Ubuntu 2.6.24-27.67-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005f7dfffc (usable)
[    0.000000]  BIOS-e820: 000000005f7dfffc - 000000005f7fffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000005f7fffc0 - 000000005f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 631MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 391135) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   391135
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   391135
[    0.000000] On node 0 totalpages: 391135
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1263 pages used for memmap
[    0.000000]   HighMem zone: 160496 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00E5010 checksum 0
[    0.000000] ACPI: RSDP 000E5010, 0014 (r0 TOSINV)
[    0.000000] ACPI: RSDT 5F7F86C7, 0034 (r1 INSYDE RSDT_000      100 ABCD    10200)
[    0.000000] ACPI: FACP 5F7FFB30, 0074 (r1 TOSINV FACP_000      100 0000    10200)
[    0.000000] ACPI: DSDT 5F7F8D10, 6E13 (r1 TOSINV SONOMA       1004 INTL  2002036)
[    0.000000] ACPI: FACS 5F7FFFC0, 0040
[    0.000000] ACPI: MCFG 5F7FFBC0, 003C (r1 INSYDE MCFG_000 30303030 0000 30303030)
[    0.000000] ACPI: SSDT 5F7F88B5, 0237 (r1  PmRef  Cpu0Ist     3000 INTL 20030522)
[    0.000000] ACPI: SSDT 5F7F86FB, 01BA (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
[    0.000000] ACPI: DMI detected: Toshiba
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 5f800000:a0700000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 388080
[    0.000000] Kernel command line: root=UUID=101d90ae-ebe6-48a2-b01b-51421c9cbfc7 ro vga=791
**[COLOR=DarkOrange][    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"[/COLOR]**
[    0.000000] mapped APIC to ffffb000 (01c01000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1596.088 MHz processor.
[    9.973770] Console: colour dummy device 80x25
[    9.973775] console [tty0] enabled
[    9.974261] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    9.974738] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.049457] Memory: 1538440k/1564540k available (2182k kernel code, 24904k reserved, 1005k data, 368k init, 647036k highmem)
[   10.049479] virtual kernel memory layout:
[   10.049480]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   10.049482]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   10.049483]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   10.049484]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   10.049486]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   10.049487]       .data : 0xc032189a - 0xc041cdc4   (1005 kB)
[   10.049488]       .text : 0xc0100000 - 0xc032189a   (2182 kB)
[   10.049513] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.049579] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   10.049642] Calibrating delay loop (skipped), using tsc calculated value.. 3192.17 BogoMIPS (lpj=6384352)
[   10.049687] Security Framework initialized
[COLOR=DarkOrange][   10.049702] SELinux:  Disabled at boot.[/COLOR]
[   10.049724] AppArmor: AppArmor initialized
[COLOR=DarkOrange]**[   10.049732] Failure registering capabilities with primary security module.**[/COLOR]
[   10.049745] Mount-cache hash table entries: 512
[   10.049918] Initializing cgroup subsys ns
[   10.049932] Initializing cgroup subsys cpuacct
[   10.049950] CPU: After generic identify, caps: afe9f9ff 00000000 00000000 00000000 00000180 00000000 00000000 00000000
[   10.049964] CPU: L1 I cache: 32K, L1 D cache: 32K
[   10.049969] CPU: L2 cache: 2048K
[   10.049975] CPU: After all inits, caps: afe9f9ff 00000000 00000000 00042040 00000180 00000000 00000000 00000000
[   10.049986] Compat vDSO mapped to ffffe000.
[   10.050004] Checking 'hlt' instruction... OK.
[   10.066011] SMP alternatives: switching to UP code
[   10.068004] Freeing SMP alternatives: 11k freed
[   10.068136] Early unpacking initramfs... done
[   10.468896] ACPI: Core revision 20070126
**[COLOR=DarkOrange][   10.468980] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.[/COLOR]**
[   10.471901] ACPI: setting ELCR to 0200 (from 0c20)
[   10.543292] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 08
[   10.543310] SMP motherboard not detected.
[COLOR=DarkOrange]** [   10.543314] Local APIC not detected. Using dummy APIC emulation.**[/COLOR]
[   10.543362] Brought up 1 CPUs
[   10.543382] CPU0 attaching sched-domain:
[   10.543385]  domain 0: span 01
[   10.543387]   groups: 01
[   10.543578] net_namespace: 64 bytes
[   10.543590] Booting paravirtualized kernel on bare hardware
[   10.544075] Time: 13:49:10  Date: 03/16/10
[   10.544106] NET: Registered protocol family 16
[   10.544310] EISA bus registered
[   10.544334] ACPI: bus type pci registered
[   10.544469] PCI: PCI BIOS revision 2.10 entry at 0xea7d4, last bus=5
[   10.544475] PCI: Using configuration type 1
[   10.544487] Setting up standard PCI resources
[   10.547095] ACPI: EC: Look up EC in DSDT
[   10.554445] ACPI: Interpreter enabled
[   10.554451] ACPI: (supports S0 S3 S4 S5)
[   10.554468] ACPI: Using PIC for interrupt routing
[   10.575305] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[   10.575312] ACPI: EC: driver started in poll mode
[   10.575355] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.576115] Force enabled HPET at base address 0xfed00000
[   10.576121] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   10.576129] PCI quirk: region 1300-133f claimed by ICH6 GPIO
[   10.576955] PCI: Transparent bridge - 0000:00:1e.0
[   10.577043] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   10.577454] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   10.577631] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   10.577823] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   10.604576] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *11)
[   10.604746] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *10 11)
[   10.604857] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 *11)
[   10.604967] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10 *11)
[   10.605076] ACPI: PCI Interrupt Link [LNKE] (IRQs *5 11)
[COLOR=DarkOrange] [   10.605185] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 10) *0, disabled.[/COLOR]
[   10.605337] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *11
[   10.605447] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 10) *11
[   10.605582] ACPI: Power Resource [PFA1] (off)
[   10.605626] Linux Plug and Play Support v0.97 (c) Adam Belay
[COLOR=DarkOrange][   10.605660] pnp: PnP ACPI init
[   10.605669] ACPI: bus type pnp registered
[   10.613722] pnp: PnP ACPI: found 9 devices
[   10.613727] ACPI: ACPI bus type pnp unregistered
[   10.613733] PnPBIOS: Disabled by ACPI PNP[/COLOR]
[   10.613960] PCI: Using ACPI for IRQ routing
[   10.613966] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
**[COLOR=DarkOrange][   10.614005] PCI: Cannot allocate resource region 0 of device 0000:05:06.0[/COLOR]**
[   10.636265] NET: Registered protocol family 8
[   10.636270] NET: Registered protocol family 20
[   10.636451] hpet clockevent registered
[   10.636458] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   10.636465] hpet0: 3 64-bit timers, 14318180 Hz
[   10.637500] AppArmor: AppArmor Filesystem Enabled
[   10.640452] Time: tsc clocksource has been installed.
[   10.648482] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[   10.648490] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[   10.648496] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[   10.648502] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[   10.648509] system 00:01: iomem range 0xf0008000-0xf000bfff has been reserved
[   10.648515] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[   10.648521] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[   10.648527] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[   10.648537] system 00:05: ioport range 0x300-0x36f has been reserved
[   10.648543] system 00:05: ioport range 0x800-0x80f has been reserved
[   10.648549] system 00:05: ioport range 0x1000-0x107f has been reserved
[   10.648555] system 00:05: ioport range 0x1300-0x133f has been reserved
[   10.648561] system 00:05: iomem range 0xe0000000-0xefffffff has been reserved
[   10.648567] system 00:05: iomem range 0xf0008000-0xf000bfff has been reserved
[   10.648574] system 00:05: iomem range 0xfed14000-0xfed17fff has been reserved
[   10.648580] system 00:05: iomem range 0xfed18000-0xfed18fff has been reserved
[   10.648586] system 00:05: iomem range 0xfed19000-0xfed19fff has been reserved
[   10.678979] PCI: Bridge: 0000:00:1c.0
[   10.678985]   IO window: c000-dfff
[   10.678993]   MEM window: cc000000-cfffffff
[   10.678999]   PREFETCH window: 9c000000-9fffffff
[   10.679008] PCI: Bridge: 0000:00:1c.1
[   10.679013]   IO window: a000-bfff
[   10.679020]   MEM window: c8000000-cbffffff
[   10.679027]   PREFETCH window: 98000000-9bffffff
[   10.679042] PCI: Bus 6, cardbus bridge: 0000:05:06.0
[   10.679047]   IO window: 00008000-000080ff
[   10.679054]   IO window: 00008400-000084ff
[   10.679061]   PREFETCH window: 88000000-8bffffff
[   10.679069]   MEM window: bc000000-bfffffff
[   10.679076] PCI: Bridge: 0000:00:1e.0
[   10.679081]   IO window: 8000-9fff
[   10.679089]   MEM window: b8000000-c7ffffff
[   10.679095]   PREFETCH window: 88000000-97ffffff
[   10.679292] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   10.679298] PCI: setting IRQ 10 as level-triggered
[   10.679303] ACPI: PCI Interrupt 0000:00:1c.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   10.679315] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   10.679493] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   10.679499] PCI: setting IRQ 11 as level-triggered
[   10.679504] ACPI: PCI Interrupt 0000:00:1c.1[B] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   10.679515] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   10.679528] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   10.679701] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   10.679706] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   10.679726] NET: Registered protocol family 2
[   10.716441] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   10.716670] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   10.717474] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   10.717942] TCP: Hash tables configured (established 131072 bind 65536)
[   10.717950] TCP reno registered
[   10.728529] checking if image is initramfs... it is
[   11.139993] Switched to high resolution mode on CPU 0
[   11.514365] Freeing initrd memory: 7717k freed
[   11.514963] audit: initializing netlink socket (disabled)
[   11.514987] audit(1268747351.396:1): initialized
[   11.515197] highmem bounce pool size: 64 pages
[   11.517248] VFS: Disk quotas dquot_6.5.1
[   11.517333] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.517495] io scheduler noop registered
[   11.517500] io scheduler anticipatory registered
[   11.517505] io scheduler deadline registered
[   11.517519] io scheduler cfq registered (default)
[   11.517535] Boot video device is 0000:00:02.0
[   11.517736] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   11.517788] assign_interrupt_mode Found MSI capability
[   11.517838] Allocate Port Service[0000:00:1c.0:pcie00]
[   11.517881] Allocate Port Service[0000:00:1c.0:pcie02]
[   11.517977] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   11.518029] assign_interrupt_mode Found MSI capability
[   11.518074] Allocate Port Service[0000:00:1c.1:pcie00]
[   11.518109] Allocate Port Service[0000:00:1c.1:pcie02]
[   11.518361] isapnp: Scanning for PnP cards...
[   11.872070] isapnp: No Plug & Play device found
[   11.900312] Real Time Clock Driver v1.12ac
[   11.900438] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.901290] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 5
[   11.901297] PCI: setting IRQ 5 as level-triggered
[   11.901303] ACPI: PCI Interrupt 0000:00:1e.3[B] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[COLOR=DarkOrange] [   11.901319] ACPI: PCI interrupt for device 0000:00:1e.3 disabled[/COLOR]
[   11.901997] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.902075] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   11.902179] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.905248] i8042.c: Detected active multiplexing controller, rev 1.1.
[   11.906863] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.906870] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   11.906875] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   11.906880] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   11.906885] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   11.907439] mice: PS/2 mouse device common for all mice
[   11.907555] EISA: Probing bus 0 at eisa.0
[B][COLOR=DarkOrange][   11.907566] Cannot allocate resource for EISA slot 1
[   11.907592] Cannot allocate resource for EISA slot 8[/COLOR][/B]
[   11.907597] EISA: Detected 0 cards.
[   11.907602] cpuidle: using governor ladder
[   11.907606] cpuidle: using governor menu
[   11.907707] NET: Registered protocol family 1
[   11.907737] Using IPI No-Shortcut mode
[   11.907777] registered taskstats version 1
[   11.907897]   Magic number: 2:349:837
[   11.907958]   hash matches device ptyu3
[COLOR=YellowGreen][B][   11.908002] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   11.908007] EDD information not available.[/B][/COLOR]
[   11.908208] Freeing unused kernel memory: 368k freed
[   11.908240] Write protecting the kernel read-only data: 803k
[   11.915158] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   12.003330] vesafb: framebuffer at 0xa0000000, mapped to 0xf8880000, using 3072k, total 7872k
[   12.003345] vesafb: mode is 1024x768x16, linelength=2048, pages=4
[   12.003350] vesafb: scrolling: redraw
[   12.003355] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[   12.003475] Console: switching to colour frame buffer device 128x48
[   12.018823] fb0: VESA VGA frame buffer device
[   12.131080] fuse init (API version 7.9)
[   12.143431] ACPI: Transitioning device [FAN1] to D3
[   12.143580] ACPI: Transitioning device [FAN1] to D3
[   12.143725] ACPI: Fan [FAN1] (off)
[   12.149879] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   12.150073] ACPI: Processor [CPU0] (supports 8 throttling states)
**[COLOR=DarkOrange][   12.150274] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126][/COLOR]**
[   12.215093] ACPI: Thermal Zone [TZCR] (39 C)
[   12.223071] ACPI: Thermal Zone [TZCL] (16 C)
[COLOR=DarkRed]**[   12.634582] Clocksource tsc unstable (delta = -4672948208 ns)**[/COLOR]
[   12.638571] Time: hpet clocksource has been installed.
[   12.829017] usbcore: registered new interface driver usbfs
[   12.829212] usbcore: registered new interface driver hub
[   12.834469] usbcore: registered new device driver usb
[   12.846408] USB Universal Host Controller Interface driver v3.0
[   12.852302] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[   12.857903] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   12.863733] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   12.863738] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   12.906693] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   12.912656] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200
[   12.946669] usb usb1: configuration #1 chosen from 1 choice
[   12.961248] hub 1-0:1.0: USB hub found
[   12.967238] hub 1-0:1.0: 2 ports detected
[   13.078512] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   13.084582] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   13.090821] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.090826] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.097049] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   13.103306] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001220
[   13.109621] usb usb2: configuration #1 chosen from 1 choice
[   13.115896] hub 2-0:1.0: USB hub found
[   13.126120] hub 2-0:1.0: 2 ports detected
[   13.151986] SCSI subsystem initialized
[   13.220036] libata version 3.00 loaded.
[   13.246109] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   13.252197] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   13.252202] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.258213] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   13.264199] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001240
[   13.270225] usb usb3: configuration #1 chosen from 1 choice
[   13.276191] hub 3-0:1.0: USB hub found
[   13.282061] hub 3-0:1.0: 2 ports detected
[   13.389979] ACPI: PCI Interrupt 0000:00:1d.3[D] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   13.396014] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   13.396019] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   13.402074] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   13.408164] uhci_hcd 0000:00:1d.3: irq 11, io base 0x00001260
[   13.414391] usb usb4: configuration #1 chosen from 1 choice
[   13.420571] hub 4-0:1.0: USB hub found
[   13.426686] hub 4-0:1.0: 2 ports detected
[   13.534006] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[   13.540029] ACPI: PCI Interrupt 0000:00:1d.7[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   13.546104] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.546109] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.553387] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   13.563496] ehci_hcd 0000:00:1d.7: debug port 1
**[COLOR=DarkOrange][   13.569627] PCI: cache line size of 32 is not supported by device 0000:00:1d.7[/COLOR]**
[   13.569635] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xf4000000
[   13.589663] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.596000] usb usb5: configuration #1 chosen from 1 choice
[   13.602309] hub 5-0:1.0: USB hub found
[   13.608500] hub 5-0:1.0: 8 ports detected
[   13.717989] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 6
[   13.724150] PCI: setting IRQ 6 as level-triggered
[   13.724155] ACPI: PCI Interrupt 0000:05:06.2[C] -> Link [LNKG] -> GSI 6 (level, low) -> IRQ 6
[   13.780295] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   13.797399] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   13.804307] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[COLOR=Red][   13.804321] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   13.816892] ahci 0000:00:1f.2: version 3.0
[   13.816905] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   13.823802] ACPI: PCI interrupt for device 0000:00:1f.2 disabled[/COLOR]
**[COLOR=Red][   13.830600] ahci: probe of 0000:00:1f.2 failed with error -22[/COLOR]**
[   13.840591] ata_piix 0000:00:1f.2: version 2.12
[   13.840597] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   13.989456] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   13.996428] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   13.996507] scsi0 : ata_piix
[   14.003493] scsi1 : ata_piix
[   14.011187] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[   14.018127] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[   14.028290] ata1.00: ATA-6: IC25N080ATMR04-0, MO4OAD4A, max UDMA/100
[   14.035110] ata1.00: 156301488 sectors, multi 16: LBA48 
[   14.041814] ata1.00: applying bridge limits
[   14.050072] ata1.00: configured for UDMA/100
[   14.062046] ata2.00: ATAPI: MATSHITADVD-RAM UJ-830S, 1.00, max UDMA/33
[   14.075570] ata2.00: configured for UDMA/33
[   14.082305] scsi 0:0:0:0: Direct-Access     ATA      IC25N080ATMR04-0 MO4O PQ: 0 ANSI: 5
[   14.089816] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-830S  1.00 PQ: 0 ANSI: 5
**[COLOR=Red][   14.106852] Driver 'sd' needs updating - please use bus_type methods[/COLOR]**
[   14.113761] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   14.122238] sd 0:0:0:0: [sda] Write Protect is off
[   14.129014] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.129287] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.138783] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
**[COLOR=Red][   14.145713] Driver 'sr' needs updating - please use bus_type methods[/COLOR]**
[   14.153123] sd 0:0:0:0: [sda] Write Protect is off
[   14.160104] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.160124] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.167884]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 > sda3
[   14.176802] sd 0:0:0:0: [sda] Attached SCSI disk
[   14.187342] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   14.194408] Uniform CD-ROM driver Revision: 3.20
[   14.201471] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   14.210096] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   14.217175] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   14.271372] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00080da0d1bbae17]
[   14.367421] Attempting manual resume
[   14.374483] swsusp: Resume From Partition 8:6
[   14.374485] PM: Checking swsusp image.
**[COLOR=DarkOrange][   14.374626] PM: Resume from disk failed.[/COLOR]**
[   14.397692] ReiserFS: sda5: found reiserfs format "3.6" with standard journal
[   14.404917] ReiserFS: sda5: using ordered data mode
[   14.412579] ReiserFS: sda5: journal params: device sda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   14.427850] ReiserFS: sda5: checking transaction log (sda5)
[   14.436050] ReiserFS: sda5: Using r5 hash to sort names
[   17.940375] Linux agpgart interface v0.102
[   18.063962] iTCO_vendor_support: vendor-support=0
[   18.195849] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   18.202754] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   18.209335] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.443660] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   18.531535] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.599477] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.671395] agpgart: Detected an Intel 915GM Chipset.
[   18.678391] agpgart: Detected 7932K stolen memory.
[   18.706314] agpgart: AGP aperture is 256M @ 0xa0000000
[   19.023742] input: Power Button (FF) as /devices/virtual/input/input3
[   19.054973] ACPI: Power Button (FF) [PWRF]
[   19.061404] input: Lid Switch as /devices/virtual/input/input4
[   19.083050] ACPI: Lid Switch [LID0]
[   19.089432] input: Power Button (CM) as /devices/virtual/input/input5
[   19.122918] ACPI: Power Button (CM) [PWRB]
[   19.131029] ACPI: AC Adapter [AC] (on-line)
[   19.218800] intel_rng: FWH not detected
[   19.322911] ACPI: Battery Slot [BAT1] (battery present)
[   19.514518] ieee80211_crypt: registered algorithm 'NULL'
[   19.562464] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   19.568698] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   20.241165] Yenta: CardBus bridge found at 0000:05:06.0 [1179:ff10]
[   20.247643] Yenta: Enabling burst memory read transactions
[   20.254097] Yenta: Using CSCINT to route CSC interrupts to PCI
[   20.260452] Yenta: Routing CardBus interrupts to PCI
[   20.266703] Yenta TI: socket 0000:05:06.0, mfunc 0x01aa1b22, devctl 0x66
[   20.502099] Yenta: ISA IRQ mask 0x0098, PCI irq 11
[   20.508327] Socket status: 30000006
[   20.514533] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   20.520794] pcmcia: parent PCI bridge I/O window: 0x8000 - 0x9fff
[   20.527881] cs: IO port probe 0x8000-0x9fff: clean.
[   20.534506] pcmcia: parent PCI bridge Memory window: 0xb8000000 - 0xc7ffffff
[   20.540613] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x97ffffff
[   20.570161] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   20.601438] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   20.609625] ACPI: PCI Interrupt 0000:05:06.3[D] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   20.673515] sdhci: Secure Digital Host Controller Interface driver
[   20.679993] sdhci: Copyright(c) Pierre Ossman
[   20.686885] sdhci: SDHCI controller found at 0000:05:06.4 [104c:8034] (rev 0)
[   20.693518] ACPI: PCI Interrupt 0000:05:06.4[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   20.700372] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   20.708466] mmc0: SDHCI at 0xb800a000 irq 11 DMA
[   20.715350] sdhci:slot1: Will use DMA mode even though HW doesn't fully claim to support it.
[   20.724471] mmc1: SDHCI at 0xb800a100 irq 11 DMA
[   20.731577] sdhci:slot2: Will use DMA mode even though HW doesn't fully claim to support it.
[   20.761280] mmc2: SDHCI at 0xb800a200 irq 11 DMA
[   20.896982] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   20.904497] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   20.917940] ACPI: PCI Interrupt 0000:05:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   20.971287] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   21.505485] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa56eb1, caps: 0x804713/0x0
[   21.513247] synaptics: Toshiba Satellite M45 detected, limiting rate to 40pps.
[   21.581422] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   22.758629] ipw2200: Radio Frequency Kill Switch is On:
[   22.758632] Kill switch must be turned off for wireless networking to work.
[   22.785308] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   22.793361] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   22.801507] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   22.801537] sky2 0000:01:00.0: v1.20 addr 0xcc000000 irq 11 Yukon-FE (0xb7) rev 1
[   22.836378] udev: renamed network interface eth0 to eth1
[   22.855019] sky2 0000:01:00.0: No interrupt generated using MSI, switching to INTx mode.
[   22.863580] sky2 eth0: addr 00:a0:d1:bb:ae:17
[   22.871791] ACPI: PCI Interrupt 0000:00:1e.2[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   22.880268] cs: IO port probe 0x100-0x3af: clean.
[   22.889962] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   22.898931] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   22.899311] cs: IO port probe 0x820-0x8ff: clean.
[   22.908115] cs: IO port probe 0xc00-0xcf7: clean.
[   22.916994] cs: IO port probe 0xa00-0xaff: clean.
[   22.931724] sky2 eth0: enabling interface
[   23.010957] intel8x0_measure_ac97_clock: measured 55449 usecs
[   23.018826] intel8x0: clocking to 48000
[   23.166606] lp: driver loaded but no devices found
[   23.356257] NET: Registered protocol family 17
[   23.415416] Adding 1277128k swap on /dev/sda6.  Priority:-1 extents:1 across:1277128k
[   23.852449] device-mapper: uevent: version 1.0.3
[   23.852481] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   25.384677] ip_tables: (C) 2000-2006 Netfilter Core Team
[   25.438670] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   25.546042] NET: Registered protocol family 10
[   25.546281] lo: Disabled Privacy Extensions
[   25.546892] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.569499] ip6_tables: (C) 2000-2006 Netfilter Core Team
**[COLOR=Red][   26.363421] ACPI: Error installing notify handler[/COLOR]**
[   26.363481] No dock devices found.
[   27.099027] ACPI: PCI Interrupt 0000:00:1e.3[B] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   27.099050] PCI: Setting latency timer of device 0000:00:1e.3 to 64
[   27.401786] ppdev: user-space parallel port driver
[   27.468794] audit(1268743810.733:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5576 profile="/usr/sbin/cupsd" namespace="default"
[   27.552558] sky2 eth0: disabling interface
[   27.647932] apm: BIOS not found.
[   27.707898] sky2 eth0: enabling interface
[   27.711722] ADDRCONF(NETDEV_UP): eth0: link is not ready
**[COLOR=DarkRed][   56.998312] Marking TSC unstable due to: cpufreq changes.[/COLOR]**
[   28.737509] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   30.144776] [drm] Initialized drm 1.1.0 20060810
[   60.357414] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   60.357430] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   60.357546] [drm] Initialized i915 1.6.0 20060119 on minor 0
[COLOR=Red][B][   87.334819] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   87.337360] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[   87.337363]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[/B][/COLOR] [B][COLOR=Red][   87.337366]          res 51/14:10:10:14:fb/00:00:00:00:00/b0 Emask 0x1 (device error)
[   87.339940] ata2.00: status: { DRDY ERR }
[   87.344926] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   87.347462] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[   87.347465]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[   87.347468]          res 41/04:00:00:04:eb/00:00:00:00:00/a0 Emask 0x1 (device error)
[   87.350049] ata2.00: status: { DRDY ERR }
[   87.352634] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[   87.355306] sr: Sense Key : Aborted Command [current] [descriptor]
[   87.355313] sr: Add. Sense: No additional sense information
[   87.360447] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   87.363093] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[   87.363096]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[   87.363099]          res 51/14:10:10:14:fb/00:00:00:00:00/b0 Emask 0x1 (device error)
[   87.365768] ata2.00: status: { DRDY ERR }
[   87.368419] sr 1:0:0:0: ioctl_internal_command return code = 8000002
[   87.368423]    : Sense Key : Aborted Command [current] [descriptor]
[   87.368430]    : Add. Sense: No additional sense information
[   52.753619] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   52.755355] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[   52.755357]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[   52.755359]          res 41/04:00:00:04:eb/00:00:00:00:00/a0 Emask 0x1 (device error)
[   52.757048] ata2.00: status: { DRDY ERR }
[   52.764196] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   52.765898] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[   52.765900]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[   52.765901]          res 51/14:10:10:14:fb/00:00:00:00:00/b0 Emask 0x1 (device error)
[   52.767588] ata2.00: status: { DRDY ERR }
[   52.769816] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
[   52.771607] sr: Sense Key : Aborted Command [current] [descriptor]
[   52.771611] sr: Add. Sense: No additional sense information
[   43.989698] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   43.991183] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[   43.991185]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[   43.991186]          res 51/14:10:10:14:fb/00:00:00:00:00/b0 Emask 0x1 (device error)
[   43.992657] ata2.00: status: { DRDY ERR }
[   43.994137] sr 1:0:0:0: ioctl_internal_command return code = 8000002
[   43.994139]    : Sense Key : Aborted Command [current] [descriptor]
[   43.994143]    : Add. Sense: No additional sense information
[   88.700717] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   88.703561] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[   88.703564]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[   88.703567]          res 51/14:10:10:14:fb/00:00:00:00:00/b0 Emask 0x1 (device error)
[   88.706401] ata2.00: status: { DRDY ERR }
[  108.297609] spurious 8259A interrupt: IRQ7.[/COLOR][/B]

```Thanx

---

### Post by HotForLinux on 2010-03-23
- Bump -

---

### Post by Muzer on 2010-03-23
Looks to me like disk read errors - either your HDD is failing, or for some reason coming out of suspend (which seemed to fail according to the log) made the HDD go weird.

---

### Post by HotForLinux on 2010-03-31
> **Muzer said:**
> Looks to me like disk read errors - either your HDD is failing, or for some reason coming out of suspend (which seemed to fail according to the log) made the HDD go weird.


I don't see why you say that. I see some warnings of old drivers. How to update them?? But, well I have been hibernating very often.
After hibernating I always receive a message in the lower-right corner of the graphic display saying that the hibernation failed (nothing  else) but I see everything perfectly ok.

I will post again *dmesg*'s output now that the boot didn't went through an hibernating hibernation recovery.

---

### Post by HotForLinux on 2010-03-31
Now the output is different, but there are still many error and warning messages which I'd like to understand and deal with. Please help:

**dmesg:**

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-27-generic (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Fri Mar 12 01:10:31 UTC 2010 (Ubuntu 2.6.24-27.68-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005f7dfffc (usable)
[    0.000000]  BIOS-e820: 000000005f7dfffc - 000000005f7fffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000005f7fffc0 - 000000005f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 631MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 391135) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   391135
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   391135
[    0.000000] On node 0 totalpages: 391135
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1263 pages used for memmap
[    0.000000]   HighMem zone: 160496 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00E5010 checksum 0
[    0.000000] ACPI: RSDP 000E5010, 0014 (r0 TOSINV)
[    0.000000] ACPI: RSDT 5F7F86C7, 0034 (r1 INSYDE RSDT_000      100 ABCD    10200)
[    0.000000] ACPI: FACP 5F7FFB30, 0074 (r1 TOSINV FACP_000      100 0000    10200)
[    0.000000] ACPI: DSDT 5F7F8D10, 6E13 (r1 TOSINV SONOMA       1004 INTL  2002036)
[    0.000000] ACPI: FACS 5F7FFFC0, 0040
[    0.000000] ACPI: MCFG 5F7FFBC0, 003C (r1 INSYDE MCFG_000 30303030 0000 30303030)
[    0.000000] ACPI: SSDT 5F7F88B5, 0237 (r1  PmRef  Cpu0Ist     3000 INTL 20030522)
[    0.000000] ACPI: SSDT 5F7F86FB, 01BA (r1  PmRef  Cpu0Cst     3001 INTL 20030522)
[    0.000000] ACPI: DMI detected: Toshiba
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 5f800000:a0700000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 388080
[    0.000000] Kernel command line: root=UUID=101d90ae-ebe6-48a2-b01b-51421c9cbfc7 ro vga=791
[COLOR=Orange]**[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"**[/COLOR]
[    0.000000] mapped APIC to ffffb000 (01c01000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1596.016 MHz processor.
[   29.381878] Console: colour dummy device 80x25
[   29.381884] console [tty0] enabled
[   29.382372] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   29.382849] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   29.457884] Memory: 1538440k/1564540k available (2182k kernel code, 24904k reserved, 1005k data, 368k init, 647036k highmem)
[   29.457906] virtual kernel memory layout:
[   29.457908]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   29.457909]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   29.457910]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   29.457912]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   29.457913]       .init : 0xc0423000 - 0xc047f000   ( 368 kB)
[   29.457914]       .data : 0xc03218ca - 0xc041cdc4   (1005 kB)
[   29.457916]       .text : 0xc0100000 - 0xc03218ca   (2182 kB)
[   29.457941] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   29.458007] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   29.458071] Calibrating delay loop (skipped), using tsc calculated value.. 3192.03 BogoMIPS (lpj=6384064)
[   29.458117] Security Framework initialized
[COLOR=DarkOrange][   29.458131] SELinux:  Disabled at boot.[/COLOR]
[   29.458154] AppArmor: AppArmor initialized
[COLOR=DarkOrange]**[   29.458161] Failure registering capabilities with primary security module.**[/COLOR]
[   29.458176] Mount-cache hash table entries: 512
[   29.458348] Initializing cgroup subsys ns
[   29.458361] Initializing cgroup subsys cpuacct
[   29.458378] CPU: After generic identify, caps: afe9f9ff 00000000 00000000 00000000 00000180 00000000 00000000 00000000
[   29.458390] CPU: L1 I cache: 32K, L1 D cache: 32K
[   29.458396] CPU: L2 cache: 2048K
[   29.458403] CPU: After all inits, caps: afe9f9ff 00000000 00000000 00042040 00000180 00000000 00000000 00000000
[   29.458414] Compat vDSO mapped to ffffe000.
[   29.458433] Checking 'hlt' instruction... OK.
[   29.474437] SMP alternatives: switching to UP code
[   29.476432] Freeing SMP alternatives: 11k freed
[   29.476564] Early unpacking initramfs... done
[   29.877531] ACPI: Core revision 20070126
**[COLOR=DarkOrange][   29.877614] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.[/COLOR]**
[   29.880534] ACPI: setting ELCR to 0200 (from 0c20)
[   29.952446] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 08
[   29.952463] SMP motherboard not detected.
**[COLOR=DarkOrange][   29.952467] Local APIC not detected. Using dummy APIC emulation.[/COLOR]**
[   29.952515] Brought up 1 CPUs
[   29.952535] CPU0 attaching sched-domain:
[   29.952538]  domain 0: span 01
[   29.952539]   groups: 01
[   29.952732] net_namespace: 64 bytes
[   29.952743] Booting paravirtualized kernel on bare hardware
[   29.953229] Time: 16:32:39  Date: 03/31/10
[   29.953260] NET: Registered protocol family 16
[   29.953464] EISA bus registered
[   29.953488] ACPI: bus type pci registered
[   29.953623] PCI: PCI BIOS revision 2.10 entry at 0xea7d4, last bus=5
[   29.953629] PCI: Using configuration type 1
[   29.953640] Setting up standard PCI resources
[   29.956245] ACPI: EC: Look up EC in DSDT
[   29.963598] ACPI: Interpreter enabled
[   29.963603] ACPI: (supports S0 S3 S4 S5)
[   29.963620] ACPI: Using PIC for interrupt routing
[   29.984461] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[   29.984468] ACPI: EC: driver started in poll mode
[   29.984511] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   29.985272] Force enabled HPET at base address 0xfed00000
[   29.985279] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   29.985287] PCI quirk: region 1300-133f claimed by ICH6 GPIO
[   29.986112] PCI: Transparent bridge - 0000:00:1e.0
[   29.986199] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   29.986611] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   29.986788] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   29.986980] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   30.013730] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *11)
[   30.013900] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *10 11)
[   30.014011] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 *11)
[   30.014120] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10 *11)
[   30.014230] ACPI: PCI Interrupt Link [LNKE] (IRQs *5 11)
[COLOR=DarkOrange][   30.014339] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 10) *0, disabled.[/COLOR]
[   30.014490] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *11
[   30.014599] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 10) *11
[   30.014735] ACPI: Power Resource [PFA1] (off)
[   30.014779] Linux Plug and Play Support v0.97 (c) Adam Belay
[COLOR=DarkOrange][   30.014813] pnp: PnP ACPI init
[   30.014822] ACPI: bus type pnp registered
[   30.022878] pnp: PnP ACPI: found 9 devices
[   30.022884] ACPI: ACPI bus type pnp unregistered
[   30.022889] PnPBIOS: Disabled by ACPI PNP[/COLOR]
[   30.023118] PCI: Using ACPI for IRQ routing
[   30.023123] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
**[COLOR=DarkOrange][   30.023162] PCI: Cannot allocate resource region 0 of device 0000:05:06.0[/COLOR]**
[   30.045419] NET: Registered protocol family 8
[   30.045424] NET: Registered protocol family 20
[   30.045604] hpet clockevent registered
[   30.045611] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   30.045618] hpet0: 3 64-bit timers, 14318180 Hz
[   30.046653] AppArmor: AppArmor Filesystem Enabled
[   30.049605] Time: tsc clocksource has been installed.
[   30.057635] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[   30.057642] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[   30.057649] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[   30.057655] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[   30.057661] system 00:01: iomem range 0xf0008000-0xf000bfff has been reserved
[   30.057668] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[   30.057674] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[   30.057680] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[   30.057690] system 00:05: ioport range 0x300-0x36f has been reserved
[   30.057696] system 00:05: ioport range 0x800-0x80f has been reserved
[   30.057702] system 00:05: ioport range 0x1000-0x107f has been reserved
[   30.057708] system 00:05: ioport range 0x1300-0x133f has been reserved
[   30.057714] system 00:05: iomem range 0xe0000000-0xefffffff has been reserved
[   30.057720] system 00:05: iomem range 0xf0008000-0xf000bfff has been reserved
[   30.057726] system 00:05: iomem range 0xfed14000-0xfed17fff has been reserved
[   30.057733] system 00:05: iomem range 0xfed18000-0xfed18fff has been reserved
[   30.057739] system 00:05: iomem range 0xfed19000-0xfed19fff has been reserved
[   30.088133] PCI: Bridge: 0000:00:1c.0
[   30.088139]   IO window: c000-dfff
[   30.088147]   MEM window: cc000000-cfffffff
[   30.088154]   PREFETCH window: 9c000000-9fffffff
[   30.088162] PCI: Bridge: 0000:00:1c.1
[   30.088167]   IO window: a000-bfff
[   30.088174]   MEM window: c8000000-cbffffff
[   30.088181]   PREFETCH window: 98000000-9bffffff
[   30.088195] PCI: Bus 6, cardbus bridge: 0000:05:06.0
[   30.088200]   IO window: 00008000-000080ff
[   30.088208]   IO window: 00008400-000084ff
[   30.088215]   PREFETCH window: 88000000-8bffffff
[   30.088222]   MEM window: bc000000-bfffffff
[   30.088229] PCI: Bridge: 0000:00:1e.0
[   30.088234]   IO window: 8000-9fff
[   30.088242]   MEM window: b8000000-c7ffffff
[   30.088248]   PREFETCH window: 88000000-97ffffff
[   30.088444] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   30.088451] PCI: setting IRQ 10 as level-triggered
[   30.088456] ACPI: PCI Interrupt 0000:00:1c.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   30.088468] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   30.088646] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   30.088652] PCI: setting IRQ 11 as level-triggered
[   30.088656] ACPI: PCI Interrupt 0000:00:1c.1[B] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   30.088668] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   30.088681] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   30.088853] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   30.088859] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   30.088878] NET: Registered protocol family 2
[   30.125595] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   30.125824] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   30.126628] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   30.127097] TCP: Hash tables configured (established 131072 bind 65536)
[   30.127104] TCP reno registered
[   30.137685] checking if image is initramfs... it is
[   30.549147] Switched to high resolution mode on CPU 0
[   30.922539] Freeing initrd memory: 7717k freed
[   30.923136] audit: initializing netlink socket (disabled)
[   30.923158] audit(1270053160.396:1): initialized
[   30.923366] highmem bounce pool size: 64 pages
[   30.925414] VFS: Disk quotas dquot_6.5.1
[   30.925498] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   30.925659] io scheduler noop registered
[   30.925664] io scheduler anticipatory registered
[   30.925668] io scheduler deadline registered
[   30.925683] io scheduler cfq registered (default)
[   30.925699] Boot video device is 0000:00:02.0
[   30.925900] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   30.925953] assign_interrupt_mode Found MSI capability
[   30.926003] Allocate Port Service[0000:00:1c.0:pcie00]
[   30.926045] Allocate Port Service[0000:00:1c.0:pcie02]
[   30.926142] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   30.926193] assign_interrupt_mode Found MSI capability
[   30.926238] Allocate Port Service[0000:00:1c.1:pcie00]
[   30.926273] Allocate Port Service[0000:00:1c.1:pcie02]
[   30.926524] isapnp: Scanning for PnP cards...
[   31.280169] isapnp: No Plug & Play device found
[   31.308146] Real Time Clock Driver v1.12ac
[   31.308270] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   31.309329] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 5
[   31.309337] PCI: setting IRQ 5 as level-triggered
[   31.309342] ACPI: PCI Interrupt 0000:00:1e.3[B] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[COLOR=DarkOrange][   31.309358] ACPI: PCI interrupt for device 0000:00:1e.3 disabled[/COLOR]
[   31.310009] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.310087] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   31.310189] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   31.314827] i8042.c: Detected active multiplexing controller, rev 1.1.
[   31.316504] serio: i8042 KBD port at 0x60,0x64 irq 1
[   31.316511] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   31.316517] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   31.316522] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   31.316527] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   31.320449] mice: PS/2 mouse device common for all mice
[   31.320563] EISA: Probing bus 0 at eisa.0
[COLOR=DarkOrange][B][   31.320573] Cannot allocate resource for EISA slot 1
[   31.320600] Cannot allocate resource for EISA slot 8[/B][/COLOR]
[   31.320604] EISA: Detected 0 cards.
[   31.320610] cpuidle: using governor ladder
[   31.320614] cpuidle: using governor menu
[   31.320714] NET: Registered protocol family 1
[   31.320743] Using IPI No-Shortcut mode
[   31.320782] registered taskstats version 1
[   31.320902]   Magic number: 2:486:541
[B][COLOR=YellowGreen][   31.321002] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   31.321007] EDD information not available.[/COLOR][/B]
[   31.321210] Freeing unused kernel memory: 368k freed
[   31.321241] Write protecting the kernel read-only data: 803k
[   31.326281] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   31.416596] vesafb: framebuffer at 0xa0000000, mapped to 0xf8880000, using 3072k, total 7872k
[   31.416611] vesafb: mode is 1024x768x16, linelength=2048, pages=4
[   31.416616] vesafb: scrolling: redraw
[   31.416621] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[   31.416739] Console: switching to colour frame buffer device 128x48
[   31.432087] fb0: VESA VGA frame buffer device
[   31.544365] fuse init (API version 7.9)
[   31.556786] ACPI: Transitioning device [FAN1] to D3
[   31.556935] ACPI: Transitioning device [FAN1] to D3
[   31.557079] ACPI: Fan [FAN1] (off)
[   31.563222] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   31.563416] ACPI: Processor [CPU0] (supports 8 throttling states)
[   31.563617] **[COLOR=DarkOrange]ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126][/COLOR]**
[   31.628175] ACPI: Thermal Zone [TZCR] (36 C)
[   31.636150] ACPI: Thermal Zone [TZCL] (22 C)
**[COLOR=DarkRed][   32.043644] Clocksource tsc unstable (delta = -4679771927 ns)[/COLOR]**
[   32.047634] Time: hpet clocksource has been installed.
[   32.235530] usbcore: registered new interface driver usbfs
[   32.235725] usbcore: registered new interface driver hub
[   32.247477] usbcore: registered new device driver usb
[   32.254272] USB Universal Host Controller Interface driver v3.0
[   32.260159] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[   32.265781] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   32.271558] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   32.271562] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   32.307784] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   32.313762] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200
[   32.346034] usb usb1: configuration #1 chosen from 1 choice
[   32.352098] hub 1-0:1.0: USB hub found
[   32.379336] hub 1-0:1.0: 2 ports detected
[   32.491562] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   32.497668] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   32.503915] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   32.503920] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   32.510161] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   32.516438] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001220
[   32.522766] usb usb2: configuration #1 chosen from 1 choice
[   32.529005] hub 2-0:1.0: USB hub found
[   32.535401] hub 2-0:1.0: 2 ports detected
[   32.565504] SCSI subsystem initialized
[   32.638589] libata version 3.00 loaded.
[   32.643208] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   32.649287] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   32.649292] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   32.655306] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   32.661299] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001240
[   32.667331] usb usb3: configuration #1 chosen from 1 choice
[   32.673299] hub 3-0:1.0: USB hub found
[   32.682205] hub 3-0:1.0: 2 ports detected
[   32.791056] ACPI: PCI Interrupt 0000:00:1d.3[D] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   32.797106] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   32.797111] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   32.803506] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   32.809609] uhci_hcd 0000:00:1d.3: irq 11, io base 0x00001260
[   32.815856] usb usb4: configuration #1 chosen from 1 choice
[   32.822042] hub 4-0:1.0: USB hub found
[   32.828167] hub 4-0:1.0: 2 ports detected
[   32.935085] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[   32.941119] ACPI: PCI Interrupt 0000:00:1d.7[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   32.947208] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   32.947213] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   32.954507] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   32.964621] ehci_hcd 0000:00:1d.7: debug port 1
**[COLOR=DarkOrange][   32.970764] PCI: cache line size of 32 is not supported by device 0000:00:1d.7[/COLOR]**
[   32.970772] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xf4000000
[   32.990734] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   32.997089] usb usb5: configuration #1 chosen from 1 choice
[   33.003403] hub 5-0:1.0: USB hub found
[   33.009612] hub 5-0:1.0: 8 ports detected
[   33.119058] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 6
[   33.125258] PCI: setting IRQ 6 as level-triggered
[   33.125264] ACPI: PCI Interrupt 0000:05:06.2[C] -> Link [LNKG] -> GSI 6 (level, low) -> IRQ 6
[   33.181415] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   33.198585] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   33.205490] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[COLOR=Red][   33.205505] ACPI: PCI interrupt for device 0000:00:1f.2 disabled[/COLOR]
[   33.218111] ahci 0000:00:1f.2: version 3.0
[COLOR=Red][   33.218124] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   33.225037] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
**[   33.231853] ahci: probe of 0000:00:1f.2 failed with error -22**[/COLOR]
[   33.241859] ata_piix 0000:00:1f.2: version 2.12
[   33.241865] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   33.402348] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   33.409343] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   33.410248] scsi0 : ata_piix
[   33.417300] scsi1 : ata_piix
[   33.424997] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[   33.431939] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[   33.444421] ata1.00: ATA-6: IC25N080ATMR04-0, MO4OAD4A, max UDMA/100
[   33.451248] ata1.00: 156301488 sectors, multi 16: LBA48 
[   33.457960] ata1.00: applying bridge limits
[   33.466160] ata1.00: configured for UDMA/100
[   33.477644] ata2.00: ATAPI: MAT****ADVD-RAM UJ-830S, 1.00, max UDMA/33
[   33.487227] ata2.00: configured for UDMA/33
[   33.493968] scsi 0:0:0:0: Direct-Access     ATA      IC25N080ATMR04-0 MO4O PQ: 0 ANSI: 5
[   33.501477] scsi 1:0:0:0: CD-ROM            MAT****A DVD-RAM UJ-830S  1.00 PQ: 0 ANSI: 5
[COLOR=Red]**[   33.518485] Driver 'sd' needs updating - please use bus_type methods**[/COLOR]
[   33.525417] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   33.533923] sd 0:0:0:0: [sda] Write Protect is off
[   33.540711] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.543274] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
**[COLOR=Red][   33.550433] Driver 'sr' needs updating - please use bus_type methods[/COLOR]**
[   33.557905] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   33.564929] sd 0:0:0:0: [sda] Write Protect is off
[   33.571947] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.572345] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.580144]  sda:<7>ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00080da0d1bbae17]
[   33.591772]  sda1 sda2 < sda5 sda6 sda7 sda8 > sda3
[   33.600274] sd 0:0:0:0: [sda] Attached SCSI disk
[   33.613827] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   33.620886] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   33.632573] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   33.639682] Uniform CD-ROM driver Revision: 3.20
[   33.646758] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   33.788956] Attempting manual resume
[   33.796105] swsusp: Resume From Partition 8:6
[   33.796107] PM: Checking swsusp image.
[COLOR=DarkOrange]**[   33.796238] PM: Resume from disk failed.**[/COLOR]
[   33.819359] ReiserFS: sda5: found reiserfs format "3.6" with standard journal
[   33.826608] ReiserFS: sda5: using ordered data mode
[   33.834364] ReiserFS: sda5: journal params: device sda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   33.849643] ReiserFS: sda5: checking transaction log (sda5)
[   33.857655] ReiserFS: sda5: Using r5 hash to sort names
[   37.416551] Linux agpgart interface v0.102
[   37.541007] iTCO_vendor_support: vendor-support=0
[   37.632521] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   37.639438] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   37.646036] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   37.888170] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   37.960031] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   38.079944] agpgart: Detected an Intel 915GM Chipset.
[   38.087374] agpgart: Detected 7932K stolen memory.
[   38.114710] agpgart: AGP aperture is 256M @ 0xa0000000
[   38.231778] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   38.323809] input: Power Button (FF) as /devices/virtual/input/input3
[   38.355622] ACPI: Power Button (FF) [PWRF]
[   38.362082] input: Lid Switch as /devices/virtual/input/input4
[   38.387683] ACPI: Lid Switch [LID0]
[   38.394034] input: Power Button (CM) as /devices/virtual/input/input5
[   38.435569] ACPI: Power Button (CM) [PWRB]
[   38.479531] intel_rng: FWH not detected
[   38.787379] ACPI: Battery Slot [BAT1] (battery present)
[   38.835276] ACPI: AC Adapter [AC] (on-line)
[   39.054977] Yenta: CardBus bridge found at 0000:05:06.0 [1179:ff10]
[   39.061354] Yenta: Enabling burst memory read transactions
[   39.067646] Yenta: Using CSCINT to route CSC interrupts to PCI
[   39.073936] Yenta: Routing CardBus interrupts to PCI
[   39.080214] Yenta TI: socket 0000:05:06.0, mfunc 0x01aa1b22, devctl 0x66
[   39.150958] ieee80211_crypt: registered algorithm 'NULL'
[   39.234740] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   39.240991] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   39.315242] Yenta: ISA IRQ mask 0x0098, PCI irq 11
[   39.321500] Socket status: 30000006
[   39.327700] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   39.333981] pcmcia: parent PCI bridge I/O window: 0x8000 - 0x9fff
[   39.340268] cs: IO port probe 0x8000-0x9fff: clean.
[   39.346916] pcmcia: parent PCI bridge Memory window: 0xb8000000 - 0xc7ffffff
[   39.353048] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x97ffffff
[   39.864935] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   39.898076] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   40.041977] ACPI: PCI Interrupt 0000:05:06.3[D] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   40.321658] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   40.328226] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   40.349816] ACPI: PCI Interrupt 0000:05:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   40.397553] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   40.412170] sdhci: Secure Digital Host Controller Interface driver
[   40.419077] sdhci: Copyright(c) Pierre Ossman
[   40.969413] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa56eb1, caps: 0x804713/0x0
[   40.976493] synaptics: Toshiba Satellite M45 detected, limiting rate to 40pps.
[   41.040320] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   42.103350] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   42.110821] sdhci: SDHCI controller found at 0000:05:06.4 [104c:8034] (rev 0)
[   42.118310] ACPI: PCI Interrupt 0000:05:06.4[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   42.125990] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   42.135163] mmc0: SDHCI at 0xb800a000 irq 11 DMA
[   42.142789] sdhci:slot1: Will use DMA mode even though HW doesn't fully claim to support it.
[   42.152631] mmc1: SDHCI at 0xb800a100 irq 11 DMA
[   42.160370] sdhci:slot2: Will use DMA mode even though HW doesn't fully claim to support it.
[   42.185338] mmc2: SDHCI at 0xb800a200 irq 11 DMA
[   42.193204] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   42.201260] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   42.201290] sky2 0000:01:00.0: v1.20 addr 0xcc000000 irq 11 Yukon-FE (0xb7) rev 1
[   42.274004] udev: renamed network interface eth0 to eth1
[   42.298441] sky2 0000:01:00.0: No interrupt generated using MSI, switching to INTx mode.
[   42.307031] sky2 eth0: addr 00:a0:d1:bb:ae:17
[   42.315283] ACPI: PCI Interrupt 0000:00:1e.2[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   42.323621] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   42.323912] cs: IO port probe 0x100-0x3af: clean.
[   42.333578] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   42.342764] cs: IO port probe 0x820-0x8ff: clean.
[   42.351450] cs: IO port probe 0xc00-0xcf7: clean.
[   42.360197] cs: IO port probe 0xa00-0xaff: clean.
[   42.397126] ieee80211_crypt: registered algorithm 'WEP'
[   42.462204] sky2 eth0: enabling interface
[   42.558204] intel8x0_measure_ac97_clock: measured 55418 usecs
[   42.566116] intel8x0: clocking to 48000
[   42.715326] lp: driver loaded but no devices found
[   42.929703] Adding 1277128k swap on /dev/sda6.  Priority:-1 extents:1 across:1277128k
[   43.047404] NET: Registered protocol family 17
[   43.482453] device-mapper: uevent: version 1.0.3
[   43.482484] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   43.855554] NET: Registered protocol family 10
[   43.855779] lo: Disabled Privacy Extensions
[   43.856356] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   45.433322] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.487701] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   45.582126] ip6_tables: (C) 2000-2006 Netfilter Core Team
**[COLOR=Red][   46.379486] ACPI: Error installing notify handler[/COLOR]**
[   46.379546] No dock devices found.
[   46.535886] eth1: no IPv6 routers present
[   47.122358] ACPI: PCI Interrupt 0000:00:1e.3[B] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   47.122381] PCI: Setting latency timer of device 0000:00:1e.3 to 64
[   47.426071] ppdev: user-space parallel port driver
[   47.469773] audit(1270046022.742:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5758 profile="/usr/sbin/cupsd" namespace="default"
[   47.560908] sky2 eth0: disabling interface
[   47.666247] spurious 8259A interrupt: IRQ7.
[   47.671626] apm: BIOS not found.
[   47.822573] sky2 eth0: enabling interface
[   47.826386] ADDRCONF(NETDEV_UP): eth0: link is not ready
**[COLOR=DarkRed][   97.610112] Marking TSC unstable due to: cpufreq changes.[/COLOR]**
[  100.940763] [drm] Initialized drm 1.1.0 20060810
[  100.988314] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[  100.988331] PCI: Setting latency timer of device 0000:00:02.0 to 64
[  100.988459] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  368.989941] ACPI: EC: non-query interrupt received, switching to interrupt mode
```

---

### Post by HotForLinux on 2010-04-04
Still looking for help on this.

---

### Post by HotForLinux on 2010-05-25
- Bump -

---

### Post by josarn on 2010-05-27
Hi! I have recently become a regular dmesg output reader. I find myself not understanding things quite often and suspect there is no way of avoiding that. I really wanted to let you know that I think that the effort you put in understanding your linux box is worth your time. Have you tried making a google search with the text of the entry you don't understand?

---

### Post by HotForLinux on 2010-05-30
> **josarn said:**
> Hi! I have recently become a regular dmesg output reader. I find myself not understanding things quite often and suspect there is no way of avoiding that. I really wanted to let you know that I think that the effort you put in understanding your linux box is worth your time. Have you tried making a google search with the text of the entry you don't understand?
Yes and no, I have tried with some of them.

---

### Post by HotForLinux on 2011-06-16
- Bump -

---

