---
title: "Upgrade from 9.04 to 9.10 fails because ubuntu-desktop has a broken dep"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by stalet on 2009-10-29
Im not really sure how to interpret this log but it seems some new package has a broken dependency ?

Output from apt.log:
Log time: 2009-10-29 20:47:39.522510
Log time: 2009-10-29 20:47:42.477616
Log time: 2009-10-29 20:48:10.014035
Installing libsgutils2-2 as dep of sg3-utils
Installing libio-compress-perl as dep of libio-compress-base-perl
Installing libcompress-raw-zlib-perl as dep of libio-compress-perl
Installing perl as dep of libcompress-raw-zlib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing libcompress-raw-bzip2-perl as dep of libio-compress-perl
Installing libgtk2.0-0 as dep of bluez-gnome
Installing libcups2 as dep of libgtk2.0-0
Installing libgnutls26 as dep of libcups2
Installing libgcrypt11 as dep of libgnutls26
Installing libgpg-error0 as dep of libgcrypt11
Installing libtasn1-3 as dep of libgnutls26
Installing libgssapi-krb5-2 as dep of libcups2
Installing libk5crypto3 as dep of libgssapi-krb5-2
Installing libkrb5support0 as dep of libk5crypto3
Installing libkrb5-3 as dep of libgssapi-krb5-2
Installing libglib2.0-0 as dep of libgtk2.0-0
Installing libc6 as dep of libglib2.0-0
Installing libc-bin as dep of libc6
Installing libselinux1 as dep of libglib2.0-0
Installing libmono-system2.0-cil as dep of libmono-data-tds2.0-cil
Installing mono-runtime as dep of libmono-system2.0-cil
Installing mono-gac as dep of mono-runtime
Installing mono-2.0-gac as dep of mono-gac
Installing libtalloc1 as dep of libsmbclient
Installing libwbclient0 as dep of libsmbclient
Installing libflickrnet2.2-cil as dep of f-spot
Installing libgconf2.0-cil as dep of f-spot
Installing libglade2.0-cil as dep of f-spot
Installing libglib2.0-cil as dep of libglade2.0-cil
Installing libgtk2.0-cil as dep of libglade2.0-cil
Installing libgnome-keyring1.0-cil as dep of f-spot
Installing libgnome-vfs2.0-cil as dep of f-spot
Installing libgphoto2-2 as dep of f-spot
Installing libgphoto2-port0 as dep of libgphoto2-2
Installing libmono-cairo2.0-cil as dep of f-spot
Installing libmono-posix2.0-cil as dep of f-spot
Installing util-linux as dep of dmsetup
Installing upstart as dep of util-linux
Installing libdbus-1-3 as dep of upstart
Installing mountall as dep of upstart
Installing libusplash0 as dep of usplash
Installing initramfs-tools as dep of usplash
Installing busybox-initramfs as dep of initramfs-tools
Installing udev as dep of initramfs-tools
Installing libdevkit-power-gobject1 as dep of gdm
Installing libpolkit-gobject-1-0 as dep of gdm
Installing libeggdbus-1-0 as dep of libpolkit-gobject-1-0
Installing libxklavier15 as dep of gdm
Installing libxml2 as dep of libxklavier15
Installing gnome-session-bin as dep of gdm
Installing policykit-1-gnome as dep of gnome-session-bin
Installing libpolkit-agent-1-0 as dep of policykit-1-gnome
Installing policykit-1 as dep of policykit-1-gnome
Installing libpolkit-backend-1-0 as dep of policykit-1
Installing console-setup as dep of xserver-xorg
Installing hal as dep of gdm
Installing libblkid1 as dep of hal
Installing dbus as dep of hal
Installing libbsd0 as dep of libedit2
Installing openoffice.org-core as dep of openoffice.org-draw
Installing openoffice.org-common as dep of openoffice.org-core
Installing openoffice.org-style-galaxy as dep of openoffice.org-common
new important dependency: xfonts-mathml
Installing xfonts-mathml as dep of openoffice.org-common
Installing latex-xft-fonts as dep of xfonts-mathml
Installing libhunspell-1.2-0 as dep of openoffice.org-core
Installing libicu40 as dep of openoffice.org-core
Installing libneon27-gnutls as dep of openoffice.org-core
Installing librdf0 as dep of openoffice.org-core
Installing libmysqlclient16 as dep of librdf0
Installing mysql-common as dep of libmysqlclient16
Installing libpq5 as dep of librdf0
Installing libraptor1 as dep of librdf0
Installing libsqlite3-0 as dep of librdf0
Installing libstdc++6 as dep of openoffice.org-core
Installing gcc-4.4-base as dep of libstdc++6
Installing libgcc1 as dep of libstdc++6
Installing ure as dep of openoffice.org-core
Installing uno-libs3 as dep of ure
Installing libbluetooth3 as dep of bluez-alsa
Installing libiec61883-0 as dep of libfreebob0
Installing libraw1394-11 as dep of libiec61883-0
new important dependency: libcanberra-pulse
Installing libcanberra-pulse as dep of gnome-session-canberra
Installing libcanberra0 as dep of libcanberra-pulse
Installing libsm6 as dep of libsm-dev
Installing libgstfarsight0.10-0 as dep of libpurple0
Installing libgssdp-1.0-1 as dep of libgstfarsight0.10-0
Installing libgstreamer-plugins-base0.10-0 as dep of libgstfarsight0.10-0
Installing libgstreamer0.10-0 as dep of libgstreamer-plugins-base0.10-0
Installing libgupnp-1.0-2 as dep of libgstfarsight0.10-0
Installing libsoup2.4-1 as dep of libgupnp-1.0-2
Installing libgupnp-igd-1.0-2 as dep of libgstfarsight0.10-0
Installing libnice0 as dep of libgstfarsight0.10-0
Installing gstreamer0.10-plugins-good as dep of libgstfarsight0.10-0
Installing libsoup-gnome2.4-1 as dep of gstreamer0.10-plugins-good
Installing libtag1c2a as dep of gstreamer0.10-plugins-good
Installing libtag1-vanilla as dep of libtag1c2a
Installing gstreamer0.10-nice as dep of libgstfarsight0.10-0
Installing libsilcclient-1.1-3 as dep of libpurple0
Installing libzephyr4 as dep of libpurple0
Installing python-gobject as dep of python-gnome2
Installing python-support as dep of python-gobject
Installing python-gconf as dep of python-gnome2
Installing tsconf as dep of libts-0.0-0
Installing apt as dep of apt-transport-https
Installing openssh-client as dep of openssh-server
Installing indicator-applet-session as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing indicator-applet as dep of indicator-applet-session
Installing indicator-messages as dep of indicator-applet
Installing libdbusmenu-glib0 as dep of indicator-messages
Installing libdbusmenu-gtk0 as dep of indicator-messages
Installing libindicate3 as dep of indicator-messages
Installing indicator-session as dep of indicator-applet-session
Installing libempathy30 as dep of indicator-session
Installing libnm-glib2 as dep of libempathy30
Installing libgudev-1.0-0 as dep of libnm-glib2
Installing libnm-util1 as dep of libnm-glib2
Installing libuuid1 as dep of libnm-util1
Installing libtelepathy-farsight0 as dep of libempathy30
Installing libtelepathy-glib0 as dep of libtelepathy-farsight0
Installing telepathy-mission-control-5 as dep of libempathy30
Installing devicekit-power as dep of indicator-session
Installing libgd2-xpm as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing software-center as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing python-apt as dep of software-center
Installing apt-utils as dep of python-apt
new important dependency: libjs-jquery
Installing libjs-jquery as dep of python-apt
Installing python-aptdaemon as dep of software-center
Installing aptdaemon as dep of python-aptdaemon
Installing python-aptdaemon-gtk as dep of software-center
Installing sreadahead as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing xsplash as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing ubuntu-xsplash-artwork as dep of xsplash
new important dependency: empathy
Installing empathy as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing libebook1.2-9 as dep of empathy
Installing libcamel1.2-14 as dep of libebook1.2-9
Installing libedataserver1.2-11 as dep of libcamel1.2-14
Installing libempathy-gtk28 as dep of empathy
Installing libenchant1c2a as dep of libempathy-gtk28
Installing libwebkit-1.0-2 as dep of libempathy-gtk28
Installing libwebkit-1.0-common as dep of libwebkit-1.0-2
Installing libindicate-gtk1 as dep of empathy
Installing telepathy-gabble as dep of empathy
Installing libloudmouth1-0 as dep of telepathy-gabble
Installing telepathy-salut as dep of empathy
Installing telepathy-haze as dep of empathy
Installing telepathy-butterfly as dep of empathy
Installing python-telepathy as dep of telepathy-butterfly
Installing python-papyon as dep of telepathy-butterfly
Installing python-crypto as dep of python-papyon
new important dependency: evolution-couchdb
Installing evolution-couchdb as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing evolution as dep of evolution-couchdb
Installing libebackend1.2-0 as dep of evolution
Installing libecal1.2-7 as dep of evolution
Installing libedataserverui1.2-8 as dep of evolution
Installing libegroupwise1.2-13 as dep of evolution
Installing libexchange-storage1.2-3 as dep of evolution
Installing libgdata-google1.2-1 as dep of evolution
Installing libgdata1.2-1 as dep of libgdata-google1.2-1
Installing libgnome-desktop-2-11 as dep of evolution
Installing libstartup-notification0 as dep of libgnome-desktop-2-11
Installing libxcb-atom1 as dep of libstartup-notification0
Installing libxcb-aux0 as dep of libstartup-notification0
Installing libxcb-event1 as dep of libstartup-notification0
Installing evolution-common as dep of evolution
Installing evolution-data-server as dep of evolution
Installing libedata-book1.2-2 as dep of evolution-data-server
Installing libedata-cal1.2-6 as dep of evolution-data-server
Installing evolution-data-server-common as dep of evolution-data-server
previously satisfied important dependency on evolution-documentation
Installing evolution-documentation-en as dep of evolution
Installing libcouchdb-glib-1.0-1 as dep of evolution-couchdb
Installing libjson-glib-1.0-0 as dep of libcouchdb-glib-1.0-1
Installing desktopcouch as dep of evolution-couchdb
Installing couchdb-bin as dep of desktopcouch
Installing libcurl3 as dep of couchdb-bin
Installing erlang-base as dep of couchdb-bin
Installing libsctp1 as dep of erlang-base
Installing lksctp-tools as dep of libsctp1
Installing erlang-crypto as dep of erlang-base
Installing erlang-syntax-tools as dep of erlang-base
Installing erlang-inets as dep of couchdb-bin
Installing erlang-mnesia as dep of erlang-inets
Installing erlang-public-key as dep of erlang-inets
Installing erlang-runtime-tools as dep of erlang-inets
Installing erlang-ssl as dep of erlang-inets
Installing erlang-xmerl as dep of couchdb-bin
Installing xulrunner-1.9.1 as dep of couchdb-bin
Installing python-couchdb as dep of desktopcouch
Installing python-httplib2 as dep of python-couchdb
Installing python-avahi as dep of desktopcouch
Installing python-desktopcouch as dep of desktopcouch
Installing python-gnomekeyring as dep of python-desktopcouch
Installing python-desktopcouch-records as dep of desktopcouch
Installing python-oauth as dep of python-desktopcouch-records
new important dependency: gnome-bluetooth
Installing gnome-bluetooth as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing libgnome-bluetooth7 as dep of gnome-bluetooth
Installing bluez as dep of gnome-bluetooth
Installing obexd-client as dep of gnome-bluetooth
new important dependency: gnome-disk-utility
Installing gnome-disk-utility as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing libgdu-gtk0 as dep of gnome-disk-utility
Installing libatasmart4 as dep of libgdu-gtk0
Installing libgdu0 as dep of gnome-disk-utility
Installing devicekit-disks as dep of gnome-disk-utility
Installing libparted1.8-12 as dep of devicekit-disks
new important dependency: ibus
Installing ibus as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing libibus1 as dep of ibus
Installing python-ibus as dep of ibus
Installing python-rsvg as dep of ibus
Installing ibus-gtk as dep of ibus
new important dependency: ibus-m17n
Installing ibus-m17n as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing libm17n-0 as dep of ibus-m17n
Installing libanthy0 as dep of libm17n-0
Installing libotf0 as dep of libm17n-0
Installing libthai0 as dep of libm17n-0
Installing libdatrie1 as dep of libthai0
Installing libthai-data as dep of libthai0
Installing m17n-db as dep of libm17n-0
Installing m17n-contrib as dep of libm17n-0
new important dependency: ibus-table
Installing ibus-table as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
new important dependency: kerneloops-daemon
Installing kerneloops-daemon as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
new important dependency: pulseaudio-module-bluetooth
Installing pulseaudio-module-bluetooth as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing libpulse0 as dep of pulseaudio-module-bluetooth
Installing pulseaudio as dep of pulseaudio-module-bluetooth
Installing pulseaudio-module-udev as dep of pulseaudio
new important dependency: speech-dispatcher
Installing speech-dispatcher as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing libdotconf1.0 as dep of speech-dispatcher
Installing libspeechd2 as dep of speech-dispatcher
Installing dpkg as dep of speech-dispatcher
new important dependency: telepathy-idle
Installing telepathy-idle as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
new important dependency: ttf-kacst
Installing ttf-kacst as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
new important dependency: ttf-vlgothic
Installing ttf-vlgothic as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
new important dependency: ubuntuone-client-gnome
Installing ubuntuone-client-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing ubuntuone-client as dep of ubuntuone-client-gnome
Installing python-ubuntuone-client as dep of ubuntuone-client
Installing python-ubuntuone-storageprotocol as dep of python-ubuntuone-client
Installing python-protobuf as dep of python-ubuntuone-storageprotocol
Installing protobuf-compiler as dep of python-protobuf
Installing libprotobuf3 as dep of protobuf-compiler
Installing python-pyinotify as dep of python-ubuntuone-client
Installing python-twisted-names as dep of python-ubuntuone-client
Installing python-configglue as dep of ubuntuone-client
new important dependency: usb-creator-gtk
Installing usb-creator-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing usb-creator-common as dep of usb-creator-gtk
Installing libavutil49 as dep of libswscale0
Installing openoffice.org-l10n-common as dep of openoffice.org-l10n-nb
Installing libhamcrest-java as dep of junit4
Installing libbz2-1.0 as dep of bzip2
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
Installing libopal3.6.4 as dep of ekiga
Installing libpt2.6.4 as dep of libopal3.6.4
Installing libpt2.6.4-plugins as dep of ekiga
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing language-pack-en-base as dep of language-pack-gnome-en
Installing language-pack-en as dep of language-pack-en-base
new important dependency: libaccess-bridge-java-jni
Installing libaccess-bridge-java-jni as dep of libaccess-bridge-java
new important dependency: libpam-modules
Installing libpam-modules as dep of update-notifier-common
Installing base-files as dep of libpam-modules
Installing pidgin as dep of pidgin-libnotify
Installing pidgin-data as dep of pidgin
Installing gthumb-data as dep of gthumb
Installing libice6 as dep of libice-dev
Installing libcolamd2.7.1 as dep of lp-solve
Installing libcommons-net2-java as dep of libwagon-java
Installing libmaven-scm-java as dep of libwagon-java
Installing libnetbeans-cvsclient-java as dep of libmaven-scm-java
Installing libplexus-containers-java as dep of libmaven-scm-java
Installing libgoogle-collections-java as dep of libplexus-containers-java
Installing libxbean-java as dep of libplexus-containers-java
Installing libasm2-java as dep of libxbean-java
Installing libasm3-java as dep of libxbean-java
Installing groovy as dep of libxbean-java
Installing libbsf-java as dep of groovy
Installing libmockobjects-java as dep of groovy
Installing libjline-java as dep of groovy
Installing libxstream-java as dep of groovy
Installing libxpp3-java as dep of libxstream-java
Installing ivy as dep of groovy
Installing libnekohtml-java as dep of libwagon-java
Installing eclipse-platform as dep of eclipse-jdt
Installing eclipse-platform-data as dep of eclipse-platform
Installing eclipse-rcp as dep of eclipse-platform
Installing libequinox-osgi-java as dep of eclipse-rcp
Installing libswt-gtk-3.5-java as dep of eclipse-rcp
Installing libswt-gtk-3.5-jni as dep of libswt-gtk-3.5-java
Installing eclipse-plugin-cvs as dep of eclipse-jdt
Installing gcj-4.3-base as dep of libgcj9-0-awt
Installing libgcj9-0 as dep of libgcj9-0-awt
previously satisfied important dependency on libgcj9-jar
Installing libgcj9-jar as dep of libgcj9-0
Installing libpulse-mainloop-glib0 as dep of gnome-media
Installing metacity-common as dep of metacity
Installing libexempi3 as dep of nautilus
Installing nautilus-data as dep of nautilus
Installing libqt4-designer as dep of libqt4-qt3support
Installing libqt4-script as dep of libqt4-designer
Installing libqt4-dbus as dep of libqt4-script
Installing libqt4-xml as dep of libqt4-dbus
Installing libqtcore4 as dep of libqt4-xml
Installing libqtgui4 as dep of libqt4-designer
Installing libqt4-network as dep of libqt4-qt3support
Installing libqt4-sql as dep of libqt4-qt3support
Installing libgnome2-common as dep of libgnome2-0
Installing libsepol1 as dep of sysvinit-utils
Installing compiz-core as dep of libcompizconfig0
Installing compiz-wrapper as dep of compiz-core
previously satisfied important dependency on compiz-plugins
Installing compiz-plugins as dep of compiz-core
Installing checkbox as dep of checkbox-gtk
Installing libbind9-50 as dep of bind9-host
Installing libdns50 as dep of libbind9-50
Installing libgeoip1 as dep of libdns50
Installing geoip-database as dep of libgeoip1
Installing libisc50 as dep of libdns50
Installing libisccfg50 as dep of libbind9-50
Installing libisccc50 as dep of libisccfg50
Installing liblwres50 as dep of bind9-host
Installing libgamin0 as dep of gamin
Installing gvfs as dep of gvfs-fuse
Installing libaspell15 as dep of aspell
Installing nvidia-185-modaliases as dep of nvidia-common
Installing python2.6-minimal as dep of python-minimal
Installing xsane-common as dep of xsane
Installing libass3 as dep of gstreamer0.10-plugins-bad
Installing libcelt0 as dep of gstreamer0.10-plugins-bad
Installing libdirac0c2a as dep of gstreamer0.10-plugins-bad
Installing libdirectfb-1.2-0 as dep of gstreamer0.10-plugins-bad
Installing libgsm1 as dep of gstreamer0.10-plugins-bad
Installing libkate1 as dep of gstreamer0.10-plugins-bad
Installing libmimic0 as dep of gstreamer0.10-plugins-bad
Installing libschroedinger-1.0-0 as dep of gstreamer0.10-plugins-bad
Installing liboil0.3 as dep of libschroedinger-1.0-0
Installing libtotem-plparser12 as dep of libbrasero-media0
Installing libgmime-2.4-2 as dep of libtotem-plparser12
Installing libgcj-common as dep of libgcj-bc
Installing libgcj10 as dep of libgcj-bc
Installing gcj-4.4-base as dep of libgcj10
Installing gcj-4.4-jre-lib as dep of libgcj10
Installing libxine1-bin as dep of libxine1-x
Installing libgnomekbd4 as dep of gnome-applets
Installing libgnomekbd-common as dep of libgnomekbd4
Installing libgnomekbdui4 as dep of gnome-applets
Installing gnome-applets-data as dep of gnome-applets
new important dependency: python-gnomeapplet
Installing python-gnomeapplet as dep of gnome-applets
Installing libpoppler5 as dep of poppler-utils
Installing libsnmp-base as dep of libsnmp15
Installing network-manager as dep of network-manager-gnome
new important dependency: modemmanager
Installing modemmanager as dep of network-manager
Installing mobile-broadband-provider-info as dep of network-manager-gnome
Installing esound-common as dep of esound-clients
Installing samba-common as dep of smbclient
new important dependency: samba-common-bin
Installing samba-common-bin as dep of samba-common
Installing libreadline6 as dep of samba-common-bin
Installing libnewt0.52 as dep of whiptail
Installing libatspi1.0-0 as dep of brltty-x11
Installing brltty as dep of brltty-x11
Installing bluez-gnome as dep of libmbca0
Installing totem as dep of totem-plugins
Installing gstreamer0.10-plugins-base as dep of totem
Installing libtheora0 as dep of gstreamer0.10-plugins-base
Installing totem-common as dep of totem
new important dependency: totem-mozilla
Installing totem-mozilla as dep of totem
Installing libgdata5 as dep of totem-plugins
Installing libgdata-common as dep of libgdata5
Installing aisleriot as dep of gnome-games
Installing libcanberra-gtk0 as dep of aisleriot
Installing gnome-games-common as dep of aisleriot
Installing gnome-blackjack as dep of gnome-games
Installing glchess as dep of gnome-games
Installing glines as dep of gnome-games
Installing gnect as dep of gnome-games
Installing gnibbles as dep of gnome-games
Installing gnobots2 as dep of gnome-games
Installing gnome-sudoku as dep of gnome-games
Installing gnometris as dep of gnome-games
Installing libclutter-1.0-0 as dep of gnometris
Installing libclutter-gtk-0.10-0 as dep of gnometris
Installing gnomine as dep of gnome-games
Installing gnotravex as dep of gnome-games
Installing gnotski as dep of gnome-games
Installing gtali as dep of gnome-games
Installing iagno as dep of gnome-games
Installing gnome-mahjongg as dep of gnome-games
Installing same-gnome as dep of gnome-games
Installing libpst4 as dep of evolution-plugins
Installing gdebi-core as dep of gdebi
Installing libglibmm-2.4-1c2a as dep of libpangomm-1.4-1
Installing lib32bz2-1.0 as dep of ia32-libs
Installing libc6-i386 as dep of lib32bz2-1.0
Installing lib32v4l-0 as dep of ia32-libs
Installing epiphany-browser as dep of epiphany-gecko
Installing epiphany-browser-data as dep of epiphany-browser
Installing libgirepository1.0-0 as dep of epiphany-browser
Installing libseed0 as dep of epiphany-browser
Installing gnome-js-common as dep of libseed0
Installing gobject-introspection-glib-2.0 as dep of libseed0
Installing libglib2.0-dev as dep of gobject-introspection-glib-2.0
Installing gobject-introspection as dep of gobject-introspection-glib-2.0
Installing gobject-introspection-freedesktop as dep of libseed0
Installing libcairo2-dev as dep of gobject-introspection-freedesktop
Installing libcairo2 as dep of libcairo2-dev
Installing libxcb-render-util0 as dep of libcairo2
Installing libfontconfig1-dev as dep of libcairo2-dev
Installing libexpat1-dev as dep of libfontconfig1-dev
Installing libexpat1 as dep of libexpat1-dev
Installing libfreetype6-dev as dep of libfontconfig1-dev
Installing libfreetype6 as dep of libfreetype6-dev
Installing libxrender-dev as dep of libcairo2-dev
Installing libxrender1 as dep of libxrender-dev
Installing x11proto-render-dev as dep of libxrender-dev
Installing libpng12-dev as dep of libcairo2-dev
Installing libpng12-0 as dep of libpng12-dev
Installing libdirectfb-dev as dep of libcairo2-dev
Installing libdirectfb-extra as dep of libdirectfb-dev
Installing libjpeg62-dev as dep of libdirectfb-dev
Installing libjpeg62 as dep of libjpeg62-dev
Installing libxext-dev as dep of libdirectfb-dev
Installing libxext6 as dep of libxext-dev
Installing x11proto-xext-dev as dep of libxext-dev
Installing libsysfs-dev as dep of libdirectfb-dev
Installing libpixman-1-dev as dep of libcairo2-dev
Installing libpixman-1-0 as dep of libpixman-1-dev
Installing libxcb-render0-dev as dep of libcairo2-dev
Installing libxcb-render0 as dep of libxcb-render0-dev
Installing libxcb-render-util0-dev as dep of libcairo2-dev
Installing libxfixes-dev as dep of gobject-introspection-freedesktop
Installing x11proto-fixes-dev as dep of libxfixes-dev
Installing libxft-dev as dep of gobject-introspection-freedesktop
Installing libxml2-dev as dep of gobject-introspection-freedesktop
Installing mesa-common-dev as dep of gobject-introspection-freedesktop
Installing gobject-introspection-repository as dep of libseed0
Installing libantlr-java as dep of antlr
Installing xserver-xorg-core as dep of xserver-xorg-video-mga
Installing libmagickcore2 as dep of obex-data-server
Installing libdjvulibre21 as dep of libmagickcore2
Installing libdjvulibre-text as dep of libdjvulibre21
Installing libmagickwand2 as dep of libmagickcore2
Installing cups-ppdc as dep of cupsddk
Installing libcupsppdc1 as dep of cups-ppdc
Installing libglib-perl as dep of libgtk2-perl
Installing libpango-perl as dep of libgtk2-perl
Installing libgnome-menu2 as dep of libgnome-window-settings1
new important dependency: libmono-i18n-west2.0-cil
Installing libmono-i18n-west2.0-cil as dep of libmono-corlib2.0-cil
Installing gcc-4.3-base as dep of g++-4.3
Installing gcc-4.3 as dep of g++-4.3
Installing cpp-4.3 as dep of gcc-4.3
Installing libgomp1 as dep of gcc-4.3
Installing libstdc++6-4.3-dev as dep of g++-4.3
new important dependency: kpartx
Installing kpartx as dep of gparted
new important dependency: dmraid
Installing dmraid as dep of gparted
Installing libdmraid1.0.0.rc15 as dep of dmraid
Installing at-spi as dep of python-pyatspi
Installing media-player-info as dep of rhythmbox
Installing python2.6 as dep of libpython2.6
Installing libffado1 as dep of libjack0
Installing python-gmenu as dep of alacarte
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing liblzma0 as dep of kdelibs5
Installing libqt4-phonon as dep of kdelibs5
Installing libqt4-svg as dep of kdelibs5
Installing libsoprano4 as dep of kdelibs5
Installing soprano-daemon as dep of libsoprano4
Installing libstreamanalyzer0 as dep of kdelibs5
Installing libstreams0 as dep of libstreamanalyzer0
Installing kdelibs5-data as dep of kdelibs5
Installing kdelibs-bin as dep of kdelibs5
Installing python-gtkhtml2 as dep of python-gnome2-extras
Installing python-gtkmozembed as dep of python-gnome2-extras
Installing python-eggtrayicon as dep of python-gnome2-extras
Installing python-gtkspell as dep of python-gnome2-extras
Installing python-gksu2 as dep of python-gnome2-extras
Installing python-gdl as dep of python-gnome2-extras
Installing libgdl-1-3 as dep of python-gdl
Installing libgdl-1-common as dep of libgdl-1-3
Installing python-gda as dep of python-gnome2-extras
Installing libgda-4.0-4 as dep of python-gda
Installing libgda-4.0-common as dep of libgda-4.0-4
Installing libdrm-intel1 as dep of libgl1-mesa-dri
Installing libdrm-radeon1 as dep of libgl1-mesa-dri
Installing libvte9 as dep of gnome-terminal
Installing gnome-terminal-data as dep of gnome-terminal
Installing hplip as dep of hpijs
Installing hplip-data as dep of hplip
Installing linux-image-generic as dep of linux-generic
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing linux-image-2.6.31-14-generic as dep of linux-image-generic
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing libphysfs1 as dep of supertux
Installing cups-common as dep of cups-client
Installing mplayer-skins as dep of mplayer
Installing mplayer-nogui as dep of mplayer
Installing libx264-67 as dep of mplayer-nogui
new important dependency: byobu
Installing byobu as dep of screen
Installing libevent-1.4-2 as dep of transmission-gtk
Installing transmission-common as dep of transmission-gtk
Installing libcryptui0 as dep of seahorse
Installing libept0 as dep of aptitude
Installing openjdk-6-jre-headless as dep of icedtea-6-jre-cacao
Installing openjdk-6-jre-lib as dep of openjdk-6-jre-headless
Installing ecj as dep of ecj-gcj
Installing gcj-4.4-jre-headless as dep of ecj
Installing libecj-java-gcj as dep of ecj-gcj
Installing libscim8c2a as dep of scim
new important dependency: scim-gtk2-immodule
Installing scim-gtk2-immodule as dep of scim
Installing scim-modules-socket as dep of scim-gtk2-immodule
new important dependency: apport-symptoms
Installing apport-symptoms as dep of apport
Installing cpp as dep of g++
Installing cpp-4.4 as dep of cpp
Installing gcc as dep of g++
Installing gcc-4.4 as dep of gcc
Installing binutils as dep of gcc-4.4
Installing g++-4.4 as dep of g++
Installing libstdc++6-4.4-dev as dep of g++-4.4
Installing system-config-printer-udev as dep of hal-cups-utils
Installing python-cups as dep of system-config-printer-udev
Installing rsyslog as dep of ubuntu-minimal
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing libart2.0-cil as dep of libgnome2.24-cil
Installing e2fslibs as dep of e2fsprogs
Installing kdebase-runtime as dep of khelpcenter4
Installing libknotificationitem1 as dep of kdebase-runtime
Installing libplasma3 as dep of kdebase-runtime
Installing libqt4-webkit as dep of libplasma3
Installing kdebase-runtime-bin-kde4 as dep of kdebase-runtime
Installing kdebase-runtime-data as dep of kdebase-runtime
Installing libhd16 as dep of hwinfo
Installing update-manager-core as dep of update-manager
Installing librsvg2-2 as dep of librsvg2-common
Installing libgsf-1-114 as dep of librsvg2-2
Installing libruby1.8 as dep of ruby1.8
Installing gconf-defaults-service as dep of gconf-editor
new important dependency: notify-osd-icons
Installing notify-osd-icons as dep of notify-osd
Installing libasound2 as dep of lib32asound2
Installing libvlccore2 as dep of libvlc2
Installing vlc-data as dep of libvlccore2
Installing xserver-xorg-input-vmmouse as dep of xserver-xorg-input-all
Installing humanity-icon-theme as dep of human-theme
Installing libgnomeprint2.2-data as dep of libgnomeprint2.2-0
Installing python-speechd as dep of gnome-orca
new important dependency: python-louis
Installing python-louis as dep of gnome-orca
Installing liblouis0 as dep of python-louis
Installing liblouis-data as dep of liblouis0
Installing libgcj9-dev as dep of gcj-4.3
Installing firefox-3.5 as dep of firefox
Installing firefox-3.5-branding as dep of firefox-3.5
Installing python-gtk2 as dep of python-glade2
Installing default-jre as dep of default-jdk
Installing dia-common as dep of dia
Installing gnome-desktop-data as dep of gnome-about
Installing libpolkit-gtk-1-0 as dep of gnome-system-tools
Installing system-tools-backends as dep of gnome-system-tools
Installing libdvbpsi5 as dep of vlc-nox
Installing libxapian15 as dep of python-xapian
Installing ghostscript-cups as dep of cups-driver-gutenprint
Installing ghostscript as dep of ghostscript-cups
Installing libgs8 as dep of ghostscript
Installing libpam-runtime as dep of cron
Installing linux-headers-2.6.31-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.31-14 as dep of linux-headers-2.6.31-14-generic
Installing firefox-3.5-gnome-support as dep of firefox-3.0-gnome-support
Installing xulrunner-1.9.1-gnome-support as dep of firefox-3.5-gnome-support
Installing libcupscgi1 as dep of cups
Installing libcupsdriver1 as dep of cups
Installing libcupsmime1 as dep of cups
Installing zlib1g as dep of zlib1g-dev
Installing libmagic1 as dep of file
Installing apturl-common as dep of apturl
Installing libnetpbm10 as dep of netpbm
new important dependency: ttf-mscorefonts-installer
Installing ttf-mscorefonts-installer as dep of wine
Installing librpm0 as dep of rpm
Installing librpmio0 as dep of librpm0
Installing librpmbuild0 as dep of rpm
Installing trigger-rally as dep of trigger
Installing trigger-rally-data as dep of trigger-rally
Installing libplib1 as dep of supertuxkart
Installing libbit-vector-perl as dep of libwww-search-perl
Installing libcarp-clan-perl as dep of libbit-vector-perl
Installing libdate-manip-perl as dep of libwww-search-perl
Installing libfile-slurp-perl as dep of libwww-search-perl
Installing libgimp2.0 as dep of gimp
previously satisfied important dependency on gimp-data
Installing gimp-data as dep of libgimp2.0
Installing vim-runtime as dep of vim
new important dependency: vlc-plugin-pulse
Installing vlc-plugin-pulse as dep of vlc
previously satisfied important dependency on wormux
Installing wormux as dep of wormux-data
Installing dhcp3-common as dep of dhcp3-client
Installing liferea-data as dep of liferea
new important dependency: bcmwl-modaliases
Installing bcmwl-modaliases as dep of jockey-common
Installing libc-dev-bin as dep of libc6-dev
Installing libavahi-core6 as dep of avahi-daemon
Installing computer-janitor as dep of computer-janitor-gtk
new important dependency: libservlet2.5-java
Installing libservlet2.5-java as dep of velocity
new important dependency: libjdom1-java
Installing libjdom1-java as dep of velocity
Installing xorg-docs-core as dep of xorg
Installing libsasl2-modules as dep of libsasl2-2
Installing capplets-data as dep of gnome-control-center
Installing python-launchpadlib as dep of python-apport
Installing python-wadllib as dep of python-launchpadlib
Installing python-lazr-uri as dep of python-wadllib
Installing python-lazr-restfulclient as dep of python-launchpadlib
Installing ca-certificates as dep of ca-certificates-java
new important dependency: timidity-daemon
Installing timidity-daemon as dep of timidity
Installing libsub-name-perl as dep of libclass-accessor-perl
new important dependency: libcompress-bzip2-perl
Installing libcompress-bzip2-perl as dep of libwww-perl
Installing libplexus-interpolation-java as dep of libplexus-utils-java
new important dependency: os-prober
Installing os-prober as dep of grub-common
Installing install-info as dep of info
Installing python-mako as dep of gwibber
Installing python-beaker as dep of python-mako
Installing python-sqlalchemy as dep of python-beaker
Installing python-pycurl as dep of gwibber
Installing insserv as dep of sysv-rc
Installing libplexus-i18n-java as dep of libdoxia-java
new important dependency: libcommons-configuration-java
Installing libcommons-configuration-java as dep of libdoxia-java
Installing libcommons-jxpath-java as dep of libcommons-configuration-java
new important dependency: fop
Installing fop as dep of libdoxia-java
Installing libavalon-framework-java as dep of fop
Installing libbatik-java as dep of fop
Installing libcommons-io-java as dep of libbatik-java
Installing java-wrappers as dep of libbatik-java
Installing libxml-commons-external-java as dep of libbatik-java
Installing libxmlgraphics-commons-java as dep of fop
Installing libsaxon-java as dep of fop
new important dependency: libitext1-java
Installing libitext1-java as dep of libdoxia-java
Installing openjdk-6-jre as dep of openjdk-6-jdk
Installing libmagick++2 as dep of inkscape
Installing libntfs-3g54 as dep of ntfs-3g
Installing libmaven2-core-java as dep of maven2
Installing libslf4j-java as dep of libmaven2-core-java
Installing libmodello-java as dep of libmaven2-core-java
Installing libplexus-build-api-java as dep of libmodello-java
Installing libplexus-archiver-java as dep of libmaven2-core-java
Installing libplexus-io-java as dep of libplexus-archiver-java
Installing libplexus-sec-dispatcher-java as dep of libmaven2-core-java
Installing libplexus-cipher-java as dep of libplexus-sec-dispatcher-java
Installing libplexus-ant-factory-java as dep of libmaven2-core-java
Installing libplexus-bsh-factory-java as dep of libmaven2-core-java
Installing bsh as dep of libplexus-bsh-factory-java
Installing libbackport-util-concurrent-java as dep of libmaven2-core-java
new important dependency: libmaven-clean-plugin-java
Installing libmaven-clean-plugin-java as dep of maven2
Installing libmaven-file-management-java as dep of libmaven-clean-plugin-java
Installing libmaven-shared-io-java as dep of libmaven-file-management-java
new important dependency: libmaven-compiler-plugin-java
Installing libmaven-compiler-plugin-java as dep of maven2
Installing libmaven-plugin-tools-java as dep of libmaven-compiler-plugin-java
Installing libmaven-reporting-impl-java as dep of libmaven-plugin-tools-java
Installing libcommons-validator-java as dep of libmaven-reporting-impl-java
Installing libdoxia-sitetools-java as dep of libmaven-reporting-impl-java
Installing libqdox-java as dep of libmaven-plugin-tools-java
Installing libplexus-compiler-api-java as dep of libmaven-compiler-plugin-java
Installing libplexus-compiler-manager-java as dep of libmaven-compiler-plugin-java
Installing libplexus-compiler-javac-java as dep of libmaven-compiler-plugin-java
new important dependency: libmaven-install-plugin-java
Installing libmaven-install-plugin-java as dep of maven2
Installing libplexus-digest-java as dep of libmaven-install-plugin-java
new important dependency: libmaven-jar-plugin-java
Installing libmaven-jar-plugin-java as dep of maven2
Installing libmaven-archiver-java as dep of libmaven-jar-plugin-java
new important dependency: libmaven-resources-plugin-java
Installing libmaven-resources-plugin-java as dep of maven2
Installing libmaven-filtering-java as dep of libmaven-resources-plugin-java
new important dependency: libmaven-shade-plugin-java
Installing libmaven-shade-plugin-java as dep of maven2
Installing libmaven-dependency-tree-java as dep of libmaven-shade-plugin-java
Installing python-bugbuddy as dep of python-gnome2-desktop
Installing python-evince as dep of python-gnome2-desktop
Installing python-evolution as dep of python-gnome2-desktop
Installing python-gnomedesktop as dep of python-gnome2-desktop
Installing python-gnomeprint as dep of python-gnome2-desktop
Installing python-gtksourceview as dep of python-gnome2-desktop
Installing python-gtop as dep of python-gnome2-desktop
Installing python-mediaprofiles as dep of python-gnome2-desktop
Installing python-metacity as dep of python-gnome2-desktop
Installing python-nautilusburn as dep of python-gnome2-desktop
Installing python-totem-plparser as dep of python-gnome2-desktop
Installing python-wnck as dep of python-gnome2-desktop
Starting
Starting 2
Investigating sysvinit-utils
Package sysvinit-utils has broken dep on sysvconfig
  Considering sysvconfig -1 as a solution to sysvinit-utils 5141
  Added sysvconfig to the remove list
  Fixing sysvinit-utils via remove of sysvconfig
