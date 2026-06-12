---
title: "No access to partner repository"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by helgman on 2009-03-24
I've got a machine running Ubuntu Server 8.10 that I'm trying to install some 3rd party software on but no luck - it doesn't fetch anything from the third-party repository (or so I think). I'm looking for the Alfresco Lab 3 ...

(No look with the search function or Google ...)

Anyway, here's my sources.list:
```
# 
# deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ intrepid main restricted

#deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://se.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://se.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://se.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://se.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://se.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://se.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://se.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://se.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://se.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
```

Regards,
Helgman

---

### Post by cariboo on 2009-03-24
The reason you can't install the packages from the repositories, is that it isn't there, it looks like you have to go [here]("http://wiki.alfresco.com/wiki/Labs_3_Final_download_files") to download it.

If you are in doubt about a package, you can always check [here]("http://packages.ubuntu.com/") to see if it is available.

Jim

---

### Post by helgman on 2009-03-25
Thank you for helping out, guess I'll have to make it the long way around then ...

The reason I hoped to find it in the partner repository was this (some what old) article: [http://www.ubuntu.com/news/alfresco-enterprise-content-management](http://www.ubuntu.com/news/alfresco-enterprise-content-management)

And the reason for me thinking I didn't find anything else that I've "heard" should be in the repository (like parallels) - but now I see adobe-flashplugin and I guess that one should be hosted there so ... my mistake.

Time to look at the installation link.

Regards,
Helmgan

---

