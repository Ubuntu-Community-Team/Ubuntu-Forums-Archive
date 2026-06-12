---
title: "Executing software without installing."
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-04-08
Suppose I have compiled a software is it necessary to 'make install' to make them run?...I mean can I run them directly from the place where the binaries got made?

---

### Post by linux_lover69 on 2009-04-08
Did you compile it, or did it came compiled

I think you have to install it. unless it came precompiled

---

### Post by LoloftheRings on 2009-04-08
Maybe you can run from the compiling directory without installing. Try searching some documentation about the ./configure file.

---

### Post by dE_logics on 2009-04-08
I know how to install and all...just asking.

So it depends on the source?

---

### Post by Mark Phelps on 2009-04-08
The typical sequence is ...
1) configure
2) make
3) make install

The third typically builds the executables and copies them to the appropriate directories so that they are then seen using the default PATH.  It also typically adds an entry to an application menu with an icon so you can launch it.

So, I suppose you could edit the menu entry to point to the directory where the executable got originally built.

---

### Post by dE_logics on 2009-04-09
Ok...thanks I'll play around with that.

---

