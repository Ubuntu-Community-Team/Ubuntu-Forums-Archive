---
title: "Facebook Videos Wont Work. Help!"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by xjamespx on 2009-09-27
Hey guys. Im new to the ubuntu community- 

Facebook Videos will not work for me, however the youtube videos do.

I've installed the flash plugin.

It appears to me that im not the only one whos had this problem.... 
Any help to fix this problem would be greatly appreciated- Thanks

---

### Post by Catarina on 2009-09-27
Have you tried installing ubuntu-restricted-extras? :popcorn:

---

### Post by greyfox1 on 2009-09-27
I was having this problem too, and Computer Janitor (System->Administration->Computer Janitor) fixed it for me.  I honestly don't recall exactly what the problem was, but I remember it said something about a conflicting package and recommended I remove it.

There are different Flash plugins in the repositories, so if you installed the wrong one/ multiple (pretty sure this is possible), that can be the problem.  I think the "bad" one is called flashplugin-nonfree.  HTH

---

### Post by xjamespx on 2009-09-27
> **Catarina said:**
> Have you tried installing ubuntu-restricted-extras? :popcorn:

How do you go about doing this?

I tried using the cleanup janitor to work it out... and no luck.
Greyfox- where would i go about finding  flashplugin-nonfree

---

### Post by greyfox1 on 2009-09-27
You can find flashplugin-nonfree in Synaptic (System->Administration->Synaptic Package Manager).  Learn to love Synaptic - it's the source for installing everything possible from the software repositories (including ubuntu-restricted extras).  

I'll warn you that I am not an expert on Flash issues, but I can tell you that Flash on Facebook works for me and the Flash-related packages I have installed are:

flashplugin-nonfree
flashplugin-installer

If you start Synaptic and type "flash" in the Quick Search box, you can see what you have installed already (represented by a green box to the left of the package name).  Before you go messing around adding or removing Flash packages, though, you should check that you have ubuntu-restricted-extras installed like Catarina said.  

Again, open Synaptic, and search for "ubuntu-restricted-extras". If it shows up in the search results but isn't installed, place a check mark in the box then click Apply at the top.  It's OK if Synaptic tells you that it will have to install other packages too - just let it do what it wants to do and follow the instructions onscreen.  Further info on the restricted extras can be found [here]("https://help.ubuntu.com/community/RestrictedFormats"), on the Ubuntu wiki (check it out, it's a great resource!)  You might want to read up on [Synaptic]("https://help.ubuntu.com/community/SynapticHowto") while you're at it.

If you already have ubuntu-restricted-extras installed or installing it doesn't resolve your problem, please post back what Flash packages you have installed and we'll try to help.

---

