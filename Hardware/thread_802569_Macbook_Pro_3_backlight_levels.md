---
title: "Macbook Pro 3 backlight levels"
date: 2008-05-21
forum: Hardware
---

### Post by zhark1 on 2008-05-21
Hello!

When turning the brightness to the bare minimum (no light), and increasing it one level in Ubuntu (with pommed), the screen is much brighter than the second lowest level in OSX. In OSX one has 2-3 brightness levels in between level 0-1 in Ubuntu. The screen is almost too bright (at night) at the backlights lowest level without beeing completely turned off in Ubuntu. Does anyone know of a fix/workaround for this problem?

Macbook Pro rev3: 15.4", Santa Rosa, Nvidia 8600m GT.

---

### Post by zhark1 on 2008-05-24
Bump, plus a related question, when I put my MBP to sleep (suspend to RAM) and awakens it afterwards, the brightness level of the display is not restored, and is always at maximum brightness. This particular problem wasn't (as far as I can remember) present in Gutsy.

Edit: Fixed the brightness restore thing by adding /etc/init.d/pommed restart to a file in /usr/lib/pm-utils/sleep.d

---

