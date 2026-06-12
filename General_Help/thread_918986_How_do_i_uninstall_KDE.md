---
title: "How do i uninstall KDE"
date: 2008-09-13
forum: General Help
---

### Post by Jonathan45 on 2008-09-13
Hi.
Today i installed KDE4 Through synaptic but KDE has flaws and made ubuntu unstable...
can i uninstall KDE in synaptic by uninstalling the KDE packages?
Please help if i cant get help soon im gonna have 2 uninstall ubuntu.
 PS ive already tried the sudo apt-get remove codes but it failed...

---

### Post by cdtech on 2008-09-13
Have you tried the package manager?

---

### Post by cdtech on 2008-09-13
Here's a post with a possible solution and links.
[http://ubuntuforums.org/showthread.php?t=677588](http://ubuntuforums.org/showthread.php?t=677588)

---

### Post by Jonathan45 on 2008-09-13
can i uninstall KDE4 with Synaptic?
or will i screw up the system more?!

---

### Post by uberlube on 2008-09-13
It will probably screw things up more. :lolflag:

---

### Post by Jonathan45 on 2008-09-13
ok

---

### Post by Jonathan45 on 2008-09-13
if i remove KDE and reinstall gnome will my stuff be there or will everything disappear?
By the way how do i re-install gnome?

---

### Post by Atsuko on 2008-09-13
> sudo apt-get remove kde4-core
If you didn't remove gnome before it will still be there just choose it in the new session when you login.

---

### Post by Jonathan45 on 2008-09-15
thank you very much! i was close to uninstall ubuntu because of it thank you!!

---

### Post by Jonathan45 on 2008-09-18
Hi i tried it now but nothing happened...

---

### Post by hyperman on 2010-04-20
well found something for you
```
sudo apt-get remove python-packagekit ksystemlog libqscintilla2-5 libpackagekit-glib11 krdc krfb kde-zeroconf kppp userconfig libkonq5-templates libqca2 kipi-plugins libksane0 update-notifier-kde libkonqsidebarplugin4 kdebase-runtime-data-common libpolkit-dbus2 libkorundum4-ruby1.8 kubuntu-default-settings libqt4-qt3support kubuntu-desktop kubuntu-firefox-installer libqt4-phonon libkabcommon4 libxine1-x ktorrent-data libk3b6 kpackagekit plasma-widget-facebook libindicate-qt0 libqca2-plugin-ossl ksnapshot libpolkit-qt0 libkipi6 kdepim-groupware libotr2 libqtscript4-network konqueror-nsplugins libqt4-test libqt4-script libknotificationitem1 libqt4-designer libkleo4 libqt4-dbus language-selector-qt libsmokeqt4-2 libjpeg-progs libqtscript4-gui plasma-widget-kimpanel gwenview kdelibs5 libxcb-xv0 kubuntu-docs printer-applet quassel plasma-scriptengine-python libkontactinterfaces4 klipper libmimelib4 plasma-widget-kubuntu-qa-feedback kaddressbook kontact kdebase-workspace-bin kwalletmanager usb-creator-kde libpoppler-qt4-3 ibus-qt4 libkexiv2-7 ksysguard libokularcore1 libtag-extras1 libexiv2-5 mysql-server-core-5.1 libkcddb4 konq-plugins apturl-kde libscim8c2a kdepim-kresources libqtscript4-sql kdegraphics-strigi-plugins dolphin plasma-dataengines-addons khelpcenter4 kdesudo policykit liblzma0 k3b-data libqtscript4-xml kde-style-qtcurve libqt4-xmlpatterns libqt4-sql-sqlite pinentry-gtk2 libsmokekde4-2 libakonadiprivate1 konsole libstrigiqtdbusclient0 korganizer openoffice.org-kde k3b libsoprano4 ktimetracker akonadi-server akregator openoffice.org-style-oxygen kde-icons-oxygen libqt4-help python-qt4 kamera ijsgutenprint ark libkpgp4 kde-window-manager libclucene0ldbl network-manager konqueror-plugins kvkbd libkonq5 libkdepim4 amarok-utils plasma-widget-indicatordisplay libkdecorations4 libqimageblitz4 gtk2-engines-qtcurve python-sip4 phonon-backend-xine libksieve4 kfind ttf-arphic-uming dragonplayer kdebase-bin kdepimlibs-data plasma-widget-folderview kdm speedcrunch pinentry-qt4 amarok gnupg-agent libpolkit-grant2 software-properties-kde libpackagekit-qt11 libvncserver0 libao2 amarok-common libkwineffects1 libxine1-console plasma-widgets-addons knotes soprano-daemon kdepim-runtime-libs4 libqt4-sql foomatic-db-gutenprint libkopete4 libqt4-svg kdebase-workspace-data kdebase-workspace-libs4+5 konqueror libqt4-xml libzip1 install-package cdrdao kdebase-workspace-kgreet-plugins packagekit libqt4-assistant gdebi-kde libplasma3 libqt4-ruby1.8 plasma-dataengines-workspace plasma-widget-lancelot libxine1-misc-plugins ksysguardd kdepimlibs5 update-manager-kde plasma-widget-quickaccess kdelibs-bin kdebluetooth kwin-style-qtcurve kdepim-runtime-data ktorrent jockey-kde liblancelot0 kdemultimedia-kio-plugins libstreams0 python-qt4-dbus libqt4-webkit libepub0 konq-plugins-l10n exiv2 kopete kdelibs5-data plasma-widget-googlecalendar kdebase-runtime quassel-data libqtscript4-uitools kdepim-wizards kdebase-data libqt4-sql-mysql kate kmail liblastfm0 libqt4-scripttools kubuntu-artwork-usplash libxcb-shape0 libqtscript4-core libxcb-shm0 systemsettings kdebase-runtime-data kdebase-plasma system-config-printer-kde apport-kde kdepim-runtime kdebase-runtime-bin-kde4 oxygen-cursor-theme plasma-widget-networkmanagement konqueror-plugin-searchbar okular kmousetool kdepim-strigi-plugins plasma-widgets-workspace libmsn0.1 hpijs-ppds kmag libxine1-bin libkdcraw7 kubuntu-konqueror-shortcuts python-kde4 okular-extra-backends kdepasswd kmix libstreamanalyzer0 libpolkit2 kcm-gtk packagekit-backend-apt libxine1 

```

that's all the packages that install when installing KDE from sympatic
enjoy

---

### Post by Untitled_No4 on 2010-04-20
Can you tell us how you installed KDE in the first place?

---

