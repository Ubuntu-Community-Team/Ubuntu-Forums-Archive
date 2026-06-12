---
title: "Usb"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by bkeithly on 2007-01-25
USB not working...

I have an HP dv6040

running edgy 6.10

Having to pass kernel options:  noapic and nolapic

If I don't pass those options I don't get wifi and nvidia drivers to work.

Now I have installed edgy 3 times and I used USD to get NDISwrapper and other bits of software on the machine.  Yet now USB has ceased to work....

Any trouble shooting suggestions?

---

### Post by K.Mandla on 2007-01-26
Are the USB ports completely unworking, or is it just that drives don't automount? Check your hardware configuration with *lspci* and *lshw* -- I believe one of those should show if your USB ports are at least detected.

---

