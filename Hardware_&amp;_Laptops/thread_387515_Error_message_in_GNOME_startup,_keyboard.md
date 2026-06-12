---
title: "Error message in GNOME startup, keyboard"
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by Ryupower on 2007-03-18
Hey
I tried changing the keyboard layout by the keyboard menu, it didn't change, instead-
 now, whenever I start a Gnome session I get the following error message: 
> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70000000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

I changed the keyboard layout back to default, I still get that message.

I reinstalled the named packages via synaptic, but it still won't go away....

HELP! ANYONE! How can I get rid of that message and change the keyboard layout knowing I WON'T get it again?

BTW: KDE doesn't give me that error. Only GNOME.

---

### Post by happy-and-lost on 2007-03-18
> If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

Please :)

---

### Post by Ryupower on 2007-03-18
> **happy-and-lost said:**
> Please :)



> If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

What does that message mean though?
Has anyone else had this?

---

### Post by Ryupower on 2007-03-22
anyone?
Also: KDE doesn't do some of my keys right, like, I'd type, but nothing appears

---

