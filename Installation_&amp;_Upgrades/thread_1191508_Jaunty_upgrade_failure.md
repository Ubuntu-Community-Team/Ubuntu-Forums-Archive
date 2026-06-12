---
title: "Jaunty: upgrade failure"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2009-06-19
Hi,
I'm on Kubuntu Jaunty (9.04). During the last SEVERAL updates (with reboots between), I've got the following failure message:
"/etc/init.d/mdadm: 77: TERM: parameter not set invoke-rc.d: initscript mdadm, action "start" failed. "

How can I fix my problem?
Enclosed below find a copy of my sources.list.

Best Regards,

Michael Badt

-----------copy of my sources list-------------
# deb cdrom:[Kubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to                        
# newer versions of the distribution.                                                            

deb [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty main restricted
deb-src [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty-updates main restricted
deb-src [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any  
## review or updates from the Ubuntu security team.                        
deb [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty universe                     
deb-src [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty universe                 
deb [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty-updates universe             
deb-src [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty-updates universe         

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty multiverse
deb-src [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty multiverse
deb [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty-updates multiverse
deb-src [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty-security main restricted
deb-src [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty-security main restricted
deb [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty-security universe
deb-src [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty-security universe
deb [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty-security multiverse
deb-src [http://ubuntu.fastbull.org/ubuntu/](http://ubuntu.fastbull.org/ubuntu/) jaunty-security multiverse

# Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

#wine
#deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
#deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

#medibuntu
## Medibuntu - Ubuntu 9.04 "jaunty jackalope"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
------------end of sources.list------------

---

