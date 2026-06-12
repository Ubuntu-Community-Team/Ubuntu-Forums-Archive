---
title: "External Hard Drive Error"
date: 2009-08-27
forum: Hardware
---

### Post by Goombie on 2009-08-27
I have a Seagate 1TB  SATA hard drive, inside an Acommdata enclosure, plugged into a Belkin USB hub. the drive is currently formatted as NTFS with one big partition. Whenever I turn the drive on, Ubuntu can't see it, and I get the following error messages in dmesg:
```

[ 4090.872086] usb 1-6.1: new high speed USB device using ehci_hcd and address 17
[ 4090.967485] usb 1-6.1: configuration #1 chosen from 1 choice
[ 4090.978530] scsi6 : SCSI emulation for USB Mass Storage devices
[ 4090.981065] usb-storage: device found at 17
[ 4090.981070] usb-storage: waiting for device to settle before scanning
[ 4096.980227] usb-storage: device scan complete
[ 4103.076192] usb 1-6.1: reset high speed USB device using ehci_hcd and address 17
[ 4103.161276] usb 1-6.1: device descriptor read/64, error -71
[ 4103.364158] usb 1-6.1: device descriptor read/64, error -71
[ 4103.540111] usb 1-6.1: reset high speed USB device using ehci_hcd and address 17
[ 4103.624224] usb 1-6.1: device descriptor read/64, error -71
[ 4103.816193] usb 1-6.1: device descriptor read/64, error -71
[ 4103.992142] usb 1-6.1: reset high speed USB device using ehci_hcd and address 17
[ 4104.408020] usb 1-6.1: device not accepting address 17, error -71
[ 4104.480241] usb 1-6.1: reset high speed USB device using ehci_hcd and address 17
[ 4104.896021] usb 1-6.1: device not accepting address 17, error -71
[ 4104.896270] scsi 6:0:0:0: Device offlined - not ready after error recovery
[ 4104.896731] usb 1-6.1: USB disconnect, address 17
[ 4105.008119] usb 1-6.1: new high speed USB device using ehci_hcd and address 18
[ 4105.092108] usb 1-6.1: device descriptor read/64, error -71
[ 4105.280183] usb 1-6.1: device descriptor read/64, error -71
[ 4105.456147] usb 1-6.1: new high speed USB device using ehci_hcd and address 19
[ 4105.540142] usb 1-6.1: device descriptor read/64, error -71
[ 4105.728130] usb 1-6.1: device descriptor read/64, error -71
[ 4105.904096] usb 1-6.1: new high speed USB device using ehci_hcd and address 20
[ 4106.320026] usb 1-6.1: device not accepting address 20, error -71
[ 4106.392142] usb 1-6.1: new high speed USB device using ehci_hcd and address 21
[ 4106.810345] usb 1-6.1: device not accepting address 21, error -71
[ 4106.810419] hub 1-6:1.0: unable to enumerate USB device on port 1

```

I can't really tell what those messages mean, except that Ubuntu is having problems mounting the drive. Does anyone know what to do? Thanks in advance! :)

---

### Post by rockhopper on 2009-09-09
This looks like [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/387161](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/387161)

Removing the devicekit-disks package and reconnecting the disk was suggested in one of the comments there; and has worked for me.

---

