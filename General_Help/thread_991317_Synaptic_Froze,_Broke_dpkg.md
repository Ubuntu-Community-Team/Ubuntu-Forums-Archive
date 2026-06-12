---
title: "Synaptic Froze, Broke dpkg"
date: 2008-11-23
forum: General Help
---

### Post by gamechampionx on 2008-11-23
Synaptic froze on me and left my packages in an inconsistent state.

Now, when I open it, it tells me to run "dpkg --configure -a".

I run the said command and I'm greeted with:

(user and system junk)$ sudo dpkg --configure -a
Setting up rocksndiamonds (3.2.4+dfsg-2) ...
Update menu
sh: update-menus: not found
/usr/share/games/rocksndiamonds/downloads/rocksndiamonds-3.2.4.tar.gz: OK
/usr/share/games/rocksndiamonds/downloads/Zelda-1.0.0.zip: OK
/usr/share/games/rocksndiamonds/downloads/Emerald_Mine_Club-2.0.0.7z: OK

It just sits there for a long time.  It doesn't seem to do anything.

I tried to find a more verbose output mode with no luck.  I've seen this problem posted elsewhere but I couldn't find a solution.

---

