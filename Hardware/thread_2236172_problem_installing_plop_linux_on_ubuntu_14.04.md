---
title: "problem installing plop linux on ubuntu 14.04"
date: 2014-07-25
forum: Hardware
---

### Post by alex191 on 2014-07-25
Im using this guide [http://makegadgetswork.blogspot.com/2012/02/how-to-boot-from-usb-when-bios-does-not.html](http://makegadgetswork.blogspot.com/2012/02/how-to-boot-from-usb-when-bios-does-not.html) to install plop on my sony vaio pc.  When I enter  -PCG-V505BX-UC:~$ gksu nautilus  /boot  i get (nautilus:3112): GLib-GObject-WARNING **: invalid cast from 'GtkMessageDialog' to 'NautilusWindow' ** ERROR:nautilus-window.c:2116:nautilus_window_get_slots: assertion failed: (NAUTILUS_IS_WINDOW (window))

---

### Post by bapoumba on 2014-07-25
I used that : [http://www.plop.at/en/bootmanager/mbrinstall.html](http://www.plop.at/en/bootmanager/mbrinstall.html)
(Install on CD though).

---

### Post by sudodus on 2014-07-25
I can also recommend Plop directly from the source [www.plop.at]("http://www.plop.at") including the instructions how to install it.

Have a look at chainloading as an alternative (as long as you can boot into Ubuntu in an internal drive)

[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

---

