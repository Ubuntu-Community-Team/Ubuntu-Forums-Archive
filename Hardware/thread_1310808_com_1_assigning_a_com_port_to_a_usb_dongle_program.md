---
title: "com 1: assigning a com port to a usb dongle programmer fdti usb tools"
date: 2009-11-02
forum: Hardware
---

### Post by brettybaby on 2009-11-02
**com 1: assigning a com port to a usb dongle programmer fdti usb tools ? how?**

---

### Post by cszikszoy on 2010-02-08
it should show up as /dev/ttyUSB<N> when you plug it in.  It should show up as /dev/ttyUSB0 (mine does).

I also seem to remember having to remove brltty package to get usb serial to work.  You can do some googling to find out more.  Googling "ubuntu usb serial brltty" should give enough info.

---

