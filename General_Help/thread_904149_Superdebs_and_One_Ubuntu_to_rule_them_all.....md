---
title: "Superdebs and One Ubuntu to rule them all...."
date: 2008-08-29
forum: General Help
---

### Post by hammer v2 on 2008-08-29
Hey guys... I'm trying to make a one click packaging system for ubuntu, kubuntu and xubuntu. It doesn't reinvent the wheel and works by using stuff that's already in ubuntu (apt debs etc..). 
Basically the deal is this (Warning slightly techie here);

I'm creating an automated way to bundle a package and all it's dependencies together into one executable file. When The user clicks on the file, it creates a local repository, updates the sources.list and install a metapackage that depends on everything in the new repository. I've tested it and it works great! Yay! 

Anyway, the creation of these "superdebs" happens in a Virtual Machine. Basically I create a BASE distribution as a live CD (Read only) that only gets run in a VM. All this distro does is run my package creator script. It opens up synaptic. You choose which package you want in your superdeb and presto! It creates a superdeb for you.

Only catch is....I need a "BASE" distro. 
Too much stuff in the base distro and the superdebs won't work for everyone. Too little and each "superdeb" will be enormous!

I know I can't please everyone here... but what would be a base distro that would provide a superdeb that works accross kubuntu, xubuntu and Ubuntu?

Sorry for the long post....
H.

---

### Post by Sam Lars on 2008-08-29
I'm not sure I totally understand what you're saying.
Some packages require a lot of dependencies and are going to be really big.
Do you mean by "base distro" the packages you'll assume are installed by default that don't need to be in the package?
If it's not too environment specific, it should work fine for everyone.  If not, you could mave a native superdeb that would have fewer packages.  For example, a Gnome app for Gnome users would not need all the basic libs that they would have installed.  And then you could mave a non-native one for KDE/XFCE/Other environment users that would include all the necessary Gnome packages that they wouldn't have.

---

### Post by silverglade00 on 2008-08-29
Ubuntu Server with none of the servers chosen at install time might be a good starting point. Maybe you should throw in X as well.

---

### Post by hammer v2 on 2008-08-29
> **Sam Lars said:**
> I'm not sure I totally understand what you're saying.
Some packages require a lot of dependencies and are going to be really big.
Do you mean by "base distro" the packages you'll assume are installed by default that don't need to be in the package?
If it's not too environment specific, it should work fine for everyone.  If not, you could mave a native superdeb that would have fewer packages.  For example, a Gnome app for Gnome users would not need all the basic libs that they would have installed.  And then you could mave a non-native one for KDE/XFCE/Other environment users that would include all the necessary Gnome packages that they wouldn't have.


Hmm... good pints..but quite honestly I'd rather have the superdeb large and work for everybody than smaller and only work for a set environment. It will be beginners using the system and they won't know their KDEs from their Gnomes. :)

---

### Post by hammer v2 on 2008-08-29
Hey here's an Idea! I think I worked out how to do it. I'll download the three metapackages used to create ubuntu, kubuntu and xubuntu respectively. I think Their called u/k/xbuntu-desktop then I'll open up their lists of dependancies and only use which packages appear 3 times. 


Can anyone see any problems with this approach?


The server Idea is good too... hmmm

H.

---

