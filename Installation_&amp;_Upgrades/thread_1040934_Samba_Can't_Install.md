---
title: "Samba Can't Install"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by Moozacman on 2009-01-16
When I try and install samba I receive the following error
Could not mark all packages for installation or upgrade
The follwing packages have unresolvable dependencies. make sure that all required repositories are added and enabled in the preferences.

samba:
 Depends: samba-common but it is not going to be installed
  Depends: libc6 (>=2.8~20080505) but 2.7-10ubuntu4 is to be installed
 Depends: libcups2 (>=1.3.8) but it is not installable
 Depends: libgnutls26 (>=2.4.0-0) but it is not installable
  Depends: libpopt0 (>=1.14) but 1.10-3build1 is to be installed
 Depends: libwbclient0 but it is not going to be installed
  Depends: lsb-base (>=3.2-14) but 3.2-4ubuntu1 is to be installed

......

I've tried going and re-installing a few of the repositories but it's not working. Can anyone tell me what I need to do to fix this?

---

### Post by Partyboi2 on 2009-01-16
Can you open a terminal (Applications>Accessories>Terminal) and please post the output to
```
cat /etc/apt/sources.list
```

---

### Post by Moozacman on 2009-01-30
Hey guy, sorry I don't actually get on this computer very often so I haven't been able to reply.

Here's what you asked me to get

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

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
deb [http://ppa.launchpad.net/tcarrez/ubuntu](http://ppa.launchpad.net/tcarrez/ubuntu) intrepid main

---

### Post by Partyboi2 on 2009-01-31
You have all the repos enabled for hardy , but I noticed that you have 
```
deb [http://ppa.launchpad.net/tcarrez/ubuntu](http://ppa.launchpad.net/tcarrez/ubuntu) intrepid main
``` which also provides samba packages, which could be causing the conflict as adding intrepid repos to hardy can do.
I would suggest removing or commenting out that repo from your sources.list
Open a terminal and open your sources.list 
```
gksu gedit /etc/apt/sources.list
```then delete or add a # infront of
```
deb [http://ppa.launchpad.net/tcarrez/ubuntu](http://ppa.launchpad.net/tcarrez/ubuntu) intrepid main
```then save and back in the terminal
```
sudo apt-get update
``` then try installing samba again.

---

