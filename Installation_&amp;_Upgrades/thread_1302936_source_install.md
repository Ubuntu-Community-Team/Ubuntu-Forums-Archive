---
title: "source install"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by Sam5472 on 2009-10-27
I basically know how to compile from source, but in terms of dependencies I can only find them by running ./configure over and over and over again.  Is there a way to determine all of the dependencies needed from a source.tar.gz file without having to run ./configure.

---

### Post by zvacet on 2009-10-28
From directory where you downloaded source ( home I believe) type

```
sudo apt-get build-dep package_name
```

---

### Post by Sam5472 on 2009-10-28
Yes this works fine for source packages downloaded from a debian repository, but will it work on source packages not from a debian repository.

---

### Post by zvacet on 2009-10-29
Other option is to install auto-apt


```
sudo apt-get install auto-apt
sudo auto-apt update
sudo auto-apt updatedb && sudo auto-apt update-local
```

Then run command

```
auto-apt run ./configure
```

Taken from [here.]("http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html#s-auto-apt")

---

### Post by Sam5472 on 2009-10-29
Thank you.  This should work perfectly.

---

