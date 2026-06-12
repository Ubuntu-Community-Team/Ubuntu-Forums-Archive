---
title: "Install KDE 3.5 instead of kubuntu-desktop?"
date: 2005-11-17
forum: General Help
---

### Post by Faerine on 2005-11-17
I am currently using Ubuntu with Gnome, and I would like to try KDE. I know I can install kubuntu-desktop, or kde-core, etc. However, according to this thread, [http://www.ubuntuforums.org/showthread.php?t=89255](http://www.ubuntuforums.org/showthread.php?t=89255), there is a release candiate of KDE 3.5, which is not the default kubuntu.  I would like to try this, instead of the old version, so what is the best way to do that?

---

### Post by sdr_ar on 2005-11-17
In the kubuntu Page appears the repositories. These are: 

deb [http://kubuntu.org/packages/kde35rc1](http://kubuntu.org/packages/kde35rc1) breezy main

So what you have to do are this steps:

1) :~$ wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
2) :~$ sudo apt-key add kubuntu-packages-jriddell-key.gpg
3) Edit /etc/apt/sources.list to add the repositories
4) :~$ sudo apt-get update
5) :~$ sudo apt-get install kde

---

### Post by sdr_ar on 2005-11-17
In the kubuntu Page appears the repositories. These are: 

deb [http://kubuntu.org/packages/kde35rc1](http://kubuntu.org/packages/kde35rc1) breezy main

So what you have to do are this steps:

1) Edit /etc/apt/sources.list to add the repositories
2) :~$ sudo apt-get update
3) :~$ wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
4) :~$ sudo apt-key add kubuntu-packages-jriddell-key.gpg
5) :~$ sudo apt-get install kde

---

### Post by sdr_ar on 2005-11-17
Then, if you want, you can install kubuntu-desktop to add all the applications that it offers, but using kde 3.5 rc1

---

### Post by eeknay on 2005-11-18
hi.

If I do this, I end up only upgrading the following packages:
[B]
kdebase-data kdelibs-data kdemultimedia-kappfinder-data[/B]

All other packages are withhold:
[B]  akregator ark arts artsbuilder kaddressbook kamera kappfinder karm kate
  kaudiocreator kcontrol kcron kdeadmin-kfile-plugins kdebase-bin
  kdebase-kio-plugins kdegraphics-kfile-plugins kdelibs-bin kdelibs4-dev
  kdelibs4c2 kdemultimedia-kfile-plugins kdemultimedia-kio-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins
  kdepim-wizards kdeprint kdesktop kdm kedit kfind kghostview khelpcenter
  kicker klaptopdaemon klipper kmail kmenuedit kmilo kmix knetworkconf knotes
  konqueror konqueror-nsplugins konsole kontact kooka kopete korganizer kpdf
  kpf kppp krdc krfb kscd kscreensaver ksmserver ksnapshot ksplash ksvg
  ksysguard ksysguardd kuser kwalletmanager kwifimanager kwin libarts1-dev
  libarts1c2 libartsc0 libartsc0-dev libkcddb1 libkonq4 libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 libktnef1[/B]

This does not do me any good :/

eeknay

---

### Post by Single on 2005-11-18
What i did was install kubuntu-desktop from official ubuntu repo, then add the key and rc1 repo into sources.list and apt-get update && apt-get upgrade.
If u don't have broadband this may take a while though.

---

### Post by eeknay on 2005-11-18
well, I installed kubuntu-desktop a while ago from the official repos. Now I'm just curious and added the new repo in my sources.list, but unfortunally this does not help.

edit: Oh, I see. Once I've installed kubuntu-desktop it somehow prevents stuff from getting installed.

---

### Post by ace2005 on 2005-11-19
A word of advice the best thing to do is add all the repos, for Beta 1, Beta 2 and RC1, Some packages from Beta 1 are not in the RC1 repo

Edit: Looks like they've all been updated and working ok

---

