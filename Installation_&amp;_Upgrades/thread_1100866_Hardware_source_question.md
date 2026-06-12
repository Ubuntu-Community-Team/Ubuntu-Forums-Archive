---
title: "Hardware source question"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by Hagar55 on 2009-03-19
I'm using Intrepid for the moment but I upgraded it from a Hardy install.
When I check the packages I get errors reffering to hardy sources, mainly from Banshee, AWN, but also from KDE4 (wich I installed as well).

Should I remove these from the sources list or not ?

---

### Post by Pumalite on 2009-03-19
When you upgrade; you are supposed to remove all third parties from your sources.list first. So do.

---

### Post by zvacet on 2009-03-19
You have this options:

1. remove sources from source list
2.just put # sign in front of that lines 
3.replace hardy with itrepid in that lines (if you don´t allready have same intrepid lines)

Whatever option you choose after that type in terminal

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Hagar55 on 2009-03-23
Thanks, I think I'll wait untill the next upgrade to Jaunty.
Maybe even do a clean install then

---

