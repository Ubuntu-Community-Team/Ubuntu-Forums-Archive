---
title: "Display won't open"
date: 2009-07-13
forum: Hardware
---

### Post by ltwinner on 2009-07-13
I wanted to get dual monitors going with linux mint so I plugged in my spare dell monitor, went to display and enabled 'separate x view' for it, then I enabled xinerama on both monitors. I saved the configuration file and restared. It turns out that this spreads the desktop background over two monitors which is not what I wanted, I want separate backgrouns on each monitor.

However since doing that, Display will no longer open so I can't reset it back to the way it was. I just get a message saying "Could not get screen information" and "RANDR extension is not present". Anyone know what's going on here?

---

### Post by dezert on 2009-07-13
I have exactly the same problem too. I guess I'll have to manually edit xorg.conf to disable Cinerama until this bug is solved. I think iy may have to do with the bug recently reported, which I also have, in which you can't turn on visual effects in Compiz.

---

