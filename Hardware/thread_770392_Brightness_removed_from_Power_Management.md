---
title: "Brightness removed from Power Management ??"
date: 2008-04-27
forum: Hardware
---

### Post by Onesimus on 2008-04-27
Having recently installed Hardy, I am having a few problems adjusting the brightness of my laptop screen.  From memory there was the ability to adjust the brightness in the Power Management of Gutsy.  This appears to have now disappeared.  I can adjust brightness using the keyboard but it alters the brightness from 0% to 100% in one go - there is no fine adjustment.

As the screen brightness affects laptop battery life time - I am keen to have this resolved.

---

### Post by zgoda on 2008-04-27
The only way to set LCD dim on battery is to manually edit the key /apps/gnome-power-manager/backlight/brightness_battery in gconf-editor.

---

### Post by jordiR on 2008-04-27
Or you can add the gnome-brightness-applet to your panel.

---

