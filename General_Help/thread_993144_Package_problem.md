---
title: "Package problem"
date: 2008-11-25
forum: General Help
---

### Post by denny577 on 2008-11-25
I don't get standard games in my package list. What repositories do I need?

On [this list](https://help.ubuntu.com/community/Games) it says I just have to search in Add/Remove. If I type wormux it doesn't find anything. Am I missing some standard repository? After adding ```
deb http://ppa.launchpad.net/exaile-devel/ubuntu intrepid main
``` I was able to download Exaile.

:confused::confused::confused:

My sources.list (with stripped comments):
```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

deb http://nl.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ intrepid restricted main multiverse universe

deb http://nl.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties

deb http://nl.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://nl.archive.ubuntu.com/ubuntu/ intrepid-updates universe

deb http://nl.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

# deb http://nl.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://nl.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse

deb http://ppa.launchpad.net/exaile-devel/ubuntu intrepid main
```
Regards, Dennis

---

### Post by fooman on 2008-11-25
when you open add/remove,  there is a box in the top middle that says "show".

make sure that "all available applications" is chosen in that box.

---

### Post by denny577 on 2008-11-25
Ofcourse...

Thanks very much :D

---

