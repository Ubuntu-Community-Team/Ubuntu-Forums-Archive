---
title: "USB Drives not mounting (Edgy)"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by mogwai on 2006-11-07
No USB drives are being mounted on my installation. :confused: 
I have checked out the Device Manager and an entry is created when I plugin my drive(s).
'fdisk -l' yeilds nothing and dmesg shows:
```
[17179667.352000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[17179668.120000] usb 1-1: configuration #1 chosen from 1 choice
[17179668.128000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179668.128000] usb-storage: device found at 3
[17179668.128000] usb-storage: waiting for device to settle before scanning
[17179673.132000] usb-storage: device scan complete
[17179673.248000] usb 1-1: reset full speed USB device using uhci_hcd and address 3
[17179673.816000] usb 1-1: reset full speed USB device using uhci_hcd and address 3
[17179674.320000] usb 1-1: reset full speed USB device using uhci_hcd and address 3
[17179674.824000] usb 1-1: reset full speed USB device using uhci_hcd and address 3
```

From what I have seen, it appears that a block device is not being associated with the device. :-k 

Any suggestions?

---

### Post by Rexbron! on 2006-11-07
Is your problem like this?

[https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/65662](https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/65662)

---

### Post by mogwai on 2006-11-09
No. My problem seems to be worse.
It doesn't even seem to get to the stage of assigning a block device (eg: /dev/sdc).

btw - I am using Gnome, not KDE.

---

