---
title: "&quot;failed to fetch&quot; &quot;404&quot; errors when updating"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by gojetsgo on 2009-10-28
I haven't used my Ubuntu computer in a while, and I have a load of updates available for me, 168 total.  I am running 6.10 and an upgrade is available to 7.04 in my package manager.

The problem is NOTHING seems to connect.  I've spent a couple hours reading different solutions out there, but it's quite possible I just don't know what I'm doing.  I get endless errors.  For examples, when trying to upgrade to 7.04, I get:

Failed to fetch [http://edevelop.org/pkg-e/ubuntu/dists/edgy/Release.gpg](http://edevelop.org/pkg-e/ubuntu/dists/edgy/Release.gpg) Temporary failure resolving 'edevelop.org'
Failed to fetch [http://edevelop.org/pkg-e/ubuntu/dists/edgy/e17/i18n/Translation-en_US.bz2](http://edevelop.org/pkg-e/ubuntu/dists/edgy/e17/i18n/Translation-en_US.bz2) Temporary failure resolving 'edevelop.org'
Failed to fetch [http://atp.wicd.net/dists/edgy/Release.gpg](http://atp.wicd.net/dists/edgy/Release.gpg) Could not resolve 'atp.wicd.net'
Failed to fetch [http://atp.wicd.net/dists/edgy/extras/i18n/Translation-en_US.bz2](http://atp.wicd.net/dists/edgy/extras/i18n/Translation-en_US.bz2) Could not resolve 'atp.wicd.net'
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/Release](http://wine.budgetdedicated.com/apt/dists/edgy/Release) Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch [http://javadesktop.org/lg3d/debian/dists/stable/contrib/binary-i386/Packages.gz](http://javadesktop.org/lg3d/debian/dists/stable/contrib/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://atp.wicd.net/dists/edgy/extras/binary-i386/Packages.gz](http://atp.wicd.net/dists/edgy/extras/binary-i386/Packages.gz) Could not resolve 'atp.wicd.net'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.46 80]

---

### Post by gojetsgo on 2009-10-28
Here's the contents of my sources.list file:

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed main restricted universe multiverse
deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) stable contrib

 ## E17 repository "edevelop.org"
deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17
deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17
deb [http://atp.wicd.net](http://atp.wicd.net) edgy extras
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security restricted main multiverse universe

---

### Post by QIII on 2009-10-28
Looks like your sources list is looking for Edgy, which is way out of date.

Feisty is no longer supported, so the files are not there for you to get at.

You can try

[sudo update-manager -d[/code]

to see if there is still the option to upgrade to Gutsy, but its support may have run out too.

---

### Post by gojetsgo on 2009-10-28
So does that mean I have to do a full reinstall of ubuntu?  Is there any way for me to upgrade from 6.10 to the current version?

---

