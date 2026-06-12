---
title: "libqt4 broken packages"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by Vishesh on 2009-06-22
Hi I was trying to install Skype and it was giving me the error that libqt4-gui is not installed. So I tried something as simple as -
```

sudo apt-get install libqt4-gui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt4-gui: Depends: libqtgui4 (= 4.5.0-0ubuntu4.1) but 4.5.1-1ubuntu1~jaunty1~ppa1 is to be installed
              Depends: libqt4-svg (= 4.5.0-0ubuntu4.1) but it is not going to be installed
              Depends: libqt4-opengl (= 4.5.0-0ubuntu4.1) but it is not going to be installed
              Depends: libqt4-designer (= 4.5.0-0ubuntu4.1) but it is not going to be installed
              Depends: libqt4-assistant (= 4.5.0-0ubuntu4.1) but it is not going to be installed
E: Broken packages

```Now libqt4-core is already installed. Since I have KDE installed as well as gnome (I keep switching). Anyway since I could find no way to install it I though maybe I could just reinstall the entire libqt4-* lib. So I did a sudo apt-get remove libqt4-*. Now this landed up removing all my KDE applications as well.
Once this was done I though I should reinstall atleast the applications I use, and then KDE. But this is what I get - 
```

sudo apt-get install ktorrent amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amarok: Depends: amarok-common (= 2:2.0.2mysql5.1.30-0ubuntu3) but 2:2.0.90mysql5.1.30-0ubuntu1~jaunty1~ppa2 is to be installed
          Depends: kdebase-runtime (>= 4:4.2.1) but it is not going to be installed
          Depends: kdelibs5 (>= 4:4.2.1) but it is not going to be installed
          Depends: libphonon4 (> 4:4.3.1) but it is not going to be installed
          Depends: libqt4-dbus (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-network (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-opengl (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-script (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-sql (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-svg (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-test (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-webkit (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-xml (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: phonon (> 4:4.3.1) but it is not going to be installed
          Recommends: kdemultimedia-kio-plugins (>= 4:4.1.96) but it is not going to be installed
  ktorrent: Depends: kdebase-runtime (>= 4:4.2.1) but it is not going to be installed
            Depends: kdelibs5 (>= 4:4.2.1) but it is not going to be installed
            Depends: kdepimlibs5 (>= 4:4.2.2) but it is not going to be installed
            Depends: libphonon4 (> 4:4.3.1) but it is not going to be installed
            Depends: libqt4-dbus (>= 4.5.0~+rc1) but it is not going to be installed
            Depends: libqt4-network (>= 4.5.0~+rc1) but it is not going to be installed
            Depends: libqt4-qt3support (>= 4.5.0~+rc1) but it is not going to be installed
            Depends: libqt4-script (>= 4.5.0~+rc1) but it is not going to be installed
            Depends: libqt4-svg (>= 4.5.0~+rc1) but it is not going to be installed
            Depends: libqt4-xml (>= 4.5.0~+rc1) but it is not going to be installed
            Depends: phonon (> 4:4.3.1) but it is not going to be installed
E: Broken packages

```And if I try to install any of these packages I get some dependency errors.
```
sudo apt-get install libqt4-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt4-core: Depends: libqtcore4 (= 4.5.0-0ubuntu4.1) but 4.5.1-1ubuntu1~jaunty1~ppa1 is to be installed
               Depends: libqt4-network (= 4.5.0-0ubuntu4.1) but it is not going to be installed
               Depends: libqt4-script (= 4.5.0-0ubuntu4.1) but it is not going to be installed
               Depends: libqt4-xml (= 4.5.0-0ubuntu4.1) but it is not going to be installed
               Depends: libqt4-dbus (= 4.5.0-0ubuntu4.1) but it is not going to be installed
               Depends: libqt4-test (= 4.5.0-0ubuntu4.1) but it is not going to be installed
E: Broken packages

```Now this is just weird. So now I really don't give a damn about skype I just want kde back. I'm posting my sources.list file as well.
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://in.archive.ubuntu.com/ubuntu/ jaunty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ jaunty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

#KDE
# deb http://ppa.launchpad.net/project-neon/ubuntu hardy main
# deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main

#OpenGl
# deb http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu intrepid main

deb http://ppa.launchpad.net/medigeek/ppa/ubuntu jaunty main
# deb http://ppa.launchpad.net/kubuntu-experimental/ppa/ubuntu jaunty main

#Themes
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main

# Skype packages
deb http://download.skype.com/linux/repos/debian/ stable non-free

