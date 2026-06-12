---
title: "repository problems"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by wesly82 on 2009-01-26
I went to update my computer, having Ubuntu 8.10, but it says the repositories are out of date. How do I fix this?

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.

Here's my source list

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by taurus on 2009-01-26
I just checked with my machine and everything is looking good here.  In fact, I have 29 packages I need to upgrade (evolution, vim, libxine, etc.).

Try updating your machine from a terminal and see what happens.

---

### Post by wesly82 on 2009-01-26
I did that, and it said the same thing.

---

### Post by lunatico on 2009-03-26
I'm having this same problem.
Anyone been able to fix it?

---

### Post by lunatico on 2009-03-27
I think I finally found the way to fix this.

For all I tried have a look at my post at [https://answers.edge.launchpad.net/ubuntu/+source/apt/+question/65425](https://answers.edge.launchpad.net/ubuntu/+source/apt/+question/65425)

In summary:

Reboot and on the grub menu select Recovery Mode, when you get to the menu choose the repair broken packages option. It will probably say it needs to update a package, press d to see the details of the package and take note of the package name. If your choose yes to proceed with installation/update it will most likely fail as there is probably no Internet connection. So boot normally and open Synaptic, search for the package or packages you wrote down, select them and install them. After that things should be fine.

---

