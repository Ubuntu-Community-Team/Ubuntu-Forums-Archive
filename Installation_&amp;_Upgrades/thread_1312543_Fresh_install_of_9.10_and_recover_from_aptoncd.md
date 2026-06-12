---
title: "Fresh install of 9.10 and recover from aptoncd"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by hariks0 on 2009-11-03
Hey all,

I upgraded from 9.04 to 9.10 using alternate cd and it crashed at the end. But I can boot to 9.10 but with some problems. Fortunately, I had taken aptoncd before upgrade.
My questions are 

1. Whether I can repair the crashed 9.10 ?

2. Or whether I can do a fresh install of 9.10 and use the aptoncd to get back all my applications of 9.04 into 9.10 ?

FRESH INSTALL 9.10 --> APTONCD 9.04

3. Or should I do a clean install of 9.04 followed by recovery from aptoncd and upgrade from the alternate cd.

FRESH INSTALL 9.04 --> APTONCD 9.04 --> ALTERNATE 9.10 UPGRADE

Thanks in advance for any help.

---

### Post by zvacet on 2009-11-03
You can try to repair with this commands

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove
```

If that does't work try fresh install.

---

