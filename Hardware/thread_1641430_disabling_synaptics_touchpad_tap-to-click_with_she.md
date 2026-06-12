---
title: "disabling synaptics touchpad tap-to-click with shell script"
date: 2010-12-09
forum: Hardware
---

### Post by feuxfollets on 2010-12-09
Hello all,

I'm using a synaptics touchpad on my Envy 14, and I'm trying to get a script to disable the touchpad click. Thpere's a checkbox for it in the preferences > mouse area. There's also a file in ~/.gconf/desktop/gnome/peripherals/touchpad/%gconf.xml
that has the same options as those found in the gui menu, as far as I can tell.

There's a field for the tap to click with a boolean value, but regardless of whether I enter true or false for that value, the tap to click remains the same. If I enable tap to click via gui then it will show up in the file as true, but if I enable it in the file it does not show up in the gui (nor does tap to click work).

Does anyone know how to get this working? Thanks for the help.

---

