---
title: "hoary's kernel doesn't support pci=nopci option... so : no sound"
date: 2004-11-07
forum: Hardware &amp; Laptops
---

### Post by kil on 2004-11-07
I install hoary because I must use latest version of some software like Gimp (for exif support)

All works find like warty but no sound !

in warty, like I found in this forum, i put pci=noacpi option in kernel boot and it's OK. but in hoary, the pci=noacpi is not supported by kernel, so I have no sound.

I doesn't want to rebuld kernel because I used nvidia drivers and atmel drivers for my wireless card.. So what can I do ?

---

### Post by ulrich on 2004-11-08
then what about **acpi=off**?

---

### Post by kil on 2004-11-08
[QUOTE=ulrich]then what about **acpi=off**?[/QUOTE]

Ubuntu doesn't start with acpi=off option :-(

the message is :

Uncompressing Linux... OK, booting the kernel
PCI: Adress space collision on region 7 of bridge 0000:00:1f.0 [800:87F]
PCI: Cannot allocate resource region 4 of device 0000:00:1d.2
Starting Ubuntu...

and system hang :-(

---

