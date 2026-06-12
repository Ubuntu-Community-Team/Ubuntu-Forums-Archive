---
title: "[SOLVED] How do I find my Wireless Chipset?"
date: 2008-07-17
forum: Hardware
---

### Post by the lemming on 2008-07-17
I'd like to know what my Wireless Chipset is on my Laptop but I don't have a clue how to do this.

I have an Advent wireless laptop which I bought from PC World but the casing does not mention anything about the internal wireless card.

Could somebody please explain what I need to do to find out what my wireless card is and its chipset?

Cheers

---

### Post by the lemming on 2008-07-17
I've just found a website that suggested typing dmesg into a terminal.

Unfortunately I got a load of information which is way over my head and I would appreciate it if somebody could help me.


















[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4
.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24
-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004f6e0000 (usable)
[    0.000000]  BIOS-e820: 000000004f6e0000 - 000000004f6ea000 (ACPI data)
[    0.000000]  BIOS-e820: 000000004f6ea000 - 000000004f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004f700000 - 0000000050000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 374MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 325344) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   325344
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   325344
[    0.000000] On node 0 totalpages: 325344
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 749 pages used for memmap
[    0.000000]   HighMem zone: 95219 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6900 checksum 0
[    0.000000] ACPI: RSDP 000F6900, 0014 (r0 QCI___)
[    0.000000] ACPI: RSDT 4F6E2510, 0040 (r1 QCI___ EF6C____ 20041230  LTP
  0)
[    0.000000] ACPI: APIC 4F6E9E88, 0068 (r1 FUJ___ EF6_____ 20041230 LOHR
 5F)
[    0.000000] ACPI: FACP 4F6E9EF0, 0074 (r1 QCI___ EF6C____ 20041230 LOHR
 5F)
[    0.000000] ACPI: DSDT 4F6E2D93, 70F5 (r1 QCI___ EF6C____ 20041230 MSFT  1000
00E)
[    0.000000] ACPI: FACS 4F6FAFC0, 0040
[    0.000000] ACPI: BOOT 4F6E9FD8, 0028 (r1 QCI___ EF6C     20041230  LTP
  1)
[    0.000000] ACPI: MCFG 4F6E9F9C, 003C (r1 FUJ___ EF6_____ 20041230 LOHR
 5F)
[    0.000000] ACPI: SSDT 4F6E294A, 02B9 (r1  PmRef  Cpu0Ist     3000 INTL 20030
224)
[    0.000000] ACPI: SSDT 4F6E2769, 01E1 (r1  PmRef  Cpu0Cst     3001 INTL 20030
224)
[    0.000000] ACPI: SSDT 4F6E2550, 0219 (r1  PmRef    CpuPm     3000 INTL 20030
224)
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
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:9000
0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000
000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000
000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 00000
00000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pag
es: 322803
[    0.000000] Kernel command line: root=UUID=9dbd9fd7-b22d-4235-aee4-6a0abf4690
93 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1596.047 MHz processor.
[   10.559200] Console: colour VGA+ 80x25
[   10.559204] console [tty0] enabled
[   10.559649] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   10.560166] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.616177] Memory: 1277244k/1301376k available (2177k kernel code, 22848k re
served, 1006k data, 368k init, 383872k highmem)
[   10.616187] virtual kernel memory layout:
[   10.616188]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   10.616190]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   10.616191]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   10.616192]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   10.616194]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   10.616195]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   10.616196]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   10.616200] Checking if this processor honours the WP bit even in supervisor
mode... Ok.
[   10.616267] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, N
odes=1
[   10.696231] Calibrating delay using timer specific routine.. 3195.73 BogoMIPS
 (lpj=6391478)
