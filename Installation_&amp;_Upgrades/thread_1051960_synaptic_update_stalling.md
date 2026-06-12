---
title: "synaptic update stalling"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by kdub on 2009-01-27
Trying to do todays updates and all goes well till I get to the download status bar.Nothing happens- no progress, the only way to reboot is to force the update to close. I also get the same results with the add/remove program app. Anyone know what's wrong?
thanx
kdub

---

### Post by taurus on 2009-01-27
Close down synaptic or add/remove if you have them open.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kdub on 2009-01-27
> **taurus said:**
> Close down synaptic or add/remove if you have them open.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```
It works!!
Thank you!
(uhmmm what did that command do?)
kdub (ken)

---

### Post by x33a on 2009-01-27
1. update command refreshed the sources.
2. upgrade command installed the available updates.

---

