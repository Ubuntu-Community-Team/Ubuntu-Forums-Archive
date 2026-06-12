---
title: "Wubi 8.04 - No wireless/wired network"
date: 2008-07-27
forum: General Help
---

### Post by retrodans on 2008-07-27
I recently reformatted my entire laptop, and installed XP, and then WUBI through this.  All drivers worked in XP fine before the installation, but when I load Ubuntu I don't think the wireless or wired network are working.  I click the network manager icon, and no networks are listed for wireless, and when I plug in the network cable, the internet still doesn't work.  If anyone could help, that would be excellent.

Thankyou

---

### Post by Bison Ravi on 2008-07-27
First of all, you have to see whether the ethernet and wireless cards are up:

type in a terminal:

ifconfig

send me the output

Another thing is to see whether the drivers are loaded and the cards recognized by linux.

type in a terminal:

dmesg

lspci

send the output of these two commands also

---

### Post by retrodans on 2008-07-27
Thankyou for your help on this, I have run the 3 commands you suggested. Hope this makes sense.
Dan

--------------------------------------------------------

[SIZE="5"]**Ifconfig**[/SIZE]
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:fe:7c:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:23 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1270 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1270 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:63500 (62.0 KB)  TX bytes:63500 (62.0 KB) 


[SIZE="5"]**dmesg**[/SIZE]
[    0.000000]   Movable zone: 0 pages used for memmap 
[    0.000000] ATI board detected. Disabling timer routing over 8254. 
[    0.000000] ACPI: PM-Timer IO Port: 0x8008 
[    0.000000] ACPI: Local APIC address 0xfee00000 
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled) 
[    0.000000] Processor #0 (Bootup-CPU) 
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1]) 
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0]) 
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge) 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level) 
[    0.000000] ACPI: IRQ0 used by override. 
[    0.000000] ACPI: IRQ2 used by override. 
[    0.000000] Setting APIC routing to flat 
[    0.000000] Using ACPI (MADT) for SMP configuration information 
[    0.000000] swsusp: Registered nosave memory region: 000000000009b000 - 000000000009c000 
[    0.000000] swsusp: Registered nosave memory region: 000000000009c000 - 00000000000a0000 
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d0000 
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 0000000000100000 
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aec00000) 
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs 
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 321532 
[    0.000000] Policy zone: DMA32 
[    0.000000] Kernel command line: root=UUID=1568-13FD loop=/ubuntu/disks/root.disk ro quiet splash 
[    0.000000] Initializing CPU#0 
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes) 
[    0.000000] TSC calibrated against PM_TIMER 
[   27.572481] time.c: Detected 1600.002 MHz processor. 
[   27.573772] Console: colour VGA+ 80x25 
[   27.573776] console [tty0] enabled 
[   27.573797] Checking aperture... 
[   27.573800] CPU 0: aperture @ 84bc000000 size 32 MB 
[   27.573803] Aperture too small (32 MB) 
[   27.585924] No AGP bridge found 
[   27.608464] Memory: 1277508k/1309312k available (2489k kernel code, 31400k reserved, 1318k data, 320k init) 
[   27.608520] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1 
[   27.686294] Calibrating delay using timer specific routine.. 3203.48 BogoMIPS (lpj=6406967) 
[   27.686340] Security Framework initialized 
[   27.686352] SELinux:  Disabled at boot. 
[   27.686371] AppArmor: AppArmor initialized 
[   27.686376] Failure registering capabilities with primary security module. 
[   27.686586] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes) 
[   27.689151] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes) 
[   27.690471] Mount-cache hash table entries: 256 
[   27.690667] Initializing cgroup subsys ns 
[   27.690672] Initializing cgroup subsys cpuacct 
[   27.690690] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line) 
[   27.690692] CPU: L2 Cache: 512K (64 bytes/line) 
[   27.690695] CPU 0/0 -> Node 0 
[   27.690722] SMP alternatives: switching to UP code 
[   27.691368] Freeing SMP alternatives: 24k freed 
[   27.691920] Early unpacking initramfs... done 
[   28.121871] ACPI: Core revision 20070126 
[   28.121951] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found. 
[   28.167672] ..MP-BIOS bug: 8254 timer not connected to IO-APIC 
[   28.207711] Using local APIC timer interrupts. 
[   28.270119] APIC timer calibration result 12499996 
[   28.270121] Detected 12.499 MHz APIC timer. 
[   28.270191] Brought up 1 CPUs 
[   28.270264] CPU0 attaching sched-domain: 
[   28.270267]  domain 0: span 01 
[   28.270269]   groups: 01 
[   28.270465] net_namespace: 120 bytes 
[   28.270940] Time: 16:39:20  Date: 07/27/08 
[   28.270982] NET: Registered protocol family 16 
[   28.271188] ACPI: bus type pci registered 
[   28.271265] PCI: Using configuration type 1 
[   28.272300] ACPI: EC: Look up EC in DSDT 
[   28.275933] ACPI: Interpreter enabled 
[   28.275936] ACPI: (supports S0 S3 S4 S5) 
[   28.275950] ACPI: Using IOAPIC for interrupt routing 
[   28.278599] ACPI: EC: non-query interrupt received, switching to interrupt mode 
[   28.313556] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62 
[   28.313560] ACPI: EC: driver started in interrupt mode 
[   28.313605] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[   28.315416] PCI: Transparent bridge - 0000:00:14.4 
[   28.315498] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[   28.315665] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT] 
[   28.315787] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT] 
[   28.315910] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT] 
[   28.316035] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT] 
[   28.319537] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled. 
[   28.319658] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled. 
[   28.319776] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled. 
[   28.319894] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled. 
[   28.320011] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled. 
[   28.320129] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled. 
[   28.320247] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled. 
[   28.320365] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled. 
[   28.320495] Linux Plug and Play Support v0.97 (c) Adam Belay 
[   28.320527] pnp: PnP ACPI init 
[   28.320537] ACPI: bus type pnp registered 
[   28.328307] pnp: PnP ACPI: found 11 devices 
[   28.328310] ACPI: ACPI bus type pnp unregistered 
[   28.328561] PCI: Using ACPI for IRQ routing 
[   28.328564] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
[   28.328573] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0 
[   28.328576] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0 
[   28.328578] PCI: Cannot allocate resource region 7 of bridge 0000:00:07.0 
[   28.328580] PCI: Cannot allocate resource region 8 of bridge 0000:00:07.0 
[   28.334097] NET: Registered protocol family 8 
[   28.334099] NET: Registered protocol family 20 
[   28.334242] AppArmor: AppArmor Filesystem Enabled 
[   28.338032] Time: tsc clocksource has been installed. 
[   28.346057] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved 
[   28.346062] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved 
[   28.346066] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved 
[   28.346075] system 00:08: ioport range 0x1080-0x1080 has been reserved 
[   28.346079] system 00:08: ioport range 0x1200-0x120f has been reserved 
[   28.346083] system 00:08: ioport range 0x500-0x51f has been reserved 
[   28.346086] system 00:08: ioport range 0x40b-0x40b has been reserved 
[   28.346089] system 00:08: ioport range 0x4d0-0x4d1 has been reserved 
[   28.346093] system 00:08: ioport range 0x4d6-0x4d6 has been reserved 
[   28.346096] system 00:08: ioport range 0xc00-0xc01 has been reserved 
[   28.346100] system 00:08: ioport range 0xc14-0xc14 has been reserved 
[   28.346103] system 00:08: ioport range 0xc50-0xc52 has been reserved 
[   28.346107] system 00:08: ioport range 0xc6c-0xc6c has been reserved 
[   28.346110] system 00:08: ioport range 0xc6f-0xc6f has been reserved 
[   28.346114] system 00:08: ioport range 0xcd4-0xcd5 has been reserved 
[   28.346117] system 00:08: ioport range 0xcd6-0xcd7 has been reserved 
[   28.346121] system 00:08: ioport range 0xcd8-0xcdf has been reserved 
[   28.346124] system 00:08: ioport range 0x8000-0x805f has been reserved 
[   28.346128] system 00:08: ioport range 0xf40-0xf47 has been reserved 
[   28.346131] system 00:08: ioport range 0x87f-0x87f has been reserved 
[   28.346143] system 00:09: iomem range 0xe0000-0xfffff could not be reserved 
[   28.346147] system 00:09: iomem range 0xfff80000-0xffffffff could not be reserved 
[   28.346151] system 00:09: iomem range 0x0-0xfff could not be reserved 
[   28.346564] PCI: Bridge: 0000:00:02.0 
[   28.346567]   IO window: 9000-9fff 
[   28.346570]   MEM window: c0100000-c01fffff 
[   28.346573]   PREFETCH window: c8000000-cfffffff 
[   28.346576] PCI: Bridge: 0000:00:06.0 
[   28.346578]   IO window: disabled. 
[   28.346581]   MEM window: disabled. 
[   28.346583]   PREFETCH window: disabled. 
[   28.346586] PCI: Bridge: 0000:00:07.0 
[   28.346587]   IO window: disabled. 
[   28.346590]   MEM window: disabled. 
[   28.346592]   PREFETCH window: disabled. 
[   28.346606] PCI: Bus 7, cardbus bridge: 0000:06:06.0 
[   28.346608]   IO window: 0000a400-0000a4ff 
[   28.346614]   IO window: 0000a800-0000a8ff 
[   28.346620]   PREFETCH window: 60000000-63ffffff 
[   28.346626]   MEM window: 64000000-67ffffff 
[   28.346631] PCI: Bridge: 0000:00:14.4 
[   28.346635]   IO window: a000-afff 
[   28.346641]   MEM window: c0200000-c02fffff 
[   28.346646]   PREFETCH window: disabled. 
[   28.346665] PCI: Setting latency timer of device 0000:00:02.0 to 64 
[   28.346674] PCI: Setting latency timer of device 0000:00:06.0 to 64 
[   28.346682] PCI: Setting latency timer of device 0000:00:07.0 to 64 
[   28.346715] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 20 (level, low) -> IRQ 20 
[   28.346778] NET: Registered protocol family 2 
[   28.382105] IP route cache hash table entries: 65536 (order: 7, 524288 bytes) 
[   28.383221] TCP established hash table entries: 262144 (order: 10, 4194304 bytes) 
[   28.388448] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes) 
[   28.389729] TCP: Hash tables configured (established 262144 bind 65536) 
[   28.389733] TCP reno registered 
[   28.398137] checking if image is initramfs... it is 
[   28.849240] Switched to high resolution mode on CPU 0 
[   29.226820] Freeing initrd memory: 8458k freed 
[   29.238195] audit: initializing netlink socket (disabled) 
[   29.238211] audit(1217176761.576:1): initialized 
[   29.240391] VFS: Disk quotas dquot_6.5.1 
[   29.240475] Dquot-cache hash table entries: 512 (order 0, 4096 bytes) 
[   29.240664] io scheduler noop registered 
[   29.240666] io scheduler anticipatory registered 
[   29.240668] io scheduler deadline registered 
[   29.240784] io scheduler cfq registered (default) 
[   29.240792] PCI: MSI quirk detected. MSI deactivated. 
[   29.672102] Boot video device is 0000:01:00.0 
[   29.672292] PCI: Setting latency timer of device 0000:00:02.0 to 64 
[   29.672314] assign_interrupt_mode Found MSI capability 
[   29.672318] Allocate Port Service[0000:00:02.0:pcie00] 
[   29.672386] PCI: Setting latency timer of device 0000:00:06.0 to 64 
[   29.672408] assign_interrupt_mode Found MSI capability 
[   29.672411] Allocate Port Service[0000:00:06.0:pcie00] 
[   29.672469] PCI: Setting latency timer of device 0000:00:07.0 to 64 
[   29.672491] assign_interrupt_mode Found MSI capability 
[   29.672493] Allocate Port Service[0000:00:07.0:pcie00] 
[   29.703377] Real Time Clock Driver v1.12ac 
[   29.703485] Linux agpgart interface v0.102 
[   29.703488] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
[   29.703734] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
[   29.704149] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17 
[   29.704159] ACPI: PCI interrupt for device 0000:00:14.6 disabled 
[   29.704804] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
[   29.704875] input: Macintosh mouse button emulation as /devices/virtual/input/input0 
[   29.704969] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[   29.705316] i8042.c: Detected active multiplexing controller, rev 1.1. 
[   29.705392] serio: i8042 KBD port at 0x60,0x64 irq 1 
[   29.705397] serio: i8042 AUX0 port at 0x60,0x64 irq 12 
[   29.705400] serio: i8042 AUX1 port at 0x60,0x64 irq 12 
[   29.705402] serio: i8042 AUX2 port at 0x60,0x64 irq 12 
[   29.705404] serio: i8042 AUX3 port at 0x60,0x64 irq 12 
[   29.708147] mice: PS/2 mouse device common for all mice 
[   29.708188] cpuidle: using governor ladder 
[   29.708190] cpuidle: using governor menu 
[   29.708364] NET: Registered protocol family 1 
[   29.708483] registered taskstats version 1 
[   29.708644]   Magic number: 0:864:692 
[   29.708824] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0) 
[   29.708828] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[   29.708830] EDD information not available. 
[   29.708845] Freeing unused kernel memory: 320k freed 
[   29.711898] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1 
[   30.938373] fuse init (API version 7.9) 
[   30.961526] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3]) 
[   30.965771] Marking TSC unstable due to TSC halts in idle 
[   30.965784] Time: acpi_pm clocksource has been installed. 
[   31.005804] ACPI: Thermal Zone [TZS0] (92 C) 
[   31.058843] ACPI: Thermal Zone [TZS1] (71 C) 
[   31.110095] ACPI: Thermal Zone [TZSV] (77 C) 
[   31.772966] usbcore: registered new interface driver usbfs 
[   31.772992] usbcore: registered new interface driver hub 
[   31.781840] usbcore: registered new device driver usb 
[   31.791886] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver 
[   31.791952] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19 
[   31.792115] ohci_hcd 0000:00:13.0: OHCI Host Controller 
[   31.792414] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1 
[   31.792440] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000 
[   31.852566] usb usb1: configuration #1 chosen from 1 choice 
[   31.852596] hub 1-0:1.0: USB hub found 
[   31.852608] hub 1-0:1.0: 4 ports detected 
[   31.856597] SCSI subsystem initialized 
[   31.900814] libata version 3.00 loaded. 
[   31.956644] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19 
[   31.956857] ohci_hcd 0000:00:13.1: OHCI Host Controller 
[   31.956931] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2 
[   31.956953] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000 
[   32.016289] usb usb2: configuration #1 chosen from 1 choice 
[   32.016319] hub 2-0:1.0: USB hub found 
[   32.016331] hub 2-0:1.0: 4 ports detected 
[   32.120239] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19 
[   32.120401] ehci_hcd 0000:00:13.2: EHCI Host Controller 
[   32.120471] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3 
[   32.120533] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000 
[   32.131929] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[   32.132057] usb usb3: configuration #1 chosen from 1 choice 
[   32.132082] hub 3-0:1.0: USB hub found 
[   32.132090] hub 3-0:1.0: 8 ports detected 
[   32.236290] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 21 (level, low) -> IRQ 21 
[   32.236347] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16 
[   32.236399] PCI: Setting latency timer of device 0000:00:14.1 to 64 
[   32.239789] scsi0 : pata_atiixp 
[   32.241064] scsi1 : pata_atiixp 
[   32.242199] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14 
[   32.242202] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15 
[   32.255972] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243) 
[   32.255989] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243) 
[   32.255999] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243) 
[   32.256008] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243) 
[   32.295822] ssb: Sonics Silicon Backplane found on PCI device 0000:06:05.0 
[   32.404516] ata1.00: ATA-6: ST9100822A, 3.01, max UDMA/100 
[   32.404521] ata1.00: 195371568 sectors, multi 16: LBA48 
[   32.421156] ata1.00: configured for UDMA/100 
[   32.739591] ata2.00: ATAPI: MATSHITAUJ-845D, D100, max UDMA/33 
[   32.911279] ata2.00: configured for UDMA/33 
[   32.911417] scsi 0:0:0:0: Direct-Access     ATA      ST9100822A       3.01 PQ: 0 ANSI: 5 
[   32.913397] scsi 1:0:0:0: CD-ROM            MATSHITA UJ-845D          D100 PQ: 0 ANSI: 5 
[   32.917324] ACPI: PCI Interrupt 0000:06:06.2[C] -> GSI 22 (level, low) -> IRQ 22 
[   32.967488] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[c0208000-c02087ff]  Max Packet=[2048]  IR/IT contexts=[4/8] 
[   32.971586] r8169 Gigabit Ethernet driver 2.2LK loaded 
[   32.971629] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 23 (level, low) -> IRQ 23 
[   32.971915] eth0: RTL8169sb/8110sb at 0xffffc200008bc400, 00:0a:e4:fe:7c:e8, XID 10000000 IRQ 23 
[   32.982780] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2 
[   32.982787] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx 
[   32.999436] Driver 'sd' needs updating - please use bus_type methods 
[   32.999530] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB) 
[   32.999542] sd 0:0:0:0: [sda] Write Protect is off 
[   32.999545] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[   32.999559] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   32.999606] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB) 
[   32.999614] sd 0:0:0:0: [sda] Write Protect is off 
[   32.999617] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[   32.999629] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   32.999633]  sda:<4>Driver 'sr' needs updating - please use bus_type methods 
[   33.082874]  sda1 sda2 sda3 < sda5 > 
[   33.103400] sd 0:0:0:0: [sda] Attached SCSI disk 
[   33.110699] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[   33.110725] sr 1:0:0:0: Attached scsi generic sg1 type 5 
[   33.111533] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda caddy 
[   33.111539] Uniform CD-ROM driver Revision: 3.20 
[   33.111595] sr 1:0:0:0: Attached scsi CD-ROM sr0 
[   33.619364] loop: module loaded 
[   33.670469] kjournald starting.  Commit interval 5 seconds 
[   33.670482] EXT3-fs: mounted filesystem with ordered data mode. 
[   39.902241] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device 
[   39.955322] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   40.003283] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   40.258888] input: PC Speaker as /devices/platform/pcspkr/input/input2 
[   40.375681] input: Power Button (FF) as /devices/virtual/input/input3 
[   40.397163] ACPI: Power Button (FF) [PWRF] 
[   40.397431] input: Lid Switch as /devices/virtual/input/input4 
[   40.404085] ACPI: Lid Switch [LID0] 
[   40.404188] input: Sleep Button (CM) as /devices/virtual/input/input5 
[   40.419924] ACPI: Sleep Button (CM) [SLPB] 
[   40.614464] ACPI: WMI-Acer: Mapper loaded 
[   40.929775] Yenta: CardBus bridge found at 0000:06:06.0 [1025:0080] 
[   40.929804] Yenta: Using CSCINT to route CSC interrupts to PCI 
[   40.929806] Yenta: Routing CardBus interrupts to PCI 
[   40.929813] Yenta TI: socket 0000:06:06.0, mfunc 0x010a1b22, devctl 0x64 
[   41.162200] Yenta: ISA IRQ mask 0x0ef8, PCI irq 20 
[   41.162206] Socket status: 30000006 
[   41.162209] Yenta: Raising subordinate bus# of parent bus (#06) from #06 to #08 
[   41.162217] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff 
[   41.162220] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff 
[   41.329142] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17 
[   41.421115] sdhci: Secure Digital Host Controller Interface driver 
[   41.421120] sdhci: Copyright(c) Pierre Ossman 
[   41.845514] ACPI: PCI Interrupt 0000:06:06.3[A] -> GSI 20 (level, low) -> IRQ 20 
[   41.845674] sdhci: SDHCI controller found at 0000:06:06.4 [104c:8034] (rev 0) 
[   41.845695] ACPI: PCI Interrupt 0000:06:06.4[A] -> GSI 20 (level, low) -> IRQ 20 
[   41.845982] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it. 
[   41.846083] mmc0: SDHCI at 0xc0209000 irq 20 DMA 
[   41.846180] sdhci:slot1: Will use DMA mode even though HW doesn't fully claim to support it. 
[   41.846267] mmc1: SDHCI at 0xc0208c00 irq 20 DMA 
[   41.846359] sdhci:slot2: Will use DMA mode even though HW doesn't fully claim to support it. 
[   41.846441] mmc2: SDHCI at 0xc0208800 irq 20 DMA 
[   42.067344] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17 
[   42.175707] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2160: MC'97 1 converters and GPIO not ready (0xff00) 
[   42.284109] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:10/LNXVIDEO:00/input/input6 
[   42.299473] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no) 
[   42.300014] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/LNXVIDEO:01/input/input7 
[   42.315426] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no) 
[   43.101383] acer_acpi: Acer Laptop ACPI Extras version 0.11.1 
[   43.101394] acer_acpi: Detected Acer AMW0 version 2 interface 
[   43.255949] irda_init() 
[   43.255977] NET: Registered protocol family 23 
[   43.396441] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000 
[   43.426731] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8 
[   43.459645] ACPI: Battery Slot [BAT0] (battery present) 
[   43.468251] b43-phy0: Broadcom 4318 WLAN found 
[   43.491874] Registered led device: acer_acpi:mail 
[   43.491929] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3. 
[   43.491966] nsc-ircc, chip->init 
[   43.491981] nsc-ircc, Found chip at base=0x02e 
[   43.492023] nsc-ircc, driver loaded (Dag Brattli) 
[   43.492029] nsc_ircc_open(), can't get iobase of 0x2f8 
[   43.492077] nsc-ircc, Found chip at base=0x02e 
[   43.492119] nsc-ircc, driver loaded (Dag Brattli) 
[   43.492121] nsc_ircc_open(), can't get iobase of 0x2f8 
[   43.492377] nsc-ircc 00:0a: disabled 
[   43.509514] b43-phy0 debug: Found PHY: Analog 3, Type 2, Revision 7 
[   43.509529] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 8 
[   43.535738] phy0: Selected rate control algorithm 'simple' 
[   43.551575] ACPI: AC Adapter [ADP1] (on-line) 
[   45.523514] lp: driver loaded but no devices found 
[   46.338799] EXT3 FS on loop0, internal journal 
[   47.121084] kjournald starting.  Commit interval 5 seconds 
[   47.121109] EXT3 FS on loop1, internal journal 
[   47.121113] EXT3-fs: mounted filesystem with ordered data mode. 
[   47.121465] kjournald starting.  Commit interval 5 seconds 
[   47.121488] EXT3 FS on loop2, internal journal 
[   47.121491] EXT3-fs: mounted filesystem with ordered data mode. 
[   48.505394] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k 
[   51.590660] ip_tables: (C) 2000-2006 Netfilter Core Team 
[   52.115497] ACPI: ACPI Dock Station Driver 
[   52.504938] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-28 processors (1 cpu cores) (version 2.20.00) 
[   52.504977] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x4 
[   52.504979] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16 
[   53.614691] ppdev: user-space parallel port driver 
[   53.773243] audit(1217173186.386:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4952 profile="/usr/sbin/cupsd" namespace="default" 
[   54.736504] ttyS1: LSR safety check engaged! 
[   55.609080] r8169: eth0: link down 
[   55.682088] input: b43-phy0 as /devices/virtual/input/input9 
[   55.777650] Bluetooth: Core ver 2.11 
[   55.785815] NET: Registered protocol family 31 
[   55.785820] Bluetooth: HCI device and connection manager initialized 
[   55.785825] Bluetooth: HCI socket layer initialized 
[   55.829978] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed. 
[   55.829984] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4). 
[   55.837555] Bluetooth: L2CAP ver 2.9 
[   55.837559] Bluetooth: L2CAP socket layer initialized 
[   55.912935] Bluetooth: RFCOMM socket layer initialized 
[   55.913123] Bluetooth: RFCOMM TTY layer initialized 
[   55.913127] Bluetooth: RFCOMM ver 1.8 
[   56.047189] Clocksource tsc unstable (delta = -250002810 ns) 
[   57.429644] [drm] Initialized drm 1.1.0 20060810 
[   57.451036] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 18 
[   57.451047] PCI: Setting latency timer of device 0000:01:00.0 to 64 
[   57.451143] [drm] Initialized radeon 1.28.0 20060524 on minor 0 
[   57.860535] input: b43-phy0 as /devices/virtual/input/input10 
[   57.893500] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed. 
[   57.893507] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4). 
[   60.155418] [drm] Setting GART location based on new memory map 
[   60.155734] [drm] Loading R300 Microcode 
[   60.155753] [drm] writeback test succeeded in 1 usecs 
[   66.424720] input: b43-phy0 as /devices/virtual/input/input11 
[   66.458384] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed. 
[   66.458391] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4). 
[   72.093932] NET: Registered protocol family 10 
[   72.094353] lo: Disabled Privacy Extensions 
[   72.094909] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   75.557415] input: b43-phy0 as /devices/virtual/input/input12 
[   75.622071] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed. 
[   75.622080] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4). 
[   80.904393] ISO 9660 Extensions: Microsoft Joliet Level 1 
[   80.928620] ISOFS: changing to secondary root 
[   86.058603] input: b43-phy0 as /devices/virtual/input/input13 
[   86.090945] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed. 
[   86.090952] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4). 
[   94.616934] input: b43-phy0 as /devices/virtual/input/input14 
[   94.647170] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed. 
[   94.647177] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4). 
[  109.994748] input: b43-phy0 as /devices/virtual/input/input15 
[  110.026151] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed. 
[  110.026158] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4). 
[  120.000828] input: b43-phy0 as /devices/virtual/input/input16 
[  120.068289] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed. 
[  120.068297] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4). 
[  128.992395] input: b43-phy0 as /devices/virtual/input/input17 
[  129.022431] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed. 
[  129.022437] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4). 


