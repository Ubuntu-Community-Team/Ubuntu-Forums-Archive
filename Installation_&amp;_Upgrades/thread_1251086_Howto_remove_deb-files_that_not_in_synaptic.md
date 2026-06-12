---
title: "Howto remove deb-files that not in synaptic?"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by Azyx on 2009-08-27
I installed this HandBrake-0.9.3-Ubuntu_GUI_i386.deb

It doen't work on 8.04.

I can't use sudo apt-get autoremove ghb or sudo apt-get remove ghb becurse it can't find the package. ghb is the name in terminal.

/Cheers

---

### Post by Partyboi2 on 2009-08-27
Hi, open a terminal and
```
sudo apt-get remove handbrake
```

---

### Post by Azyx on 2009-08-27
> **Partyboi2 said:**
> Hi, open a terminal and
```
sudo apt-get remove handbrake
```

Thanx :)
How do I know the name of the program? When I should it in terminal I shouls use ghb...

---

### Post by Partyboi2 on 2009-08-27
I just use 
```
dpkg -l |less
``` then look for the package.

---

### Post by Azyx on 2009-08-27
> **Partyboi2 said:**
> I just use 
```
dpkg -l |less
``` then look for the package.

Thanx :)

---

