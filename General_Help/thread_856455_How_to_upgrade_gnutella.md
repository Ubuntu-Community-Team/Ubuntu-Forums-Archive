---
title: "How to upgrade gnutella"
date: 2008-07-11
forum: General Help
---

### Post by Pacopag on 2008-07-11
Hi.  When I open gnutella it tells me that my version is old and that I should get the new one.  I went to the website and downloaded it, but I don't know what to do with it.  I downloaded the tar.bz2 at [http://gtk-gnutella.sourceforge.net/en/?page=news](http://gtk-gnutella.sourceforge.net/en/?page=news) and unzipped it, but I don't know what to do with the files.

---

### Post by dracayr on 2008-07-11
open a terminal and cd into the unzipped folder:

```
cd *foldername*
```
then, if the folder contains a autogen.sh file or a configure file, execute it:
```
./autogen.sh
or
./configure
```
compile and install
```
make
sudo make install
```

dracayr

---

### Post by Pacopag on 2008-07-11
Great. Thanks.  Will that upgrade my old one, or will it install a new one? Should I uninstall my old one first?

---

### Post by Pacopag on 2008-07-11
Thanks again.  But it didn't work.  It gave me all kinds of errors.  I installed the packages that it recommended, but that didn't work either.  If I just wait a while, will I be able to get the new one using Synaptic?

---

### Post by dracayr on 2008-07-11
I don't know. I don't even know what gnutella is. Just try if you can get it via synaptic/apt-get

dracayr

---

### Post by Pacopag on 2008-07-11
ok thanks

---

