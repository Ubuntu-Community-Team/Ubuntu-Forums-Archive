---
title: "silly apt-get. trying to install X from scratch."
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by gnomes on 2005-12-22
no matter what i try and install actually, apt-get won't resolve dependancies. for example it will always say

"Depends: [package] but it is not going to be installed"

i seem to recall it should resolve dependancies?

---

### Post by az on 2005-12-22
Have you mixed repositories?  (like debian and ubuntu repositories)

Apt will not so something if the dependancies are not compatible.  It may have to remove packages for it to do what you want.

---

### Post by gnomes on 2005-12-22
[QUOTE=azz]Have you mixed repositories?  (like debian and ubuntu repositories)

Apt will not so something if the dependancies are not compatible.  It may have to remove packages for it to do what you want.[/QUOTE]
actually, i believe i do have mixed repositories. and it is has also been awhile, and im not sure how to fix that anymore.

---

### Post by az on 2005-12-23
Comment out all your apt sources and put in breezy ones.  Make sure you have all the repositories you need (universe, multiverse, security-updates, etc...)

and do and update and dist-upgrade.  See what happens.

sudo apt-get -s dist-upgrade

(-s for no action, just simulate to see what happens)

---

