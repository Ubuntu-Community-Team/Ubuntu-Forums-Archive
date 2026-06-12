---
title: "Can't use UpdateManager/Synaptic/apt-get install because of Broken Packages"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by xaxa on 2009-02-19
Hi guys,
Newbie post starts:
I've just installed **Ubuntu 8.04 - the Hardy Hero** and I'm having a serious problem when trying to launch UpdateManager or Synaptic or apt-get install. I'm always having the same package error, which is:

 ```
Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

Here's what I already tried to fix this (based on what I found on the net):
[LIST]
[*]Synaptic -> edit -> fix broken packages (didn't work)

[*]Launch update Manager: it displays an error message "Couldn't initialize the package information.... E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

[*]go su, then run  apt-get -f dist-upgrade, here's the output:
```
r# apt-get -f dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  debhelper: Depends: html2text but it is not installed
             Depends: po-debconf but it is not installed
  dpkg-dev: Depends: patch (>= 2.2-1) but it is not installed
            Depends: libtimedate-perl but it is not installed
  perl: Depends: perl-base (= 5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.4 is installed
        Depends: perl-modules (>= 5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.4 is installed
  rpm: Depends: libbeecrypt6 but it is not installed
       Depends: libpopt0 (>= 1.14) but 1.10-3build1 is installed
       Depends: librpm4.4 (>= 4.4) but it is not installed
       Depends: librpm4.4 (< 4.5) but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

[*]tried  apt-get -f install, same output as above.

[*]tried to manually install theses broken packages, here's what happens:
```
apt-get install html2text
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  debhelper: Depends: po-debconf but it is not going to be installed
  dpkg-dev: Depends: patch (>= 2.2-1) but it is not going to be installed
            Depends: libtimedate-perl but it is not going to be installed
  perl: Depends: perl-base (= 5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.4 is to be installed
        Depends: perl-modules (>= 5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.4 is to be installed
  rpm: Depends: libbeecrypt6 but it is not going to be installed
       Depends: libpopt0 (>= 1.14) but 1.10-3build1 is to be installed
       Depends: librpm4.4 (>= 4.4) but it is not going to be installed
       Depends: librpm4.4 (< 4.5) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
and it still says debhelper depends on html2text when I run a new apt-get -f install
[/LIST]

I don't know if there is a link with the fact that each time I try to launch firefox I got an error message from it saying another instance of ff is already running and I first need to close it, BUT, when I launch it from the profilemanager ("sudo firefox -profilemanager" in the console) it works...

Is there any chance I can fix this without having to reinstall ubuntu?
(if so I'm a bit pissed because I installed it something like 3 days ago and its already 'broken', whereas I'm doing computer sciences studies and on the ubuntu website it says 'Linux for Human Beings!' :')

THANKS very much for your help pros!

---

### Post by taurus on 2009-02-19
Why don't you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by xaxa on 2009-02-19
here it is:
```

cat /etc/apt/sources.list

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

```

---

### Post by taurus on 2009-02-19
What's the output of this command from a terminal?

```
sudo apt-get update
```

---

### Post by xaxa on 2009-02-19
Ok here it is:
```

sudo apt-get update
[sudo] password for xavier: 
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://security.ubuntu.com hardy-security/main Packages         
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done


```

---

### Post by taurus on 2009-02-20
And

```
sudo apt-get upgrade
```

---

### Post by xaxa on 2009-02-20
sudo apt-get upgrade:
```

Reading package lists...

Building dependency tree...

Reading state information...

You might want to run `apt-get -f install' to correct these.

The following packages have unmet dependencies:
  
debhelper: Depends: html2text but it is not installed
             
Depends: po-debconf but it is not installed
  
dpkg-dev: Depends: patch (>= 2.2-1) but it is not installed
            
Depends: libtimedate-perl but it is not installed
  
perl: Depends: perl-base (= 5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.4 is installed
        
Depends: perl-modules (>= 5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.4 is installed
  
rpm: Depends: libbeecrypt6 but it is not installed
       
Depends: libpopt0 (>= 1.14) but 1.10-3build1 is installed
       
Depends: librpm4.4 (>= 4.4) but it is not installed
       
Depends: librpm4.4 (< 4.5) but it is not installed

```

sudo apt-get -f upgrade:
```

Reading package lists...

Building dependency tree...

Reading state information...

Correcting dependencies... failed.

The following packages have unmet dependencies:
  
debhelper: Depends: html2text but it is not installed
             
Depends: po-debconf but it is not installed
  
dpkg-dev: Depends: patch (>= 2.2-1) but it is not installed
            
Depends: libtimedate-perl but it is not installed
  
perl: Depends: perl-base (= 5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.4 is installed
        
Depends: perl-modules (>= 5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.4 is installed
  
rpm: Depends: libbeecrypt6 but it is not installed
       
Depends: libpopt0 (>= 1.14) but 1.10-3build1 is installed
       
Depends: librpm4.4 (>= 4.4) but it is not installed
       
Depends: librpm4.4 (< 4.5) but it is not installed

```

sudo apt-get install
```

Reading package lists...

Building dependency tree...

Reading state information...

You might want to run `apt-get -f install' to correct these.

The following packages have unmet dependencies:
  
debhelper: Depends: html2text but it is not installed
             
Depends: po-debconf but it is not installed
  
dpkg-dev: Depends: patch (>= 2.2-1) but it is not installed
            
Depends: libtimedate-perl but it is not installed
  perl: 
Depends: perl-base (= 5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.4 is installed
        
Depends: perl-modules (>= 5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.4 is installed
  
rpm: Depends: libbeecrypt6 but it is not installed
       
Depends: libpopt0 (>= 1.14) but 1.10-3build1 is installed
       
Depends: librpm4.4 (>= 4.4) but it is not installed
       
Depends: librpm4.4 (< 4.5) but it is not installed


```

sudo apt-get -f install
```

Reading package lists...

Building dependency tree...

Reading state information...

Correcting dependencies... failed.

The following packages have unmet dependencies:
  
debhelper: Depends: html2text but it is not installed
             
Depends: po-debconf but it is not installed
  
dpkg-dev: Depends: patch (>= 2.2-1) but it is not installed
            
Depends: libtimedate-perl but it is not installed
  
perl: Depends: perl-base (= 5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.4 is installed
        
Depends: perl-modules (>= 5.10.0-11.1ubuntu2.2) but 5.8.8-12ubuntu0.4 is installed
 
 rpm: Depends: libbeecrypt6 but it is not installed
       
Depends: libpopt0 (>= 1.14) but 1.10-3build1 is installed
       
Depends: librpm4.4 (>= 4.4) but it is not installed
       
Depends: librpm4.4 (< 4.5) but it is not installed


```

---

