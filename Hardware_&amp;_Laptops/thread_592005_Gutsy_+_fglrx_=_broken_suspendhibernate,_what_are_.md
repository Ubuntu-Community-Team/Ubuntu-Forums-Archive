---
title: "Gutsy + fglrx = broken suspend/hibernate, what are the workarounds?"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by samosamo on 2007-10-26
Suspend function worked on Feisty, now it is broken on a clean install of Gutsy with fglrx drivers.  Did some searching, it seems fglrx is not compatible with the kernel 2.6.22's new power management features (namely SLUB) which was unfortunately included in Gutsy.

One workaround is to not use fglrx.  Can anyone help me disable it?  I tried to disable it via Restricted Drivers Manager, but after rebooting Gnome would quit with XGL(?) errors.  I had to reenable fglrx in fail-safe mode.

Another workaround may be to use Feisty's kernel.  Can anyone help me install it?  I would much rather downgrade just the kernel than downgrade Ubuntu by reinstalling Feisty.

---

### Post by blu3ness on 2007-10-26
second this post, having the exactly same problem, I upgraded to gutsy, so I still have my old kernel, however, when I boot with the older kernel, there seems to be some problem with the new XGL, screen has some broken pieces around the corners, direct rendering is also disabled.

---

### Post by samosamo on 2007-10-26
morning bump

---

### Post by samosamo on 2007-10-26
I am currently compiling a 2.6.23.1 kernel using the Gutsy stock config (after running it through oldconfig).  I made one important change: Use SLAB instead of SLUB (which is default).  I will post results.

---

### Post by cow_racer on 2007-10-27
> **samosamo said:**
> Suspend function worked on Feisty, now it is broken on a clean install of Gutsy with fglrx drivers.  Did some searching, it seems fglrx is not compatible with the kernel 2.6.22's new power management features (namely SLUB) which was unfortunately included in Gutsy.

One workaround is to not use fglrx.  Can anyone help me disable it?  I tried to disable it via Restricted Drivers Manager, but after rebooting Gnome would quit with XGL(?) errors.  I had to reenable fglrx in fail-safe mode.

Another workaround may be to use Feisty's kernel.  Can anyone help me install it?  I would much rather downgrade just the kernel than downgrade Ubuntu by reinstalling Feisty.

to disable fglrx, 

sudo gedit /etc/X11/xorg.conf

Then search for "fglrx"

change it to "vesa".

save xorg.conf.

reboot.

You should be able to suspend your laptop after that.

There is no performance difference except no 3d graphics.

---

### Post by samosamo on 2007-10-27
Thank you for that tip.

Compiling my own kernel turned out to be more trouble than it was worth.  Is there any other way to use SLAB instead of SLUB without recompiling the kernel?

---

### Post by blu3ness on 2007-10-27
i doubt it... :x

I upgrade my feisty (in full working condition) to gutsy (almost full working condition, except hibernate and suspend), so I still have my old kernel images, I tried using those ( i believe the version is 2.6.20-16),however, the XGL server doesn't start properly with that kernel version.

I'm thinking of just downgrading to feisty completely, or just live without suspend for 6 months and waiting for a fix from fglrx or the next release.

---

### Post by samosamo on 2007-10-28
Given up.  Downgraded back to Feisty.  Next time I won't be so fast to upgrade.  Maybe by then I'll have an ATI-free laptop anyway.  Time to boycott companies who can't get with the act.

---

### Post by blu3ness on 2007-10-28
Yep, I have also jumped the ship, gutsy is just not stable enough for people with Ati cards.

---

