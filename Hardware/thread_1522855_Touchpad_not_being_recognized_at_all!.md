---
title: "Touchpad not being recognized at all!"
date: 2010-07-02
forum: Hardware
---

### Post by inno89 on 2010-07-02
Hi. I installed Ubuntu and the touchpad does not work at all. I even tried it with Fedora, and even it doesn't recognize the touchpad. I followed this guide: [http://www.debuntu.org/2006/06/18/67-how-to-setting-up-touchpad-on-a-laptop-a-complete-guide/2/](http://www.debuntu.org/2006/06/18/67-how-to-setting-up-touchpad-on-a-laptop-a-complete-guide/2/) and copied other variations of the xorg.conf file into my directory but nothing I have tried so far doesn't work. The main problem is that that both Ubuntu and Fedora ** don't even recognize the touchpad at all** when I did " cat /proc/bus/input/devices". It shows the keyboard, the power button, even the lid (since when I close it, it sleeps), but not the touchpad. This is a Sony Vaio F12. I tried to install Ubuntu in the past but I ran into problems there, and now I'm getting this on my new computer :-? . This is the x86_64 10.04 version, installed with Wubi.

---

### Post by inno89 on 2010-07-03
Bump :-/

---

### Post by Pim. on 2010-07-03
Have you tried to edit /etc/default/grub and add 'i8042.nopnp' to the line GRUB_CMDLINE_LINUX=""

?

---

### Post by inno89 on 2010-07-03
That didn't do anything :(

---

### Post by Pim. on 2010-07-04
ah sorry, you have to run update-grub and reboot ;)

---

