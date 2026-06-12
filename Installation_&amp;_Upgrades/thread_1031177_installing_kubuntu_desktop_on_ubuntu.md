---
title: "installing kubuntu desktop on ubuntu"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by chao226 on 2009-01-05
Hi I Have recently returned the the world of linux and I currently have a unbuntu installation I am attempting to install KDE desktop on the install so i can switch at boot up.  however when I go into the add remove applications find KDE4 It states my computer type (i386) is not compatable with KDE.  I have a fairly standard system core 2 duo processor and nvidia geforce gfx card.  Is there any way I can install KDE on this system?

Thanks regards Dave

---

### Post by joshmuffin on 2009-01-05
Open a terminal
Applications > Accessories > Terminal
and type:

```
sudo apt-get install kubuntu-desktop
```

---

### Post by chao226 on 2009-01-05
Ok tryed that and the stragest thing it will not allow me to type my pw on the termanal when it asks for it never had this issue before on thetermanal is there another way to install the desktop?

---

### Post by cherva on 2009-01-05
First type ```
sudo su
``` and then when you switch to root terminal just type ```
apt-get install kubuntu-desktop
```
But what KDE do you want ? KDE 3 or KDE 4 ?

---

### Post by chao226 on 2009-01-05
i'm not really aware what the differences are between KDE 3 and 4 i have limited Linux experience and 100% of that experience has been with gnome I have a resonable decent system hardware wise what would you recommend and why?

---

### Post by avtolle on 2009-01-05
I don't use KDE, but from reading threads on this and other forums, KDE 4 is seemingly unstable. The advice I've gleaned from these  other threads is to use KDE 3.5. HTH.

---

### Post by cherva on 2009-01-05
Use Google to see some screenshots of KDE 3 and KDE 4 and decide I can't give you an advice because I don't use KDE. Fro me KDE 3 is ... too shiny and KDE 4 better looking, but on the other side KDE 4 is young and lack some configurations, but again I just took a quick look in a virtual machine I never actually used it.

---

### Post by chao226 on 2009-01-06
not that botherd either way tbh I installed KDE 4 and its only purpose is to easy my family into linux I heard and got confimation after installing that is good more of a windows feel to it and after installing I have to say yes it does.  so KDE stays on my system for the family to use i however and sticking with gnome.  Thanks for all the help guys apriciate it.


Dave

---

### Post by cherva on 2009-01-08
Have Fun :)

---

### Post by Sjums07 on 2009-01-09
Help needed here :D well, i used ```
sudo apt-get install kubuntu-desktop
``` and i was not satisfied with the result :p so i wish to go back to the ubuntu desktop :D but how do i do? :O ```
sudo apt-get autoremove kubuntu-desktop
``` or ```
sudo apt-get install ubuntu-desktop
``` won't do anything -.- the autoremove tells it does something, but i can't figure out what ;) all the KDE apps are still there and it looks like the same :O and install ubuntu-desktop says i has it already ;s please help me get back my normal Gnome look and loginscreen!! :D

---

### Post by Hooya on 2009-01-09
Your old Gnome is still on your system.  Log out, choose to start a Gnome session instead of KDE on the login screen, then make sure you use that as the default setting.

Once you're in Gnome, try
$sudo aptitude remove kubuntu-desktop && sudo aptitude autoclean

Or just go into Synaptic, find kubuntu-desktop, and mark it for complete removal.

---

### Post by Sjums07 on 2009-01-09
hmm, the kde apps are still there :/ and my login screen is still the kde :O and the shutdown screen say "kubuntu" :S ANNOYING! (; else thanks xD other ideas? :D

---

### Post by cherva on 2009-01-09
It's a little long, but I hope it helps  
FOR 8.10 :```
sudo apt-get remove adept akregator amarok amarok-common amarok-engine-xine apport-qt ark dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk-qt-engine guidance-power-manager gwenview hpijs-ppds hplip-gui ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdeplasma-addons-libs4 kdesudo kdm kfind kgrubeditor khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact konversation kopete korganizer krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libcapseo0 libcaptury0 libclucene0ldbl libdbus-1-qt3 libdbus-qt-1-1c2 libexiv2-4 libfftw3-3 libflac++6 libgeoip1 libifp4 libk3b3 libkcddb4 libkdecorations4 libkdepim4 libkholidays4 libkipi-common libkipi5 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 liblua50 liblualib50 libmimelib4 libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libokularcore1 libphonon4 libplasma2 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libraptor1 librasqal0 librdf0 libruby1.8 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libtunepimp5 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxvmc1 libzip1 mediamanager mysql-common network-manager-kde okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme phonon phonon-backend-gstreamer phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasmoid-quickaccess python-kde4 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 qt4-qtconfig raptor-utils redland-utils ruby ruby1.8 software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dustin update-manager-kde update-notifier-kde && sudo apt-get install ubuntu-desktop
```
FOR 8.04: ```
 sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts cryptsetup debtags desktop-effects-kde digikam dmsetup dolphin enscript foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hpijs-ppds hplip-gui ijsgutenprint jockey-kde k3b kaddressbook kaffeine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-qtcurve kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libflac++6 libgmp3c2 libgsm1 libifp4 libijs-0.35 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw3 libkdepim1a libkexiv2-3 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 libnjb5 libofa0 libpoppler-qt2 libpostproc1d libpq5 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-dev python-kde3 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 python2.5-dev qca-tls rdiff-backup ruby ruby1.8 scim-bridge-client-qt scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon system-config-printer-kde ttf-arphic-ukai vorbis-tools && sudo apt-get install ubuntu-desktop 
```

---

### Post by Sjums07 on 2009-01-09
i don't hope you wrote that yourselvf? xD

---

### Post by Sjums07 on 2009-01-09
phew :D that worked ;D thanks a lot :p never play with kde-desktop xD only the full kde in kubuntu xD

---

### Post by Hooya on 2009-01-09
In the future you could use
$sudo apt-get install kde-core
That will give you the apps and ability to login to a KDE desktop, but leave GDM for your login manager and otherwise leave your system alone.

---

### Post by Sjums07 on 2009-01-11
well, i think kde has a nice look, but it doesnt work properly on my machine :p so i'll forget it xD

---

