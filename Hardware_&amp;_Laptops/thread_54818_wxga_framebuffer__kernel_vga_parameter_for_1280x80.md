---
title: "wxga framebuffer / kernel vga parameter for 1280x800"
date: 2005-08-06
forum: Hardware &amp; Laptops
---

### Post by C38a7r1zvl on 2005-08-06
¡Hola!

I'm not quite sure about about my choice of the category to post in but well.. what do we pay the mods for ;)

Basically I'm just looking for a nice number to put in my list of kernel parameters so that I have nice looking terminals. Everytime I boot up Ubuntu I get sick of the way too large letters on my screen..

[vbetest](http://sourceforge.net/projects/lrmi/) gave me the following:
```
[snip]
[261] 1024x768 (256 color palette)
[278] 1024x768 (5:5:5)
[279] 1024x768 (5:6:5)
[280] 1024x768 (8:8:8)
[291] 1024x768 (8:8:8)
[263] 1280x1024 (256 color palette)
[281] 1280x1024 (5:5:5)
[282] 1280x1024 (5:6:5)
[283] 1280x1024 (8:8:8)
[292] 1280x1024 (8:8:8)
[snip]
```

so apparently there isn't a appropriate vesa mode available on my system. Is there any other way to get wxga resolution on bootup and the terminals with "standard" ubuntu stuff? Otherwise I would most certainly have to [follow guides like this](http://http://gentoo-wiki.com/HARDWARE_Sony_VGN-FS500#Console) and well.. that looks like a lot of work :D

Greetings from Cologne, Germany,
Niels.

---

### Post by funkyhat on 2007-02-09
I've got my console running at 1280x800 (ATi card), all I did was add radeonfb on a new line in /etc/modules
(I think this method will only work if you are using the open source radeon drivers, I heard radeonfb and the binary ATi drivers don't mix)

---

