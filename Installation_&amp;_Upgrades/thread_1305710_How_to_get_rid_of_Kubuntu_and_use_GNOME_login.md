---
title: "How to: get rid of Kubuntu and use GNOME login"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by moe_syzlak on 2009-10-30
This is for the people who tried out Kubuntu desktop and want to go back to gdm as the default display manager:
[SIZE="4"]1 - open Synaptic
2 - remove kdm, and the relevant helper programs that Synaptic recommends
3 - make sure gdm is installed before rebooting. most likely it is. if not, then install gdm
3 - reboot
4 - you should be presented with normal gdm login[/SIZE]

**[COLOR="Red"]Note: I did this on Karmic Koala 9.10[/COLOR]**

To uninstall all those crazy KDE apps (Amarok, Kate, Korganizer, Kontact, etc.) that came with the kubuntu-desktop install:
[SIZE="4"]1 - launch Synaptic
2 - uninstall kdebase-runtime-bin-kde4, kdebase-bin, and kdebase-workspace-bin[/SIZE]

---

### Post by moe_syzlak on 2009-11-04
Here is a guy who has more information on this. The steps are identically the same.

[LINK] [http://computersight.com/operating-systems/linux/how-to-uninstall-kubuntu-desktop/](http://computersight.com/operating-systems/linux/how-to-uninstall-kubuntu-desktop/)

---

