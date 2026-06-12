---
title: "shutdown hangs in feisty on HP laptop"
date: 2007-09-06
forum: Hardware &amp; Laptops
---

### Post by igeterrors on 2007-09-06
A couple of days ago, I began noticing that on shutdown of my HP dv1411se laptop,  the system hangs on what seems to be the scripts in the rc6.d directory.  Another symptom I've noticed is that Apache no longer starts by itself on bootup as it used to do.  Now  I have to manually start it.  Who knows what else may be wrong.  I've probably messed things up trying to fix this (e.g. I uninstalled Samba and Cupsys as these were where the shut down would hang, but now it just hangs earlier.  Plus who knows, maybe I'll want to print something someday...)  Meanwhile the only way I can shut down is by pressing and holding the power button, and that cannot be a good thing.

As far as I know, I have changed nothing configuration-wise to cause this to happen, although it seems there was a Feisty kernel "upgrade" that I was forced to download and install a couple of days ago and that seems to be when the trouble started.

Any help??  Thanks.

---

### Post by reckless2k2 on 2007-09-06
"forced" is such a nasty word. hahaha. do us a favor and run dmesg from the terminal to give us an idea of some error messages.

---

### Post by igeterrors on 2007-09-06
> **reckless2k2 said:**
> "forced" is such a nasty word. hahaha. 
I know... : )   but really, it's not like I had a choice, right?  I suppose I could just ignore the little icon saying "software upgrades!" forever...

