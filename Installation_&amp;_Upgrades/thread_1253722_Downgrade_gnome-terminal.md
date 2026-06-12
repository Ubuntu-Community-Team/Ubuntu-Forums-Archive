---
title: "Downgrade gnome-terminal"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by Winterhart on 2009-08-30
Since the Jaunty version of gnome-terminal (2.26.0) breaks devilspie, I'd rather like to downgrade it back to 2.22.x.

I tried adding a Hardy mirror and using package->force version in synaptic to force gnome-terminal and gnome-terminal-data back to 2.22.1, but before I can reinstall them I get notified that the changes will cause ubuntu-desktop to be uninstalled.

What gives?  The terminal is *not* a required part of gnome-desktop, and there has to be a way to downgrade it.

---

### Post by earthpigg on 2009-08-30
> **Winterhart said:**
> 
What gives?  The terminal is *not* a required part of gnome-desktop, and there has to be a way to downgrade it.

ubuntu-desktop is a metapackage. it contains nothing except a list of things *Ubuntu* considers essential. for that package to be installed, it is a requirement that everything on the list be installed.... but uninstalling ubuntu-desktop will not uninstall any actual software on your computer.

it would appear you disagree with Ubuntu about what is essential.

if it where me, i would go ahead and uninstall ubuntu-desktop. but you are not me. the choice is yours.

if you dont want to fight ubuntu's way of doing things: an alternative you may want to consider, however, is to try some other terminals - they all work fine.

open synaptic and search for 'terminal'. install a dozen of them and see which one you prefer.

uninstall the dozen-minus-one that did not meet your needs, and stick with the one that does.

one unconventional terminal you may want to check out is 'hotwire'.

---

### Post by Winterhart on 2009-08-30
> **earthpigg said:**
> ubuntu-desktop is a metapackage. it contains nothing except a list of things *Ubuntu* considers essential. for that package to be installed, it is a requirement that everything on the list be installed.... but uninstalling ubuntu-desktop will not uninstall any actual software on your computer.


Fantastic, thanks very much!

I rather prefer xterm when I don't have anything else riding on it, but in this case (a transparent terminal 'embedded' on the desktop via devilspie) I specifically need gnome-terminal's "profile" functionality.  The latest version of gnome-terminal apparently fixed some hacks that devilspie had been taking advantage of, hence the need to downgrade to maintain the desired functionality (see [bug report #522533]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=522533") for more details.)

I'll check out hotwire for my normal terminal usage; again, thanks!

---

