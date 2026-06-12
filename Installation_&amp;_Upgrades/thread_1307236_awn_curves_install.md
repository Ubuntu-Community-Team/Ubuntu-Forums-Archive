---
title: "awn curves install"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Shamsul007 on 2009-10-30
> shamsul@shamsul-laptop:~$ sudo rm -f /usr/local/bin/awn*
[sudo] password for shamsul: 
shamsul@shamsul-laptop:~$ sudo rm -f /usr/local/bin/awn*
shamsul@shamsul-laptop:~$ sudo rm -f /usr/local/bin/avant*
shamsul@shamsul-laptop:~$ sudo rm -rf /usr/local/lib/awn
shamsul@shamsul-laptop:~$ sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
shamsul@shamsul-laptop:~$ sudo rm -f /usr/local/share/applications/avant*
shamsul@shamsul-laptop:~$ sudo rm -f /usr/local/share/applications/awn*
shamsul@shamsul-laptop:~$ sudo rm -rf /usr/local/share/avant-window-navigator
shamsul@shamsul-laptop:~$ sudo rm -f /usr/local/lib/libawn*
shamsul@shamsul-laptop:~$ sudo rm -rf /usr/local/include/libawn
shamsul@shamsul-laptop:~$ sudo rm -f /usr/local/lib/libawn*
shamsul@shamsul-laptop:~$ sudo rm -f /usr/local/lib/pkgconfig/awn.pc
shamsul@shamsul-laptop:~$ sudo rm -rf /usr/local/share/awn-core-applets
shamsul@shamsul-laptop:~$ sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/
shamsul@shamsul-laptop:~$ sudo apt-get install bzr m4 gnome-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bzr is already the newest version.
m4 is already the newest version.
gnome-common is already the newest version.
The following packages were automatically installed and are no longer required:
  libsnack2-alsa libkopete4 libindicate-qt0 tcl8.5 tk8.5 libqca2-plugin-ossl
  tcl-tls libmsn0.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shamsul@shamsul-laptop:~$ sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
autotools-dev is already the newest version.
autotools-dev set to manually installed.
libgnome2-common is already the newest version.
E: Couldn't find package libgnome-vfs-dev
shamsul@shamsul-laptop:~$ bzr co [http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves](http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves) awn-curves

Format <RepositoryFormatKnit1> for [http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves/.bzr/](http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves/.bzr/) is deprecated - please use 'bzr upgrade' to get better performance
shamsul@shamsul-laptop:~$                                                      
shamsul@shamsul-laptop:~$ cd awn-curves
shamsul@shamsul-laptop:~/awn-curves$ ./autogen.sh && make
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.64
checking for automake >= 1.9...
  testing automake-1.11... found 1.11
checking for libtool >= 1.5...
  testing libtoolize... found 2.2.6
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.22.2
checking for intltool >= 0.30...
  testing intltoolize... found 0.41.0
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: You should add the contents of the following files to `aclocal.m4':
libtoolize:   `/usr/share/aclocal/libtool.m4'
libtoolize:   `/usr/share/aclocal/ltoptions.m4'
libtoolize:   `/usr/share/aclocal/ltversion.m4'
libtoolize:   `/usr/share/aclocal/ltsugar.m4'
libtoolize:   `/usr/share/aclocal/lt~obsolete.m4'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.in and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Running intltoolize...
Running aclocal-1.11...
configure.in:93: warning: macro `AM_GCONF_SOURCE_2' not found in library
Running autoconf...
configure.in:93: error: possibly undefined macro: AM_GCONF_SOURCE_2
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
shamsul@shamsul-laptop:~/awn-curves$ sudo make install
make: *** No rule to make target `install'. Stop.
shamsul@shamsul-laptop:~/awn-curves$ 
shamsul@shamsul-laptop:~/awn-curves$ wget [http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/avant-window-navigator-bzr_0.2.0-bzr158-1_i386.deb](http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/avant-window-navigator-bzr_0.2.0-bzr158-1_i386.deb) [http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/awn-core-applets-bzr_0.2.0-bzr296-1_i386.deb](http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/awn-core-applets-bzr_0.2.0-bzr296-1_i386.deb) [http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/libawn-bzr-dev_0.2.0-bzr158-1_i386.deb](http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/libawn-bzr-dev_0.2.0-bzr158-1_i386.deb) [http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/libawn-bzr_0.2.0-bzr158-1_i386.deb](http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/libawn-bzr_0.2.0-bzr158-1_i386.deb) [http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/python-libawn-bzr_0.2.0-bzr158-1_i386.deb](http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/python-libawn-bzr_0.2.0-bzr158-1_i386.deb) 
--2009-10-31 03:41:07--  [http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/avant-window-navigator-bzr_0.2.0-bzr158-1_i386.deb](http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/avant-window-navigator-bzr_0.2.0-bzr158-1_i386.deb)
Resolving download.tuxfamily.org... 212.85.158.13
Connecting to download.tuxfamily.org|212.85.158.13|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 303978 (297K) [application/x-debian-package]
Saving to: `avant-window-navigator-bzr_0.2.0-bzr158-1_i386.deb'

100%[======================================>] 303,978      373K/s   in 0.8s    

2009-10-31 03:41:08 (373 KB/s) - `avant-window-navigator-bzr_0.2.0-bzr158-1_i386.deb' saved [303978/303978]

