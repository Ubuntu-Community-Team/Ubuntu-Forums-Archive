---
title: "[SOLVED] Updating fails - bad request 400"
date: 2008-11-26
forum: General Help
---

### Post by Oswald1 on 2008-11-26
Howdy all,

My problem is this: Ubuntus update manager offers me a bunch of updates including many for openoffice. When I try to download and install the updates, the manager says it cannot download some files. When I run sudo aptitude update, I get errors as well reporting bad request 400.

Also if I try to reload the repositories in Synaptic, I get bad request 400 errors and it fails to load some stuff.

Changing the download location doesn't help.

Here's my current sources.list, if that's of any help. Don't spot any obvious problems there though.

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ intrepid main restricted
deb-src http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ intrepid-updates main restricted
deb-src http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ intrepid universe
deb-src http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ intrepid universe
deb http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ intrepid-updates universe
deb-src http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ intrepid multiverse
deb-src http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ intrepid multiverse
deb http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ intrepid-updates multiverse
deb-src http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://fi.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://fi.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ intrepid-security main restricted
deb-src http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ intrepid-security main restricted
deb http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ intrepid-security universe
deb-src http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ intrepid-security universe
deb http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ intrepid-security multiverse
deb-src http://www.nic.funet.fi/pub/mirrors/archive.ubuntu.com/ intrepid-security multiverse
# deb http://ppa.launchpad.net/spring/ubuntu hardy main
# deb-src http://ppa.launchpad.net/spring/ubuntu hardy main
# deb http://blognux.free.fr/ubuntu hardy main
# deb-src http://blognux.free.fr/ubuntu hardy main
# deb http://getswiftfox.com/builds/debian unstable non-free
```

Also, before this updates have worked just fine.

---

### Post by Oswald1 on 2008-11-27
Any clues anyone? I really don't know where to look for a solution.

---

### Post by adult swim on 2008-11-27
maybe the server is down.  try going to synaptic package manager and then go to settings>repositories.  look down where is says "download from" and try changing to the main server or a different one than you currently have.
then see if it will update.

---

### Post by Oswald1 on 2008-11-27
As I mentioned, I've tried different servers locations to no avail. One thing I noticed this morning was that pidgin was having trouble connecting to msn as well, so this might be some networking problem. I will test how things work with my laptop once I get home. Strange though, that surfing the web for example works just fine.

One networking related thing I did some days ago was setting firefox, galeon and opera use a proxy for some testing purposes, but these I changed back to no proxies (I don't see how this could affect updating though).

---

### Post by Oswald1 on 2008-11-27
Hmm, silly me. It really was a proxy problem. I didn't realize that changing firefox's proxy settings (or some other browsers) affects the whole system.

So in case someone else has similar troubles: System->Preferences->Network proxy and choose Direct internet connection, if using a proxy isn't necessary.

---

