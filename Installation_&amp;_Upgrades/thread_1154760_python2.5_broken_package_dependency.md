---
title: "python2.5 broken package dependency"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by i0exception on 2009-05-10
Well I needed python-gobject >= 2.15 So i downloaded the .deb file and tried installing. Dependency checker led me to install python2.5-minimal=2.5.2-11ubuntu1. After I tried installing the .deb file for this, I keep getting an error that the system has broken packages. If I run sudo apt-get -f install, it tells me that I have to remove a lot of major packages. Synaptic says that the package python2.5 is broken. Apt-get gives an error :
```

python2.5: Depends: python2.5-minimal (= 2.5.2-2ubuntu4) but 2.5.2-11.1ubuntu1 is to be installed

```

How do i set back the system to how it was before installing python2.5-minimal=2.5.2-11ubuntu1 ?

Thanks.

---

### Post by i0exception on 2009-05-10
Nevermind, sudo aptitude install python2.5-minimal solved the problem

---

