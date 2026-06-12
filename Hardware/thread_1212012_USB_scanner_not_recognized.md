---
title: "USB scanner not recognized"
date: 2009-07-13
forum: Hardware
---

### Post by J.K.Makowka on 2009-07-13
I would like to support a central scanner on my Ubuntu 8.04 server (ebox) (via an automated script and scanbuttond), but the usb scanner does not show up under /dev/usb (in fact the usb directory does not exist) nor can it be found with sane-find-scanner.

Any idea what could be causing this?

The scanner (canon N670U) itself works fine on a Ubuntu 9.04 client, and I enabled usb support in the BIOS (it was not enabled during installation of the system though).

lspci -v

Shows the two USB 1.1 controllers

And
-------
lsmod | grep usb
usbcore               146284  1 uhci_hcd
-------
Gives this result.

I am a bit at a loss since I have never had problems with usb support before... so thanks for you help!

---

### Post by J.K.Makowka on 2009-08-16
bump.

Anyone got an idea?

---

