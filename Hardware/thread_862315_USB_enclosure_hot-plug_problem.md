---
title: "USB enclosure hot-plug problem"
date: 2008-07-17
forum: Hardware
---

### Post by michaelbaranov on 2008-07-17
Hi, friends!
Any help appreciated!!!

PC: Toshiba Satellite p205 laptop
Enclosure: Acomdata Samba USB SATA/PATA enclosure with Hitachi SATA2 500GB drive.
Ubuntu: Hardy
Kernel: 2.6.24-16-generic, 2.6.24-19-generic

When hot-plugged in the enclosure is not detected. No /dev/* device created. Dmesg shows errors.
When cold-plugged (before boot) it is detected as /dev/sdb.
'sudo modprobe -r ehci_hcd' allows to hot-plug the enclosure once and works at ~1mb/s speed (USB 1.0?)
'lsusb' does not always list the device (it may appear on one call and disappear on subsequent calls)

dmesg has:
[  125.156023] usb 5-2: new high speed USB device using ehci_hcd and address 4
[  125.290192] usb 5-2: configuration #1 chosen from 1 choice
[  125.405864] usbcore: registered new interface driver libusual
[  125.431752] Initializing USB Mass Storage driver...
[  125.432294] scsi2 : SCSI emulation for USB Mass Storage devices
[  125.432850] usbcore: registered new interface driver usb-storage
[  125.432856] USB Mass Storage support registered.
[  125.433741] usb-storage: device found at 4
[  125.433746] usb-storage: waiting for device to settle before scanning
[  131.432050] usb-storage: device scan complete
[  137.040797] usb 5-2: reset high speed USB device using ehci_hcd and address 4
[  137.152754] usb 5-2: device descriptor read/64, error -71
[  137.368675] usb 5-2: device descriptor read/64, error -71
[  137.584601] usb 5-2: reset high speed USB device using ehci_hcd and address 4
[  137.696588] usb 5-2: device descriptor read/64, error -71
[  137.912464] usb 5-2: device descriptor read/64, error -71
[  138.128404] usb 5-2: reset high speed USB device using ehci_hcd and address 4
[  138.539259] usb 5-2: device not accepting address 4, error -71
[  138.647235] usb 5-2: reset high speed USB device using ehci_hcd and address 4
[  139.056073] usb 5-2: device not accepting address 4, error -71
[  139.056141] scsi 2:0:0:0: Device offlined - not ready after error recovery


More info here:
[https://bugs.launchpad.net/ubuntu/+bug/249218](https://bugs.launchpad.net/ubuntu/+bug/249218)

However, hot-plugging the same enclosure to my Ubuntu Hardy desktop works as expected 100%. The laptop hardware is 100% OK.

Thank you!!!

---

### Post by ultione on 2009-07-21
I have the same type of problem as you described.

Haven't tried the cold-plugged or hot-plugged as yet.

But for hot-plugged, one way to get it to be recognised as a high speed device that I found was,

sudo rmmod ehci_hcd (this changes USB 2.0 to USB 1.0, unloads the ehci module)

Then the Acomdata Ext USB enclosure gets recognised.

Then I go and type this
sudo modprobe ehci_hcd (this loads ehci module back in)

Now it is recognised properly as a High speed usb device.

Not sure why it works this way, seem to be a pain to have to do this all the time.
Oh I'm using kernel 2.6.15-53 Ubuntu 6.06 server

If anyone knows why this works, please do let me know.

---

