---
title: "Brother Printer - Laughable Dependency List - What's Wrong and Where to Report It?"
date: 2017-07-05
forum: Hardware
---

### Post by MrKevin1a on 2017-07-05
Hey folks.  I've been using this printer over several releases with minimal issues, both over USB and as a network printer.  I grabbed the drivers from the brother site here: [http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=mfcj870dw_us_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=mfcj870dw_us_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625)

This time, I ended up with a mile long list of dependencies that took up nearly a full page in my terminal.  I can tell just by looking at them that it's wrong and something somewhere changed.

Screenshot: [http://imgur.com/U6qFFG5](http://imgur.com/U6qFFG5)

My question is who do I report this too, and what the heck happened!  I'm guessing it's on their end, but I really have no idea.  :P[TABLE]
[/TABLE]

---

### Post by vasa1 on 2017-07-05
Please post terminal output using code tags rather than as screenshots on 3rd party hosting sites. That way, you can post content exceeding one screen and others can quote what they want from the code when they respond to you.

---

### Post by vasa1 on 2017-07-05
Also, please share the output of ```
lsb_release -a

```and```
cat /etc/*-release
```and```
cat /var/log/installer/media-info
```and```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by MrKevin1a on 2017-07-06
Thanks for the reply.  Sorry about the screenshot.  I usually use IRC for my questions, but this one seemed more lengthy and I thought I'd be more likely to get an answer here.  I also have to confess something. :P  I'm using an ubuntu-based system, not one of the official variants, but I think it's likely to be the same situation.  I'm comfortable with the community here, having been a longtime Ubuntu user in the gnome2 days.

```
Downloads # bash linux-brprinter-installer-2.1.1-1 
Input model name ->MFC-J870DW


You are going to install following packages.
   mfcj870dwlpr-3.0.0-1.i386.deb
   mfcj870dwcupswrapper-3.0.0-1.i386.deb
   brscan4-0.4.4-3.amd64.deb
   brscan-skey-0.2.4-1.amd64.deb
OK? [y/N] ->y


Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                                                                                                                                                            
Hit:2 http://archive.canonical.com/ubuntu xenial InRelease                                                                                                                                                                                                                              
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]                                                                                               
Hit:4 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial InRelease                                                                                                      
Hit:5 http://dl.google.com/linux/chrome/deb stable Release                                                                                                                         
Hit:6 http://repository.spotify.com stable InRelease                                                                                                         
Get:8 http://ppa.launchpad.net/noobslab/icons/ubuntu xenial InRelease [17.5 kB]                                                                              
Ign:9 http://mirrors.xmission.com/linuxmint sonya InRelease                                                                                         
Hit:10 http://ppa.launchpad.net/numix/ppa/ubuntu xenial InRelease              
Hit:11 http://ppa.launchpad.net/webupd8team/brackets/ubuntu xenial InRelease                               
Hit:12 http://mirrors.xmission.com/ubuntu xenial InRelease                                                 
Hit:13 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease                                   
Get:14 http://mirrors.xmission.com/ubuntu xenial-updates InRelease [102 kB]                                
Hit:15 http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu xenial InRelease           
Get:16 http://ppa.launchpad.net/noobslab/icons/ubuntu xenial/main Sources [17.5 kB]                                    
Get:17 http://ppa.launchpad.net/noobslab/icons/ubuntu xenial/main amd64 Packages [11.9 kB]                                       
Get:18 http://ppa.launchpad.net/noobslab/icons/ubuntu xenial/main i386 Packages [11.9 kB]
Get:19 http://mirrors.xmission.com/ubuntu xenial-backports InRelease [102 kB]                                                  
Get:20 http://mirrors.xmission.com/linuxmint sonya Release [24.1 kB]
Get:21 http://mirrors.xmission.com/ubuntu xenial-updates/main amd64 Packages [572 kB]
Get:22 http://mirrors.xmission.com/ubuntu xenial-updates/main i386 Packages [553 kB]                                                                                                                                                                                                                                         
Get:23 http://mirrors.xmission.com/ubuntu xenial-updates/universe amd64 Packages [493 kB]                                                                                                                                                                                                                                    
Get:24 http://mirrors.xmission.com/ubuntu xenial-updates/universe i386 Packages [474 kB]                                                                                                                                                                                                                                     
Get:25 http://mirrors.xmission.com/ubuntu xenial-backports/main amd64 Packages [4,680 B]                                                                                                                                                                                                                                     
Get:26 http://mirrors.xmission.com/ubuntu xenial-backports/main i386 Packages [4,688 B]                                                                                                                                                                                                                                      
97% [24 Packages store 0 B]                                                                                                                                                                                                                     Get:27 http://mirrors.xmission.com/linuxmint sonya Release.gpg [819 B]         
Get:28 http://mirrors.xmission.com/linuxmint sonya/main amd64 Packages [18.1 kB]
Get:29 http://mirrors.xmission.com/linuxmint sonya/main i386 Packages [17.5 kB]
Get:30 http://mirrors.xmission.com/linuxmint sonya/backport amd64 Packages [72.4 kB]
Get:31 http://mirrors.xmission.com/linuxmint sonya/backport i386 Packages [72.9 kB]
Fetched 2,671 kB in 18s (147 kB/s)                                             
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  esound-common gcc-5-base:i386 glib-networking:i386 gstreamer0.10-plugins-base:i386 gstreamer0.10-plugins-good:i386 gtk2-engines:i386 gtk2-engines-murrine:i386 gtk2-engines-oxygen:i386 gtk2-engines-pixbuf:i386 gvfs:i386 gvfs-libs:i386
  ibus-gtk:i386 libaa1:i386 libacl1:i386 libaio1:i386 libao4:i386 libasound2:i386 libasound2-plugins:i386 libasyncns0:i386 libatk1.0-0:i386 libattr1:i386 libaudio2:i386 libaudiofile1:i386 libavahi-client3:i386 libavahi-common-data:i386
  libavahi-common3:i386 libavc1394-0:i386 libbsd0:i386 libbz2-1.0:i386 libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386 libcanberra-gtk-module:i386 libcanberra-gtk0:i386 libcanberra0:i386 libcap2:i386 libcapi20-3:i386
  libcdparanoia0:i386 libcomerr2:i386 libcroco3:i386 libcups2:i386 libcupsfilters1:i386 libcupsimage2:i386 libdatrie1:i386 libdbus-1-3:i386 libdbus-glib-1-2:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdrm2:i386 libdv4:i386 libedit2:i386 libelf1:i386 libesd0:i386 libexif12:i386 libexpat1:i386 libffi6:i386 libflac8:i386 libfluidsynth1:i386 libfontconfig1:i386 libfreetype6:i386 libgail-common:i386 libgail18:i386
  libgck-1-0:i386 libgconf-2-4:i386 libgcr-base-3-1:i386 libgcrypt20:i386 libgd3:i386 libgdbm3:i386 libgdk-pixbuf2.0-0:i386 libgettextpo0:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libglib2.0-0:i386
  libglu1-mesa:i386 libgmp10:i386 libgnutls30:i386 libgpg-error0:i386 libgphoto2-6:i386 libgphoto2-port12:i386 libgpm2:i386 libgraphite2-3:i386 libgssapi-krb5-2:i386 libgstreamer-plugins-base0.10-0:i386
  libgstreamer-plugins-base1.0-0:i386 libgstreamer0.10-0:i386 libgstreamer1.0-0:i386 libgtk2.0-0:i386 libgudev-1.0-0:i386 libharfbuzz0b:i386 libhogweed4:i386 libibus-1.0-5:i386 libice6:i386 libicu55:i386 libidn11:i386 libiec61883-0:i386
  libieee1284-3:i386 libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 libjson-c2:i386 libk5crypto3:i386 libkeyutils1:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms2-2:i386 libllvm3.8:i386 libltdl7:i386
  liblzma5:i386 libmad0:i386 libmikmod3:i386 libmng2:i386 libmpg123-0:i386 libncurses5:i386 libncursesw5:i386 libnettle6:i386 libnspr4:i386 libnss3:i386 libodbc1:i386 libogg0:i386 libopenal1:i386 liborc-0.4-0:i386 libp11-kit0:i386
  libpango-1.0-0:i386 libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386 libpciaccess0:i386 libpcre3:i386 libpixman-1-0:i386 libpng12-0:i386 libproxy1v5:i386 libpulse-mainloop-glib0:i386 libpulse0:i386 libpulsedsp:i386 libqt4-dbus:i386
  libqt4-declarative:i386 libqt4-designer:i386 libqt4-network:i386 libqt4-opengl:i386 libqt4-qt3support:i386 libqt4-script:i386 libqt4-scripttools:i386 libqt4-sql:i386 libqt4-svg:i386 libqt4-test:i386 libqt4-xml:i386
  libqt4-xmlpatterns:i386 libqtcore4:i386 libqtdbus4:i386 libqtgui4:i386 libqtwebkit4:i386 libraw1394-11:i386 libreadline6:i386 librsvg2-2:i386 librsvg2-common:i386 libsamplerate0:i386 libsane:i386 libsdl-image1.2:i386
  libsdl-mixer1.2:i386 libsdl-net1.2:i386 libsdl-ttf2.0-0:i386 libsdl1.2debian:i386 libsecret-1-0:i386 libselinux1:i386 libshout3:i386 libslang2:i386 libsm6:i386 libsndfile1:i386 libsoup-gnome2.4-1:i386 libsoup2.4-1:i386 libspeex1:i386
  libspeexdsp1:i386 libsqlite3-0:i386 libssl1.0.0:i386 libstdc++5:i386 libstdc++6:i386 libsystemd0:i386 libtag1v5:i386 libtag1v5-vanilla:i386 libtasn1-6:i386 libtdb1:i386 libthai0:i386 libtheora0:i386 libtiff5:i386 libtinfo5:i386
  libudev1:i386 libunistring0:i386 libusb-1.0-0:i386 libuuid1:i386 libv4l-0:i386 libv4lconvert0:i386 libvisual-0.4-0:i386 libvorbis0a:i386 libvorbisenc2:i386 libvorbisfile3:i386 libvpx3:i386 libwavpack1:i386 libwebp5:i386 libwrap0:i386
  libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxaw7:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb1:i386 libxcomposite1:i386
  libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxml2:i386 libxmu6:i386 libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxshmfence1:i386 libxslt1.1:i386 libxss1:i386
  libxt6:i386 libxtst6:i386 libxv1:i386 libxxf86vm1:i386 odbcinst odbcinst1debian2:i386 odbcinst1debian2 xaw3dg:i386 zlib1g:i386
