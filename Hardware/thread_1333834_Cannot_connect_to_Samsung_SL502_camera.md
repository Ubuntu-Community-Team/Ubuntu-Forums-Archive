---
title: "Cannot connect to Samsung SL502 camera"
date: 2009-11-21
forum: Hardware
---

### Post by lallha on 2009-11-21
I bought a Samsung SL502 from Costco and I am unable to connect to it through USB with ubuntu to download my pictures.

The camera is set to USB Computer mode, and when I attach it, I get the following output via dmesg:

```
[2975289.448028] usb 4-2: new full speed USB device using uhci_hcd and address 2
[2975289.568032] usb 4-2: device descriptor read/64, error -71
[2975289.792019] usb 4-2: device descriptor read/64, error -71
[2975290.008027] usb 4-2: new full speed USB device using uhci_hcd and address 3
[2975290.128032] usb 4-2: device descriptor read/64, error -71
[2975290.352027] usb 4-2: device descriptor read/64, error -71
[2975290.568039] usb 4-2: new full speed USB device using uhci_hcd and address 4
[2975290.976026] usb 4-2: device not accepting address 4, error -71
[2975291.088033] usb 4-2: new full speed USB device using uhci_hcd and address 5
[2975291.496039] usb 4-2: device not accepting address 5, error -71
[2975291.496064] hub 4-0:1.0: unable to enumerate USB device on port 2
```

---

