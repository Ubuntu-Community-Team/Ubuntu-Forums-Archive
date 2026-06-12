---
title: "NVidia module not found"
date: 2011-05-17
forum: Hardware
---

### Post by ender4 on 2011-05-17
My brother recently update to 11.04.  Now he is having troubles with the graphics card.  GRUB doesn't show up on screen, but by hitting enter he can get access to a command prompt, but the X server won't start, and when we try startx, we get an error about not being able to load the nvidia module. Does anyone know how to fix this, with no access to the GUI?

---

### Post by ender4 on 2011-05-17
Solved!

 I changed the line Driver "nvidia" to Driver "nouveu" in /etc/X11/xorg.conf

---

