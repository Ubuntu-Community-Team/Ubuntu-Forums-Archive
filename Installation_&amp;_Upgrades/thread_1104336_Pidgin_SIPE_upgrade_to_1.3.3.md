---
title: "Pidgin SIPE upgrade to 1.3.3"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by simonbrain on 2009-03-23
I am trying to upgrade to the latest SIPE version. I have downloaded and done ./configure, make and make install but current version 1.2-1 remains. Has anyone carried out this upgrade on Ubuntu?

Many thanks Simon

---

### Post by aquino.dong on 2009-04-06
Hi There, i did the same thing in Jaunty. what i did is apt-get remove pidgin-sipe, the ./configure --prefix=/usr; make; sudo make install, then i can use "Microsoft/LCS" in pidgin.

hope it can help.

---

### Post by g33k on 2009-04-08
Attempting to build pidgin-sipe 1.3 from source and get this:

```
checking for libpurple... configure: error: Package requirements (pidgin >= 2.0.0) were not met:

No package 'pidgin' found
```

Current pidgin version is 2.5.5.  

I ran this:

```
./configure --prefix=/usr
```

---

### Post by rgsteele on 2009-04-28
I too was looking to install the latest version of pidgin-sipe. I discovered that the developer, Anibal Avelar, has a PPA which provides the latest version of the plugin:

[https://launchpad.net/~aavelar/+archive/ppa](https://launchpad.net/~aavelar/+archive/ppa)

---

