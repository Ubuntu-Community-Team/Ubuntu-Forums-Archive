---
title: "Ubuntu Throwing Errors When Checking For Updates"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by RookieUbuntuUser58 on 2009-02-18
Here is 2 screenshots of the errors I get everytime I check for updates. I have a feeling its preventing me from getting major updates. Any ideas how to fix this?

---

### Post by RookieUbuntuUser58 on 2009-02-18
Here is the result of my ```
cat /etc/apt/sources.list
```:

```
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
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
deb http://ppa.launchpad.net/tualatrix/ubuntu intrepid main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu intrepid main

```

---

### Post by RookieUbuntuUser58 on 2009-02-18
Bump I really need help with this, its preventing me from updating my Ubuntu install.

---

### Post by Tiler on 2009-02-18
I'm getting it too with UNR Hardy.  I didn't convert from vanilla, I had to install from the IMG on a Dell Mini-12.  Looking for a place to find the sources UNR should have installed.

I'm getting references to lpia/packages in the error but nothing shows up in the sources.list indicating it's looking there.

---

### Post by RookieUbuntuUser58 on 2009-02-18
Afternoon bump for some help.


Surprising no one here has posted a solution yet, usually I could depend upon Ubuntu forums for some help.

---

### Post by oldos2er on 2009-02-18
Have you tried a different server? System, Administration, Software Sources, Download from... Other, Select Best Server.

---

### Post by RookieUbuntuUser58 on 2009-02-18
Thanks for the help but now I get this error instead.

---

### Post by oldos2er on 2009-02-19
That's just a warning; it can be safely ignored.

---

