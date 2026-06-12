---
title: "external USB disk stopped working"
date: 2007-09-13
forum: Hardware &amp; Laptops
---

### Post by casinino on 2007-09-13
Hi there,
I have a 250 GB external USB disk with 2 partitions on it (FAT32 and NTFS). It is always plugged into the USB port and both partitions are normally mounted at boot without problems.
However, this morning it failed to mount, and I cannot really determine why. The computer does  see the device (Cypress AT2LP RC42) as is evident from  /proc/bus/usb/devices.
But it  does not seem to recognize that this device is a hard disk. 

I should note that MS Windows also sees the device but does not mount it  any longer (wants to install drivers).

My questions are now: 
1) how can I tell Linux that the USB device is a hard disk?
2) and how can I show it in parted?
3) how can I mount it?

Thanks for answering
casinino

output from dmesg and cat /proc/bus/usb/devices:


root@Kandy:~# dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003f6d3800 end: 000000003f7d3800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003f7d3800 size: 000000000082c800 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010007000 end: 00000000f0007000 type: 2
[    0.000000] copy_e820_map() start: 00000000f0008000 size: 0000000000004000 end: 00000000f000c000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed20000 size: 00000000000f0000 end: 00000000fee10000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7d3800 (usable)
[    0.000000]  BIOS-e820: 000000003f7d3800 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 119MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 260051) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   260051
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   260051
[    0.000000] On node 0 totalpages: 260051
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 239 pages used for memmap
[    0.000000]   HighMem zone: 30436 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fc9b0
[    0.000000] ACPI: RSDT (v001 DELL    CPi R   0x27d5041b ASL  0x00000061) @ 0x3f7d4425
[    0.000000] ACPI: FADT (v001 DELL    CPi R   0x27d5041b ASL  0x00000061) @ 0x3f7d4c00
[    0.000000] ACPI: MADT (v001 DELL    CPi R   0x27d5041b ASL  0x00000047) @ 0x3f7d5400
[    0.000000] ACPI: MCFG (v016 DELL    CPi R   0x27d5041b ASL  0x00000061) @ 0x3f7d53c0
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030522) @ 0x3f7d4658
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030522) @ 0x3f7d445d
[    0.000000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
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
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Detected 1396.578 MHz processor.
[   15.269906] Built 1 zonelists.  Total pages: 258020
[   15.269912] Kernel command line: root=UUID=8cde0a23-4782-4867-b7e9-5431398bc747 ro quiet splash
[   15.270111] mapped APIC to ffffd000 (fee00000)
[   15.270114] mapped IOAPIC to ffffc000 (fec00000)
[   15.270118] Enabling fast FPU save and restore... done.
[   15.270122] Enabling unmasked SIMD FPU exception support... done.
[   15.270132] Initializing CPU#0
[   15.270213] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   15.272323] Console: colour VGA+ 80x25
[   15.272775] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   15.273339] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.309552] Memory: 1020020k/1040204k available (1993k kernel code, 19404k reserved, 900k data, 328k init, 122700k highmem)
[   15.309565] virtual kernel memory layout:
[   15.309566]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   15.309568]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.309570]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   15.309571]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   15.309573]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   15.309574]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[   15.309576]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[   15.309580] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.386186] Calibrating delay using timer specific routine.. 2796.21 BogoMIPS (lpj=5592432)
[   15.386239] Security Framework v1.0.0 initialized
[   15.386253] SELinux:  Disabled at boot.
[   15.386272] Mount-cache hash table entries: 512
[   15.386468] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[   15.386485] CPU: L1 I cache: 32K, L1 D cache: 32K
[   15.386489] CPU: L2 cache: 1024K
[   15.386492] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000000 00000000 00000000
[   15.386506] Compat vDSO mapped to ffffe000.
[   15.386513] Remapping vsyscall page to ffffe000
[   15.386531] Checking 'hlt' instruction... OK.
[   15.402338] SMP alternatives: switching to UP code
[   15.402637] Freeing SMP alternatives: 11k freed
[   15.402884] Early unpacking initramfs... done
[   15.795125] ACPI: Core revision 20060707
[   15.803697] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   15.808865] CPU0: Intel(R) Celeron(R) M processor         1.40GHz stepping 08
[   15.808893] Total of 1 processors activated (2796.21 BogoMIPS).
[   15.809088] ENABLING IO-APIC IRQs
[   15.809295] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   15.954057] Brought up 1 CPUs
[   15.954339] Booting paravirtualized kernel on bare hardware
[   15.954421] Time: 10:00:13  Date: 08/13/107
[   15.954451] NET: Registered protocol family 16
[   15.954546] EISA bus registered
[   15.954551] ACPI: bus type pci registered
[   15.992129] PCI: PCI BIOS revision 2.10 entry at 0xfb5be, last bus=10
[   15.992132] PCI: Using configuration type 1
[   15.992134] Setting up standard PCI resources
[   16.007607] ACPI: Interpreter enabled
[   16.007611] ACPI: Using IOAPIC for interrupt routing
[   16.009318] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.009328] PCI: Probing PCI hardware (bus 00)
[   16.009476] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   16.025239] Boot video device is 0000:00:02.0
[   16.025851] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   16.025856] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[   16.026374] PCI: Transparent bridge - 0000:00:1e.0
[   16.026447] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#03) (try 'pci=assign-busses')
[   16.026450] Please report the result to linux-kernel to fix this permanently
[   16.026474] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.065017] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[   16.065323] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[   16.065621] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[   16.065920] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[   16.066210] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.066499] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.066786] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.069593] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[   16.070950] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.070960] pnp: PnP ACPI init
[   16.130371] pnp: PnP ACPI: found 14 devices
[   16.130376] PnPBIOS: Disabled by ACPI PNP
[   16.130431] PCI: Using ACPI for IRQ routing
[   16.130434] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.158915] NET: Registered protocol family 8
[   16.158917] NET: Registered protocol family 20
[   16.178080] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   16.178084] pnp: 00:02: ioport range 0x1000-0x1005 could not be reserved
[   16.178088] pnp: 00:02: ioport range 0x1008-0x100f could not be reserved
[   16.178099] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[   16.178103] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
[   16.178106] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
[   16.178110] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
[   16.178113] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
[   16.178116] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
[   16.178124] pnp: 00:08: ioport range 0x900-0x90f has been reserved
[   16.178127] pnp: 00:08: ioport range 0x910-0x91f has been reserved
[   16.178130] pnp: 00:08: ioport range 0x920-0x92f has been reserved
[   16.178134] pnp: 00:08: ioport range 0x930-0x93f has been reserved
[   16.178137] pnp: 00:08: ioport range 0x940-0x97f has been reserved
[   16.178144] pnp: 00:0d: ioport range 0x7b0-0x7bb has been reserved
[   16.178148] pnp: 00:0d: ioport range 0x7c0-0x7df has been reserved
[   16.178151] pnp: 00:0d: ioport range 0xbb0-0xbbb has been reserved
[   16.178154] pnp: 00:0d: ioport range 0xbc0-0xbdf has been reserved
[   16.178157] pnp: 00:0d: ioport range 0xfb0-0xfbb has been reserved
[   16.178161] pnp: 00:0d: ioport range 0xfc0-0xfdf has been reserved
[   16.178164] pnp: 00:0d: ioport range 0x13b0-0x13bb has been reserved
[   16.178167] pnp: 00:0d: ioport range 0x13c0-0x13df has been reserved
[   16.178458] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   16.178469] PCI: Failed to allocate I/O resource #7:1000@10000 for 0000:00:1e.0
[   16.178539] PCI: Bus 3, cardbus bridge: 0000:02:01.0
[   16.178542]   IO window: 00001400-000014ff
[   16.178548]   IO window: 00001800-000018ff
[   16.178554]   PREFETCH window: 50000000-53ffffff
[   16.178560]   MEM window: 54000000-57ffffff
[   16.178566] PCI: Bridge: 0000:00:1e.0
[   16.178568]   IO window: disabled.
[   16.178574]   MEM window: dfd00000-dfdfffff
[   16.178580]   PREFETCH window: 50000000-53ffffff
[   16.178602] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.178621] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
[   16.178631] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 19 (level, low) -> IRQ 16
[   16.178665] NET: Registered protocol family 2
[   16.218001] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.218137] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.219382] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.220235] TCP: Hash tables configured (established 131072 bind 65536)
[   16.220241] TCP reno registered
[   16.230121] checking if image is initramfs... it is
[   17.005699] Freeing initrd memory: 6773k freed
[   17.006232] audit: initializing netlink socket (disabled)
[   17.006251] audit(1189677613.816:1): initialized
[   17.006337] highmem bounce pool size: 64 pages
[   17.006412] VFS: Disk quotas dquot_6.5.1
[   17.006436] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.006501] io scheduler noop registered
[   17.006505] io scheduler anticipatory registered
[   17.006507] io scheduler deadline registered
[   17.006518] io scheduler cfq registered (default)
[   17.006885] isapnp: Scanning for PnP cards...
[   17.361092] isapnp: No Plug & Play device found
[   17.396776] Real Time Clock Driver v1.12ac
[   17.396850] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.397002] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.398019] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.398252] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 17 (level, low) -> IRQ 17
[   17.398262] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   17.398340] mice: PS/2 mouse device common for all mice
[   17.398949] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.399227] input: Macintosh mouse button emulation as /class/input/input0
[   17.399273] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   17.399279] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   17.399523] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   17.405164] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.405169] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.405313] EISA: Probing bus 0 at eisa.0
[   17.405325] Cannot allocate resource for EISA slot 1
[   17.405363] EISA: Detected 0 cards.
[   17.435472] TCP cubic registered
[   17.435485] NET: Registered protocol family 1
[   17.435509] Using IPI No-Shortcut mode
[   17.435592] ACPI: (supports S0 S3 S4 S5)
[   17.435646]   Magic number: 7:16:22
[   17.436024] Freeing unused kernel memory: 328k freed
[   17.437572] Time: tsc clocksource has been installed.
[   17.437686] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.684952] Capability LSM initialized
[   18.726702] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   18.726709] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.726718] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   18.731150] ACPI: Thermal Zone [THM] (47 C)
[   19.183644] usbcore: registered new interface driver usbfs
[   19.183670] usbcore: registered new interface driver hub
[   19.183698] usbcore: registered new device driver usb
[   19.184776] USB Universal Host Controller Interface driver v3.0
[   19.184834] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 18
[   19.184852] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   19.184857] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   19.185024] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   19.185089] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000bf80
[   19.185222] usb usb1: configuration #1 chosen from 1 choice
[   19.185250] hub 1-0:1.0: USB hub found
[   19.185259] hub 1-0:1.0: 2 ports detected
[   19.259367] SCSI subsystem initialized
[   19.265564] libata version 2.20 loaded.
[   19.289215] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[   19.289234] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   19.289239] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   19.289265] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   19.289300] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[   19.289409] usb usb2: configuration #1 chosen from 1 choice
[   19.289438] hub 2-0:1.0: USB hub found
[   19.289448] hub 2-0:1.0: 2 ports detected
[   19.303227] ieee1394: Initialized config rom entry `ip1394'
[   19.393146] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   19.393164] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   19.393169] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   19.393197] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   19.393232] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000bf40
[   19.393336] usb usb3: configuration #1 chosen from 1 choice
[   19.393369] hub 3-0:1.0: USB hub found
[   19.393375] hub 3-0:1.0: 2 ports detected
[   19.497132] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 16
[   19.497151] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   19.497156] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   19.497182] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   19.497218] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000bf20
[   19.497322] usb usb4: configuration #1 chosen from 1 choice
[   19.497352] hub 4-0:1.0: USB hub found
[   19.497360] hub 4-0:1.0: 2 ports detected
[    4.176000] Time: acpi_pm clocksource has been installed.
[    4.228000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 18
[    4.228000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.228000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.228000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.228000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.228000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.228000] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80800
[    4.232000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.232000] usb usb5: configuration #1 chosen from 1 choice
[    4.232000] hub 5-0:1.0: USB hub found
[    4.232000] hub 5-0:1.0: 8 ports detected
[    4.336000] ahci 0000:00:1f.2: version 2.1
[    4.336000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[    4.336000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[    4.336000] ahci: probe of 0000:00:1f.2 failed with error -22
[    4.340000] ata_piix 0000:00:1f.2: version 2.10ac1
[    4.340000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.496000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[    4.496000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.496000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[    4.496000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[    4.496000] scsi0 : ata_piix
[    4.628000] usb 5-7: new high speed USB device using ehci_hcd and address 2
[    4.660000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.660000] ata1.00: ATA-6: FUJITSU MHV2080AH, 00000096, max UDMA/100
[    4.660000] ata1.00: 156301488 sectors, multi 8: LBA 
[    4.660000] ata1.00: applying bridge limits
[    4.672000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.672000] ata1.00: configured for UDMA/100
[    4.672000] scsi1 : ata_piix
[    4.760000] usb 5-7: config 1 has an invalid interface number: 2 but max is 1
[    4.760000] usb 5-7: config 1 has no interface number 1
[    4.760000] usb 5-7: configuration #1 chosen from 1 choice
[    4.784000] usbcore: registered new interface driver hiddev
[    4.788000] hiddev96: USB HID v1.10 Device [Cypress AT2LP RC42] on usb-0000:00:1d.7-7
[    4.788000] usbcore: registered new interface driver usbhid
[    4.788000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    4.992000] ata2.00: ATAPI, max UDMA/33
[    5.156000] ata2.00: configured for UDMA/33
[    5.156000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2080A 0000 PQ: 0 ANSI: 5
[    5.156000] scsi 1:0:0:0: CD-ROM            SONY     DVD+-RW DW-D56A  PDS3 PQ: 0 ANSI: 5
[    5.156000] b44.c:v1.01 (Jun 16, 2006)
[    5.156000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 19
[    5.160000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:12:3f:12:2f:e2
[    5.160000] ACPI: PCI Interrupt 0000:02:01.2[B] -> GSI 18 (level, low) -> IRQ 19
[    5.212000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[dfdf8800-dfdf8fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.224000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    5.224000] sda: Write Protect is off
[    5.224000] sda: Mode Sense: 00 3a 00 00
[    5.224000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.224000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    5.224000] sda: Write Protect is off
[    5.224000] sda: Mode Sense: 00 3a 00 00
[    5.224000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.224000]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 sda9 >
[    5.384000] sd 0:0:0:0: Attached scsi disk sda
[    5.388000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.388000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.392000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    5.392000] Uniform CD-ROM driver Revision: 3.20
[    5.392000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.880000] Attempting manual resume
[    5.880000] swsusp: Resume From Partition 8:9
[    5.880000] PM: Checking swsusp image.
[    5.880000] PM: Resume from disk failed.
[    5.932000] kjournald starting.  Commit interval 5 seconds
[    5.932000] EXT3-fs: mounted filesystem with ordered data mode.
[    6.484000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[4a4fc00036c5d830]
[   18.228000] b44: eth0: BUG!  Timeout waiting for bit 00000002 of register 42c to clear.
[   19.312000] NET: Registered protocol family 17
[   20.196000] Linux agpgart interface v0.102 (c) Dave Jones
[   20.220000] agpgart: Detected an Intel 915GM Chipset.
[   20.220000] agpgart: Detected 7932K stolen memory.
[   20.240000] agpgart: AGP aperture is 256M @ 0xc0000000
[   20.268000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:01af]
[   20.268000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   20.268000] Yenta: Routing CardBus interrupts to PCI
[   20.268000] Yenta TI: socket 0000:02:01.0, mfunc 0x01001022, devctl 0x64
[   20.500000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   20.500000] Socket status: 30000006
[   20.500000] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   20.500000] pcmcia: parent PCI bridge Memory window: 0xdfd00000 - 0xdfdfffff
[   20.500000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   20.584000] iTCO_vendor_support: vendor-support=0
[   21.000000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   21.000000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   21.000000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   21.084000] input: PC Speaker as /class/input/input2
[   21.104000] parport: PnPBIOS parport detected.
[   21.104000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   21.112000] ieee80211_crypt: registered algorithm 'NULL'
[   21.124000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   21.124000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   21.212000] intel_rng: FWH not detected
[   21.276000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   21.276000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   21.276000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 17 (level, low) -> IRQ 17
[   21.276000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   21.368000] input: PS/2 Mouse as /class/input/input3
[   21.464000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   21.496000] usbcore: registered new interface driver xpad
[   21.496000] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   21.684000] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[   21.728000] cs: IO port probe 0x100-0x3af: clean.
[   21.728000] cs: IO port probe 0x3e0-0x4ff: clean.
[   21.728000] cs: IO port probe 0x820-0x8ff: clean.
[   21.732000] cs: IO port probe 0xc00-0xcf7: clean.
[   21.732000] cs: IO port probe 0xa00-0xaff: clean.
[   21.788000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 18
[   21.788000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   22.608000] intel8x0_measure_ac97_clock: measured 55441 usecs
[   22.608000] intel8x0: clocking to 48000
[   22.780000] fuse init (API version 7.8)
[   22.812000] lp0: using parport0 (interrupt-driven).
[   22.864000] Adding 1140572k swap on /dev/disk/by-uuid/3e0be10e-b44f-4fe6-a396-d6206b324a1a.  Priority:-1 extents:1 across:1140572k
[   23.088000] EXT3 FS on sda7, internal journal
[   47.284000] NET: Registered protocol family 10
[   47.284000] lo: Disabled Privacy Extensions
[   47.284000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   57.664000] eth1: no IPv6 routers present
[   75.844000] kjournald starting.  Commit interval 5 seconds
[   75.844000] EXT3 FS on sda8, internal journal
[   75.844000] EXT3-fs: mounted filesystem with ordered data mode.
[   77.324000] Using specific hotkey driver
[   77.376000] input: Lid Switch as /class/input/input5
[   77.376000] ACPI: Lid Switch [LID]
[   77.452000] input: Power Button (CM) as /class/input/input6
[   77.456000] ACPI: Power Button (CM) [PBTN]
[   77.500000] input: Sleep Button (CM) as /class/input/input7
[   77.504000] ACPI: Sleep Button (CM) [SBTN]
[   77.536000] ACPI: ACPI Dock Station Driver 
[   77.672000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   77.672000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   78.016000] ACPI: Battery Slot [BAT0] (battery present)
[   78.016000] ACPI: Battery Slot [BAT1] (battery absent)
[   78.036000] ACPI: AC Adapter [AC] (on-line)
[   78.056000] ibm_acpi: ec object not found
[   78.136000] pcc_acpi: loading...
[   84.844000] ppdev: user-space parallel port driver
[   84.872000] [drm] Initialized drm 1.1.0 20060810
[   84.908000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 18
[   84.912000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   86.848000] apm: BIOS not found.
[  362.428000] usb 5-7: USB disconnect, address 2
[  370.668000] usb 5-7: new high speed USB device using ehci_hcd and address 3
[  370.800000] usb 5-7: config 1 has an invalid interface number: 2 but max is 1
[  370.800000] usb 5-7: config 1 has no interface number 1
[  370.800000] usb 5-7: configuration #1 chosen from 1 choice
[  370.800000] hiddev96: USB HID v1.10 Device [Cypress AT2LP RC42] on usb-0000:00:1d.7-7
root@Kandy:~# cat /proc/bus/usb/devices 

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
B:  Alloc=  0/800 us ( 0%), #Int=  1, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=05 Lev=01 Prnt=01 Port=06 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04b4 ProdID=6830 Rev= 0.41
S:  Product=Cypress AT2LP RC42
S:  SerialNumber=M00000000000
C:* #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=06 Prot=50 Driver=(none)
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=86(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I:  If#= 2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=64ms

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms



EOF

---

### Post by xiota on 2007-09-13
I assume that when you write the drive is not recognized as a hard drive, no /dev/sdx device was created for the drive.

Since you wrote that the drive also does not work with Windows, I suspect hardware failure.  Here are some types of failures I've experienced:
[LIST]
[*]The cable went bad.
[*]The enclosure stopped working.
[*]The hard drive itself failed.
[/LIST]
I would move the hard drive to an enclosure that is known to be working.  If you are willing to risk damaging another hard drive, you may test the cable and enclosure with a known working hard drive.

If a /dev/sdxn device is created when you attempt to access the drive with the working enclosure, then you may attempt to mount it read-only.  If it mounts, the best option is to copy all of your data off the drive.  Verify the data (I usually compare md5 checksums).  And reformat the drive.

The next best option is to copy important data off the drive, then run appropriate file system checks from the operating system from which the file system originates.

If a /dev/sdx device was created, but not /dev/sdxn, when you plugged in the drive, then the partition tables of the drive were probably corrupted.  If that happened, there is a good chance you will lose data.

If the drive has only one partition, you can try mounting the offset where that partition would be located.  Something like the following might work (you're responsible for double checking though):

```
sudo mount -t ntfs -o ro,offset=32256 /dev/sdx
```

Change "ntfs" and "sdx" to match your circumstances.

You may also try recovering partitions with "testdisk".  Make sure any of your attempts at mounting have been unmounted.  After running test disk, run "sync" and disconnect the drive from the computer for a dozen seconds.  After reconnecting the drive, check for /dev/sdxn.  If it exists, mount read-only and backup your data.

If none of the above works, the hard drive itself may be damaged.  If that were the case, you'd probably know by now.  The drive would likely have been producing weird noises for a while.  I've also had drives simply fail to spin up.  In one case, I retrieved the data by changing the drive's circuit board.

---

### Post by bliffle on 2007-09-17
Some of those external USB boxes are better than others. All I buy now are the $30 boxes that have an internal slot to hold the innards in place, and they have the 40pin connector opposite from the USB connector. There is a real danger of bending a pin when inserting a drive in a USB box, so you have to be careful, and I find the $15 box is most unreliable.

Some of the queries for shooting these bugs are:

fdisk -l
mount -l
dmesg
lspci
lsdev

Sometimes "GNOME Parted" from the pulldown will display useful info and help figure it out.

---

