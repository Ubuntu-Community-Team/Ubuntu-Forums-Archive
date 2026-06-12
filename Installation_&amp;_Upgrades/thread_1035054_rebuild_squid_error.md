---
title: "rebuild squid error"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by maniaxx on 2009-01-09
hi i'm new here.
can anyone help me rebuild squid,

after fress install from live-cd
$ sudo su
$ apt-get update
$ apt-get install devscripts build-essential
$ apt-get source squid
$ apt-get build-dep squid
$ cd squid-2.7.STABLE3
$ nano debian/rules
  adding some rules --enable blah3
$ ./configure
$ debuild -us -uc -b
  then i got this error :

checking build system type... config.sub: missing argument
Try `config.sub --help' for more information.
configure: error: /bin/bash cfgaux/config.sub failed
make: *** [config.status] Error 1
dpkg-buildpackage: failure: debian/rules build gave error exit status 2
debuild: fatal error at line 1329:
dpkg-buildpackage -rfakeroot -D -us -uc -b failed

---

### Post by Partyboi2 on 2009-01-10
Why not install squid using apt-get?
```
sudo apt-get install squid
```

---

### Post by Sociologist on 2011-05-10
> **Partyboi2 said:**
> Why not install squid using apt-get?
```
sudo apt-get install squid
```

Need to add ssl support, for example...

---

