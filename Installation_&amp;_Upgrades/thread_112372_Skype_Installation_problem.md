---
title: "Skype Installation problem"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by noeluylee on 2006-01-04
I am trying to install skype on my Ubuntu with Kubuntu-desktop, KDE 

I downloaded the skype_1.2.0.18-1_i386.deb at [www.skype.com](www.skype.com) upon installing it I encounter error... see below.

Desktop  skype_1.2.0.18-1_i386.deb
noel@Noel:~$ sudo dpkg -i skype_1.2.0.18-1_i386.deb
(Reading database ... 109488 files and directories currently installed.)
Preparing to replace skype 1.2.0.18-1 (using skype_1.2.0.18-1_i386.deb) ...
Unpacking replacement skype ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt3c102-mt (>= 3:3.3.3.2); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype
noel@Noel:~$ sudo apt-get install libqt3c102-mt
Reading package lists... Done
Building dependency tree... Done
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libqt3-mt
E: Package libqt3c102-mt has no installation candidate
noel@Noel:~$

I cannot find the skype on synaptic.

Hope you could help.

TY

---

### Post by noeluylee on 2006-01-04
sorry -- here's my sources.list for reference

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by patrick295767 on 2006-01-04
From : [http://www.skype.com/products/skype/linux/](http://www.skype.com/products/skype/linux/)
u could unpack this : Static binary tar.bz2 with Qt 3.2 compiled in (10.4 MB)
  
then, unpack for instance with mc 
(midnight commander)
  
then, ./skype should work ... 
U can then place skype at another specific location and so on ... 

Greetz'

---

### Post by noeluylee on 2006-01-04
Where should I unpack the Static binary tar.bz2? what location? :)

can I just unpack it using tar -xvcf ?:)

TY

---

