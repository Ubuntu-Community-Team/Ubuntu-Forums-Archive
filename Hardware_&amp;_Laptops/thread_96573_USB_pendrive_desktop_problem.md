---
title: "USB pendrive desktop problem"
date: 2005-11-29
forum: Hardware &amp; Laptops
---

### Post by skirkpatrick on 2005-11-29
I have Ubuntu (new install) on my work laptop and on my home desktop (upgrade from Hoary).  My USB pendrive works fine on the laptop but I get this problem on my desktop from dmesg:
> 
[4318929.872000] usb 5-8: new high speed USB device using ehci_hcd and address 9[4318929.934000] usb 5-8: device descriptor read/64, error -71
[4318930.097000] usb 5-8: device descriptor read/64, error -71
[4318930.260000] usb 5-8: new high speed USB device using ehci_hcd and address 10
[4318930.322000] usb 5-8: device descriptor read/64, error -71
[4318930.485000] usb 5-8: device descriptor read/64, error -71
[4318930.648000] usb 5-8: new high speed USB device using ehci_hcd and address 11
[4318931.050000] usb 5-8: device not accepting address 11, error -71
[4318931.112000] usb 5-8: new high speed USB device using ehci_hcd and address 12
[4318931.514000] usb 5-8: device not accepting address 12, error -71


Any thoughts?

---

### Post by richardhp on 2005-12-19
I have a similar problem - When I first installed Ubuntu the USB pendrive worked fine but when I came to use it again a while ago it just wouldn't work. It appears in the device manager so must be being detected by the computer, but i cannot find the drive itself or access any files.

---

