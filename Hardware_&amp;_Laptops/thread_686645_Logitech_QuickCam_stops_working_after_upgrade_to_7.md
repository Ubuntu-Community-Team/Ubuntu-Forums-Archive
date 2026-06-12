---
title: "Logitech QuickCam stops working after upgrade to 7.10"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by jharr on 2008-02-03
I had my Logitech Quickcam Communicate (model: 961443-0403) working in 7.04, and I believe 6.10. I was using 'motion' to capture frames (was using it as a security device), after my upgrade to 7.10 it no longer works. This is what I see in dmesg when I plug it in:

[INDENT][2171374.992246] usb 1-3: new full speed USB device using ohci_hcd and address 62
[2171375.195718] usb 1-3: configuration #1 chosen from 1 choice[/INDENT]

Further investigation reveals that there is no /dev/video* devices either, which is what the driver use setup. I've tried this with two of the same model and both do the exact same thing.

Any ideas?

---

