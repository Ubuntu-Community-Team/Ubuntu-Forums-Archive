---
title: "Ubuntu to Kbuntu"
date: 2006-02-08
forum: Installation &amp; Upgrades
---

### Post by CookieOrc on 2006-02-08
Been lookin for about half an hour with no luck. Can someone point me to where these is a walkthrough or something to switch from Ubuntu to Kubuntu

Thanks

---

### Post by ssam on 2006-02-08
just install the kubuntu-desktop package in synaptic package manager. then log out, and choose kde in the session menu on the log in screen.

---

### Post by CookieOrc on 2006-02-08
The only options it is giving me is for KDE destop Enviroment and if i try to install one package it list the 5000 dependancies that cant be installed....

---

### Post by Ashish Meena on 2006-02-08
just try 
if you need just kde base then type 
apt-get install kde-base
or 
apt-get install kubuntu-desktop

---

### Post by CookieOrc on 2006-02-08
lol now here is the error
E: Couldn't find package kde-base

Where can I add the package the computer knows where to find it?

---

### Post by Ashish Meena on 2006-02-08
have u uncommented the repositories in

/etc/apt/sources.list  then try
apt-get update and again apt-get install kde-base

---

### Post by CookieOrc on 2006-02-08
This is all that is in there ... Nothing for Kubuntu  

What is the dep-scr so I can add it

> 
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
##after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe



---

