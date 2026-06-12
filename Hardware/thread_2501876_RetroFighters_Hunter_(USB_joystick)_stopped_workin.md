---
title: "RetroFighters Hunter (USB joystick) stopped working"
date: 2024-10-24
forum: Hardware
---

### Post by msknight on 2024-10-24
Since upgrading to Ubuntu 24.04.1 LTS Cinamon 6.0.4 kernel 6.8.0-45-generic, the USB dongle of the RetroFighters Hunter joypad is no longer showing up in jstest. Grateful for any thoughts as I'm willing to bet that all their controllers are identifying the same way, then likely all their joysticks are suffering the same.

Syslog says...

```
2024-10-24T08:54:53.458178+01:00 mich-desktop kernel: usb 1-6.1: new full-speed USB device number 77 using xhci_hcd  
2024-10-24T08:54:53.560147+01:00 mich-desktop kernel: usb 1-6.1: New USB device found, idVendor=057e, idProduct=2009, bcdDevice= 2.00  
2024-10-24T08:54:53.560174+01:00 mich-desktop kernel: usb 1-6.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3  
2024-10-24T08:54:53.560178+01:00 mich-desktop kernel: usb 1-6.1: Product: Pro Controller  
2024-10-24T08:54:53.560181+01:00 mich-desktop kernel: usb 1-6.1: Manufacturer: Nintendo Co., Ltd.  
2024-10-24T08:54:53.560183+01:00 mich-desktop kernel: usb 1-6.1: SerialNumber: 000000000001  
2024-10-24T08:54:53.568087+01:00 mich-desktop kernel: nintendo 0003:057E:2009.0021: hidraw8: USB HID v81.11 Joystick [Nintendo Co., Ltd. Pro Controller] on usb-0000:00:14.0-6.1/input0  
2024-10-24T08:54:55.696146+01:00 mich-desktop kernel: nintendo 0003:057E:2009.0021: Failed to set baudrate; ret=-110  
2024-10-24T08:54:55.696172+01:00 mich-desktop kernel: nintendo 0003:057E:2009.0021: Failed to initialize controller; ret=-110  
2024-10-24T08:54:55.698092+01:00 mich-desktop kernel: nintendo 0003:057E:2009.0021: probe - fail = -110  
2024-10-24T08:54:55.698114+01:00 mich-desktop kernel: nintendo: probe of 0003:057E:2009.0021 failed with error -110  
2024-10-24T08:54:55.732840+01:00 mich-desktop mtp-probe: checking bus 1, device 77: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6.1"  
2024-10-24T08:54:55.732981+01:00 mich-desktop mtp-probe: bus: 1, device: 77 was not an MTP device  
2024-10-24T08:54:55.760126+01:00 mich-desktop mtp-probe: checking bus 1, device 77: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6.1"  
2024-10-24T08:54:55.760197+01:00 mich-desktop mtp-probe: bus: 1, device: 77 was not an MTP device
```

---

