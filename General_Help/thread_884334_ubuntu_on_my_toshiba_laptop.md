---
title: "ubuntu on my toshiba laptop"
date: 2008-08-08
forum: General Help
---

### Post by endo666 on 2008-08-08
im trying to get online with my new laptop but ubuntu didnt load wired or wireless network drivers. it has the restricted wifi driver but i still dont have wifi either. any advice. it is a brand new laptop

toshiba satellite m305d-s4831

---

### Post by Taxman415a on 2008-08-08
Can you give the output of ```
sudo lspci
``` and ```
ifconfig -a
``` ?
Also if you know the relevant parts of the dmesg output to report that could help. What version of Ubuntu did you install?

The supposedly detailed tech specs I downloaded from toshiba.com for that model only list 
10/100 Ethernet
Integrated Wi-Fi compliant wireless:
    o Atheros 802.11b/g wireless-LAN

The Atheros may be good news since they just released a free and open source driver for (some of?) their 802.11n so that may help you eventually.

---

### Post by endo666 on 2008-08-08
> **Taxman415a said:**
> Can you give the output of ```
sudo lspci
``` and ```
ifconfig -a
``` ?
Also if you know the relevant parts of the dmesg output to report that could help. What version of Ubuntu did you install?

The supposedly detailed tech specs I downloaded from toshiba.com for that model only list 
10/100 Ethernet
Integrated Wi-Fi compliant wireless:
    o Atheros 802.11b/g wireless-LAN

The Atheros may be good news since they just released a free and open source driver for (some of?) their 802.11n so that may help you eventually.

you will have to give me a second i have to boot into ubuntu first then switch back to windows to post

i installed ubuntu 8.04

---

### Post by endo666 on 2008-08-08
here you go

> **Taxman415a said:**
> Can you give the output of ```
sudo lspci
``` 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Unknown device 9602
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4355 (rev 12)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
09:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
09:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)


> **Taxman415a said:**
> and ```
ifconfig -a
``` ?

sean@sean-laptop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by endo666 on 2008-08-08
> **Taxman415a said:**
> Also if you know the relevant parts of the dmesg output to report that could help. What version of Ubuntu did you install?

The supposedly detailed tech specs I downloaded from toshiba.com for that model only list 
10/100 Ethernet
Integrated Wi-Fi compliant wireless:
    o Atheros 802.11b/g wireless-LAN

The Atheros may be good news since they just released a free and open source driver for (some of?) their 802.11n so that may help you eventually.


