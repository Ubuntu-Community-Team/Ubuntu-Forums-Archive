---
title: "Intrepid to Jaunty - Partial upgrade error"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by prickee on 2009-05-04
I had Intrepid up and running just fine, then I decided to try Jaunty.  At first all looked fine until I got this during updating.  Here's the screenshots and sources.list.  I'm sure I'm missing something so hope someone can point me in the right direction.  Thanks in advance.


# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.its.uidaho.edu/pub/ubuntu/](http://mirror.its.uidaho.edu/pub/ubuntu/) jaunty main restricted
deb-src [http://mirror.its.uidaho.edu/pub/ubuntu/](http://mirror.its.uidaho.edu/pub/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.its.uidaho.edu/pub/ubuntu/](http://mirror.its.uidaho.edu/pub/ubuntu/) jaunty-updates main restricted
deb-src [http://mirror.its.uidaho.edu/pub/ubuntu/](http://mirror.its.uidaho.edu/pub/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.its.uidaho.edu/pub/ubuntu/](http://mirror.its.uidaho.edu/pub/ubuntu/) jaunty universe
deb-src [http://mirror.its.uidaho.edu/pub/ubuntu/](http://mirror.its.uidaho.edu/pub/ubuntu/) jaunty universe
deb [http://mirror.its.uidaho.edu/pub/ubuntu/](http://mirror.its.uidaho.edu/pub/ubuntu/) jaunty-updates universe
deb-src [http://mirror.its.uidaho.edu/pub/ubuntu/](http://mirror.its.uidaho.edu/pub/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.its.uidaho.edu/pub/ubuntu/](http://mirror.its.uidaho.edu/pub/ubuntu/) jaunty multiverse
deb-src [http://mirror.its.uidaho.edu/pub/ubuntu/](http://mirror.its.uidaho.edu/pub/ubuntu/) jaunty multiverse
deb [http://mirror.its.uidaho.edu/pub/ubuntu/](http://mirror.its.uidaho.edu/pub/ubuntu/) jaunty-updates multiverse
deb-src [http://mirror.its.uidaho.edu/pub/ubuntu/](http://mirror.its.uidaho.edu/pub/ubuntu/) jaunty-updates multiverse

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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://mirror.its.uidaho.edu/pub/ubuntu/](http://mirror.its.uidaho.edu/pub/ubuntu/) jaunty-security main restricted
deb-src [http://mirror.its.uidaho.edu/pub/ubuntu/](http://mirror.its.uidaho.edu/pub/ubuntu/) jaunty-security main restricted
deb [http://mirror.its.uidaho.edu/pub/ubuntu/](http://mirror.its.uidaho.edu/pub/ubuntu/) jaunty-security universe
deb-src [http://mirror.its.uidaho.edu/pub/ubuntu/](http://mirror.its.uidaho.edu/pub/ubuntu/) jaunty-security universe
deb [http://mirror.its.uidaho.edu/pub/ubuntu/](http://mirror.its.uidaho.edu/pub/ubuntu/) jaunty-security multiverse
deb-src [http://mirror.its.uidaho.edu/pub/ubuntu/](http://mirror.its.uidaho.edu/pub/ubuntu/) jaunty-security multiverse
deb [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) jaunty main


# Project Neon: Amarok Nightly and KDE Nightly
# deb [http://ppa.launchpad.net/project-neon/ppa/ubuntu](http://ppa.launchpad.net/project-neon/ppa/ubuntu) jaunty main
# deb-src [http://ppa.launchpad.net/project-neon/ppa/ubuntu](http://ppa.launchpad.net/project-neon/ppa/ubuntu) jaunty main


# Medibuntu (ex PLF)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

---

### Post by taurus on 2009-05-04
It's probably best to comment out those 3rd party repos when you want to upgrade from one release to the next.  Therefore, put a # in front of the last two lines, Medibuntu's repos and the compiz from ppa.launchpad.net too.

---

### Post by prickee on 2009-05-04
I did the above suggested...no change...still researching..

---

### Post by taurus on 2009-05-04
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by prickee on 2009-05-04
sudo apt-get dist-upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  ffmpeg mplayer
The following packages will be upgraded:
  amsn
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 3376kB of archives.
After this operation, 10.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  amsn
Install these packages without verification [y/N]? y
Get:1 [http://repoubuntusoftware.info](http://repoubuntusoftware.info) intrepid/all amsn 0.97.20070524-1 [3376kB]
Fetched 3376kB in 1s (2267kB/s)
(Reading database ... 248132 files and directories currently installed.)
Preparing to replace amsn 0.97.2~debian-2ubuntu2 (using .../amsn_0.97.20070524-1_i386.deb) ...
Unpacking replacement amsn ...
dpkg: error processing /var/cache/apt/archives/amsn_0.97.20070524-1_i386.deb (--unpack):
 trying to overwrite `/usr/share/doc/amsn/READMEru', which is also in package amsn-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/amsn_0.97.20070524-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by taurus on 2009-05-04
Clean out the cache.

```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```
Otherwise, go into System -> Administration -> Software Sources and switch to another server.

---

### Post by prickee on 2009-05-05
I did the above mentioned and i seem to be getting this on a consistent basis

Unpacking replacement amsn ...
dpkg: error processing /var/cache/apt/archives/amsn_0.97.20070524-1_i386.deb (--unpack):
 trying to overwrite `/usr/share/doc/amsn/READMEru', which is also in package amsn-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/amsn_0.97.20070524-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


It won't overwrite the package? Is there a way to just ignore installation or upgrade of amsn since I don't even use it?
Oh and I changed to Main Server is Software Sources.

---

