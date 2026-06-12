---
title: "Uprgeded ubuntu to 9.10, now i have xubuntu???"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by Thoralex on 2009-11-07
I just upgraded from Ubuntu 9.04 using the update manager, and now i suddenly have Xubuntu. What append and how do i fix it?

---

### Post by coffeecat on 2009-11-07
When you say Xubuntu, I guess you mean the desktop is now Xfce, but during the boot-up sequence is the branding Xubuntu rather than Ubuntu? And is the login screen an xfce rather than a gdm one? Although I wouldn't know what that looks like.

Did you at any time, when you were running 9.04, install the meta-package xubuntu-desktop, in order to get the Ubuntu-ised Xfce desktop as an alternative to gnome? If so a dist-upgrade would have upgraded both the gnome and xfce packages and perhaps, through some obscure bug, your system now defaults to all the Xubuntu bootup stuff and Xfce is the default desktop. If this is the case, when you next get to the login screen, click on 'options' and choose gnome. You should be able to set that as default. But if you are getting a blue (or whatever colour it is now) Xubuntu boot sequence, I can't help you.

If you didn't install xubuntu-desktop during your 9.04 time, all I can say is that this is very bizarre. I guess all you could do is install the metapackage 'ubuntu-desktop' and all its dependencies and log into the gnome desktop as described above.

---

### Post by Thoralex on 2009-11-07
Thanks, figured it out now. I still have ubuntu, but for some reason it started up with xfce.

---

