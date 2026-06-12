---
title: "Question about Live CD"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by bardu on 2009-01-18
I'm wondering whether a download able Live CD of a specific Ubuntu version is kept up-to-date. Or is the Live CD available in November the same in, lets say, March?

---

### Post by ibutho on 2009-01-18
Usually the cd images of a particular release remain the same regardless of when you download it. There is an exception with LTS releases because the installation images are sometimes updated and the version number bumped e.g. Ubuntu 8.04 was updated to Ubuntu 8.04.1.

---

### Post by bardu on 2009-01-18
Thanks. And I suppose there is no way to install new drivers while running Ubuntu from Live CD!?

The reason for my question is that I can't run Ubuntu 8.10 from Live CD on a brand new Toshiba Satellite A350 with a ATI Mobility Radeon HD 3650 graphics card. After booting the screen turns blank and that's it. The same happens when I add "xdriver=vesa" to the boot options. I suppose the problem is the driver for the graphics card, and would like to install the latest Radeon drivers from [www.freedesktop.org](www.freedesktop.org).

---

### Post by ibutho on 2009-01-18
Theoretically you could update or install anything whilst the live cd is running, but this may affect performance of the live disc and you'll lose your changes after a reboot. You could try creating a live usb disk instead of using a live cd. I've done this with Fedora and you can even store things on the usb disk, install/remove packages and generally use it like an OS installed on your HD.

---

### Post by bardu on 2009-01-18
Thanks for your feedback, I'll give it a try.

---

