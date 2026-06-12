---
title: "Noobie Package Installing Question"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by spiffo on 2009-11-08
Ok, I think this might be a real noobs question, but here goes.

I installed a package using Synaptic Package Manager, it seemed to go fine, I marked for install, hit apply and everything seemed to work. However it doesn't appear in my Applications List and it doesn't appear in Ubuntu Software Centre - Installed Software.

I tracked the executable down to /usr/bin When I try to Open it nothing happens and under properties it says the owner is root, so I guess even though I installed it, I don't have the rights to run it  ???

Did I install it incorrectly, how do I get it to appear in my Applications ?

---

### Post by earthpigg on 2009-11-08
what program was it?

if it's a terminal app, it won't appear in the menus. one would generally launch a terminal app by typing the command associated with the program in a terminal - often the program name.

if it's a graphical program, you can right click on the top menu -> edit menus -> click around to add/change the menu items. 

if you let us know what specific program/package it is, we can be more specific.

---

### Post by spiffo on 2009-11-08
I've tried a couple, it seems to be everything I try and install, I'm obviously doing something fundamentally stupid.

an - anagram program
animals - some kind of game

They get installed but I can't run them !

---

### Post by earthpigg on 2009-11-08
yup, those are both terminal games, not graphical ones. :D you are installing them correctly.

to read the manual for an, type this in a terminal:
```
man an
```
to read the manual for animals, type this in a terminal:
```
man animals
```
(starting to see a pattern? :D )

to run animals (which looks like a fun little game, thanks!), type this in a terminal:
```
animals
```

---

### Post by devi59 on 2009-11-08
> **earthpigg said:**
> ...to read the manual for animals,...
```
man animals
```
I'm sorry I'm trolling but this actually made me giggle a little. I know that is how you see manuals but I like man animals every man I know IS an animal!

---

### Post by spiffo on 2009-11-08
There you go, I knew I was doing something stupid, they're all programs designed to be run from a Terminal session.

Cheers, Guys !

---

