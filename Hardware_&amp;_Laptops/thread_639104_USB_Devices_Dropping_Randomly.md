---
title: "USB Devices Dropping Randomly"
date: 2007-12-12
forum: Hardware &amp; Laptops
---

### Post by jasajoh on 2007-12-12
Hey all, Have used this site for 2 years as an AMAZING resource for solving my issues in Ubuntu, and now I make my first post :)

I seem to be having an issue where all of my usb devices plugged into a hub die randomly. 
Connected to the hub is the following:

Pioneer DVR-112DBK DVD Burner
Sony DRU-820 DVD Burner
Seagate FreeAgent Pro 320 Ext. USB 2.0 HDD
Optical Mouse USB 2.0
Wired ZBoard Keyboard  USB 2.0

I am running Gutsy Gibbon running 2.6.22-14-generic
Thhis is a Compaq Presario 3240CA Laptop
Athlon XP 3200+
768 Mb. PC-2100
64mb nVidia 440GO

being that this is a laptop, it is only my USB devices that seem to "die" on me as the built-in keyboard /touchpad work fine after the USB is gone, so it's not a freezing issue.

All the devices work on an Intel iMac flawlessly in both the Mac and the Windows partition and I never encounter this issue, so it is isolated to Ubuntu.
 
If I reboot, everything works fine again for an unspecified period of time.

I ran dmesg as sooon as I lost all my devices and will paste the output after this post.
Thanks in advance for any assistance you give me!!

