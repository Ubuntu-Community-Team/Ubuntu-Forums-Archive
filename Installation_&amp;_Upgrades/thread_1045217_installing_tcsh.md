---
title: "installing tcsh"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by xie_jiabao on 2009-01-20
Dear all,

I have a dual boot windows xp-ubuntu linux 8.04.1 intel core2 duo laptop. I am trying to install the protein crystallography software CNS on linux. But this installation requires the execution of a tcsh script. I have tried using apt-get (sudo apt-get install tcsh/ sudo -i apt-get install tcsh)to install tcsh but this does not work. I cannot use synaptic package manager to download and install tcsh and required dependencies since I can only connect to the internet through windows at the moment and not through linux (my internet data card is compatible only with windows). I have manually downloaded the following files from the internet.
a) tcsh_6.14.00.orig.tar.gz
b) glibc_2.4.orig.tar.gz
c) libncurses5 (>= 5.4-5) 

Will these files suffice for tcsh installation? What is the easiest way to install these packages? I am new to ubuntu and would appreciate any help in this regard.
Thanks in advance,
Xie

---

### Post by taurus on 2009-01-20
What is the error message when you try to install tcsh with apt-get?

Otherwise, post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

The tcsh_6.14.00.orig.tar.gz is the source so you need to build it for your machine.

---

### Post by xie_jiabao on 2009-01-20
Thanks for responding to my query. When I type sudo apt-get install tcsh I get the following message.

Reading package lists...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package tcsh

Upon typing sudo -i apt-get install tcsh I see the following message
/usr/bin/apt-get: /usr/bin/apt-get: cannot execute binary file

The following are the contents of /etc/apt/sources.list

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse 

Xie

---

