---
title: "Installing KDE"
date: 2005-12-03
forum: General Help
---

### Post by stack445 on 2005-12-03
Is there a way to install KDE windows manager so that i actually have gnome and KDE like so many distro ?

---

### Post by invalid on 2005-12-03
```
sudo apt-get install kubuntu-desktop
```

Cb

---

### Post by 23meg on 2005-12-03
[QUOTE=invalid]```
sudo apt-get install kubuntu-desktop
```

Cb[/QUOTE]
That will install all the Kubuntu suite of apps along with KDE. If you just want the KDE environment, ```
sudo apt-get install kde
``` will do.

---

### Post by mfarquhar on 2005-12-03
[QUOTE=invalid]```
sudo apt-get install kubuntu-desktop
```

Cb[/QUOTE]

i tried this and while it is buggy ( it uninstalled X and is a pain) it also uninstalled GNOME (through aptitude a text based package manager) how do you get BOTH of them to stay:-k 

at least i think it uninstalled GNOME (i know i saw it on the remove list)

if you have the same problems go to [GNOME to KDE switch problems]("http://ubuntuforums.org/showthread.php?t=96253")

---

### Post by aysiu on 2005-12-03
Can you copy and paste the output of the command ```
sudo apt-get install kubuntu-desktop
```? For example, when I type the command in, this is what comes out: ```
sudo apt-get install kubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  adept amarok amarok-gstreamer debtags gtk2-engines-gtk-qt gwenview ivman
  kaffeine kaffeine-gstreamer katapult kde-guidance kde-style-lipstik
  kde-systemsettings kdebluetooth kdm kio-apt kio-locate knetworkconf konserve
  konversation krita ksystemlog kubuntu-artwork-usplash
  kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts libkipi0
  liblockdev1 libopenobex-1.0-0 libpythonize0 libtdb1 openoffice.org2-kde
  python-kde3 python-opengl python2.4-dev python2.4-kde3 python2.4-opengl
  python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex sanekonsole speedcrunch
  ttf-dejavu
Suggested packages:
  python-qt3 libqt0-ruby1.8 libsoap-lite-perl oooqs-kde python-qt3-doc
  libqt3-mt-mysql libqt3-mt-odbc libqt3-mt-psql
Recommended packages:
  libqt-perl
The following NEW packages will be installed:
  adept amarok amarok-gstreamer debtags gtk2-engines-gtk-qt gwenview ivman
  kaffeine kaffeine-gstreamer katapult kde-guidance kde-style-lipstik
  kde-systemsettings kdebluetooth kdm kio-apt kio-locate knetworkconf konserve
  konversation krita ksystemlog kubuntu-artwork-usplash
  kubuntu-default-settings kubuntu-desktop kubuntu-docs
  kubuntu-konqueror-shortcuts libkipi0 liblockdev1 libopenobex-1.0-0
  libpythonize0 libtdb1 openoffice.org2-kde python-kde3 python-opengl
  python2.4-dev python2.4-kde3 python2.4-opengl python2.4-qt3
  python2.4-sip4-qt3 qca-tls qobex sanekonsole speedcrunch ttf-dejavu
0 upgraded, 45 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.1MB/47.2MB of archives.
After unpacking 142MB of additional disk space will be used.
Do you want to continue [Y/n]?n
Abort.
```

---

### Post by mfarquhar on 2005-12-12
when i used aptitude i think i saw GNOME on the remove list
so if i just reinstall GNOME and keep KDE i can have both?

---

### Post by features on 2005-12-12
Yes, by not using aptitude, you will have both.  Aptitude is cool and all, but sometimes it make some weird decisions about want you want and don't want.  Use the command posted 2 above me.

---

