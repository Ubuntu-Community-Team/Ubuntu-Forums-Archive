---
title: "Broken Packages Problem"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by sarthorks on 2009-06-29
Please help me!
I tried to install some dependencies from the internet as those versions were not available in synaptic. I ended up "breaking dependencies". I have searched a lot, but i cant solve my problem. 

```

sarthak@sarthorks:~$ sudo apt-get install --fix-broken
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  airstrike-common wx2.6-headers trigger-data kdelibs-data java-common
  openoffice.org-hyphenation-en-us hannah-data mysql-common libempathy-common
  linux-libc-dev gcc-3.4-base wx2.4-headers xmoto-data stellarium-data
  armagetronad-common libpthread-stubs0-dev libpthread-stubs0 maxima-doc
  libgtk1.2-common realtimebattle-common wx2.8-headers liquidwar-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  aajm acl acpi acpi-support acpid adduser adobe-flashplugin airstrike
  alacarte alsa-base alsa-utils anacron apmd apparmor apparmor-utils apport
  apport-gtk apt apt-utils aptitude apturl armagetronad aspell aspell-en at
  at-spi audacity avahi-autoipd avahi-daemon base-files base-passwd bash
  bash-completion bc belocs-locales-bin bind9-host binfmt-support binutils
  binutils-static blender bloboats bluez-audio bluez-cups bluez-gnome
  bluez-utils bogofilter bogofilter-bdb brasero brltty brltty-x11 bsdmainutils
  bsdutils bsh bug-buddy bzip2 ca-certificates camorama capplets-data
  cdparanoia cdrdao cheese cli-common comix command-not-found compiz
  compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main
  compiz-gnome compiz-plugins compizconfig-backend-gconf console-setup
  console-terminus console-tools consolekit contact-lookup-applet coreutils
  cpio cpp cpp-3.4 cpp-4.2 cron cups-pdf cupsddk cupsddk-drivers cupsys
  cupsys-bsd cupsys-client cupsys-driver-gutenprint dash dbus dbus-x11 dc
  dcraw debconf debconf-i18n debianutils defoma deluge-torrent
  deluge-torrent-common deskbar-applet desktop-file-utils dhcdbd dhcp3-client
  dhcp3-common dictionaries-common diff displayconfig-gtk diveintopython
  dmidecode dnsutils doc-base docbook-xml dosfstools dpkg dvd+rw-tools
  e2fslibs e2fsprogs ed eject ekiga empathy empathy-megaphone-applet
  engauge-digitizer eog espeak ethtool evince evolution evolution-data-server
  evolution-exchange evolution-plugins evolution-webcal f-spot
  fast-user-switch-applet fdutils file file-roller findutils finger firefox
  firefox-3.0 firefox-3.0-gnome-support firefox-gnome-support
  flashplugin-nonfree fontconfig fontconfig-config foo2zjs foomatic-db-engine
  foomatic-db-hpijs foomatic-filters fortune-mod fortunes-min freeglut3
  friendly-recovery ftp fuse-utils g++ g++-3.4 g++-4.2 gamin gcalctool gcc
  gcc-3.4 gcc-4.2 gconf-editor gconf2 gconf2-common gdb gdebi gdebi-core
  gdk-imlib11 gdk-imlib11-dev gdm gedit genisoimage gettext gettext-base
  ghostscript ghostscript-x gimp gimp-gnomevfs gimp-help-en gimp-python gksu
  gnome-accessibility-themes gnome-app-install gnome-applets
  gnome-applets-data gnome-bluetooth gnome-control-center gnome-doc-utils
  gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag
  gnome-media gnome-media-common gnome-menus gnome-mount
  gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-panel-data
  gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver
  gnome-session gnome-settings-daemon gnome-spell gnome-system-monitor
  gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes
  gnome-user-guide gnome-utils gnome-volume-manager gnupg gnuplot-nox gpgv
  gpredict grep groff-base grub gsfonts gstreamer0.10-alsa
  gstreamer0.10-ffmpeg gstreamer0.10-gnomevfs gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps
  gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly
  gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gtk2-engines
  gtk2-engines-murrine gtk2-engines-pixbuf gtk2-engines-ubuntulooks
  gtkhtml3.14 gucharmap guidance-backends guile-1.6-libs gvfs gvfs-backends
  gvfs-fuse gzip hal hal-cups-utils hannah hdparm hostname hotkey-setup hpijs
  hplip human-theme hwtest hwtest-gtk iamerican ibritish ifupdown imlib-base
  info initramfs-tools initscripts inputattach iproute iptables iputils-arping
  iputils-ping iputils-tracepath ispell jockey-common jockey-gtk kdelibs4c2a
  kdissert kgoldrunner klogd ktron lame language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-selector
  language-selector-common language-support-en
  language-support-translations-en language-support-writing-en laptop-detect
  laptop-mode-tools launchpad-integration less lftp lib64gcc1 lib64stdc++6
  liba52-0.7.4 libaa1 libacl1 liballegro4.2 libalut0 libao2 libapm1
  libarchive1 libart-2.0-2 libart2.0-cil libarts1c2a libartsc0 libasound2
  libaspell15 libatk1.0-0 libatk1.0-dev libatm1 libatspi1.0-0 libattr1
  libaudio2 libaudiofile0 libavahi-client3 libavahi-common3
  libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1 libavahi-qt3-1
  libavahi-ui0 libavc1394-0 libavcodec-dev libavcodec0d libavcodec1d
  libavformat-dev libavformat0d libavformat1d libavutil-dev libavutil1d
  libbeagle1 libbind9-30 libblkid1 libbluetooth2 libbonobo2-0 libbonoboui2-0
  libboost-date-time1.34.1 libboost-filesystem1.34.1 libboost-thread1.34.1
  libbrlapi0.5 libbtctl4 libbz2-1.0 libc6 libc6-amd64 libc6-dev libc6-i686
  libcaca0 libcairo-perl libcairo2 libcairo2-dev libcairomm-1.0-1
  libcamel1.2-11 libcap1 libcdaudio1 libcdio-cdda0 libcdio-paranoia0 libcdio7
  libcdparanoia0 libchromexvmc1 libchromexvmcpro1 libck-connector0 libcomerr2
  libcompizconfig0 libconsole libcroco3 libcucul0 libcupsimage2 libcupsys2
  libcurl3 libcurl3-gnutls libcv-dev libcv1 libcvaux-dev libcvaux1 libcwidget3
  libdaemon0 libdatrie0 libdb4.6 libdbus-1-3 libdbus-glib-1-2 libdc1394-13
  libdc1394-13-dev libdecoration0 libdeskbar-tracker libdevmapper1.02.1
  libdirectfb-1.0-0 libdjvulibre15 libdmx1 libdns32 libdns35 libdrm2 libdv4
  libdvbpsi4 libdvdnav4 libdvdread3 libebml0 libebook1.2-9 libecal1.2-7
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9
  libedataserverui1.2-8 libedit2 libeel2-2 libegroupwise1.2-13 libelfg0
  libempathy-gtk-common libempathy-gtk11 libempathy11 libenchant1c2a
  libesd-alsa0 libespeak1 libexchange-storage1.2-3 libexempi3 libexif12
  libexpat1 libexpat1-dev libfaad0 libffi4 libfftw3-3 libflac++6 libflac8
  libflickrnet2.1.5-cil libfontconfig1 libfontconfig1-dev libfontenc1
  libfreebob0 libfreetype6 libfreetype6-dev libfribidi0 libfs6 libfuse2
  libgadu3 libgail-common libgail-gnome-module libgail18 libgamin0 libgc1c2
  libgcc1 libgconf2-4 libgconf2.0-cil libgcrypt11 libgd2-noxpm
  libgdata-google1.2-1 libgdata1.2-1 libgdbm3 libgdk-pixbuf-dev libgdk-pixbuf2
  libgfortran2 libggz2 libggzcore9 libggzmod4 libgif4 libgimp2.0 libgksu2-0
  libgl1-mesa-dev libgl1-mesa-dri libgl1-mesa-glx libglade2-0 libglade2.0-cil
  libglew1.5 libglib-perl libglib1.2-dev libglib1.2ldbl libglib2.0-0
  libglib2.0-cil libglib2.0-dev libglibmm-2.4-1c2a libglu1-mesa
  libglu1-mesa-dev libglu1-xorg-dev libglut3 libgmime-2.0-2 libgmime2.2-cil
  libgmp3c2 libgmyth0 libgnome-desktop-2 libgnome-keyring0 libgnome-mag2
  libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech7
  libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0
  libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl
  libgnome2.0-cil libgnomebt0 libgnomecanvas2-0 libgnomecups1.0-1
  libgnomekbd-common libgnomekbd2 libgnomekbdui2 libgnomeprint2.2-0
  libgnomeprintui2.2-0 libgnomeui-0 libgnomevfs2-0 libgnomevfs2-bin
  libgnomevfs2-common libgnomevfs2-extra libgnutls13 libgomp1 libgpg-error0
  libgpgme11 libgphoto2-2 libgphoto2-port0 libgpmg1 libgpod-common libgpod3
  libgraphviz4 libgs8 libgsf-1-114 libgsl0ldbl libgsm1 libgsm1-dev
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk-vnc-1.0-0
  libgtk1.2 libgtk1.2-dev libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil
  libgtk2.0-dev libgtkhtml2-0 libgtkhtml3.14-19 libgtkhtml3.16-cil
  libgtkmm-2.4-1c2a libgtksourceview1.0-0 libgtksourceview2.0-0 libgtkspell0
  libgtop2-7 libgucharmap6 libguile-ltdl-1 libgutenprint2 libgvfscommon0
  libgweather-common libgweather1 libhal-storage1 libhal1 libhesiod0
  libhighgui-dev libhighgui1 libhsqldb-java libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhunspell-1.1-0 libice-dev libice6
  libicu38 libid3tag0 libidl0 libidn11 libiec61883-0 libieee1284-3
  libiptcdata0 libisc32 libisc35 libisccc30 libisccfg30 libiso9660-5 libiw29
  libjack0 libjasper1 libjaxp1.3-java libjline-java libjpeg62 libjpeg62-dev
  libkdegames1 libkeyutils1 libkpathsea4 libkrb53 liblame0
  liblaunchpad-integration1 liblcms1 libldap-2.4-2 liblircclient0
  liblocale-gettext-perl libloudmouth1-0 liblpint-bonobo0 libltdl3 liblua5.1-0
  liblua50 liblualib50 liblwres30 liblzo2-2 libmad0 libmagic1 libmagick10
  libmatroska0 libmeanwhile1 libmetacity0 libmissioncontrol-client0
  libmissioncontrol-server1 libmms0 libmng1 libmodplug0c2
  libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil
  libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil
  libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-security1.0-cil
  libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil
  libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil
  libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil
  libmono-system2.0-cil libmono0 libmono1.0-cil libmono2.0-cil libmpcdec3
  libmpeg2-4 libmtp7 libmusicbrainz4c2a libmysqlclient15off libnautilus-burn4
  libnautilus-extension1 libncurses5 libncursesw5 libndesk-dbus-glib1.0-cil
  libndesk-dbus1.0-cil libneon27 libnet-dbus-perl libnetpbm10 libnewt0.52
  libnl1 libnm-glib0 libnm-util0 libnotify1 libnspr4-0d libnss-mdns libnss3-1d
  libntfs-3g23 libode0debian1 libogg-dev libogg0 liboil0.3 liboobs-1-4
  libopal-2.2 libopenal0a libopencdk10 libopenexr2ldbl libopenobex1
  libopenspc0 liborbit2 libotr2 libpam-gnome-keyring libpam-modules libpam0g
  libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpango1.0-dev
  libpaper-utils libpaper1 libparted1.7-1 libpcap0.8 libpcre3 libperl5.8
  libphysfs-1.0-0 libpisock9 libpisync1 libpixman-1-0 libpixman-1-dev
  libpng12-0 libpng12-dev libpolkit-dbus2 libpolkit-gnome0 libpolkit-grant2
  libpolkit2 libpoppler-glib2 libpoppler2 libpopt0 libportaudio0 libpostproc1d
  libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l
  libpt-1.10.10-plugins-v4l2 libpth20 libpulse-browse0 libpulse0 libpulsecore5
  libpurple0 libqt3-mt libqt4-core libqt4-gui libqthreads-12 librarian0
  libraw1394-8 libraw1394-dev libreadline5 librecode0 librpc-xml-perl
  librsvg2-2 librsvg2-common libsamplerate0 libsane libsasl2-2
  libsasl2-modules libscim8c2a libscrollkeeper0 libsdl-gfx1.2-4
  libsdl-gfx1.2-dev libsdl-image1.2 libsdl-image1.2-dev libsdl-mixer1.2
  libsdl-net1.2 libsdl-ttf2.0-0 libsdl-ttf2.0-dev libsdl1.2-dev
  libsdl1.2debian libsdl1.2debian-all libselinux1 libsensors3 libsepol1
  libservlet2.4-java libsexy2 libsgutils1 libshout3 libsidplay1
  libsigc++-2.0-0c2a libslang2 libslp1 libsm-dev libsm6 libsmbclient
  libsmbios1 libsndfile1 libsnmp15 libsoundtouch1c2 libsoup2.4-1 libspeex1
  libsqlite0 libsqlite3-0 libss2 libssl0.9.8 libstartup-notification0
  libstdc++6 libstdc++6-4.2-dev libstdc++6-dev libstdc++6-pic libsvga1
  libswscale1d libsysfs2 libtag1c2a libtar libtasn1-3 libtelepathy-glib0
  libtelepathy2 libterm-readkey-perl libtext-charwidth-perl libtext-iconv-perl
  libtext-wrapi18n-perl libthai0 libtheora-dev libtheora0 libtiff4
  libtiff4-dev libtiffxx0c2 libtotem-plparser10 libtracker-gtk0
  libtrackerclient0 libuniconf4.4 liburi-perl libusb-0.1-4 libusplash0
  libuuid1 libvcdinfo0 libvisual-0.4-0 libvlc0 libvolume-id0 libvorbis-dev
  libvorbis0a libvorbisenc2 libvorbisfile3 libvte9 libwavpack1 libwildmidi0
  libwmf0.2-7 libwnck22 libwpd8c2a libwpg-0.1-1 libwps-0.1-1 libwrap0
  libwvstreams4.4-base libwvstreams4.4-extras libwww-perl libwxbase2.4-1
  libwxbase2.4-dev libwxbase2.6-0 libwxbase2.6-dev libwxbase2.8-0
  libwxbase2.8-dev libwxgtk2.4-1 libwxgtk2.4-1-contrib libwxgtk2.4-contrib-dev
  libwxgtk2.4-dev libwxgtk2.6-0 libwxgtk2.6-dev libwxgtk2.8-0 libwxgtk2.8-dev
  libwxsvg-dev libwxsvg0 libx11-6 libx11-data libx11-dev libx11-xcb1 libx86-1
  libxalan2-java libxau-dev libxau6 libxaw7 libxcb-xlib0 libxcb-xlib0-dev
  libxcb1 libxcb1-dev libxcomposite-dev libxcomposite1 libxcursor-dev
  libxcursor1 libxdamage-dev libxdamage1 libxdmcp-dev libxdmcp6
  libxerces2-java libxevie1 libxext-dev libxext6 libxfixes-dev libxfixes3
  libxfont1 libxft-dev libxft2 libxi-dev libxi6 libxinerama-dev libxinerama1
  libxkbfile1 libxklavier12 libxml-parser-perl libxml-twig-perl libxml2
  libxml2-utils libxmu6 libxmuu1 libxosd2 libxp6 libxplc0.3.13 libxpm4
  libxrandr-dev libxrandr2 libxrender-dev libxrender1 libxres1 libxslt1.1
  libxss1 libxt6 libxtrap6 libxtst-dev libxtst6 libxv1 libxxf86dga1
  libxxf86misc1 libxxf86vm1 libzephyr3 libzvbi0 linux-generic
  linux-headers-2.6.24-16 linux-headers-2.6.24-16-generic
  linux-headers-2.6.24-23 linux-headers-2.6.24-23-generic
  linux-headers-2.6.24-24 linux-headers-2.6.24-24-generic
  linux-headers-generic linux-image-2.6.24-16-generic
  linux-image-2.6.24-23-generic linux-image-2.6.24-24-generic
  linux-image-generic linux-restricted-modules-2.6.24-16-generic
  linux-restricted-modules-2.6.24-23-generic
  linux-restricted-modules-2.6.24-24-generic linux-restricted-modules-common
  linux-restricted-modules-generic linux-sound-base
  linux-ubuntu-modules-2.6.24-16-generic
  linux-ubuntu-modules-2.6.24-23-generic
  linux-ubuntu-modules-2.6.24-24-generic liquidwar liquidwar-server locales
  login logrotate lsb-base lsb-release lshw lsof ltrace lzma make makedev
  man-db matrem mawk maxima mdetect mesa-common-dev mesa-utils metacity
  metacity-common mii-diag min12xxw mktemp mlocate module-init-tools
  mono-common mono-gac mono-jit mono-runtime mount mousetweaks mscompress
  mtr-tiny myspell-en-gb myspell-en-us myspell-en-za nano nautilus
  nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share ncurses-base
  ncurses-bin net-tools netbase netcat netcat-traditional netpbm
  network-manager network-manager-gnome njam notification-daemon ntfs-3g
  ntpdate nvidia-kernel-common o3read obex-data-server odbcinst1debian1
  onboard openoffice.org openoffice.org-base openoffice.org-base-core
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-filter-binfilter
  openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk
  openoffice.org-help-en-gb openoffice.org-help-en-us
  openoffice.org-hyphenation openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-common openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-math openoffice.org-officebean
  openoffice.org-style-human openoffice.org-thesaurus-en-au
  openoffice.org-thesaurus-en-us openoffice.org-writer
  openoffice.org-writer2latex openssh-client openssl openssl-blacklist parted
  passwd pciutils pcmciautils perl perl-base perl-modules pia pidgin
  pidgin-otr pkg-config pm-utils pnm2ppa pokerth policykit policykit-gnome
  poppler-utils popularity-contest powermanagement-interface powermgmt-base
  powernowd ppp pppconfig pppoeconf preview-latex-style procps psmisc
  pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf
  pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils pxljr python
  python-apport python-apt python-brlapi python-cairo python-central
  python-cups python-dbus python-gconf python-gdata python-gdbm python-glade2
  python-gmenu python-gnome2 python-gnome2-desktop python-gnomecanvas
  python-gnupginterface python-gobject python-gst0.10 python-gtk2
  python-gtkhtml2 python-gtksourceview2 python-imaging python-launchpad-bugs
  python-launchpad-integration python-libxml2 python-minimal python-notify
  python-numeric python-openssl python-problem-report python-pyatspi
  python-pyopenssl python-pyorbit python-sexy python-software-properties
  python-support python-uno python-virtkey python-vte python-xdg python2.5
  python2.5-minimal radeontool rdesktop readahead realtimebattle reiserfsprogs
  rhythmbox rss-glx rsync samba-common scantv scilab scilab-bin scim
  scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule
  scim-modules-socket screen screensaver-default-images scrollkeeper seahorse
  sed sgml-base sgml-data shared-mime-info skype smartdimmer smbclient
  software-properties-gtk sound-juicer splix sqlite sqlite3 ssh-askpass-gnome
  ssl-cert startup-tasks stellarium strace sudo sun-java6-bin sun-java6-jre
  sun-java6-plugin synaesthesia synaptic sysklogd system-config-printer-common
  system-config-printer-gnome system-services system-tools-backends sysvutils
  tangerine-icon-theme tar tasksel tasksel-data tcl8.4 tcpd tcpdump
  telepathy-gabble telepathy-gabble-dbg telepathy-mission-control telnet
  tex-common texlive-base texlive-base-bin texlive-common texlive-doc-base
  texlive-latex-base texlive-latex-extra texlive-pictures texmaker
  thunderbird-locale-en-gb time tk8.4 tomboy toshset totem totem-common
  totem-gstreamer totem-mozilla totem-plugins tracker tracker-search-tool
  transmission-gtk trigger tsclient ttf-arabeyes ttf-arphic-uming
  ttf-bitstream-vera ttf-dejavu ttf-dejavu-core ttf-dejavu-extra ttf-freefont
  ttf-indic-fonts-core ttf-kochi-gothic ttf-kochi-mincho ttf-lao
  ttf-malayalam-fonts ttf-opensymbol ttf-thai-tlwg ttf-unfonts-core tzdata
  ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-keyring
  ubuntu-minimal ubuntu-standard ucf udev ufw unattended-upgrades unixodbc
  unrar unrar-free unzip update-inetd update-manager update-manager-core
  update-notifier upstart upstart-compat-sysv upstart-logd usbutils usplash
  usplash-theme-ubuntu util-linux util-linux-locales uuid-runtime v4l-conf
  vbetool vim-common vim-tiny vinagre vino vlc vlc-nox vlc-plugin-pulse w3m
  wamerican wbritish wget whiptail whois wine wireless-tools wodim
  wpasupplicant wvdial wxmaxima x-dev x-ttcidfont-conf x11-apps x11-common
  x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils
  x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-record-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev xauth xaw3dg xawtv xawtv-plugins xbase-clients
  xbitmaps xdg-user-dirs xdg-user-dirs-gtk xfonts-100dpi xfonts-75dpi
  xfonts-base xfonts-encodings xfonts-scalable xfonts-utils xinit xml-core
  xmoto xorg xsane xscreensaver-data xscreensaver-gl xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-kbd xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-amd xserver-xorg-video-apm xserver-xorg-video-ark
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus
  xserver-xorg-video-cyrix xserver-xorg-video-dummy xserver-xorg-video-fbdev
  xserver-xorg-video-geode xserver-xorg-video-glint xserver-xorg-video-i128
  xserver-xorg-video-i740 xserver-xorg-video-i810 xserver-xorg-video-imstt
  xserver-xorg-video-intel xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-newport xserver-xorg-video-nsc xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-psb
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xsltproc xterm
  xtrans-dev xulrunner-1.9 xulrunner-1.9-gnome-support xutils xutils-dev yelp
  zenity zip zlib1g zlib1g-dev
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libc6 (due to apt) libgcc1 (due to apt) libstdc++6 (due to apt)
  base-files base-passwd (due to base-files) libpam-modules (due to
  base-files) bash debianutils (due to bash) libncurses5 (due to bash)
  bsdutils coreutils libacl1 (due to coreutils) libselinux1 (due to coreutils)
  dash mktemp (due to debianutils) diff dpkg lzma (due to dpkg) e2fsprogs
  e2fslibs (due to e2fsprogs) libblkid1 (due to e2fsprogs) libcomerr2 (due to
  e2fsprogs) libss2 (due to e2fsprogs) libuuid1 (due to e2fsprogs) findutils
  grep gzip hostname login libpam0g (due to login) mount ncurses-base
  ncurses-bin perl-base python-minimal python2.5-minimal (due to
  python-minimal) sed sysvutils libsepol1 (due to sysvutils) tar util-linux
  lsb-base (due to util-linux) tzdata (due to util-linux) libslang2 (due to
  util-linux) zlib1g (due to util-linux)
0 upgraded, 0 newly installed, 1332 to remove and 0 not upgraded.
After this operation, 3225MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] 


```

