---
title: "ument dependencies (gcc-4.0)"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by Reggie on 2005-12-28
Hi,

Whenever I try to install a package with apt I get the following error:

> root@kwebbel:/home/reggie/software/eggdrop1.6.17 # apt-get install tcl8.4-dev tk 8.4-dev
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  cpp-4.0: Depends: gcc-4.0-base (= 4.0.2-3ubuntu1) but 4.0.2-5ubuntu2 is to be installed
  g++-4.0: Depends: gcc-4.0-base (= 4.0.2-3ubuntu1) but 4.0.2-5ubuntu2 is to be installed
  gcc-4.0: Depends: gcc-4.0-base (= 4.0.2-3ubuntu1) but 4.0.2-5ubuntu2 is to be installed
  lib64stdc++6: Depends: gcc-4.0-base (= 4.0.2-3ubuntu1) but 4.0.2-5ubuntu2 is t o be installed
  libgcj6: Depends: gcc-4.0-base (= 4.0.2-3ubuntu1) but 4.0.2-5ubuntu2 is to be installed
  libstdc++6-4.0-dev: Depends: gcc-4.0-base (= 4.0.2-3ubuntu1) but 4.0.2-5ubuntu 2 is to be installed
  tk8.4-dev: Depends: x-dev but it is not going to be installed or
                      xlibs-dev but it is not going to be installed
             Depends: libx11-dev but it is not going to be installed or
                      xlibs-dev but it is not going to be installed
             Depends: libxt-dev but it is not going to be installed or
                      xlibs-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s olution).


When I do apt-get -f install 

> root@kwebbel:/home/reggie/software/eggdrop1.6.17 # apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  alien bug-buddy capplets-data contact-lookup-applet cpp cpp-4.0 debhelper eog evolution evolution-data-server
  evolution-exchange evolution-webcal file-roller firefox g++ g++-4.0 gcalctool gcc gcc-4.0 gconf-editor gconf2 gdm gedit
  gettext gnome-about gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-games
  gnome-gv gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-utils gnome-volume-manager gstreamer0.8-gnomevfs
  gstreamer0.8-misc gstreamer0.8-vorbis gthumb gtkhtml3.6 gtkhtml3.8 gucharmap hal-device-manager hwdb-client
  intltool-debian lib64stdc++6 libbonobo2-0 libbonobo2-common libbonoboui2-0 libcamel1.2-6 libebook1.2-5 libecal1.2-2
  libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-4 libedataserverui1.2-6 libeel2-2 libegroupwise1.2-5
  libegroupwise1.2-8 libexchange-storage1.2-0 libgal2.4-0 libgal2.4-common libgcj6 libgconf2-4 libgnome-desktop-2
  libgnome-menu0 libgnome2-0 libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomecupsui1.0-1 libgnomeui-0
  libgnomevfs2-0 libgnomevfs2-common libgsf-1 libgstreamer-gconf0.8-0 libgtkhtml3.6-18 libgtkhtml3.8-15 libgucharmap4
  libidl0 liblpint-bonobo0 libmetacity0 libnautilus-extension1 liborbit2 libpanel-applet2-0 librsvg2-2 librsvg2-common
  libstdc++6-4.0-dev libtotem-plparser0 lsb lsb-core lsb-cxx lsb-graphics metacity mozilla-firefox
  mozilla-firefox-locale-en-gb nautilus nautilus-cd-burner nautilus-sendto po-debconf python-gnome2 python-pyorbit
  python2.4-gnome2 python2.4-pyorbit rhythmbox totem totem-gstreamer tsclient update-manager update-notifier vino yelp
0 upgraded, 0 newly installed, 122 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 344MB disk space will be freed.
Do you want to continue [Y/n]?


.. how can I fix this ?

---

### Post by Reggie on 2005-12-28
Ok found it. Just reainstall the unmet dependencies with dpkg...

---

