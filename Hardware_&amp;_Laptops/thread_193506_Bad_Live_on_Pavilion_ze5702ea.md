---
title: "Bad Live on Pavilion ze5702ea"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by mpalla on 2006-06-10
Hi everybody!

This is my very first post in this forum, although I've been an ubuntu user since a couple of years.
Right now I have Ubuntu Breezy installed in dual-boot with Windows XP on my laptop, a [Pavilion ze5702ea]("http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&cc=it&dlc=it&product=414532&rule=28948&"), and although the actual install is a little "screwed up", I've never run into serious problem.

Now, I'd like to clean up my laptop and install Dapper as the only OS, and then configure everything in detail, and maybe then write a tutorial for my laptop. So the first step is: [COLOR="Red"]**run the live and check if there are any hardware problems.**[/COLOR]

And, unfortunately, it seems that there are...

The system seems to work, but there are a lot of bad messages at the startup, maybe someone out there can help me sort it out.

From the startup screen:

```
 * Loading hardware drivers...
[COLOR="Red"][4294854.135000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[4294854.135000] ali mixer 1 creating error.
[4294854.644000] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized -
upgrade BIOS or use force_addr=0xaddr
[4294854.644000] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not in
serted.
                                                                         [ ok ]
^[[M [/COLOR]* Starting PCMCIA services...                                       [ ok ]
 * Loading manual drivers...                                             [ ok ]
[COLOR="Red"]mount: Function not implemented[/COLOR]
 * Starting RAID devices...                                              [ ok ]
 * Setting up LVM Volume Groups...                                       [ ok ]
 * Starting Enterprise Volume Management System...                       [ ok ]
 * Checking all filesystems...                                           [ ok ]
 * Configuring network interfaces...                                     [ ok ]
 * INIT: Entering runlevel: 2
[COLOR="Red"]cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
cat: /var/lib/acpi-support/system-product-name: No such file or directory
cat: /var/lib/acpi-support/system-version: No such file or directory
cat: /var/lib/acpi-support/bios-version: No such file or directory[/COLOR]
 * Saving VESA state...                                                  [ ok ]
```

I think that the message about the ali mixer are quite harmless and also present in Breezy, but the ali15x3, mount and acpi messages are scary :shock:

Ok, let's see the dmesg output:

