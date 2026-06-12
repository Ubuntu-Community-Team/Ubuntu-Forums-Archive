---
title: "[SOLVED] Update manager permanently outdated"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by barbolanero on 2008-12-12
I have been experiencing some odd bug on my Hardy. Out of nowhere update manager started to show a message saying it was outdated, but if I check for updates it doesn't seem to upgrade and gives this message:

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

I'd tried with sudo-aptitude update and sudo aptitude full-upgrade (out of random) and didn't work either.

I have Intrepid running on my laptop just perfectly fine. Don't know what to do? Any ideas?

Barbolanero

---

### Post by albinootje on 2008-12-12
If you're using Intrepid now, you can remove the Hardy cdrom lines in /etc/apt/sources.list

---

### Post by barbolanero on 2008-12-12
I'm using Hardy, Intrepid is being use on my laptop. I just stated it to say that Intrepid is not giving me any problem, whereas Hardy is. Don't know if has anything to do though.

---

### Post by barbolanero on 2008-12-15
Anyone out there?

---

### Post by bapoumba on 2008-12-15
Please post your sources.list:
```
cat /etc/apt/sources.list
```
You probably need to comment out the cdrom.

---

### Post by barbolanero on 2008-12-15
Well, this is my source list:

> deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Edubuntu 8.04.1 _Hardy Heron_ - Release i386 Binary-1 (20080701.1)]/ hardy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://uy.archive.ubuntu.com/ubuntu/](http://uy.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse

deb [http://trylegaldownloads.de/ubuntu](http://trylegaldownloads.de/ubuntu) hardy games
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports restricted main multiverse universe

Also, today it just happened to inform me of two updates. I downloaded thinking maybe it was fixed, but after downloading them it still says it's outdated. Please help me!:confused:

---

### Post by 67GTA on 2008-12-15
Open the software sources tool and uncheck the box for the Ubuntu CDROM.

---

### Post by barbolanero on 2008-12-15
That did the trick for me! Thanks a lot:guitar:. I was wandering if someone could explain to me what the heck happened?. I mean, how did the get active and why did turning them off solved my problem? And also, do I have all the repositories that I should on my source list?. Is there anything else I could add to improve it?

---

### Post by 67GTA on 2008-12-15
There are a few packages that are installable from the Ubuntu live CD. It is enabled by default. It is like a small repo. The updater is choking because it can't refresh the package list on the CD. Intrepid is the first version where I have seen this happen. Your sources list looks fine. You have multiverse, universe, and backports enabled, so you have everything.

---

