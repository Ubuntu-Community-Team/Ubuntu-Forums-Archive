---
title: "I just install lxde, now says wireless is wired"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by Tclarkie on 2009-09-09
I just install lxde, now says wireless is wired

---

### Post by earthpigg on 2009-09-09
you still have gnome or xfce installed, right?

if so, let's make nm-applet run in lxde:

```
sed -i 's/OnlyShowIn/#OnlyShowIn/g' /etc/xdg/autostart/nm-applet.desktop
```

this will comment out the OnlyShownIn line of /etc/xdg/autostart/nm-applet.desktop to allow nm-applet to function outside of gnome and xfce.

you can run "sudo nano /etc/xdg/autostart/nm.applet.desktop" and put the # there yourself, if you dont trust my command :D

log out of lxde, log back in.

source:
[http://sites.google.com/site/masonux/home/notes-to-myself](http://sites.google.com/site/masonux/home/notes-to-myself)

---

### Post by appier on 2009-09-10
I had the same problem.  Your instructions worked perfectly.  Thank you!

---