[SIZE="5"]**lspci**[/SIZE]
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01) 
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port 
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller 
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller 
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller 
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11) 
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller 
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge 
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge 
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02) 
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE) 
06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller 
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller 
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller 
06:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller 
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

---

### Post by Bison Ravi on 2008-07-27
Okay, for the wireless, it looks like there is a couple of problems

Let us try the wired network first. type in:

sudo dhclient eth0

The command simply asks the router for an IP address. It is supposed to be that simple in 99.9% of the cases.

---

### Post by Bison Ravi on 2008-07-27
As for the wireless, the dmesg command says to visit:

[http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

So try to do what they say.

---

### Post by Bison Ravi on 2008-07-27
I found a thread that might be of interest for the wired network configuration:

[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

### Post by retrodans on 2008-07-27
Thankyou for all your help, I went through all the instructions, and now have a wired network working in Ubuntu (which is a great start).  Sadly, the wireless is not yet working.  So I reran dmesg as before, and the output is different so have attached it to this reply.

-----------------------------------------------------------

[SIZE="5"]DMESG[/SIZE]

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] Command line: root=UUID=1568-13FD loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b800 (usable)
[    0.000000]  BIOS-e820: 000000000009b800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004fea0000 (usable)
[    0.000000]  BIOS-e820: 000000004fea0000 - 000000004feae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000004feae000 - 000000004ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004ff00000 - 0000000050000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 155) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 327328) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6DA0 checksum 0
[    0.000000] ACPI: RSDP 000F6DA0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 4FEA81E3, 0034 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 4FEADE41, 0074 (r1 ATI    Piranha   6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 4FEA8217, 5C2A (r1    ATI    SB400  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 4FEAEFC0, 0040
[    0.000000] ACPI: SSDT 4FEADEB5, 00B5 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: APIC 4FEADF6A, 005A (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG 4FEADFC4, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: DMI detected: Acer
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 1 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000004fea0000
[    0.000000] Entering add_active_range(0, 0, 155) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 327328) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000004fea0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      155
[    0.000000]     0:      256 ->   327328
[    0.000000] On node 0 totalpages: 327227
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1220 pages reserved
[    0.000000]   DMA zone: 2719 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 4419 pages used for memmap
[    0.000000]   DMA32 zone: 318813 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009b000 - 000000000009c000
[    0.000000] swsusp: Registered nosave memory region: 000000000009c000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aec00000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 321532
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=1568-13FD loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[   26.969302] time.c: Detected 1600.002 MHz processor.
[   26.970595] Console: colour VGA+ 80x25
[   26.970600] console [tty0] enabled
[   26.970621] Checking aperture...
[   26.970624] CPU 0: aperture @ 84bc000000 size 32 MB
[   26.970626] Aperture too small (32 MB)
[   26.982746] No AGP bridge found
[   27.005283] Memory: 1277508k/1309312k available (2489k kernel code, 31400k reserved, 1318k data, 320k init)
[   27.005339] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   27.083113] Calibrating delay using timer specific routine.. 3203.52 BogoMIPS (lpj=6407054)
[   27.083160] Security Framework initialized
[   27.083172] SELinux:  Disabled at boot.
[   27.083191] AppArmor: AppArmor initialized
[   27.083197] Failure registering capabilities with primary security module.
[   27.083407] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   27.085971] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   27.087291] Mount-cache hash table entries: 256
[   27.087486] Initializing cgroup subsys ns
[   27.087491] Initializing cgroup subsys cpuacct
[   27.087509] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   27.087512] CPU: L2 Cache: 512K (64 bytes/line)
[   27.087515] CPU 0/0 -> Node 0
[   27.087542] SMP alternatives: switching to UP code
[   27.088188] Freeing SMP alternatives: 24k freed
[   27.088739] Early unpacking initramfs... done
[   27.518678] ACPI: Core revision 20070126
[   27.518758] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   27.564479] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   27.604518] Using local APIC timer interrupts.
[   27.666926] APIC timer calibration result 12499999
[   27.666928] Detected 12.499 MHz APIC timer.
[   27.666998] Brought up 1 CPUs
[   27.667071] CPU0 attaching sched-domain:
[   27.667074]  domain 0: span 01
[   27.667075]   groups: 01
[   27.667271] net_namespace: 120 bytes
[   27.667746] Time: 19:22:39  Date: 07/27/08
[   27.667788] NET: Registered protocol family 16
[   27.667994] ACPI: bus type pci registered
[   27.668071] PCI: Using configuration type 1
[   27.669103] ACPI: EC: Look up EC in DSDT
[   27.671717] ACPI: Interpreter enabled
[   27.671720] ACPI: (supports S0 S3 S4 S5)
[   27.671734] ACPI: Using IOAPIC for interrupt routing
[   27.674686] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   27.709751] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[   27.709755] ACPI: EC: driver started in interrupt mode
[   27.709800] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   27.711605] PCI: Transparent bridge - 0000:00:14.4
[   27.711688] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   27.711856] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   27.711978] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[   27.712100] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[   27.712225] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   27.715736] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   27.715857] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   27.715976] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   27.716094] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   27.716211] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   27.716329] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   27.716447] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   27.716565] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   27.716696] Linux Plug and Play Support v0.97 (c) Adam Belay
[   27.716729] pnp: PnP ACPI init
[   27.716739] ACPI: bus type pnp registered
[   27.724565] pnp: PnP ACPI: found 11 devices
[   27.724569] ACPI: ACPI bus type pnp unregistered
[   27.724820] PCI: Using ACPI for IRQ routing
[   27.724823] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   27.724832] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
[   27.724834] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
[   27.724837] PCI: Cannot allocate resource region 7 of bridge 0000:00:07.0
[   27.724839] PCI: Cannot allocate resource region 8 of bridge 0000:00:07.0
[   27.726939] NET: Registered protocol family 8
[   27.726941] NET: Registered protocol family 20
[   27.727082] AppArmor: AppArmor Filesystem Enabled
[   27.730845] Time: tsc clocksource has been installed.
[   27.738870] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[   27.738875] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   27.738879] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   27.738889] system 00:08: ioport range 0x1080-0x1080 has been reserved
[   27.738892] system 00:08: ioport range 0x1200-0x120f has been reserved
[   27.738896] system 00:08: ioport range 0x500-0x51f has been reserved
[   27.738899] system 00:08: ioport range 0x40b-0x40b has been reserved
[   27.738903] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   27.738906] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   27.738909] system 00:08: ioport range 0xc00-0xc01 has been reserved
[   27.738913] system 00:08: ioport range 0xc14-0xc14 has been reserved
[   27.738916] system 00:08: ioport range 0xc50-0xc52 has been reserved
[   27.738920] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[   27.738923] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[   27.738927] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[   27.738930] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[   27.738934] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[   27.738937] system 00:08: ioport range 0x8000-0x805f has been reserved
[   27.738941] system 00:08: ioport range 0xf40-0xf47 has been reserved
[   27.738944] system 00:08: ioport range 0x87f-0x87f has been reserved
[   27.738956] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   27.738960] system 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   27.738964] system 00:09: iomem range 0x0-0xfff could not be reserved
[   27.739381] PCI: Bridge: 0000:00:02.0
[   27.739384]   IO window: 9000-9fff
[   27.739388]   MEM window: c0100000-c01fffff
[   27.739391]   PREFETCH window: c8000000-cfffffff
[   27.739394] PCI: Bridge: 0000:00:06.0
[   27.739395]   IO window: disabled.
[   27.739398]   MEM window: disabled.
[   27.739400]   PREFETCH window: disabled.
[   27.739403] PCI: Bridge: 0000:00:07.0
[   27.739405]   IO window: disabled.
[   27.739407]   MEM window: disabled.
[   27.739410]   PREFETCH window: disabled.
[   27.739423] PCI: Bus 7, cardbus bridge: 0000:06:06.0
[   27.739425]   IO window: 0000a400-0000a4ff
[   27.739431]   IO window: 0000a800-0000a8ff
[   27.739437]   PREFETCH window: 60000000-63ffffff
[   27.739442]   MEM window: 64000000-67ffffff
[   27.739448] PCI: Bridge: 0000:00:14.4
[   27.739452]   IO window: a000-afff
[   27.739458]   MEM window: c0200000-c02fffff
[   27.739463]   PREFETCH window: disabled.
[   27.739483] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   27.739491] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   27.739499] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   27.739532] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 20 (level, low) -> IRQ 20
[   27.739595] NET: Registered protocol family 2
[   27.774910] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   27.776025] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   27.781260] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   27.782542] TCP: Hash tables configured (established 262144 bind 65536)
[   27.782546] TCP reno registered
[   27.790948] checking if image is initramfs... it is
[   28.242054] Switched to high resolution mode on CPU 0
[   28.618915] Freeing initrd memory: 8458k freed
[   28.630289] audit: initializing netlink socket (disabled)
[   28.630305] audit(1217186559.572:1): initialized
[   28.632580] VFS: Disk quotas dquot_6.5.1
[   28.632664] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   28.632829] io scheduler noop registered
[   28.632831] io scheduler anticipatory registered
[   28.632833] io scheduler deadline registered
[   28.632952] io scheduler cfq registered (default)
[   28.632959] PCI: MSI quirk detected. MSI deactivated.
[   29.064917] Boot video device is 0000:01:00.0
[   29.065107] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   29.065130] assign_interrupt_mode Found MSI capability
[   29.065134] Allocate Port Service[0000:00:02.0:pcie00]
[   29.065199] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   29.065221] assign_interrupt_mode Found MSI capability
[   29.065224] Allocate Port Service[0000:00:06.0:pcie00]
[   29.065283] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   29.065304] assign_interrupt_mode Found MSI capability
[   29.065307] Allocate Port Service[0000:00:07.0:pcie00]
[   29.096261] Real Time Clock Driver v1.12ac
[   29.096365] Linux agpgart interface v0.102
[   29.096368] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   29.096610] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   29.097015] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   29.097025] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   29.097665] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   29.097737] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   29.097832] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   29.098181] i8042.c: Detected active multiplexing controller, rev 1.1.
[   29.098257] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.098261] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   29.098264] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   29.098266] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   29.098268] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   29.104808] mice: PS/2 mouse device common for all mice
[   29.104848] cpuidle: using governor ladder
[   29.104851] cpuidle: using governor menu
[   29.105025] NET: Registered protocol family 1
[   29.105142] registered taskstats version 1
[   29.105301]   Magic number: 0:873:395
[   29.105466]   hash matches device 0000:00:07.0
[   29.105486] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   29.105495] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   29.105497] EDD information not available.
[   29.105506] Freeing unused kernel memory: 320k freed
[   29.108570] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   30.333255] fuse init (API version 7.9)
[   30.356435] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   30.359993] Marking TSC unstable due to TSC halts in idle
[   30.363434] Time: acpi_pm clocksource has been installed.
[   30.399352] ACPI: Thermal Zone [TZS0] (85 C)
[   30.448609] ACPI: Thermal Zone [TZS1] (71 C)
[   30.497252] ACPI: Thermal Zone [TZSV] (69 C)
[   31.168349] usbcore: registered new interface driver usbfs
[   31.168377] usbcore: registered new interface driver hub
[   31.175927] usbcore: registered new device driver usb
[   31.189308] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   31.189378] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   31.189546] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   31.189839] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   31.189865] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[   31.237411] SCSI subsystem initialized
[   31.249362] usb usb1: configuration #1 chosen from 1 choice
[   31.249389] hub 1-0:1.0: USB hub found
[   31.249401] hub 1-0:1.0: 4 ports detected
[   31.321069] libata version 3.00 loaded.
[   31.353171] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   31.353350] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   31.353419] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   31.353441] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[   31.413087] usb usb2: configuration #1 chosen from 1 choice
[   31.413117] hub 2-0:1.0: USB hub found
[   31.413130] hub 2-0:1.0: 4 ports detected
[   31.517045] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   31.517201] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   31.517271] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   31.517334] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[   31.528724] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.528859] usb usb3: configuration #1 chosen from 1 choice
[   31.528888] hub 3-0:1.0: USB hub found
[   31.528896] hub 3-0:1.0: 8 ports detected
[   31.632854] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 21 (level, low) -> IRQ 21
[   31.632910] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   31.632970] PCI: Setting latency timer of device 0000:00:14.1 to 64
[   31.634593] scsi0 : pata_atiixp
[   31.635560] scsi1 : pata_atiixp
[   31.636739] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[   31.636743] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[   31.652749] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[   31.652766] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[   31.652776] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[   31.652785] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[   31.692584] ssb: Sonics Silicon Backplane found on PCI device 0000:06:05.0
[   31.801731] ata1.00: ATA-6: ST9100822A, 3.01, max UDMA/100
[   31.801737] ata1.00: 195371568 sectors, multi 16: LBA48 
[   31.818360] ata1.00: configured for UDMA/100
[   32.136382] ata2.00: ATAPI: MATSHITAUJ-845D, D100, max UDMA/33
[   32.308090] ata2.00: configured for UDMA/33
[   32.308228] scsi 0:0:0:0: Direct-Access     ATA      ST9100822A       3.01 PQ: 0 ANSI: 5
[   32.310291] scsi 1:0:0:0: CD-ROM            MATSHITA UJ-845D          D100 PQ: 0 ANSI: 5
[   32.312750] r8169 Gigabit Ethernet driver 2.2LK loaded
[   32.312789] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 23 (level, low) -> IRQ 23
[   32.313049] eth0: RTL8169sb/8110sb at 0xffffc200008b6400, 00:0a:e4:fe:7c:e8, XID 10000000 IRQ 23
[   32.313616] ACPI: PCI Interrupt 0000:06:06.2[C] -> GSI 22 (level, low) -> IRQ 22
[   32.363771] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[c0208000-c02087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   32.378993] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   32.379001] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   32.394467] Driver 'sd' needs updating - please use bus_type methods
[   32.394566] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   32.394578] sd 0:0:0:0: [sda] Write Protect is off
[   32.394581] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.394595] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.394641] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   32.394649] sd 0:0:0:0: [sda] Write Protect is off
[   32.394651] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.394664] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.394669]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   32.480074]  sda1 sda2 sda3 < sda5 >
[   32.500589] sd 0:0:0:0: [sda] Attached SCSI disk
[   32.510384] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   32.510406] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   32.513954] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda caddy
[   32.513962] Uniform CD-ROM driver Revision: 3.20
[   32.514022] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   32.939024] loop: module loaded
[   32.990126] kjournald starting.  Commit interval 5 seconds
[   32.990143] EXT3-fs: mounted filesystem with ordered data mode.
[   39.807380] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.843357] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.960157] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   40.031090] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   40.374603] input: Power Button (FF) as /devices/virtual/input/input3
[   40.390411] ACPI: Power Button (FF) [PWRF]
[   40.390554] input: Lid Switch as /devices/virtual/input/input4
[   40.396580] ACPI: Lid Switch [LID0]
[   40.396694] input: Sleep Button (CM) as /devices/virtual/input/input5
[   40.410353] ACPI: Sleep Button (CM) [SLPB]
[   40.463826] ACPI: WMI-Acer: Mapper loaded
[   40.590252] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   40.701902] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2160: MC'97 1 converters and GPIO not ready (0xff00)
[   40.869705] Yenta: CardBus bridge found at 0000:06:06.0 [1025:0080]
[   40.869736] Yenta: Using CSCINT to route CSC interrupts to PCI
[   40.869739] Yenta: Routing CardBus interrupts to PCI
[   40.869745] Yenta TI: socket 0000:06:06.0, mfunc 0x010a1b22, devctl 0x64
[   41.093298] sdhci: Secure Digital Host Controller Interface driver
[   41.093303] sdhci: Copyright(c) Pierre Ossman
[   41.102134] Yenta: ISA IRQ mask 0x0ef8, PCI irq 20
[   41.102139] Socket status: 30000006
[   41.102142] Yenta: Raising subordinate bus# of parent bus (#06) from #06 to #08
[   41.102148] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   41.102152] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   41.157496] ACPI: PCI Interrupt 0000:06:06.3[A] -> GSI 20 (level, low) -> IRQ 20
[   41.157575] sdhci: SDHCI controller found at 0000:06:06.4 [104c:8034] (rev 0)
[   41.157595] ACPI: PCI Interrupt 0000:06:06.4[A] -> GSI 20 (level, low) -> IRQ 20
[   41.157734] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   41.157835] mmc0: SDHCI at 0xc0209000 irq 20 DMA
[   41.157929] sdhci:slot1: Will use DMA mode even though HW doesn't fully claim to support it.
[   41.158015] mmc1: SDHCI at 0xc0208c00 irq 20 DMA
[   41.158105] sdhci:slot2: Will use DMA mode even though HW doesn't fully claim to support it.
[   41.158188] mmc2: SDHCI at 0xc0208800 irq 20 DMA
[   41.369684] acer_acpi: Acer Laptop ACPI Extras version 0.11.1
[   41.369694] acer_acpi: Detected Acer AMW0 version 2 interface
[   41.370861] Registered led device: acer_acpi:mail
[   41.456691] irda_init()
[   41.456716] NET: Registered protocol family 23
[   41.538278] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   41.538317] nsc-ircc, chip->init
[   41.538332] nsc-ircc, Found chip at base=0x02e
[   41.538375] nsc-ircc, driver loaded (Dag Brattli)
[   41.538380] nsc_ircc_open(), can't get iobase of 0x2f8
[   41.538429] nsc-ircc, Found chip at base=0x02e
[   41.538471] nsc-ircc, driver loaded (Dag Brattli)
[   41.538473] nsc_ircc_open(), can't get iobase of 0x2f8
[   41.538728] nsc-ircc 00:0a: disabled
[   42.044104] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   42.321565] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:10/LNXVIDEO:00/input/input6
[   42.331457] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   42.332047] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/LNXVIDEO:01/input/input7
[   42.343435] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   42.580102] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   42.854419] [fglrx] Maximum main memory to use for locked dma buffers: 1163 MBytes.
[   42.854458] [fglrx] ASYNCIO init succeed!
[   42.854602] [fglrx] PAT is enabled successfully!
[   42.857821] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   43.052074] ACPI: AC Adapter [ADP1] (on-line)
[   43.301198] b43-phy0: Broadcom 4318 WLAN found
[   43.307914] ACPI: Battery Slot [BAT0] (battery present)
[   43.341618] b43-phy0 debug: Found PHY: Analog 3, Type 2, Revision 7
[   43.341643] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 8
[   43.378200] phy0: Selected rate control algorithm 'simple'
[   43.549657] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[   43.579768] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   46.239535] lp: driver loaded but no devices found
[   47.043451] EXT3 FS on loop0, internal journal
[   47.825761] kjournald starting.  Commit interval 5 seconds
[   47.825788] EXT3 FS on loop1, internal journal
[   47.825792] EXT3-fs: mounted filesystem with ordered data mode.
[   47.826142] kjournald starting.  Commit interval 5 seconds
[   47.826161] EXT3 FS on loop2, internal journal
[   47.826164] EXT3-fs: mounted filesystem with ordered data mode.
[   49.290533] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k
[   52.328538] ip_tables: (C) 2000-2006 Netfilter Core Team
[   52.976777] ACPI: ACPI Dock Station Driver 
[   53.375812] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-28 processors (1 cpu cores) (version 2.20.00)
[   53.375851] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x4
[   53.375853] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16
[   54.651469] ppdev: user-space parallel port driver
[   54.809360] audit(1217182986.702:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4976 profile="/usr/sbin/cupsd" namespace="default"
[   55.441992] Clocksource tsc unstable (delta = -249995752 ns)
[   55.646005] ttyS1: LSR safety check engaged!
[   55.855261] r8169: eth0: link down
[   55.917390] input: b43-phy0 as /devices/virtual/input/input9
[   55.999197] Bluetooth: Core ver 2.11
[   56.003140] NET: Registered protocol family 31
[   56.003143] Bluetooth: HCI device and connection manager initialized
[   56.003147] Bluetooth: HCI socket layer initialized
[   56.068995] Bluetooth: L2CAP ver 2.9
[   56.068999] Bluetooth: L2CAP socket layer initialized
[   56.136644] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   56.181775] Bluetooth: RFCOMM socket layer initialized
[   56.181791] Bluetooth: RFCOMM TTY layer initialized
[   56.181794] Bluetooth: RFCOMM ver 1.8
[   57.378748] b43-phy0 debug: Chip initialized
[   57.379289] b43-phy0 debug: 32-bit DMA initialized
[   57.399098] Registered led device: b43-phy0:tx
[   57.399391] Registered led device: b43-phy0:rx
[   57.399546] Registered led device: b43-phy0:radio
[   57.399590] b43-phy0 debug: Wireless interface started
[   57.444792] b43-phy0: Radio hardware status changed to DISABLED
[   57.446061] b43-phy0 debug: Adding Interface type 2
[   57.742941] r8169: eth0: link up
[   58.131639] b43-phy0: Radio turned on by software
[   58.131646] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[   59.374480] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   59.697097] NET: Registered protocol family 17
[   60.314127] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
[   60.314134] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X40000
[   60.314137] [fglrx] Reserve Block - 2 offset =  0X7fbb000 length = 0X40000
[   60.381290] [fglrx] interrupt source 20008000 successfully enabled
[   60.381296] [fglrx] enable ID = 0x00000004
[   60.381573] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   60.381787] [fglrx] interrupt source 10000000 successfully enabled
[   60.381790] [fglrx] enable ID = 0x00000005
[   60.382026] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   61.802948] NET: Registered protocol family 10
[   61.803370] lo: Disabled Privacy Extensions
[   61.804393] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   67.740418] eth0: no IPv6 routers present
[  128.146560] r8169: eth0: link down
[  147.447593] r8169: eth0: link up
[  147.448970] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  156.272739] eth0: no IPv6 routers present

