---
title: "[SOLVED] Unpet Dependencies. Audacious"
date: 2008-09-04
forum: General Help
---

### Post by ragflan on 2008-09-04
Hi, I'm under Hardy Heron. And when I try to install Audacious through a Terminal using **sudo apt-get install audacious**, I get the following error message: 

The following packages have unmet dependencies: 
audacious: Depends: audacious-plugins but it is not going to be installed
E: Broken packages.

When I open Synpatic Package Manager and select Edit -> Fix Broken Packages, nothing happens so I cannot click apply. 

How do I resolve this problem?

---

### Post by ragflan on 2008-09-04
What a dolt. I wrote the title as unpet. Sorry!

---

### Post by ragflan on 2008-09-04
When I try and install Audacious-Plugins, I get the same error:

The following packages have unmet dependencies:
audacious-plugins: Depends: audacious (<1.9) but 1:1.2.2-4ubuntu1 is to be installed
E: Broken Packages.

Anyone know what's wrong?

---

### Post by ragflan on 2008-09-04
Anyone? Haha, I keep checking every minute because I'm trying to try Google Chrome and I have unmet dependencies for libnss3-dev as well.

---

### Post by ragflan on 2008-09-04
Someone? Anyone? I dont wanna relog into Windows just to try Google Chrome, when there are installation instructions for the Linux version... Very excited!

---

### Post by ragflan on 2008-09-04
Hey guys, I'm having multiple unmet dependency problems. Any help would be appreciated. Here's a copy of my Sources.list file:


```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security multiverse

deb http://ppa.launchpad.net/awn-core/ubuntu hardy main #AWN
deb http://ppa.launchpad.net/do-core/ubuntu hardy main #GNOME Do
deb http://ppa.launchpad.net/banshee-team/ubuntu hardy main #Banshee
deb http://download.skype.com/linux/repos/debian stable non-free #Skype
deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock #Cairo Dock
deb http://ppa.launchpad.net/compiz/ubuntu hardy main #Compiz Fusion

deb http://ppa.launchpad.net/tualatrix/ubuntu hardy main #Ubuntu Tweak
deb http://ppa.launchpad.net/gilir/ubuntu hardy main #Screenlets
deb http://ppa.launchpad.net/gscrot/ubuntu hardy main #GScrot
deb http://ppa.launchpad.net/daou/ubuntu hardy main
deb-src http://ppa.launchpad.net/daou/ubuntu hardy main
deb http://packages.medibuntu.org/ hardy free non-free
# deb-src http://packages.medibuntu.org/ hardy free non-free
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://ppa.launchpad.net/exaile-devel/ubuntu hardy main

deb http://ppa.launchpad.net/thjaeger/ubuntu hardy main
deb-src http://ppa.launchpad.net/thjaeger/ubuntu hardy main

deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main

```

---

### Post by oldos2er on 2008-09-04
> **ragflan said:**
> Someone? Anyone? I dont wanna relog into Windows just to try Google Chrome, when there are installation instructions for the Linux version... Very excited!

 There is no Linux version of Chrome yet.

 For the dependency issues, check your Software Sources and make sure all repositories are enabled. To fix broken packages, type "sudo aptitude install -f" in a terminal.

---

### Post by ragflan on 2008-09-04
Oh, I read the Google Chromium website and there's some developmental release or something for Linux. So I was just trying that. [http://dev.chromium.org/](http://dev.chromium.org/) I logged into Windows and tested it. Epiphany is faster!

---

### Post by dale.novak on 2008-09-05
Hello,

I also am using ubuntu 8.04.1 and I can't "sudo apt-get install audacious".  I get the dreaded "The following packages have unmet dependencies:
  audacious: Depends: audacious-plugins but it is not going to be installed
E: Broken packages" error message.

I have tried to "sudo aptitude install -f" in a terminal to no avail.

Also, how come this thread is marked as solved when the OP did not respond with a "thanks it worked"?

---

### Post by funkameleon on 2008-09-06
I have the same problem:

The following packages have unmet dependencies:
  audacious: Depends: audacious-plugins but it is not going to be installed
E: Broken packages

---