```
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[4294667.296000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000d8000 - 00000000000e0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000002bf70000 (usable)
[4294667.296000]  BIOS-e820: 000000002bf70000 - 000000002bf7c000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000002bf7c000 - 000000002bf80000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000002bf80000 - 000000002c000000 (reserved)
[4294667.296000]  BIOS-e820: 000000003bf80000 - 000000003c000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 703MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 180080
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 175984 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ATI board detected. Disabling timer routing over 8254.
[4294667.296000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6ab0
[4294667.296000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x2bf7529b
[4294667.296000] ACPI: FADT (v001 ATI    Salmon   0x06040000 ATI  0x000f4240) @ 0x2bf7bf64
[4294667.296000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x2bf7bfd8
[4294667.296000] ACPI: DSDT (v001    ATI MS2_1535 0x06040000 MSFT 0x0100000e) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x8008
[4294667.296000] Allocating PCI resources starting at 40000000 (gap: 3c000000:c3f80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- kbd-chooser/method=it
[4294667.296000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01582000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[4294667.296000] Detected 2791.560 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294667.398000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294667.401000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294667.442000] Memory: 703156k/720320k available (1976k kernel code, 16596k reserved, 606k data, 288k init, 0k highmem)
[4294667.442000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294667.503000] Calibrating delay using timer specific routine.. 5588.23 BogoMIPS (lpj=2794117)
[4294667.503000] Security Framework v1.0.0 initialized
[4294667.503000] SELinux:  Disabled at boot.
[4294667.503000] Mount-cache hash table entries: 512
[4294667.503000] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[4294667.503000] CPU: After vendor identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[4294667.503000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[4294667.503000] CPU: L2 cache: 128K
[4294667.503000] CPU: After all inits, caps: bfebf9ff 00000000 00000000 00000080 00004400 00000000 00000000
[4294667.503000] mtrr: v2.0 (20020519)
[4294667.503000] CPU: Intel(R) Celeron(R) CPU 2.80GHz stepping 09
[4294667.503000] Enabling fast FPU save and restore... done.
[4294667.503000] Enabling unmasked SIMD FPU exception support... done.
[4294667.503000] Checking 'hlt' instruction... OK.
[4294667.507000] checking if image is initramfs... it is
[4294668.637000] Freeing initrd memory: 6838k freed
[4294668.695000] ACPI: Looking for DSDT ... not found!
[4294668.700000] ACPI: setting ELCR to 0200 (from 0420)
[4294668.704000] NET: Registered protocol family 16
[4294668.704000] EISA bus registered
[4294668.704000] ACPI: bus type pci registered
[4294668.738000] PCI: PCI BIOS revision 2.10 entry at 0xfd89b, last bus=2
[4294668.738000] PCI: Using configuration type 1
[4294668.739000] ACPI: Subsystem revision 20051216
[4294668.805000] ACPI: Interpreter enabled
[4294668.805000] ACPI: Using PIC for interrupt routing
[4294668.806000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.806000] PCI: Probing PCI hardware (bus 00)
[4294668.810000] PCI quirk: region 8000-803f claimed by ali7101 ACPI
[4294668.810000] PCI quirk: region 8040-805f claimed by ali7101 SMB
[4294668.810000] Boot video device is 0000:01:05.0
[4294668.810000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.813000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[4294668.816000] ACPI: PCI Interrupt Link [LNK0] (IRQs 7 10) *0, disabled.
[4294668.817000] ACPI: PCI Interrupt Link [LNK1] (IRQs 7 *10)
[4294668.817000] ACPI: PCI Interrupt Link [LNK2] (IRQs 7 *10)
[4294668.818000] ACPI: PCI Interrupt Link [LNK3] (IRQs 7 *10)
[4294668.819000] ACPI: PCI Interrupt Link [LNK4] (IRQs 7 10) *0, disabled.
[4294668.819000] ACPI: PCI Interrupt Link [LNK5] (IRQs 7 *11)
[4294668.820000] ACPI: PCI Interrupt Link [LNK6] (IRQs 7 10) *0, disabled.
[4294668.820000] ACPI: PCI Interrupt Link [LNK7] (IRQs *5)
[4294668.821000] ACPI: PCI Interrupt Link [LNK8] (IRQs 7 10) *0, disabled.
[4294668.825000] ACPI: Embedded Controller [EC0] (gpe 24) interrupt mode.
[4294668.830000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.830000] pnp: PnP ACPI init
[4294668.835000] pnp: PnP ACPI: found 11 devices
[4294668.835000] PnPBIOS: Disabled by ACPI PNP
[4294668.835000] PCI: Using ACPI for IRQ routing
[4294668.835000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.838000] pnp: 00:06: ioport range 0x40b-0x40b has been reserved
[4294668.838000] pnp: 00:06: ioport range 0x480-0x48f has been reserved
[4294668.838000] pnp: 00:06: ioport range 0x4d0-0x4d1 has been reserved
[4294668.838000] pnp: 00:06: ioport range 0x4d6-0x4d6 has been reserved
[4294668.838000] pnp: 00:06: ioport range 0x8000-0x807f could not be reserved
[4294668.839000] PCI: Bridge: 0000:00:01.0
[4294668.839000]   IO window: 9000-9fff
[4294668.839000]   MEM window: d0300000-d03fffff
[4294668.839000]   PREFETCH window: d8000000-dfffffff
[4294668.839000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[4294668.839000]   IO window: 00001800-000018ff
[4294668.839000]   IO window: 00001c00-00001cff
[4294668.839000]   PREFETCH window: 40000000-41ffffff
[4294668.839000]   MEM window: 42000000-43ffffff
[4294668.839000] PCI: Enabling device 0000:00:0a.0 (0005 -> 0007)
[COLOR="Red"][4294668.839000] **** SET: Misaligned resource pointer: dfe1e5c2 Type 07 Len 0[/COLOR]
[4294668.840000] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 11
[4294668.840000] PCI: setting IRQ 11 as level-triggered
[4294668.840000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[4294668.840000] Simple Boot Flag at 0x37 set to 0x1
[4294668.841000] audit: initializing netlink socket (disabled)
[4294668.841000] audit(1149927854.840:1): initialized
[4294668.842000] VFS: Disk quotas dquot_6.5.1
[4294668.842000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.842000] Initializing Cryptographic API
[4294668.842000] io scheduler noop registered
[4294668.842000] io scheduler anticipatory registered
[4294668.842000] io scheduler deadline registered
[4294668.842000] io scheduler cfq registered
[4294668.842000] Activating ISA DMA hang workarounds.
[4294668.842000] isapnp: Scanning for PnP cards...
[4294669.200000] isapnp: No Plug & Play device found
[4294669.287000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[4294669.291000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.291000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.291000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294669.303000] PCI: Enabling device 0000:00:08.0 (0000 -> 0003)
[COLOR="red"][4294669.303000] **** SET: Misaligned resource pointer: dfee11c2 Type 07 Len 0[/COLOR]
[4294669.304000] ACPI: PCI Interrupt Link [LNK6] enabled at IRQ 10
[4294669.304000] PCI: setting IRQ 10 as level-triggered
[4294669.304000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNK6] -> GSI 10 (level, low) -> IRQ 10
[4294669.308000] 0000:00:08.0: ttyS9 at I/O 0x1428 (irq = 10) is a 8250
[4294669.309000] 0000:00:08.0: ttyS12 at I/O 0x1440 (irq = 10) is a 8250
[4294669.311000] 0000:00:08.0: ttyS14 at I/O 0x1450 (irq = 10) is a 8250
[4294669.312000] 0000:00:08.0: ttyS16 at I/O 0x1460 (irq = 10) is a 8250
[4294669.313000] 0000:00:08.0: ttyS18 at I/O 0x1470 (irq = 10) is a 8250
[4294669.326000] RAMDISK driver initialized: 16 RAM disks of 1048576K size 1024 blocksize
[4294669.326000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294669.326000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294669.327000] mice: PS/2 mouse device common for all mice
[4294669.330000] EISA: Probing bus 0 at eisa.0
[4294669.330000] Cannot allocate resource for EISA slot 1
[4294669.330000] Cannot allocate resource for EISA slot 2
[4294669.330000] Cannot allocate resource for EISA slot 8
[4294669.330000] EISA: Detected 0 cards.
[4294669.330000] NET: Registered protocol family 2
[4294669.340000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294669.340000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[4294669.341000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.342000] TCP: Hash tables configured (established 131072 bind 65536)
[4294669.342000] TCP reno registered
[4294669.342000] TCP bic registered
[4294669.342000] NET: Registered protocol family 1
[4294669.342000] NET: Registered protocol family 8
[4294669.342000] NET: Registered protocol family 20
[4294669.342000] Using IPI Shortcut mode
[4294669.342000] ACPI wakeup devices: 
[4294669.342000] PCI0 MDEM  LAN  LID 
[4294669.342000] ACPI: (supports S0 S3 S4 S5)
[4294669.342000] Freeing unused kernel memory: 288k freed
[4294669.369000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294669.433000] vga16fb: initializing
[4294669.433000] vga16fb: mapped to 0xc00a0000
[4294669.560000] Console: switching to colour frame buffer device 80x25
[4294669.560000] fb0: VGA16 VGA frame buffer device
[4294670.594000] Capability LSM initialized
[4294670.759000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294670.762000] ACPI: Thermal Zone [THRM] (33 C)
[4294672.040000] ALI15X3: IDE controller at PCI slot 0000:00:10.0
[4294672.040000] ACPI: PCI Interrupt 0000:00:10.0[A]: no GSI
[4294672.040000] ALI15X3: chipset revision 196
[4294672.040000] ALI15X3: not 100% native mode: will probe irqs later
[4294672.040000]     ide0: BM-DMA at 0x2040-0x2047, BIOS settings: hda:DMA, hdb:pio
[4294672.040000]     ide1: BM-DMA at 0x2048-0x204f, BIOS settings: hdc:pio, hdd:pio
[4294672.040000] Probing IDE interface ide0...
[4294672.304000] hda: ST93015A, ATA DISK drive
[4294672.922000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294673.528000] Probing IDE interface ide1...
[4294674.200000] hdc: SD-R6252, ATAPI CD/DVD-ROM drive
[4294674.812000] ide1 at 0x170-0x177,0x376 on irq 15
[4294674.838000] hda: max request size: 128KiB
[4294674.860000] hda: 58605120 sectors (30005 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[4294674.863000] hda: cache flushes supported
[4294674.863000]  hda: hda1 hda2 < hda5 hda6 > hda3
[4294675.198000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[4294675.198000] Uniform CD-ROM driver Revision: 3.20
[4294675.678000] usbcore: registered new driver usbfs
[4294675.679000] usbcore: registered new driver hub
[4294675.682000] USB Universal Host Controller Interface driver v2.3
[COLOR="red"][4294675.682000] **** SET: Misaligned resource pointer: dfcc5402 Type 07 Len 0[/COLOR]
[4294675.682000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 10
[4294675.682000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
[4294675.682000] uhci_hcd 0000:00:0b.0: UHCI Host Controller
[4294675.683000] uhci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[4294675.683000] uhci_hcd 0000:00:0b.0: irq 10, io base 0x00002000
[4294675.683000] hub 1-0:1.0: USB hub found
[4294675.683000] hub 1-0:1.0: 2 ports detected
[COLOR="red"][4294675.784000] **** SET: Misaligned resource pointer: dfcc5102 Type 07 Len 0[/COLOR]
[4294675.784000] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 10
[4294675.784000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LNK3] -> GSI 10 (level, low) -> IRQ 10
[4294675.784000] uhci_hcd 0000:00:0b.1: UHCI Host Controller
[4294675.785000] uhci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[4294675.785000] uhci_hcd 0000:00:0b.1: irq 10, io base 0x00002020
[4294675.786000] hub 2-0:1.0: USB hub found
[4294675.786000] hub 2-0:1.0: 2 ports detected
[4294675.890000] PCI: Enabling device 0000:00:0b.2 (0010 -> 0012)
[4294675.890000] ACPI: PCI Interrupt 0000:00:0b.2[C] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[4294675.890000] PCI: Via IRQ fixup for 0000:00:0b.2, from 255 to 11
[4294675.890000] ehci_hcd 0000:00:0b.2: EHCI Host Controller
[4294675.891000] ehci_hcd 0000:00:0b.2: new USB bus registered, assigned bus number 3
[4294675.891000] ehci_hcd 0000:00:0b.2: irq 11, io mem 0xd0003000
[4294675.891000] ehci_hcd 0000:00:0b.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[4294675.891000] hub 3-0:1.0: USB hub found
[4294675.891000] hub 3-0:1.0: 4 ports detected
[4294676.593000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[4294676.762000] usbcore: registered new driver hiddev
[4294676.786000] input: PS/2+USB Mouse as /class/input/input1
[4294676.787000] input: USB HID v1.10 Mouse [PS/2+USB Mouse] on usb-0000:00:0b.1-1
[4294676.787000] usbcore: registered new driver usbhid
[4294676.787000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[COLOR="red"][4294677.908000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294677.908000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[4294677.908000] ide: failed opcode was: unknown
[4294677.908000] end_request: I/O error, dev hdc, sector 1429192
[4294677.908000] Buffer I/O error on device hdc, logical block 357298
[4294679.004000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294679.004000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[4294679.004000] ide: failed opcode was: unknown
[4294679.004000] end_request: I/O error, dev hdc, sector 1429192
[4294679.004000] Buffer I/O error on device hdc, logical block 357298
[4294680.114000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294680.114000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[4294680.114000] ide: failed opcode was: unknown
[4294680.114000] end_request: I/O error, dev hdc, sector 1429192
[4294680.114000] Buffer I/O error on device hdc, logical block 357298
[4294681.221000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294681.221000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[4294681.221000] ide: failed opcode was: unknown
[4294681.221000] end_request: I/O error, dev hdc, sector 1429192
[4294681.221000] Buffer I/O error on device hdc, logical block 357298
[4294682.376000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294682.376000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[4294682.376000] ide: failed opcode was: unknown
[4294682.376000] end_request: I/O error, dev hdc, sector 1429192
[4294682.376000] Buffer I/O error on device hdc, logical block 357298
[4294683.532000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294683.532000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[4294683.532000] ide: failed opcode was: unknown
[4294683.532000] end_request: I/O error, dev hdc, sector 1429192
[4294683.532000] Buffer I/O error on device hdc, logical block 357298
[4294683.914000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294683.914000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[4294683.914000] ide: failed opcode was: unknown
[4294683.914000] end_request: I/O error, dev hdc, sector 1429184
[4294683.914000] Buffer I/O error on device hdc, logical block 357296
[4294683.991000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294683.991000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[4294683.991000] ide: failed opcode was: unknown
[4294683.991000] end_request: I/O error, dev hdc, sector 1429188
[4294683.991000] Buffer I/O error on device hdc, logical block 357297
[4294684.068000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294684.068000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[4294684.068000] ide: failed opcode was: unknown
[4294684.068000] end_request: I/O error, dev hdc, sector 1429184
[4294684.068000] Buffer I/O error on device hdc, logical block 357296
[4294684.145000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294684.145000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[4294684.145000] ide: failed opcode was: unknown
[4294684.145000] end_request: I/O error, dev hdc, sector 1429188
[4294684.145000] Buffer I/O error on device hdc, logical block 357297[/COLOR][4294684.656000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294684.733000] ISO 9660 Extensions: RRIP_1991A
[4294684.813000] loop: loaded (max 8 devices)
[4294684.837000] Registering unionfs 1.1.2
[4294684.962000] squashfs: version 3.0prerelease (2006/1/24) Phillip Lougher
[4294814.566000] natsemi dp8381x driver, version 1.07+LK1.0.17, Sep 27, 2002
[4294814.566000]   originally by Donald Becker <becker@scyld.com>
[4294814.566000]   http://www.scyld.com/network/natsemi.html
[4294814.566000]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[COLOR="red"][4294814.567000] **** SET: Misaligned resource pointer: dfcc4602 Type 07 Len 0[/COLOR]
[4294814.567000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
[4294814.567000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNK1] -> GSI 10 (level, low) -> IRQ 10
[4294814.570000] natsemi eth0: NatSemi DP8381[56] at 0xd0004000 (0000:00:12.0), 00:0f:20:27:e6:e6, IRQ 10, port TP.
[4294849.020000] eth0: DSPCFG accepted after 0 usec.
[4294849.020000] eth0: link up.
[4294849.020000] eth0: Setting full-duplex based on negotiated link capability.
[4294849.028000] ts: Compaq touchscreen protocol output
[4294850.187000] NET: Registered protocol family 17
[4294851.824000] Linux agpgart interface v0.101 (c) Dave Jones
[4294853.096000] PCI: Enabling device 0000:00:06.0 (0005 -> 0007)
[COLOR="red"][4294853.096000] **** SET: Misaligned resource pointer: eb6751c2 Type 07 Len 0[/COLOR]
[4294853.096000] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 5
[4294853.096000] PCI: setting IRQ 5 as level-triggered
[4294853.096000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNK7] -> GSI 5 (level, low) -> IRQ 5
[4294853.386000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294854.135000] AC'97 1 does not respond - RESET
[4294854.135000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[4294854.135000] ali mixer 1 creating error.
[4294854.644000] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[4294854.644000] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
[4294855.847000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[4294855.847000] Yenta: CardBus bridge found at 0000:00:0a.0 [103c:0850]
[4294855.847000] Yenta O2: res at 0x94/0xD4: 00/ea
[4294855.847000] Yenta O2: enabling read prefetch/write burst
[4294855.969000] Yenta: ISA IRQ mask 0x0098, PCI irq 11
[4294855.969000] Socket status: 30000007
[4294856.549000] NET: Registered protocol family 10
[4294856.549000] lo: Disabled Privacy Extensions
[4294856.550000] IPv6 over IPv4 tunneling driver
[4294856.562000] agpgart: Detected Ati IGP345M chipset
[4294856.573000] agpgart: AGP aperture is 64M @ 0xd4000000
[4294857.062000] parport: PnPBIOS parport detected.
[4294857.062000] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294857.553000] Real Time Clock Driver v1.12
[4294857.764000] input: PC Speaker as /class/input/input2
[4294857.792000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294858.314000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[4294858.316000] cs: IO port probe 0x3e0-0x4ff: clean.
[4294858.317000] cs: IO port probe 0x820-0x8ff: clean.
[4294858.318000] cs: IO port probe 0xc00-0xcf7: clean.
[4294858.319000] cs: IO port probe 0xa00-0xaff: clean.
[4294858.417000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[4294858.454000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[4294859.884000] Adding 425680k swap on /dev/hda6.  Priority:-1 extents:1 across:425680k
[4294862.392000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294862.392000] md: bitmap version 4.39
[4294863.213000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294866.612000] eth0: no IPv6 routers present
[4294879.696000] ACPI: AC Adapter [ACAD] (on-line)
[4294879.799000] ACPI: Battery Slot [BAT1] (battery present)
[4294879.892000] ACPI: Power Button (FF) [PWRF]
[4294879.893000] ACPI: Power Button (CM) [PWRB]
[4294879.893000] ACPI: Lid Switch [LID]
[4294880.047000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
[4294880.047000] ibm_acpi: http://ibm-acpi.sf.net/
[4294880.083000] pcc_acpi: loading...
[4294880.225000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294885.438000] [drm] Initialized drm 1.0.1 20051102
[COLOR="red"][4294885.878000] **** SET: Misaligned resource pointer: dfca0102 Type 07 Len 0[/COLOR]
[4294885.878000] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 10
[4294885.878000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK0] -> GSI 10 (level, low) -> IRQ 10
[4294885.879000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[4294886.596000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294886.596000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294886.596000] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
[4294886.844000] [drm] Setting GART location based on old memory map
[4294886.845000] [drm] writeback test succeeded in 1 usecs
[4294899.919000] lp0: using parport0 (interrupt-driven).
[4294900.083000] ppdev: user-space parallel port driver
[4294901.839000] apm: BIOS not found.
[COLOR="red"][4294914.297000] serial8250: too much work for irq10
[4294914.314000] serial8250: too much work for irq10
[4294914.330000] serial8250: too much work for irq10
[4294914.347000] serial8250: too much work for irq10
[4294915.179000] serial8250: too much work for irq10
[4294915.195000] serial8250: too much work for irq10
[4294915.212000] serial8250: too much work for irq10
[4294915.228000] serial8250: too much work for irq10
[4294915.262000] serial8250: too much work for irq10
[4294915.278000] serial8250: too much work for irq10
[4294915.295000] serial8250: too much work for irq10
[4294915.312000] serial8250: too much work for irq10
[4294915.328000] serial8250: too much work for irq10
[4294915.677000] serial8250: too much work for irq10
[4294915.694000] serial8250: too much work for irq10
[4294915.711000] serial8250: too much work for irq10
[4294915.727000] serial8250: too much work for irq10
[4294915.777000] serial8250: too much work for irq10
[4294915.794000] serial8250: too much work for irq10
[4294915.810000] serial8250: too much work for irq10
[4294915.827000] serial8250: too much work for irq10[/COLOR][4294942.570000] Bluetooth: Core ver 2.8
[4294942.570000] NET: Registered protocol family 31
[4294942.570000] Bluetooth: HCI device and connection manager initialized
[4294942.570000] Bluetooth: HCI socket layer initialized
[4294944.472000] Bluetooth: L2CAP ver 2.8
[4294944.472000] Bluetooth: L2CAP socket layer initialized
[4294945.151000] Bluetooth: RFCOMM socket layer initialized
[4294945.151000] Bluetooth: RFCOMM TTY layer initialized
[4294945.151000] Bluetooth: RFCOMM ver 1.7

```

