---
title: "problems with ati card"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by Cybercool on 2005-04-22
Hello,

I have installed Ubuntu 5.xx on my fujitsu-siemens laptop.
Everything is working well, exept one thing.
My ATI radeon 9600/9700 graphic card.
I have installed the fglrx (xorg) packages, and changed the xorg.conf in X11 directory from ati to fglrx. But when i run glxgears, I only get 1400fps.

Now i know that's to low, because on my normal desktop machine with ubuntu 4.0 and a radeon 9000 (Xfree) i get 6500 fps.

Does anyone know what this could be?

I can't even set a normal screensaver like fuzy (very nice).
Please help??

---

### Post by jdodson on 2005-04-22
[QUOTE=Cybercool]Hello,

I have installed Ubuntu 5.xx on my fujitsu-siemens laptop.
Everything is working well, exept one thing.
My ATI radeon 9600/9700 graphic card.
I have installed the fglrx (xorg) packages, and changed the xorg.conf in X11 directory from ati to fglrx. But when i run glxgears, I only get 1400fps.

Now i know that's to low, because on my normal desktop machine with ubuntu 4.0 and a radeon 9000 (Xfree) i get 6500 fps.

Does anyone know what this could be?

I can't even set a normal screensaver like fuzy (very nice).
Please help??[/QUOTE]

did you do all the steps from this guide: [http://ubuntuforums.org/showthread.php?t=3567](http://ubuntuforums.org/showthread.php?t=3567)

it might have some optimizations you missed.

---

### Post by Cybercool on 2005-04-22
I installed the packages fglrx, set Option "UseInternalAGPGART" "no".

And i still get with fglrxinfo :mesa, and not ati!!

does anyone maybe know what i'm doing wrong.
I'm using xorg, and not xfree!!

I installed ubuntu 5.xx with the 2.6.10-5 kernel, fglrx is compiled in this kernel, or not??

If i do modprobe fglrx
it says:
FATAL: Module fglrx not found.

---

