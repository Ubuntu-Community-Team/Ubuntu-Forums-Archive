---
title: "direct rendering"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by Alessio on 2005-05-02
alessio@Ubuntu:~ $ glxinfo | grep rendering
direct rendering: No

How can i set it? on yes?
My card
Trident Blade 3D PCI\AGP
Thanks

---

### Post by gasolio on 2005-05-02
Molto probabilmente i driver della tua scheda video non sono configurati bene o non sono neanche istallati. Ho trovato sto link dacci un occhiata.
[http://display-and-video.free-driver-download.com/Trident/682/Trident-Blade-3D-Driver-For-Linux.html](http://display-and-video.free-driver-download.com/Trident/682/Trident-Blade-3D-Driver-For-Linux.html)

For enable direct rendering you must install video driver for you card or configure it.

---

### Post by alastair on 2005-05-02
What is a "Trident Blade 3D PCI\AGP"?

Post :

/etc/X11/xorg.conf
/var/log/Xorg.0.log

---

