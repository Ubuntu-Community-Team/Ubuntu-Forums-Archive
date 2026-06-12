---
title: "Upgrade issues"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by absolutezero1287 on 2009-10-17
I'm trying to upgrade from Ubuntu 8.04 to 8.10 but I keep getting an error saying something about an "unresolvable failure".

I tried apt-get autoclean and apt-get autoremove but still got the same error.
Attached is a screenshot of the error message.

I coped some files from /var/log/dist-upgrade
Here's apt.log
```

Log time: 2009-10-17 18:57:13.513349
Log time: 2009-10-17 18:57:49.894709
Log time: 2009-10-17 18:58:43.482007
Installing xserver-xorg-core as dep of xserver-xorg
Installing xserver-common as dep of xserver-xorg-core
Installing libpciaccess0 as dep of xserver-xorg-core
new important dependency: libgl1-mesa-dri
Installing libgl1-mesa-dri as dep of xserver-xorg-core
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing libxi6 as dep of xserver-xorg-input-synaptics
Installing libcanberra-gtk0 as dep of gnome-control-center
Installing libcanberra0 as dep of libcanberra-gtk0
Installing libasound2 as dep of libcanberra0
Installing libltdl7 as dep of libcanberra0
Installing libgtk2.0-0 as dep of libcanberra-gtk0
Installing libcups2 as dep of libgtk2.0-0
Installing libgnutls26 as dep of libcups2
Installing libc6 as dep of libgnutls26
Installing findutils as dep of libc6
Installing libgcrypt11 as dep of libgnutls26
Installing libglib2.0-0 as dep of libgtk2.0-0
Installing libselinux1 as dep of libglib2.0-0
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libcairo2 as dep of libpango1.0-0
Installing libpixman-1-0 as dep of libcairo2
Installing libxcb-render-util0 as dep of libcairo2
Installing libxcb-render0 as dep of libxcb-render-util0
Installing libcanberra-gtk-module as dep of libcanberra-gtk0
Installing libebook1.2-9 as dep of gnome-control-center
Installing libcamel1.2-14 as dep of libebook1.2-9
Installing libedataserver1.2-11 as dep of libcamel1.2-14
Installing libsoup2.4-1 as dep of libedataserver1.2-11
Installing libsqlite3-0 as dep of libcamel1.2-14
Installing libpopt0 as dep of libebook1.2-9
Installing libgnome-desktop-2-7 as dep of gnome-control-center
Installing libgnomekbd3 as dep of gnome-settings-daemon
Installing libxklavier12 as dep of libgnomekbd3
Installing libgnomekbd-common as dep of libgnomekbd3
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libgnomekbdui3 as dep of gnome-control-center
Installing capplets-data as dep of gnome-control-center
Installing gconf2-common as dep of gnome-control-center
Installing ubuntu-system-service as dep of gnome-control-center
new important dependency: screen-resolution-extra
Installing screen-resolution-extra as dep of gnome-control-center
Installing python-xkit as dep of screen-resolution-extra
new important dependency: bluetooth
Installing bluetooth as dep of bluez-gnome
Installing bluez as dep of bluetooth
Installing libbluetooth3 as dep of bluez
Installing bluez-alsa as dep of bluetooth
Installing bluez-gstreamer as dep of bluetooth
Installing libgp11-0 as dep of gnome-keyring
Installing libglade2.0-cil as dep of f-spot
Installing libglib2.0-cil as dep of libglade2.0-cil
Installing libgtk2.0-cil as dep of libglade2.0-cil
Installing libglitz-glx1 as dep of f-spot
Installing libglitz1 as dep of libglitz-glx1
Installing libgnome-keyring1.0-cil as dep of f-spot
Installing libmono-system-web2.0-cil as dep of f-spot
Installing libmono-system2.0-cil as dep of libmono-system-web2.0-cil
Installing libmono-security2.0-cil as dep of libmono-system2.0-cil
Installing libmono0 as dep of libmono-system2.0-cil
Installing mono-jit as dep of libmono-system2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono2.0-cil as dep of libmono-system-web2.0-cil
Installing libgdiplus as dep of libmono-system-web2.0-cil
Installing gvfs-bin as dep of f-spot
Installing libsane as dep of libsane-dev
Installing libdevmapper1.02.1 as dep of dmsetup
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libsm6 as dep of libsm-dev
Installing libruby1.8 as dep of ruby1.8-dev
Installing gcc-4.3-base as dep of libstdc++6
Installing libgmime2.2-cil as dep of tomboy
Installing libgmime-2.0-2a as dep of libgmime2.2-cil
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing libuuid-perl as dep of doc-base
Installing dpkg as dep of doc-base
Installing libmldbm-perl as dep of doc-base
Installing libfreezethaw-perl as dep of libmldbm-perl
Installing perl-modules as dep of perl
Installing libbz2-1.0 as dep of bzip2
Installing libecal1.2-7 as dep of evolution-webcal
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
Installing libpt-1.10.10 as dep of ekiga
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing libhunspell-1.2-0 as dep of openoffice.org-core
Installing libhyphen0 as dep of openoffice.org-core
Installing libneon27 as dep of openoffice.org-core
Installing libqtcore4 as dep of libqt4-opengl
Installing libqtgui4 as dep of libqt4-opengl
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing cups-common as dep of cupsys-common
Installing compiz-wrapper as dep of compiz-core
Installing update-manager-core as dep of update-manager
Installing python-apt as dep of update-manager-core
Installing apt-utils as dep of python-apt
Installing apt as dep of apt-utils
Installing libdb4.7 as dep of apt-utils
Installing openoffice.org-base-core as dep of openoffice.org-writer
new important dependency: openoffice.org-emailmerge
Installing openoffice.org-emailmerge as dep of openoffice.org-writer
Installing libqt4-network as dep of libqt4-assistant
Installing gnome-media-common as dep of gnome-media
Installing metacity-common as dep of metacity
Installing libgtkglext1 as dep of libgtk-vnc-1.0-0
Installing libeel2-2 as dep of nautilus
Installing nautilus-data as dep of nautilus
Installing libtasn1-3 as dep of libtasn1-3-dev
Installing libgnome2-common as dep of libgnome2-0
Installing cups as dep of hal-cups-utils
Installing libcupsimage2 as dep of cups
Installing libijs-0.35 as dep of cups
Installing libpoppler3 as dep of cups
Installing cups-client as dep of cups
Installing avahi-utils as dep of cups
Installing python-cupshelpers as dep of hal-cups-utils
Installing python-usb as dep of hal-cups-utils
Installing libbind9-40 as dep of bind9-host
Installing libcap2 as dep of libbind9-40
Installing libdns43 as dep of libbind9-40
Installing libisc44 as dep of libdns43
Installing libisccfg40 as dep of libbind9-40
Installing libisccc40 as dep of libisccfg40
Installing liblwres40 as dep of bind9-host
Installing libatspi1.0-0 as dep of libgail-gnome-module
Installing gimp-help-common as dep of gimp-help-en
Installing openoffice.org-draw as dep of openoffice.org-impress
Installing language-pack-en as dep of language-pack-en-base
Installing libaudclient1 as dep of audacious
Installing audacious-plugins as dep of audacious
Installing libmad0 as dep of audacious-plugins
Installing libneon27-gnutls as dep of audacious-plugins
Installing libaudid3tag1 as dep of audacious
Installing linux-headers-2.6.27-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.27-14 as dep of linux-headers-2.6.27-14-generic
Installing libaspell15 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing xserver-xorg-video-geode as dep of xserver-xorg-video-amd
Installing ruby1.8 as dep of irb1.8
Installing libreadline-ruby1.8 as dep of irb1.8
Installing xserver-xorg-video-apm as dep of xserver-xorg-video-all
Installing xserver-xorg-video-ark as dep of xserver-xorg-video-all
Installing xserver-xorg-video-ati as dep of xserver-xorg-video-all
Installing xserver-xorg-video-r128 as dep of xserver-xorg-video-ati
Installing xserver-xorg-video-mach64 as dep of xserver-xorg-video-ati
Installing xserver-xorg-video-radeon as dep of xserver-xorg-video-ati
Installing xserver-xorg-video-chips as dep of xserver-xorg-video-all
Installing xserver-xorg-video-cirrus as dep of xserver-xorg-video-all
Installing xserver-xorg-video-fbdev as dep of xserver-xorg-video-all
Installing xserver-xorg-video-i128 as dep of xserver-xorg-video-all
Installing xserver-xorg-video-i740 as dep of xserver-xorg-video-all
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
Installing xserver-xorg-video-mga as dep of xserver-xorg-video-all
Installing xserver-xorg-video-neomagic as dep of xserver-xorg-video-all
Installing xserver-xorg-video-nv as dep of xserver-xorg-video-all
Installing xserver-xorg-video-s3 as dep of xserver-xorg-video-all
Installing xserver-xorg-video-savage as dep of xserver-xorg-video-all
Installing xserver-xorg-video-siliconmotion as dep of xserver-xorg-video-all
Installing xserver-xorg-video-sis as dep of xserver-xorg-video-all
Installing xserver-xorg-video-sisusb as dep of xserver-xorg-video-all
Installing xserver-xorg-video-tdfx as dep of xserver-xorg-video-all
Installing xserver-xorg-video-trident as dep of xserver-xorg-video-all
Installing xserver-xorg-video-tseng as dep of xserver-xorg-video-all
Installing xserver-xorg-video-vesa as dep of xserver-xorg-video-all
Installing xserver-xorg-video-openchrome as dep of xserver-xorg-video-all
Installing xserver-xorg-video-voodoo as dep of xserver-xorg-video-all
Installing xserver-xorg-video-vmware as dep of xserver-xorg-video-all
Installing xserver-xorg-video-v4l as dep of xserver-xorg-video-all
Installing xsane-common as dep of xsane
Installing libgsf-1-114 as dep of tracker
Installing libgsf-1-common as dep of libgsf-1-114
Installing libpoppler-glib3 as dep of tracker
Installing libcups2-dev as dep of libcupsimage2-dev
Installing libsnmp-base as dep of libsnmp15
Installing libperl5.10 as dep of libsnmp15
Installing myspell-en-au as dep of language-support-writing-en
Installing hunspell-en-us as dep of language-support-writing-en
Installing samba-common as dep of smbclient
Installing libtalloc1 as dep of samba-common
Installing libwbclient0 as dep of samba-common
Installing foomatic-filters as dep of pxljr
Installing libgucharmap7 as dep of gucharmap
Installing libgpm2 as dep of brltty-x11
Installing brltty as dep of brltty-x11
Installing libnm-glib0 as dep of network-manager
Installing libnm-util0 as dep of libnm-glib0
new important dependency: libmbca0
Installing libmbca0 as dep of network-manager-gnome
Installing libgweather1 as dep of libmbca0
Installing mobile-broadband-provider-info as dep of libmbca0
Installing wpasupplicant as dep of network-manager
Installing libpcsclite1 as dep of wpasupplicant
Installing guile-1.8-libs as dep of gnome-games
Installing libggz2 as dep of gnome-games
Installing libggzcore9 as dep of gnome-games
Installing libggzmod4 as dep of gnome-games
Installing gnome-games-data as dep of gnome-games
Installing gnome-cards-data as dep of gnome-games-data
Installing gdebi-core as dep of gdebi
Installing evolution as dep of evolution-exchange
Installing libebackend1.2-0 as dep of evolution
Installing libedataserverui1.2-8 as dep of evolution
Installing libegroupwise1.2-13 as dep of evolution
Installing libexchange-storage1.2-3 as dep of evolution
Installing libgdata-google1.2-1 as dep of evolution
Installing libgdata1.2-1 as dep of libgdata-google1.2-1
Installing libgtkhtml-editor0 as dep of evolution
Installing libgtkhtml3.14-19 as dep of libgtkhtml-editor0
Installing libgtkhtml-editor-common as dep of libgtkhtml-editor0
Installing evolution-data-server as dep of evolution
Installing libedata-book1.2-2 as dep of evolution-data-server
Installing libedata-cal1.2-6 as dep of evolution-data-server
Installing evolution-data-server-common as dep of evolution-data-server
Installing libasound2-plugins as dep of pulseaudio
Installing libboost-iostreams1.34.1 as dep of wesnoth
Installing wesnoth-data as dep of wesnoth
Installing gcc-4.2-base as dep of g++-4.2
Installing gcc-4.2 as dep of g++-4.2
Installing cpp-4.2 as dep of gcc-4.2
Installing libgcc1 as dep of gcc-4.2
Installing libstdc++6-4.2-dev as dep of g++-4.2
Installing libcairomm-1.0-1 as dep of gparted
Installing libglibmm-2.4-1c2a as dep of gparted
Installing libgtkmm-2.4-1c2a as dep of gparted
Installing libpangomm-1.4-1 as dep of libgtkmm-2.4-1c2a
Installing libparted1.8-9 as dep of gparted
Installing totem-gstreamer as dep of totem-plugins
Installing libtotem-plparser12 as dep of totem-gstreamer
Installing totem-common as dep of totem-gstreamer
Installing python-rdflib as dep of totem-plugins
Installing python-pkg-resources as dep of python-rdflib
Installing python-gobject as dep of totem-plugins
Installing python2.5 as dep of python-gobject
Installing python2.5-minimal as dep of python2.5
Installing libffi5 as dep of python-gobject
Installing python-gtk2 as dep of totem-plugins
Installing linux-image-2.6.27-14-generic as dep of linux-image-generic
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing linux-firmware as dep of linux-image-generic
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libqt4-xml as dep of libqt4-dbus
Installing libmtp8 as dep of rhythmbox
Installing libmp3lame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libgmp3c2 as dep of libgmp3-dev
Installing libgmpxx4ldbl as dep of libgmp3-dev
Installing libdjvulibre21 as dep of libmagick10
Installing libgraphviz4 as dep of libmagick10
Installing libgd2-noxpm as dep of libgraphviz4
Installing libilmbase6 as dep of libmagick10
Installing libopenexr6 as dep of libmagick10
Installing libggi2 as dep of mplayer
Installing libglide2 as dep of libggi2
Installing libopenal1 as dep of mplayer
Installing libspeex1 as dep of mplayer
Installing libx264-59 as dep of mplayer
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing libsasl2-2 as dep of libsasl2-modules
Installing openssl as dep of openssl-blacklist
Installing python-imaging as dep of python-imaging-tk
Installing esound-common as dep of libesd-alsa0
Installing gtk2-engines as dep of gnome-themes
Installing libcryptui0 as dep of seahorse
Installing libgpgme11 as dep of seahorse
new important dependency: seahorse-plugins
Installing seahorse-plugins as dep of seahorse
Installing cups-bsd as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing cups-driver-gutenprint as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libgutenprint2 as dep of cups-driver-gutenprint
Installing gstreamer0.10-schroedinger as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libcanberra-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libpam-ck-connector as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing rarian-compat as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing xml-core as dep of rarian-compat
new important dependency: gdm-guest-session
Installing gdm-guest-session as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing gdm as dep of gdm-guest-session
new important dependency: usb-creator
Installing usb-creator as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing syslinux as dep of usb-creator
Installing mtools as dep of syslinux
Installing libept0 as dep of aptitude
Installing libxapian15 as dep of libept0
Installing libqt4-script as dep of libqt4-core
Installing libxerces-c28 as dep of libxalan110
Installing fontconfig-config as dep of libfontconfig1
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libghc6-x11-dev as dep of libghc6-hgl-dev
Installing libxinerama-dev as dep of libghc6-x11-dev
Installing libxext-dev as dep of libxinerama-dev
Installing libxext6 as dep of libxext-dev
Installing x11proto-xext-dev as dep of libxext-dev
Installing libxinerama1 as dep of libxinerama-dev
Installing x11proto-xinerama-dev as dep of libxinerama-dev
Installing libavahi-gobject0 as dep of vinagre
Installing scim-gtk2-immodule as dep of scim
Installing libxdmcp6 as dep of libxdmcp-dev
Installing libkrb53 as dep of libkrb5-dev
Installing libkadm55 as dep of libkrb5-dev
Installing cpp as dep of g++
Installing cpp-4.3 as dep of cpp
Installing libmpfr1ldbl as dep of cpp-4.3
Installing gcc as dep of g++
Installing gcc-4.3 as dep of gcc
Installing g++-4.3 as dep of g++
Installing libstdc++6-4.3-dev as dep of g++-4.3
Installing libwww-perl as dep of librpc-xml-perl
Installing libtag1c2a as dep of gstreamer0.10-plugins-good
Installing libv4l-0 as dep of gstreamer0.10-plugins-good
Installing libvte9 as dep of gnome-terminal
Installing gnome-terminal-data as dep of gnome-terminal
Installing openoffice.org-common as dep of openoffice.org-style-human
Installing e2fslibs as dep of e2fsprogs
Installing libpng12-0 as dep of libpng12-dev
Installing libpci3 as dep of toshset
Installing libpolkit2 as dep of policykit
Installing upstart as dep of upstart-compat-sysv
Installing sysvinit-utils as dep of upstart
Installing libsepol1 as dep of sysvinit-utils
Installing libhd14 as dep of hwinfo
Installing libssl0.9.8 as dep of openssh-client
Installing libts-0.0-0 as dep of libdirectfb-1.0-0
new important dependency: nvidia-common
Installing nvidia-common as dep of jockey-common
Installing nvidia-177-modaliases as dep of nvidia-common
Installing nvidia-173-modaliases as dep of nvidia-common
Installing nvidia-96-modaliases as dep of nvidia-common
Installing nvidia-71-modaliases as dep of nvidia-common
Installing nvidia-180-modaliases as dep of nvidia-common
new important dependency: fglrx-modaliases
Installing fglrx-modaliases as dep of jockey-common
new important dependency: libltdl7-dev
Installing libltdl7-dev as dep of libtool
Installing libpolkit-dbus2 as dep of libgconf2-4
Installing at-spi as dep of python-pyatspi
Installing libavcodec51 as dep of gstreamer0.10-ffmpeg
Installing libavutil49 as dep of libavcodec51
Installing libavformat52 as dep of gstreamer0.10-ffmpeg
Installing libpostproc51 as dep of gstreamer0.10-ffmpeg
Installing firefox-3.0-branding as dep of firefox
Installing firefox-3.0 as dep of firefox-3.0-branding
Installing libexif12 as dep of libexif-dev
Installing libftgl2 as dep of chromium
Installing ttf-uralic as dep of chromium
Installing python-compizconfig as dep of compizconfig-settings-manager
Installing libqt4-svg as dep of libqt4-gui
Installing libqt4-designer as dep of libqt4-gui
Installing ghc6 as dep of ghc6-prof
Installing libsmbios2 as dep of hal
Installing libelf1 as dep of bug-buddy
Installing language-selector-common as dep of language-selector
new important dependency: libavcodec-unstripped-51
Installing libavcodec-unstripped-51 as dep of ubuntu-restricted-extras
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing wesnoth-tsg as dep of wesnoth-all
Installing wesnoth-trow as dep of wesnoth-all
Installing wesnoth-ttb as dep of wesnoth-all
Installing wesnoth-ei as dep of wesnoth-all
Installing wesnoth-utbs as dep of wesnoth-all
Installing wesnoth-did as dep of wesnoth-all
Installing wesnoth-nr as dep of wesnoth-all
Installing wesnoth-sof as dep of wesnoth-all
Installing wesnoth-l as dep of wesnoth-all
Installing wesnoth-aoi as dep of wesnoth-all
Installing kbd as dep of ubuntu-minimal
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libbonobo2-common as dep of libbonobo2-0
Installing libspectre1 as dep of evince
Installing zlib1g as dep of zlib1g-dev
Installing libmagic1 as dep of file
Installing libxi-dev as dep of x11proto-input-dev
Installing libtiff4 as dep of libtiff4-dev
Installing libtiffxx0c2 as dep of libtiff4-dev
Installing libspeexdsp1 as dep of libopal-2.2
Installing python-pycurl as dep of landscape-client
Installing python-twisted-web as dep of landscape-client
Installing python-twisted-core as dep of python-twisted-web
Installing python-twisted-bin as dep of python-twisted-core
Installing python-zopeinterface as dep of python-twisted-core
Installing python-pyopenssl as dep of python-twisted-core
Installing python-openssl as dep of python-pyopenssl
Installing python-pam as dep of python-twisted-core
Installing python-serial as dep of python-twisted-core
Installing landscape-common as dep of landscape-client
Installing update-motd as dep of landscape-common
Installing libdc1394-22 as dep of gstreamer0.10-plugins-bad
Installing libofa0 as dep of gstreamer0.10-plugins-bad
Installing libfftw3-3 as dep of libofa0
Installing iptables as dep of ufw
Installing libgimp2.0 as dep of gimp
Installing gimp-data as dep of gimp
Installing libbabl-0.0-0 as dep of gimp
Installing libgegl-0.0-0 as dep of gimp
Installing libbinio1ldbl as dep of audacious-plugins-extra
Installing libmikmod2 as dep of libsdl-mixer1.2
Installing imagemagick as dep of devede
new important dependency: apt-xapian-index
Installing apt-xapian-index as dep of synaptic
Installing python-xapian as dep of apt-xapian-index
Installing python-debian as dep of apt-xapian-index
Installing gnome-applets-data as dep of gnome-applets
Installing xinput as dep of xorg
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-i810
new important dependency: lockfile-progs
Installing lockfile-progs as dep of ntpdate
Installing liblockfile1 as dep of lockfile-progs
Installing linux-restricted-modules-2.6.27-14-generic as dep of linux-restricted-modules-generic
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libbrasero-media0 as dep of brasero
Installing libapparmor-perl as dep of apparmor-utils
Installing libapparmor1 as dep of libapparmor-perl
Installing gnome-panel-data as dep of gnome-panel
Installing libswscale0 as dep of libquicktime1
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libgdl-1-common as dep of libgdl-1-0
Starting
Starting 2
Investigating libgtk2.0-0
Package libgtk2.0-0 has broken dep on libgail18
  Considering libgail18 1 as a solution to libgtk2.0-0 850
  Added libgail18 to the remove list
  Fixing libgtk2.0-0 via remove of libgail18
Investigating xserver-xorg-core
Package xserver-xorg-core has broken dep on xserver-xorg-video-2
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-siliconmotion 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-ati 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-i740 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-geode 3 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-via -1 as a solution to xserver-xorg-core 90
  Added xserver-xorg-video-via to the remove list
  Considering xserver-xorg-video-nv 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-i810 0 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-intel 3 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-chips 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-tga 0 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-trident 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-s3 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-vga 0 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-i128 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-mga 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-nsc 0 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-newport -1 as a solution to xserver-xorg-core 90
  Added xserver-xorg-video-newport to the remove list
  Considering xserver-xorg-video-neomagic 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-cirrus 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-ark 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-tdfx 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-sisusb 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-dummy 0 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-rendition 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-vesa 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-cyrix -1 as a solution to xserver-xorg-core 90
  Added xserver-xorg-video-cyrix to the remove list
  Considering xserver-xorg-video-imstt -1 as a solution to xserver-xorg-core 90
  Added xserver-xorg-video-imstt to the remove list
  Considering xserver-xorg-video-glint 0 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-fbdev 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-savage 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-vmware 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-openchrome 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-s3virge 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-voodoo 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-apm 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-sis 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-v4l 2 as a solution to xserver-xorg-core 90
Package xserver-xorg-core has broken dep on xserver-xorg-video-psb
  Considering xserver-xorg-video-psb -1 as a solution to xserver-xorg-core 90
  Added xserver-xorg-video-psb to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-via
  Fixing xserver-xorg-core via remove of xserver-xorg-video-newport
  Fixing xserver-xorg-core via remove of xserver-xorg-video-cyrix
  Fixing xserver-xorg-core via remove of xserver-xorg-video-imstt
  Fixing xserver-xorg-core via remove of xserver-xorg-video-psb
Investigating rarian-compat
Package rarian-compat has broken dep on scrollkeeper
  Considering scrollkeeper 37 as a solution to rarian-compat 25
  Holding Back rarian-compat rather than change scrollkeeper
Investigating kbd
Package kbd has broken dep on console-utilities
  Considering console-tools 12 as a solution to kbd 22
  Considering console-tools 12 as a solution to kbd 22
  Added console-tools to the remove list
Package kbd has broken dep on open
  Considering console-tools 12 as a solution to kbd 22
  Considering console-tools 12 as a solution to kbd 22
  Added console-tools to the remove list
  Fixing kbd via remove of console-tools
  Fixing kbd via remove of console-tools
Investigating gimp-data
Package gimp-data has broken dep on gimp-python
  Considering gimp-python -1 as a solution to gimp-data 6
  Added gimp-python to the remove list
  Fixing gimp-data via remove of gimp-python
Investigating libmp3lame0
Package libmp3lame0 has broken dep on liblame0
  Considering liblame0 -1 as a solution to libmp3lame0 5
  Added liblame0 to the remove list
  Fixing libmp3lame0 via remove of liblame0
Investigating gimp
Package gimp has broken dep on gimp-gnomevfs
  Considering gimp-gnomevfs -1 as a solution to gimp 4
  Added gimp-gnomevfs to the remove list
  Fixing gimp via remove of gimp-gnomevfs
Investigating libgmime-2.0-2a
Package libgmime-2.0-2a has broken dep on libgmime-2.0-2
  Considering libgmime-2.0-2 -1 as a solution to libgmime-2.0-2a 4
  Added libgmime-2.0-2 to the remove list
  Fixing libgmime-2.0-2a via remove of libgmime-2.0-2
Investigating libpurple0
Package libpurple0 has broken dep on perlapi-5.8.8
  Considering perl-base 5283 as a solution to libpurple0 3
  Removing libpurple0 rather than change perlapi-5.8.8
Investigating hunspell-en-us
Package hunspell-en-us has broken dep on myspell-en-us
  Considering myspell-en-us 0 as a solution to hunspell-en-us 2
  Added myspell-en-us to the remove list
  Considering myspell-en-us 0 as a solution to hunspell-en-us 2
  Fixing hunspell-en-us via remove of myspell-en-us
Investigating xserver-xorg-video-openchrome
Package xserver-xorg-video-openchrome has broken dep on libchromexvmc1
  Considering libchromexvmc1 -1 as a solution to xserver-xorg-video-openchrome 2
  Added libchromexvmc1 to the remove list
Package xserver-xorg-video-openchrome has broken dep on libchromexvmcpro1
  Considering libchromexvmcpro1 -1 as a solution to xserver-xorg-video-openchrome 2
  Added libchromexvmcpro1 to the remove list
  Fixing xserver-xorg-video-openchrome via remove of libchromexvmc1
  Fixing xserver-xorg-video-openchrome via remove of libchromexvmcpro1
Investigating human-theme
Package human-theme has broken dep on gtk2-engines-ubuntulooks
  Considering gtk2-engines-ubuntulooks 0 as a solution to human-theme 2
  Added gtk2-engines-ubuntulooks to the remove list
  Fixing human-theme via remove of gtk2-engines-ubuntulooks
Investigating pidgin
Package pidgin has broken dep on libpurple0
  Considering libpurple0 3 as a solution to pidgin 2
  Removing pidgin rather than change libpurple0
Investigating libgnomekbd2
Package libgnomekbd2 has broken dep on libgnomekbd-common
  Considering libgnomekbd-common 6 as a solution to libgnomekbd2 1
  Removing libgnomekbd2 rather than change libgnomekbd-common
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5283 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libgtkhtml-editor-common
Package libgtkhtml-editor-common has broken dep on gtkhtml3.14
  Considering gtkhtml3.14 -1 as a solution to libgtkhtml-editor-common 1
  Added gtkhtml3.14 to the remove list
  Fixing libgtkhtml-editor-common via remove of gtkhtml3.14
Investigating libbinio1ldbl
Package libbinio1ldbl has broken dep on libbinio1c2
  Considering libbinio1c2 -1 as a solution to libbinio1ldbl 0
  Added libbinio1c2 to the remove list
  Fixing libbinio1ldbl via remove of libbinio1c2
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on rarian-compat
  Considering rarian-compat 25 as a solution to ubuntu-desktop 0
  Holding Back ubuntu-desktop rather than change rarian-compat
Investigating libhd14
Package libhd14 has broken dep on libhd13
  Considering libhd13 -1 as a solution to libhd14 0
  Added libhd13 to the remove list
  Fixing libhd14 via remove of libhd13
Investigating pidgin-mpris
Package pidgin-mpris has broken dep on libpurple0
  Considering libpurple0 3 as a solution to pidgin-mpris 0
  Removing pidgin-mpris rather than change libpurple0
Investigating pidgin-otr
Package pidgin-otr has broken dep on pidgin
  Considering pidgin 2 as a solution to pidgin-otr 0
  Removing pidgin-otr rather than change pidgin
Investigating landscape-common
Package landscape-common has broken dep on python-smartpm
Investigating libgail-common
Package libgail-common has broken dep on libgail18
  Considering libgail18 1 as a solution to libgail-common -1
  Removing libgail-common rather than change libgail18
Investigating libgdl-gnome-1-0
Package libgdl-gnome-1-0 has broken dep on libgdl-1-common
  Considering libgdl-1-common 5 as a solution to libgdl-gnome-1-0 -1
  Removing libgdl-gnome-1-0 rather than change libgdl-1-common
Investigating libffi4
Package libffi4 has broken dep on gcc-4.2-base
  Considering gcc-4.2-base 10 as a solution to libffi4 -1
  Removing libffi4 rather than change gcc-4.2-base
Investigating libgnomekbdui2
Package libgnomekbdui2 has broken dep on libgnomekbd2
  Considering libgnomekbd2 1 as a solution to libgnomekbdui2 -1
  Removing libgnomekbdui2 rather than change libgnomekbd2
Investigating libltdl7-dev
Package libltdl7-dev has broken dep on libltdl3-dev
  Considering libltdl3-dev -1 as a solution to libltdl7-dev -1
  Holding Back libltdl7-dev rather than change libltdl3-dev
 Try to Re-Instate ubuntu-desktop
Investigating landscape-client
Package landscape-client has broken dep on landscape-common
  Considering landscape-common 0 as a solution to landscape-client 0
  Holding Back landscape-client rather than change landscape-common
 Try to Re-Instate landscape-client
Done
Installing python2.4 as dep of python2.4-minimal
Starting
Starting 2
Investigating landscape-common
Package landscape-common has broken dep on python-smartpm
Done
Log time: 2009-10-17 19:02:49.331152
Log time: 2009-10-17 19:03:36.771402
Log time: 2009-10-17 19:04:11.035961
Log time: 2009-10-17 19:04:53.706600
Installing xserver-xorg-core as dep of xserver-xorg
Installing xserver-common as dep of xserver-xorg-core
Installing libpciaccess0 as dep of xserver-xorg-core
new important dependency: libgl1-mesa-dri
Installing libgl1-mesa-dri as dep of xserver-xorg-core
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing libxi6 as dep of xserver-xorg-input-synaptics
Installing libcanberra-gtk0 as dep of gnome-control-center
Installing libcanberra0 as dep of libcanberra-gtk0
Installing libasound2 as dep of libcanberra0
Installing libltdl7 as dep of libcanberra0
Installing libgtk2.0-0 as dep of libcanberra-gtk0
Installing libcups2 as dep of libgtk2.0-0
Installing libgnutls26 as dep of libcups2
Installing libc6 as dep of libgnutls26
Installing findutils as dep of libc6
Installing libgcrypt11 as dep of libgnutls26
Installing libglib2.0-0 as dep of libgtk2.0-0
Installing libselinux1 as dep of libglib2.0-0
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libcairo2 as dep of libpango1.0-0
Installing libpixman-1-0 as dep of libcairo2
Installing libxcb-render-util0 as dep of libcairo2
Installing libxcb-render0 as dep of libxcb-render-util0
Installing libcanberra-gtk-module as dep of libcanberra-gtk0
Installing libebook1.2-9 as dep of gnome-control-center
Installing libcamel1.2-14 as dep of libebook1.2-9
Installing libedataserver1.2-11 as dep of libcamel1.2-14
Installing libsoup2.4-1 as dep of libedataserver1.2-11
Installing libsqlite3-0 as dep of libcamel1.2-14
Installing libpopt0 as dep of libebook1.2-9
Installing libgnome-desktop-2-7 as dep of gnome-control-center
Installing libgnomekbd3 as dep of gnome-settings-daemon
Installing libxklavier12 as dep of libgnomekbd3
Installing libgnomekbd-common as dep of libgnomekbd3
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libgnomekbdui3 as dep of gnome-control-center
Installing capplets-data as dep of gnome-control-center
Installing gconf2-common as dep of gnome-control-center
Installing ubuntu-system-service as dep of gnome-control-center
new important dependency: screen-resolution-extra
Installing screen-resolution-extra as dep of gnome-control-center
Installing python-xkit as dep of screen-resolution-extra
new important dependency: bluetooth
Installing bluetooth as dep of bluez-gnome
Installing bluez as dep of bluetooth
Installing libbluetooth3 as dep of bluez
Installing bluez-alsa as dep of bluetooth
Installing bluez-gstreamer as dep of bluetooth
Installing libgp11-0 as dep of gnome-keyring
Installing libglade2.0-cil as dep of f-spot
Installing libglib2.0-cil as dep of libglade2.0-cil
Installing libgtk2.0-cil as dep of libglade2.0-cil
Installing libglitz-glx1 as dep of f-spot
Installing libglitz1 as dep of libglitz-glx1
Installing libgnome-keyring1.0-cil as dep of f-spot
Installing libmono-system-web2.0-cil as dep of f-spot
Installing libmono-system2.0-cil as dep of libmono-system-web2.0-cil
Installing libmono-security2.0-cil as dep of libmono-system2.0-cil
Installing libmono0 as dep of libmono-system2.0-cil
Installing mono-jit as dep of libmono-system2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono2.0-cil as dep of libmono-system-web2.0-cil
Installing libgdiplus as dep of libmono-system-web2.0-cil
Installing gvfs-bin as dep of f-spot
Installing libsane as dep of libsane-dev
Installing libdevmapper1.02.1 as dep of dmsetup
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libsm6 as dep of libsm-dev
Installing libruby1.8 as dep of ruby1.8-dev
Installing gcc-4.3-base as dep of libstdc++6
Installing libgmime2.2-cil as dep of tomboy
Installing libgmime-2.0-2a as dep of libgmime2.2-cil
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing libuuid-perl as dep of doc-base
Installing dpkg as dep of doc-base
Installing libmldbm-perl as dep of doc-base
Installing libfreezethaw-perl as dep of libmldbm-perl
Installing perl-modules as dep of perl
Installing libbz2-1.0 as dep of bzip2
Installing libecal1.2-7 as dep of evolution-webcal
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
Installing libpt-1.10.10 as dep of ekiga
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing libhunspell-1.2-0 as dep of openoffice.org-core
Installing libhyphen0 as dep of openoffice.org-core
Installing libneon27 as dep of openoffice.org-core
Installing libqtcore4 as dep of libqt4-opengl
Installing libqtgui4 as dep of libqt4-opengl
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing cups-common as dep of cupsys-common
Installing compiz-wrapper as dep of compiz-core
Installing update-manager-core as dep of update-manager
Installing python-apt as dep of update-manager-core
Installing apt-utils as dep of python-apt
Installing apt as dep of apt-utils
Installing libdb4.7 as dep of apt-utils
Installing openoffice.org-base-core as dep of openoffice.org-writer
new important dependency: openoffice.org-emailmerge
Installing openoffice.org-emailmerge as dep of openoffice.org-writer
Installing libqt4-network as dep of libqt4-assistant
Installing gnome-media-common as dep of gnome-media
Installing metacity-common as dep of metacity
Installing libgtkglext1 as dep of libgtk-vnc-1.0-0
Installing libeel2-2 as dep of nautilus
Installing nautilus-data as dep of nautilus
Installing libtasn1-3 as dep of libtasn1-3-dev
Installing libgnome2-common as dep of libgnome2-0
Installing cups as dep of hal-cups-utils
Installing libcupsimage2 as dep of cups
Installing libijs-0.35 as dep of cups
Installing libpoppler3 as dep of cups
Installing cups-client as dep of cups
Installing avahi-utils as dep of cups
Installing python-cupshelpers as dep of hal-cups-utils
Installing python-usb as dep of hal-cups-utils
Installing libbind9-40 as dep of bind9-host
Installing libcap2 as dep of libbind9-40
Installing libdns43 as dep of libbind9-40
Installing libisc44 as dep of libdns43
Installing libisccfg40 as dep of libbind9-40
Installing libisccc40 as dep of libisccfg40
Installing liblwres40 as dep of bind9-host
Installing libatspi1.0-0 as dep of libgail-gnome-module
Installing gimp-help-common as dep of gimp-help-en
Installing openoffice.org-draw as dep of openoffice.org-impress
Installing language-pack-en as dep of language-pack-en-base
Installing libaudclient1 as dep of audacious
Installing audacious-plugins as dep of audacious
Installing libmad0 as dep of audacious-plugins
Installing libneon27-gnutls as dep of audacious-plugins
Installing libaudid3tag1 as dep of audacious
Installing linux-headers-2.6.27-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.27-14 as dep of linux-headers-2.6.27-14-generic
Installing libaspell15 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing xserver-xorg-video-geode as dep of xserver-xorg-video-amd
Installing ruby1.8 as dep of irb1.8
Installing libreadline-ruby1.8 as dep of irb1.8
Installing xserver-xorg-video-apm as dep of xserver-xorg-video-all
Installing xserver-xorg-video-ark as dep of xserver-xorg-video-all
Installing xserver-xorg-video-ati as dep of xserver-xorg-video-all
Installing xserver-xorg-video-r128 as dep of xserver-xorg-video-ati
Installing xserver-xorg-video-mach64 as dep of xserver-xorg-video-ati
Installing xserver-xorg-video-radeon as dep of xserver-xorg-video-ati
Installing xserver-xorg-video-chips as dep of xserver-xorg-video-all
Installing xserver-xorg-video-cirrus as dep of xserver-xorg-video-all
Installing xserver-xorg-video-fbdev as dep of xserver-xorg-video-all
Installing xserver-xorg-video-i128 as dep of xserver-xorg-video-all
Installing xserver-xorg-video-i740 as dep of xserver-xorg-video-all
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
Installing xserver-xorg-video-mga as dep of xserver-xorg-video-all
Installing xserver-xorg-video-neomagic as dep of xserver-xorg-video-all
Installing xserver-xorg-video-nv as dep of xserver-xorg-video-all
Installing xserver-xorg-video-s3 as dep of xserver-xorg-video-all
Installing xserver-xorg-video-savage as dep of xserver-xorg-video-all
Installing xserver-xorg-video-siliconmotion as dep of xserver-xorg-video-all
Installing xserver-xorg-video-sis as dep of xserver-xorg-video-all
Installing xserver-xorg-video-sisusb as dep of xserver-xorg-video-all
Installing xserver-xorg-video-tdfx as dep of xserver-xorg-video-all
Installing xserver-xorg-video-trident as dep of xserver-xorg-video-all
Installing xserver-xorg-video-tseng as dep of xserver-xorg-video-all
Installing xserver-xorg-video-vesa as dep of xserver-xorg-video-all
Installing xserver-xorg-video-openchrome as dep of xserver-xorg-video-all
Installing xserver-xorg-video-voodoo as dep of xserver-xorg-video-all
Installing xserver-xorg-video-vmware as dep of xserver-xorg-video-all
Installing xserver-xorg-video-v4l as dep of xserver-xorg-video-all
Installing xsane-common as dep of xsane
Installing libgsf-1-114 as dep of tracker
Installing libgsf-1-common as dep of libgsf-1-114
Installing libpoppler-glib3 as dep of tracker
Installing libcups2-dev as dep of libcupsimage2-dev
Installing libsnmp-base as dep of libsnmp15
Installing libperl5.10 as dep of libsnmp15
Installing myspell-en-au as dep of language-support-writing-en
Installing hunspell-en-us as dep of language-support-writing-en
Installing samba-common as dep of smbclient
Installing libtalloc1 as dep of samba-common
Installing libwbclient0 as dep of samba-common
Installing foomatic-filters as dep of pxljr
Installing libgucharmap7 as dep of gucharmap
Installing libgpm2 as dep of brltty-x11
Installing brltty as dep of brltty-x11
Installing libnm-glib0 as dep of network-manager
Installing libnm-util0 as dep of libnm-glib0
new important dependency: libmbca0
Installing libmbca0 as dep of network-manager-gnome
Installing libgweather1 as dep of libmbca0
Installing mobile-broadband-provider-info as dep of libmbca0
Installing wpasupplicant as dep of network-manager
Installing libpcsclite1 as dep of wpasupplicant
Installing guile-1.8-libs as dep of gnome-games
Installing libggz2 as dep of gnome-games
Installing libggzcore9 as dep of gnome-games
Installing libggzmod4 as dep of gnome-games
Installing gnome-games-data as dep of gnome-games
Installing gnome-cards-data as dep of gnome-games-data
Installing gdebi-core as dep of gdebi
Installing evolution as dep of evolution-exchange
Installing libebackend1.2-0 as dep of evolution
Installing libedataserverui1.2-8 as dep of evolution
Installing libegroupwise1.2-13 as dep of evolution
Installing libexchange-storage1.2-3 as dep of evolution
Installing libgdata-google1.2-1 as dep of evolution
Installing libgdata1.2-1 as dep of libgdata-google1.2-1
Installing libgtkhtml-editor0 as dep of evolution
Installing libgtkhtml3.14-19 as dep of libgtkhtml-editor0
Installing libgtkhtml-editor-common as dep of libgtkhtml-editor0
Installing evolution-data-server as dep of evolution
Installing libedata-book1.2-2 as dep of evolution-data-server
Installing libedata-cal1.2-6 as dep of evolution-data-server
Installing evolution-data-server-common as dep of evolution-data-server
Installing libasound2-plugins as dep of pulseaudio
Installing libboost-iostreams1.34.1 as dep of wesnoth
Installing wesnoth-data as dep of wesnoth
Installing gcc-4.2-base as dep of g++-4.2
Installing gcc-4.2 as dep of g++-4.2
Installing cpp-4.2 as dep of gcc-4.2
Installing libgcc1 as dep of gcc-4.2
Installing libstdc++6-4.2-dev as dep of g++-4.2
Installing libcairomm-1.0-1 as dep of gparted
Installing libglibmm-2.4-1c2a as dep of gparted
Installing libgtkmm-2.4-1c2a as dep of gparted
Installing libpangomm-1.4-1 as dep of libgtkmm-2.4-1c2a
Installing libparted1.8-9 as dep of gparted
Installing totem-gstreamer as dep of totem-plugins
Installing libtotem-plparser12 as dep of totem-gstreamer
Installing totem-common as dep of totem-gstreamer
Installing python-rdflib as dep of totem-plugins
Installing python-pkg-resources as dep of python-rdflib
Installing python-gobject as dep of totem-plugins
Installing python2.5 as dep of python-gobject
Installing python2.5-minimal as dep of python2.5
Installing libffi5 as dep of python-gobject
Installing python-gtk2 as dep of totem-plugins
Installing linux-image-2.6.27-14-generic as dep of linux-image-generic
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing linux-firmware as dep of linux-image-generic
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libqt4-xml as dep of libqt4-dbus
Installing libmtp8 as dep of rhythmbox
Installing libmp3lame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libgmp3c2 as dep of libgmp3-dev
Installing libgmpxx4ldbl as dep of libgmp3-dev
Installing libdjvulibre21 as dep of libmagick10
Installing libgraphviz4 as dep of libmagick10
Installing libgd2-noxpm as dep of libgraphviz4
Installing libilmbase6 as dep of libmagick10
Installing libopenexr6 as dep of libmagick10
Installing libggi2 as dep of mplayer
Installing libglide2 as dep of libggi2
Installing libopenal1 as dep of mplayer
Installing libspeex1 as dep of mplayer
Installing libx264-59 as dep of mplayer
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing libsasl2-2 as dep of libsasl2-modules
Installing openssl as dep of openssl-blacklist
Installing python-imaging as dep of python-imaging-tk
Installing esound-common as dep of libesd-alsa0
Installing gtk2-engines as dep of gnome-themes
Installing libcryptui0 as dep of seahorse
Installing libgpgme11 as dep of seahorse
new important dependency: seahorse-plugins
Installing seahorse-plugins as dep of seahorse
Installing cups-bsd as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing cups-driver-gutenprint as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libgutenprint2 as dep of cups-driver-gutenprint
Installing gstreamer0.10-schroedinger as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libcanberra-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libpam-ck-connector as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing rarian-compat as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing xml-core as dep of rarian-compat
new important dependency: gdm-guest-session
Installing gdm-guest-session as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing gdm as dep of gdm-guest-session
new important dependency: usb-creator
Installing usb-creator as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing syslinux as dep of usb-creator
Installing mtools as dep of syslinux
Installing libept0 as dep of aptitude
Installing libxapian15 as dep of libept0
Installing libqt4-script as dep of libqt4-core
Installing libxerces-c28 as dep of libxalan110
Installing fontconfig-config as dep of libfontconfig1
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libghc6-x11-dev as dep of libghc6-hgl-dev
Installing libxinerama-dev as dep of libghc6-x11-dev
Installing libxext-dev as dep of libxinerama-dev
Installing libxext6 as dep of libxext-dev
Installing x11proto-xext-dev as dep of libxext-dev
Installing libxinerama1 as dep of libxinerama-dev
Installing x11proto-xinerama-dev as dep of libxinerama-dev
Installing libavahi-gobject0 as dep of vinagre
Installing scim-gtk2-immodule as dep of scim
Installing libxdmcp6 as dep of libxdmcp-dev
Installing libkrb53 as dep of libkrb5-dev
Installing libkadm55 as dep of libkrb5-dev
Installing cpp as dep of g++
Installing cpp-4.3 as dep of cpp
Installing libmpfr1ldbl as dep of cpp-4.3
Installing gcc as dep of g++
Installing gcc-4.3 as dep of gcc
Installing g++-4.3 as dep of g++
Installing libstdc++6-4.3-dev as dep of g++-4.3
Installing libwww-perl as dep of librpc-xml-perl
Installing libtag1c2a as dep of gstreamer0.10-plugins-good
Installing libv4l-0 as dep of gstreamer0.10-plugins-good
Installing libvte9 as dep of gnome-terminal
Installing gnome-terminal-data as dep of gnome-terminal
Installing openoffice.org-common as dep of openoffice.org-style-human
Installing e2fslibs as dep of e2fsprogs
Installing libpng12-0 as dep of libpng12-dev
Installing libpci3 as dep of toshset
Installing libpolkit2 as dep of policykit
Installing upstart as dep of upstart-compat-sysv
Installing sysvinit-utils as dep of upstart
Installing libsepol1 as dep of sysvinit-utils
Installing libhd14 as dep of hwinfo
Installing libssl0.9.8 as dep of openssh-client
Installing libts-0.0-0 as dep of libdirectfb-1.0-0
new important dependency: nvidia-common
Installing nvidia-common as dep of jockey-common
Installing nvidia-177-modaliases as dep of nvidia-common
Installing nvidia-173-modaliases as dep of nvidia-common
Installing nvidia-96-modaliases as dep of nvidia-common
Installing nvidia-71-modaliases as dep of nvidia-common
Installing nvidia-180-modaliases as dep of nvidia-common
new important dependency: fglrx-modaliases
Installing fglrx-modaliases as dep of jockey-common
new important dependency: libltdl7-dev
Installing libltdl7-dev as dep of libtool
Installing libpolkit-dbus2 as dep of libgconf2-4
Installing at-spi as dep of python-pyatspi
Installing libavcodec51 as dep of gstreamer0.10-ffmpeg
Installing libavutil49 as dep of libavcodec51
Installing libavformat52 as dep of gstreamer0.10-ffmpeg
Installing libpostproc51 as dep of gstreamer0.10-ffmpeg
Installing firefox-3.0-branding as dep of firefox
Installing firefox-3.0 as dep of firefox-3.0-branding
Installing libexif12 as dep of libexif-dev
Installing libftgl2 as dep of chromium
Installing ttf-uralic as dep of chromium
Installing python-compizconfig as dep of compizconfig-settings-manager
Installing libqt4-svg as dep of libqt4-gui
Installing libqt4-designer as dep of libqt4-gui
Installing ghc6 as dep of ghc6-prof
Installing libsmbios2 as dep of hal
Installing libelf1 as dep of bug-buddy
Installing language-selector-common as dep of language-selector
new important dependency: libavcodec-unstripped-51
Installing libavcodec-unstripped-51 as dep of ubuntu-restricted-extras
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing wesnoth-tsg as dep of wesnoth-all
Installing wesnoth-trow as dep of wesnoth-all
Installing wesnoth-ttb as dep of wesnoth-all
Installing wesnoth-ei as dep of wesnoth-all
Installing wesnoth-utbs as dep of wesnoth-all
Installing wesnoth-did as dep of wesnoth-all
Installing wesnoth-nr as dep of wesnoth-all
Installing wesnoth-sof as dep of wesnoth-all
Installing wesnoth-l as dep of wesnoth-all
Installing wesnoth-aoi as dep of wesnoth-all
Installing kbd as dep of ubuntu-minimal
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libbonobo2-common as dep of libbonobo2-0
Installing libspectre1 as dep of evince
Installing zlib1g as dep of zlib1g-dev
Installing libmagic1 as dep of file
Installing libxi-dev as dep of x11proto-input-dev
Installing libtiff4 as dep of libtiff4-dev
Installing libtiffxx0c2 as dep of libtiff4-dev
Installing libspeexdsp1 as dep of libopal-2.2
Installing python-pycurl as dep of landscape-client
Installing python-twisted-web as dep of landscape-client
Installing python-twisted-core as dep of python-twisted-web
Installing python-twisted-bin as dep of python-twisted-core
Installing python-zopeinterface as dep of python-twisted-core
Installing python-pyopenssl as dep of python-twisted-core
Installing python-openssl as dep of python-pyopenssl
Installing python-pam as dep of python-twisted-core
Installing python-serial as dep of python-twisted-core
Installing landscape-common as dep of landscape-client
Installing update-motd as dep of landscape-common
Installing libdc1394-22 as dep of gstreamer0.10-plugins-bad
Installing libofa0 as dep of gstreamer0.10-plugins-bad
Installing libfftw3-3 as dep of libofa0
Installing iptables as dep of ufw
Installing libgimp2.0 as dep of gimp
Installing gimp-data as dep of gimp
Installing libbabl-0.0-0 as dep of gimp
Installing libgegl-0.0-0 as dep of gimp
Installing libbinio1ldbl as dep of audacious-plugins-extra
Installing libmikmod2 as dep of libsdl-mixer1.2
Installing imagemagick as dep of devede
new important dependency: apt-xapian-index
Installing apt-xapian-index as dep of synaptic
Installing python-xapian as dep of apt-xapian-index
Installing python-debian as dep of apt-xapian-index
Installing gnome-applets-data as dep of gnome-applets
Installing xinput as dep of xorg
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-i810
new important dependency: lockfile-progs
Installing lockfile-progs as dep of ntpdate
Installing liblockfile1 as dep of lockfile-progs
Installing linux-restricted-modules-2.6.27-14-generic as dep of linux-restricted-modules-generic
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libbrasero-media0 as dep of brasero
Installing libapparmor-perl as dep of apparmor-utils
Installing libapparmor1 as dep of libapparmor-perl
Installing gnome-panel-data as dep of gnome-panel
Installing libswscale0 as dep of libquicktime1
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libgdl-1-common as dep of libgdl-1-0
Starting
Starting 2
Investigating libgtk2.0-0
Package libgtk2.0-0 has broken dep on libgail18
  Considering libgail18 1 as a solution to libgtk2.0-0 850
  Added libgail18 to the remove list
  Fixing libgtk2.0-0 via remove of libgail18
Investigating xserver-xorg-core
Package xserver-xorg-core has broken dep on xserver-xorg-video-2
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-siliconmotion 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-ati 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-i740 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-geode 3 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-via -1 as a solution to xserver-xorg-core 90
  Added xserver-xorg-video-via to the remove list
  Considering xserver-xorg-video-nv 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-i810 0 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-intel 3 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-chips 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-tga 0 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-trident 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-s3 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-vga 0 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-i128 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-mga 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-nsc 0 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-newport -1 as a solution to xserver-xorg-core 90
  Added xserver-xorg-video-newport to the remove list
  Considering xserver-xorg-video-neomagic 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-cirrus 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-ark 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-tdfx 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-sisusb 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-dummy 0 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-rendition 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-vesa 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-cyrix -1 as a solution to xserver-xorg-core 90
  Added xserver-xorg-video-cyrix to the remove list
  Considering xserver-xorg-video-imstt -1 as a solution to xserver-xorg-core 90
  Added xserver-xorg-video-imstt to the remove list
  Considering xserver-xorg-video-glint 0 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-fbdev 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-savage 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-vmware 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-openchrome 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-s3virge 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-voodoo 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-apm 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-sis 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-v4l 2 as a solution to xserver-xorg-core 90
Package xserver-xorg-core has broken dep on xserver-xorg-video-psb
  Considering xserver-xorg-video-psb -1 as a solution to xserver-xorg-core 90
  Added xserver-xorg-video-psb to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-via
  Fixing xserver-xorg-core via remove of xserver-xorg-video-newport
  Fixing xserver-xorg-core via remove of xserver-xorg-video-cyrix
  Fixing xserver-xorg-core via remove of xserver-xorg-video-imstt
  Fixing xserver-xorg-core via remove of xserver-xorg-video-psb
Investigating rarian-compat
Package rarian-compat has broken dep on scrollkeeper
  Considering scrollkeeper 37 as a solution to rarian-compat 25
  Holding Back rarian-compat rather than change scrollkeeper
Investigating kbd
Package kbd has broken dep on console-utilities
  Considering console-tools 12 as a solution to kbd 22
  Considering console-tools 12 as a solution to kbd 22
  Added console-tools to the remove list
Package kbd has broken dep on open
  Considering console-tools 12 as a solution to kbd 22
  Considering console-tools 12 as a solution to kbd 22
  Added console-tools to the remove list
  Fixing kbd via remove of console-tools
  Fixing kbd via remove of console-tools
Investigating gimp-data
Package gimp-data has broken dep on gimp-python
  Considering gimp-python -1 as a solution to gimp-data 6
  Added gimp-python to the remove list
  Fixing gimp-data via remove of gimp-python
Investigating libmp3lame0
Package libmp3lame0 has broken dep on liblame0
  Considering liblame0 -1 as a solution to libmp3lame0 5
  Added liblame0 to the remove list
  Fixing libmp3lame0 via remove of liblame0
Investigating gimp
Package gimp has broken dep on gimp-gnomevfs
  Considering gimp-gnomevfs -1 as a solution to gimp 4
  Added gimp-gnomevfs to the remove list
  Fixing gimp via remove of gimp-gnomevfs
Investigating libgmime-2.0-2a
Package libgmime-2.0-2a has broken dep on libgmime-2.0-2
  Considering libgmime-2.0-2 -1 as a solution to libgmime-2.0-2a 4
  Added libgmime-2.0-2 to the remove list
  Fixing libgmime-2.0-2a via remove of libgmime-2.0-2
Investigating libpurple0
Package libpurple0 has broken dep on perlapi-5.8.8
  Considering perl-base 5283 as a solution to libpurple0 3
  Removing libpurple0 rather than change perlapi-5.8.8
Investigating hunspell-en-us
Package hunspell-en-us has broken dep on myspell-en-us
  Considering myspell-en-us 0 as a solution to hunspell-en-us 2
  Added myspell-en-us to the remove list
  Considering myspell-en-us 0 as a solution to hunspell-en-us 2
  Fixing hunspell-en-us via remove of myspell-en-us
Investigating xserver-xorg-video-openchrome
Package xserver-xorg-video-openchrome has broken dep on libchromexvmc1
  Considering libchromexvmc1 -1 as a solution to xserver-xorg-video-openchrome 2
  Added libchromexvmc1 to the remove list
Package xserver-xorg-video-openchrome has broken dep on libchromexvmcpro1
  Considering libchromexvmcpro1 -1 as a solution to xserver-xorg-video-openchrome 2
  Added libchromexvmcpro1 to the remove list
  Fixing xserver-xorg-video-openchrome via remove of libchromexvmc1
  Fixing xserver-xorg-video-openchrome via remove of libchromexvmcpro1
Investigating human-theme
Package human-theme has broken dep on gtk2-engines-ubuntulooks
  Considering gtk2-engines-ubuntulooks 0 as a solution to human-theme 2
  Added gtk2-engines-ubuntulooks to the remove list
  Fixing human-theme via remove of gtk2-engines-ubuntulooks
Investigating pidgin
Package pidgin has broken dep on libpurple0
  Considering libpurple0 3 as a solution to pidgin 2
  Removing pidgin rather than change libpurple0
Investigating libgnomekbd2
Package libgnomekbd2 has broken dep on libgnomekbd-common
  Considering libgnomekbd-common 6 as a solution to libgnomekbd2 1
  Removing libgnomekbd2 rather than change libgnomekbd-common
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5283 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libgtkhtml-editor-common
Package libgtkhtml-editor-common has broken dep on gtkhtml3.14
  Considering gtkhtml3.14 -1 as a solution to libgtkhtml-editor-common 1
  Added gtkhtml3.14 to the remove list
  Fixing libgtkhtml-editor-common via remove of gtkhtml3.14
Investigating libbinio1ldbl
Package libbinio1ldbl has broken dep on libbinio1c2
  Considering libbinio1c2 -1 as a solution to libbinio1ldbl 0
  Added libbinio1c2 to the remove list
  Fixing libbinio1ldbl via remove of libbinio1c2
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on rarian-compat
  Considering rarian-compat 25 as a solution to ubuntu-desktop 0
  Holding Back ubuntu-desktop rather than change rarian-compat
Investigating libhd14
Package libhd14 has broken dep on libhd13
  Considering libhd13 -1 as a solution to libhd14 0
  Added libhd13 to the remove list
  Fixing libhd14 via remove of libhd13
Investigating pidgin-mpris
Package pidgin-mpris has broken dep on libpurple0
  Considering libpurple0 3 as a solution to pidgin-mpris 0
  Removing pidgin-mpris rather than change libpurple0
Investigating pidgin-otr
Package pidgin-otr has broken dep on pidgin
  Considering pidgin 2 as a solution to pidgin-otr 0
  Removing pidgin-otr rather than change pidgin
Investigating landscape-common
Package landscape-common has broken dep on python-smartpm
Investigating libgail-common
Package libgail-common has broken dep on libgail18
  Considering libgail18 1 as a solution to libgail-common -1
  Removing libgail-common rather than change libgail18
Investigating libgdl-gnome-1-0
Package libgdl-gnome-1-0 has broken dep on libgdl-1-common
  Considering libgdl-1-common 5 as a solution to libgdl-gnome-1-0 -1
  Removing libgdl-gnome-1-0 rather than change libgdl-1-common
Investigating libffi4
Package libffi4 has broken dep on gcc-4.2-base
  Considering gcc-4.2-base 10 as a solution to libffi4 -1
  Removing libffi4 rather than change gcc-4.2-base
Investigating libgnomekbdui2
Package libgnomekbdui2 has broken dep on libgnomekbd2
  Considering libgnomekbd2 1 as a solution to libgnomekbdui2 -1
  Removing libgnomekbdui2 rather than change libgnomekbd2
Investigating libltdl7-dev
Package libltdl7-dev has broken dep on libltdl3-dev
  Considering libltdl3-dev -1 as a solution to libltdl7-dev -1
  Holding Back libltdl7-dev rather than change libltdl3-dev
 Try to Re-Instate ubuntu-desktop
Investigating landscape-client
Package landscape-client has broken dep on landscape-common
  Considering landscape-common 0 as a solution to landscape-client 0
  Holding Back landscape-client rather than change landscape-common
 Try to Re-Instate landscape-client
Done
Installing python2.4 as dep of python2.4-minimal
Starting
Starting 2
Investigating landscape-common
Package landscape-common has broken dep on python-smartpm
Done
Log time: 2009-10-17 19:05:27.861047
Log time: 2009-10-17 19:11:19.177203
Log time: 2009-10-17 19:11:55.691782
Log time: 2009-10-17 19:27:39.381031
Installing xserver-xorg-core as dep of xserver-xorg
Installing xserver-common as dep of xserver-xorg-core
Installing libpciaccess0 as dep of xserver-xorg-core
new important dependency: libgl1-mesa-dri
Installing libgl1-mesa-dri as dep of xserver-xorg-core
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing libxi6 as dep of xserver-xorg-input-synaptics
Installing libcanberra-gtk0 as dep of gnome-control-center
Installing libcanberra0 as dep of libcanberra-gtk0
Installing libasound2 as dep of libcanberra0
Installing libltdl7 as dep of libcanberra0
Installing libgtk2.0-0 as dep of libcanberra-gtk0
Installing libcups2 as dep of libgtk2.0-0
Installing libgnutls26 as dep of libcups2
Installing libc6 as dep of libgnutls26
Installing findutils as dep of libc6
Installing libgcrypt11 as dep of libgnutls26
Installing libglib2.0-0 as dep of libgtk2.0-0
Installing libselinux1 as dep of libglib2.0-0
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libcairo2 as dep of libpango1.0-0
Installing libpixman-1-0 as dep of libcairo2
Installing libxcb-render-util0 as dep of libcairo2
Installing libxcb-render0 as dep of libxcb-render-util0
Installing libcanberra-gtk-module as dep of libcanberra-gtk0
Installing libebook1.2-9 as dep of gnome-control-center
Installing libcamel1.2-14 as dep of libebook1.2-9
Installing libedataserver1.2-11 as dep of libcamel1.2-14
Installing libsoup2.4-1 as dep of libedataserver1.2-11
Installing libsqlite3-0 as dep of libcamel1.2-14
Installing libpopt0 as dep of libebook1.2-9
Installing libgnome-desktop-2-7 as dep of gnome-control-center
Installing libgnomekbd3 as dep of gnome-settings-daemon
Installing libxklavier12 as dep of libgnomekbd3
Installing libgnomekbd-common as dep of libgnomekbd3
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libgnomekbdui3 as dep of gnome-control-center
Installing capplets-data as dep of gnome-control-center
Installing gconf2-common as dep of gnome-control-center
Installing ubuntu-system-service as dep of gnome-control-center
new important dependency: screen-resolution-extra
Installing screen-resolution-extra as dep of gnome-control-center
Installing python-xkit as dep of screen-resolution-extra
new important dependency: bluetooth
Installing bluetooth as dep of bluez-gnome
Installing bluez as dep of bluetooth
Installing libbluetooth3 as dep of bluez
Installing bluez-alsa as dep of bluetooth
Installing bluez-gstreamer as dep of bluetooth
Installing libgp11-0 as dep of gnome-keyring
Installing libglade2.0-cil as dep of f-spot
Installing libglib2.0-cil as dep of libglade2.0-cil
Installing libgtk2.0-cil as dep of libglade2.0-cil
Installing libglitz-glx1 as dep of f-spot
Installing libglitz1 as dep of libglitz-glx1
Installing libgnome-keyring1.0-cil as dep of f-spot
Installing libmono-system-web2.0-cil as dep of f-spot
Installing libmono-system2.0-cil as dep of libmono-system-web2.0-cil
Installing libmono-security2.0-cil as dep of libmono-system2.0-cil
Installing libmono0 as dep of libmono-system2.0-cil
Installing mono-jit as dep of libmono-system2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono2.0-cil as dep of libmono-system-web2.0-cil
Installing libgdiplus as dep of libmono-system-web2.0-cil
Installing gvfs-bin as dep of f-spot
Installing libsane as dep of libsane-dev
Installing libdevmapper1.02.1 as dep of dmsetup
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libsm6 as dep of libsm-dev
Installing libruby1.8 as dep of ruby1.8-dev
Installing gcc-4.3-base as dep of libstdc++6
Installing libgmime2.2-cil as dep of tomboy
Installing libgmime-2.0-2a as dep of libgmime2.2-cil
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing libuuid-perl as dep of doc-base
Installing dpkg as dep of doc-base
Installing libmldbm-perl as dep of doc-base
Installing libfreezethaw-perl as dep of libmldbm-perl
Installing perl-modules as dep of perl
Installing libbz2-1.0 as dep of bzip2
Installing libecal1.2-7 as dep of evolution-webcal
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
Installing libpt-1.10.10 as dep of ekiga
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing libhunspell-1.2-0 as dep of openoffice.org-core
Installing libhyphen0 as dep of openoffice.org-core
Installing libneon27 as dep of openoffice.org-core
Installing libqtcore4 as dep of libqt4-opengl
Installing libqtgui4 as dep of libqt4-opengl
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing cups-common as dep of cupsys-common
Installing compiz-wrapper as dep of compiz-core
Installing update-manager-core as dep of update-manager
Installing python-apt as dep of update-manager-core
Installing apt-utils as dep of python-apt
Installing apt as dep of apt-utils
Installing libdb4.7 as dep of apt-utils
Installing openoffice.org-base-core as dep of openoffice.org-writer
new important dependency: openoffice.org-emailmerge
Installing openoffice.org-emailmerge as dep of openoffice.org-writer
Installing libqt4-network as dep of libqt4-assistant
Installing gnome-media-common as dep of gnome-media
Installing metacity-common as dep of metacity
Installing libgtkglext1 as dep of libgtk-vnc-1.0-0
Installing libeel2-2 as dep of nautilus
Installing nautilus-data as dep of nautilus
Installing libtasn1-3 as dep of libtasn1-3-dev
Installing libgnome2-common as dep of libgnome2-0
Installing cups as dep of hal-cups-utils
Installing libcupsimage2 as dep of cups
Installing libijs-0.35 as dep of cups
Installing libpoppler3 as dep of cups
Installing cups-client as dep of cups
Installing avahi-utils as dep of cups
Installing python-cupshelpers as dep of hal-cups-utils
Installing python-usb as dep of hal-cups-utils
Installing libbind9-40 as dep of bind9-host
Installing libcap2 as dep of libbind9-40
Installing libdns43 as dep of libbind9-40
Installing libisc44 as dep of libdns43
Installing libisccfg40 as dep of libbind9-40
Installing libisccc40 as dep of libisccfg40
Installing liblwres40 as dep of bind9-host
Installing libatspi1.0-0 as dep of libgail-gnome-module
Installing gimp-help-common as dep of gimp-help-en
Installing openoffice.org-draw as dep of openoffice.org-impress
Installing language-pack-en as dep of language-pack-en-base
Installing libaudclient1 as dep of audacious
Installing audacious-plugins as dep of audacious
Installing libmad0 as dep of audacious-plugins
Installing libneon27-gnutls as dep of audacious-plugins
Installing libaudid3tag1 as dep of audacious
Installing linux-headers-2.6.27-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.27-14 as dep of linux-headers-2.6.27-14-generic
Installing libaspell15 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing xserver-xorg-video-geode as dep of xserver-xorg-video-amd
Installing ruby1.8 as dep of irb1.8
Installing libreadline-ruby1.8 as dep of irb1.8
Installing xserver-xorg-video-apm as dep of xserver-xorg-video-all
Installing xserver-xorg-video-ark as dep of xserver-xorg-video-all
Installing xserver-xorg-video-ati as dep of xserver-xorg-video-all
Installing xserver-xorg-video-r128 as dep of xserver-xorg-video-ati
Installing xserver-xorg-video-mach64 as dep of xserver-xorg-video-ati
Installing xserver-xorg-video-radeon as dep of xserver-xorg-video-ati
Installing xserver-xorg-video-chips as dep of xserver-xorg-video-all
Installing xserver-xorg-video-cirrus as dep of xserver-xorg-video-all
Installing xserver-xorg-video-fbdev as dep of xserver-xorg-video-all
Installing xserver-xorg-video-i128 as dep of xserver-xorg-video-all
Installing xserver-xorg-video-i740 as dep of xserver-xorg-video-all
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
Installing xserver-xorg-video-mga as dep of xserver-xorg-video-all
Installing xserver-xorg-video-neomagic as dep of xserver-xorg-video-all
Installing xserver-xorg-video-nv as dep of xserver-xorg-video-all
Installing xserver-xorg-video-s3 as dep of xserver-xorg-video-all
Installing xserver-xorg-video-savage as dep of xserver-xorg-video-all
Installing xserver-xorg-video-siliconmotion as dep of xserver-xorg-video-all
Installing xserver-xorg-video-sis as dep of xserver-xorg-video-all
Installing xserver-xorg-video-sisusb as dep of xserver-xorg-video-all
Installing xserver-xorg-video-tdfx as dep of xserver-xorg-video-all
Installing xserver-xorg-video-trident as dep of xserver-xorg-video-all
Installing xserver-xorg-video-tseng as dep of xserver-xorg-video-all
Installing xserver-xorg-video-vesa as dep of xserver-xorg-video-all
Installing xserver-xorg-video-openchrome as dep of xserver-xorg-video-all
Installing xserver-xorg-video-voodoo as dep of xserver-xorg-video-all
Installing xserver-xorg-video-vmware as dep of xserver-xorg-video-all
Installing xserver-xorg-video-v4l as dep of xserver-xorg-video-all
Installing xsane-common as dep of xsane
Installing libgsf-1-114 as dep of tracker
Installing libgsf-1-common as dep of libgsf-1-114
Installing libpoppler-glib3 as dep of tracker
Installing libcups2-dev as dep of libcupsimage2-dev
Installing libsnmp-base as dep of libsnmp15
Installing libperl5.10 as dep of libsnmp15
Installing myspell-en-au as dep of language-support-writing-en
Installing hunspell-en-us as dep of language-support-writing-en
Installing samba-common as dep of smbclient
Installing libtalloc1 as dep of samba-common
Installing libwbclient0 as dep of samba-common
Installing foomatic-filters as dep of pxljr
Installing libgucharmap7 as dep of gucharmap
Installing libgpm2 as dep of brltty-x11
Installing brltty as dep of brltty-x11
Installing libnm-glib0 as dep of network-manager
Installing libnm-util0 as dep of libnm-glib0
new important dependency: libmbca0
Installing libmbca0 as dep of network-manager-gnome
Installing libgweather1 as dep of libmbca0
Installing mobile-broadband-provider-info as dep of libmbca0
Installing wpasupplicant as dep of network-manager
Installing libpcsclite1 as dep of wpasupplicant
Installing guile-1.8-libs as dep of gnome-games
Installing libggz2 as dep of gnome-games
Installing libggzcore9 as dep of gnome-games
Installing libggzmod4 as dep of gnome-games
Installing gnome-games-data as dep of gnome-games
Installing gnome-cards-data as dep of gnome-games-data
Installing gdebi-core as dep of gdebi
Installing evolution as dep of evolution-exchange
Installing libebackend1.2-0 as dep of evolution
Installing libedataserverui1.2-8 as dep of evolution
Installing libegroupwise1.2-13 as dep of evolution
Installing libexchange-storage1.2-3 as dep of evolution
Installing libgdata-google1.2-1 as dep of evolution
Installing libgdata1.2-1 as dep of libgdata-google1.2-1
Installing libgtkhtml-editor0 as dep of evolution
Installing libgtkhtml3.14-19 as dep of libgtkhtml-editor0
Installing libgtkhtml-editor-common as dep of libgtkhtml-editor0
Installing evolution-data-server as dep of evolution
Installing libedata-book1.2-2 as dep of evolution-data-server
Installing libedata-cal1.2-6 as dep of evolution-data-server
Installing evolution-data-server-common as dep of evolution-data-server
Installing libasound2-plugins as dep of pulseaudio
Installing libboost-iostreams1.34.1 as dep of wesnoth
Installing wesnoth-data as dep of wesnoth
Installing gcc-4.2-base as dep of g++-4.2
Installing gcc-4.2 as dep of g++-4.2
Installing cpp-4.2 as dep of gcc-4.2
Installing libgcc1 as dep of gcc-4.2
Installing libstdc++6-4.2-dev as dep of g++-4.2
Installing libcairomm-1.0-1 as dep of gparted
Installing libglibmm-2.4-1c2a as dep of gparted
Installing libgtkmm-2.4-1c2a as dep of gparted
Installing libpangomm-1.4-1 as dep of libgtkmm-2.4-1c2a
Installing libparted1.8-9 as dep of gparted
Installing totem-gstreamer as dep of totem-plugins
Installing libtotem-plparser12 as dep of totem-gstreamer
Installing totem-common as dep of totem-gstreamer
Installing python-rdflib as dep of totem-plugins
Installing python-pkg-resources as dep of python-rdflib
Installing python-gobject as dep of totem-plugins
Installing python2.5 as dep of python-gobject
Installing python2.5-minimal as dep of python2.5
Installing libffi5 as dep of python-gobject
Installing python-gtk2 as dep of totem-plugins
Installing linux-image-2.6.27-14-generic as dep of linux-image-generic
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing linux-firmware as dep of linux-image-generic
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libqt4-xml as dep of libqt4-dbus
Installing libmtp8 as dep of rhythmbox
Installing libmp3lame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libgmp3c2 as dep of libgmp3-dev
Installing libgmpxx4ldbl as dep of libgmp3-dev
Installing libdjvulibre21 as dep of libmagick10
Installing libgraphviz4 as dep of libmagick10
Installing libgd2-noxpm as dep of libgraphviz4
Installing libilmbase6 as dep of libmagick10
Installing libopenexr6 as dep of libmagick10
Installing libggi2 as dep of mplayer
Installing libglide2 as dep of libggi2
Installing libopenal1 as dep of mplayer
Installing libspeex1 as dep of mplayer
Installing libx264-59 as dep of mplayer
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing libsasl2-2 as dep of libsasl2-modules
Installing openssl as dep of openssl-blacklist
Installing python-imaging as dep of python-imaging-tk
Installing esound-common as dep of libesd-alsa0
Installing gtk2-engines as dep of gnome-themes
Installing libcryptui0 as dep of seahorse
Installing libgpgme11 as dep of seahorse
new important dependency: seahorse-plugins
Installing seahorse-plugins as dep of seahorse
Installing cups-bsd as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing cups-driver-gutenprint as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libgutenprint2 as dep of cups-driver-gutenprint
Installing gstreamer0.10-schroedinger as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libcanberra-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libpam-ck-connector as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing rarian-compat as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing xml-core as dep of rarian-compat
new important dependency: gdm-guest-session
Installing gdm-guest-session as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing gdm as dep of gdm-guest-session
new important dependency: usb-creator
Installing usb-creator as dep of ubuntu-desktop
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing syslinux as dep of usb-creator
Installing mtools as dep of syslinux
Installing libept0 as dep of aptitude
Installing libxapian15 as dep of libept0
Installing libqt4-script as dep of libqt4-core
Installing fontconfig-config as dep of libfontconfig1
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libghc6-x11-dev as dep of libghc6-hgl-dev
Installing libxinerama-dev as dep of libghc6-x11-dev
Installing libxext-dev as dep of libxinerama-dev
Installing libxext6 as dep of libxext-dev
Installing x11proto-xext-dev as dep of libxext-dev
Installing libxinerama1 as dep of libxinerama-dev
Installing x11proto-xinerama-dev as dep of libxinerama-dev
Installing libavahi-gobject0 as dep of vinagre
Installing scim-gtk2-immodule as dep of scim
Installing libxdmcp6 as dep of libxdmcp-dev
Installing libkrb53 as dep of libkrb5-dev
Installing libkadm55 as dep of libkrb5-dev
Installing cpp as dep of g++
Installing cpp-4.3 as dep of cpp
Installing libmpfr1ldbl as dep of cpp-4.3
Installing gcc as dep of g++
Installing gcc-4.3 as dep of gcc
Installing g++-4.3 as dep of g++
Installing libstdc++6-4.3-dev as dep of g++-4.3
Installing libwww-perl as dep of librpc-xml-perl
Installing libtag1c2a as dep of gstreamer0.10-plugins-good
Installing libv4l-0 as dep of gstreamer0.10-plugins-good
Installing libvte9 as dep of gnome-terminal
Installing gnome-terminal-data as dep of gnome-terminal
Installing openoffice.org-common as dep of openoffice.org-style-human
Installing e2fslibs as dep of e2fsprogs
Installing libpng12-0 as dep of libpng12-dev
Installing libpci3 as dep of toshset
Installing libpolkit2 as dep of policykit
Installing upstart as dep of upstart-compat-sysv
Installing sysvinit-utils as dep of upstart
Installing libsepol1 as dep of sysvinit-utils
Installing libhd14 as dep of hwinfo
Installing libssl0.9.8 as dep of openssh-client
Installing libts-0.0-0 as dep of libdirectfb-1.0-0
new important dependency: nvidia-common
Installing nvidia-common as dep of jockey-common
Installing nvidia-177-modaliases as dep of nvidia-common
Installing nvidia-173-modaliases as dep of nvidia-common
Installing nvidia-96-modaliases as dep of nvidia-common
Installing nvidia-71-modaliases as dep of nvidia-common
Installing nvidia-180-modaliases as dep of nvidia-common
new important dependency: fglrx-modaliases
Installing fglrx-modaliases as dep of jockey-common
new important dependency: libltdl7-dev
Installing libltdl7-dev as dep of libtool
Installing libpolkit-dbus2 as dep of libgconf2-4
Installing at-spi as dep of python-pyatspi
Installing libavcodec51 as dep of gstreamer0.10-ffmpeg
Installing libavutil49 as dep of libavcodec51
Installing libavformat52 as dep of gstreamer0.10-ffmpeg
Installing libpostproc51 as dep of gstreamer0.10-ffmpeg
Installing firefox-3.0-branding as dep of firefox
Installing firefox-3.0 as dep of firefox-3.0-branding
Installing libexif12 as dep of libexif-dev
Installing libftgl2 as dep of chromium
Installing ttf-uralic as dep of chromium
Installing python-compizconfig as dep of compizconfig-settings-manager
Installing libqt4-svg as dep of libqt4-gui
Installing libqt4-designer as dep of libqt4-gui
Installing ghc6 as dep of ghc6-prof
Installing libsmbios2 as dep of hal
Installing libelf1 as dep of bug-buddy
Installing language-selector-common as dep of language-selector
new important dependency: libavcodec-unstripped-51
Installing libavcodec-unstripped-51 as dep of ubuntu-restricted-extras
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing wesnoth-tsg as dep of wesnoth-all
Installing wesnoth-trow as dep of wesnoth-all
Installing wesnoth-ttb as dep of wesnoth-all
Installing wesnoth-ei as dep of wesnoth-all
Installing wesnoth-utbs as dep of wesnoth-all
Installing wesnoth-did as dep of wesnoth-all
Installing wesnoth-nr as dep of wesnoth-all
Installing wesnoth-sof as dep of wesnoth-all
Installing wesnoth-l as dep of wesnoth-all
Installing wesnoth-aoi as dep of wesnoth-all
Installing kbd as dep of ubuntu-minimal
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libbonobo2-common as dep of libbonobo2-0
Installing libspectre1 as dep of evince
Installing zlib1g as dep of zlib1g-dev
Installing libmagic1 as dep of file
Installing libxi-dev as dep of x11proto-input-dev
Installing libtiff4 as dep of libtiff4-dev
Installing libtiffxx0c2 as dep of libtiff4-dev
Installing libspeexdsp1 as dep of libopal-2.2
Installing python-pycurl as dep of landscape-client
Installing python-twisted-web as dep of landscape-client
Installing python-twisted-core as dep of python-twisted-web
Installing python-twisted-bin as dep of python-twisted-core
Installing python-zopeinterface as dep of python-twisted-core
Installing python-pyopenssl as dep of python-twisted-core
Installing python-openssl as dep of python-pyopenssl
Installing python-pam as dep of python-twisted-core
Installing python-serial as dep of python-twisted-core
Installing landscape-common as dep of landscape-client
Installing update-motd as dep of landscape-common
Installing libdc1394-22 as dep of gstreamer0.10-plugins-bad
Installing libofa0 as dep of gstreamer0.10-plugins-bad
Installing libfftw3-3 as dep of libofa0
Installing iptables as dep of ufw
Installing libgimp2.0 as dep of gimp
Installing gimp-data as dep of gimp
Installing libbabl-0.0-0 as dep of gimp
Installing libgegl-0.0-0 as dep of gimp
Installing libbinio1ldbl as dep of audacious-plugins-extra
Installing libmikmod2 as dep of libsdl-mixer1.2
Installing imagemagick as dep of devede
new important dependency: apt-xapian-index
Installing apt-xapian-index as dep of synaptic
Installing python-xapian as dep of apt-xapian-index
Installing python-debian as dep of apt-xapian-index
Installing gnome-applets-data as dep of gnome-applets
Installing xinput as dep of xorg
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-i810
new important dependency: lockfile-progs
Installing lockfile-progs as dep of ntpdate
Installing liblockfile1 as dep of lockfile-progs
Installing linux-restricted-modules-2.6.27-14-generic as dep of linux-restricted-modules-generic
Setting NOT as auto-installed (direct dep of pkg in APT::Never-MarkAuto-Section)
Installing libbrasero-media0 as dep of brasero
Installing libapparmor-perl as dep of apparmor-utils
Installing libapparmor1 as dep of libapparmor-perl
Installing gnome-panel-data as dep of gnome-panel
Installing libswscale0 as dep of libquicktime1
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libgdl-1-common as dep of libgdl-1-0
Starting
Starting 2
Investigating libgtk2.0-0
Package libgtk2.0-0 has broken dep on libgail18
  Considering libgail18 1 as a solution to libgtk2.0-0 850
  Added libgail18 to the remove list
  Fixing libgtk2.0-0 via remove of libgail18
Investigating xserver-xorg-core
Package xserver-xorg-core has broken dep on xserver-xorg-video-2
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-siliconmotion 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-ati 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-i740 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-geode 3 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-via -1 as a solution to xserver-xorg-core 90
  Added xserver-xorg-video-via to the remove list
  Considering xserver-xorg-video-nv 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-i810 0 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-intel 3 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-chips 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-tga 0 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-trident 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-s3 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-vga 0 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-i128 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-mga 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-nsc 0 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-newport -1 as a solution to xserver-xorg-core 90
  Added xserver-xorg-video-newport to the remove list
  Considering xserver-xorg-video-neomagic 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-cirrus 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-ark 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-tdfx 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-sisusb 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-dummy 0 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-rendition 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-vesa 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-cyrix -1 as a solution to xserver-xorg-core 90
  Added xserver-xorg-video-cyrix to the remove list
  Considering xserver-xorg-video-imstt -1 as a solution to xserver-xorg-core 90
  Added xserver-xorg-video-imstt to the remove list
  Considering xserver-xorg-video-glint 0 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-fbdev 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-savage 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-vmware 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-openchrome 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-s3virge 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-voodoo 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-apm 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-sis 2 as a solution to xserver-xorg-core 90
  Considering xserver-xorg-video-v4l 2 as a solution to xserver-xorg-core 90
Package xserver-xorg-core has broken dep on xserver-xorg-video-psb
  Considering xserver-xorg-video-psb -1 as a solution to xserver-xorg-core 90
  Added xserver-xorg-video-psb to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-via
  Fixing xserver-xorg-core via remove of xserver-xorg-video-newport
  Fixing xserver-xorg-core via remove of xserver-xorg-video-cyrix
  Fixing xserver-xorg-core via remove of xserver-xorg-video-imstt
  Fixing xserver-xorg-core via remove of xserver-xorg-video-psb
Investigating rarian-compat
Package rarian-compat has broken dep on scrollkeeper
  Considering scrollkeeper 37 as a solution to rarian-compat 25
  Holding Back rarian-compat rather than change scrollkeeper
Investigating kbd
Package kbd has broken dep on console-utilities
  Considering console-tools 12 as a solution to kbd 22
  Considering console-tools 12 as a solution to kbd 22
  Added console-tools to the remove list
Package kbd has broken dep on open
  Considering console-tools 12 as a solution to kbd 22
  Considering console-tools 12 as a solution to kbd 22
  Added console-tools to the remove list
  Fixing kbd via remove of console-tools
  Fixing kbd via remove of console-tools
Investigating gimp-data
Package gimp-data has broken dep on gimp-python
  Considering gimp-python -1 as a solution to gimp-data 6
  Added gimp-python to the remove list
  Fixing gimp-data via remove of gimp-python
Investigating libmp3lame0
Package libmp3lame0 has broken dep on liblame0
  Considering liblame0 -1 as a solution to libmp3lame0 5
  Added liblame0 to the remove list
  Fixing libmp3lame0 via remove of liblame0
Investigating gimp
Package gimp has broken dep on gimp-gnomevfs
  Considering gimp-gnomevfs -1 as a solution to gimp 4
  Added gimp-gnomevfs to the remove list
  Fixing gimp via remove of gimp-gnomevfs
Investigating libgmime-2.0-2a
Package libgmime-2.0-2a has broken dep on libgmime-2.0-2
  Considering libgmime-2.0-2 -1 as a solution to libgmime-2.0-2a 4
  Added libgmime-2.0-2 to the remove list
  Fixing libgmime-2.0-2a via remove of libgmime-2.0-2
Investigating libpurple0
Package libpurple0 has broken dep on perlapi-5.8.8
  Considering perl-base 5283 as a solution to libpurple0 3
  Removing libpurple0 rather than change perlapi-5.8.8
Investigating hunspell-en-us
Package hunspell-en-us has broken dep on myspell-en-us
  Considering myspell-en-us 0 as a solution to hunspell-en-us 2
  Added myspell-en-us to the remove list
  Considering myspell-en-us 0 as a solution to hunspell-en-us 2
  Fixing hunspell-en-us via remove of myspell-en-us
Investigating xserver-xorg-video-openchrome
Package xserver-xorg-video-openchrome has broken dep on libchromexvmc1
  Considering libchromexvmc1 -1 as a solution to xserver-xorg-video-openchrome 2
  Added libchromexvmc1 to the remove list
Package xserver-xorg-video-openchrome has broken dep on libchromexvmcpro1
  Considering libchromexvmcpro1 -1 as a solution to xserver-xorg-video-openchrome 2
  Added libchromexvmcpro1 to the remove list
  Fixing xserver-xorg-video-openchrome via remove of libchromexvmc1
  Fixing xserver-xorg-video-openchrome via remove of libchromexvmcpro1
Investigating human-theme
Package human-theme has broken dep on gtk2-engines-ubuntulooks
  Considering gtk2-engines-ubuntulooks 0 as a solution to human-theme 2
  Added gtk2-engines-ubuntulooks to the remove list
  Fixing human-theme via remove of gtk2-engines-ubuntulooks
Investigating pidgin
Package pidgin has broken dep on libpurple0
  Considering libpurple0 3 as a solution to pidgin 2
  Removing pidgin rather than change libpurple0
Investigating libgnomekbd2
Package libgnomekbd2 has broken dep on libgnomekbd-common
  Considering libgnomekbd-common 6 as a solution to libgnomekbd2 1
  Removing libgnomekbd2 rather than change libgnomekbd-common
Investigating libperl5.8
Package libperl5.8 has broken dep on perl-base
  Considering perl-base 5283 as a solution to libperl5.8 1
  Removing libperl5.8 rather than change perl-base
Investigating libgtkhtml-editor-common
Package libgtkhtml-editor-common has broken dep on gtkhtml3.14
  Considering gtkhtml3.14 -1 as a solution to libgtkhtml-editor-common 1
  Added gtkhtml3.14 to the remove list
  Fixing libgtkhtml-editor-common via remove of gtkhtml3.14
Investigating libbinio1ldbl
Package libbinio1ldbl has broken dep on libbinio1c2
  Considering libbinio1c2 -1 as a solution to libbinio1ldbl 0
  Added libbinio1c2 to the remove list
  Fixing libbinio1ldbl via remove of libbinio1c2
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on rarian-compat
  Considering rarian-compat 25 as a solution to ubuntu-desktop 0
  Holding Back ubuntu-desktop rather than change rarian-compat
Investigating libhd14
Package libhd14 has broken dep on libhd13
  Considering libhd13 -1 as a solution to libhd14 0
  Added libhd13 to the remove list
  Fixing libhd14 via remove of libhd13
Investigating pidgin-mpris
Package pidgin-mpris has broken dep on libpurple0
  Considering libpurple0 3 as a solution to pidgin-mpris 0
  Removing pidgin-mpris rather than change libpurple0
Investigating pidgin-otr
Package pidgin-otr has broken dep on pidgin
  Considering pidgin 2 as a solution to pidgin-otr 0
  Removing pidgin-otr rather than change pidgin
Investigating landscape-common
Package landscape-common has broken dep on python-smartpm
Investigating libgail-common
Package libgail-common has broken dep on libgail18
  Considering libgail18 1 as a solution to libgail-common -1
  Removing libgail-common rather than change libgail18
Investigating libgdl-gnome-1-0
Package libgdl-gnome-1-0 has broken dep on libgdl-1-common
  Considering libgdl-1-common 5 as a solution to libgdl-gnome-1-0 -1
  Removing libgdl-gnome-1-0 rather than change libgdl-1-common
Investigating libffi4
Package libffi4 has broken dep on gcc-4.2-base
  Considering gcc-4.2-base 10 as a solution to libffi4 -1
  Removing libffi4 rather than change gcc-4.2-base
Investigating libgnomekbdui2
Package libgnomekbdui2 has broken dep on libgnomekbd2
  Considering libgnomekbd2 1 as a solution to libgnomekbdui2 -1
  Removing libgnomekbdui2 rather than change libgnomekbd2
Investigating libltdl7-dev
Package libltdl7-dev has broken dep on libltdl3-dev
  Considering libltdl3-dev -1 as a solution to libltdl7-dev -1
  Holding Back libltdl7-dev rather than change libltdl3-dev
 Try to Re-Instate ubuntu-desktop
Investigating landscape-client
Package landscape-client has broken dep on landscape-common
  Considering landscape-common 0 as a solution to landscape-client 0
  Holding Back landscape-client rather than change landscape-common
 Try to Re-Instate landscape-client
Done
Installing python2.4 as dep of python2.4-minimal
Starting
Starting 2
Investigating landscape-common
Package landscape-common has broken dep on python-smartpm
Done
Log time: 2009-10-17 19:28:11.282030

```

