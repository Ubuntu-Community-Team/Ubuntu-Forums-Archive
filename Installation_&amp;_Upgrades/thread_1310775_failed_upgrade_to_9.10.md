---
title: "failed upgrade to 9.10"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by ffxigotenks on 2009-11-02
I've been working on upgrading to 9.10 and I'm getting the following error

```
Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.
```

in a dialog box, and I've tried fixing broken packages and running "sudo apt-get install -f" and getting nothing new, any ideas on why this is happening and what I can do?

---

### Post by zey on 2009-11-02
i recommend you to do a fresh install ubuntu 9.10

---

### Post by ffxigotenks on 2009-11-09
I tried to do a fresh install and was having some issues with wine, I'd like to try to upgrade from 9.04 again, but I'm still getting this error even after doing a fresh install of 9.04, here are my files

apt.log
```

Log time: 2009-11-08 18:01:45.332819
Log time: 2009-11-08 18:01:47.760528
Log time: 2009-11-08 18:02:12.837340
Installing console-setup as dep of xserver-xorg
Installing libglib2.0-cil as dep of libmono-addins-gui0.2-cil
Installing libgtk2.0-cil as dep of libmono-addins-gui0.2-cil
Installing libmono-posix2.0-cil as dep of libmono-addins-gui0.2-cil
Installing libc6 as dep of libmono-posix2.0-cil
Installing libc-bin as dep of libc6
Installing libmono-system2.0-cil as dep of libmono-posix2.0-cil
Installing mono-runtime as dep of libmono-system2.0-cil
Installing mono-gac as dep of mono-runtime
Installing mono-2.0-gac as dep of mono-gac
Installing libsgutils2-2 as dep of sg3-utils
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
Installing libselinux1 as dep of libglib2.0-0
Installing gcc-4.3-base as dep of libstdc++6-4.3-dev
Installing g++-4.3 as dep of libstdc++6-4.3-dev
Installing gcc-4.3 as dep of g++-4.3
Installing cpp-4.3 as dep of gcc-4.3
Installing libgcc1 as dep of gcc-4.3
Installing gcc-4.4-base as dep of libgcc1
Installing libgomp1 as dep of gcc-4.3
Installing libstdc++6 as dep of libstdc++6-4.3-dev
Installing libflickrnet2.2-cil as dep of f-spot
Installing libgconf2.0-cil as dep of f-spot
Installing libglade2.0-cil as dep of f-spot
Installing libgnome-keyring1.0-cil as dep of f-spot
Installing libgnome-vfs2.0-cil as dep of f-spot
Installing libgphoto2-2 as dep of f-spot
Installing libgphoto2-port0 as dep of libgphoto2-2
Installing libmono-cairo2.0-cil as dep of f-spot
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
Installing hal as dep of gdm
Installing libblkid1 as dep of hal
Installing dbus as dep of hal
Installing libbsd0 as dep of libedit2
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libbluetooth3 as dep of bluez-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdirectfb-1.2-0 as dep of libsdl1.2debian-alsa
Installing libiec61883-0 as dep of libfreebob0
Installing libraw1394-11 as dep of libiec61883-0
Installing libsm6 as dep of libsm-dev
Installing libgstfarsight0.10-0 as dep of libpurple0
Installing libgssdp-1.0-1 as dep of libgstfarsight0.10-0
Installing libgupnp-1.0-2 as dep of libgstfarsight0.10-0
Installing libsoup2.4-1 as dep of libgupnp-1.0-2
Installing libgupnp-igd-1.0-2 as dep of libgstfarsight0.10-0
Installing libnice0 as dep of libgstfarsight0.10-0
Installing gstreamer0.10-plugins-good as dep of libgstfarsight0.10-0
Installing libsoup-gnome2.4-1 as dep of gstreamer0.10-plugins-good
Installing libsqlite3-0 as dep of libsoup-gnome2.4-1
Installing libtag1c2a as dep of gstreamer0.10-plugins-good
Installing libtag1-vanilla as dep of libtag1c2a
Installing gstreamer0.10-nice as dep of libgstfarsight0.10-0
Installing libsilcclient-1.1-3 as dep of libpurple0
Installing libzephyr4 as dep of libpurple0
Installing perl as dep of libpurple0
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing tsconf as dep of libts-0.0-0
Installing libavutil49 as dep of libswscale0
Installing python-twisted-bin as dep of python-twisted-core
Installing libattr1 as dep of libattr1-dev
Installing libbz2-1.0 as dep of bzip2
Installing libedataserver1.2-11 as dep of evolution-webcal
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
Installing libebook1.2-9 as dep of ekiga
Installing libcamel1.2-14 as dep of libebook1.2-9
Installing libopal3.6.4 as dep of ekiga
Installing libpt2.6.4 as dep of libopal3.6.4
Installing libpt2.6.4-plugins as dep of ekiga
Installing computer-janitor as dep of computer-janitor-gtk
Installing openoffice.org-core as dep of openoffice.org-gnome
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
Installing ure as dep of openoffice.org-core
Installing uno-libs3 as dep of ure
Installing libqtcore4 as dep of libqca2
Installing libqtgui4 as dep of libqt4-opengl
Installing libio-compress-perl as dep of libio-compress-zlib-perl
Installing libcompress-raw-zlib-perl as dep of libio-compress-perl
Installing libcompress-raw-bzip2-perl as dep of libio-compress-perl
Installing libavutil-extra-49 as dep of libavutil-unstripped-49
Installing xserver-xorg-core as dep of xserver-xorg-input-evdev
Installing libice6 as dep of libice-dev
Installing libcolamd2.7.1 as dep of lp-solve
Installing compiz-core as dep of libcompizconfig0
Installing libstartup-notification0 as dep of compiz-core
Installing libxcb-atom1 as dep of libstartup-notification0
Installing libxcb-aux0 as dep of libstartup-notification0
Installing libxcb-event1 as dep of libstartup-notification0
Installing compiz-wrapper as dep of compiz-core
previously satisfied important dependency on compiz-plugins
Installing compiz-plugins as dep of compiz-core
Installing update-manager-core as dep of update-manager
new important dependency: libpam-modules
Installing libpam-modules as dep of update-manager-core
Installing base-files as dep of libpam-modules
Installing libbeagle1 as dep of python-beagle
Installing openoffice.org-base-core as dep of openoffice.org-writer
Installing libaspell15 as dep of libaspell-dev
Installing python-gobject as dep of python-gnome2
Installing python-gconf as dep of python-gnome2
Installing libmono-i18n-west2.0-cil as dep of libmono-i18n2.0-cil
Installing libpulse-mainloop-glib0 as dep of gnome-media
Installing libpulse0 as dep of libpulse-mainloop-glib0
Installing gnome-media-common as dep of gnome-media
Installing metacity-common as dep of metacity
Installing libexempi3 as dep of nautilus
Installing libgnome-desktop-2-11 as dep of nautilus
Installing nautilus-data as dep of nautilus
Installing libgnome2-common as dep of libgnome2-0
Installing system-config-printer-udev as dep of hal-cups-utils
Installing python-cups as dep of system-config-printer-udev
Installing libbind9-50 as dep of bind9-host
Installing libdns50 as dep of libbind9-50
Installing libisc50 as dep of libdns50
Installing libisccfg50 as dep of libbind9-50
Installing libisccc50 as dep of libisccfg50
Installing liblwres50 as dep of bind9-host
Installing libjson-glib-1.0-0 as dep of pidgin-facebookchat
Installing gimp-help-common as dep of gimp-help-en
Installing openoffice.org-draw as dep of openoffice.org-impress
Installing libindicate-gtk1 as dep of pidgin-libnotify
Installing libindicate3 as dep of libindicate-gtk1
Installing pidgin as dep of pidgin-libnotify
Installing pidgin-data as dep of pidgin
Installing language-pack-en as dep of language-pack-en-base
Installing libgamin0 as dep of gamin
Installing gvfs as dep of gvfs-fuse
Installing libgdu0 as dep of gvfs
Installing devicekit-disks as dep of gvfs
Installing libatasmart4 as dep of devicekit-disks
Installing libgudev-1.0-0 as dep of devicekit-disks
Installing libparted1.8-12 as dep of devicekit-disks
Installing libuuid1 as dep of libparted1.8-12
Installing linux-headers-2.6.31-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.31-14 as dep of linux-headers-2.6.31-14-generic
Installing dhcp3-common as dep of dhcp3-client
Installing libuniconf4.6 as dep of wvdial
Installing libwvstreams4.6-base as dep of libuniconf4.6
Installing libwvstreams4.6-extras as dep of libuniconf4.6
Installing xsane-common as dep of xsane
Installing libgsf-1-114 as dep of tracker
Installing libgsf-1-common as dep of libgsf-1-114
Installing libtotem-plparser12 as dep of tracker
Installing libgmime-2.4-2 as dep of libtotem-plparser12
Installing libaudiofile0 as dep of libaudiofile-dev
Installing libaudio2 as dep of libaudio-dev
Installing libxine1-bin as dep of libxine1-x
Installing libsnmp-base as dep of libsnmp15
Installing libdjvulibre-text as dep of libdjvulibre21
Installing libmagickcore2 as dep of obex-data-server
Installing libmagickwand2 as dep of libmagickcore2
Installing libgnomekbd4 as dep of gnome-settings-daemon
Installing libgnomekbd-common as dep of libgnomekbd4
Installing evolution as dep of evolution-indicator
Installing libebackend1.2-0 as dep of evolution
Installing libecal1.2-7 as dep of evolution
Installing libedataserverui1.2-8 as dep of evolution
Installing libegroupwise1.2-13 as dep of evolution
Installing libexchange-storage1.2-3 as dep of evolution
Installing libgdata-google1.2-1 as dep of evolution
Installing libgdata1.2-1 as dep of libgdata-google1.2-1
Installing libgweather1 as dep of evolution
Installing evolution-data-server as dep of evolution
Installing libedata-book1.2-2 as dep of evolution-data-server
Installing libedata-cal1.2-6 as dep of evolution-data-server
Installing evolution-data-server-common as dep of evolution-data-server
previously satisfied important dependency on evolution-documentation
Installing evolution-documentation-en as dep of evolution
Installing samba-common as dep of smbclient
new important dependency: samba-common-bin
Installing samba-common-bin as dep of samba-common
Installing libreadline6 as dep of samba-common-bin
Installing libwbclient0 as dep of samba-common-bin
Installing libnewt0.52 as dep of whiptail
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
Installing libjs-jquery as dep of libgda-4.0-common
Installing libgucharmap7 as dep of gucharmap
Installing libatspi1.0-0 as dep of brltty-x11
Installing brltty as dep of brltty-x11
Installing libjasper1 as dep of libjasper-dev
Installing libavahi-core6 as dep of avahi-daemon
Installing aisleriot as dep of gnome-games
Installing libcanberra-gtk0 as dep of aisleriot
Installing libcanberra0 as dep of libcanberra-gtk0
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
new important dependency: libcanberra-pulse
Installing libcanberra-pulse as dep of gnome-session-canberra
Installing gdebi-core as dep of gdebi
Installing pulseaudio-module-udev as dep of pulseaudio
Installing libtrackerclient0 as dep of tracker-utils
Installing dpkg as dep of comerr-dev
Installing cups-ppdc as dep of cupsddk
Installing libcupsppdc1 as dep of cups-ppdc
Installing libsub-name-perl as dep of libclass-accessor-perl
Installing devicekit-power as dep of gnome-power-manager
Installing libpcre3 as dep of libpcre3-dev
Installing libpcrecpp0 as dep of libpcre3-dev
Installing libavcodec52 as dep of libdlna0
Installing libgsm1 as dep of libavcodec52
Installing libwxbase2.8-0 as dep of libwxgtk2.8-0
Installing totem as dep of totem-plugins
Installing gstreamer0.10-plugins-base as dep of totem
Installing libtheora0 as dep of gstreamer0.10-plugins-base
Installing totem-common as dep of totem
new important dependency: totem-mozilla
Installing totem-mozilla as dep of totem
Installing libgdata5 as dep of totem-plugins
Installing libgdata-common as dep of libgdata5
Installing kdelibs5 as dep of kdebase-runtime
Installing liblzma0 as dep of kdelibs5
Installing libqt4-dbus as dep of kdelibs5
Installing libqt4-xml as dep of libqt4-dbus
Installing libqt4-designer as dep of kdelibs5
Installing libqt4-script as dep of libqt4-designer
Installing libqt4-network as dep of kdelibs5
Installing libqt4-phonon as dep of kdelibs5
Installing libqt4-qt3support as dep of kdelibs5
Installing libqt4-sql as dep of libqt4-qt3support
Installing libqt4-svg as dep of kdelibs5
Installing libsoprano4 as dep of kdelibs5
Installing soprano-daemon as dep of libsoprano4
Installing libstreamanalyzer0 as dep of kdelibs5
Installing libstreams0 as dep of libstreamanalyzer0
Installing kdelibs5-data as dep of kdelibs5
Installing kdelibs-bin as dep of kdelibs5
Installing libknotificationitem1 as dep of kdebase-runtime
Installing libplasma3 as dep of kdebase-runtime
Installing libqt4-webkit as dep of libplasma3
Installing kdebase-runtime-bin-kde4 as dep of kdebase-runtime
Installing kdebase-runtime-data as dep of kdebase-runtime
Installing linux-image-2.6.31-14-generic as dep of linux-image-generic
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing libgnome-menu2 as dep of gnome-screensaver
Installing libgnomekbdui4 as dep of gnome-screensaver
Installing media-player-info as dep of rhythmbox
Installing libx264-67 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libcelt0 as dep of libjack0
Installing libffado1 as dep of libjack0
Installing libglibmm-2.4-1c2a as dep of libffado1
new important dependency: libmono-i18n-west1.0-cil
Installing libmono-i18n-west1.0-cil as dep of libmono-corlib1.0-cil
Installing python-gmenu as dep of alacarte
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing hplip as dep of hpijs
Installing hplip-data as dep of hplip
Installing liblualib50 as dep of liblualib50-dev
previously satisfied important dependency on virtualbox-ose-source
Installing virtualbox-ose-source as dep of virtualbox-ose
new important dependency: virtualbox-ose-qt
Installing virtualbox-ose-qt as dep of virtualbox-ose
Installing libcupsimage2 as dep of cups-client
Installing cups-common as dep of cups-client
Installing apt as dep of apt-transport-https
Installing mysql-client-5.0 as dep of mysql-server-5.0
Installing libmysqlclient15off as dep of mysql-client-5.0
Installing mysql-server-core-5.0 as dep of mysql-server-5.0
Installing mplayer-nogui as dep of mplayer
Installing libmono-data-tds1.0-cil as dep of libmono-data1.0-cil
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
new important dependency: byobu
Installing byobu as dep of screen
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing capplets-data as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing gnome-audio as dep of timer-applet
Installing libxi6 as dep of libxi-dev
Installing gconf2-common as dep of gconf2
Installing esound-common as dep of libesd-alsa0
Installing libxrender1 as dep of libxrender-dev
Installing libcryptui0 as dep of seahorse
Installing libept0 as dep of aptitude
Installing apt-utils as dep of python-apt
Installing libscim8c2a as dep of scim-modules-socket
Installing libtelepathy-glib0 as dep of vinagre
Installing libvte9 as dep of vinagre
Installing libsvn1 as dep of subversion
Installing libaprutil1 as dep of libsvn1
Installing apache2.2-bin as dep of apache2.2-common
Installing libaprutil1-dbd-sqlite3 as dep of apache2.2-bin
Installing libaprutil1-ldap as dep of apache2.2-bin
new important dependency: libaccess-bridge-java-jni
Installing libaccess-bridge-java-jni as dep of libaccess-bridge-java
new important dependency: scim-gtk2-immodule
Installing scim-gtk2-immodule as dep of scim
Installing libart2.0-cil as dep of libgnome2.24-cil
Installing libkadm5srv6 as dep of libkrb5-dev
Installing libgssrpc4 as dep of libkadm5srv6
Installing libkdb5-4 as dep of libkadm5srv6
Installing openjdk-6-jre-headless as dep of icedtea-6-jre-cacao
Installing openjdk-6-jre-lib as dep of openjdk-6-jre-headless
new important dependency: apport-symptoms
Installing apport-symptoms as dep of apport
Installing libavahi-client3 as dep of libavahi-client-dev
Installing libogg0 as dep of libogg-dev
Installing python2.5-minimal as dep of python2.5
Installing libavcodec-extra-52 as dep of libavcodec-unstripped-52
Installing libdirac0c2a as dep of libavcodec-extra-52
Installing libopenjpeg2 as dep of libavcodec-extra-52
Installing libgutenprint2 as dep of cups-driver-gutenprint
Installing ghostscript-cups as dep of cups-driver-gutenprint
Installing ghostscript as dep of ghostscript-cups
Installing libgs8 as dep of ghostscript
Installing gnome-terminal-data as dep of gnome-terminal
Installing libqt3-headers as dep of libqt3-compat-headers
Installing e2fslibs as dep of e2fsprogs
Installing libpng12-0 as dep of libpng12-dev
Installing libpolkit-gtk-1-0 as dep of gnome-system-tools
Installing nvidia-185-modaliases as dep of nvidia-180-modaliases
new important dependency: bcmwl-modaliases
Installing bcmwl-modaliases as dep of jockey-common
new important dependency: libltdl-dev
Installing libltdl-dev as dep of libtool
Installing libltdl7 as dep of libltdl-dev
Installing liboil0.3 as dep of libschroedinger-1.0-0
new important dependency: notify-osd-icons
Installing notify-osd-icons as dep of notify-osd
Installing libvlccore2 as dep of libvlc2
Installing vlc-data as dep of libvlccore2
Installing humanity-icon-theme as dep of human-theme
Installing liblua50 as dep of liblua50-dev
Installing libxcursor1 as dep of libxcursor-dev
Installing libdbusmenu-glib0 as dep of indicator-messages
Installing libdbusmenu-gtk0 as dep of indicator-messages
Installing python-speechd as dep of gnome-orca
Installing speech-dispatcher as dep of python-speechd
Installing libdotconf1.0 as dep of speech-dispatcher
Installing libspeechd2 as dep of speech-dispatcher
new important dependency: python-louis
Installing python-louis as dep of gnome-orca
Installing liblouis0 as dep of python-louis
Installing liblouis-data as dep of liblouis0
Installing at-spi as dep of python-pyatspi
Installing firefox-3.5 as dep of firefox
Installing firefox-3.5-branding as dep of firefox-3.5
Installing ubufox as dep of firefox-3.5
Installing libavahi-qt3-1 as dep of libavahi-qt3-dev
Installing cpp-4.4 as dep of cpp
Installing libthai0 as dep of libpango1.0-0
Installing libdatrie1 as dep of libthai0
Installing libthai-data as dep of libthai0
Installing xserver-xorg-input-vmmouse as dep of xserver-xorg-input-all
Installing libass3 as dep of vlc-nox
Installing libdvbpsi5 as dep of vlc-nox
Installing gcc-4.4 as dep of gcc
Installing binutils as dep of gcc-4.4
Installing libqt3-mt as dep of libqt3-mt-dev
Installing python-gtk2 as dep of python-glade2
Installing libssl0.9.8 as dep of libssl-dev
Installing language-selector-common as dep of language-selector
Installing libxmu6 as dep of libxmu-dev
Installing mysql-server-5.1 as dep of mysql-server
Installing mysql-client-5.1 as dep of mysql-server-5.1
Installing mysql-server-core-5.1 as dep of mysql-server-5.1
Installing libpango-perl as dep of libgtk2-perl
Installing libxext6 as dep of libxext-dev
Installing libxapian15 as dep of python-xapian
Installing libjpeg62 as dep of libjpeg62-dev
new important dependency: libavcodec52
Installing libavcodec52 as dep of ubuntu-restricted-extras
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
new important dependency: libmp4v2-0
Installing libmp4v2-0 as dep of ubuntu-restricted-extras
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing libgtkmm-2.4-1c2a as dep of gnome-system-monitor
Installing libavdevice52 as dep of ffmpeg
Installing libavfilter0 as dep of ffmpeg
Installing rsyslog as dep of ubuntu-minimal
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Sections)
Installing libcupscgi1 as dep of cups
Installing libcupsdriver1 as dep of cups
Installing libcupsmime1 as dep of cups
Installing libpoppler5 as dep of cups
Installing poppler-utils as dep of cups
Installing libbonobo2-common as dep of libbonobo2-0
Installing zlib1g as dep of zlib1g-dev
Installing libmagic1 as dep of file
Installing libtiff4 as dep of libtiff4-dev
Installing libtiffxx0c2 as dep of libtiff4-dev
Installing libfreetype6 as dep of libfreetype6-dev
Installing apturl-common as dep of apturl
Installing libpst4 as dep of evolution-plugins
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
Installing libgl1-mesa-glx as dep of libgl1-mesa-dev
Installing libsepol1 as dep of sysvinit-utils
Installing libxrandr2 as dep of libxrandr-dev
Installing libdrm-radeon1 as dep of libgl1-mesa-dri
Installing libjline-java as dep of rhino
Installing libc-dev-bin as dep of libc6-dev
Installing gnome-applets-data as dep of gnome-applets
new important dependency: python-gnomeapplet
Installing python-gnomeapplet as dep of gnome-applets
Installing xorg-docs-core as dep of xorg
Installing gconf-defaults-service as dep of gconf-editor
Installing php5-common as dep of php5-mysql
Installing gnome-panel-data as dep of gnome-panel
new important dependency: libcompress-bzip2-perl
Installing libcompress-bzip2-perl as dep of libwww-perl
new important dependency: os-prober
Installing os-prober as dep of grub-common
Installing install-info as dep of info
Installing python-launchpadlib as dep of python-apport
Installing python-wadllib as dep of python-launchpadlib
Installing python-simplejson as dep of python-wadllib
Installing python-lazr-uri as dep of python-wadllib
Installing python-httplib2 as dep of python-launchpadlib
Installing python-lazr-restfulclient as dep of python-launchpadlib
Installing python-oauth as dep of python-launchpadlib
Installing insserv as dep of sysv-rc
Installing libmng1 as dep of libmng-dev
Installing libavahi-common3 as dep of libavahi-common-dev
Installing python-bugbuddy as dep of python-gnome2-desktop
Installing python-evince as dep of python-gnome2-desktop
Installing python-evolution as dep of python-gnome2-desktop
Installing python-gnomedesktop as dep of python-gnome2-desktop
Installing python-gnomekeyring as dep of python-gnome2-desktop
Installing python-gnomeprint as dep of python-gnome2-desktop
Installing python-gtksourceview as dep of python-gnome2-desktop
Installing python-gtop as dep of python-gnome2-desktop
Installing python-mediaprofiles as dep of python-gnome2-desktop
Installing python-metacity as dep of python-gnome2-desktop
Installing python-nautilusburn as dep of python-gnome2-desktop
Installing python-rsvg as dep of python-gnome2-desktop
Installing python-totem-plparser as dep of python-gnome2-desktop
Installing python-wnck as dep of python-gnome2-desktop
new important dependency: svn
Installing libntfs-3g54 as dep of ntfs-3g
Installing usb-creator-gtk as dep of usb-creator
Installing usb-creator-common as dep of usb-creator-gtk
Installing libevent-1.4-2 as dep of transmission-gtk
Starting
Starting 2
Investigating mono-runtime
Package mono-runtime has broken dep on mono-2.0-runtime
  Considering mono-2.0-runtime -1 as a solution to mono-runtime 207
  Added mono-2.0-runtime to the remove list
Package mono-runtime has broken dep on mono-common
  Considering mono-common 0 as a solution to mono-runtime 207
  Added mono-common to the remove list
Package mono-runtime has broken dep on mono-jit
  Considering mono-jit 1 as a solution to mono-runtime 207
  Added mono-jit to the remove list
  Fixing mono-runtime via remove of mono-2.0-runtime
  Fixing mono-runtime via remove of mono-common
  Fixing mono-runtime via remove of mono-jit
Investigating libthai0
Package libthai0 has broken dep on libdatrie0
  Considering libdatrie0 -1 as a solution to libthai0 190
  Added libdatrie0 to the remove list
  Fixing libthai0 via remove of libdatrie0
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
Investigating libavcodec-extra-52
Package libavcodec-extra-52 has broken dep on libavcodec52
  Considering libavcodec52 50 as a solution to libavcodec-extra-52 51
  Added libavcodec52 to the remove list
  Fixing libavcodec-extra-52 via keep of libavcodec52
Investigating cups
Package cups has broken dep on cupsddk-drivers
  Considering cupsddk-drivers -1 as a solution to cups 20
  Added cupsddk-drivers to the remove list
  Fixing cups via remove of cupsddk-drivers
Investigating gnome-games-common
Package gnome-games-common has broken dep on gnome-cards-data
  Considering gnome-cards-data 3 as a solution to gnome-games-common 17
  Added gnome-cards-data to the remove list
  Fixing gnome-games-common via remove of gnome-cards-data
Investigating libtag1c2a
Package libtag1c2a has broken dep on libtag-extras0
  Considering libtag-extras0 -1 as a solution to libtag1c2a 11
  Added libtag-extras0 to the remove list
  Fixing libtag1c2a via remove of libtag-extras0
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
Investigating libgconf2.0-cil
Package libgconf2.0-cil has broken dep on libgconf2.24-cil
  Considering libgconf2.24-cil -1 as a solution to libgconf2.0-cil 5
  Added libgconf2.24-cil to the remove list
  Fixing libgconf2.0-cil via remove of libgconf2.24-cil
Investigating foomatic-db
Package foomatic-db has broken dep on foomatic-db-hpijs
  Considering foomatic-db-hpijs -1 as a solution to foomatic-db 4
  Added foomatic-db-hpijs to the remove list
  Fixing foomatic-db via remove of foomatic-db-hpijs
Investigating libgnome-vfs2.0-cil
Package libgnome-vfs2.0-cil has broken dep on libgnome-vfs2.24-cil
  Considering libgnome-vfs2.24-cil -1 as a solution to libgnome-vfs2.0-cil 4
  Added libgnome-vfs2.24-cil to the remove list
  Fixing libgnome-vfs2.0-cil via remove of libgnome-vfs2.24-cil
Investigating libart2.0-cil
Package libart2.0-cil has broken dep on libart2.24-cil
  Considering libart2.24-cil -1 as a solution to libart2.0-cil 3
  Added libart2.24-cil to the remove list
  Fixing libart2.0-cil via remove of libart2.24-cil
Investigating gdm
Package gdm has broken dep on fast-user-switch-applet
  Considering fast-user-switch-applet 9999 as a solution to gdm 3
  Holding Back gdm rather than change fast-user-switch-applet
Investigating mobile-broadband-provider-info
Package mobile-broadband-provider-info has broken dep on libmbca0
  Considering libmbca0 -2 as a solution to mobile-broadband-provider-info 2
  Added libmbca0 to the remove list
  Fixing mobile-broadband-provider-info via remove of libmbca0
Investigating upstart-logd
Package upstart-logd has broken dep on upstart
  Considering upstart 157 as a solution to upstart-logd 2
  Removing upstart-logd rather than change upstart
Investigating libgnomekbd3
Package libgnomekbd3 has broken dep on libgnomekbd-common
  Considering libgnomekbd-common 6 as a solution to libgnomekbd3 1
  Removing libgnomekbd3 rather than change libgnomekbd-common
Investigating usplash
Package usplash has broken dep on gdm
  Considering gdm 3 as a solution to usplash 1
  Holding Back usplash rather than change gdm
Investigating aisleriot
Package aisleriot has broken dep on gnome-games-data
  Considering gnome-games-data -1 as a solution to aisleriot 0
  Added gnome-games-data to the remove list
  Fixing aisleriot via remove of gnome-games-data
Investigating mysql-server-5.1
Package mysql-server-5.1 has broken dep on mysql-server-5.0
  Considering mysql-server-5.0 0 as a solution to mysql-server-5.1 0
  Holding Back mysql-server-5.1 rather than change mysql-server-5.0
Investigating mysql-client-5.1
Package mysql-client-5.1 has broken dep on mysql-client-5.0
  Considering mysql-client-5.0 1 as a solution to mysql-client-5.1 0
  Holding Back mysql-client-5.1 rather than change mysql-client-5.0
Investigating mysql-server-core-5.1
Package mysql-server-core-5.1 has broken dep on mysql-server-core-5.0
  Considering mysql-server-core-5.0 1 as a solution to mysql-server-core-5.1 0
  Holding Back mysql-server-core-5.1 rather than change mysql-server-core-5.0
Investigating mysql-server
Package mysql-server has broken dep on mysql-server-5.1
  Considering mysql-server-5.1 0 as a solution to mysql-server 0
  Holding Back mysql-server rather than change mysql-server-5.1
Investigating libpt2.6.4-plugins
Package libpt2.6.4-plugins has broken dep on libpt2.6.1-plugins-alsa
  Considering libpt2.6.1-plugins-alsa -1 as a solution to libpt2.6.4-plugins 0
  Added libpt2.6.1-plugins-alsa to the remove list
Package libpt2.6.4-plugins has broken dep on libpt2.6.1-plugins-v4l2
  Considering libpt2.6.1-plugins-v4l2 -1 as a solution to libpt2.6.4-plugins 0
  Added libpt2.6.1-plugins-v4l2 to the remove list
  Fixing libpt2.6.4-plugins via remove of libpt2.6.1-plugins-alsa
  Fixing libpt2.6.4-plugins via remove of libpt2.6.1-plugins-v4l2
Investigating libuniconf4.6
Package libuniconf4.6 has broken dep on libuniconf4.4
  Considering libuniconf4.4 -1 as a solution to libuniconf4.6 0
  Added libuniconf4.4 to the remove list
  Fixing libuniconf4.6 via remove of libuniconf4.4
Investigating gdm-guest-session
Package gdm-guest-session has broken dep on gdm
  Considering gdm 3 as a solution to gdm-guest-session 0
  Holding Back gdm-guest-session rather than change gdm
Investigating libgnomekbdui3
Package libgnomekbdui3 has broken dep on libgnomekbd3
  Considering libgnomekbd3 1 as a solution to libgnomekbdui3 -1
  Removing libgnomekbdui3 rather than change libgnomekbd3
Investigating libltdl7-dev
Package libltdl7-dev has broken dep on libltdl7
  Considering libltdl7 94 as a solution to libltdl7-dev -1
  Removing libltdl7-dev rather than change libltdl7
Investigating libgdl-1-0
Package libgdl-1-0 has broken dep on libgdl-1-common
  Considering libgdl-1-common 3 as a solution to libgdl-1-0 -1
  Removing libgdl-1-0 rather than change libgdl-1-common
Investigating x11-common
Package x11-common has broken dep on gdm
  Considering gdm 3 as a solution to x11-common 496
  Upgrading gdm due to Breaks field in x11-common
Investigating initramfs-tools
Package initramfs-tools has broken dep on usplash
  Considering usplash 1 as a solution to initramfs-tools 66
  Upgrading usplash due to Breaks field in initramfs-tools
Investigating gdm
Package gdm has broken dep on fast-user-switch-applet
  Considering fast-user-switch-applet 9999 as a solution to gdm 3
  Holding Back gdm rather than change fast-user-switch-applet
Investigating usplash
Package usplash has broken dep on gdm
  Considering gdm 3 as a solution to usplash 1
  Holding Back usplash rather than change gdm
Investigating mysql-server-5.0
Package mysql-server-5.0 has broken dep on mysql-server
  Considering mysql-server 0 as a solution to mysql-server-5.0 0
  Holding Back mysql-server-5.0 rather than change mysql-server
 Try to Re-Instate mysql-server
 Try to Re-Instate gdm-guest-session
Investigating x11-common
Package x11-common has broken dep on gdm
  Considering gdm 3 as a solution to x11-common 496
  Upgrading gdm due to Breaks field in x11-common
Investigating initramfs-tools
Package initramfs-tools has broken dep on usplash
  Considering usplash 1 as a solution to initramfs-tools 66
  Upgrading usplash due to Breaks field in initramfs-tools
Investigating gdm
Package gdm has broken dep on fast-user-switch-applet
  Considering fast-user-switch-applet 9999 as a solution to gdm 3
  Holding Back gdm rather than change fast-user-switch-applet
Investigating usplash
Package usplash has broken dep on gdm
  Considering gdm 3 as a solution to usplash 1
  Holding Back usplash rather than change gdm
 Try to Re-Instate mysql-server-5.0
Investigating x11-common
Package x11-common has broken dep on gdm
  Considering gdm 3 as a solution to x11-common 496
  Upgrading gdm due to Breaks field in x11-common
Investigating initramfs-tools
Package initramfs-tools has broken dep on usplash
  Considering usplash 1 as a solution to initramfs-tools 66
  Upgrading usplash due to Breaks field in initramfs-tools
Investigating gdm
Package gdm has broken dep on fast-user-switch-applet
  Considering fast-user-switch-applet 9999 as a solution to gdm 3
  Holding Back gdm rather than change fast-user-switch-applet
Investigating usplash
Package usplash has broken dep on gdm
  Considering gdm 3 as a solution to usplash 1
  Holding Back usplash rather than change gdm
Investigating x11-common
Package x11-common has broken dep on gdm
  Considering gdm 3 as a solution to x11-common 496
  Upgrading gdm due to Breaks field in x11-common
Investigating initramfs-tools
Package initramfs-tools has broken dep on usplash
  Considering usplash 1 as a solution to initramfs-tools 66
  Upgrading usplash due to Breaks field in initramfs-tools
Investigating gdm
Package gdm has broken dep on fast-user-switch-applet
  Considering fast-user-switch-applet 9999 as a solution to gdm 3
  Holding Back gdm rather than change fast-user-switch-applet
Investigating usplash
Package usplash has broken dep on gdm
  Considering gdm 3 as a solution to usplash 1
  Holding Back usplash rather than change gdm
Investigating x11-common
Package x11-common has broken dep on gdm
  Considering gdm 3 as a solution to x11-common 496
  Upgrading gdm due to Breaks field in x11-common
Investigating initramfs-tools
Package initramfs-tools has broken dep on usplash
  Considering usplash 1 as a solution to initramfs-tools 66
  Upgrading usplash due to Breaks field in initramfs-tools
Investigating gdm
Package gdm has broken dep on fast-user-switch-applet
  Considering fast-user-switch-applet 9999 as a solution to gdm 3
  Holding Back gdm rather than change fast-user-switch-applet
Investigating usplash
Package usplash has broken dep on gdm
  Considering gdm 3 as a solution to usplash 1
  Holding Back usplash rather than change gdm
Investigating x11-common
Package x11-common has broken dep on gdm
  Considering gdm 3 as a solution to x11-common 496
  Upgrading gdm due to Breaks field in x11-common
Investigating initramfs-tools
Package initramfs-tools has broken dep on usplash
  Considering usplash 1 as a solution to initramfs-tools 66
  Upgrading usplash due to Breaks field in initramfs-tools
Investigating gdm
Package gdm has broken dep on fast-user-switch-applet
  Considering fast-user-switch-applet 9999 as a solution to gdm 3
  Holding Back gdm rather than change fast-user-switch-applet
Investigating usplash
Package usplash has broken dep on gdm
  Considering gdm 3 as a solution to usplash 1
  Holding Back usplash rather than change gdm
Investigating x11-common
Package x11-common has broken dep on gdm
  Considering gdm 3 as a solution to x11-common 496
  Upgrading gdm due to Breaks field in x11-common
Investigating initramfs-tools
Package initramfs-tools has broken dep on usplash
  Considering usplash 1 as a solution to initramfs-tools 66
  Upgrading usplash due to Breaks field in initramfs-tools
Investigating gdm
Package gdm has broken dep on fast-user-switch-applet
  Considering fast-user-switch-applet 9999 as a solution to gdm 3
  Holding Back gdm rather than change fast-user-switch-applet
Investigating usplash
Package usplash has broken dep on gdm
  Considering gdm 3 as a solution to usplash 1
  Holding Back usplash rather than change gdm
Investigating x11-common
Package x11-common has broken dep on gdm
  Considering gdm 3 as a solution to x11-common 496
  Upgrading gdm due to Breaks field in x11-common
Investigating initramfs-tools
Package initramfs-tools has broken dep on usplash
  Considering usplash 1 as a solution to initramfs-tools 66
  Upgrading usplash due to Breaks field in initramfs-tools
Investigating gdm
Package gdm has broken dep on fast-user-switch-applet
  Considering fast-user-switch-applet 9999 as a solution to gdm 3
  Holding Back gdm rather than change fast-user-switch-applet
Investigating usplash
Package usplash has broken dep on gdm
  Considering gdm 3 as a solution to usplash 1
  Holding Back usplash rather than change gdm
Investigating x11-common
Package x11-common has broken dep on gdm
  Considering gdm 3 as a solution to x11-common 496
  Upgrading gdm due to Breaks field in x11-common
Investigating initramfs-tools
Package initramfs-tools has broken dep on usplash
  Considering usplash 1 as a solution to initramfs-tools 66
  Upgrading usplash due to Breaks field in initramfs-tools
Investigating gdm
Package gdm has broken dep on fast-user-switch-applet
  Considering fast-user-switch-applet 9999 as a solution to gdm 3
  Holding Back gdm rather than change fast-user-switch-applet
Investigating usplash
Package usplash has broken dep on gdm
  Considering gdm 3 as a solution to usplash 1
  Holding Back usplash rather than change gdm
Done
Log time: 2009-11-08 18:02:31.956284

```

