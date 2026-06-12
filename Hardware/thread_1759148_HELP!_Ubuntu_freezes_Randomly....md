---
title: "HELP! Ubuntu freezes Randomly..."
date: 2011-05-15
forum: Hardware
---

### Post by xcommunistx on 2011-05-15
Dear Ubuntu Users,

Since i installed Ubuntu everything was Ok and i thought it was the Fastest System ever...
Then i downloaded some New Things and now everytime i Open Ubuntu Software Center, Synaptic Package it freezes and i can't Deinstall those Things, heres what i downloaded:
OpenShot Video-Editor
lib-extra
libdev
Opera Web browser
X-Manager
X-ScreenVideoRecorder
So now i can't Deinstall and when i can there comes Error: PackaeSystem is Defect or Aptdaemon is Defect, you can't remove/install now...
Please, do anyone now about this? I would Re-Install Ubuntu but it will take too much Work and i will lose some Files...

Greetings,
xcommunistx

---

### Post by slooksterpsv on 2011-05-15
Ok I tried to research this out to find out what's going on, but I can barely find anything really. Could I have you do the following:

Click on your Applications menu, search for Gnome-Terminal, open Gnome-Terminal

Type in the following:
```

gksudo apt-get update
sudo apt-get install -f

```

Copy and paste the results of the last command here. Not sure if that would help but if something "defunct" it may. There's another command we could try, but I want to hold off, it's: sudo dpkg-reconfigure -a

---

### Post by xcommunistx on 2011-05-15
The last one i already tried, but dpkg can not open....
 Now the first doesn't help anyway, here what cames out at the second...
I have an German OS so i translate...

[code]
Paketlisten werden gelesen (Package List loading)... Fertig (done)
Abhängigkeitsbaum wird aufgebaut (Depend-three builds)      
Statusinformationen werden eingelesen (reading Stats information) ... Fertig (done)
Abhängigkeiten werden korrigiert (correcting dependence)... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
(the followig Packages was installed automatically and are not more needed)
  librpmbuild1 libtasn1-3-dev libvalhalla2 libx264-106 wine1.2 libwxgtk2.8-0
  libgcrypt11-dev libportsmf0 libavidemux0 avidemux-plugins-common libcdt4
  audacity-data librpmio1 libflac++6 esound-common libaften0
  libavcodec-extra-52 libgssrpc4 libavutil-extra-50 appmenu-qt libexif-dev
  libqtcore4 krb5-multidev libvpx0 libgavl1 libavformat-dev libwxbase2.8-0
  icoutils ttf-mscorefonts-installer libqt4-svg libmagickcore3 libgsm1
  libdvdread4 wireless-crda libavcodec-dev libmagickwand3 libsox-fmt-alsa
  libmagickcore3-extra libqtgui4 mjpegtools libva1 winbind libsox1b
  libquicktime1 libdirac-encoder0 openshot-doc gnome-exe-thumbnailer
  libpathplan4 libnfo1 libopencore-amrwb0 libidn11-dev liba52-0.7.4
  libqt4-dbus libqt4-xml cabextract libdbusmenu-qt2 comerr-dev imagemagick
  liblqr-1-0 libdjvulibre21 libesd0 libaudiofile0 libavformat52 libswscale0
  libgraph4 libgvc5 libkadm5srv-mit7 libkadm5clnt-mit7 libaudio2 libavutil-dev
  libschroedinger-1.0-0 libdjvulibre-text libgpg-error-dev libkdb5-4 librpm1
  rpm-common libopenal1 libmp3lame0 libfaad2 libopenjpeg2 libopencore-amrnb0
  libmpg123-0 libxvidcore4 libfaac0 libmjpegtools-1.9