deb http://in.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe

```

Any kind of help would really be appreciated !!

---

### Post by zvacet on 2009-06-22
```
sudo apt-get -f install
```

And you can install Skype from [Medibuntu.]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Vishesh on 2009-06-22
No !! Thats doesn't help at all ..

```
sudo apt-get -f install
[sudo] password for vishesh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libqca2 libqimageblitz4 kdeartwork-misc
  kdeplasma-addons-data kdevelop-doc libxine1-x librdf0
  kdebase-runtime-data-common comerr-dev libboost-program-options1.35.0
  quassel-data plasma-desktopthemes-artwork libxine1-misc-plugins libxcb-xv0
  kdevelop-data libsearchclient0 libvncserver0 libapr1 amarok-common
  libxmu-headers python-dev python-qt4-common kde-icons-oxygen libexiv2-5
  libkrb5-dev librasqal1 libglu1-xorg-dev libsqlite0-dev libeet1 dontzap
  libsvn1 libtool redland-utils kdelibs5-data kdeartwork-emoticons
  python-qt4-dbus python-sip4 kdewallpapers libssl-dev qt4-qmake libxcb-shape0
  libxmu-dev libltdl7-dev python2.6-dev libstreamanalyzer0 libfluidsynth1 stk
  kdebase-workspace-data ksysguardd libstrigihtmlgui0 liblcms1-dev libpq-dev
  libkadm55 libkonq5-templates libstk0c2a ktorrent-data libpq5 libstreams0
  exiv2 libtag-extras0 libmng-dev ladcca2 libxcb-shm0 kdebase-runtime-data
  libaprutil1 kdepimlibs-data libmsn0.1 strigi-daemon libxine1-console
  libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
vishesh@vishesh-desktop:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  skype: Depends: libqt4-core (>= 4.2.1) but it is not going to be installed
         Depends: libqt4-gui (>= 4.2.1) but it is not going to be installed
E: Broken packages
vishesh@vishesh-desktop:~$ sudo apt-get install ktorrent amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amarok: Depends: amarok-common (= 2:2.0.2mysql5.1.30-0ubuntu3) but 2:2.0.90mysql5.1.30-0ubuntu1~jaunty1~ppa2 is to be installed
          Depends: kdebase-runtime (>= 4:4.2.1) but it is not going to be installed
          Depends: kdelibs5 (>= 4:4.2.1) but it is not going to be installed
          Depends: libphonon4 (> 4:4.3.1) but it is not going to be installed
          Depends: libqt4-dbus (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-network (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-opengl (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-script (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-sql (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-svg (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-test (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-webkit (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: libqt4-xml (>= 4.5.0~+rc1) but it is not going to be installed
          Depends: phonon (> 4:4.3.1) but it is not going to be installed
          Recommends: kdemultimedia-kio-plugins (>= 4:4.1.96) but it is not going to be installed
  ktorrent: Depends: kdebase-runtime (>= 4:4.2.1) but it is not going to be installed
            Depends: kdelibs5 (>= 4:4.2.1) but it is not going to be installed
            Depends: kdepimlibs5 (>= 4:4.2.2) but it is not going to be installed
            Depends: libphonon4 (> 4:4.3.1) but it is not going to be installed
            Depends: libqt4-dbus (>= 4.5.0~+rc1) but it is not going to be installed
            Depends: libqt4-network (>= 4.5.0~+rc1) but it is not going to be installed
            Depends: libqt4-qt3support (>= 4.5.0~+rc1) but it is not going to be installed
            Depends: libqt4-script (>= 4.5.0~+rc1) but it is not going to be installed
            Depends: libqt4-svg (>= 4.5.0~+rc1) but it is not going to be installed
            Depends: libqt4-xml (>= 4.5.0~+rc1) but it is not going to be installed
            Depends: phonon (> 4:4.3.1) but it is not going to be installed
E: Broken packages

```

---

### Post by Vishesh on 2009-06-23
Fixed. Apparently I had added the kubuntu experimental repository to my sources.list at one time. So my libqt4 that was installed was version 4.5.1 whereas all these softwares required 4.5.0. Therefore the errors.

I removed libqt4 and then installed version 4.5.0 and I was good to go. :-)

---

### Post by jherskow on 2009-08-25
i dont understand what u guys have been saying, im a newbie,  but i have a problem that allot of stuff i try to install have dependencies, and when i try to install them, they have dependencies, and nothing works.'
(im pretty sure the libqt thing is one of them) 

if that fits the problem here, can you please help me?

---

