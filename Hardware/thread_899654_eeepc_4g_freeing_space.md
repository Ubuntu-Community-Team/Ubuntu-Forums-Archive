---
title: "eeepc 4g freeing space"
date: 2008-08-24
forum: Hardware
---

### Post by ashadocat on 2008-08-24
I have an eeepc 4g running xubuntu and I'm wandering what packages I don't need. I'm hoping to get every byte I can free free. I obviously don't need cd support or modem support, what packages can I remove that will free up space and are required by modems or cd drives. it would be nice if you put what need those packages to work so others can still find this thread useful.

alright, I found some useful information. sometimes you can get more then one kernel. kernels take up space.

The command uname -a in a terminal will tell you which kernel you are running. you can remove any kernel you are not running. searching linux-image in synaptic will give you a list of available kernels. I managed to free **326 mb**

---

### Post by RedPandaFox on 2008-08-24
Games are an easy one to get rid of?

---

### Post by easybake on 2008-08-24
You could have just done a Core install of xubuntu for the minimal install.

---

### Post by aysiu on 2008-08-25
I hava 4 GB Eee PC.

I installed eeeXubuntu, removed a lot of packages and added in a very few more. Then I upgraded to Ubuntu 8.04.

Right now these are all the Xubuntu packages I do **not** have installed: ```
abiword abiword-common abiword-plugins app-install-data app-install-data-commercial apport apport-gtk apturl avahi-autoipd avahi-daemon bluez-audio bluez-cups bluez-utils bogofilter bogofilter-bdb bogofilter-common brasero ca-certificates cdparanoia cups-pdf cupsddk cupsddk-drivers cupsys cupsys-bsd cupsys-client cupsys-common cupsys-driver-gutenprint displayconfig-gtk doc-base dvd+rw-tools evince-gtk foo2zjs foomatic-db foomatic-db-engine foomatic-db-hpijs freeglut3 gdebi gdebi-core genisoimage ghostscript-x gnome-accessibility-themes gnome-app-install gnome-cards-data gnome-games gnome-games-data gnome-screensaver gnome-system-monitor gnome-system-tools gnumeric-common gnumeric-gtk gtk2-engines-xfce guile-1.6-libs hal-cups-utils hpijs hplip hplip-data im-switch jockey-common jockey-gtk libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libavahi-compat-libdnssd1 libavahi-core5 libavahi-ui0 libbeagle1 libdaemon0 libgadu3 libgdome2-0 libgdome2-cpp-smart0c2a libggz2 libggzcore9 libggzmod4 libgl1-mesa-dri libglut3 libgnomekbd-common libgnomekbd2 libgnomekbdui2 libgoffice-0-6 libgoffice-0-6-common libgphoto2-2 libgphoto2-port0 libgsf-gnome-1-114 libgsl0ldbl libgtk-vnc-1.0-0 libgtkmathview0c2a libgtkspell0 libguile-ltdl-1 libhesiod0 libieee1284-3 libkpathsea4 liblink-grammar4 libmeanwhile1 libnl1 libnm-glib0 libnm-util0 libnss-mdns liboobs-1-4 libotr2 libots0 libperl5.8 libpurple0 libqthreads-12 libsane libscim8c2a libsensors3 libslp1 libsnmp-base libsnmp15 libt1-5 libuniconf4.4 libwpd-stream8c2a libwvstreams4.4-base libwvstreams4.4-extras libxklavier12 libxplc0.3.13 libzephyr3 network-manager network-manager-gnome orage pidgin pidgin-data pidgin-otr ppp python-imaging python-software-properties readahead ristretto samba-common scim scim-gtk2-immodule scim-modules-socket scim-modules-table scim-tables-additional screensaver-default-images smbclient software-properties-gtk system-config-printer-common system-config-printer-gnome tango-icon-theme tango-icon-theme-common thunar-thumbnailers transmission-common transmission-gtk ubufox ubuntu-artwork ubuntu-gdm-themes ubuntu-wallpapers unattended-upgrades update-manager update-manager-core update-notifier update-notifier-common usplash vim-runtime vinagre wvdial xcursor-themes xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-governor-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mcs-plugins-extra xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfwm4-themes xscreensaver-data xscreensaver-gl xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs zenity
```

---

