---
title: "USB port possibly damaged?"
date: 2013-12-29
forum: Hardware
---

### Post by radiobert on 2013-12-29
I am using kubuntu 12.04 on a laptop and recently probably due to static damage, all the usb ports stopped working (damage is only done on one port but all other ports ceased working).   This is what I found in the kernel log:

```

12/29/13 01:33:54 PM    tyf-Lenovo-G580    kernel    [   42.718293] usb 3-4: Device not responding to set address.
12/29/13 01:33:54 PM    tyf-Lenovo-G580    kernel    [   42.921828] usb 3-4: device not accepting address 23, error -71
12/29/13 01:33:54 PM    tyf-Lenovo-G580    kernel    [   43.033706] usb 3-4: new full-speed USB device number 24 using xhci_hcd
12/29/13 01:33:54 PM    tyf-Lenovo-G580    kernel    [   43.033989] usb 3-4: Device not responding to set address.
12/29/13 01:33:55 PM    tyf-Lenovo-G580    kernel    [   43.237686] usb 3-4: Device not responding to set address.
12/29/13 01:33:55 PM    tyf-Lenovo-G580    kernel    [   43.441158] usb 3-4: device not accepting address 24, error -71
12/29/13 01:33:55 PM    tyf-Lenovo-G580    kernel    [   43.553032] usb 3-4: new full-speed USB device number 25 using xhci_hcd
12/29/13 01:33:55 PM    tyf-Lenovo-G580    kernel    [   43.553318] usb 3-4: Device not responding to set address.
12/29/13 01:33:55 PM    tyf-Lenovo-G580    kernel    [   43.757006] usb 3-4: Device not responding to set address.
12/29/13 01:33:55 PM    tyf-Lenovo-G580    kernel    [   43.960523] usb 3-4: device not accepting address 25, error -71
12/29/13 01:33:55 PM    tyf-Lenovo-G580    kernel    [   43.960561] hub 3-0:1.0: unable to enumerate USB device on port 4
12/29/13 01:33:56 PM    tyf-Lenovo-G580    kernel    [   44.184358] usb 1-1.3: new low-speed USB device number 7 using ehci_hcd
12/29/13 01:33:56 PM    tyf-Lenovo-G580    kernel    [   44.256260] usb 1-1.3: device descriptor read/64, error -32
12/29/13 01:33:56 PM    tyf-Lenovo-G580    kernel    [   44.432032] usb 1-1.3: device descriptor read/64, error -32
12/29/13 01:33:56 PM    tyf-Lenovo-G580    kernel    [   44.607808] usb 1-1.3: new low-speed USB device number 8 using ehci_hcd
12/29/13 01:33:56 PM    tyf-Lenovo-G580    kernel    [   44.679710] usb 1-1.3: device descriptor read/64, error -32
12/29/13 01:33:56 PM    tyf-Lenovo-G580    kernel    [   44.855479] usb 1-1.3: device descriptor read/64, error -32
12/29/13 01:33:56 PM    tyf-Lenovo-G580    kernel    [   45.031258] usb 1-1.3: new low-speed USB device number 9 using ehci_hcd
12/29/13 01:33:57 PM    tyf-Lenovo-G580    kernel    [   45.438554] usb 1-1.3: device not accepting address 9, error -32
12/29/13 01:33:57 PM    tyf-Lenovo-G580    kernel    [   45.510633] usb 1-1.3: new low-speed USB device number 10 using ehci_hcd
12/29/13 01:33:57 PM    tyf-Lenovo-G580    kernel    [   45.917975] usb 1-1.3: device not accepting address 10, error -32
12/29/13 01:33:57 PM    tyf-Lenovo-G580    kernel    [   45.918134] hub 1-1:1.0: unable to enumerate USB device on port 3


```

     I didn't connect any usb device to the ports, but the internal webcam and the bluetooth module are internally connected to some USB ports on the motherboard.  Should I replace the motherboard? Any hints?

---

### Post by Bucky Ball on 2013-12-29
You're saying the webcam and bluetooth are now not working?

What you could do is plug a USB device in to each port in turn, checking the end of dmesg after each insertion to see if it is picked up. If you've killed one USB port, then I would go so far as to replace the motherboard. You could get a powered hub and plug it into a working port and have a heap of USB ports. ;)

---

### Post by radiobert on 2013-12-29
Sadly, all the USB ports are defective, the 5v supply is present but plugging whatever mouse or thumb drive doesn't work.... perhaps the USB controller is damaged....

---

### Post by tgalati4 on 2013-12-29
Try cleaning the motherboard.  Take the machine apart and blow out the dust.  Dust can enter through the USB ports can cause issues.  Reseat any cables.

---

