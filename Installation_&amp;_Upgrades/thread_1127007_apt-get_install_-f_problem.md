---
title: "apt-get install -f problem"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by somepalli on 2009-04-16
root@ubuntu:~# [COLOR="Green"]apt-get install -f[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  vim-gui-common bochsbios nautilus-script-manager gnokii-common
  tecnoballz-data glabels-data squid-common classpath-common gftp-common
  openvpn-blacklist discover1-data transmission-common htmldoc-common
  mplayer-skins libnunit-doc vgabios ubuntu-gdm-themes libgii1-target-x
  ubuntu-wallpapers vim-runtime libapache-singleton-perl quanta-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  adduser alacarte alien alsa-base alsa-oss alsa-source alsa-tools
  alsa-tools-gui alsa-utils alsamixergui alsaplayer-alsa alsaplayer-common
  alsaplayer-gtk amavisd-new anacron apache2 apache2-mpm-prefork apache2-utils
  apache2.2-common apparmor apparmor-utils apport apport-gtk apt apt-utils
  aptitude apturl arj ark asoundconf-gtk aspell at at-spi audacious
  audacious-plugins audacity auth-client-config avahi-autoipd avahi-daemon
  banshee base-files base-passwd bash bash-completion bc belocs-locales-bin
  bind9 bind9-host binfmt-support binutils binutils-static bison bittorrent
  blt bluefish bluez-audio bluez-cups bluez-gnome bluez-utils bogofilter
  bogofilter-bdb bouml brasero brltty brltty-x11 bsdmainutils bsdutils bsh
  buddi bug-buddy bzip2 ca-certificates cabextract cacao cameramonitor
  camorama camserv capplets-data cbrowser ccache cdparanoia cdrdao childsplay
  chm2pdf chmsee clamav clamav-base clamav-daemon clamav-freshclam classpath
  classpath-gtkpeer cli-common command-not-found compiz compiz-core
  compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome
  compiz-plugins compizconfig-backend-gconf compizconfig-settings-manager
  console-setup console-terminus console-tools consolekit
  contact-lookup-applet coreutils courier-authdaemon courier-authlib
  courier-authlib-ldap courier-authlib-userdb courier-base courier-imap
  courier-imap-ssl courier-ldap courier-pop courier-pop-ssl courier-ssl cpio
  cpp cpp-3.4 cpp-4.1 cpp-4.2 cpp-4.3 cron cryptsetup cscope cups-pdf cupsddk
  cupsddk-drivers cupsys cupsys-bsd cupsys-client cupsys-driver-gutenprint cvs
  dansguardian dash db4.6-util dbus dbus-x11 dc dcraw ddd debconf debconf-i18n
  debconf-utils debhelper debianutils deborphan defoma deluge-torrent
  deluge-torrent-common deskbar-applet desktop-file-utils dhcdbd dhcp3-client
  dhcp3-common dhcp3-server dialog dictionaries-common diff discover1
  displayconfig-gtk diveintopython dmidecode dmsetup dnsutils doc-base
  docbook-xml dosfstools dpkg dpkg-dev dselect dvd+rw-tools e2fslibs e2fsprogs
  ebox ebox-ca ebox-dhcp ebox-dns ebox-firewall ebox-jabber ebox-mail
  ebox-mailfilter ebox-network ebox-ntp ebox-objects ebox-openvpn
  ebox-printers ebox-samba ebox-services ebox-software ebox-squid
  ebox-trafficshaping ebox-usersandgroups ebox-webserver ed eject ekiga
  emerald enscript eog epdfview esofttool espeak ethtool evince evolution
  evolution-data-server evolution-exchange evolution-plugins evolution-webcal
  expect f-spot fakeroot fdutils file file-roller findutils finger
  firebird2.0-common firefox firefox-3.0 firefox-3.0-gnome-support
  firefox-gnome-support fontconfig fontconfig-config foo2zjs
  foomatic-db-engine foomatic-db-hpijs foomatic-filters fortune-mod
  fortunes-min fping freeglut3 friendly-recovery ftp fuse-utils gamin garlic
  gausssum gawk gcalctool gcc gcc-3.4 gcc-4.1 gcc-4.2 gcc-4.3 gcjwebplugin
  gconf-editor gconf2 gconf2-common gdb gdebi gdebi-core gdk-imlib11 geany
  gedit genisoimage getlibs gettext gettext-base gftp gftp-gtk gftp-text
  gfxboot ghostscript ghostscript-x gij gij-4.2 gimp gimp-gnomevfs gimp-python
  gksu glabels glade-3 gnochm gnokii gnokii-cli gnome-accessibility-themes
  gnome-app-install gnome-applets gnome-applets-data gnome-bin gnome-bluetooth
  gnome-btdownload gnome-control-center gnome-doc-utils gnome-games
  gnome-games-data gnome-humility-icon-theme gnome-icon-theme gnome-iconedit
  gnome-keyring gnome-keyring-manager gnome-libs-data gnome-mag gnome-media
  gnome-media-common gnome-menus gnome-netstatus-applet gnome-nettool
  gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits
  gnome-screensaver gnome-settings-daemon gnome-spell gnome-system-monitor
  gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes
  gnome-user-guide gnome-utils gnupg gnuplot gnuplot-nox gnuplot-x11 gparted
  gpgkeys gpgsm gpgv gpsim gputils graphviz grep groff-base grub gsfonts
  gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-ffmpeg
  gstreamer0.10-gnomevfs gstreamer0.10-gnonlin gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
  gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x gthumb
  gtk-engines-mono gtk-im-libthai gtk-qt-engine gtk-sharp2 gtk-sharp2-examples
  gtk-sharp2-gapi gtk2-engines gtk2-engines-gtk-qt gtk2-engines-murrine
  gtk2-engines-pixbuf gtk2-engines-ubuntulooks gtk2-ex-formfactory-perl
  gtkhtml3.14 gtkorphan gucharmap guidance-backends guile-1.6-libs gvfs
  gvfs-backends gvfs-fuse gxine gxineplugin gzip hdparm hostname hotkey-setup
  hpijs hplip html2text htmldoc human-theme hwtest hwtest-gtk
  icedtea-gcjwebplugin icon-slicer idle-python2.5 ifupdown imagemagick
  imlib-base info initramfs-tools initscripts inputattach intltool-debian
  iproute iptables iputils-arping iputils-ping iputils-tracepath isomaster
  jabber-common jabberd2-ldap-bdb jackd jnettop jockey-common jockey-gtk k3b
  kamera kcontrol kde-i18n-uk kde4libs-bin kdebase-bin kdebase-bin-kde3
  kdebase-kio-plugins kdebase-runtime kdebase-runtime-bin-kde4 kdelibs4c2a
  kdelibs5 kdemultimedia-kio-plugins kdesktop kdesudo kfilereplace kfind
  kicker kiconedit kiconedit-kde4 kiki kiosktool klinkstatus klogd kommander
  konqueror konqueror-kde4 konqueror-nsplugins konsole konsole-kde4
  kpersonalizer ksmserver ktechlab kview kwin kwin-kde4 kxsldbg
  language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base language-pack-kde-uk language-pack-kde-uk-base
  language-selector language-selector-common lapack3 laptop-detect
  laptop-mode-tools launchpad-integration ldap-auth-client ldap-auth-config
  less lesstif2 lftp liba52-0.7.4 libaa1 libaccess-bridge-java libacl1
  libakode2 libalut0 libao2 libapache-authcookie-perl
  libapache2-mod-auth-mysql libapache2-mod-ldap-userdir libapache2-mod-perl2
  libapache2-mod-php5 libapm1 libapr1 libaprutil1 libarchive-tar-perl
  libarchive-zip-perl libarchive1 libart-2.0-2 libart2 libart2.0-cil
  libarts1-akode libarts1c2a libartsc0 libasound2 libaspell15 libatk1.0-0
  libatm1 libatspi1.0-0 libattr1 libaudclient1 libaudid3tag1 libaudio2
  libaudiofile0 libauthen-sasl-perl libavahi-client3 libavahi-common3
  libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1 libavahi-qt3-1
  libavahi-ui0 libavahi1.0-cil libavc1394-0 libavcodec1d libavformat1d
  libavutil1d libbeagle0 libbeagle1 libbeecrypt6 libberkeleydb-perl
  libbind9-30 libbit-vector-perl libblas3gf libblkid1 libbluetooth2
  libbonobo2-0 libbonoboui2-0 libboo2.0-cil libboost-date-time1.34.1
  libboost-filesystem1.34.1 libboost-thread1.34.1 libbrlapi0.5 libbrlapi1
  libbtctl4 libbz2-1.0 libc6 libc6-dev libcaca0 libcache-cache-perl
  libcairo-perl libcairo2 libcairomm-1.0-1 libcamel1.2-10 libcamel1.2-11
  libcap1 libcapseo0 libcaptury0 libcarp-clan-perl libcdaudio1 libcddb2
  libcdio-cdda0 libcdio-paranoia0 libcdio6 libcdio7 libcdparanoia0
  libchart-perl libchm-bin libchm1 libchromexvmc1 libchromexvmcpro1
  libck-connector0 libclamav3 libclass-container-perl
  libclass-data-inheritable-perl libclass-singleton-perl libclone-perl
  libclucene0ldbl libcomerr2 libcompizconfig0 libcompress-raw-zlib-perl
  libcompress-zlib-perl libconsole libconvert-asn1-perl libconvert-binhex-perl
  libconvert-tnef-perl libconvert-uulib-perl libcroco3 libcrypt-smbhash-perl
  libcucul0 libcupsimage2 libcupsys2 libcurl3 libcurl3-gnutls libcvsservice0
  libcwidget3 libdaemon0 libdate-calc-perl libdatetime-format-mail-perl
  libdatetime-format-w3cdtf-perl libdatetime-locale-perl libdatetime-perl
  libdatetime-timezone-perl libdatrie0 libdb4.2 libdb4.3 libdb4.4 libdb4.5
  libdb4.6 libdbd-mysql-perl libdbd-pg-perl libdbi-perl libdbus-1-3
  libdbus-glib-1-2 libdbus-qt-1-1c2 libdc1394-13 libdecoration0
  libdeskbar-tracker libdevel-stacktrace-perl libdevel-symdump-perl
  libdevmapper1.02.1 libdigest-hmac-perl libdigest-md4-perl
  libdigest-sha1-perl libdirectfb-0.9-25 libdirectfb-1.0-0 libdiscid0
  libdiscover1 libdjvulibre15 libdmx1 libdns32 libdns35 libdrm2 libdv4
  libdvbpsi4 libdvdnav4 libdvdread3 libebml0 libebook1.2-9 libebox
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9
  libedataserverui1.2-8 libedit2 libeel2-2 libegroupwise1.2-13 libelfg0
  libemeraldengine0 libenca0 libenchant1c2a liberror-perl libesd-alsa0
  libesmtp5 libespeak1 libexception-class-perl libexchange-storage1.2-3
  libexempi3 libexif12 libexpat1 libexporter-cluster-perl libfaac0 libfaad0
  libfbclient2 libffi4 libffi4-dev libfftw3-3 libfile-copy-recursive-perl
  libfile-mmagic-perl libfile-slurp-perl libfile-tail-perl libfile-temp-perl
  libfilesys-df-perl libflac++6 libflac8 libflickrnet2.1.5-cil libfltk1.1
  libfontconfig1 libfontenc1 libfreebob0 libfreetype6 libfribidi0 libfs6
  libfuse2 libg2c0 libgadu3 libgail-common libgail-gnome-module libgail18
  libgamin0 libgc1c2 libgcc1 libgcj-bc libgcj8-1 libgconf2-4 libgconf2.0-cil
  libgcrypt11 libgd-gd2-perl libgd2-xpm libgda3-3 libgdata-google1.2-1
  libgdata1.2-1 libgdbm3 libgdiplus libgdk-pixbuf2 libgdl-1-0 libgdl-gnome-1-0
  libgfortran2 libggi2 libggz2 libggzcore9 libggzmod4 libgif-dev libgif4
  libgii1 libgimp2.0 libgksu1.2-1 libgksu2-0 libgksuui1.0-1 libgl1-mesa-dri
  libgl1-mesa-glx libglade2-0 libglade2.0-cil libgladeui-1-7 libglew1.4
  libglew1.5 libglib-perl libglib1.2ldbl libglib2.0-0 libglib2.0-cil
  libglib2.0-dev libglibmm-2.4-1c2a libglu1-mesa libglut3 libgmime-2.0-2
  libgmp3c2 libgmyth0 libgnokii3 libgnome-desktop-2 libgnome-keyring0
  libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2
  libgnome-speech7 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0
  libgnome2-canvas-perl libgnome2-common libgnome2-gconf-perl libgnome2-perl
  libgnome2-vfs-perl libgnome2.0-cil libgnome32 libgnomebt0 libgnomecanvas2-0
  libgnomecups1.0-1 libgnomekbd-common libgnomekbd2 libgnomekbdui2
  libgnomeprint2.2-0 libgnomeprintui2.2-0 libgnomesupport0 libgnomeui-0
  libgnomeui32 libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common
  libgnomevfs2-extra libgnorba27 libgnorbagtk0 libgnutls13 libgomp1
  libgpg-error0 libgpgme11 libgphoto2-2 libgphoto2-port0 libgpmg1
  libgpod-common libgpod2 libgpod3 libgraphviz4 libgs8 libgsf-1-114 libgsl0
  libgsl0ldbl libgsm1 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0
  libgtk-vnc-1.0-0 libgtk1.2 libgtk2-gladexml-perl libgtk2-perl libgtk2.0-0
  libgtk2.0-bin libgtk2.0-cil libgtkextra-x11-2.0-1 libgtkhtml2-0
  libgtkhtml3.14-19 libgtkhtml3.16-cil libgtkhtml3.8-15 libgtkmm-2.4-1c2a
  libgtksourceview1.0-0 libgtksourceview2.0-0 libgtksourceview2.0-cil
  libgtkspell0 libgtop2-7 libgucharmap6 libguile-ltdl-1 libgutenprint2
  libgutenprintui2-1 libgvfscommon0 libgweather-common libgweather1
  libhal-storage1 libhal1 libhesiod0 libhsqldb-java libhtml-mason-perl
  libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhunspell-1.1-0
  libical0 libice6 libicu36 libicu38 libid3tag0 libidl0 libidn11 libiec61883-0
  libieee1284-3 libimlib2 libintl-perl libio-compress-base-perl
  libio-compress-zlib-perl libio-multiplex-perl libio-socket-ssl-perl
  libio-stringy-perl libio-zlib-perl libipc-sharelite-perl libipoddevice0
  libiptcdata0 libisc32 libisc35 libisccc30 libisccfg30 libiso9660-5 libiw29
  libjack0 libjasper1 libjaxp1.3-java libjcode-pm-perl libjline-java libjpeg62
  libk3b2 libkarma0 libkcddb1 libkeyutils1 libkonq4 libkonq5 libkpathsea4
  libkrb53 libksba8 liblame0 liblapack3gf liblaunchpad-integration0
  liblaunchpad-integration1 liblcms1 libldap-2.4-2 libldap2 liblircclient0
  liblocale-gettext-perl liblockfile1 liblog-dispatch-perl
  liblog-log4perl-perl liblpint-bonobo0 libltdl3 liblua50 liblualib50
  liblwres30 liblzo2-2 libmad0 libmagic1 libmagick10 libmagick9
  libmail-rfc822-address-perl libmailtools-perl libmatroska0 libmcrypt4
  libmcs1 libmeanwhile1 libmetacity0 libmikmod2 libmime-perl
  libmime-tools-perl libmjpegtools0c2a libmms0 libmng1 libmodplug0c2
  libmono-accessibility2.0-cil libmono-addins-gui0.2-cil libmono-addins0.2-cil
  libmono-bytefx0.7.6.2-cil libmono-c5-1.0-cil libmono-cairo1.0-cil
  libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil
  libmono-corlib2.1-cil libmono-cscompmgd8.0-cil libmono-data-tds1.0-cil
  libmono-data-tds2.0-cil libmono-db2-1.0-cil libmono-firebirdsql1.7-cil
  libmono-i18n2.0-cil libmono-ldap2.0-cil libmono-microsoft-build2.0-cil
  libmono-microsoft-visualbasic8.0-cil libmono-microsoft7.0-cil
  libmono-microsoft8.0-cil libmono-mozilla0.2-cil libmono-npgsql2.0-cil
  libmono-peapi2.0-cil libmono-relaxng2.0-cil libmono-security1.0-cil
  libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil
  libmono-sqlite2.0-cil libmono-system-data1.0-cil libmono-system-data2.0-cil
  libmono-system-ldap2.0-cil libmono-system-runtime2.0-cil
  libmono-system-web1.0-cil libmono-system-web2.0-cil libmono-system1.0-cil
  libmono-system2.0-cil libmono-system2.1-cil libmono-winforms2.0-cil
  libmono-zeroconf1.0-cil libmono0 libmono1.0-cil libmono2.0-cil libmowgli1
  libmozjs0d libmpcdec3 libmpeg2-4 libmpfr1ldbl libmtp6 libmtp7
  libmusicbrainz4c2a libmysqlclient15off libnautilus-burn4
  libnautilus-extension1 libncbi6 libncurses5 libncursesw5
  libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon26 libneon27
  libneon27-gnutls libnet-arp-perl libnet-cidr-perl libnet-cups-perl
  libnet-daemon-perl libnet-dbus-perl libnet-dns-perl libnet-ip-perl
  libnet-jabber-perl libnet-ldap-perl libnet-server-perl libnet-ssleay-perl
  libnet-xmpp-perl libnewt0.52 libnjb5 libnl1 libnm-glib0 libnm-util0
  libnotify1 libnspr4-0d libnspr4-0d-dbg libnspr4-dev libnss-ldap libnss-mdns
  libnss3-0d libnss3-1d libnss3-1d-dbg libnss3-dev libntfs-3g12 libntfs-3g23
  libntfs-3g5 libnunit2.2.6-cil libofa0 libogg0 liboil0.3 liboobs-1-3
  liboobs-1-4 libopal-2.2 libopenal0a libopencdk10 libopencdk8 libopenexr2ldbl
  libopenobex1 liborbit0 liborbit2 libotr2 libpam-foreground
  libpam-gnome-keyring libpam-ldap libpam-modules libpam0g libpanel-applet2-0
  libpango1.0-0 libpango1.0-common libpaper-utils libpaper1
  libparams-validate-perl libparted1.7-1 libpcap0.8 libpci2 libpcre3
  libpcrecpp0 libpcsclite1 libperl5.8 libperl6-junction-perl libphonon4
  libpisock9 libpisync0 libpisync1 libpixman-1-0 libplrpc-perl libpng12-0
  libpolkit-dbus2 libpolkit-gnome0 libpolkit-grant2 libpolkit2
  libpoppler-glib2 libpoppler2 libpopt0 libportaudio0 libportaudio2
  libpostproc1d libpq5 libproc-process-perl libproc-processtable-perl
  libpt-1.10.0 libpt-1.10.10 libpt-1.10.10-plugins-alsa
  libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpt-plugins-alsa
  libpt-plugins-v4l libpt-plugins-v4l2 libpth20 libpulse-browse0 libpulse0
  libpulsecore5 libpurple-bin libpurple0 libqt3-mt libqt4-assistant
  libqt4-core libqt4-dbus libqt4-designer libqt4-gui libqt4-network
  libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-svg
  libqt4-xml libqtcore4 libqtgui4 libquicktime1 libraptor1 librarian0
  librasqal0 libraw1394-8 librdf0 libreadline5 libreadonly-perl
  libreadonly-xs-perl librecode0 libresid-builder0c2a librpc-xml-perl
  librpm4.4 librrd2 librrds-perl librsvg2-2 librsvg2-common libruby libruby1.8
  libsamplerate0 libsane libsasl2-2 libsasl2-modules libscim8c2a
  libscrollkeeper0 libsdl-image1.2 libsdl-mixer1.2 libsdl-ttf2.0-0
  libsdl1.2debian libsdl1.2debian-alsa libselinux1 libsensors3 libsepol1
  libservlet2.4-java libsexy2 libsgutils1 libshout3 libsidplay1 libsidplay2
  libsigc++-2.0-0c2a libslang2 libslp1 libsm6 libsmbclient libsmbios1
  libsmpeg0 libsndfile1 libsnmp10 libsnmp15 libsocket6-perl libsoprano4
  libsoundtouch1c2 libsoup2.2-8 libsoup2.4-1 libspeex1 libsqlite0 libsqlite3-0
  libss2 libssl0.9.8 libstartup-notification0 libstdc++6 libstreamanalyzer0
  libstreams0 libstrigiqtdbusclient0 libsuitesparse libsuitesparse-3.1.0
  libsvg1 libsvga1 libsvn1 libswfdec-0.6-90 libsys-cpu-perl
  libsys-cpuload-perl libsys-hostname-long-perl libsysfs2 libtag1c2a libtagc0
  libtaglib2.0-cil libtar libtasn1-3 libterm-readkey-perl
  libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libthai0
  libtheora0 libtidy-0.99-0 libtiff4 libtimedate-perl libtotem-plparser10
  libtotem-plparser7 libtracker-gtk0 libtrackerclient0 libtree-perl
  libungif4-dev libunicode-map-perl libunicode-map8-perl
  libunicode-maputf8-perl libunicode-string-perl libuniconf4.3 libuniconf4.4
  libunix-syslog-perl liburi-perl libusb-0.1-4 libusplash0 libuuid1
  libvcdinfo0 libvibrant6a libvisual-0.4-0 libvlc0 libvolume-id0 libvorbis0a
  libvorbisenc2 libvorbisfile3 libvte9 libwavpack1 libwildmidi0 libwmf0.2-7
  libwnck22 libwpd8c2a libwpg-0.1-1 libwps-0.1-1 libwrap0 libwvstreams4.3-base
  libwvstreams4.3-extras libwvstreams4.4-base libwvstreams4.4-extras
  libwww-perl libwxbase2.6-0 libwxbase2.8-0 libwxgtk2.6-0 libwxgtk2.8-0
  libx11-6 libx11-data libx11-xcb1 libx264-57 libx86-1 libxalan110
  libxalan2-java libxau6 libxaw7 libxcb-shape0 libxcb-shm0 libxcb-xlib0
  libxcb-xv0 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6
  libxerces2-java libxerces27 libxevie1 libxext6 libxfixes3 libxfont1 libxft2
  libxi6 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-gnome
  libxine1-misc-plugins libxine1-plugins libxine1-x libxinerama1 libxkbfile1
  libxklavier11 libxklavier12 libxml-libxml-common-perl libxml-libxml-perl
  libxml-namespacesupport-perl libxml-parser-perl libxml-rss-perl
  libxml-sax-perl libxml-stream-perl libxml-twig-perl libxml1 libxml2
  libxml2-utils libxmu6 libxmuu1 libxosd2 libxp6 libxplc0.3.13 libxpm4
  libxrandr2 libxrender1 libxres1 libxslt1.1 libxss1 libxt6 libxtrap6 libxtst6
  libxv1 libxvidcore4 libxvmc1 libxxf86dga1 libxxf86misc1 libxxf86vm1
  libzephyr3 libzlib-ruby linux-generic linux-headers-2.6.22-12
  linux-headers-2.6.22-12-generic linux-headers-2.6.22-14
  linux-headers-2.6.22-14-generic linux-headers-2.6.24-16
  linux-headers-2.6.24-16-generic linux-headers-2.6.24-19
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-22
  linux-headers-2.6.24-22-generic linux-headers-2.6.24-23
  linux-headers-2.6.24-23-generic linux-headers-generic
  linux-image-2.6.22-12-generic linux-image-2.6.22-14-generic
  linux-image-2.6.24-16-generic linux-image-2.6.24-16-openvz
  linux-image-2.6.24-16-rt linux-image-2.6.24-16-server
  linux-image-2.6.24-18-generic linux-image-2.6.24-19-generic
  linux-image-2.6.24-22-generic linux-image-2.6.24-23-generic
  linux-image-generic linux-restricted-modules-2.6.22-12-generic
  linux-restricted-modules-2.6.22-14-generic
  linux-restricted-modules-2.6.24-16-generic
  linux-restricted-modules-2.6.24-16-server
  linux-restricted-modules-2.6.24-19-generic
  linux-restricted-modules-2.6.24-22-generic
  linux-restricted-modules-2.6.24-23-generic linux-restricted-modules-common
  linux-restricted-modules-generic linux-sound-base
  linux-ubuntu-modules-2.6.22-12-generic
  linux-ubuntu-modules-2.6.22-14-generic
  linux-ubuntu-modules-2.6.24-16-generic
  linux-ubuntu-modules-2.6.24-19-generic
  linux-ubuntu-modules-2.6.24-22-generic
  linux-ubuntu-modules-2.6.24-23-generic locales login logrotate lp-solve
  lsb-base lsb-release lshw lsof ltrace lynx lzma m4 make makedev man-db mawk
  mcpp mdetect mesa-utils metacity metacity-common mii-diag mikmod min12xxw
  mktemp mlocate module-init-tools mono-2.0-devel mono-2.0-service
  mono-apache-server mono-apache-server2 mono-basic-dbg mono-common
  mono-fastcgi-server mono-fastcgi-server2 mono-gac mono-gmcs mono-jay
  mono-jit mono-jit-dbg mono-mcs mono-mjs mono-runtime mono-smcs mono-utils
  mono-vbnc mono-xbuild mono-xsp mono-xsp-base mono-xsp2 mono-xsp2-base
  monodevelop monodevelop-nunit monodevelop-versioncontrol monodoc
  monodoc-base monodoc-browser monodoc-http mount mousetweaks
  mozilla-plugin-vlc mplayer mscompress msttcorefonts mtools mtr-tiny
  mysql-client-5.0 mysql-server mysql-server-5.0 nano nautilus
  nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share
  ncbi-tools-x11 ncurses-base ncurses-bin net-tools netbase netcat
  netcat-traditional notification-daemon ntfs-3g ntp ntpdate nunit
  nunit-console nvidia-glx-new nvidia-kernel-common nvidia-settings o3read
  obex-data-server odbcinst1debian1 onboard openbsd-inetd openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib openoffice.org openoffice.org-base
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-filter-binfilter openoffice.org-filter-mobiledev
  openoffice.org-gnome openoffice.org-gtk openoffice.org-hyphenation
  openoffice.org-impress openoffice.org-java-common openoffice.org-math
  openoffice.org-officebean openoffice.org-style-human openoffice.org-writer
  openoffice.org-writer2latex openssh-client openssh-server openssl
  openssl-blacklist openvpn oprofile p7zip-full parted passwd patch pciutils
  pcmciautils perl perl-base perl-modules phonon phonon-backend-gstreamer php5
  php5-cli php5-common php5-mcrypt php5-mysql phpmyadmin pidgin pidgin-otr
  pitivi pkg-config pm-utils pnm2ppa po-debconf policykit policykit-gnome
  poppler-utils popularity-contest postfix postfix-ldap postgresql
  postgresql-8.3 postgresql-client-8.3 postgresql-client-common
  postgresql-common powermgmt-base powernowd ppp pppconfig pppoeconf procps
  psmisc pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf
  pulseaudio-module-x11 pulseaudio-utils purrr pxljr pybridge pybridge-common
  pychecker python python-4suite-xml python-apport python-apt python-at-spi
  python-bittorrent python-brlapi python-cairo python-central python-chm
  python-compizconfig python-configobj python-cups python-dbus python-dev
  python-egenix-mxdatetime python-egenix-mxtools python-gconf python-gdata
  python-gdbm python-glade2 python-gmenu python-gnome2 python-gnome2-desktop
  python-gnome2-extras python-gnomecanvas python-gnupginterface python-gobject
  python-gobject-dev python-gst0.10 python-gtk2 python-gtkhtml2
  python-gtksourceview2 python-imaging python-imaging-tk python-launchpad-bugs
  python-launchpad-integration python-libxml2 python-libxslt1 python-minimal
  python-notify python-numeric python-numpy python-openssl
  python-pkg-resources python-problem-report python-psycopg python-psycopg2
  python-pyatspi python-pychart python-pydot python-pygame python-pyopenssl
  python-pyorbit python-pyparsing python-reportlab python-setuptools
  python-sexy python-software-properties python-support python-tk
  python-twisted-bin python-twisted-core python-tz python-uno python-virtkey
  python-vte python-wxglade python-wxgtk2.6 python-wxgtk2.8 python-wxtools
  python-wxversion python-xdg python-xml python-zopeinterface python2.4
  python2.4-minimal python2.5 python2.5-dev python2.5-minimal qemu
  qemu-launcher qemulator quagga quanta quota rdesktop readahead refblas3
  reiserfsprogs rhino rhythmbox rpm rrdtool rss-glx rsync samba samba-common
  sasl2-bin scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule
  scim-modules-socket screen screensaver-default-images scrollkeeper seahorse
  sed serpentine sgml-base sgml-data shared-mime-info slapd slocate smbclient
  smbldap-tools software-properties-gtk soprano-daemon spamassassin spe splix
  sqlite sqlite3 squashfs-tools squid ssh ssh-askpass-gnome ssl-cert
  startup-tasks strace subversion sudo sun-java6-bin sun-java6-jre
  swfdec-mozilla synaptic sysinfo sysklogd syslinux
  system-config-printer-common system-config-printer-gnome system-services
  system-tools-backends sysvutils tangerine-icon-theme tar tasksel
  tasksel-data tcl8.4 tcpd tcpdump tecnoballz telnet tftpd-hpa tidy time
  timeout tinyerp-server tk8.4 totem totem-common totem-gstreamer
  totem-mozilla totem-plugins tracker tracker-search-tool transmission-gtk
  tsclient ttf-arabeyes ttf-arphic-uming ttf-bitstream-vera ttf-dejavu
  ttf-dejavu-core ttf-dejavu-extra ttf-dustin ttf-freefont ttf-gentium
  ttf-indic-fonts-core ttf-kochi-gothic ttf-kochi-mincho ttf-lao
  ttf-malayalam-fonts ttf-mgopen ttf-opensymbol ttf-sil-gentium ttf-thai-tlwg
  ttf-unfonts-core tzdata ubufox ubuntu-artwork ubuntu-docs ubuntu-keyring
  ubuntu-minimal ubuntu-standard ubuntu-tweak ucf uck udev ufw
  unattended-upgrades unixodbc unrar unzip unzoo update-inetd update-manager
  update-manager-core upstart upstart-compat-sysv upstart-logd usbutils
  usplash usplash-theme-ubuntu util-linux util-linux-locales uuid-runtime
  vbetool vdr vdr-plugin-vcd vim-common vim-gnome vim-tiny vinagre vino
  virtualbox-ose virtualbox-ose-modules-2.6.24-16-generic
  virtualbox-ose-modules-2.6.24-16-openvz virtualbox-ose-modules-2.6.24-16-rt
  virtualbox-ose-modules-2.6.24-16-server vlan vlc vlc-nox vlc-plugin-alsa
  vlc-plugin-arts vlc-plugin-esd vlc-plugin-ggi vlc-plugin-pulse
  vlc-plugin-sdl w3m wget whiptail whois winbind winpdb wireless-tools wodim
  wpasupplicant wvdial wxvlc x-ttcidfont-conf x11-apps x11-common
  x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils
  x264 xauth xbase-clients xbitmaps xdg-user-dirs xdg-user-dirs-gtk
  xfonts-100dpi xfonts-75dpi xfonts-base xfonts-encodings xfonts-scalable
  xfonts-utils xgnokii xinit xml-core xmms-xmmplayer xmms2-core
  xmms2-plugin-all xmms2-plugin-alsa xmms2-plugin-ao xmms2-plugin-asx
  xmms2-plugin-avcodec xmms2-plugin-avformat xmms2-plugin-cdda
  xmms2-plugin-cue xmms2-plugin-curl xmms2-plugin-daap xmms2-plugin-flac
  xmms2-plugin-gnomevfs xmms2-plugin-ices xmms2-plugin-icymetaint
  xmms2-plugin-id3v2 xmms2-plugin-jack xmms2-plugin-lastfm xmms2-plugin-m3u
  xmms2-plugin-mad xmms2-plugin-mms xmms2-plugin-modplug xmms2-plugin-mp4
  xmms2-plugin-musepack xmms2-plugin-ofa xmms2-plugin-oss xmms2-plugin-pls
  xmms2-plugin-rss xmms2-plugin-sid xmms2-plugin-smb xmms2-plugin-vocoder
  xmms2-plugin-vorbis xmms2-plugin-wma xmms2-plugin-xml xmms2-plugin-xspf xoo
  xorg xresprobe xsane xscreensaver-data xscreensaver-gl xserver-xephyr
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-cyrix xserver-xorg-video-dummy
  xserver-xorg-video-fbdev xserver-xorg-video-glint xserver-xorg-video-i128
  xserver-xorg-video-i810 xserver-xorg-video-intel xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-rendition
  xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xsltproc xterm
  xulrunner-1.9 xulrunner-1.9-gnome-support xutils xutils-dev xvnc4viewer yelp
  zenity zip zlib1g
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
0 upgraded, 0 newly installed, 1846 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 5154MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase [COLOR="Red"]'Yes, do as I say!'[/COLOR]
 ?]
