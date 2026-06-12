---
title: "Update Manager ?"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by Jhf4473 on 2009-03-28
I updated compiz
now in update manager this -> compiz-fusion-plugins-extra <- was not able to be installed -> I get this -> 

Upgrade manager error
E: /var/cache/apt/archives/compiz-fusion-plugins-extra_0.7.6-0ubuntu1~ppa1_i386.deb: trying to overwrite `/usr/lib/compiz/libwallpaper.so', which is also in package compiz-fusion-plugins-unofficial

My question is how to get - compiz-fusion-plugins-extra - out of the update manager so it will quit trying to install the plugins

---

### Post by Partyboi2 on 2009-04-04
You could try to force the overwrite. Open a terminal (Applications>Accessories>Terminal)
and type
```
cd /var/cache/apt/archives
``````
sudo dpkg --force-overwrite --install compiz-fusion-plugins-extra_0.7.6-0ubuntu1~ppa1_i386.deb
```

---