Investigating libthai0
Package libthai0 has broken dep on libdatrie0
  Considering libdatrie0 -1 as a solution to libthai0 230
  Added libdatrie0 to the remove list
  Fixing libthai0 via remove of libdatrie0
Investigating mono-runtime
Package mono-runtime has broken dep on mono-2.0-runtime
  Considering mono-2.0-runtime -1 as a solution to mono-runtime 162
  Added mono-2.0-runtime to the remove list
Package mono-runtime has broken dep on mono-common
  Considering mono-common 0 as a solution to mono-runtime 162
  Added mono-common to the remove list
Package mono-runtime has broken dep on mono-jit
  Considering mono-jit 1 as a solution to mono-runtime 162
  Added mono-jit to the remove list
  Fixing mono-runtime via remove of mono-2.0-runtime
  Fixing mono-runtime via remove of mono-common
  Fixing mono-runtime via remove of mono-jit
Investigating upstart
Package upstart has broken dep on startup-tasks
  Considering startup-tasks 2 as a solution to upstart 157
  Added startup-tasks to the remove list
Package upstart has broken dep on system-services
  Considering system-services 2 as a solution to upstart 157
  Added system-services to the remove list
Package upstart has broken dep on upstart-compat-sysv
  Considering upstart-compat-sysv 5 as a solution to upstart 157
  Added upstart-compat-sysv to the remove list
  Fixing upstart via remove of startup-tasks
  Fixing upstart via remove of system-services
  Fixing upstart via remove of upstart-compat-sysv
