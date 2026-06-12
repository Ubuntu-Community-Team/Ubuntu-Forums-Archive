---
title: "Can't install beryl."
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by GroogFish on 2009-09-01
I'm following all the instructions on this page-
[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

And I can't run this line-
sudo apt-get install beryl emerald-themes


I get this error-
micah@micah-comp:~$ sudo apt-get install beryl emerald-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package beryl**

Why doesn't ubuntu have install files that does all this terminal stuff for you?

---

### Post by oldos2er on 2009-09-01
Are you running 7.04? It's support ended long ago; you should probably update to 8.04 or newer.

 Compiz-fusion has been installed by default since 7.10. Enable it via menus System, Preferences, Appearance, Visual Effects.

---

### Post by GroogFish on 2009-09-01
I have 8.04 and I can go to the visual effects but this doesn't look at all like the beryl I see on youtube. The only thing that happens is everything looks liquid when I move it.

---

### Post by oldos2er on 2009-09-01
Install the package compizconfig-settings-manager, which will give you greater control over compiz plugins.

---

### Post by presence1960 on 2009-09-01
> **oldos2er said:**
> Install the package compizconfig-settings-manager, which will give you greater control over compiz plugins.

+1

in addition you can install simple-ccsm as well.

BTW beryl has been merged and is now know as compiz.

---

### Post by nogoodreason on 2009-09-26
I'd like to nominate this thread to be stickied in the Absolute Beginners forum.  I'd been trying to activate the YouTube-hyped Beryl for weeks before coming across this thread, and I'm sure I'm not the only one.

Thanks for finally bringing some life to my Linux experience. :)  And here's hoping the next release will have this stuff pre-installed instead of just leaving it at the option of "wobbly windows".

---

