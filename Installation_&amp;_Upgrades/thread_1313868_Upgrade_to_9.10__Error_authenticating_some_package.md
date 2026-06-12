---
title: "Upgrade to 9.10 : Error authenticating some packages"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by captain_rob on 2009-11-04
Wanted to upgrade Ubuntu from 9.04 (64) to 9.10 (64) but got a error message with online upgrade as well with the alternate cd. Tried several times and also after reinstalling te packages the same error

[B]Error authenticating some packages
[/B]

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

firefox
firefox-3.0
firefox-3.0-branding
firefox-3.0-gnome-support
firefox-3.5
firefox-3.5-branding
firefox-3.5-gnome-support
firefox-gnome-support
kerneloops-daemon
libpoppler-glib4
libpoppler5
libpython2.6
poppler-utils
python-ubuntuone-client
python2.6
python2.6-minimal
ubuntuone-client
ubuntuone-client-gnome
update-manager
update-manager-core
xulrunner-1.9.1
xulrunner-1.9.1-gnome-support

Please help me out :confused:

P.M. 
I remember this packages were just upgraded a few days ago !

---

### Post by kirzhanov on 2009-11-04
My problem may be similar to the one reported above as may not. 

I was using Kubuntu 9.04, then installed gnome above it and than upgraded to Kubuntu 9.10 still using gnome. After the reboot I tried to install some additional packages and Synaptic hung. A reboot solved the problem but I received an error in the root filesystem which was situated in /var/lib/dpkg as the manual fsck run showed. 

Now the system runs smoothly except this [[https://bugs.launchpad.net/ubuntu/+bug/81057]](https://bugs.launchpad.net/ubuntu/+bug/81057]) problem which can be in most cases solved manually until there would be a comprehensive solution.

But  _all the packages in Synaptic are listed as unauthenticated_. I still can install/uninstall them and all the keys are listed in Synaptic. The Ubuntu icon which allows to distinguish  between Canonical-supported and unsupported software is also not displayed in any package record. A message about installation of unauthenticated package is displayed every time I install a package.

Since I had a filesystem error it seems that something is damaged in package database or in software I installed. Is there a way to "repair" my installation?

---