As you can see, I cannot allow that, as it will REMOVE ALL my packages.

My /etc/apt/sources.list is 
```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://in.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy universe
deb http://in.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://in.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# deb http://wine.budgetdedicated.com/apt hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"

```

And, 
```

sarthak@sarthorks:~$ sudo apt-get install --reinstall gcc-4.4-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of gcc-4.4-base is not possible, it cannot be downloaded.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libgcc1: Depends: gcc-4.4-base (= 4.4.0-5) but 4.4.0-10 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Please help me!!

---

### Post by sarthorks on 2009-06-29
I have gone through this thread too : [http://ubuntuforums.org/showthread.php?p=4347682](http://ubuntuforums.org/showthread.php?p=4347682) , but i don't know what to do, as my problem is a bit different. 
Please help! Anybody?
 I was trying to install this :libstdc++6_4.4.0-10_i386.deb
But i needed to install this first : gcc-4.4-base_4.4.0-10_i386
But i guess by mistake i mixed up 4.4.0-10 and 4.4.0-5 versions, and in the confusion, something happened to libgcc1.

Please! Someone?

---

### Post by sarthorks on 2009-06-29
I guess the problem lies in:

libgcc1 DEPENDS: gcc-4.4-base(=4.4.0-5)
But I dont have that installed. I have gcc-4.4-base(=4.4.0-10) installed.

But I cant even try and remove 4.4.0-10 gcc and install 4.4.0-5, as it first asks me to FIX the BROKEN dependencies, which leads to it asking me to remove ALL my packages i have installed till now.

Help!

---

### Post by directhex on 2009-06-29
You've managed to break your system HARD. gcc-4.4-base is part of Karmic only - but your sources.list is for Hardy. On your system (hardy and hardy-security) you should have libgcc1 1:4.2.4-1ubuntu3, but it.......


Have you been installing system-critical packages from DEBIAN?

```
   libgcc1 | 1:3.3.6-15 |     etch-m68k | m68k
   libgcc1 | 1:3.3.6-15 |     oldstable | hppa
   libgcc1 | 1:4.1.1-21 |     oldstable | alpha, amd64, arm, i386, ia64, mips, mipsel, powerpc, s390, sparc
   libgcc1 | 1:4.3.2-1.1 |        stable | alpha, amd64, arm, armel, i386, ia64, mips, mipsel, powerpc, s390, sparc
