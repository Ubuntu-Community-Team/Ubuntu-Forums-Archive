---
title: "Empathy Installing Problem"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by psychok7 on 2009-03-18
Hi there im trying to build empathy 2.26 from source but when i ran ./autogen.sh it gives me this : 

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

can anyone guide me trough this problem or offer me another solution?

---

### Post by Partyboi2 on 2009-03-19
Try
```
sudo apt-get build-dep empathy
``` then
```
./autogen.sh 
```

Another possible way of installing it is to download the deb package from [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/jaunty/empathy")

---

### Post by psychok7 on 2009-03-19
> **Partyboi2 said:**
> Try
```
sudo apt-get build-dep empathy
``` then
```
./autogen.sh 
```

Another possible way of installing it is to download the deb package from [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/jaunty/empathy")
the first doesnt help me still, and the second one says i have a dependency that is not satisfiable, but i have it installed

---

