---
title: "Upgrading from 8.10 to 9.04 - Needing third party repositories"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by PVO300C on 2009-05-13
Hello all, please bare with me as I've only been running Linux for a few months now and don't know much.

I upgraded from 8.10 to 9.04 via the i386 alternate cd, as I did not have an internet connection at the time of upgrade. The upgrade wasn't complete before I finally had access to the internet, as it dowloaded 700+ MB of data during the package manager update, so I'm guessing that there was a snag when trying to upgrade from the cd..?

Anyway, now my system runs 9.04 Jaunty but my third party repositories still reference intrepid (except for the two that I edited myself).
This is the readout from <cat etc/apt/sources.list> :


# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
# deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe main multiverse restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe main multiverse restricted #Added by software-properties

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted


I commented the third party repositories that referenced intrepid after all the updates were applied, but I thought that they would automatically be disabled during the upgrade.

What can I do to fix my repositories?

---

### Post by catatonic on 2009-05-13
Ubuntu Tweak is what I use, simplifies it a bit.

---

### Post by PVO300C on 2009-05-13
> **catatonic said:**
> Ubuntu Tweak is what I use, simplifies it a bit.

Thanks for your quick response!

Will this application add third party repositories for my existing applications or will it only add repositories for the applications that it installs afterwards?

Does this application run full time or only when you load it?
The reason I ask this is that I'd rather not install more applications than what I need, as my laptop is showing it's age and I want to keep it fairly responsive.
I'm hoping there's a way it can be done without adding another application.

Besides, if I don't do things from the terminal, how will I ever become a proficient Linux user? ;)

I nonetheless appreciate your input!

---

### Post by catatonic on 2009-05-13
> **PVO300C said:**
> Thanks for your quick response!

Will this application add third party repositories for my existing applications or will it only add repositories for the applications that it installs afterwards?

Does this application run full time or only when you load it?
The reason I ask this is that I'd rather not install more applications than what I need, as my laptop is showing it's age and I want to keep it fairly responsive.
I'm hoping there's a way it can be done without adding another application.

Besides, if I don't do things from the terminal, how will I ever become a proficient Linux user? ;)

I nonetheless appreciate your input!

It will only add for applications you install through it (I believe), but it has a simplified source editor that I prefer. It will not run full time it only runs when you load it. I'm still a newbie myself, but I have found editing my sources was much easier through ubuntu tweak.

[http://ubuntu-tweak.com/about](http://ubuntu-tweak.com/about)

---

### Post by PVO300C on 2009-10-30
Sorry, but I had forgotten this thread... this was fixed by, iirc, commenting all of the intrepid and cd-rom sources and uncommenting the jaunty sources, then doing an apt-get update.

Again, this is from my memory of the events, as it's been a while... I'll try to follow up faster next time, sorry!

---

