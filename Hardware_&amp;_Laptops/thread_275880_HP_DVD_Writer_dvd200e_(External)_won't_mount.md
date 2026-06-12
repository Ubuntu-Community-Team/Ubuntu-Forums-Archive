---
title: "HP DVD Writer dvd200e (External) won't mount"
date: 2006-10-12
forum: Hardware &amp; Laptops
---

### Post by mssever on 2006-10-12
I just bought a new in box external DVD burner (HP dvd200e; IEEE 1394 and USB connections) manufactured in November 2002 on eBay.

When I plug it in, Dapper detects the drive and sets up the appropriate device node and symlinks. However, I can't mount a CD or DVD.

Attempting to mount a CD:
```
sudo mount -t iso9660 /dev/disk/by-id/ieee1394-0060b0000501c665\:0\:0 /mnt
# Long (>60s) time delay here in which the drive can be heard to be doing something
mount: ieee1394-0060b0000501c665:0:0 is not a valid block device

```And /var/log/messages contains (from the time the drive was connected):
```
Oct 11 22:30:27 localhost kernel: [17200889.288000] scsi8 : SCSI emulation for IEEE-1394 SBP-2 Devices
Oct 11 22:30:28 localhost kernel: [17200890.404000] ieee1394: sbp2: Logged into SBP-2 device
Oct 11 22:30:28 localhost kernel: [17200890.420000]   Vendor: HP        Model: DVD Writer 200j   Rev: 1.36
Oct 11 22:30:28 localhost kernel: [17200890.420000]   Type:   CD-ROM                             ANSI SCSI revision: 00
Oct 11 22:31:30 localhost kernel: [17200952.896000] sr1: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
Oct 11 22:31:30 localhost kernel: [17200952.896000] sr 8:0:0:0: Attached scsi generic sg1 type 5
Oct 11 22:31:54 localhost kernel: [17200976.500000] sr: Current: sense key: Medium Error
Oct 11 22:31:54 localhost kernel: [17200976.500000]     Additional sense: Unable to recover table-of-contents
Oct 11 22:31:54 localhost kernel: [17200976.508000] sr: Current: sense key: Medium Error
Oct 11 22:31:54 localhost kernel: [17200976.508000]     Additional sense: Unable to recover table-of-contents
Oct 11 22:31:54 localhost kernel: [17200976.508000] cdrom: open failed.
Oct 11 22:32:26 localhost kernel: [17201008.568000] usb 3-4: USB disconnect, address 6
Oct 11 22:41:19 localhost kernel: [17201541.268000] sr: Current: sense key: Hardware Error
Oct 11 22:41:19 localhost kernel: [17201541.268000]     Additional sense: Tracking servo failure
Oct 11 22:41:49 localhost kernel: [17201571.272000] sr 8:0:0:0:
Oct 11 22:41:49 localhost kernel: [17201571.272000]         command: Read TOC/PMA/ATIP: 43 00 00 00 00 00 00 00 0c 00
Oct 11 22:41:59 localhost kernel: [17201581.272000] sr 8:0:0:0:
Oct 11 22:41:59 localhost kernel: [17201581.272000]         command: Test Unit Ready: 00 00 00 00 00 00
Oct 11 22:42:09 localhost kernel: [17201591.272000] sr 8:0:0:0:
Oct 11 22:42:09 localhost kernel: [17201591.272000]         command: Test Unit Ready: 00 00 00 00 00 00
Oct 11 22:42:29 localhost kernel: [17201611.276000] sr 8:0:0:0:
Oct 11 22:42:29 localhost kernel: [17201611.276000]         command: Test Unit Ready: 00 00 00 00 00 00
Oct 11 22:42:49 localhost kernel: [17201631.280000] sr 8:0:0:0:
Oct 11 22:42:49 localhost kernel: [17201631.280000]         command: Test Unit Ready: 00 00 00 00 00 00
Oct 11 22:42:49 localhost kernel: [17201631.280000] sr 8:0:0:0: scsi: Device offlined - not ready after error recovery
Oct 11 22:42:49 localhost kernel: [17201631.280000] cdrom: open failed.
```When I insert a video DVD, here's what I get in /var/log/messages:
```
Oct 12 00:39:43 localhost kernel: [17208645.228000] scsi9 : SCSI emulation for IEEE-1394 SBP-2 Devices
Oct 12 00:39:44 localhost kernel: [17208646.340000] ieee1394: sbp2: Logged into SBP-2 device
Oct 12 00:39:44 localhost kernel: [17208646.348000]   Vendor: HP        Model: DVD Writer 200j   Rev: 1.36
Oct 12 00:39:44 localhost kernel: [17208646.348000]   Type:   CD-ROM                             ANSI SCSI revision: 00
Oct 12 00:39:44 localhost kernel: [17208646.352000] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
Oct 12 00:39:44 localhost kernel: [17208646.356000] sr 9:0:0:0: Attached scsi generic sg0 type 5
Oct 12 00:41:14 localhost kernel: [17208735.980000] sr: Current: sense key: Medium Error
Oct 12 00:41:14 localhost kernel: [17208735.980000]     Additional sense: Unable to recover table-of-contents
Oct 12 00:41:14 localhost kernel: [17208735.984000] sr: Current: sense key: Medium Error
Oct 12 00:41:14 localhost kernel: [17208735.984000]     Additional sense: Unable to recover table-of-contents
Oct 12 00:41:14 localhost kernel: [17208735.996000] sr: Current: sense key: Medium Error
Oct 12 00:41:14 localhost kernel: [17208735.996000]     Additional sense: Unable to recover table-of-contents
``` The last two lines keep repeating while the light on the drive flashes.

Any idea how to make this work? Or is this a dud drive? I've never used IEEE 1394 before, but I get the same errors when hooked up via USB.

---

### Post by mssever on 2006-10-12
bump

---

### Post by mssever on 2006-10-13
Another bump

---

