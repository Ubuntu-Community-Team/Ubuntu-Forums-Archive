---
title: "Difference between update-manager -d and changing sources"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by MarcusW on 2009-10-25
I'm thinking of upgrading 9.04->9.10 when karmic comes out, but I don't like the fact that upgrades seem to sometime mess up the install (from what I've read here). So I was wondering, is it "safer" to just replace all jaunty->karmic in sources.list or is that the exact same thing as update-manager -d?

A clean install is not really an option right now, and I don't have enough space to do a full system backup...

---

### Post by mac9416 on 2009-10-25
I tried 'update-manager -d' first, but it (for whatever reason) insists on installing ubuntu-desktop when upgrading. I use Fluxbox and have removed most of what comes with ubuntu-desktop, so it would have downloaded quite a few debs that I didn't need. So, I went for the sources.list method. The upgrade took all night, and I believe my laptop must have overheated. In short it failed, and I had to download alpha 6 and do a fresh install.

The moral of this story: 'update-manager -d' is probably better unless you have slimmed down your installation and don't want to reinstall all that you had removed. Also, start the upgrade in the morning so you can keep an eye on it.

Good luck!

---

### Post by sandivilli on 2009-10-25
.... and, whats the differemce between updating from 9.04 to 9.10, if i update my ubuntu everitime it asks me (with /usr/bin/update-manager). My system is update alright?
So, why i've to "update" to 9.10 ?


thanks

---

