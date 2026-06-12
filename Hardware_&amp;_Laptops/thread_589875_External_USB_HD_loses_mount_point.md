---
title: "External USB HD loses mount point"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by emullet on 2007-10-24
So I have a Seagate Free Agent 500 gb USB 2.0 drive. I've had no end of problems using it in Ubuntu. 

The latest problem is that after a while the drive will no longer be available to mount from /dev/sdb1 

When I plug the drive in and type dmesg | tail I get the following

[71210.844000] usb 5-8: new high speed USB device using ehci_hcd and address 21
[71225.956000] usb 5-8: device descriptor read/64, error -110
[71241.172000] usb 5-8: device descriptor read/64, error -110
[71241.388000] usb 5-8: new high speed USB device using ehci_hcd and address 22
[71246.408000] usb 5-8: device descriptor read/8, error -110
[71251.528000] usb 5-8: device descriptor read/8, error -110
[71251.744000] usb 5-8: new high speed USB device using ehci_hcd and address 23
[71256.764000] usb 5-8: device descriptor read/8, error -110
[71261.884000] usb 5-8: device descriptor read/8, error -110
[72066.480000] usb 5-8: new high speed USB device using ehci_hcd and address 24

I've googled to no avail to find out what error 110 is. Any help would be greatly appreciated.

---

### Post by surfed on 2007-11-11
I have had same problem and it turned out to be a defective enclosure.

---

