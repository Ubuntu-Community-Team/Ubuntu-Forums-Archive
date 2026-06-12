---
title: "Wacom Volito driving me nuts"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by damkor on 2007-03-26
I got this Wacom Volito USB tablet. I got it working in other linux distributions with no problems at all. In Edgy, something seems to be wrong with my tablet.

I already installed all wacom-related packages (xorg-input-wacom, wacom-tools, etc). When I plug it in, a new event node is made under /dev/input/event<something>, and /dev/input/wacom points to it.

Now comes the stupid part. Cat /dev/input/wacom shows nothing. wacdump shows nothing. xxd shows nothing, the mouse can't be moved with the pencil. Xorg.0.log reports no problem with the tablet. However, something is not working at all.

Things I already tried:
- Changing xorg.conf to point to the right device name (obviously).
- Removing the driver and reloading it again.
- Installing a new driver taken from linuxwacom.sf.net

I'm using an Intel Core 2 Duo.

---

