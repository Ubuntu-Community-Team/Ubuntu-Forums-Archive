---
title: "No gdm, broken packages, no ethernet"
date: 2009-03-09
forum: Hardware
---

### Post by OliverN on 2009-03-09
[COLOR="Red"]EDIT: Solved by reinstall
[/COLOR]
Last night i decided to get rid of kde by doing

```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts cryptsetup debtags desktop-effects-kde digikam dmsetup dolphin enscript foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs-ppds hplip-gui ijsgutenprint jockey-kde k3b kaddressbook kaffeine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-qtcurve kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libflac++6 libgmp3c2 libgsm1 libifp4 libijs-0.35 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 libnjb5 libofa0 libpoppler-qt2 libpostproc1d libpq5 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-dev python-kde3 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 python2.5-dev qca-tls rdiff-backup ruby ruby1.8 scim-bridge-client-qt scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon system-config-printer-kde ttf-arphic-ukai vorbis-tools && sudo apt-get install ubuntu-desktop
```

I set the system to shut down after an hour by doing

```
sudo shutdown -h +60
```

figuring it had to be done by then. I realize now how stupid that was. When I boot I am left with a text-based login. X won't start, never mind gdm. I tried doing

```
sudo dpkg --configure -a && sudo aptitude update && sudo aptitude safe-upgrade 
```

but I can't get even get a wired connection going. I figure that has to be the most important thing right now. I'm absolutely positive there's nothing wrong with my internet connection as I've been able to get a wired connection on the same laptop, running the same system, doing the same procedure previously (plugging the damn thing in). Can anyone recommend some steps? -Besides reinstalling?

---

### Post by directhex on 2009-03-09
You could try manually getting it going with ifconfig and a static IP

---

### Post by OliverN on 2009-03-09
thanks for your reply.

esh, unfortunately my totalitarian isp manages my router so I can't set a static ip. -They're on a contract with my block so in my defense they're extremely cheap.:oops:

anyway, here's another thought: Could I perhaps add a live cd to the repositories and reinstall ubuntu-desktop that way? -If that's possible, what should I add to my sources.list?

---

### Post by directhex on 2009-03-10
> **OliverN said:**
> thanks for your reply.

esh, unfortunately my totalitarian isp manages my router so I can't set a static ip. -They're on a contract with my block so in my defense they're extremely cheap.:oops:

anyway, here's another thought: Could I perhaps add a live cd to the repositories and reinstall ubuntu-desktop that way? -If that's possible, what should I add to my sources.list?

Run "apt-cdrom add" - but it won't work for a livecd, only for an alt install cd

---

### Post by OliverN on 2009-03-10
Should I boot to my regular install and do

```
sudo apt-crom add
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
```

?

Because that doesn't get me anywhere. The cd speeds up but I end up getting the same errors.

---

### Post by Neo_The_User on 2009-03-10
Did you by any chance compile GCC 4.4 from source? I did that and everything you are having, I was having.

---

### Post by OliverN on 2009-03-10
Nope, didn't do that.

Reinstalling is sounding more and more compelling after all. My drives are partitioned sensibly. I just know I'll be deleting *something* important. I'll give it another day. Still googling about.

---

