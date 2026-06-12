---
title: "[SOLVED] Is it possible to convert .tar.gz to .deb ?"
date: 2008-08-30
forum: General Help
---

### Post by gjoellee on 2008-08-30
Hey there! I have been using google to find a way to convert tarballs to .deb

 I gave up and now I asking you instead :)
Is there a way to convert .tar.gz, .tar.bz2 to .deb ?

---

### Post by spiderbatdad on 2008-08-30
checkinstall

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

In fact, it is wise to do so, when possible. It makes removal much easier, as checkinstall adds the package to synaptic.

To really get into it...check out packaging:[https://help.ubuntu.com/ubuntu/packagingguide/C/](https://help.ubuntu.com/ubuntu/packagingguide/C/)

---

### Post by bodhi.zazen on 2008-08-30
Assuming the tar ball is source code, you can use checkinstall. Checkistall is a bit of a hack, however, and it does not do a good enough job to submit to a repository.

you would 

./configure
make
sudo checkinstall -D

If you are a developer, take a look at any of the various on'line guides :

[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

---

### Post by Shadow12313 on 2009-10-12
Just use alien

sudo apt-get install alien
sudo alien -d tarball.tar.gz

---

### Post by ascariz on 2010-08-11
here the tutorial convert source to deb use alien
[http://ascarizdiscovery.blogspot.com/2010/07/convert-source-tarbz2-to-ubuntu-deb.html](http://ascarizdiscovery.blogspot.com/2010/07/convert-source-tarbz2-to-ubuntu-deb.html)

---

### Post by bodhi.zazen on 2010-08-11
> **Shadow12313 said:**
> Just use alien

sudo apt-get install alien
sudo alien -d tarball.tar.gz

> **ascariz said:**
> here the tutorial convert source to deb use alien
[http://ascarizdiscovery.blogspot.com/2010/07/convert-source-tarbz2-to-ubuntu-deb.html](http://ascarizdiscovery.blogspot.com/2010/07/convert-source-tarbz2-to-ubuntu-deb.html)

Although alien may seem nice, be aware that it does not always work as advertised (try converting a .deb to a .rpm and sometimes you will have problems with the debina pre or post install scripts).

In addition, although uncommon, packages made with alien can over write system libs without warning, and cause irreversible damage to the system.

IMHO, you are far safer either installing from source (.configure -> make -> make install) or using checkinstall.

When installing from source, use --prefix=/usr/local (an option for configure) when at all possible (it usually is). This places the files in /usr/local rather then the system files.

---

### Post by specialk1st on 2010-11-06
Do a Google search for: "Ubucompilator"

It's an awesome program with a GUI interface.

Also check out this link for a video demo:  [http://www.ubuntugeek.com/ubucompilator-easy-way-of-creating-deb-packages-from-source-files.html](http://www.ubuntugeek.com/ubucompilator-easy-way-of-creating-deb-packages-from-source-files.html)

---

