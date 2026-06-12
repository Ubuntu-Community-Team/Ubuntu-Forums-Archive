---
title: "how do I tell USB to run a program?"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by XoRDy on 2006-10-26
Hi,

I've created the file :/etc/udev/rules.d/mis_removibles.rules
with this into it:

BUS="usb", SYSFS{product}="uPD720133", KERNEL="sd?1", NAME="%k", SYMLINK="disco_usb", RUN+="/usr/bin/montadisco"

it names the devices as disco_usb, but it don't run the "montadisco" script...
The script is 755, so it can be executable by anyone.

even if I put *echo "hello" > /text.log* it don't do anything

What I am doing wrong?

thank you

---

