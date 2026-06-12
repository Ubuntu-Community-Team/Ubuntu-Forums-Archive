---
title: "Clash of KDE packages"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by steevc on 2009-04-14
I tried to apply some updates to my 8.10 a couple of weeks back and something went wrong. I now get this error when I try to update:

E: /var/cache/apt/archives/kdebase-workspace-data_4%3a4.1.4-0ubuntu1~intrepid3.1_all.deb: trying to overwrite `/usr/share/kde4/apps/desktoptheme/default/colors', which is also in package kdebase-runtime-data

It seems that kdebase-workspace-bin and libplasma2 are broken.

Any suggestions?

I'm getting by running xfce for now. It's actually not that bad and I can run most stuff, but I'd like KDE back. I expect I need to fix this before thinking about upgrading to Jaunty.

---

### Post by dabl on 2009-04-14
Try (in the Konsole):

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```
```

sudo apt-get dist-upgrade
```


Note any error messages that are given.

---

### Post by steevc on 2009-04-15
Thanks for the prompt response.

The dpkg gives a load of errors about dependencies, starting with kdebase-workspace-data, as you might expect.

'sudo apt-get dist-upgrade' gave

```
Reading package lists... Done                                                                                        
Building dependency tree                                                                                             
Reading state information... Done                                                                                    
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  kdebase-workspace-bin: Depends: kdebase-workspace-data (= 4:4.1.4-0ubuntu1~intrepid3.1) but it is not installed
  libplasma2: Depends: kdebase-workspace-data (= 4:4.1.4-0ubuntu1~intrepid3.1) but it is not installed
E: Unmet dependencies. Try using -f.

```

Trying the suggested 'apt-get -f install' got me back to

```
dpkg: error processing /var/cache/apt/archives/kdebase-workspace-data_4%3a4.1.4-0ubuntu1~intrepid3.1_all.deb (--unpack):
 trying to overwrite `/usr/share/kde4/apps/desktoptheme/default/colors', which is also in package kdebase-runtime-data
```

---

### Post by taurus on 2009-04-15
You probably need to look at your repos to make sure you have not mixed the releases.

```
cat /etc/apt/sources.list
```

---

### Post by inobe on 2009-04-15
to my understanding enabling unsupported will upgrade you to 4.2.

adept> sources> edit software sources> updates tab> check unsupported updates.

close it and it should fetch a hundred or so megs in updates.

granted if that is kde 4.1' it wasn't the most stable release.

4.2 has been out for a wile and it has much improved since.

---

### Post by steevc on 2009-04-15
It's all set to intrepid there. I did a fresh install fairly recently and updates were working fine for a while.

Here you go anyway:

```

# deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
# deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main

```

---

### Post by steevc on 2009-04-17
I may have worked around the issue using the suggestion here

[http://shreevatsa.wordpress.com/2006/04/16/dpkg-error-trying-to-overwrite-x-which-is-also-in-package-y/](http://shreevatsa.wordpress.com/2006/04/16/dpkg-error-trying-to-overwrite-x-which-is-also-in-package-y/)

Uses 

```
sudo dpkg -i --force-overwrite AAA
```

Where AAA is the problem file. Then

```
sudo apt-get -f install
```

After that I can finally run KDE again!

However, all is not quite right yet. Any apps I open have no title bar and open full screen so I can't see the panel or minimise them. Am I missing something?

UPDATE: An apt-get install kubuntu-desktop resolved the title bar issue :)

---

