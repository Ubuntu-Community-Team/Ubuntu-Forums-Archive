---
title: "install drivers before or after?"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by A-Sylum on 2007-08-22
my radeon 9250 ati works fine on my computer until i get to the login screen it just shows black and i dont know if i install the drivers for it before or after i boot up with the card in the system? does anybody know when to install before or after? thanks !!!

---

### Post by tseliot on 2007-08-23
Boot in Recovery Mode (select it from the GRUB menu)

type:
```
dpkg-reconfigure xserver-xorg
```

select the "vesa" driver and press ENTER whenever you don't know the answer to a question.

then type:
```
reboot 
```

and boot as usual

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

---

