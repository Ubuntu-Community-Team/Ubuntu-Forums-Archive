---
title: "Latest nvidia drivers not available [Hardy]"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by liberostelios on 2009-01-15
Hi,

I am getting the following problem: i know that nvidia released the latest 180.22 drivers. But i am stuck on using some old nvidia drivers because the latest version of them in synaptic is 169.12, which is pretty old! Even envyng supports only up to 173.14.12. What should i do to have the latest nvidia drivers available on my PMS?

Here is my sources.list:

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
deb-src [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) hardy main restricted
deb-src [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) hardy multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) hardy-updates main restricted
deb-src [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) hardy universe
deb [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) hardy multiverse
deb [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) hardy-security main restricted
deb-src [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) hardy-security universe
deb [http://ubuntu.otenet.gr/](http://ubuntu.otenet.gr/) hardy-security multiverse
deb [http://ppa.launchpad.net/festor90/ubuntu](http://ppa.launchpad.net/festor90/ubuntu) hardy main
deb [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) hardy main
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
```

---

### Post by FAMUgolfer on 2009-01-15
Follow the directions carefully in this post....The only problem with upgrading to the newest nvidia driver is that it requires to reformat the kernel!!!

[http://ubuntuforums.org/showthread.php?t=1002828&highlight=hardy+nvidia+180.22](http://ubuntuforums.org/showthread.php?t=1002828&highlight=hardy+nvidia+180.22)

Good luck!!

---

### Post by liberostelios on 2009-01-16
Thanks really much for the help. ;) It's a pity, though, that there is now easy way for having the newest nvidia drivers, all the time.

---

