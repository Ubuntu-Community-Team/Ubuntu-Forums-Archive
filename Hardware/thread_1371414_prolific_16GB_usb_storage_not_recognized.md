---
title: "prolific 16GB usb storage not recognized?"
date: 2010-01-03
forum: Hardware
---

### Post by Ashrael on 2010-01-03
I have a A-data (067b:2528 Prolific Technology, Inc) 16 Gb usb storage, but ubuntu 8.10/9.04 do not recognize it, even though W*nd*ws XP does...

It sometimes is seen (lsusb) as 067b:2528 Prolific Technology, Inc., but (dmesg) says:

[ 2254.588043] usb 1-7: new high speed USB device using ehci_hcd and address 23
[ 2254.759222] usb 1-7: configuration #1 chosen from 1 choice
[ 2254.806618] scsi16 : SCSI emulation for USB Mass Storage devices
[ 2254.809484] usb-storage: device found at 23
[ 2254.809491] usb-storage: waiting for device to settle before scanning
[ 2259.809250] usb-storage: device scan complete
[ 2266.112055] usb 1-7: reset high speed USB device using ehci_hcd and address 23
[ 2281.224066] usb 1-7: device descriptor read/64, error -110
[ 2296.440069] usb 1-7: device descriptor read/64, error -110
[ 2296.656071] usb 1-7: reset high speed USB device using ehci_hcd and address 23

Looked all over the net for solution to this seemingly old problem, but to no avail...

Anybody have a clue how I am going to be able to use this stick?


TIA!

---

