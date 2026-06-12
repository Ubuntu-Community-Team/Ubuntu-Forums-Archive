---
title: "Scanner doesn't work"
date: 2010-09-24
forum: Hardware
---

### Post by satimis on 2010-09-24
Hi folks,

Ubuntu 10.04 64-bit
Epson scanner Perfection 3490 Photo
XSane Image Scanner

Applications -> XSane Image Scanner
Warning```

Failed to open device snapscan:libuse:001:015 invalid argument

```

$ lsusb```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:071f Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 016: ID 04b8:0122 Seiko Epson Corp. Perfection 3590 scanner
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
It is there.

$ scanimage -L```

device `snapscan:libusb:001:016' is a EPSON EPSON Scanner flatbed scanner

```

It is there as well


I found following thread;
[ubuntu] How to get Epson 3490 Scanner working under Hardy H
[http://wwww.ubuntuforums.org/showthread.php?p=9387348](http://wwww.ubuntuforums.org/showthread.php?p=9387348)

but it is for Hardy,

Please advise.  TIA

B.R.
satimis

---

### Post by Hobgoblin on 2010-09-25
> **satimis said:**
> 
I found following thread;
[ubuntu] How to get Epson 3490 Scanner working under Hardy H
[http://wwww.ubuntuforums.org/showthread.php?p=9387348](http://wwww.ubuntuforums.org/showthread.php?p=9387348)

but it is for Hardy,


Did you try?

---

### Post by satimis on 2010-09-25
> **Hobgoblin said:**
> Did you try?

Hi,

I can't find .bin the execute file there```

$ ls -al /usr/share/sane/xsane/
total 1604
drwxr-xr-x 2 root root   4096 2010-06-09 12:19 .
drwxr-xr-x 4 root root   4096 2010-02-28 00:39 ..
-rw-r--r-- 1 root root  32448 2010-06-01 18:53 Mustek-logo.xpm
-rw-r--r-- 1 root root  27183 2010-06-01 18:53 Plustek-logo.xpm
-rw-r--r-- 1 root root  31931 2010-06-01 18:53 sane-epson-logo.xpm
-rw-r--r-- 1 root root  28061 2010-06-01 18:53 sane-hp-logo.xpm
-rw-r--r-- 1 root root  32927 2010-06-01 18:53 sane-umax-logo.xpm
-rw-r--r-- 1 root root  30816 2010-06-01 18:53 sane-xsane-logo.xpm
-rw-r--r-- 1 root root  12611 2010-06-01 18:53 UMAX-logo.xpm
-rw-r--r-- 1 root root 656457 2010-06-01 18:53 xsane-calibration.pnm
-rw-r--r-- 1 root root   1265 2010-06-01 18:53 xsane-eula.txt
-rw-r--r-- 1 root root  14961 2010-06-01 18:53 xsane-gpl.txt
-rw-r--r-- 1 root root  79099 2010-06-01 18:53 xsane-logo.xpm

```

$ ls /usr/share/ | grep xsane
No printout

ls /usr/share/ | grep sane```

sane

```

$ cat /etc/sane.d/epson.conf```

# epson.conf
#
# here are some examples for how to configure the EPSON backend
#
# SCSI scanner:
scsi EPSON
# for the GT-6500:
scsi "EPSON SC"
#
# Parallel port scanner:
#pio 0x278
#pio 0x378
#pio 0x3BC
#
# USB scanner:
# There are two different methods of configuring a USB scanner: libusb and the kernel module
# For any system with libusb support (which is pretty much any recent Linux distribution) the
# following line is sufficient. This however assumes that the connected scanner (or to be more
# accurate, it's device ID) is known to the backend. 
usb
# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
# usb 0x4b8 0x110
# And for the scanner module, use the following configuration:
#usb /dev/usbscanner0
#usb /dev/usb/scanner0

```


B.R.
satimis

---

### Post by ellgor on 2010-09-25
Hi,

Go to this site "Avasys" and get their "imagescan" app, go through the form filling in bit as if you are getting a package for your printer, when on the download page scroll right down and near the bottom will be "imagescan.deb", needs a reboot to work properly.

Regards, Ellgor.

---

### Post by satimis on 2010-09-25
> **ellgor said:**
> Hi,

Go to this site "Avasys" and get their "imagescan" app, go through the form filling in bit as if you are getting a package for your printer, when on the download page scroll right down and near the bottom will be "imagescan.deb", needs a reboot to work properly.


Hi Ellgor,

Thanks for your advice.

On;
[http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do)```


Download for Perfection 3490 PHOTO (for gcc 3.4 or later)
RPM package 	
iscan-2.10.0-1.c2.i386.rpm 	359,714 bytes
iscan-plugin-gt-f520-1.0.0-1.c2.i386.rpm 	125,919 bytes
	
Source file 	
iscan_2.10.0-1.tar.gz 	1,437,822 bytes

```

I can't find iscan-*.deb file

B.R.
satimis

---

### Post by jcolyn on 2010-09-25
> **satimis said:**
> I can't find iscan-*.deb file

B.R.
satimis

You need to install alien to convert .rpm's to .deb ```
sudo apt-get install alien
```cd to the download directory where you downloaded the two .rpm's and use the below terminal command to convert them to .deb

```
sudo alien -k name_of_file.rpm
```

---

### Post by satimis on 2010-09-26
> **jcolyn said:**
> You need to install alien to convert .rpm's to .deb ```
sudo apt-get install alien
```cd to the download directory where you downloaded the two .rpm's and use the below terminal command to convert them to .deb

```
sudo alien -k name_of_file.rpm
```

Hi,

Thanks for your advice.

$ sudo alien -k iscan-2.10.0-1.c2.i386.rpm ```

error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package iscan: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_clean: Compatibility levels before 5 are deprecated.
dh_installdirs
dh_installdirs: Compatibility levels before 5 are deprecated.
dh_installdocs
dh_installdocs: Compatibility levels before 5 are deprecated.
dh_installchangelogs
dh_installchangelogs: Compatibility levels before 5 are deprecated.
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/iscan
dh_compress
dh_compress: Compatibility levels before 5 are deprecated.
dh_makeshlibs
dh_makeshlibs: Compatibility levels before 5 are deprecated.
dh_installdeb
dh_installdeb: Compatibility levels before 5 are deprecated.
dh_shlibdeps
dh_shlibdeps: Compatibility levels before 5 are deprecated.
dpkg-shlibdeps: warning: dependency on libpangox-1.0.so.0 could be avoided if "debian/iscan/usr/bin/iscan" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libjpeg.so.62 could be avoided if "debian/iscan/usr/bin/iscan debian/iscan/usr/lib/sane/libsane-epkowa.so.1.0.15" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libieee1284.so.3 could be avoided if "debian/iscan/usr/bin/iscan debian/iscan/usr/lib/sane/libsane-epkowa.so.1.0.15" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libatk-1.0.so.0 could be avoided if "debian/iscan/usr/bin/iscan" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libnsl.so.1 could be avoided if "debian/iscan/usr/bin/iscan debian/iscan/usr/lib/sane/libsane-epkowa.so.1.0.15" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libgdk_pixbuf-2.0.so.0 could be avoided if "debian/iscan/usr/bin/iscan" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libpango-1.0.so.0 could be avoided if "debian/iscan/usr/bin/iscan" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libgmodule-2.0.so.0 could be avoided if "debian/iscan/usr/bin/iscan" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libpangoxft-1.0.so.0 could be avoided if "debian/iscan/usr/bin/iscan" were not uselessly linked against it (they use none of its symbols).
dh_gencontrol
dh_gencontrol: Compatibility levels before 5 are deprecated.
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: dpkg-gencontrol -ldebian/changelog -Tdebian/iscan.substvars -Pdebian/iscan returned exit code 255
make: *** [binary-arch] Error 9
find: `iscan-2.10.0': No such file or directory

```


$ sudo updatedb

$ locate iscan-* | grep .deb```

/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/changelog
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/control
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/copyright
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan.debhelper.log
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan.postinst.debhelper
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan.postrm.debhelper
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan.substvars
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/rules
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/DEBIAN
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/etc
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/DEBIAN/conffiles
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/DEBIAN/postinst
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/DEBIAN/postrm
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/DEBIAN/shlibs
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/etc/hotplug
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/etc/sane.d
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/etc/hotplug/usb
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/etc/hotplug/usb/iscan-device
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/etc/hotplug/usb/iscan.usermap
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/etc/sane.d/epkowa.conf
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/bin
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/lib
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/bin/iscan
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/lib/iscan
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/lib/libesmod.so
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/lib/libesmod.so.1
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/lib/libesmod.so.1.1.0
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/lib/sane
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/lib/iscan/make-udev-rules
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/lib/sane/libsane-epkowa.la
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/lib/sane/libsane-epkowa.so.1
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/lib/sane/libsane-epkowa.so.1.0.15
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/doc
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/man
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/doc/iscan
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/doc/iscan-2.10.0
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/doc/iscan/changelog.Debian.gz
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/doc/iscan/copyright
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/doc/iscan-2.10.0/AUTHORS
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/doc/iscan-2.10.0/COPYING.LIB.gz
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/doc/iscan-2.10.0/COPYING.gz
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/doc/iscan-2.10.0/EAPL.en.txt
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/doc/iscan-2.10.0/EAPL.ja.txt
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/doc/iscan-2.10.0/NEWS.gz
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/doc/iscan-2.10.0/NEWS.ja.gz
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/doc/iscan-2.10.0/README.gz
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/doc/iscan-2.10.0/README.ja.gz
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/doc/iscan-2.10.0/xinetd.sane
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/de
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/en@boldquot
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/en@quot
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/es
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/fr
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/it
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/ja
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/ko
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/nl
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/pt
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/zh_CN
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/zh_TW
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/de/LC_MESSAGES
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/de/LC_MESSAGES/iscan.mo
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/en@boldquot/LC_MESSAGES
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/en@boldquot/LC_MESSAGES/iscan.mo
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/en@quot/LC_MESSAGES
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/en@quot/LC_MESSAGES/iscan.mo
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/es/LC_MESSAGES
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/es/LC_MESSAGES/iscan.mo
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/fr/LC_MESSAGES
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/fr/LC_MESSAGES/iscan.mo
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/it/LC_MESSAGES
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/it/LC_MESSAGES/iscan.mo
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/ja/LC_MESSAGES
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/ja/LC_MESSAGES/iscan.mo
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/ko/LC_MESSAGES
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/ko/LC_MESSAGES/iscan.mo
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/nl/LC_MESSAGES
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/nl/LC_MESSAGES/iscan.mo
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/pt/LC_MESSAGES
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/pt/LC_MESSAGES/iscan.mo
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/zh_CN/LC_MESSAGES
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/zh_CN/LC_MESSAGES/iscan.mo
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/zh_TW/LC_MESSAGES
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/locale/zh_TW/LC_MESSAGES/iscan.mo
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/man/man1
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/man/man5
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/man/man1/iscan.1.gz
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian/iscan/usr/share/man/man5/sane-epkowa.5.gz

```

Where is the converted package?  TIA

Edit:

The driver is 32-bit
The OS is 64-bit

Would it be the problem?

B.R.
satimis

---

### Post by alan145 on 2010-09-26
you should found the manual of this scanner to found how to settle it

---

### Post by IcarusR on 2010-09-26
It seams that you have a lot of iscan files in 
```
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian
```
I would delete them all & get rid of any trace of iscan & start again.

> Where is the converted package?

It will be in the directory you ran alien from.

> The driver is 32-bit
The OS is 64-bit

Would it be the problem?

You can force dpkg to install, should run OK.

```
dpkg -i --force-architecture xxxx.deb
```

Alternatively you could compile from source & use checkinstall to create a .deb

---

### Post by satimis on 2010-09-26
> **IcarusR said:**
> It seams that you have a lot of iscan files in 
```
/home/satimisu910/Downloads/Imagescan/iscan-2.10.0/debian
```
I would delete them all & get rid of any trace of iscan & start again.

- snip -


iscan-2.10.0

directory and files were created when I ran;

$ sudo alien -k iscan-2.10.0-1.c2.i386.rpm

previously.


$ sudo mv Downloads/Imagescan/iscan-2.10.0 Temp/

$ ls Downloads/Imagescan/
iscan-2.10.0-1.c2.i386.rpm  iscan-plugin-gt-f520-1.0.0-1.c2.i386.rpm
iscan_2.10.0-1.tar.gz

$ cd Downloads/Imagescan/

$ sudo alien -k iscan-2.10.0-1.c2.i386.rpm ```

error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package iscan: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_clean: Compatibility levels before 5 are deprecated.
dh_installdirs
dh_installdirs: Compatibility levels before 5 are deprecated.
dh_installdocs
dh_installdocs: Compatibility levels before 5 are deprecated.
dh_installchangelogs
dh_installchangelogs: Compatibility levels before 5 are deprecated.
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/iscan
dh_compress
dh_compress: Compatibility levels before 5 are deprecated.
dh_makeshlibs
dh_makeshlibs: Compatibility levels before 5 are deprecated.
dh_installdeb
dh_installdeb: Compatibility levels before 5 are deprecated.
dh_shlibdeps
dh_shlibdeps: Compatibility levels before 5 are deprecated.
dpkg-shlibdeps: warning: dependency on libpangox-1.0.so.0 could be avoided if "debian/iscan/usr/bin/iscan" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libjpeg.so.62 could be avoided if "debian/iscan/usr/bin/iscan debian/iscan/usr/lib/sane/libsane-epkowa.so.1.0.15" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libieee1284.so.3 could be avoided if "debian/iscan/usr/bin/iscan debian/iscan/usr/lib/sane/libsane-epkowa.so.1.0.15" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libatk-1.0.so.0 could be avoided if "debian/iscan/usr/bin/iscan" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libnsl.so.1 could be avoided if "debian/iscan/usr/bin/iscan debian/iscan/usr/lib/sane/libsane-epkowa.so.1.0.15" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libgdk_pixbuf-2.0.so.0 could be avoided if "debian/iscan/usr/bin/iscan" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libpango-1.0.so.0 could be avoided if "debian/iscan/usr/bin/iscan" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libgmodule-2.0.so.0 could be avoided if "debian/iscan/usr/bin/iscan" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: dependency on libpangoxft-1.0.so.0 could be avoided if "debian/iscan/usr/bin/iscan" were not uselessly linked against it (they use none of its symbols).
dh_gencontrol
dh_gencontrol: Compatibility levels before 5 are deprecated.
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: dpkg-gencontrol -ldebian/changelog -Tdebian/iscan.substvars -Pdebian/iscan returned exit code 255
make: *** [binary-arch] Error 9
find: `iscan-2.10.0': No such file or directory

```

Still the same.


B.R.
satimis

---

### Post by coffeecat on 2010-09-26
@satimis, this may or may not work for your Epson 3490, but if you substitute the USB ID for your Epson into the method I describe in this thread:

[http://ubuntuforums.org/showthread.php?t=1581065](http://ubuntuforums.org/showthread.php?t=1581065)

.. it might work. From the ID in your lsusb line I'm guessing you would need to do:

```
echo "usb 0x4b8 0x122" | sudo tee -a /etc/sane.d/epson2.conf
```instead of.. 

```
echo "usb 0x4b8 0x838" | sudo tee -a /etc/sane.d/epson2.conf
```... to get an appropriate line into epson2.conf. You'll see from that thread that the OP got their Epson scanner working without the Avasys software.

---

### Post by IcarusR on 2010-09-26
Strange as it worked perfectly on my 10.04 install.

Have you tried compiling from source ??

---