[    7.024000] usb 2-1: USB disconnect, address 2
[    7.024000] usb 2-1.1: USB disconnect, address 3
[    7.024000] usb 2-1.2: USB disconnect, address 4
[    7.024000] usb 2-1.3: USB disconnect, address 5
[    7.024000] usb 2-1.4: USB disconnect, address 6
[    7.156000]  hda1 hda2 hda3
[    7.584000] usb 3-3: new high speed USB device using ehci_hcd and address 3
[    7.672000] Attempting manual resume
[    7.672000] swsusp: Resume From Partition 3:3
[    7.672000] PM: Checking swsusp image.
[    7.692000] PM: Resume from disk failed.
[    7.708000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    7.708000] EXT3-fs: write access will be enabled during recovery.
[    7.716000] usb 3-3: configuration #1 chosen from 1 choice
[    7.716000] hub 3-3:1.0: USB hub found
[    7.716000] hub 3-3:1.0: 7 ports detected
[    7.820000] usbcore: registered new interface driver usbhid
[    7.820000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    8.124000] usb 1-1: new low speed USB device using ohci_hcd and address 3
[    8.328000] usb 1-1: configuration #1 chosen from 1 choice
[    8.336000] input: HID 04b3:310b as /class/input/input2
[    8.336000] input: USB HID v1.00 Mouse [HID 04b3:310b] on usb-0000:00:02.0-1
[    8.552000] usb 3-3.1: new low speed USB device using ehci_hcd and address 4
[    8.740000] usb 3-3.1: configuration #1 chosen from 1 choice
[    9.276000] hiddev96: USB HID v1.10 Device [American Power Conversion Back-UPS XS 1200 FW:8.g1 .D USB FW:g1 ] on usb-0000:00:02.2-3.1
[    9.492000] usb 3-3.2: new low speed USB device using ehci_hcd and address 5
[    9.632000] usb 3-3.2: configuration #1 chosen from 1 choice
[    9.872000] hiddev97: USB HID v1.10 Device [APC Back-UPS ES 350 FW:800.e5.D USB FW:e5] on usb-0000:00:02.2-3.2
[   10.092000] usb 3-3.3: new high speed USB device using ehci_hcd and address 6
[   10.200000] usb 3-3.3: configuration #1 chosen from 1 choice
[   10.416000] usb 3-3.4: new high speed USB device using ehci_hcd and address 7
[   10.524000] usb 3-3.4: configuration #1 chosen from 1 choice
[   10.524000] hub 3-3.4:1.0: USB hub found
[   10.524000] hub 3-3.4:1.0: 7 ports detected
[   10.688000] kjournald starting.  Commit interval 5 seconds
[   10.688000] EXT3-fs: hda2: orphan cleanup on readonly fs
[   10.688000] ext3_orphan_cleanup: deleting unreferenced inode 1064968
[   10.688000] ext3_orphan_cleanup: deleting unreferenced inode 1064967
[   10.688000] ext3_orphan_cleanup: deleting unreferenced inode 1064966
[   10.688000] ext3_orphan_cleanup: deleting unreferenced inode 1064965
[   10.688000] ext3_orphan_cleanup: deleting unreferenced inode 1064962
[   10.688000] EXT3-fs: hda2: 5 orphan inodes deleted
[   10.688000] EXT3-fs: recovery complete.
[   10.712000] EXT3-fs: mounted filesystem with ordered data mode.
[   10.844000] usb 3-3.5: new high speed USB device using ehci_hcd and address 8
[   10.980000] usb 3-3.5: configuration #1 chosen from 1 choice
[   11.208000] usb 3-3.6: new high speed USB device using ehci_hcd and address 9
[   11.316000] usb 3-3.6: configuration #1 chosen from 1 choice
[   11.532000] usb 3-3.7: new high speed USB device using ehci_hcd and address 10
[   11.640000] usb 3-3.7: configuration #1 chosen from 1 choice
[   22.152000] Linux agpgart interface v0.102 (c) Dave Jones
[   22.156000] agpgart: Detected AGP bridge 0
[   22.156000] agpgart: Setting up Nforce3 AGP.
[   22.160000] agpgart: AGP aperture is 128M @ 0xe8000000
[   22.340000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x2040
[   22.340000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
[   22.932000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   22.940000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.980000] usbcore: registered new interface driver xpad
[   22.980000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   23.264000] usbcore: registered new interface driver libusual
[   23.568000] Initializing USB Mass Storage driver...
[   23.568000] scsi0 : SCSI emulation for USB Mass Storage devices
[   23.568000] usb-storage: device found at 8
[   23.568000] usb-storage: waiting for device to settle before scanning
[   23.568000] scsi1 : SCSI emulation for USB Mass Storage devices
[   23.568000] usb-storage: device found at 9
[   23.568000] usb-storage: waiting for device to settle before scanning
[   23.568000] scsi2 : SCSI emulation for USB Mass Storage devices
[   23.568000] usb-storage: device found at 10
[   23.568000] usb-storage: waiting for device to settle before scanning
[   23.568000] usbcore: registered new interface driver usb-storage
[   23.568000] USB Mass Storage support registered.
[   23.584000] input: PS/2 Mouse as /class/input/input3
[   23.596000] Yenta: CardBus bridge found at 0000:02:04.0 [103c:006d]
[   23.596000] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[   23.596000]   IO window: 00003000-000030ff
[   23.596000]   IO window: 00003400-000034ff
[   23.596000]   PREFETCH window: 40000000-43ffffff
[   23.596000]   MEM window: e0400000-e07fffff
[   23.596000] Yenta: Enabling burst memory read transactions
[   23.596000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   23.596000] Yenta: Routing CardBus interrupts to PCI
[   23.596000] Yenta TI: socket 0000:02:04.0, mfunc 0x01111d22, devctl 0x64
[   23.604000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   23.636000] input: PC Speaker as /class/input/input5
[   23.760000] ieee80211_crypt: registered algorithm 'NULL'
[   23.760000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   23.760000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   23.828000] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
[   23.828000] Socket status: 30000086
[   23.828000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   23.828000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[   23.828000] cs: IO port probe 0x3000-0x7fff: clean.
[   23.828000] pcmcia: parent PCI bridge Memory window: 0xe0100000 - 0xe17fffff
[   23.828000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x47ffffff
[   23.828000] Yenta: CardBus bridge found at 0000:02:04.1 [103c:006d]
[   23.828000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   23.828000] Yenta: Routing CardBus interrupts to PCI
[   23.828000] Yenta TI: socket 0000:02:04.1, mfunc 0x01111d22, devctl 0x64
[   23.868000] bcm43xx driver
[   23.896000] nvidia: module license 'NVIDIA' taints kernel.
[   24.152000] parport_pc 00:0b: reported by Plug and Play ACPI
[   24.152000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   24.280000] Yenta: ISA IRQ mask 0x0c38, PCI irq 17
[   24.280000] Socket status: 30000006
[   24.280000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   24.280000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[   24.280000] cs: IO port probe 0x3000-0x7fff: clean.
[   24.280000] pcmcia: parent PCI bridge Memory window: 0xe0100000 - 0xe17fffff
[   24.280000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x47ffffff
[   24.284000] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 17
[   24.284000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNK3] -> GSI 17 (level, low) -> IRQ 21
[   24.320000] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 16
[   24.320000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNK5] -> GSI 16 (level, low) -> IRQ 22
[   24.320000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   24.464000] ACPI: PCI Interrupt Link [LACI] enabled at IRQ 21
[   24.464000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LACI] -> GSI 21 (level, low) -> IRQ 19
[   24.464000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   24.576000] AC'97 0 analog subsections not ready
[   25.040000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x20f
[   25.044000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   25.044000] cs: IO port probe 0x820-0x8ff: clean.
[   25.044000] cs: IO port probe 0xc00-0xcf7: clean.
[   25.044000] cs: IO port probe 0xa00-0xaff: clean.
[   25.084000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x20f
[   25.088000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   25.088000] cs: IO port probe 0x820-0x8ff: clean.
[   25.088000] cs: IO port probe 0xc00-0xcf7: clean.
[   25.088000] cs: IO port probe 0xa00-0xaff: clean.
[   25.148000] intel8x0_measure_ac97_clock: measured 55899 usecs
[   25.148000] intel8x0: clocking to 47489
[   26.824000] floppy0: no floppy controllers found
[   27.776000] lp0: using parport0 (interrupt-driven).
[   27.848000] Adding 3903784k swap on /dev/hda3.  Priority:-1 extents:1 across:3903784k
[   28.176000] EXT3 FS on hda2, internal journal
[   28.568000] usb-storage: device scan complete
[   28.568000] usb-storage: device scan complete
[   28.568000] scsi 1:0:0:0: CD-ROM            SONY     DVD RW DRU-820A  2.0c PQ: 0 ANSI: 0
[   28.568000] scsi 2:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-112D 1.21 PQ: 0 ANSI: 0
[   28.572000] usb-storage: device scan complete
[   28.580000] scsi 0:0:0:0: Direct-Access     Seagate  FreeAgent Pro    400A PQ: 0 ANSI: 4
[   28.636000] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   28.636000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   28.644000] sr1: scsi3-mmc drive: 62x/62x writer cd/rw xa/form2 cdda tray
[   28.644000] sr 2:0:0:0: Attached scsi CD-ROM sr1
[   28.668000] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   28.668000] sr 1:0:0:0: Attached scsi generic sg0 type 5
[   28.668000] sr 2:0:0:0: Attached scsi generic sg1 type 5
[   28.668000] sd 0:0:0:0: Attached scsi generic sg2 type 0
[   28.704000] sd 0:0:0:0: [sda] Write Protect is off
[   28.704000] sd 0:0:0:0: [sda] Mode Sense: 1c 00 00 00
[   28.704000] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   28.740000] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   28.744000] sd 0:0:0:0: [sda] Write Protect is off
[   28.744000] sd 0:0:0:0: [sda] Mode Sense: 1c 00 00 00
[   28.744000] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   28.744000]  sda: sda1
[   28.748000] sd 0:0:0:0: [sda] Attached SCSI disk
[   29.624000] input: Power Button (FF) as /class/input/input6
[   29.628000] ACPI: Power Button (FF) [PWRF]
[   29.660000] input: Power Button (CM) as /class/input/input7
[   29.664000] ACPI: Power Button (CM) [PWRB]
[   29.696000] input: Lid Switch as /class/input/input8
[   29.700000] ACPI: Lid Switch [LID]
[   29.740000] No dock devices found.
[   29.876000] ACPI: Battery Slot [BAT1] (battery present)
[   29.892000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   29.904000] ACPI: AC Adapter [ACAD] (on-line)
[   31.052000] ACPI: PCI Interrupt 0000:00:06.1[B] -> Link [LMCI] -> GSI 22 (level, low) -> IRQ 18
[   31.052000] PCI: Setting latency timer of device 0000:00:06.1 to 64
[   31.316000] eth0: link down
[   32.504000] ppdev: user-space parallel port driver
[   32.608000] audit(1197502711.645:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5234 profile="/usr/sbin/cupsd"
[   32.912000] cdrom: This disc doesn't have any tracks I recognize!
[   33.008000] cdrom: This disc doesn't have any tracks I recognize!
[   35.592000] apm: BIOS not found.
[   43.308000] NET: Registered protocol family 10
[   43.308000] lo: Disabled Privacy Extensions
[   43.308000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   43.308000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   43.324000] Failure registering capabilities with primary security module.
[   48.184000] Bluetooth: Core ver 2.11
[   48.184000] NET: Registered protocol family 31
[   48.184000] Bluetooth: HCI device and connection manager initialized
[   48.184000] Bluetooth: HCI socket layer initialized
[   48.264000] Bluetooth: L2CAP ver 2.8
[   48.264000] Bluetooth: L2CAP socket layer initialized
[   48.412000] Bluetooth: RFCOMM socket layer initialized
[   48.412000] Bluetooth: RFCOMM TTY layer initialized
[   48.412000] Bluetooth: RFCOMM ver 1.8
[   49.920000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   49.920000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   49.920000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   52.936000] /dev/vmmon[6455]: Module vmmon: registered with major=10 minor=165
[   52.936000] /dev/vmmon[6455]: Module vmmon: initialized
[   53.272000] /dev/vmnet: open called by PID 6480 (vmnet-bridge)
[   53.272000] /dev/vmnet: hub 0 does not exist, allocating memory.
[   53.272000] /dev/vmnet: port on hub 0 successfully opened
[   53.272000] bridge-eth0: enabling the bridge
[   53.272000] bridge-eth0: up
[   53.272000] bridge-eth0: already up
[   53.272000] bridge-eth0: attached
[   53.320000] /dev/vmnet: open called by PID 6494 (vmnet-natd)
[   53.320000] /dev/vmnet: hub 2 does not exist, allocating memory.
[   53.324000] /dev/vmnet: port on hub 2 successfully opened
[   53.344000] /dev/vmnet: open called by PID 6495 (vmnet-netifup)
[   53.344000] /dev/vmnet: hub 1 does not exist, allocating memory.
[   53.344000] /dev/vmnet: port on hub 1 successfully opened
[   53.348000] /dev/vmnet: open called by PID 6496 (vmnet-netifup)
[   53.348000] /dev/vmnet: port on hub 2 successfully opened
[   53.352000] /dev/vmnet: open called by PID 6502 (vmnet-netifup)
[   53.352000] /dev/vmnet: hub 8 does not exist, allocating memory.
[   53.352000] /dev/vmnet: port on hub 8 successfully opened
[   53.380000] /dev/vmnet: open called by PID 6506 (vmnet-natd)
[   53.380000] /dev/vmnet: port on hub 8 successfully opened
[   53.860000] /dev/vmnet: open called by PID 6539 (vmnet-dhcpd)
[   53.860000] /dev/vmnet: port on hub 8 successfully opened
[   54.468000] /dev/vmnet: open called by PID 6540 (vmnet-dhcpd)
[   54.468000] /dev/vmnet: port on hub 2 successfully opened
[   54.468000] /dev/vmnet: open called by PID 6537 (vmnet-dhcpd)
[   54.468000] /dev/vmnet: port on hub 1 successfully opened
[   63.560000] vmnet1: no IPv6 routers present
[   64.008000] vmnet2: no IPv6 routers present
[   64.264000] vmnet8: no IPv6 routers present
[ 1409.952000] sd 0:0:0:0: [sda] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 1409.952000] : Add. Sense: Logical unit not ready, initializing command required
[ 1409.952000] end_request: I/O error, dev sda, sector 63
[ 1409.952000] Buffer I/O error on device sda1, logical block 0
[ 1409.952000] Buffer I/O error on device sda1, logical block 1
[ 1409.952000] Buffer I/O error on device sda1, logical block 2
[ 1409.952000] Buffer I/O error on device sda1, logical block 3
[ 1409.952000] Buffer I/O error on device sda1, logical block 4
[ 1409.952000] Buffer I/O error on device sda1, logical block 5
[ 1409.952000] Buffer I/O error on device sda1, logical block 6
[ 1409.952000] Buffer I/O error on device sda1, logical block 7
[ 1409.952000] Buffer I/O error on device sda1, logical block 8
[ 1409.952000] Buffer I/O error on device sda1, logical block 9
[ 1409.964000] sd 0:0:0:0: [sda] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 1409.964000] : Add. Sense: Logical unit not ready, initializing command required
[ 1409.964000] end_request: I/O error, dev sda, sector 63
[ 1409.972000] sd 0:0:0:0: [sda] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 1409.972000] : Add. Sense: Logical unit not ready, initializing command required
[ 1409.972000] end_request: I/O error, dev sda, sector 65
[ 1423.456000] NET: Registered protocol family 17
[ 1423.876000] printk: 10 messages suppressed.
[ 1423.876000] SoftMAC: Open Authentication completed with 00:1b:11:56:17:53
[ 1423.888000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1423.916000] ieee80211_crypt: registered algorithm 'CCMP'
[ 1427.348000] ieee80211_crypt: registered algorithm 'TKIP'
[ 1443.132000] eth1: no IPv6 routers present
[ 1527.312000] sd 0:0:0:0: [sda] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 1527.312000] : Add. Sense: Logical unit not ready, initializing command required
[ 1527.312000] end_request: I/O error, dev sda, sector 63
[ 1527.312000] Buffer I/O error on device sda1, logical block 0
[ 1527.312000] Buffer I/O error on device sda1, logical block 1
[ 1527.312000] Buffer I/O error on device sda1, logical block 2
[ 1527.312000] Buffer I/O error on device sda1, logical block 3
[ 1527.312000] Buffer I/O error on device sda1, logical block 4
[ 1527.312000] Buffer I/O error on device sda1, logical block 5
[ 1527.312000] Buffer I/O error on device sda1, logical block 6
[ 1527.312000] Buffer I/O error on device sda1, logical block 7
[ 1527.312000] Buffer I/O error on device sda1, logical block 8
[ 1527.312000] Buffer I/O error on device sda1, logical block 9
[ 1527.324000] sd 0:0:0:0: [sda] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 1527.324000] : Add. Sense: Logical unit not ready, initializing command required
[ 1527.324000] end_request: I/O error, dev sda, sector 63
[ 1527.332000] sd 0:0:0:0: [sda] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 1527.332000] : Add. Sense: Logical unit not ready, initializing command required
[ 1527.332000] end_request: I/O error, dev sda, sector 65
[ 1893.608000] printk: 10 messages suppressed.
[ 2031.792000] cdrom: This disc doesn't have any tracks I recognize!
[ 2058.956000] sd 0:0:0:0: [sda] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 2058.956000] : Add. Sense: Logical unit not ready, initializing command required
[ 2058.956000] end_request: I/O error, dev sda, sector 6291815
[ 2058.956000] Buffer I/O error on device sda1, logical block 786469
[ 2058.964000] sd 0:0:0:0: [sda] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 2058.964000] : Add. Sense: Logical unit not ready, initializing command required
[ 2058.964000] end_request: I/O error, dev sda, sector 6291815
[ 2058.964000] Buffer I/O error on device sda1, logical block 786469
[ 2058.976000] sd 0:0:0:0: [sda] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 2058.976000] : Add. Sense: Logical unit not ready, initializing command required
[ 2058.976000] end_request: I/O error, dev sda, sector 6291815
[ 2058.976000] Buffer I/O error on device sda1, logical block 786469
[ 3042.316000] sd 0:0:0:0: [sda] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 3042.316000] : Add. Sense: Logical unit not ready, initializing command required
[ 3042.316000] end_request: I/O error, dev sda, sector 6291527
[ 3042.316000] Buffer I/O error on device sda1, logical block 786433
[ 3049.028000] sd 0:0:0:0: [sda] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 3049.028000] : Add. Sense: Logical unit not ready, initializing command required
[ 3049.028000] end_request: I/O error, dev sda, sector 6291527
[ 3049.028000] Buffer I/O error on device sda1, logical block 786433
[ 3049.036000] sd 0:0:0:0: [sda] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 3049.036000] : Add. Sense: Logical unit not ready, initializing command required
[ 3049.036000] end_request: I/O error, dev sda, sector 6291527
[ 3049.036000] Buffer I/O error on device sda1, logical block 786433
[ 3434.128000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[ 3434.132000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[ 3434.132000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[ 4785.336000] sd 0:0:0:0: [sda] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 4785.336000] : Add. Sense: Logical unit not ready, initializing command required
[ 4785.336000] end_request: I/O error, dev sda, sector 6291839
[ 4785.336000] Buffer I/O error on device sda1, logical block 786472
[ 4785.348000] sd 0:0:0:0: [sda] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 4785.348000] : Add. Sense: Logical unit not ready, initializing command required
[ 4785.348000] end_request: I/O error, dev sda, sector 6312631
[ 4785.348000] Buffer I/O error on device sda1, logical block 789071
[ 4785.360000] sd 0:0:0:0: [sda] Device not ready: <6>: Sense Key : Not Ready [current] 
[ 4785.360000] : Add. Sense: Logical unit not ready, initializing command required
[ 4785.360000] end_request: I/O error, dev sda, sector 6312631
[ 4785.360000] Buffer I/O error on device sda1, logical block 789071
[ 5820.936000] hub 3-3:1.0: cannot reset port 5 (err = -110)
[ 5820.936000] hub 3-3:1.0: cannot reset port 5 (err = -71)
[ 5820.936000] usb 3-3: USB disconnect, address 3
[ 5820.936000] usb 3-3.1: USB disconnect, address 4
[ 5820.936000] usb 3-3.2: USB disconnect, address 5
[ 5820.936000] usb 3-3.3: USB disconnect, address 6
[ 5820.936000] usb 3-3.4: USB disconnect, address 7
[ 5820.936000] usb 3-3.5: USB disconnect, address 8
[ 5820.936000] hub 3-3:1.0: cannot reset port 5 (err = -71)
[ 5820.936000] hub 3-3:1.0: cannot reset port 5 (err = -19)
[ 5820.936000] hub 3-3:1.0: cannot disable port 5 (err = -19)
[ 5820.936000] hub 3-3:1.0: cannot reset port 5 (err = -19)
[ 5820.936000] hub 3-3:1.0: cannot disable port 5 (err = -19)
[ 5820.936000] hub 3-3:1.0: cannot reset port 5 (err = -19)
[ 5820.936000] hub 3-3:1.0: cannot disable port 5 (err = -19)
[ 5820.936000] hub 3-3:1.0: cannot reset port 5 (err = -19)
[ 5820.936000] hub 3-3:1.0: cannot disable port 5 (err = -19)
[ 5820.936000] hub 3-3:1.0: cannot disable port 5 (err = -19)
[ 5820.936000] hub 3-3:1.0: cannot reset port 6 (err = -19)
[ 5820.936000] hub 3-3:1.0: cannot disable port 6 (err = -19)
[ 5820.936000] hub 3-3:1.0: cannot reset port 6 (err = -19)
[ 5820.936000] hub 3-3:1.0: cannot disable port 6 (err = -19)
[ 5820.936000] hub 3-3:1.0: cannot reset port 6 (err = -19)
[ 5820.936000] hub 3-3:1.0: cannot disable port 6 (err = -19)
[ 5820.936000] hub 3-3:1.0: cannot reset port 6 (err = -19)
[ 5820.936000] hub 3-3:1.0: cannot disable port 6 (err = -19)
[ 5820.936000] hub 3-3:1.0: cannot disable port 6 (err = -19)
[ 5820.940000] sd 0:0:0:0: scsi: Device offlined - not ready after error recovery
[ 5820.940000] hub 3-3:1.0: cannot reset port 7 (err = -19)
[ 5820.940000] hub 3-3:1.0: cannot disable port 7 (err = -19)
[ 5820.940000] hub 3-3:1.0: cannot reset port 7 (err = -19)
[ 5820.940000] hub 3-3:1.0: cannot disable port 7 (err = -19)
[ 5820.940000] hub 3-3:1.0: cannot reset port 7 (err = -19)
[ 5820.940000] hub 3-3:1.0: cannot disable port 7 (err = -19)
[ 5820.940000] hub 3-3:1.0: cannot reset port 7 (err = -19)
[ 5820.940000] hub 3-3:1.0: cannot disable port 7 (err = -19)
[ 5820.940000] hub 3-3:1.0: cannot disable port 7 (err = -19)
[ 5820.940000] sr 1:0:0:0: scsi: Device offlined - not ready after error recovery
[ 5820.940000] sr 2:0:0:0: scsi: Device offlined - not ready after error recovery
[ 5820.940000] sr 1:0:0:0: rejecting I/O to offline device
[ 5820.940000] sr 2:0:0:0: rejecting I/O to offline device
[ 5820.944000] sd 0:0:0:0: [sda] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 5820.944000] end_request: I/O error, dev sda, sector 200403791
[ 5820.944000] Buffer I/O error on device sda1, logical block 25050466
[ 5820.944000] Buffer I/O error on device sda1, logical block 95
[ 5820.944000] lost page write due to I/O error on sda1
[ 5820.944000] Buffer I/O error on device sda1, logical block 96
[ 5820.944000] lost page write due to I/O error on sda1
[ 5820.944000] Buffer I/O error on device sda1, logical block 36259
[ 5820.944000] lost page write due to I/O error on sda1
[ 5820.944000] Buffer I/O error on device sda1, logical block 36260
[ 5820.944000] lost page write due to I/O error on sda1
[ 5820.944000] Buffer I/O error on device sda1, logical block 405137
[ 5820.944000] lost page write due to I/O error on sda1
[ 5820.944000] Buffer I/O error on device sda1, logical block 405139
[ 5820.944000] lost page write due to I/O error on sda1
[ 5820.944000] Buffer I/O error on device sda1, logical block 405140
[ 5820.944000] lost page write due to I/O error on sda1
[ 5820.944000] Buffer I/O error on device sda1, logical block 786433
[ 5820.944000] lost page write due to I/O error on sda1
[ 5820.944000] Buffer I/O error on device sda1, logical block 786468
[ 5820.944000] lost page write due to I/O error on sda1
[ 5820.976000] usb 3-3.6: USB disconnect, address 9
[ 5820.976000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5820.980000] usb 3-3.7: USB disconnect, address 10
[ 5820.980000] hub 3-0:1.0: hub_port_status failed (err = -108)
[ 5820.980000] hub 3-0:1.0: cannot disable port 3 (err = -108)
[ 5821.776000] irq 18: nobody cared (try booting with the "irqpoll" option)
[ 5821.776000]  [<c015b594>] __report_bad_irq+0x24/0x80
[ 5821.776000]  [<f0db54a9>] snd_intel8x0_interrupt+0x199/0x200 [snd_intel8x0m]
[ 5821.776000]  [<c015b852>] note_interrupt+0x262/0x2a0
[ 5821.776000]  [<c015aab0>] handle_IRQ_event+0x30/0x60
[ 5821.776000]  [<c015c23b>] handle_fasteoi_irq+0xbb/0xf0
[ 5821.776000]  [<c0106b1b>] do_IRQ+0x3b/0x70
[ 5821.776000]  [<c0106b20>] do_IRQ+0x40/0x70
[ 5821.776000]  [<c012da61>] irq_exit+0x51/0x80
[ 5821.776000]  [<c0118735>] smp_apic_timer_interrupt+0x55/0x80
[ 5821.776000]  [<c0105223>] common_interrupt+0x23/0x30
[ 5821.776000]  [<c0274227>] acpi_pm_read+0x7/0x10
[ 5821.776000]  [<c0140e36>] getnstimeofday+0x36/0xd0
[ 5821.776000]  [<c013eeb6>] ktime_get_ts+0x16/0x50
[ 5821.776000]  [<c013eefd>] ktime_get+0xd/0x30
[ 5821.776000]  [<f084a74b>] acpi_processor_idle+0x0/0x425 [processor]
[ 5821.776000]  [<c0144b6e>] tick_nohz_restart_sched_tick+0x2e/0x140
[ 5821.776000]  [<f084a74b>] acpi_processor_idle+0x0/0x425 [processor]
[ 5821.776000]  [<c0102458>] cpu_idle+0x98/0xe0
[ 5821.776000]  [<c03e3a85>] start_kernel+0x325/0x3b0
[ 5821.776000]  [<c03e31f0>] unknown_bootoption+0x0/0x260
[ 5821.776000]  =======================
[ 5821.776000] handlers:
[ 5821.776000] [<f08806a0>] (usb_hcd_irq+0x0/0x60 [usbcore])
[ 5821.776000] [<f0db5310>] (snd_intel8x0_interrupt+0x0/0x200 [snd_intel8x0m])
[ 5821.776000] Disabling IRQ #18
[ 5821.884000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5821.884000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5821.940000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5821.940000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5821.940000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5821.940000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5821.940000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5821.952000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5821.952000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5821.952000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5822.284000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5822.340000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5822.352000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5822.356000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5822.360000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5822.528000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5822.528000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5823.300000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5823.300000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5823.300000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.148000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.152000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.468000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.472000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.472000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.600000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.600000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.600000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.600000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.612000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.612000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.612000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.612000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.612000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.612000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.612000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.612000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.612000] scsi 0:0:0:0: rejecting I/O to dead device
[ 5824.612000] scsi 0:0:0:0: rejecting I/O to dead device

