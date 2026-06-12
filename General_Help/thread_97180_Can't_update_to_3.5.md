---
title: "Can't update to 3.5"
date: 2005-11-30
forum: General Help
---

### Post by tagbre on 2005-11-30
I've been trying to update to KDE 3.5 since yesterday but I can't finish downloading packages, I keep getting a size mismatch in some of them:

tom@dhcp-3573-201:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  akregator kaddressbook karm kdegraphics-kfile-plugins kdenetwork-filesharing
  kdepim-kio-plugins kdepim-wizards kmail knotes kontact korganizer
  libkpimexchange1 libkpimidentities1 superkaramba
The following packages will be upgraded:
  ark arts artsbuilder giftui kamera kappfinder kate kaudiocreator kcontrol
  kcron kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins
  kdegames-card-data kdelibs-bin kdelibs-data kdelibs4c2
  kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins
  kdemultimedia-kio-plugins kdenetwork-kfile-plugins kdepasswd kdeprint
  kdesktop kdm kfind kghostview khelpcenter kicker klaptopdaemon klipper
  kmahjongg kmenuedit kmilo kmix knetworkconf konq-plugins konqueror
  konqueror-nsplugins konsole kopete kpdf kpf krdc krfb kscreensaver ksmserver
  ksnapshot ksplash ksvg ksysguard ksysguardd kuser kwin libarts1c2 libartsc0
  libkcddb1 libkdegames1 libkonq4 libksieve0 libktnef1
62 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
Need to get 87.5kB/66.6MB of archives.
After unpacking 9060kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://kubuntu.org](http://kubuntu.org) breezy/main libksieve0 4:3.5.0-0ubuntu0breezy1 [38.3kB]Get:2 [http://kubuntu.org](http://kubuntu.org) breezy/main libktnef1 4:3.5.0-0ubuntu0breezy1 [49.3kB]
Fetched 49.3kB in 0s (70.3kB/s)
Failed to fetch [http://kubuntu.org/packages/kde35/pool-breezy/kdepim/libksieve0_3.5.0-0ubuntu0breezy1_i386.deb](http://kubuntu.org/packages/kde35/pool-breezy/kdepim/libksieve0_3.5.0-0ubuntu0breezy1_i386.deb)  Size mismatch
Failed to fetch [http://kubuntu.org/packages/kde35/pool-breezy/kdepim/libktnef1_3.5.0-0ubuntu0breezy1_i386.deb](http://kubuntu.org/packages/kde35/pool-breezy/kdepim/libktnef1_3.5.0-0ubuntu0breezy1_i386.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by barbarian on 2005-11-30
Hello,

You should get the keys before upgade:

1. wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)

2. sudo apt-key add kubuntu-packages-jriddell-key.gpg

instuctions here:

[http://kubuntu.org/announcements/kde-35.php](http://kubuntu.org/announcements/kde-35.php)

---

### Post by tagbre on 2005-11-30
But I did get the keys...:???:

---

