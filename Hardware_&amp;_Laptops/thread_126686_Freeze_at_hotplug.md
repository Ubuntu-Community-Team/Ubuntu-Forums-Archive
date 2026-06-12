---
title: "Freeze at hotplug"
date: 2006-02-07
forum: Hardware &amp; Laptops
---

### Post by Joh_ on 2006-02-07
I just installed ubuntu on my dad's computer, but I can't seem to start it too well. It just freezes at the hotplug initialization. Same goes for the Live CD after trying with that too.

Obviously, something isn't right, and since it's the first time I encounter this, I have no idea where to start. :mad:

I *can* start it by pressing Alt+SysRq+E (SysRq = PrintScreen), but having to do that every time you try starting the computer can be annoying.

I'm not too sure about his hardware, but what I DO know, is this:
Mainboard: FIC P4M-915G
CPU: P4 @ 3.06 GHz
Graphic Card: ATI Radeon X800XL on PCI-e

lspci and dmesg output is as stated below. Thanks in advance

lspci output:
```
$ lspci
0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 915G/P/GV PCI Express Root Port (rev 04)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 554d
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 556d
0000:02:04.0 Communication controller: Intel Corp. 536EP Data Fax Modem
0000:02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

dmesg output:
```
$ dmesg

[4294669.465000] VFS: Disk quotas dquot_6.5.1
[4294669.465000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.466000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294669.466000] devfs: boot_options: 0x0
[4294669.466000] Initializing Cryptographic API
[4294669.466000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294669.466000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294669.466000] assign_interrupt_mode Found MSI capability
[4294669.466000] Allocate Port Service[pcie00]
[4294669.466000] Allocate Port Service[pcie03]
[4294669.466000] isapnp: Scanning for PnP cards...
[4294669.816000] isapnp: No Plug & Play device found
[4294669.835000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294669.837000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.838000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.838000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294669.838000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.838000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294669.840000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.840000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294669.840000] io scheduler noop registered
[4294669.840000] io scheduler anticipatory registered
[4294669.840000] io scheduler deadline registered
[4294669.840000] io scheduler cfq registered
[4294669.841000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.841000] EISA: Probing bus 0 at eisa.0
[4294669.841000] EISA: Detected 0 cards.
[4294669.841000] NET: Registered protocol family 2
[4294669.850000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294669.850000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[4294669.850000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.850000] TCP: Hash tables configured (established 131072 bind 65536)
[4294669.850000] NET: Registered protocol family 8
[4294669.850000] NET: Registered protocol family 20
[4294669.851000] ACPI wakeup devices:
[4294669.851000] PCI0 PEX0 PEX1 PEX2 PEX3 HUB0 UAR1 UAR2 USB0 USB1 USB2 USB3 USBE AC97 AZAL
[4294669.851000] ACPI: (supports S0 S3 S4 S5)
[4294669.851000] Freeing unused kernel memory: 224k freed
[4294669.866000] vga16fb: initializing
[4294669.866000] vga16fb: mapped to 0xc00a0000
[4294669.985000] Console: switching to colour frame buffer device 80x30
[4294669.985000] fb0: VGA16 VGA frame buffer device
[4294669.997000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294671.121000] Capability LSM initialized
[4294671.131000] NET: Registered protocol family 1
[4294671.144000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.144000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.144000] ACPI: bus type ide registered
[4294671.153000] SCSI subsystem initialized
[4294671.154000] libata version 1.11 loaded.
[4294671.155000] ahci version 1.00
[4294671.155000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[4294675.467000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294675.467000] ahci(0000:00:1f.2) AHCI 0001.0000 32 slots 4 ports 1.5 Gbps 0xf impl IDE mode
[4294675.467000] ahci(0000:00:1f.2) flags: 64bit ncq pm led slum part
[4294675.467000] ata1: SATA max UDMA/133 cmd 0xF886E100 ctl 0x0 bmdma 0x0 irq 19[4294675.467000] ata2: SATA max UDMA/133 cmd 0xF886E180 ctl 0x0 bmdma 0x0 irq 19[4294675.467000] ata3: SATA max UDMA/133 cmd 0xF886E200 ctl 0x0 bmdma 0x0 irq 19[4294675.467000] ata4: SATA max UDMA/133 cmd 0xF886E280 ctl 0x0 bmdma 0x0 irq 19[4294675.670000] ata1: dev 0 cfg 49:2f00 82:346b 83:7f61 84:4003 85:3468 86:3c41 87:4003 88:007f
[4294675.670000] ata1: dev 0 ATA, max UDMA/133, 312581808 sectors: lba48
[4294675.672000] ata1: dev 0 configured for UDMA/133
[4294675.672000] scsi0 : ahci
[4294675.873000] ata2: no device found (phy stat 00000000)
[4294675.873000] scsi1 : ahci
[4294676.074000] ata3: no device found (phy stat 00000000)
[4294676.074000] scsi2 : ahci
[4294676.275000] ata4: no device found (phy stat 00000000)
[4294676.275000] scsi3 : ahci
[4294676.275000]   Vendor: ATA       Model: WDC WD1600JD-00H  Rev: 08.0
[4294676.275000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294676.283000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[4294676.283000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[4294676.283000] ICH6: chipset revision 3
[4294676.283000] ICH6: not 100% native mode: will probe irqs later
[4294676.283000]     ide0: BM-DMA at 0xfb00-0xfb07, BIOS settings: hda:DMA, hdb:DMA
[4294676.283000]     ide1: BM-DMA at 0xfb08-0xfb0f, BIOS settings: hdc:pio, hdd:pio
[4294676.283000] Probing IDE interface ide0...
[4294676.955000] hda: SAMSUNG DVD-ROM SD-616Q, ATAPI CD/DVD-ROM drive
[4294677.669000] hdb: HL-DT-ST DVDRAM GMA-4020B, ATAPI CD/DVD-ROM drive
[4294677.720000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294677.720000] Probing IDE interface ide1...
[4294678.239000] Probing IDE interface ide1...
[4294678.757000] Probing IDE interface ide2...
[4294679.269000] Probing IDE interface ide3...
[4294679.781000] Probing IDE interface ide4...
[4294680.293000] Probing IDE interface ide5...
[4294680.809000] hda: ATAPI 48X DVD-ROM drive, 512kB Cache
[4294680.809000] Uniform CD-ROM driver Revision: 3.20
[4294680.813000] hdb: ATAPI 32X DVD-ROM DVD-R-RAM CD-R/RW drive, 1312kB Cache
[4294680.825000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[4294680.825000] SCSI device sda: drive cache: write back
[4294680.825000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[4294680.825000] SCSI device sda: drive cache: write back
[4294680.825000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 < p5 p6 >
[4294680.859000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4294681.236000] Attempting manual resume
[4294681.236000] swsusp: Suspend partition has wrong signature?
[4294681.262000] usbcore: registered new driver usbfs
[4294681.262000] usbcore: registered new driver hub
[4294681.263000] USB Universal Host Controller Interface driver v2.2
[4294681.263000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[4294681.263000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294681.263000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
[4294681.325000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294681.325000] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ff00
[4294681.325000] hub 1-0:1.0: USB hub found
[4294681.325000] hub 1-0:1.0: 2 ports detected
[4294681.328000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[4294681.328000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294681.328000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
[4294681.390000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294681.390000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fe00
[4294681.390000] hub 2-0:1.0: USB hub found
[4294681.390000] hub 2-0:1.0: 2 ports detected
[4294681.393000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4294681.393000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294681.393000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
[4294681.455000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294681.455000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fd00
[4294681.455000] hub 3-0:1.0: USB hub found
[4294681.455000] hub 3-0:1.0: 2 ports detected
[4294681.458000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[4294681.458000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294681.458000] uhci_hcd 0000:00:1d.3: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
[4294681.520000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294681.520000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fc00
[4294681.520000] hub 4-0:1.0: USB hub found
[4294681.520000] hub 4-0:1.0: 2 ports detected
[4294681.547000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[4294681.547000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294681.547000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
[4294681.547000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294681.548000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdfff000
[4294681.551000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[4294681.551000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294681.551000] hub 5-0:1.0: USB hub found
[4294681.552000] hub 5-0:1.0: 8 ports detected
[4294681.634000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294681.634000] 8139cp: pci dev 0000:02:06.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[4294681.634000] 8139cp: Try the "8139too" driver instead.
[4294681.635000] 8139too Fast Ethernet driver 0.9.27
[4294681.635000] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294681.636000] eth0: RealTek RTL8139 at 0xec00, 00:40:ca:87:90:45, IRQ 18
[4294681.636000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294684.224000] ACPI: Fan [FAN] (on)
[4294684.226000] ACPI: CPU0 (power states: C1[C1])
[4294684.227000] ACPI: Thermal Zone [THRM] (36 C)
[4294684.427000] Attempting manual resume
[4294684.427000] swsusp: Suspend partition has wrong signature?
[4294684.433000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294684.433000] EXT3-fs: write access will be enabled during recovery.
[4294685.354000] kjournald starting.  Commit interval 5 seconds
[4294685.354000] EXT3-fs: recovery complete.
[4294685.359000] EXT3-fs: mounted filesystem with ordered data mode.
[4294686.021000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294688.710000] Adding 1052216k swap on /dev/sda5.  Priority:-1 extents:1
[4294688.928000] EXT3 FS on sda2, internal journal
[4294693.250000] parport: PnPBIOS parport detected.
[4294693.250000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294693.334000] lp0: using parport0 (interrupt-driven).
[4294693.357000] mice: PS/2 mouse device common for all mice
[4294693.389000] ieee1394: Initialized config rom entry `ip1394'
[4294693.393000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294693.642000] input: ImExPS/2 Generic Explorer Mouse on isa0060/serio1
[4294694.241000] ts: Compaq touchscreen protocol output
[4294696.884000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294697.433000] cdrom: open failed.
[4294697.445000] cdrom: open failed.
[4294697.972000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4294697.995000] NTFS volume version 3.1.
[4294698.022000] NTFS volume version 3.1.
[4294699.040000] Linux agpgart interface v0.101 (c) Dave Jones
[4294699.047000] agpgart: Detected an Intel 915G Chipset.
[4294699.077000] agpgart: AGP aperture is 256M @ 0x0
[4294699.188000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294699.197000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294699.339000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294699.339000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[4294699.357000] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[4294699.447000] Unable to handle kernel NULL pointer dereference at virtual address 00000000
[4294699.447000]  printing eip:
[4294699.447000] f8ba15b1
[4294699.447000] *pde = 00000000
[4294699.447000] Oops: 0002 [#1]
[4294699.447000] Modules linked in: snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc shpchp pci_hotplug intel_agp agpgart nls_cp437 ntfs dm_mod tsdev evdev sr_mod sbp2 ieee1394 psmouse mousedev parport_pc lp parport md ext3 jbd thermal processor fan 8139too 8139cp mii ehci_hcd uhci_hcd usbcore sd_mod ide_cd cdrom ide_generic ata_piix ahci libata scsi_mod piix ide_core unix vesafb capability commoncap vga16fb vgastate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font bitblit
[4294699.447000] CPU:    0
[4294699.447000] EIP:    0060:[<f8ba15b1>]    Not tainted VLI
[4294699.447000] EFLAGS: 00010246   (2.6.12-9-386)
[4294699.447000] EIP is at alc880_auto_fill_dac_nids+0x39/0x92 [snd_hda_codec]
[4294699.447000] eax: 00000000   ebx: dfc7d148   ecx: 00000000   edx: fffffffe
[4294699.447000] esi: dfc7d000   edi: 00000000   ebp: dfdd8000   esp: f7e7be1c
[4294699.447000] ds: 007b   es: 007b   ss: 0068
[4294699.447000] Process modprobe (pid: 6879, threadinfo=f7e7a000 task=f7a80020)[4294699.447000] Stack: 00000000 00000000 00000000 00000000 dfc7d000 dfc7d148 00000006 f8ba19f0
[4294699.447000]        dfc7d000 dfc7d148 dfc7d000 dfdd8000 f8ba1b49 dfdd8000 dfdd8000 dfdd8000
[4294699.447000]        c1b1e900 00000000 f8b9e7a1 dfdd8000 00001007 c1b1e900 f8ba9b04 c1b1e900
[4294699.447000] Call Trace:
[4294699.447000]  [<f8ba19f0>] alc880_parse_auto_config+0x27/0xda [snd_hda_codec]
[4294699.447000]  [<f8ba1b49>] patch_alc880+0x82/0x1e7 [snd_hda_codec]
[4294699.447000]  [<f8b9e7a1>] snd_hda_codec_new+0x13f/0x18f [snd_hda_codec]
[4294699.447000]  [<f8aef698>] azx_codec_create+0x73/0xa1 [snd_hda_intel]
[4294699.447000]  [<f8aef0f2>] azx_send_cmd+0x0/0x60 [snd_hda_intel]
[4294699.447000]  [<f8aef1d5>] azx_get_response+0x0/0x5b [snd_hda_intel]
[4294699.447000]  [<f8af00f7>] azx_probe+0xdc/0x150 [snd_hda_intel]
[4294699.447000]  [<c01a2cdd>] pci_device_probe_static+0x2e/0x41
[4294699.447000]  [<c01a2d0f>] __pci_device_probe+0x1f/0x32
[4294699.447000]  [<c01a2d3e>] pci_device_probe+0x1c/0x31
[4294699.447000]  [<c01ebfe6>] driver_probe_device+0x36/0x54
[4294699.447000]  [<c01ec0be>] driver_attach+0x39/0x6a
[4294699.447000]  [<c01ec444>] bus_add_driver+0x5e/0x80
[4294699.447000]  [<c01ec7a5>] driver_register+0x23/0x25
[4294699.447000]  [<c01a2f01>] pci_register_driver+0x5f/0x72
[4294699.447000]  [<f8aa200a>] alsa_card_azx_init+0xa/0xc [snd_hda_intel]
[4294699.447000]  [<c0129682>] sys_init_module+0xb5/0x172
[4294699.447000]  [<c0102e9f>] sysenter_past_esp+0x54/0x75
[4294699.447000] Code: 74 24 20 8b 5c 24 24 89 e7 f3 ab 31 ff 3b 3b 7d 28 0f b7 54 7b 04 8d 42 ec 66 83 f8 03 77 17 0f b7 c2 8b 4e 3c 83 e8 14 8d 50 fe <66> 89 14 79 c7 04 84 01 00 00 00 47 eb d4 31 ff 8b 13 39 d7 7d
[4294699.447000]  <6>hw_random hardware driver 1.0.0 loaded
[4294716.702000] SysRq : Terminate All Tasks
[4294716.921000] ACPI: Power Button (FF) [PWRF]
[4294716.921000] ACPI: Power Button (CM) [PWRB]
[4294716.984000] ibm_acpi: ec object not found
[4294721.316000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294721.316000] apm: overridden by ACPI.
[4294721.642000] acpi-cpufreq: CPU0 - ACPI performance management activated.
[4294721.743000] Bluetooth: Core ver 2.7
[4294721.743000] NET: Registered protocol family 31
[4294721.743000] Bluetooth: HCI device and connection manager initialized
[4294721.743000] Bluetooth: HCI socket layer initialized
[4294721.763000] Bluetooth: L2CAP ver 2.7
[4294721.763000] Bluetooth: L2CAP socket layer initialized
[4294721.781000] Bluetooth: RFCOMM ver 1.5
[4294721.781000] Bluetooth: RFCOMM socket layer initialized
[4294721.781000] Bluetooth: RFCOMM TTY layer initialized
[4294729.662000] NET: Registered protocol family 10
[4294729.662000] Disabled Privacy Extensions on device c02eb280(lo)
[4294729.662000] IPv6 over IPv4 tunneling driver

```

---

### Post by munim on 2006-02-07
hey... i had the same problem and i solved it... does linux work with your onboard card enabled? if so... you can try what i did
[http://www.ubuntuforums.org/showpost.php?p=713502&postcount=7](http://www.ubuntuforums.org/showpost.php?p=713502&postcount=7)

---

### Post by Joh_ on 2006-02-10
I don't think we've got the same problem. Mine freezes at the hotplug initialization. I *can* bypass this by leaving this runlevel, and I'm writing from linux atm (without using on-board card). In other words, xorg isn't the problem.

The problem seems to be some module that won't work like it should, but I have no idea which one and how...

---

### Post by MartyAB on 2006-02-10
Hi. 

I have the same problem. It stops at hotplug initialization. Its very strange.

---

### Post by MartyAB on 2006-02-11
Im back. now i managed to go a little longer in the process. i turned off my integrated soundcard. but now it stopps at my ati x800gto and says that it can not load the grafix. please im total newbie in linux so are there any drivers and if so how do i load them?

---

### Post by arckeda on 2006-02-11
you guys sure you mean install it or do you mean when you boot it?

---

### Post by MartyAB on 2006-02-11
For me its when i boot.

---

### Post by Joh_ on 2006-03-09
As I said, it's when I boot. The install worked just fine.

---

### Post by mickeyren on 2006-03-09
anybody had a solution to this?

its happening to my computer now.

i have a shuttle computer(xpc), 3.2 giga, 1.5 ram, 6600 geforce card. 160 gb hd. 

please help thanks.

---

### Post by hebb on 2006-03-15
I'm having the same problem with my pci geforce 5200.  I'm currently running onboard to get around the hang.   How can I tell what module is failing?  This is a real pain as I have dual monitors and can't use them.

---

