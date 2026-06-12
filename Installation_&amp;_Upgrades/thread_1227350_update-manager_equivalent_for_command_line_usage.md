---
title: "update-manager equivalent for command line usage"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by rsgrimes on 2009-07-30
The update-manager is great for my desktop machine - really makes keeping the system up-to-date so easy.  But I have a second Ubuntu machine set up as a server that to which I only have ssh access.  What is the best equivalent command that I can run from a ssh shell?

Thanks,
-Bob

---

### Post by birdwin on 2009-07-30
'sudo apt-get update'
'sudo apt-get upgrade'

is the easiest way (use 'apt-get dist-upgrade' instead to upgrade your kernel in between Ubuntu releases; 'apt-get upgrade' will keep the kernel upgrades back). 'sudo aptitude' provides more fine-grained control over upgrades, but isn't as easy.

---

### Post by slakkie on 2009-07-31
For upgrading to a newer release you can use do-release-upgrade. You need to install update-manager-core package for that: sudo aptitude install update-manager-core

---

### Post by rsgrimes on 2009-08-04
> **birdwin said:**
> 'sudo apt-get update'
'sudo apt-get upgrade'

So, the first command updates package status from the Sources, and the second upgrades locally installed packages, right?

Thanks!
-Bob

---

