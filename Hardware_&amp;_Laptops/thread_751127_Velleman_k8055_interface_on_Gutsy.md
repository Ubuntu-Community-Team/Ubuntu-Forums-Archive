---
title: "Velleman k8055 interface on Gutsy"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by jheagney on 2008-04-10
Recently built the Velleman k8055 interface and tried to hook it up to my Gutsy laptop.
Had a considerable time getting the udev rules to set the appropriate file permissions, but eventually got the following to work:

[http://tentodata.net/?p=3]("http://tentodata.net/?p=3")

with ONE important change in the udev rules. 
Where it says:

SUBSYSTEMS!="usb"

I had to change this to include a wildcard thus:

SUBSYSTEMS!="usb*"

As it seems that the k8055 is no longer recognised as a simple usb device. Probably something like usb_device or usbfs, but I couldn't be bothered hunting it down. :)

Hope this helps some others.

Joal Heagney

---

