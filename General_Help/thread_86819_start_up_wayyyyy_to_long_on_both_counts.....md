---
title: "start up wayyyyy to long on both counts...."
date: 2005-11-06
forum: General Help
---

### Post by Trab on 2005-11-06
after switching to breezy final from colony 3, i was very happy about most of the new features and such. but the start up.... ugh the start up.... it takes forever! but to be honest, i think its something i did wrong... this is hte start up part where it says "starting network blah blah blah" and such...
and then i have another issue.... after all that crap is figured out, X and Gnome start.... but all it is is a brown screen with my mouse on it... i can move the mouse but i cant click.... perhaps 5 minutes after sitting there, it magically works fine... this, as you can imagine, is VERY annoying, the first time it happend i was worried about it being broken....
any help would be apcrecated.
-Trab

---

### Post by Trab on 2005-11-07
i felt this needed a bump.... the gnome start-up time is repulsive... when i ctrl+backspace and relogin it takes long as well....
any help would be great, thanks....

---

### Post by az on 2005-11-07
What processor do you have, how much memory, too?

Post the output of
dmesg
from a terminal.


Also run top and see if something it hogging your cpu power.  A display of all running processes by percent cpu power will be displayed.

---

### Post by dtfinch on 2005-11-07
Do you have a home network? The bootup network delay could be if you do but there is no dhcp server to answer its request. If your internet access does not go over your lan, like with dialup, this problem might go unnoticed.

For the other slowness, having 512mb or more ram helps.

Also, it's not entirely unheard of for an intensive process to be running in the background on systems that have been customized a lot. I installed something called "samhain" once that slowed down my system to a near crawl. I was unaware that installing it would cause it to run almost all the time. Also, there's a cron job called slocate (shows as updatedb) that sometimes causes slowdowns, but not during startup.

---

