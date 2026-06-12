---
title: "Can't downgrade GIMP 2.7 to 2.6!"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by rafaellaguna on 2009-09-07
I've tested the new version, but now that I can't continue using it (it's under heavy development), when trying to downgrade to Canonical's repos, GIMP doesn't work anymore. It says he needs libgegl-0.0.0 but it's already installed. I'm considering re-format my partition and reinstalling Ubuntu again, because there's no thing I can do (UI've cleaned prefs, etc folder, everything).

Thanks in advance. And be careful you all, don't install this beta now!

---

### Post by rafaellaguna on 2009-09-07
Removed mathews ppa from sources, forced in Synaptic to use this:


[LIST]
[*]libbabl: 1.0.22-1 (jaunty) (not no or jj version; CTRL+E)
[*]libgegl-0.0.0: 0.0.22-ubuntu3 (jaunty)
[*]gimp, libgimp and gimp-data: 2.6.7 (downloaded DEBs from GetDeb)
[/LIST]

It seems it was an incoherence between package, but all were "compatible" during installation, so there was no error until execute.

Thank you anyway (arf, after a week working hard for this).

---

### Post by jayrajkharvadi on 2010-12-04
I am facing the same issue.
Were u able to solve and get back to the stable gimp????

Thanks in advance. :)

---

### Post by jayrajkharvadi on 2010-12-04
allrighty brother. got it to work.
By ur method using Ctrl + E in Synaptic. :)
thanks.

---

