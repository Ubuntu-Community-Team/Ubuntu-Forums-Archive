---
title: "Kobo Ereader doesn't mount 14.4 and 14.10"
date: 2014-11-14
forum: Hardware
---

### Post by 7-webmaster on 2014-11-14
I used to be able to mount by Kobo Ereader but since going to 14.4 and now to 14.10 it doesn't mount.  Nothing shows up in lsusb.  The ereader claims it is connected and charging.  I have tried multiple USB ports on my computer, and checked by plugging in a USB thumb-drive.  I cannot see any advice on resolving this issue, and the only thread that mentions this issue, which was opened 2 years ago, was closed without any explanation.

---

### Post by 7-webmaster on 2014-11-14
dmesg output:
```

[ 1327.411729] usb 8-2: new full-speed USB device number 17 using xhci_hcd
[ 1327.531756] usb 8-2: device descriptor read/64, error -71
[ 1327.635679] xhci_hcd 0000:00:10.1: Setup ERROR: setup context command for slot 2.
[ 1327.635697] usb 8-2: hub failed to enable device, error -22
[ 1327.747631] usb 8-2: new full-speed USB device number 18 using xhci_hcd
[ 1327.867532] usb 8-2: device descriptor read/64, error -71
[ 1327.971462] xhci_hcd 0000:00:10.1: Setup ERROR: setup context command for slot 2.
[ 1327.971480] usb 8-2: hub failed to enable device, error -22
[ 1328.083503] usb 8-2: new full-speed USB device number 19 using xhci_hcd
[ 1328.086433] usb 8-2: Device not responding to setup address.
[ 1328.290379] usb 8-2: Device not responding to setup address.
[ 1328.491227] usb 8-2: device not accepting address 19, error -71
[ 1328.603358] usb 8-2: new full-speed USB device number 20 using xhci_hcd
[ 1328.606308] usb 8-2: Device not responding to setup address.
[ 1328.810247] usb 8-2: Device not responding to setup address.
[ 1329.011053] usb 8-2: device not accepting address 20, error -71
[ 1329.011230] usb usb8-port2: unable to enumerate USB device
```

---

### Post by 7-webmaster on 2014-11-20
FYI the problem was that the mini-USB socket on the Kobo E-reader had become damaged, probably through inadvertently trying to plug the cable in upside down.  In other words Murphy's Law in it original form.  I understand that the industry group is working on a new symmetrical design for this interface.

---

### Post by isetome on 2015-01-02
Crap. I have the same problem, and just now when i tried to insert my usb cable (the right way) the connector said 'plok' and came loose. Still works but now i have to prop up the cable... Time to find a tut on changing the connector because i lurv my ereader.

---

