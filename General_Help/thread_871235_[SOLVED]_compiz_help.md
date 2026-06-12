---
title: "[SOLVED] compiz help"
date: 2008-07-26
forum: General Help
---

### Post by mikedemario17 on 2008-07-26
so i got a new card its a = Radeon 9250 128MB PCI graphics Card


> mike@mike-desktop:~$ sudo lshw -short | grep display
PCI (sysfs)
/0/100/1e/9 display RV280 [Radeon 9200 PRO]
/0/100/1e/9.1 display RV280 [Radeon 9200 PRO] (Secondary)
mike@mike-desktop:~$
when i go to enable the restricted drivers... it says there are none and under the package manger it says compiz is already installed but the custom setting dont show up under visual effects and there is no advanced graphics setting under admin... whats wrong?

---

### Post by MatthewPlanchard on 2008-07-26
Do you have the package compizconfig-settings-manager installed?

```
sudo aptitude install compizconfig-settings-manager
```

---

### Post by mikedemario17 on 2008-07-26
i found it out

---

### Post by MatthewPlanchard on 2008-07-26
What was the problem, specifically?

---

### Post by mikedemario17 on 2008-07-26
my repositories wernt cheeked under System->administration->Software Sources->Ubuntu Software (tab) none checked.

---

### Post by saratchandra on 2008-07-27
> **mikedemario17 said:**
> my repositories wernt cheeked under System->administration->Software Sources->Ubuntu Software (tab) none checked.

aaaahhh, I remember doing that when I was new to compiz:)

---

### Post by mikedemario17 on 2008-07-27
YEAH...i went and got all the fancy stuff for linux and when i got kiba dock thing the pc crashed and it destroyed my 40GB xp drive so now im on my 30gb win.2000

---