--2009-10-31 03:41:08--  [http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/awn-core-applets-bzr_0.2.0-bzr296-1_i386.deb](http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/awn-core-applets-bzr_0.2.0-bzr296-1_i386.deb)
Reusing existing connection to download.tuxfamily.org:80.
HTTP request sent, awaiting response... 200 OK
Length: 2580420 (2.5M) [application/x-debian-package]
Saving to: `awn-core-applets-bzr_0.2.0-bzr296-1_i386.deb'

100%[======================================>] 2,580,420    517K/s   in 5.0s    

2009-10-31 03:41:13 (505 KB/s) - `awn-core-applets-bzr_0.2.0-bzr296-1_i386.deb' saved [2580420/2580420]

--2009-10-31 03:41:13--  [http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/libawn-bzr-dev_0.2.0-bzr158-1_i386.deb](http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/libawn-bzr-dev_0.2.0-bzr158-1_i386.deb)
Reusing existing connection to download.tuxfamily.org:80.
HTTP request sent, awaiting response... 200 OK
Length: 72138 (70K) [application/x-debian-package]
Saving to: `libawn-bzr-dev_0.2.0-bzr158-1_i386.deb'

100%[======================================>] 72,138      --.-K/s   in 0.1s    

2009-10-31 03:41:14 (708 KB/s) - `libawn-bzr-dev_0.2.0-bzr158-1_i386.deb' saved [72138/72138]

--2009-10-31 03:41:14--  [http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/libawn-bzr_0.2.0-bzr158-1_i386.deb](http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/libawn-bzr_0.2.0-bzr158-1_i386.deb)
Reusing existing connection to download.tuxfamily.org:80.
HTTP request sent, awaiting response... 200 OK
Length: 63970 (62K) [application/x-debian-package]
Saving to: `libawn-bzr_0.2.0-bzr158-1_i386.deb'

100%[======================================>] 63,970      --.-K/s   in 0.09s   

2009-10-31 03:41:14 (698 KB/s) - `libawn-bzr_0.2.0-bzr158-1_i386.deb' saved [63970/63970]

--2009-10-31 03:41:14--  [http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/python-libawn-bzr_0.2.0-bzr158-1_i386.deb](http://download.tuxfamily.org/syzygy42/static/awn-curves-archive/i386/python-libawn-bzr_0.2.0-bzr158-1_i386.deb)
Reusing existing connection to download.tuxfamily.org:80.
HTTP request sent, awaiting response... 200 OK
Length: 27650 (27K) [application/x-debian-package]
Saving to: `python-libawn-bzr_0.2.0-bzr158-1_i386.deb'

100%[======================================>] 27,650      --.-K/s   in 0.04s   

2009-10-31 03:41:14 (726 KB/s) - `python-libawn-bzr_0.2.0-bzr158-1_i386.deb' saved [27650/27650]

FINISHED --2009-10-31 03:41:14--
Downloaded: 5 files, 2.9M in 6.0s (495 KB/s)
shamsul@shamsul-laptop:~/awn-curves$ sudo gdebi *.deb
Reading package lists: Donekarmic-security/multiverse Packages: 94   
Reading state information: Done
Reading state information: Done
Reading state information: Done
This package is uninstallable
Conflicts with the installed package 'avant-window-navigator'


can you tell me where im going wrong and whats the problem?

sorry if its in wrong place

running ubuntu 9.10

---

### Post by jaden93 on 2009-11-01
uninstall avant-window-navigator  

```
sudo aptitude purge avant-window-navigator
```

---

