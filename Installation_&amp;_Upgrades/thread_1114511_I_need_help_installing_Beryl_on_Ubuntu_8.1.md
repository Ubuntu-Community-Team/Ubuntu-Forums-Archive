---
title: "I need help installing Beryl on Ubuntu 8.1"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by Talynz on 2009-04-02
Ok, I just downloaded Ubuntu 2 days ago so I'm the ultimate NOOB when it comes to doing stuff on Ubuntu. So anyway I want to Install Beryl on my computer and I dont know how to?? I have no clue what to do. So If some one could please give me a detailed description on what to do I would dance at your next wedding! And if this helps clarify something I have a nVidia 8600 graphics card and Ubuntu 8.1
Please Help me guys! Thanks!!

---

### Post by avacomputers on 2009-04-02
Beryl is no longer a stand alone project. It re-merged with Compiz. Install compiz and you will have all effects.

---

### Post by upchucky on 2009-04-02
first make sure u have 3d graphics enabled for your card, 8.10 has issues but it can be done.

open a terminal, applications-->accessories,-->terminal and type this ```
glxgears
```

if after a few seconds u see a set of gears spinning and get a report of high frame rates, say about 11,000fps then 3d is functioning fine.

if no gears and/or very slow frame rates, 3d has trouble.

then you need to find info on how to get your nvidia working right.

once you have nvidia working, then search for instructions on compiz, it is the replacement for beryl and does more things better than beryl.

---

### Post by Sef on 2009-04-02
Compiz is installed by default.   To use it you need to do the following:

1) System > Administration > Hardware drivers > activate Nvidia's restricted drivers

2) Applications > Add/Remove > Show: All Available Applications > Search: CCSM > click on the box next to CCSM > apply changes > apply > close.

---

### Post by Talynz on 2009-04-02
> **Sef said:**
> Compiz is installed by default.   To use it you need to do the following:

1) System > Administration > Hardware drivers > activate Nvidia's restricted drivers

2) Applications > Add/Remove > Show: All Available Applications > Search: CCSM > click on the box next to CCSM > apply changes > apply > close.



Ok I did all that and at the last step I hit Apply and this message came up. 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What does that mean?? It came up when I tried to install Limewire too. please help. =)

---

### Post by Peasantoid on 2009-04-02
> **Talynz said:**
> Ok I did all that and at the last step I hit Apply and this message came up. 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What does that mean?? It came up when I tried to install Limewire too. please help. =)
You do what it says, of course! :) Just run "sudo dpkg --configure -a".

---

### Post by Talynz on 2009-04-02
Oh ok I got it working I think. But how do you use the cube? What buttons do you push to make the cube come up?

---

