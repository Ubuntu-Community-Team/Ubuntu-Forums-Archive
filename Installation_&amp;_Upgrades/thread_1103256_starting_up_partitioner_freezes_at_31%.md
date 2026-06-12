---
title: "starting up partitioner freezes at 31%"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by tummel on 2009-03-22
I tried to install kubuntu on my pc, which already has XP, but the installation never gets beyond the point, where there comes up a loading bar with the heading "starting up partitioner" ... Up till 31% it goes quite fast, after that nothing happens. I researched that problem and found a lot of people having the same problem (sometimes at 45% or 52%), but unfortunately they never got any answer what they could do about that. 
Hope I will have more luck. ^^
Thanks a lot.

Tummel

---

### Post by upchucky on 2009-03-22
make sure you are only doing one partition task at a time.

since this has windows on it make sure you have defragged the windows partition several times, windows puts stuff willy nilly all over the place and this slows down the pc, the defrag, and the partitioner.

I have seen Gparted fail to do certain partition tasks, and switching to partedit picks up where gparted fails, and vice versa.

---

### Post by Tobi-fp on 2009-03-22
It seams to be a problem with the KUBUNTU installer, try ubuntu, or another flavor and then just install kubuntu with "sudo apt-get install kubuntu-desktop"

---

### Post by tummel on 2009-03-22
I have defragged the windows partition already (before you ask, there is no other partition). The trouble is, during installation, you can't do anything (as far as I know). You just press next, the window pops up, and there's nothing to be done except to quit the installation.

---

