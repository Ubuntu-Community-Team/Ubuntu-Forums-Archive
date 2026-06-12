---
title: "gdebi without prompt"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by gamont on 2009-05-17
I want to install a .deb using the command line prog gdebi inside a script. 
But it prompt a y/n to confirm the installation.

There is a option 'non-interactive' but the warning scared me.

Is there an option like -y in apt-get for gdebi ?

And gdeb (in repository) is the same as gdebi ?

thanks

---

### Post by kpkeerthi on 2009-05-17
Its easier with **dpkg**

```
dpkg -i <my-package>.deb
```

---

### Post by gamont on 2009-05-17
thanks !

---

