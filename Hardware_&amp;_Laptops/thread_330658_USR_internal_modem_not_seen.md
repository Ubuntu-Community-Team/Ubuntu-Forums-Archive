---
title: "USR internal modem not seen"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by ktindle on 2007-01-03
Hello all- it seems my US Robotics controller based modem can't be seen in Edgy??

Note well- this is *NOT* a winmodem!  It is an internal PCI bus modem with a controller.

The kernel spots the serial UART as /dev/ttyS1, but pppconfig thinks there is nothing there that "seems to be a modem."

If this is not Hayes compatible, is there a kernel module to load that will wake this guy up?  I've never had problems with real modems under Linux before- I'm stumped.

---