Here's main.log
```

2009-10-17 19:11:17,054 INFO release-upgrader version '0.93.34' started
2009-10-17 19:11:18,150 DEBUG svg pixbuf loader failed (Error displaying image)
2009-10-17 19:11:18,304 DEBUG Using 'DistUpgradeViewGtk' view
2009-10-17 19:11:18,440 DEBUG enable dpkg --force-overwrite
2009-10-17 19:11:18,714 DEBUG lsb-release: 'hardy'
2009-10-17 19:11:18,715 DEBUG _pythonSymlinkCheck run
2009-10-17 19:11:18,717 DEBUG openCache()
2009-10-17 19:11:19,182 DEBUG /openCache()
2009-10-17 19:11:19,184 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2009-10-17 19:11:19,185 DEBUG checkViewDepends()
2009-10-17 19:11:19,186 DEBUG running doUpdate() (showErrors=False)
2009-10-17 19:11:46,843 DEBUG openCache()
2009-10-17 19:11:55,694 DEBUG /openCache()
2009-10-17 19:11:55,695 DEBUG doPostInitialUpdate
2009-10-17 19:11:55,696 DEBUG quirks: running intrepidPostInitialUpdate
2009-10-17 19:11:55,697 DEBUG running intrepidPostInitialUpdate
2009-10-17 19:12:03,052 DEBUG Foreign: libdca0 gstreamer0.10-plugins-base gstreamer0.10-alsa libcdparanoia0 vlc-nox gstreamer0.10-plugins-base-apps gstreamer0.10-gnomevfs vlc-data pidgin-data libschroedinger-1.0-0 libvlc2 libpurple0 libgstreamer-plugins-base0.10-0 vlc pidgin libvlccore0 libgstreamer0.10-0 cdparanoia gstreamer0.10-x liboil0.3 gstreamer0.10-tools virtualbox-3.0
2009-10-17 19:12:03,053 DEBUG Obsolete: truecrypt
2009-10-17 19:12:03,057 DEBUG updateSourcesList()
2009-10-17 19:12:03,366 DEBUG rewriteSourcesList()
2009-10-17 19:12:03,381 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted'
2009-10-17 19:12:03,382 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted' updated to new dist
2009-10-17 19:12:03,383 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted'
2009-10-17 19:12:03,384 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted' updated to new dist
2009-10-17 19:12:03,385 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted'
2009-10-17 19:12:03,386 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted' updated to new dist
2009-10-17 19:12:03,387 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted'
2009-10-17 19:12:03,387 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted' updated to new dist
2009-10-17 19:12:03,388 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy universe'
2009-10-17 19:12:03,389 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe' updated to new dist
2009-10-17 19:12:03,390 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe'
2009-10-17 19:12:03,391 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe' updated to new dist
2009-10-17 19:12:03,391 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe'
2009-10-17 19:12:03,393 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe' updated to new dist
2009-10-17 19:12:03,394 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe'
2009-10-17 19:12:03,395 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe' updated to new dist
2009-10-17 19:12:03,396 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse'
2009-10-17 19:12:03,397 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse' updated to new dist
2009-10-17 19:12:03,398 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse'
2009-10-17 19:12:03,398 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse' updated to new dist
2009-10-17 19:12:03,399 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse'
2009-10-17 19:12:03,400 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse' updated to new dist
2009-10-17 19:12:03,401 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse'
2009-10-17 19:12:03,402 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse' updated to new dist
2009-10-17 19:12:03,403 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse'
2009-10-17 19:12:03,403 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse' updated to new dist
2009-10-17 19:12:03,406 DEBUG examining: 'deb http://archive.canonical.com/ubuntu hardy partner'
2009-10-17 19:12:03,406 DEBUG entry 'deb http://archive.canonical.com/ubuntu intrepid partner' updated to new dist
2009-10-17 19:12:03,407 DEBUG examining: 'deb-src http://archive.canonical.com/ubuntu hardy partner'
2009-10-17 19:12:03,410 DEBUG entry 'deb-src http://archive.canonical.com/ubuntu intrepid partner' updated to new dist
2009-10-17 19:12:03,411 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu hardy-security main restricted'
2009-10-17 19:12:03,412 DEBUG entry 'deb http://security.ubuntu.com/ubuntu intrepid-security main restricted' updated to new dist
2009-10-17 19:12:03,413 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted'
2009-10-17 19:12:03,413 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted' updated to new dist
2009-10-17 19:12:03,414 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu hardy-security universe'
2009-10-17 19:12:03,415 DEBUG entry 'deb http://security.ubuntu.com/ubuntu intrepid-security universe' updated to new dist
2009-10-17 19:12:03,417 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu hardy-security universe'
2009-10-17 19:12:03,418 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu intrepid-security universe' updated to new dist
2009-10-17 19:12:03,419 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu hardy-security multiverse'
2009-10-17 19:12:03,420 DEBUG entry 'deb http://security.ubuntu.com/ubuntu intrepid-security multiverse' updated to new dist
2009-10-17 19:12:03,420 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe'
2009-10-17 19:12:03,421 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe' updated to new dist
2009-10-17 19:12:03,422 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse'
2009-10-17 19:12:03,423 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse' updated to new dist
2009-10-17 19:12:03,424 DEBUG examining: 'deb http://ppa.launchpad.net/c-korn/vlc/ubuntu hardy main'
2009-10-17 19:12:03,431 DEBUG entry '# deb http://ppa.launchpad.net/c-korn/vlc/ubuntu hardy main' was disabled (unknown mirror)
2009-10-17 19:12:03,432 DEBUG examining: 'deb-src http://ppa.launchpad.net/c-korn/vlc/ubuntu hardy main'
2009-10-17 19:12:03,437 DEBUG entry '# deb-src http://ppa.launchpad.net/c-korn/vlc/ubuntu hardy main' was disabled (unknown mirror)
2009-10-17 19:12:03,438 DEBUG examining: 'deb http://download.virtualbox.org/virtualbox/debian hardy non-free'
2009-10-17 19:12:03,445 DEBUG entry '# deb http://download.virtualbox.org/virtualbox/debian hardy non-free' was disabled (unknown mirror)
2009-10-17 19:12:03,446 DEBUG examining: 'deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu hardy main'
2009-10-17 19:12:03,451 DEBUG entry '# deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu hardy main' was disabled (unknown mirror)
2009-10-17 19:27:03,106 DEBUG running doUpdate() (showErrors=True)
2009-10-17 19:27:30,257 DEBUG openCache()
2009-10-17 19:27:39,385 DEBUG /openCache()
2009-10-17 19:27:48,535 DEBUG Installing 'python2.4-minimal' (priority in required set 'required' but not scheduled for install)
2009-10-17 19:27:49,429 DEBUG Installing 'ash' (priority in required set 'required' but not scheduled for install)
2009-10-17 19:27:51,464 DEBUG Running KeepInstalledSection rules
2009-10-17 19:27:51,676 DEBUG Kernel uname: '2.6.24-24-generic' 
2009-10-17 19:27:51,695 DEBUG nvidiaUpdate()
2009-10-17 19:27:51,765 INFO no old nvidia driver installed, installing no new
2009-10-17 19:27:51,767 DEBUG Removing 'libflashsupport' (Distro PostUpgradeRemove rule)
2009-10-17 19:27:51,768 DEBUG Removing 'xscreensaver' (ubuntu-desktop PostUpgradeRemove rule)
2009-10-17 19:27:52,104 DEBUG Removing 'gnome-cups-manager' (ubuntu-desktop PostUpgradeRemove rule)
2009-10-17 19:27:52,105 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2009-10-17 19:27:52,106 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2009-10-17 19:27:52,107 DEBUG Purging 'ltsp-client' (Distro PostUpgradePurge rule)
2009-10-17 19:27:52,437 DEBUG Purging 'ltspfsd' (Distro PostUpgradePurge rule)
2009-10-17 19:27:52,824 DEBUG Purging 'python2.3' (Distro PostUpgradePurge rule)
2009-10-17 19:27:52,826 DEBUG quirks: running intrepidPostDistUpgradeCache
2009-10-17 19:27:52,827 DEBUG running intrepidPostDistUpgradeCache
2009-10-17 19:27:53,042 DEBUG Removing 'landscape-client' (custom landscape stub removal rule)
2009-10-17 19:27:53,700 DEBUG Installing 'landscape-common' (custom landscape-common stub install rule (to ensure its nor marked for auto-remove))
2009-10-17 19:28:10,472 ERROR Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'
2009-10-17 19:28:10,479 DEBUG openCache()
2009-10-17 19:28:11,284 DEBUG /openCache()

```

---

### Post by mac9416 on 2009-10-17
Someone had the exact same problem here: [http://ubuntuforums.org/showthread.php?t=1286683&highlight=landscape-common](http://ubuntuforums.org/showthread.php?t=1286683&highlight=landscape-common)

I suggested that he disable third-party repos and uninstall landscape-common/landscape-client. He hasn't said whether that worked or not yet.

---

### Post by absolutezero1287 on 2009-10-18
It turns out that it worked. I'm starting the upgrade now and I will report back in once its finished.

---