[   10.696276] Security Framework initialized
[   10.696287] SELinux:  Disabled at boot.
[   10.696308] AppArmor: AppArmor initialized
[   10.696314] Failure registering capabilities with primary security module.
[   10.696324] Mount-cache hash table entries: 512
[   10.696507] Initializing cgroup subsys ns
[   10.696513] Initializing cgroup subsys cpuacct
[   10.696528] CPU: After generic identify, caps: afe9fbff 00100000 00000000 000
00000 00000180 00000000 00000000 00000000
[   10.696542] CPU: L1 I cache: 32K, L1 D cache: 32K
[   10.696545] CPU: L2 cache: 2048K
[   10.696549] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 0
0000180 00000000 00000000 00000000
[   10.696560] Compat vDSO mapped to ffffe000.
[   10.696578] Checking 'hlt' instruction... OK.
[   10.712668] SMP alternatives: switching to UP code
[   10.714801] Freeing SMP alternatives: 11k freed
[   10.714934] Early unpacking initramfs... done
[   11.118939] ACPI: Core revision 20070126
[   11.119027] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not
found.
[   11.146165] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 08
[   11.146191] Total of 1 processors activated (3195.73 BogoMIPS).
[   11.146384] ENABLING IO-APIC IRQs
[   11.146582] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   11.291760] Brought up 1 CPUs
[   11.291789] CPU0 attaching sched-domain:
[   11.291792]  domain 0: span 01
[   11.291794]   groups: 01
[   11.291971] net_namespace: 64 bytes
[   11.291982] Booting paravirtualized kernel on bare hardware
[   11.292475] Time:  9:07:14  Date: 07/17/08
[   11.292502] NET: Registered protocol family 16
[   11.292706] EISA bus registered
[   11.292732] ACPI: bus type pci registered
[   11.293294] PCI: PCI BIOS revision 2.10 entry at 0xfd954, last bus=6
[   11.293299] PCI: Using configuration type 1
[   11.293314] Setting up standard PCI resources
[   11.298759] ACPI: EC: Look up EC in DSDT
[   11.300549] ACPI: Interpreter enabled
[   11.300553] ACPI: (supports S0 S3 S4 S5)
[   11.300568] ACPI: Using IOAPIC for interrupt routing
[   11.300890] ACPI: EC: non-query interrupt received, switching to interrupt mo
de
[   11.307192] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   11.307195] ACPI: EC: driver started in interrupt mode
[   11.307236] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.308059] Force enabled HPET at base address 0xfed00000
[   11.308066] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   11.308070] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   11.308958] PCI: Transparent bridge - 0000:00:1e.0
[   11.309044] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.309392] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   11.316197] ACPI: PCI Interrupt Link [LNKA] (IRQs 11) *10
[   11.316294] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[   11.316388] ACPI: PCI Interrupt Link [LNKC] (IRQs *10)
[   11.316481] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[   11.316573] ACPI: PCI Interrupt Link [LNKE] (IRQs 11) *10
[   11.316666] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[   11.316764] ACPI: PCI Interrupt Link [LNKG] (IRQs 11) *0, disabled.
[   11.316858] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[   11.316980] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.317011] pnp: PnP ACPI init
[   11.317020] ACPI: bus type pnp registered
[   11.320166] pnp: PnP ACPI: found 10 devices
[   11.320168] ACPI: ACPI bus type pnp unregistered
[   11.320173] PnPBIOS: Disabled by ACPI PNP
[   11.320390] PCI: Using ACPI for IRQ routing
[   11.320392] PCI: If a device doesn't work, try "pci=routeirq".  If it helps,
post a report
[   11.320397] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   11.320399] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   11.320402] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   11.320404] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[   11.320407] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[   11.320409] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[   11.347698] NET: Registered protocol family 8
[   11.347702] NET: Registered protocol family 20
[   11.347869] hpet clockevent registered
[   11.347875] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   11.347880] hpet0: 3 64-bit timers, 14318180 Hz
[   11.348916] AppArmor: AppArmor Filesystem Enabled
[   11.351662] Time: tsc clocksource has been installed.
[   11.359692] system 00:01: iomem range 0xe0000000-0xefffffff could not be rese
rved
[   11.359695] system 00:01: iomem range 0xf0000000-0xf0003fff could not be rese
rved
[   11.359699] system 00:01: iomem range 0xf0004000-0xf0004fff could not be rese
rved
[   11.359702] system 00:01: iomem range 0xf0005000-0xf0005fff could not be rese
rved
[   11.359705] system 00:01: iomem range 0xf0008000-0xf000bfff could not be rese
rved
[   11.359709] system 00:01: iomem range 0xfed20000-0xfed8ffff could not be rese
rved
[   11.359716] system 00:05: ioport range 0x680-0x6ff has been reserved
[   11.359719] system 00:05: ioport range 0x800-0x80f has been reserved
[   11.359722] system 00:05: ioport range 0x1000-0x107f has been reserved
[   11.359725] system 00:05: ioport range 0x1180-0x11bf has been reserved
[   11.359728] system 00:05: ioport range 0x1640-0x164f has been reserved
[   11.390135] PCI: Bridge: 0000:00:1c.0
[   11.390137]   IO window: disabled.
[   11.390143]   MEM window: disabled.
[   11.390147]   PREFETCH window: disabled.
[   11.390153] PCI: Bridge: 0000:00:1c.1
[   11.390155]   IO window: disabled.
[   11.390160]   MEM window: disabled.
[   11.390165]   PREFETCH window: disabled.
[   11.390179] PCI: Bus 7, cardbus bridge: 0000:06:09.0
[   11.390181]   IO window: 00003400-000034ff
[   11.390187]   IO window: 00003800-000038ff
[   11.390192]   PREFETCH window: 64000000-67ffffff
[   11.390198]   MEM window: 68000000-6bffffff
[   11.390203] PCI: Bridge: 0000:00:1e.0
[   11.390206]   IO window: 3000-3fff
[   11.390212]   MEM window: b0100000-b01fffff
[   11.390216]   PREFETCH window: disabled.
[   11.390246] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ
 16