Investigating cups
Package cups has broken dep on cupsddk-drivers
  Considering cupsddk-drivers -1 as a solution to cups 24
  Added cupsddk-drivers to the remove list
  Fixing cups via remove of cupsddk-drivers
Investigating gnome-games-common
Package gnome-games-common has broken dep on gnome-cards-data
  Considering gnome-cards-data 3 as a solution to gnome-games-common 17
  Added gnome-cards-data to the remove list
  Fixing gnome-games-common via remove of gnome-cards-data
Investigating libgconf2.0-cil
Package libgconf2.0-cil has broken dep on libgconf2.24-cil
  Considering libgconf2.24-cil -1 as a solution to libgconf2.0-cil 8
  Added libgconf2.24-cil to the remove list
  Fixing libgconf2.0-cil via remove of libgconf2.24-cil
Investigating rsyslog
Package rsyslog has broken dep on linux-kernel-log-daemon
  Considering klogd 0 as a solution to rsyslog 8
  Considering syslog-ng 0 as a solution to rsyslog 8
  Considering socklog-run 0 as a solution to rsyslog 8
  Considering klogd 0 as a solution to rsyslog 8
  Added klogd to the remove list
  Considering inetutils-syslogd 0 as a solution to rsyslog 8
  Considering dsyslog 0 as a solution to rsyslog 8