main.log
```

2009-11-08 18:01:42,204 INFO Using config files '['./DistUpgrade.cfg']'
2009-11-08 18:01:42,218 INFO release-upgrader version '0.126.6.1' started
2009-11-08 18:01:42,760 DEBUG svg pixbuf loader failed (Error displaying image)
2009-11-08 18:01:42,767 DEBUG Using 'DistUpgradeViewGtk' view
2009-11-08 18:01:42,853 DEBUG aufsOptionsAndEnvironmentSetup()
2009-11-08 18:01:42,855 DEBUG using '/tmp/upgrade-rw-J3KAUE' as aufs_rw_dir
2009-11-08 18:01:42,855 DEBUG using '/tmp/upgrade-chroot-QHPh5c' as aufs chroot dir
2009-11-08 18:01:42,856 DEBUG enable dpkg --force-overwrite
2009-11-08 18:01:42,974 DEBUG lsb-release: 'jaunty'
2009-11-08 18:01:42,984 DEBUG who -m --ips: ''
2009-11-08 18:01:42,986 DEBUG _pythonSymlinkCheck run
2009-11-08 18:01:42,987 DEBUG openCache()
2009-11-08 18:01:45,334 DEBUG /openCache(), new cache size 26955
2009-11-08 18:01:45,335 DEBUG needServerMode(): can not find a desktop meta package or key deps, running in server mode
2009-11-08 18:01:45,335 DEBUG checkViewDepends()
2009-11-08 18:01:45,335 DEBUG running doUpdate() (showErrors=False)
2009-11-08 18:01:46,358 DEBUG openCache()
2009-11-08 18:01:47,762 DEBUG /openCache(), new cache size 26955
2009-11-08 18:01:47,763 DEBUG doPostInitialUpdate
2009-11-08 18:01:47,763 DEBUG Plugin modules in ./plugins: langpack_manual_plugin.py dpkg_status_plugin.py deb_plugin.py remove_lilo_plugin.py kdelibs4to5_plugin.py
2009-11-08 18:01:47,763 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2009-11-08 18:01:47,765 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2009-11-08 18:01:47,766 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2009-11-08 18:01:47,768 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2009-11-08 18:01:47,768 DEBUG Loading module ./plugins/deb_plugin.py
2009-11-08 18:01:47,769 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2009-11-08 18:01:47,769 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2009-11-08 18:01:47,770 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2009-11-08 18:01:47,771 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2009-11-08 18:01:47,772 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2009-11-08 18:01:47,773 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2009-11-08 18:01:47,773 DEBUG plugins for condition 'karmicPostInitialUpdate' are '[]'
2009-11-08 18:01:47,773 DEBUG plugins for condition 'from_jauntyPostInitialUpdate' are '[]'
2009-11-08 18:01:47,773 DEBUG quirks: running karmicPostInitialUpdate
2009-11-08 18:01:47,773 DEBUG running karmicPostInitialUpdate
2009-11-08 18:01:51,510 DEBUG Foreign: wine-gecko libgeoip1 swiftfox-athlon64-32bit deluge deluge-common opera picasa chromium-browser geoip-database wicd python-support libtorrent-rasterbar5 python-libtorrent chromium-codecs-ffmpeg deluge-gtk wine
2009-11-08 18:01:51,510 DEBUG Obsolete: 
2009-11-08 18:01:51,511 DEBUG updateSourcesList()
2009-11-08 18:01:51,575 DEBUG rewriteSourcesList()
2009-11-08 18:01:51,579 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted'
2009-11-08 18:01:51,579 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted' updated to new dist
2009-11-08 18:01:51,580 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted'
2009-11-08 18:01:51,580 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted' updated to new dist
2009-11-08 18:01:51,580 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted'
2009-11-08 18:01:51,580 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted' updated to new dist
2009-11-08 18:01:51,580 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted'
2009-11-08 18:01:51,580 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted' updated to new dist
2009-11-08 18:01:51,580 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe'
2009-11-08 18:01:51,580 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ karmic universe' updated to new dist
2009-11-08 18:01:51,581 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe'
2009-11-08 18:01:51,581 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe' updated to new dist
2009-11-08 18:01:51,581 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe'
2009-11-08 18:01:51,581 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe' updated to new dist
2009-11-08 18:01:51,581 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe'
2009-11-08 18:01:51,581 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe' updated to new dist
2009-11-08 18:01:51,581 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse'
2009-11-08 18:01:51,581 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse' updated to new dist
2009-11-08 18:01:51,581 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse'
2009-11-08 18:01:51,582 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse' updated to new dist
2009-11-08 18:01:51,582 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse'
2009-11-08 18:01:51,582 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse' updated to new dist
2009-11-08 18:01:51,582 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse'
2009-11-08 18:01:51,582 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse' updated to new dist
2009-11-08 18:01:51,582 DEBUG examining: 'deb-src http://archive.canonical.com/ubuntu jaunty partner'
2009-11-08 18:01:51,582 DEBUG entry 'deb-src http://archive.canonical.com/ubuntu karmic partner' updated to new dist
2009-11-08 18:01:51,582 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu jaunty-security main restricted'
2009-11-08 18:01:51,583 DEBUG entry 'deb http://security.ubuntu.com/ubuntu karmic-security main restricted' updated to new dist
2009-11-08 18:01:51,583 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted'
2009-11-08 18:01:51,583 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted' updated to new dist
2009-11-08 18:01:51,583 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu jaunty-security universe'
2009-11-08 18:01:51,583 DEBUG entry 'deb http://security.ubuntu.com/ubuntu karmic-security universe' updated to new dist
2009-11-08 18:01:51,583 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu jaunty-security universe'
2009-11-08 18:01:51,583 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu karmic-security universe' updated to new dist
2009-11-08 18:01:51,583 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu jaunty-security multiverse'
2009-11-08 18:01:51,583 DEBUG entry 'deb http://security.ubuntu.com/ubuntu karmic-security multiverse' updated to new dist
2009-11-08 18:01:51,584 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse'
2009-11-08 18:01:51,584 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse' updated to new dist
2009-11-08 18:01:51,584 DEBUG examining: 'deb http://apt.wicd.net jaunty extras'
2009-11-08 18:01:51,588 DEBUG entry '# deb http://apt.wicd.net karmic extras # disabled on upgrade to karmic' was disabled (unknown mirror)
2009-11-08 18:01:51,588 DEBUG examining: 'deb http://archive.canonical.com/ubuntu jaunty partner'
2009-11-08 18:01:51,588 DEBUG entry 'deb http://archive.canonical.com/ubuntu karmic partner' updated to new dist
2009-11-08 18:01:51,588 DEBUG examining: 'deb http://deb.opera.com/opera/ stable non-free'
2009-11-08 18:01:51,592 DEBUG entry '# deb http://deb.opera.com/opera/ stable non-free # disabled on upgrade to karmic' was disabled (unknown mirror)
2009-11-08 18:01:51,592 DEBUG examining: 'deb http://dl.google.com/linux/deb/ stable non-free'
2009-11-08 18:01:51,596 DEBUG entry '# deb http://dl.google.com/linux/deb/ stable non-free # disabled on upgrade to karmic' was disabled (unknown mirror)
2009-11-08 18:01:51,596 DEBUG examining: 'deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 8.10 "Intrepid Ibex" disabled on upgrade to jaunty'
2009-11-08 18:01:51,600 DEBUG entry '# deb http://wine.budgetdedicated.com/apt karmic main #WineHQ - Ubuntu 8.10 "Intrepid Ibex" disabled on upgrade to jaunty disabled on upgrade to karmic' was disabled (unknown mirror)
2009-11-08 18:01:51,600 DEBUG examining: 'deb http://www.fbriere.net/debian/dists/unstable ./'
2009-11-08 18:01:51,605 DEBUG entry '# deb http://www.fbriere.net/debian/dists/unstable ./ # disabled on upgrade to karmic' was disabled (unknown mirror)
2009-11-08 18:01:51,605 DEBUG examining: 'deb http://getswiftfox.com/builds/debian unstable non-free'
2009-11-08 18:01:51,609 DEBUG entry '# deb http://getswiftfox.com/builds/debian unstable non-free # disabled on upgrade to karmic' was disabled (unknown mirror)
2009-11-08 18:01:51,609 DEBUG examining: 'deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu jaunty main'
2009-11-08 18:01:51,613 DEBUG entry '# deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu karmic main # disabled on upgrade to karmic' was disabled (unknown mirror)
2009-11-08 18:01:51,613 DEBUG examining: 'deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main'
2009-11-08 18:01:51,617 DEBUG entry '# deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main # disabled on upgrade to karmic' was disabled (unknown mirror)
2009-11-08 18:01:51,617 DEBUG examining: 'deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main'
2009-11-08 18:01:51,621 DEBUG entry '# deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main # disabled on upgrade to karmic' was disabled (unknown mirror)
2009-11-08 18:01:51,621 INFO fixing components inconsistency from 'deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted'
2009-11-08 18:01:51,621 INFO to new entry 'deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted'
2009-11-08 18:01:51,621 INFO fixing components inconsistency from 'deb http://security.ubuntu.com/ubuntu karmic-security main restricted'
2009-11-08 18:01:51,621 INFO to new entry 'deb http://security.ubuntu.com/ubuntu karmic-security main restricted'
2009-11-08 18:01:52,673 DEBUG running doUpdate() (showErrors=True)
2009-11-08 18:02:07,642 DEBUG openCache()
2009-11-08 18:02:12,838 DEBUG /openCache(), new cache size 28947
2009-11-08 18:02:12,907 DEBUG demoted: 'acl binutils-static bluez-gnome contact-lookup-applet cpp-4.3 cupsddk g++-4.3 gcc-4.3 gcc-4.3-base gnome-mount gstreamer0.10-gnomevfs human-icon-theme klogd libglew1.5 libgnome-speech7 libgnomevfs2-bin libmono-data1.0-cil libmono-data2.0-cil libmono-getoptions1.0-cil libmono-posix1.0-cil libmysqlclient15-dev libmysqlclient15off libpolkit-gnome0 libsmbios2 libstdc++6-4.3-dev nvidia-180-modaliases phonon phonon-backend-gstreamer pidgin-otr policykit-gnome python-gdata python-launchpad-bugs python-usb qt4-qtconfig rss-glx sysklogd tangerine-icon-theme ttf-kochi-gothic ttf-sazanami-gothic ubuntu-gdm-themes'
2009-11-08 18:02:27,687 ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
2009-11-08 18:02:27,688 DEBUG abort called
2009-11-08 18:02:27,690 DEBUG openCache()
2009-11-08 18:02:31,957 DEBUG /openCache(), new cache size 26955
2009-11-08 18:02:31,958 DEBUG enabling apt cron job

```

