---
title: "ups not detected"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by jureuninet on 2007-10-24
I can't make my ups working. I don't even know where to start. The kernel recognized a new usb hid device but didn't make any new node in /dev. To be honest I don't even know what would be the name in /dev. I don't know if I should recompile the kernel now and if that would help at all, because I think that before I can use nut to listen to the ups the kernel should make a new node somehwere in /dev so that nut can talk to this ups.

Here is the relevant part of var log messages:

usb 1-1: configuration #1 chosen from 1 choice
usbcore: registered new interface driver hiddev
hiddev96: USB HID v1.00 Device [TRIPP LITE TRIPP LITE OMNIVSINT800       ] on usb-0000:00:1d.0-1
usbcore: registered new interface driver usbhid
drivers/usb/input/hid-core.c: v2.6:USB HID core driver

---

