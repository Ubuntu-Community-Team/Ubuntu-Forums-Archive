---
title: "how to enable DRI on 915GMA"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by mengqing on 2007-03-11
Hi, how do I enable DRI on 915GMA chipset

currently I only get 100fps in glxgears, and when i use glxinfo | grep direct, it shows that direct rednering is no

so how do I enable it? 

thx

---

### Post by mengqing on 2007-03-11
somebody help plz/

---

### Post by ramjet_1953 on 2007-03-12
You need to edit your /etc/X11/xorg.conf file.

Before doing so, BACK IT UP FIRST!

Right at the bottom of the file, there should be this:

Section "DRI"
	Mode	0666
EndSection

Regards,
Roger :cool:

---

