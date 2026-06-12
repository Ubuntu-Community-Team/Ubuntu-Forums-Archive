---
title: "Under 7.04,how to install PCMCIA CDMA modem in Ubuntu (urgent call from China)"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by wucongxiao on 2007-06-20
Hi, is there anyone can help me with this problem? If you can help me , you will help to promote Ubuntu in China since millions chines e  have the same problem. It is due to the PCMCIA CDMA network device is very common in China. I DO have read millions posts on internet, but still doesn't find out methods which can  solve my problem. Since I am a newbie to Ubuntu, I do hope that someone can help me.
My machines is Lenovo's laptop and the CDMA CARD is HST-628P. After I have finished and restarted my Ubuntu, I can find that the CDMA CARD 's light is on ( it's  a sign that Ubuntu recognize my CDMA CARD, I pressume)
And, when I open "device manager", I can find " CDMA CARD" at “82801 Mobile PCI Bridge"-”PCIXX12 Cardbus Controller". And when I have a look of it, the "vender" and "device" all showed "Unknown","Status" showed "Status", "Bus type" showed ”PCMCIA"&#65292;"Device type" showed “serial","Capabilites" showed“serial"&#12290;
and, when I have a look of  ”Advanced", it showed as follows. CAN ANYONE HELP ME WITH THIS KIND OF PROBLEM? 

key  type  value
info.capabilities string "serial"
info.category string serial
info.parent string /org/freedesktop/Hal/devices/pcmcia_1_1
info.product string CDMA CARD
info.udi string /org/freedesktop/Hal/devices/pcmcia_1_1_serial_platform
linux.device_file string /dev/ttyS0
linux.hotplug_type int 2(0X2)
linux.subsystem string tty
linux.sysfs_path string /sys/class/tty/ttys0
serial.device string /dev/ttyS0
serial.physical_device string /org/freedesktop/Hal/devices/pcmcia_1_1
serial.port int 0(0X2)
serial.type string platform

when I dmesg, the Ubuntu system showed that :

[code]lionwoods@lionwoods-laptop:~$ dmesg
[ 0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] sanitize start
[ 0.000000] sanitize end
[ 0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[ 0.000000] copy_e820_map() type is E820_RAM
[ 0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[ 0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[ 0.000000] copy_e820_map() start: 0000000000100000 size: 000000001f586000 end: 000000001f686000 type: 1
[ 0.000000] copy_e820_map() type is E820_RAM
[ 0.000000] copy_e820_map() start: 000000001f686000 size: 000000000007a000 end: 000000001f700000 type: 4
[ 0.000000] copy_e820_map() start: 000000001f700000 size: 0000000000900000 end: 0000000020000000 type: 2
[ 0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[ 0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[ 0.000000] copy_e820_map() start: 00000000fed00000 size: 0000000000000400 end: 00000000fed00400 type: 2
[ 0.000000] copy_e820_map() start: 00000000fed14000 size: 0000000000006000 end: 00000000fed1a000 type: 2
[ 0.000000] copy_e820_map() start: 00000000fed1c000 size: 0000000000074000 end: 00000000fed90000 type: 2
[ 0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[ 0.000000] copy_e820_map() start: 00000000ff000000 size: 0000000001000000 end: 0000000100000000 type: 2
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[ 0.000000] BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000001f686000 (usable)
[ 0.000000] BIOS-e820: 000000001f686000 - 000000001f700000 (ACPI NVS)
[ 0.000000] BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[ 0.000000] BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[ 0.000000] BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[ 0.000000] BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[ 0.000000] BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[ 0.000000] 0MB HIGHMEM available.
[ 0.000000] 502MB LOWMEM available.
[ 0.000000] found SMP MP-table at 000f6c70
[ 0.000000] Entering add_active_range(0, 0, 128646) 0 entries of 256 used
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0 -> 4096
[ 0.000000] Normal 4096 -> 128646
[ 0.000000] HighMem 128646 -> 128646
[ 0.000000] early_node_map[1] active PFN ranges
[ 0.000000] 0: 0 -> 128646
[ 0.000000] On node 0 totalpages: 128646
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 4064 pages, LIFO batch:0
[ 0.000000] Normal zone: 973 pages used for memmap
[ 0.000000] Normal zone: 123577 pages, LIFO batch:31
[ 0.000000] HighMem zone: 0 pages used for memmap
[ 0.000000] DMI 2.4 present.
[ 0.000000] ACPI: RSDP (v000 PTLTD ) @ 0x000f6b90
[ 0.000000] ACPI: RSDT (v001 LENOVO CB-01 0x06040000 LTP 0x00000000) @ 0x1f6e75f6
[ 0.000000] ACPI: FADT (v001 LENOVO CB-01 0x06040000 LOHR 0x0000005a) @ 0x1f6edc86
[ 0.000000] ACPI: MADT (v001 LENOVO CB-01 0x06040000 LOHR 0x0000005a) @ 0x1f6edcfa
[ 0.000000] ACPI: HPET (v001 LENOVO CB-01 0x06040000 LOHR 0x0000005a) @ 0x1f6edd62
[ 0.000000] ACPI: MCFG (v001 LENOVO CB-01 0x06040000 LOHR 0x0000005a) @ 0x1f6edd9a
[ 0.000000] ACPI: SLIC (v001 LENOVO CB-01 0x06040000 LTP 0x00000000) @ 0x1f6ede8a
[ 0.000000] ACPI: MADT (v001 LENOVO CB-01 0x06040000 LTP 0x00000000) @ 0x1f6ede08
[ 0.000000] ACPI: BOOT (v001 LENOVO CB-01 0x06040000 LTP 0x00000001) @ 0x1f6ede62
[ 0.000000] ACPI: SSDT (v001 SataRe SataPri 0x00001000 INTL 0x20050624) @ 0x1f6e83aa
[ 0.000000] ACPI: SSDT (v001 SataRe SataSec 0x00001000 INTL 0x20050624) @ 0x1f6e7d18
[ 0.000000] ACPI: SSDT (v001 PmRef Cpu0Cst 0x00003001 INTL 0x20050624) @ 0x1f6e7b3c
[ 0.000000] ACPI: SSDT (v001 PmRef CpuPm 0x00003000 INTL 0x20050624) @ 0x1f6e7646
[ 0.000000] ACPI: DSDT (v001 LENOVO CB-01 0x06040000 INTL 0x20050624) @ 0x00000000
[ 0.000000] ACPI: PM-Timer IO Port: 0x1008
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: 2 duplicate APIC table ignored.
[ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[ 0.000000] Processor #0 6:14 APIC version 20
[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[ 0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[ 0.000000] Detected 1596.595 MHz processor.
[ 10.899044] Built 1 zonelists. Total pages: 127641
[ 10.899049] Kernel command line: root=UUID=10ab257c-9096-4435-b6af-1beda3957a00 ro quiet splash
[ 10.899219] mapped APIC to ffffd000 (fee00000)
[ 10.899222] mapped IOAPIC to ffffc000 (fec00000)
[ 10.899225] Enabling fast FPU save and restore... done.
[ 10.899228] Enabling unmasked SIMD FPU exception support... done.
[ 10.899237] Initializing CPU#0
[ 10.899317] PID hash table entries: 2048 (order: 11, 8192 bytes)
[ 10.901327] Console: colour VGA+ 80x25
[ 10.901490] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 10.901695] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 10.914840] Memory: 499008k/514584k available (1992k kernel code, 15124k reserved, 893k data, 328k init, 0k highmem)
[ 10.914850] virtual kernel memory layout:
[ 10.914852] fixmap : 0xfff4e000 - 0xfffff000 ( 708 kB)
[ 10.914853] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 10.914854] vmalloc : 0xe0000000 - 0xff7fe000 ( 503 MB)
[ 10.914856] lowmem : 0xc0000000 - 0xdf686000 ( 502 MB)
[ 10.914857] .init : 0xc03d7000 - 0xc0429000 ( 328 kB)
[ 10.914859] .data : 0xc02f2264 - 0xc03d16d4 ( 893 kB)
[ 10.914860] .text : 0xc0100000 - 0xc02f2264 (1992 kB)
[ 10.914864] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 10.915045] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[ 10.915051] hpet0: 3 64-bit timers, 14318180 Hz
[ 10.916057] Using HPET for base-timer
[ 10.994997] Calibrating delay using timer specific routine.. 3196.80 BogoMIPS (lpj=6393612)
[ 10.995042] Security Framework v1.0.0 initialized
[ 10.995050] SELinux: Disabled at boot.
[ 10.995066] Mount-cache hash table entries: 512
[ 10.995199] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
[ 10.995207] monitor/mwait feature present.
[ 10.995209] using mwait in idle threads.
[ 10.995214] CPU: L1 I cache: 32K, L1 D cache: 32K
[ 10.995217] CPU: L2 cache: 1024K
[ 10.995220] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002940 0000c109 00000000 00000000
[ 10.995229] Compat vDSO mapped to ffffe000.
[ 10.995233] Remapping vsyscall page to ffffe000
[ 10.995246] Checking 'hlt' instruction... OK.
[ 11.011091] SMP alternatives: switching to UP code
[ 11.011274] Freeing SMP alternatives: 11k freed
[ 11.011461] Early unpacking initramfs... done
[ 11.370006] ACPI: Core revision 20060707
[ 11.370254] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[ 11.395780] CPU0: Intel(R) Celeron(R) M CPU 420 @ 1.60GHz stepping 08
[ 11.395807] Total of 1 processors activated (3196.80 BogoMIPS).
[ 11.396011] ENABLING IO-APIC IRQs
[ 11.396222] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 11.542677] Brought up 1 CPUs
[ 11.542918] Booting paravirtualized kernel on bare hardware
[ 11.543017] Time: 12:48:36 Date: 05/20/107
[ 11.543043] NET: Registered protocol family 16
[ 11.543125] EISA bus registered
[ 11.543129] ACPI: bus type pci registered
[ 11.543224] PCI: PCI BIOS revision 2.10 entry at 0xfd833, last bus=6
[ 11.543227] PCI: Using configuration type 1
[ 11.543228] Setting up standard PCI resources
[ 11.548319] ACPI: Interpreter enabled
[ 11.548322] ACPI: Using IOAPIC for interrupt routing
[ 11.549058] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 11.549063] PCI: Probing PCI hardware (bus 00)
[ 11.549941] Boot video device is 0000:00:02.0
[ 11.550516] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[ 11.550521] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[ 11.551030] PCI: Transparent bridge - 0000:00:1e.0
[ 11.551104] PCI: Bus #06 (-#09) is hidden behind transparent bridge #05 (-#06) (try 'pci=assign-busses')
[ 11.551107] Please report the result to linux-kernel to fix this permanently
[ 11.551131] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 11.555187] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[ 11.555803] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[ 11.556063] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[ 11.556323] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[ 11.556579] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[ 11.556832] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[ 11.557086] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[ 11.557348] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[ 11.557603] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[ 11.656152] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 11.656162] pnp: PnP ACPI init
[ 11.658609] pnp: PnP ACPI: found 11 devices
[ 11.658614] PnPBIOS: Disabled by ACPI PNP
[ 11.658663] PCI: Using ACPI for IRQ routing
[ 11.658668] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report
[ 11.674714] NET: Registered protocol family 8
[ 11.674716] NET: Registered protocol family 20
[ 11.675029] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
[ 11.675032] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
[ 11.675299] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[ 11.675308] PCI: Bus 6, cardbus bridge: 0000:05:09.0
[ 11.675310] IO window: 00002000-000020ff
[ 11.675315] IO window: 00002400-000024ff
[ 11.675321] PREFETCH window: 30000000-33ffffff
[ 11.675326] MEM window: 34000000-37ffffff
[ 11.675331] PCI: Bridge: 0000:00:1e.0
[ 11.675335] IO window: 2000-2fff
[ 11.675341] MEM window: d0000000-d00fffff
[ 11.675346] PREFETCH window: 30000000-33ffffff
[ 11.675366] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[ 11.675390] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 18 (level, low) -> IRQ 16
[ 11.675419] NET: Registered protocol family 2
[ 11.714593] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[ 11.714667] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[ 11.714775] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[ 11.714828] TCP: Hash tables configured (established 16384 bind 8192)
[ 11.714831] TCP reno registered
[ 11.726641] checking if image is initramfs... it is
[ 12.438512] Freeing initrd memory: 6998k freed
[ 12.438735] Simple Boot Flag at 0x36 set to 0x1
[ 12.439063] audit: initializing netlink socket (disabled)
[ 12.439077] audit(1182343716.584:1): initialized
[ 12.439196] VFS: Disk quotas dquot_6.5.1
[ 12.439216] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 12.439266] io scheduler noop registered
[ 12.439269] io scheduler anticipatory registered
[ 12.439271] io scheduler deadline registered
[ 12.439282] io scheduler cfq registered (default)
[ 12.439575] isapnp: Scanning for PnP cards...
[ 12.793618] isapnp: No Plug & Play device found
[ 12.820159] Real Time Clock Driver v1.12ac
[ 12.820225] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 12.820997] mice: PS/2 mouse device common for all mice
[ 12.821551] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 12.821792] input: Macintosh mouse button emulation as /class/input/input0
[ 12.821869] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 12.821873] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 12.822177] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[ 12.825944] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 12.825950] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 12.826098] EISA: Probing bus 0 at eisa.0
[ 12.826108] Cannot allocate resource for EISA slot 1
[ 12.826110] Cannot allocate resource for EISA slot 2
[ 12.826136] EISA: Detected 0 cards.
[ 12.856225] TCP cubic registered
[ 12.856232] NET: Registered protocol family 1
[ 12.856253] Using IPI No-Shortcut mode
[ 12.856322] ACPI: (supports S0 S3 S4 S5)
[ 12.856371] Magic number: 11:561:835
[ 12.856495] hash matches device ptyu1
[ 12.856693] Freeing unused kernel memory: 328k freed
[ 12.857808] Time: tsc clocksource has been installed.
[ 12.871526] input: AT Translated Set 2 keyboard as /class/input/input1
[ 14.090640] Capability LSM initialized
[ 14.124902] ACPI: CPU0 (power states: C1[C1] C2[C2])
[ 14.124909] ACPI: Processor [CPU0] (supports 8 throttling states)
[ 14.124917] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[ 14.127054] ACPI: Thermal Zone [TZ00] (55 C)
[ 14.502919] usbcore: registered new interface driver usbfs
[ 14.502942] usbcore: registered new interface driver hub
[ 14.502965] usbcore: registered new device driver usb
[ 14.503848] USB Universal Host Controller Interface driver v3.0
[ 14.503898] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 17
[ 14.503910] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[ 14.503915] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 14.504073] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[ 14.504106] uhci_hcd 0000:00:1d.0: irq 17, io base 0x00001820
[ 14.504215] usb usb1: configuration #1 chosen from 1 choice
[ 14.504240] hub 1-0:1.0: USB hub found
[ 14.504246] hub 1-0:1.0: 2 ports detected
[ 14.608867] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[ 14.608881] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[ 14.608886] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 14.608908] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[ 14.608942] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00001840
[ 14.609036] usb usb2: configuration #1 chosen from 1 choice
[ 14.609060] hub 2-0:1.0: USB hub found
[ 14.609066] hub 2-0:1.0: 2 ports detected
[ 14.618702] ieee1394: Initialized config rom entry `ip1394'
[ 14.716782] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 16
[ 14.716796] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[ 14.716801] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 14.716824] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[ 14.716861] uhci_hcd 0000:00:1d.2: irq 16, io base 0x00001860
[ 14.716952] usb usb3: configuration #1 chosen from 1 choice
[ 14.716976] hub 3-0:1.0: USB hub found
[ 14.716984] hub 3-0:1.0: 2 ports detected
[ 3.740000] Time: hpet clocksource has been installed.
[ 3.788000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 19
[ 3.788000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[ 3.788000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[ 3.788000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[ 3.788000] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00001880
[ 3.788000] usb usb4: configuration #1 chosen from 1 choice
[ 3.788000] hub 4-0:1.0: USB hub found
[ 3.788000] hub 4-0:1.0: 2 ports detected
[ 3.896000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 17
[ 3.896000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[ 3.896000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 3.896000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[ 3.896000] ehci_hcd 0000:00:1d.7: debug port 1
[ 3.896000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[ 3.896000] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xd0444000
[ 3.900000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 3.900000] usb usb5: configuration #1 chosen from 1 choice
[ 3.900000] hub 5-0:1.0: USB hub found
[ 3.900000] hub 5-0:1.0: 8 ports detected
[ 4.012000] SCSI subsystem initialized
[ 4.016000] b44.c:v1.01 (Jun 16, 2006)
[ 4.016000] ACPI: PCI Interrupt 0000:05:07.0[A] -> GSI 17 (level, low) -> IRQ 20
[ 4.020000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:16:36:8e:6c:77
[ 4.020000] ACPI: PCI Interrupt 0000:05:09.1[B] -> GSI 19 (level, low) -> IRQ 18
[ 4.072000] libata version 2.20 loaded.
[ 4.072000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18] MMIO=[d0008000-d00087ff] Max Packet=[2048] IR/IT contexts=[4/8]
[ 4.072000] ata_piix 0000:00:1f.2: version 2.10ac1
[ 4.072000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[ 4.232000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
[ 4.232000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[ 4.232000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[ 4.232000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
[ 4.232000] scsi0 : ata_piix
[ 4.404000] ata1.00: ata_hpa_resize 1: sectors = 110060685, hpa_sectors = 117210240
[ 4.404000] ata1.00: Host Protected Area detected.
[ 4.404000] current size : 110060685 sectors (56351 MB)
[ 4.404000] native size : 117210240 sectors (60011 MB)
[ 4.416000] ata1.00: Native size increased to 117210240 sectors
[ 4.416000] ata1.00: ATA-7: ST96812AS, 3.04, max UDMA/133
[ 4.416000] ata1.00: 117210240 sectors, multi 16: LBA48 NCQ (depth 0/32)
[ 4.428000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[ 4.428000] ata1.00: configured for UDMA/133
[ 4.428000] scsi1 : ata_piix
[ 4.560000] usb 3-1: new low speed USB device using uhci_hcd and address 2
[ 4.728000] usb 3-1: configuration #1 chosen from 1 choice
[ 4.744000] usbcore: registered new interface driver hiddev
[ 4.756000] input: HID 062a:0000 as /class/input/input2
[ 4.756000] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:1d.2-1
[ 4.756000] usbcore: registered new interface driver usbhid
[ 4.756000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[ 4.760000] ata2.00: ATAPI, max UDMA/33
[ 4.932000] ata2.00: configured for UDMA/33
[ 4.932000] scsi 0:0:0:0: Direct-Access ATA ST96812AS 3.04 PQ: 0 ANSI: 5
[ 4.932000] scsi 1:0:0:0: CD-ROM PHILIPS CDRW/DVD SCB5265 TX11 PQ: 0 ANSI: 5
[ 4.948000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[ 4.948000] sda: Write Protect is off
[ 4.948000] sda: Mode Sense: 00 3a 00 00
[ 4.948000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4.948000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[ 4.948000] sda: Write Protect is off
[ 4.948000] sda: Mode Sense: 00 3a 00 00
[ 4.948000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4.948000] sda: sda1 sda2 sda3 sda4
[ 4.984000] sd 0:0:0:0: Attached scsi disk sda
[ 4.988000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 4.988000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[ 5.000000] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[ 5.000000] Uniform CD-ROM driver Revision: 3.20
[ 5.004000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 5.320000] Attempting manual resume
[ 5.320000] swsusp: Resume From Partition 8:3
[ 5.320000] PM: Checking swsusp image.
[ 5.320000] PM: Resume from disk failed.
[ 5.360000] ieee1394: Host added: ID:BUS[0-00:1023] GUID[00c09f0000b91b76]
[ 5.368000] kjournald starting. Commit interval 5 seconds
[ 5.368000] EXT3-fs: mounted filesystem with ordered data mode.
[ 16.324000] NET: Registered protocol family 17
[ 17.088000] Linux agpgart interface v0.102 (c) Dave Jones
[ 17.112000] agpgart: Detected an Intel 945GM Chipset.
[ 17.112000] agpgart: Detected 7932K stolen memory.
[ 17.128000] agpgart: AGP aperture is 256M @ 0xc0000000
[ 17.132000] intel_rng: FWH not detected
[ 17.148000] Yenta: CardBus bridge found at 0000:05:09.0 [17aa:2075]
[ 17.148000] Yenta: Enabling burst memory read transactions
[ 17.148000] Yenta: Using CSCINT to route CSC interrupts to PCI
[ 17.148000] Yenta: Routing CardBus interrupts to PCI
[ 17.148000] Yenta TI: socket 0000:05:09.0, mfunc 0x01101b22, devctl 0x66
[ 17.312000] iTCO_vendor_support: vendor-support=0
[ 17.312000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[ 17.312000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[ 17.312000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[ 17.392000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[ 17.392000] Socket status: 30000410
[ 17.392000] Yenta: Raising subordinate bus# of parent bus (#05) from #06 to #09
[ 17.392000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[ 17.392000] cs: IO port probe 0x2000-0x2fff: clean.
[ 17.392000] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd00fffff
[ 17.392000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[ 17.396000] ACPI: PCI Interrupt 0000:05:09.2[A] -> GSI 18 (level, low) -> IRQ 16
[ 17.956000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[ 17.956000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[ 18.032000] pccard: PCMCIA card inserted into slot 0
[ 18.056000] cs: memory probe 0xd0000000-0xd00fffff: excluding 0xd0000000-0xd000ffff
[ 18.068000] pcmcia: registering new device pcmcia0.0
[ 18.100000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1da0b1, caps: 0xa04713/0x204006
[ 18.104000] cs: IO port probe 0x100-0x3af: clean.
[ 18.108000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[ 18.108000] cs: IO port probe 0x820-0x8ff: clean.
[ 18.108000] cs: IO port probe 0xc00-0xcf7: clean.
[ 18.108000] cs: IO port probe 0xa00-0xaff: clean.
[ 18.136000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[ 18.328000] ttyS0: detected caps 00000700 should be 00000100
[ 18.328000] 0.0: ttyS0 at I/O 0x3f8 (irq = 3) is a 16C950/954
[ 18.560000] fuse init (API version 7.Cool
[ 18.620000] lp: driver loaded but no devices found
[ 18.664000] Adding 1236996k swap on /dev/disk/by-uuid/5a25ff31-dcc3-47ba-b6e9-69ed880adaf9. Priority:-1 extents:1 across:1236996k
[ 18.860000] EXT3 FS on sda2, internal journal
[ 34.148000] ieee80211_crypt: registered algorithm 'NULL'
[ 34.152000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[ 34.152000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[ 36.092000] ACPI: AC Adapter [ACAD] (on-line)
[ 36.144000] ACPI: Video Device [GFX0] (multi-head: yes rom: no post: no)
[ 36.184000] ibm_acpi: ec object not found
[ 36.212000] ACPI: Battery Slot [BAT1] (battery absent)
[ 36.264000] input: Power Button (FF) as /class/input/input4
[ 36.272000] ACPI: Power Button (FF) [PWRF]
[ 36.304000] input: Lid Switch as /class/input/input5
[ 36.312000] ACPI: Lid Switch [LID]
[ 36.348000] input: Power Button (CM) as /class/input/input6
[ 36.356000] ACPI: Power Button (CM) [PWRB]
[ 36.388000] input: Sleep Button (CM) as /class/input/input7
[ 36.396000] ACPI: Sleep Button (CM) [SLPB]
[ 36.412000] Using specific hotkey driver
[ 36.524000] No dock devices found.
[ 36.540000] pcc_acpi: loading...
[ 36.588000] wmi_add device=dddf6c00
[ 36.588000] calling WQBA
[ 40.132000] capifs: Rev 1.1.2.3
[ 41.052000] [drm] Initialized drm 1.1.0 20060810
[ 41.056000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 19
[ 41.060000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[ 41.932000] ppdev: user-space parallel port driver
[ 42.556000] apm: BIOS not found.
[ 45.772000] Bluetooth: Core ver 2.11
[ 45.772000] NET: Registered protocol family 31
[ 45.772000] Bluetooth: HCI device and connection manager initialized
[ 45.772000] Bluetooth: HCI socket layer initialized
[ 45.860000] input: Mouseemu virtual keyboard as /class/input/input8
[ 45.860000] input: Mouseemu virtual mouse as /class/input/input9
[ 45.860000] Bluetooth: L2CAP ver 2.8
[ 45.860000] Bluetooth: L2CAP socket layer initialized
[ 46.132000] Bluetooth: RFCOMM socket layer initialized
[ 46.132000] Bluetooth: RFCOMM TTY layer initialized
[ 46.132000] Bluetooth: RFCOMM ver 1.8
[ 60.088000] NET: Registered protocol family 10
[ 60.088000] lo: Disabled Privacy Extensions
[ 60.088000] ADDRCONF(NETDEV_UP): eth0: link is not ready


---

### Post by thekoez on 2008-05-19
Hi, i have similar situation also, and recently i have found the solution from guys from china :)..

run dmesg to find what serial interface is simulated by your PCMCIA card

$ dmesg | grep tty
..
..
[  695.124000] ttyS3: detected caps 00000700 should be 00000100 [695.124000] ttyS3: detected caps 00000700 should be 00000100
[  695.124000] 0.0: ttyS3 at I/O 0x2e8 (irq = 3) is a 16C950/954 [695.124000] 0.0: ttyS3 at I / O 0x2e8 (irq = 3) is a 16C950/954
..
..
since this kind of modem simulate serial interface with baud rate 230400, you need "setserial" to set ttyS3 accordingly

$ sudo apt-get install setserial
..
..
$ setserial /dev/ttyS3 baud_base 230400
$ sudo setserial /dev/ttyS3 -a
/dev/ttyS3, Line 0, UART: 16950/954, Port: 0x03f8, IRQ: 3
	Baud_base: 230400, close_delay: 50, divisor: 0
	closing_wait: 3000
	Flags: spd_normal skip_test

Then you need to edit wvdial.conf

$ sudo gedit /etc/ wvdial.conf 

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Dial Command = ATDT

[Dialer pcmcia]
Baud = 57600
SetVolume = 1
Modem = /dev/ttyS3
Password = password
Username = username
Phone = #777
FlowControl = Hardware (CRTSCTS)

then try to dial using wvdial...

$ sudo wvdial pcmcia
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
OK
--> Re-Sending: ATZ
OK
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
OK
--> Re-Sending: ATZ
OK
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue May 20 05:57:44 2008
..
..

at this point you should be able to access internet.

Happy ubuntuing

---

