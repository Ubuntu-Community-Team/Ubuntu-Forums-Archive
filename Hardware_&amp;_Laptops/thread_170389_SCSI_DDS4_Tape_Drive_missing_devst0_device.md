---
title: "SCSI DDS4 Tape Drive: missing /dev/st0 device"
date: 2006-05-04
forum: Hardware &amp; Laptops
---

### Post by carpetsloth on 2006-05-04
Hello all,

I have an Adaptec 29160 SCSI card connected to a Seagate 06240-XXX DAT drive. The SCSI card detects the tape drive and it shows up in dmesg but for some reason it's not getting a device in /dev/. 

I previously had a Seagate DDS3 Tape drive in this machine and it worked fine. My hunch is that it's related to Kernel 2.6 or udev. When I boot off a Fedora Core4 cd in rescue mode I again don't have a device for the tape drive in /dev. But when I boot from a RedHat 9 CD in rescue mode I can see the proper /dev/st0 device and I can read/write to tapes no problem. Also the tape drive works in freebsd and windows no problem.

Anyway, here's the output of uname and dmesg on my Ubuntu machine. Any hints would be great!
> 
 > uname -a
Linux pinky 2.6.12-10-386 #1 Sat Mar 11 16:13:17 UTC 2006 i686 GNU/Linux


