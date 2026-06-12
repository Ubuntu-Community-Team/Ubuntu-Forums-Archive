---
title: "Using Only Some Software from PPAs"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by Otustelija on 2009-08-24
I'm trying to install two versions of Firefox at the same time: the 3.5 stable "Shiretoko" from the main Jaunty archives, and the 3.6 alpha "Namoroka" from the Mozilla daily PPA. However, since the PPA also offers the development version of 3.5, Synaptic pulls them both from the PPA.

How can I keep 3.5 to the latest in the main archives and 3.6 to the latest in the PPA?

---

### Post by zkriesse on 2009-08-24
Ah, first off why are you trying to run to different versions of Firefox at one time? That is just a LITTLE bit on the not okay side...

---

### Post by Otustelija on 2009-08-24
> **Zachk18 said:**
> Ah, first off why are you trying to run to different versions of Firefox at one time? That is just a LITTLE bit on the not okay side...

Not run at the same time, exactly. I just want to have both a development version and a stable version installed, so if the development release has a bug that prevents me from doing something, I can try with the stable one.

---

### Post by Moop on 2009-08-24
In Synaptic you can select Package and then lock version.

---

### Post by Otustelija on 2009-08-24
> **Moop said:**
> In Synaptic you can select Package and then lock version.

Locking any of firefox-3.5, firefox-3.5-branding and/or firefox-3.5-gnome-support results in "broken package" warnings...

EDIT: Nevermind, I had to disable the PPA, lock them and then enable the PPA. Now it works. Now I'll have to manually install next update to firefox-3.5, though...

---

