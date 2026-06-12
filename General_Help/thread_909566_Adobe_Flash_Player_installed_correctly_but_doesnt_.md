---
title: "Adobe Flash Player installed correctly but doesnt exist"
date: 2008-09-03
forum: General Help
---

### Post by winrowc on 2008-09-03
Hi everyone,
I tried installing Adobe Flash Player many times in Firefox 3.0, but to no avail. If the installations had failed that would be one thing, but the thing is that they succeeded, but arent showing up in my plugins menu. When I go to a site that requires flash, it says I need to download it. I tried first the apt-get way, and that installed successfully, but there was no change in firefox. Then I tried doing it the tar.gz way, but that also was not effective. I have Gutsy Gibbon, and I am at a loss for what it could be. I tried restarting firefox and my computer multiple times, but nothing helped.Thanks in advance!

---

### Post by gjoellee on 2008-09-03
lets make sure you have flash removed....
```
sudo apt-get remove flashplayer-plugin
```

now go to the page below and download the flashplugin.deb
[http://www.kshoster.net/?c=downloads&h=deb](http://www.kshoster.net/?c=downloads&h=deb)

---

### Post by winrowc on 2008-09-03
Woops, I made a silly mistake. It was all because I had been logged in as root for something else that it was installing in the wrong directory. Should have just used the sudo command. Lesson learned :)

---

