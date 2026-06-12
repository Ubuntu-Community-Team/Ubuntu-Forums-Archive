---
title: "need help undoing a divert"
date: 2008-11-17
forum: General Help
---

### Post by jbeiter on 2008-11-17
Awhile back I tried to install firefox 3 and reconcile the problems with updates by following the instructions to divert the package on this website [http://linuxowns.wordpress.com/2008/02/15/install-firefox-3-beta-3-on-ubuntu/](http://linuxowns.wordpress.com/2008/02/15/install-firefox-3-beta-3-on-ubuntu/)

Now, I can't de-install firefox or update via synaptic. Can anyone tell me how to remove that divert directive?

Thank you

---

### Post by jbeiter on 2008-11-17
when I try to update or remove firefox, I get this error:

E: /var/cache/apt/archives/firefox-3.0_3.0.3+build1+nobinonly-0ubuntu0.8.04.1_i386.deb: trying to overwrite `/usr/bin/firefox', which is the diverted version of `/usr/bin/firefox'

The current build of firefox I'm running sucks, incredibly. I would like to get this fixed and updated via the normal update channel.

How do I rip this out?

---

### Post by cdtech on 2008-11-17
You need to manually remove the divert.
(to see the diversions)
```
dpkg-divert --list
```
use dpkg-divert --remove to remove the diversion.

---

### Post by jbeiter on 2008-11-17
Thank you! that worked.

---

### Post by cdtech on 2008-11-17
congrats... :guitar:

---