[   11.390255] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   11.390278] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ
 17
[   11.390285] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   11.390299] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   11.390317] ACPI: PCI Interrupt 0000:06:09.0[A] -> GSI 16 (level, low) -> IRQ
 17
[   11.390324] PCI: Setting latency timer of device 0000:06:09.0 to 64
[   11.390336] NET: Registered protocol family 2
[   11.427660] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   11.427901] TCP established hash table entries: 131072 (order: 8, 1048576 byt
es)
[   11.428777] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   11.429287] TCP: Hash tables configured (established 131072 bind 65536)
[   11.429290] TCP reno registered
[   11.439751] checking if image is initramfs... it is
[   11.851213] Switched to high resolution mode on CPU 0
[   12.229490] Freeing initrd memory: 7726k freed
[   12.229722] Simple Boot Flag at 0x35 set to 0x1
[   12.230164] audit: initializing netlink socket (disabled)
[   12.230181] audit(1216285634.488:1): initialized
[   12.230376] highmem bounce pool size: 64 pages
[   12.232428] VFS: Disk quotas dquot_6.5.1
[   12.232511] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   12.233281] io scheduler noop registered
[   12.233284] io scheduler anticipatory registered
[   12.233286] io scheduler deadline registered
[   12.233299] io scheduler cfq registered (default)
[   12.233314] Boot video device is 0000:00:02.0
[   12.233629] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   12.233685] assign_interrupt_mode Found MSI capability
[   12.233736] Allocate Port Service[0000:00:1c.0:pcie00]
[   12.233791] Allocate Port Service[0000:00:1c.0:pcie02]
[   12.233891] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   12.233946] assign_interrupt_mode Found MSI capability
[   12.233991] Allocate Port Service[0000:00:1c.1:pcie00]
[   12.234027] Allocate Port Service[0000:00:1c.1:pcie02]
[   12.234288] isapnp: Scanning for PnP cards...
[   12.588273] isapnp: No Plug & Play device found
[   12.616817] Real Time Clock Driver v1.12ac
[   12.616944] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing
enabled
[   12.617153] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[   12.617676] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ
 18
[   12.617685] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   12.618367] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bloc
ksize
[   12.618662] input: Macintosh mouse button emulation as /devices/virtual/input
/input0
[   12.618764] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq
 1,12
[   12.620722] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.620727] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.630485] mice: PS/2 mouse device common for all mice
[   12.630599] EISA: Probing bus 0 at eisa.0
[   12.630606] Cannot allocate resource for EISA slot 1
[   12.630609] Cannot allocate resource for EISA slot 2
[   12.630611] Cannot allocate resource for EISA slot 3
[   12.630632] EISA: Detected 0 cards.
[   12.630636] cpuidle: using governor ladder
[   12.630638] cpuidle: using governor menu
[   12.630737] NET: Registered protocol family 1
[   12.630764] Using IPI No-Shortcut mode
[   12.630797] registered taskstats version 1
[   12.630916]   Magic number: 0:301:121
[   12.631020] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   12.631023] EDD information not available.
[   12.631245] Freeing unused kernel memory: 368k freed
[   12.666393] input: AT Translated Set 2 keyboard as /devices/platform/i8042/se
rio0/input/input1
[   13.868130] fuse init (API version 7.9)
[   13.889048] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   13.889066] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Dev
ice is not present [20070126]
[   13.890751] ACPI: Thermal Zone [THRM] (44 C)
[   14.504694] usbcore: registered new interface driver usbfs
[   14.504720] usbcore: registered new interface driver hub
[   14.512118] usbcore: registered new device driver usb
[   14.528597] USB Universal Host Controller Interface driver v3.0
[   14.528662] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ
 19
