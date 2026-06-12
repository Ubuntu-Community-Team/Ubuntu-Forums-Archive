---
title: "Wine: where is wine?!!!"
date: 2005-12-15
forum: Installation &amp; Upgrades
---

### Post by spacifique1 on 2005-12-15
I installed wine two times using synaptic. It worked fine. I also got the lib and winetools. After install, i can`t find any link to wine...
Any help?

---

### Post by aysiu on 2005-12-15
Find the .exe file you want to open with Wine. Right-click on it and select "open with" and "Wine."

---

### Post by spacifique1 on 2005-12-15
Ok. I installed DVD shrink. Thanks.

---

### Post by MetalMusicAddict on 2005-12-15
I would add these lines to your repos:

[B]sudo gedit /etc/apt/sources.list
[/B]
Then add lines:
[B]deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/[/B]

Then:
**sudo apt-get update**

Search for WINE.

They are repos right from the WINE guys. The version in Breezy I had so much trouble with. The current WINE is great. :)

---