term.log is empty

---

### Post by ffxigotenks on 2009-11-11
anyone?

---

### Post by Peter Davis on 2010-01-25
I have the same problem.  I also had major problems trying clean installing from 8.04 CDs, so am very reluctant to try that again.  I reported all the detail as Bug #472979, and would be glad if anybody can come up with any suggestions.

---

### Post by tachuela on 2010-01-25
From now on guys; make a separate partition for /home. That way; if the upgrade fails; you can do a fresh install on the '/' particion and you keep your /home by picking it, but NOT FORMATTING it.

---

### Post by Peter Davis on 2010-01-29
I've done that, thanks.  Now how do I overcome the inability to calculate the upgrade?

---

### Post by Hagar Delest on 2010-01-30
Basically, I never upgrade by soft (dist-upgrade or Synaptic). I tried that once or twice, too many issues. Even if it works, former files can cause troubles in the new version. As recommended above, make several partitions (for your documents, not for the whole /home directory) but also for profiles: then, just create links to the profiles, that way you don't lose anything. For example I have a partition with a /Thunderbird folder and my ~/.thunderbird is a link to that directory.

The most important is to write down which partition corresponds to which use so that you don't format the wrong ones!

---

### Post by tachuela on 2010-01-30
Upgrades fail because users fail to remove all third parties from the repositories; or fail to remove Medibuntu Folder after having removed it from the repositories; or fail to fully update the system to be upgraded.

---