Suggested packages:
  murrine-themes:i386 kde-config-gtk-style:i386 nas:i386 libcanberra-pulse:i386 isdnutils-doc:i386 libdv-bin:i386 oss-compat:i386 pulseaudio-esound-compat:i386 rng-tools:i386 libgd-tools:i386 gnutls-bin:i386 gphoto2:i386 gpm:i386
  krb5-doc:i386 krb5-user:i386 libvisual-0.4-plugins:i386 gstreamer-codec-install:i386 | gnome-codec-install:i386 gstreamer0.10-tools:i386 gstreamer1.0-tools:i386 jackd2:i386 libmyodbc:i386 odbc-postgresql:i386 tdsodbc:i386
  unixodbc-bin:i386 libportaudio2:i386 libqt4-declarative-folderlistmodel:i386 libqt4-declarative-gestures:i386 libqt4-declarative-particles:i386 libqt4-declarative-shaders:i386 qt4-qmlviewer:i386 libqt4-dev:i386 qt4-qtconfig:i386
  libraw1394-doc:i386 librsvg2-bin:i386 hplip:i386 libsane-extras:i386 speex:i386
Recommended packages:
  gstreamer0.10-x:i386 libtxc-dxtn-s2tc:i386 | libtxc-dxtn-s2tc0:i386 | libtxc-dxtn0:i386 gstreamer1.0-plugins-base:i386 libqt4-sql-mysql:i386 | libqt4-sql-odbc:i386 | libqt4-sql-psql:i386 | libqt4-sql-sqlite:i386 qt-at-spi:i386
  musescore-soundfont-gm:i386 | fluid-soundfont-gm:i386 | freepats:i386 xml-core:i386