Verwenden Sie »apt-get autoremove«, um sie zu entfernen. (use apt-get autoremove to remove them...)
Die folgenden zusätzlichen Pakete werden installiert: (the following Packages get installed)
  apport apt-utils aptdaemon aspell at avahi-daemon bamfdaemon base-passwd
  bash bash-completion bind9-host binutils bogofilter-bdb bogofilter-common
  brasero-common bsdmainutils busybox-initramfs busybox-static ca-certificates
  cabextract comerr-dev compiz-core compiz-gnome compiz-plugins-main
  compizconfig-backend-gconf console-setup console-terminus consolekit cpio
  cpp cron cups cups-common cups-driver-gutenprint dbus-x11 dc debconf-i18n
  defoma dictionaries-common diffstat dmsetup docbook-xml dosfstools dpkg
  e2fslibs e2fsprogs eject espeak espeak-data exiv2 findutils firefox
  fontconfig-config foomatic-db-engine foomatic-filters ftp fuse-utils gawk
  gcc gcc-4.5-base gconf-defaults-service gconf2 genisoimage ghostscript
  ghostscript-cups gir1.2-dbusmenu-glib-0.4 gir1.2-dee-0.5 gir1.2-freedesktop
  gir1.2-gdkpixbuf-2.0 gir1.2-glib-2.0 gir1.2-gtk-2.0 gir1.2-pango-1.0
  gir1.2-vte-0.0 gksu gnome-about gnome-control-center gnome-desktop-data
  gnome-icon-theme gnome-menus gnome-panel-data gnome-power-manager
  gnome-session gnome-session-bin gnome-session-common gnome-terminal-data
  gnome-utils-common gnupg groff-base growisofs gs-cjk-resource
  gsettings-desktop-schemas gstreamer0.10-gnonlin gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x gtk2-engines-pixbuf gvfs gwibber-service
  gwibber-service-identica gwibber-service-twitter hdparm humanity-icon-theme
  hunspell-en-ca ibus ibus-pinyin-db-open-phrase im-switch imagemagick
  indicator-application info initramfs-tools-bin initscripts insserv
  intltool-debian iptables iputils-ping iputils-tracepath iso-codes kbd
  keyboard-configuration keyutils klibc-utils language-pack-de
  language-pack-de-base language-pack-en-base language-pack-gnome-de-base
  language-pack-gnome-en language-selector-common launchpad-integration libaa1
  libacl1 libappindicator1 libarchive1 libatk1.0-0 libatk1.0-data
  libatkmm-1.6-1 libattr1 libaudio2 libaudiofile0 libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core7 libavahi-gobject0
  libavformat52 libavutil-dev libbabl-0.0-0 libbamf0 libblkid1
  libbonoboui2-common libboost-serialization1.42.0 libbrasero-media1
  libbrlapi0.5 libbsd0 libbz2-1.0 libc-bin libc6 libcaca0 libcairo-gobject2
  libcairo-perl libcairomm-1.0-1 libcamel1.2-19 libcanberra-gtk0 libcanberra0
  libcap-ng0 libcap2 libcdio-paranoia0 libcdio10 libcdparanoia0 libcomerr2
  libcompizconfig0 libcroco3 libcryptui0 libcups2 libcupscgi1 libcupsimage2
  libcupsppdc1 libdaemon0 libdatrie1 libdb4.8 libdbusmenu-gtk3 libdbusmenu-qt2
  libdee-1.0-1 libdevmapper-event1.02.1 libdevmapper1.02.1 libdjvulibre-text
  libdjvulibre21 libdrm-intel1 libebackend1.2-0 libecryptfs0
  libedata-book1.2-8 libedata-cal1.2-10 libedataserverui1.2-11 libedit2
  libemail-valid-perl libept1 libesd0 libexiv2-10 libexpat1 libfaac0 libfaad2
  libfile-copy-recursive-perl libfile-desktopentry-perl libfolks22 libfontenc1
  libfs6 libgadu3 libgail18 libgdata-common libgdata1.7-cil libgdu0 libgee2
  libgeoclue0 libgexiv2-0 libgkeyfile1.0-cil libgksu2-0 libgl1-mesa-glx
  libglade2.0-cil libglew1.5 libglewmx1.5 libglib-perl libglib2.0-0
  libglib2.0-bin libglib2.0-cil libglibmm-2.4-1c2a libgmime-2.4-2
  libgnome-keyring0 libgnome-menu2 libgnome-vfs2.0-cil libgnome2-0
  libgnome2-common libgnome2.24-cil libgnomecanvas2-common libgnomekbd-common
  libgnomeui-common libgnomevfs2-0 libgnutls26 libgomp1 libgp11-0
  libgpg-error-dev libgphoto2-2 libgphoto2-port0 libgpm2 libgraph4 libgs9
  libgs9-common libgsl0ldbl libgstreamer0.10-0 libgtk-sharp-beans-cil
  libgtk2-perl libgtk2.0-bin libgtk2.0-common libgtksourceview2.0-0
  libgtksourceview2.0-common libgudev1.0-cil libgupnp-1.0-3 libgutenprint2
  libgvc5 libgweather-common libhpmud0 libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhunspell-1.2-0 libhyphen0 libice6 libicu44 libidn11
  libiec61883-0 libijs-0.35 libilmbase6 libindicate5 libindicator3
  libio-pty-perl libio-string-perl libipc-run-perl libisofs6 libjack-jackd2-0
  libjasper1 libjbig2dec0 libkadm5clnt-mit7 libkadm5srv-mit7 libkdb5-4
  libkeyutils1 libkrb5-3 libkrb5support0 liblaunchpad-integration1
  liblaunchpad-integration1.0-cil liblcms1 libldap-2.4-2
  liblocale-gettext-perl liblqr-1-0 libltdl7 liblua5.1-0 liblvm2app2.2
  liblwres60 liblzma2 libmeanwhile1 libmetacity-private0
  libmission-control-plugins0 libmjpegtools-1.9 libmng1 libmono-addins0.2-cil
  libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-i18n-west2.0-cil
  libmono-management2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil
  libmono-system2.0-cil libmono-zeroconf1.0-cil libmp3lame0 libmpc2 libmpfr4
  libmpg123-0 libmtdev1 libmythes-1.2-0 libnautilus-extension1 libncurses5
  libncursesw5 libndesk-dbus-glib1.0-cil libnet-dns-perl libnewt0.52
  libnfnetlink0 libnice10 libnih-dbus1 libnih1 libnm-glib-vpn1 libnm-glib2
  libnspr4 libnss-mdns libnss3 libnss3-1d libntfs-3g79 libntfs10 libnux-0.9-0
  libnux-0.9-common libopenal1 libopencc1 libopencore-amrnb0 libopenexr6
  libopenjpeg2 libopenobex1 liborbit2 liborc-0.4-0 liboverlay-scrollbar-0.1-0
  libpam-ck-connector libpam-modules-bin libpam-runtime libpango1.0-0
  libpangomm-1.4-1 libpaper-utils libpaper1 libparse-debianchangelog-perl
  libpcap0.8 libpciaccess0 libpcre3 libpcsclite1 libpipeline1 libpixman-1-0
  libplist1 libplymouth2 libpng12-0 libpolkit-backend-1-0 libpoppler-glib6
  libpoppler13 libportaudio2 libproxy0 libpulse-browse0
  libpulse-mainloop-glib0 libpulse0 libqt4-dbus libqt4-xml libquvi0 libraptor1
  librarian0 librasqal2 libreadline6 libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-gtk librpm1 librsvg2-2 librsvg2-common
  libsasl2-2 libsasl2-modules libschroedinger-1.0-0 libsdl1.2debian-alsa
  libselinux1 libsensors4 libshout3 libsigc++-2.0-0c2a libsilc-1.1-2
  libsilcclient-1.1-3 libslang2 libsm6 libsndfile1 libsnmp15 libspeexdsp1
  libsqlite3-0 libss2 libstartup-notification0 libstdc++6 libstlport4.6ldbl
  libsub-name-perl libswscale0 libtag1c2a libtaglib2.0-cil libtalloc2
  libtext-charwidth-perl libtext-iconv-perl libtextcat-data libtextcat0
  libtheora0 libtiff4 libunique-1.0-0 libunity-misc0 libupower-glib1
  libutouch-geis1 libutouch-grail1 libuuid-perl libvisual-0.4-0
  libvisual-0.4-plugins libvorbis0a libvorbisenc2 libvte-common libvte9
  libwnck-common libwnck22 libwpg-0.2-2 libwrap0 libwww-perl libx11-6
  libx11-data libx11-xcb1 libx86-1 libxau6 libxaw7 libxcb-atom1 libxcb-aux0
  libxcb-dri2-0 libxcb-render0 libxcb-shape0 libxcursor1 libxdamage1
  libxfixes3 libxft2 libxi6 libxklavier16 libxml2-utils libxmu6 libxt6
  libxtst6 libxvidcore4 libxxf86vm1 libzeitgeist-1.0-1 libzephyr4 lintian
  logrotate lshw lsof ltrace make mime-support mono-gmcs multiarch-support
  myspell-en-za nautilus net-tools notification-daemon ntfsprogs nux-tools
  openssh-client parted passwd patch perl pinyin-database pkg-config plymouth
  plymouth-theme-ubuntu-text pm-utils policykit-1 poppler-utils
  popularity-contest powermgmt-base ppp pptp-linux pulseaudio
  pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils python-appindicator python-apt python-apt-common
  python-aptdaemon-gtk python-aptdaemon.gtkwidgets python-argparse
  python-cairo python-central python-chardet python-configglue python-crypto
  python-cups python-cupshelpers python-debian python-farsight python-gconf
  python-glade2 python-gmenu python-gnomekeyring python-gobject
  python-gobject-cairo python-gst0.10 python-gtk2 python-gtksourceview2
  python-httplib2 python-imaging python-keyring python-launchpadlib
  python-lazr.restfulclient python-libxml2 python-markupsafe python-notify
  python-oauth python-openssl python-pam python-piston-mini-client
  python-problem-report python-pycurl python-pygoocanvas python-pyinotify
  python-pyorbit python-serial python-simplejson python-smbc python-telepathy
  python-twisted-core python-twisted-names python-ubuntuone-storageprotocol
  python-vte python-wadllib python-webkit python-wsgi-intercept python-xapian
  python-xdg python2.7-minimal rarian-compat readline-common rpm-common rsync
  rtkit samba-common samba-common-bin sed sgml-data software-properties-gtk
  strace synaptic syslinux system-config-printer-common sysvinit-utils time
  totem-common ttf-freefont ttf-opensymbol ubufox ubuntu-system-service udev
  udisks unattended-upgrades uno-libs3 upower upstart usb-modeswitch-data
  usbmuxd usbutils util-linux vbetool wbritish wget x-ttcidfont-conf x11-apps
  x11-common x11-utils x11-xfs-utils x11-xserver-utils xauth xbitmaps
  xdg-user-dirs xfonts-base xfonts-encodings xfonts-utils xinit xinput
  xkb-data xml-core xorg-docs-core xserver-xorg-input-mouse
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-geode xserver-xorg-video-i128
  xserver-xorg-video-i740 xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-r128
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-siliconmotion xserver-xorg-video-sisusb
  xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-tseng
  xserver-xorg-video-vesa xsltproc xul-ext-ubufox xz-utils yelp yelp-xsl
  zeitgeist-datahub zenity
