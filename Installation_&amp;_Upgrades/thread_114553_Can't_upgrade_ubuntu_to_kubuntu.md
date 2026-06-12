---
title: "Can't upgrade ubuntu to kubuntu"
date: 2006-01-08
forum: Installation &amp; Upgrades
---

### Post by paranoia on 2006-01-08
Alright, I just installed Ubuntu 5.10 PPC on my 800mhz iMac G4, and I decided that I'd like to run kubuntu as well. So, as per instructions, I searched for "kubuntu-install" in synaptic. Nothing. None of the kubuntu packages show up. I tried running "sudo apt-get install kubuntu-install", but it returns 
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kubuntu-install

```
So I'm stumped... I searched the forum but didn't see anyone with the same problem... Any help?
Thanks in advance.

---

### Post by matthew on 2006-01-08
You got the package name wrong, that's all. The correct name is kubuntu-desktop

---

### Post by paranoia on 2006-01-08
Whoopsies... I just wrote the command wrong in my post... I actually did use apt-get install kubuntu-desktop. Thanks for the quick response... any ideas what's going on?

---

### Post by matthew on 2006-01-08
Well, it's in the main repository so it's not an issue of having the extra repositories enabled. Could you post the contents of your /etc/apt/sources.list file here and let me have a look at it? I think it's possible you only have the original installation cd enabled as a repository??

---

### Post by paranoia on 2006-01-08
I enabled the repositories, and it's working fine... Here's the unedited file. 
```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb http://ca.archive.ubuntu.com/ubuntu breezy main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://ca.archive.ubuntu.com/ubuntu breezy-updates main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://ca.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://ca.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu breezy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```
I just made a clean install... Isn't it normal to have the main repository enabled? Anyway, thanks for the help. It's much appreciated.

---

### Post by aysiu on 2006-01-08
Follow the instructions in the first link of my sig. Then ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

---