**   libgcc1 |  1:4.4.0-5 |       testing | alpha, amd64, armel, i386, ia64, mips, mipsel, powerpc, s390, sparc**
   libgcc1 |  1:4.4.0-8 |      unstable | armel, mips, mipsel
   libgcc1 |  1:4.4.0-9 |      unstable | alpha, hurd-i386, kfreebsd-amd64, powerpc, s390, sparc
   libgcc1 | 1:4.4.0-10 |      unstable | amd64, i386, ia64, kfreebsd-i386
```

It's hard to overstate just how much you've made a mess of things. You've copy-pasted c:\windows\system32 from a vista box to an xp box and wondered why it's broken kinda broken.

You need to revert to an Ubuntu system - not a broken mix of Debian and Ubuntu, and it's not something I can advise on remotely - frankly it's not something I'd personally expect to be able to fix in less time than a reformat.

---

### Post by sarthorks on 2009-06-29
Yes, I installed it from Debian. MY bad. Did not know much about these inconsistencies. Can you help me try to revert the changes?

---

### Post by directhex on 2009-06-29
> **sarthorks said:**
> Yes, I installed it from Debian. MY bad. Did not know much about these inconsistencies. Can you help me try to revert the changes?

If you're INCREDIBLY lucky, you could force installation of [http://security.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/libgcc1_4.2.4-1ubuntu3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/libgcc1_4.2.4-1ubuntu3_i386.deb)

But chances are your only escape is an upgrade to Karmic

---

### Post by sarthorks on 2009-06-29
Ah problem SOLVED. 

I have Ubuntu Hardy Heron.
I had installed libgcc1_4.4.0-5_i386, gcc-4.4-base_4.4.0-10_i386, and in between i installed and then removed gcc-4.4-base_4.4.0-5, then _i386libstdc++6_4.4.0-10_i386, and libavformat0d_0.cvs20060823-8+etch1_i386, and libavcodec0d_0.cvs20060823-8+etch1_i386 from Debian source.

I did:sudo dpkg -P libgcc1_4.4.0-5_i386, and got
```