---

### Post by AndyM3 on 2008-07-28
Did you try running ```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
``` as said in the linuxwireless.org link?

---

### Post by retrodans on 2008-07-28
Yes, I ran that script, all that I get back from it is the general process saying it is successful.  But when I click the network icon at the bottom, it still doesn't list any wireless networks.  So believe it still has the same issue.
[SIZE="5"]
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh[/SIZE]

--20:36:15--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652,866 (638K) [application/x-object]

100%[====================================>] 652,866      594.50K/s             

20:36:16 (592.92 KB/s) - `wl_apsta-3.130.20.0.o' saved [652866/652866]

--20:36:17--  [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
           => `broadcom-wl-4.80.53.0.tar.bz2'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 904,072 (883K) [application/x-tar]

100%[====================================>] 904,072      646.55K/s             

20:36:18 (644.19 KB/s) - `broadcom-wl-4.80.53.0.tar.bz2' saved [904072/904072]

This file is recognised as:
  ID         :  FW10
  filename   :  wl_apsta.o
  version    :  295.14
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3
Extracting b43legacy/ucode2.fw
Extracting b43legacy/ucode4.fw
Extracting b43legacy/ucode5.fw
Extracting b43legacy/ucode11.fw
Extracting b43legacy/pcm4.fw
Extracting b43legacy/pcm5.fw
Extracting b43legacy/a0g0bsinitvals2.fw
Extracting b43legacy/b0g0bsinitvals5.fw
Extracting b43legacy/a0g0initvals5.fw
Extracting b43legacy/a0g1bsinitvals5.fw
Extracting b43legacy/a0g0initvals2.fw
Extracting b43legacy/a0g1initvals5.fw
Extracting b43legacy/b0g0bsinitvals2.fw
Extracting b43legacy/b0g0initvals5.fw
Extracting b43legacy/b0g0initvals2.fw
Extracting b43legacy/a0g0bsinitvals5.fw
broadcom-wl-4.80.53.0/
broadcom-wl-4.80.53.0/kmod/
broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
broadcom-wl-4.80.53.0/kmod/wl_apsta.o
broadcom-wl-4.80.53.0/nas
broadcom-wl-4.80.53.0/wl
broadcom-wl-4.80.53.0/WHERE_FROM
broadcom-wl-4.80.53.0/libbcmcrypto.so
This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta_mimo.o
  version    :  351.126
  MD5        :  722e2e0d8cc04b8f118bb5afe6829ff9
Extracting b43/ucode4.fw
Extracting b43/ucode5.fw
Extracting b43/ucode11.fw
Extracting b43/ucode13.fw
Extracting b43/pcm4.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0initvals4.fw
Extracting b43/b0g0bsinitvals4.fw
Extracting b43/a0g0initvals4.fw
Extracting b43/a0g0bsinitvals4.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/lp0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/a0g1bsinitvals13.fw

---

### Post by minhmeoke on 2008-07-29
The driver seems to be installed correctly, is there a physical switch on your laptop that turns on the wireless? It seems to be off.

> 
[ 57.399590] b43-phy0 debug: Wireless interface started
[ 57.444792] b43-phy0: Radio hardware status changed to DISABLED
[ 57.446061] b43-phy0 debug: Adding Interface type 2
[ 57.742941] r8169: eth0: link up
[ 58.131639] b43-phy0: Radio turned on by software
[ 58.131646] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.


---

### Post by retrodans on 2008-07-29
I am writing to you via my wireless network.  The button didn't work, but your help set me down the right train of thought and I found the below url

[http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi&page=4](http://ubuntuforums.org/showthread.php?t=224349&highlight=acer_acpi&page=4)

Which told me to type in:
sudo chmod 777 /proc/acpi/acer/wireless
sudo echo 1 > /proc/acpi/acer/wireless

I don't suppose you know what the latter line does do you. In php echo prints onto the page, is this similar?

Thankyou again for all your help.
Dan

---

### Post by AndyM3 on 2008-08-01
I think that ```
sudo chmod 777 /proc/acpi/acer/wireless
```gave you write permissions and ```
sudo echo 1 > /proc/acpi/acer/wireless
```printed "1" to the file, the OS retained that and activated the module.

---

### Post by haydemon on 2008-08-01
> **AndyM3 said:**
> I think that ```
sudo chmod 777 /proc/acpi/acer/wireless
```gave you write permissions and ```
sudo echo 1 > /proc/acpi/acer/wireless
```printed "1" to the file, the OS retained that and activated the module.
Quick question: does this work with wicd, or just Network Manager? I've disabled the latter in favor of the former, but still not much luck getting wireless to work.:confused:

---

