---
title: "Changing Keyboard Layout"
date: 2008-11-14
forum: General Help
---

### Post by achelis on 2008-11-14
Hi.

I just wondered if there is an easy way to change between keyboard layouts, and have the different layouts remembered between startups (I can get it done for a single session using System->Preferences->Keyboard - but I'd prefer not having to do this step every time I boot. Alternatively, if it must be done every time I boot, I'd prefer writing a script to do it, but I have no idea what's happening behind my back when using the GUI-frontend to change the layout.

My default layout is Danish and I'm switching to UK depending on what I'm doing.

---

### Post by drave on 2008-11-14
for X checkout /etc/X11/xorg.conf

mine is looking pretty bare now (some new scheme !!) but it used to look like this for a uk/gb keyboard


Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "keyboard"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xfree86"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

---

### Post by giuspen on 2008-11-14
this is a bug in hardy... switch to intrepid and he will remember what u set from keyboard settings with no need to edit the xorg.

---

