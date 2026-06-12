---
title: "Ugly!!"
date: 2008-07-21
forum: Hardware
---

### Post by connord94 on 2008-07-21
Experts,

I have ubuntu hardy (8.04) installed on an external hard drive, all works fine, I took my hard drive to my dads house and used it on his computer, and It didn't recognise his graphics card, and ran in low graphics mode, fair enough. But now I on my own computer again, It's still running in low graphics mode, with a crap resolution! How do I redetect my monitor/graphics card, I've tried the reconfigure xorg thing, but that just takes me through the setup of a keyboard!

Help getting my own screen res etc. back ?? ??


Connor

---

### Post by connord94 on 2008-07-21
Sorry for the time waste, a simple reboot did the trick - I really need to try all of the possibilities before I seek help...


Connor

---

### Post by coffeecat on 2008-07-21
It's not a time waste, don't worry. In case you come back to this thread, a nugget of information for you. Did you have the monitor switched off when you booted up? If the Xserver (the basis of the GUI) can't detect a monitor, it will default down to a low-resolution. You didn't have to reboot. A simple logout and login (with the monitor switched on :wink: ) would have done.

By the way, the Xserver doesn't start handling the display until the login screen. Before that (and during shutdown) it's some sort of framebuffer display.

---