Vorgeschlagene Pakete: (Refferented Packages)
  aspell-doc spellutils default-mta mail-transport-agent bash-doc binutils-doc
  db4.8-util vacation nvidia-glx gnome-themes cpp-doc anacron checksecurity
  lockfile-progs cups-bsd foomatic-db-compressed-ppds foomatic-db hplip
  cups-pdf smbclient gutenprint-doc gutenprint-locales defoma-doc psfontmgr
  libfont-freetype-perl ispell emacsen-common jed-extra docbook docbook-dsssl
  docbook-xsl docbook-defguide gpart e2fsck-static cdtool setcd mlocate locate
  slocate firefox-gnome-support firefox-kde-support latex-xft-fonts
  foomatic-db-gutenprint gcc-multilib autoconf automake1.9 libtool flex bison
  gcc-doc wodim cdrkit-doc ghostscript-x gnome-screensaver xscreensaver
  gstreamer0.10-alsa gstreamer0.10-audiosink desktop-base gnupg-curl gnupg-doc
  groff ttf-sazanami-mincho ttf-sazanami-gothic ttf-arphic-ukai
  ttf-arphic-uming ttf-unfonts-core apmd hunspell openoffice.org-hunspell
  openoffice.org-core imagemagick-doc autotrace enscript ffmpeg gnuplot grads
  hp2xx html2ps libwmf-bin mplayer povray radiance texlive-base-bin transfig
  xdg-utils ufraw-batch texinfo-doc-nonfree bootchart traceroute isoquery
  language-support-de konqueror nas gstreamer0.10-fluendo-mp3
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly cdrdao glibc-doc
  libcanberra-pulse esound-clients esound monodoc-gtk2.0-manual glew-utils
  libgnomevfs2-bin libgnomevfs2-extra gnutls-bin gphoto2 gtkam gpm
  gsl-ref-psdoc gsl-doc-pdf gsl-doc-info gsl-ref-html libgtk2-perl-doc
  libdata-dump-perl jackd2 libjasper-runtime krb5-doc krb5-user liblcms-utils
  libmono-i18n2.0-cil libgdiplus libmono-winforms2.0-cil
  libio-socket-inet6-perl ttf-japanese-mincho ttf-thryomanes ttf-baekmuk
  ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp
  ttf-arphic-bkai00mp libhtml-template-perl libxml-simple-perl pcscd
  poppler-data raptor-utils rasqal-utils libreoffice-style-hicontrast
  libreoffice-style-tango libreoffice-style-crystal libreoffice-style-oxygen
  librsvg2-bin libsasl2-modules-otp libsasl2-modules-ldap libsasl2-modules-sql
  libsasl2-modules-gssapi-mit libsasl2-modules-gssapi-heimdal lm-sensors
  libcrypt-ssleay-perl libio-socket-ssl-perl binutils-multiarch
  libtext-template-perl mailx make-doc evince pdf-viewer libpam-ssh keychain
  openssh-blacklist openssh-blacklist-extra parted-doc diffutils-doc
  libterm-readline-gnu-perl libterm-readline-perl-perl cpufrequtils
  wireless-tools ethtool radeontool pavumeter paman paprefs
  pulseaudio-module-raop python-apt-dbg python-apt-doc python-argparse-doc
  python-crypto-dbg python-gnome2-doc python-gtk2-doc python-gobject-dbg
  python-gst0.10-dev python-gst0.10-dbg python-numpy libgtksourceview2.0-dev
  python-imaging-doc python-imaging-dbg python-openssl-doc python-openssl-dbg
  python-pam-dbg libcurl4-gnutls-dev python-pycurl-dbg python-pyinotify-doc
  python-pyorbit-dbg python-wxgtk2.8 python-wxgtk2.6 python-wxgtk python-tk
  python-qt3 python-profiler xapian-doc openssh-server perlsgml doc-html-w3
  opensp dwww menu deborphan sash watershed xfsprogs reiserfsprogs mdadm
  cryptsetup bsd-mailx graphviz util-linux-locales mesa-utils nickle cairo-5c
  xfs xserver debhelper xorg-docs firmware-linux xz-lzma ttf-dejavu
