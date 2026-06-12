---
title: "Error msg when connecting SE mobile phone"
date: 2009-08-03
forum: Hardware
---

### Post by sandydoull on 2009-08-03
When I connect my mobile phone via USB cable, I am not able to access it in ubuntu, I receive the following dmesg output:

```
dmesg|tail
[  624.888134] usb 2-1: device descriptor read/64, error -71
[  625.112133] usb 2-1: device descriptor read/64, error -71
[  625.328144] usb 2-1: new full speed USB device using uhci_hcd and address 7
[  625.448134] usb 2-1: device descriptor read/64, error -71
[  625.672115] usb 2-1: device descriptor read/64, error -71
[  625.888093] usb 2-1: new full speed USB device using uhci_hcd and address 8
[  626.296068] usb 2-1: device not accepting address 8, error -71
[  626.408090] usb 2-1: new full speed USB device using uhci_hcd and address 9
[  626.816083] usb 2-1: device not accepting address 9, error -71
[  626.816127] hub 2-0:1.0: unable to enumerate USB device on port 1
```

---

