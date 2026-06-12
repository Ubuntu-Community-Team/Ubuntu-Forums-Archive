---
title: "Boot from eSata on HP EliteBook 8440p"
date: 2011-01-05
forum: Hardware
---

### Post by cyberiad on 2011-01-05
Hi all,

I've successfully installed Ubuntu on an external eSata HDD, but now I'm having problems to boot from it in the HP 8440p.

Apparently the BIOS does not include the eSata drive on the boot device order list, for some reason. Searching about it seems that it's been a major running issue for some time.

My question is: will it work if I install GRUB to the MBR of the internal HDD? Will it detect the eSata drive?

Also, I originally installed the bootloader to the eSata drive itself to have both drives completely independent. Will this cause problems with the new bootloader? Or is it best just to reinstall Ubuntu and set the bootloader to the internal HDD?

Thanks for everything.

---

### Post by psusi on 2011-01-05
It will probably work, but you won't be able to boot without the esata drive connected unless you put a /boot partition on the internal drive.

---

