---
title: "installation halted accidentally"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by ecoli0157h7 on 2009-01-05
Hey guys,

My officemate accidentally turned off a desktop while upgrade to 8.04 is being done. After I've powered on the PC again, the ubuntu would not go further after the log-in screen. All I've got is a blank brown screen. I tried rebooting the system in the recovery mode and tried also dpkg --configure -a but I encountered a ton of dependency problems which I cannot understand. How can I re-install Ubuntu without formatting my old partition? I have very important files and documents on my previous system.

Help!!!

---

### Post by iaculallad on 2009-01-05
While booted on recovery mode, try:

```
sudo apt-get install -f
sudo dpkg --configure -a
sudo xfix
startx
```

---

### Post by ecoli0157h7 on 2009-01-05
> **iaculallad said:**
> While booted on recovery mode, try:

```
sudo apt-get install -f
sudo dpkg --configure -a
sudo xfix
startx
```

firstly, thanks.

I already tried all the codes you gave above but the problems aren't fixed yet--still the same. I think the computer was shut down during the installation phase of the upgrade and corrupted a chunk of files/registry on my previous system. How can I correct these?

---

