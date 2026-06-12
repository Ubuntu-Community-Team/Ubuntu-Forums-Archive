---
title: "problem compiling KOffice 1.4.2"
date: 2005-11-20
forum: General Help
---

### Post by TeraDyne on 2005-11-20
Probably something simple I'm missing, but I'm trying to compile KOffice 1.4.2. Everything's fine until I get to this part:

```
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

```

What do I need to do to fix this? I'm running KDE 3.5 RC1, if it helps anything.

---

### Post by abandoned_hussam on 2005-11-21
you can get koffice 1.4.2 for breezy here [http://kubuntu.org/packages/koffice142/]("http://kubuntu.org/packages/koffice142/")
but if you want to compile, you need kdelibs-dev and build-essential

you might also want to "apt-get build-dep koffice" if you have deb-src enabled in apt.

---

### Post by TeraDyne on 2005-11-21
Thanks. It was kdelibs-dev that I needed. I perfer to compile from downloaded source so, if something goes wrong, I know exactly what borked up. 

Sometimes, apt-get just isn't as fulfilling as doing things yourself. :)

Thanks again.

---

