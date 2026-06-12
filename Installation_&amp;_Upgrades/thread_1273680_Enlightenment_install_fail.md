---
title: "Enlightenment install fail"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by BigTA78 on 2009-09-23
Hello
Be warned, I'm a relative newbie when it comes to Linux/Ubuntu (Jaunty)

I've tried to install Enlightenment but I keep getting the error:

svn: URL 'http://svn.enlightenment.org/svn/e/trunk/epsilon' does not exit

The thing is, everything I try just seems to restart the install and fail. I now can't even open Synaptic.
I've tried using the easy_e17.sh script as well as apt-get install e17-svn but to no avail.

Any help appreciated.

---

### Post by earthpigg on 2009-09-23
well, let's fix your sources.list, and then take a look at the directions from enlightenment and start the process over again and see if we can find out where either you or the folks at enlightenment made a human error.

can you copy/paste the contents of your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by BigTA78 on 2009-09-23
Thanks earthpigg

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://www.bunkus.org/ubuntu/jaunty/](http://www.bunkus.org/ubuntu/jaunty/) ./
deb-src [http://www.bunkus.org/ubuntu/jaunty/](http://www.bunkus.org/ubuntu/jaunty/) ./
deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) tinwoodman main

---

### Post by Tux Aubrey on 2009-09-23
Hi BigTA78

You are attempting something in the "crazy expert only" category here - there have been several changes to the e17 svn code base since that script was last edited and you'll need to do a whole mess of editing to get it to work (see my post at [http://ubuntuforums.org/showpost.php?p=7488509&postcount=392](http://ubuntuforums.org/showpost.php?p=7488509&postcount=392) for a few of them - epsilon is just another package that has been taken off the server.)

My personal suggestion is to GIVE UP NOW! and install e17 from the packages.enlightenment repository rather than from source code - you honestly would not notice any difference in the desktop and you have at least a 50:50 chance of remaining sane.

I'll summarize the instructions here:


Add the enlightenment repo (for jaunty) to etc/apt/sources.list

```
deb http://packages.enlightenment.org/ubuntu jaunty main extras
```

get the enlightenment package key:

```
wget http://packages.enlightenment.org/repo.key
```

add it:

```
sudo apt-key add repo.key
```


```
sudo apt-get update
```

Install enlightenment plus any modules you want - eg (serving suggestion)

```
sudo apt-get install e17 emodule-bling emodule-calendar emodule-cpu emodule-deskshow emodule-diskio emodule-edgar emodule-efm-nav emodule-efm-path emodule-efm-pathbar emodule-extramenu emodule-flame emodule-mail emodule-mem emodule-notification emodule-places emodule-screenshot emodule-taskbar emodule-tiling emodule-trash emodule-winselector emodule-wlan wicd
```

(note "wicd" - not an enlightenment package but a useful network manager for non-gnome systems)

This should give you a functional and fairly up-to-date e17 desktop with enough modules to get you setup (these are actually the only ones I personally use and know are stable and functional - which is why I don't recommend installing emodules-all).

Once you have a desktop working, you can browse the e17 repo in synaptic and install additional modules if you want (but very much at your own risk).

Please note that I haven't personally used these jaunty repos (However I'm doing much the same with Karmic and having no e17 related problems - only Karmic ones!)

see [http://packages.enlightenment.org](http://packages.enlightenment.org) for further info.

---