dpkg - warning: ignoring request to remove libgcc1_4.4.0-5_i386 which isn't installed

```

dpkg -s libc6 gave
```

Package: libc6
Status: install ok installed
Priority: required
Section: libs
Installed-Size: 10432
etc..

```

dpkg -l libc6 gave
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
 +++-==============-==============-============================================
ii  libc6          2.7-10ubuntu4  GNU C Library: Shared libraries

```

Then i downloaded the package from here [http://packages.ubuntu.com/hardy-updates/libgcc1](http://packages.ubuntu.com/hardy-updates/libgcc1)

and cd to the installation directory and did
dpkg -i libgcc1_4.2.4-1ubuntu4_i386.deb
it gave
```

dpkg - warning: downgrading libgcc1 from 1:4.4.0-5 to 1:4.2.4-1ubuntu4.
(Reading database ... 166803 files and directories currently installed.)
Preparing to replace libgcc1 1:4.4.0-5 (using libgcc1_4.2.4-1ubuntu4_i386.deb) ...
Unpacking replacement libgcc1 ...
Setting up libgcc1 (1:4.2.4-1ubuntu4) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```
No errors! :p

Then did sudo apt-get -f install and got
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

Then in synaptic, in Status, and in "Installed (local or obsolete)",
it showed
adobe-flashplugin
gcc-4.4-base
libavcodec0d
libavformat0d
skype
wine

So i COMPLETELY removed gcc-4.4 and libav*.

Problem solved and computer back to normal! :guitar:

Got help from IRC #ubuntu. ITs great!

---

### Post by sarthorks on 2009-06-29
How do I mark this as [SOLVED]?
The Thread Tools isnt showing that option.

---

### Post by jherskow on 2009-08-25
i dont understand what u guys have been saying, but i have a problem that allot of stuff i try to install hae dependencies, and when i try to install them, they have dependencies, and nothing works.'

if that fits the problem here, can you please help me?

---

### Post by directhex on 2009-08-25
> **jherskow said:**
> i dont understand what u guys have been saying, but i have a problem that allot of stuff i try to install hae dependencies, and when i try to install them, they have dependencies, and nothing works.'

if that fits the problem here, can you please help me?

A problem without specifics isn't a problem, it's a hallucination.

---

### Post by jherskow on 2009-08-26
what?

im just writing everything i see,  i done understand the specifics of it, thats why im turning to you guys.

not hallucinating,
jeez.

---

### Post by Khakilang on 2009-08-26
I have similarly problem too but the situation is different because I use Synaptic to update when this thing happen. So I go back to Synaptic Manager to find the broken files and download again. After this I hope everything works.

---

### Post by jherskow on 2009-08-26
if i use add/remove, it tells me that there is in installation conflict. when i go to synaptci, it list dependencies, and when i tell it to download it, it tells me it cannot because the dependencies have dependencies, and then i try to install those.......and so on and so on.....

this is *very* frustrating.
please help.
thanks,
jherskow

---

### Post by directhex on 2009-08-26
> **jherskow said:**
> if i use add/remove, it tells me that there is in installation conflict. when i go to synaptci, it list dependencies, and when i tell it to download it, it tells me it cannot because the dependencies have dependencies, and then i try to install those.......and so on and so on.....

this is *very* frustrating.
please help.
thanks,
jherskow

These are no more specifics than "I go to drive my car, and the thing in the thing goes 'bloop' and it doesn't work".

"it list dependencies" - WHAT dependencies?

"i tell it to download it" - WHAT is "it"?

Only specific problems can be helped, and right now, you have no specific problem, because you have no specifics.

Actual error messages, actual screenshots, that kind of stuff can produce help.

---

### Post by jherskow on 2009-08-26
you're a nice guy, y'know that?

---

### Post by jherskow on 2009-08-27
ok, here is a full description of the problem:

im attaching a screenshot of every error, if i can.

this happens to a few programs, i don't know how many, but it happens often.
 im going to use the example of convertall- a usefull app to convert between measurement systems.

first im going to try the easy way. i go to add/remove from the desktop, and go to convertall.
i click on the square to mark it, and i get the following error:

> cannot install convertall
this app conflicts with other intlld sftware. to install the cnflctng sftwr must be removed.

switch to synaptic to resolve.

so off we go to synaptic.

when i mark convertall for installation a get another window

> mark additional required changes?

the following changes must be installed to proceed:

to be installed:

python 2.5

python 2.5-minimal

so i click "mark"

and i get a new lovely error message:

> could not mark all packages for installation or upgrade

the following packages have unresolvable dependencies.

please make sure all the required repositories are added and enabled in the prefrences:

convertall:

depends: python-qt4 but ut is not going to be installed

so i go to python-qt4 in synaptic and try to install:

i get the same window again:

> mark additional required changes?

the following changes must be installed to proceed:

to be installed:

python 2.5

 python 2.5-minimal

(note this is the same as the previous window, so i have only uploaded 1 screenshot)

and after clicking mark:

> 
could not mark all packages for installation or upgrade
 
 the following packages have unresolvable dependencies.
 
 please make sure all the required repositories are added and enabled in the prefrences:

python-qt4:
 Depends: libqt4-assistant but it is not going to be installed
 Depends: libqt4-help but it is not going to be installed
 Depends: libqt4-svg but it is not going to be installed
 Depends: libqt4-test but it is not going to be installed
 Depends: libqt4-webkit but it is not going to be installed
 Depends: libqt4-xmlpatterns but it is not going to be installed
  Depends: python (<2.6) but 2.6.2-0ubuntu1 is to be installed
 Depends: python-sip4 but it is not going to be installed
 Depends: python-sip4 but it is not going to be installed
 Depends: python-qt4-common but it is not going to be installed


this is the point at which i give up.

ok, so now iv'e given you all the details.

can you help me?

---

### Post by directhex on 2009-08-27
Okay, it appears from where I'm sat that you somehow have a mix of Intrepid and Jaunty on your system - "python" should be version 2.6.something in Jaunty, but only "python-qt4" from Intrepid demands 2.5.something (Jaunty's python-qt4 expects 2.6.something)

