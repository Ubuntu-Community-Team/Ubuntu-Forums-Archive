---
title: "USB wont show up anywhere!"
date: 2012-07-01
forum: Hardware
---

### Post by JustSteph on 2012-07-01
My 16Gb Sandisk USB stick is not being detected anywhere on my laptop. When I plug it in, the light comes on for a few seconds, then goes off. It's not listed on disk utility, lsusb, fdisk -l or mount manager. The output of dmesg | tail is:

```
[ 2247.536114] usb 2-1: new high speed USB device using ehci_hcd and address 19
[ 2247.669228] usb 2-1: configuration #1 chosen from 1 choice
[ 2247.669485] scsi21 : SCSI emulation for USB Mass Storage devices
[ 2247.669704] usb-storage: device found at 19
[ 2247.669708] usb-storage: waiting for device to settle before scanning
[ 2250.580054] usb 2-1: USB disconnect, address 19
```It seems to be powering itself down before it's even mounted. My other memory sticks and my external hard drive are working fine. Is this a problem with ubuntu or has the memory stick had its day?

Thanks

---

