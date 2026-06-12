---
title: "upgrade related quiery"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by abhinav.p on 2009-06-21
this might seem a bit stupid but is there any difference in the upgrade done online and clean  installation using a cd.i wanted to upgrade and want to know which is better..

---

### Post by drs305 on 2009-06-21
A network /online upgrade will preserve your personal settings, which are stored in /home. This would include your email settings, panel shortcuts, display optimizations, etc. Unless you have a separate /home partition, a clean install will not. Also an online upgrade will save system configuration settings in /etc (such as network settings) that would have to be recreated from a fresh install.

With a clean install, you start from the beginning. You can reset partition sizes, applications that you have added since the original installation will have to be manually reinstalled, the system will have no extraneous bits and pieces and accumulated files no longer needed. You will probably be surprised at how many things you have changed and will require reconfiguring. If you have installed apps in a special way to get them to work with your computer, you will have to repeat these steps again.

It's a personal choice. If you want to keep your system pretty much the way it is without a lot of tinkering, an online upgrade would be less work. If you want to clean everything out, start fresh, and don't mind spending the time to tweak everything to your liking, a clean install may be a better answer.

---

### Post by abhinav.p on 2009-06-21
but would'nt it be sometimes necessary to have old application softwares to be replaced by new versions?would an  online upgradation take care of it?

---

### Post by drs305 on 2009-06-21
> **abhinav.p said:**
> but would'nt it be sometimes necessary to have old application softwares to be replaced by new versions?would an  online upgradation take care of it?

Yes, the newer versions would be installed by either method. 

With an online upgrade, any application registered with APT (normal installations) would be upgraded if a newer version was available. 

With a clean install, any default installation would be the latest listed in the repositories and any package you added after the installation would be the latest version available in the repositories.

---

