---
title: "Keyboard Problem kernel 686"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by ketekojo on 2006-06-01
I have a problem. I installed ubuntu 6.06 RC and the LTS version and i have the same problem. When i change the i386 kernel and install the i686 kernel the keyboard does not work (i have a Logitech Media Keyboard connected to the PS/2 connector). So that functions I have to connect other keyboard in the front usb connector of my computer. ¿What is the problem?

---

### Post by johnc4510 on 2006-06-01
When you changed to the 686 kernel, did you also install:
linux-image-686
Linux-restricted-modules-686

---

### Post by ketekojo on 2006-06-02
I run Synaptycs and the restricted-module-686 is dont load, y try to load and reboot the system and the result is the same... the keyboard is missing.... :(.

P.D. In the 5.10 Breezy, then i boot in the linux-686 the keyboard it works perfectly.

---

### Post by ketekojo on 2006-06-03
Well, i downloading and installing the DVD version of the 6.06 Dapper Drake in Text Mode. This install the i686 kernel directly and the result is the same: the keyboard connected to the PS/2 connector it does not work.

I NEED HELP...

---

### Post by padre999 on 2006-06-04
Found some other posts:

[http://ubuntuforums.org/showthread.php?t=186689](http://ubuntuforums.org/showthread.php?t=186689)
[http://ubuntuforums.org/showthread.php?t=187896](http://ubuntuforums.org/showthread.php?t=187896)

Looks like it could be the Bios settings...

---

### Post by ketekojo on 2006-06-04
[QUOTE=padre999]Found some other posts:

[http://ubuntuforums.org/showthread.php?t=186689](http://ubuntuforums.org/showthread.php?t=186689)
[http://ubuntuforums.org/showthread.php?t=187896](http://ubuntuforums.org/showthread.php?t=187896)

Looks like it could be the Bios settings...[/QUOTE]

Thanks.... i enter in BIOS and change de USB keyboard and mouse support to OS and the linux-kernel 686 it works perfectly. I try too to disable Hyperthreading and the keyboard works perfectly, but i missed the hyperthreading support... thanks... thanks... thanks....

---

