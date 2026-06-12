---
title: "Monitor calibration fails"
date: 2018-09-25
forum: Hardware
---

### Post by SimonHGR on 2018-09-25
Hi, I'm trying to profile the monitors on my new install of Ubuntu 18.04. I have a ColorVision Spyder 2 (which I'm confident works, since I just pulled it from a windows machine that I'm hoping to finally move away from!)

Unfortunately, when I try to profile a monitor, I get to the point where the display changes to a grey transparent background with a white square marked "position your colorimeter here" (or words to that effect) and then I press "Start". At that point, it immediately fails saying "Internal Error"

dmesg shows the colorimeter was seen on the USB bus, but has no other information beyond that:

```
[   71.101113] usb 3-8: new low-speed USB device number 8 using xhci_hcd
[   71.256928] usb 3-8: New USB device found, idVendor=085c, idProduct=0200
[   71.256930] usb 3-8: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   71.256932] usb 3-8: Product: ColorVision Monitor Spyder
[   71.256934] usb 3-8: Manufacturer: ColorVision Inc.

```

---