Package rsyslog has broken dep on system-log-daemon
  Considering sysklogd 0 as a solution to rsyslog 8
  Considering syslog-ng 0 as a solution to rsyslog 8
  Considering sysklogd 0 as a solution to rsyslog 8
  Added sysklogd to the remove list
  Considering socklog-run 0 as a solution to rsyslog 8
  Considering inetutils-syslogd 0 as a solution to rsyslog 8
  Considering dsyslog 0 as a solution to rsyslog 8
  Fixing rsyslog via remove of klogd
  Fixing rsyslog via remove of sysklogd
Investigating epiphany-browser
Package epiphany-browser has broken dep on epiphany-gecko
  Considering epiphany-gecko 2 as a solution to epiphany-browser 7
  Added epiphany-gecko to the remove list
  Considering epiphany-gecko 2 as a solution to epiphany-browser 7
  Fixing epiphany-browser via remove of epiphany-gecko
Investigating libgnome-vfs2.0-cil
Package libgnome-vfs2.0-cil has broken dep on libgnome-vfs2.24-cil
  Considering libgnome-vfs2.24-cil -1 as a solution to libgnome-vfs2.0-cil 7
  Added libgnome-vfs2.24-cil to the remove list
  Fixing libgnome-vfs2.0-cil via remove of libgnome-vfs2.24-cil