[COLOR="Blue"]Here if i say 'Yes, do as I say' it is removing all files. to fix this problem what i have to do. I tried with synaptic also but i am getting same issue.[/COLOR]
Please help me !!!:(

---

### Post by directhex on 2009-04-16
Odd. What does "aptitude install ubuntu-desktop" return?

---

### Post by somepalli on 2009-05-06
Thank you
[COLOR="Red"][SIZE="5"]After using following command i am getting this error[/SIZE][/COLOR] 


root@ubuntu:~# [COLOR="Blue"]aptitude install ubtuntu-desktop[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "ubtuntu-desktop"
Couldn't find any package whose name or description matched "ubtuntu-desktop"
The following packages are BROKEN:
  cpp-4.3 gcc-4.2 gcc-4.3 libgcc1 libgomp1 
The following packages are unused and will be REMOVED:
  cpp-4.2 libdmx1 libnl1 libsmbios1 pm-utils 
The following packages have been automatically kept back:
  clamav clamav-daemon clamav-freshclam dansguardian libqt4-core 
The following packages have been kept back:
  doc-base flex gcc k3b language-pack-en language-pack-gnome-en libpurple0 
  linux-generic linux-headers-generic linux-image-generic 
  linux-restricted-modules-generic ntfs-3g pidgin pidgin-data 
0 packages upgraded, 0 newly installed, 5 to remove and 20 not upgraded.
Need to get 0B of archives. After unpacking 7688kB will be freed.
The following packages have unmet dependencies:
  libgomp1: Depends: gcc-4.3-base (= 4.3.2-1.1) but 4.3.3-5ubuntu4 is installed.
  gcc-4.2: Depends: cpp-4.2 (= 4.2.4-1ubuntu3) but it is not installable
           Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-1ubuntu4 is installed.
  gcc-4.3: Depends: cpp-4.3 (= 4.3.3-5ubuntu4) but 4.3.2-1.1 is installed.
           Depends: binutils (>= 2.19.1) but 2.18.1~cvs20080103-0ubuntu1 is installed.
           Depends: libgcc1 (>= 1:4.3.3-5ubuntu4) but 1:4.3.2-1.1 is installed.
           Depends: libgomp1 (>= 4.3.3-5ubuntu4) but 4.3.2-1.1 is installed.
  libgcc1: Depends: gcc-4.3-base (= 4.3.2-1.1) but 4.3.3-5ubuntu4 is installed.
  cpp-4.3: Depends: gcc-4.3-base (= 4.3.2-1.1) but 4.3.3-5ubuntu4 is installed.
Resolving dependencies...
E: I wasn't able to locate file for the ebox-squid package. This might mean you need to manually fix this package.
The following actions will resolve these dependencies:

Remove the following packages:
cpp-4.3
gcc-4.3

Keep the following packages at their current version:
cpp-4.2 [4.2.4-1ubuntu4 (hardy-proposed, now)]

Upgrade the following packages:
gcc-4.2 [4.2.4-1ubuntu3 (hardy-updates, hardy-security, now) -> 4.2.4-1ubuntu4
(hardy-proposed)]

Downgrade the following packages:
cpp [4:4.3.2-2 (now) -> 4:4.2.3-1ubuntu6 (hardy-updates)]
libgcc1 [1:4.3.2-1.1 (now) -> 1:4.2.4-1ubuntu4 (hardy-proposed)]
libgomp1 [4.3.2-1.1 (now) -> 4.2.4-1ubuntu4 (hardy-proposed)]

Score is 243

Accept this solution? [Y/n/q/?] y
The following packages are unused and will be REMOVED:
  libdmx1 libmpfr1ldbl libnl1 libsmbios1 pm-utils 
The following packages have been automatically kept back:
  clamav clamav-daemon clamav-freshclam dansguardian libqt4-core 
The following packages will be automatically REMOVED:
  cpp-4.3 gcc-4.3 
The following packages will be DOWNGRADED:
  cpp libgcc1 libgomp1 
The following packages have been kept back:
  doc-base flex gcc k3b language-pack-en language-pack-gnome-en libpurple0 
  linux-generic linux-headers-generic linux-image-generic 
  linux-restricted-modules-generic ntfs-3g pidgin pidgin-data 
The following packages will be REMOVED:
  cpp-4.3 gcc-4.3 
The following packages will be upgraded:
  gcc-4.2 
1 packages upgraded, 0 newly installed, 3 downgraded, 7 to remove and 19 not upgraded.
Need to get 0B of archives. After unpacking 14.9MB will be freed.
Do you want to continue? [Y/n/?] y
[COLOR="Red"][SIZE="4"]Writing extended state information... Error!
E: I wasn't able to locate file for the ebox-squid package. This might mean you need to manually fix this package.[/SIZE][/COLOR]
root@ubuntu:~#
[COLOR="SeaGreen"][SIZE="5"]What i have to do here?[/SIZE][/COLOR]

---

### Post by directhex on 2009-05-06
> **somepalli said:**
> [COLOR="SeaGreen"][SIZE="5"]What i have to do here?[/SIZE][/COLOR]

Spell "ubuntu-desktop" properly, that would be a good start

---

### Post by somepalli on 2009-05-07
Thank you in Advance...

root@ubuntu:~# [COLOR="Blue"][SIZE="3"]aptitude install ubuntu-desktop[/SIZE][/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information     
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  cpp-4.3 gcc-4.2 gcc-4.3 libgcc1 libgomp1 
The following packages have been automatically kept back:
  clamav clamav-daemon clamav-freshclam dansguardian libqt4-core 
The following NEW packages will be automatically installed:
  acl acpid desktop-base gdm gdm-themes gnome-mount hal libgmime2.2-cil 
  libsmbios-bin libsmbiosxml1 network-manager radeontool smartdimmer 
  sound-juicer 
The following packages have been kept back:
  doc-base flex gcc k3b language-pack-en language-pack-gnome-en libpurple0 
  linux-generic linux-headers-generic linux-image-generic 
  linux-restricted-modules-generic ntfs-3g pidgin pidgin-data 
The following NEW packages will be installed:
  acl acpi acpi-support acpid desktop-base fast-user-switch-applet gdm 
  gdm-themes gnome-mount gnome-power-manager gnome-session 
  gnome-volume-manager hal hal-cups-utils libgmime2.2-cil libsmbios-bin 
  libsmbiosxml1 network-manager network-manager-gnome 
  powermanagement-interface pulseaudio-module-hal radeontool smartdimmer 
  sound-juicer tomboy ubuntu-desktop update-notifier 
0 packages upgraded, 27 newly installed, 0 to remove and 20 not upgraded.
Need to get 0B of archives. After unpacking 69.9MB will be used.
The following packages have unmet dependencies:
  libgomp1: Depends: gcc-4.3-base (= 4.3.2-1.1) but 4.3.3-5ubuntu4 is installed.
  gcc-4.2: Depends: cpp-4.2 (= 4.2.4-1ubuntu3) but 4.2.4-1ubuntu4 is installed.
           Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-1ubuntu4 is installed.
  gcc-4.3: Depends: cpp-4.3 (= 4.3.3-5ubuntu4) but 4.3.2-1.1 is installed.
           Depends: binutils (>= 2.19.1) but 2.18.1~cvs20080103-0ubuntu1 is installed.
           Depends: libgcc1 (>= 1:4.3.3-5ubuntu4) but 1:4.3.2-1.1 is installed.
           Depends: libgomp1 (>= 4.3.3-5ubuntu4) but 4.3.2-1.1 is installed.
  libgcc1: Depends: gcc-4.3-base (= 4.3.2-1.1) but 4.3.3-5ubuntu4 is installed.
  cpp-4.3: Depends: gcc-4.3-base (= 4.3.2-1.1) but 4.3.3-5ubuntu4 is installed.
Resolving dependencies...
E: I wasn't able to locate file for the ebox-squid package. This might mean you need to manually fix this package.
The following actions will resolve these dependencies:

Remove the following packages:
cpp-4.3
gcc-4.3

Install the following packages:
acpi-support [0.109 (hardy)]

Upgrade the following packages:
gcc-4.2 [4.2.4-1ubuntu3 (hardy-updates, hardy-security, now) -> 4.2.4-1ubuntu4
(hardy-proposed)]

Downgrade the following packages:
cpp [4:4.3.2-2 (now) -> 4:4.2.3-1ubuntu6 (hardy-updates)]
libgcc1 [1:4.3.2-1.1 (now) -> 1:4.2.4-1ubuntu4 (hardy-proposed)]
libgomp1 [4.3.2-1.1 (now) -> 4.2.4-1ubuntu4 (hardy-proposed)]

Leave the following dependencies unresolved:
acpi-support recommends toshset
Score is 0

Accept this solution? [Y/n/q/?] Y
The following packages are unused and will be REMOVED:
  libmpfr1ldbl 
The following packages have been automatically kept back:
  clamav clamav-daemon clamav-freshclam dansguardian libqt4-core 
The following NEW packages will be automatically installed:
  acl acpid desktop-base gdm gdm-themes gnome-mount hal libgmime2.2-cil 
  libsmbios-bin libsmbiosxml1 network-manager radeontool smartdimmer 
  sound-juicer 
The following packages will be automatically REMOVED:
  cpp-4.3 gcc-4.3 
The following packages will be DOWNGRADED:
  cpp libgcc1 libgomp1 
The following packages have been kept back:
  doc-base flex gcc k3b language-pack-en language-pack-gnome-en libpurple0 
  linux-generic linux-headers-generic linux-image-generic 
  linux-restricted-modules-generic ntfs-3g pidgin pidgin-data 
The following NEW packages will be installed:
  acl acpi acpi-support acpid desktop-base fast-user-switch-applet gdm 
  gdm-themes gnome-mount gnome-power-manager gnome-session 
  gnome-volume-manager hal hal-cups-utils libgmime2.2-cil libsmbios-bin 
  libsmbiosxml1 network-manager network-manager-gnome 
  powermanagement-interface pulseaudio-module-hal radeontool smartdimmer 
  sound-juicer tomboy ubuntu-desktop update-notifier 
The following packages will be REMOVED:
  cpp-4.3 gcc-4.3 
The following packages will be upgraded:
  gcc-4.2 
1 packages upgraded, 27 newly installed, 3 downgraded, 3 to remove and 19 not upgraded.
Need to get 0B of archives. After unpacking 56.3MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Error!
[COLOR="Red"][SIZE="4"]E: I wasn't able to locate file for the ebox-squid package. This might mean you need to manually fix this package.[/SIZE][/COLOR]
root@ubuntu:~# 
[COLOR="Green"]
Again i am getting same problem........[/COLOR]

---

### Post by directhex on 2009-05-07
> **somepalli said:**
> [COLOR="Green"]
Again i am getting same problem........[/COLOR]

Your /etc/apt/sources.list sounds entirely broken. Paste the contents of /etc/apt/sources.list

---

### Post by somepalli on 2009-05-07
[COLOR="Blue"]Thank you[/COLOR]

:popcorn:

[COLOR="Green"]I got solution[/COLOR]

I changed the all of my Hardy repositories to Jaunty repositories means just i replaced Jaunty instead of hardy but [COLOR="Lime"]i am giving my source.list here[/COLOR]

#

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 8.04 _jaunty Heron_ - Release amd64 (20080423)]/ jaunty main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
# deb [http://ppa.launchpad.net/juruen/ubuntu](http://ppa.launchpad.net/juruen/ubuntu) jaunty main
# deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) jaunty main
# deb [http://directhex.mfgames.com/](http://directhex.mfgames.com/) jaunty main

# deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) jaunty main
# deb-src [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) jaunty main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports restricted main multiverse universe




deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse

---

### Post by Partyboi2 on 2009-05-07
> I changed the all of my Hardy repositories to Jaunty repositories means just i replaced Jaunty instead of hardy but [COLOR=Lime]i am giving my source.list here[/COLOR]
If you are running hardy and replace your sources.list with the jaunty ones you will end up with breakages. 
[COLOR=Lime][/COLOR]

---

### Post by directhex on 2009-05-07
> **Partyboi2 said:**
> If you are running hardy and replace your sources.list with the jaunty ones you will end up with breakages. 
[COLOR=Lime][/COLOR]

Indeed. Hardy -> Jaunty is not a supported upgrade path. The following are allowed:

LTS -> LTS+1 (e.g. Dapper -> Hardy)
Distro -> Distro+1 (e.g. Hardy -> Intrepid)

Skipping releases is unsupported, and may break, as a package maintainer may make certain assumptions about package versions when applying certain logic

---

### Post by somepalli on 2009-05-09
[COLOR="Blue"][SIZE="4"]But i changed my source.list from Hardy to Jaunty .. then my broken packages fixed,,,, but i dont know may this will work for some other packages or not..... [/SIZE][/COLOR]


[COLOR="Green"][SIZE="4"]Thank you for giving reply[/SIZE][/COLOR]

---

