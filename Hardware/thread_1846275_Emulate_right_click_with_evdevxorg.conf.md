---
title: "Emulate right click with evdev/xorg.conf?"
date: 2011-09-18
forum: Hardware
---

### Post by abtekk on 2011-09-18
Is it possible to emulate right click by doing a long press on a touchscreen with either the evdev driver or xorg.conf?

All help appreciated :).

---

### Post by anikol on 2011-12-20
I am looking for a solution of the problem also. Hasn't anybody found the solution yet?

---

### Post by imayoda on 2011-12-20
> **anikol said:**
> I am looking for a solution of the problem also. Hasn't anybody found the solution yet?

simply launch in terminal

mousetweaks --ssc

here some info

[http://library.gnome.org/users/mousetweaks/stable/mouse-a11y-how-to-start-features.html.en](http://library.gnome.org/users/mousetweaks/stable/mouse-a11y-how-to-start-features.html.en)

---

### Post by anikol on 2011-12-20
Being a part of Gnome it obviously requires it to be installed as well. But using Lubuntu with lxdm, it is unlikely to get the whole Gnome environment just to use mousetweaks. Is there another way to make things work?

---

### Post by anikol on 2012-01-10
Finally I found a [solution]("http://www.staff.amu.edu.pl/%7Ekalmar/blog/?p=247") for emulating right-clicks at the evdev level. There is no support at the current version of evdev, but after compiling the [new one]("http://cgit.freedesktop.org/xorg/driver/xf86-input-evdev/commit/?id=d9001a6be9d86a5f30549af9fbb02a466f4b0709") the feature started to work.

---

