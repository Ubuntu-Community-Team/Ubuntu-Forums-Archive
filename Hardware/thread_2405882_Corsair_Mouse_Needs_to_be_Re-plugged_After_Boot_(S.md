---
title: "Corsair Mouse Needs to be Re-plugged After Boot (Sometimes)"
date: 2018-11-12
forum: Hardware
---

### Post by patreek on 2018-11-12
After booting Ubuntu, my wired Corsair RGP0030 mouse will sometimes need to be re-plugged for it to work.  This never happens when going into my BIOS settings or booting into Windows.  So far, I haven't noticed this problem during cold boots or running live versions of Ubuntu.  Also, the LED light on the mouse seems to stay lit well past booting Ubuntu.  Seems to turn off around the time the desktop is loaded.

I've tried every combination of USB settings on my motherboard, an ASUS H270F, with no luck.

Here's some output from dmesg after the mouse failing and re-plugging:

```
$ dmesg | grep -E 'usb(hid)?\s1-8'

[    2.340108] usb 1-8: new full-speed USB device number 5 using xhci_hcd
[   12.764194] usb 1-8: string descriptor 0 read error: -110
[   12.764210] usb 1-8: New USB device found, idVendor=1b1c, idProduct=1b3c
[   12.764211] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   17.884562] usb 1-8: can't set config #1, error -110
[   60.317121] usb 1-8: USB disconnect, device number 5
[   64.510030] usb 1-8: new full-speed USB device number 8 using xhci_hcd
[   64.660491] usb 1-8: New USB device found, idVendor=1b1c, idProduct=1b3c
[   64.660496] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   64.660500] usb 1-8: Product: Corsair Gaming HARPOON RGB Mouse
[   64.660504] usb 1-8: Manufacturer: Corsair
[   64.660508] usb 1-8: SerialNumber: 16025030AF1584A959495BAAF5001943
[   64.784586] usbhid 1-8:1.2: couldn't find an input interrupt endpoint
```

---

### Post by leo.lsdb on 2018-11-30
Same problem here.

And it seems upgrading my kernel solved the problem.
I was on Ubuntu 18.04 with kernel 4.15. So i upgraded for 18.10 with kernel 4.18. 
I will see if this is a steady solution.

---

### Post by leo.lsdb on 2018-12-31
Nope. Same problem, but it seems to happen a little bit less than with old kernel...

---

