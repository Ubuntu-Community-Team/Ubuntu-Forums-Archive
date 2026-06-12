---
title: "Java 1.6_16?"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by mebigfatguy on 2009-09-06
Greetings,

  Is their a way to convince synaptic that the java version I want is 1.6_16 as opposed to the 1.6_14 that it thinks i should have? 1.6_14 is a disaster of a release, having a problem where break points aren't hit. 

[https://bugs.eclipse.org/bugs/show_bug.cgi?id=279137](https://bugs.eclipse.org/bugs/show_bug.cgi?id=279137)

 Or do i need to just install it manually.

---

### Post by mebigfatguy on 2009-09-06
Oooh, found this

adding

-XX:+UseParallelGC


fixes the 1.6_14 problem, so it's not so urgent.

---

### Post by jamesstansell on 2009-09-06
If you add the jaunty-proposed (or hardy-proposed if you still use 8.04) repository to synaptic you should be able to install 6u16.

If you run 8.10 or the 9.10 alpha you should be able to download 6u16-9.04 files from the repository and install them with dpkg -i.

---