Can you post the contents of /etc/apt/sources.list ?

---

### Post by jherskow on 2009-08-27
sure, coming right up:

```
# deb cdrom:[Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)]/ jaunty main multiverse restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.ovh.net/ubuntu/ jaunty main restricted
deb-src http://mirror.ovh.net/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.ovh.net/ubuntu/ jaunty-updates main restricted
deb-src http://mirror.ovh.net/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.ovh.net/ubuntu/ jaunty universe
deb-src http://mirror.ovh.net/ubuntu/ jaunty universe
deb http://mirror.ovh.net/ubuntu/ jaunty-updates universe
deb-src http://mirror.ovh.net/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.ovh.net/ubuntu/ jaunty multiverse
deb-src http://mirror.ovh.net/ubuntu/ jaunty multiverse
deb http://mirror.ovh.net/ubuntu/ jaunty-updates multiverse
deb-src http://mirror.ovh.net/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://il.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://il.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://mirror.ovh.net/ubuntu/ jaunty-security main restricted
deb-src http://mirror.ovh.net/ubuntu/ jaunty-security main restricted
deb http://mirror.ovh.net/ubuntu/ jaunty-security universe
deb-src http://mirror.ovh.net/ubuntu/ jaunty-security universe
deb http://mirror.ovh.net/ubuntu/ jaunty-security multiverse
deb-src http://mirror.ovh.net/ubuntu/ jaunty-security multiverse
deb http://dl.google.com/linux/deb/ stable non-free main
deb http://ppa.launchpad.net/glasen/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main
```