[   14.528674] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   14.528679] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   14.529071] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus numbe
r 1
[   14.529103] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[   14.529246] usb usb1: configuration #1 chosen from 1 choice
[   14.529271] hub 1-0:1.0: USB hub found
[   14.529277] hub 1-0:1.0: 2 ports detected
[   14.632599] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ
 20
[   14.632613] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   14.632618] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   14.632642] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus numbe
r 2
[   14.632676] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[   14.632799] usb usb2: configuration #1 chosen from 1 choice
[   14.632825] hub 2-0:1.0: USB hub found
[   14.632831] hub 2-0:1.0: 2 ports detected
[   14.736491] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ
 21
[   14.736505] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   14.736510] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   14.736534] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus numbe
r 3
[   14.736567] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00001860
[   14.736684] usb usb3: configuration #1 chosen from 1 choice
[   14.736708] hub 3-0:1.0: USB hub found
[   14.736715] hub 3-0:1.0: 2 ports detected
[   14.768403] SCSI subsystem initialized
[   14.820299] libata version 3.00 loaded.
[   14.840387] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ
 17
[   14.840401] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   14.840406] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   14.840431] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus numbe
r 4
[   14.840466] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   14.840587] usb usb4: configuration #1 chosen from 1 choice
[   14.840612] hub 4-0:1.0: USB hub found
[   14.840618] hub 4-0:1.0: 2 ports detected
[   14.944419] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ
 19
[   14.944435] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   14.944440] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   14.944466] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus numbe
r 5
[   14.948381] ehci_hcd 0000:00:1d.7: debug port 1
[   14.948388] PCI: cache line size of 32 is not supported by device 0000:00:1d.
7
[   14.948395] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xb0040000
[   14.964161] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec
2004
[   14.964277] usb usb5: configuration #1 chosen from 1 choice
[   14.964303] hub 5-0:1.0: USB hub found
[   14.964310] hub 5-0:1.0: 8 ports detected
[   15.068262] r8169 Gigabit Ethernet driver 2.2LK loaded
[   15.068295] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ
 20
[   15.068551] eth0: RTL8169sb/8110sb at 0xf883a000, 00:16:36:0b:8e:fa, XID 1000
0000 IRQ 20
[   15.069200] ACPI: PCI Interrupt 0000:06:09.2[C] -> GSI 18 (level, low) -> IRQ
 21
[   15.118975] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[b0106800
-b0106fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   15.122076] ata_piix 0000:00:1f.2: version 2.12
[   15.122083] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   15.122112] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ
 20
