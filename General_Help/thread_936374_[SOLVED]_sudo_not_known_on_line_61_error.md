---
title: "[SOLVED] sudo not known on line 61 error"
date: 2008-10-02
forum: General Help
---

### Post by Mikejones23 on 2008-10-02
Well I'm new to Ubuntu so I wasn't too sure on how to fix this error. every time I try to open the the package manager or install a program it comes up with this message:

> E: Type 'sudo' is not known on line 61 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I'm not sure if I need to post this list but someone with an error similar to mine was asked to post it.

>  # deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

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
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

thanks for any help

---

### Post by Calmatory on 2008-10-02
> **Mikejones23 said:**
> Well I'm new to Ubuntu so I wasn't too sure on how to fix this error. every time I try to open the the package manager or install a program it comes up with this message:



I'm not sure if I need to post this list but someone with an error similar to mine was asked to post it.



thanks for any help

Remove the second last line which says "**sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr**" and you will be fine. :)

The problem is that the **sources.list** file is used to store addresses of repository sources. Now, you have that line in the file and the **sudo** program does not know what it means and thus the error.

---

### Post by Mikejones23 on 2008-10-02
well that was easy, thanks for the help :)

and if you don't mind I have a question while you're here, there's this burning program I use "xilisoft avi to dvd" and after I installed it , it wouldn't load the program. I have wine which seemed to work with everything else but maybe it isnt compatable with ubuntu? i'm not sure

---

### Post by Calmatory on 2008-10-02
> **Mikejones23 said:**
> well that was easy, thanks for the help :)

and if you don't mind I have a question while you're here, there's this burning program I use "xilisoft avi to dvd" and after I installed it , it wouldn't load the program. I have wine which seemed to work with everything else but maybe it isnt compatable with ubuntu? i'm not sure

So you use that "xilisoft avi to dvd" via WINE?

Not everything works under WINE, some work better, some worse. Google seems to have alot of tutorials about avi to dvd under linux, might wanna check one out. You might also get better responses by creating new thread, but I doubt that there is any better way other than WINE/tutorials on google. :|

Not to nitpick, but could you add the [SOLVED] to the tittle for others to learn? :) 

Thanks.

---

