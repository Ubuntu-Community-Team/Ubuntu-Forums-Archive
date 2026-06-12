---
title: "reset full speed USB device permanently, why?"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by HilliBilly on 2007-02-01
hi, 

need some help. the usb device of my laptop (edgy, gnome) is being reset all the time. why? second question: it works, so should i care about this issue at all?

connecting the cd rom drive to the usb port

dmesg | grep usb

[17219505.116000] usb 1-1: new full speed USB device using uhci_hcd and address 11
[17219505.288000] usb 1-1: configuration #1 chosen from 1 choice
[17219505.296000] usb-storage: device found at 11
[17219505.296000] usb-storage: waiting for device to settle before scanning
[17219510.296000] usb-storage: device scan complete
[17219510.592000] usb 1-1: reset full speed USB device using uhci_hcd and address 11
[17219510.860000] usb 1-1: reset full speed USB device using uhci_hcd and address 11
[17219511.128000] usb 1-1: reset full speed USB device using uhci_hcd and address 11
[17219511.396000] usb 1-1: reset full speed USB device using uhci_hcd and address 11
[17219511.756000] usb 1-1: reset full speed USB device using uhci_hcd and address 11
[17219512.016000] usb 1-1: reset full speed USB device using uhci_hcd and address 11
[17219512.276000] usb 1-1: reset full speed USB device using uhci_hcd and address 11

this "reset full speed USB ..." continues for ever. it doesnt't stop

unplugging the usb cable of the cd drive

[17219585.600000] usb 1-1: reset full speed USB device using uhci_hcd and address 11
[17219585.744000] usb 1-1: failed to restore interface 0 altsetting 0 (error=-71)
[17219585.744000] usb 1-1: USB disconnect, address 11

connecting a usb memory stick to the usb port

[17219737.456000] usb 1-1: new full speed USB device using uhci_hcd and address 12
[17219737.620000] usb 1-1: configuration #1 chosen from 1 choice
[17219737.624000] usb-storage: device found at 12
[17219737.624000] usb-storage: waiting for device to settle before scanning
[17219742.624000] usb-storage: device scan complete

and that's it. no "reset full ...".

i also tried to power the cd drive with an external power supply but this did not keep the system off from permanently resetting.

i also checked it with another cd drive (same model), again this resetting appears.

what's wrong?

uname -r
2.6.17-10-386

hald --version
HAL package version: 0.5.7.1

and btw: what exactly says this long number [172...] in front of each line?

---

