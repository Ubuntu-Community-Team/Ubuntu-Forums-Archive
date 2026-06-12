---
title: "touch screen doesn't wake up"
date: 2011-07-21
forum: Hardware
---

### Post by ivzave on 2011-07-21
Hi. My Gigabyte T1005P's touchscreen doesn't work after warm reboot or suspend. I've attached more info (lspci, lsusb, lshw before restart and dmesg after restart).

dmesg shows such strings (extract):
```

[    5.820160] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   20.940137] usb 3-2: device descriptor read/64, error -110
[   36.170130] usb 3-2: device descriptor read/64, error -110
[   36.400880] usb 3-2: new full speed USB device using uhci_hcd and address 3
[   51.520157] usb 3-2: device descriptor read/64, error -110
[   66.750186] usb 3-2: device descriptor read/64, error -110
[   66.980198] usb 3-2: new full speed USB device using uhci_hcd and address 4
[   72.001818] usb 3-2: device descriptor read/8, error -110
[   77.132257] usb 3-2: device descriptor read/8, error -110
[   77.360167] usb 3-2: new full speed USB device using uhci_hcd and address 5
[   82.381629] usb 3-2: device descriptor read/8, error -110
[   87.512069] usb 3-2: device descriptor read/8, error -110
[   87.620200] hub 3-0:1.0: unable to enumerate USB device on port 2

```Any help appreciated.

---

