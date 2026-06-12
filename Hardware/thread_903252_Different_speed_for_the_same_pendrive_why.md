---
title: "Different speed for the same pendrive: why?"
date: 2008-08-28
forum: Hardware
---

### Post by egalua on 2008-08-28
Hi all,

I have a small problem with a 2.0 usb pendrive.
My settings are: 2 desktops with ubuntu 8.04 and an eeepc 900 with the default xandros.

On the eeepc, the pendrive correcly works at 2.0 fullspeed.

On the desktops, the pendrive seems to be correctly recognized as 2.0, 
as reported by dmesg:

[614.617] usb 4-3: new high speed USB device using ehci_hcd and address 4

Moreover, the device is shown under ehci in usbview.

Regardless of this, on both desktops the pendrive is very slow, with the same speed rate as if it were a low speed usb 1.1.

I have to add that I have other usb devices which work at full speed on both desktop: the problem is only with this pendrive.

Does anybody have any hint?

Thanks a lot

Fabio

---

### Post by chris_nava on 2008-08-28
What other devices are plugged in?
Having any 1.x device plugged into a bus slows all the 2.0 devices on the same bus.

---

### Post by egalua on 2008-08-29
> **chris_nava said:**
> What other devices are plugged in?
Having any 1.x device plugged into a bus slows all the 2.0 devices on the same bus.

Scanner and printer, both 2.0 and both turned off (the scanner is even unplugged from the power line). 
In any case, with the same configuration my 2.0 usb disk reaches hispeed.

Fabio

---