---

### Post by gorilla_au on 2008-01-01
I have a similar issue with the same piece of hardware (Segate Free Agent)

As a possible workaround, I have found that reloading the usb kernel module ehci-hcd would resolve this problem. (Might save some people a reboot.)

* # sudo modprobe -r ehci_hcd; sudo modprobe -v ehci_hcd*

kernel version: 2.6.22-14

---

### Post by MJN on 2008-01-02
This sort of issue, particularly where there exists a potential single point of failure (i.e. the hub) really needs a process of elimination to get to the bottom of.
 
Hence, try and beg, borrow, or steal another hub (preferably a completely different make/model) to try and see if the problem returns.
 
I know it's a pain but it's a surefire way of narrowing down the problem. I once spent weeks of research diagnosing why a particular USB webcam kept bombing out despite having worked fine for years. For some reason I was so sure it was a software/configuration issue (probably the fact that it only stopped working shortly after a majory system tweak) that I didn't get round to trying the cam on another machine. Lo and behold I did and managed to see the same problem - turns out the cable had gone bad.
 
Incidentally, is the hub powered?
 
Mathew

---

### Post by Daelyn on 2008-01-02
[http://ubuntuforums.org/showthread.php?t=210376](http://ubuntuforums.org/showthread.php?t=210376)

---

