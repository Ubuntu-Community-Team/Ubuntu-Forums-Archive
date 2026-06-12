---
title: "install java on fluxbuntu"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by mscoxoh on 2009-09-01
Not sure if this is the right place; can't find any forums specifically for Fluxbuntu.

How do I install Java? None of the references I've found work (i.e. apt-get install sun-java6.bin, et al). It's not found. Any ideas? Thanks.

---

### Post by oldos2er on 2009-09-01
** sudo apt-get install sun-java6-jre** should work across all versions of Ubuntu. Can you copy and paste the command you're running and its output?

---

### Post by mscoxoh on 2009-09-02
> **oldos2er said:**
> ** sudo apt-get install sun-java6-jre** should work across all versions of Ubuntu. Can you copy and paste the command you're running and its output?

Sure. Here is what I get:

```
sudo apt-get install sun-java6-jre6*
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package sun-java6-jre*
```

Do I need to add something to my sources.list? Here's what I have:

 
```
# deb cdrom:[Fluxbuntu 7.10 _Gutsy Gibbon_ - Release Candidate i386 (20071026)]/ gutsy main

deb cdrom:[Fluxbuntu 7.10 _Gutsy Gibbon_ - Release Candidate i386 (20071026)]/ gutsy main
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

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
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by stumbleUpon on 2009-09-02
You have commented out all the ubuntu software repositories and are using only what is available in your cd-rom. You need to uncomment them.

The support for gutsy (ubuntu 7.10) has ended this april 2009. Please upgrade to hardy or jaunty.

---

### Post by mscoxoh on 2009-09-02
> Ah... Well I didn't comment out anything. I guess that's the way Fluxbuntu installs. I should've noticed! Whooops.

I'll upgrade Fluxbuntu as soon as one is available! :)  (I think they have an 8.10 in "testing" right now...)

Well, it's a catch-22. They're commented out because the sources are unreachable, probably because, as you said, support has ended for that release. However, that's the only release available in Fluxbuntu right now, so I can't upgrade to get access to newer sources.

---

### Post by snowpine on 2009-09-02
You have basically three options (four I guess if you count downloading Java from the Sun website):

1. Uncomment out the sources and change them to old-releases. You'll then be able to install things from the Gutsy archives, which are no longer maintained and will become increasingly out of date. For example:

```
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
```

becomes:

```
deb http://old-releases.ubuntu.com/ubuntu/ gutsy main restricted
```

2. Change sources to hardy so you'll have long term support through april 2011. (don't upgrade to intrepid; it won't work!) For example:

```
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
```

Then from the terminal:

```
sudo apt-get update && sudo do-release-upgrade
```

3. Choose a distro that is still under development and has an active community. I strongly recommend this third option. CrunchBang is my favorite "lightweight Ubuntu," AntiX is my favorite active Fluxbox distro, and SliTaz is my favorite distro for older hardware.

---

### Post by mscoxoh on 2009-09-02
Thanks for the extensive reply, snowpine. It does seem Fluxbuntu is still being developed and about to release 9.10 by the end of October ([http://wiki.fluxbuntu.org/index.php?title=KarmicReleaseSchedule](http://wiki.fluxbuntu.org/index.php?title=KarmicReleaseSchedule)).

I want lightweight AND fast! My Flexbuntu boots in 25 seconds (in a VMWare session on my MacBook) and takes 1.9gb with only the base + Firefox installed. I need a very basic Linux with Firefox. Which of those Ubuntu flavors would you recommend based on that?

---

### Post by snowpine on 2009-09-02
> **mscoxoh said:**
> Thanks for the extensive reply, snowpine. It does seem Fluxbuntu is still being developed and about to release 9.10 by the end of October ([http://wiki.fluxbuntu.org/index.php?title=KarmicReleaseSchedule](http://wiki.fluxbuntu.org/index.php?title=KarmicReleaseSchedule)).


That's the *Ubuntu* Karmic release schedule... the most recent release of *Fluxbuntu* is 7.10 "release candidate." Drop by the official forums to see the state of the project: [http://community.fluxbuntu.org/](http://community.fluxbuntu.org/)

It's a shame because it was one of my favorite distros at the time. :( I'm even still running it (upgraded to 8.04) on one of my old laptops.

> **mscoxoh said:**
> I want lightweight AND fast! My Flexbuntu boots in 25 seconds (in a VMWare session on my MacBook) and takes 1.9gb with only the base + Firefox installed. I need a very basic Linux with Firefox. Which of those Ubuntu flavors would you recommend based on that?

SliTaz is 30mb, includes Firefox, and boots and runs much faster than anything based on Ubuntu. Highly recommended.

---

### Post by oldos2er on 2009-09-02
Couldn't you do a minimal Ubuntu install, and add fluxbox?

---

