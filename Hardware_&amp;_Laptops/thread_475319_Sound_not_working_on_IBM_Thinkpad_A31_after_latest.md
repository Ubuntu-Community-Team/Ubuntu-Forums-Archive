---
title: "Sound not working on IBM Thinkpad A31 after latest updates"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by darksider415 on 2007-06-16
The sound worked perfectly on my Thinkpad A31 when I first installed Kubuntu Feisty, but now that I've installed the latest updates, the sound has stopped working. Completely silent out of the speakers, and the headphone jack... I've tried every trick I know to get this up and now I turn to you, the good people of the Ubuntu forums..

Thanks in advance for any help you may give..

Below is the asoundconf and dmesg output..

```
bill@bill-laptop:~$ asoundconf list
Names of available sound cards:
I82801CAICH3
bill@bill-laptop:~$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d2000 size: 0000000000002000 end: 00000000000d4000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000002fe60000 end: 000000002ff60000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000002ff60000 size: 000000000001a000 end: 000000002ff7a000 type: 3
[    0.000000] copy_e820_map() start: 000000002ff7a000 size: 0000000000002000 end: 000000002ff7c000 type: 4
[    0.000000] copy_e820_map() start: 000000002ff7c000 size: 0000000000084000 end: 0000000030000000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff800000 size: 0000000000800000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002ff60000 (usable)
[    0.000000]  BIOS-e820: 000000002ff60000 - 000000002ff7a000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002ff7a000 - 000000002ff7c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002ff7c000 - 0000000030000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 196448) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196448
[    0.000000]   HighMem    196448 ->   196448
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196448
[    0.000000] On node 0 totalpages: 196448
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1502 pages used for memmap
[    0.000000]   Normal zone: 190850 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v002 IBM                                   ) @ 0x000f7070
[    0.000000] ACPI: XSDT (v001 IBM    TP-1G    0x00001020  LTP 0x00000000) @ 0x2ff6ee43
[    0.000000] ACPI: FADT (v001 IBM    TP-1G    0x00001020 IBM  0x00000001) @ 0x2ff6ee87
[    0.000000] ACPI: SSDT (v001 IBM    TP-1G    0x00001020 MSFT 0x0100000d) @ 0x2ff6ef3b
[    0.000000] ACPI: ECDT (v001 IBM    TP-1G    0x00001020 IBM  0x00000001) @ 0x2ff79f87
[    0.000000] ACPI: BOOT (v001 IBM    TP-1G    0x00001020  LTP 0x00000001) @ 0x2ff79fd8
[    0.000000] ACPI: DSDT (v001 IBM    TP-1G    0x00001020 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cf800000)
[    0.000000] Detected 1598.701 MHz processor.
[    2.559113] Built 1 zonelists.  Total pages: 194914
[    2.559121] Kernel command line: root=UUID=184a60cb-896a-46db-8e41-6cfe6edb59aa ro quiet splash
[    2.559396] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    2.559409] mapped APIC to ffffd000 (0160c000)
[    2.559414] Enabling fast FPU save and restore... done.
[    2.559421] Enabling unmasked SIMD FPU exception support... done.
[    2.559438] Initializing CPU#0
[    2.559543] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    2.561102] Console: colour VGA+ 80x25
[    2.562057] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    2.563024] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    2.594981] Memory: 767800k/785792k available (1992k kernel code, 17416k reserved, 900k data, 328k init, 0k highmem)
[    2.594997] virtual kernel memory layout:
[    2.594999]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    2.595001]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    2.595003]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[    2.595004]     lowmem  : 0xc0000000 - 0xeff60000   ( 767 MB)
[    2.595006]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    2.595008]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[    2.595009]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[    2.595014] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    2.671462] Calibrating delay using timer specific routine.. 3200.96 BogoMIPS (lpj=6401928)
[    2.671534] Security Framework v1.0.0 initialized
[    2.671545] SELinux:  Disabled at boot.
[    2.671574] Mount-cache hash table entries: 512
[    2.671815] CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[    2.671835] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    2.671839] CPU: L2 cache: 512K
[    2.671843] CPU: Hyper-Threading is disabled
[    2.671846] CPU: After all inits, caps: 3febf9ff 00000000 00000000 00003080 00000000 00000000 00000000
[    2.671864] Compat vDSO mapped to ffffe000.
[    2.671870] Remapping vsyscall page to ffffe000
[    2.671889] Checking 'hlt' instruction... OK.
[    2.687665] SMP alternatives: switching to UP code
[    2.688016] Freeing SMP alternatives: 11k freed
[    2.688386] Early unpacking initramfs... done
[    3.195013] ACPI: Core revision 20060707
[    3.195306] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    3.202583] ACPI: setting ELCR to 0200 (from 0800)
[    3.213682] CPU0: Intel(R) Pentium(R) 4 Mobile CPU 1.60GHz stepping 04
[    3.213691] SMP motherboard not detected.
[    3.213696] Local APIC not detected. Using dummy APIC emulation.
[    3.213760] Brought up 1 CPUs
[    3.214177] Booting paravirtualized kernel on bare hardware
[    3.214271] Time: 22:43:34  Date: 05/15/107
[    3.214319] NET: Registered protocol family 16
[    3.214470] EISA bus registered
[    3.214478] ACPI: bus type pci registered
[    3.214568] PCI: PCI BIOS revision 2.10 entry at 0xfd8fe, last bus=8
[    3.214572] PCI: Using configuration type 1
[    3.214575] Setting up standard PCI resources
[    3.219304] ACPI Exception (acpi_ec-0908): AE_NOT_FOUND, Could not use ECDT [20060707]
[    3.225976] ACPI Error (evregion-0317): No handler for Region [ECOR] (eedad754) [EmbeddedControl] [20060707]
[    3.225986] ACPI Error (exfldio-0290): Region EmbeddedControl(3) has no handler [20060707]
[    3.225995] ACPI Exception (dswexec-0458): AE_NOT_EXIST, While resolving operands for [OpcodeName unavailable] [20060707]
[    3.226005] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC_.FDC_._INI] (Node eedbbedc), AE_NOT_EXIST
[    3.226109] ACPI Error (evregion-0317): No handler for Region [ECOR] (eedad754) [EmbeddedControl] [20060707]
[    3.226118] ACPI Error (exfldio-0290): Region EmbeddedControl(3) has no handler [20060707]
[    3.226127] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC_.EC__._INI] (Node eedb7ba8), AE_NOT_EXIST
[    3.227698] ACPI: Interpreter enabled
[    3.227703] ACPI: Using PIC for interrupt routing
[    3.228891] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    3.229734] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    3.230581] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    3.231441] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    3.232281] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    3.233047] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    3.233814] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    3.234580] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    3.235232] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    3.235240] PCI: Probing PCI hardware (bus 00)
[    3.237390] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    3.237397] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[    3.237792] Boot video device is 0000:01:00.0
[    3.238014] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[    3.238114] PCI: Transparent bridge - 0000:00:1e.0
[    3.238307] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    3.245081] ACPI: Power Resource [PUBS] (on)
[    3.246306] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    3.246748] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    3.251198] Linux Plug and Play Support v0.97 (c) Adam Belay
[    3.251220] pnp: PnP ACPI init
[    3.258244] pnp: PnP ACPI: found 13 devices
[    3.258252] PnPBIOS: Disabled by ACPI PNP
[    3.258344] PCI: Using ACPI for IRQ routing
[    3.258349] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    3.272156] NET: Registered protocol family 8
[    3.272160] NET: Registered protocol family 20
[    3.273500] PCI: Bridge: 0000:00:01.0
[    3.273505]   IO window: 3000-3fff
[    3.273512]   MEM window: d0100000-d01fffff
[    3.273519]   PREFETCH window: e8000000-efffffff
[    3.273534] PCI: Bus 3, cardbus bridge: 0000:02:00.0
[    3.273538]   IO window: 00004000-000040ff
[    3.273545]   IO window: 00004400-000044ff
[    3.273552]   PREFETCH window: f0000000-f3ffffff
[    3.273560]   MEM window: d4000000-d7ffffff
[    3.273567] PCI: Bus 7, cardbus bridge: 0000:02:00.1
[    3.273572]   IO window: 00004800-000048ff
[    3.273578]   IO window: 00004c00-00004cff
[    3.273585]   PREFETCH window: f4000000-f7ffffff
[    3.273592]   MEM window: d8000000-dbffffff
[    3.273599] PCI: Bridge: 0000:00:1e.0
[    3.273605]   IO window: 4000-8fff
[    3.273614]   MEM window: d0200000-dfffffff
[    3.273621]   PREFETCH window: f0000000-f7ffffff
[    3.273647] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    3.274298] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    3.274304] PCI: setting IRQ 11 as level-triggered
[    3.274309] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.274924] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    3.274929] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    3.274999] NET: Registered protocol family 2
[    3.315078] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    3.315397] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    3.316883] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    3.317845] TCP: Hash tables configured (established 131072 bind 65536)
[    3.317853] TCP reno registered
[    3.327202] checking if image is initramfs... it is
[    4.326203] Freeing initrd memory: 6768k freed
[    4.326515] Simple Boot Flag at 0x35 set to 0x1
[    4.326811] audit: initializing netlink socket (disabled)
[    4.326832] audit(1181947415.944:1): initialized
[    4.327053] VFS: Disk quotas dquot_6.5.1
[    4.327085] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    4.327165] io scheduler noop registered
[    4.327170] io scheduler anticipatory registered
[    4.327174] io scheduler deadline registered
[    4.327187] io scheduler cfq registered (default)
[    4.327595] isapnp: Scanning for PnP cards...
[    4.680976] isapnp: No Plug & Play device found
[    4.727502] Real Time Clock Driver v1.12ac
[    4.727587] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    4.729514] pnp: Device 00:0a activated.
[    4.729778] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    4.730264] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    4.730280] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[    4.730393] mice: PS/2 mouse device common for all mice
[    4.731331] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    4.731729] input: Macintosh mouse button emulation as /class/input/input0
[    4.731791] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    4.731797] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    4.732085] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    4.740535] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.740545] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.740800] EISA: Probing bus 0 at eisa.0
[    4.740811] Cannot allocate resource for EISA slot 1
[    4.740815] Cannot allocate resource for EISA slot 2
[    4.740819] Cannot allocate resource for EISA slot 3
[    4.740822] Cannot allocate resource for EISA slot 4
[    4.740826] Cannot allocate resource for EISA slot 5
[    4.740829] Cannot allocate resource for EISA slot 6
[    4.740832] Cannot allocate resource for EISA slot 7
[    4.740836] Cannot allocate resource for EISA slot 8
[    4.740838] EISA: Detected 0 cards.
[    4.770968] TCP cubic registered
[    4.770979] NET: Registered protocol family 1
[    4.771018] Using IPI No-Shortcut mode
[    4.771123] ACPI: (supports S0 S3 S4 S5)
[    4.771198]   Magic number: 11:146:755
[    4.771949] Freeing unused kernel memory: 328k freed
[    4.773797] Time: tsc clocksource has been installed.
[    4.774063] input: AT Translated Set 2 keyboard as /class/input/input1
[    6.120216] Capability LSM initialized
[    6.917850] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    6.917861] ACPI: Processor [CPU] (supports 8 throttling states)
[    6.920612] ACPI: Thermal Zone [THM0] (46 C)
[    7.851788] usbcore: registered new interface driver usbfs
[    7.851828] usbcore: registered new interface driver hub
[    7.851868] usbcore: registered new device driver usb
[    7.853504] USB Universal Host Controller Interface driver v3.0
[    7.853583] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    7.853602] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    7.853608] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    7.853820] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    7.853854] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[    7.854030] usb usb1: configuration #1 chosen from 1 choice
[    7.854074] hub 1-0:1.0: USB hub found
[    7.854088] hub 1-0:1.0: 2 ports detected
[    7.926371] SCSI subsystem initialized
[    7.936691] libata version 2.20 loaded.
[    7.956186] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    7.956193] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    7.956211] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    7.956217] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    7.956257] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    7.956288] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[    7.956451] usb usb2: configuration #1 chosen from 1 choice
[    7.956500] hub 2-0:1.0: USB hub found
[    7.956513] hub 2-0:1.0: 2 ports detected
[    8.023271] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[    8.023278] e100: Copyright(c) 1999-2006 Intel Corporation
[    8.060107] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    8.060114] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    8.060134] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    8.060140] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    8.060181] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    8.060213] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[    8.060372] usb usb3: configuration #1 chosen from 1 choice
[    8.060415] hub 3-0:1.0: USB hub found
[    8.060427] hub 3-0:1.0: 2 ports detected
[    8.184951] Floppy drive(s): fd0 is 1.44M
[    8.223677] ata_piix 0000:00:1f.1: version 2.10ac1
[    8.223700] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    8.223717] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    8.223748] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    8.223827] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
[    8.223870] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
[    8.223907] scsi0 : ata_piix
[    8.239467] FDC 0 is a National Semiconductor PC87306
[    5.804000] Time: acpi_pm clocksource has been installed.
[    5.988000] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[    5.988000] ata1.00: ATA-6: ST9160821A, 3.ALD, max UDMA/100
[    5.988000] ata1.00: 312581808 sectors, multi 16: LBA48
[    5.988000] ata1.01: ATAPI, max UDMA/33
[    5.996000] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[    5.996000] ata1.00: configured for UDMA/100
[    6.160000] ata1.01: configured for UDMA/33
[    6.160000] scsi1 : ata_piix
[    6.480000] ata2.00: ATAPI, max UDMA/33
[    6.644000] ata2.00: configured for UDMA/33
[    6.644000] scsi 0:0:0:0: Direct-Access     ATA      ST9160821A       3.AL PQ: 0 ANSI: 5
[    6.648000] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVD-RW GWA-4082N CS01 PQ: 0 ANSI: 5
[    6.648000] scsi 1:0:0:0: CD-ROM            _NEC     DVD+RW ND-6100A  1.N1 PQ: 0 ANSI: 5
[    6.656000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    6.656000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[    6.680000] e100: eth0: e100_probe: addr 0xd0200000, irq 11, MAC addr 00:D0:59:CD:65:4C
[    6.716000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[    6.716000] sda: Write Protect is off
[    6.716000] sda: Mode Sense: 00 3a 00 00
[    6.716000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.716000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[    6.716000] sda: Write Protect is off
[    6.716000] sda: Mode Sense: 00 3a 00 00
[    6.716000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.716000]  sda: sda1 sda2 sda3 sda4
[    6.788000] sd 0:0:0:0: Attached scsi disk sda
[    6.796000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.796000] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    6.796000] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[    6.804000] sr0: scsi3-mmc drive: 62x/62x writer cd/rw xa/form2 cdda tray
[    6.804000] Uniform CD-ROM driver Revision: 3.20
[    6.804000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    6.804000] sr1: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    6.804000] sr 1:0:0:0: Attached scsi CD-ROM sr1
[    7.208000] Attempting manual resume
[    7.208000] swsusp: Resume From Partition 8:3
[    7.208000] PM: Checking swsusp image.
[    7.208000] PM: Resume from disk failed.
[    7.224000] ReiserFS: sda4: found reiserfs format "3.6" with standard journal
[    7.224000] ReiserFS: sda4: using ordered data mode
[    7.232000] ReiserFS: sda4: journal params: device sda4, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    7.232000] ReiserFS: sda4: checking transaction log (sda4)
[    7.284000] ReiserFS: sda4: Using r5 hash to sort names
[   19.740000] NET: Registered protocol family 17
[   20.716000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   20.772000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.964000] intel_rng: FWH not detected
[   21.016000] iTCO_vendor_support: vendor-support=0
[   21.016000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   21.016000] iTCO_wdt: Found a ICH3-M TCO device (Version=1, TCOBASE=0x1060)
[   21.016000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   21.140000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.180000] agpgart: Detected an Intel i845 Chipset.
[   21.184000] agpgart: AGP aperture is 64M @ 0xe0000000
[   22.020000] Yenta: CardBus bridge found at 0000:02:00.0 [1014:0185]
[   22.256000] input: PC Speaker as /class/input/input2
[   22.328000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   22.328000] Socket status: 30000820
[   22.328000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   22.328000] cs: IO port probe 0x4000-0x8fff: clean.
[   22.332000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xdfffffff
[   22.332000] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf7ffffff
[   22.332000] Yenta: CardBus bridge found at 0000:02:00.1 [1014:0185]
[   22.332000] parport: PnPBIOS parport detected.
[   22.332000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   22.460000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[   22.460000] Socket status: 30000006
[   22.460000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   22.460000] cs: IO port probe 0x4000-0x8fff: clean.
[   22.464000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xdfffffff
[   22.464000] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf7ffffff
[   22.464000] irda_init()
[   22.464000] NET: Registered protocol family 23
[   22.736000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   22.756000] input: TPPS/2 IBM TrackPoint as /class/input/input3
[   22.772000] pnp: Device 00:0c activated.
[   22.772000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   22.772000] nsc-ircc, chip->init
[   22.772000] nsc-ircc, Found chip at base=0x02e
[   22.772000] nsc-ircc, driver loaded (Dag Brattli)
[   22.772000] IrDA: Registered device irda0
[   22.772000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   22.932000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   22.932000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   22.968000] pccard: CardBus card inserted into slot 0
[   23.044000] ath_hal: module license 'Proprietary' taints kernel.
[   23.044000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   23.204000] wlan: 0.8.4.2 (0.9.3)
[   23.236000] ath_pci: 0.9.4.5 (0.9.3)
[   23.296000] cs: IO port probe 0x100-0x3af: clean.
[   23.296000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   23.296000] cs: IO port probe 0x820-0x8ff: clean.
[   23.296000] cs: IO port probe 0xc00-0xcf7: clean.
[   23.300000] cs: IO port probe 0xa00-0xaff: clean.
[   23.312000] cs: IO port probe 0x100-0x3af: clean.
[   23.312000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   23.312000] cs: IO port probe 0x820-0x8ff: clean.
[   23.316000] cs: IO port probe 0xc00-0xcf7: clean.
[   23.316000] cs: IO port probe 0xa00-0xaff: clean.
[   23.504000] intel8x0_measure_ac97_clock: measured 55206 usecs
[   23.504000] intel8x0: clocking to 48000
[   23.508000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[   23.508000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   24.136000] ath_rate_sample: 1.2 (0.9.3)
[   24.136000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   24.136000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   24.136000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   24.136000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   24.136000] wifi0: mac 7.9 phy 4.5 radio 5.6
[   24.136000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   24.136000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   24.136000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   24.136000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   24.136000] wifi0: Use hw queue 8 for CAB traffic
[   24.136000] wifi0: Use hw queue 9 for beacons
[   24.216000] wifi0: Atheros 5212: mem=0xd4000000, irq=11
[   24.496000] fuse init (API version 7.8)
[   24.544000] lp0: using parport0 (interrupt-driven).
[   24.596000] Adding 1502068k swap on /dev/disk/by-uuid/c1986939-89eb-4fbf-a8ec-c48f6115b314.  Priority:-1 extents:1 across:1502068k
[   37.292000] NET: Registered protocol family 10
[   37.292000] lo: Disabled Privacy Extensions
[   37.292000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.544000] kjournald starting.  Commit interval 5 seconds
[   37.544000] EXT3 FS on sda2, internal journal
[   37.544000] EXT3-fs: mounted filesystem with ordered data mode.
[   37.604000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   37.680000] NTFS volume version 3.1.
[   42.556000] ACPI: Battery Slot [BAT0] (battery present)
[   42.580000] ACPI: AC Adapter [AC] (on-line)
[   42.660000] input: Power Button (FF) as /class/input/input4
[   42.664000] ACPI: Power Button (FF) [PWRF]
[   42.716000] input: Lid Switch as /class/input/input5
[   42.724000] ACPI: Lid Switch [LID]
[   42.772000] input: Sleep Button (CM) as /class/input/input6
[   42.772000] ACPI: Sleep Button (CM) [SLPB]
[   47.448000] ath0: no IPv6 routers present
[   48.428000] cdrom: This disc doesn't have any tracks I recognize!
[   52.068000] ppdev: user-space parallel port driver
[   52.968000] IBM machine detected. Enabling interrupts during APM calls.
[   52.968000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   52.968000] apm: overridden by ACPI.
[   53.144000] Non-volatile memory driver v1.2
[   53.172000] input: /usr/sbin/thinkpad-keys as /class/input/input7
[   53.964000] Bluetooth: Core ver 2.11
[   53.964000] NET: Registered protocol family 31
[   53.964000] Bluetooth: HCI device and connection manager initialized
[   53.964000] Bluetooth: HCI socket layer initialized
[   54.032000] Bluetooth: L2CAP ver 2.8
[   54.032000] Bluetooth: L2CAP socket layer initialized
[   54.132000] Bluetooth: RFCOMM socket layer initialized
[   54.132000] Bluetooth: RFCOMM TTY layer initialized
[   54.132000] Bluetooth: RFCOMM ver 1.8
[   56.132000] [drm] Initialized drm 1.1.0 20060810
[   56.144000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   56.148000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   57.728000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   57.728000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   57.728000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[   58.000000] [drm] Setting GART location based on new memory map
[   58.000000] [drm] writeback test succeeded in 1 usecs
[  101.368000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  119.524000] ath0: no IPv6 routers present
bill@bill-laptop:~$

```

---

