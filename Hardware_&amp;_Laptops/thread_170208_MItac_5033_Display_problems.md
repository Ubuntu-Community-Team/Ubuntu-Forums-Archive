---
title: "MItac 5033 Display problems"
date: 2006-05-04
forum: Hardware &amp; Laptops
---

### Post by Avionix on 2006-05-04
Hi, I have installed 5.10 on an old MITAC 5033, it now dual boots with Windoze 98, in windows the display is fine, high colour 16 bit, resolution 800x600, all good.
When I boot into ubuntu I only get my half of my login screen displayed on the right Hand side of the screen, I've have changed resolutions in the xorg.conf file to no avail, I am now informed it is most likely a driver problem. The video hardware is Trident 9685/9680 etc with 2mb memory, does anyone know where I can get drivers for and how I would install them, I'm pretty new to all this so please be gentle.

Thanks in advance

---

### Post by oli888 on 2006-05-21
[QUOTE=Avionix]Hi, I have installed 5.10 on an old MITAC 5033, it now dual boots with Windoze 98, in windows the display is fine, high colour 16 bit, resolution 800x600, all good.
When I boot into ubuntu I only get my half of my login screen displayed on the right Hand side of the screen, I've have changed resolutions in the xorg.conf file to no avail, I am now informed it is most likely a driver problem. The video hardware is Trident 9685/9680 etc with 2mb memory, does anyone know where I can get drivers for and how I would install them, I'm pretty new to all this so please be gentle.

Thanks in advance[/QUOTE]

Hopefully, the Dapper Drake (released on June 1 2006) will have support as I have the same problem. I haven't tried it but when booting, try:

boot:vga=normal

Please reply to see if this works

Thanks,

Oli

---

