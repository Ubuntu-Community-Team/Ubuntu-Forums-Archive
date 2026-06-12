---
title: "a list of new installed programs"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by KhaaL on 2009-02-25
I'm looking to complement a backup script i'm writing with which programs i have installed. I got the tip to use 

dpkg –get-selections | grep -v deinstall > installed-apps

However there is one problem with that line... it makes a list of *everything* installed, even the libs for the system! I'm only interested in what programs i've installed *after*. How can I do that?

---

### Post by KhaaL on 2009-02-26
bumping...

---