Investigating libgd2-xpm
Package libgd2-xpm has broken dep on libgd2
  Considering libgd2-noxpm 5 as a solution to libgd2-xpm 6
  Added libgd2-noxpm to the remove list
Package libgd2-xpm has broken dep on libgd2-noxpm
  Considering libgd2-noxpm 5 as a solution to libgd2-xpm 6
  Added libgd2-noxpm to the remove list
  Fixing libgd2-xpm via remove of libgd2-noxpm
  Fixing libgd2-xpm via remove of libgd2-noxpm
Investigating foomatic-db
Package foomatic-db has broken dep on foomatic-db-hpijs
  Considering foomatic-db-hpijs -1 as a solution to foomatic-db 6
  Added foomatic-db-hpijs to the remove list
  Fixing foomatic-db via remove of foomatic-db-hpijs
Investigating gdm
Package gdm has broken dep on fast-user-switch-applet
  Considering fast-user-switch-applet -1 as a solution to gdm 5
  Added fast-user-switch-applet to the remove list
  Fixing gdm via remove of fast-user-switch-applet
Investigating libart2.0-cil
Package libart2.0-cil has broken dep on libart2.24-cil
  Considering libart2.24-cil -1 as a solution to libart2.0-cil 4
  Added libart2.24-cil to the remove list
  Fixing libart2.0-cil via remove of libart2.24-cil
