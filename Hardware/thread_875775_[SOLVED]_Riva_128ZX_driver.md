---
title: "[SOLVED] Riva 128ZX driver"
date: 2008-07-31
forum: Hardware
---

### Post by adudutz on 2008-07-31
my dad has a riva 128zx installed with ubuntu. I think I need to download a driver for his pc cause after installing ubuntu, the vga is not working fully. When he was using xp, it can reach 1024*768 @ 85hz. In ubuntu it was only 800*600 @ 60hz. I think this is kind of disturbing.

Any suggestions where to download? He doesn't have any internet connection.

---

### Post by overdrank on 2008-07-31
> **adudutz said:**
> my dad has a riva 128zx installed with ubuntu. I think I need to download a driver for his pc cause after installing ubuntu, the vga is not working fully. When he was using xp, it can reach 1024*768 @ 85hz. In ubuntu it was only 800*600 @ 60hz. I think this is kind of disturbing.

Any suggestions where to download? He doesn't have any internet connection.

Hi and you may try the command using the alt, F2 keys
```
gksu displayconfig-gtk
``` there you may adjust your settings.

---

### Post by adudutz on 2008-07-31
I also want to ask, how to display the device manager (or such thing) on ubuntu?

---

### Post by adudutz on 2008-07-31
I've tried your solution, but the max display is still 800*600 @ 60hz. My monitor can support much more (Philips 107E).

---

### Post by overdrank on 2008-07-31
> **adudutz said:**
> I've tried your solution, but the max display is still 800*600 @ 60hz. My monitor can support much more (Philips 107E).

Hi and have you tried to select a higher resolution monitor there in display configure. You may be able to change the monitor with the command I gave.

---

### Post by adudutz on 2008-07-31
Well, it seems that it is working properly, but on the logon screen, the screen is not centered (I can't see the bar below)

EDIT: I've managed to adjust the monitor, so it will display correctly both on the desktop and the logon screen. Also, the driver is automatically detected.

Problem SOLVED.

---

