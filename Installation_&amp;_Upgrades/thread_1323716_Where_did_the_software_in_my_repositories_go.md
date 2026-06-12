---
title: "Where did the software in my repositories go?"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by rootless on 2009-11-11
```
me@boltbox:~$ apt-cache show nessus
me@boltbox:~$ 

```

Where did my software go?

```
# deb cdrom:[Xubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.3)]/ karmic main multiverse restricted universe
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse

```

---

### Post by slakkie on 2009-11-11
Gone.. 

[http://packages.ubuntu.com/search?searchon=names&keywords=nessus](http://packages.ubuntu.com/search?searchon=names&keywords=nessus)

---

### Post by rootless on 2009-11-12
Why do you think they did away with nessus? I guess I'll have to compile from source.

---

### Post by slakkie on 2009-11-12
That is a good question, you can ask on #ubuntu-devel or the mailing list..

---

### Post by rootless on 2009-11-22
After coming back to this WAY later, I've discovered nessus has been  replaced by OpenVAS.

```
[B]Package nessus is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  openvas-client[/B]
E: Package nessus has no installation candidate
vermont@boltbox:~/Downloads$ apt-cache show openvas-client
Package: openvas-client
Priority: extra
Section: universe/net
Installed-Size: 1088
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Debian OpenVAS Maintainers <openvas-distro-deb@wald.intevation.org>
Architecture: i386
Version: 2.0.3-2
Replaces: nessus (<< 3), nessusclient
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2.1), libgd2-noxpm (>= 2.0.36~rc1~dfsg) | libgd2-xpm (>= 2.0.36~rc1~dfsg), libgdchart-gd2-noxpm | libgdchart-gd2-xpm, libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.16.0), libpango1.0-0 (>= 1.14.0), libpng12-0 (>= 1.2.13-4), libssl0.9.8 (>= 0.9.8f-5), zlib1g (>= 1:1.1.4)
Filename: pool/universe/o/openvas-client/openvas-client_2.0.3-2_i386.deb
Size: 418662
MD5sum: a61b7dc6690e269f28ba0b5d2a9beb41
SHA1: 2d84a53455aafe3687f7600bb1dc9f678c8d71c9
SHA256: bade2ed26b399753ff21d3695408a3a73b63a669a2dfd48033e03b078ee06ad2
Description: Remote network security auditor, the client
 [B]The OpenVAS Security Scanner is a security auditing tool. It makes
 possible to test security modules in an attempt to find vulnerable
 spots that should be fixed.
 .
 It is made up of two parts: a server, and a client. The server/daemon,
 openvasd, is in charge of the attacks, whereas the client,
 OpenVAS-Client, provides the user a nice X11/GTK+ interface.[/B]
 .
 This package contains the GTK+ client.
Homepage: http://www.openvas.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

I'm so glad we finally got a FULLY open-source vuln scanner, that includes more than just the old vulns for free!

---