Investigating eclipse-rcp-gcj
Package eclipse-rcp-gcj has broken dep on eclipse-rcp
  Considering eclipse-rcp 10 as a solution to eclipse-rcp-gcj 4
  Removing eclipse-rcp-gcj rather than change eclipse-rcp
Investigating mobile-broadband-provider-info
Package mobile-broadband-provider-info has broken dep on libmbca0
  Considering libmbca0 -2 as a solution to mobile-broadband-provider-info 3
  Added libmbca0 to the remove list
  Fixing mobile-broadband-provider-info via remove of libmbca0
Investigating libempathy30
Package libempathy30 has broken dep on libempathy-common
  Considering libempathy-common 1 as a solution to libempathy30 3
  Holding Back libempathy30 rather than change libempathy-common
Investigating upstart-logd
Package upstart-logd has broken dep on upstart
  Considering upstart 157 as a solution to upstart-logd 2
  Removing upstart-logd rather than change upstart
Investigating libempathy-gtk28
Package libempathy-gtk28 has broken dep on libempathy30
  Considering libempathy30 3 as a solution to libempathy-gtk28 1
  Holding Back libempathy-gtk28 rather than change libempathy30
Investigating eclipse-platform-gcj
Package eclipse-platform-gcj has broken dep on eclipse-platform
  Considering eclipse-platform 11 as a solution to eclipse-platform-gcj 1
  Removing eclipse-platform-gcj rather than change eclipse-platform
