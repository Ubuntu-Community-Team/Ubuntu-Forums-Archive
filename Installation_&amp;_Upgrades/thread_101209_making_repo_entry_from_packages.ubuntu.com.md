---
title: "making repo entry from packages.ubuntu.com"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by thegnark on 2005-12-09
if i find a package on packages.ubuntu.com, how do i compose a apt source line to add to my repo list?

package: [http://packages.ubuntu.com/breezy/misc/xorg-driver-fglrx-dev](http://packages.ubuntu.com/breezy/misc/xorg-driver-fglrx-dev)


i'd like to know so i can deal with this in the future :) thanks

---

### Post by Rinzwind on 2005-12-09
I'm a newbie at this page but what I see here leads me to the conclusion below:
> 
Package: xorg-driver-fglrx-dev (6.8.0-8.16.20-0ubuntu16.1) [security] [restricted]
= Did you see those letters in brackets in the quote? Those (to me) indicate you need the "security" and "restricted" repository for Breezy

To add these read this:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

But do change ALL hoary's to breezy cuz you want the Breezy repo's :)

So like this: 

> ## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted

It could be rubbish tho (cuz I am doing this from my head and can't verify anything).
Do backup all files before you commit changes ;)

---

### Post by thegnark on 2005-12-09
i figure out that much (needing to add security and restricted), but i was more specifically interested in figuring out on which source these would pertain to

---

### Post by Rinzwind on 2005-12-09
You lost me now. The package name would be xorg-driver-fglrx-dev. 
If I start kpackage and search for xorg-driver-fglrx-dev it brings it up ;)

so
> 
sudo apt-get install xorg-driver-fglrx-dev 

is what you wanted to know?

Or did you mean this with source> 
description Video driver for the ATI Radeon and FireGL graphics accelerators. . This package provides definitions for the GL and GLX extensions and the FGLRXGAMMA extension interface library.
architecture i386
depends xorg-driver-fglrx (= 6.8.0-8.16.20-0ubuntu16.1)
conflicts fglrx-driver-dev, xfree86-driver-fglrx-dev
provides fglrx-driver-dev
replaces fglrx-driver-dev, xfree86-driver-fglrx-dev
priority optional
maintainer Adam Conrad <adconrad@ubuntu.com>
**source linux-restricted-modules-2.6.12 (2.6.12.4-11.1)**
filename pool/restricted/l/linux-restricted-modules-2.6.12/ xorg-driver-fglrx-dev_6.8.0-8.16.20-0ubuntu16.1_i386.deb
origin Ubuntu
bugs mailto:ubuntu-users@lists.ubuntu.com

---

### Post by thegnark on 2005-12-09
see, the problem is that the package doens't show up in an apt-cache search (and thus i cannot apt-get install)

maybe this explains it better:
[http://www.ubuntuforums.org/showpost.php?p=549115&postcount=53]("http://www.ubuntuforums.org/showpost.php?p=549115&postcount=53")
[http://www.ubuntuforums.org/showpost.php?p=549115&postcount=56]("http://www.ubuntuforums.org/showpost.php?p=549115&postcount=56")
[http://www.ubuntuforums.org/showpost.php?p=549115&postcount=58]("http://www.ubuntuforums.org/showpost.php?p=549115&postcount=58")

P.S. I downloaded the linked deb and did a dpkg -i <file>, but i'm still curious as to get it in my repo list

---

