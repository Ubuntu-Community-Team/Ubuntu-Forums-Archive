---
title: "compilling eye of gnome"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by maticmatija on 2009-10-02
I can't compile the Eye of gnome. When I try ./configure I get error that gnome-desktop is missing. I don't want to install that since it takes a lot of space and if you install the Eog from repositories this isn't necessary. How can I override this problem? I'm using Ubuntu 8.10. 

Thanks,
Matic Matija

---

### Post by Partyboi2 on 2009-10-03
Generally when you are compiling you need to install the dev packages of the missing packages.
So for gnome-desktop you would probably need to install 'libgnome-desktop-dev'
```
sudo apt-get install libgnome-desktop-dev
```

Eye of gnome is also in the Ubuntu repositories and can be installed with
```
sudo apt-get install eog
```

Which is a lot easier then compiling it from source. :)

---

### Post by ad_267 on 2009-10-03
Another useful command is "apt-get build-dep" which will install all of the build dependencies of a package.

I'd suggest having a look at viewnior, which has all of the features of eog but without any gnome dependencies, and is more lightweight.

---

