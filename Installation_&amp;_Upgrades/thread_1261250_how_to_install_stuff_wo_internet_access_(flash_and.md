---
title: "how to install stuff w/o internet access (flash and java plug ins)"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by rhythmiccycle on 2009-09-08
i have a computer at work that doesn't have full internet access.

i need flash and java plugins for the browser. I cannot install them directly off of the net. 

how can i do this? 
are there deb files i can get online, and then bring them to work?

i would also like to do things like update the system, can this be done off line?

---

### Post by oldos2er on 2009-09-08
[http://keryxproject.org/](http://keryxproject.org/)

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by StuartN on 2009-09-08
Go to Synaptic on the work computer, select all the packages you want and then choose File->Generate package download script. Take the script home and run it in a terminal on the computer with internet access. Bring all the downloaded packages back to work and go to Synaptic and File->Add downloaded packages.

---

### Post by rhythmiccycle on 2009-09-08
> **StuartN said:**
> Go to Synaptic on the work computer, select all the packages you want and then choose File->Generate package download script. 

i need to install:
Package: flashplugin-installer
(it shows up from with in firefox)

also:
Package: sun-java6-plugin
(if 6 is the latest)
(it is in the add/remove)

when i type flash or java in synaptic i don' see any of those.

also, i want to do a all around update "apt-get update"

---

