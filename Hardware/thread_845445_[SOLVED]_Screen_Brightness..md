---
title: "[SOLVED] Screen Brightness."
date: 2008-06-30
forum: Hardware
---

### Post by Newuser1111 on 2008-06-30
Is there a way to keep it always on the lowest brightness?

---

### Post by phidia on 2008-06-30
You can add the brightness applet to one of your panels from right clicking the panel and selecting "Add to Panel..." The brightness applet is in the system & hardware section. On a desktop monitor and maybe some laptops too you can also do this from the monitor menu or screen brightness button.

---

### Post by AlesUbu123 on 2008-06-30
If you want to have brightness permanently set to minimum you could do this:
1. In the terminal, type:
```
gconf-editor 
```

in case gconf-editor is not installed, use :
```
sudo apt-get install gconf-editor
```


2. In the right column click apps, then gnome-power-manager, then backlight.

3. In the right window set values of brightness_ac, brightness_battery and idle_brightness to 0.

Hope it helps!

---

### Post by Newuser1111 on 2008-06-30
Thanks!

---

