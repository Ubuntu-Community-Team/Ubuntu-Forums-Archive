---
title: "Synaptic not showing apps that can be installed"
date: 2008-11-16
forum: General Help
---

### Post by simonjp on 2008-11-16
Whenever I open Synaptic and search for an application, e.g. elisa, the Search results are always blank.  I've reloaded the Software Sources but to no avail.  Any ideas anyone?

---

### Post by boof1988 on 2008-11-16
> **simonjp said:**
> Whenever I open Synaptic and search for an application, e.g. elisa, the Search results are always blank.  I've reloaded the Software Sources but to no avail.  Any ideas anyone?

When you first open Synaptic Package Manager (before any search), does it show a list of packages?

One way I use to search is:
[LIST=1]
[*]Click (single-click) on any package in the package list
[*]Then type the first few letters of the desired package
[/LIST]

Below is a screen-capture of my search for elisa.

Hope this helps some.

---

### Post by frankleeee on 2008-11-16
> **simonjp said:**
> Whenever I open Synaptic and search for an application, e.g. elisa, the Search results are always blank.  I've reloaded the Software Sources but to no avail.  Any ideas anyone?

I am not on my linux computer right now but are you sure you have the repositories open or installed that would have what you need, here is the elisa site
[http://elisa.fluendo.com/](http://elisa.fluendo.com/)

---

### Post by oldos2er on 2008-11-16
> **simonjp said:**
> Whenever I open Synaptic and search for an application, e.g. elisa, the Search results are always blank.  I've reloaded the Software Sources but to no avail.  Any ideas anyone?

 Can you post the output of "cat /etc/apt/sources.list"?

---

### Post by simonjp on 2008-11-16
> **boof1988 said:**
> When you first open Synaptic Package Manager (before any search), does it show a list of packages?

One way I use to search is:
[LIST=1]
[*]Click (single-click) on any package in the package list
[*]Then type the first few letters of the desired package
[/LIST]

Below is a screen-capture of my search for elisa.

Hope this helps some.

Thanks, I tried this and elisa appeared in the list!

In fact when I searched for any app I wouldn't get any results.  Now, after I searched for an item I highlighted, search results are appearing.

---

### Post by simonjp on 2008-11-16
> **oldos2er said:**
> Can you post the output of "cat /etc/apt/sources.list"?

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse restricted universe main
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main

---

### Post by boof1988 on 2008-11-16
> **simonjp said:**
> Thanks, I tried this and elisa appeared in the list!

In fact when I searched for any app I wouldn't get any results.  Now, after I searched for an item I highlighted, search results are appearing.

Attached is a screen-capture for a search in Synaptics Package Manager.  I opened up the scroll-box(?) to show the *options* of the search.  Maybe when you searched earlier, the search option was incorrect for your search?

I'm just trying to give some more ideas on what might help with searches for anyone.

---

### Post by simonjp on 2008-11-17
Thanks very much for the suggestion.  The problem occured when using the Quick Search.  I've since restarted my computer and searching for packages in Synaptic looks to be working now.  Strange one this, I've never experienced this before but at least now know what to do to fix it.

---

