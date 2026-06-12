---
title: "[SOLVED] OK, so I fiddled"
date: 2008-07-12
forum: General Help
---

### Post by basicuser on 2008-07-12
Just installed a second monitor to Packard Bell laptop running 8.04.

I tweaked the screen resolutions, then got a window telling me my graphics card couldn't be detected and I had to set up manually.

I think I must have chosen the wrong driver because now the screen(s) are a mass of illegible lines, so I can't log on.

Tried rebooting with and without second screen. No good.

What's the emergency procedure?

Thanks in advance

---

### Post by jpeddicord on 2008-07-12
Reboot, and at the GRUB menu (the one that says "Press ESC for menu" at startup) select an option with "recovery mode" at the end of it.

Let the system boot, and then:
**8.04 or above**
When the menu appears, select "Fix X configuration" or similar.
If that fails, or you simply get a command line, run **dexconf** and reboot.

**7.10 or below**
Once the terminal appears, run **dpkg-reconfigure -phigh xserver-xorg**

---

### Post by basicuser on 2008-07-12
Thanks. It worked.

---

