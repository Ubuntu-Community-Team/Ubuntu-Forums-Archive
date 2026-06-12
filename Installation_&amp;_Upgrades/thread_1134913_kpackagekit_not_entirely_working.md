---
title: "kpackagekit not entirely working"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Mr_Bumpy on 2009-04-24
I just installed Kubuntu 9.04 (Jaunty) and while some packages seem to install fine, others just fail silently.  I've had two packages fail so far: linux-rt and kubuntu-restricted-extras.  What happens is I mark the package for installation, then click "Apply", and okay the confirmation, and then it says the package was installed in something like 250 milliseconds.  However, the package shows up as not installed.  I can repeat the process over and over, but it never installs the package.  Also, each of the problem packages has dependencies, but kpackagekit never asks about satisfying them.

I've had to use the command line (sudo apt-get install) to install these packages.  I'm a little scared to use kpackagekit any more, because I don't want it to screw something up.

---

### Post by myrddinemrys on 2009-05-05
I'm getting the same problem with kubuntu-restricted-extras on both of my two new Kubuntu Jaunty installs.

Also, it never asks for my password prior to (not) installing this package.

---

### Post by Zorael on 2009-05-06
I remember reading something somewhere about there being a known bug in kpackagekit that made it unable to resolve dependencies, making it fail silently. So yes, for the time being (until a fix is released), I suggest you do it the terminal way when kpackagekit won't do the trick.
```
$ sudo aptitude install *<package name>*
```

---

