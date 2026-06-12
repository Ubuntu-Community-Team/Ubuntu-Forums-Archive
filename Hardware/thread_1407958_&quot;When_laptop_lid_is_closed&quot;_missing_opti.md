---
title: "&quot;When laptop lid is closed&quot; missing option."
date: 2010-02-15
forum: Hardware
---

### Post by hxcobd on 2010-02-15
Just picked up one of the Thinkpad X41 that Tigerdirect has on sale. Running 9.10 like a charm; the tablet features even work out-of-the-box with no tweaking!

One question though: Under the Power Management menu, on my previous 9.10 laptop, I could have sworn the option that says "When laptop lid is closed" had an option for "Do nothing."

I don't see it on this laptop. Any particular reason why this might be happening, or how to add it?

I use an external monitor 90% of the time, and would like to be able to close the laptop screen without the external monitor going black.

---

### Post by hxcobd on 2010-02-15
Answered my own question(s)!

[http://www.rebelzero.com/fixes/karmic-gnome-power-manager-hides-do-nothing-from-the-gui/223](http://www.rebelzero.com/fixes/karmic-gnome-power-manager-hides-do-nothing-from-the-gui/223)

And when you are ONLY using an external screen and want the Gnome panels on it:

[http://linux.about.com/library/gnome/blgnome4n2a.htm](http://linux.about.com/library/gnome/blgnome4n2a.htm)

(Right click a panel, uncheck "expand," drag panel to new screen)

---

### Post by phishsauce on 2011-06-24
I had a similar issue with ubuntu 10.10 and setting the option value through the gconf-editor did not work. Only when I did it using gconftool did the value take and this problem go away.

The value did end up showing in the power management dialog after setting it.

---

