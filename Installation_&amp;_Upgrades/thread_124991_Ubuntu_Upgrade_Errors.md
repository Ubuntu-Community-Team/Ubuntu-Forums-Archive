---
title: "Ubuntu Upgrade Errors"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by Jaygo333 on 2006-02-02
Everytime I try to update ubuntu, I get the following errors. 

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_20060126_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_20060126_all.deb)
  404 Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_20060126_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_20060126_all.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/imagemagick_6.2.3.4-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/imagemagick_6.2.3.4-1ubuntu1.1_i386.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick6_6.2.3.4-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick6_6.2.3.4-1ubuntu1.1_i386.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.4.3-0ubuntu2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.4.3-0ubuntu2_all.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs4c2_3.4.3-0ubuntu2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs4c2_3.4.3-0ubuntu2_i386.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-bin_3.4.3-0ubuntu2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-bin_3.4.3-0ubuntu2_i386.deb)
  404 Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq4_8.1.2-1~breezy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq4_8.1.2-1~breezy1_i386.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/m/mydns/mydns-common_1.1.0+pre-2ubuntu0.1_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/m/mydns/mydns-common_1.1.0+pre-2ubuntu0.1_all.deb)
  404 Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_5.10-6.2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_5.10-6.2_all.deb)
  404 Not Found

W: Failed to fetch [http://wine.sourceforge.net/apt/binary/wine_0.9.6-winehq-1_i386.deb](http://wine.sourceforge.net/apt/binary/wine_0.9.6-winehq-1_i386.deb)
  404 Not Found

Help. 
What to do, What to do.1

:h34r: Jaygo333 :h34r:

---

### Post by aysiu on 2006-02-02
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by Jaygo333 on 2006-02-03
[QUOTE=aysiu]Can you post the output of this command? ```
cat /etc/apt/sources.list
```[/QUOTE]

Here:

jaygo333@Ubuntu:~$ cat /etc/apt/sources.list
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

## deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
## deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
## deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse
## created by arnieplanetremoved
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
jaygo333@Ubuntu:~$

What do you need it for?
Please say it helps.

:h34r: Jaygo333 :h34r:

---

