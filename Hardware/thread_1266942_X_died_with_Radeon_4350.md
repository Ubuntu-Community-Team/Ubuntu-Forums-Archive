---
title: "X died with Radeon 4350"
date: 2009-09-15
forum: Hardware
---

### Post by taddy_porter on 2009-09-15
I was experiencing random lock-ups and wanted to rule out the video card, so I uninstalled FGLRX (via jockey). I didn't restart X then. It locked up a couple hours later and I had to hard boot.

When reboot was done, I was presented with a plain white screen. ctrl-alt-backspace took me back to gdm. I logged in to KDE (usually use gnome) and everything worked fine. I reinstalled FGLRX (via sudo jockey-gtk) and reloaded X. I got a black screen that didn't respond to any cntrl-alt commands.

Rebooted into the terminal, removed FGLRX, reconfigured X, and rebooted again. Presented with a black screen, cntrl-alt don't work. Monitor reports I'm getting 1680x1050, no start up sounds.

Terminal, manually configured xorg.conf to load Radeon drivers. White screen. Set KDM in place of GDM so I didn't try to login to gnome, but still white screen.

That's where I'm at now. I'm connected to an LCD screen via vga (also have dvi, but it doesn't work). Where do I go from here?

---

