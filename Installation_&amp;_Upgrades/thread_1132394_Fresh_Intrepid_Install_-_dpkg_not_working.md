---
title: "Fresh Intrepid Install - dpkg not working"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by dejay703 on 2009-04-21
Hi guys,

I just installed Intrepid (64 bit) on my newly built machine.  Install went over fine, and everything seemed to be working.

I installed the proprietary drivers for my NVidia card, restarted, and still everything worked.

Now anything I try to install seems to go through (program works afterwards), but the end of the command prompt always ends with error.  Even if I try to install an already installed package I get an error.  I attached the output I get when running
```
sudo apt-get install gedit
```

Any ideas?  I have also tried to run
```
sudo dpkg --configure -a
```
but that also gives a bunch of errors. I would attach the output, but for some reason the usual redirection ">" did not work.

Any ideas?  This is the first time I've done an install of Ubuntu not on top of a current windows install, so I used the "Guided" method, mainly because I was too lazy to figure out how to set up the partitions.  Could this have screwed it up?

---

### Post by night_fox on 2009-04-21
could you try running dpkg from the recovery mode?

---

### Post by dejay703 on 2009-04-21
Just tried, and still get a ton of warnings (much of the same).  I saw though that it said it couldn't download a package from the security repository, but I haven't made any changes to my sources.list since the install... any other way to debug?

btw, thanks for the quick reply :)

---

### Post by dejay703 on 2009-04-21
I gave up, reinstalled, and now everything is working.  Thanks for the help anyway!

---

