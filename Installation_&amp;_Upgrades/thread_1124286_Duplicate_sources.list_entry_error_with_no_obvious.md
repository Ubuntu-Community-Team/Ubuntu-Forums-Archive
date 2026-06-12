---
title: "Duplicate sources.list entry error with no obvious duplicate"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by vussvillem on 2009-04-13
Hey!

I'm using Ubuntu 8.04. When I do "sudo apt-get update" I get:

> W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_hardy_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

I do not find any duplicate in my sources list; and I can not fix the problem by: 1) apt-get update; 2) apt-get clean; 3) apt-get autoremove; 4) apt-get check; 5) sudo apt-get -f install

What I'm missing in here?

My sources.list:
# deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

##Virtualbox non-free version
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free

## Bibus
deb [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./
deb-src [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./

deb [http://ppa.launchpad.net/lxde/ubuntu](http://ppa.launchpad.net/lxde/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/lxde/ubuntu](http://ppa.launchpad.net/lxde/ubuntu) hardy main

---

### Post by Aubergines on 2009-04-13
As a wild guess some of the files in /var/lib/apt/lists/ contain the same information (you can check the file in there and see if theres any with a matching file size and take a look) so while the entries in your source.list looks different some could be picking up the same thing. That's a guess btw :P

Did you try an apt-get update? It could be some funkyness with the repositories.

---

### Post by vussvillem on 2009-04-13
Yes, I've tried apt-get update without any success.

Two files seem to have the same information in them, I mean they list the same packages (I did not look up all the way through the files - because they're huge - but at least the beginning and the end are the same):

1)ee.archive.ubuntu.com_ubuntu_dists_hardy-updates_restricted_binary-i386_Packages 
2)security.ubuntu.com_ubuntu_dists_hardy-security_restricted_binary-i386_Packages

Sorry for being stupid about the architecture and functioning of package source system, however, I guess the above mentioned files should be very similar, shouldn't they?

Just in case I will post here my /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_hardy_partner_b inary-i386_Packages file as a text file just because initial error message refers to that file :)

---

### Post by cajunlibra on 2009-05-16
I'm having the same problem.  Here is my sources.list:

archive.ubuntu.com/ubuntu is where I'm getting the error. There are a few that look really similar but I'm not sure.

Thanks

```
## UBUNTU REPOSITORIES
deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe #Added by software-properties

deb-src http://archive.canonical.com/ubuntu jaunty partner

# deb http://ppa.launchpad.net/ubuntume.team/ubuntu jaunty main # Ubuntu Muslim Edition
# deb-src http://ppa.launchpad.net/ubuntume.team/ubuntu jaunty main # Ubuntu Muslim Edition
## +++ Backports & Proposed (Ubuntu Unstable) +++
deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-backports restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed restricted multiverse
## +++ Source Repositories +++
# deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu jaunty main
deb http://archive.ubuntu.com/ubuntu/ jaunty restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates restricted
##Universe
## Multiverse
## Backports
deb http://archive.ubuntu.com/ubuntu/ jaunty-backports restricted multiverse
## Canonical Partner Repository
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner
deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
## PLF REPOSITORY
## +++ Medibuntu +++
deb http://packages.medibuntu.org/ jaunty free non-free
#deb http://deb.mulx.net/ jaunty main

# deb http://download.tuxfamily.org/swiftweasel jaunty multiverse
deb http://streaming.stat.iastate.edu/CRAN//bin/linux/ubuntu jaunty/
deb http://dl.google.com/linux/deb/ stable non-free
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/awn-testing/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/fta/ubuntu jaunty main
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu jaunty main
deb http://www.estamos.de/download/apt stable main
# deb http://ppa.launchpad.net/frederik-elwert/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/frederik-elwert/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/synce/ubuntu jaunty main
deb http://ppa.launchpad.net/phylu/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/phylu/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/synce/ubuntu jaunty main
```

---

### Post by lswb on 2009-05-16
Try looking in any files in /etc/apt/sources.list.d
The files in this directory are read & used just like, and in addition to /etc/apt/sources.list by apt, synaptic, or other package managers.

---

### Post by cajunlibra on 2009-05-16
Um, there's only one file in that directory: jockey.list and it has only one line pointing to openprinting.org


Is there anything else I can do?

---

### Post by vussvillem on 2009-05-18
Problem solved: There was a duplication in the Software Sources (System -> Administration -> Software Sources) in the Third-Party Software tab although the /etc/apt/sources.list file was correct. I have no idea, why.

Thanks to user Kostkon [http://ubuntuforums.org/showthread.php?p=6078633](http://ubuntuforums.org/showthread.php?p=6078633)

---

