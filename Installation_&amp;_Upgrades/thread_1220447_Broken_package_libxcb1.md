---
title: "Broken package libxcb1"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by map7 on 2009-07-22
I'm trying to install libgtk2.0-dev as it's a dependency for a package I'm trying to compile.

I'm running Ubuntu 9.04 32bit.

Here is what happens when I try and install it:
```

$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.6.4-6.1) but it is not going to be installed
                 Depends: libx11-dev (>= 2:1.0.0-6) but it is not going to be installed
                 Depends: libxext-dev (>= 1:1.0.1-2) but it is not going to be installed
                 Depends: libxinerama-dev (>= 1:1.0.1-4.1) but it is not going to be installed
                 Depends: libxi-dev (>= 1:1.0.1-4) but it is not going to be installed
                 Depends: libxrandr-dev (>= 1:1.2.99) but it is not going to be installed
                 Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxfixes-dev (>= 1:3.0.0-3) but it is not going to be installed
                 Depends: libxcomposite-dev (>= 1:0.2.0-3) but it is not going to be installed
                 Depends: libxdamage-dev (>= 1:1.0.1-3) but it is not going to be installed
E: Broken packages
```


I've narrowed it down to libxcb1-dev and it requires one package which cannot be reinstalled for some reason.

```
$ sudo apt-get install libxcb1-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxcb1-dev: Depends: libxcb1 (= 1.1.93-0ubuntu3.1) but 1.1.93-0ubuntu4 is to be installed
E: Broken packages

```
How do I fix this problem? can it be done without rebooting?

---

### Post by Partyboi2 on 2009-07-23
Hi, open a terminal and try fixing the broken package with
```
sudo apt-get -f install
``` can you also post your sources.list as well
```
cat /etc/apt/sources.list
```

---

### Post by sb08786734` on 2009-07-23
Same issue, running ubuntu 9.04, trying to install libqt4-dev but it fails.
sudo apt-get install -f libqt4-dev
```

$ sudo apt-get install -f libqt4-dev Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libqt4-dev: Depends: libxext-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
              Depends: libxrandr-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
              Depends: libxmu-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
              Depends: libx11-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
              Depends: libxt-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
              Depends: libxrender-dev but it is not going to be installed
              Depends: libxcursor-dev but it is not going to be installed
              Depends: libxinerama-dev but it is not going to be installed
              Depends: libxi-dev but it is not going to be installed
              Depends: libglu1-xorg-dev but it is not going to be installed or
                       libglu1-mesa-dev but it is not going to be installed or
                       libglu-dev
              Depends: libxft-dev but it is not going to be installed
              Recommends: libqt4-opengl-dev (= 4.5.0-0ubuntu4) but it is not going to be installed
E: Broken packages

```sudo apt-get -f install libxcb1-dev
```
$ sudo apt-get -f install libxcb1-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libxcb1-dev: Depends: libxcb1 (= 1.1.93-0ubuntu3) but 1.1.93-0ubuntu3.1 is to be installed
E: Broken packages

```running cat /etc/apt/sourcs.list
```

$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

```

Any ideas?

---

### Post by Partyboi2 on 2009-07-23
Looks like you have not enabled updates.
Open a terminal and type
```
gksu gedit /etc/apt/sources.list
```
then add
```
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe
``` to the bottom of the file then save the changes and close gedit. Then back in the terminal
```
sudo apt-get update
sudo apt-get install libqt4-dev
```

---

### Post by sb08786734` on 2009-07-23
Fixed!! 

Many thanks for your info, it also fixed the problem I had with installing sox development libs.

Many Thanks

Stuart:D

---

### Post by map7 on 2009-07-23
I've already tried 'sudo apt-get -f install' but it doesn't fix the problem.

Here is my sources.list
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main multiverse universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-backports restricted main multiverse universe
# deb [http://ppa.launchpad.net/stgraber/ppa/ubuntu](http://ppa.launchpad.net/stgraber/ppa/ubuntu) jaunty main
```

---

### Post by Partyboi2 on 2009-07-24
Your source.list seems to be in order. Open up Synaptic and do a search for 'libxcb1' then highlight the package and select "Package" > "Force Version" and see if you can downgrade the libxcb1 package to 1.1.93-0ubuntu3.1, then reload the package list and try installing 'libgtk2.0-dev'.

---

### Post by map7 on 2009-07-26
That fixed some of it.  I forced it to install the 3.1 version of libxcb1 instead of the 4.0 version which was installed.  

I still have a problem with installing libgtk2.0-dev now I get:

```

~ $sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.6.4-6.1) but it is not going to be installed
E: Broken packages

```

I've tried to reinstall libcairo2-dev but I get the same problems, and the 'force version' is disabled for this package.

---

### Post by Partyboi2 on 2009-07-27
Try removing those 2 packages first```
sudo apt-get remove libpango1.0-dev libcairo2-dev
```
then try installing  libgtk2.0-dev which should reinstall those packages as well.
```
sudo apt-get install   libgtk2.0-dev
```

If that does not work the only other thing I can think of is to disable your backport repos, sometimes these can cause problems.

---

### Post by map7 on 2009-07-27
I found that libcairo2-dev required another libxcb package which was at version 4.0.  So I downgraded it to 3.1 and everything has come to life.  Thanks guys for all your help.

---

