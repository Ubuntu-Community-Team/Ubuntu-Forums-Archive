---
title: "Finding, mounting and retrieving data from old hard drive"
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by IainT on 2007-03-25
Hi,

I'm trying to get some data off an old Western Digital 31600 hard drive which has win95 on it.

Can't seem to get it to run (played with bios settings, jumpers etc) as a slave to a main hard drive. So I've connected it alone, and am typing this from a Dapper livecd that I had lying around.

Dapper has not automagically mounted it, fdisk -l doesn't find it. dmesg gives me (sorry if this is irrelevant, I'm not good at all this)

```
[17179636.648000] hub 4-0:1.0: USB hub found
[17179636.648000] hub 4-0:1.0: 6 ports detected
[17179636.680000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179637.396000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[17179637.396000] hdb: command error: error=0x50 { LastFailedSense=0x05 }
[17179637.396000] ide: failed opcode was: unknown
[17179637.396000] end_request: I/O error, dev hdb, sector 1430336
[17179637.548000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[17179637.548000] hdb: command error: error=0x50 { LastFailedSense=0x05 }
[17179637.548000] ide: failed opcode was: unknown
[17179637.548000] end_request: I/O error, dev hdb, sector 1430336
[17179637.624000] usb 4-1: new high speed USB device using ehci_hcd and address 2
[17179637.700000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[17179637.700000] hdb: command error: error=0x50 { LastFailedSense=0x05 }
[17179637.700000] ide: failed opcode was: unknown
[17179637.700000] end_request: I/O error, dev hdb, sector 1430336
[17179637.768000] SCSI subsystem initialized
[17179637.772000] Initializing USB Mass Storage driver...
[17179637.860000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[17179637.860000] hdb: command error: error=0x50 { LastFailedSense=0x05 }
[17179637.860000] ide: failed opcode was: unknown
[17179637.860000] end_request: I/O error, dev hdb, sector 1430336
[17179637.940000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179637.940000] usb-storage: device found at 2
[17179637.940000] usb-storage: waiting for device to settle before scanning
[17179637.940000] usbcore: registered new driver usb-storage
[17179637.940000] USB Mass Storage support registered.
[17179638.004000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[17179638.004000] hdb: command error: error=0x50 { LastFailedSense=0x05 }
[17179638.004000] ide: failed opcode was: unknown
[17179638.004000] end_request: I/O error, dev hdb, sector 1430336
[17179638.172000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[17179638.172000] hdb: command error: error=0x50 { LastFailedSense=0x05 }
[17179638.172000] ide: failed opcode was: unknown
[17179638.172000] end_request: I/O error, dev hdb, sector 1430336
[17179638.296000] usb 2-2: new low speed USB device using uhci_hcd and address 2[17179638.472000] usbcore: registered new driver hiddev
[17179638.492000] input: PS/2+USB Mouse as /class/input/input1
[17179638.492000] input: USB HID v1.00 Mouse [PS/2+USB Mouse] on usb-0000:00:10.1-2
[17179638.492000] usbcore: registered new driver usbhid
[17179638.492000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179638.496000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179638.520000] ISO 9660 Extensions: RRIP_1991A
[17179638.556000] loop: loaded (max 8 devices)
[17179638.576000] Registering unionfs 1.1.2
[17179638.628000] squashfs: version 3.0prerelease (2006/1/24) Phillip Lougher
[17179642.940000]   Vendor: Mass      Model: Storage           Rev: 0.00
[17179642.940000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179642.948000] Driver 'sd' needs updating - please use bus_type methods
[17179642.952000] SCSI device sda: 989184 512-byte hdwr sectors (506 MB)
[17179642.952000] usb-storage: device scan complete
[17179642.952000] sda: Write Protect is off
[17179642.952000] sda: Mode Sense: 00 00 00 00
[17179642.952000] sda: assuming drive cache: write through
[17179642.964000] sd 0:0:0:0: ioctl_internal_command return code = 8000002
[17179642.964000]    : Current: sense key: No Sense
[17179642.964000]     Additional sense: No additional sense information
[17179642.964000] SCSI device sda: 989184 512-byte hdwr sectors (506 MB)
[17179642.964000] sda: Write Protect is off
[17179642.964000] sda: Mode Sense: 00 00 00 00
[17179642.964000] sda: assuming drive cache: write through
[17179642.964000]  sda: sda1
[17179642.968000] sd 0:0:0:0: Attached scsi removable disk sda
[17179642.980000] sd 0:0:0:0: ioctl_internal_command return code = 8000002
[17179642.980000]    : Current: sense key: No Sense
[17179642.980000]     Additional sense: No additional sense information
[17179654.668000] sd 0:0:0:0: ioctl_internal_command return code = 8000002
[17179654.668000]    : Current: sense key: No Sense
[17179654.668000]     Additional sense: No additional sense information
[17179670.488000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179670.492000] **** SET: Misaligned resource pointer: ed321aa2 Type 07 Len 0
[17179670.492000] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[17179670.492000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[17179670.492000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 185
[17179670.496000] eth0: VIA Rhine II at 0x1ec00, 00:0a:e6:d0:82:d5, IRQ 185.
[17179670.496000] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[17179691.824000] end_request: I/O error, dev hdd, sector 3172992
[17179691.824000] printk: 67 messages suppressed.
[17179691.824000] Buffer I/O error on device hdd, logical block 396624
[17179691.824000] end_request: I/O error, dev hdd, sector 3172992
[17179691.824000] Buffer I/O error on device hdd, logical block 396624
[17179691.824000] end_request: I/O error, dev hdd, sector 3173176
[17179691.824000] Buffer I/O error on device hdd, logical block 396647
[17179691.824000] end_request: I/O error, dev hdd, sector 3173176
[17179691.824000] Buffer I/O error on device hdd, logical block 396647
[17179691.824000] end_request: I/O error, dev hdd, sector 3173176
[17179691.824000] Buffer I/O error on device hdd, logical block 396647
[17179691.824000] end_request: I/O error, dev hdd, sector 3173176
[17179691.824000] Buffer I/O error on device hdd, logical block 396647
[17179691.824000] end_request: I/O error, dev hdd, sector 3173176
[17179691.824000] Buffer I/O error on device hdd, logical block 396647
[17179691.824000] end_request: I/O error, dev hdd, sector 3173176
[17179691.824000] Buffer I/O error on device hdd, logical block 396647
[17179691.824000] end_request: I/O error, dev hdd, sector 3173120
[17179691.824000] Buffer I/O error on device hdd, logical block 396640
[17179691.824000] end_request: I/O error, dev hdd, sector 3173120
[17179691.824000] Buffer I/O error on device hdd, logical block 396640
[17179691.824000] end_request: I/O error, dev hdd, sector 3173168
[17179691.824000] end_request: I/O error, dev hdd, sector 3173168
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 8
[17179691.824000] end_request: I/O error, dev hdd, sector 16
[17179691.824000] end_request: I/O error, dev hdd, sector 24
[17179691.824000] end_request: I/O error, dev hdd, sector 32
[17179691.824000] end_request: I/O error, dev hdd, sector 40
[17179691.824000] end_request: I/O error, dev hdd, sector 48
[17179691.824000] end_request: I/O error, dev hdd, sector 56
[17179691.824000] end_request: I/O error, dev hdd, sector 64
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 72
[17179691.824000] end_request: I/O error, dev hdd, sector 80
[17179691.824000] end_request: I/O error, dev hdd, sector 88
[17179691.824000] end_request: I/O error, dev hdd, sector 96
[17179691.824000] end_request: I/O error, dev hdd, sector 104
[17179691.824000] end_request: I/O error, dev hdd, sector 112
[17179691.824000] end_request: I/O error, dev hdd, sector 120
[17179691.824000] end_request: I/O error, dev hdd, sector 128
[17179691.824000] end_request: I/O error, dev hdd, sector 136
[17179691.824000] end_request: I/O error, dev hdd, sector 144
[17179691.824000] end_request: I/O error, dev hdd, sector 152
[17179691.824000] end_request: I/O error, dev hdd, sector 160
[17179691.824000] end_request: I/O error, dev hdd, sector 168
[17179691.824000] end_request: I/O error, dev hdd, sector 176
[17179691.824000] end_request: I/O error, dev hdd, sector 184
[17179691.824000] end_request: I/O error, dev hdd, sector 192
[17179691.824000] end_request: I/O error, dev hdd, sector 200
[17179691.824000] end_request: I/O error, dev hdd, sector 208
[17179691.824000] end_request: I/O error, dev hdd, sector 216
[17179691.824000] end_request: I/O error, dev hdd, sector 224
[17179691.824000] end_request: I/O error, dev hdd, sector 232
[17179691.824000] end_request: I/O error, dev hdd, sector 240
[17179691.824000] end_request: I/O error, dev hdd, sector 248
[17179691.824000] end_request: I/O error, dev hdd, sector 256
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179691.824000] end_request: I/O error, dev hdd, sector 0
[17179692.384000] ts: Compaq touchscreen protocol output
[17179692.528000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179692.852000] sd 0:0:0:0: ioctl_internal_command return code = 8000002
[17179692.852000]    : Current: sense key: No Sense
[17179692.852000]     Additional sense: No additional sense information
[17179693.560000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179694.640000] NET: Registered protocol family 17
[17179694.888000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179695.148000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179695.376000] irda_init()
[17179695.376000] NET: Registered protocol family 23
[17179696.032000] Linux agpgart interface v0.101 (c) Dave Jones
[17179696.720000] agpgart: Detected VIA PM266/KM266 chipset
[17179696.824000] agpgart: AGP aperture is 128M @ 0xd0000000
[17179696.932000] input: PC Speaker as /class/input/input2
[17179696.940000] **** SET: Misaligned resource pointer: e8eed5c2 Type 07 Len 0
[17179696.940000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[17179696.940000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179696.940000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 193
[17179696.940000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179697.044000] Real Time Clock Driver v1.12
[17179697.104000] Floppy drive(s): fd0 is 1.44M
[17179697.144000] FDC 0 is a post-1991 82077
[17179697.212000] parport: PnPBIOS parport detected.
[17179697.212000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179699.164000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179699.164000] md: bitmap version 4.39
[17179699.372000] end_request: I/O error, dev hdd, sector 3172992
[17179699.372000] printk: 59 messages suppressed.
[17179699.372000] Buffer I/O error on device hdd, logical block 396624
[17179699.372000] end_request: I/O error, dev hdd, sector 3172992
[17179699.396000] sd 0:0:0:0: ioctl_internal_command return code = 8000002
[17179699.396000]    : Current: sense key: No Sense
[17179699.396000]     Additional sense: No additional sense information
[17179699.408000] sd 0:0:0:0: ioctl_internal_command return code = 8000002
[17179699.408000]    : Current: sense key: No Sense
[17179699.408000]     Additional sense: No additional sense information
[17179699.592000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179700.060000] sd 0:0:0:0: ioctl_internal_command return code = 8000002
[17179700.060000]    : Current: sense key: No Sense
[17179700.060000]     Additional sense: No additional sense information
[17179700.068000] sd 0:0:0:0: ioctl_internal_command return code = 8000002
[17179700.068000]    : Current: sense key: No Sense
[17179700.068000]     Additional sense: No additional sense information
[17179700.068000] sd 0:0:0:0: ioctl_internal_command return code = 8000002
[17179700.068000]    : Current: sense key: No Sense
[17179700.068000]     Additional sense: No additional sense information
[17179700.072000] sd 0:0:0:0: ioctl_internal_command return code = 8000002
[17179700.072000]    : Current: sense key: No Sense
[17179700.072000]     Additional sense: No additional sense information
[17179700.072000] sd 0:0:0:0: ioctl_internal_command return code = 8000002
[17179700.072000]    : Current: sense key: No Sense
[17179700.072000]     Additional sense: No additional sense information
[17179700.076000] end_request: I/O error, dev hdd, sector 0
[17179700.076000] end_request: I/O error, dev hdd, sector 8
[17179700.076000] end_request: I/O error, dev hdd, sector 16
[17179700.076000] end_request: I/O error, dev hdd, sector 24
[17179700.076000] end_request: I/O error, dev hdd, sector 32
[17179700.076000] end_request: I/O error, dev hdd, sector 40
[17179700.076000] end_request: I/O error, dev hdd, sector 48
[17179700.076000] end_request: I/O error, dev hdd, sector 56
[17179700.076000] end_request: I/O error, dev hdd, sector 0
[17179700.076000] end_request: I/O error, dev hdd, sector 3172992
[17179700.076000] end_request: I/O error, dev hdd, sector 0
[17179700.088000] sd 0:0:0:0: ioctl_internal_command return code = 8000002
[17179700.088000]    : Current: sense key: No Sense
[17179700.088000]     Additional sense: No additional sense information
[17179700.088000] end_request: I/O error, dev hdd, sector 0
[17179702.100000] NET: Registered protocol family 10
[17179702.100000] lo: Disabled Privacy Extensions
[17179702.100000] IPv6 over IPv4 tunneling driver
[17179702.208000] cdrom: hdb: mrw address space DMA selected
[17179702.220000] sd 0:0:0:0: ioctl_internal_command return code = 8000002
[17179702.220000]    : Current: sense key: No Sense
[17179702.220000]     Additional sense: No additional sense information
[17179702.220000] end_request: I/O error, dev hdd, sector 1
[17179702.220000] end_request: I/O error, dev hdd, sector 2
[17179702.220000] end_request: I/O error, dev hdd, sector 0
[17179702.224000] end_request: I/O error, dev hdd, sector 0
[17179702.224000] end_request: I/O error, dev hdd, sector 3173183
[17179702.224000] end_request: I/O error, dev hdd, sector 0
[17179702.224000] end_request: I/O error, dev hdd, sector 1
[17179702.224000] end_request: I/O error, dev hdd, sector 3173183
[17179702.228000] end_request: I/O error, dev hdd, sector 0
[17179702.228000] end_request: I/O error, dev hdd, sector 0
[17179702.228000] end_request: I/O error, dev hdd, sector 0
[17179702.228000] end_request: I/O error, dev hdd, sector 1
[17179702.232000] end_request: I/O error, dev hdd, sector 0
[17179702.232000] end_request: I/O error, dev hdd, sector 3172992
[17179702.232000] printk: 10 messages suppressed.
[17179702.232000] Buffer I/O error on device hdd, logical block 396624
[17179702.232000] end_request: I/O error, dev hdd, sector 3172992
[17179702.232000] end_request: I/O error, dev hdd, sector 3173168
[17179702.232000] end_request: I/O error, dev hdd, sector 3173168
[17179702.232000] end_request: I/O error, dev hdd, sector 0
[17179702.232000] end_request: I/O error, dev hdd, sector 8
[17179702.232000] end_request: I/O error, dev hdd, sector 16
[17179702.232000] end_request: I/O error, dev hdd, sector 24
[17179702.232000] end_request: I/O error, dev hdd, sector 32
[17179702.232000] end_request: I/O error, dev hdd, sector 40
[17179702.232000] end_request: I/O error, dev hdd, sector 48
[17179702.232000] end_request: I/O error, dev hdd, sector 56
[17179702.232000] end_request: I/O error, dev hdd, sector 0
[17179702.236000] end_request: I/O error, dev hdd, sector 8
[17179702.236000] end_request: I/O error, dev hdd, sector 8
[17179702.240000] end_request: I/O error, dev hdd, sector 3172992
[17179702.240000] end_request: I/O error, dev hdd, sector 3172992
[17179702.240000] end_request: I/O error, dev hdd, sector 3173168
[17179702.240000] end_request: I/O error, dev hdd, sector 3173168
[17179702.240000] end_request: I/O error, dev hdd, sector 0
[17179702.240000] end_request: I/O error, dev hdd, sector 8
[17179702.240000] end_request: I/O error, dev hdd, sector 16
[17179702.240000] end_request: I/O error, dev hdd, sector 24
[17179702.240000] end_request: I/O error, dev hdd, sector 32
[17179702.240000] end_request: I/O error, dev hdd, sector 40
[17179702.240000] end_request: I/O error, dev hdd, sector 48
[17179702.240000] end_request: I/O error, dev hdd, sector 56
[17179702.240000] end_request: I/O error, dev hdd, sector 0
[17179702.240000] end_request: I/O error, dev hdd, sector 8
[17179702.240000] end_request: I/O error, dev hdd, sector 8
[17179702.240000] end_request: I/O error, dev hdd, sector 3172992
[17179702.240000] end_request: I/O error, dev hdd, sector 3172992
[17179702.240000] end_request: I/O error, dev hdd, sector 3173168
[17179702.240000] end_request: I/O error, dev hdd, sector 3173168
[17179702.240000] end_request: I/O error, dev hdd, sector 0
[17179702.240000] end_request: I/O error, dev hdd, sector 8
[17179702.240000] end_request: I/O error, dev hdd, sector 16
[17179702.240000] end_request: I/O error, dev hdd, sector 24
[17179702.240000] end_request: I/O error, dev hdd, sector 32
[17179702.240000] end_request: I/O error, dev hdd, sector 40
[17179702.240000] end_request: I/O error, dev hdd, sector 48
[17179702.240000] end_request: I/O error, dev hdd, sector 56
[17179702.240000] end_request: I/O error, dev hdd, sector 0
[17179702.240000] end_request: I/O error, dev hdd, sector 8
[17179702.240000] end_request: I/O error, dev hdd, sector 8
[17179702.244000] end_request: I/O error, dev hdd, sector 3172992
[17179702.244000] end_request: I/O error, dev hdd, sector 3172992
[17179702.244000] end_request: I/O error, dev hdd, sector 3173168
[17179702.244000] end_request: I/O error, dev hdd, sector 3173168
[17179702.244000] end_request: I/O error, dev hdd, sector 0
[17179702.244000] end_request: I/O error, dev hdd, sector 8
[17179702.244000] end_request: I/O error, dev hdd, sector 16
[17179702.244000] end_request: I/O error, dev hdd, sector 24
[17179702.244000] end_request: I/O error, dev hdd, sector 32
[17179702.244000] end_request: I/O error, dev hdd, sector 40
[17179702.244000] end_request: I/O error, dev hdd, sector 48
[17179702.244000] end_request: I/O error, dev hdd, sector 56
[17179702.244000] end_request: I/O error, dev hdd, sector 0
[17179702.244000] end_request: I/O error, dev hdd, sector 8
[17179702.244000] end_request: I/O error, dev hdd, sector 8
[17179702.244000] end_request: I/O error, dev hdd, sector 3172992
[17179702.244000] end_request: I/O error, dev hdd, sector 3172992
[17179702.244000] end_request: I/O error, dev hdd, sector 3173168
[17179702.244000] end_request: I/O error, dev hdd, sector 3173168
[17179702.244000] end_request: I/O error, dev hdd, sector 0
[17179702.244000] end_request: I/O error, dev hdd, sector 8
[17179702.244000] end_request: I/O error, dev hdd, sector 16
[17179702.244000] end_request: I/O error, dev hdd, sector 24
[17179702.244000] end_request: I/O error, dev hdd, sector 32
[17179702.244000] end_request: I/O error, dev hdd, sector 40
[17179702.244000] end_request: I/O error, dev hdd, sector 48
[17179702.244000] end_request: I/O error, dev hdd, sector 56
[17179702.244000] end_request: I/O error, dev hdd, sector 0
[17179702.244000] end_request: I/O error, dev hdd, sector 8
[17179702.244000] end_request: I/O error, dev hdd, sector 8
[17179702.244000] end_request: I/O error, dev hdd, sector 3173183
[17179702.248000] end_request: I/O error, dev hdd, sector 3173182
[17179702.248000] end_request: I/O error, dev hdd, sector 3173183
[17179702.248000] end_request: I/O error, dev hdd, sector 3173182
[17179702.360000] end_request: I/O error, dev hdd, sector 0
[17179702.360000] end_request: I/O error, dev hdd, sector 16
[17179702.360000] end_request: I/O error, dev hdd, sector 24
[17179702.360000] end_request: I/O error, dev hdd, sector 32
[17179702.360000] end_request: I/O error, dev hdd, sector 40
[17179702.360000] end_request: I/O error, dev hdd, sector 48
[17179702.360000] end_request: I/O error, dev hdd, sector 56
[17179702.360000] end_request: I/O error, dev hdd, sector 0
[17179702.360000] end_request: I/O error, dev hdd, sector 64
[17179702.360000] end_request: I/O error, dev hdd, sector 64
[17179702.360000] end_request: I/O error, dev hdd, sector 120
[17179702.360000] end_request: I/O error, dev hdd, sector 120
[17179702.360000] end_request: I/O error, dev hdd, sector 8
[17179702.360000] end_request: I/O error, dev hdd, sector 0
[17179702.360000] end_request: I/O error, dev hdd, sector 3173176
[17179702.360000] end_request: I/O error, dev hdd, sector 3173176
[17179702.360000] end_request: I/O error, dev hdd, sector 1586592
[17179702.360000] end_request: I/O error, dev hdd, sector 1586592
[17179702.360000] end_request: I/O error, dev hdd, sector 128
[17179702.360000] end_request: I/O error, dev hdd, sector 128
[17179702.360000] end_request: I/O error, dev hdd, sector 0
[17179702.360000] end_request: I/O error, dev hdd, sector 0
[17179702.360000] end_request: I/O error, dev hdd, sector 128
[17179702.360000] end_request: I/O error, dev hdd, sector 0
[17179702.360000] end_request: I/O error, dev hdd, sector 0
[17179702.360000] end_request: I/O error, dev hdd, sector 0
[17179702.364000] end_request: I/O error, dev hdd, sector 0
[17179702.368000] end_request: I/O error, dev hdd, sector 64
[17179702.368000] end_request: I/O error, dev hdd, sector 120
[17179702.368000] end_request: I/O error, dev hdd, sector 8
[17179702.368000] end_request: I/O error, dev hdd, sector 0
[17179702.368000] end_request: I/O error, dev hdd, sector 3173176
[17179702.368000] end_request: I/O error, dev hdd, sector 1586592
[17179702.368000] end_request: I/O error, dev hdd, sector 128
[17179702.368000] end_request: I/O error, dev hdd, sector 0
[17179702.368000] end_request: I/O error, dev hdd, sector 0
[17179702.368000] end_request: I/O error, dev hdd, sector 128
[17179702.368000] end_request: I/O error, dev hdd, sector 0
[17179702.368000] end_request: I/O error, dev hdd, sector 0
[17179702.368000] end_request: I/O error, dev hdd, sector 0
[17179708.924000] ACPI: Power Button (FF) [PWRF]
[17179708.924000] ACPI: Power Button (CM) [PWRB]
[17179708.924000] ACPI: Sleep Button (CM) [SLPB]
[17179709.056000] ibm_acpi: ec object not found
[17179709.096000] pcc_acpi: loading...
[17179713.096000] eth0: no IPv6 routers present
[17179719.312000] [drm] Initialized drm 1.0.1 20051102
[17179719.548000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 201
[17179719.548000] [drm] Initialized savage 2.4.1 20050313 on minor 0
[17179719.552000] mtrr: base(0xda000000) is not aligned on a size(0x5000000) boundary
[17179719.552000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179719.552000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[17179719.552000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[17179721.904000] lp0: using parport0 (interrupt-driven).
[17179721.944000] ppdev: user-space parallel port driver
[17179722.688000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179722.688000] apm: overridden by ACPI.
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] printk: 114 messages suppressed.
[17179728.252000] Buffer I/O error on device hdd, logical block 0
[17179728.252000] end_request: I/O error, dev hdd, sector 8
[17179728.252000] Buffer I/O error on device hdd, logical block 1
[17179728.252000] end_request: I/O error, dev hdd, sector 16
[17179728.252000] Buffer I/O error on device hdd, logical block 2
[17179728.252000] end_request: I/O error, dev hdd, sector 24
[17179728.252000] Buffer I/O error on device hdd, logical block 3
[17179728.252000] end_request: I/O error, dev hdd, sector 32
[17179728.252000] Buffer I/O error on device hdd, logical block 4
[17179728.252000] end_request: I/O error, dev hdd, sector 40
[17179728.252000] end_request: I/O error, dev hdd, sector 48
[17179728.252000] end_request: I/O error, dev hdd, sector 56
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 64
[17179728.252000] end_request: I/O error, dev hdd, sector 72
[17179728.252000] end_request: I/O error, dev hdd, sector 80
[17179728.252000] end_request: I/O error, dev hdd, sector 88
[17179728.252000] end_request: I/O error, dev hdd, sector 96
[17179728.252000] end_request: I/O error, dev hdd, sector 104
[17179728.252000] end_request: I/O error, dev hdd, sector 112
[17179728.252000] end_request: I/O error, dev hdd, sector 120
[17179728.252000] end_request: I/O error, dev hdd, sector 128
[17179728.252000] end_request: I/O error, dev hdd, sector 136
[17179728.252000] end_request: I/O error, dev hdd, sector 144
[17179728.252000] end_request: I/O error, dev hdd, sector 152
[17179728.252000] end_request: I/O error, dev hdd, sector 160
[17179728.252000] end_request: I/O error, dev hdd, sector 168
[17179728.252000] end_request: I/O error, dev hdd, sector 176
[17179728.252000] end_request: I/O error, dev hdd, sector 184
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 192
[17179728.252000] end_request: I/O error, dev hdd, sector 200
[17179728.252000] end_request: I/O error, dev hdd, sector 208
[17179728.252000] end_request: I/O error, dev hdd, sector 216
[17179728.252000] end_request: I/O error, dev hdd, sector 224
[17179728.252000] end_request: I/O error, dev hdd, sector 232
[17179728.252000] end_request: I/O error, dev hdd, sector 240
[17179728.252000] end_request: I/O error, dev hdd, sector 248
[17179728.252000] end_request: I/O error, dev hdd, sector 256
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179728.252000] end_request: I/O error, dev hdd, sector 0
[17179731.092000] Bluetooth: Core ver 2.8
[17179731.092000] NET: Registered protocol family 31
[17179731.092000] Bluetooth: HCI device and connection manager initialized
[17179731.092000] Bluetooth: HCI socket layer initialized
[17179731.248000] Bluetooth: L2CAP ver 2.8
[17179731.248000] Bluetooth: L2CAP socket layer initialized
[17179731.460000] Bluetooth: RFCOMM socket layer initialized
[17179731.460000] Bluetooth: RFCOMM TTY layer initialized
[17179731.460000] Bluetooth: RFCOMM ver 1.7
[17179745.956000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179969.528000] end_request: I/O error, dev hdd, sector 0
[17179969.528000] printk: 52 messages suppressed.
[17179969.528000] Buffer I/O error on device hdd, logical block 0
[17179969.528000] end_request: I/O error, dev hdd, sector 8
[17179969.528000] Buffer I/O error on device hdd, logical block 1
[17179969.528000] end_request: I/O error, dev hdd, sector 16
[17179969.528000] Buffer I/O error on device hdd, logical block 2
[17179969.528000] end_request: I/O error, dev hdd, sector 24
[17179969.528000] Buffer I/O error on device hdd, logical block 3
[17179969.528000] end_request: I/O error, dev hdd, sector 32
[17179969.528000] Buffer I/O error on device hdd, logical block 4
[17179969.528000] end_request: I/O error, dev hdd, sector 40
[17179969.528000] Buffer I/O error on device hdd, logical block 5
[17179969.528000] end_request: I/O error, dev hdd, sector 48
[17179969.528000] Buffer I/O error on device hdd, logical block 6
[17179969.528000] end_request: I/O error, dev hdd, sector 56
[17179969.528000] Buffer I/O error on device hdd, logical block 7
[17179969.528000] end_request: I/O error, dev hdd, sector 0
[17179969.528000] Buffer I/O error on device hdd, logical block 0

```

