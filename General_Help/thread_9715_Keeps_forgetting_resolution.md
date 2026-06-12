---
title: "Keeps forgetting resolution"
date: 2004-12-31
forum: General Help
---

### Post by techn9ne on 2004-12-31
Everytime I login I have to keep setting my resolution. When I logout I hit the button that says "save settings" but it doesn't work.

Can I edit some config files manually somewhere ?

---

### Post by techn9ne on 2004-12-31
I fixed it myself by going into applications->system->configuration editor and finding the value and changing it manually for all users.

---

### Post by Ufo on 2005-01-01
I had samekind of problem after installation.
I wanted to drop the resolution installation had chosen.
Changing it from menus lasted only for that session.
So i changed it by running in console

sudo dpkg-reconfigure xserver-xfree86

and choosing lower value there.
After restarting gdm with

sudo /etc/init.d/gdm restart

resolution has been ok.

---

