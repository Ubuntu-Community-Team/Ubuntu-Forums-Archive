---
title: "take lxde from cache"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by navaneethan on 2009-09-17
i have installed ubuntu hardy,and i have lxde it is nice

i'd like to take backup the installed lxde modules from my system,because i can use those modules can be installed when i am going to reinstall my ubuntu

i need to find only lxde files(all dependencies) to tkae back-up


:guitar:NavTux loves Linux:guitar:

---

### Post by shredder12 on 2009-09-17
One of the way is to use this command

```
sudo apt-cache depends lxde
```

But the dependency list here is quite big..
some of the listed packages are the libraries that you will already have installed..

so its better to search your cache folder to look for lxde files..
```
ls /var/cache/apt/archives/ | grep lxde 
```

this might be not be  very effective..
but will probably list all the useful packages..

---

