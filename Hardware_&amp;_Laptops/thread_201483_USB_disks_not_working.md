---
title: "USB disks not working"
date: 2006-06-21
forum: Hardware &amp; Laptops
---

### Post by bushda on 2006-06-21
I'm having no luck getting USB jump drives working. It doesn't matter if it's one of my digital camera (1 Aiptek IS-DV and 1 Olympus C-740), a Lexar card reader, or a Lexar 64 MB jump drive. 

dmesg always gives results similar to this:

[17180075.816000] usb 3-1: new full speed USB device using uhci_hcd and address 10
[17180075.936000] usb 3-1: device descriptor read/64, error -71
[17180076.160000] usb 3-1: device descriptor read/64, error -71
[17180076.376000] usb 3-1: new full speed USB device using uhci_hcd and address 11
[17180076.496000] usb 3-1: device descriptor read/64, error -71
[17180076.720000] usb 3-1: device descriptor read/64, error -71
[17180076.936000] usb 3-1: new full speed USB device using uhci_hcd and address 12
[17180077.344000] usb 3-1: device not accepting address 12, error -71
[17180077.456000] usb 3-1: new full speed USB device using uhci_hcd and address 13
[17180077.864000] usb 3-1: device not accepting address 13, error -71

While all of these fail, other USB things seem to be working fine. My Logitech Quick Cam is working fine. 

Help!

---

