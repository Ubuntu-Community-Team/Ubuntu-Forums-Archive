---
title: "Usb not showing up in /dev"
date: 2013-01-30
forum: Hardware
---

### Post by da_steve123 on 2013-01-30
Hi,

I was using a 2GB usb, i mounted it manually in a tty. I think i either just pulled it out while it was busy or shutdown when it was. Anyway, the problem is it wont mount ... on anything (i even tried windows)

There is no /dev entry when it is plugged in. Here is the dmesg output:

usb 2-1.1: new full-speed USB device number 21 using ehci_hcd
usb 2-1.1: device descriptor read/64, error -32
usb 2-1.1: device descriptor read/64, error -32
usb 2-1.1: new full-speed USB device number 22 using ehci_hcd
usb 2-1.1: device descriptor read/64, error -32
usb 2-1.1: device descriptor read/64, error -32
usb 2-1.1: new full-speed USB device number 23 using ehci_hcd
usb 2-1.1: device not accepting address 23, error -32
usb 2-1.1: new full-speed USB device number 24 using ehci_hcd
usb 2-1.1: device not accepting address 24, error -32
hub 2-1:1.0: unable to enumerate USB device on port 1

I cant find what 'error -32' is.

Any ideas?

Thanks
Stephen

---

### Post by da_steve123 on 2013-01-30
Ok, so -32 means broken pipe ...

[http://www.barricane.com/c-error-codes-include-errno](http://www.barricane.com/c-error-codes-include-errno)

---

