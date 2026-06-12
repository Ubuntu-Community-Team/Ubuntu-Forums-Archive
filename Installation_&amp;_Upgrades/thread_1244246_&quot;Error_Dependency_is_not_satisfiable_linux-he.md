---
title: "&quot;Error: Dependency is not satisfiable: linux-headers&quot;"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by jomex on 2009-08-19
i was installing the new kernel from:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc6/)

when i want to install the headers i get:
> Error: Dependency is not satisfiable: linux-headers-2.6.31-020631rc6

> sudo apt-get install linux-headers-$(uname -r)

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.31-020631rc6-generic


what's wrong?

system is Ubuntu 9.04 Alt AMD64

---

### Post by dstew on 2009-08-19
Are the deb-src repositories in the /etc/apt/sources.list file? If not, you can activate them using the System --> Administration --> Software Sources interface. These are the source code repositories.

---

### Post by Cheesemill on 2009-08-19
You're installing a new kernel that isn't in the standard repos.
 
It follows that the standard repos won't have the linux-headers package for the kernel you've installed, you'll have to search elsewhere for it (PPA maybe).
 
 
*Edit - You could try **apt-get install linux-headers-2.6.31** but I doubt it will work.*

---

### Post by jomex on 2009-08-21
given the link used above:
[http://kernel.ubuntu.com/~kernel-ppa...e/v2.6.31-rc6/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.31-rc6/")

how would i enter it in sources? it seems a source link always needs the form of dist/UBUNTUVERSION/CPU/...

---

