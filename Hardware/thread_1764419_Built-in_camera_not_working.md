---
title: "Built-in camera not working"
date: 2011-05-21
forum: Hardware
---

### Post by Jobbo256 on 2011-05-21
I have an Acer Aspire One, I recently put ubuntu on it and im a mega noob. Yeah... >_>

Anyways, I know you need the drivers and everything for it, but I don't know how or where to get them.

Heres lsusb results:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Please I NEED HELP

---

### Post by noidian on 2011-05-21
You might want to try this page:
[http://www.ubuntu.com/certification/catalog/component/usb:62C0:0C45-VIDEO](http://www.ubuntu.com/certification/catalog/component/usb:62C0:0C45-VIDEO)

I have had driver issues as well but check the ubuntu version you have and see if it matches.

---

### Post by Jobbo256 on 2011-05-21
> **noidian said:**
> You might want to try this page:
[http://www.ubuntu.com/certification/catalog/component/usb:62C0:0C45-VIDEO](http://www.ubuntu.com/certification/catalog/component/usb:62C0:0C45-VIDEO)

I have had driver issues as well but check the ubuntu version you have and see if it matches.

I just updated to 11.4 D:

---

### Post by noidian on 2011-05-21
There is a relevant discussion in the below forum:
[https://lists.berlios.de/pipermail/linux-uvc-devel/2009-June/004880.html](https://lists.berlios.de/pipermail/linux-uvc-devel/2009-June/004880.html)

You have to probably compile the kernel mentioned for ubuntu 11.4

Check this as well:
[http://bbs.archlinux.org/viewtopic.php?id=70685](http://bbs.archlinux.org/viewtopic.php?id=70685)

and the solution by "slimmer".

---

