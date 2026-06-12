---
title: "Dual Monitors - Larger One as &quot;Primary&quot;"
date: 2015-06-28
forum: Hardware
---

### Post by Glkanter on 2015-06-28
Hi Guys,

I have a 25" monitor connected to the DVI port, and I'm messing with a 19" monitor connected through the VGA port.

I use MATE, and the control panel won't let me assign the top and bottom panels to the 25" monitor.

The control panel only allows me to assign Left and Right, and the panels stay with the 19".

Any thoughts?

Thanks!

---

### Post by tgalati4 on 2015-06-28
The xorg (X11) graphics server uses the "Super Desktop" framework.  Your two monitors are added together to produce a Super Desktop with a resolution of the combination of both displays.  So if your monitors are on top of one another, the Top display will get the top panel and the bottom display will get the bottom panel.  Try it.

When you put the monitors side by side, the notion of top and bottom panels gets confusing.  So the "first" monitor, or primary monitor gets the panels and the second display is simply an extension of empty desktop space.  There are ways to play with the locations and locking the panels, but you will have to spend some time with the documentation.

MATE is based on gnome2, so *gnome-panel* tweaks may work, but again, you will have to experiment.  [http://askubuntu.com/questions/15340/spanning-gnome-panel-across-dual-monitors](http://askubuntu.com/questions/15340/spanning-gnome-panel-across-dual-monitors)

Of course, post the exact steps that you tried to get the final working configuration.

---

### Post by Glkanter on 2015-06-28
Thanks for that very informative post!
I found this via Google:
[https://wiki.gentoo.org/wiki/Xorg/Guide#Multiple_monitors](https://wiki.gentoo.org/wiki/Xorg/Guide#Multiple_monitors)
Sadly, at my "skill" level, all I can see is trouble if I start fooling around.

---

### Post by tgalati4 on 2015-06-28
Well, yes, if you create a bad xorg.conf, you will not get a display--a black screen.  Incidentally, the initial xorg.conf file will probably be put in /etc/X11/xorg.conf, but newer versions of Ubuntu have moved it.

Once you understand the Super Desktop concept, you can add panels (put them on the sides as well) to display all of your panel data and quick links.

More reading:

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

[http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there](http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there)

---

