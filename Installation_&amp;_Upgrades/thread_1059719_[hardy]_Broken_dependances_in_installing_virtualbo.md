---
title: "[hardy] Broken dependances in installing virtualbox-2.1"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by pistacchio on 2009-02-04
Hi to all,
i'm trying to install virtualbox-2.1, but this is what i get. i have all the updates available and i've already tried with sudo apt-get install -f

```

gu@memole:~$ sudo apt-get install virtualbox-2.1
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
  virtualbox-2.1: Depends: libqt4-network (>= 4.4.3) but 4.4.0-1ubuntu5~hardy1 is to be installed
                  Depends: libqtcore4 (>= 4.4.3) but 4.4.0-1ubuntu5~hardy1 is to be installed
                  Depends: libqtgui4 (>= 4.4.3) but 4.4.0-1ubuntu5~hardy1 is to be installed
E: Broken packages

```

Any help?
thanks in advance
Gustavo

UPDATE:
my fault, followinga a guide, i ended up adding to the source list the ibex url.

---

