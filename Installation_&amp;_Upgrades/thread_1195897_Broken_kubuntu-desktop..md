---
title: "Broken kubuntu-desktop."
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by vl4dimir on 2009-06-24
Hi, 

I'm on Ubuntu Jaunty. Earlier, I was installing kubuntu-desktop and the power went off. Now I got a big list of broken things that nothing is fixing. I tried all, can't install/update/upgrade/remove. I thought Ubuntu was perfect and least expected to be hit with this harsh reality of package management. I have had power cuts during install/upgrade on other distros before but never experienced this.

```
emmings@lemmings-desktop:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: ark but it is not going to be installed
                   Depends: dolphin but it is not going to be installed
                   Depends: dragonplayer but it is not going to be installed
                   Depends: kde-window-manager but it is not going to be installed
                   Depends: kde-zeroconf but it is not going to be installed
                   Depends: kdebase-workspace-bin but it is not going to be installed
                   Depends: kdemultimedia-kio-plugins but it is not going to be installed
                   Depends: kdepasswd but it is not going to be installed
                   Depends: kdm but it is not going to be installed
                   Depends: khelpcenter4 but it is not going to be installed
                   Depends: klipper but it is not going to be installed
                   Depends: kmix but it is not going to be installed
                   Depends: konsole but it is not going to be installed
                   Depends: ksnapshot but it is not going to be installed
                   Depends: ksysguard but it is not going to be installed
                   Depends: ksystemlog but it is not going to be installed
                   Depends: kuser but it is not going to be installed
                   Depends: language-selector-qt but it is not going to be installed
                   Depends: okular but it is not going to be installed
                   Depends: software-properties-kde but it is not going to be installed
                   Depends: systemsettings but it is not going to be installed
                   Recommends: akregator but it is not going to be installed
                   Recommends: amarok but it is not going to be installed
                   Recommends: apport-qt but it is not going to be installed
                   Recommends: gwenview but it is not going to be installed
                   Recommends: install-package but it is not going to be installed
                   Recommends: jockey-kde but it is not going to be installed
                   Recommends: kaddressbook but it is not going to be installed
                   Recommends: kamera but it is not going to be installed
                   Recommends: kate but it is not going to be installed
                   Recommends: kde-printer-applet but it is not going to be installed
                   Recommends: kdebase-plasma but it is not going to be installed
                   Recommends: kdebluetooth but it is not going to be installed
                   Recommends: kdegraphics-strigi-plugins but it is not going to be installed
                   Recommends: kdepim-kresources but it is not going to be installed
                   Recommends: kdepim-strigi-plugins but it is not going to be installed
                   Recommends: kdepim-wizards but it is not going to be installed
                   Recommends: kdeplasma-addons but it is not going to be installed
                   Recommends: kdesudo but it is not going to be installed
                   Recommends: kmag but it is not going to be installed
                   Recommends: kmail but it is not going to be installed
                   Recommends: kmousetool but it is not going to be installed
                   Recommends: knotes but it is not going to be installed
                   Recommends: konqueror but it is not going to be installed
                   Recommends: konqueror-nsplugins but it is not going to be installed
                   Recommends: konqueror-plugin-searchbar but it is not going to be installed
                   Recommends: kontact but it is not going to be installed
                   Recommends: kopete but it is not going to be installed
                   Recommends: korganizer but it is not going to be installed
                   Recommends: kpackagekit but it is not going to be installed
                   Recommends: krdc but it is not going to be installed
                   Recommends: krfb but it is not going to be installed
                   Recommends: ktimetracker but it is not going to be installed
                   Recommends: kubuntu-konqueror-shortcuts but it is not going to be installed
                   Recommends: kvkbd but it is not going to be installed
                   Recommends: kwalletmanager but it is not going to be installed
                   Recommends: libqca2-plugin-ossl but it is not going to be installed
                   Recommends: okular-extra-backends but it is not going to be installed
                   Recommends: plasma-widget-network-manager but it is not going to be installed
                   Recommends: plasma-widget-quickaccess but it is not going to be installed
                   Recommends: quassel but it is not going to be installed
                   Recommends: system-config-printer-kde but it is not going to be installed
                   Recommends: update-notifier-kde but it is not going to be installed
E: Broken packages
lemmings@lemmings-desktop:~$ 
```

So, how do I get outta this dep hell now?

Also, my sources.lst
```
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
```

---

### Post by vl4dimir on 2009-06-25
Wow, not even a single reply in 15 hours and is also bogged down to multiple pages, so no further hopes either. Well I guess, the more the monkeys, the more the questions and less the solutions.

You baboontus can keep your shite coloured distro to yourself, I ain't touching it ever again. I'm sure my co-workers will now see the real community of poobuntu. I'm outta here.

---

### Post by dsavi on 2009-06-25
Patience is a virtue, my good man. You have tried sudo apt-get -f, of course?

---

