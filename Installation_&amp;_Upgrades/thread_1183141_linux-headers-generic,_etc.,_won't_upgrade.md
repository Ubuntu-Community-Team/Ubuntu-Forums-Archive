---
title: "linux-headers-generic, etc., won't upgrade"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by lesterness on 2009-06-09
linux-headers-generic, linux-image-generic, linux-restricted-modules-generic, won't upgrade, although everything else does.  Why? What should I do?

lesterness

---

### Post by ptn107 on 2009-06-09
The latest stable kernel update for Ubuntu is 2.6.28-11.42 and modules are 2.6.28-11.15.  Check your version numbers with:
```
dpkg -l | grep linux-
```
Your packages may not even need to be upgraded.  Did an apt-get [dist-]upgrade fail? You could force install the package with:
```
sudo apt-get install <package>
```

---

### Post by sotvomike on 2009-06-10
I am having the very same problem.  Today my desktop upgraded to 13 while my laptop is still stick at 11.  When I looked at the desktop this morning, Update Manager was already open telling me there was an upgrade available.  When I open my laptop and run Update Manager, it says my system is up to date.  I run apt-get update and apt-get upgrade and it says there is nothing to update/upgrade.

---

### Post by ptn107 on 2009-06-18
Make sure the jaunty-proposed repository in Software Sources is NOT checked.  Those packages are still being tested out.  Unless you like fixing things you shouldn't install software from that repository.

---

### Post by sotvomike on 2009-06-18
Well, I don't know what is up with this, but just right now I powered up my laptop and started Update Manager.  It said my computer was up to date.  I clicked CHECK and then there they were, the linux generic kernel updates.  Oh well, who knows?

---

