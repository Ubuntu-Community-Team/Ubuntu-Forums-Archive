---
title: "Cannot install libssl-dev on Ubuntu 8.04.1"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by kcarter80 on 2009-04-24
I don't understand the error.

Help! =)

root@foo:/home# apt-get install libssl-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libssl-dev: Depends: libssl0.9.8 (= 0.9.8g-4ubuntu3) but 0.9.8g-4ubuntu3.3 is to be installed
E: Broken packages

---

### Post by kcarter80 on 2009-04-24
Anyone?

---