Empfohlene Pakete: (Preferred Package)
  netpbm xserver-xorg-video-cyrix xserver-xorg-video-nsc
Die folgenden NEUEN Pakete werden installiert: (the following NEW packages get installed)
  apport apt-utils aptdaemon aspell at avahi-daemon bamfdaemon base-passwd
  bash bash-completion bind9-host binutils bogofilter-bdb bogofilter-common
  brasero-common bsdmainutils busybox-initramfs busybox-static ca-certificates
  cabextract comerr-dev compiz-core compiz-gnome compiz-plugins-main
  compizconfig-backend-gconf console-setup console-terminus consolekit cpio
  cpp cron cups cups-common cups-driver-gutenprint dbus-x11 dc debconf-i18n
  defoma dictionaries-common diffstat dmsetup docbook-xml dosfstools dpkg
  e2fslibs e2fsprogs eject espeak espeak-data exiv2 findutils firefox
  fontconfig-config foomatic-db-engine foomatic-filters ftp fuse-utils gawk
  gcc gcc-4.5-base gconf-defaults-service gconf2 genisoimage ghostscript
  ghostscript-cups gir1.2-dbusmenu-glib-0.4 gir1.2-dee-0.5 gir1.2-freedesktop
  gir1.2-gdkpixbuf-2.0 gir1.2-glib-2.0 gir1.2-gtk-2.0 gir1.2-pango-1.0
  gir1.2-vte-0.0 gksu gnome-about gnome-control-center gnome-desktop-data
  gnome-icon-theme gnome-menus gnome-panel-data gnome-power-manager
  gnome-session gnome-session-bin gnome-session-common gnome-terminal-data
  gnome-utils-common gnupg groff-base growisofs gs-cjk-resource
  gsettings-desktop-schemas gstreamer0.10-gnonlin gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x gtk2-engines-pixbuf gvfs gwibber-service
  gwibber-service-identica gwibber-service-twitter hdparm humanity-icon-theme
  hunspell-en-ca ibus ibus-pinyin-db-open-phrase im-switch imagemagick
  indicator-application info initramfs-tools-bin initscripts insserv
  intltool-debian iptables iputils-ping iputils-tracepath iso-codes kbd
  keyboard-configuration keyutils klibc-utils language-pack-de
  language-pack-de-base language-pack-en-base language-pack-gnome-de-base
  language-pack-gnome-en language-selector-common launchpad-integration libaa1
  libacl1 libappindicator1 libarchive1 libatk1.0-0 libatk1.0-data
  libatkmm-1.6-1 libattr1 libaudio2 libaudiofile0 libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core7 libavahi-gobject0
  libavformat52 libavutil-dev libbabl-0.0-0 libbamf0 libblkid1
  libbonoboui2-common libboost-serialization1.42.0 libbrasero-media1
  libbrlapi0.5 libbsd0 libbz2-1.0 libc-bin libc6 libcaca0 libcairo-gobject2
  libcairo-perl libcairomm-1.0-1 libcamel1.2-19 libcanberra-gtk0 libcanberra0
  libcap-ng0 libcap2 libcdio-paranoia0 libcdio10 libcdparanoia0 libcomerr2
  libcompizconfig0 libcroco3 libcryptui0 libcups2 libcupscgi1 libcupsimage2
  libcupsppdc1 libdaemon0 libdatrie1 libdb4.8 libdbusmenu-gtk3 libdbusmenu-qt2
  libdee-1.0-1 libdevmapper-event1.02.1 libdevmapper1.02.1 libdjvulibre-text
  libdjvulibre21 libdrm-intel1 libebackend1.2-0 libecryptfs0
  libedata-book1.2-8 libedata-cal1.2-10 libedataserverui1.2-11 libedit2
  libemail-valid-perl libept1 libesd0 libexiv2-10 libexpat1 libfaac0 libfaad2
  libfile-copy-recursive-perl libfile-desktopentry-perl libfolks22 libfontenc1
  libfs6 libgadu3 libgail18 libgdata-common libgdata1.7-cil libgdu0 libgee2
  libgeoclue0 libgexiv2-0 libgkeyfile1.0-cil libgksu2-0 libgl1-mesa-glx
  libglade2.0-cil libglew1.5 libglewmx1.5 libglib-perl libglib2.0-0
  libglib2.0-bin libglib2.0-cil libglibmm-2.4-1c2a libgmime-2.4-2
  libgnome-keyring0 libgnome-menu2 libgnome-vfs2.0-cil libgnome2-0
  libgnome2-common libgnome2.24-cil libgnomecanvas2-common libgnomekbd-common
  libgnomeui-common libgnomevfs2-0 libgnutls26 libgomp1 libgp11-0
  libgpg-error-dev libgphoto2-2 libgphoto2-port0 libgpm2 libgraph4 libgs9
  libgs9-common libgsl0ldbl libgstreamer0.10-0 libgtk-sharp-beans-cil
  libgtk2-perl libgtk2.0-bin libgtk2.0-common libgtksourceview2.0-0
  libgtksourceview2.0-common libgudev1.0-cil libgupnp-1.0-3 libgutenprint2
  libgvc5 libgweather-common libhpmud0 libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhunspell-1.2-0 libhyphen0 libice6 libicu44 libidn11
  libiec61883-0 libijs-0.35 libilmbase6 libindicate5 libindicator3
  libio-pty-perl libio-string-perl libipc-run-perl libisofs6 libjack-jackd2-0
  libjasper1 libjbig2dec0 libkadm5clnt-mit7 libkadm5srv-mit7 libkdb5-4
  libkeyutils1 libkrb5-3 libkrb5support0 liblaunchpad-integration1
  liblaunchpad-integration1.0-cil liblcms1 libldap-2.4-2
  liblocale-gettext-perl liblqr-1-0 libltdl7 liblua5.1-0 liblvm2app2.2
  liblwres60 liblzma2 libmeanwhile1 libmetacity-private0
  libmission-control-plugins0 libmjpegtools-1.9 libmng1 libmono-addins0.2-cil
  libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-i18n-west2.0-cil
  libmono-management2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil
  libmono-system2.0-cil libmono-zeroconf1.0-cil libmp3lame0 libmpc2 libmpfr4
  libmpg123-0 libmtdev1 libmythes-1.2-0 libnautilus-extension1 libncurses5
  libncursesw5 libndesk-dbus-glib1.0-cil libnet-dns-perl libnewt0.52
  libnfnetlink0 libnice10 libnih-dbus1 libnih1 libnm-glib-vpn1 libnm-glib2
  libnspr4 libnss-mdns libnss3 libnss3-1d libntfs-3g79 libntfs10 libnux-0.9-0
  libnux-0.9-common libopenal1 libopencc1 libopencore-amrnb0 libopenexr6
  libopenjpeg2 libopenobex1 liborbit2 liborc-0.4-0 liboverlay-scrollbar-0.1-0
  libpam-ck-connector libpam-modules-bin libpam-runtime libpango1.0-0
  libpangomm-1.4-1 libpaper-utils libpaper1 libparse-debianchangelog-perl
  libpcap0.8 libpciaccess0 libpcre3 libpcsclite1 libpipeline1 libpixman-1-0
  libplist1 libplymouth2 libpng12-0 libpolkit-backend-1-0 libpoppler-glib6
  libpoppler13 libportaudio2 libproxy0 libpulse-browse0 libpulse0 libqt4-dbus
  libqt4-xml libquvi0 libraptor1 librarian0 librasqal2 libreadline6
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-gtk librpm1
  librsvg2-2 librsvg2-common libsasl2-2 libsasl2-modules libschroedinger-1.0-0
  libsdl1.2debian-alsa libselinux1 libsensors4 libshout3 libsigc++-2.0-0c2a
  libsilc-1.1-2 libsilcclient-1.1-3 libslang2 libsm6 libsndfile1 libsnmp15
  libspeexdsp1 libsqlite3-0 libss2 libstartup-notification0 libstdc++6
  libstlport4.6ldbl libsub-name-perl libswscale0 libtag1c2a libtaglib2.0-cil
  libtalloc2 libtext-charwidth-perl libtext-iconv-perl libtextcat-data
  libtextcat0 libtheora0 libtiff4 libunique-1.0-0 libunity-misc0
  libupower-glib1 libutouch-geis1 libutouch-grail1 libuuid-perl
  libvisual-0.4-0 libvisual-0.4-plugins libvorbis0a libvorbisenc2
  libvte-common libvte9 libwnck-common libwnck22 libwpg-0.2-2 libwrap0
  libwww-perl libx11-6 libx11-data libx11-xcb1 libx86-1 libxau6 libxaw7
  libxcb-atom1 libxcb-aux0 libxcb-dri2-0 libxcb-render0 libxcb-shape0
  libxcursor1 libxdamage1 libxfixes3 libxft2 libxi6 libxklavier16
  libxml2-utils libxmu6 libxt6 libxtst6 libxvidcore4 libxxf86vm1
  libzeitgeist-1.0-1 libzephyr4 lintian logrotate lshw lsof ltrace make
  mime-support mono-gmcs multiarch-support myspell-en-za nautilus net-tools
  notification-daemon ntfsprogs nux-tools openssh-client parted passwd patch
  perl pinyin-database pkg-config plymouth plymouth-theme-ubuntu-text pm-utils
  policykit-1 poppler-utils popularity-contest powermgmt-base ppp pptp-linux
  pulseaudio pulseaudio-esound-compat python-appindicator python-apt
  python-apt-common python-aptdaemon-gtk python-aptdaemon.gtkwidgets
  python-argparse python-cairo python-central python-chardet python-configglue
  python-crypto python-cups python-cupshelpers python-debian python-farsight
  python-gconf python-glade2 python-gmenu python-gnomekeyring python-gobject
  python-gobject-cairo python-gst0.10 python-gtk2 python-gtksourceview2
  python-httplib2 python-imaging python-keyring python-launchpadlib
  python-lazr.restfulclient python-libxml2 python-markupsafe python-notify
  python-oauth python-openssl python-pam python-piston-mini-client
  python-problem-report python-pycurl python-pygoocanvas python-pyinotify
  python-pyorbit python-serial python-simplejson python-smbc python-telepathy
  python-twisted-core python-twisted-names python-ubuntuone-storageprotocol
  python-vte python-wadllib python-webkit python-wsgi-intercept python-xapian
  python-xdg python2.7-minimal rarian-compat readline-common rpm-common rsync
  rtkit samba-common samba-common-bin sed sgml-data software-properties-gtk
  strace synaptic syslinux system-config-printer-common sysvinit-utils time
  totem-common ttf-freefont ttf-opensymbol ubufox ubuntu-system-service udev
  udisks unattended-upgrades uno-libs3 upower upstart usb-modeswitch-data
  usbmuxd usbutils util-linux vbetool wbritish wget x-ttcidfont-conf x11-apps
  x11-common x11-utils x11-xfs-utils x11-xserver-utils xauth xbitmaps
  xdg-user-dirs xfonts-base xfonts-encodings xfonts-utils xinit xinput
  xkb-data xml-core xorg-docs-core xserver-xorg-input-mouse
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-geode xserver-xorg-video-i128
  xserver-xorg-video-i740 xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-r128
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-siliconmotion xserver-xorg-video-sisusb
  xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-tseng
  xserver-xorg-video-vesa xsltproc xul-ext-ubufox xz-utils yelp yelp-xsl
  zeitgeist-datahub zenity
