---
title: "I seem to have messed up sources.list"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by Lovok on 2009-01-15
As the title says, I seem to have messed something up while adding repositories to sources.list. 
I am running Edubuntu 8.04, and this started happening after Intrepid Ibex was released. The repositories I tried adding were in regards to Spring and Complete Annihilation :)

Here is what I have :

```

# 
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```

I did try and edit it a bit, adding the intrepid ibex repos, removing the spring ones (yet they still updated yesterday.. :/)
The "errors" I get with updating are the following :
The only things that show up in the Synaptic Package Manager are already installed, leading me to believe it only knows what's already on here..
And when I do sudo apt-get update, 
```

Ign http://ppa.launchpad.net hardy Release.gpg
Ign http://ppa.launchpad.net hardy/main Translation-en_CA
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]
Ign http://ppa.launchpad.net hardy/main Packages
Ign http://ppa.launchpad.net hardy/main Sources
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/main Sources
Fetched 1B in 2s (0B/s)
Reading package lists... Done

```

Any ideas?
Thanks.

---

### Post by Lovok on 2009-01-15
...in my tinkering frenzy, I must have done something to untick all of the "Downloadable from the Internet" options in Software Sources...
Everything seems to be in order now :)
Now if there was only a way to delete this thread.... :/

---

