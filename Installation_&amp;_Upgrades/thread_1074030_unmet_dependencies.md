---
title: "unmet dependencies"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by bita on 2009-02-18
hi everyone ,

i have ubuntu 8.04 and i ran an update on it ,after that my network manager stopped working i removed my network manager and now when i try to reinstall it i get a message that says :

The following packages have unmet dependencies:
  libnm-util0: Breaks: network-manager-gnome (< 0.7~~) but 0.6.6-0ubuntu3 is installed
  libnm-util1: Breaks: network-manager-gnome (< 0.7~~) but 0.6.6-0ubuntu3 is installed

E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

and when i try apt-get -f install i get the message that says :

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

I really need to get my network manager back so appreciate any help .

---

### Post by taurus on 2009-02-18
What does your /etc/apt/sources.list look like?

```
cat /etc/apt/sources.list
```

---

### Post by konqueror7 on 2009-02-18
try
```
sudo apt-get autoremove
```
see if that helps, it removes packages no longer used
or you could try
```
sudo apt-get autoremove --purge gnome-network-manager
```
this will both remove the packages related and its configuration files. btw, why do you want to uninstall gnome-network-manager?

---

### Post by bita on 2009-02-18
This is what i have in my /etc/apt/sources.list :

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main

i tried sudo apt-get autoremove and it said :

Correcting dependencies... failed.
The following packages have unmet dependencies:
  libnm-util0: Breaks: network-manager-gnome (< 0.7~~) but 0.6.6-0ubuntu3 is installed
  libnm-util1: Breaks: network-manager-gnome (< 0.7~~) but 0.6.6-0ubuntu3 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

But then sudo apt-get autoremove --purge network-manager-gnome worked and it removed network manager gnome but again when i try to install network manager by using sudo apt-get install network-manager-gnome it says :

The following packages have unmet dependencies:
  network-manager-gnome: Depends: network-manager (>= 0.7~~svn20080928) but it is not going to be installed
E: Broken packages

---

### Post by taurus on 2009-02-18
What if you edit your /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and comment out the two repos for network-manager by placing a # in front of them.

```

**[COLOR="Blue"]#[/COLOR]**deb http://ppa.launchpad.net/network-manager/ubuntu hardy main
**[COLOR="Blue"]#[/COLOR]**deb-src http://ppa.launchpad.net/network-manager/ubuntu hardy main

```
Save it and see if you can reinstall network-manager now.

---

