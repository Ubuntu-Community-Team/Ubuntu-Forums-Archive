---
title: "[SOLVED] Repository for recent kde librairies"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by Creat on 2008-12-20
Hi,

  Can someone indicate me which repository I should add to my source list to be able to get this package ([https://launchpad.net/ubuntu/intrepid/i386/kdelibs5-dev/4:4.1.3-0ubuntu1~intrepid4](https://launchpad.net/ubuntu/intrepid/i386/kdelibs5-dev/4:4.1.3-0ubuntu1~intrepid4)) and its dependencies?

   Thanks for your help!
     - Creat

---

### Post by Partyboi2 on 2008-12-20
For the kdelibs5-dev package if you are using intrepid you can enable backports under "updates" in Software Sources.

---

### Post by Creat on 2008-12-21
Actually I already have backports repositories activated. Currently the version I can get is 4.1.2 but I'd like to get 4.1.3.

---

### Post by Partyboi2 on 2008-12-21
according to [[COLOR=Blue]this[/COLOR]]("http://packages.ubuntu.com/search?keywords=kdelibs5-dev&searchon=names&suite=all&section=all") its in the backports repo. Have you tried
```
sudo apt-get update
sudo apt-get upgrade
```
Another thing to have a look at is open up Synaptic and search for kdelibs5-dev highlight it and select "Package" then "force version" and choose the 4.1.3 verion if you are able to.

---

### Post by Creat on 2008-12-22
Thanks for your help. It's just that the mirror I was using wasn't up to date.

---