Die folgenden Pakete werden aktualisiert (Upgrade): (those Packages got an Upgrade)
  libpulse-mainloop-glib0 pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils
4 Updated, 626 New installings, 0 to delete and 6 not Updated.
Needed 0 B of 240 MB  Archives to be downloaded
After this Operation there will be  837 MB more in Use...
DO you want to COntinue [Y/n]?

Now i choosed Yes, i think i had to, not?
Thats what came out...
Ectracting Packages: 100%
Pre-COfiguration of Packages ...
dpkg: Error: COuld not read »/var/lib/dpkg/status«: Input-/OutputError
W: Encountered status field in a non-version description
W: Try »apt-get update«, to Solve the Problem
E: Sub-process /usr/bin/dpkg returned an error code (2)
 [code]

 Then i tried Again and  apt-get update returned the same Error, so can you help me?

---

### Post by slooksterpsv on 2011-05-15
All of those packages, are the core components of Ubuntu, so no we don't want to uninstall those. Could you edit that and put either 
\[code\]
tags around it so that it shows it in a box like this (without the \'s)
```

see

```

Umm... wow this is odd, try this:

sudo dpkg-reconfigure -a - that will go through and reconfigure pretty much everything.

---

### Post by xcommunistx on 2011-05-15
How to set the Code exactly, you see i did this but it doesnt work...
aynway, to make this sudo command i need some programm (my terminal said) called adduser, i tried to install this but i cant install things like i said and so it still comes the same. I tried as root and still it doesnt work, is there something like an command to delete everything except od the basics? I know there is Computer-Janitor but even this doesnt work...
When i dont get a Solution i think i have to unfortunaly Re-Install Ubuntu!

---

### Post by slooksterpsv on 2011-05-15
> **xcommunistx said:**
> How to set the Code exactly, you see i did this but it doesnt work...
aynway, to make this sudo command i need some programm (my terminal said) called adduser, i tried to install this but i cant install things like i said and so it still comes the same. I tried as root and still it doesnt work, is there something like an command to delete everything except od the basics? I know there is Computer-Janitor but even this doesnt work...
When i dont get a Solution i think i have to unfortunaly Re-Install Ubuntu!

Something fubar'ed - yeah you're going to reinstall.

---

### Post by xcommunistx on 2011-05-16
So i have Re-install...
Thank you for taking time to Help!

---

