---
title: "dpkg error"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by m3tal666 on 2009-09-12
Hey Guys, after recently trying to install xbmc on a fresh install (iv done this a fair few times on ff, hh, ii and now JJ it has given me an error of this

Unpacking replacement libsmpeg0 ...
dpkg: error processing /var/cache/apt/archives/libsmpeg0_0.4.5+cvs20030824-2.2_i386.deb (--install):
 unable to remove obsolete info file `/var/lib/dpkg/info//libsmpeg0.lhst-new': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libsmpeg0_0.4.5+cvs20030824-2.2_i386.deb


from what i can see on this error the is a // after info seeming that it may be a typo and this is why it cant find the file.... im stumped as on this and the worst thing is i cant get rid of it and i cant install anything or do anything....

HELP.. i dont wana fresh install again....

---

### Post by Soul-Sing on 2009-09-12
Did you install xbmc via the PPA repos.?

example for jaunty:deb [http://ppa.launchpad.net/team-xbmc/jaunty-ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/jaunty-ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/team-xbmc/jaunty-ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/jaunty-ppa/ubuntu) jaunty main

key: (sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9317790E)

---

### Post by Partyboi2 on 2009-09-12
Have you tried to create a blank '/var/lib/dpkg/info//libsmpeg0.lhst-new' file?
```
gksu gedit /var/lib/dpkg/info//libsmpeg0.lhst-new
```
Save the empty file and
```
sudo dpkg --configure -a
```

---

### Post by m3tal666 on 2009-09-12
hey thanks guys, i ended up doing a fresh install,

just found a post lying around saying to install xbmc from the intrepid repos.... just done this and all the updates and its all working sweet as.. my mediacentre is Working again!!!!

---

