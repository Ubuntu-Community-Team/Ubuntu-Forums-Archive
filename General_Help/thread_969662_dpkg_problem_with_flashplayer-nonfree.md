---
title: "dpkg problem with flashplayer-nonfree"
date: 2008-11-03
forum: General Help
---

### Post by Game_boy on 2008-11-03
*Ubuntu 8.10 32-bit Final*

While installing a set of packages in Intrepid, it got stuck on flashplugin-nonfree (i.e. it was downloading, but at a rate which would take hours to complete). I ended the process because I couldn't stop it any other way.

Now, I cannot install anything before running dpkg --configure -a (obviously), but I can't run that without hitting the flashplugin-nonfree problem. 

1. How can I remove flashplugin-nonfree from the list of things to be installed so I can dpkg --configure -a without stalling?

2. How can I make the flashplugin-nonfree package download and install correctly?

---

### Post by sisco311 on 2008-11-03
try:
```
sudo aptitude -f install
```

---

### Post by Game_boy on 2008-11-03
> **sisco311 said:**
> try:
```
sudo aptitude -f install
```

Tells me to dpkg --configure -a like anything else. What should it have done?

---

