---
title: "Synaptic Search is Broken on 8.10"
date: 2008-11-13
forum: General Help
---

### Post by nlinux on 2008-11-13
Maybe it's just me but I've checked this on two separate machines.  If I fire up synaptic and try to do a quick search, it only returns a partial result of packages.  Try searching for linux and see what you get :).  If I do a full search for anything it's broken completely and returns nothing.

Anyone else seeing this?

---

### Post by taurus on 2008-11-13
Not sure why but let's have a quick look at your /etc/apt/sources.list then.  Open a terminal and post the output of your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by nlinux on 2008-11-13
Here you go, but it's unrelated to my sources as using apt and aptitude seems to work fine, this appears to be synaptic specific.

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

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
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://ppa.launchpad.net/awn-testing/ubuntu intrepid main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu intrepid main
deb http://repository.cairo-dock.org/ubuntu intrepid cairo-dock
# deb http://ppa.launchpad.net/compiz/ubuntu hardy main
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

---

### Post by SamNSane on 2008-11-14
If you're talking about entering text in the search field in the toolbar, yeah, that didn't work for me at all. It didn't even give me partial results. It didn't do anything. But invoking a search in the traditional sense gave me the results I would have expected.

I saw this on two systems. It was only one of many little glitches that helped me make up my mind to go back to Hardy.

---

### Post by daka on 2008-11-20
Yes, Synaptic Search seems broken on my Intrepid install too.  I am surprised many people haven't experienced this and commented on it.

daka

---

### Post by fooman on 2008-11-20
> **daka said:**
> Yes, Synaptic Search seems broken on my Intrepid install too.  I am surprised many people haven't experienced this and commented on it.

daka

not sure if this is what you mean,  but if you are first trying a "quick search"...and *then* trying the regular "search" option,  then you will need to clear the "quick search" field *before typing into the field of the regular "search"*.

*if you do not first clear the "quick search" field*...then the regular "search" will be limited to the results of the "quick search" you just performed.

if you *clear* the "quick search" field first,  *then* use the regular "search"...you will get the full results.

try it with a search for "linux" (like in the original post)...first do quick search for "linux",  then do a regular search for "linux"...the results will be the same.

close synaptic,  then open it again.

now try another quick search for "linux",  this time after it completes...*clear the "quick search" field*,  then do a regular search for "linux".

see the difference.

hope that somehow makes sense.

---

### Post by SamNSane on 2008-11-20
I'm interested in knowing more about this. In my case, entering text in the toolbar field resulted in no results. But calling up the regular dialog with Ctrl-F or by clicking on the binoculars icon in the toolbar and entering text in the field that was presented on my systems resulted in the normal results. So the search wasn't totally broken for me. Only the toolbar applet was broken. Is that what's going on with your systems?

---

### Post by daka on 2008-11-22
Thanks Guys!  I have the regular search working nicely.  It is the 'Quick Search' that is broken.

But I didn't even know that I had a regular search option until now!!!

Thanks again, life is much simpler with search option in  Synaptic.

All in all I am very happy with Intrepid.  I have a very new laptop Toshiba Pavilion L300 and it has been very problematic.  I suspect that by the next release it should be fully functional.

I DO NOT RECOMMEND THIS LAPTOP  for Linux, or even for Windows.

Daka

---

### Post by jocko on 2008-11-22
***Nothing*** is broken.
The search function searches all packages (available from the repos or installed manually), while the quick search function is simply a filter for which packages to show.
If you do a quick search without having a list of packages, you will not get any results.
If you list all installed packages (status -->installed), then do a quick search for "linux", you will only see* installed* packages with linux in their name. If you first do a full search for "linux" and then a quick search for "restricted", you will just see the packages with both "linux" and "restricted" in their names...

So the only thing that is wrong is that some people get confused by having two search functions... Maybe the name "quick search" is misleading...

---

### Post by DraconPern on 2008-11-22
yeah, quick search is broken.  When search finds nothing, it's broken. It doesn't matter how the search is performed.

---

### Post by SamNSane on 2008-11-22
> **jocko said:**
> ***Nothing*** is broken.
The search function searches all packages (available from the repos or installed manually), while the quick search function is simply a filter for which packages to show.
If you do a quick search without having a list of packages, you will not get any results.
If you list all installed packages (status -->installed), then do a quick search for "linux", you will only see* installed* packages with linux in their name. If you first do a full search for "linux" and then a quick search for "restricted", you will just see the packages with both "linux" and "restricted" in their names...

So the only thing that is wrong is that some people get confused by having two search functions... Maybe the name "quick search" is misleading...

That's interesting information. I agree with you that "quick search" is misleading, so "broken" in a user interface sort of way.

Not only is such a design not intuitive, it is counter-intuitive, going against normally accepted design practices that have been used almost universally for this type of functionality for years -- functionality for which most folks have pretty well-defined expectations.

The developers should probably alter the way it works, because almost no one is going to think to look in a help file or FAQ when they see what seems to be frankly "broken" behavior in a search function. (Well, at least dopes like me won't.) It shouldn't be impossible to design it so that it remains grayed out until conditions for its successful use are met (there is a list for it to search). It could also be called "search within", which is a common enough practice in some types of search systems.

Thank you for your observation. Without it, I wouldn't have thought to try to use it at all. I can see how it could be helpful.

Unfortunately, I went back to Hardy because of myriad little glitches in Intrepid on my systems. For these particular computers I'm probably better off sticking with LTS anyway.

Thanks again.

---

