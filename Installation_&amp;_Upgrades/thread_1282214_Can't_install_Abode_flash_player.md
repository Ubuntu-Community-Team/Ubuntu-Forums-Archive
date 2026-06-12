---
title: "Can't install Abode flash player"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by M.B.williams on 2009-10-04
:confused:Hi, have been trying to install abode flash player 10 on Ubuntu 9.04
When i have tried to install comes up with error
-Error dependency is not satisfiable :libnspr4-dev
What does this mean? Can anybody help me.

---

### Post by dustsnow on 2009-10-04
It means the adobe-flashplugin need the libnspr4-dev that doesn't be found in your linux. simply install the libnspr4-dev in synaptic 
or command line:sudo apt-get install libnspr4-dev

---

### Post by hal10000 on 2009-10-04
Why don't you use your package manager to install it? Or just type on the command-line:
```
sudo apt-get install flashplugin-nonfree

```

---

### Post by M.B.williams on 2009-10-04
Hi, i downloaded updates for Ubuntu and then tried to load flash player, work ok this time.
Thanks for Help.:P

---

