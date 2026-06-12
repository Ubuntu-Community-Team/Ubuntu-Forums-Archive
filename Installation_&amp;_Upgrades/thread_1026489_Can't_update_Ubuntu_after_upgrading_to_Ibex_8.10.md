---
title: "Can't update Ubuntu after upgrading to Ibex 8.10"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by caole261188 on 2008-12-31
Hi,

First of all, I tried googling this problem before, but couldn't find the answer to my case. I hope you can help me with this.

I have a laptop and a desktop computer. Three days ago, I was over-excited and decided to upgrade my desktop from Hardy to Ibex, then made a fresh installation of Ibex on my laptop.

The weird thing is that, although the upgrade process went smoothly (no connection errors), I cannot update ubuntu ibex anymore. Here's the output I got from sudo apt-get update:

```
Err http://archive.ubuntu.com intrepid Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-updates/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-updates/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-security Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-security/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-security/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-security/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-security/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://download.skype.com stable Release.gpg
  Could not resolve 'download.skype.com'
Err http://download.skype.com stable/non-free Translation-en_US
  Could not resolve 'download.skype.com'
Err http://archive.canonical.com intrepid Release.gpg
  Could not resolve 'archive.canonical.com'
Err http://archive.canonical.com intrepid/partner Translation-en_US
  Could not resolve 'archive.canonical.com'
Err http://archive.canonical.com hardy Release.gpg
  Could not resolve 'archive.canonical.com'

```

Here's my sources.list file:

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://jp.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://jp.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb http://download.skype.com/linux/repos/debian/ stable non-free

```

Do you have any idea what's going on with my ibex?

Your help is much appreciated.

Thanks in advance,

Gary.

---

### Post by lemming465 on 2009-01-01
I forget the launchpad bug number, but intrepid had a bug where problems with any repositories caused the update-manager to completely flake out.  Try commenting out the hardy and skype repositories, then run **sudo apt-get update; sudo apt-get upgrade** and see if your luck changes.  Also check for any 3rd party /etc/apt/sources.list.d/*.list files you might have laying about.

---

### Post by blindvic on 2009-01-18
> Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
  Could not resolve 'archive.ubuntu.com'
...
Have the same problem. Konqueror works perfectly, can access web-pages.
The only solution i found - before 'apt-get update' making 'nslookup archive.ubuntu.com'

Kubuntu Jaunty Alpha 3

---

