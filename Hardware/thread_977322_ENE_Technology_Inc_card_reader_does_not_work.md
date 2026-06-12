---
title: "ENE Technology Inc card reader does not work"
date: 2008-11-10
forum: Hardware
---

### Post by lakersforce on 2008-11-10
I scanned over this at launchpad and someone gave the following answer:

> 
This is a generic problem. The cardreader is on an internal USB bus, so it is present on boot. Ubuntu Hardy does not detect USB storage devices if they are present on boot.

Please fix it by building the kernel with CONFIG_LIBUSUAL=n. This is the solution adopted in Fedora Core 7.


I have no idea where to find CONFIG_LIBUSUAL=n.

---

### Post by lakersforce on 2008-11-11
Come on, someone has to know this. How do I make usb that is present at boot also present in Ubuntu? (I have tried a more recent kernel, but no go).

---

### Post by lakersforce on 2008-11-11
My friend has suggested that I apply it to the command-line. I'll have to look into it later.

---

