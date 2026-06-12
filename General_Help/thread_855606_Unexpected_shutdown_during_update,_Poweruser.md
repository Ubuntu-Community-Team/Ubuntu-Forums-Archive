---
title: "Unexpected shutdown during update, Poweruser?"
date: 2008-07-10
forum: General Help
---

### Post by mxdxj.86 on 2008-07-10
Hi,
There was a power cut in my area as I was updating my ubuntu, doh! I restarted and the "No entry sign" said i needed to run the package manager to find out the problem (It basically said I had some unmet dependencies) ... I started the package manager and a popup appeared saying

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So i entered a terminal and typed in dpkg... and i get told it requires superuser privileges.

I'm running ubuntu 8.04 on a laptop with an AMD Sempron 2800+ 512MB of DDR2, and its practically a fresh install (I was doing a system update to get up to date with what was missed) Hope someone can give me a hand

Thanks guys

MJ

---

### Post by f37u5g0d on 2008-07-10
When you need super user privileges you can easily get them by typing sudo before the command you want to run.  So in the terminal type" sudo dpkg -configure -a "  It will automagically fix it's problems for you (ubuntu is great like that)

---

### Post by dracayr on 2008-07-10
> **f37u5g0d said:**
> It will automagically fix it's problems for you (ubuntu is great like that)


actually, exactly that is not ubuntu, but the debian part of ubuntu...

dracayr

---

### Post by mxdxj.86 on 2008-07-14
Thanks guys, great help :-) Got it all working last night and my wireless card too which was a great challenge but very worth it. Thank god I'm not going to have to make the transition to Vista

M

---