[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2000.128 MHz processor.
[   14.485531] Console: colour VGA+ 80x25
[   14.485534] console [tty0] enabled
[   14.485806] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.486155] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.649219] Memory: 3064888k/4194304k available (2157k kernel code, 45452k reserved, 998k data, 364k init, 2194176k highmem)
[   14.649227] virtual kernel memory layout:
[   14.649228]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   14.649229]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.649230]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.649231]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.649232]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   14.649234]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   14.649235]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   14.649238] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.649270] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   14.649400] hpet clockevent registered
[   14.729250] Calibrating delay using timer specific routine.. 4003.49 BogoMIPS (lpj=8006992)
[   14.729270] Security Framework initialized
[   14.729274] SELinux:  Disabled at boot.
[   14.729287] AppArmor: AppArmor initialized
[   14.729291] Failure registering capabilities with primary security module.
[   14.729299] Mount-cache hash table entries: 512
[   14.729404] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000131f 00000000
[   14.729413] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.729415] CPU: L2 Cache: 512K (64 bytes/line)
[   14.729418] CPU 0(2) -> Core 0
[   14.729420] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000510 00002001 00000000 0000131f 00000000
[   14.729428] Compat vDSO mapped to ffffe000.
[   14.729437] Checking 'hlt' instruction... OK.
[   14.745595] SMP alternatives: switching to UP code
[   14.747206] Early unpacking initramfs... done
[   15.067284] ACPI: Core revision 20070126
[   15.067373] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.409061] CPU0: AMD Turion(tm) X2 Dual-Core Mobile RM-70 stepping 01
[   16.409079] SMP alternatives: switching to SMP code
[   16.409842] Booting processor 1/1 eip 3000
[   16.377978] Initializing CPU#1
[   16.455974] Calibrating delay using timer specific routine.. 4000.15 BogoMIPS (lpj=8000306)
[   16.455982] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000131f 00000000
[   16.455988] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   16.455990] CPU: L2 Cache: 512K (64 bytes/line)
[   16.455993] CPU 1(2) -> Core 1
[   16.455994] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000510 00002001 00000000 0000131f 00000000
[   16.498057] CPU1: AMD Turion(tm) X2 Dual-Core Mobile RM-70 stepping 01
[   16.498071] Total of 2 processors activated (8003.64 BogoMIPS).
[   16.498160] ENABLING IO-APIC IRQs
[   16.498325] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   16.645652] Brought up 2 CPUs
[   16.645675] CPU0 attaching sched-domain:
[   16.645677]  domain 0: span 03
[   16.645679]   groups: 01 02
[   16.645682] CPU1 attaching sched-domain:
[   16.645684]  domain 0: span 03
[   16.645685]   groups: 02 01
[   16.645871] net_namespace: 64 bytes
[   16.645877] Booting paravirtualized kernel on bare hardware
[   16.646304] Time: 21:27:09  Date: 08/08/08
[   16.646328] NET: Registered protocol family 16
[   16.646493] EISA bus registered
[   16.646497] ACPI: bus type pci registered
[   16.658929] PCI: PCI BIOS revision 3.00 entry at 0xfdc18, last bus=11
[   16.658931] PCI: Using configuration type 1
[   16.658933] Setting up standard PCI resources
[   16.660998] ACPI: EC: Look up EC in DSDT
[   16.663881] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   16.664504] ACPI: Interpreter enabled
[   16.664507] ACPI: (supports S0 S3 S4 S5)
[   16.664518] ACPI: Using IOAPIC for interrupt routing
[   16.670340] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[   16.670343] ACPI: EC: driver started in poll mode
[   16.670378] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.672305] PCI: Transparent bridge - 0000:00:14.4
[   16.672336] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.672637] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[   16.672753] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[   16.672867] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB10._PRT]
[   16.672994] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   16.673090] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   16.676272] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   16.676401] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   16.676529] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   16.676655] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   16.676782] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   16.676909] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   16.677036] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   16.677163] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   16.677288] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.677315] pnp: PnP ACPI init
[   16.677322] ACPI: bus type pnp registered
[   16.680075] pnp: PnP ACPI: found 11 devices
[   16.680077] ACPI: ACPI bus type pnp unregistered
[   16.680080] PnPBIOS: Disabled by ACPI PNP
[   16.680267] PCI: Using ACPI for IRQ routing
[   16.680269] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.680276] PCI: Cannot allocate resource region 7 of bridge 0000:00:07.0
[   16.680278] PCI: Cannot allocate resource region 8 of bridge 0000:00:07.0
[   16.680280] PCI: Cannot allocate resource region 9 of bridge 0000:00:07.0
[   16.757345] NET: Registered protocol family 8
[   16.757347] NET: Registered protocol family 20
[   16.757381] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   16.757385] hpet0: 4 32-bit timers, 14318180 Hz
[   16.758421] AppArmor: AppArmor Filesystem Enabled
[   16.761331] Time: hpet clocksource has been installed.
[   16.761345] Switched to high resolution mode on CPU 0
[   16.719586] Switched to high resolution mode on CPU 1
[   16.769317] system 00:01: iomem range 0xfec00000-0xfec10fff could not be reserved
[   16.769321] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   16.769328] system 00:08: ioport range 0x220-0x22f has been reserved
[   16.769331] system 00:08: ioport range 0x40b-0x40b has been reserved
[   16.769334] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   16.769336] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   16.769339] system 00:08: ioport range 0x530-0x537 has been reserved
[   16.769341] system 00:08: ioport range 0xc00-0xc01 has been reserved
[   16.769344] system 00:08: ioport range 0xc14-0xc14 has been reserved
[   16.769346] system 00:08: ioport range 0xc50-0xc52 has been reserved
[   16.769349] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[   16.769351] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[   16.769354] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[   16.769356] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[   16.769358] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[   16.769361] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[   16.769364] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[   16.769366] system 00:08: ioport range 0x8000-0x805f has been reserved
[   16.769369] system 00:08: ioport range 0xf40-0xf47 has been reserved
[   16.769371] system 00:08: ioport range 0x87f-0x87f has been reserved
[   16.769377] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   16.769380] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[   16.769382] system 00:09: iomem range 0x0-0x0 could not be reserved
[   16.769385] system 00:09: iomem range 0xff800000-0xff80ffff has been reserved
[   16.799701] PCI: Bridge: 0000:00:01.0
[   16.799704]   IO window: 9000-9fff
[   16.799708]   MEM window: cfd00000-cfefffff
[   16.799711]   PREFETCH window: d0000000-dfffffff
[   16.799715] PCI: Bridge: 0000:00:05.0
[   16.799717]   IO window: a000-afff
[   16.799720]   MEM window: f0400000-f04fffff
[   16.799723]   PREFETCH window: disabled.
[   16.799726] PCI: Bridge: 0000:00:07.0
[   16.799728]   IO window: disabled.
[   16.799731]   MEM window: disabled.
[   16.799733]   PREFETCH window: disabled.
[   16.799737] PCI: Bridge: 0000:00:0a.0
[   16.799738]   IO window: disabled.
[   16.799742]   MEM window: f0300000-f03fffff
[   16.799744]   PREFETCH window: disabled.
[   16.799753] PCI: Bridge: 0000:00:14.4
[   16.799754]   IO window: disabled.
[   16.799760]   MEM window: f0500000-f05fffff
[   16.799764]   PREFETCH window: disabled.
[   16.799790] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 16
[   16.799795] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   16.799803] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 19 (level, low) -> IRQ 17
[   16.799808] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   16.799817] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 18
[   16.799821] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   16.799838] NET: Registered protocol family 2
[   16.837217] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.837469] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.838116] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.838417] TCP: Hash tables configured (established 131072 bind 65536)
[   16.838419] TCP reno registered
[   16.849260] checking if image is initramfs...<6>ACPI: EC: non-query interrupt received, switching to interrupt mode
[   17.143267]  it is
[   17.467392] Freeing initrd memory: 7690k freed
[   17.467522] Simple Boot Flag at 0x37 set to 0x1
[   17.427309] audit: initializing netlink socket (disabled)
[   17.427324] audit(1218230828.384:1): initialized
[   17.427688] highmem bounce pool size: 64 pages
[   17.433388] VFS: Disk quotas dquot_6.5.1
[   17.433452] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.433569] io scheduler noop registered
[   17.433571] io scheduler anticipatory registered
[   17.433574] io scheduler deadline registered
[   17.433583] io scheduler cfq registered (default)
[   17.433759] Boot video device is 0000:01:05.0
[   17.433880] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   17.433911] assign_interrupt_mode Found MSI capability
[   17.433942] Allocate Port Service[0000:00:05.0:pcie00]
[   17.434020] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   17.434051] assign_interrupt_mode Found MSI capability
[   17.434081] Allocate Port Service[0000:00:07.0:pcie00]
[   17.434226] Allocate Port Service[0000:00:07.0:pcie02]
[   17.434298] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   17.434326] assign_interrupt_mode Found MSI capability
[   17.434353] Allocate Port Service[0000:00:0a.0:pcie00]
[   17.434778] isapnp: Scanning for PnP cards...
[   17.788056] isapnp: No Plug & Play device found
[   17.867677] Real Time Clock Driver v1.12ac
[   17.868204] hpet_resources: 0xfed00000 is busy
[   17.868226] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.871222] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.871284] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   17.871662] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   17.874007] i8042.c: Detected active multiplexing controller, rev 1.1.
[   17.875926] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.875931] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   17.875934] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   17.875937] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   17.875939] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   17.890379] mice: PS/2 mouse device common for all mice
[   17.890685] EISA: Probing bus 0 at eisa.0
[   17.890719] Cannot allocate resource for EISA slot 8
[   17.890721] EISA: Detected 0 cards.
[   17.890723] cpuidle: using governor ladder
[   17.890725] cpuidle: using governor menu
[   17.890806] NET: Registered protocol family 1
[   17.890830] Using IPI No-Shortcut mode
[   17.890860] registered taskstats version 1
[   17.890973]   Magic number: 4:766:499
[   17.891111] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   17.891113] EDD information not available.
[   17.891325] Freeing unused kernel memory: 364k freed
[   18.749094] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.135868] fuse init (API version 7.9)
[   19.200704] ACPI: Processor [CPU0] (supports 8 throttling states)
[   19.202447] ACPI: Thermal Zone [THRM] (64 C)
[   19.423707] SCSI subsystem initialized
[   19.447356] libata version 3.00 loaded.
[   19.449794] usbcore: registered new interface driver usbfs
[   19.449816] usbcore: registered new interface driver hub
[   19.450435] ahci 0000:00:11.0: version 3.0
[   19.450465] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 22 (level, low) -> IRQ 19
[   19.450490] ahci 0000:00:11.0: controller can't do PMP, turning off CAP_PMP
[   19.451004] usbcore: registered new device driver usb
[   19.460081] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   20.450076] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   20.450081] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck led clo pio slum part 
[   20.450420] scsi0 : ahci
[   20.450693] scsi1 : ahci
[   20.450825] scsi2 : ahci
[   20.450953] scsi3 : ahci
[   20.451052] ata1: SATA max UDMA/133 abar m1024@0xf0208000 port 0xf0208100 irq 19
[   20.451056] ata2: SATA max UDMA/133 abar m1024@0xf0208000 port 0xf0208180 irq 19
[   20.451060] ata3: SATA max UDMA/133 abar m1024@0xf0208000 port 0xf0208200 irq 19
[   20.451063] ata4: SATA max UDMA/133 abar m1024@0xf0208000 port 0xf0208280 irq 19
[   20.929092] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   20.888225] ata1.00: ATA-8: Hitachi HTS542520K9SA00, BBDOC33P, max UDMA/133
[   20.888230] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   20.889353] ata1.00: configured for UDMA/133
[   21.240476] ata2: SATA link down (SStatus 0 SControl 300)
[   21.551861] ata3: SATA link down (SStatus 0 SControl 300)
[   21.863246] ata4: SATA link down (SStatus 0 SControl 300)
[   21.863350] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54252 BBDO PQ: 0 ANSI: 5
[   21.864916] ACPI: PCI Interrupt 0000:00:12.2[B] -> GSI 17 (level, low) -> IRQ 16
[   21.864931] ehci_hcd 0000:00:12.2: EHCI Host Controller
[   21.865227] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[   21.865268] ehci_hcd 0000:00:12.2: debug port 1
[   21.865284] ehci_hcd 0000:00:12.2: irq 16, io mem 0xf0208400
[   21.831472] Driver 'sd' needs updating - please use bus_type methods
[   21.831554] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   21.831566] sd 0:0:0:0: [sda] Write Protect is off
[   21.831568] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.831584] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.831636] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   21.831644] sd 0:0:0:0: [sda] Write Protect is off
[   21.831646] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.831660] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.831663]  sda:<6>ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.875340] usb usb1: configuration #1 chosen from 1 choice
[   21.875362] hub 1-0:1.0: USB hub found
[   21.875368] hub 1-0:1.0: 6 ports detected
[   21.852579]  sda1 sda2 sda3 sda4
[   21.880786] sd 0:0:0:0: [sda] Attached SCSI disk
[   21.886298] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   21.979140] ACPI: PCI Interrupt 0000:00:13.2[B] -> GSI 19 (level, low) -> IRQ 17
[   21.979157] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   21.979180] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[   21.979219] ehci_hcd 0000:00:13.2: debug port 1
[   21.979234] ehci_hcd 0000:00:13.2: irq 17, io mem 0xf0208800
[   21.990981] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.991062] usb usb2: configuration #1 chosen from 1 choice
[   21.991082] hub 2-0:1.0: USB hub found
[   21.991087] hub 2-0:1.0: 6 ports detected