### Post by Trab on 2005-11-08
its a new processor, and i think i havd 512mb ram....
its a new problem... as of 2 weeks ago friday... i dont REALLY mind the start-up that comes after grub (the ok fail part) but something is wrong with gnome, even when i hit ctrl+backspace and then relogin i get the "brown screen of lag"
here is the dmesg stuff....
```

tedd@raptor:~$ dmesg
4669.121000] NET: Registered protocol family 2
[4294669.131000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294669.131000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[4294669.131000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294669.131000] TCP: Hash tables configured (established 32768 bind 32768)
[4294669.131000] NET: Registered protocol family 8
[4294669.131000] NET: Registered protocol family 20
[4294669.131000] ACPI wakeup devices:
[4294669.131000] PCI0 USB0 USB1 USB2 USB6 USB7 USB8 USB9 LAN0 UAR1 LPT1
[4294669.131000] ACPI: (supports S0 S1 S4 S5)
[4294669.132000] Freeing unused kernel memory: 224k freed
[4294669.142000] vga16fb: initializing
[4294669.142000] vga16fb: mapped to 0xc00a0000
[4294669.277000] Console: switching to colour frame buffer device 80x30
[4294669.277000] fb0: VGA16 VGA frame buffer device
[4294669.285000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294670.400000] Capability LSM initialized
[4294670.409000] NET: Registered protocol family 1
[4294670.418000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.418000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.418000] ACPI: bus type ide registered
[4294670.423000] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[4294670.423000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[4294670.423000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[4294670.423000] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 20
[4294670.423000] PCI: Via IRQ fixup for 0000:00:0f.1, from 255 to 4
[4294670.423000] VP_IDE: chipset revision 6
[4294670.423000] VP_IDE: not 100% native mode: will probe irqs later
[4294670.423000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[4294670.423000]     ide0: BM-DMA at 0xa800-0xa807, BIOS settings: hda:pio, hdb:pio
[4294670.423000]     ide1: BM-DMA at 0xa808-0xa80f, BIOS settings: hdc:pio, hdd:pio
[4294670.423000] Probing IDE interface ide0...
[4294670.807000] hda: WDC WD200EB-00BHF0, ATA DISK drive
[4294671.062000] hdb: QUANTUM FIREBALL EX10.2A, ATA DISK drive
[4294671.115000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.115000] Probing IDE interface ide1...
[4294671.907000] hdc: LITE-ON LTR-52327S, ATAPI CD/DVD-ROM drive
[4294672.519000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.519000] Probing IDE interface ide2...
[4294673.032000] Probing IDE interface ide3...
[4294673.544000] Probing IDE interface ide4...
[4294674.056000] Probing IDE interface ide5...
[4294674.570000] hda: max request size: 128KiB
[4294674.595000] hda: Host Protected Area detected.
[4294674.595000]        current capacity is 39096127 sectors (20017 MB)
[4294674.595000]        native  capacity is 39102336 sectors (20020 MB)
[4294674.597000] hda: Host Protected Area disabled.
[4294674.597000] hda: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(100)
[4294674.597000] hda: cache flushes not supported
[4294674.597000]  /dev/ide/host0/bus0/target0/lun0: p1
[4294674.599000] hdb: max request size: 128KiB
[4294674.609000] hdb: 20044080 sectors (10262 MB) w/418KiB Cache, CHS=19885/16/63, UDMA(33)
[4294674.609000] hdb: cache flushes not supported
[4294674.609000]  /dev/ide/host0/bus0/target1/lun0: p2 < p5 p6 p7 >
[4294674.645000] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[4294674.645000] Uniform CD-ROM driver Revision: 3.20
[4294674.930000] Attempting manual resume
[4294674.938000] swsusp: Suspend partition has wrong signature?
[4294674.959000] SCSI subsystem initialized
[4294674.959000] libata version 1.11 loaded.
[4294674.960000] sata_via version 1.1
[4294674.960000] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 20
[4294674.960000] PCI: Via IRQ fixup for 0000:00:0f.0, from 11 to 4
[4294674.960000] sata_via(0000:00:0f.0): routed to hard irq line 4
[4294674.960000] ata1: SATA max UDMA/133 cmd 0x9000 ctl 0x9402 bmdma 0xA000 irq 20
[4294674.960000] ata2: SATA max UDMA/133 cmd 0x9800 ctl 0x9C02 bmdma 0xA008 irq 20
[4294675.161000] ata1: no device found (phy stat 00000000)
[4294675.161000] scsi0 : sata_via
[4294675.362000] ata2: no device found (phy stat 00000000)
[4294675.362000] scsi1 : sata_via
[4294675.377000] usbcore: registered new driver usbfs
[4294675.377000] usbcore: registered new driver hub
[4294675.378000] USB Universal Host Controller Interface driver v2.2
[4294675.378000] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[4294675.378000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[4294675.378000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[4294675.378000] PCI: Via IRQ fixup for 0000:00:10.0, from 10 to 5
[4294675.378000] uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
[4294675.440000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[4294675.440000] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000ac00
[4294675.440000] hub 1-0:1.0: USB hub found
[4294675.440000] hub 1-0:1.0: 2 ports detected
[4294675.443000] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[4294675.443000] PCI: Via IRQ fixup for 0000:00:10.1, from 10 to 5
[4294675.443000] uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
[4294675.505000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[4294675.505000] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000b000
[4294675.505000] hub 2-0:1.0: USB hub found
[4294675.505000] hub 2-0:1.0: 2 ports detected
[4294675.508000] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[4294675.508000] uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
[4294675.570000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[4294675.570000] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000b400
[4294675.570000] hub 3-0:1.0: USB hub found
[4294675.570000] hub 3-0:1.0: 2 ports detected
[4294675.573000] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[4294675.573000] uhci_hcd 0000:00:10.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#4)
[4294675.609000] usb 1-1: new full speed USB device using uhci_hcd and address 2[4294675.635000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[4294675.635000] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000b800
[4294675.635000] hub 4-0:1.0: USB hub found
[4294675.635000] hub 4-0:1.0: 2 ports detected
[4294675.663000] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[4294675.663000] PCI: Via IRQ fixup for 0000:00:10.4, from 11 to 5
[4294675.663000] ehci_hcd 0000:00:10.4: VIA Technologies, Inc. USB 2.0
[4294675.663000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[4294675.663000] ehci_hcd 0000:00:10.4: irq 21, io mem 0xe2000000
[4294675.663000] ehci_hcd 0000:00:10.4: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294675.663000] hub 5-0:1.0: USB hub found
[4294675.663000] hub 5-0:1.0: 8 ports detected
[4294675.703000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294675.703000] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[4294675.703000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[4294675.703000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 23
[4294675.703000] PCI: Via IRQ fixup for 0000:00:12.0, from 10 to 7
[4294675.703000] eth0: VIA Rhine II at 0x1c000, 00:0f:ea:fa:fb:f2, IRQ 23.
[4294675.704000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[4294676.859000] usb 1-1: new full speed USB device using uhci_hcd and address 3[4294677.726000] Initializing USB Mass Storage driver...
[4294677.728000] scsi2 : SCSI emulation for USB Mass Storage devices
[4294677.728000] usb-storage: device found at 3
[4294677.728000] usb-storage: waiting for device to settle before scanning
[4294677.728000] usbcore: registered new driver usb-storage
[4294677.728000] USB Mass Storage support registered.
[4294678.050000] ACPI: CPU0 (power states: C1[C1])
[4294678.292000] Attempting manual resume
[4294678.292000] swsusp: Suspend partition has wrong signature?
[4294678.315000] kjournald starting.  Commit interval 5 seconds
[4294678.315000] EXT3-fs: mounted filesystem with ordered data mode.
[4294680.447000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294682.728000]   Vendor: Sandisk   Model: ImageMate SDDR-0  Rev: 0100
[4294682.728000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294682.768000] usb-storage: device scan complete
[4294684.514000] Adding 506008k swap on /dev/hdb5.  Priority:-1 extents:1
[4294684.941000] EXT3 FS on hdb6, internal journal
[4294696.662000] parport: PnPBIOS parport detected.
[4294696.662000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[4294696.748000] lp0: using parport0 (interrupt-driven).
[4294696.775000] mice: PS/2 mouse device common for all mice
[4294697.024000] logips2pp: Detected unknown logitech mouse model 86
[4294697.089000] input: ImExPS/2 Logitech Explorer Mouse on isa0060/serio1
[4294697.436000] ts: Compaq touchscreen protocol output
[4294700.232000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294702.514000] cdrom: hdc: mrw address space DMA selected
[4294712.500000] kjournald starting.  Commit interval 5 seconds
[4294712.500000] EXT3 FS on hdb7, internal journal
[4294712.500000] EXT3-fs: mounted filesystem with ordered data mode.
[4294712.509000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4294712.540000] NTFS volume version 3.1.
[4294714.098000] Linux agpgart interface v0.101 (c) Dave Jones
[4294714.105000] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[4294714.124000] agpgart: AGP aperture is 128M @ 0xd0000000
[4294714.191000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294714.201000] shpchp: shpc_init : shpc_cap_offset == 0
[4294714.201000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294714.691000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[4294714.691000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[4294714.691000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 22
[4294714.691000] PCI: Via IRQ fixup for 0000:00:11.5, from 11 to 6
[4294714.692000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294716.592000] sddr09: could not read card info
[4294716.598000] sddr09: could not read card info
[4294716.598000] sda: test WP failed, assume Write Enabled
[4294716.598000] sda: assuming drive cache: write through
[4294716.599000] Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
[4294718.282000] Real Time Clock Driver v1.12
[4294718.310000] input: PC Speaker
[4294718.427000] Floppy drive(s): fd0 is 1.44M
[4294718.442000] FDC 0 is a post-1991 82077
[4294720.096000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294721.595000] NET: Registered protocol family 10
[4294721.596000] Disabled Privacy Extensions on device c02eb280(lo)
[4294721.596000] IPv6 over IPv4 tunneling driver
[4294723.436000] ACPI: Power Button (FF) [PWRF]
[4294723.436000] ACPI: Power Button (CM) [PWRB]
[4294723.516000] ibm_acpi: ec object not found
[4294732.079000] eth0: no IPv6 routers present
[4294754.001000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294754.001000] apm: overridden by ACPI.
[4294760.698000] Bluetooth: Core ver 2.7
[4294760.698000] NET: Registered protocol family 31
[4294760.698000] Bluetooth: HCI device and connection manager initialized
[4294760.698000] Bluetooth: HCI socket layer initialized
[4294760.833000] Bluetooth: L2CAP ver 2.7
[4294760.833000] Bluetooth: L2CAP socket layer initialized
[4294760.998000] Bluetooth: RFCOMM ver 1.5
[4294760.998000] Bluetooth: RFCOMM socket layer initialized
[4294760.998000] Bluetooth: RFCOMM TTY layer initialized
[4294787.409000] sddr09: could not read card info
[4294787.415000] sddr09: could not read card info
[4294787.415000] sda: test WP failed, assume Write Enabled
[4294787.415000] sda: assuming drive cache: write through
[4295213.189000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295213.189000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295213.889000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295213.889000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295215.022000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295215.022000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295215.164000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295215.164000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295242.436000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295242.436000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295243.424000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295243.424000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295243.580000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295243.580000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295243.745000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295243.745000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295243.803000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295243.803000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295243.919000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295243.919000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295243.974000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295243.974000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295244.087000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295244.087000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295244.360000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295244.360000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295244.529000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295244.529000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295246.180000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295246.180000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295246.319000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295246.319000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295248.286000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295248.286000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295248.429000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295248.429000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295248.505000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295248.505000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295248.636000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295248.636000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

```


help is aprecated

---

