---
title: "USB storage corruption problem in Breezy"
date: 2005-11-07
forum: Hardware &amp; Laptops
---

### Post by Adapted.Cat on 2005-11-07
Hi all,

I have linux-image-2.6.12-9-k7 installed, with standard modules etc, and a big SATA drive in an external USB 2.0 enclosure. All seems to be going well, copying back and forth, except that occasionally (and it's usually the boot block or root folder here) instead of data being stored on the drive I get USB traffic stored on the drive. For example, here is a dump of data close to the start of my filesystem:
```
000001f0: 0000 0000 0000 0000 0000 0000 0000 55aa  ..............U.
00000200: 5252 6141 0000 0000 0000 0000 0000 0000  RRaA............
00000210: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00000220: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00000230: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00000240: 5553 4243 b3ba 0d00 0002 0000 0000 0a2a  USBC...........*
00000250: 0017 4a1c 8300 0001 0000 0000 0000 0000  ..J.............
00000260: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00000270: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00000280: 5252 6141 0000 0000 0000 0000 0000 0000  RRaA............
00000290: 0000 0000 0000 0000 0000 0000 0000 0000  ................
000002a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
000002b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
000002c0: 5553 4243 b3ba 0d00 0002 0000 0000 0a2a  USBC...........*
000002d0: 0017 4a1c 8300 0001 0000 0000 0000 0000  ..J.............
000002e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
000002f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00000300: 5252 6141 0000 0000 0000 0000 0000 0000  RRaA............

```

There is no way this stuff should be on my hard disk. USBC is a USB protocol magic number - I think there's a USBS going the other way, but I haven't seen that on the drive. I just spent all of last night and tonight recovering data from a FAT partition and an XFS partition (the latter was so much easier!) after the root directory of each died when moving files from one to the other.

And yet for the most part, everything functions normally. The drive certainly works under windows - at least I haven't seen any problems there - but under linux every so often there's a catastrophic glitch that messes up the drive.

Here are my USB modules:
```
usb_storage            74560  4
usbhid                 35552  0
usbcore               118204  5 usb_storage,usbhid,ehci_hcd,uhci_hcd
scsi_mod              135944  3 sd_mod,usb_storage,libata
ide_core              139028  5 usb_storage,ide_cd,ide_disk,ide_generic,via82cxxx

```

Here are the specs from usbview showing the device:
```
JM20338 SATA, USB Combo
Manufacturer: JMicron
Serial Number: 860888788888
Speed: 480Mb/s (high)
USB Version:  2.00
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 64
Number of Configurations: 1
Vendor Id: 152d
Product Id: 2338
Revision Number:  1.00

Config Number: 1
	Number of Interfaces: 1
	Attributes: c0
	MaxPower Needed:   2mA

	Interface Number: 0
		Name: usb-storage
		Alternate Number: 0
		Class: 08(stor.) 
		Sub Class: 6
		Protocol: 50
		Number of Endpoints: 2

			Endpoint Address: 81
			Direction: in
			Attribute: 2
			Type: Bulk
			Max Packet Size: 512
			Interval: 0ms

			Endpoint Address: 02
			Direction: out
			Attribute: 2
			Type: Bulk
			Max Packet Size: 512
			Interval: 0ms

```

Here are the excerpts from dmesg:
```
Nov  8 00:27:22 adapted kernel: [4294677.690000] usbcore: registered new driver usbfs
Nov  8 00:27:22 adapted kernel: [4294677.690000] usbcore: registered new driver hub
Nov  8 00:27:22 adapted kernel: [4294677.690000] USB Universal Host Controller Interface driver v2.2
Nov  8 00:27:22 adapted kernel: [4294677.690000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
Nov  8 00:27:22 adapted kernel: [4294677.690000] PCI: Via IRQ fixup for 0000:00:10.0, from 0 to 5
Nov  8 00:27:22 adapted kernel: [4294677.690000] uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Nov  8 00:27:22 adapted kernel: [4294677.752000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Nov  8 00:27:22 adapted kernel: [4294677.752000] uhci_hcd 0000:00:10.0: irq 21, io base 0x00008400
Nov  8 00:27:22 adapted kernel: [4294677.752000] hub 1-0:1.0: USB hub found
Nov  8 00:27:22 adapted kernel: [4294677.752000] hub 1-0:1.0: 2 ports detected
Nov  8 00:27:22 adapted kernel: [4294677.755000] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
Nov  8 00:27:22 adapted kernel: [4294677.755000] PCI: Via IRQ fixup for 0000:00:10.1, from 0 to 5
Nov  8 00:27:22 adapted kernel: [4294677.755000] uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Nov  8 00:27:22 adapted kernel: [4294677.817000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Nov  8 00:27:22 adapted kernel: [4294677.817000] uhci_hcd 0000:00:10.1: irq 21, io base 0x00008000
Nov  8 00:27:22 adapted kernel: [4294677.817000] hub 2-0:1.0: USB hub found
Nov  8 00:27:22 adapted kernel: [4294677.817000] hub 2-0:1.0: 2 ports detected
Nov  8 00:27:22 adapted kernel: [4294677.820000] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
Nov  8 00:27:22 adapted kernel: [4294677.820000] PCI: Via IRQ fixup for 0000:00:10.2, from 0 to 5
Nov  8 00:27:22 adapted kernel: [4294677.820000] uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
Nov  8 00:27:22 adapted kernel: [4294677.882000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Nov  8 00:27:22 adapted kernel: [4294677.882000] uhci_hcd 0000:00:10.2: irq 21, io base 0x00007800
Nov  8 00:27:22 adapted kernel: [4294677.882000] hub 3-0:1.0: USB hub found
Nov  8 00:27:22 adapted kernel: [4294677.882000] hub 3-0:1.0: 2 ports detected
Nov  8 00:27:22 adapted kernel: [4294677.885000] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
Nov  8 00:27:22 adapted kernel: [4294677.885000] PCI: Via IRQ fixup for 0000:00:10.3, from 0 to 5
Nov  8 00:27:22 adapted kernel: [4294677.885000] uhci_hcd 0000:00:10.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#4)
Nov  8 00:27:22 adapted kernel: [4294677.921000] usb 1-1: new low speed USB device using uhci_hcd and address 2
Nov  8 00:27:22 adapted kernel: [4294677.947000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Nov  8 00:27:22 adapted kernel: [4294677.947000] uhci_hcd 0000:00:10.3: irq 21, io base 0x00007400
Nov  8 00:27:22 adapted kernel: [4294677.947000] hub 4-0:1.0: USB hub found
Nov  8 00:27:22 adapted kernel: [4294677.947000] hub 4-0:1.0: 2 ports detected
Nov  8 00:27:22 adapted kernel: [4294677.978000] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
Nov  8 00:27:22 adapted kernel: [4294677.978000] PCI: Via IRQ fixup for 0000:00:10.4, from 0 to 5
Nov  8 00:27:22 adapted kernel: [4294677.978000] ehci_hcd 0000:00:10.4: VIA Technologies, Inc. USB 2.0
Nov  8 00:27:22 adapted kernel: [4294677.978000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Nov  8 00:27:22 adapted kernel: [4294677.978000] ehci_hcd 0000:00:10.4: irq 21, io mem 0xde000000
Nov  8 00:27:22 adapted kernel: [4294677.978000] ehci_hcd 0000:00:10.4: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
Nov  8 00:27:22 adapted kernel: [4294677.979000] hub 5-0:1.0: USB hub found
Nov  8 00:27:22 adapted kernel: [4294677.979000] hub 5-0:1.0: 8 ports detected

Nov  8 00:27:22 adapted kernel: [4294679.497000] usb 5-2: new high speed USB device using ehci_hcd and address 3
Nov  8 00:27:22 adapted kernel: [4294679.739000] usb 1-1: new low speed USB device using uhci_hcd and address 4
Nov  8 00:27:22 adapted kernel: [4294680.044000] usbcore: registered new driver hiddev
Nov  8 00:27:22 adapted kernel: [4294680.140000] input: USB HID v1.10 Joystick [Saitek Cyborg 3D Rumble Force] on usb-0000:00:10.0-1
Nov  8 00:27:22 adapted kernel: [4294680.140000] usbcore: registered new driver usbhid
Nov  8 00:27:22 adapted kernel: [4294680.140000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
Nov  8 00:27:22 adapted kernel: [4294680.176000] Initializing USB Mass Storage driver...
Nov  8 00:27:22 adapted kernel: [4294680.177000] scsi2 : SCSI emulation for USB Mass Storage devices
Nov  8 00:27:22 adapted kernel: [4294680.177000] usbcore: registered new driver usb-storage
Nov  8 00:27:22 adapted kernel: [4294680.177000] USB Mass Storage support registered.

```

Here are some log lines from when things were really bad...
```
Nov  5 14:35:24 adapted kernel: [4313559.443000] xfs_force_shutdown(sda1,0x8) called from line 3311 of file fs/xfs/xfs_inode.c.  Return address = 0xf96aa749

Nov  5 17:10:05 adapted kernel: [4322841.683000] usb 5-4: reset high speed USB device using ehci_hcd and address 6
Nov  5 17:10:05 adapted kernel: [4322842.071000] usb 5-4: reset high speed USB device using ehci_hcd and address 6
Nov  5 17:10:05 adapted kernel: [4322842.459000] usb 5-4: reset high speed USB device using ehci_hcd and address 6
Nov  5 17:10:06 adapted kernel: [4322842.924000] usb 5-4: reset high speed USB device using ehci_hcd and address 6
Nov  5 17:10:06 adapted kernel: [4322843.326000] scsi: Device offlined - not ready after error recovery: host 5 channel 0 id 0 lun 0
Nov  5 17:10:06 adapted kernel: [4322843.326000] SCSI error : <5 0 0 0> return code = 0x50000
Nov  5 17:10:06 adapted kernel: [4322843.326000] end_request: I/O error, dev sda, sector 75567791
Nov  5 17:10:06 adapted kernel: [4322843.326000] usb 5-4: USB disconnect, address 6
Nov  5 17:10:06 adapted kernel: [4322843.597000] xfs_force_shutdown(sda1,0x1) called from line 353 of file fs/xfs/xfs_rw.c.  Return address = 0xf96cc400
Nov  5 17:10:07 adapted kernel: [4322843.668000] usb 5-4: new high speed USB device using ehci_hcd and address 7
Nov  5 17:10:07 adapted kernel: [4322844.056000] usb 5-4: new high speed USB device using ehci_hcd and address 8
Nov  5 17:10:07 adapted kernel: [4322844.445000] usb 5-4: new high speed USB device using ehci_hcd and address 9
Nov  5 17:10:08 adapted kernel: [4322844.909000] usb 5-4: new high speed USB device using ehci_hcd and address 10
Nov  5 17:15:23 adapted kernel: [4323160.155000] xfs_force_shutdown(sda1,0x1) called from line 353 of file fs/xfs/xfs_rw.c.  Return address = 0xf96cc400
Nov  5 17:15:36 adapted shutdown[18765]: shutting down for system reboot
Nov  5 17:15:36 adapted kernel: [4323173.639000] xfs_force_shutdown(sda1,0x1) called from line 353 of file fs/xfs/xfs_rw.c.  Return address = 0xf96cc400


Nov  7 00:57:53 adapted kernel: [4294968.609000] usb 5-4: new high speed USB device using ehci_hcd and address 3
Nov  7 00:57:54 adapted kernel: [4294968.828000] Initializing USB Mass Storage driver...
Nov  7 00:57:54 adapted kernel: [4294968.833000] scsi2 : SCSI emulation for USB Mass Storage devices
Nov  7 00:57:54 adapted kernel: [4294968.835000] usbcore: registered new driver usb-storage
Nov  7 00:57:54 adapted kernel: [4294968.835000] USB Mass Storage support registered.
Nov  7 00:57:54 adapted usb.agent[9314]:      usb-storage: loaded successfully
Nov  7 00:57:59 adapted kernel: [4294973.835000]   Vendor: Maxtor 6  Model: L608JR7G          Rev: BANC
Nov  7 00:57:59 adapted kernel: [4294973.835000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Nov  7 00:57:59 adapted kernel: [4294973.902000] SCSI device sda: 586114704 512-byte hdwr sectors (300091 MB)
Nov  7 00:57:59 adapted kernel: [4294973.905000] SCSI device sda: 586114704 512-byte hdwr sectors (300091 MB)
Nov  7 00:57:59 adapted kernel: [4294973.905000]  /dev/scsi/host2/bus0/target0/lun0: p1 p2
Nov  7 00:57:59 adapted kernel: [4294973.926000] Attached scsi disk sda at scsi2, channel 0, id 0, lun 0
Nov  7 00:57:59 adapted scsi.agent[9376]:      sd_mod: loaded sucessfully (for disk)
Nov  7 01:06:06 adapted kernel: [4295461.070000] loop: loaded (max 8 devices)
Nov  7 01:07:33 adapted kernel: ] FAT: Filesystem panic (dev sda2)
Nov  7 01:24:16 adapted kernel: [4296551.823000] XFS mounting filesystem sda1
Nov  7 01:24:16 adapted kernel: [4296551.928000] XFS: nil uuid in log - IRIX style log
Nov  7 01:24:16 adapted kernel: [4296551.939000] Starting XFS recovery on filesystem: sda1 (dev: sda1)
Nov  7 01:24:16 adapted kernel: [4296551.940000] XFS: dirty log written in incompatible format - can't recover
Nov  7 01:24:16 adapted kernel: [4296551.940000] XFS: log mount/recovery failed: error 5
Nov  7 01:24:16 adapted kernel: [4296551.940000] XFS: log mount failed
Nov  7 01:25:33 adapted kernel: [4296628.534000] XFS mounting filesystem sda1

```

And some really freaky errors from XFS itself (VFAT driver is a little less verbose):
```
Nov  7 00:12:43 adapted kernel: <0x99 [xfs]
Nov  7 00:12:43 adapted kernel: [4310099.007000]  [real_lookup+192/224] real_lookup+0xc0/0xe0
Nov  7 00:12:43 adapted kernel: [4310099.007000]  [do_lookup+157/168] do_lookup+0x9d/0xa8
Nov  7 00:12:43 adapted kernel: [4310099.007000]  [__link_path_walk+2252/3616] __link_path_walk+0x8cc/0xe20
Nov  7 00:12:43 adapted kernel: [4310099.007000]  [link_path_walk+83/245] link_path_walk+0x53/0xf5
Nov  7 00:12:43 adapted kernel: [4310099.007000]  [pty_write+99/117] pty_write+0x63/0x75
Nov  7 00:12:43 adapted kernel: [4310099.007000]  [tty_write+483/568] tty_write+0x1e3/0x238
Nov  7 00:12:43 adapted kernel: [4310099.007000]  [path_lookup+119/266] path_lookup+0x77/0x10a
Nov  7 00:12:43 adapted kernel: [4310099.007000]  [__user_walk+51/92] __user_walk+0x33/0x5c
Nov  7 00:12:43 adapted kernel: [4310099.007000]  [vfs_lstat+28/100] vfs_lstat+0x1c/0x64
Nov  7 00:12:43 adapted kernel: [4310099.007000]  [tty_write+483/568] tty_write+0x1e3/0x238
Nov  7 00:12:43 adapted kernel: [4310099.007000]  [sys_lstat64+24/54] sys_lstat64+0x18/0x36
Nov  7 00:12:43 adapted kernel: [4310099.007000]  [schedule+771/1445] schedule+0x303/0x5a5
Nov  7 00:12:43 adapted kernel: [4310099.007000]  [sysenter_past_esp+84/117] sysenter_past_esp+0x54/0x75
Nov  7 00:12:43 adapted kernel: [4310099.009000]  [pg0+959629357/1069855744] xfs_da_do_buf+0x881/0x927 [xfs]
Nov  7 00:12:43 adapted kernel: [4310099.009000]  [pg0+959629669/1069855744] xfs_da_read_buf+0x47/0x4b [xfs]
Nov  7 00:12:43 adapted last message repeated 2 times
Nov  7 00:12:43 adapted kernel: [4310099.009000]  [pg0+959646069/1069855744] xfs_dir2_block_lookup_int+0x52/0x1b8 [xfs]
Nov  7 00:12:43 adapted kernel: [4310099.009000]  [pg0+959646069/1069855744] xfs_dir2_block_lookup_int+0x52/0x1b8 [xfs]
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [pg0+959645795/1069855744] xfs_dir2_block_lookup+0x2f/0xef [xfs]
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [pg0+959641407/1069855744] xfs_dir2_isblock+0x2c/0x74 [xfs]
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [pg0+959638953/1069855744] xfs_dir2_lookup+0x156/0x166 [xfs]
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [activate_task+100/119] activate_task+0x64/0x77
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [pg0+959844870/1069855744] xfs_dir_lookup_int+0x4c/0x144 [xfs]
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [__wake_up_common+56/87] __wake_up_common+0x38/0x57
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [pg0+959868439/1069855744] xfs_lookup+0x55/0x8a [xfs]
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [pg0+959920626/1069855744] linvfs_lookup+0x52/0x99 [xfs]
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [real_lookup+192/224] real_lookup+0xc0/0xe0
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [do_lookup+157/168] do_lookup+0x9d/0xa8
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [__link_path_walk+2252/3616] __link_path_walk+0x8cc/0xe20
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [link_path_walk+83/245] link_path_walk+0x53/0xf5
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [pty_write+99/117] pty_write+0x63/0x75
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [tty_write+483/568] tty_write+0x1e3/0x238
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [path_lookup+119/266] path_lookup+0x77/0x10a
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [__user_walk+51/92] __user_walk+0x33/0x5c
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [vfs_lstat+28/100] vfs_lstat+0x1c/0x64
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [tty_write+483/568] tty_write+0x1e3/0x238
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [sys_lstat64+24/54] sys_lstat64+0x18/0x36
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [schedule+771/1445] schedule+0x303/0x5a5
Nov  7 00:12:43 adapted kernel: [4310099.010000]  [sysenter_past_esp+84/117] sysenter_past_esp+0x54/0x75
Nov  7 00:12:43 adapted kernel: [4310099.012000]  [pg0+959629357/1069855744] xfs_da_do_buf+0x881/0x927 [xfs]
Nov  7 00:12:43 adapted kernel: [4310099.012000]  [pg0+959629669/1069855744] xfs_da_read_buf+0x47/0x4b [xfs]

```
My scheduler is:
noop [anticipatory] deadline cfq

I notice that someone else posted recently about usb problems, but I think this error is slightly different - correct me if I'm wrong.

Can anybody help? Is this a kernel module bug? Is there a "be nice to the USB device and be safe" option to usb-storage?

---

### Post by Adapted.Cat on 2005-11-08
I think this is a kernel bug:

[http://bugzilla.kernel.org/show_bug.cgi?id=3505](http://bugzilla.kernel.org/show_bug.cgi?id=3505)

To answer my own question, apparently "rmmod ehci" can increase stability at the expense of speed.

---

### Post by mike3k on 2006-12-28
That JMicron chipset has problems. I'm using an external drive in a SATA to USB enclosure which uses the JMicron 2338 on my MacBook Pro (the drive in the enclosure is my old internal, which I removed when I upgraded it). In heavy use, the drive will suddenly hang with the access light on steady and my computer will lock up. A google search turned up several reports of problems with that chipset.

---

### Post by fortran01 on 2007-01-25
I also have this problem on Dapper Drake (6.06 LTS), kernel 2.6.15-27-386
The chipset of the USB-IDE cable is "ID 067b:2507 Prolific Technology, Inc." (please see output of lsusb -vv below).

I got the following messages in dmesg:
usb 5-2: reset high speed USB device using ehci_hcd and address 4

For some reason, the transfer from the hard drive to the PC via the USB-IDE cable **stalls**. *Adapted.Cat* is right, unloading the ehci_hcd module increases stability at the expense of speed:

```
rmmod ehci_hcd
```

lsusb -vv

```
Bus 001 Device 003: ID 067b:2507 Prolific Technology, Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x067b Prolific Technology, Inc.
  idProduct          0x2507
  bcdDevice            1.00
  iManufacturer           1 Prolific Technology Inc.
  iProduct                2 Mass Storage Device
  iSerial                 3 00
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered
```

---

### Post by Enverex on 2007-01-25
Just incase anyone was wondering, EHCI is the USB2 controler, so if you unload that then you lose USB2 (480Mb/s) and fall back to USB1.1 (11Mb/s). I'd look at reporting it to the right people as that's going to cripple speeds if you're using drives on it.

---

### Post by fortran01 on 2007-01-25
I am still getting the error in my custom compiled **2.6.18 Linux kernel**. I will try to turn on debugging in the kernel, and post the results tomorrow.

---