The following NEW packages will be installed:
  esound-common gcc-5-base:i386 glib-networking:i386 gstreamer0.10-plugins-base:i386 gstreamer0.10-plugins-good:i386 gtk2-engines:i386 gtk2-engines-murrine:i386 gtk2-engines-oxygen:i386 gtk2-engines-pixbuf:i386 gvfs:i386 gvfs-libs:i386
  ia32-libs ibus-gtk:i386 libaa1:i386 libacl1:i386 libaio1:i386 libao4:i386 libasound2:i386 libasound2-plugins:i386 libasyncns0:i386 libatk1.0-0:i386 libattr1:i386 libaudio2:i386 libaudiofile1:i386 libavahi-client3:i386
  libavahi-common-data:i386 libavahi-common3:i386 libavc1394-0:i386 libbsd0:i386 libbz2-1.0:i386 libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386 libcanberra-gtk-module:i386 libcanberra-gtk0:i386 libcanberra0:i386 libcap2:i386
  libcapi20-3:i386 libcdparanoia0:i386 libcomerr2:i386 libcroco3:i386 libcups2:i386 libcupsfilters1:i386 libcupsimage2:i386 libdatrie1:i386 libdbus-1-3:i386 libdbus-glib-1-2:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libdv4:i386 libedit2:i386 libelf1:i386 libesd0:i386 libexif12:i386 libexpat1:i386 libffi6:i386 libflac8:i386 libfluidsynth1:i386 libfontconfig1:i386 libfreetype6:i386
  libgail-common:i386 libgail18:i386 libgck-1-0:i386 libgconf-2-4:i386 libgcr-base-3-1:i386 libgcrypt20:i386 libgd3:i386 libgdbm3:i386 libgdk-pixbuf2.0-0:i386 libgettextpo0:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386
  libglapi-mesa:i386 libglib2.0-0:i386 libglu1-mesa:i386 libgmp10:i386 libgnutls30:i386 libgpg-error0:i386 libgphoto2-6:i386 libgphoto2-port12:i386 libgpm2:i386 libgraphite2-3:i386 libgssapi-krb5-2:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer-plugins-base1.0-0:i386 libgstreamer0.10-0:i386 libgstreamer1.0-0:i386 libgtk2.0-0:i386 libgudev-1.0-0:i386 libharfbuzz0b:i386 libhogweed4:i386 libibus-1.0-5:i386 libice6:i386
  libicu55:i386 libidn11:i386 libiec61883-0:i386 libieee1284-3:i386 libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 libjson-c2:i386 libk5crypto3:i386 libkeyutils1:i386 libkrb5-3:i386 libkrb5support0:i386
  liblcms2-2:i386 libllvm3.8:i386 libltdl7:i386 liblzma5:i386 libmad0:i386 libmikmod3:i386 libmng2:i386 libmpg123-0:i386 libncurses5:i386 libncursesw5:i386 libnettle6:i386 libnspr4:i386 libnss3:i386 libodbc1:i386 libogg0:i386
  libopenal1:i386 liborc-0.4-0:i386 libp11-kit0:i386 libpango-1.0-0:i386 libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386 libpciaccess0:i386 libpcre3:i386 libpixman-1-0:i386 libpng12-0:i386 libproxy1v5:i386 libpulse-mainloop-glib0:i386
  libpulse0:i386 libpulsedsp:i386 libqt4-dbus:i386 libqt4-declarative:i386 libqt4-designer:i386 libqt4-network:i386 libqt4-opengl:i386 libqt4-qt3support:i386 libqt4-script:i386 libqt4-scripttools:i386 libqt4-sql:i386 libqt4-svg:i386
  libqt4-test:i386 libqt4-xml:i386 libqt4-xmlpatterns:i386 libqtcore4:i386 libqtdbus4:i386 libqtgui4:i386 libqtwebkit4:i386 libraw1394-11:i386 libreadline6:i386 librsvg2-2:i386 librsvg2-common:i386 libsamplerate0:i386 libsane:i386
  libsdl-image1.2:i386 libsdl-mixer1.2:i386 libsdl-net1.2:i386 libsdl-ttf2.0-0:i386 libsdl1.2debian:i386 libsecret-1-0:i386 libselinux1:i386 libshout3:i386 libslang2:i386 libsm6:i386 libsndfile1:i386 libsoup-gnome2.4-1:i386
  libsoup2.4-1:i386 libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl1.0.0:i386 libstdc++5:i386 libstdc++6:i386 libsystemd0:i386 libtag1v5:i386 libtag1v5-vanilla:i386 libtasn1-6:i386 libtdb1:i386 libthai0:i386 libtheora0:i386
  libtiff5:i386 libtinfo5:i386 libudev1:i386 libunistring0:i386 libusb-1.0-0:i386 libuuid1:i386 libv4l-0:i386 libv4lconvert0:i386 libvisual-0.4-0:i386 libvorbis0a:i386 libvorbisenc2:i386 libvorbisfile3:i386 libvpx3:i386 libwavpack1:i386
  libwebp5:i386 libwrap0:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxaw7:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb1:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxml2:i386 libxmu6:i386 libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxshmfence1:i386
  libxslt1.1:i386 libxss1:i386 libxt6:i386 libxtst6:i386 libxv1:i386 libxxf86vm1:i386 odbcinst odbcinst1debian2:i386 odbcinst1debian2 xaw3dg:i386 zlib1g:i386
