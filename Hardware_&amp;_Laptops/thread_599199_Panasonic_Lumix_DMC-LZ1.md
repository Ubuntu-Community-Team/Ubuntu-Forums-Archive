---
title: "Panasonic Lumix DMC-LZ1"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by greizer on 2007-11-01
Hello,
I'm experiencing trouble trying to import photos from my digicam Panasonic Lumix DMC-LZ1 under Kubuntu 7.10.

When I plug the camera a notification window opens and a camera icon appears at the desktop.
When I click on "open in new window" dolphin opens and comes up with an error message:
Unknown error code 50
Unspecified error
Please send a full bug report at [http://bugs.kde.org](http://bugs.kde.org)

I tried to import using digiKam and gThumb but it does not work as well. 
When I rightclick on the camera icon the menu does not even contain an unmount option.

Here is what appears in /var/log/messages:
Oct 28 10:35:51 smaakPC kernel: [ 544.576000] usb 2-2: new full speed USB device using ohci_hcd and address 3
Oct 28 10:35:51 smaakPC kernel: [ 544.792000] usb 2-2: configuration #1 chosen from 1 choice
Oct 28 10:35:51 smaakPC kernel: [ 544.792000] scsi3 : SCSI emulation for USB Mass Storage devices

lsusb output:
Bus 002 Device 004: ID 04da:2372 Panasonic (Matsushita) Lumix DMC-FZ10 Camera
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Under Kubuntu 7.04 on my Dell Latitude it works. 
The obvious difference is that 2 icons appear on the desktop: camera and usb stick. I also get two notification windows.
Accessing the camera does only work with the usb stick symbol, not with the camera one. The usb stick rightclick menu also allows me to unmout the camera.

/var/log/messages:
Oct 28 10:47:27 smaaklp kernel: [ 122.772000] usb 2-2: new full speed USB device using uhci_hcd and address 2
Oct 28 10:47:27 smaaklp kernel: [ 122.940000] usb 2-2: configuration #1 chosen from 1 choice
Oct 28 10:47:27 smaaklp kernel: [ 123.052000] usbcore: registered new interface driver libusual
Oct 28 10:47:27 smaaklp kernel: [ 123.072000] Initializing USB Mass Storage driver...
Oct 28 10:47:27 smaaklp kernel: [ 123.076000] scsi2 : SCSI emulation for USB Mass Storage devices
Oct 28 10:47:27 smaaklp kernel: [ 123.076000] usbcore: registered new interface driver usb-storage
Oct 28 10:47:27 smaaklp kernel: [ 123.076000] USB Mass Storage support registered.
Oct 28 10:47:32 smaaklp kernel: [ 128.080000] scsi 2:0:0:0: Direct-Access MATSHITA DMC-LZ1 0100 PQ: 0 ANSI: 2
Oct 28 10:47:32 smaaklp kernel: [ 128.088000] SCSI device sdb: 1000448 512-byte hdwr sectors (512 MB)
Oct 28 10:47:32 smaaklp kernel: [ 128.092000] sdb: Write Protect is off
Oct 28 10:47:32 smaaklp kernel: [ 128.100000] SCSI device sdb: 1000448 512-byte hdwr sectors (512 MB)
Oct 28 10:47:32 smaaklp kernel: [ 128.100000] sdb: Write Protect is off
Oct 28 10:47:32 smaaklp kernel: [ 128.100000] sdb: sdb1
Oct 28 10:47:32 smaaklp kernel: [ 128.116000] sd 2:0:0:0: Attached scsi removable disk sdb
Oct 28 10:47:32 smaaklp kernel: [ 128.116000] sd 2:0:0:0: Attached scsi generic sg2 type 0

lsusb:
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 04da:2372 Panasonic (Matsushita) Lumix DMC-FZ10 Camera
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 006: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 001 Device 005: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 001 Device 004: ID 0b97:7761 O2 Micro, Inc.
Bus 001 Device 003: ID 413c:a005 Dell Computer Corp.
Bus 001 Device 001: ID 0000:0000


Does anyone have an idea what I can do to solve this issue?
Thanks, Steffen

---

### Post by greizer on 2007-11-01
I think the reason is a bug in KDE:

[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/155788]("https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/155788")

---

### Post by ipelegri6 on 2008-04-21
I had the same problem with a DMC-FX33. I follow the suggestion made in [http://www.kubuntuforums.net/forums/index.php?topic=3091844](http://www.kubuntuforums.net/forums/index.php?topic=3091844) and I was able to get the pictures with digiKam only by switching the camera to the print position.
I hope it'll also work :-)

---

