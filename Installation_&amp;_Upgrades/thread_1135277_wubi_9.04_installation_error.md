---
title: "wubi 9.04 installation error"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by amocanu on 2009-04-24
I tried to install Ubuntu 9.04 (official release) from inside windows using Wubi from the cd, and it always throws the following error : 
"writelines() argument must be a sequence of strings" when i'ts suppose to start the installation

Is there any way to avoid this error ?

---

### Post by eeVoskos on 2009-04-24
I get the same error while trying to install on a VAIO CS11 (Vista x86 SP1) from a Ubuntu 9.04 image + downloaded wubi installer.

---

### Post by eeVoskos on 2009-04-24
Well, it is now a known bug as you see [here]("https://bugs.launchpad.net/wubi/+bug/365642"). I followed the solution proposed [here]("https://bugs.launchpad.net/wubi/+bug/365642/comments/7"), changing the default current format (see: regional settings) to English and it worked! I hope it works for you as well.

---

