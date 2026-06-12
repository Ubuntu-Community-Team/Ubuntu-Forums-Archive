---
title: "duplicate sources.list entry"
date: 2008-11-25
forum: General Help
---

### Post by kakyoism on 2008-11-25
I'm getting this warning when doing 
sudo apt-get update.

```
W: Duplicate sources.list entry http://xxx.xxxx.xx hardy/multiverse Packages (/var/lib/apt/lists/xxx.xxxx.xx_ubuntu_dists_hardy_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

How should I solve this problem?
Thanks.

---

### Post by taurus on 2008-11-25
Look at your /etc/apt/sources.list to see which entries are the same.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by kakyoism on 2008-11-25
thanks did that.
i removed the duplicated multiverse line
but still get the same problem with a unique line:

deb mirror://www.getdeb.net/playdeb-mirror/hardy/ // hardy/. 


I got this repo from here:
[http://www.playdeb.net/](http://www.playdeb.net/)

---

### Post by taurus on 2008-11-25
Can you post your /etc/apt/sources.list?

---

### Post by kakyoism on 2008-11-25
Here it is:

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gulus.usherbrooke.ca/ubuntu/ hardy main restricted
deb-src http://gulus.usherbrooke.ca/ubuntu/ hardy main restricted
 
## Major bug fix updates produced after the final release of the
## distribution.
deb http://gulus.usherbrooke.ca/ubuntu/ hardy-updates main restricted
deb-src http://gulus.usherbrooke.ca/ubuntu/ hardy-updates main restricted
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gulus.usherbrooke.ca/ubuntu/ hardy universe multiverse
deb-src http://gulus.usherbrooke.ca/ubuntu/ hardy universe multiverse
 
deb http://gulus.usherbrooke.ca/ubuntu/ hardy-updates universe
deb-src http://gulus.usherbrooke.ca/ubuntu/ hardy-updates universe
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

deb http://gulus.usherbrooke.ca/ubuntu/ hardy-updates multiverse
deb-src http://gulus.usherbrooke.ca/ubuntu/ hardy-updates multiverse
 
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
 
deb http://gulus.usherbrooke.ca/ubuntu/ hardy-security main restricted
deb-src http://gulus.usherbrooke.ca/ubuntu/ hardy-security main restricted
 
deb http://gulus.usherbrooke.ca/ubuntu/ hardy-security universe
deb-src http://gulus.usherbrooke.ca/ubuntu/ hardy-security universe
 
deb http://gulus.usherbrooke.ca/ubuntu/ hardy-security multiverse
deb-src http://gulus.usherbrooke.ca/ubuntu/ hardy-security multiverse
 
deb http://ppa.launchpad.net/banshee-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu hardy main
 
deb mirror://www.getdeb.net/playdeb-mirror/hardy/// hardy/
 
# deb http://ppa.launchpad.net/deluge-team/ubuntu hardy main
# deb-src http://ppa.launchpad.net/deluge-team/ubuntu hardy main

deb http://ppa.launchpad.net/rvm/ubuntu hardy main
 
```

---

### Post by taurus on 2008-11-25
> **kakyoism said:**
> Here it is:

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gulus.usherbrooke.ca/ubuntu/ hardy main restricted
deb-src http://gulus.usherbrooke.ca/ubuntu/ hardy main restricted
 
## Major bug fix updates produced after the final release of the
## distribution.
deb http://gulus.usherbrooke.ca/ubuntu/ hardy-updates main restricted
deb-src http://gulus.usherbrooke.ca/ubuntu/ hardy-updates main restricted
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gulus.usherbrooke.ca/ubuntu/ hardy universe multiverse
deb-src http://gulus.usherbrooke.ca/ubuntu/ hardy universe multiverse
 
deb http://gulus.usherbrooke.ca/ubuntu/ hardy-updates universe
deb-src http://gulus.usherbrooke.ca/ubuntu/ hardy-updates universe
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

deb http://gulus.usherbrooke.ca/ubuntu/ hardy-updates multiverse
deb-src http://gulus.usherbrooke.ca/ubuntu/ hardy-updates multiverse
 
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
 
deb http://gulus.usherbrooke.ca/ubuntu/ hardy-security main restricted
deb-src http://gulus.usherbrooke.ca/ubuntu/ hardy-security main restricted
 
deb http://gulus.usherbrooke.ca/ubuntu/ hardy-security universe
deb-src http://gulus.usherbrooke.ca/ubuntu/ hardy-security universe
 
deb http://gulus.usherbrooke.ca/ubuntu/ hardy-security multiverse
deb-src http://gulus.usherbrooke.ca/ubuntu/ hardy-security multiverse
 
deb http://ppa.launchpad.net/banshee-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu hardy main
 
**[COLOR="Blue"]deb mirror://www.getdeb.net/playdeb-mirror/hardy/// hardy/[/COLOR]**
 
# deb http://ppa.launchpad.net/deluge-team/ubuntu hardy main
# deb-src http://ppa.launchpad.net/deluge-team/ubuntu hardy main

deb http://ppa.launchpad.net/rvm/ubuntu hardy main
 
```

The entry in blue just looks weird!  Edit your /etc/apt/sources.list put a # in front of that entry to comment it out.  Save it and close down gedit window.  Now, what happens when you run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kakyoism on 2008-11-25
thanks, the problem is gone,
but that means i can't get the playdeb package anymore...
See here
[http://www.playdeb.net/](http://www.playdeb.net/)

---

### Post by fooman on 2008-11-25
just use the .deb from that same link...[[COLOR="Blue"]click here[/COLOR]]("http://www.playdeb.net/playdeb_0.2-0%7Egetdeb1_all.deb")

that will add the correct repo.

---

