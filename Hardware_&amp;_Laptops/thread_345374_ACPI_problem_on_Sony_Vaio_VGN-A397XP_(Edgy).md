---
title: "ACPI problem on Sony Vaio VGN-A397XP (Edgy)"
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by lollypork on 2007-01-24
Hey everybody :)

I'm having a problem here. I can't get ACPI to work on a Sony Vaio VGN-A397XP laptop, even the edgy livecd had problems before I wrote acpi=off in the boot parameters. This is a fresh install of Edgy (Ubuntu, Gnome), and everything else is working.

ACPI being off means that the laptop won't shut down by itself, I have to press the power button after it has shutdown. The batteryindicator in the panel just shows what was connected at boot, and if I press a hotkey on computer (like volume up/down) nothing happens, but the keyboard doesn't work anymore until the next reboot (nothing happens when keys are pressed).

Here's my dmesg (system booted with acpi=off):

```

[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001ffc0000 (usable)
[17179569.184000]  BIOS-e820: 000000001ffc0000 - 000000001ffcf000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001ffcf000 - 0000000020000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 131008
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126912 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] Intel MultiProcessor Specification v1.4
[17179569.184000]     Virtual Wire compatibility mode.
[17179569.184000] OEM ID: ASUSTeK  Product ID: SONOMA       APIC at: 0xFEE00000
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] I/O APIC #1 Version 32 at 0xFEC00000.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Processors: 1
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda3 ro quiet splash acpi=off noapic irqpoll
[17179569.184000] Misrouted IRQ fixup and polling support enabled
[17179569.184000] This may significantly impact system performance
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1995.409 MHz processor.
[   13.635801] Using tsc for high-res timesource
[   13.636995] Console: colour VGA+ 80x25
[   13.637222] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   13.637429] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.648217] Memory: 509800k/524032k available (1910k kernel code, 13596k reserved, 1069k data, 308k init, 0k highmem)
[   13.648220] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.727708] Calibrating delay using timer specific routine.. 4006.20 BogoMIPS (lpj=8012418)
[   13.727741] Security Framework v1.0.0 initialized
[   13.727748] SELinux:  Disabled at boot.
[   13.727761] Mount-cache hash table entries: 512
[   13.727875] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[   13.727883] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[   13.727891] CPU: L1 I cache: 32K, L1 D cache: 32K
[   13.727894] CPU: L2 cache: 2048K
[   13.727895] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000180 00000000 00000000
[   13.727910] Checking 'hlt' instruction... OK.
[   13.743760] SMP alternatives: switching to UP code
[   13.743912] Freeing SMP alternatives: 16k freed
[   13.744011] checking if image is initramfs... it is
[   14.191372] Freeing initrd memory: 5322k freed
[   14.191381] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 08
[   14.191405] Total of 1 processors activated (4006.20 BogoMIPS).
[   14.295553] Brought up 1 CPUs
[   14.295572] migration_cost=0
[   14.295854] NET: Registered protocol family 16
[   14.295881] EISA bus registered
[   14.295996] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=3
[   14.296003] PCI: Using configuration type 1
[   14.296005] Setting up standard PCI resources
[   14.296347] ACPI: Interpreter disabled.
[   14.296351] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.296357] pnp: PnP ACPI: disabled
[   14.296360] PnPBIOS: Scanning system for PnP BIOS support...
[   14.296386] PnPBIOS: Found PnP BIOS installation structure at 0xc00f4650
[   14.296388] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x526a, dseg 0xf0000
[   14.296743] PnPBIOS: 13 nodes reported by PnP BIOS; 13 recorded by driver
[   14.296774] PCI: Probing PCI hardware
[   14.296777] PCI: Probing PCI hardware (bus 00)
[   14.297308] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   14.297312] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   14.297365] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[   14.297551] Boot video device is 0000:03:00.0
[   14.297999] PCI: Transparent bridge - 0000:00:1e.0
[   14.298572] PCI: Using IRQ router PIIX/ICH [8086/2641] at 0000:00:1f.0
[   14.298592] PCI: Found IRQ 3 for device 0000:00:1f.1
[   14.298618] PCI: Sharing IRQ 3 with 0000:01:02.0
[   14.298630] PCI: Found IRQ 7 for device 0000:01:01.0
[   14.298639] PCI: Sharing IRQ 7 with 0000:00:1d.3
[   14.306812] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   14.306815] pnp: 00:0a: ioport range 0xcf8-0xcff could not be reserved
[   14.306818] pnp: 00:0a: ioport range 0x480-0x4bf has been reserved
[   14.306820] pnp: 00:0a: ioport range 0x800-0x87f has been reserved
[   14.306985] PCI: Bridge: 0000:00:01.0
[   14.306987]   IO window: a000-cfff
[   14.306990]   MEM window: fea00000-feafffff
[   14.306993]   PREFETCH window: cff00000-dfefffff
[   14.307002] PCI: Bus 2, cardbus bridge: 0000:01:01.0
[   14.307004]   IO window: 00009000-000090ff
[   14.307008]   IO window: 00009400-000094ff
[   14.307013]   PREFETCH window: 30000000-31ffffff
[   14.307017]   MEM window: 34000000-35ffffff
[   14.307022] PCI: Bridge: 0000:00:1e.0
[   14.307024]   IO window: 9000-9fff
[   14.307029]   MEM window: fe900000-fe9fffff
[   14.307033]   PREFETCH window: 30000000-32ffffff
[   14.307046] PCI: Found IRQ 11 for device 0000:00:01.0
[   14.307050] PCI: Sharing IRQ 11 with 0000:00:1b.0
[   14.307068] PCI: Sharing IRQ 11 with 0000:03:00.0
[   14.307079] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   14.307091] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   14.307108] PCI: Found IRQ 7 for device 0000:01:01.0
[   14.307117] PCI: Sharing IRQ 7 with 0000:00:1d.3
[   14.307153] NET: Registered protocol family 2
[   14.335464] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   14.335544] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   14.335675] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   14.335733] TCP: Hash tables configured (established 16384 bind 8192)
[   14.335735] TCP reno registered
[   14.336174] audit: initializing netlink socket (disabled)
[   14.336182] audit(1169647518.784:1): initialized
[   14.336274] VFS: Disk quotas dquot_6.5.1
[   14.336287] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   14.336327] Initializing Cryptographic API
[   14.336331] io scheduler noop registered
[   14.336336] io scheduler anticipatory registered
[   14.336340] io scheduler deadline registered
[   14.336349] io scheduler cfq registered (default)
[   14.336458] PCI: Found IRQ 11 for device 0000:00:01.0
[   14.336462] PCI: Sharing IRQ 11 with 0000:00:1b.0
[   14.336480] PCI: Sharing IRQ 11 with 0000:03:00.0
[   14.336491] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   14.336518] assign_interrupt_mode Found MSI capability
[   14.336554] Allocate Port Service[0000:00:01.0:pcie00]
[   14.336634] isapnp: Scanning for PnP cards...
[   14.692573] isapnp: No Plug & Play device found
[   14.710572] Real Time Clock Driver v1.12ac
[   14.710629] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.711185] mice: PS/2 mouse device common for all mice
[   14.711661] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.711829] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   14.711833] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   14.712062] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   14.713807] serio: i8042 AUX port at 0x60,0x64 irq 12
[   14.713868] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.714175] EISA: Probing bus 0 at eisa.0
[   14.714206] EISA: Detected 0 cards.
[   14.714399] TCP bic registered
[   14.714410] NET: Registered protocol family 1
[   14.714415] NET: Registered protocol family 8
[   14.714417] NET: Registered protocol family 20
[   14.714437] Using IPI No-Shortcut mode
[   14.714632] Freeing unused kernel memory: 308k freed
[   14.741830] input: AT Translated Set 2 keyboard as /class/input/input0
[   15.783533] Capability LSM initialized
[   16.030238] ICH6: IDE controller at PCI slot 0000:00:1f.1
[   16.030253] PCI: Found IRQ 3 for device 0000:00:1f.1
[   16.030281] PCI: Sharing IRQ 3 with 0000:01:02.0
[   16.030291] ICH6: chipset revision 4
[   16.030293] ICH6: not 100% native mode: will probe irqs later
[   16.030304]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[   16.030317]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
[   16.030326] Probing IDE interface ide0...
[   16.770381] hda: SONY DVD RW DW-D56A, ATAPI CD/DVD-ROM drive
[   17.445921] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   17.446038] Probing IDE interface ide1...
[   18.023042] hda: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   18.023050] Uniform CD-ROM driver Revision: 3.20
[   18.063506] SCSI subsystem initialized
[   18.065958] libata version 1.20 loaded.
[   18.067105] ahci 0000:00:1f.2: version 1.2
[   18.067125] PCI: Found IRQ 5 for device 0000:00:1f.2
[   18.067144] PCI: Sharing IRQ 5 with 0000:00:1f.3
[   18.067159] PCI: Sharing IRQ 5 with 0000:01:03.0
[   23.886410] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   23.886417] ahci 0000:00:1f.2: AHCI 0001.0000 32 slots 4 ports 1.5 Gbps 0x5 impl IDE mode
[   23.886420] ahci 0000:00:1f.2: flags: 64bit ncq pm led slum part 
[   23.886458] ata1: SATA max UDMA/133 cmd 0xE082AD00 ctl 0x0 bmdma 0x0 irq 5
[   23.886475] ata2: SATA max UDMA/133 cmd 0xE082AD80 ctl 0x0 bmdma 0x0 irq 5
[   23.886493] ata3: SATA max UDMA/133 cmd 0xE082AE00 ctl 0x0 bmdma 0x0 irq 5
[   23.886510] ata4: SATA max UDMA/133 cmd 0xE082AE80 ctl 0x0 bmdma 0x0 irq 5
[   24.262221] ata1: SATA link up 1.5 Gbps (SStatus 113)
[   24.263219] ata1: dev 0 cfg 49:0f00 82:746b 83:7f69 84:4023 85:f469 86:3e49 87:4023 88:203f
[   24.263223] ata1: dev 0 ATA-6, max UDMA/100, 156301488 sectors: LBA48
[   24.264447] ata1: dev 0 configured for UDMA/100
[   24.264449] scsi0 : ahci
[   24.470102] ata2: SATA link down (SStatus 0)
[   24.470105] scsi1 : ahci
[   24.673996] ata3: SATA link down (SStatus 0)
[   24.673998] scsi2 : ahci
[   24.877889] ata4: SATA link down (SStatus 0)
[   24.877892] scsi3 : ahci
[   24.878046]   Vendor: ATA       Model: HTS541080G9SA00   Rev: MB4O
[   24.878055]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   24.885181] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   24.885192] sda: Write Protect is off
[   24.885194] sda: Mode Sense: 00 3a 00 00
[   24.885205] SCSI device sda: drive cache: write back
[   24.885243] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   24.885250] sda: Write Protect is off
[   24.885252] sda: Mode Sense: 00 3a 00 00
[   24.885262] SCSI device sda: drive cache: write back
[   24.885265]  sda: sda1 sda2 sda3 sda4 < sda5 >
[   25.275355] sd 0:0:0:0: Attached scsi disk sda
[   25.724762] Probing IDE interface ide1...
[   25.753127] usbcore: registered new driver usbfs
[   25.753144] usbcore: registered new driver hub
[   25.793775] USB Universal Host Controller Interface driver v3.0
[   25.794056] PCI: Found IRQ 3 for device 0000:00:1d.0
[   25.794069] PCI: Sharing IRQ 3 with 0000:00:1d.7
[   25.794085] PCI: Sharing IRQ 3 with 0000:01:01.2
[   25.794099] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   25.794103] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   25.794306] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   25.794332] uhci_hcd 0000:00:1d.0: irq 3, io base 0x0000d880
[   25.794465] usb usb1: configuration #1 chosen from 1 choice
[   25.794549] hub 1-0:1.0: USB hub found
[   25.794555] hub 1-0:1.0: 2 ports detected
[   25.798476] ieee1394: Initialized config rom entry `ip1394'
[   25.901529] PCI: Found IRQ 6 for device 0000:00:1d.1
[   25.901559] PCI: Sharing IRQ 6 with 0000:01:01.3
[   25.901571] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   25.901575] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   25.901696] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   25.901723] uhci_hcd 0000:00:1d.1: irq 6, io base 0x0000dc00
[   25.901846] usb usb2: configuration #1 chosen from 1 choice
[   25.901932] hub 2-0:1.0: USB hub found
[   25.901937] hub 2-0:1.0: 2 ports detected
[   26.009404] PCI: Found IRQ 4 for device 0000:00:1d.2
[   26.009436] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   26.009439] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   26.009519] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   26.009540] uhci_hcd 0000:00:1d.2: irq 4, io base 0x0000e000
[   26.009699] usb usb3: configuration #1 chosen from 1 choice
[   26.009780] hub 3-0:1.0: USB hub found
[   26.009785] hub 3-0:1.0: 2 ports detected
[   26.117347] PCI: Found IRQ 7 for device 0000:00:1d.3
[   26.117369] PCI: Sharing IRQ 7 with 0000:01:01.0
[   26.117380] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   26.117383] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   26.117466] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   26.117488] uhci_hcd 0000:00:1d.3: irq 7, io base 0x0000e080
[   26.117645] usb usb4: configuration #1 chosen from 1 choice
[   26.117731] hub 4-0:1.0: USB hub found
[   26.117736] hub 4-0:1.0: 2 ports detected
[   26.141228] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   26.225359] PCI: Found IRQ 3 for device 0000:01:01.2
[   26.225365] PCI: Sharing IRQ 3 with 0000:00:1d.0
[   26.225371] PCI: Sharing IRQ 3 with 0000:00:1d.7
[   26.275523] PCI: Found IRQ 3 for device 0000:00:1d.7
[   26.275529] PCI: Sharing IRQ 3 with 0000:00:1d.0
[   26.275549] PCI: Sharing IRQ 3 with 0000:01:01.2
[   26.275561] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   26.275564] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   26.275655] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   26.275684] ehci_hcd 0000:00:1d.7: debug port 1
[   26.275690] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   26.275694] ehci_hcd 0000:00:1d.7: irq 3, io mem 0xfebff800
[   26.279579] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   26.279692] usb usb5: configuration #1 chosen from 1 choice
[   26.279785] hub 5-0:1.0: USB hub found
[   26.279791] hub 5-0:1.0: 8 ports detected
[   26.301098] usb 1-2: device descriptor read/all, error -71
[   26.307968] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[3]  MMIO=[fe9ff000-fe9ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   26.450289] Attempting manual resume
[   26.471680] kjournald starting.  Commit interval 5 seconds
[   26.471687] EXT3-fs: mounted filesystem with ordered data mode.
[   27.096733] usb 1-2: new low speed USB device using uhci_hcd and address 4
[   27.279588] usb 1-2: configuration #1 chosen from 1 choice
[   27.524509] usb 4-2: new full speed USB device using uhci_hcd and address 2
[   27.580614] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460301d48eac]
[   27.733658] usb 4-2: configuration #1 chosen from 1 choice
[   35.332663] Linux agpgart interface v0.101 (c) Dave Jones
[   35.348223] agpgart: Detected an Intel 915GM Chipset.
[   35.585345] input: PC Speaker as /class/input/input1
[   35.699340] agpgart: AGP aperture is 256M @ 0x0
[   35.774800] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.806792] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.816867] input: PS/2 Mouse as /class/input/input2
[   35.835771] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[   35.912816] hw_random: RNG not detected
[   36.117501] ts: Compaq touchscreen protocol output
[   36.333442] PCI: Found IRQ 11 for device 0000:00:1b.0
[   36.333468] PCI: Sharing IRQ 11 with 0000:03:00.0
[   36.333491] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   36.384422] usbcore: registered new driver hiddev
[   36.450556] input: Logitech USB Receiver as /class/input/input4
[   36.450621] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
[   36.450635] usbcore: registered new driver usbhid
[   36.450638] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   36.839677] PCI: Found IRQ 7 for device 0000:01:01.0
[   36.839689] PCI: Sharing IRQ 7 with 0000:00:1d.3
[   36.839718] Yenta: CardBus bridge found at 0000:01:01.0 [104d:818f]
[   36.839735] Yenta: Enabling burst memory read transactions
[   36.839740] Yenta: Using CSCINT to route CSC interrupts to PCI
[   36.839741] Yenta: Routing CardBus interrupts to PCI
[   36.839746] Yenta TI: socket 0000:01:01.0, mfunc 0x01001b22, devctl 0x64
[   36.956833] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   37.006163] Bluetooth: Core ver 2.8
[   37.006166] NET: Registered protocol family 31
[   37.006168] Bluetooth: HCI device and connection manager initialized
[   37.006177] Bluetooth: HCI socket layer initialized
[   37.017158] Bluetooth: HCI USB driver ver 2.9
[   37.019569] usbcore: registered new driver hci_usb
[   37.042852] ieee80211_crypt: registered algorithm 'NULL'
[   37.044648] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   37.044651] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   37.071767] Yenta: ISA IRQ mask 0x0600, PCI irq 7
[   37.071771] Socket status: 30000006
[   37.071775] pcmcia: parent PCI bridge I/O window: 0x9000 - 0x9fff
[   37.071777] cs: IO port probe 0x9000-0x9fff: clean.
[   37.071960] pcmcia: parent PCI bridge Memory window: 0xfe900000 - 0xfe9fffff
[   37.071962] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x32ffffff
[   37.084830] r8169 Gigabit Ethernet driver 2.2LK loaded
[   37.084852] PCI: Found IRQ 5 for device 0000:01:03.0
[   37.084870] PCI: Sharing IRQ 5 with 0000:00:1f.2
[   37.084873] PCI: Sharing IRQ 5 with 0000:00:1f.3
[   37.084990] eth0: Identified chip type is 'RTL8169s/8110s'.
[   37.084993] eth0: RTL8169 at 0xe0a96c00, 00:01:4a:1c:e3:52, IRQ 5
[   37.159237] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[   37.159241] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   37.159244] Driver 'ipw2200' needs updating - please use bus_type methods
[   37.159326] PCI: Found IRQ 3 for device 0000:01:02.0
[   37.159343] PCI: Sharing IRQ 3 with 0000:00:1f.1
[   37.164265] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   37.447911] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[   37.495296] r8169: eth0: link down
[   37.569782] cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x370-0x377
[   37.571204] cs: IO port probe 0x3e0-0x4ff: clean.
[   37.571575] cs: IO port probe 0x820-0x8ff: clean.
[   37.571850] cs: IO port probe 0xc00-0xcf7: clean.
[   37.572456] cs: IO port probe 0xa00-0xaff: clean.
[   37.706205] lp: driver loaded but no devices found
[   37.723406] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   37.723410] ieee1394: sbp2: Try serialize_io=0 for better performance
[   37.740702] Adding 7325600k swap on /dev/disk/by-uuid/ea30e755-834c-453d-a600-30fe2e4b00a1.  Priority:-1 extents:1 across:7325600k
[   37.840688] EXT3 FS on sda3, internal journal
[   38.098048] NTFS driver 2.1.27 [Flags: R/O MODULE].
[   38.144045] NTFS volume version 3.1.
[   38.187254] NTFS volume version 3.1.
[   38.560279] NET: Registered protocol family 17
[   40.833688] eth1: NETDEV_TX_BUSY returned; driver should report queue full via ieee_device->is_queue_full.
[   44.078447] [drm] Initialized drm 1.0.1 20051102
[   44.086957] PCI: Found IRQ 11 for device 0000:03:00.0
[   44.086964] PCI: Sharing IRQ 11 with 0000:00:1b.0
[   44.087761] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   44.419431] apm: BIOS not found.
[   46.096726] [drm] Setting GART location based on new memory map
[   46.097548] [drm] Loading R300 Microcode
[   46.097595] [drm] writeback test succeeded in 1 usecs
[   47.437442] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   47.439350] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = off
[   47.439355] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[   47.439357] sonypi: device allocated minor is 63
[   47.501077] input: Sony Vaio Jogdial as /class/input/input5
[   47.586056] input: Sony Vaio Keys as /class/input/input6
[   47.756117] Bluetooth: L2CAP ver 2.8
[   47.756121] Bluetooth: L2CAP socket layer initialized
[   47.857325] Bluetooth: RFCOMM socket layer initialized
[   47.857336] Bluetooth: RFCOMM TTY layer initialized
[   47.857338] Bluetooth: RFCOMM ver 1.7
[   56.825817] NET: Registered protocol family 10
[   56.825898] lo: Disabled Privacy Extensions
[   56.825935] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   56.825993] IPv6 over IPv4 tunneling driver
[   66.975918] eth1: no IPv6 routers present
[   70.885357] ieee80211_crypt: registered algorithm 'CCMP'
[   89.036398] eth1: no IPv6 routers present
[  276.281791] hda: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[  384.624173] hda: cdrom_pc_intr: The drive appears confused (ireason = 0x01)

```

I don't know if it's possible to post a dmesg when it doesn't boot, I'll try something - don't know if this dmesg is useful.

I'd appreciate any help at all. :)

Cheers!

---

### Post by lollypork on 2007-01-28
Bump. :)

---

