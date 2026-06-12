---
title: "Syetem not upgradeing properly"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by SteveNorman on 2009-08-25
Hello all, I am running ubuntu 9.04 after an upgrade from 8.10.

I think some of my repos borked in the upgrade. I get a partial upgrade only message when I try and update things, and the only kernal that took is 2.6.28-11-generic .

How does one go about reloading all the repos needed?

also here is the error code I get when I try and reload my repos.
```
GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 778978B00F7992B0GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 91DAE98F32FFB679GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC66403D8670A035Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch http://ppa.launchpad.net/flam3/ubuntu/dists/jaunty/main/binary-i386/Packages  404 Not Found
Failed to fetch http://ppa.launchpad.net/flam3/ubuntu/dists/jaunty/main/source/Sources  404 Not Found
Failed to fetch http://ppa.launchpad.net/m-buck/ubuntu/dists/jaunty/main/binary-i386/Packages  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```


my sources.list:

```
$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nz.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nz.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://nz.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://nz.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nz.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://nz.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://nz.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://nz.archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ jaunty-security restricted main multiverse universe #Added by software-properties
deb http://nz.archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://nz.archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb http://ppa.launchpad.net/flam3/ubuntu jaunty main # disabled on upgrade to jaunty
deb-src http://ppa.launchpad.net/flam3/ubuntu jaunty main # disabled on upgrade to jaunty
deb http://ppa.launchpad.net/project-neon/ubuntu jaunty main # disabled on upgrade to jaunty
deb http://ppa.launchpad.net/m-buck/ubuntu jaunty main # disabled on upgrade to jaunty
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main

```

---

### Post by SteveNorman on 2009-08-25
now the dam thing wont stop beeping.

---

