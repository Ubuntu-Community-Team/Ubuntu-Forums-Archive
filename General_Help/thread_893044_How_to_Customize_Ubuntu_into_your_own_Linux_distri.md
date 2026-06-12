---
title: "How to Customize Ubuntu into your own Linux distribution"
date: 2008-08-17
forum: General Help
---

### Post by flouran on 2008-08-17
Hi Guys,
I was thinking of creating my own custom Ubuntu distribution. I've used Reconstructor before to customize Ubuntu 7.10; however, when I boot up my customized distribution, it drops me to a job control shell. Are there any good guides on the internet describing how I could go about customizing Ubuntu into my own, new Linux distribution (such as changing the themes, changing the LiveCD/Installer from using Ubuntu anywhere in the software to using a name of my own, and adding/removing software)? Or could anyone help me out?

Your help is greatly appreciated,
Flouran

---

### Post by UbuntuNerd on 2008-08-17
check here [http://ubuntuforums.org/showthread.php?t=852868]("http://ubuntuforums.org/showthread.php?t=852868")

---

### Post by flouran on 2008-08-18
Hi,
That was a great link, UbuntuNerd!

I also had another question to ask, which line in /etc/apt/sources.list (or is it even this file?) allows Ubuntu to download a new Operating System version (for instance, when someone is running Ubuntu 7.10, what enables his computer to discover an 8.04 update?) ?

-Flouran

---

### Post by UbuntuNerd on 2008-08-18
I think all updates are detected by the update manager and its controlled through the Software Sources control panel but I'm not 100 percent sure. Go under your "System" menu, select "Administration", and select "Software Sources." You will be prompted for your  password, once the window opens select the "Updates" tab to see some update options 

I think we need the opinion of someone who knows more about the topic!!!!

---

### Post by flouran on 2008-08-19
Here is my /etc/apt/sources.list, in case anyone is wondering:

#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by flouran on 2008-08-19
I think it is this line which enables Ubuntu to search for Operating System Version updates:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted

When I follow the link to [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu), and browse the webpage, there is a link called: [http://security.ubuntu.com/ubuntu/di...-upgrader-all/](http://security.ubuntu.com/ubuntu/di...-upgrader-all/)

What do you guys think?

---

