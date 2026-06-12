---
title: "Stellarium 0.10.2 on Hardy"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by MaindotC on 2009-09-07
If any of you have refused to move to Jaunty, as I have because my video card(s) are no longer supported, and you just happen to take Solar Astronomy and the professor demands you pay $5 for the software "Starry Night", check out [Stellarium for Linux](http://www.stellarium.org).  He said it was an acceptable substitution and I couldn't get Starry Night to Wine properly anyway.  It does everything I need to get my labs done, and the interface is sweet.

Unfortunately, the latest version requires some versions of packages that are not immediately available on 8.04.3 so this tutorial will show you how to install it.  First, I suggest for the sake of simplicity, install the version from the repos so it makes a nice little icon and menu entry for you:

```

sudo apt-get install stellarium

```

My professor uses Gentoo so he ran into the same issue w/ QT4 so the following is an excerpt from an email I sent him:

```

x@x:~$ cd Desktop/stellarium-0.10.2/

```

Make these directories per the Stellarium compilation on Linux directions
```

x@x:~/Desktop/stellarium-0.10.2$ mkdir -p builds/unix

```

In Ubuntu, the package manager I use is called APT and I have to enable a repository called "backports".  This will install my libqt4-dev 4.4.0 (from 4.3.4) and cmake 2.7 versions which are necessary for this installation.  If Gentoo operates on the concept of repositories, I'm sure you have a similar option. The list of repositories is kept in /etc/apt/sources.list:
```

x@x:~/Desktop/stellarium-0.10.2$ sudo nano /etc/apt/sources.list
[sudo] password for x: 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

```
Update my repository list:
```

x@x:~/Desktop/stellarium-0.10.2$ sudo apt-get update

```
Now I'm going to install the following packages:  gettext, cmake, libqt4-dev, libqt4-opengl-dev libbost-dev, and build-essential (package that contains C++ compiler and development files)  They all have a 200MB+ of depdencies:
```

x@x:~/Desktop/stellarium-0.10.2$ sudo apt-get install gettext cmake libqt4-dev libqt4-opengl-dev libboost-dev build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  comerr-dev cpp-3.3 dpkg-dev g++ g++-3.3 g++-4.2 gcc-3.3 gcc-3.3-base
  libaudio-dev libaudio2 libc6-dev libexpat1-dev libfontconfig1-dev
  libfreetype6-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev
  libglu1-xorg-dev libice-dev libjpeg62-dev libkadm55 libkrb5-dev liblcms1-dev
  libmng-dev libpng12-dev libpq-dev libpq5 libpthread-stubs0
  libpthread-stubs0-dev libqt4-assistant libqt4-dbus libqt4-designer
  libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script
  libqt4-sql libqt4-svg libqt4-test libqt4-webkit libqt4-xml
  libqt4-xmlpatterns libqtcore4 libqtgui4 libsm-dev libsqlite0-dev libssl-dev
  libstdc++5 libstdc++5-3.3-dev libstdc++6-4.2-dev libtimedate-perl libx11-dev
  libxau-dev libxcb-xlib0-dev libxcb1-dev libxcursor-dev libxdmcp-dev
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxmu-dev
  libxmu-headers libxrandr-dev libxrender-dev libxt-dev linux-libc-dev
  mesa-common-dev patch x11proto-core-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev
  x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev
Suggested packages:
  debian-keyring g++-multilib gcc-3.3-doc g++-4.2-multilib gcc-4.2-doc
  libstdc++6-4.2-dbg cvs gettext-doc nas glibc-doc manpages-dev libglib2.0-doc
  krb5-doc postgresql-doc-8.3 firebird2.0-dev libiodbc2-dev
  libmysqlclient15-dev libsqlite3-dev qt4-dev-tools qt4-doc sqlite-doc
  libstdc++5-3.3-doc libstdc++6-4.2-doc diff-doc
Recommended packages:
  libboost-date-time-dev libboost-doc libboost-filesystem-dev
  libboost-graph-dev libboost-iostreams-dev libboost-program-options-dev
  libboost-python-dev libboost-regex-dev libboost-serialization-dev
  libboost-signals-dev libboost-test-dev libboost-thread-dev libboost-wave-dev
  libqt4-sql-mysql libqt4-sql-odbc libqt4-sql-psql libqt4-sql-sqlite
  libqt4-sql-sqlite2 qt4-qtconfig
The following NEW packages will be installed:
  build-essential cmake comerr-dev cpp-3.3 dpkg-dev g++ g++-3.3 g++-4.2
  gcc-3.3 gcc-3.3-base gettext libaudio-dev libaudio2 libboost-dev libc6-dev
  libexpat1-dev libfontconfig1-dev libfreetype6-dev libgl1-mesa-dev
  libglib2.0-dev libglu1-mesa-dev libglu1-xorg-dev libice-dev libjpeg62-dev
  libkadm55 libkrb5-dev liblcms1-dev libmng-dev libpng12-dev libpq-dev libpq5
  libpthread-stubs0 libpthread-stubs0-dev libqt4-assistant libqt4-dbus
  libqt4-designer libqt4-dev libqt4-help libqt4-network libqt4-opengl
  libqt4-opengl-dev libqt4-qt3support libqt4-script libqt4-sql libqt4-svg
  libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4
  libsm-dev libsqlite0-dev libssl-dev libstdc++5 libstdc++5-3.3-dev
  libstdc++6-4.2-dev libtimedate-perl libx11-dev libxau-dev libxcb-xlib0-dev
  libxcb1-dev libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev
  libxi-dev libxinerama-dev libxmu-dev libxmu-headers libxrandr-dev
  libxrender-dev libxt-dev linux-libc-dev mesa-common-dev patch
  x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-render-dev x11proto-xext-dev
  x11proto-xinerama-dev xtrans-dev zlib1g-dev
0 upgraded, 87 newly installed, 0 to remove and 15 not upgraded.
Need to get 58.8MB of archives.
After this operation, 218MB of additional disk space will be used.
Do you want to continue [Y/n]

```
Those packages automatically install and next I'll edit the CMakeLists.txt file so it doesn't complain about QT4.  Look for this line:
```

SET(QT_MIN_VERSION "4.4.2")

```
Change it to:
```

SET(QT_MIN_VERSION "4.4.0")

```
Save, and install using the following commands:
```

x@x:~/Desktop/stellarium-0.10.2$ cd builds/unix/
x@x:~/Desktop/stellarium-0.10.2/builds/unix$ cmake ../..
-- Looking for Q_WS_X11
-- Looking for Q_WS_X11 - found
-- Looking for Q_WS_WIN
-- Looking for Q_WS_WIN - not found.
-- Looking for Q_WS_QWS
-- Looking for Q_WS_QWS - not found.
-- Looking for Q_WS_MAC
-- Looking for Q_WS_MAC - not found.
-- Found Qt-Version 4.4.0
-- Performing Test ICONV_SECOND_ARGUMENT_IS_CONST
-- Performing Test ICONV_SECOND_ARGUMENT_IS_CONST - Failed
-- Found Iconv: /usr/lib/libc.so
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so - found
-- Looking for gethostbyname
-- Looking for gethostbyname - found
-- Looking for connect
-- Looking for connect - found
-- Looking for remove
-- Looking for remove - found
-- Looking for shmat
-- Looking for shmat - found
-- Looking for IceConnectionNumber in ICE
-- Looking for IceConnectionNumber in ICE - found
-- Found X11: /usr/lib/libX11.so
-- Found ZLIB: /usr/lib/libz.so
-- Found PNG: /usr/lib/libpng.so
-- Found JPEG: /usr/lib/libjpeg.so
-- Boost version: 1.34.1
-- Found the following Boost libraries:
-- Found FreeType2: library: /usr/lib/libfreetype.so, include path: /usr/include/freetype2
-- Check if the system is big endian
-- Searching 16 bit integer
-- Looking for sys/types.h
-- Looking for sys/types.h - found
-- Looking for stdint.h
-- Looking for stdint.h - found
-- Looking for stddef.h
-- Looking for stddef.h - found
-- Check size of unsigned short
-- Check size of unsigned short - done
-- Using unsigned short
-- Check if the system is big endian - little endian
-- Configuring done
-- Generating done
-- Build files have been written to: /home/x/Desktop/stellarium-0.10.2/builds/unix

```
Make:
```

x@x:~/Desktop/stellarium-0.10.2/builds/unix$ make
Scanning dependencies of target GenerateUiHeaders
[  0%] Generating ui_locationDialogGui.h
[  0%] Generating ui_helpDialogGui.h
[  0%] Generating ui_dateTimeDialogGui.h
[  0%] Generating ui_viewDialog.h
Warning: name gridLayout is already used
[  0%] Generating ui_searchDialogGui.h
[  0%] Generating ui_configurationDialog.h
[  0%] Generating ui_downloadPopup.h
[  2%] Built target GenerateUiHeaders
...
...
[ 79%] Generating sr.gmo
[ 79%] Generating sv.gmo
[ 79%] Generating te.gmo
[ 79%] Generating th.gmo
[ 79%] Generating tl.gmo
[ 79%] Generating tr.gmo
[ 79%] Generating uk.gmo
[ 79%] Generating vi.gmo
[ 79%] Generating zh_CN.gmo
[ 79%] Generating zh_HK.gmo
[ 79%] Generating zh_TW.gmo
[100%] Built target translations-stellarium-skyculture

```
In order for the binary executable (and other files) to be placed in /usr/bin (and other locations) it needs root permissions so run this command as sudo:
```

x@x:~/Desktop/stellarium-0.10.2/builds/unix$ sudo make install
[  2%] Built target GenerateUiHeaders
[ 57%] Built target stellarium
[ 58%] Built target testStelSphereGeometry
[ 58%] Built target testdates
[ 59%] Built target ManPages
[ 79%] Built target translations-stellarium
[100%] Built target translations-stellarium-skycultures
Install the project...
-- Install configuration: "Release"
-- Up-to-date: /usr/local/share/stellarium/data/stellarium.ico
-- Up-to-date: /usr/local/share/stellarium/data/ssystem.ini
-- Up-to-date: /usr/local/share/stellarium/data/zone.tab
...
...
-- Up-to-date: /usr/local/share/stellarium/stars/default/stars_1_0v0_1.cat
-- Up-to-date: /usr/local/share/stellarium/stars/default/stars_2_0v0_1.cat
-- Up-to-date: /usr/local/share/stellarium/stars/default/stars_3_1v0_0.cat
-- Up-to-date: /usr/local/share/stellarium/stars/default/stars_hip_cids_0v0_0.cat
-- Up-to-date: /usr/local/share/stellarium/stars/default/stars_hip_sp_0v0_0.cat
x@x:~/Desktop/stellarium-0.10.2/builds/unix$

```

And you should be done!  Execute the following command to show your version, and you should also see the version number when you start Stellarium from Applications -> Education -> Stellarium.

```

x@x:~/Desktop/stellarium-0.10.2/builds/unix$ stellarium --version
QProcess: Destroyed while process is still running.
Stellarium 0.10.2 
x@x:~/Desktop/stellarium-0.10.2/builds/unix$

```

Be sure to re-comment the backports line so you don't update any more files from backports.

---

