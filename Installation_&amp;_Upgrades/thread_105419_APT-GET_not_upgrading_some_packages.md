---
title: "APT-GET not upgrading some packages"
date: 2005-12-18
forum: Installation &amp; Upgrades
---

### Post by Julian David Pitt on 2005-12-18
When I run apt-get dist-upgrade get the following
>  Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  bluefish eog evms evms-ncurses gnomebaker gthumb k3b k3blibs libevms-2.5
  pmount rhythmbox totem totem-xine
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
root@ubuntu:/home/julian # 
Why can i not get these packages upgraded please and why is this happening. I am only doing this after performing an update and how do I run smart-upgrade which is the other option I am given after apt-get dist-upgrade. Cheers all.

---

### Post by aysiu on 2005-12-18
If you read the manual for apt-get by typing ```
man apt-get
``` you'll see this option in there > --ignore-hold
Ignore  package Holds; This causes apt-get to ignore a hold placed on a package. This may be useful in conjunction with dist-upgrade to override a large number of undesired holds. Configuration Item: APT::Ignore-Hold. So what you would do is ```
sudo apt-get --ignore-hold dist-upgrade
```

---

