---
title: "Loosing keyboard layout"
date: 2008-10-14
forum: General Help
---

### Post by Zlatan on 2008-10-14
Hello,

one of my PC-s Ubuntu Hardy (GNOME) is loosing keyboard layout. Choosing default layout is not active. After each booting it looses Lithuanian layout or it does not work. USA layout is OK. So Lithuanian layout has to be added again.
Maybe someone has already managed how to deal with this?

Thank you

---

### Post by Elfy on 2008-10-14
Try adding the code, which I think is lt, to xorg.conf, there will be a part looks like

> Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "uk"

add "lt" to the layout line, backup and edit, then restart x with Ctrl+Bkspace

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.1410
gksudo gedit /etc/X11/xorg.conf
```

---

