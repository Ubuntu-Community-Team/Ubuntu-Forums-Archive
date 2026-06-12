---
title: "installing skype"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by neodudecurt on 2009-06-04
hello again, (three times in one day, I'm going to end up setting a record)

I tried downloading skype from the skype site, and I got the one for Ubuntu, but when I try to install the package it says.

Error: Dependency is not satisfiable: libqt4-core (>= 4.2.1)

I understand that this means that the package in question, (libqt4-core) needs to be a higher version than 4.2.1, but even when I looked through the synoptic package manager, and installed the most recent edition of that package, skype refuses to install. Could this be a problem with my sudo apt-get update command not working, and whether it is or not, is there some way I can fix it?

---

### Post by dE_logics on 2009-06-04
Are you on x64 and trying to do a force install?

If this is so, you have manually download that 32bit package for qt and force install it...do this for all dependencies, then it should work.

---

### Post by neodudecurt on 2009-06-04
well, I recently discovered, after doing some investigation that I am using ubuntu 9.04, whereas the skype program currently is only compatible with 8.04. It is going to be a very long day...

---

### Post by merlinus on 2009-06-04
There is definitely a 64-bit skype, but it is not listed with a link on their website.

The filename is:

skype_ubuntu-2.0.0.72-1_amd64

---

