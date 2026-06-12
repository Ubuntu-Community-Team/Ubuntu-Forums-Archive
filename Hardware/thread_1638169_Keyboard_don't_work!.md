---
title: "Keyboard don't work!"
date: 2010-12-05
forum: Hardware
---

### Post by morenosolis on 2010-12-05
First, Sorry for my English...

Well, I use Ubuntu Lucid and this happened:

Yesterday I update using APT-GET and now my keyboard is not working... at least in graphic mode.

I test killing X server and the keyboard works fine in cosole mode and into other SO.

Some weeks ago I try to get my nVidia video card works with Hardware Acel... so I installed the Xorg and xserver-xorg packages from xorgedgers repository... and that not works... I leave the packages installed and all works fine. Yesterday I tray to install libSDL but it wasn't compatible with some like "libglu-mesa" so I downgrade to the official repository version and I installed SDL. Later I realize the third level keys don't work... So I went to Menu -> Preferences -> Keyboard and try to get the third level keys works again but then the keyboard stop working except the numerical keyboard at the right.

I think the trouble is on X11... I reinstalled xserver-xorg and xorg from official repository and don't works... copy the /usr/share/X11/xkb from another partition and I still having the same trouble!

Somebody can help?? Please!

Thanks a lot!

---

