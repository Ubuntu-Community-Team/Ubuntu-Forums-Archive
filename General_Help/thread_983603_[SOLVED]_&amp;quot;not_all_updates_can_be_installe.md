---
title: "[SOLVED] &amp;quot;not all updates can be installed&amp;quot; &amp;quot;run a partial upgrade...&amp;quot;"
date: 2008-11-15
forum: General Help
---

### Post by alisonjo2786 on 2008-11-15
Every time I've run Update Manager for at least a couple months, I've gotten this message: (see also the** screenshot below**)[INDENT]Not all updates can be installed.
Run a partial upgrade, to install as many updates as possible.
This can be caused by:

[LIST]
[*]A previous upgrade which didn't complete
[*]Problems with some of the installed software
[*]Unofficial software packages not provided by Ubuntu
[*]Normal changes of a pre-release version of Ubuntu
[/LIST]
[/INDENT]Maybe this was really dumb of me, but I've essentially ignored this for ages and just kept running Partial Upgrades.  Every time, there were several updates listed in Update Manager "unchecked".  Here's a current list of updates that can't be installed:

"Important security updates"[INDENT]firefox
firefox-3.0
firefox-3.0-dev
firefox-3.0-gnome-support
libxine-dev
libxine1-bin
[/INDENT]"Recommended updates"[INDENT]bind9-host
dnsutils
libbind9-30
libdns35
libisccc30
libisccfg30
linux-generic
linux-headers-generic
linux-image-generic
linux-restricted-modules-generic
[/INDENT]"Other updates"[INDENT]firefox-3.1
firefox-3.1-dev
firefox-3.1-gnome-support
[/INDENT]The reason I'm finally posting a thread about this is I've been having [COLOR=Blue]_[problems with Firefox]("http://ubuntuforums.org/showthread.php?t=981696")_[/COLOR] (I have 3.04pre, by the way; anyone know what the "pre" means, if anything?) and I'm considering uninstalling/reinstalling FF completely but I wanted to see if anyone has any thoughts, advice, suggestions, ideas, whatever, about this Update thing.  It seems like it probably matters, and I probably should have posted something sooner, but until recently, I've felt insecure about doing so.

So, any help/ideas would be greatly appreciated!  And of course, let me know what additional info I should post.  Thank you!

**Screenshot:**
[IMG]http://gwias.com/images/update-mngr_screenshot.gif[/IMG]

---

### Post by alisonjo2786 on 2008-11-16
bump

---

### Post by taurus on 2008-11-16
I think if you replace a program from the repos with something like pre-release or beta, sometimes that could cause problems when you try to upgrade your machine.  So it looks like firefox is the trouble one then.  

How did you install firefox 3.04pre anyway?

---

### Post by alisonjo2786 on 2008-11-16
No idea, haha.  I don't remember installing any updates that Update Manager didn't tell me to install.  (Does "pre" mean "pre-release"?)  Maybe I'll try to force it to install Firefox 3.1.

Today a friend suggested to me that I change the name of the directory where Firefox is on my computer so it will have to create a new User Profile, so I might try that, in addition to or instead of trying to upgrade to 3.1.

---

### Post by alisonjo2786 on 2008-11-17
I changed the directory name and that fixed other problems I was having with Firefox, but I still have FF 3.0.2pre, and Update Manager is still doing the same thing.

Also, someone suggested I go to Software Sources, "Download From..." and do "Select Best Server".  I did that, but Update Manager is still acting the same way.

So that's where things are at for now.  Any thoughts anyone?

---

### Post by cariboo on 2008-11-17
Which version of firefox do you actually have installed? Your post mentions mentions Firefox 3.1 which isn't available yet, although it was updated this morning to 3.04.

Jim

---

### Post by Butthead on 2008-11-17
Did you try running as root (without quotes) "apt-get -f install" under terminal? :confused:

---

### Post by Yellow Pasque on 2008-11-17
You apparently either have the "proposed" repo enabled or a 3rd-party repo enabled.
Post output of:
```
cat /etc/apt/sources.list
```

> Did you try running (without quotes) "apt-get -f install" under terminal?
Force installing can you get you in a lot of trouble quickly if your repo sources are screwed up.

---

### Post by alisonjo2786 on 2008-11-18
Sorry about the delay, I really appreciate everyone's help, suggestions, and input.  Was caught up with school and homework.  Anyway...
> **Temüjin said:**
> Post output of:
```
cat /etc/apt/sources.list
```
(Hope I'm posting this in the appropriate way; if not, please let me know and I'll fix it ASAP)
```
alison@alison-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse
deb-src http://archive.linux.duke.edu/ubuntu/ hardy-security restricted main multiverse #Added by software-properties
deb http://archive.linux.duke.edu/ubuntu/ hardy-updates restricted main multiverse
deb-src http://archive.linux.duke.edu/ubuntu/ hardy-updates restricted main multiverse #Added by software-properties
deb http://archive.linux.duke.edu/ubuntu/ hardy-proposed restricted main multiverse
deb-src http://archive.linux.duke.edu/ubuntu/ hardy-proposed restricted main multiverse #Added by software-properties
deb http://archive.linux.duke.edu/ubuntu/ hardy universe main restricted multiverse
deb-src http://archive.linux.duke.edu/ubuntu/ hardy universe main multiverse restricted #Added by software-properties
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb http://nightlies.videolan.org/build/hardy-i386/arch ./
deb http://archive.linux.duke.edu/ubuntu/ hardy-backports universe main multiverse restricted
deb-src http://archive.linux.duke.edu/ubuntu/ hardy-backports universe main multiverse restricted
deb http://ppa.launchpad.net/fta/ubuntu hardy main
```

---

### Post by alisonjo2786 on 2008-11-18
> **cariboo907 said:**
> Which version of firefox do you actually have installed? Your post mentions mentions Firefox 3.1 which isn't available yet, although it was updated this morning to 3.04.
Excellent question, that is pretty weird isn't it.  I don't know how I ended up with a directory called "firefox-3.1", but I did.  **Below is a screenshot** of said directory.  It is inside the directory I re-named so that it would make a new one, with a new user profile, b/c of the problems I was having with Firefox acting up.

In other words, this directory in which there is a directory called firefox-3.1, I am no longer using this directory. Hope that was clear, but let me know if it wasn't.

**Screenshot:**
[IMG]http://gwias.com/images/Screenshot_FF3-1.gif[/IMG]

---

### Post by alisonjo2786 on 2008-11-21
bump

---

