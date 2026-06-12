---
title: "USB hard drive no longer mounts"
date: 2005-04-06
forum: Hardware &amp; Laptops
---

### Post by mendicant on 2005-04-06
This was working last week and (with some problems) yesterday.  I updated the kernel a few times over this time period:
Sun Apr 3:
[UPGRADE] linux-image-2.6.10-5-686 2.6.10-32 -> 2.6.10-33
Tue Apr 5:
[UPGRADE] linux-image-2.6.10-5-686 2.6.10-33 -> 2.6.10-34

I get the following:
usb 2-2: new full speed USB device using uhci_hcd and address 64
usb 2-2: device not accepting address 64, error -71
usb 2-2: new full speed USB device using uhci_hcd and address 65
usb 2-2: device not accepting address 65, error -71
usb 2-2: new full speed USB device using uhci_hcd and address 66
usb 2-2: device descriptor read/64, error -71
usb 2-2: device descriptor read/64, error -71
usb 2-2: new full speed USB device using uhci_hcd and address 67
usb 2-2: device descriptor read/64, error -71
usb 2-2: device descriptor read/64, error -71

Looking on google shows the suggestion that I change usbcore parameters.  I did that (in /etc/modules) and rebooted, confirmed that the changes seem to have been made:
% cat /sys/module/usbcore/parameters/*
N
Y
N
Y

old_scheme_first is set to Y (the second entry above).  This doesn't fix my problem.  I also got error -32 when I connected it to an external hub.  Currently, I'm trying it without the hub.  I also got some of these problems yesterday, and multiple retries of disconnecting and reconnecting got it working.  That doesn't seem to work today, though (as you can see by the large numbered addresses above).

Any ideas?

Thanks.

---

### Post by mendicant on 2005-04-07
Ah.  Hardware failure, it seems.  A different enclosure works fine.

---

