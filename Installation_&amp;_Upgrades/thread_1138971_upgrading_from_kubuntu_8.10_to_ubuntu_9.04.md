---
title: "upgrading from kubuntu 8.10 to ubuntu 9.04"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by matt_30 on 2009-04-26
as the title states is there a way to upgrade to ubuntu jaunty on a kubuntu 8.10 instalation without doing a clean slate install?

---

### Post by zvacet on 2009-04-26
Upgrade to Kubuntu and then replace desktops.For that run in terminal

```
sudo apt-get remove akregator amarok amarok-common apport-qt ark cdrdao dolphin dontzap dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk2-engines-qtcurve gwenview hpijs-ppds ijsgutenprint install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-style-qtcurve kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdesudo kdm kfind khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete korganizer kpackagekit krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent ktorrent-data kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libao2 libaudio2 libavahi-qt3-1 libboost-program-options1.35.0 libclucene0ldbl libdbus-qt-1-1c2 libeet1 libexiv2-5 libflac++6 libgeoip1 libk3b3 libk3b3-extracodecs libkcddb4 libkdecorations4 libkdepim4 libkexiv2-7 libkholidays4 libkipi6 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 libloudmouth1-0 liblua50 liblualib50 libmad0 libmimelib4 libmodplug0c2 libmpcdec3 libmsn0.1 libmysqlclient15off libokularcore1 libpackagekit-glib11 libpackagekit-qt11 libphonon4 libplasma3 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqedje0 libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqzion0 libraptor1 librasqal1 librdf0 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libzip1 mysql-common okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme packagekit packagekit-backend-apt phonon phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasma-widget-network-manager plasma-widget-quickaccess python-dev python-kde4 python-packagekit python-plasma python-qt4 python-qt4-common python-qt4-dbus python-sip4 python2.6-dev qt4-qtconfig quassel quassel-data raptor-utils redland-utils software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dejavu ttf-dejavu-extra update-manager-kde update-notifier-kde && sudo apt-get install ubuntu-desktop
```

---