[   15.122151] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   15.122962] scsi0 : ata_piix
[   15.123474] scsi1 : ata_piix
[   15.124485] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[   15.124489] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[   15.616064] ata2.00: ATA-7: FUJITSU MHV2080AH, 000000A0, max UDMA/100
[   15.616069] ata2.00: 156301488 sectors, multi 16: LBA
[   15.616098] ata2.01: ATAPI: PHILIPS DVD+/-RW SDVD8441, PX38, max UDMA/33
[   15.631986] ata2.00: configured for UDMA/100
[   15.803935] ata2.01: configured for UDMA/33
[   15.804085] scsi 1:0:0:0: Direct-Access     ATA      FUJITSU MHV2080A 0000 PQ
: 0 ANSI: 5
[   15.811474] scsi 1:0:1:0: CD-ROM            PHILIPS  DVD+-RW SDVD8441 PX38 PQ
: 0 ANSI: 5
[   15.832950] Driver 'sd' needs updating - please use bus_type methods
[   15.833032] sd 1:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   15.833046] sd 1:0:0:0: [sda] Write Protect is off
[   15.833049] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.833065] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[   15.833112] sd 1:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   15.833122] sd 1:0:0:0: [sda] Write Protect is off
[   15.833124] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.833140] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[   15.833144]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   15.843304] Clocksource tsc unstable (delta = -35703803261 ns)
[   15.845503]  sda1 sda2 sda3
[   15.847144] sd 1:0:0:0: [sda] Attached SCSI disk
[   15.847295] Time: hpet clocksource has been installed.
[   15.852695] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   15.852716] sr 1:0:1:0: Attached scsi generic sg1 type 5
[   15.880695] sr0: scsi3-mmc drive: 12x/24x writer cd/rw xa/form2 cdda tray
[   15.880701] Uniform CD-ROM driver Revision: 3.20
[   15.880762] sr 1:0:1:0: Attached scsi CD-ROM sr0
[   15.957633] Attempting manual resume
[   15.957637] swsusp: Resume From Partition 8:3
[   15.957639] PM: Checking swsusp image.
[   15.957791] PM: Resume from disk failed.
[   15.975286] kjournald starting.  Commit interval 5 seconds
[   15.975297] EXT3-fs: mounted filesystem with ordered data mode.
[   16.004849] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f0000810d00]
[   19.530253] Linux agpgart interface v0.102
[   19.662683] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   19.722052] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.762217] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.885853] intel_rng: FWH not detected
[   19.929855] agpgart: Detected an Intel 915GM Chipset.
[   19.930469] agpgart: Detected 7932K stolen memory.
[   19.949327] agpgart: AGP aperture is 256M @ 0xc0000000
[   20.265512] iTCO_vendor_support: vendor-support=0
[   20.335400] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   20.335499] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   20.335536] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.642350] input: Power Button (FF) as /devices/virtual/input/input3
[   20.657085] ACPI: Power Button (FF) [PWRF]
[   20.657118] ACPI Error (evxfevnt-0186): Could not enable SleepButton event [2
0070126]
[   20.657124] ACPI Warning (evxface-0145): Could not enable fixed event 3 [2007
0126]
[   20.657198] input: Lid Switch as /devices/virtual/input/input4
[   20.657560] ACPI: Lid Switch [LID]
[   20.657611] input: Sleep Button (CM) as /devices/virtual/input/input5
[   20.669059] ACPI: Sleep Button (CM) [SLPB]
[   20.742152] irda_init()
[   20.742174] NET: Registered protocol family 23
[   20.770564] ACPI: AC Adapter [ACAD] (on-line)
[   20.825462] ACPI: Battery Slot [BAT1] (battery present)
[   20.916231] Yenta: CardBus bridge found at 0000:06:09.0 [152d:0746]
[   20.916256] Yenta: Enabling burst memory read transactions
[   20.916262] Yenta: Using CSCINT to route CSC interrupts to PCI
[   20.916264] Yenta: Routing CardBus interrupts to PCI
[   20.916270] Yenta TI: socket 0000:06:09.0, mfunc 0x01ac1b22, devctl 0x64
[   20.954445] ieee80211_crypt: registered algorithm 'NULL'
[   20.980844] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   20.980849] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@li
nux.intel.com>
[   21.031603] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dm
a 1.
[   21.031633] nsc-ircc, chip->init
[   21.031646] nsc-ircc, Found chip at base=0x02e
[   21.031680] nsc-ircc, driver loaded (Dag Brattli)
[   21.031686] nsc_ircc_open(), can't get iobase of 0x2f8
[   21.031724] nsc-ircc, Found chip at base=0x02e
[   21.031759] nsc-ircc, driver loaded (Dag Brattli)
[   21.031762] nsc_ircc_open(), can't get iobase of 0x2f8
[   21.031779] nsc-ircc, chip->init
[   21.031791] nsc-ircc, Found chip at base=0x02e
[   21.031826] nsc-ircc, driver loaded (Dag Brattli)
[   21.032068] nsc-ircc 00:09: disabled
[   21.132092] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmp
rq
[   21.132098] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   21.145401] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   21.145406] Socket status: 30000006
[   21.145410] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   21.145413] cs: IO port probe 0x3000-0x3fff: clean.
[   21.145673] pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
[   21.151434] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 17 (level, low) -> IRQ
 16
[   21.151645] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   21.480268] sdhci: Secure Digital Host Controller Interface driver
[   21.480273] sdhci: Copyright(c) Pierre Ossman
[   21.762637] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa56eb1, caps: 0x8047
13/0x0
[   21.794796] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/seri
o1/input/input6
[   22.287867] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/dev
ice:01/LNXVIDEO:00/input/input7
[   22.311465] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   22.312137] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNX
VIDEO:01/input/input8
[   22.339431] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   24.372562] cs: IO port probe 0x100-0x3af: clean.
[   24.374277] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   24.375001] cs: IO port probe 0x820-0x8ff: clean.
[   24.375603] cs: IO port probe 0xc00-0xcf7: clean.
[   24.376365] cs: IO port probe 0xa00-0xaff: clean.
[   24.454122] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a
channels)
[   24.454169] ACPI: PCI Interrupt 0000:06:09.3[A] -> GSI 16 (level, low) -> IRQ
 17
