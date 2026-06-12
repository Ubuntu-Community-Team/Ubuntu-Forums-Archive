---
title: "procedure upgrading from 7.04 to 7.10"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by malcove on 2009-01-20
Following the upgrade instructions, regarding the changes to sources.list at
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)
does not quite work.

You need to do the following:
1) backup your sources.list
2) completely replace sources.list with those lines it suggests adding
3) run the upgrade procedure until you get an error about missing mirror.
4) before answering the prompt, copy back the original source.list
5) pick yes.

just thought I'd mention it in case anyone else had problems upgrading 7.04

---

### Post by Pumalite on 2009-01-20
Or you could try this:
```
sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 
sudo apt-get update 
sudo apt-get dist-upgrade 
```

---

