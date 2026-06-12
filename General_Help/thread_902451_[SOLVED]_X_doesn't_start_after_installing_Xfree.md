---
title: "[SOLVED] X doesn't start after installing Xfree"
date: 2008-08-27
forum: General Help
---

### Post by yetanotheruser on 2008-08-27
Hello all,
I'm quite new to Ubuntu and I'm experiencing some serious trouble with it...

When it tries to start X, the screen flashes for a while and then I get a "No signal" message.

This happens since I installed (or, more likely, tried to install) Xfree, although (apparently) the installation went fine.

I can run fine recovery mode (I tried xfix but didn't work)

I searched a lot, but I found only one post similar to this. It suggested to run
> apt-get install xserver-xorg
but since I was in recovery mode I couldn't connect to the internet (stupid wifi) and download it. Neither downloading the package from [packages.ubuntu.com]("http://packages.ubuntu.com/") solved the problem (could it depend on the fact that I ran it from an NFTS disk?).
Moreover when I try to remove any xfree-related package with dpkg -r it says that they're already uninstalled.

I am running Hardy, any suggestion is welcome. Forgive any English mistake. :-)

[SIZE="1"]By the way... you may be wondering why I wanted to install Xfree... but this will be subject of another thread, as soon as this problem is solved ;)[/SIZE]

---

### Post by LateNiteTV on 2008-08-27
what version of ubuntu are you using and why wasnt xorg installed by default?

---

### Post by yetanotheruser on 2008-08-27
Xorg was installed by default, but I started messing up with Totem's code (the media player) and the "Audio buttons" keys did no longer work, since they were defined
> #ifdef GDK_WINDOWING_X11
/* X11 headers */
#include <gdk/gdkx.h>
#include <X11/Xlib.h>
#ifdef HAVE_XFREE
#include <X11/XF86keysym.h> [COLOR="Red"]<-- HERE[/COLOR]
#endif
#endif

Thinking that Xfree would have given me that keys back, I installed it (yes, I know I'm a n00b)

EDIT: I re-installed all the xorg packages (x11-common, xserver-xorg, xserver-xorg-core & xserver-xorg-input-*) and got my X server back but still some buttons on my keyoard don't work (at sign, sharp sign don't work anymore). It also seems that the screen no longer has anti-alising (or is it a my impression after switching back from a lower resolution Windows?)

---