0 upgraded, 240 newly installed, 0 to remove and 8 not upgraded.
1 not fully installed or removed.
Need to get 83.7 MB of archives.
After this operation, 409 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
```

```
myname@hostname ~/Downloads $ lsb_release -a
No LSB modules are available.
Distributor ID:    LinuxMint
Description:    Linux Mint 18.2 Sonya
Release:    18.2
Codename:    sonya
myname@hostname ~/Downloads $ cat /etc/*-release
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=18.2
DISTRIB_CODENAME=sonya
DISTRIB_DESCRIPTION="Linux Mint 18.2 Sonya"
NAME="Linux Mint"
VERSION="18.2 (Sonya)"
ID=linuxmint
ID_LIKE=ubuntu
PRETTY_NAME="Linux Mint 18.2"
VERSION_ID="18.2"
HOME_URL="http://www.linuxmint.com/"
SUPPORT_URL="http://forums.linuxmint.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/linuxmint/"
VERSION_CODENAME=sonya
UBUNTU_CODENAME=xenial
cat: /etc/upstream-release: Is a directory
myname@hostname ~/Downloads $ cat /var/log/installer/media-info
Linux Mint 18.2 "Sonya" - Release amd64 20170628
myname@hostname ~/Downloads $ grep -Ev '(^#|^ *$|deb-src)' /ect/apt/sources.list /etc/apt/sources.list.d/*
grep: /ect/apt/sources.list: No such file or directory
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/nilarimogard-webupd8-xenial.list:deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main
/etc/apt/sources.list.d/noobslab-icons-xenial.list:deb http://ppa.launchpad.net/noobslab/icons/ubuntu xenial main
/etc/apt/sources.list.d/numix-ppa-xenial.list:deb http://ppa.launchpad.net/numix/ppa/ubuntu xenial main
/etc/apt/sources.list.d/official-package-repositories.list:deb http://mirrors.xmission.com/linuxmint sonya main upstream import backport 
/etc/apt/sources.list.d/official-package-repositories.list:deb http://mirrors.xmission.com/ubuntu xenial main restricted universe multiverse
/etc/apt/sources.list.d/official-package-repositories.list:deb http://mirrors.xmission.com/ubuntu xenial-updates main restricted universe multiverse
/etc/apt/sources.list.d/official-package-repositories.list:deb http://mirrors.xmission.com/ubuntu xenial-backports main restricted universe multiverse
/etc/apt/sources.list.d/official-package-repositories.list:deb http://security.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse
/etc/apt/sources.list.d/official-package-repositories.list:deb http://archive.canonical.com/ubuntu/ xenial partner
/etc/apt/sources.list.d/spotify.list:deb http://repository.spotify.com stable non-free
/etc/apt/sources.list.d/webupd8team-brackets-xenial.list:deb http://ppa.launchpad.net/webupd8team/brackets/ubuntu xenial main
/etc/apt/sources.list.d/webupd8team-java-xenial.list:deb http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main
/etc/apt/sources.list.d/webupd8team-tor-browser-xenial.list:deb http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu xenial main



```


It looks to me like a lot of those libraries that it's requesting are 32bit which is odd since I see 64 bit drivers listed, so it's odd that the installer wouldn't just adapt.  I just don't remember a list like this in the past.  It's recommending "murrine-themes" :P  I'm sure that'll contribute heavily to the proper functioning of my printer! :D

---

### Post by SeijiSensei on 2017-07-06
Are you connecting to the printer [over the network]("http://support.brother.com/g/s/id/htmldoc/mfc/cv_mfcj870dw/use/index.html#GUID-D794C1F8-D421-4575-8F28-D5B169D851FC_230")?  Does it have its own IP address?  If so, try pointing a browser at [http://localhost:631/](http://localhost:631/) on the machine you want to print from.  Click Add Printers, enter your username and password, and see if the device appears as a "Discovered Network Printer."  If so, choose that device and follow the prompts.  If there are multiple entries for the same printer, choose the first in the list.

---

### Post by sp40140 on 2017-07-07
@Sensei.. This is all in one. So, scanner will be problem. The printer will work without any driver install. But for scanner you do need to install packages from Brother.
@Kevin.. What you can try is delete the printer (if you have it installed). And then only try to install the deb files for scanner. That's what I did for my MFC-240c.
The dependency list IS bit long (which is weird).

---

### Post by steeldriver on 2017-07-07
It's presumably a long list of dependencies because mfcj870dwlpr-3.0.0-1.**i386.de**b and mfcj870dwcupswrapper-3.0.0-1.**i386.deb** are 32-bit package and you're installing them on a 64-bit OS (so it needs to install a whole 32-bit subsystem for them)

---

