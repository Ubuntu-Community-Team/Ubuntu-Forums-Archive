---
title: "Update problem"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by littlemattjk on 2009-02-02
resolution problem and update problem
Ok, on my 8.10 ubuntu os my screen has a black line on the right and hangs off the left so i cant see some of the screen and it does it the bottom as well.
Also my Add/Remove program is not working when i try to download somethig it says

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

and i also downloaded a program from the web and when i install using package installer it says

"please close the other application e.g. 'Update Manager','aptitude' or' Synaptic' first"

even when there's not any other program running at all


System Hardware
Intel pentium dual Core desktop processors
3gb of ram
Nvidia Geforce 7100 Graphics

I also like to play a game called "teeworlds" and ill play it for about ehh 2-5 minutes and my computer will freeze and all i can do is shut down!

---

### Post by Partyboi2 on 2009-02-02
Open a terminal (Applications>Accessories>terminal) and type
```
ps -e
``` This will show a list of all your running processes. Look download the list and see if any package managers are listed. If they are then type
```
killall name of process
```eg
```
killall synaptic
```then type
```
sudo dpkg --configure -a
```for your add/remove problem.

---

### Post by littlemattjk on 2009-02-02
thanks for your help i greatly appreciate it

---

