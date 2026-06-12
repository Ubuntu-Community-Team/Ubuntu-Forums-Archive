---
title: "Wine 1.0.1 on Kubuntu 8.04.1"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by Casper Hansen on 2009-01-30
Hey

I would know if it was possible to get Wine 1.0.1 on Kubuntu Hardy Heron 8.04.1? When I add Wine HQ's repository I get 1.1.13 which I don't want.

Regards
Casper.

---

### Post by gjoellee on 2009-01-30
Remove the wine repo and install wine: ```
sudo apt-get update && sudo apt-get install wine
```
it shoul dgive you the wine 1.0.1

---

### Post by russu52 on 2009-01-30
try here:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

they are for ubuntu, but i assume that kubuntu reads .deb packages just fine

---

### Post by Casper Hansen on 2009-01-30
> **gjoellee said:**
> Remove the wine repo and install wine: ```
sudo apt-get update && sudo apt-get install wine
```
it shoul dgive you the wine 1.0.1

Well, first of all I installed it without adding their repo, then I got Wine 1.0.

[QUOTE=russu52]try here:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

they are for ubuntu, but i assume that kubuntu reads .deb packages just fine[/QUOTE]

Hm, is it just me who's blind, but I can't find 1.0.1.

Thanks for the replies!

---

### Post by russu52 on 2009-01-30
opps! and so right you are! there were so many 1.1.1.1.1.1.'s
that i assumed it was there!

sorry mate, did not intend to lead you into a blind alley

---

### Post by Casper Hansen on 2009-01-30
> **russu52 said:**
> opps! and so right you are! there were so many 1.1.1.1.1.1.'s
that i assumed it was there!

sorry mate, did not intend to lead you into a blind alley

That's okay, just tried one of them, but it didn't help. With 1.0 First Class works fine, but I have a Danish/French dictionary that works on Kubuntu Intrepid Ibex w/ Wine 1.0.1, but it doesn't work in HH :(

---

