---
title: "[SOLVED] Wacom Graphire: doesn't show up in gimp"
date: 2006-11-01
forum: Hardware &amp; Laptops
---

### Post by Matyy on 2006-11-01
Hi,

I already found some topics about the Wacom tablets, but nothing helped me yet. 

I have got a Wacom Graphire tablet, I think Graphire 3. It perfectly works as a mouse. But it doesn't show up in gimp's extended input thing. So no pressure there :/

I installed wacom-tools, so I can use wacdump. If I start it in Gnome (sudo wacdump /dev/input/wacom) nothing happens. I can move my pen wherever I want. It still works, but no output from wacdump.
But when I change to a terminal (ctrl+alt+f1) wacdump works. Same command (sudo wacdump /dev/input/wacom) and while moving my pen around, I get all the output I want. Even pressure is working.

So the error must be something with X.

Is this perhaps because I use XGL? Perhaps I should try disabling it.

Any other ideas?

Xorg log: [http://www.ubuntuusers.de/paste/4822/](http://www.ubuntuusers.de/paste/4822/)
xorg.conf: [http://www.ubuntuusers.de/paste/4823/](http://www.ubuntuusers.de/paste/4823/)

---

### Post by Matyy on 2006-11-02
It is XGL... without it it works.

---

