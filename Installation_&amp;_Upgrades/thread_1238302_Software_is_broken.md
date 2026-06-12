---
title: "Software is broken"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by oggydude on 2009-08-12
I have been trying to install a printer and have corrupted the package manager I get a message saying I have a bad package and need to do a partial upgrade

the offending package is 1l1050cupswrapper and when i try this i get the same waring and closing this box (only option) closes the upgrade with no partial upgrade taking place

---

### Post by Assim on 2009-08-12
How did you try to install the printer? By plug-and-play or another method?

---

### Post by fennec_fox on 2009-08-12
Do you mean like you can't use the package manager at all or the package manager only is stuck on those packages? 

If it's an HP printer you can install hplip and it might take care of it

Whats the make and model of the printer?

---

### Post by zvacet on 2009-08-12
```
sudo apt-get update && sudo apt-get upgrade
```

---

