---
title: "USB 3.0 frontpanel not working anymore"
date: 2015-06-06
forum: Hardware
---

### Post by chris137 on 2015-06-06
Hi,

I'm using Ubuntu 14.04.2 LTS (GNU/Linux 3.13.0-53-generic x86_64).
About a month ago I got a USB 3.0 frontpanel for my PC.
It's attatched to a USB 3.0 PCIe-card which I bought at the same time.
The card works properly but the frontpanel suddenly stopped working.
It got 3 USB 3.0-ports and one charger-port.
I get power on all four but can't use the devices.
Here is what syslog gives me when I plug it in:
```
Jun  6 15:21:46 knix kernel: [ 2370.481006] usb 3-2: new full-speed USB device number 14 using xhci_hcd
Jun  6 15:21:46 knix kernel: [ 2370.481825] usb 3-2: Device not responding to set address.
Jun  6 15:21:47 knix kernel: [ 2370.685911] usb 3-2: Device not responding to set address.
Jun  6 15:21:47 knix kernel: [ 2370.889194] usb 3-2: device not accepting address 14, error -71
Jun  6 15:21:47 knix kernel: [ 2371.001293] usb 3-2: new full-speed USB device number 15 using xhci_hcd
Jun  6 15:21:47 knix kernel: [ 2371.002152] usb 3-2: Device not responding to set address.
Jun  6 15:21:47 knix kernel: [ 2371.206049] usb 3-2: Device not responding to set address.
Jun  6 15:21:47 knix kernel: [ 2371.409449] usb 3-2: device not accepting address 15, error -71
Jun  6 15:21:47 knix kernel: [ 2371.521526] usb 3-2: new full-speed USB device number 16 using xhci_hcd
Jun  6 15:21:47 knix kernel: [ 2371.522229] usb 3-2: Device not responding to set address.
Jun  6 15:21:48 knix kernel: [ 2371.726360] usb 3-2: Device not responding to set address.
Jun  6 15:21:48 knix kernel: [ 2371.929792] usb 3-2: device not accepting address 16, error -71
Jun  6 15:21:48 knix kernel: [ 2372.041830] usb 3-2: new full-speed USB device number 17 using xhci_hcd
Jun  6 15:21:48 knix kernel: [ 2372.042493] usb 3-2: Device not responding to set address.
Jun  6 15:21:48 knix kernel: [ 2372.246544] usb 3-2: Device not responding to set address.
Jun  6 15:21:48 knix kernel: [ 2372.450050] usb 3-2: device not accepting address 17, error -71
Jun  6 15:21:48 knix kernel: [ 2372.450144] hub 3-0:1.0: unable to enumerate USB device on port 2
```
I checked my dpkg.log and according to this I did not install any updates between May 27 (last update) and May 30 (first occurence of the error).

Is there a different place where other update-logs are stored?
Suddenly getting an error without a hardware change and without a software change are pretty rare I guess.
I read it could be a hardware-failure but the device is only a month old.
Possible but not my first guess.

Any further ideas?

---

### Post by weatherman2 on 2015-06-06
Try booting a live USB Ubuntu and see if you have the same problem.  If you don't have the problem with a live USB, then you know it's a software issue.

Obviously, check the cable connections inside, just to make sure they are tight, between the card and the front panel.

---

### Post by chris137 on 2015-06-07
I hadn't had time to try that yet but today it suddenly worked again.
Since the USB 3.0-ports are easier to reach I just put a SD-card reader in and it worked.
I checked the cables and everything but it wouldn't work yesterday.
Also rebooted a few times.

Does this rule out either hard- or software issue?

---

### Post by weatherman2 on 2015-06-07
It probably doesn't rule anything out.  If it happens again, you can think about it then; if it never happens again, you are done worrying about it!

---

### Post by chris137 on 2015-06-07
I set it to solved for the moment.
If it happens again I'll try booting via Live-CD.

Thanks so far!

---

