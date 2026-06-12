---
title: "I'd like my upgrade to feel like a new install, possible?"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by concord on 2009-04-24
:guitar:


Today I upgraded my 8.10 Ubuntu desktop to 9.04 just as I had upgraded my 8.04 Ubuntu desktop to 8.10 six months ago.

Over the years I've set my desktop up with applets, panels, icons, etc... but I'd like to start over again (at least as far as the appearance of the desktop).  Can I do this?

If I delete my .gnome2 directory I assume I'll lose all kinds of stuff.  What file(s) would I delete to just have my desktop appear the same way it would if I did a completely clean install?

Thanks in advance.

---

### Post by zvacet on 2009-04-24
```
sudo /etc/init.d/gdm stop

rm -rf .gconf* .gnome* .nautilus*

sudo reboot
```

---

### Post by Bakon Jarser on 2009-04-24
Or you could make a new user.

---

