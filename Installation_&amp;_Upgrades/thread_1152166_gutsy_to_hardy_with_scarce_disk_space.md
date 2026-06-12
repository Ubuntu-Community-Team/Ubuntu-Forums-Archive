---
title: "gutsy to hardy with scarce disk space"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by hardmath on 2009-05-07
I'm trying to do a distribution upgrade on an older machine with a mere 3.2Gbyte hard disk.  When it was necessary to move from Feisty to Gutsy, I did the upgrade by the skin of my teeth by removing some packages, then adding them back after the upgrade.

So now with the Gutsy End_of_Life upon me, I have to do something similar.

The error message about insufficient disk space suggests that I could add more space to /, but the simple expedient of plugging in a 4Gbyte memory stick does not help.

So, does anyone have a variant on this "garden path" approach of temporarily adding more disk space that has a better chance of working?  One danger is that any space usable by the distribution upgrade manager may get committed to use by the new distribution!!

Failing that, does anyone have a suggestion about efficiently identifying a group of packages to remove until the distribution has been upgraded?  The insufficient disk space message wants me to free up about 320Mbytes, so I should perhaps aim to free up somewhat more, perhaps 400Mbytes just to be sure.

Failing that, what directories should I backup in order to do a fresh install of a later distribution?  Is it just the home directory (with its usernamed subdirectories) that I will essentially need?

regards, and TIA
hardmath

---

### Post by zvacet on 2009-05-07
> Failing that, does anyone have a suggestion about efficiently identifying a group of packages to remove until the distribution has been upgraded? 

You can try to remove every third party packages you installed.You will find them in **synaptic>sources**.Also when you do the upgrade uncheck all third party repos.Yes,you need home because there are all your settings and probably files/data you don´t want to lose.

---

### Post by HyRax on 2009-05-07
You're going to be really cutting it fine. A vanilla 9.04 Jaunty installation eats up 2GB of space, but you need at least an extra 2GB to store updates and so forth. Sure, you can clear the Apt cache after you've finished installing updates to clear space for future updates, but this is only going to carry you so far.

I'd definitely recommend trimming down the default install. You can get it down to 1GB by removing a lot of stuff you don't need such as The GIMP, Gnome Games, etc. but it's a bit of a hassle - it'd save you some frustration to simply buy more storage for that machine, really. If the machine is too old to handle larger hard-drives, then consider a PCI SATA controller that can be had for about $20 and connect drives that way.

Alternatively, dump the old PC altogether - you can build some pretty kick-**** machines for less than $300 using new components now - good enough to virtualise on too.

EDIT: I should add that my quote for 2GB is JUST for the installed OS. This does not take into consideration the extra disk space taken up with the swap partition.

---

### Post by sailthesea on 2009-05-07
If you can get a LiveCD of Hardy together you may be able to use the install to squeeze it onto your machine if you slash everything else 
 Gonna find my CD and see
 I'm not sure if thats enough disk space though:(

---

### Post by sailthesea on 2009-05-07
Right, that didn't go very well
It may be worth trying a LiveCD install of Hardy, but a lighter distro is probably the answer if this is your only machine and you can't afford a new one like the rest of us
:)

---

