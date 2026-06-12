---
title: "edubuntu package manager"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by joshstl79 on 2009-03-23
Hi folks.  I'm pretty new, obviously, and i was hoping maybe somebody could help me out.  Well, i was trying to get Google Earth working, so i did the responsible thing and read some forum posts and tried what was suggested...  anyway, i changed something in update manager, and now i've got some kind of update manager problem.  See attached to see the error. 

I've tried to pull up Software sources, but i get basically the same error.  

Also, when i pull up the medibuntu list, heres what it has in the file:

## Medibuntu - Ubuntu 8.10 "intrepid ibex"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free

Anyway, i'd really not like to have to do a fresh install, I basically have everything setup correctly - well, of course except this.  Thanks in advance for your help.

---

### Post by Partyboi2 on 2009-03-25
Open a terminal and remove the /etc/apt/sources.list.d/medibuntu.list
```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```then 
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```then```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

