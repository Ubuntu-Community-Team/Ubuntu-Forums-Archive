---
title: "Falling at the first hurdle - where is my device manager?"
date: 2008-08-08
forum: General Help
---

### Post by dr_horse on 2008-08-08
Hey guys, just downloaded and installed Ubuntu 8.04 (for 64 bit systems) on a second hard drive with the intention of teaching myself some linux as I've only used windows until now. Didn't take me long to find my first snag though:

In the (albiet slightly out of date) Ubuntu book I have it says device manager (or its Ubuntu equivalent) can be found at System > Administration > Device Manager. It's not there, so I looked it up in Help and it says it can be found at System > Preferences > Hardware Info... well guess what it isn't there either.

It must be somewhere, so if one of you guys could forgive my noobness and point out to me where I can find it then I'll be on my way...

Thank you in advance.

---

### Post by pytheas22 on 2008-08-08
I think they removed that program in Hardy.  You can install it (or something quite similar) with:
```

sudo apt-get install hardinfo
```

(you may need to make sure first that all of the software repositories are enabled; go to System>Administration>Software Sources and check all the boxes under the "Ubuntu Software" tab)

and then it will be available at System>Preferences>System Profiler and Benchmark.

You can also view hardware information from the command-line (remember, you're on Linux now, so you don't need to feel like the command-line is your enemy anymore:)) with the command:
```

lspci
```

which outputs information about PCI cards and components of the motherboard (use 'lsusb' for USB devices).

---

### Post by drs305 on 2008-08-08
pytheas22 is correct that in hardy it is no longer installed by default. The original gnome device manager can be added with:
```
sudo aptitude install gnome-device-manager
```
from the universe repository.

Open it with the same command or from the System Tools menu.

---

### Post by john.nicholls on 2008-08-08
Alternatively you can install gnome-device-manager

---

