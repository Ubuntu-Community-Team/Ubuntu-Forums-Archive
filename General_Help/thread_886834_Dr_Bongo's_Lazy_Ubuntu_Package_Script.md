---
title: "Dr Bongo's Lazy Ubuntu Package Script"
date: 2008-08-11
forum: General Help
---

### Post by drbongo on 2008-08-11
Do you want to pimp your ubuntu with lots of goodies, but are too lazy to get off your butt and trawl through all those packages and try them out? Then drbongo's (pre)script(ion) is just what you need!

Simply copy and paste the code from the attached .txt file into a terminal (Ctrl+C, Ctrl+Shift+V), press enter and then sit back as your vanilla Hardy Heron is pimped with all kinds of multimedia, office and python goodies!

If there is something you don't want simply remove it from the list, or if there is something missing (like Nvidia or ATI drivers) just add them to the list.

Have fun,

drbongo

---

### Post by Nepherte on 2008-08-11
No offense, but if you don't give a little more details you won't get a lot of positive reactions.

---

### Post by loell on 2008-08-11
well, this kind "tip" style would have worked three years ago. ;)

but not anymore [-X

here's the content of your text file, which you seem too lazy to post on a code tag ;)

```
sudo apt-get install anacron ant-optional ant aptoncd audacity avidemux-common avidemux bicyclerepair bind9-host blt bluefish bsh cabextract debhelper deskbar-applet dnsutils dpkg-dev drpython eclipse-jdt eclipse-pde eclipse-platform eclipse-pydev eclipse-rcp eclipse-sdk eclipse eog evolution-common evolution-data-server-common evolution-data-server evolution-exchange evolution-plugins evolution fakeroot firefox-3.0-gnome-support firefox-3.0 firefox-gnome-support firefox flashplugin-nonfree gambas2-dev gambas2-doc gambas2-gb-chart gambas2-gb-compress-bzlib2 gambas2-gb-compress-zlib gambas2-gb-compress gambas2-gb-crypt gambas2-gb-db-firebird gambas2-gb-db-form gambas2-gb-db-mysql gambas2-gb-db-odbc gambas2-gb-db-postgresql gambas2-gb-db-sqlite gambas2-gb-db gambas2-gb-desktop gambas2-gb-form-dialog gambas2-gb-form-mdi gambas2-gb-form gambas2-gb-gtk-ext gambas2-gb-gtk-svg gambas2-gb-gtk gambas2-gb-gui gambas2-gb-image gambas2-gb-info gambas2-gb-net-curl gambas2-gb-net-smtp gambas2-gb-net gambas2-gb-opengl gambas2-gb-pcre gambas2-gb-pdf gambas2-gb-qt-ext gambas2-gb-qt-kde-html gambas2-gb-qt-kde gambas2-gb-qt-opengl gambas2-gb-qt gambas2-gb-report gambas2-gb-sdl gambas2-gb-settings gambas2-gb-v4l gambas2-gb-vb gambas2-gb-web gambas2-gb-xml gambas2-ide gambas2-runtime gambas2 gcalctool gdm gettext gmountiso gnome-about gnome-cards-data gnome-desktop-data gnome-games-data gnome-games gnome-panel-data gnome-panel gnome-system-monitor gpaint gparted gs-gpl gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly gtk-recordmydesktop gtk2-engines-murrine gtk2-engines-ubuntulooks gtk2-engines gtkhtml3.14 gvfs-backends gvfs-fuse gvfs hal html2text hydrogen-drumkits hydrogen idle-python2.5 imagemagick inkscape intltool-debian iproute java-common junit junit4 jython kdelibs-data kdelibs4c2a language-pack-en language-pack-gnome-en liba52-0.7.4 libarts1c2a libartsc0 libatk1.0-dev libaudio2 libavahi-qt3-1 libavcodec1d libavformat1d libavutil1d libbcel-java libbind9-30 libc6-dev libcairo2-dev libcal3d12 libcamel1.2-11 libcdaudio1 libcommons-beanutils-java libcommons-codec-java libcommons-collections-java libcommons-collections3-java libcommons-dbcp-java libcommons-digester-java libcommons-el-java libcommons-launcher-java libcommons-logging-java libcommons-modeler-java libcommons-pool-java libdc1394-13 libdns35 libdvdread3 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 libexpat1-dev libfaac0 libfaad0 libffi4-dev libfftw3-3 libflac++6 libfltk1.1 libfontconfig1-dev libfreebob0 libfreetype6-dev libgda3-3 libgda3-common libgdata-google1.2-1 libgdata1.2-1 libgdl-1-0 libgdl-1-common libgdl-gnome-1-0 libglib2.0-0 libglib2.0-dev libglibmm-2.4-1c2a libgmyth0 libgnome-desktop-2 libgsm1 libgtk2.0-dev libgtkhtml3.14-19 libgtksourceview2.0-0 libgtksourceview2.0-common libgvfscommon0 libgweather-common libgweather1 libhal-storage1 libhal1 libhsqldb-java libice-dev libid3tag0 libiptcdata0 libisc32 libisccc30 libisccfg30 libjack0 libjaxp1.3-java libjline-java libjsch-java liblame0 liblash2 libldap-2.4-2 liblog4j1.2-java liblrdf0 liblua50 liblualib50 liblucene-java-doc liblucene-java liblwres30 libmad0 libmagick++10 libmjpegtools0c2a libmms0 libmozjs0d libmpcdec3 libmpeg2-4 libmx4j-java libmxml1 libmysqlclient15off libode0debian1 libopenspc0 libpam-smbpass libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpango1.0-dev libpcre3 libpixman-1-dev libpng12-dev libpoppler-glib2 libpoppler2 libpostproc1d libpq5 libpthread-stubs0-dev libpthread-stubs0 libpurple0 libqt3-mt libqt4-core libqt4-gui libquicktime1 libraptor1 libreadline-java libregexp-java librsync1 libsdl-image1.2 libsdl-mixer1.2 libsdl-ttf2.0-0 libservlet2.3-java libservlet2.4-java libsidplay1 libsm-dev libsmbios1 libsmpeg0 libsnack2-dev libsnack2-doc libsnack2 libsoundtouch1c2 libswt3.2-gtk-java libswt3.2-gtk-jni libtimedate-perl libtomcat5.5-java libwildmidi0 libwnck-common libwnck22 libwxbase2.6-0 libwxbase2.8-0 libwxgtk2.6-0 libwxgtk2.8-0 libx11-dev libx264-57 libxalan2-java libxau-dev libxcb-xlib0-dev libxcb1-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxerces2-java libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev libxslt1.1 libxul-common libxul0d libxvidcore4 linux-headers-2.6.24-19-generic linux-headers-2.6.24-19 linux-image-2.6.24-19-generic linux-libc-dev linux-restricted-modules-2.6.24-19-generic linux-restricted-modules-common msttcorefonts mysql-common nautilus-actions nautilus-gksu nautilus-image-converter nautilus-open-terminal nautilus-script-audio-convert nautilus-script-manager nautilus-sendto  odbcinst1debian1 openoffice.org-base openoffice.org-filter-binfilter openoffice.org-filter-mobiledev openoffice.org-java-common openoffice.org-math openoffice.org-officebean openoffice.org-writer2latex openoffice.org openssl-blacklist patch pciutils pidgin-data pidgin planner po-debconf poppler-utils procps pybackpack python-alsaaudio python-cerealizer python-dev python-editobj python-gnome2-extras python-gobject-dev python-gobject python-gtk2-dev python-gtk2-doc python-gtk2-tutorial python-imaging-tk python-oss python-pygame python-soya-doc python-soya python-tk python-tksnack python-twisted-bin python-twisted-core python-wxglade python-wxgtk2.6 python-wxgtk2.8 python-wxversion python-zopeinterface python2.5-dev python2.5-doc python2.5-examples python2.5-minimal python2.5 rdiff-backup recordmydesktop samba scribus-ng soundconverter ssl-cert sun-java6-bin sun-java6-jre sun-java6-plugin tcl8.4 tk8.4 ttf-dejavu-extra ttf-dejavu tzdata ubuntu-restricted-extras ufw unixodbc unrar x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xserver-xorg-video-intel xsltproc xtrans-dev xulrunner-1.9-gnome-support xulrunner-1.9 yelp zlib1g-dev zynaddsubfx

```

---

### Post by drbongo on 2008-08-11
I wasn't really after positive replies - I just wanted to share my package list so other people could achieve the same result easily without having to trawl through hundreds of packages and try them out.

I was not aware that I was supposed to use a code tag as most of the other forums I use tend to use text files for this sort of thing, but I will use one next time.

I apologise for not giving enough details, I just assumed that people would look through the package list. I have added extra open office packages, many multimedia packages such as Audacity, ZynAddSubFx, Hydrogen (with extra drumkits) and avidemux for video editing. I have also added a whole bunch of python development apps including DrPython, Idle, wxGlade and lots of additional python modules behind the scenes.

Look through the package list if you want a complete list.

drbongo

---

### Post by Nepherte on 2008-08-11
> **drbongo said:**
> I just wanted to share my package list so other people could achieve the same result easily without having to trawl through hundreds of packages and try them out.From the packages you suggest, I use quite a lot of them myself and can be very useful. I just found it a little odd just naming a bunch of packages. Didn't want to come over aggressive or something.

cheers,

Nepherte

---

### Post by drbongo on 2008-08-11
No problem - no offence taken :) I also forgot to mention that this code snippet contains all of the recent updates (100+) made to Ubuntu 8.04.1.

If UCK and/or reconstructor are still working I may release it as a bootable/installable iso instead. But I am quite lazy!

drbongo

---

### Post by Vivaldi Gloria on 2008-08-11
I suggest some improvements for your list:

1) You should remove system packages. For example remove linux-* packages. These can breake a working system.

2) Remove already installed apps. For example eog, ufw, evolution*, ff, gdm, gvfs. pidgin etc. etc. are already installed in ubuntu. There are more of this sort in your list.

3) Remove duplications: gstreamer, java, libdvdread3, msttcorefonts, unrar etc. are already in ubuntu-restricted-extras.

4) Some apps need restricted & multiverse repos enabled. You should mention it.

5) Add build-essential to your list. Necessary for installing from source.

To be honest, these lists are only good for the creator of the list. Since there are all kinds of programs in it, no one will ever want to install them all. But I also keep a list of packages that I install so that I don't forget to install them the next time I install ubuntu.

---

