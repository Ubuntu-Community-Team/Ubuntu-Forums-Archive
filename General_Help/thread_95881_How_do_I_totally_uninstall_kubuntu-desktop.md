---
title: "How do I totally uninstall kubuntu-desktop?"
date: 2005-11-27
forum: General Help
---

### Post by Jengu on 2005-11-27
```

apt-get remove kubuntu-desktop

```

Basically does nothing. KDE and all its apps stay installed. How do I remove kubuntu-desktop completely?

---

### Post by Xian on 2005-11-27
This [PAGE](http://packages.ubuntu.com/breezy/misc/kubuntu-desktop) lists all the deps of kubuntu-desktop. Remove as little or as much as you like. Some are system files and will need to stay of course. Uninstalling kdelibs would probably take out most of them.

---

### Post by Jengu on 2005-11-27
That's not really optimal. I can tell a ton of those packages are needed whether you have ubuntu-desktop or kubuntu-desktop, but it's going to be a major pain in the arse to figure out which I need to keep if I want Gnome to keep working. Is there some way I can tell it to remove all kubuntu-desktop dependencies except those that ubuntu-desktop also depends on? Seems sort of absurd that Ubuntu has no easy install/uninstall option for this.

---

### Post by aysiu on 2005-11-27
[QUOTE=Jengu]I can tell a ton of those packages are needed whether you have ubuntu-desktop or kubuntu-desktop, but it's going to be a major pain in the arse to figure out which I need to keep if I want Gnome to keep working. Is there some way I can tell it to remove all kubuntu-desktop dependencies except those that ubuntu-desktop also depends on?[/QUOTE] I can't guarantee this'll work, but try copying and pasting this into a terminal: ```
sudo apt-get remove adept akregator amarok amarok-gstreamer ark arts debtags enscript gtk2-engines-gtk-qt gwenview imagemagick ivman kaddressbook kaffeine kaffeine-gstreamer kamera kappfinder karm katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdm kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror-nsplugins konserve konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksvg ksysguard ksysguardd ksystemlog kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager kwin libgadu3 libgpgme11 libjpeg-progs libkcal2a libkcddb1 libkdepim1 libkipi0 libkleopatra0a libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmimelib1a libopenobex-1.0-0 libpythonize0 libsensors3 libtdb1 openoffice.org2-kde poster psutils python-kde3 python-opengl python2.4-dev python2.4-kde3 python2.4-opengl python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex sanekonsole speedcrunch ttf-dejavu xlibs
``` Where did I get this? I have only Gnome and XFCE installed on my current installation (I have multiple Ubuntus--don't ask).

So I typed in ```
sudo apt-get install kubuntu-desktop
``` and those were the packages Ubuntu was going to install before I hit cancel. So removing those should not affect your ubuntu-desktop package.

I don't vouch for this, as I haven't tried it, but it should work.

P.S. If it does work, please let me know, and I'll make this into a HowTo somewhere.

---

### Post by Enzogram on 2008-02-15
> **Xian said:**
> This [PAGE](http://packages.ubuntu.com/breezy/misc/kubuntu-desktop) lists all the deps of kubuntu-desktop. Remove as little or as much as you like. Some are system files and will need to stay of course. Uninstalling kdelibs would probably take out most of them.

If you used the Synaptic Package Manager it should have created a log of what packages you installed with the kubuntu-desktop package. It should be under File->History. I decided to test our kubuntu-desktop today, and here are the files that were required:

Good luck :P

---

