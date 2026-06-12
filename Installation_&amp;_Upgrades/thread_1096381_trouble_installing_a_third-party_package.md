---
title: "trouble installing a third-party package"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by 0505 on 2009-03-14
Hi,

I'm trying to install a program from a third-party package repository, and I'm getting an error message: 

The following packages have unmet dependencies:
  libgeant4-dev: Depends: libxmu-dev which is a virtual package.
                 Depends: libxt-dev which is a virtual package.
                 Depends: libx11-dev which is a virtual package.
                 Depends: libxaw7-dev which is a virtual package.
                 Depends: zlib1g-dev which is a virtual package.
  lesstif2-dev: Depends: libice-dev which is a virtual package.
                Depends: libsm-dev which is a virtual package.
                Depends: libx11-dev which is a virtual package.
                Depends: libxext-dev which is a virtual package.
                Depends: libxp-dev which is a virtual package.
                Depends: libxt-dev which is a virtual package.
                Depends: libxrender-dev which is a virtual package.
                Depends: libxft-dev which is a virtual package.
                Depends: libfontconfig1-dev which is a virtual package.
                Depends: libfreetype6-dev which is a virtual package.
  libg4opengl-dev: Depends: libglu1-mesa-dev which is a virtual package. or
                            libglu-dev which is a virtual package.
                   Depends: libgl1-mesa-dev which is a virtual package. or
                            libgl-dev which is a virtual package.

after which it refuses to download the program. Do I need to download these packages it lists? I have gutsy 7.10. Any help would be appreciated!

---

### Post by taurus on 2009-03-14
What are you trying to install and did you add the 3rd-party repo to your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by 0505 on 2009-03-14
I'm trying to install geant4. I don't know what a 3rd party repo is, but I did add the lines: 

deb [http://lcg-heppkg.web.cern.ch/lcg-heppkg/debian](http://lcg-heppkg.web.cern.ch/lcg-heppkg/debian) gutsy hep
deb-src [http://lcg-heppkg.web.cern.ch/lcg-heppkg/debian](http://lcg-heppkg.web.cern.ch/lcg-heppkg/debian) gutsy hep

and uncommented the lines: 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

but everything else in the /etc/apt/sources.list file is still commented.

---

### Post by taurus on 2009-03-14
Can you post the whole file?

---

### Post by 0505 on 2009-03-14
The whole "etc/apt/sources.list" file? Here it is:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the
## Ubuntu team, and may not be under a free licence. Please satisfy
## yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu
## security
## team.
# Line commented out by installer because it failed to verify:
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main re$
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted univ$
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted $

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

deb [http://lcg-heppkg.web.cern.ch/lcg-heppkg/debian](http://lcg-heppkg.web.cern.ch/lcg-heppkg/debian) gutsy hep
deb-src [http://lcg-heppkg.web.cern.ch/lcg-heppkg/debian](http://lcg-heppkg.web.cern.ch/lcg-heppkg/debian) gutsy hep

---

### Post by taurus on 2009-03-14
> **0505 said:**
> The whole "etc/apt/sources.list" file? Here it is:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the
## Ubuntu team, and may not be under a free licence. Please satisfy
## yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu
## security
## team.
# Line commented out by installer because it failed to verify:
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

**[COLOR="Red"]#[/COLOR]**deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main re$
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
**[COLOR="Blue"]#[/COLOR]** deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
**[COLOR="Blue"]#[/COLOR]** deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
**[COLOR="Blue"]#[/COLOR]** deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
**[COLOR="Blue"]#[/COLOR]** deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
**[COLOR="Blue"]#[/COLOR]** deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted univ$
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted $

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
**[COLOR="Blue"]#[/COLOR]** deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
**[COLOR="Blue"]#[/COLOR]** deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
**[COLOR="Blue"]#[/COLOR]** deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
**[COLOR="Blue"]#[/COLOR]** deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

deb [http://lcg-heppkg.web.cern.ch/lcg-heppkg/debian](http://lcg-heppkg.web.cern.ch/lcg-heppkg/debian) gutsy hep
deb-src [http://lcg-heppkg.web.cern.ch/lcg-heppkg/debian](http://lcg-heppkg.web.cern.ch/lcg-heppkg/debian) gutsy hep

Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove those #'s in blue.  Once done, save it and run

```
sudo apt-get update
sudo apt-get upgrade
```
Now, see if you can install geant4 this time.

p.s.  Put a # in front of the line for cdrom to comment it out.

---

### Post by 0505 on 2009-03-14
It worked! Thank you so much for your help!

---

