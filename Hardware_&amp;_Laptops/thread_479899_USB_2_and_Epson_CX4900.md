---
title: "USB 2 and Epson CX4900"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by gator on 2007-06-20
Having just bought an Epson CX4900 printer/scanner i thought i would have no probs with Feisty/Gutsy - however plugging it in gets the following dmesg
[  161.960000] usb 4-1: new high speed USB device using ehci_hcd and address 3
[  162.072000] usb 4-1: device descriptor read/64, error -71
[  162.288000] usb 4-1: device descriptor read/64, error -71
[  162.504000] usb 4-1: new high speed USB device using ehci_hcd and address 4
[  162.616000] usb 4-1: device descriptor read/64, error -71
[  162.832000] usb 4-1: device descriptor read/64, error -71
[  163.048000] usb 4-1: new high speed USB device using ehci_hcd and address 5
[  163.456000] usb 4-1: device not accepting address 5, error -71
[  163.568000] usb 4-1: new high speed USB device using ehci_hcd and address 6
[  163.976000] usb 4-1: device not accepting address 6, error -71

Other people seem to have the same problem with other USB devices....after some searching i discovered that removing the USB 2 module that the device can be discovered ( @ USB 1.1 speed)

sudo modprobe -r ehci_hcd

Any fixes for this prob? Both Feisty and Gutsy kernel same results.
Next the scanner did not work....again after some searching i found this (thanks gonk)
[http://ubuntuforums.org/showthread.php?t=184052](http://ubuntuforums.org/showthread.php?t=184052)
i simply copied the instuctions replacing the product id with the CX4900 id:-  082b
Printer and scanner now work but how do we fix the USB prob and also adding the printer/scanner to the config files for future releases?

---

### Post by gator on 2007-12-09
Problem fixed with a new usb2 cable

---

