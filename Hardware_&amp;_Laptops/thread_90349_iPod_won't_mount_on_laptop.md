---
title: "iPod won't mount on laptop"
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by Heliode on 2005-11-14
Good day, my fellow forum members!

I am puzzled with an issue I still seem to be having with my iPod... I'd hate to repost this, but the problem was never solved and upgrading to Breezy didn't fix it.

It works fine and all that. When I mount it on my PC (running Ubuntu Breezy) it mounts fine, and I can poke GTKpod at it all I want. However, when I connect it to my laptop, it simply refuses to mount! This puzzles me greatly, since both machines run Ubuntu, and even the same kernel version! (although the PC runs the SMP version). They even share the same sources.list. 

When I plug it into my laptop, I see this in dmesg:

```
usb 4-1: new high speed USB device using ehci_hcd and address 3
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
  Vendor: Apple     Model: iPod              Rev: 1.62
  Type:   Direct-Access                      ANSI SCSI revision: 00
usb-storage: device scan complete
SCSI device sda: 39063024 512-byte hdwr sectors (20000 MB)
sda: Write Protect is off
sda: Mode Sense: 64 00 00 08
sda: assuming drive cache: write through
SCSI device sda: 39063024 512-byte hdwr sectors (20000 MB)
sda: Write Protect is off
sda: Mode Sense: 64 00 00 08
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0: p1 p2
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0

```
But it just ends there, and doesn't mount the device.
When I try to mount sda2 (where I assume from dmesg the data partition is) manually, it fails, saying '/dev/sda2 is not a valid block device', and these messages start showing up in dmesg:

```

scsi0 (0:0): rejecting I/O to offline device
Buffer I/O error on device sda1, logical block 256
Buffer I/O error on device sda1, logical block 257
Buffer I/O error on device sda1, logical block 258
Buffer I/O error on device sda1, logical block 259

```

The iPod, meanwhile, displays the "Don't disconnect" message until I shutdown the laptop.

Here is the dmesg of the PC, which automatically mounts the iPod just fine (in a mountpoint aptly named after the iPods name, no less) spot in /media :

```

usb 5-8: new high speed USB device using ehci_hcd and address 6
scsi1 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 6
usb-storage: waiting for device to settle before scanning
  Vendor: Apple     Model: iPod              Rev: 1.62
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sde: 39063024 512-byte hdwr sectors (20000 MB)
sde: Write Protect is off
sde: Mode Sense: 64 00 00 08
sde: assuming drive cache: write through
SCSI device sde: 39063024 512-byte hdwr sectors (20000 MB)
sde: Write Protect is off
sde: Mode Sense: 64 00 00 08
sde: assuming drive cache: write through
 /dev/scsi/host1/bus0/target0/lun0: p1 p2
Attached scsi removable disk sde at scsi1, channel 0, id 0, lun 0
usb-storage: device scan complete
hdc: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
hdc: set_drive_speed_status: error=0xd0
ide: failed opcode was 100
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```

both machines have kernel version 2.6.12-9-686, and identical versions of HAL and dbus, so I am completely at a loss about what might cause this problem! It is great that the iPod works on my PC, but it would be even greater if I could add to/extract files from it while 'on the road' or at school, so if anyone has even the slightest idea what might be causing this problem, please let me know! The wierdest thing is that it has worked on every single PC I've tried it on, on a variety of OS's (Linux or otherwise), and on both USB 1.1 and 2.0 ports. In all cases it would at least mount. No such luck for the laptop though :(

Any thanks would be, as always, greatly appreciated!

---

