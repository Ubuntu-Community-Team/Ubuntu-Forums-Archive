---
title: "Toshiba Satellite A135-S4666 Unable to install packages"
date: 2009-03-04
forum: Hardware
---

### Post by mulder_edu on 2009-03-04
I have a Satellite A135-S4666 that I just installed Ubuntu Intrepid on, but I am unable to install any packages from the terminal using apt-get.  It attempts to run the install, but then just says the the package was not found.  Nothing that I've tried so far will install.  Any ideas why apt-get wont work?  I'm connected to the internet through wifi.

---

### Post by taurus on 2009-03-04
Can you post the exact command that you ran and the error message?

---

### Post by mulder_edu on 2009-03-04
This is one that I tried to install... I'm baffled that it can't find build essentials, or anything else for that matter.

```
sudo apt-get install build-essential ncurses-dev gettext
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Couldn't find package build-essential
```

---

### Post by taurus on 2009-03-04
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by mulder_edu on 2009-03-04
This is the output:

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse


```

---

### Post by stchman on 2009-03-04
> **mulder_edu said:**
> I have a Satellite A135-S4666 that I just installed Ubuntu Intrepid on, but I am unable to install any packages from the terminal using apt-get.  It attempts to run the install, but then just says the the package was not found.  Nothing that I've tried so far will install.  Any ideas why apt-get wont work?  I'm connected to the internet through wifi.


Are you able to surf websites?

---

### Post by mulder_edu on 2009-03-04
I even tried enabling the restricted repositories, but that didn't do it.

---

### Post by mulder_edu on 2009-03-04
Yes, the internet works fine. My wife is checking facebook on it right now :)

---

### Post by taurus on 2009-03-04
Did you remember to run the **sudo apt-get update** first?  Post the outputs of these two commands from a terminal.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by mulder_edu on 2009-03-04
Oh, of course! Duh. Thanks. Just needed to do a sudo apt-get update. Works fine now.

---

### Post by stchman on 2009-03-05
When you enables the other repositories an update should have been performed.

---

