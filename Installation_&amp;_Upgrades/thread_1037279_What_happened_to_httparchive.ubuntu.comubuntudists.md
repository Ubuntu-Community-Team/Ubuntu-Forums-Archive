---
title: "What happened to http://archive.ubuntu.com/ubuntu/dists/feisty?"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by gpongo on 2009-01-11
I can't load anything or even upgrade to gusty gibson, because even thought ./feisty-security/, ./feisty-backports/, etc. is there, upgrade barfs because the main directory ./feisty/ is not.

Is this a permanent change, or temporary. What can I do?

---

### Post by whoop on 2009-01-11
Don't think feisty is still supported.

Is this worth anything: [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

hope this helps

---

### Post by gpongo on 2009-01-11
Does this mean I can upgrade if I manually edit /etc/apt/sources.list? The menu for System/Administration/Software sources doesn't let me enter "http://old-releases.ubuntu.com/ubuntu/dists/". The upgrade tool won't let me upgrade to 7.10. They both generate a dialog saying 

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

and then in a label box below, it lists the http including the missing fiesty directory.

What can I do to quickly upgrade my system? Am I out of luck at this point?

---

### Post by gpongo on 2009-01-11
OK, I changed /etc/apt/sources.list to be

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main universe
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports universe main
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security universe main
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates universe main
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-proposed universe main

and then executed
sudo apt-get update
and for now things appear to be OK. Hopefully I will be able to upgrage to 7.10 when I fix the current problem I've been dealing with.

Thanks!

---

### Post by gihzmo on 2009-02-02
You dont know how much of a headache this was... thank you so much. :D

---

### Post by vilerichard on 2009-02-23
This thread helped me a lot.  I ran into some other problems upgrading from Feisty to Gutsy today.  I've posted some details at [http://wunderhacks.blogspot.com/2009/02/ubuntu-upgrading-from-fiesty-to-gutsy.html]("http://wunderhacks.blogspot.com/2009/02/ubuntu-upgrading-from-fiesty-to-gutsy.html").  Maybe someone else will find them helpful.

---

