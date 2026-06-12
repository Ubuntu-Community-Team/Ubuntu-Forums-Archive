---
title: "Serious problems with Kubuntu"
date: 2005-11-03
forum: General Help
---

### Post by joflow on 2005-11-03
Hi,

I just switched from Ubuntu to Kubuntu...fresh install, formatted linux partition.  So far I've been having nothing but problems.

I've been trying to sudo kate /etc/apt/source.list and I get the following error:

Error: "/var/tmp/kdecache-joflow" is owned by uid 1000 instead of uid 0.
Creating link /root/.kde/cache-ubuntu.
Created link from "/root/.kde/cache-ubuntu" to "/var/tmp/kdecache-root"
kate: ERROR: Communication problem with kate, it probably crashed.

I can't ungrade to 686 or run SuperKaramba or install almost anything and I think this is because I haven't been able to enable the universe repo.

I also can't run Adept.

---

### Post by aysiu on 2005-11-03
I don't know about Adept, but you should do ```
sudo kwrite
``` not ```
sudo kate
``` Actually, to be totally "proper" about it, you should do ```
kdesu kwrite
```

---

### Post by joflow on 2005-11-03
Thanks.  That allowed me to add the universe repo.  But I'm still having dependency problems when attempting to install anything.

---

### Post by joflow on 2005-11-03
Adept is now running.  I was able to install 686 through adept.  SuperKaramba works.  Everything works except I can't get the "GTK styles and fonts" in LookNFeel to run.

---