Be grateful for any ideas.

---

### Post by s0cket on 2007-03-26
You have a dead disk most likely.

---

### Post by dentament on 2007-04-15
Hi, I had a similar experience some months ago with ubuntu 6.06 installed on a western digital hard-disk (on via vt8235 chipset).
At every boot got the "misaligned" etc. warning message in dmesg, but my drive mounted correctly most times. Only sometimes it did not, and these times dmesg showed the "DriveReady SeekComplete Error". I did not investigate that much. At first fsck massive data corruption was detected. Most personal sensible data was recovered (and I did backup that on another drive), but I lost some stuff and system data and decided to reinstall 6.06 (from scratch, formatting and without recovering my data from the backup drive because I just wanted to test). After reinstalling I hacked a bit with kernel parameters but with no result and same beahaviour ("misaligned" etc. at every boot, sometimes no mount and "DriveReady SeekComplete Error"); then at first fsck, same data corruption. Then I reinstalled ubuntu 5.10, which always worked no problem before and has worked no problem until now (it's about 2 years I think). Now, since 5.10 is going to be unsupported, I'm trying 6.10 ... its livecd gives no warning in dmesg (while 6.06's livecd does give the "misaligned" ecc. msg), so I'm installing it just now and I hope (I think) it's not going to make mess. I think the problem with my hd on 6.06 could be related with some bug in how it's kernel version manages the via chipset, but couldn't find much about this searching around.
Bye.

---