Investigating libgnomekbd3
Package libgnomekbd3 has broken dep on libgnomekbd-common
  Considering libgnomekbd-common 6 as a solution to libgnomekbd3 1
  Removing libgnomekbd3 rather than change libgnomekbd-common
Investigating eclipse-jdt-gcj
Package eclipse-jdt-gcj has broken dep on eclipse-jdt
  Considering eclipse-jdt 6 as a solution to eclipse-jdt-gcj 1
  Removing eclipse-jdt-gcj rather than change eclipse-jdt
Investigating eclipse-pde-gcj
Package eclipse-pde-gcj has broken dep on eclipse-pde
  Considering eclipse-pde 3 as a solution to eclipse-pde-gcj 1
  Removing eclipse-pde-gcj rather than change eclipse-pde
Investigating gnome-mahjongg
Package gnome-mahjongg has broken dep on gnome-games-data
  Considering gnome-games-data -1 as a solution to gnome-mahjongg 0
  Added gnome-games-data to the remove list
  Fixing gnome-mahjongg via remove of gnome-games-data
Investigating gstreamer0.10-plugins-bad
Package gstreamer0.10-plugins-bad has broken dep on gstreamer0.10-schroedinger
  Considering gstreamer0.10-schroedinger -1 as a solution to gstreamer0.10-plugins-bad 0
  Added gstreamer0.10-schroedinger to the remove list
  Fixing gstreamer0.10-plugins-bad via remove of gstreamer0.10-schroedinger
