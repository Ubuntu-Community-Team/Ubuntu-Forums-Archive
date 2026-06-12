---
title: "Really deep doo doo"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by sheepsbrain on 2006-02-03
(I tried to post this once, but I guess nothing is wokring for me today so this might be a double post, sorry in advance :confused:)

This is the dumbest thing I've probably ever done: I somehow managed to uninstall synaptic and can't install it again. I was trying to fix broken dependencies in synaptic so that I could install a package (python2.4-dev). 

It gave me a list of like 300 packages that it was going to uninstall. Initially I said no, but somehow it came up again and I clicked OK so now I have no synaptic (I don't even boot into the desktop -- only into the commandline), as well as a lot of other stuff.  :( 

And I can't install synaptic. It gives me an unmet dependency error: "liblaunchpad-integration0" apparently "it's not going to be installed". I can't install that package either, and I am just really at the end of my energy. I don't know what else to do. Should I just re-install the whole thing again?

---

### Post by az on 2006-02-03
Make sure you only have breezy repositories in your list (or only Dapper if that is what you want), update and install ubuntu-desktop

sudo nano /etc/apt/sources.list (or if you have a working gui, sudo gedit /etc/apt/sources.list)
sudo apt-get update
sudo apt-get install ubuntu-desktop.

---

### Post by sheepsbrain on 2006-02-03
Just tried it, and it gives me a whole list of dependencies that are not going to be installed concluding with: "E: broken packages".

My sources.list seems to be only breezy.

---

### Post by az on 2006-02-04
try 
sudo apt-get -f install

---