---

### Post by directhex on 2009-08-27
> **jherskow said:**
> sure, coming right up:

```
# deb cdrom:[Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)]/ jaunty main multiverse restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.ovh.net/ubuntu/ jaunty main restricted
deb-src http://mirror.ovh.net/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.ovh.net/ubuntu/ jaunty-updates main restricted
deb-src http://mirror.ovh.net/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.ovh.net/ubuntu/ jaunty universe
deb-src http://mirror.ovh.net/ubuntu/ jaunty universe
deb http://mirror.ovh.net/ubuntu/ jaunty-updates universe
deb-src http://mirror.ovh.net/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.ovh.net/ubuntu/ jaunty multiverse
deb-src http://mirror.ovh.net/ubuntu/ jaunty multiverse
deb http://mirror.ovh.net/ubuntu/ jaunty-updates multiverse
deb-src http://mirror.ovh.net/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://il.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://il.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://mirror.ovh.net/ubuntu/ jaunty-security main restricted
deb-src http://mirror.ovh.net/ubuntu/ jaunty-security main restricted
deb http://mirror.ovh.net/ubuntu/ jaunty-security universe
deb-src http://mirror.ovh.net/ubuntu/ jaunty-security universe
deb http://mirror.ovh.net/ubuntu/ jaunty-security multiverse
deb-src http://mirror.ovh.net/ubuntu/ jaunty-security multiverse
deb http://dl.google.com/linux/deb/ stable non-free main
deb http://ppa.launchpad.net/glasen/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu jaunty main
```

