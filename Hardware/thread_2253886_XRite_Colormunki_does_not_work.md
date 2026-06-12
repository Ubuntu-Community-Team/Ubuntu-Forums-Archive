---
title: "XRite Colormunki does not work"
date: 2014-11-23
forum: Hardware
---

### Post by ubootfanat on 2014-11-23
Hi there,

I recently upgraded my hardware from Surface Pro 2 to Surface Pro 3 running Ubuntu Gnome 13.10 and 14.10, respectively.

Issue: my Colormunki stopped working. It is still working on the Surface Pro 2.
To be exact, I suspect that the xhci drivers are the ones to blame.

Anyhow, here the syslog of plugging in the colormunki:
```
... kernel: [ 5254.234412] usb 1-1.2: new full-speed USB device number 13 using xhci_hcd
... kernel: [ 5254.337159] usb 1-1.2: New USB device found, idVendor=0765, idProduct=5020
... kernel: [ 5254.337169] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
... kernel: [ 5254.337174] usb 1-1.2: Product: ColorMunki Display
... kernel: [ 5254.337178] usb 1-1.2: Manufacturer: X-Rite, Inc.
... kernel: [ 5254.339462] hid-generic 0003:0765:5020.0008: hiddev0,hidraw6: USB HID v1.11 Device [X-Rite, Inc. ColorMunki Display] on usb-0000:00:14.0-1.2/input0
... colord: Sensor added: i1-display3-00

```
looks good isn't it?

Now the Gnome Colormanagement pops up. Nice. I select the display I want to calibrate and fight my way through the wizard. The software asks me to put the calibration hardware on the screen and press "start". I press start and this happens:
```
... kernel: [ 5289.101483] usb 1-1.2: reset full-speed USB device number 13 using xhci_hcd
... kernel: [ 5289.101560] xhci_hcd 0000:00:14.0: Setup ERROR: setup context command for slot 14.
... kernel: [ 5289.101571] usb 1-1.2: hub failed to enable device, error -22
... kernel: [ 5289.185240] usb 1-1.2: reset full-speed USB device number 13 using xhci_hcd
... kernel: [ 5289.185281] xhci_hcd 0000:00:14.0: Setup ERROR: setup context command for slot 14.
... kernel: [ 5289.185286] usb 1-1.2: hub failed to enable device, error -22
... kernel: [ 5289.269252] usb 1-1.2: reset full-speed USB device number 13 using xhci_hcd
... kernel: [ 5289.285925] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801d3c954c8
... kernel: [ 5289.285933] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801d3c95480

```
and thats the bummer. Unrecoverable Error is what the software says.

removing the device says:
```
... kernel: [ 5771.200481] usb 1-1.2: USB disconnect, device number 13
... colord: Sensor removed: i1-display3-00

```

Any ideas? Thanks in advance!
ubootfanat

---

