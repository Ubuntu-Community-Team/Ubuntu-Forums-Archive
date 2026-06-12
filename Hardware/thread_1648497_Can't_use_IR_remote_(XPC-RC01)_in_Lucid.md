---
title: "Can't use IR remote (XPC-RC01) in Lucid"
date: 2010-12-18
forum: Hardware
---

### Post by Fry-kun on 2010-12-18
Specifically, this is XBMC Live install which uses Lucid as base.
The same remote works perfectly in Fedora 14.

* F14 dmesg:
> [74981.504099] usb 3-1: new low speed USB device using uhci_hcd and address 3
[74981.722151] usb 3-1: New USB device found, idVendor=3351, idProduct=3715
[74981.722158] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[74981.766229] input: HID 3351:3715 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input11
[74981.767241] generic-usb 0003:3351:3715.0003: input,hiddev96,hidraw0: USB HID v10.01 Mouse [HID 3351:3715] on usb-0000:00:1d.1-1/input0
[74981.828285] input: HID 3351:3715 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input12
[74981.828498] generic-usb 0003:3351:3715.0004: input,hidraw1: USB HID v10.01 Keyboard [HID 3351:3715] on usb-0000:00:1d.1-1/input1


* Lucid (XBMC Live) dmesg:
> Dec 18 21:22:12 XBMCLive kernel: [  117.456079] usb 4-1: new low speed USB device using ohci_hcd and address 3
Dec 18 21:22:12 XBMCLive kernel: [  117.667828] usb 4-1: configuration #1 chosen from 1 choice
Dec 18 21:22:12 XBMCLive kernel: [  117.688657] input: HID 3351:3715 as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.0/input/input9
Dec 18 21:22:12 XBMCLive kernel: [  117.689203] generic-usb 0003:3351:3715.0005: input,hiddev96,hidraw0: USB HID v10.01 Mouse [HID 3351:3715] on usb-0000:00:06.0-1/input0
Dec 18 21:22:12 XBMCLive kernel: [  117.712859] input: HID 3351:3715 as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.1/input/input10
Dec 18 21:22:12 XBMCLive kernel: [  117.713283] generic-usb 0003:3351:3715.0006: input,hidraw1: USB HID v10.01 Keyboard [HID 3351:3715] on usb-0000:00:06.0-1/input1




Is ohci_hcd preventing it from working?

Thanks!


Edit: solved using libhid from [http://libhid.alioth.debian.org/](http://libhid.alioth.debian.org/) and lircd-xpc from [http://mathema.tician.de/dl/software/xpc-remote/lircd-xpc](http://mathema.tician.de/dl/software/xpc-remote/lircd-xpc)

---

### Post by daehenoc on 2011-01-03
Hi,

I've just started to try to set this up in Mythtv and was wondering if you could let me know exactly what you did to get it working?

I know that it's a HID device, and it's listed in /dev/input/by-id/usb-3353_3713-x, where 'x' is one of 'event-if01|event-mouse|mouse'.

I know that some button presses are passed through to the current application (i.e. 0-9 in a terminal) and other keypresses do other things (like 'Close' is Alt-F4), but I don't know how to set up the keypresses to do things that I want, like 'Stop' is Esc.  (Keypress information found here: [http://forum.team-mediaportal.com/general-support-51/xpc-rc01-remote-help-12670/](http://forum.team-mediaportal.com/general-support-51/xpc-rc01-remote-help-12670/))

Any information would be very helpful!

---

### Post by Fry-kun on 2011-01-03
The default behavior is to emulate keyboard/mouse, so it's a bit hard to reuse that. Instead, use libhid/lircd-xpc to have the OS see it as an actual IR remote

---

