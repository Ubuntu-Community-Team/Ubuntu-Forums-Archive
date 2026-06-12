---
title: "can't access repositories options"
date: 2008-11-08
forum: General Help
---

### Post by AntiHeroJoe on 2008-11-08
Just upgraded to ibex and am unable to access repositories menu. I go to System > Administration > Synaptic Package Manager, then Settings > Repositories, the system tells me 'The repository information has changed. You have to click on the "Reload" button for your changes to take effect", so I click reload, wait, go to Setting > Repositories, and it tells me the same thing...over and over and over again.

Why must upgrading with ubuntu always be painful?

---

### Post by taurus on 2008-11-08
Post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by AntiHeroJoe on 2008-11-08
Thanks for the fast response

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-backports restricted main multiverse universe
# deb http://gandalfn.club.fr/ubuntu feisty motu
# deb http://download.tuxfamily.org/3v1deb feisty eyecandy
# deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

deb http://archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe
# deb http://www.danilocesar.com/ubuntu debs/
# deb http://apt.wicd.net feisty extras

# deb http://archive.canonical.com/ gutsy partner

# PulseAudio Fixes - http://ubuntuforums.org/showthread.php?p=5587712
# deb http://ppa.launchpad.net/psyke83/ubuntu hardy main
# deb-src http://ppa.launchpad.net/psyke83/ubuntu hardy main
```

---

### Post by adult swim on 2008-11-08
it looks like you have all of the ones available in the repo options except the canonical partner repos 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

---

### Post by taurus on 2008-11-08
First, close down synaptic if you have it open.  Then, see if you can upgrade your machine from a terminal with

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by AntiHeroJoe on 2008-11-08
Hello. I tried adding those two repos as well as running the two commands given. Everything seemed to go just fine, updated opera mostly, but I'm still getting the same problem. Really weird.

---

### Post by adult swim on 2008-11-08
does it display that message as soon as you open up the repo options or when you are exiting the repo options?

---

### Post by alwayshere on 2008-11-08
Open your sources.list file to add the repository:
sudo gedit /etc/apt/sources.list

---

### Post by AntiHeroJoe on 2008-11-08
So when I click Settings > Repositories, it gives me that message (to reload), and I can't get past it to get to the options

---

### Post by alwayshere on 2008-11-08
try in terminal 

sudo apt-get update

---

### Post by AntiHeroJoe on 2008-11-08
So, I restarted a few mins ago and tried a sudo apt-get update, and I got the following:

```
W: Duplicate sources.list entry http://us.archive.ubuntu.com intrepid/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_intrepid_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

Can't seem to find the duplicate in the file though

---

### Post by alwayshere on 2008-11-08
Try 
sudo gedit /etc/apt/sources.list

then see if you have  Duplicate sources if so delete one of the two then save the file and try 

sudo apt-get update

again

---

### Post by AntiHeroJoe on 2008-11-08
Can't find the duplicate. Can you spot it? I see these two lines which maybe the error is referring to:

```
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
```

but I would assume deb and deb-src are different

---

### Post by alwayshere on 2008-11-08
ok might be easier to look graphical way goto 

places 

computer

filesystem

var

lib

apt

list

---------------

now in that list folder if there is a copy the copied file should have 
a (copy) in the file name it should be fairly easy to spot

---

### Post by adult swim on 2008-11-08
here is my list which is every box in the repo options selected (including backports and proposed, if you want to leave them out you can comment them out.)  try saving your sources.list as sources.backup and then copy and save this as your sources.list
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release Candidate i386 (20081022)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse

```
and then from a terminal run ```
sudo apt-get update
```

---

### Post by Xgen on 2008-11-08
Never had that problem, but perhaps try from the start by renaming your sources.list, then go into Software Sources and checking whatever you want. Reload it and sources.list will be rebuilt - if that  works, take it from there. Nothing to lose...your renamed one can always be reinstated or info transferred from it...

---

### Post by AntiHeroJoe on 2008-11-08
Hi everyone, thanks for all your input.

I tried renaming sources.list and doing a sudo apt-get update. That worked with no error, but I still got the previous "reload" loop in the Synaptic Package Manager.

I also tried copy/paste of the sources.list provided, but the same as above. A sudo apt-get update is successful with no complaints, but still the same issue with the Synaptic Package Manager.

---

### Post by alwayshere on 2008-11-08
try 

sudo apt-get install synaptic

---

### Post by AntiHeroJoe on 2008-11-08
Tried sudo apt-get install synaptic and I get the same message. Do I need to purge before trying to install?

---

### Post by AntiHeroJoe on 2008-11-09
Please see [http://ubuntuforums.org/showthread.php?t=975887&page=4](http://ubuntuforums.org/showthread.php?t=975887&page=4) for solution

---

