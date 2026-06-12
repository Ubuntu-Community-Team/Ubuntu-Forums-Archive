---
title: "ATI driver installlation"
date: 2010-03-10
forum: Hardware
---

### Post by fered on 2010-03-10
Hi
I use kubuntu 9.10 and downlaoded ati driver then after this command:
fakeroot sh ati-driver-installer-9-6-x86.x86_64.run --buildpkg Ubuntu/karmic

I saw these messages:

(synaptic:28573): Gtk-WARNING **: cannot open display: :0
Unable to resolve  cdbs.  Please manually install and try again.
Package build failed!                                           
Package build utility output:                                   
building fglrx-installer in fglrx-installer_8.620.orig.tar.gz   
dpkg-buildpackage: warning: using a gain-root-command while being root
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value:
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.620-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 fakeroot debian/rules clean
fakeroot: FAKEROOTKEY set to 1478555234
fakeroot: nested operation not yet supported
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 1
dpkg-buildpackage: warning: using a gain-root-command while being root
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value:
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.620-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
debian/rules:6: /usr/share/cdbs/1/rules/debhelper.mk: No such file or directory
make: *** No rule to make target `/usr/share/cdbs/1/rules/debhelper.mk'.  Stop.
dpkg-buildpackage: error: debian/rules build gave error exit status 2
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value:
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.620-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
debian/rules:6: /usr/share/cdbs/1/rules/debhelper.mk: No such file or directory
make: *** No rule to make target `/usr/share/cdbs/1/rules/debhelper.mk'.  Stop.
dpkg-buildpackage: error: debian/rules build gave error exit status 2
Removing temporary directory: fglrx-install.4k4HAD

what is the problem?
Tanx

---

