---
title: "Wierd iPod mounting issue"
date: 2005-08-13
forum: Hardware &amp; Laptops
---

### Post by Heliode on 2005-08-13
Good day, my fellow forum members!

I am puzzled with an issue I seem to be having with my new iPod (one of [these](http://www.apple.com/ipod/color/)).

It works fine and all that. When I mount it on my PC (running Ubuntu Hoary) it mounts fine, and I can poke GTKpod at it all I want. However, when I connect it to my laptop, it simply refuses to mount! This puzzles me greatly, since both machines run Ubuntu, and even the same kernel version! (although the PC runs the SMP version). They even share the same sources.list. 

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

The iPod, meanwhile, displays the "Don't disconnect" message until I shutdown the laptop!

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

both machines have kernel version 2.6.10-5-686, and identical versions of HAL and dbus, so I am completely at a loss about what might cause this problem! It is great that the iPod works on my PC, but it would be even greater if I could add to/extract files from it while 'on the road' or at school, so if anyone has even the slightest idea what might be causing this problem, please let me know!

Any thanks would be, as always, greatly appreciated!

---

### Post by PeP on 2005-08-13
to unplug it use eject /dev/sda ...

I have sometimes problems  with my laptop and my Ipod when the first is running low on bat and is supposed to power the second

---

### Post by varunus on 2005-08-13
Can you mount normal USB drives on your laptop?  Is gnome-volume-manager running?

---

### Post by Heliode on 2005-08-13
[QUOTE=varunus]Can you mount normal USB drives on your laptop?  Is gnome-volume-manager running?[/QUOTE]

Mouting other USB storage devices works just fine actually... I've tried with my 128 mb pen drive, a 256 mb mp3 player, and a 200 gb external hard drive, and all mount automatically once connected.
'ps ax' reports gnome-volume-manager chugging along nicely. 

Hmm... the mystery deepens, it seems!

Edit:
there is, however, a difference between what 'ps ax' reports on gnome-volume-manager on both machines.
on the PC:
```

11116 ?    Ss  0:00 gnome-volume-manager --sm-client-id default5

```
while the report on the laptop is a lot more verbose:
```
 
8685 ?    Ss     0:00 gnome-volume-manager --sm-config-prefix /gnome-volume-manager-upytgD/ --sm-client-id 117f000001000111486947500000083030002 --screen 0

``` 

I can't make sense of that at all, but perhaps someone here can?

---

