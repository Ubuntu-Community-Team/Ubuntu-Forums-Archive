---
title: "Blocked Updates?"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by knichel on 2009-10-30
I have been running with 9.04 for some time now.  I recently noticed that my update manager shows 4 blocked updates.  

linux-headers-generic-2.6.28.15.20 (amd64)
linux-restricted-modules-generic-generic-2.6.28.15.20 (amd64)
linux-generic-2.6.28.15.20 (amd64)
linux-image-generic-2.6.28.15.20 (amd64)

My sources are...
```

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse


deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

deb http://download.virtualbox.org/virtualbox/debian jaunty non-free
deb http://packages.medibuntu.org/ jaunty free non-free
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
deb http://download.webmin.com/download/repository sarge contrib


```

my current kernel is...
```

Linux Gumby 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux

```

Why do I have blocked updates?

---

### Post by hal10000 on 2009-10-30
> Why do I have blocked updates?
This usually only happens if you blocked them yourself in your package manager.
With synaptic you can unblock the affecting packages (menu--->package--->block version)

---

### Post by knichel on 2009-11-04
Thanks for responding.  However, when I open Synaptic, there is no menu "Menu" but under "Package" there is no "block...".  When I try to locate one of the blocked packages in the list of packages, it is there and marked as upgradable...

Someone else suggested sudo apt-get dist-upgrade... is that correct?

---

### Post by hal10000 on 2009-11-04
> but under "Package" there is no "block..."

I don't know the exact English expression, because in my synaptic-version everything is in german, but under "Package" it's the seventh menu entry.
I hope you find it now.

---

### Post by knichel on 2009-11-05
The 7th menu item in my Package menu is "Lock Version".  No mention of block... and everything in my Package menu is Grayed out.

---

### Post by note32 on 2009-11-05
$ sudo apt-get update

$ sudo apt-get dist-upgrade

should work i had this happen to me to when i had 9.04

---

### Post by note32 on 2009-11-05
also look at this thread 

[http://ubuntuforums.org/showthread.php?t=1191493](http://ubuntuforums.org/showthread.php?t=1191493)

---

### Post by hal10000 on 2009-11-05
> and everything in my Package menu is Grayed out

of course it's greyed out, as long as you don't choose a package

---

### Post by knichel on 2009-11-06
I performed a dist-upgrade and it seems to have taken care of the blocked updates.  This is strange, as the blocked updates were fore kernel 2.6.28-15 and the dist upgrade installed 2.6.28.16  is this going to happen every time a new kernel is released?

---

### Post by knichel on 2009-12-14
I am bumping this since this morning I have 12 blocked updates and some of them are the 2.6.28.16.21  kernel packages.  Along with others, this is very frustrating.  Someone needs to figure out why they are blocked, please...

These are the ones blocked...
```

bind9-host dnsutils libbind9-40 libdns45 libisc45 libisccc40 libisccfg40 liblwres40 linux-generic
  linux-headers-generic linux-image-generic linux-restricted-modules-generic

```

---

### Post by knichel on 2010-02-15
Once again I have blocked updates.
```

The following packages have been kept back:
google-chrome-unstable 
linux-generic 
linux-headers-generic 
linux-image-generic 
linux-restricted-modules-generic

```

I know that performing a dist-upgrade will correct this, but it seems that every month or so I have to do that.  What is going on?  Do I have something in my sources causing this?

```

#deb cdrom:[Kubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to                        
# newer versions of the distribution.                                                            

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any  
## review or updates from the Ubuntu security team.                        
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe                   
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe               
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe           
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe       

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse                  
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse              
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
 deb http://archive.canonical.com/ubuntu jaunty partner
 deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

# CUSTOM by mike
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free
#deb http://deb.opera.com/opera/ stable non-free
deb http://packages.medibuntu.org/ jaunty free non-free
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main
deb http://download.webmin.com/download/repository sarge contrib

```

---