That all seems normal enough

Try an "aptitude dist-upgrade" and paste what it proposes doing

---

### Post by jherskow on 2009-09-01
> :~$ aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

im not 100% sure what root is, but mine is the first and only account.

---

### Post by directhex on 2009-09-01
> **jherskow said:**
> im not 100% sure what root is, but mine is the first and only account.

**sudo** aptitude dist-upgrade

Nobody runs as an administrator day-ro-day in Linux land, we run as normal users & gain rights only when needed

---

### Post by jherskow on 2009-09-07
> josh@JoshBook:~$ 
josh@JoshBook:~$ sudo aptitude dist-upgrade
[sudo] password for josh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  libbabl-0.0-0{u} libgegl-0.0-0{u} libpoppler-glib3{u} libpoppler3{u} 
0 packages upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 3801kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 133233 files and directories currently installed.)
Removing libgegl-0.0-0 ...
Removing libbabl-0.0-0 ...
Removing libpoppler-glib3 ...
Removing libpoppler3 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

josh@JoshBook:~$ 
josh@JoshBook:~$ 


done

---

### Post by Ron G on 2009-09-08
> **sarthorks said:**
> How do I mark this as [SOLVED]?
The Thread Tools isnt showing that option.

Go to the original post , do an edit, and mark it in the title (solved) at the beginning of the title.:)

---

### Post by jherskow on 2009-09-08
ummm, it's not solved for me....:)

---

