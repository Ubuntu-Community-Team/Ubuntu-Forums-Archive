---
title: "Installing package problem??"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by Alec Sacul on 2009-02-12
Ok so when i download a package i get this error message when im trying to install it. it says: Error: Dependency is not satisfiable: sun-java6-jre/icedtea-java7-jre/sun-java6-jdk/icedtea-java7-jdk/
i have already searched for this stuff under synaptic and stuff and i cant find it. please help me i already have java installed
and when i put it in terminal to get them nothing happens it says it can't find it
help please and thankyou

---

### Post by taurus on 2009-02-12
If you need to install java, go into synaptic and look for sun-java6-jre.  Otherwise, install it from a terminal with

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
And what program are you trying to install anyway?

---

### Post by Alec Sacul on 2009-02-13
im trying to install limewire but instead of installing it it says it can't find it
E: couldn't find package sun-java6-bin im on ubuntu 7.10 or gutsy gibson

---

