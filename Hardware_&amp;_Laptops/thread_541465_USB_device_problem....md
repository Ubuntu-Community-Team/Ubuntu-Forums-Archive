---
title: "USB device problem..."
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by ninhobomba on 2007-09-02
Hello.
Something odd is happening to my laptop. Its a HP Pavilion dv6420la... and i am running a fully updated Kubuntu Feisty Fawn 7.04,
When I boot up it does recognize whatever i plug via USB, but after a while they just stop working.. and sometimes they are not recognized at all...
I connected an USB pendrive and ran dmesg and this was the output i got:
I guess the important part is the last one but ill include it all just in case....
Any ideas?

```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1
.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-1
6.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009dc00 en
d: 000000000009dc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009dc00 size: 0000000000002400 en
d: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d2000 size: 000000000002e000 en
d: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000077e00000 en
d: 0000000077f00000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000077f00000 size: 0000000000016000 en
d: 0000000077f16000 type: 3
[    0.000000] copy_e820_map() start: 0000000077f16000 size: 000000000006a000 en
d: 0000000077f80000 type: 4
[    0.000000] copy_e820_map() start: 0000000077f80000 size: 0000000008080000 en
d: 0000000080000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 en
d: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 en
d: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 en
d: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 en
d: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077f00000 (usable)
[    0.000000]  BIOS-e820: 0000000077f00000 - 0000000077f16000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077f16000 - 0000000077f80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077f80000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 1023MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8910
[    0.000000] Entering add_active_range(0, 0, 491264) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   491264
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   491264
[    0.000000] On node 0 totalpages: 491264
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2046 pages used for memmap
[    0.000000]   HighMem zone: 259842 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 HP                                    ) @ 0x000f
88e0
[    0.000000] ACPI: RSDT (v001 HPQOEM SLIC-MPC 0x06040000  LTP 0x00000000) @ 0x
77f0cb68
[    0.000000] ACPI: FADT (v001 HP     MCP51M   0x06040000 PTL_ 0x000f4240) @ 0x
77f15b58
[    0.000000] ACPI: SSDT (v001 HP     POWERNOW 0x06040000  LTP 0x00000001) @ 0x
77f15bcc
[    0.000000] ACPI: MCFG (v001 HP       MCFG   0x06040000  LTP 0x00000000) @ 0x
77f15d90
[    0.000000] ACPI: HPET (v001 PTLTD  HPETTBL  0x06040000  LTP 0x00000001) @ 0x
77f15dcc
[    0.000000] ACPI: MADT (v001 HP       APIC   0x06040000  LTP 0x00000000) @ 0x
77f15e04
[    0.000000] ACPI: BOOT (v001     HP $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x
77f15e62
[    0.000000] ACPI: SLIC (v001 HPQOEM SLIC-MPC 0x06040000  LTP 0x00000001) @ 0x
77f15e8a
[    0.000000] ACPI: DSDT (v001 HP       MCP51M 0x06040000 MSFT 0x03000000) @ 0x
00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:8 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: nVIDIA   Product ID: C51-MCP51    APIC at: 0xFEE00000
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:6000
0000)
[    0.000000] Detected 1808.233 MHz processor.
[   26.176368] Built 1 zonelists.  Total pages: 487426
[   26.176372] Kernel command line: root=UUID=0c5c61d7-a289-4480-ac28-e23f3bb13e
1f ro quiet splash noapic noacpi
[   26.176519] mapped APIC to ffffd000 (fee00000)
[   26.176522] mapped IOAPIC to ffffc000 (fec00000)
[   26.176525] Enabling fast FPU save and restore... done.
[   26.176527] Enabling unmasked SIMD FPU exception support... done.
[   26.176534] Initializing CPU#0
[   26.176600] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   26.176633] spurious 8259A interrupt: IRQ7.
[   26.179751] Console: colour VGA+ 80x25
[   26.180088] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   26.180501] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   26.242239] Memory: 1937220k/1965056k available (1993k kernel code, 26684k re
served, 900k data, 328k init, 1047552k highmem)
[   26.242249] virtual kernel memory layout:
[   26.242251]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   26.242252]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   26.242253]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   26.242255]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   26.242256]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   26.242257]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[   26.242258]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[   26.242261] Checking if this processor honours the WP bit even in supervisor
mode... Ok.
[   26.242421] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   26.242426] hpet0: 3 32-bit timers, 25000000 Hz
[   26.243436] Using HPET for base-timer
[   26.322381] Calibrating delay using timer specific routine.. 3619.60 BogoMIPS
 (lpj=7239210)
[   26.322421] Security Framework v1.0.0 initialized
[   26.322428] SELinux:  Disabled at boot.
[   26.322441] Mount-cache hash table entries: 512
[   26.322566] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 000
00000 00002001 00000000 0000001f
[   26.322575] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   26.322577] CPU: L2 Cache: 512K (64 bytes/line)
[   26.322580] CPU 0(2) -> Core 0
[   26.322582] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 0
0002001 00000000 0000001f
[   26.322592] Compat vDSO mapped to ffffe000.
[   26.322596] Remapping vsyscall page to ffffe000
[   26.322605] Checking 'hlt' instruction... OK.
[   26.338500] SMP alternatives: switching to UP code
[   26.338862] Early unpacking initramfs... done
[   26.645012] ACPI: Core revision 20060707
[   26.647877] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found,
using machine DSDT.
[   26.650100] ACPI: setting ELCR to 0200 (from 0ca0)
[   26.806059] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[   26.806081] SMP alternatives: switching to SMP code
[   26.806172] Booting processor 1/1 eip 3000
[   26.817296] Initializing CPU#1
[   26.895015] Calibrating delay using timer specific routine.. 3616.51 BogoMIPS
 (lpj=7233032)
[   26.895022] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 000
00000 00002001 00000000 0000001f
[   26.895029] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   26.895031] CPU: L2 Cache: 512K (64 bytes/line)
[   26.895034] CPU 1(2) -> Core 1
[   26.895035] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 0
0002001 00000000 0000001f
[   26.894257] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[   26.894272] Total of 2 processors activated (7236.12 BogoMIPS).
[   27.002022] checking TSC synchronization across 2 CPUs:
[    0.000001] CPU#0 had -469 usecs TSC skew, fixed it up.
[    0.000003] CPU#1 had 469 usecs TSC skew, fixed it up.
[    0.003998] Brought up 2 CPUs
[    0.037387] migration_cost=302
[    0.037621] Booting paravirtualized kernel on bare hardware
[    0.037711] Time: 19:11:33  Date: 08/02/107
[    0.037740] NET: Registered protocol family 16
[    0.037817] EISA bus registered
[    0.037820] ACPI: bus type pci registered
[    0.053284] PCI: BIOS BUG #81[49435000] found
[    0.053327] PCI: Using configuration type 1
[    0.053329] Setting up standard PCI resources
[    0.058970] ACPI: Interpreter enabled
[    0.058973] ACPI: Using PIC for interrupt routing
[    0.059855] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.059860] PCI: Probing PCI hardware (bus 00)
[    0.060059] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.060379] Boot video device is 0000:00:05.0
[    0.061301] PCI: Transparent bridge - 0000:00:10.0
[    0.061329] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.099254] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.100494] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.100669] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.101022] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[    0.101341] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 *11 14 15)
[    0.101652] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 *11 14 15)
[    0.101962] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[    0.102272] ACPI: PCI Interrupt Link [LK1E] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[    0.102582] ACPI: PCI Interrupt Link [LK2E] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[    0.102893] ACPI: PCI Interrupt Link [LK3E] (IRQs 5 7 9 10 *11 14 15)
[    0.103203] ACPI: PCI Interrupt Link [LK4E] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[    0.103513] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.103823] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 *10 11 14 15)
[    0.104151] ACPI: PCI Interrupt Link [LUS0] (IRQs 5 7 9 10 *11 14 15)
[    0.104468] ACPI: PCI Interrupt Link [LUS2] (IRQs 5 *7 9 10 11 14 15)
[    0.104777] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[    0.105088] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[    0.105400] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[    0.105711] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[    0.106024] ACPI: PCI Interrupt Link [LPID] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[    0.106345] ACPI: PCI Interrupt Link [LTID] (IRQs *5 7 9 10 11 14 15)
[    0.106657] ACPI: PCI Interrupt Link [LSI1] (IRQs 5 7 9 *10 11 14 15), disabl
ed.
[    0.107636] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.107645] pnp: PnP ACPI init
[    0.110709] pnp: PnP ACPI: found 13 devices
[    0.110714] PnPBIOS: Disabled by ACPI PNP
[    0.110772] PCI: Using ACPI for IRQ routing
[    0.110776] PCI: If a device doesn't work, try "pci=routeirq".  If it helps,
post a report
[    0.110879] NET: Registered protocol family 8
[    0.110881] NET: Registered protocol family 20
[    0.111393] pnp: 00:04: ioport range 0x1000-0x107f could not be reserved
[    0.111396] pnp: 00:04: ioport range 0x1080-0x10ff has been reserved
[    0.111401] pnp: 00:04: ioport range 0x1400-0x147f has been reserved
[    0.111404] pnp: 00:04: ioport range 0x1480-0x14ff could not be reserved
[    0.111406] pnp: 00:04: ioport range 0x1800-0x187f has been reserved
[    0.111409] pnp: 00:04: ioport range 0x1880-0x18ff has been reserved
[    0.111412] pnp: 00:04: ioport range 0x2000-0x203f has been reserved
[    0.111662] PCI: Bridge: 0000:00:02.0
[    0.111665]   IO window: 4000-4fff
[    0.111669]   MEM window: b4000000-b5ffffff
[    0.111672]   PREFETCH window: d0000000-d01fffff
[    0.111674] PCI: Bridge: 0000:00:03.0
[    0.111676]   IO window: disabled.
[    0.111679]   MEM window: b6000000-b7ffffff
[    0.111681]   PREFETCH window: disabled.
[    0.111684] PCI: Bridge: 0000:00:10.0
[    0.111685]   IO window: disabled.
[    0.111689]   MEM window: b8000000-b80fffff
[    0.111692]   PREFETCH window: disabled.
[    0.111704] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    0.111711] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    0.111718] PCI: Setting latency timer of device 0000:00:10.0 to 64
[    0.111751] NET: Registered protocol family 2
[    0.159992] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.160136] TCP established hash table entries: 131072 (order: 8, 1048576 byt
es)
[    0.160995] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.161445] TCP: Hash tables configured (established 131072 bind 65536)
[    0.161448] TCP reno registered
[    0.176040] checking if image is initramfs... it is
[    0.784719] Freeing initrd memory: 6780k freed
[    0.784870] Simple Boot Flag at 0x36 set to 0x1
[    1.288000] audit: initializing netlink socket (disabled)
[    1.288000] audit(1188760294.472:1): initialized
[    1.288000] highmem bounce pool size: 64 pages
[    1.288000] VFS: Disk quotas dquot_6.5.1
[    1.288000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.288000] io scheduler noop registered
[    1.288000] io scheduler anticipatory registered
[    1.288000] io scheduler deadline registered
[    1.288000] io scheduler cfq registered (default)
[    1.308000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    1.308000] assign_interrupt_mode Found MSI capability
[    1.308000] Allocate Port Service[0000:00:02.0:pcie00]
[    1.308000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    1.308000] assign_interrupt_mode Found MSI capability
[    1.308000] Allocate Port Service[0000:00:03.0:pcie00]
[    1.308000] isapnp: Scanning for PnP cards...
[    1.660000] isapnp: No Plug & Play device found
[    1.680000] Real Time Clock Driver v1.12ac
[    1.680000] hpet_resources: 0xfed00000 is busy
[    1.680000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing
enabled
[    1.680000] mice: PS/2 mouse device common for all mice
[    1.680000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bloc
ksize
[    1.680000] input: Macintosh mouse button emulation as /class/input/input0
[    1.684000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.684000] ide: Assuming 33MHz system bus speed for PIO modes; override with
 idebus=xx
[    1.684000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq
 1,12
[    1.700000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.700000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.700000] EISA: Probing bus 0 at eisa.0
[    1.700000] Cannot allocate resource for EISA slot 1
[    1.700000] Cannot allocate resource for EISA slot 2
[    1.700000] Cannot allocate resource for EISA slot 3
[    1.700000] Cannot allocate resource for EISA slot 4
[    1.700000] EISA: Detected 0 cards.
[    1.732000] TCP cubic registered
[    1.732000] NET: Registered protocol family 1
[    1.732000] Starting balanced_irq
[    1.732000] Using IPI No-Shortcut mode
[    1.732000] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.732000] ACPI: (supports S0 S3 S4 S5)
[    1.732000]   Magic number: 7:798:191
[    1.732000]   hash matches drivers/base/power/resume.c:46
[    1.732000]   hash matches device ttys3
[    1.732000] Freeing unused kernel memory: 328k freed
[    1.736000] Time: hpet clocksource has been installed.
[    2.968000] Capability LSM initialized
[    3.012000] ACPI: Thermal Zone [THRM] (29 C)
[    3.552000] usbcore: registered new interface driver usbfs
[    3.552000] usbcore: registered new interface driver hub
[    3.552000] usbcore: registered new device driver usb
[    3.552000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Dr
iver
[    3.552000] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 11
[    3.552000] PCI: setting IRQ 11 as level-triggered
[    3.552000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 11 (lev
el, low) -> IRQ 11
[    3.552000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    3.552000] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    3.552000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus numbe
r 1
[    3.552000] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xb0004000
[    3.556000] SCSI subsystem initialized
[    3.564000] libata version 2.20 loaded.
[    3.608000] ieee1394: Initialized config rom entry `ip1394'
[    3.628000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0
.59.
[    3.628000] usb usb1: configuration #1 chosen from 1 choice
[    3.628000] hub 1-0:1.0: USB hub found
[    3.628000] hub 1-0:1.0: 8 ports detected
[    3.732000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
[    3.732000] PCI: setting IRQ 10 as level-triggered
[    3.732000] ACPI: PCI Interrupt 0000:07:05.0[A] -> Link [LNK1] -> GSI 10 (lev
el, low) -> IRQ 10
[    3.732000] sata_nv 0000:00:0e.0: version 3.3
[    3.732000] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[    3.732000] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 5
[    3.732000] PCI: setting IRQ 5 as level-triggered
[    3.732000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 5 (leve
l, low) -> IRQ 5
[    3.732000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    3.744000] ata1: SATA max UDMA/133 cmd 0x000130c0 ctl 0x000130b6 bmdma 0x000
13090 irq 5
[    3.744000] ata2: SATA max UDMA/133 cmd 0x000130b8 ctl 0x000130b2 bmdma 0x000
13098 irq 5
[    3.744000] scsi0 : sata_nv
[    3.784000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[b8000000
-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.036000] usb 1-4: new full speed USB device using ohci_hcd and address 2
[    4.212000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.220000] ata1.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC7BP, max UDMA/100
[    4.220000] ata1.00: 312581808 sectors, multi 16: LBA48
[    4.228000] ata1.00: configured for UDMA/100
[    4.228000] scsi1 : sata_nv
[    4.240000] usb 1-4: configuration #1 chosen from 1 choice
[    4.540000] ata2: SATA link down (SStatus 0 SControl 300)
[    4.548000] ATA: abnormal status 0x7F on port 0x000130bf
[    4.548000] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ
: 0 ANSI: 5
[    4.548000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 10
[    4.548000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 10 (lev
el, low) -> IRQ 10
[    4.548000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[    4.548000] forcedeth: using HIGHDMA
[    5.060000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00303c2200]
[    5.072000] eth0: forcedeth.c: subsystem: 0103c:30b7 bound to 0000:00:14.0
[    5.072000] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 7
[    5.072000] PCI: setting IRQ 7 as level-triggered
[    5.072000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 7 (leve
l, low) -> IRQ 7
[    5.072000] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[    5.072000] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    5.072000] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus numbe
r 2
[    5.072000] ehci_hcd 0000:00:0b.1: debug port 1
[    5.072000] PCI: cache line size of 64 is not supported by device 0000:00:0b.
1
[    5.072000] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xb0005000
[    5.072000] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec
2004
[    5.072000] usb 1-4: USB disconnect, address 2
[    5.072000] usb usb2: configuration #1 chosen from 1 choice
[    5.072000] hub 2-0:1.0: USB hub found
[    5.072000] hub 2-0:1.0: 8 ports detected
[    5.176000] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[    5.176000] NFORCE-MCP51: chipset revision 241
[    5.176000] NFORCE-MCP51: not 100% native mode: will probe irqs later
[    5.176000] NFORCE-MCP51: BIOS didn't set cable bits correctly. Enabling work
around.
[    5.176000] NFORCE-MCP51: 0000:00:0d.0 (rev f1) UDMA133 controller
[    5.176000]     ide0: BM-DMA at 0x3080-0x3087, BIOS settings: hda:DMA, hdb:pi
o
[    5.176000] Probing IDE interface ide0...
[    5.196000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[    5.196000] sda: Write Protect is off
[    5.196000] sda: Mode Sense: 00 3a 00 00
[    5.196000] SCSI device sda: write cache: enabled, read cache: enabled, doesn
't support DPO or FUA
[    5.196000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[    5.196000] sda: Write Protect is off
[    5.196000] sda: Mode Sense: 00 3a 00 00
[    5.196000] SCSI device sda: write cache: enabled, read cache: enabled, doesn
't support DPO or FUA
[    5.196000]  sda:<6>usb 2-4: new high speed USB device using ehci_hcd and add
ress 2
[    5.576000] usb 2-4: configuration #1 chosen from 1 choice
[    5.620000]  sda1 sda2 sda3 sda4
[    5.632000] sd 0:0:0:0: Attached scsi disk sda
[    5.636000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.912000] hda: HL-DT-ST DVDRAM GSA-T20L, ATAPI CD/DVD-ROM drive
[    5.980000] Attempting manual resume
[    5.980000] swsusp: Resume From Partition 8:3
[    5.980000] PM: Checking swsusp image.
[    5.980000] PM: Resume from disk failed.
[    6.004000] kjournald starting.  Commit interval 5 seconds
[    6.004000] EXT3-fs: mounted filesystem with ordered data mode.
[    6.248000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   14.148000] eth0: no link during initialization.
[   15.220000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   15.220000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   15.420000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.508000] nvidia: module license 'NVIDIA' taints kernel.
[   15.768000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.796000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.800000] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 11
[   15.800000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LK3E] -> GSI 11 (lev
el, low) -> IRQ 11
[   15.800000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   15.800000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov
9 17:38:10 PST 2006
[   15.860000] NET: Registered protocol family 17
[   16.044000] sdhci: Secure Digital Host Controller Interface driver
[   16.044000] sdhci: Copyright(c) Pierre Ossman
[   16.044000] sdhci: SDHCI controller found at 0000:07:05.1 [1180:0822] (rev 19
)
[   16.044000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 11
[   16.044000] ACPI: PCI Interrupt 0000:07:05.1[B] -> Link [LNK2] -> GSI 11 (lev
el, low) -> IRQ 11
[   16.044000] mmc0: SDHCI at 0xb8000800 irq 11 DMA
[   16.060000] input: PC Speaker as /class/input/input2
[   16.172000] Linux video capture interface: v2.00
[   16.260000] usbcam: registering driver r5u870 0.10.0
[   16.316000] hda: ATAPI 31X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, DMA
[   16.316000] Uniform CD-ROM driver Revision: 3.20
[   16.352000] r5u870-0: Detected HP Pavilion Webcam
[   16.512000] usbcore: registered new interface driver r5u870
[   16.556000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 9
[   16.556000] PCI: setting IRQ 9 as level-triggered
[   16.556000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 9 (leve
l, low) -> IRQ 9
[   16.556000] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   16.608000] usbcore: registered new interface driver uvcvideo
[   16.608000] USB Video Class driver (v0.1.0)
[   16.772000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa0471
3/0x200000
[   16.840000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   18.980000] fuse init (API version 7.8)
[   19.044000] lp: driver loaded but no devices found
[   19.164000] ndiswrapper version 1.47 loaded (smp=yes)
[   19.252000] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) load
ed
[   19.252000] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 10
[   19.252000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 10 (lev
el, low) -> IRQ 10
[   19.252000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   19.260000] ndiswrapper: using IRQ 10
[   19.612000] wlan0: ethernet device 00:1a:73:5d:f4:05 using NDIS driver: bcmwl
5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4
:4312.5.conf
[   19.612000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2
PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   19.616000] usbcore: registered new interface driver ndiswrapper
[   19.652000] Adding 489972k swap on /dev/disk/by-uuid/e0893a67-7c42-4d78-a2a3-
2432ff9c0ffc.  Priority:-1 extents:1 across:489972k
[   19.848000] EXT3 FS on sda2, internal journal
[   20.204000] kjournald starting.  Commit interval 5 seconds
[   20.204000] EXT3 FS on sda4, internal journal
[   20.204000] EXT3-fs: mounted filesystem with ordered data mode.
[   20.256000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   20.336000] NTFS volume version 3.1.
[   25.112000] usbcore: registered new interface driver hsfusbcd2
[   25.308000] ibm_acpi: ec object not found
[   25.376000] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   25.376000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   25.400000] input: Power Button (FF) as /class/input/input4
[   25.400000] ACPI: Power Button (FF) [PWRF]
[   25.400000] input: Power Button (CM) as /class/input/input5
[   25.400000] ACPI: Power Button (CM) [PWRB]
[   25.424000] input: Sleep Button (CM) as /class/input/input6
[   25.428000] ACPI: Sleep Button (CM) [SLPB]
[   25.436000] input: Lid Switch as /class/input/input7
[   25.440000] ACPI: Lid Switch [LID]
[   25.552000] ACPI: AC Adapter [ACAD] (off-line)
[   25.560000] No dock devices found.
[   25.580000] ACPI: Battery Slot [BAT0] (battery present)
[   25.588000] Using specific hotkey driver
[   25.724000] pcc_acpi: loading...
[   25.744000] wmi_add device=df8fbc00
[   25.744000] calling WQBA
[   25.908000] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-56
 processors (version 2.00.00)
[   25.908000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x12
[   25.908000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
[   25.908000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e
[   32.204000] ppdev: user-space parallel port driver
[   32.968000] apm: BIOS not found.
[   33.748000] NET: Registered protocol family 10
[   33.748000] lo: Disabled Privacy Extensions
[   33.748000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.748000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.172000] Bluetooth: Core ver 2.11
[   34.172000] NET: Registered protocol family 31
[   34.172000] Bluetooth: HCI device and connection manager initialized
[   34.172000] Bluetooth: HCI socket layer initialized
[   34.192000] Bluetooth: L2CAP ver 2.8
[   34.192000] Bluetooth: L2CAP socket layer initialized
[   34.240000] Bluetooth: RFCOMM socket layer initialized
[   34.240000] Bluetooth: RFCOMM TTY layer initialized
[   34.240000] Bluetooth: RFCOMM ver 1.8
[   99.276000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  118.732000] wlan0: no IPv6 routers present
[  145.224000] usb 2-1: new high speed USB device using ehci_hcd and address 3
[  145.356000] usb 2-1: configuration #1 chosen from 1 choice
[  397.884000] irq 7: nobody cared (try booting with the "irqpoll" option)
[  397.884000]  [<c0154334>] __report_bad_irq+0x24/0x80
[  397.884000]  [<c0102236>] __switch_to+0xc6/0x1f0
[  397.884000]  [<c01545ee>] note_interrupt+0x25e/0x290
[  397.884000]  [<c011bfe0>] native_write_cr0+0x0/0x10
[  397.884000]  [<f888bf32>] usb_hcd_irq+0x22/0x60 [usbcore]
[  397.884000]  [<c0153860>] handle_IRQ_event+0x30/0x60
[  397.884000]  [<c015516b>] handle_level_irq+0xeb/0x120
[  397.884000]  [<c0105b70>] do_IRQ+0x40/0x80
[  397.884000]  [<c0104233>] common_interrupt+0x23/0x30
[  397.884000]  [<c0101e00>] default_idle+0x0/0x60
[  397.884000]  [<c011c0a2>] native_safe_halt+0x2/0x10
[  397.884000]  [<c0101e3d>] default_idle+0x3d/0x60
[  397.884000]  [<c0101409>] cpu_idle+0x49/0xd0
[  397.884000]  =======================
[  397.884000] handlers:
[  397.884000] [<f888bf10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  397.884000] Disabling IRQ #7
[  759.740000] usb 2-1: USB disconnect, address 3
[  852.516000] usb 2-6: new high speed USB device using ehci_hcd and address 4
[  864.076000] usb 2-6: device not accepting address 4, error -110
[  864.188000] usb 2-6: new high speed USB device using ehci_hcd and address 5
[  875.740000] usb 2-6: device not accepting address 5, error -110
[  875.852000] usb 2-6: new high speed USB device using ehci_hcd and address 6
[  886.276000] usb 2-6: device not accepting address 6, error -110
[  886.388000] usb 2-6: new high speed USB device using ehci_hcd and address 7
[  896.816000] usb 2-6: device not accepting address 7, error -110
[  906.868000] usb 2-6: new high speed USB device using ehci_hcd and address 8
[  918.416000] usb 2-6: device not accepting address 8, error -110
[  918.528000] usb 2-6: new high speed USB device using ehci_hcd and address 9
[  930.076000] usb 2-6: device not accepting address 9, error -110
[  930.188000] usb 2-6: new high speed USB device using ehci_hcd and address 10
[  940.616000] usb 2-6: device not accepting address 10, error -110
[  940.728000] usb 2-6: new high speed USB device using ehci_hcd and address 11
[  951.152000] usb 2-6: device not accepting address 11, error -110
[  981.576000] usb 2-6: new high speed USB device using ehci_hcd and address 12
[  993.120000] usb 2-6: device not accepting address 12, error -110
[  993.232000] usb 2-6: new high speed USB device using ehci_hcd and address 13
[ 1004.784000] usb 2-6: device not accepting address 13, error -110
[ 1004.896000] usb 2-6: new high speed USB device using ehci_hcd and address 14
[ 1015.328000] usb 2-6: device not accepting address 14, error -110
[ 1015.448000] usb 2-6: new high speed USB device using ehci_hcd and address 15
[ 1025.872000] usb 2-6: device not accepting address 15, error -110
[ 1136.864000] usb 2-1: new high speed USB device using ehci_hcd and address 16
[ 1148.416000] usb 2-1: device not accepting address 16, error -110
[ 1148.528000] usb 2-1: new high speed USB device using ehci_hcd and address 17
[ 1160.080000] usb 2-1: device not accepting address 17, error -110
[ 1160.192000] usb 2-1: new high speed USB device using ehci_hcd and address 18
[ 1170.628000] usb 2-1: device not accepting address 18, error -110
[ 1170.744000] usb 2-1: new high speed USB device using ehci_hcd and address 19
[ 1181.168000] usb 2-1: device not accepting address 19, error -110
[ 1242.260000] usb 2-2: new high speed USB device using ehci_hcd and address 20
[ 1253.816000] usb 2-2: device not accepting address 20, error -110
[ 1253.932000] usb 2-2: new high speed USB device using ehci_hcd and address 21
[ 1265.492000] usb 2-2: device not accepting address 21, error -110
[ 1265.604000] usb 2-2: new high speed USB device using ehci_hcd and address 22
[ 1276.036000] usb 2-2: device not accepting address 22, error -110
[ 1276.148000] usb 2-2: new high speed USB device using ehci_hcd and address 23
[ 1286.572000] usb 2-2: device not accepting address 23, error -110
[ 1737.080000] usb 2-2: new high speed USB device using ehci_hcd and address 24
[ 1748.636000] usb 2-2: device not accepting address 24, error -110
[ 1748.752000] usb 2-2: new high speed USB device using ehci_hcd and address 25
[ 1760.304000] usb 2-2: device not accepting address 25, error -110
[ 1760.416000] usb 2-2: new high speed USB device using ehci_hcd and address 26
[ 1770.844000] usb 2-2: device not accepting address 26, error -110
[ 1770.956000] usb 2-2: new high speed USB device using ehci_hcd and address 27
[ 1781.384000] usb 2-2: device not accepting address 27, error -110
[ 1781.644000] usb 2-2: new high speed USB device using ehci_hcd and address 28
[ 1793.200000] usb 2-2: device not accepting address 28, error -110
[ 1793.320000] usb 2-2: new high speed USB device using ehci_hcd and address 29
[ 1804.876000] usb 2-2: device not accepting address 29, error -110
[ 1875.248000] usb 2-2: new high speed USB device using ehci_hcd and address 31
[ 1886.800000] usb 2-2: device not accepting address 31, error -110
[ 1886.912000] usb 2-2: new high speed USB device using ehci_hcd and address 32
[ 1898.464000] usb 2-2: device not accepting address 32, error -110
[ 1898.576000] usb 2-2: new high speed USB device using ehci_hcd and address 33
[ 1909.008000] usb 2-2: device not accepting address 33, error -110
[ 1909.128000] usb 2-2: new high speed USB device using ehci_hcd and address 34
[ 1919.556000] usb 2-2: device not accepting address 34, error -110
[ 2088.956000] set_level status: 0
[ 2089.448000] set_level status: 0
[ 2089.484000] set_level status: 0
[ 2089.516000] set_level status: 0
[ 2089.544000] set_level status: 0
[ 2089.576000] set_level status: 0
[ 2089.608000] set_level status: 0
[ 2089.640000] set_level status: 0
[ 2089.672000] set_level status: 0
[ 2089.704000] set_level status: 0
[ 2089.736000] set_level status: 0
[ 2089.768000] set_level status: 0
[ 2089.800000] set_level status: 0
[ 2089.832000] set_level status: 0
[ 2089.864000] set_level status: 0
[ 2089.896000] set_level status: 0
[ 2089.928000] set_level status: 0
[ 2089.960000] set_level status: 0
[ 2089.992000] set_level status: 0
[ 2090.020000] set_level status: 0
[ 2090.056000] set_level status: 0
[ 2090.084000] set_level status: 0
[ 2090.116000] set_level status: 0
[ 2090.148000] set_level status: 0
[ 2090.180000] set_level status: 0
[ 2090.212000] set_level status: 0
[ 2090.244000] set_level status: 0
[ 2090.276000] set_level status: 0
[ 2090.308000] set_level status: 0
[ 2090.340000] set_level status: 0
[ 2090.372000] set_level status: 0
[ 2090.404000] set_level status: 0
[ 2090.436000] set_level status: 0
[ 2090.468000] set_level status: 0
[ 2090.500000] set_level status: 0
[ 2090.532000] set_level status: 0
[ 2090.564000] set_level status: 0
[ 2090.596000] set_level status: 0
[ 2090.624000] set_level status: 0
[ 2090.660000] set_level status: 0
[ 2090.692000] set_level status: 0
[ 2090.720000] set_level status: 0
[ 2090.752000] set_level status: 0
[ 2090.784000] set_level status: 0
[ 2090.816000] set_level status: 0
[ 2090.848000] set_level status: 0
[ 2090.880000] set_level status: 0
[ 2090.912000] set_level status: 0
[ 2090.944000] set_level status: 0
[ 2090.976000] set_level status: 0
[ 2091.008000] set_level status: 0
[ 2091.040000] set_level status: 0
[ 2091.072000] set_level status: 0
[ 2091.104000] set_level status: 0
[ 2091.136000] set_level status: 0
[ 2091.168000] set_level status: 0
[ 2091.200000] set_level status: 0
[ 2091.228000] set_level status: 0
[ 2091.264000] set_level status: 0
[ 2091.296000] set_level status: 0
[ 2091.324000] set_level status: 0
[ 2091.356000] set_level status: 0
[ 2091.388000] set_level status: 0
[ 2091.420000] set_level status: 0
[ 2091.452000] set_level status: 0
[ 2091.484000] set_level status: 0
[ 2091.516000] set_level status: 0
[ 2091.552000] set_level status: 0
[ 2091.580000] set_level status: 0
[ 2091.612000] set_level status: 0
[ 2091.644000] set_level status: 0
[ 2091.676000] set_level status: 0
[ 2091.708000] set_level status: 0
[ 2091.740000] set_level status: 0
[ 2091.772000] set_level status: 0
[ 2091.804000] set_level status: 0
[ 2091.836000] set_level status: 0
[ 2091.868000] set_level status: 0
[ 2091.900000] set_level status: 0
[ 2091.928000] set_level status: 0
[ 2091.960000] set_level status: 0
[ 2091.996000] set_level status: 0
[ 2092.028000] set_level status: 0
[ 2174.516000] usb 2-2: new high speed USB device using ehci_hcd and address 35
[ 2186.064000] usb 2-2: device not accepting address 35, error -110
[ 2186.176000] usb 2-2: new high speed USB device using ehci_hcd and address 36
[ 2197.732000] usb 2-2: device not accepting address 36, error -110
[ 2197.844000] usb 2-2: new high speed USB device using ehci_hcd and address 37
[ 2208.268000] usb 2-2: device not accepting address 37, error -110
[ 2208.380000] usb 2-2: new high speed USB device using ehci_hcd and address 38
[ 2218.812000] usb 2-2: device not accepting address 38, error -110
[ 3530.228000] spurious 8259A interrupt: IRQ15.
[ 3664.904000] usb 2-1: new high speed USB device using ehci_hcd and address 39
[ 3676.452000] usb 2-1: device not accepting address 39, error -110
[ 3676.572000] usb 2-1: new high speed USB device using ehci_hcd and address 40
```

---

### Post by CRCarl on 2007-09-02
I think the first thing to try is turning acpi off as a test. Next time you reboot get into the GRUB menu. The default boot command will be highlighted, press e. add this to the end of the line ;

```
acpi=no
```

press enter, then b.

Let us know if you can use the USB port after that. 

C

---

### Post by ninhobomba on 2007-09-02
It worked for like 15 minutes.. then back again to the way it was not working.
By the way.. do i have to do the acpi=no thing everytime i boot? or is there a way i teach that to grub?...and, if it didn't work that well.. do i still need it?

Any other ideas? please?

---

### Post by CRCarl on 2007-09-03
You do not have to type it every time, but we want to make sure the change works before we update GRUB. 

Next time you reboot try this at the end of that line -
 ```
no_timer_check noacpi acpi=off noapci nolapci
```

If that works you need to edit /boot/grub/menu.lst

BE VERY CAREFUL

First - take a backup - 

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.usb.fix
```

Then open menu.lst in whatever text editor you use and find the line that starts with "default". The number after default is the default boot line. Scroll down. The bottom of the file is what makes up the menu you see when you are booting.  Each "menu line" starts with a title line. Find the line section you use to boot from by counting from zero down. (default   0 means the first section) and paste the code above to the end of the kernel line. 

Note: I have replaced "quiet splash" with "verbose" so I can watch boot messages. Up to you.

Here is what the bottom of my menu.lst would look like if I wanted to make that change to my machine (DO NOT COPY AND PASTE THIS, YOU WON'T BE ABLE TO BOOT!)

```
## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=0d740541-b986-40bc-8c0e-1eb616e91f8c ro verbose no_timer_check noacpi acpi=off noapci nolapci
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=0d740541-b986-40bc-8c0e-1eb616e91f8c ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0d740541-b986-40bc-8c0e-1eb616e91f8c ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0d740541-b986-40bc-8c0e-1eb616e91f8c ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by CRCarl on 2007-09-03
Also - I had the same problem with one of my machines, a ASUS motherboard. A BIOS update fixed the issue, so be sure to make sure that your BIOS and firmware are all up to date. 

C

---

### Post by MrHobbit on 2007-09-03
I have exactly the same problem, Same error codes etc ...
I found posts on the internet that this is a kernel bug.
See: [https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/49367]("https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/49367")
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54419]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54419")
The solutions mentioned there did not solve the problem for me.
I could bypass the problem by using a USB hub and plug my USB memory stick in the USB hub in stead of directly in a USB port of the computer. Very strange, I agree. I also have no explanation for this, but at least, it works now. Th USB hub I use must be a very cheap one because it is one I got as promotion gift from a company.

---

### Post by ninhobomba on 2007-09-03
@ CRCarl
Sorry for the noobness but i dont really know how to update my bios or firmware... could you please explain how this is done?

And about the other fix... (The no_timer_check noacpi acpi=off noapci nolapci, on GRUB) well... it changed nothing... as always the usb drives worked just after rebooting but went dead shortly afterwards.

On the other hand,
@MrHobbit:
Your mysterious solution regarding a cheap USB Hub works like a charm. Even though my usb devices are not detected on their own... adding a USB Hub, (Also cheap blue one falling apart at times) works every time. After doing this I go back to the lone USB port and bum.. it doesn't work again.... just how mysterious can this be?

And... also.. checking the links you posted back on launchpad i found the following command:
```

sudo modprobe -r ehci_hcd
```

Which makes my usb ports work without the need of a Hub (cheap or otherwise). I ran this command about 2 hours ago and I've been testing the usb ports randomly and they have all worked every time.
I really don't know for sure what that command does exactly, but it seems to work so I'm considering adding it to my Startup folder so it runs automatically every time I start my machine..
Other alternatives include learning the command by heart or carrying my cheap blue USB hub with me all the time.

Any thoughts?

---

