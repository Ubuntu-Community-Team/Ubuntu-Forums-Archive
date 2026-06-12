---
title: "kernel sources"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by jamieb22 on 2009-10-12
Hi There

I have a fresh install of Ubuntu 8.04.1 Hardy server and am trying to install the Asterisk Dahdi package which requires the kernel sources to be installed.

When I run the Dahdi package make, I receive:

You do not appear to have the sources for the 2.6.24-19-server kernel installed.

Thinking this would be easy, I ran 

sudo apt-get install linux-source

However, the above command appears to install the wrong kernel 2.6.24-generic 

Here are my machine details:

Linux ubuntu820051.aspadmin.net 2.6.24-19-server #1 SMP Wed Jun 18 14:44:47 UTC 2008 x86_64 GNU/Linux

Here is my sources.list file:

c/apt/sources.list
#
# deb cdrom:[Ubuntu-Server 8.04.1 _Hardy Heron_ - Release amd64 (20080701)]/ hardy main restricted

#deb cdrom:[Ubuntu-Server 8.04.1 _Hardy Heron_ - Release amd64 (20080701)]/ hardy main restricted
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


Any help would be much appreciated.

---

### Post by Ravernomina on 2009-10-12
try also adding Sever to that command as well.. might work

---

### Post by zeronothing on 2009-10-12
if you are building packages make sure you download the "build-essentials" package from the ubuntu repository. If your on the command-line just do:

sudo apt-get install build-essential

when you install that package I believe it installs the kernel-source but if that doesn't work try installing

sudo apt-get install linux-source

---

### Post by jamieb22 on 2009-10-12
thanks for your suggestions. as it happened, i figured it out on my own. 

the reason is, as of Hardy, you can no longer go:

sudo apt-get build-dep linux-source
apt-get source linux-source

You have to go:

sudo apt-get build-dep linux-ubuntu-modules-$(uname -r)
apt-get source linux-ubuntu-modules-$(uname -r)

---

### Post by zeronothing on 2009-10-12
sweet, I'm glad you figured it.

---