Anyway, there's quite a lot of output from dmesg, but I assume you know that and you asked for it anyway : )  I hope there's nothing embarrassing in here, but here goes:
```
[    0.000000] Linux version 2.6.20-16-386 (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 Fri Aug 31 00:51:58 UTC 2007 (Ubuntu 2.6.20-16.31-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003f5e0000 end: 000000003f6e0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003f6e0000 size: 000000000000b000 end: 000000003f6eb000 type: 3
[    0.000000] copy_e820_map() start: 000000003f6eb000 size: 0000000000015000 end: 000000003f700000 type: 4
[    0.000000] copy_e820_map() start: 000000003f700000 size: 0000000000900000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010006000 end: 00000000f0006000 type: 2
[    0.000000] copy_e820_map() start: 00000000f0008000 size: 0000000000004000 end: 00000000f000c000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed00000 size: 0000000000000400 end: 00000000fed00400 type: 2
[    0.000000] copy_e820_map() start: 00000000fed20000 size: 0000000000070000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff000000 size: 0000000001000000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6e0000 (usable)
[    0.000000]  BIOS-e820: 000000003f6e0000 - 000000003f6eb000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f6eb000 - 000000003f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 259808) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259808
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259808
[    0.000000] On node 0 totalpages: 259808
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 237 pages used for memmap
[    0.000000]   HighMem zone: 30195 pages, LIFO batch:7
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 HP                                    ) @ 0x000f7b10
[    0.000000] ACPI: RSDT (v001 HP     308F     0x20040323  LTP 0x00000000) @ 0x3f6e5589
[    0.000000] ACPI: MADT (v001 HP     308F     0x20040323 LOHR 0x0000005f) @ 0x3f6eae88
[    0.000000] ACPI: FADT (v001 HP     308F     0x20040323 PTL  0x0000005f) @ 0x3f6eaef0
[    0.000000] ACPI: HPET (v001 HP     308F     0x20040323 LOHR 0x0000005f) @ 0x3f6eaf64
[    0.000000] ACPI: MCFG (v001 HP     308F     0x20040323 LOHR 0x0000005f) @ 0x3f6eaf9c
[    0.000000] ACPI: BOOT (v001 HP     308F     0x20040323  LTP 0x00000001) @ 0x3f6eafd8
[    0.000000] ACPI: SSDT (v001 HP     308F     0x00003001 INTL 0x20030224) @ 0x3f6e57b7
[    0.000000] ACPI: SSDT (v001 HP     308F     0x00003000 INTL 0x20030224) @ 0x3f6e55c9
[    0.000000] ACPI: DSDT (v001 HP     308F     0x20040323 MSFT 0x0100000e) @ 0x00000000
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
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0x0
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Detected 1496.455 MHz processor.
[   17.735936] Built 1 zonelists.  Total pages: 257779
[   17.735939] Kernel command line: root=UUID=cd5065a9-a9f6-4a96-a738-e5db11597923 ro quiet splash
[   17.736122] mapped APIC to ffffd000 (fee00000)
[   17.736125] mapped IOAPIC to ffffc000 (fec00000)
[   17.736129] Enabling fast FPU save and restore... done.
[   17.736132] Enabling unmasked SIMD FPU exception support... done.
[   17.736140] Initializing CPU#0
[   17.736199] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   17.738030] Console: colour VGA+ 80x25
[   17.738468] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   17.739019] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.772414] Memory: 1018032k/1039232k available (1917k kernel code, 20504k reserved, 867k data, 328k init, 121728k highmem)
[   17.772427] virtual kernel memory layout:
[   17.772428]     fixmap  : 0xfffa9000 - 0xfffff000   ( 344 kB)
[   17.772430]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.772431]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   17.772433]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   17.772434]       .init : 0xc03bc000 - 0xc040e000   ( 328 kB)
[   17.772436]       .data : 0xc02df4e3 - 0xc03b8434   ( 867 kB)
[   17.772437]       .text : 0xc0100000 - 0xc02df4e3   (1917 kB)
[   17.772441] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.852158] Calibrating delay using timer specific routine.. 2995.39 BogoMIPS (lpj=5990789)
[   17.852198] Security Framework v1.0.0 initialized
[   17.852207] SELinux:  Disabled at boot.
[   17.852219] Mount-cache hash table entries: 512
[   17.852357] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[   17.852371] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.852374] CPU: L2 cache: 1024K
[   17.852377] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000000 00000000 00000000
[   17.852388] Compat vDSO mapped to ffffe000.
[   17.852397] Remapping vsyscall page to ffffe000
[   17.852408] CPU: Intel(R) Celeron(R) M processor         1.50GHz stepping 08
[   17.852416] Checking 'hlt' instruction... OK.
[   17.868681] Early unpacking initramfs... done
[   18.303123] ACPI: Core revision 20060707
[   18.303514] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   18.337216] ENABLING IO-APIC IRQs
[   18.337410] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.484122] Booting paravirtualized kernel on bare hardware
[   18.484187] Time: 18:52:43  Date: 08/06/107
[   18.484215] NET: Registered protocol family 16
[   18.484301] EISA bus registered
[   18.484305] ACPI: bus type pci registered
[   18.484728] PCI: PCI BIOS revision 2.10 entry at 0xfd96e, last bus=6
[   18.484730] PCI: Using configuration type 1
[   18.484732] Setting up standard PCI resources
[   18.493059] ACPI: Interpreter enabled
[   18.493062] ACPI: Using IOAPIC for interrupt routing
[   18.493737] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.493744] PCI: Probing PCI hardware (bus 00)
[   18.494572] Boot video device is 0000:00:02.0
[   18.495103] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   18.495107] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   18.495652] PCI: Transparent bridge - 0000:00:1e.0
[   18.495716] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#06) (try 'pci=assign-busses')
[   18.495719] Please report the result to linux-kernel to fix this permanently
[   18.495740] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.502251] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   18.502913] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[   18.503185] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[   18.503452] ACPI: PCI Interrupt Link [LNKC] (IRQs *4)
[   18.503726] ACPI: PCI Interrupt Link [LNKD] (IRQs *3)
[   18.504024] ACPI: PCI Interrupt Link [LNKE] (IRQs *11)
[   18.504288] ACPI: PCI Interrupt Link [LNKF] (IRQs 3) *0, disabled.
[   18.504565] ACPI: PCI Interrupt Link [LNKG] (IRQs *4)
[   18.504832] ACPI: PCI Interrupt Link [LNKH] (IRQs *3)
[   18.505888] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.505899] pnp: PnP ACPI init
[   18.508900] pnp: PnP ACPI: found 10 devices
[   18.508904] PnPBIOS: Disabled by ACPI PNP
[   18.508948] PCI: Using ACPI for IRQ routing
[   18.508951] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.524222] NET: Registered protocol family 8
[   18.524224] NET: Registered protocol family 20
[   18.524586] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   18.524602] PCI: Bus 7, cardbus bridge: 0000:06:09.0
[   18.524605]   IO window: 00003400-000034ff
[   18.524610]   IO window: 00003800-000038ff
[   18.524615]   PREFETCH window: 50000000-53ffffff
[   18.524620]   MEM window: 58000000-5bffffff
[   18.524625] PCI: Bridge: 0000:00:1e.0
[   18.524628]   IO window: 3000-3fff
[   18.524634]   MEM window: b0100000-b01fffff
[   18.524639]   PREFETCH window: 50000000-53ffffff
[   18.524656] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   18.524676] ACPI: PCI Interrupt 0000:06:09.0[A] -> GSI 20 (level, low) -> IRQ 16
[   18.524703] NET: Registered protocol family 2
[   18.563928] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.564052] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[   18.564613] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   18.564936] TCP: Hash tables configured (established 131072 bind 65536)
[   18.564940] TCP reno registered
[   18.576043] checking if image is initramfs... it is
[   19.430864] Freeing initrd memory: 8056k freed
[   19.431110] Simple Boot Flag at 0x36 set to 0x1
[   19.431354] audit: initializing netlink socket (disabled)
[   19.431372] audit(1189104764.744:1): initialized
[   19.431442] highmem bounce pool size: 64 pages
[   19.431515] VFS: Disk quotas dquot_6.5.1
[   19.431552] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.431615] io scheduler noop registered
[   19.431620] io scheduler anticipatory registered
[   19.431623] io scheduler deadline registered
[   19.431632] io scheduler cfq registered (default)
[   19.431975] isapnp: Scanning for PnP cards...
[   19.785673] isapnp: No Plug & Play device found
[   19.818046] hpet_acpi_add: no address or irqs in _CRS
[   19.818065] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.818953] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 16
[   19.818962] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   19.819035] mice: PS/2 mouse device common for all mice
[   19.819624] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.819882] input: Macintosh mouse button emulation as /class/input/input0
[   19.819915] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   19.819921] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   19.820128] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PSM1] at 0x60,0x64 irq 1,12
[   19.822949] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.822955] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.823093] EISA: Probing bus 0 at eisa.0
[   19.823101] Cannot allocate resource for EISA slot 1
[   19.823105] Cannot allocate resource for EISA slot 2
[   19.823107] Cannot allocate resource for EISA slot 3
[   19.823127] EISA: Detected 0 cards.
[   19.853221] TCP cubic registered
[   19.853230] NET: Registered protocol family 1
[   19.853250] Using IPI Shortcut mode
[   19.853315] ACPI: (supports S0 S3 S4 S5)
[   19.853364]   Magic number: 7:716:897
[   19.853470]   hash matches device ptyy7
[   19.853486]   hash matches device ptyva
[   19.853738] Freeing unused kernel memory: 328k freed
[   19.855360] Time: tsc clocksource has been installed.
[   19.868560] input: AT Translated Set 2 keyboard as /class/input/input1
[   21.086092] Capability LSM initialized
[   21.102426] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[   21.131528] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   21.131535] ACPI: Processor [CPU0] (supports 8 throttling states)
[   21.133944] ACPI: Thermal Zone [THRM] (73 C)
[   21.218505] md: linear personality registered for level -1
[   21.222393] md: multipath personality registered for level -4
[   21.225994] md: raid0 personality registered for level 0
[   21.230095] md: raid1 personality registered for level 1
[   21.233558] raid5: automatically using best checksumming function: pIII_sse
[   21.250797]    pIII_sse  :  3891.000 MB/sec
[   21.250799] raid5: using function: pIII_sse (3891.000 MB/sec)
[   21.322800] raid6: int32x1    500 MB/s
[   21.390807] raid6: int32x2    589 MB/s
[   21.458784] raid6: int32x4    487 MB/s
[   21.526825] raid6: int32x8    411 MB/s
[   21.594691] raid6: mmxx1     1501 MB/s
[   21.662643] raid6: mmxx2     1720 MB/s
[   21.730614] raid6: sse1x1    1098 MB/s
[   21.798603] raid6: sse1x2    1800 MB/s
[   21.866576] raid6: sse2x1    1967 MB/s
[   21.934539] raid6: sse2x2    2199 MB/s
[   21.934541] raid6: using algorithm sse2x2 (2199 MB/s)
[   21.934545] md: raid6 personality registered for level 6
[   21.934547] md: raid5 personality registered for level 5
[   21.934550] md: raid4 personality registered for level 4
[   21.973755] md: raid10 personality registered for level 10
[   22.278515] usbcore: registered new interface driver usbfs
[   22.278537] usbcore: registered new interface driver hub
[   22.278562] usbcore: registered new device driver usb
[   22.279448] USB Universal Host Controller Interface driver v3.0
[   22.279503] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 17
[   22.279515] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   22.279520] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   22.279674] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   22.279704] uhci_hcd 0000:00:1d.0: irq 17, io base 0x00001820
[   22.279810] usb usb1: configuration #1 chosen from 1 choice
[   22.279838] hub 1-0:1.0: USB hub found
[   22.279844] hub 1-0:1.0: 2 ports detected
[   22.382499] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   22.382513] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   22.382518] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   22.382540] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   22.382571] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00001840
[   22.382670] usb usb2: configuration #1 chosen from 1 choice
[   22.382695] hub 2-0:1.0: USB hub found
[   22.382702] hub 2-0:1.0: 2 ports detected
[   22.385162] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   22.416619] ieee1394: Initialized config rom entry `ip1394'
[   22.486486] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   22.486501] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   22.486506] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.486528] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   22.486560] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00001860
[   22.486656] usb usb3: configuration #1 chosen from 1 choice
[   22.486681] hub 3-0:1.0: USB hub found
[   22.486687] hub 3-0:1.0: 2 ports detected
[   22.590450] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 20
[   22.590464] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   22.590469] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   22.590496] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   22.590527] uhci_hcd 0000:00:1d.3: irq 20, io base 0x00001880
[   22.590631] usb usb4: configuration #1 chosen from 1 choice
[   22.590657] hub 4-0:1.0: USB hub found
[   22.590665] hub 4-0:1.0: 2 ports detected
[    4.736000] Time: acpi_pm clocksource has been installed.
[    4.832000] SCSI subsystem initialized
[    4.840000] libata version 2.20 loaded.
[    4.844000] ata_piix 0000:00:1f.1: version 2.10ac1
[    4.844000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[    4.844000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.844000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.844000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    4.844000] scsi0 : ata_piix
[    5.228000] ata1.00: ATA-6: ST9808210A, 3.02, max UDMA/100
[    5.228000] ata1.00: 156301488 sectors, multi 16: LBA48 
[    5.228000] ata1.01: ATAPI, max MWDMA2
[    5.236000] ata1.00: configured for UDMA/100
[    5.416000] ata1.01: configured for MWDMA2
[    5.416000] scsi1 : ata_piix
[    5.416000] ata2: port disabled. ignoring.
[    5.416000] scsi 0:0:0:0: Direct-Access     ATA      ST9808210A       3.02 PQ: 0 ANSI: 5
[    5.416000] scsi 0:0:1:0: CD-ROM            TSSTcorp CD/DVDW TS-L532M HR04 PQ: 0 ANSI: 5
[    5.416000] 8139cp 0000:06:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    5.416000] 8139cp 0000:06:00.0: Try the "8139too" driver instead.
[    5.420000] 8139too Fast Ethernet driver 0.9.28
[    5.420000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[    5.420000] eth0: RealTek RTL8139 at 0xf8840000, 00:c0:9f:c8:e9:ff, IRQ 20
[    5.420000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    5.420000] ACPI: PCI Interrupt 0000:06:09.2[C] -> GSI 22 (level, low) -> IRQ 21
[    5.468000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[b0108800-b0108fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.484000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 17
[    5.484000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    5.484000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.484000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    5.488000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    5.488000] ehci_hcd 0000:00:1d.7: debug port 1
[    5.488000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    5.488000] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xb0040000
[    5.492000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.492000] sda: Write Protect is off
[    5.492000] sda: Mode Sense: 00 3a 00 00
[    5.492000] usb usb5: configuration #1 chosen from 1 choice
[    5.492000] hub 5-0:1.0: USB hub found
[    5.492000] hub 5-0:1.0: 8 ports detected
[    5.492000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.492000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    5.492000] sda: Write Protect is off
[    5.492000] sda: Mode Sense: 00 3a 00 00
[    5.492000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.492000]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 >
[    5.592000] sd 0:0:0:0: Attached scsi disk sda
[    5.596000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.596000] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    5.600000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    5.600000] Uniform CD-ROM driver Revision: 3.20
[    5.600000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    6.160000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.160000] EXT3-fs: write access will be enabled during recovery.
[    6.740000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f00006fd73b]
[    9.948000] kjournald starting.  Commit interval 5 seconds
[    9.948000] EXT3-fs: sda8: orphan cleanup on readonly fs
[    9.948000] ext3_orphan_cleanup: deleting unreferenced inode 732971
[    9.948000] ext3_orphan_cleanup: deleting unreferenced inode 732970
[    9.948000] ext3_orphan_cleanup: deleting unreferenced inode 732969
[    9.948000] ext3_orphan_cleanup: deleting unreferenced inode 732968
[    9.948000] ext3_orphan_cleanup: deleting unreferenced inode 732967
[    9.948000] EXT3-fs: sda8: 5 orphan inodes deleted
[    9.948000] EXT3-fs: recovery complete.
[    9.996000] EXT3-fs: mounted filesystem with ordered data mode.
[   18.192000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.204000] agpgart: Detected an Intel 915GM Chipset.
[   18.204000] agpgart: Detected 7932K stolen memory.
[   18.224000] agpgart: AGP aperture is 256M @ 0xc0000000
[   18.520000] iTCO_vendor_support: vendor-support=0
[   18.568000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   18.568000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   18.568000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.600000] ACPI: PCI Interrupt 0000:06:09.3[A] -> GSI 20 (level, low) -> IRQ 16
[   19.048000] intel_rng: FWH not detected
[   19.080000] Yenta: CardBus bridge found at 0000:06:09.0 [103c:3080]
[   19.080000] Yenta: Enabling burst memory read transactions
[   19.080000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   19.080000] Yenta: Routing CardBus interrupts to PCI
[   19.080000] Yenta TI: socket 0000:06:09.0, mfunc 0x01a01b22, devctl 0x64
[   19.216000] sdhci: Secure Digital Host Controller Interface driver
[   19.216000] sdhci: Copyright(c) Pierre Ossman
[   19.260000] Real Time Clock Driver v1.12ac
[   19.312000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   19.312000] Socket status: 30000006
[   19.312000] Yenta: Raising subordinate bus# of parent bus (#06) from #06 to #0a
[   19.312000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   19.312000] cs: IO port probe 0x3000-0x3fff: clean.
[   19.312000] pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
[   19.312000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   19.312000] sdhci: SDHCI controller found at 0000:06:09.4 [104c:8034] (rev 0)
[   19.312000] ACPI: PCI Interrupt 0000:06:09.4[A] -> GSI 20 (level, low) -> IRQ 16
[   19.312000] mmc0: SDHCI at 0xb0109400 irq 16 DMA
[   19.316000] mmc1: SDHCI at 0xb0109000 irq 16 DMA
[   19.316000] mmc2: SDHCI at 0xb0108400 irq 16 DMA
[   19.796000] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[   19.828000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   20.136000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 22
[   20.136000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   20.212000] cs: IO port probe 0x100-0x3af: clean.
[   20.216000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   20.216000] cs: IO port probe 0x820-0x8ff: clean.
[   20.216000] cs: IO port probe 0xc00-0xcf7: clean.
[   20.216000] cs: IO port probe 0xa00-0xaff: clean.
[   20.448000] intel8x0_measure_ac97_clock: measured 54092 usecs
[   20.448000] intel8x0: clocking to 48000
[   20.620000] lp: driver loaded but no devices found
[   20.748000] ndiswrapper version 1.38 loaded (preempt=no,smp=no)
[   20.844000] ndiswrapper: driver bcmwl5a (Broadcom,12/22/2004, 3.100.46.0) loaded
[   20.844000] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 18 (level, low) -> IRQ 19
[   20.852000] ndiswrapper: using IRQ 19
[   21.536000] wlan0: ethernet device 00:14:a5:1b:05:58 using NDIS driver: bcmwl5a, version: 0x3642e00, NDIS version: 0x501, vendor: '', 14E4:4318.5.conf
[   21.536000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   21.536000] usbcore: registered new interface driver ndiswrapper
[   21.628000] Adding 1253052k swap on /dev/disk/by-uuid/6133a92c-5a0b-4005-84ae-7a423cadda5c.  Priority:-1 extents:1 across:1253052k
[   21.644000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   21.828000] EXT3 FS on sda8, internal journal
[   39.636000] kjournald starting.  Commit interval 5 seconds
[   39.636000] EXT3 FS on dm-4, internal journal
[   39.636000] EXT3-fs: mounted filesystem with ordered data mode.
[   39.704000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   39.808000] NTFS volume version 3.1.
[   39.828000] kjournald starting.  Commit interval 5 seconds
[   39.828000] EXT3 FS on dm-1, internal journal
[   39.828000] EXT3-fs: mounted filesystem with ordered data mode.
[   39.852000] kjournald starting.  Commit interval 5 seconds
[   39.852000] EXT3 FS on dm-5, internal journal
[   39.852000] EXT3-fs: mounted filesystem with ordered data mode.
[   40.048000] Adding 1253052k swap on /dev/disk/by-uuid/6133a92c-5a0b-4005-84ae-7a423cadda5c.  Priority:-2 extents:1 across:1253052k
[   49.216000] ACPI: AC Adapter [ACAD] (on-line)
[   49.316000] ACPI: Battery Slot [BAT0] (battery present)
[   49.380000] input: Power Button (FF) as /class/input/input3
[   49.384000] ACPI: Power Button (FF) [PWRF]
[   49.432000] input: Power Button (CM) as /class/input/input4
[   49.432000] ACPI: Power Button (CM) [PRWB]
[   49.480000] input: Sleep Button (CM) as /class/input/input5
[   49.484000] ACPI: Sleep Button (CM) [SLPB]
[   49.528000] input: Lid Switch as /class/input/input6
[   49.532000] ACPI: Lid Switch [LID]
[   49.552000] Using specific hotkey driver
[   49.592000] No dock devices found.
[   49.668000] ibm_acpi: ec object not found
[   49.764000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   49.808000] pcc_acpi: loading...
[   49.820000] wmi_add device=c1a69800
[   49.820000] calling WQBA
[   66.732000] eth0: link down
[   68.232000] [drm] Initialized drm 1.1.0 20060810
[   68.288000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 20
[   68.288000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   73.872000] apm: BIOS not found.
[   84.284000] NET: Registered protocol family 10
[   84.284000] lo: Disabled Privacy Extensions
[   84.284000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   87.300000] ISO 9660 Extensions: Microsoft Joliet Level 1
[   87.508000] ISO 9660 Extensions: IEEE_P1282
[   94.896000] eth1: no IPv6 routers present

```

---

### Post by igeterrors on 2007-09-06
Another thing I forgot to mention but that might be relevant is that once upon booting up I saw a little dialog box pop up in the GDM telling me that HAL failed to initialize.  Something like that, anyway.  I thought they deactivated HAL.  I guess he came back.

---

### Post by reckless2k2 on 2007-09-06
hey i can't help you. i'm going to bed. need my beauty sleep. hahaha. 

seriously though....HAL errors and hanging on shutdown. sounds like hardware issue. not sure where to start. i'm sure someone will chime in. 

if not...backup...reinstall....monitor...if happens again.....thinking it's hardware. 

query HAL errors in the forums.

---

### Post by nullrev on 2007-09-14
I have a Compaq presario v6000 with a fresh install. My shutdown started hanging immediately after I updated today, so it sounds like we are in much the same boat.

---

