---
title: "To block the ports usb"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by mogotocoro on 2007-01-07
hello friends, usb through a commando exists the possibility of being able to block the ports usb. In my company this prohibited to use the flash memory and not like blocking it so that the current user us can use, but only for the user root

---

### Post by RandomJoe on 2007-01-07
You could prevent the kernel from loading the kernel modules for USB, which would completely shut down the USB subsystem.  (Have to use PS/2 keyboard and mouse.)  Or if USB storage devices are the only issue, then just prevent the loading of the usb-storage module.

I think it may work to place usb-storage into the /etc/modprobe.d/blacklist file to keep it from loading.  Not sure how you would then load it just for root, although manually calling 'insmod usb-storage' may be sufficient to override the blacklist...  (Just be sure to unload it after you're through! ;) )

---

