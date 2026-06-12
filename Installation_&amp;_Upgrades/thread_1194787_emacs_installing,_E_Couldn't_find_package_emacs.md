---
title: "emacs installing, E: Couldn't find package emacs"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by mdoroudi on 2009-06-23
Hi,
I used to have the older versions of Ubuntu and never had problem with this.
I am trying to install emacs so i do

$sudo apt-get install emacs

then i get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package emacs

I also trying 
$sudo apt-get install emacs21
$sudo apt-get install emacs-snapshot-gtk

and pretty much everything i could find on google, but I keep getting the same error message.

Thanks! 
Mina

---

### Post by ad_267 on 2009-06-23
Don't look on google for packages, but yes there should be an emacs package. You can search for packages using "apt-cache search search_term" or "apt-cache search -n search_term" to search only the package names. You can also use the Synaptic package manager from System - Administration - Synaptic Package Manager.

Have you only just installed Ubuntu? You have to do a "sudo apt-get update" to update your package list first.

---

### Post by kingzleshe on 2009-06-23
try
 
sudo apt-get install Emacs  
 
 
good luck

---

### Post by dsavi on 2009-06-23
Packages always have lowercase names. I would also say sudo apt-get update.
And I believe it may be called emacs22/emacs-22.

If none of the above works, can you post the contents of your /etc/apt/sources.list?

---

### Post by mdoroudi on 2009-06-23
Hi,
I did all those suggestions and none worked.
$sudo apt-get install Emacs  
$sudo apt-get install emacs22
$sudo apt-get install emacs-22

they all give me the same error.

I recently installed this Ubuntu 7.04, before I had the older version and emacs was fine on there. 
I also have done $sudo apt-get update, and also just did it again, and it didn't help.

as for System - Administration - Synaptic Package Manager, it's weird
becaue it barely has any thing in it. My older Ubuntu had plenty and plenty of applications in there, which i could check or uncheck to be installed. but this new one only has some limited applications which are all installed. and emacs is not there, I also did a search for emacs and got nothing. Anybody knows how to get it act like the older versions of Ubuntu? to show more packages? 

I also did 
$apt-cache search emacs 
$apt-cache search emacs22 
...
and they return nothing

The content of /etc/apt/sources.list is:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

Thanks for the help! :)

---

### Post by ad_267 on 2009-06-23
Support for 7.04 ended October last year, so I'm guessing the software repositories are no longer available. You'll have to upgrade to a newer version if you want to be able to install applications. The latest is 9.04 which is vastly improved over 7.04.

See [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

---

### Post by serxyz on 2009-06-25
Have you tried to uncomment the lines in "source.list" that allow adding software from 'universe' repository? 

================================
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
================================

I had the same problem (E: Couldn't find package emacs) using DapperDrake and it got fixed once I uncommented those lines. So that you get:

Hope that helps.

Regards,

S.

---