---

### Post by endo666 on 2008-08-08
[   22.053053] PCI: Enabling device 0000:09:01.0 (0015 -> 0017)
[   22.053066] ACPI: PCI Interrupt 0000:09:01.0[A] -> GSI 20 (level, low) -> IRQ 20
[   22.095281] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 21
[   22.095301] ohci_hcd 0000:00:12.0: OHCI Host Controller
[   22.095327] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[   22.095345] ohci_hcd 0000:00:12.0: irq 21, io mem 0xf0004000
[   22.103802] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[f0501000-f05017ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   22.154764] usb usb3: configuration #1 chosen from 1 choice
[   22.154787] hub 3-0:1.0: USB hub found
[   22.154795] hub 3-0:1.0: 3 ports detected
[   22.218536] usb 1-3: new high speed USB device using ehci_hcd and address 2
[   22.258563] ACPI: PCI Interrupt 0000:00:12.1[A] -> GSI 16 (level, low) -> IRQ 21
[   22.258579] ohci_hcd 0000:00:12.1: OHCI Host Controller
[   22.258603] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[   22.258618] ohci_hcd 0000:00:12.1: irq 21, io mem 0xf0005000
[   22.240898] Attempting manual resume
[   22.240902] swsusp: Resume From Partition 8:4
[   22.240904] PM: Checking swsusp image.
[   22.241084] PM: Resume from disk failed.
[   22.318450] usb usb4: configuration #1 chosen from 1 choice
[   22.318475] hub 4-0:1.0: USB hub found
[   22.318485] hub 4-0:1.0: 3 ports detected
[   22.325905] kjournald starting.  Commit interval 5 seconds
[   22.284059] EXT3-fs: mounted filesystem with ordered data mode.
[   22.323507] usb 1-3: configuration #1 chosen from 1 choice
[   22.422230] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[   22.422248] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   22.422270] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[   22.422286] ohci_hcd 0000:00:13.0: irq 17, io mem 0xf0006000
[   22.482092] usb usb5: configuration #1 chosen from 1 choice
[   22.482114] hub 5-0:1.0: USB hub found
[   22.482122] hub 5-0:1.0: 3 ports detected
[   22.585855] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[   22.585864] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   22.585881] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[   22.585892] ohci_hcd 0000:00:13.1: irq 17, io mem 0xf0007000
[   22.563923] usb 2-6: new high speed USB device using ehci_hcd and address 2
[   22.645748] usb usb6: configuration #1 chosen from 1 choice
[   22.645764] hub 6-0:1.0: USB hub found
[   22.645771] hub 6-0:1.0: 3 ports detected
[   22.699432] usb 2-6: configuration #1 chosen from 1 choice
[   22.749810] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 17 (level, low) -> IRQ 16
[   22.749864] ACPI: PCI interrupt for device 0000:00:14.1 disabled
[   23.375635] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001b2400010d675b]
[   28.995134] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   29.034463] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   29.246729] input: Power Button (FF) as /devices/virtual/input/input2
[   29.276572] ACPI: Power Button (FF) [PWRF]
[   29.276637] input: Power Button (CM) as /devices/virtual/input/input3
[   29.292541] ACPI: Power Button (CM) [PWRB]
[   29.292878] ACPI: AC Adapter [ACAD] (on-line)
[   29.293018] input: Lid Switch as /devices/virtual/input/input4
[   29.293088] ACPI: Lid Switch [LID]
[   29.678993] ACPI: Battery Slot [BAT1] (battery present)
[   29.720938] ACPI: WMI-Acer: Mapper loaded
[   29.870571] Linux agpgart interface v0.102
[   29.872781] ath_hal: module license 'Proprietary' taints kernel.
[   29.882996] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   30.010293] wlan: 0.9.4
[   30.102108] ath_pci: 0.9.4
[   30.102172] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   30.102183] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   30.126493] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   30.126513] ACPI: PCI interrupt for device 0000:06:00.0 disabled
[   30.209646] Linux video capture interface: v2.00
[   30.262339] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   30.262345] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   30.316733] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   30.337545] ACPI: EC: missing address confirmation, don't expect it any longer.
[   30.347314] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1e/LNXVIDEO:00/input/input5
[   30.356669] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[   30.359724] usbcore: registered new interface driver uvcvideo
[   30.359729] USB Video Class driver (v0.1.0)
[   30.369479] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   30.392590] ATIIXP: IDE controller (0x1002:0x439c rev 0x00) at  PCI slot 0000:00:14.1
[   30.392607] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 17 (level, low) -> IRQ 16
[   30.392617] ATIIXP: not 100% native mode: will probe irqs later
[   30.392632]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[   30.392645]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:pio, hdd:pio
[   30.392656] Probing IDE interface ide0...
[   30.512064] usbcore: registered new interface driver libusual
[   30.554596] Initializing USB Mass Storage driver...
[   30.562252] scsi4 : SCSI emulation for USB Mass Storage devices
[   30.594883] usbcore: registered new interface driver usb-storage
[   30.594890] USB Mass Storage support registered.
[   30.594895] usb-storage: device found at 2
[   30.594896] usb-storage: waiting for device to settle before scanning
[   30.700924] sdhci: Secure Digital Host Controller Interface driver
[   30.700928] sdhci: Copyright(c) Pierre Ossman
[   30.852936] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   31.463970] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1e0b1, caps: 0xd04711/0xa00000
[   31.463977] synaptics: Toshiba Satellite M305D detected, limiting rate to 40pps.
[   31.467617] hda: PIONEER DVD-RW DVRTD08L, ATAPI CD/DVD-ROM drive
[   31.467648] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   31.469038] hda: UDMA/33 mode selected
[   31.471715] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   31.484460] Probing IDE interface ide1...
[   31.507923] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   32.057161] sdhci: SDHCI controller found at 0000:09:01.2 [1217:7120] (rev 2)
[   32.057187] ACPI: PCI Interrupt 0000:09:01.2[A] -> GSI 20 (level, low) -> IRQ 20
[   32.057203] sdhci:slot0: Unknown controller version (2). You may experience problems.
[   32.057261] mmc0: SDHCI at 0xf0500800 irq 20 DMA
[   32.057304] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 17 (level, low) -> IRQ 16
[   32.310009] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2000kB Cache
[   32.310017] Uniform CD-ROM driver Revision: 3.20
[   32.913856] lp: driver loaded but no devices found
[   33.047475] Adding 5116692k swap on /dev/sda4.  Priority:-1 extents:1 across:5116692k
[   33.631302] EXT3 FS on sda3, internal journal
[   34.832331] ip_tables: (C) 2000-2006 Netfilter Core Team
[   35.351422] No dock devices found.
[   35.585676] usb-storage: device scan complete
[   35.544472] scsi 4:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  4.04 PQ: 0 ANSI: 2
[   35.545700] sd 4:0:0:0: [sdb] 4013713 512-byte hardware sectors (2055 MB)
[   35.547345] sd 4:0:0:0: [sdb] Write Protect is off
[   35.547349] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   35.547352] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   35.549941] sd 4:0:0:0: [sdb] 4013713 512-byte hardware sectors (2055 MB)
[   35.550565] sd 4:0:0:0: [sdb] Write Protect is off
[   35.550568] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   35.550570] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   35.550575]  sdb: sdb1
[   35.551519] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   35.551557] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   36.406172] apm: BIOS not found.
[   36.592587] ppdev: user-space parallel port driver
[   36.669433] audit(1218248848.870:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5063 profile="/usr/sbin/cupsd" namespace="default"
[   38.663655] Bluetooth: Core ver 2.11
[   38.663735] NET: Registered protocol family 31
[   38.663737] Bluetooth: HCI device and connection manager initialized
[   38.663741] Bluetooth: HCI socket layer initialized
[   38.738928] Bluetooth: L2CAP ver 2.9
[   38.738932] Bluetooth: L2CAP socket layer initialized
[   38.754969] Bluetooth: RFCOMM socket layer initialized
[   38.754988] Bluetooth: RFCOMM TTY layer initialized
[   38.754990] Bluetooth: RFCOMM ver 1.8
[   46.246780] hda-intel: Invalid position buffer, using LPIB read method instead.
[   52.672123] NET: Registered protocol family 10
[   52.672332] lo: Disabled Privacy Extensions
[   58.596114] CPU0 attaching NULL sched-domain.
[   58.596123] CPU1 attaching NULL sched-domain.
[   58.618516] CPU0 attaching sched-domain:
[   58.618522]  domain 0: span 03
[   58.618524]   groups: 01 02
[   58.618527] CPU1 attaching sched-domain:
[   58.618529]  domain 0: span 03
[   58.618531]   groups: 02 01

---

### Post by Taxman415a on 2008-08-08
Ok, I don't have any ideas on getting that wired ethernet working. Boo hiss on Toshiba for including hardware that doesn't have free drivers. My first step would be to email/call their support and ask for linux open source drivers for both of the network devices.

For the wireless, you have a few options. I'm a little unsure about Atheros' chipset vs chip numbering, but it seems from [http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros) that it's possible the madwifi driver supports you wireless chip. So one step would be to follow their instructions to install that. The next try would be to try the [http://wireless.kernel.org/en/users/Drivers/ath5k](http://wireless.kernel.org/en/users/Drivers/ath5k) driver and see if that works. The other would be to use ndiswrapper to use the windows driver.

Ok now I see the proprietary ath_hal: stuff and the error. That's not good.
[ 30.126493] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

---

### Post by endo666 on 2008-08-09
all of this stuff is very confusing to me.

---

### Post by Taxman415a on 2008-08-09
Yeah, sorry. Basically what's happened is Toshiba has used some really poorly supported hardware in this laptop. Your best bet may be to try ndiswrapper to get it working for not, then test later to get a free driver working. I'm not really an expert in ndiswrapper, I just know enough to get it working on one laptop, but the basic steps that you can try are.
1. Boot into windows and find what driver file runs the wireless card. Copy that inf file to Ubuntu.
2. sudo aptitude install ndiswrapper-utils-1.9  (actually to make sure you get the right version, just type most of that package name then tab to complete it.)
3. sudo ndiswrapper -i drivername.inf
4. sudo ndiswrapper -l
5. sudo ndiswrapper -m
6. sudo modprobe ndiswrapper

Not sure, but it may require unloading the proprietary driver that tried to load earlier. Before figuring that out, try the above and see what the ouput is of the above commands, then dmesg|tail, and ifconfig -a

---

### Post by endo666 on 2008-08-09
> **Taxman415a said:**
> Yeah, sorry. Basically what's happened is Toshiba has used some really poorly supported hardware in this laptop. Your best bet may be to try ndiswrapper to get it working for not, then test later to get a free driver working. I'm not really an expert in ndiswrapper, I just know enough to get it working on one laptop, but the basic steps that you can try are.
1. Boot into windows and find what driver file runs the wireless card. Copy that inf file to Ubuntu.
2. sudo aptitude install ndiswrapper-utils-1.9  (actually to make sure you get the right version, just type most of that package name then tab to complete it.)
3. sudo ndiswrapper -i drivername.inf
4. sudo ndiswrapper -l
5. sudo ndiswrapper -m
6. sudo modprobe ndiswrapper

Not sure, but it may require unloading the proprietary driver that tried to load earlier. Before figuring that out, try the above and see what the ouput is of the above commands, then dmesg|tail, and ifconfig -a

that sounds a little simpler but i also dont have a wired connection to download anything in ubuntu. so that makes things a little more challenging. lol

---

### Post by Bigtime_Scrub on 2008-08-09
> **endo666 said:**
> that sounds a little simpler but i also dont have a wired connection to download anything in ubuntu. so that makes things a little more challenging. lol

Well you could find those programs on the net (use your Windows side since you are dual booting) and download all that as a tarball and save to a flash disk or CD or even onto a repository CD you make and then install it that way.

---

### Post by endo666 on 2008-08-10
> **Bigtime_Scrub said:**
> Well you could find those programs on the net (use your Windows side since you are dual booting) and download all that as a tarball and save to a flash disk or CD or even onto a repository CD you make and then install it that way.

yes that is what i will end up doing im sure.

---

### Post by Taxman415a on 2008-08-10
You can use synaptic to get a download script that shows the locations of all the files you need. Go to File -> Generate package download script. Then save that file and open it and download the needed files from Windows.

---

### Post by endo666 on 2008-08-10
> **Taxman415a said:**
> You can use synaptic to get a download script that shows the locations of all the files you need. Go to File -> Generate package download script. Then save that file and open it and download the needed files from Windows.

thank you for all of your help.

---

### Post by thonuz on 2008-09-17
Hi,

I just saw this. Your laptop will work both wired and wireless without any configuration on Ubuntu 8.10. ATI graphics still won't work with compiz though.You can search for the daily build of Intrepid Ibex or wait for the beat release. Older versions of Ubuntu will not work without lots of configuration -- good luck!

---

### Post by shane2peru on 2008-10-10
Howdy fellow Toshiba Laptop user, and fellow Ubuntu user!  I have the same Laptop, except one number difference I have a Satellite M305D-S4830 and managed to get the wireless working.  Still no luck on the hard wired yet.  Worst problem of all is the sound issue!  It works, but I can't get the mic to work at all!  That is how I stumbled across this thread.  If you want help with wireless let me know and I can search around to find the answer.  I used madwifi and after I got it working, and updated, the updates got my wifi working without madwifi (may have been kernel update or something).  At any rate, the wireless works, still no hardwired.

Shane

---

