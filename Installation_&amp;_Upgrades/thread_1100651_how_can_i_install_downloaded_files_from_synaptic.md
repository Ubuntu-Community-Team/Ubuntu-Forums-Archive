---
title: "how can i install downloaded files from synaptic"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by raspotin on 2009-03-19
hi guys

iam ubuntu 8.10 user

i've downloaded larfe number of packages about 3.2 g
 
and installed most of them 

but i've formated my pervious ubuntu and re installed it

how can i install that pervious packages from synaptic without redownloading cuz  i already have them on the hard disk

---

### Post by blackened on 2009-03-19
Unless you backed up the files located in /var/cache/apt/archives before you reinstalled, then you'll have to download them all again.

---

### Post by raspotin on 2009-03-19
i've backup them 

and i put them again in /var/cache/apt/archives
i've tried to install some of them by synaptic
hoping it will read them as downloaded files
but invain

---

### Post by blackened on 2009-03-19
Have you tried installing them with dpkg or apt-get install --no-download? Installing them en masse is gonna be tricky using either of those methods though.

---

