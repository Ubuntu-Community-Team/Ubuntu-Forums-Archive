---
title: "Compiz installation on 9.04"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by captpicard12 on 2009-04-28
Hey, would somebody mind helping me out?  I just upgraded to jaunty jackalope tonight, and its great except i need to figure out how to install compiz.  What i typed was [COLOR="SeaGreen"]sudo apt-get install compiz compizconfig-settings-manager[/COLOR], and then my password, and what it gave me back was [COLOR="MediumTurquoise"]"Reading package lists...done
Building dependency tree
Reading state information..done
compiz is already the newest version.
E: Couldn't find package compizconfig-settings-manager"
[/COLOR]
What i gathered from this was that I had already installed compiz at one point, but not the settings manager.  When i tried typing in "ccsm", it said 
"The program 'ccsm' is currently not installed.  You can install it by typing "sudo apt-get install compizconfig-settings-manager bash: ccsm: command not found.
Please help!

---

### Post by captpicard12 on 2009-04-28
Sorry, correction, it doesn't seem to be able to find any packages at all, not just compiz!!!
whatever apps i install it says E: couldn't find package whatever, and that's all i can get out of it!  please help, as i can't do much at all with a computer like this!  I had to connect it to the ethernet to work, because even it's wireless card needs a driver that it can't find the package for!!!!!

---

### Post by lovinglinux on 2009-04-28
> **captpicard12 said:**
> Sorry, correction, it doesn't seem to be able to find any packages at all, not just compiz!!!
whatever apps i install it says E: couldn't find package whatever, and that's all i can get out of it!  please help, as i can't do much at all with a computer like this!  I had to connect it to the ethernet to work, because even it's wireless card needs a driver that it can't find the package for!!!!!

Yes, it can. The message below means it found compiz, but since it is the newest version, it won't install it again. The other message means you haven't enabled the proper repository in the "System >>> Software Sources", so it can't find it. CCSM is not in the repository supported by Canonical, but in the "Universe", which is supported by the community.

> **captpicard12 said:**
> [COLOR="MediumTurquoise"]"Reading package lists...done
Building dependency tree
Reading state information..done
compiz is already the newest version.
E: Couldn't find package compizconfig-settings-manager"
[/COLOR]

---

### Post by captpicard12 on 2009-04-29
Thanks, I got cafuego ubuntu working.

---