[   24.454316] sdhci: SDHCI controller found at 0000:06:09.4 [104c:8034] (rev 0)
[   24.454336] ACPI: PCI Interrupt 0000:06:09.4[A] -> GSI 16 (level, low) -> IRQ
 17
[   24.454350] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim
 to support it.
[   24.454394] mmc0: SDHCI at 0xb0108400 irq 17 DMA
[   24.454405] sdhci:slot1: Will use DMA mode even though HW doesn't fully claim
 to support it.
[   24.454432] mmc1: SDHCI at 0xb0108000 irq 17 DMA
[   24.454443] sdhci:slot2: Will use DMA mode even though HW doesn't fully claim
 to support it.
[   24.454472] mmc2: SDHCI at 0xb0106400 irq 17 DMA
[   24.461302] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ
 16
[   24.461318] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   24.534794] intel8x0_measure_ac97_clock: measured 54053 usecs
[   24.534798] intel8x0: clocking to 48000
[   24.621817] lp: driver loaded but no devices found
[   24.823938] Adding 1855496k swap on /dev/sda3.  Priority:-1 extents:1 across:
1855496k
[   24.909911] EXT3 FS on sda1, internal journal
[   24.958665] device-mapper: uevent: version 1.0.3
[   24.958701] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-d
[email]evel@redhat.com[/email]
[   25.108076] kjournald starting.  Commit interval 5 seconds
[   25.108251] EXT3 FS on sda2, internal journal
[   25.108256] EXT3-fs: mounted filesystem with ordered data mode.
[   25.399962] ip_tables: (C) 2000-2006 Netfilter Core Team
[   25.615793] ACPI: ACPI Dock Station Driver
[   26.334455] apm: BIOS not found.
[   26.370098] ppdev: user-space parallel port driver
[   26.387292] audit(1216285694.272:2): type=1503 operation="inode_permission" r
equested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4979 profile="/usr/sbi
n/cupsd" namespace="default"
[   52.970227] Marking TSC unstable due to: cpufreq changes.
[   26.961786] ttyS1: LSR safety check engaged!
[   27.090851] r8169: eth0: link down
[   40.813009] Bluetooth: Core ver 2.11
[   40.813612] NET: Registered protocol family 31
[   40.813617] Bluetooth: HCI device and connection manager initialized
[   40.813622] Bluetooth: HCI socket layer initialized
[   54.463504] Bluetooth: L2CAP ver 2.9
[   54.463511] Bluetooth: L2CAP socket layer initialized
[   27.252262] Bluetooth: RFCOMM socket layer initialized
[   27.252277] Bluetooth: RFCOMM TTY layer initialized
[   27.252279] Bluetooth: RFCOMM ver 1.8
[   28.210451] [drm] Initialized drm 1.1.0 20060810
[   28.213331] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ                                             17
[   28.213338] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   28.213398] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   59.658277] NET: Registered protocol family 10
[   59.659046] lo: Disabled Privacy Extensions
[   59.660035] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   59.660691] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   87.359117] NET: Registered protocol family 17
[   87.392796] ieee80211_crypt: registered algorithm 'WEP'
[   87.553813] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   88.100838] eth1: no IPv6 routers present
frank@frank-laptop:~$

---

### Post by Berean on 2008-07-17
Hi,

If you type - in terminal - sudo lshw (entering your password) then it will list the hardware that you have on your laptop.  It should be quite clear what wireless chipset you have from the readout, after the HDD, RAM, etc.

---

### Post by Berean on 2008-07-17
Sorry,

I couldn't see the wood for the trees!  Your chipset would appear to be RTL8169sb/8110sb, which I'm pretty sure is Realtek.  You may have difficulty connecting to a wireless network with anything Realtek, I'm sorry to say, but give it a go.

---

### Post by the lemming on 2008-07-17
Thank you for taking the time to wade through all that information.

It is much appreciated

---

### Post by Berean on 2008-07-17
You're most welcom.  If this thread is solved can you indicate so on the options, please?  Regards,

---