mmm :-k what to say... are there problems with acpi, ide, something else? The most strange thing is that, I just want to stress it, _Breezy is working fine_!!!

I've found something about the misaligned pointer on launchpad that's very similar to what I'm experiencing: [Misaligned Resource Pointers in dmesg output]("https://launchpad.net/distros/ubuntu/+bug/44800")

The last log, if it can help, is the lspci output:

```
0000:00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
0000:00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
0000:00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
0000:00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
0000:00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
0000:00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

```

I hope that someone can help me 8-[

---

### Post by david_e on 2006-06-10
I can't help you because I am not experienced, but I have looked into my dmesg:

```
davide@acer-ferrari:~$ dmesg |grep Misaligned
[4294670.604000] **** SET: Misaligned resource pointer: dfe377e2 Type 07 Len 0
[4294672.714000] **** SET: Misaligned resource pointer: df9e23c2 Type 07 Len 0
[4294675.303000] **** SET: Misaligned resource pointer: dfc605e2 Type 07 Len 0
[4294675.608000] **** SET: Misaligned resource pointer: dfb98b02 Type 07 Len 0

```
However I have no error messages in dmesg:

```
davide@acer-ferrari:~$ dmesg |grep error
davide@acer-ferrari:~$     
```
So the Buffer error messages could be linked to a different problem...

---

### Post by mpalla on 2006-06-17
So, after being a bit disappointed :???: by the first look at the Dapper release, and by the lack of help by the Ubuntu community, I have investigated a little bit more on the issues above, and my conclusions so far are the following:

[COLOR="Red"]**AC'97 and ali15x3_smbus errors:**[/COLOR]
they seems to be only warnings, or maybe things to be fine-tuned, because they appears even on Breezy and other live distributions. Not my first concern now.

[COLOR="red"]**Misaligned resource pointer warning:**[/COLOR]
it seems that a lot of users are experiencing this one, and according to [this one]("https://launchpad.net/distros/ubuntu/+bug/44800"), it seems that it can be safely ignored if you don't have any problems... david_e, you can relax now, but I think I still can't :sad:

**[COLOR="Red"]acpi-support error at startup:[/COLOR]**
:confused: still not sure about this one. Please advice!

**[COLOR="Red"]irq error:[/COLOR]**
:confused: again... Come on Ubuntu community, I need your help!

**[COLOR="Red"]mount & hd errors:[/COLOR]**
The hardware it's not faulty (checked with BIOS built-in utility), and these do not appear in Breezy and other live distributions. Also, I've noticed that after I've run the Dapper live, if I boot Breezy up, it just hangs the first time. After a power cycle, it starts again from the hd, after some fix to the file system...:-k
So, I think that there's definitely a problem with Dapper, and also a lot of other users are experiencing something like [this]("http://www.ubuntuforums.org/showthread.php?t=186115"), although a little bit different. I hope it will be fixed soon!!!

I hope I will be able to solve everything with someone's help, because I'm an Ubuntu enthusiast :KS, and just wish to continue using it...

---

### Post by mpalla on 2006-06-24
So, I've done a text install, and the system actually starts, but the errors are still there:

```
[17179569.184000] Linux version 2.6.15-25-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d8000 - 00000000000e0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000002bf70000 (usable)
[17179569.184000]  BIOS-e820: 000000002bf70000 - 000000002bf7c000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000002bf7c000 - 000000002bf80000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000002bf80000 - 000000002c000000 (reserved)
[17179569.184000]  BIOS-e820: 000000003bf80000 - 000000003c000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 703MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 180080
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 175984 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6ab0
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x2bf7529b
[17179569.184000] ACPI: FADT (v001 ATI    Salmon   0x06040000 ATI  0x000f4240) @ 0x2bf7bf64
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x2bf7bfd8
[17179569.184000] ACPI: DSDT (v001    ATI MS2_1535 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 3c000000:c3f80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01582000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 2791.455 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.564000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.564000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.604000] Memory: 703284k/720320k available (1976k kernel code, 16372k reserved, 606k data, 288k init, 0k highmem)
[17179569.604000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.684000] Calibrating delay using timer specific routine.. 5591.45 BogoMIPS (lpj=11182900)
[17179569.684000] Security Framework v1.0.0 initialized
[17179569.684000] SELinux:  Disabled at boot.
[17179569.684000] Mount-cache hash table entries: 512
[17179569.684000] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[17179569.684000] CPU: After vendor identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[17179569.684000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179569.684000] CPU: L2 cache: 128K
[17179569.684000] CPU: After all inits, caps: bfebf9ff 00000000 00000000 00000080 00004400 00000000 00000000
[17179569.684000] mtrr: v2.0 (20020519)
[17179569.684000] CPU: Intel(R) Celeron(R) CPU 2.80GHz stepping 09
[17179569.684000] Enabling fast FPU save and restore... done.
[17179569.684000] Enabling unmasked SIMD FPU exception support... done.
[17179569.684000] Checking 'hlt' instruction... OK.
[17179569.700000] checking if image is initramfs... it is
[17179570.760000] Freeing initrd memory: 6613k freed
[17179570.816000] ACPI: Looking for DSDT ... not found!
[17179570.820000] ACPI: setting ELCR to 0200 (from 0420)
[17179570.824000] NET: Registered protocol family 16
[17179570.824000] EISA bus registered
[17179570.824000] ACPI: bus type pci registered
[17179570.860000] PCI: PCI BIOS revision 2.10 entry at 0xfd89b, last bus=2
[17179570.860000] PCI: Using configuration type 1
[17179570.864000] ACPI: Subsystem revision 20051216
[17179570.928000] ACPI: Interpreter enabled
[17179570.928000] ACPI: Using PIC for interrupt routing
[17179570.928000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.928000] PCI: Probing PCI hardware (bus 00)
[17179570.932000] PCI quirk: region 8000-803f claimed by ali7101 ACPI
[17179570.932000] PCI quirk: region 8040-805f claimed by ali7101 SMB
[17179570.932000] Boot video device is 0000:01:05.0
[17179570.932000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.936000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[17179570.940000] ACPI: PCI Interrupt Link [LNK0] (IRQs 7 10) *0, disabled.
[17179570.940000] ACPI: PCI Interrupt Link [LNK1] (IRQs 7 *10)
[17179570.940000] ACPI: PCI Interrupt Link [LNK2] (IRQs 7 *10)
[17179570.940000] ACPI: PCI Interrupt Link [LNK3] (IRQs 7 *10)
[17179570.940000] ACPI: PCI Interrupt Link [LNK4] (IRQs 7 10) *0, disabled.
[17179570.944000] ACPI: PCI Interrupt Link [LNK5] (IRQs 7 *11)
[17179570.944000] ACPI: PCI Interrupt Link [LNK6] (IRQs 7 10) *0, disabled.
[17179570.944000] ACPI: PCI Interrupt Link [LNK7] (IRQs *5)
[17179570.944000] ACPI: PCI Interrupt Link [LNK8] (IRQs 7 10) *0, disabled.
[17179570.948000] ACPI: Embedded Controller [EC0] (gpe 24) interrupt mode.
[17179570.956000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.956000] pnp: PnP ACPI init
[17179570.960000] pnp: PnP ACPI: found 11 devices
[17179570.960000] PnPBIOS: Disabled by ACPI PNP
[17179570.960000] PCI: Using ACPI for IRQ routing
[17179570.960000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.964000] pnp: 00:06: ioport range 0x40b-0x40b has been reserved
[17179570.964000] pnp: 00:06: ioport range 0x480-0x48f has been reserved
[17179570.964000] pnp: 00:06: ioport range 0x4d0-0x4d1 has been reserved
[17179570.964000] pnp: 00:06: ioport range 0x4d6-0x4d6 has been reserved
[17179570.964000] pnp: 00:06: ioport range 0x8000-0x807f could not be reserved
[17179570.964000] PCI: Bridge: 0000:00:01.0
[17179570.964000]   IO window: 9000-9fff
[17179570.964000]   MEM window: d0300000-d03fffff
[17179570.964000]   PREFETCH window: d8000000-dfffffff
[17179570.964000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[17179570.964000]   IO window: 00001800-000018ff
[17179570.964000]   IO window: 00001c00-00001cff
[17179570.964000]   PREFETCH window: 40000000-41ffffff
[17179570.964000]   MEM window: 42000000-43ffffff
[17179570.964000] PCI: Enabling device 0000:00:0a.0 (0005 -> 0007)
[17179570.964000] **** SET: Misaligned resource pointer: dfe755c2 Type 07 Len 0
[17179570.964000] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 11
[17179570.964000] PCI: setting IRQ 11 as level-triggered
[17179570.964000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[17179570.964000] Simple Boot Flag at 0x37 set to 0x1
[17179570.964000] audit: initializing netlink socket (disabled)
[17179570.964000] audit(1151145134.964:1): initialized
[17179570.964000] VFS: Disk quotas dquot_6.5.1
[17179570.964000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.964000] Initializing Cryptographic API
[17179570.964000] io scheduler noop registered
[17179570.964000] io scheduler anticipatory registered
[17179570.964000] io scheduler deadline registered
[17179570.964000] io scheduler cfq registered
[17179570.964000] Activating ISA DMA hang workarounds.
[17179570.968000] isapnp: Scanning for PnP cards...
[17179571.320000] isapnp: No Plug & Play device found
[17179571.404000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179571.408000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.412000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.412000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179571.424000] PCI: Enabling device 0000:00:08.0 (0000 -> 0003)
[17179571.424000] **** SET: Misaligned resource pointer: dfc421c2 Type 07 Len 0
[17179571.424000] ACPI: PCI Interrupt Link [LNK6] enabled at IRQ 10
[17179571.424000] PCI: setting IRQ 10 as level-triggered
[17179571.424000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNK6] -> GSI 10 (level, low) -> IRQ 10
[17179571.428000] 0000:00:08.0: ttyS9 at I/O 0x1428 (irq = 10) is a 8250
[17179571.428000] 0000:00:08.0: ttyS12 at I/O 0x1440 (irq = 10) is a 8250
[17179571.432000] 0000:00:08.0: ttyS14 at I/O 0x1450 (irq = 10) is a 8250
[17179571.432000] 0000:00:08.0: ttyS16 at I/O 0x1460 (irq = 10) is a 8250
[17179571.432000] 0000:00:08.0: ttyS18 at I/O 0x1470 (irq = 10) is a 8250
[17179571.444000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.444000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.444000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.448000] mice: PS/2 mouse device common for all mice
[17179571.448000] EISA: Probing bus 0 at eisa.0
[17179571.448000] Cannot allocate resource for EISA slot 1
[17179571.448000] Cannot allocate resource for EISA slot 2
[17179571.448000] Cannot allocate resource for EISA slot 8
[17179571.448000] EISA: Detected 0 cards.
[17179571.448000] NET: Registered protocol family 2
[17179571.484000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.484000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.484000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.484000] TCP: Hash tables configured (established 131072 bind 65536)
[17179571.484000] TCP reno registered
[17179571.484000] TCP bic registered
[17179571.484000] NET: Registered protocol family 1
[17179571.484000] NET: Registered protocol family 8
[17179571.484000] NET: Registered protocol family 20
[17179571.484000] Using IPI Shortcut mode
[17179571.484000] ACPI wakeup devices: 
[17179571.484000] PCI0 MDEM  LAN  LID 
[17179571.484000] ACPI: (supports S0 S3 S4 S5)
[17179571.484000] Freeing unused kernel memory: 288k freed
[17179571.488000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.572000] vga16fb: initializing
[17179571.572000] vga16fb: mapped to 0xc00a0000
[17179571.700000] Console: switching to colour frame buffer device 80x25
[17179571.700000] fb0: VGA16 VGA frame buffer device
[17179572.820000] Capability LSM initialized
[17179572.892000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179572.896000] ACPI: Thermal Zone [THRM] (55 C)
[17179574.252000] ALI15X3: IDE controller at PCI slot 0000:00:10.0
[17179574.252000] ACPI: PCI Interrupt 0000:00:10.0[A]: no GSI
[17179574.252000] ALI15X3: chipset revision 196
[17179574.252000] ALI15X3: not 100% native mode: will probe irqs later
[17179574.252000]     ide0: BM-DMA at 0x2040-0x2047, BIOS settings: hda:DMA, hdb:pio
[17179574.252000]     ide1: BM-DMA at 0x2048-0x204f, BIOS settings: hdc:pio, hdd:pio
[17179574.252000] Probing IDE interface ide0...
[17179574.540000] hda: ST93015A, ATA DISK drive
[17179575.212000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.508000] Probing IDE interface ide1...
[17179576.244000] hdc: SD-R6252, ATAPI CD/DVD-ROM drive
[17179576.964000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.992000] hda: max request size: 128KiB
[17179577.008000] hda: 58605120 sectors (30005 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179577.008000] hda: cache flushes supported
[17179577.008000]  hda: hda1 hda2 < hda5 hda6 > hda3
[17179577.392000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[17179577.392000] Uniform CD-ROM driver Revision: 3.20
[17179577.872000] usbcore: registered new driver usbfs
[17179577.872000] usbcore: registered new driver hub
[17179577.876000] USB Universal Host Controller Interface driver v2.3
[17179577.876000] **** SET: Misaligned resource pointer: dfcba402 Type 07 Len 0
[17179577.876000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 10
[17179577.876000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
[17179577.876000] uhci_hcd 0000:00:0b.0: UHCI Host Controller
[17179577.880000] uhci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[17179577.880000] uhci_hcd 0000:00:0b.0: irq 10, io base 0x00002000
[17179577.880000] hub 1-0:1.0: USB hub found
[17179577.880000] hub 1-0:1.0: 2 ports detected
[17179577.984000] **** SET: Misaligned resource pointer: dfcba102 Type 07 Len 0
[17179577.984000] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 10
[17179577.984000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LNK3] -> GSI 10 (level, low) -> IRQ 10
[17179577.984000] uhci_hcd 0000:00:0b.1: UHCI Host Controller
[17179577.984000] uhci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[17179577.984000] uhci_hcd 0000:00:0b.1: irq 10, io base 0x00002020
[17179577.984000] hub 2-0:1.0: USB hub found
[17179577.984000] hub 2-0:1.0: 2 ports detected
[17179578.088000] PCI: Enabling device 0000:00:0b.2 (0010 -> 0012)
[17179578.088000] ACPI: PCI Interrupt 0000:00:0b.2[C] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[17179578.088000] PCI: Via IRQ fixup for 0000:00:0b.2, from 255 to 11
[17179578.088000] ehci_hcd 0000:00:0b.2: EHCI Host Controller
[17179578.092000] ehci_hcd 0000:00:0b.2: new USB bus registered, assigned bus number 3
[17179578.092000] ehci_hcd 0000:00:0b.2: irq 11, io mem 0xd0003000
[17179578.092000] ehci_hcd 0000:00:0b.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[17179578.092000] hub 3-0:1.0: USB hub found
[17179578.092000] hub 3-0:1.0: 4 ports detected
[17179578.352000] Attempting manual resume
[17179578.396000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.424000] kjournald starting.  Commit interval 5 seconds
[17179579.084000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[17179593.732000] Real Time Clock Driver v1.12
[17179593.768000] Linux agpgart interface v0.101 (c) Dave Jones
[17179593.772000] agpgart: Detected Ati IGP345M chipset
[17179593.780000] agpgart: AGP aperture is 64M @ 0xd4000000
[17179593.832000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[17179593.832000] Yenta: CardBus bridge found at 0000:00:0a.0 [103c:0850]
[17179593.832000] Yenta O2: res at 0x94/0xD4: 00/ea
[17179593.832000] Yenta O2: enabling read prefetch/write burst
[17179593.880000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179593.952000] PCI: Enabling device 0000:00:06.0 (0005 -> 0007)
[17179593.952000] **** SET: Misaligned resource pointer: e943e702 Type 07 Len 0
[17179593.952000] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 5
[17179593.952000] PCI: setting IRQ 5 as level-triggered
[17179593.952000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNK7] -> GSI 5 (level, low) -> IRQ 5
[17179593.992000] Yenta: ISA IRQ mask 0x0098, PCI irq 11
[17179593.992000] Socket status: 30000007
[17179594.004000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179594.004000] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[17179594.004000] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
[17179594.132000] parport: PnPBIOS parport detected.
[17179594.132000] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179594.276000] usbcore: registered new driver hiddev
[17179594.308000] input: PS/2+USB Mouse as /class/input/input1
[17179594.308000] input: USB HID v1.10 Mouse [PS/2+USB Mouse] on usb-0000:00:0b.1-1
[17179594.308000] usbcore: registered new driver usbhid
[17179594.308000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179594.500000] input: PC Speaker as /class/input/input2
[17179594.520000] ts: Compaq touchscreen protocol output
[17179594.576000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[17179594.576000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179594.576000] cs: IO port probe 0x820-0x8ff: clean.
[17179594.580000] cs: IO port probe 0xc00-0xcf7: clean.
[17179594.580000] cs: IO port probe 0xa00-0xaff: clean.
[17179594.676000] natsemi dp8381x driver, version 1.07+LK1.0.17, Sep 27, 2002
[17179594.676000]   originally by Donald Becker <becker@scyld.com>
[17179594.676000]   http://www.scyld.com/network/natsemi.html
[17179594.676000]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[17179595.000000] AC'97 1 does not respond - RESET
[17179595.000000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[17179595.000000] ali mixer 1 creating error.
[17179595.020000] **** SET: Misaligned resource pointer: e70c55c2 Type 07 Len 0
[17179595.020000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
[17179595.020000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNK1] -> GSI 10 (level, low) -> IRQ 10
[17179595.028000] natsemi eth0: NatSemi DP8381[56] at 0xd0004000 (0000:00:12.0), 00:0f:20:27:e6:e6, IRQ 10, port TP.
[17179595.656000] eth0: DSPCFG accepted after 0 usec.
[17179595.656000] eth0: link up.
[17179595.656000] eth0: Setting full-duplex based on negotiated link capability.
[17179595.956000] lp0: using parport0 (interrupt-driven).
[17179596.008000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[17179596.048000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[17179596.152000] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
[17179596.152000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[17179596.164000] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
[17179596.164000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[17179596.212000] Adding 425680k swap on /dev/hda6.  Priority:-1 extents:1 across:425680k
[17179596.388000] EXT3 FS on hda3, internal journal
[17179596.676000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179596.676000] md: bitmap version 4.39
[17179596.708000] NET: Registered protocol family 17
[17179597.256000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179598.268000] cdrom: open failed.
[17179598.564000] NET: Registered protocol family 10
[17179598.564000] lo: Disabled Privacy Extensions
[17179598.564000] IPv6 over IPv4 tunneling driver
[17179600.920000] ACPI: AC Adapter [ACAD] (on-line)
[17179600.924000] ACPI: Battery Slot [BAT1] (battery present)
[17179601.048000] ACPI: Power Button (FF) [PWRF]
[17179601.048000] ACPI: Power Button (CM) [PWRB]
[17179601.048000] ACPI: Lid Switch [LID]
[17179601.192000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
[17179601.196000] ibm_acpi: http://ibm-acpi.sf.net/
[17179601.236000] pcc_acpi: loading...
[17179601.388000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179607.536000] [drm] Initialized drm 1.0.1 20051102
[17179607.624000] **** SET: Misaligned resource pointer: e6de2c02 Type 07 Len 0
[17179607.628000] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 10
[17179607.628000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK0] -> GSI 10 (level, low) -> IRQ 10
[17179607.628000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[17179608.600000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179608.600000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179608.600000] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
[17179608.704000] ppdev: user-space parallel port driver
[17179608.872000] [drm] Setting GART location based on old memory map
[17179608.872000] [drm] writeback test succeeded in 1 usecs
[17179609.016000] eth0: no IPv6 routers present
[17179609.456000] apm: BIOS not found.
[17179611.020000] serial8250: too much work for irq10
[17179611.036000] serial8250: too much work for irq10
[17179611.052000] serial8250: too much work for irq10
[17179611.068000] serial8250: too much work for irq10
[17179611.120000] serial8250: too much work for irq10
[17179611.136000] serial8250: too much work for irq10
[17179611.152000] serial8250: too much work for irq10
[17179611.168000] serial8250: too much work for irq10
[17179611.220000] serial8250: too much work for irq10
[17179611.236000] serial8250: too much work for irq10
[17179611.252000] serial8250: too much work for irq10
[17179611.268000] serial8250: too much work for irq10
[17179611.300000] serial8250: too much work for irq10
[17179611.320000] serial8250: too much work for irq10
[17179611.336000] serial8250: too much work for irq10
[17179611.352000] serial8250: too much work for irq10
[17179611.368000] serial8250: too much work for irq10
[17179611.420000] serial8250: too much work for irq10
[17179611.436000] serial8250: too much work for irq10
[17179611.452000] serial8250: too much work for irq10
[17179611.468000] serial8250: too much work for irq10
[17179614.624000] Bluetooth: Core ver 2.8
[17179614.624000] NET: Registered protocol family 31
[17179614.624000] Bluetooth: HCI device and connection manager initialized
[17179614.624000] Bluetooth: HCI socket layer initialized
[17179614.648000] Bluetooth: L2CAP ver 2.8
[17179614.648000] Bluetooth: L2CAP socket layer initialized
[17179614.656000] Bluetooth: RFCOMM socket layer initialized
[17179614.656000] Bluetooth: RFCOMM TTY layer initialized
[17179614.656000] Bluetooth: RFCOMM ver 1.7

```

More info:

```
 cat /proc/interrupts
           CPU0
  0:     137644          XT-PIC  timer
  1:        759          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  5:       1969          XT-PIC  ALI 5451
  7:          2          XT-PIC  parport0
  8:          3          XT-PIC  rtc
  9:       7964          XT-PIC  acpi
 10:      54340          XT-PIC  uhci_hcd:usb1, uhci_hcd:usb2, eth0, radeon@pci:0000:01:05.0
 11:          6          XT-PIC  ehci_hcd:usb3, yenta
 12:        123          XT-PIC  i8042
 14:       6990          XT-PIC  ide0
 15:       8762          XT-PIC  ide1
NMI:          0
LOC:          0
ERR:          0
MIS:          0

```

and

```
tail messages
Jun 24 10:32:58 mobile kernel: [17179614.656000] Bluetooth: RFCOMM socket layer initialized
Jun 24 10:32:58 mobile kernel: [17179614.656000] Bluetooth: RFCOMM TTY layer initialized
Jun 24 10:32:58 mobile kernel: [17179614.656000] Bluetooth: RFCOMM ver 1.7
Jun 24 10:33:07 mobile gconfd (mpalla-4814): starting (version 2.14.0), pid 4814 user 'mpalla'
Jun 24 10:33:07 mobile gconfd (mpalla-4814): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 24 10:33:07 mobile gconfd (mpalla-4814): Resolved address "xml:readwrite:/home/mpalla/.gconf" to a writable configuration source at position 1
Jun 24 10:33:07 mobile gconfd (mpalla-4814): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 24 10:33:07 mobile gconfd (mpalla-4814): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 24 10:33:07 mobile gconfd (mpalla-4814): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 24 10:33:12 mobile gconfd (mpalla-4814): Resolved address "xml:readwrite:/home/mpalla/.gconf" to a writable configuration source at position 0

```

Please, any idea :confused:

---

### Post by mpalla on 2006-07-03
please, anyone?

---

### Post by mpalla on 2006-07-08
So, I managed to clean up my dmesg a little bit, disabling a lot of unused services at the startup, using the [bum]("http://packages.ubuntu.com/dapper/admin/bum") application. Now my dmesg looks like:

```
[17179569.184000] Linux version 2.6.15-25-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d8000 - 00000000000e0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000002bf70000 (usable)
[17179569.184000]  BIOS-e820: 000000002bf70000 - 000000002bf7c000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000002bf7c000 - 000000002bf80000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000002bf80000 - 000000002c000000 (reserved)
[17179569.184000]  BIOS-e820: 000000003bf80000 - 000000003c000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 703MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 180080
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 175984 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6ab0
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x2bf7529b
[17179569.184000] ACPI: FADT (v001 ATI    Salmon   0x06040000 ATI  0x000f4240) @ 0x2bf7bf64
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x2bf7bfd8
[17179569.184000] ACPI: DSDT (v001    ATI MS2_1535 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 3c000000:c3f80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01673000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 2791.288 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.948000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.952000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.996000] Memory: 701944k/720320k available (2101k kernel code, 17716k reserved, 592k data, 332k init, 0k highmem)
[17179571.996000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.076000] Calibrating delay using timer specific routine.. 5592.64 BogoMIPS (lpj=11185280)
[17179572.076000] Security Framework v1.0.0 initialized
[17179572.076000] SELinux:  Disabled at boot.
[17179572.076000] Mount-cache hash table entries: 512
[17179572.076000] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.076000] CPU: After vendor identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.076000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179572.076000] CPU: L2 cache: 128K
[17179572.076000] CPU: Hyper-Threading is disabled
[17179572.076000] CPU: After all inits, caps: bfebf9ff 00000000 00000000 00000080 00004400 00000000 00000000
[17179572.076000] mtrr: v2.0 (20020519)
[17179572.076000] Enabling fast FPU save and restore... done.
[17179572.076000] Enabling unmasked SIMD FPU exception support... done.
[17179572.076000] Checking 'hlt' instruction... OK.
[17179572.092000] SMP alternatives: switching to UP code
[17179572.092000] checking if image is initramfs... it is
[17179573.156000] Freeing initrd memory: 6804k freed
[17179573.216000] ACPI: Looking for DSDT ... not found!
[17179573.220000] ACPI: setting ELCR to 0200 (from 0420)
[17179573.224000] CPU0: Intel(R) Celeron(R) CPU 2.80GHz stepping 09
[17179573.224000] SMP motherboard not detected.
[17179573.224000] Local APIC not detected. Using dummy APIC emulation.
[17179573.224000] Brought up 1 CPUs
[17179573.224000] NET: Registered protocol family 16
[17179573.224000] EISA bus registered
[17179573.224000] ACPI: bus type pci registered
[17179573.260000] PCI: PCI BIOS revision 2.10 entry at 0xfd89b, last bus=2
[17179573.260000] PCI: Using configuration type 1
[17179573.260000] ACPI: Subsystem revision 20051216
[17179573.328000] ACPI: Interpreter enabled
[17179573.328000] ACPI: Using PIC for interrupt routing
[17179573.328000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.328000] PCI: Probing PCI hardware (bus 00)
[17179573.332000] PCI quirk: region 8000-803f claimed by ali7101 ACPI
[17179573.332000] PCI quirk: region 8040-805f claimed by ali7101 SMB
[17179573.332000] Boot video device is 0000:01:05.0
[17179573.332000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.336000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[17179573.340000] ACPI: PCI Interrupt Link [LNK0] (IRQs 7 10) *0, disabled.
[17179573.340000] ACPI: PCI Interrupt Link [LNK1] (IRQs 7 *10)
[17179573.340000] ACPI: PCI Interrupt Link [LNK2] (IRQs 7 *10)
[17179573.340000] ACPI: PCI Interrupt Link [LNK3] (IRQs 7 *10)
[17179573.340000] ACPI: PCI Interrupt Link [LNK4] (IRQs 7 10) *0, disabled.
[17179573.344000] ACPI: PCI Interrupt Link [LNK5] (IRQs 7 *11)
[17179573.344000] ACPI: PCI Interrupt Link [LNK6] (IRQs 7 10) *0, disabled.
[17179573.344000] ACPI: PCI Interrupt Link [LNK7] (IRQs *5)
[17179573.344000] ACPI: PCI Interrupt Link [LNK8] (IRQs 7 10) *0, disabled.
[17179573.348000] ACPI: Embedded Controller [EC0] (gpe 24) interrupt mode.
[17179573.356000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.356000] pnp: PnP ACPI init
[17179573.360000] pnp: PnP ACPI: found 11 devices
[17179573.360000] PnPBIOS: Disabled by ACPI PNP
[17179573.360000] PCI: Using ACPI for IRQ routing
[17179573.360000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.364000] pnp: 00:06: ioport range 0x40b-0x40b has been reserved
[17179573.364000] pnp: 00:06: ioport range 0x480-0x48f has been reserved
[17179573.364000] pnp: 00:06: ioport range 0x4d0-0x4d1 has been reserved
[17179573.364000] pnp: 00:06: ioport range 0x4d6-0x4d6 has been reserved
[17179573.364000] pnp: 00:06: ioport range 0x8000-0x807f could not be reserved
[17179573.364000] PCI: Bridge: 0000:00:01.0
[17179573.364000]   IO window: 9000-9fff
[17179573.364000]   MEM window: d0300000-d03fffff
[17179573.364000]   PREFETCH window: d8000000-dfffffff
[17179573.364000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[17179573.364000]   IO window: 00001800-000018ff
[17179573.364000]   IO window: 00001c00-00001cff
[17179573.364000]   PREFETCH window: 40000000-41ffffff
[17179573.364000]   MEM window: 42000000-43ffffff
[17179573.364000] PCI: Enabling device 0000:00:0a.0 (0005 -> 0007)
[17179573.364000] **** SET: Misaligned resource pointer: dfe09dc2 Type 07 Len 0
[17179573.364000] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 11
[17179573.364000] PCI: setting IRQ 11 as level-triggered
[17179573.364000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[17179573.364000] Simple Boot Flag at 0x37 set to 0x1
[17179573.364000] audit: initializing netlink socket (disabled)
[17179573.364000] audit(1152349668.360:1): initialized
[17179573.368000] VFS: Disk quotas dquot_6.5.1
[17179573.368000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.368000] Initializing Cryptographic API
[17179573.368000] io scheduler noop registered
[17179573.368000] io scheduler anticipatory registered
[17179573.368000] io scheduler deadline registered
[17179573.368000] io scheduler cfq registered
[17179573.368000] Activating ISA DMA hang workarounds.
[17179573.368000] isapnp: Scanning for PnP cards...
[17179573.720000] isapnp: No Plug & Play device found
[17179573.820000] Real Time Clock Driver v1.12
[17179573.820000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179573.824000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.824000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.824000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179573.836000] PCI: Enabling device 0000:00:08.0 (0000 -> 0003)
[17179573.836000] **** SET: Misaligned resource pointer: dfedd3c2 Type 07 Len 0
[17179573.836000] ACPI: PCI Interrupt Link [LNK6] enabled at IRQ 10
[17179573.836000] PCI: setting IRQ 10 as level-triggered
[17179573.836000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNK6] -> GSI 10 (level, low) -> IRQ 10
[17179573.840000] 0000:00:08.0: ttyS9 at I/O 0x1428 (irq = 10) is a 8250
[17179573.844000] 0000:00:08.0: ttyS12 at I/O 0x1440 (irq = 10) is a 8250
[17179573.844000] 0000:00:08.0: ttyS14 at I/O 0x1450 (irq = 10) is a 8250
[17179573.844000] 0000:00:08.0: ttyS16 at I/O 0x1460 (irq = 10) is a 8250
[17179573.848000] 0000:00:08.0: ttyS18 at I/O 0x1470 (irq = 10) is a 8250
[17179573.860000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.860000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.860000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.860000] mice: PS/2 mouse device common for all mice
[17179573.860000] EISA: Probing bus 0 at eisa.0
[17179573.860000] Cannot allocate resource for EISA slot 1
[17179573.860000] Cannot allocate resource for EISA slot 2
[17179573.860000] Cannot allocate resource for EISA slot 8
[17179573.860000] EISA: Detected 0 cards.
[17179573.860000] NET: Registered protocol family 2
[17179573.900000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.900000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[17179573.900000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.904000] TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
[17179573.904000] TCP: Hash tables configured (established 131072 bind 65536)
[17179573.904000] TCP reno registered
[17179573.904000] TCP bic registered
[17179573.904000] NET: Registered protocol family 1
[17179573.904000] NET: Registered protocol family 8
[17179573.904000] NET: Registered protocol family 20
[17179573.904000] Using IPI No-Shortcut mode
[17179573.904000] ACPI wakeup devices: 
[17179573.904000] PCI0 MDEM  LAN  LID 
[17179573.904000] ACPI: (supports S0 S3 S4 S5)
[17179573.904000] Freeing unused kernel memory: 332k freed
[17179574.004000] vga16fb: initializing
[17179574.004000] vga16fb: mapped to 0xc00a0000
[17179574.132000] Console: switching to colour frame buffer device 80x25
[17179574.132000] fb0: VGA16 VGA frame buffer device
[17179575.220000] Capability LSM initialized
[17179575.392000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179575.396000] ACPI: Thermal Zone [THRM] (49 C)
[17179577.272000] ALI15X3: IDE controller at PCI slot 0000:00:10.0
[17179577.272000] ACPI: PCI Interrupt 0000:00:10.0[A]: no GSI
[17179577.272000] ALI15X3: chipset revision 196
[17179577.272000] ALI15X3: not 100% native mode: will probe irqs later
[17179577.272000]     ide0: BM-DMA at 0x2040-0x2047, BIOS settings: hda:DMA, hdb:pio
[17179577.272000]     ide1: BM-DMA at 0x2048-0x204f, BIOS settings: hdc:pio, hdd:pio
[17179577.272000] Probing IDE interface ide0...
[17179577.560000] hda: ST93015A, ATA DISK drive
[17179578.232000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179578.496000] Probing IDE interface ide1...
[17179579.232000] hdc: SD-R6252, ATAPI CD/DVD-ROM drive
[17179579.916000] ide1 at 0x170-0x177,0x376 on irq 15
[17179579.948000] hda: max request size: 128KiB
[17179579.968000] hda: 58605120 sectors (30005 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179579.972000] hda: cache flushes supported
[17179579.972000]  hda: hda1 hda2 < hda5 hda6 > hda3
[17179580.392000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[17179580.392000] Uniform CD-ROM driver Revision: 3.20
[17179580.940000] usbcore: registered new driver usbfs
[17179580.940000] usbcore: registered new driver hub
[17179580.948000] USB Universal Host Controller Interface driver v2.3
[17179580.948000] **** SET: Misaligned resource pointer: dfc16882 Type 07 Len 0
[17179580.952000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 10
[17179580.952000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
[17179580.952000] uhci_hcd 0000:00:0b.0: UHCI Host Controller
[17179580.952000] uhci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[17179580.952000] uhci_hcd 0000:00:0b.0: irq 10, io base 0x00002000
[17179580.956000] hub 1-0:1.0: USB hub found
[17179580.956000] hub 1-0:1.0: 2 ports detected
[17179581.060000] **** SET: Misaligned resource pointer: dfc16702 Type 07 Len 0
[17179581.060000] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 10
[17179581.060000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LNK3] -> GSI 10 (level, low) -> IRQ 10
[17179581.060000] uhci_hcd 0000:00:0b.1: UHCI Host Controller
[17179581.060000] uhci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[17179581.060000] uhci_hcd 0000:00:0b.1: irq 10, io base 0x00002020
[17179581.064000] hub 2-0:1.0: USB hub found
[17179581.064000] hub 2-0:1.0: 2 ports detected
[17179581.172000] PCI: Enabling device 0000:00:0b.2 (0010 -> 0012)
[17179581.172000] ACPI: PCI Interrupt 0000:00:0b.2[C] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[17179581.172000] PCI: Via IRQ fixup for 0000:00:0b.2, from 255 to 11
[17179581.172000] ehci_hcd 0000:00:0b.2: EHCI Host Controller
[17179581.172000] ehci_hcd 0000:00:0b.2: new USB bus registered, assigned bus number 3
[17179581.172000] ehci_hcd 0000:00:0b.2: irq 11, io mem 0xd0003000
[17179581.172000] ehci_hcd 0000:00:0b.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[17179581.176000] hub 3-0:1.0: USB hub found
[17179581.176000] hub 3-0:1.0: 4 ports detected
[17179581.424000] Attempting manual resume
[17179581.476000] EXT3-fs: mounted filesystem with ordered data mode.
[17179581.500000] kjournald starting.  Commit interval 5 seconds
[17179582.164000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[17179597.536000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179597.556000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179597.692000] Linux agpgart interface v0.101 (c) Dave Jones
[17179597.696000] agpgart: Detected Ati IGP345M chipset
[17179597.704000] agpgart: AGP aperture is 64M @ 0xd4000000
[17179598.116000] PCI: Enabling device 0000:00:06.0 (0005 -> 0007)
[17179598.116000] **** SET: Misaligned resource pointer: ea848a82 Type 07 Len 0
[17179598.116000] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 5
[17179598.116000] PCI: setting IRQ 5 as level-triggered
[17179598.116000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNK7] -> GSI 5 (level, low) -> IRQ 5
[17179598.188000] natsemi dp8381x driver, version 1.07+LK1.0.17, Sep 27, 2002
[17179598.188000]   originally by Donald Becker <becker@scyld.com>
[17179598.188000]   http://www.scyld.com/network/natsemi.html
[17179598.188000]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[17179598.312000] input: PC Speaker as /class/input/input1
[17179598.456000] usbcore: registered new driver hiddev
[17179598.484000] input: PS/2+USB Mouse as /class/input/input2
[17179598.484000] input: USB HID v1.10 Mouse [PS/2+USB Mouse] on usb-0000:00:0b.1-1
[17179598.484000] usbcore: registered new driver usbhid
[17179598.484000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179598.516000] parport: PnPBIOS parport detected.
[17179598.516000] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179598.868000] ts: Compaq touchscreen protocol output
[17179598.908000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[17179598.944000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[17179599.052000] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
[17179599.052000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[17179599.064000] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
[17179599.064000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[17179599.160000] AC'97 1 does not respond - RESET
[17179599.160000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[17179599.160000] ali mixer 1 creating error.
[17179599.172000] **** SET: Misaligned resource pointer: e6c9db82 Type 07 Len 0
[17179599.172000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
[17179599.172000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNK1] -> GSI 10 (level, low) -> IRQ 10
[17179599.176000] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[17179599.176000] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
[17179599.176000] natsemi eth0: NatSemi DP8381[56] at 0xd0004000 (0000:00:12.0), 00:0f:20:27:e6:e6, IRQ 10, port TP.
[17179599.176000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[17179599.176000] Yenta: CardBus bridge found at 0000:00:0a.0 [103c:0850]
[17179599.176000] Yenta O2: res at 0x94/0xD4: 00/ea
[17179599.176000] Yenta O2: enabling read prefetch/write burst
[17179599.304000] Yenta: ISA IRQ mask 0x0018, PCI irq 11
[17179599.304000] Socket status: 30000007
[17179599.596000] eth0: DSPCFG accepted after 0 usec.
[17179599.596000] eth0: link up.
[17179599.596000] eth0: Setting full-duplex based on negotiated link capability.
[17179599.708000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[17179599.712000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179599.712000] cs: IO port probe 0x820-0x8ff: clean.
[17179599.712000] cs: IO port probe 0xc00-0xcf7: clean.
[17179599.716000] cs: IO port probe 0xa00-0xaff: clean.
[17179600.140000] lp0: using parport0 (interrupt-driven).
[17179600.252000] Adding 425680k swap on /dev/hda6.  Priority:-1 extents:1 across:425680k
[17179600.424000] EXT3 FS on hda3, internal journal
[17179600.692000] NET: Registered protocol family 17
[17179600.756000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179600.756000] md: bitmap version 4.39
[17179601.376000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179602.324000] cdrom: open failed.
[17179605.108000] ACPI: AC Adapter [ACAD] (on-line)
[17179605.124000] ACPI: Battery Slot [BAT1] (battery present)
[17179605.256000] ACPI: Power Button (FF) [PWRF]
[17179605.256000] ACPI: Power Button (CM) [PWRB]
[17179605.256000] ACPI: Lid Switch [LID]
[17179605.428000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
[17179605.428000] ibm_acpi: http://ibm-acpi.sf.net/
[17179605.472000] pcc_acpi: loading...
[17179605.644000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179610.904000] NET: Registered protocol family 10
[17179610.904000] lo: Disabled Privacy Extensions
[17179610.904000] IPv6 over IPv4 tunneling driver
[17179612.580000] [drm] Initialized drm 1.0.1 20051102
[17179612.600000] **** SET: Misaligned resource pointer: e6c56782 Type 07 Len 0
[17179612.600000] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 10
[17179612.600000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK0] -> GSI 10 (level, low) -> IRQ 10
[17179612.600000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[17179613.612000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179613.612000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179613.612000] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
[17179613.872000] [drm] Setting GART location based on old memory map
[17179613.872000] [drm] writeback test succeeded in 1 usecs
[17179621.576000] eth0: no IPv6 routers present

```

---

