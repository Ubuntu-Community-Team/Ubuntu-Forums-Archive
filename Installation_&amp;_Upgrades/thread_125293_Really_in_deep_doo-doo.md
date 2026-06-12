---
title: "Really in deep doo-doo"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by sheepsbrain on 2006-02-03
Hello, I was having trouble earlier installing some package (python2.4-dev), and so I was trying to install dependencies using apt-get. This didn't work. So then I went to synaptic, it reported that there were broken dependencies and said to use the broken filter, so I used the broken filter, checked the files and there was like a whole lot of stuff including gnome stuff and python stuff and I guess synaptic itself. I didn't run apply at first, then somehow accidentally, clicking around for this python-dev thing, I clicked apply. :(

And here's where all my trouble started: I lost synaptic in the menu. I lost most every other thing, running apt-get install synaptic gets me an unmet dependecy error: "liblaunchpad-integration0" and that's it. I don't know what to do. It seems that no one has been as stupid as me on Google, since this problem is nowhere to be found. What should I do? Should I just reinstall the whole system?? Plz help.

---

### Post by Saiboogu on 2006-02-03
Does apt-get -f install fix it? Maybe not, if your dependancies are truely buggered.

I've thought it was dead a few times, and that fixed it. If its too far gone, perhaps a fresh install will be best. However, I've seen the following suggested as a fix before, perhaps you want to give it a shot.. 

Scenario 3 seems to be the one for you:
[http://ubuntuforums.org/showthread.php?t=90675](http://ubuntuforums.org/showthread.php?t=90675)

Good luck!

---