> 
May  4 14:19:42 localhost kernel: [4295514.286000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
May  4 14:19:42 localhost kernel: [4295514.286000] apm: disabled on user request.
May  4 14:19:46 localhost kernel: Kernel logging (proc) stopped.
May  4 14:19:46 localhost kernel: Kernel log daemon terminating.
May  4 14:19:46 localhost exiting on signal 15
May  4 14:49:58 localhost syslogd 1.4.1#17ubuntu3: restart.
May  4 14:49:58 localhost kernel: Inspecting /boot/System.map-2.6.12-10-386
May  4 14:49:58 localhost kernel: Loaded 29010 symbols from /boot/System.map-2.6.12-10-386.
May  4 14:49:58 localhost kernel: Symbols match kernel version 2.6.12.
May  4 14:49:58 localhost kernel: No module symbols loaded - kernel modules not enabled.
May  4 14:49:58 localhost kernel: errupt routing
May  4 14:49:58 localhost kernel: [4294670.493000] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  4 14:49:58 localhost kernel: [4294670.493000] PCI: Probing PCI hardware (bus 00)
May  4 14:49:58 localhost kernel: [4294670.493000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
May  4 14:49:58 localhost kernel: [4294670.493000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
May  4 14:49:58 localhost kernel: [4294670.535000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12) *5
May  4 14:49:58 localhost kernel: [4294670.535000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 *10 11 12)
May  4 14:49:58 localhost kernel: [4294670.535000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
May  4 14:49:58 localhost kernel: [4294670.536000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
May  4 14:49:58 localhost kernel: [4294670.536000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
May  4 14:49:58 localhost kernel: [4294670.536000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
May  4 14:49:58 localhost kernel: [4294670.536000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
May  4 14:49:58 localhost kernel: [4294670.537000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
May  4 14:49:58 localhost kernel: [4294670.537000] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
May  4 14:49:58 localhost kernel: [4294670.537000] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
May  4 14:49:58 localhost kernel: [4294670.538000] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
May  4 14:49:58 localhost kernel: [4294670.538000] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
May  4 14:49:58 localhost kernel: [4294670.540000] Linux Plug and Play Support v0.97 (c) Adam Belay
May  4 14:49:58 localhost kernel: [4294670.540000] pnp: PnP ACPI init
May  4 14:49:58 localhost kernel: [4294670.544000] pnp: PnP ACPI: found 11 devices
May  4 14:49:58 localhost kernel: [4294670.544000] PnPBIOS: Disabled by ACPI PNP
May  4 14:49:58 localhost kernel: [4294670.544000] PCI: Using ACPI for IRQ routing
May  4 14:49:58 localhost kernel: [4294670.544000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May  4 14:49:58 localhost kernel: [4294670.573000] pnp: 00:01: ioport range 0x4000-0x407f could not be reserved
May  4 14:49:58 localhost kernel: [4294670.573000] pnp: 00:01: ioport range 0x5000-0x500f has been reserved
May  4 14:49:58 localhost kernel: [4294670.573000] audit: initializing netlink socket (disabled)
May  4 14:49:58 localhost kernel: [4294670.573000] audit: initialized
May  4 14:49:58 localhost kernel: [4294670.573000] VFS: Disk quotas dquot_6.5.1
May  4 14:49:58 localhost kernel: [4294670.573000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  4 14:49:58 localhost kernel: [4294670.573000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
May  4 14:49:58 localhost kernel: [4294670.573000] devfs: boot_options: 0x0
May  4 14:49:58 localhost kernel: [4294670.573000] Initializing Cryptographic API
May  4 14:49:58 localhost kernel: [4294670.574000] isapnp: Scanning for PnP cards...
May  4 14:49:58 localhost kernel: [4294670.926000] isapnp: No Plug & Play device found
May  4 14:49:58 localhost kernel: [4294670.941000] PNP: PS/2 controller doesn't have KBD irq; using default 0x1
May  4 14:49:58 localhost kernel: [4294670.941000] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 1,12
May  4 14:49:58 localhost kernel: [4294670.941000] serio: i8042 AUX port at 0x60,0x64 irq 12
May  4 14:49:58 localhost kernel: [4294670.941000] serio: i8042 KBD port at 0x60,0x64 irq 1
May  4 14:49:58 localhost kernel: [4294670.941000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
May  4 14:49:58 localhost kernel: [4294670.941000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  4 14:49:58 localhost kernel: [4294670.943000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  4 14:49:58 localhost kernel: [4294670.943000] io scheduler noop registered
May  4 14:49:58 localhost kernel: [4294670.943000] io scheduler anticipatory registered
May  4 14:49:58 localhost kernel: [4294670.943000] io scheduler deadline registered
May  4 14:49:58 localhost kernel: [4294670.943000] io scheduler cfq registered
May  4 14:49:58 localhost kernel: [4294670.943000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May  4 14:49:58 localhost kernel: [4294670.944000] EISA: Probing bus 0 at eisa.0
May  4 14:49:58 localhost kernel: [4294670.944000] Cannot allocate resource for EISA slot 4
May  4 14:49:58 localhost kernel: [4294670.944000] Cannot allocate resource for EISA slot 5
May  4 14:49:58 localhost kernel: [4294670.944000] EISA: Detected 0 cards.
May  4 14:49:58 localhost kernel: [4294670.944000] NET: Registered protocol family 2
May  4 14:49:58 localhost kernel: [4294670.954000] IP: routing cache hash table of 4096 buckets, 32Kbytes
May  4 14:49:58 localhost kernel: [4294670.954000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
May  4 14:49:58 localhost kernel: [4294670.954000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
May  4 14:49:58 localhost kernel: [4294670.955000] TCP: Hash tables configured (established 32768 bind 32768)
May  4 14:49:58 localhost kernel: [4294670.955000] NET: Registered protocol family 8
May  4 14:49:58 localhost kernel: [4294670.955000] NET: Registered protocol family 20
May  4 14:49:58 localhost kernel: [4294670.955000] ACPI wakeup devices:
May  4 14:49:58 localhost kernel: [4294670.955000] PCI0 USB0 USB1 USB2 USB6 USB7 USB8 USB9 LAN0 MC97 UAR1 ECP1
May  4 14:49:58 localhost kernel: [4294670.955000] ACPI: (supports S0 S3 S4 S5)
May  4 14:49:58 localhost kernel: [4294670.955000] Freeing unused kernel memory: 224k freed
May  4 14:49:58 localhost kernel: [4294670.966000] vga16fb: mapped to 0xc00a0000
May  4 14:49:58 localhost kernel: [4294671.096000] Console: switching to colour frame buffer device 80x30
May  4 14:49:58 localhost kernel: [4294671.096000] fb0: VGA16 VGA frame buffer device
May  4 14:49:58 localhost kernel: [4294672.230000] Capability LSM initialized
May  4 14:49:58 localhost kernel: [4294672.242000] NET: Registered protocol family 1
May  4 14:49:58 localhost kernel: [4294672.255000] SCSI subsystem initialized
May  4 14:49:58 localhost kernel: [4294672.258000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 18
May  4 14:49:58 localhost kernel: [4294672.469000] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 6.2.36
May  4 14:49:58 localhost kernel: [4294672.469000]         <Adaptec 29160 Ultra160 SCSI adapter>
May  4 14:49:58 localhost kernel: [4294672.469000]         aic7892: Ultra160 Wide Channel A, SCSI Id=7, 32/253 SCBs
May  4 14:49:58 localhost kernel: [4294672.469000]
May  4 14:49:58 localhost kernel: [4294687.469000]   Vendor: FUJITSU   Model: MAT3073NP         Rev: 0107
May  4 14:49:58 localhost kernel: [4294687.469000]   Type:   Direct-Access                      ANSI SCSI revision: 03
May  4 14:49:58 localhost kernel: [4294687.469000] scsi0:A:0:0: Tagged Queuing enabled.  Depth 8
May  4 14:49:58 localhost kernel: [4294687.469000]  target0:0:0: Beginning Domain Validation
May  4 14:49:58 localhost kernel: [4294687.471000] WIDTH IS 1
May  4 14:49:58 localhost kernel: [4294687.472000] (scsi0:A:0): 6.600MB/s transfers (16bit)
May  4 14:49:58 localhost kernel: [4294687.477000] (scsi0:A:0): 160.000MB/s transfers (80.000MHz DT, offset 127, 16bit)
May  4 14:49:58 localhost kernel: [4294687.480000]  target0:0:0: Ending Domain Validation
May  4 14:49:58 localhost kernel: [4294688.763000]   Vendor: SEAGATE   Model: DAT    06240-XXX  Rev: 8040
May  4 14:49:58 localhost kernel: [4294688.763000]   Type:   Sequential-Access                  ANSI SCSI revision: 03
May  4 14:49:58 localhost kernel: [4294688.763000]  target0:0:6: Beginning Domain Validation
May  4 14:49:58 localhost kernel: [4294688.768000] WIDTH IS 1
May  4 14:49:58 localhost kernel: [4294688.769000] (scsi0:A:6): 6.600MB/s transfers (16bit)
May  4 14:49:58 localhost kernel: [4294688.787000]  target0:0:6: Domain Validation skipping write tests
May  4 14:49:58 localhost kernel: [4294688.788000] (scsi0:A:6): 40.000MB/s transfers (20.000MHz, offset 32, 16bit)
May  4 14:49:58 localhost kernel: [4294688.793000]  target0:0:6: Ending Domain Validation
May  4 14:49:58 localhost kernel: [4294690.860000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
May  4 14:49:58 localhost kernel: [4294690.860000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
May  4 14:49:58 localhost kernel: [4294690.860000] ACPI: bus type ide registered
May  4 14:49:58 localhost kernel: [4294690.867000] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
May  4 14:49:58 localhost kernel: [4294690.868000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
May  4 14:49:58 localhost kernel: [4294690.868000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
May  4 14:49:58 localhost kernel: [4294690.868000] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 20
May  4 14:49:58 localhost kernel: [4294690.868000] PCI: Via IRQ fixup for 0000:00:0f.1, from 255 to 4
May  4 14:49:58 localhost kernel: [4294690.868000] VP_IDE: chipset revision 6
May  4 14:49:58 localhost kernel: [4294690.868000] VP_IDE: not 100%% native mode: will probe irqs later
May  4 14:49:58 localhost kernel: [4294690.868000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
May  4 14:49:58 localhost kernel: [4294690.868000]     ide0: BM-DMA at 0xb000-0xb007, BIOS settings: hda:DMA, hdb:pio
May  4 14:49:58 localhost kernel: [4294690.868000]     ide1: BM-DMA at 0xb008-0xb00f, BIOS settings: hdc:DMA, hdd:pio
May  4 14:49:58 localhost kernel: [4294691.252000] hda: WDC WD800JB-00CRA1, ATA DISK drive
May  4 14:49:58 localhost kernel: [4294691.865000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
May  4 14:49:58 localhost kernel: [4294692.657000] hdc: TOSHIBA DVD-ROM SD-M1212, ATAPI CD/DVD-ROM drive
May  4 14:49:58 localhost kernel: [4294693.269000] ide1 at 0x170-0x177,0x376 on irq 15
May  4 14:49:58 localhost kernel: [4294695.324000] hda: max request size: 128KiB
May  4 14:49:58 localhost kernel: [4294695.339000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
May  4 14:49:58 localhost kernel: [4294695.339000] hda: cache flushes not supported
May  4 14:49:58 localhost kernel: [4294695.339000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4
May  4 14:49:58 localhost kernel: [4294695.350000] hdc: ATAPI 32X DVD-ROM drive, 256kB Cache
May  4 14:49:58 localhost kernel: [4294695.350000] Uniform CD-ROM driver Revision: 3.20
May  4 14:49:58 localhost kernel: [4294695.361000] SCSI device sda: 143638992 512-byte hdwr sectors (73543 MB)
May  4 14:49:58 localhost kernel: [4294695.362000] SCSI device sda: drive cache: write back
May  4 14:49:58 localhost kernel: [4294695.362000] SCSI device sda: 143638992 512-byte hdwr sectors (73543 MB)
May  4 14:49:58 localhost kernel: [4294695.364000] SCSI device sda: drive cache: write back
May  4 14:49:58 localhost kernel: [4294695.364000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2
May  4 14:49:58 localhost kernel: [4294695.378000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
May  4 14:49:58 localhost kernel: [4294695.659000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
May  4 14:49:58 localhost kernel: [4294695.660000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 16
May  4 14:49:58 localhost kernel: [4294695.660000] PCI: Via IRQ fixup for 0000:00:08.0, from 5 to 0
May  4 14:49:58 localhost kernel: [4294695.670000] eth0: VIA Rhine at 0x19000, 00:50:ba:c6:60:31, IRQ 16.
May  4 14:49:58 localhost kernel: [4294695.676000] eth0: MII PHY found at address 8, status 0x782d advertising 05e1 Link 41e1.
May  4 14:49:58 localhost kernel: [4294695.676000] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
May  4 14:49:58 localhost kernel: [4294695.676000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
May  4 14:49:58 localhost kernel: [4294695.676000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 23
May  4 14:49:58 localhost kernel: [4294695.676000] PCI: Via IRQ fixup for 0000:00:12.0, from 5 to 7
May  4 14:49:58 localhost kernel: [4294695.680000] eth1: VIA Rhine II at 0x1c800, 00:14:2a:4b:64:96, IRQ 23.
May  4 14:49:58 localhost kernel: [4294695.681000] eth1: MII PHY found at address 1, status 0x786d advertising 05e1 Link 0021.
May  4 14:49:58 localhost kernel: [4294695.711000] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 20
May  4 14:49:58 localhost kernel: [4294695.711000] PCI: Via IRQ fixup for 0000:00:0f.0, from 10 to 4
May  4 14:49:58 localhost kernel: [4294695.711000] sata_via(0000:00:0f.0): routed to hard irq line 4
May  4 14:49:58 localhost kernel: [4294695.711000] ata1: SATA max UDMA/133 cmd 0x9800 ctl 0x9C02 bmdma 0xA800 irq 20
May  4 14:49:58 localhost kernel: [4294695.711000] ata2: SATA max UDMA/133 cmd 0xA000 ctl 0xA402 bmdma 0xA808 irq 20
May  4 14:49:58 localhost kernel: [4294695.912000] ata1: no device found (phy stat 00000000)
May  4 14:49:58 localhost kernel: [4294695.912000] scsi1 : sata_via
May  4 14:49:58 localhost kernel: [4294696.113000] ata2: no device found (phy stat 00000000)
May  4 14:49:58 localhost kernel: [4294696.113000] scsi2 : sata_via
May  4 14:49:58 localhost kernel: [4294696.133000] usbcore: registered new driver usbfs
May  4 14:49:58 localhost kernel: [4294696.134000] usbcore: registered new driver hub
May  4 14:49:58 localhost kernel: [4294696.134000] USB Universal Host Controller Interface driver v2.2
May  4 14:49:58 localhost kernel: [4294696.135000] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
May  4 14:49:58 localhost kernel: [4294696.135000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
May  4 14:49:58 localhost kernel: [4294696.135000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
May  4 14:49:58 localhost kernel: [4294696.135000] uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
May  4 14:49:58 localhost kernel: [4294696.197000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
May  4 14:49:58 localhost kernel: [4294696.197000] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000b400
May  4 14:49:58 localhost kernel: [4294696.197000] hub 1-0:1.0: USB hub found
May  4 14:49:58 localhost kernel: [4294696.197000] hub 1-0:1.0: 2 ports detected
May  4 14:49:58 localhost kernel: [4294696.200000] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
May  4 14:49:58 localhost kernel: [4294696.200000] uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
May  4 14:49:58 localhost kernel: [4294696.262000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
May  4 14:49:58 localhost kernel: [4294696.262000] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000b800
May  4 14:49:58 localhost kernel: [4294696.262000] hub 2-0:1.0: USB hub found
May  4 14:49:58 localhost kernel: [4294696.262000] hub 2-0:1.0: 2 ports detected
May  4 14:49:58 localhost kernel: [4294696.265000] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
May  4 14:49:58 localhost kernel: [4294696.265000] PCI: Via IRQ fixup for 0000:00:10.2, from 10 to 5
May  4 14:49:58 localhost kernel: [4294696.265000] uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
May  4 14:49:58 localhost kernel: [4294696.327000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
May  4 14:49:58 localhost kernel: [4294696.327000] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000bc00
May  4 14:49:58 localhost kernel: [4294696.327000] hub 3-0:1.0: USB hub found
May  4 14:49:58 localhost kernel: [4294696.327000] hub 3-0:1.0: 2 ports detected
May  4 14:49:58 localhost kernel: [4294696.330000] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
May  4 14:49:58 localhost kernel: [4294696.330000] PCI: Via IRQ fixup for 0000:00:10.3, from 10 to 5
May  4 14:49:58 localhost kernel: [4294696.330000] uhci_hcd 0000:00:10.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#4)
May  4 14:49:58 localhost kernel: [4294696.392000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
May  4 14:49:58 localhost kernel: [4294696.392000] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000c000
May  4 14:49:58 localhost kernel: [4294696.392000] hub 4-0:1.0: USB hub found
May  4 14:49:58 localhost kernel: [4294696.392000] hub 4-0:1.0: 2 ports detected
May  4 14:49:58 localhost kernel: [4294696.429000] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
May  4 14:49:58 localhost kernel: [4294696.429000] PCI: Via IRQ fixup for 0000:00:10.4, from 11 to 5
May  4 14:49:58 localhost kernel: [4294696.429000] ehci_hcd 0000:00:10.4: VIA Technologies, Inc. USB 2.0
May  4 14:49:58 localhost kernel: [4294696.429000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
May  4 14:49:58 localhost kernel: [4294696.429000] ehci_hcd 0000:00:10.4: irq 21, io mem 0xe3007000
May  4 14:49:58 localhost kernel: [4294696.429000] ehci_hcd 0000:00:10.4: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
May  4 14:49:58 localhost kernel: [4294696.429000] hub 5-0:1.0: USB hub found
May  4 14:49:58 localhost kernel: [4294696.429000] hub 5-0:1.0: 8 ports detected
May  4 14:49:58 localhost kernel: [4294697.381000] usb 2-1: new low speed USB device using uhci_hcd and address 2
May  4 14:49:58 localhost kernel: [4294698.510000] usbcore: registered new driver hiddev
May  4 14:49:58 localhost kernel: [4294698.529000] input: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:10.1-1
May  4 14:49:58 localhost kernel: [4294698.529000] usbcore: registered new driver usbhid
May  4 14:49:58 localhost kernel: [4294698.529000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
May  4 14:49:58 localhost kernel: [4294698.849000] ACPI: Fan [FAN] (on)
May  4 14:49:58 localhost kernel: [4294698.852000] ACPI: CPU0 (power states: C1[C1] C2[C2])
May  4 14:49:58 localhost kernel: [4294699.053000] ACPI: Thermal Zone [THRM] (32 C)
May  4 14:49:58 localhost kernel: [4294699.159000] kjournald starting.  Commit interval 5 seconds
May  4 14:49:58 localhost kernel: [4294699.159000] EXT3-fs: mounted filesystem with ordered data mode.
May  4 14:49:58 localhost kernel: [4294700.023000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
May  4 14:49:58 localhost kernel: [4294702.477000] Adding 803240k swap on /dev/sda2.  Priority:-1 extents:1
May  4 14:49:58 localhost kernel: [4294702.573000] EXT3 FS on sda1, internal journal
May  4 14:49:58 localhost kernel: [4294705.481000] parport: PnPBIOS parport detected.
May  4 14:49:58 localhost kernel: [4294705.481000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
May  4 14:49:58 localhost kernel: [4294705.572000] lp0: using parport0 (interrupt-driven).
May  4 14:49:58 localhost kernel: [4294705.604000] mice: PS/2 mouse device common for all mice
May  4 14:49:58 localhost kernel: [4294705.697000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
May  4 14:49:58 localhost kernel: [4294705.909000] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
May  4 14:49:58 localhost kernel: [4294706.160000] ts: Compaq touchscreen protocol output
May  4 14:49:58 localhost kernel: [4294708.989000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
May  4 14:49:58 localhost kernel: [4294709.484000] cdrom: open failed.
May  4 14:49:58 localhost kernel: [4294710.428000] Linux agpgart interface v0.101 (c) Dave Jones
May  4 14:49:58 localhost kernel: [4294710.439000] agpgart: Detected VIA KM400/KM400A chipset
May  4 14:49:58 localhost kernel: [4294710.482000] agpgart: AGP aperture is 256M @ 0xc0000000
May  4 14:49:58 localhost kernel: [4294710.582000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  4 14:49:58 localhost kernel: [4294710.760000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
May  4 14:49:58 localhost kernel: [4294710.760000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 17
May  4 14:49:58 localhost kernel: [4294710.818000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[e3004000-e30047ff]  Max Packet=[2048]
May  4 14:49:58 localhost kernel: [4294711.637000] via82xx: Assuming DXS channels with 48k fixed sample rate.
May  4 14:49:58 localhost kernel: [4294711.637000]          Please try dxs_support=5 option
May  4 14:49:58 localhost kernel: [4294711.637000]          and report if it works on your machine.
May  4 14:49:58 localhost kernel: [4294711.637000]          For more details, read ALSA-Configuration.txt.
May  4 14:49:58 localhost kernel: [4294711.638000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
May  4 14:49:58 localhost kernel: [4294711.638000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
May  4 14:49:58 localhost kernel: [4294711.638000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 22
May  4 14:49:58 localhost kernel: [4294711.638000] PCI: Via IRQ fixup for 0000:00:11.5, from 11 to 6
May  4 14:49:58 localhost kernel: [4294714.190000] Real Time Clock Driver v1.12
May  4 14:49:58 localhost kernel: [4294714.298000] input: PC Speaker
May  4 14:49:58 localhost kernel: [4294714.402000] Floppy drive(s): fd0 is 1.44M
May  4 14:49:58 localhost kernel: [4294714.423000] FDC 0 is a post-1991 82077
May  4 14:49:58 localhost kernel: [4294715.370000] eth1: link up, 10Mbps, half-duplex, lpa 0x0021
May  4 14:49:58 localhost kernel: [4294715.505000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
May  4 14:49:58 localhost kernel: [4294715.517000] NET: Registered protocol family 17
May  4 14:49:58 localhost kernel: [4294778.741000] ACPI: Power Button (FF) [PWRF]
May  4 14:49:58 localhost kernel: [4294778.741000] ACPI: Power Button (CM) [PWRB]
May  4 14:50:01 localhost hpiod: 0.9.5 accepting connections at 32769...
May  4 14:50:01 localhost hp: unable to open /var/run/hplip/hpssd.port: No such file or directory: prnt/hpijs/hplip_api.c 84
May  4 14:50:01 localhost hp: unable to connect hpssd socket 50002: Connection refused: prnt/hpijs/hplip_api.c 710
May  4 14:50:02 localhost kernel: [4294783.873000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
May  4 14:50:02 localhost kernel: [4294783.873000] apm: overridden by ACPI.
May  4 14:50:06 localhost kernel: [4294787.434000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
May  4 14:50:06 localhost kernel: [4294787.444000] powernow: Trying ACPI perflib
May  4 14:50:06 localhost kernel: [4294787.444000] powernow: ACPI perflib can not be used in this platform
May  4 14:50:06 localhost kernel: [4294787.444000] powernow: ACPI and legacy methods failed
May  4 14:50:06 localhost kernel: [4294787.444000] powernow: See [http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.shtml](http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.shtml)
May  4 14:50:07 localhost kernel: [4294787.976000] NET: Registered protocol family 10
May  4 14:50:07 localhost kernel: [4294787.976000] Disabled Privacy Extensions on device c02eb280(lo)
May  4 14:50:07 localhost kernel: [4294787.976000] IPv6 over IPv4 tunneling driver
May  4 14:50:07 localhost kernel: [4294788.245000] Bluetooth: Core ver 2.7
May  4 14:50:07 localhost kernel: [4294788.245000] NET: Registered protocol family 31
May  4 14:50:07 localhost kernel: [4294788.245000] Bluetooth: HCI device and connection manager initialized
May  4 14:50:07 localhost kernel: [4294788.245000] Bluetooth: HCI socket layer initialized
May  4 14:50:07 localhost kernel: [4294788.267000] Bluetooth: L2CAP ver 2.7
May  4 14:50:07 localhost kernel: [4294788.267000] Bluetooth: L2CAP socket layer initialized
May  4 14:50:07 localhost kernel: [4294788.288000] Bluetooth: RFCOMM ver 1.5
May  4 14:50:07 localhost kernel: [4294788.288000] Bluetooth: RFCOMM socket layer initialized
May  4 14:50:07 localhost kernel: [4294788.288000] Bluetooth: RFCOMM TTY layer initialized
May  4 14:50:50 localhost gconfd (cswanson-8120): starting (version 2.12.0), pid 8120 user 'cswanson'


---

### Post by mikeyman on 2006-05-16
You are correct in suspecting the Udev in the new kernels. You have to edit /etc/modules and add st to the end. I have a changer, so I need to add sg also. This will only take effect on a reboot. You can load the proper modules by typing sudo modprobe st.

Cheers!

Mike

---

