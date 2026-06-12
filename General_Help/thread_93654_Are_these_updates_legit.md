---
title: "Are these updates legit?"
date: 2005-11-22
forum: General Help
---

### Post by suRoot on 2005-11-22
I'm still getting used to the whole apt-get system.  I'm a little concerned about a few updates that appeared earlier, see attached screenshot.  They're all kernel related, but they're supposedly "not authenticated".

Seems a legitimate kernel upgrade shouldn't be flagged in this manner.  Can anyone tell me whether these are legitimate updates or not?

Thanks.

---

### Post by MarcDM on 2005-11-22
Which repositories do you have enabled?

If you only have the default Ubuntu repos, then I think they should be safe. I'm getting them too, but I've been ignoring them at least until I finish some other stuff.

---

### Post by suRoot on 2005-11-22
I've added a few things to my sources as I've been installing software.  I feel better knowing someone else is seeing the updates, though.

Here it is:

```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## deb http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
## deb-src http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi

## created by newarnieplf

```

---

### Post by juancnuno on 2005-11-22
I only use the official repositories, no mirrors, and I get the same not authorized warnings.  I go ahead and install the updates, but the warnings keep me up at night...

Here is my sources.list:

```

deb http://archive.ubuntu.com/ubuntu/ breezy           main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ breezy-updates   main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ breezy-security  main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse

```

---

### Post by ranf on 2005-11-22
[QUOTE=juancnuno]I only use the official repositories, no mirrors, and I get the same not authorized warnings.  I go ahead and install the updates, but the warnings keep me up at night...
[/QUOTE]
I always wait until there is an announcement available (Security Announcements here at ubuntuforums.org).

Ahh and yes it is there in the mean time.

---

