---
title: "Dist upgrade with unsupport fglrx ati card. How do I get the option back?"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by tipp98 on 2009-07-18
I am running Kubuntu 8.04.3 with ATI Technologies Inc RV350 AP [Radeon 9600]. The card is not supported with newer fglrx drivers and thus is not supported in newer releases through fglrx. A while back I had a dist-upgrade dialog saying that the card was not supported through fglrx and if I still wanted to upgrade. I selected no and not to ask again. I have since disabled proprietary driver support and now wish to upgrade, how do I do this?

sudo apt-get update
sudo apt-get dist-upgrade

has nothing to do.

---

### Post by tipp98 on 2009-07-18
found it [https://help.ubuntu.com/community/IntrepidUpgrades/Kubuntu]("https://help.ubuntu.com/community/IntrepidUpgrades/Kubuntu")

```
kdesudo "adept_manager --dist-upgrade" 
```

---

