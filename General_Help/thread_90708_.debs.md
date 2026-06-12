---
title: ".debs"
date: 2005-11-15
forum: General Help
---

### Post by denisesballs on 2005-11-15
A few questions from a rpm-minded guy:

1. Is there a way to apt-get install a .deb file so it installs the missing dependencies like yum install whatever.rpm?

2. Is there a way to install .deb to tell it not to install if it has errors? Everytime I dpkg -i whatever.deb and am missing a dependecy, it installs it anyways even though it doesn work.

3. Can I add a specific package to my sources.list like for this one [http://us.archive.ubuntu.com/ubuntu/pool/main/s/screem/](http://us.archive.ubuntu.com/ubuntu/pool/main/s/screem/) so I can apt-get install screem and it will upgrade it? 

Mostly this all comes down to my troubles building Screem 0.16.

---

### Post by Kyral on 2005-11-15
If Screem is installed an in the Repos then it will be updated with your system as normal.

There is a FINE difference between being installed and configured. It may be installed, but its not configured, so its kinda in limbo. As for installing with Apt, you might. Try it :D

---

### Post by denisesballs on 2005-11-15
[QUOTE=Kyral]If Screem is installed an in the Repos then it will be updated with your system as normal.

There is a FINE difference between being installed and configured. It may be installed, but its not configured, so its kinda in limbo. As for installing with Apt, you might. Try it :D[/QUOTE]

The official repos don't have the newest screem, that mirror does. But I don't know how to add just one package mirror like that.

---

### Post by Kyral on 2005-11-15
Dude, that mirror IS one of the official repos :D

---

### Post by denisesballs on 2005-11-15
[QUOTE=Kyral]Dude, that mirror IS one of the official repos :D[/QUOTE]

I know! But it's not upgrading it! I have all the repos in there, and the backports, and even tried using the dapper ones!

---

### Post by Kyral on 2005-11-15
Its in Dapper. Request a Backport for it

The reason its not upgrading is because its not at that version in Breezy. Yes its there at Dapper, but going to Dapper for one package isn't smart. It should be accepted into Backports :D

---

### Post by denisesballs on 2005-11-15
[QUOTE=Kyral]Its in Dapper. Request a Backport for it

The reason its not upgrading is because its not at that version in Breezy. Yes its there at Dapper, but going to Dapper for one package isn't smart. It should be accepted into Backports :D[/QUOTE]

I know it's not smart. I don't care. If it's in dapper and I use the dapper repos, why wouldn't it upgrade?

---

### Post by Kyral on 2005-11-15
If you use "upgrade" instead of "dist-upgrade" then it will hold back packages that could break the system in the filling of their depends. Even a Dist-Upgrade will sometimes hold back packages

---

### Post by denisesballs on 2005-11-15
```
jesse@jesseubuntu:~$ sudo apt-get install screem
Reading package lists... Done
Building dependency tree... Done
screem is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 474 not upgraded.
```

That would do it if it was there.

---

### Post by Kyral on 2005-11-15
do a ```
sudo apt-get dist-upgrade -s
``` and paste the output

---

### Post by denisesballs on 2005-11-15
```
jesse@jesseubuntu:~$ sudo apt-get dist-upgrade -s
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  imlib1 libpng10-0
The following NEW packages will be installed:
  gdk-imlib11 libgtk2-gladexml-perl libkpathsea4 libparted1.6-13 readline-common tex-common
The following packages have been kept back:
  ant mplayer-386 slib
The following packages will be upgraded:
  alien apache2 apache2-common apache2-mpm-prefork apache2-utils appres artsbuilder aspell audacity autoconf autotools-dev babygimp base-config base-files beforelight binutils
  binutils-static bitmap bluez-cups bluez-pcmcia-support bluez-utils bmp-mp4 bmp-musepack bonobo bsdmainutils bum clamav clamav-base clamav-freshclam cpp cpp-3.4 cpp-4.0 cpuburn
  dbus dbus-1-utils debhelper dialog dmidecode doc-debian dpatch drivel editres eog ethtool evolution evolution-data-server evolution-plugins fastjar fdutils file-roller findutils
  finger flex foomatic-db-engine foomatic-filters fping freeciv-client-gtk freeciv-data freeciv-server fstobdf g++ g++-3.4 g++-4.0 gaim-extendedprefs gcalctool gcc gcc-3.3-base
  gcc-3.4 gcc-3.4-base gcc-4.0 gcc-4.0-base gconf2 gdesklets-data gdk-imlib1 gdm gij gij-4.0 gimp-help-common gimp-help-en glabels glabels-data glabels-dev gnome-about gnome-bin
  gnome-btdownload gnome-desktop-data gnome-icon-theme gnome-iconedit gnome-libs-data gnome-panel gnome-panel-data gnome-spell gnome-system-monitor gnome-themes gnome-utils
  gnome-vlc gnome-volume-manager gnomebaker gnupg gstreamer0.8-lame gtkhtml3.8 hal hal-device-manager hicolor-icon-theme hostname html2text hwdata iceauth ico ifrename imake
  imlib-base imlib11 initramfs-tools inkscape installation-report intltool-debian iso-codes k3b k3blibs kdelibs-bin kdelibs-data kdelibs4c2 krename leafpad less lftp libacl1
  libapr0 libart-dev libart2 libarts1c2 libartsc0 libasound2 libaspell15 libaspell15c2 libattr1 libavc1394-0 libbluetooth1 libbonobo2 libcamel1.2-6 libclamav1 libcommons-cli-java
  libdate-manip-perl libdb1-compat libdbd-mysql-perl libdbi-perl libdbus-1-cil libdbus-qt-1-1c2 libdrm1 libdvdread3 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1
  libedataserver1.2-4 libedataserverui1.2-6 libedit2 libeel2-2 libeel2-data libefs1 libegroupwise1.2-8 libenchant-dev libenchant1c2 libevent-perl libevolution-cil
  libexchange-storage1.2-0 libfaad2-0 libfontenc1 libfribidi0 libfs6 libg++2.8.1.3-glibc2.2 libgcc1 libgcj-common libgcj6 libgcj6-awt libgcj6-common libgconf2-4 libgcrypt11
  libgdk-pixbuf-gnome2 libgdk-pixbuf2 libgecko2.0-cil libgeoip1 libghttp1 libglade-gnome0 libglade0 libglib-perl libglibmm-2.4-1c2 libglibmm-2.4-dev libgnome-desktop-2
  libgnome2-vfs-perl libgnome32 libgnomeprint-bin libgnomeprint-data libgnomeprint15 libgnomesupport0 libgnomeui32 libgnorba27 libgnorbagtk0 libgnutls11 libgpg-error0 libgsl0
  libgtk1.2 libgtk1.2-common libgtk1.2-dev libgtk2-perl libgtkhtml3.8-15 libgtkmm-2.4-1c2 libgtkspell0 libgwrapguile1 libhal-storage1 libhal1 libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libice-dev libice6 libidn11 libijs-0.35 libintl-perl libiw28 libkrb53 libltdl3 libmetacity0 libmodplug0c2 libmono-dev libmono0 libmpcdec3
  libmyspell3c2 libnautilus-extension1 liboaf0 libopenal0 libopencdk8 libosgal-cvs libpanel-applet2-0 libpcap0.8 libpoker-eval libportaudio0 libpq4 libpvm3 libreadline4
  libreadline5 librecode0 libsdl-gfx1.2 libsdl-net1.2 libsdl1.2debian libsdl1.2debian-oss libselinux1 libshout3 libsidplay1 libsigc++-2.0-0c2 libsigc++-2.0-dev libslang2 libslp1
  libsm-dev libsm6 libsndfile1 libspeex1 libsqlite3-0 libssl-dev libssl0.9.7 libstdc++2.10-glibc2.2 libstdc++5 libstdc++6 libstdc++6-4.0-dev libstdc++6-dev libt1-5 libtag1c2
  libtagc0 libtar libtasn1-2 libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libtool libungif4g libvte-common libvte4 libwmf0.2-7 libwpd8c2 libwww-ssl0 libx11-6
  libx11-dev libxau-dev libxau6 libxaw7 libxcomposite1 libxdmcp6 libxext-dev libxext6 libxi-dev libxi6 libxinerama-dev libxinerama1 libxkbfile1 libxml2 libxml2-dev libxml2-utils
  libxmu-dev libxmu-headers libxmu6 libxmuu-dev libxmuu1 libxpm-dev libxpm4 libxrandr-dev libxrandr2 libxres1 libxss1 libxt-dev libxt6 libxtrap-dev libxtrap6 libxtst-dev libxtst6
  libxv-dev libxv1 libxxf86dga1 libxxf86misc1 libxxf86vm1 libzvt2 liferea liferea-gtkhtml listres logrotate lsof m4 makedepend memtest86+ metacity mime-support mono
  mono-assemblies-base mono-classlib-1.0 mono-common mono-devel mono-gac mono-jay mono-jit mono-mcs mono-utils muine nano nautilus nautilus-cd-burner nautilus-data nfs-user-server
  ntp ntp-server ntp-simple ntpdate nvidia-kernel-common nvidia-kernel-source oaf oclock openssl parted pmount po-debconf postfix python-glade2 python-gst python-gtk2
  python-numeric python-parted python-pysqlite2 python-twisted python-xdg python-zopeinterface python2.4-dbus python2.4-glade2 python2.4-gtk2 python2.4-libxml2 python2.4-numeric
  python2.4-pysqlite2 python2.4-twisted python2.4-twisted-bin python2.4-zopeinterface rhythmbox rssh sed sessreg smproxy sox tcl8.4 telnet tetex-base tetex-bin tetex-extra tk8.4
  toshset transcode ttf-mgopen ucf viewres vim vim-common vim-gtk vlc vorbis-tools whois wireless-tools wxvlc x-dev x11perf x11proto-core-dev x11proto-fixes-dev x11proto-input-dev
  x11proto-kb-dev x11proto-randr-dev x11proto-record-dev x11proto-render-dev x11proto-trap-dev x11proto-video-dev x11proto-xext-dev x11proto-xinerama-dev xauth xcalc xclipboard
  xclock xconsole xcursorgen xditview xdpyinfo xdriinfo xev xeyes xf86dga xfd xfontsel xfsprogs xgamma xgc xhost xinit xkbutils xkeyboard-config xkill xload xlogo xlsatoms
  xlsclients xlsfonts xmag xman xmessage xmms-coverviewer xmodmap xmore xpmutils xprop xrandr xrdb xrefresh xresprobe xrgb xset xsetmode xsetpointer xsetroot xsm xstdcmap xterm
  xtrap xvidtune xvinfo xwd xwininfo xwnc xwud zenity
471 upgraded, 6 newly installed, 2 to remove and 3 not upgraded.
```

---

### Post by Kyral on 2005-11-15
There is the problem. us.archive.ubuntu.com hasn't synced back to archive.ubuntu.com in almost 5 days. No wonder its packages are out of date. You'd have to change your sources.list to use archive.ubuntu.com instead of us.archive.ubuntu.com

---

### Post by denisesballs on 2005-11-15
AHHHHHHHHHHHHHHHHHHHHHHHHH! Thanks so much dude!

Why isn't that in there by default?

---

### Post by Kyral on 2005-11-15
Because normally (Read as people should use Breezy ;P) updates don't come out fast enough. But it should be syncing every 6 hours if I remember the mirror guidelines right. There is a reason there are mirrors...

---

