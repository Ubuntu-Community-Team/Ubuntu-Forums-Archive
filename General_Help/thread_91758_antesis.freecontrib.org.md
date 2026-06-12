---
title: "antesis.freecontrib.org"
date: 2005-11-17
forum: General Help
---

### Post by monkblah on 2005-11-17
I have the following lines in my /etc/apt/sources.list file:

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free


It used to work, but now I get error messages about antesis.freecontrib.org whenever I use apt. What happened to the server & what should I do?

---

### Post by Chickenmonger on 2005-11-18
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

According to the wiki, the primary mirror is down. Use the secondary one instead:

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

---

### Post by monkblah on 2005-11-18
Thanks, chickenmonger!

---

### Post by rwabel on 2005-11-20
none of them are working right now

---