Investigating sreadahead
Package sreadahead has broken dep on readahead
  Considering readahead -1 as a solution to sreadahead 0
  Added readahead to the remove list
  Fixing sreadahead via remove of readahead
Investigating libpt2.6.4-plugins
Package libpt2.6.4-plugins has broken dep on libpt2.6.1-plugins-alsa
  Considering libpt2.6.1-plugins-alsa -1 as a solution to libpt2.6.4-plugins 0
  Added libpt2.6.1-plugins-alsa to the remove list
Package libpt2.6.4-plugins has broken dep on libpt2.6.1-plugins-v4l2
  Considering libpt2.6.1-plugins-v4l2 -1 as a solution to libpt2.6.4-plugins 0
  Added libpt2.6.1-plugins-v4l2 to the remove list
  Fixing libpt2.6.4-plugins via remove of libpt2.6.1-plugins-alsa
  Fixing libpt2.6.4-plugins via remove of libpt2.6.1-plugins-v4l2
Investigating indicator-session
Package indicator-session has broken dep on libempathy30
  Considering libempathy30 3 as a solution to indicator-session 0
  Holding Back indicator-session rather than change libempathy30
Investigating libphysfs1
Package libphysfs1 has broken dep on libphysfs-1.0-0
  Considering libphysfs-1.0-0 0 as a solution to libphysfs1 0
  Holding Back libphysfs1 rather than change libphysfs-1.0-0
Investigating libgnomekbdui3
Package libgnomekbdui3 has broken dep on libgnomekbd3
  Considering libgnomekbd3 1 as a solution to libgnomekbdui3 -1
  Removing libgnomekbdui3 rather than change libgnomekbd3
Investigating eclipse-gcj
Package eclipse-gcj has broken dep on eclipse-jdt-gcj
  Considering eclipse-jdt-gcj 1 as a solution to eclipse-gcj -1
  Removing eclipse-gcj rather than change eclipse-jdt-gcj
Investigating empathy
Package empathy has broken dep on libempathy-gtk28
  Considering libempathy-gtk28 1 as a solution to empathy -1
  Holding Back empathy rather than change libempathy-gtk28
Investigating librpm4.4
Package librpm4.4 has broken dep on librpm0
  Considering librpm0 1 as a solution to librpm4.4 -1
  Removing librpm4.4 rather than change librpm0
Investigating eclipse-source
Package eclipse-source has broken dep on eclipse-platform
  Considering eclipse-platform 11 as a solution to eclipse-source -1
  Removing eclipse-source rather than change eclipse-platform
Investigating libplib1
Package libplib1 has broken dep on plib1.8.4c2
  Considering plib1.8.4c2 -2 as a solution to libplib1 -1
  Added plib1.8.4c2 to the remove list
  Fixing libplib1 via remove of plib1.8.4c2
Investigating libgdl-1-0
Package libgdl-1-0 has broken dep on libgdl-1-common
  Considering libgdl-1-common 3 as a solution to libgdl-1-0 -1
  Removing libgdl-1-0 rather than change libgdl-1-common
Investigating supertux
Package supertux has broken dep on libphysfs1
  Considering libphysfs1 0 as a solution to supertux 0
  Holding Back supertux rather than change libphysfs1
Investigating indicator-applet-session
Package indicator-applet-session has broken dep on indicator-session
  Considering indicator-session 0 as a solution to indicator-applet-session 0
  Holding Back indicator-applet-session rather than change indicator-session
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on indicator-applet-session
  Considering indicator-applet-session 0 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change indicator-applet-session
 Try to Re-Instate supertux
Done
Installing indicator-applet-session as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing indicator-session as dep of indicator-applet-session
Installing libempathy30 as dep of indicator-session
new important dependency: empathy
Installing empathy as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing libempathy-gtk28 as dep of empathy
new important dependency: gnome-bluetooth
Installing gnome-bluetooth as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Starting
Starting 2
Investigating libempathy30
Package libempathy30 has broken dep on libempathy-common
  Considering libempathy-common 1 as a solution to libempathy30 3
  Holding Back libempathy30 rather than change libempathy-common
Investigating libempathy-gtk28
Package libempathy-gtk28 has broken dep on libempathy30
  Considering libempathy30 3 as a solution to libempathy-gtk28 1
  Holding Back libempathy-gtk28 rather than change libempathy30
Investigating indicator-session
Package indicator-session has broken dep on libempathy30
  Considering libempathy30 3 as a solution to indicator-session 0
  Holding Back indicator-session rather than change libempathy30
Investigating empathy
Package empathy has broken dep on libempathy-gtk28
  Considering libempathy-gtk28 1 as a solution to empathy -1
  Holding Back empathy rather than change libempathy-gtk28
Investigating indicator-applet-session
Package indicator-applet-session has broken dep on indicator-session
  Considering indicator-session 0 as a solution to indicator-applet-session 0
  Holding Back indicator-applet-session rather than change indicator-session
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on indicator-applet-session
  Considering indicator-applet-session 0 as a solution to ubuntu-desktop 10000
    Reinst Failed early because of libempathy-common
    Reinst Failed because of libempathy30
    Reinst Failed because of indicator-session
Done
Log time: 2009-10-29 20:55:38.955207

---

