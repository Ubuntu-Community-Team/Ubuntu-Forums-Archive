---
title: "dpkg: serious warning: files list file for package * missing"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by white_eagle-mk on 2008-12-11
I can't remove the xorg-driver-fglrx package, please help! I get that I need to reinstall the package when i try to remove it w/ 'sudo apt-get remove xorg-driver-fglrx' so I try reinstalling it and I get this. Please bear in mind that there are **LOTS AND LOTS** of many 'serious warnings' like these above (~4000 lines and I still couldn't see the "Reading package lists... Done Building dependency tree Reading state information... Done" lines!

Here it is:

```
dpkg: serious warning: files list file for package `libgnomedesktop2.20-cil' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libwpd8c2a' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libapr1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libtagc0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python2.4-minimal' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `software-properties-gtk' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxcursor-dev' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `abiword-plugin-grammar' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `telepathy-mission-control' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libtar-dev' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libtomcat5.5-java' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `usplash' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `liblivemedia-dev' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `aspell-fr' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libid3tag0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libemail-mime-encodings-perl' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libcupsimage2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libqt4-assistant' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgnutls13' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gimpshop' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `p7zip' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `eclair' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libpango1-ruby1.8' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-id3' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `o3read' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `falconseye-data' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libwrap0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `cups' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgnome-media0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libode0-dev' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `netcat' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `lsof' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-pysqlite2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-pyogg' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `liblockfile1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxau6' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `liblaunchpad-integration1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `liblaunchpad-integration0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libglade2-dev' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `pulseaudio-utils-dbg' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libecore-file0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxcomposite-dev' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gnome-power-manager' missing, assuming package has no files currently installed.
43 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 2:8.552-0ubuntu0.1 (using .../xorg-driver-fglrx_2%3a8.552-0ubuntu0.1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx ...
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_2%3a8.552-0ubuntu0.1_i386.deb (--unpack):
 unable to create updated files list file for package xorg-driver-fglrx: No such file or directory
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_2%3a8.552-0ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
whiteeagle@whiteeagle-laptop:/var/cache/apt/archives$ 

```

Please help me solve this, because I don't have 3D acceleration now :(

---

### Post by taurus on 2008-12-11
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by white_eagle-mk on 2008-12-11
> **taurus said:**
> Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```
Here it is:

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://mk.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://mk.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://mk.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://mk.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu*
## team, and may not be under a free licence. Please satisfy yourself as to*
## your rights to use the software. Also, please note that software in*
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mk.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://mk.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://archive.ubuntu.com/ubuntu/ intrepid main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe main multiverse restricted #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe main multiverse restricted
deb http://security.ubuntu.com/ubuntu/ intrepid-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ intrepid-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-proposed universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-proposed universe main multiverse restricted
# deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
# deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
# deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
# deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
# deb http://ppa.launchpad.net/galaxium/ubuntu hardy main
# deb-src http://ppa.launchpad.net/galaxium/ubuntu hardy main
# deb http://ppa.launchpad.net/banshee-team/ubuntu hardy main
# deb-src http://ppa.launchpad.net/banshee-team/ubuntu hardy main
# deb http://ppa.launchpad.net/do-core/ubuntu hardy main
# deb-src http://ppa.launchpad.net/do-core/ubuntu hardy main
# deb http://ppa.launchpad.net/do-core/ubuntu hardy main
# deb http://ppa.launchpad.net/do-core/ubuntu hardy main
# deb http://ppa.launchpad.net/googlegadgets/ubuntu hardy main #Google gadgets
# deb http://ppa.launchpad.net/awn-core/ubuntu hardy main #AWN
# deb http://ppa.launchpad.net/compiz/ubuntu hardy main #Compiz Fusion
# deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock #Cairo Dock
# deb http://ppa.launchpad.net/tualatrix/ubuntu hardy main #Ubuntu Tweak
# deb http://ppa.launchpad.net/gilir/ubuntu hardy main #Screenlets
# deb http://apt.last.fm/ debian stable
deb http://fr.archive.ubuntu.com/ubuntu intrepid-backports main universe
# deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock

# deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
# deb http://ppa.launchpad.net/mattva01/ubuntu hardy main restricted universe multiverse
# deb http://apt.boxee.tv hardy main
# deb http://ppa.launchpad.net/do-core/ubuntu hardy main
# deb-src http://ppa.launchpad.net/do-core/ubuntu hardy main
# deb-src http://ppa.launchpad.net/do-core/ubuntu hardy main
# deb http://mirror.noreply.org/pub/tor etch main
# deb-src http://mirror.noreply.org/pub/tor etch main
```

---

